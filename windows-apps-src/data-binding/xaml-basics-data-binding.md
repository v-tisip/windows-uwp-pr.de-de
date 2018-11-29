---
title: Erstellen von Datenbindungen
description: In diesem Artikel werden die Grundlagen der Datenbindung in XAML behandelt
keywords: XAML, UWP, Erste Schritte
ms.date: 08/30/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 21a053934d7391d12f7cd987026524b9ff4c279d
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8192654"
---
# <a name="create-data-bindings"></a><span data-ttu-id="321c9-104">Erstellen von Datenbindungen</span><span class="sxs-lookup"><span data-stu-id="321c9-104">Create data bindings</span></span>

<span data-ttu-id="321c9-105">Angenommen, Sie haben eine schöne UI entworfen und implementiert, die mit Platzhalterbildern, "Lorem Ipsum"-Standardtext und Steuerelementen gefüllt ist, die noch keine Funktion haben.</span><span class="sxs-lookup"><span data-stu-id="321c9-105">Suppose you've designed and implemented a nice looking UI filled with placeholder images, "lorem ipsum" boilerplate text, and controls that don't do anything yet.</span></span> <span data-ttu-id="321c9-106">Als Nächstes möchten Sie es von einem Prototyp-Entwurf in eine echten App umwandeln und mit echte Daten verbinden.</span><span class="sxs-lookup"><span data-stu-id="321c9-106">Next, you'll want to connect it to real data and transform it from a design prototype into a living app.</span></span> 

<span data-ttu-id="321c9-107">In diesem Lernprogramm erfahren Sie, wie Sie Ihre Textbausteine durch Datenbindungen ersetzen und andere direkte Links zwischen der Benutzeroberfläche und Ihren Daten erstellen.</span><span class="sxs-lookup"><span data-stu-id="321c9-107">In this tutorial, you'll learn how to replace your boilerplate with data bindings and create other direct links between your UI and your data.</span></span> <span data-ttu-id="321c9-108">Außerdem erfahren, wie Sie die Daten für die Anzeige formatieren oder konvertieren und die Benutzeroberfläche und die Daten synchron halten. Wenn Sie dieses Lernprogramm abgeschlossen haben, können Sie die Einfachheit und Organisation des XAML- und C#-Codes vereinfachen und organisieren, damit die Verwaltung und Erweiterung einfacher ist.</span><span class="sxs-lookup"><span data-stu-id="321c9-108">You'll also learn how to format or convert your data for display, and keep your UI and data in sync. When you complete this tutorial, you'll be able to improve the simplicity and organization of the XAML and C# code, making it easier to maintain and extend.</span></span>

<span data-ttu-id="321c9-109">Sie beginnen mit einer vereinfachten Version des PhotoLab-Beispiels.</span><span class="sxs-lookup"><span data-stu-id="321c9-109">You'll start with a simplified version of the PhotoLab sample.</span></span> <span data-ttu-id="321c9-110">Dieses Starterversion umfasst die vollständigen Datenebene sowie ein grundlegendes XAML-Layout und lässt viele kleinere Features aus, um den Code leichter zu durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="321c9-110">This starter version includes the complete data layer plus the basic XAML page layouts, and leaves out many features to make the code easier to browse around in.</span></span> <span data-ttu-id="321c9-111">In diesem Lernprogramm lernen Sie nicht das Erstellen der vollständigen App. Lesen Sie daher die endgültige Version zu Features durch wie z.B. benutzerdefinierte Animationen und Support für Ihre Telefon.</span><span class="sxs-lookup"><span data-stu-id="321c9-111">This tutorial doesn't build up to the complete app, so be sure to check out the final version to see features such as custom animations and phone support.</span></span> <span data-ttu-id="321c9-112">Die endgültige Version finden Sie im Stammordner des [Windows-appsample-photo-lab](https://github.com/Microsoft/Windows-appsample-photo-lab)-Repos.</span><span class="sxs-lookup"><span data-stu-id="321c9-112">You can find the final version in the root folder of the [Windows-appsample-photo-lab](https://github.com/Microsoft/Windows-appsample-photo-lab) repo.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="321c9-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="321c9-113">Prerequisites</span></span>

* <span data-ttu-id="321c9-114">[Visual Studio 2017 und die neueste Version des Windows 10-SDKs](https://developer.microsoft.com/windows/downloads).</span><span class="sxs-lookup"><span data-stu-id="321c9-114">[Visual Studio 2017 and the latest version of the Windows 10 SDK](https://developer.microsoft.com/windows/downloads).</span></span>

## <a name="part-0-get-the-code"></a><span data-ttu-id="321c9-115">Teil 0: Code herunterladen</span><span class="sxs-lookup"><span data-stu-id="321c9-115">Part 0: Get the code</span></span>
<span data-ttu-id="321c9-116">Der Startpunkt für diese Übung befindet sich im PhotoLab-Beispiel-Repository, im Ordner [xaml-basics-starting-points/data-binding](https://github.com/Microsoft/Windows-appsample-photo-lab/tree/master/xaml-basics-starting-points/data-binding).</span><span class="sxs-lookup"><span data-stu-id="321c9-116">The starting point for this lab is located in the PhotoLab sample repository, in the [xaml-basics-starting-points/data-binding](https://github.com/Microsoft/Windows-appsample-photo-lab/tree/master/xaml-basics-starting-points/data-binding) folder.</span></span> <span data-ttu-id="321c9-117">Nachdem Sie das Repository geklont/heruntergeladen haben, können Sie das Projekt bearbeiten, indem Sie PhotoLab.sln mit Visual Studio2017 öffnen.</span><span class="sxs-lookup"><span data-stu-id="321c9-117">After you've cloned or downloaded the repo, you can edit the project by opening PhotoLab.sln with Visual Studio 2017.</span></span>

<span data-ttu-id="321c9-118">Die PhotoLab-App besteht aus zwei Hauptseiten:</span><span class="sxs-lookup"><span data-stu-id="321c9-118">The PhotoLab app has two primary pages:</span></span>

<span data-ttu-id="321c9-119">**MainPage.xaml:** zeigt eine Ansicht der Foto-Galerie, zusammen mit einigen Informationen über jede Bilddatei an.</span><span class="sxs-lookup"><span data-stu-id="321c9-119">**MainPage.xaml:** displays a photo gallery view, along with some information about each image file.</span></span>
![MainPage](../design/basics/images/xaml-basics/mainpage.png)

<span data-ttu-id="321c9-121">**DetailPage.xaml:** zeigt ein einzelnes Foto an, nachdem es ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="321c9-121">**DetailPage.xaml:** displays a single photo after it has been selected.</span></span> <span data-ttu-id="321c9-122">Über ein Flyout-Menü kann das Foto bearbeitet, umbenannt und gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="321c9-122">A flyout editing menu allows the photo to be altered, renamed, and saved.</span></span>
![DetailPage](../design/basics/images/xaml-basics/detailpage.png)

## <a name="part-1-replace-the-placeholders"></a><span data-ttu-id="321c9-124">Teil 1: Ersetzen Sie die Platzhalter</span><span class="sxs-lookup"><span data-stu-id="321c9-124">Part 1: Replace the placeholders</span></span>

<span data-ttu-id="321c9-125">Hier erstellen Sie einmalige Bindungen der XAML-Datenvorlage, um echte Bilder und Metadaten von Bildern anstelle der Platzhalterinhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="321c9-125">Here you'll create one-time bindings in data-template XAML to display real images and image metadata instead of placeholder content.</span></span> 

<span data-ttu-id="321c9-126">Einmalige Bindungen eignen sich für schreibgeschützte, nicht veränderliche Daten d.h. sie sind sehr leistungsfähig und leicht zu erstellen und zeigen große Datensätze in den **GridView**- und **ListView**-Steuerelementen an.</span><span class="sxs-lookup"><span data-stu-id="321c9-126">One-time bindings are for read-only, unchanging data, which means they are high performance and easy to create, letting you display large data sets in **GridView** and **ListView** controls.</span></span> 

**<span data-ttu-id="321c9-127">Ersetzen Sie den Platzhalter mit einmaligen Bindungen</span><span class="sxs-lookup"><span data-stu-id="321c9-127">Replace the placeholders with one-time bindings</span></span>**

1. <span data-ttu-id="321c9-128">Öffnen Sie den Ordner „xaml-basics-startpunkte\data-binding” und starten Sie die Datei PhotoLab.sln.</span><span class="sxs-lookup"><span data-stu-id="321c9-128">Open the xaml-basics-starting-points\data-binding folder and launch the PhotoLab.sln file.</span></span> 

2. <span data-ttu-id="321c9-129">Stellen Sie sicher, dass Ihre Projektmappen-Plattform auf x86 oder x64 und nicht ARM festgelegt ist und führen Sie die App aus.</span><span class="sxs-lookup"><span data-stu-id="321c9-129">Make sure your Solution Platform is set to x86 or x64, not ARM, and then run the app.</span></span> <span data-ttu-id="321c9-130">Dies zeigt den Status der App mit UI-Platzhaltern an, bevor Bindungen hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="321c9-130">This shows the state of the app with UI placeholders, before bindings have been added.</span></span> 

    ![Ausführen der App mit Platzhalterbildern und Text](../design/basics/images/xaml-basics/gallery-with-placeholder-templates.png)

3. <span data-ttu-id="321c9-132">Öffnen Sie MainPage.xaml und suchen Sie nach einem **DataTemplate** mit dem Namen **ImageGridView_DefaultItemTemplate**.</span><span class="sxs-lookup"><span data-stu-id="321c9-132">Open MainPage.xaml and search for a **DataTemplate** named **ImageGridView_DefaultItemTemplate**.</span></span> <span data-ttu-id="321c9-133">Aktualisieren Sie diese Vorlage, um Datenbindungen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="321c9-133">You'll update this template to use data bindings.</span></span> 

    **<span data-ttu-id="321c9-134">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-134">Before:</span></span>**
    ```xaml
    <DataTemplate x:Key="ImageGridView_DefaultItemTemplate">
    ```

    <span data-ttu-id="321c9-135">Der Wert **x: Key** wird von **ImageGridView** verwendet, um diese Vorlage zum Anzeigen von Datenobjekten auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="321c9-135">The **x:Key** value is used by the **ImageGridView** to select this template for displaying data objects.</span></span> 

4. <span data-ttu-id="321c9-136">Fügen Sie der Vorlage einen Wert **x: DataType** hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-136">Add an **x:DataType** value to the template.</span></span> 

    **<span data-ttu-id="321c9-137">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-137">After:</span></span>**
    ```xaml
    <DataTemplate x:Key="ImageGridView_DefaultItemTemplate" 
                  x:DataType="local:ImageFileInfo">
    ```

    <span data-ttu-id="321c9-138">**x: DataType** gibt an, für welchen Typ dies eine Vorlage ist.</span><span class="sxs-lookup"><span data-stu-id="321c9-138">**x:DataType** indicates which type this is a template for.</span></span> <span data-ttu-id="321c9-139">In diesem Fall ist es eine Vorlage für die **ImageFileInfo**-Klasse (wobei "lokal:" den lokalen Namespace gemäß der Definition in einer xmlns-Deklaration im oberen Bereich der Datei angibt).</span><span class="sxs-lookup"><span data-stu-id="321c9-139">In this case, it's a template for the **ImageFileInfo** class (where "local:" indicates the local namespace, as defined in an xmlns declaration near the top of the file).</span></span>
    
    <span data-ttu-id="321c9-140">**x: DataType** wird benötigt, wenn **x: Bind**-Ausdrücke in einer Datenvorlage verwendet werden, wie nachfolgend beschrieben.</span><span class="sxs-lookup"><span data-stu-id="321c9-140">**x:DataType** is required when using **x:Bind** expressions in a data template, as described next.</span></span> 

5. <span data-ttu-id="321c9-141">Suchen Sie in **DataTemplate** das Element **Image** mit dem Namen **ItemImage** und ersetzen Sie seinen **Quell**-Wert wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="321c9-141">In the **DataTemplate**, find the **Image** element named **ItemImage** and replace its **Source** value as shown.</span></span> 

    **<span data-ttu-id="321c9-142">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-142">Before:</span></span>**
    ```xaml
    <Image x:Name="ItemImage" 
           Source="/Assets/StoreLogo.png" 
           Stretch="Uniform" />
    ```
    
    **<span data-ttu-id="321c9-143">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-143">After:</span></span>**
    ```xaml
    <Image x:Name="ItemImage" 
           Source="{x:Bind ImageSource}" 
           Stretch="Uniform" />
    ```
    
    <span data-ttu-id="321c9-144">**x: Name** identifiziert ein XAML-Element, damit Sie darauf an anderer Stelle im XAML-Code und im CodeBehind verweisen können.</span><span class="sxs-lookup"><span data-stu-id="321c9-144">**x:Name** identifies a XAML element so you can refer to it elsewhere in the XAML and in the code-behind.</span></span> 

    <span data-ttu-id="321c9-145">**x: Bind**-Ausdrücke geben der UI-Eigenschaft einen Wert, indem es einen Wert von einer **Datenobjekt**-Eigenschaft abruft.</span><span class="sxs-lookup"><span data-stu-id="321c9-145">**x:Bind** expressions supply a value to a UI property by getting the value from a **data-object** property.</span></span> <span data-ttu-id="321c9-146">In Vorlagen ist die angegebene Eigenschaft eine Eigenschaft, die im **x: DataType** festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="321c9-146">In templates, the property indicated is a property of whatever the **x:DataType** has been set to.</span></span> <span data-ttu-id="321c9-147">In diesem Fall ist die Datenquelle also die **ImageFileInfo.ImageSource**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="321c9-147">So in this case, the data source is the **ImageFileInfo.ImageSource** property.</span></span> 
    
    > [!NOTE] 
    > <span data-ttu-id="321c9-148">Der **x: Bind**-Wert informiert ebenfalls den Editor über den Datentyp, damit Sie IntelliSense anstatt verwenden können, anstatt den Namen der Eigenschaft in den **X: Bind**-Ausdruck einzugeben.</span><span class="sxs-lookup"><span data-stu-id="321c9-148">The **x:Bind** value also lets the editor know about the data type, so you can use IntelliSense instead of typing in the property name in an **x:Bind** expression.</span></span> <span data-ttu-id="321c9-149">Versuchen Sie diesen Vorgang auf dem gerade eingefügten Code durchzuführen: platzieren Sie den Cursor unmittelbar nach **x: Bind** und drücken Sie die LEERTASTE, um eine Liste der Eigenschaften anzuzeigen, für die Sie eine Bindung erstellen können.</span><span class="sxs-lookup"><span data-stu-id="321c9-149">Try it on the code you just pasted in: place the cursor just after **x:Bind** and press the Spacebar to see a list of properties you can bind to.</span></span>

6. <span data-ttu-id="321c9-150">Ersetzen Sie die Werte der anderen UI-Steuerelemente auf die gleiche Weise.</span><span class="sxs-lookup"><span data-stu-id="321c9-150">Replace the values of the other UI controls in the same way.</span></span> <span data-ttu-id="321c9-151">(Probieren Sie es mithilfe von IntelliSense anstatt Kopieren/Einfügen!)</span><span class="sxs-lookup"><span data-stu-id="321c9-151">(Try doing this with IntelliSense instead of copy/pasting!)</span></span>

    **<span data-ttu-id="321c9-152">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-152">Before:</span></span>**
    ```xaml
    <TextBlock Text="Placeholder" ... />
    <StackPanel ... >
        <TextBlock Text="PNG file" ... />
        <TextBlock Text="50 x 50" ... />
    </StackPanel>
    <telerikInput:RadRating Value="3" ... />
    ```
    
    **<span data-ttu-id="321c9-153">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-153">After:</span></span>**
    ```xaml
    <TextBlock Text="{x:Bind ImageTitle}" ... />
    <StackPanel ... >
        <TextBlock Text="{x:Bind ImageFileType}" ... />
        <TextBlock Text="{x:Bind ImageDimensions}" ... />
    </StackPanel>
    <telerikInput:RadRating Value="{x:Bind ImageRating}" ... />
    ```

<span data-ttu-id="321c9-154">Führen Sie die App aus, um herauszufinden, wie sie bisher aussieht.</span><span class="sxs-lookup"><span data-stu-id="321c9-154">Run the app to see how it looks so far.</span></span> <span data-ttu-id="321c9-155">Keine weiteren Platzhalter!</span><span class="sxs-lookup"><span data-stu-id="321c9-155">No more placeholders!</span></span> <span data-ttu-id="321c9-156">Das ist ein guter Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="321c9-156">We're off to a good start.</span></span> 

![Die App mit richtigen Bildern und Text anstelle von Platzhaltern ausführen](../design/basics/images/xaml-basics/gallery-with-populated-templates.png)

> [!Note]
> <span data-ttu-id="321c9-158">Wenn Sie weiter experimentieren möchten, versuchen Sie, der Datenvorlage einen neuen TextBlock hinzuzufügen, und verwenden Sie den x: Bind IntelliSense-Trick, um eine Eigenschaft zu suchen, die Sie anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="321c9-158">If you want to experiment further, try adding a new TextBlock to the data template, and use the x:Bind IntelliSense trick to find a property to display.</span></span> 

## <a name="part-2-use-binding-to-connect-the-gallery-ui-to-the-images"></a><span data-ttu-id="321c9-159">Teil 2: Verwenden der Bindung,um die Galerie-UI mit Bildern zu verbinden</span><span class="sxs-lookup"><span data-stu-id="321c9-159">Part 2: Use binding to connect the gallery UI to the images</span></span>

<span data-ttu-id="321c9-160">Hier erstellen Sie einmalige Bindungen auf XAML-Seiten für die Verbindung der Fotogalerie-Ansicht mit der Bildersammlung und ersetzen dadurch den vorhandenen prozeduralen Code, der dies im CodeBehind durchführt.</span><span class="sxs-lookup"><span data-stu-id="321c9-160">Here, you'll create one-time bindings in page XAML to connect the gallery view to the image collection, replacing the existing procedural code that does this in code-behind.</span></span> <span data-ttu-id="321c9-161">Erstellen Sie außerdem eine Schaltfläche **Löschen**, um zu sehen, wie sich die Fotogalerie-Ansicht ändert, wenn Sie Bilder aus der Sammlung entfernen.</span><span class="sxs-lookup"><span data-stu-id="321c9-161">You'll also create a **Delete** button to see how the gallery view changes when images are removed from the collection.</span></span> <span data-ttu-id="321c9-162">Gleichzeitig erfahren Sie, wie Ereignisse für mehr Flexibilität als herkömmliche Ereignishandler an Ereignishandler gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="321c9-162">At the same time, you'll learn how to bind events to event handlers for more flexibility than that provided by traditional event handlers.</span></span> 

<span data-ttu-id="321c9-163">Alle Bindungen, die bisher behandelt wurden, befinden sich innerhalb der Datenvorlagen und beziehen sich auf Eigenschaften der Klasse, die vom Wert **x: DataType** angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="321c9-163">All the bindings covered so far are inside data templates and refer to properties of the class indicated by the **x:DataType** value.</span></span> <span data-ttu-id="321c9-164">Was ist mit den Rest des XAML-Codes auf der Seite?</span><span class="sxs-lookup"><span data-stu-id="321c9-164">What about the rest of the XAML in your page?</span></span> 

<span data-ttu-id="321c9-165">**x: Bind**-Ausdrücke außerhalb von Datenvorlagen sind immer an die Seite selbst gebunden.</span><span class="sxs-lookup"><span data-stu-id="321c9-165">**x:Bind** expressions outside of data templates are always bound to the page itself.</span></span> <span data-ttu-id="321c9-166">Dies bedeutet, dass Sie auf alles im CodeBehind oder auf XAML verweisen können, einschließlich der benutzerdefinierten Eigenschaften und der Eigenschaften anderer UI-Steuerelemente auf der Seite (solange sie einen Wert **x: Name** haben).</span><span class="sxs-lookup"><span data-stu-id="321c9-166">This means you can reference anything you put in code-behind or declare in XAML, including custom properties and properties of other UI controls on the page (as long as they have an **x:Name** value).</span></span> 

<span data-ttu-id="321c9-167">Im PhotoLab-Beispiel kann eine solche Bindung verwendet werden, um das Haupt-**GridView**-Steuerelement direkt mit der Sammlung von Bildern zu verbinden, anstatt dies im CodeBehind durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="321c9-167">In the PhotoLab sample, one use for a binding like this is to connect the main **GridView** control directly to the collection of images, instead of doing it in code-behind.</span></span> <span data-ttu-id="321c9-168">Später sehen Sie weitere Beispiele.</span><span class="sxs-lookup"><span data-stu-id="321c9-168">Later, you'll see other examples.</span></span> 

**<span data-ttu-id="321c9-169">Binden des Haupt-Steuerelements „GridView” an die Bildersammlung</span><span class="sxs-lookup"><span data-stu-id="321c9-169">Bind the main GridView control to the Images collection</span></span>**

1. <span data-ttu-id="321c9-170">Suchen Sie unter MainPage.xaml.cs die **OnNavigatedTo**-Methode und entfernen Sie den Code, der \*\*ItemsSource \*\* festlegt.</span><span class="sxs-lookup"><span data-stu-id="321c9-170">In MainPage.xaml.cs, find the **OnNavigatedTo** method and remove the code that sets **ItemsSource**.</span></span>

    **<span data-ttu-id="321c9-171">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-171">Before:</span></span>**
    ```c#
    ImageGridView.ItemsSource = Images;
    ```

    **<span data-ttu-id="321c9-172">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-172">After:</span></span>**
    ```c#
    // Replaced with XAML binding:
    // ImageGridView.ItemsSource = Images;
    ```

2. <span data-ttu-id="321c9-173">Suchen Sie in MainPage.xaml das **GridView** mit dem Namen **ImageGridView** und fügen Sie ein **ItemsSource**-Attribut hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-173">In MainPage.xaml, find the **GridView** named **ImageGridView** and add an **ItemsSource** attribute.</span></span> <span data-ttu-id="321c9-174">Verwenden Sie für den Wert einen **X: Bind**-Ausdruck, der sich auf die **Bild**-Eigenschaft bezieht, die im CodeBehind implementiert wurde.</span><span class="sxs-lookup"><span data-stu-id="321c9-174">For the value, use an **x:Bind** expression that refers to the **Images** property implemented in code-behind.</span></span> 

    **<span data-ttu-id="321c9-175">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-175">Before:</span></span>**
    ```xaml
    <GridView x:Name="ImageGridView" 
    ```

    **<span data-ttu-id="321c9-176">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-176">After:</span></span>**
    ```xaml
    <GridView x:Name="ImageGridView" 
              ItemsSource="{x:Bind Images}" 
    ```

    <span data-ttu-id="321c9-177">Die **Bild**-Eigenschaft ist vom Typ **ObservableCollection\ < ImageFileInfo\>**, sodass die einzelnen Elemente, in unter **GridView** angezeigt werden vom Typ **ImageFileInfo** sind.</span><span class="sxs-lookup"><span data-stu-id="321c9-177">The **Images** property is of type **ObservableCollection\<ImageFileInfo\>**, so the individual items displayed in the **GridView** are of type **ImageFileInfo**.</span></span> <span data-ttu-id="321c9-178">Dies entspricht dem **x: DataType**-Wert, der in Teil 1 beschrieben wurde.</span><span class="sxs-lookup"><span data-stu-id="321c9-178">This matches the **x:DataType** value described in Part 1.</span></span> 

<span data-ttu-id="321c9-179">Alle Bindungen, die wir haben bisher untersucht haben, sind einmalige, schreibgeschützte Bindungen und entsprechen dem Standardverhalten für nur **x: Bind**-Ausdrücke.</span><span class="sxs-lookup"><span data-stu-id="321c9-179">All the bindings we've looked at so far are one-time, read-only bindings, which is the default behavior for plain **x:Bind** expressions.</span></span> <span data-ttu-id="321c9-180">Die Daten werden nur bei der Initialisierung hochgeladen, wodurch High-End-Bindungen entstehen – dies eignet sich ideal für die Unterstützung von mehreren komplexen Ansichten großer Datensätze.</span><span class="sxs-lookup"><span data-stu-id="321c9-180">The data is loaded only at initialization, which makes for high-performance bindings - perfect for supporting multiple, complex views of large data sets.</span></span> 

<span data-ttu-id="321c9-181">Sogar die **ItemsSource**-Bindung, die Sie gerade hinzugefügt haben ist nur eine einmalige, schreibgeschützte Bindung für einen statischen Wert der Eigenschaft, aber hier gibt es einen wichtigen Unterschied.</span><span class="sxs-lookup"><span data-stu-id="321c9-181">Even the **ItemsSource** binding you just added is a one-time, read-only binding to an unchanging property value, but there's an important distinction to make here.</span></span> <span data-ttu-id="321c9-182">Der sich nicht ändernde Wert der **Bild**-Eigenschaft ist eine einzelne, spezifische Instanz einer Sammlung, die einmal, wie hier gezeigt, initialisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="321c9-182">The unchanging value of the **Images** property is a single, specific instance of a collection, initialized once as shown here.</span></span>

```Csharp
private ObservableCollection<ImageFileInfo> Images { get; }
    = new ObservableCollection<ImageFileInfo>();
```

<span data-ttu-id="321c9-183">Der **Bild**-Eigenschaftswert ändert sich nie, aber da die Eigenschaft vom Typ **ObservableCollection\<T\>** ist können sich die *Inhalte* der Sammlung ändern, und die Bindung wird automatisch die Änderungen erkennen und die Benutzeroberfläche aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-183">The **Images** property value never changes, but because the property is of type **ObservableCollection\<T\>**, the *contents* of the collection can change, and the binding will automatically notice the changes and update the UI.</span></span> 

<span data-ttu-id="321c9-184">Um dies zu testen, werden wir vorübergehend eine Schaltfläche hinzufügen, die das derzeit ausgewählte Bild löscht.</span><span class="sxs-lookup"><span data-stu-id="321c9-184">To test this, we're going to temporarily add a button that deletes the currently-selected image.</span></span> <span data-ttu-id="321c9-185">In der endgültigen Version ist diese Schaltfläche nicht vorhanden, da die Auswahl eines Bildes Sie zu einer Detailseite führt.</span><span class="sxs-lookup"><span data-stu-id="321c9-185">This button isn't in the final version because selecting an image will take you to a detail page.</span></span> <span data-ttu-id="321c9-186">Das Verhalten von **ObservableCollection\<T\>** ist jedoch im letzten PhotoLab-Beispiel wichtig, da der XAML-Code im Seitenkonstruktor initialisiert wird (über den **InitializeComponent**-Methodenaufruf). Die **Bild**-Sammlung wird unten in der **OnNavigatedTo**-Methode aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="321c9-186">However, the behavior of **ObservableCollection\<T\>** is still important in the final PhotoLab sample because the XAML is initialized in the page constructor (through the **InitializeComponent** method call), but the **Images** collection is populated later in the **OnNavigatedTo** method.</span></span> 

**<span data-ttu-id="321c9-187">Schaltfläche „Löschen” hinzufügen</span><span class="sxs-lookup"><span data-stu-id="321c9-187">Add a delete button</span></span>**

1. <span data-ttu-id="321c9-188">Suchen Sie in MainPage.xaml die **CommandBar** mit dem Namen **MainCommandBar** und fügen Sie eine neue Schaltfläche vor der Schaltfläche zum Zoomen hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-188">In MainPage.xaml, find the **CommandBar** named **MainCommandBar** and add a new button before the zoom button.</span></span> <span data-ttu-id="321c9-189">(Die Zoomsteuerelemente funktionieren noch nicht.</span><span class="sxs-lookup"><span data-stu-id="321c9-189">(The zoom controls don't work yet.</span></span> <span data-ttu-id="321c9-190">Sie können diese im nächsten Teil des Lernprogramms anschließen.)</span><span class="sxs-lookup"><span data-stu-id="321c9-190">You'll hook those up in the next part of the tutorial.)</span></span>

    ```xaml
    <AppBarButton Icon="Delete"
                  Label="Delete selected image"
                  Click="{x:Bind DeleteSelectedImage}" />
    ```

    <span data-ttu-id="321c9-191">Wenn Sie bereits mit XAML vertraut sind, sieht dieser **Klick**-Wert möglicherweise ungewöhnlich aus.</span><span class="sxs-lookup"><span data-stu-id="321c9-191">If you're already familiar with XAML, this **Click** value might look unusual.</span></span> <span data-ttu-id="321c9-192">In früheren Versionen von XAML mussten Sie dies zu einer Methode mit einer bestimmten Ereignishandler-Signatur hinzufügen, einschließlich der Parameter für den Absender des Ereignisses und eines ereignisspezifischen Argumentobjekts.</span><span class="sxs-lookup"><span data-stu-id="321c9-192">In previous versions of XAML, you had to set this to a method with a specific event-handler signature, typically including parameters for the event sender and an event-specific arguments object.</span></span> <span data-ttu-id="321c9-193">Sie können diese Technik auch weiterhin verwenden, wenn Sie Ereignisargumente benötigen, aber mit x: Bind können Sie keine Verbindung zu anderen Methoden herstellen.</span><span class="sxs-lookup"><span data-stu-id="321c9-193">You can still use this technique when you need the event arguments, but with x:Bind, you can connect to other methods, too.</span></span> <span data-ttu-id="321c9-194">Wenn Sie beispielsweise die Ereignisdaten nicht benötigen, können Sie keine Verbindung zu Methoden herstellen, die keine Parameter haben, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="321c9-194">For example, if you don't need the event data, you can connect to methods that have no parameters, like we do here.</span></span>

    <!-- TODO add doc links about event binding - and doc links in general? -->

2. <span data-ttu-id="321c9-195">Fügen Sie in MainPage.xaml.cs die **DeleteSelectedImage**-Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-195">In MainPage.xaml.cs, add the **DeleteSelectedImage** method.</span></span>

    ```c#
    private void DeleteSelectedImage() =>
        Images.Remove(ImageGridView.SelectedItem as ImageFileInfo);
    ```

    <span data-ttu-id="321c9-196">Diese Methode löscht das ausgewählte Bild aus der **Bild**-Sammlung.</span><span class="sxs-lookup"><span data-stu-id="321c9-196">This method simply deletes the selected image from the **Images** collection.</span></span> 

<span data-ttu-id="321c9-197">Führen Sie jetzt die App aus und verwenden Sie die Schaltfläche, um ein paar Bilder zu löschen.</span><span class="sxs-lookup"><span data-stu-id="321c9-197">Now run the app and use the button to delete a few images.</span></span> <span data-ttu-id="321c9-198">Wie Sie sehen, wird die Benutzeroberfläche automatisch aktualisiert, Dank der Datenbindung und dem **ObservableCollection\<T\>**-Typ.</span><span class="sxs-lookup"><span data-stu-id="321c9-198">As you can see, the UI is updated automatically, thanks to data binding and the **ObservableCollection\<T\>** type.</span></span> 

> [!Note]
> <span data-ttu-id="321c9-199">Hier ist eine schwierigere Herausforderung: versuchen Sie, zwei Schaltflächen hinzuzufügen, die das ausgewählte Bild in der Liste nach oben oder unten verschieben, und binden Sie dann das x: Bind-Klick-Ereignisse dieser zwei neuen Methoden an DeleteSelectedImage.</span><span class="sxs-lookup"><span data-stu-id="321c9-199">For a challenge, try adding two buttons that move the selected image up or down in the list, then x:Bind their Click events to two new methods similar to DeleteSelectedImage.</span></span>
 
## <a name="part-3-set-up-the-zoom-slider"></a><span data-ttu-id="321c9-200">Teil 3: Einrichten des Zoom-Schiebereglers</span><span class="sxs-lookup"><span data-stu-id="321c9-200">Part 3: Set up the zoom slider</span></span> 

<span data-ttu-id="321c9-201">In dieser Phase erstellen wir unidirektionale Bindungen von einem Steuerelement in der Datenvorlage zum Zoomschieberegler, der sich außerhalb der Vorlage befindet.</span><span class="sxs-lookup"><span data-stu-id="321c9-201">In this part, you'll create one-way bindings from a control in the data template to the zoom slider, which is outside the template.</span></span> <span data-ttu-id="321c9-202">Außerdem erfahren Sie, dass Sie die Datenbindung mit vielen Eigenschaften des Steuerelements verwenden können, nicht nur die offensichtlichsten, wie **TextBlock.Text** und **Image.Source**.</span><span class="sxs-lookup"><span data-stu-id="321c9-202">You'll also learn that you can use data binding with many control properties, not just the most obvious ones like **TextBlock.Text** and **Image.Source**.</span></span> 

**<span data-ttu-id="321c9-203">Binden Sie die Datenvorlage Bild an den Zoomschieberegler an</span><span class="sxs-lookup"><span data-stu-id="321c9-203">Bind the image data template to the zoom slider</span></span>**

* <span data-ttu-id="321c9-204">Suchen Sie ein **DataTemplate** mit dem Namen **ImageGridView_DefaultItemTemplate** und ersetzen Sie die Werte von **Höhe** und **Breite** des **Raster**-Steuerelements im oberen Bereich der Vorlage.</span><span class="sxs-lookup"><span data-stu-id="321c9-204">Find the **DataTemplate** named **ImageGridView_DefaultItemTemplate** and replace the **Height** and **Width** values of the **Grid** control at the top of the template.</span></span>

    **<span data-ttu-id="321c9-205">Vorher</span><span class="sxs-lookup"><span data-stu-id="321c9-205">Before</span></span>**
    ```xaml
    <DataTemplate x:Key="ImageGridView_DefaultItemTemplate" 
                  x:DataType="local:ImageFileInfo">
        <Grid Height="200"
              Width="200"
              Margin="{StaticResource LargeItemMargin}">
    ```
    
    **<span data-ttu-id="321c9-206">Nachher</span><span class="sxs-lookup"><span data-stu-id="321c9-206">After</span></span>**
    ```xaml
    <DataTemplate x:Key="ImageGridView_DefaultItemTemplate" 
                  x:DataType="local:ImageFileInfo">
        <Grid Height="{Binding Value, ElementName=ZoomSlider}"
              Width="{Binding Value, ElementName=ZoomSlider}"
              Margin="{StaticResource LargeItemMargin}">
    ```
    
    <!-- TODO talk about dependency properties --> 
    
    <span data-ttu-id="321c9-207">Haben Sie bemerkt, dass dies **Bindungs**-Ausdrücke sind und nicht **x: Bind**-Ausdrücke?</span><span class="sxs-lookup"><span data-stu-id="321c9-207">Did you notice that these are **Binding** expressions, and not **x:Bind** expressions?</span></span> <span data-ttu-id="321c9-208">Dies ist die alte Vorgehensweise der Nutzung von Datenbindungen, und diese ist veraltet.</span><span class="sxs-lookup"><span data-stu-id="321c9-208">This is the old way of doing data bindings, and it's mostly obsolete.</span></span> <span data-ttu-id="321c9-209">**x: Bind** hat fast alle Funktionen von **Bindung** und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="321c9-209">**x:Bind** does nearly everything that **Binding** does, and more.</span></span> <span data-ttu-id="321c9-210">Wenn Sie jedoch **x: Bind** in einer Datenvorlage verwenden, bindet sie sich an den Typ, der im Wert **x: DataType** deklariert ist.</span><span class="sxs-lookup"><span data-stu-id="321c9-210">However, when you use **x:Bind** in a data template, it binds to the type declared in the **x:DataType** value.</span></span> <span data-ttu-id="321c9-211">Wie binden Sie etwas in der Vorlage an etwas auf der XAML-Seite oder im CodeBehind?</span><span class="sxs-lookup"><span data-stu-id="321c9-211">So how do you bind something in the template to something in the page XAML or in code-behind?</span></span> <span data-ttu-id="321c9-212">Müssen Sie einen veralteten **Bindungs**-Ausdruck verwenden.</span><span class="sxs-lookup"><span data-stu-id="321c9-212">You must use an old-style **Binding** expression.</span></span> 
    
    <span data-ttu-id="321c9-213">**Bindungs**-Ausdrücke erkennen den **x: DataType**-Wert nicht an, aber diese **Bindungs**-Ausdrücken haben **ElementName**-Werte, die nahezu auf die gleiche Weise funktionieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-213">**Binding** expressions don't recognize the **x:DataType** value, but these **Binding** expressions have **ElementName** values that work almost the same way.</span></span> <span data-ttu-id="321c9-214">Diese teilen dem Bindungsmodul mit, dass **Binding Value** eine Bindung für die **Wert**-Eigenschaft für das angegebene Element auf der Seite ist (d.h. das Element mit dem **x: Name**-Wert).</span><span class="sxs-lookup"><span data-stu-id="321c9-214">These tell the binding engine that **Binding Value** is a binding to the **Value** property of the specified element on the page (that is, the element with that **x:Name** value).</span></span> <span data-ttu-id="321c9-215">Wenn Sie eine Eigenschaft im CodeBehind binden möchten, würde es etwa so aussehen ```{Binding MyCodeBehindProperty, ElementName=page}``` wobei **Seite** sich auf den **x: Name**-Wert bezieht, der im Element **Seite** in XAML festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="321c9-215">If you want to bind to a property in code-behind, it would look something like ```{Binding MyCodeBehindProperty, ElementName=page}``` where **page** refers to the **x:Name** value set in the **Page** element in XAML.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="321c9-216">In der Standardeinstellung sind **Bindungs**-Ausdrücke *unilateral*, was bedeutet, dass sie die Benutzeroberfläche automatisch aktualisieren, wenn die Eigenschaft des gebundenen Werts sich ändert.</span><span class="sxs-lookup"><span data-stu-id="321c9-216">By default, **Binding** expressions are one-*way*, meaning that they will automatically update the UI when the bound property value changes.</span></span> 
    > 
    > <span data-ttu-id="321c9-217">Im Gegensatz dazu ist die Standardeinstellung für **x: Bind** *einmalig*, was bedeutet, dass jegliche Änderungen an der gebundenen Eigenschaft ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="321c9-217">In contrast, the default for **x:Bind** is one-*time*, meaning that any changes to the bound property are ignored.</span></span> <span data-ttu-id="321c9-218">Dies ist die Standardeinstellung, da es die leistungsstärkste Option ist und die meisten Bindungen zu statischen, schreibgeschützten Daten erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="321c9-218">This is the default because it's the most high-performance option, and most bindings are to static, read-only data.</span></span> 
    >
    > <span data-ttu-id="321c9-219">Hier gilt folgende Lektion: die bei Verwendung von **X: Bind** mit Eigenschaften, deren Werte sich ändern kann, müssen Sie ```Mode=OneWay```oder ```Mode=TwoWay``` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="321c9-219">The lesson here is that if you use **x:Bind** with properties that can change their values, be sure to add ```Mode=OneWay``` or ```Mode=TwoWay```.</span></span> <span data-ttu-id="321c9-220">Im nächsten Abschnitt sehen Sie ein Beispiel dafür.</span><span class="sxs-lookup"><span data-stu-id="321c9-220">You'll see examples of this in the next section.</span></span>

<span data-ttu-id="321c9-221">Führen Sie die App aus und verwenden Sie den Schieberegler, um die Größe der Image-Vorlage zu ändern.</span><span class="sxs-lookup"><span data-stu-id="321c9-221">Run the app and use the slider to change the image-template dimensions.</span></span> <span data-ttu-id="321c9-222">Wie Sie sehen können, ist der Effekt auch ohne viel Code imposant.</span><span class="sxs-lookup"><span data-stu-id="321c9-222">As you can see, the effect is pretty powerful without needing much code.</span></span> 

![Die App mit angezeigtem Zoomschieberegler ausführen](../design/basics/images/xaml-basics/gallery-with-zoom-control.png)

> [!NOTE]
> <span data-ttu-id="321c9-224">Hier ist eine Herausforderung: versuchen Sie andere UI-Eigenschaften an die **Wert**-Eigenschaft des Zoomschiebereglers oder eines anderen Reglers zu binden, den Sie nach dem Zoomschieberegler hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="321c9-224">For a challenge, try binding other UI properties to the zoom slider **Value** property, or to other sliders that you add after the zoom slider.</span></span> <span data-ttu-id="321c9-225">Sie können z.B. die **FontSize**-Eigenschaft der **TitleTextBlock** auf einen neuen Schieberegler mit einem Standardwert von **24** binden.</span><span class="sxs-lookup"><span data-stu-id="321c9-225">For example, you could bind the **FontSize** property of the **TitleTextBlock** to a new slider with a default value of **24**.</span></span> <span data-ttu-id="321c9-226">Achten Sie darauf, dass Sie angemessene minimale und maximalen Werte festlegen.</span><span class="sxs-lookup"><span data-stu-id="321c9-226">Be sure to set reasonable minimum and maximum values.</span></span>

## <a name="part-4-improve-the-zoom-experience"></a><span data-ttu-id="321c9-227">Teil 4: Verbessern der Zoomerfahrung</span><span class="sxs-lookup"><span data-stu-id="321c9-227">Part 4: Improve the zoom experience</span></span> 

<span data-ttu-id="321c9-228">In diesem Abschnitt fügen Sie dem CodeBehind eine benutzerdefinierte **ItemSize**-Eigenschaft hinzu und erstellen eine unidirektionale Bindungen von der Bildvorlage auf die neue Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="321c9-228">In this part, you'll add a custom **ItemSize** property to code-behind and create one-way bindings from the image template to the new property.</span></span> <span data-ttu-id="321c9-229">Der **ItemSize**-Wert wird vom Zoomschieberegler und anderen Faktoren wie z.B. dem Umschalten von **Bildschirmgröße anpassen** und der Fenstergröße aktualisiert, die so eine präzisere Erfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="321c9-229">The **ItemSize** value will be updated by the zoom slider and other factors such as the **Fit to screen** toggle and the window size, making for a more refined experience.</span></span> 

<span data-ttu-id="321c9-230">Im Gegensatz zu integrierten Steuerelement-Eigenschaften werden Ihre benutzerdefinierten Eigenschaften nicht automatisch die Benutzeroberfläche aktualisieren, auch nicht bei unidirektionale und bidirektionale Bindungen.</span><span class="sxs-lookup"><span data-stu-id="321c9-230">Unlike built-in control properties, your custom properties do not automatically update the UI, even with one-way and two-way bindings.</span></span> <span data-ttu-id="321c9-231">Sie funktionieren gut **einmaligen** Bindungen, aber wenn Sie Ihre Änderungen tatsächlich auf der Benutzeroberfläche anzeigen möchten, müssen Sie zuerst einige Aufgaben ausführen.</span><span class="sxs-lookup"><span data-stu-id="321c9-231">They work fine with one-**time** bindings, but if you want your property changes to actually show up in your UI, you need to do some work.</span></span> 

**<span data-ttu-id="321c9-232">Erstellen Sie die ItemSize-Eigenschaft, damit die Benutzeroberfläche aktualisiert wird</span><span class="sxs-lookup"><span data-stu-id="321c9-232">Create the ItemSize property so that it updates the UI</span></span>**

1. <span data-ttu-id="321c9-233">In MainPage.xaml.cs, ändern Sie die Signatur der **MainPage**-Klasse, damit die **INotifyPropertyChanged**-Schnittstelle implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="321c9-233">In MainPage.xaml.cs, change the signature of the **MainPage** class so that it implements the **INotifyPropertyChanged** interface.</span></span>

    **<span data-ttu-id="321c9-234">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-234">Before:</span></span>**
    ```c#
    public sealed partial class MainPage : Page
    ```

    **<span data-ttu-id="321c9-235">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-235">After:</span></span>**
    ```c#
    public sealed partial class MainPage : Page, INotifyPropertyChanged
    ```

    <span data-ttu-id="321c9-236">Dies informiert das Bindungssystem, das auf „MainPage” ein „PropertyChanged”-Ereignis durchgeführt wurde (wird als Nächstes hinzugefügt), auf das Bindungen horchen können, um die UI zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-236">This informs the binding system that MainPage has a PropertyChanged event (added next) that bindings can listen for in order to update the UI.</span></span> 

2. <span data-ttu-id="321c9-237">Fügen Sie ein **PropertyChanged**-Ereignis der **MainPage**-Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-237">Add a **PropertyChanged** event to the **MainPage** class.</span></span>

    ```c#
    public event PropertyChangedEventHandler PropertyChanged;
    ```

    <span data-ttu-id="321c9-238">Dieses Ereignis bietet die vollständige Implementierung, die von der **INotifyPropertyChanged**-Schnittstelle benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="321c9-238">This event provides the complete implementation required by the **INotifyPropertyChanged** interface.</span></span> <span data-ttu-id="321c9-239">Damit es wirksam wird, müssen Sie explizit das Ereignis in Ihren benutzerdefinierten Eigenschaften auslösen.</span><span class="sxs-lookup"><span data-stu-id="321c9-239">However, for it to have any effect, you must explicitly raise the event in your custom properties.</span></span> 

3. <span data-ttu-id="321c9-240">Fügen Sie eine **ItemSize**-Eigenschaft hinzu und lösen Sie das **PropertyChanged**-Ereignis in seinem Setter.</span><span class="sxs-lookup"><span data-stu-id="321c9-240">Add an **ItemSize** property and raise the **PropertyChanged** event in its setter.</span></span>

    ```c#
    public double ItemSize
    {
        get => _itemSize;
        set
        {
            if (_itemSize != value)
            {
                _itemSize = value;
                PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(nameof(ItemSize)));
            }
        }
    }
    private double _itemSize;
    ```

    <span data-ttu-id="321c9-241">Die **ItemSize**-Eigenschaft enthält den Wert eines privaten **_itemSize**-Felds.</span><span class="sxs-lookup"><span data-stu-id="321c9-241">The **ItemSize** property exposes the value of a private **_itemSize** field.</span></span> <span data-ttu-id="321c9-242">Durch Verwenden eines solchen Sicherungsfelds kann die Eigenschaft überprüfen, ob ein neuer Wert identisch mit dem alten Wert ist, bevor es möglicherweise unnötig ein **PropertyChanged**-Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="321c9-242">Using a backing field like this enables the property to check whether a new value is the same as the old value before it raises a potentially unnecessary **PropertyChanged** event.</span></span>

    <span data-ttu-id="321c9-243">Das Ereignis selbst wird durch die **Invoke**-Methode ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="321c9-243">The event itself is raised by the **Invoke** method.</span></span> <span data-ttu-id="321c9-244">Das Fragezeichen überprüft, ob das **PropertyChanged**-Ereignis null ist – d.h., ob bereits ein Ereignishandler hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="321c9-244">The question mark checks whether the **PropertyChanged** event is null - that is, whether any event handlers have been added yet.</span></span> <span data-ttu-id="321c9-245">Jede unidirektionale oder bidirektionale Bindung fügt einen Ereignishandler in den Hintergrund hinzu, aber wenn niemand horcht, geschieht hier nichts mehr.</span><span class="sxs-lookup"><span data-stu-id="321c9-245">Every one-way or two-way binding adds an event handler behind the scenes, but if no one is listening, nothing more would happen here.</span></span> <span data-ttu-id="321c9-246">Wenn **PropertyChanged** nicht null ist, wird **Invoke** mit einem Verweis auf die Ereignisquelle (die Seite selbst, die durch das Schlagwort **dies** dargestellt wird) und einem **Ereignisargument**-Objekt aufgerufen , das den Namen der Eigenschaft anzeigt.</span><span class="sxs-lookup"><span data-stu-id="321c9-246">If **PropertyChanged** isn't null, however, then **Invoke** is called with a reference to the event source (the page itself, represented by the **this** keyword) and an **event-args** object that indicates the name of the property.</span></span> <span data-ttu-id="321c9-247">Mit diesen Informationen, wird jede unidirektionale oder bidirektionalen Bindungen für die **ItemSize**-Eigenschaft über jegliche Änderungen informiert, damit die gebundene UI aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="321c9-247">With this info, any one-way or two-way bindings to the **ItemSize** property will be informed of any changes so they can update the bound UI.</span></span> 

4. <span data-ttu-id="321c9-248">Suchen Sie in MainPage.xaml ein **DataTemplate** mit dem Namen **ImageGridView_DefaultItemTemplate** und ersetzen Sie die Werte von **Höhe** und **Breite** des **Raster**-Steuerelements im oberen Bereich der Vorlage.</span><span class="sxs-lookup"><span data-stu-id="321c9-248">In MainPage.xaml, find the **DataTemplate** named **ImageGridView_DefaultItemTemplate** and replace the **Height** and **Width** values of the **Grid** control at the top of the template.</span></span> <span data-ttu-id="321c9-249">(Wenn Sie im vorherigen Teil dieses Lernprogramms die Bindungen von einem Steuerelement zum anderen erstellt haben, müssen Sie als einzige Änderungen **Wert** durch **ItemSize** und **ZoomSlider** durch **Seite** ersetzen.</span><span class="sxs-lookup"><span data-stu-id="321c9-249">(If you did the control-to-control binding in the previous part of this tutorial, the only changes are to replace **Value** with **ItemSize** and **ZoomSlider** with **page**.</span></span> <span data-ttu-id="321c9-250">Führen Sie dies für die Höhe und Breite aus!)</span><span class="sxs-lookup"><span data-stu-id="321c9-250">Be sure to do this for both Height and Width!)</span></span>

    **<span data-ttu-id="321c9-251">Vorher</span><span class="sxs-lookup"><span data-stu-id="321c9-251">Before</span></span>**
    ```xaml
    <DataTemplate x:Key="ImageGridView_DefaultItemTemplate" 
                  x:DataType="local:ImageFileInfo">
        <Grid Height="{Binding Value, ElementName=ZoomSlider}"
            Width="{Binding Value, ElementName=ZoomSlider}"
            Margin="{StaticResource LargeItemMargin}">
    ```
    
    **<span data-ttu-id="321c9-252">Nachher</span><span class="sxs-lookup"><span data-stu-id="321c9-252">After</span></span>**
    ```xaml
    <DataTemplate x:Key="ImageGridView_DefaultItemTemplate" 
                  x:DataType="local:ImageFileInfo">
        <Grid Height="{Binding ItemSize, ElementName=page}"
              Width="{Binding ItemSize, ElementName=page}"
              Margin="{StaticResource LargeItemMargin}">
    ```

<span data-ttu-id="321c9-253">Da die Benutzeroberfläche auf die Änderung von **ItemSize** reagieren kann, müssen Sie tatsächlich einige Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="321c9-253">Now that the UI can respond to **ItemSize** changes, you need to actually make some changes.</span></span> <span data-ttu-id="321c9-254">Wie bereits erwähnt, wird der **ItemSize**-Wert vom aktuellen Status der verschiedenen UI-Steuerelemente berechnet, aber die Berechnung muss ausgeführt werden, wenn sich der Zustand dieser Steuerelemente ändert.</span><span class="sxs-lookup"><span data-stu-id="321c9-254">As mentioned previously, the **ItemSize** value is calculated from the current state of various UI controls, but the calculation must be performed whenever those controls change state.</span></span> <span data-ttu-id="321c9-255">Zu diesem Zweck können Sie die Ereignisbindung verwenden, damit bestimmte UI-Änderungen eine Hilfsmethode aufrufen, die **ItemSize** aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="321c9-255">To do this, you'll use event binding so that certain UI changes will call a helper method that updates **ItemSize**.</span></span> 

**<span data-ttu-id="321c9-256">Aktualisieren Sie den Wert der ItemSize-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="321c9-256">Update the ItemSize property value</span></span>**

1. <span data-ttu-id="321c9-257">Fügen Sie MainPage.xaml.cs die **DetermineItemSize**-Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-257">Add the **DetermineItemSize** method to MainPage.xaml.cs.</span></span>

    ```c#
    private void DetermineItemSize()
    {
        if (FitScreenToggle != null
            && FitScreenToggle.IsOn == true
            && ImageGridView != null
            && ZoomSlider != null)
        {
            // The 'margins' value represents the total of the margins around the
            // image in the grid item. 8 from the ItemTemplate root grid + 8 from
            // the ItemContainerStyle * (Right + Left). If those values change, 
            // this value needs to be updated to match.
            int margins = (int)this.Resources["LargeItemMarginValue"] * 4;
            double gridWidth = ImageGridView.ActualWidth -
                (int)this.Resources["DesktopWindowSidePaddingValue"];
    
            if (AnalyticsInfo.VersionInfo.DeviceFamily == "Windows.Mobile" &&
                UIViewSettings.GetForCurrentView().UserInteractionMode ==
                    UserInteractionMode.Touch)
            {
                margins = (int)this.Resources["SmallItemMarginValue"] * 4;
                gridWidth = ImageGridView.ActualWidth -
                    (int)this.Resources["MobileWindowSidePaddingValue"];
            }
    
            double ItemWidth = ZoomSlider.Value + margins;
            // We need at least 1 column.
            int columns = (int)Math.Max(gridWidth / ItemWidth, 1);
    
            // Adjust the available grid width to account for margins around each item.
            double adjustedGridWidth = gridWidth - (columns * margins);
    
            ItemSize = (adjustedGridWidth / columns);
        }
        else
        {
            ItemSize = ZoomSlider.Value;
        }
    }
    ```

2. <span data-ttu-id="321c9-258">Navigieren Sie in MainPage.xaml an den Anfang der Datei und fügen Sie eine **SizeChanged**-Ereignisbindung dem Element **Seite** hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-258">In MainPage.xaml, navigate to the top of the file and add a **SizeChanged** event binding to the **Page** element.</span></span>

    **<span data-ttu-id="321c9-259">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-259">Before:</span></span>**
    ```xaml
    <Page x:Name="page"  
    ```

    **<span data-ttu-id="321c9-260">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-260">After:</span></span>**
    ```xaml
    <Page x:Name="page" 
          SizeChanged="{x:Bind DetermineItemSize}"
    ```

3. <span data-ttu-id="321c9-261">Suchen Sie den **Schieberegler** mit dem Namen **ZoomSlider** und fügen Sie die **ValueChanged**-Ereignisbindung hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-261">Find the **Slider** named **ZoomSlider** and add a **ValueChanged** event binding.</span></span>

    **<span data-ttu-id="321c9-262">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-262">Before:</span></span>**
    ```xaml
    <Slider x:Name="ZoomSlider"
    ```

    **<span data-ttu-id="321c9-263">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-263">After:</span></span>**
    ```xaml
    <Slider x:Name="ZoomSlider"
            ValueChanged="{x:Bind DetermineItemSize}"
    ```

4. <span data-ttu-id="321c9-264">Suchen Sie den **ToggleSwitch** mit dem Namen **FitScreenToggle** und fügen Sie die **Toggled**-Ereignisbindung hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-264">Find the **ToggleSwitch** named **FitScreenToggle** and add a **Toggled** event binding.</span></span>

    **<span data-ttu-id="321c9-265">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-265">Before:</span></span>**
    ```xaml
    <ToggleSwitch x:Name="FitScreenToggle"
    ```

    **<span data-ttu-id="321c9-266">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-266">After:</span></span>**
    ```xaml
    <ToggleSwitch x:Name="FitScreenToggle"
                  Toggled="{x:Bind DetermineItemSize}"
    ```

<span data-ttu-id="321c9-267">Führen Sie die App aus und verwenden Sie den Zoomschieberegler und den Schalter **Bildschirmgröße anpassen**, um die Größe des Image-Vorlage zu ändern.</span><span class="sxs-lookup"><span data-stu-id="321c9-267">Run the app and use the zoom slider and **Fit to screen** toggle to change the image-template dimensions.</span></span> <span data-ttu-id="321c9-268">Wie Sie sehen können, ermöglichen die neuesten Änderungen eine genauere Erfahrung der Zoomgröße, während der Code gut organisiert bleibt.</span><span class="sxs-lookup"><span data-stu-id="321c9-268">As you can see, the latest changes enable a more refined zoom/resize experience while keeping the code well organized.</span></span> 

![Ausführen der App mit aktivierter Bildschirmanpassung](../design/basics/images/xaml-basics/gallery-with-fit-to-screen.png)

> [!NOTE]
> <span data-ttu-id="321c9-270">Hier ist eine Herausforderung: versuchen Sie einen **TextBlock** nach dem **ZoomSlider** hinzuzufügen und die **Text**-Eigenschaft an die **ItemSize**-Eigenschaft zu binden.</span><span class="sxs-lookup"><span data-stu-id="321c9-270">For a challenge, try adding a **TextBlock** after the **ZoomSlider** and binding the **Text** property to the **ItemSize** property.</span></span> <span data-ttu-id="321c9-271">Da es sich nicht um eine Datenvorlage handelt, können Sie **x: Bind** anstelle von **Bindung** wie in den vorherigen **ItemSize**-Bindungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="321c9-271">Because it's not in a data template, you can use **x:Bind** instead of **Binding** like in the previous **ItemSize** bindings.</span></span>  
<span data-ttu-id="321c9-272">}</span><span class="sxs-lookup"><span data-stu-id="321c9-272">}</span></span>

## <a name="part-5-enable-user-edits"></a><span data-ttu-id="321c9-273">Teil 5: Aktivieren der Bearbeitung durch den Benutzer</span><span class="sxs-lookup"><span data-stu-id="321c9-273">Part 5: Enable user edits</span></span>

<span data-ttu-id="321c9-274">Hier erstellen Sie bidirektionale Bindungen, damit Benutzer die Werte aktualisieren können, einschließlich der Bildtitel, Bewertung und verschiedener visuelle Effekte.</span><span class="sxs-lookup"><span data-stu-id="321c9-274">Here, you'll create two-way bindings to enable users to update values, including the image title, rating, and various visual effects.</span></span> 

<span data-ttu-id="321c9-275">Um dies zu erreichen, aktualisieren Sie die vorhandene **DetailPage**, die ein einzige Bildanzeige, ein Zoom-Steuerelement und das Bearbeiten der Benutzeroberfläche ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="321c9-275">To achieve this, you'll update the existing **DetailPage**, which provides a single-image viewer, zoom control, and editing UI.</span></span>  

<span data-ttu-id="321c9-276">Zunächst müssen Sie jedoch die **DetailPage** anhängen, damit die App darauf navigiert, wenn der Benutzer ein Bild in der Galerie anklickt.</span><span class="sxs-lookup"><span data-stu-id="321c9-276">First, however, you need to attach the **DetailPage** so that the app navigates to it when the user clicks an image in the gallery view.</span></span>

**<span data-ttu-id="321c9-277">Anhängen der DetailPage</span><span class="sxs-lookup"><span data-stu-id="321c9-277">Attach the DetailPage</span></span>**

1. <span data-ttu-id="321c9-278">Suchen Sie in MainPage.xaml das **GridView** mit dem Namen **ImageGridView** und fügen Sie ein **ItemClick**-Attribut hinzu.</span><span class="sxs-lookup"><span data-stu-id="321c9-278">In MainPage.xaml, find the **GridView** named **ImageGridView** and add an **ItemClick** value.</span></span> 

    > [!TIP] 
    > <span data-ttu-id="321c9-279">Wenn Sie die Änderung eintippen anstatt diese zu kopieren/einzufügen, sehen Sie ein IntelliSense-Popup mit der Bezeichnung "\<New Event Handler\>".</span><span class="sxs-lookup"><span data-stu-id="321c9-279">If you type in the change below instead of copy/pasting, you'll see an IntelliSense pop-up that says "\<New Event Handler\>".</span></span> <span data-ttu-id="321c9-280">Wenn Sie die Tab-Taste drücken, wird es den Wert mit dem Namen eines standardmäßigen Ereignishandlers füllen und automatisch die Methode im nächsten Schritt auskommentieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-280">If you press the Tab key, it will fill in the value with a default method handler name, and automatically stub out the method shown in the next step.</span></span> <span data-ttu-id="321c9-281">Drücken Sie dann F12, um zu der Methode im CodeBehind zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-281">You can then press F12 to navigate to the method in the code-behind.</span></span> 

    **<span data-ttu-id="321c9-282">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-282">Before:</span></span>**
    ```xaml
    <GridView x:Name="ImageGridView"
    ```

    **<span data-ttu-id="321c9-283">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-283">After:</span></span>**
    ```xaml
    <GridView x:Name="ImageGridView"
              ItemClick="ImageGridView_ItemClick"
    ```

    > [!NOTE] 
    > <span data-ttu-id="321c9-284">Wir verwenden hier einen herkömmlichen Ereignishandler anstelle eines x: Bind-Ausdrucks.</span><span class="sxs-lookup"><span data-stu-id="321c9-284">We're using a conventional event handler here instead of an x:Bind expression.</span></span> <span data-ttu-id="321c9-285">Dies liegt daran, dass wir die Ereignisdaten sehen müssen, wie nachfolgend dargestellt.</span><span class="sxs-lookup"><span data-stu-id="321c9-285">This is because we need to see the event data, as shown next.</span></span> 

2. <span data-ttu-id="321c9-286">Fügen Sie unter MainPage.xaml.cs den Ereignishandler hinzu (oder füllen Sie ihn aus, wenn Sie den Tipp im letzten Schritt verwendeten).</span><span class="sxs-lookup"><span data-stu-id="321c9-286">In MainPage.xaml.cs, add the event handler (or fill it in, if you used the tip in the last step).</span></span>

    ```c#
    private void ImageGridView_ItemClick(object sender, ItemClickEventArgs e)
    {
        this.Frame.Navigate(typeof(DetailPage), e.ClickedItem);
    }
    ```

    <span data-ttu-id="321c9-287">Diese Methode navigiert einfach auf die Detailseite, und übergibt das geklickt Element, was ein **ImageFileInfo**-Objekt ist, das von **DetailPage.OnNavigatedTo** zum Initialisieren der Seite verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="321c9-287">This method simply navigates to the detail page, passing in the clicked item, which is an **ImageFileInfo** object used by **DetailPage.OnNavigatedTo** for initializing the page.</span></span> <span data-ttu-id="321c9-288">Sie müssen diese Methode nicht in diesem Lernprogramm implementieren, aber Sie können hier sehen, was das Resultat ist.</span><span class="sxs-lookup"><span data-stu-id="321c9-288">You won't have to implement that method in this tutorial, but you can take a look to see what it does.</span></span> 
    
3. <span data-ttu-id="321c9-289">(Optional) Löschen Sie, oder kommentieren Sie alle Steuerelemente, die Sie in vorherigen Play-Punkten hinzugefügt haben und die mit dem aktuell ausgewählten Bild funktionieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-289">(Optional) Delete or comment out any controls you added in previous play-points that work with the currently selected image.</span></span> <span data-ttu-id="321c9-290">Das Beibehalten schadet zwar nicht, es ist macht es viel schwieriger, ein Bild auszuwählen, ohne zur Detailseite zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-290">Keeping them around won't hurt anything, but it's now a lot harder to select an image without navigating to the detail page.</span></span> 

<span data-ttu-id="321c9-291">Jetzt, wo Sie die beiden Seiten angeschlossen haben, führen Sie die App aus und schauen sie im Detail an.</span><span class="sxs-lookup"><span data-stu-id="321c9-291">Now that you've connected the two pages, run the app and take a look around.</span></span> <span data-ttu-id="321c9-292">Alles funktioniert mit Ausnahme der Steuerelemente im Bereich „Bearbeiten”, der nicht reagieren, wenn Sie versuchen, die Werte zu ändern.</span><span class="sxs-lookup"><span data-stu-id="321c9-292">Everything works except the controls on the editing pane, which don't respond when you try to change the values.</span></span> 

<span data-ttu-id="321c9-293">Wie Sie sehen können, zeigt das Textfeld den Titel an und Sie können Änderungen eingeben.</span><span class="sxs-lookup"><span data-stu-id="321c9-293">As you can see, the title text box does display the title and lets you type in changes.</span></span> <span data-ttu-id="321c9-294">Sie müssen den Fokus auf ein anderes Steuerelement leiten, um die Änderungen zu übernehmen, aber der Titel in der oberen linken Ecke des Bildschirms kann noch nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="321c9-294">You have to change focus to another control to commit the changes, but the title in the upper-left corner of the screen doesn't update yet.</span></span> 

<span data-ttu-id="321c9-295">Alle Steuerelemente sind bereits mithilfe der einfachen **x: Bind**-Ausdrücke gebunden, die wir in Teil 1 behandelt haben.</span><span class="sxs-lookup"><span data-stu-id="321c9-295">All the controls are already bound using the plain **x:Bind** expressions we covered in Part 1.</span></span> <span data-ttu-id="321c9-296">Wenn Sie sich erinnern, bedeutet dies, dass sie alle einmalige Bindungen sind, was erklärt, warum die Änderungen der Werte nicht registriert sind.</span><span class="sxs-lookup"><span data-stu-id="321c9-296">If you recall, this means they are all one-time bindings, which explains why changes to the values aren't registered.</span></span> <span data-ttu-id="321c9-297">Um dieses Problem zu beheben, müssen wir diese lediglich in bidirektionalen Bindungen umwandeln.</span><span class="sxs-lookup"><span data-stu-id="321c9-297">To fix this, all we have to do is turn them into two-way bindings.</span></span> 

**<span data-ttu-id="321c9-298">Machen Sie die Bearbeitungssteuerelemente interaktiv</span><span class="sxs-lookup"><span data-stu-id="321c9-298">Make the editing controls interactive</span></span>**

1. <span data-ttu-id="321c9-299">Suchen Sie in DetailPage.xaml den **TextBlock** mit dem Namen **TitleTextBlock** und das **RadRating**-Steuerelement dahinter, und aktualisieren Sie deren **x: Bind**-Ausdrücke, damit sie **Mode = TwoWay** enthalten.</span><span class="sxs-lookup"><span data-stu-id="321c9-299">In DetailPage.xaml, find the **TextBlock** named **TitleTextBlock** and the **RadRating** control after it, and update their **x:Bind** expressions to include **Mode=TwoWay**.</span></span>

    **<span data-ttu-id="321c9-300">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-300">Before:</span></span>**
    ```xaml
    <TextBlock x:Name="TitleTextBlock"
               Text="{x:Bind item.ImageTitle}"
               ... >
    <telerikInput:RadRating Value="{x:Bind item.ImageRating}"
                            ... >
    ```

    **<span data-ttu-id="321c9-301">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-301">After:</span></span>**
    ```xaml
    <TextBlock x:Name="TitleTextBlock" 
               Text="{x:Bind item.ImageTitle, Mode=TwoWay}" 
               ... >
    <telerikInput:RadRating Value="{x:Bind item.ImageRating, Mode=TwoWay}" 
                            ... >
    ```

2. <span data-ttu-id="321c9-302">Führen Sie dieselben Schritte für den Effekt-Schieberegler durch, die dem Bewertungssteuerelement folgen.</span><span class="sxs-lookup"><span data-stu-id="321c9-302">Do the same thing for all the effect sliders that come after the rating control.</span></span>

    ```xaml
    <Slider Header="Exposure"    ... Value="{x:Bind item.Exposure, Mode=TwoWay}" ...
    <Slider Header="Temperature" ... Value="{x:Bind item.Temperature, Mode=TwoWay}" ... 
    <Slider Header="Tint"        ... Value="{x:Bind item.Tint, Mode=TwoWay}" ... 
    <Slider Header="Contrast"    ... Value="{x:Bind item.Contrast, Mode=TwoWay}" ... 
    <Slider Header="Saturation"  ... Value="{x:Bind item.Saturation, Mode=TwoWay}" ...
    <Slider Header="Blur"        ... Value="{x:Bind item.Blur, Mode=TwoWay}" ... 
    ```

<span data-ttu-id="321c9-303">Der Zwei-Wege-Modus bedeutet, dass die Daten in beide Richtungen verschoben werden, wenn Änderungen auf beiden Seiten vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="321c9-303">The two-way mode, as you might expect, means that the data moves in both directions whenever there are changes on either side.</span></span> 

<span data-ttu-id="321c9-304">Wie die unidirektionalen Bindungen, die wir vorher behandelt haben, werden diese bidirektionalen Bindungen jetzt die UI aktualisieren, wenn die gebundenen sich ändern. Dies geschieht dank der **INotifyPropertyChanged**-Implementierung in der **ImageFileInfo**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="321c9-304">Like the one-way bindings covered earlier, these two-way bindings will now update the UI whenever the bound properties change, thanks to the **INotifyPropertyChanged** implementation in the **ImageFileInfo** class.</span></span> <span data-ttu-id="321c9-305">Mit bidirektionaler Bindung werden jedoch die Werte auch von der Benutzeroberfläche auf die gebundenen Eigenschaften verschoben, wenn der Benutzer mit dem Steuerelement interagiert.</span><span class="sxs-lookup"><span data-stu-id="321c9-305">With two-way binding, however, the values will also move from the UI to the bound properties whenever the user interacts with the control.</span></span> <span data-ttu-id="321c9-306">Auf der XAML-Seite ist nichts weiter erforderlich.</span><span class="sxs-lookup"><span data-stu-id="321c9-306">Nothing more is needed on the XAML side.</span></span> 

<span data-ttu-id="321c9-307">Führen Sie die App aus und testen Sie die Bearbeitungssteuerelemente.</span><span class="sxs-lookup"><span data-stu-id="321c9-307">Run the app and try the editing controls.</span></span> <span data-ttu-id="321c9-308">Wenn Sie eine Änderung vornehmen, wirkt sich dies jetzt auf den Bildwert aus, und diese Änderungen bleiben konstant, wenn Sie wieder zur Hauptseite navigieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-308">As you can see, when you make a change, it now affects the image values, and those changes persist when you navigate back to the main page.</span></span> 

## <a name="part-6-format-values-through-function-binding"></a><span data-ttu-id="321c9-309">Teil 6: Formatieren von Werten über die Bind-Funktion</span><span class="sxs-lookup"><span data-stu-id="321c9-309">Part 6: Format values through function binding</span></span>

<span data-ttu-id="321c9-310">Ein letztes Problem bleibt bestehen.</span><span class="sxs-lookup"><span data-stu-id="321c9-310">One last problem remains.</span></span> <span data-ttu-id="321c9-311">Wenn Sie den Effekt-Schieberegler verschieben, ändern Sie die Beschriftungen daneben nicht.</span><span class="sxs-lookup"><span data-stu-id="321c9-311">When you move the effect sliders, the labels next to them still don't change.</span></span> 

![Effekt-Schieberegler mit Standardbezeichnungswerten](../design/basics/images/xaml-basics/effect-sliders-before-label-fix.png)

<span data-ttu-id="321c9-313">Der letzte Teil dieses Lernprogramms behandelt das Hinzufügen von Bindungen, die die Werte des Schiebereglers für die Anzeige formatieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-313">The final part in this tutorial is to add bindings that format the slider values for display.</span></span>

**<span data-ttu-id="321c9-314">Binden Sie die Effekt-Schiebereglerbeschriftungen und formatieren Sie die Werte für die Anzeige</span><span class="sxs-lookup"><span data-stu-id="321c9-314">Bind the effect-slider labels and format the values for display</span></span>**

1. <span data-ttu-id="321c9-315">Suchen Sie den **TextBlock** hinter dem **Belichtungs**-Schieberegler und ersetzen den **Text**-Wert durch den hier gezeigten Bindungsausdruck.</span><span class="sxs-lookup"><span data-stu-id="321c9-315">Find the **TextBlock** after the **Exposure** slider and replace the **Text** value with the binding expression shown here.</span></span>

    **<span data-ttu-id="321c9-316">Vorher:</span><span class="sxs-lookup"><span data-stu-id="321c9-316">Before:</span></span>**
    ```xaml
    <Slider Header="Exposure" ... />
    <TextBlock ... Text="0.00" />
    ```

    **<span data-ttu-id="321c9-317">Nachher:</span><span class="sxs-lookup"><span data-stu-id="321c9-317">After:</span></span>**
    ```xaml
    <Slider Header="Exposure" ... />
    <TextBlock ... Text="{x:Bind item.Exposure.ToString('N', culture), Mode=OneWay}" />
    ```

    <span data-ttu-id="321c9-318">Dies wird Funktions-Bindung genannt, da Sie eine an den Rückgabewert einer Methode binden.</span><span class="sxs-lookup"><span data-stu-id="321c9-318">This is called a function binding because you are binding to the return value of a method.</span></span> <span data-ttu-id="321c9-319">Die Methode muss über die Seite „CodeBehind” oder über den **x: DataType**-Typ zugänglich sein, wenn Sie in einer Datenvorlage arbeiten.</span><span class="sxs-lookup"><span data-stu-id="321c9-319">The method must be accessible through the page's code-behind or the **x:DataType** type if you are in a data template.</span></span> <span data-ttu-id="321c9-320">In diesem Fall ist die Methode die vertraute .NET **ToString**-Methode, auf die über die Elementeigenschaft auf der Seite zugegriffen werden kann, sowie über die **Belichtungs**-Eigenschaft des Elements.</span><span class="sxs-lookup"><span data-stu-id="321c9-320">In this case, the method is the familiar .NET **ToString** method, which is accessed through the item property of the page, and then through the **Exposure** property of the item.</span></span> <span data-ttu-id="321c9-321">(Dies veranschaulicht, wie Sie eine Bindung an die Methoden und Eigenschaften erstellen können, die in einer Kette von Verbindungen tief verschachtelt sind.)</span><span class="sxs-lookup"><span data-stu-id="321c9-321">(This illustrates how you can bind to methods and properties that are deeply nested in a chain of connections.)</span></span>

    <span data-ttu-id="321c9-322">Funktions-Bindung ist eine ideale Möglichkeit zur Formatierung von Werten für die Anzeige, da andere Bindungsquellen als Methodenargumente übergeben werden können und der Bindungsausdruck die Änderungen für diese Werte abhört, wie bei dem unidirektionalen Modus erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="321c9-322">Function binding is an ideal way to format values for display because you can pass in other binding sources as method arguments, and the binding expression will listen for changes to those values as expected with the one-way mode.</span></span> <span data-ttu-id="321c9-323">In diesem Beispiel ist das **Kultur**-Argument ein Verweis auf ein sich nicht änderndes Feld, das im CodeBehind implementiert ist, aber es könnte genauso einfach eine Eigenschaft sein, die **PropertyChanged**-Ereignisse auslöst.</span><span class="sxs-lookup"><span data-stu-id="321c9-323">In this example, the **culture** argument is a reference to an unchanging field implemented in code-behind, but it could just as easily have been a property that raises **PropertyChanged** events.</span></span> <span data-ttu-id="321c9-324">In diesem Fall würden jegliche Änderungen an den Wert der Eigenschaft den **X: Bind**-Ausdruck zum Aufrufen von **ToString** mit dem neuen Wert auslösen und dann die Benutzeroberfläche mit dem Ergebnis aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-324">In that case, any changes to the property value would cause the **x:Bind** expression to call **ToString** with the new value and then update the UI with the result.</span></span> 

2. <span data-ttu-id="321c9-325">Führen Sie dieselben Schritte für die **TextBlocks**-Bezeichnungen durch, die die anderen Effekt-Schieberegler beschriften.</span><span class="sxs-lookup"><span data-stu-id="321c9-325">Do the same thing for the **TextBlocks** that label the other effect sliders.</span></span>

    ```xaml
    <Slider Header="Temperature" ... />
    <TextBlock ... Text="{x:Bind item.Temperature.ToString('N', culture), Mode=OneWay}" />

    <Slider Header="Tint" ... />
    <TextBlock ... Text="{x:Bind item.Tint.ToString('N', culture), Mode=OneWay}" />

    <Slider Header="Contrast" ... />
    <TextBlock ... Text="{x:Bind item.Contrast.ToString('N', culture), Mode=OneWay}" />

    <Slider Header="Saturation" ... />
    <TextBlock ... Text="{x:Bind item.Saturation.ToString('N', culture), Mode=OneWay}" />

    <Slider Header="Blur" ... />
    <TextBlock ... Text="{x:Bind item.Blur.ToString('N', culture), Mode=OneWay}" />
    ```

<span data-ttu-id="321c9-326">Wenn Sie die App ausführen, funktioniert jetzt alles, einschließlich der Schiebereglerbeschriftungen.</span><span class="sxs-lookup"><span data-stu-id="321c9-326">Now when you run the app, everything works, including the slider labels.</span></span> 

![Effekt-Schieberegler mit Funktionsbezeichnungen](../design/basics/images/xaml-basics/effect-sliders-after-label-fix.png)

> [!NOTE]
> <span data-ttu-id="321c9-328">Versuchen Sie die Funktions-Bindung mit dem **TextBlock** vom letzten Play-Punkt und binden Sie sie an eine neue Methode, die eine Zeichenfolge im "000 x 000"-Format zurückgibt, wenn Sie sie an den **ItemSize**-Wert übergeben.</span><span class="sxs-lookup"><span data-stu-id="321c9-328">Try using function binding with the **TextBlock** from the last play-point and bind it to a new method that returns a string in "000 x 000" format when you pass it the **ItemSize** value.</span></span>


## <a name="conclusion"></a><span data-ttu-id="321c9-329">Fazit</span><span class="sxs-lookup"><span data-stu-id="321c9-329">Conclusion</span></span>

<span data-ttu-id="321c9-330">In diesem Lernprogramm haben Sie einen Einblick in die Datenbindung und einige der verfügbaren Funktionen erhalten.</span><span class="sxs-lookup"><span data-stu-id="321c9-330">This tutorial has given you a taste of data binding and shown you some of the functionality available.</span></span> <span data-ttu-id="321c9-331">Eines möchten wir jedoch zu bedenken geben: nicht alles kann gebunden werden, und in einigen Fällen sind die Werte zum Herstellen einer Verbindung nicht kompatibel mit den Eigenschaften, die Sie anbinden möchten.</span><span class="sxs-lookup"><span data-stu-id="321c9-331">One word of caution before we wrap up: not everything is bindable, and sometimes the values you try to connect to are incompatible with the properties you are trying to bind.</span></span> <span data-ttu-id="321c9-332">Es gibt zwar ein hohes Maß an Flexibilität beim Binden, dies funktioniert allerdings nicht in jeder Situation.</span><span class="sxs-lookup"><span data-stu-id="321c9-332">There is a lot of flexibility in binding, but it won't work in every situation.</span></span>

<span data-ttu-id="321c9-333">Ein Beispiel für ein Problem, das nicht durch Bindungen angesprochen wird ist, wenn ein Steuerelement keine geeigneten Eigenschaften zum Binden hat, wie bei der Detailseite der Zoom-Funktion.</span><span class="sxs-lookup"><span data-stu-id="321c9-333">One example of a problem not addressed by binding is when a control has no suitable properties to bind to, as with the detail page zoom feature.</span></span> <span data-ttu-id="321c9-334">Dieser Zoomschieberegler muss mit **ScrollViewer** interagieren, das das Bild anzeigt, aber **ScrollViewer** kann nur über die **ChangeView**-Methode aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="321c9-334">This zoom slider needs to interact with the **ScrollViewer** that displays the image, but **ScrollViewer** can only be updated through its **ChangeView** method.</span></span> <span data-ttu-id="321c9-335">In diesem Fall verwenden wir herkömmliche Ereignishandler, um **ScrollViewer** und den Zoomschieberegler zu synchronisieren. Weitere Details zu den Methoden finden Sie unter **DetailPage\*\*\*\*ZoomSlider_ValueChanged** und **MainImageScroll_ViewChanged**.</span><span class="sxs-lookup"><span data-stu-id="321c9-335">In this case, we use conventional event handlers to keep the **ScrollViewer** and the zoom slider in sync; see the **DetailPage** **ZoomSlider_ValueChanged** and **MainImageScroll_ViewChanged** methods for details.</span></span>

<span data-ttu-id="321c9-336">Trotzdem ist das Binden eine leistungsfähige und flexible Möglichkeit zur Vereinfachung des Codes und um die UI-Logik von der Datenlogik getrennt zu halten.</span><span class="sxs-lookup"><span data-stu-id="321c9-336">Nonetheless, binding is a powerful and flexible way to simplify your code and keep your UI logic separate from your data logic.</span></span> <span data-ttu-id="321c9-337">Dadurch ist es viel einfacher für Sie, beide Seiten zu koordinieren und gleichzeitig das Risikos der Einführung von Fehlern auf der anderen Seite zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-337">This will make it much easier for you adjust either side of this divide while reducing the risk of introducing bugs on the other side.</span></span> 

<span data-ttu-id="321c9-338">Ein Beispiel der Trennung von Benutzeroberfläche und Daten ist die **ImageFileInfo.ImageTitle**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="321c9-338">One example of UI and data separation is with the **ImageFileInfo.ImageTitle** property.</span></span> <span data-ttu-id="321c9-339">Diese Eigenschaft (und die **ImageRating**-Eigenschaft) unterscheidet sich etwas von der **ItemSize**-Eigenschaft im Teil 4, da der Wert in den Dateimetadaten statt in einem Feld gespeichert wird (über den **ImageProperties**-Typ).</span><span class="sxs-lookup"><span data-stu-id="321c9-339">This property (and the **ImageRating** property) is slightly different than the **ItemSize** property you created in Part 4 because the value is stored in the file metadata (exposed through the **ImageProperties** type) instead of in a field.</span></span> <span data-ttu-id="321c9-340">Darüber hinaus gibt der **ImageTitle** den **ImageName**-Wert zurück (auf den Namen der Datei festgelegt), wenn kein Titel in den Metadaten der Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="321c9-340">Additionally, **ImageTitle** returns the **ImageName** value (set to the file name) if there is no title in the file metadata.</span></span> 

```c#
public string ImageTitle
{
    get => String.IsNullOrEmpty(ImageProperties.Title) ? ImageName : ImageProperties.Title;
    set
    {
        if (ImageProperties.Title != value)
        {
            ImageProperties.Title = value;
            var ignoreResult = ImageProperties.SavePropertiesAsync();
            OnPropertyChanged();
        }
    }
}
```

<span data-ttu-id="321c9-341">Wie Sie sehen können, aktualisiert der Setter die **ImageProperties.Title**-Eigenschaft und ruft dann **SavePropertiesAsync** auf, um den neuen Wert in die Datei zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="321c9-341">As you can see, the setter updates the **ImageProperties.Title** property and then calls **SavePropertiesAsync** to write the new value to the file.</span></span> <span data-ttu-id="321c9-342">(Hierbei handelt es sich um eine asynchrone Methode, aber wir können nicht das **await**-Schlüsselwort in einer Eigenschaft verwenden – was nicht wünschenswert wäre, da das Erstellen und Abrufen von Eigenschaften sofort ausgeführt würde.</span><span class="sxs-lookup"><span data-stu-id="321c9-342">(This is an async method, but we can't use the **await** keyword in a property - and you wouldn't want to because property getters and setters should complete immediately.</span></span> <span data-ttu-id="321c9-343">Sie würden stattdessen die Methode aufrufen und die das zurückgegebene **Aufgabe**-Objekt ignorieren.)</span><span class="sxs-lookup"><span data-stu-id="321c9-343">So instead, you would call the method and ingore the **Task** object it returns.)</span></span> 

<!-- TODO more screenshots? -->

## <a name="going-further"></a><span data-ttu-id="321c9-344">Vertiefung</span><span class="sxs-lookup"><span data-stu-id="321c9-344">Going further</span></span>

<span data-ttu-id="321c9-345">Nach Abschluss dieser Übung verfügen Sie über ausreichende adaptive Bindungs-Kenntnisse, um selbst weiter zu experimentieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-345">Now that you've completed this lab, you have enough binding knowledge tackle a problem on your own.</span></span>

<span data-ttu-id="321c9-346">Wie Sie gesehen haben, wenn Sie den Zoomfaktor auf der Detailseite ändern, wird er automatisch zurückgesetzt, wenn Sie rückwärts navigieren und das gleiche Bild erneut aktivieren.</span><span class="sxs-lookup"><span data-stu-id="321c9-346">As you might have noticed, if you change the zoom level on the details page, it resets automatically when you navigate backward then select the same image again.</span></span> <span data-ttu-id="321c9-347">Können Sie herausfinden, wie Sie den Zoomfaktor für jedes Bild einzeln erhalten und wieder herstellen?</span><span class="sxs-lookup"><span data-stu-id="321c9-347">Can you figure out how to preserve and restore the zoom level for each image individually?</span></span> <span data-ttu-id="321c9-348">Viel Glück!</span><span class="sxs-lookup"><span data-stu-id="321c9-348">Good luck!</span></span>
    
<span data-ttu-id="321c9-349">Sie sollten in diesem Lernprogramm alle benötigten Informationen erhalten haben, aber wenn Sie weitere Unterstützung benötigen, sind die Datenbindungsdokumente nur einen Mausklick entfernt.</span><span class="sxs-lookup"><span data-stu-id="321c9-349">You should have all the info you need in this tutorial, but if you need more guidance, the data binding docs are only a click away.</span></span> <span data-ttu-id="321c9-350">Beginnen Sie hier:</span><span class="sxs-lookup"><span data-stu-id="321c9-350">Start here:</span></span>

+ [<span data-ttu-id="321c9-351">{x:Bind}-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="321c9-351">{x:Bind} markup extension</span></span>](https://docs.microsoft.com/windows/uwp/xaml-platform/x-bind-markup-extension)
+ [<span data-ttu-id="321c9-352">Datenbindung im Detail</span><span class="sxs-lookup"><span data-stu-id="321c9-352">Data binding in depth</span></span>](https://docs.microsoft.com/windows/uwp/data-binding/data-binding-in-depth)