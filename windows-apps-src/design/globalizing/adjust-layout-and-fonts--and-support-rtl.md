---
author: stevewhims
Description: Design your app to support the layouts and fonts of multiple languages, including RTL (right-to-left) flow direction.
title: Layout und Schriften anpassen und RTL unterstützen
ms.assetid: F2522B07-017D-40F1-B3C8-C4D0DFD03AC3
label: Adjust layout and fonts, and support RTL
template: detail.hbs
ms.author: stwhi
ms.date: 11/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Lokalisierbarkeit, Lokalisierung, rtl, ltr
ms.localizationpriority: medium
ms.openlocfilehash: cf3a2d781dc916fbda9a9d6386dee4e2e6144873
ms.sourcegitcommit: 2470c6596d67e1f5ca26b44fad56a2f89773e9cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
ms.locfileid: "1673977"
---
# <a name="adjust-layout-and-fonts-and-support-rtl"></a><span data-ttu-id="03df2-103">Layout und Schriften anpassen und RTL unterstützen</span><span class="sxs-lookup"><span data-stu-id="03df2-103">Adjust layout and fonts, and support RTL</span></span>

<span data-ttu-id="03df2-104">Entwerfen Sie Ihre App so, dass die Layouts und Schriften mehrerer Sprachen unterstützen – beispielsweise auch den Textfluss von rechts nach links (right-to-left, RTL).</span><span class="sxs-lookup"><span data-stu-id="03df2-104">Design your app to support the layouts and fonts of multiple languages, including RTL (right-to-left) flow direction.</span></span> <span data-ttu-id="03df2-105">Die Textflussrichtung ist die Richtung, in der ein Text geschrieben und angezeigt wird, und die UI-Elemente auf der Seite werden entsprechend gelesen.</span><span class="sxs-lookup"><span data-stu-id="03df2-105">Flow direction is the direction in which script is written and displayed, and the UI elements on the page are scanned by the eye.</span></span>

## <a name="layout-guidelines"></a><span data-ttu-id="03df2-106">Layoutrichtlinien</span><span class="sxs-lookup"><span data-stu-id="03df2-106">Layout guidelines</span></span>

<span data-ttu-id="03df2-107">Sprachen wie Deutsch und Finnisch benötigen in der Regel mehr Zeichen als Englisch.</span><span class="sxs-lookup"><span data-stu-id="03df2-107">Languages such as German and Finnish typically use more characters than English does.</span></span> <span data-ttu-id="03df2-108">Fernöstliche Schriften benötigen normalerweise mehr Höhe.</span><span class="sxs-lookup"><span data-stu-id="03df2-108">Far Eastern fonts typically require more height.</span></span> <span data-ttu-id="03df2-109">Und bei Sprachen wie Arabisch und Hebräisch muss die Leserichtung in Textfeldern und des App-Elementen von rechts nach links (RTL) verlaufen.</span><span class="sxs-lookup"><span data-stu-id="03df2-109">And languages such as Arabic and Hebrew require that layout panels and text elements be laid out in right-to-left (RTL) reading order.</span></span>

<span data-ttu-id="03df2-110">Aufgrund der variablen Länge des übersetzten Texts sollten Sie dynamische UI-Layoutmechanismen anstelle von absoluten Positionierungen, festen Breiten oder festen Höhen verwenden.</span><span class="sxs-lookup"><span data-stu-id="03df2-110">Because of the variable length of translated text, you should use dynamic UI layout mechanisms instead of absolute positioning, fixed widths, or fixed heights.</span></span> <span data-ttu-id="03df2-111">Durch die Pseudolokalisierung für die App werden problematische Fälle aufgedeckt, in denen UI-Elemente nicht richtig an den Inhalt angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="03df2-111">Pseudo-localizing your app will uncover any problematic edge cases where your UI elements don't size to content properly.</span></span>

<span data-ttu-id="03df2-112">Verwenden Sie für RTL-Sprachen die Eigenschaft [**FrameworkElement.FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection), und legen Sie symmetrische Abstände und Ränder fest.</span><span class="sxs-lookup"><span data-stu-id="03df2-112">For RTL languages, use the [**FrameworkElement.FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection) property, and set symmetrical padding and margins.</span></span> <span data-ttu-id="03df2-113">Layoutpanels wie [**Grid**](/uwp/api/Windows.UI.Xaml.Controls.Grid?branch=live) skalieren und spiegeln sich automatisch gemäß dem von Ihnen festgelegten Wert für **FlowDirection**.</span><span class="sxs-lookup"><span data-stu-id="03df2-113">Layout panels such as [**Grid**](/uwp/api/Windows.UI.Xaml.Controls.Grid?branch=live) scale and flip automatically with the value of **FlowDirection** that you set.</span></span>

<span data-ttu-id="03df2-114">Es folgt ein Beispiel für die Bereitstellung einer FlowDirection-Eigenschaft in Ihrer App als Ressource, die von Lokalisierern entsprechend festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="03df2-114">Here's an example of how you can expose a FlowDirection property in your app as a resource that localizers can set appropriately.</span></span>

<span data-ttu-id="03df2-115">Fügen Sie zunächst in der Ressourcendatei Ihrer App (.resw) eine Eigenschaften-ID mit dem Namen „MainPage.FlowDirection” hinzu (anstelle von „MainPage” können Sie einen beliebigen Namen verwenden).</span><span class="sxs-lookup"><span data-stu-id="03df2-115">First, in your app's Resources File (.resw), add a property identifier with the name "MainPage.FlowDirection" (instead of "MainPage", you can use any name you like).</span></span>

<span data-ttu-id="03df2-116">Verwenden Sie dann **x:Uid**, um Ihr hauptsächliches **Page**-Element mit dieser Eigenschaftskennung zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="03df2-116">Then, use an **x:Uid** to associate your main **Page** element with this property identifier.</span></span>

```xaml
<Page x:Uid="MainPage">
```

<span data-ttu-id="03df2-117">Weitere Informationen zu Zeichenfolgenressourcen-Bezeichner und Ressourcendateien (.resw) finden Sie unter Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App.
Weitere Informationen zu Ressourcendateien (.resw), Eigenschaften-IDs und **x:Uid** finden Sie unter [Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im App-Paketmanifest](../../app-resources/localize-strings-ui-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="03df2-117">For more info about Resources Files (.resw), property identifiers, and **x:Uid**, see [Localize strings in your UI and app package manifest](../../app-resources/localize-strings-ui-manifest.md).</span></span>

<span data-ttu-id="03df2-118">Vermeiden Sie, absolute Layoutwerte für ein beliebiges Benutzeroberflächenelement basierend auf der Sprache festzulegen.</span><span class="sxs-lookup"><span data-stu-id="03df2-118">You should avoid setting absolute layout values on any UI element based on language.</span></span> <span data-ttu-id="03df2-119">Wenn das jedoch absolut unvermeidbar ist, können Sie eine Eigenschaftskennung der Form „TitleText.Width” erstellen.</span><span class="sxs-lookup"><span data-stu-id="03df2-119">But if it's absolutely unavoidable, then you can create a property identifier of the form "TitleText.Width".</span></span>

```xaml
<TextBlock x:Uid="TitleText">
```

## <a name="fonts"></a><span data-ttu-id="03df2-120">Schriften</span><span class="sxs-lookup"><span data-stu-id="03df2-120">Fonts</span></span>

<span data-ttu-id="03df2-121">Verwenden Sie die [**LanguageFont**](/uwp/api/Windows.Globalization.Fonts.LanguageFont?branch=live)-Schriftzuordnungsklasse für den programmgesteuerten Zugriff auf die empfohlene Familie und Breite und den empfohlenen Grad und Schnitt der Schriftart für eine spezielle Sprache.</span><span class="sxs-lookup"><span data-stu-id="03df2-121">Use the [**LanguageFont**](/uwp/api/Windows.Globalization.Fonts.LanguageFont?branch=live) font-mapping class for programmatic access to the recommended font family, size, weight, and style for a particular language.</span></span> <span data-ttu-id="03df2-122">Die **LanguageFont**-Klasse ermöglicht den Zugriff auf die richtigen Schriftartinformationen für verschiedene Inhaltskategorien: UI-Kopfzeilen, Benachrichtigungen, Textkörper und Schriften für den Textkörper, die vom Benutzer bearbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="03df2-122">The **LanguageFont** class provides access to the correct font info for various categories of content including UI headers, notifications, body text, and user-editable document body fonts.</span></span>

## <a name="mirroring-images"></a><span data-ttu-id="03df2-123">Spiegeln von Bildern</span><span class="sxs-lookup"><span data-stu-id="03df2-123">Mirroring images</span></span>

<span data-ttu-id="03df2-124">Wenn Ihre App Bilder enthält, die für die Leserichtung rechts nach links (RTL) gespiegelt werden müssen (Umkehrung des Bilds), können Sie die **FlowDirection**-Eigenschaft verwenden.</span><span class="sxs-lookup"><span data-stu-id="03df2-124">If your app has images that must be mirrored (that is, the same image can be flipped) for RTL, then you can use **FlowDirection**.</span></span>

```xaml
<!-- en-US\localized.xaml -->
<Image ... FlowDirection="LeftToRight" />

<!-- ar-SA\localized.xaml -->
<Image ... FlowDirection="RightToLeft" />
```

<span data-ttu-id="03df2-125">Wenn die App ein anderes Bild benötigt, damit dieses richtig umgedreht werden kann, können Sie das Ressourcenverwaltungssystem mit dem `LayoutDirection`-Qualifizierer verwenden (s. LayoutDirection-Abschnitt in [Ressourcen an Sprache, Skalierung und andere Qualifikationsmerkmale anpassen](../../app-resources/tailor-resources-lang-scale-contrast.md#layoutdirection)).</span><span class="sxs-lookup"><span data-stu-id="03df2-125">If your app requires a different image to flip the image correctly, then you can use the resource management system with the `LayoutDirection` qualifier (see the LayoutDirection section of [Tailor your resources for language, scale, and other qualifiers](../../app-resources/tailor-resources-lang-scale-contrast.md#layoutdirection)).</span></span> <span data-ttu-id="03df2-126">Das System wählt ein Bild mit dem Namen `file.layoutdir-rtl.png` aus, wenn die App-Laufzeitsprache (s. [Benutzerprofilsprachen und App-Manifest-Sprachen verstehen](manage-language-and-region.md))auf eine RTL-Sprache festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="03df2-126">The system chooses an image named `file.layoutdir-rtl.png` when the app runtime language (see [Understand user profile languages and app manifest languages](manage-language-and-region.md)) is set to an RTL language.</span></span> <span data-ttu-id="03df2-127">Diese Vorgehensweise ist möglicherweise nötig, wenn nicht alle Teile des Bilds umgedreht werden.</span><span class="sxs-lookup"><span data-stu-id="03df2-127">This approach may be necessary when some part of the image is flipped, but another part isn't.</span></span>

## <a name="best-practices-for-handling-right-to-left-rtl-languages"></a><span data-ttu-id="03df2-128">Bewährte Methoden für die Behandlung von Sprachen, die von rechts nach links gelesen werden (RTL-Sprachen)</span><span class="sxs-lookup"><span data-stu-id="03df2-128">Best practices for handling right-to-left (RTL) languages</span></span>

<span data-ttu-id="03df2-129">Wenn Ihre App für Sprachen lokalisiert wurde, die von rechts nach links gelesen werden (RTL-Sprachen), können Sie APIs verwenden, um die standardmäßige Textrichtung für das Root-Layout-Panel Ihrer Seite festzulegen</span><span class="sxs-lookup"><span data-stu-id="03df2-129">When your app is localized for right-to-left (RTL) languages, use APIs to set the default text direction for the root layout panel of your Page.</span></span> <span data-ttu-id="03df2-130">So wird erreicht, dass alle Steuerelemente, die in Root-Panel enthalten sind, richtig auf die standardmäßige Textrichtung reagieren.</span><span class="sxs-lookup"><span data-stu-id="03df2-130">This causes all of the controls contained within the root panel to respond appropriately to the default text direction.</span></span> <span data-ttu-id="03df2-131">Wenn mehr als eine Sprache unterstützt wird, verwenden Sie `LayoutDirection` für die bevorzugte App-Laufzeitsprache, um die Eigenschaft [**FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection) festzulegen (s. Codebeispiel unten).</span><span class="sxs-lookup"><span data-stu-id="03df2-131">When more than one language is supported, use `LayoutDirection` for the top app runtime language to set the [**FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection) property (see code example below).</span></span> <span data-ttu-id="03df2-132">Die meisten Steuerelemente in Windows verwenden **FlowDirection** bereits.</span><span class="sxs-lookup"><span data-stu-id="03df2-132">Most controls included in Windows use **FlowDirection** already.</span></span> <span data-ttu-id="03df2-133">Wenn Sie benutzerdefinierte Steuerelemente implementieren, sollte **FlowDirection** verwendet werden, um entsprechende Layoutänderungen für RTL- und LTR-Sprachen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="03df2-133">If you are implementing custom controls, they should use **FlowDirection** to make appropriate layout changes for RTL and LTR languages.</span></span>

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

### <a name="rtl-faq"></a><span data-ttu-id="03df2-134">Häufig gestellte Fragen zu RTL</span><span class="sxs-lookup"><span data-stu-id="03df2-134">RTL FAQ</span></span> 

<span data-ttu-id="03df2-135">**F:** Wird **FlowDirection** automatisch basierend auf der aktuellen Sprachauswahl festgelegt?</span><span class="sxs-lookup"><span data-stu-id="03df2-135">**Q:** Is **FlowDirection** set automatically based on the current language selection?</span></span> <span data-ttu-id="03df2-136">Wenn ich beispielsweise Englisch auswähle, wird dann die Links-nach-rechts-Leserichtung angezeigt, und für Arabisch die Rechts-nach-links-Leserichtung?</span><span class="sxs-lookup"><span data-stu-id="03df2-136">For example, if I select English will it display left to right, and if I select Arabic, will it display right to left?</span></span>

> <span data-ttu-id="03df2-137">**A:** **FlowDirection** ist nicht mit einer Berücksichtigung der Sprache verbunden.</span><span class="sxs-lookup"><span data-stu-id="03df2-137">**A:** **FlowDirection** does not take into account the language.</span></span> <span data-ttu-id="03df2-138">Sie legen **FlowDirection** entsprechend für die Sprache fest, die gerade angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="03df2-138">You set **FlowDirection** appropriately for the language you are currently displaying.</span></span> <span data-ttu-id="03df2-139">Siehe obigen Beispielcode.</span><span class="sxs-lookup"><span data-stu-id="03df2-139">See the sample code above.</span></span>

<span data-ttu-id="03df2-140">**F:** Ich kenne mich mit Lokalisierung nicht aus.</span><span class="sxs-lookup"><span data-stu-id="03df2-140">**Q:** I'm not very familiar with localization.</span></span> <span data-ttu-id="03df2-141">Enthalten die Ressourcen bereits die Textflussrichtung?</span><span class="sxs-lookup"><span data-stu-id="03df2-141">Do the resources already contain flow direction?</span></span> <span data-ttu-id="03df2-142">Ist es möglich, die Flussrichtung für die aktuelle Sprache zu bestimmen?</span><span class="sxs-lookup"><span data-stu-id="03df2-142">Is it possible to determine the flow direction from the current language?</span></span>

> <span data-ttu-id="03df2-143">**A:** Wenn Sie sich an die derzeitigen bewährten Methoden halten, enthalten die Ressourcen die Flussrichtung nicht direkt.</span><span class="sxs-lookup"><span data-stu-id="03df2-143">**A:** If you are using current best practices, then resources do not contain flow direction directly.</span></span> <span data-ttu-id="03df2-144">Sie müssen die Flussrichtung für die aktuelle Sprache bestimmen.</span><span class="sxs-lookup"><span data-stu-id="03df2-144">You must determine flow direction for the current language.</span></span> <span data-ttu-id="03df2-145">Dazu gibt es zwei Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="03df2-145">Here are two ways to do this.</span></span>
> 
> <span data-ttu-id="03df2-146">Die bevorzugte Methode ist die Verwendung von **LayoutDirection** für die bevorzugte Sprache, um die Eigenschaft **FlowDirection** für den RootFrame festzulegen.</span><span class="sxs-lookup"><span data-stu-id="03df2-146">The preferred way is to use the **LayoutDirection** for the top preferred language to set the **FlowDirection** property of the RootFrame.</span></span> <span data-ttu-id="03df2-147">Alle Steuerelemente in RootFrame erben „FlowDirection“ vom RootFrame-Element.</span><span class="sxs-lookup"><span data-stu-id="03df2-147">All the controls in the RootFrame inherit FlowDirection from the RootFrame.</span></span>
> 
> <span data-ttu-id="03df2-148">Eine andere Möglichkeit ist das Festlegen von FlowDirection in der RESW-Datei für die RTL-Sprachen, für die Sie die Lokalisierung durchführen.</span><span class="sxs-lookup"><span data-stu-id="03df2-148">Another way is to set the FlowDirection in the .resw file for the RTL languages you are localizing for.</span></span> <span data-ttu-id="03df2-149">Sie können beispielsweise eine arabische RESW-Datei und eine hebräische RESW-Datei verwenden.</span><span class="sxs-lookup"><span data-stu-id="03df2-149">For example, you might have an Arabic resw file and a Hebrew resw file.</span></span> <span data-ttu-id="03df2-150">In diesen Dateien können Sie „x:UID“ zum Festlegen von FlowDirection verwenden.</span><span class="sxs-lookup"><span data-stu-id="03df2-150">In these files you could use x:UID to set the FlowDirection.</span></span> <span data-ttu-id="03df2-151">Diese Methode ist aber fehleranfälliger als die programmgesteuerte Methode.</span><span class="sxs-lookup"><span data-stu-id="03df2-151">This method is more prone to errors than the programmatic method, though.</span></span>

## <a name="important-apis"></a><span data-ttu-id="03df2-152">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="03df2-152">Important APIs</span></span>

* [<span data-ttu-id="03df2-153">FrameworkElement.FlowDirection</span><span class="sxs-lookup"><span data-stu-id="03df2-153">FrameworkElement.FlowDirection</span></span>](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection)
* [<span data-ttu-id="03df2-154">LanguageFont</span><span class="sxs-lookup"><span data-stu-id="03df2-154">LanguageFont</span></span>](/uwp/api/Windows.Globalization.Fonts.LanguageFont?branch=live)

## <a name="related-topics"></a><span data-ttu-id="03df2-155">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="03df2-155">Related topics</span></span>

* [<span data-ttu-id="03df2-156">Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im Paketmanifest der App</span><span class="sxs-lookup"><span data-stu-id="03df2-156">Localize strings in your UI and app package manifest</span></span>](../../app-resources/localize-strings-ui-manifest.md)
* [<span data-ttu-id="03df2-157">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und andere Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="03df2-157">Tailor your resources for language, scale, and other qualifiers</span></span>](../../app-resources/tailor-resources-lang-scale-contrast.md)
* [<span data-ttu-id="03df2-158">Benutzerprofilsprachen und App-Manifest-Sprachen verstehen</span><span class="sxs-lookup"><span data-stu-id="03df2-158">Understand user profile languages and app manifest languages</span></span>](manage-language-and-region.md)