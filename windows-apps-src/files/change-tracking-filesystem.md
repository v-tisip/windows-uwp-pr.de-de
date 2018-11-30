---
title: Datei systemänderungen im Hintergrund nachverfolgen
description: Beschreibt, wie Sie die Änderungen in Dateien und Ordner im Hintergrund nachverfolgt, wenn Benutzer das System bewegen.
ms.date: 11/20/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: e90692753924572a932767b9c188ed6d24f94593
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8202257"
---
# <a name="track-file-system-changes-in-the-background"></a>Datei systemänderungen im Hintergrund nachverfolgen

Die [StorageLibraryChangeTracker](https://docs.microsoft.com/uwp/api/Windows.Storage.StorageLibraryChangeTracker) -Klasse ermöglicht apps das Nachverfolgen der Änderungen in Dateien und Ordner, wenn Benutzer das System bewegen. Mit der **StorageLibraryChangeTracker** -Klasse, kann eine app nachverfolgt werden:

- Datei-Operationen u. a. hinzufügen, löschen, ändern.
- Ordner Vorgänge wie z. B. umbenennen und löschen.
- Dateien und Ordner auf dem Laufwerk verschieben.

Verwenden Sie dieses Handbuch erfahren, das Programing Modell für die Arbeit mit der Änderung Tracker, einige Codebeispiele zeigen und Verstehen der unterschiedlichen Arten von Dateien, die durch **StorageLibraryChangeTracker**nachverfolgt werden.

**StorageLibraryChangeTracker** funktioniert für Benutzer Bibliotheken oder für alle Ordner auf dem lokalen Computer. Dazu zählen sekundären Laufwerke oder Wechseldatenträger zu verwenden, aber enthält keine NAS-Laufwerke und Netzlaufwerke.

## <a name="using-the-change-tracker"></a>Verwenden den Änderung tracker

Der Änderung Tracker wird als ein kreisförmiges Puffer Speichern der letzten *N* Dateisystemvorgänge auf System implementiert. Apps können die Änderungen aus dem Puffer lesen und verarbeiten sie in ihre eigenen Funktionen zur Verfügung. Wenn die app mit den Änderungen abgeschlossen ist, es werden die Änderungen als verarbeitet gekennzeichnet und nie, sie erneut angezeigt werden.

Um die Tracker Änderung für einen Ordner zu verwenden, gehen Sie folgendermaßen vor:

1. Aktivieren Sie Änderungsprotokoll für den Ordner.
2. Warten Sie auf Änderungen.
3. Lesen Sie Änderungen an.
4. Akzeptieren Sie Änderungen an.

In den nächsten Abschnitten werden durch die einzelnen Schritte für einige Codebeispiele geführt. Das vollständige Codebeispiel wird am Ende des Artikels bereitgestellt.

### <a name="enable-the-change-tracker"></a>Aktivieren Sie den Änderung tracker

Der erste Schritt, der die app muss ist, um dem System mitzuteilen, dass er eine angegebene Bibliothek im Änderungsprotokoll interessiert ist. Dies geschieht durch Aufrufen von der Methode [Aktivieren Sie](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) auf die Änderung Tracker für die Bibliothek von Interesse sind.

```csharp
StorageLibrary videosLib = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
StorageLibraryChangeTracker videoTracker = videosLib.ChangeTracker;
videoTracker.Enable();
```

Einige wichtige Hinweise:

- Stellen Sie sicher, dass Ihre app berechtigt zur richtigen Bibliothek im Manifest vor dem Erstellen des [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) -Objekts. Weitere Informationen finden Sie in der [Berechtigungen für den Dateizugriff](https://docs.microsoft.com/en-us/windows/uwp/files/file-access-permissions) .
- [Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) ist threadsicher, den Zeiger wird nicht zurückgesetzt und so oft wie (mehr dazu später gewünscht) aufgerufen werden kann.

![Aktivieren eine leere Änderung tracker](images/changetracker-enable.png)

### <a name="wait-for-changes"></a>Warten Sie, bis Änderungen

Nachdem der Änderung Tracker initialisiert wurde, beginnt dieser aller Vorgänge aufzeichnen, die in einer Bibliothek auch auftreten, während die app nicht ausgeführt wird. Apps können registrieren, um jederzeit aktiviert, wenn eine Änderung durch die Registrierung für das Ereignis [StorageLibraryChangedTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.StorageLibraryContentChangedTrigger) vorliegt.

![Änderungen, die Änderung Tracker hinzugefügt wird, ohne dass die app zu lesen](images/changetracker-waiting.png)

### <a name="read-the-changes"></a>Lesen Sie die Änderungen

Die app kann dann Abfragen, ändert sich von der Änderung Tracker und erhalten eine Liste der Änderungen seit dem letzten ausgecheckt. Der folgende Code zeigt, wie eine Liste von Änderungen aus der Änderung Tracker abrufen.

```csharp
StorageLibrary videosLibrary = await StorageLibrary.GetLibraryAsync(KnownLibraryId.Videos);
videosLibrary.ChangeTracker.Enable();
StorageLibraryChangeReader videoChangeReader = videosLibrary.ChangeTracker.GetChangeReader();
IReadOnlyList changeSet = await changeReader.ReadBatchAsync();
```

Die app ist verantwortlich für die Verarbeitung der Änderungen in eine eigene Benutzeroberfläche oder eine Datenbank je nach Bedarf.

![Lesen Sie die Änderungen aus der Änderung Tracker in eine app-Datenbank](images/changetracker-reading.png)

> [!TIP]
> Der zweite Aufruf von aktivieren ist zur Verteidigung gegen eine Racebedingung, wenn der Benutzer einen anderen Ordner zur Bibliothek hinzufügt, während Ihre app Änderungen gelesen wird. Ohne die zusätzlichen Aufruf zum **Aktivieren** fehl der Code mit EcSearchFolderScopeViolation (0 x 80070490) Wenn der Benutzer die Ordner in ihrer Bibliothek ändert

### <a name="accept-the-changes"></a>Akzeptieren Sie die Änderung

Nach Abschluss die app verarbeiten die Änderungen, sollten sie das System nicht diese Änderungen erneut angezeigt werden durch Aufrufen der Methode [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync) erkennen.

```csharp
await changeReader.AcceptChangesAsync();
```

![Markieren von Änderungen als lesen, damit er erneut nie angezeigt werden](images/changetracker-accepting.png)

Die app jetzt erhalten nur neue Änderungen beim Tracker Änderung in der Zukunft zu lesen.

- Wenn Änderungen zwischen aufruft, [ReadBatchAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.readbatchasync) und [AcceptChangesAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangereader.acceptchangesasync)geschehen, kann der Zeiger wird nur auf die letzte Änderung die app angezeigt wurde erweitert werden. Diese anderen Änderungen ist weiterhin verfügbar das nächste Mal **ReadBatchAsync**aufgerufen.
- Die Änderungen nicht akzeptieren, wird das System den gleichen Satz von Änderungen das nächste Mal zurückgeben, das die app **ReadBatchAsync**aufruft.

## <a name="important-things-to-remember"></a>Wichtige Dinge zu beachten

Wenn Sie den Änderung Tracker verwenden zu können, stehen einige Dinge, die Sie bedenken sollten sicherstellen, dass alles ordnungsgemäß funktioniert.

### <a name="buffer-overruns"></a>Pufferüberläufe

Obwohl wir versuchen, reservieren Sie ausreichend Platz in der Änderung Tracker enthalten alle Vorgänge, die auf dem System ausgeführt werden, bis Ihre app gelesen werden kann, ist es sehr einfach, ein Szenario vorstellen, an dem die app die Änderungen Lesen nicht, bevor der kreisförmige Puffer selbst überschreibt. Insbesondere dann, wenn der Benutzer Wiederherstellen von Daten aus einer Sicherung oder eine große Sammlung von Bildern von ihrem Handy synchronisieren.

In diesem Fall wird **ReadBatchAsync** den Fehlercode [StorageLibraryChangeType.ChangeTrackingLost](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetype)zurück. Wenn Ihre app dieser Fehlercode empfängt, bedeutet dies ein paar Dinge:

* Der Puffer hat sich selbst seit dem letzten überschrieben angezeigten es. Die beste Vorgehensweise ist für die Bibliothek erneut, da alle Informationen aus der Tracker möglicherweise nicht vollständig.
* Der Änderung Tracker wird erst Sie [Zurücksetzen rufen](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.reset)weitere Änderungen zurückgegeben. Nachdem die app zurücksetzen aufgerufen hat, der Zeiger wird in der letzten Änderung verschoben werden und Tracking normal fortgesetzt.

Es sollte seltenen Fällen abgerufen werden, in Szenarien, in denen der Benutzer eine große Anzahl von Dateien auf ihrer Festplatte verschoben wird, soll jedoch nicht den Änderung Tracker Sprechblase und zu viel Speicher belegen. Sollte apps auf massive Dateisystemvorgänge reagieren, während die Kundenzufriedenheit in Windows nicht beschädigt werden können.

### <a name="changes-to-a-storagelibrary"></a>Änderungen an einem StorageLibrary

Die [StorageLibrary](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary) -Klasse, die als virtuelle Gruppe von Root-Ordner, die anderen Ordner enthalten vorhanden ist. Um dies zu einem Datei System ändern Tracker abzugleichen, haben wir die folgenden Optionen aus:

- Jegliche Änderungen an der Stamm-Bibliotheksordner absteigende werden in der Änderung Tracker dargestellt werden. Die Bibliothek Stammordner können mithilfe der Eigenschaft [Ordner](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) gefunden werden.
- Hinzufügen oder Entfernen von Stammordner aus einer **StorageLibrary** (über [RequestAddFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestaddfolderasync) und [RequestRemoveFolderAsync](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.requestremovefolderasync)) wird keinen Eintrag in der Änderung Tracker erstellen. Diese Änderungen können über das Ereignis [DefinitionChanged](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.definitionchanged) oder durch die Enumeration der Stammordner in der Bibliothek mithilfe der Eigenschaft [Ordner](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrary.folders) überwacht werden.
- Wenn ein Ordner mit Inhalt bereits zur Bibliothek hinzugefügt wird, kann es keine Änderung Benachrichtigung oder Änderung Einträge generiert. Alle nachfolgenden Änderungen auf die Nachfolgerelemente dieses Ordners Benachrichtigungen generiert und Einträge zu ändern.

### <a name="calling-the-enable-method"></a>Aufrufen der Methode aktivieren

Apps dürfen [Aktivieren](https://docs.microsoft.com/uwp/api/windows.storage.storagelibrarychangetracker.enable) aufrufen, sobald sie Starten des Dateisystems nachverfolgen und vor jeder Aufzählung von Änderungen. Dadurch wird sichergestellt, dass alle Änderungen durch die Änderung Tracker aufgenommen werden.  

## <a name="putting-it-together"></a>Letzte Schritte

Hier ist der Code, der verwendet wird, ändert sich der von der Videobibliothek registrieren und Starten vom Änderung Tracker abrufen, die Änderungen.

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
