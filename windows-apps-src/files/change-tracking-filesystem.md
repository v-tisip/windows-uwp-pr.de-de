---
title: Datei systemänderungen im Hintergrund nachverfolgen
description: Beschreibt, wie Sie die Änderungen in Dateien und Ordner im Hintergrund nachverfolgt, wenn Benutzer das System bewegen.
ms.date: 11/20/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: e90692753924572a932767b9c188ed6d24f94593
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8701862"
---
# <a name="track-file-system-changes-in-the-background"></a><span data-ttu-id="3e4cb-104">Datei systemänderungen im Hintergrund nachverfolgen</span><span class="sxs-lookup"><span data-stu-id="3e4cb-104">Track file system changes in the background</span></span>

<span data-ttu-id="3e4cb-105">Die [StorageLibraryChangeTracker](https://docs.microsoft.com/uwp/api/Windows.Storage.StorageLibraryChangeTracker) -Klasse ermöglicht apps das Nachverfolgen der Änderungen in Dateien und Ordner, wenn Benutzer das System bewegen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-105">The [StorageLibraryChangeTracker](https://docs.microsoft.com/uwp/api/Windows.Storage.StorageLibraryChangeTracker) class allows apps to track changes in files and folders as users move them around the system.</span></span> <span data-ttu-id="3e4cb-106">Mit der **StorageLibraryChangeTracker** -Klasse, kann eine app nachverfolgt werden:</span><span class="sxs-lookup"><span data-stu-id="3e4cb-106">Using the **StorageLibraryChangeTracker** class, an app can track:</span></span>

- <span data-ttu-id="3e4cb-107">Datei-Operationen u. a. hinzufügen, löschen, ändern.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-107">File operations including add, delete, modify.</span></span>
- <span data-ttu-id="3e4cb-108">Ordner Vorgänge wie z. B. umbenennen und löschen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-108">Folder operations such as renames and deletes.</span></span>
- <span data-ttu-id="3e4cb-109">Dateien und Ordner auf dem Laufwerk verschieben.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-109">Files and folders moving on the drive.</span></span>

<span data-ttu-id="3e4cb-110">Verwenden Sie dieses Handbuch erfahren, das Programing Modell für die Arbeit mit der Änderung Tracker, einige Codebeispiele zeigen und Verstehen der unterschiedlichen Arten von Dateien, die durch **StorageLibraryChangeTracker**nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-110">Use this guide to learn the programing model for working with the change tracker, view some sample code, and understand the different types of file operations that are tracked by **StorageLibraryChangeTracker**.</span></span>

<span data-ttu-id="3e4cb-111">**StorageLibraryChangeTracker** funktioniert für Benutzer Bibliotheken oder für alle Ordner auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-111">**StorageLibraryChangeTracker** works for user libraries, or for any folder on the local machine.</span></span> <span data-ttu-id="3e4cb-112">Dazu zählen sekundären Laufwerke oder Wechseldatenträger zu verwenden, aber enthält keine NAS-Laufwerke und Netzlaufwerke.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-112">This includes secondary drives or removable drives but does not include NAS drives or network drives.</span></span>

## <a name="using-the-change-tracker"></a><span data-ttu-id="3e4cb-113">Verwenden den Änderung tracker</span><span class="sxs-lookup"><span data-stu-id="3e4cb-113">Using the change tracker</span></span>

<span data-ttu-id="3e4cb-114">Der Änderung Tracker wird als ein kreisförmiges Puffer Speichern der letzten *N* Dateisystemvorgänge auf System implementiert.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-114">The change tracker is implemented on system as a circular buffer storing the last *N* file system operations.</span></span> <span data-ttu-id="3e4cb-115">Apps können die Änderungen aus dem Puffer lesen und verarbeiten sie in ihre eigenen Funktionen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-115">Apps are able to read the changes off of the buffer and then process them into their own experiences.</span></span> <span data-ttu-id="3e4cb-116">Wenn die app mit den Änderungen abgeschlossen ist, es werden die Änderungen als verarbeitet gekennzeichnet und nie, sie erneut angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-116">Once the app is finished with the changes it marks the changes as processed and will never see them again.</span></span>

<span data-ttu-id="3e4cb-117">Um die Tracker Änderung für einen Ordner zu verwenden, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="3e4cb-117">To use the change tracker on a folder, follow these steps:</span></span>

1. <span data-ttu-id="3e4cb-118">Aktivieren Sie Änderungsprotokoll für den Ordner.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-118">Enable change tracking for the folder.</span></span>
2. <span data-ttu-id="3e4cb-119">Warten Sie auf Änderungen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-119">Wait for changes.</span></span>
3. <span data-ttu-id="3e4cb-120">Lesen Sie Änderungen an.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-120">Read changes.</span></span>
4. <span data-ttu-id="3e4cb-121">Akzeptieren Sie Änderungen an.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-121">Accept changes.</span></span>

<span data-ttu-id="3e4cb-122">In den nächsten Abschnitten werden durch die einzelnen Schritte für einige Codebeispiele geführt.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-122">The next sections walk through each of the steps with some code examples.</span></span> <span data-ttu-id="3e4cb-123">Das vollständige Codebeispiel wird am Ende des Artikels bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-123">The complete code sample is provided at the end of the article.</span></span>

### <a name="enable-the-change-tracker"></a><span data-ttu-id="3e4cb-124">Aktivieren Sie den Änderung tracker</span><span class="sxs-lookup"><span data-stu-id="3e4cb-124">Enable the change tracker</span></span>

<span data-ttu-id="3e4cb-125">Der erste Schritt, der die app muss ist, um dem System mitzuteilen, dass er eine angegebene Bibliothek im Änderungsprotokoll interessiert ist.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-125">The first thing that the app needs to do is to tell the system that it is interested in change tracking a given library.</span></span> <span data-ttu-id="3e4cb-126">Dies geschieht durch Aufrufen von der Methode [Aktivieren Sie](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) auf die Änderung Tracker für die Bibliothek von Interesse sind.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-126">It does this by calling the [Enable](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) method on the change tracker for the library of interest.</span></span>

```csharp
StorageLibrary videosLib = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
StorageLibraryChangeTracker videoTracker = videosLib.ChangeTracker;
videoTracker.Enable();
```

<span data-ttu-id="3e4cb-127">Einige wichtige Hinweise:</span><span class="sxs-lookup"><span data-stu-id="3e4cb-127">A few important notes:</span></span>

- <span data-ttu-id="3e4cb-128">Stellen Sie sicher, dass Ihre app berechtigt zur richtigen Bibliothek im Manifest vor dem Erstellen des [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) -Objekts.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-128">Make sure your app has permission to the correct library in the manifest before creating the [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) object.</span></span> <span data-ttu-id="3e4cb-129">Weitere Informationen finden Sie in der [Berechtigungen für den Dateizugriff](https://docs.microsoft.com/en-us/windows/uwp/files/file-access-permissions) .</span><span class="sxs-lookup"><span data-stu-id="3e4cb-129">See [File Access Permissions](https://docs.microsoft.com/en-us/windows/uwp/files/file-access-permissions) for more details.</span></span>
- <span data-ttu-id="3e4cb-130">[Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) ist threadsicher, den Zeiger wird nicht zurückgesetzt und so oft wie (mehr dazu später gewünscht) aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-130">[Enable](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) is thread safe, will not reset your pointer, and can be called as many times as you like (more on this later).</span></span>

![Aktivieren eine leere Änderung tracker](images/changetracker-enable.png)

### <a name="wait-for-changes"></a><span data-ttu-id="3e4cb-132">Warten Sie, bis Änderungen</span><span class="sxs-lookup"><span data-stu-id="3e4cb-132">Wait for changes</span></span>

<span data-ttu-id="3e4cb-133">Nachdem der Änderung Tracker initialisiert wurde, beginnt dieser aller Vorgänge aufzeichnen, die in einer Bibliothek auch auftreten, während die app nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-133">After the change tracker is initialized, it will begin to record all of the operations that occur within a library, even while the app isn’t running.</span></span> <span data-ttu-id="3e4cb-134">Apps können registrieren, um jederzeit aktiviert, wenn eine Änderung durch die Registrierung für das Ereignis [StorageLibraryChangedTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.StorageLibraryContentChangedTrigger) vorliegt.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-134">Apps can register to be activated any time there is a change by registering for the [StorageLibraryChangedTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.StorageLibraryContentChangedTrigger) event.</span></span>

![Änderungen, die Änderung Tracker hinzugefügt wird, ohne dass die app zu lesen](images/changetracker-waiting.png)

### <a name="read-the-changes"></a><span data-ttu-id="3e4cb-136">Lesen Sie die Änderungen</span><span class="sxs-lookup"><span data-stu-id="3e4cb-136">Read the changes</span></span>

<span data-ttu-id="3e4cb-137">Die app kann dann Abfragen, ändert sich von der Änderung Tracker und erhalten eine Liste der Änderungen seit dem letzten ausgecheckt.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-137">The app can then poll for changes from the change tracker and receive a list of the changes since the last time it checked.</span></span> <span data-ttu-id="3e4cb-138">Der folgende Code zeigt, wie eine Liste von Änderungen aus der Änderung Tracker abrufen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-138">The code below shows how to get a list of changes from the change tracker.</span></span>

```csharp
StorageLibrary videosLibrary = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
videosLibrary.ChangeTracker.Enable();
StorageLibraryChangeReader videoChangeReader = videosLibrary.ChangeTracker.GetChangeReader();
IReadOnlyList changeSet = await changeReader.ReadBatchAsync();
```

<span data-ttu-id="3e4cb-139">Die app ist verantwortlich für die Verarbeitung der Änderungen in eine eigene Benutzeroberfläche oder eine Datenbank je nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-139">The app is then responsible for processing the changes into its own experience or database as needed.</span></span>

![Lesen Sie die Änderungen aus der Änderung Tracker in eine app-Datenbank](images/changetracker-reading.png)

> [!TIP]
> <span data-ttu-id="3e4cb-141">Der zweite Aufruf von aktivieren ist zur Verteidigung gegen eine Racebedingung, wenn der Benutzer einen anderen Ordner zur Bibliothek hinzufügt, während Ihre app Änderungen gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-141">The second call to enable is to defend against a race condition if the user adds another folder to the library while your app is reading changes.</span></span> <span data-ttu-id="3e4cb-142">Ohne die zusätzlichen Aufruf zum **Aktivieren** fehl der Code mit EcSearchFolderScopeViolation (0 x 80070490) Wenn der Benutzer die Ordner in ihrer Bibliothek ändert</span><span class="sxs-lookup"><span data-stu-id="3e4cb-142">Without the extra call to **Enable** the code will fail with ecSearchFolderScopeViolation (0x80070490) if the user is changing the folders in their library</span></span>

### <a name="accept-the-changes"></a><span data-ttu-id="3e4cb-143">Akzeptieren Sie die Änderung</span><span class="sxs-lookup"><span data-stu-id="3e4cb-143">Accept the changes</span></span>

<span data-ttu-id="3e4cb-144">Nach Abschluss die app verarbeiten die Änderungen, sollten sie das System nicht diese Änderungen erneut angezeigt werden durch Aufrufen der Methode [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync) erkennen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-144">After the app is done processing the changes, it should tell the system to never show those changes again by calling the [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync) method.</span></span>

```csharp
await changeReader.AcceptChangesAsync();
```

![Markieren von Änderungen als lesen, damit er erneut nie angezeigt werden](images/changetracker-accepting.png)

<span data-ttu-id="3e4cb-146">Die app jetzt erhalten nur neue Änderungen beim Tracker Änderung in der Zukunft zu lesen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-146">The app will now only receive new changes when reading the change tracker in the future.</span></span>

- <span data-ttu-id="3e4cb-147">Wenn Änderungen zwischen aufruft, [ReadBatchAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.readbatchasync) und [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync)geschehen, kann der Zeiger wird nur auf die letzte Änderung die app angezeigt wurde erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-147">If changes have happened between calling [ReadBatchAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.readbatchasync) and [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync), the pointer will be only be advanced to the most recent change the app has seen.</span></span> <span data-ttu-id="3e4cb-148">Diese anderen Änderungen ist weiterhin verfügbar das nächste Mal **ReadBatchAsync**aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-148">Those other changes will still be available the next time it calls **ReadBatchAsync**.</span></span>
- <span data-ttu-id="3e4cb-149">Die Änderungen nicht akzeptieren, wird das System den gleichen Satz von Änderungen das nächste Mal zurückgeben, das die app **ReadBatchAsync**aufruft.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-149">Not accepting the changes will cause the system to return the same set of changes the next time the app calls **ReadBatchAsync**.</span></span>

## <a name="important-things-to-remember"></a><span data-ttu-id="3e4cb-150">Wichtige Dinge zu beachten</span><span class="sxs-lookup"><span data-stu-id="3e4cb-150">Important things to remember</span></span>

<span data-ttu-id="3e4cb-151">Wenn Sie den Änderung Tracker verwenden zu können, stehen einige Dinge, die Sie bedenken sollten sicherstellen, dass alles ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-151">When using the change tracker, there are a few things that you should keep in mind to make sure that everything is working correctly.</span></span>

### <a name="buffer-overruns"></a><span data-ttu-id="3e4cb-152">Pufferüberläufe</span><span class="sxs-lookup"><span data-stu-id="3e4cb-152">Buffer overruns</span></span>

<span data-ttu-id="3e4cb-153">Obwohl wir versuchen, reservieren Sie ausreichend Platz in der Änderung Tracker enthalten alle Vorgänge, die auf dem System ausgeführt werden, bis Ihre app gelesen werden kann, ist es sehr einfach, ein Szenario vorstellen, an dem die app die Änderungen Lesen nicht, bevor der kreisförmige Puffer selbst überschreibt.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-153">Although we try to reserve enough space in the change tracker to hold all the operations happening on the system until your app can read them, it is very easy to imagine a scenario where the app doesn’t read the changes before the circular buffer overwrites itself.</span></span> <span data-ttu-id="3e4cb-154">Insbesondere dann, wenn der Benutzer Wiederherstellen von Daten aus einer Sicherung oder eine große Sammlung von Bildern von ihrem Handy synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-154">Especially if the user is restoring data from a backup or syncing a large collection of pictures from their camera phone.</span></span>

<span data-ttu-id="3e4cb-155">In diesem Fall wird **ReadBatchAsync** den Fehlercode [StorageLibraryChangeType.ChangeTrackingLost](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetype)zurück.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-155">In this case, **ReadBatchAsync** will return the error code [StorageLibraryChangeType.ChangeTrackingLost](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetype).</span></span> <span data-ttu-id="3e4cb-156">Wenn Ihre app dieser Fehlercode empfängt, bedeutet dies ein paar Dinge:</span><span class="sxs-lookup"><span data-stu-id="3e4cb-156">If your app receives this error code, it means a couple things:</span></span>

* <span data-ttu-id="3e4cb-157">Der Puffer hat sich selbst seit dem letzten überschrieben angezeigten es.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-157">The buffer has overwritten itself since the last time you looked at it.</span></span> <span data-ttu-id="3e4cb-158">Die beste Vorgehensweise ist für die Bibliothek erneut, da alle Informationen aus der Tracker möglicherweise nicht vollständig.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-158">The best course of action is to recrawl the library, because any information from the tracker will be incomplete.</span></span>
* <span data-ttu-id="3e4cb-159">Der Änderung Tracker wird erst Sie [Zurücksetzen rufen](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.reset)weitere Änderungen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-159">The change tracker will not return any more changes until you call [Reset](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.reset).</span></span> <span data-ttu-id="3e4cb-160">Nachdem die app zurücksetzen aufgerufen hat, der Zeiger wird in der letzten Änderung verschoben werden und Tracking normal fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-160">After the app calls reset, the pointer will be moved to the most recent change and tracking will resume normally.</span></span>

<span data-ttu-id="3e4cb-161">Es sollte seltenen Fällen abgerufen werden, in Szenarien, in denen der Benutzer eine große Anzahl von Dateien auf ihrer Festplatte verschoben wird, soll jedoch nicht den Änderung Tracker Sprechblase und zu viel Speicher belegen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-161">It should be rare to get these cases, but in scenarios where the user is moving a large number of files around on their disk we don’t want the change tracker to balloon and take up too much storage.</span></span> <span data-ttu-id="3e4cb-162">Sollte apps auf massive Dateisystemvorgänge reagieren, während die Kundenzufriedenheit in Windows nicht beschädigt werden können.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-162">This should allow apps to react to massive file system operations while not damaging the customer experience in Windows.</span></span>

### <a name="changes-to-a-storagelibrary"></a><span data-ttu-id="3e4cb-163">Änderungen an einem StorageLibrary</span><span class="sxs-lookup"><span data-stu-id="3e4cb-163">Changes to a StorageLibrary</span></span>

<span data-ttu-id="3e4cb-164">Die [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) -Klasse, die als virtuelle Gruppe von Root-Ordner, die anderen Ordner enthalten vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-164">The [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) class exists as a virtual group of root folders that contain other folders.</span></span> <span data-ttu-id="3e4cb-165">Um dies zu einem Datei System ändern Tracker abzugleichen, haben wir die folgenden Optionen aus:</span><span class="sxs-lookup"><span data-stu-id="3e4cb-165">To reconcile this with a file system change tracker, we made the following choices:</span></span>

- <span data-ttu-id="3e4cb-166">Jegliche Änderungen an der Stamm-Bibliotheksordner absteigende werden in der Änderung Tracker dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-166">Any changes to descendent of the root library folders will be represented in the change tracker.</span></span> <span data-ttu-id="3e4cb-167">Die Bibliothek Stammordner können mithilfe der Eigenschaft [Ordner](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-167">The root library folders can be found using the [Folders](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) property.</span></span>
- <span data-ttu-id="3e4cb-168">Hinzufügen oder Entfernen von Stammordner aus einer **StorageLibrary** (über [RequestAddFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestaddfolderasync) und [RequestRemoveFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestremovefolderasync)) wird keinen Eintrag in der Änderung Tracker erstellen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-168">Adding or removing root folders from a **StorageLibrary** (through [RequestAddFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestaddfolderasync) and [RequestRemoveFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestremovefolderasync)) will not create an entry in the change tracker.</span></span> <span data-ttu-id="3e4cb-169">Diese Änderungen können über das Ereignis [DefinitionChanged](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.definitionchanged) oder durch die Enumeration der Stammordner in der Bibliothek mithilfe der Eigenschaft [Ordner](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) überwacht werden.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-169">These changes can be tracked through the [DefinitionChanged](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.definitionchanged) event or by enumerating the root folders in the library using the [Folders](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) property.</span></span>
- <span data-ttu-id="3e4cb-170">Wenn ein Ordner mit Inhalt bereits zur Bibliothek hinzugefügt wird, kann es keine Änderung Benachrichtigung oder Änderung Einträge generiert.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-170">If a folder with content already in it is added to the library, there will not be a change notification or change tracker entries generated.</span></span> <span data-ttu-id="3e4cb-171">Alle nachfolgenden Änderungen auf die Nachfolgerelemente dieses Ordners Benachrichtigungen generiert und Einträge zu ändern.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-171">Any subsequent changes to the descendants of that folder will generate notifications and change tracker entries.</span></span>

### <a name="calling-the-enable-method"></a><span data-ttu-id="3e4cb-172">Aufrufen der Methode aktivieren</span><span class="sxs-lookup"><span data-stu-id="3e4cb-172">Calling the Enable method</span></span>

<span data-ttu-id="3e4cb-173">Apps dürfen [Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) aufrufen, sobald sie Starten des Dateisystems nachverfolgen und vor jeder Aufzählung von Änderungen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-173">Apps should call [Enable](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) as soon as they start tracking the file system and before every enumeration of the changes.</span></span> <span data-ttu-id="3e4cb-174">Dadurch wird sichergestellt, dass alle Änderungen durch die Änderung Tracker aufgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-174">This will ensure that all changes will be captured by the change tracker.</span></span>  

## <a name="putting-it-together"></a><span data-ttu-id="3e4cb-175">Letzte Schritte</span><span class="sxs-lookup"><span data-stu-id="3e4cb-175">Putting it together</span></span>

<span data-ttu-id="3e4cb-176">Hier ist der Code, der verwendet wird, ändert sich der von der Videobibliothek registrieren und Starten vom Änderung Tracker abrufen, die Änderungen.</span><span class="sxs-lookup"><span data-stu-id="3e4cb-176">Here is all the code that is used to register for the changes from the video library and start pulling the changes from the change tracker.</span></span>

```csharp
private async void EnableChangeTracker()
{
    StorageLibrary videosLib = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
    StorageLibraryChangeTracker videoTracker = videosLib.ChangeTracker;
    videoTracker.Enable();
}

private async void GetChanges()
{
    StorageLibrary videosLibrary = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
    videosLibrary.ChangeTracker.Enable();
    StorageLibraryChangeReader videoChangeReader = videosLibrary.ChangeTracker.GetChangeReader();
    IReadOnlyList changeSet = await changeReader.ReadBatchAsync();


    //Below this line is for the blog post. Above the line is for the magazine
    foreach (StorageLibraryChange change in changeSet)
    {
        if (change.ChangeType == StorageLibraryChangeType.ChangeTrackingLost)
        {
            //We are in trouble. Nothing else is going to be valid.
            log("Resetting the change tracker");
            videosLibrary.ChangeTracker.Reset();
            return;
        }
        if (change.IsOfType(StorageItemTypes.Folder))
        {
            await HandleFileChange(change);
        }
        else if (change.IsOfType(StorageItemTypes.File))
        {
            await HandleFolderChange(change);
        }
        else if (change.IsOfType(StorageItemTypes.None))
        {
            if (change.ChangeType == StorageLibraryChangeType.Deleted)
            {
                RemoveItemFromDB(change.Path);
            }
        }
    }
    await changeReader.AcceptChangesAsync();
}
```
