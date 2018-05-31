---
author: mijacobs
Description: In a Universal Windows Platform (UWP) app, command elements are the interactive UI elements that enable the user to perform actions, such as sending an email, deleting an item, or submitting a form.
title: Befehlsdesigngrundlagen für Apps der universellen Windows-Plattform (UWP)
ms.assetid: 1DB48285-07B7-4952-80EF-02B57D4469F2
label: Command design basics
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 07b9ce7b5a57f6dc1ba202ed57e8b2d4d93e583f
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1654389"
---
#  <a name="command-design-basics-for-uwp-apps"></a>Befehlsdesigngrundlagen für UWP-Apps

Bei den *Befehlselementen* in einer Universellen Windows-Plattform (UWP)-App handelt es sich um die interaktiven Benutzeroberflächenelemente, mit denen der Benutzer Aktionen durchführen kann, um beispielsweise eine E-Mail zu senden, ein Element zu löschen oder ein Formular zu übermitteln. 

Dieser Artikel beschreibt allgemeine Befehlselemente, die von ihnen unterstützten Interaktionen und die Befehlsoberflächen für ihr Hosting.

![Befehlselemente in der Maps-App](images/maps.png)

Oben finden Sie Beispiele für Befehlselemente in der Maps-App.

## <a name="provide-the-right-type-of-interactions"></a>Bereitstellen geeigneter Interaktionen

Die wichtigste Entscheidung bei der Gestaltung einer Befehlsschnittstelle ist die Wahl der möglichen Benutzeraktionen. Um die richtige Art Interaktionen zu planen, konzentrieren Sie sich auf Ihre App – denken Sie daran, welche Benutzererfahrungen Sie ermöglichen möchten und welche Schritte die Benutzer unternehmen müssen. Sobald Sie entscheiden, was die Benutzer erreichen sollen, können Sie ihnen die entsprechenden Werkzeuge zur Verfügung stellen.

Einige Interaktionen für Ihre App sind:

- Senden oder Übermitteln von Informationen 
- Auswählen von Einstellungen und Auswahlmöglichkeiten
- Suchen und Filtern von Inhalten
- Öffnen, Speichern und Löschen von Dateien
- Inhalte bearbeiten oder erstellen

## <a name="use-the-right-command-element-for-the-interaction"></a>Verwenden Sie das richtige Befehlselement für die Interaktion

Die Verwendung der richtigen Elemente zur Befehlsinteraktionen kann den Unterschied zwischen einer intuitiven, benutzerfreundlichen App und einer schwierigen, verwirrenden App ausmachen. Die Universelle Windows-Plattform (UWP) bietet eine große Anzahl von Befehlselementen, die Sie in Ihrer App verwenden können. Die folgende Liste enthält einige der gängigsten Steuerelemente sowie eine Zusammenfassung der jeweils möglichen Interaktionen:

<div class="mx-responsive-img">
<table>
<thead>
<tr class="header">
<th align="left">Kategorie</th>
<th align="left">Elemente</th>
<th align="left">Interaktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b>Schaltflächen</b><br/><br/>
    <img src="../controls-and-patterns/images/controls/button.png" alt="button" /></td>
<td align="left"><a href="../controls-and-patterns/buttons.md">Schaltfläche</a></td>
<td align="left">Löst eine sofortige Aktion aus. Beispiele hierfür sind das Versenden einer E-Mail, das Senden von Formulardaten oder das Bestätigen einer Aktion in einem Dialog.</td>
</tr>
<tr class="even">
<td align="left">Listen<br/><br/>
    <img src="../controls-and-patterns/images/controls/combo-box-open.png" alt="drop down list" /></td>
<td align="left"><a href="../controls-and-patterns/lists.md">Dropdownliste, Listenfeld, Listen- und Rasteransicht</a></td>
<td align="left">Stellt Elemente in einer interaktiven Liste oder in einem Raster dar. Wird normalerweise für viele Optionen oder Anzeigeelemente verwendet.</td>
</tr>
<tr class="odd">
<td align="left">Auswahlsteuerelemente<br/><br/>
    <img src="../controls-and-patterns/images/controls/radio-button.png" alt="radio button" /></td>
<td align="left"><a href="../controls-and-patterns/checkbox.md">Kontrollkästchen</a>, <a href="../controls-and-patterns/radio-button.md">Optionsfeld</a>, <a href="../controls-and-patterns/toggles.md">Umschalter</a></td>
<td align="left">Ermöglicht die Auswahl einiger Optionen, z. B. beim Ausfüllen einer Umfrage oder beim Konfigurieren von App-Einstellungen.</td>
</tr>
<tr class="even">
<td align="left">Datums- und Zeitauswahl<br/><br/>
    <img src="../controls-and-patterns/images/controls/calendar-date-picker-open.png" alt="date picker" /></td>
<td align="left"><a href="../controls-and-patterns/date-and-time.md">Kalenderdatumsauswahl, Kalenderansicht, Datumsauswahl, Zeitauswahl</a></td>
<td align="left">Ermöglicht die Anzeige und Änderung von Datum und Uhrzeit, z. B. beim Erstellen eines Ereignisses oder beim Einstellen eines Alarms.</td>
</tr>
<tr class="odd">
<td align="left">Textvorhersage<br/><br/>
    <img src="../controls-and-patterns/images/controls/auto-suggest-box.png" alt="autosuggest box" /></td>
<td align="left"><a href="../controls-and-patterns/auto-suggest-box.md">Feld mit automatischen Vorschlägen</a></td>
<td align="left">Bietet Vorschläge als Benutzertyp, z. B. bei der Eingabe von Daten oder beim Ausführen von Abfragen.</td>
</tr>
</tbody>
</table>
</div>

Eine vollständige Liste finden Sie unter [Steuerelemente und UI-Elemente](https://dev.windows.com/design/controls-patterns).

##  <a name="place-commands-on-the-right-surface"></a>Platzieren von Befehlen auf der passenden Oberfläche
Sie können Befehlselemente auf einer Reihe von Oberflächen in Ihrer App platzieren, einschließlich der App-Canvas oder spezieller Befehlscontainer, wie Befehlsleisten, Menüs, Dialoge und Flyouts.

Beachten Sie, dass Sie den Benutzern möglichst erlauben sollten, Inhalte direkt zu manipulieren, anstatt Befehle zu verwenden, die auf den Inhalt wirken. Beispielsweise können Benutzer Listen durch Ziehen und Ablegen von Listenelementen neu anordnen, anstatt die Befehlsschaltflächen nach oben und unten zu verwenden.
  
Wenn Benutzer Inhalte nicht direkt manipulieren können, platzieren Sie Befehlselemente auf einer Befehlsoberfläche in Ihrer App:

<div class="mx-responsive-img">
<table class="uwpd-top-aligned-table">

<tr class="header">
<th align="left">Oberfläche</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>

<tr class="odd">
<td align="left" style="vertical-align: top">App-Canvas (Inhaltsbereich)
<p><img src="images/content-area.png" alt="The content area of an app" /></p></td>

<td align="left" style="vertical-align: top;">Wenn ein Befehl ständig für Kernszenarien benötigt wird, legen Sie ihn auf die Canvas. Da Sie Befehle in der Nähe von (oder auf) Objekten platzieren können, die durch den Befehl beeinflusst werden, sind auf der Canvas platzierte Befehle besonders komfortabel und intuitiv.
<p>Wählen Sie die Befehle für die Canvas aber mit Bedacht. Wenn Sie zu viele Befehle auf der App-Canvas positionieren, geht wertvoller Platz und die Übersichtlichkeit für den Benutzer verloren. Wenn der Befehl nicht häufig verwendet wird, sollten Sie ihn in eine andere Befehlsoberfläche einfügen.</p> 
</td><td>
Ein Vorschlagsfeld auf der Maps-App-Canvas.
<br></br>
  <img src="images/maps-canvas.png" alt="autosuggest box on Maps app canvas"/>
</td>
</tr>

<tr class="even">
<td align="left" style="vertical-align: top;"><a href="../controls-and-patterns/app-bars.md">Befehlsleiste</a>
<p><img src="../controls-and-patterns/images/controls_appbar_icons.png" alt="Example of a command bar with icons" /></p></td>
<td align="left" style="vertical-align: top;"> Befehlsleisten helfen beim Organisieren von Befehlen und machen sie leicht zugänglich. Befehlsleisten können am oberen Bildschirmrand, am unteren Bildschirmrand oder sowohl am oberen als auch am unteren Bildschirmrand platziert werden. 
</td>
<td>
Eine Befehlsleiste am oberen Rand der Maps-App.
<br></br>
<img src="images/maps-commandbar.png" alt="command bar in Maps app"/>
</td>
</tr>

<tr class="odd">
<td align="left" style="vertical-align: top;"><a href="../controls-and-patterns/menus.md">Menüs und Kontextmenüs</a>
<p><img src="images/controls-contextmenu-singlepane.png" alt="Example of a single-pane context menu" /></p></td>
<td align="left" style="vertical-align: top;">Mitunter ist es effektiver, mehrere Befehle in einem Befehlsmenü zu gruppieren, um Platz zu sparen. Menüs und Kontextmenüs zeigen auf Anforderung des Benutzers eine Liste von Befehlen oder Optionen an.
<p>Kontextmenüs eignen sich für Verknüpfungen mit häufig verwendeten Aktionen und ermöglichen den Zugriff auf sekundäre Befehle, die nur in bestimmten Kontexten relevant sind (z. B. die Zwischenablage oder spezielle Befehle). Kontextmenüs werden in der Regel durch einen Rechtsklick des Benutzers aufgerufen.</p>
</td><td>
Ein Kontextmenü erscheint, wenn der Benutzer mit der rechten Maustaste in der App-Maps klickt.
<br></br>
  <img src="images/maps-contextmenu.png" alt="context menu in Maps app"/>
</td>
</tr>
</table>
</div>

## <a name="provide-feedback-for-interactions"></a>Geben Sie Ihr Feedback zu Interaktionen

Feedback kommuniziert die Ergebnisse von Befehlen und ermöglicht dem Benutzer zu verstehen, was er getan hat und was er als nächstes tun kann. Im Idealfall sollte das Feedback natürlich in Ihre Benutzeroberfläche integriert werden, so dass Benutzer nicht unterbrochen werden müssen oder zusätzliche Maßnahmen ergreifen müssen, es sei denn, dies ist absolut notwendig. 

Hier sind einige Möglichkeiten, um Feedback in Ihrer App bereitzustellen.

<div class="mx-responsive-img">
<table class="uwpd-top-aligned-table">

<tr class="header">
<th align="left">Oberfläche</th>
<th align="left">Beschreibung</th>
</tr>

<tr class="odd">
<td align="left" style="vertical-align: top;"> <a href="../controls-and-patterns/app-bars.md">Befehlsleiste</a>
<p><img src="../controls-and-patterns/images/controls_appbar_icons.png" alt="Example of a command bar with icons" /></p>
</td>
<td align="left" style="vertical-align: top;"> Der Inhaltsbereich der Befehlsleiste ist ein intuitiver Ort, um Benutzern einen Status mitzuteilen.
<p>
  <img src="images/commandbar_anatomy.png" alt="Command bar content area for feedback"/>
  </p>
</td>
</tr>

<tr class="even">
<td align="left" style="vertical-align: top;"><a href="../controls-and-patterns/dialogs.md">Flyout</a>
<p><img src="images/controls-flyout-default-200.png" alt="Image of default flyout" /></p></td>
<td align="left" style="vertical-align: top;">
Ein einfaches, kontextbezogenes Popup, das durch Antippen oder Klicken außerhalb des Flyouts verworfen werden kann.
<p>
  <img src="../controls-and-patterns/images/controls/flyout.png" alt="Flyout above button"/>
  </p>
</td>
</tr>

<tr class="odd">
<td align="left" style="vertical-align: top;"><a href="../controls-and-patterns/dialogs.md">Dialogfeld-Steuerelemente</a>
<p><img src="images/controls-dialog-twobutton-200.png" alt="Example of a simple two-button dialog" /></p></td>
<td align="left" style="vertical-align: top;">Dialogfelder sind modale Benutzeroberflächenüberlagerungen, die kontextbezogene App-Informationen enthalten. Die meisten Dialogfelder blockieren die Interaktion mit dem App-Fenster, bis sie explizit geschlossen werden, und erfordern häufig eine Aktion des Benutzers.
<p>Dialogfelder können als störend empfunden werden und sollten daher nur in bestimmten Situationen zum Einsatz kommen. Weitere Informationen finden Sie unter [Bestätigen oder Rückgängigmachen von Aktionen](#when-to-confirm-or-undo-actions)</p>
<p>
  <img src="../controls-and-patterns/images/dialogs/dialog_RS2_delete_file.png" alt="dialog delete file"/></p>
</td>
</tr>

</table>
</div>

> [!TIP]
> Verwenden Sie nicht zu viele Bestätigungsdialogfelder. Diese können zwar sehr hilfreich sein, wenn dem Benutzer ein Fehler unterläuft, bei bewusst durchgeführten Aktionen sind sie jedoch eher hinderlich.

### <a name="when-to-confirm-or-undo-actions"></a>Bestätigen oder Rückgängigmachen von Aktionen

Ganz gleich, wie gut die Benutzeroberfläche gestaltet ist und wie vorsichtig der Benutzer vorgeht: Irgendwann wird jeder Benutzer eine Aktion ausführen, die er lieber nicht ausgeführt hätte. In einer solchen Situation kann Ihre App dem Benutzer helfen, indem sie eine Aktionsbestätigung anfordert oder eine Möglichkeit zum Rückgängigmachen der kürzlich durchgeführten Aktionen anbietet.

-   Für Aktionen, die nicht rückgängig gemacht werden können und schwerwiegende Auswirkungen haben, empfehlen wir die Verwendung eines Bestätigungsdialogfelds. Beispiele für solche Aktionen:
    -   Überschreiben einer Datei
    -   Schließen einer Datei ohne Speichern
    -   Bestätigen der endgültigen Löschung einer Datei oder von Daten
    -   Einkaufen (es sei denn, der Benutzer lehnt eine Bestätigungsanforderung ab)
    -   Senden eines Formulars, z. B. bei Registrierungen
-   Für Aktionen, die rückgängig gemacht werden können, ist ein einfacher „Rückgängig“-Befehl in der Regel ausreichend. Beispiele für solche Aktionen:
    -   Löschen einer Datei
    -   Löschen einer E-Mail (nicht endgültig)
    -   Ändern des Inhalts oder Bearbeiten von Text
    -   Umbenennen einer Datei

##  <a name="optimize-for-specific-input-types"></a> Optimieren für bestimmte Eingabearten

Ausführliche Informationen zum Optimieren der Benutzerfreundlichkeit bei einem bestimmten Eingabetyp oder -gerät finden Sie unter [Einführung in die Interaktion](../input/index.md).