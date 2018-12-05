---
Description: Learn how to pin secondary tiles to taskbar.
title: Sekundäre Kacheln an Taskleiste anheften
label: Pin secondary tiles to taskbar
template: detail.hbs
ms.date: 11/28/2018
ms.topic: article
keywords: Windows 10, Uwp, an die sekundäre Kachel-Taskleiste anheften, sekundäre Kacheln an Taskleiste anheften Kontextmenü
ms.localizationpriority: medium
ms.openlocfilehash: 7ad322fe371b0e1f3605ffb4c29108a15bb28e0c
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8733381"
---
# <a name="pin-secondary-tiles-to-taskbar"></a><span data-ttu-id="2fb80-103">Sekundäre Kacheln an Taskleiste anheften</span><span class="sxs-lookup"><span data-stu-id="2fb80-103">Pin secondary tiles to taskbar</span></span>

<span data-ttu-id="2fb80-104">Genau wie sekundäre Kacheln an die Startseite anheften, können Sie sekundäre Kacheln an die Taskleiste anheften, die Ihre Benutzer schnellen Zugriff auf Inhalte in Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="2fb80-104">Just like pinning secondary tiles to Start, you can pin secondary tiles to the taskbar, giving your users quick access to content within your app.</span></span>

<img alt="Taskbar pinning" src="../images/taskbar/pin-secondary-ui.png" width="972"/>

> [!IMPORTANT]
> <span data-ttu-id="2fb80-105">**Begrenzte Access-API**: Diese API ist ein Feature eingeschränkten Zugriff.</span><span class="sxs-lookup"><span data-stu-id="2fb80-105">**Limited Access API**: This API is a limited access feature.</span></span> <span data-ttu-id="2fb80-106">Um diese API verwenden möchten, wenden Sie sich an [taskbarsecondarytile@microsoft.com](mailto:taskbarsecondarytile@microsoft.com?Subject=Limited%20Access%20permission%20to%20use%20secondary%20tiles%20on%20taskbar).</span><span class="sxs-lookup"><span data-stu-id="2fb80-106">To use this API, please contact [taskbarsecondarytile@microsoft.com](mailto:taskbarsecondarytile@microsoft.com?Subject=Limited%20Access%20permission%20to%20use%20secondary%20tiles%20on%20taskbar).</span></span>

> <span data-ttu-id="2fb80-107">**Erfordert Oktober 2018 Update**: Sie müssen als Ziel SDK 17763 und Build 17763 oder höher ausführen, um an Taskleiste anheften.</span><span class="sxs-lookup"><span data-stu-id="2fb80-107">**Requires October 2018 Update**: You must target SDK 17763 and be running build 17763 or higher to pin to taskbar.</span></span>


## <a name="guidance"></a><span data-ttu-id="2fb80-108">Anleitung</span><span class="sxs-lookup"><span data-stu-id="2fb80-108">Guidance</span></span>

<span data-ttu-id="2fb80-109">Eine sekundäre Kachel stellt eine einheitliche und effiziente Möglichkeit für Benutzer, direkt auf bestimmte Bereiche innerhalb einer app zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="2fb80-109">A secondary tile provides a consistent, efficient way for users to directly access specific areas within an app.</span></span> <span data-ttu-id="2fb80-110">Auch wenn ein Benutzer, ob er "eine sekundäre Kachel an die Taskleiste anheften" werden, die anheftbereiche einer app vom Entwickler vorgegeben.</span><span class="sxs-lookup"><span data-stu-id="2fb80-110">Although a user chooses whether or not to "pin" a secondary tile to the taskbar, the pinnable areas in an app are determined by the developer.</span></span> <span data-ttu-id="2fb80-111">Weitere Informationen finden Sie in der [Anleitung für sekundäre Kacheln](secondary-tiles-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="2fb80-111">For more guidance, see [Secondary tile guidance](secondary-tiles-guidance.md).</span></span>


## <a name="1-determine-if-api-exists-and-unlock-limited-access"></a><span data-ttu-id="2fb80-112">1. zu ermitteln Sie, ob die API vorhanden ist und entsperren Sie eingeschränktem Zugriff</span><span class="sxs-lookup"><span data-stu-id="2fb80-112">1. Determine if API exists and unlock Limited-Access</span></span>

<span data-ttu-id="2fb80-113">Ältere Geräte müssen nicht die Taskleiste anheften APIs (Wenn Sie mit ältere Versionen von Windows 10 ausrichten).</span><span class="sxs-lookup"><span data-stu-id="2fb80-113">Older devices don't have the taskbar pinning APIs (if you're targeting older versions of Windows 10).</span></span> <span data-ttu-id="2fb80-114">Aus diesem Grund sollten nicht Sie eine Pin-Schaltfläche auf diesen Geräten anzeigen, die nicht angeheftet werden kann.</span><span class="sxs-lookup"><span data-stu-id="2fb80-114">Therefore, you shouldn't display a pin button on these devices that aren't capable of pinning.</span></span>

<span data-ttu-id="2fb80-115">Darüber hinaus ist dieses Feature unter eingeschränktem Zugriff gesperrt.</span><span class="sxs-lookup"><span data-stu-id="2fb80-115">Additionally, this feature is locked under Limited-Access.</span></span> <span data-ttu-id="2fb80-116">Wenden Sie sich an Microsoft, um Zugriff zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2fb80-116">To gain access, contact Microsoft.</span></span> <span data-ttu-id="2fb80-117">API-Aufrufe an **[TaskbarManager.RequestPinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.requestpinsecondarytileasync#Windows_UI_Shell_TaskbarManager_RequestPinSecondaryTileAsync_Windows_UI_StartScreen_SecondaryTile_)**, **[TaskbarManager.IsSecondaryTilePinnedAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.issecondarytilepinnedasync)** und **[TaskbarManager.TryUnpinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.tryunpinsecondarytileasync)** fehl mit Ausnahme der Zugriff verweigert.</span><span class="sxs-lookup"><span data-stu-id="2fb80-117">API calls to **[TaskbarManager.RequestPinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.requestpinsecondarytileasync#Windows_UI_Shell_TaskbarManager_RequestPinSecondaryTileAsync_Windows_UI_StartScreen_SecondaryTile_)**, **[TaskbarManager.IsSecondaryTilePinnedAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.issecondarytilepinnedasync)**, and **[TaskbarManager.TryUnpinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.tryunpinsecondarytileasync)** will fail with an Access Denied exception.</span></span> <span data-ttu-id="2fb80-118">Apps dürfen keine Verwendung dieser API ohne Genehmigung und die API-Definition kann jederzeit ändern.</span><span class="sxs-lookup"><span data-stu-id="2fb80-118">Apps are not allowed to use this API without permission, and the API definition may change at any time.</span></span>

<span data-ttu-id="2fb80-119">Verwenden Sie die [ApiInformation.IsMethodPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation.ismethodpresent#Windows_Foundation_Metadata_ApiInformation_IsMethodPresent_System_String_System_String_) -Methode, um festzustellen, ob die APIs vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="2fb80-119">Use the [ApiInformation.IsMethodPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation.ismethodpresent#Windows_Foundation_Metadata_ApiInformation_IsMethodPresent_System_String_System_String_) method to determine if the APIs are present.</span></span> <span data-ttu-id="2fb80-120">Und verwenden Sie die **[LimitedAccessFeatures](https://docs.microsoft.com/uwp/api/windows.applicationmodel.limitedaccessfeatures)** API, die API entsperren.</span><span class="sxs-lookup"><span data-stu-id="2fb80-120">And then use the **[LimitedAccessFeatures](https://docs.microsoft.com/uwp/api/windows.applicationmodel.limitedaccessfeatures)** API to try unlocking the API.</span></span>

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


## <a name="2-get-the-taskbarmanager-instance"></a><span data-ttu-id="2fb80-121">2. Rufen Sie die TaskbarManager-Instanz</span><span class="sxs-lookup"><span data-stu-id="2fb80-121">2. Get the TaskbarManager instance</span></span>

<span data-ttu-id="2fb80-122">UWP-Apps können auf einer Vielzahl von Geräten ausgeführt werden. Nicht alle Geräte unterstützen die Taskleiste.</span><span class="sxs-lookup"><span data-stu-id="2fb80-122">UWP apps can run on a wide variety of devices; not all of them support the taskbar.</span></span> <span data-ttu-id="2fb80-123">Derzeit unterstützen nur Desktop-Geräte die Taskleiste.</span><span class="sxs-lookup"><span data-stu-id="2fb80-123">Right now, only Desktop devices support the taskbar.</span></span> <span data-ttu-id="2fb80-124">Darüber hinaus kann Vorhandensein der Taskleiste stammen, und wechseln Sie.</span><span class="sxs-lookup"><span data-stu-id="2fb80-124">Additionally, presence of the taskbar might come and go.</span></span> <span data-ttu-id="2fb80-125">Um zu überprüfen, ob die Taskleiste derzeit vorhanden ist, rufen Sie die Methode **[TaskbarManager.GetDefault](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.getdefault)** und überprüfen Sie, dass die zurückgegebene Instanz ist nicht null.</span><span class="sxs-lookup"><span data-stu-id="2fb80-125">To check whether taskbar is currently present, call the **[TaskbarManager.GetDefault](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.getdefault)** method and check that the instance returned is not null.</span></span> <span data-ttu-id="2fb80-126">Eine Pin-Schaltfläche nicht angezeigt werden, wenn die Taskleiste nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-126">Don't display a pin button if the taskbar isn't present.</span></span>

<span data-ttu-id="2fb80-127">Wir empfehlen Betrieb auf die Instanz für die Dauer der einem einzigen Vorgang, z. B. anheften, und klicken Sie dann das nächste Mal, das Sie ein anderer Vorgang müssen dafür eine neue Instanz.</span><span class="sxs-lookup"><span data-stu-id="2fb80-127">We recommend holding onto the instance for the duration of a single operation, like pinning, and then grabbing a new instance the next time you need to do another operation.</span></span>

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


## <a name="3-check-whether-your-tile-is-currently-pinned-to-the-taskbar"></a><span data-ttu-id="2fb80-128">3. Überprüfen Sie, ob die Kachel derzeit an die Taskleiste angeheftet ist</span><span class="sxs-lookup"><span data-stu-id="2fb80-128">3. Check whether your tile is currently pinned to the taskbar</span></span>

<span data-ttu-id="2fb80-129">Wenn die Kachel bereits angeheftet ist, sollten Sie stattdessen eine Schaltfläche "lösen" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2fb80-129">If your tile is already pinned, you should display an unpin button instead.</span></span> <span data-ttu-id="2fb80-130">Sie können die **[IsSecondaryTilePinnedAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.issecondarytilepinnedasync)** -Methode überprüfen, ob die Kachel derzeit angeheftet ist (Benutzer können lösen sie zu einem beliebigen Zeitpunkt).</span><span class="sxs-lookup"><span data-stu-id="2fb80-130">You can use the **[IsSecondaryTilePinnedAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.issecondarytilepinnedasync)** method to check whether your tile is currently pinned (users can unpin it at any time).</span></span> <span data-ttu-id="2fb80-131">In dieser Methode übergeben Sie die Kachel, die Sie wissen möchten, der **TileId** angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-131">In this method, you pass the **TileId** of the tile you want to know is pinned.</span></span>

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


## <a name="4-check-whether-pinning-is-allowed"></a><span data-ttu-id="2fb80-132">4. Überprüfen Sie, ob anheften zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-132">4. Check whether pinning is allowed</span></span>

<span data-ttu-id="2fb80-133">An die Taskleiste anheften kann durch eine Gruppenrichtlinie deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="2fb80-133">Pinning to the taskbar can be disabled by Group Policy.</span></span> <span data-ttu-id="2fb80-134">Die [TaskbarManager.IsPinningAllowed](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.ispinningallowed) -Eigenschaft können Sie überprüfen, ob anheften zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-134">The [TaskbarManager.IsPinningAllowed](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.ispinningallowed) property lets you check whether pinning is allowed.</span></span>

<span data-ttu-id="2fb80-135">Wenn der Benutzer die Pin-Schaltfläche klickt, sollten Sie diese Eigenschaft überprüfen, und wenn "false" ist, sollten Sie ein Meldungsdialogfeld informiert den Benutzer, den zum Anheften von auf diesem Computer nicht zulässig ist anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2fb80-135">When the user clicks your pin button, you should check this property, and if it's false, you should display a message dialog informing the user that pinning is not allowed on this machine.</span></span>

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


## <a name="5-construct-and-pin-your-tile"></a><span data-ttu-id="2fb80-136">5. erstellen Sie und anheften Sie Ihrer Kachel</span><span class="sxs-lookup"><span data-stu-id="2fb80-136">5. Construct and pin your tile</span></span>

<span data-ttu-id="2fb80-137">Der Benutzer die Pin-Schaltfläche geklickt hat, und festgestellt haben, dass die APIs vorhanden sind, Taskleiste vorhanden ist, und zum Anheften von wird die erforderliche Berechtigung bis zum Anheften!</span><span class="sxs-lookup"><span data-stu-id="2fb80-137">The user has clicked your pin button, and you've determined that the APIs are present, taskbar is present, and pinning is allowed... time to pin!</span></span>

<span data-ttu-id="2fb80-138">Erstellen Sie zuerst die sekundäre Kachel, ebenso wie bei an das Startmenü angeheftet.</span><span class="sxs-lookup"><span data-stu-id="2fb80-138">First, construct your secondary tile just like you would when pinning to Start.</span></span> <span data-ttu-id="2fb80-139">Erfahren Sie mehr über die sekundäre Kachel-Eigenschaften, lesen Sie [Sekundäre Kacheln an die Startseite anheften](secondary-tiles-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="2fb80-139">You can learn more about the secondary tile properties by reading [Pin secondary tiles to Start](secondary-tiles-pinning.md).</span></span> <span data-ttu-id="2fb80-140">Allerdings ist beim anheften an Taskleiste, zusätzlich zu den zuvor erforderlichen Eigenschaften Square44x44Logo (Dies ist das Logo, die von der Taskleiste verwendet) auch erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2fb80-140">However, when pinning to taskbar, in addition to the previously required properties, Square44x44Logo (this is the logo used by taskbar) is also required.</span></span> <span data-ttu-id="2fb80-141">Andernfalls wird eine Ausnahme ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="2fb80-141">Otherwise, an exception will be thrown.</span></span>

<span data-ttu-id="2fb80-142">Anschließend übergeben Sie die Kachel an die **[RequestPinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.requestpinsecondarytileasync)** -Methode.</span><span class="sxs-lookup"><span data-stu-id="2fb80-142">Then, pass the tile to the **[RequestPinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.requestpinsecondarytileasync)** method.</span></span> <span data-ttu-id="2fb80-143">Da dies unter eingeschränktem Zugriff ist, dies kein Bestätigungsdialogfeld angezeigt, und es wird einen UI-Thread ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2fb80-143">Since this is under limited-access, this will not display a confirmation dialog and does not require a UI thread.</span></span> <span data-ttu-id="2fb80-144">Jedoch in Zukunft Wenn dies geöffnet wird oben über begrenzte Zugriff, Aufrufer nicht mit eingeschränktem Zugriff wird ein Dialogfeld angezeigt und muss im UI-Thread verwenden.</span><span class="sxs-lookup"><span data-stu-id="2fb80-144">But in the future when this is opened up beyond limited-access, callers not utilizing limited-access will receive a dialog and be required to use the UI thread.</span></span>

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

<span data-ttu-id="2fb80-145">Diese Methode gibt einen booleschen Wert, der angibt, ob die Kachel jetzt an die Taskleiste angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-145">This method returns a boolean value that indicates whether your tile is now pinned to the taskbar.</span></span> <span data-ttu-id="2fb80-146">Wenn die Kachel bereits angeheftet war, wird die Methode aktualisiert die vorhandene Kachel und "true" zurück.</span><span class="sxs-lookup"><span data-stu-id="2fb80-146">If your tile was already pinned, the method updates the existing tile and returns true.</span></span> <span data-ttu-id="2fb80-147">Wenn zum Anheften von war nicht zulässig oder Taskleiste wird nicht unterstützt, gibt die Methode "false".</span><span class="sxs-lookup"><span data-stu-id="2fb80-147">If pinning wasn't allowed or taskbar isn't supported, the method returns false.</span></span>


## <a name="enumerate-tiles"></a><span data-ttu-id="2fb80-148">Auflisten von Kacheln</span><span class="sxs-lookup"><span data-stu-id="2fb80-148">Enumerate tiles</span></span>

<span data-ttu-id="2fb80-149">Um alle Kacheln anzuzeigen, die Sie erstellt haben und weiterhin an einer beliebigen Stelle angeheftet verwenden (Start, Taskleiste oder beides), **[FindAllAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.findallasync)**.</span><span class="sxs-lookup"><span data-stu-id="2fb80-149">To see all the tiles that you created and are still pinned somewhere (Start, taskbar, or both), use **[FindAllAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.findallasync)**.</span></span> <span data-ttu-id="2fb80-150">Anschließend können Sie überprüfen, ob diese Kacheln auf der Taskleiste bzw. die Startseite angeheftet sind.</span><span class="sxs-lookup"><span data-stu-id="2fb80-150">You can subsequently check whether these tiles are pinned to the taskbar and/or Start.</span></span> <span data-ttu-id="2fb80-151">Wenn die Oberfläche nicht unterstützt wird, geben diese Methoden "false" zurück.</span><span class="sxs-lookup"><span data-stu-id="2fb80-151">If the surface isn't supported, these methods return false.</span></span>

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


## <a name="update-a-tile"></a><span data-ttu-id="2fb80-152">Aktualisieren von Kacheln</span><span class="sxs-lookup"><span data-stu-id="2fb80-152">Update a tile</span></span>

<span data-ttu-id="2fb80-153">Um eine bereits angeheftete Kachel zu aktualisieren, können Sie die Methode [**SecondaryTile.UpdateAsync**](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.updateasync) gemäß [Aktualisieren einer sekundären Kachel](secondary-tiles-pinning.md#updating-a-secondary-tile).</span><span class="sxs-lookup"><span data-stu-id="2fb80-153">To update an already pinned tile, you can use the [**SecondaryTile.UpdateAsync**](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.updateasync) method as described in [Updating a secondary tile](secondary-tiles-pinning.md#updating-a-secondary-tile).</span></span>


## <a name="unpin-a-tile"></a><span data-ttu-id="2fb80-154">Lösen Sie eine Kachel</span><span class="sxs-lookup"><span data-stu-id="2fb80-154">Unpin a tile</span></span>

<span data-ttu-id="2fb80-155">Ihre app sollte eine Schaltfläche "lösen" angeben, ob die Kachel derzeit angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-155">Your app should provide an unpin button if the tile is currently pinned.</span></span> <span data-ttu-id="2fb80-156">Um die Kachel zu lösen, rufen Sie einfach **[TryUnpinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.tryunpinsecondarytileasync)**, und übergeben Sie die **TileId** der sekundären Kachel gewünschte gelöst hat.</span><span class="sxs-lookup"><span data-stu-id="2fb80-156">To unpin the tile, simply call **[TryUnpinSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.tryunpinsecondarytileasync)**, passing in the **TileId** of the secondary tile you would like unpinned.</span></span>

<span data-ttu-id="2fb80-157">Diese Methode gibt einen booleschen Wert, der angibt, ob die Kachel nicht mehr an die Taskleiste angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-157">This method returns a boolean value that indicates whether your tile is no longer pinned to the taskbar.</span></span> <span data-ttu-id="2fb80-158">Wenn in erster Linie die Kachel angeheftet wurde nicht, zurück dies auch "true".</span><span class="sxs-lookup"><span data-stu-id="2fb80-158">If your tile wasn't pinned in the first place, this also returns true.</span></span> <span data-ttu-id="2fb80-159">Wenn lösen dürfen nicht war, gibt diese "false" zurück.</span><span class="sxs-lookup"><span data-stu-id="2fb80-159">If unpinning wasn't allowed, this returns false.</span></span>

<span data-ttu-id="2fb80-160">Wenn die Kachel nur an Taskleiste angeheftet wurde, wird dadurch die Kachel gelöscht, da es nicht mehr an einer beliebigen Stelle angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-160">If your tile was only pinned to taskbar, this will delete the tile since it is no longer pinned anywhere.</span></span>

```csharp
var taskbarManager = TaskbarManager.GetDefault();
if (taskbarManager != null)
{
    bool isUnpinned = await taskbarManager.TryUnpinSecondaryTileAsync("myTileId");
}
```


## <a name="delete-a-tile"></a><span data-ttu-id="2fb80-161">Löschen Sie eine Kachel</span><span class="sxs-lookup"><span data-stu-id="2fb80-161">Delete a tile</span></span>

<span data-ttu-id="2fb80-162">Wenn Sie eine Kachel von überall (Start, Taskleiste) lösen möchten, verwenden Sie die **[RequestDeleteAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.requestdeleteasync)** -Methode.</span><span class="sxs-lookup"><span data-stu-id="2fb80-162">If you want to unpin a tile from everywhere (Start, taskbar), use the **[RequestDeleteAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile.requestdeleteasync)** method.</span></span>

<span data-ttu-id="2fb80-163">Dies eignet sich für Fälle, in denen die Inhalte der Benutzer angeheftet nicht mehr anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-163">This is appropriate for cases where the content the user pinned is no longer applicable.</span></span> <span data-ttu-id="2fb80-164">Beispielsweise sollten Ihrer app können Sie ein Notizbuch Startmenü und Taskleiste anheften und dann der Benutzer das Notizbuch löscht, Sie einfach das Notizbuch zugeordnete Kachel löschen.</span><span class="sxs-lookup"><span data-stu-id="2fb80-164">For example, if your app lets you pin a notebook to Start and taskbar, and then the user deletes the notebook, you should simply delete the tile associated with the notebook.</span></span>

```csharp
// Initialize a secondary tile with the same tile ID you want removed.
// Or, locate it with FindAllAsync()
SecondaryTile toBeDeleted = new SecondaryTile(tileId);

// And then delete the tile
await toBeDeleted.RequestDeleteAsync();
```


## <a name="unpin-only-from-start"></a><span data-ttu-id="2fb80-165">Lösen Sie nur auf dem Startbildschirm</span><span class="sxs-lookup"><span data-stu-id="2fb80-165">Unpin only from Start</span></span>

<span data-ttu-id="2fb80-166">Wenn Sie nur eine sekundäre Kachel auf der Startseite, ohne dass es auf der Taskleiste lösen möchten, können Sie die **[StartScreenManager.TryRemoveSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager.tryremovesecondarytileasync)** -Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2fb80-166">If you only want to unpin a secondary tile from Start while leaving it on Taskbar, you can call the **[StartScreenManager.TryRemoveSecondaryTileAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager.tryremovesecondarytileasync)** method.</span></span> <span data-ttu-id="2fb80-167">Dadurch wird die Kachel auf ähnliche Weise gelöscht, wenn es nicht mehr für alle anderen Oberflächen angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-167">This will similarly delete the tile if it is no longer pinned to any other surfaces.</span></span>

<span data-ttu-id="2fb80-168">Diese Methode gibt einen booleschen Wert, der angibt, ob die Kachel nicht mehr an die Startseite angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="2fb80-168">This method returns a boolean value that indicates whether your tile is no longer pinned to Start.</span></span> <span data-ttu-id="2fb80-169">Wenn in erster Linie die Kachel angeheftet wurde nicht, zurück dies auch "true".</span><span class="sxs-lookup"><span data-stu-id="2fb80-169">If your tile wasn't pinned in the first place, this also returns true.</span></span> <span data-ttu-id="2fb80-170">Lösen war nicht zulässig oder Start wird nicht unterstützt, gibt dies "false".</span><span class="sxs-lookup"><span data-stu-id="2fb80-170">If unpinning wasn't allowed or Start isn't supported, this returns false.</span></span>

```csharp
await StartScreenManager.GetDefault().TryRemoveSecondaryTileAsync("myTileId");
```


## <a name="resources"></a><span data-ttu-id="2fb80-171">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="2fb80-171">Resources</span></span>

* [<span data-ttu-id="2fb80-172">TaskbarManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="2fb80-172">TaskbarManager class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager)
* [<span data-ttu-id="2fb80-173">Sekundäre Kacheln an die Startseite anheften</span><span class="sxs-lookup"><span data-stu-id="2fb80-173">Pin secondary tiles to Start</span></span>](secondary-tiles-pinning.md)