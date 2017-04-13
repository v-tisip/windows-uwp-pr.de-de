---
description: "In diesem Artikel erfahren Sie, wie Sie Ihrer UWP-App (Universelle Windows-Plattform) Drag & Drop hinzufügen."
title: Drag & Drop
ms.assetid: A15ED2F5-1649-4601-A761-0F6C707A8B7E
author: awkoren
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: 84f78d43a0d9a34b8ba992a2357f08ad374b32d1
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="drag-and-drop"></a>Drag & Drop

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]


In diesem Artikel erfahren Sie, wie Sie Ihrer Universellen Windows-Plattform (UWP)-App Drag&Drop hinzufügen. Drag&Drop ist ein klassisches, natürliches Interaktionsmodell für Inhalte wie Bilder und Dateien. Nach der Implementierung stehen Drag & Drop-Vorgänge für sämtliche Richtungen (App zu App, App zu Desktop und Desktop zu App) zur Verfügung.

## <a name="set-valid-areas"></a>Festlegen gültiger Bereiche

Verwenden Sie die Eigenschaften [**AllowDrop**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.AllowDrop) und [**CanDrag**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.CanDrag), um die Bereiche der App festzulegen, die für Drag & Drop infrage kommen.

Das folgende Markup veranschaulicht, wie Sie mithilfe von [**AllowDrop**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.AllowDrop) in XAML einen bestimmten Bereich der App als gültig für Dropvorgänge festlegen. Wenn ein Benutzer versucht, Elemente an anderer Stelle abzulegen, wird dies vom System nicht zugelassen. Wenn Benutzer die Möglichkeit haben sollen, Elemente an einer beliebigen Stelle Ihrer App abzulegen, legen Sie den gesamten Hintergrund als Dropziel fest.

[!code-xml[Main](./code/drag_drop/cs/MainPage.xaml#SnippetDropArea)]

Beim Ziehen sollten Sie in der Regel genau festlegen, was gezogen werden kann. Benutzer möchten meist nicht alle Elemente Ihrer App ziehen, sondern nur bestimmte Elemente wie beispielsweise Bilder. Nachfolgend sehen Sie, wie Sie [**CanDrag**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.CanDrag) mithilfe von XAML festlegen.

[!code-xml[Main](./code/drag_drop/cs/MainPage.xaml#SnippetDragArea)]

Sie müssen keine weiteren Aktionen durchführen, um das Ziehen zu ermöglichen, es sei denn, Sie möchten die Benutzeroberfläche anpassen (dies wird später in diesem Artikel behandelt). Das Ablegen erfordert einige weitere Schritte.

## <a name="handle-the-dragover-event"></a>Verarbeiten des DragOver-Ereignisses

Das [**DragOver**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.DragOver)-Ereignis wird ausgelöst, wenn ein Benutzer ein Element über Ihre App gezogen, aber noch nicht abgelegt hat. In diesem Handler müssen Sie mithilfe der [**AcceptedOperation**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.DragEventArgs.AcceptedOperation)-Eigenschaft angeben, welche Art von Vorgängen Ihre App unterstützt. Kopieren ist der häufigste Vorgang.

[!code-cs[Main](./code/drag_drop/cs/MainPage.xaml.cs#SnippetGrid_DragOver)]

## <a name="process-the-drop-event"></a>Verarbeiten des Dropereignisses

Das [**Drop**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.Drop)-Ereignis tritt auf, wenn der Benutzer Elemente in einem gültigen Dropbereich ablegt. Verarbeiten Sie dieses Ereignis mit der [**DataView**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.DragEventArgs.DataView)-Eigenschaft.

Der Einfachheit halber wird im folgenden Beispiel angenommen, dass der Benutzer ein einzelnes Foto abgelegt hat und auf dieses zugreift. In der Praxis können Benutzer mehrere Elemente unterschiedlicher Formate gleichzeitig ablegen. Ihre App sollte diese Möglichkeit behandeln, indem sie überprüft, welche Dateitypen abgelegt wurden, sie entsprechend verarbeitet und den Benutzer benachrichtigt, wenn er versucht, eine von der App nicht unterstützte Aktion auszuführen.

[!code-cs[Main](./code/drag_drop/cs/MainPage.xaml.cs#SnippetGrid_Drop)]

## <a name="customize-the-ui"></a>Anpassen der Benutzeroberfläche

Das System bietet eine Standardbenutzeroberfläche für Drag&Drop. Sie können jedoch auch verschiedene Teile der Benutzeroberfläche anpassen, indem Sie benutzerdefinierte Beschriftungen und Symbole festlegen oder angeben, dass keine Benutzeroberfläche angezeigt werden soll. Verwenden Sie zum Anpassen der Benutzeroberfläche die [**DragEventArgs.DragUIOverride**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.DragEventArgs.DragUIOverride)-Eigenschaft.

[!code-cs[Main](./code/drag_drop/cs/MainPage.xaml.cs#SnippetGrid_DragOverCustom)]

## <a name="open-a-context-menu-on-an-item-you-can-drag-with-touch"></a>Öffnen eines Kontextmenüs für ein Element, das per Toucheingabe gezogen werden kann

Bei der Toucheingabe erfordern das Ziehen eines [**UI-Elements**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement) und das Öffnen des Kontextmenüs ähnliche Touchgesten. Beide beginnen mit Drücken und Halten. Hier erfahren Sie, wie das System zwischen den beiden Aktionen für Elemente unterscheidet, die beide unterstützen: 

* Wenn der Benutzer ein Element drückt und hält und es innerhalb von 500Millisekunden zu ziehen beginnt, wird es gezogen. Das Kontextmenü wird nicht angezeigt. 
* Wenn der Benutzer drückt und hält, jedoch nicht innerhalb von 500Millisekunden zieht, wird das Kontextmenü geöffnet. 
* Wenn der Benutzer bei geöffnetem Kontextmenü versucht, das Element zu ziehen (ohne den Finger anzuheben), wird das Kontextmenü geschlossen und das Ziehen gestartet.

## <a name="designate-an-item-in-a-listview-or-gridview-as-a-folder"></a>Festlegen eines Elements in einer ListView oder GridView als Ordner

Sie können ein [**ListViewItem**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.ListViewItem) oder [**GridViewItem**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.GridViewItem) als Ordner festlegen. Dies ist besonders hilfreich für TreeView- und Datei-Explorer-Szenarien. Setzen Sie hierzu für das Element die [**AllowDrop**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.AllowDrop)-Eigenschaft auf **True**. 

Das System zeigt automatisch die entsprechenden Animationen zum Ablegen in einen Ordner anstelle eines Nicht-Ordner-Elements an. Der App-Code muss für das Ordnerelement (sowie das Nicht-Ordner-Element) auch weiterhin das Ereignis [**Drop**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.Drop) beinhalten, damit die Datenquelle aktualisiert und das abgelegte Element im Zielordner hinzugefügt wird.

## <a name="see-also"></a>Weitere Informationen

* [App-zu-App-Kommunikation](index.md)
* [AllowDrop](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.allowdrop.aspx)
* [CanDrag](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.candrag.aspx)
* [DragOver](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.dragover.aspx)
* [AcceptedOperation](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.drageventargs.acceptedoperation.aspx)
* [DataView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.drageventargs.dataview.aspx)
* [DragUIOverride](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.drageventargs.draguioverride.aspx)
* [Drop](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.drop.aspx)
* [IsDragSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isdragsource.aspx)
