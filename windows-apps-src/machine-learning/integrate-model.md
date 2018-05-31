---
author: serenaz
title: Integrieren eines Modells in Ihre App mit Windows ML
description: Integrieren Sie ein Modell in Ihre App nach dem Muster „Laden, Binden und Auswerten“.
ms.author: sezhen
ms.date: 03/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Winml, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 87454c46a08b80b8a315ede1d2e6a1f6cda909df
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1815475"
---
# <a name="integrate-a-model-into-your-app-with-windows-ml"></a><span data-ttu-id="438e1-104">Integrieren eines Modells in Ihre App mit Windows ML</span><span class="sxs-lookup"><span data-stu-id="438e1-104">Integrate a model into your app with Windows ML</span></span>

<span data-ttu-id="438e1-105">Windows ML [automatische Code-Generierung](overview.md#automatic-interface-code-generation) erstellt eine Schnittstelle, die [Windows ML-APIs](/uwp/api/windows.ai.machinelearning.preview) automatisch erstellt, sodass Sie einfach mit dem Modell interagieren können.</span><span class="sxs-lookup"><span data-stu-id="438e1-105">Windows ML's [automatic code generation](overview.md#automatic-interface-code-generation) creates an interface that calls the [Windows ML APIs](/uwp/api/windows.ai.machinelearning.preview) for you, allowing you to easily interact with your model.</span></span> <span data-ttu-id="438e1-106">Mithilfe der generierten Wrapper-Klassen der Schnittstelle können Sie dem Muster zum Laden, Binden und Auswerten folgen, um Ihr ML-Modell in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="438e1-106">Using the interface's generated wrapper classes, you'll follow the load, bind, and evaluate pattern to integrate your ML model into your app.</span></span>

![Laden, Binden, Auswerten](images/load-bind-evaluate.png)

<span data-ttu-id="438e1-108">In diesem Artikel verwenden wir das MNIST-Modell [Erste Schritte](get-started.md), um das Laden, Binden und Auswerten eines Modells in Ihrer App zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="438e1-108">In this article, we'll use the MNIST model from [Get Started](get-started.md) to demonstrate how to load, bind, and evaluate a model in your app.</span></span>

## <a name="add-the-model"></a><span data-ttu-id="438e1-109">Hinzufügen des Modells</span><span class="sxs-lookup"><span data-stu-id="438e1-109">Add the model</span></span>

<span data-ttu-id="438e1-110">Zunächst müssen Sie Ihr ONNX-Modell den Ressourcen Ihres Visual Studio-Projekts hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="438e1-110">First, you'll need to add your ONNX model to your Visual Studio project's Assets.</span></span> <span data-ttu-id="438e1-111">Wenn Sie eine UWP-App mit [Visual Studio (Version 15.7 – Preview 1)](https://www.visualstudio.com/vs/preview/) erstellen, generiert Visual Studio die Wrapper-Klassen automatisch in einer neuen Datei.</span><span class="sxs-lookup"><span data-stu-id="438e1-111">If you're building a UWP app with [Visual Studio (version 15.7 - Preview 1)](https://www.visualstudio.com/vs/preview/), then Visual Studio will automatically generate the wrapper classes in a new file.</span></span> <span data-ttu-id="438e1-112">Für andere Workflows müssen mit das [MLGEN](overview.md#automatic-interface-code-generation)-Tool zum Generieren von Wrapper-Klassen verwenden.</span><span class="sxs-lookup"><span data-stu-id="438e1-112">For other workflows, you'll need to use the [mlgen](overview.md#automatic-interface-code-generation) tool to generate wrapper classes.</span></span>

<span data-ttu-id="438e1-113">Nachfolgend finden Sie die Wrapper-Klassen, die von Windows ML für das MNIST-Modell generiert werden.</span><span class="sxs-lookup"><span data-stu-id="438e1-113">Below are the Windows ML generated wrapper classes for the MNIST model.</span></span> <span data-ttu-id="438e1-114">Im verbleibenden Teil dieses Artikels wird erläutert, wie diese Klassen in Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="438e1-114">We'll use the remainder of this article to explain how to use these classes in your app.</span></span>

```csharp
public sealed class MNISTModelInput
{
    public VideoFrame Input3 { get; set; }
}

public sealed class MNISTModelOutput
{
    public IList<float> Plus214_Output_0 { get; set; }
    public MNISTModelOutput()
    {
        this.Plus214_Output_0 = new List<float>();
    }
}

public sealed class MNISTModel
{
    private LearningModelPreview learningModel;
    public static async Task<MNISTModel> CreateMNISTModel(StorageFile file)
    {
        LearningModelPreview learningModel = await LearningModelPreview.LoadModelFromStorageFileAsync(file);
        MNISTModel model = new MNISTModel();
        model.learningModel = learningModel;
        return model;
    }
    public async Task<MNISTModelOutput> EvaluateAsync(MNISTModelInput input) {
        MNISTModelOutput output = new MNISTModelOutput();
        LearningModelBindingPreview binding = new LearningModelBindingPreview(learningModel);
        binding.Bind("Input3", input.Input3);
        binding.Bind("Plus214_Output_0", output.Plus214_Output_0);
        LearningModelEvaluationResultPreview evalResult = await learningModel.EvaluateAsync(binding, string.Empty);
        return output;
    }
}
```

<span data-ttu-id="438e1-115">**Hinweis**: Um sicherzustellen, dass Ihr Modell beim Kompilieren Ihrer Anwendung erstellt wird, klicken Sie mit der rechten Maustaste auf die `.onnx`-Datei, und wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="438e1-115">**Note**: To make sure your model builds when you compile your application, right click on the `.onnx` file, and select **Properties**.</span></span> <span data-ttu-id="438e1-116">Für **Buildvorgang** wählen Sie **Inhalt**.</span><span class="sxs-lookup"><span data-stu-id="438e1-116">For **Build Action**, select **Content**.</span></span>

## <a name="load"></a><span data-ttu-id="438e1-117">Laden</span><span class="sxs-lookup"><span data-stu-id="438e1-117">Load</span></span>

<span data-ttu-id="438e1-118">Sobald Sie über die generierten Wrapper-Klassen verfügen, laden Sie das Modell in Ihre App.</span><span class="sxs-lookup"><span data-stu-id="438e1-118">Once you have the generated wrapper classes, you'll load the model in your app.</span></span>

<span data-ttu-id="438e1-119">Die MNISTModel-Klasse stellt das MNIST-Modell dar, und zum Laden des Modells rufen wir die CreateMNISTModel-Methode auf, indem die ONNX-Datei als Parameter übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="438e1-119">The MNISTModel class represents the MNIST model, and to load the model, we call the CreateMNISTModel method, passing in the ONNX file as the parameter.</span></span>

```csharp
// Load the model
StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/MNIST.onnx"));
MNISTModel model = MNISTModel.CreateMNISTModel(modelFile);
```

## <a name="bind"></a><span data-ttu-id="438e1-120">Bindung</span><span class="sxs-lookup"><span data-stu-id="438e1-120">Bind</span></span>

<span data-ttu-id="438e1-121">Der generierte Code enthält auch die Eingabe- und Ausgabe-Wrapper-Klassen.</span><span class="sxs-lookup"><span data-stu-id="438e1-121">The generated code also includes Input and Output wrapper classes.</span></span> <span data-ttu-id="438e1-122">Die Eingabe-Klasse stellt die erwarteten Eingaben und die Ausgabe-Klasse die erwarteten Ausgaben des Modells dar.</span><span class="sxs-lookup"><span data-stu-id="438e1-122">The Input class represents the model's expected inputs, and the Output class represents the model's expected outputs.</span></span>

<span data-ttu-id="438e1-123">Rufen Sie zum Initialisieren des Eingabeobjekts des Modells den Eingabeklassenkonstruktor auf, indem Sie Ihre Anwendungsdaten übergeben und sicherstellen, dass Ihre Eingabedaten dem Eingabetyp entsprechen, den Ihr Modell erwartet.</span><span class="sxs-lookup"><span data-stu-id="438e1-123">To initialize the model's input object, call the Input class constructor, passing in your application data, and make sure that your input data matches the input type that your model expects.</span></span> <span data-ttu-id="438e1-124">Die MNISTModelInput-Klasse erwartet einen VideoFrame, daher verwenden wir eine Hilfsmethode, um einen VideoFrame für die Eingabe abzurufen.</span><span class="sxs-lookup"><span data-stu-id="438e1-124">The MNISTModelInput class expects a VideoFrame, so we use a helper method to get a VideoFrame for the input.</span></span>

```csharp
//Bind the input data to the model
MNISTModelInputs ModelInput = new MNISTModelInputs();
ModelInput.Input3 = await helper.GetHandWrittenImage(inkGrid);
```

<span data-ttu-id="438e1-125">Ausgabeobjekte werden mit *Null*-Werten initialisiert und nach dem ersten Schritt zum Auswerten mit den Ergebnissen des Modells aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="438e1-125">Output objects are initialized to *Null* values and will be updated with the model's results after the next step, Evaluate.</span></span>

## <a name="evaluate"></a><span data-ttu-id="438e1-126">Auswerten</span><span class="sxs-lookup"><span data-stu-id="438e1-126">Evaluate</span></span>

<span data-ttu-id="438e1-127">Nachdem Ihre Eingaben initialisiert wurden, rufen Sie die EvaluateAsync-Methode des Modells auf, um Ihr Modell anhand der Eingabedaten auszuwerten.</span><span class="sxs-lookup"><span data-stu-id="438e1-127">Once your inputs are initialized, call the model's EvaluateAsync method to evaluate your model on the input data.</span></span> <span data-ttu-id="438e1-128">EvaluateAsync bindet Ihre Ein- und Ausgaben an das Modellobjekt und wertet das Modell anhand der Eingaben aus.</span><span class="sxs-lookup"><span data-stu-id="438e1-128">EvaluateAsync binds your inputs and outputs to the model object and evaluates the model on the inputs.</span></span>

```csharp
// Evaluate the model
MNISTModelOuput ModelOutput = model.EvaluateAsync(ModelInput);
```

<span data-ttu-id="438e1-129">Nach der Auswertung enthält die Ausgabe die Ergebnisse des Modells, die Sie jetzt anzeigen und analysieren können.</span><span class="sxs-lookup"><span data-stu-id="438e1-129">After evaluation, your output contains the model's results, which you now can view and analyze.</span></span> <span data-ttu-id="438e1-130">Da das MNIST-Modell eine Liste der Wahrscheinlichkeiten ausgibt, durchlaufen wir die Liste, um die Ziffer mit der höchsten Wahrscheinlichkeit zu suchen und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="438e1-130">Since the MNIST model outputs a list of probabilities, we iterate through the list to find and display the digit with the highest probability.</span></span>

```csharp
 //Iterate through output to determine highest probability digit
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
```

## <a name="using-the-windows-ml-apis-directly"></a><span data-ttu-id="438e1-131">Direkte Verwendung von Windows ML-APIs</span><span class="sxs-lookup"><span data-stu-id="438e1-131">Using the Windows ML APIs directly</span></span>

<span data-ttu-id="438e1-132">Obwohl der automatische Codegenerator von Windows ML eine bequeme Benutzeroberfläche für die Interaktion mit dem Modell bietet, müssen Sie die Wrapper-Klassen nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="438e1-132">Although Windows ML's automatic code generator provides a convenient interface to interact with your model, you don't have to use the wrapper classes.</span></span> <span data-ttu-id="438e1-133">Stattdessen können Sie die Windows ML-APIs direkt in Ihrer App aufrufen.</span><span class="sxs-lookup"><span data-stu-id="438e1-133">Instead, you can call the Windows ML APIs directly in your app.</span></span>
<span data-ttu-id="438e1-134">In diesem Fall folgen Sie dem gleichen Muster: Laden Sie das Modell, binden Sie die Ein- und Ausgaben, und werten Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="438e1-134">If you choose to do so, you'll follow the same pattern: load your model, bind your inputs and outputs, and evaluate.</span></span>

<span data-ttu-id="438e1-135">Weitere Informationen zur Verwendung der APIs finden Sie in der [Windows ML-API-Referenz](/uwp/api/windows.ai.machinelearning.preview).</span><span class="sxs-lookup"><span data-stu-id="438e1-135">For more information on using the APIs, see the [Windows ML API reference](/uwp/api/windows.ai.machinelearning.preview).</span></span>
