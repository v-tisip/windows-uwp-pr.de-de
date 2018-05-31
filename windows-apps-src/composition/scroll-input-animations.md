---
author: jwmsft
title: Erweitern vorhandener ScrollViewer-Erfahrungen
description: Lernen Sie, wie Sie mit einem XAML-ScrollViewer und ExpressionAnimations dynamische, eingabegesteuerte Bewegungserlebnisse erzeugen können.
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: 58e696bc3d376b80b21149a9e55a2b0547a91c0c
ms.sourcegitcommit: 67cb03db41556cf0d58993073654cd0706aede84
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/03/2018
ms.locfileid: "1480716"
---
# <a name="enhance-existing-scrollviewer-experiences"></a><span data-ttu-id="63db4-104">Erweitern vorhandener ScrollViewer-Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="63db4-104">Enhance existing ScrollViewer experiences</span></span>

<span data-ttu-id="63db4-105">Dieser Artikel erklärt, wie Sie mit einem XAML-ScrollViewer und ExpressionAnimations dynamische, eingabegesteuerte Bewegungserlebnisse erzeugen können.</span><span class="sxs-lookup"><span data-stu-id="63db4-105">This article explains how to use a XAML ScrollViewer and ExpressionAnimations to create dynamic input-driven motion experiences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63db4-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="63db4-106">Prerequisites</span></span>

<span data-ttu-id="63db4-107">Wir gehen hier davon aus, dass Sie mit den in diesen Artikeln behandelten Konzepten vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="63db4-107">Here, we assume that you're familiar with the concepts discussed in these articles:</span></span>

- [<span data-ttu-id="63db4-108">Eingabegesteuerte Animationen</span><span class="sxs-lookup"><span data-stu-id="63db4-108">Input-driven animations</span></span>](input-driven-animations.md)
- [<span data-ttu-id="63db4-109">Relationsbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="63db4-109">Relation based animations</span></span>](relation-animations.md)

## <a name="why-build-on-top-of-scrollviewer"></a><span data-ttu-id="63db4-110">Warum auf ScrollViewer aufbauen?</span><span class="sxs-lookup"><span data-stu-id="63db4-110">Why build on top of ScrollViewer?</span></span>

<span data-ttu-id="63db4-111">Normalerweise verwenden Sie den vorhandenen XAML ScrollViewer, um eine scrollbare und zoombare Oberfläche für Ihre App-Inhalte zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="63db4-111">Typically, you use the existing XAML ScrollViewer to create a scrollable and zoomable surface for your app content.</span></span> <span data-ttu-id="63db4-112">Mit der Einführung der Fluent Design-Sprache sollten Sie sich nun auch darauf konzentrieren, wie Sie den Akt des Scrollens oder Zooms einer Oberfläche nutzen können, um andere Bewegungserlebnisse zu steuern.</span><span class="sxs-lookup"><span data-stu-id="63db4-112">With the introduction of the Fluent Design language, you should now also be focusing on how to use the act of scrolling or zooming a surface to drive other motion experiences.</span></span> <span data-ttu-id="63db4-113">Zum Beispiel, mit Scrolling eine unscharfe Animation eines Hintergrunds zu nutzen oder die Position eines „Sticky-Headers“ zu steuern.</span><span class="sxs-lookup"><span data-stu-id="63db4-113">For example, using scrolling to drive a blur animation of a background or drive the position of a "sticky header".</span></span>

<span data-ttu-id="63db4-114">In diesen Szenarien nutzen Sie das Verhalten oder Manipulations-Erlebnisse wie Scrolling und Zoomen, um andere Teile Ihrer Anwendung dynamischer zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="63db4-114">In these scenarios, you are leveraging the behavior or manipulation experiences like Scrolling and zooming to make other parts of your app more dynamic.</span></span> <span data-ttu-id="63db4-115">Diese ermöglichen es der App, sich in sich geschlossener anzufühlen und die Erlebnisse in den Augen der Endbenutzer noch einprägsamer zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="63db4-115">These in turn enable the app to feel more cohesive, making the experiences more memorable in the eyes of end users.</span></span> <span data-ttu-id="63db4-116">Durch die Verbesserung der Benutzeroberfläche der App werden Endbenutzer häufiger und länger mit der App in Kontakt treten.</span><span class="sxs-lookup"><span data-stu-id="63db4-116">By making the app UI more memorable, end users will engage with the app more frequently and for longer periods.</span></span>

## <a name="what-can-you-build-on-top-of-scrollviewer"></a><span data-ttu-id="63db4-117">Was können Sie auf ScrollViewer aufbauen?</span><span class="sxs-lookup"><span data-stu-id="63db4-117">What can you build on top of ScrollViewer?</span></span>

<span data-ttu-id="63db4-118">Sie können die Position eines ScrollViewer nutzen, um eine Reihe dynamischer Erlebnisse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="63db4-118">You can leverage the position of a ScrollViewer to build a number of dynamic experiences:</span></span>

- <span data-ttu-id="63db4-119">Parallax – Nutzen Sie die Position eines ScrollViewer, um den Hintergrund- oder Vordergrundinhalte relativ schnell auf die Scrollposition zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="63db4-119">Parallax – use the position of a ScrollViewer to move background or foreground content at a relative rate to the scroll position.</span></span>
- <span data-ttu-id="63db4-120">StickyHeaders – Verwenden Sie die Position eines ScrollViewer, um einen Header zu animieren und an eine Position zu „kleben“.</span><span class="sxs-lookup"><span data-stu-id="63db4-120">StickyHeaders – use the position of a ScrollViewer to animate and "stick" a header to a position</span></span>
- <span data-ttu-id="63db4-121">Input-Driven Effects – Verwenden Sie die Position eines Scrollviewer, um einen Kompositionseffekt wie z. B. Blur zu animieren.</span><span class="sxs-lookup"><span data-stu-id="63db4-121">Input-Driven Effects – use the position of a Scrollviewer to animate a Composition Effect such as Blur.</span></span>

<span data-ttu-id="63db4-122">Im Allgemeinen ist es möglich, durch Referenzieren der Position eines ScrollViewer mit einer ExpressionAnimation eine Animation zu erstellen, die sich dynamisch relativ zum Scroll-Betrag ändert.</span><span class="sxs-lookup"><span data-stu-id="63db4-122">In general, by referencing the position of a ScrollViewer with an ExpressionAnimation, you are able to create an animation that dynamically changes relative the scroll amount.</span></span>

![Listenansicht mit Parallax](images/animation/parallax.gif)

![Ein Shy-Header](images/animation/shy-header.gif)

## <a name="using-scrollmanipulationpropertyset"></a><span data-ttu-id="63db4-125">Verwenden von ScrollManipulationPropertySet</span><span class="sxs-lookup"><span data-stu-id="63db4-125">Using ScrollManipulationPropertySet</span></span>

<span data-ttu-id="63db4-126">Um diese dynamischen Erlebnisse mit einem XAML ScrollViewer zu erzeugen, müssen Sie die Scroll-Position in einer Animation referenzieren können.</span><span class="sxs-lookup"><span data-stu-id="63db4-126">To create these dynamic experiences using a XAML ScrollViewer, you must be able to reference the scroll position in an animation.</span></span> <span data-ttu-id="63db4-127">Dies geschieht durch den Zugriff auf ein CompositionPropertySet aus dem XAML ScrollViewer, das ScrollManipulationPropertySet.</span><span class="sxs-lookup"><span data-stu-id="63db4-127">This is done by accessing a CompositionPropertySet off of the XAML ScrollViewer called the ScrollManipulationPropertySet.</span></span>
<span data-ttu-id="63db4-128">Das ScrollManipulationPropertySet enthält eine einzige Vector3-Eigenschaft namens Translation, die Zugriff auf die Scroll-Position des ScrollViewer ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="63db4-128">The ScrollManipulationPropertySet contains a single Vector3 property called Translation that provides access to the scroll position of the ScrollViewer.</span></span> <span data-ttu-id="63db4-129">Sie können diese dann wie jedes andere CompositionPropertySet in Ihrer ExpressionAnimation referenzieren.</span><span class="sxs-lookup"><span data-stu-id="63db4-129">You can then reference this like any other CompositionPropertySet in your ExpressionAnimation.</span></span>

<span data-ttu-id="63db4-130">Allgemeine Schritte zum Einstieg:</span><span class="sxs-lookup"><span data-stu-id="63db4-130">General Steps to getting started:</span></span>

1. <span data-ttu-id="63db4-131">Greifen Sie über ElementCompositionPreview auf ScrollManipulationPropertySet zu.</span><span class="sxs-lookup"><span data-stu-id="63db4-131">Access the ScrollManipulationPropertySet via ElementCompositionPreview.</span></span>
    - `ElementCompositionPreview.GetScrollManipulationPropertySet(ScrollViewer scroller)`
1. <span data-ttu-id="63db4-132">Erstellen Sie eine ExpressionAnimation, die auf die Eigenschaft Translation des PropertySet verweist.</span><span class="sxs-lookup"><span data-stu-id="63db4-132">Create an ExpressionAnimation that references the Translation property from the PropertySet.</span></span>
    - <span data-ttu-id="63db4-133">Vergessen Sie nicht, den Referenzparameter festzulegen!</span><span class="sxs-lookup"><span data-stu-id="63db4-133">Don’t forget to set the Reference Parameter!</span></span>
1. <span data-ttu-id="63db4-134">Mit der ExpressionAnimation können Sie die Eigenschaft eines CompositionObjects gezielt ansteuern.</span><span class="sxs-lookup"><span data-stu-id="63db4-134">Target a CompositionObject’s property with the ExpressionAnimation.</span></span>

> [!NOTE]
> <span data-ttu-id="63db4-135">Es wird empfohlen, das PropertySet, das von der Methode GetScrollManipulationPropertySet zurückgegeben wird, einer Klassenvariablen zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="63db4-135">It is recommended that you assign the PropertySet returned from the GetScrollManipulationPropertySet method to a class variable.</span></span> <span data-ttu-id="63db4-136">Dies stellt sicher, dass das Property-Set nicht durch die Garbage-Collection bereinigt wird und hat somit keinen Einfluss auf die ExpressionAnimation, in der es referenziert wird.</span><span class="sxs-lookup"><span data-stu-id="63db4-136">This ensures that the property set does not get cleaned up by Garbage Collection and thus does not have any effect on the ExpressionAnimation it is referenced in.</span></span> <span data-ttu-id="63db4-137">ExpressionAnimations hat keine starke Referenz auf die in der Gleichung verwendeten Objekte.</span><span class="sxs-lookup"><span data-stu-id="63db4-137">ExpressionAnimations do not maintain a strong reference to any of the objects used in the equation.</span></span>

## <a name="example"></a><span data-ttu-id="63db4-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="63db4-138">Example</span></span>

<span data-ttu-id="63db4-139">Schauen wir uns an, wie das oben gezeigte Parallax-Beispiel zusammengesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="63db4-139">Let's take a look at how the Parallax sample shown above is put together.</span></span> <span data-ttu-id="63db4-140">Als Referenz finden Sie den gesamten Quellcode der App im [Window UI Dev Labs-Repo auf GitHub](https://github.com/Microsoft/WindowsUIDevLabs).</span><span class="sxs-lookup"><span data-stu-id="63db4-140">For reference, all the source code for the app is found in the [Window UI Dev Labs repo on GitHub](https://github.com/Microsoft/WindowsUIDevLabs).</span></span>

<span data-ttu-id="63db4-141">Das Erste ist, eine Referenz auf das ScrollManipulationPropertySet zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="63db4-141">The first thing is to get a reference to the ScrollManipulationPropertySet.</span></span>

```csharp
_scrollProperties =
    ElementCompositionPreview.GetScrollViewerManipulationPropertySet(myScrollViewer);
```

<span data-ttu-id="63db4-142">Der nächste Schritt ist die ExpressionAnimation, die eine Gleichung definiert, die die Scroll-Position des ScrollViewer verwendet.</span><span class="sxs-lookup"><span data-stu-id="63db4-142">The next step is to create the ExpressionAnimation that defines an equation that utilizes the scroll Position of the ScrollViewer.</span></span>

```csharp
_parallaxExpression = compositor.CreateExpressionAnimation();
_parallaxExpression.SetScalarParameter("StartOffset", 0.0f);
_parallaxExpression.SetScalarParameter("ParallaxValue", 0.5f);
_parallaxExpression.SetScalarParameter("ItemHeight", 0.0f);
_parallaxExpression.SetReferenceParameter("ScrollManipulation", _scrollProperties);
_parallaxExpression.Expression = "(ScrollManipulation.Translation.Y + StartOffset - (0.5 * ItemHeight)) * ParallaxValue - (ScrollManipulation.Translation.Y + StartOffset - (0.5 * ItemHeight))";
```

> [!NOTE]
> <span data-ttu-id="63db4-143">Sie können auch die ExpressionBuilder-Helper-Klassen verwenden, um denselben Ausdruck ohne Zeichenfolgen zu konstruieren:</span><span class="sxs-lookup"><span data-stu-id="63db4-143">You can also utilize ExpressionBuilder helper classes to construct this same Expression without the need for Strings:</span></span>

> ```csharp
> var scrollPropSet = _scrollProperties.GetSpecializedReference<ManipulationPropertySetReferenceNode>();
> var parallaxValue = 0.5f;
> var parallax = (scrollPropSet.Translation.Y + startOffset);
> _parallaxExpression = parallax * parallaxValue - parallax;
> ```

<span data-ttu-id="63db4-144">Schließlich nehmen Sie diese ExpressionAnimation und zielen auf das Visual, dass Sie per Parallax animieren wollen.</span><span class="sxs-lookup"><span data-stu-id="63db4-144">Finally, you take this ExpressionAnimation and target the Visual that you want to parallax.</span></span> <span data-ttu-id="63db4-145">In diesem Fall ist es das Bild für jeden Eintrag in der Liste.</span><span class="sxs-lookup"><span data-stu-id="63db4-145">In this case, it is the image for each of the items in the list.</span></span>

```csharp
Visual visual = ElementCompositionPreview.GetElementVisual(image);
visual.StartAnimation("Offset.Y", _parallaxExpression);
```