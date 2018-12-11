---
Description: TODO
title: Interaktionen von Gamepad und Fernbedienung
ms.assetid: 784a08dc-2736-4bd3-bea0-08da16b1bd47
label: Gamepad and remote interactions
template: detail.hbs
isNew: true
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: daf0452a30d494b3835ea043eee7d596921b0a75
ms.sourcegitcommit: 231065c899d0de285584d41e6335251e0c2c4048
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8828848"
---
# <a name="gamepad-and-remote-control-interactions"></a>Interaktionen von Gamepad und Fernbedienung

![Fernbedienung und Steuerkreuz](images/dpad-remote/dpad-remote.png)

Universelle Windows-Plattform Apps (UWP) unterstützen jetzt Eingaben von Gamepad- und Fernbedienung, welche die primären Eingabegeräte für Xbox und TV-Gerät sind.

UWP-Apps sollten für diese Eingabegerätetypen ebenso optimiert werden wie für die Eingabe per Tastatur und Maus auf einem PC oder für die Toucheingabe auf einem Smartphone oder Tablet.

Der wichtigste Schritt bei der Optimierung für Xbox und TV-Gerät besteht darin, sicherzustellen, dass die App gut mit diesen Eingabegeräten funktioniert.

> [!NOTE] 
> Es ist jetzt möglich, das Gamepad an einen PC anzuschließen und mit UWP-Apps zu verwenden. Die Überprüfung Ihrer Arbeit wird somit erleichtert.

Um bei Verwendung eines Gamepads oder einer Fernbedienung eine funktionierende und praktische Benutzeroberfläche für Ihre UWP-App zu gewährleisten, sollten Sie Folgendes beachten:

* [Hardwaretasten](../devices/designing-for-tv.md#hardware-buttons): Die Tasten und Konfigurationen von Gamepad und Fernbedienung unterscheiden sich stark.

* [XY-Fokusnavigation und Interaktion](../devices/designing-for-tv.md#xy-focus-navigation-and-interaction): Mithilfe der XY-Fokusnavigation können die Benutzer auf der Benutzeroberfläche Ihrer App navigieren.

* [Mausmodus](../devices/designing-for-tv.md#mouse-mode): Im Mausmodus kann Ihre App eine Mauseingabe emulieren, wenn die XY Fokusnavigation nicht ausreichend ist.
