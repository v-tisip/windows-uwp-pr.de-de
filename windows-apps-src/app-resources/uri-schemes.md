---
Description: There are several URI (Uniform Resource Identifier) schemes that you can use to refer to files that come from your app's package, your app's data folders, or the cloud. You can also use a URI scheme to refer to strings loaded from your app's Resources Files (.resw).
title: URI-Schemen
template: detail.hbs
ms.date: 10/16/2017
ms.topic: article
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
ms.localizationpriority: medium
ms.openlocfilehash: 345a41a45e28843161e65ecb04f0083f1a71269a
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7855338"
---
# <a name="uri-schemes"></a><span data-ttu-id="2ccae-103">URI-Schemen</span><span class="sxs-lookup"><span data-stu-id="2ccae-103">URI schemes</span></span>

<span data-ttu-id="2ccae-104">Es gibt mehrere URI (Uniform Resource Identifier)-Schemen, die Sie verwenden können, um auf Dateien aus Ihrem App Paket, dem App-Ordner oder der Cloud zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="2ccae-104">There are several URI (Uniform Resource Identifier) schemes that you can use to refer to files that come from your app's package, your app's data folders, or the cloud.</span></span> <span data-ttu-id="2ccae-105">Sie können ebenfalls ein URI-Schema verwenden, um auf Zeichenfolgen, die von der App-Ressourcendateien (.resw) geladen wurden, zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="2ccae-105">You can also use a URI scheme to refer to strings loaded from your app's Resources Files (.resw).</span></span> <span data-ttu-id="2ccae-106">Sie können diese URI-Schemen in Ihrem Code, im XAML-Markup, in Ihrem App-Paketmanifest oder in der Kachel und Popupbenachrichtigungsvorlage verwenden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-106">You can use these URI schemes in your code, in your XAML markup, in your app package manifest, or in your tile and toast notification templates.</span></span>

## <a name="common-features-of-the-uri-schemes"></a><span data-ttu-id="2ccae-107">Allgemeine Features der URI-Schemen</span><span class="sxs-lookup"><span data-stu-id="2ccae-107">Common features of the URI schemes</span></span>

<span data-ttu-id="2ccae-108">Alle in diesem Thema beschriebenen Schemen folgen den typischen URI-Schema-Regeln für die Normalisierung und den Ressourcenabruf.</span><span class="sxs-lookup"><span data-stu-id="2ccae-108">All of the schemes described in this topic follow typical URI scheme rules for normalization and resource retrieval.</span></span> <span data-ttu-id="2ccae-109">Weitere Informationen für die allgemeine Syntax für eine URI finden Sie unter [RFC 3986](http://go.microsoft.com/fwlink/p/?LinkId=263444).</span><span class="sxs-lookup"><span data-stu-id="2ccae-109">See [RFC 3986](http://go.microsoft.com/fwlink/p/?LinkId=263444) for the generic syntax of a URI.</span></span>

<span data-ttu-id="2ccae-110">Bei allen URI-Schemen wird der hierarchische Teil gemäß [RFC 3986](http://go.microsoft.com/fwlink/p/?LinkId=263444) als die Autoritäts- und Pfadkomponenten des URI definiert:</span><span class="sxs-lookup"><span data-stu-id="2ccae-110">All of the URI schemes define the hierarchical part per [RFC 3986](http://go.microsoft.com/fwlink/p/?LinkId=263444) as the authority and path components of the URI.</span></span>

```syntax
URI         = scheme ":" hier-part [ "?" query ] [ "#" fragment ]
hier-part   = "//" authority path-abempty
            / path-absolute
            / path-rootless
            / path-empty
```

<span data-ttu-id="2ccae-111">Dies bedeutet, dass es im Wesentlichen drei Komponenten für einen URI gibt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-111">What this means is that there are essentially three components to a URI.</span></span> <span data-ttu-id="2ccae-112">Unmittelbar nach den Schrägstrichen des URI *Schemas* ist eine Komponente (ggf. leer), die als *authority* bezeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="2ccae-112">Immediately following the two forward slashes of the URI *scheme* is a component (which can be empty) called the *authority*.</span></span> <span data-ttu-id="2ccae-113">Und direkt danach befindet sich *path*.</span><span class="sxs-lookup"><span data-stu-id="2ccae-113">And immediately following that is the *path*.</span></span> <span data-ttu-id="2ccae-114">Als Beispiel: Bei der URI `http://www.contoso.com/welcome.png` ist das Schema "`http://`", die Autorität "`www.contoso.com`" und der Pfad "`/welcome.png`".</span><span class="sxs-lookup"><span data-stu-id="2ccae-114">Taking the URI `http://www.contoso.com/welcome.png` as an example, the scheme is "`http://`", the authority is "`www.contoso.com`", and the path is "`/welcome.png`".</span></span> <span data-ttu-id="2ccae-115">Ein weiteres Beispiel ist die URI `ms-appx:///logo.png`, wobei die Autorität für die Komponenten leer ist und einen Standardwert annimmt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-115">Another example is the URI `ms-appx:///logo.png`, where the authority components is empty and takes a default value.</span></span>

<span data-ttu-id="2ccae-116">Die Fragment-Komponente wird bei der schemenspezifischen Verarbeitung der hier aufgeführten URIs ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-116">The fragment component is ignored by the scheme-specific processing of the URIs mentioned in this topic.</span></span> <span data-ttu-id="2ccae-117">Beim Ressourcenabruf und Vergleich hat die Fragment-Komponente keine Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="2ccae-117">During resource retrieval and comparison, the fragment component has no bearing.</span></span> <span data-ttu-id="2ccae-118">Ebenen über einer bestimmten Implementierung können die Fragment-Komponente jedoch so interpretieren, dass sie eine sekundäre Ressource abruft.</span><span class="sxs-lookup"><span data-stu-id="2ccae-118">However, layers above specific implementation may interpret the fragment to retrieve a secondary resource.</span></span>

<span data-ttu-id="2ccae-119">Der Vergleich findet byteweise nach der Normalisierung aller IRI-Komponenten statt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-119">Comparison occurs byte for byte after normalization of all IRI components.</span></span>

## <a name="case-insensitivity-and-normalization"></a><span data-ttu-id="2ccae-120">Das Ignorieren der Groß-/Kleinschreibung und die Normalisierung</span><span class="sxs-lookup"><span data-stu-id="2ccae-120">Case-insensitivity and normalization</span></span>

<span data-ttu-id="2ccae-121">Alle in diesem Thema beschriebenen URI-Schemen folgen den typischen URI-Regeln (RFC 3986) für die Normalisierung und den Ressourcenabruf für Schemen.</span><span class="sxs-lookup"><span data-stu-id="2ccae-121">All the URI schemes described in this topic follow typical URI rules (RFC 3986) for normalization and resource retrieval for schemes.</span></span> <span data-ttu-id="2ccae-122">Bei der normalisierten Form der URI bleibt die Groß-/Kleinschreibung erhalten, und von nicht reservierten RFC 3986-Zeichen werden die Prozentzeichen entfernt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-122">The normalized form of these URIs maintains case and percent-decodes RFC 3986 unreserved characters.</span></span>

<span data-ttu-id="2ccae-123">Für alle in diesem Thema beschriebenen URI-Schemen ignorieren *Schema*, *Autorität* und *Pfad* entweder standardmäßig die Groß- und Kleinschreibung oder werden andernfalls vom System ohne Beachtung der Schreibweise verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="2ccae-123">For all the URI schemes described in this topic, *scheme*, *authority*, and *path* are either case-insensitive by standard, or else are processed by the system in a case-insensitive way.</span></span> <span data-ttu-id="2ccae-124">**Hinweis:** Die einzige Ausnahme von dieser Regel ist die *Autorität* `ms-resource`, bei die Schreibweise von Bedeutung ist.</span><span class="sxs-lookup"><span data-stu-id="2ccae-124">**Note** The only exception to that rule is the *authority* of `ms-resource`, which is case-sensitive.</span></span>

## <a name="ms-appx-and-ms-appx-web"></a><span data-ttu-id="2ccae-125">ms-appx und ms-appx-web</span><span class="sxs-lookup"><span data-stu-id="2ccae-125">ms-appx and ms-appx-web</span></span>

<span data-ttu-id="2ccae-126">Verwenden Sie `ms-appx` oder `ms-appx-web`-URI-Schemen, um auf eine Datei zu verweisen, die aus Ihrem App-Paket stammt (siehe [Verpacken von Apps](../packaging/index.md)).</span><span class="sxs-lookup"><span data-stu-id="2ccae-126">Use the `ms-appx` or the `ms-appx-web` URI scheme to refer to a file that comes from your app's package (see [Packaging apps](../packaging/index.md)).</span></span> <span data-ttu-id="2ccae-127">Bei diesen Dateien Ihres App-Pakets handelt es sich in der Regel um statische Bilder, Daten, Code und Layoutdateien.</span><span class="sxs-lookup"><span data-stu-id="2ccae-127">Files in your app package are typically static images, data, code, and layout files.</span></span> <span data-ttu-id="2ccae-128">Das `ms-appx-web`-Schema greift auf die gleichen Dateien wie `ms-appx` zu, jedoch im Webdepot.</span><span class="sxs-lookup"><span data-stu-id="2ccae-128">The `ms-appx-web` scheme accesses the same files as `ms-appx`, but in the web compartment.</span></span> <span data-ttu-id="2ccae-129">Beispiele und weitere Informationen finden Sie unter [Verweisen auf ein Bild oder eine Ressource aus XAML-Markup und Code](images-tailored-for-scale-theme-contrast.md#reference-an-image-or-other-asset-from-xaml-markup-and-code).</span><span class="sxs-lookup"><span data-stu-id="2ccae-129">For examples and more info, see [Reference an image or other asset from XAML markup and code](images-tailored-for-scale-theme-contrast.md#reference-an-image-or-other-asset-from-xaml-markup-and-code).</span></span>

### <a name="scheme-name-ms-appx-and-ms-appx-web"></a><span data-ttu-id="2ccae-130">Schemaname (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="2ccae-130">Scheme name (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="2ccae-131">Die Zeichenfolge "ms-appx" oder "ms-appx-web" stellt den URI-Schemanamen dar.</span><span class="sxs-lookup"><span data-stu-id="2ccae-131">The URI scheme name is the string "ms-appx" or "ms-appx-web".</span></span>

```xml
ms-appx://
```

```xml
ms-appx-web://
```

### <a name="authority-ms-appx-and-ms-appx-web"></a><span data-ttu-id="2ccae-132">Autorität (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="2ccae-132">Authority (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="2ccae-133">Die Autorität ist der Paketidentitätsname, der im Paketmanifest definiert ist.</span><span class="sxs-lookup"><span data-stu-id="2ccae-133">The authority is the package identity name that is defined in the package manifest.</span></span> <span data-ttu-id="2ccae-134">Sie ist daher sowohl in der URI- als auch der IRI (Internationalized Resource Identifier)-Form auf den für den Paketidentitätsnamen zulässigen Zeichensatz beschränkt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-134">It is therefore limited in both the URI and IRI (Internationalized resource identifier) form to the set of characters allowed in a package identity name.</span></span> <span data-ttu-id="2ccae-135">Der Paketname muss ein Namen des Pakets im Paketabhängigkeitsdiagramms der ausgeführten App sein.</span><span class="sxs-lookup"><span data-stu-id="2ccae-135">The package name must be the name of one of the packages in the current running app's package dependency graph.</span></span>

```xml
ms-appx://Contoso.MyApp/
ms-appx-web://Contoso.MyApp/
```

<span data-ttu-id="2ccae-136">Werden in der Autorität andere Zeichen angegeben, schlagen Abruf und Vergleich fehl.</span><span class="sxs-lookup"><span data-stu-id="2ccae-136">If any other character appears in the authority, then retrieval and comparison fail.</span></span> <span data-ttu-id="2ccae-137">Der Standardwert für die Autorität ist das derzeit ausgeführte App-Paket.</span><span class="sxs-lookup"><span data-stu-id="2ccae-137">The default value for the authority is the currently running app's package.</span></span>

```xml
ms-appx:///
ms-appx-web:///
```

### <a name="user-info-and-port-ms-appx-and-ms-appx-web"></a><span data-ttu-id="2ccae-138">Benutzerinformationen und Port (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="2ccae-138">User info and port (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="2ccae-139">Das `ms-appx`-Schema definiert im Gegensatz zu anderen beliebten Schemen keine Benutzerinformationen oder Portkomponente.</span><span class="sxs-lookup"><span data-stu-id="2ccae-139">The `ms-appx` scheme, unlike other popular schemes, does not define a user info or port component.</span></span> <span data-ttu-id="2ccae-140">Da "@" and ":" nicht als gültige Autoritätswerte zulässig sind, schlägt die Suche fehl, wenn diese Zeichen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="2ccae-140">Since "@" and ":" are not allowed as valid authority values, lookup will fail if they are included.</span></span> <span data-ttu-id="2ccae-141">Folgende Beispiele schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="2ccae-141">Each of the following fails.</span></span>

```xml
ms-appx://john@contoso.myapp/default.html
ms-appx://john:password@contoso.myapp/default.html
ms-appx://contoso.myapp:8080/default.html
ms-appx://john:password@contoso.myapp:8080/default.html
```

### <a name="path-ms-appx-and-ms-appx-web"></a><span data-ttu-id="2ccae-142">Pfad (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="2ccae-142">Path (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="2ccae-143">Die Pfadkomponente entspricht der generischen RFC 3986-Syntax und unterstützt Nicht-ASCII-Zeichen in IRIs.</span><span class="sxs-lookup"><span data-stu-id="2ccae-143">The path component matches the generic RFC 3986 syntax and supports non-ASCII characters in IRIs.</span></span> <span data-ttu-id="2ccae-144">Die Pfadkomponente definiert den logischen oder physischen Dateipfad einer Datei.</span><span class="sxs-lookup"><span data-stu-id="2ccae-144">The path component defines the logical or physical file path of a file.</span></span> <span data-ttu-id="2ccae-145">Diese Datei ist in einem Ordner enthalten, der mit dem Installationsort des Pakets einer von der Autorität angegebenen App verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="2ccae-145">That file is in a folder associated with the installed location of the app package, for the app specified by the authority.</span></span>

<span data-ttu-id="2ccae-146">Wenn der Pfad auf einem physischen Pfad und Dateiname verweist, wird die physische Dateiressource abgerufen.</span><span class="sxs-lookup"><span data-stu-id="2ccae-146">If the path refers to a physical path and file name then that physical file asset is retrieved.</span></span> <span data-ttu-id="2ccae-147">Wenn keine physische Datei gefunden wird, wird die tatsächlich während des Abrufs zurückgegebene Ressource zur Laufzeit mittels Inhaltsaushandlung ermittelt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-147">But if no such physical file is found then the actual resource returned during retrieval is determined by using content negotiation at runtime.</span></span> <span data-ttu-id="2ccae-148">Diese Ermittlung basiert auf App, Betriebssystem und Benutzereinstellungen wie Sprache, Skalierungsfaktor, Designs, hoher Kontrast und andere Laufzeitkontexte.</span><span class="sxs-lookup"><span data-stu-id="2ccae-148">This determination is based on app, OS, and user settings such as language, display scale factor, theme, high contrast, and other runtime contexts.</span></span> <span data-ttu-id="2ccae-149">Eine Kombination der Sprachen der App, die Anzeigeeinstellungen des Systems und die hohen Kontrasteinstellungen des Benutzers werden beispielsweise  berücksichtigt, wenn der tatsächliche abzurufende Ressourcenwert ermittelt wird:</span><span class="sxs-lookup"><span data-stu-id="2ccae-149">For example, a combination of the app's languages, the system's display settings, and the user's high contrast settings may be taken into account when determining the actual resource value to be retrieved.</span></span>

```xml
ms-appx:///images/logo.png
```

<span data-ttu-id="2ccae-150">Die oben genannte URI kann tatsächlich eine Datei im aktuellen App-Paket mit folgendem physischen Dateinamen abrufen.</span><span class="sxs-lookup"><span data-stu-id="2ccae-150">The URI above may actually retrieve a file within the current app's package with the following physical file name.</span></span>

```
\Images\fr-FR\logo.scale-100_contrast-white.png
```

<span data-ttu-id="2ccae-151">Sie können natürlich auch die gleiche physische Datei abrufen, indem Sie direkt mit dem vollständigen Namen darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="2ccae-151">You could of course also retrieve that same physical file by referring to it directly by its full name.</span></span>

```xaml
<Image Source="ms-appx:///images/fr-FR/logo.scale-100_contrast-white.png"/>
```

<span data-ttu-id="2ccae-152">Bei der Pfadkomponente von `ms-appx(-web)` muss wie bei generischen URIs die Groß-/Kleinschreibung beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-152">The path component of `ms-appx(-web)` is, like generic URIs, case sensitive.</span></span> <span data-ttu-id="2ccae-153">Wenn beim zugrunde liegenden Dateisystem, von dem auf die Ressource zugegriffen wird, wie bei NTFS die Groß-/Kleinschreibung nicht berücksichtigt wird, wird auch beim Abrufen der Ressource die Groß-/Kleinschreibung ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-153">However, when the underlying file system by which the resource is accessed is case insensitive, such as for NTFS, the retrieval of the resource is done case-insensitively.</span></span>

<span data-ttu-id="2ccae-154">Bei der normalisierten Form des URI bleibt die Groß-/Kleinschreibung erhalten, und von nicht reservierten RFC 3986-Zeichen werden die Prozentzeichen entfernt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-154">The normalized form of the URI maintains case, and percent-decodes (a "%" symbol followed by the two-digit hexadecimal representation) RFC 3986 unreserved characters.</span></span> <span data-ttu-id="2ccae-155">Die Zeichen "?", "#", "/", "\*" und '”' (doppelte Anführungszeichen) müssen in einem Pfad mit einem Prozentzeichen versehen werden, um Daten wie Datei- oder Ordnernamen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="2ccae-155">The characters "?", "#", "/", "\*", and '”' (the double-quote character) must be percent-encoded in a path to represent data such as file or folder names.</span></span> <span data-ttu-id="2ccae-156">Alle mit Prozentzeichen versehenen Zeichen werden vor dem Abrufen decodiert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-156">All percent-encoded characters are decoded before retrieval.</span></span> <span data-ttu-id="2ccae-157">Verwenden Sie daher zum Abrufen der Datei "Hello#World.html" diese URI.</span><span class="sxs-lookup"><span data-stu-id="2ccae-157">Thus, to retrieve a file named Hello#World.html, use this URI.</span></span>

```xml
ms-appx:///Hello%23World.html
```

### <a name="query-ms-appx-and-ms-appx-web"></a><span data-ttu-id="2ccae-158">Abfrage (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="2ccae-158">Query (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="2ccae-159">Abfrageparameter werden während des Abrufens von Ressourcen ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-159">Query parameters are ignored during retrieval of resources.</span></span> <span data-ttu-id="2ccae-160">Bei der normalisierten Form von Abfrageparametern wird die Groß-/Kleinschreibung erhalten.</span><span class="sxs-lookup"><span data-stu-id="2ccae-160">The normalized form of query parameters maintains case.</span></span> <span data-ttu-id="2ccae-161">Abfrageparameter werden beim Vergleich nicht ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-161">Query parameters are not ignored during comparison.</span></span>

## <a name="ms-appdata"></a><span data-ttu-id="2ccae-162">ms-appdata</span><span class="sxs-lookup"><span data-stu-id="2ccae-162">ms-appdata</span></span>

<span data-ttu-id="2ccae-163">Verweisen Sie mithilfe des `ms-appdata`-URI Schemas auf App-Dateien, die aus den lokalen und temporären Datenordnern sowie Roamingdatenordnern stammen.</span><span class="sxs-lookup"><span data-stu-id="2ccae-163">Use the `ms-appdata` URI scheme to refer to files that come from the app's local, roaming, and temporary data folders.</span></span> <span data-ttu-id="2ccae-164">Weitere Informationen zu diesen App-Datendateien finden Sie unter [Speichern und Abrufen von Einstellungen und anderen App-Daten](../design/app-settings/store-and-retrieve-app-data.md).</span><span class="sxs-lookup"><span data-stu-id="2ccae-164">For more info about these app data folders, see [Store and retrieve settings and other app data](../design/app-settings/store-and-retrieve-app-data.md).</span></span>

<span data-ttu-id="2ccae-165">Das `ms-appdata`-URI-Schema führt keine Laufzeit mittels Inhaltsaushandlung durch, die [ms-appx and ms-appx-web](#ms-appx-and-ms-appx-web) durchführen.</span><span class="sxs-lookup"><span data-stu-id="2ccae-165">The `ms-appdata` URI scheme does not perform the runtime content negotiation that [ms-appx and ms-appx-web](#ms-appx-and-ms-appx-web) do.</span></span> <span data-ttu-id="2ccae-166">Sie können allerdings auf den Inhalt des [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.QualifierValues) reagieren und die richtigen Ressourcen über den gesamten physischen Dateiname im URI in App-Daten laden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-166">But you can respond to the contents of [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext.QualifierValues) and load the appropriate assets from app data using their full physical file name in the URI.</span></span>

### <a name="scheme-name-ms-appdata"></a><span data-ttu-id="2ccae-167">Schemaname (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="2ccae-167">Scheme name (ms-appdata)</span></span>

<span data-ttu-id="2ccae-168">Die Zeichenfolge „ms-appdata” stellt den URI-Schemanamen dar.</span><span class="sxs-lookup"><span data-stu-id="2ccae-168">The URI scheme name is the string "ms-appdata".</span></span>

```xml
ms-appdata://
```

### <a name="authority-ms-appdata"></a><span data-ttu-id="2ccae-169">Autorität (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="2ccae-169">Authority (ms-appdata)</span></span>

<span data-ttu-id="2ccae-170">Die Autorität ist der Paketidentitätsname, der im Paketmanifest definiert ist.</span><span class="sxs-lookup"><span data-stu-id="2ccae-170">The authority is the package identity name that is defined in the package manifest.</span></span> <span data-ttu-id="2ccae-171">Sie ist daher sowohl in der URI- als auch der IRI (Internationalized Resource Identifier)-Form auf den für den Paketidentitätsnamen zulässigen Zeichensatz beschränkt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-171">It is therefore limited in both the URI and IRI (Internationalized resource identifier) form to the set of characters allowed in a package identity name.</span></span> <span data-ttu-id="2ccae-172">Der Paketname muss der Name des aktuellen Pakets der ausgeführten App sein.</span><span class="sxs-lookup"><span data-stu-id="2ccae-172">The package name must be the name of the current running app's package.</span></span>

```xml
ms-appdata://Contoso.MyApp/
```

<span data-ttu-id="2ccae-173">Werden in der Autorität andere Zeichen angegeben, schlagen Abruf und Vergleich fehl.</span><span class="sxs-lookup"><span data-stu-id="2ccae-173">If any other character appears in the authority, then retrieval and comparison fail.</span></span> <span data-ttu-id="2ccae-174">Der Standardwert für die Autorität ist das derzeit ausgeführte App-Paket.</span><span class="sxs-lookup"><span data-stu-id="2ccae-174">The default value for the authority is the currently running app's package.</span></span>

```xml
ms-appdata:///
```

### <a name="user-info-and-port-ms-appdata"></a><span data-ttu-id="2ccae-175">Benutzerinformationen und Port (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="2ccae-175">User info and port (ms-appdata)</span></span>

<span data-ttu-id="2ccae-176">Das `ms-appdata`-Schema definiert im Gegensatz zu anderen beliebten Schemen keine Benutzerinformationen oder Portkomponente.</span><span class="sxs-lookup"><span data-stu-id="2ccae-176">The `ms-appdata` scheme, unlike other popular schemes, does not define a user info or port component.</span></span> <span data-ttu-id="2ccae-177">Da "@" and ":" nicht als gültige Autoritätswerte zulässig sind, schlägt die Suche fehl, wenn diese Zeichen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="2ccae-177">Since "@" and ":" are not allowed as valid authority values, lookup will fail if they are included.</span></span> <span data-ttu-id="2ccae-178">Folgende Beispiele schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="2ccae-178">Each of the following fails.</span></span>

```xml
ms-appdata://john@contoso.myapp/local/data.xml
ms-appdata://john:password@contoso.myapp/local/data.xml
ms-appdata://contoso.myapp:8080/local/data.xml
ms-appdata://john:password@contoso.myapp:8080/local/data.xml
```

### <a name="path-ms-appdata"></a><span data-ttu-id="2ccae-179">Pfad (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="2ccae-179">Path (ms-appdata)</span></span>

<span data-ttu-id="2ccae-180">Die Pfadkomponente entspricht der generischen RFC 3986-Syntax und unterstützt Nicht-ASCII-Zeichen in IRIs.</span><span class="sxs-lookup"><span data-stu-id="2ccae-180">The path component matches the generic RFC 3986 syntax and supports non-ASCII characters in IRIs.</span></span> <span data-ttu-id="2ccae-181">Am Speicherort [Windows.Storage.ApplicationData](/uwp/api/Windows.Storage.ApplicationData?branch=live) befinden sich drei reservierte Ordner für lokale und temporäre Statusspeicher sowie für Roamingstatusspeicher.</span><span class="sxs-lookup"><span data-stu-id="2ccae-181">Within the [Windows.Storage.ApplicationData](/uwp/api/Windows.Storage.ApplicationData?branch=live) location are three reserved folders for local, roaming, and temporary state storage.</span></span> <span data-ttu-id="2ccae-182">Das Schema `ms-appdata` ermöglicht den Zugriff auf Dateien und Ordner an diesen Speicherorten.</span><span class="sxs-lookup"><span data-stu-id="2ccae-182">The `ms-appdata` scheme allows access to files and folders in those locations.</span></span> <span data-ttu-id="2ccae-183">Im ersten Segment der Pfadkomponente muss der bestimmte Ordner in folgendem Format angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-183">The first segment of the path component must specify the particular folder in the following fashion.</span></span> <span data-ttu-id="2ccae-184">Daher ist die Form „path-empty” von „hier-part” nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="2ccae-184">Thus the "path-empty" form of "hier-part" is not legal.</span></span>

<span data-ttu-id="2ccae-185">Lokaler Ordner.</span><span class="sxs-lookup"><span data-stu-id="2ccae-185">Local folder.</span></span>

```xml
ms-appdata:///local/
```

<span data-ttu-id="2ccae-186">Temporärer Ordner.</span><span class="sxs-lookup"><span data-stu-id="2ccae-186">Temporary folder.</span></span>

```xml
ms-appdata:///temp/
```

<span data-ttu-id="2ccae-187">Roamingordner.</span><span class="sxs-lookup"><span data-stu-id="2ccae-187">Roaming folder.</span></span>

```xml
ms-appdata:///roaming/
```

<span data-ttu-id="2ccae-188">Bei der Pfadkomponente von `ms-appdata` muss wie bei generischen URIs die Groß-/Kleinschreibung beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-188">The path component of `ms-appdata` is, like generic URIs, case sensitive.</span></span> <span data-ttu-id="2ccae-189">Wenn beim zugrunde liegenden Dateisystem, von dem auf die Ressource zugegriffen wird, wie bei NTFS die Groß-/Kleinschreibung nicht berücksichtigt wird, wird auch beim Abrufen der Ressource die Groß-/Kleinschreibung ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-189">However, when the underlying file system by which the resource is accessed is case insensitive, such as for NTFS, the retrieval of the resource is done case-insensitively.</span></span>

<span data-ttu-id="2ccae-190">Bei der normalisierten Form des URI bleibt die Groß-/Kleinschreibung erhalten, und von nicht reservierten RFC 3986-Zeichen werden die Prozentzeichen entfernt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-190">The normalized form of the URI maintains case, and percent-decodes (a "%" symbol followed by the two-digit hexadecimal representation) RFC 3986 unreserved characters.</span></span> <span data-ttu-id="2ccae-191">Die Zeichen "?", "#", "/", "\*" und '”' (doppelte Anführungszeichen) müssen in einem Pfad mit einem Prozentzeichen versehen werden, um Daten wie Datei- oder Ordnernamen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="2ccae-191">The characters "?", "#", "/", "\*", and '”' (the double-quote character) must be percent-encoded in a path to represent data such as file or folder names.</span></span> <span data-ttu-id="2ccae-192">Alle mit Prozentzeichen versehenen Zeichen werden vor dem Abrufen decodiert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-192">All percent-encoded characters are decoded before retrieval.</span></span> <span data-ttu-id="2ccae-193">Verwenden Sie daher zum Abrufen der lokalen Datei "Hello#World.html" diese URI.</span><span class="sxs-lookup"><span data-stu-id="2ccae-193">Thus, to retrieve a local file named Hello#World.html, use this URI.</span></span>

```xml
ms-appdata://local/Hello%23World.html
```

<span data-ttu-id="2ccae-194">Der Abruf der Ressource und die Identifikation des Segments für den Pfad auf oberster Ebene werden nach der Normalisierung von Punkten behandelt (".././b/c").</span><span class="sxs-lookup"><span data-stu-id="2ccae-194">Retrieval of the resource, and identification of the top level path segment, are handled after normalization of dots (".././b/c").</span></span> <span data-ttu-id="2ccae-195">Daher können bei URIs keine Punkte für die reservierten Ordner verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-195">Therefore, URIs cannot dot themselves out of one of the reserved folders.</span></span> <span data-ttu-id="2ccae-196">Die folgenden URI sind also nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="2ccae-196">Thus, the following URI is not allowed.</span></span>

```xml
ms-appdata:///local/../hello/logo.png
```

<span data-ttu-id="2ccae-197">Diese URI ist jedoch zulässig (wenn auch redundant).</span><span class="sxs-lookup"><span data-stu-id="2ccae-197">But this URI is allowed (albeit redundant).</span></span>

```xml
ms-appdata:///local/../roaming/logo.png
```

### <a name="query-ms-appdata"></a><span data-ttu-id="2ccae-198">Abfrage (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="2ccae-198">Query (ms-appdata)</span></span>

<span data-ttu-id="2ccae-199">Abfrageparameter werden während des Abrufens von Ressourcen ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-199">Query parameters are ignored during retrieval of resources.</span></span> <span data-ttu-id="2ccae-200">Bei der normalisierten Form von Abfrageparametern wird die Groß-/Kleinschreibung erhalten.</span><span class="sxs-lookup"><span data-stu-id="2ccae-200">The normalized form of query parameters maintains case.</span></span> <span data-ttu-id="2ccae-201">Abfrageparameter werden beim Vergleich nicht ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-201">Query parameters are not ignored during comparison.</span></span>

## <a name="ms-resource"></a><span data-ttu-id="2ccae-202">ms-resource</span><span class="sxs-lookup"><span data-stu-id="2ccae-202">ms-resource</span></span>

<span data-ttu-id="2ccae-203">Verwenden Sie das URI-Schema `ms-resource` , um auf Zeichenfolgen zu verweisen, die aus den Ressourcendateien Ihrer App (.resw) geladen wurden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-203">Use the `ms-resource` URI scheme to refer to strings loaded from your app's Resources Files (.resw).</span></span> <span data-ttu-id="2ccae-204">Weitere Beispiele und Informationen zu Ressourcendateien (.resw) finden Sie unter [Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App](localize-strings-ui-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="2ccae-204">For examples and more info about Resources Files, see [Localize strings in your UI and app package manifest](localize-strings-ui-manifest.md).</span></span>

### <a name="scheme-name-ms-resource"></a><span data-ttu-id="2ccae-205">Schemaname (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="2ccae-205">Scheme name (ms-resource)</span></span>

<span data-ttu-id="2ccae-206">Die Zeichenfolge „ms-resource” stellt den URI-Schemanamen dar.</span><span class="sxs-lookup"><span data-stu-id="2ccae-206">The URI scheme name is the string "ms-resource".</span></span>

```xml
ms-resource://
```

### <a name="authority-ms-resource"></a><span data-ttu-id="2ccae-207">Autorität (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="2ccae-207">Authority (ms-resource)</span></span>

<span data-ttu-id="2ccae-208">Bei der Autorität handelt es sich um die im Package Resource Index (PRI) definierte Ressourcenzuordnung der obersten Ebene, die in der Regel dem Paketidentitätsnamen entspricht, der im Paketmanifest festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="2ccae-208">The authority is the top-level resource map defined in the Package Resource Index (PRI), which typically corresponds to the package identity name that is defined in the package manifest.</span></span> <span data-ttu-id="2ccae-209">Siehe [Verpacken von Apps](../packaging/index.md).</span><span class="sxs-lookup"><span data-stu-id="2ccae-209">See [Packaging apps](../packaging/index.md)).</span></span> <span data-ttu-id="2ccae-210">Sie ist daher sowohl in der URI- als auch der IRI (Internationalized Resource Identifier)-Form auf den für den Paketidentitätsnamen zulässigen Zeichensatz beschränkt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-210">It is therefore limited in both the URI and IRI (Internationalized resource identifier) form to the set of characters allowed in a package identity name.</span></span> <span data-ttu-id="2ccae-211">Der Paketname muss ein Namen des Pakets im Paketabhängigkeitsdiagramms der ausgeführten App sein.</span><span class="sxs-lookup"><span data-stu-id="2ccae-211">The package name must be the name of one of the packages in the current running app's package dependency graph.</span></span>

```xml
ms-resource://Contoso.MyApp/
ms-resource://Microsoft.WinJS.1.0/
```

<span data-ttu-id="2ccae-212">Werden in der Autorität andere Zeichen angegeben, schlagen Abruf und Vergleich fehl.</span><span class="sxs-lookup"><span data-stu-id="2ccae-212">If any other character appears in the authority, then retrieval and comparison fail.</span></span> <span data-ttu-id="2ccae-213">Der Standardwert für die Autorität ist der die Groß-/Kleinschreibung beachtende Name der aktuell ausgeführten App.</span><span class="sxs-lookup"><span data-stu-id="2ccae-213">The default value for the authority is the case-sensitive package name of the currently running app.</span></span>

```xml
ms-resource:///
```

<span data-ttu-id="2ccae-214">Bei der Autorität wird die Groß-/Kleinschreibung berücksichtigt und bei der normalisierten Form die Groß-/Kleinschreibung erhalten.</span><span class="sxs-lookup"><span data-stu-id="2ccae-214">The authority is case sensitive, and the normalized form maintains its case.</span></span> <span data-ttu-id="2ccae-215">Bei der Suche nach einer Ressource wird die Groß-/Kleinschreibung jedoch ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-215">Lookup of a resource, however, happens case-insensitively.</span></span>

### <a name="user-info-and-port-ms-resource"></a><span data-ttu-id="2ccae-216">Benutzerinformationen und Port (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="2ccae-216">User info and port (ms-resource)</span></span>

<span data-ttu-id="2ccae-217">Das `ms-resource`-Schema definiert im Gegensatz zu anderen beliebten Schemen keine Benutzerinformationen oder Portkomponente.</span><span class="sxs-lookup"><span data-stu-id="2ccae-217">The `ms-resource` scheme, unlike other popular schemes, does not define a user info or port component.</span></span> <span data-ttu-id="2ccae-218">Da "@" and ":" nicht als gültige Autoritätswerte zulässig sind, schlägt die Suche fehl, wenn diese Zeichen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="2ccae-218">Since "@" and ":" are not allowed as valid authority values, lookup will fail if they are included.</span></span> <span data-ttu-id="2ccae-219">Folgende Beispiele schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="2ccae-219">Each of the following fails.</span></span>

```xml
ms-resource://john@contoso.myapp/Resources/String1
ms-resource://john:password@contoso.myapp/Resources/String1
ms-resource://contoso.myapp:8080/Resources/String1
ms-resource://john:password@contoso.myapp:8080/Resources/String1
```

### <a name="path-ms-resource"></a><span data-ttu-id="2ccae-220">Pfad (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="2ccae-220">Path (ms-resource)</span></span>

<span data-ttu-id="2ccae-221">Der Pfad gibt den hierarchischen Ort der [ResourceMap](/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceMap?branch=live)-Unterstruktur (siehe [Resource Management System](https://msdn.microsoft.com/library/windows/apps/jj552947)) und das darin enthaltene [NamedResource](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource?branch=live)-Element an.</span><span class="sxs-lookup"><span data-stu-id="2ccae-221">The path identifies the hierarchical location of the [ResourceMap](/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceMap?branch=live) subtree (see [Resource Management System](https://msdn.microsoft.com/library/windows/apps/jj552947)) and the [NamedResource](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource?branch=live) within it.</span></span> <span data-ttu-id="2ccae-222">Dies entspricht in der Regel dem Dateinamen (ohne Erweiterung) der Ressourcendatei (.resw) und dem Bezeichner der darin enthaltenen Zeichenfolgenressource.</span><span class="sxs-lookup"><span data-stu-id="2ccae-222">Typically, this corresponds to the filename (excluding extension) of a Resources Files (.resw) and the identifier of a string resource within it.</span></span>

<span data-ttu-id="2ccae-223">Beispiele und weitere Informationen finden Sie unter [Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App](localize-strings-ui-manifest.md) und [Unterstützte Kachel- und Popupbenachrichtigungen für Sprache, Skalierungsfaktor und hohen Kontrast](../design/shell/tiles-and-notifications/tile-toast-language-scale-contrast.md).</span><span class="sxs-lookup"><span data-stu-id="2ccae-223">For examples and more info, see [Localize strings in your UI and app package manifest](localize-strings-ui-manifest.md) and [Tile and toast notification support for language, scale, and high contrast](../design/shell/tiles-and-notifications/tile-toast-language-scale-contrast.md).</span></span>

<span data-ttu-id="2ccae-224">Bei der Pfadkomponente von `ms-resource` muss wie bei generischen URIs die Groß-/Kleinschreibung beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-224">The path component of `ms-resource` is, like generic URIs, case sensitive.</span></span> <span data-ttu-id="2ccae-225">Der zugrunde liegende Abruf jedoch eine [CompareStringOrdinal](https://msdn.microsoft.com/library/windows/apps/br224628) und *IgnoreCase* auf festgelegt `true`.</span><span class="sxs-lookup"><span data-stu-id="2ccae-225">However, the underlying retrieval does a [CompareStringOrdinal](https://msdn.microsoft.com/library/windows/apps/br224628) with *ignoreCase* set to `true`.</span></span>

<span data-ttu-id="2ccae-226">Bei der normalisierten Form des URI bleibt die Groß-/Kleinschreibung erhalten, und von nicht reservierten RFC 3986-Zeichen werden die Prozentzeichen entfernt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-226">The normalized form of the URI maintains case, and percent-decodes (a "%" symbol followed by the two-digit hexadecimal representation) RFC 3986 unreserved characters.</span></span> <span data-ttu-id="2ccae-227">Die Zeichen "?", "#", "/", "\*" und '”' (doppelte Anführungszeichen) müssen in einem Pfad mit einem Prozentzeichen versehen werden, um Daten wie Datei- oder Ordnernamen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="2ccae-227">The characters "?", "#", "/", "\*", and '”' (the double-quote character) must be percent-encoded in a path to represent data such as file or folder names.</span></span> <span data-ttu-id="2ccae-228">Alle mit Prozentzeichen versehenen Zeichen werden vor dem Abrufen decodiert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-228">All percent-encoded characters are decoded before retrieval.</span></span> <span data-ttu-id="2ccae-229">Daher zum Abrufen einer Zeichenfolgenressource aus einer Ressourcendatei mit dem Namen `Hello#World.resw`, verwenden Sie diese URI.</span><span class="sxs-lookup"><span data-stu-id="2ccae-229">Thus, to retrieve a string resource from a Resources File named `Hello#World.resw`, use this URI.</span></span>

```xml
ms-resource:///Hello%23World/String1
```

### <a name="query-ms-resource"></a><span data-ttu-id="2ccae-230">Abfrage (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="2ccae-230">Query (ms-resource)</span></span>

<span data-ttu-id="2ccae-231">Abfrageparameter werden während des Abrufens von Ressourcen ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-231">Query parameters are ignored during retrieval of resources.</span></span> <span data-ttu-id="2ccae-232">Bei der normalisierten Form von Abfrageparametern wird die Groß-/Kleinschreibung erhalten.</span><span class="sxs-lookup"><span data-stu-id="2ccae-232">The normalized form of query parameters maintains case.</span></span> <span data-ttu-id="2ccae-233">Abfrageparameter werden beim Vergleich nicht ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2ccae-233">Query parameters are not ignored during comparison.</span></span> <span data-ttu-id="2ccae-234">Beim Vergleichen von Abfrageparametern wird die Groß-/Kleinschreibung berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="2ccae-234">Query parameters are compared case-sensitively.</span></span>

<span data-ttu-id="2ccae-235">Entwickler bestimmter Komponenten, die sich in Ebenen über dieser URI-Analyse befinden, können die Abfrageparameter flexibel verwenden.</span><span class="sxs-lookup"><span data-stu-id="2ccae-235">Developers of particular components layered above this URI parsing may choose to use the query parameters as they see fit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="2ccae-236">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2ccae-236">Related topics</span></span>

* [<span data-ttu-id="2ccae-237">Uniform Resource Identifier (URI): Allgemeine Syntax</span><span class="sxs-lookup"><span data-stu-id="2ccae-237">Uniform Resource Identifier (URI): Generic Syntax</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=263444)
* [<span data-ttu-id="2ccae-238">Verpacken von Apps</span><span class="sxs-lookup"><span data-stu-id="2ccae-238">Packaging apps</span></span>](../packaging/index.md)
* [<span data-ttu-id="2ccae-239">Verweisen auf ein Bild oder eine Ressource aus XAML-Markup und Code</span><span class="sxs-lookup"><span data-stu-id="2ccae-239">Reference an image or other asset from XAML markup and code</span></span>](images-tailored-for-scale-theme-contrast.md#reference-an-image-or-other-asset-from-xaml-markup-and-code)
* [<span data-ttu-id="2ccae-240">Speichern und Abrufen von Einstellungen und anderen App-Daten</span><span class="sxs-lookup"><span data-stu-id="2ccae-240">Store and retrieve settings and other app data</span></span>](../design/app-settings/store-and-retrieve-app-data.md)
* [<span data-ttu-id="2ccae-241">Lokalisieren von Zeichenfolgen im Paketmanifest der Benutzeroberfläche und der App</span><span class="sxs-lookup"><span data-stu-id="2ccae-241">Localize strings in your UI and app package manifest</span></span>](localize-strings-ui-manifest.md)
* [<span data-ttu-id="2ccae-242">Ressourcenverwaltungssystem</span><span class="sxs-lookup"><span data-stu-id="2ccae-242">Resource Management System</span></span>](https://msdn.microsoft.com/library/windows/apps/jj552947)
* [<span data-ttu-id="2ccae-243">Unterstützte Kachel- und Popupbenachrichtigungen für die Sprache, den Skalierungsfaktor für die Anzeige, das Design und den hohen Kontrast</span><span class="sxs-lookup"><span data-stu-id="2ccae-243">Tile and toast notification support for language, scale, and high contrast</span></span>](../design/shell/tiles-and-notifications/tile-toast-language-scale-contrast.md)