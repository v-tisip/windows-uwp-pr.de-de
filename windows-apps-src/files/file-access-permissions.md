---
ms.assetid: 3A404CC0-A997-45C8-B2E8-44745539759D
title: Berechtigungen für den Dateizugriff
description: Apps können standardmäßig auf bestimmte Dateisystemspeicherorte zugreifen. Apps können darüber hinaus mithilfe der Dateiauswahl oder durch die Deklaration von Funktionen auf weitere Speicherorte zugreifen.
ms.date: 06/28/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 05ff8dd78f58910512291b819d59d68f682cc93c
ms.sourcegitcommit: 23748871459931fc838c5e259e4822bffcf3cdea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "8970935"
---
# <a name="file-access-permissions"></a><span data-ttu-id="9edc1-105">Berechtigungen für den Dateizugriff</span><span class="sxs-lookup"><span data-stu-id="9edc1-105">File access permissions</span></span>

<span data-ttu-id="9edc1-106">Universelle Windows-Apps (Apps) können standardmäßig auf bestimmte Dateisystemspeicherorte zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-106">Universal Windows Apps (apps) can access certain file system locations by default.</span></span> <span data-ttu-id="9edc1-107">Apps können außerdem mithilfe der Dateiauswahl oder durch die Deklaration von Funktionen auf weitere Speicherorte zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-107">Apps can also access additional locations through the file picker, or by declaring capabilities.</span></span>

## <a name="the-locations-that-all-apps-can-access"></a><span data-ttu-id="9edc1-108">Für alle Apps zugängliche Speicherorte</span><span class="sxs-lookup"><span data-stu-id="9edc1-108">The locations that all apps can access</span></span>

<span data-ttu-id="9edc1-109">Bei Erstellung einer neuen App können Sie standardmäßig auf folgende Dateisystemspeicherorte zugreifen:</span><span class="sxs-lookup"><span data-stu-id="9edc1-109">When you create a new app, you can access the following file system locations by default:</span></span>

### <a name="application-install-directory"></a><span data-ttu-id="9edc1-110">Installationsverzeichnis der Anwendung</span><span class="sxs-lookup"><span data-stu-id="9edc1-110">Application install directory</span></span>
<span data-ttu-id="9edc1-111">Der Ordner, in denen Ihre app auf dem System des Benutzers installiert ist.</span><span class="sxs-lookup"><span data-stu-id="9edc1-111">The folder where your app is installed on the user's system.</span></span>

<span data-ttu-id="9edc1-112">Es gibt zwei wesentlichen Möglichkeiten, greifen Sie auf Dateien und Ordner in Ihrer app Installationsverzeichnis:</span><span class="sxs-lookup"><span data-stu-id="9edc1-112">There are two primary ways to access files and folders in your app's install directory:</span></span>

1. <span data-ttu-id="9edc1-113">Sie können auf folgende Weise einen [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) aufrufen, der das Installationsverzeichnis Ihrer App darstellt:</span><span class="sxs-lookup"><span data-stu-id="9edc1-113">You can retrieve a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) that represents your app's install directory, like this:</span></span>

```csharp
Windows.Storage.StorageFolder installedLocation = Windows.ApplicationModel.Package.Current.InstalledLocation;
```

```javascript
var installDirectory = Windows.ApplicationModel.Package.current.installedLocation;
```

```cppwinrt
#include <winrt/Windows.Storage.h>
...
Windows::Storage::StorageFolder installedLocation{ Windows::ApplicationModel::Package::Current().InstalledLocation() };
```

```cpp
Windows::Storage::StorageFolder^ installedLocation = Windows::ApplicationModel::Package::Current->InstalledLocation;
```

<span data-ttu-id="9edc1-114">Sie können anschließend mithilfe von [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230)-Methoden auf Dateien und Ordner im Verzeichnis zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-114">You can then access files and folders in the directory using [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) methods.</span></span> <span data-ttu-id="9edc1-115">Im Beispiel wird dieser **StorageFolder** in der `installDirectory`-Variablen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="9edc1-115">In the example, this **StorageFolder** is stored in the `installDirectory` variable.</span></span> <span data-ttu-id="9edc1-116">Sie können das [Informationsbeispiel des Anwendungspakets](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Package) von GitHub herunterladen, um mehr über die Arbeit mit dem App-Paket und dem Installationsverzeichnis zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="9edc1-116">You can learn more about working with your app package and install directory from the [App package information sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Package) on GitHub.</span></span>

2. <span data-ttu-id="9edc1-117">Sie können eine Datei direkt aus dem Installationsverzeichnis Ihrer Anwendung mithilfe der Anwendungs-URI wie folgt aufrufen:</span><span class="sxs-lookup"><span data-stu-id="9edc1-117">You can retrieve a file directly from your app's install directory by using an app URI, like this:</span></span>

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

```cppwinrt
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    Windows::Storage::StorageFile file{
        co_await Windows::Storage::StorageFile::GetFileFromApplicationUriAsync(Windows::Foundation::Uri{L"ms-appx:///file.txt"})
    };
    // Process file
}
```

```cpp
auto getFileTask = create_task(StorageFile::GetFileFromApplicationUriAsync(ref new Uri("ms-appx:///file.txt")));
getFileTask.then([](StorageFile^ file) 
{
    // Process file
});
```

<span data-ttu-id="9edc1-118">Nach vollständiger Ausführung von [**GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) wird ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) zurückgegeben, das die Datei `file.txt` im Installationsverzeichnis der App darstellt (`file` im Beispiel).</span><span class="sxs-lookup"><span data-stu-id="9edc1-118">When [**GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) completes, it returns a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) that represents the `file.txt` file in the app's install directory (`file` in the example).</span></span>

<span data-ttu-id="9edc1-119">Das Präfix „ms-appx:///“ in der URI bezieht sich auf das Installationsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="9edc1-119">The "ms-appx:///" prefix in the URI refers to the app's install directory.</span></span> <span data-ttu-id="9edc1-120">Weitere Informationen zur Verwendung von App-URIs finden Sie unter [Verwenden von URIs zum Verweisen auf Inhalte](https://msdn.microsoft.com/library/windows/apps/hh781215).</span><span class="sxs-lookup"><span data-stu-id="9edc1-120">You can learn more about using app URIs in [How to use URIs to reference content](https://msdn.microsoft.com/library/windows/apps/hh781215).</span></span>

<span data-ttu-id="9edc1-121">Darüber hinaus können Sie im Gegensatz zu anderen Speicherorten auf das Installationsverzeichnis Ihrer App auch direkt mit [Win32 und COM für UWP-Apps (Universelle Windows-Plattform)](https://msdn.microsoft.com/library/windows/apps/br205757) und einigen [Funktionen der C/C++-Standardbibliothek in Microsoft Visual Studio](http://msdn.microsoft.com/library/hh875057.aspx) zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-121">In addition, and unlike other locations, you can also access files in your app install directory by using some [Win32 and COM for Universal Windows Platform (UWP) apps](https://msdn.microsoft.com/library/windows/apps/br205757) and some [C/C++ Standard Library functions from Microsoft Visual Studio](http://msdn.microsoft.com/library/hh875057.aspx).</span></span>

<span data-ttu-id="9edc1-122">Das Installationsverzeichnis der Anwendung ist ein schreibgeschützter Speicherort.</span><span class="sxs-lookup"><span data-stu-id="9edc1-122">The app's install directory is a read-only location.</span></span> <span data-ttu-id="9edc1-123">Sie können nicht über die Dateiauswahl auf das Installationsverzeichnis zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-123">You can't gain access to the install directory through the file picker.</span></span>

### <a name="application-data-locations"></a><span data-ttu-id="9edc1-124">Speicherorte von Anwendungsdaten</span><span class="sxs-lookup"><span data-stu-id="9edc1-124">Application data locations</span></span>
<span data-ttu-id="9edc1-125">Die Ordner, in denen Ihre App Daten speichern kann.</span><span class="sxs-lookup"><span data-stu-id="9edc1-125">The folders where your app can store data.</span></span> <span data-ttu-id="9edc1-126">Diese Ordner (lokal, servergespeichert und temporär) werden nach Installation Ihrer Anwendung erstellt.</span><span class="sxs-lookup"><span data-stu-id="9edc1-126">These folders (local, roaming and temporary) are created when your app is installed.</span></span>

<span data-ttu-id="9edc1-127">Es gibt zwei grundlegende Verfahren Zugriff auf Dateien und Ordner in den Dateispeicherorten Ihrer app:</span><span class="sxs-lookup"><span data-stu-id="9edc1-127">There are two primary ways to access files and folders from your app's data locations:</span></span>

1.  <span data-ttu-id="9edc1-128">Verwenden Sie die [**ApplicationData**](https://msdn.microsoft.com/library/windows/apps/br241587)-Eigenschaften, um einen Dateiordner abzurufen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-128">Use [**ApplicationData**](https://msdn.microsoft.com/library/windows/apps/br241587) properties to retrieve an app data folder.</span></span>

<span data-ttu-id="9edc1-129">Sie können zum Beispiel [**ApplicationData**](https://msdn.microsoft.com/library/windows/apps/br241587).[**LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621) verwenden, um einen [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) abzurufen, der den lokalen Ordner Ihrer Anwendung wie folgt darstellt:</span><span class="sxs-lookup"><span data-stu-id="9edc1-129">For example, you can use [**ApplicationData**](https://msdn.microsoft.com/library/windows/apps/br241587).[**LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621) to retrieve a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) that represents your app's local folder like this:</span></span>

```cs
using Windows.Storage;
StorageFolder localFolder = ApplicationData.Current.LocalFolder;
```

```javascript
var localFolder = Windows.Storage.ApplicationData.current.localFolder;
```

```cppwinrt
Windows::Storage::StorageFolder storageFolder{
    Windows::Storage::ApplicationData::Current().LocalFolder()
};
```

```cpp
using namespace Windows::Storage;
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
```

<span data-ttu-id="9edc1-130">Wenn Sie auf den servergespeicherten oder temporären Ordner Ihrer Anwendung zugreifen möchten, verwenden Sie stattdessen die [**RoamingFolder**](https://msdn.microsoft.com/library/windows/apps/br241623)- oder [**TemporaryFolder**](https://msdn.microsoft.com/library/windows/apps/br241629)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="9edc1-130">If you want to access your app's roaming or temporary folder, use the [**RoamingFolder**](https://msdn.microsoft.com/library/windows/apps/br241623) or [**TemporaryFolder**](https://msdn.microsoft.com/library/windows/apps/br241629) property instead.</span></span>

<span data-ttu-id="9edc1-131">Nach dem Aufrufen des [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230), der den Dateispeicherort der Anwendung darstellt, können Sie auf Dateien und Ordner im Verzeichnis mithilfe der **StorageFolder**-Methode zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-131">After you retrieve a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) that represents an app data location, you can access files and folders in that location by using **StorageFolder** methods.</span></span> <span data-ttu-id="9edc1-132">Im Beispiel werden diese **StorageFolder**-Objekte in der `localFolder`-Variablen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="9edc1-132">In the example, these **StorageFolder** objects are stored in the `localFolder` variable.</span></span> <span data-ttu-id="9edc1-133">Weitere Informationen zum Verwenden der Speicherorte von App-Daten finden Sie unter [ApplicationData-Klasse](https://docs.microsoft.com/uwp/api/windows.storage.applicationdata). Sie können auch das [Beispiel für Anwendungsdaten](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationData) von GitHub herunterladen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-133">You can learn more about using app data locations from the guidance on the [ApplicationData class](https://docs.microsoft.com/uwp/api/windows.storage.applicationdata) page, and by downloading the [Application data sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationData) from GitHub.</span></span>

2. <span data-ttu-id="9edc1-134">Sie können eine Datei zum Beispiel mithilfe der Anwendungs-URI direkt aus dem lokalen Ordner Ihrer Anwendung wie folgt aufrufen:</span><span class="sxs-lookup"><span data-stu-id="9edc1-134">For example, you can retrieve a file directly from your app's local folder by using an app URI, like this:</span></span>

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

```cppwinrt
Windows::Storage::StorageFile file{
    co_await Windows::Storage::StorageFile::GetFileFromApplicationUriAsync(Windows::Foundation::Uri{ L"ms-appdata:///local/file.txt" })
};
// Process file
```

```cpp
using Windows::Storage;
auto getFileTask = create_task(StorageFile::GetFileFromApplicationUriAsync(ref new Uri("ms-appdata:///local/file.txt")));
getFileTask.then([](StorageFile^ file) 
{
    // Process file
});
```

<span data-ttu-id="9edc1-135">Nach vollständiger Ausführung von [**GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) wird ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) zurückgegeben, das die Datei `file.txt` im lokalen Ordner der App darstellt (`file` im Beispiel).</span><span class="sxs-lookup"><span data-stu-id="9edc1-135">When [**GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) completes, it returns a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) that represents the `file.txt` file in the app's local folder (`file` in the example).</span></span>

<span data-ttu-id="9edc1-136">Das Präfix „ms-appdata:///local/“ in der URI bezieht sich auf den lokalen Ordner der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="9edc1-136">The "ms-appdata:///local/" prefix in the URI refers to the app's local folder.</span></span> <span data-ttu-id="9edc1-137">Für den Zugriff auf Dateien in servergespeicherten oder temporären Ordnern verwenden Sie „ms-appdata:///roaming/“ oder „ms-appdata:///temporary/“.</span><span class="sxs-lookup"><span data-stu-id="9edc1-137">To access files in the app's roaming or temporary folders use "ms-appdata:///roaming/" or "ms-appdata:///temporary/" instead.</span></span> <span data-ttu-id="9edc1-138">Weitere Informationen zur Verwendung von Anwendungs-URIs finden Sie in [So wird's gemacht: Laden von Dateiressourcen](https://msdn.microsoft.com/library/windows/apps/hh781229).</span><span class="sxs-lookup"><span data-stu-id="9edc1-138">You can learn more about using app URIs in [How to load file resources](https://msdn.microsoft.com/library/windows/apps/hh781229).</span></span>

<span data-ttu-id="9edc1-139">Darüber hinaus können Sie, im Gegensatz zu anderen Speicherorten, auf Dateien in den App-Datenspeicherorten auch mit [Win32 und COM für UWP-Apps (Universelle Windows-Plattform)](https://msdn.microsoft.com/library/windows/apps/br205757) und einigen Funktionen der C/C++-Standardbibliothek in Microsoft Visual Studio zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-139">In addition, and unlike other locations, you can also access files in your app data locations by using some [Win32 and COM for UWP apps](https://msdn.microsoft.com/library/windows/apps/br205757) and some C/C++ Standard Library functions from Visual Studio.</span></span>

<span data-ttu-id="9edc1-140">Sie können nicht über die Dateiauswahl auf die lokale, servergespeicherte oder temporäre Ordner zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-140">You can't access the local, roaming, or temporary folders through the file picker.</span></span>

### <a name="removable-devices"></a><span data-ttu-id="9edc1-141">Wechselmedien</span><span class="sxs-lookup"><span data-stu-id="9edc1-141">Removable devices</span></span>
<span data-ttu-id="9edc1-142">Darüber hinaus kann Ihre App standardmäßig auf einige der Dateien auf verbundenen Geräten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-142">Additionally, your app can access some of the files on connected devices by default.</span></span> <span data-ttu-id="9edc1-143">Diese Möglichkeit besteht, wenn Ihre App die [Erweiterung für die automatische Wiedergabe](https://msdn.microsoft.com/library/windows/apps/xaml/hh464906.aspx#autoplay) verwendet, die automatisch gestartet wird, sobald Benutzer ein Gerät, wie eine Kamera oder einen USB-Speicherstick, an Ihr System anschließen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-143">This is an option if your app uses the [AutoPlay extension](https://msdn.microsoft.com/library/windows/apps/xaml/hh464906.aspx#autoplay) to launch automatically when users connect a device, like a camera or USB thumb drive, to their system.</span></span> <span data-ttu-id="9edc1-144">Die Dateien, auf welche Ihre App zugreifen kann, sind auf bestimmte Dateitypen begrenzt, die über Deklarationen von Dateitypzuordnungen in Ihrem App-Manifest festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="9edc1-144">The files your app can access are limited to specific file types that are specified via File Type Association declarations in your app manifest.</span></span>

<span data-ttu-id="9edc1-145">Sie können natürlich auch auf Dateien und Ordner auf einem Wechselmedium mithilfe der Dateiauswahl zugreifen (unter Verwendung von [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) und [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881)) und den Benutzer die Dateien und Ordner auswählen lassen, auf welche Ihre App Zugriff haben soll.</span><span class="sxs-lookup"><span data-stu-id="9edc1-145">Of course, you can also gain access to files and folders on a removable device by calling the file picker (using [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) and [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881)) and letting the user pick files and folders for your app to access.</span></span> <span data-ttu-id="9edc1-146">Weitere Informationen zur Verwendung der Dateiauswahl finden Sie unter [Öffnen von Dateien und Ordnern mit einer Auswahl](quickstart-using-file-and-folder-pickers.md).</span><span class="sxs-lookup"><span data-stu-id="9edc1-146">Learn how to use the file picker in [Open files and folders with a picker](quickstart-using-file-and-folder-pickers.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9edc1-147">Weitere Informationen zum Zugriff auf eine SD-Karte oder andere Wechselgeräte finden Sie unter [Zugreifen auf die SD-Karte](access-the-sd-card.md).</span><span class="sxs-lookup"><span data-stu-id="9edc1-147">For more info about accessing an SD card or other removable devices, see [Access the SD card](access-the-sd-card.md).</span></span>

## <a name="locations-that-uwp-apps-can-access"></a><span data-ttu-id="9edc1-148">UWP-apps zugängliche Speicherorte</span><span class="sxs-lookup"><span data-stu-id="9edc1-148">Locations that UWP apps can access</span></span>
### <a name="users-downloads-folder"></a><span data-ttu-id="9edc1-149">Downloadordner des Benutzers</span><span class="sxs-lookup"><span data-stu-id="9edc1-149">User's Downloads folder</span></span>

<span data-ttu-id="9edc1-150">Der Ordner, in dem heruntergeladene Dateien standardmäßig gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="9edc1-150">The folder where downloaded files are saved by default.</span></span>

<span data-ttu-id="9edc1-151">Standardmäßig kann Ihre Anwendung nur auf Dateien und Ordner im Ordner "Downloads" des Benutzers zugreifen, die von Ihrer App erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="9edc1-151">By default, your app can only access files and folders in the user's Downloads folder that your app created.</span></span> <span data-ttu-id="9edc1-152">Sie können jedoch durch Aufrufen der Dateiauswahl auf weitere Dateien und Ordner im Downloadordner des Benutzers zugreifen ([**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) oder [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881)), sodass Benutzer zu Dateien oder Ordner navigieren und diese auswählen können und Ihre Anwendung Zugriff auf diese erhält.</span><span class="sxs-lookup"><span data-stu-id="9edc1-152">However, you can gain access to files and folders in the user's Downloads folder by calling a file picker ([**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) or [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/br207881)) so that users can navigate and pick files or folders for your app to access.</span></span>

- <span data-ttu-id="9edc1-153">Sie können im Downloadordner des Benutzers eine Datei wie folgt erstellen:</span><span class="sxs-lookup"><span data-stu-id="9edc1-153">You can create a file in the user's Downloads folder like this:</span></span>

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

```cppwinrt
Windows::Storage::StorageFile newFile{
    co_await Windows::Storage::DownloadsFolder::CreateFileAsync(L"file.txt")
};
// Process file
```

```cpp
using Windows::Storage;
auto createFileTask = create_task(DownloadsFolder::CreateFileAsync(L"file.txt"));
createFileTask.then([](StorageFile^ newFile)
{
    // Process file
});
```

<span data-ttu-id="9edc1-154">[**DownloadsFolder**](https://msdn.microsoft.com/library/windows/apps/br241632).[**CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh996761) wird überladen, sodass Sie festlegen können, was das System im Fall einer bereits vorhandenen gleichnamigen Datei im Downloadordner des Benutzers tun sollte.</span><span class="sxs-lookup"><span data-stu-id="9edc1-154">[**DownloadsFolder**](https://msdn.microsoft.com/library/windows/apps/br241632).[**CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh996761) is overloaded so that you can specify what the system should do if there is already an existing file in the Downloads folder that has the same name.</span></span> <span data-ttu-id="9edc1-155">Nach vollständiger Ausführung dieser Methoden wird ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) zurückgegeben, das die erstellte Datei darstellt.</span><span class="sxs-lookup"><span data-stu-id="9edc1-155">When these methods complete, they return a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) that represents the file that was created.</span></span> <span data-ttu-id="9edc1-156">Diese Datei wird im Beispiel `newFile` genannt.</span><span class="sxs-lookup"><span data-stu-id="9edc1-156">This file is called `newFile` in the example.</span></span>

- <span data-ttu-id="9edc1-157">Sie können im Downloadordner des Benutzers wie folgt einen Unterordner erstellen:</span><span class="sxs-lookup"><span data-stu-id="9edc1-157">You can create a subfolder in the user's Downloads folder like this:</span></span>

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

```cppwinrt
Windows::Storage::StorageFolder newFolder{
    co_await Windows::Storage::DownloadsFolder::CreateFolderAsync(L"New Folder")
};
// Process folder
```

```cpp
using Windows::Storage;
auto createFolderTask = create_task(DownloadsFolder::CreateFolderAsync(L"New Folder"));
createFolderTask.then([](StorageFolder^ newFolder)
{
    // Process folder
});
```

<span data-ttu-id="9edc1-158">[**DownloadsFolder**](https://msdn.microsoft.com/library/windows/apps/br241632).[**CreateFolderAsync**](https://msdn.microsoft.com/library/windows/apps/hh996763) wird überladen, sodass Sie festlegen können, was das System im Fall eines bereits vorhandenen gleichnamigen Unterordners im Ordner „Downloads“ des Benutzers tun sollte.</span><span class="sxs-lookup"><span data-stu-id="9edc1-158">[**DownloadsFolder**](https://msdn.microsoft.com/library/windows/apps/br241632).[**CreateFolderAsync**](https://msdn.microsoft.com/library/windows/apps/hh996763) is overloaded so that you can specify what the system should do if there is already an existing subfolder in the Downloads folder that has the same name.</span></span> <span data-ttu-id="9edc1-159">Nach vollständiger Ausführung dieser Methoden wird ein [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) zurückgegeben, der den erstellten Unterordner darstellt.</span><span class="sxs-lookup"><span data-stu-id="9edc1-159">When these methods complete, they return a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) that represents the subfolder that was created.</span></span> <span data-ttu-id="9edc1-160">Diese Datei wird im Beispiel `newFolder` genannt.</span><span class="sxs-lookup"><span data-stu-id="9edc1-160">This file is called `newFolder` in the example.</span></span>

<span data-ttu-id="9edc1-161">Wenn Sie eine Datei oder einen Ordner im Downloadordner erstellen, empfehlen wir, die Datei oder den Ordner der [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) Ihrer App hinzuzufügen, sodass zukünftig leicht auf dieses Element zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="9edc1-161">If you create a file or folder in the Downloads folder, we recommend that you add that item to your app's [**FutureAccessList**](https://msdn.microsoft.com/library/windows/apps/br207457) so that your app can readily access that item in the future.</span></span>

## <a name="accessing-additional-locations"></a><span data-ttu-id="9edc1-162">Zugriff auf zusätzliche Speicherorte</span><span class="sxs-lookup"><span data-stu-id="9edc1-162">Accessing additional locations</span></span>

<span data-ttu-id="9edc1-163">Zusätzlich zu den Standardspeicherorten kann eine App durch das Deklarieren von Funktionen im App-Manifest (siehe [Deklaration der App-Funktionen](https://msdn.microsoft.com/library/windows/apps/mt270968)) oder durch Aufrufen der Dateiauswahl auf zusätzliche Dateien und Ordner zugreifen, um den Benutzer Dateien und Ordner auswählen zu lassen, auf welche die App Zugriff haben soll (siehe [Öffnen von Dateien und Ordnern mit einer Auswahl](quickstart-using-file-and-folder-pickers.md)).</span><span class="sxs-lookup"><span data-stu-id="9edc1-163">In addition to the default locations, an app can access additional files and folders by declaring capabilities in the app manifest (see [App capability declarations](https://msdn.microsoft.com/library/windows/apps/mt270968)), or by calling a file picker to let the user pick files and folders for the app to access (see [Open files and folders with a picker](quickstart-using-file-and-folder-pickers.md)).</span></span>

<span data-ttu-id="9edc1-164">App, die die [AppExecutionAlias](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-appexecutionalias)-Erweiterung deklarieren, haben Dateisystemberechtigungen für das Verzeichnis, aus dem sie im Konsolenfenster gestartet werden, und darunter liegende Verzeichnisse.</span><span class="sxs-lookup"><span data-stu-id="9edc1-164">App's that that declare the [AppExecutionAlias](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-appexecutionalias) extension, have file-system permissions from the directory that they are launched from in the console window, and downwards.</span></span>

<span data-ttu-id="9edc1-165">In der folgenden Tabelle sind weitere Speicherorte aufgeführt, auf die Sie durch Deklarieren von Funktionen und Verwenden der zugehörigen [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/br227346)-APIs zugreifen können:</span><span class="sxs-lookup"><span data-stu-id="9edc1-165">The following table lists additional locations that you can access by declaring a capability (or capabilities) and using the associated [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/br227346) API:</span></span>

| <span data-ttu-id="9edc1-166">Ort</span><span class="sxs-lookup"><span data-stu-id="9edc1-166">Location</span></span> | <span data-ttu-id="9edc1-167">Funktion</span><span class="sxs-lookup"><span data-stu-id="9edc1-167">Capability</span></span> | <span data-ttu-id="9edc1-168">Windows.Storage-API</span><span class="sxs-lookup"><span data-stu-id="9edc1-168">Windows.Storage API</span></span> |
|----------|------------|---------------------|
| <span data-ttu-id="9edc1-169">Alle Dateien, auf die der Benutzer Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="9edc1-169">All files that the user has access to.</span></span> <span data-ttu-id="9edc1-170">Beispiel: Dokumente, Bilder, Fotos, Downloads, Desktop, OneDrive usw.</span><span class="sxs-lookup"><span data-stu-id="9edc1-170">For example: documents, pictures, photos, downloads, desktop, OneDrive, etc.</span></span> | <span data-ttu-id="9edc1-171">broadFileSystemAccess</span><span class="sxs-lookup"><span data-stu-id="9edc1-171">broadFileSystemAccess</span></span><br><br><span data-ttu-id="9edc1-172">Dies ist eine eingeschränkte Funktion.</span><span class="sxs-lookup"><span data-stu-id="9edc1-172">This is a restricted capability.</span></span> <span data-ttu-id="9edc1-173">Zugriff kann unter " **Einstellungen"** konfiguriert > **Datenschutz** > **Dateisystem**.</span><span class="sxs-lookup"><span data-stu-id="9edc1-173">Access is configurable in **Settings** > **Privacy** > **File system**.</span></span> <span data-ttu-id="9edc1-174">Da Benutzer gewähren oder verweigern jederzeit in den **Einstellungen**können, sollten Sie sicherstellen, dass Ihre app diese Änderungen flexibel.</span><span class="sxs-lookup"><span data-stu-id="9edc1-174">Because users can grant or deny the permission any time in **Settings**, you should ensure that your app is resilient to those changes.</span></span> <span data-ttu-id="9edc1-175">Wenn Sie feststellen, dass Ihre app nicht zugreifen kann, können Sie den Benutzer auffordern, die Einstellung zu ändern, indem Sie einen Link zum Artikel [Zugriff auf das Dateisystem Windows 10 und Datenschutz](https://privacy.microsoft.com/en-US/windows-10-file-system-access-and-privacy) .</span><span class="sxs-lookup"><span data-stu-id="9edc1-175">If you find that your app does not have access, you may choose to prompt the user to change the setting by providing a link to the [Windows 10 file system access and privacy](https://privacy.microsoft.com/en-US/windows-10-file-system-access-and-privacy) article.</span></span> <span data-ttu-id="9edc1-176">Beachten Sie, dass der Benutzer die app zu schließen, Sie schalten und starten Sie die app muss.</span><span class="sxs-lookup"><span data-stu-id="9edc1-176">Note that the user must close the app, toggle the setting, and restart the app.</span></span> <span data-ttu-id="9edc1-177">Wenn sie die Einstellung aktivieren, während die app ausgeführt wird, wird die Plattform Ihre app angehalten, damit können Sie den Zustand speichern, und dann die app erzwungener zu beenden, um die neue Einstellung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="9edc1-177">If they toggle the setting while the app is running, the platform will suspend your app so that you can save the state, then forcibly terminate the app in order to apply the new setting.</span></span> <span data-ttu-id="9edc1-178">Im April 2018-Update ist die Standardeinstellung für die Berechtigung.</span><span class="sxs-lookup"><span data-stu-id="9edc1-178">In the April 2018 update, the default for the permission is On.</span></span> <span data-ttu-id="9edc1-179">In den Oktober 2018-Update ist standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="9edc1-179">In the October 2018 update, the default is Off.</span></span><br /><br /><span data-ttu-id="9edc1-180">Wenn Sie eine App an den Store übermitteln, die diese Funktion deklariert, müssen Sie zusätzliche Beschreibungen dazu bereitstellen, warum die App diese Funktion benötigt und wie sie diese verwenden wird.</span><span class="sxs-lookup"><span data-stu-id="9edc1-180">If you submit an app to the Store that declares this capability, you will need to supply additional descriptions of why your app needs this capability, and how it intends to use it.</span></span><br><span data-ttu-id="9edc1-181">Diese Funktion funktioniert für APIs im [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346) -Namespace.</span><span class="sxs-lookup"><span data-stu-id="9edc1-181">This capability works for APIs in the [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346) namespace.</span></span> <span data-ttu-id="9edc1-182">Finden Sie im Abschnitt " **Beispiel** " am Ende dieses Artikels finden Sie ein Beispiel für diese Funktion in Ihrer app zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9edc1-182">See the **Example** section at the end of this article for an example of how to enable this capability in your app.</span></span> | <span data-ttu-id="9edc1-183">n.a.</span><span class="sxs-lookup"><span data-stu-id="9edc1-183">n/a</span></span> |
| <span data-ttu-id="9edc1-184">Dokumente</span><span class="sxs-lookup"><span data-stu-id="9edc1-184">Documents</span></span> | <span data-ttu-id="9edc1-185">DocumentsLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-185">DocumentsLibrary</span></span> <br><br><span data-ttu-id="9edc1-186">Hinweis: Sie müssen Ihrem App-Manifest Dateitypzuordnungen hinzufügen, die bestimmte Dateitypen deklarieren, auf die Ihre App an diesem Speicherort Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="9edc1-186">Note: You must add File Type Associations to your app manifest that declare specific file types that your app can access in this location.</span></span> <br><br><span data-ttu-id="9edc1-187">Verwenden Sie diese Funktion, wenn Ihre App:</span><span class="sxs-lookup"><span data-stu-id="9edc1-187">Use this capability if your app:</span></span><br><span data-ttu-id="9edc1-188">- Den plattformübergreifenden Offlinezugriff auf bestimmte OneDrive-Inhalte mit gültigen OneDrive-URLs oder Ressourcen-IDs ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="9edc1-188">- Facilitates cross-platform offline access to specific OneDrive content using valid OneDrive URLs or Resource IDs</span></span><br><span data-ttu-id="9edc1-189">-Speichert geöffneten Dateien des Benutzers automatisch im OneDrive offline</span><span class="sxs-lookup"><span data-stu-id="9edc1-189">- Saves open files to the user's OneDrive automatically while offline</span></span> | [<span data-ttu-id="9edc1-190">KnownFolders.DocumentsLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-190">KnownFolders.DocumentsLibrary</span></span>](https://msdn.microsoft.com/library/windows/apps/br227152) |
| <span data-ttu-id="9edc1-191">Musik</span><span class="sxs-lookup"><span data-stu-id="9edc1-191">Music</span></span>     | <span data-ttu-id="9edc1-192">MusicLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-192">MusicLibrary</span></span> <br><span data-ttu-id="9edc1-193">Weitere Informationen finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="9edc1-193">Also see [Files and folders in the Music, Pictures, and Videos libraries](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span> | [<span data-ttu-id="9edc1-194">KnownFolders.MusicLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-194">KnownFolders.MusicLibrary</span></span>](https://msdn.microsoft.com/library/windows/apps/br227155) |    
| <span data-ttu-id="9edc1-195">Bilder</span><span class="sxs-lookup"><span data-stu-id="9edc1-195">Pictures</span></span>  | <span data-ttu-id="9edc1-196">PicturesLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-196">PicturesLibrary</span></span><br> <span data-ttu-id="9edc1-197">Weitere Informationen finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="9edc1-197">Also see [Files and folders in the Music, Pictures, and Videos libraries](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span> | [<span data-ttu-id="9edc1-198">KnownFolders.PicturesLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-198">KnownFolders.PicturesLibrary</span></span>](https://msdn.microsoft.com/library/windows/apps/br227156) |  
| <span data-ttu-id="9edc1-199">Videos</span><span class="sxs-lookup"><span data-stu-id="9edc1-199">Videos</span></span>    | <span data-ttu-id="9edc1-200">VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-200">VideosLibrary</span></span><br><span data-ttu-id="9edc1-201">Weitere Informationen finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="9edc1-201">Also see [Files and folders in the Music, Pictures, and Videos libraries](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span> | [<span data-ttu-id="9edc1-202">KnownFolders.VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-202">KnownFolders.VideosLibrary</span></span>](https://msdn.microsoft.com/library/windows/apps/br227159) |   
| <span data-ttu-id="9edc1-203">Wechselmedien</span><span class="sxs-lookup"><span data-stu-id="9edc1-203">Removable devices</span></span>  | <span data-ttu-id="9edc1-204">RemovableDevices</span><span class="sxs-lookup"><span data-stu-id="9edc1-204">RemovableDevices</span></span> <br><br><span data-ttu-id="9edc1-205">Hinweis: Sie müssen Ihrem App-Manifest Dateitypzuordnungen hinzufügen, die bestimmte Dateitypen deklarieren, auf die Ihre App an diesem Speicherort Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="9edc1-205">Note  You must add File Type Associations to your app manifest that declare specific file types that your app can access in this location.</span></span> <br><br><span data-ttu-id="9edc1-206">Weitere Informationen finden Sie unter [Zugreifen auf die SD-Karte](access-the-sd-card.md).</span><span class="sxs-lookup"><span data-stu-id="9edc1-206">Also see [Access the SD card](access-the-sd-card.md).</span></span> | [<span data-ttu-id="9edc1-207">KnownFolders.RemovableDevices</span><span class="sxs-lookup"><span data-stu-id="9edc1-207">KnownFolders.RemovableDevices</span></span>](https://msdn.microsoft.com/library/windows/apps/br227158) |  
| <span data-ttu-id="9edc1-208">Bibliotheken der Heimnetzgruppen</span><span class="sxs-lookup"><span data-stu-id="9edc1-208">Homegroup libraries</span></span>  | <span data-ttu-id="9edc1-209">Mindestens eine der folgenden Funktionen ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9edc1-209">At least one of the following capabilities is needed.</span></span> <br><span data-ttu-id="9edc1-210">– MusicLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-210">- MusicLibrary</span></span> <br><span data-ttu-id="9edc1-211">– PicturesLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-211">- PicturesLibrary</span></span> <br><span data-ttu-id="9edc1-212">– VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-212">- VideosLibrary</span></span> | [<span data-ttu-id="9edc1-213">KnownFolders.HomeGroup</span><span class="sxs-lookup"><span data-stu-id="9edc1-213">KnownFolders.HomeGroup</span></span>](https://msdn.microsoft.com/library/windows/apps/br227153) |      
| <span data-ttu-id="9edc1-214">Medienservergeräte (DLNA)</span><span class="sxs-lookup"><span data-stu-id="9edc1-214">Media server devices (DLNA)</span></span> | <span data-ttu-id="9edc1-215">Mindestens eine der folgenden Funktionen ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9edc1-215">At least one of the following capabilities is needed.</span></span> <br><span data-ttu-id="9edc1-216">– MusicLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-216">- MusicLibrary</span></span> <br><span data-ttu-id="9edc1-217">– PicturesLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-217">- PicturesLibrary</span></span> <br><span data-ttu-id="9edc1-218">– VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="9edc1-218">- VideosLibrary</span></span> | [<span data-ttu-id="9edc1-219">KnownFolders.MediaServerDevices</span><span class="sxs-lookup"><span data-stu-id="9edc1-219">KnownFolders.MediaServerDevices</span></span>](https://msdn.microsoft.com/library/windows/apps/br227154) |
| <span data-ttu-id="9edc1-220">Universal Naming Convention (UNC)-Ordner</span><span class="sxs-lookup"><span data-stu-id="9edc1-220">Universal Naming Convention (UNC) folders</span></span> | <span data-ttu-id="9edc1-221">Eine Kombination der folgenden Funktionen ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9edc1-221">A combination of the following capabilities is needed.</span></span> <br><br><span data-ttu-id="9edc1-222">Die Funktion für Heim- oder Arbeitsplatznetzwerke:</span><span class="sxs-lookup"><span data-stu-id="9edc1-222">The home and work networks capability:</span></span> <br><span data-ttu-id="9edc1-223">– PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="9edc1-223">- PrivateNetworkClientServer</span></span> <br><br><span data-ttu-id="9edc1-224">Zudem mindestens eine Funktion zu Internet und öffentlichen Netzwerken:</span><span class="sxs-lookup"><span data-stu-id="9edc1-224">And at least one internet and public networks capability:</span></span> <br><span data-ttu-id="9edc1-225">– InternetClient</span><span class="sxs-lookup"><span data-stu-id="9edc1-225">- InternetClient</span></span> <br><span data-ttu-id="9edc1-226">– InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="9edc1-226">- InternetClientServer</span></span> <br><br><span data-ttu-id="9edc1-227">Und gegebenenfalls die Funktion für Domänenanmeldeinformationen:</span><span class="sxs-lookup"><span data-stu-id="9edc1-227">And, if applicable, the domain credentials capability:</span></span><br><span data-ttu-id="9edc1-228">– EnterpriseAuthentication</span><span class="sxs-lookup"><span data-stu-id="9edc1-228">- EnterpriseAuthentication</span></span> <br><br><span data-ttu-id="9edc1-229">Hinweis: Sie müssen Ihrem App-Manifest Dateitypzuordnungen hinzufügen, die bestimmte Dateitypen deklarieren, auf die Ihre App an diesem Speicherort Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="9edc1-229">Note: You must add File Type Associations to your app manifest that declare specific file types that your app can access in this location.</span></span> | <span data-ttu-id="9edc1-230">Abrufen eines Ordners mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="9edc1-230">Retrieve a folder using:</span></span> <br>[<span data-ttu-id="9edc1-231">StorageFolder.GetFolderFromPathAsync</span><span class="sxs-lookup"><span data-stu-id="9edc1-231">StorageFolder.GetFolderFromPathAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/br227278) <br><br><span data-ttu-id="9edc1-232">Abrufen einer Datei mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="9edc1-232">Retrieve a file using:</span></span> <br>[<span data-ttu-id="9edc1-233">StorageFile.GetFileFromPathAsync</span><span class="sxs-lookup"><span data-stu-id="9edc1-233">StorageFile.GetFileFromPathAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/br227206) |

**<span data-ttu-id="9edc1-234">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9edc1-234">Example</span></span>**

<span data-ttu-id="9edc1-235">In diesem Beispiel wird die eingeschränkte `broadFileSystemAccess`-Funktion hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9edc1-235">This example adds the restricted `broadFileSystemAccess` capability.</span></span> <span data-ttu-id="9edc1-236">Zusätzlich zur Angabe der Funktion muss der `rescap`-Namespace muss hinzugefügt werden und wird auch zu `IgnorableNamespaces` hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="9edc1-236">In addition to specifying the capability, the `rescap` namespace must be added, and is also added to `IgnorableNamespaces`:</span></span>

```xaml
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
> <span data-ttu-id="9edc1-237">Eine vollständige Liste der App-Funktionen finden Sie unter [Deklarationen von App-Funktionen](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span><span class="sxs-lookup"><span data-stu-id="9edc1-237">For a complete list of app capabilities, see [App capability declarations](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span></span>
