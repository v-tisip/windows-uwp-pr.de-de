---
author: wschin
title: Konvertieren vorhandener ML-Modelle in ONNX
description: Codebeispiele demonstrieren, wie mit WinMLTools bestehende Modelle in scikit-learn und Core ML in das ONNX-Format konvertiert werden.
ms.author: sezhen
ms.date: 3/7/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, maschinelles Lernen in Windows, WinML, WinMLTools, ONNX, ONNXMLTools, scikit-learn, Core ML
ms.localizationpriority: medium
ms.openlocfilehash: 7b2e9c8b661ccd2b0358882992da6c4f160b49f0
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1843000"
---
# <a name="convert-existing-ml-models-to-onnx"></a><span data-ttu-id="44e80-104">Konvertieren vorhandener ML-Modelle in ONNX</span><span class="sxs-lookup"><span data-stu-id="44e80-104">Convert existing ML models to ONNX</span></span>

<span data-ttu-id="44e80-105">[WinMLTools](https://pypi.org/project/winmltools/) ermöglicht es Benutzern, in anderen Frameworks trainierte Modelle in das ONNX Format zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="44e80-105">[WinMLTools](https://pypi.org/project/winmltools/) allows users to convert models trained in other frameworks to ONNX format.</span></span> <span data-ttu-id="44e80-106">Hier zeigen wir Ihnen, wie Sie das WinMLTools-Paket installieren und vorhandene Modelle in scikit-learn und Core ML mit Python-Code in ONNX konvertieren.</span><span class="sxs-lookup"><span data-stu-id="44e80-106">Here we demonstrate how to install the WinMLTools package and how to convert existing models in scikit-learn and Core ML into ONNX via Python code.</span></span>

## <a name="install-winmltools"></a><span data-ttu-id="44e80-107">Installieren der WinMLTools</span><span class="sxs-lookup"><span data-stu-id="44e80-107">Install WinMLTools</span></span>

<span data-ttu-id="44e80-108">WinMLTools ist ein Python-Paket (winmltools), das die Python-Versionen 2.7 und 3.6 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="44e80-108">WinMLTools is a Python package (winmltools) that supports Python versions 2.7 and 3.6.</span></span> <span data-ttu-id="44e80-109">Wenn Sie an einem Projekt mit wissenschaftlichen Daten arbeiten, empfehlen wir die Installation einer wissenschaftlichen Python-Distribution wie Anaconda.</span><span class="sxs-lookup"><span data-stu-id="44e80-109">If you are working on a data science project, we recommend installing a scientific Python distribution such as Anaconda.</span></span>

<span data-ttu-id="44e80-110">WinMLTools folgt dem [standardmäßigen Installationsvorgang für Python-Pakete](https://packaging.python.org/installing/).</span><span class="sxs-lookup"><span data-stu-id="44e80-110">WinMLTools follows the [standard python package installation process](https://packaging.python.org/installing/).</span></span> <span data-ttu-id="44e80-111">Führen Sie in Ihrer Python-Umgebung Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="44e80-111">From your python environment, run:</span></span>

```
pip install winmltools
```

<span data-ttu-id="44e80-112">Für WinMLTools gelten die folgenden Abhängigkeiten:</span><span class="sxs-lookup"><span data-stu-id="44e80-112">WinMLTools has the following dependencies:</span></span>

- <span data-ttu-id="44e80-113">numpy v1.10.0+</span><span class="sxs-lookup"><span data-stu-id="44e80-113">numpy v1.10.0+</span></span>
- <span data-ttu-id="44e80-114">onnxmltools 0.1.0.0+</span><span class="sxs-lookup"><span data-stu-id="44e80-114">onnxmltools 0.1.0.0+</span></span>
- <span data-ttu-id="44e80-115">protobuf v.3.1.0+</span><span class="sxs-lookup"><span data-stu-id="44e80-115">protobuf v.3.1.0+</span></span>

<span data-ttu-id="44e80-116">Um die abhängigen Pakete zu aktualisieren, führen Sie den pip-Befehl mit dem Argument '-U' aus.</span><span class="sxs-lookup"><span data-stu-id="44e80-116">To update the dependent packages, please run the pip command with ‘-U’ argument.</span></span>

```
pip install -U winmltools
```

<span data-ttu-id="44e80-117">Weitere Informationen zu onnxmltools-Abhängigkeiten finden Sie unter [onnxmltools](https://github.com/onnx/onnxmltools) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="44e80-117">Please follow [onnxmltools](https://github.com/onnx/onnxmltools) on GitHub for further information on onnxmltools dependencies.</span></span>

<span data-ttu-id="44e80-118">Weitere Details zur Verwendung von WinMLTools finden Sie in der paketspezifischen Dokumentation über die Hilfefunktion.</span><span class="sxs-lookup"><span data-stu-id="44e80-118">Additional details on how to use WinMLTools can be found on the package specific documentation with the help function.</span></span>

```
help(winmltools)
```

> [!NOTE]
> <span data-ttu-id="44e80-119">Mit der Erweiterung „Visual Studio Tools for AI” können Sie auch WinMLTools in der Visual Studio-IDE verwenden. Damit erhalten Sie eine benutzerfreundlichere Click-Through-Funktionalität zum Konvertieren Ihrer Modelle in das ONNX-Format.</span><span class="sxs-lookup"><span data-stu-id="44e80-119">With the Visual Studio Tools for AI extension, you can also use WinMLTools within the Visual Studio IDE for a more friendly, click-through experience to convert your models into ONNX format.</span></span> <span data-ttu-id="44e80-120">Weitere Informationen finden Sie unter [VS-Tools für AI](https://github.com/Microsoft/vs-tools-for-ai/).</span><span class="sxs-lookup"><span data-stu-id="44e80-120">To learn more, please visit [VS Tools for AI](https://github.com/Microsoft/vs-tools-for-ai/).</span></span>

## <a name="scikit-learn-models"></a><span data-ttu-id="44e80-121">Scikit-learn-Modelle</span><span class="sxs-lookup"><span data-stu-id="44e80-121">Scikit-learn models</span></span>

<span data-ttu-id="44e80-122">Das folgende Code-Snippet trainiert eine lineare Support Vector Machine in scikit-learn und konvertiert das Modell in ONNX.</span><span class="sxs-lookup"><span data-stu-id="44e80-122">The following code snippet trains a linear support vector machine in scikit-learn and converts the model into ONNX.</span></span>

~~~python
# First, we create a toy data set.
# The training matrix X contains three examples, with two features each.
# The label vector, y, stores the labels of all examples.
X = [[0.5, 1.], [-1., -1.5], [0., -2.]]
y = [1, -1, -1]

# Then, we create a linear classifier and train it.
from sklearn.svm import LinearSVC
linear_svc = LinearSVC()
linear_svc.fit(X, y)

# To convert scikit-learn models, we need to specify the input feature's name and type for our converter. 
# The following line means we have a 2-D float feature vector, and its name is "input" in ONNX.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_sklearn
linear_svc_onnx = convert_sklearn(linear_svc, name='LinearSVC', input_features=[('input', 'float', 2)])    

# Now, we save the ONNX model into binary format.
from winmltools.utils import save_model
save_model(linear_svc_onnx, 'linear_svc.onnx')

# If you'd like to load an ONNX binary file, our tool can also help.
from winmltools.utils import load_model
linear_svc_onnx = load_model('linear_svc.onnx')

# To see the produced ONNX model, we can print its contents or save it in text format.
print(linear_svc_onnx)
from winmltools.utils import save_text
save_text(linear_svc_onnx, 'linear_svc.txt')

# The conversion of linear regression is very similar. See the example below.
from sklearn.svm import LinearSVR
linear_svr = LinearSVR()
linear_svr.fit(X, y)
linear_svr_onnx = convert_sklearn(linear_svr, name='LinearSVR', input_features=[('input', 'float', 2)])   
~~~

<span data-ttu-id="44e80-123">Benutzer können `LinearSVC` durch andere scikit-learn-Modelle wie `RandomForestClassifier` ersetzen.</span><span class="sxs-lookup"><span data-stu-id="44e80-123">Users can replace `LinearSVC` with other scikit-learn models such as `RandomForestClassifier`.</span></span> <span data-ttu-id="44e80-124">Beachten Sie, dass der [automatische Codegenerator](overview.md#automatic-interface-code-generation) die `name`-Parameter verwendet, um Klassennamen und Variablen zu generieren.</span><span class="sxs-lookup"><span data-stu-id="44e80-124">Please note that the [automatic code generator](overview.md#automatic-interface-code-generation) uses the `name` parameter to generate class names and variables.</span></span> <span data-ttu-id="44e80-125">Wird `name` nicht angegeben wird, wird eine GUID generiert, die nicht den Benennungskonventionen für Sprachen wie C++ und C # entspricht.</span><span class="sxs-lookup"><span data-stu-id="44e80-125">If `name` is not provided, then a GUID is generated, which will not comply with variable naming conventions for languages like C++/C#.</span></span> 

## <a name="scikit-learn-pipelines"></a><span data-ttu-id="44e80-126">Scikit-learn-Pipelines</span><span class="sxs-lookup"><span data-stu-id="44e80-126">Scikit-learn pipelines</span></span>

<span data-ttu-id="44e80-127">Als nächstes zeigen wir, wie scikit-learn-Pipelines in ONNX konvertiert werden können.</span><span class="sxs-lookup"><span data-stu-id="44e80-127">Next, we show how scikit-learn pipelines can be converted into ONNX.</span></span>

~~~python
# First, we create a toy data set.
# Notice that the first example's last feature value, 300, is large.
X = [[0.5, 1., 300.], [-1., -1.5, -4.], [0., -2., -1.]]
y = [1, -1, -1]

# Then, we declare a linear classifier.
from sklearn.svm import LinearSVC
linear_svc = LinearSVC()

# One common trick to improve a linear model's performance is to normalize the input data.
from sklearn.preprocessing import Normalizer
normalizer = Normalizer()

# Here, we compose our scikit-learn pipeline. 
# First, we apply our normalization. 
# Then we feed the normalized data into the linear model.
from sklearn.pipeline import make_pipeline
pipeline = make_pipeline(normalizer, linear_svc)
pipeline.fit(X, y)

# Now, we convert the scikit-learn pipeline into ONNX format. 
# Compared to the previous example, notice that the specified feature dimension becomes 3.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_sklearn
pipeline_onnx = convert_sklearn(linear_svc, name='NormalizerLinearSVC', input_features=[('input', 'float', 3)])   

# We can print the fresh ONNX model.
print(pipeline_onnx)

# We can also save the ONNX model into binary file for later use.
from winmltools.utils import save_model
save_model(pipeline_onnx, 'pipeline.onnx')

# Our conversion framework provides limited support of heterogeneous feature values.
# We cannot have numerical types and string type in one feature vector. 
# Let's assume that the first two features are floats and the last feature is integer (encoded a categorical attribute).
X_heter = [[0.5, 1., 300], [-1., -1.5, 400], [0., -2., 100]]

# One popular way to represent categorical is one-hot encoding.
from sklearn.preprocessing import OneHotEncoder
one_hot_encoder = OneHotEncoder(categorical_features=[2])

# Let's initialize a classifier. 
# It will be right after the one-hot encoder in our pipeline.
linear_svc = LinearSVC()

# Then, we form a two-stage pipeline.
another_pipeline = make_pipeline(one_hot_encoder, linear_svc)
another_pipeline.fit(X_heter, y)

# Now, we convert, save, and load the converted model. 
# For heterogeneous feature vectors, we need to seperately specify their types for all homogeneous segments.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
another_pipeline_onnx = convert_sklearn(another_pipeline, name='OneHotLinearSVC', input_features=[('input', 'float', 2), ('another_input', 'int64', 1)])
save_model(another_pipeline_onnx, 'another_pipeline.onnx')
from winmltools.utils import load_model
loaded_onnx_model = load_model('another_pipeline.onnx')

# Of course, we can print the ONNX model to see if anything went wrong.
print(another_pipeline_onnx)
~~~

## <a name="core-ml-models"></a><span data-ttu-id="44e80-128">Core ML-Modelle</span><span class="sxs-lookup"><span data-stu-id="44e80-128">Core ML models</span></span>

<span data-ttu-id="44e80-129">Hier gehen wird davon aus, dass *example.mlmodel* der Pfad zu einer Beispieldatei mit einem Core ML-Modell ist.</span><span class="sxs-lookup"><span data-stu-id="44e80-129">Here, we assume that the path of an example Core ML model file is *example.mlmodel*.</span></span>

~~~python
from coremltools.models.utils import load_spec
# Load model file
model_coreml = load_spec('example.mlmodel')
from winmltools import convert_coreml
# Convert it!
# The automatic code generator (mlgen) uses the name parameter to generate class names.
model_onnx = convert_coreml(model_coreml, name='ExampleModel')   
~~~

<span data-ttu-id="44e80-130">`model_onnx` ist ein [ModelProto](https://github.com/onnx/onnxmltools/blob/0f453c3f375c1ae928b83a4c7909c82c013a5bff/onnxmltools/proto/onnx-ml.proto#L176)-Objekt von ONNX.</span><span class="sxs-lookup"><span data-stu-id="44e80-130">The `model_onnx` is an ONNX [ModelProto](https://github.com/onnx/onnxmltools/blob/0f453c3f375c1ae928b83a4c7909c82c013a5bff/onnxmltools/proto/onnx-ml.proto#L176) object.</span></span> <span data-ttu-id="44e80-131">Wir können es in zwei verschiedenen Formaten speichern.</span><span class="sxs-lookup"><span data-stu-id="44e80-131">We can save it in two different formats.</span></span>

~~~python
from winmltools.utils import save_model
# Save the produced ONNX model in binary format
save_model(model_onnx, 'example.onnx')
# Save the produced ONNX model in text format
from winmltools.utils import save_text
save_text(model_onnx, 'example.txt')
~~~

<span data-ttu-id="44e80-132">**Hinweis:**: CoreMLTools ist ein Python-Paket, das von Apple bereitgestellt wird, aber unter Windows nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="44e80-132">**Note**: CoreMLTools is a Python package provided by Apple, but is not available on Windows.</span></span> <span data-ttu-id="44e80-133">Wenn Sie das Paket unter Windows installieren müssen, installieren Sie das Paket direkt aus dem Repository:</span><span class="sxs-lookup"><span data-stu-id="44e80-133">If you need to install the package on Windows, install the package directly from the repo:</span></span>

```
pip install git+https://github.com/apple/coremltools
```

## <a name="core-ml-models-with-image-inputs-or-outputs"></a><span data-ttu-id="44e80-134">Core ML-Modelle mit Bildern als Ein- oder Ausgaben</span><span class="sxs-lookup"><span data-stu-id="44e80-134">Core ML models with image inputs or outputs</span></span>

<span data-ttu-id="44e80-135">Aufgrund fehlender Bildtypen in ONNX erfordert das Umwandeln von Core ML-Bildmodellen (Modelle, die Bilder als Eingaben oder Ausgaben verwenden) einige Vor- und Nachverarbeitungsschritte.</span><span class="sxs-lookup"><span data-stu-id="44e80-135">Because of the lack of image types in ONNX, converting Core ML image models (i.e., models using images as inputs or outputs) requires some pre-processing and post-processing steps.</span></span>

<span data-ttu-id="44e80-136">Das Ziel der Vorverarbeitung ist sicherzustellen, dass ein Eingabebild korrekt als ONNX-Tensor formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="44e80-136">The objective of pre-processing is to make sure the input image is properly formatted as an ONNX tensor.</span></span> <span data-ttu-id="44e80-137">Nehmen wir an, *X* ist eine Bildeingabe der Form [C, H, W] in Core ML.</span><span class="sxs-lookup"><span data-stu-id="44e80-137">Assume *X* is an image input with shape [C, H, W] in Core ML.</span></span> <span data-ttu-id="44e80-138">In ONNX wäre die Variable *X* ein Gleitkommatensor mit der gleichen Form, und *X*[0, :, :]/*X*[1, :, :]/*X*[2, :, :] würde den Rot/Grün/Blau-Kanal des Bilds enthalten.</span><span class="sxs-lookup"><span data-stu-id="44e80-138">In ONNX, the variable *X* would be a floating-point tensor with the same shape and *X*[0, :, :]/*X*[1, :, :]/*X*[2, :, :] stores the image's red/green/blue channel.</span></span> <span data-ttu-id="44e80-139">Die Formate für Graustufenbilder in Core ML sind [1, H, W]-Tensoren in ONNX, da es nur einen Kanal gibt.</span><span class="sxs-lookup"><span data-stu-id="44e80-139">For gray scale images in Core ML, their format are [1, H, W]-tensors in ONNX because we only have one channel.</span></span>

<span data-ttu-id="44e80-140">Wenn das ursprüngliche Core ML-Modell ein Bild ausgibt, wandeln Sie die Gleitkommaausgabetensoren von ONNX manuell in Bilder um.</span><span class="sxs-lookup"><span data-stu-id="44e80-140">If the original Core ML model outputs an image, manually convert ONNX's floating-point output tensors back into images.</span></span> <span data-ttu-id="44e80-141">Es gibt zwei grundlegende Schritte.</span><span class="sxs-lookup"><span data-stu-id="44e80-141">There are two basic steps.</span></span> <span data-ttu-id="44e80-142">Der erste Schritt besteht darin, Werte größer als 255 auf 255 zu verkürzen und alle negativen Werte auf 0 zu setzen.</span><span class="sxs-lookup"><span data-stu-id="44e80-142">The first step is to truncate values greater than 255 to 255 and change all negative values to 0.</span></span> <span data-ttu-id="44e80-143">Der zweite Schritt besteht darin, alle Pixelwerte auf ganze Zahlen zu runden (indem 0,5 addiert und dann die Dezimalstellen abgeschnitten werden).</span><span class="sxs-lookup"><span data-stu-id="44e80-143">The second step is to round all pixel values to integers (by adding 0.5 and then truncating the decimals).</span></span> <span data-ttu-id="44e80-144">Die Reihenfolge des Ausgabekanals (z. B. RGB oder BGR) ist im Core ML-Modell angegeben.</span><span class="sxs-lookup"><span data-stu-id="44e80-144">The output channel order (e.g., RGB or BGR) is indicated in the Core ML model.</span></span> <span data-ttu-id="44e80-145">Um eine korrekte Bildausgabe zu generieren, müssen wir möglicherweise transponieren oder mischen, um das gewünschte Format wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="44e80-145">To generate proper image output, we may need to transpose or shuffle to recover the desired format.</span></span>

<span data-ttu-id="44e80-146">Hier betrachten wir das Core ML-Modell „FNS-Candy”, heruntergeladen von [GitHub](https://github.com/likedan/Awesome-CoreML-Models), als ein konkretes Umwandlungsbeispiel, um den Unterschied zwischen ONNX- und Core ML-Formaten darzulegen.</span><span class="sxs-lookup"><span data-stu-id="44e80-146">Here we consider a Core ML model, FNS-Candy, downloaded from [GitHub](https://github.com/likedan/Awesome-CoreML-Models), as a concrete conversion example to demonstrate the difference between ONNX and Core ML formats.</span></span> <span data-ttu-id="44e80-147">Beachten Sie, dass alle nachfolgenden Befehle in einer Python-Umgebung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="44e80-147">Note that all the subsequent commands are executed in a python enviroment.</span></span>

<span data-ttu-id="44e80-148">Zunächst laden wir das Core ML-Modell und untersuchen seine Eingabe- und Ausgabeformate.</span><span class="sxs-lookup"><span data-stu-id="44e80-148">First, we load the Core ML model and examine its input and output formats.</span></span>

~~~python
from coremltools.models.utils import load_spec
model_coreml = load_spec('FNS-Candy.mlmodel')
model_coreml.description # Print the content of Core ML model description
~~~

<span data-ttu-id="44e80-149">Bildschirmausgabe:</span><span class="sxs-lookup"><span data-stu-id="44e80-149">Screen output:</span></span>

~~~
...
input {
    ...
      imageType {
      width: 720
      height: 720
      colorSpace: BGR
    ...
}
...
output {
    ...
      imageType {
      width: 720
      height: 720
      colorSpace: BGR
    ...
}
...
~~~

<span data-ttu-id="44e80-150">In diesem Fall handelt es sich bei Eingabe und Ausgabe um ein 720x720-BGR-Bild.</span><span class="sxs-lookup"><span data-stu-id="44e80-150">In this case, both the input and output are 720x720 BGR-image.</span></span> <span data-ttu-id="44e80-151">Unser nächster Schritt besteht darin, das Core ML-Modell mit WinMLTools zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="44e80-151">Our next step is to convert the Core ML model with WinMLTools.</span></span>

~~~python
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from onnxmltools import convert_coreml
model_onnx = convert_coreml(model_coreml, name='FNSCandy')    
~~~

<span data-ttu-id="44e80-152">Eine alternative Methode zum Anzeigen der Eingabe- und Ausgabeformate des Modells in ONNX ist die Verwendung des folgenden Befehls:</span><span class="sxs-lookup"><span data-stu-id="44e80-152">An alternative method to view the model input and output formats in ONNX, is to use the following command:</span></span>

~~~python
model_onnx.graph.input # Print out the ONNX input tensor's information
~~~

<span data-ttu-id="44e80-153">Bildschirmausgabe:</span><span class="sxs-lookup"><span data-stu-id="44e80-153">Screen output:</span></span>

~~~
...
  tensor_type {
    elem_type: FLOAT
    shape {
      dim {
        dim_param: "None"
      }
      dim {
        dim_value: 3
      }
      dim {
        dim_value: 720
      }
      dim {
        dim_value: 720
      }
    }
  }
...
~~~

<span data-ttu-id="44e80-154">Die erzeugten Eingabe (gekennzeichnet durch *X*) in ONNX ist ein 4-D-Tensor.</span><span class="sxs-lookup"><span data-stu-id="44e80-154">The produced input (denoted by *X*) in ONNX is a 4-D tensor.</span></span> <span data-ttu-id="44e80-155">Die letzten 3 Achsen sind C-, H- und W-Achsen.</span><span class="sxs-lookup"><span data-stu-id="44e80-155">The last 3 axes are C-, H-, and W-axes, respectively.</span></span> <span data-ttu-id="44e80-156">Die erste Dimension ist „None”, was bedeutet, dass dieses ONNX-Modell auf eine beliebige Anzahl von Bildern angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="44e80-156">The first dimension is "None" which means that this ONNX model can be applied to any number of images.</span></span> <span data-ttu-id="44e80-157">Bei der Verarbeitung von 2 Bildern mit diesem Modell entspricht das erste Bild *X*[0, :, :, :], während *X*[1, :, :, :] dem zweiten Bild entspricht.</span><span class="sxs-lookup"><span data-stu-id="44e80-157">To apply this model to process a batch of 2 images, the first image corresponds to *X*[0, :, :, :] while *X*[1, :, :, :] corresponds to the second image.</span></span> <span data-ttu-id="44e80-158">Die Kanäle Blau/Grün/Rot des ersten Bilds sind *X*[0, 0, :, :]/*X*[0, 1, :, :]/*X*[0, 2, :, :]. Entsprechendes gilt für das zweite Bild.</span><span class="sxs-lookup"><span data-stu-id="44e80-158">The blue/green/red channels of the first image are *X*[0, 0, :, :]/*X*[0, 1, :, :]/*X*[0, 2, :, :], and similar for the second image.</span></span>

~~~python
model_onnx.graph.output # Print out the ONNX output tensor's information
~~~

<span data-ttu-id="44e80-159">Bildschirmausgabe:</span><span class="sxs-lookup"><span data-stu-id="44e80-159">Screen output:</span></span>

~~~
...
  tensor_type {
    elem_type: FLOAT
    shape {
      dim {
        dim_param: "None"
      }
      dim {
        dim_value: 3
      }
      dim {
        dim_value: 720
      }
      dim {
        dim_value: 720
      }
    }
  }
...
~~~

<span data-ttu-id="44e80-160">Wie Sie sehen, ist das produzierte Format mit dem ursprünglichen Modelleingabeformat identisch.</span><span class="sxs-lookup"><span data-stu-id="44e80-160">As you can see, the produced format is identical to the original model input format.</span></span> <span data-ttu-id="44e80-161">Allerdings handelt es sich in diesem Fall nicht um ein Bild, da die Pixelwerte ganze Zahlen und keine Fließkommazahlen sind.</span><span class="sxs-lookup"><span data-stu-id="44e80-161">However, in this case, it's not an image because the pixel values are integers, not floating-point numbers.</span></span> <span data-ttu-id="44e80-162">Um zurück in ein Bild zu konvertieren, verkürzen Sie Werte größer als 255 auf 255, ändern Sie die negativen Werte in 0, und runden Sie alle Dezimalzahlen auf Ganzzahlen.</span><span class="sxs-lookup"><span data-stu-id="44e80-162">To convert back to an image, truncate values greater than 255 to 255, change negative values to 0, and round all decimals to integers.</span></span>