---
author: Karl-Bridge-Microsoft
Description: This topic describes the new Windows UI for rotation and provides user experience guidelines that should be considered when using this new interaction mechanism in your UWP app.
title: Drehung
ms.assetid: f098bc05-35b3-46b2-9e9b-9ff292d067ca
label: Rotation
template: detail.hbs
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 9bffed44921df05a72025e86917901a65fe7ea82
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5838688"
---
# <a name="rotation"></a><span data-ttu-id="2b6ef-103">Drehung</span><span class="sxs-lookup"><span data-stu-id="2b6ef-103">Rotation</span></span>


<span data-ttu-id="2b6ef-104">In diesem Artikel wird die neue Windows-Benutzeroberfläche beschrieben, die Drehungen unterstützt. Außerdem enthält das Thema Richtlinien für die Benutzeroberfläche, die Sie berücksichtigen sollten, wenn Sie diesen neuen Interaktionsmechanismus in einer UWP-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-104">This article describes the new Windows UI for rotation and provides user experience guidelines that should be considered when using this new interaction mechanism in your UWP app.</span></span>

> <span data-ttu-id="2b6ef-105">**Wichtige APIs**: [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994)</span><span class="sxs-lookup"><span data-stu-id="2b6ef-105">**Important APIs**: [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994)</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="2b6ef-106">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="2b6ef-106">Dos and don'ts</span></span>

-   <span data-ttu-id="2b6ef-107">Verwenden Sie Drehung, damit Benutzer leichter UI-Elemente direkt drehen können.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-107">Use rotation to help users directly rotate UI elements.</span></span>

## <a name="additional-usage-guidance"></a><span data-ttu-id="2b6ef-108">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="2b6ef-108">Additional usage guidance</span></span>


**<span data-ttu-id="2b6ef-109">Übersicht über Drehung</span><span class="sxs-lookup"><span data-stu-id="2b6ef-109">Overview of rotation</span></span>**

<span data-ttu-id="2b6ef-110">Die Drehung ist eine für Touchscreens optimierte Technik, die von UWP-Apps verwendet wird und mit der Benutzer ein Objekt kreisförmig drehen können (im Uhrzeigersinn oder gegen den Uhrzeigersinn).</span><span class="sxs-lookup"><span data-stu-id="2b6ef-110">Rotation is the touch-optimized technique used by UWP apps to enable users to turn an object in a circular direction (clockwise or counter-clockwise).</span></span>

<span data-ttu-id="2b6ef-111">Abhängig vom Eingabegerät wird für die Drehungsinteraktion Folgendes verwendet:</span><span class="sxs-lookup"><span data-stu-id="2b6ef-111">Depending on the input device, the rotation interaction is performed using:</span></span>

-   <span data-ttu-id="2b6ef-112">Eine Maus oder ein aktiver Zeichenstift/Eingabestift zum Verschieben des Drehungsziehelements eines ausgewählten Objekts.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-112">A mouse or active pen/stylus to move the rotation gripper of a selected object.</span></span>
-   <span data-ttu-id="2b6ef-113">Berührung oder passiver Zeichen-/Eingabestift zum Drehen des Objekts in die gewünschte Richtung mit der Drehbewegung.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-113">Touch or passive pen/stylus to turn the object in the desired direction using the rotate gesture.</span></span>

**<span data-ttu-id="2b6ef-114">Gründe für die Verwendung von Drehung</span><span class="sxs-lookup"><span data-stu-id="2b6ef-114">When to use rotation</span></span>**

<span data-ttu-id="2b6ef-115">Verwenden Sie Drehung, damit Benutzer leichter UI-Elemente direkt drehen können.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-115">Use rotation to help users directly rotate UI elements.</span></span> <span data-ttu-id="2b6ef-116">In den folgenden Diagrammen sehen Sie einige der unterstützten Fingerpositionen für die Drehungsinteraktion.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-116">The following diagrams show some of the supported finger positions for the rotation interaction.</span></span>

![Diagramm zur Veranschaulichung verschiedener Fingerhaltungen, die für Drehungen unterstützt werden](images/ux-rotate-positions.png)

<span data-ttu-id="2b6ef-118">**Hinweis:**  intuitiv in den meisten Fällen ist der drehungspunkt ist einer der zwei Berührungspunkte, wenn der Benutzer kann einen drehungspunkt Bezug zu den Kontaktpunkten (z. B. in einer Zeichen- oder layoutanwendung) angeben.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-118">**Note** Intuitively, and in most cases, the rotation point is one of the two touch points unless the user can specify a rotation point unrelated to the contact points (for example, in a drawing or layout application).</span></span> <span data-ttu-id="2b6ef-119">In den folgenden Abbildungen wird gezeigt, wie die Benutzeroberfläche beeinträchtigt werden kann, wenn der Drehungspunkt nicht auf diese Weise eingeschränkt ist.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-119">The following images demonstrate how the user experience can be degraded if the rotation point is not constrained in this way.</span></span>

<span data-ttu-id="2b6ef-120">In der ersten Abbildung sehen Sie den ersten (Daumen) und den zweiten Berührungspunkt (Zeigefinger): Der Zeigefinger berührt einen Baum, und der Daumen berührt einen Holzblock.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-120">This first picture shows the initial (thumb) and secondary (index finger) touch points: the index finger is touching a tree and the thumb is touching a log.</span></span>

![Abbildung mit den zwei anfänglichen Berührungspunkten für die Drehbewegung](images/ux-rotate-points1.png)
<span data-ttu-id="2b6ef-122">In dieser zweiten Abbildung wird die Drehung um den anfänglichen Berührungspunkt (Daumen) ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-122">In this second picture, rotation is performed around the initial (thumb) touch point.</span></span> <span data-ttu-id="2b6ef-123">Nach der Drehung berührt immer noch der Zeigefinger den Baumstamm und der Daumen den Holzblock (Drehungspunkt).</span><span class="sxs-lookup"><span data-stu-id="2b6ef-123">After the rotation, the index finger is still touching the tree trunk and the thumb is still touching the log (the rotation point).</span></span>

![Abbildung mit einem gedrehten Bild, dessen Drehungspunkt durch einen der zwei anfänglichen Berührungspunkte eingeschränkt ist](images/ux-rotate-points2.png)
<span data-ttu-id="2b6ef-125">In dieser dritten Abbildung wurde der Mittelpunkt der Drehung durch die Anwendung als Mittelpunkt des Bilds definiert (oder vom Benutzer entsprechend festgelegt).</span><span class="sxs-lookup"><span data-stu-id="2b6ef-125">In this third picture, the center of rotation has been defined by the application (or set by the user) to be the center point of the picture.</span></span> <span data-ttu-id="2b6ef-126">Da das Bild nicht um einen der Finger gedreht wurde, hat der Benutzer nach der Drehung nicht das Gefühl, direkt etwas geändert zu haben (es sei denn, er hat diese Einstellung ausgewählt).</span><span class="sxs-lookup"><span data-stu-id="2b6ef-126">After the rotation, because the picture did not rotate around one of the fingers, the illusion of direct manipulation is broken (unless the user has chosen this setting).</span></span>

![Abbildung mit einem gedrehten Bild, dessen Drehungspunkt durch den Mittelpunkt des Bilds anstatt durch die zwei anfänglichen Berührungspunkte eingeschränkt ist](images/ux-rotate-points3.png)
<span data-ttu-id="2b6ef-128">In dieser letzten Abbildung wurde der Mittelpunkt der Drehung durch die Anwendung als Mittelpunkt des Bilds definiert (oder vom Benutzer entsprechend festgelegt).</span><span class="sxs-lookup"><span data-stu-id="2b6ef-128">In this last picture, the center of rotation has been defined by the application (or set by the user) to be a point in the middle of the left edge of the picture.</span></span> <span data-ttu-id="2b6ef-129">Auch in diesem Fall hat der Benutzer nicht das Gefühl, direkt etwas geändert zu haben (es sei denn, er hat diese Einstellung ausgewählt).</span><span class="sxs-lookup"><span data-stu-id="2b6ef-129">Again, unless the user has chosen this setting, the illusion of direct manipulation is broken in this case.</span></span>

![Abbildung mit einem gedrehten Bild, dessen Drehungspunkt durch den am weitesten links angeordneten Mittelpunkt des Bilds anstatt durch die zwei anfänglichen Berührungspunkte eingeschränkt ist](images/ux-rotate-points4.png)

 

<span data-ttu-id="2b6ef-131">Windows8 unterstützt drei drehungsarten: frei, eingeschränkt und kombiniert.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-131">Windows8 supports three types of rotation: free, constrained, and combined.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2b6ef-132">Typ</span><span class="sxs-lookup"><span data-stu-id="2b6ef-132">Type</span></span></th>
<th align="left"><span data-ttu-id="2b6ef-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2b6ef-133">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2b6ef-134">Freie Drehung</span><span class="sxs-lookup"><span data-stu-id="2b6ef-134">Free rotation</span></span></td>
<td align="left"><p><span data-ttu-id="2b6ef-135">Mit der freien Drehung können Benutzer Inhalte frei in einem beliebigen Bereich von 360Grad drehen. Wenn der Benutzer das Objekt ablegt, bleibt das Objekt in der ausgewählten Position.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-135">Free rotation enables a user to rotate content freely anywhere in a 360 degree arc. When the user releases the object, the object remains in the chosen position.</span></span> <span data-ttu-id="2b6ef-136">Die freie Drehung ist hilfreich in Zeichen- und Layoutanwendungen wie beispielsweise MicrosoftPowerPoint, Word, Visio und Paint sowie Adobe Photoshop, Illustrator und Flash.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-136">Free rotation is useful for drawing and layout applications such as Microsoft PowerPoint, Word, Visio, and Paint; and Adobe Photoshop, Illustrator, and Flash.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2b6ef-137">Eingeschränkte Drehung</span><span class="sxs-lookup"><span data-stu-id="2b6ef-137">Constrained rotation</span></span></td>
<td align="left"><p><span data-ttu-id="2b6ef-138">Die eingeschränkte Drehung unterstützt freie Drehung während der Änderung, erzwingt aber beim Loslassen Andockpunkte in 90-Grad-Schritten (0, 90, 180 und 270).</span><span class="sxs-lookup"><span data-stu-id="2b6ef-138">Constrained rotation supports free rotation during the manipulation but enforces snap points at 90 degree increments (0, 90, 180, and 270) upon release.</span></span> <span data-ttu-id="2b6ef-139">Wenn Benutzer das Objekt loslassen, wird es automatisch zum nächsten Andockpunkt gedreht.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-139">When the user releases the object, the object automatically rotates to the nearest snap point.</span></span></p>
<p><span data-ttu-id="2b6ef-140">Die eingeschränkte Drehung ist die gängigste Drehungsmethode und funktioniert ähnlich wie ein Bildlauf in Inhalten.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-140">Constrained rotation is the most common method of rotation, and it functions in a similar way to scrolling content.</span></span> <span data-ttu-id="2b6ef-141">Dank der Andockpunkte müssen Benutzer nicht präzise arbeiten und können trotzdem ihr Ziel erreichen.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-141">Snap points let a user be imprecise and still achieve their goal.</span></span> <span data-ttu-id="2b6ef-142">Die eingeschränkte Drehung ist hilfreich für Anwendungen wie beispielsweise Webbrowser und Fotoalben.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-142">Constrained rotation is useful for applications such as web browsers and photo albums.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2b6ef-143">Kombinierte Drehung</span><span class="sxs-lookup"><span data-stu-id="2b6ef-143">Combined rotation</span></span></td>
<td align="left"><p><span data-ttu-id="2b6ef-144">Die kombinierte Drehung unterstützt freie Drehung mit Zonen (ähnlich wie Führungsschienen unter <a href="guidelines-for-panning.md">Richtlinien für Verschiebung</a>) an jedem der 90-Grad-Andockpunkte, die durch die eingeschränkte Drehung erzwungen werden.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-144">Combined rotation supports free rotation with zones (similar to rails in <a href="guidelines-for-panning.md">Guidelines for panning</a>) at each of the 90 degree snap points enforced by constrained rotation.</span></span> <span data-ttu-id="2b6ef-145">Wenn das Objekt außerhalb einer der 90-Grad-Zonen losgelassen wird, bleibt das Objekt in dieser Position. Anderenfalls wird das Objekt automatisch zu einem Andockpunkt gedreht.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-145">If the user releases the object outside of one of 90 degree zones, the object remains in that position; otherwise, the object automatically rotates to a snap point.</span></span></p>
<div class="alert"><span data-ttu-id="2b6ef-146">
<strong>Hinweis:</strong>eine Benutzeroberflächen-Führungsschiene ist ein Feature, in denen ein Bereich um ein Ziel beschränkt die Bewegung zu einem bestimmten Wert oder Speicherort für die Auswahl zu beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="2b6ef-146">
<strong>Note</strong>A user interface rail is a feature in which an area around a target constrains movement towards some specific value or location to influence its selection.</span></span>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a><span data-ttu-id="2b6ef-147">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2b6ef-147">Related topics</span></span>


**<span data-ttu-id="2b6ef-148">Beispiele</span><span class="sxs-lookup"><span data-stu-id="2b6ef-148">Samples</span></span>**
* [<span data-ttu-id="2b6ef-149">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="2b6ef-149">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="2b6ef-150">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="2b6ef-150">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="2b6ef-151">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="2b6ef-151">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="2b6ef-152">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="2b6ef-152">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="2b6ef-153">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="2b6ef-153">Archive samples</span></span>**
* [<span data-ttu-id="2b6ef-154">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="2b6ef-154">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="2b6ef-155">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="2b6ef-155">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="2b6ef-156">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="2b6ef-156">Input: Touch hit testing sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="2b6ef-157">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="2b6ef-157">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="2b6ef-158">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="2b6ef-158">Input: Simplified ink sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="2b6ef-159">Eingabe: Gesten und Manipulationen mit GestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="2b6ef-159">Input: Gestures and manipulations with GestureRecognizer</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="2b6ef-160">Eingabe: Beispiel für Manipulationen und Gesten (C++)</span><span class="sxs-lookup"><span data-stu-id="2b6ef-160">Input: Manipulations and gestures (C++) sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="2b6ef-161">Beispiel für die DirectX-Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="2b6ef-161">DirectX touch input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 




