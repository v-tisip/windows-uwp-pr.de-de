---
Description: Your app can load image resource files containing images tailored for display scale factor, theme, high contrast, and other runtime contexts.
title: Laden von Bildern und Ressourcen mit Anpassung an Skalierung, Design, hohen Kontrast usw.
template: detail.hbs
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, uwp, Ressourcen, Bild, Element, MRT, Qualifizierer
ms.localizationpriority: medium
ms.openlocfilehash: 6f4749b8560624ed58f43b33fe3373d909919347
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8929496"
---
# <a name="load-images-and-assets-tailored-for-scale-theme-high-contrast-and-others"></a><span data-ttu-id="396c9-103">Laden von Bilder und Ressourcen mit Anpassung an Skalierung, Design, hohen Kontrast und anders</span><span class="sxs-lookup"><span data-stu-id="396c9-103">Load images and assets tailored for scale, theme, high contrast, and others</span></span>
<span data-ttu-id="396c9-104">Ihre App kann Bild-Ressourcendateien mit Bildern (und andere Ressourcendateien) laden, die speziell auf den [Skalierungsfaktor für die Anzeige](../design/layout/screen-sizes-and-breakpoints-for-responsive-design.md), das Design, den hohen Kontrast und anderen Laufzeitkontexte angepasst wurden</span><span class="sxs-lookup"><span data-stu-id="396c9-104">Your app can load image resource files (or other asset files) tailored for [display scale factor](../design/layout/screen-sizes-and-breakpoints-for-responsive-design.md), theme, high contrast, and other runtime contexts.</span></span> <span data-ttu-id="396c9-105">Auf diese Bilder kann im imperativen Code oder im XAML-Markup verwiesen werden, z.B. als **Quellen**-Eigenschaft eines **Bildes**.</span><span class="sxs-lookup"><span data-stu-id="396c9-105">These images can be referenced from imperative code or from XAML markup, for example as the **Source** property of an **Image**.</span></span> <span data-ttu-id="396c9-106">Sie können auch in Ihrer App-Paketmanifest-Quelldatei erscheinen (in der Datei `Package.appxmanifest`), z.B. als Wert für das App-Symbol auf der Registerkarte „Visuelle Anlagen” des Manifest-Designers von Visual Studio, oder auf Ihren Kacheln und Popups.</span><span class="sxs-lookup"><span data-stu-id="396c9-106">They can also appear in your app package manifest source file (the `Package.appxmanifest` file)&mdash;for example, as the value for App Icon on the Visual Assets tab of the Visual Studio Manifest Designer&mdash;or on your tiles and toasts.</span></span> <span data-ttu-id="396c9-107">Indem Sie Qualifizierer in den Dateinamen Ihrer Bilder verwenden und die Bilder optional mit Hilfe eines [**ResourceContext**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live) dynamisch laden, können Sie die am besten passende Bilddatei laden, die den Runtime-Einstellungen des Benutzers für Bildschirmskalierung, Design, hohen Kontrast, Sprache und andere Kontexte am besten entspricht.</span><span class="sxs-lookup"><span data-stu-id="396c9-107">By using qualifiers in your images' file names, and optionally dynamically loading them with the help of a [**ResourceContext**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live), you can cause the most appropriate image file to be loaded that best matches the user's runtime settings for display scale, theme, high contrast, language, and other contexts.</span></span>

<span data-ttu-id="396c9-108">Eine Bildressource ist in einer Bildressourcendatei enthalten.</span><span class="sxs-lookup"><span data-stu-id="396c9-108">An image resource is contained in an image resource file.</span></span> <span data-ttu-id="396c9-109">Sie können Bilder auch als Ressource betrachten, und die Datei, die es enthält als Ressourcendatei. Diese Arten von Ressourcendateien finden Sie im Ordner des Projekts \Assets.</span><span class="sxs-lookup"><span data-stu-id="396c9-109">You can also think of the image as an asset, and the file that contains it as an asset file; and you can find these kinds of resource files in your project's \Assets folder.</span></span> <span data-ttu-id="396c9-110">Hintergrundinformationen zur Verwendung von Qualifizierern in den Namen der Bild-Ressourcendateien finden Sie unter [Passen Sie Ihrer Ressourcen der Sprache, Skalierung und anderen Qualifizierern an](tailor-resources-lang-scale-contrast.md).</span><span class="sxs-lookup"><span data-stu-id="396c9-110">For background on how to use qualifiers in the names of your image resource files, see [Tailor your resources for language, scale, and other qualifiers](tailor-resources-lang-scale-contrast.md).</span></span>

<span data-ttu-id="396c9-111">Einige allgemeine Qualifizierer für Bilder sind [Skalierung](tailor-resources-lang-scale-contrast.md#scale), [Design](tailor-resources-lang-scale-contrast.md#theme), [Kontrast](tailor-resources-lang-scale-contrast.md#contrast) und [Zielgröße](tailor-resources-lang-scale-contrast.md#targetsize).</span><span class="sxs-lookup"><span data-stu-id="396c9-111">Some common qualifiers for images are [scale](tailor-resources-lang-scale-contrast.md#scale), [theme](tailor-resources-lang-scale-contrast.md#theme), [contrast](tailor-resources-lang-scale-contrast.md#contrast), and [targetsize](tailor-resources-lang-scale-contrast.md#targetsize).</span></span>

## <a name="qualify-an-image-resource-for-scale-theme-and-contrast"></a><span data-ttu-id="396c9-112">Qualifizieren von Bildressourcen für Skalierung, Design und Kontrast</span><span class="sxs-lookup"><span data-stu-id="396c9-112">Qualify an image resource for scale, theme, and contrast</span></span>
<span data-ttu-id="396c9-113">Der Standardwert für den `scale` Qualifizierer lautet `scale-100`.</span><span class="sxs-lookup"><span data-stu-id="396c9-113">The default value for the `scale` qualifier is `scale-100`.</span></span> <span data-ttu-id="396c9-114">Daher sind diese beiden Varianten gleichwertig (sie bieten ein Bild mit einer Skalierung von 100 oder einem Skalierungsfaktor von 1).</span><span class="sxs-lookup"><span data-stu-id="396c9-114">So, these two variants are equivalent (they both provide an image at scale 100, or scale factor 1).</span></span>

```
\Assets\Images\logo.png
\Assets\Images\logo.scale-100.png
```

<span data-ttu-id="396c9-115">Sie können Qualifizierer in Ordnernamen anstelle von Dateinamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="396c9-115">You can use qualifiers in folder names instead of file names.</span></span> <span data-ttu-id="396c9-116">Wenn Sie mehrere Ressourcendateien pro Qualifizierer haben, ist dies eine bessere Strategie.</span><span class="sxs-lookup"><span data-stu-id="396c9-116">That would be a better strategy if you have several asset files per qualifier.</span></span> <span data-ttu-id="396c9-117">Zu Demonstrationszwecken sind diese zwei Varianten mit den beiden obigen gleichwertig.</span><span class="sxs-lookup"><span data-stu-id="396c9-117">For purposes of illustration, these two variants are equivalent to the two above.</span></span>

```
\Assets\Images\logo.png
\Assets\Images\scale-100\logo.png
```

<span data-ttu-id="396c9-118">Als Nächstes sehen Sie ein Beispiel zur Bereitstellung von Varianten in einer Bildressource&mdash;mit dem Namen `/Assets/Images/logo.png`&mdash;für unterschiedliche Einstellungen der Anzeige: Skalierung, Design, hoher Kontrast.</span><span class="sxs-lookup"><span data-stu-id="396c9-118">Next is an example of how you can provide variants of an image resource&mdash;named `/Assets/Images/logo.png`&mdash;for different settings of display scale, theme, and high contrast.</span></span> <span data-ttu-id="396c9-119">Dieses Beispiel verwendet die Ordnerbenennung.</span><span class="sxs-lookup"><span data-stu-id="396c9-119">This example uses folder naming.</span></span>

```
\Assets\Images\contrast-standard\theme-dark
    \scale-100\logo.png
    \scale-200\logo.png
\Assets\Images\contrast-standard\theme-light
    \scale-100\logo.png
    \scale-200\logo.png
\Assets\Images\contrast-high
    \scale-100\logo.png
    \scale-200\logo.png
```

## <a name="reference-an-image-or-other-asset-from-xaml-markup-and-code"></a><span data-ttu-id="396c9-120">Verweisen auf ein Bild oder eine Ressource aus XAML-Markup und Code</span><span class="sxs-lookup"><span data-stu-id="396c9-120">Reference an image or other asset from XAML markup and code</span></span>
<span data-ttu-id="396c9-121">Der Name&mdash;oder Bezeichner&mdash;einer Bildressource ist der Pfad und Dateiname, aus dem alle Qualifizierer entfernt wurden.</span><span class="sxs-lookup"><span data-stu-id="396c9-121">The name&mdash;or identifier&mdash;of an image resource is its path and file name with any and all qualifiers removed.</span></span> <span data-ttu-id="396c9-122">Wenn Sie Ordner und/oder Dateien wie im obigen Beispiele des vorherigen Abschnitts benannt haben, erhalten Sie eine einzelne Bild-Ressource und der Anzeigename (als absoluter Pfad) lautet `/Assets/Images/logo.png`.</span><span class="sxs-lookup"><span data-stu-id="396c9-122">If you name folders and/or files as in any of the examples in the previous section, then you have a single image resource and its name (as an absolute path) is `/Assets/Images/logo.png`.</span></span> <span data-ttu-id="396c9-123">So verwenden Sie diesen Namen in XAML-Markups.</span><span class="sxs-lookup"><span data-stu-id="396c9-123">Here’s how you use that name in XAML markup.</span></span>

```xaml
<Image x:Name="myXAMLImageElement" Source="ms-appx:///Assets/Images/logo.png"/>
```

<span data-ttu-id="396c9-124">Beachten Sie, dass Sie das `ms-appx`-URI-Schema verwenden, da Sie auf eine Datei verweisen, die von Ihrem App-Paket stammt.</span><span class="sxs-lookup"><span data-stu-id="396c9-124">Notice that you use the `ms-appx` URI scheme because you're referring to a file that comes from your app's package.</span></span> <span data-ttu-id="396c9-125">Weitere Informationen finden Sie unter [URI-Schemen](uri-schemes.md).</span><span class="sxs-lookup"><span data-stu-id="396c9-125">See [URI schemes](uri-schemes.md).</span></span> <span data-ttu-id="396c9-126">Hier erfahren Sie, wie Sie auf die gleiche Bildressource in imperativem Code verweisen.</span><span class="sxs-lookup"><span data-stu-id="396c9-126">And here’s how you refer to the same image resource in imperative code.</span></span>

```csharp
this.myXAMLImageElement.Source = new BitmapImage(new Uri("ms-appx:///Assets/Images/logo.png"));
```

<span data-ttu-id="396c9-127">Sie können mit `ms-appx` jede beliebige Datei aus dem App-Paket laden.</span><span class="sxs-lookup"><span data-stu-id="396c9-127">You can use `ms-appx` to load any arbitrary file from your app package.</span></span>

```csharp
var uri = new System.Uri("ms-appx:///Assets/anyAsset.ext");
var storagefile = await Windows.Storage.StorageFile.GetFileFromApplicationUriAsync(uri);
```

<span data-ttu-id="396c9-128">Das `ms-appx-web`-Schema greift auf die gleichen Dateien wie `ms-appx` zu, jedoch im Webdepot.</span><span class="sxs-lookup"><span data-stu-id="396c9-128">The `ms-appx-web` scheme accesses the same files as `ms-appx`, but in the web compartment.</span></span>

```xaml
<WebView x:Name="myXAMLWebViewElement" Source="ms-appx-web:///Pages/default.html"/>
```

```csharp
this.myXAMLWebViewElement.Source = new Uri("ms-appx-web:///Pages/default.html");
```

<span data-ttu-id="396c9-129">Für die in diesen Beispielen gezeigten Szenarien verwenden Sie die [URI-Konstruktor](https://docs.microsoft.com/en-us/dotnet/api/system.uri.-ctor?view=netcore-2.0#System_Uri__ctor_System_String_)-Überladung, die [UriKind](https://docs.microsoft.com/en-us/dotnet/api/system.urikind) ableitet.</span><span class="sxs-lookup"><span data-stu-id="396c9-129">For any of the scenarios shown in these examples, use the [Uri constructor](https://docs.microsoft.com/en-us/dotnet/api/system.uri.-ctor?view=netcore-2.0#System_Uri__ctor_System_String_) overload that infers the [UriKind](https://docs.microsoft.com/en-us/dotnet/api/system.urikind).</span></span> <span data-ttu-id="396c9-130">Geben Sie einen gültigen absoluten URI einschließlich Schema und Autorität ein oder überlassen Sie die Autorität dem Standardwert des App-Pakets, wie im obigen Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="396c9-130">Specify a valid absolute URI including the scheme and authority, or just let the authority default to the app's package as in the example above.</span></span>

<span data-ttu-id="396c9-131">Beachten Sie, wie auf die Beispielschemen-URIs ("`ms-appx` "oder" `ms-appx-web`") folgt, denen "`://`" folgt, das einem absoluten Pfad folgt.</span><span class="sxs-lookup"><span data-stu-id="396c9-131">Notice how in these example URIs the scheme ("`ms-appx`" or "`ms-appx-web`") is followed by "`://`" which is followed by an absolute path.</span></span> <span data-ttu-id="396c9-132">In einem absoluten Pfad, bewirkt das führende "`/`", das der Pfad aus dem Stammverzeichnis des Pakets interpretiert wird.</span><span class="sxs-lookup"><span data-stu-id="396c9-132">In an absolute path, the leading "`/`" causes the path to be interpreted from the root of the package.</span></span>

<span data-ttu-id="396c9-133">**Hinweis:** Die `ms-resource` URI-Schemen (für [Zeichenfolgenressourcen](localize-strings-ui-manifest.md)) und `ms-appx(-web)` (für Bilder und andere Ressourcen) führen einen automatischen Qualifiziererabgleich aus, um die Ressource zu suchen, die für den aktuellen Kontext am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="396c9-133">**Note** The `ms-resource` (for [string resources](localize-strings-ui-manifest.md)) and `ms-appx(-web)` (for images and other assets) URI schemes perform automatic qualifier matching to find the resource that's most appropriate for the current context.</span></span> <span data-ttu-id="396c9-134">Das `ms-appdata`URI-Schema (das zum Laden von App-Daten verwendet wird) führt keinen automatischen Abgleich durch, Sie können allerdings auf den Inhalt des [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.QualifierValues) reagieren und die entsprechenden Ressourcen explizit von App-Daten mit ihrem gesamten physischen Dateinamen in der URI verwenden.</span><span class="sxs-lookup"><span data-stu-id="396c9-134">The `ms-appdata` URI scheme (which is used to load app data) does not perform any such automatic matching, but you can respond to the contents of [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.QualifierValues) and explicitly load the appropriate assets from app data using their full physical file name in the URI.</span></span> <span data-ttu-id="396c9-135">Weitere Informationen zu Anwendungsdaten finden Sie unter [Speichern und Abrufen von Einstellungen und anderen App-Daten](../design/app-settings/store-and-retrieve-app-data.md).</span><span class="sxs-lookup"><span data-stu-id="396c9-135">For info about app data, see [Store and retrieve settings and other app data](../design/app-settings/store-and-retrieve-app-data.md).</span></span> <span data-ttu-id="396c9-136">Web-URI-Schemen (z.B. `http`, `https`  und `ftp`) führen keinen automatischen Abgleich durch.</span><span class="sxs-lookup"><span data-stu-id="396c9-136">Web URI schemes (for example, `http`, `https`, and `ftp`) do not perform automatic matching, either.</span></span> <span data-ttu-id="396c9-137">Informationen darüber, was Sie in diesem Fall tun sollten, finden Sie unter [Hosting and loading images in the cloud](../design/shell/tiles-and-notifications/tile-toast-language-scale-contrast.md#hosting-and-loading-images-in-the-cloud).</span><span class="sxs-lookup"><span data-stu-id="396c9-137">For info about what to do in that case, see [Hosting and loading images in the cloud](../design/shell/tiles-and-notifications/tile-toast-language-scale-contrast.md#hosting-and-loading-images-in-the-cloud).</span></span>

<span data-ttu-id="396c9-138">Absolute Pfade sind eine gute Wahl, wenn die Dateien dort bleiben, wo sie sich in der Projektstruktur befinden.</span><span class="sxs-lookup"><span data-stu-id="396c9-138">Absolute paths are a good choice if your image files remain where they are in the project structure.</span></span> <span data-ttu-id="396c9-139">Wenn Sie eine Bilddatei verschieben möchten, Sie allerdings sehr genau darauf achten möchten, dass sie in der gleichen Position relativ zu der verweisenden XAML-Markup-Datei bleibt, können Sie anstelle eines absoluten Pfads einen Pfad verwenden, der relativ zur enthaltenden Markup-Datei existiert.</span><span class="sxs-lookup"><span data-stu-id="396c9-139">If you want to be able to move an image file, but you're careful that it remains in the same location relative to its referencing XAML markup file, then instead of an absolute path you might want to use a path that's relative to the containing markup file.</span></span> <span data-ttu-id="396c9-140">Wenn Sie dies tun, brauchen Sie kein URI-Schema.</span><span class="sxs-lookup"><span data-stu-id="396c9-140">If you do that, then you needn't use a URI scheme.</span></span> <span data-ttu-id="396c9-141">Sie profitieren in diesem Fall auch weiterhin vom automatischen Qualifiziererabgleich, jedoch nur deshalb, weil Sie den relativen Pfad im XAML-Markup verwenden.</span><span class="sxs-lookup"><span data-stu-id="396c9-141">You will still benefit from automatic qualifier matching in this case, but only because you are using the relative path in XAML markup.</span></span>

```xaml
<Image Source="Assets/Images/logo.png"/>
```

<span data-ttu-id="396c9-142">Siehe ebenfalls [Kachel- und Popupunterstützung für Sprache, Skalierung und hohen Kontrast](../design/shell/tiles-and-notifications/tile-toast-language-scale-contrast.md).</span><span class="sxs-lookup"><span data-stu-id="396c9-142">Also see [Tile and toast support for language, scale, and high contrast](../design/shell/tiles-and-notifications/tile-toast-language-scale-contrast.md).</span></span>

## <a name="qualify-an-image-resource-for-targetsize"></a><span data-ttu-id="396c9-143">Qualifizieren einer Bildressource als Zielgröße</span><span class="sxs-lookup"><span data-stu-id="396c9-143">Qualify an image resource for targetsize</span></span>
<span data-ttu-id="396c9-144">Sie können die `scale` und `targetsize`-Qualifizierer auf verschiedenen Varianten der gleichen Bildressource verwenden. Sie können diese allerdings nicht gleichzeitig auf einer einzelnen Variante einer Ressource verwenden.</span><span class="sxs-lookup"><span data-stu-id="396c9-144">You can use the `scale` and `targetsize` qualifiers on different variants of the same image resource; but you can't use them both on a single variant of a resource.</span></span> <span data-ttu-id="396c9-145">Es muss ebenfalls mindestens eine Variante ohne `TargetSize`-Qualifizierer definiert sein.</span><span class="sxs-lookup"><span data-stu-id="396c9-145">Also, you need to define at least one variant without a `TargetSize` qualifier.</span></span> <span data-ttu-id="396c9-146">Diese Variante muss entweder einen Wert für `scale` definieren oder ihn standardmäßig auf `scale-100` lassen.</span><span class="sxs-lookup"><span data-stu-id="396c9-146">That variant must either define a value for `scale`, or let it default to `scale-100`.</span></span> <span data-ttu-id="396c9-147">Diese beiden Varianten der `/Assets/Square44x44Logo.png`-Ressource sind ebenfalls gültig.</span><span class="sxs-lookup"><span data-stu-id="396c9-147">So, these two variants of the `/Assets/Square44x44Logo.png` resource are valid.</span></span>

```
\Assets\Square44x44Logo.scale-200.png
\Assets\Square44x44Logo.targetsize-24.png
```

<span data-ttu-id="396c9-148">Und diese zwei Varianten sind gültig.</span><span class="sxs-lookup"><span data-stu-id="396c9-148">And these two variants are valid.</span></span> 

```
\Assets\Square44x44Logo.png // defaults to scale-100
\Assets\Square44x44Logo.targetsize-24.png
```

<span data-ttu-id="396c9-149">Diese Variante ist allerdings nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="396c9-149">But this variant is not valid.</span></span>

```
\Assets\Square44x44Logo.scale-200_targetsize-24.png
```

## <a name="refer-to-an-image-file-from-your-app-package-manifest"></a><span data-ttu-id="396c9-150">Verweisen auf eine Bilddatei aus Ihrem App-Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="396c9-150">Refer to an image file from your app package manifest</span></span>
<span data-ttu-id="396c9-151">Wenn Sie Ordner und/oder Dateien wie in einem der obigen Beispiele des vorherigen Abschnitts benannt haben, erhalten Sie eine einzelne Symbolbildressource und der Anzeigename (als relativer Pfad) lautet `Assets\Square44x44Logo.png`.</span><span class="sxs-lookup"><span data-stu-id="396c9-151">If you name folders and/or files as in either of the two valid examples in the previous section, then you have a single app icon image resource and its name (as a relative path) is `Assets\Square44x44Logo.png`.</span></span> <span data-ttu-id="396c9-152">Verweisen Sie in Ihrem App-Paketmanifest einfach auf die Ressource nach Namen.</span><span class="sxs-lookup"><span data-stu-id="396c9-152">In your app package manifest, simply refer to the resource by name.</span></span> <span data-ttu-id="396c9-153">Es ist kein URI-Schema notwendig.</span><span class="sxs-lookup"><span data-stu-id="396c9-153">There's no need to use any URI scheme.</span></span>

![Ressource hinzufügen, Englisch](images/app-icon.png)

<span data-ttu-id="396c9-155">Dies ist alles, was, die Sie tun müssen. Das Betriebssystem führt einen automatischen Qualifiziererabgleich aus, um die Ressource zu suchen, die für den aktuellen Kontext am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="396c9-155">That's all you need to do, and the OS will perform automatic qualifier matching to find the resource that's most appropriate for the current context.</span></span> <span data-ttu-id="396c9-156">Sie finden unter [Localizable Manifest Elemente](/uwp/schemas/appxpackage/uapmanifestschema/localizable-manifest-items-win10?branch=live) eine Liste aller Elemente im App-Paketmanifest, die Sie lokalisieren oder anderweitig auf diese Weise qualifizieren können.</span><span class="sxs-lookup"><span data-stu-id="396c9-156">For a list of all items in the app package manifest that you can localize or otherwise qualify in this way, see [Localizable manifest items](/uwp/schemas/appxpackage/uapmanifestschema/localizable-manifest-items-win10?branch=live).</span></span>

## <a name="qualify-an-image-resource-for-layoutdirection"></a><span data-ttu-id="396c9-157">Qualifizieren einer Bildressource als Layoutrichtung</span><span class="sxs-lookup"><span data-stu-id="396c9-157">Qualify an image resource for layoutdirection</span></span>
<span data-ttu-id="396c9-158">Weitere Informationen finden Sie unter [Spiegeln von Bildern](../design/globalizing/adjust-layout-and-fonts--and-support-rtl.md#mirroring-images).</span><span class="sxs-lookup"><span data-stu-id="396c9-158">See [Mirroring images](../design/globalizing/adjust-layout-and-fonts--and-support-rtl.md#mirroring-images).</span></span>

## <a name="load-an-image-for-a-specific-language-or-other-context"></a><span data-ttu-id="396c9-159">Laden eines Bilds für eine bestimmte Sprache oder einen anderen Kontext</span><span class="sxs-lookup"><span data-stu-id="396c9-159">Load an image for a specific language or other context</span></span>
<span data-ttu-id="396c9-160">Weitere Informationen zum Wertversprechen durch Lokalisierung Ihrer App finden Sie unter [Globalisierung und Lokalisierung](../design/globalizing/globalizing-portal.md).</span><span class="sxs-lookup"><span data-stu-id="396c9-160">For more info about the value proposition of localizing your app, see [Globalization and localization](../design/globalizing/globalizing-portal.md).</span></span>

<span data-ttu-id="396c9-161">Der standardmäßige [**ResourceContext**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live) (abgerufen über [**ResourceContext.GetForCurrentView**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.GetForCurrentView)) enthält einen Qualifiziererwert für jeden Qualifizierernamen, der den standardmäßigen Laufzeitkontext darstellt (also die Einstellungen für den aktuellen Benutzer und Computer).</span><span class="sxs-lookup"><span data-stu-id="396c9-161">The default [**ResourceContext**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live) (obtained from [**ResourceContext.GetForCurrentView**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.GetForCurrentView)) contains a qualifier value for each qualifier name, representing the default runtime context (in other words, the settings for the current user and machine).</span></span> <span data-ttu-id="396c9-162">Bilddateien werden abgeglichen&mdash;basierend auf den Qualifizierern in ihren Namen&mdash;und anhand der Qualifiziererwerte in diesem Laufzeitkontext.</span><span class="sxs-lookup"><span data-stu-id="396c9-162">Image files are matched&mdash;based on the qualifiers in their names&mdash;against the qualifier values in that runtime context.</span></span>

<span data-ttu-id="396c9-163">Sie können die Systemeinstellungen Ihrer App außer Kraft setzen und explizit die Sprache, Skalierung oder andere Qualifiziererwerte festlegen, wenn ein übereinstimmendes Bild geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="396c9-163">But there might be times when you want your app to override the system settings and be explicit about the language, scale, or other qualifier value to use when looking for a matching image to load.</span></span> <span data-ttu-id="396c9-164">Sie können z.B. steuern, wann und welche Bilder mit hohem Kontrast geladen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="396c9-164">For example, you might want to control exactly when and which high contrast images are loaded.</span></span>

<span data-ttu-id="396c9-165">Sie können hierzu einen neuen **ResourceContext** erstellen (anstelle des Standardmäßigen), die Werte überschreiben und das Kontextobjekt anschließend in Ihren Suchvorgängen verwenden.</span><span class="sxs-lookup"><span data-stu-id="396c9-165">You can do that by constructing a new **ResourceContext** (instead of using the default one), overriding its values, and then using that context object in your image lookups.</span></span>

```csharp
var resourceContext = new Windows.ApplicationModel.Resources.Core.ResourceContext(); // not using ResourceContext.GetForCurrentView 
resourceContext.QualifierValues["Contrast"] = "high";
var namedResource = Windows.ApplicationModel.Resources.Core.ResourceManager.Current.MainResourceMap[@"Files/Assets/Logo.png"];
var resourceCandidate = namedResource.Resolve(resourceContext);
var imageFileStream = resourceCandidate.GetValueAsStreamAsync().GetResults();
var bitmapImage = new Windows.UI.Xaml.Media.Imaging.BitmapImage();
bitmapImage.SetSourceAsync(imageFileStream);
this.myXAMLImageElement.Source = bitmapImage;
```

<span data-ttu-id="396c9-166">Um den gleichen Effekt auf globaler Ebene zu erzielen, *können* Sie die Qualifiziererwerte im standardmäßigen **ResourceContext** außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="396c9-166">For the same effect at a global level, you *can* override the qualifier values in the default **ResourceContext**.</span></span> <span data-ttu-id="396c9-167">Wir empfehlen, stattdessen [**ResourceContext.SetGlobalQualifierValue**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.setglobalqualifiervalue?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_) aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="396c9-167">But instead we advise you to call [**ResourceContext.SetGlobalQualifierValue**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.setglobalqualifiervalue?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_).</span></span> <span data-ttu-id="396c9-168">Sie legen die Werte nur einmal mit einem Aufruf von **SetGlobalQualifierValue** fest und diese Werte sind auf dem standardmäßigen **ResourceContext** jedes Mal gültig, wenn Sie ihn für Suchvorgänge verwenden.</span><span class="sxs-lookup"><span data-stu-id="396c9-168">You set values one time with a call to **SetGlobalQualifierValue** and then those values are in effect on the default **ResourceContext** each time you use it for lookups.</span></span> <span data-ttu-id="396c9-169">Standardmäßig verwendet die [**ResourceManager**](/uwp/api/windows.applicationmodel.resources.core.resourcemanager?branch=live)-Klasse den standardmäßigen **ResourceContext**.</span><span class="sxs-lookup"><span data-stu-id="396c9-169">By default, the [**ResourceManager**](/uwp/api/windows.applicationmodel.resources.core.resourcemanager?branch=live) class uses the default **ResourceContext**.</span></span>

```csharp
Windows.ApplicationModel.Resources.Core.ResourceContext.SetGlobalQualifierValue("Contrast", "high");
var namedResource = Windows.ApplicationModel.Resources.Core.ResourceManager.Current.MainResourceMap[@"Files/Assets/Logo.png"];
this.myXAMLImageElement.Source = new Windows.UI.Xaml.Media.Imaging.BitmapImage(namedResource.Uri);
```

## <a name="updating-images-in-response-to-qualifier-value-change-events"></a><span data-ttu-id="396c9-170">Aktualisieren von Bildern als Antwort auf Änderungsereignisse im Qualifiziererwert</span><span class="sxs-lookup"><span data-stu-id="396c9-170">Updating images in response to qualifier value change events</span></span>
<span data-ttu-id="396c9-171">Die aktive App kann auf Änderungen in den Systemeinstellungen reagieren, die die Qualifiziererwerte im standardmäßigen Ressourcekontext betreffen.</span><span class="sxs-lookup"><span data-stu-id="396c9-171">Your running app can respond to changes in system settings that affect the qualifier values in the default resource context.</span></span> <span data-ttu-id="396c9-172">Die folgenden Systemeinstellungen rufen ein [**"MapChanged"**](/uwp/api/windows.foundation.collections.iobservablemap-2.mapchanged?branch=live)-Ereignis auf [**ResourceContext.QualifierValues**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.QualifierValues) auf.</span><span class="sxs-lookup"><span data-stu-id="396c9-172">Any of these system settings invokes the [**MapChanged**](/uwp/api/windows.foundation.collections.iobservablemap-2.mapchanged?branch=live) event on [**ResourceContext.QualifierValues**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.QualifierValues).</span></span>

<span data-ttu-id="396c9-173">Als Reaktion auf dieses Ereignis können Sie Ihre Bilder mithilfe des standardmäßigen **ResourceContext** aktualisieren, den der [**ResourceManager**](/uwp/api/windows.applicationmodel.resources.core.resourcemanager?branch=live) standardmäßig verwendet.</span><span class="sxs-lookup"><span data-stu-id="396c9-173">In response to this event, you can reload your images with the help of the default **ResourceContext**, which [**ResourceManager**](/uwp/api/windows.applicationmodel.resources.core.resourcemanager?branch=live) uses by default.</span></span>

```csharp
public MainPage()
{
    this.InitializeComponent();

    ...

    // Subscribe to the event that's raised when a qualifier value changes.
    var qualifierValues = Windows.ApplicationModel.Resources.Core.ResourceContext.GetForCurrentView().QualifierValues;
    qualifierValues.MapChanged += new Windows.Foundation.Collections.MapChangedEventHandler<string, string>(QualifierValues_MapChanged);
}

private async void QualifierValues_MapChanged(IObservableMap<string, string> sender, IMapChangedEventArgs<string> @event)
{
    var dispatcher = this.myImageXAMLElement.Dispatcher;
    if (dispatcher.HasThreadAccess)
    {
        this.RefreshUIImages();
    }
    else
    {
        await dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, () => this.RefreshUIImages());
    }
}

private void RefreshUIImages()
{
    var namedResource = Windows.ApplicationModel.Resources.Core.ResourceManager.Current.MainResourceMap[@"Files/Assets/Logo.png"];
    this.myImageXAMLElement.Source = new Windows.UI.Xaml.Media.Imaging.BitmapImage(namedResource.Uri);
}
```

## <a name="important-apis"></a><span data-ttu-id="396c9-174">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="396c9-174">Important APIs</span></span>
* [<span data-ttu-id="396c9-175">ResourceContext</span><span class="sxs-lookup"><span data-stu-id="396c9-175">ResourceContext</span></span>](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live)
* [<span data-ttu-id="396c9-176">ResourceContext.SetGlobalQualifierValue</span><span class="sxs-lookup"><span data-stu-id="396c9-176">ResourceContext.SetGlobalQualifierValue</span></span>](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.setglobalqualifiervalue?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_)
* [<span data-ttu-id="396c9-177">MapChanged</span><span class="sxs-lookup"><span data-stu-id="396c9-177">MapChanged</span></span>](/uwp/api/windows.foundation.collections.iobservablemap-2.mapchanged?branch=live)

## <a name="related-topics"></a><span data-ttu-id="396c9-178">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="396c9-178">Related topics</span></span>
* [<span data-ttu-id="396c9-179">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und anderen</span><span class="sxs-lookup"><span data-stu-id="396c9-179">Tailor your resources for language, scale, and other qualifiers</span></span>](tailor-resources-lang-scale-contrast.md)
* [<span data-ttu-id="396c9-180">Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App</span><span class="sxs-lookup"><span data-stu-id="396c9-180">Localize strings in your UI and app package manifest</span></span>](localize-strings-ui-manifest.md)
* [<span data-ttu-id="396c9-181">Speichern und Abrufen von Einstellungen und anderen App-Daten</span><span class="sxs-lookup"><span data-stu-id="396c9-181">Store and retrieve settings and other app data</span></span>](../design/app-settings/store-and-retrieve-app-data.md)
* [<span data-ttu-id="396c9-182">Kachel- und Popupunterstützung für die Sprache, den Skalierungsfaktor für die Anzeige, das Design und den hohen Kontrastsupport for language, scale, and high contrast</span><span class="sxs-lookup"><span data-stu-id="396c9-182">Tile and toast support for language, scale, and high contrast</span></span>](tile-toast-language-scale-contrast.md)
* [<span data-ttu-id="396c9-183">Lokalisierbare Manifestelemente</span><span class="sxs-lookup"><span data-stu-id="396c9-183">Localizable manifest items</span></span>](/uwp/schemas/appxpackage/uapmanifestschema/localizable-manifest-items-win10?branch=live)
* [<span data-ttu-id="396c9-184">Spiegeln von Bildern</span><span class="sxs-lookup"><span data-stu-id="396c9-184">Mirroring images</span></span>](../design/globalizing/adjust-layout-and-fonts--and-support-rtl.md#mirroring-images)
* [<span data-ttu-id="396c9-185">Globalisierung und Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="396c9-185">Globalization and localization</span></span>](../design/globalizing/globalizing-portal.md)
