---
author: Karl-Bridge-Microsoft
Description: Use handwriting recognition and ink analysis to recognize Windows Ink strokes as text and shapes.
title: Erkennen von Windows Ink-Strichen als Text und Formen
ms.assetid: C2F3F3CE-737F-4652-98B7-5278A462F9D3
label: Recognize Windows Ink strokes as text
template: detail.hbs
keywords: Windows Ink, Windows-Freihandeingabe, DirectInk, InkPresenter, InkCanvas, Handschrifterkennung, Benutzerinteraktion, Eingabe
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 83142b0a3b24e25f8e7a922d800262f505cd8cc2
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5689623"
---
# <a name="recognize-windows-ink-strokes-as-text-and-shapes"></a><span data-ttu-id="4bf9b-103">Erkennen von Windows Ink-Strichen als Text und Formen</span><span class="sxs-lookup"><span data-stu-id="4bf9b-103">Recognize Windows Ink strokes as text and shapes</span></span>

<span data-ttu-id="4bf9b-104">Konvertieren Sie mithilfe der integrierten Erkennungsfunktionen in Windows Ink Freihandstriche in Text und Form.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-104">Convert ink strokes to text and shapes using the recognition capabilities built into Windows Ink.</span></span>

> <span data-ttu-id="4bf9b-105">**Wichtige APIs**: [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535), [**Windows.UI.Input.Inking**](https://msdn.microsoft.com/library/windows/apps/br208524)</span><span class="sxs-lookup"><span data-stu-id="4bf9b-105">**Important APIs**: [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535), [**Windows.UI.Input.Inking**](https://msdn.microsoft.com/library/windows/apps/br208524)</span></span>


## <a name="free-form-recognition-with-ink-analysis"></a><span data-ttu-id="4bf9b-106">Freiformerkennung mit der Freihandeingabenanalyse</span><span class="sxs-lookup"><span data-stu-id="4bf9b-106">Free-form recognition with ink analysis</span></span>

<span data-ttu-id="4bf9b-107">Hier wird veranschaulicht, wie Sie das Windows Ink-Analysemodul ([Windows.UI.Input.Inking.Analysis](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.analysis)) zur Klassifizierung, Analyse und Erkennung von Freiformstrichen in einer [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Klasse als Text oder Formen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-107">Here, we demonstrate how to use the Windows Ink analysis engine ([Windows.UI.Input.Inking.Analysis](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.analysis)) to classify, analyze, and recognize a set of free-form strokes on an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) as either text or shapes.</span></span> <span data-ttu-id="4bf9b-108">(Zusätzlich zur Text- und Formenerkennung können Sie mithilfe der Freihandeingabenanalyse die Dokumentstruktur, Aufzählungen und generische Zeichnungen erkennen.)</span><span class="sxs-lookup"><span data-stu-id="4bf9b-108">(In addition to text and shape recognition, ink analysis can also be used to recognize document structure, bullet lists, and generic drawings.)</span></span>

> [!NOTE]
> <span data-ttu-id="4bf9b-109">Informationen zu einfachen, einzeilige, Nur-Text-Szenarien wie der Formulareingabe finden Sie später unter [Eingeschränkte Schrifterkennung](#constrained-handwriting-recognition).</span><span class="sxs-lookup"><span data-stu-id="4bf9b-109">For basic, single-line, plain text scenarios such as form input, see [Constrained handwriting recognition](#constrained-handwriting-recognition) later in this topic.</span></span>

<span data-ttu-id="4bf9b-110">In diesem Beispiel wird die Erkennung durch den Benutzer initiiert, wenn er nach Abschluss des Zeichnens auf eine Schaltfläche klickt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-110">In this example, recognition is initiated when the user clicks a button to indicate they are finished drawing.</span></span>

**<span data-ttu-id="4bf9b-111">Laden Sie dieses Beispiel aus [Beispiel für die Freihandeingabeanalyse (einfach)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-analysis-basic.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-111">Download this sample from [Ink analysis sample (basic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-analysis-basic.zip)</span></span>**

1.  <span data-ttu-id="4bf9b-112">Zunächst richten wir die Benutzeroberfläche ein (MainPage.xaml).</span><span class="sxs-lookup"><span data-stu-id="4bf9b-112">First, we set up the UI (MainPage.xaml).</span></span> 

    <span data-ttu-id="4bf9b-113">Die Benutzeroberfläche bietet die Schaltfläche „Erkennen“, eine [**InkCanvas**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.InkCanvas)- und eine [**Canvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.canvas)-Standardkomponente.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-113">The UI includes a "Recognize" button, an [**InkCanvas**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.InkCanvas), and a standard [**Canvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.canvas).</span></span> <span data-ttu-id="4bf9b-114">Bei Betätigen der Schaltfläche „Erkennen“ werden alle Freihandstriche im Freihandeingabe-Zeichenbereich analysiert. Wenn Formen und Texte erkannt werden, werden sie im Standardzeichenbereich gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-114">When the "Recognize" button is pressed, all ink strokes on the ink canvas are analyzed and (if recognized) corresponding shapes and text are drawn on the standard canvas.</span></span> <span data-ttu-id="4bf9b-115">Die ursprünglichen Freihandstriche werden anschließend aus dem Freihandeingabe-Zeichenbereich gelöscht.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-115">The original ink strokes are then deleted from the ink canvas.</span></span>
```xaml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="HeaderPanel" 
                    Orientation="Horizontal" 
                    Grid.Row="0">
            <TextBlock x:Name="Header" 
                        Text="Basic ink analysis sample" 
                        Style="{ThemeResource HeaderTextBlockStyle}" 
                        Margin="10,0,0,0" />
            <Button x:Name="recognize" 
                    Content="Recognize" 
                    Margin="50,0,10,0"/>
        </StackPanel>
        <Grid x:Name="drawingCanvas" Grid.Row="1">

            <!-- The canvas where we render the replacement text and shapes. -->
            <Canvas x:Name="recognitionCanvas" />
            <!-- The canvas for ink input. -->
            <InkCanvas x:Name="inkCanvas" />

        </Grid>
    </Grid>
```
2. <span data-ttu-id="4bf9b-116">Fügen Sie in der CodeBehind-Datei der Benutzeroberfläche (MainPage.xaml.cs) die für die Freihandfunktion und die Freihandeingabenanalyse benötigten Namespaceverweistypen hinzu:</span><span class="sxs-lookup"><span data-stu-id="4bf9b-116">In the UI code-behind file (MainPage.xaml.cs), add the namespace type references required for our ink and ink analysis functionality:</span></span>
    - [<span data-ttu-id="4bf9b-117">Windows.UI.Input.Inking</span><span class="sxs-lookup"><span data-stu-id="4bf9b-117">Windows.UI.Input.Inking</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.inking)
    - [<span data-ttu-id="4bf9b-118">Windows.UI.Input.Inking.Analysis</span><span class="sxs-lookup"><span data-stu-id="4bf9b-118">Windows.UI.Input.Inking.Analysis</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.analysis)
    - [<span data-ttu-id="4bf9b-119">Windows.UI.Xaml.Shapes</span><span class="sxs-lookup"><span data-stu-id="4bf9b-119">Windows.UI.Xaml.Shapes</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.shapes)

3. <span data-ttu-id="4bf9b-120">Anschließend geben wir die globalen Variablen an:</span><span class="sxs-lookup"><span data-stu-id="4bf9b-120">We then specify our global variables:</span></span>
```csharp
    InkAnalyzer inkAnalyzer = new InkAnalyzer();
    IReadOnlyList<InkStroke> inkStrokes = null;
    InkAnalysisResult inkAnalysisResults = null;
```
4.  <span data-ttu-id="4bf9b-121">Dann werden einige grundlegende Verhaltensweisen für Freihandeingaben festgelegt:</span><span class="sxs-lookup"><span data-stu-id="4bf9b-121">Next, we set some basic ink input behaviors:</span></span>
    - <span data-ttu-id="4bf9b-122">Die [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Eigenschaft wird für die Interpretation von Eingabedaten von Stift, Maus und Toucheingabe als Freihandstriche ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)) konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-122">The [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) is configured to interpret input data from pen, mouse, and touch as ink strokes ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)).</span></span> 
    - <span data-ttu-id="4bf9b-123">Freihandstriche werden in der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Klasse mit der angegebenen [**InkDrawingAttributes**](https://msdn.microsoft.com/library/windows/desktop/ms695050)-Klasse gerendert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-123">Ink strokes are rendered on the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) using the specified [**InkDrawingAttributes**](https://msdn.microsoft.com/library/windows/desktop/ms695050).</span></span> 
    - <span data-ttu-id="4bf9b-124">Außerdem wird ein Listener für das Click-Ereignis der Schaltfläche „Erkennen“ deklariert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-124">A listener for the click event on the "Recognize" button is also declared.</span></span>
```csharp
/// <summary>
/// Initialize the UI page.
/// </summary>
public MainPage()
    {
        this.InitializeComponent();

        // Set supported inking device types.
        inkCanvas.InkPresenter.InputDeviceTypes =
            Windows.UI.Core.CoreInputDeviceTypes.Mouse |
            Windows.UI.Core.CoreInputDeviceTypes.Pen | 
            Windows.UI.Core.CoreInputDeviceTypes.Touch;

        // Set initial ink stroke attributes.
        InkDrawingAttributes drawingAttributes = new InkDrawingAttributes();
        drawingAttributes.Color = Windows.UI.Colors.Black;
        drawingAttributes.IgnorePressure = false;
        drawingAttributes.FitToCurve = true;
        inkCanvas.InkPresenter.UpdateDefaultDrawingAttributes(drawingAttributes);

        // Listen for button click to initiate recognition.
        recognize.Click += RecognizeStrokes_Click;
    }
```
5.  <span data-ttu-id="4bf9b-125">In diesem Beispiel wird die Freihandeingabenanalyse mit dem Click-Ereignishandler der Schaltfläche „Erkennen“ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-125">For this example, we perform the ink analysis in the click event handler of the "Recognize" button.</span></span>
    - <span data-ttu-id="4bf9b-126">Rufen Sie zuerst [**GetStrokes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkstrokecontainer.GetStrokes) im [**StrokeContainer**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter.StrokeContainer) von [**InkCanvas.InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.inkcanvas.InkPresenter) auf, um alle aktuell erfassten Freihandstriche abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-126">First, call [**GetStrokes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkstrokecontainer.GetStrokes) on the [**StrokeContainer**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter.StrokeContainer) of the [**InkCanvas.InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.inkcanvas.InkPresenter) to get the collection of all current ink strokes.</span></span>
    - <span data-ttu-id="4bf9b-127">Wenn Freihandstriche vorhanden sind, übergeben Sie sie in einem Aufruf an [**AddDataForStrokes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer#Windows_UI_Input_Inking_Analysis_InkAnalyzer_AddDataForStrokes_Windows_Foundation_Collections_IIterable_Windows_UI_Input_Inking_InkStroke__) von InkAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-127">If ink strokes are present, pass them in a call to [**AddDataForStrokes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer#Windows_UI_Input_Inking_Analysis_InkAnalyzer_AddDataForStrokes_Windows_Foundation_Collections_IIterable_Windows_UI_Input_Inking_InkStroke__) of the InkAnalyzer.</span></span>
    - <span data-ttu-id="4bf9b-128">Wir versuchen, Zeichnungen und Text zu erkennen, Sie können allerdings auch die Methode [**SetStrokeDataKind**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.setstrokedatakind) verwenden, um anzugeben, ob Sie nur am Text (einschließlich der Dokumentstruktur und Aufzählungen) oder nur an den Zeichnungen (einschließlich der Formenerkennung) interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-128">We're trying to recognize both drawings and text, but you can use the [**SetStrokeDataKind**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.setstrokedatakind) method to specify whether you're interested only in text (including document structure and bullet lists) or only in drawings (including shape recognition).</span></span>
    - <span data-ttu-id="4bf9b-129">Rufen Sie [**AnalyzeAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.AnalyzeAsync) auf, um die Freihandeingabenanalyse zu initiieren und [**InkAnalysisResult**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult) abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-129">Call [**AnalyzeAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.AnalyzeAsync) to initiate ink analysis and get the [**InkAnalysisResult**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult).</span></span>
    - <span data-ttu-id="4bf9b-130">Wenn unter [**Status**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult.Status) die Option **Aktualisiert** zurückgegeben wird, rufen Sie [**FindNodes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisroot.findnodes) für [**InkAnalysisNodeKind.InkWord**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisnodekind) und [**InkAnalysisNodeKind.InkDrawing**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisnodekind) auf.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-130">If [**Status**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult.Status) returns a state of **Updated**, call [**FindNodes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisroot.findnodes) for both [**InkAnalysisNodeKind.InkWord**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisnodekind) and [**InkAnalysisNodeKind.InkDrawing**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisnodekind).</span></span>
    - <span data-ttu-id="4bf9b-131">Durchlaufen Sie beide Sätze der Knotentypen und zeichnen Sie den entsprechenden Text oder die Form in den Erkennungszeichenbereich (unter dem Freihandeingabe-Zeichenbereich).</span><span class="sxs-lookup"><span data-stu-id="4bf9b-131">Iterate through both sets of node types and draw the respective text or shape on the recognition canvas (below the ink canvas).</span></span>
    - <span data-ttu-id="4bf9b-132">Löschen Sie dann die erkannten Knoten aus dem InkAnalyzer und die entsprechenden Freihandstriche aus dem Freihandeingabe-Zeichenbereich.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-132">Finally, delete the recognized nodes from the InkAnalyzer and the corresponding ink strokes from the ink canvas.</span></span>
```csharp
/// <summary>
/// The "Analyze" button click handler.
/// Ink recognition is performed here.
/// </summary>
/// <param name="sender">Source of the click event</param>
/// <param name="e">Event args for the button click routed event</param>
private async void RecognizeStrokes_Click(object sender, RoutedEventArgs e)
    {
        inkStrokes = inkCanvas.InkPresenter.StrokeContainer.GetStrokes();
        // Ensure an ink stroke is present.
        if (inkStrokes.Count > 0)
        {
            inkAnalyzer.AddDataForStrokes(inkStrokes);

            // In this example, we try to recognizing both 
            // writing and drawing, so the platform default 
            // of "InkAnalysisStrokeKind.Auto" is used.
            // If you're only interested in a specific type of recognition,
            // such as writing or drawing, you can constrain recognition 
            // using the SetStrokDataKind method as follows:
            // foreach (var stroke in strokesText)
            // {
            //     analyzerText.SetStrokeDataKind(
            //      stroke.Id, InkAnalysisStrokeKind.Writing);
            // }
            // This can improve both efficiency and recognition results.
            inkAnalysisResults = await inkAnalyzer.AnalyzeAsync();

            // Have ink strokes on the canvas changed?
            if (inkAnalysisResults.Status == InkAnalysisStatus.Updated)
            {
                // Find all strokes that are recognized as handwriting and 
                // create a corresponding ink analysis InkWord node.
                var inkwordNodes = 
                    inkAnalyzer.AnalysisRoot.FindNodes(
                        InkAnalysisNodeKind.InkWord);

                // Iterate through each InkWord node.
                // Draw primary recognized text on recognitionCanvas 
                // (for this example, we ignore alternatives), and delete 
                // ink analysis data and recognized strokes.
                foreach (InkAnalysisInkWord node in inkwordNodes)
                {
                    // Draw a TextBlock object on the recognitionCanvas.
                    DrawText(node.RecognizedText, node.BoundingRect);

                    foreach (var strokeId in node.GetStrokeIds())
                    {
                        var stroke = 
                            inkCanvas.InkPresenter.StrokeContainer.GetStrokeById(strokeId);
                        stroke.Selected = true;
                    }
                    inkAnalyzer.RemoveDataForStrokes(node.GetStrokeIds());
                }
                inkCanvas.InkPresenter.StrokeContainer.DeleteSelected();

                // Find all strokes that are recognized as a drawing and 
                // create a corresponding ink analysis InkDrawing node.
                var inkdrawingNodes =
                    inkAnalyzer.AnalysisRoot.FindNodes(
                        InkAnalysisNodeKind.InkDrawing);
                // Iterate through each InkDrawing node.
                // Draw recognized shapes on recognitionCanvas and
                // delete ink analysis data and recognized strokes.
                foreach (InkAnalysisInkDrawing node in inkdrawingNodes)
                {
                    if (node.DrawingKind == InkAnalysisDrawingKind.Drawing)
                    {
                        // Catch and process unsupported shapes (lines and so on) here.
                    }
                    // Process generalized shapes here (ellipses and polygons).
                    else
                    {
                        // Draw an Ellipse object on the recognitionCanvas (circle is a specialized ellipse).
                        if (node.DrawingKind == InkAnalysisDrawingKind.Circle || node.DrawingKind == InkAnalysisDrawingKind.Ellipse)
                        {
                            DrawEllipse(node);
                        }
                        // Draw a Polygon object on the recognitionCanvas.
                        else
                        {
                            DrawPolygon(node);
                        }
                        foreach (var strokeId in node.GetStrokeIds())
                        {
                            var stroke = inkCanvas.InkPresenter.StrokeContainer.GetStrokeById(strokeId);
                            stroke.Selected = true;
                        }
                    }
                    inkAnalyzer.RemoveDataForStrokes(node.GetStrokeIds());
                }
                inkCanvas.InkPresenter.StrokeContainer.DeleteSelected();
            }
        }
    }
```
6. <span data-ttu-id="4bf9b-133">Im Folgenden wird die Funktion zum Zeichnen eines TextBlock-Elements im Erkennungszeichenbereich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-133">Here's the function for drawing a TextBlock on our recognition canvas.</span></span> <span data-ttu-id="4bf9b-134">Wir verwenden das umgebende Rechteck der zugehörigen Freihandstriche auf dem Freihandeingabe-Zeichenbereich, um die Position und den Schriftgrad des TextBlock-Elements festlegen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-134">We use the bounding rectangle of the associated ink stroke on the ink canvas to set the position and font size of the TextBlock.</span></span>
```csharp
/// <summary>
/// Draw ink recognition text string on the recognitionCanvas.
/// </summary>
/// <param name="recognizedText">The string returned by text recognition.</param>
/// <param name="boundingRect">The bounding rect of the original ink writing.</param>
private void DrawText(string recognizedText, Rect boundingRect)
{
    TextBlock text = new TextBlock();
    Canvas.SetTop(text, boundingRect.Top);
    Canvas.SetLeft(text, boundingRect.Left);

    text.Text = recognizedText;
    text.FontSize = boundingRect.Height;

    recognitionCanvas.Children.Add(text);
}
```
7. <span data-ttu-id="4bf9b-135">Im Folgenden werden die Funktionen zum Zeichnen von Ellipsen und Polygonen im Erkennungszeichenbereich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-135">Here are the functions for drawing ellipses and polygons on our recognition canvas.</span></span> <span data-ttu-id="4bf9b-136">Wir verwenden das umgebende Rechteck der zugehörigen Freihandstriche auf dem Freihandeingabe-Zeichenbereich, um die Position und den Schriftgrad der Formen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-136">We use the bounding rectangle of the associated ink stroke on the ink canvas to set the position and font size of the shapes.</span></span>
```csharp
    // Draw an ellipse on the recognitionCanvas.
    private void DrawEllipse(InkAnalysisInkDrawing shape)
    {
        var points = shape.Points;
        Ellipse ellipse = new Ellipse();

        ellipse.Width = shape.BoundingRect.Width;
        ellipse.Height = shape.BoundingRect.Height;

        Canvas.SetTop(ellipse, shape.BoundingRect.Top);
        Canvas.SetLeft(ellipse, shape.BoundingRect.Left);

        var brush = new SolidColorBrush(Windows.UI.ColorHelper.FromArgb(255, 0, 0, 255));
        ellipse.Stroke = brush;
        ellipse.StrokeThickness = 2;
        recognitionCanvas.Children.Add(ellipse);
    }

    // Draw a polygon on the recognitionCanvas.
    private void DrawPolygon(InkAnalysisInkDrawing shape)
    {
        List<Point> points = new List<Point>(shape.Points);
        Polygon polygon = new Polygon();

        foreach (Point point in points)
        {
            polygon.Points.Add(point);
        }

        var brush = new SolidColorBrush(Windows.UI.ColorHelper.FromArgb(255, 0, 0, 255));
        polygon.Stroke = brush;
        polygon.StrokeThickness = 2;
        recognitionCanvas.Children.Add(polygon);
    }
```

<span data-ttu-id="4bf9b-137">Nachfolgend finden Sie das Beispiel in Aktion:</span><span class="sxs-lookup"><span data-stu-id="4bf9b-137">Here's this sample in action:</span></span>

| <span data-ttu-id="4bf9b-138">Vor der Analyse</span><span class="sxs-lookup"><span data-stu-id="4bf9b-138">Before analysis</span></span> | <span data-ttu-id="4bf9b-139">Nach der Analyse</span><span class="sxs-lookup"><span data-stu-id="4bf9b-139">After analysis</span></span> |
| --- | --- |
| ![Vor der Analyse](images/ink/ink-analysis-raw2-small.png) | ![Nach der Analyse](images/ink/ink-analysis-analyzed2-small.png) |

---

## <a name="constrained-handwriting-recognition"></a><span data-ttu-id="4bf9b-142">Eingeschränkte Schrifterkennung</span><span class="sxs-lookup"><span data-stu-id="4bf9b-142">Constrained handwriting recognition</span></span>

<span data-ttu-id="4bf9b-143">Im vorherigen Abschnitt ([Freiformerkennung mit der Freihandeingabenanalyse](#free-form-recognition-with-ink-analysis)) haben wir erklärt, wie Sie [Ink-Analyse-APIs](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis) verwenden, um beliebige Freihandstriche in einem InkCanvas-Bereich zu analysieren und zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-143">In the preceding section ([Free-form recognition with ink analysis](#free-form-recognition-with-ink-analysis)), we demonstrated how to use the [ink analysis APIs](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis) to analyze and recognize arbitrary ink strokes within an InkCanvas area.</span></span>

<span data-ttu-id="4bf9b-144">In diesem Abschnitt wird veranschaulicht, wie mit dem Windows Ink-Schrifterkennungsmodul (nicht der Freihandeingabenanalyse) ein Satz von Freihandstrichen in einer [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Klasse in Text interpretiert wird (je nach standardmäßig installiertem Sprachpaket).</span><span class="sxs-lookup"><span data-stu-id="4bf9b-144">In this section, we demonstrate how to use the Windows Ink handwriting recognition engine (not ink analysis) to convert a set of strokes on an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) to text (based on the installed default language pack).</span></span>

> [!NOTE]
> <span data-ttu-id="4bf9b-145">Die grundlegende Schrifterkennung, so wie in diesem Abschnitt beschrieben, eignet sich insbesondere für einfache einzeilige Nur-Text-Eingabeszenarien wie Formulareingaben.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-145">The basic handwriting recognition shown in this section is best suited for single-line, text input scenarios such as form input.</span></span> <span data-ttu-id="4bf9b-146">Informationen zu umfangreicheren Erkennungsszenarien, die eine Analyse und Interpretation der Dokumentstruktur, Listenelemente, Formen und Zeichnungen (zusätzlich zur Texterkennung) umfassen, finden Sie im vorherigen Abschnitt: [Freiformerkennung mit der Freihandeingabenanalyse](#free-form-recognition-with-ink-analysis).</span><span class="sxs-lookup"><span data-stu-id="4bf9b-146">For richer recognition scenarios that include analysis and interpretation of document structure, list items, shapes, and drawings (in addition to text recognition), see the previous section: [Free-form recognition with ink analysis](#free-form-recognition-with-ink-analysis).</span></span>

<span data-ttu-id="4bf9b-147">In diesem Beispiel wird die Erkennung durch den Benutzer initiiert, wenn er nach Abschluss des Schreibens auf eine Schaltfläche klickt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-147">In this example, recognition is initiated when the user clicks a button to indicate they are finished writing.</span></span>

**<span data-ttu-id="4bf9b-148">Laden Sie dieses Beispiel aus [Beispiel für die Freihandschrifterkennung](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-handwriting-reco.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-148">Download this sample from [Ink handwriting recognition sample](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-handwriting-reco.zip)</span></span>**

1.  <span data-ttu-id="4bf9b-149">Zuerst wird die Benutzeroberfläche eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-149">First, we set up the UI.</span></span>

    <span data-ttu-id="4bf9b-150">Die Benutzeroberfläche umfasst die Schaltfläche „Erkennen“, die [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Klasse und einen Bereich zum Anzeigen der Ergebnisse der Erkennung.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-150">The UI includes a "Recognize" button, the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535), and an area to display recognition results.</span></span>    
```    XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="HeaderPanel"
                    Orientation="Horizontal"
                    Grid.Row="0">
            <TextBlock x:Name="Header"
                       Text="Basic ink recognition sample"
                       Style="{ThemeResource HeaderTextBlockStyle}"
                       Margin="10,0,0,0" />
            <Button x:Name="recognize"
                    Content="Recognize"
                    Margin="50,0,10,0"/>
        </StackPanel>
        <Grid Grid.Row="1">
            <Grid.RowDefinitions>
                <RowDefinition Height="*"/>
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <InkCanvas x:Name="inkCanvas"
                       Grid.Row="0"/>
            <TextBlock x:Name="recognitionResult"
                       Grid.Row="1"
                       Margin="50,0,10,0"/>
        </Grid>
    </Grid>
```

2. <span data-ttu-id="4bf9b-151">In diesem Beispiel müssen Sie zunächst die für die Freihandfunktion benötigten Namespaceverweistypen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="4bf9b-151">For this example, you need to first add the namespace type references required for our ink functionality:</span></span>
    - [<span data-ttu-id="4bf9b-152">Windows.UI.Input</span><span class="sxs-lookup"><span data-stu-id="4bf9b-152">Windows.UI.Input</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input)
    - [<span data-ttu-id="4bf9b-153">Windows.UI.Input.Inking</span><span class="sxs-lookup"><span data-stu-id="4bf9b-153">Windows.UI.Input.Inking</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.inking)


3.  <span data-ttu-id="4bf9b-154">Dann werden einige grundlegende Verhaltensweisen für Freihandeingaben festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-154">We then set some basic ink input behaviors.</span></span>

    <span data-ttu-id="4bf9b-155">Die [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Eigenschaft wird für die Interpretation von Eingabedaten von Stift oder Maus als Freihandstriche ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)) konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-155">The [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) is configured to interpret input data from both pen and mouse as ink strokes ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)).</span></span> <span data-ttu-id="4bf9b-156">Freihandstriche werden in der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Klasse mit der angegebenen [**InkDrawingAttributes**](https://msdn.microsoft.com/library/windows/desktop/ms695050)-Klasse gerendert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-156">Ink strokes are rendered on the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) using the specified [**InkDrawingAttributes**](https://msdn.microsoft.com/library/windows/desktop/ms695050).</span></span> <span data-ttu-id="4bf9b-157">Außerdem wird ein Listener für das Click-Ereignis der Schaltfläche „Erkennen“ deklariert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-157">A listener for the click event on the "Recognize" button is also declared.</span></span>
```csharp
public MainPage()
    {
        this.InitializeComponent();

        // Set supported inking device types.
        inkCanvas.InkPresenter.InputDeviceTypes =
            Windows.UI.Core.CoreInputDeviceTypes.Mouse |
            Windows.UI.Core.CoreInputDeviceTypes.Pen;

        // Set initial ink stroke attributes.
        InkDrawingAttributes drawingAttributes = new InkDrawingAttributes();
        drawingAttributes.Color = Windows.UI.Colors.Black;
        drawingAttributes.IgnorePressure = false;
        drawingAttributes.FitToCurve = true;
        inkCanvas.InkPresenter.UpdateDefaultDrawingAttributes(drawingAttributes);

        // Listen for button click to initiate recognition.
        recognize.Click += Recognize_Click;
    }
```

4.  <span data-ttu-id="4bf9b-158">Zum Schluss wird die grundlegende Schrifterkennung durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-158">Finally, we perform the basic handwriting recognition.</span></span> <span data-ttu-id="4bf9b-159">In diesem Beispiel wird die Schrifterkennung mit dem Click-Ereignishandler der Schaltfläche „Erkennen“ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-159">For this example, we use the click event handler of the "Recognize" button to perform the handwriting recognition.</span></span>

    <span data-ttu-id="4bf9b-160">Ein [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) speichert alle Freihandstriche in einem [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-160">An [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) stores all ink strokes in an [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) object.</span></span> <span data-ttu-id="4bf9b-161">Die Freihandstriche werden durch die [**StrokeContainer**](https://msdn.microsoft.com/library/windows/apps/dn948766)-Eigenschaft von **InkPresenter** verfügbar gemacht und mit der [**GetStrokes**](https://msdn.microsoft.com/library/windows/apps/br208499)-Methode abgerufen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-161">The strokes are exposed through the [**StrokeContainer**](https://msdn.microsoft.com/library/windows/apps/dn948766) property of the **InkPresenter** and retrieved using the [**GetStrokes**](https://msdn.microsoft.com/library/windows/apps/br208499) method.</span></span>
```csharp
// Get all strokes on the InkCanvas.
    IReadOnlyList<InkStroke> currentStrokes = inkCanvas.InkPresenter.StrokeContainer.GetStrokes();
```

    An [**InkRecognizerContainer**](https://msdn.microsoft.com/library/windows/apps/br208479) is created to manage the handwriting recognition process.

```csharp
// Create a manager for the InkRecognizer object
    // used in handwriting recognition.
    InkRecognizerContainer inkRecognizerContainer =
        new InkRecognizerContainer();
```

    [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/br208446) is called to retrieve a set of [**InkRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/br208464) objects.

    Recognition results are produced for each word that is detected by an [**InkRecognizer**](https://msdn.microsoft.com/library/windows/apps/br208478).

```csharp
// Recognize all ink strokes on the ink canvas.
    IReadOnlyList<InkRecognitionResult> recognitionResults =
        await inkRecognizerContainer.RecognizeAsync(
            inkCanvas.InkPresenter.StrokeContainer,
            InkRecognitionTarget.All);
```

    Each [**InkRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/br208464) object contains a set of text candidates. The topmost item in this list is considered by the recognition engine to be the best match, followed by the remaining candidates in order of decreasing confidence.

    We iterate through each [**InkRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/br208464) and compile the list of candidates. The candidates are then displayed and the [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) is cleared (which also clears the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)).

```csharp
string str = "Recognition result\n";
    // Iterate through the recognition results.
    foreach (var result in recognitionResults)
    {
        // Get all recognition candidates from each recognition result.
        IReadOnlyList<string> candidates = result.GetTextCandidates();
        str += "Candidates: " + candidates.Count.ToString() + "\n";
        foreach (string candidate in candidates)
        {
            str += candidate + " ";
        }
    }
    // Display the recognition candidates.
    recognitionResult.Text = str;
    // Clear the ink canvas once recognition is complete.
    inkCanvas.InkPresenter.StrokeContainer.Clear();
```

    Here's the click handler example, in full.

```csharp
// Handle button click to initiate recognition.
    private async void Recognize_Click(object sender, RoutedEventArgs e)
    {
        // Get all strokes on the InkCanvas.
        IReadOnlyList<InkStroke> currentStrokes = inkCanvas.InkPresenter.StrokeContainer.GetStrokes();

        // Ensure an ink stroke is present.
        if (currentStrokes.Count > 0)
        {
            // Create a manager for the InkRecognizer object
            // used in handwriting recognition.
            InkRecognizerContainer inkRecognizerContainer =
                new InkRecognizerContainer();

            // inkRecognizerContainer is null if a recognition engine is not available.
            if (!(inkRecognizerContainer == null))
            {
                // Recognize all ink strokes on the ink canvas.
                IReadOnlyList<InkRecognitionResult> recognitionResults =
                    await inkRecognizerContainer.RecognizeAsync(
                        inkCanvas.InkPresenter.StrokeContainer,
                        InkRecognitionTarget.All);
                // Process and display the recognition results.
                if (recognitionResults.Count > 0)
                {
                    string str = "Recognition result\n";
                    // Iterate through the recognition results.
                    foreach (var result in recognitionResults)
                    {
                        // Get all recognition candidates from each recognition result.
                        IReadOnlyList<string> candidates = result.GetTextCandidates();
                        str += "Candidates: " + candidates.Count.ToString() + "\n";
                        foreach (string candidate in candidates)
                        {
                            str += candidate + " ";
                        }
                    }
                    // Display the recognition candidates.
                    recognitionResult.Text = str;
                    // Clear the ink canvas once recognition is complete.
                    inkCanvas.InkPresenter.StrokeContainer.Clear();
                }
                else
                {
                    recognitionResult.Text = "No recognition results.";
                }
            }
            else
            {
                Windows.UI.Popups.MessageDialog messageDialog = new Windows.UI.Popups.MessageDialog("You must install handwriting recognition engine.");
                await messageDialog.ShowAsync();
            }
        }
        else
        {
            recognitionResult.Text = "No ink strokes to recognize.";
        }
    }
```

## <a name="international-recognition"></a><span data-ttu-id="4bf9b-162">Internationale Erkennung</span><span class="sxs-lookup"><span data-stu-id="4bf9b-162">International recognition</span></span>

<span data-ttu-id="4bf9b-163">Das Handschrifterkennungstool ist in die Windows-Freihandplattform integriert und umfasst einen Satz von Gebietsschemas und Sprachen, die von Windows unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-163">The handwriting recognition built into the Windows ink platform includes an extensive subset of locales and languages supported by Windows.</span></span>

<span data-ttu-id="4bf9b-164">Im Abschnitt der Eigenschaften [**InkRecognizer.Name**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkrecognizer.name.aspx) finden Sie eine Liste der von [**InkRecognizer**](https://msdn.microsoft.com/library/windows/apps/br208478) unterstützten Sprachen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-164">See the [**InkRecognizer.Name**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkrecognizer.name.aspx) property topic for a list of languages supported by the [**InkRecognizer**](https://msdn.microsoft.com/library/windows/apps/br208478) .</span></span>

<span data-ttu-id="4bf9b-165">Ihre App kann den Satz der installierten Schrifterkennungsmodule abfragen und eines davon verwenden, oder der Benutzer wählt die bevorzugte Sprache aus.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-165">Your app can query the set of installed handwriting recognition engines and use one of those, or let a user select their preferred language.</span></span>

<span data-ttu-id="4bf9b-166">**Hinweis:**  Benutzer können eine Liste der installierten Sprachen anzeigen, indem Sie zum wechseln **Einstellungen –&gt; Zeit & Sprache**.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-166">**Note** Users can see a list of installed languages by going to **Settings -&gt; Time & Language**.</span></span> <span data-ttu-id="4bf9b-167">Die installierten Sprachen werden unter **Sprachen** aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-167">Installed languages are listed under **Languages**.</span></span>

<span data-ttu-id="4bf9b-168">So installieren Sie ein neues Sprachpaket und aktivieren die Schrifterkennung für die Sprache</span><span class="sxs-lookup"><span data-stu-id="4bf9b-168">To install new language packs and enable handwriting recognition for that language:</span></span>

1.  <span data-ttu-id="4bf9b-169">Öffnen Sie **Einstellungen &gt; Zeit & Sprache &gt; Region & Sprache**.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-169">Go to **Settings &gt; Time & language &gt; Region & language**.</span></span>
2.  <span data-ttu-id="4bf9b-170">Wählen Sie **Sprache hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-170">Select **Add a language**.</span></span>
3.  <span data-ttu-id="4bf9b-171">Wählen Sie eine Sprache aus der Liste und dann die Regionsversion aus.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-171">Select a language from the list, then choose the region version.</span></span> <span data-ttu-id="4bf9b-172">Die Sprache wird jetzt auf der Seite **Region & Sprache** aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-172">The language is now listed on the **Region & language** page.</span></span>
4.  <span data-ttu-id="4bf9b-173">Klicken Sie auf die Sprache, und wählen Sie **Optionen** aus.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-173">Click the language and select **Options**.</span></span>
5.  <span data-ttu-id="4bf9b-174">Laden Sie auf der Seite **Sprachoptionen** das **Schrifterkennungsmodul** herunter. (Sie können auch das vollständige Sprachpaket, das Spracherkennungsmodul und das Tastaturlayout hier herunterladen.)</span><span class="sxs-lookup"><span data-stu-id="4bf9b-174">On the **Language options** page, download the **Handwriting recognition engine** (they can also download the full language pack, speech recognition engine, and keyboard layout here).</span></span>

 

<span data-ttu-id="4bf9b-175">Hier wird gezeigt, wie auf Grundlage der ausgewählten Erkennung mit dem Schrifterkennungsmodul eine Reihe von Freihandstrichen in einer [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Klasse interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-175">Here, we demonstrate how to use the handwriting recognition engine to interpret a set of strokes on an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) based on the selected recognizer.</span></span>

<span data-ttu-id="4bf9b-176">Die Erkennung wird durch den Benutzer initiiert, indem er nach Abschluss des Schreibvorgangs auf eine Schaltfläche klickt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-176">The recognition is initiated by the user clicking a button when they are finished writing.</span></span>

1.  <span data-ttu-id="4bf9b-177">Zuerst wird die Benutzeroberfläche eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-177">First, we set up the UI.</span></span>

    <span data-ttu-id="4bf9b-178">Die Benutzeroberfläche umfasst die Schaltfläche „Erkennen“, ein Kombinationsfeld mit allen installierten Schrifterkennungen, den [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) und einen Bereich zum Anzeigen der Ergebnisse der Erkennung.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-178">The UI includes a "Recognize" button, a combo box that lists all installed handwriting recognizers, the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535), and an area to display recognition results.</span></span>
```    XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="HeaderPanel"
                    Orientation="Horizontal"
                    Grid.Row="0">
            <TextBlock x:Name="Header"
                       Text="Advanced international ink recognition sample"
                       Style="{ThemeResource HeaderTextBlockStyle}"
                       Margin="10,0,0,0" />
            <ComboBox x:Name="comboInstalledRecognizers"
                     Margin="50,0,10,0">
                <ComboBox.ItemTemplate>
                    <DataTemplate>
                        <StackPanel Orientation="Horizontal">
                            <TextBlock Text="{Binding Name}" />
                        </StackPanel>
                    </DataTemplate>
                </ComboBox.ItemTemplate>
            </ComboBox>
            <Button x:Name="buttonRecognize"
                    Content="Recognize"
                    IsEnabled="False"
                    Margin="50,0,10,0"/>
        </StackPanel>
        <Grid Grid.Row="1">
            <Grid.RowDefinitions>
                <RowDefinition Height="*"/>
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <InkCanvas x:Name="inkCanvas"
                       Grid.Row="0"/>
            <TextBlock x:Name="recognitionResult"
                       Grid.Row="1"
                       Margin="50,0,10,0"/>
        </Grid>
    </Grid>
```

2.  <span data-ttu-id="4bf9b-179">Dann werden einige grundlegende Verhalten für Freihandeingaben festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-179">We then set some basic ink input behaviors.</span></span>

    <span data-ttu-id="4bf9b-180">Die [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Eigenschaft wird für die Interpretation von Eingabedaten von Stift oder Maus als Freihandstriche ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)) konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-180">The [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) is configured to interpret input data from both pen and mouse as ink strokes ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)).</span></span> <span data-ttu-id="4bf9b-181">Freihandstriche werden in der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Klasse mit der angegebenen [**InkDrawingAttributes**](https://msdn.microsoft.com/library/windows/desktop/ms695050)-Klasse gerendert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-181">Ink strokes are rendered on the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) using the specified [**InkDrawingAttributes**](https://msdn.microsoft.com/library/windows/desktop/ms695050).</span></span>

    <span data-ttu-id="4bf9b-182">Zum Ausfüllen des Kombinationsfelds für die Erkennung mit einer Liste der installierten Schrifterkennungen wird eine `InitializeRecognizerList`-Funktion aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-182">We call an `InitializeRecognizerList` function to populate the recognizer combo box with a list of installed handwriting recognizers.</span></span>

    <span data-ttu-id="4bf9b-183">Außerdem werden Listener für das Click-Ereignis auf die Schaltfläche „Erkennen“ und das Ereignis der geänderten Auswahl im Kombinationsfeld für die Erkennung deklariert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-183">We also declare listeners for the click event on the "Recognize" button and the selection changed event on the recognizer combo box.</span></span>
```csharp
 public MainPage()
     {
         this.InitializeComponent();

         // Set supported inking device types.
         inkCanvas.InkPresenter.InputDeviceTypes =
             Windows.UI.Core.CoreInputDeviceTypes.Mouse |
             Windows.UI.Core.CoreInputDeviceTypes.Pen;

         // Set initial ink stroke attributes.
         InkDrawingAttributes drawingAttributes = new InkDrawingAttributes();
         drawingAttributes.Color = Windows.UI.Colors.Black;
         drawingAttributes.IgnorePressure = false;
         drawingAttributes.FitToCurve = true;
         inkCanvas.InkPresenter.UpdateDefaultDrawingAttributes(drawingAttributes);

         // Populate the recognizer combo box with installed recognizers.
         InitializeRecognizerList();

         // Listen for combo box selection.
         comboInstalledRecognizers.SelectionChanged +=
             comboInstalledRecognizers_SelectionChanged;

         // Listen for button click to initiate recognition.
         buttonRecognize.Click += Recognize_Click;
     }
```

3.  <span data-ttu-id="4bf9b-184">Das Kombinationsfeld für die Erkennung wird mit einer Liste der installierten Schrifterkennungen aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-184">We populate the recognizer combo box with a list of installed handwriting recognizers.</span></span>

    <span data-ttu-id="4bf9b-185">Eine [**InkRecognizerContainer**](https://msdn.microsoft.com/library/windows/apps/br208479)-Klasse wird erstellt, um den Schrifterkennungsprozess zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-185">An [**InkRecognizerContainer**](https://msdn.microsoft.com/library/windows/apps/br208479) is created to manage the handwriting recognition process.</span></span> <span data-ttu-id="4bf9b-186">Rufen Sie mit diesem Objekt [**GetRecognizers**](https://msdn.microsoft.com/library/windows/apps/br208480). Rufen Sie dann die Liste der installierten Erkennungen ab, um das Kombinationsfeld für die Erkennung aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-186">Use this object to call [**GetRecognizers**](https://msdn.microsoft.com/library/windows/apps/br208480) and retrieve the list of installed recognizers to populate the recognizer combo box.</span></span>
```csharp
// Populate the recognizer combo box with installed recognizers.
    private void InitializeRecognizerList()
    {
        // Create a manager for the handwriting recognition process.
        inkRecognizerContainer = new InkRecognizerContainer();
        // Retrieve the collection of installed handwriting recognizers.
        IReadOnlyList<InkRecognizer> installedRecognizers =
            inkRecognizerContainer.GetRecognizers();
        // inkRecognizerContainer is null if a recognition engine is not available.
        if (!(inkRecognizerContainer == null))
        {
            comboInstalledRecognizers.ItemsSource = installedRecognizers;
            buttonRecognize.IsEnabled = true;
        }
    }
```

4.  <span data-ttu-id="4bf9b-187">Aktualisieren Sie die Handschrifterkennung, wenn die Auswahl im Kombinationsfeld für die Erkennung geändert wird.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-187">Update the handwriting recognizer if the recognizer combo box selection changes.</span></span>

    <span data-ttu-id="4bf9b-188">Rufen Sie mit [**InkRecognizerContainer**](https://msdn.microsoft.com/library/windows/apps/br208479) die [**SetDefaultRecognizer**](https://msdn.microsoft.com/library/windows/apps/hh920328)-Methode auf Grundlage der ausgewählten Erkennung im Kombinationsfeld für die Erkennung auf.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-188">Use the [**InkRecognizerContainer**](https://msdn.microsoft.com/library/windows/apps/br208479) to call [**SetDefaultRecognizer**](https://msdn.microsoft.com/library/windows/apps/hh920328) based on the selected recognizer from the recognizer combo box.</span></span>
```csharp
// Handle recognizer change.
    private void comboInstalledRecognizers_SelectionChanged(
        object sender, SelectionChangedEventArgs e)
    {
        inkRecognizerContainer.SetDefaultRecognizer(
            (InkRecognizer)comboInstalledRecognizers.SelectedItem);
    }
```

5.  <span data-ttu-id="4bf9b-189">Abschließend wird die Schrifterkennung auf Grundlage der ausgewählten Erkennung für die Handschrift ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-189">Finally, we perform the handwriting recognition based on the selected handwriting recognizer.</span></span> <span data-ttu-id="4bf9b-190">In diesem Beispiel wird die Schrifterkennung mit dem Click-Ereignishandler der Schaltfläche „Erkennen“ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-190">For this example, we use the click event handler of the "Recognize" button to perform the handwriting recognition.</span></span>

    <span data-ttu-id="4bf9b-191">Ein [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) speichert alle Freihandstriche in einem [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-191">An [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) stores all ink strokes in an [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) object.</span></span> <span data-ttu-id="4bf9b-192">Die Freihandstriche werden durch die [**StrokeContainer**](https://msdn.microsoft.com/library/windows/apps/dn948766)-Eigenschaft von **InkPresenter** verfügbar gemacht und mit der [**GetStrokes**](https://msdn.microsoft.com/library/windows/apps/br208499)-Methode abgerufen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-192">The strokes are exposed through the [**StrokeContainer**](https://msdn.microsoft.com/library/windows/apps/dn948766) property of the **InkPresenter** and retrieved using the [**GetStrokes**](https://msdn.microsoft.com/library/windows/apps/br208499) method.</span></span>
```csharp
// Get all strokes on the InkCanvas.
    IReadOnlyList<InkStroke> currentStrokes =
        inkCanvas.InkPresenter.StrokeContainer.GetStrokes();
```

    [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/br208446) is called to retrieve a set of [**InkRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/br208464) objects.

    Recognition results are produced for each word that is detected by an [**InkRecognizer**](https://msdn.microsoft.com/library/windows/apps/br208478).

```csharp
// Recognize all ink strokes on the ink canvas.
    IReadOnlyList<InkRecognitionResult> recognitionResults =
        await inkRecognizerContainer.RecognizeAsync(
            inkCanvas.InkPresenter.StrokeContainer,
            InkRecognitionTarget.All);
```

    Each [**InkRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/br208464) object contains a set of text candidates. The topmost item in this list is considered by the recognition engine to be the best match, followed by the remaining candidates in order of decreasing confidence.

    We iterate through each [**InkRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/br208464) and compile the list of candidates. The candidates are then displayed and the [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) is cleared (which also clears the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)).

```csharp
string str = "Recognition result\n";
    // Iterate through the recognition results.
    foreach (InkRecognitionResult result in recognitionResults)
    {
        // Get all recognition candidates from each recognition result.
        IReadOnlyList<string> candidates =
            result.GetTextCandidates();
        str += "Candidates: " + candidates.Count.ToString() + "\n";
        foreach (string candidate in candidates)
        {
            str += candidate + " ";
        }
    }
    // Display the recognition candidates.
    recognitionResult.Text = str;
    // Clear the ink canvas once recognition is complete.
    inkCanvas.InkPresenter.StrokeContainer.Clear();
```

    Here's the click handler example, in full.
    
```csharp
// Handle button click to initiate recognition.
    private async void Recognize_Click(object sender, RoutedEventArgs e)
    {
        // Get all strokes on the InkCanvas.
        IReadOnlyList<InkStroke> currentStrokes =
            inkCanvas.InkPresenter.StrokeContainer.GetStrokes();

        // Ensure an ink stroke is present.
        if (currentStrokes.Count > 0)
        {
            // inkRecognizerContainer is null if a recognition engine is not available.
            if (!(inkRecognizerContainer == null))
            {
                // Recognize all ink strokes on the ink canvas.
                IReadOnlyList<InkRecognitionResult> recognitionResults =
                    await inkRecognizerContainer.RecognizeAsync(
                        inkCanvas.InkPresenter.StrokeContainer,
                        InkRecognitionTarget.All);
                // Process and display the recognition results.
                if (recognitionResults.Count > 0)
                {
                    string str = "Recognition result\n";
                    // Iterate through the recognition results.
                    foreach (InkRecognitionResult result in recognitionResults)
                    {
                        // Get all recognition candidates from each recognition result.
                        IReadOnlyList<string> candidates =
                            result.GetTextCandidates();
                        str += "Candidates: " + candidates.Count.ToString() + "\n";
                        foreach (string candidate in candidates)
                        {
                            str += candidate + " ";
                        }
                    }
                    // Display the recognition candidates.
                    recognitionResult.Text = str;
                    // Clear the ink canvas once recognition is complete.
                    inkCanvas.InkPresenter.StrokeContainer.Clear();
                }
                else
                {
                    recognitionResult.Text = "No recognition results.";
                }
            }
            else
            {
                Windows.UI.Popups.MessageDialog messageDialog =
                    new Windows.UI.Popups.MessageDialog(
                        "You must install handwriting recognition engine.");
                await messageDialog.ShowAsync();
            }
        }
        else
        {
            recognitionResult.Text = "No ink strokes to recognize.";
        }
    }
```

## <a name="dynamic-recognition"></a><span data-ttu-id="4bf9b-193">Dynamische Erkennung</span><span class="sxs-lookup"><span data-stu-id="4bf9b-193">Dynamic recognition</span></span>

<span data-ttu-id="4bf9b-194">Während der Benutzer bei den beiden obigen Beispielen auf eine Schaltfläche zum Starten der Spracherkennung drücken müssen, können Sie die dynamische Erkennung mithilfe der Freihandstricheingabe mit einer einfachen Timing-Funktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-194">While, the previous two examples require the user to press a button to start recognition, you can also perform dynamic recognition using stroke input paired with a basic timing function.</span></span>

<span data-ttu-id="4bf9b-195">In diesem Beispiel werden die gleichen Einstellungen für Benutzeroberfläche und Freihandstriche verwendet wie im Beispiel für internationale Erkennung oben.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-195">For this example, we'll use the same UI and stroke settings as the previous international recognition example.</span></span>

1. <span data-ttu-id="4bf9b-196">Diese globalen Objekte ([InkAnalyzer](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.analysis.inkanalyzer), [InkStroke](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkstroke), [InkAnalysisResult](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult), [DispatcherTimer](https://docs.microsoft.com/uwp/api/windows.ui.xaml.dispatchertimer)) werden in der gesamten App verwendet.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-196">These global objects ([InkAnalyzer](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.analysis.inkanalyzer), [InkStroke](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkstroke), [InkAnalysisResult](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult), [DispatcherTimer](https://docs.microsoft.com/uwp/api/windows.ui.xaml.dispatchertimer)) are used throughout our app.</span></span>    
```csharp
    // Stroke recognition globals.
    InkAnalyzer inkAnalyzer;
    DispatcherTimer recoTimer;
```

2.  <span data-ttu-id="4bf9b-197">Anstelle einer Schaltfläche zum Initiieren der Erkennung werden Listener für zwei [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Freihandstrichereignisse ([**StrokesCollected**](https://msdn.microsoft.com/library/windows/apps/dn922024) und [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702)) hinzugefügt. Zudem wird ein einfacher Timer ([**DispatcherTimer**](https://msdn.microsoft.com/library/windows/apps/br244250)) mit einem [**Tick**](https://msdn.microsoft.com/library/windows/apps/br244256)-Intervall von einer Sekunde eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-197">Instead of a button to initiate recognition, we add listeners for two [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) stroke events ([**StrokesCollected**](https://msdn.microsoft.com/library/windows/apps/dn922024) and [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702)), and set up a basic timer ([**DispatcherTimer**](https://msdn.microsoft.com/library/windows/apps/br244250)) with a one second [**Tick**](https://msdn.microsoft.com/library/windows/apps/br244256) interval.</span></span>    
```csharp
    public MainPage()
    {
        this.InitializeComponent();

        // Set supported inking device types.
        inkCanvas.InkPresenter.InputDeviceTypes =
            Windows.UI.Core.CoreInputDeviceTypes.Mouse |
            Windows.UI.Core.CoreInputDeviceTypes.Pen;

        // Listen for stroke events on the InkPresenter to 
        // enable dynamic recognition.
        // StrokesCollected is fired when the user stops inking by 
        // lifting their pen or finger, or releasing the mouse button.
        inkCanvas.InkPresenter.StrokesCollected += inkCanvas_StrokesCollected;
        // StrokeStarted is fired when ink input is first detected.
        inkCanvas.InkPresenter.StrokeInput.StrokeStarted +=
            inkCanvas_StrokeStarted;

        inkAnalyzer = new InkAnalyzer();

        // Timer to manage dynamic recognition.
        recoTimer = new DispatcherTimer();
        recoTimer.Interval = TimeSpan.FromSeconds(1);
        recoTimer.Tick += recoTimer_TickAsync;
    }
```

3.  <span data-ttu-id="4bf9b-198">Anschließend definieren wir die Handler für die InkPresenter-Ereignisse, die wir im ersten Schritt deklariert haben (wir überschreiben ebenfalls das [**OnNavigatingFrom**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.page.onnavigatingfrom)-Ereignis der Seite, um den Timer zu verwalten).</span><span class="sxs-lookup"><span data-stu-id="4bf9b-198">We then define the handlers for the InkPresenter events we declared in the first step (we also override the [**OnNavigatingFrom**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.page.onnavigatingfrom) page event to manage our timer).</span></span>

    - [**<span data-ttu-id="4bf9b-199">StrokesCollected</span><span class="sxs-lookup"><span data-stu-id="4bf9b-199">StrokesCollected</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn922024)  
    <span data-ttu-id="4bf9b-200">Fügen Sie dem InkAnalyzer Freihandstriche hinzu ([**AddDataForStrokes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.adddataforstrokes)) und starten Sie den Timer für die Erkennung, wenn der Benutzer die Freihandeingabe beendet, indem er den Stift oder Finger anhebt oder die Maustaste loslässt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-200">Add ink strokes ([**AddDataForStrokes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.adddataforstrokes)) to the InkAnalyzer and start the recognition timer when the user stops inking (by lifting their pen or finger, or releasing the mouse button).</span></span> <span data-ttu-id="4bf9b-201">Nach einer Sekunde ohne Freihandeingabe wird die Spracherkennung initiiert.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-201">After one second of no ink input, recognition is initiated.</span></span>  

        <span data-ttu-id="4bf9b-202">Verwenden Sie die Methode [**SetStrokeDataKind**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.setstrokedatakind), um anzugeben, ob Sie nur am Text (einschließlich der Dokumentstruktur und Aufzählungen) oder nur an den Zeichnungen (einschließlich der Formenerkennung) interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-202">Use the [**SetStrokeDataKind**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.setstrokedatakind) method to specify whether you're interested only in text (including document structure amd bullet lists) or only in drawings (inlcuding shape recognition).</span></span>

    - [**<span data-ttu-id="4bf9b-203">StrokeStarted</span><span class="sxs-lookup"><span data-stu-id="4bf9b-203">StrokeStarted</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn914702)  
    <span data-ttu-id="4bf9b-204">Wenn ein neuer Freihandstrich vor dem nächsten Tick-Ereignis des Timers beginnt, wird der Timer beendet, da es sich bei dem neuen Freihandstrich wahrscheinlich um die Fortsetzung der vorherigen Handschrifteingabe handelt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-204">If a new stroke starts before the next timer tick event, stop the timer as the new stroke is likely the continuation of a single handwriting entry.</span></span>
```csharp
    // Handler for the InkPresenter StrokeStarted event.
    // Don't perform analysis while a stroke is in progress.
    // If a new stroke starts before the next timer tick event,
    // stop the timer as the new stroke is likely the continuation
    // of a single handwriting entry.
    private void inkCanvas_StrokeStarted(InkStrokeInput sender, PointerEventArgs args)
    {
        recoTimer.Stop();
    }    
    // Handler for the InkPresenter StrokesCollected event.
    // Stop the timer and add the collected strokes to the InkAnalyzer.
    // Start the recognition timer when the user stops inking (by 
    // lifting their pen or finger, or releasing the mouse button).
    // If ink input is not detected after one second, initiate recognition.
    private void inkCanvas_StrokesCollected(InkPresenter sender, InkStrokesCollectedEventArgs args)
    {
        recoTimer.Stop();
        // If you're only interested in a specific type of recognition,
        // such as writing or drawing, you can constrain recognition 
        // using the SetStrokDataKind method, which can improve both 
        // efficiency and recognition results.
        // In this example, "InkAnalysisStrokeKind.Writing" is used.
        foreach (var stroke in args.Strokes)
        {
            inkAnalyzer.AddDataForStroke(stroke);
            inkAnalyzer.SetStrokeDataKind(stroke.Id, InkAnalysisStrokeKind.Writing);
        }
        recoTimer.Start();
    }    
    // Override the Page OnNavigatingFrom event handler to 
    // stop our timer if user leaves page.
    protected override void OnNavigatingFrom(NavigatingCancelEventArgs e)
    {
        recoTimer.Stop();
    } 
```

4.  <span data-ttu-id="4bf9b-205">Zum Schluss wird die Schrifterkennung durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-205">Finally, we perform the handwriting recognition.</span></span> <span data-ttu-id="4bf9b-206">In diesem Beispiel wird zum Initiieren der Schrifterkennung der [**Tick**](https://msdn.microsoft.com/library/windows/apps/br244256)-Ereignishandler einer [**DispatcherTimer**](https://msdn.microsoft.com/library/windows/apps/br244250)-Klasse verwendet.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-206">For this example, we use the [**Tick**](https://msdn.microsoft.com/library/windows/apps/br244256) event handler of a [**DispatcherTimer**](https://msdn.microsoft.com/library/windows/apps/br244250) to initiate the handwriting recognition.</span></span>
    - <span data-ttu-id="4bf9b-207">Rufen Sie [**AnalyzeAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.AnalyzeAsync) auf, um die Freihandeingabenanalyse zu initiieren und [**InkAnalysisResult**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult) abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-207">Call [**AnalyzeAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalyzer.AnalyzeAsync) to initiate ink analysis and get the [**InkAnalysisResult**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult).</span></span>
    - <span data-ttu-id="4bf9b-208">Wenn der [**Status**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult.Status) den Zustand **Aktualisiert** zurückgibt, rufen Sie [**FindNodes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisroot.findnodes) für Knotentypen von [**InkAnalysisNodeKind.InkWord**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisnodekind) auf.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-208">If [**Status**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisresult.Status) returns a state of **Updated**, call [**FindNodes**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisroot.findnodes) for node types of  [**InkAnalysisNodeKind.InkWord**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.analysis.inkanalysisnodekind).</span></span>
    - <span data-ttu-id="4bf9b-209">Durchlaufen Sie alle Knoten und zeigen Sie den erkannten Text an.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-209">Iterate through the nodes and display the recognized text.</span></span>
    - <span data-ttu-id="4bf9b-210">Löschen Sie dann die erkannten Knoten aus dem InkAnalyzer und die entsprechenden Freihandstriche aus dem Freihandeingabe-Zeichenbereich.</span><span class="sxs-lookup"><span data-stu-id="4bf9b-210">Finally, delete the recognized nodes from the InkAnalyzer and the corresponding ink strokes from the ink canvas.</span></span>
```csharp
    private async void recoTimer_TickAsync(object sender, object e)
    {
        recoTimer.Stop();
        if (!inkAnalyzer.IsAnalyzing)
        {
            InkAnalysisResult result = await inkAnalyzer.AnalyzeAsync();

            // Have ink strokes on the canvas changed?
            if (result.Status == InkAnalysisStatus.Updated)
            {
                // Find all strokes that are recognized as handwriting and 
                // create a corresponding ink analysis InkWord node.
                var inkwordNodes =
                    inkAnalyzer.AnalysisRoot.FindNodes(
                        InkAnalysisNodeKind.InkWord);

                // Iterate through each InkWord node.
                // Display the primary recognized text (for this example, 
                // we ignore alternatives), and then delete the 
                // ink analysis data and recognized strokes.
                foreach (InkAnalysisInkWord node in inkwordNodes)
                {
                    string recognizedText = node.RecognizedText;
                    // Display the recognition candidates.
                    recognitionResult.Text = recognizedText;

                    foreach (var strokeId in node.GetStrokeIds())
                    {
                        var stroke =
                            inkCanvas.InkPresenter.StrokeContainer.GetStrokeById(strokeId);
                        stroke.Selected = true;
                    }
                    inkAnalyzer.RemoveDataForStrokes(node.GetStrokeIds());
                }
                inkCanvas.InkPresenter.StrokeContainer.DeleteSelected();
            }
        }
        else
        {
            // Ink analyzer is busy. Wait a while and try again.
            recoTimer.Start();
        }
    }
```

## <a name="related-articles"></a><span data-ttu-id="4bf9b-211">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="4bf9b-211">Related articles</span></span>

* [<span data-ttu-id="4bf9b-212">Zeichen- und Eingabestiftinteraktionen</span><span class="sxs-lookup"><span data-stu-id="4bf9b-212">Pen and stylus interactions</span></span>](pen-and-stylus-interactions.md)

**<span data-ttu-id="4bf9b-213">Themenbeispiele</span><span class="sxs-lookup"><span data-stu-id="4bf9b-213">Topic samples</span></span>**
* [<span data-ttu-id="4bf9b-214">Freihandeingabenanalyse (einfach) (C#)</span><span class="sxs-lookup"><span data-stu-id="4bf9b-214">Ink analysis sample (basic) (C#)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-analysis-basic.zip)
* [<span data-ttu-id="4bf9b-215">Beispiel für Freihandschrifterkennung (C#)</span><span class="sxs-lookup"><span data-stu-id="4bf9b-215">Ink handwriting recognition sample (C#)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-handwriting-reco.zip)

**<span data-ttu-id="4bf9b-216">Andere Beispiele</span><span class="sxs-lookup"><span data-stu-id="4bf9b-216">Other samples</span></span>**
* [<span data-ttu-id="4bf9b-217">Einfaches Freihandbeispiel (C#/C++)</span><span class="sxs-lookup"><span data-stu-id="4bf9b-217">Simple ink sample (C#/C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620312)
* [<span data-ttu-id="4bf9b-218">Komplexes Freihandbeispiel (C++)</span><span class="sxs-lookup"><span data-stu-id="4bf9b-218">Complex ink sample (C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620314)
* [<span data-ttu-id="4bf9b-219">Freihandbeispiel (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="4bf9b-219">Ink sample (JavaScript)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620308)
* [<span data-ttu-id="4bf9b-220">Lernprogramm „Erste Schritte:” Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="4bf9b-220">Get Started Tutorial: Support ink in your UWP app</span></span>](https://aka.ms/appsample-ink)
* [<span data-ttu-id="4bf9b-221">Malbuchbeispiel</span><span class="sxs-lookup"><span data-stu-id="4bf9b-221">Coloring book sample</span></span>](https://aka.ms/cpubsample-coloringbook)
* [<span data-ttu-id="4bf9b-222">Familiennotizbeispiel</span><span class="sxs-lookup"><span data-stu-id="4bf9b-222">Family notes sample</span></span>](https://aka.ms/cpubsample-familynotessample)


 
