---
author: mukin
ms.assetid: bfabd3d5-dd56-4917-9572-f3ba0de4f8c0
title: Referenz zu Kern-APIs des Device Portal
description: "Hier erhalten Sie Informationen zu den Kern-REST-APIs für das Windows Device Portal, die Sie für den Zugriff auf die Daten und die programmatische Steuerung des Geräts verwenden können."
ms.author: mukin
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: b6df8f361df82ef65098877027cf1857fa575b0b
ms.sourcegitcommit: d2ec178103f49b198da2ee486f1681e38dcc8e7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2017
---
# <a name="device-portal-core-api-reference"></a><span data-ttu-id="5ed5c-104">Referenz zu Kern-APIs des Device Portal</span><span class="sxs-lookup"><span data-stu-id="5ed5c-104">Device Portal core API reference</span></span>

<span data-ttu-id="5ed5c-105">Alle Komponenten im Windows Device Portal basieren auf REST-APIs, die Sie für den Zugriff auf die Daten und die programmatische Steuerung des Geräts verwenden können.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-105">Everything in the Windows Device Portal is built on top of REST APIs that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deployment"></a><span data-ttu-id="5ed5c-106">App-Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-106">App deployment</span></span>

---
### <a name="install-an-app"></a><span data-ttu-id="5ed5c-107">Installieren einer App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-107">Install an app</span></span>

**<span data-ttu-id="5ed5c-108">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-108">Request</span></span>**

<span data-ttu-id="5ed5c-109">Mit dem folgenden Anforderungsformat können Sie eine App installieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-109">You can install an app by using the following request format.</span></span>

<span data-ttu-id="5ed5c-110">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-110">Method</span></span>      | <span data-ttu-id="5ed5c-111">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-111">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-112">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-112">POST</span></span> | <span data-ttu-id="5ed5c-113">/api/app/packagemanager/package</span><span class="sxs-lookup"><span data-stu-id="5ed5c-113">/api/app/packagemanager/package</span></span>
<br />
**<span data-ttu-id="5ed5c-114">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-114">URI parameters</span></span>**

<span data-ttu-id="5ed5c-115">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-115">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-116">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-116">URI parameter</span></span> | <span data-ttu-id="5ed5c-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-117">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-118">package</span><span class="sxs-lookup"><span data-stu-id="5ed5c-118">package</span></span>   | <span data-ttu-id="5ed5c-119">(**erforderlich**) Der Dateiname des zu installierenden Pakets.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-119">(**required**) The file name of the package to be installed.</span></span>
<br />
**<span data-ttu-id="5ed5c-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-120">Request headers</span></span>**

- <span data-ttu-id="5ed5c-121">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-121">None</span></span>

**<span data-ttu-id="5ed5c-122">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-122">Request body</span></span>**

- <span data-ttu-id="5ed5c-123">Die APPX- oder APPXBUNDLE-Datei sowie alle von der App benötigten Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-123">The .appx or .appxbundle file, as well as any dependencies the app requires.</span></span> 
- <span data-ttu-id="5ed5c-124">Das Zertifikat zum Signieren der App, wenn es sich um ein IoT- oder Windows-Desktop-Gerät handelt.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-124">The certificate used to sign the app, if the device is IoT or Windows Desktop.</span></span> <span data-ttu-id="5ed5c-125">Bei anderen Plattformen ist das Zertifikat nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-125">Other platforms do not require the certificate.</span></span> 

**<span data-ttu-id="5ed5c-126">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-126">Response</span></span>**

**<span data-ttu-id="5ed5c-127">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-127">Status code</span></span>**

<span data-ttu-id="5ed5c-128">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-128">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-129">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-129">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-130">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-131">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-131">200</span></span> | <span data-ttu-id="5ed5c-132">Bereitstellungsanforderung akzeptiert und wird verarbeitet</span><span class="sxs-lookup"><span data-stu-id="5ed5c-132">Deploy request accepted and being processed</span></span>
<span data-ttu-id="5ed5c-133">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-133">4XX</span></span> | <span data-ttu-id="5ed5c-134">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-134">Error codes</span></span>
<span data-ttu-id="5ed5c-135">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-135">5XX</span></span> | <span data-ttu-id="5ed5c-136">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-136">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-137">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-137">Available device families</span></span>**

* <span data-ttu-id="5ed5c-138">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-138">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-139">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-139">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-140">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-140">Xbox</span></span>
* <span data-ttu-id="5ed5c-141">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-141">HoloLens</span></span>
* <span data-ttu-id="5ed5c-142">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-142">IoT</span></span>

---
### <a name="get-app-installation-status"></a><span data-ttu-id="5ed5c-143">Abrufen des App-Installationsstatus</span><span class="sxs-lookup"><span data-stu-id="5ed5c-143">Get app installation status</span></span>

**<span data-ttu-id="5ed5c-144">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-144">Request</span></span>**

<span data-ttu-id="5ed5c-145">Mit dem folgenden Anforderungsformat können Sie den Status einer derzeit ausgeführten App-Installation abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-145">You can get the status of an app installation that is currently in progress by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-146">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-146">Method</span></span>      | <span data-ttu-id="5ed5c-147">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-147">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-148">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-148">GET</span></span> | <span data-ttu-id="5ed5c-149">/api/app/packagemanager/state</span><span class="sxs-lookup"><span data-stu-id="5ed5c-149">/api/app/packagemanager/state</span></span>
<br />
**<span data-ttu-id="5ed5c-150">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-150">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-151">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-151">None</span></span>

**<span data-ttu-id="5ed5c-152">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-152">Request headers</span></span>**

- <span data-ttu-id="5ed5c-153">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-153">None</span></span>

**<span data-ttu-id="5ed5c-154">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-154">Request body</span></span>**

- <span data-ttu-id="5ed5c-155">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-155">None</span></span>

**<span data-ttu-id="5ed5c-156">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-156">Response</span></span>**

**<span data-ttu-id="5ed5c-157">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-157">Status code</span></span>**

<span data-ttu-id="5ed5c-158">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-158">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-159">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-159">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-160">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-161">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-161">200</span></span> | <span data-ttu-id="5ed5c-162">Das Ergebnis der letzten Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-162">The result of the last deployment</span></span>
<span data-ttu-id="5ed5c-163">204</span><span class="sxs-lookup"><span data-stu-id="5ed5c-163">204</span></span> | <span data-ttu-id="5ed5c-164">Die Installation läuft</span><span class="sxs-lookup"><span data-stu-id="5ed5c-164">The installation is running</span></span>
<span data-ttu-id="5ed5c-165">404</span><span class="sxs-lookup"><span data-stu-id="5ed5c-165">404</span></span> | <span data-ttu-id="5ed5c-166">Keine Installationsaktion wurde gefunden</span><span class="sxs-lookup"><span data-stu-id="5ed5c-166">No installation action was found</span></span>
<br />
**<span data-ttu-id="5ed5c-167">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-167">Available device families</span></span>**

* <span data-ttu-id="5ed5c-168">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-168">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-169">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-169">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-170">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-170">Xbox</span></span>
* <span data-ttu-id="5ed5c-171">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-171">HoloLens</span></span>
* <span data-ttu-id="5ed5c-172">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-172">IoT</span></span>

---
### <a name="uninstall-an-app"></a><span data-ttu-id="5ed5c-173">Deinstallieren einer App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-173">Uninstall an app</span></span>

**<span data-ttu-id="5ed5c-174">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-174">Request</span></span>**

<span data-ttu-id="5ed5c-175">Mit dem folgenden Anforderungsformat können Sie eine App deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-175">You can uninstall an app by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-176">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-176">Method</span></span>      | <span data-ttu-id="5ed5c-177">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-177">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-178">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-178">DELETE</span></span> | <span data-ttu-id="5ed5c-179">/api/app/packagemanager/package</span><span class="sxs-lookup"><span data-stu-id="5ed5c-179">/api/app/packagemanager/package</span></span>
<br />

**<span data-ttu-id="5ed5c-180">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-180">URI parameters</span></span>**

<span data-ttu-id="5ed5c-181">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-181">URI parameter</span></span> | <span data-ttu-id="5ed5c-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-182">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-183">package</span><span class="sxs-lookup"><span data-stu-id="5ed5c-183">package</span></span>   | <span data-ttu-id="5ed5c-184">(**Erforderlich**) PackageFullName (von GET /api/app/packagemanager/packages) der Ziel-App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-184">(**required**) The PackageFullName (from GET /api/app/packagemanager/packages) of the target app</span></span>

**<span data-ttu-id="5ed5c-185">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-185">Request headers</span></span>**

- <span data-ttu-id="5ed5c-186">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-186">None</span></span>

**<span data-ttu-id="5ed5c-187">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-187">Request body</span></span>**

- <span data-ttu-id="5ed5c-188">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-188">None</span></span>

**<span data-ttu-id="5ed5c-189">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-189">Response</span></span>**

**<span data-ttu-id="5ed5c-190">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-190">Status code</span></span>**

<span data-ttu-id="5ed5c-191">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-191">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-192">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-192">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-193">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-194">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-194">200</span></span> | <span data-ttu-id="5ed5c-195">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-195">OK</span></span>
<span data-ttu-id="5ed5c-196">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-196">4XX</span></span> | <span data-ttu-id="5ed5c-197">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-197">Error codes</span></span>
<span data-ttu-id="5ed5c-198">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-198">5XX</span></span> | <span data-ttu-id="5ed5c-199">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-199">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-200">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-200">Available device families</span></span>**

* <span data-ttu-id="5ed5c-201">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-201">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-202">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-202">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-203">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-203">Xbox</span></span>
* <span data-ttu-id="5ed5c-204">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-204">HoloLens</span></span>
* <span data-ttu-id="5ed5c-205">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-205">IoT</span></span>

---
### <a name="get-installed-apps"></a><span data-ttu-id="5ed5c-206">Abrufen installierter Apps</span><span class="sxs-lookup"><span data-stu-id="5ed5c-206">Get installed apps</span></span>

**<span data-ttu-id="5ed5c-207">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-207">Request</span></span>**

<span data-ttu-id="5ed5c-208">Mit dem folgenden Anforderungsformat können Sie eine Liste der auf dem System installierten Apps abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-208">You can get a list of apps installed on the system by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-209">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-209">Method</span></span>      | <span data-ttu-id="5ed5c-210">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-210">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-211">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-211">GET</span></span> | <span data-ttu-id="5ed5c-212">/api/app/packagemanager/packages</span><span class="sxs-lookup"><span data-stu-id="5ed5c-212">/api/app/packagemanager/packages</span></span>
<br />

**<span data-ttu-id="5ed5c-213">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-213">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-214">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-214">None</span></span>

**<span data-ttu-id="5ed5c-215">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-215">Request headers</span></span>**

- <span data-ttu-id="5ed5c-216">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-216">None</span></span>

**<span data-ttu-id="5ed5c-217">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-217">Request body</span></span>**

- <span data-ttu-id="5ed5c-218">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-218">None</span></span>

**<span data-ttu-id="5ed5c-219">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-219">Response</span></span>**

<span data-ttu-id="5ed5c-220">Die Antwort enthält eine Liste der installierten Pakete mit zugehörigen Details.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-220">The response includes a list of installed packages with associated details.</span></span> <span data-ttu-id="5ed5c-221">Die Vorlage für diese Antwort lautet wie folgt.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-221">The template for this response is as follows.</span></span>
```
{"InstalledPackages": [
    {
        "Name": string,
        "PackageFamilyName": string,
        "PackageFullName": string,
        "PackageOrigin": int, (https://msdn.microsoft.com/en-us/library/windows/desktop/dn313167(v=vs.85).aspx)
        "PackageRelativeId": string,
        "Publisher": string,
        "Version": {
            "Build": int,
            "Major": int,
            "Minor": int,
            "Revision": int
     },
     "RegisteredUsers": [
     {
        "UserDisplayName": string,
        "UserSID": string
     },...
     ]
    },...
]}
```
**<span data-ttu-id="5ed5c-222">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-222">Status code</span></span>**

<span data-ttu-id="5ed5c-223">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-223">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-224">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-224">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-225">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-225">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-226">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-226">200</span></span> | <span data-ttu-id="5ed5c-227">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-227">OK</span></span>
<span data-ttu-id="5ed5c-228">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-228">4XX</span></span> | <span data-ttu-id="5ed5c-229">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-229">Error codes</span></span>
<span data-ttu-id="5ed5c-230">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-230">5XX</span></span> | <span data-ttu-id="5ed5c-231">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-231">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-232">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-232">Available device families</span></span>**

* <span data-ttu-id="5ed5c-233">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-233">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-234">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-234">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-235">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-235">Xbox</span></span>
* <span data-ttu-id="5ed5c-236">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-236">HoloLens</span></span>
* <span data-ttu-id="5ed5c-237">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-237">IoT</span></span>

---
## Device manager
---
### <a name="get-the-installed-devices-on-the-machine"></a><span data-ttu-id="5ed5c-238">Abrufen der auf dem Computer installierten Geräte</span><span class="sxs-lookup"><span data-stu-id="5ed5c-238">Get the installed devices on the machine</span></span>

**<span data-ttu-id="5ed5c-239">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-239">Request</span></span>**

<span data-ttu-id="5ed5c-240">Mit dem folgenden Anforderungsformat können Sie eine Liste der auf dem Computer installierten Geräte abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-240">You can get a list of devices that are installed on the machine by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-241">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-241">Method</span></span>      | <span data-ttu-id="5ed5c-242">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-242">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-243">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-243">GET</span></span> | <span data-ttu-id="5ed5c-244">/api/devicemanager/devices</span><span class="sxs-lookup"><span data-stu-id="5ed5c-244">/api/devicemanager/devices</span></span>
<br />

**<span data-ttu-id="5ed5c-245">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-245">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-246">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-246">None</span></span>

**<span data-ttu-id="5ed5c-247">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-247">Request headers</span></span>**

- <span data-ttu-id="5ed5c-248">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-248">None</span></span>

**<span data-ttu-id="5ed5c-249">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-249">Request body</span></span>**

- <span data-ttu-id="5ed5c-250">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-250">None</span></span>

**<span data-ttu-id="5ed5c-251">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-251">Response</span></span>**

<span data-ttu-id="5ed5c-252">Die Antwort enthält ein JSON-Array von Geräten, die mit dem Gerät verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-252">The response includes a JSON array of devices attached to the device.</span></span>
``` 
{"DeviceList": [
    {
        "Class": string,
        "Description": string,
        "ID": string,
        "Manufacturer": string,
        "ParentID": string,
        "ProblemCode": int,
        "StatusCode": int
    },...
]}
```

**<span data-ttu-id="5ed5c-253">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-253">Status code</span></span>**

<span data-ttu-id="5ed5c-254">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-254">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-255">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-255">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-256">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-256">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-257">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-257">200</span></span> | <span data-ttu-id="5ed5c-258">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-258">OK</span></span>
<span data-ttu-id="5ed5c-259">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-259">4XX</span></span> | <span data-ttu-id="5ed5c-260">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-260">Error codes</span></span>
<span data-ttu-id="5ed5c-261">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-261">5XX</span></span> | <span data-ttu-id="5ed5c-262">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-262">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-263">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-263">Available device families</span></span>**

* <span data-ttu-id="5ed5c-264">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-264">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-265">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-265">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-266">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-266">IoT</span></span>

---
## Dump collection
---
### <a name="get-the-list-of-all-crash-dumps-for-apps"></a><span data-ttu-id="5ed5c-267">Abrufen der Liste aller Absturzabbilder für Apps</span><span class="sxs-lookup"><span data-stu-id="5ed5c-267">Get the list of all crash dumps for apps</span></span>

**<span data-ttu-id="5ed5c-268">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-268">Request</span></span>**

<span data-ttu-id="5ed5c-269">Mit dem folgenden Anforderungsformat können Sie die Liste aller verfügbaren Absturzabbilder für jede quergeladene App abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-269">You can get the list of all the available crash dumps for all sideloaded apps by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-270">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-270">Method</span></span>      | <span data-ttu-id="5ed5c-271">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-271">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-272">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-272">GET</span></span> | <span data-ttu-id="5ed5c-273">/api/debug/dump/usermode/dumps</span><span class="sxs-lookup"><span data-stu-id="5ed5c-273">/api/debug/dump/usermode/dumps</span></span>
<br />

**<span data-ttu-id="5ed5c-274">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-274">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-275">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-275">None</span></span>

**<span data-ttu-id="5ed5c-276">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-276">Request headers</span></span>**

- <span data-ttu-id="5ed5c-277">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-277">None</span></span>

**<span data-ttu-id="5ed5c-278">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-278">Request body</span></span>**

- <span data-ttu-id="5ed5c-279">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-279">None</span></span>

**<span data-ttu-id="5ed5c-280">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-280">Response</span></span>**

<span data-ttu-id="5ed5c-281">Die Antwort enthält eine Liste der Absturzabbilder für jede quergeladene Anwendung.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-281">The response includes a list of crash dumps for each sideloaded application.</span></span>

**<span data-ttu-id="5ed5c-282">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-282">Status code</span></span>**

<span data-ttu-id="5ed5c-283">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-283">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-284">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-284">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-285">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-285">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-286">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-286">200</span></span> | <span data-ttu-id="5ed5c-287">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-287">OK</span></span>
<span data-ttu-id="5ed5c-288">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-288">4XX</span></span> | <span data-ttu-id="5ed5c-289">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-289">Error codes</span></span>
<span data-ttu-id="5ed5c-290">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-290">5XX</span></span> | <span data-ttu-id="5ed5c-291">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-291">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-292">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-292">Available device families</span></span>**

* <span data-ttu-id="5ed5c-293">Windows Mobile (im Windows-Insider-Programm)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-293">Window Mobile (in Windows Insider Program)</span></span>
* <span data-ttu-id="5ed5c-294">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-294">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-295">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-295">HoloLens</span></span>
* <span data-ttu-id="5ed5c-296">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-296">IoT</span></span>

---
### <a name="get-the-crash-dump-collection-settings-for-an-app"></a><span data-ttu-id="5ed5c-297">Abrufen der Absturzabbildsammlungs-Einstellungen für eine App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-297">Get the crash dump collection settings for an app</span></span>

**<span data-ttu-id="5ed5c-298">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-298">Request</span></span>**

<span data-ttu-id="5ed5c-299">Mit dem folgenden Anforderungsformat können Sie die Absturzabbildsammlungs-Einstellungen für eine quergeladene App abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-299">You can get the crash dump collection settings for a sideloaded app by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-300">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-300">Method</span></span>      | <span data-ttu-id="5ed5c-301">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-301">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-302">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-302">GET</span></span> | <span data-ttu-id="5ed5c-303">/api/debug/dump/usermode/crashcontrol</span><span class="sxs-lookup"><span data-stu-id="5ed5c-303">/api/debug/dump/usermode/crashcontrol</span></span>
<br />

**<span data-ttu-id="5ed5c-304">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-304">URI parameters</span></span>**

<span data-ttu-id="5ed5c-305">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-305">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-306">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-306">URI parameter</span></span> | <span data-ttu-id="5ed5c-307">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-307">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-308">packageFullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-308">packageFullname</span></span>   | <span data-ttu-id="5ed5c-309">(**erforderlich**) Der vollständige Name des Pakets für die quergeladene App.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-309">(**required**) The full name of the package for the sideloaded app.</span></span>
<br />
**<span data-ttu-id="5ed5c-310">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-310">Request headers</span></span>**

- <span data-ttu-id="5ed5c-311">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-311">None</span></span>

**<span data-ttu-id="5ed5c-312">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-312">Request body</span></span>**

- <span data-ttu-id="5ed5c-313">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-313">None</span></span>

**<span data-ttu-id="5ed5c-314">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-314">Response</span></span>**

<span data-ttu-id="5ed5c-315">Die Antwort weist das folgende Format auf.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-315">The response has the following format.</span></span>
```
{"CrashDumpEnabled": bool}
```

**<span data-ttu-id="5ed5c-316">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-316">Status code</span></span>**

<span data-ttu-id="5ed5c-317">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-317">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-318">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-318">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-319">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-319">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-320">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-320">200</span></span> | <span data-ttu-id="5ed5c-321">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-321">OK</span></span>
<span data-ttu-id="5ed5c-322">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-322">4XX</span></span> | <span data-ttu-id="5ed5c-323">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-323">Error codes</span></span>
<span data-ttu-id="5ed5c-324">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-324">5XX</span></span> | <span data-ttu-id="5ed5c-325">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-325">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-326">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-326">Available device families</span></span>**

* <span data-ttu-id="5ed5c-327">Windows Mobile (im Windows-Insider-Programm)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-327">Window Mobile (in Windows Insider Program)</span></span>
* <span data-ttu-id="5ed5c-328">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-328">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-329">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-329">HoloLens</span></span>
* <span data-ttu-id="5ed5c-330">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-330">IoT</span></span>

---
### <a name="delete-a-crash-dump-for-a-sideloaded-app"></a><span data-ttu-id="5ed5c-331">Löschen eines Absturzabbilds für eine quergeladene App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-331">Delete a crash dump for a sideloaded app</span></span>

**<span data-ttu-id="5ed5c-332">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-332">Request</span></span>**

<span data-ttu-id="5ed5c-333">Mit dem folgenden Anforderungsformat können Sie das Absturzabbild einer quergeladenen App löschen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-333">You can delete a sideloaded app's crash dump by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-334">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-334">Method</span></span>      | <span data-ttu-id="5ed5c-335">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-335">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-336">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-336">DELETE</span></span> | <span data-ttu-id="5ed5c-337">/api/debug/dump/usermode/crashdump</span><span class="sxs-lookup"><span data-stu-id="5ed5c-337">/api/debug/dump/usermode/crashdump</span></span>
<br />

**<span data-ttu-id="5ed5c-338">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-338">URI parameters</span></span>**

<span data-ttu-id="5ed5c-339">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-339">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-340">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-340">URI parameter</span></span> | <span data-ttu-id="5ed5c-341">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-341">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-342">packageFullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-342">packageFullname</span></span>   | <span data-ttu-id="5ed5c-343">(**erforderlich**) Der vollständige Name des Pakets für die quergeladene App.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-343">(**required**) The full name of the package for the sideloaded app.</span></span>
<span data-ttu-id="5ed5c-344">fileName</span><span class="sxs-lookup"><span data-stu-id="5ed5c-344">fileName</span></span>   | <span data-ttu-id="5ed5c-345">(**erforderlich**) Der Name der Absturzabbilddatei, die gelöscht werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-345">(**required**) The name of the dump file that should be deleted.</span></span>
<br />
**<span data-ttu-id="5ed5c-346">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-346">Request headers</span></span>**

- <span data-ttu-id="5ed5c-347">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-347">None</span></span>

**<span data-ttu-id="5ed5c-348">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-348">Request body</span></span>**

- <span data-ttu-id="5ed5c-349">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-349">None</span></span>

**<span data-ttu-id="5ed5c-350">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-350">Response</span></span>**

**<span data-ttu-id="5ed5c-351">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-351">Status code</span></span>**

<span data-ttu-id="5ed5c-352">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-352">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-353">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-353">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-354">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-354">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-355">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-355">200</span></span> | <span data-ttu-id="5ed5c-356">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-356">OK</span></span>
<span data-ttu-id="5ed5c-357">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-357">4XX</span></span> | <span data-ttu-id="5ed5c-358">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-358">Error codes</span></span>
<span data-ttu-id="5ed5c-359">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-359">5XX</span></span> | <span data-ttu-id="5ed5c-360">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-360">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-361">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-361">Available device families</span></span>**

* <span data-ttu-id="5ed5c-362">Windows Mobile (im Windows-Insider-Programm)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-362">Window Mobile (in Windows Insider Program)</span></span>
* <span data-ttu-id="5ed5c-363">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-363">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-364">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-364">HoloLens</span></span>
* <span data-ttu-id="5ed5c-365">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-365">IoT</span></span>

---
### <a name="disable-crash-dumps-for-a-sideloaded-app"></a><span data-ttu-id="5ed5c-366">Deaktivieren der Absturzabbilder für eine quergeladene App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-366">Disable crash dumps for a sideloaded app</span></span>

**<span data-ttu-id="5ed5c-367">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-367">Request</span></span>**

<span data-ttu-id="5ed5c-368">Mit dem folgenden Anforderungsformat können Sie Absturzabbilder für eine quergeladene App deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-368">You can disable crash dumps for a sideloaded app by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-369">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-369">Method</span></span>      | <span data-ttu-id="5ed5c-370">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-370">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-371">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-371">DELETE</span></span> | <span data-ttu-id="5ed5c-372">/api/debug/dump/usermode/crashcontrol</span><span class="sxs-lookup"><span data-stu-id="5ed5c-372">/api/debug/dump/usermode/crashcontrol</span></span>

<br />
**<span data-ttu-id="5ed5c-373">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-373">URI parameters</span></span>**

<span data-ttu-id="5ed5c-374">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-374">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-375">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-375">URI parameter</span></span> | <span data-ttu-id="5ed5c-376">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-376">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-377">packageFullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-377">packageFullname</span></span>   | <span data-ttu-id="5ed5c-378">(**erforderlich**) Der vollständige Name des Pakets für die quergeladene App.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-378">(**required**) The full name of the package for the sideloaded app.</span></span>
<br />
**<span data-ttu-id="5ed5c-379">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-379">Request headers</span></span>**

- <span data-ttu-id="5ed5c-380">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-380">None</span></span>

**<span data-ttu-id="5ed5c-381">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-381">Request body</span></span>**

- <span data-ttu-id="5ed5c-382">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-382">None</span></span>

**<span data-ttu-id="5ed5c-383">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-383">Response</span></span>**

**<span data-ttu-id="5ed5c-384">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-384">Status code</span></span>**

<span data-ttu-id="5ed5c-385">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-385">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-386">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-386">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-387">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-387">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-388">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-388">200</span></span> | <span data-ttu-id="5ed5c-389">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-389">OK</span></span>
<span data-ttu-id="5ed5c-390">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-390">4XX</span></span> | <span data-ttu-id="5ed5c-391">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-391">Error codes</span></span>
<span data-ttu-id="5ed5c-392">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-392">5XX</span></span> | <span data-ttu-id="5ed5c-393">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-393">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-394">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-394">Available device families</span></span>**

* <span data-ttu-id="5ed5c-395">Windows Mobile (im Windows-Insider-Programm)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-395">Window Mobile (in Windows Insider Program)</span></span>
* <span data-ttu-id="5ed5c-396">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-396">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-397">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-397">HoloLens</span></span>
* <span data-ttu-id="5ed5c-398">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-398">IoT</span></span>

---
### <a name="download-the-crash-dump-for-a-sideloaded-app"></a><span data-ttu-id="5ed5c-399">Herunterladen des Absturzabbilds für eine quergeladene App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-399">Download the crash dump for a sideloaded app</span></span>

**<span data-ttu-id="5ed5c-400">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-400">Request</span></span>**

<span data-ttu-id="5ed5c-401">Mit dem folgenden Anforderungsformat können Sie das Absturzabbild einer quergeladenen App herunterladen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-401">You can download a sideloaded app's crash dump by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-402">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-402">Method</span></span>      | <span data-ttu-id="5ed5c-403">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-403">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-404">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-404">GET</span></span> | <span data-ttu-id="5ed5c-405">/api/debug/dump/usermode/crashdump</span><span class="sxs-lookup"><span data-stu-id="5ed5c-405">/api/debug/dump/usermode/crashdump</span></span>
<br />

**<span data-ttu-id="5ed5c-406">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-406">URI parameters</span></span>**

<span data-ttu-id="5ed5c-407">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-407">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-408">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-408">URI parameter</span></span> | <span data-ttu-id="5ed5c-409">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-409">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-410">packageFullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-410">packageFullname</span></span>   | <span data-ttu-id="5ed5c-411">(**erforderlich**) Der vollständige Name des Pakets für die quergeladene App.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-411">(**required**) The full name of the package for the sideloaded app.</span></span>
<span data-ttu-id="5ed5c-412">fileName</span><span class="sxs-lookup"><span data-stu-id="5ed5c-412">fileName</span></span>   | <span data-ttu-id="5ed5c-413">(**erforderlich**) Der Name der Absturzabbilddatei, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-413">(**required**) The name of the dump file that you want to download.</span></span>
<br />
**<span data-ttu-id="5ed5c-414">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-414">Request headers</span></span>**

- <span data-ttu-id="5ed5c-415">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-415">None</span></span>

**<span data-ttu-id="5ed5c-416">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-416">Request body</span></span>**

- <span data-ttu-id="5ed5c-417">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-417">None</span></span>

**<span data-ttu-id="5ed5c-418">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-418">Response</span></span>**

<span data-ttu-id="5ed5c-419">Die Antwort enthält eine Absturzabbilddatei.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-419">The response includes a dump file.</span></span> <span data-ttu-id="5ed5c-420">Sie können die Absturzabbilddatei mit WinDbg oder Visual Studio untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-420">You can use WinDbg or Visual Studio to examine the dump file.</span></span>

**<span data-ttu-id="5ed5c-421">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-421">Status code</span></span>**

<span data-ttu-id="5ed5c-422">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-422">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-423">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-423">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-424">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-424">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-425">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-425">200</span></span> | <span data-ttu-id="5ed5c-426">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-426">OK</span></span>
<span data-ttu-id="5ed5c-427">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-427">4XX</span></span> | <span data-ttu-id="5ed5c-428">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-428">Error codes</span></span>
<span data-ttu-id="5ed5c-429">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-429">5XX</span></span> | <span data-ttu-id="5ed5c-430">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-430">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-431">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-431">Available device families</span></span>**

* <span data-ttu-id="5ed5c-432">Windows Mobile (im Windows-Insider-Programm)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-432">Window Mobile (in Windows Insider Program)</span></span>
* <span data-ttu-id="5ed5c-433">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-433">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-434">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-434">HoloLens</span></span>
* <span data-ttu-id="5ed5c-435">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-435">IoT</span></span>

---
### <a name="enable-crash-dumps-for-a-sideloaded-app"></a><span data-ttu-id="5ed5c-436">Aktivieren der Absturzabbilder für eine quergeladene App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-436">Enable crash dumps for a sideloaded app</span></span>

**<span data-ttu-id="5ed5c-437">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-437">Request</span></span>**

<span data-ttu-id="5ed5c-438">Mit dem folgenden Anforderungsformat können Sie Absturzabbilder für eine quergeladene App aktivieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-438">You can enable crash dumps for a sideloaded app by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-439">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-439">Method</span></span>      | <span data-ttu-id="5ed5c-440">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-440">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-441">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-441">POST</span></span> | <span data-ttu-id="5ed5c-442">/api/debug/dump/usermode/crashcontrol</span><span class="sxs-lookup"><span data-stu-id="5ed5c-442">/api/debug/dump/usermode/crashcontrol</span></span>
<br />

**<span data-ttu-id="5ed5c-443">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-443">URI parameters</span></span>**

<span data-ttu-id="5ed5c-444">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-444">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-445">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-445">URI parameter</span></span> | <span data-ttu-id="5ed5c-446">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-446">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-447">packageFullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-447">packageFullname</span></span>   | <span data-ttu-id="5ed5c-448">(**erforderlich**) Der vollständige Name des Pakets für die quergeladene App.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-448">(**required**) The full name of the package for the sideloaded app.</span></span>
<br />
**<span data-ttu-id="5ed5c-449">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-449">Request headers</span></span>**

- <span data-ttu-id="5ed5c-450">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-450">None</span></span>

**<span data-ttu-id="5ed5c-451">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-451">Request body</span></span>**

- <span data-ttu-id="5ed5c-452">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-452">None</span></span>

**<span data-ttu-id="5ed5c-453">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-453">Response</span></span>**

**<span data-ttu-id="5ed5c-454">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-454">Status code</span></span>**

<span data-ttu-id="5ed5c-455">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-455">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-456">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-456">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-457">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-457">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-458">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-458">200</span></span> | <span data-ttu-id="5ed5c-459">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-459">OK</span></span>
<br />
**<span data-ttu-id="5ed5c-460">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-460">Available device families</span></span>**

* <span data-ttu-id="5ed5c-461">Windows Mobile (im Windows-Insider-Programm)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-461">Window Mobile (in Windows Insider Program)</span></span>
* <span data-ttu-id="5ed5c-462">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-462">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-463">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-463">HoloLens</span></span>
* <span data-ttu-id="5ed5c-464">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-464">IoT</span></span>

---
### <a name="get-the-list-of-bugcheck-files"></a><span data-ttu-id="5ed5c-465">Abrufen der Liste der Fehlerüberprüfungsdateien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-465">Get the list of bugcheck files</span></span>

**<span data-ttu-id="5ed5c-466">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-466">Request</span></span>**

<span data-ttu-id="5ed5c-467">Mit dem folgenden Anforderungsformat können Sie die Liste der Fehlerüberprüfungs-Minidumpdateien abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-467">You can get the list of bugcheck minidump files by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-468">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-468">Method</span></span>      | <span data-ttu-id="5ed5c-469">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-469">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-470">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-470">GET</span></span> | <span data-ttu-id="5ed5c-471">/api/debug/dump/kernel/dumplist</span><span class="sxs-lookup"><span data-stu-id="5ed5c-471">/api/debug/dump/kernel/dumplist</span></span>
<br />

**<span data-ttu-id="5ed5c-472">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-472">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-473">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-473">None</span></span>

**<span data-ttu-id="5ed5c-474">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-474">Request headers</span></span>**

- <span data-ttu-id="5ed5c-475">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-475">None</span></span>

**<span data-ttu-id="5ed5c-476">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-476">Request body</span></span>**

- <span data-ttu-id="5ed5c-477">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-477">None</span></span>

**<span data-ttu-id="5ed5c-478">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-478">Response</span></span>**

<span data-ttu-id="5ed5c-479">Die Antwort enthält eine Liste der Minidumpdateinamen und die Größen dieser Dateien.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-479">The response includes a list of dump file names and the sizes of these files.</span></span> <span data-ttu-id="5ed5c-480">Diese Liste wird das folgende Format aufweisen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-480">This list will be in the following format.</span></span> 
```
{"DumpFiles": [
    {
        "FileName": string,
        "FileSize": int
    },...
]}
```

**<span data-ttu-id="5ed5c-481">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-481">Status code</span></span>**

<span data-ttu-id="5ed5c-482">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-482">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-483">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-483">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-484">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-484">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-485">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-485">200</span></span> | <span data-ttu-id="5ed5c-486">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-486">OK</span></span>
<br />
**<span data-ttu-id="5ed5c-487">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-487">Available device families</span></span>**

* <span data-ttu-id="5ed5c-488">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-488">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-489">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-489">IoT</span></span>

---
### <a name="download-a-bugcheck-dump-file"></a><span data-ttu-id="5ed5c-490">Herunterladen einer Fehlerüberprüfungs-Speicherabbilddatei</span><span class="sxs-lookup"><span data-stu-id="5ed5c-490">Download a bugcheck dump file</span></span>

**<span data-ttu-id="5ed5c-491">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-491">Request</span></span>**

<span data-ttu-id="5ed5c-492">Mit dem folgenden Anforderungsformat können Sie eine Fehlerüberprüfungs-Speicherabbilddatei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-492">You can download a bugcheck dump file by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-493">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-493">Method</span></span>      | <span data-ttu-id="5ed5c-494">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-494">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-495">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-495">GET</span></span> | <span data-ttu-id="5ed5c-496">/api/debug/dump/kernel/dump</span><span class="sxs-lookup"><span data-stu-id="5ed5c-496">/api/debug/dump/kernel/dump</span></span>
<br />

**<span data-ttu-id="5ed5c-497">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-497">URI parameters</span></span>**

<span data-ttu-id="5ed5c-498">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-498">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-499">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-499">URI parameter</span></span> | <span data-ttu-id="5ed5c-500">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-500">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-501">filename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-501">filename</span></span>   | <span data-ttu-id="5ed5c-502">(**erforderlich**) Der Dateiname der Speicherabbilddatei.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-502">(**required**) The file name of the dump file.</span></span> <span data-ttu-id="5ed5c-503">Sie finden diesen mithilfe der API zum Abrufen der Speicherabbildliste.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-503">You can find this by using the API to get the dump list.</span></span>
<br />
**<span data-ttu-id="5ed5c-504">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-504">Request headers</span></span>**

- <span data-ttu-id="5ed5c-505">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-505">None</span></span>

**<span data-ttu-id="5ed5c-506">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-506">Request body</span></span>**

- <span data-ttu-id="5ed5c-507">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-507">None</span></span>

**<span data-ttu-id="5ed5c-508">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-508">Response</span></span>**

<span data-ttu-id="5ed5c-509">Die Antwort enthält die Speicherabbilddatei.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-509">The response includes the dump file.</span></span> <span data-ttu-id="5ed5c-510">Sie können diese Datei mithilfe von WinDbg untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-510">You can inspect this file using WinDbg.</span></span>

**<span data-ttu-id="5ed5c-511">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-511">Status code</span></span>**

<span data-ttu-id="5ed5c-512">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-512">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-513">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-513">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-514">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-514">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-515">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-515">200</span></span> | <span data-ttu-id="5ed5c-516">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-516">OK</span></span>
<span data-ttu-id="5ed5c-517">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-517">4XX</span></span> | <span data-ttu-id="5ed5c-518">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-518">Error codes</span></span>
<span data-ttu-id="5ed5c-519">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-519">5XX</span></span> | <span data-ttu-id="5ed5c-520">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-520">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-521">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-521">Available device families</span></span>**

* <span data-ttu-id="5ed5c-522">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-522">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-523">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-523">IoT</span></span>

---
### <a name="get-the-bugcheck-crash-control-settings"></a><span data-ttu-id="5ed5c-524">Abrufen der CrashControl-Fehlerüberprüfungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="5ed5c-524">Get the bugcheck crash control settings</span></span>

**<span data-ttu-id="5ed5c-525">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-525">Request</span></span>**

<span data-ttu-id="5ed5c-526">Mit dem folgenden Anforderungsformat können Sie die CrashControl-Fehlerüberprüfungseinstellungen abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-526">You can get the bugcheck crash control settings by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-527">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-527">Method</span></span>      | <span data-ttu-id="5ed5c-528">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-528">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-529">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-529">GET</span></span> | <span data-ttu-id="5ed5c-530">/api/debug/dump/kernel/crashcontrol</span><span class="sxs-lookup"><span data-stu-id="5ed5c-530">/api/debug/dump/kernel/crashcontrol</span></span>

<br />
**<span data-ttu-id="5ed5c-531">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-531">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-532">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-532">None</span></span>

**<span data-ttu-id="5ed5c-533">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-533">Request headers</span></span>**

- <span data-ttu-id="5ed5c-534">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-534">None</span></span>

**<span data-ttu-id="5ed5c-535">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-535">Request body</span></span>**

- <span data-ttu-id="5ed5c-536">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-536">None</span></span>

**<span data-ttu-id="5ed5c-537">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-537">Response</span></span>**

<span data-ttu-id="5ed5c-538">Die Antwort enthält die CrashControl-Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-538">The response includes the crash control settings.</span></span> <span data-ttu-id="5ed5c-539">Weitere Informationen zu CrashControl finden Sie im Artikel [](https://technet.microsoft.com/library/cc951703.aspx).</span><span class="sxs-lookup"><span data-stu-id="5ed5c-539">For more information about CrashControl, see the [CrashControl](https://technet.microsoft.com/library/cc951703.aspx) article.</span></span> <span data-ttu-id="5ed5c-540">Die Vorlage für die Antwort lautet wie folgt.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-540">The template for the response is as follows.</span></span>
```
{
    "autoreboot": bool (0 or 1),
    "dumptype": int (0 to 4),
    "maxdumpcount": int,
    "overwrite": bool (0 or 1)
}
```

**<span data-ttu-id="5ed5c-541">Abbildtypen</span><span class="sxs-lookup"><span data-stu-id="5ed5c-541">Dump types</span></span>**

<span data-ttu-id="5ed5c-542">0: Deaktiviert</span><span class="sxs-lookup"><span data-stu-id="5ed5c-542">0: Disabled</span></span>

<span data-ttu-id="5ed5c-543">1: Vollständiges Speicherabbild (sammelt den gesamten verwendeten Arbeitsspeicher)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-543">1: Complete memory dump (collects all in-use memory)</span></span>

<span data-ttu-id="5ed5c-544">2: Kernelspeicherabbild (ignoriert den Benutzermodusspeicher)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-544">2: Kernel memory dump (ignores user mode memory)</span></span>

<span data-ttu-id="5ed5c-545">3: Eingeschränktes Kernelminiabbild</span><span class="sxs-lookup"><span data-stu-id="5ed5c-545">3: Limited kernel minidump</span></span>

**<span data-ttu-id="5ed5c-546">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-546">Status code</span></span>**

<span data-ttu-id="5ed5c-547">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-547">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-548">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-548">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-549">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-549">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-550">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-550">200</span></span> | <span data-ttu-id="5ed5c-551">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-551">OK</span></span>
<span data-ttu-id="5ed5c-552">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-552">4XX</span></span> | <span data-ttu-id="5ed5c-553">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-553">Error codes</span></span>
<span data-ttu-id="5ed5c-554">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-554">5XX</span></span> | <span data-ttu-id="5ed5c-555">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-555">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-556">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-556">Available device families</span></span>**

* <span data-ttu-id="5ed5c-557">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-557">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-558">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-558">IoT</span></span>

---
### <a name="get-a-live-kernel-dump"></a><span data-ttu-id="5ed5c-559">Abrufen eines Live-Kernelspeicherabbilds</span><span class="sxs-lookup"><span data-stu-id="5ed5c-559">Get a live kernel dump</span></span>

**<span data-ttu-id="5ed5c-560">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-560">Request</span></span>**

<span data-ttu-id="5ed5c-561">Mit dem folgenden Anforderungsformat können Sie ein Live-Kernelspeicherabbild abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-561">You can get a live kernel dump by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-562">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-562">Method</span></span>      | <span data-ttu-id="5ed5c-563">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-563">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-564">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-564">GET</span></span> | <span data-ttu-id="5ed5c-565">/api/debug/dump/livekernel</span><span class="sxs-lookup"><span data-stu-id="5ed5c-565">/api/debug/dump/livekernel</span></span>
<br />

**<span data-ttu-id="5ed5c-566">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-566">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-567">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-567">None</span></span>

**<span data-ttu-id="5ed5c-568">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-568">Request headers</span></span>**

- <span data-ttu-id="5ed5c-569">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-569">None</span></span>

**<span data-ttu-id="5ed5c-570">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-570">Request body</span></span>**

- <span data-ttu-id="5ed5c-571">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-571">None</span></span>

**<span data-ttu-id="5ed5c-572">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-572">Response</span></span>**

<span data-ttu-id="5ed5c-573">Die Antwort enthält das vollständige Kernelmodus-Speicherabbild.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-573">The response includes the full kernel mode dump.</span></span> <span data-ttu-id="5ed5c-574">Sie können diese Datei mithilfe von WinDbg untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-574">You can inspect this file using WinDbg.</span></span>

**<span data-ttu-id="5ed5c-575">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-575">Status code</span></span>**

<span data-ttu-id="5ed5c-576">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-576">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-577">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-577">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-578">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-578">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-579">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-579">200</span></span> | <span data-ttu-id="5ed5c-580">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-580">OK</span></span>
<span data-ttu-id="5ed5c-581">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-581">4XX</span></span> | <span data-ttu-id="5ed5c-582">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-582">Error codes</span></span>
<span data-ttu-id="5ed5c-583">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-583">5XX</span></span> | <span data-ttu-id="5ed5c-584">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-584">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-585">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-585">Available device families</span></span>**

* <span data-ttu-id="5ed5c-586">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-586">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-587">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-587">IoT</span></span>

---
### <a name="get-a-dump-from-a-live-user-process"></a><span data-ttu-id="5ed5c-588">Abrufen eines Speicherabbilds von einem Livebenutzerprozess</span><span class="sxs-lookup"><span data-stu-id="5ed5c-588">Get a dump from a live user process</span></span>

**<span data-ttu-id="5ed5c-589">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-589">Request</span></span>**

<span data-ttu-id="5ed5c-590">Mit dem folgenden Anforderungsformat können Sie das Speicherabbild von einem Livebenutzerprozess abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-590">You can get the dump for live user process by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-591">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-591">Method</span></span>      | <span data-ttu-id="5ed5c-592">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-592">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-593">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-593">GET</span></span> | <span data-ttu-id="5ed5c-594">/api/debug/dump/usermode/live</span><span class="sxs-lookup"><span data-stu-id="5ed5c-594">/api/debug/dump/usermode/live</span></span>
<br />

**<span data-ttu-id="5ed5c-595">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-595">URI parameters</span></span>**

<span data-ttu-id="5ed5c-596">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-596">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-597">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-597">URI parameter</span></span> | <span data-ttu-id="5ed5c-598">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-598">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-599">pid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-599">pid</span></span>   | <span data-ttu-id="5ed5c-600">(**erforderlich**) Die eindeutige Prozess-ID für den betreffenden Prozess.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-600">(**required**) The unique process id for the process you are interested in.</span></span>
<br />
**<span data-ttu-id="5ed5c-601">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-601">Request headers</span></span>**

- <span data-ttu-id="5ed5c-602">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-602">None</span></span>

**<span data-ttu-id="5ed5c-603">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-603">Request body</span></span>**

- <span data-ttu-id="5ed5c-604">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-604">None</span></span>

**<span data-ttu-id="5ed5c-605">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-605">Response</span></span>**

<span data-ttu-id="5ed5c-606">Die Antwort enthält die Prozesssicherung.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-606">The response includes the process dump.</span></span> <span data-ttu-id="5ed5c-607">Sie können diese Datei mit WinDbg oder Visual Studio untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-607">You can inspect this file using WinDbg or Visual Studio.</span></span>

**<span data-ttu-id="5ed5c-608">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-608">Status code</span></span>**

<span data-ttu-id="5ed5c-609">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-609">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-610">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-610">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-611">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-611">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-612">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-612">200</span></span> | <span data-ttu-id="5ed5c-613">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-613">OK</span></span>
<span data-ttu-id="5ed5c-614">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-614">4XX</span></span> | <span data-ttu-id="5ed5c-615">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-615">Error codes</span></span>
<span data-ttu-id="5ed5c-616">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-616">5XX</span></span> | <span data-ttu-id="5ed5c-617">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-617">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-618">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-618">Available device families</span></span>**

* <span data-ttu-id="5ed5c-619">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-619">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-620">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-620">IoT</span></span>

---
### <a name="set-the-bugcheck-crash-control-settings"></a><span data-ttu-id="5ed5c-621">Festlegen der CrashControl-Fehlerüberprüfungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="5ed5c-621">Set the bugcheck crash control settings</span></span>

**<span data-ttu-id="5ed5c-622">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-622">Request</span></span>**

<span data-ttu-id="5ed5c-623">Mit dem folgenden Anforderungsformat können Sie die Einstellungen zum Sammeln von Fehlerüberprüfungsdaten festlegen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-623">You can set the settings for collecting bugcheck data by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-624">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-624">Method</span></span>      | <span data-ttu-id="5ed5c-625">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-625">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-626">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-626">POST</span></span> | <span data-ttu-id="5ed5c-627">/api/debug/dump/kernel/crashcontrol</span><span class="sxs-lookup"><span data-stu-id="5ed5c-627">/api/debug/dump/kernel/crashcontrol</span></span>
<br />

**<span data-ttu-id="5ed5c-628">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-628">URI parameters</span></span>**

<span data-ttu-id="5ed5c-629">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-629">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-630">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-630">URI parameter</span></span> | <span data-ttu-id="5ed5c-631">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-631">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-632">autoreboot</span><span class="sxs-lookup"><span data-stu-id="5ed5c-632">autoreboot</span></span>   | <span data-ttu-id="5ed5c-633">(**optional**) True oder False.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-633">(**optional**) True or false.</span></span> <span data-ttu-id="5ed5c-634">Dieser Parameter gibt an, ob das System nach einem Fehler oder Einfrieren automatisch neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-634">This indicates whether the system restarts automatically after it fails or locks.</span></span>
<span data-ttu-id="5ed5c-635">dumptype</span><span class="sxs-lookup"><span data-stu-id="5ed5c-635">dumptype</span></span>   | <span data-ttu-id="5ed5c-636">(**optional**) Der Speicherabbildtyp.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-636">(**optional**) The dump type.</span></span> <span data-ttu-id="5ed5c-637">Die unterstützten Werte finden Sie unter [CrashDumpType-Enumeration](https://msdn.microsoft.com/library/azure/microsoft.azure.management.insights.models.crashdumptype.aspx).</span><span class="sxs-lookup"><span data-stu-id="5ed5c-637">For the supported values, see the [CrashDumpType Enumeration](https://msdn.microsoft.com/library/azure/microsoft.azure.management.insights.models.crashdumptype.aspx).</span></span>
<span data-ttu-id="5ed5c-638">maxdumpcount</span><span class="sxs-lookup"><span data-stu-id="5ed5c-638">maxdumpcount</span></span>   | <span data-ttu-id="5ed5c-639">(**optional**) Die maximale Anzahl der zu speichernden Speicherabbilder.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-639">(**optional**) The maximum number of dumps to save.</span></span>
<span data-ttu-id="5ed5c-640">overwrite</span><span class="sxs-lookup"><span data-stu-id="5ed5c-640">overwrite</span></span>   | <span data-ttu-id="5ed5c-641">(**optional**) True oder False.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-641">(**optional**) True of false.</span></span> <span data-ttu-id="5ed5c-642">Dieser Parameter gibt an, ob alte Speicherabbilder überschrieben werden, wenn der durch *maxdumpcount* angegebene Höchstwert für die Anzahl von Speicherabbildern erreicht wurde.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-642">This indicates whether or not to overwrite old dumps when the dump counter limit specified by *maxdumpcount* has been reached.</span></span>
<br />
**<span data-ttu-id="5ed5c-643">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-643">Request headers</span></span>**

- <span data-ttu-id="5ed5c-644">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-644">None</span></span>

**<span data-ttu-id="5ed5c-645">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-645">Request body</span></span>**

- <span data-ttu-id="5ed5c-646">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-646">None</span></span>

**<span data-ttu-id="5ed5c-647">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-647">Response</span></span>**

**<span data-ttu-id="5ed5c-648">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-648">Status code</span></span>**

<span data-ttu-id="5ed5c-649">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-649">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-650">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-650">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-651">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-651">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-652">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-652">200</span></span> | <span data-ttu-id="5ed5c-653">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-653">OK</span></span>
<span data-ttu-id="5ed5c-654">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-654">4XX</span></span> | <span data-ttu-id="5ed5c-655">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-655">Error codes</span></span>
<span data-ttu-id="5ed5c-656">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-656">5XX</span></span> | <span data-ttu-id="5ed5c-657">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-657">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-658">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-658">Available device families</span></span>**

* <span data-ttu-id="5ed5c-659">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-659">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-660">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-660">IoT</span></span>

---
## ETW
---
### <a name="create-a-realtime-etw-session-over-a-websocket"></a><span data-ttu-id="5ed5c-661">Erstellen einer Echtzeit-ETW-Sitzung über ein Websocket</span><span class="sxs-lookup"><span data-stu-id="5ed5c-661">Create a realtime ETW session over a websocket</span></span>

**<span data-ttu-id="5ed5c-662">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-662">Request</span></span>**

<span data-ttu-id="5ed5c-663">Mit dem folgenden Anforderungsformat können Sie eine Echtzeit-ETW-Sitzung erstellen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-663">You can create a realtime ETW session by using the following request format.</span></span> <span data-ttu-id="5ed5c-664">Dies erfolgt über ein Websocket.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-664">This will be managed over a websocket.</span></span>  <span data-ttu-id="5ed5c-665">ETW-Ereignisse werden auf dem Server zusammengefasst und einmal pro Sekunde an den Client gesendet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-665">ETW events are batched on the server and sent to the client once per second.</span></span> 
 
<span data-ttu-id="5ed5c-666">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-666">Method</span></span>      | <span data-ttu-id="5ed5c-667">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-667">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-668">GET/WebSocket</span><span class="sxs-lookup"><span data-stu-id="5ed5c-668">GET/WebSocket</span></span> | <span data-ttu-id="5ed5c-669">/api/etw/session/realtime</span><span class="sxs-lookup"><span data-stu-id="5ed5c-669">/api/etw/session/realtime</span></span>
<br />

**<span data-ttu-id="5ed5c-670">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-670">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-671">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-671">None</span></span>

**<span data-ttu-id="5ed5c-672">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-672">Request headers</span></span>**

- <span data-ttu-id="5ed5c-673">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-673">None</span></span>

**<span data-ttu-id="5ed5c-674">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-674">Request body</span></span>**

- <span data-ttu-id="5ed5c-675">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-675">None</span></span>

**<span data-ttu-id="5ed5c-676">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-676">Response</span></span>**

<span data-ttu-id="5ed5c-677">Die Antwort enthält die ETW-Ereignisse von den aktivierten Anbietern.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-677">The response includes the ETW events from the enabled providers.</span></span>  <span data-ttu-id="5ed5c-678">ETW-WebSocket-Befehle finden Sie unten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-678">See ETW WebSocket commands below.</span></span> 

**<span data-ttu-id="5ed5c-679">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-679">Status code</span></span>**

<span data-ttu-id="5ed5c-680">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-680">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-681">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-681">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-682">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-682">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-683">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-683">200</span></span> | <span data-ttu-id="5ed5c-684">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-684">OK</span></span>
<span data-ttu-id="5ed5c-685">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-685">4XX</span></span> | <span data-ttu-id="5ed5c-686">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-686">Error codes</span></span>
<span data-ttu-id="5ed5c-687">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-687">5XX</span></span> | <span data-ttu-id="5ed5c-688">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-688">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-689">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-689">Available device families</span></span>**

* <span data-ttu-id="5ed5c-690">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-690">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-691">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-691">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-692">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-692">HoloLens</span></span>
* <span data-ttu-id="5ed5c-693">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-693">IoT</span></span>

### <a name="etw-websocket-commands"></a><span data-ttu-id="5ed5c-694">ETW-WebSocket-Befehle</span><span class="sxs-lookup"><span data-stu-id="5ed5c-694">ETW WebSocket commands</span></span>
<span data-ttu-id="5ed5c-695">Diese Befehle werden vom Client an den Server gesendet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-695">These commands are sent from the client to the server.</span></span>

<span data-ttu-id="5ed5c-696">Befehl</span><span class="sxs-lookup"><span data-stu-id="5ed5c-696">Command</span></span> | <span data-ttu-id="5ed5c-697">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-697">Description</span></span>
:----- | :-----
<span data-ttu-id="5ed5c-698">Anbieter *{guid}* aktivieren *{level}*</span><span class="sxs-lookup"><span data-stu-id="5ed5c-698">provider *{guid}* enable *{level}*</span></span> | <span data-ttu-id="5ed5c-699">Den durch *{guid}* (ohne Klammern) markierten Anbieter auf der angegebenen Ebene aktivieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-699">Enable the provider marked by *{guid}* (without brackets) at the specified level.</span></span> <span data-ttu-id="5ed5c-700">*{level}* ist ein **int** zwischen 1 (am wenigsten detailliert) und 5 (ausführlich).</span><span class="sxs-lookup"><span data-stu-id="5ed5c-700">*{level}* is an **int** from 1 (least detail) to 5 (verbose).</span></span>
<span data-ttu-id="5ed5c-701">Anbieter *{guid}* deaktivieren</span><span class="sxs-lookup"><span data-stu-id="5ed5c-701">provider *{guid}* disable</span></span> | <span data-ttu-id="5ed5c-702">Den durch *{guid}* (ohne Klammern) markierten Anbieter deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-702">Disable the provider marked by *{guid}* (without brackets).</span></span>

<span data-ttu-id="5ed5c-703">Diese Antworten werden vom Server an den Client gesendet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-703">This responses is sent from the server to the client.</span></span> <span data-ttu-id="5ed5c-704">Diese werden als Text gesendet, und erhalten Sie das folgende Format durch eine JSON-Analyse.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-704">This is sent as text and you get the following format by parsing the JSON.</span></span>
```
{
    "Events":[
        {
            "Timestamp": int,
            "ProviderName": string,
            "ID": int, 
            "TaskName": string,
            "Keyword": int,
            "Level": int,
            payload objects...
        },...
    ],
    "Frequency": int
}
```

<span data-ttu-id="5ed5c-705">Nutzlast-Objekte sind zusätzliche Schlüssel-Wert-Paare (Zeichenkette:Zeichenkette), die im ursprünglichen ETW-Ereignis bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-705">Payload objects are extra key-value pairs (string:string) that are provided in the original ETW event.</span></span>

<span data-ttu-id="5ed5c-706">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-706">Example:</span></span>
```
{
    "ID" : 42, 
    "Keyword" : 9223372036854775824, 
    "Level" : 4, 
    "Message" : "UDPv4: 412 bytes transmitted from 10.81.128.148:510 to 132.215.243.34:510. ",
    "PID" : "1218", 
    "ProviderName" : "Microsoft-Windows-Kernel-Network", 
    "TaskName" : "KERNEL_NETWORK_TASK_UDPIP", 
    "Timestamp" : 131039401761757686, 
    "connid" : "0", 
    "daddr" : "132.245.243.34", 
    "dport" : "500", 
    "saddr" : "10.82.128.118", 
    "seqnum" : "0", 
    "size" : "412", 
    "sport" : "500"
}
```

---
### <a name="enumerate-the-registered-etw-providers"></a><span data-ttu-id="5ed5c-707">Auflisten der registrierten ETW-Anbieter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-707">Enumerate the registered ETW providers</span></span>

**<span data-ttu-id="5ed5c-708">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-708">Request</span></span>**

<span data-ttu-id="5ed5c-709">Mit dem folgenden Anforderungsformat können Sie die registrierten Anbieter auflisten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-709">You can enumerate through the registered providers by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-710">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-710">Method</span></span>      | <span data-ttu-id="5ed5c-711">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-711">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-712">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-712">GET</span></span> | <span data-ttu-id="5ed5c-713">/api/etw/providers</span><span class="sxs-lookup"><span data-stu-id="5ed5c-713">/api/etw/providers</span></span>
<br />

**<span data-ttu-id="5ed5c-714">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-714">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-715">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-715">None</span></span>

**<span data-ttu-id="5ed5c-716">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-716">Request headers</span></span>**

- <span data-ttu-id="5ed5c-717">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-717">None</span></span>

**<span data-ttu-id="5ed5c-718">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-718">Request body</span></span>**

- <span data-ttu-id="5ed5c-719">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-719">None</span></span>

**<span data-ttu-id="5ed5c-720">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-720">Response</span></span>**

<span data-ttu-id="5ed5c-721">Die Antwort enthält die Liste der ETW-Anbieter.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-721">The response includes the list of ETW providers.</span></span> <span data-ttu-id="5ed5c-722">Diese Liste enthält den Anzeigenamen und die GUID für jeden Anbieter im folgenden Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-722">The list will include the friendly name and GUID for each provider in the following format.</span></span>
```
{"Providers": [
    {
        "GUID": string, (GUID)
        "Name": string
    },...
]}
```

**<span data-ttu-id="5ed5c-723">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-723">Status code</span></span>**

<span data-ttu-id="5ed5c-724">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-724">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-725">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-725">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-726">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-726">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-727">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-727">200</span></span> | <span data-ttu-id="5ed5c-728">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-728">OK</span></span>
<br />
**<span data-ttu-id="5ed5c-729">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-729">Available device families</span></span>**

* <span data-ttu-id="5ed5c-730">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-730">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-731">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-731">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-732">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-732">HoloLens</span></span>
* <span data-ttu-id="5ed5c-733">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-733">IoT</span></span>

---
### <a name="enumerate-the-custom-etw-providers-exposed-by-the-platform"></a><span data-ttu-id="5ed5c-734">Auflisten der benutzerdefinierten ETW-Anbieter, die von der Plattform verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-734">Enumerate the custom ETW providers exposed by the platform.</span></span>

**<span data-ttu-id="5ed5c-735">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-735">Request</span></span>**

<span data-ttu-id="5ed5c-736">Mit dem folgenden Anforderungsformat können Sie die registrierten Anbieter auflisten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-736">You can enumerate through the registered providers by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-737">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-737">Method</span></span>      | <span data-ttu-id="5ed5c-738">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-738">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-739">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-739">GET</span></span> | <span data-ttu-id="5ed5c-740">/api/etw/customproviders</span><span class="sxs-lookup"><span data-stu-id="5ed5c-740">/api/etw/customproviders</span></span>
<br />

**<span data-ttu-id="5ed5c-741">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-741">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-742">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-742">None</span></span>

**<span data-ttu-id="5ed5c-743">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-743">Request headers</span></span>**

- <span data-ttu-id="5ed5c-744">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-744">None</span></span>

**<span data-ttu-id="5ed5c-745">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-745">Request body</span></span>**

- <span data-ttu-id="5ed5c-746">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-746">None</span></span>

**<span data-ttu-id="5ed5c-747">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-747">Response</span></span>**

<span data-ttu-id="5ed5c-748">200 OK.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-748">200 OK.</span></span> <span data-ttu-id="5ed5c-749">Die Antwort enthält die Liste der ETW-Anbieter.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-749">The response includes the list of ETW providers.</span></span> <span data-ttu-id="5ed5c-750">Diese Liste enthält den Anzeigenamen und die GUID für jeden Anbieter.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-750">The list will include the friendly name and GUID for each provider.</span></span>

```
{"Providers": [
    {
        "GUID": string, (GUID)
        "Name": string
    },...
]}
```

**<span data-ttu-id="5ed5c-751">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-751">Status code</span></span>**

- <span data-ttu-id="5ed5c-752">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-752">Standard status codes.</span></span>
<br />
**<span data-ttu-id="5ed5c-753">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-753">Available device families</span></span>**

* <span data-ttu-id="5ed5c-754">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-754">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-755">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-755">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-756">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-756">HoloLens</span></span>
* <span data-ttu-id="5ed5c-757">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-757">IoT</span></span>

---
## OS information
---
### <a name="get-the-machine-name"></a><span data-ttu-id="5ed5c-758">Abrufen des Computernamens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-758">Get the machine name</span></span>

**<span data-ttu-id="5ed5c-759">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-759">Request</span></span>**

<span data-ttu-id="5ed5c-760">Sie können den Namen eines Computers durch Verwendung des folgenden Anforderungsformats abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-760">You can get the name of a machine by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-761">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-761">Method</span></span>      | <span data-ttu-id="5ed5c-762">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-762">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-763">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-763">GET</span></span> | <span data-ttu-id="5ed5c-764">/api/os/machinename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-764">/api/os/machinename</span></span>
<br />

**<span data-ttu-id="5ed5c-765">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-765">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-766">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-766">None</span></span>

**<span data-ttu-id="5ed5c-767">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-767">Request headers</span></span>**

- <span data-ttu-id="5ed5c-768">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-768">None</span></span>

**<span data-ttu-id="5ed5c-769">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-769">Request body</span></span>**

- <span data-ttu-id="5ed5c-770">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-770">None</span></span>

**<span data-ttu-id="5ed5c-771">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-771">Response</span></span>**

<span data-ttu-id="5ed5c-772">Die Antwort enthält den Namen des Computers im folgenden Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-772">The response includes the computer name in the following format.</span></span> 

```
{"ComputerName": string}
```

**<span data-ttu-id="5ed5c-773">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-773">Status code</span></span>**

<span data-ttu-id="5ed5c-774">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-774">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-775">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-775">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-776">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-776">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-777">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-777">200</span></span> | <span data-ttu-id="5ed5c-778">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-778">OK</span></span>
<span data-ttu-id="5ed5c-779">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-779">4XX</span></span> | <span data-ttu-id="5ed5c-780">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-780">Error codes</span></span>
<span data-ttu-id="5ed5c-781">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-781">5XX</span></span> | <span data-ttu-id="5ed5c-782">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-782">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-783">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-783">Available device families</span></span>**

* <span data-ttu-id="5ed5c-784">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-784">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-785">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-785">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-786">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-786">Xbox</span></span>
* <span data-ttu-id="5ed5c-787">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-787">HoloLens</span></span>
* <span data-ttu-id="5ed5c-788">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-788">IoT</span></span>

---
### <a name="get-the-operating-system-information"></a><span data-ttu-id="5ed5c-789">Abrufen der Betriebssysteminformationen</span><span class="sxs-lookup"><span data-stu-id="5ed5c-789">Get the operating system information</span></span>

**<span data-ttu-id="5ed5c-790">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-790">Request</span></span>**

<span data-ttu-id="5ed5c-791">Mit dem folgenden Anforderungsformat können Sie die Betriebssysteminformationen für einen Computer abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-791">You can get the OS information for a machine by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-792">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-792">Method</span></span>      | <span data-ttu-id="5ed5c-793">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-793">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-794">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-794">GET</span></span> | <span data-ttu-id="5ed5c-795">/api/os/info</span><span class="sxs-lookup"><span data-stu-id="5ed5c-795">/api/os/info</span></span>
<br />

**<span data-ttu-id="5ed5c-796">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-796">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-797">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-797">None</span></span>

**<span data-ttu-id="5ed5c-798">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-798">Request headers</span></span>**

- <span data-ttu-id="5ed5c-799">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-799">None</span></span>

**<span data-ttu-id="5ed5c-800">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-800">Request body</span></span>**

- <span data-ttu-id="5ed5c-801">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-801">None</span></span>

**<span data-ttu-id="5ed5c-802">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-802">Response</span></span>**

<span data-ttu-id="5ed5c-803">Die Antwort enthält die Betriebssysteminformationen im folgenden Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-803">The response includes the OS information in the following format.</span></span>

```
{
    "ComputerName": string,
    "OsEdition": string,
    "OsEditionId": int,
    "OsVersion": string,
    "Platform": string
}
```

**<span data-ttu-id="5ed5c-804">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-804">Status code</span></span>**

<span data-ttu-id="5ed5c-805">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-805">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-806">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-806">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-807">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-807">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-808">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-808">200</span></span> | <span data-ttu-id="5ed5c-809">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-809">OK</span></span>
<span data-ttu-id="5ed5c-810">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-810">4XX</span></span> | <span data-ttu-id="5ed5c-811">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-811">Error codes</span></span>
<span data-ttu-id="5ed5c-812">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-812">5XX</span></span> | <span data-ttu-id="5ed5c-813">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-813">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-814">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-814">Available device families</span></span>**

* <span data-ttu-id="5ed5c-815">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-815">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-816">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-816">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-817">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-817">Xbox</span></span>
* <span data-ttu-id="5ed5c-818">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-818">HoloLens</span></span>
* <span data-ttu-id="5ed5c-819">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-819">IoT</span></span>

---
### <a name="get-the-device-family"></a><span data-ttu-id="5ed5c-820">Abrufen der Gerätefamilie</span><span class="sxs-lookup"><span data-stu-id="5ed5c-820">Get the device family</span></span> 

**<span data-ttu-id="5ed5c-821">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-821">Request</span></span>**

<span data-ttu-id="5ed5c-822">Mit dem folgenden Anforderungsformat können Sie die Gerätefamilie (Xbox, Smartphone, Desktop usw.) abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-822">You can get the device family (Xbox, phone, desktop, etc) using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-823">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-823">Method</span></span>      | <span data-ttu-id="5ed5c-824">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-824">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-825">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-825">GET</span></span> | <span data-ttu-id="5ed5c-826">/api/os/devicefamily</span><span class="sxs-lookup"><span data-stu-id="5ed5c-826">/api/os/devicefamily</span></span>
<br />

**<span data-ttu-id="5ed5c-827">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-827">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-828">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-828">None</span></span>

**<span data-ttu-id="5ed5c-829">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-829">Request headers</span></span>**

- <span data-ttu-id="5ed5c-830">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-830">None</span></span>

**<span data-ttu-id="5ed5c-831">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-831">Request body</span></span>**

- <span data-ttu-id="5ed5c-832">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-832">None</span></span>

**<span data-ttu-id="5ed5c-833">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-833">Response</span></span>**

<span data-ttu-id="5ed5c-834">Die Antwort enthält die Gerätefamilie (SKU – Desktop, Xbox, usw.).</span><span class="sxs-lookup"><span data-stu-id="5ed5c-834">The response includes the device family (SKU - Desktop, Xbox, etc).</span></span>

```
{
   "DeviceType" : string
}
```

<span data-ttu-id="5ed5c-835">„DeviceType“ sieht wie folgt aus: „Windows.Xbox“, „Windows.Desktop“ usw.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-835">DeviceType will look like "Windows.Xbox", "Windows.Desktop", etc.</span></span> 

**<span data-ttu-id="5ed5c-836">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-836">Status code</span></span>**

<span data-ttu-id="5ed5c-837">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-837">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-838">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-838">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-839">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-839">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-840">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-840">200</span></span> | <span data-ttu-id="5ed5c-841">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-841">OK</span></span>
<span data-ttu-id="5ed5c-842">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-842">4XX</span></span> | <span data-ttu-id="5ed5c-843">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-843">Error codes</span></span>
<span data-ttu-id="5ed5c-844">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-844">5XX</span></span> | <span data-ttu-id="5ed5c-845">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-845">Error codes</span></span>

**<span data-ttu-id="5ed5c-846">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-846">Available device families</span></span>**

* <span data-ttu-id="5ed5c-847">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-847">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-848">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-848">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-849">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-849">Xbox</span></span>
* <span data-ttu-id="5ed5c-850">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-850">HoloLens</span></span>
* <span data-ttu-id="5ed5c-851">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-851">IoT</span></span>

---
### <a name="set-the-machine-name"></a><span data-ttu-id="5ed5c-852">Festlegen des Computernamens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-852">Set the machine name</span></span>

**<span data-ttu-id="5ed5c-853">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-853">Request</span></span>**

<span data-ttu-id="5ed5c-854">Mit dem folgenden Anforderungsformat können Sie den Namen eines Computers festlegen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-854">You can set the name of a machine by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-855">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-855">Method</span></span>      | <span data-ttu-id="5ed5c-856">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-856">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-857">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-857">POST</span></span> | <span data-ttu-id="5ed5c-858">/api/os/machinename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-858">/api/os/machinename</span></span>
<br />

**<span data-ttu-id="5ed5c-859">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-859">URI parameters</span></span>**

<span data-ttu-id="5ed5c-860">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-860">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-861">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-861">URI parameter</span></span> | <span data-ttu-id="5ed5c-862">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-862">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-863">name</span><span class="sxs-lookup"><span data-stu-id="5ed5c-863">name</span></span> | <span data-ttu-id="5ed5c-864">(**erforderlich**) Der neue Name für den Computer.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-864">(**required**) The new name for the machine.</span></span>
<br />
**<span data-ttu-id="5ed5c-865">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-865">Request headers</span></span>**

- <span data-ttu-id="5ed5c-866">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-866">None</span></span>

**<span data-ttu-id="5ed5c-867">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-867">Request body</span></span>**

- <span data-ttu-id="5ed5c-868">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-868">None</span></span>

**<span data-ttu-id="5ed5c-869">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-869">Response</span></span>**

**<span data-ttu-id="5ed5c-870">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-870">Status code</span></span>**

<span data-ttu-id="5ed5c-871">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-871">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-872">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-872">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-873">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-873">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-874">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-874">200</span></span> | <span data-ttu-id="5ed5c-875">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-875">OK</span></span>
<br />
**<span data-ttu-id="5ed5c-876">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-876">Available device families</span></span>**

* <span data-ttu-id="5ed5c-877">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-877">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-878">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-878">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-879">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-879">Xbox</span></span>
* <span data-ttu-id="5ed5c-880">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-880">HoloLens</span></span>
* <span data-ttu-id="5ed5c-881">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-881">IoT</span></span>

---
## User information
---
### <a name="get-the-active-user"></a><span data-ttu-id="5ed5c-882">Aktiven Benutzer ermitteln</span><span class="sxs-lookup"><span data-stu-id="5ed5c-882">Get the active user</span></span>

**<span data-ttu-id="5ed5c-883">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-883">Request</span></span>**

<span data-ttu-id="5ed5c-884">Mit dem folgenden Anforderungsformat können Sie den Namen des aktiven Gerätebenutzers abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-884">You can get the name of the active user on the device by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-885">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-885">Method</span></span>      | <span data-ttu-id="5ed5c-886">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-886">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-887">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-887">GET</span></span> | <span data-ttu-id="5ed5c-888">/api/users/activeuser</span><span class="sxs-lookup"><span data-stu-id="5ed5c-888">/api/users/activeuser</span></span>
<br />

**<span data-ttu-id="5ed5c-889">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-889">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-890">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-890">None</span></span>

**<span data-ttu-id="5ed5c-891">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-891">Request headers</span></span>**

- <span data-ttu-id="5ed5c-892">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-892">None</span></span>

**<span data-ttu-id="5ed5c-893">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-893">Request body</span></span>**

- <span data-ttu-id="5ed5c-894">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-894">None</span></span>

**<span data-ttu-id="5ed5c-895">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-895">Response</span></span>**

<span data-ttu-id="5ed5c-896">Die Antwort enthält Benutzerinformationen im folgenden Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-896">The response includes user information in the following format.</span></span> 

<span data-ttu-id="5ed5c-897">Bei Erfolg:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-897">On success:</span></span> 
```
{
    "UserDisplayName" : string, 
    "UserSID" : string
}
```
<span data-ttu-id="5ed5c-898">Bei Misserfolg:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-898">On failure:</span></span>
```
{
    "Code" : int, 
    "CodeText" : string, 
    "Reason" : string, 
    "Success" : bool
}
```

**<span data-ttu-id="5ed5c-899">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-899">Status code</span></span>**

<span data-ttu-id="5ed5c-900">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-900">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-901">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-901">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-902">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-902">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-903">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-903">200</span></span> | <span data-ttu-id="5ed5c-904">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-904">OK</span></span>
<span data-ttu-id="5ed5c-905">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-905">4XX</span></span> | <span data-ttu-id="5ed5c-906">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-906">Error codes</span></span>
<span data-ttu-id="5ed5c-907">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-907">5XX</span></span> | <span data-ttu-id="5ed5c-908">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-908">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-909">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-909">Available device families</span></span>**

* <span data-ttu-id="5ed5c-910">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-910">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-911">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-911">HoloLens</span></span>
* <span data-ttu-id="5ed5c-912">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-912">IoT</span></span>

---
## Performance data
---
### <a name="get-the-list-of-running-processes"></a><span data-ttu-id="5ed5c-913">Abrufen der Liste der ausgeführten Prozesse</span><span class="sxs-lookup"><span data-stu-id="5ed5c-913">Get the list of running processes</span></span>

**<span data-ttu-id="5ed5c-914">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-914">Request</span></span>**

<span data-ttu-id="5ed5c-915">Mit dem folgenden Anforderungsformat können Sie die Liste der derzeit ausgeführten Prozesse abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-915">You can get the list of currently running processes by using the following request format.</span></span>  <span data-ttu-id="5ed5c-916">Dies kann auch zu einer WebSocket-Verbindung aktualisiert werden, wobei einmal pro Sekunde die gleichen JSON-Daten per Push an den Client gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-916">this can be upgraded to a WebSocket connection as well, with the same JSON data being pushed to the client once per second.</span></span> 
 
<span data-ttu-id="5ed5c-917">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-917">Method</span></span>      | <span data-ttu-id="5ed5c-918">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-918">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-919">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-919">GET</span></span> | <span data-ttu-id="5ed5c-920">/api/resourcemanager/processes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-920">/api/resourcemanager/processes</span></span>
<span data-ttu-id="5ed5c-921">GET/WebSocket</span><span class="sxs-lookup"><span data-stu-id="5ed5c-921">GET/WebSocket</span></span> | <span data-ttu-id="5ed5c-922">/api/resourcemanager/processes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-922">/api/resourcemanager/processes</span></span>
<br />

**<span data-ttu-id="5ed5c-923">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-923">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-924">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-924">None</span></span>

**<span data-ttu-id="5ed5c-925">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-925">Request headers</span></span>**

- <span data-ttu-id="5ed5c-926">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-926">None</span></span>

**<span data-ttu-id="5ed5c-927">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-927">Request body</span></span>**

- <span data-ttu-id="5ed5c-928">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-928">None</span></span>

**<span data-ttu-id="5ed5c-929">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-929">Response</span></span>**

<span data-ttu-id="5ed5c-930">Die Antwort enthält eine Liste der Prozesse mit Details für jeden Prozess.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-930">The response includes a list of processes with details for each process.</span></span> <span data-ttu-id="5ed5c-931">Die Informationen sind im JSON-Format und haben die folgende Vorlage.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-931">The information is in JSON format and has the following template.</span></span>
```
{"Processes": [
    {
        "CPUUsage": int,
        "ImageName": string,
        "PageFileUsage": int,
        "PrivateWorkingSet": int,
        "ProcessId": int,
        "SessionId": int,
        "UserName": string,
        "VirtualSize": int,
        "WorkingSetSize": int
    },...
]}
```

**<span data-ttu-id="5ed5c-932">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-932">Status code</span></span>**

<span data-ttu-id="5ed5c-933">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-933">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-934">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-934">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-935">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-935">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-936">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-936">200</span></span> | <span data-ttu-id="5ed5c-937">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-937">OK</span></span>
<span data-ttu-id="5ed5c-938">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-938">4XX</span></span> | <span data-ttu-id="5ed5c-939">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-939">Error codes</span></span>
<span data-ttu-id="5ed5c-940">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-940">5XX</span></span> | <span data-ttu-id="5ed5c-941">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-941">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-942">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-942">Available device families</span></span>**

* <span data-ttu-id="5ed5c-943">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-943">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-944">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-944">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-945">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-945">HoloLens</span></span>
* <span data-ttu-id="5ed5c-946">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-946">IoT</span></span>

---
### <a name="get-the-system-performance-statistics"></a><span data-ttu-id="5ed5c-947">Abrufen der Leistungsstatistik des Systems</span><span class="sxs-lookup"><span data-stu-id="5ed5c-947">Get the system performance statistics</span></span>

**<span data-ttu-id="5ed5c-948">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-948">Request</span></span>**

<span data-ttu-id="5ed5c-949">Mit dem folgenden Anforderungsformat können Sie die Leistungsstatistik des Systems abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-949">You can get the system performance statistics by using the following request format.</span></span> <span data-ttu-id="5ed5c-950">Diese Informationen umfassen z. B. Lese- und Schreibzyklen sowie die Menge des genutzten Arbeitsspeichers.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-950">This includes information such as read and write cycles and how much memory has been used.</span></span>
 
<span data-ttu-id="5ed5c-951">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-951">Method</span></span>      | <span data-ttu-id="5ed5c-952">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-952">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-953">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-953">GET</span></span> | <span data-ttu-id="5ed5c-954">/api/resourcemanager/systemperf</span><span class="sxs-lookup"><span data-stu-id="5ed5c-954">/api/resourcemanager/systemperf</span></span>
<span data-ttu-id="5ed5c-955">GET/WebSocket</span><span class="sxs-lookup"><span data-stu-id="5ed5c-955">GET/WebSocket</span></span> | <span data-ttu-id="5ed5c-956">/api/resourcemanager/systemperf</span><span class="sxs-lookup"><span data-stu-id="5ed5c-956">/api/resourcemanager/systemperf</span></span>
<br />
<span data-ttu-id="5ed5c-957">Dies kann auch auf eine WebSocket-Verbindung aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-957">This can also be upgraded to a WebSocket connection.</span></span>  <span data-ttu-id="5ed5c-958">Sie stellt unten einmal pro Sekunde die gleichen JSON-Daten bereit.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-958">It provides the same JSON data below once every second.</span></span> 

**<span data-ttu-id="5ed5c-959">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-959">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-960">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-960">None</span></span>

**<span data-ttu-id="5ed5c-961">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-961">Request headers</span></span>**

- <span data-ttu-id="5ed5c-962">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-962">None</span></span>

**<span data-ttu-id="5ed5c-963">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-963">Request body</span></span>**

- <span data-ttu-id="5ed5c-964">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-964">None</span></span>

**<span data-ttu-id="5ed5c-965">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-965">Response</span></span>**

<span data-ttu-id="5ed5c-966">Die Antwort enthält die Leistungsstatistik für das System, z. B. CPU- und GPU-Nutzung, Speicherzugriff und Netzwerkzugriff.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-966">The response includes the performance statistics for the system such as CPU and GPU usage, memory access, and network access.</span></span> <span data-ttu-id="5ed5c-967">Diese Informationen sind im JSON-Format und haben die folgende Vorlage.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-967">This information is in JSON format and has the following template.</span></span>
```
{
    "AvailablePages": int,
    "CommitLimit": int,
    "CommittedPages": int,
    "CpuLoad": int,
    "IOOtherSpeed": int,
    "IOReadSpeed": int,
    "IOWriteSpeed": int,
    "NonPagedPoolPages": int,
    "PageSize": int,
    "PagedPoolPages": int,
    "TotalInstalledInKb": int,
    "TotalPages": int,
    "GPUData": 
    {
        "AvailableAdapters": [{ (One per detected adapter)
            "DedicatedMemory": int,
            "DedicatedMemoryUsed": int,
            "Description": string,
            "SystemMemory": int,
            "SystemMemoryUsed": int,
            "EnginesUtilization": [ float,... (One per detected engine)]
        },...
    ]},
    "NetworkingData": {
        "NetworkInBytes": int,
        "NetworkOutBytes": int
    }
}
```

**<span data-ttu-id="5ed5c-968">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-968">Status code</span></span>**

<span data-ttu-id="5ed5c-969">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-969">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-970">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-970">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-971">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-971">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-972">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-972">200</span></span> | <span data-ttu-id="5ed5c-973">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-973">OK</span></span>
<span data-ttu-id="5ed5c-974">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-974">4XX</span></span> | <span data-ttu-id="5ed5c-975">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-975">Error codes</span></span>
<span data-ttu-id="5ed5c-976">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-976">5XX</span></span> | <span data-ttu-id="5ed5c-977">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-977">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-978">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-978">Available device families</span></span>**

* <span data-ttu-id="5ed5c-979">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-979">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-980">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-980">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-981">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-981">Xbox</span></span>
* <span data-ttu-id="5ed5c-982">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-982">HoloLens</span></span>
* <span data-ttu-id="5ed5c-983">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-983">IoT</span></span>

---
## Power
---
### <a name="get-the-current-battery-state"></a><span data-ttu-id="5ed5c-984">Abrufen des aktuellen Akkustatus</span><span class="sxs-lookup"><span data-stu-id="5ed5c-984">Get the current battery state</span></span>

**<span data-ttu-id="5ed5c-985">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-985">Request</span></span>**

<span data-ttu-id="5ed5c-986">Mit dem folgenden Anforderungsformat können Sie den aktuellen Akkustatus abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-986">You can get the current state of the battery by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-987">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-987">Method</span></span>      | <span data-ttu-id="5ed5c-988">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-988">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-989">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-989">GET</span></span> | <span data-ttu-id="5ed5c-990">/api/power/battery</span><span class="sxs-lookup"><span data-stu-id="5ed5c-990">/api/power/battery</span></span>
<br />

**<span data-ttu-id="5ed5c-991">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-991">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-992">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-992">None</span></span>

**<span data-ttu-id="5ed5c-993">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-993">Request headers</span></span>**

- <span data-ttu-id="5ed5c-994">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-994">None</span></span>

**<span data-ttu-id="5ed5c-995">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-995">Request body</span></span>**

- <span data-ttu-id="5ed5c-996">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-996">None</span></span>

**<span data-ttu-id="5ed5c-997">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-997">Response</span></span>**

<span data-ttu-id="5ed5c-998">Die Informationen zum aktuellen Akkustatus werden im folgenden Format zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-998">The current battery state information is returned using the following format.</span></span>
```
{
    "AcOnline": int (0 | 1),
    "BatteryPresent": int (0 | 1),
    "Charging": int (0 | 1),
    "DefaultAlert1": int,
    "DefaultAlert2": int,
    "EstimatedTime": int,
    "MaximumCapacity": int,
    "RemainingCapacity": int
}
```

**<span data-ttu-id="5ed5c-999">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-999">Status code</span></span>**

<span data-ttu-id="5ed5c-1000">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1000">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1001">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1001">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1002">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1002">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1003">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1003">200</span></span> | <span data-ttu-id="5ed5c-1004">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1004">OK</span></span>
<span data-ttu-id="5ed5c-1005">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1005">4XX</span></span> | <span data-ttu-id="5ed5c-1006">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1006">Error codes</span></span>
<span data-ttu-id="5ed5c-1007">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1007">5XX</span></span> | <span data-ttu-id="5ed5c-1008">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1008">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1009">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1009">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1010">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1010">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1011">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1011">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1012">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1012">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1013">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1013">IoT</span></span>

---
### <a name="get-the-active-power-scheme"></a><span data-ttu-id="5ed5c-1014">Abrufen des aktiven Energieschemas</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1014">Get the active power scheme</span></span>

**<span data-ttu-id="5ed5c-1015">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1015">Request</span></span>**

<span data-ttu-id="5ed5c-1016">Mit dem folgenden Anforderungsformat können Sie das aktive Energieschema abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1016">You can get the active power scheme by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1017">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1017">Method</span></span>      | <span data-ttu-id="5ed5c-1018">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1018">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1019">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1019">GET</span></span> | <span data-ttu-id="5ed5c-1020">/api/power/activecfg</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1020">/api/power/activecfg</span></span>
<br />

**<span data-ttu-id="5ed5c-1021">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1021">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1022">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1022">None</span></span>

**<span data-ttu-id="5ed5c-1023">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1023">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1024">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1024">None</span></span>

**<span data-ttu-id="5ed5c-1025">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1025">Request body</span></span>**

- <span data-ttu-id="5ed5c-1026">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1026">None</span></span>

**<span data-ttu-id="5ed5c-1027">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1027">Response</span></span>**

<span data-ttu-id="5ed5c-1028">Das aktive Energieschema hat das folgende Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1028">The active power scheme has the following format.</span></span>
```
{"ActivePowerScheme": string (guid of scheme)}
```

**<span data-ttu-id="5ed5c-1029">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1029">Status code</span></span>**

<span data-ttu-id="5ed5c-1030">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1030">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1031">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1031">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1032">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1032">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1033">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1033">200</span></span> | <span data-ttu-id="5ed5c-1034">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1034">OK</span></span>
<span data-ttu-id="5ed5c-1035">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1035">4XX</span></span> | <span data-ttu-id="5ed5c-1036">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1036">Error codes</span></span>
<span data-ttu-id="5ed5c-1037">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1037">5XX</span></span> | <span data-ttu-id="5ed5c-1038">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1038">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1039">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1039">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1040">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1040">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1041">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1041">IoT</span></span>

---
### <a name="get-the-sub-value-for-a-power-scheme"></a><span data-ttu-id="5ed5c-1042">Abrufen des Unterwerts für ein Energieschema</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1042">Get the sub-value for a power scheme</span></span>

**<span data-ttu-id="5ed5c-1043">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1043">Request</span></span>**

<span data-ttu-id="5ed5c-1044">Mit dem folgenden Anforderungsformat können Sie den Unterwert für ein Energieschema abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1044">You can get the sub-value for a power scheme by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1045">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1045">Method</span></span>      | <span data-ttu-id="5ed5c-1046">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1046">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1047">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1047">GET</span></span> | <span data-ttu-id="5ed5c-1048">/api/power/cfg/*<power scheme path>*</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1048">/api/power/cfg/*<power scheme path>*</span></span>
<br />
<span data-ttu-id="5ed5c-1049">Optionen:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1049">Options:</span></span>
- <span data-ttu-id="5ed5c-1050">SCHEME_CURRENT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1050">SCHEME_CURRENT</span></span>

**<span data-ttu-id="5ed5c-1051">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1051">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1052">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1052">None</span></span>

**<span data-ttu-id="5ed5c-1053">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1053">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1054">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1054">None</span></span>

**<span data-ttu-id="5ed5c-1055">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1055">Request body</span></span>**

<span data-ttu-id="5ed5c-1056">Eine vollständige Liste der verfügbaren Energiezustände ist auf einzelne Anwendungen bezogen und enthält die Einstellungen zur Kennzeichnung verschiedener Energiezustände wie niedriger und kritischer Ladezustand.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1056">A full listing of power states available is on a per-application basis and the settings for flagging various power states like low and critical batterty.</span></span> 

**<span data-ttu-id="5ed5c-1057">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1057">Response</span></span>**

**<span data-ttu-id="5ed5c-1058">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1058">Status code</span></span>**

<span data-ttu-id="5ed5c-1059">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1059">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1060">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1060">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1061">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1061">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1062">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1062">200</span></span> | <span data-ttu-id="5ed5c-1063">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1063">OK</span></span>
<span data-ttu-id="5ed5c-1064">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1064">4XX</span></span> | <span data-ttu-id="5ed5c-1065">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1065">Error codes</span></span>
<span data-ttu-id="5ed5c-1066">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1066">5XX</span></span> | <span data-ttu-id="5ed5c-1067">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1067">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1068">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1068">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1069">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1069">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1070">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1070">IoT</span></span>

---
### <a name="get-the-power-state-of-the-system"></a><span data-ttu-id="5ed5c-1071">Abrufen des Energiestatus des Systems</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1071">Get the power state of the system</span></span>

**<span data-ttu-id="5ed5c-1072">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1072">Request</span></span>**

<span data-ttu-id="5ed5c-1073">Mit dem folgenden Anforderungsformat können Sie den Energiestatus des Systems überprüfen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1073">You can check the power state of the system by using the following request format.</span></span> <span data-ttu-id="5ed5c-1074">So können Sie überprüfen, ob es sich im Energiesparmodus befindet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1074">This will let you check to see if it is in a low power state.</span></span>
 
<span data-ttu-id="5ed5c-1075">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1075">Method</span></span>      | <span data-ttu-id="5ed5c-1076">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1076">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1077">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1077">GET</span></span> | <span data-ttu-id="5ed5c-1078">/api/power/state</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1078">/api/power/state</span></span>
<br />

**<span data-ttu-id="5ed5c-1079">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1079">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1080">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1080">None</span></span>

**<span data-ttu-id="5ed5c-1081">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1081">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1082">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1082">None</span></span>

**<span data-ttu-id="5ed5c-1083">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1083">Request body</span></span>**

- <span data-ttu-id="5ed5c-1084">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1084">None</span></span>

**<span data-ttu-id="5ed5c-1085">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1085">Response</span></span>**

<span data-ttu-id="5ed5c-1086">Die Informationen zum Energiezustand haben die folgende Vorlage.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1086">The power state information has the following template.</span></span>
```
{"LowPowerStateAvailable": bool}
```

**<span data-ttu-id="5ed5c-1087">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1087">Status code</span></span>**

<span data-ttu-id="5ed5c-1088">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1088">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1089">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1089">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1090">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1090">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1091">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1091">200</span></span> | <span data-ttu-id="5ed5c-1092">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1092">OK</span></span>
<span data-ttu-id="5ed5c-1093">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1093">4XX</span></span> | <span data-ttu-id="5ed5c-1094">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1094">Error codes</span></span>
<span data-ttu-id="5ed5c-1095">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1095">5XX</span></span> | <span data-ttu-id="5ed5c-1096">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1096">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1097">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1097">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1098">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1098">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1099">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1099">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1100">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1100">IoT</span></span>

---
### <a name="set-the-active-power-scheme"></a><span data-ttu-id="5ed5c-1101">Festlegen des aktiven Energieschemas</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1101">Set the active power scheme</span></span>

**<span data-ttu-id="5ed5c-1102">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1102">Request</span></span>**

<span data-ttu-id="5ed5c-1103">Mit dem folgenden Anforderungsformat können Sie das aktive Energieschema festlegen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1103">You can set the active power scheme by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1104">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1104">Method</span></span>      | <span data-ttu-id="5ed5c-1105">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1105">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1106">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1106">POST</span></span> | <span data-ttu-id="5ed5c-1107">/api/power/activecfg</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1107">/api/power/activecfg</span></span>
<br />

**<span data-ttu-id="5ed5c-1108">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1108">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1109">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1109">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1110">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1110">URI parameter</span></span> | <span data-ttu-id="5ed5c-1111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1111">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1112">scheme</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1112">scheme</span></span> | <span data-ttu-id="5ed5c-1113">(**erforderlich**) Die GUID des Schemas, das Sie als das aktive Energieschema für das System festlegen möchten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1113">(**required**) The GUID of the scheme you want to set as the active power scheme for the system.</span></span>
<br />
**<span data-ttu-id="5ed5c-1114">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1114">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1115">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1115">None</span></span>

**<span data-ttu-id="5ed5c-1116">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1116">Request body</span></span>**

- <span data-ttu-id="5ed5c-1117">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1117">None</span></span>

**<span data-ttu-id="5ed5c-1118">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1118">Response</span></span>**

**<span data-ttu-id="5ed5c-1119">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1119">Status code</span></span>**

<span data-ttu-id="5ed5c-1120">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1120">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1121">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1121">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1122">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1123">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1123">200</span></span> | <span data-ttu-id="5ed5c-1124">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1124">OK</span></span>
<span data-ttu-id="5ed5c-1125">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1125">4XX</span></span> | <span data-ttu-id="5ed5c-1126">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1126">Error codes</span></span>
<span data-ttu-id="5ed5c-1127">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1127">5XX</span></span> | <span data-ttu-id="5ed5c-1128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1128">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1129">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1129">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1130">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1130">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1131">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1131">IoT</span></span>

---
### <a name="set-the-sub-value-for-a-power-scheme"></a><span data-ttu-id="5ed5c-1132">Festlegen des Unterwerts für ein Energieschema</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1132">Set the sub-value for a power scheme</span></span>

**<span data-ttu-id="5ed5c-1133">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1133">Request</span></span>**

<span data-ttu-id="5ed5c-1134">Mit dem folgenden Anforderungsformat können Sie den Unterwert für ein Energieschema festlegen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1134">You can set the sub-value for a power scheme by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1135">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1135">Method</span></span>      | <span data-ttu-id="5ed5c-1136">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1136">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1137">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1137">POST</span></span> | <span data-ttu-id="5ed5c-1138">/api/power/cfg/*<power scheme path>*</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1138">/api/power/cfg/*<power scheme path>*</span></span>
<br />

**<span data-ttu-id="5ed5c-1139">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1139">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1140">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1140">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1141">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1141">URI parameter</span></span> | <span data-ttu-id="5ed5c-1142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1142">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1143">valueAC</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1143">valueAC</span></span> | <span data-ttu-id="5ed5c-1144">(**erforderlich**) Der für den Netzbetrieb zu verwendende Wert.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1144">(**required**) The value to use for A/C power.</span></span>
<span data-ttu-id="5ed5c-1145">valueDC</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1145">valueDC</span></span> | <span data-ttu-id="5ed5c-1146">(**erforderlich**) Der für den Akkubetrieb zu verwendende Wert.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1146">(**required**) The value to use for battery power.</span></span>
<br />
**<span data-ttu-id="5ed5c-1147">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1147">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1148">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1148">None</span></span>

**<span data-ttu-id="5ed5c-1149">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1149">Request body</span></span>**

- <span data-ttu-id="5ed5c-1150">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1150">None</span></span>

**<span data-ttu-id="5ed5c-1151">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1151">Response</span></span>**

**<span data-ttu-id="5ed5c-1152">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1152">Status code</span></span>**

<span data-ttu-id="5ed5c-1153">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1153">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1154">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1154">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1155">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1156">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1156">200</span></span> | <span data-ttu-id="5ed5c-1157">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1157">OK</span></span>
<br />
**<span data-ttu-id="5ed5c-1158">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1158">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1159">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1159">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1160">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1160">IoT</span></span>

---
### <a name="get-a-sleep-study-report"></a><span data-ttu-id="5ed5c-1161">Abrufen eines Berichts zur Ruhezustandsuntersuchung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1161">Get a sleep study report</span></span>

**<span data-ttu-id="5ed5c-1162">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1162">Request</span></span>**

<span data-ttu-id="5ed5c-1163">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1163">Method</span></span>      | <span data-ttu-id="5ed5c-1164">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1164">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1165">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1165">GET</span></span> | <span data-ttu-id="5ed5c-1166">/api/power/sleepstudy/report</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1166">/api/power/sleepstudy/report</span></span>
<br />
<span data-ttu-id="5ed5c-1167">Mit dem folgenden Anforderungsformat können Sie einen Bericht zur Ruhezustandsuntersuchung abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1167">You can get a sleep study report by using the following request format.</span></span>

**<span data-ttu-id="5ed5c-1168">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1168">URI parameters</span></span>**
<span data-ttu-id="5ed5c-1169">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1169">URI parameter</span></span> | <span data-ttu-id="5ed5c-1170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1170">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1171">FileName</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1171">FileName</span></span> | <span data-ttu-id="5ed5c-1172">(**erforderlich**) Der vollständige Name für die Datei, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1172">(**required**) The full name for the file you want to download.</span></span> <span data-ttu-id="5ed5c-1173">Dieser Wert sollte hex64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1173">This value should be hex64 encoded.</span></span>
<br />
**<span data-ttu-id="5ed5c-1174">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1174">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1175">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1175">None</span></span>

**<span data-ttu-id="5ed5c-1176">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1176">Request body</span></span>**

- <span data-ttu-id="5ed5c-1177">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1177">None</span></span>

**<span data-ttu-id="5ed5c-1178">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1178">Response</span></span>**

<span data-ttu-id="5ed5c-1179">Die Antwort ist eine Datei mit der Ruhezustandsuntersuchung.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1179">The response is a file containing the sleep study.</span></span> 

**<span data-ttu-id="5ed5c-1180">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1180">Status code</span></span>**

<span data-ttu-id="5ed5c-1181">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1181">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1182">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1182">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1183">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1183">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1184">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1184">200</span></span> | <span data-ttu-id="5ed5c-1185">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1185">OK</span></span>
<span data-ttu-id="5ed5c-1186">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1186">4XX</span></span> | <span data-ttu-id="5ed5c-1187">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1187">Error codes</span></span>
<span data-ttu-id="5ed5c-1188">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1188">5XX</span></span> | <span data-ttu-id="5ed5c-1189">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1189">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1190">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1190">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1191">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1191">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1192">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1192">IoT</span></span>

---
### <a name="enumerate-the-available-sleep-study-reports"></a><span data-ttu-id="5ed5c-1193">Auflisten der verfügbaren Berichte zu Ruhezustandsuntersuchungen</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1193">Enumerate the available sleep study reports</span></span>

**<span data-ttu-id="5ed5c-1194">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1194">Request</span></span>**

<span data-ttu-id="5ed5c-1195">Mit dem folgenden Anforderungsformat können Sie die verfügbaren Berichte zu Ruhezustandsuntersuchungen auflisten</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1195">You can enumerate the available sleep study reports by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1196">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1196">Method</span></span>      | <span data-ttu-id="5ed5c-1197">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1197">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1198">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1198">GET</span></span> | <span data-ttu-id="5ed5c-1199">/api/power/sleepstudy/reports</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1199">/api/power/sleepstudy/reports</span></span>
<br />

**<span data-ttu-id="5ed5c-1200">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1200">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1201">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1201">None</span></span>

**<span data-ttu-id="5ed5c-1202">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1202">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1203">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1203">None</span></span>

**<span data-ttu-id="5ed5c-1204">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1204">Request body</span></span>**

- <span data-ttu-id="5ed5c-1205">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1205">None</span></span>

**<span data-ttu-id="5ed5c-1206">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1206">Response</span></span>**

<span data-ttu-id="5ed5c-1207">Die Liste der verfügbaren Berichte hat die folgende Vorlage.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1207">The list of available reports has the following template.</span></span>

```
{"Reports": [
    {
        "FileName": string
    },...
]}
```

**<span data-ttu-id="5ed5c-1208">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1208">Status code</span></span>**

<span data-ttu-id="5ed5c-1209">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1209">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1210">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1210">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1211">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1211">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1212">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1212">200</span></span> | <span data-ttu-id="5ed5c-1213">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1213">OK</span></span>
<span data-ttu-id="5ed5c-1214">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1214">4XX</span></span> | <span data-ttu-id="5ed5c-1215">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1215">Error codes</span></span>
<span data-ttu-id="5ed5c-1216">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1216">5XX</span></span> | <span data-ttu-id="5ed5c-1217">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1217">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1218">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1218">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1219">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1219">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1220">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1220">IoT</span></span>

---
### <a name="get-the-sleep-study-transform"></a><span data-ttu-id="5ed5c-1221">Abrufen der Transformation der Ruhezustandsuntersuchung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1221">Get the sleep study transform</span></span>

**<span data-ttu-id="5ed5c-1222">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1222">Request</span></span>**

<span data-ttu-id="5ed5c-1223">Mit dem folgenden Anforderungsformat können Sie die Transformation der Ruhezustandsuntersuchung abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1223">You can get the sleep study transform by using the following request format.</span></span> <span data-ttu-id="5ed5c-1224">Diese Transformation ist eine XSLT-Datei, die den Bericht zur Ruhezustandsuntersuchung in ein lesbares XML-Format konvertiert.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1224">This transform is an XSLT that converts the sleep study report into an XML format that can be read by a person.</span></span>
 
<span data-ttu-id="5ed5c-1225">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1225">Method</span></span>      | <span data-ttu-id="5ed5c-1226">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1226">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1227">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1227">GET</span></span> | <span data-ttu-id="5ed5c-1228">/api/power/sleepstudy/transform</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1228">/api/power/sleepstudy/transform</span></span>
<br />

**<span data-ttu-id="5ed5c-1229">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1229">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1230">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1230">None</span></span>

**<span data-ttu-id="5ed5c-1231">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1231">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1232">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1232">None</span></span>

**<span data-ttu-id="5ed5c-1233">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1233">Request body</span></span>**

- <span data-ttu-id="5ed5c-1234">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1234">None</span></span>

**<span data-ttu-id="5ed5c-1235">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1235">Response</span></span>**

<span data-ttu-id="5ed5c-1236">Die Antwort enthält die Transformation der Ruhezustandsuntersuchung.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1236">The response contains the sleep study transform.</span></span>

**<span data-ttu-id="5ed5c-1237">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1237">Status code</span></span>**

<span data-ttu-id="5ed5c-1238">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1238">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1239">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1239">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1240">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1240">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1241">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1241">200</span></span> | <span data-ttu-id="5ed5c-1242">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1242">OK</span></span>
<span data-ttu-id="5ed5c-1243">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1243">4XX</span></span> | <span data-ttu-id="5ed5c-1244">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1244">Error codes</span></span>
<span data-ttu-id="5ed5c-1245">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1245">5XX</span></span> | <span data-ttu-id="5ed5c-1246">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1246">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1247">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1247">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1248">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1248">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1249">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1249">IoT</span></span>

---
## Remote control
---
### <a name="restart-the-target-computer"></a><span data-ttu-id="5ed5c-1250">Neustarten des Zielcomputers</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1250">Restart the target computer</span></span>

**<span data-ttu-id="5ed5c-1251">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1251">Request</span></span>**

<span data-ttu-id="5ed5c-1252">Mit dem folgenden Anforderungsformat können Sie den Zielcomputer neu starten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1252">You can restart the target computer by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1253">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1253">Method</span></span>      | <span data-ttu-id="5ed5c-1254">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1254">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1255">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1255">POST</span></span> | <span data-ttu-id="5ed5c-1256">/api/control/restart</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1256">/api/control/restart</span></span>
<br />

**<span data-ttu-id="5ed5c-1257">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1257">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1258">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1258">None</span></span>

**<span data-ttu-id="5ed5c-1259">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1259">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1260">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1260">None</span></span>

**<span data-ttu-id="5ed5c-1261">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1261">Request body</span></span>**

- <span data-ttu-id="5ed5c-1262">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1262">None</span></span>

**<span data-ttu-id="5ed5c-1263">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1263">Response</span></span>**

**<span data-ttu-id="5ed5c-1264">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1264">Status code</span></span>**

<span data-ttu-id="5ed5c-1265">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1265">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1266">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1266">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1267">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1267">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1268">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1268">200</span></span> | <span data-ttu-id="5ed5c-1269">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1269">OK</span></span>
<br />
**<span data-ttu-id="5ed5c-1270">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1270">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1271">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1271">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1272">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1272">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1273">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1273">Xbox</span></span>
* <span data-ttu-id="5ed5c-1274">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1274">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1275">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1275">IoT</span></span>

---
### <a name="shut-down-the-target-computer"></a><span data-ttu-id="5ed5c-1276">Herunterfahren des Zielcomputers</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1276">Shut down the target computer</span></span>

**<span data-ttu-id="5ed5c-1277">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1277">Request</span></span>**

<span data-ttu-id="5ed5c-1278">Mit dem folgenden Anforderungsformat können Sie den Zielcomputer herunterfahren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1278">You can shut down the target computer by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1279">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1279">Method</span></span>      | <span data-ttu-id="5ed5c-1280">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1280">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1281">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1281">POST</span></span> | <span data-ttu-id="5ed5c-1282">/api/control/shutdown</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1282">/api/control/shutdown</span></span>
<br />

**<span data-ttu-id="5ed5c-1283">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1283">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1284">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1284">None</span></span>

**<span data-ttu-id="5ed5c-1285">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1285">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1286">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1286">None</span></span>

**<span data-ttu-id="5ed5c-1287">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1287">Request body</span></span>**

- <span data-ttu-id="5ed5c-1288">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1288">None</span></span>

**<span data-ttu-id="5ed5c-1289">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1289">Response</span></span>**

**<span data-ttu-id="5ed5c-1290">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1290">Status code</span></span>**

<span data-ttu-id="5ed5c-1291">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1291">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1292">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1292">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1293">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1293">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1294">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1294">200</span></span> | <span data-ttu-id="5ed5c-1295">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1295">OK</span></span>
<span data-ttu-id="5ed5c-1296">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1296">4XX</span></span> | <span data-ttu-id="5ed5c-1297">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1297">Error codes</span></span>
<span data-ttu-id="5ed5c-1298">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1298">5XX</span></span> | <span data-ttu-id="5ed5c-1299">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1299">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1300">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1300">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1301">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1301">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1302">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1302">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1303">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1303">Xbox</span></span>
* <span data-ttu-id="5ed5c-1304">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1304">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1305">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1305">IoT</span></span>

---
## Task manager
---
### <a name="start-a-modern-app"></a><span data-ttu-id="5ed5c-1306">Starten einer Modern App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1306">Start a modern app</span></span>

**<span data-ttu-id="5ed5c-1307">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1307">Request</span></span>**

<span data-ttu-id="5ed5c-1308">Mit dem folgenden Anforderungsformat können Sie eine Modern App starten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1308">You can start a modern app by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1309">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1309">Method</span></span>      | <span data-ttu-id="5ed5c-1310">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1310">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1311">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1311">POST</span></span> | <span data-ttu-id="5ed5c-1312">/api/taskmanager/app</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1312">/api/taskmanager/app</span></span>
<br />

**<span data-ttu-id="5ed5c-1313">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1313">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1314">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1314">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1315">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1315">URI parameter</span></span> | <span data-ttu-id="5ed5c-1316">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1316">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1317">appid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1317">appid</span></span>   | <span data-ttu-id="5ed5c-1318">(**erforderlich**) Die PRAID für die App, die gestartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1318">(**required**) The PRAID for the app you want to start.</span></span> <span data-ttu-id="5ed5c-1319">Dieser Wert sollte hex64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1319">This value should be hex64 encoded.</span></span>
<span data-ttu-id="5ed5c-1320">package</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1320">package</span></span>   | <span data-ttu-id="5ed5c-1321">(**erforderlich**) Der vollständige Name für das App-Paket, das Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1321">(**required**) The full name for the app package you want to start.</span></span> <span data-ttu-id="5ed5c-1322">Dieser Wert sollte hex64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1322">This value should be hex64 encoded.</span></span>
<br />
**<span data-ttu-id="5ed5c-1323">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1323">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1324">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1324">None</span></span>

**<span data-ttu-id="5ed5c-1325">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1325">Request body</span></span>**

- <span data-ttu-id="5ed5c-1326">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1326">None</span></span>

**<span data-ttu-id="5ed5c-1327">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1327">Response</span></span>**

**<span data-ttu-id="5ed5c-1328">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1328">Status code</span></span>**

<span data-ttu-id="5ed5c-1329">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1329">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1330">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1330">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1331">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1331">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1332">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1332">200</span></span> | <span data-ttu-id="5ed5c-1333">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1333">OK</span></span>
<span data-ttu-id="5ed5c-1334">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1334">4XX</span></span> | <span data-ttu-id="5ed5c-1335">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1335">Error codes</span></span>
<span data-ttu-id="5ed5c-1336">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1336">5XX</span></span> | <span data-ttu-id="5ed5c-1337">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1337">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1338">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1338">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1339">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1339">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1340">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1340">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1341">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1341">Xbox</span></span>
* <span data-ttu-id="5ed5c-1342">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1342">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1343">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1343">IoT</span></span>

---
### <a name="stop-a-modern-app"></a><span data-ttu-id="5ed5c-1344">Beenden einer Modern App</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1344">Stop a modern app</span></span>

**<span data-ttu-id="5ed5c-1345">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1345">Request</span></span>**

<span data-ttu-id="5ed5c-1346">Mit dem folgenden Anforderungsformat können Sie eine Modern App beenden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1346">You can stop a modern app by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1347">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1347">Method</span></span>      | <span data-ttu-id="5ed5c-1348">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1348">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1349">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1349">DELETE</span></span> | <span data-ttu-id="5ed5c-1350">/api/taskmanager/app</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1350">/api/taskmanager/app</span></span>
<br />

**<span data-ttu-id="5ed5c-1351">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1351">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1352">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1352">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1353">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1353">URI parameter</span></span> | <span data-ttu-id="5ed5c-1354">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1354">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1355">package</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1355">package</span></span>   | <span data-ttu-id="5ed5c-1356">(**erforderlich**) Der vollständige Name des App-Pakets, das Sie beenden möchten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1356">(**required**) The full name of the app packages that you want to stop.</span></span> <span data-ttu-id="5ed5c-1357">Dieser Wert sollte hex64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1357">This value should be hex64 encoded.</span></span>
<span data-ttu-id="5ed5c-1358">forcestop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1358">forcestop</span></span>   | <span data-ttu-id="5ed5c-1359">(**optional**) Der Wert **yes** gibt an, dass das Beenden sämtlicher Prozesse erzwungen werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1359">(**optional**) A value of **yes** indicates that the system should force all processes to stop.</span></span>
<br />
**<span data-ttu-id="5ed5c-1360">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1360">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1361">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1361">None</span></span>

**<span data-ttu-id="5ed5c-1362">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1362">Request body</span></span>**

- <span data-ttu-id="5ed5c-1363">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1363">None</span></span>

**<span data-ttu-id="5ed5c-1364">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1364">Response</span></span>**

**<span data-ttu-id="5ed5c-1365">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1365">Status code</span></span>**

<span data-ttu-id="5ed5c-1366">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1366">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1367">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1367">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1368">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1368">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1369">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1369">200</span></span> | <span data-ttu-id="5ed5c-1370">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1370">OK</span></span>
<span data-ttu-id="5ed5c-1371">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1371">4XX</span></span> | <span data-ttu-id="5ed5c-1372">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1372">Error codes</span></span>
<span data-ttu-id="5ed5c-1373">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1373">5XX</span></span> | <span data-ttu-id="5ed5c-1374">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1374">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1375">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1375">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1376">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1376">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1377">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1377">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1378">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1378">Xbox</span></span>
* <span data-ttu-id="5ed5c-1379">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1379">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1380">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1380">IoT</span></span>

---
### <a name="kill-process-by-pid"></a><span data-ttu-id="5ed5c-1381">Prozess per PID beenden</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1381">Kill process by PID</span></span>

**<span data-ttu-id="5ed5c-1382">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1382">Request</span></span>**

<span data-ttu-id="5ed5c-1383">Mit dem folgenden Anforderungsformat können Sie einen Prozess beenden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1383">You can kill a process by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1384">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1384">Method</span></span>      | <span data-ttu-id="5ed5c-1385">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1385">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1386">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1386">DELETE</span></span> | <span data-ttu-id="5ed5c-1387">/api/taskmanager/process</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1387">/api/taskmanager/process</span></span>
<br />

**<span data-ttu-id="5ed5c-1388">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1388">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1389">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1389">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1390">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1390">URI parameter</span></span> | <span data-ttu-id="5ed5c-1391">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1391">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1392">pid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1392">pid</span></span>   | <span data-ttu-id="5ed5c-1393">(**erforderlich**) Die eindeutige Prozess-ID für den zu beendenden Prozess.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1393">(**required**) The unique process id for the process to stop.</span></span>
<br />
**<span data-ttu-id="5ed5c-1394">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1394">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1395">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1395">None</span></span>

**<span data-ttu-id="5ed5c-1396">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1396">Request body</span></span>**

- <span data-ttu-id="5ed5c-1397">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1397">None</span></span>

**<span data-ttu-id="5ed5c-1398">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1398">Response</span></span>**

**<span data-ttu-id="5ed5c-1399">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1399">Status code</span></span>**

<span data-ttu-id="5ed5c-1400">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1400">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1401">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1401">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1402">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1402">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1403">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1403">200</span></span> | <span data-ttu-id="5ed5c-1404">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1404">OK</span></span>
<span data-ttu-id="5ed5c-1405">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1405">4XX</span></span> | <span data-ttu-id="5ed5c-1406">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1406">Error codes</span></span>
<span data-ttu-id="5ed5c-1407">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1407">5XX</span></span> | <span data-ttu-id="5ed5c-1408">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1408">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1409">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1409">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1410">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1410">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1411">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1411">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1412">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1412">IoT</span></span>

---
## Networking
---
### <a name="get-the-current-ip-configuration"></a><span data-ttu-id="5ed5c-1413">Abrufen der aktuellen IP-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1413">Get the current IP configuration</span></span>

**<span data-ttu-id="5ed5c-1414">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1414">Request</span></span>**

<span data-ttu-id="5ed5c-1415">Mit dem folgenden Anforderungsformat können Sie die aktuelle IP-Konfiguration abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1415">You can get the current IP configuration by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1416">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1416">Method</span></span>      | <span data-ttu-id="5ed5c-1417">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1417">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1418">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1418">GET</span></span> | <span data-ttu-id="5ed5c-1419">/api/networking/ipconfig</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1419">/api/networking/ipconfig</span></span>
<br />

**<span data-ttu-id="5ed5c-1420">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1420">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1421">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1421">None</span></span>

**<span data-ttu-id="5ed5c-1422">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1422">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1423">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1423">None</span></span>

**<span data-ttu-id="5ed5c-1424">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1424">Request body</span></span>**

- <span data-ttu-id="5ed5c-1425">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1425">None</span></span>

**<span data-ttu-id="5ed5c-1426">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1426">Response</span></span>**

<span data-ttu-id="5ed5c-1427">Die Antwort enthält die IP-Konfiguration in der folgenden Vorlage.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1427">The response includes the IP configuration in the following template.</span></span>

```
{"Adapters": [
    {
        "Description": string,
        "HardwareAddress": string,
        "Index": int,
        "Name": string,
        "Type": string,
        "DHCP": {
            "LeaseExpires": int, (timestamp)
            "LeaseObtained": int, (timestamp)
            "Address": {
                "IpAddress": string,
                "Mask": string
            }
        },
        "WINS": {(WINS is optional)
            "Primary": {
                "IpAddress": string,
                "Mask": string
            },
            "Secondary": {
                "IpAddress": string,
                "Mask": string
            }
        },
        "Gateways": [{ (always 1+)
            "IpAddress": "10.82.128.1",
            "Mask": "255.255.255.255"
            },...
        ],
        "IpAddresses": [{ (always 1+)
            "IpAddress": "10.82.128.148",
            "Mask": "255.255.255.0"
            },...
        ]
    },...
]}
```

**<span data-ttu-id="5ed5c-1428">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1428">Status code</span></span>**

<span data-ttu-id="5ed5c-1429">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1429">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1430">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1430">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1431">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1431">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1432">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1432">200</span></span> | <span data-ttu-id="5ed5c-1433">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1433">OK</span></span>
<span data-ttu-id="5ed5c-1434">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1434">4XX</span></span> | <span data-ttu-id="5ed5c-1435">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1435">Error codes</span></span>
<span data-ttu-id="5ed5c-1436">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1436">5XX</span></span> | <span data-ttu-id="5ed5c-1437">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1437">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1438">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1438">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1439">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1439">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1440">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1440">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1441">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1441">Xbox</span></span>
* <span data-ttu-id="5ed5c-1442">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1442">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1443">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1443">IoT</span></span>

--
### <a name="enumerate-wireless-network-interfaces"></a><span data-ttu-id="5ed5c-1444">Auflisten der Drahtlos-Netzwerkschnittstellen</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1444">Enumerate wireless network interfaces</span></span>

**<span data-ttu-id="5ed5c-1445">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1445">Request</span></span>**

<span data-ttu-id="5ed5c-1446">Mit dem folgenden Anforderungsformat können Sie die Drahtlos-Netzwerkschnittstellen auflisten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1446">You can enumerate the available wireless network interfaces by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1447">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1447">Method</span></span>      | <span data-ttu-id="5ed5c-1448">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1448">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1449">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1449">GET</span></span> | <span data-ttu-id="5ed5c-1450">/api/wifi/interfaces</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1450">/api/wifi/interfaces</span></span>
<br />

**<span data-ttu-id="5ed5c-1451">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1451">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1452">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1452">None</span></span>

**<span data-ttu-id="5ed5c-1453">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1453">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1454">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1454">None</span></span>

**<span data-ttu-id="5ed5c-1455">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1455">Request body</span></span>**

- <span data-ttu-id="5ed5c-1456">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1456">None</span></span>

**<span data-ttu-id="5ed5c-1457">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1457">Response</span></span>**

<span data-ttu-id="5ed5c-1458">Eine Liste der verfügbaren Drahtlosschnittstellen mit Details im folgenden Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1458">A list of the available wireless interfaces with details in the following format.</span></span>

``` 
{"Interfaces": [{
    "Description": string,
    "GUID": string (guid with curly brackets),
    "Index": int,
    "ProfilesList": [
        {
            "GroupPolicyProfile": bool,
            "Name": string, (Network currently connected to)
            "PerUserProfile": bool
        },...
    ]
    }
]}
```

**<span data-ttu-id="5ed5c-1459">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1459">Status code</span></span>**

<span data-ttu-id="5ed5c-1460">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1460">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1461">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1461">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1462">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1462">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1463">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1463">200</span></span> | <span data-ttu-id="5ed5c-1464">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1464">OK</span></span>
<span data-ttu-id="5ed5c-1465">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1465">4XX</span></span> | <span data-ttu-id="5ed5c-1466">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1466">Error codes</span></span>
<span data-ttu-id="5ed5c-1467">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1467">5XX</span></span> | <span data-ttu-id="5ed5c-1468">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1468">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1469">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1469">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1470">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1470">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1471">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1471">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1472">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1472">Xbox</span></span>
* <span data-ttu-id="5ed5c-1473">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1473">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1474">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1474">IoT</span></span>

---
### <a name="enumerate-wireless-networks"></a><span data-ttu-id="5ed5c-1475">Auflisten von Drahtlosnetzwerken</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1475">Enumerate wireless networks</span></span>

**<span data-ttu-id="5ed5c-1476">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1476">Request</span></span>**

<span data-ttu-id="5ed5c-1477">Mit dem folgenden Anforderungsformat können Sie die Liste der Drahtlosnetzwerke an der angegebenen Schnittstelle auflisten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1477">You can enumerate the list of wireless networks on the specified interface by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1478">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1478">Method</span></span>      | <span data-ttu-id="5ed5c-1479">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1479">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1480">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1480">GET</span></span> | <span data-ttu-id="5ed5c-1481">/api/wifi/networks</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1481">/api/wifi/networks</span></span>
<br />

**<span data-ttu-id="5ed5c-1482">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1482">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1483">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1483">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1484">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1484">URI parameter</span></span> | <span data-ttu-id="5ed5c-1485">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1485">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1486">interface</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1486">interface</span></span>   | <span data-ttu-id="5ed5c-1487">(**erforderlich**) Die GUID für die Netzwerkschnittstelle, die zum Suchen nach Drahtlosnetzwerken verwendet werden soll, ohne Klammern.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1487">(**required**) The GUID for the network interface to use to search for wireless networks, without brackets.</span></span> 
<br />
**<span data-ttu-id="5ed5c-1488">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1488">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1489">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1489">None</span></span>

**<span data-ttu-id="5ed5c-1490">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1490">Request body</span></span>**

- <span data-ttu-id="5ed5c-1491">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1491">None</span></span>

**<span data-ttu-id="5ed5c-1492">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1492">Response</span></span>**

<span data-ttu-id="5ed5c-1493">Die Liste der an der angegebenen *interface* gefundenen Drahtlosnetzwerke.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1493">The list of wireless networks found on the provided *interface*.</span></span> <span data-ttu-id="5ed5c-1494">Diese enthält Details für die Netzwerke im folgenden Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1494">This includes details for the networks in the following format.</span></span>

```
{"AvailableNetworks": [
    {
        "AlreadyConnected": bool,
        "AuthenticationAlgorithm": string, (WPA2, etc)
        "Channel": int,
        "CipherAlgorithm": string, (e.g. AES)
        "Connectable": int, (0 | 1)
        "InfrastructureType": string,
        "ProfileAvailable": bool,
        "ProfileName": string,
        "SSID": string,
        "SecurityEnabled": int, (0 | 1)
        "SignalQuality": int,
        "BSSID": [int,...],
        "PhysicalTypes": [string,...]
    },...
]}
```

**<span data-ttu-id="5ed5c-1495">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1495">Status code</span></span>**

<span data-ttu-id="5ed5c-1496">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1496">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1497">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1497">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1498">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1498">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1499">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1499">200</span></span> | <span data-ttu-id="5ed5c-1500">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1500">OK</span></span>
<span data-ttu-id="5ed5c-1501">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1501">4XX</span></span> | <span data-ttu-id="5ed5c-1502">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1502">Error codes</span></span>
<span data-ttu-id="5ed5c-1503">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1503">5XX</span></span> | <span data-ttu-id="5ed5c-1504">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1504">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1505">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1505">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1506">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1506">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1507">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1507">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1508">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1508">Xbox</span></span>
* <span data-ttu-id="5ed5c-1509">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1509">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1510">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1510">IoT</span></span>

---
### <a name="connect-and-disconnect-to-a-wi-fi-network"></a><span data-ttu-id="5ed5c-1511">Herstellen der Verbindung mit einem WLAN-Netzwerk und Trennen der Verbindung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1511">Connect and disconnect to a Wi-Fi network.</span></span>

**<span data-ttu-id="5ed5c-1512">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1512">Request</span></span>**

<span data-ttu-id="5ed5c-1513">Mit dem folgenden Anforderungsformat können Sie eine Verbindung mit einem WLAN-Netzwerk herstellen oder die Verbindung trennen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1513">You can connect or disconnect to a Wi-Fi network by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1514">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1514">Method</span></span>      | <span data-ttu-id="5ed5c-1515">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1515">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1516">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1516">POST</span></span> | <span data-ttu-id="5ed5c-1517">/api/wifi/network</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1517">/api/wifi/network</span></span>
<br />

**<span data-ttu-id="5ed5c-1518">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1518">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1519">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1519">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1520">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1520">URI parameter</span></span> | <span data-ttu-id="5ed5c-1521">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1521">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1522">interface</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1522">interface</span></span>   | <span data-ttu-id="5ed5c-1523">(**erforderlich**) Die GUID für die Netzwerkschnittstelle, die zum Herstellen der Verbindung mit dem Netzwerk verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1523">(**required**) The GUID for the network interface you use to connect to the network.</span></span>
<span data-ttu-id="5ed5c-1524">op</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1524">op</span></span>   | <span data-ttu-id="5ed5c-1525">(**erforderlich**) Gibt die durchzuführende Aktion an.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1525">(**required**) Indicates the action to take.</span></span> <span data-ttu-id="5ed5c-1526">Mögliche Werte sind „connect“ und „disconnect“.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1526">Possible values are connect or disconnect.</span></span>
<span data-ttu-id="5ed5c-1527">ssid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1527">ssid</span></span>   | <span data-ttu-id="5ed5c-1528">(**Erforderlich, wenn *op* == connect**) Die SSID des Netzwerks, mit dem die Verbindung hergestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1528">(**required if *op* == connect**) The SSID to connect to.</span></span>
<span data-ttu-id="5ed5c-1529">key</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1529">key</span></span>   | <span data-ttu-id="5ed5c-1530">(**Erforderlich, wenn *op* == connect und Netzwerk erfordert Authentifizierung**) Der gemeinsam verwendete Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1530">(**required if *op* == connect and network requires authentication**) The shared key.</span></span>
<span data-ttu-id="5ed5c-1531">createprofile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1531">createprofile</span></span> | <span data-ttu-id="5ed5c-1532">(**erforderlich**) Erstellen Sie ein Profil für das Netzwerk auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1532">(**required**) Create a profile for the network on the device.</span></span>  <span data-ttu-id="5ed5c-1533">Dadurch stellt das Gerät künftig automatisch eine Verbindung zum Netzwerk her.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1533">This will cause the device to auto-connect to the network in the future.</span></span> <span data-ttu-id="5ed5c-1534">Dies kann **ja** oder **nein** sein.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1534">This can be **yes** or **no**.</span></span> 

**<span data-ttu-id="5ed5c-1535">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1535">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1536">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1536">None</span></span>

**<span data-ttu-id="5ed5c-1537">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1537">Request body</span></span>**

- <span data-ttu-id="5ed5c-1538">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1538">None</span></span>

**<span data-ttu-id="5ed5c-1539">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1539">Response</span></span>**

**<span data-ttu-id="5ed5c-1540">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1540">Status code</span></span>**

<span data-ttu-id="5ed5c-1541">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1541">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1542">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1542">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1543">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1543">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1544">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1544">200</span></span> | <span data-ttu-id="5ed5c-1545">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1545">OK</span></span>
<br />
**<span data-ttu-id="5ed5c-1546">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1546">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1547">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1547">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1548">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1548">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1549">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1549">Xbox</span></span>
* <span data-ttu-id="5ed5c-1550">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1550">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1551">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1551">IoT</span></span>

---
### <a name="delete-a-wi-fi-profile"></a><span data-ttu-id="5ed5c-1552">Löschen eines WLAN-Profils</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1552">Delete a Wi-Fi profile</span></span>

**<span data-ttu-id="5ed5c-1553">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1553">Request</span></span>**

<span data-ttu-id="5ed5c-1554">Mit dem folgenden Anforderungsformat können Sie ein Profil löschen, das einem Netzwerk an einer bestimmten Schnittstelle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1554">You can delete a profile associated with a network on a specific interface by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1555">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1555">Method</span></span>      | <span data-ttu-id="5ed5c-1556">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1556">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1557">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1557">DELETE</span></span> | <span data-ttu-id="5ed5c-1558">/api/wifi/network</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1558">/api/wifi/network</span></span>
<br />

**<span data-ttu-id="5ed5c-1559">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1559">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1560">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1560">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1561">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1561">URI parameter</span></span> | <span data-ttu-id="5ed5c-1562">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1562">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1563">interface</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1563">interface</span></span>   | <span data-ttu-id="5ed5c-1564">(**erforderlich**) Die GUID der Netzwerkschnittstelle, die dem zu löschenden Profil zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1564">(**required**) The GUID for the network interface associated with the profile to delete.</span></span>
<span data-ttu-id="5ed5c-1565">profile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1565">profile</span></span>   | <span data-ttu-id="5ed5c-1566">(**erforderlich**) Der Name des zu löschenden Profils.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1566">(**required**) The name of the profile to delete.</span></span>
<br />
**<span data-ttu-id="5ed5c-1567">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1567">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1568">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1568">None</span></span>

**<span data-ttu-id="5ed5c-1569">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1569">Request body</span></span>**

- <span data-ttu-id="5ed5c-1570">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1570">None</span></span>

**<span data-ttu-id="5ed5c-1571">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1571">Response</span></span>**

**<span data-ttu-id="5ed5c-1572">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1572">Status code</span></span>**

<span data-ttu-id="5ed5c-1573">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1573">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1574">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1574">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1575">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1575">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1576">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1576">200</span></span> | <span data-ttu-id="5ed5c-1577">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1577">OK</span></span>
<br />
**<span data-ttu-id="5ed5c-1578">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1578">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1579">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1579">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1580">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1580">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1581">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1581">Xbox</span></span>
* <span data-ttu-id="5ed5c-1582">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1582">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1583">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1583">IoT</span></span>

---
## Windows Error Reporting (WER)
---
### <a name="download-a-windows-error-reporting-wer-file"></a><span data-ttu-id="5ed5c-1584">Herunterladen einer WER-Datei (Windows Error Reporting)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1584">Download a Windows error reporting (WER) file</span></span>

**<span data-ttu-id="5ed5c-1585">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1585">Request</span></span>**

<span data-ttu-id="5ed5c-1586">Mit dem folgenden Anforderungsformat können Sie eine WER-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1586">You can download a WER-related file by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1587">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1587">Method</span></span>      | <span data-ttu-id="5ed5c-1588">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1588">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1589">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1589">GET</span></span> | <span data-ttu-id="5ed5c-1590">/api/wer/report/file</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1590">/api/wer/report/file</span></span>
<br />

**<span data-ttu-id="5ed5c-1591">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1591">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1592">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1592">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1593">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1593">URI parameter</span></span> | <span data-ttu-id="5ed5c-1594">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1594">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1595">user</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1595">user</span></span>   | <span data-ttu-id="5ed5c-1596">(**erforderlich**) Der dem Bericht zugeordnete Benutzername.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1596">(**required**) The user name associated with the report.</span></span>
<span data-ttu-id="5ed5c-1597">type</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1597">type</span></span>   | <span data-ttu-id="5ed5c-1598">(**erforderlich**) Der Typ des Berichts.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1598">(**required**) The type of report.</span></span> <span data-ttu-id="5ed5c-1599">Dieser kann **queried** oder **archived** lauten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1599">This can be either **queried** or **archived**.</span></span>
<span data-ttu-id="5ed5c-1600">name</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1600">name</span></span>   | <span data-ttu-id="5ed5c-1601">(**erforderlich**) Der Name des Berichts.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1601">(**required**) The name of the report.</span></span> <span data-ttu-id="5ed5c-1602">Dieser sollte base64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1602">This should be base64 encoded.</span></span> 
<span data-ttu-id="5ed5c-1603">file</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1603">file</span></span>   | <span data-ttu-id="5ed5c-1604">(**erforderlich**) Der Name der Datei des Berichts, die heruntergeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1604">(**required**) The name of the file to download from the report.</span></span> <span data-ttu-id="5ed5c-1605">Dieser sollte base64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1605">This should be base64 encoded.</span></span> 
<br />
**<span data-ttu-id="5ed5c-1606">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1606">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1607">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1607">None</span></span>

**<span data-ttu-id="5ed5c-1608">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1608">Request body</span></span>**

- <span data-ttu-id="5ed5c-1609">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1609">None</span></span>

**<span data-ttu-id="5ed5c-1610">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1610">Response</span></span>**

- <span data-ttu-id="5ed5c-1611">Antwort enthält die angeforderte Datei.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1611">Response contains the requested file.</span></span> 

**<span data-ttu-id="5ed5c-1612">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1612">Status code</span></span>**

<span data-ttu-id="5ed5c-1613">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1613">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1614">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1614">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1615">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1615">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1616">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1616">200</span></span> | <span data-ttu-id="5ed5c-1617">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1617">OK</span></span>
<span data-ttu-id="5ed5c-1618">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1618">4XX</span></span> | <span data-ttu-id="5ed5c-1619">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1619">Error codes</span></span>
<span data-ttu-id="5ed5c-1620">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1620">5XX</span></span> | <span data-ttu-id="5ed5c-1621">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1621">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1622">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1622">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1623">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1623">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1624">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1624">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1625">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1625">IoT</span></span>

---
### <a name="enumerate-files-in-a-windows-error-reporting-wer-report"></a><span data-ttu-id="5ed5c-1626">Auflisten von Dateien in einem Bericht zur Windows-Fehlerberichterstattung (WER)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1626">Enumerate files in a Windows error reporting (WER) report</span></span>

**<span data-ttu-id="5ed5c-1627">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1627">Request</span></span>**

<span data-ttu-id="5ed5c-1628">Mit dem folgenden Anforderungsformat können Sie die Dateien in einem WER-Bericht auflisten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1628">You can enumerate the files in a WER report by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1629">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1629">Method</span></span>      | <span data-ttu-id="5ed5c-1630">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1630">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1631">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1631">GET</span></span> | <span data-ttu-id="5ed5c-1632">/api/wer/report/files</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1632">/api/wer/report/files</span></span>
<br />

**<span data-ttu-id="5ed5c-1633">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1633">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1634">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1634">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1635">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1635">URI parameter</span></span> | <span data-ttu-id="5ed5c-1636">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1636">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1637">user</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1637">user</span></span>   | <span data-ttu-id="5ed5c-1638">(**erforderlich**) Der dem Bericht zugeordnete Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1638">(**required**) The user associated with the report.</span></span>
<span data-ttu-id="5ed5c-1639">type</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1639">type</span></span>   | <span data-ttu-id="5ed5c-1640">(**erforderlich**) Der Typ des Berichts.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1640">(**required**) The type of report.</span></span> <span data-ttu-id="5ed5c-1641">Dieser kann **queried** oder **archived** lauten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1641">This can be either **queried** or **archived**.</span></span>
<span data-ttu-id="5ed5c-1642">name</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1642">name</span></span>   | <span data-ttu-id="5ed5c-1643">(**erforderlich**) Der Name des Berichts.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1643">(**required**) The name of the report.</span></span> <span data-ttu-id="5ed5c-1644">Dieser sollte base64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1644">This should be base64 encoded.</span></span> 
<br />
**<span data-ttu-id="5ed5c-1645">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1645">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1646">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1646">None</span></span>

**<span data-ttu-id="5ed5c-1647">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1647">Request body</span></span>**

```
{"Files": [
    {
        "Name": string, (Filename, not base64 encoded)
        "Size": int (bytes)
    },...
]}
```

**<span data-ttu-id="5ed5c-1648">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1648">Response</span></span>**

**<span data-ttu-id="5ed5c-1649">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1649">Status code</span></span>**

<span data-ttu-id="5ed5c-1650">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1650">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1651">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1651">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1652">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1652">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1653">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1653">200</span></span> | <span data-ttu-id="5ed5c-1654">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1654">OK</span></span>
<span data-ttu-id="5ed5c-1655">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1655">4XX</span></span> | <span data-ttu-id="5ed5c-1656">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1656">Error codes</span></span>
<span data-ttu-id="5ed5c-1657">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1657">5XX</span></span> | <span data-ttu-id="5ed5c-1658">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1658">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1659">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1659">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1660">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1660">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1661">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1661">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1662">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1662">IoT</span></span>

---
### <a name="list-the-windows-error-reporting-wer-reports"></a><span data-ttu-id="5ed5c-1663">Auflisten der Berichte zur Windows-Fehlerberichterstattung (WER)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1663">List the Windows error reporting (WER) reports</span></span>

**<span data-ttu-id="5ed5c-1664">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1664">Request</span></span>**

<span data-ttu-id="5ed5c-1665">Mit dem folgenden Anforderungsformat können Sie die WER-Berichte abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1665">You can get the WER reports by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1666">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1666">Method</span></span>      | <span data-ttu-id="5ed5c-1667">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1667">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1668">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1668">GET</span></span> | <span data-ttu-id="5ed5c-1669">/api/wer/reports</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1669">/api/wer/reports</span></span>
<br />

**<span data-ttu-id="5ed5c-1670">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1670">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1671">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1671">None</span></span>

**<span data-ttu-id="5ed5c-1672">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1672">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1673">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1673">None</span></span>

**<span data-ttu-id="5ed5c-1674">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1674">Request body</span></span>**

- <span data-ttu-id="5ed5c-1675">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1675">None</span></span>

**<span data-ttu-id="5ed5c-1676">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1676">Response</span></span>**

<span data-ttu-id="5ed5c-1677">Die WER-Berichte in folgendem Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1677">The WER reports in the following format.</span></span>

```
{"WerReports": [
    {
        "User": string,
        "Reports": [
            {
                "CreationTime": int,
                "Name": string, (not base64 encoded)
                "Type": string ("Queue" or "Archive")
            },
    },...
]}
```

**<span data-ttu-id="5ed5c-1678">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1678">Status code</span></span>**

<span data-ttu-id="5ed5c-1679">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1679">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1680">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1680">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1681">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1681">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1682">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1682">200</span></span> | <span data-ttu-id="5ed5c-1683">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1683">OK</span></span>
<span data-ttu-id="5ed5c-1684">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1684">4XX</span></span> | <span data-ttu-id="5ed5c-1685">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1685">Error codes</span></span>
<span data-ttu-id="5ed5c-1686">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1686">5XX</span></span> | <span data-ttu-id="5ed5c-1687">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1687">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1688">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1688">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1689">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1689">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1690">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1690">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1691">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1691">IoT</span></span>

---
## Windows Performance Recorder (WPR) 
---
### <a name="start-tracing-with-a-custom-profile"></a><span data-ttu-id="5ed5c-1692">Starten der Ablaufverfolgung mit einem benutzerdefinierten Profil</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1692">Start tracing with a custom profile</span></span>

**<span data-ttu-id="5ed5c-1693">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1693">Request</span></span>**

<span data-ttu-id="5ed5c-1694">Mit dem folgenden Anforderungsformat können Sie ein WPR-Profil hochladen und die Ablaufverfolgung mit diesem Profil starten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1694">You can upload a WPR profile and start tracing using that profile by using the following request format.</span></span>  <span data-ttu-id="5ed5c-1695">Es kann immer nur eine Spur ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1695">Only one trace can run at a time.</span></span> <span data-ttu-id="5ed5c-1696">Das Profil bleibt nicht auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1696">The profile will not remain on the device.</span></span> 
 
<span data-ttu-id="5ed5c-1697">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1697">Method</span></span>      | <span data-ttu-id="5ed5c-1698">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1698">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1699">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1699">POST</span></span> | <span data-ttu-id="5ed5c-1700">/api/wpr/customtrace</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1700">/api/wpr/customtrace</span></span>
<br />

**<span data-ttu-id="5ed5c-1701">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1701">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1702">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1702">None</span></span>

**<span data-ttu-id="5ed5c-1703">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1703">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1704">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1704">None</span></span>

**<span data-ttu-id="5ed5c-1705">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1705">Request body</span></span>**

- <span data-ttu-id="5ed5c-1706">Ein multipart-konformer HTTP-Text, der das benutzerdefinierte WPR-Profil enthält.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1706">A multi-part conforming http body that contains the custom WPR profile.</span></span>

**<span data-ttu-id="5ed5c-1707">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1707">Response</span></span>**

<span data-ttu-id="5ed5c-1708">Der Status der WPR-Sitzung im folgenden Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1708">The WPR session status in the following format.</span></span>

```
{
    "SessionType": string, (Running or Idle) 
    "State": string (normal or boot)
}
```

**<span data-ttu-id="5ed5c-1709">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1709">Status code</span></span>**

<span data-ttu-id="5ed5c-1710">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1710">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1711">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1711">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1712">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1712">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1713">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1713">200</span></span> | <span data-ttu-id="5ed5c-1714">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1714">OK</span></span>
<span data-ttu-id="5ed5c-1715">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1715">4XX</span></span> | <span data-ttu-id="5ed5c-1716">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1716">Error codes</span></span>
<span data-ttu-id="5ed5c-1717">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1717">5XX</span></span> | <span data-ttu-id="5ed5c-1718">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1718">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1719">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1719">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1720">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1720">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1721">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1721">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1722">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1722">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1723">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1723">IoT</span></span>

---
### <a name="start-a-boot-performance-tracing-session"></a><span data-ttu-id="5ed5c-1724">Starten einer Startleistungs-Ablaufverfolgungssitzung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1724">Start a boot performance tracing session</span></span>

**<span data-ttu-id="5ed5c-1725">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1725">Request</span></span>**

<span data-ttu-id="5ed5c-1726">Mit dem folgenden Anforderungsformat können Sie eine WPR-Start-Ablaufverfolgungssitzung starten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1726">You can start a boot WPR tracing session by using the following request format.</span></span> <span data-ttu-id="5ed5c-1727">Diese wird auch als Leistungs-Ablaufverfolgungssitzung bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1727">This is also known as a performance tracing session.</span></span>
 
<span data-ttu-id="5ed5c-1728">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1728">Method</span></span>      | <span data-ttu-id="5ed5c-1729">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1729">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1730">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1730">POST</span></span> | <span data-ttu-id="5ed5c-1731">/api/wpr/boottrace</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1731">/api/wpr/boottrace</span></span>
<br />

**<span data-ttu-id="5ed5c-1732">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1732">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1733">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1733">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1734">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1734">URI parameter</span></span> | <span data-ttu-id="5ed5c-1735">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1735">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1736">profile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1736">profile</span></span>   | <span data-ttu-id="5ed5c-1737">(**erforderlich**) Dieser Parameter ist beim Starten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1737">(**required**) This parameter is required on start.</span></span> <span data-ttu-id="5ed5c-1738">Der Name des Profils, das eine Leistungs-Ablaufverfolgungssitzung starten soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1738">The name of the profile that should start a performance tracing session.</span></span> <span data-ttu-id="5ed5c-1739">Die möglichen Profile werden in „perfprofiles/profiles.json“ gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1739">The possible profiles are stored in perfprofiles/profiles.json.</span></span>
<br />
**<span data-ttu-id="5ed5c-1740">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1740">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1741">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1741">None</span></span>

**<span data-ttu-id="5ed5c-1742">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1742">Request body</span></span>**

- <span data-ttu-id="5ed5c-1743">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1743">None</span></span>

**<span data-ttu-id="5ed5c-1744">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1744">Response</span></span>**

<span data-ttu-id="5ed5c-1745">Beim Start gibt diese API den Status der WPR-Sitzung im folgenden Format zurück.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1745">On start, this API returns the WPR session status in the following format.</span></span>

```
{
    "SessionType": string, (Running or Idle) 
    "State": string (boot)
}
```

**<span data-ttu-id="5ed5c-1746">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1746">Status code</span></span>**

<span data-ttu-id="5ed5c-1747">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1747">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1748">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1748">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1749">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1749">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1750">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1750">200</span></span> | <span data-ttu-id="5ed5c-1751">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1751">OK</span></span>
<span data-ttu-id="5ed5c-1752">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1752">4XX</span></span> | <span data-ttu-id="5ed5c-1753">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1753">Error codes</span></span>
<span data-ttu-id="5ed5c-1754">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1754">5XX</span></span> | <span data-ttu-id="5ed5c-1755">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1755">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1756">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1756">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1757">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1757">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1758">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1758">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1759">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1759">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1760">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1760">IoT</span></span>

---
### <a name="stop-a-boot-performance-tracing-session"></a><span data-ttu-id="5ed5c-1761">Beenden einer Startleistungs-Ablaufverfolgungssitzung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1761">Stop a boot performance tracing session</span></span>

**<span data-ttu-id="5ed5c-1762">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1762">Request</span></span>**

<span data-ttu-id="5ed5c-1763">Mit dem folgenden Anforderungsformat können Sie eine WPR-Start-Ablaufverfolgungssitzung beenden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1763">You can stop a boot WPR tracing session by using the following request format.</span></span> <span data-ttu-id="5ed5c-1764">Diese wird auch als Leistungs-Ablaufverfolgungssitzung bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1764">This is also known as a performance tracing session.</span></span>
 
<span data-ttu-id="5ed5c-1765">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1765">Method</span></span>      | <span data-ttu-id="5ed5c-1766">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1766">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1767">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1767">GET</span></span> | <span data-ttu-id="5ed5c-1768">/api/wpr/boottrace</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1768">/api/wpr/boottrace</span></span>
<br />

**<span data-ttu-id="5ed5c-1769">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1769">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1770">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1770">None</span></span>

**<span data-ttu-id="5ed5c-1771">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1771">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1772">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1772">None</span></span>

**<span data-ttu-id="5ed5c-1773">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1773">Request body</span></span>**

- <span data-ttu-id="5ed5c-1774">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1774">None</span></span>

**<span data-ttu-id="5ed5c-1775">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1775">Response</span></span>**

-  <span data-ttu-id="5ed5c-1776">Keine.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1776">None.</span></span>  <span data-ttu-id="5ed5c-1777">**Hinweis** Hierbei handelt es sich um einen Vorgang mit langer Ausführungsdauer.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1777">**Note:** This is a long running operation.</span></span>  <span data-ttu-id="5ed5c-1778">Er wird wieder verfügbar, wenn der ETL-Schreibvorgang auf der Festplatte abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1778">It will return when the ETL is finished writing to disk.</span></span>

**<span data-ttu-id="5ed5c-1779">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1779">Status code</span></span>**

<span data-ttu-id="5ed5c-1780">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1780">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1781">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1781">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1782">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1782">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1783">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1783">200</span></span> | <span data-ttu-id="5ed5c-1784">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1784">OK</span></span>
<span data-ttu-id="5ed5c-1785">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1785">4XX</span></span> | <span data-ttu-id="5ed5c-1786">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1786">Error codes</span></span>
<span data-ttu-id="5ed5c-1787">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1787">5XX</span></span> | <span data-ttu-id="5ed5c-1788">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1788">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1789">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1789">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1790">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1790">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1791">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1791">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1792">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1792">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1793">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1793">IoT</span></span>

---
### <a name="start-a-performance-tracing-session"></a><span data-ttu-id="5ed5c-1794">Starten einer Leistungs-Ablaufverfolgungssitzung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1794">Start a performance tracing session</span></span>

**<span data-ttu-id="5ed5c-1795">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1795">Request</span></span>**

<span data-ttu-id="5ed5c-1796">Mit dem folgenden Anforderungsformat können Sie eine WPR-Ablaufverfolgungssitzung starten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1796">You can start a WPR tracing session by using the following request format.</span></span> <span data-ttu-id="5ed5c-1797">Diese wird auch als Leistungs-Ablaufverfolgungssitzung bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1797">This is also known as a performance tracing session.</span></span>  <span data-ttu-id="5ed5c-1798">Es kann immer nur eine Spur ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1798">Only one trace can run at a time.</span></span> 
 
<span data-ttu-id="5ed5c-1799">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1799">Method</span></span>      | <span data-ttu-id="5ed5c-1800">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1800">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1801">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1801">POST</span></span> | <span data-ttu-id="5ed5c-1802">/api/wpr/trace</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1802">/api/wpr/trace</span></span>
<br />

**<span data-ttu-id="5ed5c-1803">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1803">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1804">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1804">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="5ed5c-1805">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1805">URI parameter</span></span> | <span data-ttu-id="5ed5c-1806">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1806">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1807">profile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1807">profile</span></span>   | <span data-ttu-id="5ed5c-1808">(**erforderlich**) Der Name des Profils, das eine Leistungs-Ablaufverfolgungssitzung starten soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1808">(**required**) The name of the profile that should start a performance tracing session.</span></span> <span data-ttu-id="5ed5c-1809">Die möglichen Profile werden in „perfprofiles/profiles.json“ gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1809">The possible profiles are stored in perfprofiles/profiles.json.</span></span>
<br />
**<span data-ttu-id="5ed5c-1810">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1810">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1811">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1811">None</span></span>

**<span data-ttu-id="5ed5c-1812">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1812">Request body</span></span>**

- <span data-ttu-id="5ed5c-1813">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1813">None</span></span>

**<span data-ttu-id="5ed5c-1814">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1814">Response</span></span>**

<span data-ttu-id="5ed5c-1815">Beim Start gibt diese API den Status der WPR-Sitzung im folgenden Format zurück.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1815">On start, this API returns the WPR session status in the following format.</span></span>

```
{
    "SessionType": string, (Running or Idle) 
    "State": string (normal)
}
```

**<span data-ttu-id="5ed5c-1816">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1816">Status code</span></span>**

<span data-ttu-id="5ed5c-1817">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1817">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1818">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1818">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1819">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1819">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1820">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1820">200</span></span> | <span data-ttu-id="5ed5c-1821">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1821">OK</span></span>
<span data-ttu-id="5ed5c-1822">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1822">4XX</span></span> | <span data-ttu-id="5ed5c-1823">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1823">Error codes</span></span>
<span data-ttu-id="5ed5c-1824">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1824">5XX</span></span> | <span data-ttu-id="5ed5c-1825">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1825">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1826">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1826">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1827">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1827">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1828">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1828">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1829">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1829">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1830">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1830">IoT</span></span>

---
### <a name="stop-a-performance-tracing-session"></a><span data-ttu-id="5ed5c-1831">Beenden einer Leistungs-Ablaufverfolgungssitzung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1831">Stop a performance tracing session</span></span>

**<span data-ttu-id="5ed5c-1832">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1832">Request</span></span>**

<span data-ttu-id="5ed5c-1833">Mit dem folgenden Anforderungsformat können Sie eine WPR-Ablaufverfolgungssitzung beenden.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1833">You can stop a WPR tracing session by using the following request format.</span></span> <span data-ttu-id="5ed5c-1834">Diese wird auch als Leistungs-Ablaufverfolgungssitzung bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1834">This is also known as a performance tracing session.</span></span>
 
<span data-ttu-id="5ed5c-1835">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1835">Method</span></span>      | <span data-ttu-id="5ed5c-1836">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1836">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1837">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1837">GET</span></span> | <span data-ttu-id="5ed5c-1838">/api/wpr/trace</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1838">/api/wpr/trace</span></span>
<br />

**<span data-ttu-id="5ed5c-1839">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1839">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1840">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1840">None</span></span>

**<span data-ttu-id="5ed5c-1841">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1841">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1842">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1842">None</span></span>

**<span data-ttu-id="5ed5c-1843">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1843">Request body</span></span>**

- <span data-ttu-id="5ed5c-1844">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1844">None</span></span>

**<span data-ttu-id="5ed5c-1845">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1845">Response</span></span>**

- <span data-ttu-id="5ed5c-1846">Keine.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1846">None.</span></span>  <span data-ttu-id="5ed5c-1847">**Hinweis** Hierbei handelt es sich um einen Vorgang mit langer Ausführungsdauer.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1847">**Note:** This is a long running operation.</span></span>  <span data-ttu-id="5ed5c-1848">Er wird wieder verfügbar, wenn der ETL-Schreibvorgang auf der Festplatte abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1848">It will return when the ETL is finished writing to disk.</span></span>  

**<span data-ttu-id="5ed5c-1849">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1849">Status code</span></span>**

<span data-ttu-id="5ed5c-1850">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1850">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1851">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1851">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1852">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1852">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1853">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1853">200</span></span> | <span data-ttu-id="5ed5c-1854">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1854">OK</span></span>
<span data-ttu-id="5ed5c-1855">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1855">4XX</span></span> | <span data-ttu-id="5ed5c-1856">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1856">Error codes</span></span>
<span data-ttu-id="5ed5c-1857">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1857">5XX</span></span> | <span data-ttu-id="5ed5c-1858">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1858">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1859">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1859">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1860">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1860">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1861">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1861">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1862">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1862">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1863">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1863">IoT</span></span>

---
### <a name="retrieve-the-status-of-a-tracing-session"></a><span data-ttu-id="5ed5c-1864">Abrufen des Status einer Ablaufverfolgungssitzung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1864">Retrieve the status of a tracing session</span></span>

**<span data-ttu-id="5ed5c-1865">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1865">Request</span></span>**

<span data-ttu-id="5ed5c-1866">Mit dem folgenden Anforderungsformat können Sie den Status der aktuellen WPR-Sitzung abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1866">You can retrieve the status of the current WPR session by using the following request format.</span></span>
 
<span data-ttu-id="5ed5c-1867">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1867">Method</span></span>      | <span data-ttu-id="5ed5c-1868">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1868">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1869">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1869">GET</span></span> | <span data-ttu-id="5ed5c-1870">/api/wpr/status</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1870">/api/wpr/status</span></span>
<br />

**<span data-ttu-id="5ed5c-1871">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1871">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1872">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1872">None</span></span>

**<span data-ttu-id="5ed5c-1873">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1873">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1874">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1874">None</span></span>

**<span data-ttu-id="5ed5c-1875">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1875">Request body</span></span>**

- <span data-ttu-id="5ed5c-1876">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1876">None</span></span>

**<span data-ttu-id="5ed5c-1877">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1877">Response</span></span>**

<span data-ttu-id="5ed5c-1878">Der Status der WPR-Ablaufverfolgungssitzung im folgenden Format.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1878">The status of the WPR tracing session in the following format.</span></span>

```
{
    "SessionType": string, (Running or Idle) 
    "State": string (normal or boot)
}
```

**<span data-ttu-id="5ed5c-1879">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1879">Status code</span></span>**

<span data-ttu-id="5ed5c-1880">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1880">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1881">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1881">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1882">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1882">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1883">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1883">200</span></span> | <span data-ttu-id="5ed5c-1884">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1884">OK</span></span>
<span data-ttu-id="5ed5c-1885">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1885">4XX</span></span> | <span data-ttu-id="5ed5c-1886">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1886">Error codes</span></span>
<span data-ttu-id="5ed5c-1887">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1887">5XX</span></span> | <span data-ttu-id="5ed5c-1888">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1888">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1889">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1889">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1890">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1890">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1891">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1891">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1892">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1892">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1893">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1893">IoT</span></span>

---
### <a name="list-completed-tracing-sessions-etls"></a><span data-ttu-id="5ed5c-1894">Aufführen abgeschlossener Ablaufverfolgungssitzungen (ETLs)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1894">List completed tracing sessions (ETLs)</span></span>

**<span data-ttu-id="5ed5c-1895">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1895">Request</span></span>**

<span data-ttu-id="5ed5c-1896">Mit dem folgenden Anforderungsformat können Sie eine Liste mit ETL-Ablaufverfolgungen für das Gerät abrufen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1896">You can get a listing of ETL traces on the device using the following request format.</span></span> 

<span data-ttu-id="5ed5c-1897">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1897">Method</span></span>      | <span data-ttu-id="5ed5c-1898">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1898">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1899">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1899">GET</span></span> | <span data-ttu-id="5ed5c-1900">/api/wpr/tracefiles</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1900">/api/wpr/tracefiles</span></span>
<br />

**<span data-ttu-id="5ed5c-1901">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1901">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-1902">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1902">None</span></span>

**<span data-ttu-id="5ed5c-1903">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1903">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1904">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1904">None</span></span>

**<span data-ttu-id="5ed5c-1905">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1905">Request body</span></span>**

- <span data-ttu-id="5ed5c-1906">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1906">None</span></span>

**<span data-ttu-id="5ed5c-1907">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1907">Response</span></span>**

<span data-ttu-id="5ed5c-1908">Die Liste mit den abgeschlossenen Ablaufverfolgungssitzungen wird im folgenden Format bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1908">The listing of completed tracing sessions is provided in the following format.</span></span>

```
{"Items": [{
    "CurrentDir": string (filepath),
    "DateCreated": int (File CreationTime),
    "FileSize": int (bytes),
    "Id": string (filename),
    "Name": string (filename),
    "SubPath": string (filepath),
    "Type": int
}]}
```

**<span data-ttu-id="5ed5c-1909">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1909">Status code</span></span>**

<span data-ttu-id="5ed5c-1910">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1910">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1911">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1911">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1912">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1912">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1913">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1913">200</span></span> | <span data-ttu-id="5ed5c-1914">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1914">OK</span></span>
<span data-ttu-id="5ed5c-1915">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1915">4XX</span></span> | <span data-ttu-id="5ed5c-1916">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1916">Error codes</span></span>
<span data-ttu-id="5ed5c-1917">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1917">5XX</span></span> | <span data-ttu-id="5ed5c-1918">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1918">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1919">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1919">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1920">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1920">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1921">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1921">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1922">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1922">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1923">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1923">IoT</span></span>

---
### <a name="download-a-tracing-session-etl"></a><span data-ttu-id="5ed5c-1924">Herunterladen einer Ablaufverfolgungssitzung (ETL)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1924">Download a tracing session (ETL)</span></span>

**<span data-ttu-id="5ed5c-1925">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1925">Request</span></span>**

<span data-ttu-id="5ed5c-1926">Mit dem folgenden Anforderungsformat können Sie eine Ablaufverfolgungsdatei (Systemstart- oder Benutzermodus-Ablaufverfolgung) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1926">You can download a tracefile (boot trace or user-mode trace) using the following request format.</span></span> 

<span data-ttu-id="5ed5c-1927">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1927">Method</span></span>      | <span data-ttu-id="5ed5c-1928">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1928">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1929">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1929">GET</span></span> | <span data-ttu-id="5ed5c-1930">/api/wpr/tracefile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1930">/api/wpr/tracefile</span></span>
<br />

**<span data-ttu-id="5ed5c-1931">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1931">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1932">Im Anforderungs-URI kann der folgende zusätzliche Parameter angegeben werden:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1932">You can specify the following additional parameter on the request URI:</span></span>

<span data-ttu-id="5ed5c-1933">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1933">URI parameter</span></span> | <span data-ttu-id="5ed5c-1934">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1934">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1935">filename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1935">filename</span></span>   | <span data-ttu-id="5ed5c-1936">(**erforderlich**) Der Name der herunterzuladenden ETL-Ablaufverfolgung.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1936">(**required**) The name of the ETL trace to download.</span></span>  <span data-ttu-id="5ed5c-1937">Diese befinden sich unter „/api/wpr/tracefiles“.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1937">These can be found in /api/wpr/tracefiles</span></span>

**<span data-ttu-id="5ed5c-1938">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1938">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1939">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1939">None</span></span>

**<span data-ttu-id="5ed5c-1940">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1940">Request body</span></span>**

- <span data-ttu-id="5ed5c-1941">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1941">None</span></span>

**<span data-ttu-id="5ed5c-1942">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1942">Response</span></span>**

- <span data-ttu-id="5ed5c-1943">Gibt die ETL-Ablaufverfolgungsdatei zurück.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1943">Returns the trace ETL file.</span></span>

**<span data-ttu-id="5ed5c-1944">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1944">Status code</span></span>**

<span data-ttu-id="5ed5c-1945">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1945">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1946">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1946">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1947">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1947">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1948">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1948">200</span></span> | <span data-ttu-id="5ed5c-1949">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1949">OK</span></span>
<span data-ttu-id="5ed5c-1950">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1950">4XX</span></span> | <span data-ttu-id="5ed5c-1951">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1951">Error codes</span></span>
<span data-ttu-id="5ed5c-1952">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1952">5XX</span></span> | <span data-ttu-id="5ed5c-1953">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1953">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1954">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1954">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1955">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1955">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1956">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1956">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1957">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1957">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1958">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1958">IoT</span></span>

---
### <a name="delete-a-tracing-session-etl"></a><span data-ttu-id="5ed5c-1959">Löschen einer Ablaufverfolgungssitzung (ETL)</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1959">Delete a tracing session (ETL)</span></span>

**<span data-ttu-id="5ed5c-1960">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1960">Request</span></span>**

<span data-ttu-id="5ed5c-1961">Mit dem folgenden Anforderungsformat können Sie eine Ablaufverfolgungsdatei (Systemstart- oder Benutzermodus-Ablaufverfolgung) löschen.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1961">You can delete a tracefile (boot trace or user-mode trace) using the following request format.</span></span> 

<span data-ttu-id="5ed5c-1962">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1962">Method</span></span>      | <span data-ttu-id="5ed5c-1963">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1963">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1964">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1964">DELETE</span></span> | <span data-ttu-id="5ed5c-1965">/api/wpr/tracefile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1965">/api/wpr/tracefile</span></span>
<br />

**<span data-ttu-id="5ed5c-1966">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1966">URI parameters</span></span>**

<span data-ttu-id="5ed5c-1967">Im Anforderungs-URI kann der folgende zusätzliche Parameter angegeben werden:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1967">You can specify the following additional parameter on the request URI:</span></span>

<span data-ttu-id="5ed5c-1968">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1968">URI parameter</span></span> | <span data-ttu-id="5ed5c-1969">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1969">Description</span></span>
:---          | :---
<span data-ttu-id="5ed5c-1970">filename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1970">filename</span></span>   | <span data-ttu-id="5ed5c-1971">(**erforderlich**) Der Name der zu löschenden ETL-Ablaufverfolgung.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1971">(**required**) The name of the ETL trace to delete.</span></span>  <span data-ttu-id="5ed5c-1972">Diese befinden sich unter „/api/wpr/tracefiles“.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1972">These can be found in /api/wpr/tracefiles</span></span>

**<span data-ttu-id="5ed5c-1973">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1973">Request headers</span></span>**

- <span data-ttu-id="5ed5c-1974">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1974">None</span></span>

**<span data-ttu-id="5ed5c-1975">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1975">Request body</span></span>**

- <span data-ttu-id="5ed5c-1976">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1976">None</span></span>

**<span data-ttu-id="5ed5c-1977">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1977">Response</span></span>**

- <span data-ttu-id="5ed5c-1978">Gibt die ETL-Ablaufverfolgungsdatei zurück.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1978">Returns the trace ETL file.</span></span>

**<span data-ttu-id="5ed5c-1979">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1979">Status code</span></span>**

<span data-ttu-id="5ed5c-1980">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1980">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-1981">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1981">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-1982">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1982">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-1983">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1983">200</span></span> | <span data-ttu-id="5ed5c-1984">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1984">OK</span></span>
<span data-ttu-id="5ed5c-1985">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1985">4XX</span></span> | <span data-ttu-id="5ed5c-1986">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1986">Error codes</span></span>
<span data-ttu-id="5ed5c-1987">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1987">5XX</span></span> | <span data-ttu-id="5ed5c-1988">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1988">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-1989">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1989">Available device families</span></span>**

* <span data-ttu-id="5ed5c-1990">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1990">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-1991">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1991">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-1992">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1992">HoloLens</span></span>
* <span data-ttu-id="5ed5c-1993">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1993">IoT</span></span>

---
## DNS-SD Tags 
---
### <a name="view-tags"></a><span data-ttu-id="5ed5c-1994">Anzeigen von Tags</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1994">View Tags</span></span>

**<span data-ttu-id="5ed5c-1995">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1995">Request</span></span>**

<span data-ttu-id="5ed5c-1996">Anzeigen der derzeit für das Gerät angewendeten Tags.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1996">View the currently applied tags for the device.</span></span>  <span data-ttu-id="5ed5c-1997">Diese werden über DNS-SD-TXT-Datensätze im T-Schlüssel angekündigt.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1997">These are advertised via DNS-SD TXT records in the T key.</span></span>  
 
<span data-ttu-id="5ed5c-1998">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1998">Method</span></span>      | <span data-ttu-id="5ed5c-1999">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-1999">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2000">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2000">GET</span></span> | <span data-ttu-id="5ed5c-2001">/api/dns-sd/tags</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2001">/api/dns-sd/tags</span></span>
<br />

**<span data-ttu-id="5ed5c-2002">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2002">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-2003">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2003">None</span></span>

**<span data-ttu-id="5ed5c-2004">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2004">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2005">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2005">None</span></span>

**<span data-ttu-id="5ed5c-2006">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2006">Request body</span></span>**

- <span data-ttu-id="5ed5c-2007">Keiner</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2007">None</span></span>

<span data-ttu-id="5ed5c-2008">**Antwort** Die derzeit angewendeten Tags im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2008">**Response** The currently applied tags in the following format.</span></span> 
```
 {
    "tags": [
        "tag1", 
        "tag2", 
        ...
     ]
}
```

**<span data-ttu-id="5ed5c-2009">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2009">Status code</span></span>**

<span data-ttu-id="5ed5c-2010">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2010">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2011">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2011">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2012">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2012">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2013">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2013">200</span></span> | <span data-ttu-id="5ed5c-2014">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2014">OK</span></span>
<span data-ttu-id="5ed5c-2015">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2015">5XX</span></span> | <span data-ttu-id="5ed5c-2016">Serverfehler</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2016">Server Error</span></span> 

<br />
**<span data-ttu-id="5ed5c-2017">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2017">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2018">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2018">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2019">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2019">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2020">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2020">Xbox</span></span>
* <span data-ttu-id="5ed5c-2021">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2021">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2022">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2022">IoT</span></span>

---
### <a name="delete-tags"></a><span data-ttu-id="5ed5c-2023">Löschen von Tags</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2023">Delete Tags</span></span>

**<span data-ttu-id="5ed5c-2024">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2024">Request</span></span>**

<span data-ttu-id="5ed5c-2025">Löschen aller Tags derzeit von DNS-SD angekündigten Tags.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2025">Delete all tags currently advertised by DNS-SD.</span></span>   
 
<span data-ttu-id="5ed5c-2026">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2026">Method</span></span>      | <span data-ttu-id="5ed5c-2027">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2027">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2028">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2028">DELETE</span></span> | <span data-ttu-id="5ed5c-2029">/api/dns-sd/tags</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2029">/api/dns-sd/tags</span></span>
<br />

**<span data-ttu-id="5ed5c-2030">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2030">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-2031">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2031">None</span></span>

**<span data-ttu-id="5ed5c-2032">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2032">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2033">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2033">None</span></span>

**<span data-ttu-id="5ed5c-2034">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2034">Request body</span></span>**

- <span data-ttu-id="5ed5c-2035">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2035">None</span></span>

**<span data-ttu-id="5ed5c-2036">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2036">Response</span></span>**
 - <span data-ttu-id="5ed5c-2037">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2037">None</span></span>

**<span data-ttu-id="5ed5c-2038">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2038">Status code</span></span>**

<span data-ttu-id="5ed5c-2039">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2039">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2040">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2040">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2041">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2041">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2042">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2042">200</span></span> | <span data-ttu-id="5ed5c-2043">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2043">OK</span></span>
<span data-ttu-id="5ed5c-2044">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2044">5XX</span></span> | <span data-ttu-id="5ed5c-2045">Serverfehler</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2045">Server Error</span></span> 

<br />
**<span data-ttu-id="5ed5c-2046">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2046">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2047">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2047">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2048">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2048">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2049">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2049">Xbox</span></span>
* <span data-ttu-id="5ed5c-2050">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2050">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2051">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2051">IoT</span></span>

---
### <a name="delete-tag"></a><span data-ttu-id="5ed5c-2052">Löschen eines Tags</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2052">Delete Tag</span></span>

**<span data-ttu-id="5ed5c-2053">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2053">Request</span></span>**

<span data-ttu-id="5ed5c-2054">Löschen eines derzeit von DNS-SD angekündigten Tags.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2054">Delete a tag currently advertised by DNS-SD.</span></span>   
 
<span data-ttu-id="5ed5c-2055">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2055">Method</span></span>      | <span data-ttu-id="5ed5c-2056">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2056">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2057">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2057">DELETE</span></span> | <span data-ttu-id="5ed5c-2058">/api/dns-sd/tag</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2058">/api/dns-sd/tag</span></span>
<br />

**<span data-ttu-id="5ed5c-2059">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2059">URI parameters</span></span>**

<span data-ttu-id="5ed5c-2060">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2060">URI parameter</span></span> | <span data-ttu-id="5ed5c-2061">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2061">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2062">tagValue</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2062">tagValue</span></span> | <span data-ttu-id="5ed5c-2063">(**Erforderlich**) Das zu entfernende Tag.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2063">(**required**) The tag to be removed.</span></span>

**<span data-ttu-id="5ed5c-2064">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2064">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2065">Keiner</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2065">None</span></span>

**<span data-ttu-id="5ed5c-2066">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2066">Request body</span></span>**

- <span data-ttu-id="5ed5c-2067">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2067">None</span></span>

**<span data-ttu-id="5ed5c-2068">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2068">Response</span></span>**
 - <span data-ttu-id="5ed5c-2069">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2069">None</span></span>

**<span data-ttu-id="5ed5c-2070">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2070">Status code</span></span>**

<span data-ttu-id="5ed5c-2071">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2071">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2072">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2072">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2073">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2073">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2074">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2074">200</span></span> | <span data-ttu-id="5ed5c-2075">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2075">OK</span></span>

<br />
**<span data-ttu-id="5ed5c-2076">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2076">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2077">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2077">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2078">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2078">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2079">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2079">Xbox</span></span>
* <span data-ttu-id="5ed5c-2080">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2080">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2081">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2081">IoT</span></span>
 
---
### <a name="add-a-tag"></a><span data-ttu-id="5ed5c-2082">Hinzufügen eines Tags</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2082">Add a Tag</span></span>

**<span data-ttu-id="5ed5c-2083">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2083">Request</span></span>**

<span data-ttu-id="5ed5c-2084">Hinzufügen eines Tags zur DNS-SD-Ankündigung.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2084">Add a tag to the DNS-SD advertisement.</span></span>   
 
<span data-ttu-id="5ed5c-2085">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2085">Method</span></span>      | <span data-ttu-id="5ed5c-2086">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2086">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2087">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2087">POST</span></span> | <span data-ttu-id="5ed5c-2088">/api/dns-sd/tag</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2088">/api/dns-sd/tag</span></span>
<br />

**<span data-ttu-id="5ed5c-2089">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2089">URI parameters</span></span>**

<span data-ttu-id="5ed5c-2090">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2090">URI parameter</span></span> | <span data-ttu-id="5ed5c-2091">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2091">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2092">tagValue</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2092">tagValue</span></span> | <span data-ttu-id="5ed5c-2093">(**Erforderlich**) Das hinzuzufügende Tag.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2093">(**required**) The tag to be added.</span></span>

**<span data-ttu-id="5ed5c-2094">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2094">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2095">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2095">None</span></span>

**<span data-ttu-id="5ed5c-2096">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2096">Request body</span></span>**

- <span data-ttu-id="5ed5c-2097">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2097">None</span></span>

**<span data-ttu-id="5ed5c-2098">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2098">Response</span></span>**
 - <span data-ttu-id="5ed5c-2099">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2099">None</span></span>

**<span data-ttu-id="5ed5c-2100">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2100">Status code</span></span>**

<span data-ttu-id="5ed5c-2101">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2101">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2102">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2102">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2103">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2103">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2104">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2104">200</span></span> | <span data-ttu-id="5ed5c-2105">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2105">OK</span></span>
<span data-ttu-id="5ed5c-2106">401</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2106">401</span></span> | <span data-ttu-id="5ed5c-2107">Überlauf des Tagbereichs.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2107">Tag space Overflow.</span></span>  <span data-ttu-id="5ed5c-2108">Tritt auf, wenn das vorgeschlagene Tag zu lang für den resultierenden DNS-SD-Dienstdatensatz ist.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2108">Results when the proposed tag is too long for the resulting DNS-SD service record.</span></span>  

<br />
**<span data-ttu-id="5ed5c-2109">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2109">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2110">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2110">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2111">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2111">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2112">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2112">Xbox</span></span>
* <span data-ttu-id="5ed5c-2113">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2113">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2114">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2114">IoT</span></span>

## <a name="app-file-explorer"></a><span data-ttu-id="5ed5c-2115">App-Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2115">App File Explorer</span></span>

---
### <a name="get-known-folders"></a><span data-ttu-id="5ed5c-2116">Abrufen bekannter Ordner</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2116">Get known folders</span></span>

**<span data-ttu-id="5ed5c-2117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2117">Request</span></span>**

<span data-ttu-id="5ed5c-2118">Abrufen einer Liste zugänglicher Ordner der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2118">Obtain a list of accessible top-level folders.</span></span>

<span data-ttu-id="5ed5c-2119">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2119">Method</span></span>      | <span data-ttu-id="5ed5c-2120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2120">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2121">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2121">GET</span></span> | <span data-ttu-id="5ed5c-2122">/api/filesystem/apps/knownfolders</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2122">/api/filesystem/apps/knownfolders</span></span>
<br />

**<span data-ttu-id="5ed5c-2123">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2123">URI parameters</span></span>**

- <span data-ttu-id="5ed5c-2124">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2124">None</span></span>

**<span data-ttu-id="5ed5c-2125">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2125">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2126">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2126">None</span></span>

**<span data-ttu-id="5ed5c-2127">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2127">Request body</span></span>**

- <span data-ttu-id="5ed5c-2128">Keiner</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2128">None</span></span>

<span data-ttu-id="5ed5c-2129">**Antwort** Die verfügbaren Ordner im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2129">**Response** The available folders in the following format.</span></span> 
```
 {"KnownFolders": [
    "folder0",
    "folder1",...
]}
```
**<span data-ttu-id="5ed5c-2130">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2130">Status code</span></span>**

<span data-ttu-id="5ed5c-2131">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2131">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2132">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2132">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2133">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2134">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2134">200</span></span> | <span data-ttu-id="5ed5c-2135">Bereitstellungsanforderung akzeptiert und wird verarbeitet</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2135">Deploy request accepted and being processed</span></span>
<span data-ttu-id="5ed5c-2136">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2136">4XX</span></span> | <span data-ttu-id="5ed5c-2137">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2137">Error codes</span></span>
<span data-ttu-id="5ed5c-2138">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2138">5XX</span></span> | <span data-ttu-id="5ed5c-2139">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2139">Error codes</span></span>
<br />

**<span data-ttu-id="5ed5c-2140">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2140">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2141">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2141">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2142">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2142">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2143">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2143">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2144">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2144">Xbox</span></span>
* <span data-ttu-id="5ed5c-2145">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2145">IoT</span></span>

---
### <a name="get-files"></a><span data-ttu-id="5ed5c-2146">Abrufen von Dateien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2146">Get files</span></span>

**<span data-ttu-id="5ed5c-2147">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2147">Request</span></span>**

<span data-ttu-id="5ed5c-2148">Abrufen einer Liste von Dateien in einem Ordner.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2148">Obtain a list of files in a folder.</span></span>

<span data-ttu-id="5ed5c-2149">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2149">Method</span></span>      | <span data-ttu-id="5ed5c-2150">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2150">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2151">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2151">GET</span></span> | <span data-ttu-id="5ed5c-2152">/api/filesystem/apps/files</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2152">/api/filesystem/apps/files</span></span>
<br />

**<span data-ttu-id="5ed5c-2153">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2153">URI parameters</span></span>**

<span data-ttu-id="5ed5c-2154">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2154">URI parameter</span></span> | <span data-ttu-id="5ed5c-2155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2155">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2156">knownfolderid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2156">knownfolderid</span></span> | <span data-ttu-id="5ed5c-2157">(**Erforderlich**) Das Verzeichnis auf oberster Ebene, das die Liste der Dateien enthalten soll.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2157">(**required**) The top-level directory where you want the list of files.</span></span> <span data-ttu-id="5ed5c-2158">Verwenden Sie **LocalAppData** für den Zugriff auf quergeladene Apps.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2158">Use **LocalAppData** for access to sideloaded apps.</span></span> 
<span data-ttu-id="5ed5c-2159">packagefullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2159">packagefullname</span></span> | <span data-ttu-id="5ed5c-2160">(**Erforderlich, wenn *knownfolderid* == LocalAppData**) Der vollständige Name des Pakets der App, für die Sie sich interessieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2160">(**required if *knownfolderid* == LocalAppData**) The package full name of the app you are interested in.</span></span> 
<span data-ttu-id="5ed5c-2161">path</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2161">path</span></span> | <span data-ttu-id="5ed5c-2162">(**Optional**) Das Unterverzeichnis in dem oben angegebenen Ordner oder Paket.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2162">(**optional**) The sub-directory within the folder or package specified above.</span></span> 

**<span data-ttu-id="5ed5c-2163">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2163">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2164">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2164">None</span></span>

**<span data-ttu-id="5ed5c-2165">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2165">Request body</span></span>**

- <span data-ttu-id="5ed5c-2166">Keiner</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2166">None</span></span>

<span data-ttu-id="5ed5c-2167">**Antwort** Die verfügbaren Ordner im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2167">**Response** The available folders in the following format.</span></span> 
```
{"Items": [
    {
        "CurrentDir": string (folder under the requested known folder),
        "DateCreated": int,
        "FileSize": int (bytes),
        "Id": string,
        "Name": string,
        "SubPath": string (present if this item is a folder, this is the name of the folder),
        "Type": int
    },...
]}
```
**<span data-ttu-id="5ed5c-2168">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2168">Status code</span></span>**

<span data-ttu-id="5ed5c-2169">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2169">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2170">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2170">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2171">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2171">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2172">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2172">200</span></span> | <span data-ttu-id="5ed5c-2173">OK</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2173">OK</span></span>
<span data-ttu-id="5ed5c-2174">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2174">4XX</span></span> | <span data-ttu-id="5ed5c-2175">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2175">Error codes</span></span>
<span data-ttu-id="5ed5c-2176">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2176">5XX</span></span> | <span data-ttu-id="5ed5c-2177">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2177">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-2178">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2178">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2179">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2179">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2180">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2180">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2181">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2181">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2182">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2182">Xbox</span></span>
* <span data-ttu-id="5ed5c-2183">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2183">IoT</span></span>

---
### <a name="download-a-file"></a><span data-ttu-id="5ed5c-2184">Herunterladen einer Datei</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2184">Download a file</span></span>

**<span data-ttu-id="5ed5c-2185">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2185">Request</span></span>**

<span data-ttu-id="5ed5c-2186">Abrufen einer Datei aus einem bekannten Ordner oder aus „appLocalData“</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2186">Obtain a file from a known folder or appLocalData.</span></span>

<span data-ttu-id="5ed5c-2187">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2187">Method</span></span>      | <span data-ttu-id="5ed5c-2188">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2188">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2189">GET</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2189">GET</span></span> | <span data-ttu-id="5ed5c-2190">/api/filesystem/apps/file</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2190">/api/filesystem/apps/file</span></span>

**<span data-ttu-id="5ed5c-2191">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2191">URI parameters</span></span>**

<span data-ttu-id="5ed5c-2192">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2192">URI parameter</span></span> | <span data-ttu-id="5ed5c-2193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2193">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2194">knownfolderid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2194">knownfolderid</span></span> | <span data-ttu-id="5ed5c-2195">(**Erforderlich**) Das Verzeichnis auf oberster Ebene, in das Sie Dateien herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2195">(**required**) The top-level directory where you want to download files.</span></span> <span data-ttu-id="5ed5c-2196">Verwenden Sie **LocalAppData** für den Zugriff auf quergeladene Apps.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2196">Use **LocalAppData** for access to sideloaded apps.</span></span> 
<span data-ttu-id="5ed5c-2197">filename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2197">filename</span></span> | <span data-ttu-id="5ed5c-2198">(**Erforderlich**) Der Name der Datei, die heruntergeladen wird.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2198">(**required**) The name of the file being downloaded.</span></span> 
<span data-ttu-id="5ed5c-2199">packagefullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2199">packagefullname</span></span> | <span data-ttu-id="5ed5c-2200">(**Erforderlich, wenn *knownfolderid* == LocalAppData**) Der vollständige Name des Pakets, für das Sie sich interessieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2200">(**required if *knownfolderid* == LocalAppData**) The package full name you are interested in.</span></span> 
<span data-ttu-id="5ed5c-2201">path</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2201">path</span></span> | <span data-ttu-id="5ed5c-2202">(**Optional**) Das Unterverzeichnis in dem oben angegebenen Ordner oder Paket.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2202">(**optional**) The sub-directory within the folder or package specified above.</span></span>

**<span data-ttu-id="5ed5c-2203">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2203">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2204">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2204">None</span></span>

**<span data-ttu-id="5ed5c-2205">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2205">Request body</span></span>**

- <span data-ttu-id="5ed5c-2206">Die angeforderte Datei, sofern vorhanden</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2206">The file requested, if present</span></span>

**<span data-ttu-id="5ed5c-2207">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2207">Response</span></span>**

**<span data-ttu-id="5ed5c-2208">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2208">Status code</span></span>**

<span data-ttu-id="5ed5c-2209">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2209">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2210">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2210">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2211">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2211">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2212">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2212">200</span></span> | <span data-ttu-id="5ed5c-2213">Die angeforderte Datei</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2213">The requested file</span></span>
<span data-ttu-id="5ed5c-2214">404</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2214">404</span></span> | <span data-ttu-id="5ed5c-2215">Datei nicht gefunden</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2215">File not found</span></span>
<span data-ttu-id="5ed5c-2216">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2216">5XX</span></span> | <span data-ttu-id="5ed5c-2217">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2217">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-2218">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2218">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2219">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2219">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2220">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2220">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2221">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2221">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2222">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2222">Xbox</span></span>
* <span data-ttu-id="5ed5c-2223">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2223">IoT</span></span>

---
### <a name="rename-a-file"></a><span data-ttu-id="5ed5c-2224">Umbenennen einer Datei</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2224">Rename a file</span></span>

**<span data-ttu-id="5ed5c-2225">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2225">Request</span></span>**

<span data-ttu-id="5ed5c-2226">Umbenennen einer Datei in einem Ordner.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2226">Rename a file in a folder.</span></span>

<span data-ttu-id="5ed5c-2227">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2227">Method</span></span>      | <span data-ttu-id="5ed5c-2228">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2228">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2229">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2229">POST</span></span> | <span data-ttu-id="5ed5c-2230">/api/filesystem/apps/rename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2230">/api/filesystem/apps/rename</span></span>

<br />
**<span data-ttu-id="5ed5c-2231">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2231">URI parameters</span></span>**

<span data-ttu-id="5ed5c-2232">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2232">URI parameter</span></span> | <span data-ttu-id="5ed5c-2233">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2233">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2234">knownfolderid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2234">knownfolderid</span></span> | <span data-ttu-id="5ed5c-2235">(**Erforderlich**) Das übergeordnete Verzeichnis, in dem sich die Datei befindet.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2235">(**required**) The top-level directory where the file is located.</span></span> <span data-ttu-id="5ed5c-2236">Verwenden Sie **LocalAppData** für den Zugriff auf quergeladene Apps.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2236">Use **LocalAppData** for access to sideloaded apps.</span></span> 
<span data-ttu-id="5ed5c-2237">filename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2237">filename</span></span> | <span data-ttu-id="5ed5c-2238">(**Erforderlich**) Der ursprüngliche Name der umzubenennenden Datei.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2238">(**required**) The original name of the file being renamed.</span></span> 
<span data-ttu-id="5ed5c-2239">newfilename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2239">newfilename</span></span> | <span data-ttu-id="5ed5c-2240">(**erforderlich**) Der neue Name der Datei.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2240">(**required**) The new name of the file.</span></span>
<span data-ttu-id="5ed5c-2241">packagefullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2241">packagefullname</span></span> | <span data-ttu-id="5ed5c-2242">(**Erforderlich, wenn *knownfolderid* == LocalAppData**) Der vollständige Name des Pakets der App, für die Sie sich interessieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2242">(**required if *knownfolderid* == LocalAppData**) The package full name of the app you are interested in.</span></span> 
<span data-ttu-id="5ed5c-2243">path</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2243">path</span></span> | <span data-ttu-id="5ed5c-2244">(**Optional**) Das Unterverzeichnis in dem oben angegebenen Ordner oder Paket.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2244">(**optional**) The sub-directory within the folder or package specified above.</span></span> 

**<span data-ttu-id="5ed5c-2245">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2245">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2246">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2246">None</span></span>

**<span data-ttu-id="5ed5c-2247">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2247">Request body</span></span>**

- <span data-ttu-id="5ed5c-2248">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2248">None</span></span>

**<span data-ttu-id="5ed5c-2249">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2249">Response</span></span>**

- <span data-ttu-id="5ed5c-2250">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2250">None</span></span>

**<span data-ttu-id="5ed5c-2251">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2251">Status code</span></span>**

<span data-ttu-id="5ed5c-2252">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2252">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2253">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2253">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2254">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2254">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2255">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2255">200</span></span> | <span data-ttu-id="5ed5c-2256">OK.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2256">OK.</span></span> <span data-ttu-id="5ed5c-2257">Datei umbenannt</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2257">The file is renamed</span></span>
<span data-ttu-id="5ed5c-2258">404</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2258">404</span></span> | <span data-ttu-id="5ed5c-2259">Datei nicht gefunden</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2259">File not found</span></span>
<span data-ttu-id="5ed5c-2260">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2260">5XX</span></span> | <span data-ttu-id="5ed5c-2261">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2261">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-2262">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2262">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2263">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2263">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2264">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2264">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2265">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2265">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2266">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2266">Xbox</span></span>
* <span data-ttu-id="5ed5c-2267">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2267">IoT</span></span>

---
### <a name="delete-a-file"></a><span data-ttu-id="5ed5c-2268">Löschen einer Datei</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2268">Delete a file</span></span>

**<span data-ttu-id="5ed5c-2269">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2269">Request</span></span>**

<span data-ttu-id="5ed5c-2270">Löschen einer Datei in einem Ordner.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2270">Delete a file in a folder.</span></span>

<span data-ttu-id="5ed5c-2271">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2271">Method</span></span>      | <span data-ttu-id="5ed5c-2272">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2272">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2273">DELETE</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2273">DELETE</span></span> | <span data-ttu-id="5ed5c-2274">/api/filesystem/apps/file</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2274">/api/filesystem/apps/file</span></span>
<br />
**<span data-ttu-id="5ed5c-2275">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2275">URI parameters</span></span>**

<span data-ttu-id="5ed5c-2276">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2276">URI parameter</span></span> | <span data-ttu-id="5ed5c-2277">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2277">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2278">knownfolderid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2278">knownfolderid</span></span> | <span data-ttu-id="5ed5c-2279">(**Erforderlich**) Das Verzeichnis auf oberster Ebene, in dem Sie Dateien löschen möchten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2279">(**required**) The top-level directory where you want to delete files.</span></span> <span data-ttu-id="5ed5c-2280">Verwenden Sie **LocalAppData** für den Zugriff auf quergeladene Apps.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2280">Use **LocalAppData** for access to sideloaded apps.</span></span> 
<span data-ttu-id="5ed5c-2281">filename</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2281">filename</span></span> | <span data-ttu-id="5ed5c-2282">(**erforderlich**) Der Name der zu löschenden Datei.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2282">(**required**) The name of the file being deleted.</span></span> 
<span data-ttu-id="5ed5c-2283">packagefullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2283">packagefullname</span></span> | <span data-ttu-id="5ed5c-2284">(**Erforderlich, wenn *knownfolderid* == LocalAppData**) Der vollständige Name des Pakets der App, für die Sie sich interessieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2284">(**required if *knownfolderid* == LocalAppData**) The package full name of the app you are interested in.</span></span> 
<span data-ttu-id="5ed5c-2285">path</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2285">path</span></span> | <span data-ttu-id="5ed5c-2286">(**Optional**) Das Unterverzeichnis in dem oben angegebenen Ordner oder Paket.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2286">(**optional**) The sub-directory within the folder or package specified above.</span></span>

**<span data-ttu-id="5ed5c-2287">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2287">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2288">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2288">None</span></span>

**<span data-ttu-id="5ed5c-2289">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2289">Request body</span></span>**

- <span data-ttu-id="5ed5c-2290">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2290">None</span></span>

**<span data-ttu-id="5ed5c-2291">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2291">Response</span></span>**

- <span data-ttu-id="5ed5c-2292">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2292">None</span></span> 

**<span data-ttu-id="5ed5c-2293">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2293">Status code</span></span>**

<span data-ttu-id="5ed5c-2294">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2294">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2295">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2295">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2296">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2296">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2297">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2297">200</span></span> | <span data-ttu-id="5ed5c-2298">OK.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2298">OK.</span></span> <span data-ttu-id="5ed5c-2299">Die Datei wird gelöscht.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2299">The file is deleted</span></span>
<span data-ttu-id="5ed5c-2300">404</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2300">404</span></span> | <span data-ttu-id="5ed5c-2301">Datei nicht gefunden</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2301">File not found</span></span>
<span data-ttu-id="5ed5c-2302">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2302">5XX</span></span> | <span data-ttu-id="5ed5c-2303">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2303">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-2304">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2304">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2305">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2305">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2306">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2306">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2307">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2307">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2308">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2308">Xbox</span></span>
* <span data-ttu-id="5ed5c-2309">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2309">IoT</span></span>

---
### <a name="upload-a-file"></a><span data-ttu-id="5ed5c-2310">Hochladen einer Datei</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2310">Upload a file</span></span>

**<span data-ttu-id="5ed5c-2311">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2311">Request</span></span>**

<span data-ttu-id="5ed5c-2312">Hochladen einer Datei in einen Ordner.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2312">Upload a file to a folder.</span></span>  <span data-ttu-id="5ed5c-2313">Dadurch wird eine vorhandene Datei mit demselben Namen überschrieben, es werden jedoch keine neuen Ordner erstellt.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2313">This will overwrite an existing file with the same name, but will not create new folders.</span></span> 

<span data-ttu-id="5ed5c-2314">Methode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2314">Method</span></span>      | <span data-ttu-id="5ed5c-2315">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2315">Request URI</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2316">POST</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2316">POST</span></span> | <span data-ttu-id="5ed5c-2317">/api/filesystem/apps/file</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2317">/api/filesystem/apps/file</span></span>
<br />
**<span data-ttu-id="5ed5c-2318">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2318">URI parameters</span></span>**

<span data-ttu-id="5ed5c-2319">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2319">URI parameter</span></span> | <span data-ttu-id="5ed5c-2320">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2320">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2321">knownfolderid</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2321">knownfolderid</span></span> | <span data-ttu-id="5ed5c-2322">(**Erforderlich**) Das Verzeichnis auf oberster Ebene, in das Sie Dateien hochladen möchten.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2322">(**required**) The top-level directory where you want to upload files.</span></span> <span data-ttu-id="5ed5c-2323">Verwenden Sie **LocalAppData** für den Zugriff auf quergeladene Apps.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2323">Use **LocalAppData** for access to sideloaded apps.</span></span>
<span data-ttu-id="5ed5c-2324">packagefullname</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2324">packagefullname</span></span> | <span data-ttu-id="5ed5c-2325">(**Erforderlich, wenn *knownfolderid* == LocalAppData**) Der vollständige Name des Pakets der App, für die Sie sich interessieren.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2325">(**required if *knownfolderid* == LocalAppData**) The package full name of the app you are interested in.</span></span> 
<span data-ttu-id="5ed5c-2326">path</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2326">path</span></span> | <span data-ttu-id="5ed5c-2327">(**Optional**) Das Unterverzeichnis in dem oben angegebenen Ordner oder Paket.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2327">(**optional**) The sub-directory within the folder or package specified above.</span></span>

**<span data-ttu-id="5ed5c-2328">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2328">Request headers</span></span>**

- <span data-ttu-id="5ed5c-2329">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2329">None</span></span>

**<span data-ttu-id="5ed5c-2330">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2330">Request body</span></span>**

- <span data-ttu-id="5ed5c-2331">Keine</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2331">None</span></span>

**<span data-ttu-id="5ed5c-2332">Antwort</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2332">Response</span></span>**

**<span data-ttu-id="5ed5c-2333">Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2333">Status code</span></span>**

<span data-ttu-id="5ed5c-2334">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2334">This API has the following expected status codes.</span></span>

<span data-ttu-id="5ed5c-2335">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2335">HTTP status code</span></span>      | <span data-ttu-id="5ed5c-2336">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2336">Description</span></span>
:------     | :-----
<span data-ttu-id="5ed5c-2337">200</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2337">200</span></span> | <span data-ttu-id="5ed5c-2338">OK.</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2338">OK.</span></span> <span data-ttu-id="5ed5c-2339">Die Datei wird hochgeladen</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2339">The file is uploaded</span></span>
<span data-ttu-id="5ed5c-2340">4XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2340">4XX</span></span> | <span data-ttu-id="5ed5c-2341">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2341">Error codes</span></span>
<span data-ttu-id="5ed5c-2342">5XX</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2342">5XX</span></span> | <span data-ttu-id="5ed5c-2343">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2343">Error codes</span></span>
<br />
**<span data-ttu-id="5ed5c-2344">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2344">Available device families</span></span>**

* <span data-ttu-id="5ed5c-2345">Windows Mobile</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2345">Windows Mobile</span></span>
* <span data-ttu-id="5ed5c-2346">Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2346">Windows Desktop</span></span>
* <span data-ttu-id="5ed5c-2347">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2347">HoloLens</span></span>
* <span data-ttu-id="5ed5c-2348">Xbox</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2348">Xbox</span></span>
* <span data-ttu-id="5ed5c-2349">IoT</span><span class="sxs-lookup"><span data-stu-id="5ed5c-2349">IoT</span></span>