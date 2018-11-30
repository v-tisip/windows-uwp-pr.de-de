---
title: Geräte
description: Ein Direct3D-Gerät ist die Komponente zum Rendern von Direct3D. Ein Gerät kapselt und speichert den Renderzustand, führt Transformationen und Beleuchtungsvorgänge aus und rastert ein Bilds auf einer Oberfläche.
ms.assetid: BC903462-A32A-46BA-8411-FB294F5D2CD9
keywords:
- Geräte
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9e49a9dcaa2638065946f01797cbea084a1432a6
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8205215"
---
# <a name="devices"></a>Geräte


Ein Direct3D-Gerät ist die Komponente zum Rendern von Direct3D. Ein Gerät kapselt und speichert den Renderzustand, führt Transformationen und Beleuchtungsvorgänge aus und rastert ein Bilds auf einer Oberfläche.

Wie im folgenden Diagramm dargestellt, umfasst die Architektur von Direct3D-Geräten ein Tranformationsmodul, Beleuchtungsmoduls und ein Rastermodul.

![Diagramm der Architektur eines Direct3D-Gerätes](images/d3ddev.png)

Direct3D unterstützt zwei Hauptarten von Direct3D-Geräten:

-   Ein HAL-Gerät mit einer hardwarebeschleunigten Rasterung und Schattierung mit Hardware und Software-Vertex-Verarbeitung
-   Ein Referenzgerät

Diese Geräte stellen zwei separate Treiber dar. Software- und Referenzgeräte sind Softwaretreiber. Das HAL-Gerät ist ein Hardwaretreiber. Normalerweise wird das HAL-Geräte für die fertige Anwendung und das Referenzgerät zum Testen genutzt. Diese werden durch Drittanbieter für die Emulation von bestimmten Geräten bereitgestellt (beispielsweise noch nicht veröffentlichte Entwicklerhardware).

Das von einer Anwendung erstellte Direct3D-Gerät muss den Funktionalitäten der Hardware entsprechen, auf der die Anwendung ausgeführt wird. Direct3D stellt die Renderingfunktionen entweder über den Zugriff auf die im Computer installierte 3D-Hardware, oder über die Emulation der Funktionalitäten der 3D-Hardware per Software bereit. Aus diesem Grund stellt Direct3D Geräte für den Hardwarezugriff und zur Softwareemulation bereit.

Hardwarebeschleunigte Geräte bieten eine wesentlich bessere Leistung als Softwaregeräte. Der HAL-Gerätetyp steht auf allen von Direct3D unterstützten Grafikkarten zur Verfügung. In den meisten verfügen die Zielcomputer für die Anwendungen über eine Hardwarebeschleunigung. Computer mit weniger Leistung sind hingegen von der Softwareemulation abhängig.

Mit Ausnahme des Referenzgeräts unterstützen Softwaregeräte nicht immer die gleichen Funktionen wie ein Hardwaregerät. Anwendungen sollten daher immer die Gerätefunktionen Abfragen und so die unterstützten Funktionen ermitteln.

Da das Verhalten der Software- und Referenzgeräte von Direct3D9 dem des HAL-Gerätes identisch ist, funktioniert für das HAL-Gerät erstellter Anwendungscode ohne Änderungen auch mit den Software- und Referenzgeräten. Das Verhalten des Software- oder Referenzgeräts ist mit dem des HAL-Gerätes identisch. Die Gerätefunktionalitäten können jedoch abweichen. Vor allem das Softwaregerät implementiert möglicherweise erheblich weniger Funktionen.

## <a name="span-idin-this-sectionspanin-this-section"></a><span id="in-this-section"></span>Inhalt dieses Abschnitts


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Thema</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="device-types.md">Gerätetypen</a></p></td>
<td align="left"><p>Direct3D-Gerätetypen sind HAL-Gerät (Hardwareabstraktionsschicht) und den Referenz-Rasterizer.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="windowed-vs--full-screen-mode.md">Vergleich von Vollbild- und Fenstermodus</a></p></td>
<td align="left"><p>Direct3D-Anwendungen können entweder im Fenstermodus oder im Vollbildmodus ausgeführt werden. Im <em>Fenstermodus</em> teilt sich die Anwendung die verfügbare Bildschirmfläche auf dem Desktop mit allen anderen ausgeführten Programmen. Im <em>Vollbildmodus</em> deckt das Fenster der Anwendung den gesamten Desktop ab. Die ausgeführten Programme (einschließlich der Entwicklungsumgebung) sind nicht sichtbar.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="lost-devices.md">Lost-Zustand</a></p></td>
<td align="left"><p>Ein Direct3D-Gerät kann sich in einem Operational-Zustand oder Lost-Zustand befinden. Der Zustand <em>Operational</em> ist der normalen Zustand des Geräts. In diesem wird das Gerät ausgeführt die Renderingdarstellung läuft wie erwartet. Das Gerät wechselt zum <em>Lost</em>-Zustand sobald ein Ereignis, z.B. den Verlust des Tastaturfokus in einer Vollbildanwendung, auftritt und das Rendering somit unmöglich wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="swap-chains.md">Swapchains</a></p></td>
<td align="left"><p>Eine Swapchain ist eine Sammlung von Puffern, die zum Anzeigen von Frames für den Benutzer verwendet werden. Bei jeder Darstellung eines neuen Frames für eine Anzeige durch eine Anwendung wird der erste Puffer der Swapchain zum Anzeigepuffer. Dieser Prozess heißt <em>Swapping</em> bzw. <em>Flipping</em>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="introduction-to-rasterization-rules.md">Einführung in Rasterungsregeln</a></p></td>
<td align="left"><p>Häufig entsprechend die Punkte von Vertizes nicht exakt den Pixel auf dem Bildschirm. In diesem Fall nutzt Direct3D Dreieck-Rasterungsregeln, um zu entscheiden, welche Pixel für ein Dreieck genutzt werden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Direct3D-Grafik-Lernanleitung](index.md)

 

 




