---
author: mijacobs
Description: TODO
title: Interaktionen von Gamepad und Fernbedienung
ms.assetid: 784a08dc-2736-4bd3-bea0-08da16b1bd47
label: Gamepad and remote interactions
template: detail.hbs
isNew: True
ms.author: mijacobs
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 1c58ef4e48a91a57643e39f7fd87a700904e77dd
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="gamepad-and-remote-control-interactions"></a>Interaktionen von Gamepad und Fernbedienung

Universelle Windows-Plattform (UWP)-Apps unterstützen jetzt die Eingabe per Gamepad und Fernbedienung. Gamepads und Remotesteuerungen sind die primären Eingabegeräte in Xbox- und TV-Umgebungen. UWP-Apps sollten für diese Eingabegerätetypen ebenso optimiert werden wie für die Eingabe per Tastatur und Maus auf einem PC oder für die Toucheingabe auf einem Smartphone oder Tablet. Der wichtigste Schritt bei der Optimierung für Xbox und Fernseher besteht darin, sicherzustellen, dass die App gut mit diesen Eingabegeräten funktioniert.
Es ist jetzt möglich, das Gamepad an einen PC anzuschließen und mit UWP-Apps zu verwenden. Die Überprüfung Ihrer Arbeit wird somit erleichtert.

Um bei Verwendung eines Gamepads oder einer Fernbedienung eine funktionierende und praktische Benutzeroberfläche für Ihre UWP-App zu gewährleisten, sollten Sie Folgendes beachten:

* [Hardwaretasten](designing-for-tv.md#hardware-buttons) -
Die Tasten und Konfigurationen von Gamepad und Fernbedienung unterscheiden sich stark.

* [XY-Fokusnavigation und Interaktion](designing-for-tv.md#xy-focus-navigation-and-interaction) -
Mithilfe der XY-Fokusnavigation können die Benutzer auf der Benutzeroberfläche Ihrer App navigieren.

* [Mausmodus](designing-for-tv.md#mouse-mode) -
Im Mausmodus kann Ihre App eine Mauseingabe emulieren, wenn die XY Fokusnavigation nicht ausreichend ist.
