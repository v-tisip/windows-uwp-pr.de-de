---
description: "Hier finden Sie einen Designleitfaden und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App. Sie finden mehr als 45 leistungsstarke Steuerelemente für die Verwendung mit Ihrer App."
title: "UWP-Steuerelemente und -Muster – Entwicklung von Windows-Apps"
author: mijacobs
keywords: "UWP-Steuerelemente, Benutzeroberfläche, App-Steuerelemente"
label: Controls & patterns
template: detail.hbs
ms.author: mijacobs
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.assetid: ce2e611c-c419-4a14-9095-b88ac711d1b8
translationtype: Human Translation
ms.sourcegitcommit: 412a3f70861c6cd1bbf003fe0bd78c8547a5f3f8
ms.openlocfilehash: 7b525267c8f4d24af95f6d41d46d33a3adf10f8f
ms.lasthandoff: 02/08/2017

---
# <a name="controls-and-patterns-for-uwp-apps"></a>Steuerelemente und Muster für UWP-Apps
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

In der UWP-App-Entwicklung ist ein <i>Steuerelement</i> ein UI-Element, das Inhalte anzeigt oder Interaktionen ermöglicht. Steuerelemente sind die Bausteine der Benutzeroberfläche. Wir stellen Ihnen mehr als 45 Steuerelemente bereit, angefangen bei einfachen Schaltflächen bis hin zu leistungsstarken Datensteuerelementen wie der Rasteransicht. Ein <i>Muster</i> ist eine Anleitung zum Kombinieren verschiedener Steuerelemente, um etwas Neues zu erstellen.

Die Artikel in diesem Abschnitt enthalten Designrichtlinien und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App. 

## <a name="intro"></a>Einführung

Allgemeine Anweisungen und Codebeispiele für das Hinzufügen und Formatieren von Steuerelementen in XAML und C#.

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b>[Hinzufügen von Steuerelementen und Verarbeiten von Ereignissen](controls-and-events-intro.md)</b> <br/>
Es gibt 3 wichtige Schritte, die Sie ausführen müssen, um Ihrer App Steuerelemente hinzuzufügen: das Hinzufügen eines Steuerelements zu Ihrer App-UI, das Festlegen der Eigenschaften für das Steuerelement und das Hinzufügen von Code zu den Ereignishandlern des Steuerelements, sodass dieses eine Aktion ausführt.</li>
</ul> 
</p>
  </div>
  <div class="side-by-side-content-right">
   <p><b>[Formatieren von Steuerelementen](styling-controls.md)</b> <br/>
Das XAML-Framework bietet zahlreiche Anpassungsmöglichkeiten für die App-Darstellung. Sie können mit Formaten die Steuerelementeigenschaften festlegen und diese Einstellungen dann für andere Steuerelemente wiederverwenden, um ein einheitliches Erscheinungsbild zu erzielen.</p>
  </div>
</div>
</div>

## <a name="alphabetical-index"></a>Alphabetischer Index 

Detaillierte Informationen zu bestimmten Steuerelementen und Mustern.

(Eine nach Funktionen sortierte Liste finden Sie unter [Index der Steuerelemente nach Funktion](controls-by-function.md).)

<div class="uwpd-list-of-links">
<ul>

<li>[Feld mit automatischen Vorschlägen](auto-suggest-box.md)</li>

<li>[Balken](app-bars.md)</li>

<li>[Schaltflächen](buttons.md)</li>

<li>[Kontrollkästchen ](checkbox.md)</li>

<li>[Steuerelemente für Datum und Uhrzeit](date-and-time.md)
<ul>

<li>[Kalenderdatumsauswahl](calendar-date-picker.md)</li>

<li>[Kalenderansicht](calendar-view.md)</li>

<li>[Datumsauswahl](date-picker.md)</li>

<li>[Zeitauswahl](time-picker.md)</li>
</ul>
</li>


<li>[Dialogfelder und Flyouts](dialogs.md)</li>

<li>[Flip-Ansicht](flipview.md)</li>

<li>[Hub](hub.md)</li>

<li>[Hyperlinks](hyperlinks.md)</li>

<li>[Bilder und Bildpinsel](images-imagebrushes.md)</li>

<li>[Listen](lists.md)</li>

<li>[Kartensteuerelement](../maps-and-location/controls-map.md)</li>

<li>[Master/Details](master-details.md)</li>

<li>[Medienwiedergabe](media-playback.md)
<ul>
<li>[Benutzerdefinierte Transportsteuerelemente](custom-transport-controls.md)</li>
</ul>
</li>

<li>[Menüs und Kontextmenüs](menus.md)</li>

<li>[Navigationsbereich](nav-pane.md)</li>

<li>[Statussteuerelemente](progress-controls.md)</li>

<li>[Optionsfeld](radio-button.md)</li>

<li>[Steuerelemente für Bildlauf und Schwenken](scroll-controls.md)</li>

<li>[Suche](search.md)</li>

<li>[Semantischer Zoom](semantic-zoom.md)</li>

<li>[Schieberegler](slider.md)</li>

<li>[Geteilte Ansicht](split-view.md)</li>

<li>[Registerkarten und Pivots](tabs-pivot.md)</li>

<li>[Textsteuerelemente](text-controls.md)
<ul>

<li>[Beschriftungen](labels.md)</li>

<li>[Kennwortfelder](password-box.md)</li>

<li>[Rich-Edit-Felder](rich-edit-box.md)</li>

<li>[Rich-Text-Blöcke](rich-text-block.md)</li>

<li>[Rechtschreibprüfung und Vorhersage](spell-checking-and-prediction.md)</li>

<li>[Textblock](text-block.md)</li>

<li>[Textfeld](text-box.md)</li>
</ul>
</li>



<li>[Kacheln, Badges und Benachrichtigungen](tiles-badges-notifications.md)
<ul>

<li>[Kacheln](tiles-and-notifications-creating-tiles.md)</li>

<li>[Adaptive Kacheln](tiles-and-notifications-create-adaptive-tiles.md)</li>

<li>[Adaptives Kachelschema](tiles-and-notifications-adaptive-tiles-schema.md)</li>

<li>[Objektrichtlinien](tiles-and-notifications-app-assets.md)</li>

<li>[Spezielle Kachelvorlagen](tiles-and-notifications-special-tile-templates-catalog.md)</li>

<li>[Adaptive und interaktive Popupbenachrichtigungen](tiles-and-notifications-adaptive-interactive-toasts.md)</li>

<li>[Signalbenachrichtigungen](tiles-and-notifications-badges.md)</li>

<li>[Visualisierungstool für Benachrichtigungen](tiles-and-notifications-notifications-visualizer.md)</li>

<li>[Methoden für die Benachrichtigungsübermittlung](tiles-and-notifications-choosing-a-notification-delivery-method.md)</li>

<li>[Lokale Kachelbenachrichtigungen](tiles-and-notifications-sending-a-local-tile-notification.md)</li>

<li>[Periodische Benachrichtigungen](tiles-and-notifications-periodic-notification-overview.md)</li>

<li>[WNS](tiles-and-notifications-windows-push-notification-services--wns--overview.md)</li>

<li>[Unformatierte Benachrichtigungen](tiles-and-notifications-raw-notification-overview.md)</li>
</ul>
</li>


<li>[Ein-/Ausschalten](toggles.md)</li>
<li>[QuickInfos](tooltips.md)</li>

<li>[Webansicht](web-view.md)</li>
</ul>
</div>

## <a name="additional-controls-options"></a>Zusätzliche Steueroptionen

Zusätzliche Steuerelemente für die UWP-Entwicklung werden von Unternehmen wie [Telerik](http://www.telerik.com/), [SyncFusion](https://www.syncfusion.com/products/uwp), [DevExpress](https://www.devexpress.com/Products/NET/Controls/Win10Apps/), [Infragistics](http://www.infragistics.com/products/universal-windows-platform), [ComponentOne](https://www.componentone.com/Studio/Platform/UWP) und [ActiPro](http://www.actiprosoftware.com/products/controls/universal) bereitgestellt. Diese Steuerelemente bieten zusätzliche Unterstützung für Unternehmen und .NET-Entwickler, indem sie die Steuerelemente des Standardsystem mit benutzerdefinierten Steuerelementen und Diensten erweitern.  

Wenn Sie mehr über diese Steuerelemente erfahren möchten, sehen Sie sich das Beispiel [Customer Orders Database](https://github.com/Microsoft/Windows-appsample-customers-orders-database) in GitHub an. In diesem Beispiel werden die Steuerelemente Datenrasten und Dateneingabe von Telerik verwendet, die Teil der UI für die UWP-Suite sind. Die UI für die UWP-Suite besteht aus einer Sammlung von über 20 Steuerelementen, die als Open Source-Projekt über die .NET-Foundation verfügbar sind.

![Image der Customer Orders Database](images/customerOrdersDataGrid.png)
