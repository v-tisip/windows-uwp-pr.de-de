---
title: Device Portal Netzwerk Anmeldeinformationen API-Referenz
description: Enthält Informationen zum Hinzufügen, entfernen oder Aktualisieren der Netzwerkanmeldeinformationen programmgesteuert.
ms.localizationpriority: medium
ms.openlocfilehash: 2da8dae554a0dcbb84d3d3fc3873e2fb035175dc
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8730971"
---
# <a name="network-credentials-api-reference"></a><span data-ttu-id="25d60-103">Netzwerk-Anmeldeinformationen-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="25d60-103">Network Credentials API reference</span></span>
<span data-ttu-id="25d60-104">Sie können hinzufügen, entfernen Sie oder aktualisieren Sie gespeicherte Netzwerkanmeldeinformationen auf Ihr dev Kit mittels dieser REST-API.</span><span class="sxs-lookup"><span data-stu-id="25d60-104">You can add, remove, or update stored network credentials on your devkit using this REST API.</span></span>

## <a name="get-existing-credentials"></a><span data-ttu-id="25d60-105">Abrufen von vorhandenen Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="25d60-105">Get existing credentials</span></span>

**<span data-ttu-id="25d60-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="25d60-106">Request</span></span>**

<span data-ttu-id="25d60-107">Sie können eine Liste der gespeicherten Freigaben zusammen mit den Benutzernamen des Benutzers abrufen, die Anmeldeinformationen für diesen Netzwerkfreigabe verfügt.</span><span class="sxs-lookup"><span data-stu-id="25d60-107">You can get a list of the stored shares along with the username of the user who has credentials for that network share.</span></span>

<span data-ttu-id="25d60-108">Methode</span><span class="sxs-lookup"><span data-stu-id="25d60-108">Method</span></span>      | <span data-ttu-id="25d60-109">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="25d60-109">Request URI</span></span>
:------     | :-----
<span data-ttu-id="25d60-110">GET</span><span class="sxs-lookup"><span data-stu-id="25d60-110">GET</span></span> | <span data-ttu-id="25d60-111">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="25d60-111">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="25d60-112">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="25d60-112">URI parameters</span></span>**

- <span data-ttu-id="25d60-113">Keine</span><span class="sxs-lookup"><span data-stu-id="25d60-113">None</span></span>

**<span data-ttu-id="25d60-114">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="25d60-114">Request headers</span></span>**

- <span data-ttu-id="25d60-115">Keine</span><span class="sxs-lookup"><span data-stu-id="25d60-115">None</span></span>

**<span data-ttu-id="25d60-116">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="25d60-116">Request body</span></span>**   

- <span data-ttu-id="25d60-117">Keine</span><span class="sxs-lookup"><span data-stu-id="25d60-117">None</span></span>

**<span data-ttu-id="25d60-118">Antwort</span><span class="sxs-lookup"><span data-stu-id="25d60-118">Response</span></span>**   

- <span data-ttu-id="25d60-119">JSON-Array im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="25d60-119">JSON array in the following format:</span></span>
* <span data-ttu-id="25d60-120">Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="25d60-120">Credentials</span></span>
  * <span data-ttu-id="25d60-121">NetworkPath - den Pfad zu der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="25d60-121">NetworkPath - The path to the network share.</span></span>
  * <span data-ttu-id="25d60-122">UserName: der Benutzername die Anmeldeinformationen gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="25d60-122">Username - The username which has stored credentials.</span></span>

**<span data-ttu-id="25d60-123">Statuscode</span><span class="sxs-lookup"><span data-stu-id="25d60-123">Status code</span></span>**

<span data-ttu-id="25d60-124">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="25d60-124">This API has the following expected status codes.</span></span>

<span data-ttu-id="25d60-125">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="25d60-125">HTTP status code</span></span>      | <span data-ttu-id="25d60-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="25d60-126">Description</span></span>
:------     | :-----
<span data-ttu-id="25d60-127">200</span><span class="sxs-lookup"><span data-stu-id="25d60-127">200</span></span> | <span data-ttu-id="25d60-128">Erfolg</span><span class="sxs-lookup"><span data-stu-id="25d60-128">Success</span></span>
<span data-ttu-id="25d60-129">4XX</span><span class="sxs-lookup"><span data-stu-id="25d60-129">4XX</span></span> | <span data-ttu-id="25d60-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="25d60-130">Error codes</span></span>
<span data-ttu-id="25d60-131">5XX</span><span class="sxs-lookup"><span data-stu-id="25d60-131">5XX</span></span> | <span data-ttu-id="25d60-132">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="25d60-132">Error codes</span></span>

## <a name="add-or-update-stored-credentials-for-a-user"></a><span data-ttu-id="25d60-133">Hinzufügen oder Aktualisieren von gespeicherten Anmeldeinformationen für einen Benutzer</span><span class="sxs-lookup"><span data-stu-id="25d60-133">Add or update stored credentials for a user</span></span>

**<span data-ttu-id="25d60-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="25d60-134">Request</span></span>**

<span data-ttu-id="25d60-135">Methode</span><span class="sxs-lookup"><span data-stu-id="25d60-135">Method</span></span>      | <span data-ttu-id="25d60-136">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="25d60-136">Request URI</span></span>
:------     | :-----
<span data-ttu-id="25d60-137">POST</span><span class="sxs-lookup"><span data-stu-id="25d60-137">POST</span></span> | <span data-ttu-id="25d60-138">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="25d60-138">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="25d60-139">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="25d60-139">URI parameters</span></span>**

<span data-ttu-id="25d60-140">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="25d60-140">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="25d60-141">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="25d60-141">URI parameter</span></span>      | <span data-ttu-id="25d60-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="25d60-142">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="25d60-143">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="25d60-143">NetworkPath</span></span>        | <span data-ttu-id="25d60-144">Die Netzwerkpfad für die Freigabe sind Sie Anmeldeinformationen für den Zugriff auf Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="25d60-144">The network path to the share you are adding credentials to access.</span></span> |
<br>

**<span data-ttu-id="25d60-145">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="25d60-145">Request headers</span></span>**

- <span data-ttu-id="25d60-146">Keine</span><span class="sxs-lookup"><span data-stu-id="25d60-146">None</span></span>

**<span data-ttu-id="25d60-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="25d60-147">Request body</span></span>**

- <span data-ttu-id="25d60-148">Die folgenden JSON-Elemente:</span><span class="sxs-lookup"><span data-stu-id="25d60-148">The following JSON elements:</span></span>
* <span data-ttu-id="25d60-149">NetworkPath - den Pfad zu der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="25d60-149">NetworkPath - The path to the network share.</span></span>
* <span data-ttu-id="25d60-150">UserName: der Benutzername, um die Anmeldeinformationen zu speichern.</span><span class="sxs-lookup"><span data-stu-id="25d60-150">Username - The username to store the credentials under.</span></span>
* <span data-ttu-id="25d60-151">Password: das neue oder aktualisierte Kennwort für diesen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="25d60-151">Password - The new or updated password for this user.</span></span>

**<span data-ttu-id="25d60-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="25d60-152">Response</span></span>**   

- <span data-ttu-id="25d60-153">Keine</span><span class="sxs-lookup"><span data-stu-id="25d60-153">None</span></span>  

**<span data-ttu-id="25d60-154">Statuscode</span><span class="sxs-lookup"><span data-stu-id="25d60-154">Status code</span></span>**

<span data-ttu-id="25d60-155">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="25d60-155">This API has the following expected status codes.</span></span>

<span data-ttu-id="25d60-156">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="25d60-156">HTTP status code</span></span>      | <span data-ttu-id="25d60-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="25d60-157">Description</span></span>
:------     | :-----
<span data-ttu-id="25d60-158">204</span><span class="sxs-lookup"><span data-stu-id="25d60-158">204</span></span> | <span data-ttu-id="25d60-159">Erfolg</span><span class="sxs-lookup"><span data-stu-id="25d60-159">Success</span></span>
<span data-ttu-id="25d60-160">4XX</span><span class="sxs-lookup"><span data-stu-id="25d60-160">4XX</span></span> | <span data-ttu-id="25d60-161">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="25d60-161">Error codes</span></span>
<span data-ttu-id="25d60-162">5XX</span><span class="sxs-lookup"><span data-stu-id="25d60-162">5XX</span></span> | <span data-ttu-id="25d60-163">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="25d60-163">Error codes</span></span>

## <a name="remove-stored-credentials-for-a-share"></a><span data-ttu-id="25d60-164">Gespeicherte Anmeldeinformationen für eine Bereitstellungsfreigabe zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="25d60-164">Remove stored credentials for a share.</span></span>

**<span data-ttu-id="25d60-165">Anforderung</span><span class="sxs-lookup"><span data-stu-id="25d60-165">Request</span></span>**

<span data-ttu-id="25d60-166">Methode</span><span class="sxs-lookup"><span data-stu-id="25d60-166">Method</span></span>      | <span data-ttu-id="25d60-167">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="25d60-167">Request URI</span></span>
:------     | :-----
<span data-ttu-id="25d60-168">DELETE</span><span class="sxs-lookup"><span data-stu-id="25d60-168">DELETE</span></span> | <span data-ttu-id="25d60-169">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="25d60-169">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="25d60-170">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="25d60-170">URI parameters</span></span>**

<span data-ttu-id="25d60-171">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="25d60-171">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="25d60-172">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="25d60-172">URI parameter</span></span>      | <span data-ttu-id="25d60-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="25d60-173">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="25d60-174">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="25d60-174">NetworkPath</span></span>        | <span data-ttu-id="25d60-175">Der Netzwerkpfad für die Freigabe aus der Sie die gespeicherte Anmeldeinformationen entfernen.</span><span class="sxs-lookup"><span data-stu-id="25d60-175">The network path to the share from which you are removing stored credentials.</span></span> |
<br>

**<span data-ttu-id="25d60-176">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="25d60-176">Request headers</span></span>**

- <span data-ttu-id="25d60-177">Keine</span><span class="sxs-lookup"><span data-stu-id="25d60-177">None</span></span>

**<span data-ttu-id="25d60-178">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="25d60-178">Request body</span></span>**   

- <span data-ttu-id="25d60-179">Keine</span><span class="sxs-lookup"><span data-stu-id="25d60-179">None</span></span>

**<span data-ttu-id="25d60-180">Antwort</span><span class="sxs-lookup"><span data-stu-id="25d60-180">Response</span></span>**   

- <span data-ttu-id="25d60-181">Keine</span><span class="sxs-lookup"><span data-stu-id="25d60-181">None</span></span> 

**<span data-ttu-id="25d60-182">Statuscode</span><span class="sxs-lookup"><span data-stu-id="25d60-182">Status code</span></span>**

<span data-ttu-id="25d60-183">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="25d60-183">This API has the following expected status codes.</span></span>

<span data-ttu-id="25d60-184">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="25d60-184">HTTP status code</span></span>      | <span data-ttu-id="25d60-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="25d60-185">Description</span></span>
:------     | :-----
<span data-ttu-id="25d60-186">204</span><span class="sxs-lookup"><span data-stu-id="25d60-186">204</span></span> | <span data-ttu-id="25d60-187">Die Anforderung für die Anmeldeinformationen war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="25d60-187">The request to the credentials was successful.</span></span>
<span data-ttu-id="25d60-188">4XX</span><span class="sxs-lookup"><span data-stu-id="25d60-188">4XX</span></span> | <span data-ttu-id="25d60-189">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="25d60-189">Error codes</span></span>
<span data-ttu-id="25d60-190">5XX</span><span class="sxs-lookup"><span data-stu-id="25d60-190">5XX</span></span> | <span data-ttu-id="25d60-191">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="25d60-191">Error codes</span></span>

<br />
**<span data-ttu-id="25d60-192">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="25d60-192">Available device families</span></span>**

* <span data-ttu-id="25d60-193">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="25d60-193">Windows Xbox</span></span>


