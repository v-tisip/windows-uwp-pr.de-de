---
author: anbare
Description: "Hier erfahren Sie, wie Sie eine sekundäre Kachel von Ihrer UWP-App anheften."
title: "Sekundäre Kacheln anheften"
label: Pin secondary tiles
template: detail.hbs
ms.author: wdg-dev-content
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, sekundäre Kacheln, Anheften, anheften, Schnellstart, Codebeispiel, Beispiel, Sekundärkachel"
ms.openlocfilehash: 9525dc91ddd40265d7c7fa9ff8e73509ba3029ab
ms.sourcegitcommit: 6396a69aab081f5c7a9a59739c83538616d3b1c7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2017
---
# <a name="pin-secondary-tiles"></a><span data-ttu-id="1b0d4-104">Sekundäre Kacheln anheften</span><span class="sxs-lookup"><span data-stu-id="1b0d4-104">Pin secondary tiles</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="1b0d4-105">Dieses Thema führt Sie durch die Schritte zum Erstellen einer sekundären Kachel für Ihre UWP-App und Anheften der Kachel an das Startmenü.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-105">This topic walks you through the steps to create a secondary tile for your UWP app and pin it to the Start menu.</span></span>

![Screenshot von sekundären Kacheln](images/secondarytiles.png)

<span data-ttu-id="1b0d4-107">Weitere Informationen zum Erstellen und Anheften von Sekundärkacheln finden Sie unter [Übersicht über sekundäre Kacheln](tiles-and-notifications-secondary-tiles.md).</span><span class="sxs-lookup"><span data-stu-id="1b0d4-107">To learn more about secondary tiles, please see the [Secondary tiles overview](tiles-and-notifications-secondary-tiles.md).</span></span>


## <a name="add-namespace"></a><span data-ttu-id="1b0d4-108">Hinzufügen von Namespaces</span><span class="sxs-lookup"><span data-stu-id="1b0d4-108">Add namespace</span></span>

<span data-ttu-id="1b0d4-109">Der Windows.UI. StartScreen-Namespace enthält die SecondaryTile-Klasse.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-109">The Windows.UI.StartScreen namespace includes the SecondaryTile class.</span></span>

```csharp
using Windows.UI.StartScreen;
```


## <a name="initialize-the-secondary-tile"></a><span data-ttu-id="1b0d4-110">Initialisieren Sie die sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="1b0d4-110">Initialize the secondary tile</span></span>

<span data-ttu-id="1b0d4-111">Sekundäre Kacheln bestehen aus einigen wichtigen Komponenten...</span><span class="sxs-lookup"><span data-stu-id="1b0d4-111">Secondary tiles are composed of a few key components...</span></span>

* <span data-ttu-id="1b0d4-112">**TileId**: Ein eindeutiger Bezeichner, mit dem Sie die Kachel von Ihren anderen sekundären Kacheln identifizieren können.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-112">**TileId**: A unique identifier that lets you identify the tile among your other secondary tiles.</span></span>
* <span data-ttu-id="1b0d4-113">**DisplayName**: Der Name, der auf der Kachel angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-113">**DisplayName**: The name you want shown on the tile.</span></span>
* <span data-ttu-id="1b0d4-114">**Argumente**: Die Argumente, die an Ihre App zurück übergeben werden sollen, wenn der Benutzer auf Ihre Kachel klickt.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-114">**Arguments**: The arguments you want passed back to your app when the user clicks your tile.</span></span>
* <span data-ttu-id="1b0d4-115">**Square150x150Logo**: Das erforderliche Logo, das auf der mittelgroßen Kachel angezeigt wird (die in verkleinerter Kachelgröße angezeigt wird, wenn kein kleines Logo bereitgestellt wird).</span><span class="sxs-lookup"><span data-stu-id="1b0d4-115">**Square150x150Logo**: The required logo, displayed on the medium size tile (and resized to small size tile if no small logo provided).</span></span>

<span data-ttu-id="1b0d4-116">Sie **MÜSSEN** initialisierte Werte für alle oben genannten Eigenschaften anbieten, da andernfalls eine Ausnahme ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-116">You **MUST** provide initialized values for all of the above properties, or else you will get an exception.</span></span>

<span data-ttu-id="1b0d4-117">Es gibt eine Vielzahl von Konstruktoren, die Sie verwenden können, das Verwenden des Konstruktors, der TileId, DisplayName, Argumente, Square150x150Logo und DesiredSize annimmt, stellt allerdings sicher, dass Sie alle erforderlichen Eigenschaften festlegen.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-117">There are a variety of constructors you can use, but using the constructor that takes in the tileId, displayName, arguments, square150x150Logo, and desiredSize helps ensure you set all of the required properties.</span></span>

```csharp
// Construct a unique tile ID, which you will need to use later for updating the tile
string tileId = "City" + zipCode;

// Use a display name you like
string displayName = cityName;

// Provide all the required info in arguments so that when user
// clicks your tile, you can navigate them to the correct content
string arguments = "action=viewCity&zipCode=" + zipCode;

// Initialize the tile with required arguments
SecondaryTile tile = new SecondaryTile(
    tileId,
    displayName,
    arguments,
    new Uri("ms-appx:///Assets/CityTiles/Square150x150Logo.png"),
    TileSize.Default);
```


## <a name="optional-add-support-for-larger-tile-sizes"></a><span data-ttu-id="1b0d4-118">Optional: Hinzufügen von Unterstützung für größere Kacheln</span><span class="sxs-lookup"><span data-stu-id="1b0d4-118">Optional: Add support for larger tile sizes</span></span>

<span data-ttu-id="1b0d4-119">Wenn Sie vorhaben, umfassende Kachelbenachrichtigungen auf der sekundären Kachel anzuzeigen, sollten Sie dem Anwender ermöglichen, die Breite oder Größe ihrer Kachel zu ändern, damit noch mehr Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-119">If you're going to be displaying rich tile notifications on your secondary tile, you'll likely want to allow the user to resize their tile to be wide or large, so that they can see even more of your content.</span></span>

<span data-ttu-id="1b0d4-120">Um breite und große Kachelgrößen zu aktivieren, müssen Sie *Wide310x150Logo* und *Square310x310Logo* angeben.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-120">To enable wide and large tile sizes, you need to provide the *Wide310x150Logo* and *Square310x310Logo*.</span></span> <span data-ttu-id="1b0d4-121">Wenn möglich, sollten Sie ebenfalls *Square71x71Logo* für die kleine Kachelgröße bereitstellen (andernfalls wird die erforderliche Größe Square150x150Logo für die kleine Kachel angewandt).</span><span class="sxs-lookup"><span data-stu-id="1b0d4-121">Also, if possible, you should provide the *Square71x71Logo* for the small tile size (otherwise we will downsize your required Square150x150Logo for the small tile).</span></span>

<span data-ttu-id="1b0d4-122">Sie können ebenfalls ein eindeutiges *Square44x44Logo* bereitstellen, das optional in der unteren rechten Ecke angezeigt wird, wenn eine Benachrichtigung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-122">You can also provide a unique *Square44x44Logo*, which is optionally displayed on the bottom right corner when a notification is present.</span></span> <span data-ttu-id="1b0d4-123">Wenn Sie diese nicht angeben, wird stattdessen *Square44x44Logo* aus der primären Kachel verwendet.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-123">If you don't provide one, the *Square44x44Logo* from your primary tile will be used instead.</span></span>

```csharp
// Enable wide and large tile sizes
tile.VisualElements.Wide310x150Logo = new Uri("ms-appx:///Assets/CityTiles/Wide310x150Logo.png");
tile.VisualElements.Square310x310Logo = new Uri("ms-appx:///Assets/CityTiles/Square310x310Logo.png");

// Add a small size logo for better looking small tile
tile.VisualElements.Square71x71Logo = new Uri("ms-appx:///Assets/CityTiles/Square71x71Logo.png");

// Add a unique corner logo for the secondary tile
tile.VisualElements.Square44x44Logo = new Uri("ms-appx:///Assets/CityTiles/Square44x44Logo.png");
```


## <a name="optional-enable-showing-the-display-name"></a><span data-ttu-id="1b0d4-124">Optional: Aktivieren Sie die Anzeige des Anzeigenamens</span><span class="sxs-lookup"><span data-stu-id="1b0d4-124">Optional: Enable showing the display name</span></span>

<span data-ttu-id="1b0d4-125">Der Anzeigename wird standardmäßig nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-125">By default the display name will NOT be shown.</span></span> <span data-ttu-id="1b0d4-126">Um den Anzeigenamen in mittelgroß, breit, groß anzuzeigen, fügen Sie den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-126">To show the display name on medium/wide/large, add the following code.</span></span>

```csharp
// Show the display name on all sizes
tile.VisualElements.ShowNameOnSquare150x150Logo = true;
tile.VisualElements.ShowNameOnWide310x150Logo = true;
tile.VisualElements.ShowNameOnSquare310x310Logo = true;
```


## <a name="pin-the-secondary-tile"></a><span data-ttu-id="1b0d4-127">Anheften der sekundären Kachel</span><span class="sxs-lookup"><span data-stu-id="1b0d4-127">Pin the secondary tile</span></span>

<span data-ttu-id="1b0d4-128">Fordern Sie schließlich das Anheften der Kachel auf.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-128">Finally, request to pin the tile.</span></span> <span data-ttu-id="1b0d4-129">Beachten Sie, dass dies von einem UI-Thread aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-129">Note that this must be called from a UI thread.</span></span> <span data-ttu-id="1b0d4-130">Auf dem Desktop wird ein Dialogfeld angezeigt, das den Benutzer auffordert zu bestätigen, ob er die Kachel anheften möchte.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-130">On Desktop, a dialog will appear asking the user to confirm whether they would like to pin the tile.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b0d4-131">Bei einer Windows-Desktopanwendung, die die Desktop-Brücke verwendet, müssen Sie zuerst einen zusätzlichen Schritt ausführen, wie unter [Anheften ab einer Desktopanwendung](tiles-and-notifications-secondary-tiles-desktop-pinning.md) beschrieben</span><span class="sxs-lookup"><span data-stu-id="1b0d4-131">If you are a Windows desktop application using the Desktop Bridge, you must first perform an extra step as described in [Pin from desktop application](tiles-and-notifications-secondary-tiles-desktop-pinning.md)</span></span>

```csharp
// Pin the tile
bool isPinned = await tile.RequestCreateAsync();

// TODO: Update UI to reflect whether user can now either unpin or pin
```


## <a name="check-if-a-secondary-tile-exists"></a><span data-ttu-id="1b0d4-132">Überprüfen Sie, ob eine sekundäre Kachel vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="1b0d4-132">Check if a secondary tile exists</span></span>

<span data-ttu-id="1b0d4-133">Wenn Ihre Benutzer eine Seite in Ihrer App besuchen, die sie bereits auf der Startseite angeheftet haben, möchten Sie stattdessen eine Schaltfläche "Entfernen" anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-133">If your user visits a page in your app that they have already pinned to Start, you will want to instead display an "Unpin" button.</span></span>

<span data-ttu-id="1b0d4-134">Daher sollten Sie bei der Auswahl der Schaltfläche, die angezeigt werden soll zunächst überprüfen, ob derzeit deren sekundäre Kachel angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-134">Therefore, when choosing what button to display, you need to first check whether the secondary tile is currently pinned.</span></span>

```csharp
// Check if the secondary tile is pinned
bool isPinned = SecondaryTile.Exists(tileId);

// TODO: Update UI to reflect whether user can either unpin or pin
```


## <a name="unpinning-a-secondary-tile"></a><span data-ttu-id="1b0d4-135">Lösen einer sekundären Kachel</span><span class="sxs-lookup"><span data-stu-id="1b0d4-135">Unpinning a secondary tile</span></span>

<span data-ttu-id="1b0d4-136">Wenn die Kachel zurzeit angeheftet ist und der Benutzer klickt auf die Schaltfläche „Lösen”, sollte die Kachel gelöst (gelöscht) werden.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-136">If the tile is currently pinned, and the user clicks your unpin button, you'll want to unpin (delete) the tile.</span></span>

```csharp
// Initialize a secondary tile with the same tile ID you want removed
SecondaryTile toBeDeleted = new SecondaryTile(tileId);

// And then unpin the tile
await toBeDeleted.RequestDeleteAsync();
```


## <a name="updating-a-secondary-tile"></a><span data-ttu-id="1b0d4-137">Aktualisieren einer sekundären Kachel</span><span class="sxs-lookup"><span data-stu-id="1b0d4-137">Updating a secondary tile</span></span>

<span data-ttu-id="1b0d4-138">Wenn Sie die Logos, Anzeigenamen oder anderen Elementen auf der sekundären Kachel aktualisieren müssen, können Sie *RequestUpdateAsync* verwenden.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-138">If you need to update the logos, display name, or anything else on the secondary tile, you can use *RequestUpdateAsync*.</span></span>

```csharp
// Initialize a secondary tile with the same tile ID you want to update
SecondaryTile tile = new SecondaryTile(tileId);

// Assign ALL properties, including ones you aren't changing

// And then update it
await tile.UpdateAsync();
```


## <a name="enumerating-all-pinned-secondary-tiles"></a><span data-ttu-id="1b0d4-139">Auflisten aller angehefteten sekundären Kacheln</span><span class="sxs-lookup"><span data-stu-id="1b0d4-139">Enumerating all pinned secondary tiles</span></span>

<span data-ttu-id="1b0d4-140">Wenn Sie alle Kacheln ermitteln müssen, die der Benutzer angeheftet hat, verwenden Sie anstelle von *SecondaryTile.Exists* *SecondaryTile.FindAllAsync()*.</span><span class="sxs-lookup"><span data-stu-id="1b0d4-140">If you need to discover all the tiles your user has pinned, instead of using *SecondaryTile.Exists*, you can alternatively use *SecondaryTile.FindAllAsync()*.</span></span>

```csharp
// Get all secondary tiles
var tiles = await SecondaryTile.FindAllAsync();
```


## <a name="send-a-tile-notification"></a><span data-ttu-id="1b0d4-141">Senden einer Kachelbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="1b0d4-141">Send a tile notification</span></span>

<span data-ttu-id="1b0d4-142">Weitere Informationen zum Anzeigen umfassender Inhalte auf einer Kachel per Kachelbenachrichtigungen finden Sie unter [Senden einer lokalen Kachelbenachrichtigung](tiles-and-notifications-sending-a-local-tile-notification.md).</span><span class="sxs-lookup"><span data-stu-id="1b0d4-142">To learn how to display rich content on your tile via tile notifications, please see [Send a local tile notification](tiles-and-notifications-sending-a-local-tile-notification.md).</span></span>


## <a name="related"></a><span data-ttu-id="1b0d4-143">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1b0d4-143">Related</span></span>

* [<span data-ttu-id="1b0d4-144">Übersicht über sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="1b0d4-144">Secondary tiles overview</span></span>](tiles-and-notifications-secondary-tiles.md)
* [<span data-ttu-id="1b0d4-145">Anleitung für sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="1b0d4-145">Secondary tiles guidance</span></span>](tiles-and-notifications-secondary-tiles-guidance.md)
* [<span data-ttu-id="1b0d4-146">Kachelressourcen</span><span class="sxs-lookup"><span data-stu-id="1b0d4-146">Tile assets</span></span>](tiles-and-notifications-app-assets.md)
* [<span data-ttu-id="1b0d4-147">Dokumentation für den Kachelinhalt</span><span class="sxs-lookup"><span data-stu-id="1b0d4-147">Tile content documentation</span></span>](tiles-and-notifications-create-adaptive-tiles.md)
* [<span data-ttu-id="1b0d4-148">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="1b0d4-148">Send a local tile notification</span></span>](tiles-and-notifications-sending-a-local-tile-notification.md)