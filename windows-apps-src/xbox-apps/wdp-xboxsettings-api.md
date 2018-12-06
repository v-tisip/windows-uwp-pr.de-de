---
title: Device Portal - Referenz zur API für Xbox-Entwicklereinstellungen
description: Erfahren Sie, wie Sie auf Xbox-Entwicklereinstellungen zugreifen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 6ab12b99-2944-49c9-92d9-f995efc4f6ce
ms.localizationpriority: medium
ms.openlocfilehash: 402d535bf6ff9ced24bc642c17d13b2d48d79681
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8747027"
---
# <a name="developer-settings-api-reference"></a><span data-ttu-id="90291-104">Referenz zur API für Entwicklereinstellungen</span><span class="sxs-lookup"><span data-stu-id="90291-104">Developer settings API reference</span></span>   
<span data-ttu-id="90291-105">Mit dieser API können Sie auf Xbox One-Einstellungen zugreifen, die für die Entwicklung nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="90291-105">You can access Xbox One settings that are useful for development using this API.</span></span>

## <a name="get-all-developer-settings-at-once"></a><span data-ttu-id="90291-106">Gleichzeitiges Abrufen aller Entwicklereinstellungen</span><span class="sxs-lookup"><span data-stu-id="90291-106">Get all developer settings at once</span></span>

**<span data-ttu-id="90291-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="90291-107">Request</span></span>**

<span data-ttu-id="90291-108">Mithilfe der folgenden Anforderung können Sie alle Entwicklereinstellungen in einer einzigen Anforderung abrufen.</span><span class="sxs-lookup"><span data-stu-id="90291-108">You can use the following request to get all developer settings in a single request.</span></span>

<span data-ttu-id="90291-109">Methode</span><span class="sxs-lookup"><span data-stu-id="90291-109">Method</span></span>      | <span data-ttu-id="90291-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="90291-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="90291-111">GET</span><span class="sxs-lookup"><span data-stu-id="90291-111">GET</span></span> | <span data-ttu-id="90291-112">/ext/settings</span><span class="sxs-lookup"><span data-stu-id="90291-112">/ext/settings</span></span>
<br />
**<span data-ttu-id="90291-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="90291-113">URI parameters</span></span>**

- <span data-ttu-id="90291-114">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-114">None</span></span>

**<span data-ttu-id="90291-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="90291-115">Request headers</span></span>**

- <span data-ttu-id="90291-116">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-116">None</span></span>

**<span data-ttu-id="90291-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="90291-117">Request body</span></span>**

- <span data-ttu-id="90291-118">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-118">None</span></span>

**<span data-ttu-id="90291-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="90291-119">Response</span></span>**   
<span data-ttu-id="90291-120">Die Antwort ist ein JSON-Einstellungsarray mit allen Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="90291-120">The response is a Settings JSON array containing all the settings.</span></span> <span data-ttu-id="90291-121">Jedes Einstellungsobjekt enthält die folgenden Felder:</span><span class="sxs-lookup"><span data-stu-id="90291-121">Each settings object contains the following fields:</span></span>

* <span data-ttu-id="90291-122">Name (Zeichenfolge): Der Name der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-122">Name - (String) The name of the setting.</span></span>
* <span data-ttu-id="90291-123">Value (Zeichenfolge): Der Wert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-123">Value - (String) The value of the setting.</span></span>
* <span data-ttu-id="90291-124">RequiresReboot („Yes“|„No“): Dieses Feld gibt an, ob ein Neustart erforderlich ist, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="90291-124">RequiresReboot - ("Yes" | "No") This field indicates whether the setting requires a reboot to take effect.</span></span>
* <span data-ttu-id="90291-125">Disabled – („Yes“ | „No“): Dieses Feld gibt an, ob die Einstellung deaktiviert ist und nicht bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="90291-125">Disabled - ("Yes" | "No") This field indicates whether the setting is disabled and cannot be edited.</span></span>
* <span data-ttu-id="90291-126">Category (String): Die Kategorie der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-126">Category - (String) The category of the setting.</span></span>
* <span data-ttu-id="90291-127">Type („Text“ | „Number“ | „Bool“ | „Select“): Dieses Feld gibt den Einstellungstyp an– Texteingabe, ein boolescher Wert („true“ oder „false“), eine Zahl mit einem Mindestwert oder Maximalwert oder Auswahl aus einer bestimmten Liste mit Werten.</span><span class="sxs-lookup"><span data-stu-id="90291-127">Type - ("Text" | "Number" | "Bool" | "Select") This field indicates what type a setting is: text input, a boolean value ("true" or "false"), a number with a min and max or select with a specific list of values.</span></span>

<span data-ttu-id="90291-128">Wenn die Einstellung eine Zahl ist:</span><span class="sxs-lookup"><span data-stu-id="90291-128">If the setting is a number:</span></span>
* <span data-ttu-id="90291-129">Min. – (Number): Dieses Feld gibt den minimalen numerischen Wert der Einstellung an.</span><span class="sxs-lookup"><span data-stu-id="90291-129">Min - (Number) This field indicates the minimal numerical value of the setting.</span></span>
* <span data-ttu-id="90291-130">Max. – (Number): Dieses Feld gibt den numerischen Maximalwert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-130">Max - (Number) This field indicates the maximum numerical value of the setting.</span></span>

<span data-ttu-id="90291-131">Wenn die Einstellung "select" ist:</span><span class="sxs-lookup"><span data-stu-id="90291-131">If the setting is select:</span></span>
* <span data-ttu-id="90291-132">OptionsVariable – ("Yes" | "No") dieses Feld gibt an, ob die Einstellungsoptionen variabel sind, ob die gültigen Optionen ohne Neustart geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="90291-132">OptionsVariable - ("Yes" | "No") This field indicates whether the setting options are variable, if the valid options can change without a reboot.</span></span>
* <span data-ttu-id="90291-133">Options: JSON-Array mit den gültigen Auswahloptionen als Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="90291-133">Options - JSON array containing the valid select options as strings.</span></span>

**<span data-ttu-id="90291-134">Statuscode</span><span class="sxs-lookup"><span data-stu-id="90291-134">Status code</span></span>**

<span data-ttu-id="90291-135">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="90291-135">This API has the following expected status codes.</span></span>

<span data-ttu-id="90291-136">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="90291-136">HTTP status code</span></span>      | <span data-ttu-id="90291-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="90291-137">Description</span></span>
:------     | :-----
<span data-ttu-id="90291-138">200</span><span class="sxs-lookup"><span data-stu-id="90291-138">200</span></span> | <span data-ttu-id="90291-139">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="90291-139">Request was successful</span></span>
<span data-ttu-id="90291-140">4XX</span><span class="sxs-lookup"><span data-stu-id="90291-140">4XX</span></span> | <span data-ttu-id="90291-141">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="90291-141">Error codes</span></span>
<span data-ttu-id="90291-142">5XX</span><span class="sxs-lookup"><span data-stu-id="90291-142">5XX</span></span> | <span data-ttu-id="90291-143">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="90291-143">Error codes</span></span>

## <a name="get-settings-one-at-a-time"></a><span data-ttu-id="90291-144">Abrufen einzelner Einstellungen</span><span class="sxs-lookup"><span data-stu-id="90291-144">Get settings one at a time</span></span>
<span data-ttu-id="90291-145">Einstellungen können auch einzeln abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="90291-145">Settings can also be retrieved individually.</span></span>

**<span data-ttu-id="90291-146">Anforderung</span><span class="sxs-lookup"><span data-stu-id="90291-146">Request</span></span>**

<span data-ttu-id="90291-147">Mit der folgenden Anforderung können Sie Informationen zu einer einzelnen Einstellung abrufen.</span><span class="sxs-lookup"><span data-stu-id="90291-147">You can use the following request to get information about an individual setting.</span></span>

<span data-ttu-id="90291-148">Methode</span><span class="sxs-lookup"><span data-stu-id="90291-148">Method</span></span>      | <span data-ttu-id="90291-149">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="90291-149">Request URI</span></span>
:------     | :-----
<span data-ttu-id="90291-150">GET</span><span class="sxs-lookup"><span data-stu-id="90291-150">GET</span></span> | <span data-ttu-id="90291-151">/ext/settings/\<setting name\></span><span class="sxs-lookup"><span data-stu-id="90291-151">/ext/settings/\<setting name\></span></span>
<br />
**<span data-ttu-id="90291-152">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="90291-152">URI parameters</span></span>**

- <span data-ttu-id="90291-153">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-153">None</span></span>

**<span data-ttu-id="90291-154">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="90291-154">Request headers</span></span>**

- <span data-ttu-id="90291-155">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-155">None</span></span>

**<span data-ttu-id="90291-156">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="90291-156">Request body</span></span>**

- <span data-ttu-id="90291-157">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-157">None</span></span>

**<span data-ttu-id="90291-158">Antwort</span><span class="sxs-lookup"><span data-stu-id="90291-158">Response</span></span>**   
<span data-ttu-id="90291-159">Die Antwort ist ein JSON-Objekt mit folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="90291-159">The response is a JSON object with following fields:</span></span>

* <span data-ttu-id="90291-160">Name (Zeichenfolge): Der Name der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-160">Name - (String) The name of the setting.</span></span>
* <span data-ttu-id="90291-161">Value (Zeichenfolge): Der Wert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-161">Value - (String) The value of the setting.</span></span>
* <span data-ttu-id="90291-162">RequiresReboot („Yes“|„No“): Dieses Feld gibt an, ob ein Neustart erforderlich ist, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="90291-162">RequiresReboot - ("Yes" | "No") This field indicates whether the setting requires a reboot to take effect.</span></span>
* <span data-ttu-id="90291-163">Disabled – („Yes“ | „No“): Dieses Feld gibt an, ob die Einstellung deaktiviert ist und nicht bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="90291-163">Disabled - ("Yes" | "No") This field indicates whether the setting is disabled and cannot be edited.</span></span>
* <span data-ttu-id="90291-164">Category (String): Die Kategorie der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-164">Category - (String) The category of the setting.</span></span>
* <span data-ttu-id="90291-165">Type („Text“ | „Number“ | „Bool“ | „Select“): Dieses Feld gibt den Einstellungstyp an– Texteingabe, ein boolescher Wert („true“ oder „false“), eine Zahl mit einem Mindestwert oder Maximalwert oder Auswahl aus einer bestimmten Liste mit Werten.</span><span class="sxs-lookup"><span data-stu-id="90291-165">Type - ("Text" | "Number" | "Bool" | "Select") This field indicates what type a setting is: text input, a boolean value ("true" or "false"), a number with a min and max or select with a specific list of values.</span></span>

<span data-ttu-id="90291-166">Wenn die Einstellung eine Zahl ist:</span><span class="sxs-lookup"><span data-stu-id="90291-166">If the setting is a number:</span></span>
* <span data-ttu-id="90291-167">Min. – (Number): Dieses Feld gibt den minimalen numerischen Wert der Einstellung an.</span><span class="sxs-lookup"><span data-stu-id="90291-167">Min - (Number) This field indicates the minimal numerical value of the setting.</span></span>
* <span data-ttu-id="90291-168">Max. – (Number): Dieses Feld gibt den numerischen Maximalwert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-168">Max - (Number) This field indicates the maximum numerical value of the setting.</span></span>

<span data-ttu-id="90291-169">Wenn die Einstellung "select" ist:</span><span class="sxs-lookup"><span data-stu-id="90291-169">If the setting is select:</span></span>
* <span data-ttu-id="90291-170">OptionsVariable – ("Yes" | "No") dieses Feld gibt an, ob die Einstellungsoptionen variabel sind, ob die gültigen Optionen ohne Neustart geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="90291-170">OptionsVariable - ("Yes" | "No") This field indicates whether the setting options are variable, if the valid options can change without a reboot.</span></span>
* <span data-ttu-id="90291-171">Options: JSON-Array mit den gültigen Auswahloptionen als Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="90291-171">Options - JSON array containing the valid select options as strings.</span></span>

**<span data-ttu-id="90291-172">Statuscode</span><span class="sxs-lookup"><span data-stu-id="90291-172">Status code</span></span>**

<span data-ttu-id="90291-173">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="90291-173">This API has the following expected status codes.</span></span>

<span data-ttu-id="90291-174">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="90291-174">HTTP status code</span></span>      | <span data-ttu-id="90291-175">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="90291-175">Description</span></span>
:------     | :-----
<span data-ttu-id="90291-176">200</span><span class="sxs-lookup"><span data-stu-id="90291-176">200</span></span> | <span data-ttu-id="90291-177">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="90291-177">Request was successful</span></span>
<span data-ttu-id="90291-178">4XX</span><span class="sxs-lookup"><span data-stu-id="90291-178">4XX</span></span> | <span data-ttu-id="90291-179">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="90291-179">Error codes</span></span>
<span data-ttu-id="90291-180">5XX</span><span class="sxs-lookup"><span data-stu-id="90291-180">5XX</span></span> | <span data-ttu-id="90291-181">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="90291-181">Error codes</span></span>

## <a name="set-the-value-of-a-setting"></a><span data-ttu-id="90291-182">Festlegen des Werts einer Einstellung</span><span class="sxs-lookup"><span data-stu-id="90291-182">Set the value of a setting</span></span>
<span data-ttu-id="90291-183">Sie können den Wert einer Einstellung festlegen.</span><span class="sxs-lookup"><span data-stu-id="90291-183">You can set the value of a setting.</span></span>

**<span data-ttu-id="90291-184">Anforderung</span><span class="sxs-lookup"><span data-stu-id="90291-184">Request</span></span>**

<span data-ttu-id="90291-185">Mit der folgenden Anforderung können Sie den Wert für eine Einstellung festlegen.</span><span class="sxs-lookup"><span data-stu-id="90291-185">You can use the following request to set the value for a setting.</span></span>

<span data-ttu-id="90291-186">Methode</span><span class="sxs-lookup"><span data-stu-id="90291-186">Method</span></span>      | <span data-ttu-id="90291-187">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="90291-187">Request URI</span></span>
:------     | :-----
<span data-ttu-id="90291-188">PUT</span><span class="sxs-lookup"><span data-stu-id="90291-188">PUT</span></span> | <span data-ttu-id="90291-189">/ext/settings/\<setting name\></span><span class="sxs-lookup"><span data-stu-id="90291-189">/ext/settings/\<setting name\></span></span>
<br />
**<span data-ttu-id="90291-190">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="90291-190">URI parameters</span></span>**

- <span data-ttu-id="90291-191">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-191">None</span></span>

**<span data-ttu-id="90291-192">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="90291-192">Request headers</span></span>**

- <span data-ttu-id="90291-193">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-193">None</span></span>

**<span data-ttu-id="90291-194">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="90291-194">Request body</span></span>**   
<span data-ttu-id="90291-195">Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:</span><span class="sxs-lookup"><span data-stu-id="90291-195">The request body is JSON object containing the following field:</span></span>   
<span data-ttu-id="90291-196">Value (Zeichenfolge): Der neue Wert für die Einstellung.</span><span class="sxs-lookup"><span data-stu-id="90291-196">Value - (String) The new value for the setting.</span></span>

**<span data-ttu-id="90291-197">Antwort</span><span class="sxs-lookup"><span data-stu-id="90291-197">Response</span></span>**   

- <span data-ttu-id="90291-198">Keine</span><span class="sxs-lookup"><span data-stu-id="90291-198">None</span></span>

**<span data-ttu-id="90291-199">Statuscode</span><span class="sxs-lookup"><span data-stu-id="90291-199">Status code</span></span>**

<span data-ttu-id="90291-200">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="90291-200">This API has the following expected status codes.</span></span>

<span data-ttu-id="90291-201">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="90291-201">HTTP status code</span></span>      | <span data-ttu-id="90291-202">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="90291-202">Description</span></span>
:------     | :-----
<span data-ttu-id="90291-203">200</span><span class="sxs-lookup"><span data-stu-id="90291-203">200</span></span> | <span data-ttu-id="90291-204">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="90291-204">Request was successful</span></span>
<span data-ttu-id="90291-205">4XX</span><span class="sxs-lookup"><span data-stu-id="90291-205">4XX</span></span> | <span data-ttu-id="90291-206">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="90291-206">Error codes</span></span>
<span data-ttu-id="90291-207">5XX</span><span class="sxs-lookup"><span data-stu-id="90291-207">5XX</span></span> | <span data-ttu-id="90291-208">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="90291-208">Error codes</span></span>

<br />
**<span data-ttu-id="90291-209">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="90291-209">Available device families</span></span>**

* <span data-ttu-id="90291-210">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="90291-210">Windows Xbox</span></span>