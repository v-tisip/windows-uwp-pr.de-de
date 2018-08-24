---
author: cphilippona
description: Anzuzeigen Sie, dass Fokus einen Beleuchtungseffekt ist, der den Rahmen des Fokus Elemente animiert, wenn der Benutzer auf diese Gamepad noch die Tastatur-Fokus bewegt.
title: Fokus anzeigen
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
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2839592"
---
# <a name="reveal-focus"></a>Fokus anzeigen

![Favoritenbild](images/header-reveal-focus.svg)

Anzuzeigen Sie, dass der Fokus für [10 Fuß auftritt](/windows/uwp/design/devices/designing-for-tv), wie eine Xbox und verbringt Bildschirme einen Beleuchtungseffekt ist. Sie animieren den Rahmen des fokussierbaren Elementes wie beispielsweise Schaltflächen, wenn der Benutzer den Fokus des Gamepad oder der Tastatur darauf lenken. Es ist standardmäßig deaktiviert, lässt sich allerdings ganz einfach aktivieren. 

(Für den Effekt markieren anzuzeigen, eine interaktive Elemente hervorgehoben Wirkung der Beleuchtung finden Sie im [Artikel markieren anzuzeigen](/windows/uwp/design/style/reveal).)


> **Wichtige APIs**: [Application.FocusVisualKind-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.FocusVisualKind), [FocusVisualKind Enum](https://docs.microsoft.com/uwp/api/windows.ui.xaml.focusvisualkind), [Control.UseSystemFocusVisuals-Eigenschaft](/uwp/api/Windows.UI.Xaml.Controls.Control.UseSystemFocusVisuals)

## <a name="how-it-works"></a>Funktionsweise
Anzeigen Sie Anrufe Aufmerksamkeit auf zielgerichteten Elemente durch eine animierte Leuchteffekt um das Element Umrandung hinzufügen:

![Einblendeanzeige](images/traveling-focus-fullscreen-light-rf.gif)

Dies ist insbesondere dann nützlich, in 10 Fuß Szenarien, in dem der Benutzer nicht vollständige Aufmerksamkeit auf den ganzen Bildschirm TV bezahlt werden kann. 

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die <strong style="font-weight: semi-bold">Verwendung von XAML-Steuerelemente-Sammlung</strong> app installiert haben, klicken Sie hier, <a href="xamlcontrolsgallery:/item/RevealFocus">Öffnen Sie die app</a>und finden Sie unter Fokus in der Praxis anzuzeigen.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="how-to-use-it"></a>Verwendung

Anzuzeigen Sie, dass Fokus standardmäßig deaktiviert ist. So aktivieren Sie es:
1. Rufen Sie im Konstruktor der App die Eigenschaft [AnalyticsInfo.VersionInfo.DeviceFamily](/uwp/api/windows.system.profile.analyticsversioninfo.DeviceFamily) auf, und überprüfen Sie, ob die aktuellen Gerätefamilie `Windows.Xbox` ist.
2. Wenn die Gerätefamilie `Windows.Xbox` ist, legen Sie die Eigenschaft [Application.FocusVisualKind](/uwp/api/windows.ui.xaml.application.FocusVisualKind) auf `FocusVisualKind.Reveal` fest. 

```csharp
    if(AnalyticsInfo.VersionInfo.DeviceFamily == "Windows.Xbox")
    {
        this.FocusVisualKind = FocusVisualKind.Reveal;
    }
```

Nachdem Sie die **FocusVisualKind** -Eigenschaft festgelegt wird, wendet das System den Fokus anzeigen Effekt automatisch für alle Steuerelemente, deren [UseSystemFocusVisuals](/uwp/api/Windows.UI.Xaml.Controls.Control.UseSystemFocusVisuals) -Eigenschaft auf **True** (Standardwert für die meisten Steuerelemente) festgelegt ist. 

## <a name="why-isnt-reveal-focus-on-by-default"></a>Warum erfolgt keine anzeigen den Fokus auf standardmäßig ein? 
Wie Sie sehen können, ist es ganz leicht, die Fokus anzeigen aktivieren, wenn die app erkennt, dass er auf eine Xbox ausgeführt wird. Warum aktiviert das System die Funktion nicht einfach automatisch? Da Fokus anzeigen den Fokus visual vergrößert, möglicherweise die Probleme mit Layout der Benutzeroberfläche. In einigen Fällen sollten Sie zum Anpassen des Effekt Fokus anzuzeigen, um für Ihre app zu optimieren.

## <a name="customizing-reveal-focus"></a>Anpassen der Reveal-Fokus

Sie können durch Ändern der Fokus visuellen Eigenschaften für jedes Steuerelement den Fokus anzeigen Effekt anpassen: [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness), [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness), [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush)und [ FocusVisualSecondaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush). Dank dieser Eigenschaften können Sie die Farbe und Breite des Fokusrechtecks anpassen. (Dies sind die gleichen Eigenschaften, die Sie zum Erstellen der [Fokuselemente mit hoher Sichtbarkeit](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#high-visibility-focus-visuals) verwenden.) 

Aber bevor Sie anpassen beginnen, es ist hilfreich, Weitere Informationen zu den Komponenten kennen, die Fokus anzeigen bilden.

Es gibt drei Teile auf die Standard-Fokus anzeigen visuelle Objekte: der primäre Rahmen, den sekundären Rahmen und der Reveal leuchten. Der primäre Rahmen ist **2Pixel** breit und verläuft an der *Außenseite* des sekundären Rahmens. Der sekundäre Rahmen ist **1Pixel** breit und verläuft an der *Innenseite* des primären Rahmens. Der Leuchteffekt anzeigen den Fokus hat eine Stärke proportional zum die Stärke des Rahmens primäre und ausgeführt wird, um die *außerhalb* des primären Rahmens.

Zusätzlich zu den statischen Elemente feature Fokus anzeigen visuelle Objekte eine animierte Licht, die zur Fußstützen pulsates und beim Verschieben den Fokus in Richtung der Fokus wechselt.

![Fokus Ebenen anzuzeigen](images/reveal-breakdown.svg)

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

Verwenden Sie Farbe für den Fokus anzeigen visual zum Ändern die Eigenschaften [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) und [FocusVisualSecondaryBrush](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush) .

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

Eine andere Möglichkeit zum Anpassen der Fokus anzuzeigen ist nicht genügend visuelle Struktur der vom System bereitgestellten Fokus durch Ihre eigene visuelle Zustände mit Zeichnen zu abonnieren. Weitere Informationen finden Sie unter [Beispiel für visuelle Fokuselemente](http://go.microsoft.com/fwlink/p/?LinkID=619895).


## <a name="reveal-focus-and-the-fluent-design-system"></a>Anzeigen der Fokus und die Fluent-Design-System

Anzuzeigen Sie, dass Fokus Fluent Design Systemkomponente ist, die Ihre app Light hinzufügt. Weitere Informationen zum Fluent Design-Systems und den zugehörigen Komponenten finden Sie unter [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).

## <a name="related-articles"></a>Verwandte Artikel

- [Anzeigen der Hervorhebung](https://docs.microsoft.com/windows/uwp/design/style/reveal)
- [Entwerfen für Xbox und Fernsehgeräte](/windows/uwp/design/devices/designing-for-tv)
- [Interaktionen von Gamepad und Fernbedienung](https://docs.microsoft.com/windows/uwp/design/input/gamepad-and-remote-interactions)
- [Beispiel für visuelle Fokuselemente](http://go.microsoft.com/fwlink/p/?LinkID=619895)
- [Kompositionseffekte](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
- [Wissenschaft im System: Fluent Design und Tiefe](https://medium.com/microsoft-design/science-in-the-system-fluent-design-and-depth-fb6d0f23a53f)
- [Wissenschaft im System: Fluent Design und Licht](https://medium.com/microsoft-design/the-science-in-the-system-fluent-design-and-light-94a17e0b3a4f)
