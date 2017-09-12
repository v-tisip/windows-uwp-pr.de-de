---
author: jwmsft
title: Bedingte XAML
description: "Verwenden neuer APIs in XAML-Markup bei gleichzeitiger Gewährleistung der Kompatibilität mit früheren Versionen"
ms.author: jimwalk
ms.date: 07/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: b6fad82b8610367f5a69b236c1783106454374f3
ms.sourcegitcommit: 73ea31d42a9b352af38b5eb5d3c06504b50f6754
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="conditional-xaml"></a><span data-ttu-id="8eb6f-104">Bedingte XAML</span><span class="sxs-lookup"><span data-stu-id="8eb6f-104">Conditional XAML</span></span>

<span data-ttu-id="8eb6f-105">*Bedingte XAML* bietet eine Möglichkeit, die Methode [ApiInformation.IsApiContractPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation#Windows_Foundation_Metadata_ApiInformation_IsApiContractPresent_System_String_System_UInt16_) in XAML-Markup zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-105">*Conditional XAML* provides a way to use the [ApiInformation.IsApiContractPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation#Windows_Foundation_Metadata_ApiInformation_IsApiContractPresent_System_String_System_UInt16_) method in XAML markup.</span></span> <span data-ttu-id="8eb6f-106">Sie sind damit in der Lage, im Markup nur dann Eigenschaften festzulegen und Objekte zu initialisieren, wenn die entsprechende API vorhanden ist, ohne Code-Behind zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-106">This lets you set properties and instantiate objects in markup based on the presence of an API without needing to use code behind.</span></span> <span data-ttu-id="8eb6f-107">Elemente oder Attribute werden selektiv analysiert, um zu bestimmen, ob sie zur Laufzeit zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-107">It selectively parses elements or attributes to determine whether they will be available at runtime.</span></span> <span data-ttu-id="8eb6f-108">Bedingte Anweisungen werden zur Laufzeit ausgewertet, und Elemente, die mit einem bedingten XAML-Tag gekennzeichnet sind, werden analysiert, wenn ihre Auswertung **true** ergibt. Andernfalls werden sie ignoriert.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-108">Conditional statements are evaluated at runtime, and elements qualified with a conditional XAML tag are parsed if evaluated to **true**; otherwise, they are ignored.</span></span>

<span data-ttu-id="8eb6f-109">Bedingte XAML ist ab dem Creators-Update (Version 1703, Build 15063) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-109">Conditional XAML is available starting with the Creators Update (version 1703, build 15063).</span></span> <span data-ttu-id="8eb6f-110">Die Verwendung bedingter XAML setzt voraus, dass Sie in Ihrem Visual Studio-Projekt Build 15063 (Creators Update) oder höher als Mindestversion und eine höhere Version als Zielversion festlegen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-110">To use conditional XAML, the Minimum Version of your Visual Studio project must be set to build 15063 (Creators Update) or later, and the Target Version be set to a later version than the Minimum.</span></span> <span data-ttu-id="8eb6f-111">Weitere Informationen zum Konfigurieren Ihres Visual Studio-Projekts finden Sie unter [Versionsadaptive Apps](version-adaptive-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8eb6f-111">See [Version adaptive apps](version-adaptive-apps.md) for more info about configuring your Visual Studio project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8eb6f-112">**VORABVERSION | Erfordert das Fall Creators Update**: Sie müssen [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) verwenden und [Insider-Builds 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) oder höher ausführen, um bedingte XAML nutzen zu können</span><span class="sxs-lookup"><span data-stu-id="8eb6f-112">**PRERELEASE | Requires Fall Creators Update**: You must target [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) and be running [Insider build 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) or later to use conditional XAML.</span></span>

> [!NOTE]
> <span data-ttu-id="8eb6f-113">Sie müssen zum Erstellen einer versionsadaptiven App mit einer Mindestversion kleiner als Build 15063 [versionsadaptiven Code](version-adaptive-code.md) und nicht XAML verwenden.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-113">To create a version adaptive app with a Minimum Version less than build 15063, you must use [version adaptive code](version-adaptive-code.md), not XAML.</span></span>

<span data-ttu-id="8eb6f-114">Wichtige Hintergrundinformationen über ApiInformation und API-Verträge finden Sie unter [Versionsadaptive Apps](version-adaptive-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8eb6f-114">For important background info about ApiInformation and API contracts, see [Version adaptive apps](version-adaptive-apps.md).</span></span>

## <a name="conditional-namespaces"></a><span data-ttu-id="8eb6f-115">Bedingte Namespaces</span><span class="sxs-lookup"><span data-stu-id="8eb6f-115">Conditional namespaces</span></span>

<span data-ttu-id="8eb6f-116">Um eine Bedingung in XAML zu verwenden, müssen Sie zuerst einen bedingten [XAML-Namespace](../xaml-platform/xaml-namespaces-and-namespace-mapping.md) am Beginn der Seite deklarieren.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-116">To use a conditional in XAML, you must first declare a conditional [XAML namespace](../xaml-platform/xaml-namespaces-and-namespace-mapping.md) at the top of your page.</span></span> <span data-ttu-id="8eb6f-117">Hier ein Pseudocodebeispiel für einen bedingten Namespace:</span><span class="sxs-lookup"><span data-stu-id="8eb6f-117">Here's a psuedo-code example of a conditional namespace:</span></span>

```xaml
xmlns:myNamespace="schema?conditionalMethod(parameter)"
```

<span data-ttu-id="8eb6f-118">Ein bedingter Namespace besteht aus zwei Teilen, die durch das Zeichen '?' getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-118">A conditional namespace can be broken down into two parts separated by the '?' delimiter.</span></span> <span data-ttu-id="8eb6f-119">Der Inhalt vor dem Trennzeichen gibt den Namespace oder das Schema an, in dem die referenzierte API enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-119">The content preceding the delimiter indicates the namespace or schema that contains the API being referenced.</span></span> <span data-ttu-id="8eb6f-120">Der Inhalt nach dem Trennzeichen '?' stellt die bedingte Methode dar, die bestimmt, ob die Auswertung für den bedingten Namespace **true** oder **false** ergibt.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-120">The content after the '?' delimiter represents the conditional method that determines whether the conditional namespace evaluates to **true** or **false**.</span></span>

<span data-ttu-id="8eb6f-121">In den meisten Fällen wird das Schema der standardmäßige XAML-Namespace sein:</span><span class="sxs-lookup"><span data-stu-id="8eb6f-121">In most cases, the schema will be the default XAML namespace:</span></span>

```xaml
xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
```

<span data-ttu-id="8eb6f-122">Bedingte XAML unterstützt die folgenden bedingten Methoden:</span><span class="sxs-lookup"><span data-stu-id="8eb6f-122">Conditional XAML supports the following conditional methods:</span></span>

<span data-ttu-id="8eb6f-123">Methode</span><span class="sxs-lookup"><span data-stu-id="8eb6f-123">Method</span></span> | <span data-ttu-id="8eb6f-124">Umkehrung</span><span class="sxs-lookup"><span data-stu-id="8eb6f-124">Inverse</span></span>
------ | -------
<span data-ttu-id="8eb6f-125">IsApiContractPresent(ContractName, VersionNumber)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-125">IsApiContractPresent(ContractName, VersionNumber)</span></span> | <span data-ttu-id="8eb6f-126">IsApiContractNotPresent(ContractName, VersionNumber)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-126">IsApiContractNotPresent(ContractName, VersionNumber)</span></span>
<span data-ttu-id="8eb6f-127">IsTypePresent(ControlType)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-127">IsTypePresent(ControlType)</span></span> | <span data-ttu-id="8eb6f-128">IsTypeNotPresent(ControlType)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-128">IsTypeNotPresent(ControlType)</span></span>
<span data-ttu-id="8eb6f-129">IsPropertyPresent(ControlType, PropertyName)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-129">IsPropertyPresent(ControlType, PropertyName)</span></span> | <span data-ttu-id="8eb6f-130">IsPropertyNotPresent(ControlType, PropertyName)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-130">IsPropertyNotPresent(ControlType, PropertyName)</span></span>

<span data-ttu-id="8eb6f-131">(Weitere Informationen zu diesen Methoden finden Sie in den folgenden Abschnitten.)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-131">(More on these methods in the sections below.)</span></span>

> [!NOTE] 
> <span data-ttu-id="8eb6f-132">Es wird empfohlen, dass Sie IsApiContractPresent und IsApiContractNotPresent verwenden.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-132">We recommend you use IsApiContractPresent and IsApiContractNotPresent.</span></span> <span data-ttu-id="8eb6f-133">Andere Bedingungen werden im Visual Studio-Entwurf nicht vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-133">Other conditionals are not fully supported in the Visual Studio design experience.</span></span>

## <a name="create-a-namespace-and-set-a-property"></a><span data-ttu-id="8eb6f-134">Erstellen eines Namespace und Festlegen einer Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8eb6f-134">Create a namespace and set a property</span></span>

<span data-ttu-id="8eb6f-135">In diesem Beispiel zeigen Sie „Hello, Windows-Insider” als Inhalt eines Textblocks an, wenn die App unter der Windows Insider Preview (Fall Creators Update) ausgeführt wird, und standardmäßig keinen Inhalt, wenn eine frühere Version vorliegt.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-135">In this example, you’ll display, "Hello, Windows Insider", as the content of a text block if the app runs on the Windows Insider Preview (Fall Creators Update), and default to no content if it's on a previous version.</span></span>

<span data-ttu-id="8eb6f-136">Zuerst definieren Sie einen benutzerdefinierten Namespace mit dem Präfix „Insider” und verwenden den standardmäßigen XAML-Namespace (http://schemas.microsoft.com/winfx/2006/xaml/presentation) als das Schema, das die Eigenschaft [TextBlock.Text](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock#Windows_UI_Xaml_Controls_TextBlock_Text) enthält.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-136">First, define a custom namespace with the prefix 'insider' and use the default XAML namespace (http://schemas.microsoft.com/winfx/2006/xaml/presentation) as the schema containing the [TextBlock.Text](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock#Windows_UI_Xaml_Controls_TextBlock_Text) property.</span></span> <span data-ttu-id="8eb6f-137">Um daraus einen bedingten Namespace zu machen, fügen Sie das Trennzeichen '?'</span><span class="sxs-lookup"><span data-stu-id="8eb6f-137">To make this a conditional namespace, add the ‘?’</span></span> <span data-ttu-id="8eb6f-138">nach dem Schema ein.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-138">delimiter after the schema.</span></span>

<span data-ttu-id="8eb6f-139">Dann definieren Sie eine Bedingung, die **true** auf Geräten zurückgibt, die Windows Insider Preview ausführen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-139">You then define a conditional that returns **true** on devices that are running the Windows Insider Preview or later.</span></span> <span data-ttu-id="8eb6f-140">Sie können die ApiInformation-Methode **IsApiContractPresent** verwenden, um zu prüfen, ob die 5. Version von UniversalApiContract vorliegt.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-140">You use the ApiInformation method **IsApiContractPresent** to check for the 5th version of the UniversalApiContract.</span></span> <span data-ttu-id="8eb6f-141">Version 5 von UniversalApiContract wurde mit Windows Insider Preview (Fall Creators Update) veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-141">Version 5 of the UniversalApiContract was released with the Windows Insider Preview (Fall Creators Update).</span></span>

```xaml
xmlns:insider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"
```

<span data-ttu-id="8eb6f-142">Nachdem der Namespace definiert ist, stellen Sie das Namespacepräfix der Text-Eigenschaft Ihrer TextBox voran, um sie als Eigenschaft auszuzeichnen, die bedingt zur Laufzeit festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-142">After the namespace is defined, you prepend the namespace prefix to the Text property of your TextBox to qualify it as a property that should be set conditionally at runtime.</span></span>

```xaml
<TextBlock insider:Text="Hello, Windows Insider"/>
```

<span data-ttu-id="8eb6f-143">Hier die gesamte XAML.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-143">Here's the complete XAML.</span></span>

```xaml
<Page
    x:Class="ConditionalTest.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:insider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <TextBlock x:Name="textBlock" insider:Text="Hello, Windows Insider"/>
    </Grid>
</Page>
```

<span data-ttu-id="8eb6f-144">Wenn Sie dieses Beispiel unter der Insider Preview ausführen, wird der Text „I am a Windows Insider” angezeigt. Wenn Sie es unter dem Creators Update ausführen, wird kein Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-144">When you run this example on the Insider Preview, the text, “I am a Windows Insider” is shown; when you run it on the Creators Update, no text is shown.</span></span>

<span data-ttu-id="8eb6f-145">Mit bedingter XAML können Sie die API-Prüfungen statt im Code in Ihrem Markup ausführen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-145">Conditional XAML lets you perform the API checks you can do in code in your markup instead.</span></span> <span data-ttu-id="8eb6f-146">Hier der entsprechende Code für dieses Beispiel.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-146">Here's the equivalent code for this check.</span></span>

```csharp
if (ApiInformation.IsApiContractPresent("Windows.Foundation.UniversalApiContract", 5))
{
    textBlock.Text = "Hello, Windows Insider";
}
```

<span data-ttu-id="8eb6f-147">Beachten Sie: Obwohl die Methode IsApiContractPresent eine Zeichenfolge für den Parameter *contractName* erwartet, wird diese in der XAML-Namespace-Deklaration nicht in Anführungszeichen ("") gesetzt.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-147">Notice that even though the IsApiContractPresent method takes a string for the *contractName* parameter, you don't put it in quotes (" ") in the XAML namespace declaration.</span></span>

## <a name="use-ifelse-conditions"></a><span data-ttu-id="8eb6f-148">Verwenden von if/else-Bedingungen</span><span class="sxs-lookup"><span data-stu-id="8eb6f-148">Use if/else conditions</span></span>

<span data-ttu-id="8eb6f-149">Im vorherigen Beispiel wird die Text-Eigenschaft nur festgelegt, wenn die App mit der Insider Preview ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-149">In the previous example, the Text property is set only when the app runs on the Insider Preview.</span></span> <span data-ttu-id="8eb6f-150">Wie ist aber vorzugehen, um einen alternativen Text anzuzeigen, wenn das Creators Update ausgeführt wird?</span><span class="sxs-lookup"><span data-stu-id="8eb6f-150">But what if you want to show different text when it runs on the Creators Update?</span></span> <span data-ttu-id="8eb6f-151">Sie können versuchen, die Text-Eigenschaft wie folgt ohne einen bedingten Qualifizierer festzulegen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-151">You could try to set the Text property without a conditional qualifier, like this.</span></span>

```xaml
<!-- DO NOT USE -->
<TextBlock Text="Hello, World" insider:Text="Hello, Windows Insider"/>
```

<span data-ttu-id="8eb6f-152">Dies funktioniert unter dem Creators Update, aber mit der Insider Preview erhalten Sie eine Fehlermeldung, die besagt, dass die Text-Eigenschaft mehrmals festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-152">This will work when it’s run on the Creators Update, but when it runs on the Insider Preview, you’ll get an error saying that the Text property is set more than once.</span></span>

<span data-ttu-id="8eb6f-153">Um unterschiedliche Texte festzulegen für den Fall, dass die App unter verschiedenen Versionen von Windows10 ausgeführt wird, benötigen Sie eine andere Bedingung.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-153">To set different text when the app runs on different versions of Windows 10, you need another condition.</span></span> <span data-ttu-id="8eb6f-154">Bedingte XAML bietet eine Umkehrung jeder unterstützten ApiInformation-Methode, damit Sie wie folgt if/else-Szenarien erstellen können.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-154">Conditional XAML provides an inverse of each supported ApiInformation method to let you create if/else conditional scenarios like this.</span></span>
 
<span data-ttu-id="8eb6f-155">Die Methode IsApiContractPresent liefert **true**, wenn das aktuelle Gerät die angegebene Vertrags- und Versionsnummer enthält.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-155">The IsApiContractPresent method returns **true** if the current device contains the specified contract and version number.</span></span> <span data-ttu-id="8eb6f-156">Wenn Ihre App beispielsweise unter dem Creators-Update ausgeführt wird, hat der universelle API-Vertrag die Versionsnummer 4.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-156">For example, assume your app is running on the Creators Update, which has the 4th version of the universal API Contract.</span></span>

<span data-ttu-id="8eb6f-157">Verschiedene Aufrufe von IsApiContractPresent würden diese Ergebnisse liefern:</span><span class="sxs-lookup"><span data-stu-id="8eb6f-157">Various calls to IsApiContractPresent would have these results:</span></span>

- <span data-ttu-id="8eb6f-158">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 5) = **false**</span><span class="sxs-lookup"><span data-stu-id="8eb6f-158">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 5) = **false**</span></span>
- <span data-ttu-id="8eb6f-159">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 4) = true</span><span class="sxs-lookup"><span data-stu-id="8eb6f-159">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 4) = true</span></span>
- <span data-ttu-id="8eb6f-160">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 3) = true</span><span class="sxs-lookup"><span data-stu-id="8eb6f-160">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 3) = true</span></span>
- <span data-ttu-id="8eb6f-161">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 2) = true</span><span class="sxs-lookup"><span data-stu-id="8eb6f-161">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 2) = true</span></span>
- <span data-ttu-id="8eb6f-162">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 1) = true.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-162">IsApiContractPresent(Windows.Foundation.UniversalApiContract, 1) = true.</span></span>

<span data-ttu-id="8eb6f-163">IsApiContractNotPresent liefert die Umkehrung von IsApiContractPresent.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-163">IsApiContractNotPresent returns the inverse of IsApiContractPresent.</span></span> <span data-ttu-id="8eb6f-164">Aufrufe von IsApiContractNotPresent würden folgende Ergebnisse liefern:</span><span class="sxs-lookup"><span data-stu-id="8eb6f-164">Calls to IsApiContractNotPresent would have these results:</span></span>

- <span data-ttu-id="8eb6f-165">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 5) = **true**</span><span class="sxs-lookup"><span data-stu-id="8eb6f-165">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 5) = **true**</span></span>
- <span data-ttu-id="8eb6f-166">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 4) = false</span><span class="sxs-lookup"><span data-stu-id="8eb6f-166">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 4) = false</span></span>
- <span data-ttu-id="8eb6f-167">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 3) = false</span><span class="sxs-lookup"><span data-stu-id="8eb6f-167">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 3) = false</span></span>
- <span data-ttu-id="8eb6f-168">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 2) = false</span><span class="sxs-lookup"><span data-stu-id="8eb6f-168">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 2) = false</span></span>
- <span data-ttu-id="8eb6f-169">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 1) = false</span><span class="sxs-lookup"><span data-stu-id="8eb6f-169">IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 1) = false</span></span>

<span data-ttu-id="8eb6f-170">Um die umgekehrte Bedingung zu verwenden, erstellen Sie einen zweiten bedingten XAML-Namespace, der die Bedingung **IsApiContractNotPresent** verwendet</span><span class="sxs-lookup"><span data-stu-id="8eb6f-170">To use the inverse condition, you create a second conditional XAML namespace that uses the **IsApiContractNotPresent** conditional.</span></span> <span data-ttu-id="8eb6f-171">In diesem Fall hat sie das Präfix „notInsider”.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-171">Here, it has the prefix 'notInsider'.</span></span>

```xaml
xmlns:insider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"

xmlns:notInsider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractNotPresent(Windows.Foundation.UniversalApiContract,5)"
```

<span data-ttu-id="8eb6f-172">Sind beide Namespaces definiert, können Sie die Text-Eigenschaft doppelt festlegen, solange Sie Qualifizierer voranstellen, die gewährleisten, dass zur Laufzeit nur eine Einstellung der Eigenschaft verwendet wird. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8eb6f-172">With both namespaces defined, you can set the Text property twice as long as you prefix them with qualifiers that ensure only one property setting is used at runtime, like this:</span></span>

```xaml
<TextBlock notInsider:Text="Hello, World" 
           insider:Text="Hello, Windows Insider"/>
```

<span data-ttu-id="8eb6f-173">Hier ist ein weiteres Beispiel, das die Hintergrundfarbe einer Schaltfläche festlegt.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-173">Here's another example that sets the background of a button.</span></span> <span data-ttu-id="8eb6f-174">Das Feature [Acryl-Material](../style/acrylic.md) ist mit der Insider Preview (Fall Creators Update) verfügbar. Sie verwenden also Acryl für den Hintergrund, wenn die App unter der Insider Preview ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-174">The [Acrylic material](../style/acrylic.md) feature is available starting with the Insider Preview (Fall Creators Update), so you’ll use Acrylic for the background when the app runs on the Insider Preview.</span></span> <span data-ttu-id="8eb6f-175">Unter früheren Versionen ist Acryl nicht verfügbar; in diesen Fällen legen Sie die Hintergrundfarbe auf Rot fest.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-175">It's not available on earlier versions, so in those cases, you set the background to red.</span></span>

```xaml
<Button Content="Button"
        notInsider:Background="Red"
        insider:Background="{ThemeResource SystemControlAcrylicElementBrush}"/>
```

## <a name="create-controls-and-bind-properties"></a><span data-ttu-id="8eb6f-176">Erstellen von Steuerelementen und Binden von Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="8eb6f-176">Create controls and bind properties</span></span>

<span data-ttu-id="8eb6f-177">Bisher haben Sie erfahren, wie Eigenschaften mithilfe bedingter XAML festgelegt werden. Sie können aber auch Steuerelemente bedingt instanziieren, je nach dem API-Vertrag, der zur Laufzeit verfügbar ist</span><span class="sxs-lookup"><span data-stu-id="8eb6f-177">So far, you’ve seen how to set properties using conditional XAML, but you can also conditionally instantiate controls based on the API contract available at runtime.</span></span>

<span data-ttu-id="8eb6f-178">Hier wird ein [ColorPicker](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker) instanziiert, wenn die App unter der Insider Preview ausgeführt wird, in der das Steuerelement verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-178">Here, a [ColorPicker](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker) is instantiated when the app runs on the Insider Preview where the control is available.</span></span> <span data-ttu-id="8eb6f-179">Der ColorPicker ist erst ab der Insider Preview verfügbar. Wenn die App unter früheren Versionen ausgeführt wird, verwenden Sie eine [ComboBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.combobox), um eine vereinfachte Farbauswahl für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-179">The ColorPicker isn't available prior to the Insider Preview, so when the app runs on earlier versions, you use a [ComboBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.combobox) to provide simplified color choices to the user.</span></span>

```xaml
<insider:ColorPicker x:Name="colorPicker" Grid.Column="1"/>

<notInsider:ComboBox x:Name="colorComboBox" PlaceholderText="Pick a color"
                     Grid.Column="1" VerticalAlignment="Center">
```

<span data-ttu-id="8eb6f-180">Sie können bedingte Qualifizierer mit unterschiedlichen Arten von [XAML-Syntax für Eigenschaften](../xaml-platform/xaml-syntax-guide.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-180">You can use conditional qualifiers with different forms of [XAML property syntax](../xaml-platform/xaml-syntax-guide.md).</span></span> <span data-ttu-id="8eb6f-181">Hier wird für die Insider Preview die Fill-Eigenschaft des Rechtecks mit Syntax für Eigenschaftselemente festgelegt und für frühere Versionen mithilfe der Attributsyntax.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-181">Here, the rectangle’s Fill property is set using property element syntax for the Insider Preview, and using attribute syntax for previous versions.</span></span>

```xaml
<Rectangle x:Name="colorRectangle" Width="200" Height="200"
           notInsider:Fill="{x:Bind ((SolidColorBrush)((FrameworkElement)colorComboBox.SelectedItem).Tag), Mode=OneWay}">
    <insider:Rectangle.Fill>
        <SolidColorBrush insider:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
    </insider:Rectangle.Fill>
</Rectangle>
```

<span data-ttu-id="8eb6f-182">Wenn Sie eine Eigenschaft an eine anderen Eigenschaft binden, die von einem bedingten Namespace abhängig ist, müssen Sie dieselbe Bedingung für beide Eigenschaften verwenden.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-182">When you bind a property to another property that depends on a conditional namespace, you must use the same condition on both properties.</span></span> <span data-ttu-id="8eb6f-183">Hier ist `colorPicker.Color` vom bedingten „Insider”-Namespace abhängig, sodass Sie das Präfix „Insider” auch für Eigenschaft SolidColorBrush.Color verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-183">Here, `colorPicker.Color` depends on the 'insider' conditional namespace, so you must also place the 'insider' prefix on the SolidColorBrush.Color property.</span></span> <span data-ttu-id="8eb6f-184">(Oder verwenden Sie das Präfix „Insider” mit der Eigenschaft SolidColorBrush statt mit der Color-Eigenschaft.) Andernfalls tritt während der Kompilierung ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-184">(Or, you can place the 'insider' prefix on the SolidColorBrush instead of on the Color property.) If you don’t, you’ll get a compile-time error.</span></span>

```xaml
<SolidColorBrush insider:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
```

<span data-ttu-id="8eb6f-185">Hier folgt der vollständige XAML-Code, der diese Szenarien veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-185">Here's the complete XAML that demonstrates these scenarios.</span></span> <span data-ttu-id="8eb6f-186">Dieses Beispiel enthält ein Rechteck und eine Benutzeroberfläche, mit der Sie die Farbe des Rechtecks festlegen können.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-186">This example contains a rectangle and a UI that lets you set the color of the rectangle.</span></span>

<span data-ttu-id="8eb6f-187">Wenn die App unter der Insider Preview ausgeführt wird, verwenden Sie einen ColorPicker, um dem Benutzer die Farbauswahl zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-187">When the app runs on the Insider Preview, you use a ColorPicker to let the user set the color.</span></span> <span data-ttu-id="8eb6f-188">Da der ColorPicker erst ab der Insider Preview verfügbar ist, verwenden Sie, wenn die App unter einer früheren Version ausgeführt wird, eine ComboBox, um eine vereinfachte Farbauswahl für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8eb6f-188">The ColorPicker isn't available prior to the Insider Preview, so when the app runs on earlier versions, you use a combo box to provide simplified color choices to the user.</span></span>

```xaml
<Page
    x:Class="ConditionalTest.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:insider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"
    xmlns:notInsider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractNotPresent(Windows.Foundation.UniversalApiContract,5)">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.ColumnDefinitions>
            <ColumnDefinition/>
            <ColumnDefinition/>
        </Grid.ColumnDefinitions>

        <Rectangle x:Name="colorRectangle" Width="200" Height="200"
                   notInsider:Fill="{x:Bind ((SolidColorBrush)((FrameworkElement)colorComboBox.SelectedItem).Tag), Mode=OneWay}">
            <insider:Rectangle.Fill>
                <SolidColorBrush insider:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
            </insider:Rectangle.Fill>
        </Rectangle>

        <insider:ColorPicker x:Name="colorPicker" Grid.Column="1"/>

        <notInsider:ComboBox x:Name="colorComboBox" PlaceholderText="Pick a color"
                     Grid.Column="1" VerticalAlignment="Center">
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
        </notInsider:ComboBox>
    </Grid>
</Page>
```

## <a name="related-articles"></a><span data-ttu-id="8eb6f-189">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="8eb6f-189">Related articles</span></span>

- [<span data-ttu-id="8eb6f-190">Anleitung für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="8eb6f-190">Guide to UWP apps</span></span>](https://msdn.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)
- [<span data-ttu-id="8eb6f-191">Dynamically detecting features with API contracts (Dynamisches Erkennen von Features mithilfe von API-Verträgen)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-191">Dynamically detecting features with API contracts</span></span>](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/)
- <span data-ttu-id="8eb6f-192">[API-Verträge](https://channel9.msdn.com/Events/Build/2015/3-733) (Video für Build 2015)</span><span class="sxs-lookup"><span data-stu-id="8eb6f-192">[API Contracts](https://channel9.msdn.com/Events/Build/2015/3-733) (Build 2015 video)</span></span>