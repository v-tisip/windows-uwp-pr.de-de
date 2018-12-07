---
ms.assetid: 3604524F-112A-474F-B0CA-0726DC8DB885
title: Ermitteln der Verfügbarkeit von Microsoft OneDrive-Dateien
description: Ermitteln Sie mithilfe der StorageFile.IsAvailable-Eigenschaft, ob eine Microsoft OneDrive-Datei verfügbar ist.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: e431694f3f0effb6fd5e7688b146109dfc1f5dc7
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8786389"
---
# <a name="determining-availability-of-microsoft-onedrive-files"></a><span data-ttu-id="500e2-104">Ermitteln der Verfügbarkeit von MicrosoftOneDrive-Dateien</span><span class="sxs-lookup"><span data-stu-id="500e2-104">Determining availability of Microsoft OneDrive files</span></span>


**<span data-ttu-id="500e2-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="500e2-105">Important APIs</span></span>**

-   [**<span data-ttu-id="500e2-106">FileIO-Klasse</span><span class="sxs-lookup"><span data-stu-id="500e2-106">FileIO class</span></span>**](https://msdn.microsoft.com/library/windows/apps/Hh701440)
-   [**<span data-ttu-id="500e2-107">StorageFile-Klasse</span><span class="sxs-lookup"><span data-stu-id="500e2-107">StorageFile class</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR227171)
-   [**<span data-ttu-id="500e2-108">StorageFile.IsAvailable-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="500e2-108">StorageFile.IsAvailable property</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx)

<span data-ttu-id="500e2-109">Ermitteln Sie mithilfe der [**StorageFile.IsAvailable**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx)-Eigenschaft, ob eine Microsoft OneDrive-Datei verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="500e2-109">Determine if a Microsoft OneDrive file is available using the [**StorageFile.IsAvailable**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx) property.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="500e2-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="500e2-110">Prerequisites</span></span>

-   **<span data-ttu-id="500e2-111">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="500e2-111">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="500e2-112">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/Mt187337).</span><span class="sxs-lookup"><span data-stu-id="500e2-112">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/Mt187337).</span></span> <span data-ttu-id="500e2-113">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/Mt187334).</span><span class="sxs-lookup"><span data-stu-id="500e2-113">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/Mt187334).</span></span>

-   **<span data-ttu-id="500e2-114">Deklaration der App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="500e2-114">App capabilty declarations</span></span>**

    <span data-ttu-id="500e2-115">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](file-access-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="500e2-115">See [File access permissions](file-access-permissions.md).</span></span>

## <a name="using-the-storagefileisavailable-property"></a><span data-ttu-id="500e2-116">Verwenden der StorageFile.IsAvailable-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="500e2-116">Using the StorageFile.IsAvailable property</span></span>

<span data-ttu-id="500e2-117">Benutzer können OneDrive-Dateien als „Offline verfügbar“ (Standardeinstellung) oder „Nur online verfügbar“ kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="500e2-117">Users are able to mark OneDrive files as either available-offline (default) or online-only.</span></span> <span data-ttu-id="500e2-118">Diese Funktion bietet Benutzern die Möglichkeit, große Dateien (z. B. Bilder und Videos) in ihren OneDrive-Speicher zu verschieben, als nur online verfügbar zu kennzeichnen und so Speicherplatz auf der Festplatte zu sparen (lokal wird nur eine Datei mit Metadaten gespeichert).</span><span class="sxs-lookup"><span data-stu-id="500e2-118">This capability enables users to move large files (such as pictures and videos) to their OneDrive, mark them as online-only, and save disk space (the only thing kept locally is a metadata file).</span></span>

<span data-ttu-id="500e2-119">[**StorageFile.IsAvailable**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx) wird verwendet, um zu ermitteln, ob eine Datei zurzeit verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="500e2-119">[**StorageFile.IsAvailable**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx), is used to determine if a file is currently available.</span></span> <span data-ttu-id="500e2-120">Die folgende Tabelle zeigt den Wert der **StorageFile.IsAvailable**-Eigenschaft in verschiedenen Szenarien.</span><span class="sxs-lookup"><span data-stu-id="500e2-120">The following table shows the value of the **StorageFile.IsAvailable** property in various scenarios.</span></span>

| <span data-ttu-id="500e2-121">Dateityp</span><span class="sxs-lookup"><span data-stu-id="500e2-121">Type of file</span></span>                              | <span data-ttu-id="500e2-122">Online</span><span class="sxs-lookup"><span data-stu-id="500e2-122">Online</span></span> | <span data-ttu-id="500e2-123">Getaktetes Netzwerk</span><span class="sxs-lookup"><span data-stu-id="500e2-123">Metered network</span></span>        | <span data-ttu-id="500e2-124">Offline</span><span class="sxs-lookup"><span data-stu-id="500e2-124">Offline</span></span> |
|-------------------------------------------|--------|------------------------|---------|
| <span data-ttu-id="500e2-125">Lokale Datei</span><span class="sxs-lookup"><span data-stu-id="500e2-125">Local file</span></span>                                | <span data-ttu-id="500e2-126">True</span><span class="sxs-lookup"><span data-stu-id="500e2-126">True</span></span>   | <span data-ttu-id="500e2-127">True</span><span class="sxs-lookup"><span data-stu-id="500e2-127">True</span></span>                   | <span data-ttu-id="500e2-128">True</span><span class="sxs-lookup"><span data-stu-id="500e2-128">True</span></span>    |
| <span data-ttu-id="500e2-129">Als "Offline verfügbar" gekennzeichnete OneDrive-Datei</span><span class="sxs-lookup"><span data-stu-id="500e2-129">OneDrive file marked as available-offline</span></span> | <span data-ttu-id="500e2-130">True</span><span class="sxs-lookup"><span data-stu-id="500e2-130">True</span></span>   | <span data-ttu-id="500e2-131">True</span><span class="sxs-lookup"><span data-stu-id="500e2-131">True</span></span>                   | <span data-ttu-id="500e2-132">True</span><span class="sxs-lookup"><span data-stu-id="500e2-132">True</span></span>    |
| <span data-ttu-id="500e2-133">Als "Nur online verfügbar" gekennzeichnete OneDrive-Datei</span><span class="sxs-lookup"><span data-stu-id="500e2-133">OneDrive file marked as online-only</span></span>       | <span data-ttu-id="500e2-134">True</span><span class="sxs-lookup"><span data-stu-id="500e2-134">True</span></span>   | <span data-ttu-id="500e2-135">Basierend auf Benutzereinstellungen</span><span class="sxs-lookup"><span data-stu-id="500e2-135">Based on user settings</span></span> | <span data-ttu-id="500e2-136">False</span><span class="sxs-lookup"><span data-stu-id="500e2-136">False</span></span>   |
| <span data-ttu-id="500e2-137">Netzwerkdatei</span><span class="sxs-lookup"><span data-stu-id="500e2-137">Network file</span></span>                              | <span data-ttu-id="500e2-138">True</span><span class="sxs-lookup"><span data-stu-id="500e2-138">True</span></span>   | <span data-ttu-id="500e2-139">Basierend auf Benutzereinstellungen</span><span class="sxs-lookup"><span data-stu-id="500e2-139">Based on user settings</span></span> | <span data-ttu-id="500e2-140">False</span><span class="sxs-lookup"><span data-stu-id="500e2-140">False</span></span>   |

 

<span data-ttu-id="500e2-141">Die folgenden Schritte zeigen, wie festgestellt wird, ob eine Datei momentan verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="500e2-141">The following steps illustrate how to determine if a file is currently available.</span></span>

1.  <span data-ttu-id="500e2-142">Deklarieren Sie eine für die Bibliothek, auf die Sie zugreifen möchten, geeignete Funktion.</span><span class="sxs-lookup"><span data-stu-id="500e2-142">Declare a capability appropriate for the library you want to access.</span></span>
2.  <span data-ttu-id="500e2-143">Schließen Sie den [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346)-Namespace ein.</span><span class="sxs-lookup"><span data-stu-id="500e2-143">Include the [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346) namespace.</span></span> <span data-ttu-id="500e2-144">Dieser Namespace enthält die Typen zum Verwalten von Dateien, Ordnern und Anwendungseinstellungen.</span><span class="sxs-lookup"><span data-stu-id="500e2-144">This namespace includes the types for managing files, folders, and application settings.</span></span> <span data-ttu-id="500e2-145">Außerdem enthält er den erforderlichen [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/BR227171)-Typ.</span><span class="sxs-lookup"><span data-stu-id="500e2-145">It also includes the needed [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/BR227171) type.</span></span>
3.  <span data-ttu-id="500e2-146">Beschaffen Sie ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/BR227171)-Objekt für die gewünschte Datei bzw. die gewünschten Dateien.</span><span class="sxs-lookup"><span data-stu-id="500e2-146">Acquire a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/BR227171) object for the desired file(s).</span></span> <span data-ttu-id="500e2-147">Wenn Sie eine Bibliothek aufzählen, können Sie zur Durchführung dieses Schritts die [**StorageFolder.CreateFileQuery**](https://msdn.microsoft.com/library/windows/apps/BR227252)-Methode und dann die [**GetFilesAsync**](https://msdn.microsoft.com/library/windows/apps/br227276.aspx)-Methode des sich ergebenden [**StorageFileQueryResult**](https://msdn.microsoft.com/library/windows/apps/BR208046)-Objekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="500e2-147">If you are enumerating a library, this step is usually accomplished by calling the [**StorageFolder.CreateFileQuery**](https://msdn.microsoft.com/library/windows/apps/BR227252) method and then calling the resulting [**StorageFileQueryResult**](https://msdn.microsoft.com/library/windows/apps/BR208046) object's [**GetFilesAsync**](https://msdn.microsoft.com/library/windows/apps/br227276.aspx) method.</span></span> <span data-ttu-id="500e2-148">Die **GetFilesAsync**-Methode gibt eine [IReadOnlyList](http://go.microsoft.com/fwlink/p/?LinkId=324970)-Sammlung mit **StorageFile**-Objekten zurück.</span><span class="sxs-lookup"><span data-stu-id="500e2-148">The **GetFilesAsync** method returns an [IReadOnlyList](http://go.microsoft.com/fwlink/p/?LinkId=324970) collection of **StorageFile** objects.</span></span>
4.  <span data-ttu-id="500e2-149">Nachdem Sie den Zugriff auf ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/BR227171)-Objekt eingerichtet haben, das die gewünschten Dateien darstellt, spiegelt der Wert der [**StorageFile.IsAvailable**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx)-Eigenschaft wider, ob die Datei verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="500e2-149">Once you have the access to a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/BR227171) object representing the desired file(s), the value of the [**StorageFile.IsAvailable**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx) property reflects whether or not the file is available.</span></span>

<span data-ttu-id="500e2-150">Die folgende generische Methode veranschaulicht, wie Sie einen beliebigen Ordner aufzählen und die Sammlung mit [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/BR227171)-Objekten für diesen Ordner zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="500e2-150">The following generic method illustrates how to enumerate any folder and return the collection of [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/BR227171) objects for that folder.</span></span> <span data-ttu-id="500e2-151">Die aufrufende Methode durchläuft dann die zurückgegebene Sammlung und verweist für jede Datei auf die [**StorageFile.IsAvailable**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="500e2-151">The calling method then iterates over the returned collection referencing the [**StorageFile.IsAvailable**](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.isavailable.aspx) property for each file.</span></span>

```cs
/// <summary>
/// Generic function that retrieves all files from the specified folder.
/// </summary>
/// <param name="folder">The folder to be searched.</param>
/// <returns>An IReadOnlyList collection containing the file objects.</returns>
async Task<System.Collections.Generic.IReadOnlyList<StorageFile>> GetLibraryFilesAsync(StorageFolder folder)
{
    var query = folder.CreateFileQuery();
    return await query.GetFilesAsync();
}

private async void CheckAvailabilityOfFilesInPicturesLibrary()
{
    // Determine availability of all files within Pictures library.
    var files = await GetLibraryFilesAsync(KnownFolders.PicturesLibrary);
    for (int i = 0; i < files.Count; i++)
    {
        StorageFile file = files[i];

        StringBuilder fileInfo = new StringBuilder();
        fileInfo.AppendFormat("{0} (on {1}) is {2}",
                    file.Name,
                    file.Provider.DisplayName,
                    file.IsAvailable ? "available" : "not available");
    }
}
```
