---
author: Jwmsft
Description: "Bei Designressourcen in XAML handelt es sich um einen Satz von Ressourcen, die abhängig vom aktiven Systemdesign verschiedene Werte anwenden."
MS-HAID: dev\_ctrl\_layout\_txt.xaml\_theme\_resources
MSHAttr: PreferredLib:/library/windows/apps
Search.Product: eADQiWindows 10XVcnh
title: XAML-Designressourcen
ms.assetid: 41B87DBF-E7A2-44E9-BEBA-AF6EEBABB81B
label: XAML theme resources
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 74b16b95e1ca4e8583efa2b4967e2287c4cf5ffb
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="xaml-theme-resources"></a><span data-ttu-id="bd62e-104">XAML-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="bd62e-104">XAML theme resources</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="bd62e-105">Bei Designressourcen in XAML handelt es sich um einen Satz von Ressourcen, die abhängig vom aktiven Systemdesign verschiedene Werte anwenden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-105">Theme resources in XAML are a set of resources that apply different values depending on which system theme is active.</span></span> <span data-ttu-id="bd62e-106">Es gibt drei Designs, die das XAML-Framework unterstützt: „Light“, „Dark“ und „HighContrast“.</span><span class="sxs-lookup"><span data-stu-id="bd62e-106">There are 3 themes that the XAML framework supports: "Light", "Dark", and "HighContrast".</span></span>

**<span data-ttu-id="bd62e-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="bd62e-107">Prerequisites</span></span>**

<span data-ttu-id="bd62e-108">In diesem Thema wird vorausgesetzt, dass Sie [ResourceDictionary- und XAML-Ressourcenreferenzen](resourcedictionary-and-xaml-resource-references.md) gelesen haben.</span><span class="sxs-lookup"><span data-stu-id="bd62e-108">This topic assumes that you have read [ResourceDictionary and XAML resource references](resourcedictionary-and-xaml-resource-references.md).</span></span>

## <a name="how-theme-resources-differ-from-static-resources"></a><span data-ttu-id="bd62e-109">Unterschiede zwischen Designressourcen und statischen Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bd62e-109">How theme resources differ from static resources</span></span>

<span data-ttu-id="bd62e-110">Es gibt zwei XAML-Markuperweiterungen, die aus einem vorhandenen XAML-Ressourcenverzeichnis auf eine XAML-Ressource verweisen können: die [{StaticResource}-Markuperweiterung](../xaml-platform/staticresource-markup-extension.md) und die [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="bd62e-110">There are two XAML markup extensions that can reference a XAML resource from an existing XAML resource dictionary: [{StaticResource} markup extension](../xaml-platform/staticresource-markup-extension.md) and [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md).</span></span>

<span data-ttu-id="bd62e-111">Die Auswertung einer [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md) tritt beim Laden der App und anschließend bei jeder Änderung des Designs zur Laufzeit auf.</span><span class="sxs-lookup"><span data-stu-id="bd62e-111">Evaluation of a [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md) occurs when the app loads and subsequently each time the theme changes at runtime.</span></span> <span data-ttu-id="bd62e-112">Dies ist in der Regel das Ergebnis des Änderns der Geräteeinstellungen durch den Benutzer oder einer programmgesteuerten Änderung in der App, die das aktuelle Design ändert.</span><span class="sxs-lookup"><span data-stu-id="bd62e-112">This is typically the result of the user changing their device settings or from a programmatic change within the app that alters its current theme.</span></span>

<span data-ttu-id="bd62e-113">Für eine [{StaticResource}-Markuperweiterung](../xaml-platform/staticresource-markup-extension.md) erfolgt eine Auswertung hingegen nur, wenn die XAML zuerst von der App geladen wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-113">In contrast, a [{StaticResource} markup extension](../xaml-platform/staticresource-markup-extension.md) is evaluated only when the XAML is first loaded by the app.</span></span> <span data-ttu-id="bd62e-114">Es findet keine Aktualisierung statt.</span><span class="sxs-lookup"><span data-stu-id="bd62e-114">It does not update.</span></span> <span data-ttu-id="bd62e-115">Dies ähnelt dem Suchen und Ersetzen in XAML mit dem tatsächlichen Laufzeitwert beim Start der App.</span><span class="sxs-lookup"><span data-stu-id="bd62e-115">It’s similar to a find and replace in your XAML with the actual runtime value at app launch.</span></span>

## <a name="theme-resources-and-where-they-fit-in-the-resource-dictionary-structure"></a><span data-ttu-id="bd62e-116">Designressourcen und deren Verwendung in der Ressourcenverzeichnisstruktur</span><span class="sxs-lookup"><span data-stu-id="bd62e-116">Theme resources and where they fit in the resource dictionary structure</span></span>


<span data-ttu-id="bd62e-117">Jede Designressource ist Teil der XAML-Datei „themeresources.xaml“.</span><span class="sxs-lookup"><span data-stu-id="bd62e-117">Each theme resource is part of the XAML file themeresources.xaml.</span></span> <span data-ttu-id="bd62e-118">Zu Designzwecken steht „themeresources.xaml“ im Order „\\(Programme)\\Windows Kits\\10\\DesignTime\\CommonConfiguration\\Neutral\\UAP\\&lt;SDK version&gt;\\Generic“ aus einer Windows Software Development Kit (SDK)-Installation zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="bd62e-118">For design purposes, themeresources.xaml is available in the \\(Program Files)\\Windows Kits\\10\\DesignTime\\CommonConfiguration\\Neutral\\UAP\\&lt;SDK version&gt;\\Generic folder from a Windows Software Development Kit (SDK) installation.</span></span> <span data-ttu-id="bd62e-119">Die Ressourcenverzeichnisse in „themeresources.xaml“ werden auch in „generic.xaml“ im selben Verzeichnis reproduziert.</span><span class="sxs-lookup"><span data-stu-id="bd62e-119">The resource dictionaries in themeresources.xaml are also reproduced in generic.xaml in the same directory.</span></span>

> <span data-ttu-id="bd62e-120">**Hinweis**&nbsp;&nbsp;Die Windows-Runtime verwendet diese physischen Dateien nicht für die Runtime-Suche.</span><span class="sxs-lookup"><span data-stu-id="bd62e-120">**Note**&nbsp;&nbsp;The Windows Runtime doesn't use these physical files for runtime lookup.</span></span> <span data-ttu-id="bd62e-121">Daher befinden sie sich in einem speziellen DesignTime-Ordner und werden nicht standardmäßig in Apps kopiert.</span><span class="sxs-lookup"><span data-stu-id="bd62e-121">That's why they are specifically in a DesignTime folder, and they aren't copied into apps by default.</span></span> <span data-ttu-id="bd62e-122">Stattdessen sind die Ressourcenverzeichnisse als Teil der Windows-Runtime selbst im Speicher vorhanden, und die XAML-Ressource Ihrer App verweist auf Designressourcen (oder Systemressourcen), die dort zu Laufzeit aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-122">Instead, these resource dictionaries exist in memory as part of the Windows Runtime itself, and your app's XAML resource references to theme resources (or system resources) resolve there at runtime.</span></span>

 ## <a name="guidelines-for-using-theme-resources"></a><span data-ttu-id="bd62e-123">Richtlinien für die Verwendung von Designressourcen</span><span class="sxs-lookup"><span data-stu-id="bd62e-123">Guidelines for using theme resources</span></span>

<span data-ttu-id="bd62e-124">Halten Sie sich an die folgenden Richtlinien, wenn Sie Ihre eigenen benutzerdefinierten Designressourcen definieren und verwenden:</span><span class="sxs-lookup"><span data-stu-id="bd62e-124">Follow these guidelines when you define and consume your own custom theme resources.</span></span>

<span data-ttu-id="bd62e-125">EMPFOHLEN:</span><span class="sxs-lookup"><span data-stu-id="bd62e-125">DO:</span></span>

-   <span data-ttu-id="bd62e-126">Geben Sie zusätzlich zum Verzeichnis „HighContrast“ jeweils ein Designverzeichnis für „Light“ und „Dark“ an.</span><span class="sxs-lookup"><span data-stu-id="bd62e-126">Specify theme dictionaries for both "Light" and "Dark" in addition to your "HighContrast" dictionary.</span></span> <span data-ttu-id="bd62e-127">Sie können zwar ein [ResourceDictionary](https://msdn.microsoft.com/library/windows/apps/br208794)-Element mit „Default“ als Schlüssel erstellen, es empfiehlt sich jedoch, explizit vorzugehen und stattdessen „Light“, „Dark“ und „HighContrast“ zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-127">Although you can create a [ResourceDictionary](https://msdn.microsoft.com/library/windows/apps/br208794) with "Default" as the key, it’s preferred to be explicit and instead use "Light", "Dark", and "HighContrast".</span></span>
-   <span data-ttu-id="bd62e-128">Verwenden Sie die [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md) in Stilen, Settern, Steuerelementvorlagen, Settern für Eigenschaften und Animationen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-128">Use the [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md) in: Styles, Setters, Control templates, Property setters, and Animations.</span></span>

<span data-ttu-id="bd62e-129">NICHT EMPFOHLEN:</span><span class="sxs-lookup"><span data-stu-id="bd62e-129">DO NOT:</span></span>

-   <span data-ttu-id="bd62e-130">Verwenden Sie die [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md) nicht in Ihren Ressourcendefinitionen in [ThemeDictionaries](https://msdn.microsoft.com/library/windows/apps/br208807).</span><span class="sxs-lookup"><span data-stu-id="bd62e-130">Use the [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md) in your resource definitions inside your [ThemeDictionaries](https://msdn.microsoft.com/library/windows/apps/br208807).</span></span> <span data-ttu-id="bd62e-131">Verwenden Sie stattdessen die [{StaticResource}-Markuperweiterung](../xaml-platform/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="bd62e-131">Use [{StaticResource} markup extension](../xaml-platform/staticresource-markup-extension.md) instead.</span></span>

    <span data-ttu-id="bd62e-132">AUSNAHME: Sie können die [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md) verwenden, um auf Ressourcen zu verweisen, die in Bezug auf das App-Design in [ThemeDictionaries](https://msdn.microsoft.com/library/windows/apps/br208807) agnostisch sind.</span><span class="sxs-lookup"><span data-stu-id="bd62e-132">EXCEPTION: it is alright to use the [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md) to reference resources that are agnostic to the app theme in your [ThemeDictionaries](https://msdn.microsoft.com/library/windows/apps/br208807).</span></span> <span data-ttu-id="bd62e-133">Beispiele für diese Ressourcen sind Akzentfarbenressourcen wie `SystemAccentColor` oder Systemfarbenressourcen, die normalerweise das Präfix „SystemColor“ haben, z.B. `SystemColorButtonFaceColor`.</span><span class="sxs-lookup"><span data-stu-id="bd62e-133">Examples of these resources are accent color resources like `SystemAccentColor`, or system color resources, which are typically prefixed with "SystemColor" like `SystemColorButtonFaceColor`.</span></span>

<span data-ttu-id="bd62e-134">**Achtung**  Wenn Sie diesen Richtlinien nicht folgen, kann ein unerwartetes Verhalten im Zusammenhang mit Designs in Ihrer App auftreten.</span><span class="sxs-lookup"><span data-stu-id="bd62e-134">**Caution**  If you don’t follow these guidelines, you might see unexpected behavior related to themes in your app.</span></span> <span data-ttu-id="bd62e-135">Weitere Informationen finden Sie im Abschnitt [Problembehandlung für Designressourcen](#troubleshooting-theme-resources).</span><span class="sxs-lookup"><span data-stu-id="bd62e-135">For more info, see the [Troubleshooting theme resources](#troubleshooting-theme-resources) section.</span></span>
 

## <a name="the-xaml-color-ramp-and-theme-dependent-brushes"></a><span data-ttu-id="bd62e-136">Die XAML-Farbskala und designabhängige Pinsel</span><span class="sxs-lookup"><span data-stu-id="bd62e-136">The XAML color ramp and theme-dependent brushes</span></span>

<span data-ttu-id="bd62e-137">Die kombinierte Gruppe von Farben für die Designs „Light“, „Dark“ und „HighContrast“ bilden die *Windows-Farbskala* in XAML.</span><span class="sxs-lookup"><span data-stu-id="bd62e-137">The combined set of colors for "Light", "Dark", and "HighContrast" themes make up the *Windows color ramp* in XAML.</span></span> <span data-ttu-id="bd62e-138">Egal, ob Sie die Systemdesigns ändern oder ein Systemdesign auf Ihre eigenen XAML-Elemente anwenden möchten, ist es wichtig zu verstehen, wie die Farbressourcen strukturiert werden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-138">Whether you want to modify the system themes, or apply a system theme to your own XAML elements, it’s important to understand how the color resources are structured.</span></span>

### <a name="light-and-dark-theme-colors"></a><span data-ttu-id="bd62e-139">Helle und dunkle Designfarben</span><span class="sxs-lookup"><span data-stu-id="bd62e-139">Light and Dark theme colors</span></span>

<span data-ttu-id="bd62e-140">Das XAML-Framework stellt eine Gruppe von benannten [Color](https://msdn.microsoft.com/library/windows/apps/hh673723)-Ressourcen mit Werten bereiten, die speziell auf die Designs „Light“ und „Dark“ zugeschnitten sind.</span><span class="sxs-lookup"><span data-stu-id="bd62e-140">The XAML framework provides a set of named [Color](https://msdn.microsoft.com/library/windows/apps/hh673723) resources with values that are tailored for the "Light" and "Dark" themes.</span></span> <span data-ttu-id="bd62e-141">Die Schlüssel, die Sie zum Verweisen verwenden, haben folgendes Namensformat: `System[Simple Light/Dark Name]Color`.</span><span class="sxs-lookup"><span data-stu-id="bd62e-141">The keys you use to reference these follow the naming format: `System[Simple Light/Dark Name]Color`.</span></span>

<span data-ttu-id="bd62e-142">Diese Tabelle enthält den Schlüssel, den einfachen Namen und die Zeichenfolgendarstellung der Farbe (mit dem \#aarrggbb-Format) für die Ressourcen „Light“ und „Dark“, die vom XAML-Framework bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-142">This table lists the key, simple name, and string representation of the color (using the \#aarrggbb format) for the "Light" and "Dark" resources provided by the XAML framework.</span></span> <span data-ttu-id="bd62e-143">Der Schlüssel wird verwendet, um auf die Ressource in einer App zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-143">The key is used to reference the resource in an app.</span></span> <span data-ttu-id="bd62e-144">Der einfache Name für hell/dunkel dient als Teil der Pinselbenennungskonvention, die später erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-144">The "Simple light/dark name" is used as part of the brush naming convention that we explain later.</span></span>

| <span data-ttu-id="bd62e-145">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="bd62e-145">Key</span></span>                             | <span data-ttu-id="bd62e-146">Einfacher Name für hell/dunkel</span><span class="sxs-lookup"><span data-stu-id="bd62e-146">Simple light/dark name</span></span> | <span data-ttu-id="bd62e-147">Light</span><span class="sxs-lookup"><span data-stu-id="bd62e-147">Light</span></span>      | <span data-ttu-id="bd62e-148">Dark</span><span class="sxs-lookup"><span data-stu-id="bd62e-148">Dark</span></span>       |
|---------------------------------|------------------------|------------|------------|
| <span data-ttu-id="bd62e-149">SystemAltHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-149">SystemAltHighColor</span></span>              | <span data-ttu-id="bd62e-150">AltHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-150">AltHigh</span></span>                | <span data-ttu-id="bd62e-151">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-151">\#FFFFFFFF</span></span> | <span data-ttu-id="bd62e-152">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-152">\#FF000000</span></span> |
| <span data-ttu-id="bd62e-153">SystemAltLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-153">SystemAltLowColor</span></span>               | <span data-ttu-id="bd62e-154">AltLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-154">AltLow</span></span>                 | <span data-ttu-id="bd62e-155">\#33FFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-155">\#33FFFFFF</span></span> | <span data-ttu-id="bd62e-156">\#33000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-156">\#33000000</span></span> |
| <span data-ttu-id="bd62e-157">SystemAltMediumColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-157">SystemAltMediumColor</span></span>            | <span data-ttu-id="bd62e-158">AltMedium</span><span class="sxs-lookup"><span data-stu-id="bd62e-158">AltMedium</span></span>              | <span data-ttu-id="bd62e-159">\#99FFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-159">\#99FFFFFF</span></span> | <span data-ttu-id="bd62e-160">\#99000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-160">\#99000000</span></span> |
| <span data-ttu-id="bd62e-161">SystemAltMediumHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-161">SystemAltMediumHighColor</span></span>        | <span data-ttu-id="bd62e-162">AltMediumHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-162">AltMediumHigh</span></span>          | <span data-ttu-id="bd62e-163">\#CCFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-163">\#CCFFFFFF</span></span> | <span data-ttu-id="bd62e-164">\#CC000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-164">\#CC000000</span></span> |
| <span data-ttu-id="bd62e-165">SystemAltMediumLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-165">SystemAltMediumLowColor</span></span>         | <span data-ttu-id="bd62e-166">AltMediumLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-166">AltMediumLow</span></span>           | <span data-ttu-id="bd62e-167">\#66FFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-167">\#66FFFFFF</span></span> | <span data-ttu-id="bd62e-168">\#66000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-168">\#66000000</span></span> |
| <span data-ttu-id="bd62e-169">SystemBaseHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-169">SystemBaseHighColor</span></span>             | <span data-ttu-id="bd62e-170">BaseHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-170">BaseHigh</span></span>               | <span data-ttu-id="bd62e-171">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-171">\#FF000000</span></span> | <span data-ttu-id="bd62e-172">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-172">\#FFFFFFFF</span></span> |
| <span data-ttu-id="bd62e-173">SystemBaseLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-173">SystemBaseLowColor</span></span>              | <span data-ttu-id="bd62e-174">BaseLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-174">BaseLow</span></span>                | <span data-ttu-id="bd62e-175">\#33000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-175">\#33000000</span></span> | <span data-ttu-id="bd62e-176">\#33FFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-176">\#33FFFFFF</span></span> |
| <span data-ttu-id="bd62e-177">SystemBaseMediumColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-177">SystemBaseMediumColor</span></span>           | <span data-ttu-id="bd62e-178">BaseMedium</span><span class="sxs-lookup"><span data-stu-id="bd62e-178">BaseMedium</span></span>             | <span data-ttu-id="bd62e-179">\#99000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-179">\#99000000</span></span> | <span data-ttu-id="bd62e-180">\#99FFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-180">\#99FFFFFF</span></span> |
| <span data-ttu-id="bd62e-181">SystemBaseMediumHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-181">SystemBaseMediumHighColor</span></span>       | <span data-ttu-id="bd62e-182">BaseMediumHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-182">BaseMediumHigh</span></span>         | <span data-ttu-id="bd62e-183">\#CC000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-183">\#CC000000</span></span> | <span data-ttu-id="bd62e-184">\#CCFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-184">\#CCFFFFFF</span></span> |
| <span data-ttu-id="bd62e-185">SystemBaseMediumLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-185">SystemBaseMediumLowColor</span></span>        | <span data-ttu-id="bd62e-186">BaseMediumLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-186">BaseMediumLow</span></span>          | <span data-ttu-id="bd62e-187">\#66000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-187">\#66000000</span></span> | <span data-ttu-id="bd62e-188">\#66FFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-188">\#66FFFFFF</span></span> |
| <span data-ttu-id="bd62e-189">SystemChromeAltLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-189">SystemChromeAltLowColor</span></span>         | <span data-ttu-id="bd62e-190">ChromeAltLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-190">ChromeAltLow</span></span>           | <span data-ttu-id="bd62e-191">\#FF171717</span><span class="sxs-lookup"><span data-stu-id="bd62e-191">\#FF171717</span></span> | <span data-ttu-id="bd62e-192">\#FFF2F2F2</span><span class="sxs-lookup"><span data-stu-id="bd62e-192">\#FFF2F2F2</span></span> |
| <span data-ttu-id="bd62e-193">SystemChromeBlackHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-193">SystemChromeBlackHighColor</span></span>      | <span data-ttu-id="bd62e-194">ChromeBlackHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-194">ChromeBlackHigh</span></span>        | <span data-ttu-id="bd62e-195">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-195">\#FF000000</span></span> | <span data-ttu-id="bd62e-196">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-196">\#FF000000</span></span> |
| <span data-ttu-id="bd62e-197">SystemChromeBlackLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-197">SystemChromeBlackLowColor</span></span>       | <span data-ttu-id="bd62e-198">ChromeBlackLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-198">ChromeBlackLow</span></span>         | <span data-ttu-id="bd62e-199">\#33000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-199">\#33000000</span></span> | <span data-ttu-id="bd62e-200">\#33000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-200">\#33000000</span></span> |
| <span data-ttu-id="bd62e-201">SystemChromeBlackMediumLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-201">SystemChromeBlackMediumLowColor</span></span> | <span data-ttu-id="bd62e-202">ChromeBlackMediumLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-202">ChromeBlackMediumLow</span></span>   | <span data-ttu-id="bd62e-203">\#66000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-203">\#66000000</span></span> | <span data-ttu-id="bd62e-204">\#66000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-204">\#66000000</span></span> |
| <span data-ttu-id="bd62e-205">SystemChromeBlackMediumColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-205">SystemChromeBlackMediumColor</span></span>    | <span data-ttu-id="bd62e-206">ChromeBlackMedium</span><span class="sxs-lookup"><span data-stu-id="bd62e-206">ChromeBlackMedium</span></span>      | <span data-ttu-id="bd62e-207">\#CC000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-207">\#CC000000</span></span> | <span data-ttu-id="bd62e-208">\#CC000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-208">\#CC000000</span></span> |
| <span data-ttu-id="bd62e-209">SystemChromeDisabledHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-209">SystemChromeDisabledHighColor</span></span>   | <span data-ttu-id="bd62e-210">ChromeDisabledHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-210">ChromeDisabledHigh</span></span>     | <span data-ttu-id="bd62e-211">\#FFCCCCCC</span><span class="sxs-lookup"><span data-stu-id="bd62e-211">\#FFCCCCCC</span></span> | <span data-ttu-id="bd62e-212">\#FF333333</span><span class="sxs-lookup"><span data-stu-id="bd62e-212">\#FF333333</span></span> |
| <span data-ttu-id="bd62e-213">SystemChromeDisabledLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-213">SystemChromeDisabledLowColor</span></span>    | <span data-ttu-id="bd62e-214">ChromeDisabledLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-214">ChromeDisabledLow</span></span>      | <span data-ttu-id="bd62e-215">\#FF7A7A7A</span><span class="sxs-lookup"><span data-stu-id="bd62e-215">\#FF7A7A7A</span></span> | <span data-ttu-id="bd62e-216">\#FF858585</span><span class="sxs-lookup"><span data-stu-id="bd62e-216">\#FF858585</span></span> |
| <span data-ttu-id="bd62e-217">SystemChromeHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-217">SystemChromeHighColor</span></span>           | <span data-ttu-id="bd62e-218">ChromeHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-218">ChromeHigh</span></span>             | <span data-ttu-id="bd62e-219">\#FFCCCCCC</span><span class="sxs-lookup"><span data-stu-id="bd62e-219">\#FFCCCCCC</span></span> | <span data-ttu-id="bd62e-220">\#FF767676</span><span class="sxs-lookup"><span data-stu-id="bd62e-220">\#FF767676</span></span> |
| <span data-ttu-id="bd62e-221">SystemChromeLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-221">SystemChromeLowColor</span></span>            | <span data-ttu-id="bd62e-222">ChromeLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-222">ChromeLow</span></span>              | <span data-ttu-id="bd62e-223">\#FFF2F2F2</span><span class="sxs-lookup"><span data-stu-id="bd62e-223">\#FFF2F2F2</span></span> | <span data-ttu-id="bd62e-224">\#FF171717</span><span class="sxs-lookup"><span data-stu-id="bd62e-224">\#FF171717</span></span> |
| <span data-ttu-id="bd62e-225">SystemChromeMediumColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-225">SystemChromeMediumColor</span></span>         | <span data-ttu-id="bd62e-226">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="bd62e-226">ChromeMedium</span></span>           | <span data-ttu-id="bd62e-227">\#FFE6E6E6</span><span class="sxs-lookup"><span data-stu-id="bd62e-227">\#FFE6E6E6</span></span> | <span data-ttu-id="bd62e-228">\#FF1F1F1F</span><span class="sxs-lookup"><span data-stu-id="bd62e-228">\#FF1F1F1F</span></span> |
| <span data-ttu-id="bd62e-229">SystemChromeMediumLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-229">SystemChromeMediumLowColor</span></span>      | <span data-ttu-id="bd62e-230">ChromeMediumLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-230">ChromeMediumLow</span></span>        | <span data-ttu-id="bd62e-231">\#FFF2F2F2</span><span class="sxs-lookup"><span data-stu-id="bd62e-231">\#FFF2F2F2</span></span> | <span data-ttu-id="bd62e-232">\#FF2B2B2B</span><span class="sxs-lookup"><span data-stu-id="bd62e-232">\#FF2B2B2B</span></span> |
| <span data-ttu-id="bd62e-233">SystemChromeWhiteColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-233">SystemChromeWhiteColor</span></span>          | <span data-ttu-id="bd62e-234">ChromeWhite</span><span class="sxs-lookup"><span data-stu-id="bd62e-234">ChromeWhite</span></span>            | <span data-ttu-id="bd62e-235">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-235">\#FFFFFFFF</span></span> | <span data-ttu-id="bd62e-236">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-236">\#FFFFFFFF</span></span> |
| <span data-ttu-id="bd62e-237">SystemListLowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-237">SystemListLowColor</span></span>              | <span data-ttu-id="bd62e-238">ListLow</span><span class="sxs-lookup"><span data-stu-id="bd62e-238">ListLow</span></span>                | <span data-ttu-id="bd62e-239">\#19000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-239">\#19000000</span></span> | <span data-ttu-id="bd62e-240">\#19FFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-240">\#19FFFFFF</span></span> |
| <span data-ttu-id="bd62e-241">SystemListMediumColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-241">SystemListMediumColor</span></span>           | <span data-ttu-id="bd62e-242">ListMedium</span><span class="sxs-lookup"><span data-stu-id="bd62e-242">ListMedium</span></span>             | <span data-ttu-id="bd62e-243">\#33000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-243">\#33000000</span></span> | <span data-ttu-id="bd62e-244">\#33FFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-244">\#33FFFFFF</span></span> |


### <a name="windows-system-high-contrast-colors"></a><span data-ttu-id="bd62e-245">Windows-Systemfarben mit hohem Kontrast</span><span class="sxs-lookup"><span data-stu-id="bd62e-245">Windows system high-contrast colors</span></span>

<span data-ttu-id="bd62e-246">Zusätzlich zu den Ressourcen, die vom XAML-Framework bereitgestellt werden, gibt es eine Reihe von Farbwerten, die von der Windows-Systempalette abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-246">In addition to the set of resources provided by the XAML framework, there's a set of color values derived from the Windows system palette.</span></span> <span data-ttu-id="bd62e-247">Diese Farben werden nicht speziell für die Windows-Runtime- oder universelle Windows-Plattform-App (UWP) verwendet.</span><span class="sxs-lookup"><span data-stu-id="bd62e-247">These colors are not specific to the Windows Runtime or Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="bd62e-248">Viele der XAML-[Brush](https://msdn.microsoft.com/library/windows/apps/br228076)-Ressourcen verwenden diese Farben jedoch, wenn das System mit dem Design „HighContrast“ betrieben wird (und die App ausgeführt wird).</span><span class="sxs-lookup"><span data-stu-id="bd62e-248">However, many of the XAML [Brush](https://msdn.microsoft.com/library/windows/apps/br228076) resources consume these colors when the system is operating (and the app is running) using the "HighContrast" theme.</span></span> <span data-ttu-id="bd62e-249">Das XAML-Framework stellt diese systemweiten Farben als Ressourcen mit Schlüssel bereit.</span><span class="sxs-lookup"><span data-stu-id="bd62e-249">The XAML framework provides these system-wide colors as keyed resources.</span></span> <span data-ttu-id="bd62e-250">Die Schlüssel folgen diesem Benennungsformat: `SystemColor[name]Color`.</span><span class="sxs-lookup"><span data-stu-id="bd62e-250">The keys follow the naming format: `SystemColor[name]Color`.</span></span>

<span data-ttu-id="bd62e-251">Diese Tabelle enthält die systemweiten Farben, die XAML als Ressourcenobjekte aus der Windows-Systempalette abgeleitet bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="bd62e-251">This table lists the system-wide colors that XAML provides as resource objects derived from the Windows system palette.</span></span> <span data-ttu-id="bd62e-252">In der Spalte „Name der erleichterten Bedienung“ wird gezeigt, wie Farben in der Windows-Einstellungs-UI beschriftet werden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-252">The "Ease of Access name" column shows how color is labeled in the Windows settings UI.</span></span> <span data-ttu-id="bd62e-253">In der Spalte „Einfacher Name für HighContrast“ wird mit einem Wort beschrieben, wie die Farbe für die allgemeinen XAML-Steuerelemente angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-253">The "Simple HighContrast name" column is a one word description of how the color is applied across the XAML common controls.</span></span> <span data-ttu-id="bd62e-254">Sie wird als Teil der Pinselbenennungskonvention verwendet, die später erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-254">It's used as part of the brush naming convention that we explain later.</span></span> <span data-ttu-id="bd62e-255">Die in der Spalte „Anfänglicher Standardwert“ aufgeführten Werte erhalten Sie, wenn das System nicht mit hohem Kontrast ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-255">The "Initial default" column shows the values you'd get if the system is not running in high contrast at all.</span></span>

| <span data-ttu-id="bd62e-256">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="bd62e-256">Key</span></span>                           | <span data-ttu-id="bd62e-257">Name der erleichterten Bedienung</span><span class="sxs-lookup"><span data-stu-id="bd62e-257">Ease of Access name</span></span>            | <span data-ttu-id="bd62e-258">Einfacher Name für HighContrast</span><span class="sxs-lookup"><span data-stu-id="bd62e-258">Simple HighContrast name</span></span> | <span data-ttu-id="bd62e-259">Anfänglicher Standardwert</span><span class="sxs-lookup"><span data-stu-id="bd62e-259">Initial default</span></span> |
|-------------------------------|--------------------------------|--------------------------|-----------------|
| <span data-ttu-id="bd62e-260">SystemColorButtonFaceColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-260">SystemColorButtonFaceColor</span></span>    | <span data-ttu-id="bd62e-261">**Text der Schaltfläche** (Hintergrund)</span><span class="sxs-lookup"><span data-stu-id="bd62e-261">**Button Text** (background)</span></span>   | <span data-ttu-id="bd62e-262">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="bd62e-262">Background</span></span>               | <span data-ttu-id="bd62e-263">\#FFF0F0F0</span><span class="sxs-lookup"><span data-stu-id="bd62e-263">\#FFF0F0F0</span></span>      |
| <span data-ttu-id="bd62e-264">SystemColorButtonTextColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-264">SystemColorButtonTextColor</span></span>    | <span data-ttu-id="bd62e-265">**Text der Schaltfläche** (Vordergrund)</span><span class="sxs-lookup"><span data-stu-id="bd62e-265">**Button Text** (foreground)</span></span>   | <span data-ttu-id="bd62e-266">Vordergrund</span><span class="sxs-lookup"><span data-stu-id="bd62e-266">Foreground</span></span>               | <span data-ttu-id="bd62e-267">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-267">\#FF000000</span></span>      |
| <span data-ttu-id="bd62e-268">SystemColorGrayTextColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-268">SystemColorGrayTextColor</span></span>      | **<span data-ttu-id="bd62e-269">Deaktivierter Text</span><span class="sxs-lookup"><span data-stu-id="bd62e-269">Disabled Text</span></span>**              | <span data-ttu-id="bd62e-270">Deaktiviert</span><span class="sxs-lookup"><span data-stu-id="bd62e-270">Disabled</span></span>                 | <span data-ttu-id="bd62e-271">\#FF6D6D6D</span><span class="sxs-lookup"><span data-stu-id="bd62e-271">\#FF6D6D6D</span></span>      |
| <span data-ttu-id="bd62e-272">SystemColorHighlightColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-272">SystemColorHighlightColor</span></span>     | <span data-ttu-id="bd62e-273">**Ausgewählter Text** (Hintergrund)</span><span class="sxs-lookup"><span data-stu-id="bd62e-273">**Selected Text** (background)</span></span> | <span data-ttu-id="bd62e-274">Hervorheben</span><span class="sxs-lookup"><span data-stu-id="bd62e-274">Highlight</span></span>                | <span data-ttu-id="bd62e-275">\#FF3399FF</span><span class="sxs-lookup"><span data-stu-id="bd62e-275">\#FF3399FF</span></span>      |
| <span data-ttu-id="bd62e-276">SystemColorHighlightTextColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-276">SystemColorHighlightTextColor</span></span> | <span data-ttu-id="bd62e-277">**Ausgewählter Text** (Vordergrund)</span><span class="sxs-lookup"><span data-stu-id="bd62e-277">**Selected Text** (foreground)</span></span> | <span data-ttu-id="bd62e-278">HighlightAlt</span><span class="sxs-lookup"><span data-stu-id="bd62e-278">HighlightAlt</span></span>             | <span data-ttu-id="bd62e-279">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-279">\#FFFFFFFF</span></span>      |
| <span data-ttu-id="bd62e-280">SystemColorHotlightColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-280">SystemColorHotlightColor</span></span>      | **<span data-ttu-id="bd62e-281">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="bd62e-281">Hyperlinks</span></span>**                 | <span data-ttu-id="bd62e-282">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="bd62e-282">Hyperlink</span></span>                | <span data-ttu-id="bd62e-283">\#FF0066CC</span><span class="sxs-lookup"><span data-stu-id="bd62e-283">\#FF0066CC</span></span>      |
| <span data-ttu-id="bd62e-284">SystemColorWindowColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-284">SystemColorWindowColor</span></span>        | **<span data-ttu-id="bd62e-285">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="bd62e-285">Background</span></span>**                 | <span data-ttu-id="bd62e-286">PageBackground</span><span class="sxs-lookup"><span data-stu-id="bd62e-286">PageBackground</span></span>           | <span data-ttu-id="bd62e-287">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-287">\#FFFFFFFF</span></span>      |
| <span data-ttu-id="bd62e-288">SystemColorWindowTextColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-288">SystemColorWindowTextColor</span></span>    | **<span data-ttu-id="bd62e-289">Text</span><span class="sxs-lookup"><span data-stu-id="bd62e-289">Text</span></span>**                       | <span data-ttu-id="bd62e-290">PageText</span><span class="sxs-lookup"><span data-stu-id="bd62e-290">PageText</span></span>                 | <span data-ttu-id="bd62e-291">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-291">\#FF000000</span></span>      |


<span data-ttu-id="bd62e-292">Windows bietet verschiedene kontrastreiche Designs und ermöglicht es dem Benutzer, für ihre Einstellungen für hohen Kontrast durch das Center für erleichterte Bedienung die spezifischen Farben festzulegen, wie hier gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-292">Windows provides different high-contrast themes, and enables the user to set the specific colors to for their high-contrast settings through the Ease of Access Center, as shown here.</span></span> <span data-ttu-id="bd62e-293">Daher ist es nicht möglich, eine definitive Liste der Farbwerte mit hohem Kontrast bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-293">Therefore, it's not possible to provide a definitive list of high-contrast color values.</span></span>

![Die Windows-Einstellungs-UI für hohen Kontrast](images/high-contrast-settings.png)

<span data-ttu-id="bd62e-295">Weitere Informationen zum Unterstützen von Designs mit hohem Kontrast finden Sie unter [Designs mit hohem Kontrast](https://msdn.microsoft.com/library/windows/apps/mt244346).</span><span class="sxs-lookup"><span data-stu-id="bd62e-295">For more info about supporting high-contrast themes, see [High-contrast themes](https://msdn.microsoft.com/library/windows/apps/mt244346).</span></span>

### <a name="system-accent-color"></a><span data-ttu-id="bd62e-296">Systemakzentfarbe</span><span class="sxs-lookup"><span data-stu-id="bd62e-296">System accent color</span></span>

<span data-ttu-id="bd62e-297">Neben der Systemdesignfarben mit hohem Kontrast wird die Akzentfarbe des Systems als spezielle Ressource mit dem Schlüssel `SystemAccentColor` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="bd62e-297">In addition to the system high-contrast theme colors, the system accent color is provided as a special color resource using the key `SystemAccentColor`.</span></span> <span data-ttu-id="bd62e-298">Zur Laufzeit ruft diese Ressource die Farbe ab, die der Benutzer als Akzentfarbe in den Windows-Einstellungen zur Personalisierung angegeben hat.</span><span class="sxs-lookup"><span data-stu-id="bd62e-298">At runtime, this resource gets the color that the user has specified as the accent color in the Windows personalization settings.</span></span>

> <span data-ttu-id="bd62e-299">**Hinweis**&nbsp;&nbsp;Es ist möglich, die Systemfarbressourcen für hohen Kontrast und Akzentfarbe durch Erstellen von Ressourcen mit demselben Namen zu überschreiben, aber es wird empfohlen, die Farbauswahl des Benutzers zu respektieren, insbesondere bei Einstellungen für hohen Kontrast.</span><span class="sxs-lookup"><span data-stu-id="bd62e-299">**Note**&nbsp;&nbsp;It’s possible to override the system color resources for high-contrast color and accent color by creating resources with the same names, but it’s a best practice to respect the user’s color choices, especially for high-contrast settings.</span></span>

### <a name="theme-dependent-brushes"></a><span data-ttu-id="bd62e-300">Designabhängige Pinsel</span><span class="sxs-lookup"><span data-stu-id="bd62e-300">Theme-dependent brushes</span></span>

<span data-ttu-id="bd62e-301">Die in den vorherigen Abschnitten gezeigten Farbressourcen dienen zum Festlegen der [Color](https://msdn.microsoft.com/library/windows/apps/br242963)-Eigenschaft von [SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/br242962)-Ressourcen in den Systemdesign-Ressourcenwörterbüchern.</span><span class="sxs-lookup"><span data-stu-id="bd62e-301">The color resources shown in the preceding sections are used to set the [Color](https://msdn.microsoft.com/library/windows/apps/br242963) property of [SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/br242962) resources in the system theme resource dictionaries.</span></span> <span data-ttu-id="bd62e-302">Sie verwenden die Pinselressourcen, um die Farbe auf XAML-Elemente anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-302">You use the brush resources to apply the color to XAML elements.</span></span> <span data-ttu-id="bd62e-303">Die Schlüssel für die Pinselressourcen folgen diesem Benennungsformat: `SystemControl[Simple HighContrast name][Simple light/dark name]Brush`.</span><span class="sxs-lookup"><span data-stu-id="bd62e-303">The keys for the brush resources follow the naming format: `SystemControl[Simple HighContrast name][Simple light/dark name]Brush`.</span></span> <span data-ttu-id="bd62e-304">Beispiel: `SystemControlBackroundAltHighBrush`.</span><span class="sxs-lookup"><span data-stu-id="bd62e-304">For example, `SystemControlBackroundAltHighBrush`.</span></span>

<span data-ttu-id="bd62e-305">Sehen wir uns an, wie der Farbwert für diesen Pinsel zur Laufzeit bestimmt wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-305">Let’s look at how the color value for this brush is determined at run-time.</span></span> <span data-ttu-id="bd62e-306">In den Ressourcenverzeichnissen „Light“ und „Dark“ wird dieser Pinsel wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="bd62e-306">In the "Light" and "Dark" resource dictionaries, this brush is defined like this:</span></span>

`<SolidColorBrush x:Key="SystemControlBackgroundAltHighBrush" Color="{StaticResource SystemAltHighColor}"/>`

<span data-ttu-id="bd62e-307">Im Ressourcenverzeichnis „HighContrast“ wird dieser Pinsel wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="bd62e-307">In the "HighContrast" resource dictionary, this brush is defined like this:</span></span>

`<SolidColorBrush x:Key="SystemControlBackgroundAltHighBrush" Color="{ThemeResource SystemColorButtonFaceColor}"/>`

<span data-ttu-id="bd62e-308">Wenn dieser Pinsel auf ein XAML-Element angewendet wird, wird die Farbe zur Laufzeit durch das aktuelle Design bestimmt, wie in dieser Tabelle zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="bd62e-308">When this brush is applied to a XAML element, its color is determined at run-time by the current theme, as shown in this table.</span></span>

| <span data-ttu-id="bd62e-309">Design</span><span class="sxs-lookup"><span data-stu-id="bd62e-309">Theme</span></span>        | <span data-ttu-id="bd62e-310">Einfacher Farbname</span><span class="sxs-lookup"><span data-stu-id="bd62e-310">Color simple name</span></span> | <span data-ttu-id="bd62e-311">Farbressource</span><span class="sxs-lookup"><span data-stu-id="bd62e-311">Color resource</span></span>             | <span data-ttu-id="bd62e-312">Laufzeitwert</span><span class="sxs-lookup"><span data-stu-id="bd62e-312">Runtime value</span></span>                                              |
|--------------|-------------------|----------------------------|------------------------------------------------------------|
| <span data-ttu-id="bd62e-313">Light</span><span class="sxs-lookup"><span data-stu-id="bd62e-313">Light</span></span>        | <span data-ttu-id="bd62e-314">AltHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-314">AltHigh</span></span>           | <span data-ttu-id="bd62e-315">SystemAltHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-315">SystemAltHighColor</span></span>         | <span data-ttu-id="bd62e-316">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="bd62e-316">\#FFFFFFFF</span></span>                                                 |
| <span data-ttu-id="bd62e-317">Dark</span><span class="sxs-lookup"><span data-stu-id="bd62e-317">Dark</span></span>         | <span data-ttu-id="bd62e-318">AltHigh</span><span class="sxs-lookup"><span data-stu-id="bd62e-318">AltHigh</span></span>           | <span data-ttu-id="bd62e-319">SystemAltHighColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-319">SystemAltHighColor</span></span>         | <span data-ttu-id="bd62e-320">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="bd62e-320">\#FF000000</span></span>                                                 |
| <span data-ttu-id="bd62e-321">HighContrast</span><span class="sxs-lookup"><span data-stu-id="bd62e-321">HighContrast</span></span> | <span data-ttu-id="bd62e-322">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="bd62e-322">Background</span></span>        | <span data-ttu-id="bd62e-323">SystemColorButtonFaceColor</span><span class="sxs-lookup"><span data-stu-id="bd62e-323">SystemColorButtonFaceColor</span></span> | <span data-ttu-id="bd62e-324">Die in den Einstellungen für den Hintergrund der Schaltfläche angegebene Farbe.</span><span class="sxs-lookup"><span data-stu-id="bd62e-324">The color specified in settings for the button background.</span></span> |

<span data-ttu-id="bd62e-325">Sie können das `SystemControl[Simple HighContrast name][Simple light/dark name]Brush`-Benennungsschema verwenden, um zu bestimmen, welcher Pinsel auf Ihre eigenen XAML-Elemente angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-325">You can use the `SystemControl[Simple HighContrast name][Simple light/dark name]Brush` naming scheme to determine which brush to apply to your own XAML elements.</span></span> 

<!--
For many examples of how the brushes are used in the XAML control templates, see the [Default control styles and templates](default-control-styles-and-templates.md).
-->

> <span data-ttu-id="bd62e-326">**Hinweis**&nbsp;&nbsp;Nicht jede Kombination aus \[*Einfacher Name für HighContrast*\]\[*Einfacher Name für hell/dunkel*\] wird als Pinselressource bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="bd62e-326">**Note**&nbsp;&nbsp;Not every combination of \[*Simple HighContrast name*\]\[*Simple light/dark name*\] is provided as a brush resource.</span></span>

## <a name="the-xaml-type-ramp"></a><span data-ttu-id="bd62e-327">Die XAML-Typhierarchie</span><span class="sxs-lookup"><span data-stu-id="bd62e-327">The XAML type ramp</span></span>

<span data-ttu-id="bd62e-328">Die Datei „themeresources.xaml“ definiert verschiedene Ressourcen, die einen [Style](https://msdn.microsoft.com/library/windows/apps/br208849) definieren, den Sie auf Textcontainer in Ihrer UI speziell für [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) oder [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565) anwenden können.</span><span class="sxs-lookup"><span data-stu-id="bd62e-328">The themeresources.xaml file defines several resources that define a [Style](https://msdn.microsoft.com/library/windows/apps/br208849) that you can apply to text containers in your UI, specifically for either [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) or [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565).</span></span> <span data-ttu-id="bd62e-329">Dies sind nicht die impliziten Standardstile.</span><span class="sxs-lookup"><span data-stu-id="bd62e-329">These are not the default implicit styles.</span></span> <span data-ttu-id="bd62e-330">Sie werden bereitgestellt, um Ihnen das Erstellen von XAML-UI-Definitionen zu erleichtern, die der in [Richtlinien für Schriftarten](https://msdn.microsoft.com/library/windows/apps/hh700394) dokumentierten *Windows-Typhierarchie* entsprechen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-330">They are provided to make it easier for you to create XAML UI definitions that match the *Windows type ramp* documented in [Guidelines for fonts](https://msdn.microsoft.com/library/windows/apps/hh700394).</span></span>

<span data-ttu-id="bd62e-331">Diese Stile sind für Textattribute gedacht, die Sie auf den gesamten Textcontainer anwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="bd62e-331">These styles are for text attributes that you want applied to the whole text container.</span></span> <span data-ttu-id="bd62e-332">Wenn Sie Stile nur auf Textabschnitte anwenden möchten, legen Sie Attribute für die Textelemente im Container fest, zum Beispiel für [Run](https://msdn.microsoft.com/library/windows/apps/br209959) in [TextBlock.Inlines](https://msdn.microsoft.com/library/windows/apps/br209668) oder für [Paragraph](https://msdn.microsoft.com/library/windows/apps/br244503) in [RichTextBlock.Blocks](https://msdn.microsoft.com/library/windows/apps/br244347).</span><span class="sxs-lookup"><span data-stu-id="bd62e-332">If you want styles applied just to sections of the text, set attributes on the text elements within the container, such as on a [Run](https://msdn.microsoft.com/library/windows/apps/br209959) in [TextBlock.Inlines](https://msdn.microsoft.com/library/windows/apps/br209668) or on a [Paragraph](https://msdn.microsoft.com/library/windows/apps/br244503) in [RichTextBlock.Blocks](https://msdn.microsoft.com/library/windows/apps/br244347).</span></span>

<span data-ttu-id="bd62e-333">Die Stile sehen bei Anwendung auf ein [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)-Element wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="bd62e-333">The styles look like this when applied to a [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652):</span></span>

![Textblock-Stile](images/text-block-type-ramp.png)

### <a name="basetextblockstyle"></a><span data-ttu-id="bd62e-335">BaseTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-335">BaseTextBlockStyle</span></span>

<span data-ttu-id="bd62e-336">**TargetType**: [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)</span><span class="sxs-lookup"><span data-stu-id="bd62e-336">**TargetType**: [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)</span></span>

<span data-ttu-id="bd62e-337">Stellt die gemeinsamen Eigenschaften für alle anderen [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)-Textcontainerstile bereit.</span><span class="sxs-lookup"><span data-stu-id="bd62e-337">Supplies the common properties for all the other [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) container styles.</span></span>

```XAML
<!-- Usage -->
<TextBlock Text="Base" Style="{StaticResource BaseTextBlockStyle}"/>

<!-- Style definition -->
<Style x:Key="BaseTextBlockStyle" TargetType="TextBlock">
    <Setter Property="FontFamily" Value="Segoe UI"/>
    <Setter Property="FontWeight" Value="SemiBold"/>
    <Setter Property="FontSize" Value="15"/>
    <Setter Property="TextTrimming" Value="None"/>
    <Setter Property="TextWrapping" Value="Wrap"/>
    <Setter Property="LineStackingStrategy" Value="MaxHeight"/>
    <Setter Property="TextLineBounds" Value="Full"/>
</Style>
```

### <a name="headertextblockstyle"></a><span data-ttu-id="bd62e-338">HeaderTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-338">HeaderTextBlockStyle</span></span>

```XAML
<!-- Usage -->
<TextBlock Text="Header" Style="{StaticResource HeaderTextBlockStyle}"/>

<!-- Style definition -->
<Style x:Key="HeaderTextBlockStyle" TargetType="TextBlock"
       BasedOn="{StaticResource BaseTextBlockStyle}">
    <Setter Property="FontSize" Value="46"/>
    <Setter Property="FontWeight" Value="Light"/>
    <Setter Property="OpticalMarginAlignment" Value="TrimSideBearings"/>
</Style>
```

### <a name="subheadertextblockstyle"></a><span data-ttu-id="bd62e-339">SubheaderTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-339">SubheaderTextBlockStyle</span></span>

```XAML
<!-- Usage -->
<TextBlock Text="SubHeader" Style="{StaticResource SubheaderTextBlockStyle}"/>

<!-- Style definition -->
<Style x:Key="SubheaderTextBlockStyle" TargetType="TextBlock" 
       BasedOn="{StaticResource BaseTextBlockStyle}">
    <Setter Property="FontSize" Value="34"/>
    <Setter Property="FontWeight" Value="Light"/>
    <Setter Property="OpticalMarginAlignment" Value="TrimSideBearings"/>
</Style>
```

### <a name="titletextblockstyle"></a><span data-ttu-id="bd62e-340">TitleTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-340">TitleTextBlockStyle</span></span>

```XAML
<!-- Usage -->
<TextBlock Text="Title" Style="{StaticResource TitleTextBlockStyle}"/>

<!-- Style definition -->
<Style x:Key="TitleTextBlockStyle" TargetType="TextBlock" 
       BasedOn="{StaticResource BaseTextBlockStyle}">
    <Setter Property="FontWeight" Value="SemiLight"/>
    <Setter Property="FontSize" Value="24"/>
    <Setter Property="OpticalMarginAlignment" Value="TrimSideBearings"/>
</Style>
```

### <a name="subtitletextblockstyle"></a><span data-ttu-id="bd62e-341">SubtitleTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-341">SubtitleTextBlockStyle</span></span>

```XAML
<!-- Usage -->
<TextBlock Text="SubTitle" Style="{StaticResource SubtitleTextBlockStyle}"/>

<!-- Style definition -->
<Style x:Key="SubtitleTextBlockStyle" TargetType="TextBlock" 
       BasedOn="{StaticResource BaseTextBlockStyle}">
    <Setter Property="FontWeight" Value="Normal"/>
    <Setter Property="FontSize" Value="20"/>
    <Setter Property="OpticalMarginAlignment" Value="TrimSideBearings"/>
</Style>
```

### <a name="bodytextblockstyle"></a><span data-ttu-id="bd62e-342">BodyTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-342">BodyTextBlockStyle</span></span>

```XAML
<!-- Usage -->
<TextBlock Text="Body" Style="{StaticResource BodyTextBlockStyle}"/>

<!-- Style definition -->
<Style x:Key="BodyTextBlockStyle" TargetType="TextBlock" 
       BasedOn="{StaticResource BaseTextBlockStyle}">
    <Setter Property="FontWeight" Value="Normal"/>
    <Setter Property="FontSize" Value="15"/>
</Style>
```

### <a name="captiontextblockstyle"></a><span data-ttu-id="bd62e-343">CaptionTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-343">CaptionTextBlockStyle</span></span>

```XAML
<!-- Usage -->
<TextBlock Text="Caption" Style="{StaticResource CaptionTextBlockStyle}"/>

<!-- Style definition -->
<Style x:Key="CaptionTextBlockStyle" TargetType="TextBlock" 
       BasedOn="{StaticResource BaseTextBlockStyle}">
    <Setter Property="FontSize" Value="12"/>
    <Setter Property="FontWeight" Value="Normal"/>
</Style>
```

### <a name="baserichtextblockstyle"></a><span data-ttu-id="bd62e-344">BaseRichTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-344">BaseRichTextBlockStyle</span></span>

<span data-ttu-id="bd62e-345">**TargetType**: [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565)</span><span class="sxs-lookup"><span data-stu-id="bd62e-345">**TargetType**: [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565)</span></span>

<span data-ttu-id="bd62e-346">Stellt die gemeinsamen Eigenschaften für alle anderen [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565)-Containerstile bereit.</span><span class="sxs-lookup"><span data-stu-id="bd62e-346">Supplies the common properties for all the other [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565) container styles.</span></span>

```XAML
<!-- Usage -->
<RichTextBlock Style="{StaticResource BaseRichTextBlockStyle}">
    <Paragraph>Rich text.</Paragraph>
</RichTextBlock>

<!-- Style definition -->
<Style x:Key="BaseRichTextBlockStyle" TargetType="RichTextBlock">
    <Setter Property="FontFamily" Value="Segoe UI"/>
    <Setter Property="FontWeight" Value="SemiBold"/>
    <Setter Property="FontSize" Value="15"/>
    <Setter Property="TextTrimming" Value="None"/>
    <Setter Property="TextWrapping" Value="Wrap"/>
    <Setter Property="LineStackingStrategy" Value="MaxHeight"/>
    <Setter Property="TextLineBounds" Value="Full"/>
    <Setter Property="OpticalMarginAlignment" Value="TrimSideBearings"/>
</Style>
```

### <a name="bodyrichtextblockstyle"></a><span data-ttu-id="bd62e-347">BodyRichTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-347">BodyRichTextBlockStyle</span></span>

```XAML
<!-- Usage -->
<RichTextBlock Style="{StaticResource BodyRichTextBlockStyle}">
    <Paragraph>Rich text.</Paragraph>
</RichTextBlock>

<!-- Style definition -->
<Style x:Key="BodyRichTextBlockStyle" TargetType="RichTextBlock" BasedOn="{StaticResource BaseRichTextBlockStyle}">
    <Setter Property="FontWeight" Value="Normal"/>
</Style>
```

> <span data-ttu-id="bd62e-348">**Hinweis**&nbsp;&nbsp;  Die [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565)-Stile verfügen nicht über alle Texthierarchiestile von [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652). Dies liegt hauptsächlich daran, dass das blockbasierte Dokumentobjektmodell für **RichTextBlock** das Festlegen von Attributen für die einzelnen Textelemente erleichtert.</span><span class="sxs-lookup"><span data-stu-id="bd62e-348">**Note**&nbsp;&nbsp;  The [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565) styles don't have all the text ramp styles that [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) does, mainly because the block-based document object model for **RichTextBlock** makes it easier to set attributes on the individual text elements.</span></span> <span data-ttu-id="bd62e-349">Außerdem entsteht, wenn Sie [TextBlock.Text](https://msdn.microsoft.com/library/windows/apps/br209676) mit der XAML-Inhaltseigenschaft festlegen, eine Situation, in der kein zu formatierendes Textelement vorhanden ist und Sie daher den Container formatieren müssen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-349">Also, setting [TextBlock.Text](https://msdn.microsoft.com/library/windows/apps/br209676) using the XAML content property introduces a situation where there is no text element to style and thus you'd have to style the container.</span></span> <span data-ttu-id="bd62e-350">Das ist für **RichTextBlock** kein Problem, da sein Textinhalt immer in spezifischen Textelementen wie [Paragraph](https://msdn.microsoft.com/library/windows/apps/br244503) enthalten sein muss, in denen Sie XAML-Stile für die Kopfzeile, die Seitenunterüberschrift und ähnliche Texthierarchiedefinitionen festlegen können.</span><span class="sxs-lookup"><span data-stu-id="bd62e-350">That isn't an issue for **RichTextBlock** because its text content always has to be in specific text elements like [Paragraph](https://msdn.microsoft.com/library/windows/apps/br244503), which is where you might apply XAML styles for page header, page subheader and similar text ramp definitions.</span></span>

## <a name="miscellaneous-named-styles"></a><span data-ttu-id="bd62e-351">Sonstige benannte Stile</span><span class="sxs-lookup"><span data-stu-id="bd62e-351">Miscellaneous Named styles</span></span>

<span data-ttu-id="bd62e-352">Es gibt eine Reihe von weiteren [Style](https://msdn.microsoft.com/library/windows/apps/br208849)-Definitionen mit Schlüsseln, die Sie auf ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element anders als den impliziten Standardstil anwenden können.</span><span class="sxs-lookup"><span data-stu-id="bd62e-352">There's an additional set of keyed [Style](https://msdn.microsoft.com/library/windows/apps/br208849) definitions you can apply to style a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) differently than its default implicit style.</span></span>

### <a name="textblockbuttonstyle"></a><span data-ttu-id="bd62e-353">TextBlockButtonStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-353">TextBlockButtonStyle</span></span>

<span data-ttu-id="bd62e-354">**TargetType**: [ButtonBase](https://msdn.microsoft.com/library/windows/apps/br227736)</span><span class="sxs-lookup"><span data-stu-id="bd62e-354">**TargetType**: [ButtonBase](https://msdn.microsoft.com/library/windows/apps/br227736)</span></span>

<span data-ttu-id="bd62e-355">Wenden Sie diesen Stil auf ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element an, wenn Sie Text anzeigen müssen, auf den ein Benutzer klicken kann, um Aktionen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-355">Apply this style to a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) when you need to show text that a user can click to take action.</span></span> <span data-ttu-id="bd62e-356">Der Text wird mithilfe der aktuellen Akzentfarbe formatiert, um ihn als interaktiv hervorzuheben, und weist Fokusrechtecke auf, die gut für Text geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="bd62e-356">The text is styled using the current accent color to distinguish it as interactive and has focus rectangles that work well for text.</span></span> <span data-ttu-id="bd62e-357">Im Gegensatz zum impliziten Stil eines [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/br242739)-Elements unterstreicht der **TextBlockButtonStyle** den Text nicht.</span><span class="sxs-lookup"><span data-stu-id="bd62e-357">Unlike the implicit style of a [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/br242739), the **TextBlockButtonStyle** does not underline the text.</span></span>

<span data-ttu-id="bd62e-358">Die Vorlage formatiert außerdem den angezeigten Text für die Verwendung von **SystemControlHyperlinkBaseMediumBrush** (für den Zustand „PointerOver“), **SystemControlHighlightBaseMediumLowBrush** (für den Zustand „Pressed“) und **SystemControlDisabledBaseLowBrush** (für den Zustand „Disabled“).</span><span class="sxs-lookup"><span data-stu-id="bd62e-358">The template also styles the presented text to use **SystemControlHyperlinkBaseMediumBrush** (for "PointerOver" state), **SystemControlHighlightBaseMediumLowBrush** (for "Pressed" state) and **SystemControlDisabledBaseLowBrush** (for "Disabled" state).</span></span>

<span data-ttu-id="bd62e-359">Hier ist ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element mit der angewendeten **TextBlockButtonStyle**-Ressource.</span><span class="sxs-lookup"><span data-stu-id="bd62e-359">Here's a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) with the **TextBlockButtonStyle** resource applied to it.</span></span>

```XAML
<Button Content="Clickable text" Style="{StaticResource TextBlockButtonStyle}" 
        Click="Button_Click"/>
```

<span data-ttu-id="bd62e-360">Es sieht ungefähr so aus:</span><span class="sxs-lookup"><span data-stu-id="bd62e-360">It looks like this:</span></span>

![Eine Schaltfläche, die wie Text aussieht](images/styles-textblock-button-style.png)

### <a name="navigationbackbuttonnormalstyle"></a><span data-ttu-id="bd62e-362">NavigationBackButtonNormalStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-362">NavigationBackButtonNormalStyle</span></span>

<span data-ttu-id="bd62e-363">**TargetType**: [Button](https://msdn.microsoft.com/library/windows/apps/br209265)</span><span class="sxs-lookup"><span data-stu-id="bd62e-363">**TargetType**: [Button](https://msdn.microsoft.com/library/windows/apps/br209265)</span></span>

<span data-ttu-id="bd62e-364">Dieser [Style](https://msdn.microsoft.com/library/windows/apps/br208849) stellt eine vollständige Vorlage für ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element bereit, bei der es sich um die Navigationsschaltfläche „Zurück“ für eine Navigations-App handeln kann.</span><span class="sxs-lookup"><span data-stu-id="bd62e-364">This [Style](https://msdn.microsoft.com/library/windows/apps/br208849) provides a complete template for a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) that can be the navigation back button for a navigation app.</span></span> <span data-ttu-id="bd62e-365">Sie enthält Designressourcenverweise, durch die diese Schaltfläche die Symbolschriftart Segoe MDL2 verwendet, sodass Sie einen [Symbol](https://msdn.microsoft.com/library/windows/apps/dn252842)-Wert als Inhalt anstelle von Text verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="bd62e-365">It includes theme resource references that make this button use the Segoe MDL2 Assets symbol font, so you should use a [Symbol](https://msdn.microsoft.com/library/windows/apps/dn252842) value as the content rather than text.</span></span> <span data-ttu-id="bd62e-366">Die Standardgröße ist 40 x 40 Pixel.</span><span class="sxs-lookup"><span data-stu-id="bd62e-366">The default dimensions are 40 x 40 pixels.</span></span> <span data-ttu-id="bd62e-367">Um den Stil anzupassen, können Sie die Eigenschaften [Height](https://msdn.microsoft.com/library/windows/apps/br208718), [Width](https://msdn.microsoft.com/library/windows/apps/br208751), [FontSize](https://msdn.microsoft.com/library/windows/apps/br209406) und andere für Ihr **Button**-Element explizit festlegen oder einen abgeleiteten Stil mithilfe von [BasedOn](https://msdn.microsoft.com/library/windows/apps/br208852) erstellen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-367">To tailor the styling you can either explicitly set the [Height](https://msdn.microsoft.com/library/windows/apps/br208718), [Width](https://msdn.microsoft.com/library/windows/apps/br208751), [FontSize](https://msdn.microsoft.com/library/windows/apps/br209406), and other properties on your **Button** or create a derived style using [BasedOn](https://msdn.microsoft.com/library/windows/apps/br208852).</span></span>

<span data-ttu-id="bd62e-368">Hier ist ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element mit der angewendeten **NavigationBackButtonNormalStyle**-Ressource.</span><span class="sxs-lookup"><span data-stu-id="bd62e-368">Here's a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) with the **NavigationBackButtonNormalStyle** resource applied to it.</span></span>

```XAML
<Button Content="&amp;#xE830;" Style="{StaticResource NavigationBackButtonNormalStyle}" 
        Click="Button_Click"/>
```

<span data-ttu-id="bd62e-369">Es sieht ungefähr so aus:</span><span class="sxs-lookup"><span data-stu-id="bd62e-369">It looks like this:</span></span>

![Eine als Zurückschaltfläche formatierte Schaltfläche](images/styles-back-button-normal.png)

### <a name="navigationbackbuttonsmallstyle"></a><span data-ttu-id="bd62e-371">NavigationBackButtonSmallStyle</span><span class="sxs-lookup"><span data-stu-id="bd62e-371">NavigationBackButtonSmallStyle</span></span>

<span data-ttu-id="bd62e-372">**TargetType**: [Button](https://msdn.microsoft.com/library/windows/apps/br209265)</span><span class="sxs-lookup"><span data-stu-id="bd62e-372">**TargetType**: [Button](https://msdn.microsoft.com/library/windows/apps/br209265)</span></span>

<span data-ttu-id="bd62e-373">Dieser [Style](https://msdn.microsoft.com/library/windows/apps/br208849) stellt eine vollständige Vorlage für ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element bereit, bei der es sich um die Navigationsschaltfläche „Zurück“ für eine Navigations-App handeln kann.</span><span class="sxs-lookup"><span data-stu-id="bd62e-373">This [Style](https://msdn.microsoft.com/library/windows/apps/br208849) provides a complete template for a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) that can be the navigation back button for a navigation app.</span></span> <span data-ttu-id="bd62e-374">Sie ähnelt **NavigationBackButtonNormalStyle**, aber die Größe beträgt 30 x 30 Pixel.</span><span class="sxs-lookup"><span data-stu-id="bd62e-374">It's similar to **NavigationBackButtonNormalStyle**, but its dimensions are 30 by 30 pixels.</span></span>

<span data-ttu-id="bd62e-375">Hier ist ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element mit der angewendeten **NavigationBackButtonSmallStyle**-Ressource.</span><span class="sxs-lookup"><span data-stu-id="bd62e-375">Here's a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) with the **NavigationBackButtonSmallStyle** resource applied to it.</span></span>

```XAML
<Button Content="&amp;#xE830;" Style="{StaticResource NavigationBackButtonSmallStyle}" 
        Click="Button_Click"/>
```

## <a name="troubleshooting-theme-resources"></a><span data-ttu-id="bd62e-376">Problembehandlung für Designressourcen</span><span class="sxs-lookup"><span data-stu-id="bd62e-376">Troubleshooting theme resources</span></span>


<span data-ttu-id="bd62e-377">Wenn Sie den [Richtlinien für die Verwendung von Designressourcen](#guidelines-for-using-theme-resources) nicht folgen, kann unerwartetes Verhalten im Zusammenhang mit Designs in Ihrer App auftreten.</span><span class="sxs-lookup"><span data-stu-id="bd62e-377">If you don’t follow the [guidelines for using theme resources](#guidelines-for-using-theme-resources), you might see unexpected behavior related to themes in your app.</span></span>

<span data-ttu-id="bd62e-378">Wenn Sie beispielsweise ein Flyout mit hellem Design öffnen, ändern sich auch Teile der App mit dem dunklen Design so, als wären sie im hellen Design.</span><span class="sxs-lookup"><span data-stu-id="bd62e-378">For example, when you open a light-themed flyout, parts of your dark-themed app also change as if they were in the light theme.</span></span> <span data-ttu-id="bd62e-379">Wenn Sie zu einer Seite mit hellem Design und dann zurück navigieren, sieht die ursprüngliche Seite mit dunklem Design (oder Teile davon) so aus, als wäre sie im hellen Design.</span><span class="sxs-lookup"><span data-stu-id="bd62e-379">Or if you navigate to a light-themed page and then navigate back, the original dark-themed page (or parts of it) now looks as though it is in the light theme.</span></span>

<span data-ttu-id="bd62e-380">Diese Arten von Problemen treten in der Regel auf, wenn Sie ein Standard-Design und ein HighContrast-Design für die Unterstützung von Szenarien mit hohem Kontrast bereitstellen und dann Light- und Dark-Designs in verschiedenen Teilen der App verwenden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-380">Typically, these types of issues occur when you provide a "Default" theme and a "HighContrast" theme to support high-contrast scenarios, and then use both "Light" and "Dark" themes in different parts of your app.</span></span>

<span data-ttu-id="bd62e-381">Betrachten Sie beispielsweise diese Definition eines Designwörterbuchs:</span><span class="sxs-lookup"><span data-stu-id="bd62e-381">For example, consider this theme dictionary definition:</span></span>

```XAML
<!-- DO NOT USE. THIS XAML DEMONSTRATES AN ERROR. -->
<ResourceDictionary>
  <ResourceDictionary.ThemeDictionaries>
    <ResourceDictionary x:Key="Default">
      <SolidColorBrush x:Key="myBrush" Color="{ThemeResource SystemBaseHighColor}"/>
    </ResourceDictionary>
    <ResourceDictionary x:Key="HighContrast">
      <SolidColorBrush x:Key="myBrush" Color="{ThemeResource SystemColorButtonFaceColor}"/>
    </ResourceDictionary>
  </ResourceDictionary.ThemeDictionaries>
</ResourceDictionary>
```

<span data-ttu-id="bd62e-382">Intuitiv sieht sie richtig aus.</span><span class="sxs-lookup"><span data-stu-id="bd62e-382">Intuitively, this looks correct.</span></span> <span data-ttu-id="bd62e-383">Sie möchten die Farbe ändern, auf die durch `myBrush` mit hohem Kontrast verwiesen wird. Außerhalb des hohen Kontrasts vertrauen Sie aber auf die [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md), um sicherzustellen, dass `myBrush` auf die richtige Farbe für das Design verweist.</span><span class="sxs-lookup"><span data-stu-id="bd62e-383">You want to change the color pointed to by `myBrush` when in high-contrast, but when not in high-contrast, you rely on the [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md) to make sure that `myBrush` points to the right color for your theme.</span></span> <span data-ttu-id="bd62e-384">Wenn Ihre App nie [FrameworkElement.RequestedTheme](https://msdn.microsoft.com/library/windows/apps/dn298515) für Elemente in der visuellen Struktur festgelegt hat, funktioniert dies in der Regel wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="bd62e-384">If your app never has [FrameworkElement.RequestedTheme](https://msdn.microsoft.com/library/windows/apps/dn298515) set on elements within its visual tree, this will typically work as expected.</span></span> <span data-ttu-id="bd62e-385">Allerdings treten Probleme in Ihrer App auf, sobald Sie das Design verschiedener Teile der visuellen Struktur ändern.</span><span class="sxs-lookup"><span data-stu-id="bd62e-385">However, you run into problems in your app as soon as you start to re-theme different parts of your visual tree.</span></span>

<span data-ttu-id="bd62e-386">Das Problem tritt auf, da Pinsel im Gegensatz zu den meisten anderen XAML-Typen freigegebene Ressourcen sind.</span><span class="sxs-lookup"><span data-stu-id="bd62e-386">The problem occurs because brushes are shared resources, unlike most other XAML types.</span></span> <span data-ttu-id="bd62e-387">Wenn Sie zwei Elemente in XAML-Unterstrukturen mit verschiedenen Designs haben, die auf die gleiche Pinselressource verweisen, und das Framework für jede Teilstruktur eine Aktualisierung der Ausdrücke der [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md) durchführt, werden Änderungen an der freigegebenen Pinselressource in der anderen untergeordneten Struktur wiedergegeben, was nicht dem gewünschten Ergebnis entspricht.</span><span class="sxs-lookup"><span data-stu-id="bd62e-387">If you have 2 elements in XAML sub-trees with different themes that reference the same brush resource, then as the framework walks each sub-tree to update its [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md) expressions, changes to the shared brush resource are reflected in the other sub-tree, which is not your intended result.</span></span>

<span data-ttu-id="bd62e-388">Ersetzen Sie zum Beheben dieses Problems das Standard-Wörterbuch durch separate Designwörterbücher für die Light- und Dark-Designs zusätzlich zu „HighContrast“:</span><span class="sxs-lookup"><span data-stu-id="bd62e-388">To fix this, replace the "Default" dictionary with separate theme dictionaries for both "Light" and "Dark" themes in addition to "HighContrast":</span></span>

```XAML
<!-- DO NOT USE. THIS XAML DEMONSTRATES AN ERROR. -->
<ResourceDictionary>
  <ResourceDictionary.ThemeDictionaries>
    <ResourceDictionary x:Key="Light">
      <SolidColorBrush x:Key="myBrush" Color="{ThemeResource SystemBaseHighColor}"/>
    </ResourceDictionary>    
    <ResourceDictionary x:Key="Dark">
      <SolidColorBrush x:Key="myBrush" Color="{ThemeResource SystemBaseHighColor}"/>
    </ResourceDictionary>
    <ResourceDictionary x:Key="HighContrast">
      <SolidColorBrush x:Key="myBrush" Color="{ThemeResource SystemColorButtonFaceColor}"/>
    </ResourceDictionary>
  </ResourceDictionary.ThemeDictionaries>
</ResourceDictionary>
```

<span data-ttu-id="bd62e-389">Allerdings treten weiterhin Probleme auf, wenn auf eine dieser Ressourcen in geerbten Eigenschaften wie [Foreground](https://msdn.microsoft.com/library/windows/apps/br209414) verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-389">However, problems still occur if any of these resources are referenced in inherited properties like [Foreground](https://msdn.microsoft.com/library/windows/apps/br209414).</span></span> <span data-ttu-id="bd62e-390">Die benutzerdefinierte Steuerelementvorlage gibt möglicherweise die Vordergrundfarbe für ein Element mit der [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md) an, aber wenn das Framework den geerbten Wert an die untergeordneten Elemente weitergibt, stellt es einen direkten Verweis auf die Ressource bereit, die durch den Ausdruck der {ThemeResource}-Markuperweiterung aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="bd62e-390">Your custom control template might specify the foreground color of an element using the [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md), but when the framework propagates the inherited value to child elements, it provides a direct reference to the resource that was resolved by the {ThemeResource} markup extension expression.</span></span> <span data-ttu-id="bd62e-391">Dies führt zu Problemen, wenn das Framework Designänderungen verarbeitet, während es die visuelle Struktur des Steuerelements durchläuft.</span><span class="sxs-lookup"><span data-stu-id="bd62e-391">This causes problems when the framework processes theme changes as it walks your control's visual tree.</span></span> <span data-ttu-id="bd62e-392">Es wertet den Ausdruck der {ThemeResource}-Markuperweiterung neu aus, um eine neue Pinselressource abzurufen, gibt diesen Verweis aber noch nicht an die untergeordneten Elemente des Steuerelements weiter; dies geschieht später, zum Beispiel beim nächsten Messwertdurchlauf.</span><span class="sxs-lookup"><span data-stu-id="bd62e-392">It re-evaluates the {ThemeResource} markup extension expression to get a new brush resource but doesn’t yet propagate this reference down to the children of your control; this happens later, such as during the next measure pass.</span></span>

<span data-ttu-id="bd62e-393">Nach dem Durchlaufen der visuellen Struktur des Steuerelements in Reaktion auf eine Designänderung durchläuft das Framework daher die untergeordneten Elemente und aktualisiert Ausdrücke der [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md) für sie oder für Objekte, die für ihre Eigenschaften festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="bd62e-393">As a result, after walking the control visual tree in response to a theme change, the framework walks the children and updates any [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md) expressions set on them, or on objects set on their properties.</span></span> <span data-ttu-id="bd62e-394">Hier tritt das Problem auf. Das Framework durchläuft die Pinselressource, und da die Farbe mit einer {ThemeResource}-Markuperweiterung angegeben wird, erfolgt eine erneute Auswertung.</span><span class="sxs-lookup"><span data-stu-id="bd62e-394">This is where the problem occurs; the framework walks the brush resource and because it specifies its color using a {ThemeResource} markup extension, it's re-evaluated.</span></span>

<span data-ttu-id="bd62e-395">An dieser Stelle hat das Framework Ihr Designverzeichnis anscheinend „verunreinigt“, da es jetzt eine Ressource aus einem Wörterbuch enthält, für die die Farbe durch ein anderes Wörterbuch festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-395">At this point, the framework appears to have polluted your theme dictionary because it now has a resource from one dictionary that has its color set from another dictionary.</span></span>

<span data-ttu-id="bd62e-396">Um dieses Problem zu beheben, verwenden Sie die [{StaticResource}-Markuperweiterung](../xaml-platform/staticresource-markup-extension.md) anstatt der [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="bd62e-396">To fix this problem, use the [{StaticResource} markup extension](../xaml-platform/staticresource-markup-extension.md) instead of [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md).</span></span> <span data-ttu-id="bd62e-397">Mit den angewendeten Richtlinien sehen die Designverzeichnisse wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="bd62e-397">With the guidelines applied, the theme dictionaries look like this:</span></span>

```XAML
<ResourceDictionary>
  <ResourceDictionary.ThemeDictionaries>
    <ResourceDictionary x:Key="Light">
      <SolidColorBrush x:Key="myBrush" Color="{StaticResource SystemBaseHighColor}"/>
    </ResourceDictionary>    
    <ResourceDictionary x:Key="Dark">
      <SolidColorBrush x:Key="myBrush" Color="{StaticResource SystemBaseHighColor}"/>
    </ResourceDictionary>
    <ResourceDictionary x:Key="HighContrast">
      <SolidColorBrush x:Key="myBrush" Color="{ThemeResource SystemColorButtonFaceColor}"/>
    </ResourceDictionary>
  </ResourceDictionary.ThemeDictionaries>
</ResourceDictionary>
```

<span data-ttu-id="bd62e-398">Beachten Sie, dass die [{ThemeResource}-Markuperweiterung](../xaml-platform/themeresource-markup-extension.md) weiterhin im HighContrast-Wörterbuch anstelle der [{StaticResource}-Markuperweiterung](../xaml-platform/staticresource-markup-extension.md) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-398">Notice that the [{ThemeResource} markup extension](../xaml-platform/themeresource-markup-extension.md) is still used in the "HighContrast" dictionary instead of [{StaticResource} markup extension](../xaml-platform/staticresource-markup-extension.md).</span></span> <span data-ttu-id="bd62e-399">Diese Situation fällt unter die Ausnahme, die weiter oben in den Richtlinien angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="bd62e-399">This situation falls under the exception given earlier in the guidelines.</span></span> <span data-ttu-id="bd62e-400">Die meisten Pinselwerte für das HighContrast-Design verwenden eine Farbauswahl, die global vom System gesteuert wird, aber für XAML als Ressource mit einem speziellen Namen („SystemColor“ ist dem Namen vorangestellt) verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="bd62e-400">Most of the brush values that are used for the "HighContrast" theme are using color choices that are globally controlled by the system, but exposed to XAML as a specially-named resource (those prefixed with ‘SystemColor’ in the name).</span></span> <span data-ttu-id="bd62e-401">Das System ermöglicht es den Benutzern, im Center für erleichterte Bedienung die spezifischen Farben festzulegen, die für ihre Einstellungen für hohen Kontrast verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-401">The system enables the user to set the specific colors that should be used for their high contrast settings through the Ease of Access Center.</span></span> <span data-ttu-id="bd62e-402">Diese Farbauswahl gilt für die speziell benannten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="bd62e-402">Those color choices are applied to the specially-named resources.</span></span> <span data-ttu-id="bd62e-403">Das XAML-Framework verwendet das gleiche Designänderungsereignis, um auch diese Pinsel zu aktualisieren, wenn es erkennt, dass sie auf Systemebene geändert wurden.</span><span class="sxs-lookup"><span data-stu-id="bd62e-403">The XAML framework uses the same theme changed event to also update these brushes when it detects they’ve changed at the system level.</span></span> <span data-ttu-id="bd62e-404">Darum wird hier die {ThemeResource}-Markuperweiterung verwendet.</span><span class="sxs-lookup"><span data-stu-id="bd62e-404">This is why the {ThemeResource} markup extension is used here.</span></span>


