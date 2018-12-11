---
ms.assetid: F87DBE2F-77DB-4573-8172-29E11ABEFD34
title: Öffnen von Dateien und Ordnern mit einer Auswahl
description: Greifen Sie auf Dateien und Ordner zu, indem Sie Benutzern die Interaktion mit einer Auswahl ermöglichen. Mithilfe der FileOpenPicker- und der FileSavePicker-Klasse können Sie auf Dateien und mithilfe der FolderPicker-Klasse auf einen Ordner zugreifen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7ed2c1715ebb682aed3da4b55ef94cc0c60f8391
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8880053"
---
# <a name="open-files-and-folders-with-a-picker"></a><span data-ttu-id="d50ad-105">Öffnen von Dateien und Ordnern mit einer Auswahl</span><span class="sxs-lookup"><span data-stu-id="d50ad-105">Open files and folders with a picker</span></span>

**<span data-ttu-id="d50ad-106">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="d50ad-106">Important APIs</span></span>**

-   [**<span data-ttu-id="d50ad-107">FileOpenPicker</span><span class="sxs-lookup"><span data-stu-id="d50ad-107">FileOpenPicker</span></span>**](https://msdn.microsoft.com/library/windows/apps/br207847)
-   [**<span data-ttu-id="d50ad-108">FolderPicker</span><span class="sxs-lookup"><span data-stu-id="d50ad-108">FolderPicker</span></span>**](https://msdn.microsoft.com/library/windows/apps/br207881)
-   [**<span data-ttu-id="d50ad-109">StorageFile</span><span class="sxs-lookup"><span data-stu-id="d50ad-109">StorageFile</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227171)

<span data-ttu-id="d50ad-110">Greifen Sie auf Dateien und Ordner zu, indem Sie Benutzern die Interaktion mit einer Auswahl ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="d50ad-110">Access files and folders by letting the user interact with a picker.</span></span> <span data-ttu-id="d50ad-111">Mithilfe der Klassen [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) und [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) können Sie auf Dateien und mithilfe der Klasse [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881) auf einen Ordner zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d50ad-111">You can use the [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) and [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) classes to access files, and the [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881) to access a folder.</span></span>

> [!NOTE]
> <span data-ttu-id="d50ad-112">Ein vollständiges Beispiel finden Sie im [Dateiauswahl-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619994).</span><span class="sxs-lookup"><span data-stu-id="d50ad-112">For a complete sample, see the [File picker sample](http://go.microsoft.com/fwlink/p/?linkid=619994).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d50ad-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d50ad-113">Prerequisites</span></span>


-   **<span data-ttu-id="d50ad-114">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="d50ad-114">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="d50ad-115">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span><span class="sxs-lookup"><span data-stu-id="d50ad-115">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span></span> <span data-ttu-id="d50ad-116">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span><span class="sxs-lookup"><span data-stu-id="d50ad-116">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span></span>

-   **<span data-ttu-id="d50ad-117">Zugriffsberechtigungen für den Speicherort</span><span class="sxs-lookup"><span data-stu-id="d50ad-117">Access permissions to the location</span></span>**

    <span data-ttu-id="d50ad-118">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](file-access-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="d50ad-118">See [File access permissions](file-access-permissions.md).</span></span>

## <a name="file-picker-ui"></a><span data-ttu-id="d50ad-119">Dateiauswahl – Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="d50ad-119">File picker UI</span></span>


<span data-ttu-id="d50ad-120">Eine Dateiauswahl zeigt Informationen für die Orientierung der Benutzer an und stellt eine einheitliche Benutzererfahrung beim Öffnen oder Speichern von Dateien bereit.</span><span class="sxs-lookup"><span data-stu-id="d50ad-120">A file picker displays information to orient users and provide a consistent experience when opening or saving files.</span></span>

<span data-ttu-id="d50ad-121">Diese Informationen umfassen:</span><span class="sxs-lookup"><span data-stu-id="d50ad-121">That information includes:</span></span>

-   <span data-ttu-id="d50ad-122">Den aktuellen Speicherort</span><span class="sxs-lookup"><span data-stu-id="d50ad-122">The current location</span></span>
-   <span data-ttu-id="d50ad-123">Die Elemente, die der Benutzer ausgewählt hat</span><span class="sxs-lookup"><span data-stu-id="d50ad-123">The item or items that the user picked</span></span>
-   <span data-ttu-id="d50ad-124">Eine Struktur mit Speicherorten, die der Benutzer durchsuchen kann.</span><span class="sxs-lookup"><span data-stu-id="d50ad-124">A tree of locations that the user can browse to.</span></span> <span data-ttu-id="d50ad-125">Diese Speicherorte umfassen Dateisystemspeicherorte, wie z. B. Musik- oder Downloadordner, sowie Apps, die den Dateiauswahlvertrag (z. B. Kamera, Fotos und Microsoft OneDrive) implementieren.</span><span class="sxs-lookup"><span data-stu-id="d50ad-125">These locations include file system locations—such as the Music or Downloads folder—as well as apps that implement the file picker contract (such as Camera, Photos, and Microsoft OneDrive).</span></span>

<span data-ttu-id="d50ad-126">Eine E-Mail-App zeigt möglicherweise eine Dateiauswahl an, damit der Benutzer Anlagen auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="d50ad-126">An email app might display a file picker for the user to pick attachments.</span></span>

![Eine Dateiauswahl mit zwei zu öffnenden Dateien.](images/picker-multifile-600px.png)

## <a name="how-pickers-work"></a><span data-ttu-id="d50ad-128">Funktionsweise der Auswahl</span><span class="sxs-lookup"><span data-stu-id="d50ad-128">How pickers work</span></span>


<span data-ttu-id="d50ad-129">Mithilfe einer Auswahl kann Ihre App Zugriff auf Dateien und Ordner auf dem System des Benutzers erlangen und diese durchsuchen und speichern.</span><span class="sxs-lookup"><span data-stu-id="d50ad-129">With a picker your app can access, browse, and save files and folders on the user's system.</span></span> <span data-ttu-id="d50ad-130">Ihre App erhält diese Auswahl als [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)- und [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230)-Objekte, die Sie dann verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="d50ad-130">Your app receives those picks as [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) and [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) objects, which you can then operate on.</span></span>

<span data-ttu-id="d50ad-131">Die Auswahl verwendet eine einzige, einheitliche Oberfläche, über die der Benutzer Dateien und Ordner im Dateisystem oder in anderen Apps auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="d50ad-131">The picker uses a single, unified interface to let the user pick files and folders from the file system or from other apps.</span></span> <span data-ttu-id="d50ad-132">Mit Dateien, die in anderen Apps ausgewählt werden, verhält es sich genauso wie mit Dateien im Dateisystem: Sie werden als [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekte zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="d50ad-132">Files picked from other apps are like files from the file system: they are returned as [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) objects.</span></span> <span data-ttu-id="d50ad-133">Im Allgemeinen kann Ihre App genauso mit ihnen arbeiten wie mit anderen Objekten.</span><span class="sxs-lookup"><span data-stu-id="d50ad-133">In general, your app can operate on them in the same ways as other objects.</span></span> <span data-ttu-id="d50ad-134">Andere Apps stellen Dateien bereit, indem sie an Verträgen für die Dateiauswahl teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="d50ad-134">Other apps make files available by participating in file picker contracts.</span></span> <span data-ttu-id="d50ad-135">Wenn Ihre App Dateien, einen Speicherort oder Dateiupdates für andere Apps bereitstellen soll, finden Sie Informationen dazu unter [Integration mit Verträgen für die Dateiauswahl](https://msdn.microsoft.com/library/windows/apps/hh465192).</span><span class="sxs-lookup"><span data-stu-id="d50ad-135">If you want your app to provide files, a save location, or file updates to other apps, see [Integrating with file picker contracts](https://msdn.microsoft.com/library/windows/apps/hh465192).</span></span>

<span data-ttu-id="d50ad-136">Beispielsweise können Sie die Dateiauswahl in Ihrer App aufrufen und dem Benutzer so ermöglichen, eine Datei zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d50ad-136">For example, you might call the file picker in your app so that your user can open a file.</span></span> <span data-ttu-id="d50ad-137">Dadurch wird Ihre App zur aufrufenden App.</span><span class="sxs-lookup"><span data-stu-id="d50ad-137">This makes your app the calling app.</span></span> <span data-ttu-id="d50ad-138">Die Dateiauswahl interagiert mit dem System und/oder anderen Apps, damit der Benutzer zu einer Datei navigieren und diese auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="d50ad-138">The file picker interacts with the system and/or other apps to let the user navigate and pick the file.</span></span> <span data-ttu-id="d50ad-139">Wählt der Benutzer eine Datei aus, gibt die Dateiauswahl diese Datei an Ihre App zurück.</span><span class="sxs-lookup"><span data-stu-id="d50ad-139">When your user chooses a file, the file picker returns that file to your app.</span></span> <span data-ttu-id="d50ad-140">Dies ist der Prozess für einen Fall, in dem ein Benutzer eine Datei in einer bereitstellenden App wie etwa OneDrive auswählt.</span><span class="sxs-lookup"><span data-stu-id="d50ad-140">Here's the process for the case of the user choosing a file from a providing app, such as OneDrive.</span></span>

![Ein Diagramm, das zeigt, wie eine App eine zu öffnende Datei aus einer anderen App erhält. Die Dateiauswahl fungiert hier als Schnittstelle zwischen den beiden Apps.](images/app-to-app-diagram-600px.png)

## <a name="pick-a-single-file-complete-code-listing"></a><span data-ttu-id="d50ad-142">Auswählen einer einzelnen Datei: vollständige Codeauflistung</span><span class="sxs-lookup"><span data-stu-id="d50ad-142">Pick a single file: complete code listing</span></span>


```cs
var picker = new Windows.Storage.Pickers.FileOpenPicker();
picker.ViewMode = Windows.Storage.Pickers.PickerViewMode.Thumbnail;
picker.SuggestedStartLocation = Windows.Storage.Pickers.PickerLocationId.PicturesLibrary;
picker.FileTypeFilter.Add(".jpg");
picker.FileTypeFilter.Add(".jpeg");
picker.FileTypeFilter.Add(".png");

Windows.Storage.StorageFile file = await picker.PickSingleFileAsync();
if (file != null)
{
    // Application now has read/write access to the picked file
    this.textBlock.Text = "Picked photo: " + file.Name;
}
else
{
    this.textBlock.Text = "Operation cancelled.";
}
```

## <a name="pick-a-single-file-step-by-step"></a><span data-ttu-id="d50ad-143">Auswählen einer einzelnen Datei: Schritt für Schritt</span><span class="sxs-lookup"><span data-stu-id="d50ad-143">Pick a single file: step-by-step</span></span>


<span data-ttu-id="d50ad-144">Das Verwenden der Dateiauswahl umfasst das Erstellen und Anpassen eines Dateiauswahlobjekts und Einblenden der Dateiauswahl, sodass der Benutzer ein oder mehrere Elemente auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="d50ad-144">Using a file picker involves creating and customizing a file picker object, and then showing the file picker so the user can pick one or more items.</span></span>

1.  **<span data-ttu-id="d50ad-145">Erstellen und Anpassen eines FileOpenPicker</span><span class="sxs-lookup"><span data-stu-id="d50ad-145">Create and customize a FileOpenPicker</span></span>**

    ```cs
    var picker = new Windows.Storage.Pickers.FileOpenPicker();
    picker.ViewMode = Windows.Storage.Pickers.PickerViewMode.Thumbnail;
    picker.SuggestedStartLocation = Windows.Storage.Pickers.PickerLocationId.PicturesLibrary;
    picker.FileTypeFilter.Add(".jpg");
    picker.FileTypeFilter.Add(".jpeg");
    picker.FileTypeFilter.Add(".png");
    ```
    <span data-ttu-id="d50ad-146">Legen Sie Eigenschaften für das Dateiauswahlobjekt fest, die für Ihre Benutzer und Ihre App relevant sind.</span><span class="sxs-lookup"><span data-stu-id="d50ad-146">Set properties on the file picker object relevant to your users and app.</span></span>

    <span data-ttu-id="d50ad-147">Dieses Beispiel erstellt eine ansprechende visuelle Darstellung von Bildern, aus denen der Benutzer wählen kann, an einem praktischen Ort durch Festlegen von drei Eigenschaften: [**ViewMode**](https://msdn.microsoft.com/library/windows/apps/br207855), [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207854) und [**FileTypeFilter**](https://msdn.microsoft.com/library/windows/apps/br207850).</span><span class="sxs-lookup"><span data-stu-id="d50ad-147">This example creates a rich, visual display of pictures in a convenient location that the user can pick from by setting three properties: [**ViewMode**](https://msdn.microsoft.com/library/windows/apps/br207855), [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207854), and [**FileTypeFilter**](https://msdn.microsoft.com/library/windows/apps/br207850).</span></span>

    -   <span data-ttu-id="d50ad-148">Wenn [**ViewMode**](https://msdn.microsoft.com/library/windows/apps/br207855) auf den [**PickerViewMode**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.storage.pickers.pickerviewmode.aspx#thumbnail) **Thumbnail**-Enumerationswert festgelegt wird, entsteht eine ansprechende visuelle Darstellung, da Miniaturbilder als Darstellung für die Dateien in der Dateiauswahl erscheinen.</span><span class="sxs-lookup"><span data-stu-id="d50ad-148">Setting [**ViewMode**](https://msdn.microsoft.com/library/windows/apps/br207855) to the [**PickerViewMode**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.storage.pickers.pickerviewmode.aspx#thumbnail) **Thumbnail** enum value creates a rich, visual display by using picture thumbnails to represent files in the file picker.</span></span> <span data-ttu-id="d50ad-149">Dies gilt für die Auswahl visueller Dateien wie Bilder oder Videos.</span><span class="sxs-lookup"><span data-stu-id="d50ad-149">Do this for picking visual files such as pictures or videos.</span></span> <span data-ttu-id="d50ad-150">Verwenden Sie andernfalls [**PickerViewMode.List**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.storage.pickers.pickerviewmode.aspx#list).</span><span class="sxs-lookup"><span data-stu-id="d50ad-150">Otherwise, use [**PickerViewMode.List**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.storage.pickers.pickerviewmode.aspx#list).</span></span> <span data-ttu-id="d50ad-151">Eine hypothetische E-Mail-App mit **Bild oder Video anfügen**- und **Dokument anfügen**-Funktionen würde den **ViewMode** auf die entsprechende Funktion vor dem Anzeigen der Dateiauswahl festlegen.</span><span class="sxs-lookup"><span data-stu-id="d50ad-151">A hypothetical email app with **Attach Picture or Video** and **Attach Document** features would set the **ViewMode** appropriate to the feature before showing the file picker.</span></span>

    -   <span data-ttu-id="d50ad-152">Wenn [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207854) mithilfe von [**PickerLocationId.PicturesLibrary**](https://msdn.microsoft.com/library/windows/apps/br207890) auf Bilder festgelegt wird, beginnt der Benutzer in einem Pfad, der mit hoher Wahrscheinlichkeit Bilder enthält.</span><span class="sxs-lookup"><span data-stu-id="d50ad-152">Setting [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207854) to Pictures using [**PickerLocationId.PicturesLibrary**](https://msdn.microsoft.com/library/windows/apps/br207890) starts the user in a location where they're likely to find pictures.</span></span> <span data-ttu-id="d50ad-153">Legen Sie **SuggestedStartLocation** auf einen Speicherort fest, der dem Typ der ausgewählten Datei entspricht, z. B. Musik, Bilder, Videos oder Dokumente.</span><span class="sxs-lookup"><span data-stu-id="d50ad-153">Set **SuggestedStartLocation** to a location appropriate for the type of file being picked, for example Music, Pictures, Videos, or Documents.</span></span> <span data-ttu-id="d50ad-154">Der Benutzer kann vom Ausgangspfad aus zu anderen Speicherorten navigieren.</span><span class="sxs-lookup"><span data-stu-id="d50ad-154">From the start location, the user can navigate to other locations.</span></span>

    -   <span data-ttu-id="d50ad-155">Mit [**FileTypeFilter**](https://msdn.microsoft.com/library/windows/apps/br207850) zum Angeben von Dateitypen wählt der Benutzer weiterhin relevante Dateien aus.</span><span class="sxs-lookup"><span data-stu-id="d50ad-155">Using [**FileTypeFilter**](https://msdn.microsoft.com/library/windows/apps/br207850) to specify file types keeps the user focused on picking files that are relevant.</span></span> <span data-ttu-id="d50ad-156">Um ältere Dateitypen im **FileTypeFilter** durch neue Einträgen zu ersetzen, verwenden Sie [**ReplaceAll**](https://msdn.microsoft.com/library/windows/apps/br207844) anstelle von [**Add**](https://msdn.microsoft.com/library/windows/apps/br207834).</span><span class="sxs-lookup"><span data-stu-id="d50ad-156">To replace previous file types in the **FileTypeFilter** with new entries, use [**ReplaceAll**](https://msdn.microsoft.com/library/windows/apps/br207844) instead of [**Add**](https://msdn.microsoft.com/library/windows/apps/br207834).</span></span>

2.  **<span data-ttu-id="d50ad-157">Anzeigen von FileOpenPicker</span><span class="sxs-lookup"><span data-stu-id="d50ad-157">Show the FileOpenPicker</span></span>**

    - **<span data-ttu-id="d50ad-158">So wählen Sie eine einzelne Datei aus</span><span class="sxs-lookup"><span data-stu-id="d50ad-158">To pick a single file</span></span>**

    ```cs
    Windows.Storage.StorageFile file = await picker.PickSingleFileAsync();
    if (file != null)
    {
        // Application now has read/write access to the picked file
        this.textBlock.Text = "Picked photo: " + file.Name;
    }
    else
    {
        this.textBlock.Text = "Operation cancelled.";
    }
    ```

    - **<span data-ttu-id="d50ad-159">So wählen Sie mehrere Dateien aus</span><span class="sxs-lookup"><span data-stu-id="d50ad-159">To pick multiple files</span></span>**  

    ```cs
    var files = await picker.PickMultipleFilesAsync();
    if (files.Count > 0)
    {
        StringBuilder output = new StringBuilder("Picked files:\n");

        // Application now has read/write access to the picked file(s)
        foreach (Windows.Storage.StorageFile file in files)
        {
            output.Append(file.Name + "\n");
        }
        this.textBlock.Text = output.ToString();
    }
    else
    {
        this.textBlock.Text = "Operation cancelled.";
    }
    ```

## <a name="pick-a-folder-complete-code-listing"></a><span data-ttu-id="d50ad-160">Auswählen eines Ordners: vollständiger Code</span><span class="sxs-lookup"><span data-stu-id="d50ad-160">Pick a folder: complete code listing</span></span>


```cs
var folderPicker = new Windows.Storage.Pickers.FolderPicker();
folderPicker.SuggestedStartLocation = Windows.Storage.Pickers.PickerLocationId.Desktop;
folderPicker.FileTypeFilter.Add("*");

Windows.Storage.StorageFolder folder = await folderPicker.PickSingleFolderAsync();
if (folder != null)
{
    // Application now has read/write access to all contents in the picked folder
    // (including other sub-folder contents)
    Windows.Storage.AccessCache.StorageApplicationPermissions.
    FutureAccessList.AddOrReplace("PickedFolderToken", folder);
    this.textBlock.Text = "Picked folder: " + folder.Name;
}
else
{
    this.textBlock.Text = "Operation cancelled.";
}
```

> [!TIP]
> <span data-ttu-id="d50ad-161">Fügen Sie die Datei oder den Ordner zur Verbesserung der Nachverfolgbarkeit zur [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) oder [**MostRecentlyUsedList**](https://msdn.microsoft.com/library/windows/apps/br207458) der App hinzu, wenn Ihre App über eine Dateiauswahl auf eine Datei oder einen Ordner zugreift.</span><span class="sxs-lookup"><span data-stu-id="d50ad-161">Whenever your app accesses a file or folder through a picker, add it to your app's [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) or [**MostRecentlyUsedList**](https://msdn.microsoft.com/library/windows/apps/br207458) to keep track of it.</span></span> <span data-ttu-id="d50ad-162">Weitere Informationen zur Verwendung dieser Listen finden Sie in [So wird's gemacht: Nachverfolgen kürzlich verwendeter Dateien und Ordner](how-to-track-recently-used-files-and-folders.md).</span><span class="sxs-lookup"><span data-stu-id="d50ad-162">You can learn more about using these lists in [How to track recently-used files and folders](how-to-track-recently-used-files-and-folders.md).</span></span>