---
author: QuinnRadich
title: "Neues in der Vorschauversion des Windows 10 Creators Update – Entwicklung von UWP-Apps"
description: "Informieren Sie sich vorab über das Windows 10 Creators Update, das weiterhin Tools, Features und Umgebungen bereitstellt, die von der universellen Windows-Plattform unterstützt werden."
ms.assetid: 27a9ce65-c811-4f79-bf65-3493337199c8
keywords: Neuigkeiten, Neues, Vorschauversion, Update, Updates, Features, neu, Windows 10, Creators
ms.author: quradic
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: 29a888286062c59ea257cf0e43d3598d847a6588
ms.openlocfilehash: d36b84299b8e469624cef54f89c94744f3f4ae83
ms.lasthandoff: 02/08/2017

---

# <a name="whats-new-in-the-windows-10-creators-update-preview"></a>Neues in der Vorschauversion des Windows 10 Creators Update

Das Windows 10 Creators Update wird auch weiterhin Tools, Features und Umgebungen bereitstellen, die von der universellen Windows-Plattform unterstützt werden. Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows 10 können Sie entweder [eine neue universelle Windows-App erstellen](https://msdn.microsoft.com/library/windows/apps/bg124288) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](https://msdn.microsoft.com/library/windows/apps/mt238321) vertraut machen.

Diese Features werden erst zur Veröffentlichung des Windows 10 Creators Update öffentlich verfügbar gemacht. Derzeit können sie lediglich in Vorschaubuilds verwendet werden, die [Windows-Insidern](https://insider.windows.com/) vorbehalten sind. Diese Seite wird zukünftig möglicherweise mit Informationen zu weiteren neuen Features aktualisiert, wenn weitere Dokumentation verfügbar wird.

Weitere Informationen zu den Highlight-Features zu diesem und anderen Windows-Updates finden Sie unter [der Windows Developer Day-Website](https://developer.microsoft.com/en-us/windows/projects/campaigns/windows-developer-day) und [Die Highlights in Windows 10](http://go.microsoft.com/fwlink/?LinkId=823181). Darüber hinaus finden Sie unter [Windows Developer Platform-Features](https://developer.microsoft.com/en-us/windows/platform/features) für eine grobe Übersicht über die früheren und zukünftigen neuen Features.

Feature | Beschreibung
 :---- | :----
**Modernisierte UWP-Dokumente** | Die Dokumentation zu der universellen Windows-Plattform ist jetzt auf „docs.microsoft.com“ verfügbar. Sie können jetzt problemlos Codebeispiele einreichen, Ihr technische Fachwissen einbringen und Feedback bereitstellen. Eine Anleitung finden Sie in diesem [One Dev Minute-Video.](https://channel9.msdn.com/Blogs/One-Dev-Minute/Modernizing-the-Windows-UWP-Docs)
**Aktualisierungsbeispiel für die Datenbank der Kundenaufträge** | Das [Datenbank der Kundenaufträge](https://github.com/Microsoft/Windows-appsample-customers-orders-database)-Beispiel auf GitHub wurde aktualisiert, um sicherzustellen, dass das Rastersteuerelement und die Validierung der Dateneingabe von Telerik verwendet werden, die beide in deren Benutzeroberfläche für die UWP-Suite integriert sind. Die UI für die UWP-Suite besteht aus einer Sammlung von über 20 Steuerelementen, die als Open Source-Projekt über die .NET-Foundation verfügbar sind.
**Freihandeingabenanalyse** | Windows Ink kann jetzt von Freihandstrichen als Schrift oder als Zeichenstriche kategorisieren und Text, Formen und grundlegende Layoutstrukturen erkennen.
**Projekt „Rome”-SDK für Android** | Das Projekt „Rome”-Feature für UWP ist jetzt für die Android-Plattform verfügbar. Jetzt können Sie von Windows- *und* von Android-Geräten aus Apps remote starten und mit Aufgaben auf allen Ihren Windows-Geräten fortfahren. Informationen zu ersten Schritten finden Sie in dem offiziellen [Projekt „Rome“-Repository für die plattformübergreifenden Szenarien](https://github.com/Microsoft/project-rome).
**XAML-Steuerelemente** | ContentDialog verfügt jetzt über drei Schaltflächen: primäre, sekundäre und Schließfeld. Sie können auch eine der Schaltflächen als Standardaktion festlegen. <br> Verwenden Sie die ShowAsMonochrome-Eigenschaft, um die Bitmapsymbole in nur einer Farbe oder vollständig farbig anzuzeigen. <br> Verwenden Sie das neue SelectionChangedTrigger, um zu ändern, wie das Kombinationsfeld Auswahl mithilfe der Tastatur behandelt. <br> Neue PrepareConnectedAnimation- und TryStartConnectedAnimationAsync-APIs zu ListViewBase vereinfachen mit Listen- und Rasteransichten die Verwendung von verbundenen Animationen. <br> Verwenden Sie die neue Icon-Eigenschaft, um einem MenuFlyoutItem oder einem MenuFlyoutSubItem ein Symbol hinzufügen. <br> Verwenden Sie die Klasse „SvgImageSource“, um in XAML ein SVG-Bild hinzuzufügen. <br> Verwenden Sie die Klasse „LoadedImageSource“, um in XAML eine einer Kompositionsoberfläche hinzuzufügen. <br> Verwenden Sie die Klasse „XAMLLight“ und die UIElement.Lights-Eigenschaft, um in XAML CompositionLight-Effekte hinzuzufügen. <br> Verwenden Sie die XamlCompositionBrushBase, um in XAML Kompositionspinsel zu verwenden.

