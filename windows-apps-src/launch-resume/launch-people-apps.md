---
author: TylerMSFT
title: Starten der Kontakte-App
description: In diesem Thema wird das URI-Schema „ms-people“ beschrieben. Ihre App kann dieses URI-Schema verwenden, um die Kontakte-App für bestimmte Aktionen zu starten.
ms.assetid: 1E604599-26EF-421C-932F-E9935CDB248E
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 0b87a49f24035215d44dbabcf9e401ddfefdff47
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5833647"
---
# <a name="launch-the-people-app"></a><span data-ttu-id="bbbfe-105">Starten der Kontakte-App</span><span class="sxs-lookup"><span data-stu-id="bbbfe-105">Launch the People app</span></span>

<span data-ttu-id="bbbfe-106">In diesem Thema wird das **ms-people:**-URI-Schema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-106">This topic describes the **ms-people:** URI scheme.</span></span> <span data-ttu-id="bbbfe-107">Ihre App kann dieses URI-Schema verwenden, um die Kontakte-App für bestimmte Aktionen zu starten.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-107">Your app can use this URI scheme to launch the People app for specific actions.</span></span>

## <a name="ms-people-uri-scheme-reference"></a><span data-ttu-id="bbbfe-108">ms-people: URI-Schemaverweis</span><span class="sxs-lookup"><span data-stu-id="bbbfe-108">ms-people: URI scheme reference</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bbbfe-109">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="bbbfe-109">Results</span></span></th>
<th align="left"><span data-ttu-id="bbbfe-110">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="bbbfe-110">URI scheme</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bbbfe-111">Damit können andere Apps die Hauptseite der Kontakte-App starten.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-111">Allows other apps to launch the People app Main page.</span></span></td>
<td align="left"><span data-ttu-id="bbbfe-112">ms-people:</span><span class="sxs-lookup"><span data-stu-id="bbbfe-112">ms-people:</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bbbfe-113">Damit können andere Apps die Einstellungsseite der Kontakte-App starten.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-113">Allows other apps to launch the People app Settings page.</span></span></td>
<td align="left"><span data-ttu-id="bbbfe-114">ms-people:settings</span><span class="sxs-lookup"><span data-stu-id="bbbfe-114">ms-people:settings</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bbbfe-115">Damit können andere Apps einen Suchbegriff bereitstellen, der in der Kontakte-App mit der Ergebnisseite der Suche gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-115">Allows other apps to provide a search string that will launch the People app with the result page of the search.</span></span>
<div class="alert">
<p><span data-ttu-id="bbbfe-116">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-116">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="bbbfe-117">Wenn Sie die Syntax nicht ordnungsgemäß eingeben oder den Wert der Suchzeichenfolge vergessen, wird standardmäßig eine vollständige Liste der Kontakte ohne Filterung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-117">If you do not enter the syntax correctly, or are missing the search string value, the default behavior is to return a full list of contacts without any filtering.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="bbbfe-118">ms-people:search?SearchString=&lt;contactsearchinfo&gt;</span><span class="sxs-lookup"><span data-stu-id="bbbfe-118">ms-people:search?SearchString=&lt;contactsearchinfo&gt;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bbbfe-119">Startet mit einer vorhandenen Kontaktkarte, wenn der Kontakt gefunden wurde.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-119">Launches to an existing contact card, if the contact is found.</span></span> <span data-ttu-id="bbbfe-120">Oder startet mit einer temporären Kontaktkarte, wenn kein Kontakt gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-120">Or, launches to a temporary contact card, if no contact is found.</span></span> <span data-ttu-id="bbbfe-121">Wenn kein Eingabeparameter angegeben wird, wird die Kontakte-App mit einer Kontaktliste gestartet.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-121">If no input parameter is supplied, we will launch the People App with a contact list.</span></span>
<div class="alert">
<p><span data-ttu-id="bbbfe-122">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-122">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="bbbfe-123">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-123">The order of the parameters doesn’t matter.</span></span></p>
<p><span data-ttu-id="bbbfe-124">Wenn mehr als eine Übereinstimmung vorliegt, wird die erste Übereinstimmung des Kontakts zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-124">If there is more than one match, we will return the first match of the contact.</span></span></p>
</div>
<div> 
</div></td>
<td align="left"><span data-ttu-id="bbbfe-125">ms-people:viewcontact:?ContactId=&lt;contactid&gt;&amp;AggregatedId=&lt;aggid&gt;&amp;PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;&amp;Contact=&lt;contactobj&gt;</span><span class="sxs-lookup"><span data-stu-id="bbbfe-125">ms-people:viewcontact:?ContactId=&lt;contactid&gt;&amp;AggregatedId=&lt;aggid&gt;&amp;PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;&amp;Contact=&lt;contactobj&gt;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bbbfe-126">Startet mit einer „Kontakt speichern“-Seite innerhalb der Kontakte-App, um den angegeben Kontakt mit der angegebenen Telefonnummer oder E-Mail-Adresse zu speichern.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-126">Launches to a Save-contact page within the People app to save the given contact with the supplied phone number or email address.</span></span>
<div class="alert">
<p><span data-ttu-id="bbbfe-127">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-127">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="bbbfe-128">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-128">The order of the parameters doesn’t matter.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="bbbfe-129">ms-people:savetocontact?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span><span class="sxs-lookup"><span data-stu-id="bbbfe-129">ms-people:savetocontact?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bbbfe-130">Startet mit der Seite „Neuen Kontakt hinzufügen“ innerhalb der Kontakte-App, um den angegeben Kontakt zu speichern.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-130">Launches to the add a new contact page within the People app to save the given contact.</span></span>
<div class="alert"><p><span data-ttu-id="bbbfe-131">Verwenden Sie <a href="https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_">LaunchUriForResultsAsync</a>, um die Seite „Neuen Kontakt speichern“ zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-131">Use <a href="https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_">LaunchUriForResultsAsync</a> to open the save new contact page.</span></span> <span data-ttu-id="bbbfe-132">Mit <strong>LaunchUriAsync</strong> wird nur die Hauptseite der Kontakte-App gestartet.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-132">Using <strong>LaunchUriAsync</strong> will only launch the People app Main page.</span></span></p>
<p><span data-ttu-id="bbbfe-133">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-133">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="bbbfe-134">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-134">The order of the parameters doesn’t matter.</span></span></p>
<p><span data-ttu-id="bbbfe-135">Die unterstützten Parametern können in beliebiger Kombination verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-135">You can use any combination of supported parameters.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="bbbfe-136">ms-people:savecontacttask?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span><span class="sxs-lookup"><span data-stu-id="bbbfe-136">ms-people:savecontacttask?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span></span></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesearch-parameter-reference"></a><span data-ttu-id="bbbfe-137">ms-people:search: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="bbbfe-137">ms-people:search: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bbbfe-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="bbbfe-138">Parameter</span></span></th>
<th align="left"><span data-ttu-id="bbbfe-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bbbfe-139">Description</span></span></th>
<th align="left"><span data-ttu-id="bbbfe-140">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bbbfe-140">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-141">Suchzeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bbbfe-141">SearchString</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-142">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-142">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-143">Die Suchzeichenfolge für die Informationen zur Kontaktsuche.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-143">The search string for the contact search information.</span></span></p>
<p><span data-ttu-id="bbbfe-144">Die Telefonnummer oder den Namen des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-144">The phone number or the contact name.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-145">ms-people:search?SearchString=Smith</span><span class="sxs-lookup"><span data-stu-id="bbbfe-145">ms-people:search?SearchString=Smith</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peopleviewcontact-parameter-reference"></a><span data-ttu-id="bbbfe-146">ms-people:viewcontact: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="bbbfe-146">ms-people:viewcontact: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bbbfe-147">Parameter</span><span class="sxs-lookup"><span data-stu-id="bbbfe-147">Parameter</span></span></th>
<th align="left"><span data-ttu-id="bbbfe-148">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bbbfe-148">Description</span></span></th>
<th align="left"><span data-ttu-id="bbbfe-149">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bbbfe-149">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-150">ContactId</span><span class="sxs-lookup"><span data-stu-id="bbbfe-150">ContactId</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-151">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-151">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-152">Die Kontakt-ID des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-152">Contact Id of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-153">ms-people:viewcontact?ContactId={ContactId}</span><span class="sxs-lookup"><span data-stu-id="bbbfe-153">ms-people:viewcontact?ContactId={ContactId}</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-154">PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="bbbfe-154">PhoneNumber</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-155">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-155">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-156">Die Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-156">Phone number of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-157">ms-people:viewcontact?PhoneNumber=%2014257069326</span><span class="sxs-lookup"><span data-stu-id="bbbfe-157">ms-people:viewcontact?PhoneNumber=%2014257069326</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-158">Email</span><span class="sxs-lookup"><span data-stu-id="bbbfe-158">Email</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-159">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-159">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-160">Die E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-160">Email of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-161">ms-people:viewcontact?Email=johnsmith@contsco.com</span><span class="sxs-lookup"><span data-stu-id="bbbfe-161">ms-people:viewcontact?Email=johnsmith@contsco.com</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-162">ContactName</span><span class="sxs-lookup"><span data-stu-id="bbbfe-162">ContactName</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-163">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-163">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-164">Der Name des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-164">Name of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-165">ms-people:viewcontact?ContactName=John%20%Smith</span><span class="sxs-lookup"><span data-stu-id="bbbfe-165">ms-people:viewcontact?ContactName=John%20%Smith</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-166">Contact</span><span class="sxs-lookup"><span data-stu-id="bbbfe-166">Contact</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-167">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-167">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-168">Das Kontaktobjekt.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-168">Contact object.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-169">ms-people:viewcontact?Contact={Serialized Contact}</span><span class="sxs-lookup"><span data-stu-id="bbbfe-169">ms-people:viewcontact?Contact={Serialized Contact}</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesavetocontact-parameter-reference"></a><span data-ttu-id="bbbfe-170">ms-people:savetocontact: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="bbbfe-170">ms-people:savetocontact: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bbbfe-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="bbbfe-171">Parameter</span></span></th>
<th align="left"><span data-ttu-id="bbbfe-172">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bbbfe-172">Description</span></span></th>
<th align="left"><span data-ttu-id="bbbfe-173">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bbbfe-173">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-174">PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="bbbfe-174">PhoneNumber</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-175">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-175">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-176">Die Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-176">Phone number of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-177">ms-people:savetocontact?PhoneNumber=%2014257069326</span><span class="sxs-lookup"><span data-stu-id="bbbfe-177">ms-people:savetocontact?PhoneNumber=%2014257069326</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-178">Email</span><span class="sxs-lookup"><span data-stu-id="bbbfe-178">Email</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-179">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-179">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-180">Die E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-180">Email of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-181">ms-people:savetocontact?Email=johnsmith@contsco.com</span><span class="sxs-lookup"><span data-stu-id="bbbfe-181">ms-people:savetocontact?Email=johnsmith@contsco.com</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-182">ContactName</span><span class="sxs-lookup"><span data-stu-id="bbbfe-182">ContactName</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-183">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-183">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-184">Der Name des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-184">Name of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="bbbfe-185">ms-people:savetocontact?Email=johnsmith@contsco.com&amp;ContactName= John%20%Smith</span><span class="sxs-lookup"><span data-stu-id="bbbfe-185">ms-people:savetocontact?Email=johnsmith@contsco.com&amp;ContactName= John%20%Smith</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesavecontacttask-parameter-reference"></a><span data-ttu-id="bbbfe-186">ms-people:savecontacttask: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="bbbfe-186">ms-people:savecontacttask: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bbbfe-187">Parameter</span><span class="sxs-lookup"><span data-stu-id="bbbfe-187">Parameter</span></span></th>
<th align="left"><span data-ttu-id="bbbfe-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bbbfe-188">Description</span></span></th>

</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-189">Firma</span><span class="sxs-lookup"><span data-stu-id="bbbfe-189">Company</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-190">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-190">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-191">Firmenname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-191">Company name of the contact.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-192">Vorname</span><span class="sxs-lookup"><span data-stu-id="bbbfe-192">FirstName</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-193">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-193">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-194">Vorname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-194">First name of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-195">HomeAddressCity</span><span class="sxs-lookup"><span data-stu-id="bbbfe-195">HomeAddressCity</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-196">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-196">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-197">Ort der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-197">City of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-198">HomeAddressCountry</span><span class="sxs-lookup"><span data-stu-id="bbbfe-198">HomeAddressCountry</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-199">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-199">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-200">Land der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-200">Country of the home address.</span></span></p></td>

</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-201">HomeAddressState</span><span class="sxs-lookup"><span data-stu-id="bbbfe-201">HomeAddressState</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-202">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-202">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-203">Bundesland der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-203">State of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-204">HomeAddressStreet</span><span class="sxs-lookup"><span data-stu-id="bbbfe-204">HomeAddressStreet</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-205">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-205">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-206">Straße der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-206">Street of the home address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-207">HomeAddressZipCode</span><span class="sxs-lookup"><span data-stu-id="bbbfe-207">HomeAddressZipCode</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-208">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-208">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-209">Postleitzahl der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-209">Zip Code of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-210">HomePhone</span><span class="sxs-lookup"><span data-stu-id="bbbfe-210">HomePhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-211">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-211">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-212">Private Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-212">Home phone of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-213">JobTitle</span><span class="sxs-lookup"><span data-stu-id="bbbfe-213">JobTitle</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-214">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-214">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-215">Berufsbezeichnung des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-215">Job title of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-216">LastName</span><span class="sxs-lookup"><span data-stu-id="bbbfe-216">LastName</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-217">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-217">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-218">Nachname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-218">Last name of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-219">MiddleName</span><span class="sxs-lookup"><span data-stu-id="bbbfe-219">MiddleName</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-220">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-220">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-221">Zweiter Vorname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-221">Middle name of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-222">MobilePhone</span><span class="sxs-lookup"><span data-stu-id="bbbfe-222">MobilePhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-223">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-223">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-224">Mobiltelefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-224">Mobile phone number of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-225">Spitzname</span><span class="sxs-lookup"><span data-stu-id="bbbfe-225">Nickname</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-226">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-226">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-227">Spitzname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-227">Nickname of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-228">Notizen</span><span class="sxs-lookup"><span data-stu-id="bbbfe-228">Notes</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-229">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-229">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-230">Notizen zum Kontakt.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-230">Notes about the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-231">OtherEmail</span><span class="sxs-lookup"><span data-stu-id="bbbfe-231">OtherEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-232">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-232">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-233">Weitere E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-233">Other Email of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-234">PersonalEmail</span><span class="sxs-lookup"><span data-stu-id="bbbfe-234">PersonalEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-235">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-235">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-236">Private E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-236">Personal Email of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-237">Suffix</span><span class="sxs-lookup"><span data-stu-id="bbbfe-237">Suffix</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-238">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-238">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-239">Suffix des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-239">Suffix of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-240">Title</span><span class="sxs-lookup"><span data-stu-id="bbbfe-240">Title</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-241">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-241">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-242">Anrede des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-242">Title of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-243">Webseite</span><span class="sxs-lookup"><span data-stu-id="bbbfe-243">Website</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-244">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-244">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-245">Webseite des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-245">Website of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-246">WorkAddressCity</span><span class="sxs-lookup"><span data-stu-id="bbbfe-246">WorkAddressCity</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-247">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-247">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-248">Ort der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-248">City of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-249">WorkAddressCountry</span><span class="sxs-lookup"><span data-stu-id="bbbfe-249">WorkAddressCountry</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-250">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-250">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-251">Land der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-251">Country of the work address.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-252">WorkAddressState</span><span class="sxs-lookup"><span data-stu-id="bbbfe-252">WorkAddressState</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-253">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-253">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-254">Bundesland der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-254">State of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-255">WorkAddressStreet</span><span class="sxs-lookup"><span data-stu-id="bbbfe-255">WorkAddressStreet</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-256">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-256">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-257">Straße der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-257">Street of work address.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-258">WorkAddressZipCode</span><span class="sxs-lookup"><span data-stu-id="bbbfe-258">WorkAddressZipCode</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-259">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-259">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-260">Postleitzahl der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-260">Zip Code of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="bbbfe-261">WorkEmail</span><span class="sxs-lookup"><span data-stu-id="bbbfe-261">WorkEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-262">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-262">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-263">Geschäftliche E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-263">Work Email of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="bbbfe-264">WorkPhone</span><span class="sxs-lookup"><span data-stu-id="bbbfe-264">WorkPhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="bbbfe-265">Optional.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-265">Optional.</span></span></p>
<p><span data-ttu-id="bbbfe-266">Geschäftliche Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="bbbfe-266">Work phone number of the contact.</span></span></p></td>
</tr>
</tbody>
</table>
