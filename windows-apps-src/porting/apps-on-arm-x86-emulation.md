---
title: Funktionsweise der x86- und ARM32-Emulation auf ARM
author: msatranjr
description: Eine Übersicht über die Emulation von x86-Apps auf ARM.
ms.author: misatran
ms.date: 02/15/2018
ms.topic: article
keywords: windows10 s, always connected, x86-emulation of ARM
ms.localizationpriority: medium
ms.openlocfilehash: 6b596ab9abd31fa10d0ca07dec973082b495262e
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7302252"
---
# <a name="how-x86-emulation-works-on-arm"></a><span data-ttu-id="7c93a-104">Funktionsweise der x86-Emulation auf ARM</span><span class="sxs-lookup"><span data-stu-id="7c93a-104">How x86 emulation works on ARM</span></span>
<span data-ttu-id="7c93a-105">Emulation für x86-Anwendungen macht das reichhaltige Ökosystem von Win32-Anwendungen auf ARM verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7c93a-105">Emulation for x86 apps makes the rich ecosystem of Win32 apps available on ARM.</span></span> <span data-ttu-id="7c93a-106">Dies bietet dem Benutzer die einzigartige Erfahrung, eine bestehende x86 win32-App ohne Änderungen an der App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="7c93a-106">This provides the user the magical experience of running an existing x86 win32 app without any modifications to the app.</span></span> <span data-ttu-id="7c93a-107">Die App selbst weiß nicht einmal, dass sie unter Windows auf einem ARM-PC ausgeführt wird, es sei denn, sie ruft bestimmte APIs auf ([IsWoW64Process2](https://msdn.microsoft.com/en-us/library/windows/desktop/mt804318.aspx)).</span><span class="sxs-lookup"><span data-stu-id="7c93a-107">The app doesn’t even know that it is running on a Windows on ARM PC, unless it calls specific APIs ([IsWoW64Process2](https://msdn.microsoft.com/en-us/library/windows/desktop/mt804318.aspx)).</span></span>

<span data-ttu-id="7c93a-108">Die [WOW64](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384249(v=vs.85).aspx)-Ebene von Windows10 ermöglicht das Ausführen von x86-Code auf der ARM64-Version von Windows 10.</span><span class="sxs-lookup"><span data-stu-id="7c93a-108">The [WOW64](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384249(v=vs.85).aspx) layer of Windows 10 allows x86 code to run on the ARM64 version of Windows 10.</span></span> <span data-ttu-id="7c93a-109">Die x86-Emulation funktioniert durch Kompilieren von Blöcken von x86-Anweisungen in ARM64-Anweisungen mit Optimierungen zur Verbesserung der Leistung.</span><span class="sxs-lookup"><span data-stu-id="7c93a-109">x86 emulation works by compiling blocks of x86 instructions into ARM64 instructions with optimizations to improve performance.</span></span> <span data-ttu-id="7c93a-110">Diese übersetzten Codeblöcke werden von einem Dienst zwischengespeichert, um den Aufwand der Befehlsübersetzung zu reduzieren und eine Optimierung zu ermöglichen, wenn der Code erneut ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7c93a-110">A service caches these translated blocks of code to reduce the overhead of instruction translation and allow for optimization when the code runs again.</span></span> <span data-ttu-id="7c93a-111">Die Caches werden für jedes Modul erstellt, so dass andere Apps sie beim ersten Start verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7c93a-111">The caches are produced for each module so that other apps can make use of them on first launch.</span></span> 

<span data-ttu-id="7c93a-112">Weitere Informationen zu diesen Technologien, finden Sie im [Channel9-Video „Windows10 auf ARM”](https://channel9.msdn.com/Events/Build/2017/P4171).</span><span class="sxs-lookup"><span data-stu-id="7c93a-112">For more details about these technologies, see the [Windows 10 on ARM](https://channel9.msdn.com/Events/Build/2017/P4171) Channel9 video.</span></span> 