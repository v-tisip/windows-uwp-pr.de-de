---
title: Device Portal Netzwerk Anmeldeinformationen API-Referenz
description: Enthält Informationen zum Hinzufügen, entfernen oder Aktualisieren der Netzwerkanmeldeinformationen programmgesteuert.
ms.localizationpriority: medium
ms.openlocfilehash: 2da8dae554a0dcbb84d3d3fc3873e2fb035175dc
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7705102"
---
# <a name="network-credentials-api-reference"></a><span data-ttu-id="64e21-103">Netzwerk-Anmeldeinformationen-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="64e21-103">Network Credentials API reference</span></span>
<span data-ttu-id="64e21-104">Sie können hinzufügen, entfernen Sie oder aktualisieren Sie gespeicherten Netzwerkanmeldeinformationen auf Ihr dev Kit mittels dieser REST-API.</span><span class="sxs-lookup"><span data-stu-id="64e21-104">You can add, remove, or update stored network credentials on your devkit using this REST API.</span></span>

## <a name="get-existing-credentials"></a><span data-ttu-id="64e21-105">Abrufen von vorhandenen Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="64e21-105">Get existing credentials</span></span>

**<span data-ttu-id="64e21-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="64e21-106">Request</span></span>**

<span data-ttu-id="64e21-107">Sie können eine Liste der gespeicherten Freigaben zusammen mit den Benutzernamen des Benutzers abrufen, die Anmeldeinformationen für diese Netzwerkfreigabe verfügt.</span><span class="sxs-lookup"><span data-stu-id="64e21-107">You can get a list of the stored shares along with the username of the user who has credentials for that network share.</span></span>

<span data-ttu-id="64e21-108">Methode</span><span class="sxs-lookup"><span data-stu-id="64e21-108">Method</span></span>      | <span data-ttu-id="64e21-109">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="64e21-109">Request URI</span></span>
:------     | :-----
<span data-ttu-id="64e21-110">GET</span><span class="sxs-lookup"><span data-stu-id="64e21-110">GET</span></span> | <span data-ttu-id="64e21-111">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="64e21-111">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="64e21-112">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="64e21-112">URI parameters</span></span>**

- <span data-ttu-id="64e21-113">Keine</span><span class="sxs-lookup"><span data-stu-id="64e21-113">None</span></span>

**<span data-ttu-id="64e21-114">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="64e21-114">Request headers</span></span>**

- <span data-ttu-id="64e21-115">Keine</span><span class="sxs-lookup"><span data-stu-id="64e21-115">None</span></span>

**<span data-ttu-id="64e21-116">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="64e21-116">Request body</span></span>**   

- <span data-ttu-id="64e21-117">Keine</span><span class="sxs-lookup"><span data-stu-id="64e21-117">None</span></span>

**<span data-ttu-id="64e21-118">Antwort</span><span class="sxs-lookup"><span data-stu-id="64e21-118">Response</span></span>**   

- <span data-ttu-id="64e21-119">JSON-Array im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="64e21-119">JSON array in the following format:</span></span>
* <span data-ttu-id="64e21-120">Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="64e21-120">Credentials</span></span>
  * <span data-ttu-id="64e21-121">NetworkPath - den Pfad zu der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="64e21-121">NetworkPath - The path to the network share.</span></span>
  * <span data-ttu-id="64e21-122">UserName: der Benutzername die Anmeldeinformationen gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="64e21-122">Username - The username which has stored credentials.</span></span>

**<span data-ttu-id="64e21-123">Statuscode</span><span class="sxs-lookup"><span data-stu-id="64e21-123">Status code</span></span>**

<span data-ttu-id="64e21-124">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="64e21-124">This API has the following expected status codes.</span></span>

<span data-ttu-id="64e21-125">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="64e21-125">HTTP status code</span></span>      | <span data-ttu-id="64e21-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64e21-126">Description</span></span>
:------     | :-----
<span data-ttu-id="64e21-127">200</span><span class="sxs-lookup"><span data-stu-id="64e21-127">200</span></span> | <span data-ttu-id="64e21-128">Erfolg</span><span class="sxs-lookup"><span data-stu-id="64e21-128">Success</span></span>
<span data-ttu-id="64e21-129">4XX</span><span class="sxs-lookup"><span data-stu-id="64e21-129">4XX</span></span> | <span data-ttu-id="64e21-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="64e21-130">Error codes</span></span>
<span data-ttu-id="64e21-131">5XX</span><span class="sxs-lookup"><span data-stu-id="64e21-131">5XX</span></span> | <span data-ttu-id="64e21-132">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="64e21-132">Error codes</span></span>

## <a name="add-or-update-stored-credentials-for-a-user"></a><span data-ttu-id="64e21-133">Hinzufügen oder Aktualisieren von gespeicherten Anmeldeinformationen für einen Benutzer</span><span class="sxs-lookup"><span data-stu-id="64e21-133">Add or update stored credentials for a user</span></span>

**<span data-ttu-id="64e21-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="64e21-134">Request</span></span>**

<span data-ttu-id="64e21-135">Methode</span><span class="sxs-lookup"><span data-stu-id="64e21-135">Method</span></span>      | <span data-ttu-id="64e21-136">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="64e21-136">Request URI</span></span>
:------     | :-----
<span data-ttu-id="64e21-137">POST</span><span class="sxs-lookup"><span data-stu-id="64e21-137">POST</span></span> | <span data-ttu-id="64e21-138">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="64e21-138">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="64e21-139">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="64e21-139">URI parameters</span></span>**

<span data-ttu-id="64e21-140">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="64e21-140">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="64e21-141">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="64e21-141">URI parameter</span></span>      | <span data-ttu-id="64e21-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64e21-142">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="64e21-143">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="64e21-143">NetworkPath</span></span>        | <span data-ttu-id="64e21-144">Die Netzwerkpfad für die Freigabe sind Sie Anmeldeinformationen für den Zugriff auf Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="64e21-144">The network path to the share you are adding credentials to access.</span></span> |
<br>

**<span data-ttu-id="64e21-145">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="64e21-145">Request headers</span></span>**

- <span data-ttu-id="64e21-146">Keine</span><span class="sxs-lookup"><span data-stu-id="64e21-146">None</span></span>

**<span data-ttu-id="64e21-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="64e21-147">Request body</span></span>**

- <span data-ttu-id="64e21-148">Die folgenden JSON-Elemente:</span><span class="sxs-lookup"><span data-stu-id="64e21-148">The following JSON elements:</span></span>
* <span data-ttu-id="64e21-149">NetworkPath - den Pfad zu der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="64e21-149">NetworkPath - The path to the network share.</span></span>
* <span data-ttu-id="64e21-150">UserName: der Benutzername, um die Anmeldeinformationen, zu speichern.</span><span class="sxs-lookup"><span data-stu-id="64e21-150">Username - The username to store the credentials under.</span></span>
* <span data-ttu-id="64e21-151">Kennwort - neue oder aktualisierte für diesen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="64e21-151">Password - The new or updated password for this user.</span></span>

**<span data-ttu-id="64e21-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="64e21-152">Response</span></span>**   

- <span data-ttu-id="64e21-153">Keine</span><span class="sxs-lookup"><span data-stu-id="64e21-153">None</span></span>  

**<span data-ttu-id="64e21-154">Statuscode</span><span class="sxs-lookup"><span data-stu-id="64e21-154">Status code</span></span>**

<span data-ttu-id="64e21-155">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="64e21-155">This API has the following expected status codes.</span></span>

<span data-ttu-id="64e21-156">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="64e21-156">HTTP status code</span></span>      | <span data-ttu-id="64e21-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64e21-157">Description</span></span>
:------     | :-----
<span data-ttu-id="64e21-158">204</span><span class="sxs-lookup"><span data-stu-id="64e21-158">204</span></span> | <span data-ttu-id="64e21-159">Erfolg</span><span class="sxs-lookup"><span data-stu-id="64e21-159">Success</span></span>
<span data-ttu-id="64e21-160">4XX</span><span class="sxs-lookup"><span data-stu-id="64e21-160">4XX</span></span> | <span data-ttu-id="64e21-161">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="64e21-161">Error codes</span></span>
<span data-ttu-id="64e21-162">5XX</span><span class="sxs-lookup"><span data-stu-id="64e21-162">5XX</span></span> | <span data-ttu-id="64e21-163">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="64e21-163">Error codes</span></span>

## <a name="remove-stored-credentials-for-a-share"></a><span data-ttu-id="64e21-164">Gespeicherte Anmeldeinformationen für eine Bereitstellungsfreigabe zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="64e21-164">Remove stored credentials for a share.</span></span>

**<span data-ttu-id="64e21-165">Anforderung</span><span class="sxs-lookup"><span data-stu-id="64e21-165">Request</span></span>**

<span data-ttu-id="64e21-166">Methode</span><span class="sxs-lookup"><span data-stu-id="64e21-166">Method</span></span>      | <span data-ttu-id="64e21-167">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="64e21-167">Request URI</span></span>
:------     | :-----
<span data-ttu-id="64e21-168">DELETE</span><span class="sxs-lookup"><span data-stu-id="64e21-168">DELETE</span></span> | <span data-ttu-id="64e21-169">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="64e21-169">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="64e21-170">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="64e21-170">URI parameters</span></span>**

<span data-ttu-id="64e21-171">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="64e21-171">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="64e21-172">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="64e21-172">URI parameter</span></span>      | <span data-ttu-id="64e21-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64e21-173">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="64e21-174">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="64e21-174">NetworkPath</span></span>        | <span data-ttu-id="64e21-175">Der Netzwerkpfad für die Freigabe aus der Sie die gespeicherte Anmeldeinformationen entfernen.</span><span class="sxs-lookup"><span data-stu-id="64e21-175">The network path to the share from which you are removing stored credentials.</span></span> |
<br>

**<span data-ttu-id="64e21-176">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="64e21-176">Request headers</span></span>**

- <span data-ttu-id="64e21-177">Keine</span><span class="sxs-lookup"><span data-stu-id="64e21-177">None</span></span>

**<span data-ttu-id="64e21-178">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="64e21-178">Request body</span></span>**   

- <span data-ttu-id="64e21-179">Keine</span><span class="sxs-lookup"><span data-stu-id="64e21-179">None</span></span>

**<span data-ttu-id="64e21-180">Antwort</span><span class="sxs-lookup"><span data-stu-id="64e21-180">Response</span></span>**   

- <span data-ttu-id="64e21-181">Keine</span><span class="sxs-lookup"><span data-stu-id="64e21-181">None</span></span> 

**<span data-ttu-id="64e21-182">Statuscode</span><span class="sxs-lookup"><span data-stu-id="64e21-182">Status code</span></span>**

<span data-ttu-id="64e21-183">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="64e21-183">This API has the following expected status codes.</span></span>

<span data-ttu-id="64e21-184">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="64e21-184">HTTP status code</span></span>      | <span data-ttu-id="64e21-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64e21-185">Description</span></span>
:------     | :-----
<span data-ttu-id="64e21-186">204</span><span class="sxs-lookup"><span data-stu-id="64e21-186">204</span></span> | <span data-ttu-id="64e21-187">Die Anforderung von Anmeldeinformationen war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="64e21-187">The request to the credentials was successful.</span></span>
<span data-ttu-id="64e21-188">4XX</span><span class="sxs-lookup"><span data-stu-id="64e21-188">4XX</span></span> | <span data-ttu-id="64e21-189">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="64e21-189">Error codes</span></span>
<span data-ttu-id="64e21-190">5XX</span><span class="sxs-lookup"><span data-stu-id="64e21-190">5XX</span></span> | <span data-ttu-id="64e21-191">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="64e21-191">Error codes</span></span>

<br />
**<span data-ttu-id="64e21-192">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="64e21-192">Available device families</span></span>**

* <span data-ttu-id="64e21-193">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="64e21-193">Windows Xbox</span></span>


