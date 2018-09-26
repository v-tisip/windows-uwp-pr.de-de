---
author: andrewleader
Description: Learn how to pin a secondary tile from your UWP app.
title: Sekundäre Kacheln anheften
label: Pin secondary tiles
template: detail.hbs
ms.author: wdg-dev-content
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, sekundäre Kacheln, Anheften, anheften, Schnellstart, Codebeispiel, Beispiel, Sekundärkachel
ms.localizationpriority: medium
ms.openlocfilehash: 437d149e22f035fdd0cb1f5251a114b6dd4765e4
ms.sourcegitcommit: e4f3e1b2d08a02b9920e78e802234e5b674e7223
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2018
ms.locfileid: "4209960"
---
# <a name="pin-secondary-tiles"></a><span data-ttu-id="7c3bd-103">Sekundäre Kacheln anheften</span><span class="sxs-lookup"><span data-stu-id="7c3bd-103">Pin secondary tiles</span></span>


<span data-ttu-id="7c3bd-104">Dieses Thema führt Sie durch die Schritte zum Erstellen einer sekundären Kachel für Ihre UWP-App und Anheften der Kachel an das Startmenü.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-104">This topic walks you through the steps to create a secondary tile for your UWP app and pin it to the Start menu.</span></span>

![Screenshot von sekundären Kacheln](images/secondarytiles.png)

<span data-ttu-id="7c3bd-106">Weitere Informationen zum Erstellen und Anheften von Sekundärkacheln finden Sie unter [Übersicht über sekundäre Kacheln](secondary-tiles.md).</span><span class="sxs-lookup"><span data-stu-id="7c3bd-106">To learn more about secondary tiles, please see the [Secondary tiles overview](secondary-tiles.md).</span></span>


## <a name="add-namespace"></a><span data-ttu-id="7c3bd-107">Hinzufügen von Namespaces</span><span class="sxs-lookup"><span data-stu-id="7c3bd-107">Add namespace</span></span>

<span data-ttu-id="7c3bd-108">Der Windows.UI. StartScreen-Namespace enthält die SecondaryTile-Klasse.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-108">The Windows.UI.StartScreen namespace includes the SecondaryTile class.</span></span>

```csharp
using Windows.UI.StartScreen;
```


## <a name="initialize-the-secondary-tile"></a><span data-ttu-id="7c3bd-109">Initialisieren Sie die sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="7c3bd-109">Initialize the secondary tile</span></span>

<span data-ttu-id="7c3bd-110">Sekundäre Kacheln bestehen aus einigen wichtigen Komponenten...</span><span class="sxs-lookup"><span data-stu-id="7c3bd-110">Secondary tiles are composed of a few key components...</span></span>

* <span data-ttu-id="7c3bd-111">**TileId**: Ein eindeutiger Bezeichner, mit dem Sie die Kachel von Ihren anderen sekundären Kacheln identifizieren können.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-111">**TileId**: A unique identifier that lets you identify the tile among your other secondary tiles.</span></span>
* <span data-ttu-id="7c3bd-112">**DisplayName**: Der Name, der auf der Kachel angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-112">**DisplayName**: The name you want shown on the tile.</span></span>
* <span data-ttu-id="7c3bd-113">**Argumente**: Die Argumente, die an Ihre App zurück übergeben werden sollen, wenn der Benutzer auf Ihre Kachel klickt.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-113">**Arguments**: The arguments you want passed back to your app when the user clicks your tile.</span></span>
* <span data-ttu-id="7c3bd-114">**Square150x150Logo**: Das erforderliche Logo, das auf der mittelgroßen Kachel angezeigt wird (die in verkleinerter Kachelgröße angezeigt wird, wenn kein kleines Logo bereitgestellt wird).</span><span class="sxs-lookup"><span data-stu-id="7c3bd-114">**Square150x150Logo**: The required logo, displayed on the medium size tile (and resized to small size tile if no small logo provided).</span></span>

<span data-ttu-id="7c3bd-115">Sie **MÜSSEN** initialisierte Werte für alle oben genannten Eigenschaften anbieten, da andernfalls eine Ausnahme ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-115">You **MUST** provide initialized values for all of the above properties, or else you will get an exception.</span></span>

<span data-ttu-id="7c3bd-116">Es gibt eine Vielzahl von Konstruktoren, die Sie verwenden können, das Verwenden des Konstruktors, der TileId, DisplayName, Argumente, Square150x150Logo und DesiredSize annimmt, stellt allerdings sicher, dass Sie alle erforderlichen Eigenschaften festlegen.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-116">There are a variety of constructors you can use, but using the constructor that takes in the tileId, displayName, arguments, square150x150Logo, and desiredSize helps ensure you set all of the required properties.</span></span>

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


## <a name="optional-add-support-for-larger-tile-sizes"></a><span data-ttu-id="7c3bd-117">Optional: Hinzufügen von Unterstützung für größere Kacheln</span><span class="sxs-lookup"><span data-stu-id="7c3bd-117">Optional: Add support for larger tile sizes</span></span>

<span data-ttu-id="7c3bd-118">Wenn Sie vorhaben, umfassende Kachelbenachrichtigungen auf der sekundären Kachel anzuzeigen, sollten Sie dem Anwender ermöglichen, die Breite oder Größe ihrer Kachel zu ändern, damit noch mehr Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-118">If you're going to be displaying rich tile notifications on your secondary tile, you'll likely want to allow the user to resize their tile to be wide or large, so that they can see even more of your content.</span></span>

<span data-ttu-id="7c3bd-119">Um breite und große Kachelgrößen zu aktivieren, müssen Sie *Wide310x150Logo* und *Square310x310Logo* angeben.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-119">To enable wide and large tile sizes, you need to provide the *Wide310x150Logo* and *Square310x310Logo*.</span></span> <span data-ttu-id="7c3bd-120">Wenn möglich, sollten Sie ebenfalls *Square71x71Logo* für die kleine Kachelgröße bereitstellen (andernfalls wird die erforderliche Größe Square150x150Logo für die kleine Kachel angewandt).</span><span class="sxs-lookup"><span data-stu-id="7c3bd-120">Also, if possible, you should provide the *Square71x71Logo* for the small tile size (otherwise we will downsize your required Square150x150Logo for the small tile).</span></span>

<span data-ttu-id="7c3bd-121">Sie können ebenfalls ein eindeutiges *Square44x44Logo* bereitstellen, das optional in der unteren rechten Ecke angezeigt wird, wenn eine Benachrichtigung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-121">You can also provide a unique *Square44x44Logo*, which is optionally displayed on the bottom right corner when a notification is present.</span></span> <span data-ttu-id="7c3bd-122">Wenn Sie diese nicht angeben, wird stattdessen *Square44x44Logo* aus der primären Kachel verwendet.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-122">If you don't provide one, the *Square44x44Logo* from your primary tile will be used instead.</span></span>

```csharp
// Enable wide and large tile sizes
tile.VisualElements.Wide310x150Logo = new Uri("ms-appx:///Assets/CityTiles/Wide310x150Logo.png");
tile.VisualElements.Square310x310Logo = new Uri("ms-appx:///Assets/CityTiles/Square310x310Logo.png");

// Add a small size logo for better looking small tile
tile.VisualElements.Square71x71Logo = new Uri("ms-appx:///Assets/CityTiles/Square71x71Logo.png");

// Add a unique corner logo for the secondary tile
tile.VisualElements.Square44x44Logo = new Uri("ms-appx:///Assets/CityTiles/Square44x44Logo.png");
```


## <a name="optional-enable-showing-the-display-name"></a><span data-ttu-id="7c3bd-123">Optional: Aktivieren Sie die Anzeige des Anzeigenamens</span><span class="sxs-lookup"><span data-stu-id="7c3bd-123">Optional: Enable showing the display name</span></span>

<span data-ttu-id="7c3bd-124">Der Anzeigename wird standardmäßig nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-124">By default the display name will NOT be shown.</span></span> <span data-ttu-id="7c3bd-125">Um den Anzeigenamen in mittelgroß, breit, groß anzuzeigen, fügen Sie den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-125">To show the display name on medium/wide/large, add the following code.</span></span>

```csharp
// Show the display name on all sizes
tile.VisualElements.ShowNameOnSquare150x150Logo = true;
tile.VisualElements.ShowNameOnWide310x150Logo = true;
tile.VisualElements.ShowNameOnSquare310x310Logo = true;
```


## <a name="optional-3d-secondary-tiles"></a><span data-ttu-id="7c3bd-126">Optional: Sekundäre 3D-Kacheln</span><span class="sxs-lookup"><span data-stu-id="7c3bd-126">Optional: 3D secondary tiles</span></span>
<span data-ttu-id="7c3bd-127">Sie können die sekundäre Kachel für Windows Mixed Reality verbessern, indem Sie 3D-Ressourcen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-127">You can enhance your secondary tile for Windows Mixed Reality by adding 3D assets.</span></span> <span data-ttu-id="7c3bd-128">Benutzer können 3D-Kacheln direkt in ihre Windows Mixed Reality Home-Umgebung anstelle des Startmenüs platzieren, wenn sie Ihre App in einer Mixed Reality-Umgebung verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-128">Users can place 3D tiles directly in their Windows Mixed Reality home instead of the Start menu when using your app in a Mixed Reality environment.</span></span> <span data-ttu-id="7c3bd-129">Sie können z.B. 360° Photospheres erstellen, die direkt in einer 360°-Foto-App verknüpft werden oder Ihren Benutzern ermöglichen, ein 3D-Modell eines Stuhls aus einem Möbelkatalog zu platzieren, das eine Seite zu den Optionen für Preise und Farben für das Objekt öffnet, wenn es ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-129">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place a 3D model of a chair from a furniture catalog that opens a details page about the pricing and color options for that object when selected.</span></span> <span data-ttu-id="7c3bd-130">Informationen zu ersten Schritten finden Sie in der [Mixed Reality-Entwicklerdokumentation](https://developer.microsoft.com/windows/mixed-reality/implementing_3d_deep_links_for_your_app_in_the_windows_mixed_reality_home).</span><span class="sxs-lookup"><span data-stu-id="7c3bd-130">To get started, refer to the [Mixed Reality developer documentation](https://developer.microsoft.com/windows/mixed-reality/implementing_3d_deep_links_for_your_app_in_the_windows_mixed_reality_home).</span></span>



## <a name="pin-the-secondary-tile"></a><span data-ttu-id="7c3bd-131">Anheften der sekundären Kachel</span><span class="sxs-lookup"><span data-stu-id="7c3bd-131">Pin the secondary tile</span></span>

<span data-ttu-id="7c3bd-132">Fordern Sie schließlich das Anheften der Kachel auf.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-132">Finally, request to pin the tile.</span></span> <span data-ttu-id="7c3bd-133">Beachten Sie, dass dies von einem UI-Thread aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-133">Note that this must be called from a UI thread.</span></span> <span data-ttu-id="7c3bd-134">Auf dem Desktop wird ein Dialogfeld angezeigt, das den Benutzer auffordert zu bestätigen, ob er die Kachel anheften möchte.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-134">On Desktop, a dialog will appear asking the user to confirm whether they would like to pin the tile.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c3bd-135">Bei einer Windows-Desktopanwendung, die die Desktop-Brücke verwendet, müssen Sie zuerst einen zusätzlichen Schritt ausführen, wie unter [Anheften ab einer Desktopanwendung](secondary-tiles-desktop-pinning.md) beschrieben</span><span class="sxs-lookup"><span data-stu-id="7c3bd-135">If you are a Windows desktop application using the Desktop Bridge, you must first perform an extra step as described in [Pin from desktop application](secondary-tiles-desktop-pinning.md)</span></span>

```csharp
// Pin the tile
bool isPinned = await tile.RequestCreateAsync();

// TODO: Update UI to reflect whether user can now either unpin or pin
```


## <a name="check-if-a-secondary-tile-exists"></a><span data-ttu-id="7c3bd-136">Überprüfen Sie, ob eine sekundäre Kachel vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="7c3bd-136">Check if a secondary tile exists</span></span>

<span data-ttu-id="7c3bd-137">Wenn Ihre Benutzer eine Seite in Ihrer App besuchen, die sie bereits auf der Startseite angeheftet haben, möchten Sie stattdessen eine Schaltfläche "Entfernen" anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-137">If your user visits a page in your app that they have already pinned to Start, you will want to instead display an "Unpin" button.</span></span>

<span data-ttu-id="7c3bd-138">Daher sollten Sie bei der Auswahl der Schaltfläche, die angezeigt werden soll zunächst überprüfen, ob derzeit deren sekundäre Kachel angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-138">Therefore, when choosing what button to display, you need to first check whether the secondary tile is currently pinned.</span></span>

```csharp
// Check if the secondary tile is pinned
bool isPinned = SecondaryTile.Exists(tileId);

// TODO: Update UI to reflect whether user can either unpin or pin
```


## <a name="unpinning-a-secondary-tile"></a><span data-ttu-id="7c3bd-139">Lösen einer sekundären Kachel</span><span class="sxs-lookup"><span data-stu-id="7c3bd-139">Unpinning a secondary tile</span></span>

<span data-ttu-id="7c3bd-140">Wenn die Kachel zurzeit angeheftet ist und der Benutzer klickt auf die Schaltfläche „Lösen”, sollte die Kachel gelöst (gelöscht) werden.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-140">If the tile is currently pinned, and the user clicks your unpin button, you'll want to unpin (delete) the tile.</span></span>

```csharp
// Initialize a secondary tile with the same tile ID you want removed
SecondaryTile toBeDeleted = new SecondaryTile(tileId);

// And then unpin the tile
await toBeDeleted.RequestDeleteAsync();
```


## <a name="updating-a-secondary-tile"></a><span data-ttu-id="7c3bd-141">Aktualisieren einer sekundären Kachel</span><span class="sxs-lookup"><span data-stu-id="7c3bd-141">Updating a secondary tile</span></span>

<span data-ttu-id="7c3bd-142">Wenn Sie die Logos, Anzeigenamen oder anderen Elementen auf der sekundären Kachel aktualisieren müssen, können Sie *RequestUpdateAsync* verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-142">If you need to update the logos, display name, or anything else on the secondary tile, you can use *RequestUpdateAsync*.</span></span>

```csharp
// Initialize a secondary tile with the same tile ID you want to update
SecondaryTile tile = new SecondaryTile(tileId);

// Assign ALL properties, including ones you aren't changing

// And then update it
await tile.UpdateAsync();
```


## <a name="enumerating-all-pinned-secondary-tiles"></a><span data-ttu-id="7c3bd-143">Auflisten aller angehefteten sekundären Kacheln</span><span class="sxs-lookup"><span data-stu-id="7c3bd-143">Enumerating all pinned secondary tiles</span></span>

<span data-ttu-id="7c3bd-144">Wenn Sie alle Kacheln ermitteln müssen, die der Benutzer angeheftet hat, verwenden Sie anstelle von *SecondaryTile.Exists* *SecondaryTile.FindAllAsync()*.</span><span class="sxs-lookup"><span data-stu-id="7c3bd-144">If you need to discover all the tiles your user has pinned, instead of using *SecondaryTile.Exists*, you can alternatively use *SecondaryTile.FindAllAsync()*.</span></span>

```csharp
// Get all secondary tiles
var tiles = await SecondaryTile.FindAllAsync();
```


## <a name="send-a-tile-notification"></a><span data-ttu-id="7c3bd-145">Senden einer Kachelbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="7c3bd-145">Send a tile notification</span></span>

<span data-ttu-id="7c3bd-146">Weitere Informationen zum Anzeigen umfassender Inhalte auf einer Kachel per Kachelbenachrichtigungen finden Sie unter [Senden einer lokalen Kachelbenachrichtigung](sending-a-local-tile-notification.md).</span><span class="sxs-lookup"><span data-stu-id="7c3bd-146">To learn how to display rich content on your tile via tile notifications, please see [Send a local tile notification](sending-a-local-tile-notification.md).</span></span>


## <a name="related"></a><span data-ttu-id="7c3bd-147">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7c3bd-147">Related</span></span>

* [<span data-ttu-id="7c3bd-148">Übersicht über sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="7c3bd-148">Secondary tiles overview</span></span>](secondary-tiles.md)
* [<span data-ttu-id="7c3bd-149">Anleitung für sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="7c3bd-149">Secondary tiles guidance</span></span>](secondary-tiles-guidance.md)
* [<span data-ttu-id="7c3bd-150">Kachelressourcen</span><span class="sxs-lookup"><span data-stu-id="7c3bd-150">Tile assets</span></span>](app-assets.md)
* [<span data-ttu-id="7c3bd-151">Dokumentation für den Kachelinhalt</span><span class="sxs-lookup"><span data-stu-id="7c3bd-151">Tile content documentation</span></span>](create-adaptive-tiles.md)
* [<span data-ttu-id="7c3bd-152">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="7c3bd-152">Send a local tile notification</span></span>](sending-a-local-tile-notification.md)
