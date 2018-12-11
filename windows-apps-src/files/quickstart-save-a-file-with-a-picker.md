---
ms.assetid: 8BDDE64A-77D2-4F9D-A1A0-E4C634BCD890
title: Speichern einer Datei mit einer Auswahl
description: Mithilfe von FileSavePicker können Benutzer den Namen und Speicherort zum Speichern einer Datei durch die App angeben.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: a7e278df29a531e5bf1d0d92946cd0199f85515d
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8877138"
---
# <a name="save-a-file-with-a-picker"></a><span data-ttu-id="27845-104">Speichern einer Datei mit einer Auswahl</span><span class="sxs-lookup"><span data-stu-id="27845-104">Save a file with a picker</span></span>

**<span data-ttu-id="27845-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="27845-105">Important APIs</span></span>**

-   [**<span data-ttu-id="27845-106">FileSavePicker</span><span class="sxs-lookup"><span data-stu-id="27845-106">FileSavePicker</span></span>**](https://msdn.microsoft.com/library/windows/apps/br207871)
-   [**<span data-ttu-id="27845-107">StorageFile</span><span class="sxs-lookup"><span data-stu-id="27845-107">StorageFile</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227171)

<span data-ttu-id="27845-108">Mithilfe von [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) können Benutzer den Namen und Speicherort zum Speichern einer Datei durch die App angeben.</span><span class="sxs-lookup"><span data-stu-id="27845-108">Use [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) to let users specify the name and location where they want your app to save a file.</span></span>

> [!NOTE]
> <span data-ttu-id="27845-109">Informationen finden Sie auch unter [Beispiel zur Dateiauswahl](http://go.microsoft.com/fwlink/p/?linkid=619994).</span><span class="sxs-lookup"><span data-stu-id="27845-109">Also see the [File picker sample](http://go.microsoft.com/fwlink/p/?linkid=619994).</span></span>

 

## <a name="prerequisites"></a><span data-ttu-id="27845-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="27845-110">Prerequisites</span></span>


-   **<span data-ttu-id="27845-111">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="27845-111">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="27845-112">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span><span class="sxs-lookup"><span data-stu-id="27845-112">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span></span> <span data-ttu-id="27845-113">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span><span class="sxs-lookup"><span data-stu-id="27845-113">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span></span>

-   **<span data-ttu-id="27845-114">Zugriffsberechtigungen für den Speicherort</span><span class="sxs-lookup"><span data-stu-id="27845-114">Access permissions to the location</span></span>**

    <span data-ttu-id="27845-115">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](file-access-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="27845-115">See [File access permissions](file-access-permissions.md).</span></span>

## <a name="filesavepicker-step-by-step"></a><span data-ttu-id="27845-116">FileSavePicker: Schritt für Schritt</span><span class="sxs-lookup"><span data-stu-id="27845-116">FileSavePicker: step-by-step</span></span>

<span data-ttu-id="27845-117">Verwenden Sie [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871), damit Benutzer den Namen, Typ und Speicherort von zu speichernden Dateien angeben können.</span><span class="sxs-lookup"><span data-stu-id="27845-117">Use a [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) so that your users can specify the name, type, and location of a file to save.</span></span> <span data-ttu-id="27845-118">Erstellen Sie ein Dateiauswahlobjekt, passen und zeigen Sie es an, und speichern Sie dann Daten über das zurückgegebene [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekt, das die ausgewählte Datei darstellt.</span><span class="sxs-lookup"><span data-stu-id="27845-118">Create, customize, and show a file picker object, and then save data via the returned [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) object that represents the file picked.</span></span>

1.  **<span data-ttu-id="27845-119">Erstellen und Anpassen des FileSavePicker-Objekts</span><span class="sxs-lookup"><span data-stu-id="27845-119">Create and customize the FileSavePicker</span></span>**

```cs
var savePicker = new Windows.Storage.Pickers.FileSavePicker();
savePicker.SuggestedStartLocation =
    Windows.Storage.Pickers.PickerLocationId.DocumentsLibrary;
// Dropdown of file types the user can save the file as
savePicker.FileTypeChoices.Add("Plain Text", new List<string>() { ".txt" });
// Default file name if the user does not type one in or select a file to replace
savePicker.SuggestedFileName = "New Document";
```

<span data-ttu-id="27845-120">Legen Sie Eigenschaften für das Dateiauswahlobjekt fest, die für Ihre Benutzer und Ihre App relevant sind.</span><span class="sxs-lookup"><span data-stu-id="27845-120">Set properties on the file picker object that are relevant to your users and your app.</span></span>

<span data-ttu-id="27845-121">In diesem Beispiel werden drei Eigenschaften festgelegt: [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207880), [**FileTypeChoices**](https://msdn.microsoft.com/library/windows/apps/br207875) und [**SuggestedFileName**](https://msdn.microsoft.com/library/windows/apps/br207878).</span><span class="sxs-lookup"><span data-stu-id="27845-121">This example sets three properties: [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207880), [**FileTypeChoices**](https://msdn.microsoft.com/library/windows/apps/br207875) and [**SuggestedFileName**](https://msdn.microsoft.com/library/windows/apps/br207878).</span></span>

> [!NOTE]
><span data-ttu-id="27845-122">[**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871)-Objekte zeigen die Dateiauswahl mithilfe von [**PickerViewMode.List**](https://msdn.microsoft.com/library/windows/apps/br207891) an.</span><span class="sxs-lookup"><span data-stu-id="27845-122">[**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) objects display the file picker using the [**PickerViewMode.List**](https://msdn.microsoft.com/library/windows/apps/br207891).</span></span>
     
- <span data-ttu-id="27845-123">Da der Benutzer in unserem Fall ein Dokument oder eine Textdatei speichert, wird im Beispiel [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207880) auf den lokalen Ordner der App mithilfe von [**LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="27845-123">Because our user is saving a document or text file, the sample sets [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207880) to the app's local folder by using [**LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621).</span></span> <span data-ttu-id="27845-124">Legen Sie [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207854) auf einen Speicherort fest, der dem Typ der gespeicherten Datei entspricht, z. B. Musik, Bilder, Videos oder Dokumente.</span><span class="sxs-lookup"><span data-stu-id="27845-124">Set [**SuggestedStartLocation**](https://msdn.microsoft.com/library/windows/apps/br207854) to a location appropriate for the type of file being saved, for example Music, Pictures, Videos, or Documents.</span></span> <span data-ttu-id="27845-125">Der Benutzer kann vom Ausgangspfad aus zu anderen Speicherorten navigieren.</span><span class="sxs-lookup"><span data-stu-id="27845-125">From the start location, the user can navigate to other locations.</span></span>

- <span data-ttu-id="27845-126">Da wir sicherstellen möchten, dass unsere App die Datei nach dem Speichern öffnen kann, verwenden wir im Beispiel [**FileTypeChoices**](https://msdn.microsoft.com/library/windows/apps/br207875) für die Angabe der vom Beispiel unterstützten Dateitypen (Microsoft Word-Dokumente und Textdateien).</span><span class="sxs-lookup"><span data-stu-id="27845-126">Because we want to make sure our app can open the file after it is saved, we use [**FileTypeChoices**](https://msdn.microsoft.com/library/windows/apps/br207875) to specify file types that the sample supports (Microsoft Word documents and text files).</span></span> <span data-ttu-id="27845-127">Stellen Sie sicher, dass alle von Ihnen angegebenen Dateitypen von Ihrer App unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="27845-127">Make sure all the file types that you specify are supported by your app.</span></span> <span data-ttu-id="27845-128">Die Benutzer können ihre Datei unter einem beliebigen der von Ihnen angegebenen Dateitypen speichern.</span><span class="sxs-lookup"><span data-stu-id="27845-128">Users will be able to save their file as any of the file types you specify.</span></span> <span data-ttu-id="27845-129">Sie können auch den Dateityp ändern, indem sie einen anderen von Ihnen angegebenen Dateityp auswählen.</span><span class="sxs-lookup"><span data-stu-id="27845-129">They can also change the file type by selecting another of the file types that you specified.</span></span> <span data-ttu-id="27845-130">Der erste Dateityp in der Liste ist standardmäßig ausgewählt; Sie können diesen mit der [**DefaultFileExtension**](https://msdn.microsoft.com/library/windows/apps/br207873)-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="27845-130">The first file type choice in the list will be selected by default: to control that, set the [**DefaultFileExtension**](https://msdn.microsoft.com/library/windows/apps/br207873) property.</span></span>

> [!NOTE]
> <span data-ttu-id="27845-131">Für die Dateiauswahl wird zudem der aktuell ausgewählte Dateityp zum Filtern nach den angezeigten Dateien verwendet, sodass dem Benutzer nur die Dateitypen angezeigt werden, die mit den ausgewählten Dateitypen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="27845-131">The file picker also uses the currently selected file type to filter which files it displays, so that only file types that match the selected files types are displayed to the user.</span></span>

- <span data-ttu-id="27845-132">Um dem Benutzer einige Eingaben zu ersparen, legt das Beispiel einen [**SuggestedFileName**](https://msdn.microsoft.com/library/windows/apps/br207878) fest.</span><span class="sxs-lookup"><span data-stu-id="27845-132">To save the user some typing, the example sets a [**SuggestedFileName**](https://msdn.microsoft.com/library/windows/apps/br207878).</span></span> <span data-ttu-id="27845-133">Verwenden Sie als vorgeschlagenen Dateinamen einen Namen, der für die gespeicherte Datei relevant ist.</span><span class="sxs-lookup"><span data-stu-id="27845-133">Make your suggested file name relevant to the file being saved.</span></span> <span data-ttu-id="27845-134">Beispielsweise können Sie wie in Word den vorhandenen Dateinamen vorschlagen, sofern vorhanden. Sie können auch die erste Zeile eines Dokuments vorschlagen, wenn der Benutzer eine noch nicht benannte Datei speichert.</span><span class="sxs-lookup"><span data-stu-id="27845-134">For example, like Word, you can suggest the existing file name if there is one, or the first line of a document if the user is saving a file that does not yet have a name.</span></span>

2.  **<span data-ttu-id="27845-135">Anzeigen von FileSavePicker und Speichern in die ausgewählte Datei</span><span class="sxs-lookup"><span data-stu-id="27845-135">Show the FileSavePicker and save to the picked file</span></span>**

    <span data-ttu-id="27845-136">Zeigen Sie die Dateiauswahl durch Aufrufen von [**PickSaveFileAsync**](https://msdn.microsoft.com/library/windows/apps/br207876) an.</span><span class="sxs-lookup"><span data-stu-id="27845-136">Display the file picker by calling [**PickSaveFileAsync**](https://msdn.microsoft.com/library/windows/apps/br207876).</span></span> <span data-ttu-id="27845-137">Nachdem die Benutzer den Namen, Dateityp und Speicherort angegeben und bestätigt haben, dass die Datei gespeichert wird, gibt **PickSaveFileAsync** ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekt zurück, das die gespeicherte Datei darstellt.</span><span class="sxs-lookup"><span data-stu-id="27845-137">After the user specifies the name, file type, and location, and confirms to save the file, **PickSaveFileAsync** returns a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) object that represents the saved file.</span></span> <span data-ttu-id="27845-138">Sie können diese Datei erfassen und verarbeiten, da sie jetzt über Lese- und Schreibzugriff verfügen.</span><span class="sxs-lookup"><span data-stu-id="27845-138">You can capture and process this file now that you have read and write access to it.</span></span>

    ```cs
    Windows.Storage.StorageFile file = await savePicker.PickSaveFileAsync();
        if (file != null)
        {
            // Prevent updates to the remote version of the file until
            // we finish making changes and call CompleteUpdatesAsync.
            Windows.Storage.CachedFileManager.DeferUpdates(file);
            // write to file
            await Windows.Storage.FileIO.WriteTextAsync(file, file.Name);
            // Let Windows know that we're finished changing the file so
            // the other app can update the remote version of the file.
            // Completing updates may require Windows to ask for user input.
            Windows.Storage.Provider.FileUpdateStatus status =
                await Windows.Storage.CachedFileManager.CompleteUpdatesAsync(file);
            if (status == Windows.Storage.Provider.FileUpdateStatus.Complete)
            {
                this.textBlock.Text = "File " + file.Name + " was saved.";
            }
            else
            {
                this.textBlock.Text = "File " + file.Name + " couldn't be saved.";
            }
        }
        else
        {
            this.textBlock.Text = "Operation cancelled.";
        }
    ```

<span data-ttu-id="27845-139">Im Beispiel wird überprüft, ob die Datei gültig ist. Danach wird der eigene Dateiname in die Datei geschrieben.</span><span class="sxs-lookup"><span data-stu-id="27845-139">The example checks that the file is valid and writes its own file name into it.</span></span> <span data-ttu-id="27845-140">Weitere Informationen finden Sie unter [Erstellen, Lesen und Schreiben einer Datei](quickstart-reading-and-writing-files.md)</span><span class="sxs-lookup"><span data-stu-id="27845-140">Also see [Creating, writing, and reading a file](quickstart-reading-and-writing-files.md).</span></span>

<span data-ttu-id="27845-141">**Tipp:** sollten Sie die gespeicherte Datei, um sicherzustellen, dass es ist zulässig, vor dem Durchführen einer weiteren Verarbeitung immer überprüfen.</span><span class="sxs-lookup"><span data-stu-id="27845-141">**Tip**You should always check the saved file to make sure it is valid before you perform any other processing.</span></span> <span data-ttu-id="27845-142">Anschließend können Sie Inhalte dem Zweck der App entsprechend in der Datei speichern und das Verhalten für den Fall festlegen, dass die ausgewählte Datei nicht gültig ist.</span><span class="sxs-lookup"><span data-stu-id="27845-142">Then, you can save content to the file as appropriate for your app, and provide appropriate behavior if the picked file is not valid.</span></span>
