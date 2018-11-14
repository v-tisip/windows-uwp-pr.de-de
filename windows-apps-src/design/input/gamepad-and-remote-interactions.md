---
author: mijacobs
Description: TODO
title: Interaktionen von Gamepad und Fernbedienung
ms.assetid: 784a08dc-2736-4bd3-bea0-08da16b1bd47
label: Gamepad and remote interactions
template: detail.hbs
isNew: true
ms.author: mijacobs
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: a3e87fea7dfce66b16ccdf04ef13950c092660c8
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6252217"
---
# <a name="gamepad-and-remote-control-interactions"></a><span data-ttu-id="51b2b-103">Interaktionen von Gamepad und Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="51b2b-103">Gamepad and remote control interactions</span></span>

![Fernbedienung und Steuerkreuz](images/dpad-remote/dpad-remote.png)

<span data-ttu-id="51b2b-105">Universelle Windows-Plattform Apps (UWP) unterstützen jetzt Eingaben von Gamepad- und Fernbedienung, welche die primären Eingabegeräte für Xbox und TV-Gerät sind.</span><span class="sxs-lookup"><span data-stu-id="51b2b-105">Universal Windows Platform (UWP) apps now support gamepad and remote control input, which are the primary input devices for Xbox and TV experiences.</span></span>

<span data-ttu-id="51b2b-106">UWP-Apps sollten für diese Eingabegerätetypen ebenso optimiert werden wie für die Eingabe per Tastatur und Maus auf einem PC oder für die Toucheingabe auf einem Smartphone oder Tablet.</span><span class="sxs-lookup"><span data-stu-id="51b2b-106">UWP apps should be optimized for these input device types, just like they are for keyboard and mouse input on a PC, and touch input on a phone or tablet.</span></span>

<span data-ttu-id="51b2b-107">Der wichtigste Schritt bei der Optimierung für Xbox und TV-Gerät besteht darin, sicherzustellen, dass die App gut mit diesen Eingabegeräten funktioniert.</span><span class="sxs-lookup"><span data-stu-id="51b2b-107">Making sure that your app works well with these input devices is a critical  step when optimizing for Xbox and the TV.</span></span>

> [!NOTE] 
> <span data-ttu-id="51b2b-108">Es ist jetzt möglich, das Gamepad an einen PC anzuschließen und mit UWP-Apps zu verwenden. Die Überprüfung Ihrer Arbeit wird somit erleichtert.</span><span class="sxs-lookup"><span data-stu-id="51b2b-108">You can now plug in and use the gamepad with UWP apps on PC which makes validating the work easy.</span></span>

<span data-ttu-id="51b2b-109">Um bei Verwendung eines Gamepads oder einer Fernbedienung eine funktionierende und praktische Benutzeroberfläche für Ihre UWP-App zu gewährleisten, sollten Sie Folgendes beachten:</span><span class="sxs-lookup"><span data-stu-id="51b2b-109">To ensure a successful and enjoyable user experience for your UWP app when using a gamepad or remote control, you should consider the following:</span></span>

* <span data-ttu-id="51b2b-110">[Hardwaretasten](../devices/designing-for-tv.md#hardware-buttons): Die Tasten und Konfigurationen von Gamepad und Fernbedienung unterscheiden sich stark.</span><span class="sxs-lookup"><span data-stu-id="51b2b-110">[Hardware buttons](../devices/designing-for-tv.md#hardware-buttons) - The gamepad and remote provide very different buttons and configurations.</span></span>

* <span data-ttu-id="51b2b-111">[XY-Fokusnavigation und Interaktion](../devices/designing-for-tv.md#xy-focus-navigation-and-interaction): Mithilfe der XY-Fokusnavigation können die Benutzer auf der Benutzeroberfläche Ihrer App navigieren.</span><span class="sxs-lookup"><span data-stu-id="51b2b-111">[XY focus navigation and interaction](../devices/designing-for-tv.md#xy-focus-navigation-and-interaction) - XY focus navigation enables the user to navigate around your app's UI.</span></span>

* <span data-ttu-id="51b2b-112">[Mausmodus](../devices/designing-for-tv.md#mouse-mode): Im Mausmodus kann Ihre App eine Mauseingabe emulieren, wenn die XY Fokusnavigation nicht ausreichend ist.</span><span class="sxs-lookup"><span data-stu-id="51b2b-112">[Mouse mode](../devices/designing-for-tv.md#mouse-mode) - Mouse mode lets your app emulate a mouse experience when XY focus navigation isn't sufficient.</span></span>
