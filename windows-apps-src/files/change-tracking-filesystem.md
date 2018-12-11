---
title: Verfolgen Sie die Datei systemänderungen im Hintergrund
description: Beschreibt, wie Sie die Änderungen in Dateien und Ordner im Hintergrund nachverfolgt werden, wenn Benutzer auf das System bewegen.
ms.date: 11/20/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: e90692753924572a932767b9c188ed6d24f94593
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8892141"
---
# <a name="track-file-system-changes-in-the-background"></a><span data-ttu-id="fac88-104">Verfolgen Sie die Datei systemänderungen im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="fac88-104">Track file system changes in the background</span></span>

<span data-ttu-id="fac88-105">Die [StorageLibraryChangeTracker](https://docs.microsoft.com/uwp/api/Windows.Storage.StorageLibraryChangeTracker) -Klasse ermöglicht apps das Nachverfolgen der Änderungen in Dateien und Ordnern, wenn Benutzer das System bewegen.</span><span class="sxs-lookup"><span data-stu-id="fac88-105">The [StorageLibraryChangeTracker](https://docs.microsoft.com/uwp/api/Windows.Storage.StorageLibraryChangeTracker) class allows apps to track changes in files and folders as users move them around the system.</span></span> <span data-ttu-id="fac88-106">Mit der **StorageLibraryChangeTracker** -Klasse, kann eine app nachverfolgt werden:</span><span class="sxs-lookup"><span data-stu-id="fac88-106">Using the **StorageLibraryChangeTracker** class, an app can track:</span></span>

- <span data-ttu-id="fac88-107">Datei einschließlich hinzufügen, löschen, ändern.</span><span class="sxs-lookup"><span data-stu-id="fac88-107">File operations including add, delete, modify.</span></span>
- <span data-ttu-id="fac88-108">Ordner Vorgänge wie z. B. umbenennen und löschen.</span><span class="sxs-lookup"><span data-stu-id="fac88-108">Folder operations such as renames and deletes.</span></span>
- <span data-ttu-id="fac88-109">Dateien und Ordner auf dem Laufwerk verschieben.</span><span class="sxs-lookup"><span data-stu-id="fac88-109">Files and folders moving on the drive.</span></span>

<span data-ttu-id="fac88-110">Verwenden Sie dieses Handbuch erfahren, das Programing Modell für die Arbeit mit der Änderung Tracker, einige Codebeispiele zeigen und verstehen die verschiedenen Arten von Dateien, die von **StorageLibraryChangeTracker**nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="fac88-110">Use this guide to learn the programing model for working with the change tracker, view some sample code, and understand the different types of file operations that are tracked by **StorageLibraryChangeTracker**.</span></span>

<span data-ttu-id="fac88-111">**StorageLibraryChangeTracker** funktioniert für Benutzer Bibliotheken oder für alle Ordner auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="fac88-111">**StorageLibraryChangeTracker** works for user libraries, or for any folder on the local machine.</span></span> <span data-ttu-id="fac88-112">Dazu zählen, sekundäre Laufwerke oder Wechseldatenträger zu verwenden, aber enthält keine NAS-Laufwerke und Netzwerklaufwerke.</span><span class="sxs-lookup"><span data-stu-id="fac88-112">This includes secondary drives or removable drives but does not include NAS drives or network drives.</span></span>

## <a name="using-the-change-tracker"></a><span data-ttu-id="fac88-113">Verwenden die Änderung tracker</span><span class="sxs-lookup"><span data-stu-id="fac88-113">Using the change tracker</span></span>

<span data-ttu-id="fac88-114">Die Änderung Tracker wird als ein kreisförmiges Puffer Speichern der letzten *N* Dateisystemvorgänge auf System implementiert.</span><span class="sxs-lookup"><span data-stu-id="fac88-114">The change tracker is implemented on system as a circular buffer storing the last *N* file system operations.</span></span> <span data-ttu-id="fac88-115">Apps, lesen die Änderungen auf den Puffer und verarbeiten sie in ihre eigenen Funktionen können.</span><span class="sxs-lookup"><span data-stu-id="fac88-115">Apps are able to read the changes off of the buffer and then process them into their own experiences.</span></span> <span data-ttu-id="fac88-116">Wenn Sie die app mit den Änderungen fertig sind, sie die Änderungen als verarbeitet gekennzeichnet und nie, sie erneut angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fac88-116">Once the app is finished with the changes it marks the changes as processed and will never see them again.</span></span>

<span data-ttu-id="fac88-117">Um die Tracker Änderung für einen Ordner zu verwenden, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="fac88-117">To use the change tracker on a folder, follow these steps:</span></span>

1. <span data-ttu-id="fac88-118">Aktivieren Sie das Änderungsprotokoll für den Ordner.</span><span class="sxs-lookup"><span data-stu-id="fac88-118">Enable change tracking for the folder.</span></span>
2. <span data-ttu-id="fac88-119">Warten Sie auf Änderungen.</span><span class="sxs-lookup"><span data-stu-id="fac88-119">Wait for changes.</span></span>
3. <span data-ttu-id="fac88-120">Lesen Sie die Änderungen.</span><span class="sxs-lookup"><span data-stu-id="fac88-120">Read changes.</span></span>
4. <span data-ttu-id="fac88-121">Akzeptieren Sie die Änderungen.</span><span class="sxs-lookup"><span data-stu-id="fac88-121">Accept changes.</span></span>

<span data-ttu-id="fac88-122">In den nächsten Abschnitten werden durch die einzelnen Schritte für einige Codebeispiele geführt.</span><span class="sxs-lookup"><span data-stu-id="fac88-122">The next sections walk through each of the steps with some code examples.</span></span> <span data-ttu-id="fac88-123">Das vollständige Codebeispiel wird am Ende des Artikels bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="fac88-123">The complete code sample is provided at the end of the article.</span></span>

### <a name="enable-the-change-tracker"></a><span data-ttu-id="fac88-124">Aktivieren Sie die Änderung tracker</span><span class="sxs-lookup"><span data-stu-id="fac88-124">Enable the change tracker</span></span>

<span data-ttu-id="fac88-125">Als erstes, die die app muss ist auf dem System mitzuteilen, dass er eine angegebene Bibliothek im Änderungsprotokoll interessiert ist.</span><span class="sxs-lookup"><span data-stu-id="fac88-125">The first thing that the app needs to do is to tell the system that it is interested in change tracking a given library.</span></span> <span data-ttu-id="fac88-126">Dies geschieht durch Aufrufen der Methode [Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) auf die Änderung Tracker für die Bibliothek von Interesse sind.</span><span class="sxs-lookup"><span data-stu-id="fac88-126">It does this by calling the [Enable](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) method on the change tracker for the library of interest.</span></span>

```csharp
StorageLibrary videosLib = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
StorageLibraryChangeTracker videoTracker = videosLib.ChangeTracker;
videoTracker.Enable();
```

<span data-ttu-id="fac88-127">Einige wichtige Hinweise:</span><span class="sxs-lookup"><span data-stu-id="fac88-127">A few important notes:</span></span>

- <span data-ttu-id="fac88-128">Stellen Sie sicher, dass Ihre app über die Berechtigung zur richtigen Bibliothek im Manifest verfügt, vor dem Erstellen des [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) -Objekts.</span><span class="sxs-lookup"><span data-stu-id="fac88-128">Make sure your app has permission to the correct library in the manifest before creating the [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) object.</span></span> <span data-ttu-id="fac88-129">Weitere Informationen finden Sie in [Den Dateizugriff](https://docs.microsoft.com/en-us/windows/uwp/files/file-access-permissions) .</span><span class="sxs-lookup"><span data-stu-id="fac88-129">See [File Access Permissions](https://docs.microsoft.com/en-us/windows/uwp/files/file-access-permissions) for more details.</span></span>
- <span data-ttu-id="fac88-130">[Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) ist threadsicher, den Zeiger wird nicht zurückgesetzt und so oft wie (mehr dazu später) aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="fac88-130">[Enable](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) is thread safe, will not reset your pointer, and can be called as many times as you like (more on this later).</span></span>

![Aktivieren eine leere Änderung tracker](images/changetracker-enable.png)

### <a name="wait-for-changes"></a><span data-ttu-id="fac88-132">Warten Sie, bis Änderungen</span><span class="sxs-lookup"><span data-stu-id="fac88-132">Wait for changes</span></span>

<span data-ttu-id="fac88-133">Nachdem die Änderung Tracker initialisiert wurde, beginnt es aller Vorgänge aufzeichnen, die in einer Bibliothek auch auftreten, während die app nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fac88-133">After the change tracker is initialized, it will begin to record all of the operations that occur within a library, even while the app isn’t running.</span></span> <span data-ttu-id="fac88-134">Apps können registrieren, um zu einem beliebigen Zeitpunkt aktiviert werden, die durch die Registrierung für das Ereignis [StorageLibraryChangedTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.StorageLibraryContentChangedTrigger) geändert wird.</span><span class="sxs-lookup"><span data-stu-id="fac88-134">Apps can register to be activated any time there is a change by registering for the [StorageLibraryChangedTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.StorageLibraryContentChangedTrigger) event.</span></span>

![Änderungen, die Änderung Tracker hinzugefügt wird, ohne dass die app zu lesen](images/changetracker-waiting.png)

### <a name="read-the-changes"></a><span data-ttu-id="fac88-136">Lesen Sie die Änderungen</span><span class="sxs-lookup"><span data-stu-id="fac88-136">Read the changes</span></span>

<span data-ttu-id="fac88-137">Die app kann dann Abfragen, ändert sich von der Änderung Tracker und erhalten eine Liste der Änderungen seit dem letzten ausgecheckt.</span><span class="sxs-lookup"><span data-stu-id="fac88-137">The app can then poll for changes from the change tracker and receive a list of the changes since the last time it checked.</span></span> <span data-ttu-id="fac88-138">Der folgende Code veranschaulicht das Abrufen einer Liste von Änderungen von Tracker ändern.</span><span class="sxs-lookup"><span data-stu-id="fac88-138">The code below shows how to get a list of changes from the change tracker.</span></span>

```csharp
StorageLibrary videosLibrary = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
videosLibrary.ChangeTracker.Enable();
StorageLibraryChangeReader videoChangeReader = videosLibrary.ChangeTracker.GetChangeReader();
IReadOnlyList changeSet = await changeReader.ReadBatchAsync();
```

<span data-ttu-id="fac88-139">Die app ist verantwortlich für die Verarbeitung von Änderungen in eine eigene Benutzeroberfläche oder eine Datenbank nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="fac88-139">The app is then responsible for processing the changes into its own experience or database as needed.</span></span>

![Lesen Sie die Änderungen aus der Änderung Tracker in eine app-Datenbank](images/changetracker-reading.png)

> [!TIP]
> <span data-ttu-id="fac88-141">Der zweite Aufruf zu ist Verteidigung gegen eine Racebedingung, wenn der Benutzer einen anderen Ordner zur Bibliothek hinzufügt, während Ihre app Änderungen gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="fac88-141">The second call to enable is to defend against a race condition if the user adds another folder to the library while your app is reading changes.</span></span> <span data-ttu-id="fac88-142">Ohne die zusätzlichen Aufruf zum **Aktivieren** fehl der Code mit EcSearchFolderScopeViolation (0 x 80070490), wenn der Benutzer die Ordner in ihrer Bibliothek geändert wird</span><span class="sxs-lookup"><span data-stu-id="fac88-142">Without the extra call to **Enable** the code will fail with ecSearchFolderScopeViolation (0x80070490) if the user is changing the folders in their library</span></span>

### <a name="accept-the-changes"></a><span data-ttu-id="fac88-143">Akzeptieren Sie die Änderung</span><span class="sxs-lookup"><span data-stu-id="fac88-143">Accept the changes</span></span>

<span data-ttu-id="fac88-144">Nach Abschluss die app verarbeitet die Änderungen, sollten sie über den das System nicht diese Änderungen werden mehr durch Aufrufen der Methode [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fac88-144">After the app is done processing the changes, it should tell the system to never show those changes again by calling the [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync) method.</span></span>

```csharp
await changeReader.AcceptChangesAsync();
```

![Markieren Änderungen als lesen, damit sie erneut nie angezeigt werden](images/changetracker-accepting.png)

<span data-ttu-id="fac88-146">Die app jetzt erhalten nur neue Änderungen beim Tracker Änderung in der Zukunft zu lesen.</span><span class="sxs-lookup"><span data-stu-id="fac88-146">The app will now only receive new changes when reading the change tracker in the future.</span></span>

- <span data-ttu-id="fac88-147">Wenn Änderungen zwischen aufruft, [ReadBatchAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.readbatchasync) und [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync)geschehen, kann der Zeiger wird nur auf die letzte Änderung die app angezeigt wurde erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="fac88-147">If changes have happened between calling [ReadBatchAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.readbatchasync) and [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync), the pointer will be only be advanced to the most recent change the app has seen.</span></span> <span data-ttu-id="fac88-148">Diese anderen Änderungen ist weiterhin verfügbar das nächste Mal **ReadBatchAsync ruft**.</span><span class="sxs-lookup"><span data-stu-id="fac88-148">Those other changes will still be available the next time it calls **ReadBatchAsync**.</span></span>
- <span data-ttu-id="fac88-149">Akzeptieren die Änderungen nicht bewirkt, dass das System den gleichen Satz von Änderungen das nächste Mal zurück, das die app **ReadBatchAsync**aufruft.</span><span class="sxs-lookup"><span data-stu-id="fac88-149">Not accepting the changes will cause the system to return the same set of changes the next time the app calls **ReadBatchAsync**.</span></span>

## <a name="important-things-to-remember"></a><span data-ttu-id="fac88-150">Wichtige Dinge zu beachten</span><span class="sxs-lookup"><span data-stu-id="fac88-150">Important things to remember</span></span>

<span data-ttu-id="fac88-151">Wenn Sie die Änderung Tracker verwenden, gibt es einige Dinge, die Sie bedenken sollten sicherstellen, dass alles ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="fac88-151">When using the change tracker, there are a few things that you should keep in mind to make sure that everything is working correctly.</span></span>

### <a name="buffer-overruns"></a><span data-ttu-id="fac88-152">Pufferüberläufe</span><span class="sxs-lookup"><span data-stu-id="fac88-152">Buffer overruns</span></span>

<span data-ttu-id="fac88-153">Obwohl wir versuchen, reservieren Sie ausreichend Platz in Tracker ändern, halten Sie die Vorgänge, die auf dem System ausgeführt werden, bis Ihre app gelesen werden kann, ist es sehr einfach, ein Szenario sich vorzustellen, an dem die app die Änderungen Lesen nicht, bevor der kreisförmige Puffer selbst überschreibt.</span><span class="sxs-lookup"><span data-stu-id="fac88-153">Although we try to reserve enough space in the change tracker to hold all the operations happening on the system until your app can read them, it is very easy to imagine a scenario where the app doesn’t read the changes before the circular buffer overwrites itself.</span></span> <span data-ttu-id="fac88-154">Insbesondere dann, wenn der Benutzer und die Daten aus einer Sicherung wiederhergestellt oder eine große Sammlung von Bildern auf dem Handy Kamera Synchronisierung.</span><span class="sxs-lookup"><span data-stu-id="fac88-154">Especially if the user is restoring data from a backup or syncing a large collection of pictures from their camera phone.</span></span>

<span data-ttu-id="fac88-155">In diesem Fall wird **ReadBatchAsync** den Fehlercode [StorageLibraryChangeType.ChangeTrackingLost](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetype)zurück.</span><span class="sxs-lookup"><span data-stu-id="fac88-155">In this case, **ReadBatchAsync** will return the error code [StorageLibraryChangeType.ChangeTrackingLost](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetype).</span></span> <span data-ttu-id="fac88-156">Wenn Ihre app dieser Fehlercode empfängt, bedeutet dies ein paar Dinge:</span><span class="sxs-lookup"><span data-stu-id="fac88-156">If your app receives this error code, it means a couple things:</span></span>

* <span data-ttu-id="fac88-157">Der Puffer hat selbst seit dem letzten überschrieben, die Sie besprochen.</span><span class="sxs-lookup"><span data-stu-id="fac88-157">The buffer has overwritten itself since the last time you looked at it.</span></span> <span data-ttu-id="fac88-158">Die beste Vorgehensweise ist für die Bibliothek erneut, da alle Informationen aus der Tracker möglicherweise nicht vollständig.</span><span class="sxs-lookup"><span data-stu-id="fac88-158">The best course of action is to recrawl the library, because any information from the tracker will be incomplete.</span></span>
* <span data-ttu-id="fac88-159">Die Änderung Tracker wird erst [zurücksetzen aufrufen](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.reset)weitere Änderungen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="fac88-159">The change tracker will not return any more changes until you call [Reset](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.reset).</span></span> <span data-ttu-id="fac88-160">Nachdem die app zurücksetzen aufruft, wird der Zeiger verschoben werden, um die letzte Änderung und Tracking normal fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="fac88-160">After the app calls reset, the pointer will be moved to the most recent change and tracking will resume normally.</span></span>

<span data-ttu-id="fac88-161">Es seltenen Fällen abrufen, jedoch in Szenarien, in denen der Benutzer eine große Anzahl von Dateien auf ihrer Festplatte verschoben wird, nicht wir die Änderung Tracker Sprechblase und zu viel Speicher belegen sollten.</span><span class="sxs-lookup"><span data-stu-id="fac88-161">It should be rare to get these cases, but in scenarios where the user is moving a large number of files around on their disk we don’t want the change tracker to balloon and take up too much storage.</span></span> <span data-ttu-id="fac88-162">Sollte apps auf massive Dateisystemvorgänge reagieren, während die Kundenzufriedenheit in Windows nicht beschädigt werden können.</span><span class="sxs-lookup"><span data-stu-id="fac88-162">This should allow apps to react to massive file system operations while not damaging the customer experience in Windows.</span></span>

### <a name="changes-to-a-storagelibrary"></a><span data-ttu-id="fac88-163">Änderungen an einer StorageLibrary</span><span class="sxs-lookup"><span data-stu-id="fac88-163">Changes to a StorageLibrary</span></span>

<span data-ttu-id="fac88-164">Die [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) -Klasse, die als Root-Ordner, die anderen Ordner enthalten eine virtuelle Gruppe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="fac88-164">The [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) class exists as a virtual group of root folders that contain other folders.</span></span> <span data-ttu-id="fac88-165">Um dies zu einem Datei System ändern Tracker abzugleichen, haben wir die folgenden Optionen:</span><span class="sxs-lookup"><span data-stu-id="fac88-165">To reconcile this with a file system change tracker, we made the following choices:</span></span>

- <span data-ttu-id="fac88-166">Alle Änderungen an der Stamm-Bibliotheksordner absteigende werden in der Änderung Tracker dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="fac88-166">Any changes to descendent of the root library folders will be represented in the change tracker.</span></span> <span data-ttu-id="fac88-167">Die Bibliothek Stammordner können mithilfe der Eigenschaft [Ordner](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="fac88-167">The root library folders can be found using the [Folders](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) property.</span></span>
- <span data-ttu-id="fac88-168">Hinzufügen oder Entfernen von Stammordner aus einer **StorageLibrary** (über [RequestAddFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestaddfolderasync) und [RequestRemoveFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestremovefolderasync)) wird keinen Eintrag in der Änderung Tracker erstellen.</span><span class="sxs-lookup"><span data-stu-id="fac88-168">Adding or removing root folders from a **StorageLibrary** (through [RequestAddFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestaddfolderasync) and [RequestRemoveFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestremovefolderasync)) will not create an entry in the change tracker.</span></span> <span data-ttu-id="fac88-169">Diese Änderungen können über das Ereignis [DefinitionChanged](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.definitionchanged) oder durch die Enumeration der Stammordner in der Bibliothek, die mithilfe der Eigenschaft [Ordner](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) überwacht werden.</span><span class="sxs-lookup"><span data-stu-id="fac88-169">These changes can be tracked through the [DefinitionChanged](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.definitionchanged) event or by enumerating the root folders in the library using the [Folders](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) property.</span></span>
- <span data-ttu-id="fac88-170">Wenn Sie ein Ordner mit Inhalte bereits in der Bibliothek hinzugefügt wird, kann es keine Änderung der Benachrichtigung oder ändern Einträge generiert.</span><span class="sxs-lookup"><span data-stu-id="fac88-170">If a folder with content already in it is added to the library, there will not be a change notification or change tracker entries generated.</span></span> <span data-ttu-id="fac88-171">Alle nachfolgenden Änderungen auf die Nachfolgerelemente dieses Ordners Benachrichtigungen generiert und Einträge zu ändern.</span><span class="sxs-lookup"><span data-stu-id="fac88-171">Any subsequent changes to the descendants of that folder will generate notifications and change tracker entries.</span></span>

### <a name="calling-the-enable-method"></a><span data-ttu-id="fac88-172">Aufrufen der Methode aktivieren</span><span class="sxs-lookup"><span data-stu-id="fac88-172">Calling the Enable method</span></span>

<span data-ttu-id="fac88-173">Apps dürfen [Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) aufrufen, als das Dateisystem tracking start und vor jedem Aufzählung von Änderungen.</span><span class="sxs-lookup"><span data-stu-id="fac88-173">Apps should call [Enable](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) as soon as they start tracking the file system and before every enumeration of the changes.</span></span> <span data-ttu-id="fac88-174">Dadurch wird sichergestellt, dass alle Änderungen durch die Änderung Tracker aufgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="fac88-174">This will ensure that all changes will be captured by the change tracker.</span></span>  

## <a name="putting-it-together"></a><span data-ttu-id="fac88-175">Letzte Schritte</span><span class="sxs-lookup"><span data-stu-id="fac88-175">Putting it together</span></span>

<span data-ttu-id="fac88-176">Hier wurde der gesamte Code, der verwendet wird, ändert sich der von der Videobibliothek registrieren und starten die vom Änderung Tracker abrufen, die Änderungen.</span><span class="sxs-lookup"><span data-stu-id="fac88-176">Here is all the code that is used to register for the changes from the video library and start pulling the changes from the change tracker.</span></span>

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
