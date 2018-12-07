---
title: Tools für die Grafikdiagnose
description: Hier erfahren Sie, wie Sie in Visual Studio die Grafikdiagnosefeatures, einschließlich Grafikdebugging, Analyse von Grafikframes und GPU-Verwendung, abrufen und verwenden.
ms.assetid: 629ea462-18ed-a333-07e9-cc87ea2dcd93
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Grafiken, Diagnose, Tools, directx
ms.localizationpriority: medium
ms.openlocfilehash: f9fc1f6fa28fa36c876517eb0653693c670282ff
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8798062"
---
# <a name="graphics-diagnostics-tools"></a>Tools für die Grafikdiagnose



Mit Windows 10 sind die Grafiken Diagnosetools nun als optionales Feature in Windows zur Verfügung. Installieren Sie das optionale Grafiktoolfeature, um die in der Runtime und in VisualStudio bereitgestellten Grafikdiagnosefeatures für die Entwicklung von DirectX-Apps oder -Spielen zu nutzen:

1.  Wechseln Sie zu **Einstellungen**, wählen Sie **Apps**, und klicken Sie dann auf **optionale Features verwalten**.
2.  Klicken Sie auf **Feature hinzufügen**.   
3.  Wählen Sie in der Liste **Optionale Features** **Grafiktools** aus, und klicken Sie dann auf **Installieren**.

Die Grafikdiagnosefeatures ermöglichen das Erstellen von Direct3D-Debugging-Geräten (über Direct3D-SDK-Ebenen) in der DirectX-Runtime sowie das Grafikdebugging, die Frame-Analyse und die GPU-Verwendung.

-   Mit dem Grafikdebugging können Sie Direct3D-Aufrufe Ihrer App nachverfolgen. Anschließend können Sie diese Aufrufe wiedergeben, Parameter untersuchen, Shader debuggen und mit ihnen experimentieren sowie Grafikobjekte visualisieren, um Renderingprobleme zu diagnostizieren. Protokolle können auf Windows-PCs, in Simulatoren oder auf Geräten erstellt und auf anderer Hardware wiedergegeben werden.
-   Die Analyse von Grafikframes in VisualStudio wird für ein Grafikdebuggingprotokoll ausgeführt und erfasst Details der Grundlinienzeitsteuerung für die Direct3D-Draw-Aufrufe. Anschließend führt sie eine Reihe von Versuchen aus, indem sie verschiedene Grafikeinstellungen ändert, und generiert eine Tabelle der Zeitsteuerungsergebnisse. Diese Daten können Aufschluss über Probleme mit der Grafikleistung Ihrer App geben, und anhand der Ergebnisse der verschiedenen Versuche können Sie feststellen, wie sich die Leistung verbessern lässt.
-   Anhand der GPU-Verwendung in VisualStudio können Sie die GPU-Verwendung in Echtzeit überwachen. Sie erfasst und analysiert die Zeitdaten der Arbeitsauslastungen, die von der CPU und GPU verarbeitet werden, und ermöglicht so die Erkennung von Engpässen.

## <a name="related-topics"></a>Verwandte Themen


[Übersicht über die Grafikdiagnose in Visual Studio](http://go.microsoft.com/fwlink/p/?LinkID=526382)

 

 




