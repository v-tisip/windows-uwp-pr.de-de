---
title: Kompositionsbeleuchtung
description: Die Composition-APIs Beleuchtung kann zum Hinzufügen von dynamischen 3D Beleuchtung für Ihre Anwendung verwendet werden.
ms.date: 07/16/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5182981483069d42339ad71a5347dc9c6c36ed58
ms.sourcegitcommit: b975c8fc8cf0770dd73d8749733ae5636f2ee296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9058741"
---
# <a name="using-lights-in-windows-ui"></a>Verwendung von Licht in Windows-Benutzeroberfläche

Die Windows.UI.Composition-APIs können Sie in Echtzeit Animationen und Effekte zu erstellen. Kompositionsbeleuchtung ermöglicht 3D Beleuchtung in 2D Anwendungen. In dieser Übersicht wird wir führen Sie über die Funktionen zum setup-Komposition Licht, visuelle Elemente, um jedes Licht zu identifizieren und Effekte verwenden, um Materialien für den Inhalt zu definieren.

> [!NOTE]
> Wie [XamlLight](/uwp/api/windows.ui.xaml.media.xamllight) Objekte [CompositionLights](/uwp/api/Windows.UI.Composition.CompositionLight) um XAML-UI-Elemente beleuchtet anwenden, finden Sie unter [XAML-Beleuchtung](xaml-lighting.md).

Kompositionsbeleuchtung können Sie die Benutzeroberfläche interessanter, indem zugelassen wird, erstellen:

- Die Transformation von einem hellen unabhängig von anderen Objekte in der Szene immersive Szenarien wie Musik Wiedergabe Szenen ermöglichen.
- Die Möglichkeit, ein Objekt mit einer koppeln, sodass sie zusammen verschoben unabhängig vom Rest der Szene Szenarien wie Fluent- [Reveal-](/design/style/reveal) Highlight ermöglichen.
- Transformation und die gesamte Szene als eine Gruppe für Materialien und Tiefe zu erzeugen.

Kompositionsbeleuchtung unterstützt drei wichtige Konzepte: **Light**, **Ziele**und **SceneLightingEffect**.

## <a name="light"></a>Licht

[CompositionLight](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlight) ermöglicht Ihnen das Erstellen von verschiedenen Lichter und platzieren Sie sie im Koordinatenbereich. Diese Lichtquellen Ziel visuelle Elemente, die zu identifizieren, wenn vom Licht beleuchtet werden soll.

### <a name="light-types"></a>Lichttypen

| Typ | Beschreibung |
| --- | --- |
| [AmbientLight](/uwp/api/windows.ui.composition.ambientlight) | Von alles in der Szene reflektiert wird eine Lichtquelle, die nichtdirektionale Licht ausgibt, die angezeigt wird. |
| [DistantLight](/uwp/api/windows.ui.composition.distantlight) | Ein unendlich Lichtquelle, die Licht in einer Richtung ausgibt. Wie der Sonne. |
| [PointLight](/uwp/api/windows.ui.composition.pointlight) | Ein Punkt Quelle des Lichts, die Licht in alle Richtungen ausgibt. Wie eine Glühbirne. |
| [SpotLight](/uwp/api/windows.ui.composition.spotlight) | Eine Lichtquelle, die inneren und äußeren Kegel des Lichts ausgibt. Wie eine Taschenlampe. |

## <a name="targets"></a>Ziele

Wenn Licht ein visuelles Ziel (Hinzufügen zur Liste der [Ziele](/uwp/api/windows.ui.composition.compositionlight.targets) ), die visuelle Bearbeitung und alle seine untergeordneten Elemente bekannt und reagieren auf diese Lichtquelle. Dies kann etwa so einfach wie eine Einstellung PointLight Quelle im Stammverzeichnis des eine Struktur und alle visuellen Elemente, die folgenden reagieren auf die Animation der Richtung Licht Punkt sein.

**ExclusionsFromTargets** bietet Ihnen die Möglichkeit, die Beleuchtung eines visuellen Elements oder eine Unterstruktur von visuellen Elementen auf ähnliche Weise wie das Hinzufügen von Ziele zu entfernen. Untergeordnete Elemente in der Struktur von der visuellen, der ausgeschlossen ist daher nicht leuchtet.

### <a name="sample-targets"></a>Beispiel (Ziele)

Im folgenden Beispiel verwenden wir eine CompositionPointLight auf einem XAML-TextBlock.

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

Finden Sie umfassende [Text zu Schimmern](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/TextShimmer) an die Küche WindowUIDevLabs Beispiel, um mehr zu erfahren.

## <a name="restrictions"></a>Einschränkungen

Es gibt mehrere Faktoren beim bestimmen, welche Inhalte durch CompositionLight beleuchtet wird.

Konzept | Details
--- | ---
**Umgebungslicht** | Hinzufügen einer nicht-Umgebungslicht Ihrer Szene wird deaktiviert, wenn alle vorhandenen Licht.  Elemente nicht durch eine nicht-Umgebungslicht Zielgruppe werden schwarz angezeigt.  Um umgebenden visuelle Elemente, die nicht vom Licht auf natürliche Weise als Ziel zu beleuchten, verwenden Sie ein Umgebungslicht in Verbindung mit anderen Lichter.
**Anzahl von Lichtern** | Sie können zwei nicht-ambient Komposition anzeigen in beliebiger Kombination verwenden, auf der Benutzeroberfläche. Umgebungslicht Licht sind nicht eingeschränkt. Volltonfarben, sind Punkt und entfernte Licht.
**Lebensdauer** | CompositionLight treten Prozesslebensdauer-Bedingungen (Beispiel: der Garbage Collector kann das Lichtobjekt wiederverwenden, bevor sie verwendet wird).  Es wird empfohlen, einen Verweis auf die Lichtquellen durch Hinzufügen von Lichtquellen als Mitglied der Anwendung Lebensdauer verwalten zu halten.
**Transformationen** | Licht müssen sich bei einem Knoten über UI platziert werden, die Effekte wie [perspektivische Transformationen](/design/layout/3-d-perspective-effects) in der visuellen Struktur verwendet wird, ordnungsgemäß gezeichnet werden.
**Ziele und Koordinatenraum** | CoordinateSpace ist den Platz in dem alle die Lichter-Eigenschaften festgelegt werden müssen. CompositionLight.Targets muss innerhalb der CoordinateSpace-Struktur.

## <a name="lighting-properties"></a>Beleuchtungseigenschaften

Je nach Art des Lichts verwendet kann ein Licht über Eigenschaften für Dämpfung und Speicherplatz verfügen. Nicht alle Lichtarten verwenden alle Eigenschaften.

Eigenschaft | Beschreibung
--- | ---
**Farbe** | Die [Farbe](/uwp/api/windows.ui.color) des Lichts. Beleuchtung Farbe, die Werte von [D3D](https://docs.microsoft.com/windows/uwp/graphics-concepts/light-properties) "Diffus" Umgebung und Glanzlicht, die die abgestrahlte Farbe definiert definiert sind. Beleuchtung verwendet RGBA-Werte für Licht. die alpha-Farbkomponente wird nicht verwendet.
**Richtung** | Die Richtung des Lichts. Die Richtung, in der das Licht strahlt, ist relativ zu seiner [CoordinateSpace](/uwp/api/windows.ui.composition.distantlight.coordinatespace) Visual angegeben.
**Koordinatenbereich** | Jedes Visual weist eine implizite 3D-Koordinatensystem. X-Richtung ist von links nach rechts. Y-Richtung wird von oben nach unten. Z-Richtung ist ein Punkt außerhalb der Ebene. Die ursprüngliche diese Koordinate ist die linke obere Ecke des visuellen Elements aus, und die Einheit ist Device Independent Pixel (DIP). Eines Lichts Offset in diese Koordinate definiert.
**Inneren und äußeren Kegel** | Spotlights strahlen einen zweitteiligen Lichtkegel ab: einen hellen inneren Kegel und einen äußeren Kegel. Komposition ermöglicht, dass Sie die Kontrolle über inneren und äußeren Kegelwinkel und Farbe.
**Offset** | Offset der Lichtquelle relativ zum Koordinatenraums Visual.

> [!NOTE]
> Wenn mehrere Lichtquellen das gleiche visuelle erreicht, oder wenn Farbwert eines Lichts groß genug, um 1.0 überschritten wird, kann die Farbe des Lichts aufgrund Klammerung von ein Licht Farbkanal ändern.

### <a name="advanced-lighting-properties"></a>Erweiterte Eigenschaften Beleuchtung

Eigenschaft | Beschreibung
--- | ---
**Intensität** | Steuert die Helligkeit des Lichts.
**Dämpfung** | Die Dämpfung steuert, wie die Intensität eines Lichts gegenüber der maximalen Entfernung, angegeben durch die Eigenschaft „Reichweite“, abnimmt.  Konstante, können Quadradic und Linear Dämpfungseigenschaften verwendet werden.

## <a name="getting-started-with-lighting"></a>Erste Schritte mit Beleuchtung

Führen Sie diese allgemeinen Schritte für das Licht hinzufügen:

- Erstellen und speichern Sie die Lichter: Licht erstellen und speichern Sie sie in einem angegebenen Koordinatenraum.
- Objekte, um Licht zu identifizieren: Lichts an entsprechende visuelle Elemente als Ziel.
- [Optional] Definieren, wie einzelne Objekte reagieren auf Lichter: Verwendung SceneLightingEffect mit einer EffectBrush lichtreflektion zum Anzeigen der SpriteVisual anpassen. Standard Reflektion unterstützen die Beleuchtung der untergeordneten Elemente einer Lichtquelle CoordinateSpace.  Ein visuelles Element, das mit einem SceneLightingEffect überschreibt die Standard-Beleuchtung für dieses Visual.

## <a name="scenelightingeffect"></a>SceneLightingEffect

[SceneLightingEffect](/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect) wird verwendet, um die Standard-Beleuchtung angewendet wird, auf den Inhalt des ein [SpriteVisual](/uwp/api/Windows.UI.Composition.SpriteVisual) Ziel eine [CompositionLight](/uwp/api/windows.ui.composition.compositionlight)ändern.

[SceneLightingEffect](/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect) wird häufig für die materielle Erstellung verwendet. Ein SceneLightingEffect ist ein Effekt verwendet, wenn Sie etwas komplexer sein, z. B. reflektierende Eigenschaften eines Bilds aktivieren bzw. eine Illusion von Tiefe mit einer normalen Zuordnung bereitstellen erreichen möchten. Eine SceneLightingEffect bietet die Möglichkeit, die Benutzeroberfläche anpassen, indem Sie mithilfe der Beleuchtungseigenschaften wie und diffuse Beträge. Sie können weitere Beleuchtungseffekte mit dem Rest der Pipeline Effekte ermöglicht einzeln mischen und Verfassen von verschiedenen Beleuchtung Reaktionen durch Ihren Inhalt anpassen.

> [!NOTE]
> Beleuchtung der Szene erzeugt keine Schatten; Es ist ein Effekt, 2D Rendering konzentriert.  Es wird nicht in Betracht gezogen 3D Beleuchtung Szenarien verwendet, die tatsächliche Beleuchtung-Modellen, einschließlich Schatten enthalten.


Eigenschaft | Beschreibung
--- | ---
**Normale Karte** | NormalMaps erstellen Sie einen Effekt einer Textur, in denen ein normaler zeigt in Richtung der Lichtquelle heller und ein normaler zeigt entfernt wird dunkler. Eine NormalMap die gezielte visual Verwendung einer [CompositionSurfaceBrush](/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) Loadedimagesource verwenden, um eine NormalMap Ressource zu laden hinzu.
**Umgebung** | Ambiente-Eigenschaften werden hauptsächlich zum Steuern der allgemeinen Farbe Reflektions verwendet.
**Glanz** | Spiegelnden Reflektion erstellt Lichter auf Objekte gestalten glänzende angezeigt. Sie können die Ebene der spiegelnden Reflektion sowie über die Glanz steuern.  Diese Eigenschaften werden geändert, um Material Effekte wie Shinny Metalle oder glänzende Papier zu erstellen.
**Diffuse** | Diffuse Reflektion Streut Licht in alle Richtungen.
**Reflektion-Modell** | [Reflektion Modell](/uwp/api/windows.ui.composition.effects.scenelightingeffectreflectancemodel) können Sie zwischen [Blinn Phong](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-phong-shader) und physisch basierend Blinn Phong auswählen.  Sie auswählen physisch basierend Blinn Phong können, wenn Sie Glanzlichter zusammengefasst haben möchten.

### <a name="sample-scenelightingeffect"></a>Beispiel (SceneLightingEffect)

Das folgende Beispiel zeigt, wie eine SceneLightingEffect eine normale Karte hinzugefügt wird.

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
