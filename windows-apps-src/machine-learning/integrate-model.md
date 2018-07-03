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
ms.openlocfilehash: 8631c07b45a8642a1de700e424d3ca4f147456fc
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1842577"
---
# <a name="integrate-a-model-into-your-app-with-windows-ml"></a>Integrieren eines Modells in Ihre App mit Windows ML

Windows ML [automatische Code-Generierung](overview.md#automatic-interface-code-generation) erstellt eine Schnittstelle, die [Windows ML-APIs](/uwp/api/windows.ai.machinelearning.preview) automatisch erstellt, sodass Sie einfach mit dem Modell interagieren können. Mithilfe der generierten Wrapper-Klassen der Schnittstelle können Sie dem Muster zum Laden, Binden und Auswerten folgen, um Ihr ML-Modell in Ihre App zu integrieren.

![Laden, Binden, Auswerten](images/load-bind-evaluate.png)

In diesem Artikel verwenden wir das MNIST-Modell [Erste Schritte](get-started.md), um das Laden, Binden und Auswerten eines Modells in Ihrer App zu veranschaulichen.

## <a name="add-the-model"></a>Hinzufügen des Modells

Zunächst müssen Sie Ihr ONNX-Modell den Ressourcen Ihres Visual Studio-Projekts hinzufügen. Wenn Sie eine UWP-App mit [Visual Studio (Version 15.7 – Preview 1)](https://www.visualstudio.com/vs/preview/) erstellen, generiert Visual Studio die Wrapper-Klassen automatisch in einer neuen Datei. Für andere Workflows müssen mit das [MLGEN](overview.md#automatic-interface-code-generation)-Tool zum Generieren von Wrapper-Klassen verwenden.

Nachfolgend finden Sie die Wrapper-Klassen, die von Windows ML für das MNIST-Modell generiert werden. Im verbleibenden Teil dieses Artikels wird erläutert, wie diese Klassen in Ihrer App verwendet werden.

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

**Hinweis**: Um sicherzustellen, dass Ihr Modell beim Kompilieren Ihrer Anwendung erstellt wird, klicken Sie mit der rechten Maustaste auf die `.onnx`-Datei, und wählen Sie **Eigenschaften** aus. Für **Buildvorgang** wählen Sie **Inhalt**.

## <a name="load"></a>Laden

Sobald Sie über die generierten Wrapper-Klassen verfügen, laden Sie das Modell in Ihre App.

Die MNISTModel-Klasse stellt das MNIST-Modell dar, und zum Laden des Modells rufen wir die CreateMNISTModel-Methode auf, indem die ONNX-Datei als Parameter übergeben wird.

```csharp
// Load the model
StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/MNIST.onnx"));
MNISTModel model = MNISTModel.CreateMNISTModel(modelFile);
```

## <a name="bind"></a>Bindung

Der generierte Code enthält auch die Eingabe- und Ausgabe-Wrapper-Klassen. Die Eingabe-Klasse stellt die erwarteten Eingaben und die Ausgabe-Klasse die erwarteten Ausgaben des Modells dar.

Rufen Sie zum Initialisieren des Eingabeobjekts des Modells den Eingabeklassenkonstruktor auf, indem Sie Ihre Anwendungsdaten übergeben und sicherstellen, dass Ihre Eingabedaten dem Eingabetyp entsprechen, den Ihr Modell erwartet. Die MNISTModelInput-Klasse erwartet einen VideoFrame, daher verwenden wir eine Hilfsmethode, um einen VideoFrame für die Eingabe abzurufen.

```csharp
//Bind the input data to the model
MNISTModelInputs ModelInput = new MNISTModelInputs();
ModelInput.Input3 = await helper.GetHandWrittenImage(inkGrid);
```

Ausgabeobjekte werden mit *Null*-Werten initialisiert und nach dem ersten Schritt zum Auswerten mit den Ergebnissen des Modells aktualisiert.

## <a name="evaluate"></a>Auswerten

Nachdem Ihre Eingaben initialisiert wurden, rufen Sie die EvaluateAsync-Methode des Modells auf, um Ihr Modell anhand der Eingabedaten auszuwerten. EvaluateAsync bindet Ihre Ein- und Ausgaben an das Modellobjekt und wertet das Modell anhand der Eingaben aus.

```csharp
// Evaluate the model
MNISTModelOuput ModelOutput = model.EvaluateAsync(ModelInput);
```

Nach der Auswertung enthält die Ausgabe die Ergebnisse des Modells, die Sie jetzt anzeigen und analysieren können. Da das MNIST-Modell eine Liste der Wahrscheinlichkeiten ausgibt, durchlaufen wir die Liste, um die Ziffer mit der höchsten Wahrscheinlichkeit zu suchen und anzuzeigen.

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

## <a name="using-the-windows-ml-apis-directly"></a>Direkte Verwendung von Windows ML-APIs

Obwohl der automatische Codegenerator von Windows ML eine bequeme Benutzeroberfläche für die Interaktion mit dem Modell bietet, müssen Sie die Wrapper-Klassen nicht verwenden. Stattdessen können Sie die Windows ML-APIs direkt in Ihrer App aufrufen.
In diesem Fall folgen Sie dem gleichen Muster: Laden Sie das Modell, binden Sie die Ein- und Ausgaben, und werten Sie sie aus.

Weitere Informationen zur Verwendung der APIs finden Sie in der [Windows ML-API-Referenz](/uwp/api/windows.ai.machinelearning.preview).
