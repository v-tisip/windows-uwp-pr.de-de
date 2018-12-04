---
description: Eine Art von Pinsel, der eine durchsichtige Textur erzeugt.
title: Acryl-Material
template: detail.hbs
ms.date: 08/9/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: yulikl
design-contact: rybick
dev-contact: jevansa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 336e4e64cc0b1819081a7e42b6e3e2d099355248
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8478532"
---
# <a name="acrylic-material"></a><span data-ttu-id="f8c13-104">Acryl-Material</span><span class="sxs-lookup"><span data-stu-id="f8c13-104">Acrylic material</span></span>

![Favoritenbild](images/header-acrylic.svg)

<span data-ttu-id="f8c13-106">Acryl ist eine Art von [Pinsel](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush) , der eine durchsichtige Textur erzeugt.</span><span class="sxs-lookup"><span data-stu-id="f8c13-106">Acrylic is a type of [Brush](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Media.Brush) that creates a translucent texture.</span></span> <span data-ttu-id="f8c13-107">Sie können Acryl auf App-Oberflächen anwenden, um Tiefe hinzuzufügen und eine visuelle Hierarchie herzustellen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-107">You can apply acrylic to app surfaces to add depth and help establish a visual hierarchy.</span></span>  <!-- By allowing user-selected wallpaper or colors to shine through, acrylic keeps users in touch with the OS personalization they've chosen. -->

> <span data-ttu-id="f8c13-108">**Wichtige APIs**: [AcrylicBrush-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.Background)</span><span class="sxs-lookup"><span data-stu-id="f8c13-108">**Important APIs**: [AcrylicBrush class](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.acrylicbrush), [Background property](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.Background)</span></span>

:::row:::
    :::column:::
        Acrylic in light theme
        ![Acrylic in light theme](images/Acrylic_LightTheme_Base.png)
    :::column-end:::
    :::column:::
        Acrylic in dark theme
        ![Acrylic in dark theme](images/Acrylic_DarkTheme_Base.png)
    :::column-end:::
:::row-end:::

## <a name="acrylic-and-the-fluent-design-system"></a><span data-ttu-id="f8c13-109">Acryl und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="f8c13-109">Acrylic and the Fluent Design System</span></span>

 <span data-ttu-id="f8c13-110">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="f8c13-110">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="f8c13-111">Acryl ist Komponente des Fluent Design-Systems, die physische Struktur (Material) und Tiefe zu Ihrer App hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f8c13-111">Acrylic is a Fluent Design System component that adds physical texture (material) and depth to your app.</span></span> <span data-ttu-id="f8c13-112">Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8c13-112">To learn more, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

 ## <a name="video-summary"></a><span data-ttu-id="f8c13-113">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="f8c13-113">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev002/player]

## <a name="examples"></a><span data-ttu-id="f8c13-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="f8c13-114">Examples</span></span>

:::row:::
    :::column span:::
        ![Some image](images/XAML-controls-gallery-app-icon.png)
    :::column-end:::
    :::column span="2":::
        **XAML Controls Gallery**<br>
        If you have the XAML Controls Gallery app installed, click <a href="xamlcontrolsgallery:/item/Acrylic">here</a> to open the app and see acrylic in action.

        <a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a><br>
        <a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a>
    :::column-end:::
:::row-end:::

## <a name="acrylic-blend-types"></a><span data-ttu-id="f8c13-115">Acrylmischungen</span><span class="sxs-lookup"><span data-stu-id="f8c13-115">Acrylic blend types</span></span>
<span data-ttu-id="f8c13-116">Die auffälligste Eigenschaft von Acryl ist seine Transparenz.</span><span class="sxs-lookup"><span data-stu-id="f8c13-116">Acrylic's most noticeable characteristic is its transparency.</span></span> <span data-ttu-id="f8c13-117">Es gibt zwei Acrylmischungen, die beeinflussen, welche Inhalte durch das Material sichtbar sind:</span><span class="sxs-lookup"><span data-stu-id="f8c13-117">There are two acrylic blend types that change what’s visible through the material:</span></span>
 - <span data-ttu-id="f8c13-118">**Hintergrund-Acryl** zeigt den Desktophintergrund und andere Fenster, die sich hinter der derzeit aktiven App befinden. Dabei wird Tiefe zwischen den Fenstern der Anwendung hinzugefügt, während die Personalisierungseinstellungen des Benutzers angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-118">**Background acrylic** reveals the desktop wallpaper and other windows that are behind the currently active app, adding depth between application windows while celebrating the user’s personalization preferences.</span></span>
 - <span data-ttu-id="f8c13-119">**In-App-Acryl** fügt Tiefenwirkung innerhalb des App-Frames hinzu, wodurch sowohl Fokus als auch Hierarchie erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-119">**In-app acrylic** adds a sense of depth within the app frame, providing both focus and hierarchy.</span></span>

 ![Hintergrund-Acryl](images/BackgroundAcrylic_DarkTheme.png)

 ![In-App-Acryl](images/AppAcrylic_DarkTheme.png)

 <span data-ttu-id="f8c13-122">Schichten Sie mehrere acryloberflächen vorsichtig: mehrere Schichten von Hintergrund-Acryl ablenkende optischen täuschungen erstellen können.</span><span class="sxs-lookup"><span data-stu-id="f8c13-122">Layer multiple acrylic surfaces with caution: multiple layers of background acrylic can create distracting optical illusions.</span></span>

## <a name="when-to-use-acrylic"></a><span data-ttu-id="f8c13-123">Wann sollte Acryl verwendet werden?</span><span class="sxs-lookup"><span data-stu-id="f8c13-123">When to use acrylic</span></span>

* <span data-ttu-id="f8c13-124">Verwenden Sie in-app-Acryl, für die Unterstützung von UI, z. B. NavigationView oder Inline-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="f8c13-124">Use in-app acrylic for supporting UI, such as NavigationView or in-line commanding elements.</span></span> 
* <span data-ttu-id="f8c13-125">Verwenden Sie Hintergrund-Acryl, vorübergehende UI-Elemente, z. B. Kontextmenüs, Flyouts und Licht-Dimsissable Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="f8c13-125">Use background acrylic for transient UI elements, such as context menus, flyouts, and light-dimsissable UI.</span></span><br /><span data-ttu-id="f8c13-126">Verwendung von Acryl in vorübergehende Szenarien, trägt dazu bei, eine visuelle Beziehung mit dem Inhalt beizubehalten, die die vorübergehende Benutzeroberfläche ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="f8c13-126">Using Acrylic in transient scenarios helps maintain a visual relationship with the content that triggered the transient UI.</span></span>

<span data-ttu-id="f8c13-127">Wenn Sie in-app-Acryl auf Flächen Navigation verwenden, sollten Sie Inhalt unterhalb der acrylbereich zur Verbesserung des Fluss in Ihrer app erweitern.</span><span class="sxs-lookup"><span data-stu-id="f8c13-127">If you are using in-app acrylic on navigation surfaces, consider extending content beneath the acrylic pane to improve the flow on your app.</span></span> <span data-ttu-id="f8c13-128">Mithilfe von NavigationView ist für Sie automatisch der Fall.</span><span class="sxs-lookup"><span data-stu-id="f8c13-128">Using NavigationView will do this for you automatically.</span></span> <span data-ttu-id="f8c13-129">Vermeiden Sie streifeneffekte, versuchen nicht, platzieren Sie mehrere Acryl Edge-to-Edge - kann dies jedoch eine unerwünschte Naht zwischen den beiden verschwommen Flächen erstellen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-129">However, to avoid creating a striping effect, try not to place multiple pieces of acrylic edge-to-edge - this can create an unwanted seam between the two blurred surfaces.</span></span> <span data-ttu-id="f8c13-130">Acryl kann ist ein Tool zum Erzeugen von visuellen Harmonie in Ihren Designs, jedoch bei inkorrekter Verwendung visuelle Störungen ergeben.</span><span class="sxs-lookup"><span data-stu-id="f8c13-130">Acrylic is a tool to bring visual harmony to your designs, but when used incorrectly, can result in visual noise.</span></span>

<span data-ttu-id="f8c13-131">Berücksichtigen Sie die folgenden Verwendungsmuster zu entscheiden, wie Acryl in Ihrer app zu integrieren:</span><span class="sxs-lookup"><span data-stu-id="f8c13-131">Consider the following usage patterns to decide how best to incorporate acrylic into your app:</span></span>

### <a name="horizontal-navigation-or-commanding"></a><span data-ttu-id="f8c13-132">Horizontale Navigation oder Befehle</span><span class="sxs-lookup"><span data-stu-id="f8c13-132">Horizontal navigation or commanding</span></span>

<span data-ttu-id="f8c13-133">Wenn Ihre app nicht NavigationView nutzen kann, und Sie Acryl selbst hinzufügen möchten, empfehlen wir die Verwendung von relativ durchsichtige Acryl mit 60 % Farbton-Deckkraft.</span><span class="sxs-lookup"><span data-stu-id="f8c13-133">If your app is not able to leverage NavigationView and you plan on adding acrylic on your own, we recommend using relatively translucent acrylic with 60% tint opacity.</span></span>
 - <span data-ttu-id="f8c13-134">Wenn der Bereich als Überlagerung über anderen Inhalten der App geöffnet wird, sollte dies [60% In-App-Acryl](#acrylic-theme-resources) sein.</span><span class="sxs-lookup"><span data-stu-id="f8c13-134">When the pane opens as an overlay above other app content, this should be [60% in-app acrylic](#acrylic-theme-resources)</span></span>

![Karten-app mit in-app horizontale Befehle](images/Maps_In_App_Acrylic_1.png)

<span data-ttu-id="f8c13-136">Darüber hinaus erhalten müssen Ihre Inhalte erweitern oder Bildlauf unter der Acryl am Anfang Ihrer app eine immersive und nahtlose Darstellung.</span><span class="sxs-lookup"><span data-stu-id="f8c13-136">In addition, having your content extend or scroll under the acrylic at the top will give your app a more immersive and seamless experience.</span></span>

### <a name="vertical-panes"></a><span data-ttu-id="f8c13-137">Vertikalen Bereichen</span><span class="sxs-lookup"><span data-stu-id="f8c13-137">Vertical Panes</span></span>

<span data-ttu-id="f8c13-138">Für vertikalen Bereichen oder Oberflächen, die Abschnitt Inhalt Ihrer App zu unterstützen, empfehlen wir, dass Sie einen nicht transparenten Hintergrund anstelle von Acryl verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-138">For vertical panes or surfaces that help section off content of your app, we recommend you use an opaque background instead of acrylic.</span></span> <span data-ttu-id="f8c13-139">Wenn Ihre vertikalen Bereichen über Inhalten öffnen, sollten wie im NavigationView **Compact** oder **minimierten** Modus, dass Sie in-app-Acryl verwenden, um die Seite Kontext zu behalten, wenn der Benutzer in diesem Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-139">If your vertical panes open on top of content, like in NavigationView's **Compact** or **Minimal** modes, we suggest you use in-app acrylic to help maintain the page's context when the user has this pane open.</span></span>

### <a name="transient-surfaces"></a><span data-ttu-id="f8c13-140">Vorübergehende Oberflächen</span><span class="sxs-lookup"><span data-stu-id="f8c13-140">Transient surfaces</span></span>

<span data-ttu-id="f8c13-141">Für apps mit Menü Flyouts, nicht Modal Popups, oder einfach-ausblendbarer Bereiche, es wird empfohlen, Hintergrund-Acryl zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-141">For apps with menu flyouts, non-modal popups, or light-dismiss panes, it is recommended to use background acrylic.</span></span>

![Mail-app-Muster mit einem Informationszwecken flyout](images/Mail_TransientContextMenu.png)

<span data-ttu-id="f8c13-143">Viele der unsere Steuerelemente werden Acryl in der Standardeinstellung verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-143">Many of our controls will use acrylic by default.</span></span> <span data-ttu-id="f8c13-144">[MenuFlyouts](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/menus)"," [AutoSuggestBox](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/auto-suggest-box)"," [ComboBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.combobox) "und" ähnliche Steuerelemente mit Licht-Dimiss Popups werden alle vorübergehende Acryl verwenden, wenn sie aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-144">[MenuFlyouts](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/menus), [AutoSuggestBox](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/auto-suggest-box), [ComboBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.combobox) and similar controls with light-dimiss popups will all use the transient acrylic when they are invoked.</span></span>

> [!Note]
> <span data-ttu-id="f8c13-145">Das Rendern von acryloberflächen ist GPU-intensiv, das Gerät den Energieverbrauch zu erhöhen und Akkulaufzeit verkürzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="f8c13-145">Rendering acrylic surfaces is GPU-intensive, which can increase device power consumption and shorten battery life.</span></span> <span data-ttu-id="f8c13-146">Acryleffekte werden automatisch deaktiviert, wenn Geräte Stromsparmodus versetzt, und Benutzer können acryleffekte für alle apps, deaktivieren, wenn der Benutzer.</span><span class="sxs-lookup"><span data-stu-id="f8c13-146">Acrylic effects are automatically disabled when devices enter Battery Saver mode, and users can disable acrylic effects for all apps, if they choose.</span></span>

## <a name="usability-and-adaptability"></a><span data-ttu-id="f8c13-147">Benutzerfreundlichkeit und Anpassungsfähigkeit</span><span class="sxs-lookup"><span data-stu-id="f8c13-147">Usability and adaptability</span></span>
<span data-ttu-id="f8c13-148">Acryl passt seine Darstellung automatisch an eine Vielzahl von Geräten und Kontext an.</span><span class="sxs-lookup"><span data-stu-id="f8c13-148">Acrylic automatically adapts its appearance for a wide variety of devices and contexts.</span></span>

<span data-ttu-id="f8c13-149">Im Modus mit hohem Kontrast wird Benutzern anstelle von Acryl weiterhin die vertraute Hintergrundfarbe ihrer Wahl angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f8c13-149">In High Contrast mode, users continue to see the familiar background color of their choosing in place of acrylic.</span></span> <span data-ttu-id="f8c13-150">Darüber hinaus werden sowohl Hintergrund-als auch in-app-Acryl als Volltonfarben angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f8c13-150">In addition, both background acrylic and in-app acrylic appear as a solid color:</span></span>
 - <span data-ttu-id="f8c13-151">Wenn der Benutzer deaktiviert die Transparenz in den Einstellungen > Personalisierung > Farben</span><span class="sxs-lookup"><span data-stu-id="f8c13-151">When the user turns off transparency in Settings > Personalization > Color</span></span>
 - <span data-ttu-id="f8c13-152">Wenn der Stromsparmodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="f8c13-152">When Battery Saver mode is activated</span></span>
 - <span data-ttu-id="f8c13-153">Bei Ausführen der App auf Low-End-Hardware</span><span class="sxs-lookup"><span data-stu-id="f8c13-153">When the app runs on low-end hardware</span></span>

<span data-ttu-id="f8c13-154">Darüber hinaus wird nur beim Hintergrund-Acryl seine Transparenz und Textur mit einer Volltonfarbe ersetzt:</span><span class="sxs-lookup"><span data-stu-id="f8c13-154">In addition, only background acrylic will replace its translucency and texture with a solid color:</span></span>
 - <span data-ttu-id="f8c13-155">Bei Deaktivierung eines App-Fensters auf dem Desktop</span><span class="sxs-lookup"><span data-stu-id="f8c13-155">When an app window on desktop deactivates</span></span>
 - <span data-ttu-id="f8c13-156">Bei Ausführen der UWP-App auf einem Telefon, der Xbox, HoloLens oder einem Tablet</span><span class="sxs-lookup"><span data-stu-id="f8c13-156">When the UWP app is running on phone, Xbox, HoloLens or tablet mode</span></span>

### <a name="legibility-considerations"></a><span data-ttu-id="f8c13-157">Hinweise zur Lesbarkeit</span><span class="sxs-lookup"><span data-stu-id="f8c13-157">Legibility considerations</span></span>
<span data-ttu-id="f8c13-158">Es muss sichergestellt werden, dass Texte, die in der App dargestellt werden, [das Kontrastverhältnis erfüllen](../accessibility/accessible-text-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8c13-158">It’s important to ensure that any text your app presents to users [meets contrast ratios](../accessibility/accessible-text-requirements.md).</span></span> <span data-ttu-id="f8c13-159">Wir haben die Acrylzusammensetzung optimiert, damit Texte in Schwarz oder Weiß mit hoher Farbauflösung oder in Mittelgrau auf Acryl die Kontrastverhältnisse erfüllen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-159">We’ve optimized the acrylic recipe so that high-color black, white or even medium-color gray text meets contrast ratios on top of acrylic.</span></span> <span data-ttu-id="f8c13-160">Die Standardeinstellungen der von der Plattform bereitgestellten Designressourcen weisen kontrastierende Färbungen mit 80% Deckkraft auf.</span><span class="sxs-lookup"><span data-stu-id="f8c13-160">The theme resources provided by the platform default to contrasting tint colors at 80% opacity.</span></span> <span data-ttu-id="f8c13-161">Beim Platzieren von Textkörper mit hoher Farbauflösung auf Acryl können Sie die Farbton-Deckkraft verringern und die Lesbarkeit gleichzeitig erhalten.</span><span class="sxs-lookup"><span data-stu-id="f8c13-161">When placing high-color body text on acrylic, you can reduce tint opacity while maintaining legibility.</span></span> <span data-ttu-id="f8c13-162">Im dunklen Modus kann die Farbton-Deckkraft 70% betragen, während das Acryl im hellen Modus ein Kontrastverhältnis von 50% Deckkraft erfüllt.</span><span class="sxs-lookup"><span data-stu-id="f8c13-162">In dark mode, tint opacity can be 70%, while light mode acrylic will meet contrast ratios at 50% opacity.</span></span>

<span data-ttu-id="f8c13-163">Es wird davon abgeraten, farbigen Text auf Ihren Acryloberflächen zu platzieren, da diese Kombinationen bei einem Schriftgrad von 15px wahrscheinlich nicht die Mindestanforderungen an das Kontrastverhältnis erfüllen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-163">We don't recommend placing accent-colored text on your acrylic surfaces because these combinations are likely to not pass minimum contrast ratio requirements at 15px font size.</span></span> <span data-ttu-id="f8c13-164">Platzieren Sie möglichst keine [Hyperlinks](../controls-and-patterns/hyperlinks.md) über Acrylelementen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-164">Try to avoid placing [hyperlinks](../controls-and-patterns/hyperlinks.md) over acrylic elements.</span></span> <span data-ttu-id="f8c13-165">Vergessen Sie darüber hinaus nicht die Auswirkungen auf die Lesbarkeit, wenn Sie den Acrylfarbton oder die Deckkraftstufe auf Werte außerhalb der von der Designressource bereitgestellten Plattformstandardeinstellungen einstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="f8c13-165">Also, if you choose to customize the acrylic tint color or opacity level outside of the platform defaults provided by the theme resource, keep the impact on legibility in mind.</span></span>

## <a name="acrylic-theme-resources"></a><span data-ttu-id="f8c13-166">Acryl-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="f8c13-166">Acrylic theme resources</span></span>
<span data-ttu-id="f8c13-167">Mit dem neuen XAML AcrylicBrush oder den vordefinierten AcrylicBrush-Designressourcen können Sie Acryl ganz einfach auf die Oberflächen Ihrer App anwenden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-167">You can easily apply acrylic to your app’s surfaces using the new XAML AcrylicBrush or predefined AcrylicBrush theme resources.</span></span> <span data-ttu-id="f8c13-168">Zunächst müssen Sie entscheiden, ob Sie In-App- oder Hintergrund-Acryl verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f8c13-168">First, you’ll need to decide whether to use in-app or background acrylic.</span></span> <span data-ttu-id="f8c13-169">Prüfen Sie die zuvor in diesem Artikel beschriebenen allgemeinen App-Muster auf Empfehlungen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-169">Be sure to review common app patterns described earlier in this article for recommendations.</span></span>

<span data-ttu-id="f8c13-170">Wir haben eine Sammlung von Pinsel-Designressourcen sowohl für Hintergrund- als auch In-App-Acrylarten erstellt, die das Design der App berücksichtigen und nach Bedarf wieder auf Volltonfarben zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-170">We’ve created a collection of brush theme resources for both background and in-app acrylic types that respect the app’s theme and fall back to solid colors as needed.</span></span> <span data-ttu-id="f8c13-171">Ressourcen mit der Benennung *AcrylicWindow* stellen Hintergrund-Acryl dar, während sich *AcrylicElement* auf In-App-Acryl bezieht.</span><span class="sxs-lookup"><span data-stu-id="f8c13-171">Resources named *AcrylicWindow* represent background acrylic, while *AcrylicElement* refers to in-app acrylic.</span></span>

<table>
    <tr>
        <th align="center"><span data-ttu-id="f8c13-172">Ressourcenschlüssel</span><span class="sxs-lookup"><span data-stu-id="f8c13-172">Resource key</span></span></th>
        <th align="center"><span data-ttu-id="f8c13-173">Farbton-Deckkraft</span><span class="sxs-lookup"><span data-stu-id="f8c13-173">Tint opacity</span></span></th>
        <th align="center"><a href="color.md"><span data-ttu-id="f8c13-174">Fallbackfarbe</span><span class="sxs-lookup"><span data-stu-id="f8c13-174">Fallback color</span></span></a> </th>
    </tr>
    <tr>
        <td> <span data-ttu-id="f8c13-175">SystemControlAcrylicWindowBrush, SystemControlAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-175">SystemControlAcrylicWindowBrush, SystemControlAcrylicElementBrush</span></span> <br/> <span data-ttu-id="f8c13-176">SystemControlChromeLowAcrylicWindowBrush, SystemControlChromeLowAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-176">SystemControlChromeLowAcrylicWindowBrush, SystemControlChromeLowAcrylicElementBrush</span></span> <br/> <span data-ttu-id="f8c13-177">SystemControlBaseHighAcrylicWindowBrush, SystemControlBaseHighAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-177">SystemControlBaseHighAcrylicWindowBrush, SystemControlBaseHighAcrylicElementBrush</span></span> <br/> <span data-ttu-id="f8c13-178">SystemControlBaseLowAcrylicWindowBrush, SystemControlBaseLowAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-178">SystemControlBaseLowAcrylicWindowBrush, SystemControlBaseLowAcrylicElementBrush</span></span> <br/> <span data-ttu-id="f8c13-179">SystemControlAltHighAcrylicWindowBrush, SystemControlAltHighAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-179">SystemControlAltHighAcrylicWindowBrush, SystemControlAltHighAcrylicElementBrush</span></span> <br/> <span data-ttu-id="f8c13-180">SystemControlAltLowAcrylicWindowBrush, SystemControlAltLowAcrylicElementBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-180">SystemControlAltLowAcrylicWindowBrush, SystemControlAltLowAcrylicElementBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="f8c13-181">80%</span><span class="sxs-lookup"><span data-stu-id="f8c13-181">80%</span></span> </td>
        <td> <span data-ttu-id="f8c13-182">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="f8c13-182">ChromeMedium</span></span> <br/> <span data-ttu-id="f8c13-183">ChromeLow</span><span class="sxs-lookup"><span data-stu-id="f8c13-183">ChromeLow</span></span> <br/><br/> <span data-ttu-id="f8c13-184">BaseHigh</span><span class="sxs-lookup"><span data-stu-id="f8c13-184">BaseHigh</span></span> <br/><br/> <span data-ttu-id="f8c13-185">BaseLow</span><span class="sxs-lookup"><span data-stu-id="f8c13-185">BaseLow</span></span> <br/><br/> <span data-ttu-id="f8c13-186">AltHigh</span><span class="sxs-lookup"><span data-stu-id="f8c13-186">AltHigh</span></span> <br/><br/> <span data-ttu-id="f8c13-187">AltLow</span><span class="sxs-lookup"><span data-stu-id="f8c13-187">AltLow</span></span> </td>
    </tr>
    </tr>
        <td> <span data-ttu-id="f8c13-188"><b>Empfohlene Verwendung:</b> Hierbei handelt es sich um allgemeine Acrylressourcen, die sich in einer Vielzahl von Verwendungsarten gut einsetzen lassen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-188"><b>Recommended usage:</b> These are general-purpose acrylic resources that work well in a wide variety of usages.</span></span> <span data-ttu-id="f8c13-189">Wenn Ihre App sekundären Text in der Farbe AltMedium mit einer kleineren Textgröße als 18px verwendet, platzieren Sie eine Acrylressource von 80% hinter dem Text, um die <a href="../accessibility/accessible-text-requirements.md">Anforderungen an das Kontrastverhältnis zu erfüllen</a>.</span><span class="sxs-lookup"><span data-stu-id="f8c13-189">If your app uses secondary text of AltMedium color with text size smaller than 18px, place an 80% acrylic resource behind the text to <a href="../accessibility/accessible-text-requirements.md">meet contrast ratio requirements</a>.</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="f8c13-190">SystemControlAcrylicWindowMediumHighBrush, SystemControlAcrylicElementMediumHighBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-190">SystemControlAcrylicWindowMediumHighBrush, SystemControlAcrylicElementMediumHighBrush</span></span> <br/> <span data-ttu-id="f8c13-191">SystemControlBaseHighAcrylicWindowMediumHighBrush, SystemControlBaseHighAcrylicElementMediumHighBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-191">SystemControlBaseHighAcrylicWindowMediumHighBrush, SystemControlBaseHighAcrylicElementMediumHighBrush</span></span> </td>
        <td align="center"> <span data-ttu-id="f8c13-192">70%</span><span class="sxs-lookup"><span data-stu-id="f8c13-192">70%</span></span> </td>
        <td> <span data-ttu-id="f8c13-193">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="f8c13-193">ChromeMedium</span></span> <br/><br/> <span data-ttu-id="f8c13-194">BaseHigh</span><span class="sxs-lookup"><span data-stu-id="f8c13-194">BaseHigh</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="f8c13-195"><b>Empfohlene Verwendung:</b> Wenn Ihre app sekundären Text in der Farbe AltMedium mit einer Textgröße von 18px oder mehr verwendet, können Sie diese mehr durchsichtigen acrylressourcen 70 % hinter dem Text platzieren.</span><span class="sxs-lookup"><span data-stu-id="f8c13-195"><b>Recommended usage:</b> If your app uses secondary text of AltMedium color with a text size of 18px or larger, you can place these more translucent 70% acrylic resources behind the text.</span></span> <span data-ttu-id="f8c13-196">Wir empfehlen die Verwendung dieser Ressourcen in den oberen horizontalen Navigations- und Steuerungsbereichen in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="f8c13-196">We recommend using these resources in your app's top horizontal navigation and commanding areas.</span></span>  </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="f8c13-197">SystemControlChromeHighAcrylicWindowMediumBrush, SystemControlChromeHighAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-197">SystemControlChromeHighAcrylicWindowMediumBrush, SystemControlChromeHighAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="f8c13-198">SystemControlChromeMediumAcrylicWindowMediumBrush, SystemControlChromeMediumAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-198">SystemControlChromeMediumAcrylicWindowMediumBrush, SystemControlChromeMediumAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="f8c13-199">SystemControlChromeMediumLowAcrylicWindowMediumBrush, SystemControlChromeMediumLowAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-199">SystemControlChromeMediumLowAcrylicWindowMediumBrush, SystemControlChromeMediumLowAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="f8c13-200">SystemControlBaseHighAcrylicWindowMediumBrush, SystemControlBaseHighAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-200">SystemControlBaseHighAcrylicWindowMediumBrush, SystemControlBaseHighAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="f8c13-201">SystemControlBaseMediumLowAcrylicWindowMediumBrush, SystemControlBaseMediumLowAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-201">SystemControlBaseMediumLowAcrylicWindowMediumBrush, SystemControlBaseMediumLowAcrylicElementMediumBrush</span></span> <br/> <span data-ttu-id="f8c13-202">SystemControlAltMediumLowAcrylicWindowMediumBrush, SystemControlAltMediumLowAcrylicElementMediumBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-202">SystemControlAltMediumLowAcrylicWindowMediumBrush, SystemControlAltMediumLowAcrylicElementMediumBrush</span></span>  </td>
        <td align="center"> <span data-ttu-id="f8c13-203">60%</span><span class="sxs-lookup"><span data-stu-id="f8c13-203">60%</span></span> </td>
        <td> <span data-ttu-id="f8c13-204">ChromeHigh</span><span class="sxs-lookup"><span data-stu-id="f8c13-204">ChromeHigh</span></span> <br/><br/> <span data-ttu-id="f8c13-205">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="f8c13-205">ChromeMedium</span></span> <br/><br/> <span data-ttu-id="f8c13-206">ChromeMediumLow</span><span class="sxs-lookup"><span data-stu-id="f8c13-206">ChromeMediumLow</span></span> <br/><br/> <span data-ttu-id="f8c13-207">BaseHigh</span><span class="sxs-lookup"><span data-stu-id="f8c13-207">BaseHigh</span></span> <br/><br/> <span data-ttu-id="f8c13-208">BaseLow</span><span class="sxs-lookup"><span data-stu-id="f8c13-208">BaseLow</span></span> <br/><br/> <span data-ttu-id="f8c13-209">AltMediumLow</span><span class="sxs-lookup"><span data-stu-id="f8c13-209">AltMediumLow</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="f8c13-210"><b>Empfohlene Verwendung:</b> Wenn nur primärer Text der Farbe AltHigh über Acryl platziert wird, kann Ihre App diese Ressourcen von 60% verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-210"><b>Recommended usage:</b> When placing only primary text of AltHigh color over acrylic, your app can utilize these 60% resources.</span></span> <span data-ttu-id="f8c13-211">Es wird empfohlen, den <a href="../controls-and-patterns/navigationview.md">vertikalen Navigationsbereich</a> Ihrer App, d.h. das Hamburger-Menü, mit 60% Acryl zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-211">We recommend painting your app's <a href="../controls-and-patterns/navigationview.md">vertical navigation pane</a>, i.e. hamburger menu, with 60% acrylic.</span></span> </td>
    </tr>
</table>

<span data-ttu-id="f8c13-212">Zusätzlich zu farbneutralem Acryl haben wir Ressourcen hinzugefügt, mit denen sich das Acryl mithilfe von benutzerdefinierten Akzentfarben färben lässt.</span><span class="sxs-lookup"><span data-stu-id="f8c13-212">In addition to color-neutral acrylic, we've also added resources that tint acrylic using the user-specified accent color.</span></span> <span data-ttu-id="f8c13-213">Wir empfehlen, farbiges Acryl sparsam zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-213">We recommend using colored acrylic sparingly.</span></span> <span data-ttu-id="f8c13-214">Platzieren Sie für die bereitgestellten Varianten dark1 und dark2 weißen bzw. hellfarbigen Text der Textfarbe des dunklen Designs entsprechend über diesen Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-214">For the dark1 and dark2 variants provided, place white or light-colored text consistent with dark theme text color over these resources.</span></span>
<table>
    <tr>
        <th align="center"><span data-ttu-id="f8c13-215">Ressourcenschlüssel</span><span class="sxs-lookup"><span data-stu-id="f8c13-215">Resource key</span></span></th>
        <th align="center"><span data-ttu-id="f8c13-216">Farbton-Deckkraft</span><span class="sxs-lookup"><span data-stu-id="f8c13-216">Tint opacity</span></span></th>
        <th align="center"><a href="color.md"><span data-ttu-id="f8c13-217">Farbton und Fallbackfarben</span><span class="sxs-lookup"><span data-stu-id="f8c13-217">Tint and Fallback colors</span></span></a> </th>
    </tr>
    <tr>
        <td> <span data-ttu-id="f8c13-218">SystemControlAccentAcrylicWindowAccentMediumHighBrush, SystemControlAccentAcrylicElementAccentMediumHighBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-218">SystemControlAccentAcrylicWindowAccentMediumHighBrush, SystemControlAccentAcrylicElementAccentMediumHighBrush</span></span>  </td>
        <td align="center"> <span data-ttu-id="f8c13-219">70%</span><span class="sxs-lookup"><span data-stu-id="f8c13-219">70%</span></span> </td>
        <td> <span data-ttu-id="f8c13-220">SystemAccentColor</span><span class="sxs-lookup"><span data-stu-id="f8c13-220">SystemAccentColor</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="f8c13-221">SystemControlAccentDark1AcrylicWindowAccentDark1Brush, SystemControlAccentDark1AcrylicElementAccentDark1Brush</span><span class="sxs-lookup"><span data-stu-id="f8c13-221">SystemControlAccentDark1AcrylicWindowAccentDark1Brush, SystemControlAccentDark1AcrylicElementAccentDark1Brush</span></span>  </td>
        <td align="center"> <span data-ttu-id="f8c13-222">80%</span><span class="sxs-lookup"><span data-stu-id="f8c13-222">80%</span></span> </td>
        <td> <span data-ttu-id="f8c13-223">SystemAccentColorDark1</span><span class="sxs-lookup"><span data-stu-id="f8c13-223">SystemAccentColorDark1</span></span> </td>
    </tr>
    <tr>
        <td> <span data-ttu-id="f8c13-224">SystemControlAccentDark2AcrylicWindowAccentDark2MediumHighBrush, SystemControlAccentDark2AcrylicElementAccentDark2MediumHighBrush</span><span class="sxs-lookup"><span data-stu-id="f8c13-224">SystemControlAccentDark2AcrylicWindowAccentDark2MediumHighBrush, SystemControlAccentDark2AcrylicElementAccentDark2MediumHighBrush</span></span>  </td>
        <td align="center"> <span data-ttu-id="f8c13-225">70%</span><span class="sxs-lookup"><span data-stu-id="f8c13-225">70%</span></span> </td>
        <td> <span data-ttu-id="f8c13-226">SystemAccentColorDark2</span><span class="sxs-lookup"><span data-stu-id="f8c13-226">SystemAccentColorDark2</span></span> </td>
    </tr>
</table>


<span data-ttu-id="f8c13-227">Um eine bestimmte Oberfläche zu zeichnen, wenden Sie eines der oben genannten Designressourcen auf Elementhintergründe an. Verfahren Sie dabei genauso, wie Sie die anderen Pinselressourcen anwenden würden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-227">To paint a specific surface, apply one of the above theme resources to element backgrounds just as you would apply any other brush resource.</span></span>

```xaml
<Grid Background="{ThemeResource SystemControlAcrylicElementBrush}">
```

## <a name="custom-acrylic-brush"></a><span data-ttu-id="f8c13-228">Benutzerdefinierter Acrylpinsel</span><span class="sxs-lookup"><span data-stu-id="f8c13-228">Custom acrylic brush</span></span>
<span data-ttu-id="f8c13-229">Sie können einen Farbton zum Acryl Ihrer App hinzufügen, um das Branding anzuzeigen oder ein optisches Gleichgewicht mit anderen Elementen auf dieser Seite zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-229">You may choose to add a color tint to your app’s acrylic to show branding or provide visual balance with other elements on the page.</span></span> <span data-ttu-id="f8c13-230">Um Farbe und keine Graustufen anzuzeigen, müssen Sie Ihre eigenen Acrylpinsel mithilfe der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="f8c13-230">To show color rather than greyscale, you’ll need to define your own acrylic brushes using the following properties.</span></span>
 - <span data-ttu-id="f8c13-231">**TintColor**: die Überlagerungsschicht der Farbe/des Farbtons.</span><span class="sxs-lookup"><span data-stu-id="f8c13-231">**TintColor**: the color/tint overlay layer.</span></span> <span data-ttu-id="f8c13-232">Sie sollten sowohl den RGB-Farbwert als auch die Deckkraft des Alphakanals angeben.</span><span class="sxs-lookup"><span data-stu-id="f8c13-232">Consider specifying both the RGB color value and alpha channel opacity.</span></span>
 - <span data-ttu-id="f8c13-233">**TintOpacity**: die Deckkraft der Farbtonschicht.</span><span class="sxs-lookup"><span data-stu-id="f8c13-233">**TintOpacity**: the opacity of the tint layer.</span></span> <span data-ttu-id="f8c13-234">Wir empfehlen 80 % Deckkraft als Ausgangspunkt, obwohl verschiedene Farben bei anderer Translucencies aussehen können.</span><span class="sxs-lookup"><span data-stu-id="f8c13-234">We recommend 80% opacity as a starting point, although different colors may look more compelling at other translucencies.</span></span>
 - <span data-ttu-id="f8c13-235">**BackgroundSource**: die Kennzeichnung zum Festlegen, ob Sie Hintergrund- oder In-App Acryl verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f8c13-235">**BackgroundSource**: the flag to specify whether you want background or in-app acrylic.</span></span>
 - <span data-ttu-id="f8c13-236">**FallbackColor**: die Volltonfarbe, die Acryl in den Stromsparmodus ersetzt.</span><span class="sxs-lookup"><span data-stu-id="f8c13-236">**FallbackColor**: the solid color that replaces acrylic in Battery Saver.</span></span> <span data-ttu-id="f8c13-237">Im Fall von Hintergrund-Acryl ersetzt die Fallbackfarbe das Acryl auch, wenn Ihre App nicht im aktiven Desktopfenster angezeigt wird oder wenn die App auf dem Telefon oder der Xbox ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f8c13-237">For background acrylic, fallback color also replaces acrylic when your app isn’t in the active desktop window or when the app is running on phone and Xbox.</span></span>

![Acrylmuster für das helle Design](images/CustomAcrylic_Swatches_LightTheme.png)

![Acrylmuster für das dunkle Design](images/CustomAcrylic_Swatches_DarkTheme.png)

<span data-ttu-id="f8c13-240">Um einen Acrylpinsel hinzuzufügen, definieren Sie die Ressourcen für das dunkle und das helle Design und für das Design mit hohem Kontrast.</span><span class="sxs-lookup"><span data-stu-id="f8c13-240">To add an acrylic brush, define the three resources for dark, light and high contrast themes.</span></span> <span data-ttu-id="f8c13-241">Beachten Sie, dass wir bei hohem Kontrast die Verwendung eines SolidColorBrush mit demselben X:Key wie für den dunklen/hellen AcrylicBrush zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-241">Note that in high contrast, we recommend using a SolidColorBrush with the same x:Key as the dark/light AcrylicBrush.</span></span>

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

<span data-ttu-id="f8c13-242">Das folgende Beispiel zeigt, wie Sie AcrylicBrush in Code angeben.</span><span class="sxs-lookup"><span data-stu-id="f8c13-242">The following sample shows how to declare AcrylicBrush in code.</span></span> <span data-ttu-id="f8c13-243">Wenn Ihre App mehrere Betriebssystemziele unterstützt, müssen Sie sicherstellen, dass diese API auf dem Gerät des Benutzers verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="f8c13-243">If your app supports multiple OS targets, be sure to check that this API is available on the user’s machine.</span></span>

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

## <a name="extend-acrylic-into-the-title-bar"></a><span data-ttu-id="f8c13-244">Erweitern Sie Acryl auf die Titelleiste</span><span class="sxs-lookup"><span data-stu-id="f8c13-244">Extend acrylic into the title bar</span></span>

<span data-ttu-id="f8c13-245">Um Ihrem App-Fenster ein nahtloses Aussehen zu verleihen, können Sie im Bereich der Titelleiste Acryl verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-245">To give your app's window a seamless look, you can use acrylic in the title bar area.</span></span> <span data-ttu-id="f8c13-246">In diesem Beispiel wird Acryl in die Titelleiste erweitert, indem die [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar) der Eigenschaften des Objekts [ButtonBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonBackgroundColor) und [ButtonInactiveBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonInactiveBackgroundColor) auf [Colors.Transparent](https://docs.microsoft.com/uwp/api/Windows.UI.Colors.Transparent) festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-246">This example extends acrylic into the title bar by setting the [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar) object's [ButtonBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonBackgroundColor) and [ButtonInactiveBackgroundColor](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewTitleBar.ButtonInactiveBackgroundColor) properties to [Colors.Transparent](https://docs.microsoft.com/uwp/api/Windows.UI.Colors.Transparent).</span></span> 

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

<span data-ttu-id="f8c13-247">Dieser Code kann in die [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_)-Methode Ihre App eingefügt werden (_App.xaml.cs_), nach dem Aufruf von [Window.Activate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.Activate) wie hier gezeigt, oder auf der ersten Seite Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="f8c13-247">This code can be placed in your app's [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) method (_App.xaml.cs_), after the call to [Window.Activate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.Activate), as shown here, or in your app's first page.</span></span> 


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

<span data-ttu-id="f8c13-248">Darüber hinaus müssen Sie den Titel der App, der normalerweise automatisch in der Titelleiste angezeigt wird, mit einem TextBlock ziehen, der `CaptionTextBlockStyle` verwendet.</span><span class="sxs-lookup"><span data-stu-id="f8c13-248">In addition, you'll need to draw your app's title, which normally appears automatically in the title bar, with a TextBlock using `CaptionTextBlockStyle`.</span></span> <span data-ttu-id="f8c13-249">Weitere Informationen finden Sie unter [Anpassen der Titelleiste](../shell/title-bar.md).</span><span class="sxs-lookup"><span data-stu-id="f8c13-249">For more info, see [Title bar customization](../shell/title-bar.md).</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="f8c13-250">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="f8c13-250">Do's and don'ts</span></span>
* <span data-ttu-id="f8c13-251">Verwenden Sie Acryl als Hintergrundmaterial von nicht primären App-Oberflächen wie Navigationsbereichen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-251">Do use acrylic as the background material of non-primary app surfaces like navigation panes.</span></span>
* <span data-ttu-id="f8c13-252">Dehnen Sie das Acryl auf mindestens einen Rand der App aus, um durch eine dezente Vermischung mit der Umgebung der App eine nahtlose Oberfläche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-252">Do extend acrylic to at least one edge of your app to provide a seamless experience by subtly blending with the app’s surroundings.</span></span>
* <span data-ttu-id="f8c13-253">Versehen Sie keine desktop Arylic auf großen Hintergrund Oberflächen Ihrer App – dies bricht das mentale Modell der Acryl in erster Linie für die vorübergehende Flächen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f8c13-253">Don't put desktop arylic on large background surfaces of your app - this breaks the mental model of acrylic being used primarily for transient surfaces.</span></span>
* <span data-ttu-id="f8c13-254">Platzieren Sie In-App- und Hintergrund-Acryl nicht direkt nebeneinander, um visuelle Spannung an den Rändern zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="f8c13-254">Don’t place in-app and background acrylics directly adjacent to avoid visual tension at the seams.</span></span>
* <span data-ttu-id="f8c13-255">Platzieren Sie nicht mehrere Acrylbereiche mit demselben Farbton und derselben Deckkraft nebeneinander, da dies eine unerwünschte sichtbare Naht erzeugt.</span><span class="sxs-lookup"><span data-stu-id="f8c13-255">Don't place multiple acrylic panes with the same tint and opacity next to each other because this results in an undesirable visible seam.</span></span>
* <span data-ttu-id="f8c13-256">Platzieren Sie keinen farbigen Text über Acryloberflächen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-256">Don’t place accent-colored text over acrylic surfaces.</span></span>

## <a name="how-we-designed-acrylic"></a><span data-ttu-id="f8c13-257">Unser Acryl-Entwurfsansatz</span><span class="sxs-lookup"><span data-stu-id="f8c13-257">How we designed acrylic</span></span>

<span data-ttu-id="f8c13-258">Wir haben die Hauptkomponenten des Acryls optimiert, um eine individuelle Darstellung und einzigartige Eigenschaften zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f8c13-258">We fine-tuned acrylic’s key components to arrive at its unique appearance and properties.</span></span> <span data-ttu-id="f8c13-259">Wir begannen mit Transparenz, weichzeichnungs- und störungsfiltern visuelle Tiefe und Dimension, flachen Oberflächen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-259">We started with translucency, blur and noise to add visual depth and dimension to flat surfaces.</span></span> <span data-ttu-id="f8c13-260">Dann fügten wir eine Ausschluss-Mischmodus-Ebene hinzu, um den Kontrast und die Lesbarkeit der auf dem Acrylhintergrund platzierten UI sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-260">We added an exclusion blend mode layer to ensure contrast and legibility of UI placed on an acrylic background.</span></span> <span data-ttu-id="f8c13-261">Zuletzt fügten wir Farbtöne hinzu, um Personalisierungen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f8c13-261">Finally, we added color tint for personalization opportunities.</span></span> <span data-ttu-id="f8c13-262">Zusammen ergeben diese Ebenen ein neues, einsatzbereites Material.</span><span class="sxs-lookup"><span data-stu-id="f8c13-262">In concert these layers add up to a fresh, usable material.</span></span>

![Acrylzusammensetzung](images/AcrylicRecipe_Diagram.jpg)
<br/><span data-ttu-id="f8c13-264">Das Acryl setzt sich folgendermaßen zusammen: Hintergrund, Weichzeichnungsfilter, Ausschluss-Mischung, Überlagerung der Farbe/des Farbtons, Störungsfilter</span><span class="sxs-lookup"><span data-stu-id="f8c13-264">The acrylic recipe: background, blur, exclusion blend, color/tint overlay, noise</span></span>


## <a name="get-the-sample-code"></a><span data-ttu-id="f8c13-265">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="f8c13-265">Get the sample code</span></span>

- <span data-ttu-id="f8c13-266">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f8c13-266">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="f8c13-267">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="f8c13-267">Related articles</span></span>

[**<span data-ttu-id="f8c13-268">Reveal-highlight</span><span class="sxs-lookup"><span data-stu-id="f8c13-268">Reveal highlight</span></span>**](reveal.md)
