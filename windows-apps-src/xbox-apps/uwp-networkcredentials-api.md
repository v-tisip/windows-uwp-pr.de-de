---
title: Device Portal Netzwerk Anmeldeinformationen API-Referenz
description: Enthält Informationen zum Hinzufügen, entfernen oder Aktualisieren der Netzwerkanmeldeinformationen programmgesteuert.
ms.localizationpriority: medium
ms.topic: article
ms.date: 02/08/2017
ms.openlocfilehash: ac30d8db830c51ee40653feb49b443ed44502617
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8883049"
---
# <a name="network-credentials-api-reference"></a><span data-ttu-id="b43c3-103">Netzwerk-Anmeldeinformationen-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="b43c3-103">Network Credentials API reference</span></span>
<span data-ttu-id="b43c3-104">Sie können hinzufügen, entfernen Sie oder aktualisieren Sie gespeicherten Netzwerkanmeldeinformationen auf Ihr dev Kit mittels dieser REST-API.</span><span class="sxs-lookup"><span data-stu-id="b43c3-104">You can add, remove, or update stored network credentials on your devkit using this REST API.</span></span>

## <a name="get-existing-credentials"></a><span data-ttu-id="b43c3-105">Abrufen von vorhandenen Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="b43c3-105">Get existing credentials</span></span>

**<span data-ttu-id="b43c3-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="b43c3-106">Request</span></span>**

<span data-ttu-id="b43c3-107">Sie können eine Liste der gespeicherten Freigaben zusammen mit den Benutzernamen des Benutzers abrufen, die Anmeldeinformationen für diese Netzwerkfreigabe verfügt.</span><span class="sxs-lookup"><span data-stu-id="b43c3-107">You can get a list of the stored shares along with the username of the user who has credentials for that network share.</span></span>

<span data-ttu-id="b43c3-108">Methode</span><span class="sxs-lookup"><span data-stu-id="b43c3-108">Method</span></span>      | <span data-ttu-id="b43c3-109">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="b43c3-109">Request URI</span></span>
:------     | :-----
<span data-ttu-id="b43c3-110">GET</span><span class="sxs-lookup"><span data-stu-id="b43c3-110">GET</span></span> | <span data-ttu-id="b43c3-111">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="b43c3-111">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="b43c3-112">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="b43c3-112">URI parameters</span></span>**

- <span data-ttu-id="b43c3-113">Keine</span><span class="sxs-lookup"><span data-stu-id="b43c3-113">None</span></span>

**<span data-ttu-id="b43c3-114">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="b43c3-114">Request headers</span></span>**

- <span data-ttu-id="b43c3-115">Keine</span><span class="sxs-lookup"><span data-stu-id="b43c3-115">None</span></span>

**<span data-ttu-id="b43c3-116">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="b43c3-116">Request body</span></span>**   

- <span data-ttu-id="b43c3-117">Keine</span><span class="sxs-lookup"><span data-stu-id="b43c3-117">None</span></span>

**<span data-ttu-id="b43c3-118">Antwort</span><span class="sxs-lookup"><span data-stu-id="b43c3-118">Response</span></span>**   

- <span data-ttu-id="b43c3-119">JSON-Array im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="b43c3-119">JSON array in the following format:</span></span>
* <span data-ttu-id="b43c3-120">Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="b43c3-120">Credentials</span></span>
  * <span data-ttu-id="b43c3-121">NetworkPath - den Pfad zu der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="b43c3-121">NetworkPath - The path to the network share.</span></span>
  * <span data-ttu-id="b43c3-122">UserName: der Benutzername die Anmeldeinformationen gespeichert hat.</span><span class="sxs-lookup"><span data-stu-id="b43c3-122">Username - The username which has stored credentials.</span></span>

**<span data-ttu-id="b43c3-123">Statuscode</span><span class="sxs-lookup"><span data-stu-id="b43c3-123">Status code</span></span>**

<span data-ttu-id="b43c3-124">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="b43c3-124">This API has the following expected status codes.</span></span>

<span data-ttu-id="b43c3-125">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="b43c3-125">HTTP status code</span></span>      | <span data-ttu-id="b43c3-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b43c3-126">Description</span></span>
:------     | :-----
<span data-ttu-id="b43c3-127">200</span><span class="sxs-lookup"><span data-stu-id="b43c3-127">200</span></span> | <span data-ttu-id="b43c3-128">Erfolg</span><span class="sxs-lookup"><span data-stu-id="b43c3-128">Success</span></span>
<span data-ttu-id="b43c3-129">4XX</span><span class="sxs-lookup"><span data-stu-id="b43c3-129">4XX</span></span> | <span data-ttu-id="b43c3-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="b43c3-130">Error codes</span></span>
<span data-ttu-id="b43c3-131">5XX</span><span class="sxs-lookup"><span data-stu-id="b43c3-131">5XX</span></span> | <span data-ttu-id="b43c3-132">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="b43c3-132">Error codes</span></span>

## <a name="add-or-update-stored-credentials-for-a-user"></a><span data-ttu-id="b43c3-133">Hinzufügen oder Aktualisieren von gespeicherten Anmeldeinformationen für einen Benutzer</span><span class="sxs-lookup"><span data-stu-id="b43c3-133">Add or update stored credentials for a user</span></span>

**<span data-ttu-id="b43c3-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="b43c3-134">Request</span></span>**

<span data-ttu-id="b43c3-135">Methode</span><span class="sxs-lookup"><span data-stu-id="b43c3-135">Method</span></span>      | <span data-ttu-id="b43c3-136">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="b43c3-136">Request URI</span></span>
:------     | :-----
<span data-ttu-id="b43c3-137">POST</span><span class="sxs-lookup"><span data-stu-id="b43c3-137">POST</span></span> | <span data-ttu-id="b43c3-138">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="b43c3-138">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="b43c3-139">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="b43c3-139">URI parameters</span></span>**

<span data-ttu-id="b43c3-140">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="b43c3-140">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="b43c3-141">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="b43c3-141">URI parameter</span></span>      | <span data-ttu-id="b43c3-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b43c3-142">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="b43c3-143">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="b43c3-143">NetworkPath</span></span>        | <span data-ttu-id="b43c3-144">Die Netzwerkpfad für die Freigabe Sie Anmeldeinformationen für den Zugriff auf Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b43c3-144">The network path to the share you are adding credentials to access.</span></span> |
<br>

**<span data-ttu-id="b43c3-145">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="b43c3-145">Request headers</span></span>**

- <span data-ttu-id="b43c3-146">Keine</span><span class="sxs-lookup"><span data-stu-id="b43c3-146">None</span></span>

**<span data-ttu-id="b43c3-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="b43c3-147">Request body</span></span>**

- <span data-ttu-id="b43c3-148">Die folgenden JSON-Elemente:</span><span class="sxs-lookup"><span data-stu-id="b43c3-148">The following JSON elements:</span></span>
* <span data-ttu-id="b43c3-149">NetworkPath - den Pfad zu der Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="b43c3-149">NetworkPath - The path to the network share.</span></span>
* <span data-ttu-id="b43c3-150">UserName: der Benutzername, um die Anmeldeinformationen zu speichern.</span><span class="sxs-lookup"><span data-stu-id="b43c3-150">Username - The username to store the credentials under.</span></span>
* <span data-ttu-id="b43c3-151">Password: das neue oder aktualisierte Kennwort für diesen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="b43c3-151">Password - The new or updated password for this user.</span></span>

**<span data-ttu-id="b43c3-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="b43c3-152">Response</span></span>**   

- <span data-ttu-id="b43c3-153">Keine</span><span class="sxs-lookup"><span data-stu-id="b43c3-153">None</span></span>  

**<span data-ttu-id="b43c3-154">Statuscode</span><span class="sxs-lookup"><span data-stu-id="b43c3-154">Status code</span></span>**

<span data-ttu-id="b43c3-155">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="b43c3-155">This API has the following expected status codes.</span></span>

<span data-ttu-id="b43c3-156">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="b43c3-156">HTTP status code</span></span>      | <span data-ttu-id="b43c3-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b43c3-157">Description</span></span>
:------     | :-----
<span data-ttu-id="b43c3-158">204</span><span class="sxs-lookup"><span data-stu-id="b43c3-158">204</span></span> | <span data-ttu-id="b43c3-159">Erfolg</span><span class="sxs-lookup"><span data-stu-id="b43c3-159">Success</span></span>
<span data-ttu-id="b43c3-160">4XX</span><span class="sxs-lookup"><span data-stu-id="b43c3-160">4XX</span></span> | <span data-ttu-id="b43c3-161">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="b43c3-161">Error codes</span></span>
<span data-ttu-id="b43c3-162">5XX</span><span class="sxs-lookup"><span data-stu-id="b43c3-162">5XX</span></span> | <span data-ttu-id="b43c3-163">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="b43c3-163">Error codes</span></span>

## <a name="remove-stored-credentials-for-a-share"></a><span data-ttu-id="b43c3-164">Entfernen Sie die gespeicherte Anmeldeinformationen für eine Bereitstellungsfreigabe.</span><span class="sxs-lookup"><span data-stu-id="b43c3-164">Remove stored credentials for a share.</span></span>

**<span data-ttu-id="b43c3-165">Anforderung</span><span class="sxs-lookup"><span data-stu-id="b43c3-165">Request</span></span>**

<span data-ttu-id="b43c3-166">Methode</span><span class="sxs-lookup"><span data-stu-id="b43c3-166">Method</span></span>      | <span data-ttu-id="b43c3-167">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="b43c3-167">Request URI</span></span>
:------     | :-----
<span data-ttu-id="b43c3-168">DELETE</span><span class="sxs-lookup"><span data-stu-id="b43c3-168">DELETE</span></span> | <span data-ttu-id="b43c3-169">/ext/networkcredential</span><span class="sxs-lookup"><span data-stu-id="b43c3-169">/ext/networkcredential</span></span>
<br />
**<span data-ttu-id="b43c3-170">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="b43c3-170">URI parameters</span></span>**

<span data-ttu-id="b43c3-171">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="b43c3-171">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="b43c3-172">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="b43c3-172">URI parameter</span></span>      | <span data-ttu-id="b43c3-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b43c3-173">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="b43c3-174">NetworkPath</span><span class="sxs-lookup"><span data-stu-id="b43c3-174">NetworkPath</span></span>        | <span data-ttu-id="b43c3-175">Der Netzwerkpfad für die Freigabe aus der Sie die gespeicherte Anmeldeinformationen entfernen.</span><span class="sxs-lookup"><span data-stu-id="b43c3-175">The network path to the share from which you are removing stored credentials.</span></span> |
<br>

**<span data-ttu-id="b43c3-176">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="b43c3-176">Request headers</span></span>**

- <span data-ttu-id="b43c3-177">Keine</span><span class="sxs-lookup"><span data-stu-id="b43c3-177">None</span></span>

**<span data-ttu-id="b43c3-178">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="b43c3-178">Request body</span></span>**   

- <span data-ttu-id="b43c3-179">Keine</span><span class="sxs-lookup"><span data-stu-id="b43c3-179">None</span></span>

**<span data-ttu-id="b43c3-180">Antwort</span><span class="sxs-lookup"><span data-stu-id="b43c3-180">Response</span></span>**   

- <span data-ttu-id="b43c3-181">Keine</span><span class="sxs-lookup"><span data-stu-id="b43c3-181">None</span></span> 

**<span data-ttu-id="b43c3-182">Statuscode</span><span class="sxs-lookup"><span data-stu-id="b43c3-182">Status code</span></span>**

<span data-ttu-id="b43c3-183">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="b43c3-183">This API has the following expected status codes.</span></span>

<span data-ttu-id="b43c3-184">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="b43c3-184">HTTP status code</span></span>      | <span data-ttu-id="b43c3-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b43c3-185">Description</span></span>
:------     | :-----
<span data-ttu-id="b43c3-186">204</span><span class="sxs-lookup"><span data-stu-id="b43c3-186">204</span></span> | <span data-ttu-id="b43c3-187">Die Anforderung von Anmeldeinformationen war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="b43c3-187">The request to the credentials was successful.</span></span>
<span data-ttu-id="b43c3-188">4XX</span><span class="sxs-lookup"><span data-stu-id="b43c3-188">4XX</span></span> | <span data-ttu-id="b43c3-189">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="b43c3-189">Error codes</span></span>
<span data-ttu-id="b43c3-190">5XX</span><span class="sxs-lookup"><span data-stu-id="b43c3-190">5XX</span></span> | <span data-ttu-id="b43c3-191">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="b43c3-191">Error codes</span></span>

<br />
**<span data-ttu-id="b43c3-192">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="b43c3-192">Available device families</span></span>**

* <span data-ttu-id="b43c3-193">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="b43c3-193">Windows Xbox</span></span>


