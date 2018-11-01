---
author: Jwmsft
Description: Use a tooltip to reveal more info about a control before asking the user to perform an action.
title: QuickInfos
ms.assetid: A21BB12B-301E-40C9-B84B-C055FD43D307
label: Tooltips
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: stpete
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 87001cb99a7d5cb1a150bceed3f6c9ba187caa94
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5883746"
---
# <a name="tooltips"></a>QuickInfos

Eine QuickInfo ist eine kurze Beschreibung, die mit einem anderen Steuerelement oder Objekt verknüpft ist. QuickInfos erläutern Benutzern unbekannte Objekte, die in der Benutzeroberfläche nicht direkt beschrieben werden. Sie wird automatisch angezeigt, wenn der Benutzer den Fokus auf ein Steuerelement verschiebt, es gedrückt hält oder mit dem Mauszeiger darauf zeigt. Sie wird nach einigen Sekunden wieder ausgeblendet, wenn der Benutzer den Finger, den Mauszeiger oder den Tastatur-/Gamepad-Fokus bewegt.

![Eine QuickInfo](images/controls/tool-tip.png)

> **Wichtige APIs**: [ToolTip-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ToolTip), [ToolTipService-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.tooltipservice)

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Verwenden Sie eine QuickInfo, damit der Benutzer weitere Informationen über ein Steuerelement erhält, bevor er zum Ausführen einer Aktion aufgefordert wird. QuickInfo-Steuerelemente sollten sparsam verwendet werden, vor allem nur dann, wenn sie für Benutzer, die eine bestimmte Aufgabe ausführen möchten, wirklich nützlich sind. Es gilt folgende Faustregel: Für Informationen, die bereits an einer anderen Stelle derselben Benutzeroberfläche vermittelt werden, benötigen Sie keine QuickInfo. Eine nützliche QuickInfo bietet klärende Informationen zu einer unklaren Aktion.

Wann sollten Sie eine QuickInfo verwenden? Orientieren Sie sich an folgenden Fragen:

- **Sollen die Informationen beim Daraufzeigen sichtbar werden?**
    Wenn dies nicht erwünscht ist, verwenden Sie ein anderes Steuerelement. QuickInfos sollte niemals ohne vorhergehende Aktion angezeigt werden, sondern immer als Ergebnis einer Benutzerinteraktion.

- **Ist das Steuerelement mit Text beschriftet?**
    Wenn dies nicht der Fall ist, fügen Sie die Beschriftung als QuickInfo hinzu. Beim UX-Entwurf empfiehlt es sich, die meisten Steuerelemente inline zu beschriften, sodass QuickInfos dafür nicht erforderlich sind. Steuerelemente in Symbolleisten sowie nur Symbole zeignde Befehlsschaltflächen müssen dagegen mit QuickInfos versehen werden.

- **Wären eine Beschreibung oder zusätzliche Informationen zu einem Objekt hilfreich?**
    Verwenden Sie in diesem Fall eine QuickInfo. Der Text ist aber nur als Ergänzung gedacht – wichtige Informationen für die Hauptaufgaben dürfen nicht nur als QuickInfo vorhanden sein. Fügen Sie wichtige Informationen direkt in die Benutzeroberfläche ein, damit Benutzer nicht erst danach suchen müssen.

- **Handelt es sich bei den ergänzenden Informationen um Fehler-, Warn- oder Statusmeldungen?**
    Verwenden Sie in diesem Fall ein anderes Benutzeroberflächenelement, beispielsweise ein Flyout.

- **Müssen die Benutzer mit den Informationen interagieren?**
    Verwenden Sie in diesem Fall ein anderes Steuerelement. Eine Benutzerinteraktion mit QuickInfo ist nicht möglich, da die Informationen beim Bewegen der Maus ausgeblendet werden.

- **Müssen die Benutzer die ergänzenden Informationen drucken?**
    Verwenden Sie in diesem Fall ein anderes Steuerelement.

- **Ist anzunehmen, dass sich die Benutzer durch QuickInfo gestört oder abgelenkt fühlen?**
    Ziehen Sie in diesem Fall eine andere Lösung in Betracht. Möglicherweise können Sie ganz auf die zusätzlichen Informationen verzichten. Wenn Sie QuickInfos verwenden, obwohl dies die Benutzer möglicherweise irritiert, geben Sie den Benutzern die Möglichkeit, die QuickInfos zu deaktivieren.

## <a name="example"></a>Beispiel

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/ToolTip">die App zu öffnen und ToolTip in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

Eine QuickInfo in der App „Bing Karten”.

![Eine QuickInfo in der App „Bing Karten”](images/control-examples/tool-tip-maps.png)

## <a name="create-a-tooltip"></a>Erstellen einer QuickInfo

Eine [QuickInfo](/uwp/api/Windows.UI.Xaml.Controls.ToolTip) muss einem anderen Benutzeroberflächenelement zugewiesen werden, das deren Eigentümer ist. Die [ToolTipService](/uwp/api/windows.ui.xaml.controls.tooltipservice)-Klasse bietet statische Methoden zum Anzeigen einer QuickInfo.

Verwenden Sie in XAML die angefügte **ToolTipService.Tooltip**-Eigenschaft, um die QuickInfo einem Eigentümer zuzuweisen.

```xaml
<Button Content="Submit" ToolTipService.ToolTip="Click to submit"/>
```

Verwenden Sie im Code die Methode [ToolTipService.SetToolTip](/uwp/api/windows.ui.xaml.controls.tooltipservice.settooltip), um die QuickInfo einem Eigentümer zuzuweisen.

```xaml
<Button x:Name="submitButton" Content="Submit"/>
```

```csharp
ToolTip toolTip = new ToolTip();
toolTip.Content = "Click to submit";
ToolTipService.SetToolTip(submitButton, toolTip);
```

### <a name="content"></a>Inhalt

Sie können jedes beliebige Objekt als [Inhalt](/uwp/api/windows.ui.xaml.controls.contentcontrol.content) einer QuickInfo verwenden. Hier ist ein Beispiel für die Verwendung eines [Bilds](/uwp/api/windows.ui.xaml.controls.image) in einer QuickInfo.

```xaml
<TextBlock Text="store logo">
    <ToolTipService.ToolTip>
        <Image Source="Assets/StoreLogo.png"/>
    </ToolTipService.ToolTip>
</TextBlock>
```

### <a name="placement"></a>Platzierung

Standardmäßig wird eine QuickInfo über dem Zeiger zentriert angezeigt. Die Platzierung wird nicht durch das App-Fenster eingeschränkt, sodass die QuickInfo möglicherweise teilweise oder komplett außerhalb der Grenzen des App-Fensters angezeigt wird.

Verwenden Sie für allgemeine Anpassungen das [Placement](/uwp/api/windows.ui.xaml.controls.tooltip.placement) -Eigenschaft oder die **ToolTipService.Placement** angefügte Eigenschaft angeben, ob die QuickInfo oben, unten, links oder rechts neben dem Zeiger gezeichnet werden soll. Sie können die [VerticalOffset](/uwp/api/windows.ui.xaml.controls.tooltip.verticaloffset) oder [HorizontalOffset](/uwp/api/windows.ui.xaml.controls.tooltip.horizontaloffset) Eigenschaften so ändern Sie den Abstand zwischen dem Zeiger und der QuickInfo festlegen. Nur eine der beiden Werte zwei versetzt wird die endgültige Position - VerticalOffset beim Platzierung oben oder unten, HorizontalOffset ist, wenn Platzierung gelassen wird oder rechts beeinflussen.

```xaml
<!-- An Image with an offset ToolTip. -->
<Image Source="Assets/StoreLogo.png">
    <ToolTipService.ToolTip>
        <ToolTip Content="Offset ToolTip."
                 Placement="Right"
                 HorizontalOffset="20"/>
    </ToolTipService.ToolTip>
</Image>
```

Wenn eine QuickInfo die Inhalte, die, der Sie verdeckt sich bezieht, können Sie mit der neuen **PlacementRect** -Eigenschaft genau-Kontext anpassen. PlacementRect verankert des QuickInfo Position und dient auch als ein Bereich, den QuickInfo nicht verdeckt wird, sofern genügend Bildschirmfläche zum Zeichnen der QuickInfo außerhalb dieses Bereichs vorhanden ist. Sie können den Ursprung des Rechtecks relativ zu der QuickInfo-Besitzer und die Höhe und Breite der Ausschluss angeben. Die [Placement](/uwp/api/windows.ui.xaml.controls.tooltip.placement) -Eigenschaft definiert, ob QuickInfo oben, unten, links oder rechts neben dem PlacementRect gezeichnet werden soll. 

```xaml
<!-- An Image with a non-occluding ToolTip. -->
<Image Source="Assets/StoreLogo.png" Height="64" Width="96">
    <ToolTipService.ToolTip>
        <ToolTip Content="Non-occluding ToolTip."
                 PlacementRect="0,0,96,64"/>
    </ToolTipService.ToolTip>
</Image>
```

## <a name="recommendations"></a>Empfehlungen

- Verwenden Sie QuickInfos sparsam (oder gar nicht). QuickInfos stellen eine Unterbrechung dar. Eine QuickInfo kann genauso ablenkend wirken wie ein Popup. Verwenden Sie sie daher nur, wenn sie wirklich von Bedeutung sind.
- Halten Sie den QuickInfo-Text kurz. QuickInfos eignen sich gut für kurze Sätze und Satzfragmente. Längere Textblöcke können überfrachtet wirken, sodass ein Timeout für die QuickInfo auftritt, bevor der Benutzer sie zu Ende gelesen hat.
- Erstellen Sie hilfreiche QuickInfo-Texte mit ergänzenden Informationen. Der QuickInfo-Text muss informativ sein. Verwenden Sie keine selbstverständlichen oder bereits auf dem Bildschirm vorhandenen Informationen als QuickInfo-Text. Da der QuickInfo-Text nicht immer angezeigt wird, sollte er nur ergänzende Informationen enthalten, die nicht unbedingt gelesen werden müssen. Teilen Sie wichtige Informationen in Form von selbsterklärenden Beschriftungen für Steuerelemente oder direkt eingefügtem ergänzendem Text mit.
- Verwenden Sie ggf. Bilder als QuickInfo. Manchmal ist ein Bild aussagekräftiger als Text. Wenn der Benutzer z.B. auf einen Hyperlink zeigt, können Sie als QuickInfo eine Vorschau der verknüpften Seite anzeigen.
- Verwenden Sie die QuickInfo nicht, um bereits in der UI vorhandene Informationen anzuzeigen. Versehen Sie z.B. keine Schaltfläche mit QuickInfo-Text, der bereits auf der Schaltfläche selbst angezeigt wird.
- Fügen Sie in QuickInfos keine interaktiven Steuerelemente ein.
- Fügen Sie in QuickInfos keine Bilder ein, die wie interaktive Steuerelemente aussehen.

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.

## <a name="related-articles"></a>Verwandte Artikel

- [QuickInfo-Klasse](https://msdn.microsoft.com/library/windows/apps/br227608)
