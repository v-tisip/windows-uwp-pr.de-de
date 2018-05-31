---
author: serenaz
title: Erste Schritte mit Windows ML
description: Erstellen Sie Ihre erste Windows ML-App mit diesem schrittweisen Lernprogramm.
ms.author: sezhen
ms.date: 03/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Windows Machine Learning, Winml, Windows ML
ms.localizationpriority: medium
ms.openlocfilehash: e30786f775a66bcf5c8e6dce0b4aab4f1f239be6
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816585"
---
# <a name="get-started-with-windows-ml"></a><span data-ttu-id="8fb41-104">Erste Schritte mit Windows ML</span><span class="sxs-lookup"><span data-stu-id="8fb41-104">Get started with Windows ML</span></span>

<span data-ttu-id="8fb41-105">In diesem Lernprogramm erstellen wir eine einfache UWP-App, die ein trainiertes Machine Learning-Modell verwendet, um ein numerisches Zeichen zu erkennen, das vom Benutzer gezeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="8fb41-105">In this tutorial, we'll build a simple UWP app that uses a trained machine learning model to recognize a numeric digit drawn by the user.</span></span> <span data-ttu-id="8fb41-106">Dieses Lernprogramm ist vorrangig auf das Laden und Verwenden von Windows ML in Ihrer App ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="8fb41-106">This tutorial primarily focuses on how to load and use Windows ML in your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8fb41-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8fb41-107">Prerequisites</span></span>

- [<span data-ttu-id="8fb41-108">Windows SDK – Build 17110+</span><span class="sxs-lookup"><span data-stu-id="8fb41-108">Windows SDK - Build 17110+</span></span>](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK)
- [<span data-ttu-id="8fb41-109">Visual Studio (Version 15.7 – Preview 1)</span><span class="sxs-lookup"><span data-stu-id="8fb41-109">Visual Studio (Version 15.7 - Preview 1)</span></span>](https://www.visualstudio.com/vs/preview/) 

    <span data-ttu-id="8fb41-110">**Hinweis**: Im Visual Studio-Installer müssen Sie das optionale Windows10 Preview SDK (10.0.17110.0) deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="8fb41-110">**Note**: Inside the Visual Studio Installer, you'll need to check off the optional Windows 10 Preview SDK (10.0.17110.0).</span></span>

## <a name="1-download-the-sample"></a><span data-ttu-id="8fb41-111">1. Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="8fb41-111">1. Download the sample</span></span>

<span data-ttu-id="8fb41-112">Zunächst müssen Sie unser [MNIST_GetStarted-Beispiel](https://github.com/Microsoft/Windows-Machine-Learning) von GitHub herunterladen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-112">First, you'll need to download our [MNIST_GetStarted sample](https://github.com/Microsoft/Windows-Machine-Learning) from GitHub.</span></span> <span data-ttu-id="8fb41-113">Wir haben eine Vorlage mit implementierten XAML-Steuerelementen und Ereignissen bereitgestellt, die Folgendes beinhaltet:</span><span class="sxs-lookup"><span data-stu-id="8fb41-113">We've provided a template with implemented XAML controls and events, including:</span></span>

- <span data-ttu-id="8fb41-114">Ein [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) zum Zeichnen der Ziffer.</span><span class="sxs-lookup"><span data-stu-id="8fb41-114">An [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) to draw the digit.</span></span>
- <span data-ttu-id="8fb41-115">[Schaltflächen](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button) zum Interpretieren der Ziffer und zum Löschen des Zeichenbereichs.</span><span class="sxs-lookup"><span data-stu-id="8fb41-115">[Buttons](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button) to interpret the digit and clear the canvas.</span></span>
- <span data-ttu-id="8fb41-116">Hilfsprogramm-Routinen zum Konvertieren der InkCanvas-Ausgabe in einen [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe).</span><span class="sxs-lookup"><span data-stu-id="8fb41-116">Helper routines to convert the InkCanvas output to a [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe).</span></span>

<span data-ttu-id="8fb41-117">Ein vollständiges MNIST-Beispiel kann ebenfalls von GitHub heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="8fb41-117">A completed MNIST sample is also available to download from GitHub.</span></span>

## <a name="2-open-project-in-visual-studio-preview"></a><span data-ttu-id="8fb41-118">2. Öffnen des Projekts in Visual Studio Preview</span><span class="sxs-lookup"><span data-stu-id="8fb41-118">2. Open project in Visual Studio Preview</span></span>

<span data-ttu-id="8fb41-119">Starten Sie Visual Studio Preview, und öffnen Sie die MNIST-Beispielanwendung.</span><span class="sxs-lookup"><span data-stu-id="8fb41-119">Launch Visual Studio Preview, and open the MNIST sample application.</span></span> <span data-ttu-id="8fb41-120">(Wenn die Lösung als nicht verfügbar angezeigt wird, müssen Sie mit der rechten Maustaste klicken und "Projekt erneut laden" auswählen.)</span><span class="sxs-lookup"><span data-stu-id="8fb41-120">(If the solution is shown as unavailable, you'll need to right-click and select "Reload Project.")</span></span>

<span data-ttu-id="8fb41-121">Im Projektmappen-Explorer enthält das Projekt drei Haupt-Codedateien:</span><span class="sxs-lookup"><span data-stu-id="8fb41-121">Inside the solution explorer, the project has three main code files:</span></span>

- `MainPage.xaml` <span data-ttu-id="8fb41-122">– Unseren gesamten XAML-Code zum Erstellen der Benutzeroberfläche für InkCanvas, Schaltflächen und Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="8fb41-122">- All of our XAML code to create the UI for the InkCanvas, buttons, and labels.</span></span>
- `MainPage.xaml.cs` <span data-ttu-id="8fb41-123">– Informationen zum Speicherort des Anwendungscodes</span><span class="sxs-lookup"><span data-stu-id="8fb41-123">- Where our application code lives.</span></span>
- `Helper.cs` <span data-ttu-id="8fb41-124">– Hilfsprogramm-Routinen zum Zuschneiden und Konvertieren von Abbildformaten</span><span class="sxs-lookup"><span data-stu-id="8fb41-124">- Helper routines to crop and convert image formats.</span></span>

![Visual Studio-Projektmappen-Explorer mit Projektdateien](images/get-started1.png)

## <a name="3-build-and-run-project"></a><span data-ttu-id="8fb41-126">3. Erstellen und Ausführen des Projekts</span><span class="sxs-lookup"><span data-stu-id="8fb41-126">3. Build and run project</span></span>

<span data-ttu-id="8fb41-127">Ändern Sie in der Visual Studio-Symbolleiste die Projektmappen-Plattform von "ARM" in "x64", um das Projekt auf dem lokalen Computer auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-127">In the Visual Studio toolbar, change the Solution Platform from "ARM" to "x64" to run the project on your local machine.</span></span>

<span data-ttu-id="8fb41-128">Klicken Sie zum Ausführen des Projekts auf der Symbolleiste auf die Schaltfläche **Debugging starten**, oder drücken Sie F5.</span><span class="sxs-lookup"><span data-stu-id="8fb41-128">To run the project, click the **Start Debugging** button on the toolbar, or press F5.</span></span> <span data-ttu-id="8fb41-129">Die Anwendung sollte ein InkCanvas-Steuerelement, in das Benutzer eine Ziffer schreiben können, die Schaltfläche "Erkennen" zum Interpretieren der Zahl, ein leeres Bezeichnungsfeld, in dem die übersetzten Ziffer als Text angezeigt wird, und die Schaltfläche "Ziffer deaktivieren" zum Löschen des InkCanvas-Steuerelements anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-129">The application should show an InkCanvas where users can write a digit, a "Recognize" button to interpret the number, an empty label field where the interpreted digit will be displayed as text, and a "Clear Digit" button to clear the InkCanvas.</span></span>

![App-Screenshot](images/get-started2.png)

<span data-ttu-id="8fb41-131">**Hinweis**: Wenn Sie einen Build höher als 17110 heruntergeladen haben, müssen Sie möglicherweise die Zielversion der Bereitstellung des Projekts ändern.</span><span class="sxs-lookup"><span data-stu-id="8fb41-131">**Note**: If you downloaded a Build higher than 17110, then you might need to change the project's deployment target version.</span></span> <span data-ttu-id="8fb41-132">Wechseln Sie unter der Projektmappe zu **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="8fb41-132">Under the project solution, go to **Properties**.</span></span> <span data-ttu-id="8fb41-133">Legen Sie auf der Registerkarte „Anwendung“ die Zielversion entsprechend dem Betriebssystem und SDK fest.</span><span class="sxs-lookup"><span data-stu-id="8fb41-133">In the Application tab, set the target version to match your OS and SDK.</span></span>

## <a name="4-download-a-model"></a><span data-ttu-id="8fb41-134">4. Herunterladen eines Modells</span><span class="sxs-lookup"><span data-stu-id="8fb41-134">4. Download a model</span></span>

<span data-ttu-id="8fb41-135">Als Nächstes rufen wir ein Machine Learning-Modell ab, um es unserer App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-135">Next, let's get a machine learning model to add to our app.</span></span> <span data-ttu-id="8fb41-136">In diesem Lernprogramm verwenden wir ein bereits trainiertes **MNIST-Modell**, das mit dem [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) trainiert und [in das ONNX Format exportiert](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb) wurde.</span><span class="sxs-lookup"><span data-stu-id="8fb41-136">For this tutorial, we'll use a pre-trained **MNIST model** that was trained with the [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) and [exported to ONNX format](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb).</span></span>

<span data-ttu-id="8fb41-137">Wenn Sie das Beispiel „MNIST_GetStarted“ von GitHub verwenden, wurde das MNIST-Modell dem Ordner "Assets" bereits hinzugefügt, und Sie müssen es der Anwendung als vorhandenes Element hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-137">If you are using the MNIST_GetStarted sample from GitHub, the MNIST model has already been included in your Assets folder, and you will need to add it to your application as an existing item.</span></span> <span data-ttu-id="8fb41-138">Sie können das bereits trainierte Modell auch aus [ONNX Modell Zoo](https://github.com/onnx/models) auf GitHub herunterladen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-138">You can also download the pre-trained model from the [ONNX Model Zoo](https://github.com/onnx/models) on GitHub.</span></span>

<span data-ttu-id="8fb41-139">Falls Sie ein eigenes Modell trainieren möchten, können Sie dieses [Lernprogramm](train-ai-model.md) absolvieren, mit dem wir dieses MNIST-Modell trainiert haben.</span><span class="sxs-lookup"><span data-stu-id="8fb41-139">If you're interested in training your own model, you can follow this [tutorial](train-ai-model.md) that we used to train this MNIST model.</span></span>

## <a name="5-add-the-model"></a><span data-ttu-id="8fb41-140">5. Hinzufügen des Modells</span><span class="sxs-lookup"><span data-stu-id="8fb41-140">5. Add the model</span></span>

<span data-ttu-id="8fb41-141">Nachdem Sie das MNIST-Modell heruntergeladen haben, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Ordner "Assets", und wählen Sie **Hinzufügen** > **Vorhandenes Element** aus.</span><span class="sxs-lookup"><span data-stu-id="8fb41-141">After downloading the MNIST model, right click on the Assets folder in the Solution Explorer, and select "**Add** > **Existing Item**".</span></span> <span data-ttu-id="8fb41-142">Zeigen Sie mit der Dateiauswahl auf den Speicherort des ONNX-Modells, und klicken Sie auf „Hinzufügen“.</span><span class="sxs-lookup"><span data-stu-id="8fb41-142">Point the file picker to the location of your ONNX model, and click add.</span></span> 

<span data-ttu-id="8fb41-143">Das Projekt sollte nun zwei neue Dateien haben:</span><span class="sxs-lookup"><span data-stu-id="8fb41-143">The project should now have two new files:</span></span>

- `MNIST.onnx` <span data-ttu-id="8fb41-144">– Ihr trainiertes Modell</span><span class="sxs-lookup"><span data-stu-id="8fb41-144">- your trained model.</span></span>
- `MNIST.cs` <span data-ttu-id="8fb41-145">– den von Windows ML generierten Code</span><span class="sxs-lookup"><span data-stu-id="8fb41-145">- the Windows ML generated code.</span></span>

![Projektmappen-Explorer mit neuen Dateien](images/get-started3.png)

<span data-ttu-id="8fb41-147">Um sicherzustellen, dass das Modell beim Kompilieren der Anwendung erstellt wird, klicken Sie mit der rechten Maustaste auf die `mnist.onnx`-Datei, und wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="8fb41-147">To make sure the model builds when we compile our application, right click on the `mnist.onnx` file, and select **Properties**.</span></span> <span data-ttu-id="8fb41-148">Für **Buildvorgang** wählen Sie **Inhalt**.</span><span class="sxs-lookup"><span data-stu-id="8fb41-148">For **Build Action**, select **Content**.</span></span>

<span data-ttu-id="8fb41-149">Betrachten wir nun den neu generierten Code in der `MNIST.cs`-Datei.</span><span class="sxs-lookup"><span data-stu-id="8fb41-149">Now, let's take a look at the newly generated code in the `MNIST.cs` file.</span></span> <span data-ttu-id="8fb41-150">Es gibt drei Klassen:</span><span class="sxs-lookup"><span data-stu-id="8fb41-150">We have three classes:</span></span>

- <span data-ttu-id="8fb41-151">**MNISTModel** erstellt die Modelldarstellung, bindet die spezifischen Eingaben und Ausgaben an das Modell und wertet das Modell asynchron aus.</span><span class="sxs-lookup"><span data-stu-id="8fb41-151">**MNISTModel** creates the machine learning model representation, binds the specific inputs and outputs to model, and evaluates the model asynchronously.</span></span> 
- <span data-ttu-id="8fb41-152">**MNISTModelInput** initialisiert die Eingabetypen, die das Modell erwartet.</span><span class="sxs-lookup"><span data-stu-id="8fb41-152">**MNISTModelInput** initializes the input types that the model expects.</span></span> <span data-ttu-id="8fb41-153">In diesem Fall erwartet die Eingabe einen VideoFrame.</span><span class="sxs-lookup"><span data-stu-id="8fb41-153">In this case, the input expects a VideoFrame.</span></span>
- <span data-ttu-id="8fb41-154">**MNISTModelOutput** initialisiert die Typen, die das Modell ausgibt.</span><span class="sxs-lookup"><span data-stu-id="8fb41-154">**MNISTModelOutput** initializes the types that the model will output.</span></span> <span data-ttu-id="8fb41-155">In diesem Fall ergibt sich als Ausgabe eine Liste namens „classLabel” vom Typ `<long>` und ein Dictionary namens „prediction” vom Typ</span><span class="sxs-lookup"><span data-stu-id="8fb41-155">In this case, the output will be a list called "classLabel" of type `<long>` and a Dictionary called "prediction" of type</span></span> `<long, float>`

<span data-ttu-id="8fb41-156">Wir verwenden jetzt diese Klassen zum Laden, Binden und Auswerten des Modells in unserem Projekt.</span><span class="sxs-lookup"><span data-stu-id="8fb41-156">We'll now use these classes to load, bind, and evaluate the model in our project.</span></span>

## <a name="6-load-bind-and-evaluate-the-model"></a><span data-ttu-id="8fb41-157">6. Laden, Binden und Auswerten des Modells</span><span class="sxs-lookup"><span data-stu-id="8fb41-157">6. Load, bind, and evaluate the model</span></span>

<span data-ttu-id="8fb41-158">Für Windows ML-Anwendungen, verfolgen wird das folgende Muster: Laden > Binden > Auswerten.</span><span class="sxs-lookup"><span data-stu-id="8fb41-158">For Windows ML applications, the pattern we want to follow is: Load > Bind > Evaluate.</span></span>

- <span data-ttu-id="8fb41-159">Laden Sie das Machine Learning-Modell.</span><span class="sxs-lookup"><span data-stu-id="8fb41-159">Load the machine learning model.</span></span>
- <span data-ttu-id="8fb41-160">Binden Sie Ein- und Ausgaben an das Modell.</span><span class="sxs-lookup"><span data-stu-id="8fb41-160">Bind inputs and outputs to the model.</span></span>
- <span data-ttu-id="8fb41-161">Werten Sie das Modell aus, und zeigen Sie die Ergebnisse an.</span><span class="sxs-lookup"><span data-stu-id="8fb41-161">Evaluate the model and view results.</span></span>

<span data-ttu-id="8fb41-162">Wir verwenden den Benutzeroberflächencode, der in `MNIST.cs` erstellt wurde, um das Modell in unserer App zu laden, zu binden und auszuwerten.</span><span class="sxs-lookup"><span data-stu-id="8fb41-162">We'll use the interface code generated in `MNIST.cs` to load, bind, and evaluate the model in our app.</span></span>

<span data-ttu-id="8fb41-163">Lassen Sie uns zunächst das Modell sowie Ein- und Ausgaben in `MainPage.xaml.cs` instanziieren.</span><span class="sxs-lookup"><span data-stu-id="8fb41-163">First, in `MainPage.xaml.cs`, let's instantiate the model, inputs, and outputs.</span></span>

```csharp
namespace MNIST_Demo
{
    public sealed partial class MainPage : Page
    {
        private MNISTModel ModelGen = new MNISTModel();
        private MNISTModelInput ModelInput = new MNISTModelInput();
        private MNISTModelOutput ModelOutput = new MNISTModelOutput();
        ...
    }
}
```

<span data-ttu-id="8fb41-164">In LoadModel() wird das Modell geladen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-164">Then, in LoadModel(), we'll load the model.</span></span>

```csharp
private async void LoadModel()
{
    //Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/MNIST.onnx"));
    ModelGen = await MNISTModel.CreateMNISTModel(modelFile);
}
```

<span data-ttu-id="8fb41-165">Als Nächstes möchten wir unsere Ein- und Ausgaben an das Modell binden.</span><span class="sxs-lookup"><span data-stu-id="8fb41-165">Next, we want to bind our inputs and outputs to the model.</span></span> 

<span data-ttu-id="8fb41-166">In diesem Fall erwartet unser Modell eine Eingabe vom Typ VideoFrame.</span><span class="sxs-lookup"><span data-stu-id="8fb41-166">In this case, our model is expecting an input of type VideoFrame.</span></span> <span data-ttu-id="8fb41-167">Mit Hilfe unserer Hilfsfunktionen in `helper.cs` kopieren wir den Inhalt von InkCanvas, konvertieren ihn in den Typ VideoFrame und binden ihn an unser Modell.</span><span class="sxs-lookup"><span data-stu-id="8fb41-167">Using our included helper functions in `helper.cs`, we will copy the contents of the InkCanvas, convert it to type VideoFrame, and bind it to our model.</span></span>

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
     //Bind model input with contents from InkCanvas
     ModelInput.Input3 = await helper.GetHandWrittenImage(inkGrid);
}
```

<span data-ttu-id="8fb41-168">Zur Ausgabe rufen wir einfach EvaluateAsync() mit der angegebenen Eingabe auf.</span><span class="sxs-lookup"><span data-stu-id="8fb41-168">For output, we simply call EvaluateAsync() with the specified input.</span></span> <span data-ttu-id="8fb41-169">Da das Modell eine Liste von Ziffern mit einer entsprechenden Wahrscheinlichkeit zurückgibt, müssen wir die zurückgegebene Liste analysieren, um zu bestimmen, welche Ziffer die höchste Wahrscheinlichkeit hat, und diese anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-169">Since the model returns a list of digits with a corresponding probability, we need to parse the returned list to determine which digit had the highest probability and display that one.</span></span>

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    //Bind model input with contents from InkCanvas
    ModelInput.Input3 = await helper.GetHandWrittenImage(inkGrid);
    
    //Evaluate the model
    ModelOutput = await ModelGen.EvaluateAsync(ModelInput);
            
    //Iterate through evaluation output to determine highest probability digit
    float maxProb = 0;
    int maxIndex = 0;
    for (int i = 0; i < 10; i++)
    {
        if (ModelOutput.Plus214_Output_0[i] > maxProb)
        {
            maxIndex = i;
            maxProb = ModelOutput.Plus214_Output_0[i];
        }
    }
    numberLabel.Text = maxIndex.ToString();
}
```

<span data-ttu-id="8fb41-170">Schließlich müssen wir InkCanvas löschen, damit Benutzer eine andere Nummer ziehen können.</span><span class="sxs-lookup"><span data-stu-id="8fb41-170">Finally, we'll want to clear out the InkCanvas to allow users to draw another number.</span></span>

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="7-launch-the-app"></a><span data-ttu-id="8fb41-171">7. Starten der App</span><span class="sxs-lookup"><span data-stu-id="8fb41-171">7. Launch the app</span></span>

<span data-ttu-id="8fb41-172">Sobald wir die App erstellt und gestartet haben, können wir eine auf InkCanvas gezeichnete Zahl erkennen.</span><span class="sxs-lookup"><span data-stu-id="8fb41-172">Once we build and launch the app, we'll be able to recognize a number drawn on the InkCanvas.</span></span>

![komplette App](images/get-started4.png)

## <a name="8-next-steps"></a><span data-ttu-id="8fb41-174">8. Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="8fb41-174">8. Next steps</span></span>

<span data-ttu-id="8fb41-175">Das war's – Sie haben Ihre erste Windows ML-App erstellt!</span><span class="sxs-lookup"><span data-stu-id="8fb41-175">That's it - you've made your first Windows ML app!</span></span> <span data-ttu-id="8fb41-176">Weitere Beispiele zur Verwendung von Windows ML finden Sie unter [Beispiel-Apps](samples.md).</span><span class="sxs-lookup"><span data-stu-id="8fb41-176">For more samples that demonstrate how to use Windows ML, check out [Sample apps](samples.md).</span></span>