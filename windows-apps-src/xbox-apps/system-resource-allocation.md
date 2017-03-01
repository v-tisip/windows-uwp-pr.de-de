---
author: Mtoepke
title: "Systemressourcen für UWP-Apps und -Spiele auf der Xbox One"
description: UWP auf Xbox-Systemressourcen
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 12e87019-4315-424e-b73c-426d565deef9
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 8d6876ee6235546e74341609a55db995a77323d6
ms.lasthandoff: 02/08/2017

---

# <a name="system-resources-for-uwp-apps-and-games-on-xbox-one"></a>Systemressourcen für UWP-Apps und -Spiele auf der Xbox One

Systemressourcen für UWP-Apps und -Spiele, die auf der Xbox One ausgeführt werden, teilen sich die Ressourcen mit dem System und anderen Apps. Daher haben UWP-Apps und -Spiele Zugriff auf die folgenden Ressourcen:

* Der maximal verfügbare Arbeitsspeicher für eine im Vordergrund ausgeführte App beträgt 1 GB.
    * Der maximal verfügbare Arbeitsspeicher für eine im Hintergrund ausgeführte App beträgt 128 MB.
    * Bei Apps, die diese Arbeitsspeicheranforderungen überschreiten, treten Speicherzuweisungsfehler auf. Weitere Informationen zum Überwachen der Arbeitsspeicherverwendung finden Sie in der Referenz der [MemoryManager-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx).
    
    > [!NOTE]
    > Wenn Sie die App oder das Spiel über den Visual Studio-Debugger ausführen, gelten diese Arbeitsspeicherbeschränkungen nicht. Diese Beschränkung gilt nur, wenn die Ausführung nicht im Debugmodus erfolgt.

* Gemeinsame Nutzung von 2 bis 4 CPU-Kernen, je nach Anzahl der auf dem System ausgeführten Apps und Spiele.

* Gemeinsame Nutzung von 45 % der GPU, je nach Anzahl der im System ausgeführten Apps und Spiele.

* UWP auf der Xbox One unterstützt die DirectX 11-Featureebene 10. DirectX 12 wird derzeit nicht unterstützt.

* Alle Apps müssen auf der x64-Architektur ausgeführt werden können, um für Xbox entwickelt oder an den Store für Xbox übermittelt zu werden.  

Bei der **Anwendungsentwicklung** müssen Sie berücksichtigen, dass die verfügbaren Ressourcen im Vergleich zu einem Standard-PC möglicherweise eingeschränkt sind.

Bei der **Spieleentwicklung** müssen Sie bedenken, dass die Xbox One (wie andere Spielekonsolen auch) eine spezielle Hardware ist, für die ein spezielles hardwarebasiertes Entwicklungskit erforderlich ist, um auf alle Funktionen zugreifen zu können. Wenn Sie für ein Spiel das maximale Potenzial der Xbox One-Hardware benötigen, können Sie sich beim [ID@Xbox](http://www.xbox.com/Developers/id)-Programm registrieren, um Zugriff auf das SDK (und damit DirectX 12-Unterstützung) zu erhalten.

## <a name="see-also"></a>Siehe auch
- [UWP auf Xbox One](index.md)

