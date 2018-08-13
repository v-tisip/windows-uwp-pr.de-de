---
author: WilliamsJason
title: Gerät Portal Netzwerk Anmeldeinformationen-API-Referenz
description: Informationen Sie zum Hinzufügen, entfernen oder aktualisieren die Anmeldeinformationen für das Netzwerk Anzeigeformats.
ms.localizationpriority: medium
ms.openlocfilehash: 7e00169f92ee6f0aa48df64ec4a1186f9682b358
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "410174"
---
# <a name="network-credentials-api-reference"></a><span data-ttu-id="bea55-103">Netzwerk-Anmeldeinformationen-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="bea55-103">Network Credentials API reference</span></span>
<span data-ttu-id="bea55-104">Sie können hinzufügen, entfernen oder Aktualisieren von gespeicherten Netzwerkanmeldeinformationen auf Ihre Devkit verwenden dieses REST-API.</span><span class="sxs-lookup"><span data-stu-id="bea55-104">You can add, remove, or update stored network credentials on your devkit using this REST API.</span></span>

## <a name="get-existing-credentials"></a><span data-ttu-id="bea55-105">Abrufen von vorhandenen Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="bea55-105">Get existing credentials</span></span>

**<span data-ttu-id="bea55-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bea55-106">Request</span></span>**

<span data-ttu-id="bea55-107">Sie können eine Liste der gespeicherten Freigaben zusammen mit den Benutzernamen des Benutzers abrufen, die Anmeldeinformationen für diese Netzwerkfreigabe verfügt.</span><span class="sxs-lookup"><span data-stu-id="bea55-107">You can get a list of the stored shares along with the username of the user who has credentials for that network share.</span></span>

<span data-ttu-id="bea55-108">Methode</span><span class="sxs-lookup"><span data-stu-id="bea55-108">Method</span></span>      | <span data-ttu-id="bea55-109">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="bea55-109">Request URI</span></span>
:------     | :-----
<span data-ttu-id="bea55-110">GET</span><span class="sxs-lookup"><span data-stu-id="bea55-110">GET</span></span> | <span data-ttu-id="bea55-111">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="bea55-111">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="bea55-112">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="bea55-112">URI parameters</span></span>**

- <span data-ttu-id="bea55-113">Keine</span><span class="sxs-lookup"><span data-stu-id="bea55-113">None</span></span>

**<span data-ttu-id="bea55-114">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="bea55-114">Request headers</span></span>**

- <span data-ttu-id="bea55-115">Keine</span><span class="sxs-lookup"><span data-stu-id="bea55-115">None</span></span>

**<span data-ttu-id="bea55-116">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="bea55-116">Request body</span></span>**   

- <span data-ttu-id="bea55-117">Keine</span><span class="sxs-lookup"><span data-stu-id="bea55-117">None</span></span>

**<span data-ttu-id="bea55-118">Antwort</span><span class="sxs-lookup"><span data-stu-id="bea55-118">Response</span></span>**   

- <span data-ttu-id="bea55-119">JSON-Array im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="bea55-119">JSON array in the following format:</span></span>
* <span data-ttu-id="bea55-120">Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="bea55-120">Credentials</span></span>
  * <span data-ttu-id="bea55-121">NetworkPath - den Pfad der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="bea55-121">NetworkPath - The path to the network share.</span></span>
  * <span data-ttu-id="bea55-122">UserName - den Benutzernamen, der Anmeldeinformationen gespeichert hat.</span><span class="sxs-lookup"><span data-stu-id="bea55-122">Username - The username which has stored credentials.</span></span>

**<span data-ttu-id="bea55-123">Statuscode</span><span class="sxs-lookup"><span data-stu-id="bea55-123">Status code</span></span>**

<span data-ttu-id="bea55-124">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="bea55-124">This API has the following expected status codes.</span></span>

<span data-ttu-id="bea55-125">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="bea55-125">HTTP status code</span></span>      | <span data-ttu-id="bea55-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bea55-126">Description</span></span>
:------     | :-----
<span data-ttu-id="bea55-127">200</span><span class="sxs-lookup"><span data-stu-id="bea55-127">200</span></span> | <span data-ttu-id="bea55-128">Erfolg</span><span class="sxs-lookup"><span data-stu-id="bea55-128">Success</span></span>
<span data-ttu-id="bea55-129">4XX</span><span class="sxs-lookup"><span data-stu-id="bea55-129">4XX</span></span> | <span data-ttu-id="bea55-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bea55-130">Error codes</span></span>
<span data-ttu-id="bea55-131">5XX</span><span class="sxs-lookup"><span data-stu-id="bea55-131">5XX</span></span> | <span data-ttu-id="bea55-132">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bea55-132">Error codes</span></span>

## <a name="add-or-update-stored-credentials-for-a-user"></a><span data-ttu-id="bea55-133">Hinzufügen oder Aktualisieren von gespeicherten Anmeldeinformationen für einen Benutzer</span><span class="sxs-lookup"><span data-stu-id="bea55-133">Add or update stored credentials for a user</span></span>

**<span data-ttu-id="bea55-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bea55-134">Request</span></span>**

<span data-ttu-id="bea55-135">Methode</span><span class="sxs-lookup"><span data-stu-id="bea55-135">Method</span></span>      | <span data-ttu-id="bea55-136">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="bea55-136">Request URI</span></span>
:------     | :-----
<span data-ttu-id="bea55-137">POST</span><span class="sxs-lookup"><span data-stu-id="bea55-137">POST</span></span> | <span data-ttu-id="bea55-138">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="bea55-138">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="bea55-139">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="bea55-139">URI parameters</span></span>**

<span data-ttu-id="bea55-140">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="bea55-140">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="bea55-141">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="bea55-141">URI parameter</span></span>      | <span data-ttu-id="bea55-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bea55-142">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="bea55-143">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="bea55-143">NetworkPath</span></span>        | <span data-ttu-id="bea55-144">Der Netzwerkpfad zur Freigabe möchten Sie Anmeldeinformationen für den Zugriff auf Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bea55-144">The network path to the share you are adding credentials to access.</span></span> |
<br>

**<span data-ttu-id="bea55-145">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="bea55-145">Request headers</span></span>**

- <span data-ttu-id="bea55-146">Keine</span><span class="sxs-lookup"><span data-stu-id="bea55-146">None</span></span>

**<span data-ttu-id="bea55-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="bea55-147">Request body</span></span>**

- <span data-ttu-id="bea55-148">Die folgenden JSON-Elemente:</span><span class="sxs-lookup"><span data-stu-id="bea55-148">The following JSON elements:</span></span>
* <span data-ttu-id="bea55-149">NetworkPath - den Pfad der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="bea55-149">NetworkPath - The path to the network share.</span></span>
* <span data-ttu-id="bea55-150">Benutzername - der Benutzername zum Speichern von Anmeldeinformationen unter.</span><span class="sxs-lookup"><span data-stu-id="bea55-150">Username - The username to store the credentials under.</span></span>
* <span data-ttu-id="bea55-151">Kennwort: das neue oder aktualisierte Kennwort für diesen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="bea55-151">Password - The new or updated password for this user.</span></span>

**<span data-ttu-id="bea55-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="bea55-152">Response</span></span>**   

- <span data-ttu-id="bea55-153">Keine</span><span class="sxs-lookup"><span data-stu-id="bea55-153">None</span></span>  

**<span data-ttu-id="bea55-154">Statuscode</span><span class="sxs-lookup"><span data-stu-id="bea55-154">Status code</span></span>**

<span data-ttu-id="bea55-155">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="bea55-155">This API has the following expected status codes.</span></span>

<span data-ttu-id="bea55-156">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="bea55-156">HTTP status code</span></span>      | <span data-ttu-id="bea55-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bea55-157">Description</span></span>
:------     | :-----
<span data-ttu-id="bea55-158">204</span><span class="sxs-lookup"><span data-stu-id="bea55-158">204</span></span> | <span data-ttu-id="bea55-159">Erfolg</span><span class="sxs-lookup"><span data-stu-id="bea55-159">Success</span></span>
<span data-ttu-id="bea55-160">4XX</span><span class="sxs-lookup"><span data-stu-id="bea55-160">4XX</span></span> | <span data-ttu-id="bea55-161">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bea55-161">Error codes</span></span>
<span data-ttu-id="bea55-162">5XX</span><span class="sxs-lookup"><span data-stu-id="bea55-162">5XX</span></span> | <span data-ttu-id="bea55-163">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bea55-163">Error codes</span></span>

## <a name="remove-stored-credentials-for-a-share"></a><span data-ttu-id="bea55-164">Gespeicherte Anmeldeinformationen für eine Freigabe zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="bea55-164">Remove stored credentials for a share.</span></span>

**<span data-ttu-id="bea55-165">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bea55-165">Request</span></span>**

<span data-ttu-id="bea55-166">Methode</span><span class="sxs-lookup"><span data-stu-id="bea55-166">Method</span></span>      | <span data-ttu-id="bea55-167">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="bea55-167">Request URI</span></span>
:------     | :-----
<span data-ttu-id="bea55-168">DELETE</span><span class="sxs-lookup"><span data-stu-id="bea55-168">DELETE</span></span> | <span data-ttu-id="bea55-169">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="bea55-169">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="bea55-170">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="bea55-170">URI parameters</span></span>**

<span data-ttu-id="bea55-171">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="bea55-171">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="bea55-172">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="bea55-172">URI parameter</span></span>      | <span data-ttu-id="bea55-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bea55-173">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="bea55-174">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="bea55-174">NetworkPath</span></span>        | <span data-ttu-id="bea55-175">Der Netzwerkpfad zur Freigabe aus der Sie die gespeicherte Anmeldeinformationen entfernen.</span><span class="sxs-lookup"><span data-stu-id="bea55-175">The network path to the share from which you are removing stored credentials.</span></span> |
<br>

**<span data-ttu-id="bea55-176">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="bea55-176">Request headers</span></span>**

- <span data-ttu-id="bea55-177">Keine</span><span class="sxs-lookup"><span data-stu-id="bea55-177">None</span></span>

**<span data-ttu-id="bea55-178">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="bea55-178">Request body</span></span>**   

- <span data-ttu-id="bea55-179">Keine</span><span class="sxs-lookup"><span data-stu-id="bea55-179">None</span></span>

**<span data-ttu-id="bea55-180">Antwort</span><span class="sxs-lookup"><span data-stu-id="bea55-180">Response</span></span>**   

- <span data-ttu-id="bea55-181">Keine</span><span class="sxs-lookup"><span data-stu-id="bea55-181">None</span></span> 

**<span data-ttu-id="bea55-182">Statuscode</span><span class="sxs-lookup"><span data-stu-id="bea55-182">Status code</span></span>**

<span data-ttu-id="bea55-183">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="bea55-183">This API has the following expected status codes.</span></span>

<span data-ttu-id="bea55-184">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="bea55-184">HTTP status code</span></span>      | <span data-ttu-id="bea55-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bea55-185">Description</span></span>
:------     | :-----
<span data-ttu-id="bea55-186">204</span><span class="sxs-lookup"><span data-stu-id="bea55-186">204</span></span> | <span data-ttu-id="bea55-187">Die Anforderung an die Anmeldeinformationen war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="bea55-187">The request to the credentials was successful.</span></span>
<span data-ttu-id="bea55-188">4XX</span><span class="sxs-lookup"><span data-stu-id="bea55-188">4XX</span></span> | <span data-ttu-id="bea55-189">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bea55-189">Error codes</span></span>
<span data-ttu-id="bea55-190">5XX</span><span class="sxs-lookup"><span data-stu-id="bea55-190">5XX</span></span> | <span data-ttu-id="bea55-191">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bea55-191">Error codes</span></span>

<br />
**<span data-ttu-id="bea55-192">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="bea55-192">Available device families</span></span>**

* <span data-ttu-id="bea55-193">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="bea55-193">Windows Xbox</span></span>


