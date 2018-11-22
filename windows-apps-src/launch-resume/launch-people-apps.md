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
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7569110"
---
# <a name="launch-the-people-app"></a><span data-ttu-id="2b3b8-105">Starten der Kontakte-App</span><span class="sxs-lookup"><span data-stu-id="2b3b8-105">Launch the People app</span></span>

<span data-ttu-id="2b3b8-106">In diesem Thema wird das **ms-people:**-URI-Schema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-106">This topic describes the **ms-people:** URI scheme.</span></span> <span data-ttu-id="2b3b8-107">Ihre App kann dieses URI-Schema verwenden, um die Kontakte-App für bestimmte Aktionen zu starten.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-107">Your app can use this URI scheme to launch the People app for specific actions.</span></span>

## <a name="ms-people-uri-scheme-reference"></a><span data-ttu-id="2b3b8-108">ms-people: URI-Schemaverweis</span><span class="sxs-lookup"><span data-stu-id="2b3b8-108">ms-people: URI scheme reference</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2b3b8-109">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="2b3b8-109">Results</span></span></th>
<th align="left"><span data-ttu-id="2b3b8-110">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="2b3b8-110">URI scheme</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2b3b8-111">Damit können andere Apps die Hauptseite der Kontakte-App starten.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-111">Allows other apps to launch the People app Main page.</span></span></td>
<td align="left"><span data-ttu-id="2b3b8-112">ms-people:</span><span class="sxs-lookup"><span data-stu-id="2b3b8-112">ms-people:</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2b3b8-113">Damit können andere Apps die Einstellungsseite der Kontakte-App starten.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-113">Allows other apps to launch the People app Settings page.</span></span></td>
<td align="left"><span data-ttu-id="2b3b8-114">ms-people:settings</span><span class="sxs-lookup"><span data-stu-id="2b3b8-114">ms-people:settings</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2b3b8-115">Damit können andere Apps einen Suchbegriff bereitstellen, der in der Kontakte-App mit der Ergebnisseite der Suche gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-115">Allows other apps to provide a search string that will launch the People app with the result page of the search.</span></span>
<div class="alert">
<p><span data-ttu-id="2b3b8-116">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-116">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="2b3b8-117">Wenn Sie die Syntax nicht ordnungsgemäß eingeben oder den Wert der Suchzeichenfolge vergessen, wird standardmäßig eine vollständige Liste der Kontakte ohne Filterung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-117">If you do not enter the syntax correctly, or are missing the search string value, the default behavior is to return a full list of contacts without any filtering.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="2b3b8-118">ms-people:search?SearchString=&lt;contactsearchinfo&gt;</span><span class="sxs-lookup"><span data-stu-id="2b3b8-118">ms-people:search?SearchString=&lt;contactsearchinfo&gt;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2b3b8-119">Startet mit einer vorhandenen Kontaktkarte, wenn der Kontakt gefunden wurde.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-119">Launches to an existing contact card, if the contact is found.</span></span> <span data-ttu-id="2b3b8-120">Oder startet mit einer temporären Kontaktkarte, wenn kein Kontakt gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-120">Or, launches to a temporary contact card, if no contact is found.</span></span> <span data-ttu-id="2b3b8-121">Wenn kein Eingabeparameter angegeben wird, wird die Kontakte-App mit einer Kontaktliste gestartet.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-121">If no input parameter is supplied, we will launch the People App with a contact list.</span></span>
<div class="alert">
<p><span data-ttu-id="2b3b8-122">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-122">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="2b3b8-123">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-123">The order of the parameters doesn’t matter.</span></span></p>
<p><span data-ttu-id="2b3b8-124">Wenn mehr als eine Übereinstimmung vorliegt, wird die erste Übereinstimmung des Kontakts zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-124">If there is more than one match, we will return the first match of the contact.</span></span></p>
</div>
<div> 
</div></td>
<td align="left"><span data-ttu-id="2b3b8-125">ms-people:viewcontact:?ContactId=&lt;contactid&gt;&amp;AggregatedId=&lt;aggid&gt;&amp;PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;&amp;Contact=&lt;contactobj&gt;</span><span class="sxs-lookup"><span data-stu-id="2b3b8-125">ms-people:viewcontact:?ContactId=&lt;contactid&gt;&amp;AggregatedId=&lt;aggid&gt;&amp;PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;&amp;Contact=&lt;contactobj&gt;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2b3b8-126">Startet mit einer „Kontakt speichern“-Seite innerhalb der Kontakte-App, um den angegeben Kontakt mit der angegebenen Telefonnummer oder E-Mail-Adresse zu speichern.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-126">Launches to a Save-contact page within the People app to save the given contact with the supplied phone number or email address.</span></span>
<div class="alert">
<p><span data-ttu-id="2b3b8-127">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-127">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="2b3b8-128">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-128">The order of the parameters doesn’t matter.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="2b3b8-129">ms-people:savetocontact?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span><span class="sxs-lookup"><span data-stu-id="2b3b8-129">ms-people:savetocontact?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2b3b8-130">Startet mit der Seite „Neuen Kontakt hinzufügen“ innerhalb der Kontakte-App, um den angegeben Kontakt zu speichern.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-130">Launches to the add a new contact page within the People app to save the given contact.</span></span>
<div class="alert"><p><span data-ttu-id="2b3b8-131">Verwenden Sie <a href="https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_">LaunchUriForResultsAsync</a>, um die Seite „Neuen Kontakt speichern“ zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-131">Use <a href="https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_">LaunchUriForResultsAsync</a> to open the save new contact page.</span></span> <span data-ttu-id="2b3b8-132">Mit <strong>LaunchUriAsync</strong> wird nur die Hauptseite der Kontakte-App gestartet.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-132">Using <strong>LaunchUriAsync</strong> will only launch the People app Main page.</span></span></p>
<p><span data-ttu-id="2b3b8-133">Bei den Parametern wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-133">The parameters are case sensitive.</span></span></p>
<p><span data-ttu-id="2b3b8-134">Die Reihenfolge der Parameter spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-134">The order of the parameters doesn’t matter.</span></span></p>
<p><span data-ttu-id="2b3b8-135">Die unterstützten Parametern können in beliebiger Kombination verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-135">You can use any combination of supported parameters.</span></span></p>
</div>
<div>
</div></td>
<td align="left"><span data-ttu-id="2b3b8-136">ms-people:savecontacttask?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span><span class="sxs-lookup"><span data-stu-id="2b3b8-136">ms-people:savecontacttask?PhoneNumber= &lt;phonenum&gt;&amp;Email=&lt;email&gt;&amp;ContactName=&lt;name&gt;</span></span></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesearch-parameter-reference"></a><span data-ttu-id="2b3b8-137">ms-people:search: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="2b3b8-137">ms-people:search: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2b3b8-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="2b3b8-138">Parameter</span></span></th>
<th align="left"><span data-ttu-id="2b3b8-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2b3b8-139">Description</span></span></th>
<th align="left"><span data-ttu-id="2b3b8-140">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2b3b8-140">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-141">Suchzeichenfolge</span><span class="sxs-lookup"><span data-stu-id="2b3b8-141">SearchString</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-142">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-142">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-143">Die Suchzeichenfolge für die Informationen zur Kontaktsuche.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-143">The search string for the contact search information.</span></span></p>
<p><span data-ttu-id="2b3b8-144">Die Telefonnummer oder den Namen des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-144">The phone number or the contact name.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-145">ms-people:search?SearchString=Smith</span><span class="sxs-lookup"><span data-stu-id="2b3b8-145">ms-people:search?SearchString=Smith</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peopleviewcontact-parameter-reference"></a><span data-ttu-id="2b3b8-146">ms-people:viewcontact: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="2b3b8-146">ms-people:viewcontact: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2b3b8-147">Parameter</span><span class="sxs-lookup"><span data-stu-id="2b3b8-147">Parameter</span></span></th>
<th align="left"><span data-ttu-id="2b3b8-148">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2b3b8-148">Description</span></span></th>
<th align="left"><span data-ttu-id="2b3b8-149">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2b3b8-149">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-150">ContactId</span><span class="sxs-lookup"><span data-stu-id="2b3b8-150">ContactId</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-151">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-151">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-152">Die Kontakt-ID des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-152">Contact Id of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-153">ms-people:viewcontact?ContactId={ContactId}</span><span class="sxs-lookup"><span data-stu-id="2b3b8-153">ms-people:viewcontact?ContactId={ContactId}</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-154">PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="2b3b8-154">PhoneNumber</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-155">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-155">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-156">Die Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-156">Phone number of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-157">ms-people:viewcontact?PhoneNumber=%2014257069326</span><span class="sxs-lookup"><span data-stu-id="2b3b8-157">ms-people:viewcontact?PhoneNumber=%2014257069326</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-158">Email</span><span class="sxs-lookup"><span data-stu-id="2b3b8-158">Email</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-159">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-159">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-160">Die E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-160">Email of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-161">ms-people:viewcontact?Email=johnsmith@contsco.com</span><span class="sxs-lookup"><span data-stu-id="2b3b8-161">ms-people:viewcontact?Email=johnsmith@contsco.com</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-162">ContactName</span><span class="sxs-lookup"><span data-stu-id="2b3b8-162">ContactName</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-163">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-163">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-164">Der Name des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-164">Name of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-165">ms-people:viewcontact?ContactName=John%20%Smith</span><span class="sxs-lookup"><span data-stu-id="2b3b8-165">ms-people:viewcontact?ContactName=John%20%Smith</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-166">Contact</span><span class="sxs-lookup"><span data-stu-id="2b3b8-166">Contact</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-167">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-167">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-168">Das Kontaktobjekt.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-168">Contact object.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-169">ms-people:viewcontact?Contact={Serialized Contact}</span><span class="sxs-lookup"><span data-stu-id="2b3b8-169">ms-people:viewcontact?Contact={Serialized Contact}</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesavetocontact-parameter-reference"></a><span data-ttu-id="2b3b8-170">ms-people:savetocontact: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="2b3b8-170">ms-people:savetocontact: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2b3b8-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="2b3b8-171">Parameter</span></span></th>
<th align="left"><span data-ttu-id="2b3b8-172">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2b3b8-172">Description</span></span></th>
<th align="left"><span data-ttu-id="2b3b8-173">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2b3b8-173">Example</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-174">PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="2b3b8-174">PhoneNumber</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-175">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-175">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-176">Die Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-176">Phone number of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-177">ms-people:savetocontact?PhoneNumber=%2014257069326</span><span class="sxs-lookup"><span data-stu-id="2b3b8-177">ms-people:savetocontact?PhoneNumber=%2014257069326</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-178">Email</span><span class="sxs-lookup"><span data-stu-id="2b3b8-178">Email</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-179">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-179">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-180">Die E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-180">Email of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-181">ms-people:savetocontact?Email=johnsmith@contsco.com</span><span class="sxs-lookup"><span data-stu-id="2b3b8-181">ms-people:savetocontact?Email=johnsmith@contsco.com</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-182">ContactName</span><span class="sxs-lookup"><span data-stu-id="2b3b8-182">ContactName</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-183">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-183">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-184">Der Name des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-184">Name of the contact.</span></span></p></td>
<td align="left"><p><span data-ttu-id="2b3b8-185">ms-people:savetocontact?Email=johnsmith@contsco.com&amp;ContactName= John%20%Smith</span><span class="sxs-lookup"><span data-stu-id="2b3b8-185">ms-people:savetocontact?Email=johnsmith@contsco.com&amp;ContactName= John%20%Smith</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="ms-peoplesavecontacttask-parameter-reference"></a><span data-ttu-id="2b3b8-186">ms-people:savecontacttask: Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="2b3b8-186">ms-people:savecontacttask: parameter reference</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2b3b8-187">Parameter</span><span class="sxs-lookup"><span data-stu-id="2b3b8-187">Parameter</span></span></th>
<th align="left"><span data-ttu-id="2b3b8-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2b3b8-188">Description</span></span></th>

</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-189">Firma</span><span class="sxs-lookup"><span data-stu-id="2b3b8-189">Company</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-190">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-190">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-191">Firmenname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-191">Company name of the contact.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-192">Vorname</span><span class="sxs-lookup"><span data-stu-id="2b3b8-192">FirstName</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-193">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-193">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-194">Vorname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-194">First name of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-195">HomeAddressCity</span><span class="sxs-lookup"><span data-stu-id="2b3b8-195">HomeAddressCity</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-196">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-196">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-197">Ort der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-197">City of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-198">HomeAddressCountry</span><span class="sxs-lookup"><span data-stu-id="2b3b8-198">HomeAddressCountry</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-199">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-199">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-200">Land der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-200">Country of the home address.</span></span></p></td>

</tr>
<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-201">HomeAddressState</span><span class="sxs-lookup"><span data-stu-id="2b3b8-201">HomeAddressState</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-202">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-202">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-203">Bundesland der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-203">State of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-204">HomeAddressStreet</span><span class="sxs-lookup"><span data-stu-id="2b3b8-204">HomeAddressStreet</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-205">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-205">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-206">Straße der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-206">Street of the home address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-207">HomeAddressZipCode</span><span class="sxs-lookup"><span data-stu-id="2b3b8-207">HomeAddressZipCode</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-208">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-208">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-209">Postleitzahl der Wohnanschrift.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-209">Zip Code of the home address.</span></span></p></td>

</tr>
<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-210">HomePhone</span><span class="sxs-lookup"><span data-stu-id="2b3b8-210">HomePhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-211">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-211">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-212">Private Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-212">Home phone of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-213">JobTitle</span><span class="sxs-lookup"><span data-stu-id="2b3b8-213">JobTitle</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-214">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-214">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-215">Berufsbezeichnung des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-215">Job title of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-216">LastName</span><span class="sxs-lookup"><span data-stu-id="2b3b8-216">LastName</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-217">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-217">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-218">Nachname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-218">Last name of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-219">MiddleName</span><span class="sxs-lookup"><span data-stu-id="2b3b8-219">MiddleName</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-220">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-220">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-221">Zweiter Vorname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-221">Middle name of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-222">MobilePhone</span><span class="sxs-lookup"><span data-stu-id="2b3b8-222">MobilePhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-223">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-223">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-224">Mobiltelefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-224">Mobile phone number of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-225">Spitzname</span><span class="sxs-lookup"><span data-stu-id="2b3b8-225">Nickname</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-226">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-226">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-227">Spitzname des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-227">Nickname of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-228">Notizen</span><span class="sxs-lookup"><span data-stu-id="2b3b8-228">Notes</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-229">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-229">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-230">Notizen zum Kontakt.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-230">Notes about the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-231">OtherEmail</span><span class="sxs-lookup"><span data-stu-id="2b3b8-231">OtherEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-232">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-232">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-233">Weitere E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-233">Other Email of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-234">PersonalEmail</span><span class="sxs-lookup"><span data-stu-id="2b3b8-234">PersonalEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-235">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-235">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-236">Private E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-236">Personal Email of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-237">Suffix</span><span class="sxs-lookup"><span data-stu-id="2b3b8-237">Suffix</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-238">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-238">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-239">Suffix des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-239">Suffix of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-240">Title</span><span class="sxs-lookup"><span data-stu-id="2b3b8-240">Title</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-241">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-241">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-242">Anrede des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-242">Title of the contact.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-243">Webseite</span><span class="sxs-lookup"><span data-stu-id="2b3b8-243">Website</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-244">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-244">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-245">Webseite des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-245">Website of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-246">WorkAddressCity</span><span class="sxs-lookup"><span data-stu-id="2b3b8-246">WorkAddressCity</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-247">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-247">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-248">Ort der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-248">City of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-249">WorkAddressCountry</span><span class="sxs-lookup"><span data-stu-id="2b3b8-249">WorkAddressCountry</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-250">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-250">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-251">Land der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-251">Country of the work address.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-252">WorkAddressState</span><span class="sxs-lookup"><span data-stu-id="2b3b8-252">WorkAddressState</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-253">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-253">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-254">Bundesland der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-254">State of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-255">WorkAddressStreet</span><span class="sxs-lookup"><span data-stu-id="2b3b8-255">WorkAddressStreet</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-256">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-256">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-257">Straße der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-257">Street of work address.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-258">WorkAddressZipCode</span><span class="sxs-lookup"><span data-stu-id="2b3b8-258">WorkAddressZipCode</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-259">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-259">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-260">Postleitzahl der Geschäftsadresse.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-260">Zip Code of the work address.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><b><span data-ttu-id="2b3b8-261">WorkEmail</span><span class="sxs-lookup"><span data-stu-id="2b3b8-261">WorkEmail</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-262">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-262">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-263">Geschäftliche E-Mail-Adresse des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-263">Work Email of the contact.</span></span></p></td>
</tr>

<tr class="even">
<td align="left"><b><span data-ttu-id="2b3b8-264">WorkPhone</span><span class="sxs-lookup"><span data-stu-id="2b3b8-264">WorkPhone</span></span></b></td>
<td align="left"><p><span data-ttu-id="2b3b8-265">Optional.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-265">Optional.</span></span></p>
<p><span data-ttu-id="2b3b8-266">Geschäftliche Telefonnummer des Kontakts.</span><span class="sxs-lookup"><span data-stu-id="2b3b8-266">Work phone number of the contact.</span></span></p></td>
</tr>
</tbody>
</table>
