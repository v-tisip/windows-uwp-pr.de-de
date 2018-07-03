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
# <a name="get-started-with-windows-ml"></a>Erste Schritte mit Windows ML

In diesem Lernprogramm erstellen wir eine einfache UWP-App, die ein trainiertes Machine Learning-Modell verwendet, um ein numerisches Zeichen zu erkennen, das vom Benutzer gezeichnet wurde. Dieses Lernprogramm ist vorrangig auf das Laden und Verwenden von Windows ML in Ihrer App ausgerichtet.

## <a name="prerequisites"></a>Voraussetzungen

- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) (Biuld 17110 oder höher)
- [Visual Studio](https://developer.microsoft.com/windows/downloads)

## <a name="1-download-the-sample"></a>1. Herunterladen des Beispiels

Zunächst müssen Sie unser [MNIST_GetStarted-Beispiel](https://github.com/Microsoft/Windows-Machine-Learning) von GitHub herunterladen. Wir haben eine Vorlage mit implementierten XAML-Steuerelementen und Ereignissen bereitgestellt, die Folgendes beinhaltet:

- Ein [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) zum Zeichnen der Ziffer.
- [Schaltflächen](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button) zum Interpretieren der Ziffer und zum Löschen des Zeichenbereichs.
- Hilfsprogramm-Routinen zum Konvertieren der InkCanvas-Ausgabe in einen [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe).

Ein vollständiges MNIST-Beispiel kann ebenfalls von GitHub heruntergeladen werden.

## <a name="2-open-project-in-visual-studio-preview"></a>2. Öffnen des Projekts in Visual Studio Preview

Starten Sie Visual Studio Preview, und öffnen Sie die MNIST-Beispielanwendung. (Wenn die Lösung als nicht verfügbar angezeigt wird, müssen Sie mit der rechten Maustaste klicken und "Projekt erneut laden" auswählen.)

Im Projektmappen-Explorer enthält das Projekt drei Haupt-Codedateien:

- `MainPage.xaml` – Unseren gesamten XAML-Code zum Erstellen der Benutzeroberfläche für InkCanvas, Schaltflächen und Bezeichnungen
- `MainPage.xaml.cs` – Informationen zum Speicherort des Anwendungscodes
- `Helper.cs` – Hilfsprogramm-Routinen zum Zuschneiden und Konvertieren von Abbildformaten

![Visual Studio-Projektmappen-Explorer mit Projektdateien](images/get-started1.png)

## <a name="3-build-and-run-project"></a>3. Erstellen und Ausführen des Projekts

Ändern Sie in der Visual Studio-Symbolleiste die Projektmappen-Plattform von "ARM" in "x64", um das Projekt auf dem lokalen Computer auszuführen.

Klicken Sie zum Ausführen des Projekts auf der Symbolleiste auf die Schaltfläche **Debugging starten**, oder drücken Sie F5. Die Anwendung sollte ein InkCanvas-Steuerelement, in das Benutzer eine Ziffer schreiben können, die Schaltfläche "Erkennen" zum Interpretieren der Zahl, ein leeres Bezeichnungsfeld, in dem die übersetzten Ziffer als Text angezeigt wird, und die Schaltfläche "Ziffer deaktivieren" zum Löschen des InkCanvas-Steuerelements anzeigen.

![App-Screenshot](images/get-started2.png)

**Hinweis**: Wenn Sie einen Build höher als 17110 heruntergeladen haben, müssen Sie möglicherweise die Zielversion der Bereitstellung des Projekts ändern. Wechseln Sie unter der Projektmappe zu **Eigenschaften**. Legen Sie auf der Registerkarte „Anwendung“ die Zielversion entsprechend dem Betriebssystem und SDK fest.

## <a name="4-download-a-model"></a>4. Herunterladen eines Modells

Als Nächstes rufen wir ein Machine Learning-Modell ab, um es unserer App hinzuzufügen. In diesem Lernprogramm verwenden wir ein bereits trainiertes **MNIST-Modell**, das mit dem [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) trainiert und [in das ONNX Format exportiert](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb) wurde.

Wenn Sie das Beispiel „MNIST_GetStarted“ von GitHub verwenden, wurde das MNIST-Modell dem Ordner "Assets" bereits hinzugefügt, und Sie müssen es der Anwendung als vorhandenes Element hinzufügen. Sie können das bereits trainierte Modell auch aus [ONNX Modell Zoo](https://github.com/onnx/models) auf GitHub herunterladen.

Falls Sie ein eigenes Modell trainieren möchten, können Sie dieses [Lernprogramm](train-ai-model.md) absolvieren, mit dem wir dieses MNIST-Modell trainiert haben.

## <a name="5-add-the-model"></a>5. Hinzufügen des Modells

Nachdem Sie das MNIST-Modell heruntergeladen haben, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Ordner "Assets", und wählen Sie **Hinzufügen** > **Vorhandenes Element** aus. Zeigen Sie mit der Dateiauswahl auf den Speicherort des ONNX-Modells, und klicken Sie auf „Hinzufügen“.

Das Projekt sollte nun zwei neue Dateien haben:

- `MNIST.onnx` – Ihr trainiertes Modell
- `MNIST.cs` – den von Windows ML generierten Code

![Projektmappen-Explorer mit neuen Dateien](images/get-started3.png)

Um sicherzustellen, dass das Modell beim Kompilieren der Anwendung erstellt wird, klicken Sie mit der rechten Maustaste auf die `mnist.onnx`-Datei, und wählen Sie **Eigenschaften** aus. Für **Buildvorgang** wählen Sie **Inhalt**.

Betrachten wir nun den neu generierten Code in der `MNIST.cs`-Datei. Es gibt drei Klassen:

- **MNISTModel** erstellt die Modelldarstellung, bindet die spezifischen Eingaben und Ausgaben an das Modell und wertet das Modell asynchron aus. 
- **MNISTModelInput** initialisiert die Eingabetypen, die das Modell erwartet. In diesem Fall erwartet die Eingabe einen VideoFrame.
- **MNISTModelOutput** initialisiert die Typen, die das Modell ausgibt. In diesem Fall ergibt sich als Ausgabe eine Liste namens „classLabel” vom Typ `<long>` und ein Dictionary namens „prediction” vom Typ `<long, float>`

Wir verwenden jetzt diese Klassen zum Laden, Binden und Auswerten des Modells in unserem Projekt.

## <a name="6-load-bind-and-evaluate-the-model"></a>6. Laden, Binden und Auswerten des Modells

Für Windows ML-Anwendungen, verfolgen wird das folgende Muster: Laden > Binden > Auswerten.

- Laden Sie das Machine Learning-Modell.
- Binden Sie Ein- und Ausgaben an das Modell.
- Werten Sie das Modell aus, und zeigen Sie die Ergebnisse an.

Wir verwenden den Benutzeroberflächencode, der in `MNIST.cs` erstellt wurde, um das Modell in unserer App zu laden, zu binden und auszuwerten.

Lassen Sie uns zunächst das Modell sowie Ein- und Ausgaben in `MainPage.xaml.cs` instanziieren.

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

In LoadModel() wird das Modell geladen.

```csharp
private async void LoadModel()
{
    //Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/MNIST.onnx"));
    ModelGen = await MNISTModel.CreateMNISTModel(modelFile);
}
```

Als Nächstes möchten wir unsere Ein- und Ausgaben an das Modell binden. 

In diesem Fall erwartet unser Modell eine Eingabe vom Typ VideoFrame. Mit Hilfe unserer Hilfsfunktionen in `helper.cs` kopieren wir den Inhalt von InkCanvas, konvertieren ihn in den Typ VideoFrame und binden ihn an unser Modell.

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
     //Bind model input with contents from InkCanvas
     ModelInput.Input3 = await helper.GetHandWrittenImage(inkGrid);
}
```

Zur Ausgabe rufen wir einfach EvaluateAsync() mit der angegebenen Eingabe auf. Da das Modell eine Liste von Ziffern mit einer entsprechenden Wahrscheinlichkeit zurückgibt, müssen wir die zurückgegebene Liste analysieren, um zu bestimmen, welche Ziffer die höchste Wahrscheinlichkeit hat, und diese anzeigen.

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

Schließlich müssen wir InkCanvas löschen, damit Benutzer eine andere Nummer ziehen können.

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="7-launch-the-app"></a>7. Starten der App

Sobald wir die App erstellt und gestartet haben, können wir eine auf InkCanvas gezeichnete Zahl erkennen.

![komplette App](images/get-started4.png)

## <a name="8-next-steps"></a>8. Nächste Schritte

Das war's – Sie haben Ihre erste Windows ML-App erstellt! Weitere Beispiele zur Verwendung von Windows ML finden Sie unter [Beispiel-Apps](samples.md).