---
author: TerryWarwick
title: Erste Schritte mit Point Of Service-Geräten
description: Dieser Artikel enthält Informationen für die ersten Schritte mit PointOfService-UWP-Apps.
ms.author: jken
ms.date: 06/13/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 46dd1f615e42f6e89ee9a92cb980299e9a0e5205
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7151837"
---
# <a name="getting-started-with-point-of-service"></a>Erste Schritte mit Point Of Service-Geräten

## <a name="pointofservice-basics"></a>PointOfService-Grundlagen

Dieser Abschnitt enthält Themen, die für alle Point of Service-Gerätekategorien gleich sind.

|Thema |Beschreibung |
|------|------------|
| [Funktionsdeklaration](pos-basics-capability.md)      | Erfahren Sie, wie Sie die Funktion **pointOfService** zu Ihrem Anwendungsmanifest hinzufügen.  Diese Funktion wird für die Verwendung des Windows.Devices.PointOfService-Namespace benötigt.  |
| [Enumerieren von Geräten](pos-basics-enumerating.md)        | Erfahren Sie, wie Sie eine Geräteauswahl definieren, die verwendet wird, um die im System verfügbaren Geräte abzufragen, und verwenden diese Auswahl, um Point of Service-Geräte aufzulisten.  |
| [Erstellen eines Geräteobjekts](pos-basics-deviceobject.md)  | Erfahren Sie, wie Sie ein PointOfService-Geräteobjekt erstellen, das Ihnen den Zugriff auf schreibgeschützte Eigenschaften des Peripheriegeräts und die Beanspruchung der exklusiven Nutzung des Peripheriegeräts ermöglicht. |
| [Anspruch und aktivieren ](pos-basics-claim.md)  | Informationen Sie zum Reservieren eines PointOfService-Peripheriegeräts für die exklusive Nutzung und für e/a-Vorgänge zu aktivieren.  |
| [Freigeben von Peripheriegeräten für andere Personen](pos-basics-sharing.md) | Erfahren Sie mehr über das Netzwerk oder verbundenen Bluetooth-Peripheriegeräte mit anderen Computern in einer Umgebung Teilen, in denen mehrere PCs auf Peripheriegeräte anstatt dedizierten auf jeden Computer angeschlossenen Peripheriegeräte angewiesen sind.
| [PointOfService-End-to-end](pos-get-started.md)  | Dies ist ein End-to-End-Beispiel zum PointOfService-Peripheriegeräte unter Verwendung der obigen Beispielen interagieren. |
|

## <a name="see-also"></a>Weitere Informationen:

| Thema   | Beschreibung |
|:--------|:------------|
| [Anwendung Verteilung](../publish/distribute-lob-apps-to-enterprises.md) | Informationen Sie zu den Optionen für Ihre app an Unternehmenskunden verteilen. |
| [App-Lebenszyklus](../launch-resume/app-lifecycle.md) | Erfahren Sie mehr über den Lebenszyklus einer UWP-Anwendung und was geschieht, wenn Windows startet, anhält und Ihrer app fortgesetzt. |
| [Anwendungsressourcen](../app-resources/index.md) | Enthält Informationen zum Erstellen, Paket, und nutzen, String, Bild- und Dateiressourcen Ihrer app. |
| [Datenbindung](../data-binding/index.md) | Erfahren Sie, wie Sie die Datenbindung verwenden, um Daten in der Benutzeroberfläche Ihrer app anzeigen. |
| [Geräteenumeration](enumerate-devices.md) | Hier erfahren Sie verwenden erweiterter Enumeration Techniken, um Peripheriegeräte zu suchen.|
| [Adaptive Applications Version](../debug-test-perf/version-adaptive-apps.md) | Erläutert, wie Ihre app so entwerfen, dass sie auf mehrere Versionen von Windows 10 ausgeführt wird.|
|


## <a name="sample-code"></a>Beispielcode
+ [Beispiel für Strichcodescanner](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BarcodeScanner)
+ [Beispiel für Kassenschubladen]( https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CashDrawer)
+ [Beispiel für Zeilenanzeigen](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/LineDisplay)
+ [Beispiel für Magnetstreifenleser](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MagneticStripeReader)
+ [Beispiel für POS-Drucker](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/PosPrinter)

