---
author: m-stahl
title: Device Portal - Referenz zur API für Xbox-Entwicklereinstellungen
description: Erfahren Sie, wie Sie auf Xbox-Entwicklereinstellungen zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 6ab12b99-2944-49c9-92d9-f995efc4f6ce
ms.openlocfilehash: dfde4c45a4aa5a520e0aa98cd7f31f7d84854e08
ms.sourcegitcommit: 0e44f197e7e649d542ec3f67cd790a61dbe1226f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2017
ms.locfileid: "662506"
---
# <a name="developer-settings-api-reference"></a><span data-ttu-id="aeab6-104">Referenz zur API für Entwicklereinstellungen</span><span class="sxs-lookup"><span data-stu-id="aeab6-104">Developer settings API reference</span></span>   
<span data-ttu-id="aeab6-105">Mit dieser API können Sie auf Xbox One-Einstellungen zugreifen, die für die Entwicklung nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="aeab6-105">You can access Xbox One settings that are useful for development using this API.</span></span>

## <a name="get-all-developer-settings-at-once"></a><span data-ttu-id="aeab6-106">Gleichzeitiges Abrufen aller Entwicklereinstellungen</span><span class="sxs-lookup"><span data-stu-id="aeab6-106">Get all developer settings at once</span></span>

**<span data-ttu-id="aeab6-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="aeab6-107">Request</span></span>**

<span data-ttu-id="aeab6-108">Mithilfe der folgenden Anforderung können Sie alle Entwicklereinstellungen in einer einzigen Anforderung abrufen.</span><span class="sxs-lookup"><span data-stu-id="aeab6-108">You can use the following request to get all developer settings in a single request.</span></span>

<span data-ttu-id="aeab6-109">Methode</span><span class="sxs-lookup"><span data-stu-id="aeab6-109">Method</span></span>      | <span data-ttu-id="aeab6-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="aeab6-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="aeab6-111">GET</span><span class="sxs-lookup"><span data-stu-id="aeab6-111">GET</span></span> | <span data-ttu-id="aeab6-112">/ext/settings</span><span class="sxs-lookup"><span data-stu-id="aeab6-112">/ext/settings</span></span>
<br />
**<span data-ttu-id="aeab6-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="aeab6-113">URI parameters</span></span>**

- <span data-ttu-id="aeab6-114">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-114">None</span></span>

**<span data-ttu-id="aeab6-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="aeab6-115">Request headers</span></span>**

- <span data-ttu-id="aeab6-116">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-116">None</span></span>

**<span data-ttu-id="aeab6-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="aeab6-117">Request body</span></span>**

- <span data-ttu-id="aeab6-118">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-118">None</span></span>

**<span data-ttu-id="aeab6-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="aeab6-119">Response</span></span>**   
<span data-ttu-id="aeab6-120">Die Antwort ist ein JSON-Einstellungsarray mit allen Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="aeab6-120">The response is a Settings JSON array containing all the settings.</span></span> <span data-ttu-id="aeab6-121">Jedes Einstellungsobjekt enthält die folgenden Felder:</span><span class="sxs-lookup"><span data-stu-id="aeab6-121">Each settings object contains the following fields:</span></span>

<span data-ttu-id="aeab6-122">Name (Zeichenfolge): Der Name der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="aeab6-122">Name - (String) The name of the setting.</span></span>
<span data-ttu-id="aeab6-123">Value (Zeichenfolge): Der Wert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="aeab6-123">Value - (String) The value of the setting.</span></span>
<span data-ttu-id="aeab6-124">RequiresReboot („Yes“|„No“): Dieses Feld gibt an, ob ein Neustart erforderlich ist, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="aeab6-124">RequiresReboot - ("Yes" | "No") This field indicates whether the setting requires a reboot to take effect.</span></span>
<span data-ttu-id="aeab6-125">Disabled – („Yes“ | „No“): Dieses Feld gibt an, ob die Einstellung deaktiviert ist und nicht bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="aeab6-125">Disabled - ("Yes" | "No") This field indicates whether the setting is disabled and cannot be edited.</span></span>
<span data-ttu-id="aeab6-126">Category (String): Die Kategorie der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="aeab6-126">Category - (String) The category of the setting.</span></span>
<span data-ttu-id="aeab6-127">Type („Text“ | „Number“ | „Bool“ | „Select“): Dieses Feld gibt den Einstellungstyp an– Texteingabe, ein boolescher Wert („true“ oder „false“), eine Zahl mit einem Mindestwert oder Maximalwert oder Auswahl aus einer bestimmten Liste mit Werten.</span><span class="sxs-lookup"><span data-stu-id="aeab6-127">Type - ("Text" | "Number" | "Bool" | "Select") This field indicates what type a setting is: text input, a boolean value ("true" or "false"), a number with a min and max or select with a specific list of values.</span></span>

<span data-ttu-id="aeab6-128">Wenn die Einstellung eine Zahl ist; Min. – (Number): Dieses Feld gibt den numerischen Mindestwert der Einstellung an.</span><span class="sxs-lookup"><span data-stu-id="aeab6-128">If the setting is a number: Min - (Number) This field indicates the minimal numverical value of the setting.</span></span>
<span data-ttu-id="aeab6-129">Max. – (Number): Dieses Feld gibt den numerischen Maximalwert der Einstellung an.</span><span class="sxs-lookup"><span data-stu-id="aeab6-129">Max - (Number) This field indicates the maximum numverical value of the setting.</span></span>

<span data-ttu-id="aeab6-130">Wenn die Einstellung „Select“ ist; OptionsVariable – („Yes“ | „No“): Dieses Feld gibt an, ob die Einstellungsoptionen variabel sind und ob die gültigen Optionen ohne Neustart geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="aeab6-130">If the setting is select: OptionsVariable - ("Yes" | "No") This field indicates whether the setitng options are variable, if the valid options can change without a reboot.</span></span>
<span data-ttu-id="aeab6-131">Options: JSON-Array mit den gültigen Auswahloptionen als Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="aeab6-131">Options - JSON array containing the valid select options as strings.</span></span>

**<span data-ttu-id="aeab6-132">Statuscode</span><span class="sxs-lookup"><span data-stu-id="aeab6-132">Status code</span></span>**

<span data-ttu-id="aeab6-133">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="aeab6-133">This API has the following expected status codes.</span></span>

<span data-ttu-id="aeab6-134">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="aeab6-134">HTTP status code</span></span>      | <span data-ttu-id="aeab6-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aeab6-135">Description</span></span>
:------     | :-----
<span data-ttu-id="aeab6-136">200</span><span class="sxs-lookup"><span data-stu-id="aeab6-136">200</span></span> | <span data-ttu-id="aeab6-137">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="aeab6-137">Request was successful</span></span>
<span data-ttu-id="aeab6-138">4XX</span><span class="sxs-lookup"><span data-stu-id="aeab6-138">4XX</span></span> | <span data-ttu-id="aeab6-139">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="aeab6-139">Error codes</span></span>
<span data-ttu-id="aeab6-140">5XX</span><span class="sxs-lookup"><span data-stu-id="aeab6-140">5XX</span></span> | <span data-ttu-id="aeab6-141">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="aeab6-141">Error codes</span></span>

## <a name="get-settings-one-at-a-time"></a><span data-ttu-id="aeab6-142">Abrufen einzelner Einstellungen</span><span class="sxs-lookup"><span data-stu-id="aeab6-142">Get settings one at a time</span></span>
<span data-ttu-id="aeab6-143">Einstellungen können auch einzeln abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="aeab6-143">Settings can also be retrieved individually.</span></span>

**<span data-ttu-id="aeab6-144">Anforderung</span><span class="sxs-lookup"><span data-stu-id="aeab6-144">Request</span></span>**

<span data-ttu-id="aeab6-145">Mit der folgenden Anforderung können Sie Informationen zu einer einzelnen Einstellung abrufen.</span><span class="sxs-lookup"><span data-stu-id="aeab6-145">You can use the following request to get information about an individual setting.</span></span>

<span data-ttu-id="aeab6-146">Methode</span><span class="sxs-lookup"><span data-stu-id="aeab6-146">Method</span></span>      | <span data-ttu-id="aeab6-147">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="aeab6-147">Request URI</span></span>
:------     | :-----
<span data-ttu-id="aeab6-148">GET</span><span class="sxs-lookup"><span data-stu-id="aeab6-148">GET</span></span> | <span data-ttu-id="aeab6-149">/ext/settings/\<setting name\></span><span class="sxs-lookup"><span data-stu-id="aeab6-149">/ext/settings/\<setting name\></span></span>
<br />
**<span data-ttu-id="aeab6-150">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="aeab6-150">URI parameters</span></span>**

- <span data-ttu-id="aeab6-151">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-151">None</span></span>

**<span data-ttu-id="aeab6-152">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="aeab6-152">Request headers</span></span>**

- <span data-ttu-id="aeab6-153">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-153">None</span></span>

**<span data-ttu-id="aeab6-154">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="aeab6-154">Request body</span></span>**

- <span data-ttu-id="aeab6-155">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-155">None</span></span>

**<span data-ttu-id="aeab6-156">Antwort</span><span class="sxs-lookup"><span data-stu-id="aeab6-156">Response</span></span>**   
<span data-ttu-id="aeab6-157">Die Antwort ist ein JSON-Objekt mit folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="aeab6-157">The response is a JSON object with following fields:</span></span>

<span data-ttu-id="aeab6-158">Name (Zeichenfolge): Der Name der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="aeab6-158">Name - (String) The name of the setting.</span></span>
<span data-ttu-id="aeab6-159">Value (Zeichenfolge): Der Wert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="aeab6-159">Value - (String) The value of the setting.</span></span>
<span data-ttu-id="aeab6-160">RequiresReboot („Yes“|„No“): Dieses Feld gibt an, ob ein Neustart erforderlich ist, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="aeab6-160">RequiresReboot - ("Yes" | "No") This field indicates whether the setting requires a reboot to take effect.</span></span>
<span data-ttu-id="aeab6-161">Disabled – („Yes“ | „No“): Dieses Feld gibt an, ob die Einstellung deaktiviert ist und nicht bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="aeab6-161">Disabled - ("Yes" | "No") This field indicates whether the setting is disabled and cannot be edited.</span></span>
<span data-ttu-id="aeab6-162">Category (String): Die Kategorie der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="aeab6-162">Category - (String) The category of the setting.</span></span>
<span data-ttu-id="aeab6-163">Type („Text“ | „Number“ | „Bool“ | „Select“): Dieses Feld gibt den Einstellungstyp an– Texteingabe, ein boolescher Wert („true“ oder „false“), eine Zahl mit einem Mindestwert oder Maximalwert oder Auswahl aus einer bestimmten Liste mit Werten.</span><span class="sxs-lookup"><span data-stu-id="aeab6-163">Type - ("Text" | "Number" | "Bool" | "Select") This field indicates what type a setting is: text input, a boolean value ("true" or "false"), a number with a min and max or select with a specific list of values.</span></span>

<span data-ttu-id="aeab6-164">Wenn die Einstellung eine Zahl ist; Min. – (Number): Dieses Feld gibt den numerischen Mindestwert der Einstellung an.</span><span class="sxs-lookup"><span data-stu-id="aeab6-164">If the setting is a number: Min - (Number) This field indicates the minimal numverical value of the setting.</span></span>
<span data-ttu-id="aeab6-165">Max. – (Number): Dieses Feld gibt den numerischen Maximalwert der Einstellung an.</span><span class="sxs-lookup"><span data-stu-id="aeab6-165">Max - (Number) This field indicates the maximum numverical value of the setting.</span></span>

<span data-ttu-id="aeab6-166">Wenn die Einstellung „Select“ ist; OptionsVariable – („Yes“ | „No“): Dieses Feld gibt an, ob die Einstellungsoptionen variabel sind und ob die gültigen Optionen ohne Neustart geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="aeab6-166">If the setting is select: OptionsVariable - ("Yes" | "No") This field indicates whether the setitng options are variable, if the valid options can change without a reboot.</span></span>
<span data-ttu-id="aeab6-167">Options: JSON-Array mit den gültigen Auswahloptionen als Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="aeab6-167">Options - JSON array containing the valid select options as strings.</span></span>

**<span data-ttu-id="aeab6-168">Statuscode</span><span class="sxs-lookup"><span data-stu-id="aeab6-168">Status code</span></span>**

<span data-ttu-id="aeab6-169">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="aeab6-169">This API has the following expected status codes.</span></span>

<span data-ttu-id="aeab6-170">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="aeab6-170">HTTP status code</span></span>      | <span data-ttu-id="aeab6-171">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aeab6-171">Description</span></span>
:------     | :-----
<span data-ttu-id="aeab6-172">200</span><span class="sxs-lookup"><span data-stu-id="aeab6-172">200</span></span> | <span data-ttu-id="aeab6-173">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="aeab6-173">Request was successful</span></span>
<span data-ttu-id="aeab6-174">4XX</span><span class="sxs-lookup"><span data-stu-id="aeab6-174">4XX</span></span> | <span data-ttu-id="aeab6-175">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="aeab6-175">Error codes</span></span>
<span data-ttu-id="aeab6-176">5XX</span><span class="sxs-lookup"><span data-stu-id="aeab6-176">5XX</span></span> | <span data-ttu-id="aeab6-177">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="aeab6-177">Error codes</span></span>

## <a name="set-the-value-of-a-setting"></a><span data-ttu-id="aeab6-178">Festlegen des Werts einer Einstellung</span><span class="sxs-lookup"><span data-stu-id="aeab6-178">Set the value of a setting</span></span>
<span data-ttu-id="aeab6-179">Sie können den Wert einer Einstellung festlegen.</span><span class="sxs-lookup"><span data-stu-id="aeab6-179">You can set the value of a setting.</span></span>

**<span data-ttu-id="aeab6-180">Anforderung</span><span class="sxs-lookup"><span data-stu-id="aeab6-180">Request</span></span>**

<span data-ttu-id="aeab6-181">Mit der folgenden Anforderung können Sie den Wert für eine Einstellung festlegen.</span><span class="sxs-lookup"><span data-stu-id="aeab6-181">You can use the following request to set the value for a setting.</span></span>

<span data-ttu-id="aeab6-182">Methode</span><span class="sxs-lookup"><span data-stu-id="aeab6-182">Method</span></span>      | <span data-ttu-id="aeab6-183">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="aeab6-183">Request URI</span></span>
:------     | :-----
<span data-ttu-id="aeab6-184">PUT</span><span class="sxs-lookup"><span data-stu-id="aeab6-184">PUT</span></span> | <span data-ttu-id="aeab6-185">/ext/settings/\<setting name\></span><span class="sxs-lookup"><span data-stu-id="aeab6-185">/ext/settings/\<setting name\></span></span>
<br />
**<span data-ttu-id="aeab6-186">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="aeab6-186">URI parameters</span></span>**

- <span data-ttu-id="aeab6-187">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-187">None</span></span>

**<span data-ttu-id="aeab6-188">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="aeab6-188">Request headers</span></span>**

- <span data-ttu-id="aeab6-189">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-189">None</span></span>

**<span data-ttu-id="aeab6-190">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="aeab6-190">Request body</span></span>**   
<span data-ttu-id="aeab6-191">Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:</span><span class="sxs-lookup"><span data-stu-id="aeab6-191">The request body is JSON object containing the following field:</span></span>   
<span data-ttu-id="aeab6-192">Value (Zeichenfolge): Der neue Wert für die Einstellung.</span><span class="sxs-lookup"><span data-stu-id="aeab6-192">Value - (String) The new value for the setting.</span></span>

**<span data-ttu-id="aeab6-193">Antwort</span><span class="sxs-lookup"><span data-stu-id="aeab6-193">Response</span></span>**   

- <span data-ttu-id="aeab6-194">Keine</span><span class="sxs-lookup"><span data-stu-id="aeab6-194">None</span></span>

**<span data-ttu-id="aeab6-195">Statuscode</span><span class="sxs-lookup"><span data-stu-id="aeab6-195">Status code</span></span>**

<span data-ttu-id="aeab6-196">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="aeab6-196">This API has the following expected status codes.</span></span>

<span data-ttu-id="aeab6-197">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="aeab6-197">HTTP status code</span></span>      | <span data-ttu-id="aeab6-198">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aeab6-198">Description</span></span>
:------     | :-----
<span data-ttu-id="aeab6-199">200</span><span class="sxs-lookup"><span data-stu-id="aeab6-199">200</span></span> | <span data-ttu-id="aeab6-200">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="aeab6-200">Request was successful</span></span>
<span data-ttu-id="aeab6-201">4XX</span><span class="sxs-lookup"><span data-stu-id="aeab6-201">4XX</span></span> | <span data-ttu-id="aeab6-202">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="aeab6-202">Error codes</span></span>
<span data-ttu-id="aeab6-203">5XX</span><span class="sxs-lookup"><span data-stu-id="aeab6-203">5XX</span></span> | <span data-ttu-id="aeab6-204">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="aeab6-204">Error codes</span></span>

<br />
**<span data-ttu-id="aeab6-205">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="aeab6-205">Available device families</span></span>**

* <span data-ttu-id="aeab6-206">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="aeab6-206">Windows Xbox</span></span>