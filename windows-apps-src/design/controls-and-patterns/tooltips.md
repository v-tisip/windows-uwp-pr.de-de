---
author: Jwmsft
Description: Use a tooltip to reveal more info about a control before asking the user to perform an action.
title: QuickInfos
ms.assetid: A21BB12B-301E-40C9-B84B-C055FD43D307
label: Tooltips
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: stpete
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: b60b06d9dbe8c0eb6216c2c909cc5184855056d5
ms.sourcegitcommit: 4b522af988273946414a04fbbd1d7fde40f8ba5e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2018
ms.locfileid: "1493607"
---
# <a name="tooltips"></a><span data-ttu-id="a31b8-103">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="a31b8-103">Tooltips</span></span>
 

<span data-ttu-id="a31b8-104">Eine QuickInfo ist eine kurze Beschreibung, die mit einem anderen Steuerelement oder Objekt verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="a31b8-104">A tooltip is a short description that is linked to another control or object.</span></span> <span data-ttu-id="a31b8-105">QuickInfos erläutern Benutzern unbekannte Objekte, die in der Benutzeroberfläche nicht direkt beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="a31b8-105">Tooltips help users understand unfamiliar objects that aren't described directly in the UI.</span></span> <span data-ttu-id="a31b8-106">Sie wird automatisch angezeigt, wenn der Benutzer den Fokus auf ein Steuerelement verschiebt, es gedrückt hält oder mit dem Mauszeiger darauf zeigt.</span><span class="sxs-lookup"><span data-stu-id="a31b8-106">They display automatically when the user moves focus to, presses and holds, or hovers the mouse pointer over a control.</span></span> <span data-ttu-id="a31b8-107">Sie wird nach einigen Sekunden wieder ausgeblendet, wenn der Benutzer den Finger, den Mauszeiger oder den Tastatur-/Gamepad-Fokus bewegt.</span><span class="sxs-lookup"><span data-stu-id="a31b8-107">The tooltip disappears after a few seconds, or when the user moves the finger, pointer or keyboard/gamepad focus.</span></span>

![Eine QuickInfo](images/controls/tool-tip.png)

> <span data-ttu-id="a31b8-109">**Wichtige APIs**: [ToolTip-Klasse](https://msdn.microsoft.com/library/windows/apps/br227608), [ToolTipService-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.tooltipservice)</span><span class="sxs-lookup"><span data-stu-id="a31b8-109">**Important APIs**: [ToolTip class](https://msdn.microsoft.com/library/windows/apps/br227608), [ToolTipService class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.tooltipservice)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="a31b8-110">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="a31b8-110">Is this the right control?</span></span>

<span data-ttu-id="a31b8-111">Verwenden Sie eine QuickInfo, damit der Benutzer weitere Informationen über ein Steuerelement erhält, bevor er zum Ausführen einer Aktion aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="a31b8-111">Use a tooltip to reveal more info about a control before asking the user to perform an action.</span></span> <span data-ttu-id="a31b8-112">QuickInfo-Steuerelemente sollten sparsam verwendet werden, vor allem nur dann, wenn sie für Benutzer, die eine bestimmte Aufgabe ausführen möchten, wirklich nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="a31b8-112">Tooltips should be used sparingly, and only when they are adding distinct value for the user who is trying to complete a task.</span></span> <span data-ttu-id="a31b8-113">Es gilt folgende Faustregel: Für Informationen, die bereits an einer anderen Stelle derselben Benutzeroberfläche vermittelt werden, benötigen Sie keine QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="a31b8-113">One rule of thumb is that if the information is available elsewhere in the same experience, you do not need a tooltip.</span></span> <span data-ttu-id="a31b8-114">Eine nützliche QuickInfo bietet klärende Informationen zu einer unklaren Aktion.</span><span class="sxs-lookup"><span data-stu-id="a31b8-114">A valuable tooltip will clarify an unclear action.</span></span>

<span data-ttu-id="a31b8-115">Wann sollten Sie eine QuickInfo verwenden?</span><span class="sxs-lookup"><span data-stu-id="a31b8-115">When should you use a tooltip?</span></span> <span data-ttu-id="a31b8-116">Orientieren Sie sich an folgenden Fragen:</span><span class="sxs-lookup"><span data-stu-id="a31b8-116">To decide, consider these questions:</span></span>

-   **<span data-ttu-id="a31b8-117">Sollen die Informationen beim Daraufzeigen sichtbar werden?</span><span class="sxs-lookup"><span data-stu-id="a31b8-117">Should info become visible based on pointer hover?</span></span>**
    <span data-ttu-id="a31b8-118">Wenn dies nicht erwünscht ist, verwenden Sie ein anderes Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="a31b8-118">If not, use another control.</span></span> <span data-ttu-id="a31b8-119">QuickInfos sollte niemals ohne vorhergehende Aktion angezeigt werden, sondern immer als Ergebnis einer Benutzerinteraktion.</span><span class="sxs-lookup"><span data-stu-id="a31b8-119">Display tips only as the result of user interaction, never display them on their own.</span></span>

-   **<span data-ttu-id="a31b8-120">Ist das Steuerelement mit Text beschriftet?</span><span class="sxs-lookup"><span data-stu-id="a31b8-120">Does a control have a text label?</span></span>**
    <span data-ttu-id="a31b8-121">Wenn dies nicht der Fall ist, fügen Sie die Beschriftung als QuickInfo hinzu.</span><span class="sxs-lookup"><span data-stu-id="a31b8-121">If not, use a tooltip to provide the label.</span></span> <span data-ttu-id="a31b8-122">Beim UX-Entwurf empfiehlt es sich, die meisten Steuerelemente inline zu beschriften, sodass QuickInfos dafür nicht erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a31b8-122">It is a good UX design practice to label most controls inline and for these you don't need tooltips.</span></span> <span data-ttu-id="a31b8-123">Steuerelemente in Symbolleisten sowie nur Symbole zeignde Befehlsschaltflächen müssen dagegen mit QuickInfos versehen werden.</span><span class="sxs-lookup"><span data-stu-id="a31b8-123">Toolbar controls and command buttons showing only icons need tooltips.</span></span>

-   **<span data-ttu-id="a31b8-124">Wären eine Beschreibung oder zusätzliche Informationen zu einem Objekt hilfreich?</span><span class="sxs-lookup"><span data-stu-id="a31b8-124">Does an object benefit from a description or further info?</span></span>**
    <span data-ttu-id="a31b8-125">Verwenden Sie in diesem Fall eine QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="a31b8-125">If so, use a tooltip.</span></span> <span data-ttu-id="a31b8-126">Der Text ist aber nur als Ergänzung gedacht – wichtige Informationen für die Hauptaufgaben dürfen nicht nur als QuickInfo vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="a31b8-126">But the text must be supplemental — that is, not essential to the primary tasks.</span></span> <span data-ttu-id="a31b8-127">Fügen Sie wichtige Informationen direkt in die Benutzeroberfläche ein, damit Benutzer nicht erst danach suchen müssen.</span><span class="sxs-lookup"><span data-stu-id="a31b8-127">If it is essential, put it directly in the UI so that users don't have to discover or hunt for it.</span></span>

-   **<span data-ttu-id="a31b8-128">Handelt es sich bei den ergänzenden Informationen um Fehler-, Warn- oder Statusmeldungen?</span><span class="sxs-lookup"><span data-stu-id="a31b8-128">Is the supplemental info an error, warning, or status?</span></span>**
    <span data-ttu-id="a31b8-129">Verwenden Sie in diesem Fall ein anderes Benutzeroberflächenelement, beispielsweise ein Flyout.</span><span class="sxs-lookup"><span data-stu-id="a31b8-129">If so, use another UI element, such as a flyout.</span></span>

-   **<span data-ttu-id="a31b8-130">Müssen die Benutzer mit den Informationen interagieren?</span><span class="sxs-lookup"><span data-stu-id="a31b8-130">Do users need to interact with the tip?</span></span>**
    <span data-ttu-id="a31b8-131">Verwenden Sie in diesem Fall ein anderes Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="a31b8-131">If so, use another control.</span></span> <span data-ttu-id="a31b8-132">Eine Benutzerinteraktion mit QuickInfo ist nicht möglich, da die Informationen beim Bewegen der Maus ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="a31b8-132">Users can't interact with tips because moving the mouse makes them disappear.</span></span>

-   **<span data-ttu-id="a31b8-133">Müssen die Benutzer die ergänzenden Informationen drucken?</span><span class="sxs-lookup"><span data-stu-id="a31b8-133">Do users need to print the supplemental info?</span></span>**
    <span data-ttu-id="a31b8-134">Verwenden Sie in diesem Fall ein anderes Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="a31b8-134">If so, use another control.</span></span>

-   **<span data-ttu-id="a31b8-135">Ist anzunehmen, dass sich die Benutzer durch QuickInfo gestört oder abgelenkt fühlen?</span><span class="sxs-lookup"><span data-stu-id="a31b8-135">Will users find the tips annoying or distracting?</span></span>**
    <span data-ttu-id="a31b8-136">Ziehen Sie in diesem Fall eine andere Lösung in Betracht. Möglicherweise können Sie ganz auf die zusätzlichen Informationen verzichten.</span><span class="sxs-lookup"><span data-stu-id="a31b8-136">If so, consider using another solution — including doing nothing at all.</span></span> <span data-ttu-id="a31b8-137">Wenn Sie QuickInfos verwenden, obwohl dies die Benutzer möglicherweise irritiert, geben Sie den Benutzern die Möglichkeit, die QuickInfos zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="a31b8-137">If you do use tips where they might be distracting, allow users to turn them off.</span></span>

## <a name="example"></a><span data-ttu-id="a31b8-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a31b8-138">Example</span></span>

<table>
<th align="left"><span data-ttu-id="a31b8-139">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="a31b8-139">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="a31b8-140">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/ToolTip">die App zu öffnen und ToolTip in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="a31b8-140">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/ToolTip">open the app and see the ToolTip in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="a31b8-141">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="a31b8-141">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="a31b8-142">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a31b8-142">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="a31b8-143">Eine QuickInfo in der Bing-Karten-App.</span><span class="sxs-lookup"><span data-stu-id="a31b8-143">A tooltip in the Bing Maps app.</span></span>

![Eine QuickInfo in der Bing-Karten-App](images/control-examples/tool-tip-maps.png)

## <a name="recommendations"></a><span data-ttu-id="a31b8-145">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="a31b8-145">Recommendations</span></span>

- <span data-ttu-id="a31b8-146">Verwenden Sie QuickInfos sparsam (oder gar nicht).</span><span class="sxs-lookup"><span data-stu-id="a31b8-146">Use tooltips sparingly (or not at all).</span></span> <span data-ttu-id="a31b8-147">QuickInfos stellen eine Unterbrechung dar.</span><span class="sxs-lookup"><span data-stu-id="a31b8-147">Tooltips are an interruption.</span></span> <span data-ttu-id="a31b8-148">Eine QuickInfo kann genauso ablenkend wirken wie ein Popup. Verwenden Sie sie daher nur, wenn sie wirklich von Bedeutung sind.</span><span class="sxs-lookup"><span data-stu-id="a31b8-148">A tooltip can be as distracting as a pop-up, so don't use them unless they add significant value.</span></span>
- <span data-ttu-id="a31b8-149">Halten Sie den QuickInfo-Text kurz.</span><span class="sxs-lookup"><span data-stu-id="a31b8-149">Keep the tooltip text concise.</span></span> <span data-ttu-id="a31b8-150">QuickInfos eignen sich gut für kurze Sätze und Satzfragmente.</span><span class="sxs-lookup"><span data-stu-id="a31b8-150">Tooltips are perfect for short sentences and sentence fragments.</span></span> <span data-ttu-id="a31b8-151">Längere Textblöcke können überfrachtet wirken, sodass ein Timeout für die QuickInfo auftritt, bevor der Benutzer sie zu Ende gelesen hat.</span><span class="sxs-lookup"><span data-stu-id="a31b8-151">Large blocks of text can be overwhelming and the tooltip may time out before the user has finished reading.</span></span>
- <span data-ttu-id="a31b8-152">Erstellen Sie hilfreiche QuickInfo-Texte mit ergänzenden Informationen.</span><span class="sxs-lookup"><span data-stu-id="a31b8-152">Create helpful, supplemental tooltip text.</span></span> <span data-ttu-id="a31b8-153">Der QuickInfo-Text muss informativ sein.</span><span class="sxs-lookup"><span data-stu-id="a31b8-153">Tooltip text must be informative.</span></span> <span data-ttu-id="a31b8-154">Verwenden Sie keine selbstverständlichen oder bereits auf dem Bildschirm vorhandenen Informationen als QuickInfo-Text.</span><span class="sxs-lookup"><span data-stu-id="a31b8-154">Don't make it obvious or just repeat what is already on the screen.</span></span> <span data-ttu-id="a31b8-155">Da der QuickInfo-Text nicht immer angezeigt wird, sollte er nur ergänzende Informationen enthalten, die nicht unbedingt gelesen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="a31b8-155">Because tooltip text isn't always visible, it should be supplemental info that users don't have to read.</span></span> <span data-ttu-id="a31b8-156">Teilen Sie wichtige Informationen in Form von selbsterklärenden Beschriftungen für Steuerelemente oder direkt eingefügtem ergänzendem Text mit.</span><span class="sxs-lookup"><span data-stu-id="a31b8-156">Communicate important info using self-explanatory control labels or in-place supplemental text.</span></span>
- <span data-ttu-id="a31b8-157">Verwenden Sie ggf. Bilder als QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="a31b8-157">Use images when appropriate.</span></span> <span data-ttu-id="a31b8-158">Manchmal ist ein Bild aussagekräftiger als Text.</span><span class="sxs-lookup"><span data-stu-id="a31b8-158">Sometimes it's better to use an image in a tooltip.</span></span> <span data-ttu-id="a31b8-159">Wenn der Benutzer z.B. auf einen Hyperlink zeigt, können Sie als QuickInfo eine Vorschau der verknüpften Seite anzeigen.</span><span class="sxs-lookup"><span data-stu-id="a31b8-159">For example, when the user hovers over a hyperlink, you can use a tooltip to show a preview of the linked page.</span></span>
- <span data-ttu-id="a31b8-160">Verwenden Sie die QuickInfo nicht, um bereits in der UI vorhandene Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a31b8-160">Don't use a tooltip to display text already visible in the UI.</span></span> <span data-ttu-id="a31b8-161">Versehen Sie z.B. keine Schaltfläche mit QuickInfo-Text, der bereits auf der Schaltfläche selbst angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a31b8-161">For example, don't put a tooltip on a button that shows the same text of the button.</span></span>
- <span data-ttu-id="a31b8-162">Fügen Sie in QuickInfos keine interaktiven Steuerelemente ein.</span><span class="sxs-lookup"><span data-stu-id="a31b8-162">Don't put interactive controls inside the tooltip.</span></span>
- <span data-ttu-id="a31b8-163">Fügen Sie in QuickInfos keine Bilder ein, die wie interaktive Steuerelemente aussehen.</span><span class="sxs-lookup"><span data-stu-id="a31b8-163">Don't put images that look like they are interactive inside the tooltip.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="a31b8-164">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="a31b8-164">Get the sample code</span></span>

- <span data-ttu-id="a31b8-165">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a31b8-165">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="a31b8-166">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="a31b8-166">Related articles</span></span>

- [<span data-ttu-id="a31b8-167">QuickInfo-Klasse</span><span class="sxs-lookup"><span data-stu-id="a31b8-167">ToolTip class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227608)
