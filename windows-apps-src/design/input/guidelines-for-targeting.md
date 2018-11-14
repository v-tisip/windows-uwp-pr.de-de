---
author: Karl-Bridge-Microsoft
Description: This topic describes the use of contact geometry for touch targeting and provides best practices for targeting in Windows Runtime apps.
title: Zielbestimmung
ms.assetid: 93ad2232-97f3-42f5-9e45-3fc2143ac4d2
label: Targeting
template: detail.hbs
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: bad800f3858cdfdf3def3a9a04854f078b3af399
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6154076"
---
# <a name="guidelines-for-targeting"></a><span data-ttu-id="410b2-103">Richtlinien für die Zielbestimmung</span><span class="sxs-lookup"><span data-stu-id="410b2-103">Guidelines for targeting</span></span>


<span data-ttu-id="410b2-104">Die Touchzielbestimmung in Windows verwendet den vollständigen Kontaktbereich jedes Fingers, der durch ein Touchdigitalisierungsgerät erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="410b2-104">Touch targeting in Windows uses the full contact area of each finger that is detected by a touch digitizer.</span></span> <span data-ttu-id="410b2-105">Die größere und komplexere Menge an Eingabedaten, die vom Digitalisierungsgerät gemeldet wird, wird verwendet, um die Präzision bei der Ermittlung des durch den Benutzer (höchstwahrscheinlich) beabsichtigten Ziels zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="410b2-105">The larger, more complex set of input data reported by the digitizer is used to increase precision when determining the user's intended (or most likely) target.</span></span>

> <span data-ttu-id="410b2-106">**Wichtige APIs**: [**Windows.UI.Core**](https://msdn.microsoft.com/library/windows/apps/br208383), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994)</span><span class="sxs-lookup"><span data-stu-id="410b2-106">**Important APIs**: [**Windows.UI.Core**](https://msdn.microsoft.com/library/windows/apps/br208383), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994)</span></span>

<span data-ttu-id="410b2-107">Dieses Thema beschreibt die Verwendung von Kontaktgeometrie zur Bestimmung von Touchzielen und enthält bewährte Methoden für Ziele in UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="410b2-107">This topic describes the use of contact geometry for touch targeting and provides best practices for targeting in UWP apps.</span></span>

## <a name="measurements-and-scaling"></a><span data-ttu-id="410b2-108">Maße und Skalierung</span><span class="sxs-lookup"><span data-stu-id="410b2-108">Measurements and scaling</span></span>


<span data-ttu-id="410b2-109">Um die Konsistenz bei unterschiedlichen Bildschirmgrößen und Pixeldichten zu wahren, sind alle Zielgrößen in physischen Einheiten (Millimeter) angegeben.</span><span class="sxs-lookup"><span data-stu-id="410b2-109">To remain consistent across different screen sizes and pixel densities, all target sizes are represented in physical units (millimeters).</span></span> <span data-ttu-id="410b2-110">Physische Einheiten können mit der folgenden Gleichung in Pixel konvertiert werden:</span><span class="sxs-lookup"><span data-stu-id="410b2-110">Physical units can be converted to pixels by using the following equation:</span></span>

<span data-ttu-id="410b2-111">Pixel = Pixeldichte × Maße</span><span class="sxs-lookup"><span data-stu-id="410b2-111">Pixels = Pixel Density × Measurement</span></span>

<span data-ttu-id="410b2-112">Die folgenden Beispiele verwenden diese Formel, um eine Zielgröße von 9mm auf einem Display mit 135PPI (Pixel Per Inch, Pixel pro Zoll) und einem einfachen Skalierungsplateau in die Pixelgröße umrechnen:</span><span class="sxs-lookup"><span data-stu-id="410b2-112">The following example uses this formula to calculate the pixel size of a 9 mm target on a 135 pixel per inch (PPI) display at a 1x scaling plateau:</span></span>

<span data-ttu-id="410b2-113">Pixel = 135 PPI × 9 mm</span><span class="sxs-lookup"><span data-stu-id="410b2-113">Pixels = 135 PPI × 9 mm</span></span>

<span data-ttu-id="410b2-114">Pixel = 135PPI×(0,03937Zoll pro mm×9mm)</span><span class="sxs-lookup"><span data-stu-id="410b2-114">Pixels = 135 PPI × (0.03937 inches per mm × 9 mm)</span></span>

<span data-ttu-id="410b2-115">Pixel = 135PPI×0,35433Zoll</span><span class="sxs-lookup"><span data-stu-id="410b2-115">Pixels = 135 PPI × 0.35433 inches</span></span>

<span data-ttu-id="410b2-116">Pixel = 48 Pixel</span><span class="sxs-lookup"><span data-stu-id="410b2-116">Pixels = 48 pixels</span></span>

<span data-ttu-id="410b2-117">Dieses Ergebnis muss an jedes der im System definierten Skalierungsplateaus angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="410b2-117">This result must be adjusted according to each scaling plateau defined by the system.</span></span>

## <a name="thresholds"></a><span data-ttu-id="410b2-118">Schwellenwerte</span><span class="sxs-lookup"><span data-stu-id="410b2-118">Thresholds</span></span>


<span data-ttu-id="410b2-119">Entfernungs- und Zeitschwellenwerte können verwendet werden, um das Ergebnis einer Interaktion zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="410b2-119">Distance and time thresholds may be used to determine the outcome of an interaction.</span></span>

<span data-ttu-id="410b2-120">Wenn zum Beispiel ein Aufsetzen erkannt wird, wird ein Tippen registriert, wenn das Objekt in weniger als 2,7 mm Entfernung vom Aufsetzpunkt gezogen wird und die Berührung innerhalb von 0,1 Sekunden oder kürzer vom Aufsetzen aufgehoben wird.</span><span class="sxs-lookup"><span data-stu-id="410b2-120">For example, when a touch-down is detected, a tap is registered if the object is dragged less than 2.7 mm from the touch-down point and the touch is lifted within 0.1 second or less of the touch-down.</span></span> <span data-ttu-id="410b2-121">Wenn der Finger über den Schwellenwert von 2,7 mm hinaus bewegt wird, wird das Objekt gezogen und entweder ausgewählt oder verschoben (weitere Informationen finden Sie unter [Richtlinien für Querziehen](guidelines-for-cross-slide.md)).</span><span class="sxs-lookup"><span data-stu-id="410b2-121">Moving the finger beyond this 2.7 mm threshold results in the object being dragged and either selected or moved (for more information, see [Guidelines for cross-slide](guidelines-for-cross-slide.md)).</span></span> <span data-ttu-id="410b2-122">Wenn Sie abhängig von Ihrer App den Finger länger als 0,1 Sekunde gedrückt halten, kann dadurch die Ausführung einer Interaktion mit automatischem Einblenden durch das System ausgelöst werden (weitere Informationen finden Sie unter [Richtlinien für visuelles Feedback](guidelines-for-visualfeedback.md)).</span><span class="sxs-lookup"><span data-stu-id="410b2-122">Depending on your app, holding the finger down for longer than 0.1 second may cause the system to perform a self-revealing interaction (for more information, see [Guidelines for visual feedback](guidelines-for-visualfeedback.md)).</span></span>

## <a name="target-sizes"></a><span data-ttu-id="410b2-123">Zielgrößen</span><span class="sxs-lookup"><span data-stu-id="410b2-123">Target sizes</span></span>


<span data-ttu-id="410b2-124">Verwenden Sie für Ihr Touchziel grundsätzlich mindestens eine Fläche von 9x9mm (48x48-Pixel auf einem 135PPI-Display bei einem Skalierungsplateau von1,0).</span><span class="sxs-lookup"><span data-stu-id="410b2-124">In general, set your touch target size to 9 mm square or greater (48x48 pixels on a 135 PPI display at a 1.0x scaling plateau).</span></span> <span data-ttu-id="410b2-125">Verwenden Sie keine Touchziele mit weniger als 7x7mm.</span><span class="sxs-lookup"><span data-stu-id="410b2-125">Avoid using touch targets that are less than 7 mm square.</span></span>

<span data-ttu-id="410b2-126">Im folgenden Diagramm wird gezeigt, dass die Größe eines Ziels in der Regel eine Kombination aus visuellem Ziel, tatsächlicher Zielgröße und dem Abstand zwischen dem tatsächlichen Ziel und den anderen potenziellen Zielen ist.</span><span class="sxs-lookup"><span data-stu-id="410b2-126">The following diagram shows how target size is typically a combination of a visual target, actual target size, and any padding between the actual target and other potential targets.</span></span>

![Diagramm mit den empfohlenen Größen für visuelles Ziel, tatsächliches Ziel und Abstand](images/targeting-size.png)

<span data-ttu-id="410b2-128">Die folgende Tabelle enthält die Mindestgrößen und die empfohlenen Größen für die Komponenten eines Touchziels:</span><span class="sxs-lookup"><span data-stu-id="410b2-128">The following table lists the minimum and recommended sizes for the components of a touch target.</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="410b2-129">Zielkomponente</span><span class="sxs-lookup"><span data-stu-id="410b2-129">Target component</span></span></th>
<th align="left"><span data-ttu-id="410b2-130">Mindestgröße</span><span class="sxs-lookup"><span data-stu-id="410b2-130">Minimum size</span></span></th>
<th align="left"><span data-ttu-id="410b2-131">Empfohlene Größe</span><span class="sxs-lookup"><span data-stu-id="410b2-131">Recommended size</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="410b2-132">Abstand</span><span class="sxs-lookup"><span data-stu-id="410b2-132">Padding</span></span></td>
<td align="left"><span data-ttu-id="410b2-133">2mm</span><span class="sxs-lookup"><span data-stu-id="410b2-133">2 mm</span></span></td>
<td align="left"><span data-ttu-id="410b2-134">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="410b2-134">Not applicable.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="410b2-135">Visuelle Zielgröße</span><span class="sxs-lookup"><span data-stu-id="410b2-135">Visual target size</span></span></td>
<td align="left"><span data-ttu-id="410b2-136">&lt;60% der tatsächlichen Größe</span><span class="sxs-lookup"><span data-stu-id="410b2-136">&lt; 60% of actual size</span></span></td>
<td align="left"><span data-ttu-id="410b2-137">90 – 100% der tatsächlichen Größe</span><span class="sxs-lookup"><span data-stu-id="410b2-137">90-100% of actual size</span></span>
<p><span data-ttu-id="410b2-138">Visuelle Ziele mit weniger als 4,2x 4,2mm (60% der empfohlenen Mindestgröße von 7x7mm) werden von den meisten Benutzern nicht als toucheingabefähiges Element erkannt.</span><span class="sxs-lookup"><span data-stu-id="410b2-138">Most users won't realize a visual target is touchable if it's less than 4.2 mm square (60% of the recommended minimum target size of 7 mm).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="410b2-139">Tatsächliche Zielgröße</span><span class="sxs-lookup"><span data-stu-id="410b2-139">Actual target size</span></span></td>
<td align="left"><span data-ttu-id="410b2-140">7x7mm</span><span class="sxs-lookup"><span data-stu-id="410b2-140">7 mm square</span></span></td>
<td align="left"><span data-ttu-id="410b2-141">Mindestens 9x0mm (48x48Pixel @ 1x)</span><span class="sxs-lookup"><span data-stu-id="410b2-141">Greater than or equal to 9 mm square (48 x 48 px @ 1x)</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="410b2-142">Gesamtzielgröße</span><span class="sxs-lookup"><span data-stu-id="410b2-142">Total target size</span></span></td>
<td align="left"><span data-ttu-id="410b2-143">11 x 11 mm (ca. 60px: drei 20-px-Rastereinheiten @1x)</span><span class="sxs-lookup"><span data-stu-id="410b2-143">11 x 11 mm (approximately 60 px: three 20-px grid units @ 1x)</span></span></td>
<td align="left"><span data-ttu-id="410b2-144">13,5 x 13,5 mm (72 x 72 px @ 1x)</span><span class="sxs-lookup"><span data-stu-id="410b2-144">13.5 x 13.5 mm (72 x 72 px @ 1x)</span></span>
<p><span data-ttu-id="410b2-145">Dies impliziert, dass die Größe des tatsächlichen Ziels und des Abstands zusammen größer sein muss als die jeweiligen Mindestgrößen.</span><span class="sxs-lookup"><span data-stu-id="410b2-145">This implies that the size of the actual target and padding combined should be larger than their respective minimums.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="410b2-146">Sie können diese Empfehlungen für die Zielgröße an die Anforderungen des jeweiligen Szenarios anpassen.</span><span class="sxs-lookup"><span data-stu-id="410b2-146">These target size recommendations can be adjusted as required by your particular scenario.</span></span> <span data-ttu-id="410b2-147">In die Empfehlungen sind unter anderem die folgenden Überlegungen eingeflossen:</span><span class="sxs-lookup"><span data-stu-id="410b2-147">Some of the considerations that went into these recommendations include:</span></span>

-   <span data-ttu-id="410b2-148">Häufigkeit der Fingereingaben: Erwägen Sie, Ziele, die wiederholt bzw. häufig berührt werden, größer als die Mindestgröße auszulegen.</span><span class="sxs-lookup"><span data-stu-id="410b2-148">Frequency of Touches: Consider making targets that are repeatedly or frequently pressed larger than the minimum size.</span></span>
-   <span data-ttu-id="410b2-149">Folgen von Fehlern: Ziele, bei denen die versehentliche Berührung schwerwiegende Folgen hat, sollten einen größeren Abstand haben und weiter vom Rand des Inhaltsbereichs entfernt platziert werden.</span><span class="sxs-lookup"><span data-stu-id="410b2-149">Error Consequence: Targets that have severe consequences if touched in error should have greater padding and be placed further from the edge of the content area.</span></span> <span data-ttu-id="410b2-150">Dies gilt insbesondere für Ziele, die häufig berührt werden.</span><span class="sxs-lookup"><span data-stu-id="410b2-150">This is especially true for targets that are touched frequently.</span></span>
-   <span data-ttu-id="410b2-151">Position im Inhaltsbereich</span><span class="sxs-lookup"><span data-stu-id="410b2-151">Position in the content area</span></span>
-   <span data-ttu-id="410b2-152">Formfaktor und Bildschirmgröße</span><span class="sxs-lookup"><span data-stu-id="410b2-152">Form factor and screen size</span></span>
-   <span data-ttu-id="410b2-153">Fingerhaltung</span><span class="sxs-lookup"><span data-stu-id="410b2-153">Finger posture</span></span>
-   <span data-ttu-id="410b2-154">Fingereingabevisualisierungen</span><span class="sxs-lookup"><span data-stu-id="410b2-154">Touch visualizations</span></span>
-   <span data-ttu-id="410b2-155">Hardware und Fingereingabe-Digitalisierungsgeräte</span><span class="sxs-lookup"><span data-stu-id="410b2-155">Hardware and touch digitizers</span></span>

## <a name="targeting-assistance"></a><span data-ttu-id="410b2-156">Unterstützung bei der Zielbestimmung</span><span class="sxs-lookup"><span data-stu-id="410b2-156">Targeting assistance</span></span>


<span data-ttu-id="410b2-157">Windows unterstützt die Zielbestimmung für Szenarien, in denen die hier genannten Empfehlungen für Mindestgröße und Abstand nicht anwendbar sind. Dies gilt beispielsweise für Hyperlinks auf einer Webseite, Kalendersteuerelemente, Dropdownlisten und Kombinationsfelder oder für eine Textauswahl.</span><span class="sxs-lookup"><span data-stu-id="410b2-157">Windows provides targeting assistance to support scenarios where the minimum size or padding recommendations presented here are not applicable; for example, hyperlinks on a webpage, calendar controls, drop down lists and combo boxes, or text selection.</span></span>

<span data-ttu-id="410b2-158">Diese Verbesserungen der Zielbestimmungsplattform und des Verhaltens der Benutzeroberfläche bewirken in Kombination mit visuellem Feedback (Mehrdeutigkeitsvermeidungs-UI) mehr Genauigkeit und Sicherheit für die Benutzer.</span><span class="sxs-lookup"><span data-stu-id="410b2-158">These targeting platform improvements and user interface behaviors work together with visual feedback (disambiguation UI) to improve user accuracy and confidence.</span></span> <span data-ttu-id="410b2-159">Weitere Informationen finden Sie unter [Richtlinien für visuelles Feedback](guidelines-for-visualfeedback.md).</span><span class="sxs-lookup"><span data-stu-id="410b2-159">For more information, see [Guidelines for visual feedback](guidelines-for-visualfeedback.md).</span></span>

<span data-ttu-id="410b2-160">Wenn ein berührbares Element kleiner als die empfohlene Mindestzielgröße sein muss, können Sie mit den folgenden Techniken die dadurch entstehenden Probleme bei der Zielbestimmung minimieren.</span><span class="sxs-lookup"><span data-stu-id="410b2-160">If a touchable element must be smaller than the recommended minimum target size, the following techniques can be used to minimize the targeting issues that result.</span></span>

## <a name="tethering"></a><span data-ttu-id="410b2-161">Anzeigen einer Verbindungslinie</span><span class="sxs-lookup"><span data-stu-id="410b2-161">Tethering</span></span>


<span data-ttu-id="410b2-162">Durch Anzeigen einer Verbindungslinie (zwischen einem Kontaktpunkt und dem Begrenzungsrechteck eines Objekts) können Sie Benutzer visuell darauf hinweisen, dass sie mit einem Objekt verbunden sind und mit diesem interagieren, obwohl kein direkter Kontakt zwischen Eingabekontakt und Objekt besteht.</span><span class="sxs-lookup"><span data-stu-id="410b2-162">Tethering is a visual cue (a connector from a contact point to the bounding rectangle of an object) used to indicate to a user that they are connected to, and interacting with, an object even though the input contact isn't directly in contact with the object.</span></span> <span data-ttu-id="410b2-163">Dies ist in folgenden Situationen möglich:</span><span class="sxs-lookup"><span data-stu-id="410b2-163">This can occur when:</span></span>

-   <span data-ttu-id="410b2-164">Ein Berührungskontakt wurde zuerst innerhalb eines Näherungsschwellenwerts für ein Objekt erkannt, und das Objekt wurde als wahrscheinlichstes Ziel des Kontakts identifiziert.</span><span class="sxs-lookup"><span data-stu-id="410b2-164">A touch contact was first detected within some proximity threshold to an object and this object was identified as the most likely target of the contact.</span></span>
-   <span data-ttu-id="410b2-165">Ein Berührungskontakt wurde von einem Objekt wegbewegt, aber der Kontakt befindet sich noch innerhalb eines Näherungsschwellenwerts.</span><span class="sxs-lookup"><span data-stu-id="410b2-165">A touch contact was moved off an object but the contact is still within a proximity threshold.</span></span>

<span data-ttu-id="410b2-166">Dieses Feature wird für Entwickler von UWP-Apps, die JavaScript verwenden, nicht zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="410b2-166">This feature is not exposed to UWP app using JavaScript developers.</span></span>

## <a name="scrubbing"></a><span data-ttu-id="410b2-167">Scrubbing (Bereinigung)</span><span class="sxs-lookup"><span data-stu-id="410b2-167">Scrubbing</span></span>


<span data-ttu-id="410b2-168">Beim Scrubbing wird eine beliebige Stelle in einem Feld mit Zielen berührt, und das gewünschte Ziel wird durch Ziehen ausgewählt. Der Finger wird dabei erst gehoben, wenn er sich auf dem gewünschten Ziel befindet.</span><span class="sxs-lookup"><span data-stu-id="410b2-168">Scrubbing means to touch anywhere within a field of targets and slide to select the desired target without lifting the finger until it is over the desired target.</span></span> <span data-ttu-id="410b2-169">Dies wird auch als "Loslassaktivierung" bezeichnet, bei der das Objekt aktiviert wird, das zuletzt berührt wurde, als der Finger vom Bildschirm gehoben wurde.</span><span class="sxs-lookup"><span data-stu-id="410b2-169">This is also referred to as "take-off activation", where the object that is activated is the one that was last touched when the finger was lifted from the screen.</span></span>

<span data-ttu-id="410b2-170">Halten Sie sich an die folgenden Richtlinien, wenn Sie Scrubbinginteraktionen entwerfen:</span><span class="sxs-lookup"><span data-stu-id="410b2-170">Use the following guidelines when you design scrubbing interactions:</span></span>

-   <span data-ttu-id="410b2-171">Scrubbing wird in Verbindung mit der Mehrdeutigkeitsvermeidungs-UI verwendet.</span><span class="sxs-lookup"><span data-stu-id="410b2-171">Scrubbing is used in conjunction with disambiguation UI.</span></span> <span data-ttu-id="410b2-172">Weitere Informationen finden Sie unter [Richtlinien für visuelles Feedback](guidelines-for-visualfeedback.md).</span><span class="sxs-lookup"><span data-stu-id="410b2-172">For more information, see [Guidelines for visual feedback](guidelines-for-visualfeedback.md).</span></span>
-   <span data-ttu-id="410b2-173">Die empfohlene Mindestgröße für ein Scrubbing-Fingereingabeziel beträgt 20px (3,75mm @1xGröße).</span><span class="sxs-lookup"><span data-stu-id="410b2-173">The recommended minimum size for a scrubbing touch target is 20 px (3.75 mm @ 1x size).</span></span>
-   <span data-ttu-id="410b2-174">Scrubbing hat Vorrang, wenn es auf einer Oberfläche ausgeführt wird, die Verschieben unterstützt (beispielsweise eine Webseite).</span><span class="sxs-lookup"><span data-stu-id="410b2-174">Scrubbing takes precedence when performed on a pannable surface, such as a webpage.</span></span>
-   <span data-ttu-id="410b2-175">Scrubbingziele sollten nah beieinander liegen.</span><span class="sxs-lookup"><span data-stu-id="410b2-175">Scrubbing targets should be close together.</span></span>
-   <span data-ttu-id="410b2-176">Eine Aktion wird abgebrochen, wenn Benutzer einen Finger vom Scrubbingziel wegziehen.</span><span class="sxs-lookup"><span data-stu-id="410b2-176">An action is canceled when the user drags a finger off a scrubbing target.</span></span>
-   <span data-ttu-id="410b2-177">Das Anzeigen einer Verbindungslinie zu einem Scrubbingziel wird angegeben, wenn die vom Ziel ausgeführten Aktionen nicht destruktiv sind (beispielsweise das Wechseln zwischen Daten in einem Kalender).</span><span class="sxs-lookup"><span data-stu-id="410b2-177">Tethering to a scrubbing target is specified if the actions performed by the target are non-destructive, such as switching between dates on a calendar.</span></span>
-   <span data-ttu-id="410b2-178">Das Anzeigen von Verbindungslinien wird in einer einzigen Richtung angegeben: horizontal oder vertikal.</span><span class="sxs-lookup"><span data-stu-id="410b2-178">Tethering is specified in a single direction, horizontally or vertically.</span></span>

## <a name="related-articles"></a><span data-ttu-id="410b2-179">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="410b2-179">Related articles</span></span>


**<span data-ttu-id="410b2-180">Beispiele</span><span class="sxs-lookup"><span data-stu-id="410b2-180">Samples</span></span>**
* [<span data-ttu-id="410b2-181">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="410b2-181">Basic input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="410b2-182">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="410b2-182">Low latency input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="410b2-183">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="410b2-183">User interaction mode sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="410b2-184">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="410b2-184">Focus visuals sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="410b2-185">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="410b2-185">Archive samples</span></span>**
* [<span data-ttu-id="410b2-186">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="410b2-186">Input: XAML user input events sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="410b2-187">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="410b2-187">Input: Device capabilities sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="410b2-188">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="410b2-188">Input: Touch hit testing sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="410b2-189">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="410b2-189">XAML scrolling, panning, and zooming sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="410b2-190">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="410b2-190">Input: Simplified ink sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="410b2-191">Eingabe: Beispiel für Windows8-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="410b2-191">Input: Windows 8 gestures sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="410b2-192">Eingabe: Beispiel für Manipulationen und Gesten (C++)</span><span class="sxs-lookup"><span data-stu-id="410b2-192">Input: Manipulations and gestures (C++) sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="410b2-193">Beispiel für die DirectX-Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="410b2-193">DirectX touch input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 




