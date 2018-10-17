---
author: serenaz
description: Z-Tiefe oder relativ Tiefe und Schatten gibt zwei Möglichkeiten, Tiefe in Ihre app an Benutzer beim Fokus natürlichen und effizienten unterstützen integrieren.
title: Z-Tiefe und Schatten für UWP-apps
template: detail.hbs
ms.author: sezhen
ms.date: 02/12/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: chigy
design-contact: balrayit
ms.localizationpriority: medium
ms.openlocfilehash: a1433b131b994ee2b1323909bc7c195e00f43cde
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4748512"
---
# <a name="z-depth-and-shadow"></a><span data-ttu-id="a1421-104">Z-Tiefe und Schatten</span><span class="sxs-lookup"><span data-stu-id="a1421-104">Z-depth and shadow</span></span>

!["true" Tiefe](images/elevation-shadow/depth.svg)

<span data-ttu-id="a1421-106">Das Fluent Tiefe System verwendet physischen Konzepte wie 3D Positionierung, Light, und Schatten digitaler Benutzeroberfläche neu zu erfinden kann in einer mehr geschichteten, physikalischen Umgebung wahrgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="a1421-106">The Fluent Depth System uses physical concepts like 3D positioning, light, and shadow to reinvent how digital UI can be perceived in a more layered, physical environment.</span></span> <span data-ttu-id="a1421-107">Z-Tiefe oder relativ Tiefe und Schatten gibt zwei Möglichkeiten, Tiefe in Ihre UWP-app zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="a1421-107">Z-depth, or relative depth, and shadow are two ways to incorporate depth into your UWP app.</span></span>

## <a name="what-is-z-depth"></a><span data-ttu-id="a1421-108">Was ist die Z-Tiefe?</span><span class="sxs-lookup"><span data-stu-id="a1421-108">What is z-depth?</span></span>

<span data-ttu-id="a1421-109">Z-Tiefe beträgt der Abstand zwischen zwei Oberflächen entlang der z-Achse, und es wird veranschaulicht, wie nah ein Objekt für den Betrachter ist.</span><span class="sxs-lookup"><span data-stu-id="a1421-109">Z-depth is the distance between two surfaces along the z-axis, and it illustrates how close an object is to the viewer.</span></span>

![Z-Tiefe](images/elevation-shadow/elevation.svg)

### <a name="why-use-z-depth"></a><span data-ttu-id="a1421-111">Gründe für die Verwendung von Z-Tiefe</span><span class="sxs-lookup"><span data-stu-id="a1421-111">Why use z-depth?</span></span>

<span data-ttu-id="a1421-112">In der realen Welt neigen wir auf Objekte zu konzentrieren, die näher an uns sind.</span><span class="sxs-lookup"><span data-stu-id="a1421-112">In the physical world, we tend to focus on objects that are closer to us.</span></span> <span data-ttu-id="a1421-113">Wir können digitale UI auch diese räumliche instinktiv zuweisen.</span><span class="sxs-lookup"><span data-stu-id="a1421-113">We can apply this spatial instinct to digital UI, as well.</span></span> <span data-ttu-id="a1421-114">Z. B. Wenn Sie ein Element, das näher an dem Benutzer bringen, wird der Benutzer instinktiv für das Element konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="a1421-114">For example, if you bring an element closer to the user, then the user will instinctively focus on the element.</span></span> <span data-ttu-id="a1421-115">Durch Verschieben UI-Elemente näher in z-Achse können Sie visuelle Hierarchie zwischen Objekten, damit der Benutzer den natürlichen und effizienten in Ihrer app Aufgaben erstellen.</span><span class="sxs-lookup"><span data-stu-id="a1421-115">By moving UI elements closer in z-axis, you can establish visual hierarchy between objects, helping users complete tasks naturally and efficiently in your app.</span></span> 

![Z-Tiefe im Menü "Inhalt"](images/elevation-shadow/whyelevation.svg)

<span data-ttu-id="a1421-117">Bereitstellen des aussagekräftige visuelle Hierarchie Z-Tiefe auch, treten Sie erstellen zusätzlich zu diesen Fluss nahtlos 2D, 3D Umgebungen, Skalieren von Ihrer app für alle Geräte und Formfaktoren.</span><span class="sxs-lookup"><span data-stu-id="a1421-117">In addition to providing meaningful visual hierarchy, z-depth also allows you to create experiences that flow seamlessly from 2D to 3D environments, scaling your app across all devices and form factors.</span></span> 

![Z-Tiefe, 2d, 3D](images/elevation-shadow/elevation-2d3d.svg)

### <a name="how-is-z-depth-perceived"></a><span data-ttu-id="a1421-119">Wie wird Z-Tiefe wahrgenommen?</span><span class="sxs-lookup"><span data-stu-id="a1421-119">How is z-depth perceived?</span></span>

<span data-ttu-id="a1421-120">Basierend auf wie wir Tiefe in der realen Welt wahrnehmen, folgen Sie verschiedene Techniken, die verwendet werden können, um Näherung in digitale Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a1421-120">Based on how we perceive depth in the physical world, here are several techniques that can be used to show proximity in digital UI.</span></span>

- <span data-ttu-id="a1421-121">**Skalierung** Weiter Objekte werden kleiner als näher Objekte mit der gleichen Größe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a1421-121">**Scale** Farther objects appear smaller than closer objects of the same size.</span></span> <span data-ttu-id="a1421-122">Dies ist Methode ist nur schwer zu veranschaulichen effektiv im 2D-Raum, damit es im Allgemeinen nicht empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="a1421-122">This is method is difficult to demonstrate effectively in 2D space, so it is not generally recommended.</span></span> <span data-ttu-id="a1421-123">Allerdings können Maßstab und [Schatten](#what-is-shadow) Sie eine effektive Simulation von Objekten, die näher an den Benutzer in 2D erstellen.</span><span class="sxs-lookup"><span data-stu-id="a1421-123">However, you can use scale and [shadow](#what-is-shadow) to create an effective simulation of objects moving closer to the user in 2D.</span></span>

    ![Näherung mit Skalierung](images/elevation-shadow/elevation-scale.svg)

- <span data-ttu-id="a1421-125">**Atmosphäre** Objekte können Abstand und mit einer "verrauchte" Überlagerung oder andere der Effekt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a1421-125">**Atmosphere** Objects can appear farther away and out of focus with a “smoky” overlay or other atmospheric effect.</span></span>

    ![Näherung mit Atmosphäre](images/elevation-shadow/elevation-atmosphere.svg)

- <span data-ttu-id="a1421-127">**Bewegung** Relative Geschwindigkeit kann verwendet werden, um Näherung veranschaulichen: näher Objekte verschieben schneller als entfernte Hintergrundobjekte.</span><span class="sxs-lookup"><span data-stu-id="a1421-127">**Motion** Relative speed can be used to demonstrate proximity: closer objects move more quickly than distant background objects.</span></span> <span data-ttu-id="a1421-128">Weitere Informationen zum Implementieren dieser Effekt, finden Sie unter [Parallax](../motion/parallax.md).</span><span class="sxs-lookup"><span data-stu-id="a1421-128">To learn how to implement this effect, see [Parallax](../motion/parallax.md).</span></span>

    ![Näherung mit Bewegung](images/elevation-shadow/elevation-motion.svg)

### <a name="recommendations-for-z-depth"></a><span data-ttu-id="a1421-130">Empfehlungen für die Z-Tiefe</span><span class="sxs-lookup"><span data-stu-id="a1421-130">Recommendations for z-depth</span></span>

<span data-ttu-id="a1421-131">Reduzieren Sie die Anzahl der mit erhöhten Rechten Ebenen klare visuelle Fokus bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a1421-131">Reduce the number of elevated planes to provide clear visual focus.</span></span> <span data-ttu-id="a1421-132">In den meisten Fällen ist zwei Ebenen ausreichend: eine für Vordergrund-Elemente (high Näherung) und ein weiteres für Hintergrundelemente (niedrig Näherung).</span><span class="sxs-lookup"><span data-stu-id="a1421-132">For most scenarios, two planes is enough: one for foreground items (high proximity) and another for background items (low proximity).</span></span> <span data-ttu-id="a1421-133">Wenn Sie mehrere mit erhöhten Rechten Elemente, die sich nicht überlappen verfügen, Gruppieren der gleichen Ebene (d. h. Vordergrund), um die Anzahl der Ebenen reduzieren.</span><span class="sxs-lookup"><span data-stu-id="a1421-133">If you have multiple elevated items that don’t overlap, group them the same plane (i.e., foreground) to reduce the number of planes.</span></span>

![Z-Tiefe innerhalb einer app](images/elevation-shadow/app-depth.svg)

## <a name="what-is-shadow"></a><span data-ttu-id="a1421-135">Was ist Schatten?</span><span class="sxs-lookup"><span data-stu-id="a1421-135">What is shadow?</span></span>

![Schatten](images/elevation-shadow/shadow.svg)

<span data-ttu-id="a1421-137">Schatten ist eine Möglichkeit, erhöhte Rechte wahrnehmen.</span><span class="sxs-lookup"><span data-stu-id="a1421-137">Shadow is a way to perceive elevation.</span></span> <span data-ttu-id="a1421-138">Wenn Licht über ein mit erhöhten Rechten Objekt vorhanden ist, gibt es ein Schatten auf der Oberfläche unten an.</span><span class="sxs-lookup"><span data-stu-id="a1421-138">When there is light above an elevated object, there is a shadow on the surface below.</span></span> <span data-ttu-id="a1421-139">Je höher das Objekt, die größere und weicher wird der Schatten.</span><span class="sxs-lookup"><span data-stu-id="a1421-139">The higher the object, the larger and softer the shadow becomes.</span></span> <span data-ttu-id="a1421-140">Beachten Sie, dass mit erhöhten Rechten Objekte müssen nicht Schatten verfügen über Schatten bedeuten erhöhte Rechte.</span><span class="sxs-lookup"><span data-stu-id="a1421-140">Note that elevated objects don’t need to have shadows, but shadows do indicate elevation.</span></span>

<span data-ttu-id="a1421-141">In UWP-apps sollten Schatten gut gestaltete, nicht mutige sein.</span><span class="sxs-lookup"><span data-stu-id="a1421-141">In UWP apps, shadows should be purposeful, not aesthetic.</span></span> <span data-ttu-id="a1421-142">Wenn Schatten aus den Fokus und Produktivität beeinträchtigen, beschränken Sie die Verwendung von Schatten.</span><span class="sxs-lookup"><span data-stu-id="a1421-142">If shadows detract from focus and productivity, then limit the use of shadow.</span></span>

<span data-ttu-id="a1421-143">Sie können Schatten mit dem ThemeShadow oder DropShadow APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="a1421-143">You can use shadows with either the ThemeShadow or DropShadow APIs.</span></span>

## <a name="themeshadow"></a><span data-ttu-id="a1421-144">ThemeShadow</span><span class="sxs-lookup"><span data-stu-id="a1421-144">ThemeShadow</span></span>

<span data-ttu-id="a1421-145">Die ThemeShadow, den Typ für alle XAML-Element zum Zeichnen angewendet werden kann Schatten entsprechend basierend auf X, y, Z-Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="a1421-145">The ThemeShadow type can be applied to any XAML element to draw shadows appropriately based on x, y, z coordinates.</span></span> <span data-ttu-id="a1421-146">ThemeShadow passt sich automatisch auch für andere Umgebung Spezifikationen:</span><span class="sxs-lookup"><span data-stu-id="a1421-146">ThemeShadow also automatically adjusts for other environmental specifications:</span></span>

- <span data-ttu-id="a1421-147">Änderungen der Beleuchtung, Benutzer Design, den app-Umgebung und Shell anpasst.</span><span class="sxs-lookup"><span data-stu-id="a1421-147">Adapts to changes in lighting, user theme, app environment, and shell.</span></span>
- <span data-ttu-id="a1421-148">Schatten Elemente automatisch basierend auf ihrer erhöhte Rechte.</span><span class="sxs-lookup"><span data-stu-id="a1421-148">Shadows elements automatically based on their elevation.</span></span>
- <span data-ttu-id="a1421-149">Behält Elemente synchronisieren, beim Bewegen und erhöhte Rechte zu ändern.</span><span class="sxs-lookup"><span data-stu-id="a1421-149">Keeps elements in sync as they move and change elevation.</span></span>
- <span data-ttu-id="a1421-150">Behält Schatten konsistent im gesamten und Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="a1421-150">Keeps shadows consistent throughout and across applications.</span></span>

<span data-ttu-id="a1421-151">Hier sind Beispiele für ThemeShadow an verschiedenen rechteerweiterungen mit der helle und dunkle Designs:</span><span class="sxs-lookup"><span data-stu-id="a1421-151">Here are examples of ThemeShadow at different elevations with the light and dark themes:</span></span>

![Intelligente Schatten mit hellem Design](images/elevation-shadow/smartshadow-light.svg)

![Intelligente Schatten mit dunklem Design](images/elevation-shadow/smartshadow-dark.svg)

### <a name="themeshadow-in-common-controls"></a><span data-ttu-id="a1421-154">ThemeShadow Steuerelemente gemeinsam</span><span class="sxs-lookup"><span data-stu-id="a1421-154">ThemeShadow in common controls</span></span>

<span data-ttu-id="a1421-155">Die folgenden allgemeinen Steuerelemente verwenden automatisch ThemeShadow zum Umwandeln von Schatten:</span><span class="sxs-lookup"><span data-stu-id="a1421-155">The following common controls will automatically use ThemeShadow to cast shadows:</span></span>

- [<span data-ttu-id="a1421-156">Dialogfelder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="a1421-156">Dialogs and flyouts</span></span>](../controls-and-patterns/dialogs.md)
- [<span data-ttu-id="a1421-157">NavigationView</span><span class="sxs-lookup"><span data-stu-id="a1421-157">NavigationView</span></span>](../controls-and-patterns/navigationview.md)
- [<span data-ttu-id="a1421-158">Medientransport-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="a1421-158">Media transport control</span></span>](../controls-and-patterns/media-playback.md)
- [<span data-ttu-id="a1421-159">Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="a1421-159">Context menu</span></span>](../controls-and-patterns/menus.md)
- [<span data-ttu-id="a1421-160">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="a1421-160">Command bar</span></span>](../controls-and-patterns/app-bars.md)
- <span data-ttu-id="a1421-161">[AutoVorschlagen](../controls-and-patterns/auto-suggest-box.md), [ComboBox](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [Kalender/Datum/Uhrzeit Ordnerauswahl](../controls-and-patterns/date-and-time.md) [QuickInfo](../controls-and-patterns/tooltips.md)</span><span class="sxs-lookup"><span data-stu-id="a1421-161">[AutoSuggest](../controls-and-patterns/auto-suggest-box.md), [ComboBox](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [Calendar/Date/Time pickers](../controls-and-patterns/date-and-time.md), [Tooltip](../controls-and-patterns/tooltips.md)</span></span>
- [<span data-ttu-id="a1421-162">Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="a1421-162">Access keys</span></span>](../input/access-keys.md)

### <a name="themeshadow-in-popups"></a><span data-ttu-id="a1421-163">ThemeShadow Popups</span><span class="sxs-lookup"><span data-stu-id="a1421-163">ThemeShadow in Popups</span></span>

<span data-ttu-id="a1421-164">ThemeShadow wandelt automatisch Schatten, wenn für alle XAML-Element in einem [Popup](/uwp/api/windows.ui.xaml.controls.primitives.popup)angewendet.</span><span class="sxs-lookup"><span data-stu-id="a1421-164">ThemeShadow automatically casts shadows when applied to any XAML element in a [Popup](/uwp/api/windows.ui.xaml.controls.primitives.popup).</span></span> <span data-ttu-id="a1421-165">Es wird Schatten auf den Inhalt des app-Hintergrund hinter es und alle anderen geöffneten Popups darunter umwandeln.</span><span class="sxs-lookup"><span data-stu-id="a1421-165">It will cast shadows on the app background content behind it and any other open Popups below it.</span></span>

<span data-ttu-id="a1421-166">Um ThemeShadow mit Popups zu verwenden, verwenden die `Shadow` -Eigenschaft verwenden, um eine ThemeShadow auf ein XAML-Element angewendet.</span><span class="sxs-lookup"><span data-stu-id="a1421-166">To use ThemeShadow with Popups, use the `Shadow` property to apply a ThemeShadow to a XAML element.</span></span> <span data-ttu-id="a1421-167">Anschließend Erhöhen des Elements von anderen Elementen dahinter, z. B. die Z-Komponente von der `Translation` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a1421-167">Then, elevate the element from other elements behind it, for example by using the z component of the `Translation` property.</span></span>
<span data-ttu-id="a1421-168">Für die meisten Popup-UI ist die empfohlene erhöhte Rechte relativ zu den Inhalt des app-Hintergrund 32 effektiven Pixeln.</span><span class="sxs-lookup"><span data-stu-id="a1421-168">For most Popup UI, the recommended default elevation relative to the app background content is 32 effective pixels.</span></span>

<span data-ttu-id="a1421-169">Dieses Beispiel zeigt ein Rechteck in einem Popup scheinbar einen Schatten auf den Inhalt des app-Hintergrund und alle anderen Popups dahinter:</span><span class="sxs-lookup"><span data-stu-id="a1421-169">This example shows a Rectangle in a Popup casting a shadow onto the app background content and any other Popups behind it:</span></span>

```xaml
<Popup>
    <Rectangle x:Name="PopupRectangle" Fill="White" Height="48" Width="96">
        <Rectangle.Shadow>
            <ThemeShadow />
        </Rectangle.Shadow>
    </Rectangle>
</Popup>
```

```csharp
// Elevate the rectangle by 32px
PopupRectangle.Translation += new Vector3(0, 0, 32);
```

![Schatten Codebeispiels](images/elevation-shadow/smartshadow-example.svg)

### <a name="themeshadow-in-other-elements"></a><span data-ttu-id="a1421-171">ThemeShadow in anderen Elementen</span><span class="sxs-lookup"><span data-stu-id="a1421-171">ThemeShadow in other elements</span></span>

<span data-ttu-id="a1421-172">Um einen Schatten aus einem XAML-Element umgewandelt, die nicht in einem Popup ist, müssen Sie explizit angeben die anderen Elementen, die den Schatten in empfangen können die `ThemeShadow.Receivers` Auflistung.</span><span class="sxs-lookup"><span data-stu-id="a1421-172">To cast a shadow from a XAML element that isn't in a Popup, you must explicitly specify the other elements that can receive the shadow in the `ThemeShadow.Receivers` collection.</span></span>

<span data-ttu-id="a1421-173">Dieses Beispiel zeigt zwei Schaltflächen, die auf einem Raster hinter sie Schatten werfen:</span><span class="sxs-lookup"><span data-stu-id="a1421-173">This example shows two Buttons that cast shadows onto a Grid behind them:</span></span>

```xaml
<Grid x:Name="BackgroundGrid" Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.Resources>
        <ThemeShadow x:Name="SharedShadow" />
    </Grid.Resources>

    <Button x:Name="Button1" Content="Button 1" Shadow="{StaticResource SharedShadow}" Margin="10" />

    <Button x:Name="Button2" Content="Button 2" Shadow="{StaticResource SharedShadow}" Margin="120" />
</Grid>
```

```csharp
/// Add BackgroundGrid as a shadow receiver and elevate the casting buttons above it
SharedShadow.Receivers.Add(BackgroundGrid);

Button1.Translation += new Vector3(0, 0, 16);
Button2.Translation += new Vector3(0, 0, 32);
```

### <a name="performance-best-practices-for-themeshadow"></a><span data-ttu-id="a1421-174">Bewährte Methoden für die ThemeShadow Leistung</span><span class="sxs-lookup"><span data-stu-id="a1421-174">Performance best practices for ThemeShadow</span></span>

1. <span data-ttu-id="a1421-175">Die Anzahl der benutzerdefinierten Empfänger Elemente auf das minimum zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="a1421-175">Limit the number of custom receiver elements to the minimum necessary.</span></span> 

2. <span data-ttu-id="a1421-176">Wenn mehrere Empfänger Elemente am gleichen EoP befinden sich dann versuchen Sie, diese kombinieren, indem ein einzelnes übergeordnetes Element stattdessen abzielen.</span><span class="sxs-lookup"><span data-stu-id="a1421-176">If multiple receiver elements are at the same elevation then try to combine them by targeting a single parent element instead.</span></span>

3. <span data-ttu-id="a1421-177">Wenn mehrere Elemente die gleiche Art von Schatten auf die gleiche Empfänger Elemente umgewandelt werden den Schatten als freigegebene Ressource hinzufügen und wiederzuverwenden.</span><span class="sxs-lookup"><span data-stu-id="a1421-177">If multiple elements will cast the same type of shadow onto the same receiver elements then add the shadow as a shared resource and reuse it.</span></span>

## <a name="drop-shadow"></a><span data-ttu-id="a1421-178">Schlagschatten</span><span class="sxs-lookup"><span data-stu-id="a1421-178">Drop shadow</span></span>

<span data-ttu-id="a1421-179">DropShadow reagiert nicht automatisch auf ihrer Umgebung und keine Lichtquellen.</span><span class="sxs-lookup"><span data-stu-id="a1421-179">DropShadow is not automatically responsive to its environment and does not use light sources.</span></span> <span data-ttu-id="a1421-180">Sehen Sie beispielsweise Implementierungen, die [DropShadow-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.composition.dropshadow).</span><span class="sxs-lookup"><span data-stu-id="a1421-180">For example implementations, see the [DropShadow Class](https://docs.microsoft.com/uwp/api/windows.ui.composition.dropshadow).</span></span>

## <a name="which-shadow-should-i-use"></a><span data-ttu-id="a1421-181">Welche Schatten sollte ich verwenden?</span><span class="sxs-lookup"><span data-stu-id="a1421-181">Which shadow should I use?</span></span>

| <span data-ttu-id="a1421-182">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a1421-182">Property</span></span> | <span data-ttu-id="a1421-183">ThemeShadow</span><span class="sxs-lookup"><span data-stu-id="a1421-183">ThemeShadow</span></span> | <span data-ttu-id="a1421-184">DropShadow</span><span class="sxs-lookup"><span data-stu-id="a1421-184">DropShadow</span></span> |
| - | - | - | - |
| **<span data-ttu-id="a1421-185">Min SDK</span><span class="sxs-lookup"><span data-stu-id="a1421-185">Min SDK</span></span>** | <span data-ttu-id="a1421-186">RS5</span><span class="sxs-lookup"><span data-stu-id="a1421-186">RS5</span></span> | <span data-ttu-id="a1421-187">14393</span><span class="sxs-lookup"><span data-stu-id="a1421-187">14393</span></span> |
| **<span data-ttu-id="a1421-188">Anpassungsfähigkeit</span><span class="sxs-lookup"><span data-stu-id="a1421-188">Adaptability</span></span>** | <span data-ttu-id="a1421-189">Ja</span><span class="sxs-lookup"><span data-stu-id="a1421-189">Yes</span></span> | <span data-ttu-id="a1421-190">Nein</span><span class="sxs-lookup"><span data-stu-id="a1421-190">No</span></span> |
| **<span data-ttu-id="a1421-191">Anpassung</span><span class="sxs-lookup"><span data-stu-id="a1421-191">Customization</span></span>** | <span data-ttu-id="a1421-192">Nein</span><span class="sxs-lookup"><span data-stu-id="a1421-192">No</span></span> | <span data-ttu-id="a1421-193">Ja</span><span class="sxs-lookup"><span data-stu-id="a1421-193">Yes</span></span> |
| **<span data-ttu-id="a1421-194">Lichtquelle</span><span class="sxs-lookup"><span data-stu-id="a1421-194">Light source</span></span>** | <span data-ttu-id="a1421-195">Automatische (globale standardmäßig können aber überschreiben pro app)</span><span class="sxs-lookup"><span data-stu-id="a1421-195">Automatic (global by default, but can override per app)</span></span> | <span data-ttu-id="a1421-196">Keine</span><span class="sxs-lookup"><span data-stu-id="a1421-196">None</span></span> |
| **<span data-ttu-id="a1421-197">In 3D Umgebungen unterstützt</span><span class="sxs-lookup"><span data-stu-id="a1421-197">Supported in 3D environments</span></span>** | <span data-ttu-id="a1421-198">Ja</span><span class="sxs-lookup"><span data-stu-id="a1421-198">Yes</span></span> | <span data-ttu-id="a1421-199">Nein</span><span class="sxs-lookup"><span data-stu-id="a1421-199">No</span></span> |

- <span data-ttu-id="a1421-200">Im Allgemeinen empfehlen wir die Verwendung von ThemeShadow, die automatisch an seiner Umgebung anpasst.</span><span class="sxs-lookup"><span data-stu-id="a1421-200">Generally, we recommend using ThemeShadow, which adapts automatically to its environment.</span></span>
- <span data-ttu-id="a1421-201">Wenn Sie Szenarien für benutzerdefinierte Schatten erweiterte haben, verwenden Sie DropShadow, wodurch ein stärker angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="a1421-201">If you have more advanced scenarios for custom shadows, then use DropShadow, which allows for greater customization.</span></span>
- <span data-ttu-id="a1421-202">Für die Rückwärtsnavigation Kompatibilität zu gewährleisten, DropShadow verwenden.</span><span class="sxs-lookup"><span data-stu-id="a1421-202">For backwards compatibility, use DropShadow.</span></span>
- <span data-ttu-id="a1421-203">Bedenken hinsichtlich der Leistung die Anzahl der Schatten oder DropShadow verwenden.</span><span class="sxs-lookup"><span data-stu-id="a1421-203">For concerns about performance, limit the number of shadows, or use DropShadow.</span></span>
- <span data-ttu-id="a1421-204">Verwenden Sie auf HMDs "true" 3D ThemeShadow.</span><span class="sxs-lookup"><span data-stu-id="a1421-204">On HMDs in true 3D, use ThemeShadow.</span></span> <span data-ttu-id="a1421-205">Da DropShadow mit einem bestimmten Versatz von des visuellen Elements zeichnet, die sie von der Seite, übergeordnet ist sieht es wie er im Raum verankert ist.</span><span class="sxs-lookup"><span data-stu-id="a1421-205">Since DropShadow draws at a specified offset from the visual it is parented to, from the side, it will look like it's floating in space.</span></span> <span data-ttu-id="a1421-206">Andererseits, ist ThemeShadow auf die visuellen Elemente als Empfänger definiert gerendert.</span><span class="sxs-lookup"><span data-stu-id="a1421-206">On the other hand, ThemeShadow is rendered on top of the visuals defined as receivers.</span></span>
