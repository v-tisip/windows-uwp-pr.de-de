---
title: Eingaben für Spiele
description: In diesem Abschnitt wird die Arbeit mit Gamepads und anderen Eingabegeräten für Spiele für die Universelle Windows-Plattform (UWP) veranschaulicht.
ms.assetid: 2DD0B384-8776-4599-9E52-4FC0AA682735
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, Eingabe
ms.localizationpriority: medium
ms.openlocfilehash: 1f1daac8bc94d49c501307728c1e966ba89435f9
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8738986"
---
# <a name="input-for-games"></a><span data-ttu-id="a8647-104">Eingaben für Spiele</span><span class="sxs-lookup"><span data-stu-id="a8647-104">Input for games</span></span>

<span data-ttu-id="a8647-105">In diesem Abschnitt werden die verschiedenen Arten von Eingabegeräten beschrieben, die in Spielen für die universelle Windows-Plattform (UWP) unter Windows10 und auf Xbox One verwendet werden können. Darüber hinaus wird ihre grundlegende Nutzung veranschaulicht, und es werden Muster und Verfahren für die effektive Eingabeprogrammierung in Spielen empfohlen.</span><span class="sxs-lookup"><span data-stu-id="a8647-105">This section describes the different kinds of input devices that can be used in Universal Windows Platform (UWP) games on Windows 10 and Xbox One, demonstrates their basic usage, and recommends patterns and techniques for effective input programming in games.</span></span>

> <span data-ttu-id="a8647-106">**Hinweis**    Es gibt weitere Arten von Eingabegeräten für den Einsatz in UWP-Spielen, z.B. benutzerdefinierte Eingabegeräte, die genre- oder spielspezifisch sein können.</span><span class="sxs-lookup"><span data-stu-id="a8647-106">**Note**    Other kinds of input devices exist and are available to be used in UWP games such as custom input devices that might be genre-specific or game-specific.</span></span> <span data-ttu-id="a8647-107">Diese Geräte und deren Programmierung werden in diesem Abschnitt nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="a8647-107">Such devices and their programming are not discussed in this section.</span></span> <span data-ttu-id="a8647-108">Informationen zu den Schnittstellen, die die Bereitstellung benutzerdefinierter Eingabegeräte ermöglichen, finden Sie unter dem [Windows.Gaming.Input.Custom](https://docs.microsoft.com/uwp/api/windows.gaming.input.custom)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="a8647-108">For information on the interfaces used to facilitate custom input devices, see the [Windows.Gaming.Input.Custom](https://docs.microsoft.com/uwp/api/windows.gaming.input.custom) namespace.</span></span>

## <a name="gaming-input-devices"></a><span data-ttu-id="a8647-109">Eingabegeräte für Spiele</span><span class="sxs-lookup"><span data-stu-id="a8647-109">Gaming input devices</span></span>

<span data-ttu-id="a8647-110">Eingabegeräte für Spiele werden in UWP-Spielen und -Apps für Windows10 und Xbox One durch den [Windows.Gaming.Input](https://docs.microsoft.com/uwp/api/windows.gaming.input)-Namespace unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a8647-110">Game input devices are supported in UWP games and apps for Windows 10 and Xbox One by the [Windows.Gaming.Input](https://docs.microsoft.com/uwp/api/windows.gaming.input) namespace.</span></span>

### <a name="gamepads"></a><span data-ttu-id="a8647-111">Gamepads</span><span class="sxs-lookup"><span data-stu-id="a8647-111">Gamepads</span></span>

<span data-ttu-id="a8647-112">Gamepads sind die Standardeingabegeräte für Xbox One und werden häufig auch von Windows-Spielern als Alternative zur Tastatur und Maus genutzt.</span><span class="sxs-lookup"><span data-stu-id="a8647-112">Gamepads are the standard input device on Xbox One and a common choice for Windows gamers when they don't favor a keyboard and mouse.</span></span> <span data-ttu-id="a8647-113">Sie bieten eine Vielzahl digitaler und analoger Steuerungen, eignen sich für nahezu alle Arten von Spielen und geben durch integrierte Vibrationsmotoren auch taktiles Feedback.</span><span class="sxs-lookup"><span data-stu-id="a8647-113">They provide a variety of digital and analog controls making them suitable for almost any kind of game and also provide tactile feedback through embedded vibration motors.</span></span>

<span data-ttu-id="a8647-114">Weitere Informationen zur Verwendung von Gamepads in Ihrem UWP-Spiel finden Sie unter [Gamepad und Vibration](gamepad-and-vibration.md).</span><span class="sxs-lookup"><span data-stu-id="a8647-114">For information on how to use gamepads in your UWP game, see [Gamepad and vibration](gamepad-and-vibration.md).</span></span>

### <a name="arcade-sticks"></a><span data-ttu-id="a8647-115">Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="a8647-115">Arcade sticks</span></span>

<span data-ttu-id="a8647-116">Arcade-Joysticks sind reine digitale Eingabegeräte, die den Eindruck klassischer Arcade-Automaten vermitteln sollen und das ideale Eingabegerät für Kampfspiele und andere Spiele im Arcade-Stil darstellen.</span><span class="sxs-lookup"><span data-stu-id="a8647-116">Arcade sticks are all-digital input devices valued for reproducing the feel of stand-up arcade machines and are the perfect input device for head-to-head-fighting or other arcade-style games.</span></span>

<span data-ttu-id="a8647-117">Weitere Informationen zur Verwendung von Arcade-Joysticks in Ihrem UWP-Spiel finden Sie unter [Arcade-Joystick](arcade-stick.md).</span><span class="sxs-lookup"><span data-stu-id="a8647-117">For information on how to use arcade sticks in your UWP game, see [Arcade stick](arcade-stick.md).</span></span>

### <a name="racing-wheels"></a><span data-ttu-id="a8647-118">Rennlenkräder</span><span class="sxs-lookup"><span data-stu-id="a8647-118">Racing wheels</span></span>

<span data-ttu-id="a8647-119">Rennlenkräder sind Eingabegeräte, die Benutzern das Gefühl vermitteln, in einem echten Rennwagencockpit zu sitzen. Sie sind das ideale Eingabegerät für Rennsportspiele mit Rennwagen oder Trucks.</span><span class="sxs-lookup"><span data-stu-id="a8647-119">Racing wheels are input devices that resemble the feel of a real racecar cockpit and are the perfect input device for any racing game that features cars or trucks.</span></span> <span data-ttu-id="a8647-120">Viele Rennlenkräder sind mit einer echten Kraftrückmeldung und nicht einfach nur Vibrationsmotoren ausgestattet, d.h., sie können echte Kräfte auf eine Steuerungsachse wie das Lenkrad ausüben.</span><span class="sxs-lookup"><span data-stu-id="a8647-120">Many racing wheels are equipped with true force feedback--that is, they can apply actual forces on an axis of control such as the steering wheel--not just simple vibration.</span></span>

<span data-ttu-id="a8647-121">Informationen zur Verwendung von Rennlenkrädern in Ihrem UWP-Spiel finden Sie unter [Rennlenkräder und Kraftrückmeldung](racing-wheel-and-force-feedback.md).</span><span class="sxs-lookup"><span data-stu-id="a8647-121">For information on how to use racing wheels in your UWP game, see [Racing Wheel and force feedback](racing-wheel-and-force-feedback.md).</span></span>

### <a name="flight-sticks"></a><span data-ttu-id="a8647-122">Steuerknüppel</span><span class="sxs-lookup"><span data-stu-id="a8647-122">Flight sticks</span></span>

<span data-ttu-id="a8647-123">Steuerknüppel sind Eingabegeräte für Spiele, die das Gefühl eines Steuerknüppels reproduzieren reproduzieren, die in Flugzeugen oder raumschiffen des befinden würde.</span><span class="sxs-lookup"><span data-stu-id="a8647-123">Flight sticks are gaming input devices that reproduce the feel of flight sticks that would be found in a plane or spaceship's cockpit.</span></span> <span data-ttu-id="a8647-124">Sie sind das perfekte Eingabegerät für die schnelle und genaue Steuerung von Fluggeräten.</span><span class="sxs-lookup"><span data-stu-id="a8647-124">They're the perfect input device for quick and accurate control of flight.</span></span>

<span data-ttu-id="a8647-125">Weitere Informationen zur Verwendung von Steuerknüppel in Ihrem UWP-Spiel finden Sie unter [Steuerknüppel](flight-stick.md).</span><span class="sxs-lookup"><span data-stu-id="a8647-125">For more information on how to use flight sticks in your UWP game, see [Flight stick](flight-stick.md).</span></span>

### <a name="raw-game-controllers"></a><span data-ttu-id="a8647-126">Unformatierte Gamecontroller</span><span class="sxs-lookup"><span data-stu-id="a8647-126">Raw game controllers</span></span>

<span data-ttu-id="a8647-127">Ein unformatierter Gamecontroller bietet eine generische Darstellung mit den typischen allgemeinen Eingaben eines Gamecontrollers.</span><span class="sxs-lookup"><span data-stu-id="a8647-127">A raw game controller is a generic representation of a game controller, with inputs found on many different kinds of common game controllers.</span></span> <span data-ttu-id="a8647-128">Diese Eingaben sind als einfache Arrays von unbenannten Schaltflächen, Hebeln und Knöpfen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a8647-128">These inputs are exposed as simple arrays of unnamed buttons, switches, and axes.</span></span> <span data-ttu-id="a8647-129">Mit einem unformatierten Gamecontroller kann ein Kunde benutzerdefinierte Eingabe-Zuordnungen erstellen, unabhängig von seinem verwendeten Controllertyp.</span><span class="sxs-lookup"><span data-stu-id="a8647-129">Using a raw game controller, you can allow customers to create custom input mappings no matter what type of controller they're using.</span></span>

<span data-ttu-id="a8647-130">Weitere Informationen zur Verwendung von unformatierten Gamecontroller in Ihrem UWP-Spiel finden Sie unter [unformatierten Gamecontrollers](raw-game-controller.md).</span><span class="sxs-lookup"><span data-stu-id="a8647-130">For more information on how to use raw game controllers in your UWP game, see [Raw game controller](raw-game-controller.md).</span></span>

### <a name="ui-navigation-controllers"></a><span data-ttu-id="a8647-131">Benutzeroberflächen-navigationscontroller</span><span class="sxs-lookup"><span data-stu-id="a8647-131">UI navigation controllers</span></span>

<span data-ttu-id="a8647-132">Benutzeroberflächen-Navigationscontroller sind logische Eingabegeräte, die einen allgemeingültigen Befehlskontext für die Benutzeroberflächennavigation bieten. So wird bei unterschiedlichen Spielen und physischen Eingabegeräten eine einheitliche Benutzererfahrung gewährleistet.</span><span class="sxs-lookup"><span data-stu-id="a8647-132">UI Navigation controllers are a logical input device that exists to provide a common vocabulary for UI navigation commands that promotes a consistent user experience across different games and physical input devices.</span></span> <span data-ttu-id="a8647-133">Für die Benutzeroberfläche eines Spiels sollten anstelle gerätespezifischer Schnittstellen die UINavigationController-Schnittstellen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a8647-133">A game's user interface should use the UINavigationController interfaces instead of device-specific interfaces.</span></span>

<span data-ttu-id="a8647-134">Weitere Informationen zur Verwendung der Benutzeroberflächen-Navigationscontroller in UWP-Spielen finden Sie unter [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md).</span><span class="sxs-lookup"><span data-stu-id="a8647-134">For information on how to use UI navigation controllers in your UWP game, see [UI navigation controller](ui-navigation-controller.md).</span></span>

### <a name="headsets"></a><span data-ttu-id="a8647-135">Headsets</span><span class="sxs-lookup"><span data-stu-id="a8647-135">Headsets</span></span>

<span data-ttu-id="a8647-136">Headsets sind Geräte für die Audioaufnahme und -wiedergabe, die einem bestimmten Benutzer zugeordnet werden, wenn er über sein Eingabegerät verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="a8647-136">Headsets are audio capture and playback devices that are associated with a specific user when connected through their input device.</span></span> <span data-ttu-id="a8647-137">Sie werden häufig in Onlinespielen für Sprach-Chats verwendet, können jedoch auch die Immersion von Spielern verbessern oder Gameplayfeatures in Online- und Offlinespielen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a8647-137">They're commonly used by online games for voice chat but can also be used to enhance immersion or provide gameplay features in both online and offline games.</span></span>

<span data-ttu-id="a8647-138">Weitere Informationen zur Verwendung von Headsets in UWP-Spielen finden Sie unter [Headset](headset.md).</span><span class="sxs-lookup"><span data-stu-id="a8647-138">For information on how to use headsets in your UWP game, see [Headset](headset.md)</span></span>

### <a name="users"></a><span data-ttu-id="a8647-139">Benutzer</span><span class="sxs-lookup"><span data-stu-id="a8647-139">Users</span></span>

<span data-ttu-id="a8647-140">Jedes Eingabegerät und das angeschlossene Headset können einem bestimmten Benutzer zugeordnet werden, um seine Identität mit seinem Spiel zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="a8647-140">Each input device and its connected headset can be associated with a specific user to link their identity to their gameplay.</span></span> <span data-ttu-id="a8647-141">Die Identität des Benutzers dient auch dazu, die Eingaben über ein physisches Eingabegerät mit Eingaben über einen logischen Benutzeroberflächen-Navigationscontroller zu korrelieren.</span><span class="sxs-lookup"><span data-stu-id="a8647-141">The user identity is also the means by which input from a physical input device is correlated to input from its logical UI navigation controller.</span></span>

<span data-ttu-id="a8647-142">Weitere Informationen zur Verwaltung von Benutzern und ihren Eingabegeräten finden Sie unter [Nachverfolgen von Benutzern und ihren Geräten](input-practices-for-games.md#tracking-users-and-their-devices).</span><span class="sxs-lookup"><span data-stu-id="a8647-142">For information on how to manage users and their input devices, see [Tracking users and their devices](input-practices-for-games.md#tracking-users-and-their-devices).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8647-143">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a8647-143">See Also</span></span>

* [<span data-ttu-id="a8647-144">Eingabemethoden für Spiele</span><span class="sxs-lookup"><span data-stu-id="a8647-144">Input practices for games</span></span>](input-practices-for-games.md)
* [<span data-ttu-id="a8647-145">Windows.Gaming.Input-Namespace</span><span class="sxs-lookup"><span data-stu-id="a8647-145">Windows.Gaming.Input namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input)
* [<span data-ttu-id="a8647-146">Windows.Gaming.Input.Custom namespace</span><span class="sxs-lookup"><span data-stu-id="a8647-146">Windows.Gaming.Input.Custom namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.custom)