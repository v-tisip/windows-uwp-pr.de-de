---
author: serenaz
Description: Navigation in Universal Windows Platform (UWP) apps is based on a flexible model of navigation structures, navigation elements, and system-level features.
title: Navigationsgrundlagen für UWP-Apps
ms.assetid: B65D33BA-AAFE-434D-B6D5-1A0C49F59664
label: Navigation design basics
template: detail.hbs
op-migration-status: ready
ms.author: sezhen
ms.date: 11/27/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 3edb7dc28561b5d316a908df951e3052eafc995b
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1654269"
---
# <a name="navigation-design-basics-for-uwp-apps"></a>Navigationsdesigngrundlagen für UWP-Apps

Wenn Sie sich eine App als eine Sammlung von Seiten vorstellen, beschreibt der Begriff *Navigation* den Wechselvorgang zwischen Seiten und innerhalb einer Seite. Sie ist der Ausgangspunkt der Benutzererfahrung, und es ist, wie Benutzer die Inhalte und Funktionen finden, die sie interessieren. Sie ist sehr wichtig, und es kann schwierig sein, sie richtig einzustellen.

Es ist schwierig, weil wir als App-Designer eine Vielzahl von Entscheidungen treffen müssen. Wir könnten vorgeben, dass der Benutzer eine Reihe von Seiten in der Reihenfolge durchläuft. Oder wir könnten ein Menü anbieten, das es dem Benutzer erlaubt, direkt zu einer beliebigen Seite zu springen. Oder wir platzieren alle Elemente auf einer Seite und bieten Filtermechanismen zum Anzeigen der Inhalte an.
 
Es gibt zwar kein einheitliches Navigationsdesign, das für jede App funktioniert, aber es gibt Prinzipien und Richtlinien, die Ihnen helfen, das richtige Design für Ihre App zu finden. 

<figure class="wdg-figure">
  <img alt="Navigation diagram for an app" src="images/navigation_diagram.png" />
  <figcaption>Diagramm der Navigation einer App.</figcaption>
</figure> 

## <a name="principles-of-good-navigation"></a>Grundsätze guter Navigation
Beginnen wir mit den Grundprinzipien eines guten Navigationsdesigns: 

* Konsistenz: Erfüllen Sie die Erwartungen der Anwender.
* Einfachheit: Nicht mehr als notwendig.
* Klarheit: Bieten Sie klare Wege und Optionen.

### <a name="consistency"></a>Konsistenz
Die Navigation sollte den Erwartungen der Benutzer entsprechen. Die Verwendung von [Standardsteuerelementen](#use-the-right-controls), mit denen die Benutzer vertraut sind, und der Einhaltung von Standardkonventionen für Symbole, Position und Stil wird die Navigation für die Benutzer vorhersehbar und intuitiv.

<figure class="wdg-figure">
<img src="images/nav/nav-component-layout.png" alt="Preferred location for navigation elements"/>
  <figcaption>Benutzer erwarten, gewisse UI-Elemente an Standardorten zu finden.</figcaption>
</figure> 

### <a name="simplicity"></a>Einfachheit
Weniger Navigationselemente erleichtern den Anwendern die Entscheidungsfindung. Der einfache Zugriff auf wichtige Ziele und das Ausblenden weniger wichtiger Objekte hilft den Benutzern, schneller dorthin zu gelangen, wo sie wollen.

<figure class="wdg-figure">
<img src="images/nav/nav-simple-menus.png" alt="A simple versus a complex menu"/>
  <figcaption> Das Menü auf der linken Seite ist das Verständnis und die Nutzung für Benutzer einfacher, da es weniger Elemente gibt.
</figcaption>
</figure> 

### <a name="clarity"></a>Klarheit
Klare Pfade ermöglichen eine logische Navigation für den Benutzer. Navigationsmöglichkeiten sichtbar zu machen und Zusammenhänge zwischen den Seiten zu klären, soll verhindern, dass sich die Benutzer „verirren”.

<figure class="wdg-figure">
<img src="images/nav/nav-pages.png" alt="Clear paths and destinations"/>
  <figcaption> Die Ziele sind klar gekennzeichnet, so dass die Benutzer wissen, wo sie sich befinden.
</figcaption>
</figure> 

## <a name="general-recommendations"></a>Allgemeine Empfehlungen
Nehmen wir nun unsere Gestaltungsprinzipien – Konsistenz, Einfachheit und Klarheit – und verwenden wir sie, um einige allgemeine Empfehlungen zu formulieren.

1. Denken Sie an Ihre Benutzer. Verfolgen Sie typische Pfade, die sie durch Ihre App nehmen könnten, und überlegen Sie für jede Seite, warum der Benutzer dort ist und wohin er gehen möchte. 

2. Vermeiden Sie tiefe Navigationshierarchien. Wenn Sie über drei Navigationsebenen hinausgehen, riskieren Sie, Ihren Benutzer in einer tiefen Hierarchie zu verlieren, die er nur schwer verlassen kann.

3. Vermeiden Sie „Pogo Sticking”. Pogo Sticking tritt auf, wenn der Benutzer für die Navigation zu zugehörigen Inhalten eine Ebene nach oben und erneut eine nach unten navigieren muss.

## <a name="use-the-right-structure"></a>Verwenden Sie die richtige Navigationsstruktur 
Nun, da Sie mit den allgemeinen Navigationsprinzipien vertraut sind, überlegen wir uns die Strukturierung Ihrer App. Es gibt zwei allgemeine Strukturen: flache und hierarchische. 

### <a name="flatlateral"></a>Flach/lateral
![In einer flachen Struktur angeordnete Seiten](images/nav/nav-pages-peer.png)

In einer flachen/lateralen Struktur stehen die Seiten parallel zueinander. Sie können in beliebiger Reihenfolge von einer Seite zur nächsten wechseln. 

Wir empfehlen die Verwendung einer flachen Struktur bei: 
<ul>
<li>Die Seiten können in beliebiger Reihenfolge angezeigt werden.</li>
<li>Die Seiten sind deutlich voneinander abgegrenzt und verfügen nicht über eine offensichtliche Beziehung zwischen über- und untergeordneten Elementen.</li>
<li>Es gibt weniger als acht Seiten in der Gruppe.<br/>
(Wenn eine Gruppe mehr Seiten enthält, wird es für Benutzer möglicherweise schwierig, zu verstehen, inwiefern sich die Seiten unterscheiden oder welche Position sie zurzeit in der Gruppe haben. Wenn Sie davon ausgehen, dass dies kein Problem für Ihre App ist, machen Sie aus den Seiten Peers. Ziehen Sie andernfalls eine hierarchische Struktur in Betracht, um die Seiten in zwei oder mehr kleinere Gruppen zu unterteilen.)</li>
</ul>

### <a name="hierarchical"></a>Hierarchisch
![In einer Hierarchie angeordnete Seiten](images/nav/nav-pages-hiearchy.png)

In einer hierarchischen Struktur werden Seiten in einer Baumstruktur organisiert. Jede untergeordnete Seite hat ein übergeordnetes Element. Ein übergeordnetes Element kann jedoch eine oder mehrere untergeordnete Seiten haben. Um eine untergeordnete Seite aufzurufen, durchlaufen Sie das übergeordnete Element.

Hierarchische Strukturen sind gut geeignet, um komplexe Inhalte, die sich über viele Seiten erstrecken, zu organisieren. Der Nachteil besteht darin, dass hierarchische Seiten Navigationsmehraufwand verursachen: je tiefer die Struktur, desto mehr Klicks sind für das Wechseln der Seiten erforderlich. 

Wir empfehlen eine hierarchische Struktur bei: 
<ul>
<li>Seiten, die in einer bestimmten Reihenfolge durchlaufen werden sollen.</li>
<li>Es gibt eine klare Beziehung zwischen übergeordneten und untergeordneten Seiten.</li>
<li>In der Gruppe gibt es mehr als 7 Seiten.</li>
</ul>

### <a name="combining-structures"></a>Kombinieren von Strukturen
![App mit einer Hybridstruktur](images/nav/nav-hybridstructure.png.png)

Sie haben müssen nicht die eine oder andere Struktur wählen; viele durchdachte Apps verwenden beide Strukturen. Eine App verwendet flache Strukturen für Seiten auf obersten Ebenen, die in beliebiger Reihenfolge angezeigt werden können, und hierarchische Strukturen für Seiten, die komplexere Beziehungen haben. 

Wenn die Navigationsstruktur über mehrere Ebenen verfügt, empfehlen wir, dass Peer-to-Peer-Navigationselemente nur mit den Peers innerhalb der aktuellen Unterstruktur verknüpft sind. Beachten Sie die folgende Abbildung, die eine Navigationsstruktur mit drei Ebenen zeigt:

![App mit zwei Unterstrukturen](images/nav/nav-subtrees.png)
- Auf Ebene 1 sollte das Peer-to-Peer-Navigationselement Zugriff auf die Seiten A, B, C und D ermöglichen.
- Auf Ebene 2 sollten die Peer-to-Peer Navigationselemente für die A2-Seiten nur mit den anderen A2-Seiten verknüpft werden. Sie sollten nicht mit Seiten auf Ebene 2 in der C-Unterstruktur verknüpft sein.

![App mit zwei Unterstrukturen](images/nav/nav-subtrees2.png)

## <a name="use-the-right-controls"></a>Verwenden Sie die richtigen Steuerelemente
Sobald Sie sich für eine Seitenstruktur entschieden haben, müssen Sie entscheiden, wie der Benutzer durch die Seiten navigieren soll. UWP bietet eine Vielzahl von Navigationssteuerelementen, um ein konsistentes und zuverlässiges Navigationserlebnis in Ihrer App zu gewährleisten. 

Wir empfehlen die Auswahl eines Navigationssteuerelements anhand der Anzahl der Navigationselemente in Ihrer App. Wenn Sie fünf oder weniger Navigationselemente haben, dann verwenden Sie die Einstiegsnavigation (z. B. [Registerkarten und Pivot](../controls-and-patterns/tabs-pivot.md)). Wenn Sie sechs oder mehr Navigationspunkte haben, dann verwenden Sie die linke Navigation, wie z. B. die [Navigationsansicht](../controls-and-patterns/navigationview.md) oder [Master/Details](../controls-and-patterns/master-details.md).

<div class="mx-responsive-img">

<table>
<tr>
    <th>Steuerelement</th>
    <th>Beschreibung</th>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Frame">Frame</a><br/><br/>
    <img src="images/frame.png" alt="Frame" /></td>
    <td>Zeigt Seiten an. <p>Mit wenigen Ausnahmen verwendet jede App mit mehrere Seiten den Frame. In einem typischen Szenario hat die App eine Hauptseite, die den Frame und ein primäres Navigationselement beinhaltet, z.B. ein Navigationssteuerelement. Wählt der Benutzer eine Seite, wird sie durch den Frame geladen und angezeigt.</p></td>
</tr>
<tr>
    <td><a href="../controls-and-patterns/tabs-pivot.md">Registerkarten und Pivot</a><br/><br/>
    <img src="images/nav/nav-tabs-sm-300.png" alt="Tab-based navigation" /></td>
    <td>Zeigt eine horizontale Liste mit Links zu Seiten auf derselben Ebene an.
<p>Zu verwenden in folgenden Fällen:</p>
<ul>
<li>Es sind 2 bis 5 Seiten vorhanden. (Sie können Registerkarten/Pivots bei mehr als fünf Seiten verwenden, es kann aber schwierig sein, alle Registerkarten/Pivots auf dem Bildschirm anzuzeigen.)</li>
<li>Sie erwarten, dass Benutzer häufig zwischen Seiten wechseln werden.</li>
</ul></td>
</tr>
<tr>
    <td><a href="../controls-and-patterns/navigationview.md">Navigationsansicht</a><br/><br/>
    <img src="images/nav/nav-navpane-4page-thumb.png" alt="A navigation pane" /></td>
    <td>Zeigt eine vertikale Liste mit Links zu den übergeordneten Seiten an.
<p>Zu verwenden in folgenden Fällen:</p>
<ul>
<li>Die Seiten befinden sich auf der obersten Ebene.</li>
<li>Es gibt viele Navigationselemente (mehr als 5).</li>
<li>Sie erwarten nicht, dass Benutzer häufig zwischen Seiten wechseln werden.</li>

</ul></td>
</tr>
<tr>
<td><a href="../controls-and-patterns/master-details.md">Master/Details</a><br/><br/>
<img src="images/higsecone-masterdetail-thumb.png" alt="Master/details" /></td>
<td>Zeigt eine Liste (Masteransicht) der Elemente an. Durch Auswahl eines Elements wird die entsprechende Seite im Detailbereich angezeigt.
<p>Zu verwenden in folgenden Fällen:</p>
<ul>
<li>Sie erwarten, dass Benutzer häufig zwischen untergeordneten Elementen wechseln werden.</li>
<li>Sie möchten es dem Benutzer ermöglichen, Vorgänge auf hoher Ebene, z. B. Löschen oder Sortieren, für einzelne Elemente oder Gruppen von Elementen durchzuführen, und Sie möchten es dem Benutzer ermöglichen, Details für jedes Element anzuzeigen oder zu aktualisieren.</li>
</ul>
<p>Master/Details eignet sich gut für E-Mail-Posteingänge, Kontaktlisten und die Dateneingabe.</p>
</td>
<tr>
<td><a href="../controls-and-patterns/hub.md">Hub</a><br/><br/>
<img src="images/hub.png" alt="Hub" /></td>
<td> Zeigt Abschnitte von bestellten Artikeln in Rastern an. 
<p>Zu verwenden in folgenden Fällen:</p>
<ul>
<li>Sie möchten eine visuelle Navigation mit Hero-Images erstellen.</li>
</ul>
<p>Hubs eignen sich gut zum Durchblättern, Ansehen oder Kaufen.</p>
</td>
</tr>
<tr>
<td><a href="../controls-and-patterns/hyperlinks.md">Hyperlinks</a> und <a href="../controls-and-patterns/buttons.md">Schaltflächen</a></td>
<td> Eingebettete Navigationselemente können im Inhalt einer Seite erscheinen. Im Gegensatz zu anderen Navigationselementen, die für alle Seiten konsistent sein sollten, sind im Inhalt eingebettete Navigationselemente auf jeder Seite einzigartig.</td>
</tr>
</table>
</div>

## <a name="next-add-navigation-code-to-your-app"></a>Nächster Schritt: Hinzufügen von Navigationscode zu Ihrer App
Im nächsten Artikel, [Implementierung grundlegender Navigation,](navigate-between-two-pages.md), erfahren Sie den Code, die für die Verwendung von Frame-Steuerelementen zur Bereitstellung einer grundlegenden Navigation zwischen zwei Seiten in Ihrer App erforderlich ist. 