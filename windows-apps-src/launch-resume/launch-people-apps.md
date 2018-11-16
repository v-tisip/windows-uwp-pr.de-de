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
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6980753"
---
# <a name="launch-the-people-app"></a><span data-ttu-id="dad23-105">Starten der Kontakte-App</span><span class="sxs-lookup"><span data-stu-id="dad23-105">Launch the People app</span></span>

<span data-ttu-id="dad23-106">In diesem Thema wird das **ms-people:**-URI-Schema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="dad23-106">This topic describes the **ms-people:** URI scheme.</span></span> <span data-ttu-id="dad23-107">Ihre App kann dieses URI-Schema verwenden, um die Kontakte-App für bestimmte Aktionen zu starten.</span><span class="sxs-lookup"><span data-stu-id="dad23-107">Your app can use this URI scheme to launch the People app for specific actions.</span></span>

## <a name="ms-people-uri-scheme-reference"></a><span data-ttu-id="dad23-108">ms-people: URI-Schemaverweis</span><span class="sxs-lookup"><span data-stu-id="dad23-108">ms-people: URI scheme reference</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dad23-109">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="dad23-109">Results</span></span></th>
<th align="left"><span data-ttu-id="dad23-110">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="dad23-110">URI scheme</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="dad23-111">Damit können andere Apps die Hauptseite der Kontakte-App starten.</span><span class="sxs-lookup"><span data-stu-id="dad23-111">Allows other apps to launch the People app Main page.</span></span></td>
<td align="left"><span data-ttu-id="dad23-112">ms-people:</span><span class="sxs-lookup"><span data-stu-id="dad23-112">ms-people:</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dad23-113">Damit können andere Apps die Einstellungsseite der Kontakte-App starten.</span><span class="sxs-lookup"><span data-stu-id="dad23-113">Allows other apps to launch the People app Settings page.</span></span></td>
<td align="left"><span data-ttu-id="dad23-114">ms-people:settings</span><span class="sxs-lookup"><span data-stu-id="dad23-114">ms-people:settings</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dad23-115">Damit können andere Apps einen Suchbegriff bereitstellen, der in der Kontakte-App mit der Ergebnisseite der Suche gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="dad23-115">Allows other apps to provide a search string that will launch the People app with the result page of the search.</span></span>
<div class="alert">
<p><span data-ttu-id="dad23-116">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="dad23-116">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="dad23-117">Wenn Sie die Syntax nicht ordnungsgemäß eingeben oder den Wert der Suchzeichenfolge vergessen, wird standardmäßig eine vollständige Liste der Kontakte ohne Filterung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="dad23-117">If you do not enter the syntax correctly, or are missing the search string value, the default behavior is to return a full list of contacts without any filtering.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="dad23-118">ms-people:search?SearchString=&lt;contactsearchinfo&gt;</span><span class="sxs-lookup"><span data-stu-id="dad23-118">ms-people:search?SearchString=&lt;contactsearchinfo&gt;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dad23-119">Startet mit einer vorhandenen Kontaktkarte, wenn der Kontakt gefunden wurde.</span><span class="sxs-lookup"><span data-stu-id="dad23-119">Launches to an existing contact card, if the contact is found.</span></span> <span data-ttu-id="dad23-120">Oder startet mit einer temporären Kontaktkarte, wenn kein Kontakt gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="dad23-120">Or, launches to a temporary contact card, if no contact is found.</span></span> <span data-ttu-id="dad23-121">Wenn kein Eingabeparameter angegeben wird, wird die Kontakte-App mit einer Kontaktliste gestartet.</span><span class="sxs-lookup"><span data-stu-id="dad23-121">If no input parameter is supplied, we will launch the People App with a contact list.</span></span>
<div class="alert">
<p><span data-ttu-id="dad23-122">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="dad23-122">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="dad23-123">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="dad23-123">The order of the parameters doesn’t matter.</span></span></p>
<p><span data-ttu-id="dad23-124">Wenn mehr als eine Übereinstimmung vorliegt, wird die erste Übereinstimmung des Kontakts zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="dad23-124">If there is more than one match, we will return the first match of the contact.</span></span></p>
</div>
<div> 
</div></td>
<td align="left"><span data-ttu-id="dad23-125">ms-people:viewcontact:?ContactId=&lt;contactid&gt;&amp;AggregatedId=&lt;aggid&gt;&amp;PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;&amp;Contact=&lt;contactobj&gt;</span><span class="sxs-lookup"><span data-stu-id="dad23-125">ms-people:viewcontact:?ContactId=&lt;contactid&gt;&amp;AggregatedId=&lt;aggid&gt;&amp;PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;&amp;Contact=&lt;contactobj&gt;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dad23-126">Startet mit einer „Kontakt speichern“-Seite innerhalb der Kontakte-App, um den angegeben Kontakt mit der angegebenen Telefonnummer oder E-Mail-Adresse zu speichern.</span><span class="sxs-lookup"><span data-stu-id="dad23-126">Launches to a Save-contact page within the People app to save the given contact with the supplied phone number or email address.</span></span>
<div class="alert">
<p><span data-ttu-id="dad23-127">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="dad23-127">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="dad23-128">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="dad23-128">The order of the parameters doesn’t matter.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="dad23-129">ms-people:savetocontact?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span><span class="sxs-lookup"><span data-stu-id="dad23-129">ms-people:savetocontact?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dad23-130">Startet mit der Seite „Neuen Kontakt hinzufügen“ innerhalb der Kontakte-App, um den angegeben Kontakt zu speichern.</span><span class="sxs-lookup"><span data-stu-id="dad23-130">Launches to the add a new contact page within the People app to save the given contact.</span></span>
<div class="alert"><p><span data-ttu-id="dad23-131">Verwenden Sie <a href="https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_">LaunchUriForResultsAsync</a>, um die Seite „Neuen Kontakt speichern“ zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="dad23-131">Use <a href="https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_">LaunchUriForResultsAsync</a> to open the save new contact page.</span></span> <span data-ttu-id="dad23-132">Mit <strong>LaunchUriAsync</strong> wird nur die Hauptseite der Kontakte-App gestartet.</span><span class="sxs-lookup"><span data-stu-id="dad23-132">Using <strong>LaunchUriAsync</strong> will only launch the People app Main page.</span></span></p>
<p><span data-ttu-id="dad23-133">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="dad23-133">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="dad23-134">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="dad23-134">The order of the parameters doesn’t matter.</span></span></p>
<p><span data-ttu-id="dad23-135">Die unterstützten Parametern können in beliebiger Kombination verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="dad23-135">You can use any combination of supported parameters.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="dad23-136">ms-people:savecontacttask?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span><span class="sxs-lookup"><span data-stu-id="dad23-136">ms-people:savecontacttask?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span></span></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesearch-parameter-reference"></a><span data-ttu-id="dad23-137">ms-people:search: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="dad23-137">ms-people:search: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dad23-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="dad23-138">Parameter</span></span></th>
<th align="left"><span data-ttu-id="dad23-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dad23-139">Description</span></span></th>
<th align="left"><span data-ttu-id="dad23-140">Beispiel</span><span class="sxs-lookup"><span data-stu-id="dad23-140">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-141">Suchzeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dad23-141">SearchString</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-142">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-142">Optional.</span></span></p>
<p><span data-ttu-id="dad23-143">Die Suchzeichenfolge für die Informationen zur Kontaktsuche.</span><span class="sxs-lookup"><span data-stu-id="dad23-143">The search string for the contact search information.</span></span></p>
<p><span data-ttu-id="dad23-144">Die Telefonnummer oder den Namen des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-144">The phone number or the contact name.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-145">ms-people:search?SearchString=Smith</span><span class="sxs-lookup"><span data-stu-id="dad23-145">ms-people:search?SearchString=Smith</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peopleviewcontact-parameter-reference"></a><span data-ttu-id="dad23-146">ms-people:viewcontact: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="dad23-146">ms-people:viewcontact: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dad23-147">Parameter</span><span class="sxs-lookup"><span data-stu-id="dad23-147">Parameter</span></span></th>
<th align="left"><span data-ttu-id="dad23-148">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dad23-148">Description</span></span></th>
<th align="left"><span data-ttu-id="dad23-149">Beispiel</span><span class="sxs-lookup"><span data-stu-id="dad23-149">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-150">ContactId</span><span class="sxs-lookup"><span data-stu-id="dad23-150">ContactId</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-151">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-151">Optional.</span></span></p>
<p><span data-ttu-id="dad23-152">Die Kontakt-ID des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-152">Contact Id of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-153">ms-people:viewcontact?ContactId={ContactId}</span><span class="sxs-lookup"><span data-stu-id="dad23-153">ms-people:viewcontact?ContactId={ContactId}</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-154">PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="dad23-154">PhoneNumber</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-155">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-155">Optional.</span></span></p>
<p><span data-ttu-id="dad23-156">Die Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-156">Phone number of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-157">ms-people:viewcontact?PhoneNumber=%2014257069326</span><span class="sxs-lookup"><span data-stu-id="dad23-157">ms-people:viewcontact?PhoneNumber=%2014257069326</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-158">Email</span><span class="sxs-lookup"><span data-stu-id="dad23-158">Email</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-159">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-159">Optional.</span></span></p>
<p><span data-ttu-id="dad23-160">Die E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-160">Email of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-161">ms-people:viewcontact?Email=johnsmith@contsco.com</span><span class="sxs-lookup"><span data-stu-id="dad23-161">ms-people:viewcontact?Email=johnsmith@contsco.com</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-162">ContactName</span><span class="sxs-lookup"><span data-stu-id="dad23-162">ContactName</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-163">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-163">Optional.</span></span></p>
<p><span data-ttu-id="dad23-164">Der Name des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-164">Name of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-165">ms-people:viewcontact?ContactName=John%20%Smith</span><span class="sxs-lookup"><span data-stu-id="dad23-165">ms-people:viewcontact?ContactName=John%20%Smith</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-166">Contact</span><span class="sxs-lookup"><span data-stu-id="dad23-166">Contact</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-167">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-167">Optional.</span></span></p>
<p><span data-ttu-id="dad23-168">Das Kontaktobjekt.</span><span class="sxs-lookup"><span data-stu-id="dad23-168">Contact object.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-169">ms-people:viewcontact?Contact={Serialized Contact}</span><span class="sxs-lookup"><span data-stu-id="dad23-169">ms-people:viewcontact?Contact={Serialized Contact}</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesavetocontact-parameter-reference"></a><span data-ttu-id="dad23-170">ms-people:savetocontact: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="dad23-170">ms-people:savetocontact: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dad23-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="dad23-171">Parameter</span></span></th>
<th align="left"><span data-ttu-id="dad23-172">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dad23-172">Description</span></span></th>
<th align="left"><span data-ttu-id="dad23-173">Beispiel</span><span class="sxs-lookup"><span data-stu-id="dad23-173">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-174">PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="dad23-174">PhoneNumber</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-175">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-175">Optional.</span></span></p>
<p><span data-ttu-id="dad23-176">Die Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-176">Phone number of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-177">ms-people:savetocontact?PhoneNumber=%2014257069326</span><span class="sxs-lookup"><span data-stu-id="dad23-177">ms-people:savetocontact?PhoneNumber=%2014257069326</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-178">Email</span><span class="sxs-lookup"><span data-stu-id="dad23-178">Email</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-179">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-179">Optional.</span></span></p>
<p><span data-ttu-id="dad23-180">Die E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-180">Email of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-181">ms-people:savetocontact?Email=johnsmith@contsco.com</span><span class="sxs-lookup"><span data-stu-id="dad23-181">ms-people:savetocontact?Email=johnsmith@contsco.com</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-182">ContactName</span><span class="sxs-lookup"><span data-stu-id="dad23-182">ContactName</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-183">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-183">Optional.</span></span></p>
<p><span data-ttu-id="dad23-184">Der Name des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-184">Name of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="dad23-185">ms-people:savetocontact?Email=johnsmith@contsco.com&amp;ContactName= John%20%Smith</span><span class="sxs-lookup"><span data-stu-id="dad23-185">ms-people:savetocontact?Email=johnsmith@contsco.com&amp;ContactName= John%20%Smith</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesavecontacttask-parameter-reference"></a><span data-ttu-id="dad23-186">ms-people:savecontacttask: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="dad23-186">ms-people:savecontacttask: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dad23-187">Parameter</span><span class="sxs-lookup"><span data-stu-id="dad23-187">Parameter</span></span></th>
<th align="left"><span data-ttu-id="dad23-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dad23-188">Description</span></span></th>

</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-189">Firma</span><span class="sxs-lookup"><span data-stu-id="dad23-189">Company</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-190">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-190">Optional.</span></span></p>
<p><span data-ttu-id="dad23-191">Firmenname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-191">Company name of the contact.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-192">Vorname</span><span class="sxs-lookup"><span data-stu-id="dad23-192">FirstName</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-193">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-193">Optional.</span></span></p>
<p><span data-ttu-id="dad23-194">Vorname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-194">First name of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-195">HomeAddressCity</span><span class="sxs-lookup"><span data-stu-id="dad23-195">HomeAddressCity</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-196">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-196">Optional.</span></span></p>
<p><span data-ttu-id="dad23-197">Ort der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="dad23-197">City of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-198">HomeAddressCountry</span><span class="sxs-lookup"><span data-stu-id="dad23-198">HomeAddressCountry</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-199">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-199">Optional.</span></span></p>
<p><span data-ttu-id="dad23-200">Land der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="dad23-200">Country of the home address.</span></span></p></td>

</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-201">HomeAddressState</span><span class="sxs-lookup"><span data-stu-id="dad23-201">HomeAddressState</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-202">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-202">Optional.</span></span></p>
<p><span data-ttu-id="dad23-203">Bundesland der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="dad23-203">State of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-204">HomeAddressStreet</span><span class="sxs-lookup"><span data-stu-id="dad23-204">HomeAddressStreet</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-205">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-205">Optional.</span></span></p>
<p><span data-ttu-id="dad23-206">Straße der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="dad23-206">Street of the home address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-207">HomeAddressZipCode</span><span class="sxs-lookup"><span data-stu-id="dad23-207">HomeAddressZipCode</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-208">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-208">Optional.</span></span></p>
<p><span data-ttu-id="dad23-209">Postleitzahl der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="dad23-209">Zip Code of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-210">HomePhone</span><span class="sxs-lookup"><span data-stu-id="dad23-210">HomePhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-211">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-211">Optional.</span></span></p>
<p><span data-ttu-id="dad23-212">Private Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-212">Home phone of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-213">JobTitle</span><span class="sxs-lookup"><span data-stu-id="dad23-213">JobTitle</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-214">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-214">Optional.</span></span></p>
<p><span data-ttu-id="dad23-215">Berufsbezeichnung des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-215">Job title of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-216">LastName</span><span class="sxs-lookup"><span data-stu-id="dad23-216">LastName</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-217">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-217">Optional.</span></span></p>
<p><span data-ttu-id="dad23-218">Nachname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-218">Last name of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-219">MiddleName</span><span class="sxs-lookup"><span data-stu-id="dad23-219">MiddleName</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-220">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-220">Optional.</span></span></p>
<p><span data-ttu-id="dad23-221">Zweiter Vorname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-221">Middle name of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-222">MobilePhone</span><span class="sxs-lookup"><span data-stu-id="dad23-222">MobilePhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-223">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-223">Optional.</span></span></p>
<p><span data-ttu-id="dad23-224">Mobiltelefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-224">Mobile phone number of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-225">Spitzname</span><span class="sxs-lookup"><span data-stu-id="dad23-225">Nickname</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-226">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-226">Optional.</span></span></p>
<p><span data-ttu-id="dad23-227">Spitzname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-227">Nickname of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-228">Notizen</span><span class="sxs-lookup"><span data-stu-id="dad23-228">Notes</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-229">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-229">Optional.</span></span></p>
<p><span data-ttu-id="dad23-230">Notizen zum Kontakt.</span><span class="sxs-lookup"><span data-stu-id="dad23-230">Notes about the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-231">OtherEmail</span><span class="sxs-lookup"><span data-stu-id="dad23-231">OtherEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-232">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-232">Optional.</span></span></p>
<p><span data-ttu-id="dad23-233">Weitere E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-233">Other Email of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-234">PersonalEmail</span><span class="sxs-lookup"><span data-stu-id="dad23-234">PersonalEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-235">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-235">Optional.</span></span></p>
<p><span data-ttu-id="dad23-236">Private E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-236">Personal Email of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-237">Suffix</span><span class="sxs-lookup"><span data-stu-id="dad23-237">Suffix</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-238">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-238">Optional.</span></span></p>
<p><span data-ttu-id="dad23-239">Suffix des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-239">Suffix of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-240">Title</span><span class="sxs-lookup"><span data-stu-id="dad23-240">Title</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-241">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-241">Optional.</span></span></p>
<p><span data-ttu-id="dad23-242">Anrede des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-242">Title of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-243">Webseite</span><span class="sxs-lookup"><span data-stu-id="dad23-243">Website</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-244">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-244">Optional.</span></span></p>
<p><span data-ttu-id="dad23-245">Webseite des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-245">Website of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-246">WorkAddressCity</span><span class="sxs-lookup"><span data-stu-id="dad23-246">WorkAddressCity</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-247">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-247">Optional.</span></span></p>
<p><span data-ttu-id="dad23-248">Ort der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="dad23-248">City of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-249">WorkAddressCountry</span><span class="sxs-lookup"><span data-stu-id="dad23-249">WorkAddressCountry</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-250">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-250">Optional.</span></span></p>
<p><span data-ttu-id="dad23-251">Land der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="dad23-251">Country of the work address.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-252">WorkAddressState</span><span class="sxs-lookup"><span data-stu-id="dad23-252">WorkAddressState</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-253">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-253">Optional.</span></span></p>
<p><span data-ttu-id="dad23-254">Bundesland der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="dad23-254">State of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-255">WorkAddressStreet</span><span class="sxs-lookup"><span data-stu-id="dad23-255">WorkAddressStreet</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-256">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-256">Optional.</span></span></p>
<p><span data-ttu-id="dad23-257">Straße der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="dad23-257">Street of work address.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-258">WorkAddressZipCode</span><span class="sxs-lookup"><span data-stu-id="dad23-258">WorkAddressZipCode</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-259">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-259">Optional.</span></span></p>
<p><span data-ttu-id="dad23-260">Postleitzahl der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="dad23-260">Zip Code of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="dad23-261">WorkEmail</span><span class="sxs-lookup"><span data-stu-id="dad23-261">WorkEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-262">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-262">Optional.</span></span></p>
<p><span data-ttu-id="dad23-263">Geschäftliche E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-263">Work Email of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="dad23-264">WorkPhone</span><span class="sxs-lookup"><span data-stu-id="dad23-264">WorkPhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="dad23-265">Optional.</span><span class="sxs-lookup"><span data-stu-id="dad23-265">Optional.</span></span></p>
<p><span data-ttu-id="dad23-266">Geschäftliche Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="dad23-266">Work phone number of the contact.</span></span></p></td>
</tr>
</tbody>
</table>
