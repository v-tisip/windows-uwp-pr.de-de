---
author: jwmsft
title: Bedingte XAML
description: Verwenden neuer APIs in XAML-Markup bei gleichzeitiger Gewährleistung der Kompatibilität mit früheren Versionen
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 46954968f11f000025ee352676d3f0d17ecb9621
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7147926"
---
# <a name="conditional-xaml"></a><span data-ttu-id="bdb35-104">Bedingte XAML</span><span class="sxs-lookup"><span data-stu-id="bdb35-104">Conditional XAML</span></span>

<span data-ttu-id="bdb35-105">*Bedingte XAML* bietet eine Möglichkeit, die Methode [ApiInformation.IsApiContractPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent) in XAML-Markup zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bdb35-105">*Conditional XAML* provides a way to use the [ApiInformation.IsApiContractPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent) method in XAML markup.</span></span> <span data-ttu-id="bdb35-106">Sie sind damit in der Lage, im Markup nur dann Eigenschaften festzulegen und Objekte zu initialisieren, wenn die entsprechende API vorhanden ist, ohne Code-Behind zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bdb35-106">This lets you set properties and instantiate objects in markup based on the presence of an API without needing to use code behind.</span></span> <span data-ttu-id="bdb35-107">Elemente oder Attribute werden selektiv analysiert, um zu bestimmen, ob sie zur Laufzeit zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-107">It selectively parses elements or attributes to determine whether they will be available at runtime.</span></span> <span data-ttu-id="bdb35-108">Bedingte Anweisungen werden zur Laufzeit ausgewertet, und Elemente, die mit einem bedingten XAML-Tag gekennzeichnet sind, werden analysiert, wenn ihre Auswertung **true** ergibt. Andernfalls werden sie ignoriert.</span><span class="sxs-lookup"><span data-stu-id="bdb35-108">Conditional statements are evaluated at runtime, and elements qualified with a conditional XAML tag are parsed if they evaluate to **true**; otherwise, they are ignored.</span></span>

<span data-ttu-id="bdb35-109">Bedingte XAML ist ab dem Creators-Update (Version 1703, Build 15063) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bdb35-109">Conditional XAML is available starting with the Creators Update (version 1703, build 15063).</span></span> <span data-ttu-id="bdb35-110">Die Verwendung bedingter XAML setzt voraus, dass Sie in Ihrem Visual Studio-Projekt Build 15063 (Creators Update) oder höher als Mindestversion und eine höhere Version als Zielversion festlegen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-110">To use conditional XAML, the Minimum Version of your Visual Studio project must be set to build 15063 (Creators Update) or later, and the Target Version be set to a later version than the Minimum.</span></span> <span data-ttu-id="bdb35-111">Weitere Informationen zum Konfigurieren Ihres Visual Studio-Projekts finden Sie unter [Versionsadaptive Apps](version-adaptive-apps.md).</span><span class="sxs-lookup"><span data-stu-id="bdb35-111">See [Version adaptive apps](version-adaptive-apps.md) for more info about configuring your Visual Studio project.</span></span>

> [!NOTE]
> <span data-ttu-id="bdb35-112">Sie müssen zum Erstellen einer versionsadaptiven App mit einer Mindestversion kleiner als Build 15063 [versionsadaptiven Code](version-adaptive-code.md) und nicht XAML verwenden.</span><span class="sxs-lookup"><span data-stu-id="bdb35-112">To create a version adaptive app with a Minimum Version less than build 15063, you must use [version adaptive code](version-adaptive-code.md), not XAML.</span></span>

<span data-ttu-id="bdb35-113">Wichtige Hintergrundinformationen über ApiInformation und API-Verträge finden Sie unter [Versionsadaptive Apps](version-adaptive-apps.md).</span><span class="sxs-lookup"><span data-stu-id="bdb35-113">For important background info about ApiInformation and API contracts, see [Version adaptive apps](version-adaptive-apps.md).</span></span>

## <a name="conditional-namespaces"></a><span data-ttu-id="bdb35-114">Bedingte Namespaces</span><span class="sxs-lookup"><span data-stu-id="bdb35-114">Conditional namespaces</span></span>

<span data-ttu-id="bdb35-115">Um eine bedingte Methode in XAML zu verwenden, müssen Sie zuerst einen bedingten [XAML-Namespace](../xaml-platform/xaml-namespaces-and-namespace-mapping.md) am Beginn der Seite deklarieren.</span><span class="sxs-lookup"><span data-stu-id="bdb35-115">To use a conditional method in XAML, you must first declare a conditional [XAML namespace](../xaml-platform/xaml-namespaces-and-namespace-mapping.md) at the top of your page.</span></span> <span data-ttu-id="bdb35-116">Hier ein Pseudocodebeispiel für einen bedingten Namespace:</span><span class="sxs-lookup"><span data-stu-id="bdb35-116">Here's a psuedo-code example of a conditional namespace:</span></span>

```xaml
xmlns:myNamespace="schema?conditionalMethod(parameter)"
```

<span data-ttu-id="bdb35-117">Ein bedingter Namespace besteht aus zwei Teilen, die durch das Zeichen '?' getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="bdb35-117">A conditional namespace can be broken down into two parts separated by the '?' delimiter.</span></span> 

- <span data-ttu-id="bdb35-118">Der Inhalt vor dem Trennzeichen gibt den Namespace oder das Schema an, in dem die referenzierte API enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="bdb35-118">The content preceding the delimiter indicates the namespace or schema that contains the API being referenced.</span></span> 
- <span data-ttu-id="bdb35-119">Der Inhalt nach dem Trennzeichen '?' stellt die bedingte Methode dar, die bestimmt, ob die Auswertung für den bedingten Namespace **true** oder **false** ergibt.</span><span class="sxs-lookup"><span data-stu-id="bdb35-119">The content after the '?' delimiter represents the conditional method that determines whether the conditional namespace evaluates to **true** or **false**.</span></span>

<span data-ttu-id="bdb35-120">In den meisten Fällen wird das Schema der standardmäßige XAML-Namespace sein:</span><span class="sxs-lookup"><span data-stu-id="bdb35-120">In most cases, the schema will be the default XAML namespace:</span></span>

```xaml
xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
```

<span data-ttu-id="bdb35-121">Bedingte XAML unterstützt die folgenden bedingten Methoden:</span><span class="sxs-lookup"><span data-stu-id="bdb35-121">Conditional XAML supports the following conditional methods:</span></span>

<span data-ttu-id="bdb35-122">Methode</span><span class="sxs-lookup"><span data-stu-id="bdb35-122">Method</span></span> | <span data-ttu-id="bdb35-123">Umkehrung</span><span class="sxs-lookup"><span data-stu-id="bdb35-123">Inverse</span></span>
------ | -------
<span data-ttu-id="bdb35-124">IsApiContractPresent(ContractName, VersionNumber)</span><span class="sxs-lookup"><span data-stu-id="bdb35-124">IsApiContractPresent(ContractName, VersionNumber)</span></span> | <span data-ttu-id="bdb35-125">IsApiContractNotPresent(ContractName, VersionNumber)</span><span class="sxs-lookup"><span data-stu-id="bdb35-125">IsApiContractNotPresent(ContractName, VersionNumber)</span></span>
<span data-ttu-id="bdb35-126">IsTypePresent(ControlType)</span><span class="sxs-lookup"><span data-stu-id="bdb35-126">IsTypePresent(ControlType)</span></span> | <span data-ttu-id="bdb35-127">IsTypeNotPresent(ControlType)</span><span class="sxs-lookup"><span data-stu-id="bdb35-127">IsTypeNotPresent(ControlType)</span></span>
<span data-ttu-id="bdb35-128">IsPropertyPresent(ControlType, PropertyName)</span><span class="sxs-lookup"><span data-stu-id="bdb35-128">IsPropertyPresent(ControlType, PropertyName)</span></span> | <span data-ttu-id="bdb35-129">IsPropertyNotPresent(ControlType, PropertyName)</span><span class="sxs-lookup"><span data-stu-id="bdb35-129">IsPropertyNotPresent(ControlType, PropertyName)</span></span>

<span data-ttu-id="bdb35-130">Wir besprechen diese Methoden weiter unten in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="bdb35-130">We discuss these methods further in later sections of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="bdb35-131">Es wird empfohlen, dass Sie IsApiContractPresent und IsApiContractNotPresent verwenden.</span><span class="sxs-lookup"><span data-stu-id="bdb35-131">We recommend you use IsApiContractPresent and IsApiContractNotPresent.</span></span> <span data-ttu-id="bdb35-132">Andere Bedingungen werden im Visual Studio-Entwurf nicht vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bdb35-132">Other conditionals are not fully supported in the Visual Studio design experience.</span></span>

## <a name="create-a-namespace-and-set-a-property"></a><span data-ttu-id="bdb35-133">Erstellen eines Namespace und Festlegen einer Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="bdb35-133">Create a namespace and set a property</span></span>

<span data-ttu-id="bdb35-134">In diesem Beispiel zeigen Sie „Hello, Conditional XAML” als Inhalt eines Textblocks an, wenn die App mit dem Fall Creators Update oder später läuft, und standardmäßig keinen Inhalt, wenn sie unter einer früheren Version läuft.</span><span class="sxs-lookup"><span data-stu-id="bdb35-134">In this example, you display, "Hello, Conditional XAML", as the content of a text block if the app runs on the Fall Creators Update or later, and default to no content if it's on a previous version.</span></span>

<span data-ttu-id="bdb35-135">Zuerst definieren Sie einen benutzerdefinierten Namespace mit dem Präfix „contract5Present” und verwenden den standardmäßigen XAML-Namespace (http://schemas.microsoft.com/winfx/2006/xaml/presentation) als das Schema, das die Eigenschaft [TextBlock.Text](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock.Text) enthält).</span><span class="sxs-lookup"><span data-stu-id="bdb35-135">First, define a custom namespace with the prefix 'contract5Present' and use the default XAML namespace (http://schemas.microsoft.com/winfx/2006/xaml/presentation) as the schema containing the [TextBlock.Text](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock.Text) property.</span></span> <span data-ttu-id="bdb35-136">Um daraus einen bedingten Namespace zu machen, fügen Sie das Trennzeichen '?'</span><span class="sxs-lookup"><span data-stu-id="bdb35-136">To make this a conditional namespace, add the ‘?’</span></span> <span data-ttu-id="bdb35-137">nach dem Schema ein.</span><span class="sxs-lookup"><span data-stu-id="bdb35-137">delimiter after the schema.</span></span>

<span data-ttu-id="bdb35-138">Dann definieren Sie eine Bedingung, die **true** auf Geräten zurückgibt, die das Fall Creators Update ausführen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-138">You then define a conditional that returns **true** on devices that are running the Fall Creators Update or later.</span></span> <span data-ttu-id="bdb35-139">Sie können die ApiInformation-Methode **IsApiContractPresent** verwenden, um zu prüfen, ob die 5. Version von UniversalApiContract vorliegt.</span><span class="sxs-lookup"><span data-stu-id="bdb35-139">You use the ApiInformation method **IsApiContractPresent** to check for the 5th version of the UniversalApiContract.</span></span> <span data-ttu-id="bdb35-140">Version 5 von UniversalApiContract wurde mit dem Fall Creators Update (SDK 16299) veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="bdb35-140">Version 5 of the UniversalApiContract was released with the Fall Creators Update (SDK 16299).</span></span>

```xaml
xmlns:contract5Present="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"
```

<span data-ttu-id="bdb35-141">Nachdem der Namespace definiert ist, stellen Sie das Namespacepräfix der Text-Eigenschaft Ihrer TextBox voran, um sie als Eigenschaft auszuzeichnen, die bedingt zur Laufzeit festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bdb35-141">After the namespace is defined, you prepend the namespace prefix to the Text property of your TextBox to qualify it as a property that should be set conditionally at runtime.</span></span>

```xaml
<TextBlock contract5Present:Text="Hello, Conditional XAML"/>
```

<span data-ttu-id="bdb35-142">Hier die gesamte XAML.</span><span class="sxs-lookup"><span data-stu-id="bdb35-142">Here's the complete XAML.</span></span>

```xaml
<Page
    x:Class="ConditionalTest.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:contract5Present="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <TextBlock contract5Present:Text="Hello, Conditional XAML"/>
    </Grid>
</Page>
```

<span data-ttu-id="bdb35-143">Wenn Sie dieses Beispiel mit Fall Creators Update ausführen, wird der Text „Hello, Conditional XAML” angezeigt; wenn Sie es mit Creators Update ausführen, wird kein Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bdb35-143">When you run this example on the Fall Creators Update, the text, "Hello, Conditional XAML" is shown; when you run it on the Creators Update, no text is shown.</span></span>

<span data-ttu-id="bdb35-144">Mit bedingter XAML können Sie die API-Prüfungen statt im Code in Ihrem Markup ausführen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-144">Conditional XAML lets you perform the API checks you can do in code in your markup instead.</span></span> <span data-ttu-id="bdb35-145">Hier der entsprechende Code für dieses Beispiel.</span><span class="sxs-lookup"><span data-stu-id="bdb35-145">Here's the equivalent code for this check.</span></span>

```csharp
if (ApiInformation.IsApiContractPresent("Windows.Foundation.UniversalApiContract", 5))
{
    textBlock.Text = "Hello, Conditional XAML";
}
```

<span data-ttu-id="bdb35-146">Beachten Sie: Obwohl die Methode IsApiContractPresent eine Zeichenfolge für den Parameter *contractName* erwartet, wird diese in der XAML-Namespace-Deklaration nicht in Anführungszeichen ("") gesetzt.</span><span class="sxs-lookup"><span data-stu-id="bdb35-146">Notice that even though the IsApiContractPresent method takes a string for the *contractName* parameter, you don't put it in quotes (" ") in the XAML namespace declaration.</span></span>

## <a name="use-ifelse-conditions"></a><span data-ttu-id="bdb35-147">Verwenden von if/else-Bedingungen</span><span class="sxs-lookup"><span data-stu-id="bdb35-147">Use if/else conditions</span></span>

<span data-ttu-id="bdb35-148">Im vorherigen Beispiel wird die Eigenschaft Text nur gesetzt, wenn die App mit Fall Creators Update läuft.</span><span class="sxs-lookup"><span data-stu-id="bdb35-148">In the previous example, the Text property is set only when the app runs on the Fall Creators Update.</span></span> <span data-ttu-id="bdb35-149">Wie ist aber vorzugehen, um einen alternativen Text anzuzeigen, wenn das Creators Update ausgeführt wird?</span><span class="sxs-lookup"><span data-stu-id="bdb35-149">But what if you want to show different text when it runs on the Creators Update?</span></span> <span data-ttu-id="bdb35-150">Sie können versuchen, die Text-Eigenschaft wie folgt ohne einen bedingten Qualifizierer festzulegen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-150">You could try to set the Text property without a conditional qualifier, like this.</span></span>

```xaml
<!-- DO NOT USE -->
<TextBlock Text="Hello, World" contract5Present:Text="Hello, Conditional XAML"/>
```

<span data-ttu-id="bdb35-151">Dies funktioniert, wenn sie mit Creators Update ausgeführt wird, aber wenn sie mit Fall Creators Update ausgeführt wird, erhalten Sie eine Fehlermeldung, dass die Text-Eigenschaft mehr als einmal gesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="bdb35-151">This will work when it runs on the Creators Update, but when it runs on the Fall Creators Update, you get an error saying that the Text property is set more than once.</span></span>

<span data-ttu-id="bdb35-152">Um unterschiedliche Texte festzulegen für den Fall, dass die App unter verschiedenen Versionen von Windows10 ausgeführt wird, benötigen Sie eine andere Bedingung.</span><span class="sxs-lookup"><span data-stu-id="bdb35-152">To set different text when the app runs on different versions of Windows 10, you need another condition.</span></span> <span data-ttu-id="bdb35-153">Bedingte XAML bietet eine Umkehrung jeder unterstützten ApiInformation-Methode, damit Sie wie folgt if/else-Szenarien erstellen können.</span><span class="sxs-lookup"><span data-stu-id="bdb35-153">Conditional XAML provides an inverse of each supported ApiInformation method to let you create if/else conditional scenarios like this.</span></span>

<span data-ttu-id="bdb35-154">Die Methode IsApiContractPresent liefert **true**, wenn das aktuelle Gerät die angegebene Vertrags- und Versionsnummer enthält.</span><span class="sxs-lookup"><span data-stu-id="bdb35-154">The IsApiContractPresent method returns **true** if the current device contains the specified contract and version number.</span></span> <span data-ttu-id="bdb35-155">Wenn Ihre App beispielsweise unter dem Creators-Update ausgeführt wird, hat der universelle API-Vertrag die Versionsnummer 4.</span><span class="sxs-lookup"><span data-stu-id="bdb35-155">For example, assume your app is running on the Creators Update, which has the 4th version of the universal API Contract.</span></span>

<span data-ttu-id="bdb35-156">Verschiedene Aufrufe von IsApiContractPresent würden diese Ergebnisse liefern:</span><span class="sxs-lookup"><span data-stu-id="bdb35-156">Various calls to IsApiContractPresent would have these results:</span></span>

- <span data-ttu-id="bdb35-157">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 5) = **false**</span><span class="sxs-lookup"><span data-stu-id="bdb35-157">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 5) = **false**</span></span>
- <span data-ttu-id="bdb35-158">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 4) = true</span><span class="sxs-lookup"><span data-stu-id="bdb35-158">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 4) = true</span></span>
- <span data-ttu-id="bdb35-159">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 3) = true</span><span class="sxs-lookup"><span data-stu-id="bdb35-159">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 3) = true</span></span>
- <span data-ttu-id="bdb35-160">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 2) = true</span><span class="sxs-lookup"><span data-stu-id="bdb35-160">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 2) = true</span></span>
- <span data-ttu-id="bdb35-161">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 1) = true.</span><span class="sxs-lookup"><span data-stu-id="bdb35-161">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 1) = true.</span></span>

<span data-ttu-id="bdb35-162">IsApiContractNotPresent liefert die Umkehrung von IsApiContractPresent.</span><span class="sxs-lookup"><span data-stu-id="bdb35-162">IsApiContractNotPresent returns the inverse of IsApiContractPresent.</span></span> <span data-ttu-id="bdb35-163">Aufrufe von IsApiContractNotPresent würden folgende Ergebnisse liefern:</span><span class="sxs-lookup"><span data-stu-id="bdb35-163">Calls to IsApiContractNotPresent would have these results:</span></span>

- <span data-ttu-id="bdb35-164">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 5) = **true**</span><span class="sxs-lookup"><span data-stu-id="bdb35-164">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 5) = **true**</span></span>
- <span data-ttu-id="bdb35-165">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 4) = false</span><span class="sxs-lookup"><span data-stu-id="bdb35-165">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 4) = false</span></span>
- <span data-ttu-id="bdb35-166">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 3) = false</span><span class="sxs-lookup"><span data-stu-id="bdb35-166">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 3) = false</span></span>
- <span data-ttu-id="bdb35-167">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 2) = false</span><span class="sxs-lookup"><span data-stu-id="bdb35-167">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 2) = false</span></span>
- <span data-ttu-id="bdb35-168">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 1) = false</span><span class="sxs-lookup"><span data-stu-id="bdb35-168">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 1) = false</span></span>

<span data-ttu-id="bdb35-169">Um die umgekehrte Bedingung zu verwenden, erstellen Sie einen zweiten bedingten XAML-Namespace, der die Bedingung **IsApiContractNotPresent** verwendet</span><span class="sxs-lookup"><span data-stu-id="bdb35-169">To use the inverse condition, you create a second conditional XAML namespace that uses the **IsApiContractNotPresent** conditional.</span></span> <span data-ttu-id="bdb35-170">Hier hat sie das Präfix „contract5NotPresent”.</span><span class="sxs-lookup"><span data-stu-id="bdb35-170">Here, it has the prefix 'contract5NotPresent'.</span></span>

```xaml
xmlns:contract5NotPresent="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractNotPresent(Windows.Foundation.UniversalApiContract,5)"

xmlns:contract5Present="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"
```

<span data-ttu-id="bdb35-171">Sind beide Namespaces definiert, können Sie die Text-Eigenschaft doppelt festlegen, solange Sie Qualifizierer voranstellen, die gewährleisten, dass zur Laufzeit nur eine Einstellung der Eigenschaft verwendet wird. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bdb35-171">With both namespaces defined, you can set the Text property twice as long as you prefix them with qualifiers that ensure only one property setting is used at runtime, like this:</span></span>

```xaml
<TextBlock contract5NotPresent:Text="Hello, World"
           contract5Present:Text="Hello, Fall Creators Update"/>
```

<span data-ttu-id="bdb35-172">Hier ist ein weiteres Beispiel, das die Hintergrundfarbe einer Schaltfläche festlegt.</span><span class="sxs-lookup"><span data-stu-id="bdb35-172">Here's another example that sets the background of a button.</span></span> <span data-ttu-id="bdb35-173">Die [Acrylic Material](../design/style/acrylic.md) Funktion ist ab dem Fall Creators Update verfügbar, so dass Sie Acrylic für den Hintergrund verwenden, wenn die App unter Fall Creators Update läuft.</span><span class="sxs-lookup"><span data-stu-id="bdb35-173">The [Acrylic material](../design/style/acrylic.md) feature is available starting with the Fall Creators Update, so you’ll use Acrylic for the background when the app runs on the Fall Creators Update.</span></span> <span data-ttu-id="bdb35-174">Unter früheren Versionen ist Acryl nicht verfügbar; in diesen Fällen legen Sie die Hintergrundfarbe auf Rot fest.</span><span class="sxs-lookup"><span data-stu-id="bdb35-174">It's not available on earlier versions, so in those cases, you set the background to red.</span></span>

```xaml
<Button Content="Button"
        contract5NotPresent:Background="Red"
        contract5Present:Background="{ThemeResource SystemControlAcrylicElementBrush}"/>
```

## <a name="create-controls-and-bind-properties"></a><span data-ttu-id="bdb35-175">Erstellen von Steuerelementen und Binden von Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="bdb35-175">Create controls and bind properties</span></span>

<span data-ttu-id="bdb35-176">Bisher haben Sie erfahren, wie Eigenschaften mithilfe bedingter XAML festgelegt werden. Sie können aber auch Steuerelemente bedingt instanziieren, je nach dem API-Vertrag, der zur Laufzeit verfügbar ist</span><span class="sxs-lookup"><span data-stu-id="bdb35-176">So far, you’ve seen how to set properties using conditional XAML, but you can also conditionally instantiate controls based on the API contract available at runtime.</span></span>

<span data-ttu-id="bdb35-177">Hier wird ein [ColorPicker](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker) instanziiert, wenn die App unter Fall Creators Update ausgeführt wird, in der das Steuerelement verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="bdb35-177">Here, a [ColorPicker](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker) is instantiated when the app runs on the Fall Creators Update where the control is available.</span></span> <span data-ttu-id="bdb35-178">Der ColorPicker ist erst ab Fall Creators Update verfügbar. Wenn die App unter früheren Versionen ausgeführt wird, verwenden Sie eine [ComboBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.combobox), um eine vereinfachte Farbauswahl für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-178">The ColorPicker isn't available prior to the Fall Creators Update, so when the app runs on earlier versions, you use a [ComboBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.combobox) to provide simplified color choices to the user.</span></span>

```xaml
<contract5Present:ColorPicker x:Name="colorPicker"
                              Grid.Column="1"
                              VerticalAlignment="Center"/>

<contract5NotPresent:ComboBox x:Name="colorComboBox"
                              PlaceholderText="Pick a color"
                              Grid.Column="1"
                              VerticalAlignment="Center">
```

<span data-ttu-id="bdb35-179">Sie können bedingte Qualifizierer mit unterschiedlichen Arten von [XAML-Syntax für Eigenschaften](../xaml-platform/xaml-syntax-guide.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="bdb35-179">You can use conditional qualifiers with different forms of [XAML property syntax](../xaml-platform/xaml-syntax-guide.md).</span></span> <span data-ttu-id="bdb35-180">Hier wird für Fall Creators Update die Fill-Eigenschaft des Rechtecks mit Syntax für Eigenschaftselemente festgelegt und für frühere Versionen mithilfe der Attributsyntax.</span><span class="sxs-lookup"><span data-stu-id="bdb35-180">Here, the rectangle’s Fill property is set using property element syntax for the Fall Creators Update, and using attribute syntax for previous versions.</span></span>

```xaml
<Rectangle x:Name="colorRectangle" Width="200" Height="200"
           contract5NotPresent:Fill="{x:Bind ((SolidColorBrush)((FrameworkElement)colorComboBox.SelectedItem).Tag), Mode=OneWay}">
    <contract5Present:Rectangle.Fill>
        <SolidColorBrush contract5Present:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
    </contract5Present:Rectangle.Fill>
</Rectangle>
```

<span data-ttu-id="bdb35-181">Wenn Sie eine Eigenschaft an eine anderen Eigenschaft binden, die von einem bedingten Namespace abhängig ist, müssen Sie dieselbe Bedingung für beide Eigenschaften verwenden.</span><span class="sxs-lookup"><span data-stu-id="bdb35-181">When you bind a property to another property that depends on a conditional namespace, you must use the same condition on both properties.</span></span> <span data-ttu-id="bdb35-182">Hier hängt `colorPicker.Color` vom bedingten Namespace „contract5Present” ab. Daher müssen Sie das Präfix „contract5Present” auf die Eigenschaft SolidColorBrush.Color setzen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-182">Here, `colorPicker.Color` depends on the 'contract5Present' conditional namespace, so you must also place the 'contract5Present' prefix on the SolidColorBrush.Color property.</span></span> <span data-ttu-id="bdb35-183">(Oder verwenden Sie das Präfix „contract5Present” mit der Eigenschaft SolidColorBrush statt mit der Color-Eigenschaft.) Andernfalls tritt während der Kompilierung ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="bdb35-183">(Or, you can place the 'contract5Present' prefix on the SolidColorBrush instead of on the Color property.) If you don’t, you’ll get a compile-time error.</span></span>

```xaml
<SolidColorBrush contract5Present:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
```

<span data-ttu-id="bdb35-184">Hier folgt der vollständige XAML-Code, der diese Szenarien veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="bdb35-184">Here's the complete XAML that demonstrates these scenarios.</span></span> <span data-ttu-id="bdb35-185">Dieses Beispiel enthält ein Rechteck und eine Benutzeroberfläche, mit der Sie die Farbe des Rechtecks festlegen können.</span><span class="sxs-lookup"><span data-stu-id="bdb35-185">This example contains a rectangle and a UI that lets you set the color of the rectangle.</span></span>

<span data-ttu-id="bdb35-186">Wenn die App unter Fall Creators Update ausgeführt wird, verwenden Sie einen ColorPicker, um dem Benutzer die Farbauswahl zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-186">When the app runs on the Fall Creators Update, you use a ColorPicker to let the user set the color.</span></span> <span data-ttu-id="bdb35-187">Der ColorPicker ist erst ab Fall Creators Update verfügbar. Wenn die App unter früheren Versionen ausgeführt wird, verwenden Sie eine ComboBox, um eine vereinfachte Farbauswahl für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="bdb35-187">The ColorPicker isn't available prior to the Fall Creators Update, so when the app runs on earlier versions, you use a combo box to provide simplified color choices to the user.</span></span>

```xaml
<Page
    x:Class="ConditionalTest.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:contract5Present="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"
    xmlns:contract5NotPresent="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractNotPresent(Windows.Foundation.UniversalApiContract,5)">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.ColumnDefinitions>
            <ColumnDefinition/>
            <ColumnDefinition/>
        </Grid.ColumnDefinitions>

        <Rectangle x:Name="colorRectangle" Width="200" Height="200"
                   contract5NotPresent:Fill="{x:Bind ((SolidColorBrush)((FrameworkElement)colorComboBox.SelectedItem).Tag), Mode=OneWay}">
            <contract5Present:Rectangle.Fill>
                <SolidColorBrush contract5Present:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
            </contract5Present:Rectangle.Fill>
        </Rectangle>

        <contract5Present:ColorPicker x:Name="colorPicker"
                                      Grid.Column="1"
                                      VerticalAlignment="Center"/>

        <contract5NotPresent:ComboBox x:Name="colorComboBox"
                                      PlaceholderText="Pick a color"
                                      Grid.Column="1"
                                      VerticalAlignment="Center">
            <ComboBoxItem>Red
                <ComboBoxItem.Tag>
                    <SolidColorBrush Color="Red"/>
                </ComboBoxItem.Tag>
            </ComboBoxItem>
            <ComboBoxItem>Blue
                <ComboBoxItem.Tag>
                    <SolidColorBrush Color="Blue"/>
                </ComboBoxItem.Tag>
            </ComboBoxItem>
            <ComboBoxItem>Green
                <ComboBoxItem.Tag>
                    <SolidColorBrush Color="Green"/>
                </ComboBoxItem.Tag>
            </ComboBoxItem>
        </contract5NotPresent:ComboBox>
    </Grid>
</Page>
```

## <a name="related-articles"></a><span data-ttu-id="bdb35-188">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bdb35-188">Related articles</span></span>

- [<span data-ttu-id="bdb35-189">Anleitung für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="bdb35-189">Guide to UWP apps</span></span>](https://msdn.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)
- [<span data-ttu-id="bdb35-190">Dynamically detecting features with API contracts (Dynamisches Erkennen von Features mithilfe von API-Verträgen)</span><span class="sxs-lookup"><span data-stu-id="bdb35-190">Dynamically detecting features with API contracts</span></span>](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/)
- <span data-ttu-id="bdb35-191">[API-Verträge](https://channel9.msdn.com/Events/Build/2015/3-733) (Video für Build 2015)</span><span class="sxs-lookup"><span data-stu-id="bdb35-191">[API Contracts](https://channel9.msdn.com/Events/Build/2015/3-733) (Build 2015 video)</span></span>