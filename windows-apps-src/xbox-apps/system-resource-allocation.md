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
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5156862"
---
# <a name="system-resources-for-uwp-apps-and-games-on-xbox-one"></a><span data-ttu-id="4b839-104">Systemressourcen für UWP-Apps und -Spiele auf der Xbox One</span><span class="sxs-lookup"><span data-stu-id="4b839-104">System resources for UWP apps and games on Xbox One</span></span>

<span data-ttu-id="4b839-105">Systemressourcen für UWP-Apps, die auf der Xbox One ausgeführt werden, teilen sich die Ressourcen mit dem System und anderen Apps.</span><span class="sxs-lookup"><span data-stu-id="4b839-105">UWP apps running on Xbox One share resources with the system and other apps.</span></span> <span data-ttu-id="4b839-106">Welche Ressourcen für eine UWP-App auf Xbox One verfügbar sind, hängt davon ab, ob Sie diese als eine App oder ein Spiel im Xbox Live Creators-Programm übermitteln.</span><span class="sxs-lookup"><span data-stu-id="4b839-106">The resources available to a UWP on Xbox One app depend on whether you submit as an app or as an Xbox Live Creators Program game.</span></span>

* <span data-ttu-id="4b839-107">Maximal verfügbarer Arbeitsspeicher für eine Ausführung im Vordergrund:</span><span class="sxs-lookup"><span data-stu-id="4b839-107">Maximum available memory while running in the foreground:</span></span>
    * <span data-ttu-id="4b839-108">Apps: 1GB</span><span class="sxs-lookup"><span data-stu-id="4b839-108">Apps: 1 GB</span></span>
    * <span data-ttu-id="4b839-109">Spiele: 5GB</span><span class="sxs-lookup"><span data-stu-id="4b839-109">Games: 5 GB</span></span>

<span data-ttu-id="4b839-110">Der maximal verfügbare Arbeitsspeicher für eine im Hintergrund ausgeführte App beträgt 128MB.</span><span class="sxs-lookup"><span data-stu-id="4b839-110">The maximum memory available to an app running in the background is 128 MB.</span></span> <span data-ttu-id="4b839-111">Der Hintergrundmodus gilt nur für gleichzeitig ausgeführte Anwendungen, wie z.B. Apps zur Musikwiedergabe im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="4b839-111">Background mode only applies to concurrent applications, like background music players.</span></span>  <span data-ttu-id="4b839-112">Spiele werden angehalten und im Hintergrund beendet.</span><span class="sxs-lookup"><span data-stu-id="4b839-112">Games will be suspended and terminated in the background.</span></span>

<span data-ttu-id="4b839-113">Durch eine Überschreitung dieser Einschränkungen treten Arbeitsspeicher-Zuweisungsfehler auf.</span><span class="sxs-lookup"><span data-stu-id="4b839-113">Exceeding these limitations will cause memory allocation failures.</span></span> <span data-ttu-id="4b839-114">Weitere Informationen zum Überwachen der Arbeitsspeicherverwendung finden Sie in der Referenz der [MemoryManager-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="4b839-114">For more information about monitoring memory use, see the [MemoryManager class](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) reference.</span></span>
    
    > [!NOTE]
    > When running your app or game from the Visual Studio debugger, these memory constraints do not apply. This limit is only applicable when not running in debugging mode.

* <span data-ttu-id="4b839-115">CPU</span><span class="sxs-lookup"><span data-stu-id="4b839-115">CPU</span></span>
    * <span data-ttu-id="4b839-116">Apps: Gemeinsame Nutzung von 2 bis 4 CPU-Kernen, je nach Anzahl der auf dem System ausgeführten Apps und Spiele.</span><span class="sxs-lookup"><span data-stu-id="4b839-116">Apps: share of 2-4 CPU cores depending on the number of apps and games running on the system.</span></span>
    * <span data-ttu-id="4b839-117">Spiele: 4 exklusiv und 2 gemeinsam genutzte CPU-Kerne.</span><span class="sxs-lookup"><span data-stu-id="4b839-117">Games: 4 exclusive and 2 shared CPU cores.</span></span>

* <span data-ttu-id="4b839-118">GPU</span><span class="sxs-lookup"><span data-stu-id="4b839-118">GPU</span></span>
    * <span data-ttu-id="4b839-119">Apps: Gemeinsame Nutzung von 45% der GPU, je nach Anzahl der im System ausgeführten Apps und Spiele.</span><span class="sxs-lookup"><span data-stu-id="4b839-119">Apps: share of 45% of the GPU depending on the number of apps and games running on the system.</span></span>
    * <span data-ttu-id="4b839-120">Spiele: Vollständiger Zugriff auf alle verfügbaren GPU-Zyklen.</span><span class="sxs-lookup"><span data-stu-id="4b839-120">Games: full access to available GPU cycles.</span></span>

* <span data-ttu-id="4b839-121">DirectX-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="4b839-121">DirectX support</span></span>
    * <span data-ttu-id="4b839-122">Apps: DirectX11 – Featureebene 10.</span><span class="sxs-lookup"><span data-stu-id="4b839-122">Apps: DirectX 11 Feature Level 10.</span></span>
    * <span data-ttu-id="4b839-123">Spiele: DirectX12 und DirectX11 – Featureebene 10.</span><span class="sxs-lookup"><span data-stu-id="4b839-123">Games: DirectX 12, and DirectX 11 Feature Level 10.</span></span>

* <span data-ttu-id="4b839-124">Alle Apps und Spiele müssen auf der x64-Architektur ausgeführt werden können, um für Xbox entwickelt oder an den Store für Xbox übermittelt zu werden.</span><span class="sxs-lookup"><span data-stu-id="4b839-124">All apps and games must target the x64 architecture in order to be developed or submitted to the store for Xbox.</span></span>  

<span data-ttu-id="4b839-125">Für **Anwendungsentwicklung** sind die verfügbaren Ressourcen im Vergleich zu einem Standard-PC möglicherweise beschränkt und können je nach Anzahl der auf dem System ausgeführten Apps und Spiele variieren.</span><span class="sxs-lookup"><span data-stu-id="4b839-125">For **application development**, resources available may be limited in comparison to a standard PC and can vary based on the number of apps and games running on the system.</span></span>

<span data-ttu-id="4b839-126">Bei der **Spieleentwicklung** ist die Xbox One (wie andere Spielekonsolen auch) eine spezielle Hardware, für die ein spezielles hardwarebasiertes Entwicklungskit erforderlich ist, um auf alle Funktionen zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="4b839-126">For **games development**, Xbox One, like other games consoles, is a specialized piece of hardware that requires a specific hardware-based development kit to access its full potential.</span></span> <span data-ttu-id="4b839-127">Wenn Sie für ein Spiel das maximale Potenzial der Xbox One-Hardware benötigen, sollten Sie sich beim [ID@Xbox](http://www.xbox.com/Developers/id)-Programm registrieren, um Zugriff auf ein Xbox One-Entwicklungs-Kit zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="4b839-127">If you are working on a game that requires access to the maximum potential of the Xbox One hardware, consider registering with the [ID@Xbox](http://www.xbox.com/Developers/id) program to get access to an Xbox One development kit.</span></span>


<span data-ttu-id="4b839-128">Weitere Informationen zu den Systemressourcen für UWP-Apps auf Xbox One finden Sie im ersten Teil dieses Videos.</span><span class="sxs-lookup"><span data-stu-id="4b839-128">For more information about system resources for UWP apps on Xbox One, see the first part of this video.</span></span>
</br>
</br>
<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developing-xbox-one-applications-16860/Video-What-s-Unique--vk0fOPf9C_2006218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="see-also"></a><span data-ttu-id="4b839-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4b839-129">See also</span></span>
- [<span data-ttu-id="4b839-130">UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="4b839-130">UWP on Xbox One</span></span>](index.md)
- [<span data-ttu-id="4b839-131">Erste Schritte – Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="4b839-131">Get started with the Xbox Live Creators Program</span></span>](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md)
- [<span data-ttu-id="4b839-132">DirectX und UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="4b839-132">DirectX and UWP on Xbox One</span></span>](https://blogs.msdn.microsoft.com/chuckw/2017/12/15/directx-and-uwp-on-xbox-one/)

