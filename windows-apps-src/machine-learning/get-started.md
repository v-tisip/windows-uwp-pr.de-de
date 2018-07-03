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
ms.openlocfilehash: eec2ada8e3aadad134381a93bca2652133912b2e
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1843623"
---
# <a name="get-started-with-windows-ml"></a><span data-ttu-id="0e962-104">Erste Schritte mit Windows ML</span><span class="sxs-lookup"><span data-stu-id="0e962-104">Get started with Windows ML</span></span>

<span data-ttu-id="0e962-105">In diesem Lernprogramm erstellen wir eine einfache UWP-App, die ein trainiertes Machine Learning-Modell verwendet, um ein numerisches Zeichen zu erkennen, das vom Benutzer gezeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="0e962-105">In this tutorial, we'll build a simple UWP app that uses a trained machine learning model to recognize a numeric digit drawn by the user.</span></span> <span data-ttu-id="0e962-106">Dieses Lernprogramm ist vorrangig auf das Laden und Verwenden von Windows ML in Ihrer App ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="0e962-106">This tutorial primarily focuses on how to load and use Windows ML in your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e962-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0e962-107">Prerequisites</span></span>

- <span data-ttu-id="0e962-108">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) (Biuld 17110 oder höher)</span><span class="sxs-lookup"><span data-stu-id="0e962-108">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) (Build 17110 or higher)</span></span>
- [<span data-ttu-id="0e962-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e962-109">Visual Studio</span></span>](https://developer.microsoft.com/windows/downloads)

## <a name="1-download-the-sample"></a><span data-ttu-id="0e962-110">1. Herunterladen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="0e962-110">1. Download the sample</span></span>

<span data-ttu-id="0e962-111">Zunächst müssen Sie unser [MNIST_GetStarted-Beispiel](https://github.com/Microsoft/Windows-Machine-Learning) von GitHub herunterladen.</span><span class="sxs-lookup"><span data-stu-id="0e962-111">First, you'll need to download our [MNIST_GetStarted sample](https://github.com/Microsoft/Windows-Machine-Learning) from GitHub.</span></span> <span data-ttu-id="0e962-112">Wir haben eine Vorlage mit implementierten XAML-Steuerelementen und Ereignissen bereitgestellt, die Folgendes beinhaltet:</span><span class="sxs-lookup"><span data-stu-id="0e962-112">We've provided a template with implemented XAML controls and events, including:</span></span>

- <span data-ttu-id="0e962-113">Ein [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) zum Zeichnen der Ziffer.</span><span class="sxs-lookup"><span data-stu-id="0e962-113">An [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) to draw the digit.</span></span>
- <span data-ttu-id="0e962-114">[Schaltflächen](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button) zum Interpretieren der Ziffer und zum Löschen des Zeichenbereichs.</span><span class="sxs-lookup"><span data-stu-id="0e962-114">[Buttons](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button) to interpret the digit and clear the canvas.</span></span>
- <span data-ttu-id="0e962-115">Hilfsprogramm-Routinen zum Konvertieren der InkCanvas-Ausgabe in einen [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe).</span><span class="sxs-lookup"><span data-stu-id="0e962-115">Helper routines to convert the InkCanvas output to a [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe).</span></span>

<span data-ttu-id="0e962-116">Ein vollständiges MNIST-Beispiel kann ebenfalls von GitHub heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="0e962-116">A completed MNIST sample is also available to download from GitHub.</span></span>

## <a name="2-open-project-in-visual-studio-preview"></a><span data-ttu-id="0e962-117">2. Öffnen des Projekts in Visual Studio Preview</span><span class="sxs-lookup"><span data-stu-id="0e962-117">2. Open project in Visual Studio Preview</span></span>

<span data-ttu-id="0e962-118">Starten Sie Visual Studio Preview, und öffnen Sie die MNIST-Beispielanwendung.</span><span class="sxs-lookup"><span data-stu-id="0e962-118">Launch Visual Studio Preview, and open the MNIST sample application.</span></span> <span data-ttu-id="0e962-119">(Wenn die Lösung als nicht verfügbar angezeigt wird, müssen Sie mit der rechten Maustaste klicken und "Projekt erneut laden" auswählen.)</span><span class="sxs-lookup"><span data-stu-id="0e962-119">(If the solution is shown as unavailable, you'll need to right-click and select "Reload Project.")</span></span>

<span data-ttu-id="0e962-120">Im Projektmappen-Explorer enthält das Projekt drei Haupt-Codedateien:</span><span class="sxs-lookup"><span data-stu-id="0e962-120">Inside the solution explorer, the project has three main code files:</span></span>

- `MainPage.xaml` <span data-ttu-id="0e962-121">– Unseren gesamten XAML-Code zum Erstellen der Benutzeroberfläche für InkCanvas, Schaltflächen und Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="0e962-121">- All of our XAML code to create the UI for the InkCanvas, buttons, and labels.</span></span>
- `MainPage.xaml.cs` <span data-ttu-id="0e962-122">– Informationen zum Speicherort des Anwendungscodes</span><span class="sxs-lookup"><span data-stu-id="0e962-122">- Where our application code lives.</span></span>
- `Helper.cs` <span data-ttu-id="0e962-123">– Hilfsprogramm-Routinen zum Zuschneiden und Konvertieren von Abbildformaten</span><span class="sxs-lookup"><span data-stu-id="0e962-123">- Helper routines to crop and convert image formats.</span></span>

![Visual Studio-Projektmappen-Explorer mit Projektdateien](images/get-started1.png)

## <a name="3-build-and-run-project"></a><span data-ttu-id="0e962-125">3. Erstellen und Ausführen des Projekts</span><span class="sxs-lookup"><span data-stu-id="0e962-125">3. Build and run project</span></span>

<span data-ttu-id="0e962-126">Ändern Sie in der Visual Studio-Symbolleiste die Projektmappen-Plattform von "ARM" in "x64", um das Projekt auf dem lokalen Computer auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0e962-126">In the Visual Studio toolbar, change the Solution Platform from "ARM" to "x64" to run the project on your local machine.</span></span>

<span data-ttu-id="0e962-127">Klicken Sie zum Ausführen des Projekts auf der Symbolleiste auf die Schaltfläche **Debugging starten**, oder drücken Sie F5.</span><span class="sxs-lookup"><span data-stu-id="0e962-127">To run the project, click the **Start Debugging** button on the toolbar, or press F5.</span></span> <span data-ttu-id="0e962-128">Die Anwendung sollte ein InkCanvas-Steuerelement, in das Benutzer eine Ziffer schreiben können, die Schaltfläche "Erkennen" zum Interpretieren der Zahl, ein leeres Bezeichnungsfeld, in dem die übersetzten Ziffer als Text angezeigt wird, und die Schaltfläche "Ziffer deaktivieren" zum Löschen des InkCanvas-Steuerelements anzeigen.</span><span class="sxs-lookup"><span data-stu-id="0e962-128">The application should show an InkCanvas where users can write a digit, a "Recognize" button to interpret the number, an empty label field where the interpreted digit will be displayed as text, and a "Clear Digit" button to clear the InkCanvas.</span></span>

![App-Screenshot](images/get-started2.png)

<span data-ttu-id="0e962-130">**Hinweis**: Wenn Sie einen Build höher als 17110 heruntergeladen haben, müssen Sie möglicherweise die Zielversion der Bereitstellung des Projekts ändern.</span><span class="sxs-lookup"><span data-stu-id="0e962-130">**Note**: If you downloaded a Build higher than 17110, then you might need to change the project's deployment target version.</span></span> <span data-ttu-id="0e962-131">Wechseln Sie unter der Projektmappe zu **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="0e962-131">Under the project solution, go to **Properties**.</span></span> <span data-ttu-id="0e962-132">Legen Sie auf der Registerkarte „Anwendung“ die Zielversion entsprechend dem Betriebssystem und SDK fest.</span><span class="sxs-lookup"><span data-stu-id="0e962-132">In the Application tab, set the target version to match your OS and SDK.</span></span>

## <a name="4-download-a-model"></a><span data-ttu-id="0e962-133">4. Herunterladen eines Modells</span><span class="sxs-lookup"><span data-stu-id="0e962-133">4. Download a model</span></span>

<span data-ttu-id="0e962-134">Als Nächstes rufen wir ein Machine Learning-Modell ab, um es unserer App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0e962-134">Next, let's get a machine learning model to add to our app.</span></span> <span data-ttu-id="0e962-135">In diesem Lernprogramm verwenden wir ein bereits trainiertes **MNIST-Modell**, das mit dem [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) trainiert und [in das ONNX Format exportiert](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb) wurde.</span><span class="sxs-lookup"><span data-stu-id="0e962-135">For this tutorial, we'll use a pre-trained **MNIST model** that was trained with the [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) and [exported to ONNX format](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb).</span></span>

<span data-ttu-id="0e962-136">Wenn Sie das Beispiel „MNIST_GetStarted“ von GitHub verwenden, wurde das MNIST-Modell dem Ordner "Assets" bereits hinzugefügt, und Sie müssen es der Anwendung als vorhandenes Element hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0e962-136">If you are using the MNIST_GetStarted sample from GitHub, the MNIST model has already been included in your Assets folder, and you will need to add it to your application as an existing item.</span></span> <span data-ttu-id="0e962-137">Sie können das bereits trainierte Modell auch aus [ONNX Modell Zoo](https://github.com/onnx/models) auf GitHub herunterladen.</span><span class="sxs-lookup"><span data-stu-id="0e962-137">You can also download the pre-trained model from the [ONNX Model Zoo](https://github.com/onnx/models) on GitHub.</span></span>

<span data-ttu-id="0e962-138">Falls Sie ein eigenes Modell trainieren möchten, können Sie dieses [Lernprogramm](train-ai-model.md) absolvieren, mit dem wir dieses MNIST-Modell trainiert haben.</span><span class="sxs-lookup"><span data-stu-id="0e962-138">If you're interested in training your own model, you can follow this [tutorial](train-ai-model.md) that we used to train this MNIST model.</span></span>

## <a name="5-add-the-model"></a><span data-ttu-id="0e962-139">5. Hinzufügen des Modells</span><span class="sxs-lookup"><span data-stu-id="0e962-139">5. Add the model</span></span>

<span data-ttu-id="0e962-140">Nachdem Sie das MNIST-Modell heruntergeladen haben, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Ordner "Assets", und wählen Sie **Hinzufügen** > **Vorhandenes Element** aus.</span><span class="sxs-lookup"><span data-stu-id="0e962-140">After downloading the MNIST model, right click on the Assets folder in the Solution Explorer, and select "**Add** > **Existing Item**".</span></span> <span data-ttu-id="0e962-141">Zeigen Sie mit der Dateiauswahl auf den Speicherort des ONNX-Modells, und klicken Sie auf „Hinzufügen“.</span><span class="sxs-lookup"><span data-stu-id="0e962-141">Point the file picker to the location of your ONNX model, and click add.</span></span>

<span data-ttu-id="0e962-142">Das Projekt sollte nun zwei neue Dateien haben:</span><span class="sxs-lookup"><span data-stu-id="0e962-142">The project should now have two new files:</span></span>

- `MNIST.onnx` <span data-ttu-id="0e962-143">– Ihr trainiertes Modell</span><span class="sxs-lookup"><span data-stu-id="0e962-143">- your trained model.</span></span>
- `MNIST.cs` <span data-ttu-id="0e962-144">– den von Windows ML generierten Code</span><span class="sxs-lookup"><span data-stu-id="0e962-144">- the Windows ML generated code.</span></span>

![Projektmappen-Explorer mit neuen Dateien](images/get-started3.png)

<span data-ttu-id="0e962-146">Um sicherzustellen, dass das Modell beim Kompilieren der Anwendung erstellt wird, klicken Sie mit der rechten Maustaste auf die `mnist.onnx`-Datei, und wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="0e962-146">To make sure the model builds when we compile our application, right click on the `mnist.onnx` file, and select **Properties**.</span></span> <span data-ttu-id="0e962-147">Für **Buildvorgang** wählen Sie **Inhalt**.</span><span class="sxs-lookup"><span data-stu-id="0e962-147">For **Build Action**, select **Content**.</span></span>

<span data-ttu-id="0e962-148">Betrachten wir nun den neu generierten Code in der `MNIST.cs`-Datei.</span><span class="sxs-lookup"><span data-stu-id="0e962-148">Now, let's take a look at the newly generated code in the `MNIST.cs` file.</span></span> <span data-ttu-id="0e962-149">Es gibt drei Klassen:</span><span class="sxs-lookup"><span data-stu-id="0e962-149">We have three classes:</span></span>

- <span data-ttu-id="0e962-150">**MNISTModel** erstellt die Modelldarstellung, bindet die spezifischen Eingaben und Ausgaben an das Modell und wertet das Modell asynchron aus.</span><span class="sxs-lookup"><span data-stu-id="0e962-150">**MNISTModel** creates the machine learning model representation, binds the specific inputs and outputs to model, and evaluates the model asynchronously.</span></span> 
- <span data-ttu-id="0e962-151">**MNISTModelInput** initialisiert die Eingabetypen, die das Modell erwartet.</span><span class="sxs-lookup"><span data-stu-id="0e962-151">**MNISTModelInput** initializes the input types that the model expects.</span></span> <span data-ttu-id="0e962-152">In diesem Fall erwartet die Eingabe einen VideoFrame.</span><span class="sxs-lookup"><span data-stu-id="0e962-152">In this case, the input expects a VideoFrame.</span></span>
- <span data-ttu-id="0e962-153">**MNISTModelOutput** initialisiert die Typen, die das Modell ausgibt.</span><span class="sxs-lookup"><span data-stu-id="0e962-153">**MNISTModelOutput** initializes the types that the model will output.</span></span> <span data-ttu-id="0e962-154">In diesem Fall ergibt sich als Ausgabe eine Liste namens „classLabel” vom Typ `<long>` und ein Dictionary namens „prediction” vom Typ</span><span class="sxs-lookup"><span data-stu-id="0e962-154">In this case, the output will be a list called "classLabel" of type `<long>` and a Dictionary called "prediction" of type</span></span> `<long, float>`

<span data-ttu-id="0e962-155">Wir verwenden jetzt diese Klassen zum Laden, Binden und Auswerten des Modells in unserem Projekt.</span><span class="sxs-lookup"><span data-stu-id="0e962-155">We'll now use these classes to load, bind, and evaluate the model in our project.</span></span>

## <a name="6-load-bind-and-evaluate-the-model"></a><span data-ttu-id="0e962-156">6. Laden, Binden und Auswerten des Modells</span><span class="sxs-lookup"><span data-stu-id="0e962-156">6. Load, bind, and evaluate the model</span></span>

<span data-ttu-id="0e962-157">Für Windows ML-Anwendungen, verfolgen wird das folgende Muster: Laden > Binden > Auswerten.</span><span class="sxs-lookup"><span data-stu-id="0e962-157">For Windows ML applications, the pattern we want to follow is: Load > Bind > Evaluate.</span></span>

- <span data-ttu-id="0e962-158">Laden Sie das Machine Learning-Modell.</span><span class="sxs-lookup"><span data-stu-id="0e962-158">Load the machine learning model.</span></span>
- <span data-ttu-id="0e962-159">Binden Sie Ein- und Ausgaben an das Modell.</span><span class="sxs-lookup"><span data-stu-id="0e962-159">Bind inputs and outputs to the model.</span></span>
- <span data-ttu-id="0e962-160">Werten Sie das Modell aus, und zeigen Sie die Ergebnisse an.</span><span class="sxs-lookup"><span data-stu-id="0e962-160">Evaluate the model and view results.</span></span>

<span data-ttu-id="0e962-161">Wir verwenden den Benutzeroberflächencode, der in `MNIST.cs` erstellt wurde, um das Modell in unserer App zu laden, zu binden und auszuwerten.</span><span class="sxs-lookup"><span data-stu-id="0e962-161">We'll use the interface code generated in `MNIST.cs` to load, bind, and evaluate the model in our app.</span></span>

<span data-ttu-id="0e962-162">Lassen Sie uns zunächst das Modell sowie Ein- und Ausgaben in `MainPage.xaml.cs` instanziieren.</span><span class="sxs-lookup"><span data-stu-id="0e962-162">First, in `MainPage.xaml.cs`, let's instantiate the model, inputs, and outputs.</span></span>

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

<span data-ttu-id="0e962-163">In LoadModel() wird das Modell geladen.</span><span class="sxs-lookup"><span data-stu-id="0e962-163">Then, in LoadModel(), we'll load the model.</span></span>

```csharp
private async void LoadModel()
{
    //Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/MNIST.onnx"));
    ModelGen = await MNISTModel.CreateMNISTModel(modelFile);
}
```

<span data-ttu-id="0e962-164">Als Nächstes möchten wir unsere Ein- und Ausgaben an das Modell binden.</span><span class="sxs-lookup"><span data-stu-id="0e962-164">Next, we want to bind our inputs and outputs to the model.</span></span> 

<span data-ttu-id="0e962-165">In diesem Fall erwartet unser Modell eine Eingabe vom Typ VideoFrame.</span><span class="sxs-lookup"><span data-stu-id="0e962-165">In this case, our model is expecting an input of type VideoFrame.</span></span> <span data-ttu-id="0e962-166">Mit Hilfe unserer Hilfsfunktionen in `helper.cs` kopieren wir den Inhalt von InkCanvas, konvertieren ihn in den Typ VideoFrame und binden ihn an unser Modell.</span><span class="sxs-lookup"><span data-stu-id="0e962-166">Using our included helper functions in `helper.cs`, we will copy the contents of the InkCanvas, convert it to type VideoFrame, and bind it to our model.</span></span>

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
     //Bind model input with contents from InkCanvas
     ModelInput.Input3 = await helper.GetHandWrittenImage(inkGrid);
}
```

<span data-ttu-id="0e962-167">Zur Ausgabe rufen wir einfach EvaluateAsync() mit der angegebenen Eingabe auf.</span><span class="sxs-lookup"><span data-stu-id="0e962-167">For output, we simply call EvaluateAsync() with the specified input.</span></span> <span data-ttu-id="0e962-168">Da das Modell eine Liste von Ziffern mit einer entsprechenden Wahrscheinlichkeit zurückgibt, müssen wir die zurückgegebene Liste analysieren, um zu bestimmen, welche Ziffer die höchste Wahrscheinlichkeit hat, und diese anzeigen.</span><span class="sxs-lookup"><span data-stu-id="0e962-168">Since the model returns a list of digits with a corresponding probability, we need to parse the returned list to determine which digit had the highest probability and display that one.</span></span>

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

<span data-ttu-id="0e962-169">Schließlich müssen wir InkCanvas löschen, damit Benutzer eine andere Nummer ziehen können.</span><span class="sxs-lookup"><span data-stu-id="0e962-169">Finally, we'll want to clear out the InkCanvas to allow users to draw another number.</span></span>

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="7-launch-the-app"></a><span data-ttu-id="0e962-170">7. Starten der App</span><span class="sxs-lookup"><span data-stu-id="0e962-170">7. Launch the app</span></span>

<span data-ttu-id="0e962-171">Sobald wir die App erstellt und gestartet haben, können wir eine auf InkCanvas gezeichnete Zahl erkennen.</span><span class="sxs-lookup"><span data-stu-id="0e962-171">Once we build and launch the app, we'll be able to recognize a number drawn on the InkCanvas.</span></span>

![komplette App](images/get-started4.png)

## <a name="8-next-steps"></a><span data-ttu-id="0e962-173">8. Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="0e962-173">8. Next steps</span></span>

<span data-ttu-id="0e962-174">Das war's – Sie haben Ihre erste Windows ML-App erstellt!</span><span class="sxs-lookup"><span data-stu-id="0e962-174">That's it - you've made your first Windows ML app!</span></span> <span data-ttu-id="0e962-175">Weitere Beispiele zur Verwendung von Windows ML finden Sie unter [Beispiel-Apps](samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e962-175">For more samples that demonstrate how to use Windows ML, check out [Sample apps](samples.md).</span></span>