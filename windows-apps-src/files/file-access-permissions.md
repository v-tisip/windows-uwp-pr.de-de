---
author: laurenhughes
ms.assetid: 3A404CC0-A997-45C8-B2E8-44745539759D
title: Berechtigungen für den Dateizugriff
description: Apps können standardmäßig auf bestimmte Dateisystemspeicherorte zugreifen. Apps können darüber hinaus mithilfe der Dateiauswahl oder durch die Deklaration von Funktionen auf weitere Speicherorte zugreifen.
ms.author: lahugh
ms.date: 3/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: dc4f3532f2aebd84c8194586b3fdaad45146ff8d
ms.sourcegitcommit: cceaf2206ec53a3e9155f97f44e4795a7b6a1d78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
ms.locfileid: "1701166"
---
# <a name="file-access-permissions"></a><span data-ttu-id="4feb7-105">Berechtigungen für den Dateizugriff</span><span class="sxs-lookup"><span data-stu-id="4feb7-105">File access permissions</span></span>


<span data-ttu-id="4feb7-106">Universelle Windows-Apps (Apps) können standardmäßig auf bestimmte Dateisystemspeicherorte zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-106">Universal Windows Apps (apps) can access certain file system locations by default.</span></span> <span data-ttu-id="4feb7-107">Apps können außerdem mithilfe der Dateiauswahl oder durch die Deklaration von Funktionen auf weitere Speicherorte zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-107">Apps can also access additional locations through the file picker, or by declaring capabilities.</span></span>

## <a name="the-locations-that-all-apps-can-access"></a><span data-ttu-id="4feb7-108">Für alle Apps zugängliche Speicherorte</span><span class="sxs-lookup"><span data-stu-id="4feb7-108">The locations that all apps can access</span></span>

<span data-ttu-id="4feb7-109">Bei Erstellung einer neuen App können Sie standardmäßig auf folgende Dateisystemspeicherorte zugreifen:</span><span class="sxs-lookup"><span data-stu-id="4feb7-109">When you create a new app, you can access the following file system locations by default:</span></span>

-   <span data-ttu-id="4feb7-110">**Installationsverzeichnis von Anwendungen**</span><span class="sxs-lookup"><span data-stu-id="4feb7-110">**Application install directory**.</span></span> <span data-ttu-id="4feb7-111">Der Ordner, in welchem Ihre Anwendung im System des Benutzers installiert ist.</span><span class="sxs-lookup"><span data-stu-id="4feb7-111">The folder where your app is installed on the user’s system.</span></span>

    <span data-ttu-id="4feb7-112">Es gibt im Wesentlichen zwei Möglichkeiten, auf Dateien und Ordner im Installationsverzeichnis Ihrer App zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-112">There are two primary ways to access files and folders in your app’s install directory:</span></span>

    1.  <span data-ttu-id="4feb7-113">Sie können auf folgende Weise einen [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) aufrufen, der das Installationsverzeichnis Ihrer App darstellt:</span><span class="sxs-lookup"><span data-stu-id="4feb7-113">You can retrieve a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) that represents your app's install directory, like this:</span></span>
        > [!div class="tabbedCodeSnippets"]
        ```cs
        Windows.Storage.StorageFolder installedLocation = Windows.ApplicationModel.Package.Current.InstalledLocation;
        ```
        ```javascript
        var installDirectory = Windows.ApplicationModel.Package.current.installedLocation;
        ```
        ```cpp
        Windows::Storage::StorageFolder^ installedLocation = Windows::ApplicationModel::Package::Current->InstalledLocation;
        ```

       <span data-ttu-id="4feb7-114">Sie können anschließend mithilfe von [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230)-Methoden auf Dateien und Ordner im Verzeichnis zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-114">You can then access files and folders in the directory using [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) methods.</span></span> <span data-ttu-id="4feb7-115">Im Beispiel wird dieser **StorageFolder** in der `installDirectory`-Variablen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="4feb7-115">In the example, this **StorageFolder** is stored in the `installDirectory` variable.</span></span> <span data-ttu-id="4feb7-116">Sie können das [Informationsbeispiel des Anwendungspakets](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Package) von GitHub herunterladen, um mehr über die Arbeit mit dem App-Paket und dem Installationsverzeichnis zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="4feb7-116">You can learn more about working with your app package and install directory from the [App package information sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Package) on GitHub.</span></span>

    2.  <span data-ttu-id="4feb7-117">Sie können eine Datei direkt aus dem Installationsverzeichnis Ihrer Anwendung mithilfe der Anwendungs-URI wie folgt aufrufen:</span><span class="sxs-lookup"><span data-stu-id="4feb7-117">You can retrieve a file directly from your app's install directory by using an app URI, like this:</span></span>
        > [!div class="tabbedCodeSnippets"]
        ```cs
        using Windows.Storage;            
        StorageFile file = await StorageFile.GetFileFromApplicationUriAsync(new Uri("ms-appx:///file.txt"));
        ```
        ```javascript
        Windows.Storage.StorageFile.getFileFromApplicationUriAsync("ms-appx:///file.txt").done(
            function(file) {
                // Process file
            }
        );
        ```
        ```cpp
        auto getFileTask = create_task(StorageFile::GetFileFromApplicationUriAsync(ref new Uri("ms-appx:///file.txt")));
        getFileTask.then([](StorageFile^ file) 
        {
            // Process file
        });
        ```

        <span data-ttu-id="4feb7-118">Nach vollständiger Ausführung von [**GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) wird ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) zurückgegeben, das die Datei `file.txt` im Installationsverzeichnis der App darstellt (`file` im Beispiel).</span><span class="sxs-lookup"><span data-stu-id="4feb7-118">When [**GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) completes, it returns a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) that represents the `file.txt` file in the app's install directory (`file` in the example).</span></span>

        <span data-ttu-id="4feb7-119">Das Präfix „ms-appx:///“ in der URI bezieht sich auf das Installationsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="4feb7-119">The "ms-appx:///" prefix in the URI refers to the app's install directory.</span></span> <span data-ttu-id="4feb7-120">Weitere Informationen zur Verwendung von App-URIs finden Sie unter [Verwenden von URIs zum Verweisen auf Inhalte](https://msdn.microsoft.com/library/windows/apps/hh781215).</span><span class="sxs-lookup"><span data-stu-id="4feb7-120">You can learn more about using app URIs in [How to use URIs to reference content](https://msdn.microsoft.com/library/windows/apps/hh781215).</span></span>

    <span data-ttu-id="4feb7-121">Darüber hinaus können Sie im Gegensatz zu anderen Speicherorten auf das Installationsverzeichnis Ihrer App auch direkt mit [Win32 und COM für UWP-Apps (Universelle Windows-Plattform)](https://msdn.microsoft.com/library/windows/apps/br205757) und einigen [Funktionen der C/C++-Standardbibliothek in Microsoft Visual Studio](http://msdn.microsoft.com/library/hh875057.aspx) zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-121">In addition, and unlike other locations, you can also access files in your app install directory by using some [Win32 and COM for Universal Windows Platform (UWP) apps](https://msdn.microsoft.com/library/windows/apps/br205757) and some [C/C++ Standard Library functions from Microsoft Visual Studio](http://msdn.microsoft.com/library/hh875057.aspx).</span></span>

    <span data-ttu-id="4feb7-122">Das Installationsverzeichnis der Anwendung ist ein schreibgeschützter Speicherort.</span><span class="sxs-lookup"><span data-stu-id="4feb7-122">The app's install directory is a read-only location.</span></span> <span data-ttu-id="4feb7-123">Sie können nicht über die Dateiauswahl auf das Installationsverzeichnis zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-123">You can’t gain access to the install directory through the file picker.</span></span>

-   **<span data-ttu-id="4feb7-124">Speicherorte von Anwendungsdaten.</span><span class="sxs-lookup"><span data-stu-id="4feb7-124">Application data locations.</span></span>** <span data-ttu-id="4feb7-125">Die Ordner, in denen Ihre App Daten speichern kann.</span><span class="sxs-lookup"><span data-stu-id="4feb7-125">The folders where your app can store data.</span></span> <span data-ttu-id="4feb7-126">Diese Ordner (lokal, servergespeichert und temporär) werden nach Installation Ihrer Anwendung erstellt.</span><span class="sxs-lookup"><span data-stu-id="4feb7-126">These folders (local, roaming and temporary) are created when your app is installed.</span></span>

    <span data-ttu-id="4feb7-127">Es gibt im Wesentlichen zwei Möglichkeiten, auf Dateien und Ordner in den Dateispeicherorten Ihrer Anwendung zuzugreifen:</span><span class="sxs-lookup"><span data-stu-id="4feb7-127">There are two primary ways to access files and folders from your app’s data locations:</span></span>

    1.  <span data-ttu-id="4feb7-128">Verwenden Sie die [**ApplicationData**](https://msdn.microsoft.com/library/windows/apps/br241587)-Eigenschaften, um einen Dateiordner abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-128">Use [**ApplicationData**](https://msdn.microsoft.com/library/windows/apps/br241587) properties to retrieve an app data folder.</span></span>

        <span data-ttu-id="4feb7-129">Sie können zum Beispiel [**ApplicationData**](https://msdn.microsoft.com/library/windows/apps/br241587).[**LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621) verwenden, um einen [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) abzurufen, der den lokalen Ordner Ihrer Anwendung wie folgt darstellt:</span><span class="sxs-lookup"><span data-stu-id="4feb7-129">For example, you can use [**ApplicationData**](https://msdn.microsoft.com/library/windows/apps/br241587).[**LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621) to retrieve a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) that represents your app's local folder like this:</span></span>
        > [!div class="tabbedCodeSnippets"]
        ```cs
        using Windows.Storage;
        StorageFolder localFolder = ApplicationData.Current.LocalFolder;
        ```
        ```javascript
        var localFolder = Windows.Storage.ApplicationData.current.localFolder;
        ```
        ```cpp
        using namespace Windows::Storage;
        StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
        ```

        <span data-ttu-id="4feb7-130">Wenn Sie auf den servergespeicherten oder temporären Ordner Ihrer Anwendung zugreifen möchten, verwenden Sie stattdessen die [**RoamingFolder**](https://msdn.microsoft.com/library/windows/apps/br241623)- oder [**TemporaryFolder**](https://msdn.microsoft.com/library/windows/apps/br241629)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4feb7-130">If you want to access your app's roaming or temporary folder, use the [**RoamingFolder**](https://msdn.microsoft.com/library/windows/apps/br241623) or [**TemporaryFolder**](https://msdn.microsoft.com/library/windows/apps/br241629) property instead.</span></span>

        <span data-ttu-id="4feb7-131">Nach dem Aufrufen des [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230), der den Dateispeicherort der Anwendung darstellt, können Sie auf Dateien und Ordner im Verzeichnis mithilfe der **StorageFolder**-Methode zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-131">After you retrieve a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) that represents an app data location, you can access files and folders in that location by using **StorageFolder** methods.</span></span> <span data-ttu-id="4feb7-132">Im Beispiel werden diese **StorageFolder**-Objekte in der `localFolder`-Variablen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="4feb7-132">In the example, these **StorageFolder** objects are stored in the `localFolder` variable.</span></span> <span data-ttu-id="4feb7-133">Weitere Informationen zum Verwenden der Speicherorte von App-Daten finden Sie unter [ApplicationData-Klasse](https://docs.microsoft.com/uwp/api/windows.storage.applicationdata). Sie können auch das [Beispiel für Anwendungsdaten](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationData) von GitHub herunterladen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-133">You can learn more about using app data locations from the guidance on the [ApplicationData class](https://docs.microsoft.com/uwp/api/windows.storage.applicationdata) page, and by downloading the [Application data sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationData) from GitHub.</span></span>

    2.  <span data-ttu-id="4feb7-134">Sie können eine Datei zum Beispiel mithilfe der Anwendungs-URI direkt aus dem lokalen Ordner Ihrer Anwendung wie folgt aufrufen:</span><span class="sxs-lookup"><span data-stu-id="4feb7-134">For example, you can retrieve a file directly from your app's local folder by using an app URI, like this:</span></span>
        > [!div class="tabbedCodeSnippets"]
        ```cs
        using Windows.Storage;
        StorageFile file = await StorageFile.GetFileFromApplicationUriAsync(new Uri("ms-appdata:///local/file.txt"));
        ```
        ```javascript
        Windows.Storage.StorageFile.getFileFromApplicationUriAsync("ms-appdata:///local/file.txt").done(
            function(file) {
                // Process file
            }
        );
        ```
        ```cpp
        using Windows::Storage;
        auto getFileTask = create_task(StorageFile::GetFileFromApplicationUriAsync(ref new Uri("ms-appdata:///local/file.txt")));
        getFileTask.then([](StorageFile^ file) 
        {
            // Process file
        });
        ```

        <span data-ttu-id="4feb7-135">Nach vollständiger Ausführung von [**GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) wird ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) zurückgegeben, das die Datei `file.txt` im lokalen Ordner der App darstellt (`file` im Beispiel).</span><span class="sxs-lookup"><span data-stu-id="4feb7-135">When [**GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) completes, it returns a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) that represents the `file.txt` file in the app's local folder (`file` in the example).</span></span>

        <span data-ttu-id="4feb7-136">Das Präfix „ms-appdata:///local/“ in der URI bezieht sich auf den lokalen Ordner der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="4feb7-136">The "ms-appdata:///local/" prefix in the URI refers to the app's local folder.</span></span> <span data-ttu-id="4feb7-137">Für den Zugriff auf Dateien in servergespeicherten oder temporären Ordnern verwenden Sie „ms-appdata:///roaming/“ oder „ms-appdata:///temporary/“.</span><span class="sxs-lookup"><span data-stu-id="4feb7-137">To access files in the app's roaming or temporary folders use "ms-appdata:///roaming/" or "ms-appdata:///temporary/" instead.</span></span> <span data-ttu-id="4feb7-138">Weitere Informationen zur Verwendung von Anwendungs-URIs finden Sie in [So wird's gemacht: Laden von Dateiressourcen](https://msdn.microsoft.com/library/windows/apps/hh781229).</span><span class="sxs-lookup"><span data-stu-id="4feb7-138">You can learn more about using app URIs in [How to load file resources](https://msdn.microsoft.com/library/windows/apps/hh781229).</span></span>

    <span data-ttu-id="4feb7-139">Darüber hinaus können Sie, im Gegensatz zu anderen Speicherorten, auf Dateien in den App-Datenspeicherorten auch mit [Win32 und COM für UWP-Apps (Universelle Windows-Plattform)](https://msdn.microsoft.com/library/windows/apps/br205757) und einigen Funktionen der C/C++-Standardbibliothek in Microsoft Visual Studio zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-139">In addition, and unlike other locations, you can also access files in your app data locations by using some [Win32 and COM for UWP apps](https://msdn.microsoft.com/library/windows/apps/br205757) and some C/C++ Standard Library functions from Visual Studio.</span></span>

    <span data-ttu-id="4feb7-140">Sie können nicht über die Dateiauswahl auf lokale, servergespeicherte oder temporäre Ordner zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-140">You can’t access the local, roaming, or temporary folders through the file picker.</span></span>

-   **<span data-ttu-id="4feb7-141">Wechselmedien.</span><span class="sxs-lookup"><span data-stu-id="4feb7-141">Removable devices.</span></span>** <span data-ttu-id="4feb7-142">Darüber hinaus kann Ihre App standardmäßig auf einige der Dateien auf verbundenen Geräten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-142">Additionally, your app can access some of the files on connected devices by default.</span></span> <span data-ttu-id="4feb7-143">Diese Möglichkeit besteht, wenn Ihre App die [Erweiterung für die automatische Wiedergabe](https://msdn.microsoft.com/library/windows/apps/xaml/hh464906.aspx#autoplay) verwendet, die automatisch gestartet wird, sobald Benutzer ein Gerät, wie eine Kamera oder einen USB-Speicherstick, an Ihr System anschließen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-143">This is an option if your app uses the [AutoPlay extension](https://msdn.microsoft.com/library/windows/apps/xaml/hh464906.aspx#autoplay) to launch automatically when users connect a device, like a camera or USB thumb drive, to their system.</span></span> <span data-ttu-id="4feb7-144">Die Dateien, auf welche Ihre App zugreifen kann, sind auf bestimmte Dateitypen begrenzt, die über Deklarationen von Dateitypzuordnungen in Ihrem App-Manifest festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="4feb7-144">The files your app can access are limited to specific file types that are specified via File Type Association declarations in your app manifest.</span></span>

    <span data-ttu-id="4feb7-145">Sie können natürlich auch auf Dateien und Ordner auf einem Wechselmedium mithilfe der Dateiauswahl zugreifen (unter Verwendung von [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) und [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881)) und den Benutzer die Dateien und Ordner auswählen lassen, auf welche Ihre App Zugriff haben soll.</span><span class="sxs-lookup"><span data-stu-id="4feb7-145">Of course, you can also gain access to files and folders on a removable device by calling the file picker (using [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) and [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881)) and letting the user pick files and folders for your app to access.</span></span> <span data-ttu-id="4feb7-146">Weitere Informationen zur Verwendung der Dateiauswahl finden Sie unter [Öffnen von Dateien und Ordnern mit einer Auswahl](quickstart-using-file-and-folder-pickers.md).</span><span class="sxs-lookup"><span data-stu-id="4feb7-146">Learn how to use the file picker in [Open files and folders with a picker](quickstart-using-file-and-folder-pickers.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="4feb7-147">Weitere Informationen zum Zugriff auf eine SD-Karte oder andere Wechselgeräte finden Sie unter [Zugreifen auf die SD-Karte](access-the-sd-card.md).</span><span class="sxs-lookup"><span data-stu-id="4feb7-147">For more info about accessing an SD card or other removable devices, see [Access the SD card](access-the-sd-card.md).</span></span>

     

## <a name="locations-uwp-apps-can-access"></a><span data-ttu-id="4feb7-148">Für alle UWP-Apps zugängliche Speicherorte</span><span class="sxs-lookup"><span data-stu-id="4feb7-148">Locations UWP apps can access</span></span>

-   **<span data-ttu-id="4feb7-149">Downloadordner des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="4feb7-149">User’s Downloads folder.</span></span>** <span data-ttu-id="4feb7-150">Der Ordner, in dem heruntergeladene Dateien standardmäßig gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="4feb7-150">The folder where downloaded files are saved by default.</span></span>

    <span data-ttu-id="4feb7-151">Standardmäßig kann Ihre Anwendung nur auf Dateien und Ordner im Ordner "Downloads" des Benutzers zugreifen, die von Ihrer App erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="4feb7-151">By default, your app can only access files and folders in the user's Downloads folder that your app created.</span></span> <span data-ttu-id="4feb7-152">Sie können jedoch durch Aufrufen der Dateiauswahl auf weitere Dateien und Ordner im Downloadordner des Benutzers zugreifen ([**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) oder [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881)), sodass Benutzer zu Dateien oder Ordner navigieren und diese auswählen können und Ihre Anwendung Zugriff auf diese erhält.</span><span class="sxs-lookup"><span data-stu-id="4feb7-152">However, you can gain access to files and folders in the user's Downloads folder by calling a file picker ([**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) or [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881)) so that users can navigate and pick files or folders for your app to access.</span></span>

    -   <span data-ttu-id="4feb7-153">Sie können im Downloadordner des Benutzers eine Datei wie folgt erstellen:</span><span class="sxs-lookup"><span data-stu-id="4feb7-153">You can create a file in the user's Downloads folder like this:</span></span>
        > [!div class="tabbedCodeSnippets"]
        ```cs
        using Windows.Storage;
        StorageFile newFile = await DownloadsFolder.CreateFileAsync("file.txt");
        ```
        ```javascript
        Windows.Storage.DownloadsFolder.createFileAsync("file.txt").done(
            function(newFile) {
                // Process file
            }
        );
        ```
        ```cpp
        using Windows::Storage;
        auto createFileTask = create_task(DownloadsFolder::CreateFileAsync(L"file.txt"));
        createFileTask.then([](StorageFile^ newFile)
        {
            // Process file
        });
        ```

        <span data-ttu-id="4feb7-154">[**DownloadsFolder**](https://msdn.microsoft.com/library/windows/apps/br241632).[**CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh996761) wird überladen, sodass Sie festlegen können, was das System im Fall einer bereits vorhandenen gleichnamigen Datei im Downloadordner des Benutzers tun sollte.</span><span class="sxs-lookup"><span data-stu-id="4feb7-154">[**DownloadsFolder**](https://msdn.microsoft.com/library/windows/apps/br241632).[**CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh996761) is overloaded so that you can specify what the system should do if there is already an existing file in the Downloads folder that has the same name.</span></span> <span data-ttu-id="4feb7-155">Nach vollständiger Ausführung dieser Methoden wird ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) zurückgegeben, das die erstellte Datei darstellt.</span><span class="sxs-lookup"><span data-stu-id="4feb7-155">When these methods complete, they return a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) that represents the file that was created.</span></span> <span data-ttu-id="4feb7-156">Diese Datei wird im Beispiel `newFile` genannt.</span><span class="sxs-lookup"><span data-stu-id="4feb7-156">This file is called `newFile` in the example.</span></span>

    -   <span data-ttu-id="4feb7-157">Sie können im Downloadordner des Benutzers wie folgt einen Unterordner erstellen:</span><span class="sxs-lookup"><span data-stu-id="4feb7-157">You can create a subfolder in the user's Downloads folder like this:</span></span>
        > [!div class="tabbedCodeSnippets"]
        ```cs
        using Windows.Storage;
        StorageFolder newFolder = await DownloadsFolder.CreateFolderAsync("New Folder");
        ```
        ```javascript
        Windows.Storage.DownloadsFolder.createFolderAsync("New Folder").done(
            function(newFolder) {
                // Process folder
            }
        );
        ```
        ```cpp
        using Windows::Storage;
        auto createFolderTask = create_task(DownloadsFolder::CreateFolderAsync(L"New Folder"));
        createFolderTask.then([](StorageFolder^ newFolder)
        {
            // Process folder
        });
        ```

        <span data-ttu-id="4feb7-158">[**DownloadsFolder**](https://msdn.microsoft.com/library/windows/apps/br241632).[**CreateFolderAsync**](https://msdn.microsoft.com/library/windows/apps/hh996763) wird überladen, sodass Sie festlegen können, was das System im Fall eines bereits vorhandenen gleichnamigen Unterordners im Ordner „Downloads“ des Benutzers tun sollte.</span><span class="sxs-lookup"><span data-stu-id="4feb7-158">[**DownloadsFolder**](https://msdn.microsoft.com/library/windows/apps/br241632).[**CreateFolderAsync**](https://msdn.microsoft.com/library/windows/apps/hh996763) is overloaded so that you can specify what the system should do if there is already an existing subfolder in the Downloads folder that has the same name.</span></span> <span data-ttu-id="4feb7-159">Nach vollständiger Ausführung dieser Methoden wird ein [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) zurückgegeben, der den erstellten Unterordner darstellt.</span><span class="sxs-lookup"><span data-stu-id="4feb7-159">When these methods complete, they return a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) that represents the subfolder that was created.</span></span> <span data-ttu-id="4feb7-160">Diese Datei wird im Beispiel `newFolder` genannt.</span><span class="sxs-lookup"><span data-stu-id="4feb7-160">This file is called `newFolder` in the example.</span></span>

    <span data-ttu-id="4feb7-161">Wenn Sie eine Datei oder einen Ordner im Downloadordner erstellen, empfehlen wir, die Datei oder den Ordner der [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) Ihrer App hinzuzufügen, sodass zukünftig leicht auf dieses Element zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="4feb7-161">If you create a file or folder in the Downloads folder, we recommend that you add that item to your app's [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) so that your app can readily access that item in the future.</span></span>

## <a name="accessing-additional-locations"></a><span data-ttu-id="4feb7-162">Zugriff auf zusätzliche Speicherorte</span><span class="sxs-lookup"><span data-stu-id="4feb7-162">Accessing additional locations</span></span>

<span data-ttu-id="4feb7-163">Zusätzlich zu den Standardspeicherorten kann eine App durch das Deklarieren von Funktionen im App-Manifest (siehe [Deklaration der App-Funktionen](https://msdn.microsoft.com/library/windows/apps/mt270968)) oder durch Aufrufen der Dateiauswahl auf zusätzliche Dateien und Ordner zugreifen, um den Benutzer Dateien und Ordner auswählen zu lassen, auf welche die App Zugriff haben soll (siehe [Öffnen von Dateien und Ordnern mit einer Auswahl](quickstart-using-file-and-folder-pickers.md)).</span><span class="sxs-lookup"><span data-stu-id="4feb7-163">In addition to the default locations, an app can access additional files and folders by declaring capabilities in the app manifest (see [App capability declarations](https://msdn.microsoft.com/library/windows/apps/mt270968)), or by calling a file picker to let the user pick files and folders for the app to access (see [Open files and folders with a picker](quickstart-using-file-and-folder-pickers.md)).</span></span>

<span data-ttu-id="4feb7-164">App, die die [AppExecutionAlias](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-appexecutionalias)-Erweiterung deklarieren, haben Dateisystemberechtigungen für das Verzeichnis, aus dem sie im Konsolenfenster gestartet werden, und darunter liegende Verzeichnisse.</span><span class="sxs-lookup"><span data-stu-id="4feb7-164">App's that that declare the [AppExecutionAlias](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-appexecutionalias) extension, have file-system permissions from the directory that they are launched from in the console window, and downwards.</span></span>

<span data-ttu-id="4feb7-165">In der folgenden Tabelle sind weitere Speicherorte aufgeführt, auf die Sie durch Deklarieren von Funktionen und Verwenden der zugehörigen [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/br227346)-APIs zugreifen können:</span><span class="sxs-lookup"><span data-stu-id="4feb7-165">The following table lists additional locations that you can access by declaring a capability (or capabilities) and using the associated [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/br227346) API:</span></span>

| <span data-ttu-id="4feb7-166">Ort</span><span class="sxs-lookup"><span data-stu-id="4feb7-166">Location</span></span> | <span data-ttu-id="4feb7-167">Funktion</span><span class="sxs-lookup"><span data-stu-id="4feb7-167">Capability</span></span> | <span data-ttu-id="4feb7-168">Windows.Storage-API</span><span class="sxs-lookup"><span data-stu-id="4feb7-168">Windows.Storage API</span></span> |
|----------|------------|---------------------|
| <span data-ttu-id="4feb7-169">Alle Dateien, auf die der Benutzer Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="4feb7-169">All files that the user has access to.</span></span> <span data-ttu-id="4feb7-170">Beispiel: Dokumente, Bilder, Fotos, Downloads, Desktop, OneDrive usw.</span><span class="sxs-lookup"><span data-stu-id="4feb7-170">For example: documents, pictures, photos, downloads, desktop, OneDrive, etc.</span></span> | <span data-ttu-id="4feb7-171">broadFileSystemAccess</span><span class="sxs-lookup"><span data-stu-id="4feb7-171">broadFileSystemAccess</span></span><br><br><span data-ttu-id="4feb7-172">Dies ist eine eingeschränkte Funktion.</span><span class="sxs-lookup"><span data-stu-id="4feb7-172">This is a restricted capability.</span></span> <span data-ttu-id="4feb7-173">Bei der ersten Verwendung fordert das System den Benutzer auf, den Zugriff zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="4feb7-173">On first use, the system will prompt the user to allow access.</span></span> <span data-ttu-id="4feb7-174">Der Zugriff kann unter Einstellungen > Datenschutz > Dateisystem konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="4feb7-174">Access is configurable in Settings > Privacy > File system.</span></span> <span data-ttu-id="4feb7-175">Wenn Sie eine App an den Store übermitteln, die diese Funktion deklariert, müssen Sie zusätzliche Beschreibungen dazu bereitstellen, warum die App diese Funktion benötigt und wie sie diese verwenden wird.</span><span class="sxs-lookup"><span data-stu-id="4feb7-175">If you submit an app to the Store that declares this capability, you will need to supply additional descriptions of why your app needs this capability, and how it intends to use it.</span></span><br><span data-ttu-id="4feb7-176">Diese Funktion funktioniert für APIs im [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="4feb7-176">This capability works for APIs in the [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346) namespace</span></span> | <span data-ttu-id="4feb7-177">n.a.</span><span class="sxs-lookup"><span data-stu-id="4feb7-177">n/a</span></span> |
| <span data-ttu-id="4feb7-178">Dokumente</span><span class="sxs-lookup"><span data-stu-id="4feb7-178">Documents</span></span> | <span data-ttu-id="4feb7-179">DocumentsLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-179">DocumentsLibrary</span></span> <br><br><span data-ttu-id="4feb7-180">Hinweis: Sie müssen Ihrem App-Manifest Dateitypzuordnungen hinzufügen, die bestimmte Dateitypen deklarieren, auf die Ihre App an diesem Speicherort Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="4feb7-180">Note: You must add File Type Associations to your app manifest that declare specific file types that your app can access in this location.</span></span> <br><br><span data-ttu-id="4feb7-181">Verwenden Sie diese Funktion, wenn Ihre App:</span><span class="sxs-lookup"><span data-stu-id="4feb7-181">Use this capability if your app:</span></span><br><span data-ttu-id="4feb7-182">- Den plattformübergreifenden Offlinezugriff auf bestimmte OneDrive-Inhalte mit gültigen OneDrive-URLs oder Ressourcen-IDs ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="4feb7-182">- Facilitates cross-platform offline access to specific OneDrive content using valid OneDrive URLs or Resource IDs</span></span><br><span data-ttu-id="4feb7-183">- Geöffnete Dateien im Offlinezustand automatisch im OneDrive des Benutzers speichert.</span><span class="sxs-lookup"><span data-stu-id="4feb7-183">- Saves open files to the user’s OneDrive automatically while offline</span></span> | [<span data-ttu-id="4feb7-184">KnownFolders.DocumentsLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-184">KnownFolders.DocumentsLibrary</span></span>](https://msdn.microsoft.com/library/windows/apps/br227152) |
| <span data-ttu-id="4feb7-185">Musik</span><span class="sxs-lookup"><span data-stu-id="4feb7-185">Music</span></span>     | <span data-ttu-id="4feb7-186">MusicLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-186">MusicLibrary</span></span> <br><span data-ttu-id="4feb7-187">Weitere Informationen finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="4feb7-187">Also see [Files and folders in the Music, Pictures, and Videos libraries](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span> | [<span data-ttu-id="4feb7-188">KnownFolders.MusicLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-188">KnownFolders.MusicLibrary</span></span>](https://msdn.microsoft.com/library/windows/apps/br227155) |    
| <span data-ttu-id="4feb7-189">Bilder</span><span class="sxs-lookup"><span data-stu-id="4feb7-189">Pictures</span></span>  | <span data-ttu-id="4feb7-190">PicturesLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-190">PicturesLibrary</span></span><br> <span data-ttu-id="4feb7-191">Weitere Informationen finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="4feb7-191">Also see [Files and folders in the Music, Pictures, and Videos libraries](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span> | [<span data-ttu-id="4feb7-192">KnownFolders.PicturesLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-192">KnownFolders.PicturesLibrary</span></span>](https://msdn.microsoft.com/library/windows/apps/br227156) |  
| <span data-ttu-id="4feb7-193">Videos</span><span class="sxs-lookup"><span data-stu-id="4feb7-193">Videos</span></span>    | <span data-ttu-id="4feb7-194">VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-194">VideosLibrary</span></span><br><span data-ttu-id="4feb7-195">Weitere Informationen finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="4feb7-195">Also see [Files and folders in the Music, Pictures, and Videos libraries](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span> | [<span data-ttu-id="4feb7-196">KnownFolders.VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-196">KnownFolders.VideosLibrary</span></span>](https://msdn.microsoft.com/library/windows/apps/br227159) |   
| <span data-ttu-id="4feb7-197">Wechselmedien</span><span class="sxs-lookup"><span data-stu-id="4feb7-197">Removable devices</span></span>  | <span data-ttu-id="4feb7-198">RemovableDevices</span><span class="sxs-lookup"><span data-stu-id="4feb7-198">RemovableDevices</span></span> <br><br><span data-ttu-id="4feb7-199">Hinweis: Sie müssen Ihrem App-Manifest Dateitypzuordnungen hinzufügen, die bestimmte Dateitypen deklarieren, auf die Ihre App an diesem Speicherort Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="4feb7-199">Note  You must add File Type Associations to your app manifest that declare specific file types that your app can access in this location.</span></span> <br><br><span data-ttu-id="4feb7-200">Weitere Informationen finden Sie unter [Zugreifen auf die SD-Karte](access-the-sd-card.md).</span><span class="sxs-lookup"><span data-stu-id="4feb7-200">Also see [Access the SD card](access-the-sd-card.md).</span></span> | [<span data-ttu-id="4feb7-201">KnownFolders.RemovableDevices</span><span class="sxs-lookup"><span data-stu-id="4feb7-201">KnownFolders.RemovableDevices</span></span>](https://msdn.microsoft.com/library/windows/apps/br227158) |  
| <span data-ttu-id="4feb7-202">Bibliotheken der Heimnetzgruppen</span><span class="sxs-lookup"><span data-stu-id="4feb7-202">Homegroup libraries</span></span>  | <span data-ttu-id="4feb7-203">Mindestens eine der folgenden Funktionen ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4feb7-203">At least one of the following capabilities is needed.</span></span> <br><span data-ttu-id="4feb7-204">– MusicLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-204">- MusicLibrary</span></span> <br><span data-ttu-id="4feb7-205">– PicturesLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-205">- PicturesLibrary</span></span> <br><span data-ttu-id="4feb7-206">– VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-206">- VideosLibrary</span></span> | [<span data-ttu-id="4feb7-207">KnownFolders.HomeGroup</span><span class="sxs-lookup"><span data-stu-id="4feb7-207">KnownFolders.HomeGroup</span></span>](https://msdn.microsoft.com/library/windows/apps/br227153) |      
| <span data-ttu-id="4feb7-208">Medienservergeräte (DLNA)</span><span class="sxs-lookup"><span data-stu-id="4feb7-208">Media server devices (DLNA)</span></span> | <span data-ttu-id="4feb7-209">Mindestens eine der folgenden Funktionen ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4feb7-209">At least one of the following capabilities is needed.</span></span> <br><span data-ttu-id="4feb7-210">– MusicLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-210">- MusicLibrary</span></span> <br><span data-ttu-id="4feb7-211">– PicturesLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-211">- PicturesLibrary</span></span> <br><span data-ttu-id="4feb7-212">– VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="4feb7-212">- VideosLibrary</span></span> | [<span data-ttu-id="4feb7-213">KnownFolders.MediaServerDevices</span><span class="sxs-lookup"><span data-stu-id="4feb7-213">KnownFolders.MediaServerDevices</span></span>](https://msdn.microsoft.com/library/windows/apps/br227154) |
| <span data-ttu-id="4feb7-214">Universal Naming Convention (UNC)-Ordner</span><span class="sxs-lookup"><span data-stu-id="4feb7-214">Universal Naming Convention (UNC) folders</span></span> | <span data-ttu-id="4feb7-215">Eine Kombination der folgenden Funktionen ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4feb7-215">A combination of the following capabilities is needed.</span></span> <br><br><span data-ttu-id="4feb7-216">Die Funktion für Heim- oder Arbeitsplatznetzwerke:</span><span class="sxs-lookup"><span data-stu-id="4feb7-216">The home and work networks capability:</span></span> <br><span data-ttu-id="4feb7-217">– PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="4feb7-217">- PrivateNetworkClientServer</span></span> <br><br><span data-ttu-id="4feb7-218">Zudem mindestens eine Funktion zu Internet und öffentlichen Netzwerken:</span><span class="sxs-lookup"><span data-stu-id="4feb7-218">And at least one internet and public networks capability:</span></span> <br><span data-ttu-id="4feb7-219">– InternetClient</span><span class="sxs-lookup"><span data-stu-id="4feb7-219">- InternetClient</span></span> <br><span data-ttu-id="4feb7-220">– InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="4feb7-220">- InternetClientServer</span></span> <br><br><span data-ttu-id="4feb7-221">Und gegebenenfalls die Funktion für Domänenanmeldeinformationen:</span><span class="sxs-lookup"><span data-stu-id="4feb7-221">And, if applicable, the domain credentials capability:</span></span><br><span data-ttu-id="4feb7-222">– EnterpriseAuthentication</span><span class="sxs-lookup"><span data-stu-id="4feb7-222">- EnterpriseAuthentication</span></span> <br><br><span data-ttu-id="4feb7-223">Hinweis: Sie müssen Ihrem App-Manifest Dateitypzuordnungen hinzufügen, die bestimmte Dateitypen deklarieren, auf die Ihre App an diesem Speicherort Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="4feb7-223">Note: You must add File Type Associations to your app manifest that declare specific file types that your app can access in this location.</span></span> | <span data-ttu-id="4feb7-224">Abrufen eines Ordners mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="4feb7-224">Retrieve a folder using:</span></span> <br>[<span data-ttu-id="4feb7-225">StorageFolder.GetFolderFromPathAsync</span><span class="sxs-lookup"><span data-stu-id="4feb7-225">StorageFolder.GetFolderFromPathAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/br227278) <br><br><span data-ttu-id="4feb7-226">Abrufen einer Datei mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="4feb7-226">Retrieve a file using:</span></span> <br>[<span data-ttu-id="4feb7-227">StorageFile.GetFileFromPathAsync</span><span class="sxs-lookup"><span data-stu-id="4feb7-227">StorageFile.GetFileFromPathAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/br227206) |

**<span data-ttu-id="4feb7-228">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4feb7-228">Example</span></span>**

<span data-ttu-id="4feb7-229">In diesem Beispiel wird die eingeschränkte `broadFileSystemAccess`-Funktion hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4feb7-229">This example adds the restricted `broadFileSystemAccess` capability.</span></span> <span data-ttu-id="4feb7-230">Zusätzlich zur Angabe der Funktion muss der `rescap`-Namespace muss hinzugefügt werden und wird auch zu `IgnorableNamespaces` hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="4feb7-230">In addition to specifying the capability, the `rescap` namespace must be added, and is also added to `IgnorableNamespaces`:</span></span>

``` xaml
<Package
  ...
  xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
  IgnorableNamespaces="uap mp uap5 rescap">

...
<Capabilities>
    <rescap:Capability Name="broadFileSystemAccess" />
</Capabilities>
```

> [!NOTE]
> <span data-ttu-id="4feb7-231">Eine vollständige Liste der App-Funktionen finden Sie unter [Deklarationen von App-Funktionen](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span><span class="sxs-lookup"><span data-stu-id="4feb7-231">For a complete list of app capabilities, see [App capability declarations](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span></span>
