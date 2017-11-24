---
author: stevewhims
Description: "In diesem Thema wird das allgemeine Konzept der Qualifizierer erläutert, wie sie verwendet werden und wofür die einzelnen Qualifizierernamen dienen."
title: Passen Sie Ihrer Ressourcen der Sprache, Skalierung, dem hohen Kontrast und anderen Qualifizierern an
template: detail.hbs
ms.author: stwhi
ms.date: 10/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 99b76ad155818b56e5fd6873df19bc0400c0a218
ms.sourcegitcommit: 165f57223ba69c0b7b71b295d9e0d35ea9a50a27
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2017
---
# <a name="tailor-your-resources-for-language-scale-high-contrast-and-other-qualifiers"></a><span data-ttu-id="2728a-104">Passen Sie Ihrer Ressourcen der Sprache, Skalierung, dem hohen Kontrast und anderen Qualifizierern an</span><span class="sxs-lookup"><span data-stu-id="2728a-104">Tailor your resources for language, scale, high contrast, and other qualifiers</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="2728a-105">In diesem Thema wird das allgemeine Konzept der Ressourcenqualifizierer erläutert, wie sie verwendet werden und wofür die einzelnen Qualifizierernamen dienen.</span><span class="sxs-lookup"><span data-stu-id="2728a-105">This topic explains the general concept of resource qualifiers, how to use them, and the purpose of each of the qualifier names.</span></span> <span data-ttu-id="2728a-106">Weitere Informationen für eine Referenztabelle für die verschiedenen Qualifiziererwerte finden Sie unter [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues).</span><span class="sxs-lookup"><span data-stu-id="2728a-106">See [ResourceContext.QualifierValues](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues) for a reference table of all the possible qualifier values.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="2728a-107">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="2728a-107">Important APIs</span></span></b><br/>
<ul>
<li>**[<span data-ttu-id="2728a-108">SetGlobalQualifierValue</span><span class="sxs-lookup"><span data-stu-id="2728a-108">SetGlobalQualifierValue</span></span>](/uwp/api/windows.applicationmodel.resources.core.resourcecontext#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_)**</li>
</ul>
</div>

<span data-ttu-id="2728a-109">Ihre App kann Assets und Ressourcen laden, die für Runtime-Kontexte wie Anzeigesprache, hoher Kontrast [Skalierungsfaktor des Displays](../layout/screen-sizes-and-breakpoints-for-responsive-design.md) und mehr zugeschnitten sind.</span><span class="sxs-lookup"><span data-stu-id="2728a-109">Your app can load assets and resources that are tailored to runtime contexts such as display language, high contrast, [display scale factor](../layout/screen-sizes-and-breakpoints-for-responsive-design.md), and many others.</span></span> <span data-ttu-id="2728a-110">Das erreichen Sie unter anderem durch das Benennen des Ressourcen-Ordners oder der Dateien mit dem Namen des Qualifizierers und den Qualifiziererwerten, die diesen Kontexten entsprechen.</span><span class="sxs-lookup"><span data-stu-id="2728a-110">The way you do this is to name your resources’ folders or files to match the qualifier names and qualifier values that correspond to those contexts.</span></span> <span data-ttu-id="2728a-111">Beispielsweise können Sie einen anderen Satz von Bildressourcen im Modus mit hohem Kontrast für Ihre App geladen.</span><span class="sxs-lookup"><span data-stu-id="2728a-111">For example, you may want your app to load a different set of image assets in high contrast mode.</span></span>

## <a name="qualifier-name-qualifier-value-and-qualifier"></a><span data-ttu-id="2728a-112">Qualifizierernamen Qualifiziererwerte und Qualifizierer</span><span class="sxs-lookup"><span data-stu-id="2728a-112">Qualifier name, qualifier value, and qualifier</span></span>

<span data-ttu-id="2728a-113">Ein Qualifizierername ist ein Schlüssel, der einer Reihe von Qualifiziererwerten zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="2728a-113">A qualifier name is a key that maps to a set of qualifier values.</span></span> <span data-ttu-id="2728a-114">Hier sind Qualifizierernamen und Qualifiziererwerte für den Kontrast aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="2728a-114">Here are the qualifier name and qualifier values for contrast.</span></span>

| <span data-ttu-id="2728a-115">Kontext</span><span class="sxs-lookup"><span data-stu-id="2728a-115">Context</span></span> | <span data-ttu-id="2728a-116">Qualifizierername</span><span class="sxs-lookup"><span data-stu-id="2728a-116">Qualifier name</span></span> | <span data-ttu-id="2728a-117">Qualifiziererwerte</span><span class="sxs-lookup"><span data-stu-id="2728a-117">Qualifier values</span></span> |
| :--------------- | :--------------- | :--------------- |
| <span data-ttu-id="2728a-118">Einstellung für hohen Kontrast</span><span class="sxs-lookup"><span data-stu-id="2728a-118">The high contrast setting</span></span> | <span data-ttu-id="2728a-119">Kontrast</span><span class="sxs-lookup"><span data-stu-id="2728a-119">contrast</span></span> | <span data-ttu-id="2728a-120">Standard, hoch, schwarz, weiß</span><span class="sxs-lookup"><span data-stu-id="2728a-120">standard, high, black, white</span></span> |

<span data-ttu-id="2728a-121">Kombinieren Sie einen Qualifizierernamen mit einem Qualifiziererwert, um einen Qualifizierer zu bilden.</span><span class="sxs-lookup"><span data-stu-id="2728a-121">You combine a qualifier name with a qualifier value to form a qualifier.</span></span> `<qualifier name>-<qualifier value>` <span data-ttu-id="2728a-122">ist das Format des Qualifizierers.</span><span class="sxs-lookup"><span data-stu-id="2728a-122">is the format of a qualifier.</span></span> `contrast-standard` <span data-ttu-id="2728a-123">ist ein Beispiel für einen Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="2728a-123">is an example of a qualifier.</span></span>

<span data-ttu-id="2728a-124">Für hohen Kontrast ist der Satz von Qualifizierern `contrast-standard`, `contrast-high`, `contrast-black` und `contrast-white`.</span><span class="sxs-lookup"><span data-stu-id="2728a-124">So, for high contrast, the set of qualifiers is `contrast-standard`, `contrast-high`, `contrast-black`, and `contrast-white`.</span></span> <span data-ttu-id="2728a-125">Bei Qualifizierernamen und Qualifiziererwerten wird die Groß-/Kleinschreibung nicht beachtet.</span><span class="sxs-lookup"><span data-stu-id="2728a-125">Qualifier names and qualifier values are not case sensitive.</span></span> <span data-ttu-id="2728a-126">Beispielsweise: `contrast-standard` und `Contrast-Standard` sind die gleiche Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="2728a-126">For example, `contrast-standard` and `Contrast-Standard` are the same qualifier.</span></span>

## <a name="use-qualifiers-in-folder-names"></a><span data-ttu-id="2728a-127">Qualifizierer in Ordnernamen verwenden</span><span class="sxs-lookup"><span data-stu-id="2728a-127">Use qualifiers in folder names</span></span>

<span data-ttu-id="2728a-128">Hier ist ein Beispiel für die Verwendung von Qualifizierer zum Benennen von Ordnern, die Ressourcendateien enthalten.</span><span class="sxs-lookup"><span data-stu-id="2728a-128">Here is an example of using qualifiers to name folders that contain asset files.</span></span> <span data-ttu-id="2728a-129">Verwenden Sie Qualifizierer in Ordnernamen, wenn Sie mehrere Ressourcendateien pro Qualifizierer haben.</span><span class="sxs-lookup"><span data-stu-id="2728a-129">Use qualifiers in folder names if you have several asset files per qualifier.</span></span> <span data-ttu-id="2728a-130">Auf diese Weise legen Sie den Qualifizierer einmal auf Ordnerebene fest und der Qualifizierer gilt für alle Elemente im Ordner.</span><span class="sxs-lookup"><span data-stu-id="2728a-130">That way, you set the qualifier once at the folder level, and the qualifier applies to everything inside the folder.</span></span>

```
\Assets\Images\contrast-standard\<logo.png, and other image files>
\Assets\Images\contrast-high\<logo.png, and other image files>
\Assets\Images\contrast-black\<logo.png, and other image files>
\Assets\Images\contrast-white\<logo.png, and other image files>
```

<span data-ttu-id="2728a-131">Wenn Sie Ihre Ordner wie im obigen Beispiel benennen, verwendet Ihre App den hohen Kontrast zum Laden von Dateien aus dem Ordner mit dem Namen für den entsprechenden Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="2728a-131">If you name your folders as in the example above, then your app uses the high contrast setting to load resource files from the folder named for the appropriate qualifier.</span></span> <span data-ttu-id="2728a-132">Wenn die Einstellung hoher Kontrast (Schwarz) ist, werden die Ressourcendateien in den Ordern `\Assets\Images\contrast-black` geladen.</span><span class="sxs-lookup"><span data-stu-id="2728a-132">So, if the setting is High Contrast Black, then the resource files in the `\Assets\Images\contrast-black` folder are loaded.</span></span> <span data-ttu-id="2728a-133">Wenn die Einstellung "Keine" ist (d.h. der Computer ist nicht im Modus mit hohem Kontrast), werden die Ressourcendateien in den Ordner `\Assets\Images\standard` geladen.</span><span class="sxs-lookup"><span data-stu-id="2728a-133">If the setting is None (that is, the computer is not in high contrast mode), then the resource files in the `\Assets\Images\standard` folder are loaded.</span></span>

## <a name="use-qualifiers-in-file-names"></a><span data-ttu-id="2728a-134">Qualifizierer in Dateinamen verwenden</span><span class="sxs-lookup"><span data-stu-id="2728a-134">Use qualifiers in file names</span></span>

<span data-ttu-id="2728a-135">Anstatt Ordner zu erstellen und zu benennen können Sie einen Qualifizierer verwenden, um die Ressourcendateien selbst zu benennen.</span><span class="sxs-lookup"><span data-stu-id="2728a-135">Instead of creating and naming folders, you can use a qualifier to name the resource files themselves.</span></span> <span data-ttu-id="2728a-136">Möglicherweise möchten dies tun, wenn Sie nur eine Ressourcendatei pro Qualifizierer haben.</span><span class="sxs-lookup"><span data-stu-id="2728a-136">You might prefer to do this if you only have one resource file per qualifier.</span></span> <span data-ttu-id="2728a-137">Hier ist ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="2728a-137">Here’s an example.</span></span>

```
\Assets\Images\logo.contrast-standard.png
\Assets\Images\logo.contrast-high.png
\Assets\Images\logo.contrast-black.png
\Assets\Images\logo.contrast-white.png
```

<span data-ttu-id="2728a-138">Die Datei, deren Name den geeignetsten Qualifizierer für die Einstellung enthält, wird geladen.</span><span class="sxs-lookup"><span data-stu-id="2728a-138">The file whose name contains the qualifier most appropriate for the setting is the one that is loaded.</span></span> <span data-ttu-id="2728a-139">Diese übereinstimmende Logik funktioniert genauso für Dateinamen als auch für Ordnernamen.</span><span class="sxs-lookup"><span data-stu-id="2728a-139">This matching logic works the same way for file names as for folder names.</span></span>

## <a name="reference-a-string-or-image-resource-by-name"></a><span data-ttu-id="2728a-140">Verweisen auf eine Zeichenfolgen- oder Bildressource nach Namen</span><span class="sxs-lookup"><span data-stu-id="2728a-140">Reference a string or image resource by name</span></span>

<span data-ttu-id="2728a-141">Weitere Informationen finden Sie unter [Refer to a string resource identifier from XAML markup](put-ui-strings-into-resources.md#refer-to-a-string-resource-identifier-from-xaml-markup), [Refer to a string resource identifier from code](put-ui-strings-into-resources.md#refer-to-a-string-resource-identifier-from-code) und [Verweisen auf eine Bildressource in XAML-Markup und Code](image-qualifiers-loc-scale-accessibility.md#reference-an-image-resource-in-xaml-markup-and-code).</span><span class="sxs-lookup"><span data-stu-id="2728a-141">See [Refer to a string resource identifier from XAML markup](put-ui-strings-into-resources.md#refer-to-a-string-resource-identifier-from-xaml-markup), [Refer to a string resource identifier from code](put-ui-strings-into-resources.md#refer-to-a-string-resource-identifier-from-code), and [Reference an image resource in XAML markup and code](image-qualifiers-loc-scale-accessibility.md#reference-an-image-resource-in-xaml-markup-and-code).</span></span>

## <a name="actual-and-neutral-qualifier-matches"></a><span data-ttu-id="2728a-142">Aktuelle und neutrale Qualifizierertreffer</span><span class="sxs-lookup"><span data-stu-id="2728a-142">Actual and neutral qualifier matches</span></span>
<span data-ttu-id="2728a-143">Sie müssen nicht für *jeden* Qualifiziererwert eine Ressourcendatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="2728a-143">You don’t need to provide a resource file for *every* qualifier value.</span></span> <span data-ttu-id="2728a-144">Wenn Sie z.B. feststellen, dass Sie nur eine visuelle Ressource für hohen Kontrast und eine für den standardmäßigen Kontrast benötigen, benennen Sie diese Ressourcen wie folgt.</span><span class="sxs-lookup"><span data-stu-id="2728a-144">For example, if you find that you only need one visual asset for high contrast and one for standard contrast, then you can name those assets like this.</span></span>

```
\Assets\Images\logo.contrast-high.png
\Assets\Images\logo.png
```

<span data-ttu-id="2728a-145">Der erste Dateiname enthält den `contrast-high` Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="2728a-145">The first file name contains the `contrast-high` qualifier.</span></span> <span data-ttu-id="2728a-146">Dieser Qualifizierer ist ein *tatsächlicher* Treffer für jede Einstellung mit hohem Kontrast, wenn der hohe Kontrast *aktiviert* ist.</span><span class="sxs-lookup"><span data-stu-id="2728a-146">That qualifier is an *actual* match for any high contrast setting when high contrast is *on*.</span></span> <span data-ttu-id="2728a-147">Anders ausgedrückt, ist es ähnlich und wird daher bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="2728a-147">In other words, it's a close match so it’s preferred.</span></span> <span data-ttu-id="2728a-148">Eine *tatsächliche* Übereinstimmung kann nur auftreten, wenn der Qualifizierer einen *tatsächlichen* Wert enthält, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="2728a-148">An *actual* match can only occur if the qualifier contains an *actual* value, as this one does.</span></span> <span data-ttu-id="2728a-149">In diesem Fall ist `high` ein *tatsächlicher* Wert für `contrast`.</span><span class="sxs-lookup"><span data-stu-id="2728a-149">In this case, `high` is an *actual* value for `contrast`.</span></span>

<span data-ttu-id="2728a-150">Die Datei mit dem Namen `logo.png` hat keinen Kontrastqualifizierer.</span><span class="sxs-lookup"><span data-stu-id="2728a-150">The file named `logo.png` has no contrast qualifier on it at all.</span></span> <span data-ttu-id="2728a-151">Das Fehlen eines Qualifizierers bedeutet, es ist ein *neutraler* Wert.</span><span class="sxs-lookup"><span data-stu-id="2728a-151">The absence of a qualifier is a *neutral* value.</span></span> <span data-ttu-id="2728a-152">Wenn keine bevorzugten Übereinstimmung gefunden werden kann, dient der neutrale Wert als Fallback-Übereinstimmung.</span><span class="sxs-lookup"><span data-stu-id="2728a-152">If no preferred match can be found, then the neutral value serves as a fallback match.</span></span> <span data-ttu-id="2728a-153">In diesem Beispiel: Wenn der hohe Kontrast *deaktiviert* ist, ist keine tatsächliche Übereinstimmung vorhanden.</span><span class="sxs-lookup"><span data-stu-id="2728a-153">In this example, if high contrast is *off*, then there is no actual match.</span></span> <span data-ttu-id="2728a-154">Die *neutrale* Übereinstimmung ist die beste Übereinstimmung, die gefunden werden kann, und das Element `logo.png` wird geladen.</span><span class="sxs-lookup"><span data-stu-id="2728a-154">The *neutral* match is the best match that can be found, and so the asset `logo.png` is loaded.</span></span>

<span data-ttu-id="2728a-155">Wenn Sie den Namen von `logo.png` auf `logo.contrast-standard.png` ändern würden, würde der Dateiname einen tatsächlichen Qualifiziererwert enthalten.</span><span class="sxs-lookup"><span data-stu-id="2728a-155">If you were to change the name of `logo.png` to `logo.contrast-standard.png`, then the file name would contain an actual qualifier value.</span></span> <span data-ttu-id="2728a-156">Wenn der hohe Kontrast deaktiviert ist, gäbe es eine tatsächliche Übereinstimmung mit `logo.contrast-standard.png` und diese Element-Datei würde geladen.</span><span class="sxs-lookup"><span data-stu-id="2728a-156">With high contrast off, there would be an actual match with `logo.contrast-standard.png`, and that’s the asset file that would be loaded.</span></span> <span data-ttu-id="2728a-157">Es würden daher dieselben Dateien geladen, unter den gleichen Bedingungen, aber aufgrund unterschiedlicher Übereinstimmungen.</span><span class="sxs-lookup"><span data-stu-id="2728a-157">So, the same files would be loaded, under the same conditions, but because of different matches.</span></span>

<span data-ttu-id="2728a-158">Wenn Sie nur einen Satz von Ressourcen für hohen Kontrast brauchen und einen Satz für Standard-Kontrast festgelegt ist, können Sie Ordnernamen anstelle von Dateinamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="2728a-158">If you only need one set of assets for high contrast and one set for standard contrast, then you can use folder names instead of file names.</span></span> <span data-ttu-id="2728a-159">In diesem Fall führt ein Weglassen des Ordnernamens zu einer neutralen Übereinstimmung.</span><span class="sxs-lookup"><span data-stu-id="2728a-159">In this case, omitting the folder name entirely gives you the neutral match.</span></span>

```
\Assets\Images\contrast-high\<logo.png, and other images to load when high contrast theme is not None>
\Assets\Images\<logo.png, and other images to load when high contrast theme is None>
```

<span data-ttu-id="2728a-160">Weitere Informationen zur Funktionsweise der Übereinstimmung für Qualifizierer finden Sie unter [Ressourcenverwaltungssystem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/jj552947).</span><span class="sxs-lookup"><span data-stu-id="2728a-160">For more details on how qualifier matching works, see [Resource Management System](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/jj552947).</span></span>

## <a name="multiple-qualifiers"></a><span data-ttu-id="2728a-161">Mehrere Qualifizierer</span><span class="sxs-lookup"><span data-stu-id="2728a-161">Multiple qualifiers</span></span>

<span data-ttu-id="2728a-162">Sie können Qualifizierer in Ordner- und Dateinamen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="2728a-162">You can combine qualifiers in folder and file names.</span></span> <span data-ttu-id="2728a-163">Wenn z.B. Ihre App Bildressourcen bei aktiviertem Modus für hohen Kontrast lädt *und* der Skalierungsfaktor für die Anzeige ist 400.</span><span class="sxs-lookup"><span data-stu-id="2728a-163">For example, you may want your app to load image assets when high contrast mode is on *and* the display scale factor is 400.</span></span> <span data-ttu-id="2728a-164">Eine Möglichkeit hierfür sind geschachtelte Ordner.</span><span class="sxs-lookup"><span data-stu-id="2728a-164">One way to do this is with nested folders.</span></span>

```
\Assets\Images\contrast-high\scale-400\<logo.png, and other image files>
```

<span data-ttu-id="2728a-165">Damit `logo.png` und anderen Dateien geladen werden, müssen die Einstellungen mit *beiden* Qualifizierern übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="2728a-165">For `logo.png` and the other files to be loaded, the settings must match *both* qualifiers.</span></span>

<span data-ttu-id="2728a-166">Eine weitere Möglichkeit ist, mehrere Qualifizierer in einem Ordnernamen zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="2728a-166">Another option is to combine multiple qualifiers in one folder name.</span></span>

```
\Assets\Images\contrast-high_scale-400\<logo.png, and other image files>
```

<span data-ttu-id="2728a-167">Kombinieren Sie in einem Ordnernamen mehrere Qualifizierer und trennen Sie diese mit einem Unterstrich.</span><span class="sxs-lookup"><span data-stu-id="2728a-167">In a folder name, you combine multiple qualifiers separated with an underscore.</span></span> `<qualifier1>[_<qualifier2>...]` <span data-ttu-id="2728a-168">ist das Format.</span><span class="sxs-lookup"><span data-stu-id="2728a-168">is the format.</span></span>

<span data-ttu-id="2728a-169">Sie können mehrere Qualifizierer in einem Dateinamen im selben Format kombinieren.</span><span class="sxs-lookup"><span data-stu-id="2728a-169">You can combine multiple qualifiers in a file name in the same format.</span></span>

```
\Assets\Images\logo.contrast-high_scale-400.png
```

<span data-ttu-id="2728a-170">Je nach verwendeten Tools und Workflows bei der Asset-Erstellung und je nachdem, was am einfachsten zu Lesen und Verwalten ist, können Sie entweder eine einzelne Benennungsstrategie für alle Qualifizierer auswählen oder diese für andere Qualifizierer kombinieren.</span><span class="sxs-lookup"><span data-stu-id="2728a-170">Depending on the tools and workflow you use for asset-creation, or on what you find easiest to read and/or manage, you can either choose a single naming strategy for all qualifiers, or you can combine them for different qualifiers.</span></span>

## <a name="alternateform"></a><span data-ttu-id="2728a-171">Alternatives Format</span><span class="sxs-lookup"><span data-stu-id="2728a-171">AlternateForm</span></span>

<span data-ttu-id="2728a-172">Mit dem `alternateform` Qualifizierer können Sie ein alternatives Format einer Ressource für einen speziellen Zweck angeben.</span><span class="sxs-lookup"><span data-stu-id="2728a-172">The `alternateform` qualifier is used to provide an alternate form of a resource for some special purpose.</span></span> <span data-ttu-id="2728a-173">Dies wird in der Regel nur von japanischen App-Entwicklern verwendet, um eine Furigana-Zeichenfolge bereitzustellen, für die der Wert `msft-phonetic` reserviert ist (Informationen hierzu finden Sie im Abschnitt "Unterstützung von Furigana für japanische Zeichenfolgen, die sortiert werden können" unter [ Vorbereiten für die Lokalisierung](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh967762)).</span><span class="sxs-lookup"><span data-stu-id="2728a-173">This is typically used only by Japanese app developers to provide a furigana string for which the value `msft-phonetic` is reserved (see the section “Support Furigana for Japanese strings that can be sorted” in [How to prepare for localization](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh967762)).</span></span>

<span data-ttu-id="2728a-174">Entweder Ihr Zielsystem oder Ihre App müssen einen Wert bereitstellen, für die `alternateform`-Qualifizierer übereinstimmen müssen.</span><span class="sxs-lookup"><span data-stu-id="2728a-174">Either your target system or your app must provide a value against which `alternateform` qualifiers are matched.</span></span> <span data-ttu-id="2728a-175">Verwenden Sie das Präfix `msft-` nicht für eigene benutzerdefinierte `alternateform` Qualifiziererwerte.</span><span class="sxs-lookup"><span data-stu-id="2728a-175">Do not use the `msft-` prefix for your own custom `alternateform` qualifier values.</span></span>

## <a name="configuration"></a><span data-ttu-id="2728a-176">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="2728a-176">Configuration</span></span>

<span data-ttu-id="2728a-177">Es ist unwahrscheinlich, dass Sie den `configuration` Qualifizierernamen benötigen.</span><span class="sxs-lookup"><span data-stu-id="2728a-177">It’s unlikely that you’ll need the `configuration` qualifier name.</span></span> <span data-ttu-id="2728a-178">Dieser dient zum Angeben von Ressourcen, die nur für eine bestimmte Umgebung zur Erstellungszeit gültig sind (beispielsweise Ressourcen zu Testzwecken).</span><span class="sxs-lookup"><span data-stu-id="2728a-178">It can be used to specify resources that are applicable only to a given authoring-time environment, such as test-only resources.</span></span>

<span data-ttu-id="2728a-179">Der Qualifizierer `configuration` wird verwendet, um eine Ressource zu laden, die am besten dem Wert der `MS_CONFIGURATION_ATTRIBUTE_VALUE`-Umgebungsvariablen entspricht.</span><span class="sxs-lookup"><span data-stu-id="2728a-179">The `configuration` qualifier is used to load a resource that best matches the value of the `MS_CONFIGURATION_ATTRIBUTE_VALUE` environment variable.</span></span> <span data-ttu-id="2728a-180">Die Variable kann auf den Zeichenfolgenwert festgelegt werden, der den relevanten Ressourcen zugewiesen wurde, beispielsweise `designer` oder `test`.</span><span class="sxs-lookup"><span data-stu-id="2728a-180">So, you can set the variable to the string value that has been assigned to the relevant resources, for example `designer`, or `test`.</span></span>

## <a name="contrast"></a><span data-ttu-id="2728a-181">Kontrast</span><span class="sxs-lookup"><span data-stu-id="2728a-181">Contrast</span></span>

<span data-ttu-id="2728a-182">Der `contrast`-Qualifizierer wird verwendet, um Ressourcen anzubieten, die den Einstellungen für hohen Kontrast am besten entsprechen.</span><span class="sxs-lookup"><span data-stu-id="2728a-182">The `contrast` qualifier is used to provide resources that best match high contrast settings.</span></span>

## <a name="custom"></a><span data-ttu-id="2728a-183">Benutzerdefiniert</span><span class="sxs-lookup"><span data-stu-id="2728a-183">Custom</span></span>

<span data-ttu-id="2728a-184">Ihre App kann einen Wert für den `custom`-Qualifizierer festlegen, wobei Ressourcen geladen werden, die am besten diesem Wert entsprechen.</span><span class="sxs-lookup"><span data-stu-id="2728a-184">Your app can set a value for the `custom` qualifier, and then resources are loaded that best match that value.</span></span> <span data-ttu-id="2728a-185">Möglicherweise möchten Sie Ressourcen basierend auf der App-Lizenz laden.</span><span class="sxs-lookup"><span data-stu-id="2728a-185">For example, you may want to load resources based on your app’s license.</span></span> <span data-ttu-id="2728a-186">Wenn die App startet, wird die Lizenz überprüft und als Wert für den `custom`-Qualifizierer durch Aufrufen von [SetGlobalQualifierValue](/uwp/api/windows.applicationmodel.resources.core.resourcecontext#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_) verwendet, wie im Codebeispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2728a-186">When your app launches, it checks its license and uses that as the value for the `custom` qualifier by calling [SetGlobalQualifierValue](/uwp/api/windows.applicationmodel.resources.core.resourcecontext#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_), as shown in the code example.</span></span>

```csharp
public void SetLicenseLevel(BrandID brand)
{
    if (brand == BrandID.Premium)
    {
        ResourceContext.SetGlobalQualifierValue("Custom", "Premium", ResourceQualifierPersistence.LocalMachine);
    }
    else if (brand == BrandID.Standard)
    {
        ResourceContext.SetGlobalQualifierValue("Custom", " Standard", ResourceQualifierPersistence.LocalMachine);
    }
    else
    {
        ResourceContext.SetGlobalQualifierValue("Custom", "Trial", ResourceQualifierPersistence.LocalMachine);
    }
}
```

<span data-ttu-id="2728a-187">In diesem Fall würden Sie Ihren Ressourcen Namen geben, die den Qualifizierer `custom-premium`, `custom-standard` und `custom-trial` enthalten.</span><span class="sxs-lookup"><span data-stu-id="2728a-187">In this scenario, you would then give your resources names that include the qualifiers `custom-premium`, `custom-standard`, and `custom-trial`.</span></span>

## <a name="devicefamily"></a><span data-ttu-id="2728a-188">Gerätefamilie</span><span class="sxs-lookup"><span data-stu-id="2728a-188">DeviceFamily</span></span>

<span data-ttu-id="2728a-189">Es ist unwahrscheinlich, dass Sie den `devicefamily` Qualifizierernamen benötigen.</span><span class="sxs-lookup"><span data-stu-id="2728a-189">It’s unlikely that you’ll need the `devicefamily` qualifier name.</span></span> <span data-ttu-id="2728a-190">Sie können und sollten die Verwendung wann immer möglich vermeiden, da es viele praktische und zuverlässige Verfahren gibt, die Sie stattdessen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2728a-190">You can and should avoid using it whenever possible because there are techniques that you can use instead that are much more convenient and robust.</span></span> <span data-ttu-id="2728a-191">Diese Techniken werden unter [Erkennen der Plattform, auf der Ihre App ausgeführt wird](../porting/wpsl-to-uwp-input-and-sensors.md#detecting-the-platform-your-app-is-running-on) und [Schreiben von Code](../get-started/universal-application-platform-guide.md#writing-code) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2728a-191">Those techniques are described in [Detecting the platform your app is running on](../porting/wpsl-to-uwp-input-and-sensors.md#detecting-the-platform-your-app-is-running-on) and [Writing code](../get-started/universal-application-platform-guide.md#writing-code).</span></span>

<span data-ttu-id="2728a-192">Als letztes Mittel ist es jedoch möglich, Gerätefamilien-Qualifizierer zum Benennen von Ordnern zu verwenden, die Ihre XAML-Ansichten enthalten (eine XAML-Ansicht ist eine XAML-Datei, die UI-Layout und Steuerelemente enthält).</span><span class="sxs-lookup"><span data-stu-id="2728a-192">But as a last resort it is possible to use devicefamily qualifiers to name folders that contain your XAML views (a XAML view is a XAML file that contains UI layout and controls).</span></span>

```
\devicefamily-desktop\<MainPage.xaml, and other markup files to load when running on a desktop computer>
\devicefamily-mobile\<MainPage.xaml, and other markup files to load when running on a phone>
```

<span data-ttu-id="2728a-193">Oder Sie können Dateien benennen.</span><span class="sxs-lookup"><span data-stu-id="2728a-193">Or you can name files.</span></span>

```
\MainPage.devicefamily-desktop.xaml
\MainPage.devicefamily-mobile.xaml
```

<span data-ttu-id="2728a-194">In jedem Fall teilt jede Kopie von `MainPage.[<qualifier>].xaml` eine gemeinsame `MainPage.xaml.cs`, die in Ihrem Projekt hinsichtlich des Namens, Speicherorts und Inhalts unverändert bleibt.</span><span class="sxs-lookup"><span data-stu-id="2728a-194">In either case each copy of `MainPage.[<qualifier>].xaml` shares a common `MainPage.xaml.cs`, which remains unchanged in your project in terms of name, location, and contents.</span></span>

<span data-ttu-id="2728a-195">Sie können ebenfalls einen Gerätefamilien-Qualifizierer verwenden, um einen Ressourcen-Dateinamen (`.resw`) oder einen Ordner zu benennen.</span><span class="sxs-lookup"><span data-stu-id="2728a-195">You can also use a devicefamily qualifier to name a Resources File (`.resw`), or folder.</span></span> <span data-ttu-id="2728a-196">Wenn Ihre App beispielsweise auf der Familie der Mobilgeräte ausgeführt wird, verwendet das UI-Element `<TextBlock x:Uid="DeviceFriendlyName"/>` die Text- und Vordergrund-Ressourcen, die in Ihrer `Resources.devicefamily-mobile.resw`-Datei enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="2728a-196">For example, when your app is running on the mobile device family, the UI element `<TextBlock x:Uid="DeviceFriendlyName"/>` will use the text and foreground resources defined in your `Resources.devicefamily-mobile.resw` file if it contains</span></span>

```xml
<data name="DeviceFriendlyName.Foreground">
    <value>Red</value>
</data>
<data name="DeviceFriendlyName.Text">
    <value>Mobile device</value>
</data>
```

<span data-ttu-id="2728a-197">Weitere Informationen zur Verwendung einer Ressourcendatei finden Sie unter [Lokalisieren Ihrer UI-Zeichenfolgen](put-ui-strings-into-resources.md).</span><span class="sxs-lookup"><span data-stu-id="2728a-197">For more on using a Resources File, see [Localize your UI strings](put-ui-strings-into-resources.md).</span></span>

## <a name="dxfeaturelevel"></a><span data-ttu-id="2728a-198">DXFeatureLevel</span><span class="sxs-lookup"><span data-stu-id="2728a-198">DXFeatureLevel</span></span>

<span data-ttu-id="2728a-199">Es ist unwahrscheinlich, dass Sie den `dxfeaturelevel` Qualifizierernamen benötigen.</span><span class="sxs-lookup"><span data-stu-id="2728a-199">It’s unlikely that you’ll need the `dxfeaturelevel` qualifier name.</span></span> <span data-ttu-id="2728a-200">Es wurde entwickelt, um mit Direct3D-Spielressourcen verwendet zu werden, um Vorgängerversionen der Ressourcen zu laden, die einer bestimmten Vorgängerversion der Hardwarekonfiguration dieser Zeit entsprechen.</span><span class="sxs-lookup"><span data-stu-id="2728a-200">It was designed to be used with Direct3D game assets, to cause downlevel resources to be loaded to match a particular downlevel hardware configuration of the time.</span></span> <span data-ttu-id="2728a-201">Aber die Verbreitung dieser Hardwarekonfiguration ist jetzt so gering, dass es empfohlen wird, dass Sie diese Qualifizierer nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="2728a-201">But the prevalence of that hardware configuration is now so low that we recommend you don’t use this qualifier.</span></span>

## <a name="homeregion"></a><span data-ttu-id="2728a-202">HomeRegion</span><span class="sxs-lookup"><span data-stu-id="2728a-202">HomeRegion</span></span>

<span data-ttu-id="2728a-203">Der `homeregion`-Qualifizierer entspricht auf der Benutzereinstellung für Land/Region.</span><span class="sxs-lookup"><span data-stu-id="2728a-203">The `homeregion` qualifier corresponds to the user’s setting for country or region.</span></span> <span data-ttu-id="2728a-204">Es stellt den Wohnort des Benutzers dar.</span><span class="sxs-lookup"><span data-stu-id="2728a-204">It represents the home location of the user.</span></span> <span data-ttu-id="2728a-205">Werte umfassen beliebig gültige [BCP-47-Regionstags](http://go.microsoft.com/fwlink/p/?linkid=227302).</span><span class="sxs-lookup"><span data-stu-id="2728a-205">Values include any valid [BCP-47 region tag](http://go.microsoft.com/fwlink/p/?linkid=227302).</span></span> <span data-ttu-id="2728a-206">D.h. jeder **ISO 3166-1-Alpha-2** Regionscode mit zwei Buchstaben sowie ein Satz **ISO 3166-1 numerischen** dreistelliger geografischer Codes für zusammengesetzte Regionen (siehe [Zusammenstellung von Regionscodes der Statistikabteilung der Vereinten Nationen (M49)](http://go.microsoft.com/fwlink/p/?linkid=247929)).</span><span class="sxs-lookup"><span data-stu-id="2728a-206">That is, any **ISO 3166-1 alpha-2** two-letter region code, plus the set of **ISO 3166-1 numeric** three-digit geographic codes for composed regions (see [United Nations Statistic Division M49 composition of region codes](http://go.microsoft.com/fwlink/p/?linkid=247929)).</span></span> <span data-ttu-id="2728a-207">Codes für bestimmte wirtschaftliche und andere Gruppierungen sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="2728a-207">Codes for "Selected economic and other groupings" are not valid.</span></span>

## <a name="language"></a><span data-ttu-id="2728a-208">Sprache</span><span class="sxs-lookup"><span data-stu-id="2728a-208">Language</span></span>

<span data-ttu-id="2728a-209">Ein `language`-Qualifizierer entspricht der Einstellung für die Anzeigesprache.</span><span class="sxs-lookup"><span data-stu-id="2728a-209">A `language` qualifier corresponds to the display language setting.</span></span> <span data-ttu-id="2728a-210">Werte umfassen beliebig gültige [BCP-47-Sprachtags](http://go.microsoft.com/fwlink/p/?linkid=227302).</span><span class="sxs-lookup"><span data-stu-id="2728a-210">Values include any valid [BCP-47 language tag](http://go.microsoft.com/fwlink/p/?linkid=227302).</span></span> <span data-ttu-id="2728a-211">Eine Liste der Sprachen finden Sie unter [IANA Language Subtag Registry](http://go.microsoft.com/fwlink/p/?linkid=227303).</span><span class="sxs-lookup"><span data-stu-id="2728a-211">For a list of languages, see the [IANA language subtag registry](http://go.microsoft.com/fwlink/p/?linkid=227303).</span></span>

<span data-ttu-id="2728a-212">Wenn Ihre App unterschiedliche Sprachen unterstützten soll und Sie Zeichenfolgenliterale im Code oder im XAML-Markup haben, verschieben Sie diese Zeichenfolgen aus dem Code/Markup und in eine Ressourcendatei (`.resw`).</span><span class="sxs-lookup"><span data-stu-id="2728a-212">If you want your app to support different display languages, and you have string literals in your code or in your XAML markup, then move those strings out of the code/markup and into a Resources File (`.resw`).</span></span> <span data-ttu-id="2728a-213">Sie können dann eine übersetzte Kopie dieser Ressourcendatei für jede Sprache erstellen, die Ihre App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2728a-213">You can then make a translated copy of that Resources File for each language that your app supports.</span></span>

<span data-ttu-id="2728a-214">Verwenden Sie in der Regel einen `language`-Qualifizierer, um die Ordner zu benennen, die die Ressourcen-Dateien enthalten (`.resw`).</span><span class="sxs-lookup"><span data-stu-id="2728a-214">You typically use a `language` qualifier to name the folders that contain your Resources Files (`.resw`).</span></span>

```
\Strings\language-en\Resources.resw
\Strings\language-ja\Resources.resw
```

<span data-ttu-id="2728a-215">Lassen Sie den `language-`-Teil des `language`-Qualifizierers aus (d.h. den Qualifizierernamen).</span><span class="sxs-lookup"><span data-stu-id="2728a-215">You can omit the `language-` part of a `language` qualifier (that is, the qualifier name).</span></span> <span data-ttu-id="2728a-216">Sie können dies nicht mit anderen Arten von Qualifizierern durchführen. Sie können dies nur in einem Ordnernamen tun.</span><span class="sxs-lookup"><span data-stu-id="2728a-216">You can’t do this with the other kinds of qualifiers; and you can only do it in a folder name.</span></span>

```
\Strings\en\Resources.resw
\Strings\ja\Resources.resw
```

<span data-ttu-id="2728a-217">Anstatt Ordner zu benennen können Sie einen `language` -Qualifizierer verwenden, um die Ressourcendateien selbst zu benennen.</span><span class="sxs-lookup"><span data-stu-id="2728a-217">Instead of naming folders, you can use `language` qualifiers to name the Resources Files themselves.</span></span>

```
\Strings\Resources.language-en.resw
\Strings\Resources.language-ja.resw
```

<span data-ttu-id="2728a-218">Unter [Lokalisieren Ihrer UI-Zeichenfolgen](put-ui-strings-into-resources.md) finden Sie weitere Informationen zum Lokalisieren Ihrer App mit Zeichenfolgenressourcen und wie Sie Ihrer App eine Zeichenfolgenressource zuweisen.</span><span class="sxs-lookup"><span data-stu-id="2728a-218">See [Localize your UI strings](put-ui-strings-into-resources.md) for more information on making your app localizable by using string resources, and how to reference a string resource in your app.</span></span>

## <a name="layoutdirection"></a><span data-ttu-id="2728a-219">LayoutDirection</span><span class="sxs-lookup"><span data-stu-id="2728a-219">LayoutDirection</span></span>

<span data-ttu-id="2728a-220">Ein `layoutdirection`-Qualifizierer entspricht der Layoutrichtung der Einstellung für die Anzeigesprache.</span><span class="sxs-lookup"><span data-stu-id="2728a-220">A `layoutdirection` qualifier corresponds to the layout direction of the display language setting.</span></span> <span data-ttu-id="2728a-221">Beispielsweise muss ein Bild für eine Rechts-nach-links-Sprache wie Arabisch oder Hebräisch unter Umständen gespiegelt werden.</span><span class="sxs-lookup"><span data-stu-id="2728a-221">For example, an image may need to be mirrored for a right-to-left language such as Arabic or Hebrew.</span></span> <span data-ttu-id="2728a-222">Layoutpanels und Bilder in Ihrer Benutzeroberfläche reagieren der Layoutrichtung entsprechend, wenn Sie deren [FlowDirection](/uwp/api/Windows.UI.Xaml.FrameworkElement?branch=live#Windows_UI_Xaml_FrameworkElement_FlowDirection)-Eigenschaft festlegen (Informationen hierzu finden Sie unter [Anpassen von Layout und Schriftarten und Unterstützen von „Von rechts nach links“](adjust-layout-and-fonts--and-support-rtl.md)).</span><span class="sxs-lookup"><span data-stu-id="2728a-222">Layout panels and images in your UI will respond to layout direction appropriately if you set their [FlowDirection](/uwp/api/Windows.UI.Xaml.FrameworkElement?branch=live#Windows_UI_Xaml_FrameworkElement_FlowDirection) property (see [Adjust layout and fonts, and support RTL](adjust-layout-and-fonts--and-support-rtl.md)).</span></span> <span data-ttu-id="2728a-223">Allerdings ist der `layoutdirection`-Qualifizierer nur für Fälle, in denen ein einfaches Kippen nicht ausreicht. Sie können auf die Ausrichtung bestimmter Leserichtungen und Textausrichtungen auf allgemeine Weise reagieren.</span><span class="sxs-lookup"><span data-stu-id="2728a-223">However, the `layoutdirection` qualifier is for cases where simple flipping isn't adequate, and it allows you to respond to the directionality of specific reading order and text alignment in more general ways.</span></span>

## <a name="scale"></a><span data-ttu-id="2728a-224">Größe anpassen</span><span class="sxs-lookup"><span data-stu-id="2728a-224">Scale</span></span>

<span data-ttu-id="2728a-225">Um die richtige Größe des Bilds für einen angegebenen Anzeige-Skalierungsfaktor zu laden, verwenden Sie einen `scale`-Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="2728a-225">To load the correct size of image for a given display scale factor, you can use a `scale` qualifier.</span></span> <span data-ttu-id="2728a-226">Dieser Qualifizierer wird üblicherweise für Bilder verwendet, die auf einem Gerät mit einem höheren DPI-Wert oder in einer vergrößerten App betrachtet werden.</span><span class="sxs-lookup"><span data-stu-id="2728a-226">This is typically used for images viewed on a higher-DPI device or when the app is zoomed.</span></span> <span data-ttu-id="2728a-227">Die Skalierung einer Ressource entspricht dem Wert von [DisplayInformation.ResolutionScale](/uwp/api/windows.graphics.display.displayinformation?branch=live#Windows_Graphics_Display_DisplayInformation_ResolutionScale) oder der Ressource mit der nächstgrößeren Skalierung.</span><span class="sxs-lookup"><span data-stu-id="2728a-227">The scale of a resource matches the value of [DisplayInformation.ResolutionScale](/uwp/api/windows.graphics.display.displayinformation?branch=live#Windows_Graphics_Display_DisplayInformation_ResolutionScale), or the next-largest-scaled resource.</span></span>

<span data-ttu-id="2728a-228">Hier ist ein Beispiel, wie Sie den Qualifizierer auf Ordnerebene festlegen.</span><span class="sxs-lookup"><span data-stu-id="2728a-228">Here’s an example of setting the qualifier at the folder level.</span></span>

```
\Assets\Images\scale-100\<logo.png, and other image files>
\Assets\Images\scale-200\<logo.png, and other image files>
\Assets\Images\scale-400\<logo.png, and other image files>
```

<span data-ttu-id="2728a-229">Und in diesem Beispiel wird er auf Dateiebene festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2728a-229">And this example sets it at the file level.</span></span>

```
\Assets\Images\logo.scale-100.png
\Assets\Images\logo.scale-200.png
\Assets\Images\logo.scale-400.png
```

<span data-ttu-id="2728a-230">Weitere Informationen zum Qualifizieren einer Ressource für `scale` und `targetsize` finden Sie unter [Qualifizieren einer Bildressource als Zielgröße](image-qualifiers-loc-scale-accessibility.md#qualify-an-image-resource-for-targetsize).</span><span class="sxs-lookup"><span data-stu-id="2728a-230">For info about qualifying a resource for both `scale` and `targetsize`, see [Qualify an image resource for targetsize](image-qualifiers-loc-scale-accessibility.md#qualify-an-image-resource-for-targetsize).</span></span>

## <a name="targetsize"></a><span data-ttu-id="2728a-231">TargetSize</span><span class="sxs-lookup"><span data-stu-id="2728a-231">TargetSize</span></span>

<span data-ttu-id="2728a-232">Der `targetsize`-Qualifizierer dient in erster Linie zum Angeben von [Dateityp-Zuordnungssymbolen](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh127427) oder [Protokollsymbolen](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/bb266530), die im Datei-Explorer angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2728a-232">The `targetsize` qualifier is primarily used to specify [file type association icons](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh127427) or [protocol icons](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/bb266530) to be shown in File Explorer.</span></span> <span data-ttu-id="2728a-233">Der Qualifiziererwert stellt die Seitenlänge eines quadratischen Bilds in unformatierten (physischen) Pixeln dar.</span><span class="sxs-lookup"><span data-stu-id="2728a-233">The qualifier value represents the side length of a square image in raw (physical) pixels.</span></span> <span data-ttu-id="2728a-234">Die Ressource, deren Wert den Einstellungseigenschaften im Datei-Explorer entspricht, wird geladen. Andernfalls wird die Ressource mit dem nächsten größten Wert geladen, wenn keine genaue Übereinstimmung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2728a-234">The resource whose value matches the View setting in File Explorer is loaded; or the resource with the next-largest value in the absence of an exact match.</span></span>

<span data-ttu-id="2728a-235">Definieren Sie Ressourcen, die verschiedene Größen des `targetsize`-Qualifiziererwerts für das App-Symbol darstellen (`/Assets/Square44x44Logo.png`) auf der Registerkarte für visuelle Ressourcen für die App-Paket-Manifest-Designer.</span><span class="sxs-lookup"><span data-stu-id="2728a-235">You can define assets that represent several sizes of `targetsize` qualifier value for the App Icon (`/Assets/Square44x44Logo.png`) in the Visual Assets tab of the app package manifest designer.</span></span>

<span data-ttu-id="2728a-236">Weitere Informationen zum Qualifizieren einer Ressource für `scale` und `targetsize` finden Sie unter [Qualifizieren einer Bildressource als Zielgröße](image-qualifiers-loc-scale-accessibility.md#qualify-an-image-resource-for-targetsize).</span><span class="sxs-lookup"><span data-stu-id="2728a-236">For info about qualifying a resource for both `scale` and `targetsize`, see [Qualify an image resource for targetsize](image-qualifiers-loc-scale-accessibility.md#qualify-an-image-resource-for-targetsize).</span></span>

## <a name="theme"></a><span data-ttu-id="2728a-237">Design</span><span class="sxs-lookup"><span data-stu-id="2728a-237">Theme</span></span>

<span data-ttu-id="2728a-238">Der `theme`-Qualifizierer wird verwendet, um Ressourcen bereitzustellen, die den Standardeinstellungen für die App am besten entsprechen oder Ihrer App mit [Application.RequestedTheme](/uwp/api/windows.ui.xaml.application?branch=master#Windows_UI_Xaml_Application_RequestedTheme) überschreiben.</span><span class="sxs-lookup"><span data-stu-id="2728a-238">The `theme` qualifier is used to provide resources that best match the default app mode setting, or your app’s override using [Application.RequestedTheme](/uwp/api/windows.ui.xaml.application?branch=master#Windows_UI_Xaml_Application_RequestedTheme).</span></span>

## <a name="related-topics"></a><span data-ttu-id="2728a-239">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2728a-239">Related topics</span></span>

* [<span data-ttu-id="2728a-240">Anzeigeskalierungsfaktor</span><span class="sxs-lookup"><span data-stu-id="2728a-240">display scale factor</span></span>](../layout/screen-sizes-and-breakpoints-for-responsive-design.md)
* [<span data-ttu-id="2728a-241">Ressourcenverwaltungssystem</span><span class="sxs-lookup"><span data-stu-id="2728a-241">Resource Management System</span></span>](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/jj552947)
* [<span data-ttu-id="2728a-242">So wird's gemacht: Vorbereiten für die Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="2728a-242">How to prepare for localization</span></span>](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh967762)
* [<span data-ttu-id="2728a-243">Erkennen der Plattform, auf der Ihre App ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="2728a-243">Detecting the platform your app is running on</span></span>](../porting/wpsl-to-uwp-input-and-sensors.md#detecting-the-platform-your-app-is-running-on)
* [<span data-ttu-id="2728a-244">Schreiben von Code</span><span class="sxs-lookup"><span data-stu-id="2728a-244">Writing code</span></span>](../get-started/universal-application-platform-guide.md#writing-code)
* [<span data-ttu-id="2728a-245">Lokalisieren der Zeichenfolgen Ihrer Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="2728a-245">Localize your UI strings</span></span>](put-ui-strings-into-resources.md)
* [<span data-ttu-id="2728a-246">BCP-47</span><span class="sxs-lookup"><span data-stu-id="2728a-246">BCP-47</span></span>](http://go.microsoft.com/fwlink/p/?linkid=227302)
* [<span data-ttu-id="2728a-247">Zusammenstellung von Regionscodes der Statistikabteilung der Vereinten Nationen (M49)</span><span class="sxs-lookup"><span data-stu-id="2728a-247">United Nations Statistic Division M49 composition of region codes</span></span>](http://go.microsoft.com/fwlink/p/?linkid=247929)
* [<span data-ttu-id="2728a-248">IANA Language Subtag Registry</span><span class="sxs-lookup"><span data-stu-id="2728a-248">IANA language subtag registry</span></span>](http://go.microsoft.com/fwlink/p/?linkid=227303)
* [<span data-ttu-id="2728a-249">Anpassen von Layout und Schriftarten und Unterstützen von „Von rechts nach links“</span><span class="sxs-lookup"><span data-stu-id="2728a-249">Adjust layout and fonts, and support RTL</span></span>](adjust-layout-and-fonts--and-support-rtl.md)