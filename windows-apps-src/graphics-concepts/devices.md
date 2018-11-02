---
title: Geräte
description: Ein Direct3D-Gerät ist die Komponente zum Rendern von Direct3D. Ein Gerät kapselt und speichert den Renderzustand, führt Transformationen und Beleuchtungsvorgänge aus und rastert ein Bilds auf einer Oberfläche.
ms.assetid: BC903462-A32A-46BA-8411-FB294F5D2CD9
keywords:
- Geräte
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d1c35af3dd1f8826fbd61268c5c47cef9d77146a
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5972715"
---
# <a name="devices"></a><span data-ttu-id="69e3c-105">Geräte</span><span class="sxs-lookup"><span data-stu-id="69e3c-105">Devices</span></span>


<span data-ttu-id="69e3c-106">Ein Direct3D-Gerät ist die Komponente zum Rendern von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="69e3c-106">A Direct3D device is the rendering component of Direct3D.</span></span> <span data-ttu-id="69e3c-107">Ein Gerät kapselt und speichert den Renderzustand, führt Transformationen und Beleuchtungsvorgänge aus und rastert ein Bilds auf einer Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="69e3c-107">A device encapsulates and stores the rendering state, performs transformations and lighting operations, and rasterizes an image to a surface.</span></span>

<span data-ttu-id="69e3c-108">Wie im folgenden Diagramm dargestellt, umfasst die Architektur von Direct3D-Geräten ein Tranformationsmodul, Beleuchtungsmoduls und ein Rastermodul.</span><span class="sxs-lookup"><span data-stu-id="69e3c-108">Architecturally, Direct3D devices contain a transformation module, a lighting module, and a rasterizing module, as the following diagram shows.</span></span>

![Diagramm der Architektur eines Direct3D-Gerätes](images/d3ddev.png)

<span data-ttu-id="69e3c-110">Direct3D unterstützt zwei Hauptarten von Direct3D-Geräten:</span><span class="sxs-lookup"><span data-stu-id="69e3c-110">Direct3D supports two main types of Direct3D devices:</span></span>

-   <span data-ttu-id="69e3c-111">Ein HAL-Gerät mit einer hardwarebeschleunigten Rasterung und Schattierung mit Hardware und Software-Vertex-Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="69e3c-111">A hal device with hardware-accelerated rasterization and shading with both hardware and software vertex processing</span></span>
-   <span data-ttu-id="69e3c-112">Ein Referenzgerät</span><span class="sxs-lookup"><span data-stu-id="69e3c-112">A reference device</span></span>

<span data-ttu-id="69e3c-113">Diese Geräte stellen zwei separate Treiber dar.</span><span class="sxs-lookup"><span data-stu-id="69e3c-113">These devices are two separate drivers.</span></span> <span data-ttu-id="69e3c-114">Software- und Referenzgeräte sind Softwaretreiber. Das HAL-Gerät ist ein Hardwaretreiber.</span><span class="sxs-lookup"><span data-stu-id="69e3c-114">Software and reference devices are represented by software drivers, and the hal device is represented by a hardware driver.</span></span> <span data-ttu-id="69e3c-115">Normalerweise wird das HAL-Geräte für die fertige Anwendung und das Referenzgerät zum Testen genutzt.</span><span class="sxs-lookup"><span data-stu-id="69e3c-115">The most common way to take advantage of these devices is to use the hal device for shipping applications, and the reference device for feature testing.</span></span> <span data-ttu-id="69e3c-116">Diese werden durch Drittanbieter für die Emulation von bestimmten Geräten bereitgestellt (beispielsweise noch nicht veröffentlichte Entwicklerhardware).</span><span class="sxs-lookup"><span data-stu-id="69e3c-116">These are provided by third parties to emulate particular devices - for example, developmental hardware that has not yet been released.</span></span>

<span data-ttu-id="69e3c-117">Das von einer Anwendung erstellte Direct3D-Gerät muss den Funktionalitäten der Hardware entsprechen, auf der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="69e3c-117">The Direct3D device that an application creates must correspond to the capabilities of the hardware on which the application is running.</span></span> <span data-ttu-id="69e3c-118">Direct3D stellt die Renderingfunktionen entweder über den Zugriff auf die im Computer installierte 3D-Hardware, oder über die Emulation der Funktionalitäten der 3D-Hardware per Software bereit.</span><span class="sxs-lookup"><span data-stu-id="69e3c-118">Direct3D provides rendering capabilities, either by accessing 3D hardware that is installed in the computer or by emulating the capabilities of 3D hardware in software.</span></span> <span data-ttu-id="69e3c-119">Aus diesem Grund stellt Direct3D Geräte für den Hardwarezugriff und zur Softwareemulation bereit.</span><span class="sxs-lookup"><span data-stu-id="69e3c-119">Therefore, Direct3D provides devices for both hardware access and software emulation.</span></span>

<span data-ttu-id="69e3c-120">Hardwarebeschleunigte Geräte bieten eine wesentlich bessere Leistung als Softwaregeräte.</span><span class="sxs-lookup"><span data-stu-id="69e3c-120">Hardware-accelerated devices give much better performance than software devices.</span></span> <span data-ttu-id="69e3c-121">Der HAL-Gerätetyp steht auf allen von Direct3D unterstützten Grafikkarten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="69e3c-121">The hal device type is available on all Direct3D supported graphic adapters.</span></span> <span data-ttu-id="69e3c-122">In den meisten verfügen die Zielcomputer für die Anwendungen über eine Hardwarebeschleunigung. Computer mit weniger Leistung sind hingegen von der Softwareemulation abhängig.</span><span class="sxs-lookup"><span data-stu-id="69e3c-122">In most cases, applications target computers that have hardware acceleration and rely on software emulation to accommodate lower-end computers.</span></span>

<span data-ttu-id="69e3c-123">Mit Ausnahme des Referenzgeräts unterstützen Softwaregeräte nicht immer die gleichen Funktionen wie ein Hardwaregerät.</span><span class="sxs-lookup"><span data-stu-id="69e3c-123">With the exception of the reference device, software devices do not always support the same features as a hardware device.</span></span> <span data-ttu-id="69e3c-124">Anwendungen sollten daher immer die Gerätefunktionen Abfragen und so die unterstützten Funktionen ermitteln.</span><span class="sxs-lookup"><span data-stu-id="69e3c-124">Applications should always query for device capabilities to determine which features are supported.</span></span>

<span data-ttu-id="69e3c-125">Da das Verhalten der Software- und Referenzgeräte von Direct3D9 dem des HAL-Gerätes identisch ist, funktioniert für das HAL-Gerät erstellter Anwendungscode ohne Änderungen auch mit den Software- und Referenzgeräten.</span><span class="sxs-lookup"><span data-stu-id="69e3c-125">Because the behavior of the software and reference devices provided with Direct3D 9 is identical to that of the hal device, application code authored to work with the hal device will work with the software or reference devices without modifications.</span></span> <span data-ttu-id="69e3c-126">Das Verhalten des Software- oder Referenzgeräts ist mit dem des HAL-Gerätes identisch. Die Gerätefunktionalitäten können jedoch abweichen. Vor allem das Softwaregerät implementiert möglicherweise erheblich weniger Funktionen.</span><span class="sxs-lookup"><span data-stu-id="69e3c-126">The provided software or reference device behavior is identical to that of the hal device, but the device capabilities do vary, and a particular software device may implement a much smaller set of capabilities.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="69e3c-127"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="69e3c-127"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="69e3c-128">Thema</span><span class="sxs-lookup"><span data-stu-id="69e3c-128">Topic</span></span></th>
<th align="left"><span data-ttu-id="69e3c-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69e3c-129">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="device-types.md"><span data-ttu-id="69e3c-130">Gerätetypen</span><span class="sxs-lookup"><span data-stu-id="69e3c-130">Device types</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="69e3c-131">Direct3D-Gerätetypen sind HAL-Gerät (Hardwareabstraktionsschicht) und den Referenz-Rasterizer.</span><span class="sxs-lookup"><span data-stu-id="69e3c-131">Direct3D device types include Hardware Abstraction Layer (hal) devices and the reference rasterizer.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="windowed-vs--full-screen-mode.md"><span data-ttu-id="69e3c-132">Vergleich von Vollbild- und Fenstermodus</span><span class="sxs-lookup"><span data-stu-id="69e3c-132">Windowed vs. full-screen mode</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="69e3c-133">Direct3D-Anwendungen können entweder im Fenstermodus oder im Vollbildmodus ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="69e3c-133">Direct3D applications can run in either of two modes: windowed or full-screen.</span></span> <span data-ttu-id="69e3c-134">Im <em>Fenstermodus</em> teilt sich die Anwendung die verfügbare Bildschirmfläche auf dem Desktop mit allen anderen ausgeführten Programmen.</span><span class="sxs-lookup"><span data-stu-id="69e3c-134">In <em>windowed mode</em>, the application shares the available desktop screen space with all running applications.</span></span> <span data-ttu-id="69e3c-135">Im <em>Vollbildmodus</em> deckt das Fenster der Anwendung den gesamten Desktop ab. Die ausgeführten Programme (einschließlich der Entwicklungsumgebung) sind nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="69e3c-135">In <em>full-screen mode</em>, the window that the application runs in covers the entire desktop, hiding all running applications (including your development environment).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="lost-devices.md"><span data-ttu-id="69e3c-136">Lost-Zustand</span><span class="sxs-lookup"><span data-stu-id="69e3c-136">Lost devices</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="69e3c-137">Ein Direct3D-Gerät kann sich in einem Operational-Zustand oder Lost-Zustand befinden.</span><span class="sxs-lookup"><span data-stu-id="69e3c-137">A Direct3D device can be in either an operational state or a lost state.</span></span> <span data-ttu-id="69e3c-138">Der Zustand <em>Operational</em> ist der normalen Zustand des Geräts. In diesem wird das Gerät ausgeführt die Renderingdarstellung läuft wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="69e3c-138">The <em>operational</em> state is the normal state of the device in which the device runs and presents all rendering as expected.</span></span> <span data-ttu-id="69e3c-139">Das Gerät wechselt zum <em>Lost</em>-Zustand sobald ein Ereignis, z.B. den Verlust des Tastaturfokus in einer Vollbildanwendung, auftritt und das Rendering somit unmöglich wird.</span><span class="sxs-lookup"><span data-stu-id="69e3c-139">The device makes a transition to the <em>lost</em> state when an event, such as the loss of keyboard focus in a full-screen application, causes rendering to become impossible.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="swap-chains.md"><span data-ttu-id="69e3c-140">Swapchains</span><span class="sxs-lookup"><span data-stu-id="69e3c-140">Swap chains</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="69e3c-141">Eine Swapchain ist eine Sammlung von Puffern, die zum Anzeigen von Frames für den Benutzer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="69e3c-141">A swap chain is a collection of buffers that are used for displaying frames to the user.</span></span> <span data-ttu-id="69e3c-142">Bei jeder Darstellung eines neuen Frames für eine Anzeige durch eine Anwendung wird der erste Puffer der Swapchain zum Anzeigepuffer.</span><span class="sxs-lookup"><span data-stu-id="69e3c-142">Each time an application presents a new frame for display, the first buffer in the swap chain takes the place of the displayed buffer.</span></span> <span data-ttu-id="69e3c-143">Dieser Prozess heißt <em>Swapping</em> bzw. <em>Flipping</em>.</span><span class="sxs-lookup"><span data-stu-id="69e3c-143">This process is called <em>swapping</em> or <em>flipping</em>.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="introduction-to-rasterization-rules.md"><span data-ttu-id="69e3c-144">Einführung in Rasterungsregeln</span><span class="sxs-lookup"><span data-stu-id="69e3c-144">Introduction to rasterization rules</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="69e3c-145">Häufig entsprechend die Punkte von Vertizes nicht exakt den Pixel auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="69e3c-145">Often, the points specified for vertices do not precisely match the pixels on the screen.</span></span> <span data-ttu-id="69e3c-146">In diesem Fall nutzt Direct3D Dreieck-Rasterungsregeln, um zu entscheiden, welche Pixel für ein Dreieck genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="69e3c-146">When this happens, Direct3D applies triangle rasterization rules to decide which pixels apply to a given triangle.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="69e3c-147"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="69e3c-147"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="69e3c-148">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="69e3c-148">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 




