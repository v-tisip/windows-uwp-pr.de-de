---
title: "Vorgänge für Kachelpools"
description: "Vorgänge für Kachelpools umfassen das Ändern der Größe eines Kachelpools, das Anbieten von Ressourcen (Gewinnen von vorübergehendem Speicherplatz für das System für den gesamten Kachelpool) und das Zurückfordern von Ressourcen."
ms.assetid: 90347F7F-C991-4287-BD70-494533ECDC8A
keywords: "Vorgänge für Kachelpools"
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: e144b42782f8479bc55dc22f8505c7cfa4455713
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="operations-available-on-tile-pools"></a>Vorgänge für Kachelpools


Vorgänge für Kachelpools umfassen das Ändern der Größe eines Kachelpools, das Anbieten von Ressourcen (Gewinnen von vorübergehendem Speicherplatz für das System für den gesamten Kachelpool) und das Zurückfordern von Ressourcen.

-   Die Lebensdauer von Kachelpools funktioniert wie jede andere Direct3D-Ressource, die mittels Referenzzählung gesichert ist, in diesem Fall einschließlich der Nachverfolgung von Zuordnungen von Streaming-Ressourcen. Wenn die Anwendung nicht mehr auf einen Kachelpool verweist und alle Kachelzuordnungen auf den Speicher nicht mehr vorhanden sind und die Zugriffe durch den Grafikprozessor (GPU) abgeschlossen sind, wird das Betriebssystem die Zuordnung des Kachelpools aufheben.
-   API, die im Zusammenhang mit der gemeinsamen Nutzung und Synchronisierung von Oberflächen stehen, funktionieren für Kachelpools (jedoch nicht direkt auf Streaming-Ressourcen). Ähnlich wie das Verhalten für angebotene Kachelpools werden Direct3D-Befehle, die auf Streaming-Ressourcen zugreifen, die auf einen Kachelpool verweisen, gelöscht, wenn die Kachelpool freigegeben wurde und derzeit von einem anderen Gerät und Prozess erworben wird.
-   Ändern der Größe eines Kachelpools.
-   Anbieten von Ressourcen und Zurückfordern von Ressourcen - diese Vorgänge zum Gewinnen von vorübergehendem Speicherplatz für das System wirken auf den gesamten Kachelpool (und sind nicht für einzelne Streaming-Ressourcen verfügbar). Verweist eine Streaming-Ressource auf eine Kachel in einem angebotenen Kachelpool, verhält sich die Streaming-Ressource als würde sie angeboten (z. B. die Runtime löscht Befehle, die darauf verweisen).

Daten können nicht direkt in den und aus dem Kachelpoolspeicher kopiert werden. Zugriffe auf den Speicher erfolgen immer über Streaming-Ressourcen.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Erstellen von Streaming-Ressourcen](creating-streaming-resources.md)

 

 




