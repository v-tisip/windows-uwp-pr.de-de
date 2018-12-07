---
Description: Learn how to pin secondary tiles to taskbar.
title: Sekundäre Kacheln an Taskleiste anheften
label: Pin secondary tiles to taskbar
template: detail.hbs
ms.date: 11/28/2018
ms.topic: article
keywords: Windows 10, Uwp, an die sekundäre Kachel-Taskleiste anheften sekundäre Kacheln an Taskleiste anheften Kontextmenü
ms.localizationpriority: medium
ms.openlocfilehash: 7ad322fe371b0e1f3605ffb4c29108a15bb28e0c
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8779507"
---
# <a name="pin-secondary-tiles-to-taskbar"></a>Sekundäre Kacheln an Taskleiste anheften

Genau wie sekundäre Kacheln an die Startseite anheften können Sie sekundäre Kacheln an die Taskleiste anheften, die Ihre Benutzer schnellen Zugriff auf Inhalte in Ihrer app.

<img alt="Taskbar pinning" src="../images/taskbar/pin-secondary-ui.png" width="972"/>

> [!IMPORTANT]
> **Eingeschränkte Access-API**: Diese API ist ein Feature eingeschränkten Zugriff. Um diese API verwenden möchten, wenden Sie sich an [taskbarsecondarytile@microsoft.com](mailto:taskbarsecondarytile@microsoft.com?Subject=Limited%20Access%20permission%20to%20use%20secondary%20tiles%20on%20taskbar).

> **Erfordert Oktober 2018 Update**: Sie müssen als Ziel SDK 17763 und Build 17763 oder höher ausführen, um an Taskleiste anheften.


## <a name="guidance"></a>Anleitung

Eine sekundäre Kachel stellt eine einheitliche und effiziente Möglichkeit für Benutzer, direkt auf bestimmte Bereiche innerhalb einer app zuzugreifen. Auch wenn ein Benutzer an, ob Sie "eine sekundäre Kachel an die Taskleiste anheften", werden die anheftbereiche einer app vom Entwickler bestimmt. Weitere Informationen finden Sie in der [Anleitung für sekundäre Kacheln](secondary-tiles-guidance.md).


## <a name="1-determine-if-api-exists-and-unlock-limited-access"></a>1. zu ermitteln Sie, ob die API vorhanden ist und entsperren Sie eingeschränktem Zugriff

Ältere Geräte müssen nicht die Taskleiste anheften APIs (Wenn Sie ältere Versionen von Windows 10 ausrichten). Aus diesem Grund sollten nicht Sie eine Pin-Schaltfläche auf diesen Geräten anzeigen, die nicht angeheftet werden kann.

Darüber hinaus ist dieses Feature unter eingeschränktem Zugriff gesperrt. Wenden Sie sich an Microsoft, um Zugriff zu erhalten. API-Aufrufe an **[TaskbarManager.RequestPinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.requestpinsecondarytileasync#Windows_UI_Shell_TaskbarManager_RequestPinSecondaryTileAsync_Windows_UI_StartScreen_SecondaryTile_)**, **[TaskbarManager.IsSecondaryTilePinnedAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.issecondarytilepinnedasync)** und **[TaskbarManager.TryUnpinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.tryunpinsecondarytileasync)** tritt mit Ausnahme der Zugriff verweigert. Apps dürfen nicht ohne Genehmigung-API verwenden, und die API-Definition kann jederzeit ändern.

Verwenden Sie die [ApiInformation.IsMethodPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation.ismethodpresent#Windows_Foundation_Metadata_ApiInformation_IsMethodPresent_System_String_System_String_) -Methode, um festzustellen, ob die APIs vorhanden sind. Und verwenden Sie die **[LimitedAccessFeatures](https://docs.microsoft.com/uwp/api/windows.applicationmodel.limitedaccessfeatures)** API, die API entsperren.

```csharp
if (ApiInformation.IsMethodPresent("Windows.UI.Shell.TaskbarManager", "RequestPinSecondaryTileAsync"))
{
    // API present!
    // Unlock the pin to taskbar feature
    var result = LimitedAccessFeatures.TryUnlockFeature(
        "com.microsoft.windows.secondarytilemanagement",
        "<tokenFromMicrosoft>",
        "<publisher> has registered their use of com.microsoft.windows.secondarytilemanagement with Microsoft and agrees to the terms of use.");

    // If unlock succeeded
    if ((result.Status == LimitedAccessFeatureStatus.Available) ||
        (result.Status == LimitedAccessFeatureStatus.AvailableWithoutToken))
    {
        // Continue
    }
    else
    {
        // Don't show pin to taskbar button or call any of the below APIs
    }
}

else
{
    // Don't show pin to taskbar button or call any of the below APIs
}
```


## <a name="2-get-the-taskbarmanager-instance"></a>2. Rufen Sie die TaskbarManager-Instanz

UWP-Apps können auf einer Vielzahl von Geräten ausgeführt werden. Nicht alle Geräte unterstützen die Taskleiste. Derzeit unterstützen nur Desktop-Geräte die Taskleiste. Darüber hinaus kann Vorhandensein der Taskleiste stammen, und wechseln Sie. Um zu überprüfen, ob die Taskleiste derzeit vorhanden ist, rufen Sie die Methode **[TaskbarManager.GetDefault](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.getdefault)** und überprüfen Sie, dass die zurückgegebene Instanz ist nicht null. Eine Pin-Schaltfläche nicht angezeigt werden, wenn die Taskleiste nicht vorhanden ist.

Es wird empfohlen, halten an die Instanz für die Dauer der einem einzigen Vorgang, z. B. anheften, und klicken Sie dann das nächste Mal, das Sie ein anderer Vorgang müssen dafür eine neue Instanz.

```csharp
TaskbarManager taskbarManager = TaskbarManager.GetDefault();

if (taskbarManager != null)
{
    // Continue
}
else
{
    // Taskbar not present, don't display a pin button
}
```


## <a name="3-check-whether-your-tile-is-currently-pinned-to-the-taskbar"></a>3. Überprüfen Sie, ob die Kachel derzeit an die Taskleiste angeheftet ist

Wenn die Kachel bereits angeheftet ist, sollten Sie stattdessen eine Schaltfläche "lösen" angezeigt. Sie können die **[IsSecondaryTilePinnedAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.issecondarytilepinnedasync)** -Methode überprüfen, ob die Kachel derzeit angeheftet ist (Benutzer können lösen sie zu einem beliebigen Zeitpunkt). In dieser Methode übergeben Sie die Kachel, die Sie wissen möchten, der **TileId** angeheftet ist.

```csharp
if (await taskbarManager.IsSecondaryTilePinnedAsync("myTileId"))
{
    // The tile is already pinned. Display the unpin button.
}

else 
{
    // The tile is not pinned. Display the pin button.
}
```


## <a name="4-check-whether-pinning-is-allowed"></a>4. Überprüfen Sie, ob anheften zulässig ist.

An die Taskleiste anheften kann durch eine Gruppenrichtlinie deaktiviert werden. Die [TaskbarManager.IsPinningAllowed](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.ispinningallowed) -Eigenschaft können Sie überprüfen, ob ein anheften zugelassen wird.

Wenn der Benutzer die Pin-Schaltfläche klickt, sollten Sie diese Eigenschaft überprüfen, und wenn "false" ist, sollten kein informiert den Benutzer, den zum Anheften von auf diesem Computer nicht zulässig ist über Dialogfeld anzeigen.

```csharp
TaskbarManager taskbarManager = TaskbarManager.GetDefault();
if (taskbarManager == null)
{
    // Display message dialog informing user that taskbar is no longer present, and then hide the button
}

else if (taskbarManager.IsPinningAllowed == false)
{
    // Display message dialog informing user pinning is not allowed on this machine
}

else
{
    // Continue pinning
}
```


## <a name="5-construct-and-pin-your-tile"></a>5. erstellen und anheften der Kachel

Der Benutzer die Pin-Schaltfläche geklickt hat, und festgestellt haben, dass die APIs vorhanden sind, Taskleiste vorhanden ist und anheften ist die erforderliche Berechtigung bis zum Anheften!

Erstellen Sie zuerst die sekundäre Kachel, ebenso wie bei an das Startmenü angeheftet. Erfahren Sie mehr über die sekundäre Kachel-Eigenschaften, lesen Sie [Sekundäre Kacheln an die Startseite anheften](secondary-tiles-pinning.md). Allerdings ist beim anheften an Taskleiste, zusätzlich zu den zuvor erforderlichen Eigenschaften Square44x44Logo (Dies ist das Logo, die von der Taskleiste verwendet) auch erforderlich. Andernfalls wird eine Ausnahme ausgelöst.

Anschließend übergeben Sie die Kachel an die **[RequestPinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.requestpinsecondarytileasync)** -Methode. Da dies unter Zugriff begrenzt ist, dies kein Bestätigungsdialogfeld angezeigt, und es wird einen UI-Thread ist nicht erforderlich. Aber in Zukunft beim dies öffnen Sie über Zugriff, Aufrufer nicht mit eingeschränktem Zugriff erhält ein Dialogfeld und erforderlich, um den UI-Thread verwenden werden.

```csharp
// Initialize the tile (all properties below are required)
SecondaryTile tile = new SecondaryTile("myTileId");
tile.DisplayName = "PowerPoint 2016 (Remote)";
tile.Arguments = "app=powerpoint";
tile.VisualElements.Square44x44Logo = new Uri("ms-appdata:///AppIcons/PowerPoint_Square44x44Logo.png");
tile.VisualElements.Square150x150Logo = new Uri("ms-appdata:///AppIcons/PowerPoint_Square150x150Logo.png");

// Pin it to the taskbar
bool isPinned = await taskbarManager.RequestPinSecondaryTileAsync(tile);
```

Diese Methode gibt einen booleschen Wert, der angibt, ob die Kachel jetzt an die Taskleiste angeheftet ist. Wenn die Kachel bereits angeheftet war, wird die Methode aktualisiert den vorhandene Kachel und gibt true zurück. Anheften war nicht zulässig oder Taskleiste wird nicht unterstützt, gibt die Methode "false".


## <a name="enumerate-tiles"></a>Auflisten von Kacheln

Um alle Kacheln anzuzeigen, die Sie erstellt haben und weiterhin an einer beliebigen Stelle angeheftet verwenden (Start, Taskleiste oder beides), **[FindAllAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.findallasync)**. Sie können anschließend überprüfen, ob diese Kacheln auf der Taskleiste bzw. die Startseite angeheftet werden. Wenn die Oberfläche nicht unterstützt wird, geben diese Methoden false zurück.

```csharp
var taskbarManager = TaskbarManager.GetDefault();
var startScreenManager = StartScreenManager.GetDefault();

// Look through all tiles
foreach (SecondaryTile tile in await SecondaryTile.FindAllAsync())
{
    if (taskbarManager != null && await taskbarManager.IsSecondaryTilePinnedAsync(tile.TileId))
    {
        // Tile is pinned to the taskbar
    }

    if (startScreenManager != null && await startScreenManager.ContainsSecondaryTileAsync(tile.TileId))
    {
        // Tile is pinned to Start
    }
}
```


## <a name="update-a-tile"></a>Aktualisieren von Kacheln

Um eine bereits angeheftete Kachel zu aktualisieren, können Sie die Methode [**SecondaryTile.UpdateAsync**](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.updateasync) verwenden, wie in [einer sekundären Kachel aktualisieren](secondary-tiles-pinning.md#updating-a-secondary-tile)beschrieben.


## <a name="unpin-a-tile"></a>Lösen Sie eine Kachel

Ihre app sollte eine Schaltfläche "lösen" angeben, ob die Kachel derzeit angeheftet ist. Um die Kachel zu lösen, rufen Sie einfach **[TryUnpinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.tryunpinsecondarytileasync)**, und übergeben Sie die **TileId** die sekundäre Kachel gewünschte gelöst hat.

Diese Methode gibt einen booleschen Wert, der angibt, ob die Kachel nicht mehr an die Taskleiste angeheftet ist. Wenn in erster Linie die Kachel angeheftet wurde nicht, zurück dies auch "true". Wenn lösen zugelassen wurde nicht, wird Sie dies "false" zurückgegeben.

Wenn die Kachel nur an Taskleiste angeheftet wurde, wird dies die Kachel gelöscht werden, da es nicht mehr an einer beliebigen Stelle angeheftet ist.

```csharp
var taskbarManager = TaskbarManager.GetDefault();
if (taskbarManager != null)
{
    bool isUnpinned = await taskbarManager.TryUnpinSecondaryTileAsync("myTileId");
}
```


## <a name="delete-a-tile"></a>Löschen Sie eine Kachel

Wenn Sie eine Kachel von überall (Start, Taskleiste) lösen möchten, verwenden Sie die **[RequestDeleteAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.requestdeleteasync)** -Methode.

Dies eignet sich für Fälle, in denen die Inhalte der Benutzer angeheftet nicht mehr anwendbar ist. Beispielsweise sollten Ihrer app können Sie ein Notizbuch Startmenü und Taskleiste anheften und dann der Benutzer das Notizbuch löscht, Sie einfach das Notizbuch zugeordnete Kachel löschen.

```csharp
// Initialize a secondary tile with the same tile ID you want removed.
// Or, locate it with FindAllAsync()
SecondaryTile toBeDeleted = new SecondaryTile(tileId);

// And then delete the tile
await toBeDeleted.RequestDeleteAsync();
```


## <a name="unpin-only-from-start"></a>Lösen Sie nur auf dem Startbildschirm

Wenn Sie nur eine sekundäre Kachel auf der Startseite, ohne dass es auf der Taskleiste lösen möchten, können Sie die **[StartScreenManager.TryRemoveSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager.tryremovesecondarytileasync)** -Methode aufrufen. Dadurch werden die Kachel auf ähnliche Weise gelöscht, wenn es nicht mehr für alle anderen Oberflächen angeheftet ist.

Diese Methode gibt einen booleschen Wert, der angibt, ob die Kachel nicht mehr an die Startseite angeheftet ist. Wenn in erster Linie die Kachel angeheftet wurde nicht, zurück dies auch "true". Wenn lösen war nicht zulässig oder Start wird nicht unterstützt, zurückgegeben "false".

```csharp
await StartScreenManager.GetDefault().TryRemoveSecondaryTileAsync("myTileId");
```


## <a name="resources"></a>Ressourcen

* [TaskbarManager-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager)
* [Sekundäre Kacheln an die Startseite anheften](secondary-tiles-pinning.md)