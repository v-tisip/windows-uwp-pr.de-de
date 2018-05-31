---
author: serenaz
Description: An overview of the universal design features that are included in every UWP app to help you build apps that scale beautifully across a range of devices.
title: Einführung in das UWP-App-Design (Universelle Windows-Plattform) (Windows-Apps)
ms.assetid: 50A5605E-3A91-41DB-800A-9180717C1E86
ms.author: sezhen
ms.date: 12/13/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: d0527866777c7b5dbbc10697bb313d664f4555fa
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1817278"
---
#  <a name="introduction-to-uwp-app-design"></a><span data-ttu-id="6c2c1-103">Einführung in das UWP-App-Design</span><span class="sxs-lookup"><span data-stu-id="6c2c1-103">Introduction to UWP app design</span></span>

<span data-ttu-id="6c2c1-104">Der universelle Windows-Plattform (UWP)-Designleitfaden ist eine Ressource, um ansprechende, optimierte Apps zu entwerfen und erstellen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-104">The Universal Windows Platform (UWP) design guidance is a resource to help you design and build beautiful, polished apps.</span></span>

<span data-ttu-id="6c2c1-105">Es ist keine Liste von Vorschriften, sondern ein lebendiges Dokument, das entwickelt wurde, um sich entsprechend unseres [Fluent Design-Systems](../fluent-design-system/index.md) sowie der Bedürfnisse unserer App-Entwicklungs-Community zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-105">It's not a list of prescriptive rules - it's a living document, designed to adapt to our evolving [Fluent Design System](../fluent-design-system/index.md) as well as the needs of our app-building community.</span></span>

<span data-ttu-id="6c2c1-106">Diese Einführung bietet einen Überblick über die universellen Designfunktionen, die in jeder UWP-Apps enthalten sind. Es hilft Ihnen, Benutzeroberflächen (UIs) zu erstellen, die sich über eine Vielzahl von Geräten wunderbar skalieren lassen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-106">This introduction provides an overview of the universal design features that are included in every UWP app, helping you build user interfaces (UI) that scale beautifully across a range of devices.</span></span>

## <a name="video-summary"></a><span data-ttu-id="6c2c1-107">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="6c2c1-107">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Blogs/One-Dev-Minute/Designing-Universal-Windows-Platform-apps/player]

## <a name="effective-pixels-and-scaling"></a><span data-ttu-id="6c2c1-108">Effektive Pixel und Skalierung</span><span class="sxs-lookup"><span data-stu-id="6c2c1-108">Effective pixels and scaling</span></span>

<span data-ttu-id="6c2c1-109">UWP-Apps passen automatisch die Größe von Steuerelementen, Schriftarten und anderer UI-Elemente an, damit sie auf [allen Geräten mit UWP-App-Unterstützung](../devices/index.md) lesbar sind und die Interaktion erleichtern.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-109">UWP apps automatically adjust the size of controls, fonts, and other UI elements so that they are legible and easy to interact with on [all devices that support UWP apps](../devices/index.md).</span></span>

<span data-ttu-id="6c2c1-110">Wenn Ihre App auf einem Gerät ausgeführt wird, verwendet das System einen Algorithmus, um die Art der Anzeige der UI-Elemente auf dem Bildschirm zu normalisieren.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-110">When your app runs on a device, the system uses an algorithm to normalize the way UI elements display on the screen.</span></span> <span data-ttu-id="6c2c1-111">Dieser Skalierungsalgorithmus berücksichtigt den Abstand zum Bildschirm und die Bildschirmdichte (Pixel pro Zoll), um die wahrgenommene Größe (anstelle der physischen Größe) zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-111">This scaling algorithm takes into account viewing distance and screen density (pixels per inch) to optimize for perceived size (rather than physical size).</span></span> <span data-ttu-id="6c2c1-112">Mit dem Skalierungsalgorithmus wird sichergestellt, dass der Schriftgrad 24 Pixel auf einem 3 Meter entfernten Surface Hub genauso für den Benutzer lesbar ist wie der Schriftgrad 24 Pixel auf einem 5-Zoll-Smartphone, das nur einige Zentimeter entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-112">The scaling algorithm ensures that a 24 px font on Surface Hub 10 feet away is just as legible to the user as a 24 px font on 5" phone that's a few inches away.</span></span>

![Sichtabstände für verschiedene Geräte](images/1910808-hig-uap-toolkit-03.png)

<span data-ttu-id="6c2c1-114">Aufgrund der Funktionsweise des Skalierungssystems beim Entwerfen Ihrer UWP-App, verwenden Sie effektive Pixeln, und nicht die tatsächlichen physischen Pixel.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-114">Because of how the scaling system works, when you design your UWP app, you're designing in effective pixels, not actual physical pixels.</span></span> <span data-ttu-id="6c2c1-115">Effektive Pixel (epx) sind eine virtuelle Maßeinheit und werden verwendet, um Layoutabmessungen und -abstände unabhängig von der Pixeldichte auszudrücken.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-115">Effective pixels (epx) are a virtual unit of measurement, and they're used to express layout dimensions and spacing, independent of screen density.</span></span> <span data-ttu-id="6c2c1-116">(In unseren Richtlinien werden epx, ep und px austauschbar verwendet.)</span><span class="sxs-lookup"><span data-stu-id="6c2c1-116">(In our guidelines, epx, ep, and px are used interchangeably.)</span></span>

<span data-ttu-id="6c2c1-117">Sie können die Pixeldichte und die tatsächliche Bildschirmauflösung beim Entwerfen ignorieren.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-117">You can ignore the pixel density and the actual screen resolution when designing.</span></span> <span data-ttu-id="6c2c1-118">Entwerfen Sie stattdessen für die effektive Auflösung (die Auflösung in effektiven Pixeln) für eine Größenklasse (Details finden Sie im Artikel [Bildschirmgrößen und Haltepunkte](../layout/screen-sizes-and-breakpoints-for-responsive-design.md)).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-118">Instead, design for the effective resolution (the resolution in effective pixels) for a size class (for details, see the [Screen sizes and breakpoints article](../layout/screen-sizes-and-breakpoints-for-responsive-design.md)).</span></span>

> [!TIP]
> <span data-ttu-id="6c2c1-119">Legen Sie beim Erstellen von Bildschirmmodellen in Bildbearbeitungsprogrammen die DPI auf 72 und die Bildgröße auf effektive Auflösung für die Zielgrößenklasse fest.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-119">When creating screen mockups in image editing programs, set the DPI to 72 and set the image dimensions to the effective resolution for the size class you're targeting.</span></span> <span data-ttu-id="6c2c1-120">Eine Liste der Größenklassen und effektiven Auflösungen finden Sie unter dem [Artikel Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-120">For a list of size classes and effective resolutions, see the [Screen sizes and breakpoints article](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span></span>


## <a name="layout"></a><span data-ttu-id="6c2c1-121">Layout</span><span class="sxs-lookup"><span data-stu-id="6c2c1-121">Layout</span></span>

### <a name="margins-spacing-and-positioning"></a><span data-ttu-id="6c2c1-122">Ränder, Abstände und Positionierung</span><span class="sxs-lookup"><span data-stu-id="6c2c1-122">Margins, spacing, and positioning</span></span> 
![Raster](images/4epx.png)

<span data-ttu-id="6c2c1-124">Wenn das System die Benutzeroberfläche skaliert, erfolgt dies durch die Multiplikation mit vier.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-124">When the system scales your app's UI, it does so by multiples of 4.</span></span>

<span data-ttu-id="6c2c1-125">Daher sollten die Größen, Ränder und Positionen der **UI-Elemente immer ein Vielfaches von 4 epx betragen**.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-125">As a result, the sizes, margins, and positions of **UI elements should always be in multiples of 4 epx**.</span></span> <span data-ttu-id="6c2c1-126">Das Ergebnis ist ein optimales Rendering durch Ausrichtung auf ganze Pixel.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-126">This results in the best rendering by aligning with whole pixels.</span></span> <span data-ttu-id="6c2c1-127">Es sorgt auch dafür, dass UI-Elemente scharfe und deutliche Kanten haben.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-127">It also ensures that UI elements have crisp, sharp edges.</span></span> 

<span data-ttu-id="6c2c1-128">Beachten Sie, dass Text diese Anforderung nicht hat. Der Text kann eine beliebige Größe und Position haben.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-128">Note that text doesn't have this requirement; text can have any size and position.</span></span> <span data-ttu-id="6c2c1-129">Hinweise zum Ausrichten von Text an anderen UI-Elementen finden Sie im [UWP-Typografieleitfaden](../style/typography.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-129">For guidance on how to align text with other UI elements, see the [UWP Typography Guide](../style/typography.md).</span></span>

![Skalierung auf dem Raster](images/epx-4pixelgood.png)

### <a name="layout-patterns"></a><span data-ttu-id="6c2c1-131">Layoutmuster</span><span class="sxs-lookup"><span data-stu-id="6c2c1-131">Layout patterns</span></span>

![Ein gemeinsames Layoutmuster](images/page-components.png)

<span data-ttu-id="6c2c1-133">Die Benutzeroberfläche besteht aus drei Arten von Elementen:</span><span class="sxs-lookup"><span data-stu-id="6c2c1-133">The user interface is made up of three types of elements:</span></span> 
1. <span data-ttu-id="6c2c1-134">Mithilfe von **Navigationselementen** können Benutzer die Inhalte auswählen, die sie anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-134">**Navigation elements** help users choose the content they want to display.</span></span> <span data-ttu-id="6c2c1-135">Weitere Infos unter [Navigationsgrundlagen](navigation-basics.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-135">See [navigation basics](navigation-basics.md).</span></span>
2. <span data-ttu-id="6c2c1-136">**Befehlselemente** initiieren Aktionen wie etwa das Bearbeiten, Speichern oder Freigeben von Inhalten.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-136">**Command  elements** initiate actions, such as manipulating, saving, or sharing content.</span></span> <span data-ttu-id="6c2c1-137">Weitere Infos unter [Befehlsgrundlagen](commanding-basics.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-137">See [command basics](commanding-basics.md).</span></span>
3. <span data-ttu-id="6c2c1-138">Die **Inhaltselemente** zeigen die Inhalte der App an.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-138">**Content elements** display the app's content.</span></span> <span data-ttu-id="6c2c1-139">Weitere Infos unter [Inhaltsgrundlagen](content-basics.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-139">See [content basics](content-basics.md).</span></span>

### <a name="adaptive-behavior"></a><span data-ttu-id="6c2c1-140">Adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="6c2c1-140">Adaptive behavior</span></span>
![Adaptives Verhalten für Smartphones und Desktops](../controls-and-patterns/images/patterns_masterdetail.png)

<span data-ttu-id="6c2c1-142">Zwar ist die Benutzeroberfläche Ihrer App auf allen Windows-basierten Geräten lesbar und verwendbar, doch Sie sollten sie für bestimmte Geräte und Bildschirmgrößen anpassen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-142">While your app's UI will be legible and usable on all Windows-powered devices, you might want to customize your app's UI for specific devices and screen sizes.</span></span> <span data-ttu-id="6c2c1-143">Weitere Informationen finden Sie unter [Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md) und [Reaktionsfähige Designtechniken](../layout/responsive-design.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-143">For more specific guidance, see [screen sizes and breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md) and [responsive design techniques](../layout/responsive-design.md).</span></span>

## <a name="type"></a><span data-ttu-id="6c2c1-144">Schriftart</span><span class="sxs-lookup"><span data-stu-id="6c2c1-144">Type</span></span>

<span data-ttu-id="6c2c1-145">Standardmäßig verwenden UWP-Anwendungen die **Segoe UI**-Schriftart. Die UWP-Typhierarchie umfassen sieben Typografie-Klassen, die den effizientesten Ansatz für alle Displaygrößen anstreben.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-145">By default, UWP apps use the **Segoe UI** font, and the UWP type ramp includes seven classes of typography, striving for the most efficient approach across all display sizes.</span></span> 

![Typhierarchie](images/type-ramp.png)

<span data-ttu-id="6c2c1-147">Einzelheiten zur Typhierarchie finden Sie im [UWP-Typografieleitfaden](../style/typography.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-147">For details on the type ramp, see the [UWP Typography Guide](../style/typography.md).</span></span> <span data-ttu-id="6c2c1-148">Um zu erfahren, wie Sie die verschiedenen Ebenen der UWP-Typhierarchie in Ihrer App verwenden können, lesen Sie die den Abschnitt [Designressourcen](../controls-and-patterns/xaml-theme-resources.md#the-xaml-type-ramp).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-148">To learn how to use the different levels of the UWP type ramp in your app, see [theme resources](../controls-and-patterns/xaml-theme-resources.md#the-xaml-type-ramp).</span></span>

## <a name="color"></a><span data-ttu-id="6c2c1-149">Farben</span><span class="sxs-lookup"><span data-stu-id="6c2c1-149">Color</span></span>

<span data-ttu-id="6c2c1-150">Farben bietet eine intuitive Möglichkeit, Informationen an die Benutzer zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-150">Color provides an intuitive way of communicating information to users.</span></span> <span data-ttu-id="6c2c1-151">Sie können verwendet werden, um Interaktivität zu signalisieren, Feedback zu Benutzeraktionen zu geben, Zustandsinformationen zu übermitteln und Ihrer Benutzeroberfläche ein Gefühl der visuellen Kontinuität zu geben.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-151">It can be used to signal interactivity, give feedback to user actions, convey state information, and give your interface a sense of visual continuity.</span></span> 

<span data-ttu-id="6c2c1-152">Windows 10 bietet eine gemeinsame, universelle Farbpalette von 48 Farben, die auf die Shell und UWP-Apps angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-152">Windows 10 provides a shared universal color palette of 48 colors, which is applied across the shell and UWP apps.</span></span> 

![Universelle Windows-Farbpalette](images/colors.png)

<span data-ttu-id="6c2c1-154">Das System wendet automatisch Farben auf Ihre UWP-Apps mit der Systemakzentfarbe an.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-154">The system automatically applies color to your UWP app with the system accent color.</span></span> <span data-ttu-id="6c2c1-155">Wenn Benutzer eine Akzentfarbe aus der Farbpalette in ihren Einstellungen auswählen, wird die Farbe als Teil ihres Systemdesigns angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-155">When users choose an accent color from the color palette in their Settings, the color appears as part of their system theme.</span></span> <span data-ttu-id="6c2c1-156">Abhängig von den Benutzereinstellungen kann die Systemakzentfarbe auch auf das Startmenü, Kacheln, Taskleiste und Titelleisten angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-156">Depending on user preferences, the system accent color can also show on Start, Start Tiles, taskbar, and title bars.</span></span> 

![Akzentfarbe in den Einstellungen wählen](images/selectcolor.png)

<span data-ttu-id="6c2c1-158">Innerhalb Ihrer UWP-App spiegeln Hyperlinks und ausgewählte Zustände innerhalb gemeinsamer Steuerelemente die Akzentfarbe des Systems wider.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-158">Within your UWP app, hyperlinks and selected states within common controls will reflect the system accent color.</span></span>

![Systemakzentfarbe auf den Steuerelementen](images/accentcolor.png)

<span data-ttu-id="6c2c1-160">UWP-Apps können die Systemakzentfarbe bei der Anzeige in Steuerelementen überschreiben, indem sie eine [einfache Formatierung](../controls-and-patterns/xaml-styles.md#lightweight-styling) verwenden oder [benutzerdefinierte Steuerelemente](../controls-and-patterns/control-templates.md) erstellen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-160">UWP apps can override the system accent color from displaying in controls by using [lightweight styling](../controls-and-patterns/xaml-styles.md#lightweight-styling) or by creating [custom controls](../controls-and-patterns/control-templates.md).</span></span>

<span data-ttu-id="6c2c1-161">Weitere Informationen zur Verwendung von Farben in Ihrer UWP-App finden Sie im Artikel [Farbe](../style/color.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-161">For additional guidance on using color in your UWP app, see the [Color](../style/color.md) article.</span></span>

### <a name="themes"></a><span data-ttu-id="6c2c1-162">Designs</span><span class="sxs-lookup"><span data-stu-id="6c2c1-162">Themes</span></span>

<span data-ttu-id="6c2c1-163">Der Benutzer kann zwischen einem hellen, dunklen oder kontrastreichen Design wählen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-163">Users can choose between a light, dark, or high contrast theme.</span></span> <span data-ttu-id="6c2c1-164">Sie können das Aussehen Ihrer App je nach Design des Benutzers ändern oder dieses ignorieren.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-164">You can choose to alter the look of your app based on the user’s theme preference, or to opt out.</span></span>

<span data-ttu-id="6c2c1-165">Das helle Design eignet sich am besten für Produktivitätsaufgaben und das Lesen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-165">The light theme is best suited to productivity tasks and reading.</span></span>

<span data-ttu-id="6c2c1-166">Das dunkle Design ermöglicht mehr sichtbare Kontraste in medienzentrierten Anwendungen und Szenarien, die eine Fülle von Videos oder Bildern enthalten.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-166">The dark theme allows for more visible contrasts in media-centric apps and scenarios that include an abundance of videos or imagery.</span></span> <span data-ttu-id="6c2c1-167">In diesen Szenarien ist die Hauptaufgabe eher das Beobachten von Filmen als das Lesen bei schlechten Lichtverhältnissen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-167">In these scenarios, the primary task is more likely to be movie-watching than reading, and to take place under low-light ambient conditions.</span></span>

![Rechner im hellen und dunklen Design](images/light-dark.png)

<span data-ttu-id="6c2c1-169">Designs mit hohem Kontrast verwenden eine kleine Palette von Farbkombinationen mit hohem Farbkontrast, durch die die Benutzeroberfläche leichter zu erkennen ist.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-169">The high contrast theme uses a small palette of contrasting colors that makes the interface easier to see.</span></span>
![Rechner im hellen Design und im Design „Hoher Kontrast (Schwarz)”](../accessibility/images/high-contrast-calculators.png)


<span data-ttu-id="6c2c1-171">Weitere Informationen zur Verwendung von Design und der UWP-Farbhistorie in Ihrer App finden Sie unter [Design-Ressourcen](../controls-and-patterns/xaml-theme-resources.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-171">For more information about using themes and the UWP color ramp in your app, see [theme resources](../controls-and-patterns/xaml-theme-resources.md).</span></span>

## <a name="icons"></a><span data-ttu-id="6c2c1-172">Symbole</span><span class="sxs-lookup"><span data-stu-id="6c2c1-172">Icons</span></span>
![Symbole](images/icons.png)

<span data-ttu-id="6c2c1-174">Symbole sind eine Art Bildsprache, die sich in unseren Alltag eingeprägt hat.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-174">Icons are a type of visual language that have become engrained in our everyday lives.</span></span> <span data-ttu-id="6c2c1-175">Sie lassen uns Konzepte und Handlungen visuell überzeugend ausdrücken, sparen Platz auf dem Bildschirm und dienen der Navigation in unserem digitalen Leben.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-175">They let us express concepts and actions in a visually compelling way, save screen space, and serve as a way of navigating our digital life.</span></span> 

<span data-ttu-id="6c2c1-176">Alle UWP-App haben Zugriff auf die Symbole der Schriftart [Segoe MDL2](../style/segoe-ui-symbol-font.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-176">All UWP apps have access to the icons in the [Segoe MDL2 font](../style/segoe-ui-symbol-font.md).</span></span> <span data-ttu-id="6c2c1-177">Diese Symbole beruhen auf etablierten Formen, die jedem bekannt und leicht zu identifizieren sind, aber sie wurden auch modernisiert, damit sie sich anfühlen, als wären sie von einer Hand gezeichnet worden.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-177">These icons rely on established forms that are familiar and easily identifiable to everyone, but they're also modernized to make them feel like they were drawn by one hand.</span></span>

<span data-ttu-id="6c2c1-178">Wenn Sie Ihre eigenen Symbole erstellen möchten, finden Sie weitere Infos unter [Symbole für UWP-Apps](../style/icons.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-178">If you'd like to create your own icons, see [Icons for UWP apps](../style/icons.md).</span></span>

## <a name="tiles"></a><span data-ttu-id="6c2c1-179">Kacheln</span><span class="sxs-lookup"><span data-stu-id="6c2c1-179">Tiles</span></span>
![Kacheln im Startmenü](images/tiles.png)

<span data-ttu-id="6c2c1-181">Kacheln werden im Startmenü angezeigt und geben einen Einblick in das Geschehen in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-181">Tiles are displayed in the Start menu, and they provide a glimpse of what's going on in your app.</span></span> <span data-ttu-id="6c2c1-182">Ihr Mehrwert basiert auf dem zugrunde liegenden Inhalt und ihrem Design.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-182">Their power comes from the content behind them, and the intelligence and craft with which they're offered up.</span></span> 

<span data-ttu-id="6c2c1-183">UWP-App haben vier Kachelgrößen (klein, mittel, breit und groß), die mit dem Symbol und der Identität der App angepasst werden können.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-183">UWP apps have four tile sizes (small, medium, wide, and large) that can be customized with the app's icon and identity.</span></span> <span data-ttu-id="6c2c1-184">Hinweise zur Gestaltung von Kacheln für Ihre UWP-Apps finden Sie unter [Richtlinien für Kachel- und Symbolelemente](../shell/tiles-and-notifications/app-assets.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-184">For guidance on designing tiles for your UWP app, see [Guidelines for tile and icon assets](../shell/tiles-and-notifications/app-assets.md).</span></span>

## <a name="controls"></a><span data-ttu-id="6c2c1-185">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="6c2c1-185">Controls</span></span>
![Schaltflächen-Steuerelement](images/1910808-hig-uap-toolkit-01.png)

<span data-ttu-id="6c2c1-187">UWP bietet einen Satz von universellen Steuerelementen, die garantiert gut auf allen Windows-Geräten funktionieren.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-187">UWP provides a set of common controls that are guaranteed to work well on all Windows-powered devices.</span></span> <span data-ttu-id="6c2c1-188">Diese Steuerelemente reichen von einfachen Steuerelementen wie Schaltflächen und Textelementen bis hin zu ausgeklügelten Steuerelementen, die Listen aus einem Datensatz und einer Vorlage erzeugen können.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-188">These controls include everything from simple controls, like buttons and text elements, to sophisticated controls that can generate lists from a set of data and a template.</span></span>

<span data-ttu-id="6c2c1-189">UWP-Steuerelemente wählen automatisch das Systemdesign und die Akzentfarbe aus, arbeiten mit allen Eingabetypen und skalieren auf allen Geräten.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-189">UWP controls automatically relect the system theme and accent color, work with all input types, and scale to all devices.</span></span> <span data-ttu-id="6c2c1-190">Und sie sind außerdem sehr anpassbar. Sie können die Vordergrundfarbe eines Steuerelements ändern oder sein Aussehen komplett anpassen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-190">And they're highly customizable, too--you can change the foreground color of a control or completely customize it's appearance.</span></span> 

<span data-ttu-id="6c2c1-191">Eine vollständige Liste der UWP-Steuerelemente und der -Muster, die Sie aus ihnen erstellen können, finden Sie im Abschnitt [Steuerelemente und Muster](../controls-and-patterns/index.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-191">For a complete list of UWP controls and the patterns you can make from them, see the [controls and patterns section](../controls-and-patterns/index.md).</span></span>

## <a name="input"></a><span data-ttu-id="6c2c1-192">Eingabe</span><span class="sxs-lookup"><span data-stu-id="6c2c1-192">Input</span></span>
![Eingabe](../input/images/input-interactions/icons-inputdevices03.png)

<span data-ttu-id="6c2c1-194">UWP-Apps basieren auf intelligenten Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-194">UWP apps rely on smart interactions.</span></span> <span data-ttu-id="6c2c1-195">Dies bedeutet, dass Sie um eine Klick-Interaktion herum entwerfen können, ohne zu wissen oder festzulegen, ob der Klick von einem echten Mausklick oder einem Fingertipp stammt.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-195">You can design around a click interaction without having to know or define whether the click comes from a mouse, a stylus, or a tap of a finger.</span></span> <span data-ttu-id="6c2c1-196">Sie können Ihre Apps aber auch für bestimmte [Eingabemodi und Geräte gestalten](../input/input-primer.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-196">However, you can also design your apps for [specific input modes and devices](../input/input-primer.md).</span></span>

## <a name="accessibility"></a><span data-ttu-id="6c2c1-197">Bedienungshilfen</span><span class="sxs-lookup"><span data-stu-id="6c2c1-197">Accessibility</span></span>
![Benutzer des inklusiven Designs](images/inclusive.png)

<span data-ttu-id="6c2c1-199">Letztendlich geht es bei der Barrierefreiheit darum, das Erlebnis Ihrer App allen Nutzern zugänglich zu machen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-199">Last but not least, accessibility is about making your app's experience open to all users.</span></span> <span data-ttu-id="6c2c1-200">Es ist für alle relevant, nicht nur für Menschen mit Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-200">It's relevant to everyone, not just those with disabilities.</span></span> <span data-ttu-id="6c2c1-201">Jeder kann von einer wirklich umfassenden Benutzererfahrung profitieren. In [Benutzerfreundlichkeit von UWP-Apps](../usability/index.md) erfahren Sie, wie Sie Ihre App für jedermann benutzerfreundlich gestalten können.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-201">Everyone can benefit from truly inclusive user experiences - see [usability for UWP apps](../usability/index.md) to see how to make your app easy to use for everyone.</span></span> <span data-ttu-id="6c2c1-202">Vielleicht möchten Sie auch [Barrierefreiheitsfunktionen](../accessibility/accessibility-overview.md) für Benutzer mit eingeschränkter Seh-, Hör- und Bewegungsfreiheit in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-202">You might also want to consider [accessibility features](../accessibility/accessibility-overview.md) for users with limited sight, hearing, and mobility.</span></span> 

<span data-ttu-id="6c2c1-203">Wenn die Barrierefreiheit von Anfang an in Ihr Design integriert ist, sollte die [Umsetzung der Barrierefeiheit](../accessibility/accessibility-in-the-store.md) Ihrer App nur sehr wenig Zeit und Mühe in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-203">If accessibility is built into your design from the start, then [making your app accessible](../accessibility/accessibility-in-the-store.md) should take very little extra time and effort.</span></span>

## <a name="tools-and-design-toolkits"></a><span data-ttu-id="6c2c1-204">Tools und Design-Toolkits</span><span class="sxs-lookup"><span data-stu-id="6c2c1-204">Tools and design toolkits</span></span>
<span data-ttu-id="6c2c1-205">Da Sie nun über die grundlegenden Designfunktionen Bescheid wissen, sollten Sie die ersten Schritte beim Design Ihrer UWP-App unternehmen.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-205">Now that you know about the basic design features, how about getting started with designing your UWP app?</span></span>

<span data-ttu-id="6c2c1-206">Wir bieten eine Vielzahl von Werkzeugen zur Unterstützung Ihres Designprozesses:</span><span class="sxs-lookup"><span data-stu-id="6c2c1-206">We provide a variety of tools to help your design process:</span></span>

* <span data-ttu-id="6c2c1-207">Weitere Informationen für XD, Illustrator, Photoshop, Framer und Sketch-Toolkits sowie zusätzliche Entwicklungstools und Downloads für Schriftarten finden Sie auf der [Design-Toolkits-Seite](../downloads/index.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-207">See our [Design toolkits page](../downloads/index.md) for XD, Illustrator, Photoshop, Framer, and Sketch toolkits, as well as additional design tools and font downloads.</span></span> 

* <span data-ttu-id="6c2c1-208">Um Ihren Computer so einzurichten, dass er das Codieren von UWP-Apps ermöglicht, lesen Sie den Artikel [Erste Schritte &gt;Vorbereiten](../../get-started/get-set-up.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-208">To get your machine set up to write code for UWP apps, see our [Get started &gt; Get set up](../../get-started/get-set-up.md) article.</span></span> 

* <span data-ttu-id="6c2c1-209">Für Anregungen zur Implementierung von Benutzeroberflächen für UWP werfen Sie einen Blick auf unsere umfassenden [UWP-Beispiel-Apps](https://developer.microsoft.com/windows/samples).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-209">For inspiration on how to implement UI for UWP, take a look at our end-to-end [sample UWP apps](https://developer.microsoft.com/windows/samples).</span></span>

## <a name="next-fluent-design-system"></a><span data-ttu-id="6c2c1-210">Nächstes Thema: Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="6c2c1-210">Next: Fluent Design System</span></span>
<span data-ttu-id="6c2c1-211">Wenn Sie weitere Informationen zu der Prinzipien hinter Fluent Design (das Design-System von Microsoft) und weitere Features für Ihre UWP-App kennenlernen möchten, fahren Sie mit dem Artikel [Fluent Design-System](../fluent-design-system/index.md) fort.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-211">If you'd like to learn about the principles behind Fluent Design (Microsoft's design system) and see more features you can incorporate into your UWP app, continue on to [Fluent Design System](../fluent-design-system/index.md).</span></span>