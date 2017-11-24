---
author: stevewhims
Description: "Ihre Kacheln und Popups können Zeichenfolgen und Bilder laden, die speziell auf die Sprache, den Skalierungsfaktor für die Anzeige, das Design, den hohen Kontrast und anderen Laufzeitkontexte angepasst wurden."
title: "Kachel- und Toast-Mitteilungsunterstützung für Sprache, Skalierung und hohen Kontrast"
template: detail.hbs
ms.author: stwhi
ms.date: 10/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
localizationpriority: medium
ms.openlocfilehash: 2b294ec2c6b019933547b828d55e7709690bf713
ms.sourcegitcommit: d0c93d734639bd31f264424ae5b6fead903a951d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2017
---
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

# <a name="tile-and-toast-notification-support-for-language-scale-and-high-contrast"></a><span data-ttu-id="d5900-104">Kachel- und Toast-Mitteilungsunterstützung für Sprache, Skalierung und hohen Kontrast</span><span class="sxs-lookup"><span data-stu-id="d5900-104">Tile and toast notification support for language, scale, and high contrast</span></span>

<span data-ttu-id="d5900-105">Ihre Kacheln und Popups können Zeichenfolgen und Bilder laden, die speziell auf die Sprache, den [Skalierungsfaktor für die Anzeige](../layout/screen-sizes-and-breakpoints-for-responsive-design.md), das Design, den hohen Kontrast und anderen Laufzeitkontexte angepasst wurden.</span><span class="sxs-lookup"><span data-stu-id="d5900-105">Your tiles and toasts can load strings and images tailored for display language, [display scale factor](../layout/screen-sizes-and-breakpoints-for-responsive-design.md), high contrast, and other runtime contexts.</span></span> <span data-ttu-id="d5900-106">Hintergrundinformationen zur Verwendung von Qualifizierern in den Namen von Bildressourcendateien finden Sie unter [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und andere Eigenschaften](tailor-resources-lang-scale-contrast.md) und [Größentabellen für Ressourcen](../controls-and-patterns/tiles-and-notifications-app-assets.md#asset-size-tables).</span><span class="sxs-lookup"><span data-stu-id="d5900-106">For background on how to use qualifiers in the names of your resource files, see [Tailor your resources for language, scale, and other qualifiers](tailor-resources-lang-scale-contrast.md) and [Asset size tables](../controls-and-patterns/tiles-and-notifications-app-assets.md#asset-size-tables).</span></span>

<span data-ttu-id="d5900-107">Weitere Informationen zu einer Werterhöhung Ihrer App durch Lokalisierung finden Sie unter [Globalisierung und Lokalisierung](../globalizing/globalizing-portal.md).</span><span class="sxs-lookup"><span data-stu-id="d5900-107">For more info about the value proposition of localizing your app, see [Globalization and localization](../globalizing/globalizing-portal.md).</span></span>

## <a name="refer-to-a-string-resource-from-a-template"></a><span data-ttu-id="d5900-108">Referenzieren eines Bezeichners für Zeichenfolgenressourcen in einer Vorlage</span><span class="sxs-lookup"><span data-stu-id="d5900-108">Refer to a string resource from a template</span></span>

<span data-ttu-id="d5900-109">In Ihrer Kachel- oder Toastvorlage können Sie auf eine Zeichenfolgenressource verweisen, indem Sie das Uniform Resource Identifier (URI)-Schema `ms-resource` verwenden, gefolgt von einem einfachen Bezeichner für eine Zeichenfolgenressource.</span><span class="sxs-lookup"><span data-stu-id="d5900-109">In your tile or toast template, you can refer to a string resource using the `ms-resource` URI (Uniform Resource Identifier) scheme followed by a simple string resource identifier.</span></span> <span data-ttu-id="d5900-110">Wenn Sie beispielsweise eine Resources.resx-Datei haben, die einen Ressourceneintrag enthält, deren Name "Farewell" ist, erhalten Sie eine Zeichenfolgenressource mit dem Bezeichner "Farewell".</span><span class="sxs-lookup"><span data-stu-id="d5900-110">For example, if you have a Resources.resx file that contains a resource entry whose name is "Farewell", then you have a string resource with the identifier "Farewell".</span></span> <span data-ttu-id="d5900-111">Weitere Informationen zu Zeichenfolgenressourcen-Bezeichner und Ressourcendateien (.resw) finden Sie unter [Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App](localize-strings-ui-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="d5900-111">For more info on string resource identifiers and Resources Files (.resw), see [Localize strings in your UI and app package manifest](localize-strings-ui-manifest.md).</span></span>

<span data-ttu-id="d5900-112">So würde ein Verweis auf den Zeichenfolgenressourcen-Bezeichner "Farewell" im [Text](/uwp/schemas/tiles/tilesschema/element-text?branch=live)körper des Vorlageninhalts mit `ms-resource` aussehen.</span><span class="sxs-lookup"><span data-stu-id="d5900-112">This is how a reference to the "Farewell" string resource identifier would look in the [text](/uwp/schemas/tiles/tilesschema/element-text?branch=live) body of your template content, using `ms-resource`.</span></span>

```xml
<text id="1">ms-resource:Farewell</text>
```

<span data-ttu-id="d5900-113">Wenn Sie das `ms-resource`-URI-Schema weglassen ist der Textkörper nur ein Zeichenfolgenliteral und *nicht* ein Verweis auf einen Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="d5900-113">If you omit the `ms-resource` URI scheme, then the text body is just a string literal, and *not* a reference to an identifier.</span></span>

```xml
<text id="1">Farewell</text>
```

## <a name="refer-to-an-image-resource-from-a-template"></a><span data-ttu-id="d5900-114">Verweisen auf eine Bildressource aus einer Vorlage</span><span class="sxs-lookup"><span data-stu-id="d5900-114">Refer to an image resource from a template</span></span>

<span data-ttu-id="d5900-115">In der Kachel- oder Popupbenachrichtigungsvorlage können Sie auf eine Bildressource mithilfe des `ms-appx`-URI (Uniform Resource Identifier)-Schemas verweisen, gefolgt vom Namen der Bildressource.</span><span class="sxs-lookup"><span data-stu-id="d5900-115">In your tile or toast template, you can refer to an image resource using the `ms-appx` URI (Uniform Resource Identifier) scheme followed by the name of the image resource.</span></span> <span data-ttu-id="d5900-116">Dies entspricht der Art und Weise, in der Sie in XAML-Markup eine Bildressource referenzieren (weitere Informationen finden Sie unter [Referenzieren eines Bilds oder eines anderen Elements in XAML-Markup und Code](images-tailored-for-scale-theme-contrast.md#reference-an-image-or-other-asset-from-xaml-markup-and-code)).</span><span class="sxs-lookup"><span data-stu-id="d5900-116">This is the same way that you refer to an image resource in XAML markup (for more details, see [Reference an image or other asset from XAML markup and code](images-tailored-for-scale-theme-contrast.md#reference-an-image-or-other-asset-from-xaml-markup-and-code)).</span></span>

<span data-ttu-id="d5900-117">Beispielsweise können Sie Ordner wie folgt benennen:</span><span class="sxs-lookup"><span data-stu-id="d5900-117">For example, you might name folders like this.</span></span>

```
\Assets\Images\contrast-standard\welcome.png
\Assets\Images\contrast-high\welcome.png
```

<span data-ttu-id="d5900-118">In diesem Fall erhalten Sie eine einzelne Bildressource und der Anzeigename (als absoluter Pfad) ist `/Assets/Images/welcome.png`.</span><span class="sxs-lookup"><span data-stu-id="d5900-118">In that case, you have a single image resource and its name (as an absolute path) is `/Assets/Images/welcome.png`.</span></span> <span data-ttu-id="d5900-119">So verwenden Sie diesen Namen in Ihrer Vorlage.</span><span class="sxs-lookup"><span data-stu-id="d5900-119">Here’s how you use that name in your template.</span></span>

```xml
<image id="1" src="ms-appx:///Assets/Images/welcome.png"/>
```

<span data-ttu-id="d5900-120">Beachten Sie, wie auf die Beispielschema-URI ("`ms-appx`") "`://`" folgt, das einem absoluten Pfad folgt (ein absoluter Pfad beginnt mit "`/`").</span><span class="sxs-lookup"><span data-stu-id="d5900-120">Notice how in this example URI the scheme ("`ms-appx`") is followed by "`://`" which is followed by an absolute path (an absolute path begins with "`/`").</span></span>

## <a name="hosting-and-loading-images-in-the-cloud"></a><span data-ttu-id="d5900-121">Hosten und Laden von Bildern in der Cloud</span><span class="sxs-lookup"><span data-stu-id="d5900-121">Hosting and loading images in the cloud</span></span>

<span data-ttu-id="d5900-122">Die `ms-resource` und `ms-appx`-URI-Schemen führen einen automatischen Qualifiziererabgleich aus, um die Ressource zu suchen, die für den aktuellen Kontext am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="d5900-122">The `ms-resource` and `ms-appx` URI schemes perform automatic qualifier matching to find the resource that's most appropriate for the current context.</span></span> <span data-ttu-id="d5900-123">Web-URI-Schemen (z.B. `http`, `https`  und `ftp`) führen keinen derartigen automatischen Abgleich durch.</span><span class="sxs-lookup"><span data-stu-id="d5900-123">Web URI schemes (for example, `http`, `https`, and `ftp`) do not perform any such automatic matching.</span></span>

<span data-ttu-id="d5900-124">Fügen Sie stattdessen auf den URI des Bilds eine Abfragezeichenfolge hinzu, die den angeforderten Qualifiziererwert oder die Werte enthält.</span><span class="sxs-lookup"><span data-stu-id="d5900-124">Instead, append onto your image's URI a query string describing the requested qualifier value or values.</span></span>

```xml
<image id="1" src="http://www.contoso.com/Assets/Images/welcome.png?ms-lang=en-US"/>
```

<span data-ttu-id="d5900-125">Implementieren Sie anschließend in den App-Dienst, der die Bilder enthält, einen HTTP-Handler, der die Abfragezeichenfolge untersucht und verwendet, um ermitteln, welches Bild zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d5900-125">Then, in the app service that provides your images, implement an HTTP handler that inspects and uses the query string to determine which image to return.</span></span>

<span data-ttu-id="d5900-126">Auch muss ebenfalls das [**AddImageQuery**](/uwp/schemas/tiles/tilesschema/element-visual?branch=live)-Attribut auf `true` in der [Kachel](/uwp/schemas/tiles/tilesschema/schema-root?branch=live) oder in der [Popup](/uwp/schemas/tiles/toastschema/schema-root?branch=live)-Benachrichtung der XML-Nutzlast gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="d5900-126">You also need to set the [**addImageQuery**](/uwp/schemas/tiles/tilesschema/element-visual?branch=live) attribute to `true` in the [tile](/uwp/schemas/tiles/tilesschema/schema-root?branch=live) or [toast](/uwp/schemas/tiles/toastschema/schema-root?branch=live) notification XML payload.</span></span> <span data-ttu-id="d5900-127">Das **addImageQuery**-Attribut erscheint in den `visual`, `binding` und `image`-Elementen des Kachel- und Popupschemas.</span><span class="sxs-lookup"><span data-stu-id="d5900-127">The **addImageQuery** attribute appears in the `visual`, `binding`, and `image` elements of both the tile and toast schemas.</span></span> <span data-ttu-id="d5900-128">Das explizite Festlegen von **AddImageQuery** für ein Element überschreibt einen beliebigen Wert für ein übergeordnetes Element.</span><span class="sxs-lookup"><span data-stu-id="d5900-128">Explicitly setting **addImageQuery** on an element overrides any value set on an ancestor.</span></span> <span data-ttu-id="d5900-129">Der **addImageQuery**-Wert `true` in einem `image`-Element überschreibt den **addImageQuery**-Wert `false` im übergeordneten `binding`-Element.</span><span class="sxs-lookup"><span data-stu-id="d5900-129">For instance, an **addImageQuery** value of `true` in an `image` element overrides an **addImageQuery** of `false` in its parent `binding` element.</span></span>

<span data-ttu-id="d5900-130">Hier sind die Abfragezeichenfolgen, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d5900-130">These are the query strings you can use.</span></span>

| <span data-ttu-id="d5900-131">Qualifizierer</span><span class="sxs-lookup"><span data-stu-id="d5900-131">Qualifier</span></span> | <span data-ttu-id="d5900-132">Abfragezeichenfolge</span><span class="sxs-lookup"><span data-stu-id="d5900-132">Query string</span></span> | <span data-ttu-id="d5900-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d5900-133">Example</span></span> |
| --------- | ------------ | ------- |
| <span data-ttu-id="d5900-134">Skalierung</span><span class="sxs-lookup"><span data-stu-id="d5900-134">Scale</span></span> | <span data-ttu-id="d5900-135">ms-scale </span><span class="sxs-lookup"><span data-stu-id="d5900-135">ms-scale</span></span> | <span data-ttu-id="d5900-136">?ms-scale=400 </span><span class="sxs-lookup"><span data-stu-id="d5900-136">?ms-scale=400</span></span> |
| <span data-ttu-id="d5900-137">Sprache</span><span class="sxs-lookup"><span data-stu-id="d5900-137">Language</span></span> | <span data-ttu-id="d5900-138">ms-lang </span><span class="sxs-lookup"><span data-stu-id="d5900-138">ms-lang</span></span> | <span data-ttu-id="d5900-139">?ms-lang=en-US </span><span class="sxs-lookup"><span data-stu-id="d5900-139">?ms-lang=en-US</span></span> |
| <span data-ttu-id="d5900-140">Kontrast</span><span class="sxs-lookup"><span data-stu-id="d5900-140">Contrast</span></span> | <span data-ttu-id="d5900-141">ms-contrast </span><span class="sxs-lookup"><span data-stu-id="d5900-141">ms-contrast</span></span> | <span data-ttu-id="d5900-142">?ms-contrast=high</span><span class="sxs-lookup"><span data-stu-id="d5900-142">?ms-contrast=high</span></span> |

<span data-ttu-id="d5900-143">Eine Referenztabelle aller möglichen Qualifiziererwerte, die Sie in der Abfragezeichenfolgen verwenden können, finden Sie unter [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues).</span><span class="sxs-lookup"><span data-stu-id="d5900-143">For a reference table of all the possible qualifier values that you can use in your query strings, see [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues).</span></span>

## <a name="related-topics"></a><span data-ttu-id="d5900-144">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d5900-144">Related topics</span></span>

* [<span data-ttu-id="d5900-145">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und anderen</span><span class="sxs-lookup"><span data-stu-id="d5900-145">Tailor your resources for language, scale, and other qualifiers</span></span>](tailor-resources-lang-scale-contrast.md)
* [<span data-ttu-id="d5900-146">Richtlinien für die Ressourcen für Kacheln und Symbole</span><span class="sxs-lookup"><span data-stu-id="d5900-146">Guidelines for tile and icon assets</span></span>](../controls-and-patterns/tiles-and-notifications-app-assets.md)
* [<span data-ttu-id="d5900-147">ResourceContext.QualifierValues</span><span class="sxs-lookup"><span data-stu-id="d5900-147">ResourceContext.QualifierValues</span></span>](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues)
* [<span data-ttu-id="d5900-148">Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im App-Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="d5900-148">Localize strings in your UI and app package manifest</span></span>](localize-strings-ui-manifest.md)
* [<span data-ttu-id="d5900-149">Referenzieren eines Bilds oder eines anderen Elements in XAML-Markup und Code</span><span class="sxs-lookup"><span data-stu-id="d5900-149">Reference an image or other asset from XAML markup and code</span></span>](images-tailored-for-scale-theme-contrast.md#reference-an-image-or-other-asset-from-xaml-markup-and-code)
* [<span data-ttu-id="d5900-150">addImageQuery</span><span class="sxs-lookup"><span data-stu-id="d5900-150">addImageQuery</span></span>](/uwp/schemas/tiles/tilesschema/element-visual?branch=live)
* [<span data-ttu-id="d5900-151">Kachelschema</span><span class="sxs-lookup"><span data-stu-id="d5900-151">Tile schema</span></span>](/uwp/schemas/tiles/tilesschema/schema-root?branch=live)
* [<span data-ttu-id="d5900-152">Toastschema</span><span class="sxs-lookup"><span data-stu-id="d5900-152">Toast schema</span></span>](/uwp/schemas/tiles/toastschema/schema-root?branch=live)