---
description: Beschreibt die Schritte, mit denen Sie die Verwendbarkeit Ihrer UWP-App (Universelle Windows-Plattform) sicherstellen können, wenn ein Design mit hohem Kontrast aktiviert ist.
ms.assetid: FD7CA6F6-A8F1-47D8-AA6C-3F2EC3168C45
title: Designs mit hohem Kontrast
template: detail.hbs
ms.date: 09/28/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: e4e8d5f49d10219a06a36fdfbe7ec3abe236109a
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7700468"
---
# <a name="high-contrast-themes"></a><span data-ttu-id="64adb-104">Designs mit hohem Kontrast</span><span class="sxs-lookup"><span data-stu-id="64adb-104">High contrast themes</span></span>  

<span data-ttu-id="64adb-105">Windows unterstützt Designs mit hohem Kontrast für das Betriebssystem und Apps, die von Benutzern aktiviert werden können.</span><span class="sxs-lookup"><span data-stu-id="64adb-105">Windows supports high contrast themes for the OS and apps that users may choose to enable.</span></span> <span data-ttu-id="64adb-106">Designs mit hohem Kontrast verwenden eine kleine Palette von Farbkombinationen mit hohem Farbkontrast, durch die die Benutzeroberfläche leichter zu erkennen ist.</span><span class="sxs-lookup"><span data-stu-id="64adb-106">High contrast themes use a small palette of contrasting colors that makes the interface easier to see.</span></span>

![Rechner im hellen Design und im Design „Hoher Kontrast (Schwarz)”](images/high-contrast-calculators.png)

*<span data-ttu-id="64adb-108">Rechner im hellen Design und im Design „Hoher Kontrast (Schwarz)”</span><span class="sxs-lookup"><span data-stu-id="64adb-108">Calculator shown in light theme and High Contrast Black theme.</span></span>*

<span data-ttu-id="64adb-109">Sie können über *Einstellungen > Erleichterte Bedienung > Hoher Kontrast* zu einem Design mit hohem Kontrast wechseln.</span><span class="sxs-lookup"><span data-stu-id="64adb-109">You can switch to a high contrast theme by using *Settings > Ease of access > High contrast*.</span></span>

> [!NOTE]
> <span data-ttu-id="64adb-110">Designs mit hohem Kontrast sind nicht mit hellen und dunklen Designs zu verwechseln. Helle und dunkle Designs unterstützen eine deutlich größere Farbpalette ohne Farbkombinationen mit hohem Kontrast.</span><span class="sxs-lookup"><span data-stu-id="64adb-110">Don't confuse high contrast themes with light and dark themes, which allow a much larger color palette that isn't considered to have high contrast.</span></span> <span data-ttu-id="64adb-111">Weitere helle und dunkle Designs finden Sie im Artikel zu [Farben](../style/color.md).</span><span class="sxs-lookup"><span data-stu-id="64adb-111">For more light and dark themes, see the article on [color](../style/color.md).</span></span>

<span data-ttu-id="64adb-112">Während bei allgemeinen Steuerelementen vollständige Unterstützung für hohen Kontrast automatisch verfügbar ist, ist beim Anpassen der Benutzeroberfläche Vorsicht geboten.</span><span class="sxs-lookup"><span data-stu-id="64adb-112">While common controls come with full high contrast support for free, care needs to be taken while customizing your UI.</span></span> <span data-ttu-id="64adb-113">Die Ursache für den häufigsten Fehler bei der Verwendung von Designs mit hohem Kontrast ist die Inlinehartcodierung einer Steuerelementfarbe.</span><span class="sxs-lookup"><span data-stu-id="64adb-113">The most common high contrast bug is caused by hard-coding a color on a control inline.</span></span>

```xaml
<!-- Don't do this! -->
<Grid Background="#E6E6E6">

<!-- Instead, create BrandedPageBackgroundBrush and do this. -->
<Grid Background="{ThemeResource BrandedPageBackgroundBrush}">
```

<span data-ttu-id="64adb-114">Wird die Farbe `#E6E6E6` im ersten Beispiel inline festgelegt, behält das Raster diese Hintergrundfarbe in allen Designs bei.</span><span class="sxs-lookup"><span data-stu-id="64adb-114">When the `#E6E6E6` color is set inline in the first example, the Grid will retain that background color in all themes.</span></span> <span data-ttu-id="64adb-115">Wenn der Benutzer zum Design „Hoher Kontrast (Schwarz)” wechselt, erwartet er, dass Ihre App einen schwarzen Hintergrund hat.</span><span class="sxs-lookup"><span data-stu-id="64adb-115">If the user switches to the High Contrast Black theme, they'll expect your app to have a black background.</span></span> <span data-ttu-id="64adb-116">Da `#E6E6E6` fast weiß ist, sind einige Benutzer möglicherweise nicht in der Lage, mit Ihrer App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="64adb-116">Since `#E6E6E6` is almost white, some users may not be able to interact with your app.</span></span>

<span data-ttu-id="64adb-117">Im zweiten Beispiel wird die [**{ThemeResource}-Markuperweiterung**](../../xaml-platform/themeresource-markup-extension.md) verwendet, um auf eine Farbe in der [**ThemeDictionaries**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.resourcedictionary.themedictionaries.aspx)-Sammlung zu verweisen, bei der es sich um eine dedizierte Eigenschaft eines [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/BR208794)-Elements handelt.</span><span class="sxs-lookup"><span data-stu-id="64adb-117">In the second example, the [**{ThemeResource} markup extension**](../../xaml-platform/themeresource-markup-extension.md) is used to reference a color in the [**ThemeDictionaries**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.resourcedictionary.themedictionaries.aspx) collection, a dedicated property of a [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/BR208794) element.</span></span> <span data-ttu-id="64adb-118">Die **ThemeDictionaries**-Sammlung ermöglicht es XAML, Farben automatisch basierend auf dem aktuellen Design des Benutzers auszutauschen.</span><span class="sxs-lookup"><span data-stu-id="64adb-118">**ThemeDictionaries** allows XAML to automatically swap colors for you based on the user's current theme.</span></span>

## <a name="theme-dictionaries"></a><span data-ttu-id="64adb-119">Designverzeichnisse</span><span class="sxs-lookup"><span data-stu-id="64adb-119">Theme dictionaries</span></span>

<span data-ttu-id="64adb-120">Wenn Sie die Systemstandardfarbe ändern müssen, erstellen Sie eine ThemeDictionaries-Sammlung für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="64adb-120">When you need to change a color from its system default, create a ThemeDictionaries collection for your app.</span></span>

1. <span data-ttu-id="64adb-121">Erstellen Sie zunächst die richtige Grundstruktur (sofern nicht bereits vorhanden).</span><span class="sxs-lookup"><span data-stu-id="64adb-121">Start by creating the proper plumbing, if it doesn't already exist.</span></span> <span data-ttu-id="64adb-122">Erstellen Sie in „App.xaml” eine **ThemeDictionaries**-Sammlung, die mindestens **Default** und **HighContrast** enthält.</span><span class="sxs-lookup"><span data-stu-id="64adb-122">In App.xaml, create a **ThemeDictionaries** collection, including **Default** and **HighContrast** at a minimum.</span></span>
2. <span data-ttu-id="64adb-123">Erstellen Sie unter **Default** den gewünschten [Brush](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.brush.aspx)-Typ (in der Regel **SolidColorBrush**).</span><span class="sxs-lookup"><span data-stu-id="64adb-123">In **Default**, create the type of [Brush](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.brush.aspx) you need, usually a **SolidColorBrush**.</span></span> <span data-ttu-id="64adb-124">Vergeben Sie einen *x:Key*-Namen, der für die Verwendung spezifisch ist.</span><span class="sxs-lookup"><span data-stu-id="64adb-124">Give it a *x:Key* name specific to what it is being used for.</span></span>
3. <span data-ttu-id="64adb-125">Weisen Sie das gewünschte **Color**-Element zu.</span><span class="sxs-lookup"><span data-stu-id="64adb-125">Assign the **Color** you want for it.</span></span>
4. <span data-ttu-id="64adb-126">Kopieren Sie das **Brush**-Objekt in **HighContrast**.</span><span class="sxs-lookup"><span data-stu-id="64adb-126">Copy that **Brush** into **HighContrast**.</span></span>

``` xaml
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.ThemeDictionaries>
            <!-- Default is a fallback if a more precise theme isn't called
            out below -->
            <ResourceDictionary x:Key="Default">
                <SolidColorBrush x:Key="BrandedPageBackgroundBrush" Color="#E6E6E6" />
            </ResourceDictionary>

            <!-- Optional, Light is used in light theme.
            If included, Default will be used for Dark theme -->
            <ResourceDictionary x:Key="Light">
                <SolidColorBrush x:Key="BrandedPageBackgroundBrush" Color="#E6E6E6" />
            </ResourceDictionary>

            <!-- HighContrast is used in all high contrast themes -->
            <ResourceDictionary x:Key="HighContrast">
                <SolidColorBrush x:Key="BrandedPageBackgroundBrush" Color="#E6E6E6" />
            </ResourceDictionary>
        </ResourceDictionary.ThemeDictionaries>
    </ResourceDictionary>
</Application.Resources>
```

<span data-ttu-id="64adb-127">Im letzten Schritt bestimmen Sie, welche Farbe für hohen Kontrast verwendet werden soll. Dies wird im nächsten Abschnitt erläutert.</span><span class="sxs-lookup"><span data-stu-id="64adb-127">The last step is to determine what color to use in high contrast, which is covered in the next section.</span></span>

> [!NOTE]
> <span data-ttu-id="64adb-128">**HighContrast** ist nicht der einzige verfügbare Schlüsselname.</span><span class="sxs-lookup"><span data-stu-id="64adb-128">**HighContrast** is not the only available key name.</span></span> <span data-ttu-id="64adb-129">Es gibt auch noch **HighContrastBlack**, **HighContrastWhite** und **HighContrastCustom**.</span><span class="sxs-lookup"><span data-stu-id="64adb-129">There's also **HighContrastBlack**, **HighContrastWhite**, and **HighContrastCustom**.</span></span> <span data-ttu-id="64adb-130">In den meisten Fällen ist **HighContrast** ausreichend.</span><span class="sxs-lookup"><span data-stu-id="64adb-130">In most cases, **HighContrast** is all you need.</span></span>

## <a name="high-contrast-colors"></a><span data-ttu-id="64adb-131">Farben mit hohem Kontrast</span><span class="sxs-lookup"><span data-stu-id="64adb-131">High contrast colors</span></span>

<span data-ttu-id="64adb-132">Auf der Seite *Einstellungen > Erleichterte Bedienung > Hoher Kontrast* sind standardmäßig vier Designs mit hohem Kontrast verfügbar.</span><span class="sxs-lookup"><span data-stu-id="64adb-132">On the *Settings > Ease of access > High contrast* page, there are 4 high contrast themes by default.</span></span> 


![Einstellungen für hohen Kontrast](images/high-contrast-settings.png)  

*<span data-ttu-id="64adb-134">Nachdem der Benutzer eine Option ausgewählt hat, wird auf der Seite eine Vorschau angezeigt.</span><span class="sxs-lookup"><span data-stu-id="64adb-134">After the user selects an option, the page shows a preview.</span></span>*  

![Ressourcen mit hohem Kontrast](images/high-contrast-resources.png)  

*<span data-ttu-id="64adb-136">Sie können zum Ändern der Werte auf jedes Farbmuster in der Vorschau klicken.</span><span class="sxs-lookup"><span data-stu-id="64adb-136">Every color swatch on the preview can be clicked to change its value.</span></span> <span data-ttu-id="64adb-137">Zudem ist jedes Farbmuster direkt einer XAML-Farbressource zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="64adb-137">Every swatch also directly maps to an XAML color resource.</span></span>*  

<span data-ttu-id="64adb-138">Jede **SystemColor\*Color**-Ressource ist eine Variable, die die Farbe automatisch aktualisiert, wenn der Benutzer Designs mit hohem Kontrast wechselt.</span><span class="sxs-lookup"><span data-stu-id="64adb-138">Each **SystemColor\*Color** resource is a variable that automatically updates color when the user switches high contrast themes.</span></span> <span data-ttu-id="64adb-139">Im Folgenden finden Sie Richtlinien für die Verwendung der einzelnen Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="64adb-139">Following are guidelines for where and when to use each resource.</span></span>

<span data-ttu-id="64adb-140">Ressource</span><span class="sxs-lookup"><span data-stu-id="64adb-140">Resource</span></span> | <span data-ttu-id="64adb-141">Verwendung</span><span class="sxs-lookup"><span data-stu-id="64adb-141">Usage</span></span> |
|--------|-------|
**<span data-ttu-id="64adb-142">SystemColorWindowTextColor</span><span class="sxs-lookup"><span data-stu-id="64adb-142">SystemColorWindowTextColor</span></span>** | <span data-ttu-id="64adb-143">Textkörper, Überschriften, Listen, beliebiger Text, mit dem nicht interagiert werden kann</span><span class="sxs-lookup"><span data-stu-id="64adb-143">Body copy, headings, lists; any text that can't be interacted with</span></span> |
| **<span data-ttu-id="64adb-144">SystemColorHotlightColor</span><span class="sxs-lookup"><span data-stu-id="64adb-144">SystemColorHotlightColor</span></span>** | <span data-ttu-id="64adb-145">Links</span><span class="sxs-lookup"><span data-stu-id="64adb-145">Hyperlinks</span></span> |
| **<span data-ttu-id="64adb-146">SystemColorGrayTextColor</span><span class="sxs-lookup"><span data-stu-id="64adb-146">SystemColorGrayTextColor</span></span>** | <span data-ttu-id="64adb-147">Deaktivierte Benutzeroberflächenelemente</span><span class="sxs-lookup"><span data-stu-id="64adb-147">Disabled UI</span></span> |
| **<span data-ttu-id="64adb-148">SystemColorHighlightTextColor</span><span class="sxs-lookup"><span data-stu-id="64adb-148">SystemColorHighlightTextColor</span></span>** | <span data-ttu-id="64adb-149">Vordergrundfarbe für Text oder Benutzeroberflächenelemente, die sich in Bearbeitung befinden, die ausgewählt sind oder mit denen gegenwärtig interagiert wird</span><span class="sxs-lookup"><span data-stu-id="64adb-149">Foreground color for text or UI that's in progress, selected, or currently being interacted with</span></span> |
| **<span data-ttu-id="64adb-150">SystemColorHighlightColor</span><span class="sxs-lookup"><span data-stu-id="64adb-150">SystemColorHighlightColor</span></span>** | <span data-ttu-id="64adb-151">Hintergrundfarbe für Text oder Benutzeroberflächenelemente, die sich in Bearbeitung befinden, die ausgewählt sind oder mit denen gegenwärtig interagiert wird</span><span class="sxs-lookup"><span data-stu-id="64adb-151">Background color for text or UI that's in progress, selected, or currently being interacted with</span></span> |
| **<span data-ttu-id="64adb-152">SystemColorButtonTextColor</span><span class="sxs-lookup"><span data-stu-id="64adb-152">SystemColorButtonTextColor</span></span>** | <span data-ttu-id="64adb-153">Vordergrundfarbe für Schaltflächen und beliebige Benutzeroberflächenelemente, mit denen interagiert werden kann</span><span class="sxs-lookup"><span data-stu-id="64adb-153">Foreground color for buttons; any UI that can be interacted with</span></span> |
| **<span data-ttu-id="64adb-154">SystemColorButtonFaceColor</span><span class="sxs-lookup"><span data-stu-id="64adb-154">SystemColorButtonFaceColor</span></span>** | <span data-ttu-id="64adb-155">Hintergrundfarbe für Schaltflächen und beliebige Benutzeroberflächenelemente, mit denen interagiert werden kann</span><span class="sxs-lookup"><span data-stu-id="64adb-155">Background color for buttons; any UI that can be interacted with</span></span> |
| **<span data-ttu-id="64adb-156">SystemColorWindowColor</span><span class="sxs-lookup"><span data-stu-id="64adb-156">SystemColorWindowColor</span></span>** | <span data-ttu-id="64adb-157">Hintergrund von Seiten, Bereichen, Popups und Leisten</span><span class="sxs-lookup"><span data-stu-id="64adb-157">Background of pages, panes, popups, and bars</span></span> |

<span data-ttu-id="64adb-158">Häufig ist es hilfreich, sich in vorhandenen Apps, Startseiten oder allgemeinen Steuerelementen anzusehen, wie andere Entwickler ähnliche Probleme beim Entwerfen für hohen Kontrast gelöst haben.</span><span class="sxs-lookup"><span data-stu-id="64adb-158">It's often helpful to look to existing apps, Start, or the common controls to see how others have solved high contrast design problems that are similar to your own.</span></span>

**<span data-ttu-id="64adb-159">Empfohlen</span><span class="sxs-lookup"><span data-stu-id="64adb-159">Do</span></span>**

* <span data-ttu-id="64adb-160">Beachten Sie nach Möglichkeit die Hintergrund-/Vordergrundpaare.</span><span class="sxs-lookup"><span data-stu-id="64adb-160">Respect the background/foreground pairs where possible.</span></span>
* <span data-ttu-id="64adb-161">Testen Sie alle vier Designs mit hohem Kontrast, während die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="64adb-161">Test in all 4 high contrast themes while your app is running.</span></span> <span data-ttu-id="64adb-162">Der Benutzer sollte die App bei einem Wechsel des Designs nicht neu starten müssen.</span><span class="sxs-lookup"><span data-stu-id="64adb-162">The user should not have to restart your app when they switch themes.</span></span>
* <span data-ttu-id="64adb-163">Achten Sie auf Einheitlichkeit.</span><span class="sxs-lookup"><span data-stu-id="64adb-163">Be consistent.</span></span>

**<span data-ttu-id="64adb-164">Nicht empfohlen</span><span class="sxs-lookup"><span data-stu-id="64adb-164">Don't</span></span>**

* <span data-ttu-id="64adb-165">Hartcodierung einer Farbe im Design **HighContrast** – verwenden Sie die **SystemColor\*Color**-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="64adb-165">Hard code a color in the **HighContrast** theme; use the **SystemColor\*Color** resources.</span></span>
* <span data-ttu-id="64adb-166">Berücksichtigen Sie bei der Auswahl einer Farbressource die Ästhetik.</span><span class="sxs-lookup"><span data-stu-id="64adb-166">Choose a color resource for aesthetics.</span></span> <span data-ttu-id="64adb-167">Denken Sie daran, dass sich die Farbressourcen mit dem Design ändern.</span><span class="sxs-lookup"><span data-stu-id="64adb-167">Remember, they change with the theme!</span></span>
* <span data-ttu-id="64adb-168">Verwenden Sie **SystemColorGrayTextColor** nicht für sekundären oder als Hinweis fungierenden Textkörper.</span><span class="sxs-lookup"><span data-stu-id="64adb-168">Don't use **SystemColorGrayTextColor** for body copy that's secondary or acts as a hint.</span></span>


<span data-ttu-id="64adb-169">Im vorherigen Beispiel müssen Sie eine Ressource für **BrandedPageBackgroundBrush** auswählen.</span><span class="sxs-lookup"><span data-stu-id="64adb-169">To continue the earlier example, you need to pick a resource for **BrandedPageBackgroundBrush**.</span></span> <span data-ttu-id="64adb-170">Da der Name bereits besagt, dass dieser Pinsel für einen Hintergrund verwendet wird, ist **SystemColorWindowColor** eine gute Wahl.</span><span class="sxs-lookup"><span data-stu-id="64adb-170">Because the name indicates that it will be used for a background, **SystemColorWindowColor** is a good choice.</span></span>

``` xaml
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.ThemeDictionaries>
            <!-- Default is a fallback if a more precise theme isn't called
            out below -->
            <ResourceDictionary x:Key="Default">
                <SolidColorBrush x:Key="BrandedPageBackgroundBrush" Color="#E6E6E6" />
            </ResourceDictionary>

            <!-- Optional, Light is used in light theme.
            If included, Default will be used for Dark theme -->
            <ResourceDictionary x:Key="Light">
                <SolidColorBrush x:Key="BrandedPageBackgroundBrush" Color="#E6E6E6" />
            </ResourceDictionary>

            <!-- HighContrast is used in all high contrast themes -->
            <ResourceDictionary x:Key="HighContrast">
                <SolidColorBrush x:Key="BrandedPageBackgroundBrush" Color="{ThemeResource SystemColorWindowColor}" />
            </ResourceDictionary>
        </ResourceDictionary.ThemeDictionaries>
    </ResourceDictionary>
</Application.Resources>
```

<span data-ttu-id="64adb-171">Später können Sie dann in Ihrer App den Hintergrund festlegen.</span><span class="sxs-lookup"><span data-stu-id="64adb-171">Later in your app, you can now set the background.</span></span>

```xaml
<Grid Background="{ThemeResource BrandedPageBackgroundBrush}">
```

<span data-ttu-id="64adb-172">Beachten Sie, wie **\{ThemeResource\}** zweimal verwendet wird, einmal um auf **SystemColorWindowColor** und einmal um auf **BrandedPageBackgroundBrush** zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="64adb-172">Note how **\{ThemeResource\}** is used twice, once to reference **SystemColorWindowColor** and again to reference **BrandedPageBackgroundBrush**.</span></span> <span data-ttu-id="64adb-173">Beide Verweise sind erforderlich, damit zur Laufzeit das korrekte Design in Ihrer App verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="64adb-173">Both are required for your app to theme correctly at run time.</span></span> <span data-ttu-id="64adb-174">Dies ist ein guter Zeitpunkt, um die Funktionalität in Ihrer App zu testen.</span><span class="sxs-lookup"><span data-stu-id="64adb-174">This is a good time to test out the functionality in your app.</span></span> <span data-ttu-id="64adb-175">Der Hintergrund des Rasters wird automatisch aktualisiert, wenn Sie zu einem Design mit hohem Kontrast wechseln.</span><span class="sxs-lookup"><span data-stu-id="64adb-175">The Grid's background will automatically update as you switch to a high contrast theme.</span></span> <span data-ttu-id="64adb-176">Beim Wechseln zwischen verschiedenen Designs mit hohem Kontrast wird er ebenfalls aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="64adb-176">It will also update when switching between different high contrast themes.</span></span>

## <a name="when-to-use-borders"></a><span data-ttu-id="64adb-177">Wann sollten Rahmen verwenden werden?</span><span class="sxs-lookup"><span data-stu-id="64adb-177">When to use borders</span></span>

<span data-ttu-id="64adb-178">Für den Hintergrund von Seiten, Bereichen, Popups und Leisten sollte im Design mit hohem Kontrast **SystemColorWindowColor** verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="64adb-178">Pages, panes, popups, and bars should all use **SystemColorWindowColor** for their background in high contrast.</span></span> <span data-ttu-id="64adb-179">Fügen Sie bei Bedarf einen Rahmen nur für hohen Kontrast hinzu, um wichtige Grenzen in Ihrer Benutzeroberfläche beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="64adb-179">Add a high contrast-only border where necessary to preserve important boundaries in your UI.</span></span>

![Ein vom Rest der Seite abgegrenzter Navigationsbereich](images/high-contrast-actions-content.png)  

*<span data-ttu-id="64adb-181">Der Navigationsbereich und die Seite haben im Design mit hohem Kontrast dieselbe Hintergrundfarbe.</span><span class="sxs-lookup"><span data-stu-id="64adb-181">The navigation pane and the page both share the same background color in high contrast.</span></span> <span data-ttu-id="64adb-182">Zur Trennung der beiden Komponenten ist ein Rahmen erforderlich, der nur im Design mit hohem Kontrast verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="64adb-182">A high contrast-only border to divide them is essential.</span></span>*


## <a name="list-items"></a><span data-ttu-id="64adb-183">Listenelemente</span><span class="sxs-lookup"><span data-stu-id="64adb-183">List items</span></span>

<span data-ttu-id="64adb-184">Im Design mit hohem Kontrast wird der Hintergrund von Elementen in ein [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) auf **SystemColorHighlightColor** festgelegt, wenn der Benutzer auf sie zeigt, sie drückt oder auswählt.</span><span class="sxs-lookup"><span data-stu-id="64adb-184">In high contrast, items in a [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) have their background set to **SystemColorHighlightColor** when they are hovered, pressed, or selected.</span></span> <span data-ttu-id="64adb-185">Ein häufiger Fehler bei komplexen Listenelementen ist, dass die Farbe des Inhalts des Listenelements beim Zeigen, Drücken oder Auswählen nicht umgekehrt wird.</span><span class="sxs-lookup"><span data-stu-id="64adb-185">Complex list items commonly have a bug where the content of the list item fails to invert its color when the item is hovered, pressed, or selected.</span></span> <span data-ttu-id="64adb-186">Dies führt dazu, dass das Element nicht gelesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="64adb-186">This makes the item impossible to read.</span></span>

![Einfache Liste im hellen Design und im Design „Hoher Kontrast (Schwarz)”](images/high-contrast-list1.png)

*<span data-ttu-id="64adb-188">Einfache Liste im hellen Design (links) und im Design „Hoher Kontrast (Schwarz)” (rechts).</span><span class="sxs-lookup"><span data-stu-id="64adb-188">A simple list in light theme (left) and High Contrast Black theme (right).</span></span> <span data-ttu-id="64adb-189">Das zweite Element ist ausgewählt. Beachten Sie, dass die Textfarbe im Design mit hohem Kontrast umgekehrt wird.</span><span class="sxs-lookup"><span data-stu-id="64adb-189">The second item is selected; note how its text color is inverted in high contrast.</span></span>*


### <a name="list-items-with-colored-text"></a><span data-ttu-id="64adb-190">Listenelemente mit farbigem Text</span><span class="sxs-lookup"><span data-stu-id="64adb-190">List items with colored text</span></span>

<span data-ttu-id="64adb-191">Das Festlegen von „TextBlock.Foreground” in der [DataTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) des ListView-Steuerelements kann Probleme verursachen.</span><span class="sxs-lookup"><span data-stu-id="64adb-191">One culprit is setting TextBlock.Foreground in the ListView's [DataTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx).</span></span> <span data-ttu-id="64adb-192">Diese Einstellung wird meist vorgenommen, um eine visuelle Hierarchie zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="64adb-192">This is commonly done to establish visual hierarchy.</span></span> <span data-ttu-id="64adb-193">Die Foreground-Eigenschaft ist für das [ListViewItem](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewitem.aspx) festgelegt, und TextBlock-Elemente in der „DataTemplate” erben die richtige Vordergrundfarbe, wenn auf das Element gezeigt, es gedrückt oder ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="64adb-193">The Foreground property is set on the [ListViewItem](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewitem.aspx), and TextBlocks in the DataTemplate inherit the correct Foreground color when the item is hovered, pressed, or selected.</span></span> <span data-ttu-id="64adb-194">Durch das Festlegen der Foreground-Eigenschaft funktioniert die Vererbung jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="64adb-194">However, setting Foreground breaks the inheritance.</span></span>

![Komplexe Liste im hellen Design und im Design „Hoher Kontrast (Schwarz)”](images/high-contrast-list2.png)

*<span data-ttu-id="64adb-196">Komplexe Liste im hellen Design (links) und im Design „Hoher Kontrast (Schwarz)” (rechts).</span><span class="sxs-lookup"><span data-stu-id="64adb-196">Complex list in light theme (left) and High Contrast Black theme (right).</span></span> <span data-ttu-id="64adb-197">Beachten Sie, dass die Farbe der zweiten Zeile des ausgewählten Elements im Design mit hohem Kontrast nicht umgekehrt wurde.</span><span class="sxs-lookup"><span data-stu-id="64adb-197">In high contrast, the second line of the selected item failed to invert.</span></span>*  

<span data-ttu-id="64adb-198">Sie können dieses Problem umgehen, indem Sie die Foreground-Eigenschaft bedingt über einen Stil in einer **ThemeDictionaries**-Sammlung festlegen.</span><span class="sxs-lookup"><span data-stu-id="64adb-198">You can work around this by setting Foreground conditionally via a Style that's in a **ThemeDictionaries** collection.</span></span> <span data-ttu-id="64adb-199">Da die **Foreground**-Eigenschaft nicht durch **SecondaryBodyTextBlockStyle** in **HighContrast** festgelegt wird, wird die Farbe korrekt umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="64adb-199">Because the **Foreground** is not set by **SecondaryBodyTextBlockStyle** in **HighContrast**, its color will correctly invert.</span></span>

```xaml
<!-- In App.xaml... -->
<ResourceDictionary.ThemeDictionaries>
    <ResourceDictionary x:Key="Default">
        <Style
            x:Key="SecondaryBodyTextBlockStyle"
            TargetType="TextBlock"
            BasedOn="{StaticResource BodyTextBlockStyle}">
            <Setter Property="Foreground" Value="{StaticResource SystemControlForegroundBaseMediumBrush}" />
        </Style>
    </ResourceDictionary>

    <ResourceDictionary x:Key="Light">
        <Style
            x:Key="SecondaryBodyTextBlockStyle"
            TargetType="TextBlock"
            BasedOn="{StaticResource BodyTextBlockStyle}">
            <Setter Property="Foreground" Value="{StaticResource SystemControlForegroundBaseMediumBrush}" />
        </Style>
    </ResourceDictionary>

    <ResourceDictionary x:Key="HighContrast">
        <!-- The Foreground Setter is omitted in HighContrast -->
        <Style
            x:Key="SecondaryBodyTextBlockStyle"
            TargetType="TextBlock"
            BasedOn="{StaticResource BodyTextBlockStyle}" />
    </ResourceDictionary>
</ResourceDictionary.ThemeDictionaries>

<!-- Usage in your DataTemplate... -->
<DataTemplate>
    <StackPanel>
        <TextBlock Style="{StaticResource BodyTextBlockStyle}" Text="Double line list item" />

        <!-- Note how ThemeResource is used to reference the Style -->
        <TextBlock Style="{ThemeResource SecondaryBodyTextBlockStyle}" Text="Second line of text" />
    </StackPanel>
</DataTemplate>
```


## <a name="detecting-high-contrast"></a><span data-ttu-id="64adb-200">Erkennen von hohem Kontrast</span><span class="sxs-lookup"><span data-stu-id="64adb-200">Detecting high contrast</span></span>

<span data-ttu-id="64adb-201">Sie können mithilfe von Membern der [**AccessibilitySettings**](https://msdn.microsoft.com/library/windows/apps/BR242237)-Klasse programmgesteuert überprüfen, ob das aktuelle Design ein Design mit hohem Kontrast ist.</span><span class="sxs-lookup"><span data-stu-id="64adb-201">You can programmatically check if the current theme is a high contrast theme by using members of the [**AccessibilitySettings**](https://msdn.microsoft.com/library/windows/apps/BR242237) class.</span></span>

> [!NOTE]
> <span data-ttu-id="64adb-202">Achten Sie darauf, dass Sie den **AccessibilitySettings**-Konstruktor in einem Bereich aufrufen, in dem die App initialisiert ist und bereits Inhalt anzeigt.</span><span class="sxs-lookup"><span data-stu-id="64adb-202">Make sure you call the **AccessibilitySettings** constructor from a scope where the app is initialized and is already displaying content.</span></span>

## <a name="related-topics"></a><span data-ttu-id="64adb-203">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="64adb-203">Related topics</span></span>  
* [<span data-ttu-id="64adb-204">Barrierefreiheit</span><span class="sxs-lookup"><span data-stu-id="64adb-204">Accessibility</span></span>](accessibility.md)
* [<span data-ttu-id="64adb-205">Beispiel für UI-Kontrast und -Einstellungen</span><span class="sxs-lookup"><span data-stu-id="64adb-205">UI contrast and settings sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231539)
* [<span data-ttu-id="64adb-206">XAML-Beispiel für Barrierefreiheit</span><span class="sxs-lookup"><span data-stu-id="64adb-206">XAML accessibility sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=238570)
* [<span data-ttu-id="64adb-207">XAML-Beispiel für hohen Kontrast</span><span class="sxs-lookup"><span data-stu-id="64adb-207">XAML high contrast sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254993)
* [**<span data-ttu-id="64adb-208">AccessibilitySettings</span><span class="sxs-lookup"><span data-stu-id="64adb-208">AccessibilitySettings</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR242237)
