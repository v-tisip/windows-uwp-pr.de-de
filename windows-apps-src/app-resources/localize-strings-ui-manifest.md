---
author: stevewhims
Description: "Wenn Sie möchten, dass Ihre App verschiedene Anzeigesprachen unterstützt, und Ihr Code oder XAML-Markup- oder App-Paketmanifest Zeichenfolgenliterale enthält, verschieben Sie diese Zeichenfolgen in eine Ressourcendatei (.resw). Sie können dann eine übersetzte Kopie dieser Ressourcendatei für jede Sprache erstellen, die Ihre App unterstützt."
title: "Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im App-Paketmanifest"
ms.assetid: E420B9BB-C0F6-4EC0-BA3A-BA2875B69722
label: Localize strings in your UI and app package manifest
template: detail.hbs
ms.author: stwhi
ms.date: 11/01/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
localizationpriority: medium
ms.openlocfilehash: cca9c9b731831ce1c87ee74b7f8b502130ef97fd
ms.sourcegitcommit: d0c93d734639bd31f264424ae5b6fead903a951d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2017
---
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

# <a name="localize-strings-in-your-ui-and-app-package-manifest"></a><span data-ttu-id="e691a-105">Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im App-Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="e691a-105">Localize strings in your UI and app package manifest</span></span>

<span data-ttu-id="e691a-106">Weitere Informationen zu einer Werterhöhung Ihrer App durch Lokalisierung finden Sie unter [Globalisierung und Lokalisierung](../globalizing/globalizing-portal.md).</span><span class="sxs-lookup"><span data-stu-id="e691a-106">For more info about the value proposition of localizing your app, see [Globalization and localization](../globalizing/globalizing-portal.md).</span></span>

<span data-ttu-id="e691a-107">Wenn Sie möchten, dass Ihre App verschiedene Anzeigesprachen unterstützt, sollten Sie Zeichenfolgenliterale, die in Ihrem Code oder XAML-Markup oder App-Paketmanifest enthalten sind, in eine Ressourcendatei (.resw) verschieben.</span><span class="sxs-lookup"><span data-stu-id="e691a-107">If you want your app to support different display languages, and you have string literals in your code or XAML markup or app package manifest, then move those strings into a Resources File (.resw).</span></span> <span data-ttu-id="e691a-108">Sie können dann eine übersetzte Kopie dieser Ressourcendatei für jede Sprache erstellen, die Ihre App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e691a-108">You can then make a translated copy of that Resources File for each language that your app supports.</span></span>

<span data-ttu-id="e691a-109">Hartcodierte Zeichenfolgenliterale können in imperativem Code oder in XAML-Markup stehen, z.B. die **Text** Eigenschaft für einen **TextBlock**.</span><span class="sxs-lookup"><span data-stu-id="e691a-109">Hardcoded string literals can appear in imperative code or in XAML markup, for example as the **Text** property of a **TextBlock**.</span></span> <span data-ttu-id="e691a-110">Sie können auch in Ihrem App-Paketmanifest (die Datei `Package.appxmanifest`) auftreten, z.B. als Wert für den Anzeigenamen auf der Registerkarte „Anwendung” im Manifest-Designer von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e691a-110">They can also appear in your app package manifest (the `Package.appxmanifest` file), for example as the value for Display name on the Application tab of the Visual Studio Manifest Designer.</span></span> <span data-ttu-id="e691a-111">Verschieben Sie diese Zeichenfolgen in eine Ressourcendatei (.resw), und ersetzen Sie die hartcodierten Zeichenfolgenliterale in Ihrer App und in Ihrem Manifest durch Verweise auf Ressourcenbezeichner.</span><span class="sxs-lookup"><span data-stu-id="e691a-111">Move these strings into a Resources File (.resw), and replace the hardcoded string literals in your app and in your manifest with references to resource identifiers.</span></span>

<span data-ttu-id="e691a-112">Während eine Bildressourcendatei immer nur eine Bildressource enthält, sind in einer Zeichenfolgen-Ressourcendatei *mehrere* Zeichenfolgenressourcen enthalten.</span><span class="sxs-lookup"><span data-stu-id="e691a-112">Unlike image resources, where only one image resource is contained in an image resource file, *multiple* string resources are contained in a string resource file.</span></span> <span data-ttu-id="e691a-113">Eine Zeichenfolgen-Ressourcendatei ist die Art von Ressourcendatei (.resw), die Sie üblicherweise in einem \Strings-Ordner Ihres Projekts erstellen.</span><span class="sxs-lookup"><span data-stu-id="e691a-113">A string resource file is a Resources File (.resw), and you typically create this kind of resource file in a \Strings folder in your project.</span></span> <span data-ttu-id="e691a-114">Hintergrundinformationen zur Verwendung von Qualifizierern in den Namen von Ressourcendateien (.resw) finden Sie unter [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und andere Eigenschaften](tailor-resources-lang-scale-contrast.md).</span><span class="sxs-lookup"><span data-stu-id="e691a-114">For background on how to use qualifiers in the names of your Resources Files (.resw), see [Tailor your resources for language, scale, and other qualifiers](tailor-resources-lang-scale-contrast.md).</span></span>

## <a name="create-a-resources-file-resw-and-put-your-strings-in-it"></a><span data-ttu-id="e691a-115">Erstellen einer Ressourcendatei (.resw) und Einfügen von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="e691a-115">Create a Resources File (.resw) and put your strings in it</span></span>

1. <span data-ttu-id="e691a-116">Legen Sie die Standardsprache Ihrer App fest.</span><span class="sxs-lookup"><span data-stu-id="e691a-116">Set your app's default language.</span></span>
    1. <span data-ttu-id="e691a-117">Öffnen Sie `Package.appxmanifest`, während Ihre Projektmappe in Visual Studio geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="e691a-117">With your solution open in Visual Studio, open `Package.appxmanifest`.</span></span>
    2. <span data-ttu-id="e691a-118">Vergewissern Sie sich auf der Registerkarte „Anwendung”, dass die Standardsprache passend festgelegt ist (z.B. auf „en” oder „en-US”).</span><span class="sxs-lookup"><span data-stu-id="e691a-118">On the Application tab, confirm that the Default language is set appropriately (for example, "en" or "en-US").</span></span> <span data-ttu-id="e691a-119">Für die verbleibenden Schritte wird davon ausgegangen, dass Sie die Standardsprache auf "en-US" festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="e691a-119">The remaining steps will assume that you have set the default language to "en-US".</span></span>
    <br><span data-ttu-id="e691a-120">**Hinweis:** Sie müssen zumindest Zeichenfolgenressourcen in der Standardsprache bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e691a-120">**Note** At a minimum, you need to provide string resources localized for this default language.</span></span> <span data-ttu-id="e691a-121">Diese Ressourcen werden geladen, wenn für die bevorzugte Sprache des Benutzers oder die eingestellte Anzeigesprache keine bessere Übereinstimmung gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="e691a-121">Those are the resources that will be loaded if no better match can be found for the user's preferred language or display language settings.</span></span>
2. <span data-ttu-id="e691a-122">Erstellen Sie eine Ressourcendatei (.resw) für die Standardsprache.</span><span class="sxs-lookup"><span data-stu-id="e691a-122">Create a Resources File (.resw) for the default language.</span></span>
    1. <span data-ttu-id="e691a-123">Erstellen Sie unter Ihrem Projektknoten einen neuen Ordner mit dem Namen „Strings”.</span><span class="sxs-lookup"><span data-stu-id="e691a-123">Under your project node, create a new folder and name it "Strings".</span></span>
    2. <span data-ttu-id="e691a-124">Erstellen Sie unter `Strings` einen neuen Unterordner mit dem Namen „en-US”.</span><span class="sxs-lookup"><span data-stu-id="e691a-124">Under `Strings`, create a new sub-folder and name it "en-US".</span></span>
    3. <span data-ttu-id="e691a-125">Erstellen Sie unter `en-US` eine neue Ressourcendatei (.resw). Vergewissern Sie sich, dass sie „Resources.resw” heißt.</span><span class="sxs-lookup"><span data-stu-id="e691a-125">Under `en-US`, create a new Resources File (.resw) and confirm that it is named "Resources.resw".</span></span>
    <br><span data-ttu-id="e691a-126">**Hinweis:** Informationen für den Fall, dass Sie vorhandene .NET-Ressourcendateien (.resx) portieren möchten, finden Sie unter [Portieren von XAML und UI](../porting/wpsl-to-uwp-porting-xaml-and-ui.md#localization-and-globalization).</span><span class="sxs-lookup"><span data-stu-id="e691a-126">**Note** If you have .NET Resources Files (.resx) that you want to port, see [Porting XAML and UI](../porting/wpsl-to-uwp-porting-xaml-and-ui.md#localization-and-globalization).</span></span>
3.  <span data-ttu-id="e691a-127">Öffnen Sie `Resources.resw`, und fügen Sie diese Zeichenfolgenressourcen hinzu.</span><span class="sxs-lookup"><span data-stu-id="e691a-127">Open `Resources.resw` and add these string resources.</span></span>

    `Strings/en-US/Resources.resw`

    ![Ressource hinzufügen, Englisch](images/addresource-en-us.png)

    <span data-ttu-id="e691a-129">In diesem Beispiel ist „Greeting” der Bezeichner einer Zeichenfolgenressource, auf den Sie, wie noch gezeigt wird, im Markup verweisen können.</span><span class="sxs-lookup"><span data-stu-id="e691a-129">In this example, "Greeting" is a string resource identifier that you can refer to from your markup, as we'll show.</span></span> <span data-ttu-id="e691a-130">Für den Bezeichner „Greeting” wird eine Zeichenfolge für eine Text-Eigenschaft bereitgestellt, und es wird eine Zeichenfolge für eine Width-Eigenschaft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="e691a-130">For the identifier "Greeting", a string is provided for a Text property, and a string is provided for a Width property.</span></span> <span data-ttu-id="e691a-131">„Greeting.Text” ist ein Beispiel für einen Eigenschaftsbezeichner, da er der Eigenschaft eines Benutzeroberflächenelements entspricht.</span><span class="sxs-lookup"><span data-stu-id="e691a-131">"Greeting.Text" is an example of a property identifier because it corresponds to a property of a UI element.</span></span> <span data-ttu-id="e691a-132">Es wäre auch möglich, „Greeting.Foreground” in der Spalte „Name” hinzuzufügen, beispielsweise mit dem Wert „Red” in der Spalte „Value”.</span><span class="sxs-lookup"><span data-stu-id="e691a-132">You could also, for example, add "Greeting.Foreground" in the Name column, and set its Value to "Red".</span></span> <span data-ttu-id="e691a-133">Der Bezeichner „Farewell” ist ein einfacher Bezeichner für eine Zeichenfolgenressource. Er verfügt über keine untergeordneten Eigenschaften und kann, wie noch gezeigt wird, aus imperativem Code geladen werden.</span><span class="sxs-lookup"><span data-stu-id="e691a-133">The "Farewell" identifier is a simple string resource identifier; it has no sub-properties and it can be loaded from imperative code, as we'll show.</span></span> <span data-ttu-id="e691a-134">Die Spalte „Kommentar” ist gut geeignet, um spezielle Anweisungen für Übersetzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="e691a-134">The Comment column is a good place to provide any special instructions to translators.</span></span>

    <span data-ttu-id="e691a-135">Da wir in diesem Beispiel mit „Farewell” einen einfachen Bezeichner für Zeichenfolgenressourcen eingetragen haben, können wir *zusätzlich* keine Eigenschaftsbezeichner verwenden, die auf demselben Bezeichner basieren.</span><span class="sxs-lookup"><span data-stu-id="e691a-135">In this example, since we have a simple string resource identifier entry named "Farewell", we cannot *also* have property identifiers based on that same identifier.</span></span> <span data-ttu-id="e691a-136">Das Hinzufügen von „Farewell.Text” würde deshalb dazu führen, dass beim Erstellen von `Resources.resw` der Fehler „Doppelter Eintrag” auftritt.</span><span class="sxs-lookup"><span data-stu-id="e691a-136">So, adding "Farewell.Text" would cause a Duplicate Entry error when building `Resources.resw`.</span></span>

## <a name="refer-to-a-string-resource-identifier-from-xaml-markup"></a><span data-ttu-id="e691a-137">Referenzieren eines Bezeichners für Zeichenfolgenressourcen im XAML-Markup</span><span class="sxs-lookup"><span data-stu-id="e691a-137">Refer to a string resource identifier from XAML markup</span></span>

<span data-ttu-id="e691a-138">Verwenden Sie eine [x:Uid-Direktive](../xaml-platform/x-uid-directive.md), um ein Steuerelement oder ein anderes Element in Ihrem Markup mit dem Bezeichner einer Zeichenfolgenressource zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="e691a-138">You use an [x:Uid directive](../xaml-platform/x-uid-directive.md) to associate a control or other element in your markup with a string resource identifier.</span></span>

**<span data-ttu-id="e691a-139">XAML</span><span class="sxs-lookup"><span data-stu-id="e691a-139">XAML</span></span>**
```xml
<TextBlock x:Uid="Greeting"/>
```

<span data-ttu-id="e691a-140">Zur Laufzeit wird `\Strings\en-US\Resources.resw` geladen (da diese momentan die einzige Ressourcendatei im Projekt ist).</span><span class="sxs-lookup"><span data-stu-id="e691a-140">At run-time, `\Strings\en-US\Resources.resw` is loaded (since right now that's the only Resources File in the project).</span></span> <span data-ttu-id="e691a-141">Die Direktive **x:Uid** im **TextBlock**-Element bewirkt in `Resources.resw` eine Suche nach Eigenschaftsbezeichnern, die den Zeichenfolgenressourcen-Bezeichner „Greeting” enthalten.</span><span class="sxs-lookup"><span data-stu-id="e691a-141">The **x:Uid** directive on the **TextBlock** causes a lookup to take place, to find property identifiers inside `Resources.resw` that contain the string resource identifier "Greeting".</span></span> <span data-ttu-id="e691a-142">Die Eigenschaftsbezeichner „Greeting.Text” und „Greeting.Width” werden gefunden, und ihre Werte werden auf den **TextBlock** angewendet, wobei alle Werte, die lokal im Markup festgelegt sind, überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="e691a-142">The "Greeting.Text" and "Greeting.Width" property identifiers are found and their values are applied to the **TextBlock**, overriding any values set locally in the markup.</span></span> <span data-ttu-id="e691a-143">Der Wert „Greeting.Foreground” würde ebenfalls angewendet, wenn Sie ihn hinzugefügt hätten.</span><span class="sxs-lookup"><span data-stu-id="e691a-143">The "Greeting.Foreground" value would be applied, too, if you'd added that.</span></span> <span data-ttu-id="e691a-144">Es hätte aber keine Auswirkung, wenn Sie in diesem TextBlock-Element **a:Uid** auf „Farewell” festlegen würden, da nur Eigenschaftsbezeichner verwendet werden, um Eigenschaften für XAML-Markupelemente festzulegen.</span><span class="sxs-lookup"><span data-stu-id="e691a-144">But only property identifiers are used to set properties on XAML markup elements, so setting **x:Uid** to "Farewell" on this TextBlock would have no effect.</span></span> `Resources.resw` <span data-ttu-id="e691a-145">„Resources.resw” *enthält zwar* den Zeichenfolgenressourcen-Bezeichner „Farewell”, aber keine zugehörigen Eigenschaftsbezeichner.</span><span class="sxs-lookup"><span data-stu-id="e691a-145">*does* contain the string resource identifier "Farewell", but it contains no property identifiers for it.</span></span>

<span data-ttu-id="e691a-146">Sollten Sie einem XAML-Element einen Zeichenfolgeressourcen-Bezeichner zuordnen, müssen Sie sicherstellen, dass *alle* Eigenschaftsbezeichner für diesen Bezeichner für das XAML-Element geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="e691a-146">When assigning a string resource identifier to a XAML element, be certain that *all* the property identifiers for that identifier are appropriate for the XAML element.</span></span> <span data-ttu-id="e691a-147">Wenn Sie beispielsweise `x:Uid="Greeting"` in einem **TextBlock**-Element verwenden, wird „Greeting.Text” korrekt zugeordnet, da der Typ **TextBlock** über eine Text-Eigenschaft verfügt.</span><span class="sxs-lookup"><span data-stu-id="e691a-147">For example, if you set `x:Uid="Greeting"` on a **TextBlock** then "Greeting.Text" will resolve because the **TextBlock** type has a Text property.</span></span> <span data-ttu-id="e691a-148">Wenn Sie `x:Uid="Greeting"` aber in einem **Button**-Element verwenden, wird „Greeting.Text” einen Laufzeitfehler verursachen, da der Typ **Button** nicht über eine Texteigenschaft verfügt.</span><span class="sxs-lookup"><span data-stu-id="e691a-148">But if you set `x:Uid="Greeting"` on a **Button** then "Greeting.Text" will cause a run-time error because the **Button** type does not have a Text property.</span></span> <span data-ttu-id="e691a-149">Eine Lösung für diesen Fall ist, einen Eigenschaftsbezeichner mit dem Namen "ButtonGreeting.Content" zu erstellen und `x:Uid="ButtonGreeting"` im **Button**-Element zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e691a-149">One solution for that case is to author a property identifier named "ButtonGreeting.Content", and set `x:Uid="ButtonGreeting"` on the **Button**.</span></span>

<span data-ttu-id="e691a-150">Statt **Width** mithilfe einer Ressourcendatei festzulegen, können Sie veranlassen, dass sich Steuerelemente in ihrer Größe dynamisch an Inhalte anpassen.</span><span class="sxs-lookup"><span data-stu-id="e691a-150">Instead of setting **Width** from a Resources File, you'll probably want to allow controls to dynamically size to content.</span></span>

<span data-ttu-id="e691a-151">**Hinweis:** Für [angefügte Eigenschaften](../xaml-platform/attached-properties-overview.md) ist eine spezielle Syntax in der Spalte „Name” einer resw-Datei erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e691a-151">**Note** For [attached properties](../xaml-platform/attached-properties-overview.md), you need a special syntax in the Name column of a .resw file.</span></span> <span data-ttu-id="e691a-152">Um beispielsweise einen Wert für die angefügte Eigenschaft [AutomationProperties.Name](/uwp/api/windows.ui.xaml.automation.automationproperties?branch=live#Windows_UI_Xaml_Automation_AutomationProperties_NameProperty) des Bezeichners „Greeting” festzulegen, müssen Sie Folgendes in der Spalte „Name” eingeben:</span><span class="sxs-lookup"><span data-stu-id="e691a-152">For example, to set a value for the [AutomationProperties.Name](/uwp/api/windows.ui.xaml.automation.automationproperties?branch=live#Windows_UI_Xaml_Automation_AutomationProperties_NameProperty) attached property for the "Greeting" identifier, this is what you would enter in the Name column.</span></span>

```
Greeting.[using:Windows.UI.Xaml.Automation]AutomationProperties.Name
```

## <a name="refer-to-a-string-resource-identifier-from-code"></a><span data-ttu-id="e691a-153">Referenzieren eines Bezeichners für Zeichenfolgenressourcen im Code</span><span class="sxs-lookup"><span data-stu-id="e691a-153">Refer to a string resource identifier from code</span></span>

<span data-ttu-id="e691a-154">Sie können eine Zeichenfolgenressource explizit durch Angabe eines einfachen Zeichenfolgenressourcen-Bezeichners laden:</span><span class="sxs-lookup"><span data-stu-id="e691a-154">You can explicitly load a string resource based on a simple string resource identifier.</span></span>

**<span data-ttu-id="e691a-155">C#</span><span class="sxs-lookup"><span data-stu-id="e691a-155">C#</span></span>**
```csharp
var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView();
this.myXAMLTextBlockElement.Text = resourceLoader.GetString("Farewell");
```

**<span data-ttu-id="e691a-156">C++</span><span class="sxs-lookup"><span data-stu-id="e691a-156">C++</span></span>**
```cpp
auto resourceLoader = Windows::ApplicationModel::Resources::ResourceLoader::GetForCurrentView();
this->myXAMLTextBlockElement->Text = resourceLoader->GetString("Farewell");
```

<span data-ttu-id="e691a-157">Sie können diesen Code in einer Klassenbibliothek (Universal Windows) oder in einem [Windows Runtime Library (Universal Windows)](../winrt-components/index.md)-Projekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="e691a-157">You can use this same code from within a Class Library (Universal Windows) or a [Windows Runtime Library (Universal Windows)](../winrt-components/index.md) project.</span></span> <span data-ttu-id="e691a-158">Zur Laufzeit werden die Ressourcen der App geladen, die die Bibliothek hostet.</span><span class="sxs-lookup"><span data-stu-id="e691a-158">At runtime, the resources of the app that's hosting the library are loaded.</span></span> <span data-ttu-id="e691a-159">Wir empfehlen, dass eine Bibliothek Ressourcen aus der App lädt, die sie hostet, da die App wahrscheinlich einen höheren Lokalisierungsgrad aufweist.</span><span class="sxs-lookup"><span data-stu-id="e691a-159">We recommend that a library loads resources from the app that hosts it, since the app is likely to have a greater degree of localization.</span></span> <span data-ttu-id="e691a-160">Wenn eine Bibliothek Ressourcen bereitstellen muss, sollte sie es der App, die sie hostet, ermöglichen, diese Ressourcen als Eingabe zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="e691a-160">If a library does need to provide resources then it should give its hosting app the option to replace those resources as an input.</span></span>

<span data-ttu-id="e691a-161">**Hinweis:** Sie können den Wert auf diese Weise nur für einen einfachen Zeichenfolgenressourcen-Bezeichner laden, nicht jedoch für einen Eigenschaftsbezeichner.</span><span class="sxs-lookup"><span data-stu-id="e691a-161">**Note** You can only load the value for a simple string resource identifier this way, not for a property identifier.</span></span> <span data-ttu-id="e691a-162">So können Sie mit solchem Code zwar den Wert für „Farewell” laden, nicht aber den für „Greeting.Text”.</span><span class="sxs-lookup"><span data-stu-id="e691a-162">So we can load the value for "Farewell" using code like this, but we cannot do so for "Greeting.Text".</span></span> <span data-ttu-id="e691a-163">Wenn Sie es versuchen, wird eine leere Zeichenfolge zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="e691a-163">Trying to do so will return an empty string.</span></span>

## <a name="refer-to-a-string-resource-identifier-from-your-app-package-manifest"></a><span data-ttu-id="e691a-164">Verweisen auf einen Ressourcenbezeichner aus dem App-Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="e691a-164">Refer to a string resource identifier from your app package manifest</span></span>

1. <span data-ttu-id="e691a-165">Öffnen Sie das App-Paketmanifest (die Datei `Package.appxmanifest`). Darin ist der Anzeigenamen Ihrer App standardmäßig als Zeichenfolgenliteral angegeben.</span><span class="sxs-lookup"><span data-stu-id="e691a-165">Open your app package manifest (the `Package.appxmanifest` file), in which by default your app's Display name is expressed as a string literal.</span></span>

   ![Ressource hinzufügen, Englisch](images/display-name-before.png)

2. <span data-ttu-id="e691a-167">Um eine lokalisierbare Version dieser Zeichenfolge zu erstellen, öffnen Sie `Resources.resw` und fügen eine neue Zeichenfolgenressource mit dem Namen „AppDisplayName” und dem Wert „Adventure Works Cycles” hinzu.</span><span class="sxs-lookup"><span data-stu-id="e691a-167">To make a localizable version of this string, open `Resources.resw` and add a new string resource with the name "AppDisplayName" and the value "Adventure Works Cycles".</span></span>

3. <span data-ttu-id="e691a-168">Ersetzen Sie das Zeichenfolgenliteral für den Anzeigennamen durch einen Verweis auf den Zeichenfolgenressourcen-Bezeichner, den Sie gerade erstellt haben („AppDisplayName”).</span><span class="sxs-lookup"><span data-stu-id="e691a-168">Replace the Display name string literal with a reference to the string resource identifier that you just created ("AppDisplayName").</span></span> <span data-ttu-id="e691a-169">Verwenden Sie dazu das URI (Uniform Resource Identifier)-Schema `ms-resource`.</span><span class="sxs-lookup"><span data-stu-id="e691a-169">You use the `ms-resource` URI (Uniform Resource Identifier) scheme to do this.</span></span>

   ![Ressource hinzufügen, Englisch](images/display-name-after.png)

4. <span data-ttu-id="e691a-171">Wiederholen Sie den Vorgang für alle Zeichenfolgen im Manifest, die Sie lokalisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="e691a-171">Repeat this process for each string in your manifest that you want to localize.</span></span> <span data-ttu-id="e691a-172">Beispielsweise für den Kurznamen Ihrer App (den Sie so konfigurieren können, dass er im Startmenü auf der App-Kachel angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="e691a-172">For example, your app's Short name (which you can configure to appear on your app's tile on Start).</span></span> <span data-ttu-id="e691a-173">Eine Liste aller Elemente im App-Paketmanifest, die Sie lokalisieren können, finden Sie unter [Lokalisierbare Manifestelemente](/uwp/schemas/appxpackage/uapmanifestschema/localizable-manifest-items-win10?branch=live).</span><span class="sxs-lookup"><span data-stu-id="e691a-173">For a list of all items in the app package manifest that you can localize, see [Localizable manifest items](/uwp/schemas/appxpackage/uapmanifestschema/localizable-manifest-items-win10?branch=live).</span></span>

## <a name="localize-the-string-resources"></a><span data-ttu-id="e691a-174">Lokalisieren der Zeichenfolgenressourcen</span><span class="sxs-lookup"><span data-stu-id="e691a-174">Localize the string resources</span></span>

1. <span data-ttu-id="e691a-175">Erstellen Sie eine Kopie der Ressourcendatei (.resw) für eine andere Sprache.</span><span class="sxs-lookup"><span data-stu-id="e691a-175">Make a copy of your Resources File (.resw) for another language.</span></span>
    1. <span data-ttu-id="e691a-176">Erstellen Sie unter „Strings” einen neuen Unterordner, und nennen Sie ihn „de-DE” für Deutsch (Deutschland).</span><span class="sxs-lookup"><span data-stu-id="e691a-176">Under "Strings", create a new sub-folder and name it "de-DE" for Deutsch (Deutschland).</span></span>
   <br><span data-ttu-id="e691a-177">**Hinweis:** Für den Namen des Ordners können Sie jeden [BCP-47-Sprachtag](http://go.microsoft.com/fwlink/p/?linkid=227302) verwenden.</span><span class="sxs-lookup"><span data-stu-id="e691a-177">**Note** For the folder name, you can use any [BCP-47 language tag](http://go.microsoft.com/fwlink/p/?linkid=227302).</span></span> <span data-ttu-id="e691a-178">Details zum Sprachqualifizierer und eine Liste häufiger Sprachtags finden Sie unter [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und anderen](tailor-resources-lang-scale-contrast.md).</span><span class="sxs-lookup"><span data-stu-id="e691a-178">See [Tailor your resources for language, scale, and other qualifiers](tailor-resources-lang-scale-contrast.md) for details on the language qualifier and a list of common language tags.</span></span>
   2. <span data-ttu-id="e691a-179">Erstellen Sie im Ordner `Strings/de-DE` eine Kopie von `Strings/en-US/Resources.resw`.</span><span class="sxs-lookup"><span data-stu-id="e691a-179">Make a copy of `Strings/en-US/Resources.resw` in the `Strings/de-DE` folder.</span></span>
2. <span data-ttu-id="e691a-180">Übersetzen Sie die Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="e691a-180">Translate the strings.</span></span>
    1. <span data-ttu-id="e691a-181">Öffnen Sie `Strings/de-DE/Resources.resw`, und übersetzen Sie die Werte in der Spalte „Value”.</span><span class="sxs-lookup"><span data-stu-id="e691a-181">Open `Strings/de-DE/Resources.resw` and translate the values in the Value column.</span></span> <span data-ttu-id="e691a-182">Sie müssen die Kommentare nicht übersetzen.</span><span class="sxs-lookup"><span data-stu-id="e691a-182">You don't need to translate the comments.</span></span>

    `Strings/de-DE/Resources.resw`

    ![Ressource hinzufügen, Deutsch](images/addresource-de-de.png)

<span data-ttu-id="e691a-184">Bei Bedarf wiederholen Sie die Schritte 1 und 2 für eine weitere Sprache.</span><span class="sxs-lookup"><span data-stu-id="e691a-184">If you like, you can repeat steps 1 and 2 for a further language.</span></span>

`Strings/fr-FR/Resources.resw`

![Ressource hinzufügen, Französisch](images/addresource-fr-fr.png)

## <a name="test-your-app"></a><span data-ttu-id="e691a-186">Testen der App</span><span class="sxs-lookup"><span data-stu-id="e691a-186">Test your app</span></span>

<span data-ttu-id="e691a-187">Testen Sie die App hinsichtlich der Standardanzeigesprache.</span><span class="sxs-lookup"><span data-stu-id="e691a-187">Test the app for your default display language.</span></span> <span data-ttu-id="e691a-188">Sie können dann die Anzeigesprache in **Einstellungen** > **Zeit & Sprache** > **Region & Sprache** (oder **Sprache**) ändern und die App erneut testen.</span><span class="sxs-lookup"><span data-stu-id="e691a-188">You can then change the display language in **Settings** > **Time & language** > **Region & language** (or **Language**) and re-test your app.</span></span> <span data-ttu-id="e691a-189">Beachten Sie Zeichenfolgen in der Benutzeroberfläche und auch in der Shell (z.B. den Anzeigenamen in der Titelleiste und den Kurznamen für Ihre Kacheln).</span><span class="sxs-lookup"><span data-stu-id="e691a-189">Look at strings in your UI and also in the shell (for example, your title bar&mdash;which is your Display name&mdash;and the Short name on your tiles).</span></span>

<span data-ttu-id="e691a-190">**Hinweis:** Wenn ein Ordnername gefunden wird, der mit der Einstellung für die Anzeigesprache übereinstimmt, wird die Ressourcendatei in diesem Ordner geladen.</span><span class="sxs-lookup"><span data-stu-id="e691a-190">**Note** If a folder name can be found that matches the display language setting, then the Resources File inside that folder is loaded.</span></span> <span data-ttu-id="e691a-191">Andernfalls erfolgt ein Fallback bis auf die Ressourcen für die standardmäßige Sprache Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="e691a-191">Otherwise, fallback takes place, ending with the resources for your app's default language.</span></span>

## <a name="factoring-strings-into-multiple-resources-files"></a><span data-ttu-id="e691a-192">Verteilen von Zeichenfolgen in mehrere Ressourcendateien</span><span class="sxs-lookup"><span data-stu-id="e691a-192">Factoring strings into multiple Resources Files</span></span>

<span data-ttu-id="e691a-193">Sie können alle Zeichenfolgen in einer einzelnen Ressourcendatei (resw) zusammenfassen oder sie auf mehrere Ressourcendateien verteilen.</span><span class="sxs-lookup"><span data-stu-id="e691a-193">You can keep all of your strings in a single Resources File (resw), or you can factor them across multiple Resources Files.</span></span> <span data-ttu-id="e691a-194">Beispielsweise können in einer Ressourcendatei Fehlermeldungen ablegen, die Zeichenfolgen für das App-Paketmanifest in einer anderen, und die Zeichenfolgen für die Benutzeroberfläche in einer dritten Ressourcendatei.</span><span class="sxs-lookup"><span data-stu-id="e691a-194">For example, you might want to keep your error messages in one Resources File, your app package manifest strings in another, and your UI strings in a third.</span></span> <span data-ttu-id="e691a-195">In diesem Fall würde die Ordnerstruktur wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="e691a-195">This is what your folder structure would look like in that case.</span></span>

![Ressource hinzufügen, Englisch](images/manifest-resources.png)

<span data-ttu-id="e691a-197">Um den Verweis auf den Bezeichner einer Zeichenfolgenressource auf eine bestimmte Datei zu beziehen, setzen Sie einfach `/<resources-file-name>/` vor den Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="e691a-197">To scope a string resource identifier reference to a particular file, you just add `/<resources-file-name>/` before the identifier.</span></span> <span data-ttu-id="e691a-198">Im folgenden Markupbeispiel wird davon ausgegangen, dass `ErrorMessages.resw` eine Ressource mit dem Namen „PasswordTooWeak.Text” enthält, deren Wert einen Fehler beschreibt.</span><span class="sxs-lookup"><span data-stu-id="e691a-198">The markup example below assumes that `ErrorMessages.resw` contains a resource whose name is "PasswordTooWeak.Text" and whose value describes the error.</span></span>

**<span data-ttu-id="e691a-199">XAML</span><span class="sxs-lookup"><span data-stu-id="e691a-199">XAML</span></span>**
```xml
<TextBlock x:Uid="/ErrorMessages/PasswordTooWeak"/>
```

<span data-ttu-id="e691a-200">Im folgenden Codebeispiel wird davon ausgegangen, dass `ErrorMessages.resw` eine Ressource mit dem Namen „MismatchedPasswords” enthält, deren Wert einen Fehler beschreibt.</span><span class="sxs-lookup"><span data-stu-id="e691a-200">The code example below assumes that `ErrorMessages.resw` contains a resource whose name is "MismatchedPasswords" and whose value describes the error.</span></span>

**<span data-ttu-id="e691a-201">C#</span><span class="sxs-lookup"><span data-stu-id="e691a-201">C#</span></span>**
```csharp
var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView("ManifestResources");
this.myXAMLTextBlockElement.Text = resourceLoader.GetString("/ErrorMessages/MismatchedPasswords");
```

**<span data-ttu-id="e691a-202">C++</span><span class="sxs-lookup"><span data-stu-id="e691a-202">C++</span></span>**
```cpp
auto resourceLoader = Windows::ApplicationModel::Resources::ResourceLoader::GetForCurrentView("ManifestResources");
this->myXAMLTextBlockElement->Text = resourceLoader->GetString("/ErrorMessages/MismatchedPasswords");
```

<span data-ttu-id="e691a-203">Würden Sie die Ressource „AppDisplayName” aus `Resources.resw` in `ManifestResources.resw` verschieben, müssten Sie in Ihrem App-Paketmanifest `ms-resource:AppDisplayName` in `ms-resource:/ManifestResources/AppDisplayName` ändern.</span><span class="sxs-lookup"><span data-stu-id="e691a-203">If you were to move your "AppDisplayName" resource out of `Resources.resw` and into `ManifestResources.resw` then in your app package manifest you would change `ms-resource:AppDisplayName` to `ms-resource:/ManifestResources/AppDisplayName`.</span></span>

<span data-ttu-id="e691a-204">Für *andere Ressourcendateien* als `Resources.resw` müssen nur `/<resources-file-name>/` vor den Bezeichner für die Zeichenfolgenressource setzten.</span><span class="sxs-lookup"><span data-stu-id="e691a-204">You only need to add `/<resources-file-name>/` before the string resource identifier for Resources Files *other than* `Resources.resw`.</span></span> <span data-ttu-id="e691a-205">Der Grund ist, dass „Resources.resw” der Standarddateiname ist, der verwendet wird, wenn Sie keinen Dateinamen angeben (wie in früheren Beispielen in diesem Thema).</span><span class="sxs-lookup"><span data-stu-id="e691a-205">That's because "Resources.resw" is the default file name, so that's what's assumed if you omit a file name (as we did in the earlier examples in this topic).</span></span>

## <a name="load-a-string-for-a-specific-language-or-other-context"></a><span data-ttu-id="e691a-206">Laden einer Zeichenfolge für eine bestimmte Sprache oder einen anderen Kontext</span><span class="sxs-lookup"><span data-stu-id="e691a-206">Load a string for a specific language or other context</span></span>

<span data-ttu-id="e691a-207">Der standardmäßige [**ResourceContext**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live) (abgerufen über [**ResourceContext.GetForCurrentView**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_GetForCurrentView)) enthält einen Qualifiziererwert für jeden Qualifizierernamen, der den standardmäßigen Laufzeitkontext darstellt (also die Einstellungen für den aktuellen Benutzer und Computer).</span><span class="sxs-lookup"><span data-stu-id="e691a-207">The default [**ResourceContext**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live) (obtained from [**ResourceContext.GetForCurrentView**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_GetForCurrentView)) contains a qualifier value for each qualifier name, representing the default runtime context (in other words, the settings for the current user and machine).</span></span> <span data-ttu-id="e691a-208">Ressourcendateien (.resw) werden anhand der Qualifizierer in ihren Namen mit den Qualifiziererwerten in diesem Laufzeitkontext abgeglichen.</span><span class="sxs-lookup"><span data-stu-id="e691a-208">Resources Files (.resw) are matched&mdash;based on the qualifiers in their names&mdash;against the qualifier values in that runtime context.</span></span>

<span data-ttu-id="e691a-209">In einigen Fällen wünschen Sie vielleicht, dass Ihre App die Systemeinstellungen überschreiben und Sprache, Skalierung oder andere Qualifiziererwerte explizit angeben kann, wenn sie nach einer passenden Ressourcendatei sucht, um sie zu laden.</span><span class="sxs-lookup"><span data-stu-id="e691a-209">But there might be times when you want your app to override the system settings and be explicit about the language, scale, or other qualifier value to use when looking for a matching Resources File to load.</span></span> <span data-ttu-id="e691a-210">So könnten Sie es Ihren Benutzern beispielsweise ermöglichen, eine alternative Sprache für QuickInfos oder Fehlermeldungen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="e691a-210">For example, you might want your users to be able to select an alternative language for tooltips or error messages.</span></span>

<span data-ttu-id="e691a-211">Das ist möglich, indem Sie einen neuen **ResourceContext** erstellen (statt den standardmäßigen Kontext zu verwenden), dessen Werte überschreiben und dann dieses Kontextobjekt bei der Suche nach Zeichenfolgen verwenden.</span><span class="sxs-lookup"><span data-stu-id="e691a-211">You can do that by constructing a new **ResourceContext** (instead of using the default one), overriding its values, and then using that context object in your string lookups.</span></span>

**<span data-ttu-id="e691a-212">C#</span><span class="sxs-lookup"><span data-stu-id="e691a-212">C#</span></span>**
```csharp
var resourceContext = new Windows.ApplicationModel.Resources.Core.ResourceContext(); // not using ResourceContext.GetForCurrentView
resourceContext.QualifierValues["Language"] = "de-DE";
var resourceMap = Windows.ApplicationModel.Resources.Core.ResourceManager.Current.MainResourceMap.GetSubtree("Resources");
this.myXAMLTextBlockElement.Text = resourceMap.GetValue("Farewell", resourceContext).ValueAsString;
```

<span data-ttu-id="e691a-213">Wie **QualifierValues** im obigen Codebeispiel kann jeder Qualifizierer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e691a-213">Using **QualifierValues** as in the code example above works for any qualifier.</span></span> <span data-ttu-id="e691a-214">Für den Sonderfall Language können Sie alternativ wie folgt verfahren.</span><span class="sxs-lookup"><span data-stu-id="e691a-214">For the special case of Language, you can alternatively do this instead.</span></span>

**<span data-ttu-id="e691a-215">C#</span><span class="sxs-lookup"><span data-stu-id="e691a-215">C#</span></span>**
```csharp
resourceContext.Languages = new string[] { "de-DE" };
```

<span data-ttu-id="e691a-216">Um den gleichen Effekt auf einer globalen Ebene zu erzielen, *könnten* Sie die Qualifiziererwerte im standardmäßigen **ResourceContext** überschreiben.</span><span class="sxs-lookup"><span data-stu-id="e691a-216">For the same effect at a global level, you *can* override the qualifier values in the default **ResourceContext**.</span></span> <span data-ttu-id="e691a-217">Wir empfehlen, stattdessen [**ResourceContext.SetGlobalQualifierValue**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_) aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="e691a-217">But instead we advise you to call [**ResourceContext.SetGlobalQualifierValue**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_).</span></span> <span data-ttu-id="e691a-218">Wenn Sie Werte einmal mit einem Aufruf von **SetGlobalQualifierValue** festlegen, werden sie bei jedem Suchvorgang mit dem standardmäßigen **ResourceContext** auf diesen angewendet.</span><span class="sxs-lookup"><span data-stu-id="e691a-218">You set values one time with a call to **SetGlobalQualifierValue** and then those values are in effect on the default **ResourceContext** each time you use it for lookups.</span></span>

**<span data-ttu-id="e691a-219">C#</span><span class="sxs-lookup"><span data-stu-id="e691a-219">C#</span></span>**
```csharp
Windows.ApplicationModel.Resources.Core.ResourceContext.SetGlobalQualifierValue("Language", "de-DE");
var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView();
this.myXAMLTextBlockElement.Text = resourceLoader.GetString("Farewell");
```

<span data-ttu-id="e691a-220">Einige Qualifizierer besitzen einen Systemdatenanbieter.</span><span class="sxs-lookup"><span data-stu-id="e691a-220">Some qualifiers have a system data provider.</span></span> <span data-ttu-id="e691a-221">Statt **SetGlobalQualifierValue** aufzurufen, können Sie dann den Anbieter über seine eigene API anpassen.</span><span class="sxs-lookup"><span data-stu-id="e691a-221">So, instead of calling **SetGlobalQualifierValue** you could instead adjust the provider through its own API.</span></span> <span data-ttu-id="e691a-222">Der folgende Code zeigt an einem Beispiel, wie [**PrimaryLanguageOverride**](/uwp/api/Windows.Globalization.ApplicationLanguages?branch=live#Windows_Globalization_ApplicationLanguages_PrimaryLanguageOverride) festzulegen ist.</span><span class="sxs-lookup"><span data-stu-id="e691a-222">For example, this code shows how to set [**PrimaryLanguageOverride**](/uwp/api/Windows.Globalization.ApplicationLanguages?branch=live#Windows_Globalization_ApplicationLanguages_PrimaryLanguageOverride).</span></span>

**<span data-ttu-id="e691a-223">C#</span><span class="sxs-lookup"><span data-stu-id="e691a-223">C#</span></span>**
```csharp
Windows.Globalization.ApplicationLanguages.PrimaryLanguageOverride = "de-DE";
```

## <a name="updating-strings-in-response-to-qualifier-value-change-events"></a><span data-ttu-id="e691a-224">Aktualisieren von Zeichenfolgen als Reaktion auf Änderungen von Qualifiziererwerten</span><span class="sxs-lookup"><span data-stu-id="e691a-224">Updating strings in response to qualifier value change events</span></span>

<span data-ttu-id="e691a-225">Eine aktive App kann auf Änderungen der Systemeinstellungen reagieren, wenn sich diese Änderungen auf Qualifiziererwerte im standardmäßigen **ResourceContext** auswirken.</span><span class="sxs-lookup"><span data-stu-id="e691a-225">Your running app can respond to changes in system settings that affect the qualifier values in the default **ResourceContext**.</span></span> <span data-ttu-id="e691a-226">Jede dieser Systemeinstellungen löst das Ereignis [**MapChanged**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_?branch=live#Windows_Foundation_Collections_IObservableMap_2_MapChanged) für [**ResourceContext.QualifierValues**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues) aus.</span><span class="sxs-lookup"><span data-stu-id="e691a-226">Any of these system settings invokes the [**MapChanged**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_?branch=live#Windows_Foundation_Collections_IObservableMap_2_MapChanged) event on [**ResourceContext.QualifierValues**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues).</span></span>

<span data-ttu-id="e691a-227">Als Reaktion auf dieses Ereignis können Sie die Zeichenfolgen aus dem standardmäßigen **ResourceContext** laden.</span><span class="sxs-lookup"><span data-stu-id="e691a-227">In response to this event, you can reload your strings from the default **ResourceContext**.</span></span>

**<span data-ttu-id="e691a-228">C#</span><span class="sxs-lookup"><span data-stu-id="e691a-228">C#</span></span>**
```csharp
public MainPage()
{
    this.InitializeComponent();

    ...

    // Subscribe to the event that's raised when a qualifier value changes.
    var qualifierValues = Windows.ApplicationModel.Resources.Core.ResourceContext.GetForCurrentView().QualifierValues;
    qualifierValues.MapChanged += new Windows.Foundation.Collections.MapChangedEventHandler<string, string>(QualifierValues_MapChanged);
}

private async void QualifierValues_MapChanged(IObservableMap<string, string> sender, IMapChangedEventArgs<string> @event)
{
    var dispatcher = this.myXAMLTextBlockElement.Dispatcher;
    if (dispatcher.HasThreadAccess)
    {
        this.RefreshUIText();
    }
    else
    {
        await dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, () => this.RefreshUIText());
    }
}

private void RefreshUIText()
{
    var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView();
    this.myXAMLTextBlockElement.Text = resourceLoader.GetString("Farewell");
}
```

## <a name="loading-strings-from-a-class-library-or-a-windows-runtime-library"></a><span data-ttu-id="e691a-229">Laden von Zeichenfolgen aus einer Klassenbibliothek oder eine Windows-Runtime-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e691a-229">Loading strings from a Class Library or a Windows Runtime Library</span></span>

<span data-ttu-id="e691a-230">Die Zeichenfolgenressourcen einer referenzierten Klassenbibliothek (Universal Windows) oder [Windows-Runtime Library (Universal Windows)](../winrt-components/index.md) stehen in der Regel in einem Unterordner des Pakets. Dort werden sie während des Buildprozesses eingefügt.</span><span class="sxs-lookup"><span data-stu-id="e691a-230">The string resources of a referenced Class Library (Universal Windows) or [Windows Runtime Library (Universal Windows)](../winrt-components/index.md) are typically added into a subfolder of the package in which they're included during the build process.</span></span> <span data-ttu-id="e691a-231">Der Ressourcenbezeichner solche Zeichenfolgen besitzen in der Regel die Form *Bibliotheksname/Ressourcendateiname/Ressourcenbezeichner*.</span><span class="sxs-lookup"><span data-stu-id="e691a-231">The resource identifier of such a string usually takes the form *LibraryName/ResourcesFileName/ResourceIdentifier*.</span></span>

<span data-ttu-id="e691a-232">Eine Bibliothek kann einen ResourceLoader für ihre eigenen Ressourcen abrufen.</span><span class="sxs-lookup"><span data-stu-id="e691a-232">A library can get a ResourceLoader for its own resources.</span></span> <span data-ttu-id="e691a-233">Der folgende Code zeigt beispielsweise, wie eine Bibliothek oder eine App durch einen entsprechenden Verweis einen ResourceLoader für die Zeichenfolgenressourcen der Bibliothek abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="e691a-233">For example, the following code illustrates how either a library or an app that references it can can get a ResourceLoader for the library's string resources.</span></span>

**<span data-ttu-id="e691a-234">C#</span><span class="sxs-lookup"><span data-stu-id="e691a-234">C#</span></span>**
```csharp
var resourceLoader = new Windows.ApplicationModel.Resources.ResourceLoader("ContosoControl/Resources");
resourceLoader.GetString("string1");
```

## <a name="loading-strings-from-other-packages"></a><span data-ttu-id="e691a-235">Laden von Zeichenfolgen aus anderen Paketen</span><span class="sxs-lookup"><span data-stu-id="e691a-235">Loading strings from other packages</span></span>

<span data-ttu-id="e691a-236">Die Ressourcen für ein App-Paket werden über die oberste Ebene der [ResourceMap](/uwp/api/windows.applicationmodel.resources.core.resourcemap?branch=live) des Pakets verwaltet und erreicht, auf die über den aktuellen [ResourceManager](/uwp/api/windows.applicationmodel.resources.core.resourcemanager?branch=live) zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="e691a-236">The resources for an app package are managed and accessed through the package's own top-level [ResourceMap](/uwp/api/windows.applicationmodel.resources.core.resourcemap?branch=live) that's accessible from the current [ResourceManager](/uwp/api/windows.applicationmodel.resources.core.resourcemanager?branch=live).</span></span> <span data-ttu-id="e691a-237">In jedem Paket können Komponenten eigene ResourceMap-Unterstrukturen besitzen, auf die Sie über [ResourceMap.GetSubtree](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceMap#Windows_ApplicationModel_Resources_Core_ResourceMap_GetSubtree_System_String_) zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="e691a-237">Within each package, various components can have their own ResourceMap subtrees, which you can access via [ResourceMap.GetSubtree](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceMap#Windows_ApplicationModel_Resources_Core_ResourceMap_GetSubtree_System_String_).</span></span>

<span data-ttu-id="e691a-238">Ein Frameworkpaket kann auf seine eigenen Ressourcen über einen absolute Ressourcenbezeichner-URI zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e691a-238">A framework package can access its own resources with an absolute resource identifier URI.</span></span> <span data-ttu-id="e691a-239">Weitere Informationen finden Sie unter [URI-Schemas](uri-schemes.md).</span><span class="sxs-lookup"><span data-stu-id="e691a-239">Also see [URI schemes](uri-schemes.md).</span></span>

## <a name="important-apis"></a><span data-ttu-id="e691a-240">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="e691a-240">Important APIs</span></span>

* [<span data-ttu-id="e691a-241">ApplicationModel.Resources.ResourceLoader</span><span class="sxs-lookup"><span data-stu-id="e691a-241">ApplicationModel.Resources.ResourceLoader</span></span>](https://msdn.microsoft.com/library/windows/apps/br206014)

## <a name="related-topics"></a><span data-ttu-id="e691a-242">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e691a-242">Related topics</span></span>

* [<span data-ttu-id="e691a-243">Portieren von XAML und UI</span><span class="sxs-lookup"><span data-stu-id="e691a-243">Porting XAML and UI</span></span>](../porting/wpsl-to-uwp-porting-xaml-and-ui.md#localization-and-globalization)
* [<span data-ttu-id="e691a-244">x:Uid-Direktive</span><span class="sxs-lookup"><span data-stu-id="e691a-244">x:Uid directive</span></span>](../xaml-platform/x-uid-directive.md)
* [<span data-ttu-id="e691a-245">Angefügte Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e691a-245">attached properties</span></span>](../xaml-platform/attached-properties-overview.md)
* [<span data-ttu-id="e691a-246">Lokalisierbare Manifestelemente</span><span class="sxs-lookup"><span data-stu-id="e691a-246">Localizable manifest items</span></span>](/uwp/schemas/appxpackage/uapmanifestschema/localizable-manifest-items-win10?branch=live)
* [<span data-ttu-id="e691a-247">BCP-47-Sprachtag</span><span class="sxs-lookup"><span data-stu-id="e691a-247">BCP-47 language tag</span></span>](http://go.microsoft.com/fwlink/p/?linkid=227302)
* [<span data-ttu-id="e691a-248">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und anderen</span><span class="sxs-lookup"><span data-stu-id="e691a-248">Tailor your resources for language, scale, and other qualifiers</span></span>](tailor-resources-lang-scale-contrast.md)
* [<span data-ttu-id="e691a-249">Laden von Zeichenfolgenressourcen</span><span class="sxs-lookup"><span data-stu-id="e691a-249">How to load string resources</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh965323)