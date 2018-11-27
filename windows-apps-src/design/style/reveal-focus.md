---
description: Reveal-Focus sind Lichteffekte, die den Rahmen des fokussierbaren Elementes animieren, wenn der Benutzer den Fokus des Gamepad oder Tastatur darauf lenken.
title: Reveal-Fokus
template: detail.hbs
ms.date: 03/1/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: chphilip
design-contact: ''
dev-contact: stevenki
ms.localizationpriority: medium
ms.openlocfilehash: 311e5714c5428fac6509564fd00784299a02f630
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7711586"
---
# <a name="reveal-focus"></a><span data-ttu-id="eb2a2-104">Reveal-Fokus</span><span class="sxs-lookup"><span data-stu-id="eb2a2-104">Reveal Focus</span></span>

![Favoritenbild](images/header-reveal-focus.svg)

<span data-ttu-id="eb2a2-106">Reveal-Focus sind Lichteffekte für [10-Fuß-Erlebnisse](/windows/uwp/design/devices/designing-for-tv), wie z. B. Xbox One-und Fernsehbildschirme.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-106">Reveal Focus is a lighting effect for [10-foot experiences](/windows/uwp/design/devices/designing-for-tv), such as Xbox One and television screens.</span></span> <span data-ttu-id="eb2a2-107">Sie animieren den Rahmen des fokussierbaren Elementes wie beispielsweise Schaltflächen, wenn der Benutzer den Fokus des Gamepad oder der Tastatur darauf lenken.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-107">It animates the border of focusable elements, such as buttons, when the user moves gamepad or keyboard focus to them.</span></span> <span data-ttu-id="eb2a2-108">Es ist standardmäßig deaktiviert, lässt sich allerdings ganz einfach aktivieren.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-108">It's turned off by default, but it's simple to enable.</span></span> 

<span data-ttu-id="eb2a2-109">(Der Effekt "einblenden" markieren, ein Lichteffekt, der interaktive Elemente hervorhebt finden Sie im [Artikel "einblenden" markieren](/windows/uwp/design/style/reveal).)</span><span class="sxs-lookup"><span data-stu-id="eb2a2-109">(For the Reveal Highlight effect, a lighting affect that highlights interactive elements, see the [Reveal Highlight article](/windows/uwp/design/style/reveal).)</span></span>


> <span data-ttu-id="eb2a2-110">**Wichtige APIs**: [Application.FocusVisualKind-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.FocusVisualKind), [FocusVisualKind Enum](https://docs.microsoft.com/uwp/api/windows.ui.xaml.focusvisualkind), [Control.UseSystemFocusVisuals-Eigenschaft](/uwp/api/Windows.UI.Xaml.Controls.Control.UseSystemFocusVisuals)</span><span class="sxs-lookup"><span data-stu-id="eb2a2-110">**Important APIs**: [Application.FocusVisualKind property](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.FocusVisualKind), [FocusVisualKind enum](https://docs.microsoft.com/uwp/api/windows.ui.xaml.focusvisualkind), [Control.UseSystemFocusVisuals property](/uwp/api/Windows.UI.Xaml.Controls.Control.UseSystemFocusVisuals)</span></span>

## <a name="how-it-works"></a><span data-ttu-id="eb2a2-111">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="eb2a2-111">How it works</span></span>
<span data-ttu-id="eb2a2-112">Reveal-Focus lenkt den Fokus auf fokussierte Elemente indem ein animierter Schein um den Rahmens des Elements:</span><span class="sxs-lookup"><span data-stu-id="eb2a2-112">Reveal Focus calls attention to focused elements by adding an animated glow around the element's border:</span></span>

![Einblendeanzeige](images/traveling-focus-fullscreen-light-rf.gif)

<span data-ttu-id="eb2a2-114">Dies ist besonders in 10-Fuß-Szenarien, in denen der Benutzer nicht volle Aufmerksamkeit auf den gesamten Fernsehbildschirm lenkt.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-114">This is especially helpful in 10-foot scenarios where the user might not be paying full attention to the entire TV screen.</span></span> 

## <a name="examples"></a><span data-ttu-id="eb2a2-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="eb2a2-115">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="eb2a2-116">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="eb2a2-116">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="eb2a2-117">Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um zu <a href="xamlcontrolsgallery:/item/RevealFocus">die app zu öffnen und Reveal-Focus zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-117">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/RevealFocus">open the app and see Reveal Focus in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="eb2a2-118">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="eb2a2-118">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="eb2a2-119">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="eb2a2-119">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="how-to-use-it"></a><span data-ttu-id="eb2a2-120">Verwendung</span><span class="sxs-lookup"><span data-stu-id="eb2a2-120">How to use it</span></span>

<span data-ttu-id="eb2a2-121">Reveal-Focus ist, die sich standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-121">Reveal Focus is off by default.</span></span> <span data-ttu-id="eb2a2-122">So aktivieren Sie es:</span><span class="sxs-lookup"><span data-stu-id="eb2a2-122">To enable it:</span></span>
1. <span data-ttu-id="eb2a2-123">Rufen Sie im Konstruktor der App die Eigenschaft [AnalyticsInfo.VersionInfo.DeviceFamily](/uwp/api/windows.system.profile.analyticsversioninfo.DeviceFamily) auf, und überprüfen Sie, ob die aktuellen Gerätefamilie `Windows.Xbox` ist.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-123">In your app's constructor, call the [AnalyticsInfo.VersionInfo.DeviceFamily](/uwp/api/windows.system.profile.analyticsversioninfo.DeviceFamily) property and check whether the current device family is `Windows.Xbox`.</span></span>
2. <span data-ttu-id="eb2a2-124">Wenn die Gerätefamilie `Windows.Xbox` ist, legen Sie die Eigenschaft [Application.FocusVisualKind](/uwp/api/windows.ui.xaml.application.FocusVisualKind) auf `FocusVisualKind.Reveal` fest.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-124">If the device family is `Windows.Xbox`, set the [Application.FocusVisualKind](/uwp/api/windows.ui.xaml.application.FocusVisualKind) property to `FocusVisualKind.Reveal`.</span></span> 

```csharp
    if(AnalyticsInfo.VersionInfo.DeviceFamily == "Windows.Xbox")
    {
        this.FocusVisualKind = FocusVisualKind.Reveal;
    }
```

<span data-ttu-id="eb2a2-125">Nachdem Sie die **FocusVisualKind** -Eigenschaft festlegen, wendet das System die Reveal-Focus auf Wunsch automatisch auf alle Steuerelemente, deren [UseSystemFocusVisuals](/uwp/api/Windows.UI.Xaml.Controls.Control.UseSystemFocusVisuals) -Eigenschaft auf **"true"** (der Standardwert für die meisten Steuerelemente) festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-125">After you set the **FocusVisualKind** property, the system automatically applies the Reveal Focus effect to all controls whose [UseSystemFocusVisuals](/uwp/api/Windows.UI.Xaml.Controls.Control.UseSystemFocusVisuals) property is set to **True** (the default value for most controls).</span></span> 

## <a name="why-isnt-reveal-focus-on-by-default"></a><span data-ttu-id="eb2a2-126">Warum ist Reveal-Focus auf standardmäßig nicht?</span><span class="sxs-lookup"><span data-stu-id="eb2a2-126">Why isn't Reveal Focus on by default?</span></span> 
<span data-ttu-id="eb2a2-127">Wie Sie sehen können, ist es relativ einfach, Reveal-Focus zu aktivieren, wenn die app erkennt, dass sie auf einer Xbox ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-127">As you can see, it's fairly easy to turn on Reveal Focus when the app detects it's running on an Xbox.</span></span> <span data-ttu-id="eb2a2-128">Warum aktiviert das System die Funktion nicht einfach automatisch?</span><span class="sxs-lookup"><span data-stu-id="eb2a2-128">So, why doesn't the system just turn it on for you?</span></span> <span data-ttu-id="eb2a2-129">Reveal-Focus des visuellen Fokus erhöht, wodurch Probleme mit dem UI-Layout entstehen können.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-129">Because Reveal Focus increases the size of the focus visual, which might cause issues with your UI layout.</span></span> <span data-ttu-id="eb2a2-130">In einigen Fällen möchten Sie anpassen, die Reveal-Focus auf Wunsch für Ihre app zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-130">In some cases, you'll want to customize the Reveal Focus effect to optimize it for your app.</span></span>

## <a name="customizing-reveal-focus"></a><span data-ttu-id="eb2a2-131">Anpassen von Reveal-Focus</span><span class="sxs-lookup"><span data-stu-id="eb2a2-131">Customizing Reveal Focus</span></span>

<span data-ttu-id="eb2a2-132">Durch Ändern der Eigenschaften der visuellen Fokuselemente für jedes Steuerelement können Sie die Reveal-Focus auf Wunsch anpassen: [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness), [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness), [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush)und [ FocusVisualSecondaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush).</span><span class="sxs-lookup"><span data-stu-id="eb2a2-132">You can customize the Reveal Focus effect by modifying the focus visual properties for each control: [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness), [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness), [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush), and [FocusVisualSecondaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush).</span></span> <span data-ttu-id="eb2a2-133">Dank dieser Eigenschaften können Sie die Farbe und Breite des Fokusrechtecks anpassen.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-133">These properties let you customize the color and thickness of the focus rectangle.</span></span> <span data-ttu-id="eb2a2-134">(Dies sind die gleichen Eigenschaften, die Sie zum Erstellen der [Fokuselemente mit hoher Sichtbarkeit](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#high-visibility-focus-visuals) verwenden.)</span><span class="sxs-lookup"><span data-stu-id="eb2a2-134">(They're the same properties you use for creating [High Visibility focus visuals](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#high-visibility-focus-visuals).)</span></span> 

<span data-ttu-id="eb2a2-135">Aber bevor Sie mit dem Anpassen beginnen, es ist hilfreich, etwas mehr über die Komponenten, die Reveal-Focus bilden.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-135">But before you start customzing it, it's helpful to know a little more about the components that make up Reveal Focus.</span></span>

<span data-ttu-id="eb2a2-136">Es gibt drei Teile für den standardmäßigen Reveal-fokuselementen: der primäre und der sekundäre Rahmen sowie Reveal-glow.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-136">There are three parts to the default Reveal Focus visuals: the primary border, the secondary border and the Reveal glow.</span></span> <span data-ttu-id="eb2a2-137">Der primäre Rahmen ist **2Pixel** breit und verläuft an der *Außenseite* des sekundären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-137">The primary border is **2px** thick, and runs around the *outside* of the secondary border.</span></span> <span data-ttu-id="eb2a2-138">Der sekundäre Rahmen ist **1Pixel** breit und verläuft an der *Innenseite* des primären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-138">The secondary border is **1px** thick and runs around the *inside* of the primary border.</span></span> <span data-ttu-id="eb2a2-139">Der Reveal-Focus-Glanz hat eine Breite, die proportional zur Stärke des primären Rahmens ist und leuchtet um die *außerhalb* des primären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-139">The Reveal Focus glow has a thickness proportional to the thickness of the primary border and runs around the *outside* of the primary border.</span></span>

<span data-ttu-id="eb2a2-140">Zusätzlich zu den statischen Elementen feature Reveal-Focus-Visuals ein animiertes Licht, das bei Stillstand pulsiert und bewegt sich in Richtung des Fokus bewegt, wenn.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-140">In addition to the static elements, Reveal Focus visuals feature an animated light that pulsates when at rests and moves in the direction of focus when moving focus.</span></span>

![Revel-Focus](images/reveal-breakdown.svg)

## <a name="customize-the-border-thickness"></a><span data-ttu-id="eb2a2-142">Anpassen der Stärke des Rahmens</span><span class="sxs-lookup"><span data-stu-id="eb2a2-142">Customize the border thickness</span></span>

<span data-ttu-id="eb2a2-143">Verwenden Sie diese Eigenschaften, um die Breite der Rahmentypen eines Steuerelements zu ändern:</span><span class="sxs-lookup"><span data-stu-id="eb2a2-143">To change the thickness of the border types of a control, use these properties:</span></span>

| <span data-ttu-id="eb2a2-144">Rahmentyp</span><span class="sxs-lookup"><span data-stu-id="eb2a2-144">Border type</span></span> | <span data-ttu-id="eb2a2-145">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="eb2a2-145">Property</span></span> |
| --- | --- |
| <span data-ttu-id="eb2a2-146">Primär, Schein</span><span class="sxs-lookup"><span data-stu-id="eb2a2-146">Primary, Glow</span></span>   | [<span data-ttu-id="eb2a2-147">FocusVisualPrimaryThickness</span><span class="sxs-lookup"><span data-stu-id="eb2a2-147">FocusVisualPrimaryThickness</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness)<br/> <span data-ttu-id="eb2a2-148">(Das Ändern des primären Rahmens ändert die Breite des Scheins proportional.)</span><span class="sxs-lookup"><span data-stu-id="eb2a2-148">(Changing the primary border changes the thickness of the glow proportionately.)</span></span>   |
| <span data-ttu-id="eb2a2-149">Sekundärer</span><span class="sxs-lookup"><span data-stu-id="eb2a2-149">Secondary</span></span>   | [<span data-ttu-id="eb2a2-150">FocusVisualSecondaryThickness</span><span class="sxs-lookup"><span data-stu-id="eb2a2-150">FocusVisualSecondaryThickness</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness)   |


<span data-ttu-id="eb2a2-151">In diesem Beispiel wird die Breite des Rahmens des visuellen Fokus für eine Schaltfläche geändert:</span><span class="sxs-lookup"><span data-stu-id="eb2a2-151">This example changes the border thickness of a button's focus visual:</span></span>

```xaml
<Button FocusVisualPrimaryThickness="2" FocusVisualSecondaryThickness="1"/>
```

## <a name="customize-the-margin"></a><span data-ttu-id="eb2a2-152">Anpassen des Rands</span><span class="sxs-lookup"><span data-stu-id="eb2a2-152">Customize the margin</span></span>

<span data-ttu-id="eb2a2-153">Der Rand ist der Abstand zwischen den visuellen Grenzen des Steuerelements und dem Beginn des sekundären Rahmens der visuellen Fokuselemente.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-153">The margin is the space between the control's visual bounds and the start of the focus visuals secondary border.</span></span> <span data-ttu-id="eb2a2-154">Der standardmäßige Rand hat eine Breite von 1Pixel außerhalb der Grenzen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-154">The default margin is 1px away from the control bounds.</span></span> <span data-ttu-id="eb2a2-155">Sie können diesen Rand pro Steuerelement bearbeiten, indem Sie die Eigenschaft [FocusVisualMargin](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualMargin) ändern:</span><span class="sxs-lookup"><span data-stu-id="eb2a2-155">You can edit this margin on a per-control basis by changing the [FocusVisualMargin](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualMargin) property:</span></span>

```xaml
<Button FocusVisualPrimaryThickness="2" FocusVisualSecondaryThickness="1" FocusVisualMargin="-3"/>
```

<span data-ttu-id="eb2a2-156">Ein negativer Rand verschiebt den Rahmen weiter weg von der Mitte des Steuerelements. Ein positiver Rand verschiebt den Rahmen näher zur Mitte des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-156">A negative margin pushes the border away from the center of the control, and a positive margin moves the border closer to the center of the control.</span></span>

## <a name="customize-the-color"></a><span data-ttu-id="eb2a2-157">Anpassen der Farbe</span><span class="sxs-lookup"><span data-stu-id="eb2a2-157">Customize the color</span></span>

<span data-ttu-id="eb2a2-158">Um die Farbe von Reveal-Focus zu ändern, verwenden Sie die Eigenschaften [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) und [FocusVisualSecondaryBrush](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush) .</span><span class="sxs-lookup"><span data-stu-id="eb2a2-158">To change color of the Reveal Focus visual, use the [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) and [FocusVisualSecondaryBrush](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush) properties.</span></span>

| <span data-ttu-id="eb2a2-159">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="eb2a2-159">Property</span></span> | <span data-ttu-id="eb2a2-160">Standardressource</span><span class="sxs-lookup"><span data-stu-id="eb2a2-160">Default resource</span></span> | <span data-ttu-id="eb2a2-161">Standardressourcewert</span><span class="sxs-lookup"><span data-stu-id="eb2a2-161">Default resource value</span></span> |
| ---- | ---- | --- | 
| [<span data-ttu-id="eb2a2-162">FocusVisualPrimaryBrush</span><span class="sxs-lookup"><span data-stu-id="eb2a2-162">FocusVisualPrimaryBrush</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) | <span data-ttu-id="eb2a2-163">SystemControlRevealFocusVisualBrush</span><span class="sxs-lookup"><span data-stu-id="eb2a2-163">SystemControlRevealFocusVisualBrush</span></span>  | <span data-ttu-id="eb2a2-164">SystemAccentColor</span><span class="sxs-lookup"><span data-stu-id="eb2a2-164">SystemAccentColor</span></span> |
| [<span data-ttu-id="eb2a2-165">FocusVisualSecondaryBrush</span><span class="sxs-lookup"><span data-stu-id="eb2a2-165">FocusVisualSecondaryBrush</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryBrush)  | <span data-ttu-id="eb2a2-166">SystemControlFocusVisualSecondaryBrush</span><span class="sxs-lookup"><span data-stu-id="eb2a2-166">SystemControlFocusVisualSecondaryBrush</span></span>  | <span data-ttu-id="eb2a2-167">SystemAltMediumColor</span><span class="sxs-lookup"><span data-stu-id="eb2a2-167">SystemAltMediumColor</span></span> |

<span data-ttu-id="eb2a2-168">(Die Eigenschaft des FocusPrimaryBrush wird standardmäßig als **SystemControlRevealFocusVisualBrush**-Ressourcen verwendet, wenn **FocusVisualKind** auf \*\*Einblenden \*\* festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-168">(The FocusPrimaryBrush property only defaults to the **SystemControlRevealFocusVisualBrush** resources when **FocusVisualKind** is set to **Reveal**.</span></span> <span data-ttu-id="eb2a2-169">Andernfalls wird **SystemControlFocusVisualPrimaryBrush** verwendet.)</span><span class="sxs-lookup"><span data-stu-id="eb2a2-169">Otherwise, it uses **SystemControlFocusVisualPrimaryBrush**.)</span></span>


<span data-ttu-id="eb2a2-170">Um die Farbe des visuellen Fokus eines einzelnen Steuerelements zu ändern, legen Sie die Eigenschaften direkt im Steuerelement fest.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-170">To change the color of the focus visual of an individual control, set the properties directly on the control.</span></span> <span data-ttu-id="eb2a2-171">In diesem Beispiel wird die Farbe der Fokusanzeige einer Schaltfläche außer Kraft gesetzt.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-171">This example overrides the focus visual colors of a button.</span></span>

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

<span data-ttu-id="eb2a2-172">Um die Farbe aller Fokusanzeigen in der gesamten App zu ändern, setzen Sie die Ressourcen **SystemControlRevealFocusVisualBrush** und **SystemControlFocusVisualSecondaryBrush** mit Ihrer eigenen Definition außer Kraft:</span><span class="sxs-lookup"><span data-stu-id="eb2a2-172">To change the color of all focus visuals in your entire app, override the **SystemControlRevealFocusVisualBrush** and  **SystemControlFocusVisualSecondaryBrush** resources with your own definition:</span></span>

```xaml
<!-- App.xaml -->
<Application.Resources>

    <!-- Override Reveal Focus default resources. -->
    <SolidColorBrush x:Key="SystemControlRevealFocusVisualBrush" Color="{ThemeResource SystemBaseHighColor}"/>
    <SolidColorBrush x:Key="SystemControlFocusVisualSecondaryBrush" Color="{ThemeResource SystemAccentColor}"/>
</Application.Resources>
```

<span data-ttu-id="eb2a2-173">Weitere Informationen zum Ändern der Farbe der Fokusanzeige finden Sie unter [Farbbranding und -anpassung](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#color-branding--customizing).</span><span class="sxs-lookup"><span data-stu-id="eb2a2-173">For more information on modifying the focus visual's color, see [Color Branding & Customizing](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#color-branding--customizing).</span></span>


## <a name="show-just-the-glow"></a><span data-ttu-id="eb2a2-174">Nur den Schein anzeigen</span><span class="sxs-lookup"><span data-stu-id="eb2a2-174">Show just the glow</span></span>

<span data-ttu-id="eb2a2-175">Wenn Sie nur den Schein ohne die primäre oder sekundäre Fokusanzeige verwenden möchten, legen Sie einfach die Eigenschaften des Steuerelements [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) `Transparent`und [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness) auf `0` fest.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-175">If you'd like to use only the glow without the primary or secondary focus visual, simply set the control's [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryBrush) property to `Transparent` and the [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualSecondaryThickness)  to `0`.</span></span> <span data-ttu-id="eb2a2-176">In diesem Fall übernimmt der Schein die Farbe des Hintergrunds des Steuerelements für ein randlos Verhalten.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-176">In this case, the glow will adopt the color of the control background to provide a borderless feel.</span></span> <span data-ttu-id="eb2a2-177">Sie können die Breite des Scheins mit [FocusVisualPrimaryThickness ](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness) ändern.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-177">You can modify the thickness of the glow using [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.FocusVisualPrimaryThickness).</span></span>

```xaml

<!-- Show just the glow -->
<Button
    FocusVisualPrimaryBrush="Transparent"
    FocusVisualSecondaryThickness="0" />    
```


## <a name="use-your-own-focus-visuals"></a><span data-ttu-id="eb2a2-178">Verwenden Sie Ihre eigenen visuellen Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="eb2a2-178">Use your own focus visuals</span></span>

<span data-ttu-id="eb2a2-179">Eine weitere Möglichkeit zum Anpassen von Reveal-Focus ist können die System-Fokusanzeigen deaktivieren, indem Sie eigene visuelle Zustände verwenden.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-179">Another way to customize Reveal Focus is to opt out of the system-provided focus visuals by drawing your own using visual states.</span></span> <span data-ttu-id="eb2a2-180">Weitere Informationen finden Sie unter [Beispiel für visuelle Fokuselemente](http://go.microsoft.com/fwlink/p/?LinkID=619895).</span><span class="sxs-lookup"><span data-stu-id="eb2a2-180">To learn more, see the [Focus visuals sample](http://go.microsoft.com/fwlink/p/?LinkID=619895).</span></span>


## <a name="reveal-focus-and-the-fluent-design-system"></a><span data-ttu-id="eb2a2-181">Reveal-Focus und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="eb2a2-181">Reveal Focus and the Fluent Design System</span></span>

<span data-ttu-id="eb2a2-182">Reveal-Focus ist eine Komponente des Fluent Design-Systems, die Lichteffekte in Ihrer app ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="eb2a2-182">Reveal Focus is a Fluent Design System component that adds light to your app.</span></span> <span data-ttu-id="eb2a2-183">Weitere Informationen zum Fluent Design-Systems und den zugehörigen Komponenten finden Sie unter [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb2a2-183">To learn more about the Fluent Design system and its other components, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

## <a name="related-articles"></a><span data-ttu-id="eb2a2-184">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="eb2a2-184">Related articles</span></span>

- [<span data-ttu-id="eb2a2-185">Reveal-Highlight</span><span class="sxs-lookup"><span data-stu-id="eb2a2-185">Reveal Highlight</span></span>](https://docs.microsoft.com/windows/uwp/design/style/reveal)
- [<span data-ttu-id="eb2a2-186">Entwerfen für Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="eb2a2-186">Designing for Xbox and TV</span></span>](/windows/uwp/design/devices/designing-for-tv)
- [<span data-ttu-id="eb2a2-187">Interaktionen von Gamepad und Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="eb2a2-187">Gamepad and remote control interactions</span></span>](https://docs.microsoft.com/windows/uwp/design/input/gamepad-and-remote-interactions)
- [<span data-ttu-id="eb2a2-188">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="eb2a2-188">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)
- [<span data-ttu-id="eb2a2-189">Kompositionseffekte</span><span class="sxs-lookup"><span data-stu-id="eb2a2-189">Composition Effects</span></span>](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
- [<span data-ttu-id="eb2a2-190">Wissenschaft im System: Fluent Design und Tiefe</span><span class="sxs-lookup"><span data-stu-id="eb2a2-190">Science in the System: Fluent Design and Depth</span></span>](https://medium.com/microsoft-design/science-in-the-system-fluent-design-and-depth-fb6d0f23a53f)
- [<span data-ttu-id="eb2a2-191">Wissenschaft im System: Fluent Design und Licht</span><span class="sxs-lookup"><span data-stu-id="eb2a2-191">Science in the System: Fluent Design and Light</span></span>](https://medium.com/microsoft-design/the-science-in-the-system-fluent-design-and-light-94a17e0b3a4f)
