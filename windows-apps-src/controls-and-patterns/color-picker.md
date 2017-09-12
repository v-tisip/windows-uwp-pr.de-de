---
author: Jwmsft
Description: "Mithilfe eines Farbwählers kann der Benutzer Farben suchen und auswählen."
title: "Farbwähler"
label: Color Picker
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: kisai
design-contact: ksulliv
dev-contact: llongley
doc-status: Published
ms.openlocfilehash: 546f904239c61c36422070e946d3cd1c6496c9aa
ms.sourcegitcommit: 45490bd85e6f8d247a041841d547ecac2ff48250
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2017
---
# <a name="color-picker"></a>Farbwähler

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe möglicherweise noch substanziell verändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Mithilfe eines Farbwählers können Benutzer Farben suchen und auswählen. Standardmäßig können sie durch die Farben eines Farbspektrums navigieren oder eine bestimmte Farbe in einem Textfeld des Typs „Rot-Grün-Blau (RGB)“, „Wert für Farbton/Sättigung“ oder „Hexadezimal“ angeben.

> **Wichtige APIs:** [Klasse „ColorPicker“](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker), [Eigenschaft „Color“](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker_color), [Ereignis „ColorChanged“](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker_colorchanged)

![Ein Farbwähler in Standardausführung](images/color-picker-default.png)


## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Mithilfe eines Farbwählers können Benutzer in Ihrer App Farben auswählen. Beispielsweise können sie so Farbeinstellungen wie Textfarben, Hintergrundfarben oder App-Farbdesigns ändern.

Falls Ihre App zum Zeichnen oder für andere stiftbasierte Aufgaben gedacht ist, sollten Sie neben dem Farbwähler auch die Implementierung von [Steuerelementen für Freihandeingaben](http://windowsstyleguide/controls-and-patterns/inking-controls/) in Betracht ziehen.

## <a name="create-a-color-picker"></a>Erstellen eines Farbwählers

In diesem Beispiel zeigen wir Ihnen, wie Sie einen Standardfarbwähler in XAML erstellen können.

```xaml
<ColorPicker x:Name="myColorPicker"/>
```

Der Farbwähler zeigt standardmäßig eine Vorschau der ausgewählten Farbe in dem rechteckigen Balken neben dem Farbspektrum an. Um auf die ausgewählte Farbe zuzugreifen und sie in Ihrer App zu verwenden, können Sie entweder das Ereignis [ColorChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker_colorchanged) oder die Eigenschaft [Color](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker_color) verwenden. Detaillierten Code finden Sie in den nachfolgenden Beispielen.

### <a name="bind-to-the-chosen-color"></a>Binden an die ausgewählte Farbe

Soll die Farbauswahl sofort wirksam werden, können Sie sie entweder per Datenbindung an die Eigenschaft „Color“ binden oder über das Ereignis „ColorChanged“ in Ihrem Code auf die ausgewählte Farbe zugreifen.

In diesem Beispiel binden Sie die Eigenschaft „Color“ einer als Füllung für ein Rechteck verwendeten Klasse „SolidColorBrush“ direkt an die im Farbwähler ausgewählte Farbe. Jede Änderung am Farbwähler zieht eine Liveänderung an der gebundenen Eigenschaft nach sich.

```xaml
<ColorPicker x:Name="myColorPicker"
             ColorSpectrumShape=”Ring”
             IsColorPreviewVisible="False"
             IsColorChannelTextInputVisible="False"
             IsHexInputVisible="False"/>

<Rectangle Height="50" Width="50">
    <Rectangle.Fill>
        <SolidColorBrush Color="{x:Bind myColorPicker.Color, Mode=OneWay}"/>
    </Rectangle.Fill>
</Rectangle>
```

In diesem Beispiel wird ein vereinfachter Farbwähler verwendet, der nur aus einem kreisförmigen Spektrum und einem Schieberegler besteht. Dies ist eine gängige unkomplizierte Ausführung eines Farbwählers. Lässt sich die Farbänderung in Echtzeit an dem jeweils betroffenen Objekt nachvollziehen, muss kein Farbvorschaubalken angezeigt werden. Weitere Informationen finden Sie im Abschnitt *Anpassen des Farbwählers*.

### <a name="save-the-chosen-color"></a>Speichern der ausgewählten Farbe

In einigen Fällen soll die Farbänderung nicht direkt angewendet werden. Wenn Sie den Farbwähler beispielsweise in einem Flyout hosten, sollten Sie die ausgewählte Farbe erst anwenden, nachdem der Benutzer die Auswahl bestätigt oder das Flyout geschlossen hat. Der ausgewählte Farbwert lässt sich auch zur späteren Verwendung speichern.

In diesem Beispiel wird ein Farbwähler in einem Flyout mit „Bestätigen“-Schaltfläche und „Abbrechen“-Schaltfläche gehostet. Sobald der Benutzer seine Farbauswahl bestätigt, wird die ausgewählte Farbe gespeichert und kann später in der App verwendet werden.

```xaml
<Page.Resources>
    <Flyout x:Key="myColorPickerFlyout">
        <RelativePanel>
            <ColorPicker x:Name="myColorPicker"
                         IsColorChannelTextInputVisible="False"
                         IsHexInputVisible="False"/>

            <Grid RelativePanel.Below="myColorPicker"
                  RelativePanel.AlignLeftWithPanel="True"
                  RelativePanel.AlignRightWithPanel="True">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                </Grid.ColumnDefinitions>
                <Button Content="OK" Click="confirmColor_Click"
                        Margin="0,12,2,0" HorizontalAlignment="Stretch"/>
                <Button Content="Cancel" Click="cancelColor_Click"
                        Margin="2,12,0,0" HorizontalAlignment="Stretch"
                        Grid.Column="1"/>
            </Grid>
        </RelativePanel>
    </Flyout>
</Page.Resources>

<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Button x:Name="colorPickerButton"
            Content="Pick a color"
            Flyout="{StaticResource myColorPickerFlyout}"/>
</Grid>
```

```csharp
private Color mycolor;

private void confirmColor_Click(object sender, RoutedEventArgs e)
{
    // Assign the selected color to a variable to use outside the popup.
    myColor = myColorPicker.Color;

    // Close the Flyout.
    colorPickerButton.Flyout.Hide();
}

private void cancelColor_Click(object sender, RoutedEventArgs e)
{
    // Close the Flyout.
    colorPickerButton.Flyout.Hide();
}
```

### <a name="configure-the-color-picker"></a>Konfigurieren des Farbwählers

Zur Farbauswahl sind nicht alle Felder notwendig, daher ist der Farbwähler flexibel. Sie haben eine Vielzahl von Optionen zur Verfügung, über die Sie dieses Steuerelement an Ihre Anforderungen anpassen können.

Benötigt der Benutzer keine präzise Kontrolle, beispielsweise bei der Auswahl der Textmarkerfarbe in einer Notizen-App, können Sie eine vereinfachte Benutzeroberfläche verwenden. Sie können die Texteingabefelder ausblenden und das Farbspektrum als Kreis darstellen.

Benötigt der Benutzer präzise Kontrolle, beispielsweise in einer Grafikdesign-App, können Sie sowohl Schieberegler als auch Texteingabefelder für jeden Aspekt der Farbe anzeigen.

#### <a name="show-the-circle-spectrum"></a>Anzeigen eines kreisförmigen Spektrums

In diesem Beispiel wird demonstriert, wie Sie den Farbwähler mithilfe der Eigenschaft [ColorSpectrumShape](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker_colorspectrumshape) so konfigurieren können, dass statt des standardmäßigen quadratischen Farbspektrums ein kreisförmiges Farbspektrum angezeigt wird.

```xaml
<ColorPicker x:Name="myColorPicker"
             ColorSpectrumShape="Ring"/>
```

![Farbwähler mit kreisförmigem Spektrum](images/color-picker-ring.png)

Bei der Entscheidung zwischen einem quadratischen und einem kreisförmigen Farbspektrum ist das Hauptkriterium die Genauigkeit. In einem quadratischen Farbspektrum hat der Benutzer mehr Kontrolle über die Farbauswahl, da ein größerer Teil des Farbraums angezeigt wird. Ein kreisförmiges Spektrum ist eher für eine schnelle, unkomplizierte Farbauswahl gedacht.

#### <a name="show-the-alpha-channel"></a>Anzeigen des Alphakanals

In diesem Beispiel implementieren Sie im Farbwähler einen Schieberegler und ein Textfeld für die Deckkraft.

```xaml
<ColorPicker x:Name="myColorPicker"
             IsAlphaEnabled="True"/>
```

![Farbwähler mit „IsAlphaEnabled“ auf „true“](images/color-picker-alpha.png)

#### <a name="show-a-simple-picker"></a>Anzeigen eines einfachen Wählers

In diesem Beispiel wird demonstriert, wie Sie den Farbwähler mit einer einfachen Benutzeroberfläche für die schnelle und unkomplizierte Verwendung konfigurieren können. Sie implementieren das kreisförmige Spektrum und blenden die standardmäßigen Texteingabefelder aus. Lässt sich die Farbänderung in Echtzeit an dem jeweils betroffenen Objekt nachvollziehen, muss kein Farbvorschaubalken angezeigt werden. Andernfalls sollte die Farbvorschau sichtbar sein.

```xaml
<ColorPicker x:Name="myColorPicker"
             ColorSpectrumShape="Ring"
             IsColorPreviewVisible="False"
             IsColorChannelTextInputVisible="False"
             IsHexInputVisible="False"/>
```

![Ein einfacher Farbwähler](images/color-picker-casual.png)

#### <a name="show-or-hide-additional-features"></a>Anzeigen oder Ausblenden von zusätzlichen Funktionen

In der Tabelle unten sind alle Optionen aufgeführt, die Sie zur Konfiguration des Steuerelements „ColorPicker“ verwenden können.

Funktion | Eigenschaften
--------|-----------
Farbspektrum | IsColorSpectrumVisible, ColorSpectrumShape, ColorSpectrumComponents
Farbvorschau | IsColorPreviewVisible
Farbwerte| IsColorSliderVisible, IsColorChannelTextInputVisible
Deckkraftwerte | IsAlphaEnabled, IsAlphaSliderVisible, IsAlphaTextInputVisible
Hexwerte | IsHexInputVisible

> [!NOTE]
> Das Textfeld und der Schieberegler für die Deckkraft werden nur angezeigt, wenn „AlphaEnabled“ auf **true** gesetzt ist. Dann können Sie die Sichtbarkeit der Eingabesteuerelemente mithilfe der Eigenschaften „IsAlphaTextInputVisible“ und „IsAlphaSliderVisible“ anpassen. Details hierzu finden Sie in der API-Dokumentation.

## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen

- Überlegen Sie, welche Art Farbwähler für Ihre App die beste Option ist. Einige Szenarien erfordern keine präzise Farbauswahl; dann ist ein vereinfachter Wähler die bessere Entscheidung.
- Für maximale Genauigkeit bei der Farbauswahl sollten Sie das quadratische Spektrum verwenden, mit einer Mindestgröße von 256×256px. Alternativ können Sie die Texteingabefelder implementieren, damit der Benutzer seine Wunschfarbe präzise anpassen kann.
- Wenn Sie den Farbwähler in einem Flyout hosten, sollte die Farbauswahl nicht bereits durch ein simples Tippen in das Spektrum oder eine einfache Justierung des Schiebereglers übernommen werden. Regeln Sie die Übernahme der Auswahl wie folgt:
  - Implementieren Sie Schaltflächen zum Übernehmen und Abbrechen, über die der Benutzer seine Auswahl anwenden oder verwerfen kann. Durch Klicken oder Tippen auf die Zurück-Schaltfläche bzw. auf eine Stelle außerhalb des Flyouts wird das Flyout geschlossen, ohne dass die Auswahl des Benutzers gespeichert wird.
  - Alternativ kann die Auswahl übernommen werden, sobald der Benutzer das Flyout per Tippen oder Klicken auf eine Stelle außerhalb des Flyouts oder auf die Zurück-Schaltfläche schließt.

## <a name="related-articles"></a>Verwandte Artikel

- [Zeichen- und Eingabestiftinteraktionen in UWP-Apps](../input-and-devices/pen-and-stylus-interactions.md)
- [Freihandeingaben](inking-controls.md)

<!--
<div class=”microsoft-internal-note”>
<p>
<p>
Note: For more info, see the [color picker redlines](http://uni/DesignDepot.FrontEnd/#/ProductNav/3666/15/dv/?t=Windows%7CControls&f=RS2) on UNI.
</div>
-->