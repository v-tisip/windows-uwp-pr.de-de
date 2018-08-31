---
author: Mtoepke
title: Systemressourcen für UWP-Apps und -Spiele auf der Xbox One
description: UWP auf Xbox-Systemressourcen
ms.author: mstahl
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 12e87019-4315-424e-b73c-426d565deef9
ms.localizationpriority: medium
ms.openlocfilehash: 8d6ebe8e3344f5276939471d7ac569ae83d48311
ms.sourcegitcommit: 1e5590dd10d606a910da6deb67b6a98f33235959
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "3241639"
---
# <a name="system-resources-for-uwp-apps-and-games-on-xbox-one"></a>Systemressourcen für UWP-Apps und -Spiele auf der Xbox One

Systemressourcen für UWP-Apps, die auf der Xbox One ausgeführt werden, teilen sich die Ressourcen mit dem System und anderen Apps. Welche Ressourcen für eine UWP-App auf Xbox One verfügbar sind, hängt davon ab, ob Sie diese als eine App oder ein Spiel im Xbox Live Creators-Programm übermitteln.

* Maximal verfügbarer Arbeitsspeicher für eine Ausführung im Vordergrund:
    * Apps: 1GB
    * Spiele: 5GB

Der maximal verfügbare Arbeitsspeicher für eine im Hintergrund ausgeführte App beträgt 128MB. Der Hintergrundmodus gilt nur für gleichzeitig ausgeführte Anwendungen, wie z.B. Apps zur Musikwiedergabe im Hintergrund.  Spiele werden angehalten und im Hintergrund beendet.

Durch eine Überschreitung dieser Einschränkungen treten Arbeitsspeicher-Zuweisungsfehler auf. Weitere Informationen zum Überwachen der Arbeitsspeicherverwendung finden Sie in der Referenz der [MemoryManager-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx).
    
    > [!NOTE]
    > When running your app or game from the Visual Studio debugger, these memory constraints do not apply. This limit is only applicable when not running in debugging mode.

* CPU
    * Apps: Gemeinsame Nutzung von 2 bis 4 CPU-Kernen, je nach Anzahl der auf dem System ausgeführten Apps und Spiele.
    * Spiele: 4 exklusiv und 2 gemeinsam genutzte CPU-Kerne.

* GPU
    * Apps: Gemeinsame Nutzung von 45% der GPU, je nach Anzahl der im System ausgeführten Apps und Spiele.
    * Spiele: Vollständiger Zugriff auf alle verfügbaren GPU-Zyklen.

* DirectX-Unterstützung
    * Apps: DirectX11 – Featureebene 10.
    * Spiele: DirectX12 und DirectX11 – Featureebene 10.

* Alle Apps und Spiele müssen auf der x64-Architektur ausgeführt werden können, um für Xbox entwickelt oder an den Store für Xbox übermittelt zu werden.  

Für **Anwendungsentwicklung** sind die verfügbaren Ressourcen im Vergleich zu einem Standard-PC möglicherweise beschränkt und können je nach Anzahl der auf dem System ausgeführten Apps und Spiele variieren.

Bei der **Spieleentwicklung** ist die Xbox One (wie andere Spielekonsolen auch) eine spezielle Hardware, für die ein spezielles hardwarebasiertes Entwicklungskit erforderlich ist, um auf alle Funktionen zugreifen zu können. Wenn Sie für ein Spiel das maximale Potenzial der Xbox One-Hardware benötigen, sollten Sie sich beim [ID@Xbox](http://www.xbox.com/Developers/id)-Programm registrieren, um Zugriff auf ein Xbox One-Entwicklungs-Kit zu erhalten.


Weitere Informationen zu den Systemressourcen für UWP-Apps auf Xbox One finden Sie im ersten Teil dieses Videos.
</br>
</br>
<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developing-xbox-one-applications-16860/Video-What-s-Unique--vk0fOPf9C_2006218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="see-also"></a>Weitere Informationen
- [UWP auf Xbox One](index.md)
- [Erste Schritte – Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md)
- [DirectX und UWP auf Xbox One](https://blogs.msdn.microsoft.com/chuckw/2017/12/15/directx-and-uwp-on-xbox-one/)

