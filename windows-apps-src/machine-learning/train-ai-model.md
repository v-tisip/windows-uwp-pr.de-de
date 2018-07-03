---
author: serenaz
title: So trainieren Sie ein Modell für Windows ML in Visual Studio
description: Erfahren Sie, wie Sie mit dieser ausführlichen Anleitung ein Modell für Windows ML mit Visual Studio Tools for AI trainieren.
ms.author: sezhen
ms.date: 03/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Windows Machine Learning, Visual Studio
ms.localizationpriority: medium
ms.openlocfilehash: 1b54b0665a2483b8a0be710f505e928c852f4dba
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1842667"
---
# <a name="how-to-train-a-model-for-windows-ml-in-visual-studio"></a>So trainieren Sie ein Modell für Windows ML in Visual Studio

In diesem Lernprogramm verwenden wir [Visual Studio Tools for AI](http://aka.ms/vstoolsforai), eine Erweiterung für Entwicklung zum Erstellen, Testen und Bereitstellen von Deep Learning- und AI-Lösungen, um ein Modell für die MNIST-Beispiel-App unter [Erste Schritte](get-started.md) zu trainieren.

Wir trainieren das Modell mit dem [Microsoft Cognitive Toolkit (CNTK)](http://www.microsoft.com/en-us/cognitive-toolkit)-Framework und dem [MNIST-Dataset](http://yann.lecun.com/exdb/mnist/), das über einen Trainingssatz von 60.000Beispielen und einen Testsatz von 10.000Beispielen handschriftlicher Ziffern verfügt. Anschließend speichern wird das Modell im [Open Neural Network Exchange (ONNX)](https://onnx.ai/)-Format für die Verwendung mit Windows ML.

## <a name="prerequisites"></a>Voraussetzungen
### <a name="install-visual-studio-tools-for-ai"></a>Installieren von Visual Studio Tools for AI
Zunächst müssen Sie [Visual Studio](https://www.visualstudio.com/downloads/) herunterladen und installieren. Nachdem Sie Visual Studio geöffnet haben, aktivieren Sie die Erweiterung **Visual Studio Tools for AI**:

1. Klicken Sie auf die Menüleiste in Visual Studio, und wählen Sie „Erweiterungen und Updates“ aus.
2. Klicken Sie auf die Registerkarte „Online“, und wählen Sie „Visual Studio Marketplace durchsuchen“.
3. Suchen Sie nach „Visual Studio Tools for AI“. 
3. Klicken Sie auf die Schaltfläche **Download**. 
4. Starten Sie Visual Studio nach der Installation neu. 

Die Erweiterung ist aktiv, sobald Visual Studio neu gestartet wurde. Wenn Sie Probleme haben, finden Sie weitere Informationen unter [Suchen von Visual Studio-Erweiterungen](hhttps://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions).

### <a name="download-sample-code"></a>Herunterladen von Beispielcode
Laden Sie das [Beispiele für AI](https://github.com/Microsoft/samples-for-ai)-Repository auf GitHub herunter. In den Beispielen werden die ersten Schritte zu Deep Learning in TensorFlow, CNTK, Theano usw. behandelt.

### <a name="install-cntk"></a>Installieren von CNTK
Installieren Sie [CNTK für Python unter Windows](https://docs.microsoft.com/en-us/cognitive-toolkit/setup-windows-python?tabs=cntkpy24). Beachten Sie, dass Sie auch Python installieren müssen, sofern nicht bereits geschehen.

Alternativ finden Sie zur Vorbereitung Ihres Computers für die Entwicklung von Deep Learning-Modellen unter [Vorbereiten der Umgebung für die Entwicklung](https://github.com/Microsoft/samples-for-ai/blob/master/README.md) einen vereinfachten Installer für die Installation von Python, CNTK, TensorFlow, NVIDIA GPU-Treiber (optional) usw.

## <a name="1-open-project"></a>1. Öffnen des Projekts

Starten Sie Visual Studio, und wählen Sie **Datei > Öffnen > Projekt/Lösung** aus. Wählen Sie aus dem Repository mit Beispielen für AI den Ordner **Examples\cntk\python** aus, und öffnen Sie die Datei **CNTKPythonExamples.sln**.

![Öffnen der Projektmappe](images/open-solution.png)

## <a name="2-train-the-model"></a>2. Trainieren des Modells

Um das MNIST-Projekt als Startprojekt festzulegen, klicken Sie mit der rechten Maustaste auf das Python-Projekt, und wählen Sie **Als Startprojekt festlegen** aus.

![Projektmappe](images/mnist-startup.png)

Öffnen Sie als Nächstes die Datei „train_mnist_onnx.py“, und drücken Sie dann auf F5 oder wählen Sie die grüne Schaltfläche **Ausführen**.

## <a name="3-view-the-model-and-add-it-to-your-app"></a>3. Anzeigen des Modells und Hinzufügen zu Ihrer App

Der Ordner samples-for-ai/examples/cntk/python/MNIST sollte nun die trainierte Modelldatei **mnist.onnx** enthalten. Sie können diese trainierte Modelldatei **mnist.onnx** verwenden, um die MNIST-Beispiel-App in [Erste Schritte](get-started.md) zu erstellen! 

## <a name="4-learn-more"></a>4. Weitere Informationen
Weitere Informationen zum Beschleunigen des Trainings von Deep Learning-Modellen mit [Virtuelle GPU-fähige Azure-Computer](https://docs.microsoft.com/en-us/visualstudio/ai/tensorflow-vm) usw. finden Sie unter [Künstliche Intelligenz bei Microsoft](https://www.microsoft.com/ai) und [Microsoft Machine Learning-Technologien](https://docs.microsoft.com/en-us/azure/machine-learning/#More-Microsoft-Machine-Learning-Technologies).