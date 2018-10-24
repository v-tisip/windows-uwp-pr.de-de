---
author: laurenhughes
ms.assetid: 12ECEA89-59D2-4BCE-B24C-5A4DD525E0C7
title: Zugriff auf Inhalte in der Heimnetzgruppe
description: Greifen Sie auf Inhalte zu, die sich im Heimnetzgruppenordner des Benutzers befinden, einschließlich Bildern, Musik und Videos.
ms.author: lahugh
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 79873d014c5ee735a509328d4a123f839831325b
ms.sourcegitcommit: 4b97117d3aff38db89d560502a3c372f12bb6ed5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "5440126"
---
# <a name="accessing-homegroup-content"></a><span data-ttu-id="7470e-104">Zugriff auf Inhalte in der Heimnetzgruppe</span><span class="sxs-lookup"><span data-stu-id="7470e-104">Accessing HomeGroup content</span></span>



**<span data-ttu-id="7470e-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="7470e-105">Important APIs</span></span>**

-   [**<span data-ttu-id="7470e-106">Windows.Storage.KnownFolders-Klasse</span><span class="sxs-lookup"><span data-stu-id="7470e-106">Windows.Storage.KnownFolders class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227151)

<span data-ttu-id="7470e-107">Greifen Sie auf Inhalte zu, die sich im Heimnetzgruppenordner des Benutzers befinden, einschließlich Bildern, Musik und Videos.</span><span class="sxs-lookup"><span data-stu-id="7470e-107">Access content stored in the user's HomeGroup folder, including pictures, music, and videos.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7470e-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="7470e-108">Prerequisites</span></span>

-   **<span data-ttu-id="7470e-109">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="7470e-109">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="7470e-110">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span><span class="sxs-lookup"><span data-stu-id="7470e-110">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span></span> <span data-ttu-id="7470e-111">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span><span class="sxs-lookup"><span data-stu-id="7470e-111">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span></span>

-   **<span data-ttu-id="7470e-112">Deklaration der App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="7470e-112">App capabilty declarations</span></span>**

    <span data-ttu-id="7470e-113">Damit auf Heimnetzgruppeninhalte zugegriffen werden kann, muss auf dem Computer des Benutzers eine Heimnetzgruppe eingerichtet sein, und Ihre App muss mindestens eine der folgenden Funktionen unterstützen: **picturesLibrary**, **musicLibrary** oder **videosLibrary**.</span><span class="sxs-lookup"><span data-stu-id="7470e-113">To access HomeGroup content, the user's machine must have a HomeGroup set up and your app must have at least one of the following capabilities: **picturesLibrary**, **musicLibrary**, or **videosLibrary**.</span></span> <span data-ttu-id="7470e-114">Wenn Ihre App auf den Heimnetzgruppenordner zugreift, sieht sie nur die Bibliotheken, die den im Manifest Ihrer App deklarierten Funktionen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="7470e-114">When your app accesses the HomeGroup folder, it will see only the libraries that correspond to the capabilities declared in your app's manifest.</span></span> <span data-ttu-id="7470e-115">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](file-access-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="7470e-115">To learn more, see [File access permissions](file-access-permissions.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="7470e-116">Inhalte der Dokumentbibliothek einer Heimnetzgruppe sind für Ihre App nicht sichtbar, unabhängig von den deklarierten Funktionen in ihrem Manifest und den Freigabeeinstellungen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="7470e-116">Content in the Documents library of a HomeGroup isn't visible to your app regardless of the capabilities declared in your app's manifest and regardless of the user's sharing settings.</span></span>     

-   **<span data-ttu-id="7470e-117">So wird's gemacht: Verwenden der Dateiauswahl</span><span class="sxs-lookup"><span data-stu-id="7470e-117">Understand how to use file pickers</span></span>**

    <span data-ttu-id="7470e-118">Normalerweise verwenden Sie die Dateiauswahl, um auf Dateien und Ordner in der Heimnetzgruppe zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="7470e-118">You typically use the file picker to access files and folders in the HomeGroup.</span></span> <span data-ttu-id="7470e-119">Informationen zur Verwendung der Dateiauswahl finden Sie unter [Öffnen von Dateien und Ordnern mit einer Auswahl](quickstart-using-file-and-folder-pickers.md).</span><span class="sxs-lookup"><span data-stu-id="7470e-119">To learn how to use the file picker, see [Open files and folders with a picker](quickstart-using-file-and-folder-pickers.md).</span></span>

-   **<span data-ttu-id="7470e-120">Datei- und Ordnerabfragen</span><span class="sxs-lookup"><span data-stu-id="7470e-120">Understand file and folder queries</span></span>**

    <span data-ttu-id="7470e-121">Sie können Abfragen dazu verwenden, Dateien und Ordner in der Heimnetzgruppe aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="7470e-121">You can use queries to enumerate files and folders in the HomeGroup.</span></span> <span data-ttu-id="7470e-122">Weitere Informationen zu Datei- und Ordnerabfragen finden Sie unter [Aufzählen und Abfragen von Dateien und Ordnern](quickstart-listing-files-and-folders.md).</span><span class="sxs-lookup"><span data-stu-id="7470e-122">To learn about file and folder queries, see [Enumerating and querying files and folders](quickstart-listing-files-and-folders.md).</span></span>

## <a name="open-the-file-picker-at-the-homegroup"></a><span data-ttu-id="7470e-123">Öffnen der Dateiauswahl für die Heimnetzgruppe</span><span class="sxs-lookup"><span data-stu-id="7470e-123">Open the file picker at the HomeGroup</span></span>

<span data-ttu-id="7470e-124">Führen Sie die folgenden Schritte durch, um eine Instanz der Dateiauswahl zu öffnen, mit der Benutzer Dateien und Ordner in der Heimnetzgruppe auswählen können:</span><span class="sxs-lookup"><span data-stu-id="7470e-124">Follow these steps to open an instance of the file picker that lets the user pick files and folders from the HomeGroup:</span></span>

1.  **<span data-ttu-id="7470e-125">Erstellen und Anpassen der Dateiauswahl</span><span class="sxs-lookup"><span data-stu-id="7470e-125">Create and customize the file picker</span></span>**

    <span data-ttu-id="7470e-126">Verwenden Sie [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) zum Erstellen einer Dateiauswahl, und legen Sie dann den [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207854) der Auswahl auf [**PickerLocationId.HomeGroup**](https://msdn.microsoft.com/library/windows/apps/br207890) fest.</span><span class="sxs-lookup"><span data-stu-id="7470e-126">Use [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) to create the file picker, and then set the picker's [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207854) to [**PickerLocationId.HomeGroup**](https://msdn.microsoft.com/library/windows/apps/br207890).</span></span> <span data-ttu-id="7470e-127">Optional können Sie weitere Eigenschaften festlegen, die für Benutzer und App relevant sind.</span><span class="sxs-lookup"><span data-stu-id="7470e-127">Or, set other properties that are relevant to your users and your app.</span></span> <span data-ttu-id="7470e-128">Richtlinien zur Anpassung der Dateiauswahl erhalten Sie in [Richtlinien und Prüfliste für die Dateiauswahl](https://msdn.microsoft.com/library/windows/apps/hh465182).</span><span class="sxs-lookup"><span data-stu-id="7470e-128">For guidelines to help you decide how to customize the file picker, see [Guidelines and checklist for file pickers](https://msdn.microsoft.com/library/windows/apps/hh465182)</span></span>

    <span data-ttu-id="7470e-129">In diesem Beispiel wird eine Dateiauswahl erstellt, die in der Heimnetzgruppe geöffnet wird, bei der Dateien jeglichen Typs angezeigt werden und die Dateien als Miniaturbilder erscheinen:</span><span class="sxs-lookup"><span data-stu-id="7470e-129">This example creates a file picker that opens at the HomeGroup, includes files of any type, and displays the files as thumbnail images:</span></span>
    ```cs
    Windows.Storage.Pickers.FileOpenPicker picker = new Windows.Storage.Pickers.FileOpenPicker();
    picker.ViewMode = Windows.Storage.Pickers.PickerViewMode.Thumbnail;
    picker.SuggestedStartLocation = Windows.Storage.Pickers.PickerLocationId.HomeGroup;
    picker.FileTypeFilter.Clear();
    picker.FileTypeFilter.Add("*");
    ```

2.  **<span data-ttu-id="7470e-130">Blenden Sie die Dateiauswahl ein und verarbeiten Sie die ausgewählte Datei.</span><span class="sxs-lookup"><span data-stu-id="7470e-130">Show the file picker and process the picked file.</span></span>**

    <span data-ttu-id="7470e-131">Lassen Sie den Benutzer eine Datei auswählen, indem Sie [**FileOpenPicker.PickSingleFileAsync**](https://msdn.microsoft.com/library/windows/apps/jj635275) aufrufen, oder mehrere Dateien auswählen, indem Sie [**FileOpenPicker.PickMultipleFilesAsync**](https://msdn.microsoft.com/library/windows/apps/br207851) aufrufen, nachdem Sie die Dateiauswahl erstellt und angepasst haben.</span><span class="sxs-lookup"><span data-stu-id="7470e-131">After you create and customize the file picker, let the user pick one file by calling [**FileOpenPicker.PickSingleFileAsync**](https://msdn.microsoft.com/library/windows/apps/jj635275), or multiple files by calling [**FileOpenPicker.PickMultipleFilesAsync**](https://msdn.microsoft.com/library/windows/apps/br207851).</span></span>

    <span data-ttu-id="7470e-132">Dieses Beispiel zeigt eine Dateiauswahl, bei der der Benutzer eine Datei auswählen kann:</span><span class="sxs-lookup"><span data-stu-id="7470e-132">This example displays the file picker to let the user pick one file:</span></span>
    ```cs
    Windows.Storage.StorageFile file = await picker.PickSingleFileAsync();

    if (file != null)
    {
        // Do something with the file.
    }
    else
    {
        // No file returned. Handle the error.
    }   
    ```

## <a name="search-the-homegroup-for-files"></a><span data-ttu-id="7470e-133">Durchsuchen der Heimnetzgruppe nach Dateien</span><span class="sxs-lookup"><span data-stu-id="7470e-133">Search the HomeGroup for files</span></span>

<span data-ttu-id="7470e-134">In diesem Beispiel wird erläutert, wie Elemente in der Heimnetzgruppe gefunden werden können, die einem vom Benutzer angegebenen Abfrageausdruck entsprechen.</span><span class="sxs-lookup"><span data-stu-id="7470e-134">This section shows how to find HomeGroup items that match a query term provided by the user.</span></span>

1.  **<span data-ttu-id="7470e-135">Rufen Sie den Abfrageausdruck vom Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="7470e-135">Get the query term from the user.</span></span>**

    <span data-ttu-id="7470e-136">Hier erhalten wir einen Abfrageausdruck, den der Benutzer in ein [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683)-Steuerelement namens `searchQueryTextBox` eingegeben hat:</span><span class="sxs-lookup"><span data-stu-id="7470e-136">Here we get a query term that the user has entered into a [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) control called `searchQueryTextBox`:</span></span>
    ```cs
    string queryTerm = this.searchQueryTextBox.Text;    
    ```

2.  **<span data-ttu-id="7470e-137">Legen Sie die Abfrageoptionen und Suchfilter fest.</span><span class="sxs-lookup"><span data-stu-id="7470e-137">Set the query options and search filter.</span></span>**

    <span data-ttu-id="7470e-138">Abfrageoptionen bestimmen, wie die Suchergebnisse sortiert werden, während durch den Suchfilter festgelegt wird, welche Elemente in den Suchergebnissen erscheinen.</span><span class="sxs-lookup"><span data-stu-id="7470e-138">Query options determine how the search results are sorted, while the search filter determines which items are included in the search results.</span></span>

    <span data-ttu-id="7470e-139">In diesem Beispiel werden Abfrageoptionen festgelegt, die die Suchergebnisse nach Relevanz und dem Änderungsdatum sortieren.</span><span class="sxs-lookup"><span data-stu-id="7470e-139">This example sets query options that sort the search results by relevance and then the date modified.</span></span> <span data-ttu-id="7470e-140">Beim Suchfilter handelt es sich um den Abfrageausdruck, den der Benutzer im vorherigen Schritt eingegeben hat:</span><span class="sxs-lookup"><span data-stu-id="7470e-140">The search filter is the query term that the user entered in the previous step:</span></span>
    ```cs
    Windows.Storage.Search.QueryOptions queryOptions =
            new Windows.Storage.Search.QueryOptions
                (Windows.Storage.Search.CommonFileQuery.OrderBySearchRank, null);
    queryOptions.UserSearchFilter = queryTerm.Text;
    Windows.Storage.Search.StorageFileQueryResult queryResults =
            Windows.Storage.KnownFolders.HomeGroup.CreateFileQueryWithOptions(queryOptions);    
    ```

3.  **<span data-ttu-id="7470e-141">Führen Sie die Abfrage aus und verarbeiten Sie die Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="7470e-141">Run the query and process the results.</span></span>**

    <span data-ttu-id="7470e-142">Im folgenden Beispiel wird die Suchabfrage in der Heimnetzgruppe ausgeführt, und die Namen aller passenden Dateien werden in einer Liste mit Zeichenfolgen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="7470e-142">The following example runs the search query in the HomeGroup and saves the names of any matching files as a list of strings.</span></span>
    ```cs
    System.Collections.Generic.IReadOnlyList<Windows.Storage.StorageFile> files =
        await queryResults.GetFilesAsync();

    if (files.Count > 0)
    {
        outputString += (files.Count == 1) ? "One file found\n" : files.Count.ToString() + " files found\n";
        foreach (Windows.Storage.StorageFile file in files)
        {
            outputString += file.Name + "\n";
        }
    }    
    ```


## <a name="search-the-homegroup-for-a-particular-users-shared-files"></a><span data-ttu-id="7470e-143">Durchsuchen der Heimnetzgruppe nach den freigegebenen Dateien eines bestimmten Benutzers</span><span class="sxs-lookup"><span data-stu-id="7470e-143">Search the HomeGroup for a particular user's shared files</span></span>

<span data-ttu-id="7470e-144">In diesem Abschnitt erfahren Sie, wie Sie nach Heimnetzgruppendateien suchen, die von einem bestimmten Benutzer freigegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="7470e-144">This section shows you how to find HomeGroup files that are shared by a particular user.</span></span>

1.  **<span data-ttu-id="7470e-145">Stellen Sie eine Sammlung von Heimnetzgruppenbenutzern zusammen.</span><span class="sxs-lookup"><span data-stu-id="7470e-145">Get a collection of HomeGroup users.</span></span>**

    <span data-ttu-id="7470e-146">Jeder Ordner auf oberster Ebene in der Heimnetzgruppe repräsentiert einen bestimmten Heimnetzgruppenbenutzer.</span><span class="sxs-lookup"><span data-stu-id="7470e-146">Each of the first-level folders in the HomeGroup represents an individual HomeGroup user.</span></span> <span data-ttu-id="7470e-147">Um die Sammlung der Heimnetzgruppenbenutzer zu erhalten, rufen Sie also [**GetFoldersAsync**](https://msdn.microsoft.com/library/windows/apps/br227279) auf, um die Heimnetzgruppenordner der obersten Ebene abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7470e-147">So, to get the collection of HomeGroup users, call [**GetFoldersAsync**](https://msdn.microsoft.com/library/windows/apps/br227279) retrieve the top-level HomeGroup folders.</span></span>
    ```cs
    System.Collections.Generic.IReadOnlyList<Windows.Storage.StorageFolder> hgFolders =
        await Windows.Storage.KnownFolders.HomeGroup.GetFoldersAsync();    
    ```

2.  **<span data-ttu-id="7470e-148">Suchen Sie dann nach dem Ordner des Zielbenutzers, und erstellen Sie eine Dateiabfrage, die auf den Ordner dieses Benutzers eingegrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="7470e-148">Find the target user's folder, and then create a file query scoped to that user's folder.</span></span>**

    <span data-ttu-id="7470e-149">Das folgende Beispiel geht die abgerufenen Ordner durch, um den Ordner des Zielbenutzers zu finden.</span><span class="sxs-lookup"><span data-stu-id="7470e-149">The following example iterates through the retrieved folders to find the target user's folder.</span></span> <span data-ttu-id="7470e-150">Anschließend legt es die Abfrageoptionen so fest, dass alle Dateien im Ordner gefunden werden, primär nach Relevanz und zweitrangig nach dem Änderungsdatum sortiert.</span><span class="sxs-lookup"><span data-stu-id="7470e-150">Then, it sets query options to find all files in the folder, sorted first by relevance and then by the date modified.</span></span> <span data-ttu-id="7470e-151">Das Beispiel generiert eine Zeichenfolge, die die Anzahl der gefundenen Dateien zusammen mit den Namen der Dateien ausgibt.</span><span class="sxs-lookup"><span data-stu-id="7470e-151">The example builds a string that reports the number of files found, along with the names of the files.</span></span>
    ```cs
    bool userFound = false;
    foreach (Windows.Storage.StorageFolder folder in hgFolders)
    {
        if (folder.DisplayName == targetUserName)
        {
            // Found the target user's folder, now find all files in the folder.
            userFound = true;
            Windows.Storage.Search.QueryOptions queryOptions =
                new Windows.Storage.Search.QueryOptions
                    (Windows.Storage.Search.CommonFileQuery.OrderBySearchRank, null);
            queryOptions.UserSearchFilter = "*";
            Windows.Storage.Search.StorageFileQueryResult queryResults =
                folder.CreateFileQueryWithOptions(queryOptions);
            System.Collections.Generic.IReadOnlyList<Windows.Storage.StorageFile> files =
                await queryResults.GetFilesAsync();

            if (files.Count > 0)
            {
                string outputString = "Searched for files belonging to " + targetUserName + "'\n";
                outputString += (files.Count == 1) ? "One file found\n" : files.Count.ToString() + " files found\n";
                foreach (Windows.Storage.StorageFile file in files)
                {
                    outputString += file.Name + "\n";
                }
            }
        }
    }    
    ```

## <a name="stream-video-from-the-homegroup"></a><span data-ttu-id="7470e-152">Streamen von Videos aus der Heimnetzgruppe</span><span class="sxs-lookup"><span data-stu-id="7470e-152">Stream video from the HomeGroup</span></span>

<span data-ttu-id="7470e-153">Gehen Sie wie folgt vor, um Videoinhalte aus der Heimnetzgruppe zu streamen:</span><span class="sxs-lookup"><span data-stu-id="7470e-153">Follow these steps to stream video content from the HomeGroup:</span></span>

1.  **<span data-ttu-id="7470e-154">Fügen Sie Ihrer App ein „MediaElement“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="7470e-154">Include a MediaElement in your app.</span></span>**

    <span data-ttu-id="7470e-155">Mithilfe von [**MediaElement**](https://msdn.microsoft.com/library/windows/apps/br242926) können Sie Audio- und Videoinhalte in Ihrer App wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="7470e-155">A [**MediaElement**](https://msdn.microsoft.com/library/windows/apps/br242926) lets you play back audio and video content in your app.</span></span> <span data-ttu-id="7470e-156">Weitere Informationen zur Audio- und Videowiedergabe finden Sie unter [Erstellen von benutzerdefinierten Transportsteuerelementen](https://msdn.microsoft.com/library/windows/apps/mt187271) und [Audio, Video und Kamera](https://msdn.microsoft.com/library/windows/apps/mt203788).</span><span class="sxs-lookup"><span data-stu-id="7470e-156">For more information on audio and video playback, see [Create custom transport controls](https://msdn.microsoft.com/library/windows/apps/mt187271) and [Audio, video, and camera](https://msdn.microsoft.com/library/windows/apps/mt203788).</span></span>
    ```HTML
    <Grid x:Name="Output" HorizontalAlignment="Left" VerticalAlignment="Top" Grid.Row="1">
        <MediaElement x:Name="VideoBox" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0" Width="400" Height="300"/>
    </Grid>    
    ```

2.  **<span data-ttu-id="7470e-157">Öffnen Sie eine Dateiauswahl für die Heimnetzgruppe und wenden Sie einen Filter an, der alle Dateien ausschließt, bei denen es sich nicht um Videodateiformate handelt, die Ihre App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7470e-157">Open a file picker at the HomeGroup and apply a filter that includes video files in the formats that your app supports.</span></span>**

    <span data-ttu-id="7470e-158">In diesem Beispiel werden MP4- und WMV-Dateien für die Dateiauswahl festgelegt.</span><span class="sxs-lookup"><span data-stu-id="7470e-158">This example includes .mp4 and .wmv files in the file open picker.</span></span>
    ```cs
    Windows.Storage.Pickers.FileOpenPicker picker = new Windows.Storage.Pickers.FileOpenPicker();
    picker.ViewMode = Windows.Storage.Pickers.PickerViewMode.Thumbnail;
    picker.SuggestedStartLocation = Windows.Storage.Pickers.PickerLocationId.HomeGroup;
    picker.FileTypeFilter.Clear();
    picker.FileTypeFilter.Add(".mp4");
    picker.FileTypeFilter.Add(".wmv");
    Windows.Storage.StorageFile file = await picker.PickSingleFileAsync();   
    ```

3.  <span data-ttu-id="7470e-159">**Dateiauswahl des Benutzers für den Lesezugriff zu öffnen, und legen Sie den Dateidatenstrom als Quelle für die** [**MediaElement**](https://msdn.microsoft.com/library/windows/apps/br242926)und dann Wiedergabe der Datei.</span><span class="sxs-lookup"><span data-stu-id="7470e-159">**Open the user's file selection for read access, and set the file stream as the source for the** [**MediaElement**](https://msdn.microsoft.com/library/windows/apps/br242926), and then play the file.</span></span>
    ```cs
    if (file != null)
    {
        var stream = await file.OpenAsync(Windows.Storage.FileAccessMode.Read);
        VideoBox.SetSource(stream, file.ContentType);
        VideoBox.Stop();
        VideoBox.Play();
    }
    else
    {
        // No file selected. Handle the error here.
    }    
    ```
