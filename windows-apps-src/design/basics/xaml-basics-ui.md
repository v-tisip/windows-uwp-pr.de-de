---
title: Erstellen einer einfachen Benutzeroberfläche – Tutorial
description: In diesem Artikel werden die Grundlagen für Erstellen einer Benutzeroberfläche in XAML behandelt
keywords: XAML, UWP, Erste Schritte
ms.date: 08/30/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 1bae8455f1062b3ad62aeac3807c6c58ae274a1b
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7970114"
---
# <a name="tutorial-create-a-user-interface"></a><span data-ttu-id="62ccf-104">Erstellen einer einfachen Benutzeroberfläche – Tutorial</span><span class="sxs-lookup"><span data-stu-id="62ccf-104">Tutorial: Create a user interface</span></span>

<span data-ttu-id="62ccf-105">In diesem Tutorial lernen Sie, wie Sie eine grundlegende Benutzeroberfläche für ein Bildbearbeitungsprogramm erstellen:</span><span class="sxs-lookup"><span data-stu-id="62ccf-105">In this tutorial, you'll learn how to create a basic UI for an image editing program by:</span></span> 

+ <span data-ttu-id="62ccf-106">Unter Verwendung des XAML-Tools in Visual Studio, z.B. XAML-Designer, Toolbox, XAML-Editor Eigenschaftenpanel und Dokumentgliederung können Sie Steuerelemente und Inhalte auf der Benutzeroberfläche hinzufügen</span><span class="sxs-lookup"><span data-stu-id="62ccf-106">Using the XAML tools in Visual Studio, such as XAML Designer, Toolbox, XAML editor, Properties panel, and Document Outline to add controls and content to your UI</span></span>
+ <span data-ttu-id="62ccf-107">Unter Verwendung einiger der häufigsten XAML-Layoutpanels, z.B. RelativePanel, Grid und StackPanel-Element.</span><span class="sxs-lookup"><span data-stu-id="62ccf-107">Utilizing some of the most common XAML layout panels, such as RelativePanel, Grid, and StackPanel.</span></span>

<span data-ttu-id="62ccf-108">Das Bildbearbeitungsprogramm hat zwei Seiten/Bildschirme:</span><span class="sxs-lookup"><span data-stu-id="62ccf-108">The image editing program has two pages/screens:</span></span>

<span data-ttu-id="62ccf-109">Die **Hauptseite** zeigt eine Ansicht der Foto-Galerie, zusammen mit einigen Informationen über jede Bilddatei an.</span><span class="sxs-lookup"><span data-stu-id="62ccf-109">The **main page**, which displays a photo gallery view, along with some information about each image file.</span></span>

![MainPage](images/xaml-basics/mainpage.png)

<span data-ttu-id="62ccf-111">Die **Detailsseite** zeigt ein einzelnes Foto an, nachdem es ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="62ccf-111">The **details page**, which displays a single photo after it has been selected.</span></span> <span data-ttu-id="62ccf-112">Über ein Flyout-Menü kann das Foto bearbeitet, umbenannt und gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-112">A flyout editing menu allows the photo to be altered, renamed, and saved.</span></span>

![DetailPage](images/xaml-basics/detailpage.png)


## <a name="prerequisites"></a><span data-ttu-id="62ccf-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="62ccf-114">Prerequisites</span></span>

* <span data-ttu-id="62ccf-115">Visual Studio 2017: [Visual Studio 2017 Community herunterladen (kostenlos)](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&campaign=WinDevCenter&ocid=wdgcx-windevcenter-community-download)</span><span class="sxs-lookup"><span data-stu-id="62ccf-115">Visual Studio 2017: [Download Visual Studio 2017 Community (free)](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&campaign=WinDevCenter&ocid=wdgcx-windevcenter-community-download)</span></span> 
* <span data-ttu-id="62ccf-116">Windows 10 SDK (10.0.15063.468 oder höher): [Neuestes Windows SDK herunterladen (kostenlos)](https://developer.microsoft.com/windows/downloads/windows-10-sdk)</span><span class="sxs-lookup"><span data-stu-id="62ccf-116">Windows 10 SDK (10.0.15063.468 or later):  [Download the latest Windows SDK (free)](https://developer.microsoft.com/windows/downloads/windows-10-sdk)</span></span>

## <a name="part-0-get-the-starter-code-from-github"></a><span data-ttu-id="62ccf-117">Teil 0: Startcode von Github holen</span><span class="sxs-lookup"><span data-stu-id="62ccf-117">Part 0: Get the starter code from github</span></span>

<span data-ttu-id="62ccf-118">Für dieses Tutorial starten Sie mit einer vereinfachten Version des PhotoLab-Beispiels.</span><span class="sxs-lookup"><span data-stu-id="62ccf-118">For this tutorial, you'll start with a simplified version of the PhotoLab sample.</span></span> 

1. <span data-ttu-id="62ccf-119">Wechseln Sie zu [https://github.com/Microsoft/Windows-appsample-photo-lab](https://github.com/Microsoft/Windows-appsample-photo-lab).</span><span class="sxs-lookup"><span data-stu-id="62ccf-119">Go to [https://github.com/Microsoft/Windows-appsample-photo-lab](https://github.com/Microsoft/Windows-appsample-photo-lab).</span></span> <span data-ttu-id="62ccf-120">Sie gelangen auf die GitHub-Seite für das Beispiel.</span><span class="sxs-lookup"><span data-stu-id="62ccf-120">This takes you to the GitHub page for the sample.</span></span> 
2. <span data-ttu-id="62ccf-121">Als nächstes müssen Sie das Beispiel klonen oder herunterladen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-121">Next, you'll need to clone or download the sample.</span></span> <span data-ttu-id="62ccf-122">Klicken Sie auf die Schaltfläche **Clone or download**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-122">Click the **Clone or download** button.</span></span> <span data-ttu-id="62ccf-123">Ein Untermenü erscheint.</span><span class="sxs-lookup"><span data-stu-id="62ccf-123">A sub-menu appears.</span></span>
    <figure>
        <img src="images/xaml-basics/clone-repo.png" alt="The Clone or download menu on GitHub">
        <figcaption><span data-ttu-id="62ccf-124">Das <b>Clone or download</b>-Menü auf der GitHub-Seite des Fotolbeispiels.</span><span class="sxs-lookup"><span data-stu-id="62ccf-124">The <b>Clone or download</b> menu on the Photo lab sample's GitHub page.</span></span></figcaption>
    </figure>

    **<span data-ttu-id="62ccf-125">Wenn Sie mit GitHub nicht vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="62ccf-125">If you're not familiar with GitHub:</span></span>**
    
    <span data-ttu-id="62ccf-126">a.</span><span class="sxs-lookup"><span data-stu-id="62ccf-126">a.</span></span> <span data-ttu-id="62ccf-127">Klicken Sie auf **Download ZIP** und speichern Sie die Datei lokal.</span><span class="sxs-lookup"><span data-stu-id="62ccf-127">Click **Download ZIP** and save the file locally.</span></span> <span data-ttu-id="62ccf-128">Es wird eine ZIP-Datei heruntergeladen, die alle benötigten Projektdateien enthält.</span><span class="sxs-lookup"><span data-stu-id="62ccf-128">This downloads a .zip file that contains all the project files you need.</span></span>
    <span data-ttu-id="62ccf-129">b.</span><span class="sxs-lookup"><span data-stu-id="62ccf-129">b.</span></span> <span data-ttu-id="62ccf-130">Entpacken Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="62ccf-130">Extract the file.</span></span> <span data-ttu-id="62ccf-131">Verwenden Sie den Datei-Explorer, um zu der gerade heruntergeladenen ZIP-Datei zu navigieren, klicken Sie mit der rechten Maustaste darauf und wählen Sie **Alle extrahieren...** aus. c.</span><span class="sxs-lookup"><span data-stu-id="62ccf-131">Use the File Explorer to navigate to the .zip file you just downloaded, right-click it, and select **Extract All...**. c.</span></span> <span data-ttu-id="62ccf-132">Navigieren Sie zu Ihrer lokalen Kopie des Beispiels und wechseln Sie zum `Windows-appsample-photo-lab-master\xaml-basics-starting-points\user-interface`-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="62ccf-132">Navigate to your local copy of the sample and go the `Windows-appsample-photo-lab-master\xaml-basics-starting-points\user-interface` directory.</span></span>    

    **<span data-ttu-id="62ccf-133">Wenn Sie mit GitHub vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="62ccf-133">If you are familiar with GitHub:</span></span>**

    <span data-ttu-id="62ccf-134">a.</span><span class="sxs-lookup"><span data-stu-id="62ccf-134">a.</span></span> <span data-ttu-id="62ccf-135">Klonen Sie den Master-Branch des Repos lokal.</span><span class="sxs-lookup"><span data-stu-id="62ccf-135">Clone the master branch of the repo locally.</span></span>
    <span data-ttu-id="62ccf-136">b.</span><span class="sxs-lookup"><span data-stu-id="62ccf-136">b.</span></span> <span data-ttu-id="62ccf-137">Navigieren Sie zum `Windows-appsample-photo-lab\xaml-basics-starting-points\user-interface`-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="62ccf-137">Navigate to the `Windows-appsample-photo-lab\xaml-basics-starting-points\user-interface` directory.</span></span>

3. <span data-ttu-id="62ccf-138">Öffnen Sie das Projekt durch einen Klick auf `Photolab.sln`.</span><span class="sxs-lookup"><span data-stu-id="62ccf-138">Open the project by clicking `Photolab.sln`.</span></span>

## <a name="part-1-add-a-textblock-using-xaml-designer"></a><span data-ttu-id="62ccf-139">Teil 1: Hinzufügen eines TextBlock-Steuerelements mit XAML-Designer</span><span class="sxs-lookup"><span data-stu-id="62ccf-139">Part 1: Add a TextBlock using XAML Designer</span></span>

<span data-ttu-id="62ccf-140">Visual Studio bietet verschiedene Tools zum leichteren Erstellen der XAML-UI.</span><span class="sxs-lookup"><span data-stu-id="62ccf-140">Visual Studio provides several tools to make creating your XAML UI easier.</span></span> <span data-ttu-id="62ccf-141">Mit XAML-Designer können Sie Steuerelemente auf die Designoberfläche ziehen und vor dem Ausführen der App anschauen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-141">XAML Designer lets you drag controls onto the design surface and see what they'll look like before you run the app.</span></span> <span data-ttu-id="62ccf-142">Mit dem Eigenschaftenpanel können Sie alle Eigenschaften des Steuerelements, die im Designer aktiv sind, ansehen und einstellen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-142">The Properties panel lets you view and set all the properties of the control that are active in the designer.</span></span> <span data-ttu-id="62ccf-143">Die Dokumentgliederung zeigt die über- und untergeordnete Struktur der visuellen XAML-Struktur für Ihre Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="62ccf-143">Document Outline shows the parent-child structure of the XAML visual tree for your UI.</span></span> <span data-ttu-id="62ccf-144">Mit dem XAML-Editor können Sie das XAML-Markup direkt eingeben und ändern.</span><span class="sxs-lookup"><span data-stu-id="62ccf-144">The XAML editor lets you directly enter and modify the XAML markup.</span></span>

<span data-ttu-id="62ccf-145">Hier ist die Visual Studio-UI mit den bezeichneten Tools.</span><span class="sxs-lookup"><span data-stu-id="62ccf-145">Here's the Visual Studio UI with the tools labeled.</span></span>

![Layout in Visual Studio](images/xaml-basics/visual-studio-tools.png)

<span data-ttu-id="62ccf-147">Diese Tools helfen Ihnen beim einfachen Erstellen der Benutzeroberfläche, deshalb werden sie alle in diesem Lernprogramm verwendet.</span><span class="sxs-lookup"><span data-stu-id="62ccf-147">Each of these tools make creating your UI easier, so we'll use all of them in this tutorial.</span></span> <span data-ttu-id="62ccf-148">Beginnen Sie mit XAML-Designer zum Hinzufügen eines Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="62ccf-148">You'll start by using XAML Designer to add a control.</span></span> 

**<span data-ttu-id="62ccf-149">Hinzufügen eines Steuerelements mithilfe von XAML-Designer:</span><span class="sxs-lookup"><span data-stu-id="62ccf-149">Add a control using XAML Designer:</span></span>**

1. <span data-ttu-id="62ccf-150">Doppelklicken Sie im Projektmappen-Explorer auf die Datei **MainPage.xaml**, um sie zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-150">Double-click **MainPage.xaml** in Solution Explorer to open it.</span></span> <span data-ttu-id="62ccf-151">Dies zeigt die Hauptseite der App an, ohne das ein UI-Element hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="62ccf-151">This shows the main page of the app without any UI elements added.</span></span>

2. <span data-ttu-id="62ccf-152">Vor dem fortfahren müssen Sie einige Anpassungen zu Visual Studio vornehmen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-152">Before going further, you need to make some adjustments to Visual Studio.</span></span>

    - <span data-ttu-id="62ccf-153">Stellen Sie sicher, dass Ihre Projektmappen-Plattform auf x86 oder x64 und nicht ARM festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="62ccf-153">Make sure the Solution Platform is set to x86 or x64, not ARM.</span></span>
    - <span data-ttu-id="62ccf-154">Legen Sie auf der Hauptseite des XAML-Designer die Desktopvorschau auf 13,3" fest.</span><span class="sxs-lookup"><span data-stu-id="62ccf-154">Set the main page XAML Designer to show the 13.3" Desktop preview.</span></span>

    <span data-ttu-id="62ccf-155">Beide Einstellungen sollten im oberen Bereich des Fensters angezeigt werden, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-155">You should see both settings near the top of the window, as shown here.</span></span>

    ![VS-Einstellungen:](images/xaml-basics/layout-vs-settings.png)

    <span data-ttu-id="62ccf-157">Sie können die App jetzt ausführen, es wird allerdings nicht viel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-157">You can run the app now, but you won't see much.</span></span> <span data-ttu-id="62ccf-158">Lassen Sie uns einige UI-Elemente einfügen, um die Dinge interessanter zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="62ccf-158">Let's add some UI elements to make things more interesting.</span></span>

3. <span data-ttu-id="62ccf-159">Erweitern Sie in der Toolbox **Allgemeine XAML-Steuerelemente** und suchen Sie das [TextBlock](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="62ccf-159">In Toolbox, expand **Common XAML controls** and find the [TextBlock](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock) control.</span></span> <span data-ttu-id="62ccf-160">Ziehen Sie einen TextBlock auf die Designoberfläche neben die obere linke Ecke der Seite.</span><span class="sxs-lookup"><span data-stu-id="62ccf-160">Drag a TextBlock onto the design surface near the upper left corner of the page.</span></span>

    <span data-ttu-id="62ccf-161">Der TextBlock wird zur Seite hinzugefügt, und der Designer legt einige Eigenschaften auf Grundlage seiner Einschätzung des gewünschten Layouts fest.</span><span class="sxs-lookup"><span data-stu-id="62ccf-161">The TextBlock is added to the page, and the designer sets some properties based on its best guess at the layout you want.</span></span> <span data-ttu-id="62ccf-162">Der TextBlock wird blau hervorgehoben, womit angezeigt wird, dass es sich dabei um das aktive Objekt handelt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-162">A blue highlight appears around the TextBlock to indicate that it is now the active object.</span></span> <span data-ttu-id="62ccf-163">Beachten Sie die Ränder und andere Einstellungen, die vom Designer hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-163">Notice the margins and other settings added by the designer.</span></span> <span data-ttu-id="62ccf-164">Ihr XAML sieht etwa wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="62ccf-164">Your XAML will look something like this.</span></span> <span data-ttu-id="62ccf-165">Keine Sorge, wenn er nicht genau wie folgt formatiert ist. Wir haben ihn hier verkürzt, um ihn einfacher zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="62ccf-165">Don't worry if it's not formatted exactly like this; we abbreviated here to make it easier to read.</span></span>

    ```xaml
    <TextBlock x:Name="textBlock"
               HorizontalAlignment="Left"
               Margin="351,44,0,0"
               TextWrapping="Wrap"
               Text="TextBlock"
               VerticalAlignment="Top"/>
    ```

    <span data-ttu-id="62ccf-166">In den nächsten Schritten aktualisieren Sie diese Werte.</span><span class="sxs-lookup"><span data-stu-id="62ccf-166">In the next steps, you'll update these values.</span></span>

4. <span data-ttu-id="62ccf-167">Ändern Sie im Bereich Eigenschaften den Namenswert des TextBlock von **TextBlock** auf **TitleTextBlock**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-167">In the Properties panel, change the Name value of the TextBlock from **textBlock** to **TitleTextBlock**.</span></span> <span data-ttu-id="62ccf-168">(Stellen Sie sicher, dass der TextBlock noch das aktive Objekt ist.)</span><span class="sxs-lookup"><span data-stu-id="62ccf-168">(Make sure the TextBlock is still the active object.)</span></span>

5. <span data-ttu-id="62ccf-169">Unter **Common**, ändern Sie den Textwert zu **Collection**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-169">Under **Common**, change the Text value to **Collection**.</span></span>

    ![TextBlock-Eigenschaften](images/xaml-basics/text-block-properties.png)

    <span data-ttu-id="62ccf-171">Im XAML-Editor sieht der XAML-Code nun wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="62ccf-171">In the XAML editor, your XAML will now look like this.</span></span>

    ```xaml
    <TextBlock x:Name="TitleTextBlock"
               HorizontalAlignment="Left"
               Margin="351,44,0,0"
               TextWrapping="Wrap"
               Text="Collection"
               VerticalAlignment="Top"/>
    ```

6. <span data-ttu-id="62ccf-172">Um den TextBlock zu positionieren, sollten Sie zunächst die Eigenschaftswerte entfernen, die von Visual Studio hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-172">To position the TextBlock, you should first remove the property values that were added by Visual Studio.</span></span> <span data-ttu-id="62ccf-173">Klicken Sie unter Dokumentgliederung mit der rechten Maustaste auf **TitleTextBlock** und wählen Sie dann **Layout > Alle zurücksetzen** aus.</span><span class="sxs-lookup"><span data-stu-id="62ccf-173">In Document Outline, right-click **TitleTextBlock**, then select **Layout > Reset All**.</span></span>

![Dokumentgliederung](images/xaml-basics/doc-outline-reset.png)

7. <span data-ttu-id="62ccf-175">Geben Sie im Bereich Eigenschaften **Margin** in das Suchfeld ein, um die Eigenschaft der **Margin** ganz leicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-175">In the Properties panel, enter **margin** into the search box to easily find the **Margin** property.</span></span> <span data-ttu-id="62ccf-176">Legen Sie den linken und unteren Rand auf 24 Pixel fest.</span><span class="sxs-lookup"><span data-stu-id="62ccf-176">Set the left and bottom margins to 24.</span></span>

    ![TextBlock-Ränder](images/xaml-basics/margins.png)

    <span data-ttu-id="62ccf-178">Ränder bieten die einfachste Positionierung eines Elements auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="62ccf-178">Margins provide the most basic positioning of an element on the page.</span></span> <span data-ttu-id="62ccf-179">Sie eignen sich für die Feinabstimmung des Layouts, aber das Verwenden großer Randwerte wie die von Visual Studio hinzugefügten Werte, machen es für Ihre Benutzeroberfläche schwieriger, sich an verschiedene Bildschirmgrößen anzupassen und sollten daher vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-179">They're useful for fine-tuning your layout, but using large margin values like those added by Visual Studio makes it difficult for your UI to adapt to various screen sizes, and should be avoided.</span></span>

    <span data-ttu-id="62ccf-180">Weitere Informationen hierzu finden Sie unter [Ausrichtung, Ränder und Abstand](../layout/alignment-margin-padding.md).</span><span class="sxs-lookup"><span data-stu-id="62ccf-180">For more info, see [Alignment, margins, and padding](../layout/alignment-margin-padding.md).</span></span>

8. <span data-ttu-id="62ccf-181">Klicken Sie mit der rechten Maustaste auf **TitleTextBlock** und wählen Sie dann **Edit Style > Apply Resource > TitleTextBlockStyle**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-181">In the Document Outline panel, right-click **TitleTextBlock**, then select **Edit Style > Apply Resource > TitleTextBlockStyle**.</span></span> <span data-ttu-id="62ccf-182">Dies wendet ein vom System definiertes Format für den Titeltext an.</span><span class="sxs-lookup"><span data-stu-id="62ccf-182">This applies a system-defined style to your title text.</span></span>

    ```xaml
    <TextBlock x:Name="TitleTextBlock"
               TextWrapping="Wrap"
               Text="Collection"
               Margin="24,0,0,24"
               Style="{StaticResource TitleTextBlockStyle}"/>
    ```

9. <span data-ttu-id="62ccf-183">Geben Sie im Bereich Eigenschaften **textwrapping** in das Suchfeld ein, um die Eigenschaft der **TextWrapping** ganz leicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-183">In the Properties panel, enter **textwrapping** into the search box to find the **TextWrapping** property.</span></span> <span data-ttu-id="62ccf-184">Klicken Sie auf den _Eigenschaftsmarker_ für den **TextWrapping**, um das Menü zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-184">Click the _property marker_ for the **TextWrapping** property to open its menu.</span></span> <span data-ttu-id="62ccf-185">(Der _Eigenschaftsmarker_ ist das kleine rechteckige Symbol rechts neben jedem Eigenschaftswert.</span><span class="sxs-lookup"><span data-stu-id="62ccf-185">(The _property marker_ is the small box symbol to the right of each property value.</span></span> <span data-ttu-id="62ccf-186">Der _Eigenschaftsmarker_ ist schwarz, um anzuzeigen, dass die Eigenschaft nicht auf einen Standardwert festgelegt ist.) Wählen Sie im Menü **Eigenschaften** **Zurücksetzen** aus, um die Eigenschaften von TextWrapping zurückzusetzen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-186">The _property marker_ is black to indicate that the property is set to a non-default value.) On the **Property** menu, select **Reset** to reset the TextWrapping property.</span></span>

    <span data-ttu-id="62ccf-187">Visual Studio fügt diese Eigenschaft hinzu, aber sie ist bereits in der Formatvorlage festgelegt, die Sie angewendet haben und Sie ist hier überflüssig.</span><span class="sxs-lookup"><span data-stu-id="62ccf-187">Visual Studio adds this property, but it's already set in the style you applied, so you don't need it here.</span></span>

<span data-ttu-id="62ccf-188">Sie haben Ihrer App den ersten Teil der Benutzeroberfläche hinzugefügt!</span><span class="sxs-lookup"><span data-stu-id="62ccf-188">You've added the first part of the UI to your app!</span></span> <span data-ttu-id="62ccf-189">Führen Sie die App jetzt aus, um herauszufinden, wie sie aussieht.</span><span class="sxs-lookup"><span data-stu-id="62ccf-189">Run the app now to see what it looks like.</span></span>

<span data-ttu-id="62ccf-190">Haben Sie bemerkt, dass Ihre App im XAML-Designer weißen Text auf schwarzem Hintergrund zeigt, aber wenn sie ausgeführt wird, schwarzen Text auf weißem Hintergrund anzeigt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-190">You might have noticed that in XAML Designer, your app showed white text on a black background, but when you ran it, it showed black text on a white background.</span></span> <span data-ttu-id="62ccf-191">Der Grund dafür ist, dass Windows über ein dunkles und ein helles Design verfügt, und das Standarddesign je nach Gerät variiert.</span><span class="sxs-lookup"><span data-stu-id="62ccf-191">That's because Windows has both a Dark and a Light theme, and the default theme varies by device.</span></span> <span data-ttu-id="62ccf-192">Auf einem PC ist das Standarddesign hell.</span><span class="sxs-lookup"><span data-stu-id="62ccf-192">On a PC, the default theme is Light.</span></span> <span data-ttu-id="62ccf-193">Sie können das Zahnradsymbol oben im XAML-Designer anklicken, um die Geräteeinstellungen für die Vorschau zu öffnen und das Design auf ändern setzen, damit die App im XAML-Designer genauso wie auf Ihrem PC aussieht.</span><span class="sxs-lookup"><span data-stu-id="62ccf-193">You can click the gear icon at the top of XAML Designer to open Device Preview Settings and change the theme to Light to make the app in XAML Designer look the same as it does on your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="62ccf-194">In diesem Teil des Lernprogramms haben Sie ein Steuerelement durch Ziehen und Ablegen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-194">In this part of the tutorial, you added a control by dragging-and-dropping.</span></span> <span data-ttu-id="62ccf-195">Sie können ebenfalls ein Steuerelement hinzufügen, indem Sie auf die Toolbox doppelklicken.</span><span class="sxs-lookup"><span data-stu-id="62ccf-195">You can also add a control by double-clicking it in Toolbox.</span></span> <span data-ttu-id="62ccf-196">Probieren Sie es aus, und sehen Sie die Unterschiede im XAML-Code, den Visual Studio generiert.</span><span class="sxs-lookup"><span data-stu-id="62ccf-196">Give it a try, and see the differences in the XAML that Visual Studio generates.</span></span>

## <a name="part-2-add-a-gridview-control-using-the-xaml-editor"></a><span data-ttu-id="62ccf-197">Teil 2: Hinzufügen eines GridView-Steuerelements mit dem XAML-Editor</span><span class="sxs-lookup"><span data-stu-id="62ccf-197">Part 2: Add a GridView control using the XAML editor</span></span>

<span data-ttu-id="62ccf-198">In Teil 1 haben Sie einen Einblick auf die Verwendung von XAML-Designer und einige der von Visual Studio bereitgestellten Tools erhalten.</span><span class="sxs-lookup"><span data-stu-id="62ccf-198">In Part 1, you had a taste of using XAML Designer and some of the other tools provided by Visual Studio.</span></span> <span data-ttu-id="62ccf-199">Hier verwenden Sie den XAML-Editor, um direkt mit XAML-Markup zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="62ccf-199">Here, you'll use the XAML editor to work directly with the XAML markup.</span></span> <span data-ttu-id="62ccf-200">Wenn Sie mit XAML vertraut sind, finden Sie unter Umständen, dass es sich um eine effiziente Art und Weise der Arbeit handelt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-200">As you become more familiar with XAML, you might find that this is a more efficient way for you to work.</span></span>

<span data-ttu-id="62ccf-201">Ersetzen Sie zuerst das Stammlayout-[Raster](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.grid) mit einem [**RelativePanel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.relativepanel).</span><span class="sxs-lookup"><span data-stu-id="62ccf-201">First, you'll replace the root layout [Grid](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.grid) with a [**RelativePanel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.relativepanel).</span></span> <span data-ttu-id="62ccf-202">Das RelativePanel erleichtert die Neuanordnung der Benutzeroberfläche relativ zum Bereich oder anderen Teilen der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="62ccf-202">The RelativePanel makes it easier to rearrange chunks of UI relative to the panel or other pieces of UI.</span></span> <span data-ttu-id="62ccf-203">Sie sehen den Nutzens im Lernprogramm [Adaptives XAML-Layout](xaml-basics-adaptive-layout.md).</span><span class="sxs-lookup"><span data-stu-id="62ccf-203">You'll see its usefulness in the [XAML Adaptive Layout](xaml-basics-adaptive-layout.md) tutorial.</span></span> 

<span data-ttu-id="62ccf-204">Fügen Sie dann ein [GridView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.gridview)-Steuerelement zum Anzeigen Ihrer Daten hinzu.</span><span class="sxs-lookup"><span data-stu-id="62ccf-204">Then, you'll add a [GridView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.gridview) control to display your data.</span></span>

**<span data-ttu-id="62ccf-205">Hinzufügen eines Steuerelements mit dem XAML-Editor</span><span class="sxs-lookup"><span data-stu-id="62ccf-205">Add a control using the XAML editor</span></span>**

1. <span data-ttu-id="62ccf-206">Ändern Sie im XAML-Editor das Stamm-**Raster** zu einem **RelativePanel**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-206">In the XAML editor, change the root **Grid** to a **RelativePanel**.</span></span>

    **<span data-ttu-id="62ccf-207">Vorher</span><span class="sxs-lookup"><span data-stu-id="62ccf-207">Before</span></span>**
    ```xaml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
          <TextBlock x:Name="TitleTextBlock"
                     Text="Collection"
                     Margin="24,0,0,24"
                     Style="{StaticResource TitleTextBlockStyle}"/>
    </Grid>
    ```

    **<span data-ttu-id="62ccf-208">Nachher</span><span class="sxs-lookup"><span data-stu-id="62ccf-208">After</span></span>**
    ```xaml
    <RelativePanel Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <TextBlock x:Name="TitleTextBlock"
                   Text="Collection"
                   Margin="24,0,0,24"
                   Style="{StaticResource TitleTextBlockStyle}"/>
    </RelativePanel>
    ```

    <span data-ttu-id="62ccf-209">Weitere Informationen zum Layout mit einem **RelativePanel** finden Sie unter [Layoutpanels](https://docs.microsoft.com/windows/uwp/layout/layout-panels#relativepanel).</span><span class="sxs-lookup"><span data-stu-id="62ccf-209">For more info about layout using a **RelativePanel**, see [Layout panels](https://docs.microsoft.com/windows/uwp/layout/layout-panels#relativepanel).</span></span>

2. <span data-ttu-id="62ccf-210">Fügen Sie unterhalb des **TextBlock**-Elements ein **GridView-Steuerelements** mit dem Namen 'ImageGridView' hinzu.</span><span class="sxs-lookup"><span data-stu-id="62ccf-210">Below the **TextBlock** element, add a **GridView control** named 'ImageGridView'.</span></span> <span data-ttu-id="62ccf-211">Legen Sie die _angefügte Eigenschaften_ des **RelativePanels**, um das Steuerelement unter dem Titeltext zu platzieren und erstrecken Sie es über die gesamte Breite des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="62ccf-211">Set the **RelativePanel** _attached properties_ to place the control below the title text and make it stretch across the entire width of the screen.</span></span>

    **<span data-ttu-id="62ccf-212">Diesen XAML-Code hinzufügen</span><span class="sxs-lookup"><span data-stu-id="62ccf-212">Add this XAML</span></span>**

    ```xaml
    <GridView x:Name="ImageGridView"
              Margin="0,0,0,8"
              RelativePanel.AlignLeftWithPanel="True"
              RelativePanel.AlignRightWithPanel="True"
              RelativePanel.Below="TitleTextBlock"/>
    ```

    **<span data-ttu-id="62ccf-213">Nach dem TextBlock</span><span class="sxs-lookup"><span data-stu-id="62ccf-213">After the TextBlock</span></span>**
    ```xaml
    <RelativePanel Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <TextBlock x:Name="TitleTextBlock"
                   Text="Collection"
                   Margin="24,0,0,24"
                   Style="{StaticResource TitleTextBlockStyle}"/>
        
        <!-- Add the GridView here. -->

    </RelativePanel>
    ```

    <span data-ttu-id="62ccf-214">Weitere Informationen zu Angefügte Paneleigenschaften finden Sie unter [Layoutpanels](https://docs.microsoft.com/windows/uwp/layout/layout-panels).</span><span class="sxs-lookup"><span data-stu-id="62ccf-214">For more info about Panel attached properties, see [Layout panels](https://docs.microsoft.com/windows/uwp/layout/layout-panels).</span></span>

3. <span data-ttu-id="62ccf-215">Damit **GridView** Elemente anzeigt, müssen Sie ihm eine Sammlung von Daten zum Anzeigen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-215">In order for the **GridView** to show anything, you need to give it a collection of data to show.</span></span> <span data-ttu-id="62ccf-216">Öffnen Sie MainPage.xaml.cs und suchen Sie die **GetItemsAsync**-Methode.</span><span class="sxs-lookup"><span data-stu-id="62ccf-216">Open MainPage.xaml.cs and find the **GetItemsAsync** method.</span></span> <span data-ttu-id="62ccf-217">Diese Methode füllt eine Sammlung mit dem Namen „Bilder” auf, was eine Eigenschaft ist, die wir unter MainPage hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="62ccf-217">This method populates a collection called Images, which is a property that we've added to MainPage.</span></span>

    <span data-ttu-id="62ccf-218">Fügen Sie nach der **foreach**-Schleife in **GetItemsAsync** folgende Codezeile hinzu.</span><span class="sxs-lookup"><span data-stu-id="62ccf-218">After the **foreach** loop in **GetItemsAsync**, add this line of code.</span></span>

    ```csharp
    ImageGridView.ItemsSource = Images;
    ```

    <span data-ttu-id="62ccf-219">Dadurch wird die GridView **ItemsSource**-Eigenschaft auf die **Bilder**-Sammlung der App festgelegt und es gibt Elemente **GridView**, die angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="62ccf-219">This sets the GridView's **ItemsSource** property to the app's **Images** collection and gives the **GridView** something to show.</span></span>

<span data-ttu-id="62ccf-220">Dies ist ein guter Ausgangspunkt zum Ausführen der App. Stellen Sie sicher, dass alles funktioniert.</span><span class="sxs-lookup"><span data-stu-id="62ccf-220">This is a good place to run the app and make sure everything's working.</span></span> <span data-ttu-id="62ccf-221">Es sieht etwa wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="62ccf-221">It should look something like this.</span></span>

![App-UI-Prüfpunkt 1](images/xaml-basics/layout-0.png)

<span data-ttu-id="62ccf-223">Sie werden feststellen, dass in der App noch keine Bilder angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-223">You'll notice that the app isn't showing images yet.</span></span> <span data-ttu-id="62ccf-224">Standardmäßig wird der ToString-Wert des Datentyps, der sich in der Auflistung befindet, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-224">By default, it shows the ToString value of the data type that's in the collection.</span></span> <span data-ttu-id="62ccf-225">Als Nächstes erstellen Sie eine Vorlage, die definiert, wie die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-225">Next, you'll create a data template to define how the data is shown.</span></span>

> [!NOTE]
> <span data-ttu-id="62ccf-226">Sie finden weitere Informationen zur Verwendung des Layouts eines **RelativePanel** im Artikel [Layoutpanels](https://docs.microsoft.com/windows/uwp/layout/layout-panels#relativepanel).</span><span class="sxs-lookup"><span data-stu-id="62ccf-226">You can find out more about layout using a **RelativePanel** in the [Layout panels](https://docs.microsoft.com/windows/uwp/layout/layout-panels#relativepanel) article.</span></span> <span data-ttu-id="62ccf-227">Schauen Sie mal nach und experimentieren Sie dann mit einigen anderen Layouts, indem Sie die angefügten Eigenschaften des RelativePanel auf **TextBlock** und **GridView** festlegen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-227">Take a look, and then experiment with some different layouts by setting RelativePanel attached properties on the **TextBlock** and **GridView**.</span></span>

## <a name="part-3-add-a-datatemplate-to-display-your-data"></a><span data-ttu-id="62ccf-228">Teil 3: Hinzufügen eines DataTemplates zum Anzeigen Ihrer Daten</span><span class="sxs-lookup"><span data-stu-id="62ccf-228">Part 3: Add a DataTemplate to display your data</span></span>

<span data-ttu-id="62ccf-229">Erstellen Sie jetzt ein [DataTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.datatemplate), das GridView mitteilt, wie Ihre Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-229">Now, you'll create a [DataTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.datatemplate) that tells the GridView how to display your data.</span></span> <span data-ttu-id="62ccf-230">Eine ausführliche Erläuterung der Datenvorlagen finden Sie unter [Elementcontainer und Vorlagen](../controls-and-patterns/item-containers-templates.md).</span><span class="sxs-lookup"><span data-stu-id="62ccf-230">For a full explanation of data templates, see [Item containers and templates](../controls-and-patterns/item-containers-templates.md).</span></span>

<span data-ttu-id="62ccf-231">Zunächst müssen Sie nur Platzhalter hinzufügen, die Ihnen beim Erstellen des gewünschten Layouts helfen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-231">For now, you'll only be adding placeholders to help you create the layout you want.</span></span> <span data-ttu-id="62ccf-232">Im Lernprogramm [XAML-Datenbindung](../../data-binding/xaml-basics-data-binding.md) können Sie diese Platzhalter durch echte Daten aus der **ImageFileInfo**-Klasse ersetzen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-232">In the [XAML Data Binding](../../data-binding/xaml-basics-data-binding.md) tutorial, you'll replace these placeholders with real data from the **ImageFileInfo** class.</span></span> <span data-ttu-id="62ccf-233">Sie können jetzt die ImageFileInfo.cs-Datei öffnen, wenn Sie überprüfen möchten, wie das Datenobjekt aussieht.</span><span class="sxs-lookup"><span data-stu-id="62ccf-233">You can open the ImageFileInfo.cs file now if you want to see what the data object looks like.</span></span>

**<span data-ttu-id="62ccf-234">Hinzufügen einer Datenvorlage zu einer Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="62ccf-234">Add a data template to a grid view</span></span>**

1. <span data-ttu-id="62ccf-235">Öffnen Sie MainPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="62ccf-235">Open MainPage.xaml.</span></span>

2. <span data-ttu-id="62ccf-236">Wenn die Bewertung anzeigen möchten, verwenden Sie das **RadRating**-Steuerelement aus dem [Telerik UI für UWP](https://github.com/telerik/UI-For-UWP)-NuGet-Paket.</span><span class="sxs-lookup"><span data-stu-id="62ccf-236">To show the rating, you use the **RadRating** control from the [Telerik UI for UWP](https://github.com/telerik/UI-For-UWP) NuGet package.</span></span> <span data-ttu-id="62ccf-237">Fügen Sie einen XAML-Namespace-Verweis hinzu, der den Namespace für das Telerik-Steuerelemente angibt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-237">Add a XAML namespace reference that specifies the namespace for the Telerik controls.</span></span> <span data-ttu-id="62ccf-238">Fügen Sie ihn dem Starttag **Seite** hinzu, direkt nach den anderen ' Xmlns:'-Einträgen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-238">Put this in the opening **Page** tag, right after the other 'xmlns:' entries.</span></span>

    **<span data-ttu-id="62ccf-239">Diesen XAML-Code hinzufügen</span><span class="sxs-lookup"><span data-stu-id="62ccf-239">Add this XAML</span></span>**

    ```xaml
    xmlns:telerikInput="using:Telerik.UI.Xaml.Controls.Input"
    ```

    **<span data-ttu-id="62ccf-240">Nach dem letzten ' Xmlns:'-Eintrag</span><span class="sxs-lookup"><span data-stu-id="62ccf-240">After the last 'xmlns:' entry</span></span>**

    ```xaml
    <Page x:Name="page"
      x:Class="PhotoLab.MainPage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:local="using:PhotoLab"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:telerikInput="using:Telerik.UI.Xaml.Controls.Input"
      mc:Ignorable="d"
      NavigationCacheMode="Enabled">
    ```

    <span data-ttu-id="62ccf-241">Weitere Informationen zu XAML-Namespaces finden Sie unter [XAML-Namespaces und Namespacezuordnung](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-namespaces-and-namespace-mapping).</span><span class="sxs-lookup"><span data-stu-id="62ccf-241">For more info about XAML namespaces, see [XAML namespaces and namespace mapping](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-namespaces-and-namespace-mapping).</span></span>

3. <span data-ttu-id="62ccf-242">Klicken Sie mit der rechten Maustaste unter Dokumentgliederung auf **ImageGridView**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-242">In Document Outline, right-click **ImageGridView**.</span></span> <span data-ttu-id="62ccf-243">Wählen Sie im Kontextmenü die Option \*\*Weitere Vorlagen bearbeiten > Generierten Inhalt bearbeiten (ItemTemplate) > Leere ... erstellen \*\*. Dies öffnet das Dialogfeld **Ressource erstellen**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-243">In the context menu, select **Edit Additional Templates > Edit Generated Items (ItemTemplate) > Create Empty...**. The **Create Resource** dialog opens.</span></span>

4. <span data-ttu-id="62ccf-244">Ändern Sie im Dialogfeld den Wert des Namens (Schlüssel) zu **ImageGridView_DefaultItemTemplate** und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-244">In the dialog, change the Name (key) value to **ImageGridView_DefaultItemTemplate**, and then click **OK**.</span></span>

    <span data-ttu-id="62ccf-245">Folgendes passiert, wenn Sie auf **OK** klicken.</span><span class="sxs-lookup"><span data-stu-id="62ccf-245">Several things happen when you click **OK**.</span></span>

    - <span data-ttu-id="62ccf-246">Es wird ein **DataTemplate** dem Abschnitt Page.Resources auf MainPage.xaml hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-246">A **DataTemplate** is added to the Page.Resources section of MainPage.xaml.</span></span>

        ```xaml
        <Page.Resources>
            <DataTemplate x:Key="ImageGridView_DefaultItemTemplate">
                <Grid/>
            </DataTemplate>
        </Page.Resources>
        ```

    - <span data-ttu-id="62ccf-247">Der Dokumentgliederungsbereicht wird auf **DataTemplate** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-247">The Document Outline scope is set to this **DataTemplate**.</span></span>

        <span data-ttu-id="62ccf-248">Wenn Sie die Datenvorlage erstellt haben, klicken Sie auf den Pfeil in der oberen linken Ecke der Dokumentgliederung, um zum Seitenbereich zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="62ccf-248">When you're done creating the data template, you can click the up arrow in the top left corner of Document Outline to return to page scope.</span></span>

    - <span data-ttu-id="62ccf-249">Die GridView **ItemTemplate**-Eigenschaft wird auf die **DataTemplate**-Ressource festgelegt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-249">The GridView's **ItemTemplate** property is set to the **DataTemplate** resource.</span></span>

    ```xaml
        <GridView x:Name="ImageGridView"
                  Margin="0,0,0,8"
                  RelativePanel.AlignLeftWithPanel="True"
                  RelativePanel.AlignRightWithPanel="True"
                  RelativePanel.Below="TitleTextBlock"
                  ItemTemplate="{StaticResource ImageGridView_DefaultItemTemplate}"/>
    ```

5. <span data-ttu-id="62ccf-250">In der **ImageGridView_DefaultItemTemplate**-Ressource, geben Sie dem Stamm-**Raster** eine Höhe und Breite von **300**, und einen Rand von **8**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-250">In the **ImageGridView_DefaultItemTemplate** resource, give the root **Grid** a Height and Width of **300**, and Margin of **8**.</span></span> <span data-ttu-id="62ccf-251">Fügen Sie dann zwei Zeilen hinzu und legen Sie die Höhe der zweiten Zeile auf **Auto** fest.</span><span class="sxs-lookup"><span data-stu-id="62ccf-251">Then add two rows and set the Height of the second row to **Auto**.</span></span>

    **<span data-ttu-id="62ccf-252">Vorher</span><span class="sxs-lookup"><span data-stu-id="62ccf-252">Before</span></span>**
    ```xaml
    <Grid/>
    ```

    **<span data-ttu-id="62ccf-253">Nachher</span><span class="sxs-lookup"><span data-stu-id="62ccf-253">After</span></span>**
    ```xaml
    <Grid Height="300"
          Width="300"
          Margin="8">
        <Grid.RowDefinitions>
            <RowDefinition />
            <RowDefinition Height="Auto" />
        </Grid.RowDefinitions>
    </Grid>
    ```

    <span data-ttu-id="62ccf-254">Weitere Informationen zu Rasterlayouts finden Sie unter [Layoutpanels](https://docs.microsoft.com/windows/uwp/layout/layout-panels#grid).</span><span class="sxs-lookup"><span data-stu-id="62ccf-254">For more info about Grid layouts, see [Layout panels](https://docs.microsoft.com/windows/uwp/layout/layout-panels#grid).</span></span>

6. <span data-ttu-id="62ccf-255">Hinzufügen von Steuerelementen zum Raster.</span><span class="sxs-lookup"><span data-stu-id="62ccf-255">Add controls to the Grid.</span></span>

    <span data-ttu-id="62ccf-256">a.</span><span class="sxs-lookup"><span data-stu-id="62ccf-256">a.</span></span> <span data-ttu-id="62ccf-257">Fügen Sie ein **Bild**-Steuerelement in die erste Rasterzeile ein.</span><span class="sxs-lookup"><span data-stu-id="62ccf-257">Add an **Image** control in the first grid row.</span></span> <span data-ttu-id="62ccf-258">Hier wird das Bild angezeigt, doch im Moment können Sie das Logo des App Stores als Platzhalter verwenden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-258">This is where the image will be shown, but for now, you'll use the app's store logo as a placeholder.</span></span>

    <span data-ttu-id="62ccf-259">b.</span><span class="sxs-lookup"><span data-stu-id="62ccf-259">b.</span></span> <span data-ttu-id="62ccf-260">Fügen Sie **TextBlock**-Steuerelemente zum Anzeigen des Namens, Dateityps und der Dimensionen des Bilds hinzu.</span><span class="sxs-lookup"><span data-stu-id="62ccf-260">Add **TextBlock** controls to show the image's name, file type, and dimensions.</span></span> <span data-ttu-id="62ccf-261">Verwenden Sie hierzu **StackPanel**-Steuerelemente, um die Textblöcke anzuordnen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-261">For this, you use **StackPanel** controls to arrange the text blocks.</span></span>

    <span data-ttu-id="62ccf-262">Weitere Informationen zu **StackPanel**-Layouts finden Sie unter [Layoutpanels](https://docs.microsoft.com/windows/uwp/layout/layout-panels#stackpanel)</span><span class="sxs-lookup"><span data-stu-id="62ccf-262">For more info about **StackPanel** layout, see [Layout panels](https://docs.microsoft.com/windows/uwp/layout/layout-panels#stackpanel)</span></span>

    <span data-ttu-id="62ccf-263">c.</span><span class="sxs-lookup"><span data-stu-id="62ccf-263">c.</span></span> <span data-ttu-id="62ccf-264">Hinzufügen des **RadRating**-Steuerelements zum äußeren (vertikalen) **StackPanel**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-264">Add the **RadRating** control to the outer (vertical) **StackPanel**.</span></span> <span data-ttu-id="62ccf-265">Platzieren Sie es nach dem inneren (horizontalen) **StackPanel**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-265">Place it after the inner (horizontal) **StackPanel**.</span></span>

    **<span data-ttu-id="62ccf-266">Die endgültige Vorlage</span><span class="sxs-lookup"><span data-stu-id="62ccf-266">The final template</span></span>**

    ```xaml
    <Grid Height="300"
          Width="300"
          Margin="8">
        <Grid.RowDefinitions>
            <RowDefinition />
            <RowDefinition Height="Auto" />
        </Grid.RowDefinitions>

        <Image x:Name="ItemImage"
               Source="Assets/StoreLogo.png"
               Stretch="Uniform" />

        <StackPanel Orientation="Vertical"
                    Grid.Row="1">
            <TextBlock Text="ImageTitle"
                       HorizontalAlignment="Center"
                       Style="{StaticResource SubtitleTextBlockStyle}" />
            <StackPanel Orientation="Horizontal"
                        HorizontalAlignment="Center">
                <TextBlock Text="ImageFileType"
                           HorizontalAlignment="Center"
                           Style="{StaticResource CaptionTextBlockStyle}" />
                <TextBlock Text="ImageDimensions"
                           HorizontalAlignment="Center"
                           Style="{StaticResource CaptionTextBlockStyle}"
                           Margin="8,0,0,0" />
            </StackPanel>

            <telerikInput:RadRating Value="3"
                                    IsReadOnly="True">
                <telerikInput:RadRating.FilledIconContentTemplate>
                    <DataTemplate>
                        <SymbolIcon Symbol="SolidStar"
                                    Foreground="White" />
                    </DataTemplate>
                </telerikInput:RadRating.FilledIconContentTemplate>
                <telerikInput:RadRating.EmptyIconContentTemplate>
                    <DataTemplate>
                        <SymbolIcon Symbol="OutlineStar"
                                    Foreground="White" />
                    </DataTemplate>
                </telerikInput:RadRating.EmptyIconContentTemplate>
            </telerikInput:RadRating>

        </StackPanel>
    </Grid>
    ```

<span data-ttu-id="62ccf-267">Führen Sie die App jetzt aus, um **GridView** mit der Elementvorlage anzuzeigen, die Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="62ccf-267">Run the app now to see the **GridView** with the item template you just created.</span></span> <span data-ttu-id="62ccf-268">Möglicherweise wird das Bewertungssteuerelement nicht angezeigt, da es weiße Sternen auf weißem Hintergrund hat.</span><span class="sxs-lookup"><span data-stu-id="62ccf-268">You might not see the rating control, though, because it has white stars on a white background.</span></span> <span data-ttu-id="62ccf-269">Als Nächstes ändern Sie die Hintergrundfarbe.</span><span class="sxs-lookup"><span data-stu-id="62ccf-269">You'll change the background color next.</span></span>

![App-UI-Prüfpunkt 2](images/xaml-basics/layout-1.png)

## <a name="part-4-modify-the-item-container-style"></a><span data-ttu-id="62ccf-271">Teil 4: Ändern des Elementcontainerstils</span><span class="sxs-lookup"><span data-stu-id="62ccf-271">Part 4: Modify the item container style</span></span>

<span data-ttu-id="62ccf-272">Eine Steuerelementvorlage für ein Element enthält die optischen Elemente zur Anzeige des Zustands wie Auswahl, Zeiger und Fokus.</span><span class="sxs-lookup"><span data-stu-id="62ccf-272">An item’s control template contains the visuals that display state, like selection, pointer over, and focus.</span></span> <span data-ttu-id="62ccf-273">Diese visuellen Elemente werden über oder unter der Datenvorlage gerendert.</span><span class="sxs-lookup"><span data-stu-id="62ccf-273">These visuals are rendered either on top of or below the data template.</span></span> <span data-ttu-id="62ccf-274">Hier ändern Sie die **Hintergrund**- und **Rand**-Eigenschaften der Steuerelementvorlage, um dem **GridView**-Elemente einen grauen Hintergrund hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-274">Here, you'll modify the **Background** and **Margin** properties of the control template to give the **GridView** items a gray background.</span></span>

**<span data-ttu-id="62ccf-275">Ändern des Elementcontainers</span><span class="sxs-lookup"><span data-stu-id="62ccf-275">Modify the item container</span></span>**

1. <span data-ttu-id="62ccf-276">Klicken Sie mit der rechten Maustaste unter Dokumentgliederung auf **ImageGridView**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-276">In Document Outline, right-click **ImageGridView**.</span></span> <span data-ttu-id="62ccf-277">Wählen Sie im Kontextmenü die Option **Weitere Vorlagen bearbeiten > Generierten Containerinhalt bearbeiten (ItemContainerStyle) > Kopie erstellen...**. Dies öffnet das Dialogfeld **Ressource erstellen**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-277">On the context menu, select **Edit Additional Templates > Edit Generated Item Container (ItemContainerStyle) > Edit a Copy...**. The **Create Resource** dialog opens.</span></span>

2. <span data-ttu-id="62ccf-278">Ändern Sie im Dialogfeld den Wert des Namens (Schlüssel) zu **ImageGridView_DefaultItemContainerStyle** und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-278">In the dialog, change the Name (key) value to **ImageGridView_DefaultItemContainerStyle**, then click **OK**.</span></span>

    <span data-ttu-id="62ccf-279">Es wird eine Kopie des Standardstils dem Abschnitt **Page.Resources** des XAML-Codes hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-279">A copy of the default style is added to the **Page.Resources** section of your XAML.</span></span>

    ```xaml
    <Style x:Key="ImageGridView_DefaultItemContainerStyle" TargetType="GridViewItem">
        <Setter Property="FontFamily" Value="{ThemeResource ContentControlThemeFontFamily}"/>
        <Setter Property="FontSize" Value="{ThemeResource ControlContentThemeFontSize}"/>
        <Setter Property="Background" Value="{ThemeResource GridViewItemBackground}"/>
        <Setter Property="Foreground" Value="{ThemeResource GridViewItemForeground}"/>
        <Setter Property="TabNavigation" Value="Local"/>
        <Setter Property="IsHoldingEnabled" Value="True"/>
        <Setter Property="HorizontalContentAlignment" Value="Center"/>
        <Setter Property="VerticalContentAlignment" Value="Center"/>
        <Setter Property="Margin" Value="0,0,4,4"/>
        <Setter Property="MinWidth" Value="{ThemeResource GridViewItemMinWidth}"/>
        <Setter Property="MinHeight" Value="{ThemeResource GridViewItemMinHeight}"/>
        <Setter Property="AllowDrop" Value="False"/>
        <Setter Property="UseSystemFocusVisuals" Value="True"/>
        <Setter Property="FocusVisualMargin" Value="-2"/>
        <Setter Property="FocusVisualPrimaryBrush" Value="{ThemeResource GridViewItemFocusVisualPrimaryBrush}"/>
        <Setter Property="FocusVisualPrimaryThickness" Value="2"/>
        <Setter Property="FocusVisualSecondaryBrush" Value="{ThemeResource GridViewItemFocusVisualSecondaryBrush}"/>
        <Setter Property="FocusVisualSecondaryThickness" Value="1"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="GridViewItem">
                <!-- XAML removed for clarity
                    <ListViewItemPresenter ... />
                -->   
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
    ```

    <span data-ttu-id="62ccf-280">Der **GridViewItem**-Standardstil legt zahlreiche Eigenschaften fest.</span><span class="sxs-lookup"><span data-stu-id="62ccf-280">The **GridViewItem** default style sets a lot of properties.</span></span> <span data-ttu-id="62ccf-281">Es wird empfohlen, mit einer Kopie des Standardstils zu beginnen und nur die notwendigen Eigenschaften zu ändern.</span><span class="sxs-lookup"><span data-stu-id="62ccf-281">You should always start with a copy of the default style and modify only the properties necessary.</span></span> <span data-ttu-id="62ccf-282">Andernfalls werden die visuellen Elemente wahrscheinlich nicht so wie angezeigt, die Sie es erwarten, da einige Eigenschaften nicht richtig festgelegt sein werden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-282">Otherwise, the visuals might not show up the way you expect because some properties won't be set correctly.</span></span>

    <span data-ttu-id="62ccf-283">Und wie im vorherigen Schritt wird die GridView **ItemContainerStyle**-Eigenschaft auf die neue **Stil**-Ressource festgelegt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-283">And as in the previous step, the GridView's **ItemContainerStyle** property is set to the new **Style** resource.</span></span>

    ```xaml
        <GridView x:Name="ImageGridView"
                  Margin="0,0,0,8"
                  RelativePanel.AlignLeftWithPanel="True"
                  RelativePanel.AlignRightWithPanel="True"
                  RelativePanel.Below="TitleTextBlock"
                  ItemTemplate="{StaticResource ImageGridView_DefaultItemTemplate}"
                  ItemContainerStyle="{StaticResource ImageGridView_DefaultItemContainerStyle}"/>
    ```

3. <span data-ttu-id="62ccf-284">Ändern Sie den Wert der **Hintergrund**-Eigenschaft auf **Grau**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-284">Change the value for the **Background** property to **Gray**.</span></span>

    **<span data-ttu-id="62ccf-285">Vorher</span><span class="sxs-lookup"><span data-stu-id="62ccf-285">Before</span></span>**
    ```xaml
        <Setter Property="Background" Value="{ThemeResource GridViewItemBackground}"/>
    ```

    **<span data-ttu-id="62ccf-286">Nachher</span><span class="sxs-lookup"><span data-stu-id="62ccf-286">After</span></span>**
    ```xaml
        <Setter Property="Background" Value="Gray"/>
    ```

4. <span data-ttu-id="62ccf-287">Ändern Sie den Wert der **Rand**-Eigenschaft auf **8**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-287">Change the value for the **Margin** property to **8**.</span></span>

    **<span data-ttu-id="62ccf-288">Vorher</span><span class="sxs-lookup"><span data-stu-id="62ccf-288">Before</span></span>**
    ```xaml
        <Setter Property="Margin" Value="0,0,4,4"/>
    ```

    **<span data-ttu-id="62ccf-289">Nachher</span><span class="sxs-lookup"><span data-stu-id="62ccf-289">After</span></span>**
    ```xaml
        <Setter Property="Margin" Value="8"/>
    ```

<span data-ttu-id="62ccf-290">Führen Sie die App aus, um herauszufinden, wie sie bisher aussieht.</span><span class="sxs-lookup"><span data-stu-id="62ccf-290">Run the app and see how it looks now.</span></span> <span data-ttu-id="62ccf-291">Skalieren des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="62ccf-291">Resize the app window.</span></span> <span data-ttu-id="62ccf-292">**GridView** kümmert sich um das Neuanordnen der Bilder, aber bei einige Breiten ist noch viel Platz auf der rechten Seite des App-Fensters vorhanden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-292">The **GridView** takes care of rearranging the images for you, but at some widths, there's a lot of space on the right side of the app window.</span></span> <span data-ttu-id="62ccf-293">Es würde besser aussehen, wenn die Bilder zentriert werden.</span><span class="sxs-lookup"><span data-stu-id="62ccf-293">It would look better if the images were centered.</span></span> <span data-ttu-id="62ccf-294">Damit werden wir uns als nächstes befassen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-294">We'll take care of that next.</span></span>

![App-UI-Prüfpunkt 3](images/xaml-basics/layout-2.png)

> [!Note]
> <span data-ttu-id="62ccf-296">Wenn Sie experimentieren möchten, versuchen Sie, die Hintergrund- und Rand-Eigenschaften mit unterschiedlichen Werten festzulegen und welche Auswirkung dies hat.</span><span class="sxs-lookup"><span data-stu-id="62ccf-296">If you'd like to experiment, try setting the Background and Margin properties to different values and see what effect it has.</span></span>

## <a name="part-5-apply-some-final-adjustments-to-the-layout"></a><span data-ttu-id="62ccf-297">Teil 5: Anwenden einiger abschließender Anpassungen am Layout</span><span class="sxs-lookup"><span data-stu-id="62ccf-297">Part 5: Apply some final adjustments to the layout</span></span>

<span data-ttu-id="62ccf-298">Um die Bilder auf der Seite zu zentrieren, müssen Sie die Ausrichtung des Rasters auf der Seite anpassen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-298">To center the images in the page, you need to adjust the alignment of the Grid in the page.</span></span> <span data-ttu-id="62ccf-299">Oder möchten Sie die Ausrichtung der Bilder in **GridView** anpassen?</span><span class="sxs-lookup"><span data-stu-id="62ccf-299">Or do you need to adjust the alignment of the Images in the **GridView**?</span></span> <span data-ttu-id="62ccf-300">Ist es wichtig?</span><span class="sxs-lookup"><span data-stu-id="62ccf-300">Does it matter?</span></span> <span data-ttu-id="62ccf-301">Mal sehen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-301">Let's see.</span></span>

<span data-ttu-id="62ccf-302">Weitere Informationen zur Anpassung finden Sie unter [Ausrichtung, Ränder und Abstand](../layout/alignment-margin-padding.md).</span><span class="sxs-lookup"><span data-stu-id="62ccf-302">For more info about alignment, see [Alignment, margins, and padding](../layout/alignment-margin-padding.md).</span></span>

<span data-ttu-id="62ccf-303">(Sie können in diesem Schritt versuchen, die Einstellung des **Hintergrunds** des **GridViews** auf Ihre bevorzugte Farbe festzulegen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-303">(You might try setting the **Background** of the **GridView** to your favorite color for this step.</span></span> <span data-ttu-id="62ccf-304">So sehen Sie, was mit dem Layout passiert.)</span><span class="sxs-lookup"><span data-stu-id="62ccf-304">It will let you see more clearly what's happening with the layout.)</span></span>

**<span data-ttu-id="62ccf-305">Ändern der Ausrichtung der Bilder</span><span class="sxs-lookup"><span data-stu-id="62ccf-305">Modify the alignment of the images</span></span>**

1. <span data-ttu-id="62ccf-306">Legen Sie in **Gridview** die **HorizontalAlignment**-Eigenschaft auf **Center** fest.</span><span class="sxs-lookup"><span data-stu-id="62ccf-306">In the **Gridview**, set the **HorizontalAlignment** property to **Center**.</span></span>

    **<span data-ttu-id="62ccf-307">Vorher</span><span class="sxs-lookup"><span data-stu-id="62ccf-307">Before</span></span>**
    ```xaml
        <GridView x:Name="ImageGridView"
                  Margin="0,0,0,8"
                  RelativePanel.AlignLeftWithPanel="True"
                  RelativePanel.AlignRightWithPanel="True"
                  RelativePanel.Below="TitleTextBlock"
                  ItemTemplate="{StaticResource ImageGridView_DefaultItemTemplate}"
                  ItemContainerStyle="{StaticResource ImageGridView_DefaultItemContainerStyle}"/>
    ```

    **<span data-ttu-id="62ccf-308">Nachher</span><span class="sxs-lookup"><span data-stu-id="62ccf-308">After</span></span>**
    ```xaml
        <GridView x:Name="ImageGridView"
                  Margin="0,0,0,8"
                  RelativePanel.AlignLeftWithPanel="True"
                  RelativePanel.AlignRightWithPanel="True"
                  RelativePanel.Below="TitleTextBlock"
                  ItemTemplate="{StaticResource ImageGridView_DefaultItemTemplate}"
                  ItemContainerStyle="{StaticResource ImageGridView_DefaultItemContainerStyle}" 
                  HorizontalAlignment="Center"/>
    ```

2. <span data-ttu-id="62ccf-309">Führen Sie die App aus, und skalieren Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="62ccf-309">Run the app and resize the window.</span></span> <span data-ttu-id="62ccf-310">Scrollen Sie nach unten, um weitere Bilder anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-310">Scroll down to see more images.</span></span>

    <span data-ttu-id="62ccf-311">Die Bilder werden zentriert, was besser aussieht.</span><span class="sxs-lookup"><span data-stu-id="62ccf-311">The images are centered, which looks better.</span></span> <span data-ttu-id="62ccf-312">Die Bildlaufleiste wird jedoch am Rand von **GridView** anstelle am Rand des Fensters ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="62ccf-312">However, the scrollbar is aligned with the edge of **GridView** instead of with the edge of the window.</span></span> <span data-ttu-id="62ccf-313">Um dieses Problem zu beheben, zentrieren Sie die Bilder in der **GridView**, anstatt sie in der **GridView** auf der Seite zu zentrieren.</span><span class="sxs-lookup"><span data-stu-id="62ccf-313">To fix this, you'll center the images in the **GridView** rather than centering the **GridView** in the page.</span></span> <span data-ttu-id="62ccf-314">Es ist etwas mehr Arbeit, sieht aber am Ende besser aus.</span><span class="sxs-lookup"><span data-stu-id="62ccf-314">It's a little more work, but it will look better in the end.</span></span>

3. <span data-ttu-id="62ccf-315">Entfernen Sie die **HorizontalAlignment**-Einstellung aus dem vorherigen Schritt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-315">Remove the **HorizontalAlignment** setting from the previous step.</span></span>

4. <span data-ttu-id="62ccf-316">Klicken Sie mit der rechten Maustaste unter Dokumentgliederung auf **ImageGridView**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-316">In Document Outline, right-click **ImageGridView**.</span></span> <span data-ttu-id="62ccf-317">Wählen Sie im Kontextmenü die Option **Weitere Vorlagen bearbeiten > Layout der Elemente bearbeiten (ItemsPanel) > Kopie erstellen...**. Dies öffnet das Dialogfeld **Ressource erstellen**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-317">On the context menu, select **Edit Additional Templates > Edit Layout of Items (ItemsPanel) > Edit a Copy...**. The **Create Resource** dialog opens.</span></span>

5. <span data-ttu-id="62ccf-318">Ändern Sie im Dialogfeld den Wert des Namens (Schlüssel) zu **ImageGridView_ItemsPanelTemplate** und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="62ccf-318">In the dialog, change the Name (key) value to **ImageGridView_ItemsPanelTemplate**, and then click **OK**.</span></span>

    <span data-ttu-id="62ccf-319">Es wird eine Kopie des Standard-**ItemsPanelTemplate** dem Abschnitt **Page.Resources** des XAML-Codes hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-319">A copy of the default **ItemsPanelTemplate** is added to the **Page.Resources** section of your XAML.</span></span> <span data-ttu-id="62ccf-320">(Wie zuvor, wird die **GridView** aktualisiert, um auf diese Ressource zu verweisen.)</span><span class="sxs-lookup"><span data-stu-id="62ccf-320">(And as before, the **GridView** is updated to reference this resource.)</span></span>

    ```xaml
    <ItemsPanelTemplate x:Key="ImageGridView_ItemsPanelTemplate">
        <ItemsWrapGrid Orientation="Horizontal" />
    </ItemsPanelTemplate>
    ```

    <span data-ttu-id="62ccf-321">Genau wie die verschiedenen Bereiche für das Layout der Steuerelemente in Ihrer App verwendet wurden, enthält **GridView** einen internen Bereich, der das Layout der Elemente verwaltet.</span><span class="sxs-lookup"><span data-stu-id="62ccf-321">Just as you've used various panels to layout the controls in your app, the **GridView** has an internal panel that manages the layout of its items.</span></span> <span data-ttu-id="62ccf-322">Jetzt wo Sie Zugriff auf diesen Bereich haben (das **ItemsWrapGrid**), können Sie die Eigenschaften des Layouts der Elementen in **GridView** ändern.</span><span class="sxs-lookup"><span data-stu-id="62ccf-322">Now that you have access to this panel (the **ItemsWrapGrid**), you can modify its properties to change the layout of items inside the **GridView**.</span></span>

6. <span data-ttu-id="62ccf-323">Legen Sie in **ItemsWrapGrid** die **HorizontalAlignment**-Eigenschaft auf **Center** fest.</span><span class="sxs-lookup"><span data-stu-id="62ccf-323">In the **ItemsWrapGrid**, set the **HorizontalAlignment** property to **Center**.</span></span>

    **<span data-ttu-id="62ccf-324">Vorher</span><span class="sxs-lookup"><span data-stu-id="62ccf-324">Before</span></span>**
    ```xaml
    <ItemsPanelTemplate x:Key="ImageGridView_ItemsPanelTemplate">
        <ItemsWrapGrid Orientation="Horizontal" />
    </ItemsPanelTemplate>
    ```

    **<span data-ttu-id="62ccf-325">Nachher</span><span class="sxs-lookup"><span data-stu-id="62ccf-325">After</span></span>**
    ```xaml
    <ItemsPanelTemplate x:Key="ImageGridView_ItemsPanelTemplate">
        <ItemsWrapGrid Orientation="Horizontal"
                       HorizontalAlignment="Center"/>
    </ItemsPanelTemplate>
    ```

7. <span data-ttu-id="62ccf-326">Führen Sie die App aus, und skalieren Sie das Fenster erneut.</span><span class="sxs-lookup"><span data-stu-id="62ccf-326">Run the app and resize the window again.</span></span> <span data-ttu-id="62ccf-327">Scrollen Sie nach unten, um weitere Bilder anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="62ccf-327">Scroll down to see more images.</span></span>

![App-UI-Prüfpunkt 4](images/xaml-basics/layout-3.png)

<span data-ttu-id="62ccf-329">Nun ist die Bildlaufleiste am Rand des Fensters ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="62ccf-329">Now, the scrollbar is aligned with the edge of the window.</span></span> <span data-ttu-id="62ccf-330">Gut gemacht!</span><span class="sxs-lookup"><span data-stu-id="62ccf-330">Good job!</span></span> <span data-ttu-id="62ccf-331">Sie haben die grundlegende Benutzeroberfläche für Ihre App erstellt.</span><span class="sxs-lookup"><span data-stu-id="62ccf-331">You've created the basic UI for your app.</span></span>

## <a name="going-further"></a><span data-ttu-id="62ccf-332">Vertiefung</span><span class="sxs-lookup"><span data-stu-id="62ccf-332">Going further</span></span>

<span data-ttu-id="62ccf-333">Nachdem Sie nun die grundlegende Benutzeroberfläche erstellt haben, können Sie diese weitere Tutorials nutzen, die ebenfalls auf dem PhotoLab-Beispiel basieren:</span><span class="sxs-lookup"><span data-stu-id="62ccf-333">Now that you've created the basic UI, checkout out these other tutorials, also based on the PhotoLab sample:</span></span> 

* <span data-ttu-id="62ccf-334">Fügen Sie echte Bilder und Daten im [XAML-Datenbindungs-Tutorial](../../data-binding/xaml-basics-data-binding.md) hinzu.</span><span class="sxs-lookup"><span data-stu-id="62ccf-334">Add real images and data in the [XAML data binding tutorial](../../data-binding/xaml-basics-data-binding.md).</span></span>
* <span data-ttu-id="62ccf-335">Passen Sie die Benutzeroberfläche im [XAML-Layout-Tutorial](xaml-basics-adaptive-layout.md) an unterschiedliche Bildschirmgrößen an.</span><span class="sxs-lookup"><span data-stu-id="62ccf-335">Make the UI adapt to different screen sizes in the [XAML adaptive layout tutorial](xaml-basics-adaptive-layout.md).</span></span>


## <a name="get-the-final-version-of-the-photolab-sample"></a><span data-ttu-id="62ccf-336">Abrufen der finalen Version des PhotoLab-Beispiels</span><span class="sxs-lookup"><span data-stu-id="62ccf-336">Get the final version of the PhotoLab sample</span></span>

<span data-ttu-id="62ccf-337">In diesem Lernprogramm lernen Sie nicht das Erstellen der vollständigen App. Lesen Sie daher die [endgültige Version](https://github.com/Microsoft/Windows-appsample-photo-lab) zu Features durch wie z.B. benutzerdefinierte Animationen und Support für Ihre Telefon.</span><span class="sxs-lookup"><span data-stu-id="62ccf-337">This tutorial doesn't build up to the complete photo editing app, so be sure to check out the [final version](https://github.com/Microsoft/Windows-appsample-photo-lab) to see other features such as custom animations and phone support.</span></span>

