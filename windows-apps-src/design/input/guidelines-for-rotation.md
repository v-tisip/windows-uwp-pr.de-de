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
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 9cc30dbd9fd501d310bb037726414356354af294
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1653419"
---
# <a name="rotation"></a><span data-ttu-id="9ca45-103">Drehung</span><span class="sxs-lookup"><span data-stu-id="9ca45-103">Rotation</span></span>


<span data-ttu-id="9ca45-104">In diesem Artikel wird die neue Windows-Benutzeroberfläche beschrieben, die Drehungen unterstützt. Außerdem enthält das Thema Richtlinien für die Benutzeroberfläche, die Sie berücksichtigen sollten, wenn Sie diesen neuen Interaktionsmechanismus in einer UWP-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="9ca45-104">This article describes the new Windows UI for rotation and provides user experience guidelines that should be considered when using this new interaction mechanism in your UWP app.</span></span>

> <span data-ttu-id="9ca45-105">**Wichtige APIs**: [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994)</span><span class="sxs-lookup"><span data-stu-id="9ca45-105">**Important APIs**: [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994)</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="9ca45-106">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="9ca45-106">Dos and don'ts</span></span>

-   <span data-ttu-id="9ca45-107">Verwenden Sie Drehung, damit Benutzer leichter UI-Elemente direkt drehen können.</span><span class="sxs-lookup"><span data-stu-id="9ca45-107">Use rotation to help users directly rotate UI elements.</span></span>

## <a name="additional-usage-guidance"></a><span data-ttu-id="9ca45-108">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="9ca45-108">Additional usage guidance</span></span>


**<span data-ttu-id="9ca45-109">Übersicht über Drehung</span><span class="sxs-lookup"><span data-stu-id="9ca45-109">Overview of rotation</span></span>**

<span data-ttu-id="9ca45-110">Die Drehung ist eine für Touchscreens optimierte Technik, die von UWP-Apps verwendet wird und mit der Benutzer ein Objekt kreisförmig drehen können (im Uhrzeigersinn oder gegen den Uhrzeigersinn).</span><span class="sxs-lookup"><span data-stu-id="9ca45-110">Rotation is the touch-optimized technique used by UWP apps to enable users to turn an object in a circular direction (clockwise or counter-clockwise).</span></span>

<span data-ttu-id="9ca45-111">Abhängig vom Eingabegerät wird für die Drehungsinteraktion Folgendes verwendet:</span><span class="sxs-lookup"><span data-stu-id="9ca45-111">Depending on the input device, the rotation interaction is performed using:</span></span>

-   <span data-ttu-id="9ca45-112">Eine Maus oder ein aktiver Zeichenstift/Eingabestift zum Verschieben des Drehungsziehelements eines ausgewählten Objekts.</span><span class="sxs-lookup"><span data-stu-id="9ca45-112">A mouse or active pen/stylus to move the rotation gripper of a selected object.</span></span>
-   <span data-ttu-id="9ca45-113">Berührung oder passiver Zeichen-/Eingabestift zum Drehen des Objekts in die gewünschte Richtung mit der Drehbewegung.</span><span class="sxs-lookup"><span data-stu-id="9ca45-113">Touch or passive pen/stylus to turn the object in the desired direction using the rotate gesture.</span></span>

**<span data-ttu-id="9ca45-114">Gründe für die Verwendung von Drehung</span><span class="sxs-lookup"><span data-stu-id="9ca45-114">When to use rotation</span></span>**

<span data-ttu-id="9ca45-115">Verwenden Sie Drehung, damit Benutzer leichter UI-Elemente direkt drehen können.</span><span class="sxs-lookup"><span data-stu-id="9ca45-115">Use rotation to help users directly rotate UI elements.</span></span> <span data-ttu-id="9ca45-116">In den folgenden Diagrammen sehen Sie einige der unterstützten Fingerpositionen für die Drehungsinteraktion.</span><span class="sxs-lookup"><span data-stu-id="9ca45-116">The following diagrams show some of the supported finger positions for the rotation interaction.</span></span>

![Diagramm zur Veranschaulichung verschiedener Fingerhaltungen, die für Drehungen unterstützt werden](images/ux-rotate-positions.png)

**<span data-ttu-id="9ca45-118">Hinweis</span><span class="sxs-lookup"><span data-stu-id="9ca45-118">Note</span></span>**  
<span data-ttu-id="9ca45-119">Intuitiv ist der Drehungspunkt in den meisten Fällen einer der zwei Berührungspunkte, es sei denn, der Benutzer kann einen Drehungspunkt angeben, der in keinem Bezug zu den Kontaktpunkten steht (beispielsweise in einer Zeichen- oder Layoutanwendung).</span><span class="sxs-lookup"><span data-stu-id="9ca45-119">Intuitively, and in most cases, the rotation point is one of the two touch points unless the user can specify a rotation point unrelated to the contact points (for example, in a drawing or layout application).</span></span> <span data-ttu-id="9ca45-120">In den folgenden Abbildungen wird gezeigt, wie die Benutzeroberfläche beeinträchtigt werden kann, wenn der Drehungspunkt nicht auf diese Weise eingeschränkt ist.</span><span class="sxs-lookup"><span data-stu-id="9ca45-120">The following images demonstrate how the user experience can be degraded if the rotation point is not constrained in this way.</span></span>

<span data-ttu-id="9ca45-121">In der ersten Abbildung sehen Sie den ersten (Daumen) und den zweiten Berührungspunkt (Zeigefinger): Der Zeigefinger berührt einen Baum, und der Daumen berührt einen Holzblock.</span><span class="sxs-lookup"><span data-stu-id="9ca45-121">This first picture shows the initial (thumb) and secondary (index finger) touch points: the index finger is touching a tree and the thumb is touching a log.</span></span>

![Abbildung mit den zwei anfänglichen Berührungspunkten für die Drehbewegung](images/ux-rotate-points1.png)
<span data-ttu-id="9ca45-123">In dieser zweiten Abbildung wird die Drehung um den anfänglichen Berührungspunkt (Daumen) ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="9ca45-123">In this second picture, rotation is performed around the initial (thumb) touch point.</span></span> <span data-ttu-id="9ca45-124">Nach der Drehung berührt immer noch der Zeigefinger den Baumstamm und der Daumen den Holzblock (Drehungspunkt).</span><span class="sxs-lookup"><span data-stu-id="9ca45-124">After the rotation, the index finger is still touching the tree trunk and the thumb is still touching the log (the rotation point).</span></span>

![Abbildung mit einem gedrehten Bild, dessen Drehungspunkt durch einen der zwei anfänglichen Berührungspunkte eingeschränkt ist](images/ux-rotate-points2.png)
<span data-ttu-id="9ca45-126">In dieser dritten Abbildung wurde der Mittelpunkt der Drehung durch die Anwendung als Mittelpunkt des Bilds definiert (oder vom Benutzer entsprechend festgelegt).</span><span class="sxs-lookup"><span data-stu-id="9ca45-126">In this third picture, the center of rotation has been defined by the application (or set by the user) to be the center point of the picture.</span></span> <span data-ttu-id="9ca45-127">Da das Bild nicht um einen der Finger gedreht wurde, hat der Benutzer nach der Drehung nicht das Gefühl, direkt etwas geändert zu haben (es sei denn, er hat diese Einstellung ausgewählt).</span><span class="sxs-lookup"><span data-stu-id="9ca45-127">After the rotation, because the picture did not rotate around one of the fingers, the illusion of direct manipulation is broken (unless the user has chosen this setting).</span></span>

![Abbildung mit einem gedrehten Bild, dessen Drehungspunkt durch den Mittelpunkt des Bilds anstatt durch die zwei anfänglichen Berührungspunkte eingeschränkt ist](images/ux-rotate-points3.png)
<span data-ttu-id="9ca45-129">In dieser letzten Abbildung wurde der Mittelpunkt der Drehung durch die Anwendung als Mittelpunkt des Bilds definiert (oder vom Benutzer entsprechend festgelegt).</span><span class="sxs-lookup"><span data-stu-id="9ca45-129">In this last picture, the center of rotation has been defined by the application (or set by the user) to be a point in the middle of the left edge of the picture.</span></span> <span data-ttu-id="9ca45-130">Auch in diesem Fall hat der Benutzer nicht das Gefühl, direkt etwas geändert zu haben (es sei denn, er hat diese Einstellung ausgewählt).</span><span class="sxs-lookup"><span data-stu-id="9ca45-130">Again, unless the user has chosen this setting, the illusion of direct manipulation is broken in this case.</span></span>

![Abbildung mit einem gedrehten Bild, dessen Drehungspunkt durch den am weitesten links angeordneten Mittelpunkt des Bilds anstatt durch die zwei anfänglichen Berührungspunkte eingeschränkt ist](images/ux-rotate-points4.png)

 

<span data-ttu-id="9ca45-132">Windows8 unterstützt drei Drehungsarten: frei, eingeschränkt und kombiniert.</span><span class="sxs-lookup"><span data-stu-id="9ca45-132">Windows 8 supports three types of rotation: free, constrained, and combined.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="9ca45-133">Typ</span><span class="sxs-lookup"><span data-stu-id="9ca45-133">Type</span></span></th>
<th align="left"><span data-ttu-id="9ca45-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ca45-134">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9ca45-135">Freie Drehung</span><span class="sxs-lookup"><span data-stu-id="9ca45-135">Free rotation</span></span></td>
<td align="left"><p><span data-ttu-id="9ca45-136">Mit der freien Drehung können Benutzer Inhalte frei in einem beliebigen Bereich von 360Grad drehen. Wenn der Benutzer das Objekt ablegt, bleibt das Objekt in der ausgewählten Position.</span><span class="sxs-lookup"><span data-stu-id="9ca45-136">Free rotation enables a user to rotate content freely anywhere in a 360 degree arc. When the user releases the object, the object remains in the chosen position.</span></span> <span data-ttu-id="9ca45-137">Die freie Drehung ist hilfreich in Zeichen- und Layoutanwendungen wie beispielsweise MicrosoftPowerPoint, Word, Visio und Paint sowie Adobe Photoshop, Illustrator und Flash.</span><span class="sxs-lookup"><span data-stu-id="9ca45-137">Free rotation is useful for drawing and layout applications such as Microsoft PowerPoint, Word, Visio, and Paint; and Adobe Photoshop, Illustrator, and Flash.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9ca45-138">Eingeschränkte Drehung</span><span class="sxs-lookup"><span data-stu-id="9ca45-138">Constrained rotation</span></span></td>
<td align="left"><p><span data-ttu-id="9ca45-139">Die eingeschränkte Drehung unterstützt freie Drehung während der Änderung, erzwingt aber beim Loslassen Andockpunkte in 90-Grad-Schritten (0, 90, 180 und 270).</span><span class="sxs-lookup"><span data-stu-id="9ca45-139">Constrained rotation supports free rotation during the manipulation but enforces snap points at 90 degree increments (0, 90, 180, and 270) upon release.</span></span> <span data-ttu-id="9ca45-140">Wenn Benutzer das Objekt loslassen, wird es automatisch zum nächsten Andockpunkt gedreht.</span><span class="sxs-lookup"><span data-stu-id="9ca45-140">When the user releases the object, the object automatically rotates to the nearest snap point.</span></span></p>
<p><span data-ttu-id="9ca45-141">Die eingeschränkte Drehung ist die gängigste Drehungsmethode und funktioniert ähnlich wie ein Bildlauf in Inhalten.</span><span class="sxs-lookup"><span data-stu-id="9ca45-141">Constrained rotation is the most common method of rotation, and it functions in a similar way to scrolling content.</span></span> <span data-ttu-id="9ca45-142">Dank der Andockpunkte müssen Benutzer nicht präzise arbeiten und können trotzdem ihr Ziel erreichen.</span><span class="sxs-lookup"><span data-stu-id="9ca45-142">Snap points let a user be imprecise and still achieve their goal.</span></span> <span data-ttu-id="9ca45-143">Die eingeschränkte Drehung ist hilfreich für Anwendungen wie beispielsweise Webbrowser und Fotoalben.</span><span class="sxs-lookup"><span data-stu-id="9ca45-143">Constrained rotation is useful for applications such as web browsers and photo albums.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9ca45-144">Kombinierte Drehung</span><span class="sxs-lookup"><span data-stu-id="9ca45-144">Combined rotation</span></span></td>
<td align="left"><p><span data-ttu-id="9ca45-145">Die kombinierte Drehung unterstützt freie Drehung mit Zonen (ähnlich wie Führungsschienen unter <a href="guidelines-for-panning.md">Richtlinien für Verschiebung</a>) an jedem der 90-Grad-Andockpunkte, die durch die eingeschränkte Drehung erzwungen werden.</span><span class="sxs-lookup"><span data-stu-id="9ca45-145">Combined rotation supports free rotation with zones (similar to rails in <a href="guidelines-for-panning.md">Guidelines for panning</a>) at each of the 90 degree snap points enforced by constrained rotation.</span></span> <span data-ttu-id="9ca45-146">Wenn das Objekt außerhalb einer der 90-Grad-Zonen losgelassen wird, bleibt das Objekt in dieser Position. Anderenfalls wird das Objekt automatisch zu einem Andockpunkt gedreht.</span><span class="sxs-lookup"><span data-stu-id="9ca45-146">If the user releases the object outside of one of 90 degree zones, the object remains in that position; otherwise, the object automatically rotates to a snap point.</span></span></p>
<div class="alert"><span data-ttu-id="9ca45-147">
<strong>Hinweis</strong> Eine Benutzeroberflächen-Führungsschiene ist ein Feature, bei dem ein Bereich um ein Ziel die Bewegung zu einem bestimmten Wert oder einer bestimmten Stelle hin einschränkt, um die Auswahl zu beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="9ca45-147">
<strong>Note</strong>  A user interface rail is a feature in which an area around a target constrains movement towards some specific value or location to influence its selection.</span></span>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a><span data-ttu-id="9ca45-148">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9ca45-148">Related topics</span></span>


**<span data-ttu-id="9ca45-149">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9ca45-149">Samples</span></span>**
* [<span data-ttu-id="9ca45-150">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="9ca45-150">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="9ca45-151">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="9ca45-151">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="9ca45-152">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="9ca45-152">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="9ca45-153">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="9ca45-153">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="9ca45-154">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="9ca45-154">Archive samples</span></span>**
* [<span data-ttu-id="9ca45-155">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="9ca45-155">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="9ca45-156">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="9ca45-156">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="9ca45-157">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="9ca45-157">Input: Touch hit testing sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="9ca45-158">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="9ca45-158">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="9ca45-159">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="9ca45-159">Input: Simplified ink sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="9ca45-160">Eingabe: Gesten und Manipulationen mit GestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="9ca45-160">Input: Gestures and manipulations with GestureRecognizer</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="9ca45-161">Eingabe: Beispiel für Manipulationen und Gesten (C++)</span><span class="sxs-lookup"><span data-stu-id="9ca45-161">Input: Manipulations and gestures (C++) sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="9ca45-162">Beispiel für die DirectX-Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="9ca45-162">DirectX touch input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 




