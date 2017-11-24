---
author: stevewhims
Description: "Es gibt mehrere URI (Uniform Resource Identifier)-Schemen, die Sie verwenden können, um auf Dateien in Ihrem App Paket, im App-Ordner oder in der Cloud zu verweisen. Sie können ebenfalls ein URI-Schema verwenden, um auf Zeichenfolgen in der App-Ressourcendateien (.resw) zu verweisen."
title: URI-Schemen
template: detail.hbs
ms.author: stwhi
ms.date: 10/16/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 4f9a6202aad56d008754cc6276ed82a540316ece
ms.sourcegitcommit: 27f7829f6d86ad8e13de3d13bff72825c1dbab7f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="uri-schemes"></a><span data-ttu-id="e60d2-105">URI-Schemen</span><span class="sxs-lookup"><span data-stu-id="e60d2-105">URI schemes</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="e60d2-106">Es gibt mehrere URI (Uniform Resource Identifier)-Schemen, die Sie verwenden können, um auf Dateien aus Ihrem App Paket, dem App-Ordner oder der Cloud zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-106">There are several URI (Uniform Resource Identifier) schemes that you can use to refer to files that come from your app's package, your app's data folders, or the cloud.</span></span> <span data-ttu-id="e60d2-107">Sie können ebenfalls ein URI-Schema verwenden, um auf Zeichenfolgen, die von der App-Ressourcendateien (.resw) geladen wurden, zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-107">You can also use a URI scheme to refer to strings loaded from your app's Resources Files (.resw).</span></span> <span data-ttu-id="e60d2-108">Sie können diese URI-Schemen in Ihrem Code, im XAML-Markup, in Ihrem App-Paketmanifest oder in der Kachel und Popupbenachrichtigungsvorlage verwenden.</span><span class="sxs-lookup"><span data-stu-id="e60d2-108">You can use these URI schemes in your code, in your XAML markup, in your app package manifest, or in your tile and toast notification templates.</span></span>

## <a name="common-features-of-the-uri-schemes"></a><span data-ttu-id="e60d2-109">Allgemeine Features der URI-Schemen</span><span class="sxs-lookup"><span data-stu-id="e60d2-109">Common features of the URI schemes</span></span>

<span data-ttu-id="e60d2-110">Alle in diesem Thema beschriebenen Schemen folgen den typischen URI-Schema-Regeln für die Normalisierung und den Ressourcenabruf.</span><span class="sxs-lookup"><span data-stu-id="e60d2-110">All of the schemes described in this topic follow typical URI scheme rules for normalization and resource retrieval.</span></span> <span data-ttu-id="e60d2-111">Weitere Informationen für die allgemeine Syntax für eine URI finden Sie unter [RFC 3986](http://go.microsoft.com/fwlink/p/?LinkId=263444).</span><span class="sxs-lookup"><span data-stu-id="e60d2-111">See [RFC 3986](http://go.microsoft.com/fwlink/p/?LinkId=263444) for the generic syntax of a URI.</span></span>

<span data-ttu-id="e60d2-112">Bei allen URI-Schemen wird der hierarchische Teil gemäß [RFC 3986](http://go.microsoft.com/fwlink/p/?LinkId=263444) als die Autoritäts- und Pfadkomponenten des URI definiert:</span><span class="sxs-lookup"><span data-stu-id="e60d2-112">All of the URI schemes define the hierarchical part per [RFC 3986](http://go.microsoft.com/fwlink/p/?LinkId=263444) as the authority and path components of the URI.</span></span>

```
URI         = scheme ":" hier-part [ "?" query ] [ "#" fragment ]
hier-part   = "//" authority path-abempty
            / path-absolute
            / path-rootless
            / path-empty
```

<span data-ttu-id="e60d2-113">Dies bedeutet, dass es im Wesentlichen drei Komponenten für einen URI gibt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-113">What this means is that there are essentially three components to a URI.</span></span> <span data-ttu-id="e60d2-114">Unmittelbar nach den Schrägstrichen des URI *Schemas* ist eine Komponente (ggf. leer), die als *authority* bezeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="e60d2-114">Immediately following the two forward slashes of the URI *scheme* is a component (which can be empty) called the *authority*.</span></span> <span data-ttu-id="e60d2-115">Und direkt danach befindet sich *path*.</span><span class="sxs-lookup"><span data-stu-id="e60d2-115">And immediately following that is the *path*.</span></span> <span data-ttu-id="e60d2-116">Als Beispiel: Bei der URI `http://www.contoso.com/welcome.png` ist das Schema "`http://`", die Autorität "`www.contoso.com`" und der Pfad "`/welcome.png`".</span><span class="sxs-lookup"><span data-stu-id="e60d2-116">Taking the URI `http://www.contoso.com/welcome.png` as an example, the scheme is "`http://`", the authority is "`www.contoso.com`", and the path is "`/welcome.png`".</span></span> <span data-ttu-id="e60d2-117">Ein weiteres Beispiel ist die URI `ms-appx:///logo.png`, wobei die Autorität für die Komponenten leer ist und einen Standardwert annimmt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-117">Another example is the URI `ms-appx:///logo.png`, where the authority components is empty and takes a default value.</span></span>

<span data-ttu-id="e60d2-118">Die Fragment-Komponente wird bei der schemenspezifischen Verarbeitung der hier aufgeführten URIs ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-118">The fragment component is ignored by the scheme-specific processing of the URIs mentioned in this topic.</span></span> <span data-ttu-id="e60d2-119">Beim Ressourcenabruf und Vergleich hat die Fragment-Komponente keine Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="e60d2-119">During resource retrieval and comparison, the fragment component has no bearing.</span></span> <span data-ttu-id="e60d2-120">Ebenen über einer bestimmten Implementierung können die Fragment-Komponente jedoch so interpretieren, dass sie eine sekundäre Ressource abruft.</span><span class="sxs-lookup"><span data-stu-id="e60d2-120">However, layers above specific implementation may interpret the fragment to retrieve a secondary resource.</span></span>

<span data-ttu-id="e60d2-121">Der Vergleich findet byteweise nach der Normalisierung aller IRI-Komponenten statt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-121">Comparison occurs byte for byte after normalization of all IRI components.</span></span>

## <a name="case-insensitivity-and-normalization"></a><span data-ttu-id="e60d2-122">Das Ignorieren der Groß-/Kleinschreibung und die Normalisierung</span><span class="sxs-lookup"><span data-stu-id="e60d2-122">Case-insensitivity and normalization</span></span>

<span data-ttu-id="e60d2-123">Alle in diesem Thema beschriebenen URI-Schemen folgen den typischen URI-Regeln (RFC 3986) für die Normalisierung und den Ressourcenabruf für Schemen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-123">All the URI schemes described in this topic follow typical URI rules (RFC 3986) for normalization and resource retrieval for schemes.</span></span> <span data-ttu-id="e60d2-124">Bei der normalisierten Form der URI bleibt die Groß-/Kleinschreibung erhalten, und von nicht reservierten RFC 3986-Zeichen werden die Prozentzeichen entfernt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-124">The normalized form of these URIs maintains case and percent-decodes RFC 3986 unreserved characters.</span></span>

<span data-ttu-id="e60d2-125">Für alle in diesem Thema beschriebenen URI-Schemen ignorieren *Schema*, *Autorität* und *Pfad* entweder standardmäßig die Groß- und Kleinschreibung oder werden andernfalls vom System als Ignorieren der Groß- und Kleinschreibung verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="e60d2-125">For all the URI schemes described in this topic, *scheme*, *authority*, and *path* are either case-insensitive by standard, or else are processed by the system in a case-insensitive way.</span></span> <span data-ttu-id="e60d2-126">**Hinweis** Die einzige Ausnahme dieser Regel ist die *Autorität* der ms-resource, die die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="e60d2-126">**Note** The only exception to that rule is the *authority* of ms-resource, which is case-sensitive.</span></span>

## <a name="ms-appx-and-ms-appx-web"></a><span data-ttu-id="e60d2-127">ms-appx und ms-appx-web</span><span class="sxs-lookup"><span data-stu-id="e60d2-127">ms-appx and ms-appx-web</span></span>

<span data-ttu-id="e60d2-128">Verwenden Sie `ms-appx` oder `ms-appx-web`-URI-Schemen, um auf eine Datei zu verweisen, die aus Ihrem App-Paket stammt (siehe [Verpacken von Apps](../packaging/index.md)).</span><span class="sxs-lookup"><span data-stu-id="e60d2-128">Use the `ms-appx` or the `ms-appx-web` URI scheme to refer to a file that comes from your app's package (see [Packaging apps](../packaging/index.md)).</span></span> <span data-ttu-id="e60d2-129">Bei diesen Dateien Ihres App-Pakets handelt es sich in der Regel um statische Bilder, Daten, Code und Layoutdateien.</span><span class="sxs-lookup"><span data-stu-id="e60d2-129">Files in your app package are typically static images, data, code, and layout files.</span></span> <span data-ttu-id="e60d2-130">Das `ms-appx-web`-Schema greift auf die gleichen Dateien wie `ms-appx` zu, jedoch im Webdepot.</span><span class="sxs-lookup"><span data-stu-id="e60d2-130">The `ms-appx-web` scheme accesses the same files as `ms-appx`, but in the web compartment.</span></span> <span data-ttu-id="e60d2-131">Beispiele und weitere Informationen finden Sie unter [Verweisen auf ein Bild oder eine Ressource aus XAML-Markup und Code](image-qualifiers-loc-scale-accessibility.md#reference-an-image-or-other-asset-from-xaml-markup-and-code).</span><span class="sxs-lookup"><span data-stu-id="e60d2-131">For examples and more info, see [Reference an image or other asset from XAML markup and code](image-qualifiers-loc-scale-accessibility.md#reference-an-image-or-other-asset-from-xaml-markup-and-code).</span></span>

### <a name="scheme-name-ms-appx-and-ms-appx-web"></a><span data-ttu-id="e60d2-132">Schemaname (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="e60d2-132">Scheme name (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="e60d2-133">Die Zeichenfolge "ms-appx" oder "ms-appx-web" stellt den URI-Schemanamen dar.</span><span class="sxs-lookup"><span data-stu-id="e60d2-133">The URI scheme name is the string "ms-appx" or "ms-appx-web".</span></span>

```xml
ms-appx://
```

```xml
ms-appx-web://
```

### <a name="authority-ms-appx-and-ms-appx-web"></a><span data-ttu-id="e60d2-134">Autorität (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="e60d2-134">Authority (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="e60d2-135">Die Autorität ist der Paketidentitätsname, der im Paketmanifest definiert ist.</span><span class="sxs-lookup"><span data-stu-id="e60d2-135">The authority is the package identity name that is defined in the package manifest.</span></span> <span data-ttu-id="e60d2-136">Sie ist daher sowohl in der URI- als auch der IRI (Internationalized Resource Identifier)-Form auf den für den Paketidentitätsnamen zulässigen Zeichensatz beschränkt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-136">It is therefore limited in both the URI and IRI (Internationalized resource identifier) form to the set of characters allowed in a package identity name.</span></span> <span data-ttu-id="e60d2-137">Der Paketname muss ein Namen des Pakets im Paketabhängigkeitsdiagramms der ausgeführten App sein.</span><span class="sxs-lookup"><span data-stu-id="e60d2-137">The package name must be the name of one of the packages in the current running app's package dependency graph.</span></span>

```
ms-appx://Contoso.MyApp/
ms-appx-web://Contoso.MyApp/
```

<span data-ttu-id="e60d2-138">Werden in der Autorität andere Zeichen angegeben, schlagen Abruf und Vergleich fehl.</span><span class="sxs-lookup"><span data-stu-id="e60d2-138">If any other character appears in the authority, then retrieval and comparison fail.</span></span> <span data-ttu-id="e60d2-139">Der Standardwert für die Autorität ist das derzeit ausgeführte App-Paket.</span><span class="sxs-lookup"><span data-stu-id="e60d2-139">The default value for the authority is the currently running app's package.</span></span>

```
ms-appx:///
ms-appx-web:///
```

### <a name="user-info-and-port-ms-appx-and-ms-appx-web"></a><span data-ttu-id="e60d2-140">Benutzerinformationen und Port (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="e60d2-140">User info and port (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="e60d2-141">Das `ms-appx`-Schema definiert im Gegensatz zu anderen beliebten Schemen keine Benutzerinformationen oder Portkomponente.</span><span class="sxs-lookup"><span data-stu-id="e60d2-141">The `ms-appx` scheme, unlike other popular schemes, does not define a user info or port component.</span></span> <span data-ttu-id="e60d2-142">Da "@" and ":" nicht als gültige Autoritätswerte zulässig sind, schlägt die Suche fehl, wenn diese Zeichen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="e60d2-142">Since "@" and ":" are not allowed as valid authority values, lookup will fail if they are included.</span></span> <span data-ttu-id="e60d2-143">Folgende Beispiele schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="e60d2-143">Each of the following fails.</span></span>

```
ms-appx://john@contoso.myapp/default.html
ms-appx://john:password@contoso.myapp/default.html
ms-appx://contoso.myapp:8080/default.html
ms-appx://john:password@contoso.myapp:8080/default.html
```

### <a name="path-ms-appx-and-ms-appx-web"></a><span data-ttu-id="e60d2-144">Pfad (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="e60d2-144">Path (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="e60d2-145">Die Pfadkomponente entspricht der generischen RFC 3986-Syntax und unterstützt Nicht-ASCII-Zeichen in IRIs.</span><span class="sxs-lookup"><span data-stu-id="e60d2-145">The path component matches the generic RFC 3986 syntax and supports non-ASCII characters in IRIs.</span></span> <span data-ttu-id="e60d2-146">Die Pfadkomponente definiert den logischen oder physischen Dateipfad einer Datei.</span><span class="sxs-lookup"><span data-stu-id="e60d2-146">The path component defines the logical or physical file path of a file.</span></span> <span data-ttu-id="e60d2-147">Diese Datei ist in einem Ordner enthalten, der mit dem Installationsort des Pakets einer von der Autorität angegebenen App verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="e60d2-147">That file is in a folder associated with the installed location of the app package, for the app specified by the authority.</span></span>

<span data-ttu-id="e60d2-148">Wenn der Pfad auf einem physischen Pfad und Dateiname verweist, wird die physische Dateiressource abgerufen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-148">If the path refers to a physical path and file name then that physical file asset is retrieved.</span></span> <span data-ttu-id="e60d2-149">Wenn keine physische Datei gefunden wird, wird die tatsächlich während des Abrufs zurückgegebene Ressource zur Laufzeit mittels Inhaltsaushandlung ermittelt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-149">But if no such physical file is found then the actual resource returned during retrieval is determined by using content negotiation at runtime.</span></span> <span data-ttu-id="e60d2-150">Diese Ermittlung basiert auf App, Betriebssystem und Benutzereinstellungen wie Sprache, Skalierungsfaktor, Designs, hoher Kontrast und andere Laufzeitkontexte.</span><span class="sxs-lookup"><span data-stu-id="e60d2-150">This determination is based on app, OS, and user settings such as language, display scale factor, theme, high contrast, and other runtime contexts.</span></span> <span data-ttu-id="e60d2-151">Eine Kombination der Sprachen der App, die Anzeigeeinstellungen des Systems und die hohen Kontrasteinstellungen des Benutzers werden beispielsweise  berücksichtigt, wenn der tatsächliche abzurufende Ressourcenwert ermittelt wird:</span><span class="sxs-lookup"><span data-stu-id="e60d2-151">For example, a combination of the app's languages, the system's display settings, and the user's high contrast settings may be taken into account when determining the actual resource value to be retrieved.</span></span>

```
ms-appx:///images/logo.png
```

<span data-ttu-id="e60d2-152">Die oben genannte URI kann tatsächlich eine Datei im aktuellen App-Paket mit folgendem physischen Dateinamen abrufen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-152">The URI above may actually retrieve a file within the current app's package with the following physical file name.</span></span>

```
\Images\fr-FR\logo.scale-100_contrast-white.png
```

<span data-ttu-id="e60d2-153">Sie können natürlich auch die gleiche physische Datei abrufen, indem Sie direkt mit dem vollständigen Namen darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-153">You could of course also retrieve that same physical file by referring to it directly by its full name.</span></span>

**<span data-ttu-id="e60d2-154">XAML</span><span class="sxs-lookup"><span data-stu-id="e60d2-154">XAML</span></span>**
```xml
<Image Source="ms-appx:///images/fr-FR/logo.scale-100_contrast-white.png"/>
```

<span data-ttu-id="e60d2-155">Bei der Pfadkomponente von `ms-appx(-web)` muss wie bei generischen URIs die Groß-/Kleinschreibung beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="e60d2-155">The path component of `ms-appx(-web)` is, like generic URIs, case sensitive.</span></span> <span data-ttu-id="e60d2-156">Wenn beim zugrunde liegenden Dateisystem, von dem auf die Ressource zugegriffen wird, wie bei NTFS die Groß-/Kleinschreibung nicht berücksichtigt wird, wird auch beim Abrufen der Ressource die Groß-/Kleinschreibung ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-156">However, when the underlying file system by which the resource is accessed is case insensitive, such as for NTFS, the retrieval of the resource is done case-insensitively.</span></span>

<span data-ttu-id="e60d2-157">Bei der normalisierten Form des URI bleibt die Groß-/Kleinschreibung erhalten, und von nicht reservierten RFC 3986-Zeichen werden die Prozentzeichen entfernt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-157">The normalized form of the URI maintains case, and percent-decodes (a "%" symbol followed by the two-digit hexadecimal representation) RFC 3986 unreserved characters.</span></span> <span data-ttu-id="e60d2-158">Die Zeichen "?", "#", "/", "*" und '”' (doppelte Anführungszeichen) müssen in einem Pfad mit einem Prozentzeichen versehen werden, um Daten wie Datei- oder Ordnernamen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="e60d2-158">The characters "?", "#", "/", "*", and '”' (the double-quote character) must be percent-encoded in a path to represent data such as file or folder names.</span></span> <span data-ttu-id="e60d2-159">Alle mit Prozentzeichen versehenen Zeichen werden vor dem Abrufen decodiert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-159">All percent-encoded characters are decoded before retrieval.</span></span> <span data-ttu-id="e60d2-160">Verwenden Sie daher zum Abrufen der Datei "Hello#World.html" diese URI.</span><span class="sxs-lookup"><span data-stu-id="e60d2-160">Thus, to retrieve a file named Hello#World.html, use this URI.</span></span>

```
ms-appx:///Hello%23World.html
```

### <a name="query-ms-appx-and-ms-appx-web"></a><span data-ttu-id="e60d2-161">Abfrage (ms-appx und ms-appx-web)</span><span class="sxs-lookup"><span data-stu-id="e60d2-161">Query (ms-appx and ms-appx-web)</span></span>

<span data-ttu-id="e60d2-162">Abfrageparameter werden während des Abrufens von Ressourcen ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-162">Query parameters are ignored during retrieval of resources.</span></span> <span data-ttu-id="e60d2-163">Bei der normalisierten Form von Abfrageparametern wird die Groß-/Kleinschreibung erhalten.</span><span class="sxs-lookup"><span data-stu-id="e60d2-163">The normalized form of query parameters maintains case.</span></span> <span data-ttu-id="e60d2-164">Abfrageparameter werden beim Vergleich nicht ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-164">Query parameters are not ignored during comparison.</span></span>

## <a name="ms-appdata"></a><span data-ttu-id="e60d2-165">ms-appdata</span><span class="sxs-lookup"><span data-stu-id="e60d2-165">ms-appdata</span></span>

<span data-ttu-id="e60d2-166">Verweisen Sie mithilfe des `ms-appdata`-URI Schemas auf App-Dateien, die aus den lokalen und temporären Datenordnern sowie Roamingdatenordnern stammen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-166">Use the `ms-appdata` URI scheme to refer to files that come from the app's local, roaming, and temporary data folders.</span></span> <span data-ttu-id="e60d2-167">Weitere Informationen zu diesen App-Datendateien finden Sie unter [Speichern und Abrufen von Einstellungen und anderen App-Daten](../app-settings/store-and-retrieve-app-data).</span><span class="sxs-lookup"><span data-stu-id="e60d2-167">For more info about these app data folders, see [Store and retrieve settings and other app data](../app-settings/store-and-retrieve-app-data).</span></span>

<span data-ttu-id="e60d2-168">Das `ms-appdata`-URI-Schema führt keine Laufzeit mittels Inhaltsaushandlung durch, die [ms-appx and ms-appx-web](#ms-appx-and-ms-appx-web) durchführen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-168">The `ms-appdata` URI scheme does not perform the runtime content negotiation that [ms-appx and ms-appx-web](#ms-appx-and-ms-appx-web) do.</span></span> <span data-ttu-id="e60d2-169">Sie können allerdings auf den Inhalt des [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues) reagieren und die richtigen Ressourcen über den gesamten physischen Dateiname im URI in App-Daten laden.</span><span class="sxs-lookup"><span data-stu-id="e60d2-169">But you can respond to the contents of [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues) and load the appropriate assets from app data using their full physical file name in the URI.</span></span>

### <a name="scheme-name-ms-appdata"></a><span data-ttu-id="e60d2-170">Schemaname (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="e60d2-170">Scheme name (ms-appdata)</span></span>

<span data-ttu-id="e60d2-171">Die Zeichenfolge „ms-appdata” stellt den URI-Schemanamen dar.</span><span class="sxs-lookup"><span data-stu-id="e60d2-171">The URI scheme name is the string "ms-appdata".</span></span>

```xml
ms-appdata://
```

### <a name="authority-ms-appdata"></a><span data-ttu-id="e60d2-172">Autorität (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="e60d2-172">Authority (ms-appdata)</span></span>

<span data-ttu-id="e60d2-173">Die Autorität ist der Paketidentitätsname, der im Paketmanifest definiert ist.</span><span class="sxs-lookup"><span data-stu-id="e60d2-173">The authority is the package identity name that is defined in the package manifest.</span></span> <span data-ttu-id="e60d2-174">Sie ist daher sowohl in der URI- als auch der IRI (Internationalized Resource Identifier)-Form auf den für den Paketidentitätsnamen zulässigen Zeichensatz beschränkt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-174">It is therefore limited in both the URI and IRI (Internationalized resource identifier) form to the set of characters allowed in a package identity name.</span></span> <span data-ttu-id="e60d2-175">Der Paketname muss der Name des aktuellen Pakets der ausgeführten App sein.</span><span class="sxs-lookup"><span data-stu-id="e60d2-175">The package name must be the name of the current running app's package.</span></span>

```
ms-appdata://Contoso.MyApp/
```

<span data-ttu-id="e60d2-176">Werden in der Autorität andere Zeichen angegeben, schlagen Abruf und Vergleich fehl.</span><span class="sxs-lookup"><span data-stu-id="e60d2-176">If any other character appears in the authority, then retrieval and comparison fail.</span></span> <span data-ttu-id="e60d2-177">Der Standardwert für die Autorität ist das derzeit ausgeführte App-Paket.</span><span class="sxs-lookup"><span data-stu-id="e60d2-177">The default value for the authority is the currently running app's package.</span></span>

```
ms-appdata:///
```

### <a name="user-info-and-port-ms-appdata"></a><span data-ttu-id="e60d2-178">Benutzerinformationen und Port (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="e60d2-178">User info and port (ms-appdata)</span></span>

<span data-ttu-id="e60d2-179">Das `ms-appdata`-Schema definiert im Gegensatz zu anderen beliebten Schemen keine Benutzerinformationen oder Portkomponente.</span><span class="sxs-lookup"><span data-stu-id="e60d2-179">The `ms-appdata` scheme, unlike other popular schemes, does not define a user info or port component.</span></span> <span data-ttu-id="e60d2-180">Da "@" and ":" nicht als gültige Autoritätswerte zulässig sind, schlägt die Suche fehl, wenn diese Zeichen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="e60d2-180">Since "@" and ":" are not allowed as valid authority values, lookup will fail if they are included.</span></span> <span data-ttu-id="e60d2-181">Folgende Beispiele schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="e60d2-181">Each of the following fails.</span></span>

```
ms-appdata://john@contoso.myapp/local/data.xml
ms-appdata://john:password@contoso.myapp/local/data.xml
ms-appdata://contoso.myapp:8080/local/data.xml
ms-appdata://john:password@contoso.myapp:8080/local/data.xml
```

### <a name="path-ms-appdata"></a><span data-ttu-id="e60d2-182">Pfad (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="e60d2-182">Path (ms-appdata)</span></span>

<span data-ttu-id="e60d2-183">Die Pfadkomponente entspricht der generischen RFC 3986-Syntax und unterstützt Nicht-ASCII-Zeichen in IRIs.</span><span class="sxs-lookup"><span data-stu-id="e60d2-183">The path component matches the generic RFC 3986 syntax and supports non-ASCII characters in IRIs.</span></span> <span data-ttu-id="e60d2-184">Am Speicherort [Windows.Storage.ApplicationData](/uwp/api/Windows.Storage.ApplicationData?branch=live) befinden sich drei reservierte Ordner für lokale und temporäre Statusspeicher sowie für Roamingstatusspeicher.</span><span class="sxs-lookup"><span data-stu-id="e60d2-184">Within the [Windows.Storage.ApplicationData](/uwp/api/Windows.Storage.ApplicationData?branch=live) location are three reserved folders for local, roaming, and temporary state storage.</span></span> <span data-ttu-id="e60d2-185">Das Schema `ms-appdata` ermöglicht den Zugriff auf Dateien und Ordner an diesen Speicherorten.</span><span class="sxs-lookup"><span data-stu-id="e60d2-185">The `ms-appdata` scheme allows access to files and folders in those locations.</span></span> <span data-ttu-id="e60d2-186">Im ersten Segment der Pfadkomponente muss der bestimmte Ordner in folgendem Format angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="e60d2-186">The first segment of the path component must specify the particular folder in the following fashion.</span></span> <span data-ttu-id="e60d2-187">Daher ist die Form „path-empty” von „hier-part” nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="e60d2-187">Thus the "path-empty" form of "hier-part" is not legal.</span></span>

<span data-ttu-id="e60d2-188">Lokaler Ordner.</span><span class="sxs-lookup"><span data-stu-id="e60d2-188">Local folder.</span></span>

```
ms-appdata:///local/
```

<span data-ttu-id="e60d2-189">Temporärer Ordner.</span><span class="sxs-lookup"><span data-stu-id="e60d2-189">Temporary folder.</span></span>

```
ms-appdata:///temp/
```

<span data-ttu-id="e60d2-190">Roamingordner.</span><span class="sxs-lookup"><span data-stu-id="e60d2-190">Roaming folder.</span></span>

```
ms-appdata:///roaming/
```

<span data-ttu-id="e60d2-191">Bei der Pfadkomponente von `ms-appdata` muss wie bei generischen URIs die Groß-/Kleinschreibung beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="e60d2-191">The path component of `ms-appdata` is, like generic URIs, case sensitive.</span></span> <span data-ttu-id="e60d2-192">Wenn beim zugrunde liegenden Dateisystem, von dem auf die Ressource zugegriffen wird, wie bei NTFS die Groß-/Kleinschreibung nicht berücksichtigt wird, wird auch beim Abrufen der Ressource die Groß-/Kleinschreibung ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-192">However, when the underlying file system by which the resource is accessed is case insensitive, such as for NTFS, the retrieval of the resource is done case-insensitively.</span></span>

<span data-ttu-id="e60d2-193">Bei der normalisierten Form des URI bleibt die Groß-/Kleinschreibung erhalten, und von nicht reservierten RFC 3986-Zeichen werden die Prozentzeichen entfernt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-193">The normalized form of the URI maintains case, and percent-decodes (a "%" symbol followed by the two-digit hexadecimal representation) RFC 3986 unreserved characters.</span></span> <span data-ttu-id="e60d2-194">Die Zeichen "?", "#", "/", "*" und '”' (doppelte Anführungszeichen) müssen in einem Pfad mit einem Prozentzeichen versehen werden, um Daten wie Datei- oder Ordnernamen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="e60d2-194">The characters "?", "#", "/", "*", and '”' (the double-quote character) must be percent-encoded in a path to represent data such as file or folder names.</span></span> <span data-ttu-id="e60d2-195">Alle mit Prozentzeichen versehenen Zeichen werden vor dem Abrufen decodiert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-195">All percent-encoded characters are decoded before retrieval.</span></span> <span data-ttu-id="e60d2-196">Verwenden Sie daher zum Abrufen der lokalen Datei "Hello#World.html" diese URI.</span><span class="sxs-lookup"><span data-stu-id="e60d2-196">Thus, to retrieve a local file named Hello#World.html, use this URI.</span></span>

```
ms-appdata://local/Hello%23World.html
```

<span data-ttu-id="e60d2-197">Der Abruf der Ressource und die Identifikation des Segments für den Pfad auf oberster Ebene werden nach der Normalisierung von Punkten behandelt (".././b/c").</span><span class="sxs-lookup"><span data-stu-id="e60d2-197">Retrieval of the resource, and identification of the top level path segment, are handled after normalization of dots (".././b/c").</span></span> <span data-ttu-id="e60d2-198">Daher können bei URIs keine Punkte für die reservierten Ordner verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e60d2-198">Therefore, URIs cannot dot themselves out of one of the reserved folders.</span></span> <span data-ttu-id="e60d2-199">Die folgenden URI sind also nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="e60d2-199">Thus, the following URI is not allowed.</span></span>

```
ms-appdata:///local/../hello/logo.png
```

<span data-ttu-id="e60d2-200">Diese URI ist jedoch zulässig (wenn auch redundant).</span><span class="sxs-lookup"><span data-stu-id="e60d2-200">But this URI is allowed (albeit redundant).</span></span>

```
ms-appdata:///local/../roaming/logo.png
```

### <a name="query-ms-appdata"></a><span data-ttu-id="e60d2-201">Abfrage (ms-appdata)</span><span class="sxs-lookup"><span data-stu-id="e60d2-201">Query (ms-appdata)</span></span>

<span data-ttu-id="e60d2-202">Abfrageparameter werden während des Abrufens von Ressourcen ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-202">Query parameters are ignored during retrieval of resources.</span></span> <span data-ttu-id="e60d2-203">Bei der normalisierten Form von Abfrageparametern wird die Groß-/Kleinschreibung erhalten.</span><span class="sxs-lookup"><span data-stu-id="e60d2-203">The normalized form of query parameters maintains case.</span></span> <span data-ttu-id="e60d2-204">Abfrageparameter werden beim Vergleich nicht ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-204">Query parameters are not ignored during comparison.</span></span>

## <a name="ms-resource"></a><span data-ttu-id="e60d2-205">ms-resource</span><span class="sxs-lookup"><span data-stu-id="e60d2-205">ms-resource</span></span>

<span data-ttu-id="e60d2-206">Sie können ebenfalls das URI-Schema `ms-resource` verwenden, um auf Zeichenfolgen, die von der App-Ressourcendateien (.resw) geladen wurden, zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="e60d2-206">Use the `ms-resource` URI scheme to refer to to refer to strings loaded from your app's Resources Files (.resw).</span></span> <span data-ttu-id="e60d2-207">Weitere Beispiele und Informationen zu Ressourcendateien (.resw) finden Sie unter [Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App](put-ui-strings-into-resources.md).</span><span class="sxs-lookup"><span data-stu-id="e60d2-207">For examples and more info about Resources Files, see [Localize strings in your UI and app package manifest](put-ui-strings-into-resources.md).</span></span>

### <a name="scheme-name-ms-resource"></a><span data-ttu-id="e60d2-208">Schemaname (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="e60d2-208">Scheme name (ms-resource)</span></span>

<span data-ttu-id="e60d2-209">Die Zeichenfolge „ms-resource” stellt den URI-Schemanamen dar.</span><span class="sxs-lookup"><span data-stu-id="e60d2-209">The URI scheme name is the string "ms-resource".</span></span>

```xml
ms-resource://
```

### <a name="authority-ms-resource"></a><span data-ttu-id="e60d2-210">Autorität (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="e60d2-210">Authority (ms-resource)</span></span>

<span data-ttu-id="e60d2-211">Bei der Autorität handelt es sich um die im Package Resource Index (PRI) definierte Ressourcenzuordnung der obersten Ebene, die in der Regel dem Paketidentitätsnamen entspricht, der im Paketmanifest festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="e60d2-211">The authority is the top-level resource map defined in the Package Resource Index (PRI), which typically corresponds to the package identity name that is defined in the package manifest.</span></span> <span data-ttu-id="e60d2-212">Siehe [Verpacken von Apps](../packaging/index.md).</span><span class="sxs-lookup"><span data-stu-id="e60d2-212">See [Packaging apps](../packaging/index.md)).</span></span> <span data-ttu-id="e60d2-213">Sie ist daher sowohl in der URI- als auch der IRI (Internationalized Resource Identifier)-Form auf den für den Paketidentitätsnamen zulässigen Zeichensatz beschränkt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-213">It is therefore limited in both the URI and IRI (Internationalized resource identifier) form to the set of characters allowed in a package identity name.</span></span> <span data-ttu-id="e60d2-214">Der Paketname muss ein Namen des Pakets im Paketabhängigkeitsdiagramms der ausgeführten App sein.</span><span class="sxs-lookup"><span data-stu-id="e60d2-214">The package name must be the name of one of the packages in the current running app's package dependency graph.</span></span>

```
ms-resource://Contoso.MyApp/
ms-resource://Microsoft.WinJS.1.0/
```

<span data-ttu-id="e60d2-215">Werden in der Autorität andere Zeichen angegeben, schlagen Abruf und Vergleich fehl.</span><span class="sxs-lookup"><span data-stu-id="e60d2-215">If any other character appears in the authority, then retrieval and comparison fail.</span></span> <span data-ttu-id="e60d2-216">Der Standardwert für die Autorität ist der die Groß-/Kleinschreibung beachtende Name der aktuell ausgeführten App.</span><span class="sxs-lookup"><span data-stu-id="e60d2-216">The default value for the authority is the case-sensitive package name of the currently running app.</span></span>

```
ms-resource:///
```

<span data-ttu-id="e60d2-217">Bei der Autorität wird die Groß-/Kleinschreibung berücksichtigt und bei der normalisierten Form die Groß-/Kleinschreibung erhalten.</span><span class="sxs-lookup"><span data-stu-id="e60d2-217">The authority is case sensitive, and the normalized form maintains its case.</span></span> <span data-ttu-id="e60d2-218">Bei der Suche nach einer Ressource wird die Groß-/Kleinschreibung jedoch ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-218">Lookup of a resource, however, happens case-insensitively.</span></span>

### <a name="user-info-and-port-ms-resource"></a><span data-ttu-id="e60d2-219">Benutzerinformationen und Port (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="e60d2-219">User info and port (ms-resource)</span></span>

<span data-ttu-id="e60d2-220">Das `ms-resource`-Schema definiert im Gegensatz zu anderen beliebten Schemen keine Benutzerinformationen oder Portkomponente.</span><span class="sxs-lookup"><span data-stu-id="e60d2-220">The `ms-resource` scheme, unlike other popular schemes, does not define a user info or port component.</span></span> <span data-ttu-id="e60d2-221">Da "@" and ":" nicht als gültige Autoritätswerte zulässig sind, schlägt die Suche fehl, wenn diese Zeichen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="e60d2-221">Since "@" and ":" are not allowed as valid authority values, lookup will fail if they are included.</span></span> <span data-ttu-id="e60d2-222">Folgende Beispiele schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="e60d2-222">Each of the following fails.</span></span>

```
ms-resource://john@contoso.myapp/Resources/String1
ms-resource://john:password@contoso.myapp/Resources/String1
ms-resource://contoso.myapp:8080/Resources/String1
ms-resource://john:password@contoso.myapp:8080/Resources/String1
```

### <a name="path-ms-resource"></a><span data-ttu-id="e60d2-223">Pfad (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="e60d2-223">Path (ms-resource)</span></span>

<span data-ttu-id="e60d2-224">Der Pfad gibt den hierarchischen Ort der [ResourceMap](/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceMap?branch=live)-Unterstruktur (siehe [Resource Management System](https://msdn.microsoft.com/library/windows/apps/jj552947)) und das darin enthaltene [NamedResource](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResourcebranch=live)-Element an.</span><span class="sxs-lookup"><span data-stu-id="e60d2-224">The path identifies the hierarchical location of the [ResourceMap](/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceMap?branch=live) subtree (see [Resource Management System](https://msdn.microsoft.com/library/windows/apps/jj552947)) and the [NamedResource](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResourcebranch=live) within it.</span></span> <span data-ttu-id="e60d2-225">Dies entspricht in der Regel dem Dateinamen (ohne Erweiterung) der Ressourcendatei (.resw) und dem Bezeichner der darin enthaltenen Zeichenfolgenressource.</span><span class="sxs-lookup"><span data-stu-id="e60d2-225">Typically, this corresponds to the filename (excluding extension) of a Resources Files (.resw) and the identifier of a string resource within it.</span></span>

<span data-ttu-id="e60d2-226">Beispiele und weitere Informationen finden Sie unter [Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App](put-ui-strings-into-resources.md) und [Unterstützte Kachel- und Popupbenachrichtigungen für Sprache, Skalierungsfaktor und hohen Kontrast](tile-toast-language-scale-contrast.md).</span><span class="sxs-lookup"><span data-stu-id="e60d2-226">For examples and more info, see [Localize strings in your UI and app package manifest](put-ui-strings-into-resources.md) and [Tile and toast notification support for language, scale, and high contrast](tile-toast-language-scale-contrast.md).</span></span>

<span data-ttu-id="e60d2-227">Bei der Pfadkomponente von `ms-resource` muss wie bei generischen URIs die Groß-/Kleinschreibung beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="e60d2-227">The path component of `ms-resource` is, like generic URIs, case sensitive.</span></span> <span data-ttu-id="e60d2-228">Wenn der zugrunde liegende Abruf eine [CompareStringOrdinal](https://msdn.microsoft.com/library/windows/apps/br224628) mit *IgnoreCase* ist, wird `true` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-228">However, when the underlying retrieval.does a [CompareStringOrdinal](https://msdn.microsoft.com/library/windows/apps/br224628) with *ignoreCase* set to `true`.</span></span>

<span data-ttu-id="e60d2-229">Bei der normalisierten Form des URI bleibt die Groß-/Kleinschreibung erhalten, und von nicht reservierten RFC 3986-Zeichen werden die Prozentzeichen entfernt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-229">The normalized form of the URI maintains case, and percent-decodes (a "%" symbol followed by the two-digit hexadecimal representation) RFC 3986 unreserved characters.</span></span> <span data-ttu-id="e60d2-230">Die Zeichen "?", "#", "/", "*" und '”' (doppelte Anführungszeichen) müssen in einem Pfad mit einem Prozentzeichen versehen werden, um Daten wie Datei- oder Ordnernamen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="e60d2-230">The characters "?", "#", "/", "*", and '”' (the double-quote character) must be percent-encoded in a path to represent data such as file or folder names.</span></span> <span data-ttu-id="e60d2-231">Alle mit Prozentzeichen versehenen Zeichen werden vor dem Abrufen decodiert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-231">All percent-encoded characters are decoded before retrieval.</span></span> <span data-ttu-id="e60d2-232">Verwenden Sie daher zum Abrufen einer Zeichenfolgenressource aus einer Ressourcendatei mit dem Namen Hello#World.resw diesen URI.</span><span class="sxs-lookup"><span data-stu-id="e60d2-232">Thus, to retrieve a string resource from a Resources File named Hello#World.resw, use this URI.</span></span>

```
ms-resource:///Hello%23World/String1
```

### <a name="query-ms-resource"></a><span data-ttu-id="e60d2-233">Abfrage (ms-resource)</span><span class="sxs-lookup"><span data-stu-id="e60d2-233">Query (ms-resource)</span></span>

<span data-ttu-id="e60d2-234">Abfrageparameter werden während des Abrufens von Ressourcen ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-234">Query parameters are ignored during retrieval of resources.</span></span> <span data-ttu-id="e60d2-235">Bei der normalisierten Form von Abfrageparametern wird die Groß-/Kleinschreibung erhalten.</span><span class="sxs-lookup"><span data-stu-id="e60d2-235">The normalized form of query parameters maintains case.</span></span> <span data-ttu-id="e60d2-236">Abfrageparameter werden beim Vergleich nicht ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e60d2-236">Query parameters are not ignored during comparison.</span></span> <span data-ttu-id="e60d2-237">Beim Vergleichen von Abfrageparametern wird die Groß-/Kleinschreibung berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="e60d2-237">Query parameters are compared case-sensitively.</span></span>

<span data-ttu-id="e60d2-238">Entwickler bestimmter Komponenten, die sich in Ebenen über dieser URI-Analyse befinden, können die Abfrageparameter flexibel verwenden.</span><span class="sxs-lookup"><span data-stu-id="e60d2-238">Developers of particular components layered above this URI parsing may choose to use the query parameters as they see fit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e60d2-239">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e60d2-239">Related topics</span></span>

* [<span data-ttu-id="e60d2-240">Uniform Resource Identifier (URI): Allgemeine Syntax</span><span class="sxs-lookup"><span data-stu-id="e60d2-240">Uniform Resource Identifier (URI): Generic Syntax</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=263444)
* [<span data-ttu-id="e60d2-241">Verpacken von Apps</span><span class="sxs-lookup"><span data-stu-id="e60d2-241">Packaging apps</span></span>](../packaging/index.md)
* [<span data-ttu-id="e60d2-242">Verweisen auf ein Bild oder eine Ressource aus XAML-Markup und Code</span><span class="sxs-lookup"><span data-stu-id="e60d2-242">Reference an image or other asset from XAML markup and code</span></span>](image-qualifiers-loc-scale-accessibility.md#reference-an-image-or-other-asset-from-xaml-markup-and-code)
* [<span data-ttu-id="e60d2-243">Speichern und Abrufen von Einstellungen und anderen App-Daten</span><span class="sxs-lookup"><span data-stu-id="e60d2-243">Store and retrieve settings and other app data</span></span>](../app-settings/store-and-retrieve-app-data)
* [<span data-ttu-id="e60d2-244">Lokalisieren von Zeichenfolgen im Paketmanifest der Benutzeroberfläche und der App</span><span class="sxs-lookup"><span data-stu-id="e60d2-244">Localize strings in your UI and app package manifest</span></span>](put-ui-strings-into-resources.md)
* [<span data-ttu-id="e60d2-245">Ressourcenverwaltungssystem</span><span class="sxs-lookup"><span data-stu-id="e60d2-245">Resource Management System</span></span>](https://msdn.microsoft.com/library/windows/apps/jj552947)
* [<span data-ttu-id="e60d2-246">Unterstützte Kachel- und Popupbenachrichtigungen für die Sprache, den Skalierungsfaktor für die Anzeige, das Design und den hohen Kontrast</span><span class="sxs-lookup"><span data-stu-id="e60d2-246">Tile and toast notification support for language, scale, and high contrast</span></span>](tile-toast-language-scale-contrast.md)