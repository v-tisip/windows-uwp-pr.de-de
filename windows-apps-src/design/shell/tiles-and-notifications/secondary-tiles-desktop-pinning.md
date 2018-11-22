---
author: vladimp
Description: Windows desktop applications can pin secondary tiles thanks to the Desktop Bridge!
title: Sekundäre Kacheln von der Desktopanwendung anheften
label: Pin secondary tiles from desktop application
template: detail.hbs
ms.author: mijacobs
ms.date: 05/25/2017
ms.topic: article
keywords: Windows10, Desktop-Brücke, sekundäre Kacheln, anheften, Anheften, Schnellstart, Codebeispiel, Beispiel, Sekundärkachel, Desktopanwendung, Win32, Winforms, WPF
ms.localizationpriority: medium
ms.openlocfilehash: 44e37b47e22d10f509afd5d7503fa8f7a43ab365
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7572726"
---
# <a name="pin-secondary-tiles-from-desktop-application"></a>Sekundäre Kacheln von der Desktopanwendung anheften


Dank der [Desktop-Brück](https://developer.microsoft.com/windows/bridges/desktop) können Windows-Desktopanwendung (wie Win32, Windows Forms und WPF) sekundäre Kacheln anheften.

![Screenshot von sekundären Kacheln](images/secondarytiles.png)

> [!IMPORTANT]
> **Erfordert das Fall Creators Update**: Sie müssen als Ziel das SDK 16299 angeben und Build 16299 oder höher ausführen, um sekundäre Kacheln von Desktop-Brücke-Apps anzuheften.

Das Hinzufügen einer sekundären Kachel aus Ihrer WPF- oder WinForms-Anwendung ist einer reinen UWP-App sehr ähnlich. Der einzige Unterschied besteht darin, dass Sie das Hauptfenster-Handle (HWND) angeben müssen. Der Grund dafür ist, dass Windows beim Anheften einer Kachel ein modales Dialogfeld anzeigt, das den Benutzer auffordert zu bestätigen, dass er die Kachel anheften möchte. Wenn die Desktop-Anwendung das SecondaryTile-Objekt nicht mit dem Besitzerfenster konfigurieren, kann Windows nicht feststellen, wo das Dialogfeld gezeichnet werden soll und der Vorgang schlägt fehl.


## <a name="package-your-app-with-desktop-bridge"></a>Packen Sie Ihre App mit der Desktop-Brücke

Wenn Sie Ihre App nicht mit der Desktop-Brücke gepackt haben [müssen Sie dies zuerst durchführen](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root), um alle UWP-APIs verwenden zu können.


## <a name="enable-access-to-iinitializewithwindow-interface"></a>Aktivieren des Zugriffs auf die IInitializeWithWindow-Schnittstelle

Wenn die Anwendung in einer verwalteten Sprache wie z.B. C# oder Visual Basic geschrieben wurde, deklarieren Sie die IInitializeWithWindow-Schnittstelle im App-Code wie im folgenden C#-Beispiel mit dem [ComImport](https://msdn.microsoft.com/library/system.runtime.interopservices.comimportattribute.aspx) und dem Guid-Attribut. In diesem Beispiel wird davon ausgegangen, dass Ihre Codedatei über eine using-Anweisung für den System.Runtime.InteropServices-Namespace verfügt.

```csharp
[ComImport]
[Guid("3E68D4BD-7135-4D10-8018-9FB6D9F33FA1")]
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IInitializeWithWindow
{
    void Initialize(IntPtr hwnd);
}
```

Wenn Sie alternativ C++ verwenden, fügen Sie im Code einen Verweis auf die Headerdatei **shobjidl.h** hinzu. Diese Headerdatei enthält die Deklaration der *IInitializeWithWindow*-Schnittstelle.


## <a name="initialize-the-secondary-tile"></a>Initialisieren Sie die sekundäre Kachel

Initialisieren Sie ein neues sekundäres Kachelobjekt genau wie in einer normalen UWP-App. Weitere Informationen zum Erstellen und Anheften von Sekundärkacheln finden Sie unter [Sekundäre Kacheln anheften](secondary-tiles-pinning.md).

```csharp
// Initialize the tile with required arguments
SecondaryTile tile = new SecondaryTile(
    "myTileId5391",
    "Display name",
    "myActivationArgs",
    new Uri("ms-appx:///Assets/Square150x150Logo.png"),
    TileSize.Default);
```


## <a name="assign-the-window-handle"></a>Zuweisen des Fensterhandles

Dies ist der wichtigste Schritt für Desktopanwendung. Wandeln Sie das Objekt in ein [IInitializeWithWindow](https://msdn.microsoft.com/library/windows/desktop/hh706981.aspx)-Objekt um. Rufen Sie dann die [IInitializeWithWindow.Initialize](https://msdn.microsoft.com/library/windows/desktop/hh706982.aspx)-Methode auf, und übergeben Sie das Handle des Fensters, das der Besitzer aller modalen Dialoge sein soll. Im folgenden C#-Beispiel wird gezeigt, wie das Handle des Hauptfensters der App an die Methode übergeben wird.

```csharp
// Assign the window handle
IInitializeWithWindow initWindow = (IInitializeWithWindow)(object)tile;
initWindow.Initialize(System.Diagnostics.Process.GetCurrentProcess().MainWindowHandle);
```


## <a name="pin-the-tile"></a>Anheften der Kachel

Fordern Sie schließlich das Anheften der Kachel wie bei einer normalen UWP-App an.

```csharp
// Pin the tile
bool isPinned = await tile.RequestCreateAsync();

// TODO: Update UI to reflect whether user can now either unpin or pin
```


## <a name="send-tile-notifications"></a>Senden von Kachelbenachrichtigungen

> [!IMPORTANT]
> **Erfordert April2018 Version 17134.81 oder höher**: Sie müssen Build 17134.81 oder höher ausführen, um Kachel- oder Signalbenachrichtigungen für sekundäre Kacheln von Desktop-Brücke-Apps zu senden. Vor diesem x.81-Wartungsupdate würde beim Senden von Kachel- oder Signalbenachrichtigungen für sekundäre Kacheln von Desktop-Brücke-Apps die Ausnahme 0x80070490 *Element nicht gefunden* auftreten.

Das Senden von Kachel- oder Signalbenachrichtigungen ist identisch wie bei UWP-Apps. Weitere Informationen finden Sie unter [Senden einer lokalen Kachelbenachrichtigung](sending-a-local-tile-notification.md).


## <a name="resources"></a>Ressourcen

* [Vollständiges Codebeispiel](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SecondaryTileSample)
* [Übersicht über sekundäre Kacheln](secondary-tiles.md)
* [Sekundäre Kacheln anheften (UWP)](secondary-tiles-pinning.md)
* [Desktop-Brücke](https://developer.microsoft.com/windows/bridges/desktop)
* [Desktop-Brücke: Codebeispiele](https://github.com/Microsoft/DesktopBridgeToUWP-Samples)