---
author: serenaz
title: Übersicht über Windows ML
description: Erfahren Sie mehr über Windows Machine Learning und über die Entwicklung mit Windows ML.
ms.author: sezhen
ms.date: 03/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: a2470cff6b5c7f07c720a38d0bff00486e4c6b27
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1842870"
---
# <a name="windows-ml-overview"></a><span data-ttu-id="1bb69-104">Übersicht über Windows ML</span><span class="sxs-lookup"><span data-stu-id="1bb69-104">Windows ML overview</span></span>

![Grafik zu Windows Machine Learning](images/brain.png)

## <a name="what-is-machine-learning"></a><span data-ttu-id="1bb69-106">Was ist Machine Learning?</span><span class="sxs-lookup"><span data-stu-id="1bb69-106">What is machine learning?</span></span>

<span data-ttu-id="1bb69-107">Machine Learning (ML) ermöglicht Computern die Verwendung vorhandener Daten, um erwartete Ergebnisse und Verhaltensweisen vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="1bb69-107">Machine learning (ML) allows computers to use existing data to predict expected outcomes and behaviors.</span></span> <span data-ttu-id="1bb69-108">Durch die Verarbeitung zuvor gesammelter Daten erstellen ML-Algorithmen Modelle, die die korrekte Ausgabe bei einer neuen Eingabe vorhersagen können.</span><span class="sxs-lookup"><span data-stu-id="1bb69-108">By processing previously collected data, ML algorithms build models that can predict the correct output when presented with a new input.</span></span> <span data-ttu-id="1bb69-109">Ein Modell kann beispielsweise so trainiert werden, dass E-Mail-Nachrichten (Eingabe) als Spam bzw. nicht als Spam (Ausgabe) ausgewertet werden.</span><span class="sxs-lookup"><span data-stu-id="1bb69-109">For example, a model can be trained to evaluate email messages (input) as spam or not spam (output).</span></span>

<span data-ttu-id="1bb69-110">Die Modellerstellungsphase wird als „Training“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1bb69-110">The model-building phase is called "training."</span></span> <span data-ttu-id="1bb69-111">Sobald das Modell mit vorhandenen Daten trainiert wurde, kann es Vorhersagen mit neuen, zuvor nicht sichtbaren Daten treffen, was als "Rückschluss", "Auswertung" oder "Bewertung" bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="1bb69-111">Once trained with existing data, the model can perform predictions with new, previously unseen data, which is called "inferencing," "evaluation," or "scoring."</span></span>

<span data-ttu-id="1bb69-112">Trainierte Modelle erzeugen oft bessere Ergebnisse als Programme, die für die Befolgung strenger Anweisungen geschrieben wurden, insbesondere für komplexe Aufgaben mit vielen Kombinationsmöglichkeiten von Ein- und Ausgaben.</span><span class="sxs-lookup"><span data-stu-id="1bb69-112">Trained models often produce better results than programs written to follow a strict set of instructions, especially for complex tasks with many possible combinations of inputs and outputs.</span></span> <span data-ttu-id="1bb69-113">Empfehlungsalgorithmen stellen beispielsweise personalisierte Empfehlungen für Millionen von Benutzern auf E-Commerce- und Medienstreaming-Websites bereit, was ohne Machine Learning nahezu unmöglich wäre.</span><span class="sxs-lookup"><span data-stu-id="1bb69-113">For example, recommendation algorithms provide personalized recommendations for millions of users on e-commerce and media streaming sites, which would be nearly impossible without machine learning.</span></span> <span data-ttu-id="1bb69-114">Ein weiterer Bereich, der Machine Learning nutzt, ist Computer-Vision, die Computern die Klassifizierung und Identifizierung von Bildern nach dem Training für zuvor beschriftete Bilder ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="1bb69-114">Another field that leverages machine learning is computer vision, which allows computers to classify and identify images after training on previously labelled images.</span></span>

<span data-ttu-id="1bb69-115">Die Möglichkeiten und Anwendungen von Machine Learning sind endlos. Weitere Informationen zu Forschung und Lösungen finden Sie unter [Künstliche Intelligenz bei Microsoft](https://www.microsoft.com/ai) und [Microsoft AI-Plattform](https://azure.microsoft.com/en-us/overview/ai-platform/).</span><span class="sxs-lookup"><span data-stu-id="1bb69-115">The possibilities and applications of machine learning are endless; for more information about research and solutions, visit [Artifical Intelligence at Microsoft](https://www.microsoft.com/ai) and [Microsoft AI platform](https://azure.microsoft.com/en-us/overview/ai-platform/).</span></span> <span data-ttu-id="1bb69-116">Falls Sie Machine Learning- und AI-Modelle erstellen möchten, erhalten Sie weitere Informationen auch unter [Azure Machine Learning Services](https://docs.microsoft.com/azure/machine-learning/preview/overview-what-is-azure-ml).</span><span class="sxs-lookup"><span data-stu-id="1bb69-116">If you'd like to build Machine Learning and AI models, you can also check out [Azure Machine Learning Services](https://docs.microsoft.com/azure/machine-learning/preview/overview-what-is-azure-ml).</span></span>

## <a name="what-is-windows-ml"></a><span data-ttu-id="1bb69-117">Was ist Windows ML?</span><span class="sxs-lookup"><span data-stu-id="1bb69-117">What is Windows ML?</span></span>

<span data-ttu-id="1bb69-118">Windows ML ist eine Plattform, die trainierte Machine Learning-Modelle auf Windows10-Geräten auswertet. Dadurch können Entwickler Machine Learning in ihren Windows-Anwendungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="1bb69-118">Windows ML is a platform that evaluates trained machine learning models on Windows 10 devices, allowing developers to use machine learning within their Windows applications.</span></span>

<span data-ttu-id="1bb69-119">Hier sind einige Highlights von Windows ML:</span><span class="sxs-lookup"><span data-stu-id="1bb69-119">Some highlights of Windows ML include:</span></span>

- **<span data-ttu-id="1bb69-120">Hardwarebeschleunigung</span><span class="sxs-lookup"><span data-stu-id="1bb69-120">Hardware acceleration</span></span>**
    
    <span data-ttu-id="1bb69-121">Auf DirectX12-fähigen Geräten beschleunigt Windows ML die Auswertung von Deep Learning-Modellen mithilfe der GPU.</span><span class="sxs-lookup"><span data-stu-id="1bb69-121">On DirectX12 capable devices, Windows ML accelerates the evaluation of Deep Learning models using the GPU.</span></span> <span data-ttu-id="1bb69-122">Darüber hinaus ermöglichen CPU-Optimierungen eine leistungsstarke Auswertung klassischer ML- und Deep Learning-Algorithmen.</span><span class="sxs-lookup"><span data-stu-id="1bb69-122">CPU optimizations additionally enable high-performance evaluation of both classical ML and Deep Learning algorithms.</span></span>

- **<span data-ttu-id="1bb69-123">Lokale Auswertung</span><span class="sxs-lookup"><span data-stu-id="1bb69-123">Local evaluation</span></span>**

    <span data-ttu-id="1bb69-124">Windows ML wertet lokale Hardware aus, indem Probleme in Bezug auf Konnektivität, Bandbreite und Datenschutz beseitigt werden.</span><span class="sxs-lookup"><span data-stu-id="1bb69-124">Windows ML evaluates on local hardware, removing concerns of connectivity, bandwidth, and data privacy.</span></span> <span data-ttu-id="1bb69-125">Die lokale Auswertung ermöglicht zudem eine geringe Latenz und hohe Leistung für schnelle Bewertungsergebnisse.</span><span class="sxs-lookup"><span data-stu-id="1bb69-125">Local evaluation also enables low latency and high performance for quick evaluation results.</span></span>

- **<span data-ttu-id="1bb69-126">Bildverarbeitung</span><span class="sxs-lookup"><span data-stu-id="1bb69-126">Image processing</span></span>**

    <span data-ttu-id="1bb69-127">Für Computer-Vision-Szenarien vereinfacht und optimiert Windows ML die Verwendung von Bild-, Video und Kameradaten, indem die Vorverarbeitung von Frames behandelt und die Einrichtung der Kamera-Pipeline für die Modelleingabe bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="1bb69-127">For computer vision scenarios, Windows ML simplifies and optimizes the use of image, video, and camera data by handling frame pre-processing and providing camera pipeline setup for model input.</span></span>

## <a name="how-to-develop-with-windows-ml"></a><span data-ttu-id="1bb69-128">So entwickeln Sie mit Windows ML</span><span class="sxs-lookup"><span data-stu-id="1bb69-128">How to develop with Windows ML</span></span>

> [!VIDEO https://www.youtube.com/embed/8MCDSlm326U]

### <a name="system-requirements"></a><span data-ttu-id="1bb69-129">Systemanforderungen</span><span class="sxs-lookup"><span data-stu-id="1bb69-129">System requirements</span></span>

<span data-ttu-id="1bb69-130">Um Anwendungen zu erstellen, die Windows ML verwenden, benötigen Sie den [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)-Build 17110 oder höher.</span><span class="sxs-lookup"><span data-stu-id="1bb69-130">To build applications that use Windows ML, you'll need the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) - Build 17110 or higher.</span></span>

### <a name="onnx-models"></a><span data-ttu-id="1bb69-131">ONNX-Modelle</span><span class="sxs-lookup"><span data-stu-id="1bb69-131">ONNX models</span></span>

<span data-ttu-id="1bb69-132">Zur Verwendung von Windows ML benötigen Sie ein vorab trainiertes Machine Learning-Modell im [Open Neural Network Exchange (ONNX)](https://onnx.ai)-Format.</span><span class="sxs-lookup"><span data-stu-id="1bb69-132">To use Windows ML, you'll need a pre-trained machine learning model in the [Open Neural Network Exchange (ONNX)](https://onnx.ai) format.</span></span> <span data-ttu-id="1bb69-133">Windows ML unterstützt die v1.0-Version des ONNX-Formats, das Entwicklern die Verwendung von Modellen ermöglicht, die von verschiedenen Trainings-Frameworks erzeugt wurden.</span><span class="sxs-lookup"><span data-stu-id="1bb69-133">Windows ML supports the v1.0 release of the ONNX format, which allows developers to use models produced by different training frameworks.</span></span>

<span data-ttu-id="1bb69-134">Eine Liste der öffentlich verfügbaren ONNX-Modelle finden Sie unter [ONNX-Modelle](https://github.com/onnx/models) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="1bb69-134">For a list of publicly available ONNX models, see [ONNX Models](https://github.com/onnx/models) on GitHub.</span></span>

<span data-ttu-id="1bb69-135">Weitere Informationen zum Trainieren eines ONNX-Modells mit Visual Studio Tools for AI finden Sie unter [Trainieren eines Modells](train-ai-model.md).</span><span class="sxs-lookup"><span data-stu-id="1bb69-135">To learn how to train an ONNX model with Visual Studio Tools for AI, see [Train a model](train-ai-model.md).</span></span>

### <a name="convert-existing-models-to-onnx"></a><span data-ttu-id="1bb69-136">Konvertieren vorhandener Modelle in ONNX</span><span class="sxs-lookup"><span data-stu-id="1bb69-136">Convert existing models to ONNX</span></span>

<span data-ttu-id="1bb69-137">Viele Trainings-Frameworks unterstützen ONNX-Modelle bereits nativ. Zudem sind Konverter-Tools für viele Frameworks und Bibliotheken verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1bb69-137">Many training frameworks already natively support ONNX models, and there are converter tools for many frameworks and libraries.</span></span> <span data-ttu-id="1bb69-138">Weitere Informationen zum Exportieren aus Frameworks wie Caffe 2, PyTorch, CNTK, Chainer usw. finden Sie unter [ONNX tutorials](https://github.com/onnx/tutorials) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="1bb69-138">To learn how to export from frameworks such as Caffe 2, PyTorch, CNTK, Chainer, and more, see [ONNX tutorials](https://github.com/onnx/tutorials) on GitHub.</span></span>

<span data-ttu-id="1bb69-139">Sie können auch [WinMLTools](https://pypi.org/project/winmltools/) verwenden, um trainierte Machine Learning-Modelle in das von Windows ML akzeptierte ONNX-Format zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="1bb69-139">You can also use [WinMLTools](https://pypi.org/project/winmltools/) to convert trained machine learning model to the ONNX format accepted by Windows ML.</span></span> <span data-ttu-id="1bb69-140">WinMLTools unterstützt die Konvertierung aus den folgenden Formaten:</span><span class="sxs-lookup"><span data-stu-id="1bb69-140">WinMLTools supports conversion from these formats:</span></span>

- <span data-ttu-id="1bb69-141">Core ML</span><span class="sxs-lookup"><span data-stu-id="1bb69-141">Core ML</span></span>
- <span data-ttu-id="1bb69-142">Scikit-Learn</span><span class="sxs-lookup"><span data-stu-id="1bb69-142">Scikit-Learn</span></span>
- <span data-ttu-id="1bb69-143">XGBoost</span><span class="sxs-lookup"><span data-stu-id="1bb69-143">XGBoost</span></span>
- <span data-ttu-id="1bb69-144">LibSVM</span><span class="sxs-lookup"><span data-stu-id="1bb69-144">LibSVM</span></span>

<span data-ttu-id="1bb69-145">Weitere Informationen zum Installieren und Verwenden von WinMLTools finden Sie unter [Konvertieren eines Modells](conversion-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1bb69-145">To learn how to install and use WinMLTools, please see [Convert a model](conversion-samples.md).</span></span>

<span data-ttu-id="1bb69-146">Mit der Erweiterung „Visual Studio Tools for AI” können Sie auch WinMLTools in der Visual Studio-IDE verwenden. Damit erhalten Sie eine benutzerfreundlichere Click-Through-Funktionalität zum Konvertieren Ihrer Modelle in das ONNX-Format.</span><span class="sxs-lookup"><span data-stu-id="1bb69-146">With the Visual Studio Tools for AI extension, you can also use WinMLTools within the Visual Studio IDE for a more friendly, click-through experience to convert your models into ONNX format.</span></span> <span data-ttu-id="1bb69-147">Weitere Informationen finden Sie unter [VS-Tools für AI](https://github.com/Microsoft/vs-tools-for-ai/).</span><span class="sxs-lookup"><span data-stu-id="1bb69-147">To learn more, please visit [VS Tools for AI](https://github.com/Microsoft/vs-tools-for-ai/).</span></span>

### <a name="onnx-operators"></a><span data-ttu-id="1bb69-148">ONNX-Operatoren</span><span class="sxs-lookup"><span data-stu-id="1bb69-148">ONNX operators</span></span>

<span data-ttu-id="1bb69-149">Windows ML unterstützt 100+ ONNX-Operatoren auf der CPU und beschleunigt die Berechnung auf GPUs, die mit DirectX12 kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="1bb69-149">Windows ML supports 100+ ONNX operators on the CPU and accelerates computation on DirectX12 compatible GPUs.</span></span> <span data-ttu-id="1bb69-150">Eine vollständige Liste der Operator-Signaturen finden Sie in der Dokumentation zu ONNX-Operatorenschemas für die Namespaces [ai.onnx](https://github.com/onnx/onnx/blob/rel-1.0/docs/Operators.md) (Standard) und [ai.onnx.ml](https://github.com/onnx/onnx/blob/rel-1.0/docs/Operators-ml.md).</span><span class="sxs-lookup"><span data-stu-id="1bb69-150">For a full list of operator signatures, see the ONNX operators schemas documentation for the [ai.onnx](https://github.com/onnx/onnx/blob/rel-1.0/docs/Operators.md) (default) and [ai.onnx.ml](https://github.com/onnx/onnx/blob/rel-1.0/docs/Operators-ml.md) namespaces.</span></span>

<span data-ttu-id="1bb69-151">Windows ML unterstützt alle in der Dokumentation zu ONNX v1. 0 definierten Operatoren mit den folgenden Unterschieden:</span><span class="sxs-lookup"><span data-stu-id="1bb69-151">Windows ML supports all of the operators defined in the ONNX v1.0 documentation with the following differences:</span></span>

- <span data-ttu-id="1bb69-152">Als "experimentell"gekennzeichnete Operatoren, die von Windows ML unterstützt werden:</span><span class="sxs-lookup"><span data-stu-id="1bb69-152">Operators marked "experimental" supported by Windows ML:</span></span>
    - <span data-ttu-id="1bb69-153">Affine</span><span class="sxs-lookup"><span data-stu-id="1bb69-153">Affine</span></span>
    - <span data-ttu-id="1bb69-154">Crop</span><span class="sxs-lookup"><span data-stu-id="1bb69-154">Crop</span></span>
    - <span data-ttu-id="1bb69-155">FC</span><span class="sxs-lookup"><span data-stu-id="1bb69-155">FC</span></span>
    - <span data-ttu-id="1bb69-156">Identität</span><span class="sxs-lookup"><span data-stu-id="1bb69-156">Identity</span></span>
    - <span data-ttu-id="1bb69-157">ImageScaler</span><span class="sxs-lookup"><span data-stu-id="1bb69-157">ImageScaler</span></span>
    - <span data-ttu-id="1bb69-158">MeanVarianceNormalization</span><span class="sxs-lookup"><span data-stu-id="1bb69-158">MeanVarianceNormalization</span></span>
    - <span data-ttu-id="1bb69-159">ParametricSoftplus</span><span class="sxs-lookup"><span data-stu-id="1bb69-159">ParametricSoftplus</span></span>
    - <span data-ttu-id="1bb69-160">ScaledTanh</span><span class="sxs-lookup"><span data-stu-id="1bb69-160">ScaledTanh</span></span>
    - <span data-ttu-id="1bb69-161">ThresholdedRelu</span><span class="sxs-lookup"><span data-stu-id="1bb69-161">ThresholdedRelu</span></span>
    - <span data-ttu-id="1bb69-162">Upsample</span><span class="sxs-lookup"><span data-stu-id="1bb69-162">Upsample</span></span>
- <span data-ttu-id="1bb69-163">MatMul – größer als 2D Matrixmultiplikation wird derzeit nicht unterstützt, ausgenommen auf CPU</span><span class="sxs-lookup"><span data-stu-id="1bb69-163">MatMul - greater than 2D matrix multiplication is not currently supported, supported on CPU only</span></span>
- <span data-ttu-id="1bb69-164">Cast – nur auf CPU unterstützt</span><span class="sxs-lookup"><span data-stu-id="1bb69-164">Cast - supported on CPU only</span></span>
- <span data-ttu-id="1bb69-165">Die folgenden Operatoren werden derzeit nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="1bb69-165">The following operators are not supported at this time:</span></span>
    - <span data-ttu-id="1bb69-166">RandomUniform</span><span class="sxs-lookup"><span data-stu-id="1bb69-166">RandomUniform</span></span>
    - <span data-ttu-id="1bb69-167">RandomUniformLike</span><span class="sxs-lookup"><span data-stu-id="1bb69-167">RandomUniformLike</span></span>
    - <span data-ttu-id="1bb69-168">RandomNormal</span><span class="sxs-lookup"><span data-stu-id="1bb69-168">RandomNormal</span></span>
    - <span data-ttu-id="1bb69-169">RandomNormalLike</span><span class="sxs-lookup"><span data-stu-id="1bb69-169">RandomNormalLike</span></span>

### <a name="automatic-interface-code-generation"></a><span data-ttu-id="1bb69-170">Automatische Generierung von Schnittstellencode</span><span class="sxs-lookup"><span data-stu-id="1bb69-170">Automatic interface code generation</span></span>

<span data-ttu-id="1bb69-171">Mit einer ONNX-Modelldatei erstellt der Codegenerator von Windows ML eine Schnittstelle für die Interaktion mit dem Modell in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="1bb69-171">With an ONNX model file, Windows ML's code generator creates an interface to interact with the model in your app.</span></span> <span data-ttu-id="1bb69-172">Die generierte Schnittstelle enthält die Wrapper-Klassen, die das Modell, Eingaben und Ausgaben darstellen.</span><span class="sxs-lookup"><span data-stu-id="1bb69-172">The generated interface includes wrapper classes that represent the model, inputs, and outputs.</span></span> <span data-ttu-id="1bb69-173">Der generierte Code ruft die [Windows ML-API](/uwp/api/windows.ai.machinelearning.preview) automatisch ab, sodass Sie das Modell in Ihrem Projekt einfach laden, binden und auswerten können.</span><span class="sxs-lookup"><span data-stu-id="1bb69-173">The generated code calls the [Windows ML API](/uwp/api/windows.ai.machinelearning.preview) for you, allowing you to easily load, bind, and evaluate the model in your project.</span></span> <span data-ttu-id="1bb69-174">Der Codegenerator unterstützt derzeit C# und C++/CX.</span><span class="sxs-lookup"><span data-stu-id="1bb69-174">The code generator currently supports both C# and C++/CX.</span></span>

<span data-ttu-id="1bb69-175">Für UWP-Entwickler: Der automatische Codegenerator von Windows ML ist in [Visual Studio](https://developer.microsoft.com/windows/downloads) integriert.</span><span class="sxs-lookup"><span data-stu-id="1bb69-175">For UWP developers, Windows ML's automatic code generator is natively integrated with [Visual Studio](https://developer.microsoft.com/windows/downloads).</span></span> <span data-ttu-id="1bb69-176">Fügen Sie innerhalb Ihres Visual Studio-Projekts einfach Ihre ONNX-Datei als vorhandenes Element hinzu, und VS generiert Windows ML-Wrapperklassen in einer neuen Schnittstellendatei.</span><span class="sxs-lookup"><span data-stu-id="1bb69-176">Inside your Visual Studio project, simply add your ONNX file as an existing item, and VS will generate Windows ML wrapper classes in a new interface file.</span></span>

<span data-ttu-id="1bb69-177">Sie können auch das im Windows SDK enthaltene Befehlszeilentool `mlgen.exe` verwenden, um Wrapper-Klassen von Windows ML zu generieren.</span><span class="sxs-lookup"><span data-stu-id="1bb69-177">You can also use the command line tool `mlgen.exe`, which comes with the Windows SDK, to generate Windows ML wrapper classes.</span></span> <span data-ttu-id="1bb69-178">Das Tool befindet sich unter `(SDK_root)\bin\<version>\x64` oder `(SDK_root)\bin\<version>\x86`, wobei SDK_root das SDK-Installationsverzeichnis ist.</span><span class="sxs-lookup"><span data-stu-id="1bb69-178">The tool is located in `(SDK_root)\bin\<version>\x64` or `(SDK_root)\bin\<version>\x86`, where SDK_root is the SDK installation directory.</span></span> <span data-ttu-id="1bb69-179">Verwenden Sie zum Ausführen des Tools den nachstehenden Befehl.</span><span class="sxs-lookup"><span data-stu-id="1bb69-179">To run the tool, use the command below.</span></span>

```
mlgen -i INPUT-FILE -l LANGUAGE -n NAMESPACE [-o OUTPUT-FILE]
```

<span data-ttu-id="1bb69-180">Definition des Eingabeparameters:</span><span class="sxs-lookup"><span data-stu-id="1bb69-180">Input parameters definition:</span></span>

- `INPUT-FILE`<span data-ttu-id="1bb69-181">: die ONNX-Modelldatei</span><span class="sxs-lookup"><span data-stu-id="1bb69-181">: the ONNX model file</span></span>
- `LANGUAGE`<span data-ttu-id="1bb69-182">: CPPCX oder CS</span><span class="sxs-lookup"><span data-stu-id="1bb69-182">: CPPCX or CS</span></span>
- `NAMESPACE`<span data-ttu-id="1bb69-183">: der Namespace des generierten Codes</span><span class="sxs-lookup"><span data-stu-id="1bb69-183">: the namespace of the generated code</span></span>
- `OUTPUT-FILE`<span data-ttu-id="1bb69-184">: Pfad der Datei, in die der generierte Code geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="1bb69-184">: file path where the generated code will be written to.</span></span> <span data-ttu-id="1bb69-185">Wenn keine AUSGABEDATEI angegeben ist, wird der generierte Code in die Standardausgabe geschrieben.</span><span class="sxs-lookup"><span data-stu-id="1bb69-185">If OUTPUT-FILE is not specified, the generated code is written to the standard output</span></span>

<span data-ttu-id="1bb69-186">Weitere Informationen zum Verwenden des generierten Codes in Ihrer App finden Sie unter [Integrieren eines Modells](integrate-model.md).</span><span class="sxs-lookup"><span data-stu-id="1bb69-186">To learn how to use the generated code in your app, see [Integrate a model](integrate-model.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bb69-187">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="1bb69-187">Next steps</span></span>

<span data-ttu-id="1bb69-188">Versuchen Sie, Ihre erste Windows ML-App anhand einer ausführlichen Anleitung unter [Erste Schritt](get-started.md) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1bb69-188">Try creating your first Windows ML app with a step-by-step tutorial in [Get Started](get-started.md).</span></span>