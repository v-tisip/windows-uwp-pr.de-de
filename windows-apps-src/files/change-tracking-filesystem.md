---
title: Verfolgen Sie die Datei systemänderungen im Hintergrund
description: Beschreibt, wie Sie die Änderungen in Dateien und Ordner im Hintergrund nachverfolgt werden, wenn Benutzer auf das System bewegen.
ms.date: 11/20/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: e90692753924572a932767b9c188ed6d24f94593
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8926778"
---
# <a name="track-file-system-changes-in-the-background"></a>Verfolgen Sie die Datei systemänderungen im Hintergrund

Die [StorageLibraryChangeTracker](https://docs.microsoft.com/uwp/api/Windows.Storage.StorageLibraryChangeTracker) -Klasse ermöglicht apps das Nachverfolgen der Änderungen in Dateien und Ordnern, wenn Benutzer das System bewegen. Mit der **StorageLibraryChangeTracker** -Klasse, kann eine app nachverfolgt werden:

- Datei einschließlich hinzufügen, löschen, ändern.
- Ordner Vorgänge wie z. B. umbenennen und löschen.
- Dateien und Ordner auf dem Laufwerk verschieben.

Verwenden Sie dieses Handbuch erfahren, das Programing Modell für die Arbeit mit der Änderung Tracker, einige Codebeispiele zeigen und verstehen die verschiedenen Arten von Dateien, die von **StorageLibraryChangeTracker**nachverfolgt werden.

**StorageLibraryChangeTracker** funktioniert für Benutzer Bibliotheken oder für alle Ordner auf dem lokalen Computer. Dazu zählen, sekundäre Laufwerke oder Wechseldatenträger zu verwenden, aber enthält keine NAS-Laufwerke und Netzwerklaufwerke.

## <a name="using-the-change-tracker"></a>Verwenden die Änderung tracker

Die Änderung Tracker wird als ein kreisförmiges Puffer Speichern der letzten *N* Dateisystemvorgänge auf System implementiert. Apps, lesen die Änderungen auf den Puffer und verarbeiten sie in ihre eigenen Funktionen können. Wenn Sie die app mit den Änderungen fertig sind, sie die Änderungen als verarbeitet gekennzeichnet und nie, sie erneut angezeigt werden.

Um die Tracker Änderung für einen Ordner zu verwenden, gehen Sie folgendermaßen vor:

1. Aktivieren Sie das Änderungsprotokoll für den Ordner.
2. Warten Sie auf Änderungen.
3. Lesen Sie die Änderungen.
4. Akzeptieren Sie die Änderungen.

In den nächsten Abschnitten werden durch die einzelnen Schritte für einige Codebeispiele geführt. Das vollständige Codebeispiel wird am Ende des Artikels bereitgestellt.

### <a name="enable-the-change-tracker"></a>Aktivieren Sie die Änderung tracker

Als erstes, die die app muss ist auf dem System mitzuteilen, dass er eine angegebene Bibliothek im Änderungsprotokoll interessiert ist. Dies geschieht durch Aufrufen der Methode [Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) auf die Änderung Tracker für die Bibliothek von Interesse sind.

```csharp
StorageLibrary videosLib = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
StorageLibraryChangeTracker videoTracker = videosLib.ChangeTracker;
videoTracker.Enable();
```

Einige wichtige Hinweise:

- Stellen Sie sicher, dass Ihre app über die Berechtigung zur richtigen Bibliothek im Manifest verfügt, vor dem Erstellen des [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) -Objekts. Weitere Informationen finden Sie in [Den Dateizugriff](https://docs.microsoft.com/en-us/windows/uwp/files/file-access-permissions) .
- [Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) ist threadsicher, den Zeiger wird nicht zurückgesetzt und so oft wie (mehr dazu später) aufgerufen werden kann.

![Aktivieren eine leere Änderung tracker](images/changetracker-enable.png)

### <a name="wait-for-changes"></a>Warten Sie, bis Änderungen

Nachdem die Änderung Tracker initialisiert wurde, beginnt es aller Vorgänge aufzeichnen, die in einer Bibliothek auch auftreten, während die app nicht ausgeführt wird. Apps können registrieren, um zu einem beliebigen Zeitpunkt aktiviert werden, die durch die Registrierung für das Ereignis [StorageLibraryChangedTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.StorageLibraryContentChangedTrigger) geändert wird.

![Änderungen, die Änderung Tracker hinzugefügt wird, ohne dass die app zu lesen](images/changetracker-waiting.png)

### <a name="read-the-changes"></a>Lesen Sie die Änderungen

Die app kann dann Abfragen, ändert sich von der Änderung Tracker und erhalten eine Liste der Änderungen seit dem letzten ausgecheckt. Der folgende Code veranschaulicht das Abrufen einer Liste von Änderungen von Tracker ändern.

```csharp
StorageLibrary videosLibrary = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
videosLibrary.ChangeTracker.Enable();
StorageLibraryChangeReader videoChangeReader = videosLibrary.ChangeTracker.GetChangeReader();
IReadOnlyList changeSet = await changeReader.ReadBatchAsync();
```

Die app ist verantwortlich für die Verarbeitung von Änderungen in eine eigene Benutzeroberfläche oder eine Datenbank nach Bedarf.

![Lesen Sie die Änderungen aus der Änderung Tracker in eine app-Datenbank](images/changetracker-reading.png)

> [!TIP]
> Der zweite Aufruf zu ist Verteidigung gegen eine Racebedingung, wenn der Benutzer einen anderen Ordner zur Bibliothek hinzufügt, während Ihre app Änderungen gelesen wird. Ohne die zusätzlichen Aufruf zum **Aktivieren** fehl der Code mit EcSearchFolderScopeViolation (0 x 80070490), wenn der Benutzer die Ordner in ihrer Bibliothek geändert wird

### <a name="accept-the-changes"></a>Akzeptieren Sie die Änderung

Nach Abschluss die app verarbeitet die Änderungen, sollten sie über den das System nicht diese Änderungen werden mehr durch Aufrufen der Methode [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync) angezeigt.

```csharp
await changeReader.AcceptChangesAsync();
```

![Markieren Änderungen als lesen, damit sie erneut nie angezeigt werden](images/changetracker-accepting.png)

Die app jetzt erhalten nur neue Änderungen beim Tracker Änderung in der Zukunft zu lesen.

- Wenn Änderungen zwischen aufruft, [ReadBatchAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.readbatchasync) und [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync)geschehen, kann der Zeiger wird nur auf die letzte Änderung die app angezeigt wurde erweitert werden. Diese anderen Änderungen ist weiterhin verfügbar das nächste Mal **ReadBatchAsync ruft**.
- Akzeptieren die Änderungen nicht bewirkt, dass das System den gleichen Satz von Änderungen das nächste Mal zurück, das die app **ReadBatchAsync**aufruft.

## <a name="important-things-to-remember"></a>Wichtige Dinge zu beachten

Wenn Sie die Änderung Tracker verwenden, gibt es einige Dinge, die Sie bedenken sollten sicherstellen, dass alles ordnungsgemäß funktioniert.

### <a name="buffer-overruns"></a>Pufferüberläufe

Obwohl wir versuchen, reservieren Sie ausreichend Platz in Tracker ändern, halten Sie die Vorgänge, die auf dem System ausgeführt werden, bis Ihre app gelesen werden kann, ist es sehr einfach, ein Szenario sich vorzustellen, an dem die app die Änderungen Lesen nicht, bevor der kreisförmige Puffer selbst überschreibt. Insbesondere dann, wenn der Benutzer und die Daten aus einer Sicherung wiederhergestellt oder eine große Sammlung von Bildern auf dem Handy Kamera Synchronisierung.

In diesem Fall wird **ReadBatchAsync** den Fehlercode [StorageLibraryChangeType.ChangeTrackingLost](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetype)zurück. Wenn Ihre app dieser Fehlercode empfängt, bedeutet dies ein paar Dinge:

* Der Puffer hat selbst seit dem letzten überschrieben, die Sie besprochen. Die beste Vorgehensweise ist für die Bibliothek erneut, da alle Informationen aus der Tracker möglicherweise nicht vollständig.
* Die Änderung Tracker wird erst [zurücksetzen aufrufen](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.reset)weitere Änderungen zurückgegeben. Nachdem die app zurücksetzen aufruft, wird der Zeiger verschoben werden, um die letzte Änderung und Tracking normal fortgesetzt.

Es seltenen Fällen abrufen, jedoch in Szenarien, in denen der Benutzer eine große Anzahl von Dateien auf ihrer Festplatte verschoben wird, nicht wir die Änderung Tracker Sprechblase und zu viel Speicher belegen sollten. Sollte apps auf massive Dateisystemvorgänge reagieren, während die Kundenzufriedenheit in Windows nicht beschädigt werden können.

### <a name="changes-to-a-storagelibrary"></a>Änderungen an einer StorageLibrary

Die [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) -Klasse, die als Root-Ordner, die anderen Ordner enthalten eine virtuelle Gruppe vorhanden ist. Um dies zu einem Datei System ändern Tracker abzugleichen, haben wir die folgenden Optionen:

- Alle Änderungen an der Stamm-Bibliotheksordner absteigende werden in der Änderung Tracker dargestellt werden. Die Bibliothek Stammordner können mithilfe der Eigenschaft [Ordner](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) gefunden werden.
- Hinzufügen oder Entfernen von Stammordner aus einer **StorageLibrary** (über [RequestAddFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestaddfolderasync) und [RequestRemoveFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestremovefolderasync)) wird keinen Eintrag in der Änderung Tracker erstellen. Diese Änderungen können über das Ereignis [DefinitionChanged](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.definitionchanged) oder durch die Enumeration der Stammordner in der Bibliothek, die mithilfe der Eigenschaft [Ordner](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) überwacht werden.
- Wenn Sie ein Ordner mit Inhalte bereits in der Bibliothek hinzugefügt wird, kann es keine Änderung der Benachrichtigung oder ändern Einträge generiert. Alle nachfolgenden Änderungen auf die Nachfolgerelemente dieses Ordners Benachrichtigungen generiert und Einträge zu ändern.

### <a name="calling-the-enable-method"></a>Aufrufen der Methode aktivieren

Apps dürfen [Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) aufrufen, als das Dateisystem tracking start und vor jedem Aufzählung von Änderungen. Dadurch wird sichergestellt, dass alle Änderungen durch die Änderung Tracker aufgenommen werden.  

## <a name="putting-it-together"></a>Letzte Schritte

Hier wurde der gesamte Code, der verwendet wird, ändert sich der von der Videobibliothek registrieren und starten die vom Änderung Tracker abrufen, die Änderungen.

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
