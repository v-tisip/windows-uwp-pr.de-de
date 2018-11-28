---
title: Device Portal Netzwerk Anmeldeinformationen API-Referenz
description: Enthält Informationen zum Hinzufügen, entfernen oder Aktualisieren der Netzwerkanmeldeinformationen programmgesteuert.
ms.localizationpriority: medium
ms.openlocfilehash: 2da8dae554a0dcbb84d3d3fc3873e2fb035175dc
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7836235"
---
# <a name="network-credentials-api-reference"></a><span data-ttu-id="2a0d8-103">Netzwerk-Anmeldeinformationen-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="2a0d8-103">Network Credentials API reference</span></span>
<span data-ttu-id="2a0d8-104">Sie können hinzufügen, entfernen Sie oder aktualisieren Sie gespeicherte Netzwerkanmeldeinformationen auf Ihr dev Kit mittels dieser REST-API.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-104">You can add, remove, or update stored network credentials on your devkit using this REST API.</span></span>

## <a name="get-existing-credentials"></a><span data-ttu-id="2a0d8-105">Abrufen von vorhandenen Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="2a0d8-105">Get existing credentials</span></span>

**<span data-ttu-id="2a0d8-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="2a0d8-106">Request</span></span>**

<span data-ttu-id="2a0d8-107">Sie können eine Liste der gespeicherten Freigaben zusammen mit den Benutzernamen des Benutzers abrufen, die Anmeldeinformationen für diesen Netzwerkfreigabe verfügt.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-107">You can get a list of the stored shares along with the username of the user who has credentials for that network share.</span></span>

<span data-ttu-id="2a0d8-108">Methode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-108">Method</span></span>      | <span data-ttu-id="2a0d8-109">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="2a0d8-109">Request URI</span></span>
:------     | :-----
<span data-ttu-id="2a0d8-110">GET</span><span class="sxs-lookup"><span data-stu-id="2a0d8-110">GET</span></span> | <span data-ttu-id="2a0d8-111">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="2a0d8-111">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="2a0d8-112">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="2a0d8-112">URI parameters</span></span>**

- <span data-ttu-id="2a0d8-113">Keine</span><span class="sxs-lookup"><span data-stu-id="2a0d8-113">None</span></span>

**<span data-ttu-id="2a0d8-114">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="2a0d8-114">Request headers</span></span>**

- <span data-ttu-id="2a0d8-115">Keine</span><span class="sxs-lookup"><span data-stu-id="2a0d8-115">None</span></span>

**<span data-ttu-id="2a0d8-116">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="2a0d8-116">Request body</span></span>**   

- <span data-ttu-id="2a0d8-117">Keine</span><span class="sxs-lookup"><span data-stu-id="2a0d8-117">None</span></span>

**<span data-ttu-id="2a0d8-118">Antwort</span><span class="sxs-lookup"><span data-stu-id="2a0d8-118">Response</span></span>**   

- <span data-ttu-id="2a0d8-119">JSON-Array im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="2a0d8-119">JSON array in the following format:</span></span>
* <span data-ttu-id="2a0d8-120">Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="2a0d8-120">Credentials</span></span>
  * <span data-ttu-id="2a0d8-121">NetworkPath - den Pfad zu der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-121">NetworkPath - The path to the network share.</span></span>
  * <span data-ttu-id="2a0d8-122">UserName: der Benutzername die Anmeldeinformationen gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-122">Username - The username which has stored credentials.</span></span>

**<span data-ttu-id="2a0d8-123">Statuscode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-123">Status code</span></span>**

<span data-ttu-id="2a0d8-124">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="2a0d8-124">This API has the following expected status codes.</span></span>

<span data-ttu-id="2a0d8-125">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-125">HTTP status code</span></span>      | <span data-ttu-id="2a0d8-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2a0d8-126">Description</span></span>
:------     | :-----
<span data-ttu-id="2a0d8-127">200</span><span class="sxs-lookup"><span data-stu-id="2a0d8-127">200</span></span> | <span data-ttu-id="2a0d8-128">Erfolg</span><span class="sxs-lookup"><span data-stu-id="2a0d8-128">Success</span></span>
<span data-ttu-id="2a0d8-129">4XX</span><span class="sxs-lookup"><span data-stu-id="2a0d8-129">4XX</span></span> | <span data-ttu-id="2a0d8-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="2a0d8-130">Error codes</span></span>
<span data-ttu-id="2a0d8-131">5XX</span><span class="sxs-lookup"><span data-stu-id="2a0d8-131">5XX</span></span> | <span data-ttu-id="2a0d8-132">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="2a0d8-132">Error codes</span></span>

## <a name="add-or-update-stored-credentials-for-a-user"></a><span data-ttu-id="2a0d8-133">Hinzufügen oder Aktualisieren von gespeicherten Anmeldeinformationen für einen Benutzer</span><span class="sxs-lookup"><span data-stu-id="2a0d8-133">Add or update stored credentials for a user</span></span>

**<span data-ttu-id="2a0d8-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="2a0d8-134">Request</span></span>**

<span data-ttu-id="2a0d8-135">Methode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-135">Method</span></span>      | <span data-ttu-id="2a0d8-136">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="2a0d8-136">Request URI</span></span>
:------     | :-----
<span data-ttu-id="2a0d8-137">POST</span><span class="sxs-lookup"><span data-stu-id="2a0d8-137">POST</span></span> | <span data-ttu-id="2a0d8-138">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="2a0d8-138">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="2a0d8-139">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="2a0d8-139">URI parameters</span></span>**

<span data-ttu-id="2a0d8-140">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="2a0d8-140">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="2a0d8-141">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="2a0d8-141">URI parameter</span></span>      | <span data-ttu-id="2a0d8-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2a0d8-142">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="2a0d8-143">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="2a0d8-143">NetworkPath</span></span>        | <span data-ttu-id="2a0d8-144">Die Netzwerkpfad für die Freigabe sind Sie Anmeldeinformationen für den Zugriff auf Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-144">The network path to the share you are adding credentials to access.</span></span> |
<br>

**<span data-ttu-id="2a0d8-145">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="2a0d8-145">Request headers</span></span>**

- <span data-ttu-id="2a0d8-146">Keine</span><span class="sxs-lookup"><span data-stu-id="2a0d8-146">None</span></span>

**<span data-ttu-id="2a0d8-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="2a0d8-147">Request body</span></span>**

- <span data-ttu-id="2a0d8-148">Die folgenden JSON-Elemente:</span><span class="sxs-lookup"><span data-stu-id="2a0d8-148">The following JSON elements:</span></span>
* <span data-ttu-id="2a0d8-149">NetworkPath - den Pfad zu der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-149">NetworkPath - The path to the network share.</span></span>
* <span data-ttu-id="2a0d8-150">UserName: der Benutzername, um die Anmeldeinformationen zu speichern.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-150">Username - The username to store the credentials under.</span></span>
* <span data-ttu-id="2a0d8-151">Password: das neue oder aktualisierte Kennwort für diesen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-151">Password - The new or updated password for this user.</span></span>

**<span data-ttu-id="2a0d8-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="2a0d8-152">Response</span></span>**   

- <span data-ttu-id="2a0d8-153">Keine</span><span class="sxs-lookup"><span data-stu-id="2a0d8-153">None</span></span>  

**<span data-ttu-id="2a0d8-154">Statuscode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-154">Status code</span></span>**

<span data-ttu-id="2a0d8-155">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="2a0d8-155">This API has the following expected status codes.</span></span>

<span data-ttu-id="2a0d8-156">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-156">HTTP status code</span></span>      | <span data-ttu-id="2a0d8-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2a0d8-157">Description</span></span>
:------     | :-----
<span data-ttu-id="2a0d8-158">204</span><span class="sxs-lookup"><span data-stu-id="2a0d8-158">204</span></span> | <span data-ttu-id="2a0d8-159">Erfolg</span><span class="sxs-lookup"><span data-stu-id="2a0d8-159">Success</span></span>
<span data-ttu-id="2a0d8-160">4XX</span><span class="sxs-lookup"><span data-stu-id="2a0d8-160">4XX</span></span> | <span data-ttu-id="2a0d8-161">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="2a0d8-161">Error codes</span></span>
<span data-ttu-id="2a0d8-162">5XX</span><span class="sxs-lookup"><span data-stu-id="2a0d8-162">5XX</span></span> | <span data-ttu-id="2a0d8-163">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="2a0d8-163">Error codes</span></span>

## <a name="remove-stored-credentials-for-a-share"></a><span data-ttu-id="2a0d8-164">Gespeicherte Anmeldeinformationen für eine Bereitstellungsfreigabe zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-164">Remove stored credentials for a share.</span></span>

**<span data-ttu-id="2a0d8-165">Anforderung</span><span class="sxs-lookup"><span data-stu-id="2a0d8-165">Request</span></span>**

<span data-ttu-id="2a0d8-166">Methode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-166">Method</span></span>      | <span data-ttu-id="2a0d8-167">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="2a0d8-167">Request URI</span></span>
:------     | :-----
<span data-ttu-id="2a0d8-168">DELETE</span><span class="sxs-lookup"><span data-stu-id="2a0d8-168">DELETE</span></span> | <span data-ttu-id="2a0d8-169">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="2a0d8-169">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="2a0d8-170">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="2a0d8-170">URI parameters</span></span>**

<span data-ttu-id="2a0d8-171">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="2a0d8-171">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="2a0d8-172">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="2a0d8-172">URI parameter</span></span>      | <span data-ttu-id="2a0d8-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2a0d8-173">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="2a0d8-174">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="2a0d8-174">NetworkPath</span></span>        | <span data-ttu-id="2a0d8-175">Der Netzwerkpfad für die Freigabe aus der Sie die gespeicherte Anmeldeinformationen entfernen.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-175">The network path to the share from which you are removing stored credentials.</span></span> |
<br>

**<span data-ttu-id="2a0d8-176">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="2a0d8-176">Request headers</span></span>**

- <span data-ttu-id="2a0d8-177">Keine</span><span class="sxs-lookup"><span data-stu-id="2a0d8-177">None</span></span>

**<span data-ttu-id="2a0d8-178">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="2a0d8-178">Request body</span></span>**   

- <span data-ttu-id="2a0d8-179">Keine</span><span class="sxs-lookup"><span data-stu-id="2a0d8-179">None</span></span>

**<span data-ttu-id="2a0d8-180">Antwort</span><span class="sxs-lookup"><span data-stu-id="2a0d8-180">Response</span></span>**   

- <span data-ttu-id="2a0d8-181">Keine</span><span class="sxs-lookup"><span data-stu-id="2a0d8-181">None</span></span> 

**<span data-ttu-id="2a0d8-182">Statuscode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-182">Status code</span></span>**

<span data-ttu-id="2a0d8-183">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="2a0d8-183">This API has the following expected status codes.</span></span>

<span data-ttu-id="2a0d8-184">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="2a0d8-184">HTTP status code</span></span>      | <span data-ttu-id="2a0d8-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2a0d8-185">Description</span></span>
:------     | :-----
<span data-ttu-id="2a0d8-186">204</span><span class="sxs-lookup"><span data-stu-id="2a0d8-186">204</span></span> | <span data-ttu-id="2a0d8-187">Die Anforderung für die Anmeldeinformationen war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="2a0d8-187">The request to the credentials was successful.</span></span>
<span data-ttu-id="2a0d8-188">4XX</span><span class="sxs-lookup"><span data-stu-id="2a0d8-188">4XX</span></span> | <span data-ttu-id="2a0d8-189">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="2a0d8-189">Error codes</span></span>
<span data-ttu-id="2a0d8-190">5XX</span><span class="sxs-lookup"><span data-stu-id="2a0d8-190">5XX</span></span> | <span data-ttu-id="2a0d8-191">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="2a0d8-191">Error codes</span></span>

<br />
**<span data-ttu-id="2a0d8-192">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="2a0d8-192">Available device families</span></span>**

* <span data-ttu-id="2a0d8-193">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="2a0d8-193">Windows Xbox</span></span>


