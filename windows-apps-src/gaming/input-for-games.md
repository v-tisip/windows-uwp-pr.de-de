---
author: mithom
title: "Eingaben für Spiele"
description: "In diesem Abschnitt wird die Arbeit mit Gamepads und anderen Eingabegeräten für Spiele für die Universelle Windows-Plattform (UWP) veranschaulicht."
ms.assetid: 2DD0B384-8776-4599-9E52-4FC0AA682735
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Spiele, Eingabe
ms.openlocfilehash: ee6017648974d5283f59708550092f26d88388ce
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="input-for-games"></a>Eingaben für Spiele

In diesem Abschnitt werden die verschiedenen Arten von Eingabegeräten beschrieben, die in Spielen für die universelle Windows-Plattform (UWP) unter Windows10 und auf Xbox One verwendet werden können. Darüber hinaus wird ihre grundlegende Nutzung veranschaulicht, und es werden Muster und Verfahren für die effektive Eingabeprogrammierung in Spielen empfohlen.

> **Hinweis**    Es gibt weitere Arten von Eingabegeräten für den Einsatz in UWP-Spielen, z.B. benutzerdefinierte Eingabegeräte, die genre- oder spielspezifisch sein können. Diese Geräte und deren Programmierung werden in diesem Abschnitt nicht behandelt. Informationen zu den Schnittstellen, die die Bereitstellung benutzerdefinierter Eingabegeräte ermöglichen, finden Sie unter dem [Windows.Gaming.Input.Custom][]-Namespace.

## <a name="gaming-input-devices"></a>Eingabegeräte für Spiele

Eingabegeräte für Spiele werden in UWP-Spielen und -Apps für Windows10 und Xbox One durch den [Windows.Gaming.Input][]-Namespace unterstützt.

### <a name="gamepads"></a>Gamepads

Gamepads sind die Standardeingabegeräte für Xbox One und werden häufig auch von Windows-Spielern als Alternative zur Tastatur und Maus genutzt. Sie bieten eine Vielzahl digitaler und analoger Steuerungen, eignen sich für nahezu alle Arten von Spielen und geben durch integrierte Vibrationsmotoren auch taktiles Feedback.

Weitere Informationen zur Verwendung von Gamepads in Ihrem UWP-Spiel finden Sie unter [Gamepad und Vibration](gamepad-and-vibration.md).

### <a name="arcade-sticks"></a>Arcade-Joysticks

Arcade-Joysticks sind reine digitale Eingabegeräte, die den Eindruck klassischer Arcade-Automaten vermitteln sollen und das ideale Eingabegerät für Kampfspiele und andere Spiele im Arcade-Stil darstellen.

Weitere Informationen zur Verwendung von Arcade-Joysticks in Ihrem UWP-Spiel finden Sie unter [Arcade-Joystick](arcade-stick.md).

### <a name="racing-wheels"></a>Rennlenkräder

Rennlenkräder sind Eingabegeräte, die Benutzern das Gefühl vermitteln, in einem echten Rennwagencockpit zu sitzen. Sie sind das ideale Eingabegerät für Rennsportspiele mit Rennwagen oder Trucks. Viele Rennlenkräder sind mit einer echten Kraftrückmeldung und nicht einfach nur Vibrationsmotoren ausgestattet, d.h., sie können echte Kräfte auf eine Steuerungsachse wie das Lenkrad ausüben.

Informationen zur Verwendung von Rennlenkrädern in Ihrem UWP-Spiel finden Sie unter [Rennlenkräder und Kraftrückmeldung](racing-wheel-and-force-feedback.md).

### <a name="ui-navigation-controller"></a>Benutzeroberflächen-Navigationscontroller

Benutzeroberflächen-Navigationscontroller sind logische Eingabegeräte, die einen allgemeingültigen Befehlskontext für die Benutzeroberflächennavigation bieten. So wird bei unterschiedlichen Spielen und physischen Eingabegeräten eine einheitliche Benutzererfahrung gewährleistet. Für die Benutzeroberfläche eines Spiels sollten anstelle gerätespezifischer Schnittstellen die UINavigationController-Schnittstellen verwendet werden.

Weitere Informationen zur Verwendung der Benutzeroberflächen-Navigationscontroller in UWP-Spielen finden Sie unter [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md).

### <a name="headsets"></a>Headsets

Headsets sind Geräte für die Audioaufnahme und -wiedergabe, die einem bestimmten Benutzer zugeordnet werden, wenn er über sein Eingabegerät verbunden ist. Sie werden häufig in Onlinespielen für Sprach-Chats verwendet, können jedoch auch die Immersion von Spielern verbessern oder Gameplayfeatures in Online- und Offlinespielen bereitstellen.

Weitere Informationen zur Verwendung von Headsets in UWP-Spielen finden Sie unter [Headset](headset.md).

### <a name="users"></a>Benutzer

Jedes Eingabegerät und das angeschlossene Headset können einem bestimmten Benutzer zugeordnet werden, um seine Identität mit seinem Spiel zu verknüpfen. Die Identität des Benutzers dient auch dazu, die Eingaben über ein physisches Eingabegerät mit Eingaben über einen logischen Benutzeroberflächen-Navigationscontroller zu korrelieren.

Weitere Informationen zur Verwaltung von Benutzern und ihren Eingabegeräten finden Sie unter [Nachverfolgen von Benutzern und ihren Geräten](input-practices-for-games.md#tracking-users-and-their-devices).

## <a name="see-also"></a>Weitere Informationen
[Windows.Gaming.Input.Custom][]


[Windows.Gaming.Input]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[Windows.Gaming.Input.Custom]: https://msdn.microsoft.com/en-us/library/windows/apps/windows.gaming.input.custom.aspx
