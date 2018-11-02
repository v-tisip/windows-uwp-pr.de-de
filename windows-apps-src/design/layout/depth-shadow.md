---
author: serenaz
description: Z-Tiefe oder relativ Tiefe und Schatten gibt zwei Möglichkeiten, Tiefe in Ihre app an Benutzer beim Fokus natürlichen und effizienten unterstützen integrieren.
title: Z-Tiefe und Schatten für UWP-apps
template: detail.hbs
ms.author: sezhen
ms.date: 02/12/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: chigy
design-contact: balrayit
ms.localizationpriority: medium
ms.openlocfilehash: 3a87e7366765b7c8b304e930fed0d3c45900aad9
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5971230"
---
# <a name="z-depth-and-shadow"></a>Z-Tiefe und Schatten

!["true" Tiefe](images/elevation-shadow/depth.svg)

Das Fluent Tiefe System verwendet physischen Konzepte wie 3D Positionierung, Light, und Schatten digitaler Benutzeroberfläche neu zu erfinden kann in einer mehr geschichteten, physikalischen Umgebung wahrgenommen werden. Z-Tiefe oder relativ Tiefe und Schatten gibt zwei Möglichkeiten, Tiefe in Ihre UWP-app integrieren.

## <a name="what-is-z-depth"></a>Was ist die Z-Tiefe?

Z-Tiefe beträgt der Abstand zwischen zwei Flächen entlang der z-Achse, und es wird veranschaulicht, wie nah ein Objekt für den Betrachter ist.

![Z-Tiefe](images/elevation-shadow/elevation.svg)

### <a name="why-use-z-depth"></a>Gründe für die Verwendung von Z-Tiefe

In der realen Welt neigen wir auf Objekte zu konzentrieren, die näher an uns sind. Wir können diese räumliche instinktiv digitale UI auch anwenden. Z. B. Wenn Sie ein Element, das näher an dem Benutzer bringen, wird der Benutzer instinktiv für das Element konzentrieren. Durch Verschieben UI-Elemente näher in z-Achse können Sie visuelle Hierarchie zwischen Objekten, damit der Benutzer den natürlichen und effizienten in Ihrer app Aufgaben erstellen. 

![Z-Tiefe im Menü "Inhalt"](images/elevation-shadow/whyelevation.svg)

Bereitstellen des aussagekräftige visuelle Hierarchie Z-Tiefe auch, Funktionen Sie erstellen zusätzlich zu diesen Fluss nahtlos 2D, 3D Umgebungen, Skalieren von Ihrer app für alle Geräte und Formfaktoren. 

![Z-Tiefe in 2d, 3d](images/elevation-shadow/elevation-2d3d.svg)

### <a name="how-is-z-depth-perceived"></a>Wie wird die Z-Tiefe empfunden?

Basierend auf wie wir Tiefe in der realen Welt wahrnehmen, folgen Sie verschiedene Techniken, die verwendet werden können, um Näherung in digitale Benutzeroberfläche anzuzeigen.

- **Skalierung** Weiter Objekte werden kleiner als näher Objekte mit der gleichen Größe angezeigt. Diese Methode wird ist schwierig, veranschaulichen effektiv im 2D-Raum, sodass es im Allgemeinen nicht empfohlen wird. Allerdings können Sie zum Erstellen einer effektiven Simulations Objekte näher an den Benutzer in 2D Maßstab und [Schatten](#what-is-shadow) .

    ![Näherung mit Skalierung](images/elevation-shadow/elevation-scale.svg)

- **Atmosphäre** Objekte können welches weiter entfernt und mit einer "verrauchte" Überlagerung oder andere der Effekt unscharf erscheinen.

    ![Näherung mit Atmosphäre](images/elevation-shadow/elevation-atmosphere.svg)

- **Bewegung** Relative Geschwindigkeit kann verwendet werden, um die Näherung veranschaulichen: näher Objekte verschieben schneller als entfernte Hintergrundobjekte. Weitere Informationen zum Implementieren dieser Effekt, finden Sie unter [Parallax](../motion/parallax.md).

    ![Näherung mit Bewegung](images/elevation-shadow/elevation-motion.svg)

### <a name="recommendations-for-z-depth"></a>Empfehlungen für die Z-Tiefe

Reduzieren Sie die Anzahl der mit erhöhten Rechten Ebenen klare visuelle Fokus bereitstellen. Zwei Ebenen, die in den meisten Fällen ist ausreichend: eine für Vordergrund-Elemente (hohe Näherung) und ein weiteres für Hintergrundelemente (niedrig Näherung). Wenn Sie mehrere mit erhöhten Rechten Elemente, die sich nicht überlappen verfügen, Gruppieren der gleichen Ebene (d. h. Vordergrund), um die Anzahl der Ebenen reduzieren.

![Z-Tiefe innerhalb einer app](images/elevation-shadow/app-depth.svg)

## <a name="what-is-shadow"></a>Was ist Schatten?

![shadow](images/elevation-shadow/shadow.svg)

Schatten ist eine Möglichkeit, erhöhte Rechte wahrnehmen. Wenn Licht über ein mit erhöhten Rechten Objekt vorhanden ist, gibt es ein Schatten auf der Oberfläche unten. Je höher das Objekt, die größere und weicher wird der Schatten. Beachten Sie, dass mit erhöhten Rechten Objekte benötigen nicht Schatten Schatten bedeuten erhöhte Rechte.

In UWP-apps sollte gut gestaltete, nicht mutige Schatten sein. Wenn Schatten aus den Fokus und Produktivität beeinträchtigen, klicken Sie dann beschränken Sie die Verwendung von Schatten.

Sie können Schatten mit dem ThemeShadow oder DropShadow APIs verwenden.

## <a name="themeshadow"></a>ThemeShadow

Die ThemeShadow, die für alle XAML-Element zum Zeichnen Typ angewendet werden kann Schatten entsprechend basierend auf X, y, Z-Koordinaten. ThemeShadow passt sich automatisch auch für andere Umgebung Spezifikationen:

- Änderungen der Beleuchtung, Benutzer Design, app-Umgebung und Shell anpasst.
- Schatten Elemente automatisch basierend auf ihren erhöhte Rechte.
- Behält Elemente synchronisieren beim Bewegen und erhöhte Rechte zu ändern.
- Behält Schatten konsistent im gesamten und Anwendungen.

Hier sind Beispiele für ThemeShadow bei verschiedenen rechteerweiterungen mit der helle und dunkle Designs:

![Intelligente Schatten mit hellem Design](images/elevation-shadow/smartshadow-light.svg)

![Intelligente Schatten mit dunklem Design](images/elevation-shadow/smartshadow-dark.svg)

### <a name="themeshadow-in-common-controls"></a>ThemeShadow Steuerelemente gemeinsam

Die folgenden allgemeinen Steuerelemente verwenden automatisch ThemeShadow, Schatten werfen:

- [Dialogfelder und Flyouts](../controls-and-patterns/dialogs.md)
- [NavigationView](../controls-and-patterns/navigationview.md)
- [Medientransport-Steuerelement](../controls-and-patterns/media-playback.md)
- [Kontextmenü](../controls-and-patterns/menus.md)
- [Befehlsleiste](../controls-and-patterns/app-bars.md)
- [AutoVorschlagen](../controls-and-patterns/auto-suggest-box.md), [ComboBox](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [Kalender/Datum/Uhrzeit Ordnerauswahl](../controls-and-patterns/date-and-time.md) [QuickInfo](../controls-and-patterns/tooltips.md)
- [Zugriffstasten](../input/access-keys.md)

### <a name="themeshadow-in-popups"></a>ThemeShadow Popups

ThemeShadow wandelt automatisch Schatten, wenn für alle XAML-Element in einem [Popup](/uwp/api/windows.ui.xaml.controls.primitives.popup)angewendet. Es wird auf den Inhalt des app-Hintergrund hinter es und alle anderen geöffneten Popups darunter Schatten umwandeln.

Um ThemeShadow mit Popups zu verwenden, verwenden Sie die `Shadow` -Eigenschaft verwenden, um eine ThemeShadow auf ein XAML-Element angewendet. Anschließend Erhöhen des Elements von anderen Elementen dahinter, z. B. die Z-Komponente von der `Translation` Eigenschaft.
Für die meisten Popup-UI ist die empfohlene erhöhte Rechte relativ zu den Inhalt des app-Hintergrund 32 effektiven Pixeln.

Dieses Beispiel zeigt ein Rechteck in einem Popup scheinbar einen Schatten auf den Inhalt des app-Hintergrund und alle anderen Popups dahinter:

```xaml
<Popup>
    <Rectangle x:Name="PopupRectangle" Fill="White" Height="48" Width="96">
        <Rectangle.Shadow>
            <ThemeShadow />
        </Rectangle.Shadow>
    </Rectangle>
</Popup>
```

```csharp
// Elevate the rectangle by 32px
PopupRectangle.Translation += new Vector3(0, 0, 32);
```

![Schatten Codebeispiels](images/elevation-shadow/smartshadow-example.svg)

### <a name="themeshadow-in-other-elements"></a>ThemeShadow in anderen Elementen

Um einen Schatten aus einem XAML-Element umgewandelt, die nicht in einem Popup ist, müssen Sie explizit angeben die anderen Elemente, die den Schatten im empfangen können die `ThemeShadow.Receivers` Auflistung.

Dieses Beispiel zeigt zwei Schaltflächen, die auf einem Raster hinter sie Schatten werfen:

```xaml
<Grid x:Name="BackgroundGrid" Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.Resources>
        <ThemeShadow x:Name="SharedShadow" />
    </Grid.Resources>

    <Button x:Name="Button1" Content="Button 1" Shadow="{StaticResource SharedShadow}" Margin="10" />

    <Button x:Name="Button2" Content="Button 2" Shadow="{StaticResource SharedShadow}" Margin="120" />
</Grid>
```

```csharp
/// Add BackgroundGrid as a shadow receiver and elevate the casting buttons above it
SharedShadow.Receivers.Add(BackgroundGrid);

Button1.Translation += new Vector3(0, 0, 16);
Button2.Translation += new Vector3(0, 0, 32);
```

### <a name="performance-best-practices-for-themeshadow"></a>Bewährte Methoden für ThemeShadow Leistung

1. Die Anzahl der benutzerdefinierten Empfänger Elemente auf das minimum zu beschränken. 

2. Wenn mehrere Empfänger Elemente auf der gleichen erhöhte Rechte sind dann versuchen Sie, diese kombinieren, indem Sie ein einzelnes übergeordnetes Element stattdessen abzielen.

3. Wenn mehrere Elemente die gleiche Art von Schatten auf die gleichen Empfänger Elemente umwandelt fügen Sie des Schattens als freigegebene Ressource und wiederzuverwenden.

## <a name="drop-shadow"></a>Schlagschatten

DropShadow reagiert nicht automatisch auf seiner Umgebung und keine Lichtquellen. Sehen Sie beispielsweise Implementierungen, die [DropShadow-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.composition.dropshadow).

## <a name="which-shadow-should-i-use"></a>Welche Schatten sollte ich verwenden?

| Eigenschaft | ThemeShadow | DropShadow |
| - | - | - | - |
| **Min SDK** | RS5 | 14393 |
| **Anpassungsfähigkeit** | Ja | Nein |
| **Anpassung** | Nein | Ja |
| **Lichtquelle** | Automatische (globale standardmäßig können aber überschreiben pro app) | Keine |
| **In 3D Umgebungen unterstützt** | Ja | Nein |

- Im Allgemeinen empfehlen wir die Verwendung von ThemeShadow, die automatisch an seiner Umgebung anpasst.
- Wenn Sie Szenarien für benutzerdefinierte Schatten erweiterte haben, verwenden Sie DropShadow, die für eine umfassendere Anpassung ermöglicht.
- Für die Rückwärtsnavigation Kompatibilität zu gewährleisten, DropShadow verwenden.
- Bedenken hinsichtlich der Leistung die Anzahl der Schatten oder DropShadow verwenden.
- Verwenden Sie auf HMDs in "true" 3D ThemeShadow. Da DropShadow an einem angegebenen Offset aus dem visuellen zeichnet, die sie von der Seite, übergeordnet ist, sucht es wie er im Raum verankert ist. Andererseits, ist ThemeShadow auf die visuellen Elemente als Empfänger definiert gerendert.
