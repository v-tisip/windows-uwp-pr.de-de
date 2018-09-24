---
author: mijacobs
description: Eine Art von Pinsel, der eine durchsichtige Textur erzeugt.
title: Acryl-Material
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
ms.localizationpriority: medium
ms.openlocfilehash: 8589a450b53a5ea028f8af2cee2aef7dc0816b52
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "4155611"
---
# <a name="acrylic-material"></a>Acryl-Material

![Favoritenbild](images/header-acrylic.svg)

Acryl ist eine Art von [Pinsel](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush) , der eine durchsichtige Textur erzeugt. Sie können Acryl auf App-Oberflächen anwenden, um Tiefe hinzuzufügen und eine visuelle Hierarchie herzustellen.  <!-- By allowing user-selected wallpaper or colors to shine through, acrylic keeps users in touch with the OS personalization they've chosen. -->

> **Wichtige APIs**: [AcrylicBrush-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.Background)

:::row:::
    :::column:::
        Acryl im hellen Design ![Acryl im hellen Design](images/Acrylic_LightTheme_Base.png)
    :::column-end:::
    :::column:::
        Acryl im dunklen Design ![Acryl im dunklen Design](images/Acrylic_DarkTheme_Base.png)
    :::column-end:::
:::row-end:::

## <a name="acrylic-and-the-fluent-design-system"></a>Acryl und das Fluent Design-System

 Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten. Acryl ist Komponente des Fluent Design-Systems, die physische Struktur (Material) und Tiefe zu Ihrer App hinzugefügt. Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).

 ## <a name="video-summary"></a>Video-Zusammenfassung

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev002/player]

## <a name="examples"></a>Beispiele

:::row:::
    ::: Column Span::: ![einige Image](images/XAML-controls-gallery-app-icon.png)
    :::column-end:::
    ::: Column Span = "2"::: **XAML-Steuerelementekatalog**<br>
        Wenn Sie die XAML-Steuerelementekatalog-app installiert haben, klicken Sie <a href="xamlcontrolsgallery:/item/Acrylic">hier</a> auf die app zu öffnen und Acryl in Aktion zu sehen.

        <a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a><br>
        <a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a>
    :::column-end:::
:::row-end:::

## <a name="when-to-use-acrylic"></a>Wann sollte Acryl verwendet werden?

Wir empfehlen, unterstützende UI-Komponenten, beispielsweise In-App-Navigation oder Steuerelemente, auf einer Acryloberfläche zu platzieren. Dieses Material ist auch hilfreich für vorübergehende UI-Elemente, wie beispielsweise Dialogfelder und Flyouts, da dadurch eine sichtbare Beziehung mit dem Inhalt beibehalten werden kann, der die vorübergehende UI ausgelöst hat. Acryl wurde zur Verwendung als Hintergrundmaterial und in optisch unauffälligen Bereichen entwickelt. Sie sollten Acryl daher nicht in detaillierten Vordergrundelementen anwenden.

Für Oberflächen hinter dem primären App-Inhalt sollten einheitliche, undurchsichtige Hintergründe verwendet werden.

Ziehen Sie es in Erwägung, Acryl auf einen oder mehrere Ränder Ihrer App, einschließlich der Titelleiste des Fensters, zu erweitern, um die visuelle Darstellung zu verbessern. Vermeiden Sie Streifeneffekte durch das Stapeln von Acrylfarben verschiedener Mischungen nebeneinander. Acryl ist ein Tool zum Erzeugen von visueller Harmonie in Ihren Designs, bei inkorrekter Verwendung können sich jedoch visuelle Störungen ergeben.

Berücksichtigen Sie die folgenden Verwendungsmuster, um zu entscheiden, wie sich Acryl am besten in Ihre App integrieren lässt.

### <a name="vertical-acrylic-pane"></a>Vertikaler Acrylbereich

Es wird empfohlen, in Apps mit vertikaler Navigation Acryl auf den sekundären Bereich anzuwenden, der die Navigationselemente enthält.

![App-Muster mit einem einzigen vertikalen Acrylbereich](images/acrylic_app-pattern_vertical.png)

[NavigationView](../controls-and-patterns/navigationview.md) ist ein neues allgemeines Steuerelement zum Hinzufügen von Navigation zu Ihrer App. Der visuelle Entwurf dieses Elements enthält Acryl. Der Bereich von NavigationView zeigt Hintergrund-Acryl, wenn der Bereich parallel mit dem primären Inhalt geöffnet ist, und dieses wird automatisch in In-App-Acryl umgewandelt, wenn der Bereich als Überlagerung geöffnet ist.

Wenn Ihre app nicht NavigationView nutzen kann, und Sie Acryl selbst hinzufügen möchten, empfehlen wir die Verwendung von relativ durchsichtige Acryl mit 60 % Farbton-Deckkraft.
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
> Das Rendern von acryloberflächen ist GPU-intensiv, das Gerät den Energieverbrauch zu erhöhen und Akkulaufzeit verkürzt werden kann. Acryleffekte werden automatisch deaktiviert, wenn Geräte Stromsparmodus versetzt, und Benutzer können acryleffekte für alle apps, deaktivieren, wenn der Benutzer.


## <a name="acrylic-blend-types"></a>Acrylmischungen
Die auffälligste Eigenschaft von Acryl ist seine Transparenz. Es gibt zwei Acrylmischungen, die beeinflussen, welche Inhalte durch das Material sichtbar sind:
 - **Hintergrund-Acryl** zeigt den Desktophintergrund und andere Fenster, die sich hinter der derzeit aktiven App befinden. Dabei wird Tiefe zwischen den Fenstern der Anwendung hinzugefügt, während die Personalisierungseinstellungen des Benutzers angewendet werden.
 - **In-App-Acryl** fügt Tiefenwirkung innerhalb des App-Frames hinzu, wodurch sowohl Fokus als auch Hierarchie erzeugt werden.

 ![Hintergrund-Acryl](images/BackgroundAcrylic_DarkTheme.png)

 ![In-App-Acryl](images/AppAcrylic_DarkTheme.png)

 Schichten Sie mehrere Acryloberflächen vorsichtig übereinander. Hintergrund-Acryl sollte sich, wie der Name schon sagt, in der Z-Reihenfolge nicht am nächsten am Benutzer befinden. Mehrere Schichten von Hintergrund-Acryl führen tendenziell zu unerwarteten optischen Täuschungen und sollten vermieden werden. Wenn Sie Acryl übereinanderschichten möchten, verwenden Sie dafür In-App-Acryl, und ziehen Sie es in Erwägung, den Farbtonwert des Acryls zu reduzieren, damit die Schichten für den Betrachter optisch besser dargestellt werden.


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
 - **TintOpacity**: die Deckkraft der Farbtonschicht. Wir empfehlen 80 % Deckkraft als Ausgangspunkt, obwohl verschiedene Farben bei anderer Translucencies aussehen können.
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
* Platzieren Sie In-App- und Hintergrund-Acryl nicht direkt nebeneinander, um visuelle Spannung an den Rändern zu vermeiden.
* Platzieren Sie nicht mehrere Acrylbereiche mit demselben Farbton und derselben Deckkraft nebeneinander, da dies eine unerwünschte sichtbare Naht erzeugt.
* Platzieren Sie keinen farbigen Text über Acryloberflächen.

## <a name="how-we-designed-acrylic"></a>Unser Acryl-Entwurfsansatz

Wir haben die Hauptkomponenten des Acryls optimiert, um eine individuelle Darstellung und einzigartige Eigenschaften zu erhalten. Wir begannen mit Transparenz, weichzeichnungs- und störungsfiltern visuelle Tiefe und Dimension, flachen Oberflächen hinzufügen. Dann fügten wir eine Ausschluss-Mischmodus-Ebene hinzu, um den Kontrast und die Lesbarkeit der auf dem Acrylhintergrund platzierten UI sicherzustellen. Zuletzt fügten wir Farbtöne hinzu, um Personalisierungen zu ermöglichen. Zusammen ergeben diese Ebenen ein neues, einsatzbereites Material.

![Acrylzusammensetzung](images/AcrylicRecipe_Diagram.jpg)
<br/>Das Acryl setzt sich folgendermaßen zusammen: Hintergrund, Weichzeichnungsfilter, Ausschluss-Mischung, Überlagerung der Farbe/des Farbtons, Störungsfilter


## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.

## <a name="related-articles"></a>Verwandte Artikel

[**Reveal-highlight**](reveal.md)
