---
author: stevewhims
Description: Design your app to support the layouts and fonts of multiple languages, including RTL (right-to-left) flow direction.
title: Layout und Schriften anpassen und RTL unterstützen
ms.assetid: F2522B07-017D-40F1-B3C8-C4D0DFD03AC3
label: Adjust layout and fonts, and support RTL
template: detail.hbs
ms.author: stwhi
ms.date: 05/11/2018
ms.topic: article
keywords: Windows 10, UWP, Lokalisierbarkeit, Lokalisierung, rtl, ltr
ms.localizationpriority: medium
ms.openlocfilehash: ac69701eca128d327dfd80cfddc7fad41c50c50e
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6036820"
---
# <a name="adjust-layout-and-fonts-and-support-rtl"></a><span data-ttu-id="1b1eb-103">Layout und Schriften anpassen und RTL unterstützen</span><span class="sxs-lookup"><span data-stu-id="1b1eb-103">Adjust layout and fonts, and support RTL</span></span>
<span data-ttu-id="1b1eb-104">Entwerfen Sie Ihre App so, dass die Layouts und Schriften mehrerer Sprachen unterstützen – beispielsweise auch den Textfluss von rechts nach links (right-to-left, RTL).</span><span class="sxs-lookup"><span data-stu-id="1b1eb-104">Design your app to support the layouts and fonts of multiple languages, including RTL (right-to-left) flow direction.</span></span> <span data-ttu-id="1b1eb-105">Die Textflussrichtung ist die Richtung, in der ein Text geschrieben und angezeigt wird, und die UI-Elemente auf der Seite werden entsprechend gelesen.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-105">Flow direction is the direction in which script is written and displayed, and the UI elements on the page are scanned by the eye.</span></span>

## <a name="layout-guidelines"></a><span data-ttu-id="1b1eb-106">Layoutrichtlinien</span><span class="sxs-lookup"><span data-stu-id="1b1eb-106">Layout guidelines</span></span>
<span data-ttu-id="1b1eb-107">Sprachen wie Deutsch und Finnisch benötigen in der Regel mehr Zeichen als Englisch.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-107">Languages such as German and Finnish typically use more characters than English does.</span></span> <span data-ttu-id="1b1eb-108">Fernöstliche Schriften benötigen normalerweise mehr Höhe.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-108">Far Eastern fonts typically require more height.</span></span> <span data-ttu-id="1b1eb-109">Und bei Sprachen wie Arabisch und Hebräisch muss die Leserichtung in Textfeldern und des App-Elementen von rechts nach links (RTL) verlaufen.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-109">And languages such as Arabic and Hebrew require that layout panels and text elements be laid out in right-to-left (RTL) reading order.</span></span>

<span data-ttu-id="1b1eb-110">Wegen dieser Unterschiede in den Metriken des übersetzten Textes empfehlen wir, dass Sie keine absolute Positionierung, feste Breiten oder feste Höhen in Ihrer Benutzeroberfläche (UI) verwenden.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-110">Because of these variations in the metrics of translated text, we recommend that you don't bake absolute positioning, fixed widths, or fixed heights into your user interface (UI).</span></span> <span data-ttu-id="1b1eb-111">Nutzen Sie stattdessen die dynamischen Layoutmechanismen, die in den Windows-UI-Elementen integriert sind.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-111">Instead, take advantage of the dynamic layout mechanisms that are built into the Windows UI elements.</span></span> <span data-ttu-id="1b1eb-112">Beispielsweise werden Inhaltssteuerelemente (z. B. Schaltflächen), Elementsteuerelemente (z. B. Grid- und Listenansichten) sowie Layoutfelder (z. B. Grids und Stackpanels) automatisch an ihre Inhalte angepasst.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-112">For example, content controls (such as buttons), items controls (such as grid views and list views), and layout panels (such as grids and stackpanels) automatically resize and reflow by default to fit their content.</span></span> <span data-ttu-id="1b1eb-113">Durch die Pseudolokalisierung für die App werden problematische Fälle aufgedeckt, in denen UI-Elemente nicht richtig an den Inhalt angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-113">Pseudo-localize your app to uncover any problematic edge cases where your UI elements don't size to content properly.</span></span>

<span data-ttu-id="1b1eb-114">Die empfohlene Methode ist ein dynamisches Layout, das in den meisten Fällen anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-114">Dynamic layout is the recommended technique, and you'll be able to use it in the majority of cases.</span></span> <span data-ttu-id="1b1eb-115">Weniger empfehlenswert, aber immer noch besser als das Festlegen von Größen im Markup für die Benutzeroberfläche, ist das Festlegen von Layoutwerten als Funktion der Sprache.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-115">Less preferable, but still better than baking sizes into your UI markup, is to set layout values as a function of language.</span></span> <span data-ttu-id="1b1eb-116">Es folgt ein Beispiel für die Bereitstellung einer Width-Eigenschaft in Ihrer App als Ressource, die von Lokalisierern der jeweiligen Sprache entsprechend festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-116">Here's an example of how you can expose a Width property in your app as a resource that localizers can set appropriately per language.</span></span> <span data-ttu-id="1b1eb-117">Fügen Sie zunächst in der Ressourcendatei Ihrer App (.resw) eine Eigenschaftskennung mit dem Namen „TitleText.Width” hinzu (anstelle von „TitleText” können Sie einen beliebigen Namen verwenden).</span><span class="sxs-lookup"><span data-stu-id="1b1eb-117">First, in your app's Resources File (.resw), add a property identifier with the name "TitleText.Width" (instead of "TitleText", you can use any name you like).</span></span> <span data-ttu-id="1b1eb-118">Verwenden Sie dann **x:Uid**, um UI-Elemente mit dieser Eigenschaftskennung zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-118">Then, use an **x:Uid** to associate one or more UI elements with this property identifier.</span></span>

```xaml
<TextBlock x:Uid="TitleText">
```

<span data-ttu-id="1b1eb-119">Weitere Informationen zu Zeichenfolgenressourcen-Bezeichner und Ressourcendateien (.resw) finden Sie unter Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App.
Weitere Informationen zu Ressourcendateien (.resw), Eigenschaften-IDs und **x:Uid** finden Sie unter [Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im App-Paketmanifest](../../app-resources/localize-strings-ui-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="1b1eb-119">For more info about Resources Files (.resw), property identifiers, and **x:Uid**, see [Localize strings in your UI and app package manifest](../../app-resources/localize-strings-ui-manifest.md).</span></span>

## <a name="fonts"></a><span data-ttu-id="1b1eb-120">Schriften</span><span class="sxs-lookup"><span data-stu-id="1b1eb-120">Fonts</span></span>
<span data-ttu-id="1b1eb-121">Verwenden Sie die [**LanguageFont**](/uwp/api/Windows.Globalization.Fonts.LanguageFont?branch=live)-Schriftzuordnungsklasse für den programmgesteuerten Zugriff auf die empfohlene Familie und Breite und den empfohlenen Grad und Schnitt der Schriftart für eine spezielle Sprache.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-121">Use the [**LanguageFont**](/uwp/api/Windows.Globalization.Fonts.LanguageFont?branch=live) font-mapping class for programmatic access to the recommended font family, size, weight, and style for a particular language.</span></span> <span data-ttu-id="1b1eb-122">Die **LanguageFont**-Klasse ermöglicht den Zugriff auf die richtigen Schriftartinformationen für verschiedene Inhaltskategorien: UI-Kopfzeilen, Benachrichtigungen, Textkörper und Schriften für den Textkörper, die vom Benutzer bearbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-122">The **LanguageFont** class provides access to the correct font info for various categories of content including UI headers, notifications, body text, and user-editable document body fonts.</span></span>

## <a name="mirroring-images"></a><span data-ttu-id="1b1eb-123">Spiegeln von Bildern</span><span class="sxs-lookup"><span data-stu-id="1b1eb-123">Mirroring images</span></span>
<span data-ttu-id="1b1eb-124">Wenn Ihre App Bilder enthält, die für die Leserichtung rechts nach links (RTL) gespiegelt werden müssen (Umkehrung des Bilds), können Sie die **FlowDirection**-Eigenschaft verwenden.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-124">If your app has images that must be mirrored (that is, the same image can be flipped) for RTL, then you can use **FlowDirection**.</span></span>

```xaml
<!-- en-US\localized.xaml -->
<Image ... FlowDirection="LeftToRight" />

<!-- ar-SA\localized.xaml -->
<Image ... FlowDirection="RightToLeft" />
```

<span data-ttu-id="1b1eb-125">Wenn die App ein anderes Bild benötigt, damit dieses richtig umgedreht werden kann, können Sie das Ressourcenverwaltungssystem mit dem `LayoutDirection`-Qualifizierer verwenden (s. LayoutDirection-Abschnitt in [Ressourcen an Sprache, Skalierung und andere Qualifikationsmerkmale anpassen](../../app-resources/tailor-resources-lang-scale-contrast.md#layoutdirection)).</span><span class="sxs-lookup"><span data-stu-id="1b1eb-125">If your app requires a different image to flip the image correctly, then you can use the resource management system with the `LayoutDirection` qualifier (see the LayoutDirection section of [Tailor your resources for language, scale, and other qualifiers](../../app-resources/tailor-resources-lang-scale-contrast.md#layoutdirection)).</span></span> <span data-ttu-id="1b1eb-126">Das System wählt ein Bild mit dem Namen `file.layoutdir-rtl.png` aus, wenn die App-Laufzeitsprache (s. [Benutzerprofilsprachen und App-Manifest-Sprachen verstehen](manage-language-and-region.md))auf eine RTL-Sprache festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-126">The system chooses an image named `file.layoutdir-rtl.png` when the app runtime language (see [Understand user profile languages and app manifest languages](manage-language-and-region.md)) is set to an RTL language.</span></span> <span data-ttu-id="1b1eb-127">Diese Vorgehensweise ist möglicherweise nötig, wenn nicht alle Teile des Bilds umgedreht werden.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-127">This approach may be necessary when some part of the image is flipped, but another part isn't.</span></span>

## <a name="handling-right-to-left-rtl-languages"></a><span data-ttu-id="1b1eb-128">Behandeln von rechts-nach-links-Sprachen (RTL-Sprachen)</span><span class="sxs-lookup"><span data-stu-id="1b1eb-128">Handling right-to-left (RTL) languages</span></span>
<span data-ttu-id="1b1eb-129">Wenn Ihre App für Rechts-Links-Sprachen (RTL) lokalisiert wird, verwenden Sie die Eigenschaft [**FrameworkElement.FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection), und legen Sie symmetrische Abstände und Ränder fest.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-129">When your app is localized for right-to-left (RTL) languages, use the [**FrameworkElement.FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection) property, and set symmetrical padding and margins.</span></span> <span data-ttu-id="1b1eb-130">Layoutpanels wie [**Grid**](/uwp/api/Windows.UI.Xaml.Controls.Grid?branch=live) skalieren und spiegeln sich automatisch gemäß dem von Ihnen festgelegten Wert für **FlowDirection**.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-130">Layout panels such as [**Grid**](/uwp/api/Windows.UI.Xaml.Controls.Grid?branch=live) scale and flip automatically with the value of **FlowDirection** that you set.</span></span>

<span data-ttu-id="1b1eb-131">Legen Sie **FlowDirection** im Stammlayoutpanel (oder Frame) der Seite oder auf der Seite selbst fest.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-131">Set **FlowDirection** on the root layout panel (or frame) of your Page, or on the Page itself.</span></span> <span data-ttu-id="1b1eb-132">Dadurch erben alle enthaltenen Steuerelemente dieses Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-132">This causes all of the controls contained within to inherit that property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b1eb-133">Allerdings wird **FlowDirection** *nicht* automatisch basierend auf der vom Benutzer in den Windows-Einstellungen ausgewählten Anzeigesprache festgelegt, und die Eigenschaft ändert sich auch nicht dynamisch, wenn der Benutzer die Anzeigesprache wechselt.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-133">However, **FlowDirection** is *not* set automatically based on the user's selected display language in Windows settings; nor does it change dynamically in response to the user switching display language.</span></span> <span data-ttu-id="1b1eb-134">Stellt der Benutzer beispielsweise die Windows-Einstellungen von Englisch auf Arabisch um, ändert sich die **FlowDirection**-Eigenschaft *nicht* automatisch von links nach rechts zu rechts nach links.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-134">If the user switches Windows settings from English to Arabic, for example, then the **FlowDirection** property will *not* automatically change from left-to-right to right-to-left.</span></span> <span data-ttu-id="1b1eb-135">Als App-Entwickler müssen Sie **FlowDirection** für die Sprache festlegen, die gerade angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-135">As the app developer, you have to set **FlowDirection** appropriately for the language that you are currently displaying.</span></span>

<span data-ttu-id="1b1eb-136">Die programmatische Technik besteht darin, die Eigenschaft `LayoutDirection` der bevorzugten Benutzeranzeigesprache zu verwenden, um die Eigenschaft [**FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection) festzulegen (siehe Codebeispiel unten).</span><span class="sxs-lookup"><span data-stu-id="1b1eb-136">The programmatic technique is to use the `LayoutDirection` property of the preferred user display language to set the [**FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection) property (see the code example below).</span></span> <span data-ttu-id="1b1eb-137">Die meisten Steuerelemente in Windows verwenden **FlowDirection** bereits.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-137">Most controls included in Windows use **FlowDirection** already.</span></span> <span data-ttu-id="1b1eb-138">Wenn Sie ein benutzerdefiniertes Steuerelement implementieren, sollte es **FlowDirection** verwenden, um entsprechende Layoutänderungen für RTL- und LTR-Sprachen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-138">If you're implementing a custom control, it should use **FlowDirection** to make appropriate layout changes for RTL and LTR languages.</span></span>

```csharp    
this.languageTag = Windows.Globalization.ApplicationLanguages.Languages[0];

// For bidirectional languages, determine flow direction for the root layout panel, and all contained UI.

var flowDirectionSetting = Windows.ApplicationModel.Resources.Core.ResourceContext.GetForCurrentView().QualifierValues["LayoutDirection"];
if (flowDirectionSetting == "LTR")
{
    this.layoutRoot.FlowDirection = Windows.UI.Xaml.FlowDirection.LeftToRight;
}
else
{
    this.layoutRoot.FlowDirection = Windows.UI.Xaml.FlowDirection.RightToLeft;
}
```

```cppwinrt
#include <winrt/Windows.ApplicationModel.Resources.Core.h>
#include <winrt/Windows.Globalization.h>
...

m_languageTag = Windows::Globalization::ApplicationLanguages::Languages().GetAt(0);

// For bidirectional languages, determine flow direction for the root layout panel, and all contained UI.

auto flowDirectionSetting = Windows::ApplicationModel::Resources::Core::ResourceContext::GetForCurrentView().QualifierValues().Lookup(L"LayoutDirection");
if (flowDirectionSetting == L"LTR")
{
    layoutRoot().FlowDirection(Windows::UI::Xaml::FlowDirection::LeftToRight);
}
else
{
    layoutRoot().FlowDirection(Windows::UI::Xaml::FlowDirection::RightToLeft);
}
```

```cpp
this->languageTag = Windows::Globalization::ApplicationLanguages::Languages->GetAt(0);

// For bidirectional languages, determine flow direction for the root layout panel, and all contained UI.

auto flowDirectionSetting = Windows::ApplicationModel::Resources::Core::ResourceContext::GetForCurrentView()->QualifierValues->Lookup("LayoutDirection");
if (flowDirectionSetting == "LTR")
{
    this->layoutRoot->FlowDirection = Windows::UI::Xaml::FlowDirection::LeftToRight;
}
else
{
    this->layoutRoot->FlowDirection = Windows::UI::Xaml::FlowDirection::RightToLeft;
}
```

<span data-ttu-id="1b1eb-139">Die beschriebene Technik macht **FlowDirection** zu einer Funktion der `LayoutDirection`-Eigenschaft der bevorzugten Anzeigesprache.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-139">The technique above makes **FlowDirection** a function of the `LayoutDirection` property of the preferred user display language.</span></span> <span data-ttu-id="1b1eb-140">Wenn Sie diese Logik aus irgendeinem Grund nicht verwenden möchten, können Sie in Ihrer App eine FlowDirection-Eigenschaft als Ressource bereitstellen, die Lokalisierer für jede Sprache, in die sie übersetzen, entsprechend festlegen können.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-140">If for whatever reason you don't want that logic, then you can expose a FlowDirection property in your app as a resource that localizers can set appropriately for each language they translate into.</span></span>

<span data-ttu-id="1b1eb-141">Fügen Sie zunächst in der Ressourcendatei Ihrer App (.resw) eine Eigenschaften-ID mit dem Namen „MainPage.FlowDirection” hinzu (anstelle von „MainPage” können Sie einen beliebigen Namen verwenden).</span><span class="sxs-lookup"><span data-stu-id="1b1eb-141">First, in your app's Resources File (.resw), add a property identifier with the name "MainPage.FlowDirection" (instead of "MainPage", you can use any name you like).</span></span> <span data-ttu-id="1b1eb-142">Verwenden Sie dann **x:Uid**, um Ihr hauptsächliches **Page**-Element (oder dessen Root-Layoutpanel bzw. -Frame) mit dieser Eigenschaftskennung zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-142">Then, use an **x:Uid** to associate your main **Page** element (or its root layout panel or frame) with this property identifier.</span></span>

```xaml
<Page x:Uid="MainPage">
```

<span data-ttu-id="1b1eb-143">Statt von einer einzelnen Codezeile für alle Sprachen sind Sie nun davon abhängig, dass der Übersetzer diese Eigenschaftsressource für jede übersetzte Sprache korrekt „übersetzt”. Seien Sie sich daher bewusst, dass diese Technik eine zusätzliche Quelle für menschliche Fehler sein kann.</span><span class="sxs-lookup"><span data-stu-id="1b1eb-143">Instead of a single line of code for all languages, this depends on the translator "translating" this property resource correctly for each translated language; so be aware that there's that extra opportunity for human error when you use this technique.</span></span>

## <a name="important-apis"></a><span data-ttu-id="1b1eb-144">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="1b1eb-144">Important APIs</span></span>
* [<span data-ttu-id="1b1eb-145">FrameworkElement.FlowDirection</span><span class="sxs-lookup"><span data-stu-id="1b1eb-145">FrameworkElement.FlowDirection</span></span>](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection)
* [<span data-ttu-id="1b1eb-146">LanguageFont</span><span class="sxs-lookup"><span data-stu-id="1b1eb-146">LanguageFont</span></span>](/uwp/api/Windows.Globalization.Fonts.LanguageFont?branch=live)

## <a name="related-topics"></a><span data-ttu-id="1b1eb-147">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1b1eb-147">Related topics</span></span>
* [<span data-ttu-id="1b1eb-148">Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im Paketmanifest der App</span><span class="sxs-lookup"><span data-stu-id="1b1eb-148">Localize strings in your UI and app package manifest</span></span>](../../app-resources/localize-strings-ui-manifest.md)
* [<span data-ttu-id="1b1eb-149">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und andere Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="1b1eb-149">Tailor your resources for language, scale, and other qualifiers</span></span>](../../app-resources/tailor-resources-lang-scale-contrast.md)
* [<span data-ttu-id="1b1eb-150">Benutzerprofilsprachen und App-Manifest-Sprachen verstehen</span><span class="sxs-lookup"><span data-stu-id="1b1eb-150">Understand user profile languages and app manifest languages</span></span>](manage-language-and-region.md)