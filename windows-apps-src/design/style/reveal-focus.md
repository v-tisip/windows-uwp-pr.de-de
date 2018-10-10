---
author: cphilippona
description: Reveal-Focus sind Lichteffekte, die den Rahmen des fokussierbaren Elementes animieren, wenn der Benutzer den Fokus des Gamepad oder Tastatur darauf lenken.
title: Reveal-Focus
template: detail.hbs
ms.author: mijacobs
ms.date: 03/1/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: chphilip
design-contact: ''
dev-contact: stevenki
ms.localizationpriority: medium
ms.openlocfilehash: 7b5fa84efbe20368be55a50ce20c8e6e5d1fe439
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4504659"
---
# <a name="reveal-focus"></a>Reveal-Focus

![Favoritenbild](images/header-reveal-focus.svg)

Reveal-Focus sind Lichteffekte für [10-Fuß-Erlebnisse](/windows/uwp/design/devices/designing-for-tv), wie z. B. Xbox One-und Fernsehbildschirme. Sie animieren den Rahmen des fokussierbaren Elementes wie beispielsweise Schaltflächen, wenn der Benutzer den Fokus des Gamepad oder der Tastatur darauf lenken. Es ist standardmäßig deaktiviert, lässt sich allerdings ganz einfach aktivieren. 

(Der Effekt "einblenden" markieren, ein Lichteffekt, der interaktive Elemente hervorhebt finden Sie im [Artikel "einblenden" markieren](/windows/uwp/design/style/reveal).)


> **Wichtige APIs**: [Application.FocusVisualKind-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.FocusVisualKind), [FocusVisualKind Enum](https://docs.microsoft.com/uwp/api/windows.ui.xaml.focusvisualkind), [Control.UseSystemFocusVisuals-Eigenschaft](/uwp/api/Windows.UI.Xaml.Controls.Control.UseSystemFocusVisuals)

## <a name="how-it-works"></a>Funktionsweise
Reveal-Focus lenkt den Fokus auf fokussierte Elemente indem ein animierter Schein um den Rahmens des Elements:

![Einblendeanzeige](images/traveling-focus-fullscreen-light-rf.gif)

Dies ist besonders in 10-Fuß-Szenarien, in denen der Benutzer nicht volle Aufmerksamkeit auf den gesamten Fernsehbildschirm lenkt. 

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/RevealFocus">die app zu öffnen und Reveal-Focus in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="how-to-use-it"></a>Verwendung

Reveal-Focus ist, die sich standardmäßig deaktiviert. So aktivieren Sie es:
1. Rufen Sie im Konstruktor der App die Eigenschaft [AnalyticsInfo.VersionInfo.DeviceFamily](/uwp/api/windows.system.profile.analyticsversioninfo.DeviceFamily) auf, und überprüfen Sie, ob die aktuellen Gerätefamilie `Windows.Xbox` ist.
2. Wenn die Gerätefamilie `Windows.Xbox` ist, legen Sie die Eigenschaft [Application.FocusVisualKind](/uwp/api/windows.ui.xaml.application.FocusVisualKind) auf `FocusVisualKind.Reveal` fest. 

```csharp
    if(AnalyticsInfo.VersionInfo.DeviceFamily == "Windows.Xbox")
    {
        this.FocusVisualKind = FocusVisualKind.Reveal;
    }
```

Nach dem Festlegen der Eigenschaft **FocusVisualKind** wendet des Systems automatisch Reveal-Focus auf alle Steuerelemente, deren [UseSystemFocusVisuals](/uwp/api/Windows.UI.Xaml.Controls.Control.UseSystemFocusVisuals) -Eigenschaft auf **"true"** (der Standardwert für die meisten Steuerelemente) festgelegt ist. 

## <a name="why-isnt-reveal-focus-on-by-default"></a>Warum ist Reveal-Focus auf standardmäßig nicht? 
Wie Sie sehen können, ist es relativ einfach, Reveal-Focus zu aktivieren, wenn die app erkennt, dass sie auf einer Xbox ausgeführt wird. Warum aktiviert das System die Funktion nicht einfach automatisch? Reveal-Focus des visuellen Fokus erhöht, wodurch Probleme mit dem UI-Layout entstehen können. In einigen Fällen möchten Sie anpassen, die Reveal-Focus auf Wunsch für Ihre app zu optimieren.

## <a name="customizing-reveal-focus"></a>Anpassen von Reveal-Focus

Durch Ändern der Eigenschaften der visuellen Fokuselemente für jedes Steuerelement können Sie die Reveal-Focus auf Wunsch anpassen: [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness), [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness), [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush)und [ FocusVisualSecondaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush). Dank dieser Eigenschaften können Sie die Farbe und Breite des Fokusrechtecks anpassen. (Dies sind die gleichen Eigenschaften, die Sie zum Erstellen der [Fokuselemente mit hoher Sichtbarkeit](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#high-visibility-focus-visuals) verwenden.) 

Bevor Sie mit dem Anpassen beginnen, es ist hilfreich, etwas mehr über die Komponenten kennen, die Reveal-Focus bilden.

Es gibt drei Teile für den standardmäßigen Reveal-fokuselementen: der primäre und der sekundäre Rahmen sowie Reveal-glow. Der primäre Rahmen ist **2Pixel** breit und verläuft an der *Außenseite* des sekundären Rahmens. Der sekundäre Rahmen ist **1Pixel** breit und verläuft an der *Innenseite* des primären Rahmens. Der Reveal-Focus-Glanz hat eine Breite, die proportional zur Stärke des primären Rahmens ist und leuchtet um die *außerhalb* des primären Rahmens.

Zusätzlich zu den statischen Elementen feature Reveal-Focus-Visuals ein animiertes Licht, das bei Stillstand pulsiert und bewegt sich in Richtung des Fokus bewegt, wenn.

![Revel-Focus](images/reveal-breakdown.svg)

## <a name="customize-the-border-thickness"></a>Anpassen der Stärke des Rahmens

Verwenden Sie diese Eigenschaften, um die Breite der Rahmentypen eines Steuerelements zu ändern:

| Rahmentyp | Eigenschaft |
| --- | --- |
| Primär, Schein   | [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness)<br/> (Das Ändern des primären Rahmens ändert die Breite des Scheins proportional.)   |
| Sekundärer   | [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness)   |


In diesem Beispiel wird die Breite des Rahmens des visuellen Fokus für eine Schaltfläche geändert:

```xaml
<Button FocusVisualPrimaryThickness="2" FocusVisualSecondaryThickness="1"/>
```

## <a name="customize-the-margin"></a>Anpassen des Rands

Der Rand ist der Abstand zwischen den visuellen Grenzen des Steuerelements und dem Beginn des sekundären Rahmens der visuellen Fokuselemente. Der standardmäßige Rand hat eine Breite von 1Pixel außerhalb der Grenzen des Steuerelements. Sie können diesen Rand pro Steuerelement bearbeiten, indem Sie die Eigenschaft [FocusVisualMargin](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualMargin) ändern:

```xaml
<Button FocusVisualPrimaryThickness="2" FocusVisualSecondaryThickness="1" FocusVisualMargin="-3"/>
```

Ein negativer Rand verschiebt den Rahmen weiter weg von der Mitte des Steuerelements. Ein positiver Rand verschiebt den Rahmen näher zur Mitte des Steuerelements.

## <a name="customize-the-color"></a>Anpassen der Farbe

Um die Farbe von Reveal-Focus zu ändern, verwenden Sie die Eigenschaften [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) und [FocusVisualSecondaryBrush](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush) .

| Eigenschaft | Standardressource | Standardressourcewert |
| ---- | ---- | --- | 
| [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) | SystemControlRevealFocusVisualBrush  | SystemAccentColor |
| [FocusVisualSecondaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush)  | SystemControlFocusVisualSecondaryBrush  | SystemAltMediumColor |

(Die Eigenschaft des FocusPrimaryBrush wird standardmäßig als **SystemControlRevealFocusVisualBrush**-Ressourcen verwendet, wenn **FocusVisualKind** auf **Einblenden ** festgelegt ist. Andernfalls wird **SystemControlFocusVisualPrimaryBrush** verwendet.)


Um die Farbe des visuellen Fokus eines einzelnen Steuerelements zu ändern, legen Sie die Eigenschaften direkt im Steuerelement fest. In diesem Beispiel wird die Farbe der Fokusanzeige einer Schaltfläche außer Kraft gesetzt.

```xaml

<!-- Specifying a color directly -->
<Button
    FocusVisualPrimaryBrush="DarkRed"
    FocusVisualSecondaryBrush="Pink"/>

<!-- Using theme resources -->
<Button
    FocusVisualPrimaryBrush="{ThemeResource SystemBaseHighColor}"
    FocusVisualSecondaryBrush="{ThemeResource SystemAccentColor}"/>    
```

Um die Farbe aller Fokusanzeigen in der gesamten App zu ändern, setzen Sie die Ressourcen **SystemControlRevealFocusVisualBrush** und **SystemControlFocusVisualSecondaryBrush** mit Ihrer eigenen Definition außer Kraft:

```xaml
<!-- App.xaml -->
<Application.Resources>

    <!-- Override Reveal Focus default resources. -->
    <SolidColorBrush x:Key="SystemControlRevealFocusVisualBrush" Color="{ThemeResource SystemBaseHighColor}"/>
    <SolidColorBrush x:Key="SystemControlFocusVisualSecondaryBrush" Color="{ThemeResource SystemAccentColor}"/>
</Application.Resources>
```

Weitere Informationen zum Ändern der Farbe der Fokusanzeige finden Sie unter [Farbbranding und -anpassung](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#color-branding--customizing).


## <a name="show-just-the-glow"></a>Nur den Schein anzeigen

Wenn Sie nur den Schein ohne die primäre oder sekundäre Fokusanzeige verwenden möchten, legen Sie einfach die Eigenschaften des Steuerelements [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) `Transparent`und [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness) auf `0` fest. In diesem Fall übernimmt der Schein die Farbe des Hintergrunds des Steuerelements für ein randlos Verhalten. Sie können die Breite des Scheins mit [FocusVisualPrimaryThickness ](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness) ändern.

```xaml

<!-- Show just the glow -->
<Button
    FocusVisualPrimaryBrush="Transparent"
    FocusVisualSecondaryThickness="0" />    
```


## <a name="use-your-own-focus-visuals"></a>Verwenden Sie Ihre eigenen visuellen Fokuselemente

Eine weitere Möglichkeit zum Anpassen von Reveal-Focus ist, können die System-Fokusanzeigen deaktivieren, indem Sie eigene visuelle Zustände verwenden. Weitere Informationen finden Sie unter [Beispiel für visuelle Fokuselemente](http://go.microsoft.com/fwlink/p/?LinkID=619895).


## <a name="reveal-focus-and-the-fluent-design-system"></a>Reveal-Focus und das Fluent Design-System

Reveal-Focus ist eine Komponente des Fluent Design-Systems, die Lichteffekte in Ihrer app ermöglicht. Weitere Informationen zum Fluent Design-Systems und den zugehörigen Komponenten finden Sie unter [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).

## <a name="related-articles"></a>Verwandte Artikel

- [Reveal-Highlight](https://docs.microsoft.com/windows/uwp/design/style/reveal)
- [Entwerfen für Xbox und Fernsehgeräte](/windows/uwp/design/devices/designing-for-tv)
- [Interaktionen von Gamepad und Fernbedienung](https://docs.microsoft.com/windows/uwp/design/input/gamepad-and-remote-interactions)
- [Beispiel für visuelle Fokuselemente](http://go.microsoft.com/fwlink/p/?LinkID=619895)
- [Kompositionseffekte](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
- [Wissenschaft im System: Fluent Design und Tiefe](https://medium.com/microsoft-design/science-in-the-system-fluent-design-and-depth-fb6d0f23a53f)
- [Wissenschaft im System: Fluent Design und Licht](https://medium.com/microsoft-design/the-science-in-the-system-fluent-design-and-light-94a17e0b3a4f)
