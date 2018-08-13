---
author: TylerMSFT
title: Starten der Microsoft Store-App
description: In diesem Thema wird das URI-Schema „ms-windows-store“ beschrieben. Ihre app kann dieser URI-Schema verwenden, um die Microsoft Store-app zu bestimmten Seiten im Speicher zu starten.
ms.assetid: 9A9C6576-1637-47D1-AC3B-D1A20D49E0FF
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 0b97e4da92a7cd4066ca555189f052e3e82006fe
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "975652"
---
# <a name="launch-the-microsoft-store-app"></a><span data-ttu-id="053ee-105">Starten der Microsoft Store-App</span><span class="sxs-lookup"><span data-stu-id="053ee-105">Launch the Microsoft Store app</span></span>



<span data-ttu-id="053ee-106">In diesem Thema wird das **ms-windows-store:**-URI-Schema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="053ee-106">This topic describes the **ms-windows-store:** URI scheme.</span></span> <span data-ttu-id="053ee-107">Ihre app kann dieser URI-Schema verwenden, um die Microsoft Store-app zu bestimmten Seiten im Speicher zu starten, mithilfe der [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) -Methode.</span><span class="sxs-lookup"><span data-stu-id="053ee-107">Your app can use this URI scheme to launch the Microsoft Store app to specific pages in the store by using the [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) method.</span></span>

<span data-ttu-id="053ee-108">Dieses Beispiel zeigt, wie Sie den Speicher auf der Seite Spiele zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="053ee-108">This example shows how to open the Store to the Games page:</span></span>

```cs
bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-windows-store://navigatetopage/?Id=Games"));
```

## <a name="ms-windows-store-uri-scheme-reference"></a><span data-ttu-id="053ee-109">ms-windows-store: URI-Schemaverweis</span><span class="sxs-lookup"><span data-stu-id="053ee-109">ms-windows-store: URI scheme reference</span></span>

<table>
<tr><th><span data-ttu-id="053ee-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="053ee-110">Description</span></span></th><th></th><th><span data-ttu-id="053ee-111">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="053ee-111">URI scheme</span></span></th></tr>
<tr><td><span data-ttu-id="053ee-112">Startet die Startseite des Store.</span><span class="sxs-lookup"><span data-stu-id="053ee-112">Launches the home page of the Store.</span></span></td><td /><td><span data-ttu-id="053ee-113">ms-windows-store://home</span><span class="sxs-lookup"><span data-stu-id="053ee-113">ms-windows-store://home</span></span></td></tr>
<tr><td><span data-ttu-id="053ee-114">Startet eine der obersten Ebenen im Store.</span><span class="sxs-lookup"><span data-stu-id="053ee-114">Launches a top-level vertical in the Store.</span></span><p><span data-ttu-id="053ee-115">Hinweis: Nicht alle Benutzer haben Zugriff auf allen Ebenen.</span><span class="sxs-lookup"><span data-stu-id="053ee-115">Note: Not all users have access to all verticals.</span></span></p>
</td><td /><td>
<p><span data-ttu-id="053ee-116">ms-windows-store://navigatetopage/?Id=Apps</span><span class="sxs-lookup"><span data-stu-id="053ee-116">ms-windows-store://navigatetopage/?Id=Apps</span></span> </p>
<p><span data-ttu-id="053ee-117">ms-windows-store://navigatetopage/?Id=Games</span><span class="sxs-lookup"><span data-stu-id="053ee-117">ms-windows-store://navigatetopage/?Id=Games</span></span></p>
<p><span data-ttu-id="053ee-118">ms-windows-store://navigatetopage/?Id=Music</span><span class="sxs-lookup"><span data-stu-id="053ee-118">ms-windows-store://navigatetopage/?Id=Music</span></span></p>
<p><span data-ttu-id="053ee-119">ms-windows-store://navigatetopage/?Id=Video</span><span class="sxs-lookup"><span data-stu-id="053ee-119">ms-windows-store://navigatetopage/?Id=Video</span></span></p>
<p><span data-ttu-id="053ee-120">ms-windows-store://navigatetopage/?Id=LOB</span><span class="sxs-lookup"><span data-stu-id="053ee-120">ms-windows-store://navigatetopage/?Id=LOB</span></span></p>
</td>
</tr>
<tr>
<td rowspan="4"><span data-ttu-id="053ee-121">Startet die Seite mit Produktdetails für ein Produkt.</span><span class="sxs-lookup"><span data-stu-id="053ee-121">Launches the product details page (PDP) for a product.</span></span> <p><span data-ttu-id="053ee-122">Store-ID wird für Kunden mit Windows 10 empfohlen und funktioniert für alle Betriebssystemversionen. Die früheren Verfahren hierfür (Beispiel: PFN) werden jedoch weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="053ee-122">Store ID is recommended for customers on Windows 10, and will work on all OS versions, but the earlier ways of doing it (ex: PFN) are still supported.</span></span></p>
<p><span data-ttu-id="053ee-123">Diese Werte finden Sie im Windows Dev Center-Dashboard auf der Seite <a href="https://msdn.microsoft.com/library/windows/apps/mt148561.aspx">App-Identität</a> im Abschnitt zur App-Verwaltung für die einzelnen Apps.</span><span class="sxs-lookup"><span data-stu-id="053ee-123">These values can be found in the Windows Dev Center dashboard on the <a href="https://msdn.microsoft.com/library/windows/apps/mt148561.aspx">App identity</a> page in the App management section for each app.</span></span></p>
</td>
<td>
<span data-ttu-id="053ee-124">Store-ID</span><span class="sxs-lookup"><span data-stu-id="053ee-124">Store ID</span></span> <p><span data-ttu-id="053ee-125">(Empfohlen)</span><span class="sxs-lookup"><span data-stu-id="053ee-125">(Recommended)</span></span></p>
</td>
<td>
<p><span data-ttu-id="053ee-126">ms-windows-store://pdp/?ProductId=9WZDNCRFHVJL</span><span class="sxs-lookup"><span data-stu-id="053ee-126">ms-windows-store://pdp/?ProductId=9WZDNCRFHVJL</span></span></p>
</td>
</tr>
<tr>
<td><span data-ttu-id="053ee-127">Paketfamilienname (PFN)</span><span class="sxs-lookup"><span data-stu-id="053ee-127">Package Family Name (PFN)</span></span></td>
<td><span data-ttu-id="053ee-128">ms-windows-store://pdp/?PFN= Microsoft.Office.OneNote_8wekyb3d8bbwe</span><span class="sxs-lookup"><span data-stu-id="053ee-128">ms-windows-store://pdp/?PFN= Microsoft.Office.OneNote_8wekyb3d8bbwe</span></span>
</td>
</tr>
<tr>
<td><span data-ttu-id="053ee-129">Produkt-ID (Windows Phone 7.x/8.x)</span><span class="sxs-lookup"><span data-stu-id="053ee-129">Product ID (Windows Phone 7.x/8.x)</span></span></td>
<td><span data-ttu-id="053ee-130">ms-windows-store://pdp/?PhoneAppId=ca05b3ab-f157-450c-8c49-a1f127f5e71d</span><span class="sxs-lookup"><span data-stu-id="053ee-130">ms-windows-store://pdp/?PhoneAppId=ca05b3ab-f157-450c-8c49-a1f127f5e71d</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="053ee-131">Produkt-ID (Windows 8.x)</span><span class="sxs-lookup"><span data-stu-id="053ee-131">Product ID (Windows 8.x)</span></span></td>
<td><span data-ttu-id="053ee-132">ms-windows-store://pdp/?AppId=f022389f-f3a6-417e-ad23-704fbdf57117</span><span class="sxs-lookup"><span data-stu-id="053ee-132">ms-windows-store://pdp/?AppId=f022389f-f3a6-417e-ad23-704fbdf57117</span></span>
</td>
</tr>
<tr>
<td rowspan="4"><span data-ttu-id="053ee-133">Startet das Schreiben einer Bewertung für ein Produkt.</span><span class="sxs-lookup"><span data-stu-id="053ee-133">Launches the write a review experience for a product.</span></span></td>
<td><span data-ttu-id="053ee-134">Store-ID</span><span class="sxs-lookup"><span data-stu-id="053ee-134">Store ID</span></span> <p><span data-ttu-id="053ee-135">(Empfohlen)</span><span class="sxs-lookup"><span data-stu-id="053ee-135">(Recommended)</span></span></p></td>
<td><span data-ttu-id="053ee-136">ms-windows-store://review/?ProductId=9WZDNCRFHVJL</span><span class="sxs-lookup"><span data-stu-id="053ee-136">ms-windows-store://review/?ProductId=9WZDNCRFHVJL</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="053ee-137">Paketfamilienname (PFN)</span><span class="sxs-lookup"><span data-stu-id="053ee-137">Package Family Name (PFN)</span></span></td>
<td><span data-ttu-id="053ee-138">ms-windows-store://review/?PFN= Microsoft.Office.OneNote_8wekyb3d8bbwe</span><span class="sxs-lookup"><span data-stu-id="053ee-138">ms-windows-store://review/?PFN= Microsoft.Office.OneNote_8wekyb3d8bbwe</span></span>
</td>
</tr>
<tr>
<td><span data-ttu-id="053ee-139">Produkt-ID (Windows Phone 7.x/8.x)</span><span class="sxs-lookup"><span data-stu-id="053ee-139">Product ID (Windows Phone 7.x/8.x)</span></span></td>
<td><span data-ttu-id="053ee-140">ms-windows-store://reviewapp/?AppId=ca05b3ab-f157-450c-8c49-a1f127f5e71d</span><span class="sxs-lookup"><span data-stu-id="053ee-140">ms-windows-store://reviewapp/?AppId=ca05b3ab-f157-450c-8c49-a1f127f5e71d</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="053ee-141">Produkt-ID (Windows 8.x)</span><span class="sxs-lookup"><span data-stu-id="053ee-141">Product ID (Windows 8.x)</span></span></td>
<td><span data-ttu-id="053ee-142">ms-windows-store://review/?AppId=f022389f-f3a6-417e-ad23-704fbdf57117</span><span class="sxs-lookup"><span data-stu-id="053ee-142">ms-windows-store://review/?AppId=f022389f-f3a6-417e-ad23-704fbdf57117</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="053ee-143">Startet eine Suche nach Produkten, die einer Dateierweiterung zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="053ee-143">Launches a search for products associated with a file extension.</span></span> </td>
<td />
<td><span data-ttu-id="053ee-144">ms-windows-store://assoc/?FileExt=pdf</span><span class="sxs-lookup"><span data-stu-id="053ee-144">ms-windows-store://assoc/?FileExt=pdf</span></span>
</td>
</tr>
<tr>
<td><span data-ttu-id="053ee-145">Startet eine Suche nach Produkten, die einem Protokoll zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="053ee-145">Launches a search for products associated with a protocol.</span></span></td>
<td />
<td><span data-ttu-id="053ee-146">ms-windows-store://assoc/?Protocol=ms-word</span><span class="sxs-lookup"><span data-stu-id="053ee-146">ms-windows-store://assoc/?Protocol=ms-word</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="053ee-147">Startet eine Suche nach Produkten, die mindestens einem Tag zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="053ee-147">Launches a search for products associated with one or more tags.</span></span> <span data-ttu-id="053ee-148">Tags müssen durch Kommas getrennt werden.</span><span class="sxs-lookup"><span data-stu-id="053ee-148">Tags should be separated by commas.</span></span>
</td>
<td />
<td>
<p><span data-ttu-id="053ee-149">ms-windows-store://assoc/?Tags=Photos_Rich_Media_Edit</span><span class="sxs-lookup"><span data-stu-id="053ee-149">ms-windows-store://assoc/?Tags=Photos_Rich_Media_Edit</span></span> </p>
<p><span data-ttu-id="053ee-150">ms-windows-store://assoc/?Tags=Photos_Rich_Media_Edit, Camera_Capture_App</span><span class="sxs-lookup"><span data-stu-id="053ee-150">ms-windows-store://assoc/?Tags=Photos_Rich_Media_Edit, Camera_Capture_App</span></span></p>
</td>
</tr>
<tr>
<td>
<span data-ttu-id="053ee-151">Startet eine Suche für die angegebene Abfrage.</span><span class="sxs-lookup"><span data-stu-id="053ee-151">Launches a search for the specified query.</span></span> <span data-ttu-id="053ee-152">Leerzeichen in der Abfrage sind zulässig.</span><span class="sxs-lookup"><span data-stu-id="053ee-152">Spaces in the query are allowed.</span></span>
</td>
<td />
<td><span data-ttu-id="053ee-153">ms-windows-store://search/?query=OneNote</span><span class="sxs-lookup"><span data-stu-id="053ee-153">ms-windows-store://search/?query=OneNote</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="053ee-154">Startet eine Suche nach Produkten in einer Kategorie.</span><span class="sxs-lookup"><span data-stu-id="053ee-154">Launches a search for products in a category.</span></span></td>
<td />
<td>
<p><span data-ttu-id="053ee-155">ms-windows-store://browse/?type=Apps&amp;cat=Productivity</span><span class="sxs-lookup"><span data-stu-id="053ee-155">ms-windows-store://browse/?type=Apps&amp;cat=Productivity</span></span></p>
<p><span data-ttu-id="053ee-156">ms-windows-store://browse/?type=Apps&amp;cat=Health+%26+fitness</span><span class="sxs-lookup"><span data-stu-id="053ee-156">ms-windows-store://browse/?type=Apps&amp;cat=Health+%26+fitness</span></span> </p>
</td>
</tr>
<tr>
<td><span data-ttu-id="053ee-157">Startet eine Suche nach Produkten eines angegebenen Herausgebers.</span><span class="sxs-lookup"><span data-stu-id="053ee-157">Launches a search for products from the specified publisher.</span></span> <span data-ttu-id="053ee-158">Leerzeichen in der Abfrage sind zulässig.</span><span class="sxs-lookup"><span data-stu-id="053ee-158">Spaces in the name are allowed.</span></span>
</td>
<td />
<td><span data-ttu-id="053ee-159">ms-windows-store://publisher/?name=Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="053ee-159">ms-windows-store://publisher/?name=Microsoft Corporation</span></span>
</td>
</tr>
<tr><td><span data-ttu-id="053ee-160">Startet die Downloads- und Updateseite.</span><span class="sxs-lookup"><span data-stu-id="053ee-160">Launches the downloads and updates page.</span></span></td>
<td />
<td><span data-ttu-id="053ee-161">ms-windows-store://downloadsandupdates</span><span class="sxs-lookup"><span data-stu-id="053ee-161">ms-windows-store://downloadsandupdates</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="053ee-162">Startet die Store-Einstellungsseite.</span><span class="sxs-lookup"><span data-stu-id="053ee-162">Launches the Store settings page.</span></span></td>
<td />
<td><span data-ttu-id="053ee-163">ms-windows-store://settings</span><span class="sxs-lookup"><span data-stu-id="053ee-163">ms-windows-store://settings</span></span> </td>
</tr>
</table>

 

 
