---
author: mijacobs
title: Erstellen eigener Stile
description: In diesem Artikel werden die Grundlagen für UI-Stilelemente in XAML behandelt
keywords: XAML, UWP, Erste Schritte
ms.author: mijacobs
ms.date: 08/31/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 11f279de206a84e61144789ba43a268f2b896fee
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5933145"
---
# <a name="tutorial-create-custom-styles"></a><span data-ttu-id="c8ae4-104">Erstellen eigener Stile – Tutorial</span><span class="sxs-lookup"><span data-stu-id="c8ae4-104">Tutorial: Create custom styles</span></span>

<span data-ttu-id="c8ae4-105">In diesem Lernprogramm wird das Anpassen der Benutzeroberfläche unserer XAML-App veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-105">This tutorial shows you how to customize the UI of our XAML app.</span></span> <span data-ttu-id="c8ae4-106">Warnung: in diesem Lernprogramm kann möglicherweise ein Einhorn auftauchen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-106">Warning: this tutorial might or might not involve a unicorn.</span></span> <span data-ttu-id="c8ae4-107">(Stimmt!)</span><span class="sxs-lookup"><span data-stu-id="c8ae4-107">(It does!)</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="c8ae4-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c8ae4-108">Prerequisites</span></span>
* [<span data-ttu-id="c8ae4-109">Visual Studio2017 und das Windows10 SDK (10.0.15063.468 oder höher)</span><span class="sxs-lookup"><span data-stu-id="c8ae4-109">Visual Studio 2017 and the Windows 10 SDK (10.0.15063.468 or later)</span></span>](https://developer.microsoft.com/windows/downloads)

## <a name="part-0-get-the-code"></a><span data-ttu-id="c8ae4-110">Teil 0: Code herunterladen</span><span class="sxs-lookup"><span data-stu-id="c8ae4-110">Part 0: Get the code</span></span>
<span data-ttu-id="c8ae4-111">Der Ausgangspunkt für diese Übung befindet sich im PhotoLab-Beispielrepository, unter [xaml-basics-starting-points/style/ Ordner](https://github.com/Microsoft/Windows-appsample-photo-lab/tree/master/xaml-basics-starting-points/style).</span><span class="sxs-lookup"><span data-stu-id="c8ae4-111">The starting point for this lab is located in the PhotoLab sample repository, in the [xaml-basics-starting-points/style/ folder](https://github.com/Microsoft/Windows-appsample-photo-lab/tree/master/xaml-basics-starting-points/style).</span></span> <span data-ttu-id="c8ae4-112">Nachdem Sie das Repository geklont/heruntergeladen haben, können Sie das Projekt bearbeiten, indem Sie PhotoLab.sln mit Visual Studio2017 öffnen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-112">After you've cloned/downloaded the repo, you can edit the project by opening PhotoLab.sln with Visual Studio 2017.</span></span>

<span data-ttu-id="c8ae4-113">Die PhotoLab-App besteht aus zwei Hauptseiten:</span><span class="sxs-lookup"><span data-stu-id="c8ae4-113">The PhotoLab app has two primary pages:</span></span>

<span data-ttu-id="c8ae4-114">**MainPage.xaml:** zeigt eine Ansicht der Foto-Galerie, zusammen mit einigen Informationen über jede Bilddatei an.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-114">**MainPage.xaml:** displays a photo gallery view, along with some information about each image file.</span></span>
![MainPage](../basics/images/xaml-basics/mainpage.png)

<span data-ttu-id="c8ae4-116">**DetailPage.xaml:** zeigt ein einzelnes Foto an, nachdem es ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-116">**DetailPage.xaml:** displays a single photo after it has been selected.</span></span> <span data-ttu-id="c8ae4-117">Über ein Flyout-Menü kann das Foto bearbeitet, umbenannt und gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-117">A flyout editing menu allows the photo to be altered, renamed, and saved.</span></span>
![DetailPage](../basics/images/xaml-basics/detailpage.png)

## <a name="part-1-create-a-fancy-slider-control"></a><span data-ttu-id="c8ae4-119">Teil 1: Erstellen eines ausgefallenen Schieberegler-Steuerelements</span><span class="sxs-lookup"><span data-stu-id="c8ae4-119">Part 1: Create a fancy slider control</span></span>  

<span data-ttu-id="c8ae4-120">Die universelle Windows-Plattform (UWP) bietet eine Reihe von Möglichkeiten zum Anpassen der Darstellung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-120">Universal Windows Platform (UWP) provides a number of ways to customize the look of your app.</span></span> <span data-ttu-id="c8ae4-121">Von Schriftarten und Typografie-Einstellungen bis hin zu Farben und Farbverläufen und Weichzeichnereffekten – Sie haben viele Optionen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-121">From fonts and typography settings to colors and gradients to blur effects, you have a lot of options.</span></span> 

<span data-ttu-id="c8ae4-122">Im ersten Teil des Lernprogramms lernen wir über unsere Steuerelemente zum Bearbeiten von Fotos.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-122">For the first part of the tutorial, let's jazz up some of our photo editing controls.</span></span> 

<figure>
    <img src="../basics/images/xaml-basics/slider-start.png" />
    <figure>*<span data-ttu-id="c8ae4-123">Ein normaler Schieberegler mit dem entsprechenden Standardformat.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-123">A humble slider with default styling.</span></span>*</figure>
</figure>

<span data-ttu-id="c8ae4-124">Diese Schieberegler sind in Ordnung – sie funktionieren so, wie ein Schieberegler funktionieren sollte – aber sie haben keine ausgefallenen Effekte.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-124">These sliders are nice--they do all the things a slider should do--but they aren't very fancy.</span></span> <span data-ttu-id="c8ae4-125">Das wird hier geändert.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-125">Let's fix that.</span></span> 

<span data-ttu-id="c8ae4-126">Der Schieberegler für die Belichtung passt die Belichtung des Bilds an: ziehen Sie es auf die linke Seite und das Bild wird dunkler; Schieberegler nach rechts, und es wird heller.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-126">The exposure slider adjusts the exposure of the image: slide it to the left and the image gets darker; slider it to the right and it gets lighter.</span></span> <span data-ttu-id="c8ae4-127">Machen wir unseren Schieberegler etwas cooler und verleihen wir ihm einen Hintergrund, der von Schwarz auf Weiß verläuft.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-127">Let's make our slider cooler by giving it a background that goes from black to white.</span></span> <span data-ttu-id="c8ae4-128">Der Schieberegler sieht besser aus, was großartige ist, aber es gibt auch einen visuellen Hinweis zu den Funktionen an, die der Schieberegler bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-128">It'll make the slider look better, which is great, but it will also provide a visual clue about the functionality that the slider provides.</span></span>

### <a name="customize-a-slider-control"></a><span data-ttu-id="c8ae4-129">Anpassen des Schieberegler-Steuerelements</span><span class="sxs-lookup"><span data-stu-id="c8ae4-129">Customize a slider control</span></span>

<!-- TODO: Update folder -->
1. <span data-ttu-id="c8ae4-130">Öffnen Sie nach dem Download des Repositorys **PhotoLab.sln** unter xaml-basics-starting-points/style/ Ordner, und legen Sie Ihre Projektmappen-Plattform auf x86 oder x64 (nicht ARM) fest.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-130">After downloading the repository, open **PhotoLab.sln** in the xaml-basics-starting-points/style/ folder, and set your Solution Platform to x86 or x64 (not ARM).</span></span> 

    <span data-ttu-id="c8ae4-131">Drücken Sie F5, um die App zu übersetzen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-131">Press F5 to compile and run the app.</span></span> <span data-ttu-id="c8ae4-132">Der erste Bildschirm zeigt eine Bildergalerie.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-132">The first screen shows a gallery of images.</span></span> <span data-ttu-id="c8ae4-133">Klicken Sie auf ein Bild, um die Detailseite aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-133">Click an image to go to the image details page.</span></span> <span data-ttu-id="c8ae4-134">Klicken Sie von dort auf die Schaltfläche "Bearbeiten", um die Bearbeitungssteuerelemente zu sehen, mit denen wir arbeiten werden.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-134">Once you're there, click the edit button to see the editing controls we'll be working on.</span></span> <span data-ttu-id="c8ae4-135">Beenden Sie die App und kehren Sie zu Visual Studio zurück.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-135">Exit the app and return to Visual Studio.</span></span>  

2. <span data-ttu-id="c8ae4-136">Doppelklicken Sie im Projektmappen-Explorer-Bereich auf **DetailPage.xaml**, um sie zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-136">In the Solution Explorer panel, double-click **DetailPage.xaml** to open it.</span></span> 

    ![Die DetailPage.xaml-Datei im Projektmappen-Explorer von Visual Studio2017.](../basics/images/xaml-basics/style-detail-page-explorer.png)

3. <span data-ttu-id="c8ae4-138">Verwenden Sie ein Polygon-Element, um eine Hintergrundform für den Schieberegler für die Belichtung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-138">Use a Polygon element to create a background shape for the exposure slider.</span></span>

    <span data-ttu-id="c8ae4-139">Der [Windows.XAML.Ui.Shapes Namespace](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Shapes) enthält sieben Formen zur Auswahl.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-139">The [Windows.XAML.Ui.Shapes namespace](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Shapes) provides seven shapes to choose from.</span></span> <span data-ttu-id="c8ae4-140">Es gibt eine Ellipse, ein Rechteck, und einen „Pfad”, der jede Form zeichnen kann – sogar ein Einhorn!</span><span class="sxs-lookup"><span data-stu-id="c8ae4-140">There's an ellipse, a rectangle, and a thing called a Path, which can make any sort of shape--yes, even a unicorn!</span></span> 
    
    <span data-ttu-id="c8ae4-141"><!-- TODO reduce size --> ![Ein Einhorn](../basics/images/xaml-basics/unicorn.png)</span><span class="sxs-lookup"><span data-stu-id="c8ae4-141"><!-- TODO reduce size --> ![A unicorn](../basics/images/xaml-basics/unicorn.png)</span></span>
    
    > <span data-ttu-id="c8ae4-142">**Weitere Informationen finden sie unter:** Im Artikel [Zeichnen von Formen](https://docs.microsoft.com/en-us/windows/uwp/graphics/drawing-shapes) erfahren Sie alles Wissenswerte über XAML-Formen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-142">**Read about it:** The [Draw shapes](https://docs.microsoft.com/en-us/windows/uwp/graphics/drawing-shapes) article tells you everything you need to know about XAML shapes.</span></span> 
    
    <span data-ttu-id="c8ae4-143">Wir möchten ein dreieckig aussehendes Grafikobjekt erstellen – ähnlich der Form der Lautstärkeregelung einer Stereoanlage.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-143">We want to create a triangle-looking widget--something like the shape you'd see on a stereo's volume control.</span></span>
    
    ![Ein Schieberegler](../basics/images/xaml-basics/style-volume-slider.png)
    
    <span data-ttu-id="c8ae4-145">Klingt wie einen Auftrag für die Polygonform!</span><span class="sxs-lookup"><span data-stu-id="c8ae4-145">Sounds like a job for the Polygon shape!</span></span> <span data-ttu-id="c8ae4-146">Um einen Polygon zu definieren, geben Sie eine Reihe von Punkten an und weisen Sie ihnen eine Fläche zu.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-146">To define a polygon, you specify a set of points and give it a fill.</span></span> <span data-ttu-id="c8ae4-147">Lassen Sie uns ein Polygon erstellen, das ungefähr 200 Pixel breit und 20 Pixel hoch ist, das mit dem Farbverlauf gefüllt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-147">Let's create a polygon that's about 200 pixels wide and 20 pixels tall, with a gradient fill.</span></span>
    
    <span data-ttu-id="c8ae4-148">Suchen Sie in DetailPage.xaml den Code für den Schieberegler für die Belichtung heraus und erstellen Sie ein Polygon-Element direkt davor:</span><span class="sxs-lookup"><span data-stu-id="c8ae4-148">In DetailPage.xaml, find the code for the exposure slider, then create a Polygon element just before it:</span></span> 

    * <span data-ttu-id="c8ae4-149">Legen Sie **Grid.Row** auf "2" fest, um das Polygon in der gleichen Zeile wie den Belichtungsschieberegler zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-149">Set **Grid.Row** to "2" to put the polygon in the same row as the exposure slider.</span></span> 
    * <span data-ttu-id="c8ae4-150">Legen Sie die **Punkt**-Eigenschaft auf "0,20 200,20 200,0" fest, um die Dreiecksform zu definieren.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-150">Set the **Points** property to "0,20 200,20 200,0" to define the triangle shape.</span></span>
    * <span data-ttu-id="c8ae4-151">Legen Sie die **Stretch**-Eigenschaft auf "Fill" und die **HorizontalAlignment**-Eigenschaft auf "Stretch" fest.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-151">Set the **Stretch** property to "Fill" and the **HorizontalAlignment** property to "Stretch".</span></span>
    * <span data-ttu-id="c8ae4-152">Legen Sie die **Höhe** auf "20" und das **VerticalAlignment** auf "Center"fest.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-152">Set the **Height** to "20" and the **VerticalAlignment** to "Center".</span></span> 
    * <span data-ttu-id="c8ae4-153">Geben Sie dem **Polygon** einen linearen Farbverlauf.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-153">Give the **Polygon** a linear gradient fill.</span></span>     
    * <span data-ttu-id="c8ae4-154">Legen Sie für den Belichtungsschieberegler die **Vordergrund**-Eigenschaft auf "Transparent" fest, damit Sie das Polygon sehen können.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-154">On the exposure slider, set the **Foreground** property to "Transparent" so you can see the polygon.</span></span> 

    **<span data-ttu-id="c8ae4-155">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-155">Before</span></span>**
    ```xaml
    <Slider Header="Exposure"
        Grid.Row="2"
        Value="{x:Bind item.Exposure, Mode=TwoWay}"
        Minimum="-2"
        Maximum="2" />
    ```
    **<span data-ttu-id="c8ae4-156">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-156">After</span></span>**
    ```xaml
    <Polygon Grid.Row="2" Stretch="Fill"
                Points="0,20 200,20 200,0" HorizontalAlignment="Stretch"  
                VerticalAlignment="Center" Height="20">
        <Polygon.Fill>
            <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                <LinearGradientBrush.GradientStops>
                    <GradientStop Offset="0" Color="Black" />
                    <GradientStop Offset="1" Color="White" />
                </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
        </Polygon.Fill>
    </Polygon>
    <Slider Header="Exposure" 
        Grid.Row="2" 
        Foreground="Transparent"
        Value="{x:Bind item.Exposure, Mode=TwoWay}"
        Minimum="-2"
        Maximum="2" />
    ```

    <span data-ttu-id="c8ae4-157">Hinweise:</span><span class="sxs-lookup"><span data-stu-id="c8ae4-157">Notes:</span></span>
    * <span data-ttu-id="c8ae4-158">Wenn Sie die umgebende XAML-Codierung betrachten, sehen Sie, dass diese Elemente in einem Raster sind.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-158">If you look at the surrounding XAML, you'll see that these elements are in a Grid.</span></span> <span data-ttu-id="c8ae4-159">Wir haben das Polygon in die gleichen Zeile wie den Belichtungsschieberegler (Grid.Row="2") gesetzt, damit sie an derselben Stelle angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-159">We put the polygon in the same row as the exposure slider (Grid.Row="2") so they appear in the same spot.</span></span> <span data-ttu-id="c8ae4-160">Wir haben das Polygon vor den Schieberegler gesetzt, damit der Schieberegler über der Form rendert.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-160">We put the polygon before the slider so that the slider renders of top of the shape.</span></span>
    * <span data-ttu-id="c8ae4-161">Wir haben „Stretch” = "Fill" und „HorizontalAlignment” = "Stretch" im Polygon festgelegt, damit das Dreieck so angepasst wird, um den verfügbaren Platz auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-161">We set Stretch="Fill" and HorizontalAlignment="Stretch" on the polygon so that the triangle will adjust to fill the available space.</span></span> <span data-ttu-id="c8ae4-162">Wenn Sie den Schieberegler in der Breite verkleinern oder vergrößern wird das Polygon entsprechend vergrößert oder verkleinert.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-162">If the slider shrinks or grows in width, the polygon will shrink or grow to match.</span></span> 

4. <span data-ttu-id="c8ae4-163">Übersetzen Sie die App, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-163">Compile and run the app.</span></span> <span data-ttu-id="c8ae4-164">Der Schieberegler sollte nun großartig aussehen:</span><span class="sxs-lookup"><span data-stu-id="c8ae4-164">Your slider should now look awesome:</span></span>

    ![Ein ausgefallener Belichtungsschieberegler](../basics/images/xaml-basics/style-exposure-slider-done.png)

5. <span data-ttu-id="c8ae4-166">Geben wir jetzt dem nächsten Schieberegler, dem Schieberegler für die Temperatur, ein Upgrade.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-166">Let's give the next slider, the temperature slider, an upgrade.</span></span> <span data-ttu-id="c8ae4-167">Der Temperatur-Schieberegler ändert die Farbtemperatur des Bilds. Beim Ziehen auf die linken Seite wird das Bild blauer und beim Ziehen auf die recht Seite wird das Bild mehr gelb.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-167">The temperature slider changes the color temperature of the image; sliding to the left makes the image bluer and sliding to the right makes the image more yellow.</span></span>

    <span data-ttu-id="c8ae4-168">Wir verwenden einen anderen Polygon für diese Hintergrundform mit denselben Dimensionen wie das vorherige, aber dieses Mal ist die Füllung ein Farbverlauf in Blau-Gelb anstelle von Schwarzweiß.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-168">We'll use another polygon for this background shape with the same dimensions as the previous one, but this time we'll make the fill a blue-yellow gradient instead of black and white.</span></span> 

    **<span data-ttu-id="c8ae4-169">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-169">Before</span></span>**
    ```xaml
    <TextBlock Grid.Row="2"
                Grid.Column="1"
                 Margin="10,8,0,0" VerticalAlignment="Center" Padding="0"
                Text="{x:Bind item.Exposure.ToString('N', culture), Mode=OneWay}" />
                
    <Slider Header="Temperature"
            Grid.Row="3" Background="Transparent" Foreground="Transparent"
            Value="{x:Bind item.Temperature, Mode=TwoWay}"
            Minimum="-1"
            Maximum="1" />
    ```
    **<span data-ttu-id="c8ae4-170">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-170">After</span></span>**
    ```xaml
    <TextBlock Grid.Row="2"
                Grid.Column="1"
                Margin="10,8,0,0" VerticalAlignment="Center" Padding="0"
                Text="{x:Bind item.Exposure.ToString('N', culture), Mode=OneWay}" />         
                
    <Polygon Grid.Row="3" Stretch="Fill"
                Points="0,20 200,20 200,0" HorizontalAlignment="Stretch"  
                VerticalAlignment="Center" Height="20">
        <Polygon.Fill>
            <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                <LinearGradientBrush.GradientStops>
                    <GradientStop Offset="0" Color="Blue" />
                    <GradientStop Offset="1" Color="Yellow" />
                </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
        </Polygon.Fill>
    </Polygon>
    <Slider Header="Temperature"
            Grid.Row="3" Background="Transparent" Foreground="Transparent"
            Value="{x:Bind item.Temperature, Mode=TwoWay}"
            Minimum="-1"
            Maximum="1" />
    ```

6. <span data-ttu-id="c8ae4-171">Übersetzen Sie die App, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-171">Compile and run the app.</span></span> <span data-ttu-id="c8ae4-172">Sie verfügen jetzt über ausgefallene Schieberegler.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-172">You should now have two fancy sliders.</span></span>

    ![Zwei ausgefallene Schieberegler](../basics/images/xaml-basics/style-2sliders-done.png)

7. **<span data-ttu-id="c8ae4-174">Bonus</span><span class="sxs-lookup"><span data-stu-id="c8ae4-174">Extra credit</span></span>**

    <span data-ttu-id="c8ae4-175">Fügen Sie eine Hintergrundform für den Farbton-Schieberegler hinzu, mit einem Farbverlauf von Grün auf Rot.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-175">Add a background shape for the tint slider that has a gradient from green to red.</span></span> 

    ![Drei ausgefallene Schieberegler](../basics/images/xaml-basics/style-3sliders-done.png)


<span data-ttu-id="c8ae4-177">Herzlichen Glückwunsch! Sie haben Teil 1 abgeschlossen!</span><span class="sxs-lookup"><span data-stu-id="c8ae4-177">Congratulations, you've completed part 1!</span></span> <span data-ttu-id="c8ae4-178">Wenn Sie nicht weiterkommen oder die endgültige Lösung nicht anzeigen können, finden Sie den fertigen Code unter **UWP Academy\XAML\Styling\Part1\Finish**.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-178">If you got stuck or want to see the final solution, you can find the completed code at **UWP Academy\XAML\Styling\Part1\Finish**.</span></span>

 
    
## <a name="part-2-create-basic-styles"></a><span data-ttu-id="c8ae4-179">Teil 2: Erstellen von grundlegenden Stilen</span><span class="sxs-lookup"><span data-stu-id="c8ae4-179">Part 2: Create basic styles</span></span>

<span data-ttu-id="c8ae4-180">Einer der Vorteile der XAML-Stile ist, dass sie die Menge an Code, den Sie schreiben müssen erheblich verringern können und es jetzt viel einfach ist, das Erscheinungsbild Ihrer App zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-180">One of the advantages of XAML styles is that it can dramatically cut down the amount of code you have to write, and it can make it much, much easier to update the look of your app.</span></span>

<span data-ttu-id="c8ae4-181">Um einen Stil zu definieren, fügen Sie ein [Stil](https://msdn.microsoft.com/library/windows/apps/br208849)-Element in die [Ressourcen](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement.Resources)-Eigenschaft eines Elements ein, das das Steuerelement enthält, das Sie formatieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-181">To define a style, you add a [Style](https://msdn.microsoft.com/library/windows/apps/br208849) element to the [Resources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.frameworkelement.Resources) property of an element that contains the control you want to style.</span></span>  <span data-ttu-id="c8ae4-182">Wenn Sie Ihren Stil der **Page.Resources**-Eigenschaft hinzufügen, werden Ihre Stile für die gesamte Seite zugängig.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-182">If you add your style to the **Page.Resources** property, your styles will be accessible to the entire page.</span></span> <span data-ttu-id="c8ae4-183">Wenn Sie Ihren Stil der **Application.Resources**-Eigenschaft in der Datei App.xaml hinzufügen, wird der Stil wird für die gesamte App zugänglich.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-183">If you add your style to the **Application.Resources** property in your App.xaml file, the style will be accessible to the entire app.</span></span>

<span data-ttu-id="c8ae4-184">Sie können benannte Stile und allgemeine Stile erstellen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-184">You can create named styles and general styles.</span></span> <span data-ttu-id="c8ae4-185">Eine benannte Formatvorlage muss explizit auf bestimmte Steuerelemente angewendet werden. Ein allgemeiner Stil gilt für alle Steuerelemente, die dem angegebenen **TargetType** entsprechen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-185">A named style must be explicitly applied to specific controls; a general style is applied to any control that matches the specified **TargetType**.</span></span> 

<span data-ttu-id="c8ae4-186">In diesem Beispiel besitzt der erste Stil ein **x:Key-Attribut**, und der Zieltyp ist **Button**.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-186">In this example, the first style has an **x:Key** attribute and its target type is **Button**.</span></span> <span data-ttu-id="c8ae4-187">Die **Style**-Eigenschaft der ersten Schaltfläche wird auf diesen Schlüssel festgelegt, sodass der Stil benannt wird und explizit angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-187">The first button's **Style** property is set to this key, so this style is a named style and must be applied explicitly.</span></span> <span data-ttu-id="c8ae4-188">Der zweite Stil wird automatisch auf die zweite Schaltfläche angewendet, da deren Zieltyp **Button** ist und der Stil kein **x:Key**-Attribut besitzt.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-188">The second style is applied automatically to the second button because its target type is **Button** and the style doesn't have an **x:Key** attribute.</span></span>


```XAML
<Page.Resources>
    <Style x:Key="PurpleStyle" TargetType="Button">
        <Setter Property="FontFamily" Value="Lucida Sans Unicode"/>
        <Setter Property="FontStyle" Value="Italic"/>
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="Foreground" Value="MediumOrchid"/>
    </Style>

    <Style TargetType="Button">
        <Setter Property="Foreground" Value="Orange"/>
    </Style>
</Page.Resources>

<Grid x:Name="LayoutRoot">
    <Button Content="Button" Style="{StaticResource PurpleStyle}"/>
    <Button Content="Button" />
</Grid>
```

<span data-ttu-id="c8ae4-189">Fügen wir nun der App einen Stil hinzu.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-189">Let's add a style to our app.</span></span> <span data-ttu-id="c8ae4-190">Sehen Sie sich unter DetailsPage.xaml die Textblöcke an, die sich neben den Belichtungs-, Temperatur- und Farbton-Schiebereglern befinden.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-190">In DetailsPage.xaml, take a look at the text blocks that sit next to our exposure, temperature, and tint sliders.</span></span> <span data-ttu-id="c8ae4-191">Jeder dieser Text-Blöcke zeigt den Wert eines Schiebereglers an.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-191">Each of these text blocks displays the value of a slider.</span></span> <span data-ttu-id="c8ae4-192">Hier ist der Textblock für den Belichtungs-Schieberegler.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-192">Here's the text block for the exposure slider.</span></span> <span data-ttu-id="c8ae4-193">Sie sehen, dass die Eigenschaften für **Margin**, **VerticalAlignment** und **Padding** festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-193">Notice that the **Margin**, **VerticalAlignment**, and **Padding** properties are set.</span></span>

```XAML
<TextBlock Grid.Row="2"
            Grid.Column="1"
            Margin="10,8,0,0" VerticalAlignment="Center" Padding="0"
            Text="{x:Bind item.Exposure.ToString('N', culture), Mode=OneWay}" />
```
<span data-ttu-id="c8ae4-194">Sehen Sie sich die anderen Textblöcke an – Sie sehen, dass die gleichen Eigenschaften auf den gleichen Wert festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-194">Look at the other text blocks--notice that those same properties are set to the same values.</span></span> <span data-ttu-id="c8ae4-195">Klingt gut für einen Stil...</span><span class="sxs-lookup"><span data-stu-id="c8ae4-195">Sounds like a good candidate for a style...</span></span>

### <a name="create-a-value-text-block-style"></a><span data-ttu-id="c8ae4-196">Erstellen eines Wert-Stils für den Text-Block</span><span class="sxs-lookup"><span data-stu-id="c8ae4-196">Create a value text block style</span></span>

<!-- TODO: add second starting point -->
1. <span data-ttu-id="c8ae4-197">Öffnen Sie DetailsPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-197">Open DetailsPage.xaml.</span></span>

2. <span data-ttu-id="c8ae4-198">Suchen Sie das **Raster**-Steuerelement **EditControlsGrid**.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-198">Find the **Grid** control named **EditControlsGrid**.</span></span> <span data-ttu-id="c8ae4-199">Es enthält unsere Schieberegler und Textfelder.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-199">It contains our sliders and text boxes.</span></span> <span data-ttu-id="c8ae4-200">Beachten Sie, dass das Raster bereits ein Format für unsere Schieberegler definiert.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-200">Notice that the grid already defines a style for our sliders.</span></span> 

    ```XAML
    <Grid x:Name="EditControlsGrid"
            HorizontalAlignment="Stretch"
            Margin="24,48,24,24">
        <Grid.Resources>
            <Style TargetType="Slider">
                <Setter Property="Margin"
                        Value="0,0,0,0" />
                <Setter Property="Padding"
                        Value="0" />
                <Setter Property="MinWidth"
                        Value="100" />
                <Setter Property="StepFrequency"
                        Value="0.1" />
                <Setter Property="TickFrequency"
                        Value="0.1" />
            </Style>
        </Grid.Resources>    
    ```
3. <span data-ttu-id="c8ae4-201">Erstellen Sie einen Stil für einen **TextBlock**, der **Margin** auf "10,8,0,0", sein **VerticalAlignment** auf Center" und sein **Padding** auf "0" festlegt.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-201">Create a style for a **TextBlock** that sets its **Margin** to "10,8,0,0", its **VerticalAlignment** to "Center", and its **Padding** to "0".</span></span>

    **<span data-ttu-id="c8ae4-202">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-202">Before</span></span>**
    ```XAML
        <Grid.Resources>
            <Style TargetType="Slider">
                <Setter Property="Margin"
                        Value="0,0,0,0" />
                <Setter Property="Padding"
                        Value="0" />
                <Setter Property="MinWidth"
                        Value="100" />
                <Setter Property="StepFrequency"
                        Value="0.1" />
                <Setter Property="TickFrequency"
                        Value="0.1" />
            </Style>                           
        </Grid.Resources>
    ```

    **<span data-ttu-id="c8ae4-203">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-203">After</span></span>**
    ```XAML
        <Grid.Resources>
            <Style TargetType="Slider">
                <Setter Property="Margin"
                        Value="0,0,0,0" />
                <Setter Property="Padding"
                        Value="0" />
                <Setter Property="MinWidth"
                        Value="100" />
                <Setter Property="StepFrequency"
                        Value="0.1" />
                <Setter Property="TickFrequency"
                        Value="0.1" />
            </Style>
            <Style TargetType="TextBlock">
                <Setter Property="Margin"
                        Value="10,8,0,0" />
                <Setter Property="VerticalAlignment"
                        Value="Center" />
                <Setter Property="Padding"
                        Value="0" />
            </Style>                            
        </Grid.Resources>
    ```    

4. <span data-ttu-id="c8ae4-204">Erstellen wir daraus eine benannte Formatvorlage, damit wir angeben können, welche **TextBlock**-Steuerelemente dafür gelten.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-204">Let's make this a named style so we can specify which **TextBlock** controls it applies to.</span></span> <span data-ttu-id="c8ae4-205">Legen Sie die **x: Key** -Eigenschaft des Stils auf "ValueTextBox" fest.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-205">Set the style's **x:Key** property to "ValueTextBox".</span></span> 

    **<span data-ttu-id="c8ae4-206">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-206">Before</span></span>**
    ```XAML
            <Style TargetType="TextBlock">
                <Setter Property="Margin"
                        Value="10,8,0,0" />
                <Setter Property="VerticalAlignment"
                        Value="Center" />
                <Setter Property="Padding"
                        Value="0" />
            </Style>                            
    ```    

    **<span data-ttu-id="c8ae4-207">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-207">After</span></span>**
    ```XAML
            <Style TargetType="TextBlock"
                   x:Key="ValueTextBox">
                <Setter Property="Margin"
                        Value="10,8,0,0" />
                <Setter Property="VerticalAlignment"
                        Value="Center" />
                <Setter Property="Padding"
                        Value="0" />
            </Style>                            
    ```    

5. <span data-ttu-id="c8ae4-208">Entfernen Sie für jeden **TextBlock** die Eigenschaften **Margin**, **VerticalAlignment** und **Padding** und legen Sie die **Stil**-Eigenschaft auf "{StaticResource ValueTextBox}" fest.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-208">For each **TextBlock**, remove its **Margin**, **VerticalAlignment**, and **Padding** properties, and set its **Style** property to "{StaticResource ValueTextBox}".</span></span>

    **<span data-ttu-id="c8ae4-209">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-209">Before</span></span>**
    ```XAML
     <TextBlock Grid.Row="2"
                Grid.Column="1"
                Margin="10,8,0,0" VerticalAlignment="Center" Padding="0"
                Text="{x:Bind item.Exposure.ToString('N', culture), Mode=OneWay}" />   
    ```

    **<span data-ttu-id="c8ae4-210">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-210">After</span></span>**
    ```XAML
     <TextBlock Grid.Row="2"
                Grid.Column="1"
                Style="{StaticResource ValueTextBox}"
                Text="{x:Bind item.Exposure.ToString('N', culture), Mode=OneWay}" />   
    ```    

    <span data-ttu-id="c8ae4-211">Nehmen Sie diese Änderung an allen 6 TextBlock-Steuerelementen vor, die den Schiebereglern zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-211">Make this change to all 6 TextBlock controls associated with the sliders.</span></span>

6. <span data-ttu-id="c8ae4-212">Übersetzen Sie die App, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-212">Compile and run the app.</span></span> <span data-ttu-id="c8ae4-213">Es sollte... gleich aussehen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-213">It should look... the same.</span></span> <span data-ttu-id="c8ae4-214">Allerdings sollten Sie ein Gefühl der Zufriedenheit haben, das sich daraus ergibt, effizienten und leichter zu verwaltenden Code zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-214">But you should feel that wonderful sense of satisfaction and accomplishment that comes from writing efficient, maintainable code.</span></span>

<!-- TODO add new start/end points -->
<span data-ttu-id="c8ae4-215">Herzlichen Glückwunsch! Sie haben Teil 2 abgeschlossen!</span><span class="sxs-lookup"><span data-stu-id="c8ae4-215">Congratulations, you've completed Part 2!</span></span>


## <a name="part-3-use-a-control-template-to-make-a-fancy-slider"></a><span data-ttu-id="c8ae4-216">Teil 3: Verwenden einer Steuerelementvorlage zum Erstellen eines ausgefallenen Schiebereglers</span><span class="sxs-lookup"><span data-stu-id="c8ae4-216">Part 3: Use a control template to make a fancy slider</span></span>

<span data-ttu-id="c8ae4-217">Erinnern Sie sich, wie wir in Teil 1 eine Form hinter dem Schieberegler hinzugefügt haben, damit er cool aussieht?</span><span class="sxs-lookup"><span data-stu-id="c8ae4-217">Remember, how in Part 1 we added a shape behind the slider to make it look cool?</span></span>

<span data-ttu-id="c8ae4-218">Jetzt gibt es eine bessere Möglichkeit, den gleichen Effekt zu erzielen: Erstellen Sie eine Steuerelementvorlage.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-218">Well, we got the job done, but there's a better way to achieve the same effect: create a control template.</span></span> 

<!-- TODO add new starting points -->
1. <span data-ttu-id="c8ae4-219">Doppelklicken Sie im Projektmappen-Explorer-Bereich auf **DetailPage.xaml**.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-219">In the Solution Explorer panel, double-click **DetailPage.xaml**.</span></span>

2. <span data-ttu-id="c8ae4-220">Als Nächstes verwenden wir die standardmäßige Steuerelementvorlage für Schieberegler als Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-220">Next, we'll use the default control template for slider as our starting point.</span></span> <span data-ttu-id="c8ae4-221">Fügen Sie diesen XAML-Code dem **Page.Resources**-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-221">Add this XAML to the **Page.Resources** element.</span></span> <span data-ttu-id="c8ae4-222">(Das **Page.Resources**-Element befindet sich am Anfang der Seite.)</span><span class="sxs-lookup"><span data-stu-id="c8ae4-222">(The **Page.Resources** element is toward the beginning of the page.)</span></span>

    ```XAML
    <ControlTemplate x:Key="FancySliderControlTemplate" TargetType="Slider">
        <Grid Margin="{TemplateBinding Padding}">
            <Grid.Resources>
                <Style TargetType="Thumb" x:Key="SliderThumbStyle">
                    <Setter Property="BorderThickness" Value="0" />
                    <Setter Property="Background" Value="{ThemeResource SliderThumbBackground}" />
                    <Setter Property="Template">
                        <Setter.Value>
                            <ControlTemplate TargetType="Thumb">
                                <Border Background="{TemplateBinding Background}"
                                            BorderBrush="{TemplateBinding BorderBrush}"
                                            BorderThickness="{TemplateBinding BorderThickness}"
                                            CornerRadius="4" />
                            </ControlTemplate>
                        </Setter.Value>
                    </Setter>
                </Style>
            </Grid.Resources>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto" />
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <VisualStateManager.VisualStateGroups>
                <VisualStateGroup x:Name="CommonStates">
                    <VisualState x:Name="Normal" />
                    <VisualState x:Name="Pressed">
                        <Storyboard>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalTrackRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackFillPressed}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalTrackRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackFillPressed}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalThumb" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderThumbBackgroundPressed}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalThumb" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderThumbBackgroundPressed}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="SliderContainer" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderContainerBackgroundPressed}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalDecreaseRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackValueFillPressed}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalDecreaseRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackValueFillPressed}" />
                            </ObjectAnimationUsingKeyFrames>
                        </Storyboard>
                    </VisualState>
                    <VisualState x:Name="Disabled">
                        <Storyboard>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HeaderContentPresenter" Storyboard.TargetProperty="Foreground">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderHeaderForegroundDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalDecreaseRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackValueFillDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalTrackRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackFillDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalDecreaseRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackValueFillDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalTrackRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackFillDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalThumb" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderThumbBackgroundDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalThumb" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderThumbBackgroundDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="TopTickBar" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTickBarFillDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="BottomTickBar" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTickBarFillDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="LeftTickBar" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTickBarFillDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="RightTickBar" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTickBarFillDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="SliderContainer" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderContainerBackgroundDisabled}" />
                            </ObjectAnimationUsingKeyFrames>
                        </Storyboard>
                    </VisualState>
                    <VisualState x:Name="PointerOver">
                        <Storyboard>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalTrackRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackFillPointerOver}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalTrackRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackFillPointerOver}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalThumb" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderThumbBackgroundPointerOver}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalThumb" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderThumbBackgroundPointerOver}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="SliderContainer" Storyboard.TargetProperty="Background">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderContainerBackgroundPointerOver}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalDecreaseRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackValueFillPointerOver}" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalDecreaseRect" Storyboard.TargetProperty="Fill">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="{ThemeResource SliderTrackValueFillPointerOver}" />
                            </ObjectAnimationUsingKeyFrames>
                        </Storyboard>
                    </VisualState>
                </VisualStateGroup>
                <VisualStateGroup x:Name="FocusEngagementStates">
                    <VisualState x:Name="FocusDisengaged" />
                    <VisualState x:Name="FocusEngagedHorizontal">
                        <Storyboard>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="SliderContainer" Storyboard.TargetProperty="(Control.IsTemplateFocusTarget)">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="False" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HorizontalThumb" Storyboard.TargetProperty="(Control.IsTemplateFocusTarget)">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="True" />
                            </ObjectAnimationUsingKeyFrames>
                        </Storyboard>
                    </VisualState>
                    <VisualState x:Name="FocusEngagedVertical">
                        <Storyboard>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="SliderContainer" Storyboard.TargetProperty="(Control.IsTemplateFocusTarget)">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="False" />
                            </ObjectAnimationUsingKeyFrames>
                            <ObjectAnimationUsingKeyFrames Storyboard.TargetName="VerticalThumb" Storyboard.TargetProperty="(Control.IsTemplateFocusTarget)">
                                <DiscreteObjectKeyFrame KeyTime="0" Value="True" />
                            </ObjectAnimationUsingKeyFrames>
                        </Storyboard>
                    </VisualState>
                </VisualStateGroup>
            </VisualStateManager.VisualStateGroups>
            <ContentPresenter x:Name="HeaderContentPresenter"
                        x:DeferLoadStrategy="Lazy"
                        Visibility="Collapsed"
                        Foreground="{ThemeResource SliderHeaderForeground}"
                        Margin="{ThemeResource SliderHeaderThemeMargin}"
                        Content="{TemplateBinding Header}"
                        ContentTemplate="{TemplateBinding HeaderTemplate}"
                        FontWeight="{ThemeResource SliderHeaderThemeFontWeight}"
                        TextWrapping="Wrap" />
            <Grid x:Name="SliderContainer"
                        Background="{ThemeResource SliderContainerBackground}"
                        Grid.Row="1"
                        Control.IsTemplateFocusTarget="True">
                <Grid x:Name="HorizontalTemplate" MinHeight="44">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto" />
                        <ColumnDefinition Width="Auto" />
                        <ColumnDefinition Width="*" />
                    </Grid.ColumnDefinitions>
                    <Grid.RowDefinitions>
                        <RowDefinition Height="18" />
                        <RowDefinition Height="Auto" />
                        <RowDefinition Height="18" />
                    </Grid.RowDefinitions>
                    <Rectangle x:Name="HorizontalTrackRect"
                                Fill="{TemplateBinding Background}"
                                Height="{ThemeResource SliderTrackThemeHeight}"
                                Grid.Row="1"
                                Grid.ColumnSpan="3" />
                    <Rectangle x:Name="HorizontalDecreaseRect" Fill="{TemplateBinding Foreground}" Grid.Row="1" />
                    <TickBar x:Name="TopTickBar"
                                Visibility="Collapsed"
                                Fill="{ThemeResource SliderTickBarFill}"
                                Height="{ThemeResource SliderOutsideTickBarThemeHeight}"
                                VerticalAlignment="Bottom"
                                Margin="0,0,0,4"
                                Grid.ColumnSpan="3" />
                    <TickBar x:Name="HorizontalInlineTickBar"
                                Visibility="Collapsed"
                                Fill="{ThemeResource SliderInlineTickBarFill}"
                                Height="{ThemeResource SliderTrackThemeHeight}"
                                Grid.Row="1"
                                Grid.ColumnSpan="3" />
                    <TickBar x:Name="BottomTickBar"
                                Visibility="Collapsed"
                                Fill="{ThemeResource SliderTickBarFill}"
                                Height="{ThemeResource SliderOutsideTickBarThemeHeight}"
                                VerticalAlignment="Top"
                                Margin="0,4,0,0"
                                Grid.Row="2"
                                Grid.ColumnSpan="3" />
                    <Thumb x:Name="HorizontalThumb"
                                Style="{StaticResource SliderThumbStyle}"
                                DataContext="{TemplateBinding Value}"
                                Height="24"
                                Width="8"
                                Grid.Row="0"
                                Grid.RowSpan="3"
                                Grid.Column="1"
                                FocusVisualMargin="-14,-6,-14,-6"
                                AutomationProperties.AccessibilityView="Raw" />
                </Grid>
                <Grid x:Name="VerticalTemplate" MinWidth="44" Visibility="Collapsed">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="*" />
                        <RowDefinition Height="Auto" />
                        <RowDefinition Height="Auto" />
                    </Grid.RowDefinitions>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="18" />
                        <ColumnDefinition Width="Auto" />
                        <ColumnDefinition Width="18" />
                    </Grid.ColumnDefinitions>
                    <Rectangle x:Name="VerticalTrackRect"
                                Fill="{TemplateBinding Background}"
                                Width="{ThemeResource SliderTrackThemeHeight}"
                                Grid.Column="1"
                                Grid.RowSpan="3" />
                    <Rectangle x:Name="VerticalDecreaseRect"
                                Fill="{TemplateBinding Foreground}"
                                Grid.Column="1"
                                Grid.Row="2" />
                    <TickBar x:Name="LeftTickBar"
                                Visibility="Collapsed"
                                Fill="{ThemeResource SliderTickBarFill}"
                                Width="{ThemeResource SliderOutsideTickBarThemeHeight}"
                                HorizontalAlignment="Right"
                                Margin="0,0,4,0"
                                Grid.RowSpan="3" />
                    <TickBar x:Name="VerticalInlineTickBar"
                                Visibility="Collapsed"
                                Fill="{ThemeResource SliderInlineTickBarFill}"
                                Width="{ThemeResource SliderTrackThemeHeight}"
                                Grid.Column="1"
                                Grid.RowSpan="3" />
                    <TickBar x:Name="RightTickBar"
                                Visibility="Collapsed"
                                Fill="{ThemeResource SliderTickBarFill}"
                                Width="{ThemeResource SliderOutsideTickBarThemeHeight}"
                                HorizontalAlignment="Left"
                                Margin="4,0,0,0"
                                Grid.Column="2"
                                Grid.RowSpan="3" />
                    <Thumb x:Name="VerticalThumb"
                                Style="{StaticResource SliderThumbStyle}"
                                DataContext="{TemplateBinding Value}"
                                Width="24"
                                Height="8"
                                Grid.Row="1"
                                Grid.Column="0"
                                Grid.ColumnSpan="3"
                                FocusVisualMargin="-6,-14,-6,-14"
                                AutomationProperties.AccessibilityView="Raw" />
                </Grid>
            </Grid>
        </Grid>
    </ControlTemplate>
    ```

    <span data-ttu-id="c8ae4-223">WOW, das ist eine Menge XAML!</span><span class="sxs-lookup"><span data-stu-id="c8ae4-223">Wow, that's a lot of XAML!</span></span> <span data-ttu-id="c8ae4-224">Steuerelementvorlagen sind ein leistungsfähiges Feature, sie können jedoch sehr komplex sein, daher empfiehlt sich in der Regel, mit der Standardvorlage zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-224">Control templates are a powerful feature, but they can be quite complex, which is why it's usually a good idea to start from the default template.</span></span> 
    
3. <span data-ttu-id="c8ae4-225">Suchen Sie im gerade hinzugefügten **ControlTemplate** das Raster-Steuerelement mit dem Namen **HorizontalTemplate**.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-225">Within the **ControlTemplate** you just added, find the grid control named **HorizontalTemplate**.</span></span> <span data-ttu-id="c8ae4-226">Dieses Raster definiert den Teil der Vorlage, die wir ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-226">This grid defines the portion of the template that we want to change.</span></span>

    ```XAML
    <Grid x:Name="HorizontalTemplate" MinHeight="44">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="*" />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="18" />
            <RowDefinition Height="Auto" />
            <RowDefinition Height="18" />
        </Grid.RowDefinitions>
    ```

5.  <span data-ttu-id="c8ae4-227">Erstellen Sie ein Polygon, das genauso funktioniert wie das Polygon, das Sie für den Belichtungs-Schieberegler in Teil 1 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-227">Create a polygon that's just like the polygon you created for the exposure slider in Part 1.</span></span> <span data-ttu-id="c8ae4-228">Fügen Sie das Polygon hinzu, nachdem Sie den **Grid.RowDefinitions**-Tag geschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-228">Add the polygon after the closing **Grid.RowDefinitions** tag.</span></span> <span data-ttu-id="c8ae4-229">Legen Sie **Grid.Row** auf "0", **Grid.RowSpan** auf "3" und **Grid.ColumnSpan** auf "3" fest.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-229">Set **Grid.Row** to "0", **Grid.RowSpan** to "3", and **Grid.ColumnSpan** to "3".</span></span> 

    **<span data-ttu-id="c8ae4-230">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-230">Before</span></span>**
    ```XAML
    <Grid x:Name="HorizontalTemplate" MinHeight="44">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="*" />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="18" />
            <RowDefinition Height="Auto" />
            <RowDefinition Height="18" />
        </Grid.RowDefinitions>        
    ```

    **<span data-ttu-id="c8ae4-231">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-231">After</span></span>**
    ```XAML
    <Grid x:Name="HorizontalTemplate" MinHeight="44">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="*" />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="18" />
            <RowDefinition Height="Auto" />
            <RowDefinition Height="18" />
        </Grid.RowDefinitions>
        <Polygon Grid.Row="0" Grid.RowSpan="3"  Grid.ColumnSpan="3" Stretch="Fill"
                    Points="0,20 200,20 200,0" HorizontalAlignment="Stretch"  
                    VerticalAlignment="Center" Height="20" >
            <Polygon.Fill>
                <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                    <LinearGradientBrush.GradientStops>
                        <GradientStop Offset="0" Color="Black" />
                        <GradientStop Offset="1" Color="White" />
                    </LinearGradientBrush.GradientStops>
                </LinearGradientBrush>
            </Polygon.Fill>
        </Polygon>           
    ```

6. <span data-ttu-id="c8ae4-232">Entfernen Sie die **Polygon.Fill**-Einstellung.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-232">Remove the **Polygon.Fill** setting.</span></span> <span data-ttu-id="c8ae4-233">Legen Sie **Fill** auf "{TemplateBinding Background}" fest.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-233">Set **Fill** to "{TemplateBinding Background}".</span></span> <span data-ttu-id="c8ae4-234">Dadurch wird die **Hintergrund**-Eigenschaft des Schiebereglers auf die Eigenschaft **Fill** des Polygons festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-234">This makes it so that setting the **Background** property of the slider sets the **Fill** property of the polygon.</span></span> 

    **<span data-ttu-id="c8ae4-235">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-235">Before</span></span>**
    ```XAML
        <Polygon Grid.Row="0" Grid.RowSpan="3"  Grid.ColumnSpan="3" Stretch="Fill"
                    Points="0,20 200,20 200,0" HorizontalAlignment="Stretch"  
                    VerticalAlignment="Center" Height="20" >
            <Polygon.Fill>
                <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                    <LinearGradientBrush.GradientStops>
                        <GradientStop Offset="0" Color="Black" />
                        <GradientStop Offset="1" Color="White" />
                    </LinearGradientBrush.GradientStops>
                </LinearGradientBrush>
            </Polygon.Fill>
        </Polygon>           
    ```
    
    **<span data-ttu-id="c8ae4-236">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-236">After</span></span>**
    ```XAML
        <Polygon Grid.Row="0" Grid.RowSpan="3"  Grid.ColumnSpan="3" Stretch="Fill"
                    Points="0,20 200,20 200,0" HorizontalAlignment="Stretch"  
                    VerticalAlignment="Center" Height="20" 
                    Fill="{TemplateBinding Background}">
        </Polygon>           
    ```    

7. <span data-ttu-id="c8ae4-237">Hinter dem Polygon, den Sie gerade hinzugefügt haben, wird ein Rechteck mit dem Namen **HorizontalTrackRect** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-237">Just after the polygon you added, there's a rectangle named **HorizontalTrackRect**.</span></span> <span data-ttu-id="c8ae4-238">Entfernen Sie die **Fill**-Eigenschaft des Rechtecks, damit das Rechteck nicht angezeigt wird und unsere Polygonform nicht blockiert.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-238">Remove the Rectangle's **Fill** setting so that the rectangle won't be visible and won't block our polygon shape.</span></span> <span data-ttu-id="c8ae4-239">(Wir möchten das Rechteck nicht vollständig entfernen, da die Steuerelementvorlage auch für die Interaktion visueller Objekte wie z.B. Hover verwendet wird.)</span><span class="sxs-lookup"><span data-stu-id="c8ae4-239">(We don't want to completely remove the rectangle because the control template also uses it for interaction visuals, such as hover.)</span></span>

    **<span data-ttu-id="c8ae4-240">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-240">Before</span></span>**
    ```XAML
        <Rectangle x:Name="HorizontalTrackRect"
                    Fill="{TemplateBinding Background}"
                    Height="{ThemeResource SliderTrackThemeHeight}"
                    Grid.Row="1"
                    Grid.ColumnSpan="3" />          
    ```
    
    **<span data-ttu-id="c8ae4-241">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-241">After</span></span>**
    ```XAML
        <Rectangle x:Name="HorizontalTrackRect"
                    Height="{ThemeResource SliderTrackThemeHeight}"
                    Grid.Row="1"
                    Grid.ColumnSpan="3" />
    ```

    <span data-ttu-id="c8ae4-242">Herzlichen Glückwunsch! Sie haben diese Vorlage vollständig bearbeitet!</span><span class="sxs-lookup"><span data-stu-id="c8ae4-242">You're done with the template!</span></span> <span data-ttu-id="c8ae4-243">Nun müssen wir sie auf unsere Schieberegler anwenden.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-243">Now we need to apply it to our sliders.</span></span> 
    
8. <span data-ttu-id="c8ae4-244">Aktualisieren wir unseren Belichtungs-Schieberegler.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-244">Let's update our exposure slider.</span></span>

    * <span data-ttu-id="c8ae4-245">Legen Sie die **Vorlage**-Eigenschaft des Schiebereglers auf "{StaticResource FancySliderControlTemplate}" fest.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-245">Set the slider's **Template** property to "{StaticResource FancySliderControlTemplate}".</span></span>
    * <span data-ttu-id="c8ae4-246">Entfernen Sie die Einstellung des Schiebereglers für den Hintergrund = "Transparent".</span><span class="sxs-lookup"><span data-stu-id="c8ae4-246">Remove the slider's Background="Transparent" setting.</span></span> 
    * <span data-ttu-id="c8ae4-247">Legen Sie den Schiebereglerhintergrund auf einen linearen Farbverlauf fest, der von Schwarz in Weiß übergeht.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-247">Set the slider's Background to a linear gradient that transitions from black to white.</span></span>
    * <span data-ttu-id="c8ae4-248">Entfernen Sie das Hintergrund-Polygon, das wir in Teil 1 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-248">Remove the background polygon we created in Part 1.</span></span>
        
    **<span data-ttu-id="c8ae4-249">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-249">Before</span></span>**
    ```XAML
    <Polygon Grid.Row="2" Stretch="Fill"
                Points="0,20 200,20 200,0" HorizontalAlignment="Stretch"  
                VerticalAlignment="Center" Height="20">
        <Polygon.Fill>
            <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                <LinearGradientBrush.GradientStops>
                    <GradientStop Offset="0" Color="Black" />
                    <GradientStop Offset="1" Color="White" />
                </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
        </Polygon.Fill>
    </Polygon>
    <Slider Header="Exposure" 
            Grid.Row="2" Background="Transparent" Foreground="Transparent"
            Value="{x:Bind item.Exposure, Mode=TwoWay}"
            Minimum="-2"
            Maximum="2"
            Template="{StaticResource FancySliderControlTemplate}"/>    
    ```
    
    **<span data-ttu-id="c8ae4-250">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-250">After</span></span>**
    ```XAML
    <Slider Header="Exposure" 
            Grid.Row="2"  Foreground="Transparent"
            Value="{x:Bind item.Exposure, Mode=TwoWay}"
            Minimum="-2"
            Maximum="2"
            Template="{StaticResource FancySliderControlTemplate}">
        <Slider.Background>
            <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                <LinearGradientBrush.GradientStops>
                    <GradientStop Offset="0" Color="Black" />
                    <GradientStop Offset="1" Color="White" />
                </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
        </Slider.Background>
    </Slider>
    ```        
9. <span data-ttu-id="c8ae4-251">Führen Sie die gleichen Updates auf den Schieberegler für die Temperatur aus.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-251">Make the same updates to the temperature slider.</span></span>

    **<span data-ttu-id="c8ae4-252">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-252">Before</span></span>**
    ```XAML
    <Polygon Grid.Row="3" Stretch="Fill"
                Points="0,20 200,20 200,0" HorizontalAlignment="Stretch"  
                VerticalAlignment="Center" Height="20">
        <Polygon.Fill>
            <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                <LinearGradientBrush.GradientStops>
                    <GradientStop Offset="0" Color="Blue" />
                    <GradientStop Offset="1" Color="Yellow" />
                </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
        </Polygon.Fill>
    </Polygon>
    <Slider Header="Temperature"
            Grid.Row="3" Background="Transparent" Foreground="Transparent"
            Value="{x:Bind item.Temperature, Mode=TwoWay}"
            Minimum="-1"
            Maximum="1" />
    ```
    
    **<span data-ttu-id="c8ae4-253">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-253">After</span></span>**
    ```XAML
    <Slider Header="Temperature"
            Grid.Row="3" Foreground="Transparent"
            Value="{x:Bind item.Temperature, Mode=TwoWay}"
            Minimum="-1"
            Maximum="1"
            Template="{StaticResource FancySliderControlTemplate}">
        <Slider.Background>
            <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                <LinearGradientBrush.GradientStops>
                    <GradientStop Offset="0" Color="Blue" />
                    <GradientStop Offset="1" Color="Yellow" />
                </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
        </Slider.Background>
    </Slider>
    ```    

10. <span data-ttu-id="c8ae4-254">Führen Sie die gleichen Updates auf den Schieberegler für den Farbton aus.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-254">Make the same updates to the tint slider.</span></span>

    **<span data-ttu-id="c8ae4-255">Vorher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-255">Before</span></span>**
    ```XAML
    <Polygon Grid.Row="4" Stretch="Fill"
                Points="0,20 200,20 200,0" HorizontalAlignment="Stretch"  
                VerticalAlignment="Center" Height="20">
        <Polygon.Fill>
            <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                <LinearGradientBrush.GradientStops>
                    <GradientStop Offset="0" Color="Red" />
                    <GradientStop Offset="1" Color="Green" />
                </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
        </Polygon.Fill>
    </Polygon>
    <Slider Header="Tint"
            Grid.Row="4" Background="Transparent" Foreground="Transparent"
            Value="{x:Bind item.Tint, Mode=TwoWay}"
            Minimum="-1"
            Maximum="1" />
    ```
    
    **<span data-ttu-id="c8ae4-256">Nachher</span><span class="sxs-lookup"><span data-stu-id="c8ae4-256">After</span></span>**
    ```XAML
    <Slider Header="Tint"
            Grid.Row="4" Foreground="Transparent"
            Value="{x:Bind item.Tint, Mode=TwoWay}"
            Minimum="-1"
            Maximum="1"
            Template="{StaticResource FancySliderControlTemplate}">
        <Slider.Background>
            <LinearGradientBrush StartPoint="0,0.5" EndPoint="1,0.5">
                <LinearGradientBrush.GradientStops>
                    <GradientStop Offset="0" Color="Red" />
                    <GradientStop Offset="1" Color="Green" />
                </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
        </Slider.Background>
    </Slider>
    ```        

11. <span data-ttu-id="c8ae4-257">Übersetzen Sie die App, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-257">Compile and run the app.</span></span> 

    ![Sie haben die besten Schieberegler in der ganzen Welt](../basics/images/xaml-basics/style-sliders-templates.png)
    
    <span data-ttu-id="c8ae4-259">Wie Sie sehen können, verbessern unsere Updates die Positionierung des Polygons. Jetzt ist das untere Ende des Polygons am unteren Rand der Ziehpunkt des Schiebereglers ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-259">As you can see, our updates improved the positioning of the polygon; now the bottom of the polygon is aligned to the bottom of the slider thumb.</span></span>
    
<!-- TODO correct folder -->
<span data-ttu-id="c8ae4-260">Herzlichen Glückwunsch! Sie haben das Lernprogramm abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="c8ae4-260">Congratulations, you've finished the tutorial!</span></span> <span data-ttu-id="c8ae4-261">Wenn Sie nicht weiterkommen oder die endgültige Lösung nicht anzeigen können, finden Sie das fertige Beispiel unter [UWP-App-Beispielrepository](https://github.com/Microsoft/Windows-universal-samples).</span><span class="sxs-lookup"><span data-stu-id="c8ae4-261">If you got stuck and want to see the final solution, you can find the complete sample in the [UWP app sample repository](https://github.com/Microsoft/Windows-universal-samples).</span></span>