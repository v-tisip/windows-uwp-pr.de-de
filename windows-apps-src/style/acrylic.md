---
author: mijacobs
description: 
title: Acrylmaterial
template: detail.hbs
ms.author: mijacobs
ms.date: 08/9/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: yulikl
design-contact: rybick
dev-contact: jevansa
doc-status: Published
ms.openlocfilehash: 01c8d1bd961a5246a052d1dc7a746257687104e4
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="acrylic-material"></a>Acrylmaterial
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. grundlegend geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Acryl ist eine Art von [Pinsel](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush), der eine teilweise transparente Textur erzeugt. Sie können Acryl auf App-Oberflächen anwenden, um Tiefe hinzuzufügen und eine visuelle Hierarchie herzustellen.  <!-- By allowing user-selected wallpaper or colors to shine through, Acrylic keeps users in touch with the OS personalization they've chosen. -->

> **Wichtige APIs**: [AcrylicBrush-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_Background)


![Acryl im hellen Design](images/Acrylic_DarkTheme_Base.png)

![Acryl im dunklen Design](images/Acrylic_LightTheme_Base.png)

## <a name="acrylic-and-the-fluent-design-system"></a>Acryl und das Fluent Design-System

 Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten. Acryl ist Komponente des Fluent Design-Systems, die physische Struktur (Material) und Tiefe zu Ihrer App hinzugefügt. 

## <a name="when-to-use-acrylic"></a>Wann sollte Acryl verwendet werden?

Wir empfehlen, unterstützende UI-Komponenten, beispielsweise In-App-Navigation oder Steuerelemente, auf einer Acryloberfläche zu platzieren. Dieses Material ist auch hilfreich für vorübergehende UI-Elemente, wie beispielsweise Dialogfelder und Flyouts, da dadurch eine sichtbare Beziehung mit dem Inhalt beibehalten werden kann, der die vorübergehende UI ausgelöst hat. Acryl wurde zur Verwendung als Hintergrundmaterial und in optisch unauffälligen Bereichen entwickelt. Sie sollten Acryl daher nicht in detaillierten Vordergrundelementen anwenden.

Für Oberflächen hinter dem primären App-Inhalt sollten einheitliche, undurchsichtige Hintergründe verwendet werden.

Ziehen Sie es in Erwägung, Acryl auf einen oder mehrere Ränder Ihrer App, einschließlich der Titelleiste des Fensters, zu erweitern, um die visuelle Darstellung zu verbessern. Vermeiden Sie Streifeneffekte durch das Stapeln von Acrylfarben verschiedener Mischungen nebeneinander. Acryl ist ein Tool zum Erzeugen von visueller Harmonie in Ihren Designs, bei inkorrekter Verwendung können sich jedoch visuelle Störungen ergeben.

Berücksichtigen Sie die folgenden Verwendungsmuster, um zu entscheiden, wie sich Acryl am besten in Ihre App integrieren lässt.

### <a name="vertical-acrylic-pane"></a>Vertikaler Acrylbereich

Es wird empfohlen, in Apps mit vertikaler Navigation Acryl auf den sekundären Bereich anzuwenden, der die Navigationselemente enthält.

![App-Muster mit einem einzigen vertikalen Acrylbereich](images/acrylic_app-pattern_vertical.png)

[NavigationView](../controls-and-patterns/navigationview.md) ist ein neues allgemeines Steuerelement zum Hinzufügen von Navigation zu Ihrer App. Der visuelle Entwurf dieses Elements enthält Acryl. Der Bereich von NavigationView zeigt Hintergrund-Acryl, wenn der Bereich parallel mit dem primären Inhalt geöffnet ist, und dieses wird automatisch in In-App-Acryl umgewandelt, wenn der Bereich als Überlagerung geöffnet ist.

Wenn sich NavigationView in Ihrer App nicht verwenden lässt und Sie Acryl selbst hinzufügen möchten, empfehlen wir die Verwendung von relativ transparentem Acryl mit einer Farbton-Deckkraft von 60%.
 - Wenn der Bereich als Überlagerung über anderen Inhalten der App geöffnet wird, sollte dies [60% In-App-Acryl](#acrylic-theme-resources) sein.
 - Wenn der Bereich parallel mit dem Hauptinhalt der App geöffnet wird, sollte dies [60% Hintergrund-Acryl](#acrylic-theme-resources)sein.

### <a name="multiple-acrylic-panes"></a>Mehrere Acrylbereiche

Es wird empfohlen, in Apps mit drei verschiedenen vertikalen Bereichen Acryl zum nicht primären Inhalt hinzufügen.
 - Verwenden Sie für den sekundären Bereich, der sich am nächsten am primären Inhalt befindet, [80% Hintergrund-Acryl](#acrylic-theme-resources).
 - Verwenden Sie für den tertiären Bereich, der vom primären Inhalt weiter entfernt ist, [60% Hintergrund-Acryl](#acrylic-theme-resources).

![App-Muster mit zwei vertikalen Acrylbereichen](images/acrylic_app-pattern_double-vertical.png)

### <a name="horizontal-acrylic-pane"></a>Horizontaler Acrylbereich

Wir empfehlen, für Apps mit horizontaler Navigation, Steuerung oder sonstigen starken horizontalen Elementen am oberen Rand der App [70% Acryl](#acrylic-theme-resources) auf dieses visuelle Element anzuwenden.

![App-Muster mit einem horizontalen Acrylbereich](images/acrylic_app-pattern_horizontal.png)

In Canvas-Apps, bei denen kontinuierlicher, zoomfähiger Inhalt im Mittelpunkt steht, sollte In-App-Acryl in der oberen Leiste verwendet werden, damit Benutzer eine Verbindung mit diesem Inhalt herstellen können. Beispiele für Canvas-Apps sind Karten, Malen und Zeichnen.

Für Apps ohne einen einzigen kontinuierlichen Zeichenbereich empfehlen wir die Verwendung von Hintergrund-Acryl, um Benutzer mit Ihrer gesamten Desktopumgebung zu verbinden.

### <a name="acrylic-in-utility-apps"></a>Acryl in Hilfsprogramm-Apps

Widgets oder einfachen Apps können als Utility-Apps hervorgehoben werden, wenn im App-Fenster durchgehend Acryl verwendet wird. Apps dieser Kategorie werden in der Regel nur kurz vom Benutzer verwendet und nehmen nicht den gesamte PC-Bildschirm ein. Beispiele für solche Apps sind der Rechner und das Info-Center.

![Dienstprogramm-App „Rechner” mit Acryl im gesamten Hintergrund](images/acrylic_app-pattern_full.png)

> [!Note]
> Das Rendern von Acryloberflächen ist GPU-intensiv, wodurch der Energieverbrauch des Geräts erhöht und die Akkulaufzeit verkürzt werden kann. Acryleffekte werden automatisch deaktiviert, wenn Geräte in den Stromsparmodus versetzt werden, und die Benutzer können Acryleffekte für alle Apps wahlweise deaktivieren.


## <a name="acrylic-blend-types"></a>Acrylmischungen
Die auffälligste Eigenschaft von Acryl ist seine Transparenz. Es gibt zwei Acrylmischungen, die beeinflussen, welche Inhalte durch das Material sichtbar sind:
 - **Hintergrund-Acryl** zeigt den Desktophintergrund und andere Fenster, die sich hinter der derzeit aktiven App befinden. Dabei wird Tiefe zwischen den Fenstern der Anwendung hinzugefügt, während die Personalisierungseinstellungen des Benutzers angewendet werden.
 - **In-App-Acryl** fügt Tiefenwirkung innerhalb des App-Frames hinzu, wodurch sowohl Fokus als auch Hierarchie erzeugt werden.

 ![Hintergrund-Acryl](images/BackgroundAcrylic_DarkTheme.png)

 ![In-App-Acryl](images/AppAcrylic_DarkTheme.png)

 Schichten Sie mehrere Acryloberflächen vorsichtig übereinander. Hintergrund-Acryl sollte sich, wie der Name schon sagt, in der Z-Reihenfolge nicht am nächsten am Benutzer befinden. Mehrere Schichten von Hintergrund-Acryl führen tendenziell zu unerwarteten optischen Täuschungen und sollten vermieden werden. Wenn Sie Acryl übereinanderschichten möchten, verwenden Sie dafür In-App-Acryl, und ziehen Sie es in Erwägung, den Farbtonwert des Acryls zu reduzieren, damit die Schichten für den Betrachter optisch besser dargestellt werden.


## <a name="usability-and-adaptability"></a>Benutzerfreundlichkeit und Anpassungsfähigkeit
Acryl passt seine Darstellung automatisch an eine Vielzahl von Geräten und Kontext an.

Im Modus mit hohem Kontrast wird Benutzern anstelle von Acryl weiterhin die vertraute Hintergrundfarbe ihrer Wahl angezeigt. Darüber hinaus werden sowohl das Hintergrund- als auch das In-App-Acryl in den folgenden Fällen als Volltonfarben angezeigt:
 - Bei Deaktivierung der Transparenz in den Personalisierungseinstellungen
 - Bei aktivem Stromsparmodus
 - Bei Ausführen der App auf Low-End-Hardware

Darüber hinaus werden in den folgenden Fällen nur beim Hintergrund-Acryl Transparenz und Textur durch eine Volltonfarbe ersetzt:
 - Bei Deaktivierung eines App-Fensters auf dem Desktop
 - Bei Ausführen der UWP-App auf einem Telefon, der Xbox, HoloLens oder einem Tablet

### <a name="legibility-considerations"></a>Hinweise zur Lesbarkeit
Es muss sichergestellt werden, dass Texte, die in der App dargestellt werden, [das Kontrastverhältnis erfüllen](../accessibility/accessible-text-requirements.md). Wir haben die Acrylzusammensetzung optimiert, damit Texte in Schwarz oder Weiß mit hoher Farbauflösung oder in Mittelgrau auf Acryl die Kontrastverhältnisse erfüllen. Die Standardeinstellungen der von der Plattform bereitgestellten Designressourcen weisen kontrastierende Färbungen mit 80% Deckkraft auf. Beim Platzieren von Textkörper mit hoher Farbauflösung auf Acryl können Sie die Farbton-Deckkraft verringern und die Lesbarkeit gleichzeitig erhalten. Im dunklen Modus kann die Farbton-Deckkraft 70% betragen, während das Acryl im hellen Modus ein Kontrastverhältnis von 50% Deckkraft erfüllt.

Es wird davon abgeraten, farbigen Text auf Ihren Acryloberflächen zu platzieren, da diese Kombinationen bei einem Schriftgrad von 15px wahrscheinlich nicht die Mindestanforderungen an das Kontrastverhältnis erfüllen. Platzieren Sie möglichst keine [Hyperlinks](../controls-and-patterns/hyperlinks.md) über Acrylelementen. Vergessen Sie darüber hinaus nicht die Auswirkungen auf die Lesbarkeit, wenn Sie den Acrylfarbton oder die Deckkraftstufe auf Werte außerhalb der von der Designressource bereitgestellten Plattformstandardeinstellungen einstellen möchten.

## <a name="acrylic-theme-resources"></a>Acryl-Designressourcen
Mit dem neuen XAML AcrylicBrush oder den vordefinierten AcrylicBrush-Designressourcen können Sie Acryl ganz einfach auf die Oberflächen Ihrer App anwenden. Zunächst müssen Sie entscheiden, ob Sie In-App- oder Hintergrund-Acryl verwenden möchten. Prüfen Sie die zuvor in diesem Artikel beschriebenen allgemeinen App-Muster auf Empfehlungen.

Wir haben eine Sammlung von Pinsel-Designressourcen sowohl für Hintergrund- als auch In-App-Acrylarten erstellt, die das Design der App berücksichtigen und nach Bedarf wieder auf Volltonfarben zurückgreifen. Ressourcen mit der Benennung *Acrylic\*WindowBrush* stellen Hintergrund-Acryl dar, während sich *Acrylic\*ElementBrush* auf In-App-Acryl bezieht.

<table>
    <tr>
        <th align="center">Ressourcenschlüssel</th>
        <th align="center">Farbton-Deckkraft</th>
        <th align="center">[Fallbackfarbe](color.md)</th>
    </tr>
    <tr>
        <td> SystemControlAcrylicWindowBrush<br/>SystemControlAcrylicElementBrush </td>
        <td align="center"> 80% </td>
        <td> ChromeMedium </td>
    </tr>
    </tr>
        <td> **Empfohlene Verwendung:** Hierbei handelt es sich um allgemeine Acrylressourcen, die sich in einer Vielzahl von Verwendungsarten gut einsetzen lassen. Wenn Ihre App sekundären Text in der Farbe AltMedium mit einer kleineren Textgröße als 18px verwendet, platzieren Sie eine Acrylressource von 80% hinter dem Text, um die [Anforderungen an das Kontrastverhältnis zu erfüllen](../accessibility/accessible-text-requirements.md). </td>
    </tr>
    <tr>
        <td> SystemControlAcrylicMediumHighWindowBrush<br/>SystemControlAcrylicMediumHighElementBrush </td>
        <td align="center"> 70% </td>
        <td> ChromeMedium </td>
    </tr>
    <tr>
        <td> **Empfohlene Verwendung:** Wenn Ihre App sekundären Text in der Farbe AltMedium mit einer Textgröße von 18px oder mehr verwendet, können Sie diese transparenteren Acrylressourcen von 70% hinter dem Text platzieren. Wir empfehlen die Verwendung dieser Ressourcen in den oberen horizontalen Navigations- und Steuerungsbereichen in Ihrer App.  </td>
    </tr>
    <tr>
        <td> SystemControlAcrylicMediumWindowBrush<br/>SystemControlAcrylicMediumElementBrush </td>
        <td align="center"> 60% </td>
        <td> ChromeMediumLow </td>
    </tr>
    <tr>
        <td> **Empfohlene Verwendung:** Wenn nur primärer Text der Farbe AltHigh über Acryl platziert wird, kann Ihre App diese Ressourcen von 60% verwenden. Es wird empfohlen, den [vertikalen Navigationsbereich](../controls-and-patterns/navigationview.md) Ihrer App, d.h. das Hamburger-Menü, mit 60% Acryl zu zeichnen. </td>
    </tr>
</table>

Zusätzlich zu farbneutralem Acryl haben wir Ressourcen hinzugefügt, mit denen sich das Acryl mithilfe von benutzerdefinierten Akzentfarben färben lässt. Wir empfehlen, farbiges Acryl sparsam zu verwenden. Platzieren Sie für die bereitgestellten Varianten dark1 und dark2 weißen bzw. hellfarbigen Text der Textfarbe des dunklen Designs entsprechend über diesen Ressourcen.
<table>
    <tr>
        <th align="center">Ressourcenschlüssel</th>
        <th align="center">Farbton-Deckkraft</th>
        <th align="center">[Farbton und Fallbackfarben](color.md)</th>
    </tr>
    <tr>
        <td> SystemControlAcrylicAccentMediumHighWindowBrush<br/>SystemControlAcrylicAccentMediumHighElementBrush </td>
        <td align="center"> 70% </td>
        <td> SystemAccentColor </td>
    </tr>
    <tr>
        <td> SystemControlAcrylicAccentDark1WindowBrush<br/>SystemControlAcrylicAccentDark1ElementBrush </td>
        <td align="center"> 80% </td>
        <td> SystemAccentColorDark1 </td>
    </tr>
    <tr>
        <td> SystemControlAcrylicAccentDark2MediumHighWindowBrush<br/>SystemControlAcrylicAccentDark2MediumHighElementBrush </td>
        <td align="center"> 70% </td>
        <td> SystemAccentColorDark2 </td>
    </tr>
</table>


Um eine bestimmte Oberfläche zu zeichnen, wenden Sie eines der oben genannten Designressourcen auf Elementhintergründe an. Verfahren Sie dabei genauso, wie Sie die anderen Pinselressourcen anwenden würden.

```xaml
<Grid Background="{ThemeResource SystemControlAcrylicElementBrush}">
```

## <a name="custom-acrylic-brush"></a>Benutzerdefinierter Acrylpinsel
Sie können einen Farbton zum Acryl Ihrer App hinzufügen, um das Branding anzuzeigen oder ein optisches Gleichgewicht mit anderen Elementen auf dieser Seite zu erzeugen. Um Farbe und keine Graustufen anzuzeigen, müssen Sie Ihre eigenen Acrylpinsel mithilfe der folgenden Eigenschaften definieren:
 - **TintColor**: die Überlagerungsschicht der Farbe/des Farbtons. Sie sollten sowohl den RGB-Farbwert als auch die Deckkraft des Alphakanals angeben.
 - **TintOpacity**: die Deckkraft der Farbtonschicht. Wir empfehlen 80% Deckkraft als Ausgangspunkt, obwohl verschiedene Farben bei anderer Transparenz möglicherweise ansprechender aussehen.
 - **BackgroundSource**: die Kennzeichnung zum Festlegen, ob Sie Hintergrund- oder In-App Acryl verwenden möchten.
 - **FallbackColor**: die Volltonfarbe, die Acryl bei schwacher Akkuladung ersetzt. Im Fall von Hintergrund-Acryl ersetzt die Fallbackfarbe das Acryl auch, wenn Ihre App nicht im aktiven Desktopfenster angezeigt wird oder wenn die App auf dem Telefon oder der Xbox ausgeführt wird.


![Acrylmuster für das helle Design](images/CustomAcrylic_Swatches_LightTheme.png)

![Acrylmuster für das dunkle Design](images/CustomAcrylic_Swatches_DarkTheme.png)

Um einen Acrylpinsel hinzuzufügen, definieren Sie die Ressourcen für das dunkle und das helle Design und für das Design mit hohem Kontrast. Beachten Sie, dass wir bei hohem Kontrast die Verwendung eines SolidColorBrush mit demselben X:Key wie für den dunklen/hellen AcrylicBrush zu verwenden.

```xaml
<ResourceDictionary.ThemeDictionaries>
    <ResourceDictionary x:Key="Default">
        <AcrylicBrush x:Key="MyAcrylicBrush"
            BackgroundSource="HostBackdrop"
            TintColor="#FFFF0000"
            TintOpacity="0.8"
            FallbackColor="#FF7F0000"/>
    </ResourceDictionary>

    <ResourceDictionary x:Key="HighContrast">
        <SolidColorBrush x:Key="MyAcrylicBrush"
            Color="{ThemeResource SystemColorWindowColor}"/>
    </ResourceDictionary>

    <ResourceDictionary x:Key="Light">
        <AcrylicBrush x:Key="MyAcrylicBrush"
            BackgroundSource="HostBackdrop"
            TintColor="#FFFF0000"
            TintOpacity="0.8"
            FallbackColor="#FFFF7F7F"/>
    </ResourceDictionary>
</ResourceDictionary.ThemeDictionaries>
```

Das folgende Beispiel zeigt, wie Sie AcrylicBrush in Code angeben. Wenn Ihre App mehrere Betriebssystemziele unterstützt, müssen Sie sicherstellen, dass diese API auf dem Gerät des Benutzers verfügbar ist.

```csharp
if (Windows.Foundation.Metadata.ApiInformation.IsTypePresent("Windows.UI.Xaml.Media.XamlCompositionBrushBase"))
{
    Windows.UI.Xaml.Media.AcrylicBrush myBrush = new Windows.UI.Xaml.Media.AcrylicBrush();
    myBrush.BackgroundSource = Windows.UI.Xaml.Media.AcrylicBackgroundSource.HostBackdrop;
    myBrush.TintColor = Color.FromArgb(255, 202, 24, 37);
    myBrush.FallbackColor = Color.FromArgb(255, 202, 24, 37);
    myBrush.TintOpacity = 0.6;

    grid.Fill = myBrush;
}
else
{
    SolidColorBrush myBrush = new SolidColorBrush(Color.FromArgb(255, 202, 24, 37));

    grid.Fill = myBrush;
}
```

## <a name="extending-acrylic-into-your-title-bar"></a>Ausdehnen von Acryl auf die Titelleiste

Für eine nahtlose, fließende Darstellung im Fenster Ihrer App wird empfohlen, Acryl im Titelleistenbereich der App zu platzieren. Fügen Sie dazu den folgenden Code in der Datei App.xaml.cs hinzu.

```csharp
CoreApplication.GetCurrentView().TitleBar.ExtendViewIntoTitleBar = true;
ApplicationViewTitleBar titleBar = ApplicationView.GetForCurrentView().TitleBar;
titleBar.ButtonBackgroundColor = Colors.Transparent;
titleBar.ButtonInactiveBackgroundColor = Colors.Transparent;
```

Darüber hinaus müssen Sie den Titel der App, der normalerweise automatisch in der Titelleiste angezeigt wird, mit einem TextBlock ziehen, der `CaptionTextBlockStyle` verwendet.

## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen
* Verwenden Sie Acryl als Hintergrundmaterial von nicht primären App-Oberflächen wie Navigationsbereichen.
* Dehnen Sie das Acryl auf mindestens einen Rand der App aus, um durch eine dezente Vermischung mit der Umgebung der App eine nahtlose Oberfläche bereitzustellen.
* Platzieren Sie In-App- und Hintergrund-Acryl nicht direkt nebeneinander, um visuelle Spannung an den Rändern zu vermeiden.
* Platzieren Sie nicht mehrere Acrylbereiche mit demselben Farbton und derselben Deckkraft nebeneinander, da dies eine unerwünschte sichtbare Naht erzeugt.
* Platzieren Sie keinen farbigen Text über Acryloberflächen.

## <a name="how-we-designed-acrylic"></a>Unser Acryl-Entwurfsansatz

Wir haben die Hauptkomponenten des Acryls optimiert, um eine individuelle Darstellung und einzigartige Eigenschaften zu erhalten. Wir begannen damit, flachen Oberflächen mithilfe von Transparenz, Weichzeichnungs- und Störungsfiltern visuelle Tiefe und Dimension hinzuzufügen. Dann fügten wir eine Ausschluss-Mischmodus-Ebene hinzu, um den Kontrast und die Lesbarkeit der auf dem Acrylhintergrund platzierten UI sicherzustellen. Zuletzt fügten wir Farbtöne hinzu, um Personalisierungen zu ermöglichen. Zusammen ergeben diese Ebenen ein neues, einsatzbereites Material.

![Acrylzusammensetzung](images/AcrylicRecipe_Diagram.png)
<br/>Das Acryl setzt sich folgendermaßen zusammen: Hintergrund, Weichzeichnungsfilter, Ausschluss-Mischung, Überlagerung der Farbe/des Farbtons, Störungsfilter

<!--
<div class="microsoft-internal-note">
When designing your app, please utilize these [design resources](http://uni/DesignDepot.FrontEnd/#/Search?t=Resources%7CNeon%7CToolkit&f=Acrylic%20Material) to show acrylic in comps. The linked templates are the most accurate way to represent acrylic material in Photoshop and Illustrator. The ordering, as noted in the recipe diagram above, should start from the top: <br/>
 - Noise asset (tiled) at 4% opacity <br/>
 - Base color/tint/alpha layer <br/>
 - Exclusion blend (white @ 10% opacity) <br/>
 - Gaussian blur (30px radius) <br/>
</div>
-->


## <a name="related-articles"></a>Verwandte Artikel
[**Einblendungen**](reveal.md)
