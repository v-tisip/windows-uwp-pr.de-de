---
author: mijacobs
description: Eine Art von Pinsel, der eine durchsichtige Textur erzeugt.
title: Acryl-Material
template: detail.hbs
ms.author: mijacobs
ms.date: 08/9/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: yulikl
design-contact: rybick
dev-contact: jevansa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: c116a6131889e1d87642165f4e1d9883d78add33
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7288651"
---
# <a name="acrylic-material"></a>Acryl-Material

![Favoritenbild](images/header-acrylic.svg)

Acryl ist eine Art von [Pinsel](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush) , der eine durchsichtige Textur erzeugt. Sie können Acryl auf App-Oberflächen anwenden, um Tiefe hinzuzufügen und eine visuelle Hierarchie herzustellen.  <!-- By allowing user-selected wallpaper or colors to shine through, acrylic keeps users in touch with the OS personalization they've chosen. -->

> **Wichtige APIs**: [AcrylicBrush-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.Background)

:::row:::
    :::column:::
        Acrylic in light theme
        ![Acrylic in light theme](images/Acrylic_LightTheme_Base.png)
    :::column-end:::
    :::column:::
        Acrylic in dark theme
        ![Acrylic in dark theme](images/Acrylic_DarkTheme_Base.png)
    :::column-end:::
:::row-end:::

## <a name="acrylic-and-the-fluent-design-system"></a>Acryl und das Fluent Design-System

 Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten. Acryl ist Komponente des Fluent Design-Systems, die physische Struktur (Material) und Tiefe zu Ihrer App hinzugefügt. Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).

 ## <a name="video-summary"></a>Video-Zusammenfassung

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev002/player]

## <a name="examples"></a>Beispiele

:::row:::
    :::column span:::
        ![Some image](images/XAML-controls-gallery-app-icon.png)
    :::column-end:::
    :::column span="2":::
        **XAML Controls Gallery**<br>
        If you have the XAML Controls Gallery app installed, click <a href="xamlcontrolsgallery:/item/Acrylic">here</a> to open the app and see acrylic in action.

        <a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a><br>
        <a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a>
    :::column-end:::
:::row-end:::

## <a name="acrylic-blend-types"></a>Acrylmischungen
Die auffälligste Eigenschaft von Acryl ist seine Transparenz. Es gibt zwei Acrylmischungen, die beeinflussen, welche Inhalte durch das Material sichtbar sind:
 - **Hintergrund-Acryl** zeigt den Desktophintergrund und andere Fenster, die sich hinter der derzeit aktiven App befinden. Dabei wird Tiefe zwischen den Fenstern der Anwendung hinzugefügt, während die Personalisierungseinstellungen des Benutzers angewendet werden.
 - **In-App-Acryl** fügt Tiefenwirkung innerhalb des App-Frames hinzu, wodurch sowohl Fokus als auch Hierarchie erzeugt werden.

 ![Hintergrund-Acryl](images/BackgroundAcrylic_DarkTheme.png)

 ![In-App-Acryl](images/AppAcrylic_DarkTheme.png)

 Schichten Sie mehrere acryloberflächen vorsichtig: mehrere Schichten von Hintergrund-Acryl ablenkende optischen täuschungen erstellen können.

## <a name="when-to-use-acrylic"></a>Wann sollte Acryl verwendet werden?

* Verwenden Sie in-app-Acryl, für die Unterstützung von UI, z. B. NavigationView oder Inline-Steuerelemente. 
* Verwenden Sie Hintergrund-Acryl, vorübergehende UI-Elemente, z. B. Kontextmenüs, Flyouts und Licht-Dimsissable-Benutzeroberfläche.<br />Verwendung von Acryl in vorübergehende Szenarien, trägt dazu bei, eine visuelle Beziehung mit dem Inhalt beizubehalten, die die vorübergehende Benutzeroberfläche ausgelöst hat.

Wenn Sie in-app-Acryl auf Flächen Navigation verwenden, sollten Sie Inhalt unterhalb der acrylbereich zur Verbesserung des Fluss in Ihrer app zu erweitern. Mithilfe von NavigationView ist für Sie automatisch der Fall. Vermeiden Sie streifeneffekte, versuchen Sie nicht in mehrere Teile von Acryl Edge-to-Edge - platzieren kann dies jedoch eine unerwünschte Naht zwischen den beiden verschwommen Flächen erstellen. Acryl kann ist ein Tool zum Erzeugen von visuellen Harmonie in Ihren Designs, jedoch bei inkorrekter Verwendung visuelle Störungen ergeben.

Berücksichtigen Sie die folgenden Verwendungsmuster zu entscheiden, wie Acryl in Ihrer app zu integrieren:

### <a name="horizontal-navigation-or-commanding"></a>Horizontale Navigation oder Befehle

Wenn Ihre app nicht NavigationView nutzen kann, und Sie Acryl selbst hinzufügen möchten, empfehlen wir die Verwendung von relativ durchsichtige Acryl mit 60 % Farbton-Deckkraft.
 - Wenn der Bereich als Überlagerung über anderen Inhalten der App geöffnet wird, sollte dies [60% In-App-Acryl](#acrylic-theme-resources) sein.

![Karten-app mit in-app horizontalen Befehle](images/Maps_In_App_Acrylic_1.png)

Darüber hinaus erhält müssen Ihre Inhalte erweitern oder Bildlauf unter der Acryl am Anfang Ihrer app ein immersiven und nahtlos Erlebnis.

### <a name="vertical-panes"></a>Vertikalen Bereichen

Für vertikalen Bereichen oder Oberflächen, die im Abschnitt Inhalt Ihrer App zu helfen, empfehlen wir, dass Sie einen nicht transparenten Hintergrund anstelle von Acryl verwenden. Wenn Ihre vertikalen Bereichen basieren auf Inhalte öffnen, mit Vorschlägen wie im NavigationView **Compact** oder **minimierten** Modus, wir, dass Sie in-app-Acryl verwenden, um die Seite Kontext zu behalten, wenn der Benutzer in diesem Bereich zu öffnen.

### <a name="transient-surfaces"></a>Vorübergehende Oberflächen

Für apps mit Menü nicht Modal Popups, Flyouts oder Licht-schließen Bereiche, es wird empfohlen, Hintergrund-Acryl zu verwenden.

![Mail-app-Muster mit einem Informationszwecken flyout](images/Mail_TransientContextMenu.png)

Viele der unsere Steuerelemente werden Acryl in der Standardeinstellung verwenden. [MenuFlyouts](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/menus), [AutoSuggestBox](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/auto-suggest-box), [ComboBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.combobox) und ähnlichen Steuerelemente mit Licht Dimiss Popups werden alle die vorübergehende Acryl verwenden, wenn sie aufgerufen werden.

> [!Note]
> Das Rendern von acryloberflächen ist GPU-intensiv, die Stromverbrauch des Geräts erhöht und Akkulaufzeit verkürzt werden kann. Acryleffekte werden automatisch deaktiviert, wenn Geräte Stromsparmodus versetzt, und Benutzer können acryleffekte für alle apps, deaktivieren, wenn der Benutzer.

## <a name="usability-and-adaptability"></a>Benutzerfreundlichkeit und Anpassungsfähigkeit
Acryl passt seine Darstellung automatisch an eine Vielzahl von Geräten und Kontext an.

Im Modus mit hohem Kontrast wird Benutzern anstelle von Acryl weiterhin die vertraute Hintergrundfarbe ihrer Wahl angezeigt. Darüber hinaus werden sowohl Hintergrund-als auch in-app-Acryl als Volltonfarben angezeigt:
 - Wenn der Benutzer deaktiviert die Transparenz in den Einstellungen > Personalisierung > Farben
 - Wenn der Stromsparmodus aktiviert ist
 - Bei Ausführen der App auf Low-End-Hardware

Darüber hinaus wird nur beim Hintergrund-Acryl seine Transparenz und Textur mit einer Volltonfarbe ersetzt:
 - Bei Deaktivierung eines App-Fensters auf dem Desktop
 - Bei Ausführen der UWP-App auf einem Telefon, der Xbox, HoloLens oder einem Tablet

### <a name="legibility-considerations"></a>Hinweise zur Lesbarkeit
Es muss sichergestellt werden, dass Texte, die in der App dargestellt werden, [das Kontrastverhältnis erfüllen](../accessibility/accessible-text-requirements.md). Wir haben die Acrylzusammensetzung optimiert, damit Texte in Schwarz oder Weiß mit hoher Farbauflösung oder in Mittelgrau auf Acryl die Kontrastverhältnisse erfüllen. Die Standardeinstellungen der von der Plattform bereitgestellten Designressourcen weisen kontrastierende Färbungen mit 80% Deckkraft auf. Beim Platzieren von Textkörper mit hoher Farbauflösung auf Acryl können Sie die Farbton-Deckkraft verringern und die Lesbarkeit gleichzeitig erhalten. Im dunklen Modus kann die Farbton-Deckkraft 70% betragen, während das Acryl im hellen Modus ein Kontrastverhältnis von 50% Deckkraft erfüllt.

Es wird davon abgeraten, farbigen Text auf Ihren Acryloberflächen zu platzieren, da diese Kombinationen bei einem Schriftgrad von 15px wahrscheinlich nicht die Mindestanforderungen an das Kontrastverhältnis erfüllen. Platzieren Sie möglichst keine [Hyperlinks](../controls-and-patterns/hyperlinks.md) über Acrylelementen. Vergessen Sie darüber hinaus nicht die Auswirkungen auf die Lesbarkeit, wenn Sie den Acrylfarbton oder die Deckkraftstufe auf Werte außerhalb der von der Designressource bereitgestellten Plattformstandardeinstellungen einstellen möchten.

## <a name="acrylic-theme-resources"></a>Acryl-Designressourcen
Mit dem neuen XAML AcrylicBrush oder den vordefinierten AcrylicBrush-Designressourcen können Sie Acryl ganz einfach auf die Oberflächen Ihrer App anwenden. Zunächst müssen Sie entscheiden, ob Sie In-App- oder Hintergrund-Acryl verwenden möchten. Prüfen Sie die zuvor in diesem Artikel beschriebenen allgemeinen App-Muster auf Empfehlungen.

Wir haben eine Sammlung von Pinsel-Designressourcen sowohl für Hintergrund- als auch In-App-Acrylarten erstellt, die das Design der App berücksichtigen und nach Bedarf wieder auf Volltonfarben zurückgreifen. Ressourcen mit der Benennung *AcrylicWindow* stellen Hintergrund-Acryl dar, während sich *AcrylicElement* auf In-App-Acryl bezieht.

<table>
    <tr>
        <th align="center">Ressourcenschlüssel</th>
        <th align="center">Farbton-Deckkraft</th>
        <th align="center"><a href="color.md">Fallbackfarbe</a> </th>
    </tr>
    <tr>
        <td> SystemControlAcrylicWindowBrush, SystemControlAcrylicElementBrush <br/> SystemControlChromeLowAcrylicWindowBrush, SystemControlChromeLowAcrylicElementBrush <br/> SystemControlBaseHighAcrylicWindowBrush, SystemControlBaseHighAcrylicElementBrush <br/> SystemControlBaseLowAcrylicWindowBrush, SystemControlBaseLowAcrylicElementBrush <br/> SystemControlAltHighAcrylicWindowBrush, SystemControlAltHighAcrylicElementBrush <br/> SystemControlAltLowAcrylicWindowBrush, SystemControlAltLowAcrylicElementBrush </td>
        <td align="center"> 80% </td>
        <td> ChromeMedium <br/> ChromeLow <br/><br/> BaseHigh <br/><br/> BaseLow <br/><br/> AltHigh <br/><br/> AltLow </td>
    </tr>
    </tr>
        <td> <b>Empfohlene Verwendung:</b> Hierbei handelt es sich um allgemeine Acrylressourcen, die sich in einer Vielzahl von Verwendungsarten gut einsetzen lassen. Wenn Ihre App sekundären Text in der Farbe AltMedium mit einer kleineren Textgröße als 18px verwendet, platzieren Sie eine Acrylressource von 80% hinter dem Text, um die <a href="../accessibility/accessible-text-requirements.md">Anforderungen an das Kontrastverhältnis zu erfüllen</a>. </td>
    </tr>
    <tr>
        <td> SystemControlAcrylicWindowMediumHighBrush, SystemControlAcrylicElementMediumHighBrush <br/> SystemControlBaseHighAcrylicWindowMediumHighBrush, SystemControlBaseHighAcrylicElementMediumHighBrush </td>
        <td align="center"> 70% </td>
        <td> ChromeMedium <br/><br/> BaseHigh </td>
    </tr>
    <tr>
        <td> <b>Empfohlene Verwendung:</b> Wenn Ihre app sekundären Text in der Farbe AltMedium mit einer Textgröße von 18px oder mehr verwendet, können Sie diese mehr durchsichtigen acrylressourcen 70 % hinter dem Text platzieren. Wir empfehlen die Verwendung dieser Ressourcen in den oberen horizontalen Navigations- und Steuerungsbereichen in Ihrer App.  </td>
    </tr>
    <tr>
        <td> SystemControlChromeHighAcrylicWindowMediumBrush, SystemControlChromeHighAcrylicElementMediumBrush <br/> SystemControlChromeMediumAcrylicWindowMediumBrush, SystemControlChromeMediumAcrylicElementMediumBrush <br/> SystemControlChromeMediumLowAcrylicWindowMediumBrush, SystemControlChromeMediumLowAcrylicElementMediumBrush <br/> SystemControlBaseHighAcrylicWindowMediumBrush, SystemControlBaseHighAcrylicElementMediumBrush <br/> SystemControlBaseMediumLowAcrylicWindowMediumBrush, SystemControlBaseMediumLowAcrylicElementMediumBrush <br/> SystemControlAltMediumLowAcrylicWindowMediumBrush, SystemControlAltMediumLowAcrylicElementMediumBrush  </td>
        <td align="center"> 60% </td>
        <td> ChromeHigh <br/><br/> ChromeMedium <br/><br/> ChromeMediumLow <br/><br/> BaseHigh <br/><br/> BaseLow <br/><br/> AltMediumLow </td>
    </tr>
    <tr>
        <td> <b>Empfohlene Verwendung:</b> Wenn nur primärer Text der Farbe AltHigh über Acryl platziert wird, kann Ihre App diese Ressourcen von 60% verwenden. Es wird empfohlen, den <a href="../controls-and-patterns/navigationview.md">vertikalen Navigationsbereich</a> Ihrer App, d.h. das Hamburger-Menü, mit 60% Acryl zu zeichnen. </td>
    </tr>
</table>

Zusätzlich zu farbneutralem Acryl haben wir Ressourcen hinzugefügt, mit denen sich das Acryl mithilfe von benutzerdefinierten Akzentfarben färben lässt. Wir empfehlen, farbiges Acryl sparsam zu verwenden. Platzieren Sie für die bereitgestellten Varianten dark1 und dark2 weißen bzw. hellfarbigen Text der Textfarbe des dunklen Designs entsprechend über diesen Ressourcen.
<table>
    <tr>
        <th align="center">Ressourcenschlüssel</th>
        <th align="center">Farbton-Deckkraft</th>
        <th align="center"><a href="color.md">Farbton und Fallbackfarben</a> </th>
    </tr>
    <tr>
        <td> SystemControlAccentAcrylicWindowAccentMediumHighBrush, SystemControlAccentAcrylicElementAccentMediumHighBrush  </td>
        <td align="center"> 70% </td>
        <td> SystemAccentColor </td>
    </tr>
    <tr>
        <td> SystemControlAccentDark1AcrylicWindowAccentDark1Brush, SystemControlAccentDark1AcrylicElementAccentDark1Brush  </td>
        <td align="center"> 80% </td>
        <td> SystemAccentColorDark1 </td>
    </tr>
    <tr>
        <td> SystemControlAccentDark2AcrylicWindowAccentDark2MediumHighBrush, SystemControlAccentDark2AcrylicElementAccentDark2MediumHighBrush  </td>
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
 - **TintOpacity**: die Deckkraft der Farbtonschicht. Wir empfehlen 80 % Deckkraft als Ausgangspunkt, obwohl verschiedene Farben möglicherweise bei anderen Translucencies aussehen.
 - **BackgroundSource**: die Kennzeichnung zum Festlegen, ob Sie Hintergrund- oder In-App Acryl verwenden möchten.
 - **FallbackColor**: die Volltonfarbe, die Acryl in den Stromsparmodus ersetzt. Im Fall von Hintergrund-Acryl ersetzt die Fallbackfarbe das Acryl auch, wenn Ihre App nicht im aktiven Desktopfenster angezeigt wird oder wenn die App auf dem Telefon oder der Xbox ausgeführt wird.

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

## <a name="extend-acrylic-into-the-title-bar"></a>Erweitern Sie Acryl auf die Titelleiste

Um Ihrem App-Fenster ein nahtloses Aussehen zu verleihen, können Sie im Bereich der Titelleiste Acryl verwenden. In diesem Beispiel wird Acryl in die Titelleiste erweitert, indem die [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar) der Eigenschaften des Objekts [ButtonBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonBackgroundColor) und [ButtonInactiveBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonInactiveBackgroundColor) auf [Colors.Transparent](https://docs.microsoft.com/uwp/api/Windows.UI.Colors.Transparent) festgelegt werden. 

```csharp
/// Extend acrylic into the title bar. 
private void ExtendAcrylicIntoTitleBar()
{
    CoreApplication.GetCurrentView().TitleBar.ExtendViewIntoTitleBar = true;
    ApplicationViewTitleBar titleBar = ApplicationView.GetForCurrentView().TitleBar;
    titleBar.ButtonBackgroundColor = Colors.Transparent;
    titleBar.ButtonInactiveBackgroundColor = Colors.Transparent;
}
```

Dieser Code kann in die [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_)-Methode Ihre App eingefügt werden (_App.xaml.cs_), nach dem Aufruf von [Window.Activate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.Activate) wie hier gezeigt, oder auf der ersten Seite Ihrer App. 


```csharp
// Call your extend acrylic code in the OnLaunched event, after 
// calling Window.Current.Activate.
protected override void OnLaunched(LaunchActivatedEventArgs e)
{
    Frame rootFrame = Window.Current.Content as Frame;

    // Do not repeat app initialization when the Window already has content,
    // just ensure that the window is active
    if (rootFrame == null)
    {
        // Create a Frame to act as the navigation context and navigate to the first page
        rootFrame = new Frame();

        rootFrame.NavigationFailed += OnNavigationFailed;

        if (e.PreviousExecutionState == ApplicationExecutionState.Terminated)
        {
            //TODO: Load state from previously suspended application
        }

        // Place the frame in the current Window
        Window.Current.Content = rootFrame;
    }

    if (e.PrelaunchActivated == false)
    {
        if (rootFrame.Content == null)
        {
            // When the navigation stack isn't restored navigate to the first page,
            // configuring the new page by passing required information as a navigation
            // parameter
            rootFrame.Navigate(typeof(MainPage), e.Arguments);
        }
        // Ensure the current window is active
        Window.Current.Activate();

        // Extend acrylic
        ExtendAcrylicIntoTitleBar();
    }
}
```

Darüber hinaus müssen Sie den Titel der App, der normalerweise automatisch in der Titelleiste angezeigt wird, mit einem TextBlock ziehen, der `CaptionTextBlockStyle` verwendet. Weitere Informationen finden Sie unter [Anpassen der Titelleiste](../shell/title-bar.md).

## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen
* Verwenden Sie Acryl als Hintergrundmaterial von nicht primären App-Oberflächen wie Navigationsbereichen.
* Dehnen Sie das Acryl auf mindestens einen Rand der App aus, um durch eine dezente Vermischung mit der Umgebung der App eine nahtlose Oberfläche bereitzustellen.
* Versehen keine desktop Arylic auf großen Hintergrund Oberflächen Ihrer App – dies bricht das mentale Modell von Acryl in erster Linie für die vorübergehende Oberflächen verwendet wird.
* Platzieren Sie In-App- und Hintergrund-Acryl nicht direkt nebeneinander, um visuelle Spannung an den Rändern zu vermeiden.
* Platzieren Sie nicht mehrere Acrylbereiche mit demselben Farbton und derselben Deckkraft nebeneinander, da dies eine unerwünschte sichtbare Naht erzeugt.
* Platzieren Sie keinen farbigen Text über Acryloberflächen.

## <a name="how-we-designed-acrylic"></a>Unser Acryl-Entwurfsansatz

Wir haben die Hauptkomponenten des Acryls optimiert, um eine individuelle Darstellung und einzigartige Eigenschaften zu erhalten. Wir begannen mit Transparenz, weichzeichnungs- und Geräusch, flachen Oberflächen visuelle Tiefe und Dimension hinzuzufügen. Dann fügten wir eine Ausschluss-Mischmodus-Ebene hinzu, um den Kontrast und die Lesbarkeit der auf dem Acrylhintergrund platzierten UI sicherzustellen. Zuletzt fügten wir Farbtöne hinzu, um Personalisierungen zu ermöglichen. Zusammen ergeben diese Ebenen ein neues, einsatzbereites Material.

![Acrylzusammensetzung](images/AcrylicRecipe_Diagram.jpg)
<br/>Das Acryl setzt sich folgendermaßen zusammen: Hintergrund, Weichzeichnungsfilter, Ausschluss-Mischung, Überlagerung der Farbe/des Farbtons, Störungsfilter


## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.

## <a name="related-articles"></a>Verwandte Artikel

[**Reveal-highlight**](reveal.md)
