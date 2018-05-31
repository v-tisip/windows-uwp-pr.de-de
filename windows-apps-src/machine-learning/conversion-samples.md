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
ms.openlocfilehash: 882efca26730c990093a89a5ed3ff4b5587e05bf
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832678"
---
# <a name="convert-existing-ml-models-to-onnx"></a>Konvertieren vorhandener ML-Modelle in ONNX

[WinMLTools](https://aka.ms/winmltools) ermöglicht es Benutzern, in anderen Frameworks trainierte Modelle in das ONNX Format zu konvertieren. Hier zeigen wir Ihnen, wie Sie das WinMLTools-Paket installieren und vorhandene Modelle in scikit-learn und Core ML mit Python-Code in ONNX konvertieren.

## <a name="install-winmltools"></a>Installieren der WinMLTools

WinMLTools ist ein Python-Paket (winmltools), das die Python-Versionen 2.7 und 3.6 unterstützt. Wenn Sie an einem Projekt mit wissenschaftlichen Daten arbeiten, empfehlen wir die Installation einer wissenschaftlichen Python-Distribution wie Anaconda.

WinMLTools folgt dem [standardmäßigen Installationsvorgang für Python-Pakete](https://packaging.python.org/installing/). Führen Sie in Ihrer Python-Umgebung Folgendes aus:

```
pip install winmltools
```

Für WinMLTools gelten die folgenden Abhängigkeiten:

- numpy v1.10.0+
- onnxmltools 0.1.0.0+
- protobuf v.3.1.0+

Um die abhängigen Pakete zu aktualisieren, führen Sie den pip-Befehl mit dem Argument '-U' aus.

```
pip install -U winmltools
```

Weitere Informationen zu onnxmltools-Abhängigkeiten finden Sie unter [onnxmltools](https://github.com/onnx/onnxmltools) auf GitHub.

Weitere Details zur Verwendung von WinMLTools finden Sie in der paketspezifischen Dokumentation über die Hilfefunktion.

```
help(winmltools)
```

## <a name="scikit-learn-models"></a>Scikit-learn-Modelle

Das folgende Code-Snippet trainiert eine lineare Support Vector Machine in scikit-learn und konvertiert das Modell in ONNX.

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

Benutzer können `LinearSVC` durch andere scikit-learn-Modelle wie `RandomForestClassifier` ersetzen. Beachten Sie, dass der [automatische Codegenerator](overview.md#automatic-interface-code-generation) die `name`-Parameter verwendet, um Klassennamen und Variablen zu generieren. Wird `name` nicht angegeben wird, wird eine GUID generiert, die nicht den Benennungskonventionen für Sprachen wie C++ und C # entspricht. 

## <a name="scikit-learn-pipelines"></a>Scikit-learn-Pipelines

Als nächstes zeigen wir, wie scikit-learn-Pipelines in ONNX konvertiert werden können.

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

## <a name="core-ml-models"></a>Core ML-Modelle

Hier gehen wird davon aus, dass *example.mlmodel* der Pfad zu einer Beispieldatei mit einem Core ML-Modell ist.

~~~python
from coremltools.models.utils import load_spec
# Load model file
model_coreml = load_spec('example.mlmodel')
from winmltools import convert_coreml
# Convert it!
# The automatic code generator (mlgen) uses the name parameter to generate class names.
model_onnx = convert_coreml(model_coreml, name='ExampleModel')   
~~~

`model_onnx` ist ein [ModelProto](https://github.com/onnx/onnxmltools/blob/0f453c3f375c1ae928b83a4c7909c82c013a5bff/onnxmltools/proto/onnx-ml.proto#L176)-Objekt von ONNX. Wir können es in zwei verschiedenen Formaten speichern.

~~~python
from winmltools.utils import save_model
# Save the produced ONNX model in binary format
save_model(model_onnx, 'example.onnx')
# Save the produced ONNX model in text format
from winmltools.utils import save_text
save_text(model_onnx, 'example.txt')
~~~

**Hinweis:**: CoreMLTools ist ein Python-Paket, das von Apple bereitgestellt wird, aber unter Windows nicht verfügbar ist. Wenn Sie das Paket unter Windows installieren müssen, installieren Sie das Paket direkt aus dem Repository:

```
pip install git+https://github.com/apple/coremltools
```

## <a name="core-ml-models-with-image-inputs-or-outputs"></a>Core ML-Modelle mit Bildern als Ein- oder Ausgaben

Aufgrund fehlender Bildtypen in ONNX erfordert das Umwandeln von Core ML-Bildmodellen (Modelle, die Bilder als Eingaben oder Ausgaben verwenden) einige Vor- und Nachverarbeitungsschritte.

Das Ziel der Vorverarbeitung ist sicherzustellen, dass ein Eingabebild korrekt als ONNX-Tensor formatiert ist. Nehmen wir an, *X* ist eine Bildeingabe der Form [C, H, W] in Core ML. In ONNX wäre die Variable *X* ein Gleitkommatensor mit der gleichen Form, und *X*[0, :, :]/*X*[1, :, :]/*X*[2, :, :] würde den Rot/Grün/Blau-Kanal des Bilds enthalten. Die Formate für Graustufenbilder in Core ML sind [1, H, W]-Tensoren in ONNX, da es nur einen Kanal gibt.

Wenn das ursprüngliche Core ML-Modell ein Bild ausgibt, wandeln Sie die Gleitkommaausgabetensoren von ONNX manuell in Bilder um. Es gibt zwei grundlegende Schritte. Der erste Schritt besteht darin, Werte größer als 255 auf 255 zu verkürzen und alle negativen Werte auf 0 zu setzen. Der zweite Schritt besteht darin, alle Pixelwerte auf ganze Zahlen zu runden (indem 0,5 addiert und dann die Dezimalstellen abgeschnitten werden). Die Reihenfolge des Ausgabekanals (z. B. RGB oder BGR) ist im Core ML-Modell angegeben. Um eine korrekte Bildausgabe zu generieren, müssen wir möglicherweise transponieren oder mischen, um das gewünschte Format wiederherzustellen.

Hier betrachten wir das Core ML-Modell „FNS-Candy”, heruntergeladen von [GitHub](https://github.com/likedan/Awesome-CoreML-Models), als ein konkretes Umwandlungsbeispiel, um den Unterschied zwischen ONNX- und Core ML-Formaten darzulegen. Beachten Sie, dass alle nachfolgenden Befehle in einer Python-Umgebung ausgeführt werden.

Zunächst laden wir das Core ML-Modell und untersuchen seine Eingabe- und Ausgabeformate.

~~~python
from coremltools.models.utils import load_spec
model_coreml = load_spec('FNS-Candy.mlmodel')
model_coreml.description # Print the content of Core ML model description
~~~

Bildschirmausgabe:

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

In diesem Fall handelt es sich bei Eingabe und Ausgabe um ein 720x720-BGR-Bild. Unser nächster Schritt besteht darin, das Core ML-Modell mit WinMLTools zu konvertieren.

~~~python
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from onnxmltools import convert_coreml
model_onnx = convert_coreml(model_coreml, name='FNSCandy')    
~~~

Eine alternative Methode zum Anzeigen der Eingabe- und Ausgabeformate des Modells in ONNX ist die Verwendung des folgenden Befehls:

~~~python
model_onnx.graph.input # Print out the ONNX input tensor's information
~~~

Bildschirmausgabe:

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

Die erzeugten Eingabe (gekennzeichnet durch *X*) in ONNX ist ein 4-D-Tensor. Die letzten 3 Achsen sind C-, H- und W-Achsen. Die erste Dimension ist „None”, was bedeutet, dass dieses ONNX-Modell auf eine beliebige Anzahl von Bildern angewendet werden kann. Bei der Verarbeitung von 2 Bildern mit diesem Modell entspricht das erste Bild *X*[0, :, :, :], während *X*[1, :, :, :] dem zweiten Bild entspricht. Die Kanäle Blau/Grün/Rot des ersten Bilds sind *X*[0, 0, :, :]/*X*[0, 1, :, :]/*X*[0, 2, :, :]. Entsprechendes gilt für das zweite Bild.

~~~python
model_onnx.graph.output # Print out the ONNX output tensor's information
~~~

Bildschirmausgabe:

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

Wie Sie sehen, ist das produzierte Format mit dem ursprünglichen Modelleingabeformat identisch. Allerdings handelt es sich in diesem Fall nicht um ein Bild, da die Pixelwerte ganze Zahlen und keine Fließkommazahlen sind. Um zurück in ein Bild zu konvertieren, verkürzen Sie Werte größer als 255 auf 255, ändern Sie die negativen Werte in 0, und runden Sie alle Dezimalzahlen auf Ganzzahlen.