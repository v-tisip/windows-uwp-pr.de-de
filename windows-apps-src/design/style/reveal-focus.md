---
author: cphilippona
description: Reveal-focus sind Lichteffekte, die den Rahmen des fokussierbaren Elementes animieren, wenn der Benutzer den Fokus des Gamepad oder der Tastatur darauf lenken.
title: Reveal-focus
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
ms.localizationpriority: high
ms.openlocfilehash: 0a5f3dca3c8310bddbcd63c814d2d883151ff1f3
ms.sourcegitcommit: ef5a1e1807313a2caa9c9b35ea20b129ff7155d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="reveal-focus"></a><span data-ttu-id="22c3a-104">Reveal-focus</span><span class="sxs-lookup"><span data-stu-id="22c3a-104">Reveal focus</span></span>

<span data-ttu-id="22c3a-105">Reveal-focus sind Lichteffekte für [10-Fuß-Umgebungen](/windows/uwp/design/devices/designing-for-tv) wie z.B. Xbox One- und Fernsehbildschirme.</span><span class="sxs-lookup"><span data-stu-id="22c3a-105">Reveal focus is a lighting effect for [10 foot experiences](/windows/uwp/design/devices/designing-for-tv), such as Xbox One and television screens.</span></span> <span data-ttu-id="22c3a-106">Sie animieren den Rahmen des fokussierbaren Elementes wie beispielsweise Schaltflächen, wenn der Benutzer den Fokus des Gamepad oder der Tastatur darauf lenken.</span><span class="sxs-lookup"><span data-stu-id="22c3a-106">It  animates the border of focusable elements, such as buttons, when the user moves gamepad or keyboard focus to them.</span></span> <span data-ttu-id="22c3a-107">Es ist standardmäßig deaktiviert, lässt sich allerdings ganz einfach aktivieren.</span><span class="sxs-lookup"><span data-stu-id="22c3a-107">It's turned off by default, but it's simple to enable.</span></span> 

<span data-ttu-id="22c3a-108">(Informationen über Reveal-highlight, ein Lichteffekt, der interaktive Elemente hervorhebt, finden Sie im Artikel [Reveal highlight](/windows/uwp/design/style/reveal).)</span><span class="sxs-lookup"><span data-stu-id="22c3a-108">(For the Reveal highlight effect, a lighting affect that highlights interactive elements, see the [Reveal highlight article](/windows/uwp/design/style/reveal).)</span></span>


> <span data-ttu-id="22c3a-109">**Wichtige APIs**: [Application.FocusVisualKind-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_FocusVisualKind), [FocusVisualKind Enum](https://docs.microsoft.com/uwp/api/windows.ui.xaml.focusvisualkind), [Control.UseSystemFocusVisuals-Eigenschaft](/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_UseSystemFocusVisuals)</span><span class="sxs-lookup"><span data-stu-id="22c3a-109">**Important APIs**: [Application.FocusVisualKind property](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_FocusVisualKind), [FocusVisualKind enum](https://docs.microsoft.com/uwp/api/windows.ui.xaml.focusvisualkind), [Control.UseSystemFocusVisuals property](/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_UseSystemFocusVisuals)</span></span>

## <a name="how-it-works"></a><span data-ttu-id="22c3a-110">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="22c3a-110">How it works</span></span>
<span data-ttu-id="22c3a-111">Reveal-focus lenkt den Fokus auf fokussierte Elemente, indem ein animierter Schein um den Rahmens des Elements eingeblendet wird:</span><span class="sxs-lookup"><span data-stu-id="22c3a-111">Reveal focus calls attention to focused elements by adding an animated glow around the element's border:</span></span>

![Reveal Visual](images/traveling-focus-fullscreen-light-rf.gif)

<span data-ttu-id="22c3a-113">Dies ist besonders in 10-Fuß-Szenarien hilfreich, in denen der Benutzer nicht die volle Aufmerksamkeit auf den gesamten Fernsehbildschirm lenkt.</span><span class="sxs-lookup"><span data-stu-id="22c3a-113">This is especially helpful in 10 foot scenarios where the user might not be paying full attention to the entire TV screen.</span></span> 

## <a name="examples"></a><span data-ttu-id="22c3a-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="22c3a-114">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="22c3a-115">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="22c3a-115">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="22c3a-116">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/RevealFocus">die App zu öffnen und Reveal-focus zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="22c3a-116">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/RevealFocus">open the app and see Reveal focus in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="22c3a-117">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="22c3a-117">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="22c3a-118">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="22c3a-118">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="how-to-use-it"></a><span data-ttu-id="22c3a-119">Verwendung</span><span class="sxs-lookup"><span data-stu-id="22c3a-119">How to use it</span></span>

<span data-ttu-id="22c3a-120">Reveal-focus ist standardmäßig deaktiviert</span><span class="sxs-lookup"><span data-stu-id="22c3a-120">Reveal focus is off by default.</span></span> <span data-ttu-id="22c3a-121">So aktivieren Sie es:</span><span class="sxs-lookup"><span data-stu-id="22c3a-121">To enable it:</span></span>
1. <span data-ttu-id="22c3a-122">Rufen Sie im Konstruktor der App die Eigenschaft [AnalyticsInfo.VersionInfo.DeviceFamily](/uwp/api/windows.system.profile.analyticsversioninfo#Windows_System_Profile_AnalyticsVersionInfo_DeviceFamily) auf, und überprüfen Sie, ob die aktuellen Gerätefamilie `Windows.Xbox` ist.</span><span class="sxs-lookup"><span data-stu-id="22c3a-122">In your app's constructor, call the [AnalyticsInfo.VersionInfo.DeviceFamily](/uwp/api/windows.system.profile.analyticsversioninfo#Windows_System_Profile_AnalyticsVersionInfo_DeviceFamily) property and check whether the current device family is `Windows.Xbox`.</span></span>
2. <span data-ttu-id="22c3a-123">Wenn die Gerätefamilie `Windows.Xbox` ist, legen Sie die Eigenschaft [Application.FocusVisualKind](/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_FocusVisualKind) auf `FocusVisualKind.Reveal` fest.</span><span class="sxs-lookup"><span data-stu-id="22c3a-123">If the device family is `Windows.Xbox`, set the [Application.FocusVisualKind](/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_FocusVisualKind) property to `FocusVisualKind.Reveal`.</span></span> 

```csharp
    if(AnalyticsInfo.VersionInfo.DeviceFamily == "Windows.Xbox")
    {
        this.FocusVisualKind = FocusVisualKind.Reveal;
    }
```

<span data-ttu-id="22c3a-124">Nachdem Sie die Eigenschaft von **FocusVisualKind** festgelegt haben, wendet das System automatisch Reveal-focus auf alle Steuerelemente an, deren Eigenschaft [UseSystemFocusVisuals](/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_UseSystemFocusVisuals) auf **True** festgelegt ist (der Standardwert für die meisten Steuerelemente).</span><span class="sxs-lookup"><span data-stu-id="22c3a-124">After you set the **FocusVisualKind** property, the system automatically applies the reveal focus effect to all controls whose [UseSystemFocusVisuals](/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_UseSystemFocusVisuals) property is set to **True** (the default value for most controls).</span></span> 

## <a name="why-isnt-reveal-focus-on-by-default"></a><span data-ttu-id="22c3a-125">Warum ist Reveal-focus nicht standardmäßig aktiviert?</span><span class="sxs-lookup"><span data-stu-id="22c3a-125">Why isn't Reveal focus on by default?</span></span> 
<span data-ttu-id="22c3a-126">Wie Sie sehen können, ist es relativ einfach, Reveal-focus zu aktivieren, wenn Die App erkennt, dass es auf Xbox ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="22c3a-126">As you can see, it's fairly easy to turn on Reveal focus when the app detects it's running on an Xbox.</span></span> <span data-ttu-id="22c3a-127">Warum aktiviert das System die Funktion nicht einfach automatisch?</span><span class="sxs-lookup"><span data-stu-id="22c3a-127">So, why doesn't the system just turn it on for you?</span></span> <span data-ttu-id="22c3a-128">Reveal-focus erhöht die Fokusanzeige, wodurch Probleme mit dem UI-Layout entstehen können.</span><span class="sxs-lookup"><span data-stu-id="22c3a-128">Because Reveal focus increases the size of the focus visual, which might cause issues with your UI layout.</span></span> <span data-ttu-id="22c3a-129">Sie können Reveal-focus auf Wunsch gelegentlich anpassen, um die Funktion für Ihre App zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="22c3a-129">In some cases, you'll want to customize the Reveal focus effect to optimize it for your app.</span></span>

## <a name="customizing-reveal-focus"></a><span data-ttu-id="22c3a-130">Anpassen von Reveal-focus</span><span class="sxs-lookup"><span data-stu-id="22c3a-130">Customizing Reveal focus</span></span>

<span data-ttu-id="22c3a-131">Sie können den Effekt von Reveal-focus durch Ändern der Eigenschaften der visuellen Fokuselemente für jedes Steuerelement anpassen: [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryThickness), [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryThickness), [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryBrush), und [FocusVisualSecondaryBrush ](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryBrush).</span><span class="sxs-lookup"><span data-stu-id="22c3a-131">You can customize the Reveal focus effect by modifying the focus visual properties for each control: [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryThickness), [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryThickness), [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryBrush), and [FocusVisualSecondaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryBrush).</span></span> <span data-ttu-id="22c3a-132">Dank dieser Eigenschaften können Sie die Farbe und Breite des Fokusrechtecks anpassen.</span><span class="sxs-lookup"><span data-stu-id="22c3a-132">These properties let you customize the color and thickness of the focus rectangle.</span></span> <span data-ttu-id="22c3a-133">(Dies sind die gleichen Eigenschaften, die Sie zum Erstellen der [Fokuselemente mit hoher Sichtbarkeit](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#high-visibility-focus-visuals) verwenden.)</span><span class="sxs-lookup"><span data-stu-id="22c3a-133">(They're the same properties you use for creating [High Visibility focus visuals](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#high-visibility-focus-visuals).)</span></span> 

<span data-ttu-id="22c3a-134">Bevor Sie mit dem Anpassen beginnen, sollten Sie weitere Informationen zu den Komponenten von Reveal-focus haben.</span><span class="sxs-lookup"><span data-stu-id="22c3a-134">But before you start customzing it, it's helpful to know a little more about about the components that make up Reveal focus.</span></span>

<span data-ttu-id="22c3a-135">Es gibt drei Elemente bei den standardmäßigen Reveal-Fokuselementen: der primäre und der sekundäre Rahmen sowie Reveal-glow.</span><span class="sxs-lookup"><span data-stu-id="22c3a-135">There are three parts to the default Reveal focus visuals: the primary border, the secondary border and the Reveal glow.</span></span> <span data-ttu-id="22c3a-136">Der primäre Rahmen ist **2Pixel** breit und verläuft an der *Außenseite* des sekundären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="22c3a-136">The primary border is **2px** thick, and runs around the *outside* of the secondary border.</span></span> <span data-ttu-id="22c3a-137">Der sekundäre Rahmen ist **1Pixel** breit und verläuft an der *Innenseite* des primären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="22c3a-137">The secondary border is **1px** thick and runs around the *inside* of the primary border.</span></span> <span data-ttu-id="22c3a-138">Der Reveal-focus-Glanz hat eine Breite, die proportional zur Stärke des primären Rahmens ist und leuchtet um die *Außenseite* des primären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="22c3a-138">The Reveal focus glow has a thickness proportional to the thickness of the primary border and runs around the *outside* of the primary border.</span></span>

<span data-ttu-id="22c3a-139">Zusätzlich zu den statischen Elementen bietet Reveal-focus ein animiertes Licht, das bei Stillstand pulsiert und sich in Richtung des Fokus bewegt, wenn der Fokus geändert wird.</span><span class="sxs-lookup"><span data-stu-id="22c3a-139">In addition to the static elements, Reveal focus visuals feature an animated light that pulsates when at rests and moves in the direction of focus when moving focus.</span></span>

![Ebenen von Revel-focus](images/reveal-breakdown.svg)

## <a name="customize-the-border-thickness"></a><span data-ttu-id="22c3a-141">Anpassen der Stärke des Rahmens</span><span class="sxs-lookup"><span data-stu-id="22c3a-141">Customize the border thickness</span></span>

<span data-ttu-id="22c3a-142">Verwenden Sie diese Eigenschaften, um die Breite der Rahmentypen eines Steuerelements zu ändern:</span><span class="sxs-lookup"><span data-stu-id="22c3a-142">To change the thickness of the border types of a control, use these properties:</span></span>

| <span data-ttu-id="22c3a-143">Rahmentyp</span><span class="sxs-lookup"><span data-stu-id="22c3a-143">Border type</span></span> | <span data-ttu-id="22c3a-144">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="22c3a-144">Property</span></span> |
| --- | --- |
| <span data-ttu-id="22c3a-145">Primär, Schein</span><span class="sxs-lookup"><span data-stu-id="22c3a-145">Primary, Glow</span></span>   | [<span data-ttu-id="22c3a-146">FocusVisualPrimaryThickness</span><span class="sxs-lookup"><span data-stu-id="22c3a-146">FocusVisualPrimaryThickness</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryThickness)<br/> <span data-ttu-id="22c3a-147">(Das Ändern des primären Rahmens ändert die Breite des Scheins proportional.)</span><span class="sxs-lookup"><span data-stu-id="22c3a-147">(Changing the primary border changes the thickness of the glow proportionately.)</span></span>   |
| <span data-ttu-id="22c3a-148">Sekundärer</span><span class="sxs-lookup"><span data-stu-id="22c3a-148">Secondary</span></span>   | [<span data-ttu-id="22c3a-149">FocusVisualSecondaryThickness</span><span class="sxs-lookup"><span data-stu-id="22c3a-149">FocusVisualSecondaryThickness</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryThickness)   |


<span data-ttu-id="22c3a-150">In diesem Beispiel wird die Breite des Rahmens des visuellen Fokus für eine Schaltfläche geändert:</span><span class="sxs-lookup"><span data-stu-id="22c3a-150">This example changes the border thickness of a button's focus visual:</span></span>

```xaml
<Button FocusVisualPrimaryThickness="2" FocusVisualSecondaryThickness="1"/>
```

## <a name="customize-the-margin"></a><span data-ttu-id="22c3a-151">Anpassen des Rands</span><span class="sxs-lookup"><span data-stu-id="22c3a-151">Customize the margin</span></span>

<span data-ttu-id="22c3a-152">Der Rand ist der Abstand zwischen den visuellen Grenzen des Steuerelements und dem Beginn des sekundären Rahmens der visuellen Fokuselemente.</span><span class="sxs-lookup"><span data-stu-id="22c3a-152">The margin is the space between the control's visual bounds and the start of the focus visuals secondary border.</span></span> <span data-ttu-id="22c3a-153">Der standardmäßige Rand hat eine Breite von 1Pixel außerhalb der Grenzen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="22c3a-153">The default margin is 1px away from the control bounds.</span></span> <span data-ttu-id="22c3a-154">Sie können diesen Rand pro Steuerelement bearbeiten, indem Sie die Eigenschaft [FocusVisualMargin](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualMargin) ändern:</span><span class="sxs-lookup"><span data-stu-id="22c3a-154">You can edit this margin on a per-control basis by changing the [FocusVisualMargin](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualMargin) property:</span></span>

```xaml
<Button FocusVisualPrimaryThickness="2" FocusVisualSecondaryThickness="1" FocusVisualMargin="-3"/>
```

<span data-ttu-id="22c3a-155">Ein negativer Rand verschiebt den Rahmen weiter weg von der Mitte des Steuerelements. Ein positiver Rand verschiebt den Rahmen näher zur Mitte des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="22c3a-155">A negative margin pushes the border away from the center of the control, and a positive margin moves the border closer to the center of the control.</span></span>

## <a name="customize-the-color"></a><span data-ttu-id="22c3a-156">Anpassen der Farbe</span><span class="sxs-lookup"><span data-stu-id="22c3a-156">Customize the color</span></span>

<span data-ttu-id="22c3a-157">Um die Farbe von Reveal-focus zu ändern, verwenden Sie die Eigenschaften von [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryBrush) und [FocusVisualSecondaryBrush](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryBrush).</span><span class="sxs-lookup"><span data-stu-id="22c3a-157">To change color of the reveal focus visual, use the [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryBrush) and [FocusVisualSecondaryBrush](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryBrush) properties.</span></span>

| <span data-ttu-id="22c3a-158">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="22c3a-158">Property</span></span> | <span data-ttu-id="22c3a-159">Standardressource</span><span class="sxs-lookup"><span data-stu-id="22c3a-159">Default resource</span></span> | <span data-ttu-id="22c3a-160">Standardressourcewert</span><span class="sxs-lookup"><span data-stu-id="22c3a-160">Default resource value</span></span> |
| ---- | ---- | --- | 
| [<span data-ttu-id="22c3a-161">FocusVisualPrimaryBrush</span><span class="sxs-lookup"><span data-stu-id="22c3a-161">FocusVisualPrimaryBrush</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryBrush) | <span data-ttu-id="22c3a-162">SystemControlRevealFocusVisualBrush</span><span class="sxs-lookup"><span data-stu-id="22c3a-162">SystemControlRevealFocusVisualBrush</span></span>  | <span data-ttu-id="22c3a-163">SystemAccentColor</span><span class="sxs-lookup"><span data-stu-id="22c3a-163">SystemAccentColor</span></span> |
| [<span data-ttu-id="22c3a-164">FocusVisualSecondaryBrush</span><span class="sxs-lookup"><span data-stu-id="22c3a-164">FocusVisualSecondaryBrush</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryBrush)  | <span data-ttu-id="22c3a-165">SystemControlFocusVisualSecondaryBrush</span><span class="sxs-lookup"><span data-stu-id="22c3a-165">SystemControlFocusVisualSecondaryBrush</span></span>  | <span data-ttu-id="22c3a-166">SystemAltMediumColor</span><span class="sxs-lookup"><span data-stu-id="22c3a-166">SystemAltMediumColor</span></span> |

<span data-ttu-id="22c3a-167">(Die Eigenschaft des FocusPrimaryBrush wird standardmäßig als **SystemControlRevealFocusVisualBrush**-Ressourcen verwendet, wenn **FocusVisualKind** auf **Einblenden ** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="22c3a-167">(The FocusPrimaryBrush property only defaults to the **SystemControlRevealFocusVisualBrush** resources when **FocusVisualKind** is set to **Reveal**.</span></span> <span data-ttu-id="22c3a-168">Andernfalls wird **SystemControlFocusVisualPrimaryBrush** verwendet.)</span><span class="sxs-lookup"><span data-stu-id="22c3a-168">Otherwise, it uses **SystemControlFocusVisualPrimaryBrush**.)</span></span>


<span data-ttu-id="22c3a-169">Um die Farbe des visuellen Fokus eines einzelnen Steuerelements zu ändern, legen Sie die Eigenschaften direkt im Steuerelement fest.</span><span class="sxs-lookup"><span data-stu-id="22c3a-169">To change the color of the focus visual of an individual control, set the properties directly on the control.</span></span> <span data-ttu-id="22c3a-170">In diesem Beispiel wird die Farbe der Fokusanzeige einer Schaltfläche außer Kraft gesetzt.</span><span class="sxs-lookup"><span data-stu-id="22c3a-170">This example overrides the focus visual colors of a button.</span></span>

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

<span data-ttu-id="22c3a-171">Um die Farbe aller Fokusanzeigen in der gesamten App zu ändern, setzen Sie die Ressourcen **SystemControlRevealFocusVisualBrush** und **SystemControlFocusVisualSecondaryBrush** mit Ihrer eigenen Definition außer Kraft:</span><span class="sxs-lookup"><span data-stu-id="22c3a-171">To change the color of all focus visuals in your entire app, override the **SystemControlRevealFocusVisualBrush** and  **SystemControlFocusVisualSecondaryBrush** resources with your own definition:</span></span>

```xaml
<!-- App.xaml -->
<Application.Resources>

    <!-- Override Reveal focus default resources. -->
    <SolidColorBrush x:Key="SystemControlRevealFocusVisualBrush" Color="{ThemeResource SystemBaseHighColor}"/>
    <SolidColorBrush x:Key="SystemControlFocusVisualSecondaryBrush" Color="{ThemeResource SystemAccentColor}"/>
</Application.Resources>
```

<span data-ttu-id="22c3a-172">Weitere Informationen zum Ändern der Farbe der Fokusanzeige finden Sie unter [Farbbranding und -anpassung](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#color-branding--customizing).</span><span class="sxs-lookup"><span data-stu-id="22c3a-172">For more information on modifying the focus visual's color, see [Color Branding & Customizing](https://docs.microsoft.com/windows/uwp/design/input/guidelines-for-visualfeedback#color-branding--customizing).</span></span>


## <a name="show-just-the-glow"></a><span data-ttu-id="22c3a-173">Nur den Schein anzeigen</span><span class="sxs-lookup"><span data-stu-id="22c3a-173">Show just the glow</span></span>

<span data-ttu-id="22c3a-174">Wenn Sie nur den Schein ohne die primäre oder sekundäre Fokusanzeige verwenden möchten, legen Sie einfach die Eigenschaften des Steuerelements [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryBrush) `Transparent`und [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryThickness) auf `0` fest.</span><span class="sxs-lookup"><span data-stu-id="22c3a-174">If you'd like to use only the glow without the primary or secondary focus visual, simply set the control's [FocusVisualPrimaryBrush](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryBrush) property to `Transparent` and the [FocusVisualSecondaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualSecondaryThickness)  to `0`.</span></span> <span data-ttu-id="22c3a-175">In diesem Fall übernimmt der Schein die Farbe des Hintergrunds des Steuerelements für ein randlos Verhalten.</span><span class="sxs-lookup"><span data-stu-id="22c3a-175">In this case, the glow will adopt the color of the control background to provide a borderless feel.</span></span> <span data-ttu-id="22c3a-176">Sie können die Breite des Scheins mit [FocusVisualPrimaryThickness ](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryThickness) ändern.</span><span class="sxs-lookup"><span data-stu-id="22c3a-176">You can modify the thickness of the glow using [FocusVisualPrimaryThickness](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_FocusVisualPrimaryThickness).</span></span>

```xaml

<!-- Show just the glow -->
<Button
    FocusVisualPrimaryBrush="Transparent"
    FocusVisualSecondaryThickness="0" />    
```


## <a name="use-your-own-focus-visuals"></a><span data-ttu-id="22c3a-177">Verwenden Sie Ihre eigenen visuellen Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="22c3a-177">Use your own focus visuals</span></span>

<span data-ttu-id="22c3a-178">Sie können die systemeigenen Fokusanzeigen deaktivieren und eigene Fokusanzeigen darstellen, wenn Sie Reveal-focus anpassen möchten.</span><span class="sxs-lookup"><span data-stu-id="22c3a-178">Another way to customize reveal focus is to opt out of the system-provided focus visuals by drawing your own using visual states.</span></span> <span data-ttu-id="22c3a-179">Weitere Informationen finden Sie unter [Beispiel für visuelle Fokuselemente](http://go.microsoft.com/fwlink/p/?LinkID=619895).</span><span class="sxs-lookup"><span data-stu-id="22c3a-179">To learn more, see the [Focus visuals sample](http://go.microsoft.com/fwlink/p/?LinkID=619895).</span></span>


## <a name="reveal-focus-and-the-fluent-design-system"></a><span data-ttu-id="22c3a-180">Reveal-focus und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="22c3a-180">Reveal focus and the Fluent Design System</span></span>

<span data-ttu-id="22c3a-181">Reveal-focus ist eine Komponente des Fluent Design-Systems, die Lichteffekte in Ihrer App ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="22c3a-181">Reveal focus is a Fluent Design System component that adds light to your app.</span></span> <span data-ttu-id="22c3a-182">Weitere Informationen zum Fluent Design-Systems und den zugehörigen Komponenten finden Sie unter [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="22c3a-182">To learn more about the Fluent Design system and its other components, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

## <a name="related-articles"></a><span data-ttu-id="22c3a-183">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="22c3a-183">Related articles</span></span>

- [<span data-ttu-id="22c3a-184">Reveal-highlight</span><span class="sxs-lookup"><span data-stu-id="22c3a-184">Reveal highlight</span></span>](https://docs.microsoft.com/windows/uwp/design/style/reveal)
- [<span data-ttu-id="22c3a-185">Entwerfen für Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="22c3a-185">Designing for Xbox and TV</span></span>](/windows/uwp/design/devices/designing-for-tv)
- [<span data-ttu-id="22c3a-186">Interaktionen von Gamepad und Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="22c3a-186">Gamepad and remote control interactions</span></span>](https://docs.microsoft.com/windows/uwp/design/input/gamepad-and-remote-interactions)
- [<span data-ttu-id="22c3a-187">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="22c3a-187">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)
- [<span data-ttu-id="22c3a-188">Kompositionseffekte</span><span class="sxs-lookup"><span data-stu-id="22c3a-188">Composition Effects</span></span>](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
- [<span data-ttu-id="22c3a-189">Wissenschaft im System: Fluent Design und Tiefe</span><span class="sxs-lookup"><span data-stu-id="22c3a-189">Science in the System: Fluent Design and Depth</span></span>](https://medium.com/microsoft-design/science-in-the-system-fluent-design-and-depth-fb6d0f23a53f)
- [<span data-ttu-id="22c3a-190">Wissenschaft im System: Fluent Design und Licht</span><span class="sxs-lookup"><span data-stu-id="22c3a-190">Science in the System: Fluent Design and Light</span></span>](https://medium.com/microsoft-design/the-science-in-the-system-fluent-design-and-light-94a17e0b3a4f)
