---
author: jwmsft
title: "Natürliche Bewegungsanimationen"
description: 
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, animation
localizationpriority: medium
ms.openlocfilehash: 5e941d1115542130a3c1e0974de51210987feb49
ms.sourcegitcommit: 44a24b580feea0f188c7eae36e72e4a4f412802b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="natural-motion-animations"></a><span data-ttu-id="6a452-103">Natürliche Bewegungsanimationen</span><span class="sxs-lookup"><span data-stu-id="6a452-103">Natural motion animations</span></span>

<span data-ttu-id="6a452-104">Dieser Artikel gibt einen kurzen Überblick über den NaturalMotionAnimation-Raum und wie man konzeptionell mit diesen Animationen in der Benutzeroberfläche umgeht.</span><span class="sxs-lookup"><span data-stu-id="6a452-104">This article provides a brief overview of the NaturalMotionAnimation space and how to conceptually think about using these types of animations in your UI.</span></span>

## <a name="making-motion-feel-familiar-and-natural"></a><span data-ttu-id="6a452-105">Bewegung vertraut und natürlich machen</span><span class="sxs-lookup"><span data-stu-id="6a452-105">Making motion feel familiar and natural</span></span>

<span data-ttu-id="6a452-106">Tolle Apps sind solche, die Erlebnisse schaffen, die die Aufmerksamkeit der Benutzer auf sich ziehen und behalten und helfen, sie durch Aufgaben zu führen.</span><span class="sxs-lookup"><span data-stu-id="6a452-106">Great apps are ones that create experiences that capture and retain user attention, and help guide users through tasks.</span></span> <span data-ttu-id="6a452-107">Bewegung ist der entscheidende Unterscheidungsfaktor, der eine schlichte Benutzeroberfläche von einer Benutzererfahrung trennt, und eine Verbindung zwischen Benutzern und der Anwendung herstellt.</span><span class="sxs-lookup"><span data-stu-id="6a452-107">Motion is the key differentiating factor that separates a User Interface from a User Experience – eliciting a connection between users and the application they are interacting with.</span></span> <span data-ttu-id="6a452-108">Je besser diese Verbindung, desto mehr Engagement und Zufriedenheit der Endanwender.</span><span class="sxs-lookup"><span data-stu-id="6a452-108">The better the connection, the higher engagement and satisfaction from end users.</span></span>

<span data-ttu-id="6a452-109">Eine Möglichkeit dabei ist durch Bewegung Erfahrungen zu schaffen, die vertraut aussehen und sich vertraut anfühlen.</span><span class="sxs-lookup"><span data-stu-id="6a452-109">One way motion can help build this connection is by creating experiences that look and feel familiar to users.</span></span> <span data-ttu-id="6a452-110">Die Benutzer haben eine unbewusste Erwartung, wie sie Bewegungen wahrnehmen, die auf realen Lebenserfahrungen basieren.</span><span class="sxs-lookup"><span data-stu-id="6a452-110">Users have an unconscious expectation for how they perceive motion that is based on real life experiences.</span></span> <span data-ttu-id="6a452-111">Wir sehen, wie Gegenstände über den Boden rutschen, vom Tisch fallen, ineinander hüpfen und mit einer Feder oszillieren.</span><span class="sxs-lookup"><span data-stu-id="6a452-111">We see how objects slide across the floor, fall off the table, bounce into one another and oscillate with a spring.</span></span> <span data-ttu-id="6a452-112">Bewegung, die diese Erwartung nutzt, indem sie auf der realen Welt der Physik basiert, sehen und fühlen sich natürlicher an.</span><span class="sxs-lookup"><span data-stu-id="6a452-112">Motion that leverages this expectation by being based on real-world physics looks and feels more natural in our eyes.</span></span> <span data-ttu-id="6a452-113">Die Bewegung wird natürlicher und interaktiver. Aber noch wichtiger ist, dass das gesamte Erlebnis unvergesslicher und angenehmer wird.</span><span class="sxs-lookup"><span data-stu-id="6a452-113">The motion becomes more natural and interactive, but more importantly, the entire experience becomes more memorable and delightful.</span></span>

![<span data-ttu-id="6a452-114">Skalierungsbewegung ohne Animation](images/animation/scale-no-animation.gif)
![Skalierungsbewegung Cubic-Bezier](images/animation/scale-cubic-bezier.gif)
![Skalierungsbewegung mit Federanimation</span><span class="sxs-lookup"><span data-stu-id="6a452-114">Scale motion without animation](images/animation/scale-no-animation.gif)
![Scale motion with cubic bezier](images/animation/scale-cubic-bezier.gif)
![Scale motion with spring animation</span></span>](images/animation/scale-spring.gif)

<span data-ttu-id="6a452-115">Das Ergebnis ist eine höhere Bindung und Bindung der Nutzer an die App.</span><span class="sxs-lookup"><span data-stu-id="6a452-115">The net result is higher user engagement and retention with the app.</span></span>

## <a name="balancing-control-and-dynamism"></a><span data-ttu-id="6a452-116">Balance von Kontrolle und Dynamik</span><span class="sxs-lookup"><span data-stu-id="6a452-116">Balancing Control and Dynamism</span></span>

<span data-ttu-id="6a452-117">In der traditionellen Benutzeroberfläche sind [KeyFrameAnimations](https://docs.microsoft.com/uwp/api/windows.ui.composition.keyframeanimation) die vorherrschende Art, Bewegung zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="6a452-117">In traditional UI, [KeyFrameAnimation](https://docs.microsoft.com/uwp/api/windows.ui.composition.keyframeanimation)s are the predominant way to describe motion.</span></span> <span data-ttu-id="6a452-118">KeyFrames lieferte Designern und Entwicklern die größtmögliche Kontrolle, um Anfang, Ende und Interpolation zu definieren.</span><span class="sxs-lookup"><span data-stu-id="6a452-118">KeyFrames provided the utmost control to designers and developers to define the start, end, and interpolation.</span></span> <span data-ttu-id="6a452-119">Obwohl dies in vielen Fällen sehr nützlich ist, sind KeyFrame-Animationen nicht sehr dynamisch; die Bewegung ist nicht adaptiv und sieht unter allen Umständen gleich aus.</span><span class="sxs-lookup"><span data-stu-id="6a452-119">Although this is very useful in many cases, KeyFrame Animations are not very dynamic; the motion is not adaptive and looks the same under any condition.</span></span>

<span data-ttu-id="6a452-120">Am anderen Ende des Spektrums gibt es Simulationen, wie sie oft in Gaming- und Physik-Engines zu sehen sind.</span><span class="sxs-lookup"><span data-stu-id="6a452-120">On the other end of the spectrum, there are simulations often seen in gaming and physics engines.</span></span> <span data-ttu-id="6a452-121">Diese Erfahrungen sind oft die lebensechtesten und dynamischsten, mit denen Benutzer interagieren – sie schaffen das Gefühl von Ambiente und Zufälligkeit, das sie jeden Tag sehen.</span><span class="sxs-lookup"><span data-stu-id="6a452-121">These experiences often are the most life-like and dynamic that users interact with – creating that sense of ambiance and randomness that users see every day.</span></span> <span data-ttu-id="6a452-122">Obwohl sich Bewegungen dadurch lebendiger und dynamischer anfühlen, haben Designer und Entwickler weniger Kontrolle, wodurch die Integration in herkömmliche Benutzeroberflächen erschwert wird.</span><span class="sxs-lookup"><span data-stu-id="6a452-122">Although this makes motion feel more alive and dynamic, designers and developers have less control, therefore making it more difficult to integrate into traditional UI.</span></span>

![Kontrollspektrumdiagramm](images/animation/natural-motion-diagram.png)

<span data-ttu-id="6a452-124">[NaturalMotionAnimations](https://docs.microsoft.com/uwp/api/windows.ui.composition.naturalmotionanimation) gibt es, um diese Kluft zu überbrücken – um eine Balance zwischen Kontrolle für die wichtigen Elemente einer Animation wie Start/Ziel zu ermöglichen, aber eine Bewegung beizubehalten, die natürlich aussieht und sich natürlich und dynamisch anfühlt.</span><span class="sxs-lookup"><span data-stu-id="6a452-124">[NaturalMotionAnimation](https://docs.microsoft.com/uwp/api/windows.ui.composition.naturalmotionanimation)s exist to help bridge this divide – enabling a balance of control for the important elements of an animation like start/finish, but maintaining motion that looks and feels natural and dynamic.</span></span>

> [!NOTE]
> <span data-ttu-id="6a452-125">NaturalMotionAnimations sind nicht als Ersatz für KeyFrame-Animationen gedacht – es gibt immer noch Stellen in der Fluent Design-Sprache, an denen KeyFrames empfohlen werden.</span><span class="sxs-lookup"><span data-stu-id="6a452-125">NaturalMotionAnimations are not meant as a replacement for KeyFrame Animations – there are still places in the Fluent design language where KeyFrames are recommended.</span></span> <span data-ttu-id="6a452-126">NaturalMotionAnimations sind für den Einsatz an Orten gedacht, an denen Bewegung benötigt wird, KeyFrame Animationen aber nicht dynamisch genug sind.</span><span class="sxs-lookup"><span data-stu-id="6a452-126">NaturalMotionAnimations are meant to be used in places where motion is required but KeyFrame Animations are not dynamic enough.</span></span>

## <a name="using-naturalmotionanimations"></a><span data-ttu-id="6a452-127">Verwenden von NaturalMotionAnimations</span><span class="sxs-lookup"><span data-stu-id="6a452-127">Using NaturalMotionAnimations</span></span>

<span data-ttu-id="6a452-128">Mit dem Fall Creator's Update haben Sie Zugriff auf ein neues Bewegungserlebnis: **Federanimationen**.</span><span class="sxs-lookup"><span data-stu-id="6a452-128">Starting with the Fall Creator's Update, you have access to a new motion experience: **spring animations**.</span></span> <span data-ttu-id="6a452-129">Siehe [Federanimationen](spring-animations.md) für ausführliche Informationen.</span><span class="sxs-lookup"><span data-stu-id="6a452-129">See [Spring animations](spring-animations.md) for a more in depth walkthrough of springs.</span></span>

<span data-ttu-id="6a452-130">Erreicht wird diese Bewegungsart durch den Einsatz der neuen NaturalMotionAnimation – ein neuer Animationstyp, der es Entwicklern ermöglicht, vertraute und natürliche Bewegungen in ihre Benutzeroberfläche einzubauen, mit einer Balance aus Kontrolle und Dynamik.</span><span class="sxs-lookup"><span data-stu-id="6a452-130">This motion type is achieved by using the new NaturalMotionAnimation – a new animation type centered on enabling developers to build more familiar and natural feeling motion into their UI, with a balance of control and dynamism.</span></span> <span data-ttu-id="6a452-131">Sie bietet die folgenden Fähigkeiten:</span><span class="sxs-lookup"><span data-stu-id="6a452-131">They expose the following capabilities:</span></span>

- <span data-ttu-id="6a452-132">Angeben von Start- und Endwerten.</span><span class="sxs-lookup"><span data-stu-id="6a452-132">Define the start and end values.</span></span>
- <span data-ttu-id="6a452-133">Definieren von InitialVelocity und Anbindung an die Eingaben mit InteractionTracker.</span><span class="sxs-lookup"><span data-stu-id="6a452-133">Define InitialVelocity and tie to input with InteractionTracker.</span></span>
- <span data-ttu-id="6a452-134">Bewegungsspezifische Eigenschaften definieren (z. B. DampingRatio für Federanimationen).</span><span class="sxs-lookup"><span data-stu-id="6a452-134">Define motion specific properties (such as DampingRatio for springs.)</span></span>

<span data-ttu-id="6a452-135">Allgemeine Formel für den Einstieg:</span><span class="sxs-lookup"><span data-stu-id="6a452-135">General Formula to get started:</span></span>

1. <span data-ttu-id="6a452-136">Erstellen Sie die NaturalMotionAnimation aus dem Compositor mit einer der **Create**-Methoden.</span><span class="sxs-lookup"><span data-stu-id="6a452-136">Create the NaturalMotionAnimation off the Compositor using one of the **Create** methods.</span></span>
1. <span data-ttu-id="6a452-137">Definieren Sie die Eigenschaften der Animation.</span><span class="sxs-lookup"><span data-stu-id="6a452-137">Define the properties of the animation.</span></span>
1. <span data-ttu-id="6a452-138">Übergeben Sie die NaturalMotionAnimation als Parameter an den StartAnimation-Aufruf eines CompositionObjects.</span><span class="sxs-lookup"><span data-stu-id="6a452-138">Pass the NaturalMotionAnimation as a parameter to the StartAnimation call off of a CompositionObject.</span></span>
    - <span data-ttu-id="6a452-139">Oder setzen Sie die Motion-Eigenschaft eines InteractionTracker InertiaModifiers.</span><span class="sxs-lookup"><span data-stu-id="6a452-139">Or set to the Motion property of an InteractionTracker InertiaModifier.</span></span>

<span data-ttu-id="6a452-140">Ein einfaches Beispiel mit einer NaturalMotionAnimation-Federanimation, um eine visuelle „Feder“ zu einer neuen X-Offset-Position zu bewegen:</span><span class="sxs-lookup"><span data-stu-id="6a452-140">A basic example using a spring NaturalMotionAnimation to make a Visual "spring" to a new X Offset location:</span></span>

```csharp
_springAnimation = _compositor.CreateSpringScalarAnimation();
_springAnimation.Period = TimeSpan.FromSeconds(0.07);
_springAnimation.DelayTime = TimeSpan.FromSeconds(1);
_springAnimation.EndPoint = 500f;
sectionNav.StartAnimation("Offset.X", _springAnimation);
```