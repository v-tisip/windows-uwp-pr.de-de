---
author: vladimp
Description: Windows desktop applications can pin secondary tiles thanks to the Desktop Bridge!
title: Sekundäre Kacheln von der Desktopanwendung anheften
label: Pin secondary tiles from desktop application
template: detail.hbs
ms.author: mijacobs
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Desktop-Brücke, sekundäre Kacheln, anheften, Anheften, Schnellstart, Codebeispiel, Beispiel, Sekundärkachel, Desktopanwendung, Win32, Winforms, WPF
ms.localizationpriority: medium
ms.openlocfilehash: 0b0015a74750e08d575cad9d0ae78f8c864b7c09
ms.sourcegitcommit: d780e3a087ab5240ea643346480a1427bea9e29b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
ms.locfileid: "1573207"
---
# <a name="pin-secondary-tiles-from-desktop-application"></a><span data-ttu-id="70ab4-103">Sekundäre Kacheln von der Desktopanwendung anheften</span><span class="sxs-lookup"><span data-stu-id="70ab4-103">Pin secondary tiles from desktop application</span></span>


<span data-ttu-id="70ab4-104">Dank der [Desktop-Brück](https://developer.microsoft.com/windows/bridges/desktop) können Windows-Desktopanwendung (wie Win32, Windows Forms und WPF) sekundäre Kacheln anheften.</span><span class="sxs-lookup"><span data-stu-id="70ab4-104">Thanks to the [Desktop Bridge](https://developer.microsoft.com/windows/bridges/desktop), Windows desktop applications (like Win32, Windows Forms, and WPF) can pin secondary tiles!</span></span>

![Screenshot von sekundären Kacheln](images/secondarytiles.png)

> [!IMPORTANT]
> <span data-ttu-id="70ab4-106">**Erfordert das Fall Creators Update**: Sie müssen als Ziel Insider SDK 16299 angeben und Build 16299 oder höher ausführen, um sekundäre Kacheln von Desktop-Brücke-Apps anzuheften.</span><span class="sxs-lookup"><span data-stu-id="70ab4-106">**Requires Fall Creators Update**: You must target SDK 16299 and be running build 16299 or higher to pin secondary tiles from Desktop Bridge apps.</span></span>

<span data-ttu-id="70ab4-107">Das Hinzufügen einer sekundären Kachel von WPF oder WinForms ähnelt einer reinen UWP-App.</span><span class="sxs-lookup"><span data-stu-id="70ab4-107">Adding a secondary tile from your WPF or WinForms application is very similar to a pure UWP app.</span></span> <span data-ttu-id="70ab4-108">Der einzige Unterschied besteht darin, dass Sie das Hauptfenster-Handle (HWND) angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="70ab4-108">The only difference is that you must specify your main window handle (HWND).</span></span> <span data-ttu-id="70ab4-109">Der Grund dafür ist, dass Windows beim Anheften einer Kachel ein modales Dialogfeld anzeigt, das den Benutzer auffordert zu bestätigen, dass er die Kachel anheften möchte.</span><span class="sxs-lookup"><span data-stu-id="70ab4-109">This is because when pinning a tile, Windows displays a modal dialog asking the user to confirm whether they would like to pin the tile.</span></span> <span data-ttu-id="70ab4-110">Wenn die Desktop-Anwendung das SecondaryTile-Objekt nicht mit dem Besitzerfenster konfigurieren, kann Windows nicht feststellen, wo das Dialogfeld gezeichnet werden soll und der Vorgang schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="70ab4-110">If the desktop application doesn't configure the SecondaryTile object with the owner window, Windows doesn't know where to draw the dialog and the operation will fail.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70ab4-111">Kachelbenachrichtigungen werden auf sekundäre Kacheln, die über die Desktop-Brücke erstellt wurden, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="70ab4-111">Tile notifications are currently not supported on secondary tiles created through the Desktop Bridge.</span></span> <span data-ttu-id="70ab4-112">Wir arbeiten daran, um dieses Feature zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="70ab4-112">We're working to enable this feature.</span></span> 


## <a name="package-your-app-with-desktop-bridge"></a><span data-ttu-id="70ab4-113">Packen Sie Ihre App mit der Desktop-Brücke</span><span class="sxs-lookup"><span data-stu-id="70ab4-113">Package your app with Desktop Bridge</span></span>

<span data-ttu-id="70ab4-114">Wenn Sie Ihre App nicht mit der Desktop-Brücke gepackt haben [müssen Sie dies zuerst durchführen](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root), um alle UWP-APIs verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="70ab4-114">If you have not packaged your app with the Desktop Bridge, [you must do so first](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) before you can use any UWP APIs.</span></span>


## <a name="enable-access-to-iinitializewithwindow-interface"></a><span data-ttu-id="70ab4-115">Aktivieren des Zugriffs auf die IInitializeWithWindow-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="70ab4-115">Enable access to IInitializeWithWindow interface</span></span>

<span data-ttu-id="70ab4-116">Wenn die Anwendung in einer verwalteten Sprache wie z.B. C# oder Visual Basic geschrieben wurde, deklarieren Sie die IInitializeWithWindow-Schnittstelle im App-Code wie im folgenden C#-Beispiel mit dem [ComImport](https://msdn.microsoft.com/library/system.runtime.interopservices.comimportattribute.aspx) und dem Guid-Attribut.</span><span class="sxs-lookup"><span data-stu-id="70ab4-116">If your application is written in a managed language such as C# or Visual Basic, declare the IInitializeWithWindow interface in your app's code with the [ComImport](https://msdn.microsoft.com/library/system.runtime.interopservices.comimportattribute.aspx) and Guid attribute as shown in the following C# example.</span></span> <span data-ttu-id="70ab4-117">In diesem Beispiel wird davon ausgegangen, dass Ihre Codedatei über eine using-Anweisung für den System.Runtime.InteropServices-Namespace verfügt.</span><span class="sxs-lookup"><span data-stu-id="70ab4-117">This example assumes that your code file has a using statement for the System.Runtime.InteropServices namespace.</span></span>

```csharp
[ComImport]
[Guid("3E68D4BD-7135-4D10-8018-9FB6D9F33FA1")]
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IInitializeWithWindow
{
    void Initialize(IntPtr hwnd);
}
```

<span data-ttu-id="70ab4-118">Wenn Sie alternativ C++ verwenden, fügen Sie im Code einen Verweis auf die Headerdatei **shobjidl.h** hinzu.</span><span class="sxs-lookup"><span data-stu-id="70ab4-118">Alternatively, if you are using C++, add a reference to the **shobjidl.h** header file in your code.</span></span> <span data-ttu-id="70ab4-119">Diese Headerdatei enthält die Deklaration der *IInitializeWithWindow*-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="70ab4-119">This header file contains the declaration of the *IInitializeWithWindow* interface.</span></span>


## <a name="initialize-the-secondary-tile"></a><span data-ttu-id="70ab4-120">Initialisieren Sie die sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="70ab4-120">Initialize the secondary tile</span></span>

<span data-ttu-id="70ab4-121">Initialisieren Sie ein neues sekundäres Kachelobjekt genau wie in einer normalen UWP-App.</span><span class="sxs-lookup"><span data-stu-id="70ab4-121">Initialize a new secondary tile object exactly like you would with a normal UWP app.</span></span> <span data-ttu-id="70ab4-122">Weitere Informationen zum Erstellen und Anheften von Sekundärkacheln finden Sie unter [Sekundäre Kacheln anheften](secondary-tiles-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="70ab4-122">To learn more about creating and pinning secondary tiles, see [Pin secondary tiles](secondary-tiles-pinning.md).</span></span>

```csharp
// Initialize the tile with required arguments
SecondaryTile tile = new SecondaryTile(
    "myTileId5391",
    "Display name",
    "myActivationArgs",
    new Uri("ms-appx:///Assets/Square150x150Logo.png"),
    TileSize.Default);
```


## <a name="assign-the-window-handle"></a><span data-ttu-id="70ab4-123">Zuweisen des Fensterhandles</span><span class="sxs-lookup"><span data-stu-id="70ab4-123">Assign the window handle</span></span>

<span data-ttu-id="70ab4-124">Dies ist der wichtigste Schritt für Desktopanwendung.</span><span class="sxs-lookup"><span data-stu-id="70ab4-124">This is the key step for desktop applications.</span></span> <span data-ttu-id="70ab4-125">Wandeln Sie das Objekt in ein [IInitializeWithWindow](https://msdn.microsoft.com/library/windows/desktop/hh706981.aspx)-Objekt um.</span><span class="sxs-lookup"><span data-stu-id="70ab4-125">Cast the object to an [IInitializeWithWindow](https://msdn.microsoft.com/library/windows/desktop/hh706981.aspx) object.</span></span> <span data-ttu-id="70ab4-126">Rufen Sie dann die [IInitializeWithWindow.Initialize](https://msdn.microsoft.com/library/windows/desktop/hh706982.aspx)-Methode auf, und übergeben Sie das Handle des Fensters, das der Besitzer aller modalen Dialoge sein soll.</span><span class="sxs-lookup"><span data-stu-id="70ab4-126">Then, call the [IInitializeWithWindow.Initialize](https://msdn.microsoft.com/library/windows/desktop/hh706982.aspx) method, and pass the handle of the window that you want to be the owner for the modal dialog.</span></span> <span data-ttu-id="70ab4-127">Im folgenden C#-Beispiel wird gezeigt, wie das Handle des Hauptfensters der App an die Methode übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="70ab4-127">The following C# example shows how to pass the handle of your app’s main window to the method.</span></span>

```csharp
// Assign the window handle
IInitializeWithWindow initWindow = (IInitializeWithWindow)(object)tile;
initWindow.Initialize(System.Diagnostics.Process.GetCurrentProcess().MainWindowHandle);
```


## <a name="pin-the-tile"></a><span data-ttu-id="70ab4-128">Anheften der Kachel</span><span class="sxs-lookup"><span data-stu-id="70ab4-128">Pin the tile</span></span>

<span data-ttu-id="70ab4-129">Fordern Sie schließlich das Anheften der Kachel wie bei einer normalen UWP-App an.</span><span class="sxs-lookup"><span data-stu-id="70ab4-129">Finally, request to pin the tile as you would a normal UWP app.</span></span>

```csharp
// Pin the tile
bool isPinned = await tile.RequestCreateAsync();

// TODO: Update UI to reflect whether user can now either unpin or pin
```


## <a name="send-tile-notifications"></a><span data-ttu-id="70ab4-130">Senden von Kachelbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="70ab4-130">Send tile notifications</span></span>

<span data-ttu-id="70ab4-131">Kachelbenachrichtigungen auf sekundäre Kacheln, die über die Desktop-Brücke erstellt wurden, werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="70ab4-131">Tile notifications sent to secondary tiles are currently not supported by Desktop Bridge apps.</span></span> <span data-ttu-id="70ab4-132">Wenn Sie versuchen, eine Kachelbenachrichtigung an eine sekundäre Kachel zu senden, erhalten Sie eine Ausnahme *Element wurde nicht gefunden* mit HResult 0 x 80070490.</span><span class="sxs-lookup"><span data-stu-id="70ab4-132">If you attempt to send a tile notification to a secondary tile, you will receive an *Element not found* exception with HResult 0x80070490.</span></span> <span data-ttu-id="70ab4-133">Wir arbeiten daran, um dieses Feature zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="70ab4-133">We're working to enable this feature.</span></span>


## <a name="resources"></a><span data-ttu-id="70ab4-134">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="70ab4-134">Resources</span></span>

* [<span data-ttu-id="70ab4-135">Vollständiges Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="70ab4-135">Full code sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SecondaryTileSample)
* [<span data-ttu-id="70ab4-136">Übersicht über sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="70ab4-136">Secondary tiles overview</span></span>](secondary-tiles.md)
* [<span data-ttu-id="70ab4-137">Sekundäre Kacheln anheften (UWP)</span><span class="sxs-lookup"><span data-stu-id="70ab4-137">Pin secondary tiles (UWP)</span></span>](secondary-tiles-pinning.md)
* [<span data-ttu-id="70ab4-138">Desktop-Brücke</span><span class="sxs-lookup"><span data-stu-id="70ab4-138">Desktop Bridge</span></span>](https://developer.microsoft.com/windows/bridges/desktop)
* [<span data-ttu-id="70ab4-139">Desktop-Brücke: Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="70ab4-139">Desktop Bridge code samples</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples)