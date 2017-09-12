---
author: mijacobs
Description: "Ressourcen für App-Symbole, die in einer Vielzahl von Formen innerhalb des Windows 10-Betriebssystems vorkommen, sind die Aushängeschilder für Ihre App für die Universelle Windows-Plattform (UWP)."
title: "Ressourcen für Kacheln und Symbole"
ms.assetid: D6CE21E5-2CFA-404F-8679-36AA522206C7
label: Tile and icon assets
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 54ad78d5799a96ddcec7b060704ee198e0bf8db5
ms.sourcegitcommit: 9a1310468970c8d1ade0fb200126dff56ea8c9e1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2017
---
# <a name="guidelines-for-tile-and-icon-assets"></a>Richtlinien für die Ressourcen für Kacheln und Symbole

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 


Ressourcen für App-Symbole, die in einer Vielzahl von Formen innerhalb des Windows 10-Betriebssystems vorkommen, sind die Aushängeschilder für Ihre App für die Universelle Windows-Plattform (UWP). In diesen Richtlinien wird beschrieben, wo Ressourcen für App-Symbole im System angezeigt werden, und Sie erhalten ausführliche Designtipps zum Erstellen ansprechender Symbole.

![Starten von Windows10 und Kacheln](images/assetguidance01.jpg)

## <a name="adaptive-scaling"></a>Adaptive Skalierung


Zunächst erhalten Sie einen kurzen Überblick über die adaptive Skalierung, um die Funktion der Skalierung mit Ressourcen verstehen zu können. Mit Windows10 wird eine Weiterentwicklung des vorhandenen Skalierungsmodells eingeführt. Neben der Skalierung von Vektorinhalten gibt es einen einheitlichen Satz von Skalierungsfaktoren, der eine einheitliche Größe für UI-Elemente für eine Vielzahl von Bildschirmgrößen und -auflösungen bietet. Die Skalierungsfaktoren sind auch mit den Skalierungsfaktoren anderer Betriebssysteme wie iOS und Android kompatibel, sodass die Ressourcen einfacher für alle diese Plattformen verwendet werden können.

Die Auswahl der aus dem Store herunterzuladenden Ressourcen erfolgt zum Teil auf Grundlage des DPI-Werts eines Geräts. Nur die Ressourcen, die dem Gerät am besten entsprechen, werden heruntergeladen.

## <a name="tile-elements"></a>Kachelelemente


Die grundlegenden Komponenten einer Startkachel sind eine Rückwand, ein Symbol, eine Brandingleiste, Ränder und ein App-title:

![Aufschlüsselung der Kachelelemente](images/assetguidance02.png)

Auf der Brandingleiste am unteren Rand einer Kachel werden der App-Name, die Signalgebung und der Zähler (falls verwendet) angezeigt:

![Brandingleiste in der Kachel](images/assetguidance03.png)

Die Höhe der Brandingleiste basiert auf dem Skalierungsfaktor des Geräts, auf dem sie angezeigt wird:

| Skalierungsfaktor | Pixel |
|--------------|--------|
| 100%         | 32     |
| 125%         | 40     |
| 150%         | 48     |
| 200%         | 64     |
| 400%         | 128    |

 

Die Ränder der Kachel werden vom System festgelegt und können nicht geändert werden. Die meisten Inhalte werden innerhalb der Ränder angezeigt, wie in diesem Beispiel:

![Kachelfassaden](images/assetguidance04.png)

Die Randbreite basiert auf dem Skalierungsfaktor des Geräts, auf dem sie angezeigt wird:

| Skalierungsfaktor | Pixel |
|--------------|--------|
| 100%         | 8      |
| 125%         | 10     |
| 150%         | 12     |
| 200%         | 16     |
| 400%         | 32     |

 

## <a name="tile-assets"></a>Kachelressourcen


Jede Kachelressource hat die gleiche Größe wie die Kachel, auf der sie sich befindet. Sie können die App-Kacheln mit zwei unterschiedlichen Darstellungsformen einer Ressource kennzeichnen:

1. Ein zentriertes Symbol oder Logo mit Abstand. Auf diese Weise scheint die Farbe der Rückwand durch:

![Kachel und Rückwand](images/assetguidance05.png)

2. Eine randlose Brandingkachel ohne Abstand:

![Randlose Kachel](images/assetguidance06.png)

Zum Zweck der Einheitlichkeit auf allen Geräten hat jede Kachelgröße (klein, mittel, breit und groß) eine eigene Größenbeziehung. Um eine einheitliche Symbolanordnung auf allen Kacheln zu erreichen, empfehlen wir einige grundlegende Abstandsrichtlinien für die folgenden Kachelgrößen. Der Bereich, in dem zwei violette Überlagerungen schneiden, ist die ideale Fläche für ein Symbol. Symbole passen zwar nicht immer genau in die Fläche, das visuelle Volumen eines Symbols sollte aber ungefähr den dargestellten Beispielen entsprechen.

Kleine Kachelgröße:

![Beispiel für kleine Kachelgröße](images/assetguidance07a.png)

Mittlere Kachelgröße:

![Beispiel für mittlere Kachelgröße](images/assetguidance07b.png)

Breite Kachelgröße:

![Beispiel für breite Kachelgröße](images/assetguidance07c.png)

Große Kachelgröße:

![Beispiel für große Kachelgröße](images/assetguidance07d.png)

In diesem Beispiel ist das Symbol für die Kachel zu groß:

![Symbol zu groß für die Kachel](images/assetguidance08a.png)

In diesem Beispiel ist das Symbol für die Kachel zu klein:

![Symbol zu klein für die Kachel](images/assetguidance08b.png)

Die folgenden Abstandsverhältnisse sind optimal für horizontal oder vertikal ausgerichtete Symbole.

Beschränken Sie bei kleinen Kacheln die Breite und Höhe auf 66% der Kachelgröße:

![Verhältnisse bei kleinen Kachelgrößen](images/assetguidance09.png)

Beschränken Sie bei mittelgroßen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße. Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:

![Verhältnisse bei mittelgroßen Kacheln](images/assetguidance10.png)

Beschränken Sie bei breiten Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße. Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:

![Verhältnisse bei breiten Kacheln](images/assetguidance11.png)

Beschränken Sie bei großen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße:

![Verhältnisse bei großen Kacheln](images/assetguidance12.png)

Einige Symbole sind so konzipiert, dass sie horizontal oder vertikal ausgerichtet sind, andere Symbole hingegen weisen komplexere Formen auf, wodurch verhindert wird, dass sie direkt in die Zielabmessungen passen. Symbole, die zentriert erscheinen, können auf eine Seite geneigt sein. In diesem Fall können Teile eines Symbols aus der empfohlenen Fläche heraushängen, vorausgesetzt, das Symbol belegt dasselbe visuelle Gewicht wie ein genau passendes Symbol:

![Drei zentrierte Symbole](images/assetguidance13.png)

Berücksichtigen Sie bei randlosen Ressourcen Elemente, die innerhalb der Ränder und Kanten der Kacheln interagieren. Behalten Sie Ränder von mindestens 16 % der Höhe oder Breite der Kachel bei. Dieser Prozentsatz stellt die doppelte Breite der Ränder bei den kleinsten Kachelgrößen dar:

![Randlose Kachel mit Rändern](images/assetguidance14.png)

In diesem Beispiel sind die Ränder zu eng:

![Randlose Kachel mit zu engen Rändern](images/assetguidance15.png)

## <a name="tile-assets-in-list-views"></a>Kachelressourcen in Listenansichten


Kacheln können auch in einer Listenansicht angezeigt werden. Größenrichtlinien für Kachelressourcen, die in Listenansichten angezeigt werden, unterscheiden sich leicht von den zuvor aufgeführten Kachelressourcen. In diesem Abschnitt werden diese Einzelheiten bei der Größe erläutert.

![Kachelressourcen in einer Listenansicht](images/assetguidance16.png)

Beschränken Sie die Breite und Höhe von Symbolen auf 75% der Kachelgröße:

![Größe eines Symbols einer Listenansichtkachel](images/assetguidance17.png)

Beschränken Sie bei vertikalen und horizontalen Symbolformaten die Breite und Höhe auf 75% der Kachelgröße:

![Größe eines Symbols einer Listenansichtkachel](images/assetguidance18.png)

Behalten Sie bei randlosen Grafiken wichtiger Brandingelemente Ränder von 12,5% bei:

![Randlose Grafiken in Listenansichtkachel](images/assetguidance19.png)

In diesem Beispiel ist das Symbol in der Kachel zu groß:

![Symbol für die Kachel zu groß](images/assetguidance20a.png)

In diesem Beispiel ist das Symbol in der Kachel zu klein:

![Symbol für die Kachel zu klein](images/assetguidance20b.png)

## <a name="target-based-assets"></a>Zielbasierte Ressourcen


Zielbasierte Ressourcen gelten für Symbole und Kacheln, die in der Windows-Taskleiste, in der Aufgabenansicht, über ALT+TAB, in der Andockhilfe und in der unteren rechten Ecke von Startkacheln angezeigt werden. Sie müssen für diese Ressourcen keine Abstände hinzufügen, diese werden bei Bedarf von Windows hinzugefügt. Bei diesen Ressourcen sollte eine minimale Fläche von 16Pixeln vorgesehen werden. Unten sehen Sie ein Beispiel dafür, wie diese Ressourcen als Symbole in der Windows-Taskleiste angezeigt werden:

![Ressourcen in Windows-Taskleiste](images/assetguidance21.png)

Diese Benutzeroberfläche verwendet zwar neben einer farbigen Rückwand standardmäßig eine zielbasierte Ressource, Sie können aber auch eine zielbasierte Ressource ohne Anpassung verwenden. Ressourcen ohne Anpassung sollten so erstellt werden, dass es möglich ist, sie in unterschiedlichen Hintergrundfarben anzuzeigen.

![Ressourcen mit und ohne Anpassung](images/assetguidance22.png)

Nachfolgend finden Sie die Größenempfehlungen für zielbasierte Ressourcen mit einer Skalierung von 100%:

![Zielbasierte Ressourcengröße bei einer Skalierung von 100%](images/assetguidance23.png)

## <a name="splash-screen-assets"></a>Ressourcen für den Begrüßungsbildschirm


Das Bild für den Begrüßungsbildschirm kann als direkter Pfad zu einer Bilddatei oder als Ressource angegeben werden. Mithilfe eines Ressourcenverweises können Sie Bilder mit verschiedenen Skalierungen bereitstellen, damit Windows die optimale Größe für das jeweilige Gerät und die Bildschirmauflösung auswählen kann. Sie können auch Bilder mit hohem Kontrast für die Barrierefreiheit sowie lokalisierte Bilder für verschiedene Benutzeroberflächensprachen bereitstellen.

Wenn Sie „Package.appxmanifest“ in einem Text-Editor öffnen, wird das [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br211467)-Element als untergeordnetes Element des [**VisualElements**](https://msdn.microsoft.com/library/windows/apps/br211471)-Elements angezeigt. Das standardmäßige Begrüßungsbildschirm-Markup in der Manifestdatei sieht in einem Text-Editor wie folgt aus:

```XML
<uap:SplashScreen Image="Assets\SplashScreen.png" /></code></pre></td>
</tr>
</tbody>
</table>
```

Die Ressource für den Begrüßungsbildschirm wird von jedem Gerät zentriert, auf dem er angezeigt wird:

![Größe der Ressource für den Begrüßungsbildschirm](images/assetguidance27.png)

## <a name="high-contrast-assets"></a>Ressourcen mit hohem Kontrast


Der Modus mit hohem Kontrast verwendet separate Sätze von Ressourcen für kontrastreiches Weiß (weißer Hintergrund mit schwarzem Text) und kontrastreiches Schwarz (schwarzer Hintergrund mit weißem Text). Wenn Sie keine Ressourcen mit hohem Kontrast für Ihre App angeben, werden die Standardressourcen verwendet.

Wenn die Standardressourcen für Ihre App eine akzeptable Anzeigeumgebung bei einem schwarzweißen Hintergrund bieten, sollte Ihre App im Modus mit hohem Kontrast zumindest zufriedenstellend aussehen. Wenn Ihre die Standardressourcen keine akzeptable Anzeigeumgebung bei einem schwarzweißen Hintergrund liefern, sollten Sie in Betracht ziehen, Ressourcen mit hohem Kontrast zu verwenden. Die folgenden Beispiele zeigen die zwei Arten von Ressourcen mit hohem Kontrast:

![Beispiele für hohes Kontrastverhältnis](images/assetguidance28.png)

Wenn Sie Ressourcen mit hohem Kontrast bereitstellen möchten, müssen Sie beide Sätze – weiß auf schwarz und schwarz auf weiß – verwenden. Wenn Sie diese Ressourcen in Ihr Paket aufnehmen, können Sie einen Ordner "Kontrast Schwarz" für weiß auf schwarz, und einen Ordner "Kontrast Weiß" für schwarz auf weiß erstellen.

## <a name="asset-size-tables"></a>Größentabellen


Es wird dringend empfohlen, dass Sie mindestens Ressourcen für die Skalierungsfaktoren 100, 200 und 400 Skalierungsfaktoren bereitstellen. Wenn Sie Ressourcen für alle Skalierungsfaktoren bereitstellen, liefert dies eine optimale Benutzererfahrung.

<br/>

<table>
<thead>
<tr><th colspan="3">Kleine Kachel (Square71x71Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">Skalierung von 100 %</td>
    <td width="20%">71 x 71</td>
    <td>Square71x71Logo.scale-100.png</td>
</tr>
<tr>
    <td>Skalierung von 125 %</td>
    <td>89 x 89</td>
    <td>Square71x71Logo.scale-125.png</td>
</tr>
<tr>
    <td>Skalierung von 150 %</td>
    <td>107 x 107</td>
    <td>Square71x71Logo.scale-150.png</td>
</tr>
<tr>
    <td>Skalierung von 200 %</td>
    <td>142 x 142</td>
    <td>Square71x71Logo.scale-200.png</td>
</tr>
<tr>
    <td>Skalierung von 400 %</td>
    <td>284x284</td>
    <td>Square71x71Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">Mittelgroße Kachel (Square150x150Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">Skalierung von 100 %</td>
    <td width="20%">150x150</td>
    <td>Square150x150Logo.scale-100.png</td>
</tr>
<tr>
    <td>Skalierung von 125 %</td>
    <td>188 x 188</td>
    <td>Square150x150Logo.scale-125.png</td>
</tr>
<tr>
    <td>Skalierung von 150 %</td>
    <td>225 x 225</td>
    <td>Square150x150Logo.scale-150.png</td>
</tr>
<tr>
    <td>Skalierung von 200 %</td>
    <td>300 x 300</td>
    <td>Square150x150Logo.scale-200.png</td>
</tr>
<tr>
    <td>Skalierung von 400 %</td>
    <td>600 x 600</td>
    <td>Square150x150Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">Breite Kachel (Wide310x150Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">Skalierung von 100 %</td>
    <td width="20%">310x150</td>
    <td>Wide310x150Logo.scale-100.png</td>
</tr>
<tr>
    <td>Skalierung von 125 %</td>
    <td>388 x 188</td>
    <td>Wide310x150Logo.scale-125.png</td>
</tr>
<tr>
    <td>Skalierung von 150 %</td>
    <td>465 x 225</td>
    <td>Wide310x150Logo.scale-150.png</td>
</tr>
<tr>
    <td>Skalierung von 200 %</td>
    <td>620 x 300</td>
    <td>Wide310x150Logo.scale-200.png</td>
</tr>
<tr>
    <td>Skalierung von 400 %</td>
    <td>1240 x 600</td>
    <td>Wide310x150Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">Große Kachel (Square310x310Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">Skalierung von 100 %</td>
    <td width="20%">310x310</td>
    <td>Square310x310Logo.scale-100.png</td>
</tr>
<tr>
    <td>Skalierung von 125 %</td>
    <td>388 x 388</td>
    <td>Square310x310Logo.scale-125.png</td>
</tr>
<tr>
    <td>Skalierung von 150 %</td>
    <td>465 x 465</td>
    <td>Square310x310Logo.scale-150.png</td>
</tr>
<tr>
    <td>Skalierung von 200 %</td>
    <td>620 x 620</td>
    <td>Square310x310Logo.scale-200.png</td>
</tr>
<tr>
    <td>Skalierung von 400 %</td>
    <td>1240 x 1240</td>
    <td>Square310x310Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">App-Listensymbol (Square44x44Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">Skalierung von 100 %</td>
    <td width="20%">44 x 44</td>
    <td>Square44x44Logo.scale-100.png</td>
</tr>
<tr>
    <td>Skalierung von 125 %</td>
    <td>55 x 55</td>
    <td>Square44x44Logo.scale-125.png</td>
</tr>
<tr>
    <td>Skalierung von 150 %</td>
    <td>66 x 66</td>
    <td>Square44x44Logo.scale-150.png</td>
</tr>
<tr>
    <td>Skalierung von 200 %</td>
    <td>88 x 88</td>
    <td>Square44x44Logo.scale-200.png</td>
</tr>
<tr>
    <td>Skalierung von 400 %</td>
    <td>176 x 176</td>
    <td>Square44x44Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">Begrüßungsbildschirm (SplashScreen)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">Skalierung von 100 %</td>
    <td width="20%">620 x 300</td>
    <td>SplashScreen.scale-100.png</td>
</tr>
<tr>
    <td>Skalierung von 125 %</td>
    <td>775 x 375</td>
    <td>SplashScreen.scale-125.png</td>
</tr>
<tr>
    <td>Skalierung von 150 %</td>
    <td>930 x 450</td>
    <td>SplashScreen.scale-150.png</td>
</tr>
<tr>
    <td>Skalierung von 200 %</td>
    <td>1240 x 600</td>
    <td>SplashScreen.scale-200.png</td>
</tr>
<tr>
    <td>Skalierung von 400 %</td>
    <td>2480 x 1200</td>
    <td>SplashScreen.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>
 

**Zielbasierte Ressourcen**

Zielbasierte Ressourcen werden über mehrere Skalierungsfaktoren hinweg verwendet. Der Elementname für zielbasierte Ressourcen ist **Square44x44Logo**. Es wird dringend empfohlen, mindestens die folgenden Ressourcen zu übermitteln:

16 x 16, 24 x 24, 32 x 32, 48 x 48, 256 x 256

Die folgende Tabelle enthält alle zielbasierten Ressourcengrößen und die entsprechenden Dateinamenbeispiele:

| Ressourcengröße | Dateinamenbeispiel                  |
|------------|------------------------------------|
| 16 x 16\*    | Square44x44Logo.targetsize-16.png  |
| 24 x 24\*    | Square44x44Logo.targetsize-24.png  |
| 32 x 32\*    | Square44x44Logo.targetsize-32.png  |
| 48 x 48\*    | Square44x44Logo.targetsize-48.png  |
| 256 x 256\*  | Square44x44Logo.targetsize-256.png |
| 20 x 20      | Square44x44Logo.targetsize-20.png  |
| 30x30      | Square44x44Logo.targetsize-30.png  |
| 36 x 36      | Square44x44Logo.targetsize-36.png  |
| 40 x 40      | Square44x44Logo.targetsize-40.png  |
| 60 x 60      | Square44x44Logo.targetsize-60.png  |
| 64 x 64      | Square44x44Logo.targetsize-64.png  |
| 72 x 72      | Square44x44Logo.targetsize-72.png  |
| 80 x 80      | Square44x44Logo.targetsize-80.png  |
| 96 x 96      | Square44x44Logo.targetsize-96.png  |

 

\* Übermitteln Sie diese Ressourcengrößen als Basislinie

## <a name="asset-types"></a>Ressourcentypen


Nachfolgend sind alle Ressourcentypen, ihre Anwendungsmöglichkeiten sowie die empfohlenen Dateinamen aufgeführt.

**Kachelressourcen**

-   Zentrierte Ressourcen werden in der Regel auf der Startseite zum Präsentieren Ihrer App verwendet.
-   Dateinamenformat: [Square\Wide]\*x\*Logo.scale-\*.png
-   Betroffene Apps: Jede UWP-App
-   Anwendungsmöglichkeiten:
    -   Standard-Startkacheln (Desktop und mobil)
    -   Info-Center (Desktop und mobil)
    -   Aufgabenumschaltfunktion (mobil)
    -   Freigabeauswahl (mobil)
    -   Datumsauswahl (mobil)
    -   Store

**Skalierbare Listeressourcen mit Anpassung**

-   Diese Ressourcen werden auf Flächen verwendet, die Skalierungsfaktoren erfordern. Diese Ressourcen werden vom System angepasst oder weisen ihre eigene Hintergrundfarbe auf, wenn die App diese enthält.
-   Dateinamenformat: Square44x44Logo.scale-\*.png
-   Betroffene Apps: Jede UWP-App
-   Anwendungsmöglichkeiten:
    -   Starten der Liste aller Apps (Desktop)
    -   Liste zum Starten der am häufigsten verwendeten Apps (Desktop)
    -   Task-Manager (Desktop)
    -   Cortana-Suchergebnisse
    -   Liste zum Starten aller Apps (mobil)
    -   Einstellungen

**Zielgröße-Listenressourcen mit Anpassung**

-   Dies sind feste Größen, die nicht skaliert werden. Sie werden meistens für ältere Umgebungen verwendet. Ressourcen werden vom System überprüft.
-   Dateinamenformat: Square44x44Logo.targetsize-\*.png
-   Betroffene Apps: Jede UWP-App
-   Anwendungsmöglichkeiten:
    -   Starten der Sprungliste (Desktop)
    -   Starten der unteren Ecke der Kachel (Desktop)
    -   Tastenkombinationen (Desktop)
    -   Systemsteuerung (Desktop)

**Zielgröße-Listenressourcen ohne Anpassung**

-   Dies sind Objekte, die nicht vom System angepasst oder skaliert werden.
-   Dateinamenformat: Square44x44Logo.targetsize-\*\_altform-unplated.png
-   Betroffene Apps: Jede UWP-App
-   Anwendungsmöglichkeiten:
    -   Taskleiste und Miniaturansicht der Taskleiste (Desktop)
    -   Taskleisten-Sprungliste
    -   Aufgabenansicht
    -   ALT + TAB

**Dateierweiterungsressourcen**

-   Hierbei handelt es sich um spezielle Ressourcen für Dateierweiterungen. Sie werden neben Win32-Dateizuordnungssymbolen im Datei-Explorer angezeigt und müssen designunabhängig sein. Die Größe ist auf Desktops und mobilen Plattformen unterschiedlich.
-   Dateinamenformat: \*LogoExtensions.targetsize-\*.png
-   Betroffene Apps: Musik, Video, Fotos, Microsoft Edge, Microsoft Office
-   Anwendungsmöglichkeiten:
    -   Datei-Explorer
    -   Cortana
    -   Verschiedene Benutzeroberflächen (Desktop)

**Begrüßungsbildschirm**

-   Die Ressource, die auf dem Begrüßungsbildschirm Ihrer App angezeigt wird. Automatische Skalierung auf Desktops und mobilen Plattformen.
-   Dateinamenformat: SplashScreen.scale-*.png
-   Betroffene Apps: Jede UWP-App
-   Anwendungsmöglichkeiten:
    -   Begrüßungsbildschirm der App