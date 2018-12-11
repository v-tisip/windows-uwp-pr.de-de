---
description: Hier finden Sie einen Designleitfaden und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App. Sie finden mehr als 45leistungsstarke Steuerelemente für die Verwendung mit Ihrer App.
title: UWP-Steuerelemente und -Muster – Entwicklung von Windows-Apps
keywords: UWP-Steuerelemente, Benutzeroberfläche, App-Steuerelemente
label: Controls & patterns
template: detail.hbs
ms.date: 11/16/2017
ms.topic: article
ms.assetid: ce2e611c-c419-4a14-9095-b88ac711d1b8
ms.localizationpriority: medium
ms.openlocfilehash: c2f1a2b5ae514222ed6ef06cc7099a0261747dbc
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8877461"
---
# <a name="controls-and-patterns-for-uwp-apps"></a>Steuerelemente und Muster für UWP-Apps
 

In der UWP-App-Entwicklung ist ein <i>Steuerelement</i> ein UI-Element, das Inhalte anzeigt oder Interaktionen ermöglicht. Steuerelemente sind die Bausteine der Benutzeroberfläche. Ein <i>Muster</i> ist eine Anleitung zum Kombinieren verschiedener Steuerelemente, um etwas Neues zu erstellen.

Wir stellen Ihnen mehr als 45Steuerelemente bereit, angefangen bei einfachen Schaltflächen bis hin zu leistungsstarken Datensteuerelementen wie der Rasteransicht.  Diese Steuerelemente sind Teil des Fluent Design-Systems und können Ihnen bei der Erstellung einer ansprechenden, skalierbaren UI helfen, die auf allen Geräten und Bildschirmgrößen großartig aussieht. 

Die Artikel in diesem Abschnitt enthalten Designrichtlinien und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App. 

## <a name="intro"></a>Einführung

Allgemeine Anweisungen und Codebeispiele für das Hinzufügen und Formatieren von Steuerelementen in XAML und C#.

:::row:::
    :::column:::
      <p><b><a href="controls-and-events-intro.md">Hinzufügen von Steuerelementen und Verarbeiten von Ereignissen</a></b> <br/>
Es gibt 3 wichtige Schritte, die Sie ausführen müssen, um Ihrer App Steuerelemente hinzuzufügen: das Hinzufügen eines Steuerelements zu Ihrer App-UI, das Festlegen der Eigenschaften für das Steuerelement und das Hinzufügen von Code zu den Ereignishandlern des Steuerelements, sodass dieses eine Aktion ausführt.</p>
    :::column-end:::
    :::column:::
      <p><b><a href="xaml-styles.md">Formatieren von Steuerelementen</a></b> <br/>
Das XAML-Framework bietet zahlreiche Anpassungsmöglichkeiten für die App-Darstellung. Sie können mit Formaten die Steuerelementeigenschaften festlegen und diese Einstellungen dann für andere Steuerelemente wiederverwenden, um ein einheitliches Erscheinungsbild zu erzielen.</p>
    :::column-end:::
:::row-end:::

## <a name="get-the-windows-ui-library"></a>Abrufen der Windows-UI-Bibliothek
Einige Steuerelemente sind nur verfügbar, in der Windows-UI-Bibliothek. Um es zu erhalten, finden Sie in der [UI-Bibliothek für Windows-Übersicht und Installation-Anweisungen](/uwp/toolkits/winui/).

## <a name="alphabetical-index"></a>Alphabetischer Index 

Detaillierte Informationen zu bestimmten Steuerelementen und Mustern. (Eine nach Funktionen sortierte Liste finden Sie unter <a href="controls-by-function.md">Index der Steuerelemente nach Funktion</a>.)

<div style="column-count: 2; column-gap: 40px; margin-top: 40px;" >
<ul style="margin-top: 0px; padding-top: 0px; list-style-type: none;">
<li style="list-style-type: none;"><a href="auto-suggest-box.md">Feld mit automatischen Vorschlägen</a></li>

<li style="list-style-type: none;"><a href="app-bars.md">Balken</a></li>

<li style="list-style-type: none;"><a href="buttons.md">Schaltflächen</a></li>

<li style="list-style-type: none;"><a href="checkbox.md">Kontrollkästchen </a></li>

<li style="list-style-type: none;"><a href="color-picker.md">Farbwähler</a></li>

<li style="list-style-type: none;"><a href="contact-card.md">Visitenkarte</a></li>

<li style="list-style-type: none;"><a href="date-and-time.md">Datums- und Uhrzeitsteuerelemente</a></li>

<li style="list-style-type: none;"><a href="dialogs-and-flyouts/index.md">Dialogfelder und Flyouts</a></li>

<li style="list-style-type: none;"><a href="flipview.md">Flip-Ansicht</a></li>

<li style="list-style-type: none;"><a href="forms.md">Formulare</a></li>

<li style="list-style-type: none;"><a href="hub.md">Hub</a></li>

<li style="list-style-type: none;"><a href="hyperlinks.md">Hyperlinks</a></li>

<li style="list-style-type: none;"><a href="images-imagebrushes.md">Bilder und Bildpinsel</a></li>

<li style="list-style-type: none;"><a href="inking-controls.md">Steuerelemente für Freihandeingaben</a></li>

<li style="list-style-type: none;"><a href="lists.md">Listen</a></li>

<li style="list-style-type: none;"><a href="../../maps-and-location/controls-map.md">Kartensteuerelement</a></li>

<li style="list-style-type: none;"><a href="master-details.md">Master/Details</a></li>

<li style="list-style-type: none;"><a href="media-playback.md">Medienwiedergabe</a></li>

<li style="list-style-type: none;"><a href="menus.md">Menüs und Kontextmenüs</a></li>

<li style="list-style-type: none;"><a href="navigationview.md">Navigationsansicht</a></li>

<li style="list-style-type: none;"><a href="person-picture.md">Bild einer Person</a></li>

<li style="list-style-type: none;"><a href="pivot.md">Pivot</a></li>

<li style="list-style-type: none;"><a href="progress-controls.md">Statussteuerelemente</a></li>

<li style="list-style-type: none;"><a href="radio-button.md">Optionsschaltfläche</a></li>

<li style="list-style-type: none;"><a href="rating.md">Bewertungssteuerelement</a></li>

<li style="list-style-type: none;"><a href="scroll-controls.md">Steuerelemente für Bildlauf und Schwenken</a></li>

<li style="list-style-type: none;"><a href="search.md">Suche</a></li>

<li style="list-style-type: none;"><a href="semantic-zoom.md">Semantischer Zoom</a></li>

<li style="list-style-type: none;"><a href="shapes.md">Formen</a></li>

<li style="list-style-type: none;"><a href="slider.md">Schieberegler</a></li>

<li style="list-style-type: none;"><a href="split-view.md">Geteilte Ansicht</a></li>

<li style="list-style-type: none;"><a href="text-controls.md">Textsteuerelemente</a></li>


<li style="list-style-type: none;"><a href="toggles.md">Umschalten</a></li>
<li style="list-style-type: none;"><a href="tooltips.md">QuickInfos</a></li>

<li style="list-style-type: none;"><a href="tree-view.md">Strukturansicht</a></li>

<li style="list-style-type: none;"><a href="web-view.md">Webansicht</a></li>
</ul>
</div>

## <a name="xaml-controls-gallery"></a>XAML-Steuerelementekatalog

Rufen Sie die _XAML-Steuerelementekatalog_-App aus dem Microsoft Store ab, um diese Steuerelemente und das Fluent Design-System in Aktion zu sehen. Die App ist eine interaktive Ergänzung zu dieser Website. Wenn Sie sie installiert haben, können Sie Links auf einzelnen Steuerungsseiten verwenden, um die App zu starten und das Steuerelement in Aktion zu sehen.

<a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a>

<a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a>

<img src="images/xaml-controls-gallery.png" alt="XAML Controls Gallery screen" />

## <a name="additional-controls"></a>Zusätzliche Steuerelemente

Zusätzliche Steuerelemente für die UWP-Entwicklung werden von Unternehmen wie <a href="http://www.telerik.com/">Telerik</a>, <a href="https://www.syncfusion.com/products/uwp">SyncFusion</a>, <a href="https://www.devexpress.com/Products/NET/Controls/Win10Apps/">DevExpress</a>, <a href="http://www.infragistics.com/products/universal-windows-platform">Infragistics</a>, <a href="https://www.componentone.com/Studio/Platform/UWP">ComponentOne</a> und <a href="http://www.actiprosoftware.com/products/controls/universal">ActiPro</a> bereitgestellt. Diese Steuerelemente bieten zusätzliche Unterstützung für Unternehmen und .NET-Entwickler, indem sie die Steuerelemente des Standardsystem mit benutzerdefinierten Steuerelementen und Diensten erweitern.  

Wenn Sie mehr über diese Steuerelemente erfahren möchten, sehen Sie sich das Beispiel <a href="https://github.com/Microsoft/Windows-appsample-customers-orders-database">Customer Orders Database</a> in GitHub an. In diesem Beispiel werden die Steuerelemente Datenrasten und Dateneingabe von Telerik verwendet, die Teil der UI für die UWP-Suite sind. Die UI für die UWP-Suite besteht aus einer Sammlung von über 20 Steuerelementen, die als Open Source-Projekt über die .NET-Foundation verfügbar sind.
