---
title: Kompositionsbeleuchtung
description: Die Composition-APIs Beleuchtung kann zum Hinzufügen von dynamischen 3D Beleuchtung für Ihre Anwendung verwendet werden.
ms.date: 07/16/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d8c33504fcc785aa2f1fc94796e47fe097fbea96
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8887222"
---
# <a name="using-lights-in-windows-ui"></a>Verwendung von Licht in Windows-Benutzeroberfläche

Die Windows.UI.Composition-APIs können Sie in Echtzeit Animationen und Effekte zu erstellen. Kompositionsbeleuchtung ermöglicht 3D Beleuchtung in 2D Anwendungen. In dieser Übersicht wird wir führen Sie über die Funktionen zum Einrichten der Komposition Licht, visuelle Elemente zum Empfangen von einzelnen Lichtquellen zu identifizieren und Effekte verwenden, um Materialien für den Inhalt zu definieren.

> [!NOTE]
> Wie [XamlLight](/uwp/api/windows.ui.xaml.media.xamllight) Objekte [CompositionLights](/uwp/api/Windows.UI.Composition.CompositionLight) um XAML-UI-Elemente beleuchtet anwenden, finden Sie unter [XAML-Beleuchtung](xaml-lighting.md).

Kompositionsbeleuchtung ermöglicht die Erstellung interessante Benutzeroberflächen ermöglichen:

- Die Transformation der ein Licht unabhängig von anderen Objekten in der Szene immersive Szenarien wie Musik Medienwiedergabe im Hintergrund zu aktivieren.
- Die Möglichkeit, ein Objekt mit einer koppeln, sodass sie zusammen verschoben unabhängig vom Rest der Szene Szenarien wie Fluent- [Reveal-](/design/style/reveal.md) Highlight ermöglichen.
- Transformation und die gesamte Szene als Gruppe Materialien und Tiefe zu erstellen.

Kompositionsbeleuchtung unterstützt drei wichtige Konzepte: **Licht**, **Ziele**und **SceneLightingEffect**.

## <a name="light"></a>Licht

[CompositionLight](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlight) können Sie verschiedene Licht zu erstellen und speichern Sie sie im Koordinatenbereich. Diese Lichtquellen als Ziel visuelle Elemente, die Sie vom Licht beleuchtet festlegen möchten.

### <a name="light-types"></a>Lichttypen

| Typ | Beschreibung |
| --- | --- |
| [AmbientLight](/uwp/api/windows.ui.composition.ambientlight) | Von alles in der Szene reflektiert wird eine Lichtquelle, die nicht direktionale Licht ausgibt, die angezeigt wird. |
| [DistantLight](/uwp/api/windows.ui.composition.distantlight) | Ein unendlich Lichtquelle, die Licht in einer Richtung ausgibt. Wie der Sonne. |
| [PointLight](/uwp/api/windows.ui.composition.pointlight) | Ein Punkt Quelle des Lichts, die Licht in alle Richtungen ausgibt. Wie eine Glühbirne. |
| [SpotLight](/uwp/api/windows.ui.composition.spotlight) | Eine Lichtquelle, die inneren und äußeren Kegel des Lichts ausgibt. Wie eine Taschenlampe. |

## <a name="targets"></a>Ziele

Wenn Licht ein visuelles Ziel (Hinzufügen zur Liste der [Ziele](/uwp/api/windows.ui.composition.compositionlight.targets) ), die visuelle Bearbeitung und alle seine untergeordneten Elemente bekannt und reagieren auf diese Lichtquelle. Dies kann etwa so einfach wie eine Einstellung PointLight Quelle im Stammverzeichnis des eine Struktur und alle visuellen Elemente, die folgenden reagieren auf die Animation der Richtung Licht Punkt sein.

**ExclusionsFromTargets** bietet Ihnen die Möglichkeit, die Beleuchtung eines visuellen oder einer Teilstruktur von visuellen Elementen auf ähnliche Weise wie das Hinzufügen von Ziele zu entfernen. Untergeordnete Elemente in der Struktur von der visuellen, der ausgeschlossen ist daher nicht leuchtet.

### <a name="sample-targets"></a>Beispiel für (Ziele)

Im folgenden Beispiel verwenden wir ein CompositionPointLight auf einer XAML-TextBlock.

```cs
    _pointLight = _compositor.CreatePointLight();
    _pointLight.Color = Colors.White;
    _pointLight.CoordinateSpace = text; //set up co-ordinate space for offset
    _pointLight.Targets.Add(text); //target XAML TextBlock
```

Durch Hinzufügen von Animationen auf den Offset der Punktlichter, ist ein schimmernde Effekt ganz einfach.

```cs
_pointLight.Offset = new Vector3(-(float)TextBlock.ActualWidth, (float)TextBlock.ActualHeight / 2, (float)TextBlock.FontSize);
```

Finden Sie unter der vollständige [Text zu Schimmern](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/TextShimmer) Beispiel an die Küche WindowUIDevLabs Beispiel, um mehr zu erfahren.

## <a name="restrictions"></a>Einschränkungen

Es gibt mehrere Faktoren zu berücksichtigen, wenn Sie bestimmen, welche Inhalte durch CompositionLight beleuchtet wird.

Konzept | Details
--- | ---
**Umgebungslicht** | Hinzufügen einer nicht Ambiente-Beleuchtung der Szene wird deaktiviert, wenn alle vorhandenen Licht.  Elemente, die nicht durch eine nicht-Umgebungslicht bestimmt werden schwarz angezeigt.  Verwenden Sie zum umgebenden visuelle Elemente, die nicht vom Licht auf natürliche Weise als Ziel zu beleuchten, ein Umgebungslicht in Verbindung mit anderen Lichter.
**Anzahl von Lichtern** | Sie können alle zwei nicht Umgebungslicht Kompositions-Licht in beliebiger Kombination verwenden, auf der Benutzeroberfläche. Umgebungslicht Licht sind nicht beschränkt. unterschiedlichsten, sind Punkt und entfernte Licht.
**Lebensdauer** | CompositionLight kann Lebensdauer Bedingungen auftreten (Beispiel: der Garbage Collector kann das Lichtobjekt wiederverwenden, bevor sie verwendet wird).  Es wird empfohlen, einen Verweis auf die Lichter durch Hinzufügen von Licht als Mitglied der Anwendung Verwalten der Lebensdauer zu halten.
**Transformationen** | Licht müssen in einem Knoten über UI platziert werden, die Effekte wie [perspektivische Transformationen](/design/layout/3-d-perspective-effects.md) in der visuellen Struktur verwendet wird, ordnungsgemäß gezeichnet werden.
**Ziele und Koordinatenraum** | CoordinateSpace ist den Platz in dem alle die Lichter-Eigenschaften festgelegt werden müssen. CompositionLight.Targets muss in der Struktur CoordinateSpace sein.

## <a name="lighting-properties"></a>Beleuchtungseigenschaften

Je nach Art des Lichts verwendet kann ein Licht über Eigenschaften für Dämpfung und Speicherplatz verfügen. Nicht alle Lichtarten verwenden alle Eigenschaften.

Eigenschaft | Beschreibung
--- | ---
**Farbe** | Die [Farbe](/uwp/api/windows.ui.color) des Lichts. Beleuchtung Farbe, die Werte von [D3D](https://docs.microsoft.com/windows/uwp/graphics-concepts/light-properties) "Diffus", Umgebung und Glanzlicht, die die abgestrahlte Farbe definiert definiert sind. Beleuchtung verwendet RGBA-Werte für Licht. die alpha-Farbkomponente wird nicht verwendet.
**Richtung** | Die Richtung des Lichts. Die Richtung, in der das Licht strahlt, ist relativ zu den [CoordinateSpace](/uwp/api/windows.ui.composition.distantlight.coordinatespace) Visual angegeben.
**Koordinatenbereich** | Jede Visual verfügt über eine implizite 3D-Koordinatensystem. X-Richtung ist von links nach rechts. Y-Richtung wird von oben nach unten. Z-Richtung ist ein Punkt außerhalb der Ebene. Die ursprüngliche diese Koordinate ist der oberen linken Ecke des visuellen Elements aus, und die Device Independent Pixel (DIP) ist. Ein Licht Offset in diese Koordinate definiert.
**Inneren und äußeren Kegel** | Spotlights strahlen einen zweitteiligen Lichtkegel ab: einen hellen inneren Kegel und einen äußeren Kegel. Komposition ermöglicht, dass Sie die Kontrolle über inneren und äußeren Kegelwinkel und Farbe.
**Offset** | Offset der Lichtquelle relativ zu den Koordinatenbereich Visual.

> [!NOTE]
> Wenn mehrere Lichtquellen das gleiche visuelle erreicht oder wenn Farbwert des Lichts groß genug, um 1.0 überschritten wird, kann die Farbe des Lichts aufgrund der Klammerung von ein Licht Farbkanal ändern.

### <a name="advanced-lighting-properties"></a>Erweiterte Eigenschaften Beleuchtung

Eigenschaft | Beschreibung
--- | ---
**Intensität** | Steuert die Helligkeit des Lichts.
**Dämpfung** | Die Dämpfung steuert, wie die Intensität eines Lichts gegenüber der maximalen Entfernung, angegeben durch die Eigenschaft „Reichweite“, abnimmt.  Konstante, können Quadradic und linearer Dämpfungseigenschaften verwendet werden.

## <a name="getting-started-with-lighting"></a>Erste Schritte mit Beleuchtung

Führen Sie diese allgemeinen Schritte für das Licht hinzufügen:

- Erstellen und speichern Sie das Licht: Licht zu erstellen und speichern Sie sie in einem angegebenen Koordinatenraum.
- Objekte, um Licht zu identifizieren: Licht auf relevante visuelle Elemente ausgerichtet.
- [Optional] Definieren, wie einzelne Objekte reagieren auf Licht: Verwenden von SceneLightingEffect mit einer EffectBrush lichtreflektion zum Anzeigen der SpriteVisual anpassen. Reflektion Standardwerte unterstützen die Beleuchtung der untergeordneten Elemente von einer Lichtquelle CoordinateSpace.  Ein visuelles Element, das mit einem SceneLightingEffect überschreibt die Standard-Beleuchtung für dieses Visual.

## <a name="scenelightingeffect"></a>SceneLightingEffect

[SceneLightingEffect](/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect) wird verwendet, um die Standard-Beleuchtung angewendet wird, auf den Inhalt des ein [SpriteVisual](/uwp/api/Windows.UI.Composition.SpriteVisual) Ziel von einer [CompositionLight](/uwp/api/windows.ui.composition.compositionlight)zu ändern.

[SceneLightingEffect](/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect) wird häufig für die Erstellung von Material verwendet. Ein SceneLightingEffect ist ein Effekt, der verwendet wird, wenn Sie etwas komplexer sein, z. B. reflektierende Eigenschaften eines Bilds aktivieren bzw. bietet eine Illusion von Tiefe mit einer normalen Karte erreichen möchten. Eine SceneLightingEffect bietet die Möglichkeit, Ihre Benutzeroberfläche anpassen, indem Sie mithilfe der Beleuchtungseigenschaften wie und diffuse Beträge. Sie können weitere Beleuchtungseffekte mit dem Rest der Pipeline Effekte ermöglicht einzeln mischen und Verfassen von verschiedenen Beleuchtung Reaktionen mit Ihren Inhalt anpassen.

> [!NOTE]
> Beleuchtung der Szene erzeugt keine Schatten; Es ist ein Effekt, 2D Rendering konzentriert.  Es wird nicht in Betracht gezogen 3D Beleuchtung Szenarien verwendet, die tatsächliche Beleuchtung Modelle, einschließlich der Schatten enthalten.


Eigenschaft | Beschreibung
--- | ---
**Normale Karte** | NormalMaps erstellen Sie einen Effekt einer Textur, in denen ein normaler zeigt in Richtung der Lichtquelle heller, und ein normaler zeigt entfernt wird dunkler. Eine NormalMap die gezielte visual Verwendung einer [CompositionSurfaceBrush](/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) mit Loadedimagesource eine NormalMap Ressource laden hinzu.
**Umgebung** | Ambiente-Eigenschaften werden hauptsächlich zum Steuern der allgemeinen Farbe Reflektions verwendet.
**Spiegelnde** | Spiegelnden Reflektion erstellt Lichter auf Objekte gestalten glänzende angezeigt. Sie können die Ebene der spiegelnden Reflektion sowie über die Glanz steuern.  Diese Eigenschaften werden geändert, um Material Effekte wie Shinny Metalle oder glänzende Papier zu erstellen.
**Diffuse** | Diffuse Reflektion Streut Licht in alle Richtungen.
**Reflektion-Modell** | [Reflektion Modell](/uwp/api/windows.ui.composition.effects.scenelightingeffectreflectancemodel) können Sie zwischen [Blinn Phong](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-phong-shader) und physikalisch basierten Blinn Phong auswählen.  Wenn Sie Glanzlichter zusammengefasst haben möchten, würden Sie physikalisch basierten Blinn Phong auswählen.

### <a name="sample-scenelightingeffect"></a>Beispiel (SceneLightingEffect)

Das folgende Beispiel zeigt, wie Sie eine normale Karte ein SceneLightingEffect hinzufügen.

```cs
CompositionBrush CreateNormalMapBrush(ICompositionSurface normalMapImage)
{
    var colorSourceEffect = new ColorSourceEffect()
    {
        Color = Colors.White
    };
    var sceneLightingEffect = new SceneLightingEffect()
    {
        NormalMapSource = new CompositionEffectSourceParameter("NormalMap")
    };

    var compositeEffect = new ArithmeticCompositeEffect()
    {
        Source1 = colorSourceEffect,
        Source2 = sceneLightingEffect,
    };

    var factory = _compositor.CreateEffectFactory(sceneLightingEffect);

    var normalMapBrush = _compositor.CreateSurfaceBrush();
    normalMapBrush.Surface = normalMapImage;
    normalMapBrush.Stretch = CompositionStretch.Fill;

    var brush = factory.CreateBrush();
    brush.SetSourceParameter("NormalMap", normalMapBrush);

    return brush;
}
```

## <a name="related-articles"></a>Verwandte Artikel

- [Erstellen in der visuellen Ebene Material und Licht](https://blogs.windows.com/buildingapps/2017/08/04/creating-materials-lights-visual-layer/)
- [Übersicht über die Beleuchtung](https://docs.microsoft.com/windows/uwp/graphics-concepts/lighting-overview)
- [CompositionCapabilities-API](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositioncapabilities)
- [Beleuchtungsmathematik](https://docs.microsoft.com/windows/uwp/graphics-concepts/mathematics-of-lighting)
- [SceneLightingEffect](https://docs.microsoft.com/uwp/api/windows.ui.composition.effects.scenelightingeffect)
- [WindowsUIDevLabs-GitHub-Repository](https://github.com/Microsoft/WindowsUIDevLabs)
