---
author: mijacobs
Description: "Die Navigation in UWP-Apps (Apps für die universelle Windows-Plattform) basiert auf einem flexiblen Modell aus Navigationsstrukturen, Navigationselementen und Funktionen auf Systemebene."
title: "Navigationsgrundlagen für UWP-Apps"
ms.assetid: B65D33BA-AAFE-434D-B6D5-1A0C49F59664
label: Navigation design basics
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: a944e02ea116c0e054918397d9d46d366d43622a
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="navigation-design-basics-for-uwp-apps"></a>Navigationsdesigngrundlagen für UWP-Apps

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Wenn Sie sich eine App als eine Sammlung von Seiten vorstellen, beschreibt der Begriff *Navigation* den Wechselvorgang zwischen Seiten und innerhalb einer Seite. Es ist der Ausgangspunkt der Benutzererfahrung. So finden Benutzer die Inhalte und Funktionen, für die sie sich interessieren. Sie ist sehr wichtig, und es kann schwierig sein, sie richtig einzustellen. 

> **Wichtige APIs**: [Frame](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Frame), [Pivot-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Pivot), [NavigationView-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.NavigationView)

Ein Grund für das herausfordernde Einrichten der Navigation ist die große Anzahl an Entscheidungen, die wir als App-Entwickler treffen müssen. Wenn wir ein Buch entwerfen würden, würden unsere Entscheidungen einfach sein: in welcher Reihenfolge die Kapitel aufgeführt werden. Bei einer App können wir eine Navigationserfahrung erstellen, die ein Buch imitiert und bei der der Benutzer durch eine Reihe von Seiten blättert. Oder wir bieten ein Menü an, mit dem der Benutzer direkt zu einer beliebigen Seite wechseln kann – aber wenn wir zu viele Seiten haben, wird den Benutzer möglicherweise mit der Anzahl an Optionen überfordert. Oder wir platzieren alle Elemente auf einer Seite und bieten Filtermechanismen zum Anzeigen der Inhalte an. 

Obwohl es kein einzelnes Navigationsdesign gibt, das für jede App funktioniert, können Sie einer Reihe von Prinzipien und Richtlinien folgen, mit der Sie das richtige Design für Ihre App bestimmen können. 

## <a name="principles-of-good-design"></a>Prinzipien des guten Designs 
Beginnen wir mit den Grundprinzipien, die Forschungen zufolge die Grundlage für gutes Navigationsdesign bilden: 

* Seien Sie konsistent: Erfüllen Sie die Benutzererwartungen.
* Halten Sie es einfach: Nicht mehr als erforderlich tun.
* Behalten Sie die Übersicht: Navigationsfunktionen sollten nicht die Übersicht des Benutzers einschränken.

### <a name="be-consistent"></a>Achten Sie auf Einheitlichkeit 
Die Navigation sollte den Benutzererwartungen entsprechen und auf die Standardkonventionen für Symbole, Positionierung und Formatierung beruhen. 

In der folgenden Abbildung können Sie beispielsweise die Orte sehen, an denen Benutzer in der Regel Funktionen erwarten, wie der Navigationsbereich und die Befehlsleiste. Unterschiedliche Gerätefamilien verfügen über ihre eigenen Konventionen für Navigationselemente. Beispielsweise wird der Navigationsbereich in der Regel auf der linken Seite des Bildschirms für Tablets, aber für Mobilgeräte oben angezeigt.

<figure class="wdg-figure">
  ![Bevorzugte Orte für Navigationselemente](images/nav/nav-component-layout.png)
  <figcaption>Benutzer erwarten, gewisse UI-Elemente an Standardorten zu finden.</figcaption>
</figure> 

### <a name="keep-it-simple"></a>Einfachheit
Ein weiterer wichtiger Faktor des Navigationsdesigns ist das Hicksche Gesetz, das oft in Bezug auf Navigationsoptionen genannt wird. Dieses Gesetz ermutigt uns, zum Menü weniger Optionen hinzuzufügen. Je mehr Optionen vorhanden sind, desto langsamer werden die Benutzerinteraktionen mit diesen Optionen, besonders, wenn Benutzer eine neue App erkunden. 

<figure class="wdg-figure">
  ![Ein einfaches Menü im Vergleich zu einem komplexen Menü](images/nav/nav-simple-menus.png)
  <figcaption> Beachten Sie, dass dem Benutzer im linken Bereich weniger Optionen zur Verfügung stehen, während es auf der rechten Seite mehrere gibt. Dem Hickschen Gesetz zufolge ist es für den Benutzer einfacher, das linke Menü zu verstehen und zu nutzen.
</figcaption>
</figure> 

### <a name="keep-it-clean"></a>Bleiben Sie konsistent
Das letzte wichtige Merkmal der Navigation ist eine saubere Interaktion, was sich auf die physische Interaktion der Benutzer mit der Navigation über eine Vielzahl von Kontexten bezieht. Hierbei handelt es sich um einen Bereich, bei dem Sie sich in die Rolle des Benutzers versetzen müssen, um Ihr Design zu vermitteln. Versuchen Sie, Ihren Benutzer und sein Verhalten zu verstehen. Wenn Sie beispielsweise eine Koch-App entwickeln, könnten Sie einen schnellen Zugriff auf eine Einkaufsliste und einen Timer bereitstellen. 

## <a name="three-general-rules"></a>Drei allgemeine Regeln
Nehmen wir jetzt unsere Designprinzipien – Konsistenz, Einfachheit und saubere Interaktionen – und verwenden sie, um einige allgemeinen Regeln aufzustellen. Wie mit allen Faustregeln, sollten sie als Ausgangspunkt gesehen und bei Bedarf optimiert werden. 

1. Vermeiden Sie tiefe Navigationshierarchien. Wie viele Navigationsebenen sind für Ihre Benutzer am besten geeignet? Eine Navigation auf oberster Ebene und Hierarchieebene darunter ist in der Regel ausreichend. Wenn Sie über drei Navigationsebenen hinausgehen, verstoßen Sie gegen das Prinzip der Einfachheit. Schlimmer noch: Sie gehen das Risiko ein, dass der Benutzer sich in einer tiefen Hierarchie verirrt.

2. Vermeiden Sie zu viele Navigationsoptionen. Es werden meist drei bis sechs Navigationselemente pro Ebene verwendet. Wenn Ihre Navigation mehr Elemente benötigt, besonders auf der obersten Hierarchieebene, dann können Sie Ihre App in mehrere Apps aufteilen, da Sie möglicherweise in der einen App zu viele Funktionen haben. Zu viele Navigationselemente in einer App führen üblicherweise zu inkonsistenten und irrelevanten Zielen.

3. Vermeiden Sie „Pogo Sticking”. Pogo Sticking tritt auf, wenn der Benutzer für die Navigation zu zugehörigen Inhalten eine Ebene nach oben und erneut eine nach unten navigieren muss. Pogo Sticking verstößt gegen das Prinzip der sauberen Interaktion durch unnötige Klicks oder Interaktionen, um ein offensichtliches Ziel zu erreichen; in diesem Fall das Betrachten von aufgereihten, zugehörigen Inhalten. (Die Ausnahme dieser Regel liegt in Such- und Durchsuchungsvorgängen, in denen Pogo Sticking möglicherweise die einzige Möglichkeit ist, für die erforderliche Vielfalt und Tiefe zu sorgen.)
<figure class="wdg-figure">
  ![Ein Beispiel für Pogo Sticking](images/nav/nav-pogo-sticking-1.png)
  <figcaption> Pogo Sticking zum Navigieren einer App – der Benutzer muss (mit dem grünen Rückwärtspfeil) auf die Hauptseite zurückkehren, um zur Registerkarte „Projekte” zu navigieren.
</figcaption>
</figure> 
<figure class="wdg-figure">
  ![Das Problem des Pogo Stickings kann durch eine laterale Navigation mit Wischbewegungen behoben werden.](images/nav/nav-pogo-sticking-2.png)
  <figcaption>Sie können einige Pogo Sticking-Probleme mit einem Symbol beheben (beachten Sie die Wischbewegung in Grün).
</figcaption>
</figure> 


## <a name="use-the-right-structure"></a>Verwenden Sie die richtige Navigationsstruktur 
Nun, da Sie mit den allgemeinen Navigationsgrundsätzen und -regeln vertraut sind, ist es Zeit, die wichtigsten Entscheidungen bezüglich der Navigation zu treffen: wie sollten Sie Ihre App strukturieren? Es gibt zwei allgemeine Strukturen: flache und hierarchische. 

### <a name="flatlateral"></a>Flach/lateral
In einer flachen/lateralen Struktur stehen die Seiten parallel zueinander. Sie können in beliebiger Reihenfolge von einer Seite zur nächsten wechseln. 
<figure class="wdg-figure">
  <img src="images/nav/nav-pages-peer.png" alt="Pages arranged in a flat structure" />
<figcaption>In einer flachen Struktur angeordnete Seiten</figcaption>
</figure> 

Flache Strukturen haben viele Vorteile: sie sind einfach und übersichtlich, und durch sie können die Benutzer direkt zu einer bestimmten Seite wechseln, ohne über zwischengeschaltete Seiten navigieren zu müssen.  Im Allgemeinen sind flache Strukturen gut – aber sie funktionieren nicht für jede App. Wenn Ihre App viele Seiten hat, kann eine flache Liste den Benutzer verwirren. Eine flache Struktur kann Seiten nicht in einer bestimmten Reihenfolge anzeigen. 

Wir empfehlen die Verwendung einer flachen Struktur bei: 
<ul>
<li>Die Seiten können in beliebiger Reihenfolge angezeigt werden.</li>
<li>Die Seiten sind deutlich voneinander abgegrenzt und verfügen nicht über eine offensichtliche Beziehung zwischen über- und untergeordneten Elementen.</li>
<li>Es gibt weniger als acht Seiten in der Gruppe.<br/>
Wenn eine Gruppe mehr als 7Seiten enthält, wird es für Benutzer möglicherweise schwierig, zu verstehen, inwiefern sich die Seiten unterscheiden oder welche Position sie zurzeit in der Gruppe haben. Wenn Sie davon ausgehen, dass dies kein Problem für Ihre App ist, machen Sie aus den Seiten Peers. Ziehen Sie andernfalls eine hierarchische Struktur in Betracht, um die Seiten in zwei oder mehr kleinere Gruppen zu unterteilen. (Ein Hub-Steuerelement kann Ihnen dabei helfen, die Seiten in Kategorien zu gruppieren.)</li>
</ul>


### <a name="hierarchical"></a>Hierarchisch

In einer hierarchischen Struktur werden Seiten in einer Baumstruktur organisiert. Jede untergeordnete Seite hat nur ein übergeordnetes Element. Ein übergeordnetes Element kann jedoch eine oder mehrere untergeordnete Seiten haben. Um eine untergeordnete Seite aufzurufen, durchlaufen Sie das übergeordnete Element.

<figure class="wdg-figure">
  <img src="images/nav/nav-pages-hiearchy.png" alt="Pages arranged in a hierarchy" />
<figcaption>In einer Hierarchie angeordnete Seiten</figcaption>
</figure>

Hierarchische Strukturen eignen sich für das Organisieren von komplexen Inhalten, die viele der Seiten umfassen, oder wenn Seiten in einer bestimmten Reihenfolge angezeigt werden sollen. Der Nachteil besteht darin, dass hierarchische Seiten Navigationsmehraufwand verursachen: je tiefer die Struktur, desto mehr Klicks sind für das Wechseln der Seiten erforderlich. 

Wir empfehlen eine hierarchische Struktur bei: 
<ul>
<li>Sie erwarten, dass der Benutzer die Seiten in einer bestimmten Reihenfolge durchlaufen wird. Sie ordnen die Hierarchie entsprechend an, um die Reihenfolge zu erzwingen.</li>
<li>Es gibt eine klare Beziehung zwischen einer Seite als übergeordnetem Element und den anderen Seiten in der Gruppe als untergeordneten Elementen.</li>
<li>In der Gruppe gibt es mehr als 7 Seiten.<br/>
Wenn eine Gruppe mehr als 7Seiten enthält, wird es für Benutzer möglicherweise schwierig, zu verstehen, inwiefern sich die Seiten unterscheiden oder welche Position sie zurzeit in der Gruppe haben. Wenn Sie davon ausgehen, dass dies kein Problem für Ihre App ist, machen Sie aus den Seiten Peers. Ziehen Sie andernfalls eine hierarchische Struktur in Betracht, um die Seiten in zwei oder mehr kleinere Gruppen zu unterteilen. (Ein Hub-Steuerelement kann Ihnen dabei helfen, die Seiten in Kategorien zu gruppieren.)</li>
</ul>

### <a name="combining-structures"></a>Kombinieren von Strukturen
Sie haben müssen nicht die eine oder andere Struktur wählen; viele durchdachte Apps verwenden sowohl flache als auch hierarchische Strukturen:

![App mit einer Hybridstruktur](images/nav/nav-hybridstructure.png.png)

Diese Apps verwenden flache Strukturen für Seiten auf obersten Ebenen, die in beliebiger Reihenfolge angezeigt werden können, und hierarchische Strukturen für Seiten, die komplexere Beziehungen haben. 

Wenn die Navigationsstruktur über mehrere Ebenen verfügt, empfehlen wir, dass Peer-to-Peer-Navigationselemente nur mit den Peers innerhalb der aktuellen Unterstruktur verknüpft sind. Beachten Sie die folgende Abbildung, die eine Navigationsstruktur mit drei Ebenen zeigt:

![App mit zwei Unterstrukturen](images/nav/nav-subtrees.png)
-   Auf Ebene 1 sollte das Peer-to-Peer-Navigationselement Zugriff auf die Seiten A, B, C und D ermöglichen.
-   Auf Ebene 2 sollten die Peer-to-Peer Navigationselemente für die A2-Seiten nur mit den anderen A2-Seiten verknüpft werden. Sie sollten nicht mit Seiten auf Ebene 2 in der C-Unterstruktur verknüpft sein.

![App mit zwei Unterstrukturen](images/nav/nav-subtrees2.png)
 

## <a name="use-the-right-controls"></a>Verwenden Sie die richtigen Steuerelemente

Sobald Sie sich für eine Seitenstruktur entschieden haben, müssen Sie entscheiden, wie der Benutzer durch die Seiten navigieren soll. UWP bietet eine Vielzahl von Navigationssteuerelementen, die Sie dabei unterstützen. Da diese Steuerelemente für alle UWP-Apps verfügbar sind, wird deren Verwendung eine konsistente und zuverlässige Navigationsfunktionalität gewährleisten. 


<table>
<tr>
    <th>Steuerelement</th>
    <th>Beschreibung</th>
</tr>
<tr>
    <td>[Frame](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Frame)</td>
    <td>Mit wenigen Ausnahmen verwendet jede App mit mehrere Seiten den Frame. In einem typischen Szenario hat die App eine Hauptseite, die den Frame und ein primäres Navigationselement beinhaltet, z.B. ein Navigationssteuerelement. Wählt der Benutzer eine Seite, wird sie durch den Frame geladen und angezeigt.</td>
</tr>
<tr>
    <td>[Registerkarten und Pivot](../controls-and-patterns/tabs-pivot.md)<br/><br/>
    <img src="images/nav/nav-tabs-sm-300.png" alt="Tab-based navigation" /></td>
    <td>Zeigt eine Liste mit Links zu Seiten auf derselben Ebene an.
<p>Verwenden Sie in folgenden Fällen Registerkarten/Pivots:</p>
<ul>
<li><p>Es sind 2 bis 5 Seiten vorhanden.</p>
<p>(Sie können Registerkarten/Pivots bei mehr als fünf Seiten verwenden, es kann aber schwierig sein, alle Registerkarten/Pivots auf dem Bildschirm anzuzeigen.)</p></li>
<li>Sie erwarten, dass Benutzer häufig zwischen Seiten wechseln werden.</li>
</ul></td>
</tr>
<tr>
    <td>[Navigationsansicht](../controls-and-patterns/navigationview.md)<br/><br/>
    <img src="images/nav/nav-navpane-4page-thumb.png" alt="A navigation pane" /></td>
    <td>Zeigt eine Liste mit Links zu den übergeordneten Seiten an.
<p>Verwenden Sie in folgenden Fällen einen Navigationsbereich:</p>
<ul>
<li>Sie erwarten nicht, dass Benutzer häufig zwischen Seiten wechseln werden.</li>
<li>Sie möchten Platz sparen, wobei Sie eine Verlangsamung der Navigationsvorgänge in Kauf nehmen.</li>
<li>Die Seiten befinden sich auf der obersten Ebene.</li>
</ul></td>
</tr>
<tr>
<td>[Master/Details](../controls-and-patterns/master-details.md)<br/><br/>
<img src="images/higsecone-masterdetail-thumb.png" alt="Master/details" /></td>
<td>Zeigt eine Liste (Masteransicht) der Elementübersichten an. Durch Auswahl eines Elements wird die entsprechende Elementseite im Detailbereich angezeigt.
<p>Verwenden Sie in folgenden Fällen das Master/Details-Element:</p>
<ul>
<li>Sie erwarten, dass Benutzer häufig zwischen untergeordneten Elementen wechseln werden.</li>
<li>Sie möchten es dem Benutzer ermöglichen, Vorgänge auf hoher Ebene, z. B. Löschen oder Sortieren, für einzelne Elemente oder Gruppen von Elementen durchzuführen, und Sie möchten es dem Benutzer ermöglichen, Details für jedes Element anzuzeigen oder zu aktualisieren.</li>
</ul>
<p>Master/Details-Elemente eignen sich gut für E-Mail-Posteingänge, Kontaktlisten und die Dateneingabe.</p>
</td>
</tr>
<tr>
<td s>[Zurück](navigation-history-and-backwards-navigation.md)</td>
<td style="vertical-align:top;">Der Benutzer kann den Navigationsverlauf innerhalb einer App und, abhängig vom Gerät, von App zu App zurückverfolgen. Weitere Informationen finden Sie im Artikel [Navigationsverlauf und Rückwärtsnavigation](navigation-history-and-backwards-navigation.md).</td>
</tr>
<tr class="odd">
<td>Hyperlinks und Schaltflächen</td>
<td>Im Inhalt eingebettete Navigationselemente werden im Inhalt einer Seite angezeigt. Im Gegensatz zu anderen Navigationselementen, die für alle Gruppen oder Unterstrukturen der Seite konsistent sein sollten, sind im Inhalt eingebettete Navigationselemente auf jeder Seite einzigartig.</td>
</tr>
</table>

## <a name="next-add-navigation-code-to-your-app"></a>Nächster Schritt: Hinzufügen von Navigationscode zu Ihrer App
Im nächsten Artikel, [Implementierung grundlegender Navigation,](navigate-between-two-pages.md), erfahren Sie den XAML und Code, die für die Verwendung von Frame-Steuerelementen zur Bereitstellung einer grundlegenden Navigation in Ihrer App erforderlich sind. 


<!--
## History and the back button
UWP provides a back button and a system for traversing the user's navigation hsitory within an app. This system does most of the work for you, but there are a few APIs you need to call so that it works properly. For more info and instructions, see [History and backwards navigation](navigation-history-and-backwards-navigation.md). 
-->





