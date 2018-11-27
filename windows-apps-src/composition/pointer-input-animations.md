---
title: Zeigerbasierte Animationen
description: Lernen Sie, wie man die Position eines Zeigers verwendet, um dynamische „Stick to the Cursor“-Erfahrungen zu erzeugen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: 3512d47c8b3e689b0baadec26c1d8f0f510e03ef
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7713424"
---
# <a name="pointer-based-animations"></a><span data-ttu-id="8be95-104">Zeigerbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="8be95-104">Pointer-based animations</span></span>

<span data-ttu-id="8be95-105">Dieser Artikel zeigt, wie man die Position eines Zeigers verwendet, um dynamische „Stick to the Cursor“-Erfahrungen zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="8be95-105">This article shows how to use the position of a pointer to create dynamic "stick to the cursor" experiences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8be95-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8be95-106">Prerequisites</span></span>

<span data-ttu-id="8be95-107">Wir gehen hier davon aus, dass Sie mit den in diesen Artikeln behandelten Konzepten vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="8be95-107">Here, we assume that you're familiar with the concepts discussed in these articles:</span></span>

- [<span data-ttu-id="8be95-108">Eingabegesteuerte Animationen</span><span class="sxs-lookup"><span data-stu-id="8be95-108">Input-driven animations</span></span>](input-driven-animations.md)
- [<span data-ttu-id="8be95-109">Relationsbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="8be95-109">Relation based animations</span></span>](relation-animations.md)

## <a name="why-create-pointer-position-driven-experiences"></a><span data-ttu-id="8be95-110">Warum zeigerpositionsgesteuerte Erlebnisse erstellen?</span><span class="sxs-lookup"><span data-stu-id="8be95-110">Why Create Pointer Position-Driven Experiences?</span></span>

<span data-ttu-id="8be95-111">In der Fluent Design-Sprache ist Touch nicht die einzige Möglichkeit, mit der Benutzeroberfläche zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="8be95-111">In the Fluent design language, touch is not the only way to interact with UI.</span></span> <span data-ttu-id="8be95-112">Da sich UWP über mehrere Geräteformfaktoren erstreckt, interagieren Endbenutzer mit Apps mit anderen Eingabemodalitäten wie Maus und Stift.</span><span class="sxs-lookup"><span data-stu-id="8be95-112">Because UWP spans across multiple device form factors, end users interact with apps with other input modalities such as Mouse and Pen.</span></span> <span data-ttu-id="8be95-113">Die Verwendung von Positionsdaten aus diesen anderen Eingabemodalitäten bietet die Möglichkeit, Endbenutzern das Gefühl zu geben, dass sie sich noch mehr mit Ihrer Anwendung verbunden fühlen.</span><span class="sxs-lookup"><span data-stu-id="8be95-113">Using position data from these other input modalities provides an opportunity to make end users feel even more connected with your app.</span></span>

<span data-ttu-id="8be95-114">Zeigerpositionsgesteuerte Erlebnisse ermöglichen es Ihnen, die On-Screen-Position einer Pointer-Eingabemodalität zu nutzen, um zusätzliche Motion- und UI-Erlebnisse für Ihre App zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="8be95-114">Pointer position-driven experiences let you leverage the on-screen position of a Pointer input modality to create additional motion and UI experiences for your app.</span></span> <span data-ttu-id="8be95-115">Diese Erfahrungen können den Endbenutzern oft zusätzliche Informationen über das Verhalten und die Struktur der Benutzeroberfläche liefern.</span><span class="sxs-lookup"><span data-stu-id="8be95-115">These experiences often can provide additional context and feedback to end users about the behavior and structure of the UI.</span></span> <span data-ttu-id="8be95-116">Die Erfahrung ist nicht mehr nur ein Einweg-Stream, sondern beginnt zu einem Zweiwege-Stream zu werden, bei dem der Endbenutzer Eingaben mit seiner Eingabemodalität liefert und die App-Oberfläche darauf reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="8be95-116">The experience is no longer a one-way stream, but rather starts to become a two-way stream where the end user provides input with their input modality and the app UI can respond back.</span></span>

<span data-ttu-id="8be95-117">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="8be95-117">Some examples include:</span></span>

- <span data-ttu-id="8be95-118">Animieren der Position eines Spotlights, um dem Cursor zu folgen</span><span class="sxs-lookup"><span data-stu-id="8be95-118">Animating the position of a Spotlight to follow the cursor</span></span>

    ![Zeiger-Spotlight-Beispiel](images/animation/spotlight-reveal.gif)

- <span data-ttu-id="8be95-120">Drehen eines Bildes basierend auf der Position eines Zeigers</span><span class="sxs-lookup"><span data-stu-id="8be95-120">Rotating an image based on the position of a pointer</span></span>

    ![Beispiel Zeigerrotation](images/animation/pointer-rotate.gif)

## <a name="using-pointerpositionpropertyset"></a><span data-ttu-id="8be95-122">Verwenden von PointerPositionPropertySet</span><span class="sxs-lookup"><span data-stu-id="8be95-122">Using PointerPositionPropertySet</span></span>

<span data-ttu-id="8be95-123">Diese Erlebnisse können Sie mit dem PointerPositionPropertySet erzeugen.</span><span class="sxs-lookup"><span data-stu-id="8be95-123">You can create these experiences by using the PointerPositionPropertySet.</span></span> <span data-ttu-id="8be95-124">Dieses PropertySet wird für ein UIElement erstellt, um die Position des Zeigers beizubehalten, während das UIElement positiv Hit-getestet wird.</span><span class="sxs-lookup"><span data-stu-id="8be95-124">This PropertySet gets created for a UIElement to maintain the position of the pointer while the UIElement is positively hit-tested.</span></span> <span data-ttu-id="8be95-125">Der Positionswert ist relativ zum Koordinatenraum des UIElements (eine Position <0,0> ist die linke obere Ecke des UIElements).</span><span class="sxs-lookup"><span data-stu-id="8be95-125">The position value is relative to the coordinate space of the UIElement (a position of <0,0> is the top left corner of the UIElement).</span></span> <span data-ttu-id="8be95-126">Sie können dann diese Eigenschaft, die in einer Animation festgelegt wurde, nutzen, um die Bewegung einer anderen Eigenschaft zu steuern.</span><span class="sxs-lookup"><span data-stu-id="8be95-126">You can then leverage this property set in an Animation to drive the motion of another property.</span></span>

<span data-ttu-id="8be95-127">Für jede der verschiedenen Pointer-Eingabemodalitäten gibt es eine Reihe von Eingabezuständen, in denen sich die Positionsänderungen befinden könnten: Hover, Pressed, Pressed und Moved.</span><span class="sxs-lookup"><span data-stu-id="8be95-127">For each of the different Pointer Input Modalities, there are a number of input states the input could be in where the position changes: Hover, Pressed, Pressed & Moved.</span></span> <span data-ttu-id="8be95-128">Das PointerPositionPropertySet behält nur die Position des Zeigers in den Zuständen „Hover“, „Pressed“ und „Pressed and Moved“ für Mouse und Pen bei.</span><span class="sxs-lookup"><span data-stu-id="8be95-128">The PointerPositionPropertySet only maintains the position of the pointer in the Hover, Pressed and Pressed and Moved states for Moues and Pen.</span></span>

<span data-ttu-id="8be95-129">Allgemeine Schrittefür den Einstieg:</span><span class="sxs-lookup"><span data-stu-id="8be95-129">General steps to get started:</span></span>

1. <span data-ttu-id="8be95-130">Identifizieren Sie das UIElement, in dem Sie die Position des Zeigers verfolgen möchten.</span><span class="sxs-lookup"><span data-stu-id="8be95-130">Identify the UIElement, you wish to have the position of the pointer tracked in.</span></span>
1. <span data-ttu-id="8be95-131">Zugriff auf das PointerPositionPropertySet über ElementCompositionPreview.</span><span class="sxs-lookup"><span data-stu-id="8be95-131">Access the PointerPositionPropertySet via ElementCompositionPreview.</span></span>
    - <span data-ttu-id="8be95-132">Übergeben Sie UIElement in die Methode ElementCompositionPreview.GetPointerPositionPropertySet.</span><span class="sxs-lookup"><span data-stu-id="8be95-132">Pass UIElement into the ElementCompositionPreview.GetPointerPositionPropertySet method.</span></span>
1. <span data-ttu-id="8be95-133">Erstellen Sie eine ExpressionAnimation, die auf die Eigenschaft Position im PropertySet verweist.</span><span class="sxs-lookup"><span data-stu-id="8be95-133">Create an ExpressionAnimation that references the Position property in the PropertySet.</span></span>
    - <span data-ttu-id="8be95-134">Vergessen Sie nicht, Ihren Referenzparameter einzustellen!</span><span class="sxs-lookup"><span data-stu-id="8be95-134">Don’t forget to set your reference parameter!</span></span>
1. <span data-ttu-id="8be95-135">Mit der ExpressionAnimation können Sie die Eigenschaft eines CompositionObjects gezielt ansteuern.</span><span class="sxs-lookup"><span data-stu-id="8be95-135">Target a CompositionObject’s property with the ExpressionAnimation.</span></span>

> [!NOTE]
> <span data-ttu-id="8be95-136">Es wird empfohlen, das PropertySet, das von der Methode GetPointerPositionPropertySet zurückgegeben wird, einer Klassenvariablen zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="8be95-136">It is recommended that you assign the PropertySet returned from the GetPointerPositionPropertySet method to a class variable.</span></span> <span data-ttu-id="8be95-137">Dies stellt sicher, dass das Property-Set nicht durch die Garbage-Collection bereinigt wird und hat somit keinen Einfluss auf die ExpressionAnimation, in der es referenziert wird.</span><span class="sxs-lookup"><span data-stu-id="8be95-137">This ensures that the property set does not get cleaned up by Garbage Collection and thus does not have any effect on the ExpressionAnimation it is referenced in.</span></span> <span data-ttu-id="8be95-138">ExpressionAnimations hat keine starke Referenz auf die in der Gleichung verwendeten Objekte.</span><span class="sxs-lookup"><span data-stu-id="8be95-138">ExpressionAnimations do not maintain a strong reference to any of the objects used in the equation.</span></span>

## <a name="example"></a><span data-ttu-id="8be95-139">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8be95-139">Example</span></span>

<span data-ttu-id="8be95-140">Betrachten wir ein Beispiel, bei dem wir die Hover-Position einer Maus und eines Stifts nutzen, um ein Bild dynamisch zu drehen.</span><span class="sxs-lookup"><span data-stu-id="8be95-140">Let’s take a look at an example where we leverage the Hover position of a Mouse and Pen input modality to dynamically rotate an image.</span></span>

![Beispiel Zeigerrotation](images/animation/pointer-rotate.gif)

<span data-ttu-id="8be95-142">Das Bild ist ein UIElement, also lassen Sie uns zuerst einen Verweis auf das PointerPositionPropertySet erhalten.</span><span class="sxs-lookup"><span data-stu-id="8be95-142">The image is a UIElement, so let’s first get a reference to the PointerPositionPropertySet</span></span>

```csharp
_pointerPositionPropSet = ElementCompositionPreview.GetPointerPositionPropertySet(UIElement element);
```

<span data-ttu-id="8be95-143">In diesem Beispiel sind zwei Ausdrücke im Spiel:</span><span class="sxs-lookup"><span data-stu-id="8be95-143">In this sample, you have two Expressions at play:</span></span>

- <span data-ttu-id="8be95-144">Ein Ausdruck, bei dem sich das Bild aufgrund der Entfernung des Mauszeigers von der Bildmitte aus dreht.</span><span class="sxs-lookup"><span data-stu-id="8be95-144">An Expression where the image rotates based on far the pointer is from the center of the image.</span></span> <span data-ttu-id="8be95-145">Je weiter weg, desto mehr Drehung.</span><span class="sxs-lookup"><span data-stu-id="8be95-145">The further away, the more rotation.</span></span>
- <span data-ttu-id="8be95-146">Ein Ausdruck, bei dem sich die Rotationsachse aufgrund der Position des Zeigers ändert.</span><span class="sxs-lookup"><span data-stu-id="8be95-146">An Expression where the rotation axis changes based on the position of the pointer.</span></span> <span data-ttu-id="8be95-147">Die Drehachse soll senkrecht zum Positionsvektor stehen.</span><span class="sxs-lookup"><span data-stu-id="8be95-147">You want the rotation axis to be perpendicular to the vector of the position.</span></span>

<span data-ttu-id="8be95-148">Definieren wir nun die beiden Ausdrücke. Einen, der auf die RotationAngle-Eigenschaft zielt und den anderen die RotationAxis-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8be95-148">Let’s define the two Expressions, one that targets the RotationAngle property and the other the RotationAxis property.</span></span> <span data-ttu-id="8be95-149">Sie referenzieren das PointerPositionPropertySet wie jedes andere PropertySet.</span><span class="sxs-lookup"><span data-stu-id="8be95-149">You reference the PointerPositionPropertySet like any other PropertySet.</span></span>

<span data-ttu-id="8be95-150">In diesem Beispiel erstellen Sie Ausdrücke mit Hilfe der ExpressionBuilder-Klassen.</span><span class="sxs-lookup"><span data-stu-id="8be95-150">In this example, you are building Expressions using the ExpressionBuilder classes.</span></span>

```csharp
// || DEFINE THE EXPRESSION FOR THE ROTATION ANGLE ||
var hoverPosition = _pointerPositionPropSet.GetSpecializedReference
<PointerPositionPropertySetReferenceNode>().Position;
var angleExpressionNode =
EF.Conditional(
 hoverPosition == new Vector3(0, 0, 0),
 ExpressionValues.CurrentValue.CreateScalarCurrentValue(),
 35 * ((EF.Clamp(EF.Distance(center, hoverPosition), 0, distanceToCenter) % distanceToCenter) / distanceToCenter));
_tiltVisual.StartAnimation("RotationAngleInDegrees", angleExpressionNode);

// || DEFINE THE EXPRESSION FOR THE ROTATION AXIS ||
var axisAngleExpressionNode = EF.Vector3(
-(hoverPosition.Y - center.Y) * EF.Conditional(hoverPosition.Y == center.Y, 0, 1),
 (hoverPosition.X - center.X) * EF.Conditional(hoverPosition.X == center.X, 0, 1),
 0);
_tiltVisual.StartAnimation("RotationAxis", axisAngleExpressionNode);
```