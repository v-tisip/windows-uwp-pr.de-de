---
ms.assetid: BF929A68-9C82-4866-BC13-A32B3A550005
title: Nachverfolgen kürzlich verwendeter Dateien und Ordner
description: Sie können Dateien nachverfolgen, auf die häufig zugegriffen wird, indem Sie diese der Liste mit den zuletzt verwendeten Elementen (MRU) der App hinzufügen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 4a810c097b4f162395106e74b68d5e9cdb2f8538
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7845859"
---
# <a name="track-recently-used-files-and-folders"></a><span data-ttu-id="f09c3-104">Nachverfolgen kürzlich verwendeter Dateien und Ordner</span><span class="sxs-lookup"><span data-stu-id="f09c3-104">Track recently used files and folders</span></span>

**<span data-ttu-id="f09c3-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="f09c3-105">Important APIs</span></span>**

- [**<span data-ttu-id="f09c3-106">MostRecentlyUsedList</span><span class="sxs-lookup"><span data-stu-id="f09c3-106">MostRecentlyUsedList</span></span>**](https://msdn.microsoft.com/library/windows/apps/br207458)
- [**<span data-ttu-id="f09c3-107">FileOpenPicker</span><span class="sxs-lookup"><span data-stu-id="f09c3-107">FileOpenPicker</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh738369)

<span data-ttu-id="f09c3-108">Sie können Dateien nachverfolgen, auf die häufig zugegriffen wird, indem Sie sie der Liste mit den zuletzt verwendeten Elementen (MRU) der App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-108">Track files that your user accesses frequently by adding them to your app's most recently used list (MRU).</span></span> <span data-ttu-id="f09c3-109">Die Plattform verwaltet die MRU für Sie. Dabei werden Elemente nach der Zeit und dem Ort des letzten Zugriffs sortiert und die ältesten Elemente entfernt, wenn das Limit von 25Elementen erreicht ist.</span><span class="sxs-lookup"><span data-stu-id="f09c3-109">The platform manages the MRU for you by sorting items based on when they were last accessed, and by removing the oldest item when the list's 25-item limit is reached.</span></span> <span data-ttu-id="f09c3-110">Alle Apps besitzen eine eigene MRU.</span><span class="sxs-lookup"><span data-stu-id="f09c3-110">All apps have their own MRU.</span></span>

<span data-ttu-id="f09c3-111">Ihre App-MRU-Liste wird durch die [**StorageItemMostRecentlyUsedList**](https://msdn.microsoft.com/library/windows/apps/br207475)-Klasse repräsentiert, die Sie aus der statischen [**StorageApplicationPermissions.MostRecentlyUsedList**](https://msdn.microsoft.com/library/windows/apps/br207458)-Eigenschaft abrufen können.</span><span class="sxs-lookup"><span data-stu-id="f09c3-111">Your app's MRU is represented by the [**StorageItemMostRecentlyUsedList**](https://msdn.microsoft.com/library/windows/apps/br207475) class, which you obtain from the static [**StorageApplicationPermissions.MostRecentlyUsedList**](https://msdn.microsoft.com/library/windows/apps/br207458) property.</span></span> <span data-ttu-id="f09c3-112">MRU-Elemente werden als [**IStorageItem**](https://msdn.microsoft.com/library/windows/apps/br227129)-Objekte gespeichert. Das bedeutet, dass sowohl [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekte (die Dateien darstellen) als auch [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230)-Objekte (die Ordner darstellen) der MRU-Liste hinzugefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="f09c3-112">MRU items are stored as [**IStorageItem**](https://msdn.microsoft.com/library/windows/apps/br227129) objects, so both [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) objects (which represent files) and [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) objects (which represent folders) can be added to the MRU.</span></span>

> [!NOTE]
> <span data-ttu-id="f09c3-113">Weitere Informationen finden Sie im [Dateiauswahl-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619994) und im [Dateizugriff-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619995).</span><span class="sxs-lookup"><span data-stu-id="f09c3-113">Also see the [File picker sample](http://go.microsoft.com/fwlink/p/?linkid=619994) and the [File access sample](http://go.microsoft.com/fwlink/p/?linkid=619995).</span></span>

 

## <a name="prerequisites"></a><span data-ttu-id="f09c3-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f09c3-114">Prerequisites</span></span>

-   **<span data-ttu-id="f09c3-115">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="f09c3-115">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="f09c3-116">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span><span class="sxs-lookup"><span data-stu-id="f09c3-116">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span></span> <span data-ttu-id="f09c3-117">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span><span class="sxs-lookup"><span data-stu-id="f09c3-117">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span></span>

-   **<span data-ttu-id="f09c3-118">Zugriffsberechtigungen für den Speicherort</span><span class="sxs-lookup"><span data-stu-id="f09c3-118">Access permissions to the location</span></span>**

    <span data-ttu-id="f09c3-119">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](file-access-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="f09c3-119">See [File access permissions](file-access-permissions.md).</span></span>

-   [<span data-ttu-id="f09c3-120">Öffnen von Dateien und Ordnern mit einer Auswahl</span><span class="sxs-lookup"><span data-stu-id="f09c3-120">Open files and folders with a picker</span></span>](quickstart-using-file-and-folder-pickers.md)

    <span data-ttu-id="f09c3-121">Die ausgewählten Dateien sind meist diejenigen, auf die Benutzer immer wieder zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-121">Picked files are often the same files that users return to again and again.</span></span>

 ## <a name="add-a-picked-file-to-the-mru"></a><span data-ttu-id="f09c3-122">Hinzufügen der ausgewählten Dateien zu MRU</span><span class="sxs-lookup"><span data-stu-id="f09c3-122">Add a picked file to the MRU</span></span>

-   <span data-ttu-id="f09c3-123">Die Dateien, die der Benutzer wählt sind häufig Dateien, denen sie wiederholt zurückgeben werden.</span><span class="sxs-lookup"><span data-stu-id="f09c3-123">The files that your user picks are often files that they return to repeatedly.</span></span> <span data-ttu-id="f09c3-124">Erwägen Sie also, die ausgewählten Dateien Ihrer App-MRU-Liste hinzufügen, sobald sie ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="f09c3-124">So consider adding picked files to your app's MRU as soon as they are picked.</span></span> <span data-ttu-id="f09c3-125">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="f09c3-125">Here's how.</span></span>

    ```cs
    Windows.Storage.StorageFile file = await picker.PickSingleFileAsync();

    var mru = Windows.Storage.AccessCache.StorageApplicationPermissions.MostRecentlyUsedList;
    string mruToken = mru.Add(file, "profile pic");
    ```

    <span data-ttu-id="f09c3-126">[**StorageItemMostRecentlyUsedList.Add**](https://msdn.microsoft.com/library/windows/apps/br207476) wird überladen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-126">[**StorageItemMostRecentlyUsedList.Add**](https://msdn.microsoft.com/library/windows/apps/br207476) is overloaded.</span></span> <span data-ttu-id="f09c3-127">Im Beispiel verwenden wir [**Add(IStorageItem, String)**](https://msdn.microsoft.com/library/windows/apps/br207481), sodass wir der Datei Metadaten zuordnen können.</span><span class="sxs-lookup"><span data-stu-id="f09c3-127">In the example, we use [**Add(IStorageItem, String)**](https://msdn.microsoft.com/library/windows/apps/br207481) so that we can associate metadata with the file.</span></span> <span data-ttu-id="f09c3-128">Wenn Sie Metadaten festlegen, können Sie den Zweck des Elements festlegen, z. B. Profilauswahl.</span><span class="sxs-lookup"><span data-stu-id="f09c3-128">Setting metadata lets you record the item's purpose, for example "profile pic".</span></span> <span data-ttu-id="f09c3-129">Sie können die Datei durch einen Aufruf von [**Add(IStorageItem)**](https://msdn.microsoft.com/library/windows/apps/br207480) auch ohne Metadaten der MRU-Liste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-129">You can also add the file to the MRU without metadata by calling [**Add(IStorageItem)**](https://msdn.microsoft.com/library/windows/apps/br207480).</span></span> <span data-ttu-id="f09c3-130">Beim Hinzufügen eines Elements zur MRU-Liste gibt die Methode eine eindeutig identifizierende Zeichenfolge zurück. Mit diesem sogenannten Token wird das Element abgerufen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-130">When you add an item to the MRU, the method returns a uniquely identifying string, called a token, which is used to retrieve the item.</span></span>

> [!TIP]
> <span data-ttu-id="f09c3-131">Sie benötigen das Token zum Abrufen eines Elements aus der MRU-Liste, speichern Sie es also an einer beliebigen Stelle.</span><span class="sxs-lookup"><span data-stu-id="f09c3-131">You'll need the token to retrieve an item from the MRU, so persist it somewhere.</span></span> <span data-ttu-id="f09c3-132">Weitere Informationen zu App-Daten finden Sie unter [Verwalten von Anwendungsdaten](https://msdn.microsoft.com/library/windows/apps/hh465109).</span><span class="sxs-lookup"><span data-stu-id="f09c3-132">For more info about app data, see [Managing application data](https://msdn.microsoft.com/library/windows/apps/hh465109).</span></span>

## <a name="use-a-token-to-retrieve-an-item-from-the-mru"></a><span data-ttu-id="f09c3-133">Verwenden von Token zum Abrufen von Elementen aus der MRU-Liste</span><span class="sxs-lookup"><span data-stu-id="f09c3-133">Use a token to retrieve an item from the MRU</span></span>

<span data-ttu-id="f09c3-134">Verwenden Sie die Abrufmethode, die für das abzurufende Element am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="f09c3-134">Use the retrieval method most appropriate for the item you want to retrieve.</span></span>

-   <span data-ttu-id="f09c3-135">Rufen Sie mit [**GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br207486) eine Datei als [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) ab.</span><span class="sxs-lookup"><span data-stu-id="f09c3-135">Retrieve a file as a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) by using [**GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br207486).</span></span>
-   <span data-ttu-id="f09c3-136">Rufen Sie mit [**GetFolderAsync**](https://msdn.microsoft.com/library/windows/apps/br207489) einen Ordner als [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) ab.</span><span class="sxs-lookup"><span data-stu-id="f09c3-136">Retrieve a folder as a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) by using [**GetFolderAsync**](https://msdn.microsoft.com/library/windows/apps/br207489).</span></span>
-   <span data-ttu-id="f09c3-137">Rufen Sie mit [**GetItemAsync**](https://msdn.microsoft.com/library/windows/apps/br207492) ein allgemeines [**IStorageItem**](https://msdn.microsoft.com/library/windows/apps/br227129)-Element ab, das eine Datei oder einen Ordner darstellen kann.</span><span class="sxs-lookup"><span data-stu-id="f09c3-137">Retrieve a generic [**IStorageItem**](https://msdn.microsoft.com/library/windows/apps/br227129), which can represent either a file or folder, by using [**GetItemAsync**](https://msdn.microsoft.com/library/windows/apps/br207492).</span></span>

<span data-ttu-id="f09c3-138">Im Folgenden erfahren Sie, wie Sie die Datei abrufen können, die gerade hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="f09c3-138">Here's how to get back the file we just added.</span></span>

```cs
StorageFile retrievedFile = await mru.GetFileAsync(mruToken);
```

<span data-ttu-id="f09c3-139">Hier wird erläutert, wie alle Einträge zum Abrufen von Token und anschließend Elementen durchlaufen werden.</span><span class="sxs-lookup"><span data-stu-id="f09c3-139">Here's how to iterate all the entries to get tokens and then items.</span></span>

```cs
foreach (Windows.Storage.AccessCache.AccessListEntry entry in mru.Entries)
{
    string mruToken = entry.Token;
    string mruMetadata = entry.Metadata;
    Windows.Storage.IStorageItem item = await mru.GetItemAsync(mruToken);
    // The type of item will tell you whether it's a file or a folder.
}
```

<span data-ttu-id="f09c3-140">Mit [**AccessListEntryView**](https://msdn.microsoft.com/library/windows/apps/br227349) können Sie Einträge in der MRU-Liste durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-140">The [**AccessListEntryView**](https://msdn.microsoft.com/library/windows/apps/br227349) lets you iterate entries in the MRU.</span></span> <span data-ttu-id="f09c3-141">Diese Einträge sind [**AccessListEntry**](https://msdn.microsoft.com/library/windows/apps/br227348)-Strukturen, die das Token und Metadaten für ein Element enthalten.</span><span class="sxs-lookup"><span data-stu-id="f09c3-141">These entries are [**AccessListEntry**](https://msdn.microsoft.com/library/windows/apps/br227348) structures that contain the token and metadata for an item.</span></span>

## <a name="removing-items-from-the-mru-when-its-full"></a><span data-ttu-id="f09c3-142">Entfernen von Elementen aus der MRU-Liste beim Erreichen des Grenzwerts</span><span class="sxs-lookup"><span data-stu-id="f09c3-142">Removing items from the MRU when it's full</span></span>

<span data-ttu-id="f09c3-143">Wenn das Limit von 25 Elementen der MRU-Liste erreicht ist und ein neues Element hinzugefügt werden soll, wird das älteste Element (bei dem der letzte Zugriff am längsten zurück liegt) automatisch entfernt.</span><span class="sxs-lookup"><span data-stu-id="f09c3-143">When the MRU's 25-item limit is reached and you try to add a new item, the item that was accessed the longest time ago is automatically removed.</span></span> <span data-ttu-id="f09c3-144">Sie müssen also nie ein Element entfernen, bevor Sie ein neues hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-144">So, you never need to remove an item before you add a new one.</span></span>

## <a name="future-access-list"></a><span data-ttu-id="f09c3-145">Liste für zukünftigen Zugriff</span><span class="sxs-lookup"><span data-stu-id="f09c3-145">Future-access list</span></span>

<span data-ttu-id="f09c3-146">Genau wie eine MRU-Liste besitzt auch Ihre App eine Liste für zukünftigen Zugriff.</span><span class="sxs-lookup"><span data-stu-id="f09c3-146">As well as an MRU, your app also has a future-access list.</span></span> <span data-ttu-id="f09c3-147">Durch die Auswahl von Dateien und Ordnern erteilt der Benutzer Ihrer App die Berechtigung zum Zugreifen auf Elemente, auf die andernfalls nicht zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f09c3-147">By picking files and folders, your user grants your app permission to access items that might not be accessible otherwise.</span></span> <span data-ttu-id="f09c3-148">Wenn Sie diese Elemente zu Ihrer Liste für zukünftigen Zugriff hinzufügen, behalten Sie die Berechtigung, wenn Ihre App später erneut auf diese Elemente zugreifen möchte.</span><span class="sxs-lookup"><span data-stu-id="f09c3-148">If you add these items to your future-access list then you'll retain that permission when your app wants to access those items again later.</span></span> <span data-ttu-id="f09c3-149">Ihre App-Liste für zukünftigen Zugriff wird durch die [**StorageItemAccessList**](https://msdn.microsoft.com/library/windows/apps/br207459)-Klasse dargestellt, die Sie aus der statischen [**StorageApplicationPermissions.FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457)-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-149">Your app's future-access list is represented by the [**StorageItemAccessList**](https://msdn.microsoft.com/library/windows/apps/br207459) class, which you obtain from the static [**StorageApplicationPermissions.FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) property.</span></span>

<span data-ttu-id="f09c3-150">Wenn ein Benutzer ein Element auswählt, sollten Sie es Ihrer Liste für zukünftigen Zugriff und der MRU-Liste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f09c3-150">When a user picks an item, consider adding it to your future-access list as well as your MRU.</span></span>

-   <span data-ttu-id="f09c3-151">[**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) kann bis zu 1.000 Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="f09c3-151">The [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) can hold up to 1000 items.</span></span> <span data-ttu-id="f09c3-152">Denken Sie daran: Die Liste kann Ordner und Dateien enthalten. Das können also eine ganze Menge Ordner sein.</span><span class="sxs-lookup"><span data-stu-id="f09c3-152">Remember: it can hold folders as well as files, so that's a lot of folders.</span></span>
-   <span data-ttu-id="f09c3-153">Die Plattform entfernt niemals Elemente aus der [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) für Sie.</span><span class="sxs-lookup"><span data-stu-id="f09c3-153">The platform never removes items from the [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) for you.</span></span> <span data-ttu-id="f09c3-154">Wenn das Limit von 1.000Elementen erreicht ist, können Sie kein weiteres hinzufügen, bis Sie mit der Methode [**Remove**](https://msdn.microsoft.com/library/windows/apps/br207497) Platz geschaffen haben.</span><span class="sxs-lookup"><span data-stu-id="f09c3-154">When you reach the 1000-item limit, you can't add another until you make room with the [**Remove**](https://msdn.microsoft.com/library/windows/apps/br207497) method.</span></span>
