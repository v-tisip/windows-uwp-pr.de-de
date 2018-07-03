---
author: jwmsft
Description: Learn how Fluent motion uses directionality and gravity.
title: Direktionalität und Schwerkraft – Animation in UWP-Apps
label: Directionality and gravity
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: a5216e81bc556a2e761e88b071e988bf6e4f457e
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1843814"
---
# <a name="directionality-and-gravity"></a><span data-ttu-id="6b6e3-103">Direktionalität und Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="6b6e3-103">Directionality and gravity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b6e3-104">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe möglicherweise wesentlich geändert werden.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-104">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="6b6e3-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="6b6e3-106">Gerichtete Bewegungen festigen das mentale Modell der Reise, die ein Benutzer auf einer Oberfläche macht.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-106">Directional signals help to solidify the mental model of the journey a user takes across experiences.</span></span> <span data-ttu-id="6b6e3-107">Es ist wichtig, dass jede Bewegungsrichtung sowohl die Kontinuität des Raumes als auch die Integrität der Objekte im Raum unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-107">It is important that the direction of any motion support both the continuity of the space as well as the integrity of the objects in the space.</span></span>

<span data-ttu-id="6b6e3-108">Eine gerichtete Bewegung unterliegt Kräften wie beispielsweise der Schwerkraft.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-108">Directional movement is subject to forces like gravity.</span></span> <span data-ttu-id="6b6e3-109">Die Anwendung von Kräften auf die Bewegung verstärkt ihre die natürliche Anmutung.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-109">Applying forces to movement reinforces the natural feel of the motion.</span></span>

## <a name="direction-of-movement"></a><span data-ttu-id="6b6e3-110">Bewegungsrichtung</span><span class="sxs-lookup"><span data-stu-id="6b6e3-110">Direction of movement</span></span>

<span data-ttu-id="6b6e3-111">:::row::: :::column::: Die Bewegungsrichtung entspricht der einer physikalischen Bewegung.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-111">:::row::: :::column::: Direction of movement corresponds to physical motion.</span></span> <span data-ttu-id="6b6e3-112">Wie in der Natur können sich Objekte entlang jeder Weltachse (X, Y, Z) bewegen.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-112">Just like in nature, objects can move in any world axis - X,Y,Z.</span></span> <span data-ttu-id="6b6e3-113">Entsprechend stellen wir uns die Bewegung von Objekten auf dem Bildschirm vor.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-113">This is how we think of the movement of objects on the screen.</span></span>

        When you move objects, avoid unnatural collisions. Keep in mind where objects come from and go to, and alway support higher level constructs that may be used in the scene, such as scroll direction or layout hierarchy.
    :::column-end:::
    :::column:::
        ![direction backward in](images/Direction.gif)
    :::column-end:::
<span data-ttu-id="6b6e3-114">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="6b6e3-114">:::row-end:::</span></span>

## <a name="direction-of-navigation"></a><span data-ttu-id="6b6e3-115">Navigationsrichtung</span><span class="sxs-lookup"><span data-stu-id="6b6e3-115">Direction of navigation</span></span>

<span data-ttu-id="6b6e3-116">Die Navigationsrichtung zwischen den Szenen in Ihrer App ist konzeptionell.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-116">The direction of navigation between scenes in your app is conceptual.</span></span> <span data-ttu-id="6b6e3-117">Benutzer navigieren vorwärts oder rückwärts.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-117">Users navigate forward and back.</span></span> <span data-ttu-id="6b6e3-118">Szenen erscheinen im Blickfeld oder werden ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-118">Scenes move in and out of view.</span></span> <span data-ttu-id="6b6e3-119">Die Kombination dieser Konzepte mit physikalischen Bewegungen dient zur Führung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-119">These concepts combine with physical movement to guide the user.</span></span>

<span data-ttu-id="6b6e3-120">Wenn die Navigation ein Objekt von der vorherigen Szene zur neuen Szene bewegt, führt das Objekt auf dem Bildschirm eine einfache Bewegung von A nach B aus.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-120">When navigation causes an object to travel from the previous scene to the new scene, the object makes a simple A-to-B move on the screen.</span></span> <span data-ttu-id="6b6e3-121">Um sicherzustellen, dass die Bewegung physikalisch real erscheint, werden sowohl der standardmäßige Geschwindigkeitsverlauf als auch die Schwerkraft hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-121">To ensure that the movement feels more physical, the standard easing is added, as well as the feeling of gravity.</span></span>

<span data-ttu-id="6b6e3-122">Für die Rückwärtsnavigation wird die Verschiebung umgekehrt (von B nach A).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-122">For back navigation, the move is reversed (B-to-A).</span></span> <span data-ttu-id="6b6e3-123">Wenn der Benutzer zurück navigiert, erwartet er, dass er so schnell wie möglich in den vorherigen Zustand zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-123">When the user navigates back, they have an expectation to be returned to the previous state as soon as possible.</span></span> <span data-ttu-id="6b6e3-124">Das Timing ist schneller und direkter. Es wird ein sich verlangsamender Geschwindigkeitsverlauf verwendet.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-124">The timing is quicker, more direct, and uses the decelerate easing.</span></span>

<span data-ttu-id="6b6e3-125">Im Folgenden werden diese Prinzipien angewendet, da das ausgewählte Element während der Vorwärts- und Rückwärtsnavigation auf dem Bildschirm sichtbar bleibt.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-125">Here, these priciples are applied as the selected item stays on screen during forward and back navigation.</span></span>

![UI-Beispiel für kontinuierliche Bewegung](images/continuous3.gif)

<span data-ttu-id="6b6e3-127">Wenn Elemente auf dem Bildschirm durch die Navigation ersetzt werden, ist es wichtig zu zeigen, wohin die Szene führt und woher die neue Szene kommt.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-127">When navigation causes items on the screen to be replaced, its important to show where the exiting scene went to, and where the new scene is coming from.</span></span>

<span data-ttu-id="6b6e3-128">Dies hat mehrere Vorteile:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-128">This has several benefits:</span></span>

- <span data-ttu-id="6b6e3-129">Es festigt das mentale Raummodell des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-129">It solidifies the user's mental model of the space.</span></span>
- <span data-ttu-id="6b6e3-130">Die Dauer der auslaufenden Szene kann genutzt werden, um den Inhalt für die eingehende Szene vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-130">The duration of the exiting scene provides more time to prepare content to be animated in for the incoming scene.</span></span>
- <span data-ttu-id="6b6e3-131">De wahrgenommene Leistung der App wird verbessert.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-131">It improves the perceived performance of the app.</span></span>

<span data-ttu-id="6b6e3-132">Es sind 4 diskrete Navigationsrichtungen zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-132">There are 4 discreet directions of navigation to consider.</span></span>

<span data-ttu-id="6b6e3-133">:::row::: :::column::: **Vorwärts hinein**</span><span class="sxs-lookup"><span data-stu-id="6b6e3-133">:::row::: :::column::: **Forward-In**</span></span>

        Celebrate content entering the scene in a manner that does not collide with outgoing content. Content decelerates into the scene.
    :::column-end:::
    :::column:::
        ![direction forward in](images/forwardIN.gif)
    :::column-end:::
<span data-ttu-id="6b6e3-134">:::row-end::: :::row::: :::column::: **Vorwärts hinaus**</span><span class="sxs-lookup"><span data-stu-id="6b6e3-134">:::row-end::: :::row::: :::column::: **Forward-Out**</span></span>

        Content exits quickly. Objects accelerate off screen.
    :::column-end:::
    :::column:::
        ![direction forward out](images/forwardOUT.gif)
    :::column-end:::
<span data-ttu-id="6b6e3-135">:::row-end::: :::row::: :::column::: **Rückwärts hinein**</span><span class="sxs-lookup"><span data-stu-id="6b6e3-135">:::row-end::: :::row::: :::column::: **Backward-In**</span></span>

        Same as Forward-In, but reversed.
    :::column-end:::
    :::column:::
        ![direction backward in](images/backwardIN.gif)
    :::column-end:::
<span data-ttu-id="6b6e3-136">:::row-end::: :::row::: :::column::: **Rückwärts hinaus**</span><span class="sxs-lookup"><span data-stu-id="6b6e3-136">:::row-end::: :::row::: :::column::: **Backward-Out**</span></span>

        Same as Forward-Out, but reversed.
    :::column-end:::
    :::column:::
        ![direction backward out](images/backwardOUT.gif)
    :::column-end:::
<span data-ttu-id="6b6e3-137">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="6b6e3-137">:::row-end:::</span></span>

## <a name="gravity"></a><span data-ttu-id="6b6e3-138">Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="6b6e3-138">Gravity</span></span>

<span data-ttu-id="6b6e3-139">Schwerkraft lässt die Darstellung natürlicher wirken.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-139">Gravity makes your experiences feel more natural.</span></span> <span data-ttu-id="6b6e3-140">Objekte, die sich auf der Z-Achse bewegen und nicht durch ein On-Screen-Angebot in der Szene verankert sind, können von der Schwerkraft beeinflusst werden.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-140">Objects that move on the Z-axis and are not anchored to the scene by an onscreen affordance have the potential to be affected by gravity.</span></span> <span data-ttu-id="6b6e3-141">Wenn ein Objekt die Szene verlässt, zieht die Schwerkraft das Objekt herunter, bevor es seine Endgeschwindigkeit erreicht hat, und erzeugt so eine natürliche Krümmung der Bahn, auf dem sich das Objekt bewegt.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-141">As an object breaks free of the scene and before it reaches escape velocity, gravity pulls down on the object, creating a more natural curve of the object trajectory as it moves.</span></span>

<span data-ttu-id="6b6e3-142">Schwerkraft wird normalerweise berücksichtigt, wenn ein Objekt von einer Szene zu einer anderen springen muss.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-142">Gravity typically manifests when an object must jump from one scene to another.</span></span> <span data-ttu-id="6b6e3-143">Daher verwendet eine verbundene Animationen das Konzept der Schwerkraft.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-143">Because of this, connected animation uses the concept of gravity.</span></span>

<span data-ttu-id="6b6e3-144">Im Folgenden wird ein Element aus der oberen Reihe des Gitters durch die Schwerkraft beeinflusst, so dass es leicht fällt, wenn es seinen Platz verlässt und sich nach vorne bewegt.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-144">Here, an element in the top row of the grid is affected by gravity, causing it to drop slightly as it leaves its place and moves to the front.</span></span>

![Richtung rückwärts hinein](images/continuity-photos.gif)

## <a name="related-articles"></a><span data-ttu-id="6b6e3-146">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="6b6e3-146">Related articles</span></span>

- [<span data-ttu-id="6b6e3-147">Übersicht über Bewegungen</span><span class="sxs-lookup"><span data-stu-id="6b6e3-147">Motion overview</span></span>](index.md)
- [<span data-ttu-id="6b6e3-148">Timing und Geschwindigkeitsverlauf</span><span class="sxs-lookup"><span data-stu-id="6b6e3-148">Timing and easing</span></span>](timing-and-easing.md)