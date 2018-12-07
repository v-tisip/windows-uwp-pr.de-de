---
Description: This tutorial walks through how to create a basic application user interface. It explains and demonstrates the use of Grid and StackPanel, two of the most common XAML elements.
title: Verwenden Sie Grid und StackPanel, um eine einfache Wetter-App zu erstellen.
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
ms.assetid: 9794a04d-e67f-472c-8ba8-8ebe442f6ef2
ms.localizationpriority: medium
ms.openlocfilehash: 5b221220d417df5b70927984ac65eff93fae54a4
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8779447"
---
# <a name="tutorial-use-grid-and-stackpanel-to-create-a-simple-weather-app"></a><span data-ttu-id="6d93a-103">Tutorial: Verwenden Sie Grid und StackPanel, um eine einfache Wetter-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6d93a-103">Tutorial: Use Grid and StackPanel to create a simple weather app</span></span>

<span data-ttu-id="6d93a-104">Verwenden Sie zum Erstellen des Layouts für eine einfache Wetter-App mit XAML die Elemente **Grid** und **StackPanel**.</span><span class="sxs-lookup"><span data-stu-id="6d93a-104">Use XAML to create the layout for a simple weather app using the **Grid** and **StackPanel** elements.</span></span> <span data-ttu-id="6d93a-105">Mit diesen Tools können Sie hervorragend aussehende Apps erstellen, die auf jedem Gerät mit Windows10 funktionieren.</span><span class="sxs-lookup"><span data-stu-id="6d93a-105">With these tools you can make great looking apps that work on any device running Windows 10.</span></span> <span data-ttu-id="6d93a-106">Dieses Lernprogramm dauert 10 bis 20Minuten.</span><span class="sxs-lookup"><span data-stu-id="6d93a-106">This tutorial takes 10-20 minutes.</span></span>

> <span data-ttu-id="6d93a-107">**Wichtige APIs**: [Grid-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.grid), [StackPanel-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.stackpanel)</span><span class="sxs-lookup"><span data-stu-id="6d93a-107">**Important APIs**: [Grid class](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.grid), [StackPanel class](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.stackpanel)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d93a-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="6d93a-108">Prerequisites</span></span>
- <span data-ttu-id="6d93a-109">Windows 10 und Microsoft Visual Studio 2015 oder höher.</span><span class="sxs-lookup"><span data-stu-id="6d93a-109">Windows 10 and Microsoft Visual Studio 2015 or later.</span></span> <span data-ttu-id="6d93a-110">(Neueste Visual Studio empfohlen für die aktuelle Entwicklung und Security Updates) [Klicken Sie hier, um zu erfahren, wie Sie mit Visual Studio einrichten](../../get-started/get-set-up.md).</span><span class="sxs-lookup"><span data-stu-id="6d93a-110">(Newest Visual Studio recommended for current development and security updates) [Click here to learn how to get set up with Visual Studio](../../get-started/get-set-up.md).</span></span>
- <span data-ttu-id="6d93a-111">Kenntnisse im Erstellen einer einfachen „Hello, World“-App mit XAML und C#.</span><span class="sxs-lookup"><span data-stu-id="6d93a-111">Knowledge of how to create a basic "Hello World" app by using XAML and C#.</span></span> <span data-ttu-id="6d93a-112">Wenn Sie diese noch nicht besitzen [klicken Sie hier, um zu erfahren, wie Sie eine „Hello World“-App erstellen](https://msdn.microsoft.com/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span><span class="sxs-lookup"><span data-stu-id="6d93a-112">If you don't have that yet, [click here to learn how to create a "Hello World" app](https://msdn.microsoft.com/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span>

## <a name="step-1-create-a-blank-app"></a><span data-ttu-id="6d93a-113">Schritt1: Erstellen Sie eine leere App.</span><span class="sxs-lookup"><span data-stu-id="6d93a-113">Step 1: Create a blank app</span></span>
1. <span data-ttu-id="6d93a-114">Wählen Sie in Visual Studio **Datei** > **Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="6d93a-114">In Visual Studio menu, select **File** > **New Project**.</span></span>
2. <span data-ttu-id="6d93a-115">Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** **Visual C#** > **Windows** > **Universell** oder **Visual C++** > **Windows** > **Universell** aus.</span><span class="sxs-lookup"><span data-stu-id="6d93a-115">In the left pane of the **New Project** dialog box, select **Visual C#** > **Windows** > **Universal** or **Visual C++** > **Windows** > **Universal**.</span></span>
3. <span data-ttu-id="6d93a-116">Wählen Sie im mittleren Bereich **Blank App** aus.</span><span class="sxs-lookup"><span data-stu-id="6d93a-116">In the center pane, select **Blank App**.</span></span>
4. <span data-ttu-id="6d93a-117">Geben Sie im Feld **Name** **WeatherPanel** ein, und wählen Sie **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="6d93a-117">In the **Name** box, enter **WeatherPanel**, and select **OK**.</span></span>
5. <span data-ttu-id="6d93a-118">Wählen Sie zum Ausführen des Programms im Menü **Debugging** > **Debugging starten** aus, oder drücken Sie F5.</span><span class="sxs-lookup"><span data-stu-id="6d93a-118">To run the program, select **Debug** > **Start Debugging** from the menu, or select F5.</span></span>

## <a name="step-2-define-a-grid"></a><span data-ttu-id="6d93a-119">Schritt2: Definieren eines Rasters</span><span class="sxs-lookup"><span data-stu-id="6d93a-119">Step 2: Define a Grid</span></span>
<span data-ttu-id="6d93a-120">In XAML besteht ein **Raster** aus einer Reihe von Zeilen und Spalten.</span><span class="sxs-lookup"><span data-stu-id="6d93a-120">In XAML a **Grid** is made up of a series of rows and columns.</span></span> <span data-ttu-id="6d93a-121">Durch Angabe der Zeile und Spalte eines Elements innerhalb eines **Rasters** können Sie andere Elemente in einer Benutzeroberfläche platzieren und anordnen.</span><span class="sxs-lookup"><span data-stu-id="6d93a-121">By specifying the row and column of an element within a **Grid**, you can place and space other elements within a user interface.</span></span> <span data-ttu-id="6d93a-122">Zeilen und Spalten werden mit den Elementen **RowDefinition** und **ColumnDefinition** definiert.</span><span class="sxs-lookup"><span data-stu-id="6d93a-122">Rows and columns are defined with the **RowDefinition** and **ColumnDefinition** elements.</span></span>

<span data-ttu-id="6d93a-123">Um mit dem Erstellen eines Layouts zu beginnen, öffnen Sie **MainPage.xaml** mithilfe des **Projektmappen-Explorers** und ersetzen das automatisch generierte **Grid**-Element durch diesen Code.</span><span class="sxs-lookup"><span data-stu-id="6d93a-123">To start creating a layout, open **MainPage.xaml** by using the **Solution Explorer**, and replace the automatically generated **Grid** element with this code.</span></span>

```xml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="3*"/>
        <ColumnDefinition Width="5*"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="2*"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
</Grid>
```

<span data-ttu-id="6d93a-124">Das neue **Raster** erstellt eine Reihe von zwei Zeilen und Spalten, die das Layout der App-Oberfläche definieren.</span><span class="sxs-lookup"><span data-stu-id="6d93a-124">The new **Grid** creates a set of two rows and columns, which defines the layout of the app interface.</span></span> <span data-ttu-id="6d93a-125">Die erste Spalte hat eine **Breite** von "3\*", während die zweite Spalte eine Breite von "5\*" hat. Der horizontale Abstand zwischen den beiden Spalten wird hierdurch im Verhältnis 3:5 geteilt.</span><span class="sxs-lookup"><span data-stu-id="6d93a-125">The first column has a **Width** of "3\*", while the second has "5\*", dividing the horizontal space between the two columns at a ratio of 3:5.</span></span> <span data-ttu-id="6d93a-126">Auf die gleiche Weise haben die beiden Zeilen eine **Höhe** von "2\*" bzw. "\*", damit **Grid** der ersten Zeile zwei Mal so viel Platz zuteilt wie der zweiten Zeile ("\*" bedeutet "1\*").</span><span class="sxs-lookup"><span data-stu-id="6d93a-126">In the same way, the two rows have a **Height** of "2\*" and "\*" respectively, so the **Grid** allocates two times as much space for the first row as for the second ("\*" is the same as "1\*").</span></span> <span data-ttu-id="6d93a-127">Diese Seitenverhältnisse werden bewahrt, auch wenn die Fenstergröße oder das Gerät geändert werden.</span><span class="sxs-lookup"><span data-stu-id="6d93a-127">These ratios are maintained even if the window is resized or the device is changed.</span></span>

<span data-ttu-id="6d93a-128">Informationen zu weiteren Methoden für die Größeneinstellung von Zeilen und Spalten finden Sie unter [Definieren von Layouts mit XAML](https://msdn.microsoft.com/windows/uwp/layout/layouts-with-xaml#layout-properties).</span><span class="sxs-lookup"><span data-stu-id="6d93a-128">To learn about other methods of sizing rows and columns, see [Define layouts with XAML](https://msdn.microsoft.com/windows/uwp/layout/layouts-with-xaml#layout-properties).</span></span>

<span data-ttu-id="6d93a-129">Wenn Sie die Anwendung jetzt ausführen, wird Ihnen lediglich eine leere Seite angezeigt, da keiner der **Raster**-Bereiche Inhalte enthält.</span><span class="sxs-lookup"><span data-stu-id="6d93a-129">If you run the application now you won't see anything except a blank page, because none of the **Grid** areas have any content.</span></span> <span data-ttu-id="6d93a-130">Um das **Raster** anzuzeigen, fügen wir Farbe hinzu.</span><span class="sxs-lookup"><span data-stu-id="6d93a-130">To show the **Grid** let's give it some color.</span></span>

## <a name="step-3-color-the-grid"></a><span data-ttu-id="6d93a-131">Schritt3: Färben des Rasters</span><span class="sxs-lookup"><span data-stu-id="6d93a-131">Step 3: Color the Grid</span></span>
<span data-ttu-id="6d93a-132">Um dem **Raster** Farbe hinzuzufügen, fügen wir drei **Border**-Elemente mit jeweils einer anderen Hintergrundfarbe hinzu.</span><span class="sxs-lookup"><span data-stu-id="6d93a-132">To color the **Grid** we add three **Border** elements, each with a different background color.</span></span> <span data-ttu-id="6d93a-133">Jedes Element wird darüber hinaus einer Zeile und Spalte im übergeordneten **Grid** zugewiesen. Dies erfolgt mithilfe der Attribute **Grid.Row** und **Grid.Column**.</span><span class="sxs-lookup"><span data-stu-id="6d93a-133">Each is also assigned to a row and column in the parent **Grid** by using the **Grid.Row** and **Grid.Column** attributes.</span></span> <span data-ttu-id="6d93a-134">Die Werte dieser Attribute sind standardmäßig 0. Daher müssen Sie diese dem ersten **Border** nicht zuweisen.</span><span class="sxs-lookup"><span data-stu-id="6d93a-134">The values of these attributes default to 0, so you don't need to assign them to the first **Border**.</span></span> <span data-ttu-id="6d93a-135">Fügen Sie dem **Grid**-Element nach den Zeilen- und Spaltendefinitionen den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="6d93a-135">Add the following code to the **Grid** element after the row and column definitions.</span></span>

```xml
<Border Background="#2f5cb6"/>
<Border Grid.Column ="1" Background="#1f3d7a"/>
<Border Grid.Row="1" Grid.ColumnSpan="2" Background="#152951"/>
```

<span data-ttu-id="6d93a-136">Beachten Sie, dass für das dritte **Border**-Element ein zusätzliches Attribut verwendet wird, **Grid.ColumnSpan**. Dieses bewirkt, dass dieses **Border**-Element beide Spalten in der unteren Zeile umfasst.</span><span class="sxs-lookup"><span data-stu-id="6d93a-136">Notice that for the third **Border** we use an extra attribute, **Grid.ColumnSpan**, which causes this **Border** to span both columns in the lower row.</span></span> <span data-ttu-id="6d93a-137">Sie können **Grid.RowSpan** auf die gleiche Weise verwenden. Mit diesen Attributen können Sie ein Element über eine beliebige Anzahl von Zeilen und Spalten ausdehnen.</span><span class="sxs-lookup"><span data-stu-id="6d93a-137">You can use **Grid.RowSpan** in the same way, and together these attributes let you span an element over any number of rows and columns.</span></span> <span data-ttu-id="6d93a-138">Die obere linke Ecke einer solchen Ausdehnung entspricht stets der **Grid.Column** und **Grid.Row**, die in den Elementattributen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6d93a-138">The upper-left corner of such a span is always the **Grid.Column** and **Grid.Row** specified in the element attributes.</span></span>

<span data-ttu-id="6d93a-139">Wenn Sie die App ausführen, sieht das Ergebnis wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="6d93a-139">If you run the app, the result looks something like this.</span></span>

![Färben des Rasters](images/grid-weather-1.png)

## <a name="step-4-organize-content-by-using-stackpanel-elements"></a><span data-ttu-id="6d93a-141">Schritt4: Organisieren von Inhalten mithilfe von StackPanel-Elementen</span><span class="sxs-lookup"><span data-stu-id="6d93a-141">Step 4: Organize content by using StackPanel elements</span></span>
<span data-ttu-id="6d93a-142">**StackPanel** ist das zweite UI-Element, das wir verwenden, um die Wetter-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6d93a-142">**StackPanel** is the second UI element we'll use to create our weather app.</span></span> <span data-ttu-id="6d93a-143">**StackPanel** ist ein grundlegender Bestandteil zahlreicher Basislayouts von Apps, mit dem Sie Elemente vertikal oder horizontal stapeln können.</span><span class="sxs-lookup"><span data-stu-id="6d93a-143">The **StackPanel** is a fundamental part of many basic app layouts, allowing you to stack elements vertically or horizontally.</span></span>

<span data-ttu-id="6d93a-144">Im folgenden Code erstellen wir zwei **StackPanel**-Elemente und füllen jedes mit drei **TextBlocks**.</span><span class="sxs-lookup"><span data-stu-id="6d93a-144">In the following code, we create two **StackPanel** elements and fill each with three **TextBlocks**.</span></span> <span data-ttu-id="6d93a-145">Fügen Sie diese **StackPanel**-Elemente dem **Grid** unterhalb der **Border**-Elemente aus Schritt3 hinzu.</span><span class="sxs-lookup"><span data-stu-id="6d93a-145">Add these **StackPanel** elements to the **Grid** below the **Border** elements from Step 3.</span></span> <span data-ttu-id="6d93a-146">Dies bewirkt, dass die **TextBlock**-Elemente auf dem zuvor erstellten farbigen **Grid** gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="6d93a-146">This causes the **TextBlock** elements to render on top of the colored **Grid** we created earlier.</span></span>

```xml
<StackPanel Grid.Column="1" Margin="40,0,0,0" VerticalAlignment="Center">
    <TextBlock Foreground="White" FontSize="25" Text="Today - 64° F"/>
    <TextBlock Foreground="White" FontSize="25" Text="Partially Cloudy"/>
    <TextBlock Foreground="White" FontSize="25" Text="Precipitation: 25%"/>
</StackPanel>
<StackPanel Grid.Row="1" Grid.ColumnSpan="2" Orientation="Horizontal"
            HorizontalAlignment="Center" VerticalAlignment="Center">
    <TextBlock Foreground="White" FontSize="25" Text="High: 66°" Margin="0,0,20,0"/>
    <TextBlock Foreground="White" FontSize="25" Text="Low: 43°" Margin="0,0,20,0"/>
    <TextBlock Foreground="White" FontSize="25" Text="Feels like: 63°"/>
</StackPanel>
```

<span data-ttu-id="6d93a-147">Im ersten **Stackpanel** wird jeder **TextBlock** vertikal unterhalb des nächsten gestapelt.</span><span class="sxs-lookup"><span data-stu-id="6d93a-147">In the first **Stackpanel**, each **TextBlock** stacks vertically below the next.</span></span> <span data-ttu-id="6d93a-148">Dies ist das Standardverhalten eines StackPanel. Daher müssen wir das **Orientation**-Attribut nicht festlegen.</span><span class="sxs-lookup"><span data-stu-id="6d93a-148">This is the default behavior of a StackPanel, so we don't need to set the **Orientation** attribute.</span></span> <span data-ttu-id="6d93a-149">Im zweiten StackPanel-Element möchten wir die untergeordneten Elemente horizontal von links nach rechts stapeln. Daher legen wir das **Orientation**-Attribut auf „Horizontal“ fest.</span><span class="sxs-lookup"><span data-stu-id="6d93a-149">In the second StackPanel, we want the child elements to stack horizontally from left to right, so we set the **Orientation** attribute to "Horizontal".</span></span> <span data-ttu-id="6d93a-150">Außerdem müssen wir das **Grid.ColumnSpan**-Attribut auf „2“ festlegen, damit der Text über dem unteren **Border**-Element zentriert wird.</span><span class="sxs-lookup"><span data-stu-id="6d93a-150">We must also set the **Grid.ColumnSpan** attribute to "2", so that the text is centered over the lower **Border**.</span></span>

<span data-ttu-id="6d93a-151">Wenn Sie die App jetzt ausführen, wird sie Ihnen ungefähr wie folgt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6d93a-151">If you run the app now, you'll see something like this.</span></span>

![Hinzufügen von StackPanels](images/grid-weather-2.png)

## <a name="step-5-add-an-image-icon"></a><span data-ttu-id="6d93a-153">Schritt5: Hinzufügen eines Bildsymbols</span><span class="sxs-lookup"><span data-stu-id="6d93a-153">Step 5: Add an image icon</span></span>

<span data-ttu-id="6d93a-154">Zum Schluss füllen Sie den leeren Abschnitt im **Grid** mit einem Bild, das das Wetter von heute zeigt – ein Bild, das einen teilweise bewölkten Himmel anzeigt.</span><span class="sxs-lookup"><span data-stu-id="6d93a-154">Finally, let's fill the empty section in our **Grid** with an image that represents today's weather—something that says "partially cloudy."</span></span>

<span data-ttu-id="6d93a-155">Laden Sie das Bild unten herunter, und speichern Sie es als PNG-Datei mit dem Namen „Teilweise-bewölkt“.</span><span class="sxs-lookup"><span data-stu-id="6d93a-155">Download the image below and save it as a PNG named "partially-cloudy".</span></span>

![Teilweise bewölkt](images/partially-cloudy.PNG)

<span data-ttu-id="6d93a-157">Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Ordner **Ressourcen**, und wählen Sie **Hinzufügen** -> **Vorhandenes Element...** aus. Suchen Sie im nun angezeigten Browser die Datei „Teilweise-bewölkt“, wählen Sie die Datei aus, und klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6d93a-157">In the **Solution Explorer**, right click the **Assets** folder, and select **Add** -> **Existing Item...** Find partially-cloudy.png in the browser that pops up, select it, and click **Add**.</span></span>

<span data-ttu-id="6d93a-158">Fügen Sie als Nächstes in **"MainPage.xaml"** das folgende **Image**-Element unterhalb der StackPanels aus Schritt4 hinzu.</span><span class="sxs-lookup"><span data-stu-id="6d93a-158">Next, in **MainPage.xaml**, add the following **Image** element below the StackPanels from Step 4.</span></span>

```xml
<Image Margin="20" Source="Assets/partially-cloudy.png"/>
```

<span data-ttu-id="6d93a-159">Da das Bild in der ersten Zeile und Spalte angezeigt werden soll, müssen wir dessen **Grid.Row**- oder **Grid.Column**-Attribute nicht festlegen. Diese sind standardmäßig auf „0“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="6d93a-159">Because we want the Image in the first row and column, we don't need to set its **Grid.Row** or **Grid.Column** attributes, allowing them to default to "0".</span></span>

<span data-ttu-id="6d93a-160">Das war’s!</span><span class="sxs-lookup"><span data-stu-id="6d93a-160">And that's it!</span></span> <span data-ttu-id="6d93a-161">Sie haben das Layout für eine einfache Wetter-App erstellt.</span><span class="sxs-lookup"><span data-stu-id="6d93a-161">You've successfully created the layout for a simple weather application.</span></span> <span data-ttu-id="6d93a-162">Wenn Sie die Anwendung durch Drücken von **F5** ausführen, sollte Ihnen ungefähr Folgendes angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="6d93a-162">If you run the application by pressing **F5**, you should see something like this:</span></span>

![Beispiel für Wetterbereich](images/grid-weather-3.PNG)

<span data-ttu-id="6d93a-164">Wenn Sie möchten, können Sie mit dem Layout oben experimentieren und verschiedene Möglichkeiten erkunden, wie Sie Wetterdaten darstellen können.</span><span class="sxs-lookup"><span data-stu-id="6d93a-164">If you like, try experimenting with the layout above, and explore different ways you might represent weather data.</span></span>

## <a name="related-articles"></a><span data-ttu-id="6d93a-165">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="6d93a-165">Related articles</span></span>
<span data-ttu-id="6d93a-166">Eine Einführung in das Entwerfen von UWP-App-Layouts finden Sie unter [Einführung in das UWP-App-Design](https://msdn.microsoft.com/windows/uwp/layout/design-and-ui-intro).</span><span class="sxs-lookup"><span data-stu-id="6d93a-166">For an introduction to designing UWP app layouts, see [Introduction to UWP app design](https://msdn.microsoft.com/windows/uwp/layout/design-and-ui-intro)</span></span>

<span data-ttu-id="6d93a-167">Informationen zum Erstellen von dynamischen Layouts, die an verschiedene Bildschirmgrößen angepasst werden können, finden Sie unter [Definieren von Seitenlayouts mit XAML](https://msdn.microsoft.com/windows/uwp/layout/layouts-with-xaml).</span><span class="sxs-lookup"><span data-stu-id="6d93a-167">To learn about creating responsive layouts that adapt to different screen sizes, see [Define Page Layouts with XAML](https://msdn.microsoft.com/windows/uwp/layout/layouts-with-xaml)</span></span>
