---
title: Funktionsweise der x86- und ARM32-Emulation auf ARM
description: Eine Übersicht über die Emulation von x86-Apps auf ARM.
ms.date: 02/15/2018
ms.topic: article
keywords: windows10 s, always connected, x86-emulation of ARM
ms.localizationpriority: medium
ms.openlocfilehash: 22b8d55fa2074d18ed3e5f3fe9fa3ab8161637be
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7700871"
---
# <a name="how-x86-emulation-works-on-arm"></a>Funktionsweise der x86-Emulation auf ARM
Emulation für x86-Anwendungen macht das reichhaltige Ökosystem von Win32-Anwendungen auf ARM verfügbar. Dies bietet dem Benutzer die einzigartige Erfahrung, eine bestehende x86 win32-App ohne Änderungen an der App auszuführen. Die App selbst weiß nicht einmal, dass sie unter Windows auf einem ARM-PC ausgeführt wird, es sei denn, sie ruft bestimmte APIs auf ([IsWoW64Process2](https://msdn.microsoft.com/en-us/library/windows/desktop/mt804318.aspx)).

Die [WOW64](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384249(v=vs.85).aspx)-Ebene von Windows10 ermöglicht das Ausführen von x86-Code auf der ARM64-Version von Windows 10. Die x86-Emulation funktioniert durch Kompilieren von Blöcken von x86-Anweisungen in ARM64-Anweisungen mit Optimierungen zur Verbesserung der Leistung. Diese übersetzten Codeblöcke werden von einem Dienst zwischengespeichert, um den Aufwand der Befehlsübersetzung zu reduzieren und eine Optimierung zu ermöglichen, wenn der Code erneut ausgeführt wird. Die Caches werden für jedes Modul erstellt, so dass andere Apps sie beim ersten Start verwenden können. 

Weitere Informationen zu diesen Technologien, finden Sie im [Channel9-Video „Windows10 auf ARM”](https://channel9.msdn.com/Events/Build/2017/P4171). 