---
author: DelfCo
Description: "Nehmen Sie Zeichenfolgenressourcen für Ihre Benutzeroberfläche in Ressourcendateien auf. Sie können anschließend im Code oder Markup auf diese Zeichenfolgen verweisen."
title: Aufnehmen von UI-Zeichenfolgen in Ressourcen
ms.assetid: E420B9BB-C0F6-4EC0-BA3A-BA2875B69722
label: Put UI strings into resources
template: detail.hbs
ms.author: bobdel
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: a3e224fc51245a5f91c29da2d745a3740029cda9
ms.sourcegitcommit: 11664964e548a2af30d6e176c515cdbf330934ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2017
---
# <a name="put-ui-strings-into-resources"></a><span data-ttu-id="f290b-105">Aufnehmen von UI-Zeichenfolgen in Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f290b-105">Put UI strings into resources</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="f290b-106">Nehmen Sie Zeichenfolgenressourcen für Ihre Benutzeroberfläche in Ressourcendateien auf.</span><span class="sxs-lookup"><span data-stu-id="f290b-106">Put string resources for your UI into resource files.</span></span> <span data-ttu-id="f290b-107">Sie können anschließend im Code oder Markup auf diese Zeichenfolgen verweisen.</span><span class="sxs-lookup"><span data-stu-id="f290b-107">You can then reference those strings from your code or markup.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="f290b-108">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="f290b-108">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="f290b-109">ApplicationModel.Resources.ResourceLoader</span><span class="sxs-lookup"><span data-stu-id="f290b-109">ApplicationModel.Resources.ResourceLoader</span></span>**](https://msdn.microsoft.com/library/windows/apps/br206014)</li>
<li>[**<span data-ttu-id="f290b-110">WinJS.Resources.processAll</span><span class="sxs-lookup"><span data-stu-id="f290b-110">WinJS.Resources.processAll</span></span>**](https://msdn.microsoft.com/library/windows/apps/br211864)</li>
</ul>
</div>


<span data-ttu-id="f290b-111">In diesem Thema wird gezeigt, welche Schritte Sie ausführen müssen, um Ihrer universellen Windows-App Zeichenfolgenressourcen für mehrere Sprachen hinzuzufügen und die App kurz zu testen.</span><span class="sxs-lookup"><span data-stu-id="f290b-111">This topic shows the steps to add several language string resources to your Universal Windows app, and how to briefly test it.</span></span>

## <a name="put-strings-into-resource-files-instead-of-putting-them-directly-in-code-or-markup"></a><span data-ttu-id="f290b-112">Platzieren Sie Zeichenfolgen in Ressourcendateien und nicht direkt im Code oder Markup.</span><span class="sxs-lookup"><span data-stu-id="f290b-112">Put strings into resource files, instead of putting them directly in code or markup.</span></span>


1.  <span data-ttu-id="f290b-113">Öffnen Sie Ihre Projektmappe in Visual Studio (oder erstellen Sie eine neue).</span><span class="sxs-lookup"><span data-stu-id="f290b-113">Open your solution (or create a new one) in Visual Studio.</span></span>

2.  <span data-ttu-id="f290b-114">Öffnen Sie in Visual Studio „package.appxmanifest“, rufen Sie die Registerkarte **Anwendung** auf, und legen Sie (in diesem Beispiel) die Standardsprache auf „en-US“ fest.</span><span class="sxs-lookup"><span data-stu-id="f290b-114">Open package.appxmanifest in Visual Studio, go to the **Application** tab, and (for this example) set the Default language to "en-US".</span></span> <span data-ttu-id="f290b-115">Wenn Ihre Projektmappe mehrere Dateien namens „package.appxmanifest“ enthält, führen Sie die Schritte für jede Datei aus.</span><span class="sxs-lookup"><span data-stu-id="f290b-115">If there are multiple package.appxmanifest files in your solution, do this for each one.</span></span>
    <br><span data-ttu-id="f290b-116">**Hinweis**  Damit haben Sie die Standardsprache für das Projekt festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f290b-116">**Note**  This specifies the default language for the project.</span></span> <span data-ttu-id="f290b-117">Die Standardsprachressourcen werden verwendet, wenn die bevorzugte Sprache des Benutzers oder die Anzeigesprachen nicht mit den von der Anwendung bereitgestellten Sprachressourcen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="f290b-117">The default language resources are used if the user's preferred language or display languages do not match the language resources provided in the application.</span></span>
3.  <span data-ttu-id="f290b-118">Erstellen Sie einen Ordner, um dort die Ressourcendateien zu speichern.</span><span class="sxs-lookup"><span data-stu-id="f290b-118">Create a folder to contain the resource files.</span></span>
    1.  <span data-ttu-id="f290b-119">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt (das freigegebene Projekt, falls die Projektmappe mehrere Projekte enthält), und wählen Sie **Hinzufügen** &gt; **Neuer Ordner** aus.</span><span class="sxs-lookup"><span data-stu-id="f290b-119">In the Solution Explorer, right-click the project (the Shared project if your solution contains multiple projects) and select **Add** &gt; **New Folder**.</span></span>
    2.  <span data-ttu-id="f290b-120">Geben Sie dem neuen Ordner den Namen „Strings“.</span><span class="sxs-lookup"><span data-stu-id="f290b-120">Name the new folder "Strings".</span></span>
    3.  <span data-ttu-id="f290b-121">Wenn der neue Ordner nicht im Projektmappen-Explorer sichtbar ist, wählen Sie im Microsoft Visual Studio-Menü **Projekt** &gt; **Alle Dateien anzeigen** aus, während das Projekt noch ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="f290b-121">If the new folder is not visible in Solution Explorer, select **Project** &gt; **Show All Files** from the Microsoft Visual Studio menu while the project is still selected.</span></span>

4.  <span data-ttu-id="f290b-122">Erstellen Sie einen Unterordner und eine Ressourcendatei für Englisch (USA).</span><span class="sxs-lookup"><span data-stu-id="f290b-122">Create a sub-folder and a resource file for English (United States).</span></span>
    1.  <span data-ttu-id="f290b-123">Klicken Sie mit der rechten Maustaste auf den Ordner „Strings“, und fügen Sie darunter einen neuen Ordner hinzu.</span><span class="sxs-lookup"><span data-stu-id="f290b-123">Right-click the Strings folder and add a new folder beneath it.</span></span> <span data-ttu-id="f290b-124">Geben Sie ihm den Namen „en-US“.</span><span class="sxs-lookup"><span data-stu-id="f290b-124">Name it "en-US".</span></span> <span data-ttu-id="f290b-125">Die Ressourcendatei muss in einem Ordner mit dem Sprachtag [BCP-47](http://go.microsoft.com/fwlink/p/?linkid=227302) abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f290b-125">The resource file is to be placed in a folder that has been named for the [BCP-47](http://go.microsoft.com/fwlink/p/?linkid=227302) language tag.</span></span> <span data-ttu-id="f290b-126">Details zum Sprachqualifizierer und eine Liste häufiger Sprachtags finden Sie unter [Benennen von Ressourcen mit Qualifizierern](https://msdn.microsoft.com/library/windows/apps/xaml/hh965324).</span><span class="sxs-lookup"><span data-stu-id="f290b-126">See [How to name resources using qualifiers](https://msdn.microsoft.com/library/windows/apps/xaml/hh965324) for details on the language qualifier and a list of common language tags.</span></span>
    2.  <span data-ttu-id="f290b-127">Klicken Sie mit der rechten Maustaste auf den Ordner „en-US“, und wählen Sie **Hinzufügen** &gt; **Neues Element...** aus.</span><span class="sxs-lookup"><span data-stu-id="f290b-127">Right-click the en-US folder and select **Add** &gt; **New Item…**.</span></span>
    3.  <span data-ttu-id="f290b-128">Wählen Sie „Ressourcendatei (.resw)“ aus.</span><span class="sxs-lookup"><span data-stu-id="f290b-128">Select "Resources File (.resw)".</span></span>

    4.  <span data-ttu-id="f290b-129">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="f290b-129">Click **Add**.</span></span> <span data-ttu-id="f290b-130">Hierdurch wird eine Ressourcendatei mit dem Standardnamen „Resources.resw“ hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f290b-130">This adds a resource file with the default name "Resources.resw".</span></span> <span data-ttu-id="f290b-131">Es wird empfohlen, diesen Standarddateinamen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f290b-131">We recommend that you use this default filename.</span></span> <span data-ttu-id="f290b-132">Apps können ihre Ressourcen in andere Dateien partitionieren. Sie müssen jedoch darauf achten, richtig auf die Dateien zu verweisen (siehe [Laden von Zeichenfolgenressourcen](https://msdn.microsoft.com/library/windows/apps/xaml/hh965323)).</span><span class="sxs-lookup"><span data-stu-id="f290b-132">Apps can partition their resources into other files, but you must be careful to refer to them correctly (see [How to load string resources](https://msdn.microsoft.com/library/windows/apps/xaml/hh965323)).</span></span>
    5.  <span data-ttu-id="f290b-133">Wenn Sie ausschließlich RESX-Dateien mit Zeichenfolgenressourcen aus vorherigen .NET-Projekten verwenden, wählen Sie **Hinzufügen** &gt; **Vorhandenes Element** aus, fügen die RESX-Datei hinzu und benennen sie in .resw um.</span><span class="sxs-lookup"><span data-stu-id="f290b-133">If you have .resx files with only string resources from previous .NET projects, select **Add** &gt; **Existing Item…**, add the .resx file, and rename it to .resw.</span></span>
    6.  <span data-ttu-id="f290b-134">Öffnen Sie die Datei, und fügen Sie im Editor die folgenden Ressourcen hinzu:</span><span class="sxs-lookup"><span data-stu-id="f290b-134">Open the file and use the editor to add these resources:</span></span>


        <span data-ttu-id="f290b-135">Strings/en-US/Resources.resw ![Ressource hinzufügen, Englisch](images/addresource-en-us.png) In diesem Beispiel identifizieren „Greeting.Text“ und „Farewell“ die Zeichenfolgen, die angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f290b-135">Strings/en-US/Resources.resw ![add resource, english](images/addresource-en-us.png) In this example, "Greeting.Text" and "Farewell" identify the strings that are to be displayed.</span></span> <span data-ttu-id="f290b-136">„Greeting.Width“ identifiziert die „Width“-Eigenschaft der „Greeting“-Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="f290b-136">"Greeting.Width" identifies the Width property of the "Greeting" string.</span></span> <span data-ttu-id="f290b-137">Kommentare sind gut geeignet, um spezielle Anweisungen für Übersetzer bereitzustellen, die die Zeichenfolgen in andere Sprachen lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="f290b-137">The comments are a good place to provide any special instructions to translators who localize the strings to other languages.</span></span>

## <a name="associate-controls-to-resources"></a><span data-ttu-id="f290b-138">Ordnen Sie Steuerelemente zu Ressourcen zu.</span><span class="sxs-lookup"><span data-stu-id="f290b-138">Associate controls to resources.</span></span>

<span data-ttu-id="f290b-139">Sie müssen alle Steuerelemente, deren Texte lokalisiert werden müssen, mit der RESW-Datei verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="f290b-139">You need to associate every control that needs localized text with the .resw file.</span></span> <span data-ttu-id="f290b-140">Verwenden Sie dazu das **x:Uid**-Attribut in den XAML-Elementen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f290b-140">You do this using the **x:Uid** attribute on your XAML elements like this:</span></span>

```XML
<TextBlock x:Uid="Greeting" Text="" />
```

<span data-ttu-id="f290b-141">Für den Ressourcennamen geben Sie den **Uid**-Attributwert und die Eigenschaft an, die die übersetzte Zeichenfolge erhält (in diesem Fall die Eigenschaft „Text“).</span><span class="sxs-lookup"><span data-stu-id="f290b-141">For the resource name, you give the **Uid** attribute value, plus you specify what property is to get the translated string (in this case the Text property).</span></span> <span data-ttu-id="f290b-142">Sie können andere Eigenschaften/Werte für verschiedene Sprachen festlegen, z.B. "Greeting.Width". Sie sollten mit solchen layoutbezogenen Eigenschaften jedoch vorsichtig umgehen.</span><span class="sxs-lookup"><span data-stu-id="f290b-142">You can specify other properties/values for different languages such as Greeting.Width, but be careful with such layout-related properties.</span></span> <span data-ttu-id="f290b-143">Versuchen Sie stets, ein dynamisches Layout auf Grundlage des Gerätebildschirms für die Steuerelemente zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f290b-143">You should strive to allow the controls to lay out dynamically based on the device's screen.</span></span>

<span data-ttu-id="f290b-144">Beachten Sie weiterhin, dass die verknüpften Eigenschaften unterschiedlich in RESW-Dateien behandelt werden, z.B. "AutomationProperties.Name".</span><span class="sxs-lookup"><span data-stu-id="f290b-144">Note that attached properties are handled differently in resw files such as AutomationProperties.Name.</span></span> <span data-ttu-id="f290b-145">Sie müssen den Namespace explizit wie folgt ausschreiben:</span><span class="sxs-lookup"><span data-stu-id="f290b-145">You need to explicitly write out the namespace like this:</span></span>

```XML
MediumButton.[using:Windows.UI.Xaml.Automation]AutomationProperties.Name
```

## <a name="add-string-resource-identifiers-to-code-and-markup"></a><span data-ttu-id="f290b-146">Fügen Sie Code und Markup Zeichenfolgenressourcen-Bezeichner hinzu.</span><span class="sxs-lookup"><span data-stu-id="f290b-146">Add string resource identifiers to code and markup.</span></span>

<span data-ttu-id="f290b-147">Sie können im Code dynamisch auf Zeichenfolgen verweisen:</span><span class="sxs-lookup"><span data-stu-id="f290b-147">In your code, you can dynamically reference strings:</span></span>

**<span data-ttu-id="f290b-148">C#</span><span class="sxs-lookup"><span data-stu-id="f290b-148">C#</span></span>**
```CSharp
var loader = new Windows.ApplicationModel.Resources.ResourceLoader();
var str = loader.GetString("Farewell");
```

**<span data-ttu-id="f290b-149">C++</span><span class="sxs-lookup"><span data-stu-id="f290b-149">C++</span></span>**
```cpp
auto loader = ref new Windows::ApplicationModel::Resources::ResourceLoader();
auto str = loader->GetString("Farewell");
```


## <a name="add-folders-and-resource-files-for-two-additional-languages"></a><span data-ttu-id="f290b-150">Fügen Sie Ordner und Ressourcendateien für zwei zusätzliche Sprachen hinzu.</span><span class="sxs-lookup"><span data-stu-id="f290b-150">Add folders and resource files for two additional languages.</span></span>


1.  <span data-ttu-id="f290b-151">Fügen Sie unter dem Ordner „Strings“ einen weiteren Ordner für Deutsch hinzu.</span><span class="sxs-lookup"><span data-stu-id="f290b-151">Add another folder under the Strings folder for German.</span></span> <span data-ttu-id="f290b-152">Geben Sie dem Ordner den Namen „de-DE“ für Deutsch (Deutschland).</span><span class="sxs-lookup"><span data-stu-id="f290b-152">Name the folder "de-DE" for Deutsch (Deutschland).</span></span>
2.  <span data-ttu-id="f290b-153">Erstellen Sie eine weitere Ressourcendatei im Ordner „de-DE“, und fügen Sie Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="f290b-153">Create another resources file in the de-DE folder, and add the following:</span></span>

    <span data-ttu-id="f290b-154">strings/de-DE/Resources.resw</span><span class="sxs-lookup"><span data-stu-id="f290b-154">strings/de-DE/Resources.resw</span></span>

    ![Ressource hinzufügen, Deutsch](images/addresource-de-de.png)


3.  <span data-ttu-id="f290b-156">Erstellen Sie einen weiteren Ordner mit dem Namen „fr-FR“ für Französisch (Frankreich).</span><span class="sxs-lookup"><span data-stu-id="f290b-156">Create one more folder named "fr-FR", for français (France).</span></span> <span data-ttu-id="f290b-157">Erstellen Sie eine neue Ressourcendatei, und fügen Sie Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="f290b-157">Create a new resources file and add the following:</span></span>

    <span data-ttu-id="f290b-158">strings/fr-FR/Resources.resw</span><span class="sxs-lookup"><span data-stu-id="f290b-158">strings/fr-FR/Resources.resw</span></span>
    
    ![Ressource hinzufügen, Französisch](images/addresource-fr-fr.png)

## <a name="build-and-run-the-app"></a><span data-ttu-id="f290b-160">Erstellen Sie die App, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="f290b-160">Build and run the app.</span></span>


<span data-ttu-id="f290b-161">Testen Sie die App hinsichtlich der Standardanzeigesprache.</span><span class="sxs-lookup"><span data-stu-id="f290b-161">Test the app for your default display language.</span></span>

1.  <span data-ttu-id="f290b-162">Drücken Sie F5, um die App zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="f290b-162">Press F5 to build and run the app.</span></span>
2.  <span data-ttu-id="f290b-163">Wie Sie sehen, werden Begrüßung und Verabschiedung in der bevorzugten Sprache des Benutzers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f290b-163">Note that the greeting and farewell are displayed in the user's preferred language.</span></span>
3.  <span data-ttu-id="f290b-164">Beenden Sie die App.</span><span class="sxs-lookup"><span data-stu-id="f290b-164">Exit the app.</span></span>

<span data-ttu-id="f290b-165">Testen Sie die App für die anderen Sprachen.</span><span class="sxs-lookup"><span data-stu-id="f290b-165">Test the app for the other languages.</span></span>

1.  <span data-ttu-id="f290b-166">Rufen Sie **Einstellungen** auf Ihrem Gerät auf.</span><span class="sxs-lookup"><span data-stu-id="f290b-166">Bring up **Settings** on your device.</span></span>
2.  <span data-ttu-id="f290b-167">Wählen Sie **Zeit & Sprache** aus.</span><span class="sxs-lookup"><span data-stu-id="f290b-167">Select **Time & language**.</span></span>
3.  <span data-ttu-id="f290b-168">Wählen Sie **Region & Sprache** (oder auf einem Telefon oder im Phone-Emulator) **Sprache**) aus.</span><span class="sxs-lookup"><span data-stu-id="f290b-168">Select **Region & language** (or on a phone or phone emulator, **Language**).</span></span>
4.  <span data-ttu-id="f290b-169">Wie Sie sehen, wird die Sprache, die beim Ausführen der App angezeigt wurde, als erste Sprache aufgeführt, also Englisch, Deutsch oder Französisch.</span><span class="sxs-lookup"><span data-stu-id="f290b-169">Note that the language that was displayed when you ran the app is the top language listed that is English, German, or French.</span></span> <span data-ttu-id="f290b-170">Wenn die zuerst aufgeführte Sprache keine der drei genannten Sprachen ist, greift die App auf die erste Sprache in der Liste zurück, die von der App unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="f290b-170">If your top language is not one of these three, the app falls back to the next one on the list that the app supports.</span></span>
5.  <span data-ttu-id="f290b-171">Wenn nicht alle drei Sprachen auf Ihrem Computer verfügbar sind, fügen Sie die fehlenden Sprache hinzu, indem Sie auf **Sprache hinzufügen** klicken und die Sprachen dann zur Liste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f290b-171">If you do not have all three of these languages on your machine, add the missing ones by clicking **Add a language** and adding them to the list.</span></span>
6.  <span data-ttu-id="f290b-172">Um die App mit einer anderen Sprache zu testen, wählen Sie die Sprache in der Liste aus, und klicken Sie auf **Als Standard**. (Auf einem Telefon oder im Phone-Emulator wählen Sie die Sprache mit Tippen und Halten aus der Liste aus und tippen dann auf **Nach oben**, bis sie am Anfang der Liste steht.)</span><span class="sxs-lookup"><span data-stu-id="f290b-172">To test the app with another language, select the language in the list and click **Set as default** (or on a phone or phone emulator, tap and hold the language in the list and then tap **Move up** until it is at the top).</span></span> <span data-ttu-id="f290b-173">Führen Sie die App anschließend aus.</span><span class="sxs-lookup"><span data-stu-id="f290b-173">Then run the app.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f290b-174">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f290b-174">Related topics</span></span>


* [<span data-ttu-id="f290b-175">Benennen von Ressourcen mithilfe von Qualifizierern</span><span class="sxs-lookup"><span data-stu-id="f290b-175">How to name resources using qualifiers</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh965324)
* [<span data-ttu-id="f290b-176">Laden von Zeichenfolgenressourcen</span><span class="sxs-lookup"><span data-stu-id="f290b-176">How to load string resources</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh965323)
* [<span data-ttu-id="f290b-177">Das BCP-47-Sprachtag</span><span class="sxs-lookup"><span data-stu-id="f290b-177">The BCP-47 language tag</span></span>](http://go.microsoft.com/fwlink/p/?linkid=227302)
 

 



