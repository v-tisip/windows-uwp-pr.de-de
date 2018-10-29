---
author: mijacobs
Description: How to create app icons/logos that represent your app in the Start menu, app tiles, the taskbar, the Microsoft Store, and more.
title: App-Symbole und Logos
template: detail.hbs
ms.author: mijacobs
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP
design-contact: Judysa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 6c389aa207b0756a222c1c82ea99ea007b451b1e
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5748938"
---
# <a name="app-icons-and-logos"></a><span data-ttu-id="74eb7-103">App-Symbole und Logos</span><span class="sxs-lookup"><span data-stu-id="74eb7-103">App icons and logos</span></span> 

<span data-ttu-id="74eb7-104">Jede app verfügt über ein Symbol/Logo, das es darstellt, und das Symbol an mehreren Standorten in der Windows-Shell angezeigt:</span><span class="sxs-lookup"><span data-stu-id="74eb7-104">Every app has an icon/logo that represents it, and that icon appears in multiple locations in the Windows shell:</span></span> 

:::row:::
    :::column:::
        * <span data-ttu-id="74eb7-105">Der Titelleiste Ihrer app-Fenster</span><span class="sxs-lookup"><span data-stu-id="74eb7-105">The title bar of your app window</span></span>
        * <span data-ttu-id="74eb7-106">App-Liste im Menü "Start"</span><span class="sxs-lookup"><span data-stu-id="74eb7-106">The app list in the start menu</span></span>
        * <span data-ttu-id="74eb7-107">Die Taskleiste und Task-manager</span><span class="sxs-lookup"><span data-stu-id="74eb7-107">The taskbar and task manager</span></span>
        * <span data-ttu-id="74eb7-108">Die app Kacheln</span><span class="sxs-lookup"><span data-stu-id="74eb7-108">Your app's tiles</span></span>
        * <span data-ttu-id="74eb7-109">Begrüßungsbildschirm der app</span><span class="sxs-lookup"><span data-stu-id="74eb7-109">Your app's splash screen</span></span>
        * <span data-ttu-id="74eb7-110">Im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="74eb7-110">In the Microsoft Store</span></span>
    :::column-end:::
    :::column:::
        ![windows 10 start and tiles](images/assetguidance01.jpg)
    :::column-end:::
:::row-end:::

<span data-ttu-id="74eb7-111">In diesem Artikel werden die Grundlagen der Erstellung von app-Symbole, wie Sie Visual Studio verwaltet werden, und wie diese manuell verwalten müssen Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="74eb7-111">This article covers the basics of creating app icons, how to use Visual Studio to manage them, and how manage them manually, should you need to.</span></span>
 
<span data-ttu-id="74eb7-112">(In diesem Artikel ist insbesondere für Symbole, die die app selbst darstellen, allgemeine Symbol-Anleitung finden Sie im Artikel [Symbole](icons.md) .)</span><span class="sxs-lookup"><span data-stu-id="74eb7-112">(This article is specifically for icons that represent the app itself; for general icon guidance, see the [Icons](icons.md) article.)</span></span>

## <a name="icon-types-locations-and-scale-factors"></a><span data-ttu-id="74eb7-113">Symbol Kontotypen, Standorte und Skalierungsfaktoren</span><span class="sxs-lookup"><span data-stu-id="74eb7-113">Icon types, locations, and scale factors</span></span>

<span data-ttu-id="74eb7-114">Standardmäßig speichert Visual Studio die Symbolressourcen in ein Unterverzeichnis Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-114">By default, Visual Studio stores your icon assets in an assets subdirectory.</span></span> <span data-ttu-id="74eb7-115">Hier ist eine Liste der verschiedenen Arten von Symbolen, wo sie angezeigt werden, und wie sie benannt sind.</span><span class="sxs-lookup"><span data-stu-id="74eb7-115">Here's a list of the different types of icons, where they appear, and what they're called.</span></span> 

| <span data-ttu-id="74eb7-116">Symbol ein</span><span class="sxs-lookup"><span data-stu-id="74eb7-116">Icon name</span></span> | <span data-ttu-id="74eb7-117">Erscheint in</span><span class="sxs-lookup"><span data-stu-id="74eb7-117">Appears in</span></span> | <span data-ttu-id="74eb7-118">Asset-Dateiname</span><span class="sxs-lookup"><span data-stu-id="74eb7-118">Asset file name</span></span> |
| ---      | ---        | --- |
| <span data-ttu-id="74eb7-119">Kleine Kachel</span><span class="sxs-lookup"><span data-stu-id="74eb7-119">Small tile</span></span> | <span data-ttu-id="74eb7-120">Startmenü</span><span class="sxs-lookup"><span data-stu-id="74eb7-120">Start menu</span></span> |  <span data-ttu-id="74eb7-121">SmallTile.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-121">SmallTile.png</span></span>  |
| <span data-ttu-id="74eb7-122">Mittelgroße Kachel</span><span class="sxs-lookup"><span data-stu-id="74eb7-122">Medium tile</span></span> |<span data-ttu-id="74eb7-123">Menü "Start", Microsoft Store Listing\ \*</span><span class="sxs-lookup"><span data-stu-id="74eb7-123">Start menu,  Microsoft Store listing\*</span></span>  |  <span data-ttu-id="74eb7-124">Square150x150Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="74eb7-124">Square150x150Logo.png</span></span> |
| <span data-ttu-id="74eb7-125">Breite Kachel</span><span class="sxs-lookup"><span data-stu-id="74eb7-125">Wide tile</span></span>  | <span data-ttu-id="74eb7-126">Startmenü</span><span class="sxs-lookup"><span data-stu-id="74eb7-126">Start menu</span></span>   | <span data-ttu-id="74eb7-127">Wide310x150Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="74eb7-127">Wide310x150Logo.png</span></span> |
| <span data-ttu-id="74eb7-128">Große Kachel</span><span class="sxs-lookup"><span data-stu-id="74eb7-128">Large tile</span></span>   | <span data-ttu-id="74eb7-129">Menü "Start", Microsoft Store Listing\ \*</span><span class="sxs-lookup"><span data-stu-id="74eb7-129">Start menu,  Microsoft Store listing\*</span></span> |  <span data-ttu-id="74eb7-130">LargeTile.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-130">LargeTile.png</span></span>  |
| <span data-ttu-id="74eb7-131">App-Symbol</span><span class="sxs-lookup"><span data-stu-id="74eb7-131">App icon</span></span> | <span data-ttu-id="74eb7-132">App-Liste im Menü "Start", Taskleiste, Task-manager</span><span class="sxs-lookup"><span data-stu-id="74eb7-132">App list in start menu, task bar, task manager</span></span> | <span data-ttu-id="74eb7-133">Square44x44Logo.PNG</span><span class="sxs-lookup"><span data-stu-id="74eb7-133">Square44x44Logo.png</span></span> |
| <span data-ttu-id="74eb7-134">Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="74eb7-134">Splash screen</span></span> | <span data-ttu-id="74eb7-135">Begrüßungsbildschirm der app</span><span class="sxs-lookup"><span data-stu-id="74eb7-135">The app's splash screen</span></span> | <span data-ttu-id="74eb7-136">SplashScreen.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-136">SplashScreen.png</span></span>  |
| <span data-ttu-id="74eb7-137">Signallogo</span><span class="sxs-lookup"><span data-stu-id="74eb7-137">Badge logo</span></span> | <span data-ttu-id="74eb7-138">Die app Kacheln</span><span class="sxs-lookup"><span data-stu-id="74eb7-138">Your app's tiles</span></span> | <span data-ttu-id="74eb7-139">BadgeLogo.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-139">BadgeLogo.png</span></span>  |
| <span data-ttu-id="74eb7-140">Paket-Logo-Speicher-logo</span><span class="sxs-lookup"><span data-stu-id="74eb7-140">Package logo/Store logo</span></span> | <span data-ttu-id="74eb7-141">App-Installer, Dev Center die Option "Melden eine app" im Speicher, die Option "Einen Prüfbericht schreiben" im Store</span><span class="sxs-lookup"><span data-stu-id="74eb7-141">App installer, Dev Center, the "Report an app" option in the Store, the "Write a review" option in the Store</span></span> | <span data-ttu-id="74eb7-142">StoreLogo.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-142">StoreLogo.png</span></span>  |

<span data-ttu-id="74eb7-143">\ \* Verwendet, es sei denn, Sie für die [Anzeige nur Bilder im Store hochgeladen](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store)auswählen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-143">\* Used unless you choose to [display only uploaded images in the Store](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span></span> 

<span data-ttu-id="74eb7-144">Um sicherzustellen, dass diese Symbole für jeden Bildschirm scharf aussehen, können Sie mehrere Versionen des gleichen Schildsymbols für unterschiedliche Skalierungsfaktoren erstellen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-144">To ensure these icons look sharp on every screen, you can create multiple versions of the same icon for different display scale factors.</span></span> 

<span data-ttu-id="74eb7-145">Der Skalierungsfaktor bestimmt die Größe des UI-Elemente, z. B. Text.</span><span class="sxs-lookup"><span data-stu-id="74eb7-145">The  scale factor determines the size of UI elements, such as text.</span></span> <span data-ttu-id="74eb7-146">Skalierung von Faktoren reichen von 100 % und 400 %.</span><span class="sxs-lookup"><span data-stu-id="74eb7-146">Scale factors range from 100% to 400%.</span></span> <span data-ttu-id="74eb7-147">Mit höheren Werten erstellen größer UI-Elemente, und daher leichter auf hohe DPI-Displays finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="74eb7-147">Larger values create larger UI elements, making them easier to see on high-DPI displays.</span></span> 

:::row:::
    :::column:::
        Windows automatically sets the scale factor for each display based on its DPI (dots-per-inch) and the viewing distance of the device. 

        (Users can override the default value by going to the **Settings &gt; Display &gt; Scale and layout** page.)
    :::column-end:::
    :::column:::
        ![](images/icons/display-settings-screen.png)
    :::column-end:::
:::row-end:::  


<span data-ttu-id="74eb7-148">Da Ressourcen für app-Symbole Bitmaps sind und Bitmaps nicht gut skalieren, es wird empfohlen, einer Version jede Ressource Symbol für jedes Skalierungsfaktor: 100 %, 125 %, 150 %, 200 % und 400 %.</span><span class="sxs-lookup"><span data-stu-id="74eb7-148">Because app icon assets are bitmaps and bitmaps don't scale well, we recommend providing a version each icon asset for each scale factor: 100%, 125%, 150%, 200%, and 400%.</span></span> <span data-ttu-id="74eb7-149">Das ist eine Menge von Symbolen!</span><span class="sxs-lookup"><span data-stu-id="74eb7-149">That's a lot of icons!</span></span> <span data-ttu-id="74eb7-150">Fortunatly, Visual Studio bietet ein Tool, das zum Erstellen und aktualisieren diese Symbole erleichtert.</span><span class="sxs-lookup"><span data-stu-id="74eb7-150">Fortunatly, Visual Studio provides a tool that makes it easy to generate and update these icons.</span></span> 

## <a name="microsoft-store-listing-image"></a><span data-ttu-id="74eb7-151">Microsoft Store-Eintrag image</span><span class="sxs-lookup"><span data-stu-id="74eb7-151">Microsoft Store listing image</span></span>

<span data-ttu-id="74eb7-152">"Wie kann ich Bilder für meine app Eintrag im Microsoft Store an?"</span><span class="sxs-lookup"><span data-stu-id="74eb7-152">"How do I specify images for my app's listing in the Microsoft Store?"</span></span>

<span data-ttu-id="74eb7-153">Standardmäßig verwenden wir einige der Bilder von Ihren Paketen im Store wie in der Tabelle am Anfang dieser Seite (sowie andere [Bilder, die Sie während der Übermittlung bereitstellen](https://docs.microsoft.com/en-us/windows/uwp/publish/app-screenshots-and-images)) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="74eb7-153">By default, we use some of the images from your packages in the Store, as described in the table at the top of this page (along with other [images that you provide during the submission process](https://docs.microsoft.com/en-us/windows/uwp/publish/app-screenshots-and-images)).</span></span> <span data-ttu-id="74eb7-154">Allerdings haben Sie die Möglichkeit zu verhindern, dass den Store Logo Bilder in den Paketen Ihrer app zu verwenden, wenn Ihr Angebot für Kunden unter Windows 10 (einschließlich Xbox) angezeigt, und muss stattdessen nur Bilder verwenden, die Sie hochladen Store.</span><span class="sxs-lookup"><span data-stu-id="74eb7-154">However, you have the option to prevent the Store from using the logo images in your app's packages when displaying your listing to customers on Windows 10 (including Xbox), and instead have the Store use only images that you upload.</span></span> <span data-ttu-id="74eb7-155">Dies bietet Ihnen mehr Kontrolle über die Darstellung Ihrer app in verschiedenen anzeigen im Store.</span><span class="sxs-lookup"><span data-stu-id="74eb7-155">This gives you more control over your app’s appearance in various displays throughout the Store.</span></span> <span data-ttu-id="74eb7-156">(Beachten Sie, dass wenn Ihr Produkt für frühere Betriebssystemversionen unterstützt, die Kunden weiterhin Bilder aus Ihren Paketen angezeigt werden, auch wenn Sie diese Option verwenden.) Dies ist im **Store-Logos** Abschnitt des **Store-Eintrag** Schritts im Übermittlungsprozess möglich.</span><span class="sxs-lookup"><span data-stu-id="74eb7-156">(Note that if your product supports earlier OS versions, those customers may still see images from your packages, even if you use this option.) You can do this in the **Store logos** section of the **Store listing** step of the submission process.</span></span>

![Festlegen von Store-Logos während der app-Übermittlungsprozesses](images/app-icons/storelogodisplay.png)

<span data-ttu-id="74eb7-158">Wenn Sie dieses Kontrollkästchen aktivieren, wird ein neuer Abschnitt namens **Store Bilder anzuzeigen** .</span><span class="sxs-lookup"><span data-stu-id="74eb7-158">When you check this box, a new section called **Store display images** appears.</span></span> <span data-ttu-id="74eb7-159">Sie können hier hochladen 3 Bildgrößen, die der Store "anstelle von" logobildern aus den Paketen Ihrer app verwenden: 300 x 300, 150 x 150 und 71 x 71 Pixel.</span><span class="sxs-lookup"><span data-stu-id="74eb7-159">Here, you can upload 3 image sizes that the Store will use in place of logo images from your app’s packages: 300 x 300, 150 x 150, and 71 x 71 pixels.</span></span> <span data-ttu-id="74eb7-160">Nur die Größe 300 x 300 ist erforderlich, obwohl es wird empfohlen, alle 3 Größen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-160">Only the 300 x 300 size is required, although we recommend providing all 3 sizes.</span></span>

<span data-ttu-id="74eb7-161">Weitere Informationen finden Sie in der [Anzeige nur Bilder im Store Logo hochgeladen](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span><span class="sxs-lookup"><span data-stu-id="74eb7-161">For more info, see [Display only uploaded logo images in the Store](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).</span></span>

<!-- ### Fallback images for the Store

The simplest way to control the Store listing image is to specify it during the app submission process. If you don't provide these images during the app submission process, the Store will use a tile image:

1. Large tile
2. Medium tile

If these images aren't provided, the Store will search all matching images of the same image type with a square aspect ratio, preferable with a height greated than the scaled requested height (scaled height is the machine's resolution scale factor * display height). If none of the images meet this criteria, the Store will ignore the scale factor and select an image based on height.  -->

<!-- You can provide screenshots, logos, and other art assets (such as trailers and promotional images to include in your app's Microsoft Store listing. Some of these are required, and some are optional (although some of the optional images are important to include for the best Store display).

The Store may also use your app's tile and other images that you include in your app's package. 

For more information, see [App screenshots, images, and trailers in the Microsoft Store](/windows/uwp/publish/app-screenshots-and-images). -->


## <a name="managing-app-icons-with-the-visual-studio-manifest-designer"></a><span data-ttu-id="74eb7-162">Verwalten von app-Symbole mit dem Visual Studio-Manifest-Designer</span><span class="sxs-lookup"><span data-stu-id="74eb7-162">Managing app icons with the Visual Studio Manifest Designer</span></span>

<span data-ttu-id="74eb7-163">Visual Studio bietet ein sehr nützliches Tool für die Verwaltung von Ihrer app-Symbole im **Manifest-Designer**aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-163">Visual Studio provides a very useful tool for managing your app icons called the **Manifest Designer**.</span></span> 

> <span data-ttu-id="74eb7-164">Wenn Sie Visual Studio 2017 noch nicht, sind verschiedene Versionen verfügbar, z. B. eine kostenlose Version (Visual Studio 2017 Community Edition), und die anderen Versionen bieten kostenlose Testversionen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-164">If you don't already have Visual Studio 2017, there are several versions available, including a free version, (Visual Studio 2017 Community Edition), and the other versions offer free trials.</span></span> <span data-ttu-id="74eb7-165">Sie können sie hier herunterladen:[https://developer.microsoft.com/windows/downloads](https://developer.microsoft.com/windows/downloads)</span><span class="sxs-lookup"><span data-stu-id="74eb7-165">You can download them here: [https://developer.microsoft.com/windows/downloads](https://developer.microsoft.com/windows/downloads)</span></span>


<span data-ttu-id="74eb7-166">So starten Sie den Manifest-Designer</span><span class="sxs-lookup"><span data-stu-id="74eb7-166">To launch the Manifest Designer:</span></span>
<!-- 1. Use Visual Studio to open a UWP project.
2. In the **Solution Explorer**, double-click the package.appmanifest file. 

    ![The Visual Studio 2017 Solution Explorer](images/icons/vs-solution-explorer.png)

    Visual Studio displays the manifest designer.

    ![The Visual Studio 2017 manifest designer](images/icons/vs-manfiest-designer.png)
3. Click the **Visual Assets** tab.

    ![The Visual Assets tab](images/icons/vs-manfiest-designer-visual-assets.png) -->


:::row:::
    :::column:::
        1. <span data-ttu-id="74eb7-167">Verwenden Sie Visual Studio, um ein UWP-Projekt öffnen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-167">Use Visual Studio to open a UWP project.</span></span>
    :::column-end:::
    :::column:::
        
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        2. <span data-ttu-id="74eb7-168">Doppelklicken Sie im **Projektmappen-Explorer**auf die Datei Package.appmxanifest.</span><span class="sxs-lookup"><span data-stu-id="74eb7-168">In the **Solution Explorer**, double-click the Package.appmxanifest file.</span></span>
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
        3. <span data-ttu-id="74eb7-169">Klicken Sie auf der Registerkarte " **Visuelle Anlagen** ".</span><span class="sxs-lookup"><span data-stu-id="74eb7-169">Click the **Visual Assets** tab.</span></span>
    :::column-end:::
    :::column:::
        ![The Visual Assets tab](images/icons/vs-manfiest-designer-visual-assets.png)
    :::column-end:::
:::row-end:::        

## <a name="generating-all-assets-at-once"></a><span data-ttu-id="74eb7-170">Alle Objekte auf einmal generieren</span><span class="sxs-lookup"><span data-stu-id="74eb7-170">Generating all assets at once</span></span>

<span data-ttu-id="74eb7-171">Das erste Menüelement in der Registerkarte " **Visuelle Anlagen** ", **Alle visuellen Ressourcen**, ist genau das, was der Name schon sagt: jede visuelle Ressource, die Ihre app mit dem Drücken der Taste a muss generiert.</span><span class="sxs-lookup"><span data-stu-id="74eb7-171">The first menu item in the **Visual Assets** tab, **All Visual Assets**, does exactly what its name suggests: generates every visual asset your app needs with the press of a button.</span></span>

![Generieren von alle visuellen Ressourcen in Visual Studio](images/app-icons/all-visual-assets.png)

<span data-ttu-id="74eb7-173">Alles, was Sie tun müssen ist ein einzelnes Bild bereitstellen, und Visual Studio generiert die kleine Kachel, mittelgroßen Kachel, große Kachel, Breite Kachel, große Kachel, app-Symbol, Begrüßungsbildschirm, und Logo Ressourcen für jedes Skalierungsfaktor zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="74eb7-173">All you need to do is supply a single image, and Visual Studio will generate the small tile, medium tile, large tile, wide tile, large tile, app icon, splash screen, and package logo assets for every scale factor.</span></span>

<span data-ttu-id="74eb7-174">Um alle Ressourcen auf einmal zu generieren:</span><span class="sxs-lookup"><span data-stu-id="74eb7-174">To generate all assets at once:</span></span>
1. <span data-ttu-id="74eb7-175">Klicken Sie auf die \*\*\*\* neben dem Feld **Quelle** , und wählen Sie das Bild, das Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="74eb7-175">Click the **...** next to the **Source** field and select the image you want to use.</span></span> <span data-ttu-id="74eb7-176">Wenn Sie ein Bitmap-Bild verwenden, stellen Sie sicher, dass sie mindestens 400 um 400 Pixel ist, damit Sie scharfe Ergebnisse erhalten.</span><span class="sxs-lookup"><span data-stu-id="74eb7-176">If you're using a bitmap image, make sure it's at least 400 by 400 pixels so that you get sharp results.</span></span> <span data-ttu-id="74eb7-177">Vektorbasierte Bilder funktionieren am besten; Visual Studio können Sie AI (Adobe Illustrator) und PDF-Dateien verwenden.</span><span class="sxs-lookup"><span data-stu-id="74eb7-177">Vector-based images work best; Visual Studio lets you use AI (Adobe Illustrator) and PDF files.</span></span> 
2. <span data-ttu-id="74eb7-178">(Optional). Konfigurieren Sie im Abschnitt **Anzeigeeinstellungen** folgende Optionen:</span><span class="sxs-lookup"><span data-stu-id="74eb7-178">(Optional.) In the **Display Settings** section, configure these options:</span></span>

    <span data-ttu-id="74eb7-179">a.</span><span class="sxs-lookup"><span data-stu-id="74eb7-179">a.</span></span>  <span data-ttu-id="74eb7-180">**Kurzname**: Geben Sie einen kurzen Namen für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="74eb7-180">**Short name**:  Specify a short name for your app.</span></span>

    <span data-ttu-id="74eb7-181">b.</span><span class="sxs-lookup"><span data-stu-id="74eb7-181">b.</span></span>  <span data-ttu-id="74eb7-182">**Namen anzeigen**: angeben, ob der Kurzname für Mittel, breit, oder große Kacheln angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-182">**Show name**: Indicate whether you want to display the short name on medium, wide, or large tiles.</span></span> 

    <span data-ttu-id="74eb7-183">c.</span><span class="sxs-lookup"><span data-stu-id="74eb7-183">c.</span></span> <span data-ttu-id="74eb7-184">**Hintergrund-Kachel**: Geben Sie den Hexadezimalwert oder einen Farbnamen für die Hintergrundfarbe der Kachel.</span><span class="sxs-lookup"><span data-stu-id="74eb7-184">**Tile background**: Specify the hex value or a color name for the tile background color.</span></span> <span data-ttu-id="74eb7-185">Beispiel: `#464646`.</span><span class="sxs-lookup"><span data-stu-id="74eb7-185">For example, `#464646`.</span></span> <span data-ttu-id="74eb7-186">Der Standardwert lautet `transparent`.</span><span class="sxs-lookup"><span data-stu-id="74eb7-186">The default value is `transparent`.</span></span>

    <span data-ttu-id="74eb7-187">d.</span><span class="sxs-lookup"><span data-stu-id="74eb7-187">d.</span></span> <span data-ttu-id="74eb7-188">**Hintergrund: Splash**: Geben Sie die hex-Wert oder Farbe für den Hintergrund des: Splash.</span><span class="sxs-lookup"><span data-stu-id="74eb7-188">**Spash screen background**: Specify the hex value or color name for the spash screen background.</span></span> 

3. <span data-ttu-id="74eb7-189">Klicken Sie auf **generieren**.</span><span class="sxs-lookup"><span data-stu-id="74eb7-189">Click **Generate**.</span></span> 

<span data-ttu-id="74eb7-190">Visual Studio generiert Bilddateien und Projekt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="74eb7-190">Visual Studio generates your image files and adds them to project.</span></span> <span data-ttu-id="74eb7-191">Wenn Sie Ihre Ressourcen ändern möchten, wiederholen Sie einfach den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="74eb7-191">If you want to change your assets, simply repeat the process.</span></span> 

<span data-ttu-id="74eb7-192">Skalierte Symbolressourcen führen Sie diese Datei Namenskonvention:</span><span class="sxs-lookup"><span data-stu-id="74eb7-192">Scaled icon assets follow this file naming convention:</span></span>

<span data-ttu-id="74eb7-193">*Filename*- Scale -*Skalierungsfaktor*PNG</span><span class="sxs-lookup"><span data-stu-id="74eb7-193">*filename*-scale-*scale factor*.png</span></span>

<span data-ttu-id="74eb7-194">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="74eb7-194">For example,</span></span>

<span data-ttu-id="74eb7-195">Square150x150Logo-Scale-100.png, Square150x150Logo-Scale-200.png, Square150x150Logo-Scale-400.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-195">Square150x150Logo-scale-100.png, Square150x150Logo-scale-200.png, Square150x150Logo-scale-400.png</span></span>

<span data-ttu-id="74eb7-196">Beachten Sie, dass ein signallogo standardmäßig von Visual Studio generiert nicht.</span><span class="sxs-lookup"><span data-stu-id="74eb7-196">Notice that Visual Studio doesn't generate a badge logo by default.</span></span> <span data-ttu-id="74eb7-197">Ist, dass Ihre signallogo ist eindeutig und wahrscheinlich mit Ihrer app-Symbole sollten nicht übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-197">That's because your badge logo is unique and probably shouldn't match your other app icons.</span></span> <span data-ttu-id="74eb7-198">Weitere Informationen finden Sie unter der [signalbenachrichtigungen für UWP-apps Artikel](/windows/uwp/design/shell/tiles-and-notifications/badges).</span><span class="sxs-lookup"><span data-stu-id="74eb7-198">For more info, see the  [Badge notifications for UWP apps article](/windows/uwp/design/shell/tiles-and-notifications/badges).</span></span> 


## <a name="more-about-app-icon-assets"></a><span data-ttu-id="74eb7-199">Weitere Informationen zu Ressourcen für app-Symbole</span><span class="sxs-lookup"><span data-stu-id="74eb7-199">More about app icon assets</span></span>
<span data-ttu-id="74eb7-200">Visual Studio generiert alle app Symbolressourcen für das Projekt erforderlich, aber wenn Sie diese anpassen möchten, hilft es um zu verstehen, wie sie sich von anderen app-Ressourcen sind.</span><span class="sxs-lookup"><span data-stu-id="74eb7-200">Visual Studio will generate all the app icon assets required by your project, but if you'd like to customize them, it helps to understand how they're different from other app assets.</span></span> 

<span data-ttu-id="74eb7-201">Die app-Symbol-Ressource wird in vielen Stellen angezeigt: der Windows-Taskleiste, der Aufgabenansicht, ALT + TAB und der unteren rechten Ecke von startkacheln.</span><span class="sxs-lookup"><span data-stu-id="74eb7-201">The app icon asset appears in a lot of places: the Windows taskbar, the task view, ALT+TAB, and the lower-right corner of Start tiles.</span></span> <span data-ttu-id="74eb7-202">Da die app-Symbol Ressource an vielen Orten angezeigt wird, verfügt über einige zusätzliche größenanpassung und Optionen, die die andere Ressourcen verfügen nicht über plating: "Target-Size" Bestand und "unbeschichtete" Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-202">Because the app icon asset appears in so many places, it has some additional sizing and plating options the other assets don't have: "target-size" assets and "unplated" assets.</span></span> 

### <a name="target-size-app-icon-assets"></a><span data-ttu-id="74eb7-203">Zielgröße-app Symbolressourcen</span><span class="sxs-lookup"><span data-stu-id="74eb7-203">Target-size app icon assets</span></span>
<span data-ttu-id="74eb7-204">Zusätzlich zu den standardmäßigen Skalierungsfaktor Größen ("Square44x44Logo.scale-400.png") empfehlen wir auch "Target-Size" Ressourcen erstellen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-204">In addition to the standard scale factor sizes ("Square44x44Logo.scale-400.png"), we also recommend creating "target-size" assets.</span></span> <span data-ttu-id="74eb7-205">Wir bezeichnen diese Ressourcen Zielgröße, da sie bestimmte Größen, z. B. bestimmte Skalierungsfaktoren, z. B. 400, anstatt 16 Pixel abzielen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-205">We call these assets target-size because they target specific sizes, such as 16 pixels, rather than specific scale factors, such as 400.</span></span> <span data-ttu-id="74eb7-206">Zielgröße-Ressourcen sind für Oberflächen, die Skalierung Plateau System nicht:</span><span class="sxs-lookup"><span data-stu-id="74eb7-206">Target-size assets are for surfaces that don't use the scaling plateau system:</span></span>

* <span data-ttu-id="74eb7-207">Starten der Sprungliste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="74eb7-207">Start jump list (desktop)</span></span>
* <span data-ttu-id="74eb7-208">Starten der unteren Ecke der Kachel (Desktop)</span><span class="sxs-lookup"><span data-stu-id="74eb7-208">Start lower corner of tile (desktop)</span></span>
* <span data-ttu-id="74eb7-209">Tastenkombinationen (Desktop)</span><span class="sxs-lookup"><span data-stu-id="74eb7-209">Shortcuts (desktop)</span></span>
* <span data-ttu-id="74eb7-210">Systemsteuerung (Desktop)</span><span class="sxs-lookup"><span data-stu-id="74eb7-210">Control Panel (desktop)</span></span>

<span data-ttu-id="74eb7-211">Hier ist die Liste der Zielgröße-Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="74eb7-211">Here's the list of target-size assets:</span></span>


| <span data-ttu-id="74eb7-212">Ressourcengröße</span><span class="sxs-lookup"><span data-stu-id="74eb7-212">Asset size</span></span> | <span data-ttu-id="74eb7-213">Dateinamenbeispiel</span><span class="sxs-lookup"><span data-stu-id="74eb7-213">File name example</span></span>                  |
|------------|------------------------------------|
| <span data-ttu-id="74eb7-214">16 x 16\*</span><span class="sxs-lookup"><span data-stu-id="74eb7-214">16x16\*</span></span>    | <span data-ttu-id="74eb7-215">Square44x44Logo.targetsize-16.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-215">Square44x44Logo.targetsize-16.png</span></span>  |
| <span data-ttu-id="74eb7-216">24 x 24\*</span><span class="sxs-lookup"><span data-stu-id="74eb7-216">24x24\*</span></span>    | <span data-ttu-id="74eb7-217">Square44x44Logo.targetsize-24.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-217">Square44x44Logo.targetsize-24.png</span></span>  |
| <span data-ttu-id="74eb7-218">32 x 32\*</span><span class="sxs-lookup"><span data-stu-id="74eb7-218">32x32\*</span></span>    | <span data-ttu-id="74eb7-219">Square44x44Logo.targetsize-32.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-219">Square44x44Logo.targetsize-32.png</span></span>  |
| <span data-ttu-id="74eb7-220">48 x 48\*</span><span class="sxs-lookup"><span data-stu-id="74eb7-220">48x48\*</span></span>    | <span data-ttu-id="74eb7-221">Square44x44Logo.targetsize-48.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-221">Square44x44Logo.targetsize-48.png</span></span>  |
| <span data-ttu-id="74eb7-222">256 x 256\*</span><span class="sxs-lookup"><span data-stu-id="74eb7-222">256x256\*</span></span>  | <span data-ttu-id="74eb7-223">Square44x44Logo.targetsize-256.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-223">Square44x44Logo.targetsize-256.png</span></span> |
| <span data-ttu-id="74eb7-224">20 x 20</span><span class="sxs-lookup"><span data-stu-id="74eb7-224">20x20</span></span>      | <span data-ttu-id="74eb7-225">Square44x44Logo.targetsize-20.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-225">Square44x44Logo.targetsize-20.png</span></span>  |
| <span data-ttu-id="74eb7-226">30x30</span><span class="sxs-lookup"><span data-stu-id="74eb7-226">30x30</span></span>      | <span data-ttu-id="74eb7-227">Square44x44Logo.targetsize-30.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-227">Square44x44Logo.targetsize-30.png</span></span>  |
| <span data-ttu-id="74eb7-228">36 x 36</span><span class="sxs-lookup"><span data-stu-id="74eb7-228">36x36</span></span>      | <span data-ttu-id="74eb7-229">Square44x44Logo.targetsize-36.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-229">Square44x44Logo.targetsize-36.png</span></span>  |
| <span data-ttu-id="74eb7-230">40 x 40</span><span class="sxs-lookup"><span data-stu-id="74eb7-230">40x40</span></span>      | <span data-ttu-id="74eb7-231">Square44x44Logo.targetsize-40.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-231">Square44x44Logo.targetsize-40.png</span></span>  |
| <span data-ttu-id="74eb7-232">60 x 60</span><span class="sxs-lookup"><span data-stu-id="74eb7-232">60x60</span></span>      | <span data-ttu-id="74eb7-233">Square44x44Logo.targetsize-60.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-233">Square44x44Logo.targetsize-60.png</span></span>  |
| <span data-ttu-id="74eb7-234">64 x 64</span><span class="sxs-lookup"><span data-stu-id="74eb7-234">64x64</span></span>      | <span data-ttu-id="74eb7-235">Square44x44Logo.targetsize-64.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-235">Square44x44Logo.targetsize-64.png</span></span>  |
| <span data-ttu-id="74eb7-236">72 x 72</span><span class="sxs-lookup"><span data-stu-id="74eb7-236">72x72</span></span>      | <span data-ttu-id="74eb7-237">Square44x44Logo.targetsize-72.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-237">Square44x44Logo.targetsize-72.png</span></span>  |
| <span data-ttu-id="74eb7-238">80 x 80</span><span class="sxs-lookup"><span data-stu-id="74eb7-238">80x80</span></span>      | <span data-ttu-id="74eb7-239">Square44x44Logo.targetsize-80.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-239">Square44x44Logo.targetsize-80.png</span></span>  |
| <span data-ttu-id="74eb7-240">96 x 96</span><span class="sxs-lookup"><span data-stu-id="74eb7-240">96x96</span></span>      | <span data-ttu-id="74eb7-241">Square44x44Logo.targetsize-96.png</span><span class="sxs-lookup"><span data-stu-id="74eb7-241">Square44x44Logo.targetsize-96.png</span></span>  |

<span data-ttu-id="74eb7-242">\ \* Mindestens, es wird empfohlen, diese Größen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-242">\* At a minimum, we recommend providing these sizes.</span></span> 

<span data-ttu-id="74eb7-243">Sie müssen für diese Ressourcen keine Abstände hinzufügen, diese werden bei Bedarf von Windows hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="74eb7-243">You don't have to add padding to these assets; Windows adds padding if needed.</span></span> <span data-ttu-id="74eb7-244">Bei diesen Ressourcen sollte eine minimale Fläche von 16Pixeln vorgesehen werden.</span><span class="sxs-lookup"><span data-stu-id="74eb7-244">These assets should account for a minimum footprint of 16 pixels.</span></span> 

<span data-ttu-id="74eb7-245">Unten sehen Sie ein Beispiel dafür, wie diese Ressourcen als Symbole in der Windows-Taskleiste angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="74eb7-245">Here's an example of these assets as they appear in icons on the Windows taskbar:</span></span>

![Ressourcen in Windows-Taskleiste](images/assetguidance21.png)

### <a name="unplated-assets"></a><span data-ttu-id="74eb7-247">Unbeschichtete Ressourcen</span><span class="sxs-lookup"><span data-stu-id="74eb7-247">Unplated assets</span></span>
<span data-ttu-id="74eb7-248">Standardmäßig verwendet Windows eine zielbasierte Ressource neben einer farbigen Rückwand standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="74eb7-248">By default, Windows uses a target-based asset on top of a colored backplate by default.</span></span> <span data-ttu-id="74eb7-249">Wenn Sie möchten, können Sie eine zielbasierte zielbasierte Ressource bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-249">If you want, you can provide a target-based unplated asset.</span></span> <span data-ttu-id="74eb7-250">"Unbeschichtete" bedeutet, dass die Ressource auf einen transparenten Hintergrund angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74eb7-250">"Unplated" means the asset will be displayed on a transparent background.</span></span> <span data-ttu-id="74eb7-251">Denken Sie daran, die diese Ressourcen über eine Vielzahl von Hintergrundfarben angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74eb7-251">Keep in mind that these assets will appear over a variety of background colors.</span></span> 

![Ressourcen mit und ohne Anpassung](images/assetguidance22.png)

<span data-ttu-id="74eb7-253">Hier sind die Oberflächen, die Symbolressourcen unbeschichtete app verwenden:</span><span class="sxs-lookup"><span data-stu-id="74eb7-253">Here are the surfaces that use unplated app icon assets:</span></span>
* <span data-ttu-id="74eb7-254">Taskleiste und Miniaturansicht der Taskleiste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="74eb7-254">Taskbar and taskbar thumbnail (desktop)</span></span>
* <span data-ttu-id="74eb7-255">Taskleisten-Sprungliste</span><span class="sxs-lookup"><span data-stu-id="74eb7-255">Taskbar jumplist</span></span>
* <span data-ttu-id="74eb7-256">Aufgabenansicht</span><span class="sxs-lookup"><span data-stu-id="74eb7-256">Task view</span></span>
* <span data-ttu-id="74eb7-257">ALT + TAB</span><span class="sxs-lookup"><span data-stu-id="74eb7-257">ALT+TAB</span></span>


### <a name="target-and-unplated-sizing"></a><span data-ttu-id="74eb7-258">Ziel und zielbasierte anpassen</span><span class="sxs-lookup"><span data-stu-id="74eb7-258">Target and unplated sizing</span></span>

<span data-ttu-id="74eb7-259">Hier sind die empfohlenen Größe für zielbasierte Ressourcen bei einer Skalierung von 100 %:</span><span class="sxs-lookup"><span data-stu-id="74eb7-259">Here are the size recommendations for target-based assets, at 100% scale:</span></span>

![Zielbasierte Ressourcengröße bei einer Skalierung von 100%](images/assetguidance23.png)


## <a name="more-about-splash-screen-assets"></a><span data-ttu-id="74eb7-261">Weitere Informationen zu Ressourcen für den Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="74eb7-261">More about splash screen assets</span></span>
<span data-ttu-id="74eb7-262">Weitere Informationen zu Begrüßungsbildschirme finden Sie im [UWP Begrüßungsbildschirm Bildschirme Artikel](/windows/uwp/launch-resume/splash-screens).</span><span class="sxs-lookup"><span data-stu-id="74eb7-262">For more info about splash screens, see the [UWP splash screens article](/windows/uwp/launch-resume/splash-screens).</span></span>

## <a name="more-about-badge-logo-assets"></a><span data-ttu-id="74eb7-263">Weitere Informationen zur Badge-Logo-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="74eb7-263">More about badge logo assets</span></span>

<span data-ttu-id="74eb7-264">Wenn Sie den Asset-Generator verwenden, um alle Ressourcen zu generieren, Sie müssen, es gibt ein Grund, warum es Signal Logos standardmäßig generiert nicht: sie sind unterscheidet sich von anderen app-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-264">When you use the asset generator to generate all the assets you need, there's a reason why it doesn't generate badge logos by default: they're very different from other app assets.</span></span> <span data-ttu-id="74eb7-265">Das signallogo ist ein Status-Bild, das in Benachrichtigungen und auf die app-Kacheln angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74eb7-265">The badge logo is a status image that appears in notifications and on the app's tiles.</span></span> 

<span data-ttu-id="74eb7-266">Weitere Informationen finden Sie unter der [signalbenachrichtigungen für UWP-apps Artikel](/windows/uwp/design/shell/tiles-and-notifications/badges).</span><span class="sxs-lookup"><span data-stu-id="74eb7-266">For more information, see the [Badge notifications for UWP apps article](/windows/uwp/design/shell/tiles-and-notifications/badges).</span></span>


## <a name="customizing-asset-padding"></a><span data-ttu-id="74eb7-267">Anpassen der Ressource "Padding"</span><span class="sxs-lookup"><span data-stu-id="74eb7-267">Customizing asset padding</span></span>

<span data-ttu-id="74eb7-268">Standardmäßig gilt Asset-Generator von Visual Studio empfohlene "Padding" für alle Bilder.</span><span class="sxs-lookup"><span data-stu-id="74eb7-268">By default, Visual Studio asset generator applies recommended padding to whatever image.</span></span> <span data-ttu-id="74eb7-269">Wenn Ihre Bilder "Padding" bereits enthalten, oder Sie randlose Bilder, die am Ende der Kachel erweitern möchten, können Sie dieses Feature deaktivieren directly das Kontrollkästchen **"Padding" empfohlen anwenden** .</span><span class="sxs-lookup"><span data-stu-id="74eb7-269">If your images already contain padding or you want full bleed images that extend to the end of the tile, you can turn this feature off by unchecking the **Apply recommended padding** check box.</span></span> 

### <a name="tile-padding-recommendations"></a><span data-ttu-id="74eb7-270">Kachel "Padding" Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="74eb7-270">Tile padding recommendations</span></span>
<span data-ttu-id="74eb7-271">Wenn Sie Ihre eigene Padding bereitstellen möchten, folgen Sie unsere Empfehlungen für die Kacheln.</span><span class="sxs-lookup"><span data-stu-id="74eb7-271">If you want to provide your own padding, here are our recommendations for tiles.</span></span> 

<span data-ttu-id="74eb7-272">Es gibt 4 kachelgrößen: klein (71 x 71), Mittel (150 x 150), Wide (310 x 150) und große (310 x 310).</span><span class="sxs-lookup"><span data-stu-id="74eb7-272">There are 4 tile sizes: small (71 x 71), medium (150 x 150), wide (310 x 150), and large (310 x 310).</span></span> 

<span data-ttu-id="74eb7-273">Jede Kachelressource hat die gleiche Größe wie die Kachel, auf der sie sich befindet.</span><span class="sxs-lookup"><span data-stu-id="74eb7-273">Each tile asset is the same size as the tile on which it is placed.</span></span>

![Randlose Kachel](images/app-icons/tile-assets1.png)

<span data-ttu-id="74eb7-275">Wenn Sie nicht, dass Ihr Symbol an den Rand der Kachel erweitern möchten, können Sie transparente Pixel in Ihrem Bestand verwenden, um "Padding" zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-275">If you don't want your icon to extend to the edge of the tile, you can use transparent pixels in your asset to create padding.</span></span> 

![Kachel und Rückwand](images/assetguidance05.png)

<span data-ttu-id="74eb7-277">Beschränken Sie bei kleinen Kacheln die Breite und Höhe auf 66% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="74eb7-277">For small tiles, limit the icon width and height to 66% of the tile size:</span></span>

![Verhältnisse bei kleinen Kachelgrößen](images/assetguidance09.png)

<span data-ttu-id="74eb7-279">Beschränken Sie bei mittelgroßen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="74eb7-279">For medium tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="74eb7-280">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="74eb7-280">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei mittelgroßen Kacheln](images/assetguidance10.png)

<span data-ttu-id="74eb7-282">Beschränken Sie bei breiten Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="74eb7-282">For wide tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="74eb7-283">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="74eb7-283">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei breiten Kacheln](images/assetguidance11.png)

<span data-ttu-id="74eb7-285">Beschränken Sie bei großen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="74eb7-285">For large tiles, limit the icon width to 66% and height to 50% of tile size:</span></span>

![Verhältnisse bei großen Kacheln](images/assetguidance12.png)

<span data-ttu-id="74eb7-287">Einige Symbole sind so konzipiert, dass sie horizontal oder vertikal ausgerichtet sind, andere Symbole hingegen weisen komplexere Formen auf, wodurch verhindert wird, dass sie direkt in die Zielabmessungen passen.</span><span class="sxs-lookup"><span data-stu-id="74eb7-287">Some icons are designed to be horizontally or vertically oriented, while others have more complex shapes that prevent them from fitting squarely within the target dimensions.</span></span> <span data-ttu-id="74eb7-288">Symbole, die zentriert erscheinen, können auf eine Seite geneigt sein.</span><span class="sxs-lookup"><span data-stu-id="74eb7-288">Icons that appear to be centered can be weighted to one side.</span></span> <span data-ttu-id="74eb7-289">In diesem Fall können Teile eines Symbols aus der empfohlenen Fläche heraushängen, vorausgesetzt, das Symbol belegt dasselbe visuelle Gewicht wie ein genau passendes Symbol:</span><span class="sxs-lookup"><span data-stu-id="74eb7-289">In this case, parts of an icon may hang outside the recommended footprint, provided it occupies the same visual weight as a squarely fitted icon:</span></span>

![Drei zentrierte Symbole](images/assetguidance13.png)

<span data-ttu-id="74eb7-291">Berücksichtigen Sie bei randlosen Ressourcen Elemente, die innerhalb der Ränder und Kanten der Kacheln interagieren.</span><span class="sxs-lookup"><span data-stu-id="74eb7-291">With full-bleed assets, take into account elements that interact within the margins and edges of the tiles.</span></span> <span data-ttu-id="74eb7-292">Behalten Sie Ränder von mindestens 16 % der Höhe oder Breite der Kachel bei.</span><span class="sxs-lookup"><span data-stu-id="74eb7-292">Maintain margins of at least 16% of the height or width of the tile.</span></span> <span data-ttu-id="74eb7-293">Dieser Prozentsatz stellt die doppelte Breite der Ränder bei den kleinsten Kachelgrößen dar:</span><span class="sxs-lookup"><span data-stu-id="74eb7-293">This percentage represents double the width of the margins at the smallest tile sizes:</span></span>

![Randlose Kachel mit Rändern](images/assetguidance14.png)

<span data-ttu-id="74eb7-295">In diesem Beispiel sind die Ränder zu eng:</span><span class="sxs-lookup"><span data-stu-id="74eb7-295">In this example, margins are too tight:</span></span>

![Randlose Kachel mit zu engen Rändern](images/assetguidance15.png)









