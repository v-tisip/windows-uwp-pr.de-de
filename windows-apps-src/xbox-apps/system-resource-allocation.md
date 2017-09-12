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
ms.openlocfilehash: 76c9d372cdfd98ef86f123862c35d238b24fe2ed
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="system-resources-for-uwp-apps-and-games-on-xbox-one"></a><span data-ttu-id="702b8-104">Systemressourcen für UWP-Apps und -Spiele auf der Xbox One</span><span class="sxs-lookup"><span data-stu-id="702b8-104">System resources for UWP apps and games on Xbox One</span></span>

<span data-ttu-id="702b8-105">Systemressourcen für UWP-Apps und -Spiele, die auf der Xbox One ausgeführt werden, teilen sich die Ressourcen mit dem System und anderen Apps.</span><span class="sxs-lookup"><span data-stu-id="702b8-105">UWP apps and games running on Xbox One share resources with the system and other apps.</span></span> <span data-ttu-id="702b8-106">Daher haben UWP-Apps und -Spiele Zugriff auf die folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="702b8-106">Therefore, UWP apps and games will have access to the following resources:</span></span>

* <span data-ttu-id="702b8-107">Der maximal verfügbare Arbeitsspeicher für eine im Vordergrund ausgeführte App beträgt 1GB.</span><span class="sxs-lookup"><span data-stu-id="702b8-107">The maximum memory available to an app running in the foreground is 1 GB.</span></span>
    * <span data-ttu-id="702b8-108">Der maximal verfügbare Arbeitsspeicher für eine im Hintergrund ausgeführte App beträgt 128MB.</span><span class="sxs-lookup"><span data-stu-id="702b8-108">The maximum memory available to an app running in the background is 128 MB.</span></span>
    * <span data-ttu-id="702b8-109">Bei Apps, die diese Arbeitsspeicheranforderungen überschreiten, treten Speicherzuweisungsfehler auf.</span><span class="sxs-lookup"><span data-stu-id="702b8-109">Apps that exceed these memory requirements will encounter memory allocation failures.</span></span> <span data-ttu-id="702b8-110">Weitere Informationen zum Überwachen der Arbeitsspeicherverwendung finden Sie in der Referenz der [MemoryManager-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="702b8-110">For more information about monitoring memory use, see the [MemoryManager class](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) reference.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="702b8-111">Wenn Sie die App oder das Spiel über den Visual Studio-Debugger ausführen, gelten diese Arbeitsspeicherbeschränkungen nicht.</span><span class="sxs-lookup"><span data-stu-id="702b8-111">When running your application or game from the Visual Studio debugger, these memory constraints do not apply.</span></span> <span data-ttu-id="702b8-112">Diese Beschränkung gilt nur, wenn die Ausführung nicht im Debugmodus erfolgt.</span><span class="sxs-lookup"><span data-stu-id="702b8-112">This limit is only applicable when not running in debugging mode.</span></span>

* <span data-ttu-id="702b8-113">Gemeinsame Nutzung von 2 bis 4 CPU-Kernen, je nach Anzahl der auf dem System ausgeführten Apps und Spiele.</span><span class="sxs-lookup"><span data-stu-id="702b8-113">Share of 2-4 CPU cores depending on the number of apps and games running on the system.</span></span>

* <span data-ttu-id="702b8-114">Gemeinsame Nutzung von 45% der GPU, je nach Anzahl der im System ausgeführten Apps und Spiele.</span><span class="sxs-lookup"><span data-stu-id="702b8-114">Share of 45% of the GPU depending on the number of apps and games running on the system.</span></span>

* <span data-ttu-id="702b8-115">UWP auf Xbox One unterstützt die DirectX11-Featureebene10.</span><span class="sxs-lookup"><span data-stu-id="702b8-115">UWP on Xbox One supports DirectX 11 Feature Level 10.</span></span> <span data-ttu-id="702b8-116">DirectX12 wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="702b8-116">DirectX 12 is not supported at this time.</span></span>

* <span data-ttu-id="702b8-117">Alle Apps müssen auf der x64-Architektur ausgeführt werden können, um für Xbox entwickelt oder an den Store für Xbox übermittelt zu werden.</span><span class="sxs-lookup"><span data-stu-id="702b8-117">All apps must target the x64 architecture in order to be developed or submitted to the store for Xbox.</span></span>  

<span data-ttu-id="702b8-118">Bei der **Anwendungsentwicklung** müssen Sie berücksichtigen, dass die verfügbaren Ressourcen im Vergleich zu einem Standard-PC möglicherweise eingeschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="702b8-118">For **application development**, it's important to keep in mind that the resources available may be limited in comparison to a standard PC.</span></span>

<span data-ttu-id="702b8-119">Bei der **Spieleentwicklung** müssen Sie bedenken, dass die Xbox One (wie andere Spielekonsolen auch) eine spezielle Hardware ist, für die ein spezielles hardwarebasiertes Entwicklungskit erforderlich ist, um auf alle Funktionen zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="702b8-119">For **games development**, it’s important to keep in mind that Xbox One, like other games consoles, is a specialized piece of hardware that requires a specific hardware-based development kit to access its full potential.</span></span> <span data-ttu-id="702b8-120">Wenn Sie für ein Spiel das maximale Potenzial der Xbox One-Hardware benötigen, können Sie sich beim [ID@Xbox](http://www.xbox.com/Developers/id)-Programm registrieren, um Zugriff auf das SDK (und damit DirectX 12-Unterstützung) zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="702b8-120">If you are working on a game that requires access to the maximum potential of the Xbox One hardware, you can register with the [ID@Xbox](http://www.xbox.com/Developers/id) program to get access to Xbox One development kits, which include DirectX 12 support.</span></span>


<span data-ttu-id="702b8-121">Weitere Erläuterungen zu den Systemressourcen für UWP-Apps auf Xbox One finden Sie im ersten Teil dieses Videos.</span><span class="sxs-lookup"><span data-stu-id="702b8-121">For a little more explanation about the system resources for UWP apps on Xbox One, check out the first bit of this video.</span></span>
</br>
</br>
<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developing-xbox-one-applications-16860/Video-What-s-Unique--vk0fOPf9C_2006218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="see-also"></a><span data-ttu-id="702b8-122">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="702b8-122">See also</span></span>
- [<span data-ttu-id="702b8-123">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="702b8-123">UWP on Xbox One</span></span>](index.md)
