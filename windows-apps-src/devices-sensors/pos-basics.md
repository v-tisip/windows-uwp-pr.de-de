---
author: TerryWarwick
title: Erste Schritte mit Point Of Service-Geräten
description: Dieser Artikel enthält Informationen für die ersten Schritte mit PointOfService-UWP-Apps.
ms.author: jken
ms.date: 05/1/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: a0583adbcef9e45dfe0b2e56e03ce7e0451ac5bb
ms.sourcegitcommit: ce45a2bc5ca6794e97d188166172f58590e2e434
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "1983543"
---
# <a name="getting-started-with-point-of-service"></a>Erste Schritte mit Point Of Service-Geräten

Dieser Abschnitt enthält Themen, die für alle Point of Service-Gerätekategorien gleich sind.

|Thema |Beschreibung |
|------|------------|
| [Funktionsdeklaration](pos-basics-capability.md)      | Erfahren Sie, wie Sie die Funktion **pointOfService** zu Ihrem Anwendungsmanifest hinzufügen.  Diese Funktion wird für die Verwendung des Windows.Devices.PointOfService-Namespace benötigt.  |
| [Enumerieren von Geräten](pos-basics-enumerating.md)        | Erfahren Sie, wie Sie eine Geräteauswahl definieren, die verwendet wird, um die im System verfügbaren Geräte abzufragen, und verwenden diese Auswahl, um Point of Service-Geräte aufzulisten.  |
| [Erstellen eines Geräteobjekts](pos-basics-deviceobject.md)  | Erfahren Sie, wie Sie ein PointOfService-Geräteobjekt erstellen, das Ihnen den Zugriff auf schreibgeschützte Eigenschaften des Peripheriegeräts und die Beanspruchung der exklusiven Nutzung des Peripheriegeräts ermöglicht. |
| [Beanspruchung der exklusiven Nutzung eines Geräts ](pos-basics-claim.md)  | Erfahren Sie, wie Sie mit dem PointOfService-Anspruchsmodell die exklusive Nutzung eines PointOfService-Peripheriegeräts reservieren, während gleichzeitig andere Anwendungen auf demselben Computer auf das PointOfService-Peripheriegerät zugreifen können, wenn sie eine exklusive Nutzung benötigen.  |
|

## <a name="see-also"></a>Weitere Informationen
[Erste Schritte mit Windows.Devices.PointOfService](pos-get-started.md)


## <a name="sample-code"></a>Beispielcode
+ [Beispiel für Strichcodescanner](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BarcodeScanner)
+ [Beispiel für Kassenschubladen]( https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CashDrawer)
+ [Beispiel für Zeilenanzeigen](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/LineDisplay)
+ [Beispiel für Magnetstreifenleser](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MagneticStripeReader)
+ [Beispiel für POS-Drucker](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/PosPrinter)

