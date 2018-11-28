---
ms.assetid: CAC6A7C7-3348-4EC4-8327-D47EB6E0C238
title: Zugreifen auf die SD-Karte
description: Sie können nicht unbedingt erforderliche Daten auf einer optionalen microSD-Karte speichern und auf diese zugreifen. Dies gilt besonders für kostengünstige Geräte, die nur über einen begrenzten internen Speicher verfügen.
ms.date: 03/08/2017
ms.topic: article
keywords: Windows10, UWP, SD-Karte, Speicher
ms.localizationpriority: medium
ms.openlocfilehash: 9ef97ed489f2dc35aece83821633a583dfba77e2
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7965122"
---
# <a name="access-the-sd-card"></a><span data-ttu-id="ffa59-104">Zugreifen auf die SD-Karte</span><span class="sxs-lookup"><span data-stu-id="ffa59-104">Access the SD card</span></span>



<span data-ttu-id="ffa59-105">Sie können weniger wichtige Daten auf einer optionalen microSD-Karte speichern. Dies gilt besonders für Geräte, die nur über einen begrenzten Speicher und einen SD-Kartensteckplatz verfügen.</span><span class="sxs-lookup"><span data-stu-id="ffa59-105">You can store and access non-essential data on an optional microSD card, especially on low-cost mobile devices that have limited internal storage and have a slot for an SD card.</span></span>

<span data-ttu-id="ffa59-106">In den meisten Fällen müssen Sie die **removableStorage**-Funktion in der App-Manifestdatei angeben, bevor die App Dateien auf der SD-Karte speichern und darauf zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="ffa59-106">In most cases, you have to specify the **removableStorage** capability in the app manifest file before your app can store and access files on the SD card.</span></span> <span data-ttu-id="ffa59-107">Normalerweise müssen Sie außerdem die Registrierung durchführen, damit die Dateitypen behandelt werden können, die von der App gespeichert werden und auf die zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="ffa59-107">Typically you also have to register to handle the type of files that your app stores and accesses.</span></span>

<span data-ttu-id="ffa59-108">Sie können Dateien mithilfe der folgenden Methoden auf der optionalen SD-Karte speichern und darauf zugreifen:</span><span class="sxs-lookup"><span data-stu-id="ffa59-108">You can store and access files on the optional SD card by using the following methods:</span></span>
- <span data-ttu-id="ffa59-109">Dateiauswahlen</span><span class="sxs-lookup"><span data-stu-id="ffa59-109">File pickers.</span></span>
- <span data-ttu-id="ffa59-110">Die [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/br227346)-APIs.</span><span class="sxs-lookup"><span data-stu-id="ffa59-110">The [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/br227346) APIs.</span></span>

## <a name="what-you-can-and-cant-access-on-the-sd-card"></a><span data-ttu-id="ffa59-111">Zugriffsmöglichkeiten auf der SD-Karte</span><span class="sxs-lookup"><span data-stu-id="ffa59-111">What you can and can't access on the SD card</span></span>

### <a name="what-you-can-access"></a><span data-ttu-id="ffa59-112">Zugriffsmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="ffa59-112">What you can access</span></span>

- <span data-ttu-id="ffa59-113">Die App kann nur Dateien mit den Dateitypen lesen und schreiben, die in der App-Manifestdatei für die Verarbeitung registriert sind.</span><span class="sxs-lookup"><span data-stu-id="ffa59-113">Your app can only read and write files of file types that the app has registered to handle in the app manifest file.</span></span>
- <span data-ttu-id="ffa59-114">Mit der App können auch Ordner erstellt und verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="ffa59-114">Your app can also create and manage folders.</span></span>

### <a name="what-you-cant-access"></a><span data-ttu-id="ffa59-115">Kein Zugriff</span><span class="sxs-lookup"><span data-stu-id="ffa59-115">What you can't access</span></span>

- <span data-ttu-id="ffa59-116">Systemordner und die darin enthaltenen Dateien sind für die App nicht sichtbar, und sie kann nicht darauf zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ffa59-116">Your app can't see or access system folders and the files that they contain.</span></span>
- <span data-ttu-id="ffa59-117">Für die App sind auch keine Dateien sichtbar, die mit dem Attribut "Hidden" (Ausgeblendet) gekennzeichnet sind.</span><span class="sxs-lookup"><span data-stu-id="ffa59-117">Your app can't see files that are marked with the Hidden attribute.</span></span> <span data-ttu-id="ffa59-118">Das Attribut "Hidden" wird normalerweise verwendet, um das Risiko des versehentlichen Löschens von Daten zu verringern.</span><span class="sxs-lookup"><span data-stu-id="ffa59-118">The Hidden attribute is typically used to reduce the risk of deleting data accidentally.</span></span>
- <span data-ttu-id="ffa59-119">Außerdem kann die App die Dokumentbibliothek nicht sehen und nicht über [**KnownFolders.DocumentsLibrary**](https://msdn.microsoft.com/library/windows/apps/br227152) darauf zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ffa59-119">Your app can't see or access the Documents library by using [**KnownFolders.DocumentsLibrary**](https://msdn.microsoft.com/library/windows/apps/br227152).</span></span> <span data-ttu-id="ffa59-120">Sie können aber auf der SD-Karte auf die Dokumentbibliothek zugreifen, indem Sie das Dateisystem durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="ffa59-120">However you can access the Documents library on the SD card by traversing the file system.</span></span>

## <a name="security-and-privacy-considerations"></a><span data-ttu-id="ffa59-121">Sicherheits- und Datenschutzaspekte</span><span class="sxs-lookup"><span data-stu-id="ffa59-121">Security and privacy considerations</span></span>

<span data-ttu-id="ffa59-122">Wenn eine App Dateien an einem globalen Speicherort auf der SD-Karte speichert, werden diese Dateien nicht verschlüsselt und sind daher für andere Apps normalerweise zugänglich.</span><span class="sxs-lookup"><span data-stu-id="ffa59-122">When an app saves files in a global location on the SD card, those files are not encrypted so they are typically accessible to other apps.</span></span>

- <span data-ttu-id="ffa59-123">Wenn sich die SD-Karte im Gerät befindet, können auch andere Apps auf Ihre Dateien zugreifen, die über die Registrierung für die Verarbeitung desselben Dateityps verfügen.</span><span class="sxs-lookup"><span data-stu-id="ffa59-123">While the SD card is in the device, your files are accessible to other apps that have registered to handle the same file type.</span></span>
- <span data-ttu-id="ffa59-124">Wenn die SD-Karte aus dem Gerät herausgenommen wird und über einen PC darauf zugegriffen wird, sind Ihre Dateien im Datei-Explorer sichtbar und für andere Apps zugänglich.</span><span class="sxs-lookup"><span data-stu-id="ffa59-124">When the SD card is removed from the device and opened from a PC, your files are visible in File Explorer and accessible to other apps.</span></span>

<span data-ttu-id="ffa59-125">Wenn eine auf der SD-Karte installierte App Dateien in [**LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621) speichert, werden diese Dateien jedoch verschlüsselt und sind für andere Apps nicht zugänglich.</span><span class="sxs-lookup"><span data-stu-id="ffa59-125">When an app installed on the SD card saves files in its [**LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621), however, those files are encrypted and are not accessible to other apps.</span></span>

## <a name="requirements-for-accessing-files-on-the-sd-card"></a><span data-ttu-id="ffa59-126">Anforderungen für den Dateizugriff auf der SD-Karte</span><span class="sxs-lookup"><span data-stu-id="ffa59-126">Requirements for accessing files on the SD card</span></span>

<span data-ttu-id="ffa59-127">Zum Zugreifen auf Dateien auf der SD-Karte müssen Sie normalerweise die folgenden Dinge angeben.</span><span class="sxs-lookup"><span data-stu-id="ffa59-127">To access files on the SD card, typically you have to specify the following things.</span></span>

1.  <span data-ttu-id="ffa59-128">Sie müssen die **removableStorage**-Funktion in der App-Manifestdatei angeben.</span><span class="sxs-lookup"><span data-stu-id="ffa59-128">You have to specify the **removableStorage** capability in the app manifest file.</span></span>
2.  <span data-ttu-id="ffa59-129">Außerdem müssen Sie die Dateierweiterungen für die Verarbeitung registrieren, die dem Medientyp zugeordnet sind, auf den Sie zugreifen möchten.</span><span class="sxs-lookup"><span data-stu-id="ffa59-129">You also have to register to handle the file extensions associated with the type of media that you want to access.</span></span>

<span data-ttu-id="ffa59-130">Verwenden Sie die vorangehende Methode außerdem für den Zugriff auf Mediendateien auf der SD-Karte, ohne auf einen bekannten Ordner wie **KnownFolders.MusicLibrary** zu verweisen oder auf Mediendateien zuzugreifen, die außerhalb der Medienbibliotheksordner gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="ffa59-130">Use the preceding method also to access media files on the SD card without referencing a known folder like **KnownFolders.MusicLibrary**, or to access media files that are stored outside of the media library folders.</span></span>

<span data-ttu-id="ffa59-131">Um auf Mediendateien (Musik, Fotos oder Videos) zuzugreifen, die in den Medienbibliotheken in bekannten Ordnern gespeichert sind, müssen Sie nur die zugeordnete Funktion in der App-Manifestdatei angeben: **musicLibrary**, **picturesLibrary** oder **videoLibrary**.</span><span class="sxs-lookup"><span data-stu-id="ffa59-131">To access media files stored in the media libraries—Music, Photos, or Videos—by using known folders, you only have to specify the associated capability in the app manifest file—**musicLibrary**, **picturesLibrary**, or **videoLibrary**.</span></span> <span data-ttu-id="ffa59-132">Es ist nicht erforderlich, die **removableStorage**-Funktion anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ffa59-132">You do not have to specify the **removableStorage** capability.</span></span> <span data-ttu-id="ffa59-133">Weitere Informationen finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="ffa59-133">For more info, see [Files and folders in the Music, Pictures, and Videos libraries](quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span>

## <a name="accessing-files-on-the-sd-card"></a><span data-ttu-id="ffa59-134">Zugreifen auf Dateien auf der SD-Karte</span><span class="sxs-lookup"><span data-stu-id="ffa59-134">Accessing files on the SD card</span></span>

### <a name="getting-a-reference-to-the-sd-card"></a><span data-ttu-id="ffa59-135">Abrufen eines Verweises auf die SD-Karte</span><span class="sxs-lookup"><span data-stu-id="ffa59-135">Getting a reference to the SD card</span></span>

<span data-ttu-id="ffa59-136">Der Ordner [**KnownFolders.RemovableDevices**](https://msdn.microsoft.com/library/windows/apps/br227158) ist der Stamm-[**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) für die Wechselmedien, die derzeit an das Gerät angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="ffa59-136">The [**KnownFolders.RemovableDevices**](https://msdn.microsoft.com/library/windows/apps/br227158) folder is the logical root [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) for the set of removable devices currently connected to the device.</span></span> <span data-ttu-id="ffa59-137">Wenn eine SD-Karte vorhanden ist, stellt der erste (und einzige) **StorageFolder** unter dem Ordner **KnownFolders.RemovableDevices** die SD-Karte dar.</span><span class="sxs-lookup"><span data-stu-id="ffa59-137">If an SD card is present, the first (and only) **StorageFolder** underneath the **KnownFolders.RemovableDevices** folder represents the SD card.</span></span>

<span data-ttu-id="ffa59-138">Verwenden Sie Code der folgenden Art, um zu ermitteln, ob eine SD-Karte vorhanden ist, und um einen Verweis darauf als [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ffa59-138">Use code like the following to determine whether an SD card is present and to get a reference to it as a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230).</span></span>

```csharp
using Windows.Storage;

// Get the logical root folder for all external storage devices.
StorageFolder externalDevices = Windows.Storage.KnownFolders.RemovableDevices;

// Get the first child folder, which represents the SD card.
StorageFolder sdCard = (await externalDevices.GetFoldersAsync()).FirstOrDefault();

if (sdCard != null)
{
    // An SD card is present and the sdCard variable now contains a reference to it.
}
else
{
    // No SD card is present.
}
```

> [!NOTE]
> <span data-ttu-id="ffa59-139">Wenn Ihr SD-Kartenleser ein eingebetteter Reader (z.B. ein Steckplatz im Laptop oder PC selbst) ist, kann er möglicherweise nicht über KnownFolders.RemovableDevices aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="ffa59-139">If your SD card reader is an embedded reader (e.g., a slot in the laptop or PC itself), it may not be accessible through KnownFolders.RemovableDevices.</span></span>

### <a name="querying-the-contents-of-the-sd-card"></a><span data-ttu-id="ffa59-140">Abfragen des Inhalts der SD-Karte</span><span class="sxs-lookup"><span data-stu-id="ffa59-140">Querying the contents of the SD card</span></span>

<span data-ttu-id="ffa59-141">Die SD-Karte kann viele Ordner und Dateien enthalten, die nicht als bekannte Ordner erkannt werden und nicht abgefragt werden können, indem ein Speicherort unter [**KnownFolders**](https://msdn.microsoft.com/library/windows/apps/br227151) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ffa59-141">The SD card can contain many folders and files that aren't recognized as known folders and can't be queried by using a location from [**KnownFolders**](https://msdn.microsoft.com/library/windows/apps/br227151).</span></span> <span data-ttu-id="ffa59-142">Zum Auffinden von Dateien muss die App den Inhalt der Karte aufzählen, indem sie das Dateisystem rekursiv durchläuft.</span><span class="sxs-lookup"><span data-stu-id="ffa59-142">To find files, your app has to enumerate the contents of the card by traversing the file system recursively.</span></span> <span data-ttu-id="ffa59-143">Verwenden Sie [**GetFilesAsync (CommonFileQuery.DefaultQuery)**](https://msdn.microsoft.com/library/windows/apps/br227274) und [**GetFoldersAsync (CommonFolderQuery.DefaultQuery)**](https://msdn.microsoft.com/library/windows/apps/br227281), um die Inhalte der SD-Karte auf effiziente Weise abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ffa59-143">Use [**GetFilesAsync (CommonFileQuery.DefaultQuery)**](https://msdn.microsoft.com/library/windows/apps/br227274) and [**GetFoldersAsync (CommonFolderQuery.DefaultQuery)**](https://msdn.microsoft.com/library/windows/apps/br227281) to get the contents of the SD card efficiently.</span></span>

<span data-ttu-id="ffa59-144">Wir empfehlen Ihnen, zum Durchlaufen der SD-Karte einen Hintergrundthread zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ffa59-144">We recommend that you use a background thread to traverse the SD card.</span></span> <span data-ttu-id="ffa59-145">Eine SD-Karte kann viele Gigabyte an Daten enthalten.</span><span class="sxs-lookup"><span data-stu-id="ffa59-145">An SD card may contain many gigabytes of data.</span></span>

<span data-ttu-id="ffa59-146">Die App kann Benutzer auch zum Auswählen bestimmter Ordner mithilfe der Dateiauswahl auffordern.</span><span class="sxs-lookup"><span data-stu-id="ffa59-146">Your app can also require the user to choose specific folders by using the folder picker.</span></span>

<span data-ttu-id="ffa59-147">Beim Zugreifen auf das Dateisystem auf der SD-Karte mit einem Pfad, der von [**KnownFolders.RemovableDevices**](https://msdn.microsoft.com/library/windows/apps/br227158) abgeleitet ist, verhalten sich die untenstehenden Methoden wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ffa59-147">When you access the file system on the SD card with a path that you derived from [**KnownFolders.RemovableDevices**](https://msdn.microsoft.com/library/windows/apps/br227158), the following methods behave in the following way.</span></span>

-   <span data-ttu-id="ffa59-148">Die [**GetFilesAsync**](https://msdn.microsoft.com/library/windows/apps/br227273)-Methode gibt die Union (Vereinigung) der Dateierweiterungen, die Sie für die Verarbeitung registriert haben, und der Dateierweiterungen zurück, die den von Ihnen angegebenen Medienbibliothekfunktionen zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="ffa59-148">The [**GetFilesAsync**](https://msdn.microsoft.com/library/windows/apps/br227273) method returns the union of the file extensions that you have registered to handle and the file extensions associated with any media library capabilities that you have specified.</span></span>
-   <span data-ttu-id="ffa59-149">Für die [**GetFileFromPathAsync**](https://msdn.microsoft.com/library/windows/apps/br227206)-Methode tritt ein Fehler auf, wenn Sie die Dateierweiterung der Datei, auf die Sie zugreifen möchten, nicht für die Verarbeitung registriert haben.</span><span class="sxs-lookup"><span data-stu-id="ffa59-149">The [**GetFileFromPathAsync**](https://msdn.microsoft.com/library/windows/apps/br227206) method fails if you have not registered to handle the file extension of the file you are trying to access.</span></span>

## <a name="identifying-the-individual-sd-card"></a><span data-ttu-id="ffa59-150">Identifizieren einer individuellen SD-Karte</span><span class="sxs-lookup"><span data-stu-id="ffa59-150">Identifying the individual SD card</span></span>

<span data-ttu-id="ffa59-151">Nach der ersten Bereitstellung der SD-Karte generiert das Betriebssystem einen eindeutigen Bezeichner für die Karte.</span><span class="sxs-lookup"><span data-stu-id="ffa59-151">When the SD card is first mounted, the operating system generates a unique identifier for the card.</span></span> <span data-ttu-id="ffa59-152">Diese ID wird in einer Datei im Stammordner der Karte im Ordner "WPSystem" gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ffa59-152">It stores this ID in a file in the WPSystem folder at the root of the card.</span></span> <span data-ttu-id="ffa59-153">Mithilfe dieser ID kann eine App bestimmen, ob die Karte erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="ffa59-153">An app can use this ID to determine whether it recognizes the card.</span></span> <span data-ttu-id="ffa59-154">Wenn die Karte von einer App erkannt wird, kann die App bestimmte Vorgänge, die vorher durchgeführt wurden, unter Umständen verschieben.</span><span class="sxs-lookup"><span data-stu-id="ffa59-154">If an app recognizes the card, the app may be able to postpone certain operations that were completed previously.</span></span> <span data-ttu-id="ffa59-155">Der Inhalt der Karte kann sich seit dem letzten Zugriff auf die Karte durch die App aber geändert haben.</span><span class="sxs-lookup"><span data-stu-id="ffa59-155">However the contents of the card may have changed since the card was last accessed by the app.</span></span>

<span data-ttu-id="ffa59-156">Angenommen, eine App indiziert E-Books.</span><span class="sxs-lookup"><span data-stu-id="ffa59-156">For example, consider an app that indexes ebooks.</span></span> <span data-ttu-id="ffa59-157">Falls die App die gesamte SD-Karte bereits auf E-Book-Dateien untersucht und einen Index für die E-Books angelegt hat, kann diese Liste sofort angezeigt werden, sobald die Karte wieder eingesetzt wird und die App die Karte erkannt hat.</span><span class="sxs-lookup"><span data-stu-id="ffa59-157">If the app has previously scanned the whole SD card for ebook files and created an index of the ebooks, it can display the list immediately if the card is reinserted and the app recognizes the card.</span></span> <span data-ttu-id="ffa59-158">In einem separaten Vorgang kann ein Hintergrundthread mit geringer Priorität gestartet werden, um nach neuen E-Books zu suchen.</span><span class="sxs-lookup"><span data-stu-id="ffa59-158">Separately it can start a low-priority background thread to search for new ebooks.</span></span> <span data-ttu-id="ffa59-159">Außerdem kann ein Fehler verarbeitet werden, der bei einer Suche nach einem nicht mehr vorhandenen E-Book auftritt, wenn ein Benutzer versucht, auf das gelöschte E-Book zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="ffa59-159">It can also handle a failure to find an ebook that existed previously when the user tries to access the deleted ebook.</span></span>

<span data-ttu-id="ffa59-160">Der Name der Eigenschaft, in der diese ID enthalten ist, lautet **WindowsPhone.ExternalStorageId**.</span><span class="sxs-lookup"><span data-stu-id="ffa59-160">The name of the property that contains this ID is **WindowsPhone.ExternalStorageId**.</span></span>

```csharp
using Windows.Storage;

// Get the logical root folder for all external storage devices.
StorageFolder externalDevices = Windows.Storage.KnownFolders.RemovableDevices;

// Get the first child folder, which represents the SD card.
StorageFolder sdCard = (await externalDevices.GetFoldersAsync()).FirstOrDefault();

if (sdCard != null)
{
    var allProperties = sdCard.Properties;
    IEnumerable<string> propertiesToRetrieve = new List<string> { "WindowsPhone.ExternalStorageId" };

    var storageIdProperties = await allProperties.RetrievePropertiesAsync(propertiesToRetrieve);

    string cardId = (string)storageIdProperties["WindowsPhone.ExternalStorageId"];

    if (...) // If cardID matches the cached ID of a recognized card.
    {
        // Card is recognized. Index contents opportunistically.
    }
    else
    {
        // Card is not recognized. Index contents immediately.
    }
}
```

 

 
