---
author: Karl-Bridge-Microsoft
Description: This topic describes Windows zooming and resizing elements and provides user experience guidelines for using these interaction mechanisms in your apps.
title: Richtlinien für optischen Zoom und Größenänderung
ms.assetid: 51a0007c-8a5d-4c44-ac9f-bbbf092b8a00
label: Optical zoom and resizing
template: detail.hbs
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f1643638eaf7eb625defe1f25b44cae20faf0a5c
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2018
ms.locfileid: "5990359"
---
# <a name="optical-zoom-and-resizing"></a><span data-ttu-id="eb8a7-103">Optischer Zoom und Größenänderung</span><span class="sxs-lookup"><span data-stu-id="eb8a7-103">Optical zoom and resizing</span></span>



<span data-ttu-id="eb8a7-104">In diesem Artikel werden die Windows-Elemente für das Zoomen und die Größenänderung beschrieben. Außerdem enthält das Thema Richtlinien für die Benutzeroberfläche, um diese Interaktionsmechanismen in Ihren Apps zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-104">This article describes Windows zooming and resizing elements and provides user experience guidelines for using these interaction mechanisms in your apps.</span></span>

> <span data-ttu-id="eb8a7-105">**Wichtige APIs**: [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Input (XAML)**](https://msdn.microsoft.com/library/windows/apps/br227994)</span><span class="sxs-lookup"><span data-stu-id="eb8a7-105">**Important APIs**: [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Input (XAML)**](https://msdn.microsoft.com/library/windows/apps/br227994)</span></span>

<span data-ttu-id="eb8a7-106">Mithilfe des optischen Zooms können Benutzer die Ansicht des Inhalts in einem Inhaltsbereich vergrößern (die Vergrößerung erfolgt für den gesamten Inhaltsbereich). Bei der Größenänderung hingegen können Benutzer die relative Größe eines oder mehrerer Objekte ändern, ohne die Ansicht des Inhaltsbereichs zu ändern (die Größenänderung erfolgt für die Objekte im Inhaltsbereich).</span><span class="sxs-lookup"><span data-stu-id="eb8a7-106">Optical zoom lets users magnify their view of the content within a content area (it is performed on the content area itself), whereas resizing enables users to change the relative size of one or more objects without changing the view of the content area (it is performed on the objects within the content area).</span></span>

<span data-ttu-id="eb8a7-107">Der optische Zoom und die Größenänderung (Interaktion) werden mit den Bewegungen für Zusammendrücken und Aufziehen ausgeführt (durch Auseinanderbewegen der Finger wird vergrößert, und durch Zueinanderbewegen der Finger wird verkleinert). Alternativ können Benutzer die STRG-Taste gedrückt halten und gleichzeitig das Mausrad drehen oder die STRG-Taste gedrückt halten (wenn keine Zehnertastatur verfügbar ist, zusammen mit der UMSCHALTTASTE) und die Taste mit dem Pluszeichen (+) oder dem Minuszeichen (-) drücken.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-107">Both optical zoom and resizing interactions are performed through the pinch and stretch gestures (moving fingers farther apart zooms in and moving them closer together zooms out), or by holding the Ctrl key down while scrolling the mouse scroll wheel, or by holding the Ctrl key down (with the Shift key, if no numeric keypad is available) and pressing the plus (+) or minus (-) key.</span></span>

<span data-ttu-id="eb8a7-108">Die folgenden Diagramme verdeutlichen die Unterschiede zwischen Größenänderung und optischem Zoom.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-108">The following diagrams demonstrate the differences between resizing and optical zooming.</span></span>

<span data-ttu-id="eb8a7-109">**Optischer Zoom**: Der Benutzer wählt einen Bereich aus und vergrößert den gesamten Bereich.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-109">**Optical zoom**: User selects an area, and then zooms into the entire area.</span></span>

![Wenn die Finger aufeinander zu bewegt werden, wird der Inhaltsbereich vergrößert, beim Spreizen der Finger wird er verkleinert.](images/areazoom.png)

<span data-ttu-id="eb8a7-111">**Größe ändern**: Der Benutzer wählt ein Objekt in einem Bereich aus und ändert die Größe dieses Objekts.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-111">**Resize**: User selects an object within an area, and resizes that object.</span></span>

![Wenn die Finger aufeinander zu bewegt werden, wird das Objekt verkleinert, beim Spreizen der Finger wird es vergrößert.](images/objectresize.png)

<span data-ttu-id="eb8a7-113">**Hinweis:**  optischen Zoom dürfen nicht mit dem [Semantischen Zoom](../controls-and-patterns/semantic-zoom.md)verwechselt werden.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-113">**Note** Optical zoom shouldn't be confused with [Semantic Zoom](../controls-and-patterns/semantic-zoom.md).</span></span> <span data-ttu-id="eb8a7-114">Zwar werden bei beiden Interaktionen dieselben Gesten ausgeführt, jedoch bezieht sich der semantische Zoom auf die Darstellung von und die Navigation in Inhalten in einer einzelnen Ansicht (z.B. in der Ordnerstruktur eines Computers, einer Dokumentbibliothek oder einem Fotoalbum).</span><span class="sxs-lookup"><span data-stu-id="eb8a7-114">Although the same gestures are used for both interactions, semantic zoom refers to the presentation and navigation of content organized within a single view (such as the folder structure of a computer, a library of documents, or a photo album).</span></span>

 

## <a name="dos-and-donts"></a><span data-ttu-id="eb8a7-115">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="eb8a7-115">Dos and don'ts</span></span>


<span data-ttu-id="eb8a7-116">Beachten Sie die folgenden Richtlinien für Apps, die entweder Größenänderung oder optischen Zoom unterstützen.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-116">Use the following guidelines for apps that support either resizing or optical zooming:</span></span>

-   <span data-ttu-id="eb8a7-117">Wenn Beschränkungen oder Grenzen der maximalen und minimalen Größe definiert sind, sollte ein visuelles Feedback erfolgen, wenn der Benutzer die Grenzen erreicht oder überschreitet.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-117">If maximum and minimum size constraints or boundaries are defined, use visual feedback to demonstrate when the user reaches or exceeds those boundaries.</span></span>
-   <span data-ttu-id="eb8a7-118">Mit Andockpunkten kann das Zoom- und Größenänderungsverhalten beeinflusst werden, indem logische Punkte bereitgestellt werden, an denen die Manipulation angehalten und sichergestellt wird, dass eine bestimmte Teilmenge des Inhalts im Viewport angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-118">Use snap points to influence zooming and resizing behavior by providing logical points at which to stop the manipulation and ensure a specific subset of content is displayed in the viewport.</span></span> <span data-ttu-id="eb8a7-119">Stellen Sie Andockpunkte für gängige Zoomfaktoren oder logische Ansichten bereit, um die Auswahl dieser Zoomfaktoren zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-119">Provide snap points for common zoom levels or logical views to make it easier for a user to select those levels.</span></span> <span data-ttu-id="eb8a7-120">In Foto-Apps könnte z.B. ein Andockpunkt bei 100% für Größenänderungen bereitgestellt werden, und bei Karten-Apps könnten Andockpunkte in Ansichten von Städten, Staaten und Ländern/Regionen nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-120">For example, photo apps might provide a resizing snap point at 100% or, in the case of mapping apps, snap points might be useful at city, state, and country views.</span></span>

    <span data-ttu-id="eb8a7-121">Andockpunkte ermöglichen den Benutzern ungenaue Gesten, mit denen sie dennoch das Gewünschte erreichen.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-121">Snap points enable users to be imprecise and still achieve their goals.</span></span> <span data-ttu-id="eb8a7-122">Wenn Sie mit XAML arbeiten, finden Sie weitere Informationen unter den Eigenschaften der Andockpunkte von [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/br209527).</span><span class="sxs-lookup"><span data-stu-id="eb8a7-122">If you're using XAML, see the snap points properties of [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/br209527).</span></span> <span data-ttu-id="eb8a7-123">Verwenden Sie für JavaScript und HTML [**-ms-content-zoom-snap-points**](https://msdn.microsoft.com/library/hh771895).</span><span class="sxs-lookup"><span data-stu-id="eb8a7-123">For JavaScript and HTML, use [**-ms-content-zoom-snap-points**](https://msdn.microsoft.com/library/hh771895).</span></span>

    <span data-ttu-id="eb8a7-124">Es gibt zwei Arten von Andockpunkten:</span><span class="sxs-lookup"><span data-stu-id="eb8a7-124">There are two types of snap-points:</span></span>

    -   <span data-ttu-id="eb8a7-125">Näherung – Nachdem der Kontakt aufhoben wurde, wird ein Andockpunkt ausgewählt, wenn die Trägheitsbewegung innerhalb einer Distanzschwelle zum Andockpunkt anhält.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-125">Proximity - After the contact is lifted, a snap point is selected if inertia stops within a distance threshold of the snap point.</span></span> <span data-ttu-id="eb8a7-126">Bei Näherungsandockpunkten kann ein Zoom- oder Größenänderungsvorgang zwischen Andockpunkten enden.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-126">Proximity snap points still allow a zoom or resize to end between snap points.</span></span>
    -   <span data-ttu-id="eb8a7-127">Erforderlich – Der ausgewählte Andockpunkt ist der Punkt direkt vor oder nach dem Andockpunkt, der vor dem Aufheben des Kontakts zuletzt überschritten wurde (abhängig von der Richtung und Geschwindigkeit der Geste).</span><span class="sxs-lookup"><span data-stu-id="eb8a7-127">Mandatory - The snap point selected is the one that immediately precedes or succeeds the last snap point crossed before the contact was lifted (depending on the direction and velocity of the gesture).</span></span> <span data-ttu-id="eb8a7-128">Eine Manipulation muss an einem erforderlichen Andockpunkt enden.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-128">A manipulation must end on a mandatory snap point.</span></span>
-   <span data-ttu-id="eb8a7-129">Verwenden Sie Trägheitseffekte.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-129">Use inertia physics.</span></span> <span data-ttu-id="eb8a7-130">Dazu zählen:</span><span class="sxs-lookup"><span data-stu-id="eb8a7-130">These include the following:</span></span>
    -   <span data-ttu-id="eb8a7-131">Verlangsamung: Findet statt, wenn der Benutzer mit dem Zusammendrücken oder Aufziehen aufhört.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-131">Deceleration: Occurs when the user stops pinching or stretching.</span></span> <span data-ttu-id="eb8a7-132">Dies ist mit allmählichem Anhalten auf glattem Untergrund vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-132">This is similar to sliding to a stop on a slippery surface.</span></span>
    -   <span data-ttu-id="eb8a7-133">Springen: Beim Überschreiten einer Größeneinschränkung oder -grenze erfolgt ein leichter Rückpralleffekt.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-133">Bounce: A slight bounce-back effect occurs when a size constraint or boundary is passed.</span></span>
-   <span data-ttu-id="eb8a7-134">Verteilen Sie die Steuerelemente entsprechend den [Richtlinien für Zielbestimmung](guidelines-for-targeting.md).</span><span class="sxs-lookup"><span data-stu-id="eb8a7-134">Space controls according to the [Guidelines for targeting](guidelines-for-targeting.md).</span></span>
-   <span data-ttu-id="eb8a7-135">Stellen Sie für eine eingeschränkte Größenänderung Ziehpunkte für die Skalierung bereit.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-135">Provide scaling handles for constrained resizing.</span></span> <span data-ttu-id="eb8a7-136">Wenn keine Ziehpunkte angegeben werden, wird standardmäßig die isometrische bzw. proportionale Größenänderung verwendet.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-136">Isometric, or proportional, resizing is the default if the handles are not specified.</span></span>
-   <span data-ttu-id="eb8a7-137">Verwenden Sie nicht den Zoom, um in der UI zu navigieren oder zusätzliche Steuerelemente in der App verfügbar zu machen, sondern verwenden Sie stattdessen Verschiebungen.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-137">Don't use zooming to navigate the UI or expose additional controls within your app, use a panning region instead.</span></span> <span data-ttu-id="eb8a7-138">Weitere Informationen zur Verschiebung finden Sie unter [Richtlinien für Verschiebung](guidelines-for-panning.md).</span><span class="sxs-lookup"><span data-stu-id="eb8a7-138">For more info on panning, see [Guidelines for panning](guidelines-for-panning.md).</span></span>
-   <span data-ttu-id="eb8a7-139">Platzieren Sie keine in der Größe veränderbare Objekte in einem Inhaltsbereich, dessen Größe geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-139">Don't put resizable objects within a resizable content area.</span></span> <span data-ttu-id="eb8a7-140">Ausnahmen bilden die folgenden Fälle:</span><span class="sxs-lookup"><span data-stu-id="eb8a7-140">Exceptions to this include:</span></span>
    -   <span data-ttu-id="eb8a7-141">Zeichnungsprogramme, in denen in der Größe anpassbare Elemente in einem Zeichenbereich oder auf einer Zeichenfläche, dessen bzw. deren Größe geändert werden kann, angezeigt werden können</span><span class="sxs-lookup"><span data-stu-id="eb8a7-141">Drawing applications where resizable items can appear on a resizable canvas or art board.</span></span>
    -   <span data-ttu-id="eb8a7-142">Webseiten mit einem eingebetteten Objekt, z.B. einer Karte</span><span class="sxs-lookup"><span data-stu-id="eb8a7-142">Webpages with an embedded object such as a map.</span></span>

    <span data-ttu-id="eb8a7-143">**Hinweis:**  In allen Fällen wird der Inhaltsbereich angepasst, es sei denn, alle Berührungspunkte innerhalb der Größe anpassbaren Objekt sind.</span><span class="sxs-lookup"><span data-stu-id="eb8a7-143">**Note** In all cases, the content area is resized unless all touch points are within the resizable object.</span></span>

     

## <a name="related-articles"></a><span data-ttu-id="eb8a7-144">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="eb8a7-144">Related articles</span></span>


**<span data-ttu-id="eb8a7-145">Beispiele</span><span class="sxs-lookup"><span data-stu-id="eb8a7-145">Samples</span></span>**
* [<span data-ttu-id="eb8a7-146">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="eb8a7-146">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="eb8a7-147">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="eb8a7-147">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="eb8a7-148">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="eb8a7-148">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="eb8a7-149">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="eb8a7-149">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="eb8a7-150">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="eb8a7-150">Archive samples</span></span>**
* [<span data-ttu-id="eb8a7-151">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="eb8a7-151">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="eb8a7-152">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="eb8a7-152">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="eb8a7-153">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="eb8a7-153">Input: Touch hit testing sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="eb8a7-154">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="eb8a7-154">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="eb8a7-155">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="eb8a7-155">Input: Simplified ink sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="eb8a7-156">Eingabe: Beispiel für Windows8-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="eb8a7-156">Input: Windows 8 gestures sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="eb8a7-157">Eingabe: Beispiel für Manipulationen und Gesten (C++)</span><span class="sxs-lookup"><span data-stu-id="eb8a7-157">Input: Manipulations and gestures (C++) sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="eb8a7-158">Beispiel für die DirectX-Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="eb8a7-158">DirectX touch input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 




