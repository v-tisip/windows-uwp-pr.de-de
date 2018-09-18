---
author: mijacobs
description: Eine Art von Pinsel, der eine durchsichtige Textur erzeugt.
title: Acryl-Material
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
ms.localizationpriority: medium
ms.openlocfilehash: 8589a450b53a5ea028f8af2cee2aef7dc0816b52
ms.sourcegitcommit: f5321b525034e2b3af202709e9b942ad5557e193
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2018
ms.locfileid: "4017272"
---
# <a name="acrylic-material"></a><span data-ttu-id="ea1f1-104">Acryl-Material</span><span class="sxs-lookup"><span data-stu-id="ea1f1-104">Acrylic material</span></span>

![Favoritenbild](images/header-acrylic.svg)

<span data-ttu-id="ea1f1-106">Acryl ist eine Art von [Pinsel](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush) , der eine durchsichtige Textur erzeugt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-106">Acrylic is a type of [Brush](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush) that creates a translucent texture.</span></span> <span data-ttu-id="ea1f1-107">Sie können Acryl auf App-Oberflächen anwenden, um Tiefe hinzuzufügen und eine visuelle Hierarchie herzustellen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-107">You can apply acrylic to app surfaces to add depth and help establish a visual hierarchy.</span></span>  <!-- By allowing user-selected wallpaper or colors to shine through, acrylic keeps users in touch with the OS personalization they've chosen. -->

> <span data-ttu-id="ea1f1-108">**Wichtige APIs**: [AcrylicBrush-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.Background)</span><span class="sxs-lookup"><span data-stu-id="ea1f1-108">**Important APIs**: [AcrylicBrush class](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background property](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.Background)</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="ea1f1-109">Acryl im hellen Design ![Acryl im hellen Design</span><span class="sxs-lookup"><span data-stu-id="ea1f1-109">Acrylic in light theme ![Acrylic in light theme</span></span>](images/Acrylic_LightTheme_Base.png)
    :::column-end:::
    :::column:::
        <span data-ttu-id="ea1f1-110">Acryl im dunklen Design ![Acryl im dunklen Design</span><span class="sxs-lookup"><span data-stu-id="ea1f1-110">Acrylic in dark theme ![Acrylic in dark theme</span></span>](images/Acrylic_DarkTheme_Base.png)
    :::column-end:::
:::row-end:::

## <a name="acrylic-and-the-fluent-design-system"></a><span data-ttu-id="ea1f1-111">Acryl und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="ea1f1-111">Acrylic and the Fluent Design System</span></span>

 <span data-ttu-id="ea1f1-112">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-112">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="ea1f1-113">Acryl ist Komponente des Fluent Design-Systems, die physische Struktur (Material) und Tiefe zu Ihrer App hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-113">Acrylic is a Fluent Design System component that adds physical texture (material) and depth to your app.</span></span> <span data-ttu-id="ea1f1-114">Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="ea1f1-114">To learn more, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

 ## <a name="video-summary"></a><span data-ttu-id="ea1f1-115">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="ea1f1-115">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev002/player]

## <a name="examples"></a><span data-ttu-id="ea1f1-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ea1f1-116">Examples</span></span>

:::row:::
    <span data-ttu-id="ea1f1-117">::: Column Span::: ![einige Image</span><span class="sxs-lookup"><span data-stu-id="ea1f1-117">:::column span::: ![Some image</span></span>](images/XAML-controls-gallery-app-icon.png)
    :::column-end:::
    <span data-ttu-id="ea1f1-118">::: Column Span = "2"::: **XAML-Steuerelementekatalog**</span><span class="sxs-lookup"><span data-stu-id="ea1f1-118">:::column span="2"::: **XAML Controls Gallery**</span></span><br>
        <span data-ttu-id="ea1f1-119">Wenn Sie die XAML-Steuerelementekatalog-app installiert haben, klicken Sie <a href="xamlcontrolsgallery:/item/Acrylic">hier</a> auf die app zu öffnen und Acryl in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-119">If you have the XAML Controls Gallery app installed, click <a href="xamlcontrolsgallery:/item/Acrylic">here</a> to open the app and see acrylic in action.</span></span>

        <a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a><br>
        <a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a>
    :::column-end:::
:::row-end:::

## <a name="when-to-use-acrylic"></a><span data-ttu-id="ea1f1-120">Wann sollte Acryl verwendet werden?</span><span class="sxs-lookup"><span data-stu-id="ea1f1-120">When to use acrylic</span></span>

<span data-ttu-id="ea1f1-121">Wir empfehlen, unterstützende UI-Komponenten, beispielsweise In-App-Navigation oder Steuerelemente, auf einer Acryloberfläche zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-121">We recommend that you place supporting UI, such as in-app navigation or commanding elements, on an acrylic surface.</span></span> <span data-ttu-id="ea1f1-122">Dieses Material ist auch hilfreich für vorübergehende UI-Elemente, wie beispielsweise Dialogfelder und Flyouts, da dadurch eine sichtbare Beziehung mit dem Inhalt beibehalten werden kann, der die vorübergehende UI ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-122">This material is also helpful for transient UI elements, such as dialogs and flyouts, because it helps maintain a visual relationship with the content that triggered the transient UI.</span></span> <span data-ttu-id="ea1f1-123">Acryl wurde zur Verwendung als Hintergrundmaterial und in optisch unauffälligen Bereichen entwickelt. Sie sollten Acryl daher nicht in detaillierten Vordergrundelementen anwenden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-123">We designed acrylic to be used as a background material and show in visually discrete panes, so don't apply acrylic to detailed foreground elements.</span></span>

<span data-ttu-id="ea1f1-124">Für Oberflächen hinter dem primären App-Inhalt sollten einheitliche, undurchsichtige Hintergründe verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-124">Surfaces behind primary app content should use solid, opaque backgrounds.</span></span>

<span data-ttu-id="ea1f1-125">Ziehen Sie es in Erwägung, Acryl auf einen oder mehrere Ränder Ihrer App, einschließlich der Titelleiste des Fensters, zu erweitern, um die visuelle Darstellung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-125">Consider having acrylic extend to one or more edges of your app, including the window title bar, to improve visual flow.</span></span> <span data-ttu-id="ea1f1-126">Vermeiden Sie Streifeneffekte durch das Stapeln von Acrylfarben verschiedener Mischungen nebeneinander.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-126">Avoid creating a striping effect by stacking acrylics of different blend types adjacent to each other.</span></span> <span data-ttu-id="ea1f1-127">Acryl ist ein Tool zum Erzeugen von visueller Harmonie in Ihren Designs, bei inkorrekter Verwendung können sich jedoch visuelle Störungen ergeben.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-127">Acrylic is a tool to bring visual harmony to your designs but, when used incorrectly, can result in visual noise.</span></span>

<span data-ttu-id="ea1f1-128">Berücksichtigen Sie die folgenden Verwendungsmuster, um zu entscheiden, wie sich Acryl am besten in Ihre App integrieren lässt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-128">Consider the following usage patterns to decide how best to incorporate acrylic into your app.</span></span>

### <a name="vertical-acrylic-pane"></a><span data-ttu-id="ea1f1-129">Vertikaler Acrylbereich</span><span class="sxs-lookup"><span data-stu-id="ea1f1-129">Vertical acrylic pane</span></span>

<span data-ttu-id="ea1f1-130">Es wird empfohlen, in Apps mit vertikaler Navigation Acryl auf den sekundären Bereich anzuwenden, der die Navigationselemente enthält.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-130">For apps with vertical navigation, we recommend applying acrylic to the secondary pane containing navigation elements.</span></span>

![App-Muster mit einem einzigen vertikalen Acrylbereich](images/acrylic_app-pattern_vertical.png)

<span data-ttu-id="ea1f1-132">[NavigationView](../controls-and-patterns/navigationview.md) ist ein neues allgemeines Steuerelement zum Hinzufügen von Navigation zu Ihrer App. Der visuelle Entwurf dieses Elements enthält Acryl.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-132">[NavigationView](../controls-and-patterns/navigationview.md) is a new common control for adding navigation to your app and includes acrylic in its visual design.</span></span> <span data-ttu-id="ea1f1-133">Der Bereich von NavigationView zeigt Hintergrund-Acryl, wenn der Bereich parallel mit dem primären Inhalt geöffnet ist, und dieses wird automatisch in In-App-Acryl umgewandelt, wenn der Bereich als Überlagerung geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-133">NavigationView’s pane shows background acrylic when the pane is open side-by-side with primary content, and automatically transitions to in-app acrylic when the pane is open as an overlay.</span></span>

<span data-ttu-id="ea1f1-134">Wenn Ihre app nicht sich navigationview und Sie Acryl selbst hinzufügen möchten, empfehlen wir die Verwendung von relativ durchsichtige Acryl mit 60 % Farbton-Deckkraft.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-134">If your app is not able to leverage NavigationView and you plan on adding acrylic on your own, we recommend using relatively translucent acrylic with 60% tint opacity.</span></span>
 - <span data-ttu-id="ea1f1-135">Wenn der Bereich als Überlagerung über anderen Inhalten der App geöffnet wird, sollte dies [60% In-App-Acryl](#acrylic-theme-resources) sein.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-135">When the pane opens as an overlay above other app content, this should be [60% in-app acrylic](#acrylic-theme-resources)</span></span>
 - <span data-ttu-id="ea1f1-136">Wenn der Bereich parallel mit dem Hauptinhalt der App geöffnet wird, sollte dies [60% Hintergrund-Acryl](#acrylic-theme-resources)sein.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-136">When the pane opens side-by-side with main app content, this should be [60% background acrylic](#acrylic-theme-resources)</span></span>

### <a name="multiple-acrylic-panes"></a><span data-ttu-id="ea1f1-137">Mehrere Acrylbereiche</span><span class="sxs-lookup"><span data-stu-id="ea1f1-137">Multiple acrylic panes</span></span>

<span data-ttu-id="ea1f1-138">Es wird empfohlen, in Apps mit drei verschiedenen vertikalen Bereichen Acryl zum nicht primären Inhalt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-138">For apps with three distinct vertical panes, we recommend adding acrylic to non-primary content.</span></span>
 - <span data-ttu-id="ea1f1-139">Verwenden Sie für den sekundären Bereich, der sich am nächsten am primären Inhalt befindet, [80% Hintergrund-Acryl](#acrylic-theme-resources).</span><span class="sxs-lookup"><span data-stu-id="ea1f1-139">For the secondary pane closest to primary content, use [80% background acrylic](#acrylic-theme-resources)</span></span>
 - <span data-ttu-id="ea1f1-140">Verwenden Sie für den tertiären Bereich, der vom primären Inhalt weiter entfernt ist, [60% Hintergrund-Acryl](#acrylic-theme-resources).</span><span class="sxs-lookup"><span data-stu-id="ea1f1-140">For the tertiary pane further away from primary content, use [60% background acrylic](#acrylic-theme-resources)</span></span>

![App-Muster mit zwei vertikalen Acrylbereichen](images/acrylic_app-pattern_double-vertical.png)

### <a name="horizontal-acrylic-pane"></a><span data-ttu-id="ea1f1-142">Horizontaler Acrylbereich</span><span class="sxs-lookup"><span data-stu-id="ea1f1-142">Horizontal acrylic pane</span></span>

<span data-ttu-id="ea1f1-143">Wir empfehlen, für Apps mit horizontaler Navigation, Steuerung oder sonstigen starken horizontalen Elementen am oberen Rand der App [70% Acryl](#acrylic-theme-resources) auf dieses visuelle Element anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-143">For apps with horizontal navigation, commanding, or other strong horizontal elements across the top of the app, we recommend applying [70% acrylic](#acrylic-theme-resources) to this visual element.</span></span>

![App-Muster mit einem horizontalen Acrylbereich](images/acrylic_app-pattern_horizontal.png)

<span data-ttu-id="ea1f1-145">In Canvas-Apps, bei denen kontinuierlicher, zoomfähiger Inhalt im Mittelpunkt steht, sollte In-App-Acryl in der oberen Leiste verwendet werden, damit Benutzer eine Verbindung mit diesem Inhalt herstellen können.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-145">Canvas apps with emphasis on continuous, zoomable content should use in-app acrylic in the top bar to let users connect with this content.</span></span> <span data-ttu-id="ea1f1-146">Beispiele für Canvas-Apps sind Karten, Malen und Zeichnen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-146">Examples of canvas apps include maps, painting and drawing.</span></span>

<span data-ttu-id="ea1f1-147">Für Apps ohne einen einzigen kontinuierlichen Zeichenbereich empfehlen wir die Verwendung von Hintergrund-Acryl, um Benutzer mit Ihrer gesamten Desktopumgebung zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-147">For apps without a single continuous canvas, we recommend using background acrylic to connect users to their overall desktop environment.</span></span>

### <a name="acrylic-in-utility-apps"></a><span data-ttu-id="ea1f1-148">Acryl in Hilfsprogramm-Apps</span><span class="sxs-lookup"><span data-stu-id="ea1f1-148">Acrylic in utility apps</span></span>

<span data-ttu-id="ea1f1-149">Widgets oder einfachen Apps können als Utility-Apps hervorgehoben werden, wenn im App-Fenster durchgehend Acryl verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-149">Widgets or light-weight apps can reinforce their usage as utility apps by drawing acrylic edge-to-edge inside their app window.</span></span> <span data-ttu-id="ea1f1-150">Apps dieser Kategorie werden in der Regel nur kurz vom Benutzer verwendet und nehmen nicht den gesamte PC-Bildschirm ein.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-150">Apps belonging to this category typically have brief user engagement times and are unlikely to occupy the user's entire desktop screen.</span></span> <span data-ttu-id="ea1f1-151">Beispiele für solche Apps sind der Rechner und das Info-Center.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-151">Examples include calculator and action center.</span></span>

![Dienstprogramm-App „Rechner” mit Acryl im gesamten Hintergrund](images/acrylic_app-pattern_full.png)

> [!Note]
> <span data-ttu-id="ea1f1-153">Das Rendern von acryloberflächen ist GPU-intensiv, das Gerät den Energieverbrauch zu erhöhen und Akkulaufzeit verkürzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-153">Rendering acrylic surfaces is GPU-intensive, which can increase device power consumption and shorten battery life.</span></span> <span data-ttu-id="ea1f1-154">Acryleffekte werden automatisch deaktiviert, wenn Geräte den Stromsparmodus versetzt, und Benutzer können acryleffekte für alle apps, deaktivieren, wenn der Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-154">Acrylic effects are automatically disabled when devices enter Battery Saver mode, and users can disable acrylic effects for all apps, if they choose.</span></span>


## <a name="acrylic-blend-types"></a><span data-ttu-id="ea1f1-155">Acrylmischungen</span><span class="sxs-lookup"><span data-stu-id="ea1f1-155">Acrylic blend types</span></span>
<span data-ttu-id="ea1f1-156">Die auffälligste Eigenschaft von Acryl ist seine Transparenz.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-156">Acrylic's most noticeable characteristic is its translucency.</span></span> <span data-ttu-id="ea1f1-157">Es gibt zwei Acrylmischungen, die beeinflussen, welche Inhalte durch das Material sichtbar sind:</span><span class="sxs-lookup"><span data-stu-id="ea1f1-157">There are two acrylic blend types that change what’s visible through the material:</span></span>
 - <span data-ttu-id="ea1f1-158">**Hintergrund-Acryl** zeigt den Desktophintergrund und andere Fenster, die sich hinter der derzeit aktiven App befinden. Dabei wird Tiefe zwischen den Fenstern der Anwendung hinzugefügt, während die Personalisierungseinstellungen des Benutzers angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-158">**Background acrylic** reveals the desktop wallpaper and other windows that are behind the currently active app, adding depth between application windows while celebrating the user’s personalization preferences.</span></span>
 - <span data-ttu-id="ea1f1-159">**In-App-Acryl** fügt Tiefenwirkung innerhalb des App-Frames hinzu, wodurch sowohl Fokus als auch Hierarchie erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-159">**In-app acrylic** adds a sense of depth within the app frame, providing both focus and hierarchy.</span></span>

 ![Hintergrund-Acryl](images/BackgroundAcrylic_DarkTheme.png)

 ![In-App-Acryl](images/AppAcrylic_DarkTheme.png)

 <span data-ttu-id="ea1f1-162">Schichten Sie mehrere Acryloberflächen vorsichtig übereinander.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-162">Layer multiple acrylic surfaces with caution.</span></span> <span data-ttu-id="ea1f1-163">Hintergrund-Acryl sollte sich, wie der Name schon sagt, in der Z-Reihenfolge nicht am nächsten am Benutzer befinden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-163">Background acrylic, as its name implies, should not be closest to the user in z-order.</span></span> <span data-ttu-id="ea1f1-164">Mehrere Schichten von Hintergrund-Acryl führen tendenziell zu unerwarteten optischen Täuschungen und sollten vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-164">Multiple layers of background acrylic tend to result in unexpected optical illusions and should also be avoided.</span></span> <span data-ttu-id="ea1f1-165">Wenn Sie Acryl übereinanderschichten möchten, verwenden Sie dafür In-App-Acryl, und ziehen Sie es in Erwägung, den Farbtonwert des Acryls zu reduzieren, damit die Schichten für den Betrachter optisch besser dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-165">If you choose to layer acrylics, do so with in-app acrylic and consider making acrylic’s tint lighter in value to help visually bring the layers forward to the viewer.</span></span>


## <a name="usability-and-adaptability"></a><span data-ttu-id="ea1f1-166">Benutzerfreundlichkeit und Anpassungsfähigkeit</span><span class="sxs-lookup"><span data-stu-id="ea1f1-166">Usability and adaptability</span></span>
<span data-ttu-id="ea1f1-167">Acryl passt seine Darstellung automatisch an eine Vielzahl von Geräten und Kontext an.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-167">Acrylic automatically adapts its appearance for a wide variety of devices and contexts.</span></span>

<span data-ttu-id="ea1f1-168">Im Modus mit hohem Kontrast wird Benutzern anstelle von Acryl weiterhin die vertraute Hintergrundfarbe ihrer Wahl angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-168">In High Contrast mode, users continue to see the familiar background color of their choosing in place of acrylic.</span></span> <span data-ttu-id="ea1f1-169">Darüber hinaus werden sowohl Hintergrund-als auch in-app-Acryl als Volltonfarben angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ea1f1-169">In addition, both background acrylic and in-app acrylic appear as a solid color:</span></span>
 - <span data-ttu-id="ea1f1-170">Wenn der Benutzer deaktiviert die Transparenz in den Einstellungen > Personalisierung > Farben</span><span class="sxs-lookup"><span data-stu-id="ea1f1-170">When the user turns off transparency in Settings > Personalization > Color</span></span>
 - <span data-ttu-id="ea1f1-171">Wenn der Stromsparmodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="ea1f1-171">When Battery Saver mode is activated</span></span>
 - <span data-ttu-id="ea1f1-172">Bei Ausführen der App auf Low-End-Hardware</span><span class="sxs-lookup"><span data-stu-id="ea1f1-172">When the app runs on low-end hardware</span></span>

<span data-ttu-id="ea1f1-173">Darüber hinaus wird nur beim Hintergrund-Acryl seine Transparenz und Textur mit einer Volltonfarbe ersetzt:</span><span class="sxs-lookup"><span data-stu-id="ea1f1-173">In addition, only background acrylic will replace its translucency and texture with a solid color:</span></span>
 - <span data-ttu-id="ea1f1-174">Bei Deaktivierung eines App-Fensters auf dem Desktop</span><span class="sxs-lookup"><span data-stu-id="ea1f1-174">When an app window on desktop deactivates</span></span>
 - <span data-ttu-id="ea1f1-175">Bei Ausführen der UWP-App auf einem Telefon, der Xbox, HoloLens oder einem Tablet</span><span class="sxs-lookup"><span data-stu-id="ea1f1-175">When the UWP app is running on phone, Xbox, HoloLens or tablet mode</span></span>

### <a name="legibility-considerations"></a><span data-ttu-id="ea1f1-176">Hinweise zur Lesbarkeit</span><span class="sxs-lookup"><span data-stu-id="ea1f1-176">Legibility considerations</span></span>
<span data-ttu-id="ea1f1-177">Es muss sichergestellt werden, dass Texte, die in der App dargestellt werden, [das Kontrastverhältnis erfüllen](../accessibility/accessible-text-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea1f1-177">It’s important to ensure that any text your app presents to users [meets contrast ratios](../accessibility/accessible-text-requirements.md).</span></span> <span data-ttu-id="ea1f1-178">Wir haben die Acrylzusammensetzung optimiert, damit Texte in Schwarz oder Weiß mit hoher Farbauflösung oder in Mittelgrau auf Acryl die Kontrastverhältnisse erfüllen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-178">We’ve optimized the acrylic recipe so that high-color black, white or even medium-color gray text meets contrast ratios on top of acrylic.</span></span> <span data-ttu-id="ea1f1-179">Die Standardeinstellungen der von der Plattform bereitgestellten Designressourcen weisen kontrastierende Färbungen mit 80% Deckkraft auf.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-179">The theme resources provided by the platform default to contrasting tint colors at 80% opacity.</span></span> <span data-ttu-id="ea1f1-180">Beim Platzieren von Textkörper mit hoher Farbauflösung auf Acryl können Sie die Farbton-Deckkraft verringern und die Lesbarkeit gleichzeitig erhalten.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-180">When placing high-color body text on acrylic, you can reduce tint opacity while maintaining legibility.</span></span> <span data-ttu-id="ea1f1-181">Im dunklen Modus kann die Farbton-Deckkraft 70% betragen, während das Acryl im hellen Modus ein Kontrastverhältnis von 50% Deckkraft erfüllt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-181">In dark mode, tint opacity can be 70%, while light mode acrylic will meet contrast ratios at 50% opacity.</span></span>

<span data-ttu-id="ea1f1-182">Es wird davon abgeraten, farbigen Text auf Ihren Acryloberflächen zu platzieren, da diese Kombinationen bei einem Schriftgrad von 15px wahrscheinlich nicht die Mindestanforderungen an das Kontrastverhältnis erfüllen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-182">We don't recommend placing accent-colored text on your acrylic surfaces because these combinations are likely to not pass minimum contrast ratio requirements at 15px font size.</span></span> <span data-ttu-id="ea1f1-183">Platzieren Sie möglichst keine [Hyperlinks](../controls-and-patterns/hyperlinks.md) über Acrylelementen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-183">Try to avoid placing [hyperlinks](../controls-and-patterns/hyperlinks.md) over acrylic elements.</span></span> <span data-ttu-id="ea1f1-184">Vergessen Sie darüber hinaus nicht die Auswirkungen auf die Lesbarkeit, wenn Sie den Acrylfarbton oder die Deckkraftstufe auf Werte außerhalb der von der Designressource bereitgestellten Plattformstandardeinstellungen einstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-184">Also, if you choose to customize the acrylic tint color or opacity level outside of the platform defaults provided by the theme resource, keep the impact on legibility in mind.</span></span>

## <a name="acrylic-theme-resources"></a><span data-ttu-id="ea1f1-185">Acryl-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="ea1f1-185">Acrylic theme resources</span></span>
<span data-ttu-id="ea1f1-186">Mit dem neuen XAML AcrylicBrush oder den vordefinierten AcrylicBrush-Designressourcen können Sie Acryl ganz einfach auf die Oberflächen Ihrer App anwenden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-186">You can easily apply acrylic to your app’s surfaces using the new XAML AcrylicBrush or predefined AcrylicBrush theme resources.</span></span> <span data-ttu-id="ea1f1-187">Zunächst müssen Sie entscheiden, ob Sie In-App- oder Hintergrund-Acryl verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-187">First, you’ll need to decide whether to use in-app or background acrylic.</span></span> <span data-ttu-id="ea1f1-188">Prüfen Sie die zuvor in diesem Artikel beschriebenen allgemeinen App-Muster auf Empfehlungen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-188">Be sure to review common app patterns described earlier in this article for recommendations.</span></span>

<span data-ttu-id="ea1f1-189">Wir haben eine Sammlung von Pinsel-Designressourcen sowohl für Hintergrund- als auch In-App-Acrylarten erstellt, die das Design der App berücksichtigen und nach Bedarf wieder auf Volltonfarben zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-189">We’ve created a collection of brush theme resources for both background and in-app acrylic types that respect the app’s theme and fall back to solid colors as needed.</span></span> <span data-ttu-id="ea1f1-190">Ressourcen mit der Benennung *AcrylicWindow* stellen Hintergrund-Acryl dar, während sich *AcrylicElement* auf In-App-Acryl bezieht.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-190">Resources named *AcrylicWindow* represent background acrylic, while *AcrylicElement* refers to in-app acrylic.</span></span>

<table>
    <tr>
        <th align="center"><span data-ttu-id="ea1f1-191">Ressourcenschlüssel</span><span class="sxs-lookup"><span data-stu-id="ea1f1-191">Resource key</span></span></th>
        <th align="center"><span data-ttu-id="ea1f1-192">Farbton-Deckkraft</span><span class="sxs-lookup"><span data-stu-id="ea1f1-192">Tint opacity</span></span></th>
        <th align="center"><a href="color.md"><span data-ttu-id="ea1f1-193">Fallbackfarbe</span><span class="sxs-lookup"><span data-stu-id="ea1f1-193">Fallback color</span></span></a> </th>
    </tr>
    <tr>
        <td> <span data-ttu-id="ea1f1-194">SystemControlAcrylicWindowBrush, SystemControlAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-194">SystemControlAcrylicWindowBrush, SystemControlAcrylicElementBrush</span></span> <br/> <span data-ttu-id="ea1f1-195">SystemControlChromeLowAcrylicWindowBrush, SystemControlChromeLowAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-195">SystemControlChromeLowAcrylicWindowBrush, SystemControlChromeLowAcrylicElementBrush</span></span> <br/> <span data-ttu-id="ea1f1-196">SystemControlBaseHighAcrylicWindowBrush, SystemControlBaseHighAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-196">SystemControlBaseHighAcrylicWindowBrush, SystemControlBaseHighAcrylicElementBrush</span></span> <br/> <span data-ttu-id="ea1f1-197">SystemControlBaseLowAcrylicWindowBrush, SystemControlBaseLowAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-197">SystemControlBaseLowAcrylicWindowBrush, SystemControlBaseLowAcrylicElementBrush</span></span> <br/> <span data-ttu-id="ea1f1-198">SystemControlAltHighAcrylicWindowBrush, SystemControlAltHighAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-198">SystemControlAltHighAcrylicWindowBrush, SystemControlAltHighAcrylicElementBrush</span></span> <br/> <span data-ttu-id="ea1f1-199">SystemControlAltLowAcrylicWindowBrush, SystemControlAltLowAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-199">SystemControlAltLowAcrylicWindowBrush, SystemControlAltLowAcrylicElementBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="ea1f1-200">80%</span><span class="sxs-lookup"><span data-stu-id="ea1f1-200">80%</span></span> </td>
        <td> <span data-ttu-id="ea1f1-201">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="ea1f1-201">ChromeMedium</span></span> <br/> <span data-ttu-id="ea1f1-202">ChromeLow</span><span class="sxs-lookup"><span data-stu-id="ea1f1-202">ChromeLow</span></span> <br/><br/> <span data-ttu-id="ea1f1-203">BaseHigh</span><span class="sxs-lookup"><span data-stu-id="ea1f1-203">BaseHigh</span></span> <br/><br/> <span data-ttu-id="ea1f1-204">BaseLow</span><span class="sxs-lookup"><span data-stu-id="ea1f1-204">BaseLow</span></span> <br/><br/> <span data-ttu-id="ea1f1-205">AltHigh</span><span class="sxs-lookup"><span data-stu-id="ea1f1-205">AltHigh</span></span> <br/><br/> <span data-ttu-id="ea1f1-206">AltLow</span><span class="sxs-lookup"><span data-stu-id="ea1f1-206">AltLow</span></span> </td>
    </tr>
    </tr>
        <td> <span data-ttu-id="ea1f1-207"><b>Empfohlene Verwendung:</b> Hierbei handelt es sich um allgemeine Acrylressourcen, die sich in einer Vielzahl von Verwendungsarten gut einsetzen lassen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-207"><b>Recommended usage:</b> These are general-purpose acrylic resources that work well in a wide variety of usages.</span></span> <span data-ttu-id="ea1f1-208">Wenn Ihre App sekundären Text in der Farbe AltMedium mit einer kleineren Textgröße als 18px verwendet, platzieren Sie eine Acrylressource von 80% hinter dem Text, um die <a href="../accessibility/accessible-text-requirements.md">Anforderungen an das Kontrastverhältnis zu erfüllen</a>.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-208">If your app uses secondary text of AltMedium color with text size smaller than 18px, place an 80% acrylic resource behind the text to <a href="../accessibility/accessible-text-requirements.md">meet contrast ratio requirements</a>.</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="ea1f1-209">SystemControlAcrylicWindowMediumHighBrush, SystemControlAcrylicElementMediumHighBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-209">SystemControlAcrylicWindowMediumHighBrush, SystemControlAcrylicElementMediumHighBrush</span></span> <br/> <span data-ttu-id="ea1f1-210">SystemControlBaseHighAcrylicWindowMediumHighBrush, SystemControlBaseHighAcrylicElementMediumHighBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-210">SystemControlBaseHighAcrylicWindowMediumHighBrush, SystemControlBaseHighAcrylicElementMediumHighBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="ea1f1-211">70%</span><span class="sxs-lookup"><span data-stu-id="ea1f1-211">70%</span></span> </td>
        <td> <span data-ttu-id="ea1f1-212">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="ea1f1-212">ChromeMedium</span></span> <br/><br/> <span data-ttu-id="ea1f1-213">BaseHigh</span><span class="sxs-lookup"><span data-stu-id="ea1f1-213">BaseHigh</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="ea1f1-214"><b>Empfohlene Verwendung:</b> Wenn Ihre app sekundären Text in der Farbe AltMedium mit einer Textgröße von 18px oder mehr verwendet, können Sie diese mehr durchsichtigen acrylressourcen 70 % hinter dem Text platzieren.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-214"><b>Recommended usage:</b> If your app uses secondary text of AltMedium color with a text size of 18px or larger, you can place these more translucent 70% acrylic resources behind the text.</span></span> <span data-ttu-id="ea1f1-215">Wir empfehlen die Verwendung dieser Ressourcen in den oberen horizontalen Navigations- und Steuerungsbereichen in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-215">We recommend using these resources in your app's top horizontal navigation and commanding areas.</span></span>  </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="ea1f1-216">SystemControlChromeHighAcrylicWindowMediumBrush, SystemControlChromeHighAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-216">SystemControlChromeHighAcrylicWindowMediumBrush, SystemControlChromeHighAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="ea1f1-217">SystemControlChromeMediumAcrylicWindowMediumBrush, SystemControlChromeMediumAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-217">SystemControlChromeMediumAcrylicWindowMediumBrush, SystemControlChromeMediumAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="ea1f1-218">SystemControlChromeMediumLowAcrylicWindowMediumBrush, SystemControlChromeMediumLowAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-218">SystemControlChromeMediumLowAcrylicWindowMediumBrush, SystemControlChromeMediumLowAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="ea1f1-219">SystemControlBaseHighAcrylicWindowMediumBrush, SystemControlBaseHighAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-219">SystemControlBaseHighAcrylicWindowMediumBrush, SystemControlBaseHighAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="ea1f1-220">SystemControlBaseMediumLowAcrylicWindowMediumBrush, SystemControlBaseMediumLowAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-220">SystemControlBaseMediumLowAcrylicWindowMediumBrush, SystemControlBaseMediumLowAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="ea1f1-221">SystemControlAltMediumLowAcrylicWindowMediumBrush, SystemControlAltMediumLowAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-221">SystemControlAltMediumLowAcrylicWindowMediumBrush, SystemControlAltMediumLowAcrylicElementMediumBrush</span></span>  </td>
        <td align="center"> <span data-ttu-id="ea1f1-222">60%</span><span class="sxs-lookup"><span data-stu-id="ea1f1-222">60%</span></span> </td>
        <td> <span data-ttu-id="ea1f1-223">ChromeHigh</span><span class="sxs-lookup"><span data-stu-id="ea1f1-223">ChromeHigh</span></span> <br/><br/> <span data-ttu-id="ea1f1-224">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="ea1f1-224">ChromeMedium</span></span> <br/><br/> <span data-ttu-id="ea1f1-225">ChromeMediumLow</span><span class="sxs-lookup"><span data-stu-id="ea1f1-225">ChromeMediumLow</span></span> <br/><br/> <span data-ttu-id="ea1f1-226">BaseHigh</span><span class="sxs-lookup"><span data-stu-id="ea1f1-226">BaseHigh</span></span> <br/><br/> <span data-ttu-id="ea1f1-227">BaseLow</span><span class="sxs-lookup"><span data-stu-id="ea1f1-227">BaseLow</span></span> <br/><br/> <span data-ttu-id="ea1f1-228">AltMediumLow</span><span class="sxs-lookup"><span data-stu-id="ea1f1-228">AltMediumLow</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="ea1f1-229"><b>Empfohlene Verwendung:</b> Wenn nur primärer Text der Farbe AltHigh über Acryl platziert wird, kann Ihre App diese Ressourcen von 60% verwenden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-229"><b>Recommended usage:</b> When placing only primary text of AltHigh color over acrylic, your app can utilize these 60% resources.</span></span> <span data-ttu-id="ea1f1-230">Es wird empfohlen, den <a href="../controls-and-patterns/navigationview.md">vertikalen Navigationsbereich</a> Ihrer App, d.h. das Hamburger-Menü, mit 60% Acryl zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-230">We recommend painting your app's <a href="../controls-and-patterns/navigationview.md">vertical navigation pane</a>, i.e. hamburger menu, with 60% acrylic.</span></span> </td>
    </tr>
</table>

<span data-ttu-id="ea1f1-231">Zusätzlich zu farbneutralem Acryl haben wir Ressourcen hinzugefügt, mit denen sich das Acryl mithilfe von benutzerdefinierten Akzentfarben färben lässt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-231">In addition to color-neutral acrylic, we've also added resources that tint acrylic using the user-specified accent color.</span></span> <span data-ttu-id="ea1f1-232">Wir empfehlen, farbiges Acryl sparsam zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-232">We recommend using colored acrylic sparingly.</span></span> <span data-ttu-id="ea1f1-233">Platzieren Sie für die bereitgestellten Varianten dark1 und dark2 weißen bzw. hellfarbigen Text der Textfarbe des dunklen Designs entsprechend über diesen Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-233">For the dark1 and dark2 variants provided, place white or light-colored text consistent with dark theme text color over these resources.</span></span>
<table>
    <tr>
        <th align="center"><span data-ttu-id="ea1f1-234">Ressourcenschlüssel</span><span class="sxs-lookup"><span data-stu-id="ea1f1-234">Resource key</span></span></th>
        <th align="center"><span data-ttu-id="ea1f1-235">Farbton-Deckkraft</span><span class="sxs-lookup"><span data-stu-id="ea1f1-235">Tint opacity</span></span></th>
        <th align="center"><a href="color.md"><span data-ttu-id="ea1f1-236">Farbton und Fallbackfarben</span><span class="sxs-lookup"><span data-stu-id="ea1f1-236">Tint and Fallback colors</span></span></a> </th>
    </tr>
    <tr>
        <td> <span data-ttu-id="ea1f1-237">SystemControlAccentAcrylicWindowAccentMediumHighBrush, SystemControlAccentAcrylicElementAccentMediumHighBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-237">SystemControlAccentAcrylicWindowAccentMediumHighBrush, SystemControlAccentAcrylicElementAccentMediumHighBrush</span></span>  </td>
        <td align="center"> <span data-ttu-id="ea1f1-238">70%</span><span class="sxs-lookup"><span data-stu-id="ea1f1-238">70%</span></span> </td>
        <td> <span data-ttu-id="ea1f1-239">SystemAccentColor</span><span class="sxs-lookup"><span data-stu-id="ea1f1-239">SystemAccentColor</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="ea1f1-240">SystemControlAccentDark1AcrylicWindowAccentDark1Brush, SystemControlAccentDark1AcrylicElementAccentDark1Brush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-240">SystemControlAccentDark1AcrylicWindowAccentDark1Brush, SystemControlAccentDark1AcrylicElementAccentDark1Brush</span></span>  </td>
        <td align="center"> <span data-ttu-id="ea1f1-241">80%</span><span class="sxs-lookup"><span data-stu-id="ea1f1-241">80%</span></span> </td>
        <td> <span data-ttu-id="ea1f1-242">SystemAccentColorDark1</span><span class="sxs-lookup"><span data-stu-id="ea1f1-242">SystemAccentColorDark1</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="ea1f1-243">SystemControlAccentDark2AcrylicWindowAccentDark2MediumHighBrush, SystemControlAccentDark2AcrylicElementAccentDark2MediumHighBrush</span><span class="sxs-lookup"><span data-stu-id="ea1f1-243">SystemControlAccentDark2AcrylicWindowAccentDark2MediumHighBrush, SystemControlAccentDark2AcrylicElementAccentDark2MediumHighBrush</span></span>  </td>
        <td align="center"> <span data-ttu-id="ea1f1-244">70%</span><span class="sxs-lookup"><span data-stu-id="ea1f1-244">70%</span></span> </td>
        <td> <span data-ttu-id="ea1f1-245">SystemAccentColorDark2</span><span class="sxs-lookup"><span data-stu-id="ea1f1-245">SystemAccentColorDark2</span></span> </td>
    </tr>
</table>


<span data-ttu-id="ea1f1-246">Um eine bestimmte Oberfläche zu zeichnen, wenden Sie eines der oben genannten Designressourcen auf Elementhintergründe an. Verfahren Sie dabei genauso, wie Sie die anderen Pinselressourcen anwenden würden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-246">To paint a specific surface, apply one of the above theme resources to element backgrounds just as you would apply any other brush resource.</span></span>

```xaml
<Grid Background="{ThemeResource SystemControlAcrylicElementBrush}">
```

## <a name="custom-acrylic-brush"></a><span data-ttu-id="ea1f1-247">Benutzerdefinierter Acrylpinsel</span><span class="sxs-lookup"><span data-stu-id="ea1f1-247">Custom acrylic brush</span></span>
<span data-ttu-id="ea1f1-248">Sie können einen Farbton zum Acryl Ihrer App hinzufügen, um das Branding anzuzeigen oder ein optisches Gleichgewicht mit anderen Elementen auf dieser Seite zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-248">You may choose to add a color tint to your app’s acrylic to show branding or provide visual balance with other elements on the page.</span></span> <span data-ttu-id="ea1f1-249">Um Farbe und keine Graustufen anzuzeigen, müssen Sie Ihre eigenen Acrylpinsel mithilfe der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="ea1f1-249">To show color rather than greyscale, you’ll need to define your own acrylic brushes using the following properties.</span></span>
 - <span data-ttu-id="ea1f1-250">**TintColor**: die Überlagerungsschicht der Farbe/des Farbtons.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-250">**TintColor**: the color/tint overlay layer.</span></span> <span data-ttu-id="ea1f1-251">Sie sollten sowohl den RGB-Farbwert als auch die Deckkraft des Alphakanals angeben.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-251">Consider specifying both the RGB color value and alpha channel opacity.</span></span>
 - <span data-ttu-id="ea1f1-252">**TintOpacity**: die Deckkraft der Farbtonschicht.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-252">**TintOpacity**: the opacity of the tint layer.</span></span> <span data-ttu-id="ea1f1-253">Wir empfehlen 80 % Deckkraft als Ausgangspunkt, obwohl verschiedene Farben bei anderen Translucencies aussehen können.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-253">We recommend 80% opacity as a starting point, although different colors may look more compelling at other translucencies.</span></span>
 - <span data-ttu-id="ea1f1-254">**BackgroundSource**: die Kennzeichnung zum Festlegen, ob Sie Hintergrund- oder In-App Acryl verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-254">**BackgroundSource**: the flag to specify whether you want background or in-app acrylic.</span></span>
 - <span data-ttu-id="ea1f1-255">**FallbackColor**: die Volltonfarbe, die Acryl bei der Stromsparmodus ersetzt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-255">**FallbackColor**: the solid color that replaces acrylic in Battery Saver.</span></span> <span data-ttu-id="ea1f1-256">Im Fall von Hintergrund-Acryl ersetzt die Fallbackfarbe das Acryl auch, wenn Ihre App nicht im aktiven Desktopfenster angezeigt wird oder wenn die App auf dem Telefon oder der Xbox ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-256">For background acrylic, fallback color also replaces acrylic when your app isn’t in the active desktop window or when the app is running on phone and Xbox.</span></span>


![Acrylmuster für das helle Design](images/CustomAcrylic_Swatches_LightTheme.png)

![Acrylmuster für das dunkle Design](images/CustomAcrylic_Swatches_DarkTheme.png)

<span data-ttu-id="ea1f1-259">Um einen Acrylpinsel hinzuzufügen, definieren Sie die Ressourcen für das dunkle und das helle Design und für das Design mit hohem Kontrast.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-259">To add an acrylic brush, define the three resources for dark, light and high contrast themes.</span></span> <span data-ttu-id="ea1f1-260">Beachten Sie, dass wir bei hohem Kontrast die Verwendung eines SolidColorBrush mit demselben X:Key wie für den dunklen/hellen AcrylicBrush zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-260">Note that in high contrast, we recommend using a SolidColorBrush with the same x:Key as the dark/light AcrylicBrush.</span></span>

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

<span data-ttu-id="ea1f1-261">Das folgende Beispiel zeigt, wie Sie AcrylicBrush in Code angeben.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-261">The following sample shows how to declare AcrylicBrush in code.</span></span> <span data-ttu-id="ea1f1-262">Wenn Ihre App mehrere Betriebssystemziele unterstützt, müssen Sie sicherstellen, dass diese API auf dem Gerät des Benutzers verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-262">If your app supports multiple OS targets, be sure to check that this API is available on the user’s machine.</span></span>

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

## <a name="extend-acrylic-into-the-title-bar"></a><span data-ttu-id="ea1f1-263">Erweitern Sie Acryl auf die Titelleiste</span><span class="sxs-lookup"><span data-stu-id="ea1f1-263">Extend acrylic into the title bar</span></span>

<span data-ttu-id="ea1f1-264">Um Ihrem App-Fenster ein nahtloses Aussehen zu verleihen, können Sie im Bereich der Titelleiste Acryl verwenden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-264">To give your app's window a seamless look, you can use acrylic in the title bar area.</span></span> <span data-ttu-id="ea1f1-265">In diesem Beispiel wird Acryl in die Titelleiste erweitert, indem die [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar) der Eigenschaften des Objekts [ButtonBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonBackgroundColor) und [ButtonInactiveBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonInactiveBackgroundColor) auf [Colors.Transparent](https://docs.microsoft.com/uwp/api/Windows.UI.Colors.Transparent) festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-265">This example extends acrylic into the title bar by setting the [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar) object's [ButtonBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonBackgroundColor) and [ButtonInactiveBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonInactiveBackgroundColor) properties to [Colors.Transparent](https://docs.microsoft.com/uwp/api/Windows.UI.Colors.Transparent).</span></span> 

```csharp
/// Extend acrylic into the title bar. 
private void ExtendAcrylicIntoTitleBar()
{
    CoreApplication.GetCurrentView().TitleBar.ExtendViewIntoTitleBar = true;
    ApplicationViewTitleBar titleBar = ApplicationView.GetForCurrentView().TitleBar;
    titleBar.ButtonBackgroundColor = Colors.Transparent;
    titleBar.ButtonInactiveBackgroundColor = Colors.Transparent;
}
```

<span data-ttu-id="ea1f1-266">Dieser Code kann in die [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_)-Methode Ihre App eingefügt werden (_App.xaml.cs_), nach dem Aufruf von [Window.Activate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.Activate) wie hier gezeigt, oder auf der ersten Seite Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-266">This code can be placed in your app's [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) method (_App.xaml.cs_), after the call to [Window.Activate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.Activate), as shown here, or in your app's first page.</span></span> 


```csharp
// Call your extend acrylic code in the OnLaunched event, after 
// calling Window.Current.Activate.
protected override void OnLaunched(LaunchActivatedEventArgs e)
{
    Frame rootFrame = Window.Current.Content as Frame;

    // Do not repeat app initialization when the Window already has content,
    // just ensure that the window is active
    if (rootFrame == null)
    {
        // Create a Frame to act as the navigation context and navigate to the first page
        rootFrame = new Frame();

        rootFrame.NavigationFailed += OnNavigationFailed;

        if (e.PreviousExecutionState == ApplicationExecutionState.Terminated)
        {
            //TODO: Load state from previously suspended application
        }

        // Place the frame in the current Window
        Window.Current.Content = rootFrame;
    }

    if (e.PrelaunchActivated == false)
    {
        if (rootFrame.Content == null)
        {
            // When the navigation stack isn't restored navigate to the first page,
            // configuring the new page by passing required information as a navigation
            // parameter
            rootFrame.Navigate(typeof(MainPage), e.Arguments);
        }
        // Ensure the current window is active
        Window.Current.Activate();

        // Extend acrylic
        ExtendAcrylicIntoTitleBar();
    }
}
```

<span data-ttu-id="ea1f1-267">Darüber hinaus müssen Sie den Titel der App, der normalerweise automatisch in der Titelleiste angezeigt wird, mit einem TextBlock ziehen, der `CaptionTextBlockStyle` verwendet.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-267">In addition, you'll need to draw your app's title, which normally appears automatically in the title bar, with a TextBlock using `CaptionTextBlockStyle`.</span></span> <span data-ttu-id="ea1f1-268">Weitere Informationen finden Sie unter [Anpassen der Titelleiste](../shell/title-bar.md).</span><span class="sxs-lookup"><span data-stu-id="ea1f1-268">For more info, see [Title bar customization](../shell/title-bar.md).</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="ea1f1-269">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="ea1f1-269">Do's and don'ts</span></span>
* <span data-ttu-id="ea1f1-270">Verwenden Sie Acryl als Hintergrundmaterial von nicht primären App-Oberflächen wie Navigationsbereichen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-270">Do use acrylic as the background material of non-primary app surfaces like navigation panes.</span></span>
* <span data-ttu-id="ea1f1-271">Dehnen Sie das Acryl auf mindestens einen Rand der App aus, um durch eine dezente Vermischung mit der Umgebung der App eine nahtlose Oberfläche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-271">Do extend acrylic to at least one edge of your app to provide a seamless experience by subtly blending with the app’s surroundings.</span></span>
* <span data-ttu-id="ea1f1-272">Platzieren Sie In-App- und Hintergrund-Acryl nicht direkt nebeneinander, um visuelle Spannung an den Rändern zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-272">Don’t place in-app and background acrylics directly adjacent to avoid visual tension at the seams.</span></span>
* <span data-ttu-id="ea1f1-273">Platzieren Sie nicht mehrere Acrylbereiche mit demselben Farbton und derselben Deckkraft nebeneinander, da dies eine unerwünschte sichtbare Naht erzeugt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-273">Don't place multiple acrylic panes with the same tint and opacity next to each other because this results in an undesirable visible seam.</span></span>
* <span data-ttu-id="ea1f1-274">Platzieren Sie keinen farbigen Text über Acryloberflächen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-274">Don’t place accent-colored text over acrylic surfaces.</span></span>

## <a name="how-we-designed-acrylic"></a><span data-ttu-id="ea1f1-275">Unser Acryl-Entwurfsansatz</span><span class="sxs-lookup"><span data-stu-id="ea1f1-275">How we designed acrylic</span></span>

<span data-ttu-id="ea1f1-276">Wir haben die Hauptkomponenten des Acryls optimiert, um eine individuelle Darstellung und einzigartige Eigenschaften zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-276">We fine-tuned acrylic’s key components to arrive at its unique appearance and properties.</span></span> <span data-ttu-id="ea1f1-277">Wir begannen mit Transparenz, weichzeichnungs- und Geräusch, flachen Oberflächen visuelle Tiefe und Dimension hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-277">We started with translucency, blur and noise to add visual depth and dimension to flat surfaces.</span></span> <span data-ttu-id="ea1f1-278">Dann fügten wir eine Ausschluss-Mischmodus-Ebene hinzu, um den Kontrast und die Lesbarkeit der auf dem Acrylhintergrund platzierten UI sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-278">We added an exclusion blend mode layer to ensure contrast and legibility of UI placed on an acrylic background.</span></span> <span data-ttu-id="ea1f1-279">Zuletzt fügten wir Farbtöne hinzu, um Personalisierungen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-279">Finally, we added color tint for personalization opportunities.</span></span> <span data-ttu-id="ea1f1-280">Zusammen ergeben diese Ebenen ein neues, einsatzbereites Material.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-280">In concert these layers add up to a fresh, usable material.</span></span>

![Acrylzusammensetzung](images/AcrylicRecipe_Diagram.jpg)
<br/><span data-ttu-id="ea1f1-282">Das Acryl setzt sich folgendermaßen zusammen: Hintergrund, Weichzeichnungsfilter, Ausschluss-Mischung, Überlagerung der Farbe/des Farbtons, Störungsfilter</span><span class="sxs-lookup"><span data-stu-id="ea1f1-282">The acrylic recipe: background, blur, exclusion blend, color/tint overlay, noise</span></span>


## <a name="get-the-sample-code"></a><span data-ttu-id="ea1f1-283">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="ea1f1-283">Get the sample code</span></span>

- <span data-ttu-id="ea1f1-284">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ea1f1-284">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="ea1f1-285">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="ea1f1-285">Related articles</span></span>

[**<span data-ttu-id="ea1f1-286">Reveal-highlight</span><span class="sxs-lookup"><span data-stu-id="ea1f1-286">Reveal highlight</span></span>**](reveal.md)
