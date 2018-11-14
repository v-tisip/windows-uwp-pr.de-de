---
author: jwmsft
title: Eingabegesteuerte Animationen
description: Erfahren Sie, wie Sie Eingabeanimationen in Ihrer App-Benutzeroberfläche verwenden.
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: 04eabb4c70143a08f5b850e6444f7f3d21a9dd4a
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "6462866"
---
# <a name="input-driven-animations"></a><span data-ttu-id="692dd-104">Eingabegesteuerte Animationen</span><span class="sxs-lookup"><span data-stu-id="692dd-104">Input-driven animations</span></span>

<span data-ttu-id="692dd-105">Dieser Artikel enthält eine Einführung in die InputAnimation-API und empfiehlt, wie Sie diese Arten von Animationen in Ihrer Benutzeroberfläche verwenden können.</span><span class="sxs-lookup"><span data-stu-id="692dd-105">This article provides an introduction to the InputAnimation API, and recommends how to use these types of animations in your UI.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="692dd-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="692dd-106">Prerequisites</span></span>

<span data-ttu-id="692dd-107">Wir gehen hier davon aus, dass Sie mit den in diesen Artikeln behandelten Konzepten vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="692dd-107">Here, we assume that you're familiar with the concepts discussed in these articles:</span></span>

- [<span data-ttu-id="692dd-108">Relationsbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="692dd-108">Relation based animations</span></span>](relation-animations.md)

## <a name="smooth-motion-driven-from-user-interactions"></a><span data-ttu-id="692dd-109">Reibungslose Bewegungsabläufe durch Benutzerinteraktion</span><span class="sxs-lookup"><span data-stu-id="692dd-109">Smooth motion driven from user interactions</span></span>

<span data-ttu-id="692dd-110">In der Fluent Design-Sprache ist die Interaktion zwischen Endbenutzern und Apps von größter Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="692dd-110">In the Fluent Design language, interaction between end users and apps is of the utmost importance.</span></span> <span data-ttu-id="692dd-111">Apps müssen nicht nur gut aussehen, sondern auch natürlich und dynamisch auf die Benutzer reagieren, die mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="692dd-111">Apps not only have to look the part, but also respond naturally and dynamically to the users that interact with them.</span></span> <span data-ttu-id="692dd-112">Das bedeutet, wenn ein Finger auf dem Bildschirm platziert wird, sollte die Benutzeroberfläche auf wechselnde Eingabegrade ansprechend reagieren; das Scrollen sollte sich glatt anfühlen und an einem Finger kleben, der über den Bildschirm schwenkt.</span><span class="sxs-lookup"><span data-stu-id="692dd-112">This means when a finger is placed on the screen, the UI should gracefully react to changing degrees of input; scrolling should feel smooth, and stick to a finger panning across the screen.</span></span>

<span data-ttu-id="692dd-113">Die Erstellung einer Benutzeroberfläche, die dynamisch und flüssig auf Benutzereingaben reagiert, führt einer besseren Einbeziehung der Benutzer. Bewegung sieht so nicht nur gut aus, sondern fühlt sich auch gut und natürlich an, wenn Benutzer mit Ihren unterschiedlichen Benutzererfahrungen interagieren.</span><span class="sxs-lookup"><span data-stu-id="692dd-113">Building UI that dynamically and fluidly responds to user input results in higher user engagement - Motion now not only looks good, but feels good and natural when users interact with your different UI experiences.</span></span> <span data-ttu-id="692dd-114">Dies ermöglicht den Endbenutzern eine einfachere Verbindung mit Ihrer Anwendung, wodurch das Erlebnis unvergesslicher und angenehmer wird.</span><span class="sxs-lookup"><span data-stu-id="692dd-114">This enables end users to more easily connect with your application, making the experience more memorable and delightful.</span></span>

## <a name="expanding-past-just-touch"></a><span data-ttu-id="692dd-115">Mehr als nur Touch</span><span class="sxs-lookup"><span data-stu-id="692dd-115">Expanding past just touch</span></span>

<span data-ttu-id="692dd-116">Obwohl Touch eine der gebräuchlichsten Oberflächen ist, die Endbenutzer zur Manipulation von UI-Inhalten verwenden, werden sie auch verschiedene andere Eingabemodalitäten wie Maus und Stift verwenden.</span><span class="sxs-lookup"><span data-stu-id="692dd-116">Although touch is one of the more common interfaces end users use to manipulate UI content, they will also use various other input modalities such mouse and pen.</span></span> <span data-ttu-id="692dd-117">In diesen Fällen ist es wichtig, dass die Endbenutzer erkennen, dass Ihre Benutzeroberfläche dynamisch auf ihre Eingaben reagiert, unabhängig davon, welche Eingabemodalität sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="692dd-117">In these cases, it is important that end users perceive that your UI responds dynamically to their input, regardless of what input modality they choose to use.</span></span> <span data-ttu-id="692dd-118">Sie sollten sich der verschiedenen Eingabemodalitäten bewusst sein, wenn Sie eingabegesteuerte Bewegungserlebnisse gestalten.</span><span class="sxs-lookup"><span data-stu-id="692dd-118">You should be cognizant of the different input modalities when designing input-driven motion experiences.</span></span>

## <a name="different-input-driven-motion-experiences"></a><span data-ttu-id="692dd-119">Unterschiedliche eingabegesteuerte Bewegungserfahrungen</span><span class="sxs-lookup"><span data-stu-id="692dd-119">Different Input-Driven Motion Experiences</span></span>

<span data-ttu-id="692dd-120">Der InputAnimation-Bereich bietet Ihnen verschiedene Möglichkeiten, dynamisch reagierende Bewegungen zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="692dd-120">The InputAnimation space provides several different experiences for you to create dynamically responding motion.</span></span> <span data-ttu-id="692dd-121">Wie der Rest des Windows-UI-Animationssystems arbeiten auch diese eingabegesteuerten Animationen mit einem unabhängigen Thread, was zum dynamischen Bewegungserlebnis beiträgt.</span><span class="sxs-lookup"><span data-stu-id="692dd-121">Like the rest of the Windows UI Animation system, these input-driven animations operate on an independent thread, which helps contribute to the dynamic motion experience.</span></span> <span data-ttu-id="692dd-122">In einigen Fällen, in denen die Erfahrung jedoch auf vorhandene XAML-Steuerelemente und -Komponenten zurückgreift, sind Teile dieser Erfahrungen immer noch UI-Thread-gebunden.</span><span class="sxs-lookup"><span data-stu-id="692dd-122">However, in some cases where the experience leverages existing XAML controls and components, parts of those experiences are still UI thread bound.</span></span>

<span data-ttu-id="692dd-123">Es gibt drei Haupterlebnisse, die Sie beim Erstellen dynamischer, eingabegesteuerter Bewegungsanimationen erstellen:</span><span class="sxs-lookup"><span data-stu-id="692dd-123">There are three core experiences that you create when building dynamic input-driven motion animations:</span></span>

1. <span data-ttu-id="692dd-124">Erweitern vorhandener ScrollView-Erfahrungen – Erweitern Sie die Position eines XAML ScrollViewers, um dynamische Animationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="692dd-124">Enhancing Existing ScrollView Experiences – enable the position of a XAML ScrollViewer to drive dynamic animation experiences.</span></span>
1. <span data-ttu-id="692dd-125">Durch die Zeigerpositions gesteuerte Erlebnisse – Nutzen Sie die Position eines Cursors auf einem Hit-getesteten UIElement, um dynamische Animationen zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="692dd-125">Pointer Position-driven Experiences – utilize the position of a cursor on a hit tested UIElement to drive dynamic animation experiences.</span></span>
1. <span data-ttu-id="692dd-126">Individuelle Manipulationserfahrungen mit InteractionTracker - Erstellen Sie mit InteractionTracker eine vollständig angepasste, Off-Thread-Manipulationserfahrung (z. B. Scrollen/Zoomen).</span><span class="sxs-lookup"><span data-stu-id="692dd-126">Custom Manipulation experiences with InteractionTracker – create a fully customized, off-thread manipulation experiences with InteractionTracker (such as a scrolling/zooming canvas).</span></span>

## <a name="enhancing-existing-scrollviewer-experiences"></a><span data-ttu-id="692dd-127">Erweitern vorhandener ScrollViewer-Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="692dd-127">Enhancing Existing ScrollViewer Experiences</span></span>

<span data-ttu-id="692dd-128">Eine der häufigsten Möglichkeiten, dynamischere Erlebnisse zu schaffen, ist es, auf einem bestehenden XAML-ScrollViewer-Steuerelement aufzubauen.</span><span class="sxs-lookup"><span data-stu-id="692dd-128">One of the common ways to create more dynamic experiences is to build on top of an existing XAML ScrollViewer control.</span></span> <span data-ttu-id="692dd-129">In diesen Situationen können Sie die Scroll-Position eines ScrollViewer nutzen, um zusätzliche UI-Komponenten zu erstellen, die ein einfaches Scrollerlebnis dynamischer machen.</span><span class="sxs-lookup"><span data-stu-id="692dd-129">In these situations, you leverage the scroll position of a ScrollViewer to create additional UI components that make a simple scrolling experience more dynamic.</span></span> <span data-ttu-id="692dd-130">Einige Beispiele sind Sticky/Shy Header und Parallax.</span><span class="sxs-lookup"><span data-stu-id="692dd-130">Some examples include Sticky/Shy Headers and Parallax.</span></span>

![Listenansicht mit Parallax](images/animation/parallax.gif)

![Ein Shy-Header](images/animation/shy-header.gif)

<span data-ttu-id="692dd-133">Bei der Schaffung dieser Art von Erfahrungen gibt es eine allgemeine Formel:</span><span class="sxs-lookup"><span data-stu-id="692dd-133">When creating these types of experiences, there is a general formula to follow:</span></span>

1. <span data-ttu-id="692dd-134">Rufen Sie das ScrollManipulationPropertySet aus dem XAML ScrollViewer auf, den Sie animieren möchten.</span><span class="sxs-lookup"><span data-stu-id="692dd-134">Access the ScrollManipulationPropertySet off of the XAML ScrollViewer you wish to drive an animation.</span></span>
    - <span data-ttu-id="692dd-135">Wird über die ElementCompositionPreview.GetScrollViewerManipulationPropertySet(UIElement element)-API durchgeführt</span><span class="sxs-lookup"><span data-stu-id="692dd-135">Done via the ElementCompositionPreview.GetScrollViewerManipulationPropertySet(UIElement element) API</span></span>
    - <span data-ttu-id="692dd-136">Gibt ein CompositionPropertySet mit einer **Translation**-Eigenschaft zurück</span><span class="sxs-lookup"><span data-stu-id="692dd-136">Returns a CompositionPropertySet containing a property called **Translation**</span></span>
1. <span data-ttu-id="692dd-137">Erstellen Sie eine Composition ExpressionAnimation mit einer Gleichung, die auf die Translation-Eigenschaft verweist.</span><span class="sxs-lookup"><span data-stu-id="692dd-137">Create a Composition ExpressionAnimation with an equation that references the Translation property.</span></span>
1. <span data-ttu-id="692dd-138">Starten Sie die Animation für die Eigenschaft eines CompositionObjects.</span><span class="sxs-lookup"><span data-stu-id="692dd-138">Start the animation on a CompositionObject’s property.</span></span>

<span data-ttu-id="692dd-139">Weitere Informationen zum Erstellen dieser Erfahrungen finden Sie unter [Erweitern vorhandener ScrollViewer-Erfahrungen](scroll-input-animations.md).</span><span class="sxs-lookup"><span data-stu-id="692dd-139">For more info on building these experiences, see [Enhance existing ScrollViewer experiences](scroll-input-animations.md).</span></span>

## <a name="pointer-position-driven-experiences"></a><span data-ttu-id="692dd-140">Durch die Zeigerposition gesteuerte Erlebnisse</span><span class="sxs-lookup"><span data-stu-id="692dd-140">Pointer Position-driven experiences</span></span>

<span data-ttu-id="692dd-141">Eine weitere häufige dynamische Erfahrung mit Eingaben ist es, eine Animation basierend auf der Position eines Zeigers wie z. B. eines Mauscursors zu steuern.</span><span class="sxs-lookup"><span data-stu-id="692dd-141">Another common dynamic experience involving input is to drive an animation based on the position of a pointer such as a Mouse cursor.</span></span> <span data-ttu-id="692dd-142">In diesen Situationen nutzen Entwickler die Position eines Cursors beim Hit-Testen in einem XAML-UIElement, was Erfahrungen wie Spotlight-Reveal ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="692dd-142">In these situations, developers leverage the location of a cursor when hit tested within a XAML UIElement that makes experiences like Spotlight Reveal possible to create.</span></span>

![Zeiger-Spotlight-Beispiel](images/animation/spotlight-reveal.gif)

![Zeiger-Rotations-Beispiel](images/animation/pointer-rotate.gif)

<span data-ttu-id="692dd-145">Bei der Schaffung dieser Art von Erfahrungen gibt es eine allgemeine Formel:</span><span class="sxs-lookup"><span data-stu-id="692dd-145">When creating these types of experiences, there is a general formula to follow:</span></span>

1. <span data-ttu-id="692dd-146">Rufen Sie das PointerPositionPropertySet von einem XAML-UIElement auf, von dem Sie de Cursorposition beim Hit-Testen wissen möchten.</span><span class="sxs-lookup"><span data-stu-id="692dd-146">Access the PointerPositionPropertySet off a XAML UIElement that you wish to know the cursor position when hit tested.</span></span>
    - <span data-ttu-id="692dd-147">Wird über die ElementCompositionPreview.GetPointerPositionPropertySet(UIElement element)-API durchgeführt</span><span class="sxs-lookup"><span data-stu-id="692dd-147">Done via the ElementCompositionPreview.GetPointerPositionPropertySet(UIElement element) API</span></span>
    - <span data-ttu-id="692dd-148">Gibt ein CompositionPropertySet mit einer **Position**-Eigenschaft zurück</span><span class="sxs-lookup"><span data-stu-id="692dd-148">Returns a CompositionPropertySet containing a property called **Position**</span></span>
1. <span data-ttu-id="692dd-149">Erstellen Sie eine CompositionExpressionAnimation mit einer Gleichung, die auf die Position-Eigenschaft verweist.</span><span class="sxs-lookup"><span data-stu-id="692dd-149">Create a CompositionExpressionAnimation with an equation that references the Position property.</span></span>
1. <span data-ttu-id="692dd-150">Starten Sie die Animation für die Eigenschaft eines CompositionObjects.</span><span class="sxs-lookup"><span data-stu-id="692dd-150">Start the animation on a CompositionObject’s property.</span></span>

## <a name="custom-manipulation-experiences-with-interactiontracker"></a><span data-ttu-id="692dd-151">Angepasste Manipulation mit InteractionTracker</span><span class="sxs-lookup"><span data-stu-id="692dd-151">Custom manipulation experiences with InteractionTracker</span></span>

<span data-ttu-id="692dd-152">Eine der Herausforderungen bei der Verwendung eines XAML-ScrollViewer ist, dass er an den UI-Thread gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="692dd-152">One of the challenges with utilizing a XAML ScrollViewer is that it is bound to the UI thread.</span></span> <span data-ttu-id="692dd-153">Daher kann das Scrollen und Zoomen oft verzögern und stottern, wenn der UI-Thread beschäftigt ist, und zu einem unattraktiven Erlebnis führt.</span><span class="sxs-lookup"><span data-stu-id="692dd-153">As a result, the scrolling and zooming experience can often lag and jitter if the UI thread becomes busy and results in an unappealing experience.</span></span> <span data-ttu-id="692dd-154">Darüber hinaus ist es nicht möglich, viele Aspekte des ScrollViewer-Erlebnisses anzupassen.</span><span class="sxs-lookup"><span data-stu-id="692dd-154">In addition, it is not possible to customize many aspects of the ScrollViewer experience.</span></span> <span data-ttu-id="692dd-155">InteractionTracker wurde entwickelt, um beide Probleme zu lösen, indem eine Reihe von Bausteinen zur Verfügung gestellt wird, um benutzerdefinierte Manipulationserfahrungen zu erstellen, die in einem unabhängigen Thread ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="692dd-155">InteractionTracker was created to solve both issues by providing a set of building blocks to create custom manipulation experiences that are run on an independent thread.</span></span>

![Beispiel für 3D-Interaktionen](images/animation/interactions-3d.gif)

![Beispiel zum Ziehen zum Animieren](images/animation/pull-to-animate.gif)

<span data-ttu-id="692dd-158">Bei der Erstellung von Erfahrungen mit InteractionTracker gibt es eine allgemeine Formel:</span><span class="sxs-lookup"><span data-stu-id="692dd-158">When creating experiences with InteractionTracker, there is a general formula to follow:</span></span>

1. <span data-ttu-id="692dd-159">Erstellen Sie Ihr InteractionTracker-Objekt und definieren Sie dessen Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="692dd-159">Create your InteractionTracker object and define its properties.</span></span>
1. <span data-ttu-id="692dd-160">Erstellen Sie VisualInteractionSources für jedes CompositionVisual, das Eingaben für InteractionTracker erfassen soll.</span><span class="sxs-lookup"><span data-stu-id="692dd-160">Create VisualInteractionSources for any CompositionVisual that should capture input for InteractionTracker to consume.</span></span>
1. <span data-ttu-id="692dd-161">Erstellen Sie eine Composition ExpressionAnimation mit einer Gleichung, die auf die Position-Eigenschaft von InteractionTracker verweist.</span><span class="sxs-lookup"><span data-stu-id="692dd-161">Create a Composition ExpressionAnimation with an equation that references the Position property of InteractionTracker.</span></span>
1. <span data-ttu-id="692dd-162">Starten Sie die Animation für eine Composition Visual-Eigenschaft, die von InteractionTracker gesteuert werden soll.</span><span class="sxs-lookup"><span data-stu-id="692dd-162">Start the animation on a Composition Visual’s property that you wish to be driven by InteractionTracker.</span></span>
