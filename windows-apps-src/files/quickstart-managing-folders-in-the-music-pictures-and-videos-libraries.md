---
author: laurenhughes
ms.assetid: 1AE29512-7A7D-4179-ADAC-F02819AC2C39
title: Dateien und Ordner in den Musik-, Bild- und Videobibliotheken
description: Fügen Sie vorhandene Musik-, Bilder- oder Video-Ordner den entsprechenden Bibliotheken hinzu. Sie können auch Ordner aus Bibliotheken entfernen, die Liste der Ordner in einer Bibliothek abrufen und gespeicherte Fotos, Musik und Videos untersuchen.
ms.author: lahugh
ms.date: 06/18/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 1859d758806b4e92758decb40b8a30d02acb254d
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6667269"
---
# <a name="files-and-folders-in-the-music-pictures-and-videos-libraries"></a><span data-ttu-id="d1320-105">Dateien und Ordner in den Musik-, Bild- und Videobibliotheken</span><span class="sxs-lookup"><span data-stu-id="d1320-105">Files and folders in the Music, Pictures, and Videos libraries</span></span>

<span data-ttu-id="d1320-106">Fügen Sie vorhandene Musik-, Bilder- oder Video-Ordner den entsprechenden Bibliotheken hinzu.</span><span class="sxs-lookup"><span data-stu-id="d1320-106">Add existing folders of music, pictures, or videos to the corresponding libraries.</span></span> <span data-ttu-id="d1320-107">Sie können auch Ordner aus Bibliotheken entfernen, die Liste der Ordner in einer Bibliothek abrufen und gespeicherte Fotos, Musik und Videos untersuchen.</span><span class="sxs-lookup"><span data-stu-id="d1320-107">You can also remove folders from libraries, get the list of folders in a library, and discover stored photos, music, and videos.</span></span>

<span data-ttu-id="d1320-108">Eine Bibliothek ist eine virtuelle Sammlung von Ordnern, die standardmäßig einen bekannten Ordner sowie alle anderen Ordner enthält, die der Benutzer mithilfe Ihrer App oder einer der integrierten Apps zur Bibliothek hinzugefügt hat.</span><span class="sxs-lookup"><span data-stu-id="d1320-108">A library is a virtual collection of folders, which includes a known folder by default plus any other folders the user has added to the library by using your app or one of the built-in apps.</span></span> <span data-ttu-id="d1320-109">Die Bildbibliothek enthält z.B. standardmäßig den bekannten Ordner „Bilder“.</span><span class="sxs-lookup"><span data-stu-id="d1320-109">For example, the Pictures library includes the Pictures known folder by default.</span></span> <span data-ttu-id="d1320-110">Der Benutzer kann mithilfe Ihrer App oder der integrierten Fotos-App Ordner zur Bildbibliothek hinzufügen oder aus ihr entfernen.</span><span class="sxs-lookup"><span data-stu-id="d1320-110">The user can add folders to, or remove them from, the Pictures library by using your app or the built-in Photos app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1320-111">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d1320-111">Prerequisites</span></span>


-   **<span data-ttu-id="d1320-112">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="d1320-112">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="d1320-113">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span><span class="sxs-lookup"><span data-stu-id="d1320-113">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span></span> <span data-ttu-id="d1320-114">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span><span class="sxs-lookup"><span data-stu-id="d1320-114">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span></span>

-   **<span data-ttu-id="d1320-115">Zugriffsberechtigungen für den Speicherort</span><span class="sxs-lookup"><span data-stu-id="d1320-115">Access permissions to the location</span></span>**

    <span data-ttu-id="d1320-116">Öffnen Sie die App-Manifestdatei im Manifest-Designer in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1320-116">In Visual Studio, open the app manifest file in Manifest Designer.</span></span> <span data-ttu-id="d1320-117">Wählen Sie auf der Seite **Funktionen** die Bibliotheken aus, die Ihre App verwaltet.</span><span class="sxs-lookup"><span data-stu-id="d1320-117">On the **Capabilities** page, select the libraries that your app manages.</span></span>

    -   **<span data-ttu-id="d1320-118">Musikbibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-118">Music Library</span></span>**
    -   **<span data-ttu-id="d1320-119">Bildbibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-119">Pictures Library</span></span>**
    -   **<span data-ttu-id="d1320-120">Videobibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-120">Videos Library</span></span>**

    <span data-ttu-id="d1320-121">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](file-access-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="d1320-121">To learn more, see [File access permissions](file-access-permissions.md).</span></span>

## <a name="get-a-reference-to-a-library"></a><span data-ttu-id="d1320-122">Abrufen eines Verweises auf eine Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-122">Get a reference to a library</span></span>

> [!NOTE]
> <span data-ttu-id="d1320-123">Denken Sie daran, die Funktion entsprechend zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="d1320-123">Remember to declare the appropriate capability.</span></span> <span data-ttu-id="d1320-124">Weitere Informationen finden Sie unter [Deklarationen für App-Funktionen](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span><span class="sxs-lookup"><span data-stu-id="d1320-124">See [App capability declarations](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) for more information.</span></span>
 

<span data-ttu-id="d1320-125">Rufen Sie die [**StorageLibrary.GetLibraryAsync**](https://msdn.microsoft.com/library/windows/apps/dn251725)-Methode auf, um einen Verweis auf die Musik-, Bilder- oder Videobibliothek des Benutzers zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d1320-125">To get a reference to the user's Music, Pictures, or Video library, call the [**StorageLibrary.GetLibraryAsync**](https://msdn.microsoft.com/library/windows/apps/dn251725) method.</span></span> <span data-ttu-id="d1320-126">Geben Sie den entsprechenden Wert der [**KnownLibraryId**](https://msdn.microsoft.com/library/windows/apps/dn298399)-Enumeration ein.</span><span class="sxs-lookup"><span data-stu-id="d1320-126">Provide the corresponding value from the [**KnownLibraryId**](https://msdn.microsoft.com/library/windows/apps/dn298399) enumeration.</span></span>

-   [**<span data-ttu-id="d1320-127">KnownLibraryId.Music</span><span class="sxs-lookup"><span data-stu-id="d1320-127">KnownLibraryId.Music</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227155)
-   [**<span data-ttu-id="d1320-128">KnownLibraryId.Pictures</span><span class="sxs-lookup"><span data-stu-id="d1320-128">KnownLibraryId.Pictures</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227156)
-   [**<span data-ttu-id="d1320-129">KnownLibraryId.Videos</span><span class="sxs-lookup"><span data-stu-id="d1320-129">KnownLibraryId.Videos</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227159)

```cs
var myPictures = await Windows.Storage.StorageLibrary.GetLibraryAsync(Windows.Storage.KnownLibraryId.Pictures);
```

## <a name="get-the-list-of-folders-in-a-library"></a><span data-ttu-id="d1320-130">Abrufen der Liste der Ordner in einer Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-130">Get the list of folders in a library</span></span>


<span data-ttu-id="d1320-131">Um die Liste der Ordner in einer Bibliothek abzurufen, rufen den Wert der [**StorageLibrary.Folders**](https://msdn.microsoft.com/library/windows/apps/dn251724)-Eigenschaft ab.</span><span class="sxs-lookup"><span data-stu-id="d1320-131">To get the list of folders in a library, get the value of the [**StorageLibrary.Folders**](https://msdn.microsoft.com/library/windows/apps/dn251724) property.</span></span>

```cs
using Windows.Foundation.Collections;
IObservableVector<Windows.Storage.StorageFolder> myPictureFolders = myPictures.Folders;
```

## <a name="get-the-folder-in-a-library-where-new-files-are-saved-by-default"></a><span data-ttu-id="d1320-132">Abrufen des Ordners in einer Bibliothek, in den neue Dateien standardmäßig gespeichert werden</span><span class="sxs-lookup"><span data-stu-id="d1320-132">Get the folder in a library where new files are saved by default</span></span>


<span data-ttu-id="d1320-133">Um den Ordner in einer Bibliothek abzurufen, in den neue Dateien standardmäßig gespeichert werden, rufen Sie den Wert der [**StorageLibrary.SaveFolder**](https://msdn.microsoft.com/library/windows/apps/dn251728)-Eigenschaft ab.</span><span class="sxs-lookup"><span data-stu-id="d1320-133">To get the folder in a library where new files are saved by default, get the value of the [**StorageLibrary.SaveFolder**](https://msdn.microsoft.com/library/windows/apps/dn251728) property.</span></span>

```cs
Windows.Storage.StorageFolder savePicturesFolder = myPictures.SaveFolder;
```

## <a name="add-an-existing-folder-to-a-library"></a><span data-ttu-id="d1320-134">Hinzufügen eines vorhandenen Ordners zu einer Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-134">Add an existing folder to a library</span></span>

<span data-ttu-id="d1320-135">Um einen Ordner zu einer Bibliothek hinzuzufügen, rufen Sie [**StorageLibrary.RequestAddFolderAsync**](https://msdn.microsoft.com/library/windows/apps/dn251726) auf.</span><span class="sxs-lookup"><span data-stu-id="d1320-135">To add a folder to a library, you call the [**StorageLibrary.RequestAddFolderAsync**](https://msdn.microsoft.com/library/windows/apps/dn251726).</span></span> <span data-ttu-id="d1320-136">Das Aufrufen dieser Methode führt beispielsweise bei der Bildbibliothek zur Anzeige einer Ordnerauswahl für den Benutzer, die die Schaltfläche zum **Hinzufügen dieses Ordners zu Bildern** umfasst.</span><span class="sxs-lookup"><span data-stu-id="d1320-136">Taking the Pictures Library as an example, calling this method causes a folder picker to be shown to the user with an **Add this folder to Pictures** button.</span></span> <span data-ttu-id="d1320-137">Wenn der Benutzer einen Ordner auswählt, dann verbleibt er am ursprünglichen Speicherort auf dem Datenträger und wird zu einem Element in der [**StorageLibrary.Folders**](https://msdn.microsoft.com/library/windows/apps/dn251724)-Eigenschaft (und in der integrierten Fotos-App). Der Ordner wird aber nicht im Datei-Explorer als untergeordnetes Element des Ordners „Bilder“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d1320-137">If the user picks a folder then the folder remains in its original location on disk and it becomes an item in the [**StorageLibrary.Folders**](https://msdn.microsoft.com/library/windows/apps/dn251724) property (and in the built-in Photos app), but the folder does not appear as a child of the Pictures folder in File Explorer.</span></span>


```cs
Windows.Storage.StorageFolder newFolder = await myPictures.RequestAddFolderAsync();
```

## <a name="remove-a-folder-from-a-library"></a><span data-ttu-id="d1320-138">Entfernen eines Ordners aus einer Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-138">Remove a folder from a library</span></span>

<span data-ttu-id="d1320-139">Rufen Sie zum Entfernen eines Ordners aus einer Bibliothek die [**StorageLibrary.RequestRemoveFolderAsync**](https://msdn.microsoft.com/library/windows/apps/dn251727)-Methode auf, und geben Sie den zu entfernenden Ordner an.</span><span class="sxs-lookup"><span data-stu-id="d1320-139">To remove a folder from a library, call the [**StorageLibrary.RequestRemoveFolderAsync**](https://msdn.microsoft.com/library/windows/apps/dn251727) method and specify the folder to be removed.</span></span> <span data-ttu-id="d1320-140">Sie können [**StorageLibrary.Folders**](https://msdn.microsoft.com/library/windows/apps/dn251724) und ein [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878)-Steuerelement (oder ähnliches) verwenden, damit der Benutzer einen zu entfernenden Ordner auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="d1320-140">You could use [**StorageLibrary.Folders**](https://msdn.microsoft.com/library/windows/apps/dn251724) and a [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878) control (or similar) for the user to select a folder to remove.</span></span>

<span data-ttu-id="d1320-141">Wenn Sie [**StorageLibrary.RequestRemoveFolderAsync**](https://msdn.microsoft.com/library/windows/apps/dn251727) aufrufen, wird dem Benutzer ein Bestätigungsdialogfeld angezeigt, das darüber informiert, dass der Ordner nicht länger unter „Bilder“ angezeigt, aber auch nicht gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="d1320-141">When you call [**StorageLibrary.RequestRemoveFolderAsync**](https://msdn.microsoft.com/library/windows/apps/dn251727), the user sees a confirmation dialog saying that the folder "won't appear in Pictures anymore, but won't be deleted."</span></span> <span data-ttu-id="d1320-142">Dies bedeutet, dass der Ordner am ursprünglichen Speicherort auf dem Datenträger verbleibt, aus der [**StorageLibrary.Folders**](https://msdn.microsoft.com/library/windows/apps/dn251724)-Eigenschaft entfernt wird und nicht länger in der integrierten Fotos-App enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="d1320-142">What this means is that the folder remains in its original location on disk, is removed from the [**StorageLibrary.Folders**](https://msdn.microsoft.com/library/windows/apps/dn251724) property, and will no longer included in the built-in Photos app.</span></span>

<span data-ttu-id="d1320-143">Im folgenden Beispiel wird davon ausgegangen, dass der Benutzer den zu entfernenden Ordner aus einem [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878)-Steuerelement namens **lvPictureFolders** ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="d1320-143">The following example assumes that the user has selected the folder to remove from a [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878) control named **lvPictureFolders**.</span></span>


```cs
bool result = await myPictures.RequestRemoveFolderAsync(folder);
```

## <a name="get-notified-of-changes-to-the-list-of-folders-in-a-library"></a><span data-ttu-id="d1320-144">Empfangen von Benachrichtigungen über Änderungen an der Liste der Ordner in einer Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-144">Get notified of changes to the list of folders in a library</span></span>


<span data-ttu-id="d1320-145">Um über Änderungen an der Liste der Ordner in einer Bibliothek benachrichtigt zu werden, registrieren Sie einen Handler für das [**StorageLibrary.DefinitionChanged**](https://msdn.microsoft.com/library/windows/apps/dn251723)-Ereignis der Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="d1320-145">To get notified about changes to the list of folders in a library, register a handler for the [**StorageLibrary.DefinitionChanged**](https://msdn.microsoft.com/library/windows/apps/dn251723) event of the library.</span></span>


```cs
myPictures.DefinitionChanged += MyPictures_DefinitionChanged;

void HandleDefinitionChanged(Windows.Storage.StorageLibrary sender, object args)
{
    // ...
}
```

## <a name="media-library-folders"></a><span data-ttu-id="d1320-146">Medienbibliothekordner</span><span class="sxs-lookup"><span data-stu-id="d1320-146">Media library folders</span></span>


<span data-ttu-id="d1320-147">Ein Gerät bietet fünf vordefinierte Speicherorte, an denen Benutzer und Apps Mediendateien speichern können.</span><span class="sxs-lookup"><span data-stu-id="d1320-147">A device provides five predefined locations for users and apps to store media files.</span></span> <span data-ttu-id="d1320-148">Vorinstallierte Apps speichern an diesen Speicherorten sowohl von Benutzern erstellte Medien als auch heruntergeladene Medien.</span><span class="sxs-lookup"><span data-stu-id="d1320-148">Built-in apps store both user-created media and downloaded media in these locations.</span></span>

<span data-ttu-id="d1320-149">Die Speicherorte lauten:</span><span class="sxs-lookup"><span data-stu-id="d1320-149">The locations are:</span></span>

-   <span data-ttu-id="d1320-150">Ordner **Bilder**.</span><span class="sxs-lookup"><span data-stu-id="d1320-150">**Pictures** folder.</span></span> <span data-ttu-id="d1320-151">Enthält Bilder.</span><span class="sxs-lookup"><span data-stu-id="d1320-151">Contains pictures.</span></span>

    -   <span data-ttu-id="d1320-152">Ordner **Eigene Aufnahmen**.</span><span class="sxs-lookup"><span data-stu-id="d1320-152">**Camera Roll** folder.</span></span> <span data-ttu-id="d1320-153">Enthält Fotos und Videos, die mit der integrierten Kamera aufgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="d1320-153">Contains photos and video from the built-in camera.</span></span>

    -   <span data-ttu-id="d1320-154">Ordner **Gespeicherte Bilder**.</span><span class="sxs-lookup"><span data-stu-id="d1320-154">**Saved Pictures** folder.</span></span> <span data-ttu-id="d1320-155">Enthält Bilder, die der Benutzer aus anderen Apps gespeichert hat.</span><span class="sxs-lookup"><span data-stu-id="d1320-155">Contains pictures that the user has saved from other apps.</span></span>

-   <span data-ttu-id="d1320-156">Ordner **Musik**.</span><span class="sxs-lookup"><span data-stu-id="d1320-156">**Music** folder.</span></span> <span data-ttu-id="d1320-157">Enthält Songs, Podcasts und Hörbücher.</span><span class="sxs-lookup"><span data-stu-id="d1320-157">Contains songs, podcasts, and audio books.</span></span>

-   <span data-ttu-id="d1320-158">Ordner **Video**.</span><span class="sxs-lookup"><span data-stu-id="d1320-158">**Video** folder.</span></span> <span data-ttu-id="d1320-159">Enthält Videos.</span><span class="sxs-lookup"><span data-stu-id="d1320-159">Contains videos.</span></span>

<span data-ttu-id="d1320-160">Mediendateien können von Benutzern und Apps auch außerhalb der Medienbibliothekordner auf der SD-Karte gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="d1320-160">Users or apps may also store media files outside the media library folders on the SD card.</span></span> <span data-ttu-id="d1320-161">Durchsuchen Sie den Inhalt der SD-Karte, um eine Mediendatei auf der SD-Karte auf zuverlässige Weise zu finden, oder bitten Sie den Benutzer, mithilfe einer Dateiauswahl auf die Datei zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="d1320-161">To find a media file reliably on the SD card, scan the contents of the SD card, or ask the user to locate the file by using a file picker.</span></span> <span data-ttu-id="d1320-162">Weitere Informationen finden Sie unter [Zugreifen auf die SD-Karte](access-the-sd-card.md).</span><span class="sxs-lookup"><span data-stu-id="d1320-162">For more info, see [Access the SD card](access-the-sd-card.md).</span></span>

## <a name="querying-the-media-libraries"></a><span data-ttu-id="d1320-163">Abfragen der Medienbibliotheken</span><span class="sxs-lookup"><span data-stu-id="d1320-163">Querying the media libraries</span></span>

<span data-ttu-id="d1320-164">Um eine Sammlung von Dateien zu erhalten, geben Sie die Bibliothek und den Typ der gewünschten Dateien an.</span><span class="sxs-lookup"><span data-stu-id="d1320-164">To get a collection of files, specify the library and the type of files that you want.</span></span>

```cs
using Windows.Storage;
using Windows.Storage.Search;

private async void getSongs()
{
    QueryOptions queryOption = new QueryOptions
        (CommonFileQuery.OrderByTitle, new string[] { ".mp3", ".mp4", ".wma" });

    queryOption.FolderDepth = FolderDepth.Deep;

    Queue<IStorageFolder> folders = new Queue<IStorageFolder>();

    var files = await KnownFolders.MusicLibrary.CreateFileQueryWithOptions
      (queryOption).GetFilesAsync();

    foreach (var file in files)
    {
        // do something with the music files
    }
}
```

### <a name="query-results-include-both-internal-and-removable-storage"></a><span data-ttu-id="d1320-165">Abfrageergebnisse umfassen sowohl internen Speicher als auch Wechselmedien</span><span class="sxs-lookup"><span data-stu-id="d1320-165">Query results include both internal and removable storage</span></span>

<span data-ttu-id="d1320-166">Benutzer können angeben, dass Dateien standardmäßig auf der optionalen SD-Karte gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="d1320-166">Users can choose to store files by default on the optional SD card.</span></span> <span data-ttu-id="d1320-167">Für Apps kann festgelegt werden, dass Dateien nicht auf der SD-Karte gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="d1320-167">Apps, however, can opt out of allowing files to be stored on the SD card.</span></span> <span data-ttu-id="d1320-168">Daher können die Medienbibliotheken auf den internen Speicher und die SD-Karte des Geräts aufgeteilt werden.</span><span class="sxs-lookup"><span data-stu-id="d1320-168">As a result, the media libraries can be split across the device's internal storage and the SD card.</span></span>

<span data-ttu-id="d1320-169">Sie müssen keinen zusätzlichen Code schreiben, um diese Möglichkeit bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="d1320-169">You don't have to write additional code to handle this possibility.</span></span> <span data-ttu-id="d1320-170">In den Methoden im [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/br227346)-Namespace, mit denen bekannte Ordner abgefragt werden, sind die Abfrageergebnisse beider Speicherorte transparent kombiniert.</span><span class="sxs-lookup"><span data-stu-id="d1320-170">The methods in the [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/br227346) namespace that query known folders transparently combine the query results from both locations.</span></span> <span data-ttu-id="d1320-171">Sie müssen die **removableStorage**-Funktion in der App-Manifestdatei nicht angeben, um diese kombinierten Ergebnisse zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d1320-171">You don't have to specify the **removableStorage** capability in the app manifest file to get these combined results, either.</span></span>

<span data-ttu-id="d1320-172">Beachten Sie den Status des Gerätespeichers, der in der folgenden Abbildung dargestellt ist:</span><span class="sxs-lookup"><span data-stu-id="d1320-172">Consider the state of the device's storage shown in the following image:</span></span>

![Bilder auf dem Smartphone und der SD-Karte](images/phone-media-locations.png)

<span data-ttu-id="d1320-174">Wenn Sie den Inhalt der Bildbibliothek abfragen, indem Sie `await KnownFolders.PicturesLibrary.GetFilesAsync()` aufrufen, ist sowohl „internalPic.jpg“ als auch „SDPic.jpg“ in den Ergebnissen enthalten.</span><span class="sxs-lookup"><span data-stu-id="d1320-174">If you query the contents of the Pictures Library by calling `await KnownFolders.PicturesLibrary.GetFilesAsync()`, the results include both internalPic.jpg and SDPic.jpg.</span></span>


## <a name="working-with-photos"></a><span data-ttu-id="d1320-175">Verwenden von Fotos</span><span class="sxs-lookup"><span data-stu-id="d1320-175">Working with photos</span></span>

<span data-ttu-id="d1320-176">Auf Geräten, auf denen jedes Bild von der Kamera sowohl in niedriger als auch in hoher Auflösung gespeichert wird, wird bei tiefen Abfragen nur das Bild mit niedriger Auflösung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="d1320-176">On devices where the camera saves both a low-resolution image and a high-resolution image of every picture, the deep queries return only the low-resolution image.</span></span>

<span data-ttu-id="d1320-177">Für die Ordner „Eigene Aufnahmen“ und „Gespeicherte Bilder“ werden keine tiefen Abfragen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d1320-177">The Camera Roll and the Saved Pictures folder do not support the deep queries.</span></span>

**<span data-ttu-id="d1320-178">Öffnen eines Fotos in der App, mit der es aufgenommen wurde</span><span class="sxs-lookup"><span data-stu-id="d1320-178">Opening a photo in the app that captured it</span></span>**

<span data-ttu-id="d1320-179">Wenn Sie es Benutzern ermöglichen möchten, ein Foto später erneut in der App zu öffnen, mit der es aufgenommen wurde, können Sie die **CreatorAppId** mit den Metadaten des Fotos speichern. Verwenden Sie hierzu ähnlichen Code wie im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="d1320-179">If you want to let the user open a photo again later in the app that captured it, you can save the **CreatorAppId** with the photo's metadata by using code similar to the following example.</span></span> <span data-ttu-id="d1320-180">In diesem Beispiel ist **testPhoto** eine [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171).</span><span class="sxs-lookup"><span data-stu-id="d1320-180">In this example, **testPhoto** is a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171).</span></span>

```cs
IDictionary<string, object> propertiesToSave = new Dictionary<string, object>();

propertiesToSave.Add("System.CreatorOpenWithUIOptions", 1);
propertiesToSave.Add("System.CreatorAppId", appId);

testPhoto.Properties.SavePropertiesAsync(propertiesToSave).AsyncWait();   
```

## <a name="using-stream-methods-to-add-a-file-to-a-media-library"></a><span data-ttu-id="d1320-181">Verwenden von Datenstrommethoden zum Hinzufügen einer Datei zur Medienbibliothek</span><span class="sxs-lookup"><span data-stu-id="d1320-181">Using stream methods to add a file to a media library</span></span>

<span data-ttu-id="d1320-182">Wenn Sie auf eine Medienbibliothek zugreifen, indem Sie einen bekannten Ordner wie **KnownFolders.PictureLibrary** verwenden, und der Medienbibliothek mithilfe von Datenstrommethoden eine Datei hinzufügen, müssen Sie darauf achten, alle von Ihrem Code geöffneten Datenströme wieder zu schließen.</span><span class="sxs-lookup"><span data-stu-id="d1320-182">When you access a media library by using a known folder such as **KnownFolders.PictureLibrary**, and you use stream methods to add a file to the media library, you have to make sure to close all the streams that your code opens.</span></span> <span data-ttu-id="d1320-183">Andernfalls wird die Datei der Medienbibliothek mit diesen Methoden nicht wie erwartet hinzugefügt, weil mindestens ein Stream weiterhin über einen Handle für die Datei verfügt.</span><span class="sxs-lookup"><span data-stu-id="d1320-183">Otherwise these methods fail to add the file to the media library as expected because at least one stream still has a handle to the file.</span></span>

<span data-ttu-id="d1320-184">Wenn Sie beispielsweise den folgenden Code ausführen, wird die Datei nicht der Medienbibliothek hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d1320-184">For example, when you run the following code, the file is not added to the media library.</span></span> <span data-ttu-id="d1320-185">In der Codezeile `using (var destinationStream = (await destinationFile.OpenAsync(FileAccessMode.ReadWrite)).GetOutputStreamAt(0))` wird sowohl mit der **OpenAsync**-Methode als auch mit der **GetOutputStreamAt**-Methode ein Datenstrom geöffnet.</span><span class="sxs-lookup"><span data-stu-id="d1320-185">In the line of code, `using (var destinationStream = (await destinationFile.OpenAsync(FileAccessMode.ReadWrite)).GetOutputStreamAt(0))`, both the **OpenAsync** method and the **GetOutputStreamAt** method open a stream.</span></span> <span data-ttu-id="d1320-186">Es wird aber nur der mit der **GetOutputStreamAt**-Methode geöffnete Datenstrom aufgrund der **using**-Anweisung wieder geschlossen.</span><span class="sxs-lookup"><span data-stu-id="d1320-186">However only the stream opened by the **GetOutputStreamAt** method is disposed as a result of the **using** statement.</span></span> <span data-ttu-id="d1320-187">Der andere Datenstrom bleibt geöffnet und verhindert das Speichern der Datei.</span><span class="sxs-lookup"><span data-stu-id="d1320-187">The other stream remains open and prevents saving the file.</span></span>

```cs
StorageFolder testFolder = await StorageFolder.GetFolderFromPathAsync(@"C:\test");
StorageFile sourceFile = await testFolder.GetFileAsync("TestImage.jpg");
StorageFile destinationFile = await KnownFolders.CameraRoll.CreateFileAsync("MyTestImage.jpg");
using (var sourceStream = (await sourceFile.OpenReadAsync()).GetInputStreamAt(0))
{
    using (var destinationStream = (await destinationFile.OpenAsync(FileAccessMode.ReadWrite)).GetOutputStreamAt(0))
    {
        await RandomAccessStream.CopyAndCloseAsync(sourceStream, destinationStream);
    }
}
```

<span data-ttu-id="d1320-188">Um Streammethoden erfolgreich zum Hinzufügen einer Datei zur Medienbibliothek zu verwenden, müssen Sie alle Datenströme schließen, die von Ihrem Code geöffnet werden. Dies ist im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d1320-188">To use stream methods successfully to add a file to the media library, make sure to close all the streams that your code opens, as shown in the following example.</span></span>

```cs
StorageFolder testFolder = await StorageFolder.GetFolderFromPathAsync(@"C:\test");
StorageFile sourceFile = await testFolder.GetFileAsync("TestImage.jpg");
StorageFile destinationFile = await KnownFolders.CameraRoll.CreateFileAsync("MyTestImage.jpg");

using (var sourceStream = await sourceFile.OpenReadAsync())
{
    using (var sourceInputStream = sourceStream.GetInputStreamAt(0))
    {
        using (var destinationStream = await destinationFile.OpenAsync(FileAccessMode.ReadWrite))
        {
            using (var destinationOutputStream = destinationStream.GetOutputStreamAt(0))
            {
                await RandomAccessStream.CopyAndCloseAsync(sourceInputStream, destinationStream);
            }
        }
    }
}
```
