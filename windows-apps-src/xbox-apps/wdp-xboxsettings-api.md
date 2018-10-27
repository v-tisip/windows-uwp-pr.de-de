---
author: m-stahl
title: Device Portal - Referenz zur API für Xbox-Entwicklereinstellungen
description: Erfahren Sie, wie Sie auf Xbox-Entwicklereinstellungen zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 6ab12b99-2944-49c9-92d9-f995efc4f6ce
ms.localizationpriority: medium
ms.openlocfilehash: 8f3d0c09b242f8d60b06ee0dc510ad9a756466c5
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5703555"
---
# <a name="developer-settings-api-reference"></a><span data-ttu-id="c0ca3-104">Referenz zur API für Entwicklereinstellungen</span><span class="sxs-lookup"><span data-stu-id="c0ca3-104">Developer settings API reference</span></span>   
<span data-ttu-id="c0ca3-105">Mit dieser API können Sie auf Xbox One-Einstellungen zugreifen, die für die Entwicklung nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-105">You can access Xbox One settings that are useful for development using this API.</span></span>

## <a name="get-all-developer-settings-at-once"></a><span data-ttu-id="c0ca3-106">Gleichzeitiges Abrufen aller Entwicklereinstellungen</span><span class="sxs-lookup"><span data-stu-id="c0ca3-106">Get all developer settings at once</span></span>

**<span data-ttu-id="c0ca3-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c0ca3-107">Request</span></span>**

<span data-ttu-id="c0ca3-108">Mithilfe der folgenden Anforderung können Sie alle Entwicklereinstellungen in einer einzigen Anforderung abrufen.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-108">You can use the following request to get all developer settings in a single request.</span></span>

<span data-ttu-id="c0ca3-109">Methode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-109">Method</span></span>      | <span data-ttu-id="c0ca3-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c0ca3-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="c0ca3-111">GET</span><span class="sxs-lookup"><span data-stu-id="c0ca3-111">GET</span></span> | <span data-ttu-id="c0ca3-112">/ext/settings</span><span class="sxs-lookup"><span data-stu-id="c0ca3-112">/ext/settings</span></span>
<br />
**<span data-ttu-id="c0ca3-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="c0ca3-113">URI parameters</span></span>**

- <span data-ttu-id="c0ca3-114">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-114">None</span></span>

**<span data-ttu-id="c0ca3-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c0ca3-115">Request headers</span></span>**

- <span data-ttu-id="c0ca3-116">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-116">None</span></span>

**<span data-ttu-id="c0ca3-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c0ca3-117">Request body</span></span>**

- <span data-ttu-id="c0ca3-118">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-118">None</span></span>

**<span data-ttu-id="c0ca3-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="c0ca3-119">Response</span></span>**   
<span data-ttu-id="c0ca3-120">Die Antwort ist ein JSON-Einstellungsarray mit allen Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-120">The response is a Settings JSON array containing all the settings.</span></span> <span data-ttu-id="c0ca3-121">Jedes Einstellungsobjekt enthält die folgenden Felder:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-121">Each settings object contains the following fields:</span></span>

* <span data-ttu-id="c0ca3-122">Name (Zeichenfolge): Der Name der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-122">Name - (String) The name of the setting.</span></span>
* <span data-ttu-id="c0ca3-123">Value (Zeichenfolge): Der Wert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-123">Value - (String) The value of the setting.</span></span>
* <span data-ttu-id="c0ca3-124">RequiresReboot („Yes“|„No“): Dieses Feld gibt an, ob ein Neustart erforderlich ist, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-124">RequiresReboot - ("Yes" | "No") This field indicates whether the setting requires a reboot to take effect.</span></span>
* <span data-ttu-id="c0ca3-125">Disabled – („Yes“ | „No“): Dieses Feld gibt an, ob die Einstellung deaktiviert ist und nicht bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-125">Disabled - ("Yes" | "No") This field indicates whether the setting is disabled and cannot be edited.</span></span>
* <span data-ttu-id="c0ca3-126">Category (String): Die Kategorie der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-126">Category - (String) The category of the setting.</span></span>
* <span data-ttu-id="c0ca3-127">Type („Text“ | „Number“ | „Bool“ | „Select“): Dieses Feld gibt den Einstellungstyp an– Texteingabe, ein boolescher Wert („true“ oder „false“), eine Zahl mit einem Mindestwert oder Maximalwert oder Auswahl aus einer bestimmten Liste mit Werten.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-127">Type - ("Text" | "Number" | "Bool" | "Select") This field indicates what type a setting is: text input, a boolean value ("true" or "false"), a number with a min and max or select with a specific list of values.</span></span>

<span data-ttu-id="c0ca3-128">Wenn die Einstellung eine Zahl ist:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-128">If the setting is a number:</span></span>
* <span data-ttu-id="c0ca3-129">Min. – (Number): Dieses Feld gibt den minimalen numerischen Wert der Einstellung an.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-129">Min - (Number) This field indicates the minimal numerical value of the setting.</span></span>
* <span data-ttu-id="c0ca3-130">Max. – (Number): Dieses Feld gibt den numerischen Maximalwert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-130">Max - (Number) This field indicates the maximum numerical value of the setting.</span></span>

<span data-ttu-id="c0ca3-131">Wenn die Einstellung "select" ist:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-131">If the setting is select:</span></span>
* <span data-ttu-id="c0ca3-132">OptionsVariable – ("Yes" | "No") dieses Feld gibt an, ob die Einstellungsoptionen variabel sind, ob die gültigen Optionen ohne Neustart geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-132">OptionsVariable - ("Yes" | "No") This field indicates whether the setting options are variable, if the valid options can change without a reboot.</span></span>
* <span data-ttu-id="c0ca3-133">Options: JSON-Array mit den gültigen Auswahloptionen als Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-133">Options - JSON array containing the valid select options as strings.</span></span>

**<span data-ttu-id="c0ca3-134">Statuscode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-134">Status code</span></span>**

<span data-ttu-id="c0ca3-135">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-135">This API has the following expected status codes.</span></span>

<span data-ttu-id="c0ca3-136">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-136">HTTP status code</span></span>      | <span data-ttu-id="c0ca3-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c0ca3-137">Description</span></span>
:------     | :-----
<span data-ttu-id="c0ca3-138">200</span><span class="sxs-lookup"><span data-stu-id="c0ca3-138">200</span></span> | <span data-ttu-id="c0ca3-139">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-139">Request was successful</span></span>
<span data-ttu-id="c0ca3-140">4XX</span><span class="sxs-lookup"><span data-stu-id="c0ca3-140">4XX</span></span> | <span data-ttu-id="c0ca3-141">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c0ca3-141">Error codes</span></span>
<span data-ttu-id="c0ca3-142">5XX</span><span class="sxs-lookup"><span data-stu-id="c0ca3-142">5XX</span></span> | <span data-ttu-id="c0ca3-143">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c0ca3-143">Error codes</span></span>

## <a name="get-settings-one-at-a-time"></a><span data-ttu-id="c0ca3-144">Abrufen einzelner Einstellungen</span><span class="sxs-lookup"><span data-stu-id="c0ca3-144">Get settings one at a time</span></span>
<span data-ttu-id="c0ca3-145">Einstellungen können auch einzeln abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-145">Settings can also be retrieved individually.</span></span>

**<span data-ttu-id="c0ca3-146">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c0ca3-146">Request</span></span>**

<span data-ttu-id="c0ca3-147">Mit der folgenden Anforderung können Sie Informationen zu einer einzelnen Einstellung abrufen.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-147">You can use the following request to get information about an individual setting.</span></span>

<span data-ttu-id="c0ca3-148">Methode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-148">Method</span></span>      | <span data-ttu-id="c0ca3-149">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c0ca3-149">Request URI</span></span>
:------     | :-----
<span data-ttu-id="c0ca3-150">GET</span><span class="sxs-lookup"><span data-stu-id="c0ca3-150">GET</span></span> | <span data-ttu-id="c0ca3-151">/ext/settings/\<setting name\></span><span class="sxs-lookup"><span data-stu-id="c0ca3-151">/ext/settings/\<setting name\></span></span>
<br />
**<span data-ttu-id="c0ca3-152">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="c0ca3-152">URI parameters</span></span>**

- <span data-ttu-id="c0ca3-153">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-153">None</span></span>

**<span data-ttu-id="c0ca3-154">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c0ca3-154">Request headers</span></span>**

- <span data-ttu-id="c0ca3-155">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-155">None</span></span>

**<span data-ttu-id="c0ca3-156">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c0ca3-156">Request body</span></span>**

- <span data-ttu-id="c0ca3-157">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-157">None</span></span>

**<span data-ttu-id="c0ca3-158">Antwort</span><span class="sxs-lookup"><span data-stu-id="c0ca3-158">Response</span></span>**   
<span data-ttu-id="c0ca3-159">Die Antwort ist ein JSON-Objekt mit folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-159">The response is a JSON object with following fields:</span></span>

* <span data-ttu-id="c0ca3-160">Name (Zeichenfolge): Der Name der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-160">Name - (String) The name of the setting.</span></span>
* <span data-ttu-id="c0ca3-161">Value (Zeichenfolge): Der Wert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-161">Value - (String) The value of the setting.</span></span>
* <span data-ttu-id="c0ca3-162">RequiresReboot („Yes“|„No“): Dieses Feld gibt an, ob ein Neustart erforderlich ist, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-162">RequiresReboot - ("Yes" | "No") This field indicates whether the setting requires a reboot to take effect.</span></span>
* <span data-ttu-id="c0ca3-163">Disabled – („Yes“ | „No“): Dieses Feld gibt an, ob die Einstellung deaktiviert ist und nicht bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-163">Disabled - ("Yes" | "No") This field indicates whether the setting is disabled and cannot be edited.</span></span>
* <span data-ttu-id="c0ca3-164">Category (String): Die Kategorie der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-164">Category - (String) The category of the setting.</span></span>
* <span data-ttu-id="c0ca3-165">Type („Text“ | „Number“ | „Bool“ | „Select“): Dieses Feld gibt den Einstellungstyp an– Texteingabe, ein boolescher Wert („true“ oder „false“), eine Zahl mit einem Mindestwert oder Maximalwert oder Auswahl aus einer bestimmten Liste mit Werten.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-165">Type - ("Text" | "Number" | "Bool" | "Select") This field indicates what type a setting is: text input, a boolean value ("true" or "false"), a number with a min and max or select with a specific list of values.</span></span>

<span data-ttu-id="c0ca3-166">Wenn die Einstellung eine Zahl ist:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-166">If the setting is a number:</span></span>
* <span data-ttu-id="c0ca3-167">Min. – (Number): Dieses Feld gibt den minimalen numerischen Wert der Einstellung an.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-167">Min - (Number) This field indicates the minimal numerical value of the setting.</span></span>
* <span data-ttu-id="c0ca3-168">Max. – (Number): Dieses Feld gibt den numerischen Maximalwert der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-168">Max - (Number) This field indicates the maximum numerical value of the setting.</span></span>

<span data-ttu-id="c0ca3-169">Wenn die Einstellung "select" ist:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-169">If the setting is select:</span></span>
* <span data-ttu-id="c0ca3-170">OptionsVariable – ("Yes" | "No") dieses Feld gibt an, ob die Einstellungsoptionen variabel sind, ob die gültigen Optionen ohne Neustart geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-170">OptionsVariable - ("Yes" | "No") This field indicates whether the setting options are variable, if the valid options can change without a reboot.</span></span>
* <span data-ttu-id="c0ca3-171">Options: JSON-Array mit den gültigen Auswahloptionen als Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-171">Options - JSON array containing the valid select options as strings.</span></span>

**<span data-ttu-id="c0ca3-172">Statuscode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-172">Status code</span></span>**

<span data-ttu-id="c0ca3-173">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-173">This API has the following expected status codes.</span></span>

<span data-ttu-id="c0ca3-174">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-174">HTTP status code</span></span>      | <span data-ttu-id="c0ca3-175">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c0ca3-175">Description</span></span>
:------     | :-----
<span data-ttu-id="c0ca3-176">200</span><span class="sxs-lookup"><span data-stu-id="c0ca3-176">200</span></span> | <span data-ttu-id="c0ca3-177">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-177">Request was successful</span></span>
<span data-ttu-id="c0ca3-178">4XX</span><span class="sxs-lookup"><span data-stu-id="c0ca3-178">4XX</span></span> | <span data-ttu-id="c0ca3-179">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c0ca3-179">Error codes</span></span>
<span data-ttu-id="c0ca3-180">5XX</span><span class="sxs-lookup"><span data-stu-id="c0ca3-180">5XX</span></span> | <span data-ttu-id="c0ca3-181">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c0ca3-181">Error codes</span></span>

## <a name="set-the-value-of-a-setting"></a><span data-ttu-id="c0ca3-182">Festlegen des Werts einer Einstellung</span><span class="sxs-lookup"><span data-stu-id="c0ca3-182">Set the value of a setting</span></span>
<span data-ttu-id="c0ca3-183">Sie können den Wert einer Einstellung festlegen.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-183">You can set the value of a setting.</span></span>

**<span data-ttu-id="c0ca3-184">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c0ca3-184">Request</span></span>**

<span data-ttu-id="c0ca3-185">Mit der folgenden Anforderung können Sie den Wert für eine Einstellung festlegen.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-185">You can use the following request to set the value for a setting.</span></span>

<span data-ttu-id="c0ca3-186">Methode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-186">Method</span></span>      | <span data-ttu-id="c0ca3-187">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c0ca3-187">Request URI</span></span>
:------     | :-----
<span data-ttu-id="c0ca3-188">PUT</span><span class="sxs-lookup"><span data-stu-id="c0ca3-188">PUT</span></span> | <span data-ttu-id="c0ca3-189">/ext/settings/\<setting name\></span><span class="sxs-lookup"><span data-stu-id="c0ca3-189">/ext/settings/\<setting name\></span></span>
<br />
**<span data-ttu-id="c0ca3-190">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="c0ca3-190">URI parameters</span></span>**

- <span data-ttu-id="c0ca3-191">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-191">None</span></span>

**<span data-ttu-id="c0ca3-192">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c0ca3-192">Request headers</span></span>**

- <span data-ttu-id="c0ca3-193">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-193">None</span></span>

**<span data-ttu-id="c0ca3-194">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c0ca3-194">Request body</span></span>**   
<span data-ttu-id="c0ca3-195">Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-195">The request body is JSON object containing the following field:</span></span>   
<span data-ttu-id="c0ca3-196">Value (Zeichenfolge): Der neue Wert für die Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-196">Value - (String) The new value for the setting.</span></span>

**<span data-ttu-id="c0ca3-197">Antwort</span><span class="sxs-lookup"><span data-stu-id="c0ca3-197">Response</span></span>**   

- <span data-ttu-id="c0ca3-198">Keine</span><span class="sxs-lookup"><span data-stu-id="c0ca3-198">None</span></span>

**<span data-ttu-id="c0ca3-199">Statuscode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-199">Status code</span></span>**

<span data-ttu-id="c0ca3-200">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="c0ca3-200">This API has the following expected status codes.</span></span>

<span data-ttu-id="c0ca3-201">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="c0ca3-201">HTTP status code</span></span>      | <span data-ttu-id="c0ca3-202">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c0ca3-202">Description</span></span>
:------     | :-----
<span data-ttu-id="c0ca3-203">200</span><span class="sxs-lookup"><span data-stu-id="c0ca3-203">200</span></span> | <span data-ttu-id="c0ca3-204">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-204">Request was successful</span></span>
<span data-ttu-id="c0ca3-205">4XX</span><span class="sxs-lookup"><span data-stu-id="c0ca3-205">4XX</span></span> | <span data-ttu-id="c0ca3-206">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c0ca3-206">Error codes</span></span>
<span data-ttu-id="c0ca3-207">5XX</span><span class="sxs-lookup"><span data-stu-id="c0ca3-207">5XX</span></span> | <span data-ttu-id="c0ca3-208">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c0ca3-208">Error codes</span></span>

<br />
**<span data-ttu-id="c0ca3-209">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="c0ca3-209">Available device families</span></span>**

* <span data-ttu-id="c0ca3-210">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="c0ca3-210">Windows Xbox</span></span>