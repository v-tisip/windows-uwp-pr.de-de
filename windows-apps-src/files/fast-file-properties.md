---
author: laurenhughes
title: Schneller Zugriff auf Dateieigenschaften in UWP
description: Stellen Sie schnell eine Liste von Dateien und ihren Eigenschaften über eine Bibliothek in einer UWP-App zusammen.
ms.author: lahugh
ms.date: 03/22/2018
ms.topic: article
keywords: Windows10, Uwp, Datei, Eigenschaften
ms.localizationpriority: medium
ms.openlocfilehash: e2f63e848820361a64a2a96348a8e1cc2419f233
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6264540"
---
# <a name="fast-access-to-file-properties-in-uwp"></a><span data-ttu-id="c83aa-104">Schneller Zugriff auf Dateieigenschaften in UWP</span><span class="sxs-lookup"><span data-stu-id="c83aa-104">Fast access to file properties in UWP</span></span> 

<span data-ttu-id="c83aa-105">Erfahren Sie, wie Sie schnell eine Liste von Dateien und ihren Eigenschaften aus einer Bibliothek zusammenstellen und diese Eigenschaften in einer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c83aa-105">Learn how to quickly gather a list of files and their properties from a library and use those properties in an app.</span></span>  

<span data-ttu-id="c83aa-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c83aa-106">Prerequisites</span></span> 
- <span data-ttu-id="c83aa-107">**Asynchrone Programmierung für universelle Windows-Plattform (UWP) apps**  erfahren Sie, wie zum Schreiben von asynchronen apps in c# oder Visual Basic finden Sie unter [aufrufen asynchroner APIs in c# oder Visual Basic](https://docs.microsoft.com/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).    </span><span class="sxs-lookup"><span data-stu-id="c83aa-107">**Asynchronous programming for Universal Windows Platform (UWP) apps**     You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://docs.microsoft.com/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).</span></span> <span data-ttu-id="c83aa-108">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://docs.microsoft.com/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span><span class="sxs-lookup"><span data-stu-id="c83aa-108">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://docs.microsoft.com/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span></span> 
- <span data-ttu-id="c83aa-109">**Zugriffsberechtigungen für Bibliotheken**  Der Code in diesen Beispielen erfordert die **PicturesLibrary** -Funktion, aber Ihr Dateispeicherort erfordern einen anderen Zugriffstyp oder keinen überhaupt.</span><span class="sxs-lookup"><span data-stu-id="c83aa-109">**Access permissions to Libraries**  The code in these examples requires the **picturesLibrary** capability, but your file location may require a different capability, or no capability at all.</span></span> <span data-ttu-id="c83aa-110">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](https://docs.microsoft.com/windows/uwp/files/file-access-permissions).</span><span class="sxs-lookup"><span data-stu-id="c83aa-110">To learn more, see [File access permissions](https://docs.microsoft.com/windows/uwp/files/file-access-permissions).</span></span> 
- <span data-ttu-id="c83aa-111">**Einfache dateiauflistung**  Diesem Beispiel wird mit [QueryOptions](https://docs.microsoft.com/uwp/api/Windows.Storage.Search.QueryOptions) einige erweiterte aufzählungseigenschaften gesetzt.</span><span class="sxs-lookup"><span data-stu-id="c83aa-111">**Simple file enumeration**  This example uses [QueryOptions](https://docs.microsoft.com/uwp/api/Windows.Storage.Search.QueryOptions) to set a few advanced enumeration properties.</span></span> <span data-ttu-id="c83aa-112">Um mehr darüber zu erfahren, wie Sie eine einfache Liste von Dateien für ein kleineres Verzeichnis erhalten, lesen Sie [Aufzählen und Abfragen von Dateien und Ordnern](https://docs.microsoft.com/windows/uwp/files/quickstart-listing-files-and-folders).</span><span class="sxs-lookup"><span data-stu-id="c83aa-112">To learn more about just getting a simple list of files for a smaller directory, see [Enumerate and query files and folders](https://docs.microsoft.com/windows/uwp/files/quickstart-listing-files-and-folders).</span></span> 

## <a name="usage"></a><span data-ttu-id="c83aa-113">Verwendung</span><span class="sxs-lookup"><span data-stu-id="c83aa-113">Usage</span></span>  
<span data-ttu-id="c83aa-114">Viele Apps müssen die Eigenschaften einer Gruppe von Dateien auflisten, müssen aber nicht immer direkt mit den Dateien interagieren.</span><span class="sxs-lookup"><span data-stu-id="c83aa-114">Many apps need to list the properties of a group of files, but don't always need to interact with the files directly.</span></span> <span data-ttu-id="c83aa-115">Zum Beispiel, eine Musikanwendung spielt immer nur eine Datei ab (Öffnen), aber sie benötigt die Eigenschaften aller Dateien in einem Ordner, so dass die Anwendung die Song-Warteschlange anzeigen kann. So kann der Benutzer eine gültige Datei zum Abspielen auswählen.</span><span class="sxs-lookup"><span data-stu-id="c83aa-115">For example, a music app plays (opens) one file at a time, but it needs the properties of all of the files in a folder so the app can show the song queue, or so the user can choose a valid file to play.</span></span> 

<span data-ttu-id="c83aa-116">Die Beispiele auf dieser Seite sollten nicht in Apps verwendet werden, die die Metadaten jeder Datei modifizieren, oder in Apps, die mit allen resultierenden StorageFiles interagieren (über das Lesen ihrer Eigenschaften hinaus).</span><span class="sxs-lookup"><span data-stu-id="c83aa-116">The examples on this page shouldn't be used in apps that will modify the metadata of every file or apps that interact with all the resulting StorageFiles beyond reading their properties.</span></span> <span data-ttu-id="c83aa-117">Weitere Informationen finden Sie unter [Aufzählung und Abfrage von Dateien und Ordnern](https://docs.microsoft.com/windows/uwp/files/quickstart-listing-files-and-folders).</span><span class="sxs-lookup"><span data-stu-id="c83aa-117">See [Enumerate and query files and folders](https://docs.microsoft.com/windows/uwp/files/quickstart-listing-files-and-folders) for more information.</span></span> 

## <a name="enumerate-all-the-pictures-in-a-location"></a><span data-ttu-id="c83aa-118">Aufzählung aller Bilder eines Ortes</span><span class="sxs-lookup"><span data-stu-id="c83aa-118">Enumerate all the pictures in a location</span></span> 
<span data-ttu-id="c83aa-119">In diesem Beispiel führen Sie folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="c83aa-119">In this example, we will</span></span>
-  <span data-ttu-id="c83aa-120">Erstellen Sie ein [QueryOptions](https://docs.microsoft.com/uwp/api/Windows.Storage.Search.QueryOptions)-Objekt, um anzugeben, dass das Programm die Dateien so schnell wie möglich aufzählen möchte.</span><span class="sxs-lookup"><span data-stu-id="c83aa-120">Build a [QueryOptions](https://docs.microsoft.com/uwp/api/Windows.Storage.Search.QueryOptions) object to specify that the app wants to enumerate the files as quickly as possible.</span></span>
-  <span data-ttu-id="c83aa-121">Holen Sie Dateieigenschaften durch Auslagern von StorageFile-Objekten in das Programm.</span><span class="sxs-lookup"><span data-stu-id="c83aa-121">Fetch file properties by paging StorageFile objects into the app.</span></span> <span data-ttu-id="c83aa-122">Durch das Auslagern der Dateien wird der Speicherverbrauch des Programms reduziert und die Reaktion verbessert.</span><span class="sxs-lookup"><span data-stu-id="c83aa-122">Paging the files in reduces the memory used by the app and improves its perceived responsiveness.</span></span>

### <a name="creating-the-query"></a><span data-ttu-id="c83aa-123">Erstellen der Abfrage</span><span class="sxs-lookup"><span data-stu-id="c83aa-123">Creating the query</span></span> 
<span data-ttu-id="c83aa-124">Um die Abfrage zu erstellen, verwenden wir ein QueryOptions-Objekt, um zu spezifizieren, dass die App daran interessiert ist, nur bestimmte Typen von Bilddateien aufzulisten und mit Windows Information Protection (System.Security.EncryptionOwners) geschützte Dateien herauszufiltern.</span><span class="sxs-lookup"><span data-stu-id="c83aa-124">To build the query, we use a QueryOptions object to specify that the app is interested in enumerating only certain types of images files and to filter out files protected with Windows Information Protection (System.Security.EncryptionOwners).</span></span> 

<span data-ttu-id="c83aa-125">Es ist wichtig, die Eigenschaften einzustellen, auf die die Anwendung über [QueryOptions.SetPropertyPrefetch](https://docs.microsoft.com/uwp/api/windows.storage.search.queryoptions.setpropertyprefetch) zugreifen soll.</span><span class="sxs-lookup"><span data-stu-id="c83aa-125">It is important to set the properties the app is going to access using [QueryOptions.SetPropertyPrefetch](https://docs.microsoft.com/uwp/api/windows.storage.search.queryoptions.setpropertyprefetch).</span></span> <span data-ttu-id="c83aa-126">Wenn die App auf eine Eigenschaft zugreift, die nicht vorgeladen ist, wird sie eine erhebliche Leistungseinbuße erleiden.</span><span class="sxs-lookup"><span data-stu-id="c83aa-126">If the app accesses a property that isn’t prefetched, it will incur a significant performance penalty.</span></span>

<span data-ttu-id="c83aa-127">[OnlyUseIndexerAndOptimzeForIndexedProperties](https://docs.microsoft.com/uwp/api/Windows.Storage.Search.IndexerOption) weist das System an, die Ergebnisse so schnell wie möglich zurückzuliefern, aber nur die in [SetPropertyPrefetch](https://docs.microsoft.com/uwp/api/windows.storage.search.queryoptions.setpropertyprefetch) angegebenen Eigenschaften zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="c83aa-127">Setting [IndexerOption.OnlyUseIndexerAndOptimzeForIndexedProperties](https://docs.microsoft.com/uwp/api/Windows.Storage.Search.IndexerOption) tells the system to return results as quickly as possible, but to only include the properties specified in [SetPropertyPrefetch](https://docs.microsoft.com/uwp/api/windows.storage.search.queryoptions.setpropertyprefetch).</span></span> 

### <a name="paging-in-the-results"></a><span data-ttu-id="c83aa-128">Paging in den Ergebnissen</span><span class="sxs-lookup"><span data-stu-id="c83aa-128">Paging in the results</span></span> 
<span data-ttu-id="c83aa-129">Benutzer können Tausende oder Millionen von Dateien in ihrer Bilderbibliothek haben, so dass der Aufruf von [GetFilesAsync](https://docs.microsoft.com/uwp/api/windows.storage.search.storagefilequeryresult.getfilesasync) ihren Rechner überfordern würde, weil es eine StorageFile für jedes Bild erstellt.</span><span class="sxs-lookup"><span data-stu-id="c83aa-129">Users may have thousands or millions of files in their pictures library, so calling [GetFilesAsync](https://docs.microsoft.com/uwp/api/windows.storage.search.storagefilequeryresult.getfilesasync) would overwhelm their machine because it creates a StorageFile for each image.</span></span> <span data-ttu-id="c83aa-130">Dies kann dadurch gelöst werden, dass eine feste Anzahl von StorageFiles auf einmal erstellt wird, diese in das UI verarbeitet werden und der Speicher freigegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c83aa-130">This can be solved by creating a fixed number of StorageFiles at one time, processing them into the UI, and then releasing the memory.</span></span> 

<span data-ttu-id="c83aa-131">In unserem Beispiel tun wir dies, indem wir [StorageFileQueryResult.GetFilesAsync(UInt32 StartIndex, UInt32 maxNumberOfItems)](https://docs.microsoft.com/uwp/api/windows.storage.search.storagefilequeryresult.getfilesasync) verwenden, um jeweils nur 100 Dateien gleichzeitig zu holen.</span><span class="sxs-lookup"><span data-stu-id="c83aa-131">In our example, we do this by using [StorageFileQueryResult.GetFilesAsync(UInt32 StartIndex, UInt32 maxNumberOfItems)](https://docs.microsoft.com/uwp/api/windows.storage.search.storagefilequeryresult.getfilesasync) to only fetch 100 files at a time.</span></span> <span data-ttu-id="c83aa-132">Das Programm verarbeitet dann die Dateien und erlaubt dem Betriebssystem, den Speicher wieder freizugeben.</span><span class="sxs-lookup"><span data-stu-id="c83aa-132">The app will then process the files and allow the OS to release that memory afterwards.</span></span> <span data-ttu-id="c83aa-133">Diese Technik begrenzen den maximalen Speicher der App und stellt sicher, dass das System reaktionsschnell bleibt.</span><span class="sxs-lookup"><span data-stu-id="c83aa-133">This technique caps the maximum memory of the app and ensures the system stays responsive.</span></span> <span data-ttu-id="c83aa-134">Natürlich müssen Sie die Anzahl der zurückgesendeten Dateien für Ihr Szenario anpassen. Aber um ein reaktionsschnelles Erlebnis für alle Benutzer zu gewährleisten, ist es empfehlenswert, nicht mehr als 500 Dateien auf einmal zu holen.</span><span class="sxs-lookup"><span data-stu-id="c83aa-134">Of course, you will need to adjust the number of files returned for your scenario, but to ensure a responsive experience for all users, it's recommended to not fetch more than 500 files at one time.</span></span>


**<span data-ttu-id="c83aa-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c83aa-135">Example</span></span>**  
```csharp
StorageFolder folderToEnumerate = KnownFolders.PicturesLibrary; 
// Check if the folder is indexed before doing anything. 
IndexedState folderIndexedState = await folderToEnumerate.GetIndexedStateAsync(); 
if (folderIndexedState == IndexedState.NotIndexed || folderIndexedState == IndexedState.Unknown) 
{ 
    // Only possible in indexed directories.  
    return; 
} 
 
QueryOptions picturesQuery = new QueryOptions() 
{ 
    FolderDepth = FolderDepth.Deep, 
    // Filter out all files that have WIP enabled
    ApplicationSearchFilter = "System.Security.EncryptionOwners:[]", 
    IndexerOption = IndexerOption.OnlyUseIndexerAndOptimizeForIndexedProperties 
}; 

picturesQuery.FileTypeFilter.Add(".jpg"); 
string[] otherProperties = new string[] 
{ 
    SystemProperties.GPS.LatitudeDecimal, 
    SystemProperties.GPS.LongitudeDecimal 
}; 
 
picturesQuery.SetPropertyPrefetch(PropertyPrefetchOptions.BasicProperties | PropertyPrefetchOptions.ImageProperties, 
                                    otherProperties); 
SortEntry sortOrder = new SortEntry() 
{ 
    AscendingOrder = true, 
    PropertyName = "System.FileName" // FileName property is used as an example. Any property can be used here.  
}; 
picturesQuery.SortOrder.Add(sortOrder); 
 
// Create the query and get the results 
uint index = 0; 
const uint stepSize = 100; 
if (!folderToEnumerate.AreQueryOptionsSupported(picturesQuery)) 
{ 
    log("Querying for a sort order is not supported in this location"); 
    picturesQuery.SortOrder.Clear(); 
} 
StorageFileQueryResult queryResult = folderToEnumerate.CreateFileQueryWithOptions(picturesQuery); 
IReadOnlyList<StorageFile> images = await queryResult.GetFilesAsync(index, stepSize); 
while (images.Count != 0 || index < 10000) 
{ 
    foreach (StorageFile file in images) 
    { 
        // With the OnlyUseIndexerAndOptimizeForIndexedProperties set, this won't  
        // be async. It will run synchronously. 
        var imageProps = await file.Properties.GetImagePropertiesAsync(); 
 
        // Build the UI 
        log(String.Format("{0} at {1}, {2}", 
                    file.Path, 
                    imageProps.Latitude, 
                    imageProps.Longitude)); 
    } 
    index += stepSize; 
    images = await queryResult.GetFilesAsync(index, stepSize); 
} 
```

### <a name="results"></a><span data-ttu-id="c83aa-136">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="c83aa-136">Results</span></span> 
<span data-ttu-id="c83aa-137">Die resultierenden StorageFile-Dateien enthalten nur die angeforderten Eigenschaften, werden aber 10-mal schneller zurückgegeben als die anderen IndexerOption.</span><span class="sxs-lookup"><span data-stu-id="c83aa-137">The resulting StorageFile files only contain the properties requested, but are returned 10 times faster compared to the other IndexerOptions.</span></span><span data-ttu-id="c83aa-138">Die Anwendung kann weiterhin Zugriff auf Eigenschaften beantragen, die nicht bereits in der Abfrage enthalten sind, aber es gibt eine Leistungseinbuße, um die Datei zu öffnen und diese Eigenschaften abzurufen.</span><span class="sxs-lookup"><span data-stu-id="c83aa-138">The app can still request access to properties not already included in the query, but there is a performance penalty to open the file and retrieve those properties.</span></span>  

## <a name="adding-folders-to-libraries"></a><span data-ttu-id="c83aa-139">Hinzufügen von Ordnern zu Libraries</span><span class="sxs-lookup"><span data-stu-id="c83aa-139">Adding folders to Libraries</span></span> 
<span data-ttu-id="c83aa-140">Apps können den Benutzer mittels [StorageLibrary.RequestAddFolderAsync](https://docs.microsoft.com/uwp/api/Windows.Storage.StorageLibrary.RequestAddFolderAsync) auffordern, den Speicherort zum Index hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c83aa-140">Apps can request the user to add the location to the index using [StorageLibrary.RequestAddFolderAsync](https://docs.microsoft.com/uwp/api/Windows.Storage.StorageLibrary.RequestAddFolderAsync).</span></span> <span data-ttu-id="c83aa-141">Sobald der Speicherort einmal enthalten ist, wird er automatisch indiziert und Apps können diese Technik verwenden, um die Dateien aufzuzählen.</span><span class="sxs-lookup"><span data-stu-id="c83aa-141">Once the location is included, it will be automatically indexed and apps can use this technique to enumerate the files.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="c83aa-142">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="c83aa-142">See also</span></span>
[<span data-ttu-id="c83aa-143">QueryOptions-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="c83aa-143">QueryOptions API Reference</span></span>](https://docs.microsoft.com/uwp/api/windows.storage.search.queryoptions)  
[<span data-ttu-id="c83aa-144">Aufzählen und Abfragen von Dateien und Ordnern</span><span class="sxs-lookup"><span data-stu-id="c83aa-144">Enumerate and query files and folders</span></span>](https://docs.microsoft.com/windows/uwp/files/quickstart-listing-files-and-folders)  
[<span data-ttu-id="c83aa-145">Berechtigungen für den Dateizugriff</span><span class="sxs-lookup"><span data-stu-id="c83aa-145">File access permissions</span></span>](https://docs.microsoft.com/windows/uwp/files/file-access-permissions)  
[<span data-ttu-id="c83aa-146">Exemplarische Vorgehensweise zum schnellen Zugriff auf Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="c83aa-146">Fast Property Access Walkthrough</span></span>](https://blogs.msdn.microsoft.com/adamdwilson/2017/12/20/fast-file-enumeration-with-partially-initialized-storagefiles/)
 
 
