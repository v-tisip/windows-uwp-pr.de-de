---
author: vladimp
Description: "Windows-Desktopanwendungen können sekundäre Kacheln dank der Desktop-Brücke anheften!"
title: "Sekundäre Kacheln von der Desktopanwendung anheften"
label: Pin secondary tiles from desktop application
template: detail.hbs
ms.author: wdg-dev-content
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, Desktop-Brücke, sekundäre Kacheln, anheften, Anheften, Schnellstart, Codebeispiel, Beispiel, Sekundärkachel, Desktopanwendung, Win32, Winforms, WPF"
ms.openlocfilehash: dea17368a21983b9ca800aac2efa6410dab06958
ms.sourcegitcommit: 6396a69aab081f5c7a9a59739c83538616d3b1c7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2017
---
# <a name="pin-secondary-tiles-from-desktop-application"></a><span data-ttu-id="af35b-104">Sekundäre Kacheln von der Desktopanwendung anheften</span><span class="sxs-lookup"><span data-stu-id="af35b-104">Pin secondary tiles from desktop application</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="af35b-105">Dank der [Desktop-Brück](https://developer.microsoft.com/en-us/windows/bridges/desktop) können Windows-Desktopanwendung (wie Win32, Windows Forms und WPF) sekundäre Kacheln anheften.</span><span class="sxs-lookup"><span data-stu-id="af35b-105">Thanks to the [Desktop Bridge](https://developer.microsoft.com/en-us/windows/bridges/desktop), Windows desktop applications (like Win32, Windows Forms, and WPF) can pin secondary tiles!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af35b-106">**VORABVERSION | Erfordert das Fall Creators Update**: Sie müssen [Insider-Builds 16199](https://blogs.windows.com/windowsexperience/2017/05/17/announcing-windows-10-insider-preview-build-16199-pc-build-15215-mobile/#bDqf2Ah3Gd7FM66g.97) oder höher ausführen, um sekundäre Kacheln in Ihrer Desktopanwendung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="af35b-106">**PRERELEASE | Requires Fall Creators Update**: You must be running [Insider build 16199](https://blogs.windows.com/windowsexperience/2017/05/17/announcing-windows-10-insider-preview-build-16199-pc-build-15215-mobile/#bDqf2Ah3Gd7FM66g.97) or higher to use secondary tiles from your desktop application.</span></span>

![Screenshot von sekundären Kacheln](images/secondarytiles.png)

<span data-ttu-id="af35b-108">Das Hinzufügen einer sekundären Kachel von WPF oder WinForms ähnelt einer reinen UWP-App.</span><span class="sxs-lookup"><span data-stu-id="af35b-108">Adding a secondary tile from your WPF or WinForms application is very similar to a pure UWP app.</span></span> <span data-ttu-id="af35b-109">Der einzige Unterschied besteht darin, dass Sie das Hauptfenster-Handle (HWND) angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="af35b-109">The only difference is that you must specify your main window handle (HWND).</span></span> <span data-ttu-id="af35b-110">Der Grund dafür ist, dass Windows beim Anheften einer Kachel ein modales Dialogfeld anzeigt, das den Benutzer auffordert zu bestätigen, dass er die Kachel anheften möchte.</span><span class="sxs-lookup"><span data-stu-id="af35b-110">This is because when pinning a tile, Windows displays a modal dialog asking the user to confirm whether they would like to pin the tile.</span></span> <span data-ttu-id="af35b-111">Wenn die Desktop-Anwendung das SecondaryTile-Objekt nicht mit dem Besitzerfenster konfigurieren, kann Windows nicht feststellen, wo das Dialogfeld gezeichnet werden soll und der Vorgang schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="af35b-111">If the desktop application doesn't configure the SecondaryTile object with the owner window, Windows doesn't know where to draw the dialog and the operation will fail.</span></span>


## <a name="package-your-app-with-desktop-bridge"></a><span data-ttu-id="af35b-112">Packen Sie Ihre App mit der Desktop-Brücke</span><span class="sxs-lookup"><span data-stu-id="af35b-112">Package your app with Desktop Bridge</span></span>

<span data-ttu-id="af35b-113">Wenn Sie Ihre App nicht mit der Desktop-Brücke gepackt haben [müssen Sie dies zuerst durchführen](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root), um alle UWP-APIs verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="af35b-113">If you have not packaged your app with the Desktop Bridge, [you must do so first](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root) before you can use any UWP APIs.</span></span>


## <a name="enable-access-to-iinitializewithwindow-interface"></a><span data-ttu-id="af35b-114">Aktivieren des Zugriffs auf die IInitializeWithWindow-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="af35b-114">Enable access to IInitializeWithWindow interface</span></span>

<span data-ttu-id="af35b-115">Wenn die Anwendung in einer verwalteten Sprache wie z.B. C# oder Visual Basic geschrieben wurde, deklarieren Sie die IInitializeWithWindow-Schnittstelle im App-Code wie im folgenden C#-Beispiel mit dem [ComImport](https://msdn.microsoft.com/library/system.runtime.interopservices.comimportattribute.aspx) und dem Guid-Attribut.</span><span class="sxs-lookup"><span data-stu-id="af35b-115">If your application is written in a managed language such as C# or Visual Basic, declare the IInitializeWithWindow interface in your app's code with the [ComImport](https://msdn.microsoft.com/library/system.runtime.interopservices.comimportattribute.aspx) and Guid attribute as shown in the following C# example.</span></span> <span data-ttu-id="af35b-116">In diesem Beispiel wird davon ausgegangen, dass Ihre Codedatei über eine using-Anweisung für den System.Runtime.InteropServices-Namespace verfügt.</span><span class="sxs-lookup"><span data-stu-id="af35b-116">This example assumes that your code file has a using statement for the System.Runtime.InteropServices namespace.</span></span>

```csharp
[ComImport]
[Guid("3E68D4BD-7135-4D10-8018-9FB6D9F33FA1")]
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IInitializeWithWindow
{
    void Initialize(IntPtr hwnd);
}
```

<span data-ttu-id="af35b-117">Wenn Sie alternativ C++ verwenden, fügen Sie im Code einen Verweis auf die Headerdatei **shobjidl.h** hinzu.</span><span class="sxs-lookup"><span data-stu-id="af35b-117">Alternatively, if you are using C++, add a reference to the **shobjidl.h** header file in your code.</span></span> <span data-ttu-id="af35b-118">Diese Headerdatei enthält die Deklaration der *IInitializeWithWindow*-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="af35b-118">This header file contains the declaration of the *IInitializeWithWindow* interface.</span></span>


## <a name="initialize-the-secondary-tile"></a><span data-ttu-id="af35b-119">Initialisieren Sie die sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="af35b-119">Initialize the secondary tile</span></span>

<span data-ttu-id="af35b-120">Initialisieren Sie ein neues sekundäres Kachelobjekt genau wie in einer normalen UWP-App.</span><span class="sxs-lookup"><span data-stu-id="af35b-120">Initialize a new secondary tile object exactly like you would with a normal UWP app.</span></span> <span data-ttu-id="af35b-121">Weitere Informationen zum Erstellen und Anheften von Sekundärkacheln finden Sie unter [Sekundäre Kacheln anheften](tiles-and-notifications-secondary-tiles-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="af35b-121">To learn more about creating and pinning secondary tiles, see [Pin secondary tiles](tiles-and-notifications-secondary-tiles-pinning.md).</span></span>

```csharp
// Initialize the tile with required arguments
SecondaryTile tile = new SecondaryTile(
    "myTileId5391",
    "Display name",
    "myActivationArgs",
    new Uri("ms-appx:///Assets/Square150x150Logo.png"),
    TileSize.Default);
```


## <a name="assign-the-window-handle"></a><span data-ttu-id="af35b-122">Zuweisen des Fensterhandles</span><span class="sxs-lookup"><span data-stu-id="af35b-122">Assign the window handle</span></span>

<span data-ttu-id="af35b-123">Dies ist der wichtigste Schritt für Desktopanwendung.</span><span class="sxs-lookup"><span data-stu-id="af35b-123">This is the key step for desktop applications.</span></span> <span data-ttu-id="af35b-124">Wandeln Sie das Objekt in ein [IInitializeWithWindow](https://msdn.microsoft.com/library/windows/desktop/hh706981.aspx)-Objekt um.</span><span class="sxs-lookup"><span data-stu-id="af35b-124">Cast the object to an [IInitializeWithWindow](https://msdn.microsoft.com/library/windows/desktop/hh706981.aspx) object.</span></span> <span data-ttu-id="af35b-125">Rufen Sie dann die [IInitializeWithWindow.Initialize](https://msdn.microsoft.com/library/windows/desktop/hh706982.aspx)-Methode auf, und übergeben Sie das Handle des Fensters, das der Besitzer aller modalen Dialoge sein soll.</span><span class="sxs-lookup"><span data-stu-id="af35b-125">Then, call the [IInitializeWithWindow.Initialize](https://msdn.microsoft.com/library/windows/desktop/hh706982.aspx) method, and pass the handle of the window that you want to be the owner for the modal dialog.</span></span> <span data-ttu-id="af35b-126">Im folgenden C#-Beispiel wird gezeigt, wie das Handle des Hauptfensters der App an die Methode übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="af35b-126">The following C# example shows how to pass the handle of your app’s main window to the method.</span></span>

```csharp
// Assign the window handle
IInitializeWithWindow initWindow = (IInitializeWithWindow)(object)tile;
initWindow.Initialize(System.Diagnostics.Process.GetCurrentProcess().MainWindowHandle);
```


## <a name="pin-the-tile"></a><span data-ttu-id="af35b-127">Anheften der Kachel</span><span class="sxs-lookup"><span data-stu-id="af35b-127">Pin the tile</span></span>

<span data-ttu-id="af35b-128">Fordern Sie schließlich das Anheften der Kachel wie bei einer normalen UWP-App an.</span><span class="sxs-lookup"><span data-stu-id="af35b-128">Finally, request to pin the tile as you would a normal UWP app.</span></span>

```csharp
// Pin the tile
bool isPinned = await tile.RequestCreateAsync();

// TODO: Update UI to reflect whether user can now either unpin or pin
```


## <a name="resources"></a><span data-ttu-id="af35b-129">Resources</span><span class="sxs-lookup"><span data-stu-id="af35b-129">Resources</span></span>

* [<span data-ttu-id="af35b-130">Vollständiges Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="af35b-130">Full code sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SecondaryTileSample)
* [<span data-ttu-id="af35b-131">Übersicht über sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="af35b-131">Secondary tiles overview</span></span>](tiles-and-notifications-secondary-tiles.md)
* [<span data-ttu-id="af35b-132">Sekundäre Kacheln anheften (UWP)</span><span class="sxs-lookup"><span data-stu-id="af35b-132">Pin secondary tiles (UWP)</span></span>](tiles-and-notifications-secondary-tiles-pinning.md)
* [<span data-ttu-id="af35b-133">Desktop-Brücke</span><span class="sxs-lookup"><span data-stu-id="af35b-133">Desktop Bridge</span></span>](https://developer.microsoft.com/en-us/windows/bridges/desktop)
* [<span data-ttu-id="af35b-134">Desktop-Brücke: Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="af35b-134">Desktop Bridge code samples</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples)