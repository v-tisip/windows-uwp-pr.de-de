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
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: stpete
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 5a61b8bdcfcfad490528cdceed5e732a6f5f3a89
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4752229"
---
# <a name="tooltips"></a><span data-ttu-id="36ec6-103">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="36ec6-103">Tooltips</span></span>

<span data-ttu-id="36ec6-104">Eine QuickInfo ist eine kurze Beschreibung, die mit einem anderen Steuerelement oder Objekt verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="36ec6-104">A tooltip is a short description that is linked to another control or object.</span></span> <span data-ttu-id="36ec6-105">QuickInfos erläutern Benutzern unbekannte Objekte, die in der Benutzeroberfläche nicht direkt beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="36ec6-105">Tooltips help users understand unfamiliar objects that aren't described directly in the UI.</span></span> <span data-ttu-id="36ec6-106">Sie wird automatisch angezeigt, wenn der Benutzer den Fokus auf ein Steuerelement verschiebt, es gedrückt hält oder mit dem Mauszeiger darauf zeigt.</span><span class="sxs-lookup"><span data-stu-id="36ec6-106">They display automatically when the user moves focus to, presses and holds, or hovers the mouse pointer over a control.</span></span> <span data-ttu-id="36ec6-107">Sie wird nach einigen Sekunden wieder ausgeblendet, wenn der Benutzer den Finger, den Mauszeiger oder den Tastatur-/Gamepad-Fokus bewegt.</span><span class="sxs-lookup"><span data-stu-id="36ec6-107">The tooltip disappears after a few seconds, or when the user moves the finger, pointer or keyboard/gamepad focus.</span></span>

![Eine QuickInfo](images/controls/tool-tip.png)

> <span data-ttu-id="36ec6-109">**Wichtige APIs**: [ToolTip-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ToolTip), [ToolTipService-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.tooltipservice)</span><span class="sxs-lookup"><span data-stu-id="36ec6-109">**Important APIs**: [ToolTip class](/uwp/api/Windows.UI.Xaml.Controls.ToolTip), [ToolTipService class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.tooltipservice)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="36ec6-110">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="36ec6-110">Is this the right control?</span></span>

<span data-ttu-id="36ec6-111">Verwenden Sie eine QuickInfo, damit der Benutzer weitere Informationen über ein Steuerelement erhält, bevor er zum Ausführen einer Aktion aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="36ec6-111">Use a tooltip to reveal more info about a control before asking the user to perform an action.</span></span> <span data-ttu-id="36ec6-112">QuickInfo-Steuerelemente sollten sparsam verwendet werden, vor allem nur dann, wenn sie für Benutzer, die eine bestimmte Aufgabe ausführen möchten, wirklich nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="36ec6-112">Tooltips should be used sparingly, and only when they are adding distinct value for the user who is trying to complete a task.</span></span> <span data-ttu-id="36ec6-113">Es gilt folgende Faustregel: Für Informationen, die bereits an einer anderen Stelle derselben Benutzeroberfläche vermittelt werden, benötigen Sie keine QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="36ec6-113">One rule of thumb is that if the information is available elsewhere in the same experience, you do not need a tooltip.</span></span> <span data-ttu-id="36ec6-114">Eine nützliche QuickInfo bietet klärende Informationen zu einer unklaren Aktion.</span><span class="sxs-lookup"><span data-stu-id="36ec6-114">A valuable tooltip will clarify an unclear action.</span></span>

<span data-ttu-id="36ec6-115">Wann sollten Sie eine QuickInfo verwenden?</span><span class="sxs-lookup"><span data-stu-id="36ec6-115">When should you use a tooltip?</span></span> <span data-ttu-id="36ec6-116">Orientieren Sie sich an folgenden Fragen:</span><span class="sxs-lookup"><span data-stu-id="36ec6-116">To decide, consider these questions:</span></span>

- **<span data-ttu-id="36ec6-117">Sollen die Informationen beim Daraufzeigen sichtbar werden?</span><span class="sxs-lookup"><span data-stu-id="36ec6-117">Should info become visible based on pointer hover?</span></span>**
    <span data-ttu-id="36ec6-118">Wenn dies nicht erwünscht ist, verwenden Sie ein anderes Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="36ec6-118">If not, use another control.</span></span> <span data-ttu-id="36ec6-119">QuickInfos sollte niemals ohne vorhergehende Aktion angezeigt werden, sondern immer als Ergebnis einer Benutzerinteraktion.</span><span class="sxs-lookup"><span data-stu-id="36ec6-119">Display tips only as the result of user interaction, never display them on their own.</span></span>

- **<span data-ttu-id="36ec6-120">Ist das Steuerelement mit Text beschriftet?</span><span class="sxs-lookup"><span data-stu-id="36ec6-120">Does a control have a text label?</span></span>**
    <span data-ttu-id="36ec6-121">Wenn dies nicht der Fall ist, fügen Sie die Beschriftung als QuickInfo hinzu.</span><span class="sxs-lookup"><span data-stu-id="36ec6-121">If not, use a tooltip to provide the label.</span></span> <span data-ttu-id="36ec6-122">Beim UX-Entwurf empfiehlt es sich, die meisten Steuerelemente inline zu beschriften, sodass QuickInfos dafür nicht erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="36ec6-122">It is a good UX design practice to label most controls inline and for these you don't need tooltips.</span></span> <span data-ttu-id="36ec6-123">Steuerelemente in Symbolleisten sowie nur Symbole zeignde Befehlsschaltflächen müssen dagegen mit QuickInfos versehen werden.</span><span class="sxs-lookup"><span data-stu-id="36ec6-123">Toolbar controls and command buttons showing only icons need tooltips.</span></span>

- **<span data-ttu-id="36ec6-124">Wären eine Beschreibung oder zusätzliche Informationen zu einem Objekt hilfreich?</span><span class="sxs-lookup"><span data-stu-id="36ec6-124">Does an object benefit from a description or further info?</span></span>**
    <span data-ttu-id="36ec6-125">Verwenden Sie in diesem Fall eine QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="36ec6-125">If so, use a tooltip.</span></span> <span data-ttu-id="36ec6-126">Der Text ist aber nur als Ergänzung gedacht – wichtige Informationen für die Hauptaufgaben dürfen nicht nur als QuickInfo vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="36ec6-126">But the text must be supplemental — that is, not essential to the primary tasks.</span></span> <span data-ttu-id="36ec6-127">Fügen Sie wichtige Informationen direkt in die Benutzeroberfläche ein, damit Benutzer nicht erst danach suchen müssen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-127">If it is essential, put it directly in the UI so that users don't have to discover or hunt for it.</span></span>

- **<span data-ttu-id="36ec6-128">Handelt es sich bei den ergänzenden Informationen um Fehler-, Warn- oder Statusmeldungen?</span><span class="sxs-lookup"><span data-stu-id="36ec6-128">Is the supplemental info an error, warning, or status?</span></span>**
    <span data-ttu-id="36ec6-129">Verwenden Sie in diesem Fall ein anderes Benutzeroberflächenelement, beispielsweise ein Flyout.</span><span class="sxs-lookup"><span data-stu-id="36ec6-129">If so, use another UI element, such as a flyout.</span></span>

- **<span data-ttu-id="36ec6-130">Müssen die Benutzer mit den Informationen interagieren?</span><span class="sxs-lookup"><span data-stu-id="36ec6-130">Do users need to interact with the tip?</span></span>**
    <span data-ttu-id="36ec6-131">Verwenden Sie in diesem Fall ein anderes Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="36ec6-131">If so, use another control.</span></span> <span data-ttu-id="36ec6-132">Eine Benutzerinteraktion mit QuickInfo ist nicht möglich, da die Informationen beim Bewegen der Maus ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="36ec6-132">Users can't interact with tips because moving the mouse makes them disappear.</span></span>

- **<span data-ttu-id="36ec6-133">Müssen die Benutzer die ergänzenden Informationen drucken?</span><span class="sxs-lookup"><span data-stu-id="36ec6-133">Do users need to print the supplemental info?</span></span>**
    <span data-ttu-id="36ec6-134">Verwenden Sie in diesem Fall ein anderes Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="36ec6-134">If so, use another control.</span></span>

- **<span data-ttu-id="36ec6-135">Ist anzunehmen, dass sich die Benutzer durch QuickInfo gestört oder abgelenkt fühlen?</span><span class="sxs-lookup"><span data-stu-id="36ec6-135">Will users find the tips annoying or distracting?</span></span>**
    <span data-ttu-id="36ec6-136">Ziehen Sie in diesem Fall eine andere Lösung in Betracht. Möglicherweise können Sie ganz auf die zusätzlichen Informationen verzichten.</span><span class="sxs-lookup"><span data-stu-id="36ec6-136">If so, consider using another solution — including doing nothing at all.</span></span> <span data-ttu-id="36ec6-137">Wenn Sie QuickInfos verwenden, obwohl dies die Benutzer möglicherweise irritiert, geben Sie den Benutzern die Möglichkeit, die QuickInfos zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="36ec6-137">If you do use tips where they might be distracting, allow users to turn them off.</span></span>

## <a name="example"></a><span data-ttu-id="36ec6-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="36ec6-138">Example</span></span>

<table>
<th align="left"><span data-ttu-id="36ec6-139">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="36ec6-139">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="36ec6-140">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/ToolTip">die App zu öffnen und ToolTip in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="36ec6-140">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/ToolTip">open the app and see the ToolTip in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="36ec6-141">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="36ec6-141">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="36ec6-142">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="36ec6-142">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="36ec6-143">Eine QuickInfo in der App „Bing Karten”.</span><span class="sxs-lookup"><span data-stu-id="36ec6-143">A tooltip in the Bing Maps app.</span></span>

![Eine QuickInfo in der App „Bing Karten”](images/control-examples/tool-tip-maps.png)

## <a name="create-a-tooltip"></a><span data-ttu-id="36ec6-145">Erstellen einer QuickInfo</span><span class="sxs-lookup"><span data-stu-id="36ec6-145">Create a tooltip</span></span>

<span data-ttu-id="36ec6-146">Eine [QuickInfo](/uwp/api/Windows.UI.Xaml.Controls.ToolTip) muss einem anderen Benutzeroberflächenelement zugewiesen werden, das deren Eigentümer ist.</span><span class="sxs-lookup"><span data-stu-id="36ec6-146">A [ToolTip](/uwp/api/Windows.UI.Xaml.Controls.ToolTip) must be assigned to another UI element that is its owner.</span></span> <span data-ttu-id="36ec6-147">Die [ToolTipService](/uwp/api/windows.ui.xaml.controls.tooltipservice)-Klasse bietet statische Methoden zum Anzeigen einer QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="36ec6-147">The [ToolTipService](/uwp/api/windows.ui.xaml.controls.tooltipservice) class provides static methods to display a ToolTip.</span></span>

<span data-ttu-id="36ec6-148">Verwenden Sie in XAML die angefügte **ToolTipService.Tooltip**-Eigenschaft, um die QuickInfo einem Eigentümer zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-148">In XAML, use the **ToolTipService.Tooltip** attached property to assign the ToolTip to an owner.</span></span>

```xaml
<Button Content="Submit" ToolTipService.ToolTip="Click to submit"/>
```

<span data-ttu-id="36ec6-149">Verwenden Sie im Code die Methode [ToolTipService.SetToolTip](/uwp/api/windows.ui.xaml.controls.tooltipservice.settooltip), um die QuickInfo einem Eigentümer zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-149">In code, use the [ToolTipService.SetToolTip](/uwp/api/windows.ui.xaml.controls.tooltipservice.settooltip) method to assign the ToolTip to an owner.</span></span>

```xaml
<Button x:Name="submitButton" Content="Submit"/>
```

```csharp
ToolTip toolTip = new ToolTip();
toolTip.Content = "Click to submit";
ToolTipService.SetToolTip(submitButton, toolTip);
```

### <a name="content"></a><span data-ttu-id="36ec6-150">Inhalt</span><span class="sxs-lookup"><span data-stu-id="36ec6-150">Content</span></span>

<span data-ttu-id="36ec6-151">Sie können jedes beliebige Objekt als [Inhalt](/uwp/api/windows.ui.xaml.controls.contentcontrol.content) einer QuickInfo verwenden.</span><span class="sxs-lookup"><span data-stu-id="36ec6-151">You can use any object as the [Content](/uwp/api/windows.ui.xaml.controls.contentcontrol.content) of a ToolTip.</span></span> <span data-ttu-id="36ec6-152">Hier ist ein Beispiel für die Verwendung eines [Bilds](/uwp/api/windows.ui.xaml.controls.image) in einer QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="36ec6-152">Here's an example of using an [Image](/uwp/api/windows.ui.xaml.controls.image) in a ToolTip.</span></span>

```xaml
<TextBlock Text="store logo">
    <ToolTipService.ToolTip>
        <Image Source="Assets/StoreLogo.png"/>
    </ToolTipService.ToolTip>
</TextBlock>
```

### <a name="placement"></a><span data-ttu-id="36ec6-153">Platzierung</span><span class="sxs-lookup"><span data-stu-id="36ec6-153">Placement</span></span>

<span data-ttu-id="36ec6-154">Standardmäßig wird eine QuickInfo über dem Zeiger zentriert angezeigt.</span><span class="sxs-lookup"><span data-stu-id="36ec6-154">By default, a ToolTip is displayed centered above the pointer.</span></span> <span data-ttu-id="36ec6-155">Die Platzierung wird nicht durch das App-Fenster eingeschränkt, sodass die QuickInfo möglicherweise teilweise oder komplett außerhalb der Grenzen des App-Fensters angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="36ec6-155">The placement is not constrained by the app window, so the ToolTip might be displayed partially or completely outside of the app window bounds.</span></span>

<span data-ttu-id="36ec6-156">Verwenden Sie für allgemeine Anpassungen das [Placement](/uwp/api/windows.ui.xaml.controls.tooltip.placement) -Eigenschaft oder die **ToolTipService.Placement** angefügte Eigenschaft an, ob die QuickInfo oben, unten, links oder rechts neben dem Zeiger gezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-156">For broad adjustments, use the [Placement](/uwp/api/windows.ui.xaml.controls.tooltip.placement) property or **ToolTipService.Placement** attached property to specify whether the ToolTip should draw above, below, left, or right of the pointer.</span></span> <span data-ttu-id="36ec6-157">Sie können die [VerticalOffset](/uwp/api/windows.ui.xaml.controls.tooltip.verticaloffset) oder [HorizontalOffset](/uwp/api/windows.ui.xaml.controls.tooltip.horizontaloffset) Eigenschaften so ändern Sie den Abstand zwischen dem Zeiger und der QuickInfo festlegen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-157">You can set the [VerticalOffset](/uwp/api/windows.ui.xaml.controls.tooltip.verticaloffset) or [HorizontalOffset](/uwp/api/windows.ui.xaml.controls.tooltip.horizontaloffset) properties to change the distance between the pointer and the ToolTip.</span></span> <span data-ttu-id="36ec6-158">Nur eine der beiden Offset Werte beeinflusst die endgültige Position - VerticalOffset beim Platzierung wird oben oder unten, HorizontalOffset Platzierung übrig ist oder rechts.</span><span class="sxs-lookup"><span data-stu-id="36ec6-158">Only one of the two offset values will influence the final position - VerticalOffset when Placement is Top or Bottom, HorizontalOffset when Placement is Left or Right.</span></span>

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

<span data-ttu-id="36ec6-159">Wenn eine QuickInfo die Inhalte, die, der Sie verdeckt sich bezieht, können Sie seine Position mit der neuen **PlacementRect** -Eigenschaft genau anpassen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-159">If a ToolTip obscures the content it is referring to, you can adjust its placement precisely using the new **PlacementRect** property.</span></span> <span data-ttu-id="36ec6-160">PlacementRect verankert die QuickInfo Position und dient auch als ein Bereich, den QuickInfo nicht verdeckt wird, sofern genügend Bildschirmfläche zum Zeichnen der QuickInfo außerhalb dieses Bereichs vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="36ec6-160">PlacementRect anchors the ToolTip's position and also serves as an area that ToolTip will not occlude, provided there’s sufficient screen space to draw ToolTip outside this area.</span></span> <span data-ttu-id="36ec6-161">Sie können den Ursprung des Rechtecks relativ zu der QuickInfo-Besitzer und die Höhe und Breite der Ausschluss angeben.</span><span class="sxs-lookup"><span data-stu-id="36ec6-161">You can specify the origin of the rectangle relative to the ToolTip’s owner, and the height and width of the exclusion area.</span></span> <span data-ttu-id="36ec6-162">Die [Position](/uwp/api/windows.ui.xaml.controls.tooltip.placement) -Eigenschaft definiert, ob QuickInfo oben, unten, links oder rechts neben dem PlacementRect gezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-162">The [Placement](/uwp/api/windows.ui.xaml.controls.tooltip.placement) property will define if ToolTip should draw above, below, left, or right of the PlacementRect.</span></span> 

```xaml
<!-- An Image with a non-occluding ToolTip. -->
<Image Source="Assets/StoreLogo.png" Height="64" Width="96">
    <ToolTipService.ToolTip>
        <ToolTip Content="Non-occluding ToolTip."
                 PlacementRect="0,0,96,64"/>
    </ToolTipService.ToolTip>
</Image>
```

## <a name="recommendations"></a><span data-ttu-id="36ec6-163">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="36ec6-163">Recommendations</span></span>

- <span data-ttu-id="36ec6-164">Verwenden Sie QuickInfos sparsam (oder gar nicht).</span><span class="sxs-lookup"><span data-stu-id="36ec6-164">Use tooltips sparingly (or not at all).</span></span> <span data-ttu-id="36ec6-165">QuickInfos stellen eine Unterbrechung dar.</span><span class="sxs-lookup"><span data-stu-id="36ec6-165">Tooltips are an interruption.</span></span> <span data-ttu-id="36ec6-166">Eine QuickInfo kann genauso ablenkend wirken wie ein Popup. Verwenden Sie sie daher nur, wenn sie wirklich von Bedeutung sind.</span><span class="sxs-lookup"><span data-stu-id="36ec6-166">A tooltip can be as distracting as a pop-up, so don't use them unless they add significant value.</span></span>
- <span data-ttu-id="36ec6-167">Halten Sie den QuickInfo-Text kurz.</span><span class="sxs-lookup"><span data-stu-id="36ec6-167">Keep the tooltip text concise.</span></span> <span data-ttu-id="36ec6-168">QuickInfos eignen sich gut für kurze Sätze und Satzfragmente.</span><span class="sxs-lookup"><span data-stu-id="36ec6-168">Tooltips are perfect for short sentences and sentence fragments.</span></span> <span data-ttu-id="36ec6-169">Längere Textblöcke können überfrachtet wirken, sodass ein Timeout für die QuickInfo auftritt, bevor der Benutzer sie zu Ende gelesen hat.</span><span class="sxs-lookup"><span data-stu-id="36ec6-169">Large blocks of text can be overwhelming and the tooltip may time out before the user has finished reading.</span></span>
- <span data-ttu-id="36ec6-170">Erstellen Sie hilfreiche QuickInfo-Texte mit ergänzenden Informationen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-170">Create helpful, supplemental tooltip text.</span></span> <span data-ttu-id="36ec6-171">Der QuickInfo-Text muss informativ sein.</span><span class="sxs-lookup"><span data-stu-id="36ec6-171">Tooltip text must be informative.</span></span> <span data-ttu-id="36ec6-172">Verwenden Sie keine selbstverständlichen oder bereits auf dem Bildschirm vorhandenen Informationen als QuickInfo-Text.</span><span class="sxs-lookup"><span data-stu-id="36ec6-172">Don't make it obvious or just repeat what is already on the screen.</span></span> <span data-ttu-id="36ec6-173">Da der QuickInfo-Text nicht immer angezeigt wird, sollte er nur ergänzende Informationen enthalten, die nicht unbedingt gelesen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-173">Because tooltip text isn't always visible, it should be supplemental info that users don't have to read.</span></span> <span data-ttu-id="36ec6-174">Teilen Sie wichtige Informationen in Form von selbsterklärenden Beschriftungen für Steuerelemente oder direkt eingefügtem ergänzendem Text mit.</span><span class="sxs-lookup"><span data-stu-id="36ec6-174">Communicate important info using self-explanatory control labels or in-place supplemental text.</span></span>
- <span data-ttu-id="36ec6-175">Verwenden Sie ggf. Bilder als QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="36ec6-175">Use images when appropriate.</span></span> <span data-ttu-id="36ec6-176">Manchmal ist ein Bild aussagekräftiger als Text.</span><span class="sxs-lookup"><span data-stu-id="36ec6-176">Sometimes it's better to use an image in a tooltip.</span></span> <span data-ttu-id="36ec6-177">Wenn der Benutzer z.B. auf einen Hyperlink zeigt, können Sie als QuickInfo eine Vorschau der verknüpften Seite anzeigen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-177">For example, when the user hovers over a hyperlink, you can use a tooltip to show a preview of the linked page.</span></span>
- <span data-ttu-id="36ec6-178">Verwenden Sie die QuickInfo nicht, um bereits in der UI vorhandene Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-178">Don't use a tooltip to display text already visible in the UI.</span></span> <span data-ttu-id="36ec6-179">Versehen Sie z.B. keine Schaltfläche mit QuickInfo-Text, der bereits auf der Schaltfläche selbst angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="36ec6-179">For example, don't put a tooltip on a button that shows the same text of the button.</span></span>
- <span data-ttu-id="36ec6-180">Fügen Sie in QuickInfos keine interaktiven Steuerelemente ein.</span><span class="sxs-lookup"><span data-stu-id="36ec6-180">Don't put interactive controls inside the tooltip.</span></span>
- <span data-ttu-id="36ec6-181">Fügen Sie in QuickInfos keine Bilder ein, die wie interaktive Steuerelemente aussehen.</span><span class="sxs-lookup"><span data-stu-id="36ec6-181">Don't put images that look like they are interactive inside the tooltip.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="36ec6-182">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="36ec6-182">Get the sample code</span></span>

- <span data-ttu-id="36ec6-183">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="36ec6-183">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="36ec6-184">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="36ec6-184">Related articles</span></span>

- [<span data-ttu-id="36ec6-185">QuickInfo-Klasse</span><span class="sxs-lookup"><span data-stu-id="36ec6-185">ToolTip class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227608)
