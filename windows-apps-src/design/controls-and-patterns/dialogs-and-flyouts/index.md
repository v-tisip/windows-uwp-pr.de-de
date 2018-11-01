---
author: mijacobs
Description: Dialogs and flyouts display transient UI elements that appear when the user requests them or when something happens that requires notification or approval.
title: Dialogfelder und Flyouts
template: detail.hbs
ms.author: mijacobs
ms.date: 07/06/2018
ms.topic: article
keywords: windows 10, uwp
ms.assetid: ad6affd9-a3c0-481f-a237-9a1ecd561be8
pm-contact: yulikl
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: d4ff66e988634cf1ba48809688ea6535e6e95b03
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5871539"
---
# <a name="dialogs-and-flyouts"></a>Dialogfelder und Flyouts



Dialogfelder und Flyouts sind vorübergehende UI-Elemente, die angezeigt werden, wenn Ereignisse Benachrichtigungen, Genehmigungen oder zusätzliche Informationen vom Benutzer erfordern.

> **Wichtige APIs**: [ContentDialog-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog), [Flyout-Klasse](/uwp/api/Windows.UI.Xaml.Controls.Flyout)


:::row:::
    :::column:::
        **Dialogs**
        
        ![Example of a dialog](../images/dialogs/dialog_RS2_delete_file.png)

        Dialogs are modal UI overlays that provide contextual app information. Dialogs block interactions with the app window until being explicitly dismissed. They often request some kind of action from the user.
    :::column-end:::
    :::column::: 
        **Flyouts**

        ![Example of a flyout](../images/flyout-example2.png)

        A flyout is a lightweight contextual popup that displays UI related to what the user is doing. It includes placement and sizing logic, and can be used to reveal a secondary control or show more detail about an item.

        Unlike a dialog, a flyout can be quickly dismissed by tapping or clicking somewhere outside the flyout, pressing the Escape key or Back button, resizing the app window, or changing the device's orientation.
    :::column-end:::
:::row-end:::


## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Dialogfelder und Flyouts stellen sicher, dass den Benutzern wichtige Informationen bekannt sind, stellen jedoch auch eine Unterbrechung dar. Da Dialogfelder modal (blockierend) sind, werden die Benutzer unterbrochen und daran gehindert, andere Schritte durchzuführen, bis eine Interaktion mit dem Dialogfeld erfolgt ist. Flyouts sind weniger störend. Zu viele Flyouts können jedoch als störend empfunden werden.

Wenn ein Dialogfeld oder Flyout eingesetzt werden soll, müssen Sie sich für eine der beiden Optionen entscheiden.

Angesichts der Tatsache, dass Dialogfelder im Gegensatz zu Flyouts Interaktionen blockieren, sollten Dialogfelder auf Situationen beschränkt bleiben, in denen der Benutzer unterbrochen werden soll, um sich auf eine bestimmte Information oder die Beantwortung einer Frage zu konzentrieren. Flyouts hingegen können verwendet werden, wenn Sie auf etwas aufmerksam machen möchten, das der Benutzer jedoch ignorieren kann.

:::row:::
    :::column:::
   <p><b>Fälle, in denen ein Dialogfeld verwendet werden sollte:</b> <br/>
<ul>
<li>Für wichtige Informationen, die der Benutzer vor dem Fortsetzen lesen und bestätigen <b>muss</b>. Beispiele:
<ul>
  <li>Die Sicherheit des Benutzers ist möglicherweise gefährdet.</li>
  <li>Der Benutzer möchte eine wertvolle Ressource endgültig ändern.</li>
  <li>Der Benutzer möchte eine wertvolle Ressource löschen.</li>
  <li>Bestätigen eines In-App-Einkaufs</li>
</ul>

</li>
<li>Fehlermeldungen, die sich auf den Gesamtkontext der App beziehen, z. B. Verbindungsfehler.</li>
<li>Fragen, wenn dem Benutzer eine blockierende Frage gestellt werden muss, z. B. wenn die App nicht im Auftrag des Benutzers eine Auswahl treffen kann. Eine blockierende Frage kann nicht ignoriert oder verschoben werden und sollte dem Benutzer klar definierte Auswahlmöglichkeiten bieten.</li>
</ul>
</p>
    :::column-end:::
    :::column:::
   <p><b>Fälle, in denen ein Flyout verwendet werden sollte:</b> <br/>
<ul>
<li>Erfassen zusätzlicher Informationen, die erforderlich sind, bevor eine Aktion abgeschlossen werden kann.</li>
<li>Anzeigen von Informationen, die nur vorübergehend relevant sind. So können Sie z.B. in einer Fotogalerie-App ein Flyout einsetzen, damit eine große Version des Bilds angezeigt wird, wenn der Benutzer auf eine Miniaturansicht klickt.</li>
<li>Anzeigen weiterer Informationen, z. B. von Details oder ausführlicheren Beschreibungen eines Elements auf der Seite.</li>
</ul></p>
    :::column-end:::
:::row-end:::


## <a name="ways-to-avoid-using-dialogs-and-flyouts"></a>Möglichkeiten, um zu vermeiden, Dialogfelder und flyouts

Berücksichtigen Sie die Bedeutung der zu vermittelnden Informationen: Sind sie wichtig genug, um den Benutzer zu unterbrechen? Berücksichtigen Sie zudem, wie häufig die Informationen angezeigt werden müssen. Wenn ein Dialogfeld oder eine Benachrichtigung alle paar Minuten angezeigt wird, sollten Sie diese Informationen stattdessen in die primäre UI einbinden. So können Sie z.B. in einem Chat-Client anstatt eines Flyouts, der jedes Mal angezeigt wird, wenn sich ein Freund anmeldet, eine Liste der Freunde anzeigen, die derzeit online sind, und diejenigen Freunde hervorheben, die sich gerade anmelden.

Dialogfelder werden häufig zum Bestätigen einer Aktion vor deren Ausführung verwendet (z.B. vor dem Löschen einer Datei). Wenn Sie davon ausgehen, dass die Benutzer häufig eine bestimmte Aktion ausführen, sollten Sie eine Möglichkeit bereitstellen, versehentliche Aktionen rückgängig zu machen, anstatt jedes Mal die Bestätigung der Aktion zu erzwingen.

## <a name="how-to-create-a-dialog"></a>So erstellen Sie ein Dialogfeld

Finden Sie unter der [Artikel Dialogfelder](dialogs.md). 

## <a name="how-to-create-a-flyout"></a>So erstellen Sie ein flyout

Finden Sie im [Artikel Flyout](flyouts.md). 

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="../images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> oder <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in Aktion zu sehen.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

