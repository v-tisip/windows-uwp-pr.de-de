---
author: muhsinking
title: 'Tutorial: Erstellen von adaptiven Layouts'
description: In diesem Artikel werden die Grundlagen für adaptives Layout in XAML behandelt
keywords: XAML, UWP, Erste Schritte
ms.author: mukin
ms.date: 08/30/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 000aa2d8f3684aa813b85076d9124a87a71b6a8c
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6024268"
---
# <a name="tutorial-create-adaptive-layouts"></a><span data-ttu-id="b3998-104">Tutorial: Erstellen von adaptiven Layouts</span><span class="sxs-lookup"><span data-stu-id="b3998-104">Tutorial: Create adaptive layouts</span></span>

<span data-ttu-id="b3998-105">In diesem Lernprogramm werden die Grundlagen der Verwendung der adaptiven und maßgeschneiderten Layoutfeatures von XAML beschrieben, mit denen Sie Apps erstellen können, die auf jedem Gerät exzellent aussehen.</span><span class="sxs-lookup"><span data-stu-id="b3998-105">This tutorial covers the basics of using XAML's adaptive and tailored layout features, which let you create apps that look at home on any device.</span></span> <span data-ttu-id="b3998-106">Sie erfahren, wie Sie ein neues DataTemplate erstellen, Fenster-Andockpunkte hinzufügen und das Layout Ihrer App mit den Elementen von VisualStateManager und AdaptiveTrigger anpassen.</span><span class="sxs-lookup"><span data-stu-id="b3998-106">You'll learn how to create a new DataTemplate, add window snap points, and tailor your app's layout using the VisualStateManager and AdaptiveTrigger elements.</span></span> <span data-ttu-id="b3998-107">Wir verwenden diese Tools zum Optimieren der Bildbearbeitungs-Beispiel-App für kleinere Gerätebildschirme.</span><span class="sxs-lookup"><span data-stu-id="b3998-107">We'll use these tools to optimize an image editing program for smaller device screens.</span></span> 

<span data-ttu-id="b3998-108">Das Bildbearbeitungsprogramm, an dem Sie arbeiten werden, hat zwei Seiten/Bildschirme:</span><span class="sxs-lookup"><span data-stu-id="b3998-108">The image editing program you'll be working on has two pages/screens:</span></span>

<span data-ttu-id="b3998-109">Die **Hauptseite** zeigt eine Ansicht der Foto-Galerie, zusammen mit einigen Informationen über jede Bilddatei an.</span><span class="sxs-lookup"><span data-stu-id="b3998-109">The **main page**, which displays a photo gallery view, along with some information about each image file.</span></span>

![MainPage](../basics/images/xaml-basics/mainpage.png)

<span data-ttu-id="b3998-111">Die **Detailsseite** zeigt ein einzelnes Foto an, nachdem es ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="b3998-111">The **details page**, which displays a single photo after it has been selected.</span></span> <span data-ttu-id="b3998-112">Über ein Flyout-Menü kann das Foto bearbeitet, umbenannt und gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b3998-112">A flyout editing menu allows the photo to be altered, renamed, and saved.</span></span>

![DetailPage](../basics/images/xaml-basics/detailpage.png)

## <a name="prerequisites"></a><span data-ttu-id="b3998-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b3998-114">Prerequisites</span></span>

* <span data-ttu-id="b3998-115">Visual Studio 2017: [Visual Studio 2017 Community herunterladen (kostenlos)](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&campaign=WinDevCenter&ocid=wdgcx-windevcenter-community-download)</span><span class="sxs-lookup"><span data-stu-id="b3998-115">Visual Studio 2017: [Download Visual Studio 2017 Community (free)](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&campaign=WinDevCenter&ocid=wdgcx-windevcenter-community-download)</span></span> 
* <span data-ttu-id="b3998-116">Windows 10 SDK (10.0.15063.468 oder höher): [Neuestes Windows SDK herunterladen (kostenlos)](https://developer.microsoft.com/windows/downloads/windows-10-sdk)</span><span class="sxs-lookup"><span data-stu-id="b3998-116">Windows 10 SDK (10.0.15063.468 or later):  [Download the latest Windows SDK (free)](https://developer.microsoft.com/windows/downloads/windows-10-sdk)</span></span>
* <span data-ttu-id="b3998-117">Windows Mobile-Emulator: [Download des Windows 10 Mobile Emulators (kostenlos)](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive)</span><span class="sxs-lookup"><span data-stu-id="b3998-117">Windows mobile emulator: [Download the Windows 10 mobile emulator (free)](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive)</span></span>

## <a name="part-0-get-the-starter-code-from-github"></a><span data-ttu-id="b3998-118">Teil 0: Startcode von Github holen</span><span class="sxs-lookup"><span data-stu-id="b3998-118">Part 0: Get the starter code from github</span></span>

<span data-ttu-id="b3998-119">Für dieses Tutorial starten Sie mit einer vereinfachten Version des PhotoLab-Beispiels.</span><span class="sxs-lookup"><span data-stu-id="b3998-119">For this tutorial, you'll start with a simplified version of the PhotoLab sample.</span></span> 

1. <span data-ttu-id="b3998-120">Wechseln Sie zu [https://github.com/Microsoft/Windows-appsample-photo-lab](https://github.com/Microsoft/Windows-appsample-photo-lab).</span><span class="sxs-lookup"><span data-stu-id="b3998-120">Go to [https://github.com/Microsoft/Windows-appsample-photo-lab](https://github.com/Microsoft/Windows-appsample-photo-lab).</span></span> <span data-ttu-id="b3998-121">Sie gelangen auf die GitHub-Seite für das Beispiel.</span><span class="sxs-lookup"><span data-stu-id="b3998-121">This takes you to the GitHub page for the sample.</span></span> 
2. <span data-ttu-id="b3998-122">Als nächstes müssen Sie das Beispiel klonen oder herunterladen.</span><span class="sxs-lookup"><span data-stu-id="b3998-122">Next, you'll need to clone or download the sample.</span></span> <span data-ttu-id="b3998-123">Klicken Sie auf die Schaltfläche **Clone or download**.</span><span class="sxs-lookup"><span data-stu-id="b3998-123">Click the **Clone or download** button.</span></span> <span data-ttu-id="b3998-124">Ein Untermenü erscheint.</span><span class="sxs-lookup"><span data-stu-id="b3998-124">A sub-menu appears.</span></span>
    <figure>
        <img src="../basics/images/xaml-basics/clone-repo.png" alt="The Clone or download menu on GitHub">
        <figcaption><span data-ttu-id="b3998-125">Das <b>Clone or download</b>-Menü auf der GitHub-Seite des Fotolbeispiels.</span><span class="sxs-lookup"><span data-stu-id="b3998-125">The <b>Clone or download</b> menu on the Photo lab sample's GitHub page.</span></span></figcaption>
    </figure>

    **<span data-ttu-id="b3998-126">Wenn Sie mit GitHub nicht vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="b3998-126">If you're not familiar with GitHub:</span></span>**
    
    <span data-ttu-id="b3998-127">a.</span><span class="sxs-lookup"><span data-stu-id="b3998-127">a.</span></span> <span data-ttu-id="b3998-128">Klicken Sie auf **Download ZIP** und speichern Sie die Datei lokal.</span><span class="sxs-lookup"><span data-stu-id="b3998-128">Click **Download ZIP** and save the file locally.</span></span> <span data-ttu-id="b3998-129">Es wird eine ZIP-Datei heruntergeladen, die alle benötigten Projektdateien enthält.</span><span class="sxs-lookup"><span data-stu-id="b3998-129">This downloads a .zip file that contains all the project files you need.</span></span>
    <span data-ttu-id="b3998-130">b.</span><span class="sxs-lookup"><span data-stu-id="b3998-130">b.</span></span> <span data-ttu-id="b3998-131">Entpacken Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="b3998-131">Extract the file.</span></span> <span data-ttu-id="b3998-132">Verwenden Sie den Datei-Explorer, um zu der gerade heruntergeladenen ZIP-Datei zu navigieren, klicken Sie mit der rechten Maustaste darauf und wählen Sie **Alle extrahieren...** aus. c.</span><span class="sxs-lookup"><span data-stu-id="b3998-132">Use the File Explorer to navigate to the .zip file you just downloaded, right-click it, and select **Extract All...**. c.</span></span> <span data-ttu-id="b3998-133">Navigieren Sie zu Ihrer lokalen Kopie des Beispiels und wechseln Sie zum `Windows-appsample-photo-lab-master\xaml-basics-starting-points\adaptive-layout`-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="b3998-133">Navigate to your local copy of the sample and go the `Windows-appsample-photo-lab-master\xaml-basics-starting-points\adaptive-layout` directory.</span></span>    

    **<span data-ttu-id="b3998-134">Wenn Sie mit GitHub vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="b3998-134">If you are familiar with GitHub:</span></span>**

    <span data-ttu-id="b3998-135">a.</span><span class="sxs-lookup"><span data-stu-id="b3998-135">a.</span></span> <span data-ttu-id="b3998-136">Klonen Sie den Master-Branch des Repos lokal.</span><span class="sxs-lookup"><span data-stu-id="b3998-136">Clone the master branch of the repo locally.</span></span>
    <span data-ttu-id="b3998-137">b.</span><span class="sxs-lookup"><span data-stu-id="b3998-137">b.</span></span> <span data-ttu-id="b3998-138">Navigieren Sie zum `Windows-appsample-photo-lab\xaml-basics-starting-points\adaptive-layout`-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="b3998-138">Navigate to the `Windows-appsample-photo-lab\xaml-basics-starting-points\adaptive-layout` directory.</span></span>

3. <span data-ttu-id="b3998-139">Öffnen Sie das Projekt durch einen Klick auf `Photolab.sln`.</span><span class="sxs-lookup"><span data-stu-id="b3998-139">Open the project by clicking `Photolab.sln`.</span></span>

## <a name="part-1-run-the-mobile-emulator"></a><span data-ttu-id="b3998-140">Teil 1: Ausführen des Mobile-Emulators</span><span class="sxs-lookup"><span data-stu-id="b3998-140">Part 1: Run the mobile emulator</span></span>

<span data-ttu-id="b3998-141">Stellen Sie sicher, dass Ihre Lösungsplattform in der Visual Studio-Symbolleiste auf x86 oder x64 und nicht ARM festgelegt ist, und ändern Sie Ihr Zielgerät vom lokalen Computer auf eines der Mobile Emulatoren, die Sie installiert haben (z.B. Mobile Emulator 10.0.15063 WVGA 5 Zoll 1GB).</span><span class="sxs-lookup"><span data-stu-id="b3998-141">In the Visual Studio toolbar, make sure your Solution Platform is set to x86 or x64, not ARM, and then change your target device from Local Machine to one of the mobile emulators that you've installed (for example, Mobile Emulator 10.0.15063 WVGA 5 inch 1GB).</span></span> <span data-ttu-id="b3998-142">Führen Sie die Fotogalerie-App im ausgewählten Mobile Emulator durch Drücken von **F5** aus.</span><span class="sxs-lookup"><span data-stu-id="b3998-142">Try running the Photo Gallery app in the mobile emulator you've selected by pressing **F5**.</span></span>

<span data-ttu-id="b3998-143">Sobald die App gestartet wird, sehen Sie wahrscheinlich, dass die App zwar funktioniert, sie allerdings auf einem kleinen Viewport nicht so gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="b3998-143">As soon as the app starts, you'll probably notice that while the app works, it doesn't look great on such a small viewport.</span></span> <span data-ttu-id="b3998-144">Das dynamische Grid-Element passt sich der begrenzten Bildschirmfläche so gut wie möglich an, indem es die Anzahl der angezeigten Spalten reduziert. Dies erzeugt ein einfallsloses Layout, das unangebracht für diesen kleinen Viewport aussieht.</span><span class="sxs-lookup"><span data-stu-id="b3998-144">The fluid Grid element tries to accommodate for the limited screen real estate by reducing the number of columns displayed, but we are left with a layout that looks uninspired and ill-fitted to such a small viewport.</span></span>

![Mobiles Layout: danach](../basics/images/xaml-basics/adaptive-layout-mobile-before.png)

## <a name="part-2-build-a-tailored-mobile-layout"></a><span data-ttu-id="b3998-146">Teil 2: Erstellen eines mobilen maßgeschneiderten Layouts</span><span class="sxs-lookup"><span data-stu-id="b3998-146">Part 2: Build a tailored mobile layout</span></span>
<span data-ttu-id="b3998-147">Damit diese App auch auf kleineren Geräten gut aussieht, werden wir eine Reihe von Stilen auf unserer XAML-Seite erstellen, die nur dann angewandt wird, wenn ein mobiles Gerät erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="b3998-147">To make this app look good on smaller devices, we're going to create a separate set of styles in our XAML page that will only be used if a mobile device is detected.</span></span>

### <a name="create-a-new-datatemplate"></a><span data-ttu-id="b3998-148">Erstellen einer neuen Datenvorlage</span><span class="sxs-lookup"><span data-stu-id="b3998-148">Create a new DataTemplate</span></span>
<span data-ttu-id="b3998-149">Wir werden die Fotogalerie-Ansicht der Anwendung anpassen, indem wir eine neue Datenvorlage für die Bilder erstellen.</span><span class="sxs-lookup"><span data-stu-id="b3998-149">We're going to tailor the gallery view of the application by creating a new DataTemplate for the images.</span></span> <span data-ttu-id="b3998-150">Öffnen Sie MainPage.xaml im Projektmappen-Explorer und fügen Sie den **Page.Resources**-Tags folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3998-150">Open MainPage.xaml from the Solution Explorer, and add the following code within the **Page.Resources** tags.</span></span>

```XAML
<DataTemplate x:Key="ImageGridView_MobileItemTemplate"
              x:DataType="local:ImageFileInfo">

    <!-- Create image grid -->
    <Grid Height="{Binding ItemSize, ElementName=page}"
          Width="{Binding ItemSize, ElementName=page}">
        
        <!-- Place image in grid, stretching it to fill the pane-->
        <Image x:Name="ItemImage"
               Source="{x:Bind ImagePreview}"
               Stretch="UniformToFill">
        </Image>

    </Grid>
</DataTemplate>
```

<span data-ttu-id="b3998-151">Diese Galerievorlage speichert durch den Wegfall des Bilderrahmens Platz auf dem Bildschirm und beseitigt die Bildmetadaten (Dateiname, Bewertungen usw.) unter jeder Miniaturansicht.</span><span class="sxs-lookup"><span data-stu-id="b3998-151">This gallery template saves screen real estate by eliminating the border around images, and getting rid of the image metadata (filename, ratings, and so on.) below each thumbnail.</span></span> <span data-ttu-id="b3998-152">Stattdessen wird jede Miniaturansicht als ein einfaches Quadrat angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b3998-152">Instead, we show each thumbnail as a simple square.</span></span>

### <a name="add-metadata-to-a-tooltip"></a><span data-ttu-id="b3998-153">Einer QuickInfo Metadaten hinzufügen</span><span class="sxs-lookup"><span data-stu-id="b3998-153">Add metadata to a tooltip</span></span>
<span data-ttu-id="b3998-154">Wir möchten dennoch, das der Benutzer Zugriff auf die Metadaten für jedes Bild hat, daher fügen wir wir jedem Bildelement eine QuickInfo hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3998-154">We still want the user to be able to access the metadata for each image, so we'll add a tooltip to each image item.</span></span> <span data-ttu-id="b3998-155">Fügen Sie folgenden Code in die **Bild**-Tags für die Datenvorlage hinzu, die Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="b3998-155">Add the following code within the **Image** tags of the DataTemplate you just created.</span></span>

```XAML
<Image ...>

    <!-- Add a tooltip to the image that displays metadata -->
    <ToolTipService.ToolTip>
        <ToolTip x:Name="tooltip">

            <!-- Arrange tooltip elements vertically -->
            <StackPanel Orientation="Vertical"
                        Grid.Row="1">

                <!-- Image title -->
                <TextBlock Text="{x:Bind ImageTitle, Mode=OneWay}"
                           HorizontalAlignment="Center"
                           Style="{StaticResource SubtitleTextBlockStyle}" />

                <!-- Arrange elements horizontally -->
                <StackPanel Orientation="Horizontal"
                            HorizontalAlignment="Center">

                    <!-- Image file type -->
                    <TextBlock Text="{x:Bind ImageFileType}"
                               HorizontalAlignment="Center"
                               Style="{StaticResource CaptionTextBlockStyle}" />

                    <!-- Image dimensions -->
                    <TextBlock Text="{x:Bind ImageDimensions}"
                               HorizontalAlignment="Center"
                               Style="{StaticResource CaptionTextBlockStyle}"
                               Margin="8,0,0,0" />
                </StackPanel>
            </StackPanel>
        </ToolTip>
    </ToolTipService.ToolTip>
</Image>
```

<span data-ttu-id="b3998-156">Dadurch werden Titel, Dateityp und Dimensionen eines Bilds angezeigt, wenn Sie mit dem Mauszeiger über die Miniaturansicht zeigen (oder halten Sie den Touchscreen gedrückt).</span><span class="sxs-lookup"><span data-stu-id="b3998-156">This will show the title, file type, and dimensions of an image when you hover the mouse over the thumbnail (or press and hold on a touch screen).</span></span>

### <a name="add-a-visualstatemanager-and-statetrigger"></a><span data-ttu-id="b3998-157">Hinzufügen eines VisualStateManager und StateTrigger</span><span class="sxs-lookup"><span data-stu-id="b3998-157">Add a VisualStateManager and StateTrigger</span></span>

<span data-ttu-id="b3998-158">Wir haben jetzt ein neues Layout für die Daten erstellt, aber die App weiß derzeit nicht, wann dieses Layout anstelle der Standardstile verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b3998-158">We've now created a new layout for our data, but the app currently has no way of knowing when to use this layout over the default styles.</span></span> <span data-ttu-id="b3998-159">Um dieses Problem zu beheben, müssen wir einen **VisualStateManager** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b3998-159">To fix this, we'll need to add a **VisualStateManager**.</span></span> <span data-ttu-id="b3998-160">Fügen Sie dem Stammelement der Seite **RelativePanel** folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3998-160">Add the following code to the root element of the page, **RelativePanel**.</span></span>

```XAML
<VisualStateManager.VisualStateGroups>
    <VisualStateGroup>

        <!-- Add a new VisualState for mobile devices -->
        <VisualState x:Key="Mobile">

            <!-- Trigger visualstate when a mobile device is detected -->
            <VisualState.StateTriggers>
                <local:MobileScreenTrigger InteractionMode="Touch" />
            </VisualState.StateTriggers>

        </VisualState>
    </VisualStateGroup>
</VisualStateManager.VisualStateGroups>
```

<span data-ttu-id="b3998-161">Dadurch wird ein neuer **VisualState** und **StateTrigger**hinzugefügt, der ausgelöst wird, wenn die App erkennt, dass sie auf einem mobilen Gerät ausgeführt wird (die Logik für diesen Vorgang finden Sie im MobileScreenTrigger.cs. Dies wird für Sie im PhotoLab-Verzeichnis bereitgestellt).</span><span class="sxs-lookup"><span data-stu-id="b3998-161">This adds a new **VisualState** and **StateTrigger**, which will be triggered when the app detects that it is running on a mobile device (the logic for this operation can be found in MobileScreenTrigger.cs, which is provided for you in the PhotoLab directory).</span></span> <span data-ttu-id="b3998-162">Wenn **StateTrigger** gestartet wird, verwendet die App alle Layoutattribute, die diesem **VisualState** zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="b3998-162">When the **StateTrigger** starts, the app will use whatever layout attributes are assigned to this **VisualState**.</span></span>

### <a name="add-visualstate-setters"></a><span data-ttu-id="b3998-163">Hinzufügen von VisualState-Setter</span><span class="sxs-lookup"><span data-stu-id="b3998-163">Add VisualState setters</span></span>
<span data-ttu-id="b3998-164">Als Nächstes verwenden wir **VisualState**-Setter, um den **VisualStateManager** anzuweisen, welche bestimmten Attributen angewendet werden sollen, wenn der Zustand ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="b3998-164">Next, we'll use **VisualState** setters to tell the **VisualStateManager** what attributes to apply when the state is triggered.</span></span> <span data-ttu-id="b3998-165">Jeder Setter ist auf eine Eigenschaft eines bestimmten XAML-Elements ausgerichtet und legt dieses auf einen angegebenen Wert fest.</span><span class="sxs-lookup"><span data-stu-id="b3998-165">Each setter targets one property of a particular XAML element and sets it to the given value.</span></span> <span data-ttu-id="b3998-166">Fügen Sie diesen Code dem mobilen **VisualState** hinzu, den Sie gerade erstellt haben, und zwar unter dem **VisualState.StateTriggers**‑Element.</span><span class="sxs-lookup"><span data-stu-id="b3998-166">Add this code to the mobile **VisualState** you just created, below the **VisualState.StateTriggers** element.</span></span> 

```XAML
<VisualStateManager.VisualStateGroups>
    <VisualStateGroup>

        <VisualState x:Key="Mobile">
            ...

            <!-- Add setters for mobile visualstate -->
            <VisualState.Setters>

                <!-- Move GridView about the command bar -->
                <Setter Target="ImageGridView.(RelativePanel.Above)"
                        Value="MainCommandBar" />

                <!-- Switch to mobile layout -->
                <Setter Target="ImageGridView.ItemTemplate"
                        Value="{StaticResource ImageGridView_MobileItemTemplate}" />

                <!-- Switch to mobile container styles -->
                <Setter Target="ImageGridView.ItemContainerStyle"
                        Value="{StaticResource ImageGridView_MobileItemContainerStyle}" />

                <!-- Move command bar to bottom of the screen -->
                <Setter Target="MainCommandBar.(RelativePanel.AlignBottomWithPanel)"
                        Value="True" />
                <Setter Target="MainCommandBar.(RelativePanel.AlignLeftWithPanel)"
                        Value="True" />
                <Setter Target="MainCommandBar.(RelativePanel.AlignRightWithPanel)"
                        Value="True" />

                <!-- Adjust the zoom slider to fit mobile screens -->
                <Setter Target="ZoomSlider.Minimum"
                        Value="80" />
                <Setter Target="ZoomSlider.Maximum"
                        Value="180" />
                <Setter Target="ZoomSlider.TickFrequency"
                        Value="20" />
                <Setter Target="ZoomSlider.Value"
                        Value="100" />
            </VisualState.Setters>

        </VisualState>
    </VisualStateGroup>
</VisualStateManager.VisualStateGroups>

```

<span data-ttu-id="b3998-167">Diese Setter legen das **ItemTemplate** der Bildergalerie auf das neue **DataTemplate** fest, dass wir im ersten Teil erstellt haben und richtet die Befehlsleiste und den Zoom-Schieberegler am unteren Rand des Bildschirms aus, damit sie auf einem Mobiltelefon einfacher mit dem Daumen erreichbar sind.</span><span class="sxs-lookup"><span data-stu-id="b3998-167">These setters set the **ItemTemplate** of the image gallery to the new **DataTemplate** that we created in the first part, and align the command bar and zoom slider with the bottom of the screen, so they are easier to reach with your thumb on a mobile phone screen.</span></span>

### <a name="run-the-app"></a><span data-ttu-id="b3998-168">Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="b3998-168">Run the app</span></span>
<span data-ttu-id="b3998-169">Versuchen Sie nun die App mit Mobile-Emulator auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b3998-169">Now try running the app using a mobile emulator.</span></span> <span data-ttu-id="b3998-170">Wird das neue Layout erfolgreich angezeigt?</span><span class="sxs-lookup"><span data-stu-id="b3998-170">Does the new layout display successfully?</span></span> <span data-ttu-id="b3998-171">Ein Raster mit Miniaturansichten sollte wie folgt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b3998-171">You should see a grid of small thumbnails as below.</span></span> <span data-ttu-id="b3998-172">Wenn das alte Layout weiterhin angezeigt wird, liegt möglicherweise ein Druckfehler in Ihrem **VisualStateManager**-Code vor.</span><span class="sxs-lookup"><span data-stu-id="b3998-172">If you still see the old layout, there may be a typo in your **VisualStateManager** code.</span></span>

![Mobiles Layout: danach](../basics/images/xaml-basics/adaptive-layout-mobile-after.png)

## <a name="part-3-adapt-to-multiple-window-sizes-on-a-single-device"></a><span data-ttu-id="b3998-174">Teil 3: Anpassen mehrerer Fenstergrößen auf einem einzigen Gerät</span><span class="sxs-lookup"><span data-stu-id="b3998-174">Part 3: Adapt to multiple window sizes on a single device</span></span>
<span data-ttu-id="b3998-175">Das Erstellen eines neuen maßgeschneiderten Layouts löst die Herausforderung eines reaktionsfähigen Designs für Mobilgeräte, aber was geschieht bei Desktops und Tablet-PCs?</span><span class="sxs-lookup"><span data-stu-id="b3998-175">Creating a new tailored layout solves the challenge of responsive design for mobile devices, but what about desktops and tablets?</span></span> <span data-ttu-id="b3998-176">Die App kann im Vollbildmodus ansprechend aussehen, aber wenn der Benutzer das Fenster verkleinert kann sie unter Umständen komisch wirken.</span><span class="sxs-lookup"><span data-stu-id="b3998-176">The app may look good at full screen, but if the user shrinks the window, they may end up with an awkward interface.</span></span> <span data-ttu-id="b3998-177">Wir garantieren, dass die Oberfläche für Endbenutzer immer gut aussieht, wenn Sie **VisualStateManager** auf mehrere Fenstergrößen auf einem einzigen Gerät anpassen.</span><span class="sxs-lookup"><span data-stu-id="b3998-177">We can ensure that the end-user experience always looks and feels right by using the **VisualStateManager** to adapt to multiple window sizes on a single device.</span></span>

![Kleines Fenster: vorher](../basics/images/xaml-basics/adaptive-layout-small-before.png)

### <a name="add-window-snap-points"></a><span data-ttu-id="b3998-179">Hinzufügen von Fenster-Andockpunkten</span><span class="sxs-lookup"><span data-stu-id="b3998-179">Add window snap points</span></span>
<span data-ttu-id="b3998-180">Definieren Sie zuerst "Andockpunkte", an denen verschiedene **VisualStates** ausgelöst werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b3998-180">The first step is to define the "snap points" at which different **VisualStates** will be triggered.</span></span> <span data-ttu-id="b3998-181">Öffnen Sie App.xaml im Projektmappen-Explorer und fügen Sie den **Anwendungs**-Tags folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3998-181">Open App.xaml from the Solution Explorer, and add the following code between the **Application** tags.</span></span>

```XAML
<Application.Resources>
    <!--  window width adaptive snap points  -->
    <x:Double x:Key="MinWindowSnapPoint">0</x:Double>
    <x:Double x:Key="MediumWindowSnapPoint">641</x:Double>
    <x:Double x:Key="LargeWindowSnapPoint">1008</x:Double>
</Application.Resources>
```

<span data-ttu-id="b3998-182">Dadurch erhalten wir drei Andockpunkte, die das Erstellen neuer **VisualStates** für drei Fenstergrößen ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="b3998-182">This gives us three snap points, which allow us to create new **VisualStates** for three ranges of window sizes:</span></span>
+ <span data-ttu-id="b3998-183">Klein (0 – 640 Pixel breit)</span><span class="sxs-lookup"><span data-stu-id="b3998-183">Small (0 - 640 pixels wide)</span></span>
+ <span data-ttu-id="b3998-184">Mittel (641 1007 Pixel breit)</span><span class="sxs-lookup"><span data-stu-id="b3998-184">Medium (641 - 1007 pixels wide)</span></span>
+ <span data-ttu-id="b3998-185">Groß (> 1007 Pixel breit)</span><span class="sxs-lookup"><span data-stu-id="b3998-185">Large (> 1007 pixels wide)</span></span>

### <a name="create-new-visualstates-and-statetriggers"></a><span data-ttu-id="b3998-186">Erstellen neuer VisualStates und StateTriggers</span><span class="sxs-lookup"><span data-stu-id="b3998-186">Create new VisualStates and StateTriggers</span></span>
<span data-ttu-id="b3998-187">Als Nächstes erstellen wir **VisualStates** und **StateTriggers**, die jedem Andockpunkt entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b3998-187">Next, we create the **VisualStates** and **StateTriggers** that correspond to each snap point.</span></span> <span data-ttu-id="b3998-188">Fügen Sie dem in Teil 2 erstellten **VisualStateManager** in „MainPage.xaml.cpp“ den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3998-188">In MainPage.xaml, add the following code to the **VisualStateManager** that you created in Part 2.</span></span>

```XAML
<VisualStateManager.VisualStateGroups>
    <VisualStateGroup>
    ...

        <!-- Large window VisualState -->
        <VisualState x:Key="LargeWindow">

            <!-- Large window trigger -->
            <VisualState.StateTriggers>
                <AdaptiveTrigger MinWindowWidth="{StaticResource LargeWindowSnapPoint}"/>
            </VisualState.StateTriggers>
     
        </VisualState>

        <!-- Medium window VisualState -->
        <VisualState x:Key="MediumWindow">

            <!-- Medium window trigger -->
            <VisualState.StateTriggers>
                <AdaptiveTrigger MinWindowWidth="{StaticResource MediumWindowSnapPoint}"/>
            </VisualState.StateTriggers>
        
        </VisualState>

        <!-- Small window VisualState -->
        <VisualState x:Key="SmallWindow">

            <!-- Small window trigger -->
            <VisualState.StateTriggers >
                <AdaptiveTrigger MinWindowWidth="{StaticResource MinWindowSnapPoint}"/>
            </VisualState.StateTriggers>

        </VisualState>

    </VisualStateGroup>
</VisualStateManager.VisualStateGroups>
```

### <a name="add-setters"></a><span data-ttu-id="b3998-189">Setter hinzufügen</span><span class="sxs-lookup"><span data-stu-id="b3998-189">Add setters</span></span>
<span data-ttu-id="b3998-190">Fügen Sie zum Schluß dem **SmallWindow**-Zustand folgende Setter hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3998-190">Finally, add these setters to the **SmallWindow** state.</span></span>

```XAML

<VisualState x:Key="SmallWindow">
    ...

    <!-- Small window setters -->
    <VisualState.Setters>

        <!-- Apply mobile itemtemplate and styles -->
        <Setter Target="ImageGridView.ItemTemplate"
                Value="{StaticResource ImageGridView_MobileItemTemplate}" />
        <Setter Target="ImageGridView.ItemContainerStyle"
                Value="{StaticResource ImageGridView_MobileItemContainerStyle}" />

        <!-- Adjust the zoom slider to fit small windows-->
        <Setter Target="ZoomSlider.Minimum"
                Value="80" />
        <Setter Target="ZoomSlider.Maximum"
                Value="180" />
        <Setter Target="ZoomSlider.TickFrequency"
                Value="20" />
        <Setter Target="ZoomSlider.Value"
                Value="100" />
    </VisualState.Setters>

</VisualState>

```

<span data-ttu-id="b3998-191">Diese Setter wenden das mobile **DataTemplate** und Stile auf die Desktop-App an, wenn der Viewport kleiner als 641 Pixel breit ist.</span><span class="sxs-lookup"><span data-stu-id="b3998-191">These setters apply the mobile **DataTemplate** and styles to the desktop app, whenever the viewport is less than 641 pixels wide.</span></span> <span data-ttu-id="b3998-192">Sie passen auch den Zoomschieberegler dem kleinen Bildschirm besser an.</span><span class="sxs-lookup"><span data-stu-id="b3998-192">They also tweak the zoom slider to better fit the small screen.</span></span>

### <a name="run-the-app"></a><span data-ttu-id="b3998-193">Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="b3998-193">Run the app</span></span>

<span data-ttu-id="b3998-194">In der Visual Studio-Symbolleiste, legen Sie das Zielgerät auf **Lokaler Computer** fest und führen Sie die App aus.</span><span class="sxs-lookup"><span data-stu-id="b3998-194">In the Visual Studio toolbar set the target device to **Local Machine**, and run the app.</span></span> <span data-ttu-id="b3998-195">Wenn die App geladen wird, versuchen Sie die Größe des Fensters zu ändern.</span><span class="sxs-lookup"><span data-stu-id="b3998-195">When the app loads, try changing the size of the window.</span></span> <span data-ttu-id="b3998-196">Wenn Sie das Fenster auf eine kleinere Größe anpassen möchten, sollten Sie die App auf das mobile Layout wechseln, das Sie in Teil 2 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="b3998-196">When you shrink the window to a small size, you should see the app switch to the mobile layout you created in Part 2.</span></span>

![Kleines Fenster: nachher](../basics/images/xaml-basics/adaptive-layout-small-after.png)

## <a name="going-further"></a><span data-ttu-id="b3998-198">Vertiefung</span><span class="sxs-lookup"><span data-stu-id="b3998-198">Going further</span></span>

<span data-ttu-id="b3998-199">Nach Abschluss dieser Übung verfügen Sie über ausreichende adaptive Layout-Kenntnisse, um selbst weiter zu experimentieren.</span><span class="sxs-lookup"><span data-stu-id="b3998-199">Now that you've completed this lab, you have enough adaptive layout knowledge to experiment further on your own.</span></span> <span data-ttu-id="b3998-200">Versuchen Sie es ein Bewertungs-Steuerelement für die mobilen QuickInfos hinzuzufügen, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="b3998-200">Try adding a rating control to the mobile-only tooltip you added earlier.</span></span> <span data-ttu-id="b3998-201">Oder wenn Sie eine größere Herausforderung möchten, optimieren Sie das Layout für größere Bildschirme (wie TV-Bildschirme oder ein Surface Studio)</span><span class="sxs-lookup"><span data-stu-id="b3998-201">Or, for a bigger challenge, try optimizing the layout for larger screen sizes (think TV screens or a Surface Studio)</span></span>

<span data-ttu-id="b3998-202">Wenn Sie Probleme haben, finden Sie weitere Unterstützung in den folgenden Abschnitten von [Definieren von Seitenlayouts mit XAML](../layout/layouts-with-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b3998-202">If you get stuck, you can find more guidance in these sections of [Define page layouts with XAML](../layout/layouts-with-xaml.md).</span></span>

+ [<span data-ttu-id="b3998-203">Visuelle Zustände und Zustandsauslöser</span><span class="sxs-lookup"><span data-stu-id="b3998-203">Visual states and state triggers</span></span>](https://docs.microsoft.com/en-us/windows/uwp/layout/layouts-with-xaml#visual-states-and-state-triggers)
+ [<span data-ttu-id="b3998-204">Maßgeschneiderte Layouts</span><span class="sxs-lookup"><span data-stu-id="b3998-204">Tailored layouts</span></span>](https://docs.microsoft.com/en-us/windows/uwp/layout/layouts-with-xaml#tailored-layouts)

<span data-ttu-id="b3998-205">Auch wenn Sie weitere Informationen erhalten möchten, wie die erste Fotobearbeitungs-App erstellt wurde, sehen Sie sich dieses Lernprogramme auf XAML an: [Benutzeroberflächen](../basics/xaml-basics-ui.md) und [Datenbindung](../../data-binding/xaml-basics-data-binding.md).</span><span class="sxs-lookup"><span data-stu-id="b3998-205">Alternatively, if you want to learn more about how the initial photo editing app was built, check out these tutorials on XAML [user interfaces](../basics/xaml-basics-ui.md) and [data binding](../../data-binding/xaml-basics-data-binding.md).</span></span>

## <a name="get-the-final-version-of-the-photolab-sample"></a><span data-ttu-id="b3998-206">Abrufen der finalen Version des PhotoLab-Beispiels</span><span class="sxs-lookup"><span data-stu-id="b3998-206">Get the final version of the PhotoLab sample</span></span>

<span data-ttu-id="b3998-207">In diesem Lernprogramm lernen Sie nicht das Erstellen der vollständigen App. Lesen Sie daher die [endgültige Version](https://github.com/Microsoft/Windows-appsample-photo-lab) zu Features durch wie z.B. benutzerdefinierte Animationen und Support für Ihre Telefon.</span><span class="sxs-lookup"><span data-stu-id="b3998-207">This tutorial doesn't build up to the complete photo editing app, so be sure to check out the [final version](https://github.com/Microsoft/Windows-appsample-photo-lab) to see other features such as custom animations and phone support.</span></span>