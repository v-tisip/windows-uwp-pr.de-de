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
ms.openlocfilehash: 2ef6ea1a4e1dab23f5ff6a09aec9b8c49c135f5e
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1817661"
---
# <a name="windows-ml-overview"></a>Übersicht über Windows ML

![Grafik zu Windows Machine Learning](images/brain.png)

## <a name="what-is-machine-learning"></a>Was ist Machine Learning?

Machine Learning (ML) ermöglicht Computern die Verwendung vorhandener Daten, um erwartete Ergebnisse und Verhaltensweisen vorherzusagen. Durch die Verarbeitung zuvor gesammelter Daten erstellen ML-Algorithmen Modelle, die die korrekte Ausgabe bei einer neuen Eingabe vorhersagen können. Ein Modell kann beispielsweise so trainiert werden, dass E-Mail-Nachrichten (Eingabe) als Spam bzw. nicht als Spam (Ausgabe) ausgewertet werden.

Die Modellerstellungsphase wird als „Training“ bezeichnet. Sobald das Modell mit vorhandenen Daten trainiert wurde, kann es Vorhersagen mit neuen, zuvor nicht sichtbaren Daten treffen, was als "Rückschluss", "Auswertung" oder "Bewertung" bezeichnet wird.

Trainierte Modelle erzeugen oft bessere Ergebnisse als Programme, die für die Befolgung strenger Anweisungen geschrieben wurden, insbesondere für komplexe Aufgaben mit vielen Kombinationsmöglichkeiten von Ein- und Ausgaben. Empfehlungsalgorithmen stellen beispielsweise personalisierte Empfehlungen für Millionen von Benutzern auf E-Commerce- und Medienstreaming-Websites bereit, was ohne Machine Learning nahezu unmöglich wäre. Ein weiterer Bereich, der Machine Learning nutzt, ist Computer-Vision, die Computern die Klassifizierung und Identifizierung von Bildern nach dem Training für zuvor beschriftete Bilder ermöglicht.

Die Möglichkeiten und Anwendungen von Machine Learning sind endlos. Weitere Informationen zu Forschung und Lösungen finden Sie unter [Künstliche Intelligenz bei Microsoft](https://www.microsoft.com/ai) und [Microsoft AI-Plattform](https://azure.microsoft.com/en-us/overview/ai-platform/). Falls Sie Machine Learning- und AI-Modelle erstellen möchten, erhalten Sie weitere Informationen auch unter [Azure Machine Learning Services](https://docs.microsoft.com/azure/machine-learning/preview/overview-what-is-azure-ml).

## <a name="what-is-windows-ml"></a>Was ist Windows ML?

Windows ML ist eine Plattform, die trainierte Machine Learning-Modelle auf Windows10-Geräten auswertet. Dadurch können Entwickler Machine Learning in ihren Windows-Anwendungen verwenden.

Hier sind einige Highlights von Windows ML:

- **Hardwarebeschleunigung**
    
    Auf DirectX12-fähigen Geräten beschleunigt Windows ML die Auswertung von Deep Learning-Modellen mithilfe der GPU. Darüber hinaus ermöglichen CPU-Optimierungen eine leistungsstarke Auswertung klassischer ML- und Deep Learning-Algorithmen.

- **Lokale Auswertung**

    Windows ML wertet lokale Hardware aus, indem Probleme in Bezug auf Konnektivität, Bandbreite und Datenschutz beseitigt werden. Die lokale Auswertung ermöglicht zudem eine geringe Latenz und hohe Leistung für schnelle Bewertungsergebnisse.

- **Bildverarbeitung**

    Für Computer-Vision-Szenarien vereinfacht und optimiert Windows ML die Verwendung von Bild-, Video und Kameradaten, indem die Vorverarbeitung von Frames behandelt und die Einrichtung der Kamera-Pipeline für die Modelleingabe bereitgestellt wird.

## <a name="how-to-develop-with-windows-ml"></a>So entwickeln Sie mit Windows ML

> [!VIDEO https://www.youtube.com/embed/8MCDSlm326U]

### <a name="system-requirements"></a>Systemanforderungen

Um Anwendungen zu erstellen, die Windows ML verwenden, benötigen Sie das [Windows SDK – Build 17110 oder höher](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK).

### <a name="onnx-models"></a>ONNX-Modelle

Zur Verwendung von Windows ML benötigen Sie ein vorab trainiertes Machine Learning-Modell im [Open Neural Network Exchange (ONNX)](https://onnx.ai)-Format. Windows ML unterstützt die v1.0-Version des ONNX-Formats, das Entwicklern die Verwendung von Modellen ermöglicht, die von verschiedenen Trainings-Frameworks erzeugt wurden.

Eine Liste der öffentlich verfügbaren ONNX-Modelle finden Sie unter [ONNX-Modelle](https://github.com/onnx/models) auf GitHub.

Weitere Informationen zum Trainieren eines ONNX-Modells mit Visual Studio Tools for AI finden Sie unter [Trainieren eines Modells](train-ai-model.md).

### <a name="convert-existing-models-to-onnx"></a>Konvertieren vorhandener Modelle in ONNX

Viele Trainings-Frameworks unterstützen ONNX-Modelle bereits nativ. Zudem sind Konverter-Tools für viele Frameworks und Bibliotheken verfügbar. Weitere Informationen zum Exportieren aus Frameworks wie Caffe 2, PyTorch, CNTK, Chainer usw. finden Sie unter [ONNX tutorials](https://github.com/onnx/tutorials) auf GitHub.

Sie können auch [WinMLTools](https://pypi.org/project/winmltools/) verwenden, um trainierte Machine Learning-Modelle in das von Windows ML akzeptierte ONNX-Format zu konvertieren. WinMLTools unterstützt die Konvertierung aus den folgenden Formaten:

- Core ML
- Scikit-Learn
- XGBoost
- LibSVM

Weitere Informationen zum Installieren und Verwenden von WinMLTools finden Sie unter [Konvertieren eines Modells](conversion-samples.md).

### <a name="onnx-operators"></a>ONNX-Operatoren

Windows ML unterstützt 100+ ONNX-Operatoren auf der CPU und beschleunigt die Berechnung auf GPUs, die mit DirectX12 kompatibel sind. Eine vollständige Liste der Operator-Signaturen finden Sie in der Dokumentation zu ONNX-Operatorenschemas für die Namespaces [ai.onnx](https://github.com/onnx/onnx/blob/rel-1.0/docs/Operators.md) (Standard) und [ai.onnx.ml](https://github.com/onnx/onnx/blob/rel-1.0/docs/Operators-ml.md).

Windows ML unterstützt alle in der Dokumentation zu ONNX v1. 0 definierten Operatoren mit den folgenden Unterschieden:

- Als "experimentell"gekennzeichnete Operatoren, die von Windows ML unterstützt werden:
    - Affine
    - Crop
    - FC
    - Identität
    - ImageScaler
    - MeanVarianceNormalization
    - ParametricSoftplus
    - ScaledTanh
    - ThresholdedRelu
    - Upsample
- MatMul – größer als 2D Matrixmultiplikation wird derzeit nicht unterstützt, ausgenommen auf CPU
- Cast – nur auf CPU unterstützt
- Die folgenden Operatoren werden derzeit nicht unterstützt:
    - RandomUniform
    - RandomUniformLike
    - RandomNormal
    - RandomNormalLike

### <a name="automatic-interface-code-generation"></a>Automatische Generierung von Schnittstellencode

Mit einer ONNX-Modelldatei erstellt der Code-Generator von Windows ML eine Schnittstelle für die Interaktion mit dem Modell in Ihrer App. Die generierte Schnittstelle enthält die Wrapper-Klassen, die das Modell, Eingaben und Ausgaben darstellen. Der generierte Code ruft die [Windows ML-API](/uwp/api/windows.ai.machinelearning.preview) automatisch ab, sodass Sie das Modell in Ihrem Projekt einfach laden, binden und auswerten können. Der Code-Generator unterstützt derzeit C# und C++/CX.

Für UWP-Entwickler ist der automatische Code-Generator von Windows ML systemintern in [Visual Studio (Version 15.7 – Preview 1)](https://www.visualstudio.com/vs/preview/) integriert. (**Hinweis**: In Visual Studio Installer müssen Sie das optionale Windows10 Insider Preview SDK, Build 17110, deaktivieren.) Im Visual Studio-Projekt fügen Sie Ihre ONNX-Datei einfach als vorhandenes Element hinzu, sodass VS Wrapper-Klassen von Windows ML in einer neuen Benutzeroberflächendatei generiert.

Sie können auch das im Windows SDK enthaltene Befehlszeilentool `mlgen.exe` verwenden, um Wrapper-Klassen von Windows ML zu generieren. Das Tool befindet sich unter `(SDK_root)\bin\<version>\x64` oder `(SDK_root)\bin\<version>\x86`, wobei SDK_root das SDK-Installationsverzeichnis ist. Verwenden Sie zum Ausführen des Tools den nachstehenden Befehl.

```
mlgen -i INPUT-FILE -l LANGUAGE -n NAMESPACE [-o OUTPUT-FILE]
```

Definition des Eingabeparameters:

- `INPUT-FILE`: die ONNX-Modelldatei
- `LANGUAGE`: CPPCX oder CS
- `NAMESPACE`: der Namespace des generierten Codes
- `OUTPUT-FILE`: Pfad der Datei, in die der generierte Code geschrieben wird. Wenn keine AUSGABEDATEI angegeben ist, wird der generierte Code in die Standardausgabe geschrieben.

Weitere Informationen zum Verwenden des generierten Codes in Ihrer App finden Sie unter [Integrieren eines Modells](integrate-model.md).

## <a name="next-steps"></a>Nächste Schritte

Versuchen Sie, Ihre erste Windows ML-App anhand einer ausführlichen Anleitung unter [Erste Schritt](get-started.md) zu erstellen.