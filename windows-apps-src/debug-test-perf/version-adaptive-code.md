---
author: jwmsft
title: Versionsadaptiver Code
description: Mithilfe der neuen ApiInformation-Klasse können Sie neue APIs nutzen und gleichzeitig die Kompatibilität mit früheren Versionen gewährleisten.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: 3293e91e-6888-4cc3-bad3-61e5a7a7ab4e
ms.localizationpriority: medium
ms.openlocfilehash: e25a3bd447519ce344a95a1c335451f731552487
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5598862"
---
# <a name="version-adaptive-code"></a><span data-ttu-id="3b1e9-104">Versionsadaptiver Code</span><span class="sxs-lookup"><span data-stu-id="3b1e9-104">Version adaptive code</span></span>

<span data-ttu-id="3b1e9-105">Das Schreiben von adaptivem Code ist vergleichbar mit dem [Erstellen einer adaptiven Benutzeroberfläche](https://msdn.microsoft.com/windows/uwp/layout/layouts-with-xaml).</span><span class="sxs-lookup"><span data-stu-id="3b1e9-105">You can think about writing adaptive code similarly to how you think about [creating an adaptive UI](https://msdn.microsoft.com/windows/uwp/layout/layouts-with-xaml).</span></span> <span data-ttu-id="3b1e9-106">Dabei können Sie etwa Ihre grundlegende Benutzeroberfläche für den kleinsten Bildschirm entwerfen und anschließend Elemente verschieben oder hinzufügen, wenn erkannt wird, dass die App auf einem größeren Bildschirm ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-106">You might design your base UI to run on the smallest screen, and then move or add elements when you detect that your app is running on a larger screen.</span></span> <span data-ttu-id="3b1e9-107">Bei adaptivem Code schreiben Sie Ihren Basiscode für die niedrigste Betriebssystemversion und können anschließend ausgewählte Features hinzufügen, wenn erkannt wird, dass Ihre App unter einer höheren Version ausgeführt wird, die über das neue Feature verfügt.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-107">With adaptive code, you write your base code to run on the lowest OS version, and you can add hand-selected features when you detect that your app is running on a higher version where the new feature is available.</span></span>

<span data-ttu-id="3b1e9-108">Wichtige Hintergrundinformationen über ApiInformation, API-Verträge und das Konfigurieren von Visual Studio finden Sie unter [Versionsadaptive Apps](version-adaptive-apps.md).</span><span class="sxs-lookup"><span data-stu-id="3b1e9-108">For important background info about ApiInformation, API contracts, and configuring Visual Studio, see [Version adaptive apps](version-adaptive-apps.md).</span></span>

### <a name="runtime-api-checks"></a><span data-ttu-id="3b1e9-109">API-Laufzeitprüfungen</span><span class="sxs-lookup"><span data-stu-id="3b1e9-109">Runtime API checks</span></span>

<span data-ttu-id="3b1e9-110">Verwenden Sie die [Windows.Foundation.Metadata.ApiInformation](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.apiinformation.aspx)-Klasse in einer Bedingung in Ihrem Code, um zu testen, ob die aufzurufende API vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-110">You use the [Windows.Foundation.Metadata.ApiInformation](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.apiinformation.aspx) class in a condition in your code to test for the presence of the API you want to call.</span></span> <span data-ttu-id="3b1e9-111">Diese Bedingung wird immer ausgewertet – ganz gleich, wo Ihre App ausgeführt wird. Das Ergebnis ist aber nur dann **True**, wenn sie auf einem Gerät ausgeführt wird, auf dem die API vorhanden ist und somit aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-111">This condition is evaluated wherever your app runs, but it evaluates to **true** only on devices where the API is present and therefore available to call.</span></span> <span data-ttu-id="3b1e9-112">So können Sie Apps mit versionsadaptivem Code erstellen, die APIs verwenden, welche nur unter bestimmten Betriebssystemversionen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-112">This lets you write version adaptive code in order to create apps that use APIs that are available only on certain OS versions.</span></span>

<span data-ttu-id="3b1e9-113">Hier gehen wir anhand von spezifischen Beispielen auf die Nutzung neuer Features der Windows Insider Preview ein.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-113">Here, we look at specific examples for targeting new features in the Windows Insider Preview.</span></span> <span data-ttu-id="3b1e9-114">Eine allgemeine Übersicht über die Verwendung von **ApiInformation** finden Sie in der [Übersicht zu Gerätefamilien](https://docs.microsoft.com/en-us/uwp/extension-sdks/device-families-overview#writing-code) sowie im Blogbeitrag [Dynamically detecting features with API contracts](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/) (Dynamisches Erkennen von Features mithilfe von API-Verträgen).</span><span class="sxs-lookup"><span data-stu-id="3b1e9-114">For a general overview of using **ApiInformation**, see [Device families overview](https://docs.microsoft.com/en-us/uwp/extension-sdks/device-families-overview#writing-code) and the blog post [Dynamically detecting features with API contracts](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/).</span></span>

> [!TIP]
> <span data-ttu-id="3b1e9-115">Eine hohe Anzahl von API-Laufzeitprüfungen kann die Leistung Ihrer App beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-115">Numerous runtime API checks can affect the performance of your app.</span></span> <span data-ttu-id="3b1e9-116">Die Prüfungen werden in diesen Beispielen inline veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-116">We show the checks inline in these examples.</span></span> <span data-ttu-id="3b1e9-117">In Produktionscode empfiehlt es sich, die Prüfung nur einmal durchzuführen, das Ergebnis zwischenzuspeichern und es anschließend in der gesamten App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-117">In production code, you should perform the check once and cache the result, then used the cached result throughout your app.</span></span> 

### <a name="unsupported-scenarios"></a><span data-ttu-id="3b1e9-118">Nicht unterstützte Szenarien</span><span class="sxs-lookup"><span data-stu-id="3b1e9-118">Unsupported scenarios</span></span>

<span data-ttu-id="3b1e9-119">In den meisten Fällen können Sie die auf die SDK-Version10240 festgelegte Mindestversion Ihrer App beibehalten und neue APIs auf der Grundlage von Laufzeitprüfungen aktivieren, wenn die App unter einer höheren Version ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-119">In most cases, you can keep your app's Minimum Version set to SDK version 10240 and use runtime checks to enable any new APIs when your app runs on later a version.</span></span> <span data-ttu-id="3b1e9-120">In bestimmten Fällen müssen Sie allerdings die Mindestversion Ihrer App erhöhen, um neue Features verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-120">However, there are some cases where you must increase your app's Minimum Version in order to use new features.</span></span>

<span data-ttu-id="3b1e9-121">Die Mindestversion der App muss erhöht werden, wenn Sie Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="3b1e9-121">You must increase your app's Minimum Version if you use:</span></span>
- <span data-ttu-id="3b1e9-122">Eine neue API, die eine Funktion erfordert, die in einer früheren Version nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-122">a new API that requires a capability that isn't available in an earlier version.</span></span> <span data-ttu-id="3b1e9-123">Die unterstützte Mindestversion muss auf eine höhere Version festgelegt werden, die über diese Funktion verfügt.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-123">You must increase the minimum supported version to one that includes that capability.</span></span> <span data-ttu-id="3b1e9-124">Weitere Informationen finden Sie unter [Deklaration der App-Funktionen](../packaging/app-capability-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="3b1e9-124">For more info, see [App capability declarations](../packaging/app-capability-declarations.md).</span></span>
- <span data-ttu-id="3b1e9-125">Einen neuen Ressourcenschlüssel, der zu „generic.xaml“ hinzugefügt wurde und in einer früheren Version nicht verfügbar war.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-125">any new resource keys added to generic.xaml and not available in a previous version.</span></span> <span data-ttu-id="3b1e9-126">Die zur Laufzeit verwendete Version von „generic.xaml“ wird durch die auf dem Gerät ausgeführte Betriebssystemversion bestimmt.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-126">The version of generic.xaml used at runtime is determined by the OS version the device is running on.</span></span> <span data-ttu-id="3b1e9-127">Mit API-Laufzeitprüfungen lässt sich nicht ermitteln, ob XAML-Ressourcen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-127">You can't use runtime API checks to determine the presence of XAML resources.</span></span> <span data-ttu-id="3b1e9-128">Daher dürfen nur Ressourcenschlüssel verwendet werden, die in der von der App unterstützten Mindestversion zur Verfügung stehen. Andernfalls bringt eine [XAMLParseException](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.markup.xamlparseexception.aspx) Ihre App zur Laufzeit zum Absturz.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-128">So, you must only use resource keys that are available in the minimum version that your app supports or a [XAMLParseException](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.markup.xamlparseexception.aspx) will cause your app to crash at runtime.</span></span>

### <a name="adaptive-code-options"></a><span data-ttu-id="3b1e9-129">Optionen für adaptiven Code</span><span class="sxs-lookup"><span data-stu-id="3b1e9-129">Adaptive code options</span></span>

<span data-ttu-id="3b1e9-130">Adaptiver Code kann auf zwei Arten erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-130">There are two ways to create adaptive code.</span></span> <span data-ttu-id="3b1e9-131">In den meisten Fällen schreiben Sie den Markupcode Ihrer App für die Mindestversion und verwenden dann Ihren App-Code, um ggf. die Nutzung neuerer Betriebssystemfeatures zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-131">In most cases, you write your app markup to run on the Minimum version, then use your app code to tap into newer OS features when present.</span></span> <span data-ttu-id="3b1e9-132">Wenn Sie allerdings eine Eigenschaft in einem visuellen Zustand aktualisieren müssen und sich zwischen Betriebssystemversionen lediglich ein Eigenschafts- oder Enumerationswert ändert, können Sie einen erweiterbaren Zustandsauslöser erstellen, dessen Aktivierung davon abhängt, ob eine API vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-132">However, if you need to update a property in a visual state, and there is only a property or enumeration value change between OS versions, you can create an extensible state trigger that’s activated based on the presence of an API.</span></span>

<span data-ttu-id="3b1e9-133">Im Anschluss finden Sie eine Gegenüberstellung dieser Optionen:</span><span class="sxs-lookup"><span data-stu-id="3b1e9-133">Here, we compare these options.</span></span>

**<span data-ttu-id="3b1e9-134">App-Code</span><span class="sxs-lookup"><span data-stu-id="3b1e9-134">App code</span></span>**

<span data-ttu-id="3b1e9-135">Verwendung</span><span class="sxs-lookup"><span data-stu-id="3b1e9-135">When to use:</span></span>
- <span data-ttu-id="3b1e9-136">Empfohlen für alle Szenarien mit adaptivem Code mit Ausnahme bestimmter Fälle, die weiter unten für erweiterbare Auslöser definiert sind.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-136">Recommended for all adaptive code scenarios except for specific cases defined below for extensible triggers.</span></span>

<span data-ttu-id="3b1e9-137">Vorteile:</span><span class="sxs-lookup"><span data-stu-id="3b1e9-137">Benefits:</span></span>
- <span data-ttu-id="3b1e9-138">Weniger Aufwand/Komplexität für Entwickler beim Einbinden von API-Unterschieden in das Markup</span><span class="sxs-lookup"><span data-stu-id="3b1e9-138">Avoids developer overhead/complexity of tying API differences into markup.</span></span>

<span data-ttu-id="3b1e9-139">Nachteile:</span><span class="sxs-lookup"><span data-stu-id="3b1e9-139">Drawbacks:</span></span>
- <span data-ttu-id="3b1e9-140">Keine Designerunterstützung</span><span class="sxs-lookup"><span data-stu-id="3b1e9-140">No Designer support.</span></span>

**<span data-ttu-id="3b1e9-141">Zustandsauslöser</span><span class="sxs-lookup"><span data-stu-id="3b1e9-141">State Triggers</span></span>**

<span data-ttu-id="3b1e9-142">Verwendung</span><span class="sxs-lookup"><span data-stu-id="3b1e9-142">When to use:</span></span>
- <span data-ttu-id="3b1e9-143">Verwenden Sie diese Option, wenn sich zwischen Betriebssystemversionen nur eine Eigenschaft oder Enumeration geändert hat, keine Änderung der Logik erforderlich ist und eine Verbindung mit einem visuellen Zustand besteht.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-143">Use when there is only a property or enum change between OS versions that doesn’t require logic changes, and is connected to a visual state.</span></span>

<span data-ttu-id="3b1e9-144">Vorteile:</span><span class="sxs-lookup"><span data-stu-id="3b1e9-144">Benefits:</span></span>
- <span data-ttu-id="3b1e9-145">Ermöglicht die Erstellung spezifischer visueller Zustände, die abhängig davon ausgelöst werden, ob eine API vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-145">Lets you create specific visual states that are triggered based on the presence of an API.</span></span>
- <span data-ttu-id="3b1e9-146">Eingeschränkte Designerunterstützung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-146">Some designer support available.</span></span>

<span data-ttu-id="3b1e9-147">Nachteile:</span><span class="sxs-lookup"><span data-stu-id="3b1e9-147">Drawbacks:</span></span>
- <span data-ttu-id="3b1e9-148">Die Verwendung von benutzerdefinierten Auslösern ist auf visuelle Zustände beschränkt, weshalb sich die Option nicht für komplizierte adaptive Layouts eignet.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-148">Use of custom triggers is restricted to visual states, which doesn’t lend itself to complicated adaptive layouts.</span></span>
- <span data-ttu-id="3b1e9-149">Wertänderungen müssen mithilfe von Settern angegeben werden, sodass nur einfache Änderungen möglich sind.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-149">Must use Setters to specify value changes, so only simple changes are possible.</span></span>
- <span data-ttu-id="3b1e9-150">Die Einrichtung und Verwendung benutzerdefinierter Zustandsauslöser ist relativ aufwendig.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-150">Custom state triggers are fairly verbose to set up and use.</span></span>

## <a name="adaptive-code-examples"></a><span data-ttu-id="3b1e9-151">Beispiele für adaptiven Code</span><span class="sxs-lookup"><span data-stu-id="3b1e9-151">Adaptive code examples</span></span>

<span data-ttu-id="3b1e9-152">In diesem Abschnitt zeigen wir verschiedene Beispiele für adaptiven Code, in denen neue APIs aus der Windows10-Version1607 (Windows Insider Preview) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-152">In this section, we show several examples of adaptive code that use APIs that are new in Windows 10, version 1607 (Windows Insider Preview).</span></span>

### <a name="example-1-new-enum-value"></a><span data-ttu-id="3b1e9-153">Beispiel1: Neuer Enumerationswert</span><span class="sxs-lookup"><span data-stu-id="3b1e9-153">Example 1: New enum value</span></span>

<span data-ttu-id="3b1e9-154">In der Windows10-Version1607 wird die [InputScopeNameValue](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.input.inputscopenamevalue.aspx)-Enumeration um einen neuen Wert erweitert: **ChatWithoutEmoji**.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-154">Windows 10, version 1607 adds a new value to the [InputScopeNameValue](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.input.inputscopenamevalue.aspx) enumeration: **ChatWithoutEmoji**.</span></span> <span data-ttu-id="3b1e9-155">Dieser neue Eingabeumfang besitzt das gleiche Eingabeverhalten wie der Eingabeumfang **Chat** (Rechtschreibprüfung, AutoVervollständigen, automatische Großschreibung), wird aber einer Bildschirmtastatur ohne Emoji-Schaltfläche zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-155">This new input scope has the same input behavior as the **Chat** input scope (spellchecking, auto-complete, auto-capitalization), but it maps to a touch keyboard without an emoji button.</span></span> <span data-ttu-id="3b1e9-156">Dies ist hilfreich, wenn Sie Ihre eigene Emoji-Auswahl erstellen und die integrierte Emoji-Schaltfläche auf der Bildschirmtastatur deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-156">This is useful if you create your own emoji picker and want to disable the built-in emoji button in the touch keyboard.</span></span> 

<span data-ttu-id="3b1e9-157">Dieses Beispiel zeigt, wie Sie überprüfen, ob der **ChatWithoutEmoji**-Enumerationswert vorhanden ist, und die [InputScope](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textbox.inputscope.aspx)-Eigenschaft eines **TextBox**-Elements festlegen, falls dies der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-157">This example shows how to check if the **ChatWithoutEmoji** enum value is present and sets the [InputScope](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textbox.inputscope.aspx) property of a **TextBox** if it is.</span></span> <span data-ttu-id="3b1e9-158">Ist der Wert in dem System, auf dem die App ausgeführt wird, nicht vorhanden, wird **InputScope** stattdessen auf **Chat** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-158">If it’s not present on the system the app is run on, the **InputScope** is set to **Chat** instead.</span></span> <span data-ttu-id="3b1e9-159">Der hier gezeigte Code kann in einem Page-Konstruktor oder in einem Page.Loaded-Ereignishandler platziert werden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-159">The code shown could be placed in a Page consructor or Page.Loaded event handler.</span></span>

> [!TIP]
> <span data-ttu-id="3b1e9-160">Verlassen Sie sich beim Prüfen einer API nicht auf .NET-Sprachfeatures, sondern verwenden Sie statische Zeichenfolgen. Andernfalls versucht Ihre App unter Umständen, auf einen nicht definierten Typ zuzugreifen, was einen Absturz zur Laufzeit zur Folge hat.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-160">When you check an API, use static strings instead of relying on .NET language features, otherwise your app might try to access a type that isn’t defined and crash at runtime.</span></span>

**<span data-ttu-id="3b1e9-161">C#</span><span class="sxs-lookup"><span data-stu-id="3b1e9-161">C#</span></span>**
```csharp
// Create a TextBox control for sending messages 
// and initialize an InputScope object.
TextBox messageBox = new TextBox();
messageBox.AcceptsReturn = true;
messageBox.TextWrapping = TextWrapping.Wrap;
InputScope scope = new InputScope();
InputScopeName scopeName = new InputScopeName();

// Check that the ChatWithEmoji value is present.
// (It's present starting with Windows 10, version 1607,
//  the Target version for the app. This check returns false on earlier versions.)         
if (ApiInformation.IsEnumNamedValuePresent("Windows.UI.Xaml.Input.InputScopeNameValue", "ChatWithoutEmoji"))
{
    // Set new ChatWithoutEmoji InputScope if present.
    scopeName.NameValue = InputScopeNameValue.ChatWithoutEmoji;
}
else
{
    // Fall back to Chat InputScope.
    scopeName.NameValue = InputScopeNameValue.Chat;
}

// Set InputScope on messaging TextBox.
scope.Names.Add(scopeName);
messageBox.InputScope = scope;

// For this example, set the TextBox text to show the selected InputScope.
messageBox.Text = messageBox.InputScope.Names[0].NameValue.ToString();

// Add the TextBox to the XAML visual tree (rootGrid is defined in XAML).
rootGrid.Children.Add(messageBox);
```

<span data-ttu-id="3b1e9-162">Im vorherigen Beispiel wird das TextBox-Element erstellt, und alle Eigenschaften werden im Code festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-162">In the previous example, the TextBox is created and all properties are set in code.</span></span> <span data-ttu-id="3b1e9-163">Wenn Sie allerdings bereits über XAML verfügen und lediglich die InputScope-Eigenschaft für Systeme ändern möchten, auf denen der neue Wert unterstützt wird, können Sie dies wie hier zu sehen ohne XAML-Änderung implementieren.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-163">However, if you have existing XAML, and just need to change the InputScope property on systems where the new value is supported, you can do that without changing your XAML, as shown here.</span></span> <span data-ttu-id="3b1e9-164">Der Standardwert wird in XAML auf **Chat** festgelegt und im Code überschrieben, falls der **ChatWithoutEmoji**-Wert vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-164">You set the default value to **Chat** in XAML, but you override it in code if the **ChatWithoutEmoji** value is present.</span></span>

**<span data-ttu-id="3b1e9-165">XAML</span><span class="sxs-lookup"><span data-stu-id="3b1e9-165">XAML</span></span>**
```xaml
<TextBox x:Name="messageBox"
         AcceptsReturn="True" TextWrapping="Wrap"
         InputScope="Chat"
         Loaded="messageBox_Loaded"/>
```

**<span data-ttu-id="3b1e9-166">C#</span><span class="sxs-lookup"><span data-stu-id="3b1e9-166">C#</span></span>**
```csharp
private void messageBox_Loaded(object sender, RoutedEventArgs e)
{
    if (ApiInformation.IsEnumNamedValuePresent("Windows.UI.Xaml.Input.InputScopeNameValue", "ChatWithoutEmoji"))
    {
        // Check that the ChatWithEmoji value is present.
        // (It's present starting with Windows 10, version 1607,
        //  the Target version for the app. This code is skipped on earlier versions.)
        InputScope scope = new InputScope();
        InputScopeName scopeName = new InputScopeName();
        scopeName.NameValue = InputScopeNameValue.ChatWithoutEmoji;
        // Set InputScope on messaging TextBox.
        scope.Names.Add(scopeName);
        messageBox.InputScope = scope;
    }

    // For this example, set the TextBox text to show the selected InputScope.
    // This is outside of the API check, so it will happen on all OS versions.
    messageBox.Text = messageBox.InputScope.Names[0].NameValue.ToString();
}
```

<span data-ttu-id="3b1e9-167">Nachdem wir nun über ein konkretes Beispiel verfügen, sehen wir uns einmal an, wie in diesem Fall die Einstellungen für Mindest- und Zielversion angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-167">Now that we have a concrete example, let’s see how the Target and Minimum version settings apply to it.</span></span>

<span data-ttu-id="3b1e9-168">In diesen Beispielen können Sie den Chat-Enumerationswert in XAML oder in Code ohne Überprüfung verwenden, da der Wert in der unterstützten Mindestversion des Betriebssystems vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-168">In these examples, you can use the Chat enum value in XAML, or in code without a check, because it’s present in the minimum supported OS version.</span></span> 

<span data-ttu-id="3b1e9-169">Wenn Sie den ChatWithoutEmoji-Wert in XAML oder in Code ohne Überprüfung verwenden, wird er ohne Fehler kompiliert, da der Wert in der Zielversion des Betriebssystems vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-169">If you use the ChatWithoutEmoji value in XAML, or in code without a check, it will compile without error because it's present in the Target OS version.</span></span> <span data-ttu-id="3b1e9-170">Auch die Ausführung auf einem System mit der Zielversion des Betriebssystems ist ohne Fehler möglich.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-170">It will also run without error on a system with the Target OS version.</span></span> <span data-ttu-id="3b1e9-171">Wenn die App allerdings auf einem System mit der Mindestversion des Betriebssystems ausgeführt wird, stürzt sie zur Laufzeit ab, da der ChatWithoutEmoji-Enumerationswert nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-171">However, when the app runs on a system with an OS using the Minimum version, it will crash at runtime because the ChatWithoutEmoji enum value is not present.</span></span> <span data-ttu-id="3b1e9-172">Daher dürfen Sie diesen Wert nur in Code verwenden und müssen ihn mit einer API-Laufzeitprüfung umschließen, sodass er nur aufgerufen wird, wenn dies auf dem aktuellen System unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-172">Therefore, you must use this value only in code, and wrap it in a runtime API check so it’s called only if it’s supported on the current system.</span></span>

### <a name="example-2-new-control"></a><span data-ttu-id="3b1e9-173">Beispiel2: Neues Steuerelement</span><span class="sxs-lookup"><span data-stu-id="3b1e9-173">Example 2: New control</span></span>

<span data-ttu-id="3b1e9-174">Eine neue Version von Windows verfügt üblicherweise über neue Steuerelemente für die UWP-API-Oberfläche, die den Funktionsumfang der Plattform erweitern.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-174">A new version of Windows typically brings new controls to the UWP API surface that bring new functionality to the platform.</span></span> <span data-ttu-id="3b1e9-175">Das Vorhandensein eines neuen Steuerelements kann mithilfe der [ApiInformation.IsTypePresent](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.apiinformation.istypepresent.aspx)-Methode ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-175">To leverage the presence of a new control, use the  [ApiInformation.IsTypePresent](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.apiinformation.istypepresent.aspx) method.</span></span>

<span data-ttu-id="3b1e9-176">In der Windows10-Version1607 wird ein neues Mediensteuerelement namens [**MediaPlayerElement**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) eingeführt.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-176">Windows 10, version 1607 introduces a new media control called [**MediaPlayerElement**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx).</span></span> <span data-ttu-id="3b1e9-177">Dieses Steuerelement basiert auf der [MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.aspx)-Klasse, stellt beispielweise Features wie die problemlose Einbindung von Hintergrundaudio bereit und profitiert von Verbesserungen bei der Architektur des Medienstapels.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-177">This control builds on the [MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.aspx) class, so it brings features like the ability to easily tie into background audio, and it makes use of architectural improvements in the media stack.</span></span>

<span data-ttu-id="3b1e9-178">Wenn die App allerdings auf einem Gerät mit einer älteren Windows10-Version als1607 ausgeführt wird, muss anstelle des neuen **MediaPlayerElement**-Steuerelements das [**MediaElement**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaelement.aspx)-Steuerelement verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-178">However, if the app runs on a device that’s running a version of Windows 10 older than version 1607, you must use the [**MediaElement**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaelement.aspx) control instead of the new **MediaPlayerElement** control.</span></span> <span data-ttu-id="3b1e9-179">Sie können mithilfe der [**ApiInformation.IsTypePresent**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.apiinformation.istypepresent.aspx)-Methode zur Laufzeit überprüfen, ob das MediaPlayerElement-Steuerelement vorhanden ist, und dann das geeignete Steuerelement für das System laden, auf dem die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-179">You can use the [**ApiInformation.IsTypePresent**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.apiinformation.istypepresent.aspx) method to check for the presence of the MediaPlayerElement control at runtime, and load whichever control is suitable for the system where the app is running.</span></span>

<span data-ttu-id="3b1e9-180">Dieses Beispiel zeigt, wie Sie eine App erstellen, die abhängig davon, ob der MediaPlayerElement-Typ vorhanden ist, entweder das neue MediaPlayerElement-Steuerelement oder das alte MediaElement-Steuerelement verwendet.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-180">This example shows how to create an app that uses either the new MediaPlayerElement or the old MediaElement depending on whether MediaPlayerElement type is present.</span></span> <span data-ttu-id="3b1e9-181">In diesem Code werden die Steuerelemente samt dazugehöriger Benutzeroberfläche und entsprechendem Code mithilfe der [UserControl](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.usercontrol.aspx)-Klasse in Komponenten zerlegt, sodass sie abhängig von der Betriebssystemversion einbezogen werden können.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-181">In this code, you use the [UserControl](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.usercontrol.aspx) class to componentize the controls and their related UI and code so that you can switch them in and out based on the OS version.</span></span> <span data-ttu-id="3b1e9-182">Alternativ können Sie ein benutzerdefiniertes Steuerelement verwendet. Dieses bietet mehr Funktionen und benutzerdefiniertes Verhalten als in diesem einfachen Beispiel erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-182">As an alternative, you can use a custom control, which provides more functionality and custom behavior than what’s needed for this simple example.</span></span>
 
**<span data-ttu-id="3b1e9-183">MediaPlayerUserControl</span><span class="sxs-lookup"><span data-stu-id="3b1e9-183">MediaPlayerUserControl</span></span>** 

<span data-ttu-id="3b1e9-184">`MediaPlayerUserControl` kapselt ein **MediaPlayerElement** und mehrere Schaltflächen für eine framebasierte Mediennavigation.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-184">The `MediaPlayerUserControl` encapsulates a **MediaPlayerElement** and several buttons that are used to skip through the media frame by frame.</span></span> <span data-ttu-id="3b1e9-185">„UserControl“ ermöglicht die Behandlung dieser Steuerelemente als einzelne Entität und erleichtert den Wechsel zu „MediaElement“ bei älteren Systemen.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-185">The UserControl lets you treat these controls as a single entity and makes it easier to switch with a MediaElement on older systems.</span></span> <span data-ttu-id="3b1e9-186">Dieses Benutzersteuerelement sollte nur für Systeme verwendet werden, die über „MediaPlayerElement“ verfügen, sodass im Code innerhalb dieses Benutzersteuerelements keine ApiInformation-Prüfungen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-186">This user control should be used only on systems where MediaPlayerElement is present, so you don’t use ApiInformation checks in the code inside this user control.</span></span>

> [!NOTE]
> <span data-ttu-id="3b1e9-187">Die Schaltflächen für die Frameschritte werden außerhalb des Medienplayers platziert, um dieses Beispiel möglichst einfach und prägnant zu halten.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-187">To keep this example simple and focused, the frame step buttons are placed outside of the media player.</span></span> <span data-ttu-id="3b1e9-188">Zur Verbesserung der Benutzerfreundlichkeit sollten Sie „MediaTransportControls“ mit Ihren benutzerdefinierten Schaltflächen anpassen.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-188">For a better user experiance, you should customize the MediaTransportControls to include your custom buttons.</span></span> <span data-ttu-id="3b1e9-189">Weitere Informationen finden Sie unter [Benutzerdefinierte Transportsteuerelemente](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/custom-transport-controls).</span><span class="sxs-lookup"><span data-stu-id="3b1e9-189">See [Custom transport controls](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/custom-transport-controls) for more info.</span></span> 

**<span data-ttu-id="3b1e9-190">XAML</span><span class="sxs-lookup"><span data-stu-id="3b1e9-190">XAML</span></span>**
```xaml
<UserControl
    x:Class="MediaApp.MediaPlayerUserControl"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:MediaApp"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    d:DesignHeight="300"
    d:DesignWidth="400">

    <Grid x:Name="MPE_grid>
        <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition Height="Auto"/>
        </Grid.RowDefinitions>
        <StackPanel Orientation="Horizontal" 
                    HorizontalAlignment="Center" Grid.Row="1">
            <RepeatButton Click="StepBack_Click" Content="Step Back"/>
            <RepeatButton Click="StepForward_Click" Content="Step Forward"/>
        </StackPanel>
    </Grid>
</UserControl>
```

**<span data-ttu-id="3b1e9-191">C#</span><span class="sxs-lookup"><span data-stu-id="3b1e9-191">C#</span></span>**
```csharp
using System;
using Windows.Media.Core;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;

namespace MediaApp
{
    public sealed partial class MediaPlayerUserControl : UserControl
    {
        public MediaPlayerUserControl()
        {
            this.InitializeComponent();
            
            // The markup code compiler runs against the Minimum OS version so MediaPlayerElement must be created in app code
            MPE = new MediaPlayerElement();
            Uri videoSource = new Uri("ms-appx:///Assets/UWPDesign.mp4");
            MPE.Source = MediaSource.CreateFromUri(videoSource);
            MPE.AreTransportControlsEnabled = true;
            MPE.MediaPlayer.AutoPlay = true;

            // Add MediaPlayerElement to the Grid
            MPE_grid.Children.Add(MPE);

        }

        private void StepForward_Click(object sender, RoutedEventArgs e)
        {
            // Step forward one frame, only available using MediaPlayerElement.
            MPE.MediaPlayer.StepForwardOneFrame();
        }

        private void StepBack_Click(object sender, RoutedEventArgs e)
        {
            // Step forward one frame, only available using MediaPlayerElement.
            MPE.MediaPlayer.StepForwardOneFrame();
        }
    }
}
```

**<span data-ttu-id="3b1e9-192">MediaElementUserControl</span><span class="sxs-lookup"><span data-stu-id="3b1e9-192">MediaElementUserControl</span></span>**
 
<span data-ttu-id="3b1e9-193">`MediaElementUserControl` kapselt ein **MediaElement**-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-193">The `MediaElementUserControl` encapsulates a **MediaElement** control.</span></span>

**<span data-ttu-id="3b1e9-194">XAML</span><span class="sxs-lookup"><span data-stu-id="3b1e9-194">XAML</span></span>**
```xaml
<UserControl
    x:Class="MediaApp.MediaElementUserControl"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:MediaApp"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    d:DesignHeight="300"
    d:DesignWidth="400">

    <Grid>
        <MediaElement AreTransportControlsEnabled="True" 
                      Source="Assets/UWPDesign.mp4"/>
    </Grid>
</UserControl>
```

> [!NOTE]
> <span data-ttu-id="3b1e9-195">Die Codepage für `MediaElementUserControl` enthält nur generierten Code und wird daher nicht gezeigt.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-195">The code page for `MediaElementUserControl` contains only generated code, so it's not shown.</span></span>

**<span data-ttu-id="3b1e9-196">Initialisieren eines Steuerelements auf der Grundlage von „IsTypePresent“</span><span class="sxs-lookup"><span data-stu-id="3b1e9-196">Initialize a control based on IsTypePresent</span></span>**

<span data-ttu-id="3b1e9-197">Rufen Sie zur Laufzeit **ApiInformation.IsTypePresent** auf, um zu prüfen, ob „MediaPlayerElement“ vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-197">At runtime, you call **ApiInformation.IsTypePresent** to check for MediaPlayerElement.</span></span> <span data-ttu-id="3b1e9-198">Wenn vorhanden, laden Sie `MediaPlayerUserControl`, andernfalls laden Sie `MediaElementUserControl`.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-198">If it's present, you load `MediaPlayerUserControl`, if it's not, you load `MediaElementUserControl`.</span></span>

**<span data-ttu-id="3b1e9-199">C#</span><span class="sxs-lookup"><span data-stu-id="3b1e9-199">C#</span></span>**
```csharp
public MainPage()
{
    this.InitializeComponent();

    UserControl mediaControl;

    // Check for presence of type MediaPlayerElement.
    if (ApiInformation.IsTypePresent("Windows.UI.Xaml.Controls.MediaPlayerElement"))
    {
        mediaControl = new MediaPlayerUserControl();
    }
    else
    {
        mediaControl = new MediaElementUserControl();
    }

    // Add mediaControl to XAML visual tree (rootGrid is defined in XAML).
    rootGrid.Children.Add(mediaControl);
}
```

> [!IMPORTANT]
> <span data-ttu-id="3b1e9-200">Zur Erinnerung: Diese Überprüfung legt nur das `mediaControl`-Objekt auf `MediaPlayerUserControl` oder `MediaElementUserControl` fest.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-200">Remember that this check only sets the `mediaControl` object to either `MediaPlayerUserControl` or `MediaElementUserControl`.</span></span> <span data-ttu-id="3b1e9-201">Diese bedingten Überprüfungen müssen überall im Code durchgeführt werden, wo Sie ermitteln müssen, ob die MediaPlayerElement- oder die MediaElement-API verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-201">You need to perform these conditional checks anywhere else in your code that you need to determine whether to use MediaPlayerElement or MediaElement APIs.</span></span> <span data-ttu-id="3b1e9-202">Es empfiehlt sich, die Prüfung nur einmal durchzuführen, das Ergebnis zwischenzuspeichern und es anschließend in der gesamten App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-202">You should perform the check once and cache the result, then used the cached result throughout your app.</span></span>

## <a name="state-trigger-examples"></a><span data-ttu-id="3b1e9-203">Beispiele für Zustandsauslöser</span><span class="sxs-lookup"><span data-stu-id="3b1e9-203">State trigger examples</span></span>

<span data-ttu-id="3b1e9-204">Mithilfe erweiterbarer Zustandsauslöser können Sie Markup und Code zusammen verwenden, um Änderungen des visuellen Zustands auf der Grundlage einer im Code überprüften Bedingung auszulösen (in diesem Fall: das Vorhandensein einer bestimmten API).</span><span class="sxs-lookup"><span data-stu-id="3b1e9-204">Extensible state triggers let you use markup and code together to trigger visual state changes based on a condition that you check in code; in this case, the presence of a specific API.</span></span> <span data-ttu-id="3b1e9-205">In allgemeinen Szenarien mit adaptivem Code wird die Verwendung von Zustandsauslösern aufgrund des zusätzlichen Aufwands und der Beschränkung auf visuelle Zustände nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-205">We don’t recommend state triggers for common adaptive code scenarios because of the overhead involved, and the restriction to only visual states.</span></span> 

<span data-ttu-id="3b1e9-206">Verwenden Sie Zustandsauslöser nur dann für adaptiven Code, wenn lediglich geringfügige Benutzeroberflächenänderungen zwischen Betriebssystemversionen vorliegen, die sich nicht auf die restliche Benutzeroberfläche auswirken (etwa die Änderung einer Eigenschaft oder eines Enumerationswerts für ein Steuerelement).</span><span class="sxs-lookup"><span data-stu-id="3b1e9-206">You should use state triggers for adaptive code only when you have small UI changes between different OS versions that won’t impact the remaining UI, such as a property or enum value change on a control.</span></span>

### <a name="example-1-new-property"></a><span data-ttu-id="3b1e9-207">Beispiel1: Neue Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3b1e9-207">Example 1: New property</span></span>

<span data-ttu-id="3b1e9-208">Der erste Schritt bei der Einrichtung eines erweiterbaren Zustandsauslösers besteht in der Verwendung von Unterklassen für die [StateTriggerBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.statetriggerbase.aspx)-Klasse zur Erstellung eines benutzerdefinierten Auslösers, dessen Aktivierung davon abhängt, ob eine API vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-208">The first step in setting up an extensible state trigger is subclassing the [StateTriggerBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.statetriggerbase.aspx) class to create a custom trigger that will be active based on the presence of an API.</span></span> <span data-ttu-id="3b1e9-209">Dieses Beispiel zeigt einen Auslöser, der aktiviert wird, wenn das Vorhandensein der Eigenschaft der in XAML festgelegten `_isPresent`-Variablen entspricht.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-209">This example shows a trigger that activates if the property presence matches the `_isPresent` variable set in XAML.</span></span>

**<span data-ttu-id="3b1e9-210">C#</span><span class="sxs-lookup"><span data-stu-id="3b1e9-210">C#</span></span>**
```csharp
class IsPropertyPresentTrigger : StateTriggerBase
{
    public string TypeName { get; set; }
    public string PropertyName { get; set; }

    private Boolean _isPresent;
    private bool? _isPropertyPresent = null;

    public Boolean IsPresent
    {
        get { return _isPresent; }
        set
        {
            _isPresent = value;
            if (_isPropertyPresent == null)
            {
                // Call into ApiInformation method to determine if property is present.
                _isPropertyPresent =
                ApiInformation.IsPropertyPresent(TypeName, PropertyName);
            }

            // If the property presence matches _isPresent then the trigger will be activated;
            SetActive(_isPresent == _isPropertyPresent);
        }
    }
}
```

<span data-ttu-id="3b1e9-211">Im nächsten Schritt wird der visuelle Zustandsauslöser in XAML eingerichtet, um abhängig vom Vorhandensein der API zwei unterschiedliche visuelle Zustände zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-211">The next step is setting up the visual state trigger in XAML so that two different visual states result based on the presence of the API.</span></span> 

<span data-ttu-id="3b1e9-212">In der Windows10-Version1607 wird für die [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.aspx)-Klasse eine neue Eigenschaft namens [AllowFocusOnInteraction](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.allowfocusoninteraction.aspx) eingeführt, die bestimmt, ob ein Steuerelement den Fokus erhält, wenn ein Benutzer damit interagiert.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-212">Windows 10, version 1607 introduces a new property on the [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.aspx) class called [AllowFocusOnInteraction](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.allowfocusoninteraction.aspx) that determines whether a control takes focus when  a user interacts with it.</span></span> <span data-ttu-id="3b1e9-213">Dies ist hilfreich, falls ein Textfeld für die Dateneingabe den Fokus behalten (und die Bildschirmtastatur weiter angezeigt werden) soll, wenn der Benutzer auf eine Schaltfläche klickt.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-213">This is useful if you want to keep focus on a text box for data entry (and keep the touch keyboard showing) while the user clicks a button.</span></span>

<span data-ttu-id="3b1e9-214">Der Auslöser in diesem Beispiel überprüft, ob die Eigenschaft vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-214">The trigger in this example checks if the property is present.</span></span> <span data-ttu-id="3b1e9-215">Ist die Eigenschaft vorhanden, wird die **AllowFocusOnInteraction**-Eigenschaft für eine Schaltfläche auf **False** festgelegt. Ist die Eigenschaft nicht vorhanden, wird der ursprüngliche Zustand der Schaltfläche beibehalten.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-215">If the property is present it sets the **AllowFocusOnInteraction** property on a Button to **false**; if the property isn’t present, the Button retains its original state.</span></span> <span data-ttu-id="3b1e9-216">Das TextBox-Element dient zur Veranschaulichung der Auswirkung dieser Eigenschaft, wenn Sie den Code ausführen.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-216">The TextBox is included to make it easier to see the effect of this property when you run the code.</span></span>

**<span data-ttu-id="3b1e9-217">XAML</span><span class="sxs-lookup"><span data-stu-id="3b1e9-217">XAML</span></span>**
```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <StackPanel>
        <TextBox Width="300" Height="36"/>
        <!-- Button to set the new property on. -->
        <Button x:Name="testButton" Content="Test" Margin="12"/>
    </StackPanel>

    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup x:Name="propertyPresentStateGroup">
            <VisualState>
                <VisualState.StateTriggers>
                    <!--Trigger will activate if the AllowFocusOnInteraction property is present-->
                    <local:IsPropertyPresentTrigger 
                        TypeName="Windows.UI.Xaml.FrameworkElement" 
                        PropertyName="AllowFocusOnInteraction" IsPresent="True"/>
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Target="testButton.AllowFocusOnInteraction" 
                            Value="False"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
</Grid>
```

### <a name="example-2-new-enum-value"></a><span data-ttu-id="3b1e9-218">Beispiel2: Neuer Enumerationswert</span><span class="sxs-lookup"><span data-stu-id="3b1e9-218">Example 2: New enum value</span></span>

<span data-ttu-id="3b1e9-219">Dieses Beispiel zeigt, wie Sie abhängig davon, ob ein Wert vorhanden ist, unterschiedliche Enumerationswerte festlegen.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-219">This example shows how to set different enumeration values based on whether a value is present.</span></span> <span data-ttu-id="3b1e9-220">Hierbei kommt ein benutzerdefinierter Zustandsauslöser zum Einsatz, um das gleiche Ergebnis zu erhalten wie im vorherigen Chatbeispiel.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-220">It uses a custom state trigger to achieve the same result as the previous chat example.</span></span> <span data-ttu-id="3b1e9-221">In diesem Beispiel wird der neue ChatWithoutEmoji-Eingabeumfang verwendet, wenn auf dem Gerät die Windows10-Version1607 ausgeführt wird. Andernfalls wird der Eingabeumfang **Chat** verwendet.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-221">In this example, you use the new ChatWithoutEmoji input scope if the device is running Windows 10, version 1607, otherwise the **Chat** input scope is used.</span></span> <span data-ttu-id="3b1e9-222">Die visuellen Zustände, die diesen Auslöser verwenden, werden im *if-else*-Stil eingerichtet, wobei die Wahl des Eingabeumfangs davon abhängt, ob der neue Enumerationswert vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3b1e9-222">The visual states that use this trigger are set up in an *if-else* style where the input scope is chosen based on the presence of the new enum value.</span></span>

**<span data-ttu-id="3b1e9-223">C#</span><span class="sxs-lookup"><span data-stu-id="3b1e9-223">C#</span></span>**
```csharp
class IsEnumPresentTrigger : StateTriggerBase
{
    public string EnumTypeName { get; set; }
    public string EnumValueName { get; set; }

    private Boolean _isPresent;
    private bool? _isEnumValuePresent = null;

    public Boolean IsPresent
    {
        get { return _isPresent; }
        set
        {
            _isPresent = value;

            if (_isEnumValuePresent == null)
            {
                // Call into ApiInformation method to determine if value is present.
                _isEnumValuePresent =
                ApiInformation.IsEnumNamedValuePresent(EnumTypeName, EnumValueName);
            }

            // If the property presence matches _isPresent then the trigger will be activated;
            SetActive(_isPresent == _isEnumValuePresent);
        }
    }
}
```

**<span data-ttu-id="3b1e9-224">XAML</span><span class="sxs-lookup"><span data-stu-id="3b1e9-224">XAML</span></span>**
```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <TextBox x:Name="messageBox"
     AcceptsReturn="True" TextWrapping="Wrap"/>


    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup x:Name="EnumPresentStates">
            <!--if-->
            <VisualState x:Name="isPresent">
                <VisualState.StateTriggers>
                    <local:IsEnumPresentTrigger 
                        EnumTypeName="Windows.UI.Xaml.Input.InputScopeNameValue" 
                        EnumValueName="ChatWithoutEmoji" IsPresent="True"/>
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Target="messageBox.InputScope" Value="ChatWithoutEmoji"/>
                </VisualState.Setters>
            </VisualState>
            <!--else-->
            <VisualState x:Name="isNotPresent">
                <VisualState.StateTriggers>
                    <local:IsEnumPresentTrigger 
                        EnumTypeName="Windows.UI.Xaml.Input.InputScopeNameValue" 
                        EnumValueName="ChatWithoutEmoji" IsPresent="False"/>
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Target="messageBox.InputScope" Value="Chat"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
</Grid>
```

## <a name="related-articles"></a><span data-ttu-id="3b1e9-225">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="3b1e9-225">Related articles</span></span>

- [<span data-ttu-id="3b1e9-226">Übersicht über die Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="3b1e9-226">Device families overview</span></span>](https://docs.microsoft.com/uwp/extension-sdks/device-families-overview)
- [<span data-ttu-id="3b1e9-227">Dynamically detecting features with API contracts (Dynamisches Erkennen von Features mithilfe von API-Verträgen)</span><span class="sxs-lookup"><span data-stu-id="3b1e9-227">Dynamically detecting features with API contracts</span></span>](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/)
