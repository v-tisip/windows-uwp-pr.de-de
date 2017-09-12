---
author: mijacobs
description: 
title: Acrylmaterial
template: detail.hbs
ms.author: mijacobs
ms.date: 08/9/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: yulikl
design-contact: rybick
dev-contact: jevansa
doc-status: Published
ms.openlocfilehash: 01c8d1bd961a5246a052d1dc7a746257687104e4
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="acrylic-material"></a><span data-ttu-id="fa5f5-103">Acrylmaterial</span><span class="sxs-lookup"><span data-stu-id="fa5f5-103">Acrylic material</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

> [!IMPORTANT]
> <span data-ttu-id="fa5f5-104">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. grundlegend geändert werden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-104">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="fa5f5-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="fa5f5-106">Acryl ist eine Art von [Pinsel](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush), der eine teilweise transparente Textur erzeugt.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-106">Acrylic is a type of [Brush](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush) that creates a partially transparent texture.</span></span> <span data-ttu-id="fa5f5-107">Sie können Acryl auf App-Oberflächen anwenden, um Tiefe hinzuzufügen und eine visuelle Hierarchie herzustellen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-107">You can apply acrylic to app surfaces to add depth and help establish a visual hierarchy.</span></span>  <!-- By allowing user-selected wallpaper or colors to shine through, Acrylic keeps users in touch with the OS personalization they've chosen. -->

> <span data-ttu-id="fa5f5-108">**Wichtige APIs**: [AcrylicBrush-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_Background)</span><span class="sxs-lookup"><span data-stu-id="fa5f5-108">**Important APIs**: [AcrylicBrush class](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background property](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_Background)</span></span>


![Acryl im hellen Design](images/Acrylic_DarkTheme_Base.png)

![Acryl im dunklen Design](images/Acrylic_LightTheme_Base.png)

## <a name="acrylic-and-the-fluent-design-system"></a><span data-ttu-id="fa5f5-111">Acryl und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="fa5f5-111">Acrylic and the Fluent Design System</span></span>

 <span data-ttu-id="fa5f5-112">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-112">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="fa5f5-113">Acryl ist Komponente des Fluent Design-Systems, die physische Struktur (Material) und Tiefe zu Ihrer App hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-113">Acrylic is a Fluent Design System component that adds physical texture (material) and depth to your app.</span></span> 

## <a name="when-to-use-acrylic"></a><span data-ttu-id="fa5f5-114">Wann sollte Acryl verwendet werden?</span><span class="sxs-lookup"><span data-stu-id="fa5f5-114">When to use acrylic</span></span>

<span data-ttu-id="fa5f5-115">Wir empfehlen, unterstützende UI-Komponenten, beispielsweise In-App-Navigation oder Steuerelemente, auf einer Acryloberfläche zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-115">We recommend that you place supporting UI, such as in-app navigation or commanding elements, on an acrylic surface.</span></span> <span data-ttu-id="fa5f5-116">Dieses Material ist auch hilfreich für vorübergehende UI-Elemente, wie beispielsweise Dialogfelder und Flyouts, da dadurch eine sichtbare Beziehung mit dem Inhalt beibehalten werden kann, der die vorübergehende UI ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-116">This material is also helpful for transient UI elements, such as dialogs and flyouts, because it helps maintain a visual relationship with the content that triggered the transient UI.</span></span> <span data-ttu-id="fa5f5-117">Acryl wurde zur Verwendung als Hintergrundmaterial und in optisch unauffälligen Bereichen entwickelt. Sie sollten Acryl daher nicht in detaillierten Vordergrundelementen anwenden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-117">We designed acrylic to be used as a background material and show in visually discrete panes, so don't apply acrylic to detailed foreground elements.</span></span>

<span data-ttu-id="fa5f5-118">Für Oberflächen hinter dem primären App-Inhalt sollten einheitliche, undurchsichtige Hintergründe verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-118">Surfaces behind primary app content should use solid, opaque backgrounds.</span></span>

<span data-ttu-id="fa5f5-119">Ziehen Sie es in Erwägung, Acryl auf einen oder mehrere Ränder Ihrer App, einschließlich der Titelleiste des Fensters, zu erweitern, um die visuelle Darstellung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-119">Consider having acrylic extend to one or more edges of your app, including the window title bar, to improve visual flow.</span></span> <span data-ttu-id="fa5f5-120">Vermeiden Sie Streifeneffekte durch das Stapeln von Acrylfarben verschiedener Mischungen nebeneinander.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-120">Avoid creating a striping effect by stacking acrylics of different blend types adjacent to each other.</span></span> <span data-ttu-id="fa5f5-121">Acryl ist ein Tool zum Erzeugen von visueller Harmonie in Ihren Designs, bei inkorrekter Verwendung können sich jedoch visuelle Störungen ergeben.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-121">Acrylic is a tool to bring visual harmony to your designs but, when used incorrectly, can result in visual noise.</span></span>

<span data-ttu-id="fa5f5-122">Berücksichtigen Sie die folgenden Verwendungsmuster, um zu entscheiden, wie sich Acryl am besten in Ihre App integrieren lässt.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-122">Consider the following usage patterns to decide how best to incorporate acrylic into your app.</span></span>

### <a name="vertical-acrylic-pane"></a><span data-ttu-id="fa5f5-123">Vertikaler Acrylbereich</span><span class="sxs-lookup"><span data-stu-id="fa5f5-123">Vertical acrylic pane</span></span>

<span data-ttu-id="fa5f5-124">Es wird empfohlen, in Apps mit vertikaler Navigation Acryl auf den sekundären Bereich anzuwenden, der die Navigationselemente enthält.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-124">For apps with vertical navigation, we recommend applying acrylic to the secondary pane containing navigation elements.</span></span>

![App-Muster mit einem einzigen vertikalen Acrylbereich](images/acrylic_app-pattern_vertical.png)

<span data-ttu-id="fa5f5-126">[NavigationView](../controls-and-patterns/navigationview.md) ist ein neues allgemeines Steuerelement zum Hinzufügen von Navigation zu Ihrer App. Der visuelle Entwurf dieses Elements enthält Acryl.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-126">[NavigationView](../controls-and-patterns/navigationview.md) is a new common control for adding navigation to your app and includes acrylic in its visual design.</span></span> <span data-ttu-id="fa5f5-127">Der Bereich von NavigationView zeigt Hintergrund-Acryl, wenn der Bereich parallel mit dem primären Inhalt geöffnet ist, und dieses wird automatisch in In-App-Acryl umgewandelt, wenn der Bereich als Überlagerung geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-127">NavigationView’s pane shows background acrylic when the pane is open side-by-side with primary content, and automatically transitions to in-app acrylic when the pane is open as an overlay.</span></span>

<span data-ttu-id="fa5f5-128">Wenn sich NavigationView in Ihrer App nicht verwenden lässt und Sie Acryl selbst hinzufügen möchten, empfehlen wir die Verwendung von relativ transparentem Acryl mit einer Farbton-Deckkraft von 60%.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-128">If your app is not able to leverage NavigationView and you plan on adding acrylic on your own, we recommend using relatively transparent acrylic with 60% tint opacity.</span></span>
 - <span data-ttu-id="fa5f5-129">Wenn der Bereich als Überlagerung über anderen Inhalten der App geöffnet wird, sollte dies [60% In-App-Acryl](#acrylic-theme-resources) sein.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-129">When the pane opens as an overlay above other app content, this should be [60% in-app acrylic](#acrylic-theme-resources)</span></span>
 - <span data-ttu-id="fa5f5-130">Wenn der Bereich parallel mit dem Hauptinhalt der App geöffnet wird, sollte dies [60% Hintergrund-Acryl](#acrylic-theme-resources)sein.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-130">When the pane opens side-by-side with main app content, this should be [60% background acrylic](#acrylic-theme-resources)</span></span>

### <a name="multiple-acrylic-panes"></a><span data-ttu-id="fa5f5-131">Mehrere Acrylbereiche</span><span class="sxs-lookup"><span data-stu-id="fa5f5-131">Multiple acrylic panes</span></span>

<span data-ttu-id="fa5f5-132">Es wird empfohlen, in Apps mit drei verschiedenen vertikalen Bereichen Acryl zum nicht primären Inhalt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-132">For apps with three distinct vertical panes, we recommend adding acrylic to non-primary content.</span></span>
 - <span data-ttu-id="fa5f5-133">Verwenden Sie für den sekundären Bereich, der sich am nächsten am primären Inhalt befindet, [80% Hintergrund-Acryl](#acrylic-theme-resources).</span><span class="sxs-lookup"><span data-stu-id="fa5f5-133">For the secondary pane closest to primary content, use [80% background acrylic](#acrylic-theme-resources)</span></span>
 - <span data-ttu-id="fa5f5-134">Verwenden Sie für den tertiären Bereich, der vom primären Inhalt weiter entfernt ist, [60% Hintergrund-Acryl](#acrylic-theme-resources).</span><span class="sxs-lookup"><span data-stu-id="fa5f5-134">For the tertiary pane further away from primary content, use [60% background acrylic](#acrylic-theme-resources)</span></span>

![App-Muster mit zwei vertikalen Acrylbereichen](images/acrylic_app-pattern_double-vertical.png)

### <a name="horizontal-acrylic-pane"></a><span data-ttu-id="fa5f5-136">Horizontaler Acrylbereich</span><span class="sxs-lookup"><span data-stu-id="fa5f5-136">Horizontal acrylic pane</span></span>

<span data-ttu-id="fa5f5-137">Wir empfehlen, für Apps mit horizontaler Navigation, Steuerung oder sonstigen starken horizontalen Elementen am oberen Rand der App [70% Acryl](#acrylic-theme-resources) auf dieses visuelle Element anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-137">For apps with horizontal navigation, commanding, or other strong horizontal elements across the top of the app, we recommend applying [70% acrylic](#acrylic-theme-resources) to this visual element.</span></span>

![App-Muster mit einem horizontalen Acrylbereich](images/acrylic_app-pattern_horizontal.png)

<span data-ttu-id="fa5f5-139">In Canvas-Apps, bei denen kontinuierlicher, zoomfähiger Inhalt im Mittelpunkt steht, sollte In-App-Acryl in der oberen Leiste verwendet werden, damit Benutzer eine Verbindung mit diesem Inhalt herstellen können.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-139">Canvas apps with emphasis on continuous, zoomable content should use in-app acrylic in the top bar to let users connect with this content.</span></span> <span data-ttu-id="fa5f5-140">Beispiele für Canvas-Apps sind Karten, Malen und Zeichnen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-140">Examples of canvas apps include maps, painting and drawing.</span></span>

<span data-ttu-id="fa5f5-141">Für Apps ohne einen einzigen kontinuierlichen Zeichenbereich empfehlen wir die Verwendung von Hintergrund-Acryl, um Benutzer mit Ihrer gesamten Desktopumgebung zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-141">For apps without a single continuous canvas, we recommend using background acrylic to connect users to their overall desktop environment.</span></span>

### <a name="acrylic-in-utility-apps"></a><span data-ttu-id="fa5f5-142">Acryl in Hilfsprogramm-Apps</span><span class="sxs-lookup"><span data-stu-id="fa5f5-142">Acrylic in utility apps</span></span>

<span data-ttu-id="fa5f5-143">Widgets oder einfachen Apps können als Utility-Apps hervorgehoben werden, wenn im App-Fenster durchgehend Acryl verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-143">Widgets or light-weight apps can reinforce their usage as utility apps by drawing acrylic edge-to-edge inside their app window.</span></span> <span data-ttu-id="fa5f5-144">Apps dieser Kategorie werden in der Regel nur kurz vom Benutzer verwendet und nehmen nicht den gesamte PC-Bildschirm ein.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-144">Apps belonging to this category typically have brief user engagement times and are unlikely to occupy the user's entire desktop screen.</span></span> <span data-ttu-id="fa5f5-145">Beispiele für solche Apps sind der Rechner und das Info-Center.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-145">Examples include calculator and action center.</span></span>

![Dienstprogramm-App „Rechner” mit Acryl im gesamten Hintergrund](images/acrylic_app-pattern_full.png)

> [!Note]
> <span data-ttu-id="fa5f5-147">Das Rendern von Acryloberflächen ist GPU-intensiv, wodurch der Energieverbrauch des Geräts erhöht und die Akkulaufzeit verkürzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-147">Rendering acrylic surfaces is GPU intensive, which can increase device power consumption and shorten battery life.</span></span> <span data-ttu-id="fa5f5-148">Acryleffekte werden automatisch deaktiviert, wenn Geräte in den Stromsparmodus versetzt werden, und die Benutzer können Acryleffekte für alle Apps wahlweise deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-148">Acrylic effects are automatically disabled when devices enter battery saver mode, and users can disable acrylic effects for all apps, if they choose.</span></span>


## <a name="acrylic-blend-types"></a><span data-ttu-id="fa5f5-149">Acrylmischungen</span><span class="sxs-lookup"><span data-stu-id="fa5f5-149">Acrylic blend types</span></span>
<span data-ttu-id="fa5f5-150">Die auffälligste Eigenschaft von Acryl ist seine Transparenz.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-150">Acrylic's most noticeable characteristic is its transparency.</span></span> <span data-ttu-id="fa5f5-151">Es gibt zwei Acrylmischungen, die beeinflussen, welche Inhalte durch das Material sichtbar sind:</span><span class="sxs-lookup"><span data-stu-id="fa5f5-151">There are two acrylic blend types that change what’s visible through the material:</span></span>
 - <span data-ttu-id="fa5f5-152">**Hintergrund-Acryl** zeigt den Desktophintergrund und andere Fenster, die sich hinter der derzeit aktiven App befinden. Dabei wird Tiefe zwischen den Fenstern der Anwendung hinzugefügt, während die Personalisierungseinstellungen des Benutzers angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-152">**Background acrylic** reveals the desktop wallpaper and other windows that are behind the currently active app, adding depth between application windows while celebrating the user’s personalization preferences.</span></span>
 - <span data-ttu-id="fa5f5-153">**In-App-Acryl** fügt Tiefenwirkung innerhalb des App-Frames hinzu, wodurch sowohl Fokus als auch Hierarchie erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-153">**In-app acrylic** adds a sense of depth within the app frame, providing both focus and hierarchy.</span></span>

 ![Hintergrund-Acryl](images/BackgroundAcrylic_DarkTheme.png)

 ![In-App-Acryl](images/AppAcrylic_DarkTheme.png)

 <span data-ttu-id="fa5f5-156">Schichten Sie mehrere Acryloberflächen vorsichtig übereinander.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-156">Layer multiple acrylic surfaces with caution.</span></span> <span data-ttu-id="fa5f5-157">Hintergrund-Acryl sollte sich, wie der Name schon sagt, in der Z-Reihenfolge nicht am nächsten am Benutzer befinden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-157">Background acrylic, as its name implies, should not be closest to the user in z-order.</span></span> <span data-ttu-id="fa5f5-158">Mehrere Schichten von Hintergrund-Acryl führen tendenziell zu unerwarteten optischen Täuschungen und sollten vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-158">Multiple layers of background acrylic tend to result in unexpected optical illusions and should also be avoided.</span></span> <span data-ttu-id="fa5f5-159">Wenn Sie Acryl übereinanderschichten möchten, verwenden Sie dafür In-App-Acryl, und ziehen Sie es in Erwägung, den Farbtonwert des Acryls zu reduzieren, damit die Schichten für den Betrachter optisch besser dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-159">If you choose to layer acrylics, do so with in-app acrylic and consider making acrylic’s tint lighter in value to help visually bring the layers forward to the viewer.</span></span>


## <a name="usability-and-adaptability"></a><span data-ttu-id="fa5f5-160">Benutzerfreundlichkeit und Anpassungsfähigkeit</span><span class="sxs-lookup"><span data-stu-id="fa5f5-160">Usability and adaptability</span></span>
<span data-ttu-id="fa5f5-161">Acryl passt seine Darstellung automatisch an eine Vielzahl von Geräten und Kontext an.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-161">Acrylic automatically adapts its appearance for a wide variety of devices and contexts.</span></span>

<span data-ttu-id="fa5f5-162">Im Modus mit hohem Kontrast wird Benutzern anstelle von Acryl weiterhin die vertraute Hintergrundfarbe ihrer Wahl angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-162">In High Contrast mode, users continue to see the familiar background color of their choosing in place of acrylic.</span></span> <span data-ttu-id="fa5f5-163">Darüber hinaus werden sowohl das Hintergrund- als auch das In-App-Acryl in den folgenden Fällen als Volltonfarben angezeigt:</span><span class="sxs-lookup"><span data-stu-id="fa5f5-163">In addition, both background acrylic and in-app acrylic appear as a solid color</span></span>
 - <span data-ttu-id="fa5f5-164">Bei Deaktivierung der Transparenz in den Personalisierungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="fa5f5-164">When the user turns off transparency in Personalization settings</span></span>
 - <span data-ttu-id="fa5f5-165">Bei aktivem Stromsparmodus</span><span class="sxs-lookup"><span data-stu-id="fa5f5-165">When battery saver mode is activated</span></span>
 - <span data-ttu-id="fa5f5-166">Bei Ausführen der App auf Low-End-Hardware</span><span class="sxs-lookup"><span data-stu-id="fa5f5-166">When the app runs on low-end hardware</span></span>

<span data-ttu-id="fa5f5-167">Darüber hinaus werden in den folgenden Fällen nur beim Hintergrund-Acryl Transparenz und Textur durch eine Volltonfarbe ersetzt:</span><span class="sxs-lookup"><span data-stu-id="fa5f5-167">In addition, only background acrylic will replace its transparency and texture with a solid color</span></span>
 - <span data-ttu-id="fa5f5-168">Bei Deaktivierung eines App-Fensters auf dem Desktop</span><span class="sxs-lookup"><span data-stu-id="fa5f5-168">When an app window on desktop deactivates</span></span>
 - <span data-ttu-id="fa5f5-169">Bei Ausführen der UWP-App auf einem Telefon, der Xbox, HoloLens oder einem Tablet</span><span class="sxs-lookup"><span data-stu-id="fa5f5-169">When the UWP app is running on phone, Xbox, HoloLens or tablet mode</span></span>

### <a name="legibility-considerations"></a><span data-ttu-id="fa5f5-170">Hinweise zur Lesbarkeit</span><span class="sxs-lookup"><span data-stu-id="fa5f5-170">Legibility considerations</span></span>
<span data-ttu-id="fa5f5-171">Es muss sichergestellt werden, dass Texte, die in der App dargestellt werden, [das Kontrastverhältnis erfüllen](../accessibility/accessible-text-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa5f5-171">It’s important to ensure that any text your app presents to users [meets contrast ratios](../accessibility/accessible-text-requirements.md).</span></span> <span data-ttu-id="fa5f5-172">Wir haben die Acrylzusammensetzung optimiert, damit Texte in Schwarz oder Weiß mit hoher Farbauflösung oder in Mittelgrau auf Acryl die Kontrastverhältnisse erfüllen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-172">We’ve optimized the acrylic recipe so that high-color black, white or even medium-color gray text meets contrast ratios on top of acrylic.</span></span> <span data-ttu-id="fa5f5-173">Die Standardeinstellungen der von der Plattform bereitgestellten Designressourcen weisen kontrastierende Färbungen mit 80% Deckkraft auf.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-173">The theme resources provided by the platform default to contrasting tint colors at 80% opacity.</span></span> <span data-ttu-id="fa5f5-174">Beim Platzieren von Textkörper mit hoher Farbauflösung auf Acryl können Sie die Farbton-Deckkraft verringern und die Lesbarkeit gleichzeitig erhalten.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-174">When placing high-color body text on acrylic, you can reduce tint opacity while maintaining legibility.</span></span> <span data-ttu-id="fa5f5-175">Im dunklen Modus kann die Farbton-Deckkraft 70% betragen, während das Acryl im hellen Modus ein Kontrastverhältnis von 50% Deckkraft erfüllt.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-175">In dark mode, tint opacity can be 70%, while light mode acrylic will meet contrast ratios at 50% opacity.</span></span>

<span data-ttu-id="fa5f5-176">Es wird davon abgeraten, farbigen Text auf Ihren Acryloberflächen zu platzieren, da diese Kombinationen bei einem Schriftgrad von 15px wahrscheinlich nicht die Mindestanforderungen an das Kontrastverhältnis erfüllen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-176">We don't recommend placing accent-colored text on your acrylic surfaces because these combinations are likely to not pass minimum contrast ratio requirements at 15px font size.</span></span> <span data-ttu-id="fa5f5-177">Platzieren Sie möglichst keine [Hyperlinks](../controls-and-patterns/hyperlinks.md) über Acrylelementen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-177">Try to avoid placing [hyperlinks](../controls-and-patterns/hyperlinks.md) over acrylic elements.</span></span> <span data-ttu-id="fa5f5-178">Vergessen Sie darüber hinaus nicht die Auswirkungen auf die Lesbarkeit, wenn Sie den Acrylfarbton oder die Deckkraftstufe auf Werte außerhalb der von der Designressource bereitgestellten Plattformstandardeinstellungen einstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-178">Also, if you choose to customize the acrylic tint color or opacity level outside of the platform defaults provided by the theme resource, keep the impact on legibility in mind.</span></span>

## <a name="acrylic-theme-resources"></a><span data-ttu-id="fa5f5-179">Acryl-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="fa5f5-179">Acrylic theme resources</span></span>
<span data-ttu-id="fa5f5-180">Mit dem neuen XAML AcrylicBrush oder den vordefinierten AcrylicBrush-Designressourcen können Sie Acryl ganz einfach auf die Oberflächen Ihrer App anwenden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-180">You can easily apply acrylic to your app’s surfaces using the new XAML AcrylicBrush or predefined AcrylicBrush theme resources.</span></span> <span data-ttu-id="fa5f5-181">Zunächst müssen Sie entscheiden, ob Sie In-App- oder Hintergrund-Acryl verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-181">First, you’ll need to decide whether to use in-app or background acrylic.</span></span> <span data-ttu-id="fa5f5-182">Prüfen Sie die zuvor in diesem Artikel beschriebenen allgemeinen App-Muster auf Empfehlungen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-182">Be sure to review common app patterns described earlier in this article for recommendations.</span></span>

<span data-ttu-id="fa5f5-183">Wir haben eine Sammlung von Pinsel-Designressourcen sowohl für Hintergrund- als auch In-App-Acrylarten erstellt, die das Design der App berücksichtigen und nach Bedarf wieder auf Volltonfarben zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-183">We’ve created a collection of brush theme resources for both background and in-app acrylic types that respect the app’s theme and fall back to solid colors as needed.</span></span> <span data-ttu-id="fa5f5-184">Ressourcen mit der Benennung *Acrylic\*WindowBrush* stellen Hintergrund-Acryl dar, während sich *Acrylic\*ElementBrush* auf In-App-Acryl bezieht.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-184">Resources named *Acrylic\*WindowBrush* represent background acrylic, while *Acrylic\*ElementBrush* refers to in-app acrylic.</span></span>

<table>
    <tr>
        <th align="center"><span data-ttu-id="fa5f5-185">Ressourcenschlüssel</span><span class="sxs-lookup"><span data-stu-id="fa5f5-185">Resource key</span></span></th>
        <th align="center"><span data-ttu-id="fa5f5-186">Farbton-Deckkraft</span><span class="sxs-lookup"><span data-stu-id="fa5f5-186">Tint opacity</span></span></th>
        <th align="center">[<span data-ttu-id="fa5f5-187">Fallbackfarbe</span><span class="sxs-lookup"><span data-stu-id="fa5f5-187">Fallback color</span></span>](color.md)</th>
    </tr>
    <tr>
        <td> <span data-ttu-id="fa5f5-188">SystemControlAcrylicWindowBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-188">SystemControlAcrylicWindowBrush</span></span><br/><span data-ttu-id="fa5f5-189">SystemControlAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-189">SystemControlAcrylicElementBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="fa5f5-190">80%</span><span class="sxs-lookup"><span data-stu-id="fa5f5-190">80%</span></span> </td>
        <td> <span data-ttu-id="fa5f5-191">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="fa5f5-191">ChromeMedium</span></span> </td>
    </tr>
    </tr>
        <td> <span data-ttu-id="fa5f5-192">**Empfohlene Verwendung:** Hierbei handelt es sich um allgemeine Acrylressourcen, die sich in einer Vielzahl von Verwendungsarten gut einsetzen lassen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-192">**Recommended usage:** These are general-purpose acrylic resources that work well in a wide variety of usages.</span></span> <span data-ttu-id="fa5f5-193">Wenn Ihre App sekundären Text in der Farbe AltMedium mit einer kleineren Textgröße als 18px verwendet, platzieren Sie eine Acrylressource von 80% hinter dem Text, um die [Anforderungen an das Kontrastverhältnis zu erfüllen](../accessibility/accessible-text-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa5f5-193">If your app uses secondary text of AltMedium color with text size smaller than 18px, place an 80% acrylic resource behind the text to [meet contrast ratio requirements](../accessibility/accessible-text-requirements.md).</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="fa5f5-194">SystemControlAcrylicMediumHighWindowBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-194">SystemControlAcrylicMediumHighWindowBrush</span></span><br/><span data-ttu-id="fa5f5-195">SystemControlAcrylicMediumHighElementBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-195">SystemControlAcrylicMediumHighElementBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="fa5f5-196">70%</span><span class="sxs-lookup"><span data-stu-id="fa5f5-196">70%</span></span> </td>
        <td> <span data-ttu-id="fa5f5-197">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="fa5f5-197">ChromeMedium</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="fa5f5-198">**Empfohlene Verwendung:** Wenn Ihre App sekundären Text in der Farbe AltMedium mit einer Textgröße von 18px oder mehr verwendet, können Sie diese transparenteren Acrylressourcen von 70% hinter dem Text platzieren.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-198">**Recommended usage:** If your app uses secondary text of AltMedium color with a text size of 18px or larger, you can place these more transparent 70% acrylic resources behind the text.</span></span> <span data-ttu-id="fa5f5-199">Wir empfehlen die Verwendung dieser Ressourcen in den oberen horizontalen Navigations- und Steuerungsbereichen in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-199">We recommend using these resources in your app's top horizontal navigation and commanding areas.</span></span>  </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="fa5f5-200">SystemControlAcrylicMediumWindowBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-200">SystemControlAcrylicMediumWindowBrush</span></span><br/><span data-ttu-id="fa5f5-201">SystemControlAcrylicMediumElementBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-201">SystemControlAcrylicMediumElementBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="fa5f5-202">60%</span><span class="sxs-lookup"><span data-stu-id="fa5f5-202">60%</span></span> </td>
        <td> <span data-ttu-id="fa5f5-203">ChromeMediumLow</span><span class="sxs-lookup"><span data-stu-id="fa5f5-203">ChromeMediumLow</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="fa5f5-204">**Empfohlene Verwendung:** Wenn nur primärer Text der Farbe AltHigh über Acryl platziert wird, kann Ihre App diese Ressourcen von 60% verwenden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-204">**Recommended usage:** When placing only primary text of AltHigh color over acrylic, your app can utilize these 60% resources.</span></span> <span data-ttu-id="fa5f5-205">Es wird empfohlen, den [vertikalen Navigationsbereich](../controls-and-patterns/navigationview.md) Ihrer App, d.h. das Hamburger-Menü, mit 60% Acryl zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-205">We recommend painting your app's [vertical navigation pane](../controls-and-patterns/navigationview.md), i.e. hamburger menu, with 60% acrylic.</span></span> </td>
    </tr>
</table>

<span data-ttu-id="fa5f5-206">Zusätzlich zu farbneutralem Acryl haben wir Ressourcen hinzugefügt, mit denen sich das Acryl mithilfe von benutzerdefinierten Akzentfarben färben lässt.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-206">In addition to color-neutral acrylic, we've also added resources that tint acrylic using the user-specified accent color.</span></span> <span data-ttu-id="fa5f5-207">Wir empfehlen, farbiges Acryl sparsam zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-207">We recommend using colored acrylic sparingly.</span></span> <span data-ttu-id="fa5f5-208">Platzieren Sie für die bereitgestellten Varianten dark1 und dark2 weißen bzw. hellfarbigen Text der Textfarbe des dunklen Designs entsprechend über diesen Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-208">For the dark1 and dark2 variants provided, place white or light-colored text consistent with dark theme text color over these resources.</span></span>
<table>
    <tr>
        <th align="center"><span data-ttu-id="fa5f5-209">Ressourcenschlüssel</span><span class="sxs-lookup"><span data-stu-id="fa5f5-209">Resource key</span></span></th>
        <th align="center"><span data-ttu-id="fa5f5-210">Farbton-Deckkraft</span><span class="sxs-lookup"><span data-stu-id="fa5f5-210">Tint opacity</span></span></th>
        <th align="center">[<span data-ttu-id="fa5f5-211">Farbton und Fallbackfarben</span><span class="sxs-lookup"><span data-stu-id="fa5f5-211">Tint and Fallback colors</span></span>](color.md)</th>
    </tr>
    <tr>
        <td> <span data-ttu-id="fa5f5-212">SystemControlAcrylicAccentMediumHighWindowBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-212">SystemControlAcrylicAccentMediumHighWindowBrush</span></span><br/><span data-ttu-id="fa5f5-213">SystemControlAcrylicAccentMediumHighElementBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-213">SystemControlAcrylicAccentMediumHighElementBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="fa5f5-214">70%</span><span class="sxs-lookup"><span data-stu-id="fa5f5-214">70%</span></span> </td>
        <td> <span data-ttu-id="fa5f5-215">SystemAccentColor</span><span class="sxs-lookup"><span data-stu-id="fa5f5-215">SystemAccentColor</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="fa5f5-216">SystemControlAcrylicAccentDark1WindowBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-216">SystemControlAcrylicAccentDark1WindowBrush</span></span><br/><span data-ttu-id="fa5f5-217">SystemControlAcrylicAccentDark1ElementBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-217">SystemControlAcrylicAccentDark1ElementBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="fa5f5-218">80%</span><span class="sxs-lookup"><span data-stu-id="fa5f5-218">80%</span></span> </td>
        <td> <span data-ttu-id="fa5f5-219">SystemAccentColorDark1</span><span class="sxs-lookup"><span data-stu-id="fa5f5-219">SystemAccentColorDark1</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="fa5f5-220">SystemControlAcrylicAccentDark2MediumHighWindowBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-220">SystemControlAcrylicAccentDark2MediumHighWindowBrush</span></span><br/><span data-ttu-id="fa5f5-221">SystemControlAcrylicAccentDark2MediumHighElementBrush</span><span class="sxs-lookup"><span data-stu-id="fa5f5-221">SystemControlAcrylicAccentDark2MediumHighElementBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="fa5f5-222">70%</span><span class="sxs-lookup"><span data-stu-id="fa5f5-222">70%</span></span> </td>
        <td> <span data-ttu-id="fa5f5-223">SystemAccentColorDark2</span><span class="sxs-lookup"><span data-stu-id="fa5f5-223">SystemAccentColorDark2</span></span> </td>
    </tr>
</table>


<span data-ttu-id="fa5f5-224">Um eine bestimmte Oberfläche zu zeichnen, wenden Sie eines der oben genannten Designressourcen auf Elementhintergründe an. Verfahren Sie dabei genauso, wie Sie die anderen Pinselressourcen anwenden würden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-224">To paint a specific surface, apply one of the above theme resources to element backgrounds just as you would apply any other brush resource.</span></span>

```xaml
<Grid Background="{ThemeResource SystemControlAcrylicElementBrush}">
```

## <a name="custom-acrylic-brush"></a><span data-ttu-id="fa5f5-225">Benutzerdefinierter Acrylpinsel</span><span class="sxs-lookup"><span data-stu-id="fa5f5-225">Custom acrylic brush</span></span>
<span data-ttu-id="fa5f5-226">Sie können einen Farbton zum Acryl Ihrer App hinzufügen, um das Branding anzuzeigen oder ein optisches Gleichgewicht mit anderen Elementen auf dieser Seite zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-226">You may choose to add a color tint to your app’s acrylic to show branding or provide visual balance with other elements on the page.</span></span> <span data-ttu-id="fa5f5-227">Um Farbe und keine Graustufen anzuzeigen, müssen Sie Ihre eigenen Acrylpinsel mithilfe der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="fa5f5-227">To show color rather than greyscale, you’ll need to define your own acrylic brushes using the following properties.</span></span>
 - <span data-ttu-id="fa5f5-228">**TintColor**: die Überlagerungsschicht der Farbe/des Farbtons.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-228">**TintColor**: the color/tint overlay layer.</span></span> <span data-ttu-id="fa5f5-229">Sie sollten sowohl den RGB-Farbwert als auch die Deckkraft des Alphakanals angeben.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-229">Consider specifying both the RGB color value and alpha channel opacity.</span></span>
 - <span data-ttu-id="fa5f5-230">**TintOpacity**: die Deckkraft der Farbtonschicht.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-230">**TintOpacity**: the opacity of the tint layer.</span></span> <span data-ttu-id="fa5f5-231">Wir empfehlen 80% Deckkraft als Ausgangspunkt, obwohl verschiedene Farben bei anderer Transparenz möglicherweise ansprechender aussehen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-231">We recommend 80% opacity as a starting point, although different colors may look more compelling at other transparencies.</span></span>
 - <span data-ttu-id="fa5f5-232">**BackgroundSource**: die Kennzeichnung zum Festlegen, ob Sie Hintergrund- oder In-App Acryl verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-232">**BackgroundSource**: the flag to specify whether you want background or in-app acrylic.</span></span>
 - <span data-ttu-id="fa5f5-233">**FallbackColor**: die Volltonfarbe, die Acryl bei schwacher Akkuladung ersetzt.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-233">**FallbackColor**: the solid color that replaces acrylic in low-battery mode.</span></span> <span data-ttu-id="fa5f5-234">Im Fall von Hintergrund-Acryl ersetzt die Fallbackfarbe das Acryl auch, wenn Ihre App nicht im aktiven Desktopfenster angezeigt wird oder wenn die App auf dem Telefon oder der Xbox ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-234">For background acrylic, fallback color also replaces acrylic when your app isn’t in the active desktop window or when the app is running on phone and Xbox.</span></span>


![Acrylmuster für das helle Design](images/CustomAcrylic_Swatches_LightTheme.png)

![Acrylmuster für das dunkle Design](images/CustomAcrylic_Swatches_DarkTheme.png)

<span data-ttu-id="fa5f5-237">Um einen Acrylpinsel hinzuzufügen, definieren Sie die Ressourcen für das dunkle und das helle Design und für das Design mit hohem Kontrast.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-237">To add an acrylic brush, define the three resources for dark, light and high contrast themes.</span></span> <span data-ttu-id="fa5f5-238">Beachten Sie, dass wir bei hohem Kontrast die Verwendung eines SolidColorBrush mit demselben X:Key wie für den dunklen/hellen AcrylicBrush zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-238">Note that in high contrast, we recommend using a SolidColorBrush with the same x:Key as the dark/light AcrylicBrush.</span></span>

```xaml
<ResourceDictionary.ThemeDictionaries>
    <ResourceDictionary x:Key="Default">
        <AcrylicBrush x:Key="MyAcrylicBrush"
            BackgroundSource="HostBackdrop"
            TintColor="#FFFF0000"
            TintOpacity="0.8"
            FallbackColor="#FF7F0000"/>
    </ResourceDictionary>

    <ResourceDictionary x:Key="HighContrast">
        <SolidColorBrush x:Key="MyAcrylicBrush"
            Color="{ThemeResource SystemColorWindowColor}"/>
    </ResourceDictionary>

    <ResourceDictionary x:Key="Light">
        <AcrylicBrush x:Key="MyAcrylicBrush"
            BackgroundSource="HostBackdrop"
            TintColor="#FFFF0000"
            TintOpacity="0.8"
            FallbackColor="#FFFF7F7F"/>
    </ResourceDictionary>
</ResourceDictionary.ThemeDictionaries>
```

<span data-ttu-id="fa5f5-239">Das folgende Beispiel zeigt, wie Sie AcrylicBrush in Code angeben.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-239">The following sample shows how to declare AcrylicBrush in code.</span></span> <span data-ttu-id="fa5f5-240">Wenn Ihre App mehrere Betriebssystemziele unterstützt, müssen Sie sicherstellen, dass diese API auf dem Gerät des Benutzers verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-240">If your app supports multiple OS targets, be sure to check that this API is available on the user’s machine.</span></span>

```csharp
if (Windows.Foundation.Metadata.ApiInformation.IsTypePresent("Windows.UI.Xaml.Media.XamlCompositionBrushBase"))
{
    Windows.UI.Xaml.Media.AcrylicBrush myBrush = new Windows.UI.Xaml.Media.AcrylicBrush();
    myBrush.BackgroundSource = Windows.UI.Xaml.Media.AcrylicBackgroundSource.HostBackdrop;
    myBrush.TintColor = Color.FromArgb(255, 202, 24, 37);
    myBrush.FallbackColor = Color.FromArgb(255, 202, 24, 37);
    myBrush.TintOpacity = 0.6;

    grid.Fill = myBrush;
}
else
{
    SolidColorBrush myBrush = new SolidColorBrush(Color.FromArgb(255, 202, 24, 37));

    grid.Fill = myBrush;
}
```

## <a name="extending-acrylic-into-your-title-bar"></a><span data-ttu-id="fa5f5-241">Ausdehnen von Acryl auf die Titelleiste</span><span class="sxs-lookup"><span data-stu-id="fa5f5-241">Extending acrylic into your title bar</span></span>

<span data-ttu-id="fa5f5-242">Für eine nahtlose, fließende Darstellung im Fenster Ihrer App wird empfohlen, Acryl im Titelleistenbereich der App zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-242">For a seamless, flowing look within your app's window, we recommend placing acrylic in your app's title bar area.</span></span> <span data-ttu-id="fa5f5-243">Fügen Sie dazu den folgenden Code in der Datei App.xaml.cs hinzu.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-243">To do so, add the following code to your App.xaml.cs.</span></span>

```csharp
CoreApplication.GetCurrentView().TitleBar.ExtendViewIntoTitleBar = true;
ApplicationViewTitleBar titleBar = ApplicationView.GetForCurrentView().TitleBar;
titleBar.ButtonBackgroundColor = Colors.Transparent;
titleBar.ButtonInactiveBackgroundColor = Colors.Transparent;
```

<span data-ttu-id="fa5f5-244">Darüber hinaus müssen Sie den Titel der App, der normalerweise automatisch in der Titelleiste angezeigt wird, mit einem TextBlock ziehen, der `CaptionTextBlockStyle` verwendet.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-244">In addition, you'll need to draw your app's title, which normally appears automatically in the title bar, with a TextBlock using `CaptionTextBlockStyle`.</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="fa5f5-245">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="fa5f5-245">Do's and don'ts</span></span>
* <span data-ttu-id="fa5f5-246">Verwenden Sie Acryl als Hintergrundmaterial von nicht primären App-Oberflächen wie Navigationsbereichen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-246">Do use acrylic as the background material of non-primary app surfaces like navigation panes.</span></span>
* <span data-ttu-id="fa5f5-247">Dehnen Sie das Acryl auf mindestens einen Rand der App aus, um durch eine dezente Vermischung mit der Umgebung der App eine nahtlose Oberfläche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-247">Do extend acrylic to at least one edge of your app to provide a seamless experience by subtly blending with the app’s surroundings.</span></span>
* <span data-ttu-id="fa5f5-248">Platzieren Sie In-App- und Hintergrund-Acryl nicht direkt nebeneinander, um visuelle Spannung an den Rändern zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-248">Don’t place in-app and background acrylics directly adjacent to avoid visual tension at the seams.</span></span>
* <span data-ttu-id="fa5f5-249">Platzieren Sie nicht mehrere Acrylbereiche mit demselben Farbton und derselben Deckkraft nebeneinander, da dies eine unerwünschte sichtbare Naht erzeugt.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-249">Don't place multiple acrylic panes with the same tint and opacity next to each other because this results in an undesirable visible seam.</span></span>
* <span data-ttu-id="fa5f5-250">Platzieren Sie keinen farbigen Text über Acryloberflächen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-250">Don’t place accent-colored text over acrylic surfaces.</span></span>

## <a name="how-we-designed-acrylic"></a><span data-ttu-id="fa5f5-251">Unser Acryl-Entwurfsansatz</span><span class="sxs-lookup"><span data-stu-id="fa5f5-251">How we designed acrylic</span></span>

<span data-ttu-id="fa5f5-252">Wir haben die Hauptkomponenten des Acryls optimiert, um eine individuelle Darstellung und einzigartige Eigenschaften zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-252">We fine-tuned acrylic’s key components to arrive at its unique appearance and properties.</span></span> <span data-ttu-id="fa5f5-253">Wir begannen damit, flachen Oberflächen mithilfe von Transparenz, Weichzeichnungs- und Störungsfiltern visuelle Tiefe und Dimension hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-253">We started with transparency, blur and noise to add visual depth and dimension to flat surfaces.</span></span> <span data-ttu-id="fa5f5-254">Dann fügten wir eine Ausschluss-Mischmodus-Ebene hinzu, um den Kontrast und die Lesbarkeit der auf dem Acrylhintergrund platzierten UI sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-254">We added an exclusion blend mode layer to ensure contrast and legibility of UI placed on an acrylic background.</span></span> <span data-ttu-id="fa5f5-255">Zuletzt fügten wir Farbtöne hinzu, um Personalisierungen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-255">Finally, we added color tint for personalization opportunities.</span></span> <span data-ttu-id="fa5f5-256">Zusammen ergeben diese Ebenen ein neues, einsatzbereites Material.</span><span class="sxs-lookup"><span data-stu-id="fa5f5-256">In concert these layers add up to a fresh, usable material.</span></span>

![Acrylzusammensetzung](images/AcrylicRecipe_Diagram.png)
<br/><span data-ttu-id="fa5f5-258">Das Acryl setzt sich folgendermaßen zusammen: Hintergrund, Weichzeichnungsfilter, Ausschluss-Mischung, Überlagerung der Farbe/des Farbtons, Störungsfilter</span><span class="sxs-lookup"><span data-stu-id="fa5f5-258">The acrylic recipe: background, blur, exclusion blend, color/tint overlay, noise</span></span>

<!--
<div class="microsoft-internal-note">
When designing your app, please utilize these [design resources](http://uni/DesignDepot.FrontEnd/#/Search?t=Resources%7CNeon%7CToolkit&f=Acrylic%20Material) to show acrylic in comps. The linked templates are the most accurate way to represent acrylic material in Photoshop and Illustrator. The ordering, as noted in the recipe diagram above, should start from the top: <br/>
 - Noise asset (tiled) at 4% opacity <br/>
 - Base color/tint/alpha layer <br/>
 - Exclusion blend (white @ 10% opacity) <br/>
 - Gaussian blur (30px radius) <br/>
</div>
-->


## <a name="related-articles"></a><span data-ttu-id="fa5f5-259">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="fa5f5-259">Related articles</span></span>
[**<span data-ttu-id="fa5f5-260">Einblendungen</span><span class="sxs-lookup"><span data-stu-id="fa5f5-260">Reveal</span></span>**](reveal.md)
