---
author: TylerMSFT
title: Schema „ms-tonepicker“
description: In diesem Thema wird URI-Schema „ms-tonepicker“ beschrieben und wie Sie dieses verwenden können, um eine Tonauswahl anzuzeigen und Töne auszuwählen, zu speichern und den Anzeigenamen für Töne abzurufen.
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 0c17e4fb-7241-4da9-b457-d6d3a7aefccb
ms.localizationpriority: medium
ms.openlocfilehash: 61967f0aa81c49cb4e81b11bedac84c318be1840
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6970446"
---
# <a name="choose-and-save-tones-using-the-ms-tonepicker-uri-scheme"></a><span data-ttu-id="ea8cc-104">Wählen und Speichern von Tönen mithilfe des URI-Schemas „ms-tonepicker“</span><span class="sxs-lookup"><span data-stu-id="ea8cc-104">Choose and save tones using the ms-tonepicker URI scheme</span></span>

<span data-ttu-id="ea8cc-105">In diesem Thema wird die Verwendung des URI-Schemas **ms-tonepicker:** beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-105">This topic describes how to use the **ms-tonepicker:** URI scheme.</span></span> <span data-ttu-id="ea8cc-106">Dieses URI-Schema kann verwendet werden, um:</span><span class="sxs-lookup"><span data-stu-id="ea8cc-106">This URI scheme can be used to:</span></span>
- <span data-ttu-id="ea8cc-107">Zu ermitteln, ob die Tonauswahl auf dem Gerät verfügbar ist;</span><span class="sxs-lookup"><span data-stu-id="ea8cc-107">Determine if the tone picker is available on the device.</span></span>
- <span data-ttu-id="ea8cc-108">Die Tonauswahl anzuzeigen, um die verfügbaren Klingeltöne, Systemtöne, SMS-Klingeltöne und Alarmtöne aufzulisten, und ein Tontoken zu erhalten, das den vom Benutzer ausgewählten Ton darstellt;</span><span class="sxs-lookup"><span data-stu-id="ea8cc-108">Display the tone picker to list available ringtones, system sounds, text tones, and alarm sounds; and get a tone token which represents the sound the user selected.</span></span>
- <span data-ttu-id="ea8cc-109">Das Tool zum von Tönen anzuzeigen, das ein Sounddateitoken als Eingabe erhält und es auf dem Gerät speichert.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-109">Display the tone saver, which takes a sound file token as input and saves it to the device.</span></span> <span data-ttu-id="ea8cc-110">Gespeicherte Töne stehen anschließend über die Tonauswahl zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-110">Saved tones are then available via the tone picker.</span></span> <span data-ttu-id="ea8cc-111">Benutzer können dem Ton einen Anzeigenamen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-111">Users can also give the tone a friendly name.</span></span>
- <span data-ttu-id="ea8cc-112">Konvertieren Sie ein Tontoken in dessen Anzeigenamen.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-112">Convert a tone token to its friendly name.</span></span>

## <a name="ms-tonepicker-uri-scheme-reference"></a><span data-ttu-id="ea8cc-113">ms-tonepicker: URI-Schemareferenz</span><span class="sxs-lookup"><span data-stu-id="ea8cc-113">ms-tonepicker: URI scheme reference</span></span>

<span data-ttu-id="ea8cc-114">Dieses URI-Schema übergibt keine Argumente über die URI-Schema-Zeichenfolge, sondern über einen [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx).</span><span class="sxs-lookup"><span data-stu-id="ea8cc-114">This URI scheme does not pass arguments via the URI scheme string, but instead passes arguments via a [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx).</span></span> <span data-ttu-id="ea8cc-115">Alle Zeichenfolgen beachten die Groß- und Kleinschreibung.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-115">All strings are case-sensitive.</span></span>

<span data-ttu-id="ea8cc-116">In den folgenden Abschnitten wird angegeben, welche Argumente übergeben werden müssen, um die angegebene Aufgabe auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-116">The sections below indicate which arguments should be passed to accomplish the specified task.</span></span>

## <a name="task-determine-if-the-tone-picker-is-available-on-the-device"></a><span data-ttu-id="ea8cc-117">Aufgabe: Ermitteln, ob die Tonauswahl auf dem Gerät verfügbar ist</span><span class="sxs-lookup"><span data-stu-id="ea8cc-117">Task: Determine if the tone picker is available on the device</span></span>
```cs
var status = await Launcher.QueryUriSupportAsync(new Uri("ms-tonepicker:"),     
                                     LaunchQuerySupportType.UriForResults,
                                     "Microsoft.Tonepicker_8wekyb3d8bbwe");

if (status != LaunchQuerySupportStatus.Available)
{
    // the tone picker is not available
}
```

## <a name="task-display-the-tone-picker"></a><span data-ttu-id="ea8cc-118">Aufgabe: Anzeige der Tonauswahl</span><span class="sxs-lookup"><span data-stu-id="ea8cc-118">Task: Display the tone picker</span></span>

<span data-ttu-id="ea8cc-119">Die Argumente, die Sie zum Anzeigen der Tonauswahl übergeben können, sind:</span><span class="sxs-lookup"><span data-stu-id="ea8cc-119">The arguments you can pass to display the tone picker are as follows:</span></span>

| <span data-ttu-id="ea8cc-120">Parameter</span><span class="sxs-lookup"><span data-stu-id="ea8cc-120">Parameter</span></span> | <span data-ttu-id="ea8cc-121">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8cc-121">Type</span></span> | <span data-ttu-id="ea8cc-122">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ea8cc-122">Required</span></span> | <span data-ttu-id="ea8cc-123">Mögliche Werte</span><span class="sxs-lookup"><span data-stu-id="ea8cc-123">Possible values</span></span> | <span data-ttu-id="ea8cc-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8cc-124">Description</span></span> |
|-----------|------|----------|-------|-------------|
| <span data-ttu-id="ea8cc-125">Action</span><span class="sxs-lookup"><span data-stu-id="ea8cc-125">Action</span></span> | <span data-ttu-id="ea8cc-126">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-126">string</span></span> | <span data-ttu-id="ea8cc-127">Ja</span><span class="sxs-lookup"><span data-stu-id="ea8cc-127">yes</span></span> | <span data-ttu-id="ea8cc-128">"PickRingtone"</span><span class="sxs-lookup"><span data-stu-id="ea8cc-128">"PickRingtone"</span></span> | <span data-ttu-id="ea8cc-129">Öffnet die Tonauswahl.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-129">Opens the tone picker.</span></span> |
| <span data-ttu-id="ea8cc-130">CurrentToneFilePath</span><span class="sxs-lookup"><span data-stu-id="ea8cc-130">CurrentToneFilePath</span></span> | <span data-ttu-id="ea8cc-131">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-131">string</span></span> | <span data-ttu-id="ea8cc-132">Nein</span><span class="sxs-lookup"><span data-stu-id="ea8cc-132">no</span></span> | <span data-ttu-id="ea8cc-133">Ein vorhandenes Tontoken.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-133">An existing tone token.</span></span> | <span data-ttu-id="ea8cc-134">Der Ton, der in der Tonauswahl als aktueller Ton angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-134">The tone to show as the current tone in the tone picker.</span></span> <span data-ttu-id="ea8cc-135">Wenn dieser Wert nicht festgelegt ist, ist der erste Ton in der Liste standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-135">If this value is not set, the first tone on the list is selected by default.</span></span><br><span data-ttu-id="ea8cc-136">Streng genommen, ist dies kein Dateipfad.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-136">This is not, strictly speaking, a file path.</span></span> <span data-ttu-id="ea8cc-137">Sie können einen geeigneten Wert für `CurrenttoneFilePath` aus dem Wert `ToneToken` erhalten, der von der Tonauswahl zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-137">You can get a suitable value for `CurrenttoneFilePath` from the `ToneToken` value returned from the tone picker.</span></span>  |
| <span data-ttu-id="ea8cc-138">TypeFilter</span><span class="sxs-lookup"><span data-stu-id="ea8cc-138">TypeFilter</span></span> | <span data-ttu-id="ea8cc-139">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-139">string</span></span> | <span data-ttu-id="ea8cc-140">Nein</span><span class="sxs-lookup"><span data-stu-id="ea8cc-140">no</span></span> | <span data-ttu-id="ea8cc-141">"Ringtones", "Notifications", "Alarms", "None"</span><span class="sxs-lookup"><span data-stu-id="ea8cc-141">"Ringtones", "Notifications", "Alarms", "None"</span></span> | <span data-ttu-id="ea8cc-142">Wählt die Töne aus, die der Auswahl hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-142">Selects which tones to add to the picker.</span></span> <span data-ttu-id="ea8cc-143">Wenn kein Filter angegeben ist, werden alle Töne angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-143">If no filter is specified then all tones are displayed.</span></span> |

<span data-ttu-id="ea8cc-144">Die Werte, die in [LaunchUriResults.Result](https://msdn.microsoft.com/library/windows/apps/windows.system.launchuriresult.result.aspx) zurückgegeben werden:</span><span class="sxs-lookup"><span data-stu-id="ea8cc-144">The values that are returned in [LaunchUriResults.Result](https://msdn.microsoft.com/library/windows/apps/windows.system.launchuriresult.result.aspx):</span></span>

| <span data-ttu-id="ea8cc-145">Rückgabewerte</span><span class="sxs-lookup"><span data-stu-id="ea8cc-145">Return values</span></span> | <span data-ttu-id="ea8cc-146">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8cc-146">Type</span></span> | <span data-ttu-id="ea8cc-147">Mögliche Werte</span><span class="sxs-lookup"><span data-stu-id="ea8cc-147">Possible values</span></span> | <span data-ttu-id="ea8cc-148">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8cc-148">Description</span></span> |
|--------------|------|-------|-------------|
| <span data-ttu-id="ea8cc-149">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="ea8cc-149">Result</span></span> | <span data-ttu-id="ea8cc-150">Int32</span><span class="sxs-lookup"><span data-stu-id="ea8cc-150">Int32</span></span> | <span data-ttu-id="ea8cc-151">0 – Erfolg.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-151">0-success.</span></span> <br><span data-ttu-id="ea8cc-152">1 – Abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-152">1-cancelled.</span></span> <br><span data-ttu-id="ea8cc-153">7 – Ungültige Parameter.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-153">7-invalid parameters.</span></span> <br><span data-ttu-id="ea8cc-154">8 – Es gibt keine Töne, die den Filterkriterien entsprechen.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-154">8 - no tones match the filter criteria.</span></span> <br><span data-ttu-id="ea8cc-155">255 – Die angegebene Aktion ist nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-155">255 - specified action is not implemented.</span></span> | <span data-ttu-id="ea8cc-156">Das Ergebnis des Auswahlvorgangs.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-156">The result of the picker operation.</span></span> |
| <span data-ttu-id="ea8cc-157">ToneToken</span><span class="sxs-lookup"><span data-stu-id="ea8cc-157">ToneToken</span></span> | <span data-ttu-id="ea8cc-158">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-158">string</span></span> | <span data-ttu-id="ea8cc-159">Das Token des ausgewählten Tons.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-159">The selected tone's token.</span></span> <br><span data-ttu-id="ea8cc-160">Die Zeichenfolge ist leer, wenn der Benutzer in der Auswahl **Standard** auswählt.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-160">The string is empty if the user selects **default** in the picker.</span></span> | <span data-ttu-id="ea8cc-161">Dieses Token kann in einer Popupbenachrichtigungs-Nutzlast verwendet werden oder einem Kontakt als Klingelton oder SMS-Klingelton zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-161">This token can be used in a toast notification payload, or can be assigned as a contact’s ringtone or text tone.</span></span> <span data-ttu-id="ea8cc-162">Der Parameter wird im ValueSet nur zurückgegeben, wenn **Result** 0 ist.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-162">The parameter is returned in the ValueSet only if **Result** is 0.</span></span> |
| <span data-ttu-id="ea8cc-163">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ea8cc-163">DisplayName</span></span> | <span data-ttu-id="ea8cc-164">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-164">string</span></span> | <span data-ttu-id="ea8cc-165">Der Anzeigename des angegebenen Tons.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-165">The specified tone’s friendly name.</span></span> | <span data-ttu-id="ea8cc-166">Eine Zeichenfolge, die dem Benutzer angezeigt werden kann, um den ausgewählten Ton darzustellen.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-166">A string that can be shown to the user to represent the selected tone.</span></span> <span data-ttu-id="ea8cc-167">Der Parameter wird im ValueSet nur zurückgegeben, wenn **Result** 0 ist.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-167">The parameter is returned in the ValueSet only if **Result** is 0.</span></span> |


**<span data-ttu-id="ea8cc-168">Beispiel: Öffnen der Tonauswahl, damit der Benutzer einen Ton auswählen kann</span><span class="sxs-lookup"><span data-stu-id="ea8cc-168">Example: Open the tone picker so that the user can select a tone</span></span>**

``` cs
LauncherOptions options = new LauncherOptions();
options.TargetApplicationPackageFamilyName = "Microsoft.Tonepicker_8wekyb3d8bbwe";

ValueSet inputData = new ValueSet() {
    { "Action", "PickRingtone" },
    { "TypeFilter", "Ringtones" } // Show only ringtones
};

LaunchUriResult result = await Launcher.LaunchUriForResultsAsync(new Uri("ms-tonepicker:"), options, inputData);

if (result.Status == LaunchUriStatus.Success)
{
     Int32 resultCode =  (Int32)result.Result["Result"];
     if (resultCode == 0)
     {
         string token = result.Result["ToneToken"] as string;
         string name = result.Result["DisplayName"] as string;
     }
     else
     {
           // handle failure
     }
}
```

## <a name="task-display-the-tone-saver"></a><span data-ttu-id="ea8cc-169">Aufgabe: Anzeige des Tools für das Speichern von Tönen</span><span class="sxs-lookup"><span data-stu-id="ea8cc-169">Task: Display the tone saver</span></span>

<span data-ttu-id="ea8cc-170">Die Argumente, die Sie zum Anzeigen des Tools für das Speichern von Tönen übergeben können, sind:</span><span class="sxs-lookup"><span data-stu-id="ea8cc-170">The arguments you can pass to display the tone saver are as follows:</span></span>

| <span data-ttu-id="ea8cc-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="ea8cc-171">Parameter</span></span> | <span data-ttu-id="ea8cc-172">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8cc-172">Type</span></span> | <span data-ttu-id="ea8cc-173">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ea8cc-173">Required</span></span> | <span data-ttu-id="ea8cc-174">Mögliche Werte</span><span class="sxs-lookup"><span data-stu-id="ea8cc-174">Possible values</span></span> | <span data-ttu-id="ea8cc-175">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8cc-175">Description</span></span> |
|-----------|------|----------|-------|-------------|
| <span data-ttu-id="ea8cc-176">Action</span><span class="sxs-lookup"><span data-stu-id="ea8cc-176">Action</span></span> | <span data-ttu-id="ea8cc-177">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-177">string</span></span> | <span data-ttu-id="ea8cc-178">Ja</span><span class="sxs-lookup"><span data-stu-id="ea8cc-178">yes</span></span> | <span data-ttu-id="ea8cc-179">"SaveRingtone"</span><span class="sxs-lookup"><span data-stu-id="ea8cc-179">"SaveRingtone"</span></span> | <span data-ttu-id="ea8cc-180">Öffnet die Auswahl, um einen Klingelton zu speichern.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-180">Opens the picker to save a ringtone.</span></span> |
| <span data-ttu-id="ea8cc-181">ToneFileSharingToken</span><span class="sxs-lookup"><span data-stu-id="ea8cc-181">ToneFileSharingToken</span></span> | <span data-ttu-id="ea8cc-182">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-182">string</span></span> | <span data-ttu-id="ea8cc-183">Ja</span><span class="sxs-lookup"><span data-stu-id="ea8cc-183">yes</span></span> | <span data-ttu-id="ea8cc-184">[SharedStorageAccessManager](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.aspx)-Dateifreigabetoken für die Klingeltondatei, die gespeichert werden soll.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-184">[SharedStorageAccessManager](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.aspx) file sharing token for the ringtone file to save.</span></span> | <span data-ttu-id="ea8cc-185">Speichert eine bestimmte Audiodatei als Klingelton.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-185">Saves a specific sound file as a ringtone.</span></span> <span data-ttu-id="ea8cc-186">Die unterstützten Inhaltstypen für die Datei sind „mpeg audio“ und „x-ms-wma audio“.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-186">The supported content types for the file are mpeg audio and x-ms-wma audio.</span></span> |
| <span data-ttu-id="ea8cc-187">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ea8cc-187">DisplayName</span></span> | <span data-ttu-id="ea8cc-188">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-188">string</span></span> | <span data-ttu-id="ea8cc-189">Nein</span><span class="sxs-lookup"><span data-stu-id="ea8cc-189">no</span></span> | <span data-ttu-id="ea8cc-190">Der Anzeigename des angegebenen Tons.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-190">The specified tone’s friendly name.</span></span> | <span data-ttu-id="ea8cc-191">Legt den Anzeigenamen fest, der beim Speichern des angegebenen Klingeltons verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-191">Sets the display name to use when saving the specified ringtone.</span></span> |

<span data-ttu-id="ea8cc-192">Die Werte, die in [LaunchUriResults.Result](https://msdn.microsoft.com/library/windows/apps/windows.system.launchuriresult.result.aspx) zurückgegeben werden:</span><span class="sxs-lookup"><span data-stu-id="ea8cc-192">The values that are returned in [LaunchUriResults.Result](https://msdn.microsoft.com/library/windows/apps/windows.system.launchuriresult.result.aspx):</span></span>

| <span data-ttu-id="ea8cc-193">Rückgabewerte</span><span class="sxs-lookup"><span data-stu-id="ea8cc-193">Return values</span></span> | <span data-ttu-id="ea8cc-194">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8cc-194">Type</span></span> | <span data-ttu-id="ea8cc-195">Mögliche Werte</span><span class="sxs-lookup"><span data-stu-id="ea8cc-195">Possible values</span></span> | <span data-ttu-id="ea8cc-196">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8cc-196">Description</span></span> |
|--------------|------|-------|-------------|
| <span data-ttu-id="ea8cc-197">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="ea8cc-197">Result</span></span> | <span data-ttu-id="ea8cc-198">Int32</span><span class="sxs-lookup"><span data-stu-id="ea8cc-198">Int32</span></span> | <span data-ttu-id="ea8cc-199">0 – Erfolg.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-199">0-success.</span></span><br><span data-ttu-id="ea8cc-200">1 – Vom Benutzer abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-200">1-cancelled by user.</span></span><br><span data-ttu-id="ea8cc-201">2 – Ungültige Datei.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-201">2-Invalid file.</span></span><br><span data-ttu-id="ea8cc-202">3 – Ungültiger Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-202">3-Invalid file content type.</span></span><br><span data-ttu-id="ea8cc-203">4 – Datei überschreitet die maximal zulässige Größe für Klingeltöne (1MB in Windows10).</span><span class="sxs-lookup"><span data-stu-id="ea8cc-203">4-file exceeds maximum ringtone size (1MB in Windows 10).</span></span><br><span data-ttu-id="ea8cc-204">5 – Datei überschreitet die Begrenzung auf 40Sekunden.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-204">5-File exceeds 40 second length limit.</span></span><br><span data-ttu-id="ea8cc-205">6 – Datei wird durch Digital Rights Management geschützt.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-205">6-File is protected by digital rights management.</span></span><br><span data-ttu-id="ea8cc-206">7 – Ungültige Parameter.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-206">7-invalid  parameters.</span></span> | <span data-ttu-id="ea8cc-207">Das Ergebnis des Auswahlvorgangs.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-207">The result of the picker operation.</span></span> |

**<span data-ttu-id="ea8cc-208">Beispiel: Speichern einer lokalen Musikdatei als Klingelton</span><span class="sxs-lookup"><span data-stu-id="ea8cc-208">Example: Save a local music file as a ringtone</span></span>**

``` cs
LauncherOptions options = new LauncherOptions();
options.TargetApplicationPackageFamilyName = "Microsoft.Tonepicker_8wekyb3d8bbwe";

ValueSet inputData = new ValueSet() {
    { "Action", "SaveRingtone" },
    { "ToneFileSharingToken", SharedStorageAccessManager.AddFile(myLocalFile) }
};

LaunchUriResult result = await Launcher.LaunchUriForResultsAsync(new Uri("ms-tonepicker:"), options, inputData);

if (result.Status == LaunchUriStatus.Success)
{
     Int32 resultCode = (Int32)result.Result["Result"];

     if (resultCode == 0)
     {
         // no issues
     }
     else
     {
          switch (resultCode)
          {
             case 2:
              // The specified file was invalid
              break;
              case 3:
              // The specified file's content type is invalid
              break;
              case 4:
              // The specified file was too big
              break;
              case 5:
              // The specified file was too long
              break;
              case 6:
              // The file was protected by DRM
              break;
              case 7:
              // The specified parameter was incorrect
              break;
          }
      }
 }
```

## <a name="task-convert-a-tone-token-to-its-friendly-name"></a><span data-ttu-id="ea8cc-209">Aufgabe: Konvertieren eines Tontokens in dessen Anzeigenamen</span><span class="sxs-lookup"><span data-stu-id="ea8cc-209">Task: Convert a tone token to its friendly name</span></span>

<span data-ttu-id="ea8cc-210">Die Argumente, die Sie zum Abrufen des Anzeigenamens eines Tons übergeben können, sind:</span><span class="sxs-lookup"><span data-stu-id="ea8cc-210">The arguments you can pass to get the friendly name of a tone are as follows:</span></span>

| <span data-ttu-id="ea8cc-211">Parameter</span><span class="sxs-lookup"><span data-stu-id="ea8cc-211">Parameter</span></span> | <span data-ttu-id="ea8cc-212">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8cc-212">Type</span></span> | <span data-ttu-id="ea8cc-213">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ea8cc-213">Required</span></span> | <span data-ttu-id="ea8cc-214">Mögliche Werte</span><span class="sxs-lookup"><span data-stu-id="ea8cc-214">Possible values</span></span> | <span data-ttu-id="ea8cc-215">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8cc-215">Description</span></span> |
|-----------|------|----------|-------|-------------|
| <span data-ttu-id="ea8cc-216">Action</span><span class="sxs-lookup"><span data-stu-id="ea8cc-216">Action</span></span> | <span data-ttu-id="ea8cc-217">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-217">string</span></span> | <span data-ttu-id="ea8cc-218">Ja</span><span class="sxs-lookup"><span data-stu-id="ea8cc-218">yes</span></span> | <span data-ttu-id="ea8cc-219">"GetToneName"</span><span class="sxs-lookup"><span data-stu-id="ea8cc-219">"GetToneName"</span></span> | <span data-ttu-id="ea8cc-220">Gibt an, dass Sie den Anzeigenamen eines Tons abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-220">Indicates that you want to get the friendly name of a tone.</span></span> |
| <span data-ttu-id="ea8cc-221">ToneToken</span><span class="sxs-lookup"><span data-stu-id="ea8cc-221">ToneToken</span></span> | <span data-ttu-id="ea8cc-222">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-222">string</span></span> | <span data-ttu-id="ea8cc-223">Ja</span><span class="sxs-lookup"><span data-stu-id="ea8cc-223">yes</span></span> | <span data-ttu-id="ea8cc-224">Das Tontoken.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-224">The tone token</span></span> | <span data-ttu-id="ea8cc-225">Das Tontoken, aus dem ein Anzeigename abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-225">The tone token from which to obtain a display name.</span></span> |

<span data-ttu-id="ea8cc-226">Die Werte, die in [LaunchUriResults.Result](https://msdn.microsoft.com/library/windows/apps/windows.system.launchuriresult.result.aspx) zurückgegeben werden:</span><span class="sxs-lookup"><span data-stu-id="ea8cc-226">The values that are returned in [LaunchUriResults.Result](https://msdn.microsoft.com/library/windows/apps/windows.system.launchuriresult.result.aspx):</span></span>

| <span data-ttu-id="ea8cc-227">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ea8cc-227">Return value</span></span> | <span data-ttu-id="ea8cc-228">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8cc-228">Type</span></span> | <span data-ttu-id="ea8cc-229">Mögliche Werte</span><span class="sxs-lookup"><span data-stu-id="ea8cc-229">Possible values</span></span> | <span data-ttu-id="ea8cc-230">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8cc-230">Description</span></span> |
|--------------|------|-------|-------------|
| <span data-ttu-id="ea8cc-231">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="ea8cc-231">Result</span></span> | <span data-ttu-id="ea8cc-232">Int32</span><span class="sxs-lookup"><span data-stu-id="ea8cc-232">Int32</span></span> | <span data-ttu-id="ea8cc-233">0 – Der Auswahlvorgang war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-233">0-The picker operation succeeded.</span></span><br><span data-ttu-id="ea8cc-234">7 – Falscher Parameter (wenn beispielsweise kein Tontoken angegeben wurde).</span><span class="sxs-lookup"><span data-stu-id="ea8cc-234">7-Incorrect parameter (for example, no ToneToken provided).</span></span><br><span data-ttu-id="ea8cc-235">9 – Fehler beim Lesen des Namens für das angegebene Token.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-235">9-Error reading the name for the specified token.</span></span><br><span data-ttu-id="ea8cc-236">10 – Das angegebene Tontoken kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-236">10-Unable to find specified tone token.</span></span> | <span data-ttu-id="ea8cc-237">Das Ergebnis des Auswahlvorgangs.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-237">The result of the picker operation.</span></span>
| <span data-ttu-id="ea8cc-238">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ea8cc-238">DisplayName</span></span> | <span data-ttu-id="ea8cc-239">string</span><span class="sxs-lookup"><span data-stu-id="ea8cc-239">string</span></span> | <span data-ttu-id="ea8cc-240">Der Anzeigename des Tons.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-240">The tone's friendly name.</span></span> | <span data-ttu-id="ea8cc-241">Gibt den Anzeigenamen des ausgewählten Tons zurück.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-241">Returns the selected tone's display name.</span></span> <span data-ttu-id="ea8cc-242">Dieser Parameter wird im ValueSet nur zurückgegeben, wenn **Result** 0 ist.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-242">This parameter is only returned in the ValueSet if **Result** is 0.</span></span> |

**<span data-ttu-id="ea8cc-243">Beispiel: Abrufen eines Tontokens aus Contact.RingToneToken und Anzeigen des Anzeigenamens auf der Kontaktkarte.</span><span class="sxs-lookup"><span data-stu-id="ea8cc-243">Example: Retrieve a tone token from Contact.RingToneToken and display its friendly name in the contact card.</span></span>**

```cs
using (var connection = new AppServiceConnection())
{
    connection.AppServiceName = "ms-tonepicker-nameprovider";
    connection.PackageFamilyName = "Microsoft.Tonepicker_8wekyb3d8bbwe";
    AppServiceConnectionStatus connectionStatus = await connection.OpenAsync();
    if (connectionStatus == AppServiceConnectionStatus.Success)
    {
        var message = new ValueSet() {
            { "Action", "GetToneName" },
            { "ToneToken", token)
        };
        AppServiceResponse response = await connection.SendMessageAsync(message);
        if (response.Status == AppServiceResponseStatus.Success)
        {
            Int32 resultCode = (Int32)response.Message["Result"];
            if (resultCode == 0)
            {
                string name = response.Message["DisplayName"] as string;
            }
            else
            {
                // handle failure
            }
        }
        else
        {
            // handle failure
        }
    }
}
```
