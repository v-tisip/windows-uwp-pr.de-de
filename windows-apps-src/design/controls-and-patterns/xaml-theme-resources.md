---
author: Jwmsft
Description: Theme resources in XAML are a set of resources that apply different values depending on which system theme is active.
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
ms.localizationpriority: medium
ms.openlocfilehash: 36f7e92f1652b4c67ef63ca3cf3b536126e3c995
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832708"
---
# <a name="xaml-theme-resources"></a><span data-ttu-id="aeb13-103">XAML-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="aeb13-103">XAML theme resources</span></span>

<span data-ttu-id="aeb13-104">Bei Designressourcen in XAML handelt es sich um einen Satz von Ressourcen, die abhängig vom aktiven Systemdesign verschiedene Werte anwenden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-104">Theme resources in XAML are a set of resources that apply different values depending on which system theme is active.</span></span> <span data-ttu-id="aeb13-105">Es gibt drei Designs, die das XAML-Framework unterstützt: „Light“, „Dark“ und „HighContrast“.</span><span class="sxs-lookup"><span data-stu-id="aeb13-105">There are 3 themes that the XAML framework supports: "Light", "Dark", and "HighContrast".</span></span>

<span data-ttu-id="aeb13-106">**Prerequisites**: In diesem Thema wird vorausgesetzt, dass Sie [ResourceDictionary- und XAML-Ressourcenreferenzen](resourcedictionary-and-xaml-resource-references.md) gelesen haben.</span><span class="sxs-lookup"><span data-stu-id="aeb13-106">**Prerequisites**: This topic assumes that you have read [ResourceDictionary and XAML resource references](resourcedictionary-and-xaml-resource-references.md).</span></span>

## <a name="theme-resources-v-static-resources"></a><span data-ttu-id="aeb13-107">Designressourcen im Vergleich zu</span><span class="sxs-lookup"><span data-stu-id="aeb13-107">Theme resources v.</span></span> <span data-ttu-id="aeb13-108">statischen Ressourcen</span><span class="sxs-lookup"><span data-stu-id="aeb13-108">static resources</span></span>

<span data-ttu-id="aeb13-109">Es gibt zwei XAML-Markuperweiterungen, die aus einem vorhandenen XAML-Ressourcenverzeichnis auf eine XAML-Ressource verweisen können: die [{StaticResource}-Markuperweiterung](../../xaml-platform/staticresource-markup-extension.md) und die [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="aeb13-109">There are two XAML markup extensions that can reference a XAML resource from an existing XAML resource dictionary: [{StaticResource} markup extension](../../xaml-platform/staticresource-markup-extension.md) and [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md).</span></span>

<span data-ttu-id="aeb13-110">Die Auswertung einer [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md) tritt beim Laden der App und anschließend bei jeder Änderung des Designs zur Laufzeit auf.</span><span class="sxs-lookup"><span data-stu-id="aeb13-110">Evaluation of a [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md) occurs when the app loads and subsequently each time the theme changes at runtime.</span></span> <span data-ttu-id="aeb13-111">Dies ist in der Regel das Ergebnis des Änderns der Geräteeinstellungen durch den Benutzer oder einer programmgesteuerten Änderung in der App, die das aktuelle Design ändert.</span><span class="sxs-lookup"><span data-stu-id="aeb13-111">This is typically the result of the user changing their device settings or from a programmatic change within the app that alters its current theme.</span></span>

<span data-ttu-id="aeb13-112">Für eine [{StaticResource}-Markuperweiterung](../../xaml-platform/staticresource-markup-extension.md) erfolgt eine Auswertung hingegen nur, wenn die XAML zuerst von der App geladen wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-112">In contrast, a [{StaticResource} markup extension](../../xaml-platform/staticresource-markup-extension.md) is evaluated only when the XAML is first loaded by the app.</span></span> <span data-ttu-id="aeb13-113">Es findet keine Aktualisierung statt.</span><span class="sxs-lookup"><span data-stu-id="aeb13-113">It does not update.</span></span> <span data-ttu-id="aeb13-114">Dies ähnelt dem Suchen und Ersetzen in XAML mit dem tatsächlichen Laufzeitwert beim Start der App.</span><span class="sxs-lookup"><span data-stu-id="aeb13-114">It’s similar to a find and replace in your XAML with the actual runtime value at app launch.</span></span>

## <a name="theme-resources-in-the-resource-dictionary-structure"></a><span data-ttu-id="aeb13-115">Designressourcen in der Ressourcenverzeichnisstruktur</span><span class="sxs-lookup"><span data-stu-id="aeb13-115">Theme resources in the resource dictionary structure</span></span>

<span data-ttu-id="aeb13-116">Jede Designressource ist Teil der XAML-Datei „themeresources.xaml“.</span><span class="sxs-lookup"><span data-stu-id="aeb13-116">Each theme resource is part of the XAML file themeresources.xaml.</span></span> <span data-ttu-id="aeb13-117">Zu Designzwecken steht „themeresources.xaml“ im Order „\\(Programme)\\Windows Kits\\10\\DesignTime\\CommonConfiguration\\Neutral\\UAP\\&lt;SDK version&gt;\\Generic“ aus einer Windows Software Development Kit (SDK)-Installation zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="aeb13-117">For design purposes, themeresources.xaml is available in the \\(Program Files)\\Windows Kits\\10\\DesignTime\\CommonConfiguration\\Neutral\\UAP\\&lt;SDK version&gt;\\Generic folder from a Windows Software Development Kit (SDK) installation.</span></span> <span data-ttu-id="aeb13-118">Die Ressourcenverzeichnisse in „themeresources.xaml“ werden auch in „generic.xaml“ im selben Verzeichnis reproduziert.</span><span class="sxs-lookup"><span data-stu-id="aeb13-118">The resource dictionaries in themeresources.xaml are also reproduced in generic.xaml in the same directory.</span></span>

<span data-ttu-id="aeb13-119">Die Windows-Runtime verwendet diese physischen Dateien nicht für die Runtime-Suche.</span><span class="sxs-lookup"><span data-stu-id="aeb13-119">The Windows Runtime doesn't use these physical files for runtime lookup.</span></span> <span data-ttu-id="aeb13-120">Daher befinden sie sich in einem speziellen DesignTime-Ordner und werden nicht standardmäßig in Apps kopiert.</span><span class="sxs-lookup"><span data-stu-id="aeb13-120">That's why they are specifically in a DesignTime folder, and they aren't copied into apps by default.</span></span> <span data-ttu-id="aeb13-121">Stattdessen sind die Ressourcenverzeichnisse als Teil der Windows-Runtime selbst im Speicher vorhanden, und die XAML-Ressource Ihrer App verweist auf Designressourcen (oder Systemressourcen), die dort zu Laufzeit aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-121">Instead, these resource dictionaries exist in memory as part of the Windows Runtime itself, and your app's XAML resource references to theme resources (or system resources) resolve there at runtime.</span></span>

## <a name="guidelines-for-custom-theme-resources"></a><span data-ttu-id="aeb13-122">Richtlinien für benutzerdefinierte Designressourcen</span><span class="sxs-lookup"><span data-stu-id="aeb13-122">Guidelines for custom theme resources</span></span>

<span data-ttu-id="aeb13-123">Halten Sie sich an die folgenden Richtlinien, wenn Sie Ihre eigenen benutzerdefinierten Designressourcen definieren und verwenden:</span><span class="sxs-lookup"><span data-stu-id="aeb13-123">Follow these guidelines when you define and consume your own custom theme resources:</span></span>

- <span data-ttu-id="aeb13-124">Geben Sie zusätzlich zum Verzeichnis „HighContrast“ jeweils ein Designverzeichnis für „Light“ und „Dark“ an.</span><span class="sxs-lookup"><span data-stu-id="aeb13-124">Specify theme dictionaries for both "Light" and "Dark" in addition to your "HighContrast" dictionary.</span></span> <span data-ttu-id="aeb13-125">Sie können zwar ein [ResourceDictionary](https://msdn.microsoft.com/library/windows/apps/br208794)-Element mit „Default“ als Schlüssel erstellen, es empfiehlt sich jedoch, explizit vorzugehen und stattdessen „Light“, „Dark“ und „HighContrast“ zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-125">Although you can create a [ResourceDictionary](https://msdn.microsoft.com/library/windows/apps/br208794) with "Default" as the key, it’s preferred to be explicit and instead use "Light", "Dark", and "HighContrast".</span></span>

- <span data-ttu-id="aeb13-126">Verwenden Sie die [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md) in Stilen, Settern, Steuerelementvorlagen, Settern für Eigenschaften und Animationen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-126">Use the [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md) in: Styles, Setters, Control templates, Property setters, and Animations.</span></span>

- <span data-ttu-id="aeb13-127">Verwenden Sie die [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md) nicht in Ihren Ressourcendefinitionen in [ThemeDictionaries](https://msdn.microsoft.com/library/windows/apps/br208807).</span><span class="sxs-lookup"><span data-stu-id="aeb13-127">Don't use the [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md) in your resource definitions inside your [ThemeDictionaries](https://msdn.microsoft.com/library/windows/apps/br208807).</span></span> <span data-ttu-id="aeb13-128">Verwenden Sie stattdessen die [{StaticResource}-Markuperweiterung](../../xaml-platform/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="aeb13-128">Use [{StaticResource} markup extension](../../xaml-platform/staticresource-markup-extension.md) instead.</span></span>

    <span data-ttu-id="aeb13-129">AUSNAHME: Sie können die [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md) verwenden, um auf Ressourcen zu verweisen, die in Bezug auf das App-Design in [ThemeDictionaries](https://msdn.microsoft.com/library/windows/apps/br208807) agnostisch sind.</span><span class="sxs-lookup"><span data-stu-id="aeb13-129">EXCEPTION: You can use the [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md) to reference resources that are agnostic to the app theme in your [ThemeDictionaries](https://msdn.microsoft.com/library/windows/apps/br208807).</span></span> <span data-ttu-id="aeb13-130">Beispiele für diese Ressourcen sind Akzentfarbenressourcen wie `SystemAccentColor` oder Systemfarbenressourcen, die normalerweise das Präfix „SystemColor“ haben, z.B. `SystemColorButtonFaceColor`.</span><span class="sxs-lookup"><span data-stu-id="aeb13-130">Examples of these resources are accent color resources like `SystemAccentColor`, or system color resources, which are typically prefixed with "SystemColor" like `SystemColorButtonFaceColor`.</span></span>

> [!CAUTION]
> <span data-ttu-id="aeb13-131">Wenn Sie diesen Richtlinien nicht folgen, kann ein unerwartetes Verhalten im Zusammenhang mit Designs in Ihrer App auftreten.</span><span class="sxs-lookup"><span data-stu-id="aeb13-131">If you don’t follow these guidelines, you might see unexpected behavior related to themes in your app.</span></span> <span data-ttu-id="aeb13-132">Weitere Informationen finden Sie im Abschnitt [Problembehandlung für Designressourcen](#troubleshooting-theme-resources).</span><span class="sxs-lookup"><span data-stu-id="aeb13-132">For more info, see the [Troubleshooting theme resources](#troubleshooting-theme-resources) section.</span></span>

## <a name="the-xaml-color-ramp-and-theme-dependent-brushes"></a><span data-ttu-id="aeb13-133">Die XAML-Farbskala und designabhängige Pinsel</span><span class="sxs-lookup"><span data-stu-id="aeb13-133">The XAML color ramp and theme-dependent brushes</span></span>

<span data-ttu-id="aeb13-134">Die kombinierte Gruppe von Farben für die Designs „Light“, „Dark“ und „HighContrast“ bilden die *Windows-Farbskala* in XAML.</span><span class="sxs-lookup"><span data-stu-id="aeb13-134">The combined set of colors for "Light", "Dark", and "HighContrast" themes make up the *Windows color ramp* in XAML.</span></span> <span data-ttu-id="aeb13-135">Egal, ob Sie die Systemdesigns ändern oder ein Systemdesign auf Ihre eigenen XAML-Elemente anwenden möchten, ist es wichtig zu verstehen, wie die Farbressourcen strukturiert werden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-135">Whether you want to modify the system themes, or apply a system theme to your own XAML elements, it’s important to understand how the color resources are structured.</span></span>

<span data-ttu-id="aeb13-136">Weitere Informationen dazu, wie Sie die Farbe in der UWP-App anwenden, finden Sie unter [Farbe in UWP-Apps](../style/color.md).</span><span class="sxs-lookup"><span data-stu-id="aeb13-136">For additional information about how to apply color in your UWP app, please see [Color in UWP apps](../style/color.md).</span></span>

### <a name="light-and-dark-theme-colors"></a><span data-ttu-id="aeb13-137">Helle und dunkle Designfarben</span><span class="sxs-lookup"><span data-stu-id="aeb13-137">Light and Dark theme colors</span></span>

<span data-ttu-id="aeb13-138">Das XAML-Framework stellt eine Gruppe von benannten [Color](/uwp/api/Windows.UI.Color)-Ressourcen mit Werten bereiten, die speziell auf die Designs „Light“ und „Dark“ zugeschnitten sind.</span><span class="sxs-lookup"><span data-stu-id="aeb13-138">The XAML framework provides a set of named [Color](/uwp/api/Windows.UI.Color) resources with values that are tailored for the "Light" and "Dark" themes.</span></span> <span data-ttu-id="aeb13-139">Die Schlüssel, die Sie zum Verweisen verwenden, haben folgendes Namensformat: `System[Simple Light/Dark Name]Color`.</span><span class="sxs-lookup"><span data-stu-id="aeb13-139">The keys you use to reference these follow the naming format: `System[Simple Light/Dark Name]Color`.</span></span>

<span data-ttu-id="aeb13-140">Diese Tabelle enthält den Schlüssel, den einfachen Namen und die Zeichenfolgendarstellung der Farbe (mit dem \#aarrggbb-Format) für die Ressourcen „Light“ und „Dark“, die vom XAML-Framework bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-140">This table lists the key, simple name, and string representation of the color (using the \#aarrggbb format) for the "Light" and "Dark" resources provided by the XAML framework.</span></span> <span data-ttu-id="aeb13-141">Der Schlüssel wird verwendet, um auf die Ressource in einer App zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-141">The key is used to reference the resource in an app.</span></span> <span data-ttu-id="aeb13-142">Der einfache Name für hell/dunkel dient als Teil der Pinselbenennungskonvention, die später erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-142">The "Simple light/dark name" is used as part of the brush naming convention that we explain later.</span></span>

| <span data-ttu-id="aeb13-143">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="aeb13-143">Key</span></span>                             | <span data-ttu-id="aeb13-144">Einfacher Name für hell/dunkel</span><span class="sxs-lookup"><span data-stu-id="aeb13-144">Simple light/dark name</span></span> | <span data-ttu-id="aeb13-145">Light</span><span class="sxs-lookup"><span data-stu-id="aeb13-145">Light</span></span>      | <span data-ttu-id="aeb13-146">Dark</span><span class="sxs-lookup"><span data-stu-id="aeb13-146">Dark</span></span>       |
|---------------------------------|------------------------|------------|------------|
| <span data-ttu-id="aeb13-147">SystemAltHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-147">SystemAltHighColor</span></span>              | <span data-ttu-id="aeb13-148">AltHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-148">AltHigh</span></span>                | <span data-ttu-id="aeb13-149">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-149">\#FFFFFFFF</span></span> | <span data-ttu-id="aeb13-150">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-150">\#FF000000</span></span> |
| <span data-ttu-id="aeb13-151">SystemAltLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-151">SystemAltLowColor</span></span>               | <span data-ttu-id="aeb13-152">AltLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-152">AltLow</span></span>                 | <span data-ttu-id="aeb13-153">\#33FFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-153">\#33FFFFFF</span></span> | <span data-ttu-id="aeb13-154">\#33000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-154">\#33000000</span></span> |
| <span data-ttu-id="aeb13-155">SystemAltMediumColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-155">SystemAltMediumColor</span></span>            | <span data-ttu-id="aeb13-156">AltMedium</span><span class="sxs-lookup"><span data-stu-id="aeb13-156">AltMedium</span></span>              | <span data-ttu-id="aeb13-157">\#99FFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-157">\#99FFFFFF</span></span> | <span data-ttu-id="aeb13-158">\#99000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-158">\#99000000</span></span> |
| <span data-ttu-id="aeb13-159">SystemAltMediumHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-159">SystemAltMediumHighColor</span></span>        | <span data-ttu-id="aeb13-160">AltMediumHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-160">AltMediumHigh</span></span>          | <span data-ttu-id="aeb13-161">\#CCFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-161">\#CCFFFFFF</span></span> | <span data-ttu-id="aeb13-162">\#CC000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-162">\#CC000000</span></span> |
| <span data-ttu-id="aeb13-163">SystemAltMediumLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-163">SystemAltMediumLowColor</span></span>         | <span data-ttu-id="aeb13-164">AltMediumLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-164">AltMediumLow</span></span>           | <span data-ttu-id="aeb13-165">\#66FFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-165">\#66FFFFFF</span></span> | <span data-ttu-id="aeb13-166">\#66000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-166">\#66000000</span></span> |
| <span data-ttu-id="aeb13-167">SystemBaseHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-167">SystemBaseHighColor</span></span>             | <span data-ttu-id="aeb13-168">BaseHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-168">BaseHigh</span></span>               | <span data-ttu-id="aeb13-169">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-169">\#FF000000</span></span> | <span data-ttu-id="aeb13-170">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-170">\#FFFFFFFF</span></span> |
| <span data-ttu-id="aeb13-171">SystemBaseLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-171">SystemBaseLowColor</span></span>              | <span data-ttu-id="aeb13-172">BaseLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-172">BaseLow</span></span>                | <span data-ttu-id="aeb13-173">\#33000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-173">\#33000000</span></span> | <span data-ttu-id="aeb13-174">\#33FFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-174">\#33FFFFFF</span></span> |
| <span data-ttu-id="aeb13-175">SystemBaseMediumColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-175">SystemBaseMediumColor</span></span>           | <span data-ttu-id="aeb13-176">BaseMedium</span><span class="sxs-lookup"><span data-stu-id="aeb13-176">BaseMedium</span></span>             | <span data-ttu-id="aeb13-177">\#99000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-177">\#99000000</span></span> | <span data-ttu-id="aeb13-178">\#99FFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-178">\#99FFFFFF</span></span> |
| <span data-ttu-id="aeb13-179">SystemBaseMediumHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-179">SystemBaseMediumHighColor</span></span>       | <span data-ttu-id="aeb13-180">BaseMediumHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-180">BaseMediumHigh</span></span>         | <span data-ttu-id="aeb13-181">\#CC000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-181">\#CC000000</span></span> | <span data-ttu-id="aeb13-182">\#CCFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-182">\#CCFFFFFF</span></span> |
| <span data-ttu-id="aeb13-183">SystemBaseMediumLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-183">SystemBaseMediumLowColor</span></span>        | <span data-ttu-id="aeb13-184">BaseMediumLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-184">BaseMediumLow</span></span>          | <span data-ttu-id="aeb13-185">\#66000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-185">\#66000000</span></span> | <span data-ttu-id="aeb13-186">\#66FFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-186">\#66FFFFFF</span></span> |
| <span data-ttu-id="aeb13-187">SystemChromeAltLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-187">SystemChromeAltLowColor</span></span>         | <span data-ttu-id="aeb13-188">ChromeAltLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-188">ChromeAltLow</span></span>           | <span data-ttu-id="aeb13-189">\#FF171717</span><span class="sxs-lookup"><span data-stu-id="aeb13-189">\#FF171717</span></span> | <span data-ttu-id="aeb13-190">\#FFF2F2F2</span><span class="sxs-lookup"><span data-stu-id="aeb13-190">\#FFF2F2F2</span></span> |
| <span data-ttu-id="aeb13-191">SystemChromeBlackHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-191">SystemChromeBlackHighColor</span></span>      | <span data-ttu-id="aeb13-192">ChromeBlackHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-192">ChromeBlackHigh</span></span>        | <span data-ttu-id="aeb13-193">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-193">\#FF000000</span></span> | <span data-ttu-id="aeb13-194">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-194">\#FF000000</span></span> |
| <span data-ttu-id="aeb13-195">SystemChromeBlackLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-195">SystemChromeBlackLowColor</span></span>       | <span data-ttu-id="aeb13-196">ChromeBlackLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-196">ChromeBlackLow</span></span>         | <span data-ttu-id="aeb13-197">\#33000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-197">\#33000000</span></span> | <span data-ttu-id="aeb13-198">\#33000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-198">\#33000000</span></span> |
| <span data-ttu-id="aeb13-199">SystemChromeBlackMediumLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-199">SystemChromeBlackMediumLowColor</span></span> | <span data-ttu-id="aeb13-200">ChromeBlackMediumLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-200">ChromeBlackMediumLow</span></span>   | <span data-ttu-id="aeb13-201">\#66000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-201">\#66000000</span></span> | <span data-ttu-id="aeb13-202">\#66000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-202">\#66000000</span></span> |
| <span data-ttu-id="aeb13-203">SystemChromeBlackMediumColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-203">SystemChromeBlackMediumColor</span></span>    | <span data-ttu-id="aeb13-204">ChromeBlackMedium</span><span class="sxs-lookup"><span data-stu-id="aeb13-204">ChromeBlackMedium</span></span>      | <span data-ttu-id="aeb13-205">\#CC000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-205">\#CC000000</span></span> | <span data-ttu-id="aeb13-206">\#CC000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-206">\#CC000000</span></span> |
| <span data-ttu-id="aeb13-207">SystemChromeDisabledHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-207">SystemChromeDisabledHighColor</span></span>   | <span data-ttu-id="aeb13-208">ChromeDisabledHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-208">ChromeDisabledHigh</span></span>     | <span data-ttu-id="aeb13-209">\#FFCCCCCC</span><span class="sxs-lookup"><span data-stu-id="aeb13-209">\#FFCCCCCC</span></span> | <span data-ttu-id="aeb13-210">\#FF333333</span><span class="sxs-lookup"><span data-stu-id="aeb13-210">\#FF333333</span></span> |
| <span data-ttu-id="aeb13-211">SystemChromeDisabledLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-211">SystemChromeDisabledLowColor</span></span>    | <span data-ttu-id="aeb13-212">ChromeDisabledLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-212">ChromeDisabledLow</span></span>      | <span data-ttu-id="aeb13-213">\#FF7A7A7A</span><span class="sxs-lookup"><span data-stu-id="aeb13-213">\#FF7A7A7A</span></span> | <span data-ttu-id="aeb13-214">\#FF858585</span><span class="sxs-lookup"><span data-stu-id="aeb13-214">\#FF858585</span></span> |
| <span data-ttu-id="aeb13-215">SystemChromeHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-215">SystemChromeHighColor</span></span>           | <span data-ttu-id="aeb13-216">ChromeHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-216">ChromeHigh</span></span>             | <span data-ttu-id="aeb13-217">\#FFCCCCCC</span><span class="sxs-lookup"><span data-stu-id="aeb13-217">\#FFCCCCCC</span></span> | <span data-ttu-id="aeb13-218">\#FF767676</span><span class="sxs-lookup"><span data-stu-id="aeb13-218">\#FF767676</span></span> |
| <span data-ttu-id="aeb13-219">SystemChromeLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-219">SystemChromeLowColor</span></span>            | <span data-ttu-id="aeb13-220">ChromeLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-220">ChromeLow</span></span>              | <span data-ttu-id="aeb13-221">\#FFF2F2F2</span><span class="sxs-lookup"><span data-stu-id="aeb13-221">\#FFF2F2F2</span></span> | <span data-ttu-id="aeb13-222">\#FF171717</span><span class="sxs-lookup"><span data-stu-id="aeb13-222">\#FF171717</span></span> |
| <span data-ttu-id="aeb13-223">SystemChromeMediumColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-223">SystemChromeMediumColor</span></span>         | <span data-ttu-id="aeb13-224">ChromeMedium</span><span class="sxs-lookup"><span data-stu-id="aeb13-224">ChromeMedium</span></span>           | <span data-ttu-id="aeb13-225">\#FFE6E6E6</span><span class="sxs-lookup"><span data-stu-id="aeb13-225">\#FFE6E6E6</span></span> | <span data-ttu-id="aeb13-226">\#FF1F1F1F</span><span class="sxs-lookup"><span data-stu-id="aeb13-226">\#FF1F1F1F</span></span> |
| <span data-ttu-id="aeb13-227">SystemChromeMediumLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-227">SystemChromeMediumLowColor</span></span>      | <span data-ttu-id="aeb13-228">ChromeMediumLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-228">ChromeMediumLow</span></span>        | <span data-ttu-id="aeb13-229">\#FFF2F2F2</span><span class="sxs-lookup"><span data-stu-id="aeb13-229">\#FFF2F2F2</span></span> | <span data-ttu-id="aeb13-230">\#FF2B2B2B</span><span class="sxs-lookup"><span data-stu-id="aeb13-230">\#FF2B2B2B</span></span> |
| <span data-ttu-id="aeb13-231">SystemChromeWhiteColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-231">SystemChromeWhiteColor</span></span>          | <span data-ttu-id="aeb13-232">ChromeWhite</span><span class="sxs-lookup"><span data-stu-id="aeb13-232">ChromeWhite</span></span>            | <span data-ttu-id="aeb13-233">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-233">\#FFFFFFFF</span></span> | <span data-ttu-id="aeb13-234">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-234">\#FFFFFFFF</span></span> |
| <span data-ttu-id="aeb13-235">SystemListLowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-235">SystemListLowColor</span></span>              | <span data-ttu-id="aeb13-236">ListLow</span><span class="sxs-lookup"><span data-stu-id="aeb13-236">ListLow</span></span>                | <span data-ttu-id="aeb13-237">\#19000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-237">\#19000000</span></span> | <span data-ttu-id="aeb13-238">\#19FFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-238">\#19FFFFFF</span></span> |
| <span data-ttu-id="aeb13-239">SystemListMediumColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-239">SystemListMediumColor</span></span>           | <span data-ttu-id="aeb13-240">ListMedium</span><span class="sxs-lookup"><span data-stu-id="aeb13-240">ListMedium</span></span>             | <span data-ttu-id="aeb13-241">\#33000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-241">\#33000000</span></span> | <span data-ttu-id="aeb13-242">\#33FFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-242">\#33FFFFFF</span></span> |

<span data-ttu-id="aeb13-243">:::row::: :::column:::</span><span class="sxs-lookup"><span data-stu-id="aeb13-243">:::row::: :::column:::</span></span>
        #### Light theme
    :::column-end:::
    :::column:::
        #### Dark theme
    :::column-end:::
<span data-ttu-id="aeb13-244">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="aeb13-244">:::row-end:::</span></span>

#### <a name="base"></a><span data-ttu-id="aeb13-245">Basis</span><span class="sxs-lookup"><span data-stu-id="aeb13-245">Base</span></span>

<span data-ttu-id="aeb13-246">:::row::: :::column::: ![The base light theme](images/themes/light-base.png) :::column-end::: :::column::: ![Das dunkle Basisdesign](images/themes/dark-base.png) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="aeb13-246">:::row::: :::column::: ![The base light theme](images/themes/light-base.png) :::column-end::: :::column::: ![The base dark theme](images/themes/dark-base.png) :::column-end::: :::row-end:::</span></span>

#### <a name="alt"></a><span data-ttu-id="aeb13-247">Alternativ</span><span class="sxs-lookup"><span data-stu-id="aeb13-247">Alt</span></span>

<span data-ttu-id="aeb13-248">:::row::: :::column::: ![Das helle Alternativdesign](images/themes/light-alt.png) :::column-end::: :::column::: ![Das dunkle Alternativdesign](images/themes/dark-alt.png) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="aeb13-248">:::row::: :::column::: ![The alt light theme](images/themes/light-alt.png) :::column-end::: :::column::: ![The alt dark theme](images/themes/dark-alt.png) :::column-end::: :::row-end:::</span></span>

#### <a name="list"></a><span data-ttu-id="aeb13-249">Liste</span><span class="sxs-lookup"><span data-stu-id="aeb13-249">List</span></span>

<span data-ttu-id="aeb13-250">:::row::: :::column::: ![Das helle Listendesign](images/themes/light-list.png) :::column-end::: :::column::: ![Das dunkle Listendesign](images/themes/dark-list.png) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="aeb13-250">:::row::: :::column::: ![The list light theme](images/themes/light-list.png) :::column-end::: :::column::: ![The list dark theme](images/themes/dark-list.png) :::column-end::: :::row-end:::</span></span>

#### <a name="chrome"></a><span data-ttu-id="aeb13-251">Chrom</span><span class="sxs-lookup"><span data-stu-id="aeb13-251">Chrome</span></span>

<span data-ttu-id="aeb13-252">:::row::: :::column::: ![Das helle Chromdesign](images/themes/light-chrome.png) :::column-end::: :::column::: ![Das dunkle Chromdesign](images/themes/dark-chrome.png) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="aeb13-252">:::row::: :::column::: ![The chrome light theme](images/themes/light-chrome.png) :::column-end::: :::column::: ![The chrome dark theme](images/themes/dark-chrome.png) :::column-end::: :::row-end:::</span></span>

### <a name="windows-system-high-contrast-colors"></a><span data-ttu-id="aeb13-253">Windows-Systemfarben mit hohem Kontrast</span><span class="sxs-lookup"><span data-stu-id="aeb13-253">Windows system high-contrast colors</span></span>

<span data-ttu-id="aeb13-254">Zusätzlich zu den Ressourcen, die vom XAML-Framework bereitgestellt werden, gibt es eine Reihe von Farbwerten, die von der Windows-Systempalette abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-254">In addition to the set of resources provided by the XAML framework, there's a set of color values derived from the Windows system palette.</span></span> <span data-ttu-id="aeb13-255">Diese Farben werden nicht speziell für die Windows-Runtime- oder universelle Windows-Plattform-App (UWP) verwendet.</span><span class="sxs-lookup"><span data-stu-id="aeb13-255">These colors are not specific to the Windows Runtime or Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="aeb13-256">Viele der XAML-[Brush](/uwp/api/Windows.UI.Xaml.Media.Brush)-Ressourcen verwenden diese Farben jedoch, wenn das System mit dem Design „HighContrast“ betrieben wird (und die App ausgeführt wird).</span><span class="sxs-lookup"><span data-stu-id="aeb13-256">However, many of the XAML [Brush](/uwp/api/Windows.UI.Xaml.Media.Brush) resources consume these colors when the system is operating (and the app is running) using the "HighContrast" theme.</span></span> <span data-ttu-id="aeb13-257">Das XAML-Framework stellt diese systemweiten Farben als Ressourcen mit Schlüssel bereit.</span><span class="sxs-lookup"><span data-stu-id="aeb13-257">The XAML framework provides these system-wide colors as keyed resources.</span></span> <span data-ttu-id="aeb13-258">Die Schlüssel folgen diesem Benennungsformat: `SystemColor[name]Color`.</span><span class="sxs-lookup"><span data-stu-id="aeb13-258">The keys follow the naming format: `SystemColor[name]Color`.</span></span>

<span data-ttu-id="aeb13-259">Diese Tabelle enthält die systemweiten Farben, die XAML als Ressourcenobjekte aus der Windows-Systempalette abgeleitet bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="aeb13-259">This table lists the system-wide colors that XAML provides as resource objects derived from the Windows system palette.</span></span> <span data-ttu-id="aeb13-260">In der Spalte „Name der erleichterten Bedienung“ wird gezeigt, wie Farben in der Windows-Einstellungs-UI beschriftet werden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-260">The "Ease of Access name" column shows how color is labeled in the Windows settings UI.</span></span> <span data-ttu-id="aeb13-261">In der Spalte „Einfacher Name für HighContrast“ wird mit einem Wort beschrieben, wie die Farbe für die allgemeinen XAML-Steuerelemente angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-261">The "Simple HighContrast name" column is a one word description of how the color is applied across the XAML common controls.</span></span> <span data-ttu-id="aeb13-262">Sie wird als Teil der Pinselbenennungskonvention verwendet, die später erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-262">It's used as part of the brush naming convention that we explain later.</span></span> <span data-ttu-id="aeb13-263">Die in der Spalte „Anfänglicher Standardwert“ aufgeführten Werte erhalten Sie, wenn das System nicht mit hohem Kontrast ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-263">The "Initial default" column shows the values you'd get if the system is not running in high contrast at all.</span></span>

| <span data-ttu-id="aeb13-264">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="aeb13-264">Key</span></span>                           | <span data-ttu-id="aeb13-265">Name der erleichterten Bedienung</span><span class="sxs-lookup"><span data-stu-id="aeb13-265">Ease of Access name</span></span>            | <span data-ttu-id="aeb13-266">Einfacher Name für HighContrast</span><span class="sxs-lookup"><span data-stu-id="aeb13-266">Simple HighContrast name</span></span> | <span data-ttu-id="aeb13-267">Anfänglicher Standardwert</span><span class="sxs-lookup"><span data-stu-id="aeb13-267">Initial default</span></span> |
|-------------------------------|--------------------------------|--------------------------|-----------------|
| <span data-ttu-id="aeb13-268">SystemColorButtonFaceColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-268">SystemColorButtonFaceColor</span></span>    | <span data-ttu-id="aeb13-269">**Text der Schaltfläche** (Hintergrund)</span><span class="sxs-lookup"><span data-stu-id="aeb13-269">**Button Text** (background)</span></span>   | <span data-ttu-id="aeb13-270">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="aeb13-270">Background</span></span>               | <span data-ttu-id="aeb13-271">\#FFF0F0F0</span><span class="sxs-lookup"><span data-stu-id="aeb13-271">\#FFF0F0F0</span></span>      |
| <span data-ttu-id="aeb13-272">SystemColorButtonTextColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-272">SystemColorButtonTextColor</span></span>    | <span data-ttu-id="aeb13-273">**Text der Schaltfläche** (Vordergrund)</span><span class="sxs-lookup"><span data-stu-id="aeb13-273">**Button Text** (foreground)</span></span>   | <span data-ttu-id="aeb13-274">Vordergrund</span><span class="sxs-lookup"><span data-stu-id="aeb13-274">Foreground</span></span>               | <span data-ttu-id="aeb13-275">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-275">\#FF000000</span></span>      |
| <span data-ttu-id="aeb13-276">SystemColorGrayTextColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-276">SystemColorGrayTextColor</span></span>      | **<span data-ttu-id="aeb13-277">Deaktivierter Text</span><span class="sxs-lookup"><span data-stu-id="aeb13-277">Disabled Text</span></span>**              | <span data-ttu-id="aeb13-278">Deaktiviert</span><span class="sxs-lookup"><span data-stu-id="aeb13-278">Disabled</span></span>                 | <span data-ttu-id="aeb13-279">\#FF6D6D6D</span><span class="sxs-lookup"><span data-stu-id="aeb13-279">\#FF6D6D6D</span></span>      |
| <span data-ttu-id="aeb13-280">SystemColorHighlightColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-280">SystemColorHighlightColor</span></span>     | <span data-ttu-id="aeb13-281">**Ausgewählter Text** (Hintergrund)</span><span class="sxs-lookup"><span data-stu-id="aeb13-281">**Selected Text** (background)</span></span> | <span data-ttu-id="aeb13-282">Hervorheben</span><span class="sxs-lookup"><span data-stu-id="aeb13-282">Highlight</span></span>                | <span data-ttu-id="aeb13-283">\#FF3399FF</span><span class="sxs-lookup"><span data-stu-id="aeb13-283">\#FF3399FF</span></span>      |
| <span data-ttu-id="aeb13-284">SystemColorHighlightTextColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-284">SystemColorHighlightTextColor</span></span> | <span data-ttu-id="aeb13-285">**Ausgewählter Text** (Vordergrund)</span><span class="sxs-lookup"><span data-stu-id="aeb13-285">**Selected Text** (foreground)</span></span> | <span data-ttu-id="aeb13-286">HighlightAlt</span><span class="sxs-lookup"><span data-stu-id="aeb13-286">HighlightAlt</span></span>             | <span data-ttu-id="aeb13-287">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-287">\#FFFFFFFF</span></span>      |
| <span data-ttu-id="aeb13-288">SystemColorHotlightColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-288">SystemColorHotlightColor</span></span>      | **<span data-ttu-id="aeb13-289">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="aeb13-289">Hyperlinks</span></span>**                 | <span data-ttu-id="aeb13-290">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="aeb13-290">Hyperlink</span></span>                | <span data-ttu-id="aeb13-291">\#FF0066CC</span><span class="sxs-lookup"><span data-stu-id="aeb13-291">\#FF0066CC</span></span>      |
| <span data-ttu-id="aeb13-292">SystemColorWindowColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-292">SystemColorWindowColor</span></span>        | **<span data-ttu-id="aeb13-293">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="aeb13-293">Background</span></span>**                 | <span data-ttu-id="aeb13-294">PageBackground</span><span class="sxs-lookup"><span data-stu-id="aeb13-294">PageBackground</span></span>           | <span data-ttu-id="aeb13-295">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-295">\#FFFFFFFF</span></span>      |
| <span data-ttu-id="aeb13-296">SystemColorWindowTextColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-296">SystemColorWindowTextColor</span></span>    | **<span data-ttu-id="aeb13-297">Text</span><span class="sxs-lookup"><span data-stu-id="aeb13-297">Text</span></span>**                       | <span data-ttu-id="aeb13-298">PageText</span><span class="sxs-lookup"><span data-stu-id="aeb13-298">PageText</span></span>                 | <span data-ttu-id="aeb13-299">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-299">\#FF000000</span></span>      |

<span data-ttu-id="aeb13-300">Windows bietet verschiedene kontrastreiche Designs und ermöglicht es dem Benutzer, für ihre Einstellungen für hohen Kontrast durch das Center für erleichterte Bedienung die spezifischen Farben festzulegen, wie hier gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-300">Windows provides different high-contrast themes, and enables the user to set the specific colors to for their high-contrast settings through the Ease of Access Center, as shown here.</span></span> <span data-ttu-id="aeb13-301">Daher ist es nicht möglich, eine definitive Liste der Farbwerte mit hohem Kontrast bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-301">Therefore, it's not possible to provide a definitive list of high-contrast color values.</span></span>

![Die Windows-Einstellungs-UI für hohen Kontrast](images/high-contrast-settings.png)

<span data-ttu-id="aeb13-303">Weitere Informationen zum Unterstützen von Designs mit hohem Kontrast finden Sie unter [Designs mit hohem Kontrast](https://msdn.microsoft.com/library/windows/apps/mt244346).</span><span class="sxs-lookup"><span data-stu-id="aeb13-303">For more info about supporting high-contrast themes, see [High-contrast themes](https://msdn.microsoft.com/library/windows/apps/mt244346).</span></span>

### <a name="system-accent-color"></a><span data-ttu-id="aeb13-304">Systemakzentfarbe</span><span class="sxs-lookup"><span data-stu-id="aeb13-304">System accent color</span></span>

<span data-ttu-id="aeb13-305">Neben der Systemdesignfarben mit hohem Kontrast wird die Akzentfarbe des Systems als spezielle Ressource mit dem Schlüssel `SystemAccentColor` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="aeb13-305">In addition to the system high-contrast theme colors, the system accent color is provided as a special color resource using the key `SystemAccentColor`.</span></span> <span data-ttu-id="aeb13-306">Zur Laufzeit ruft diese Ressource die Farbe ab, die der Benutzer als Akzentfarbe in den Windows-Einstellungen zur Personalisierung angegeben hat.</span><span class="sxs-lookup"><span data-stu-id="aeb13-306">At runtime, this resource gets the color that the user has specified as the accent color in the Windows personalization settings.</span></span>

> [!NOTE]
> <span data-ttu-id="aeb13-307">Die Systemfarbenressourcen können zwar überschrieben werden, es empfiehlt sich jedoch, die Farbauswahl des Benutzers, insbesondere für Einstellungen für hohen Kontrast, zu respektieren.</span><span class="sxs-lookup"><span data-stu-id="aeb13-307">While it’s possible to override the system color resources, it’s a best practice to respect the user’s color choices, especially for high-contrast settings.</span></span>

### <a name="theme-dependent-brushes"></a><span data-ttu-id="aeb13-308">Designabhängige Pinsel</span><span class="sxs-lookup"><span data-stu-id="aeb13-308">Theme-dependent brushes</span></span>

<span data-ttu-id="aeb13-309">Die in den vorherigen Abschnitten gezeigten Farbressourcen dienen zum Festlegen der [Color](/uwp/api/Windows.UI.Xaml.Media.SolidColorBrush.Color)-Eigenschaft von [SolidColorBrush](/uwp/api/Windows.UI.Xaml.Media.SolidColorBrush)-Ressourcen in den Systemdesign-Ressourcenwörterbüchern.</span><span class="sxs-lookup"><span data-stu-id="aeb13-309">The color resources shown in the preceding sections are used to set the [Color](/uwp/api/Windows.UI.Xaml.Media.SolidColorBrush.Color) property of [SolidColorBrush](/uwp/api/Windows.UI.Xaml.Media.SolidColorBrush) resources in the system theme resource dictionaries.</span></span> <span data-ttu-id="aeb13-310">Sie verwenden die Pinselressourcen, um die Farbe auf XAML-Elemente anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-310">You use the brush resources to apply the color to XAML elements.</span></span> <span data-ttu-id="aeb13-311">Die Schlüssel für die Pinselressourcen folgen diesem Benennungsformat: `SystemControl[Simple HighContrast name][Simple light/dark name]Brush`.</span><span class="sxs-lookup"><span data-stu-id="aeb13-311">The keys for the brush resources follow the naming format: `SystemControl[Simple HighContrast name][Simple light/dark name]Brush`.</span></span> <span data-ttu-id="aeb13-312">Beispiel: `SystemControlBackroundAltHighBrush`.</span><span class="sxs-lookup"><span data-stu-id="aeb13-312">For example, `SystemControlBackroundAltHighBrush`.</span></span>

<span data-ttu-id="aeb13-313">Sehen wir uns an, wie der Farbwert für diesen Pinsel zur Laufzeit bestimmt wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-313">Let’s look at how the color value for this brush is determined at run-time.</span></span> <span data-ttu-id="aeb13-314">In den Ressourcenverzeichnissen „Light“ und „Dark“ wird dieser Pinsel wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="aeb13-314">In the "Light" and "Dark" resource dictionaries, this brush is defined like this:</span></span>

`<SolidColorBrush x:Key="SystemControlBackgroundAltHighBrush" Color="{StaticResource SystemAltHighColor}"/>`

<span data-ttu-id="aeb13-315">Im Ressourcenverzeichnis „HighContrast“ wird dieser Pinsel wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="aeb13-315">In the "HighContrast" resource dictionary, this brush is defined like this:</span></span>

`<SolidColorBrush x:Key="SystemControlBackgroundAltHighBrush" Color="{ThemeResource SystemColorButtonFaceColor}"/>`

<span data-ttu-id="aeb13-316">Wenn dieser Pinsel auf ein XAML-Element angewendet wird, wird die Farbe zur Laufzeit durch das aktuelle Design bestimmt, wie in dieser Tabelle zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="aeb13-316">When this brush is applied to a XAML element, its color is determined at run-time by the current theme, as shown in this table.</span></span>

| <span data-ttu-id="aeb13-317">Design</span><span class="sxs-lookup"><span data-stu-id="aeb13-317">Theme</span></span>        | <span data-ttu-id="aeb13-318">Einfacher Farbname</span><span class="sxs-lookup"><span data-stu-id="aeb13-318">Color simple name</span></span> | <span data-ttu-id="aeb13-319">Farbressource</span><span class="sxs-lookup"><span data-stu-id="aeb13-319">Color resource</span></span>             | <span data-ttu-id="aeb13-320">Laufzeitwert</span><span class="sxs-lookup"><span data-stu-id="aeb13-320">Runtime value</span></span>                                              |
|--------------|-------------------|----------------------------|------------------------------------------------------------|
| <span data-ttu-id="aeb13-321">Light</span><span class="sxs-lookup"><span data-stu-id="aeb13-321">Light</span></span>        | <span data-ttu-id="aeb13-322">AltHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-322">AltHigh</span></span>           | <span data-ttu-id="aeb13-323">SystemAltHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-323">SystemAltHighColor</span></span>         | <span data-ttu-id="aeb13-324">\#FFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="aeb13-324">\#FFFFFFFF</span></span>                                                 |
| <span data-ttu-id="aeb13-325">Dark</span><span class="sxs-lookup"><span data-stu-id="aeb13-325">Dark</span></span>         | <span data-ttu-id="aeb13-326">AltHigh</span><span class="sxs-lookup"><span data-stu-id="aeb13-326">AltHigh</span></span>           | <span data-ttu-id="aeb13-327">SystemAltHighColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-327">SystemAltHighColor</span></span>         | <span data-ttu-id="aeb13-328">\#FF000000</span><span class="sxs-lookup"><span data-stu-id="aeb13-328">\#FF000000</span></span>                                                 |
| <span data-ttu-id="aeb13-329">HighContrast</span><span class="sxs-lookup"><span data-stu-id="aeb13-329">HighContrast</span></span> | <span data-ttu-id="aeb13-330">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="aeb13-330">Background</span></span>        | <span data-ttu-id="aeb13-331">SystemColorButtonFaceColor</span><span class="sxs-lookup"><span data-stu-id="aeb13-331">SystemColorButtonFaceColor</span></span> | <span data-ttu-id="aeb13-332">Die in den Einstellungen für den Hintergrund der Schaltfläche angegebene Farbe.</span><span class="sxs-lookup"><span data-stu-id="aeb13-332">The color specified in settings for the button background.</span></span> |

<span data-ttu-id="aeb13-333">Sie können das Benennungsschema `SystemControl[Simple HighContrast name][Simple light/dark name]Brush` verwenden, um zu bestimmen, welcher Pinsel auf Ihre eigenen XAML-Elemente angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="aeb13-333">You can use the `SystemControl[Simple HighContrast name][Simple light/dark name]Brush` naming scheme to determine which brush to apply to your own XAML elements.</span></span>

<!--
For many examples of how the brushes are used in the XAML control templates, see the [Default control styles and templates](default-control-styles-and-templates.md).
-->

> [!NOTE]
> <span data-ttu-id="aeb13-334">Nicht jede Kombination aus \[*Einfacher Name für HighContrast*\]\[*Einfacher Name für hell/dunkel*\] wird als Pinselressource bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="aeb13-334">Not every combination of \[*Simple HighContrast name*\]\[*Simple light/dark name*\] is provided as a brush resource.</span></span>

## <a name="the-xaml-type-ramp"></a><span data-ttu-id="aeb13-335">Die XAML-Typhierarchie</span><span class="sxs-lookup"><span data-stu-id="aeb13-335">The XAML type ramp</span></span>

<span data-ttu-id="aeb13-336">Die Datei „themeresources.xaml“ definiert verschiedene Ressourcen, die einen [Style](https://msdn.microsoft.com/library/windows/apps/br208849) definieren, den Sie auf Textcontainer in Ihrer UI speziell für [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) oder [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565) anwenden können.</span><span class="sxs-lookup"><span data-stu-id="aeb13-336">The themeresources.xaml file defines several resources that define a [Style](https://msdn.microsoft.com/library/windows/apps/br208849) that you can apply to text containers in your UI, specifically for either [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) or [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565).</span></span> <span data-ttu-id="aeb13-337">Dies sind nicht die impliziten Standardstile.</span><span class="sxs-lookup"><span data-stu-id="aeb13-337">These are not the default implicit styles.</span></span> <span data-ttu-id="aeb13-338">Sie werden bereitgestellt, um Ihnen das Erstellen von XAML-UI-Definitionen zu erleichtern, die der in [Richtlinien für Schriftarten](../style/typography.md) dokumentierten *Windows-Typhierarchie* entsprechen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-338">They are provided to make it easier for you to create XAML UI definitions that match the *Windows type ramp* documented in [Guidelines for fonts](../style/typography.md).</span></span>

<span data-ttu-id="aeb13-339">Diese Stile sind für Textattribute gedacht, die Sie auf den gesamten Textcontainer anwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="aeb13-339">These styles are for text attributes that you want applied to the whole text container.</span></span> <span data-ttu-id="aeb13-340">Wenn Sie Stile nur auf Textabschnitte anwenden möchten, legen Sie Attribute für die Textelemente im Container fest, zum Beispiel für [Run](https://msdn.microsoft.com/library/windows/apps/br209959) in [TextBlock.Inlines](https://msdn.microsoft.com/library/windows/apps/br209668) oder für [Paragraph](https://msdn.microsoft.com/library/windows/apps/br244503) in [RichTextBlock.Blocks](https://msdn.microsoft.com/library/windows/apps/br244347).</span><span class="sxs-lookup"><span data-stu-id="aeb13-340">If you want styles applied just to sections of the text, set attributes on the text elements within the container, such as on a [Run](https://msdn.microsoft.com/library/windows/apps/br209959) in [TextBlock.Inlines](https://msdn.microsoft.com/library/windows/apps/br209668) or on a [Paragraph](https://msdn.microsoft.com/library/windows/apps/br244503) in [RichTextBlock.Blocks](https://msdn.microsoft.com/library/windows/apps/br244347).</span></span>

<span data-ttu-id="aeb13-341">Die Stile sehen bei Anwendung auf ein [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)-Element wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="aeb13-341">The styles look like this when applied to a [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652):</span></span>

![Textblock-Stile](../style/images/type/text-block-type-ramp.svg)

```XAML
<TextBlock Text="Header" Style="{StaticResource HeaderTextBlockStyle}"/>
<TextBlock Text="SubHeader" Style="{StaticResource SubheaderTextBlockStyle}"/>
<TextBlock Text="Title" Style="{StaticResource TitleTextBlockStyle}"/>
<TextBlock Text="SubTitle" Style="{StaticResource SubtitleTextBlockStyle}"/>
<TextBlock Text="Base" Style="{StaticResource BaseTextBlockStyle}"/>
<TextBlock Text="Body" Style="{StaticResource BodyTextBlockStyle}"/>
<TextBlock Text="Caption" Style="{StaticResource CaptionTextBlockStyle}"/>
```

<span data-ttu-id="aeb13-343">Eine Anleitung zur Verwendung der UWP-Typhierarchie in Ihrer App finden Sie unter [Typografie in UWP-Apps](../style/typography.md).</span><span class="sxs-lookup"><span data-stu-id="aeb13-343">For guidance on how to use the UWP type ramp in your app, see [Typography in UWP apps](../style/typography.md).</span></span>

### <a name="basetextblockstyle"></a><span data-ttu-id="aeb13-344">BaseTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-344">BaseTextBlockStyle</span></span>

<span data-ttu-id="aeb13-345">**TargetType**: [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)</span><span class="sxs-lookup"><span data-stu-id="aeb13-345">**TargetType**: [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)</span></span>

<span data-ttu-id="aeb13-346">Stellt die gemeinsamen Eigenschaften für alle anderen [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)-Textcontainerstile bereit.</span><span class="sxs-lookup"><span data-stu-id="aeb13-346">Supplies the common properties for all the other [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) container styles.</span></span>

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

### <a name="headertextblockstyle"></a><span data-ttu-id="aeb13-347">HeaderTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-347">HeaderTextBlockStyle</span></span>

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

### <a name="subheadertextblockstyle"></a><span data-ttu-id="aeb13-348">SubheaderTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-348">SubheaderTextBlockStyle</span></span>

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

### <a name="titletextblockstyle"></a><span data-ttu-id="aeb13-349">TitleTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-349">TitleTextBlockStyle</span></span>

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

### <a name="subtitletextblockstyle"></a><span data-ttu-id="aeb13-350">SubtitleTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-350">SubtitleTextBlockStyle</span></span>

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

### <a name="bodytextblockstyle"></a><span data-ttu-id="aeb13-351">BodyTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-351">BodyTextBlockStyle</span></span>

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

### <a name="captiontextblockstyle"></a><span data-ttu-id="aeb13-352">CaptionTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-352">CaptionTextBlockStyle</span></span>

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

### <a name="baserichtextblockstyle"></a><span data-ttu-id="aeb13-353">BaseRichTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-353">BaseRichTextBlockStyle</span></span>

<span data-ttu-id="aeb13-354">**TargetType**: [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565)</span><span class="sxs-lookup"><span data-stu-id="aeb13-354">**TargetType**: [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565)</span></span>

<span data-ttu-id="aeb13-355">Stellt die gemeinsamen Eigenschaften für alle anderen [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565)-Containerstile bereit.</span><span class="sxs-lookup"><span data-stu-id="aeb13-355">Supplies the common properties for all the other [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565) container styles.</span></span>

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

### <a name="bodyrichtextblockstyle"></a><span data-ttu-id="aeb13-356">BodyRichTextBlockStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-356">BodyRichTextBlockStyle</span></span>

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

<span data-ttu-id="aeb13-357">**Hinweis**: Die [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565)-Stile verfügen nicht über alle Texthierarchiestile von [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652). Dies liegt hauptsächlich daran, dass das blockbasierte Dokumentobjektmodell für **RichTextBlock** das Festlegen von Attributen für die einzelnen Textelemente erleichtert.</span><span class="sxs-lookup"><span data-stu-id="aeb13-357">**Note**:  The [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/br227565) styles don't have all the text ramp styles that [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) does, mainly because the block-based document object model for **RichTextBlock** makes it easier to set attributes on the individual text elements.</span></span> <span data-ttu-id="aeb13-358">Außerdem entsteht, wenn Sie [TextBlock.Text](https://msdn.microsoft.com/library/windows/apps/br209676) mit der XAML-Inhaltseigenschaft festlegen, eine Situation, in der kein zu formatierendes Textelement vorhanden ist und Sie daher den Container formatieren müssen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-358">Also, setting [TextBlock.Text](https://msdn.microsoft.com/library/windows/apps/br209676) using the XAML content property introduces a situation where there is no text element to style and thus you'd have to style the container.</span></span> <span data-ttu-id="aeb13-359">Das ist für **RichTextBlock** kein Problem, da sein Textinhalt immer in spezifischen Textelementen wie [Paragraph](https://msdn.microsoft.com/library/windows/apps/br244503) enthalten sein muss, in denen Sie XAML-Stile für die Kopfzeile, die Seitenunterüberschrift und ähnliche Texthierarchiedefinitionen festlegen können.</span><span class="sxs-lookup"><span data-stu-id="aeb13-359">That isn't an issue for **RichTextBlock** because its text content always has to be in specific text elements like [Paragraph](https://msdn.microsoft.com/library/windows/apps/br244503), which is where you might apply XAML styles for page header, page subheader and similar text ramp definitions.</span></span>

## <a name="miscellaneous-named-styles"></a><span data-ttu-id="aeb13-360">Sonstige benannte Stile</span><span class="sxs-lookup"><span data-stu-id="aeb13-360">Miscellaneous Named styles</span></span>

<span data-ttu-id="aeb13-361">Es gibt eine Reihe von weiteren [Style](https://msdn.microsoft.com/library/windows/apps/br208849)-Definitionen mit Schlüsseln, die Sie auf ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element anders als den impliziten Standardstil anwenden können.</span><span class="sxs-lookup"><span data-stu-id="aeb13-361">There's an additional set of keyed [Style](https://msdn.microsoft.com/library/windows/apps/br208849) definitions you can apply to style a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) differently than its default implicit style.</span></span>

### <a name="textblockbuttonstyle"></a><span data-ttu-id="aeb13-362">TextBlockButtonStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-362">TextBlockButtonStyle</span></span>

<span data-ttu-id="aeb13-363">**TargetType**: [ButtonBase](https://msdn.microsoft.com/library/windows/apps/br227736)</span><span class="sxs-lookup"><span data-stu-id="aeb13-363">**TargetType**: [ButtonBase](https://msdn.microsoft.com/library/windows/apps/br227736)</span></span>

<span data-ttu-id="aeb13-364">Wenden Sie diesen Stil auf ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element an, wenn Sie Text anzeigen müssen, auf den ein Benutzer klicken kann, um Aktionen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-364">Apply this style to a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) when you need to show text that a user can click to take action.</span></span> <span data-ttu-id="aeb13-365">Der Text wird mithilfe der aktuellen Akzentfarbe formatiert, um ihn als interaktiv hervorzuheben, und weist Fokusrechtecke auf, die gut für Text geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="aeb13-365">The text is styled using the current accent color to distinguish it as interactive and has focus rectangles that work well for text.</span></span> <span data-ttu-id="aeb13-366">Im Gegensatz zum impliziten Stil eines [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/br242739)-Elements unterstreicht der **TextBlockButtonStyle** den Text nicht.</span><span class="sxs-lookup"><span data-stu-id="aeb13-366">Unlike the implicit style of a [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/br242739), the **TextBlockButtonStyle** does not underline the text.</span></span>

<span data-ttu-id="aeb13-367">Die Vorlage formatiert außerdem den angezeigten Text für die Verwendung von **SystemControlHyperlinkBaseMediumBrush** (für den Zustand „PointerOver“), **SystemControlHighlightBaseMediumLowBrush** (für den Zustand „Pressed“) und **SystemControlDisabledBaseLowBrush** (für den Zustand „Disabled“).</span><span class="sxs-lookup"><span data-stu-id="aeb13-367">The template also styles the presented text to use **SystemControlHyperlinkBaseMediumBrush** (for "PointerOver" state), **SystemControlHighlightBaseMediumLowBrush** (for "Pressed" state) and **SystemControlDisabledBaseLowBrush** (for "Disabled" state).</span></span>

<span data-ttu-id="aeb13-368">Hier ist ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element mit der angewendeten **TextBlockButtonStyle**-Ressource.</span><span class="sxs-lookup"><span data-stu-id="aeb13-368">Here's a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) with the **TextBlockButtonStyle** resource applied to it.</span></span>

```XAML
<Button Content="Clickable text" Style="{StaticResource TextBlockButtonStyle}"
        Click="Button_Click"/>
```

<span data-ttu-id="aeb13-369">Es sieht ungefähr so aus:</span><span class="sxs-lookup"><span data-stu-id="aeb13-369">It looks like this:</span></span>

![Eine Schaltfläche, die wie Text aussieht](images/styles-textblock-button-style.png)

### <a name="navigationbackbuttonnormalstyle"></a><span data-ttu-id="aeb13-371">NavigationBackButtonNormalStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-371">NavigationBackButtonNormalStyle</span></span>

<span data-ttu-id="aeb13-372">**TargetType**: [Button](https://msdn.microsoft.com/library/windows/apps/br209265)</span><span class="sxs-lookup"><span data-stu-id="aeb13-372">**TargetType**: [Button](https://msdn.microsoft.com/library/windows/apps/br209265)</span></span>

<span data-ttu-id="aeb13-373">Dieser [Style](https://msdn.microsoft.com/library/windows/apps/br208849) stellt eine vollständige Vorlage für ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element bereit, bei der es sich um die Navigationsschaltfläche „Zurück“ für eine Navigations-App handeln kann.</span><span class="sxs-lookup"><span data-stu-id="aeb13-373">This [Style](https://msdn.microsoft.com/library/windows/apps/br208849) provides a complete template for a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) that can be the navigation back button for a navigation app.</span></span> <span data-ttu-id="aeb13-374">Die Standardgröße ist 40 x 40 Pixel.</span><span class="sxs-lookup"><span data-stu-id="aeb13-374">The default dimensions are 40 x 40 pixels.</span></span> <span data-ttu-id="aeb13-375">Um den Stil anzupassen, können Sie die Eigenschaften [Height](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height), [Width](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width), [FontSize](https://msdn.microsoft.com/library/windows/apps/br209406) und andere für Ihr **Button**-Element explizit festlegen oder einen abgeleiteten Stil mithilfe von [BasedOn](https://msdn.microsoft.com/library/windows/apps/br208852) erstellen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-375">To tailor the styling you can either explicitly set the [Height](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height), [Width](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width), [FontSize](https://msdn.microsoft.com/library/windows/apps/br209406), and other properties on your **Button** or create a derived style using [BasedOn](https://msdn.microsoft.com/library/windows/apps/br208852).</span></span>

<span data-ttu-id="aeb13-376">Hier ist ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element mit der angewendeten **NavigationBackButtonNormalStyle**-Ressource.</span><span class="sxs-lookup"><span data-stu-id="aeb13-376">Here's a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) with the **NavigationBackButtonNormalStyle** resource applied to it.</span></span>

```XAML
<Button Style="{StaticResource NavigationBackButtonNormalStyle}" />
```

<span data-ttu-id="aeb13-377">Es sieht ungefähr so aus:</span><span class="sxs-lookup"><span data-stu-id="aeb13-377">It looks like this:</span></span>

![Eine als Zurückschaltfläche formatierte Schaltfläche](images/styles-back-button-normal.png)

### <a name="navigationbackbuttonsmallstyle"></a><span data-ttu-id="aeb13-379">NavigationBackButtonSmallStyle</span><span class="sxs-lookup"><span data-stu-id="aeb13-379">NavigationBackButtonSmallStyle</span></span>

<span data-ttu-id="aeb13-380">**TargetType**: [Button](https://msdn.microsoft.com/library/windows/apps/br209265)</span><span class="sxs-lookup"><span data-stu-id="aeb13-380">**TargetType**: [Button](https://msdn.microsoft.com/library/windows/apps/br209265)</span></span>

<span data-ttu-id="aeb13-381">Dieser [Style](https://msdn.microsoft.com/library/windows/apps/br208849) stellt eine vollständige Vorlage für ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element bereit, bei der es sich um die Navigationsschaltfläche „Zurück“ für eine Navigations-App handeln kann.</span><span class="sxs-lookup"><span data-stu-id="aeb13-381">This [Style](https://msdn.microsoft.com/library/windows/apps/br208849) provides a complete template for a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) that can be the navigation back button for a navigation app.</span></span> <span data-ttu-id="aeb13-382">Sie ähnelt **NavigationBackButtonNormalStyle**, aber die Größe beträgt 30x30 Pixel.</span><span class="sxs-lookup"><span data-stu-id="aeb13-382">It's similar to **NavigationBackButtonNormalStyle**, but its dimensions are 30 x 30 pixels.</span></span>

<span data-ttu-id="aeb13-383">Dies ist ein [Button](https://msdn.microsoft.com/library/windows/apps/br209265)-Element mit der angewendeten **NavigationBackButtonSmallStyle**-Ressource.</span><span class="sxs-lookup"><span data-stu-id="aeb13-383">Here's a [Button](https://msdn.microsoft.com/library/windows/apps/br209265) with the **NavigationBackButtonSmallStyle** resource applied to it.</span></span>

```XAML
<Button Style="{StaticResource NavigationBackButtonSmallStyle}" />
```

## <a name="troubleshooting-theme-resources"></a><span data-ttu-id="aeb13-384">Problembehandlung für Designressourcen</span><span class="sxs-lookup"><span data-stu-id="aeb13-384">Troubleshooting theme resources</span></span>

<span data-ttu-id="aeb13-385">Wenn Sie den [Richtlinien für die Verwendung von Designressourcen](#guidelines-for-using-theme-resources) nicht folgen, kann unerwartetes Verhalten im Zusammenhang mit Designs in Ihrer App auftreten.</span><span class="sxs-lookup"><span data-stu-id="aeb13-385">If you don’t follow the [guidelines for using theme resources](#guidelines-for-using-theme-resources), you might see unexpected behavior related to themes in your app.</span></span>

<span data-ttu-id="aeb13-386">Wenn Sie beispielsweise ein Flyout mit hellem Design öffnen, ändern sich auch Teile der App mit dem dunklen Design so, als wären sie im hellen Design.</span><span class="sxs-lookup"><span data-stu-id="aeb13-386">For example, when you open a light-themed flyout, parts of your dark-themed app also change as if they were in the light theme.</span></span> <span data-ttu-id="aeb13-387">Wenn Sie zu einer Seite mit hellem Design und dann zurück navigieren, sieht die ursprüngliche Seite mit dunklem Design (oder Teile davon) so aus, als wäre sie im hellen Design.</span><span class="sxs-lookup"><span data-stu-id="aeb13-387">Or if you navigate to a light-themed page and then navigate back, the original dark-themed page (or parts of it) now looks as though it is in the light theme.</span></span>

<span data-ttu-id="aeb13-388">Diese Arten von Problemen treten in der Regel auf, wenn Sie ein Standard-Design und ein HighContrast-Design für die Unterstützung von Szenarien mit hohem Kontrast bereitstellen und dann Light- und Dark-Designs in verschiedenen Teilen der App verwenden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-388">Typically, these types of issues occur when you provide a "Default" theme and a "HighContrast" theme to support high-contrast scenarios, and then use both "Light" and "Dark" themes in different parts of your app.</span></span>

<span data-ttu-id="aeb13-389">Betrachten Sie beispielsweise diese Definition eines Designwörterbuchs:</span><span class="sxs-lookup"><span data-stu-id="aeb13-389">For example, consider this theme dictionary definition:</span></span>

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

<span data-ttu-id="aeb13-390">Intuitiv sieht sie richtig aus.</span><span class="sxs-lookup"><span data-stu-id="aeb13-390">Intuitively, this looks correct.</span></span> <span data-ttu-id="aeb13-391">Sie möchten die Farbe ändern, auf die durch `myBrush` mit hohem Kontrast verwiesen wird. Außerhalb des hohen Kontrasts vertrauen Sie aber auf die [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md), um sicherzustellen, dass `myBrush` auf die richtige Farbe für das Design verweist.</span><span class="sxs-lookup"><span data-stu-id="aeb13-391">You want to change the color pointed to by `myBrush` when in high-contrast, but when not in high-contrast, you rely on the [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md) to make sure that `myBrush` points to the right color for your theme.</span></span> <span data-ttu-id="aeb13-392">Wenn Ihre App nie [FrameworkElement.RequestedTheme](https://msdn.microsoft.com/library/windows/apps/dn298515) für Elemente in der visuellen Struktur festgelegt hat, funktioniert dies in der Regel wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="aeb13-392">If your app never has [FrameworkElement.RequestedTheme](https://msdn.microsoft.com/library/windows/apps/dn298515) set on elements within its visual tree, this will typically work as expected.</span></span> <span data-ttu-id="aeb13-393">Allerdings treten Probleme in Ihrer App auf, sobald Sie das Design verschiedener Teile der visuellen Struktur ändern.</span><span class="sxs-lookup"><span data-stu-id="aeb13-393">However, you run into problems in your app as soon as you start to re-theme different parts of your visual tree.</span></span>

<span data-ttu-id="aeb13-394">Das Problem tritt auf, da Pinsel im Gegensatz zu den meisten anderen XAML-Typen freigegebene Ressourcen sind.</span><span class="sxs-lookup"><span data-stu-id="aeb13-394">The problem occurs because brushes are shared resources, unlike most other XAML types.</span></span> <span data-ttu-id="aeb13-395">Wenn Sie zwei Elemente in XAML-Unterstrukturen mit verschiedenen Designs haben, die auf die gleiche Pinselressource verweisen, und das Framework für jede Teilstruktur eine Aktualisierung der Ausdrücke der [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md) durchführt, werden Änderungen an der freigegebenen Pinselressource in der anderen untergeordneten Struktur wiedergegeben, was nicht dem gewünschten Ergebnis entspricht.</span><span class="sxs-lookup"><span data-stu-id="aeb13-395">If you have 2 elements in XAML sub-trees with different themes that reference the same brush resource, then as the framework walks each sub-tree to update its [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md) expressions, changes to the shared brush resource are reflected in the other sub-tree, which is not your intended result.</span></span>

<span data-ttu-id="aeb13-396">Ersetzen Sie zum Beheben dieses Problems das Standard-Wörterbuch durch separate Designwörterbücher für die Light- und Dark-Designs zusätzlich zu „HighContrast“:</span><span class="sxs-lookup"><span data-stu-id="aeb13-396">To fix this, replace the "Default" dictionary with separate theme dictionaries for both "Light" and "Dark" themes in addition to "HighContrast":</span></span>

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

<span data-ttu-id="aeb13-397">Allerdings treten weiterhin Probleme auf, wenn auf eine dieser Ressourcen in geerbten Eigenschaften wie [Foreground](https://msdn.microsoft.com/library/windows/apps/br209414) verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-397">However, problems still occur if any of these resources are referenced in inherited properties like [Foreground](https://msdn.microsoft.com/library/windows/apps/br209414).</span></span> <span data-ttu-id="aeb13-398">Die benutzerdefinierte Steuerelementvorlage gibt möglicherweise die Vordergrundfarbe für ein Element mit der [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md) an, aber wenn das Framework den geerbten Wert an die untergeordneten Elemente weitergibt, stellt es einen direkten Verweis auf die Ressource bereit, die durch den Ausdruck der {ThemeResource}-Markuperweiterung aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="aeb13-398">Your custom control template might specify the foreground color of an element using the [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md), but when the framework propagates the inherited value to child elements, it provides a direct reference to the resource that was resolved by the {ThemeResource} markup extension expression.</span></span> <span data-ttu-id="aeb13-399">Dies führt zu Problemen, wenn das Framework Designänderungen verarbeitet, während es die visuelle Struktur des Steuerelements durchläuft.</span><span class="sxs-lookup"><span data-stu-id="aeb13-399">This causes problems when the framework processes theme changes as it walks your control's visual tree.</span></span> <span data-ttu-id="aeb13-400">Es wertet den Ausdruck der {ThemeResource}-Markuperweiterung neu aus, um eine neue Pinselressource abzurufen, gibt diesen Verweis aber noch nicht an die untergeordneten Elemente des Steuerelements weiter; dies geschieht später, zum Beispiel beim nächsten Messwertdurchlauf.</span><span class="sxs-lookup"><span data-stu-id="aeb13-400">It re-evaluates the {ThemeResource} markup extension expression to get a new brush resource but doesn’t yet propagate this reference down to the children of your control; this happens later, such as during the next measure pass.</span></span>

<span data-ttu-id="aeb13-401">Nach dem Durchlaufen der visuellen Struktur des Steuerelements in Reaktion auf eine Designänderung durchläuft das Framework daher die untergeordneten Elemente und aktualisiert Ausdrücke der [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md) für sie oder für Objekte, die für ihre Eigenschaften festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="aeb13-401">As a result, after walking the control visual tree in response to a theme change, the framework walks the children and updates any [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md) expressions set on them, or on objects set on their properties.</span></span> <span data-ttu-id="aeb13-402">Hier tritt das Problem auf. Das Framework durchläuft die Pinselressource, und da die Farbe mit einer {ThemeResource}-Markuperweiterung angegeben wird, erfolgt eine erneute Auswertung.</span><span class="sxs-lookup"><span data-stu-id="aeb13-402">This is where the problem occurs; the framework walks the brush resource and because it specifies its color using a {ThemeResource} markup extension, it's re-evaluated.</span></span>

<span data-ttu-id="aeb13-403">An dieser Stelle hat das Framework Ihr Designverzeichnis anscheinend „verunreinigt“, da es jetzt eine Ressource aus einem Wörterbuch enthält, für die die Farbe durch ein anderes Wörterbuch festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-403">At this point, the framework appears to have polluted your theme dictionary because it now has a resource from one dictionary that has its color set from another dictionary.</span></span>

<span data-ttu-id="aeb13-404">Um dieses Problem zu beheben, verwenden Sie die [{StaticResource}-Markuperweiterung](../../xaml-platform/staticresource-markup-extension.md) anstatt der [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="aeb13-404">To fix this problem, use the [{StaticResource} markup extension](../../xaml-platform/staticresource-markup-extension.md) instead of [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md).</span></span> <span data-ttu-id="aeb13-405">Mit den angewendeten Richtlinien sehen die Designverzeichnisse wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="aeb13-405">With the guidelines applied, the theme dictionaries look like this:</span></span>

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

<span data-ttu-id="aeb13-406">Beachten Sie, dass die [{ThemeResource}-Markuperweiterung](../../xaml-platform/themeresource-markup-extension.md) weiterhin im HighContrast-Wörterbuch anstelle der [{StaticResource}-Markuperweiterung](../../xaml-platform/staticresource-markup-extension.md) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-406">Notice that the [{ThemeResource} markup extension](../../xaml-platform/themeresource-markup-extension.md) is still used in the "HighContrast" dictionary instead of [{StaticResource} markup extension](../../xaml-platform/staticresource-markup-extension.md).</span></span> <span data-ttu-id="aeb13-407">Diese Situation fällt unter die Ausnahme, die weiter oben in den Richtlinien angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="aeb13-407">This situation falls under the exception given earlier in the guidelines.</span></span> <span data-ttu-id="aeb13-408">Die meisten Pinselwerte für das HighContrast-Design verwenden eine Farbauswahl, die global vom System gesteuert wird, aber für XAML als Ressource mit einem speziellen Namen („SystemColor“ ist dem Namen vorangestellt) verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="aeb13-408">Most of the brush values that are used for the "HighContrast" theme are using color choices that are globally controlled by the system, but exposed to XAML as a specially-named resource (those prefixed with ‘SystemColor’ in the name).</span></span> <span data-ttu-id="aeb13-409">Das System ermöglicht es den Benutzern, im Center für erleichterte Bedienung die spezifischen Farben festzulegen, die für ihre Einstellungen für hohen Kontrast verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-409">The system enables the user to set the specific colors that should be used for their high contrast settings through the Ease of Access Center.</span></span> <span data-ttu-id="aeb13-410">Diese Farbauswahl gilt für die speziell benannten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="aeb13-410">Those color choices are applied to the specially-named resources.</span></span> <span data-ttu-id="aeb13-411">Das XAML-Framework verwendet das gleiche Designänderungsereignis, um auch diese Pinsel zu aktualisieren, wenn es erkennt, dass sie auf Systemebene geändert wurden.</span><span class="sxs-lookup"><span data-stu-id="aeb13-411">The XAML framework uses the same theme changed event to also update these brushes when it detects they’ve changed at the system level.</span></span> <span data-ttu-id="aeb13-412">Darum wird hier die {ThemeResource}-Markuperweiterung verwendet.</span><span class="sxs-lookup"><span data-stu-id="aeb13-412">This is why the {ThemeResource} markup extension is used here.</span></span>