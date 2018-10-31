---
author: Karl-Bridge-Microsoft
Description: Ink tools described
title: Steuerelemente für Freihandeingaben
label: Inking Controls
template: detail.hbs
ms.author: kbridge
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 97eae5f3-c16b-4aa5-b4a1-dd892cf32ead
ms.localizationpriority: medium
ms.openlocfilehash: ed358f88470dfe1ba1c48cd3daf1ed54135ed987
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5860393"
---
# <a name="inking-controls"></a><span data-ttu-id="ec732-103">Steuerelemente für Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="ec732-103">Inking controls</span></span>



<span data-ttu-id="ec732-104">Es gibt zwei verschiedene Steuerelemente, die die Freihandeingabe in Apps in der universellen Windows-Plattform (UWP) ermöglichen: [InkCanvas](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx) und [InkToolbar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx).</span><span class="sxs-lookup"><span data-stu-id="ec732-104">There are two different controls that facilitate inking in Universal Windows Platform (UWP) apps: [InkCanvas](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx) and [InkToolbar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx).</span></span>

<span data-ttu-id="ec732-105">Das InkCanvas-Steuerelement rendert Stifteingaben entweder als Freihandstrich (mit Standardeinstellungen für Farbe und Breite) oder als Radierstrich.</span><span class="sxs-lookup"><span data-stu-id="ec732-105">The InkCanvas control renders pen input as either an ink stroke (using default settings for color and thickness) or an erase stroke.</span></span> <span data-ttu-id="ec732-106">Dieses Steuerelement ist eine transparente Überlagerung, die keine integrierte Benutzeroberfläche zum Ändern der Standardeigenschaften von Freihandstrichen enthält.</span><span class="sxs-lookup"><span data-stu-id="ec732-106">This control is a transparent overlay that doesn't include any built-in UI for changing the default ink stroke properties.</span></span>

> [!NOTE]
> <span data-ttu-id="ec732-107">„InkCanvas“ kann zur Unterstützung ähnlicher Funktionen für Maus- und Toucheingabe konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-107">InkCanvas can be configured to support similar functionality for both mouse and touch input.</span></span>

<span data-ttu-id="ec732-108">Da das InkCanvas-Steuerelement keine Unterstützung für das Ändern der Standardeinstellungen von Freihandstrichen enthält, kann es mit einem InkToolbar-Steuerelement kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-108">As the InkCanvas control does not include support for changing the default ink stroke settings, it can be paired with an InkToolbar control.</span></span> <span data-ttu-id="ec732-109">Das InkToolbar-Steuerelement enthält eine anpassbare und erweiterbare Sammlung von Schaltflächen, die Features für Freihandeingaben in einem verknüpften InkCanvas-Steuerelement aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ec732-109">The InkToolbar contains a customizable and extensible collection of buttons that activate ink-related features in an associated InkCanvas.</span></span>

<span data-ttu-id="ec732-110">Das InkToolbar-Steuerelement enthält standardmäßig Schaltflächen zum Zeichnen, Löschen, Hervorheben sowie zum Anzeigen eines Lineals.</span><span class="sxs-lookup"><span data-stu-id="ec732-110">By default, the InkToolbar includes buttons for drawing, erasing, highlighting, and displaying a ruler.</span></span> <span data-ttu-id="ec732-111">Abhängig vom Feature werden in einem Flyout weitere Einstellungen und Befehle bereitgestellt, beispielsweise für Freihandfarbe, Strichstärke und das Löschen aller Freihandeingaben.</span><span class="sxs-lookup"><span data-stu-id="ec732-111">Depending on the feature, other settings and commands, such as ink color, stroke thickness, erase all ink, are provided in a flyout.</span></span>

> [!NOTE]
> <span data-ttu-id="ec732-112">„InkToolbar“ unterstützt Stift- und Mauseingaben und kann zur Erkennung von Toucheingaben konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-112">InkToolbar supports pen and mouse input and can be configured to recognize touch input.</span></span>

<img src="images/ink-tools-invoked-toolbar.png" width="300" alt="InkToolbar palette flyout">

> <span data-ttu-id="ec732-113">**Wichtige APIs**: [InkCanvas-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx), [InkToolbar-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx), [InkPresenter-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx), [Windows.UI.Input.Inking](https://msdn.microsoft.com/library/windows/apps/br208524)</span><span class="sxs-lookup"><span data-stu-id="ec732-113">**Important APIs**: [InkCanvas class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx), [InkToolbar class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx), [InkPresenter class](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx), [Windows.UI.Input.Inking](https://msdn.microsoft.com/library/windows/apps/br208524)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="ec732-114">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="ec732-114">Is this the right control?</span></span>

<span data-ttu-id="ec732-115">Verwenden Sie das InkCanvas-Steuerelement, wenn Sie in Ihrer App einfache Freihandfeatures ohne Freihandeinstellungen für den Benutzer bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="ec732-115">Use the InkCanvas when you need to enable basic inking features in your app without providing any ink settings to the user.</span></span>

<span data-ttu-id="ec732-116">Standardmäßig werden Striche als Freihandeingabe gerendert, wenn die Stiftspitze (ein schwarzer Kugelschreiber mit einer Stärke von 2 Pixeln) verwendet wird, und als Radierer, wenn die Radiergummispitze verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ec732-116">By default, strokes are rendered as ink when using the pen tip (a black ballpoint pen with a thickness of 2 pixels) and as an eraser when using the eraser tip.</span></span> <span data-ttu-id="ec732-117">Falls keine Radiergummispitze vorhanden ist, kann das InkCanvas-Steuerelement so konfiguriert werden, dass Eingaben mit der Stiftspitze wie Radierstriche behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-117">If an eraser tip is not present, the InkCanvas can be configured to process input from the pen tip as an erase stroke.</span></span>

<span data-ttu-id="ec732-118">Kombinieren Sie das InkCanvas-Steuerelement mit einem InkToolbar-Steuerelement, um eine Benutzeroberfläche zum Aktivieren von Freihandfeatures und Festlegen grundlegender Freihandeigenschaften wie Strichgröße, Farbe und Form der Stiftspitze bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="ec732-118">Pair the InkCanvas with an InkToolbar to provide a UI for activating ink features and setting basic ink properties such as stroke size, color, and shape of the pen tip.</span></span>

> [!NOTE] 
> <span data-ttu-id="ec732-119">Verwenden Sie das zugrunde liegende [InkPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx)-Objekt, wenn Sie umfassendere Anpassungen am Rendering von Freihandeingaben für ein InkCanvas-Steuerelement vornehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="ec732-119">For more extensive customization of ink stroke rendering on an InkCanvas, use the underlying [InkPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx) object.</span></span>

## <a name="examples"></a><span data-ttu-id="ec732-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ec732-120">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="ec732-121">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="ec732-121">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="ec732-122">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/InkCanvas">die App zu öffnen und InkCanvas in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="ec732-122">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/InkCanvas">open the app and see the InkCanvas in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="ec732-123">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="ec732-123">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="ec732-124">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="ec732-124">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

**<span data-ttu-id="ec732-125">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ec732-125">Microsoft Edge</span></span>**

<span data-ttu-id="ec732-126">Microsoft Edge verwendet „InkCanvas” und „InkToolbar” für **Webseitennotizen**.</span><span class="sxs-lookup"><span data-stu-id="ec732-126">Microsoft Edge uses the InkCanvas and InkToolbar for **Web Notes**.</span></span>  
![Das InkCanvas-Steuerelement wird für Freihandeingaben in Microsoft Edge verwendet.](images/ink-tools-edge.png)

**<span data-ttu-id="ec732-128">Windows Ink-Arbeitsbereich</span><span class="sxs-lookup"><span data-stu-id="ec732-128">Windows Ink Workspace</span></span>**

<span data-ttu-id="ec732-129">Die InkCanvas- und InkToolbar-Steuerelemente werden auch für den **Skizzenblock** und **Bildschirmskizzen** im **Windows Ink-Arbeitsbereich** verwendet.</span><span class="sxs-lookup"><span data-stu-id="ec732-129">The InkCanvas and InkToolbar are also used for both **Sketchpad** and **Screen sketch** in the **Windows Ink Workspace**.</span></span>  
![InkToolbar-Steuerelement im Windows Ink-Arbeitsbereich](images/ink-tools-ink-workspace.png)

## <a name="create-an-inkcanvas-and-inktoolbar"></a><span data-ttu-id="ec732-131">Erstellen eines InkCanvas- und InkToolbar-Steuerelements</span><span class="sxs-lookup"><span data-stu-id="ec732-131">Create an InkCanvas and InkToolbar</span></span>

<span data-ttu-id="ec732-132">Zum Hinzufügen eines InkCanvas-Steuerelements zu Ihrer App ist nur eine Markupzeile erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ec732-132">Adding an InkCanvas to your app requires just one line of markup:</span></span>

```xaml
<InkCanvas x:Name=“myInkCanvas”/>
```

> [!NOTE]
> <span data-ttu-id="ec732-133">Ausführliche Informationen zur Anpassung von „InkCanvas” mit „InkPresenter” finden Sie im Artikel [Zeichen- und Eingabestiftinteraktionen in UWP-Apps](http://windowsstyleguide/input/pen-and-stylus-interactions/).</span><span class="sxs-lookup"><span data-stu-id="ec732-133">For detailed InkCanvas customization using InkPresenter, see the ["Pen and stylus interactions in UWP apps"](http://windowsstyleguide/input/pen-and-stylus-interactions/) article.</span></span>

<span data-ttu-id="ec732-134">Das InkToolbar-Steuerelement muss in Verbindung mit einem InkCanvas-Steuerelement verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-134">The InkToolbar control must be used in conjunction with an InkCanvas.</span></span> <span data-ttu-id="ec732-135">Zum Einbinden eines InkToolbar-Steuerelements (mit allen integrierten Tools) in Ihre App ist nur eine zusätzliche Markupzeile erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ec732-135">Incorporating an InkToolbar (with all built-in tools) into your app requires one additional line of markup:</span></span>

 ```xaml
<InkToolbar TargetInkCanvas=“{x:Bind myInkCanvas}”/>
 ```

<span data-ttu-id="ec732-136">Dadurch wird das folgende InkToolbar-Steuerelement angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ec732-136">This displays the following InkToolbar:</span></span>
<img src="images/ink-tools-uninvoked-toolbar.png" width="250" alt="Basic InkToolbar">

### <a name="built-in-buttons"></a><span data-ttu-id="ec732-137">Integrierte Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="ec732-137">Built-in buttons</span></span>

<span data-ttu-id="ec732-138">Das InkToolbar-Steuerelement enthält die folgenden integrierten Schaltflächen:</span><span class="sxs-lookup"><span data-stu-id="ec732-138">The InkToolbar includes the following built-in buttons:</span></span>

**<span data-ttu-id="ec732-139">Stifte</span><span class="sxs-lookup"><span data-stu-id="ec732-139">Pens</span></span>**

- <span data-ttu-id="ec732-140">Kugelschreiber – zeichnet mit einer runden Stiftspitze einen durchgehenden, undurchsichtigen Strich.</span><span class="sxs-lookup"><span data-stu-id="ec732-140">Ballpoint pen - draws a solid, opaque stroke with a circle pen tip.</span></span> <span data-ttu-id="ec732-141">Die Strichgröße hängt vom erkannten Stiftdruck ab.</span><span class="sxs-lookup"><span data-stu-id="ec732-141">The stroke size is dependent on the pen pressure detected.</span></span>
- <span data-ttu-id="ec732-142">Bleistift – zeichnet mit einer runden Stiftspitze einen auslaufenden halbtransparenten Strich mit Textur (nützlich für überlagerte Schattierungseffekte).</span><span class="sxs-lookup"><span data-stu-id="ec732-142">Pencil - draws a soft-edged, textured, and semi-transparent stroke (useful for layered shading effects) with a circle pen tip.</span></span> <span data-ttu-id="ec732-143">Die Strichfarbe (Dunkelheit) hängt vom erkannten Stiftdruck ab.</span><span class="sxs-lookup"><span data-stu-id="ec732-143">The stroke color (darkness) is dependent on the pen pressure detected.</span></span>
- <span data-ttu-id="ec732-144">Textmarker – zeichnet mit einer rechteckigen Stiftspitze einen halbtransparenten Strich.</span><span class="sxs-lookup"><span data-stu-id="ec732-144">Highlighter – draws a semi-transparent stroke with a rectangle pen tip.</span></span>

<span data-ttu-id="ec732-145">Sie können sowohl die Farbpalette als auch die Größenattribute (Mindest-, Höchst- und Standardwerte) im Flyout für jeden Stift anpassen.</span><span class="sxs-lookup"><span data-stu-id="ec732-145">You can customize both the color palette and size attributes (min, max, default) in the flyout for each pen.</span></span>

**<span data-ttu-id="ec732-146">Tool</span><span class="sxs-lookup"><span data-stu-id="ec732-146">Tool</span></span>**

- <span data-ttu-id="ec732-147">Radierer – löscht alle Freihandstriche, die berührt werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-147">Eraser – deletes any ink stroke touched.</span></span> <span data-ttu-id="ec732-148">Beachten Sie, dass der gesamte Freihandstrich gelöscht wird, nicht nur der Teil unter dem Radiererstrich.</span><span class="sxs-lookup"><span data-stu-id="ec732-148">Note that the entire ink stroke is deleted, not just the portion under the eraser stroke.</span></span>

**<span data-ttu-id="ec732-149">Ein-/Ausschalten</span><span class="sxs-lookup"><span data-stu-id="ec732-149">Toggle</span></span>**

- <span data-ttu-id="ec732-150">Lineal – blendet das Lineal ein oder aus.</span><span class="sxs-lookup"><span data-stu-id="ec732-150">Ruler – shows or hides the ruler.</span></span> <span data-ttu-id="ec732-151">Beim Zeichnen in der Nähe des Linealrands wird der Freihandstrich am Lineal ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="ec732-151">Drawing near the ruler edge causes the ink stroke to snap to the ruler.</span></span>  
 ![Dem InkToolbar-Steuerelement zugeordnetes visuelles Linealelement](images/inking-tools-ruler.png)

<span data-ttu-id="ec732-153">Obwohl dies die Standardkonfiguration ist, haben Sie die vollständige Kontrolle über die integrierten Schaltflächen, die im InkToolbar-Steuerelement für Ihre App enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="ec732-153">Although this is the default configuration, you have complete control over which built-in buttons are included in the InkToolbar for your app.</span></span>

### <a name="custom-buttons"></a><span data-ttu-id="ec732-154">Benutzerdefinierte Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="ec732-154">Custom buttons</span></span>

<span data-ttu-id="ec732-155">Das InkToolbar-Steuerelement besteht aus zwei unterschiedlichen Gruppen von Schaltflächentypen:</span><span class="sxs-lookup"><span data-stu-id="ec732-155">The InkToolbar consists of two distinct groups of button types:</span></span>

1. <span data-ttu-id="ec732-156">Eine Gruppe von „Toolschaltflächen“ mit den integrierten Schaltflächen zum Zeichnen, Radieren und Hervorheben.</span><span class="sxs-lookup"><span data-stu-id="ec732-156">A group of "tool" buttons containing the built-in drawing, erasing, and highlighting buttons.</span></span> <span data-ttu-id="ec732-157">Hier werden benutzerdefinierte Stifte und Tools hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ec732-157">Custom pens and tools are added here.</span></span>
> [!NOTE]
> <span data-ttu-id="ec732-158">Die ausgewählten Features schließen sich gegenseitig aus.</span><span class="sxs-lookup"><span data-stu-id="ec732-158">Feature selection is mutually exclusive.</span></span>

2. <span data-ttu-id="ec732-159">Eine Gruppe von „Umschaltflächen“ mit der integrierten Linealschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ec732-159">A group of "toggle" buttons containing the built-in ruler button.</span></span> <span data-ttu-id="ec732-160">Hier werden benutzerdefinierte Umschaltflächen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ec732-160">Custom toggles are added here.</span></span>
> [!NOTE]
> <span data-ttu-id="ec732-161">Die Features schließen sich nicht gegenseitig aus und können gleichzeitig mit anderen aktiven Tools verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-161">Features are not mutually exclusive and can be used concurrently with other active tools.</span></span>

<span data-ttu-id="ec732-162">Je nach Anwendung und erforderlicher Freihandfunktion können Sie dem InkToolbar-Steuerelement eine der folgenden Schaltflächen (die an die benutzerdefinierten Freihandfunktionen gebunden sind) hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="ec732-162">Depending on your application and the inking functionality required, you can add any of the following buttons (bound to your custom ink features) to the InkToolbar:</span></span>

- <span data-ttu-id="ec732-163">Benutzerdefinierter Stift: Ein Stift, für den die Farbpaletten- und Stiftspitzeneigenschaften der Freihandeingabe wie Form, Drehung und Größe von der Host-App definiert werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-163">Custom pen – a pen for which the ink color palette and pen tip properties, such as shape, rotation, and size, are defined by the host app.</span></span>
- <span data-ttu-id="ec732-164">Benutzerdefiniertes Tool: Ein Tool ohne Stift, das von der Host-App definiert wird.</span><span class="sxs-lookup"><span data-stu-id="ec732-164">Custom tool – a non-pen tool, defined by the host app.</span></span>
- <span data-ttu-id="ec732-165">Benutzerdefiniertes Umschalten: Legt den Zustand eines durch die App definierten Features auf „aktiviert“ oder „deaktiviert“ fest.</span><span class="sxs-lookup"><span data-stu-id="ec732-165">Custom toggle – Sets the state of an app-defined feature to on or off.</span></span> <span data-ttu-id="ec732-166">Wenn die Schaltfläche aktiviert ist, funktioniert das Feature in Verbindung mit dem aktiven Tool.</span><span class="sxs-lookup"><span data-stu-id="ec732-166">When turned on, the feature works in conjunction with the active tool.</span></span>

> [!NOTE]
> <span data-ttu-id="ec732-167">Die Anzeigereihenfolge der integrierten Schaltflächen kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-167">You cannot change the display order of the built-in buttons.</span></span> <span data-ttu-id="ec732-168">Die standardmäßige Anzeigereihenfolge lautet wie folgt: Kugelschreiber, Stift, Textmarker, Radierer und Lineal.</span><span class="sxs-lookup"><span data-stu-id="ec732-168">The default display order is: Ballpoint pen, pencil, highlighter, eraser, and ruler.</span></span> <span data-ttu-id="ec732-169">Benutzerdefinierte Stifte werden an den letzten Standardstift angefügt, benutzerdefinierte Tool-Schaltflächen werden zwischen der letzten Stiftschaltfläche und der Radiererschaltfläche hinzugefügt, und benutzerdefinierte Umschaltflächen werden nach der Linealschaltfläche hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ec732-169">Custom pens are appended to the last default pen, custom tool buttons are added between the last pen button and the eraser button and custom toggle buttons are added after the ruler button.</span></span> <span data-ttu-id="ec732-170">(Benutzerdefinierte Schaltflächen werden in der Reihenfolge hinzugefügt, in der sie angegeben werden.)</span><span class="sxs-lookup"><span data-stu-id="ec732-170">(Custom buttons are added in the order they are specified.)</span></span>

<span data-ttu-id="ec732-171">Obwohl das InkToolbar-Steuerelement ein Element auf oberster Ebene sein kann, wird es in der Regel über eine Schaltfläche oder einen Befehl für die Freihandeingabe verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="ec732-171">Although the InkToolbar can be a top level item, it is typically exposed through an “Inking” button or command.</span></span> <span data-ttu-id="ec732-172">Wir empfehlen, die Glyphe EE56 aus der Schriftart „Segoe MLD2 Assets“ als Symbol auf oberster Ebene zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec732-172">We recommend using EE56 glyph from the Segoe MLD2 Assets font as a top level icon.</span></span>

## <a name="inktoolbar-interaction"></a><span data-ttu-id="ec732-173">InkToolbar-Interaktion</span><span class="sxs-lookup"><span data-stu-id="ec732-173">InkToolbar Interaction</span></span>

<span data-ttu-id="ec732-174">Alle integrierten Stift- und Toolschaltflächen enthalten ein Flyoutmenü, in dem Freihandeigenschaften sowie die Form und Größe der Stiftspitze festgelegt werden können.</span><span class="sxs-lookup"><span data-stu-id="ec732-174">All built-in pen and tool buttons include a flyout menu where ink properties and pen tip shape and size can be set.</span></span> <span data-ttu-id="ec732-175">Eine „Erweiterungsglyphe”</span><span class="sxs-lookup"><span data-stu-id="ec732-175">An "extension glyph"</span></span> ![InkToolbar-Glyphe](images/ink-tools-glyph.png) <span data-ttu-id="ec732-177">wird auf der Schaltfläche angezeigt, um auf das Vorhandensein des Flyouts hinzuweisen.</span><span class="sxs-lookup"><span data-stu-id="ec732-177">is displayed on the button to indicate the existence of the flyout.</span></span>

<span data-ttu-id="ec732-178">Das Flyout wird angezeigt, wenn die Schaltfläche eines aktiven Tools erneut ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="ec732-178">The flyout is shown when the button of an active tool is selected again.</span></span> <span data-ttu-id="ec732-179">Wenn die Farbe oder Größe geändert wird, wird das Flyout automatisch geschlossen, und die Freihandeingabe kann fortgesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-179">When the color or size is changed, the flyout is automatically dismissed and inking can be resumed.</span></span> <span data-ttu-id="ec732-180">Für benutzerdefinierte Stifte und Tools kann das Standardflyoutmenü oder ein benutzerdefiniertes Flyoutmenü verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-180">Custom pens and tools can use the default flyout or specify a custom flyout.</span></span>

<span data-ttu-id="ec732-181">Der Radierer verfügt ebenfalls über ein Flyout mit dem Befehl **Freihand vollständig löschen**.</span><span class="sxs-lookup"><span data-stu-id="ec732-181">The eraser also has a flyout that provides the **Erase All Ink** command.</span></span>  
![InkToolbar-Steuerelement mit aufgerufenem Radierer-Flyout](images/ink-tools-erase-all-ink.png)

 <span data-ttu-id="ec732-183">Informationen zur Anpassung und Erweiterbarkeit finden Sie im [einfachen Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SimpleInk).</span><span class="sxs-lookup"><span data-stu-id="ec732-183">For information on customization and extensibility, check out [SimpleInk sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SimpleInk).</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="ec732-184">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="ec732-184">Do's and don'ts</span></span>

- <span data-ttu-id="ec732-185">Das InkCanvas-Steuerelement und die Freihandeingabe im Allgemeinen bieten bei der Verwendung eines aktiven Stifts die beste Benutzerfreundlichkeit.</span><span class="sxs-lookup"><span data-stu-id="ec732-185">The InkCanvas, and inking in general, is best experienced through an active pen.</span></span> <span data-ttu-id="ec732-186">Es wird jedoch empfohlen, die Freihandeingabe mit Maus- und Toucheingabe (einschließlich des passiven Stifts) zu unterstützen, wenn dies für Ihre App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="ec732-186">However, we recommend supporting inking with mouse and touch (including passive pen) input if required by your app.</span></span>
- <span data-ttu-id="ec732-187">Verwenden Sie ein InkToolbar-Steuerelement mit dem InkCanvas-Steuerelement, um grundlegende Freihandfeatures und -einstellungen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="ec732-187">Use an InkToolbar control with the InkCanvas to provide basic inking features and settings.</span></span> <span data-ttu-id="ec732-188">Sowohl das InkCanvas- als auch das InkToolbar-Steuerelement können programmgesteuert angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="ec732-188">Both the InkCanvas and InkToolbar can be programmatically customized.</span></span>
- <span data-ttu-id="ec732-189">Das InkToolbar-Steuerelement und die Freihandeingabe im Allgemeinen bieten bei der Verwendung eines aktiven Stifts die beste Benutzerfreundlichkeit.</span><span class="sxs-lookup"><span data-stu-id="ec732-189">The InkToolbar, and inking in general, is best experienced through an active pen.</span></span> <span data-ttu-id="ec732-190">Die Freihandeingabe mit Maus- und Toucheingabe kann aber unterstützt werden, wenn dies für Ihre App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="ec732-190">However, inking with mouse and touch can be supported if required by your app.</span></span>
- <span data-ttu-id="ec732-191">Bei Unterstützung der Freihandfunktion per Toucheingabe wird empfohlen, das Symbol ED5F aus der Schriftart „Segoe MLD2 Assets” für die Umschaltfläche mit einer QuickInfo „Schreiben durch Berühren” zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec732-191">If supporting inking with touch input, we recommend using the ED5F icon from the Segoe MLD2 Assets font for the toggle button, with a “Touch writing” tooltip.</span></span>
- <span data-ttu-id="ec732-192">Für die Bereitstellung der Strichauswahl empfehlen wir die Verwendung des EF20-Symbols aus der Schriftart „Segoe MLD2 Assets“ für die Toolschaltfläche, mit einer QuickInfo „Auswahltool“.</span><span class="sxs-lookup"><span data-stu-id="ec732-192">If providing stroke selection, we recommend using the EF20 icon from the Segoe MLD2 Assets font for the tool button, with a “Selection tool” tooltip.</span></span>
- <span data-ttu-id="ec732-193">Wenn Sie mehrere InkCanvas-Steuerelemente verwenden, empfehlen wir die Verwendung eines einzelnen InkToolbar-Steuerelements zum Steuern der Freihandeingabe in allen Zeichenbereichen.</span><span class="sxs-lookup"><span data-stu-id="ec732-193">If using more than one InkCanvas, we recommend using a single InkToolbar to control inking across canvases.</span></span>
- <span data-ttu-id="ec732-194">Für eine optimale Leistung empfehlen wir, das Standardflyout zu ändern, anstatt ein benutzerdefiniertes Flyout für standardmäßige und benutzerdefinierte Tools zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ec732-194">For best performance, we recommend altering the default flyout rather than creating a custom one for both default and custom tools.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="ec732-195">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="ec732-195">Get the sample code</span></span>

- <span data-ttu-id="ec732-196">[einfachen Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SimpleInk) – Erläutert acht Szenarien im Zusammenhang mit den Anpassungs- und Erweiterbarkeitsfunktionen der InkCanvas- und InkToolbar-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="ec732-196">[SimpleInk sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SimpleInk) - Demonstrates 8 scenarios around the customization and extensibility capabilities of the InkCanvas and InkToolbar controls.</span></span> <span data-ttu-id="ec732-197">Jedes Szenario bietet einen allgemeinen Überblick über gängige Situationen bei der Freihandeingabe und Steuerelementimplementierungen.</span><span class="sxs-lookup"><span data-stu-id="ec732-197">Each scenario provides basic guidance on common inking situations and control implementations.</span></span>
- <span data-ttu-id="ec732-198">[Komplexes Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ComplexInk) – Erläutert komplexere Szenarien für Freihandeingaben.</span><span class="sxs-lookup"><span data-stu-id="ec732-198">[ComplexInk sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ComplexInk) - Demonstrates more advanced inking scenarios.</span></span>
- <span data-ttu-id="ec732-199">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ec732-199">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="ec732-200">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="ec732-200">Related articles</span></span>

- [<span data-ttu-id="ec732-201">Zeichen- und Eingabestiftinteraktionen in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="ec732-201">Pen and stylus interactions in UWP apps</span></span>](http://windowsstyleguide/input/pen-and-stylus-interactions/)
- [<span data-ttu-id="ec732-202">Erkennen von Freihandstrichen</span><span class="sxs-lookup"><span data-stu-id="ec732-202">Recognize ink strokes</span></span>](http://windowsstyleguide/input/convert-ink-to-text/)
- [<span data-ttu-id="ec732-203">Speichern und Abrufen von Freihandstrichen</span><span class="sxs-lookup"><span data-stu-id="ec732-203">Store and retrieve ink strokes</span></span>](http://windowsstyleguide/input/save-and-load-ink/)
