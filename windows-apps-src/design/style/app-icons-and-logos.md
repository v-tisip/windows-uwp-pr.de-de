---
author: mijacobs
Description: How to create app icons/logos that represent your app in the Start menu, app tiles, the taskbar, the Microsoft Store, and more.
title: App-Symbole und logos
template: detail.hbs
ms.author: mijacobs
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
design-contact: Judysa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: e947b00c3a070a8d95a21e38c56bda07cd45d3c4
ms.sourcegitcommit: f5321b525034e2b3af202709e9b942ad5557e193
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2018
ms.locfileid: "4020414"
---
# <a name="app-icons-and-logos"></a><span data-ttu-id="32da8-103">App-Symbole und logos</span><span class="sxs-lookup"><span data-stu-id="32da8-103">App icons and logos</span></span> 

<span data-ttu-id="32da8-104">Jede app verfügt über ein Symbol/Logo, das es darstellt, und das Symbol an mehreren Standorten in der Windows-Shell angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="32da8-104">Every app has an icon/logo that represents it, and that icon appears in multiple locations in the Windows shell:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="32da8-105">\* Der Titelleiste Ihrer app-Fensters \* der app-Liste im Menü "Start" \* der Taskleiste und Task-Manager \* die app Kacheln \* Begrüßungsbildschirm der app \* im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="32da8-105">\* The title bar of your app window \* The app list in the start menu \* The taskbar and task manager \* Your app's tiles \* Your app's splash screen \* In the Microsoft Store</span></span> :::column-end:::
    :::column:::
        ![Starten von Windows10 und Kacheln](images/assetguidance01.jpg)
    :::column-end:::
:::row-end:::

<span data-ttu-id="32da8-107">In diesem Artikel werden die Grundlagen der Erstellung von app-Symbole, wie Sie Visual Studio zum Verwalten und wie sie manuell verwalten normalerweise erforderlich.</span><span class="sxs-lookup"><span data-stu-id="32da8-107">This article covers the basics of creating app icons, how to use Visual Studio to manage them, and how manage them manually, should you need to.</span></span>
 
<span data-ttu-id="32da8-108">(In diesem Artikel ist insbesondere für Symbole, die die app selbst darstellen, allgemeine Symbol-Anleitung finden Sie im Artikel [Symbole](icons.md) .)</span><span class="sxs-lookup"><span data-stu-id="32da8-108">(This article is specifically for icons that represent the app itself; for general icon guidance, see the [Icons](icons.md) article.)</span></span>

## <a name="icon-types-locations-and-scale-factors"></a><span data-ttu-id="32da8-109">Symbol Kontotypen, Standorte und Skalierungsfaktoren</span><span class="sxs-lookup"><span data-stu-id="32da8-109">Icon types, locations, and scale factors</span></span>

<span data-ttu-id="32da8-110">Standardmäßig speichert Visual Studio die Symbolressourcen in ein Unterverzeichnis Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="32da8-110">By default, Visual Studio stores your icon assets in an assets subdirectory.</span></span> <span data-ttu-id="32da8-111">Hier ist eine Liste der verschiedenen Typen von Symbolen, wo sie angezeigt werden, und wie sie benannt sind.</span><span class="sxs-lookup"><span data-stu-id="32da8-111">Here's a list of the different types of icons, where they appear, and what they're called.</span></span> 

| <span data-ttu-id="32da8-112">Symbol ein</span><span class="sxs-lookup"><span data-stu-id="32da8-112">Icon name</span></span> | <span data-ttu-id="32da8-113">Erscheint in</span><span class="sxs-lookup"><span data-stu-id="32da8-113">Appears in</span></span> | <span data-ttu-id="32da8-114">Asset-Dateiname</span><span class="sxs-lookup"><span data-stu-id="32da8-114">Asset file name</span></span> |
| ---      | ---        | --- |
| <span data-ttu-id="32da8-115">Kleine Kachel</span><span class="sxs-lookup"><span data-stu-id="32da8-115">Small tile</span></span> | <span data-ttu-id="32da8-116">Startmenü</span><span class="sxs-lookup"><span data-stu-id="32da8-116">Start menu</span></span> |  <span data-ttu-id="32da8-117">SmallTile.png</span><span class="sxs-lookup"><span data-stu-id="32da8-117">SmallTile.png</span></span>  |
| <span data-ttu-id="32da8-118">Mittelgroße Kachel</span><span class="sxs-lookup"><span data-stu-id="32da8-118">Medium tile</span></span> |<span data-ttu-id="32da8-119">Menü "Start", Microsoft Store Listing\ \*</span><span class="sxs-lookup"><span data-stu-id="32da8-119">Start menu,  Microsoft Store listing\*</span></span>  |  <span data-ttu-id="32da8-120">Square150x150Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="32da8-120">Square150x150Logo.png</span></span> |
| <span data-ttu-id="32da8-121">Breite Kachel</span><span class="sxs-lookup"><span data-stu-id="32da8-121">Wide tile</span></span>  | <span data-ttu-id="32da8-122">Startmenü</span><span class="sxs-lookup"><span data-stu-id="32da8-122">Start menu</span></span>   | <span data-ttu-id="32da8-123">Wide310x150Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="32da8-123">Wide310x150Logo.png</span></span> |
| <span data-ttu-id="32da8-124">Große Kachel</span><span class="sxs-lookup"><span data-stu-id="32da8-124">Large tile</span></span>   | <span data-ttu-id="32da8-125">Menü "Start", Microsoft Store Listing\ \*</span><span class="sxs-lookup"><span data-stu-id="32da8-125">Start menu,  Microsoft Store listing\*</span></span> |  <span data-ttu-id="32da8-126">LargeTile.png</span><span class="sxs-lookup"><span data-stu-id="32da8-126">LargeTile.png</span></span>  |
| <span data-ttu-id="32da8-127">App-Symbol</span><span class="sxs-lookup"><span data-stu-id="32da8-127">App icon</span></span> | <span data-ttu-id="32da8-128">App-Liste im Startmenü, Taskleiste, Task-manager</span><span class="sxs-lookup"><span data-stu-id="32da8-128">App list in start menu, task bar, task manager</span></span> | <span data-ttu-id="32da8-129">Square44x44Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="32da8-129">Square44x44Logo.png</span></span> |
| <span data-ttu-id="32da8-130">Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="32da8-130">Splash screen</span></span> | <span data-ttu-id="32da8-131">Begrüßungsbildschirm der app</span><span class="sxs-lookup"><span data-stu-id="32da8-131">The app's splash screen</span></span> | <span data-ttu-id="32da8-132">SplashScreen.png</span><span class="sxs-lookup"><span data-stu-id="32da8-132">SplashScreen.png</span></span>  |
| <span data-ttu-id="32da8-133">Signallogo</span><span class="sxs-lookup"><span data-stu-id="32da8-133">Badge logo</span></span> | <span data-ttu-id="32da8-134">Die app Kacheln</span><span class="sxs-lookup"><span data-stu-id="32da8-134">Your app's tiles</span></span> | <span data-ttu-id="32da8-135">BadgeLogo.png</span><span class="sxs-lookup"><span data-stu-id="32da8-135">BadgeLogo.png</span></span>  |
| <span data-ttu-id="32da8-136">Paket-Logo/Shop-logo</span><span class="sxs-lookup"><span data-stu-id="32da8-136">Package logo/Store logo</span></span> | <span data-ttu-id="32da8-137">App-Installer, Dev Center die Option "Eine app melden" im Store, die Option "Einen Prüfbericht schreiben" im Store</span><span class="sxs-lookup"><span data-stu-id="32da8-137">App installer, Dev Center, the "Report an app" option in the Store, the "Write a review" option in the Store</span></span> | <span data-ttu-id="32da8-138">StoreLogo.png</span><span class="sxs-lookup"><span data-stu-id="32da8-138">StoreLogo.png</span></span>  |

<span data-ttu-id="32da8-139">\ \* Verwendet, es sei denn, Sie für die [Anzeige nur Bilder im Store hochgeladen](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store)auswählen.</span><span class="sxs-lookup"><span data-stu-id="32da8-139">\* Used unless you choose to [display only uploaded images in the Store](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span></span> 

<span data-ttu-id="32da8-140">Um sicherzustellen, dass diese Symbole für jeden Bildschirm scharf aussehen, können Sie mehrere Versionen des gleichen Schildsymbols für unterschiedliche Skalierungsfaktoren erstellen.</span><span class="sxs-lookup"><span data-stu-id="32da8-140">To ensure these icons look sharp on every screen, you can create multiple versions of the same icon for different display scale factors.</span></span> 

<span data-ttu-id="32da8-141">Der Skalierungsfaktor bestimmt die Größe von UI-Elementen, z. B. Text.</span><span class="sxs-lookup"><span data-stu-id="32da8-141">The  scale factor determines the size of UI elements, such as text.</span></span> <span data-ttu-id="32da8-142">Skalierung von Faktoren reichen von 100 % und 400 %.</span><span class="sxs-lookup"><span data-stu-id="32da8-142">Scale factors range from 100% to 400%.</span></span> <span data-ttu-id="32da8-143">Mit höheren Werten zu größeren UI-Elemente, sodass schneller auf hohe DPI-Displays finden Sie unter erstellen.</span><span class="sxs-lookup"><span data-stu-id="32da8-143">Larger values create larger UI elements, making them easier to see on high-DPI displays.</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="32da8-144">Windows stellt automatisch den Skalierungsfaktor für jede Anzeige aus, basierend auf dem DPI-Wert (Punkte pro Zoll) und dem betrachtungsabstand des Geräts.</span><span class="sxs-lookup"><span data-stu-id="32da8-144">Windows automatically sets the scale factor for each display based on its DPI (dots-per-inch) and the viewing distance of the device.</span></span> 

        (Users can override the default value by going to the **Settings &gt; Display &gt; Scale and layout** page.)
    :::column-end:::
    :::column:::
        ![](images/icons/display-settings-screen.png)
    :::column-end:::
:::row-end:::  


<span data-ttu-id="32da8-145">Da Ressourcen für app-Symbole, Bitmaps sind und Bitmaps nicht gut skalieren, es wird empfohlen, einer Version alle Ressourcen Symbol für jedes Skalierungsfaktor: 100 %, 125 %, 150 %, 200 % und 400 %.</span><span class="sxs-lookup"><span data-stu-id="32da8-145">Because app icon assets are bitmaps and bitmaps don't scale well, we recommend providing a version each icon asset for each scale factor: 100%, 125%, 150%, 200%, and 400%.</span></span> <span data-ttu-id="32da8-146">Das ist eine Menge von Symbolen!</span><span class="sxs-lookup"><span data-stu-id="32da8-146">That's a lot of icons!</span></span> <span data-ttu-id="32da8-147">Fortunatly, Visual Studio bietet ein Tool, das zum Erstellen und aktualisieren diese Symbole vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="32da8-147">Fortunatly, Visual Studio provides a tool that makes it easy to generate and update these icons.</span></span> 

## <a name="microsoft-store-listing-image"></a><span data-ttu-id="32da8-148">Microsoft Store-Eintrag image</span><span class="sxs-lookup"><span data-stu-id="32da8-148">Microsoft Store listing image</span></span>

<span data-ttu-id="32da8-149">"Festlegen Bilder für meine app-Eintrag im Microsoft Store?"</span><span class="sxs-lookup"><span data-stu-id="32da8-149">"How do I specify images for my app's listing in the Microsoft Store?"</span></span>

<span data-ttu-id="32da8-150">Standardmäßig verwenden wir einige der Bilder aus Ihren im Store, wie in der Tabelle am Anfang dieser Seite (sowie andere [Bilder, die Sie während der Übermittlung bereitstellen](https://docs.microsoft.com/en-us/windows/uwp/publish/app-screenshots-and-images)) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="32da8-150">By default, we use some of the images from your packages in the Store, as described in the table at the top of this page (along with other [images that you provide during the submission process](https://docs.microsoft.com/en-us/windows/uwp/publish/app-screenshots-and-images)).</span></span> <span data-ttu-id="32da8-151">Allerdings haben Sie die Möglichkeit zu verhindern, dass den Store die Logos in den Paketen Ihrer app zu verwenden, wenn Ihr Angebot für Kunden unter Windows 10 (einschließlich Xbox) angezeigt, und stattdessen der Store muss nur Bilder verwenden, die Sie hochladen.</span><span class="sxs-lookup"><span data-stu-id="32da8-151">However, you have the option to prevent the Store from using the logo images in your app's packages when displaying your listing to customers on Windows 10 (including Xbox), and instead have the Store use only images that you upload.</span></span> <span data-ttu-id="32da8-152">Dies bietet Ihnen mehr Kontrolle über die Darstellung Ihrer app in verschiedenen anzeigen im Store.</span><span class="sxs-lookup"><span data-stu-id="32da8-152">This gives you more control over your app’s appearance in various displays throughout the Store.</span></span> <span data-ttu-id="32da8-153">(Beachten Sie, dass wenn Ihr Produkt für frühere Betriebssystemversionen unterstützt, die Kunden weiterhin Bilder aus der verpackt werden, finden Sie unter möglicherweise auch dann, wenn Sie diese Option verwenden.) Dies ist im **Store-Logos** Abschnitt des **Store-Eintrag** Schritts im Übermittlungsprozess möglich.</span><span class="sxs-lookup"><span data-stu-id="32da8-153">(Note that if your product supports earlier OS versions, those customers may still see images from your packages, even if you use this option.) You can do this in the **Store logos** section of the **Store listing** step of the submission process.</span></span>

![Festlegen von Store-Logos während der app-Übermittlungsprozesses](images/app-icons/storelogodisplay.png)

<span data-ttu-id="32da8-155">Wenn Sie dieses Kontrollkästchen aktivieren, wird ein neuer Abschnitt namens **Store Bilder anzuzeigen** .</span><span class="sxs-lookup"><span data-stu-id="32da8-155">When you check this box, a new section called **Store display images** appears.</span></span> <span data-ttu-id="32da8-156">Hier können Sie hochladen, 3 Bildgrößen, die der Store "anstelle von" logobildern aus den Paketen Ihrer app verwenden: 300 x 300, 150 x 150 und 71 x 71 Pixel.</span><span class="sxs-lookup"><span data-stu-id="32da8-156">Here, you can upload 3 image sizes that the Store will use in place of logo images from your app’s packages: 300 x 300, 150 x 150, and 71 x 71 pixels.</span></span> <span data-ttu-id="32da8-157">Nur die Größe 300 x 300 ist erforderlich, auch wenn es wird empfohlen, alle 3 Größen.</span><span class="sxs-lookup"><span data-stu-id="32da8-157">Only the 300 x 300 size is required, although we recommend providing all 3 sizes.</span></span>

<span data-ttu-id="32da8-158">Weitere Informationen finden Sie in der [Anzeige im Store Logos nur hochgeladen](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span><span class="sxs-lookup"><span data-stu-id="32da8-158">For more info, see [Display only uploaded logo images in the Store](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span></span>

<!-- ### Fallback images for the Store

The simplest way to control the Store listing image is to specify it during the app submission process. If you don't provide these images during the app submission process, the Store will use a tile image:

1. Large tile
2. Medium tile

If these images aren't provided, the Store will search all matching images of the same image type with a square aspect ratio, preferable with a height greated than the scaled requested height (scaled height is the machine's resolution scale factor * display height). If none of the images meet this criteria, the Store will ignore the scale factor and select an image based on height.  -->

<!-- You can provide screenshots, logos, and other art assets (such as trailers and promotional images to include in your app's Microsoft Store listing. Some of these are required, and some are optional (although some of the optional images are important to include for the best Store display).

The Store may also use your app's tile and other images that you include in your app's package. 

For more information, see [App screenshots, images, and trailers in the Microsoft Store](/windows/uwp/publish/app-screenshots-and-images). -->


## <a name="managing-app-icons-with-the-visual-studio-manifest-designer"></a><span data-ttu-id="32da8-159">Verwalten von app-Symbole mit Visual Studio-Manifest-Designer</span><span class="sxs-lookup"><span data-stu-id="32da8-159">Managing app icons with the Visual Studio Manifest Designer</span></span>

<span data-ttu-id="32da8-160">Visual Studio bietet sehr nützlich für die Verwaltung von Ihrer app-Symbole im **Manifest-Designer**aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="32da8-160">Visual Studio provides a very useful tool for managing your app icons called the **Manifest Designer**.</span></span> 

> <span data-ttu-id="32da8-161">Wenn Sie Visual Studio 2017 noch nicht, es gibt mehrere Versionen, z. B. eine kostenlose Version, (Visual Studio 2017 Community Edition), und andere Versionen bieten kostenlose Testversionen.</span><span class="sxs-lookup"><span data-stu-id="32da8-161">If you don't already have Visual Studio 2017, there are several versions available, including a free version, (Visual Studio 2017 Community Edition), and the other versions offer free trials.</span></span> <span data-ttu-id="32da8-162">Sie können sie hier herunterladen:[https://developer.microsoft.com/windows/downloads](https://developer.microsoft.com/windows/downloads)</span><span class="sxs-lookup"><span data-stu-id="32da8-162">You can download them here: [https://developer.microsoft.com/windows/downloads](https://developer.microsoft.com/windows/downloads)</span></span>


<span data-ttu-id="32da8-163">So starten Sie den Manifest-Designer</span><span class="sxs-lookup"><span data-stu-id="32da8-163">To launch the Manifest Designer:</span></span>
<!-- 1. Use Visual Studio to open a UWP project.
2. In the **Solution Explorer**, double-click the package.appmanifest file. 

    ![The Visual Studio 2017 Solution Explorer](images/icons/vs-solution-explorer.png)

    Visual Studio displays the manifest designer.

    ![The Visual Studio 2017 manifest designer](images/icons/vs-manfiest-designer.png)
3. Click the **Visual Assets** tab.

    ![The Visual Assets tab](images/icons/vs-manfiest-designer-visual-assets.png) -->


:::row:::
    :::column:::
        <span data-ttu-id="32da8-164">1. verwenden Sie Visual Studio, um ein UWP-Projekt öffnen.</span><span class="sxs-lookup"><span data-stu-id="32da8-164">1. Use Visual Studio to open a UWP project.</span></span>
    :::column-end:::
    :::column:::
        
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        <span data-ttu-id="32da8-165">2. im **Projektmappen-Explorer**Doppelklicken Sie auf die Datei Package.appmxanifest.</span><span class="sxs-lookup"><span data-stu-id="32da8-165">2. In the **Solution Explorer**, double-click the Package.appmxanifest file.</span></span>
    :::column-end:::
    :::column:::
        ![Manifest-Designer von Visual Studio 2017](images/icons/vs-solution-explorer.png)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
            <span data-ttu-id="32da8-167">Visual Studio zeigt die Manifest-Designer.</span><span class="sxs-lookup"><span data-stu-id="32da8-167">Visual Studio displays the Manifest Designer.</span></span>
    :::column-end:::
    :::column:::
            ![Die Registerkarte "visuelle Anlagen"](images/icons/vs-manfiest-designer.png)
    :::column-end:::
:::row-end:::    
:::row:::
    :::column:::
        <span data-ttu-id="32da8-169">3. Klicken Sie auf der Registerkarte " **Visuelle Anlagen** ".</span><span class="sxs-lookup"><span data-stu-id="32da8-169">3. Click the **Visual Assets** tab.</span></span> :::column-end:::
    :::column:::
        ![Die Registerkarte "visuelle Anlagen"](images/icons/vs-manfiest-designer-visual-assets.png)
    :::column-end:::
:::row-end:::        

## <a name="generating-all-assets-at-once"></a><span data-ttu-id="32da8-171">Erstellen alle Ressourcen auf einmal</span><span class="sxs-lookup"><span data-stu-id="32da8-171">Generating all assets at once</span></span>

<span data-ttu-id="32da8-172">Das erste Menüelement in der Registerkarte " **Visuelle Anlagen** ", **Alle visuellen Ressourcen**, ist genau das, was der Name schon sagt: jede visuelle Ressource, die Ihre app mit dem Drücken der Taste a muss generiert.</span><span class="sxs-lookup"><span data-stu-id="32da8-172">The first menu item in the **Visual Assets** tab, **All Visual Assets**, does exactly what its name suggests: generates every visual asset your app needs with the press of a button.</span></span>

![Generieren von alle visuellen Ressourcen in Visual Studio](images/app-icons/all-visual-assets.png)

<span data-ttu-id="32da8-174">Sie müssen lediglich ist Geben Sie ein einzelnes Bild und Visual Studio generiert die kleine Kachel, mittelgroße Kachel, große Kachel, Breite Kachel, große Kachel, app-Symbol, Begrüßungsbildschirm, und Flight-Logo-Ressourcen für jedes Skalierungsfaktor.</span><span class="sxs-lookup"><span data-stu-id="32da8-174">All you need to do is supply a single image, and Visaul Studio will generate the small tile, medium tile, large tile, wide tile, large tile, app icon, splash screen, and package logo assets for every scale factor.</span></span>

<span data-ttu-id="32da8-175">Um alle Ressourcen auf einmal zu generieren:</span><span class="sxs-lookup"><span data-stu-id="32da8-175">To generate all assets at once:</span></span>
1. <span data-ttu-id="32da8-176">Klicken Sie auf die \*\*\*\* neben dem Feld **Quelle** , und wählen Sie das Bild, das Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="32da8-176">Click the **...** next to the **Source** field and select the image you want to use.</span></span> <span data-ttu-id="32da8-177">Wenn Sie ein Bitmap-Bild verwenden, stellen Sie sicher, dass sie mindestens 400 von 400 Pixel ist, damit Sie scharfe Ergebnisse erhalten.</span><span class="sxs-lookup"><span data-stu-id="32da8-177">If you're using a bitmap image, make sure it's at least 400 by 400 pixels so that you get sharp results.</span></span> <span data-ttu-id="32da8-178">Vektorbasierte Bilder funktionieren am besten; Visual Studio können Sie AI (Adobe Illustrator) und PDF-Dateien verwenden.</span><span class="sxs-lookup"><span data-stu-id="32da8-178">Vector-based images work best; Visual Studio lets you use AI (Adobe Illustrator) and PDF files.</span></span> 
2. <span data-ttu-id="32da8-179">(Optional). Konfigurieren Sie im Abschnitt **Anzeigeeinstellungen** folgende Optionen:</span><span class="sxs-lookup"><span data-stu-id="32da8-179">(Optional.) In the **Display Settings** section, configure these options:</span></span>

    <span data-ttu-id="32da8-180">a.</span><span class="sxs-lookup"><span data-stu-id="32da8-180">a.</span></span>  <span data-ttu-id="32da8-181">**Kurzname**: Geben Sie einen kurzen Namen für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="32da8-181">**Short name**:  Specify a short name for your app.</span></span>

    <span data-ttu-id="32da8-182">b.</span><span class="sxs-lookup"><span data-stu-id="32da8-182">b.</span></span>  <span data-ttu-id="32da8-183">**Namen anzeigen**: angeben, ob der Kurzname auf Mittel, breit, oder große Kacheln angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="32da8-183">**Show name**: Indicate whether you want to display the short name on medium, wide, or large tiles.</span></span> 

    <span data-ttu-id="32da8-184">c.</span><span class="sxs-lookup"><span data-stu-id="32da8-184">c.</span></span> <span data-ttu-id="32da8-185">**Hintergrund-Kachel**: Geben Sie den Hexadezimalwert oder einen Farbnamen für die Hintergrundfarbe der Kachel.</span><span class="sxs-lookup"><span data-stu-id="32da8-185">**Tile background**: Specify the hex value or a color name for the tile background color.</span></span> <span data-ttu-id="32da8-186">Beispiel: `#464646`.</span><span class="sxs-lookup"><span data-stu-id="32da8-186">For example, `#464646`.</span></span> <span data-ttu-id="32da8-187">Der Standardwert lautet `transparent`.</span><span class="sxs-lookup"><span data-stu-id="32da8-187">The default value is `transparent`.</span></span>

    <span data-ttu-id="32da8-188">d.</span><span class="sxs-lookup"><span data-stu-id="32da8-188">d.</span></span> <span data-ttu-id="32da8-189">**Hintergrund des: Splash**: Geben Sie die hex-Wert oder Farbe für den Hintergrund des: Splash.</span><span class="sxs-lookup"><span data-stu-id="32da8-189">**Spash screen background**: Specify the hex value or color name for the spash screen background.</span></span> 

3. <span data-ttu-id="32da8-190">Klicken Sie auf **generieren**.</span><span class="sxs-lookup"><span data-stu-id="32da8-190">Click **Generate**.</span></span> 

<span data-ttu-id="32da8-191">Visual Studio generiert die Dateien und Projekt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="32da8-191">Visual Studio generates your image files and adds them to project.</span></span> <span data-ttu-id="32da8-192">Wenn Sie Ihre Ressourcen ändern möchten, wiederholen Sie einfach den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="32da8-192">If you want to change your assets, simply repeat the process.</span></span> 

<span data-ttu-id="32da8-193">Skalierte Symbolressourcen führen Sie diese Datei Namenskonvention:</span><span class="sxs-lookup"><span data-stu-id="32da8-193">Scaled icon assets follow this file naming convention:</span></span>

<span data-ttu-id="32da8-194">*Dateiname*- Scale -*Skalierungsfaktor*PNG</span><span class="sxs-lookup"><span data-stu-id="32da8-194">*filename*-scale-*scale factor*.png</span></span>

<span data-ttu-id="32da8-195">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="32da8-195">For example,</span></span>

<span data-ttu-id="32da8-196">Square150x150Logo-Skalierung-100.png, Square150x150Logo-Skalierung-200.png, Square150x150Logo-Skalierung-400.png</span><span class="sxs-lookup"><span data-stu-id="32da8-196">Square150x150Logo-scale-100.png, Square150x150Logo-scale-200.png, Square150x150Logo-scale-400.png</span></span>

<span data-ttu-id="32da8-197">Beachten Sie, dass ein signallogo standardmäßig von Visual Studio generiert wird.</span><span class="sxs-lookup"><span data-stu-id="32da8-197">Notice that Visual Studio doesn't generate a badge logo by default.</span></span> <span data-ttu-id="32da8-198">Ist, dass Ihre signallogo ist eindeutig und wahrscheinlich mit Ihrer app-Symbole sollten nicht übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="32da8-198">That's because your badge logo is unique and probably shouldn't match your other app icons.</span></span> <span data-ttu-id="32da8-199">Weitere Informationen finden Sie in der [signalbenachrichtigungen für UWP-apps Artikel](/windows/uwp/design/shell/tiles-and-notifications/badges).</span><span class="sxs-lookup"><span data-stu-id="32da8-199">For more info, see the  [Badge notifications for UWP apps article](/windows/uwp/design/shell/tiles-and-notifications/badges).</span></span> 


## <a name="more-about-app-icon-assets"></a><span data-ttu-id="32da8-200">Weitere Informationen zu Ressourcen für app-Symbol</span><span class="sxs-lookup"><span data-stu-id="32da8-200">More about app icon assets</span></span>
<span data-ttu-id="32da8-201">Visual Studio generiert alle app-Symbol-Assets, die für das Projekt erforderlich, aber wenn Sie diese anpassen möchten, hilft es um zu verstehen, wie sie sich von anderen app-Ressourcen sind.</span><span class="sxs-lookup"><span data-stu-id="32da8-201">Visual Studio will generate all the app icon assets required by your project, but if you'd like to customize them, it helps to understand how they're different from other app assets.</span></span> 

<span data-ttu-id="32da8-202">Das app-Symbol-Element wird in vielen Stellen: der Windows-Taskleiste, der Aufgabenansicht, ALT + TAB und der unteren rechten Ecke von startkacheln.</span><span class="sxs-lookup"><span data-stu-id="32da8-202">The app icon asset appears in a lot of places: the Windows taskbar, the task view, ALT+TAB, and the lower-right corner of Start tiles.</span></span> <span data-ttu-id="32da8-203">Da die app-Symbol-Ressource an vielen Orten angezeigt wird, verfügt über einige zusätzliche größenanpassung und Optionen, die die andere Ressourcen verfügen nicht über plating: "Target-Size" Bestand und "unbeschichtete" Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="32da8-203">Because the app icon asset appears in so many places, it has some additional sizing and plating options the other assets don't have: "target-size" assets and "unplated" assets.</span></span> 

### <a name="target-size-app-icon-assets"></a><span data-ttu-id="32da8-204">Zielgröße-app-Symbolressourcen</span><span class="sxs-lookup"><span data-stu-id="32da8-204">Target-size app icon assets</span></span>
<span data-ttu-id="32da8-205">Zusätzlich zu den standard-Skalierungsfaktor Größen ("Square44x44Logo.scale-400.png") empfehlen wir auch "Target-Size" Ressourcen erstellen.</span><span class="sxs-lookup"><span data-stu-id="32da8-205">In addition to the standard scale factor sizes ("Square44x44Logo.scale-400.png"), we also recommend creating "target-size" assets.</span></span> <span data-ttu-id="32da8-206">Wir bezeichnen diese Ressourcen Zielgröße-, da sie bestimmte Größen, z. B. bestimmte Skalierungsfaktoren, z. B. 400, anstatt 16 Pixel als Ziel.</span><span class="sxs-lookup"><span data-stu-id="32da8-206">We call these assets target-size because they target specific sizes, such as 16 pixels, rather than specific scale factors, such as 400.</span></span> <span data-ttu-id="32da8-207">Zielgröße-Ressourcen gelten für Oberflächen, die Skalierung Plateau System nicht:</span><span class="sxs-lookup"><span data-stu-id="32da8-207">Target-size assets are for surfaces that don't use the scaling plateau system:</span></span>

* <span data-ttu-id="32da8-208">Starten der Sprungliste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="32da8-208">Start jump list (desktop)</span></span>
* <span data-ttu-id="32da8-209">Starten der unteren Ecke der Kachel (Desktop)</span><span class="sxs-lookup"><span data-stu-id="32da8-209">Start lower corner of tile (desktop)</span></span>
* <span data-ttu-id="32da8-210">Tastenkombinationen (Desktop)</span><span class="sxs-lookup"><span data-stu-id="32da8-210">Shortcuts (desktop)</span></span>
* <span data-ttu-id="32da8-211">Systemsteuerung (Desktop)</span><span class="sxs-lookup"><span data-stu-id="32da8-211">Control Panel (desktop)</span></span>

<span data-ttu-id="32da8-212">Hier ist die Liste der Zielgröße-Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="32da8-212">Here's the list of target-size assets:</span></span>


| <span data-ttu-id="32da8-213">Ressourcengröße</span><span class="sxs-lookup"><span data-stu-id="32da8-213">Asset size</span></span> | <span data-ttu-id="32da8-214">Dateinamenbeispiel</span><span class="sxs-lookup"><span data-stu-id="32da8-214">File name example</span></span>                  |
|------------|------------------------------------|
| <span data-ttu-id="32da8-215">16 x 16\*</span><span class="sxs-lookup"><span data-stu-id="32da8-215">16x16\*</span></span>    | <span data-ttu-id="32da8-216">Square44x44Logo.targetsize-16.png</span><span class="sxs-lookup"><span data-stu-id="32da8-216">Square44x44Logo.targetsize-16.png</span></span>  |
| <span data-ttu-id="32da8-217">24 x 24\*</span><span class="sxs-lookup"><span data-stu-id="32da8-217">24x24\*</span></span>    | <span data-ttu-id="32da8-218">Square44x44Logo.targetsize-24.png</span><span class="sxs-lookup"><span data-stu-id="32da8-218">Square44x44Logo.targetsize-24.png</span></span>  |
| <span data-ttu-id="32da8-219">32 x 32\*</span><span class="sxs-lookup"><span data-stu-id="32da8-219">32x32\*</span></span>    | <span data-ttu-id="32da8-220">Square44x44Logo.targetsize-32.png</span><span class="sxs-lookup"><span data-stu-id="32da8-220">Square44x44Logo.targetsize-32.png</span></span>  |
| <span data-ttu-id="32da8-221">48 x 48\*</span><span class="sxs-lookup"><span data-stu-id="32da8-221">48x48\*</span></span>    | <span data-ttu-id="32da8-222">Square44x44Logo.targetsize-48.png</span><span class="sxs-lookup"><span data-stu-id="32da8-222">Square44x44Logo.targetsize-48.png</span></span>  |
| <span data-ttu-id="32da8-223">256 x 256\*</span><span class="sxs-lookup"><span data-stu-id="32da8-223">256x256\*</span></span>  | <span data-ttu-id="32da8-224">Square44x44Logo.targetsize-256.png</span><span class="sxs-lookup"><span data-stu-id="32da8-224">Square44x44Logo.targetsize-256.png</span></span> |
| <span data-ttu-id="32da8-225">20 x 20</span><span class="sxs-lookup"><span data-stu-id="32da8-225">20x20</span></span>      | <span data-ttu-id="32da8-226">Square44x44Logo.targetsize-20.png</span><span class="sxs-lookup"><span data-stu-id="32da8-226">Square44x44Logo.targetsize-20.png</span></span>  |
| <span data-ttu-id="32da8-227">30x30</span><span class="sxs-lookup"><span data-stu-id="32da8-227">30x30</span></span>      | <span data-ttu-id="32da8-228">Square44x44Logo.targetsize-30.png</span><span class="sxs-lookup"><span data-stu-id="32da8-228">Square44x44Logo.targetsize-30.png</span></span>  |
| <span data-ttu-id="32da8-229">36 x 36</span><span class="sxs-lookup"><span data-stu-id="32da8-229">36x36</span></span>      | <span data-ttu-id="32da8-230">Square44x44Logo.targetsize-36.png</span><span class="sxs-lookup"><span data-stu-id="32da8-230">Square44x44Logo.targetsize-36.png</span></span>  |
| <span data-ttu-id="32da8-231">40 x 40</span><span class="sxs-lookup"><span data-stu-id="32da8-231">40x40</span></span>      | <span data-ttu-id="32da8-232">Square44x44Logo.targetsize-40.png</span><span class="sxs-lookup"><span data-stu-id="32da8-232">Square44x44Logo.targetsize-40.png</span></span>  |
| <span data-ttu-id="32da8-233">60 x 60</span><span class="sxs-lookup"><span data-stu-id="32da8-233">60x60</span></span>      | <span data-ttu-id="32da8-234">Square44x44Logo.targetsize-60.png</span><span class="sxs-lookup"><span data-stu-id="32da8-234">Square44x44Logo.targetsize-60.png</span></span>  |
| <span data-ttu-id="32da8-235">64 x 64</span><span class="sxs-lookup"><span data-stu-id="32da8-235">64x64</span></span>      | <span data-ttu-id="32da8-236">Square44x44Logo.targetsize-64.png</span><span class="sxs-lookup"><span data-stu-id="32da8-236">Square44x44Logo.targetsize-64.png</span></span>  |
| <span data-ttu-id="32da8-237">72 x 72</span><span class="sxs-lookup"><span data-stu-id="32da8-237">72x72</span></span>      | <span data-ttu-id="32da8-238">Square44x44Logo.targetsize-72.png</span><span class="sxs-lookup"><span data-stu-id="32da8-238">Square44x44Logo.targetsize-72.png</span></span>  |
| <span data-ttu-id="32da8-239">80 x 80</span><span class="sxs-lookup"><span data-stu-id="32da8-239">80x80</span></span>      | <span data-ttu-id="32da8-240">Square44x44Logo.targetsize-80.png</span><span class="sxs-lookup"><span data-stu-id="32da8-240">Square44x44Logo.targetsize-80.png</span></span>  |
| <span data-ttu-id="32da8-241">96 x 96</span><span class="sxs-lookup"><span data-stu-id="32da8-241">96x96</span></span>      | <span data-ttu-id="32da8-242">Square44x44Logo.targetsize-96.png</span><span class="sxs-lookup"><span data-stu-id="32da8-242">Square44x44Logo.targetsize-96.png</span></span>  |

<span data-ttu-id="32da8-243">\ \* Mindestens, es wird empfohlen, diese Größen.</span><span class="sxs-lookup"><span data-stu-id="32da8-243">\* At a minimum, we recommend providing these sizes.</span></span> 

<span data-ttu-id="32da8-244">Sie müssen für diese Ressourcen keine Abstände hinzufügen, diese werden bei Bedarf von Windows hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="32da8-244">You don't have to add padding to these assets; Windows adds padding if needed.</span></span> <span data-ttu-id="32da8-245">Bei diesen Ressourcen sollte eine minimale Fläche von 16Pixeln vorgesehen werden.</span><span class="sxs-lookup"><span data-stu-id="32da8-245">These assets should account for a minimum footprint of 16 pixels.</span></span> 

<span data-ttu-id="32da8-246">Unten sehen Sie ein Beispiel dafür, wie diese Ressourcen als Symbole in der Windows-Taskleiste angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="32da8-246">Here's an example of these assets as they appear in icons on the Windows taskbar:</span></span>

![Ressourcen in Windows-Taskleiste](images/assetguidance21.png)

### <a name="unplated-assets"></a><span data-ttu-id="32da8-248">Unbeschichtete Ressourcen</span><span class="sxs-lookup"><span data-stu-id="32da8-248">Unplated assets</span></span>
<span data-ttu-id="32da8-249">Standardmäßig verwendet Windows eine zielbasierte Ressource neben einer farbigen Rückwand standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="32da8-249">By default, Windows uses a target-based asset on top of a colored backplate by default.</span></span> <span data-ttu-id="32da8-250">Wenn Sie möchten, können Sie eine Ziel zielbasierte Ressource bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="32da8-250">If you want, you can provide a target-based unplated asset.</span></span> <span data-ttu-id="32da8-251">"Unbeschichtete" bedeutet, dass die Ressource auf einen transparenten Hintergrund angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="32da8-251">"Unplated" means the asset will be displayed on a transparent background.</span></span> <span data-ttu-id="32da8-252">Denken Sie daran, die diese Ressourcen über eine Vielzahl von Hintergrundfarben angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="32da8-252">Keep in mind that these assets will appear over a variety of background colors.</span></span> 

![Ressourcen mit und ohne Anpassung](images/assetguidance22.png)

<span data-ttu-id="32da8-254">Hier sind die Oberflächen, die Ressourcen für zielbasierte app-Symbole verwenden:</span><span class="sxs-lookup"><span data-stu-id="32da8-254">Here are the surfaces that use unplated app icon assets:</span></span>
* <span data-ttu-id="32da8-255">Taskleiste und Miniaturansicht der Taskleiste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="32da8-255">Taskbar and taskbar thumbnail (desktop)</span></span>
* <span data-ttu-id="32da8-256">Taskleisten-Sprungliste</span><span class="sxs-lookup"><span data-stu-id="32da8-256">Taskbar jumplist</span></span>
* <span data-ttu-id="32da8-257">Aufgabenansicht</span><span class="sxs-lookup"><span data-stu-id="32da8-257">Task view</span></span>
* <span data-ttu-id="32da8-258">ALT + TAB</span><span class="sxs-lookup"><span data-stu-id="32da8-258">ALT+TAB</span></span>


### <a name="target-and-unplated-sizing"></a><span data-ttu-id="32da8-259">Ziel und zielbasierte anpassen</span><span class="sxs-lookup"><span data-stu-id="32da8-259">Target and unplated sizing</span></span>

<span data-ttu-id="32da8-260">Hier sind die Größe Empfehlungen für zielbasierte Ressourcen mit einer Skalierung von 100 %:</span><span class="sxs-lookup"><span data-stu-id="32da8-260">Here are the size recommendations for target-based assets, at 100% scale:</span></span>

![Zielbasierte Ressourcengröße bei einer Skalierung von 100%](images/assetguidance23.png)


## <a name="more-about-splash-screen-assets"></a><span data-ttu-id="32da8-262">Weitere Informationen zu Ressourcen für den Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="32da8-262">More about splash screen assets</span></span>
<span data-ttu-id="32da8-263">Weitere Informationen über Begrüßungsbildschirme finden Sie im [UWP Begrüßungsbildschirm Bildschirme Artikel](/windows/uwp/launch-resume/splash-screens).</span><span class="sxs-lookup"><span data-stu-id="32da8-263">For more info about splash screens, see the [UWP splash screens article](/windows/uwp/launch-resume/splash-screens).</span></span>

## <a name="more-about-badge-logo-assets"></a><span data-ttu-id="32da8-264">Weitere Informationen zur Badge-Logo-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="32da8-264">More about badge logo assets</span></span>

<span data-ttu-id="32da8-265">Wenn Sie den Asset-Generator verwenden, um alle Ressourcen zu generieren, Sie müssen, es gibt ein Grund, warum es Signal Logos standardmäßig generiert nicht: sie sind unterscheidet sich von anderen app-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="32da8-265">When you use the asset generator to generate all the assets you need, there's a reason why it doesn't generate badge logos by default: they're very different from other app assets.</span></span> <span data-ttu-id="32da8-266">Das signallogo ist ein Status-Bild, das in Benachrichtigungen und auf die app-Kacheln angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="32da8-266">The badge logo is a status image that appears in notifications and on the app's tiles.</span></span> 

<span data-ttu-id="32da8-267">Weitere Informationen finden Sie in der [signalbenachrichtigungen für UWP-apps Artikel](/windows/uwp/design/shell/tiles-and-notifications/badges).</span><span class="sxs-lookup"><span data-stu-id="32da8-267">For more information, see the [Badge notifications for UWP apps article](/windows/uwp/design/shell/tiles-and-notifications/badges).</span></span>


## <a name="customizing-asset-padding"></a><span data-ttu-id="32da8-268">Anpassen der Ressource "Padding"</span><span class="sxs-lookup"><span data-stu-id="32da8-268">Customizing asset padding</span></span>

<span data-ttu-id="32da8-269">Standardmäßig gilt Visual Studio Asset-Generator empfohlene Abstand für alle Bilder.</span><span class="sxs-lookup"><span data-stu-id="32da8-269">By default, Visual Studio asset generator applies recommended padding to whatever image.</span></span> <span data-ttu-id="32da8-270">Wenn Ihre Bilder "Padding" bereits enthalten, oder Sie die randlosen-Bilder, die am Ende der Kachel erweitern möchten, können Sie dieses Feature deaktivieren deaktivieren Sie das Kontrollkästchen **anwenden, die "Padding" empfohlen** .</span><span class="sxs-lookup"><span data-stu-id="32da8-270">If your images already contain padding or you want full bleed images that extend to the end of the tile, you can turn this feature off by unchecking the **Apply recommended padding** check box.</span></span> 

### <a name="tile-padding-recommendations"></a><span data-ttu-id="32da8-271">Kachel "Padding" Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="32da8-271">Tile padding recommendations</span></span>
<span data-ttu-id="32da8-272">Wenn Sie Ihre eigene Padding bereitstellen möchten, folgen Sie unsere Empfehlungen für die Kacheln.</span><span class="sxs-lookup"><span data-stu-id="32da8-272">If you want to provide your own padding, here are our recommendations for tiles.</span></span> 

<span data-ttu-id="32da8-273">Es gibt 4 kachelgrößen: (71 x 71) klein, Mittel (150 x 150), Wide (310 x 150) und große (310 x 310).</span><span class="sxs-lookup"><span data-stu-id="32da8-273">There are 4 tile sizes: small (71 x 71), medium (150 x 150), wide (310 x 150), and large (310 x 310).</span></span> 

<span data-ttu-id="32da8-274">Jede Kachelressource hat die gleiche Größe wie die Kachel, auf der sie sich befindet.</span><span class="sxs-lookup"><span data-stu-id="32da8-274">Each tile asset is the same size as the tile on which it is placed.</span></span>

![Randlose Kachel](images/app-icons/tile-assets1.png)

<span data-ttu-id="32da8-276">Wenn Sie nicht, dass das Symbol an den Rand der Kachel erweitern möchten, können Sie transparente Pixel in Ihrer Ressource verwenden, um Abstand zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="32da8-276">If you don't want your icon to extend to the edge of the tile, you can use transparent pixels in your asset to create padding.</span></span> 

![Kachel und Rückwand](images/assetguidance05.png)

<span data-ttu-id="32da8-278">Beschränken Sie bei kleinen Kacheln die Breite und Höhe auf 66% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="32da8-278">For small tiles, limit the icon width and height to 66% of the tile size:</span></span>

![Verhältnisse bei kleinen Kachelgrößen](images/assetguidance09.png)

<span data-ttu-id="32da8-280">Beschränken Sie bei mittelgroßen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="32da8-280">For medium tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="32da8-281">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="32da8-281">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei mittelgroßen Kacheln](images/assetguidance10.png)

<span data-ttu-id="32da8-283">Beschränken Sie bei breiten Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="32da8-283">For wide tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="32da8-284">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="32da8-284">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei breiten Kacheln](images/assetguidance11.png)

<span data-ttu-id="32da8-286">Beschränken Sie bei großen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="32da8-286">For large tiles, limit the icon width to 66% and height to 50% of tile size:</span></span>

![Verhältnisse bei großen Kacheln](images/assetguidance12.png)

<span data-ttu-id="32da8-288">Einige Symbole sind so konzipiert, dass sie horizontal oder vertikal ausgerichtet sind, andere Symbole hingegen weisen komplexere Formen auf, wodurch verhindert wird, dass sie direkt in die Zielabmessungen passen.</span><span class="sxs-lookup"><span data-stu-id="32da8-288">Some icons are designed to be horizontally or vertically oriented, while others have more complex shapes that prevent them from fitting squarely within the target dimensions.</span></span> <span data-ttu-id="32da8-289">Symbole, die zentriert erscheinen, können auf eine Seite geneigt sein.</span><span class="sxs-lookup"><span data-stu-id="32da8-289">Icons that appear to be centered can be weighted to one side.</span></span> <span data-ttu-id="32da8-290">In diesem Fall können Teile eines Symbols aus der empfohlenen Fläche heraushängen, vorausgesetzt, das Symbol belegt dasselbe visuelle Gewicht wie ein genau passendes Symbol:</span><span class="sxs-lookup"><span data-stu-id="32da8-290">In this case, parts of an icon may hang outside the recommended footprint, provided it occupies the same visual weight as a squarely fitted icon:</span></span>

![Drei zentrierte Symbole](images/assetguidance13.png)

<span data-ttu-id="32da8-292">Berücksichtigen Sie bei randlosen Ressourcen Elemente, die innerhalb der Ränder und Kanten der Kacheln interagieren.</span><span class="sxs-lookup"><span data-stu-id="32da8-292">With full-bleed assets, take into account elements that interact within the margins and edges of the tiles.</span></span> <span data-ttu-id="32da8-293">Behalten Sie Ränder von mindestens 16 % der Höhe oder Breite der Kachel bei.</span><span class="sxs-lookup"><span data-stu-id="32da8-293">Maintain margins of at least 16% of the height or width of the tile.</span></span> <span data-ttu-id="32da8-294">Dieser Prozentsatz stellt die doppelte Breite der Ränder bei den kleinsten Kachelgrößen dar:</span><span class="sxs-lookup"><span data-stu-id="32da8-294">This percentage represents double the width of the margins at the smallest tile sizes:</span></span>

![Randlose Kachel mit Rändern](images/assetguidance14.png)

<span data-ttu-id="32da8-296">In diesem Beispiel sind die Ränder zu eng:</span><span class="sxs-lookup"><span data-stu-id="32da8-296">In this example, margins are too tight:</span></span>

![Randlose Kachel mit zu engen Rändern](images/assetguidance15.png)









