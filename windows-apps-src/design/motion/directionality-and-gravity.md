---
Description: Learn how Fluent motion uses directionality and gravity.
title: Direktionalität und Schwerkraft – Animation in UWP-Apps
label: Directionality and gravity
template: detail.hbs
ms.date: 10/02/2018
ms.topic: article
keywords: Windows 10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Draft
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 4bb6f0ba60e89720a6daa37604cbe93696fb2bb7
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8346024"
---
# <a name="directionality-and-gravity"></a><span data-ttu-id="183ab-103">Direktionalität und Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="183ab-103">Directionality and gravity</span></span>

<span data-ttu-id="183ab-104">Gerichtete Bewegungen festigen das mentale Modell der Reise, die ein Benutzer auf einer Oberfläche macht.</span><span class="sxs-lookup"><span data-stu-id="183ab-104">Directional signals help to solidify the mental model of the journey a user takes across experiences.</span></span> <span data-ttu-id="183ab-105">Es ist wichtig, dass jede Bewegungsrichtung sowohl die Kontinuität des Raumes als auch die Integrität der Objekte im Raum unterstützt.</span><span class="sxs-lookup"><span data-stu-id="183ab-105">It is important that the direction of any motion support both the continuity of the space as well as the integrity of the objects in the space.</span></span>

<span data-ttu-id="183ab-106">Eine gerichtete Bewegung unterliegt Kräften wie beispielsweise der Schwerkraft.</span><span class="sxs-lookup"><span data-stu-id="183ab-106">Directional movement is subject to forces like gravity.</span></span> <span data-ttu-id="183ab-107">Die Anwendung von Kräften auf die Bewegung verstärkt ihre die natürliche Anmutung.</span><span class="sxs-lookup"><span data-stu-id="183ab-107">Applying forces to movement reinforces the natural feel of the motion.</span></span>

## <a name="direction-of-movement"></a><span data-ttu-id="183ab-108">Bewegungsrichtung</span><span class="sxs-lookup"><span data-stu-id="183ab-108">Direction of movement</span></span>

:::row:::
    :::column:::
        Direction of movement corresponds to physical motion. Just like in nature, objects can move in any world axis - X,Y,Z. This is how we think of the movement of objects on the screen.

        When you move objects, avoid unnatural collisions. Keep in mind where objects come from and go to, and alway support higher level constructs that may be used in the scene, such as scroll direction or layout hierarchy.
    :::column-end:::
    :::column:::
        ![direction backward in](images/Direction.gif)
    :::column-end:::
:::row-end:::

## <a name="direction-of-navigation"></a><span data-ttu-id="183ab-109">Navigationsrichtung</span><span class="sxs-lookup"><span data-stu-id="183ab-109">Direction of navigation</span></span>

<span data-ttu-id="183ab-110">Die Navigationsrichtung zwischen den Szenen in Ihrer App ist konzeptionell.</span><span class="sxs-lookup"><span data-stu-id="183ab-110">The direction of navigation between scenes in your app is conceptual.</span></span> <span data-ttu-id="183ab-111">Benutzer navigieren vorwärts oder rückwärts.</span><span class="sxs-lookup"><span data-stu-id="183ab-111">Users navigate forward and back.</span></span> <span data-ttu-id="183ab-112">Szenen erscheinen im Blickfeld oder werden ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="183ab-112">Scenes move in and out of view.</span></span> <span data-ttu-id="183ab-113">Die Kombination dieser Konzepte mit physikalischen Bewegungen dient zur Führung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="183ab-113">These concepts combine with physical movement to guide the user.</span></span>

<span data-ttu-id="183ab-114">Wenn die Navigation ein Objekt von der vorherigen Szene zur neuen Szene bewegt, führt das Objekt auf dem Bildschirm eine einfache Bewegung von A nach B aus.</span><span class="sxs-lookup"><span data-stu-id="183ab-114">When navigation causes an object to travel from the previous scene to the new scene, the object makes a simple A-to-B move on the screen.</span></span> <span data-ttu-id="183ab-115">Um sicherzustellen, dass die Bewegung physikalisch real erscheint, werden sowohl der standardmäßige Geschwindigkeitsverlauf als auch die Schwerkraft hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="183ab-115">To ensure that the movement feels more physical, the standard easing is added, as well as the feeling of gravity.</span></span>

<span data-ttu-id="183ab-116">Für die Rückwärtsnavigation wird die Verschiebung umgekehrt (von B nach A).</span><span class="sxs-lookup"><span data-stu-id="183ab-116">For back navigation, the move is reversed (B-to-A).</span></span> <span data-ttu-id="183ab-117">Wenn der Benutzer zurück navigiert, erwartet er, dass er so schnell wie möglich in den vorherigen Zustand zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="183ab-117">When the user navigates back, they have an expectation to be returned to the previous state as soon as possible.</span></span> <span data-ttu-id="183ab-118">Das Timing ist schneller und direkter. Es wird ein sich verlangsamender Geschwindigkeitsverlauf verwendet.</span><span class="sxs-lookup"><span data-stu-id="183ab-118">The timing is quicker, more direct, and uses the decelerate easing.</span></span>

<span data-ttu-id="183ab-119">Im Folgenden werden diese Prinzipien angewendet, da das ausgewählte Element während der Vorwärts- und Rückwärtsnavigation auf dem Bildschirm sichtbar bleibt.</span><span class="sxs-lookup"><span data-stu-id="183ab-119">Here, these priciples are applied as the selected item stays on screen during forward and back navigation.</span></span>

![UI-Beispiel für kontinuierliche Bewegung](images/continuous3.gif)

<span data-ttu-id="183ab-121">Wenn Elemente auf dem Bildschirm durch die Navigation ersetzt werden, ist es wichtig zu zeigen, wohin die Szene führt und woher die neue Szene kommt.</span><span class="sxs-lookup"><span data-stu-id="183ab-121">When navigation causes items on the screen to be replaced, its important to show where the exiting scene went to, and where the new scene is coming from.</span></span>

<span data-ttu-id="183ab-122">Dies hat mehrere Vorteile:</span><span class="sxs-lookup"><span data-stu-id="183ab-122">This has several benefits:</span></span>

- <span data-ttu-id="183ab-123">Es festigt das mentale Raummodell des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="183ab-123">It solidifies the user's mental model of the space.</span></span>
- <span data-ttu-id="183ab-124">Die Dauer der auslaufenden Szene kann genutzt werden, um den Inhalt für die eingehende Szene vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="183ab-124">The duration of the exiting scene provides more time to prepare content to be animated in for the incoming scene.</span></span>
- <span data-ttu-id="183ab-125">De wahrgenommene Leistung der App wird verbessert.</span><span class="sxs-lookup"><span data-stu-id="183ab-125">It improves the perceived performance of the app.</span></span>

<span data-ttu-id="183ab-126">Es sind 4 diskrete Navigationsrichtungen zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="183ab-126">There are 4 discreet directions of navigation to consider.</span></span>

:::row:::
    :::column:::
        **Forward-In**

        Celebrate content entering the scene in a manner that does not collide with outgoing content. Content decelerates into the scene.
    :::column-end:::
    :::column:::
        ![direction forward in](images/forwardIN.gif)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        **Forward-Out**

        Content exits quickly. Objects accelerate off screen.
    :::column-end:::
    :::column:::
        ![direction forward out](images/forwardOUT.gif)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        **Backward-In**

        Same as Forward-In, but reversed.
    :::column-end:::
    :::column:::
        ![direction backward in](images/backwardIN.gif)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        **Backward-Out**

        Same as Forward-Out, but reversed.
    :::column-end:::
    :::column:::
        ![direction backward out](images/backwardOUT.gif)
    :::column-end:::
:::row-end:::

## <a name="gravity"></a><span data-ttu-id="183ab-127">Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="183ab-127">Gravity</span></span>

<span data-ttu-id="183ab-128">Schwerkraft lässt die Darstellung natürlicher wirken.</span><span class="sxs-lookup"><span data-stu-id="183ab-128">Gravity makes your experiences feel more natural.</span></span> <span data-ttu-id="183ab-129">Objekte, die sich auf der Z-Achse bewegen und nicht durch ein On-Screen-Angebot in der Szene verankert sind, können von der Schwerkraft beeinflusst werden.</span><span class="sxs-lookup"><span data-stu-id="183ab-129">Objects that move on the Z-axis and are not anchored to the scene by an onscreen affordance have the potential to be affected by gravity.</span></span> <span data-ttu-id="183ab-130">Wenn ein Objekt die Szene verlässt, zieht die Schwerkraft das Objekt herunter, bevor es seine Endgeschwindigkeit erreicht hat, und erzeugt so eine natürliche Krümmung der Bahn, auf dem sich das Objekt bewegt.</span><span class="sxs-lookup"><span data-stu-id="183ab-130">As an object breaks free of the scene and before it reaches escape velocity, gravity pulls down on the object, creating a more natural curve of the object trajectory as it moves.</span></span>

<span data-ttu-id="183ab-131">Schwerkraft wird normalerweise berücksichtigt, wenn ein Objekt von einer Szene zu einer anderen springen muss.</span><span class="sxs-lookup"><span data-stu-id="183ab-131">Gravity typically manifests when an object must jump from one scene to another.</span></span> <span data-ttu-id="183ab-132">Daher verwendet eine verbundene Animationen das Konzept der Schwerkraft.</span><span class="sxs-lookup"><span data-stu-id="183ab-132">Because of this, connected animation uses the concept of gravity.</span></span>

<span data-ttu-id="183ab-133">Im Folgenden wird ein Element aus der oberen Reihe des Gitters durch die Schwerkraft beeinflusst, so dass es leicht fällt, wenn es seinen Platz verlässt und sich nach vorne bewegt.</span><span class="sxs-lookup"><span data-stu-id="183ab-133">Here, an element in the top row of the grid is affected by gravity, causing it to drop slightly as it leaves its place and moves to the front.</span></span>

![Richtung rückwärts hinein](images/continuity-photos.gif)

## <a name="related-articles"></a><span data-ttu-id="183ab-135">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="183ab-135">Related articles</span></span>

- [<span data-ttu-id="183ab-136">Übersicht über Bewegungen</span><span class="sxs-lookup"><span data-stu-id="183ab-136">Motion overview</span></span>](index.md)
- [<span data-ttu-id="183ab-137">Timing und Geschwindigkeitsverlauf</span><span class="sxs-lookup"><span data-stu-id="183ab-137">Timing and easing</span></span>](timing-and-easing.md)
