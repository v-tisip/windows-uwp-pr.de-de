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
# <a name="how-to-train-a-model-for-windows-ml-in-visual-studio"></a><span data-ttu-id="4d1a2-104">So trainieren Sie ein Modell für Windows ML in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4d1a2-104">How to train a model for Windows ML in Visual Studio</span></span>

<span data-ttu-id="4d1a2-105">In diesem Lernprogramm verwenden wir [Visual Studio Tools for AI](http://aka.ms/vstoolsforai), eine Erweiterung für Entwicklung zum Erstellen, Testen und Bereitstellen von Deep Learning- und AI-Lösungen, um ein Modell für die MNIST-Beispiel-App unter [Erste Schritte](get-started.md) zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-105">In this tutorial, we'll use [Visual Studio Tools for AI](http://aka.ms/vstoolsforai), a development extension for building, testing, and deploying Deep Learning & AI solutions, to train a model for the MNIST sample app in [Get Started](get-started.md).</span></span>

<span data-ttu-id="4d1a2-106">Wir trainieren das Modell mit dem [Microsoft Cognitive Toolkit (CNTK)](http://www.microsoft.com/en-us/cognitive-toolkit)-Framework und dem [MNIST-Dataset](http://yann.lecun.com/exdb/mnist/), das über einen Trainingssatz von 60.000Beispielen und einen Testsatz von 10.000Beispielen handschriftlicher Ziffern verfügt.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-106">We'll train the model with the [Microsoft Cognitive Toolkit (CNTK)](http://www.microsoft.com/en-us/cognitive-toolkit) framework and the [MNIST dataset](http://yann.lecun.com/exdb/mnist/), which has a training set of 60,000 examples and a test set of 10,000 examples of handwritten digits.</span></span> <span data-ttu-id="4d1a2-107">Anschließend speichern wird das Modell im [Open Neural Network Exchange (ONNX)](https://onnx.ai/)-Format für die Verwendung mit Windows ML.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-107">We'll then save the model using the [Open Neural Network Exchange (ONNX)](https://onnx.ai/) format to use with Windows ML.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d1a2-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="4d1a2-108">Prerequisites</span></span>
### <a name="install-visual-studio-tools-for-ai"></a><span data-ttu-id="4d1a2-109">Installieren von Visual Studio Tools for AI</span><span class="sxs-lookup"><span data-stu-id="4d1a2-109">Install Visual Studio Tools for AI</span></span>
<span data-ttu-id="4d1a2-110">Zunächst müssen Sie [Visual Studio](https://www.visualstudio.com/downloads/) herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-110">To get started, you'll need to download and install [Visual Studio](https://www.visualstudio.com/downloads/).</span></span> <span data-ttu-id="4d1a2-111">Nachdem Sie Visual Studio geöffnet haben, aktivieren Sie die Erweiterung **Visual Studio Tools for AI**:</span><span class="sxs-lookup"><span data-stu-id="4d1a2-111">Once you have Visual Studio open, activate the **Visual Studio Tools for AI** extension:</span></span>

1. <span data-ttu-id="4d1a2-112">Klicken Sie auf die Menüleiste in Visual Studio, und wählen Sie „Erweiterungen und Updates“ aus.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-112">Click on the menu bar in Visual Studio and select "Extensions and Updates..."</span></span>
2. <span data-ttu-id="4d1a2-113">Klicken Sie auf die Registerkarte „Online“, und wählen Sie „Visual Studio Marketplace durchsuchen“.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-113">Click on "Online" tab and select "Search Visual Studio Marketplace."</span></span>
3. <span data-ttu-id="4d1a2-114">Suchen Sie nach „Visual Studio Tools for AI“.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-114">Search for "Visual Studio Tools for AI."</span></span> 
3. <span data-ttu-id="4d1a2-115">Klicken Sie auf die Schaltfläche **Download**.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-115">Click on the **Download** button.</span></span> 
4. <span data-ttu-id="4d1a2-116">Starten Sie Visual Studio nach der Installation neu.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-116">After installation, restart Visual Studio.</span></span> 

<span data-ttu-id="4d1a2-117">Die Erweiterung ist aktiv, sobald Visual Studio neu gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-117">The extension will be active once Visual Studio restarts.</span></span> <span data-ttu-id="4d1a2-118">Wenn Sie Probleme haben, finden Sie weitere Informationen unter [Suchen von Visual Studio-Erweiterungen](hhttps://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions).</span><span class="sxs-lookup"><span data-stu-id="4d1a2-118">If you're having trouble, check out [Finding Visual Studio extensions](hhttps://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions).</span></span>

### <a name="download-sample-code"></a><span data-ttu-id="4d1a2-119">Herunterladen von Beispielcode</span><span class="sxs-lookup"><span data-stu-id="4d1a2-119">Download sample code</span></span>
<span data-ttu-id="4d1a2-120">Laden Sie das [Beispiele für AI](https://github.com/Microsoft/samples-for-ai)-Repository auf GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-120">Download the [Samples for AI](https://github.com/Microsoft/samples-for-ai) repo on GitHub.</span></span> <span data-ttu-id="4d1a2-121">In den Beispielen werden die ersten Schritte zu Deep Learning in TensorFlow, CNTK, Theano usw. behandelt.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-121">The samples cover getting started with deep learning across TensorFlow, CNTK, Theano and more.</span></span>

### <a name="install-cntk"></a><span data-ttu-id="4d1a2-122">Installieren von CNTK</span><span class="sxs-lookup"><span data-stu-id="4d1a2-122">Install CNTK</span></span>
<span data-ttu-id="4d1a2-123">Installieren Sie [CNTK für Python unter Windows](https://docs.microsoft.com/en-us/cognitive-toolkit/setup-windows-python?tabs=cntkpy24).</span><span class="sxs-lookup"><span data-stu-id="4d1a2-123">Install [CNTK for Python on Windows](https://docs.microsoft.com/en-us/cognitive-toolkit/setup-windows-python?tabs=cntkpy24).</span></span> <span data-ttu-id="4d1a2-124">Beachten Sie, dass Sie auch Python installieren müssen, sofern nicht bereits geschehen.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-124">Note that you'll also have to install Python if you haven't already.</span></span>

<span data-ttu-id="4d1a2-125">Alternativ finden Sie zur Vorbereitung Ihres Computers für die Entwicklung von Deep Learning-Modellen unter [Vorbereiten der Umgebung für die Entwicklung](https://github.com/Microsoft/samples-for-ai/blob/master/README.md) einen vereinfachten Installer für die Installation von Python, CNTK, TensorFlow, NVIDIA GPU-Treiber (optional) usw.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-125">Alternatively, to prepare your machine for deep learning model development, see [Preparing your development environment](https://github.com/Microsoft/samples-for-ai/blob/master/README.md) for a simplified installer for installing Python, CNTK, TensorFlow, NVIDIA GPU drivers (optional) and more.</span></span>

## <a name="1-open-project"></a><span data-ttu-id="4d1a2-126">1. Öffnen des Projekts</span><span class="sxs-lookup"><span data-stu-id="4d1a2-126">1. Open project</span></span>

<span data-ttu-id="4d1a2-127">Starten Sie Visual Studio, und wählen Sie **Datei > Öffnen > Projekt/Lösung** aus.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-127">Launch Visual Studio and select **File > Open > Project/Solution**.</span></span> <span data-ttu-id="4d1a2-128">Wählen Sie aus dem Repository mit Beispielen für AI den Ordner **Examples\cntk\python** aus, und öffnen Sie die Datei **CNTKPythonExamples.sln**.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-128">From the Samples for AI repository, select the **examples\cntk\python** folder, and open the **CNTKPythonExamples.sln** file.</span></span>

![Öffnen der Projektmappe](images/open-solution.png)

## <a name="2-train-the-model"></a><span data-ttu-id="4d1a2-130">2. Trainieren des Modells</span><span class="sxs-lookup"><span data-stu-id="4d1a2-130">2. Train the model</span></span>

<span data-ttu-id="4d1a2-131">Um das MNIST-Projekt als Startprojekt festzulegen, klicken Sie mit der rechten Maustaste auf das Python-Projekt, und wählen Sie **Als Startprojekt festlegen** aus.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-131">To set the MNIST project as the startup project, right-click on the python project and select **Set as Startup Project**.</span></span>

![Projektmappe](images/mnist-startup.png)

<span data-ttu-id="4d1a2-133">Öffnen Sie als Nächstes die Datei „train_mnist_onnx.py“, und drücken Sie dann auf F5 oder wählen Sie die grüne Schaltfläche **Ausführen**.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-133">Next, open the train_mnist_onnx.py file and **Run** the project by pressing F5 or the green Run button.</span></span>

## <a name="3-view-the-model-and-add-it-to-your-app"></a><span data-ttu-id="4d1a2-134">3. Anzeigen des Modells und Hinzufügen zu Ihrer App</span><span class="sxs-lookup"><span data-stu-id="4d1a2-134">3. View the model and add it to your app</span></span>

<span data-ttu-id="4d1a2-135">Der Ordner samples-for-ai/examples/cntk/python/MNIST sollte nun die trainierte Modelldatei **mnist.onnx** enthalten.</span><span class="sxs-lookup"><span data-stu-id="4d1a2-135">Now, the trained **mnist.onnx** model file should be in the samples-for-ai/examples/cntk/python/MNIST folder.</span></span> <span data-ttu-id="4d1a2-136">Sie können diese trainierte Modelldatei **mnist.onnx** verwenden, um die MNIST-Beispiel-App in [Erste Schritte](get-started.md) zu erstellen!</span><span class="sxs-lookup"><span data-stu-id="4d1a2-136">You can use this trained **mnist.onnx** model file to build the MNIST sample app in [Get Started](get-started.md)!</span></span> 

## <a name="4-learn-more"></a><span data-ttu-id="4d1a2-137">4. Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4d1a2-137">4. Learn more</span></span>
<span data-ttu-id="4d1a2-138">Weitere Informationen zum Beschleunigen des Trainings von Deep Learning-Modellen mit [Virtuelle GPU-fähige Azure-Computer](https://docs.microsoft.com/en-us/visualstudio/ai/tensorflow-vm) usw. finden Sie unter [Künstliche Intelligenz bei Microsoft](https://www.microsoft.com/ai) und [Microsoft Machine Learning-Technologien](https://docs.microsoft.com/en-us/azure/machine-learning/#More-Microsoft-Machine-Learning-Technologies).</span><span class="sxs-lookup"><span data-stu-id="4d1a2-138">To learn how to speed up training deep learning models by using [Azure GPU Virtual Machines](https://docs.microsoft.com/en-us/visualstudio/ai/tensorflow-vm) and more, visit [Artificial Intelligence at Microsoft](https://www.microsoft.com/ai) and [Microsoft Machine Learning Technologies](https://docs.microsoft.com/en-us/azure/machine-learning/#More-Microsoft-Machine-Learning-Technologies).</span></span>