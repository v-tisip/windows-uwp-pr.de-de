---
author: stevewhims
Description: "Ihre Kacheln und Popups können Zeichenfolgen und Bilder laden, die speziell auf die Sprache, den Skalierungsfaktor für die Anzeige, das Design, den hohen Kontrast und anderen Laufzeitkontexte angepasst wurden."
title: "Unterstützte Kachel- und Popupbenachrichtigungen für Sprache, Skalierungsfaktor und hohen Kontrast"
template: detail.hbs
ms.author: stwhi
ms.date: 10/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 10aa6ca83e66e413ec3f417ed8c9034342995e54
ms.sourcegitcommit: 165f57223ba69c0b7b71b295d9e0d35ea9a50a27
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2017
---
# <a name="tile-and-toast-notification-support-for-language-scale-and-high-contrast"></a><span data-ttu-id="08749-104">Unterstützte Kachel- und Popupbenachrichtigungen für Sprache, Skalierungsfaktor und hohen Kontrast</span><span class="sxs-lookup"><span data-stu-id="08749-104">Tile and toast notification support for language, scale, and high contrast</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="08749-105">Ihre Kacheln und Popups können Zeichenfolgen und Bilder laden, die speziell auf die Sprache, den [Skalierungsfaktor für die Anzeige](../layout/screen-sizes-and-breakpoints-for-responsive-design.md), das Design, den hohen Kontrast und anderen Laufzeitkontexte angepasst wurden.</span><span class="sxs-lookup"><span data-stu-id="08749-105">Your tiles and toasts can load strings and images tailored for display language, [display scale factor](../layout/screen-sizes-and-breakpoints-for-responsive-design.md), high contrast, and other runtime contexts.</span></span> <span data-ttu-id="08749-106">Hintergrundinformationen zur Verwendung von Qualifizierern in den Namen der Ressourcendateien finden Sie unter [Passen Sie Ihrer Ressourcen der Sprache, Skalierung und anderen Qualifizierern an](how-to-name-resources-by-using-qualifiers.md).</span><span class="sxs-lookup"><span data-stu-id="08749-106">For background on how to use qualifiers in the names of your resource files, see [Tailor your resources for language, scale, and other qualifiers](how-to-name-resources-by-using-qualifiers.md).</span></span>

## <a name="refer-to-a-string-resource-from-a-template"></a><span data-ttu-id="08749-107">Verweisen auf eine Zeichenfolgenressource aus einer Vorlage</span><span class="sxs-lookup"><span data-stu-id="08749-107">Refer to a string resource from a template</span></span>

<span data-ttu-id="08749-108">In der Kachel- oder Popupbenachrichtigungsvorlage können Sie auf eine Ressource mithilfe des `ms-resource`-URI (Uniform Resource Identifier)-Schemas verweisen, gefolgt von einem einfachen Zeichenfolgenressourcen-Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="08749-108">In your tile or toast template, you can refer to a string resource using the `ms-resource` URI (Uniform Resource Identifier) scheme followed by a simple string resource identifier.</span></span> <span data-ttu-id="08749-109">Wenn Sie beispielsweise eine Resources.resx-Datei haben, die einen Ressourceneintrag enthält, deren Name "Farewell" ist, erhalten Sie eine Zeichenfolgenressource mit dem Bezeichner "Farewell".</span><span class="sxs-lookup"><span data-stu-id="08749-109">For example, if you have a Resources.resx file that contains a resource entry whose name is "Farewell", then you have a string resource with the identifier "Farewell".</span></span> <span data-ttu-id="08749-110">Weitere Informationen zu Zeichenfolgenressourcen-Bezeichner und Ressourcendateien (.resw) finden Sie unter [Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App](put-ui-strings-into-resources.md).</span><span class="sxs-lookup"><span data-stu-id="08749-110">For more info on string resource identifiers and Resources Files (.resw), see [Localize strings in your UI and app package manifest](put-ui-strings-into-resources.md).</span></span>

<span data-ttu-id="08749-111">So würde ein Verweis auf den Zeichenfolgenressourcen-Bezeichner "Farewell" im [Text](/uwp/schemas/tiles/tilesschema/element-text?branch=live)körper des Vorlageninhalts mit `ms-resource` aussehen.</span><span class="sxs-lookup"><span data-stu-id="08749-111">This is how a reference to the "Farewell" string resource identifier would look in the [text](/uwp/schemas/tiles/tilesschema/element-text?branch=live) body of your template content, using `ms-resource`.</span></span>

```xml
<text id="1">ms-resource:Farewell</text>
```

<span data-ttu-id="08749-112">Wenn Sie das `ms-resource`-URI-Schema weglassen ist der Textkörper nur ein Zeichenfolgenliteral und *nicht* ein Verweis auf einen Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="08749-112">If you omit the `ms-resource` URI scheme, then the text body is just a string literal, and *not* a reference to an identifier.</span></span>

```xml
<text id="1">Farewell</text>
```

## <a name="refer-to-an-image-resource-from-a-template"></a><span data-ttu-id="08749-113">Verweisen auf eine Bildressource aus einer Vorlage</span><span class="sxs-lookup"><span data-stu-id="08749-113">Refer to an image resource from a template</span></span>

<span data-ttu-id="08749-114">In der Kachel- oder Popupbenachrichtigungsvorlage können Sie auf eine Bildressource mithilfe des `ms-appx`-URI (Uniform Resource Identifier)-Schemas verweisen, gefolgt vom Namen der Bildressource.</span><span class="sxs-lookup"><span data-stu-id="08749-114">In your tile or toast template, you can refer to an image resource using the `ms-appx` URI (Uniform Resource Identifier) scheme followed by the name of the image resource.</span></span> <span data-ttu-id="08749-115">So verweisen Sie ebenfalls auf eine Bildressource im XAML-Markup (Weitere Informationen finden Sie unter [Verweisen auf eine Bildressource in XAML-Markup und Code](image-qualifiers-loc-scale-accessibility.md#reference-an-image-resource-in-xaml-markup-and-code)).</span><span class="sxs-lookup"><span data-stu-id="08749-115">This is the same way that you refer to an image resource in XAML markup (for more details, see [Reference an image resource in XAML markup and code](image-qualifiers-loc-scale-accessibility.md#reference-an-image-resource-in-xaml-markup-and-code)).</span></span>

<span data-ttu-id="08749-116">Sie können z.B. Ordner wie folgt benennen.</span><span class="sxs-lookup"><span data-stu-id="08749-116">For example, you might name folders like this.</span></span>

```
\Assets\Images\contrast-standard\welcome.png
\Assets\Images\contrast-high\welcome.png
```

<span data-ttu-id="08749-117">In diesem Fall erhalten Sie eine einzelne Bildressource und der Anzeigename (als absoluter Pfad) ist `/Assets/Images/welcome.png`.</span><span class="sxs-lookup"><span data-stu-id="08749-117">In that case, you have a single image resource and its name (as an absolute path) is `/Assets/Images/welcome.png`.</span></span> <span data-ttu-id="08749-118">So verwenden Sie diesen Namen in Ihrer Vorlage.</span><span class="sxs-lookup"><span data-stu-id="08749-118">Here’s how you use that name in your template.</span></span>

```xml
<image id="1" src="ms-appx:///Assets/Images/welcome.png"/>
```

<span data-ttu-id="08749-119">Beachten Sie, wie auf die Beispielschema-URI ("`ms-appx`") "`://`" folgt, das einem absoluten Pfad folgt (ein absoluter Pfad beginnt mit "`/`").</span><span class="sxs-lookup"><span data-stu-id="08749-119">Notice how in this example URI the scheme ("`ms-appx`") is followed by "`://`" which is followed by an absolute path (an absolute path begins with "`/`").</span></span>

## <a name="hosting-and-loading-images-in-the-cloud"></a><span data-ttu-id="08749-120">Hosten und Laden von Bildern in der Cloud</span><span class="sxs-lookup"><span data-stu-id="08749-120">Hosting and loading images in the cloud</span></span>

<span data-ttu-id="08749-121">Die `ms-resource` und `ms-appx`-URI-Schemen führen einen automatischen Qualifiziererabgleich aus, um die Ressource zu suchen, die für den aktuellen Kontext am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="08749-121">The `ms-resource` and `ms-appx` URI schemes perform automatic qualifier matching to find the resource that's most appropriate for the current context.</span></span> <span data-ttu-id="08749-122">Web-URI-Schemen (z.B. `http`, `https`  und `ftp`) führen keinen derartigen automatischen Abgleich durch.</span><span class="sxs-lookup"><span data-stu-id="08749-122">Web URI schemes (for example, `http`, `https`, and `ftp`) do not perform any such automatic matching.</span></span>

<span data-ttu-id="08749-123">Fügen Sie stattdessen auf den URI des Bilds eine Abfragezeichenfolge hinzu, die den angeforderten Qualifiziererwert oder die Werte enthält.</span><span class="sxs-lookup"><span data-stu-id="08749-123">Instead, append onto your image's URI a query string describing the requested qualifier value or values.</span></span>

```xml
<image id="1" src="http://www.contoso.com/Assets/Images/welcome.png?ms-lang=en-US"/>
```

<span data-ttu-id="08749-124">Implementieren Sie anschließend in den App-Dienst, der die Bilder enthält, einen HTTP-Handler, der die Abfragezeichenfolge untersucht und verwendet, um ermitteln, welches Bild zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="08749-124">Then, in the app service that provides your images, implement an HTTP handler that inspects and uses the query string to determine which image to return.</span></span>

<span data-ttu-id="08749-125">Auch muss ebenfalls das [**AddImageQuery**](/uwp/schemas/tiles/tilesschema/element-visual?branch=live)-Attribut auf `true` in der [Kachel](/uwp/schemas/tiles/tilesschema/schema-root?branch=live) oder in der [Popup](/uwp/schemas/tiles/toastschema/schema-root?branch=live)-Benachrichtung der XML-Nutzlast gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="08749-125">You also need to set the [**addImageQuery**](/uwp/schemas/tiles/tilesschema/element-visual?branch=live) attribute to `true` in the [tile](/uwp/schemas/tiles/tilesschema/schema-root?branch=live) or [toast](/uwp/schemas/tiles/toastschema/schema-root?branch=live) notification XML payload.</span></span> <span data-ttu-id="08749-126">Das **addImageQuery**-Attribut erscheint in den `visual`, `binding` und `image`-Elementen des Kachel- und Popupschemas.</span><span class="sxs-lookup"><span data-stu-id="08749-126">The **addImageQuery** attribute appears in the `visual`, `binding`, and `image` elements of both the tile and toast schemas.</span></span> <span data-ttu-id="08749-127">Das explizite Festlegen von **AddImageQuery** für ein Element überschreibt einen beliebigen Wert für ein übergeordnetes Element.</span><span class="sxs-lookup"><span data-stu-id="08749-127">Explicitly setting **addImageQuery** on an element overrides any value set on an ancestor.</span></span> <span data-ttu-id="08749-128">Der **addImageQuery**-Wert `true` in einem `image`-Element überschreibt den **addImageQuery**-Wert `false` im übergeordneten `binding`-Element.</span><span class="sxs-lookup"><span data-stu-id="08749-128">For instance, an **addImageQuery** value of `true` in an `image` element overrides an **addImageQuery** of `false` in its parent `binding` element.</span></span>

<span data-ttu-id="08749-129">Hier sind die Abfragezeichenfolgen, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="08749-129">These are the query strings you can use.</span></span>

| <span data-ttu-id="08749-130">Qualifizierer</span><span class="sxs-lookup"><span data-stu-id="08749-130">Qualifier</span></span> | <span data-ttu-id="08749-131">Abfragezeichenfolge</span><span class="sxs-lookup"><span data-stu-id="08749-131">Query string</span></span> | <span data-ttu-id="08749-132">Beispiel</span><span class="sxs-lookup"><span data-stu-id="08749-132">Example</span></span> |
| --------- | ------------ | ------- |
| <span data-ttu-id="08749-133">Skalierung</span><span class="sxs-lookup"><span data-stu-id="08749-133">Scale</span></span> | <span data-ttu-id="08749-134">ms-scale </span><span class="sxs-lookup"><span data-stu-id="08749-134">ms-scale</span></span> | <span data-ttu-id="08749-135">?ms-scale=400 </span><span class="sxs-lookup"><span data-stu-id="08749-135">?ms-scale=400</span></span> |
| <span data-ttu-id="08749-136">Sprache</span><span class="sxs-lookup"><span data-stu-id="08749-136">Language</span></span> | <span data-ttu-id="08749-137">ms-lang </span><span class="sxs-lookup"><span data-stu-id="08749-137">ms-lang</span></span> | <span data-ttu-id="08749-138">?ms-lang=en-US </span><span class="sxs-lookup"><span data-stu-id="08749-138">?ms-lang=en-US</span></span> |
| <span data-ttu-id="08749-139">Kontrast</span><span class="sxs-lookup"><span data-stu-id="08749-139">Contrast</span></span> | <span data-ttu-id="08749-140">ms-contrast </span><span class="sxs-lookup"><span data-stu-id="08749-140">ms-contrast</span></span> | <span data-ttu-id="08749-141">?ms-contrast=high</span><span class="sxs-lookup"><span data-stu-id="08749-141">?ms-contrast=high</span></span> |

<span data-ttu-id="08749-142">Eine Referenztabelle aller möglichen Qualifiziererwerte, die Sie in der Abfragezeichenfolgen verwenden können, finden Sie unter [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues).</span><span class="sxs-lookup"><span data-stu-id="08749-142">For a reference table of all the possible qualifier values that you can use in your query strings, see [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues).</span></span>

## <a name="related-topics"></a><span data-ttu-id="08749-143">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="08749-143">Related topics</span></span>

* [<span data-ttu-id="08749-144">Passen Sie Ihrer Ressourcen der Sprache, Skalierung und anderen Qualifizierern an</span><span class="sxs-lookup"><span data-stu-id="08749-144">Tailor your resources for language, scale, and other qualifiers</span></span>](how-to-name-resources-by-using-qualifiers.md)
* [<span data-ttu-id="08749-145">ResourceContext.QualifierValues</span><span class="sxs-lookup"><span data-stu-id="08749-145">ResourceContext.QualifierValues</span></span>](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues)
* [<span data-ttu-id="08749-146">Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App</span><span class="sxs-lookup"><span data-stu-id="08749-146">Localize strings in your UI and app package manifest</span></span>](put-ui-strings-into-resources.md)
* [<span data-ttu-id="08749-147">Verweisen auf eine Bildressource in XAML-Markup und Code</span><span class="sxs-lookup"><span data-stu-id="08749-147">Reference an image resource in XAML markup and code</span></span>](image-qualifiers-loc-scale-accessibility.md#reference-an-image-resource-in-xaml-markup-and-code)
* [<span data-ttu-id="08749-148">addImageQuery</span><span class="sxs-lookup"><span data-stu-id="08749-148">addImageQuery</span></span>](/uwp/schemas/tiles/tilesschema/element-visual?branch=live)
* [<span data-ttu-id="08749-149">Kachelschema</span><span class="sxs-lookup"><span data-stu-id="08749-149">Tile schema</span></span>](/uwp/schemas/tiles/tilesschema/schema-root?branch=live)
* [<span data-ttu-id="08749-150">Schema für Popups</span><span class="sxs-lookup"><span data-stu-id="08749-150">Toast schema</span></span>](/uwp/schemas/tiles/toastschema/schema-root?branch=live)