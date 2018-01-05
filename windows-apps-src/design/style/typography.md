---
author: mijacobs
description: "Typografie muss übersichtlich sein, da sie zur visuellen Darstellung von Sprache dient. Ihr Stil darf diesem Ziel nie im Wege stehen. Typografie spielt jedoch auch als Layoutkomponente eine wichtige Rolle und wirkt sich maßgeblich auf die Dichte und Komplexität des Designs und damit auf die Benutzerfreundlichkeit des Designs aus."
title: Typografie
ms.assetid: ca35f78a-e4da-423d-9f5b-75896e0b8f82
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: bec416694e347a1432892f9dc591afdfe8548e61
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="typography"></a>Typografie

Typografie muss übersichtlich sein, da sie zur visuellen Darstellung von Sprache dient. Ihr Stil darf diesem Ziel nie im Wege stehen. Typografie spielt jedoch auch als Layoutkomponente eine wichtige Rolle und wirkt sich maßgeblich auf die Dichte und Komplexität des Designs und damit auf die Benutzerfreundlichkeit des Designs aus.

## <a name="typeface"></a>Schriftart

Wir haben uns dafür entschieden, für alle digitalen Microsoft-Designs „SegoeUI“ zu verwenden. „SegoeUI“ bietet eine breite Palette von Zeichen und zeichnet sich durch optimale Lesbarkeit bei unterschiedlichsten Größen und Pixeldichten aus. Die klare, ansprechende und offene Ästhetik passt perfekt zum Inhalt des Systems.

![Beispieltext für die Schriftart „SegoeUI“](images/segoe-sample.png)

## <a name="weights"></a>Breiten

Bei der Typografie legen wir unter anderem Wert auf Schlichtheit und Effizienz. Wir verwenden eine einzelne Schriftart, eine geringe Anzahl von Schriftbreiten und -graden sowie eine klare Hierarchie. Positionierung und Ausrichtung basieren auf dem Standardstil für die jeweilige Sprache. Im Deutschen wird Text von links nach rechts und von oben nach unten verwendet. Beziehungen zwischen Text und Bildern sind klar und einfach.

![Unterstützte Schriftbreiten: „Light“, „Semilight“, „Regular“, „Semibold“ und „Bold“](images/weights.png)

## <a name="line-spacing"></a>Zeilenabstand

![Beispiel für einen Zeilenabstand von 125Prozent](images/line-spacing.png)

Der Zeilenabstand muss mit 125Prozent des Schriftgrads berechnet und bei Bedarf auf das nächste Vielfache von Vier gerundet werden. Bei SegoeUI mit 15px wären 125Prozent beispielsweise 18,75px. Wir empfehlen, den Wert aufzurunden und den Zeilenabstand auf 20px festzulegen, um dem 4px-Raster zu entsprechen. Dadurch wird eine gute Lesbarkeit gewährleistet, und es steht ausreichend Platz für diakritische Zeichen zur Verfügung. Spezifische Beispiele finden Sie weiter unten im Abschnitt „Typhierarchie“.

Wird sich größere Schrift über kleinerer Schrift befindet, muss der Abstand zwischen der letzten Grundlinie der größeren Schrift und der ersten Grundlinie der kleineren Schrift dem Zeilenabstand der größeren Schrift entsprechen.

![Große Schrift über kleinerer Schrift](images/line-height-stacking.png)

Im XAML-Code wird dies durch Stapeln zweier [TextBlock](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.textblock.aspx)-Elemente sowie durch Festlegen des entsprechenden Rands erreicht.

```xaml
<StackPanel Width="200">
    <!-- Setting a bottom margin of 3px on the header
         puts the baseline of the body text exactly 24px
         below the baseline of the header. 24px is the
         recommended line height for a 20px font size,
         which is what’s set in SubtitleTextBlockStyle.
         The bottom margin will be different for
         different font size pairings. -->
    <TextBlock
        Style="{StaticResource SubtitleTextBlockStyle}"
        Margin="0,0,0,3"
        Text="Header text" />
    <TextBlock
        Style="{StaticResource BodyTextBlockStyle}"
        TextWrapping="Wrap"
        Text="This line of text should be positioned where the above header would have wrapped." />
</StackPanel>
```


<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
<h2>Kerning und Laufweite</h2>

Segoe ist eine humanistische Schriftart mit weicher, ansprechender Optik und organischen, offenen Formen, die von handschriftlichen Texten inspiriert sind. Um eine optimale Lesbarkeit zu gewährleisten und den humanistischen Charakter zu bewahren, müssen für Kerning und Laufweite bestimmte Werte verwendet werden.

Kerning muss auf „Metrik“ und die Laufweite auf„0“ festgelegt werden.
  </div>
  <div class="side-by-side-content-right">
<h2>Wort- und Zeichenabstand</h2>

Ähnlich wie bei Kerning und Laufweite werden auch beim Wort- und Zeichenabstand bestimmte Einstellungen verwendet, um eine optimale Lesbarkeit und die Wahrung des humanistischen Charakters zu gewährleisten.

Der Wortabstand beträgt standardmäßig immer 100Prozent. Der Zeichenabstand muss auf„0“ festgelegt werden.
  </div>
</div>
</div>
<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
![Der Unterschied zwischen Kerning und Laufweite](images/kerning-tracking.png)  
  </div>
  <div class="side-by-side-content-right">
![Der Unterschied zwischen Wort- und Zeichenabstand.](images/word-letter.png) 
  </div>
</div>
</div>


>[!NOTE]
>Verwenden Sie in einem XAML-Textsteuerelement [Typogrphy.Kerning](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.typography.kerning.aspx), um das Kerning zu steuern, und [FontStretch](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_FontStretch). um die Nachverfolgung zu steuern. Typography.Kerning ist standardmäßig auf „true“ und FontStretch ist standardmäßig auf „Normal“ festgelegt. Dies sind die empfohlenen Werte.

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
<h2>Ausrichtung</h2>

Im Allgemeinen wird die linksbündige Ausrichtung visueller Elemente und Spalten mit Schrift empfohlen. In den meisten Fällen sorgt das Konzept „links bündig, rechts mit Flatterrand“ für eine konsistente Verankerung des Inhalts und für ein einheitliches Layout. 
  </div>
  <div class="side-by-side-content-right">
<h2>Zeilenenden</h2>

Wenn Typografie nicht linksbündig mit rechtem Flatterrand positioniert wird, versuchen Sie, gleichmäßige Zeilenenden zu erreichen, und vermeiden Sie die Verwendung von Silbentrennung.
  </div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
![Zeigt linksbündigen Text.](images/alignment.png)  
  </div>
  <div class="side-by-side-content-right">
![Zeigt gleichmäßige Zeilenenden.](images/line-endings.png) 
  </div>
</div>
</div>


## <a name="paragraphs"></a>Absätze

Absätze müssen als übersprungene Zeile ohne Einzug dargestellt werden, um aufeinander abgestimmte Spaltenränder zu erhalten.

![Vollständige Leerzeile zwischen Absätzen](images/paragraphs.png)

## <a name="character-count"></a>Zeichenanzahl

Ist eine Zeile zu kurz, muss das Auge zu oft hin und her bewegt werden, was den Lesefluss stört. Verwenden Sie daher möglichst50 bis 60Wörter pro Zeile. Dies bietet den höchsten Lesekomfort.

Segoe bietet eine breite Palette von Zeichen und zeichnet sich durch optimale Lesbarkeit bei unterschiedlichen Größen und Pixeldichten aus. Eine optimale Anzahl von Buchstaben in einer Textspaltenzeile erhöht den Lesekomfort in einer Anwendung.

Zu lange Zeilen können für den Benutzer anstrengend und verwirrend sein. Bei zu kurzen Zeilen muss das Auge zu viel hin und her bewegt werden, was sich als ermüdend erweisen kann.

![Drei Absätze mit unterschiedlichen Zeilenlängen](images/character-count.png)

## <a name="hanging-text-alignment"></a>Ausrichtung von hängendem Text

Die horizontale Ausrichtung von Symbolen mit Text kann je nach Symbolgröße und Textmenge auf unterschiedliche Arten gehandhabt werden. Wenn der Text (einzelne Zeile oder mehrere Zeilen) die Höhe des Symbols nicht übersteigt, muss der Text vertikal zentriert werden.

Sobald die Höhe des Texts die Höhe des Symbols übersteigt, muss die erste Textzeile vertikal ausgerichtet werden, und der weitere Text muss dem natürlichen Textfluss folgen. Für höhere Großbuchstaben bzw. Zeichen mit höherer Ober- und Unterlänge gelten die gleichen Ausrichtungsrichtlinien.

![Mehrere Kombinationen aus Symbol und Text](images/hanging-text-alignment.png)

>[!NOTE]
>Die XAML-Eigenschaft [TextBlock.TextLineBounds](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.textblock.textlinebounds.aspx) ermöglicht den Zugriff auf die Höhe von Großbuchstaben und die Metrik der Basisschriftart. Sie kann verwendet werden, um visuell vertikal zu zentrieren oder oben ausgerichtet einzugeben.

## <a name="clipping-and-ellipses"></a>Beschnitt und Ellipsen

Nutzen Sie standardmäßig das Beschnittkonzept, und gehen Sie davon aus, dass der Text umgebrochen wird – es sei denn, es ist etwas anderes angegeben. Bei Verwendung von nicht umgebrochenem Text empfiehlt es sich, anstelle von Ellipsen den Beschnitt zu verwenden. Der Beschnitt kann am Rand des Containers, am Rand des Geräts, am Rand der Bildlaufleiste usw. erfolgen.

Ausnahme: Bei Containern, die nicht klar definiert sind (also sich etwa nicht durch eine andere Hintergrundfarbe abheben), kann eine Ellipse(...) verwendet werden.

![Gerät mit abgeschnittenem Text](images/clipping.png)

## <a name="type-ramp"></a>Typhierarchie
Die Typhierarchie stellt eine wichtige gestalterische Beziehung zwischen Überschrift und Textkörper her und schafft damit eine klare und verständliche Hierarchie zwischen den verschiedenen Ebenen. Diese Hierarchie bildet eine Struktur, die Benutzern die Navigation durch schriftliche Kommunikation erleichtert.

<div class="uwpd-image-with-caption">
    <img src="images/type-ramp.png" alt="Shows the type ramp" />
    <div>Die Größe wird jeweils in effektiven Pixeln angegeben. Weitere Informationen finden Sie unter [Einführung in das UWP-App-Design](../basics/design-and-ui-intro.md).</div>
</div>

>[!NOTE]
>Die meisten Ebenen der Typhierarchie sind in XAML als [statische Ressourcen](https://msdn.microsoft.com/en-us/library/windows/apps/Mt187274.aspx#the_xaml_type_ramp) verfügbar, die der `*TextBlockStyle`-Benennungskonvention folgen (z.B.: `HeaderTextBlockStyle`).


<!--
<div class="microsoft-internal-note">
SubtitleAlt, BaseAlt, and CaptionAlt are not currently included. You can create the styles in your own app following the code snippets in the above link. Also note that XAML does not currently match the line height exactly.
</div>
-->


## <a name="primary-and-secondary-text"></a>Primärer und sekundärer Text

Zur Erweiterung der Typhierarchie kann die Deckkraft des sekundären Texts auf 60Prozent festgelegt werden. In der [Farbschemapalette](color.md#themes) wird dafür „BaseMedium“ verwendet. Der primäre Text muss immer eine Deckkraft von 100Prozent (BaseHigh) besitzen.

<!-- Need new images
![Two phone apps using SubtitleAlt](images/type-ramp-example-2.png)
Recommended use of SubtitleAlt. Also note the primary and secondary text usage in list items.

![Two phone apps using CaptionAlt](images/type-ramp-example-1.png)
Recommended use of CaptionAlt.
-->

## <a name="all-caps-titles"></a>Titel in Großbuchstaben

Bestimmte Seitentitel sollten in GROSSBUCHSTABEN angegeben werden, um die Hierarchie um eine weitere Dimension zu erweitern. Diese Titel müssen „BaseAlt“ und einen Zeichenabstand von 0,075em verwenden. Dies kann auch bei der App-Navigation hilfreich sein.

In bestimmten Sprachen ändert sich durch eine Großschreibung jedoch die Bedeutung von Eigennamen. Daher dürfen auf Namen oder Benutzereingaben basierende Seitentitel *nicht* in Großbuchstaben umgewandelt werden.


<!-- Need new images
![Shows several apps where they should and should not use all caps](images/all-caps.png)
Green shows where all caps should be used. Red shows where it should not.
-->

## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen
* Verwenden Sie „Body“ für die meisten Texte.
* Verwenden Sie „Base“ für Titel mit begrenztem Platz.
* Integrieren Sie „SubtitleAlt“, um durch Hervorhebung des übergeordneten Inhalts einen Kontrast und eine Hierarchie zu schaffen.
* Verwenden Sie „Caption“ nicht für lange Zeichenfolgen oder Hauptaktionen.
* Verwenden Sie „Header“ oder „Subheader“ nicht, wenn der Text umgebrochen werden muss.
* Verwenden Sie „Subtitle“ und „SubtitleAlt“ nicht auf der gleichen Seite.


## <a name="related-articles"></a>Verwandte Artikel

* [Textsteuerelemente](../controls-and-patterns/text-controls.md)
* [Schriftarten](../style/fonts.md)
* [Segoe MDL2-Symbole](segoe-ui-symbol-font.md)
