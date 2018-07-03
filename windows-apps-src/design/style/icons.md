---
author: mijacobs
Description: Good icons harmonize with typography and with the rest of the design language. They don’t mix metaphors, and they communicate only what’s needed, as speedily and simply as possible.
title: Symbole
ms.assetid: b90ac02d-5467-4304-99bd-292d6272a014
label: Icons
template: detail.hbs
ms.author: mijacobs
ms.date: 05/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
design-contact: Judysa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 077967c37f76c8f1d0942f365344de65db13b041
ms.sourcegitcommit: ce45a2bc5ca6794e97d188166172f58590e2e434
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "1983573"
---
# <a name="icons-for-uwp-apps"></a><span data-ttu-id="2882e-103">Symbole für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="2882e-103">Icons for UWP apps</span></span>

![Headerbild für Symbole](images/icons/header-icons.png)

<span data-ttu-id="2882e-105">Symbole bieten eine visuelle Kurzform für eine Aktion, ein Konzept oder ein Produkt.</span><span class="sxs-lookup"><span data-stu-id="2882e-105">Icons provide a visual shorthand for an action, concept, or product.</span></span> <span data-ttu-id="2882e-106">Durch das Komprimieren der Bedeutung in ein symbolisches Bild können Symbole Sprachhürden überwinden und dazu beitragen, eine sehr wertvolle Ressource zu sparen: Platz auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="2882e-106">By compressing meaning into a symbolic image, icons can cross language barriers and help conserve an extremely valuable resource: screen space.</span></span> 

<span data-ttu-id="2882e-107">Symbole können in Apps angezeigt werden – und außerhalb von Apps:</span><span class="sxs-lookup"><span data-stu-id="2882e-107">Icons can appear in apps—and outside them:</span></span> 

<span data-ttu-id="2882e-108">:::row::: :::column::: **Symbole in der App**</span><span class="sxs-lookup"><span data-stu-id="2882e-108">:::row::: :::column::: **Icons inside the app**</span></span>

        ![icons inside the app](images/icons/inside-icons.png)
        Inside your app, you use icons to represent an action, such as copying text or navigating to the settings page.
    :::column-end:::
    :::column:::
        **Icons outside the app**

        ![icons outside the app](images/icons/outside-icons.jpg)
         Outside your app, Windows uses an icon to represent your app in the start menu and in the taskbar. If the user chooses to pin your app to the start menu, your app's start tile can feature your app's icon. Your app's icon appears in the title bar and you can choose to create a splash screen with your app's logo.
    :::column-end:::
<span data-ttu-id="2882e-109">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-109">:::row-end:::</span></span>

<span data-ttu-id="2882e-110">In diesem Artikel werden Symbole in Ihrer App beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2882e-110">This article describes icons within your app.</span></span> <span data-ttu-id="2882e-111">Informationen zu Symbolen außerhalb Ihrer App (App-Symbole) finden Sie im [Artikel zu App- und Kachelsymbolen](/windows/uwp/design/shell/tiles-and-notifications/app-assets).</span><span class="sxs-lookup"><span data-stu-id="2882e-111">To learn about icons outside your app (app icons), see the [app and tile icons article](/windows/uwp/design/shell/tiles-and-notifications/app-assets).</span></span>

## <a name="when-to-use-icons"></a><span data-ttu-id="2882e-112">Wann Symbole verwendet werden sollten</span><span class="sxs-lookup"><span data-stu-id="2882e-112">When to use icons</span></span>

<span data-ttu-id="2882e-113">Symbole können Platz sparen, aber wann ist eine Verwendung sinnvoll?</span><span class="sxs-lookup"><span data-stu-id="2882e-113">Icons can save space, but when should you use them?</span></span> 

<span data-ttu-id="2882e-114">:::row::: :::column::: ![Sinnvoll](images/do.svg) ![Standardbild für Symbole</span><span class="sxs-lookup"><span data-stu-id="2882e-114">:::row::: :::column::: ![do](images/do.svg) ![icons standard image</span></span>](images/icons/icons-standard.svg)<br>

        Use an icon for actions, like cut, copy, paste, and save, or for navigation items in a navigation menu.
    :::column-end:::
    :::column:::
        ![don't](images/dont.svg)
        ![icons concept image](images/icons/icons-concept.svg)<br>

        Use an icon if one already exists for the concept you want to represent. (To see whether an icon exists, check the Segoe icon list.)
    :::column-end:::
<span data-ttu-id="2882e-115">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-115">:::row-end:::</span></span>

<span data-ttu-id="2882e-116">:::row::: :::column::: ![Sinnvoll](images/do.svg) ![Einkaufswagensymbol</span><span class="sxs-lookup"><span data-stu-id="2882e-116">:::row::: :::column::: ![do](images/do.svg) ![icon shopping cart</span></span>](images/icons/icon-shopping-cart.svg)<br>

        Use an icon if it's easy for the user to understand what the icon means and it's simple enough to be clear at small sizes.
    :::column-end:::
    :::column:::
        ![dont](images/dont.svg)
        ![icons concept image](images/icons/icon-bad-example.png)<br>

        Don't use an icon if its meaning isn't clear, or if making it clear requires a complex shape.
    :::column-end:::
<span data-ttu-id="2882e-117">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-117">:::row-end:::</span></span>



## <a name="using-the-right-type-of-icon"></a><span data-ttu-id="2882e-118">Verwendung der richtigen Art von Symbol</span><span class="sxs-lookup"><span data-stu-id="2882e-118">Using the right type of icon</span></span>

<span data-ttu-id="2882e-119">Es gibt viele Möglichkeiten, ein Symbol zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2882e-119">There are many ways to create an icon.</span></span> <span data-ttu-id="2882e-120">Sie können eine Symbolschriftart wie Segoe MDL2 Assets verwenden.</span><span class="sxs-lookup"><span data-stu-id="2882e-120">You can use a symbol font like Segoe MDL2 Assets.</span></span> <span data-ttu-id="2882e-121">Sie können ein eigenes vektorbasiertes Bild erstellen.</span><span class="sxs-lookup"><span data-stu-id="2882e-121">You could create you own vector-based image.</span></span> <span data-ttu-id="2882e-122">Sie können sogar ein Bitmap-Bild verwenden, auch wenn das nicht empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="2882e-122">You can even use a bitmap image, although we don't recommend it.</span></span> <span data-ttu-id="2882e-123">Hier ist eine Übersicht über die verschiedenen Möglichkeiten zum Hinzufügen eines Symbols zu Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="2882e-123">Here's a summary of the different ways you can add an icon to your app.</span></span> 

### <a name="use-a-predefined-icon"></a><span data-ttu-id="2882e-124">Verwenden eines vordefinierten Symbols</span><span class="sxs-lookup"><span data-stu-id="2882e-124">Use a predefined icon.</span></span>
<span data-ttu-id="2882e-125">:::row::: :::column::: Microsoft bietet mehr als 1.000 Symbole in Form der Segoe MDL2 Assets-Schrift.</span><span class="sxs-lookup"><span data-stu-id="2882e-125">:::row::: :::column::: Microsoft provides over 1000 icons in the form of the Segoe MDL2 Assets font.</span></span> <span data-ttu-id="2882e-126">Möglicherweise ist es nicht intuitiv, ein Symbol aus einer Schriftart zu nehmen, aber unsere Schriftanzeigetechnologie bedeutet, dass diese Symbole klar und scharf auf jedem Bildschirm, bei jeder Auflösung und in jeder Größe angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2882e-126">It might not be intuitive to get an icon from a font, but our font display technology means these icons will look crisp and sharp on any display, at any resolution, and at any size.</span></span> <span data-ttu-id="2882e-127">:::column-end::: :::column::: ![Vordefiniertes Symbolbild](images/icons/predefined-icon.png) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-127">:::column-end::: :::column::: ![pre-defined icon image](images/icons/predefined-icon.png) :::column-end::: :::row-end:::</span></span>

### <a name="use-a-font"></a><span data-ttu-id="2882e-128">Verwenden einer Schriftart</span><span class="sxs-lookup"><span data-stu-id="2882e-128">Use a font.</span></span>
<span data-ttu-id="2882e-129">:::row::: :::column::: Sie müssen nicht die Segoe MDL2 Assets-Schrift verwenden, sondern können jede Schriftart nutzen, die der Benutzer auf seinem System installiert hat, z. B. Wingdings oder Webdings.</span><span class="sxs-lookup"><span data-stu-id="2882e-129">:::row::: :::column::: You don't have to use the Segoe MDL2 Assets font--you can use any font the user has installed on their system, such as Wingdings or Webdings.</span></span>
<span data-ttu-id="2882e-130">:::column-end::: :::column::: ![Wingdings-Bild](images/icons/wingdings.png) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-130">:::column-end::: :::column::: ![wingdings image](images/icons/wingdings.png) :::column-end::: :::row-end:::</span></span>

### <a name="use-a-scalable-vector-graphics-svg-file"></a><span data-ttu-id="2882e-131">Verwenden einer SVG-Datei (Scalable Vector Graphics)</span><span class="sxs-lookup"><span data-stu-id="2882e-131">Use a Scalable Vector Graphics (SVG) file.</span></span>
<span data-ttu-id="2882e-132">:::row::: :::column::: SVG-Ressourcen sind ideal für Symbole geeignet, weil sie in jeder Größe oder Auflösung immer gestochen scharf aussehen.</span><span class="sxs-lookup"><span data-stu-id="2882e-132">:::row::: :::column::: SVG resources are ideal for icons, because they always look sharp at any size or resolution.</span></span> <span data-ttu-id="2882e-133">Die meisten Zeichenanwendungen können in das SVG-Format exportieren.</span><span class="sxs-lookup"><span data-stu-id="2882e-133">Most drawing applications can export to SVG.</span></span> <span data-ttu-id="2882e-134">:::column-end::: :::column::: ![SVG-Bild](images/icons/icon-scale.gif) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-134">:::column-end::: :::column::: ![SVG image](images/icons/icon-scale.gif) :::column-end::: :::row-end:::</span></span>

### <a name="use-geometry-objects"></a><span data-ttu-id="2882e-135">Verwenden geometrischer Objekte</span><span class="sxs-lookup"><span data-stu-id="2882e-135">Use Geometry objects.</span></span>
<span data-ttu-id="2882e-136">::: Zeile:::::: Spalte::: Wie SVG-Dateien sind Geometrien eine vektorbasierte Ressource und werden deshalb immer gestochen scharf dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2882e-136">:::row::: :::column::: Like SVG files, geometries are a vector-based resource, so they always look sharp.</span></span> <span data-ttu-id="2882e-137">Das Erstellen einer Geometrie ist jedoch kompliziert, da Sie jeden Punkt und jede Kurve einzeln angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="2882e-137">However, creating a geometry is complicated because you have to individually specify each point and curve.</span></span> <span data-ttu-id="2882e-138">Es ist wirklich nur eine gute Option, wenn Sie das Symbol ändern müssen, während Ihre App ausgeführt wird (z.B. um es zu animieren).</span><span class="sxs-lookup"><span data-stu-id="2882e-138">It's really only a good choice if you need to modify the icon while your app is running (to animate it, for example).</span></span> <span data-ttu-id="2882e-139">Anweisungen finden Sie unter [Befehle zum Verschieben und Zeichnen von Geometrien](../../xaml-platform/move-draw-commands-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="2882e-139">For instructions, see [Move and draw commands for geometries](../../xaml-platform/move-draw-commands-syntax.md).</span></span> <span data-ttu-id="2882e-140">:::column-end::: :::column::: ![Bild eines Geometrieobjekts](images/icons/geometry-objects.png) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-140">:::column-end::: :::column::: ![Geometry objects image](images/icons/geometry-objects.png) :::column-end::: :::row-end:::</span></span>

### <a name="you-can-also-use-a-bitmap-image-such-as-png-gif-or-jpeg-although-we-dont-recommend-it"></a><span data-ttu-id="2882e-141">Sie können auf ein Bitmap-Bild wie PNG, GIF oder JPEG verwenden, auch wenn das nicht empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="2882e-141">You can also use a bitmap image, such as PNG, GIF, or JPEG, although we don't recommend it.</span></span>
<span data-ttu-id="2882e-142">:::row::: :::column::: Bitmap-Bilder werden in einer bestimmten Größe erstellt, sodass sie je nach gewünschter Symbolgröße und Auflösung des Bildschirms vergrößert oder verkleinert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2882e-142">:::row::: :::column::: Bitmap images are created at a specific size, so they have to be scaled up or down depending on how large you want the icon to be and the resolution of the screen.</span></span> <span data-ttu-id="2882e-143">Wenn das Bild verkleinert wird, kann es verschwommen angezeigt werden. Wenn es vergrößert wird, kann es eckig und verpixelt aussehen.</span><span class="sxs-lookup"><span data-stu-id="2882e-143">When the image is scaled down (shrunk), it can appear blurry; when it's scaled up, it can appear blocky and pixelated.</span></span> <span data-ttu-id="2882e-144">Wenn Sie ein Bitmap-Bild verwenden müssen, empfehlen wir die Verwendung einer PNG- oder GIF-Datei anstelle des JPEG-Formats.</span><span class="sxs-lookup"><span data-stu-id="2882e-144">If you have to use a bitmap image we recommend using a PNG or GIF over a JPEG.</span></span> <span data-ttu-id="2882e-145">:::column-end::: :::column::: ![Nicht sinnvoll](images/dont.svg) ![Bitmap-Bild](images/icons/bitmap-image.png) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-145">:::column-end::: :::column::: ![don't](images/dont.svg) ![Bitmap image](images/icons/bitmap-image.png) :::column-end::: :::row-end:::</span></span>

## <a name="make-the-icon-do-something"></a><span data-ttu-id="2882e-146">Festlegen einer Aktion für das Symbol</span><span class="sxs-lookup"><span data-stu-id="2882e-146">Make the icon do something</span></span>

<span data-ttu-id="2882e-147">Sobald Sie ein Symbol haben, besteht der nächste Schritt darin, es Aktion ausführen zu lassen, indem Sie ihm einen Befehl oder eine Navigationsaktion zuordnen.</span><span class="sxs-lookup"><span data-stu-id="2882e-147">Once you you have an icon, the next step is to make it do something by associating it with command or a navigation action.</span></span> <span data-ttu-id="2882e-148">Am einfachsten können Sie dies erreichen, indem Sie das Symbol zu einer Schaltfläche oder Befehlsleiste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2882e-148">The best way to to do this is to add the icon to a button or a command bar.</span></span> 

![Befehlsleistenbild](images/icons/app-bar-desktop.svg)

## <a name="create-an-icon-button"></a><span data-ttu-id="2882e-150">Erstellen einer Symbolschaltfläche</span><span class="sxs-lookup"><span data-stu-id="2882e-150">Create an icon button</span></span>

<span data-ttu-id="2882e-151">Sie können ein Symbol in eine Standardschaltfläche einfügen.</span><span class="sxs-lookup"><span data-stu-id="2882e-151">You can put an icon in a standard button.</span></span> <span data-ttu-id="2882e-152">Da Sie Schaltflächen an vielfältigeren Orten verwenden können, erhalten Sie damit etwas mehr Flexibilität, welcher Stelle Ihr Aktionssymbol angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2882e-152">Since you can use buttons in a wider variet of places, this gives you a little more flexibility for where your action icon appears.</span></span> 

<span data-ttu-id="2882e-153">Es gibt verschiedene Möglichkeiten, ein Symbol zu einer Schaltfläche hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="2882e-153">The are a few ways to add an icon to a button:</span></span>

<span data-ttu-id="2882e-154">:::row::: :::column span="2"::: <b>Schritt 1</b></span><span class="sxs-lookup"><span data-stu-id="2882e-154">:::row::: :::column span="2"::: <b>Step 1</b></span></span><br>
        <span data-ttu-id="2882e-155">Legen Sie die Schriftfamilie der Schaltfläche auf `Segoe MDL2 Assets` und seine Inhaltseigenschaft auf den Unicode-Wert des gewünschten Symbols fest: ::column-end::: :::column::: ![Erstellen einer Symbolschaltfläche – Schritt1](images/icons/create-icon-step-1.svg) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-155">Set the button's font family to `Segoe MDL2 Assets` and its content property to the unicode value of the glyph you want to use: :::column-end::: :::column::: ![Create an icon button step 1](images/icons/create-icon-step-1.svg) :::column-end::: :::row-end:::</span></span>

```xaml 
<Button FontFamily="Segoe MDL2 Assets" Content="&#xE102;" />
```

<span data-ttu-id="2882e-156">:::row::: :::column span="2"::: <b>Schritt 2</b></span><span class="sxs-lookup"><span data-stu-id="2882e-156">:::row::: :::column span="2"::: <b>Step 2</b></span></span><br>
        <span data-ttu-id="2882e-157">Sie können eins der Symbolelementobjekte verwenden: [BitmapIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.bitmapicon), [FontIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon), [PathIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pathicon) oder [SymbolIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbolicon).</span><span class="sxs-lookup"><span data-stu-id="2882e-157">You can use one of the icon element objects: [BitmapIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.bitmapicon), [FontIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon), [PathIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pathicon), or [SymbolIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbolicon).</span></span> <span data-ttu-id="2882e-158">Damit werden Ihnen mehr Symboltypen zur Auswahl gestellt, und Sie können bei Bedarf Symbole und andere Arten von Inhalten wie Text kombinieren: :::column-end::: :::column::: ![Erstellen einer Symbolschaltfläche – Schritt2](images/icons/icon-text-step-2.svg) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-158">This gives you more types of icons to choose from, and enables you to combine icons and other types of content, such as text, if you want: :::column-end::: :::column::: ![Create an icon button step 2](images/icons/icon-text-step-2.svg) :::column-end::: :::row-end:::</span></span>

```xaml 
<Button>
    <StackPanel>
        <SymbolIcon Symbol="Play" />
        <TextBlock>Play the movie</TextBlock>
    </StackPanel>
</Button>
```

## <a name="create-a-series-of-icons-in-a-command-bar"></a><span data-ttu-id="2882e-159">Erstellen einer Reihe von Symbolen in einer Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="2882e-159">Create a series of icons in a command bar</span></span>

<span data-ttu-id="2882e-160">:::row::: :::column span::: Wenn Sie eine Reihe von Befehlen haben, die zusammengehöhren, z.B. Ausschneiden/Kopieren/Einfügen oder eine Reihe von Zeichenbefehlen für ein Fotobearbeitungsprogramm, setzen Sie diese zusammen in eine [Befehlsleiste](../controls-and-patterns/app-bars.md).</span><span class="sxs-lookup"><span data-stu-id="2882e-160">:::row::: :::column span::: When you have a series of commands that go together, such as cut/copy/paste or a set of drawing commands for a photo-editing program, put them together in a [command bar](../controls-and-patterns/app-bars.md).</span></span> <span data-ttu-id="2882e-161">Eine Befehlsleiste enthält eine oder mehrere Schaltflächen oder Umschaltflächen der App-Leiste, die jeweils eine Aktion darstellen.</span><span class="sxs-lookup"><span data-stu-id="2882e-161">A command bar takes one or more app bar buttons or app bar toggle buttons, each of which represents an action.</span></span> <span data-ttu-id="2882e-162">Jede Schaltfläche verfügt über eine [Symbol](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.appbarbutton#Windows_UI_Xaml_Controls_AppBarButton_Icon)-Eigenschaft, mit der Sie steuern, welches Symbol angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2882e-162">Each button has an [Icon](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.appbarbutton#Windows_UI_Xaml_Controls_AppBarButton_Icon) property you use to control which icon it displays.</span></span> <span data-ttu-id="2882e-163">Es gibt eine Vielzahl von Möglichkeiten, um das Symbol anzugeben.</span><span class="sxs-lookup"><span data-stu-id="2882e-163">There are a variety of ways to specify the icon.</span></span> <span data-ttu-id="2882e-164">:::column-end::: :::column::: ![Beispiel einer Befehlsleiste mit Symbolen](images/icons/create-icon-command-bar.svg) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="2882e-164">:::column-end::: :::column::: ![Example of a command bar with icons](images/icons/create-icon-command-bar.svg) :::column-end::: :::row-end:::</span></span>

<span data-ttu-id="2882e-165">Die einfachste Möglichkeit ist die Verwendung der von uns bereitgestellten Liste vordefinierter Symbole: Geben Sie einfach den Namen des Symbols an, z.B. „Zurück“ oder „Beenden“, und das System zeichnet das entsprechende Symbol:</span><span class="sxs-lookup"><span data-stu-id="2882e-165">The easiest way is to use the list of predefined icons we provide—simply specify the icon name, such as "Back" or "Stop", and the system will draw it:</span></span> 

``` xaml
<CommandBar>
    <AppBarToggleButton Icon="Shuffle" Label="Shuffle" Click="AppBarButton_Click" />
    <AppBarToggleButton Icon="RepeatAll" Label="Repeat" Click="AppBarButton_Click"/>
    <AppBarSeparator/>
    <AppBarButton Icon="Back" Label="Back" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Stop" Label="Stop" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Play" Label="Play" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Forward" Label="Forward" Click="AppBarButton_Click"/>
</CommandBar>

```
<span data-ttu-id="2882e-166">Die vollständige Liste mit Symbolnamen finden Sie in der [Symbolenumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol).</span><span class="sxs-lookup"><span data-stu-id="2882e-166">For the complete list of icon names, see the [Symbol enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol).</span></span> 

<span data-ttu-id="2882e-167">Es gibt andere Möglichkeiten zum Bereitstellen von Symbolen für eine Schaltfläche in einer Befehlsleiste:</span><span class="sxs-lookup"><span data-stu-id="2882e-167">There are other ways to provide icons for a button in a command bar:</span></span>

+ <span data-ttu-id="2882e-168">[FontIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon): Das Symbol basiert auf einer Glyphe aus der angegebenen Schriftartfamilie.</span><span class="sxs-lookup"><span data-stu-id="2882e-168">[FontIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon) - the icon is based on a glyph from the specified font family.</span></span>
+ <span data-ttu-id="2882e-169">[BitmapIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.bitmapicon): Das Symbol basiert auf einer Bitmapbilddatei mit dem festgelegten **URI**.</span><span class="sxs-lookup"><span data-stu-id="2882e-169">[BitmapIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.bitmapicon) - the icon is based on a bitmap image file with the specified **Uri**.</span></span>
+ <span data-ttu-id="2882e-170">[PathIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pathicon): Das Symbol basiert auf [Path](/uwp/api/windows.ui.xaml.shapes.path)-Daten.</span><span class="sxs-lookup"><span data-stu-id="2882e-170">[PathIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pathicon) - the icon is based on [Path](/uwp/api/windows.ui.xaml.shapes.path) data.</span></span>

<span data-ttu-id="2882e-171">Weitere Informationen zu Befehlszeilen finden Sie im [Artikel zu Befehlsleisten](../controls-and-patterns/app-bars.md).</span><span class="sxs-lookup"><span data-stu-id="2882e-171">To learn more about command bars, see the [command bar article](../controls-and-patterns/app-bars.md).</span></span> 



## <a name="related-articles"></a><span data-ttu-id="2882e-172">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="2882e-172">Related articles</span></span>

* [<span data-ttu-id="2882e-173">Richtlinien für die Ressourcen für Kacheln und Symbole</span><span class="sxs-lookup"><span data-stu-id="2882e-173">Guidelines for tile and icon assets</span></span>](../shell/tiles-and-notifications/app-assets.md)
