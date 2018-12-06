---
Description: How to create app icons/logos that represent your app in the Start menu, app tiles, the taskbar, the Microsoft Store, and more.
title: App-Symbole und Logos
template: detail.hbs
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP
design-contact: Judysa
doc-status: Published
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 7083152efb4cf871f8abebf6d2970d2da4ba06e9
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8753166"
---
# <a name="app-icons-and-logos"></a><span data-ttu-id="1052c-103">App-Symbole und Logos</span><span class="sxs-lookup"><span data-stu-id="1052c-103">App icons and logos</span></span> 

<span data-ttu-id="1052c-104">Jede app verfügt über ein Symbol/Logo, das es darstellt, und das Symbol wird an mehreren Standorten in der Windows-Shell angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1052c-104">Every app has an icon/logo that represents it, and that icon appears in multiple locations in the Windows shell:</span></span> 

:::row:::
    :::column:::
        * <span data-ttu-id="1052c-105">Der Titelleiste Ihrer app-Fenster</span><span class="sxs-lookup"><span data-stu-id="1052c-105">The title bar of your app window</span></span>
        * <span data-ttu-id="1052c-106">Der app-Liste im Menü "Start"</span><span class="sxs-lookup"><span data-stu-id="1052c-106">The app list in the start menu</span></span>
        * <span data-ttu-id="1052c-107">Die Taskleiste und Task-manager</span><span class="sxs-lookup"><span data-stu-id="1052c-107">The taskbar and task manager</span></span>
        * <span data-ttu-id="1052c-108">Die app Kacheln</span><span class="sxs-lookup"><span data-stu-id="1052c-108">Your app's tiles</span></span>
        * <span data-ttu-id="1052c-109">Begrüßungsbildschirm der app</span><span class="sxs-lookup"><span data-stu-id="1052c-109">Your app's splash screen</span></span>
        * <span data-ttu-id="1052c-110">Im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="1052c-110">In the Microsoft Store</span></span>
    :::column-end:::
    :::column:::
        ![windows 10 start and tiles](images/assetguidance01.jpg)
    :::column-end:::
:::row-end:::

<span data-ttu-id="1052c-111">In diesem Artikel werden die Grundlagen der Erstellung von app-Symbole, wie Sie Visual Studio zum Verwalten und wie sie manuell verwalten müssen Sie.</span><span class="sxs-lookup"><span data-stu-id="1052c-111">This article covers the basics of creating app icons, how to use Visual Studio to manage them, and how manage them manually, should you need to.</span></span>
 
<span data-ttu-id="1052c-112">(In diesem Artikel ist insbesondere für Symbole, die die app selbst darstellen, allgemeine Symbol-Anleitung finden Sie im Artikel [Symbole](icons.md) .)</span><span class="sxs-lookup"><span data-stu-id="1052c-112">(This article is specifically for icons that represent the app itself; for general icon guidance, see the [Icons](icons.md) article.)</span></span>

## <a name="icon-types-locations-and-scale-factors"></a><span data-ttu-id="1052c-113">Symbol Kontotypen, Standorte und Skalierungsfaktoren</span><span class="sxs-lookup"><span data-stu-id="1052c-113">Icon types, locations, and scale factors</span></span>

<span data-ttu-id="1052c-114">Standardmäßig speichert Visual Studio die Symbolressourcen in ein Unterverzeichnis Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="1052c-114">By default, Visual Studio stores your icon assets in an assets subdirectory.</span></span> <span data-ttu-id="1052c-115">Hier ist eine Übersicht über die verschiedenen Arten von Symbolen, wo sie angezeigt werden, und wie sie benannt sind.</span><span class="sxs-lookup"><span data-stu-id="1052c-115">Here's a list of the different types of icons, where they appear, and what they're called.</span></span> 

| <span data-ttu-id="1052c-116">Symbol ein</span><span class="sxs-lookup"><span data-stu-id="1052c-116">Icon name</span></span> | <span data-ttu-id="1052c-117">Erscheint in</span><span class="sxs-lookup"><span data-stu-id="1052c-117">Appears in</span></span> | <span data-ttu-id="1052c-118">Name der Anlage-Datei</span><span class="sxs-lookup"><span data-stu-id="1052c-118">Asset file name</span></span> |
| ---      | ---        | --- |
| <span data-ttu-id="1052c-119">Kleine Kachel</span><span class="sxs-lookup"><span data-stu-id="1052c-119">Small tile</span></span> | <span data-ttu-id="1052c-120">Startmenü</span><span class="sxs-lookup"><span data-stu-id="1052c-120">Start menu</span></span> |  <span data-ttu-id="1052c-121">SmallTile.png</span><span class="sxs-lookup"><span data-stu-id="1052c-121">SmallTile.png</span></span>  |
| <span data-ttu-id="1052c-122">Mittelgroße Kachel</span><span class="sxs-lookup"><span data-stu-id="1052c-122">Medium tile</span></span> |<span data-ttu-id="1052c-123">Menü "Start", Microsoft Store Listing\ \*</span><span class="sxs-lookup"><span data-stu-id="1052c-123">Start menu,  Microsoft Store listing\*</span></span>  |  <span data-ttu-id="1052c-124">Square150x150Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="1052c-124">Square150x150Logo.png</span></span> |
| <span data-ttu-id="1052c-125">Breite Kachel</span><span class="sxs-lookup"><span data-stu-id="1052c-125">Wide tile</span></span>  | <span data-ttu-id="1052c-126">Startmenü</span><span class="sxs-lookup"><span data-stu-id="1052c-126">Start menu</span></span>   | <span data-ttu-id="1052c-127">Wide310x150Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="1052c-127">Wide310x150Logo.png</span></span> |
| <span data-ttu-id="1052c-128">Große Kachel</span><span class="sxs-lookup"><span data-stu-id="1052c-128">Large tile</span></span>   | <span data-ttu-id="1052c-129">Menü "Start", Microsoft Store Listing\ \*</span><span class="sxs-lookup"><span data-stu-id="1052c-129">Start menu,  Microsoft Store listing\*</span></span> |  <span data-ttu-id="1052c-130">LargeTile.png</span><span class="sxs-lookup"><span data-stu-id="1052c-130">LargeTile.png</span></span>  |
| <span data-ttu-id="1052c-131">App-Symbol</span><span class="sxs-lookup"><span data-stu-id="1052c-131">App icon</span></span> | <span data-ttu-id="1052c-132">App-Liste im Startmenü, Taskleiste, Task-manager</span><span class="sxs-lookup"><span data-stu-id="1052c-132">App list in start menu, task bar, task manager</span></span> | <span data-ttu-id="1052c-133">Square44x44Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="1052c-133">Square44x44Logo.png</span></span> |
| <span data-ttu-id="1052c-134">Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="1052c-134">Splash screen</span></span> | <span data-ttu-id="1052c-135">Begrüßungsbildschirm der app</span><span class="sxs-lookup"><span data-stu-id="1052c-135">The app's splash screen</span></span> | <span data-ttu-id="1052c-136">SplashScreen.png</span><span class="sxs-lookup"><span data-stu-id="1052c-136">SplashScreen.png</span></span>  |
| <span data-ttu-id="1052c-137">Signallogo</span><span class="sxs-lookup"><span data-stu-id="1052c-137">Badge logo</span></span> | <span data-ttu-id="1052c-138">Die app Kacheln</span><span class="sxs-lookup"><span data-stu-id="1052c-138">Your app's tiles</span></span> | <span data-ttu-id="1052c-139">BadgeLogo.png</span><span class="sxs-lookup"><span data-stu-id="1052c-139">BadgeLogo.png</span></span>  |
| <span data-ttu-id="1052c-140">Paket-Logo-Speicher-logo</span><span class="sxs-lookup"><span data-stu-id="1052c-140">Package logo/Store logo</span></span> | <span data-ttu-id="1052c-141">App-Installer, Partner Center die Option "Eine app melden" im Store, die Option "Einen Prüfbericht schreiben" im Store</span><span class="sxs-lookup"><span data-stu-id="1052c-141">App installer, Partner Center, the "Report an app" option in the Store, the "Write a review" option in the Store</span></span> | <span data-ttu-id="1052c-142">StoreLogo.png</span><span class="sxs-lookup"><span data-stu-id="1052c-142">StoreLogo.png</span></span>  |

<span data-ttu-id="1052c-143">\ \* Verwendet, es sei denn, Sie für die [Anzeige nur Bilder im Store hochgeladen](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store)auswählen.</span><span class="sxs-lookup"><span data-stu-id="1052c-143">\* Used unless you choose to [display only uploaded images in the Store](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span></span> 

<span data-ttu-id="1052c-144">Um sicherzustellen, dass diese Symbole für jeden Bildschirm scharf aussehen, können Sie mehrere Versionen des gleichen Schildsymbols für unterschiedliche Skalierungsfaktoren erstellen.</span><span class="sxs-lookup"><span data-stu-id="1052c-144">To ensure these icons look sharp on every screen, you can create multiple versions of the same icon for different display scale factors.</span></span> 

<span data-ttu-id="1052c-145">Der Skalierungsfaktor bestimmt die Größe des UI-Elemente, z. B. Text.</span><span class="sxs-lookup"><span data-stu-id="1052c-145">The  scale factor determines the size of UI elements, such as text.</span></span> <span data-ttu-id="1052c-146">Skalierung von Faktoren reichen von 100 % und 400 %.</span><span class="sxs-lookup"><span data-stu-id="1052c-146">Scale factors range from 100% to 400%.</span></span> <span data-ttu-id="1052c-147">Mit höheren Werten zu größeren UI-Elemente, sodass schneller auf hohe DPI-Displays finden Sie unter erstellen.</span><span class="sxs-lookup"><span data-stu-id="1052c-147">Larger values create larger UI elements, making them easier to see on high-DPI displays.</span></span> 

:::row:::
    :::column:::
        Windows automatically sets the scale factor for each display based on its DPI (dots-per-inch) and the viewing distance of the device. 

        (Users can override the default value by going to the **Settings &gt; Display &gt; Scale and layout** page.)
    :::column-end:::
    :::column:::
        ![](images/icons/display-settings-screen.png)
    :::column-end:::
:::row-end:::  


<span data-ttu-id="1052c-148">Da app-Symbolressourcen Bitmaps und Bitmaps nicht gut skalieren, es wird empfohlen, einer Version jedes Symbol-Ressource für jedes Skalierungsfaktor: 100 %, 125 %, 150 %, 200 % und 400 %.</span><span class="sxs-lookup"><span data-stu-id="1052c-148">Because app icon assets are bitmaps and bitmaps don't scale well, we recommend providing a version each icon asset for each scale factor: 100%, 125%, 150%, 200%, and 400%.</span></span> <span data-ttu-id="1052c-149">Das ist eine Menge von Symbolen!</span><span class="sxs-lookup"><span data-stu-id="1052c-149">That's a lot of icons!</span></span> <span data-ttu-id="1052c-150">Fortunatly, Visual Studio bietet ein Tool, das zum Erstellen und aktualisieren diese Symbole erleichtert.</span><span class="sxs-lookup"><span data-stu-id="1052c-150">Fortunatly, Visual Studio provides a tool that makes it easy to generate and update these icons.</span></span> 

## <a name="microsoft-store-listing-image"></a><span data-ttu-id="1052c-151">Microsoft Store-Eintrag Bild</span><span class="sxs-lookup"><span data-stu-id="1052c-151">Microsoft Store listing image</span></span>

<span data-ttu-id="1052c-152">"Festlegen Bilder für meine app-Eintrag im Microsoft Store?"</span><span class="sxs-lookup"><span data-stu-id="1052c-152">"How do I specify images for my app's listing in the Microsoft Store?"</span></span>

<span data-ttu-id="1052c-153">Standardmäßig verwenden wir einige der Bilder von Ihren Paketen im Store wie in der Tabelle am oberen Rand auf dieser Seite (sowie andere [Bilder, die Sie während der Übermittlung bereitstellen](https://docs.microsoft.com/en-us/windows/uwp/publish/app-screenshots-and-images)) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1052c-153">By default, we use some of the images from your packages in the Store, as described in the table at the top of this page (along with other [images that you provide during the submission process](https://docs.microsoft.com/en-us/windows/uwp/publish/app-screenshots-and-images)).</span></span> <span data-ttu-id="1052c-154">Allerdings können Sie verhindern, dass den Store die Logos in den Paketen Ihrer app zu verwenden, wenn Ihr Angebot für Kunden unter Windows 10 (einschließlich Xbox) angezeigt, und stattdessen der Store muss nur Bilder verwenden, die Sie hochladen.</span><span class="sxs-lookup"><span data-stu-id="1052c-154">However, you have the option to prevent the Store from using the logo images in your app's packages when displaying your listing to customers on Windows 10 (including Xbox), and instead have the Store use only images that you upload.</span></span> <span data-ttu-id="1052c-155">Dies bietet Ihnen mehr Kontrolle über die Darstellung Ihrer app in verschiedenen anzeigen im Store.</span><span class="sxs-lookup"><span data-stu-id="1052c-155">This gives you more control over your app’s appearance in various displays throughout the Store.</span></span> <span data-ttu-id="1052c-156">(Beachten Sie, dass wenn Ihr Produkt für frühere Betriebssystemversionen unterstützt, die Kunden weiterhin Bilder aus der verpackt werden, finden Sie unter möglicherweise auch dann, wenn Sie diese Option verwenden.) Dies ist im **Store-Logos** Teil der **Store-Eintrag** Schritt im Übermittlungsprozess möglich.</span><span class="sxs-lookup"><span data-stu-id="1052c-156">(Note that if your product supports earlier OS versions, those customers may still see images from your packages, even if you use this option.) You can do this in the **Store logos** section of the **Store listing** step of the submission process.</span></span>

![Angeben der Store-Logos während der app-Übermittlung](images/app-icons/storelogodisplay.png)

<span data-ttu-id="1052c-158">Wenn Sie dieses Kontrollkästchen aktivieren, wird ein neuer Abschnitt namens **Store Bilder anzuzeigen** .</span><span class="sxs-lookup"><span data-stu-id="1052c-158">When you check this box, a new section called **Store display images** appears.</span></span> <span data-ttu-id="1052c-159">Sie können hier hochladen, 3 Bildgrößen, die der Store anstelle von logobildern aus den Paketen Ihrer app verwenden: 300 x 300, 150 x 150 und 71 x 71 Pixel.</span><span class="sxs-lookup"><span data-stu-id="1052c-159">Here, you can upload 3 image sizes that the Store will use in place of logo images from your app’s packages: 300 x 300, 150 x 150, and 71 x 71 pixels.</span></span> <span data-ttu-id="1052c-160">Nur die Größe 300 x 300 ist erforderlich, obwohl es wird empfohlen, alle 3 Größen.</span><span class="sxs-lookup"><span data-stu-id="1052c-160">Only the 300 x 300 size is required, although we recommend providing all 3 sizes.</span></span>

<span data-ttu-id="1052c-161">Weitere Informationen finden Sie in der [Anzeige nur Logo Bilder im Store hochgeladen](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span><span class="sxs-lookup"><span data-stu-id="1052c-161">For more info, see [Display only uploaded logo images in the Store](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span></span>

<!-- ### Fallback images for the Store

The simplest way to control the Store listing image is to specify it during the app submission process. If you don't provide these images during the app submission process, the Store will use a tile image:

1. Large tile
2. Medium tile

If these images aren't provided, the Store will search all matching images of the same image type with a square aspect ratio, preferable with a height greated than the scaled requested height (scaled height is the machine's resolution scale factor * display height). If none of the images meet this criteria, the Store will ignore the scale factor and select an image based on height.  -->

<!-- You can provide screenshots, logos, and other art assets (such as trailers and promotional images to include in your app's Microsoft Store listing. Some of these are required, and some are optional (although some of the optional images are important to include for the best Store display).

The Store may also use your app's tile and other images that you include in your app's package. 

For more information, see [App screenshots, images, and trailers in the Microsoft Store](/windows/uwp/publish/app-screenshots-and-images). -->


## <a name="managing-app-icons-with-the-visual-studio-manifest-designer"></a><span data-ttu-id="1052c-162">Verwalten von app-Symbole mit der Manifest-Designer von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1052c-162">Managing app icons with the Visual Studio Manifest Designer</span></span>

<span data-ttu-id="1052c-163">Visual Studio bietet sehr nützlich für die Verwaltung von Ihrer app-Symbole im **Manifest-Designer**aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="1052c-163">Visual Studio provides a very useful tool for managing your app icons called the **Manifest Designer**.</span></span> 

> <span data-ttu-id="1052c-164">Wenn Sie Visual Studio 2017 noch nicht, es gibt mehrere Versionen, z. B. eine kostenlose Version (Visual Studio 2017 Community Edition), und die anderen Versionen bieten kostenlose Testversionen.</span><span class="sxs-lookup"><span data-stu-id="1052c-164">If you don't already have Visual Studio 2017, there are several versions available, including a free version, (Visual Studio 2017 Community Edition), and the other versions offer free trials.</span></span> <span data-ttu-id="1052c-165">Sie können sie hier herunterladen:[https://developer.microsoft.com/windows/downloads](https://developer.microsoft.com/windows/downloads)</span><span class="sxs-lookup"><span data-stu-id="1052c-165">You can download them here: [https://developer.microsoft.com/windows/downloads](https://developer.microsoft.com/windows/downloads)</span></span>


<span data-ttu-id="1052c-166">So starten Sie den Manifest-Designer</span><span class="sxs-lookup"><span data-stu-id="1052c-166">To launch the Manifest Designer:</span></span>
<!-- 1. Use Visual Studio to open a UWP project.
2. In the **Solution Explorer**, double-click the package.appmanifest file. 

    ![The Visual Studio 2017 Solution Explorer](images/icons/vs-solution-explorer.png)

    Visual Studio displays the manifest designer.

    ![The Visual Studio 2017 manifest designer](images/icons/vs-manfiest-designer.png)
3. Click the **Visual Assets** tab.

    ![The Visual Assets tab](images/icons/vs-manfiest-designer-visual-assets.png) -->


:::row:::
    :::column:::
        1. <span data-ttu-id="1052c-167">Verwenden Sie Visual Studio, um ein UWP-Projekt öffnen.</span><span class="sxs-lookup"><span data-stu-id="1052c-167">Use Visual Studio to open a UWP project.</span></span>
    :::column-end:::
    :::column:::
        
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        2. <span data-ttu-id="1052c-168">Doppelklicken Sie im **Projektmappen-Explorer**auf die Package.appmxanifest.</span><span class="sxs-lookup"><span data-stu-id="1052c-168">In the **Solution Explorer**, double-click the Package.appmxanifest file.</span></span>
    :::column-end:::
    :::column:::
        ![The Visual Studio 2017 Manifest Designer](images/icons/vs-solution-explorer.png)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
            Visual Studio displays the Manifest Designer.
    :::column-end:::
    :::column:::
            ![The Visual Assets tab](images/icons/vs-manfiest-designer.png)
    :::column-end:::
:::row-end:::    
:::row:::
    :::column:::
        3. <span data-ttu-id="1052c-169">Klicken Sie auf der Registerkarte " **Visuelle Anlagen** ".</span><span class="sxs-lookup"><span data-stu-id="1052c-169">Click the **Visual Assets** tab.</span></span>
    :::column-end:::
    :::column:::
        ![The Visual Assets tab](images/icons/vs-manfiest-designer-visual-assets.png)
    :::column-end:::
:::row-end:::        

## <a name="generating-all-assets-at-once"></a><span data-ttu-id="1052c-170">Erstellen gleichzeitig alle Ressourcen</span><span class="sxs-lookup"><span data-stu-id="1052c-170">Generating all assets at once</span></span>

<span data-ttu-id="1052c-171">Das erste Menüelement im auf der Registerkarte für **Visuelle Ressourcen** , **Alle visuellen Ressourcen**, ist genau das, was der Name schon sagt: jede visuelle Ressource, die Ihre app mit dem Drücken der Taste a muss generiert.</span><span class="sxs-lookup"><span data-stu-id="1052c-171">The first menu item in the **Visual Assets** tab, **All Visual Assets**, does exactly what its name suggests: generates every visual asset your app needs with the press of a button.</span></span>

![Generieren von alle visuellen Ressourcen in Visual Studio](images/app-icons/all-visual-assets.png)

<span data-ttu-id="1052c-173">Alles, was Sie tun müssen ist ein einzelnes Bild bereitstellen, und Visual Studio generiert die kleine Kachel, mittelgroßen Kachel, große Kachel, Breite Kachel, große Kachel, app-Symbol, Begrüßungsbildschirm, und Flight-Logo-Ressourcen für jedes Skalierungsfaktor.</span><span class="sxs-lookup"><span data-stu-id="1052c-173">All you need to do is supply a single image, and Visual Studio will generate the small tile, medium tile, large tile, wide tile, large tile, app icon, splash screen, and package logo assets for every scale factor.</span></span>

<span data-ttu-id="1052c-174">Um alle Ressourcen auf einmal zu generieren:</span><span class="sxs-lookup"><span data-stu-id="1052c-174">To generate all assets at once:</span></span>
1. <span data-ttu-id="1052c-175">Klicken Sie auf die \*\*\*\* neben der **Source** -Feld, und wählen Sie das Bild, das Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="1052c-175">Click the **...** next to the **Source** field and select the image you want to use.</span></span> <span data-ttu-id="1052c-176">Wenn Sie ein Bitmap-Bild verwenden, stellen Sie sicher, dass sie mindestens 400 um 400 Pixel ist, damit Sie scharfe Ergebnisse erhalten.</span><span class="sxs-lookup"><span data-stu-id="1052c-176">If you're using a bitmap image, make sure it's at least 400 by 400 pixels so that you get sharp results.</span></span> <span data-ttu-id="1052c-177">Vektorbasierte Bilder funktionieren am besten; Visual Studio können Sie AI (Adobe Illustrator) und PDF-Dateien verwenden.</span><span class="sxs-lookup"><span data-stu-id="1052c-177">Vector-based images work best; Visual Studio lets you use AI (Adobe Illustrator) and PDF files.</span></span> 
2. <span data-ttu-id="1052c-178">(Optional). Konfigurieren Sie im Abschnitt **Anzeigeeinstellungen** folgende Optionen:</span><span class="sxs-lookup"><span data-stu-id="1052c-178">(Optional.) In the **Display Settings** section, configure these options:</span></span>

    <span data-ttu-id="1052c-179">a.</span><span class="sxs-lookup"><span data-stu-id="1052c-179">a.</span></span>  <span data-ttu-id="1052c-180">**Kurzname**: Geben Sie einen kurzen Namen für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="1052c-180">**Short name**:  Specify a short name for your app.</span></span>

    <span data-ttu-id="1052c-181">b.</span><span class="sxs-lookup"><span data-stu-id="1052c-181">b.</span></span>  <span data-ttu-id="1052c-182">**Namen anzeigen**: angeben, ob der Kurzname für Mittel, breit, oder große Kacheln angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1052c-182">**Show name**: Indicate whether you want to display the short name on medium, wide, or large tiles.</span></span> 

    <span data-ttu-id="1052c-183">c.</span><span class="sxs-lookup"><span data-stu-id="1052c-183">c.</span></span> <span data-ttu-id="1052c-184">**Hintergrund-Kachel**: Geben Sie den Hexadezimalwert oder einen Farbnamen für die Hintergrundfarbe der Kachel.</span><span class="sxs-lookup"><span data-stu-id="1052c-184">**Tile background**: Specify the hex value or a color name for the tile background color.</span></span> <span data-ttu-id="1052c-185">Beispiel: `#464646`.</span><span class="sxs-lookup"><span data-stu-id="1052c-185">For example, `#464646`.</span></span> <span data-ttu-id="1052c-186">Der Standardwert lautet `transparent`.</span><span class="sxs-lookup"><span data-stu-id="1052c-186">The default value is `transparent`.</span></span>

    <span data-ttu-id="1052c-187">d.</span><span class="sxs-lookup"><span data-stu-id="1052c-187">d.</span></span> <span data-ttu-id="1052c-188">**Hintergrund: Splash**: Geben Sie die hex-Wert oder Farbe für den Hintergrund des: Splash.</span><span class="sxs-lookup"><span data-stu-id="1052c-188">**Spash screen background**: Specify the hex value or color name for the spash screen background.</span></span> 

3. <span data-ttu-id="1052c-189">Klicken Sie auf **generieren**.</span><span class="sxs-lookup"><span data-stu-id="1052c-189">Click **Generate**.</span></span> 

<span data-ttu-id="1052c-190">Visual Studio generiert die Dateien und Projekt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1052c-190">Visual Studio generates your image files and adds them to project.</span></span> <span data-ttu-id="1052c-191">Wenn Sie Ihre Ressourcen ändern möchten, wiederholen Sie einfach den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="1052c-191">If you want to change your assets, simply repeat the process.</span></span> 

<span data-ttu-id="1052c-192">Skalierte Symbolressourcen führen Sie diese Datei Namenskonvention:</span><span class="sxs-lookup"><span data-stu-id="1052c-192">Scaled icon assets follow this file naming convention:</span></span>

<span data-ttu-id="1052c-193">*Filename*- Scale -*Skalierungsfaktor*PNG</span><span class="sxs-lookup"><span data-stu-id="1052c-193">*filename*-scale-*scale factor*.png</span></span>

<span data-ttu-id="1052c-194">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1052c-194">For example,</span></span>

<span data-ttu-id="1052c-195">Square150x150Logo-Skalierung-100.png, Square150x150Logo-Skalierung-200.png, Square150x150Logo-Skalierung-400.png</span><span class="sxs-lookup"><span data-stu-id="1052c-195">Square150x150Logo-scale-100.png, Square150x150Logo-scale-200.png, Square150x150Logo-scale-400.png</span></span>

<span data-ttu-id="1052c-196">Beachten Sie, dass Visual Studio eine signallogo standardmäßig generiert.</span><span class="sxs-lookup"><span data-stu-id="1052c-196">Notice that Visual Studio doesn't generate a badge logo by default.</span></span> <span data-ttu-id="1052c-197">Ist, dass Ihre signallogo ist eindeutig und wahrscheinlich sollte nicht Ihre app-Symbole übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="1052c-197">That's because your badge logo is unique and probably shouldn't match your other app icons.</span></span> <span data-ttu-id="1052c-198">Weitere Informationen finden Sie unter der [signalbenachrichtigungen für UWP-apps Artikel](/windows/uwp/design/shell/tiles-and-notifications/badges).</span><span class="sxs-lookup"><span data-stu-id="1052c-198">For more info, see the  [Badge notifications for UWP apps article](/windows/uwp/design/shell/tiles-and-notifications/badges).</span></span> 


## <a name="more-about-app-icon-assets"></a><span data-ttu-id="1052c-199">Weitere Informationen zu Ressourcen für app-Symbol</span><span class="sxs-lookup"><span data-stu-id="1052c-199">More about app icon assets</span></span>
<span data-ttu-id="1052c-200">Visual Studio generiert alle app-Symbol-Assets, die für das Projekt erforderlich, aber wenn Sie diese anpassen möchten, hilft es um zu verstehen, wie sie sich von anderen app-Ressourcen sind.</span><span class="sxs-lookup"><span data-stu-id="1052c-200">Visual Studio will generate all the app icon assets required by your project, but if you'd like to customize them, it helps to understand how they're different from other app assets.</span></span> 

<span data-ttu-id="1052c-201">Das app-Symbol-Element wird in vielen Stellen: der Windows-Taskleiste, der Aufgabenansicht, ALT + TAB und der unteren rechten Ecke von startkacheln.</span><span class="sxs-lookup"><span data-stu-id="1052c-201">The app icon asset appears in a lot of places: the Windows taskbar, the task view, ALT+TAB, and the lower-right corner of Start tiles.</span></span> <span data-ttu-id="1052c-202">Da die app-Symbol-Ressource an vielen Orten angezeigt wird, verfügt über einige zusätzliche größenanpassung und Optionen, die die andere Ressourcen verfügen nicht über plating: "Target-Size" Bestand und "unbeschichtete" Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="1052c-202">Because the app icon asset appears in so many places, it has some additional sizing and plating options the other assets don't have: "target-size" assets and "unplated" assets.</span></span> 

### <a name="target-size-app-icon-assets"></a><span data-ttu-id="1052c-203">Zielgröße-app-Symbolressourcen</span><span class="sxs-lookup"><span data-stu-id="1052c-203">Target-size app icon assets</span></span>
<span data-ttu-id="1052c-204">Zusätzlich zu den standardmäßigen Skalierungsfaktor Größen ("Square44x44Logo.scale-400.png") empfehlen wir auch "Target-Size" Ressourcen erstellen.</span><span class="sxs-lookup"><span data-stu-id="1052c-204">In addition to the standard scale factor sizes ("Square44x44Logo.scale-400.png"), we also recommend creating "target-size" assets.</span></span> <span data-ttu-id="1052c-205">Wir bezeichnen diese Ressourcen-Zielgröße, da sie bestimmte Größen, z. B. bestimmte Skalierungsfaktoren, z. B. 400, anstatt 16 Pixel abzielen.</span><span class="sxs-lookup"><span data-stu-id="1052c-205">We call these assets target-size because they target specific sizes, such as 16 pixels, rather than specific scale factors, such as 400.</span></span> <span data-ttu-id="1052c-206">Zielgröße-Ressourcen sind für Oberflächen, die Skalierung Plateau System nicht:</span><span class="sxs-lookup"><span data-stu-id="1052c-206">Target-size assets are for surfaces that don't use the scaling plateau system:</span></span>

* <span data-ttu-id="1052c-207">Starten der Sprungliste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="1052c-207">Start jump list (desktop)</span></span>
* <span data-ttu-id="1052c-208">Starten der unteren Ecke der Kachel (Desktop)</span><span class="sxs-lookup"><span data-stu-id="1052c-208">Start lower corner of tile (desktop)</span></span>
* <span data-ttu-id="1052c-209">Tastenkombinationen (Desktop)</span><span class="sxs-lookup"><span data-stu-id="1052c-209">Shortcuts (desktop)</span></span>
* <span data-ttu-id="1052c-210">Systemsteuerung (Desktop)</span><span class="sxs-lookup"><span data-stu-id="1052c-210">Control Panel (desktop)</span></span>

<span data-ttu-id="1052c-211">Hier ist die Liste der Zielgröße-Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="1052c-211">Here's the list of target-size assets:</span></span>


| <span data-ttu-id="1052c-212">Ressourcengröße</span><span class="sxs-lookup"><span data-stu-id="1052c-212">Asset size</span></span> | <span data-ttu-id="1052c-213">Dateinamenbeispiel</span><span class="sxs-lookup"><span data-stu-id="1052c-213">File name example</span></span>                  |
|------------|------------------------------------|
| <span data-ttu-id="1052c-214">16 x 16\*</span><span class="sxs-lookup"><span data-stu-id="1052c-214">16x16\*</span></span>    | <span data-ttu-id="1052c-215">Square44x44Logo.targetsize-16.png</span><span class="sxs-lookup"><span data-stu-id="1052c-215">Square44x44Logo.targetsize-16.png</span></span>  |
| <span data-ttu-id="1052c-216">24 x 24\*</span><span class="sxs-lookup"><span data-stu-id="1052c-216">24x24\*</span></span>    | <span data-ttu-id="1052c-217">Square44x44Logo.targetsize-24.png</span><span class="sxs-lookup"><span data-stu-id="1052c-217">Square44x44Logo.targetsize-24.png</span></span>  |
| <span data-ttu-id="1052c-218">32 x 32\*</span><span class="sxs-lookup"><span data-stu-id="1052c-218">32x32\*</span></span>    | <span data-ttu-id="1052c-219">Square44x44Logo.targetsize-32.png</span><span class="sxs-lookup"><span data-stu-id="1052c-219">Square44x44Logo.targetsize-32.png</span></span>  |
| <span data-ttu-id="1052c-220">48 x 48\*</span><span class="sxs-lookup"><span data-stu-id="1052c-220">48x48\*</span></span>    | <span data-ttu-id="1052c-221">Square44x44Logo.targetsize-48.png</span><span class="sxs-lookup"><span data-stu-id="1052c-221">Square44x44Logo.targetsize-48.png</span></span>  |
| <span data-ttu-id="1052c-222">256 x 256\*</span><span class="sxs-lookup"><span data-stu-id="1052c-222">256x256\*</span></span>  | <span data-ttu-id="1052c-223">Square44x44Logo.targetsize-256.png</span><span class="sxs-lookup"><span data-stu-id="1052c-223">Square44x44Logo.targetsize-256.png</span></span> |
| <span data-ttu-id="1052c-224">20 x 20</span><span class="sxs-lookup"><span data-stu-id="1052c-224">20x20</span></span>      | <span data-ttu-id="1052c-225">Square44x44Logo.targetsize-20.png</span><span class="sxs-lookup"><span data-stu-id="1052c-225">Square44x44Logo.targetsize-20.png</span></span>  |
| <span data-ttu-id="1052c-226">30x30</span><span class="sxs-lookup"><span data-stu-id="1052c-226">30x30</span></span>      | <span data-ttu-id="1052c-227">Square44x44Logo.targetsize-30.png</span><span class="sxs-lookup"><span data-stu-id="1052c-227">Square44x44Logo.targetsize-30.png</span></span>  |
| <span data-ttu-id="1052c-228">36 x 36</span><span class="sxs-lookup"><span data-stu-id="1052c-228">36x36</span></span>      | <span data-ttu-id="1052c-229">Square44x44Logo.targetsize-36.png</span><span class="sxs-lookup"><span data-stu-id="1052c-229">Square44x44Logo.targetsize-36.png</span></span>  |
| <span data-ttu-id="1052c-230">40 x 40</span><span class="sxs-lookup"><span data-stu-id="1052c-230">40x40</span></span>      | <span data-ttu-id="1052c-231">Square44x44Logo.targetsize-40.png</span><span class="sxs-lookup"><span data-stu-id="1052c-231">Square44x44Logo.targetsize-40.png</span></span>  |
| <span data-ttu-id="1052c-232">60 x 60</span><span class="sxs-lookup"><span data-stu-id="1052c-232">60x60</span></span>      | <span data-ttu-id="1052c-233">Square44x44Logo.targetsize-60.png</span><span class="sxs-lookup"><span data-stu-id="1052c-233">Square44x44Logo.targetsize-60.png</span></span>  |
| <span data-ttu-id="1052c-234">64 x 64</span><span class="sxs-lookup"><span data-stu-id="1052c-234">64x64</span></span>      | <span data-ttu-id="1052c-235">Square44x44Logo.targetsize-64.png</span><span class="sxs-lookup"><span data-stu-id="1052c-235">Square44x44Logo.targetsize-64.png</span></span>  |
| <span data-ttu-id="1052c-236">72 x 72</span><span class="sxs-lookup"><span data-stu-id="1052c-236">72x72</span></span>      | <span data-ttu-id="1052c-237">Square44x44Logo.targetsize-72.png</span><span class="sxs-lookup"><span data-stu-id="1052c-237">Square44x44Logo.targetsize-72.png</span></span>  |
| <span data-ttu-id="1052c-238">80 x 80</span><span class="sxs-lookup"><span data-stu-id="1052c-238">80x80</span></span>      | <span data-ttu-id="1052c-239">Square44x44Logo.targetsize-80.png</span><span class="sxs-lookup"><span data-stu-id="1052c-239">Square44x44Logo.targetsize-80.png</span></span>  |
| <span data-ttu-id="1052c-240">96 x 96</span><span class="sxs-lookup"><span data-stu-id="1052c-240">96x96</span></span>      | <span data-ttu-id="1052c-241">Square44x44Logo.targetsize-96.png</span><span class="sxs-lookup"><span data-stu-id="1052c-241">Square44x44Logo.targetsize-96.png</span></span>  |

<span data-ttu-id="1052c-242">\ \* Mindestens, es wird empfohlen, diese Größen.</span><span class="sxs-lookup"><span data-stu-id="1052c-242">\* At a minimum, we recommend providing these sizes.</span></span> 

<span data-ttu-id="1052c-243">Sie müssen für diese Ressourcen keine Abstände hinzufügen, diese werden bei Bedarf von Windows hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1052c-243">You don't have to add padding to these assets; Windows adds padding if needed.</span></span> <span data-ttu-id="1052c-244">Bei diesen Ressourcen sollte eine minimale Fläche von 16Pixeln vorgesehen werden.</span><span class="sxs-lookup"><span data-stu-id="1052c-244">These assets should account for a minimum footprint of 16 pixels.</span></span> 

<span data-ttu-id="1052c-245">Unten sehen Sie ein Beispiel dafür, wie diese Ressourcen als Symbole in der Windows-Taskleiste angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="1052c-245">Here's an example of these assets as they appear in icons on the Windows taskbar:</span></span>

![Ressourcen in Windows-Taskleiste](images/assetguidance21.png)

### <a name="unplated-assets"></a><span data-ttu-id="1052c-247">Unbeschichtete Ressourcen</span><span class="sxs-lookup"><span data-stu-id="1052c-247">Unplated assets</span></span>
<span data-ttu-id="1052c-248">Standardmäßig verwendet Windows eine zielbasierte Ressource neben einer farbigen Rückwand standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="1052c-248">By default, Windows uses a target-based asset on top of a colored backplate by default.</span></span> <span data-ttu-id="1052c-249">Wenn Sie möchten, können Sie eine Ziel zielbasierte Ressource bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1052c-249">If you want, you can provide a target-based unplated asset.</span></span> <span data-ttu-id="1052c-250">"Zielbasierte" bedeutet, dass die Ressource auf einen transparenten Hintergrund angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1052c-250">"Unplated" means the asset will be displayed on a transparent background.</span></span> <span data-ttu-id="1052c-251">Denken Sie daran, die diese Ressourcen über eine Vielzahl von Hintergrundfarben angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1052c-251">Keep in mind that these assets will appear over a variety of background colors.</span></span> 

![Ressourcen mit und ohne Anpassung](images/assetguidance22.png)

<span data-ttu-id="1052c-253">Hier sind die Oberflächen, die Ressourcen für zielbasierte app-Symbole verwenden:</span><span class="sxs-lookup"><span data-stu-id="1052c-253">Here are the surfaces that use unplated app icon assets:</span></span>
* <span data-ttu-id="1052c-254">Taskleiste und Miniaturansicht der Taskleiste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="1052c-254">Taskbar and taskbar thumbnail (desktop)</span></span>
* <span data-ttu-id="1052c-255">Taskleisten-Sprungliste</span><span class="sxs-lookup"><span data-stu-id="1052c-255">Taskbar jumplist</span></span>
* <span data-ttu-id="1052c-256">Aufgabenansicht</span><span class="sxs-lookup"><span data-stu-id="1052c-256">Task view</span></span>
* <span data-ttu-id="1052c-257">ALT + TAB</span><span class="sxs-lookup"><span data-stu-id="1052c-257">ALT+TAB</span></span>


### <a name="target-and-unplated-sizing"></a><span data-ttu-id="1052c-258">Ziel und zielbasierte anpassen</span><span class="sxs-lookup"><span data-stu-id="1052c-258">Target and unplated sizing</span></span>

<span data-ttu-id="1052c-259">Hier sind die Größe Empfehlungen für zielbasierte Ressourcen mit einer Skalierung von 100 %:</span><span class="sxs-lookup"><span data-stu-id="1052c-259">Here are the size recommendations for target-based assets, at 100% scale:</span></span>

![Zielbasierte Ressourcengröße bei einer Skalierung von 100%](images/assetguidance23.png)


## <a name="more-about-splash-screen-assets"></a><span data-ttu-id="1052c-261">Weitere Informationen zu Ressourcen für den Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="1052c-261">More about splash screen assets</span></span>
<span data-ttu-id="1052c-262">Weitere Informationen zu Begrüßungsbildschirme finden Sie im [UWP Begrüßungsbildschirm Bildschirme Artikel](/windows/uwp/launch-resume/splash-screens).</span><span class="sxs-lookup"><span data-stu-id="1052c-262">For more info about splash screens, see the [UWP splash screens article](/windows/uwp/launch-resume/splash-screens).</span></span>

## <a name="more-about-badge-logo-assets"></a><span data-ttu-id="1052c-263">Weitere Informationen zur Badge-Logo-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="1052c-263">More about badge logo assets</span></span>

<span data-ttu-id="1052c-264">Wenn Sie den Asset-Generator verwenden, um alle Ressourcen zu generieren, Sie müssen, ist es ein Grund, warum es Signal Logos standardmäßig generiert nicht: sie sind unterscheidet sich von anderen app-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="1052c-264">When you use the asset generator to generate all the assets you need, there's a reason why it doesn't generate badge logos by default: they're very different from other app assets.</span></span> <span data-ttu-id="1052c-265">Das signallogo ist ein Status-Bild, Benachrichtigungen und in der app-Kacheln angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1052c-265">The badge logo is a status image that appears in notifications and on the app's tiles.</span></span> 

<span data-ttu-id="1052c-266">Weitere Informationen finden Sie unter der [signalbenachrichtigungen für UWP-apps Artikel](/windows/uwp/design/shell/tiles-and-notifications/badges).</span><span class="sxs-lookup"><span data-stu-id="1052c-266">For more information, see the [Badge notifications for UWP apps article](/windows/uwp/design/shell/tiles-and-notifications/badges).</span></span>


## <a name="customizing-asset-padding"></a><span data-ttu-id="1052c-267">Anpassen von Ressourcen "Padding"</span><span class="sxs-lookup"><span data-stu-id="1052c-267">Customizing asset padding</span></span>

<span data-ttu-id="1052c-268">Standardmäßig gilt Visual Studio Asset-Generator empfohlene Abstand für alle Bilder.</span><span class="sxs-lookup"><span data-stu-id="1052c-268">By default, Visual Studio asset generator applies recommended padding to whatever image.</span></span> <span data-ttu-id="1052c-269">Wenn Ihre Bilder bereits Abstand enthalten, oder Sie die randlose-Bilder, die am Ende der Kachel erweitern möchten, können Sie dieses Feature deaktivieren deaktivieren Sie das Kontrollkästchen **"Padding" empfohlen anwenden** .</span><span class="sxs-lookup"><span data-stu-id="1052c-269">If your images already contain padding or you want full bleed images that extend to the end of the tile, you can turn this feature off by unchecking the **Apply recommended padding** check box.</span></span> 

### <a name="tile-padding-recommendations"></a><span data-ttu-id="1052c-270">Kachel "Padding" Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="1052c-270">Tile padding recommendations</span></span>
<span data-ttu-id="1052c-271">Wenn Sie Ihre eigene Padding bereitstellen möchten, folgen Sie unsere Empfehlungen für die Kacheln.</span><span class="sxs-lookup"><span data-stu-id="1052c-271">If you want to provide your own padding, here are our recommendations for tiles.</span></span> 

<span data-ttu-id="1052c-272">Es sind 4 kachelgrößen: klein (71 x 71), Mittel (150 x 150), Wide (310 x 150) und große (310 x 310).</span><span class="sxs-lookup"><span data-stu-id="1052c-272">There are 4 tile sizes: small (71 x 71), medium (150 x 150), wide (310 x 150), and large (310 x 310).</span></span> 

<span data-ttu-id="1052c-273">Jede Kachelressource hat die gleiche Größe wie die Kachel, auf der sie sich befindet.</span><span class="sxs-lookup"><span data-stu-id="1052c-273">Each tile asset is the same size as the tile on which it is placed.</span></span>

![Randlose Kachel](images/app-icons/tile-assets1.png)

<span data-ttu-id="1052c-275">Wenn Sie nicht, dass das Symbol an den Rand der Kachel erweitern möchten, können transparente Pixel in der Ressource Sie "Padding" erstellen.</span><span class="sxs-lookup"><span data-stu-id="1052c-275">If you don't want your icon to extend to the edge of the tile, you can use transparent pixels in your asset to create padding.</span></span> 

![Kachel und Rückwand](images/assetguidance05.png)

<span data-ttu-id="1052c-277">Beschränken Sie bei kleinen Kacheln die Breite und Höhe auf 66% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="1052c-277">For small tiles, limit the icon width and height to 66% of the tile size:</span></span>

![Verhältnisse bei kleinen Kachelgrößen](images/assetguidance09.png)

<span data-ttu-id="1052c-279">Beschränken Sie bei mittelgroßen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="1052c-279">For medium tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="1052c-280">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="1052c-280">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei mittelgroßen Kacheln](images/assetguidance10.png)

<span data-ttu-id="1052c-282">Beschränken Sie bei breiten Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="1052c-282">For wide tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="1052c-283">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="1052c-283">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei breiten Kacheln](images/assetguidance11.png)

<span data-ttu-id="1052c-285">Beschränken Sie bei großen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="1052c-285">For large tiles, limit the icon width to 66% and height to 50% of tile size:</span></span>

![Verhältnisse bei großen Kacheln](images/assetguidance12.png)

<span data-ttu-id="1052c-287">Einige Symbole sind so konzipiert, dass sie horizontal oder vertikal ausgerichtet sind, andere Symbole hingegen weisen komplexere Formen auf, wodurch verhindert wird, dass sie direkt in die Zielabmessungen passen.</span><span class="sxs-lookup"><span data-stu-id="1052c-287">Some icons are designed to be horizontally or vertically oriented, while others have more complex shapes that prevent them from fitting squarely within the target dimensions.</span></span> <span data-ttu-id="1052c-288">Symbole, die zentriert erscheinen, können auf eine Seite geneigt sein.</span><span class="sxs-lookup"><span data-stu-id="1052c-288">Icons that appear to be centered can be weighted to one side.</span></span> <span data-ttu-id="1052c-289">In diesem Fall können Teile eines Symbols aus der empfohlenen Fläche heraushängen, vorausgesetzt, das Symbol belegt dasselbe visuelle Gewicht wie ein genau passendes Symbol:</span><span class="sxs-lookup"><span data-stu-id="1052c-289">In this case, parts of an icon may hang outside the recommended footprint, provided it occupies the same visual weight as a squarely fitted icon:</span></span>

![Drei zentrierte Symbole](images/assetguidance13.png)

<span data-ttu-id="1052c-291">Berücksichtigen Sie bei randlosen Ressourcen Elemente, die innerhalb der Ränder und Kanten der Kacheln interagieren.</span><span class="sxs-lookup"><span data-stu-id="1052c-291">With full-bleed assets, take into account elements that interact within the margins and edges of the tiles.</span></span> <span data-ttu-id="1052c-292">Behalten Sie Ränder von mindestens 16 % der Höhe oder Breite der Kachel bei.</span><span class="sxs-lookup"><span data-stu-id="1052c-292">Maintain margins of at least 16% of the height or width of the tile.</span></span> <span data-ttu-id="1052c-293">Dieser Prozentsatz stellt die doppelte Breite der Ränder bei den kleinsten Kachelgrößen dar:</span><span class="sxs-lookup"><span data-stu-id="1052c-293">This percentage represents double the width of the margins at the smallest tile sizes:</span></span>

![Randlose Kachel mit Rändern](images/assetguidance14.png)

<span data-ttu-id="1052c-295">In diesem Beispiel sind die Ränder zu eng:</span><span class="sxs-lookup"><span data-stu-id="1052c-295">In this example, margins are too tight:</span></span>

![Randlose Kachel mit zu engen Rändern](images/assetguidance15.png)









