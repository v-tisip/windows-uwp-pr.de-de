---
title: Headset
description: Verwenden Sie die Windows.Gaming.Input-Headset-APIs, um Headsets zu erkennen, die Stimme von Spielern zu erfassen und Audio wiederzugeben.
ms.assetid: 021CCA26-D339-4C8B-B084-0D499BD83ABE
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Kopfhörer
ms.localizationpriority: medium
ms.openlocfilehash: b3de68cc59c9928a52eba5caeb840e9e825eecf0
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7835255"
---
# <a name="headset"></a><span data-ttu-id="b8f5f-104">Headset</span><span class="sxs-lookup"><span data-stu-id="b8f5f-104">Headset</span></span>

<span data-ttu-id="b8f5f-105">In diesem Dokument wird die grundlegende Programmierung für Headsets unter Verwendung von [Windows.Gaming.Input.Headset][Headset] und zugehöriger APIs für die universelle Windows-Plattform (UWP) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-105">This page describes the basics of programming for headsets using [Windows.Gaming.Input.Headset][headset] and related APIs for the Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="b8f5f-106">Auf dieser Seite erhalten Sie Informationen zu folgenden Vorgängen:</span><span class="sxs-lookup"><span data-stu-id="b8f5f-106">By reading this page, you'll learn:</span></span>
* <span data-ttu-id="b8f5f-107">Zugreifen auf ein Headset, das mit einem Eingabe- oder Navigationsgerät verbunden ist</span><span class="sxs-lookup"><span data-stu-id="b8f5f-107">How to access a headset that's connected to an input or navigation device</span></span>
* <span data-ttu-id="b8f5f-108">Ermitteln, ob ein Headset verbunden oder getrennt wurde</span><span class="sxs-lookup"><span data-stu-id="b8f5f-108">How to detect that a headset has been connected or disconnected</span></span>


## <a name="headset-overview"></a><span data-ttu-id="b8f5f-109">Übersicht über Headsets</span><span class="sxs-lookup"><span data-stu-id="b8f5f-109">Headset overview</span></span>

<span data-ttu-id="b8f5f-110">Headsets sind Geräte für die Audioaufnahme und -wiedergabe und werden am häufigsten zur Kommunikation mit anderen Spielern in Onlinespielen verwendet, können aber auch im Spiel oder für andere kreative Aufgaben verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-110">Headsets are audio capture and playback devices most often used to communicate with other players in online games but can also be used in gameplay or for other creative uses.</span></span> <span data-ttu-id="b8f5f-111">Headsets werden in Windows10 und UWP-Apps für Xbox durch den [Windows.Gaming.Input][]-Namespace unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-111">Headsets are supported in Windows 10 and Xbox UWP apps by the [Windows.Gaming.Input][] namespace.</span></span>


## <a name="detect-and-track-headsets"></a><span data-ttu-id="b8f5f-112">Erkennen und Nachverfolgen von Headsets</span><span class="sxs-lookup"><span data-stu-id="b8f5f-112">Detect and track headsets</span></span>

<span data-ttu-id="b8f5f-113">Headsets werden vom System verwaltet. Daher müssen Sie diese nicht erstellen oder initialisieren.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-113">Headsets are managed by the system, therefore you don't have to create or initialize them.</span></span> <span data-ttu-id="b8f5f-114">Das System ermöglicht den Zugriff auf ein Headset über das Eingabegerät, mit dem es verbunden ist. Außerdem stellt es Ereignisse bereit, durch die Sie benachrichtigt werden, wenn ein Headset verbunden oder getrennt wird.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-114">The system provides access to a headset through the input device its connected to and events to notify you when a headset is connected or disconnected.</span></span>

### <a name="igamecontrollerheadset"></a><span data-ttu-id="b8f5f-115">IGameController.Headset</span><span class="sxs-lookup"><span data-stu-id="b8f5f-115">IGameController.Headset</span></span>

<span data-ttu-id="b8f5f-116">Alle Eingabegeräte im [Windows.Gaming.Input][]-Namespace implementieren die [IGameController][]-Schnittstelle. Diese sieht vor, dass die [Headset][igamecontroller.headset]-Eigenschaft dem aktuell mit dem Gerät verbundenen Headset entspricht.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-116">All input devices in the [Windows.Gaming.Input][] namespace implement the [IGameController][] interface which defines the [Headset][igamecontroller.headset] property to be the headset currently connected to the device.</span></span>

### <a name="connecting-and-disconnecting-headsets"></a><span data-ttu-id="b8f5f-117">Verbinden und Trennen von Headsets</span><span class="sxs-lookup"><span data-stu-id="b8f5f-117">Connecting and disconnecting headsets.</span></span>

<span data-ttu-id="b8f5f-118">Das [HeadsetConnected][igamecontroller.headsetconnected]-Ereignis bzw. das [HeadsetDisconnected][igamecontroller.headsetdisconnected]-Ereignis wird ausgelöst, wenn ein Headset verbunden bzw. getrennt wird.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-118">When a headset is connected or disconnected, the [HeadsetConnected][igamecontroller.headsetconnected] and [HeadsetDisconnected][igamecontroller.headsetdisconnected] events are raised.</span></span> <span data-ttu-id="b8f5f-119">Sie können Handler für diese Ereignisse registrieren, um nachzuverfolgen, ob derzeit ein Headset an ein Eingabegerät angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-119">You can register handlers for these events to keep track of whether an input device currently has a headset connected to it.</span></span>

<span data-ttu-id="b8f5f-120">Das folgende Beispiel zeigt, wie ein Handler für das `HeadsetConnected`-Ereignis registriert wird.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-120">The following example shows how to register a handler for the `HeadsetConnected` event.</span></span>

```cpp
auto inputDevice = myGamepads[0]; // or arcade stick, racing wheel

inputDevice.HeadsetConnected += ref new TypedEventHandler<IGameController^, Headset^>(IGameController^ device, Headset^ headset)
{
    // enable headset capture and playback on this device
}
```

<span data-ttu-id="b8f5f-121">Das folgende Beispiel zeigt, wie ein Handler für das `HeadsetDisconnected`-Ereignis registriert wird.</span><span class="sxs-lookup"><span data-stu-id="b8f5f-121">The following example shows how to register a handler for the `HeadsetDisconnected` event.</span></span>

```cpp
auto inputDevice = myGamepads[0]; // or arcade stick, racing wheel

inputDevice.HeadsetDisconnected += ref new TypedEventHandler<IGameController^, Headset^>(IGameController^ device, Headset^ headset)
{
    // disable headset capture and playback on this device
}
```

## <a name="using-the-headset"></a><span data-ttu-id="b8f5f-122">Verwenden des Headsets</span><span class="sxs-lookup"><span data-stu-id="b8f5f-122">Using the headset</span></span>

<span data-ttu-id="b8f5f-123">Die [Headset][]-Klasse besteht aus zwei Zeichenfolgen, die XAudio-Endpunkt-IDs darstellen – eine für Audioaufnahmen (über das Headsetmikrofon) und eine für das Audiorendering (über das Ohrstück des Headsets).</span><span class="sxs-lookup"><span data-stu-id="b8f5f-123">The [Headset][] class is made up of two strings that represent XAudio endpoint IDs--one for audio capture (recording from the headset microphone) and one for audio rendering (playback through the headset earpiece).</span></span>

<span data-ttu-id="b8f5f-124">Hier wird nicht ausführlich auf XAudio eingegangen. Weitere Informationen finden Sie in der [XAudio2-Programmieranleitung](https://msdn.microsoft.com/library/windows/desktop/ee415737.aspx) und in der [Referenz zur XAudio2-API](https://msdn.microsoft.com/library/windows/desktop/ee415899.aspx).</span><span class="sxs-lookup"><span data-stu-id="b8f5f-124">The details of working with XAudio are not discussed here, for more information see the [XAudio2 programming guide](https://msdn.microsoft.com/library/windows/desktop/ee415737.aspx) and [XAudio2 API reference](https://msdn.microsoft.com/library/windows/desktop/ee415899.aspx).</span></span>


[<span data-ttu-id="b8f5f-125">Windows.Gaming.Input</span><span class="sxs-lookup"><span data-stu-id="b8f5f-125">Windows.Gaming.Input</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[<span data-ttu-id="b8f5f-126">igamecontroller</span><span class="sxs-lookup"><span data-stu-id="b8f5f-126">igamecontroller</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[igamecontroller.headset]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.headset.aspx
[igamecontroller.headsetconnected]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.headsetconnected.aspx
[igamecontroller.headsetdisconnected]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.headsetdisconnected.aspx
[<span data-ttu-id="b8f5f-127">headset</span><span class="sxs-lookup"><span data-stu-id="b8f5f-127">headset</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.headset.aspx
