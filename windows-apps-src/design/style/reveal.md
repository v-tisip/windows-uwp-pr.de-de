---
author: mijacobs
description: Einblendungen sind neue Lichteffekte, welche die interaktiven Elemente in Ihrer App mit Tiefe und Fokus versehen kann.
title: Reveal-highlight
template: detail.hbs
ms.author: mijacobs
ms.date: 08/9/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: kisai
design-contact: conrwi
dev-contact: jevansa
doc-status: Published
ms.localizationpriority: high
ms.openlocfilehash: 8ba0d9939d7ab1d9826ed2848e476499f09c628f
ms.sourcegitcommit: 4b522af988273946414a04fbbd1d7fde40f8ba5e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2018
---
# <a name="reveal-highlight"></a>Reveal-highlight

Einblendungen sind neue Lichteffekte, welche die interaktiven Elemente in Ihrer App mit Tiefe und Fokus versehen kann.

> **Wichtige APIs**: [RevealBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush), [RevealBackgroundBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbackgroundbrush), [RevealBorderBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealborderbrush), [RevealBrushHelper-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrushhelper), [VisualState-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.VisualState)

Das Verhalten von Einblendungen zeigt den klickbaren Inhalt des Containers an, wenn der Mauszeiger in der Nähe ist.

![Reveal Visual](images/Nav_Reveal_Animation.gif)

Da durch Einblendungen die ausgeblendeten Rahmen um Objekte herum angezeigt werden, entwickeln Benutzer ein besseres Verständnis von dem Raum, mit dem diese Objekte interagieren. Darüber hinaus erfahren sie dadurch, welche Aktionen verfügbar sind. Dies ist besonders bei Listensteuerelementen und Gruppen von Schaltflächen wichtig.

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Reveal">die App zu öffnen und Einblendungen in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="video-summary"></a>Video-Zusammenfassung

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev013/player]

## <a name="reveal-and-the-fluent-design-system"></a>Einblendungen und das Fluent Design-System

 Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten. „Einblendungen” ist eine Komponente des Fluent Design-Systems, die Lichteffekte in Ihrer App ermöglicht. Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).

## <a name="how-to-use-it"></a>Verwendung

Einblendungen funktionieren automatisch bei einigen Steuerelementen. Für andere Steuerelemente können Sie Einblendungen aktivieren, indem Sie dem Steuerelement einen speziellen Stil zuweisen.

## <a name="controls-that-automatically-use-reveal"></a>Steuerelemente, die Einblendungen automatisch verwenden

- [**ListView**](../controls-and-patterns/lists.md)
- [**GridView**](../controls-and-patterns/lists.md)
- [**TreeView**](../controls-and-patterns/tree-view.md)
- [**NavigationView**](../controls-and-patterns/navigationview.md)
- [**AutosuggestBox**](../controls-and-patterns/auto-suggest-box.md)
- [**MediaTransportControl**](../controls-and-patterns/media-playback.md)
- [**CommandBar**](../controls-and-patterns/app-bars.md)
- [**ComboBox**](../controls-and-patterns/lists.md)

Die folgenden Abbildungen zeigen die Auswirkungen von Einblendungen auf verschiedene Steuerelemente:

![Beispiele für Einblendungen](images/RevealExamples_Collage.png)

## <a name="enabling-reveal-on-other-common-controls"></a>Aktivieren von Einblendungen für andere allgemeine Steuerelemente

Für Szenarien, in denen Einblendungen angewendet werden sollten (diese Steuerelemente sind Hauptinhalt und/oder werden in einer Liste oder Auflistungsausrichtung verwendet), haben wir optionale Ressourcenformate bereitgestellt, mithilfe derer Sie Einblendungen für solche Situationen aktivieren können.

Diese Steuerelemente verfügen nicht standardmäßig über Einblendungen, da sie kleinere Steuerelemente sind, die in der Regel als Hilfssteuerelemente für die zentralen Punkte Ihrer Anwendung dienen. Alle Apps sind jedoch verschieden, und wenn diese Steuerelemente in Ihrer App am meisten verwendet werden, stehen Ihnen einige Formate als Hilfe zur Verfügung:

| Name des Steuerelements   | Ressourcenname |
|----------|:-------------:|
| Button |  ButtonRevealStyle |
| ToggleButton | ToggleButtonRevealStyle |
| RepeatButton | RepeatButtonRevealStyle |
| AppBarButton | AppBarButtonRevealStyle |
| SemanticZoom | SemanticZoomRevealStyle |

Um diese Formate anzuwenden, aktualisieren Sie einfach folgendermaßen die Eigenschaft „Style”:

```XAML
<Button Content="Button Content" Style="{StaticResource ButtonRevealStyle}"/>
```

## <a name="enabling-reveal-on-custom-controls"></a>Aktivieren von Einblendungen für benutzerdefinierte Steuerelemente

Berücksichtigen Sie bei der Entscheidung, ob das benutzerdefinierte Steuerelement Einblendungen erhalten soll oder nicht, ob Sie eine Gruppierung von interaktiven Elementen benötigen, die sich alle auf eine übergeordnete Feature oder Aktion beziehen, die Sie in Ihrer App ausführen möchten.

Beispielsweise sind NavigationView-Elemente mit der Seitennavigation verknüpft. CommandBar-Schaltflächen beziehen sich auf Menüaktionen oder Feature-Aktionen. Die MediaTransportControl-Schaltflächen unterhalb beziehen sich auf das Medium, das wiedergegeben wird.

Die Steuerelemente, die die Einblendung erhalten, müssen nicht miteinander verknüpft werden, sondern nur in einem HD-Bereich sein und einen größeren Zweck dienen.

Rufen Sie zum Aktivieren von Einblendungen für benutzerdefinierte Steuerelemente oder Steuerelemente mit neuen Vorlagen das Format für dieses Steuerelement in den visuellen Zuständen der Vorlage für dieses Steuerelement auf, und legen Sie Einblendungen im Stammraster fest:

```xaml
<VisualState x:Name="PointerOver">
    <VisualState.Setters>
        <Setter Target="RootGrid.(RevealBrush.State)" Value="PointerOver" />
        <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPointerOver}" />
        <Setter Target="ContentPresenter.BorderBrush" Value="Transparent"/>
        <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPointerOver}" />
    </VisualState.Setters>
</VisualState>
```

Es ist wichtig zu beachten, dass zur Einblendung sowohl ein Pinsel als auch Setter in Visual State benötigt werden, um einwandfrei zu arbeiten. Das einfache Festlegen eines Steuerelements für Reveal-Pinselressourcen alleine aktivieren das Steuerelement nicht. Ziele oder Einstellungen zu verwenden ohne die Werte als Reveal-Pinsel festgelegt zu haben, aktiviert die Einblendung auch nicht.

Wir haben eine Reihe von System-Reveal-Pinsels erstellt, mit denen Sie die Benutzeroberfläche anpassen können. Sie können z.B. den Pinsel **ButtonRevealBackground** zum Erstellen eines Hintergrunds für eine benutzerdefinierte Schaltfläche oder den Pinsel **ListViewItemRevealBackground** für benutzerdefinierte Listen und so weiter verwenden.

(Informationen zur Funktionsweise von Ressourcen in XAMl finden Sie im Artikel [Xaml-Ressourcenverzeichnis](../controls-and-patterns/resourcedictionary-and-xaml-resource-references.md).)

### <a name="reveal-on-listview-controls-with-nested-buttons"></a>Einblendung auf ListView-Steuerelementen mit geschachtelten Schaltflächen

Besitzen Sie ein [ListView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ListView) und Schaltflächen oder aufgerufene Inhalte, die innerhalb eines [ListViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listviewitem)-Elements geschachtelt sind, sollten Sie die Einblendung für die geschachtelten Elemente aktivieren.

Falls Sie Schaltflächen oder Schaltflächen ähnliche Steuerelemente in einem ListViewItem haben, legen Sie einfach die [Stil](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Style)-Eigenschaft des Steuerelements auf die statische Ressource **ButtonRevealStyle** fest. 

![Geschachtelte Einblendungen](images/NestedListContent.png)

Dieses Beispiel ermöglicht Einblendungen auf mehrere Schaltflächen in einem ListViewItem. 

```XAML
<ListViewItem>
    <StackPanel Orientation="Horizontal">
        <TextBlock Margin="5">Test Text: lorem ipsum.</TextBlock>
        <StackPanel Orientation="Horizontal">
            <Button Content="&#xE71B;" FontFamily="Segoe MDL2 Assets" Width="45" Height="45" Margin="5" Style="{StaticResource ButtonRevealStyle}"/>
            <Button Content="&#xE728;" FontFamily="Segoe MDL2 Assets" Width="45" Height="45" Margin="5" Style="{StaticResource ButtonRevealStyle}"/>
            <Button Content="&#xE74D;" FontFamily="Segoe MDL2 Assets" Width="45" Height="45" Margin="5" Style="{StaticResource ButtonRevealStyle}"/>
         </StackPanel>
    </StackPanel>
</ListViewItem>
```

### <a name="listviewitempresenter-with-reveal"></a>ListViewItemPresenter mit Einblendungen

Listen werden in XAML besonders behandelt, und bei Einblendungen müssen wir Visual State-Manager für Einblendungen nur innerhalb des ListViewItemPresenters definieren:

```XAML
<ListViewItemPresenter>
<!-- ContentTransitions, SelectedForeground, etc. properties -->
RevealBackground="{ThemeResource ListViewItemRevealBackground}"
RevealBorderThickness="{ThemeResource ListViewItemRevealBorderThemeThickness}"
RevealBorderBrush="{ThemeResource ListViewItemRevealBorderBrush}">
    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup x:Name="CommonStates">
        <VisualState x:Name="Normal" />
        <VisualState x:Name="Selected" />
        <VisualState x:Name="PointerOver">
            <VisualState.Setters>
                <Setter Target="Root.(RevealBrush.State)" Value="PointerOver" />
            </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="PointerOverSelected">
                <VisualState.Setters>
                    <Setter Target="Root.(RevealBrush.State)" Value="PointerOver" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="PointerOverPressed">
                <VisualState.Setters>
                    <Setter Target="Root.(RevealBrush.State)" Value="Pressed" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="Pressed">
                <VisualState.Setters>
                    <Setter Target="Root.(RevealBrush.State)" Value="Pressed" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="PressedSelected">
                <VisualState.Setters>
                    <Setter Target="Root.(RevealBrush.State)" Value="Pressed" />
                </VisualState.Setters>
            </VisualState>
            </VisualStateGroup>
                <VisualStateGroup x:Name="EnabledGroup">
                    <VisualState x:Name="Enabled" />
                    <VisualState x:Name="Disabled">
                        <VisualState.Setters>
                             <Setter Target="Root.RevealBorderThickness" Value="0"/>
                        </VisualState.Setters>
                    </VisualState>
                </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
</ListViewItemPresenter>
```

Dies bedeutet ein Anfügen an das Ende der Eigenschaftssammlung innerhalb von ListViewItemPresenter mit den bestimmten Setter des Visual States für eine Einblendung.

### <a name="full-template-example"></a>Vollständiges Vorlagenbeispiel

Hier sehen Sie eine gesamte Vorlage und wie eine Schaltfläche zum Einblenden aussehen würde:

```XAML
<Style TargetType="Button" x:Key="ButtonStyle1">
    <Setter Property="Background" Value="{ThemeResource ButtonRevealBackground}" />
    <Setter Property="Foreground" Value="{ThemeResource ButtonForeground}" />
    <Setter Property="BorderBrush" Value="{ThemeResource ButtonRevealBorderBrush}" />
    <Setter Property="BorderThickness" Value="2" />
    <Setter Property="Padding" Value="8,4,8,4" />
    <Setter Property="HorizontalAlignment" Value="Left" />
    <Setter Property="VerticalAlignment" Value="Center" />
    <Setter Property="FontFamily" Value="{ThemeResource ContentControlThemeFontFamily}" />
    <Setter Property="FontWeight" Value="Normal" />
    <Setter Property="FontSize" Value="{ThemeResource ControlContentThemeFontSize}" />
    <Setter Property="UseSystemFocusVisuals" Value="True" />
    <Setter Property="FocusVisualMargin" Value="-3" />
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="Button">
                <Grid x:Name="RootGrid" Background="{TemplateBinding Background}">

                    <VisualStateManager.VisualStateGroups>
                        <VisualStateGroup x:Name="CommonStates">
                            <VisualState x:Name="Normal">

                                <Storyboard>
                                    <PointerUpThemeAnimation Storyboard.TargetName="RootGrid" />
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="PointerOver">
                                <VisualState.Setters>
                                    <Setter Target="RootGrid.(RevealBrush.State)" Value="PointerOver" />
                                    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPointerOver}" />
                                    <Setter Target="ContentPresenter.BorderBrush" Value="Transparent"/>
                                    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPointerOver}" />
                                </VisualState.Setters>

                                <Storyboard>
                                    <PointerUpThemeAnimation Storyboard.TargetName="RootGrid" />
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="Pressed">
                                <VisualState.Setters>
                                    <Setter Target="RootGrid.(RevealBrush.State)" Value="Pressed" />
                                    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPressed}" />
                                    <Setter Target="ContentPresenter.BorderBrush" Value="{ThemeResource ButtonRevealBackgroundPressed}" />
                                    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPressed}" />
                                </VisualState.Setters>

                                <Storyboard>
                                    <PointerDownThemeAnimation Storyboard.TargetName="RootGrid" />
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="Disabled">
                                <VisualState.Setters>
                                    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundDisabled}" />
                                    <Setter Target="ContentPresenter.BorderBrush" Value="{ThemeResource ButtonRevealBorderBrushDisabled}" />
                                    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundDisabled}" />
                                </VisualState.Setters>
                            </VisualState>
                        </VisualStateGroup>

              </VisualStateManager.VisualStateGroups>
                    <ContentPresenter x:Name="ContentPresenter"
                    BorderBrush="{TemplateBinding BorderBrush}"
                    BorderThickness="{TemplateBinding BorderThickness}"
                    Content="{TemplateBinding Content}"
                    ContentTransitions="{TemplateBinding ContentTransitions}"
                    ContentTemplate="{TemplateBinding ContentTemplate}"
                    Padding="{TemplateBinding Padding}"
                    HorizontalContentAlignment="{TemplateBinding HorizontalContentAlignment}"
                    VerticalContentAlignment="{TemplateBinding VerticalContentAlignment}"
                    AutomationProperties.AccessibilityView="Raw" />
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
```

## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen
- Verwenden Sie die Einblendung für Elemente, in denen der Benutzer Aktionen (Schaltflächen, Auswahl) ausführt
- Verwenden Sie Einblendungen bei der Gruppierung von interaktiven Elementen, die nicht standardmäßig visuelle Trennzeichen haben (Listen, Befehlsleisten)
- Verwenden Sie Einblendungen in Bereichen mit vielen interaktiven Elementen
- Verwenden Sie Einblendungen nicht auf statischen Inhalten (Hintergrund, Text)
- Verwenden Sie Einblendungen nicht in einzelnen, isolierten Situationen
- Verwenden Sie Einblendungen nicht auf sehr großen Elementen (größer als 500epx)
- Verwenden Sie Einblendungen nicht bei sicherheitsbezogenen Entscheidungen, da es die Aufmerksamkeit von der Nachricht, die Sie an die Benutzer übermitteln möchten, weglenken kann.

## <a name="how-we-designed-reveal"></a>Unser Einblendungs-Entwurfsansatz

Es gibt zwei visuelle Hauptkomponenten für Einblendungen: das Verhalten **Einblenden durch Daraufzeigen** und das Verhalten **Rahmen einblenden**.

![Ebenen einblenden](images/RevealLayers.png)

Das Verhalten „Einblenden durch Daraufzeigen” ist direkt mit dem Inhalt verbunden, auf den gezeigt wird (mit Zeiger- oder Fokuseingaben). Dabei wird ein leichter Lichthof um das Element herum eingeblendet, auf das gezeigt oder das fokussiert wird, sodass Sie wissen, dass Sie damit interagieren können.

Das Verhalten „Rahmen einblenden” wird auf das fokussierte Element und andere Elemente in dessen Nähe angewendet. Dadurch erfahren Sie, dass diese Objekte in der Nähe ähnliche Aktionen wie das aktuell fokussierte Objekt durchführen können.

Die Aufschlüsselung der Anleitung für Einblendungen sieht folgendermaßen aus:

- Das Verhalten „Rahmen einblenden” befindet sich über dem gesamten Inhalt, jedoch an den angegebenen Rändern.
- Text und Inhalt werden direkt unter dem Verhalten „Rahmen einblenden” angezeigt.
- Das Verhalten „Einblenden durch Daraufzeigen” befindet sich unterhalb von Inhalt und Text.
- Die Backplate (die das Verhalten „Rahmen einblenden” aktiviert)
- Der Hintergrund (Hintergrund des Steuerelements)

<!--
<div class=”microsoft-internal-note”>
To create your own Reveal lighting effect for static comps or prototype purposes, see the full [uni design guidance](http://uni/DesignDepot.FrontEnd/#/ProductNav/3020/1/dv/?t=Resources%7CToolkit%7CReveal&f=Neon) for this effect in illustrator.
</div>
-->  

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.

## <a name="related-articles"></a>Verwandte Artikel

- [RevealBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush)
- [Acryl](acrylic.md)
- [Kompositionseffekte](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
- [Fluent Design für UWP](../fluent-design-system/index.md)
- [Wissenschaft im System: Fluent Design und Tiefe](https://medium.com/microsoft-design/science-in-the-system-fluent-design-and-depth-fb6d0f23a53f)
- [Wissenschaft im System: Fluent Design und Licht](https://medium.com/microsoft-design/the-science-in-the-system-fluent-design-and-light-94a17e0b3a4f)
