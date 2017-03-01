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
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: b1ee5409cfca253b3bb084b95365d22526c66920
ms.lasthandoff: 02/07/2017

---

# <a name="gamepad-and-remote-control-interactions"></a>Interaktionen von Gamepad und Fernbedienung

Apps für die Universelle Windows-Plattform (UWP) unterstützen jetzt die Eingabe per Gamepad und Fernbedienung. Gamepads und Remotesteuerungen sind die primären Eingabegeräte in Xbox- und TV-Umgebungen. UWP-Apps sollten für diese Eingabegerätetypen ebenso optimiert werden wie für die Eingabe per Tastatur und Maus auf einem PC oder für die Toucheingabe auf einem Smartphone oder Tablet. Der wichtigste Schritt bei der Optimierung für Xbox und Fernseher besteht darin, sicherzustellen, dass die App gut mit diesen Eingabegeräten funktioniert.
Es ist jetzt möglich, das Gamepad an einen PC anzuschließen und mit UWP-Apps zu verwenden. Die Überprüfung Ihrer Arbeit wird somit erleichtert.

Um bei Verwendung eines Gamepads oder einer Fernbedienung eine funktionierende und praktische Benutzeroberfläche für Ihre UWP-App zu gewährleisten, sollten Sie Folgendes beachten:

* [Hardwaretasten](designing-for-tv.md#hardware-buttons) -
Die Tasten und Konfigurationen von Gamepad und Fernbedienung unterscheiden sich stark.

* [XY-Fokusnavigation und Interaktion](designing-for-tv.md#xy-focus-navigation-and-interaction) -
Mithilfe der XY-Fokusnavigation können die Benutzer auf der Benutzeroberfläche Ihrer App navigieren.

* [Mausmodus](designing-for-tv.md#mouse-mode) -
Im Mausmodus kann Ihre App eine Mauseingabe emulieren, wenn die XY Fokusnavigation nicht ausreichend ist.

