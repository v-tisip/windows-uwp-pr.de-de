---
author: QuinnRadich
Description: A progress control provides feedback to the user that a long-running operation is underway.
title: Richtlinien für Statussteuerelemente
ms.assetid: FD53B716-C43D-408D-8B07-522BC1F3DF9D
label: Progress controls
template: detail.hbs
ms.author: quradic
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: kisai
design-contact: jeffarn
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: d92005dca87d1be0cf9fddd0a28402497ab56595
ms.sourcegitcommit: 5dda01da4702cbc49c799c750efe0e430b699502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4114468"
---
# <a name="progress-controls"></a><span data-ttu-id="c1e6e-103">Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="c1e6e-103">Progress controls</span></span>

 

<span data-ttu-id="c1e6e-104">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-104">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="c1e6e-105">Dies kann bedeuten, dass der Benutzer bei Anzeigen der Statusanzeige nicht mit der App interagieren kann. Je nach verwendetem Indikator wird auch die Länge der Wartezeit angegeben.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-105">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

> <span data-ttu-id="c1e6e-106">**Wichtige APIs**: [ProgressBar-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.aspx), [IsIndeterminate Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.isindeterminate.aspx), [ProgressRing-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.aspx), [IsActive-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.isactive.aspx)</span><span class="sxs-lookup"><span data-stu-id="c1e6e-106">**Important APIs**: [ProgressBar class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.aspx), [IsIndeterminate property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.isindeterminate.aspx), [ProgressRing class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.aspx), [IsActive property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.isactive.aspx)</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="c1e6e-107">Typen von Statussteuerelementen</span><span class="sxs-lookup"><span data-stu-id="c1e6e-107">Types of progress</span></span>

<span data-ttu-id="c1e6e-108">Es gibt zwei Steuerelemente, die dem Benutzer anzeigen, dass ein Vorgang ausgeführt wird: ein ProgressBar-Element oder ein ProgressRing-Element.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-108">There are two controls to show the user that an operation is underway – either through a ProgressBar or through a ProgressRing.</span></span>

-   <span data-ttu-id="c1e6e-109">Der ProgressBar-Status *bestimmt* gibt den Prozentsatz an, zu dem eine Aufgabe abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-109">The ProgressBar *determinate* state shows the percentage completed of a task.</span></span> <span data-ttu-id="c1e6e-110">Dieses Element für Vorgänge verwendet werden, deren Dauer bekannt ist, deren Fortschritt jedoch nicht die Interaktion des Benutzers mit der App blockieren sollte.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-110">This should be used during an operation whose duration is known, but it's progress should not block the user's interaction with the app.</span></span>
-   <span data-ttu-id="c1e6e-111">Der ProgressBar-Status *unbestimmt* gibt an, dass ein Vorgang ausgeführt wird, der die Interaktion des Benutzers mit der App nicht blockiert und dessen Abschlusszeit nicht bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-111">The ProgressBar *indeterminate* state shows that an operation is underway, does not block user interaction with the app, and its completion time is unknown.</span></span>
-   <span data-ttu-id="c1e6e-112">Für das ProgressRing-Element gibt es nur den Status *unbestimmt*. Es sollte verwendet werden, wenn vor dem Abschluss eines Vorgangs keine Benutzerinteraktion möglich ist.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-112">The ProgressRing only has an *indeterminate* state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

<span data-ttu-id="c1e6e-113">Ein Statussteuerelement ist zudem schreibgeschützt und nicht interaktiv.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-113">Additionally, a progress control is read only, and not interactive.</span></span> <span data-ttu-id="c1e6e-114">Dies bedeutet, dass der Benutzer diese Steuerelemente nicht direkt aufrufen oder verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-114">Meaning that the user cannot invoke or use these controls directly.</span></span>

![ProgressBar-Status](images/ProgressBar_TwoStates.png)

*<span data-ttu-id="c1e6e-116">Von oben nach unten – unbestimmtes ProgressBar-Element und bestimmtes ProgressBar-Element</span><span class="sxs-lookup"><span data-stu-id="c1e6e-116">Top to bottom - Indeterminate ProgressBar and a determinate ProgressBar</span></span>*

![ProgressRing-Status](images/ProgressRing_SingleState.png)

*<span data-ttu-id="c1e6e-118">Ein unbestimmtes ProgressRing-Element</span><span class="sxs-lookup"><span data-stu-id="c1e6e-118">An indeterminate ProgressRing</span></span>*

## <a name="examples"></a><span data-ttu-id="c1e6e-119">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c1e6e-119">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="c1e6e-120">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="c1e6e-120">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="c1e6e-121">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ProgressBar">ProgressBar</a> oder <a href="xamlcontrolsgallery:/item/ProgressRing">ProgressRing</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-121">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/ProgressBar">ProgressBar</a> or <a href="xamlcontrolsgallery:/item/ProgressRing">ProgressRing</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="c1e6e-122">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="c1e6e-122">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="c1e6e-123">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c1e6e-123">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="when-to-use-each-control"></a><span data-ttu-id="c1e6e-124">Verwendung der einzelnen Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="c1e6e-124">When to use each control</span></span>

<span data-ttu-id="c1e6e-125">Es ist nicht immer klar erkennbar, welches Steuerelement oder welcher Status (bestimmt oder unbestimmt) zu verwenden ist, um einen Vorgang anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-125">It's not always obvious what control or what state (determinate vs indeterminate) to use when trying to show something is happening.</span></span> <span data-ttu-id="c1e6e-126">Manchmal ist eine Aufgabe so deutlich zu erkennen, dass kein Statussteuerelement erforderlich ist. Manchmal ist jedoch auch bei Verwendung eines Statussteuerelements eine Textzeile erforderlich, die den Benutzer darüber informiert, welcher Vorgang gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-126">Sometimes a task is obvious enough that it doesn’t require a progress control at all – and sometimes even if a progress control is used, a line of text is still necessary in order to explain to the user what operation is underway.</span></span>

### <a name="progressbar"></a><span data-ttu-id="c1e6e-127">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="c1e6e-127">ProgressBar</span></span>
-   **<span data-ttu-id="c1e6e-128">Verfügt das Steuerelement über eine festgelegte Dauer oder ein vorhersehbares Ende?</span><span class="sxs-lookup"><span data-stu-id="c1e6e-128">Does the control have a defined duration or predictable end?</span></span>**

    <span data-ttu-id="c1e6e-129">Verwenden Sie in diesem Fall eine bestimmte Statusanzeige, und aktualisieren Sie deren Prozentsatz oder Wert entsprechend.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-129">Use a determinate ProgressBar then, and update the percentage or value accordingly.</span></span>

-   **<span data-ttu-id="c1e6e-130">Kann der Benutzer fortfahren, ohne den Status des Vorgang zu überwachen?</span><span class="sxs-lookup"><span data-stu-id="c1e6e-130">Can the user continue without having to monitor the operation’s progress?</span></span>**

    <span data-ttu-id="c1e6e-131">Bei Verwendung eines ProgressBar-Elements ist die Interaktion nicht modal. Das bedeutet in der Regel, dass der Benutzer durch den Abschluss des Vorgangs nicht blockiert wird und die aktive App bis zum Abschluss der Aktion weiterhin verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-131">When a ProgressBar is in use, interaction is non-modal, typically meaning that the user is not blocked by that operation’s completion, and can continue to use the app in other ways until that aspect has completed.</span></span>

-   **<span data-ttu-id="c1e6e-132">Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="c1e6e-132">Keywords</span></span>**

    <span data-ttu-id="c1e6e-133">Wenn der anzuzeigende Vorgang sich mit den folgenden Schlüsselwörtern in Verbindung bringen lässt oder wenn Sie während des Vorgangs Text anzeigen möchten, in dem diese Schlüsselwörter vorkommen, sollten Sie ein ProgressBar-Element verwenden:</span><span class="sxs-lookup"><span data-stu-id="c1e6e-133">If your operation falls around these keywords, or if you’re showing text that alongside the progress operation that matches these keywords; consider using a ProgressBar:</span></span>

    - *<span data-ttu-id="c1e6e-134">Wird geladen...</span><span class="sxs-lookup"><span data-stu-id="c1e6e-134">Loading...</span></span>*
    - *<span data-ttu-id="c1e6e-135">Wird abgerufen...</span><span class="sxs-lookup"><span data-stu-id="c1e6e-135">Retrieving</span></span>*
    - *<span data-ttu-id="c1e6e-136">In Bearbeitung...</span><span class="sxs-lookup"><span data-stu-id="c1e6e-136">Working...</span></span>*

### <a name="progressring"></a><span data-ttu-id="c1e6e-137">ProgressRing</span><span class="sxs-lookup"><span data-stu-id="c1e6e-137">ProgressRing</span></span>

-   **<span data-ttu-id="c1e6e-138">Muss der Benutzer den Abschluss des Vorgangs abwarten, bevor er seine Aktivität fortsetzen kann?</span><span class="sxs-lookup"><span data-stu-id="c1e6e-138">Will the operation cause the user to wait to continue?</span></span>**

    <span data-ttu-id="c1e6e-139">Wenn ein Vorgang bis zu seinem Abschluss eine umfassende Interaktion mit der App erfordert, empfiehlt sich die Verwendung eines ProgressRing-Elements.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-139">If an operation requires all (or a large portion of) interaction with the app to wait until it has been completed, then the ProgressRing is the better choice.</span></span> <span data-ttu-id="c1e6e-140">Das ProgressRing-Steuerelement ist für modale Interaktionen vorgesehen, in denen die Aktivitäten des Benutzers blockiert werden, bis das ProgressRing-Element nicht mehr angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-140">The ProgressRing control is used for modal interactions, meaning that the user is blocked until the ProgressRing disappears.</span></span>

-   **<span data-ttu-id="c1e6e-141">Wartet die App darauf, dass der Benutzer eine Aufgabe ausführt?</span><span class="sxs-lookup"><span data-stu-id="c1e6e-141">Is the app waiting for the user to complete a task?</span></span>**

    <span data-ttu-id="c1e6e-142">In diesem Fall verwenden Sie ein ProgressRing-Steuerelement, um den Benutzer auf eine unbestimmte Wartezeit hinzuweisen.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-142">If so, use a ProgressRing, as they’re meant to indicate an unknown wait time for the user.</span></span>

-   **<span data-ttu-id="c1e6e-143">Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="c1e6e-143">Keywords</span></span>**

    <span data-ttu-id="c1e6e-144">Wenn der anzuzeigende Vorgang sich mit den folgenden Schlüsselwörtern in Verbindung bringen lässt oder wenn Sie während des Vorgangs Text anzeigen möchten, in dem diese Schlüsselwörter vorkommen, sollten Sie ein ProgressRing-Element verwenden:</span><span class="sxs-lookup"><span data-stu-id="c1e6e-144">If your operation falls around these keywords, or if you’re showing text alongside the progress operation that matches these keywords; consider using a ProgressRing:</span></span>

    - *<span data-ttu-id="c1e6e-145">Wird aktualisiert</span><span class="sxs-lookup"><span data-stu-id="c1e6e-145">Refreshing</span></span>*
    - *<span data-ttu-id="c1e6e-146">Anmelden...</span><span class="sxs-lookup"><span data-stu-id="c1e6e-146">Signing in...</span></span>*
    - *<span data-ttu-id="c1e6e-147">Verbinden...</span><span class="sxs-lookup"><span data-stu-id="c1e6e-147">Connecting...</span></span>*

### <a name="no-progress-indication-necessary"></a><span data-ttu-id="c1e6e-148">Keine Fortschrittsanzeige erforderlich</span><span class="sxs-lookup"><span data-stu-id="c1e6e-148">No progress indication necessary</span></span>
-   **<span data-ttu-id="c1e6e-149">Müssen Benutzer wissen, dass Vorgänge ausgeführt werden?</span><span class="sxs-lookup"><span data-stu-id="c1e6e-149">Does the user need to know that something is happening?</span></span>**

    <span data-ttu-id="c1e6e-150">Wenn die App z.B. im Hintergrund einen Download ausführt, der nicht vom Benutzer eingeleitet wurde, ist es auch nicht unbedingt erforderlich, den Benutzer darüber zu informieren.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-150">For example, if the app is downloading something in the background and the user didn’t initiate the download, the user doesn’t necessarily need to know about it.</span></span>

-   **<span data-ttu-id="c1e6e-151">Wird der Vorgang im Hintergrund ausgeführt, ohne die Aktivitäten des Benutzers zu blockieren, und ist er für Benutzer von geringem Interesse, aber nicht völlig irrelevant?</span><span class="sxs-lookup"><span data-stu-id="c1e6e-151">Is the operation a background activity that doesn't block user activity and is of minimal (but still some) interest to the user?</span></span>**

    <span data-ttu-id="c1e6e-152">Verwenden Sie Text, wenn die App Aufgaben ausführt, die zwar nicht immer sichtbar sein müssen, bei denen aber der Status angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-152">Use text when your app is performing tasks that don't have to be visible all the time, but you still need to show the status.</span></span>

-   **<span data-ttu-id="c1e6e-153">Möchte der Benutzer nur über den Abschluss des Vorgangs informiert werden?</span><span class="sxs-lookup"><span data-stu-id="c1e6e-153">Does the user only care about the completion of the operation?</span></span>**

    <span data-ttu-id="c1e6e-154">Manchmal ist es am besten, nur auf den Abschluss eines Vorgangs hinzuweisen oder den unmittelbaren Abschluss des Vorgangs durch ein visuelles Element anzukündigen, und den restlichen Vorgang im Hintergrund auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-154">Sometimes it’s best to show a notice only when the operation is completed, or give a visual that the operation has been completed immediately, and run the finishing touches in the background.</span></span>

## <a name="progress-controls-best-practices"></a><span data-ttu-id="c1e6e-155">Bewährte Methoden für Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="c1e6e-155">Progress controls best practices</span></span>

<span data-ttu-id="c1e6e-156">Manchmal ist eine visuelle Darstellung hilfreich, um zu ermitteln, zu welchem Zeitpunkt welches Statussteuerelement verwendet werden sollte:</span><span class="sxs-lookup"><span data-stu-id="c1e6e-156">Sometimes it’s best to see some visual representations of when and where to use these different progress controls:</span></span>

**<span data-ttu-id="c1e6e-157">ProgressBar – bestimmt</span><span class="sxs-lookup"><span data-stu-id="c1e6e-157">ProgressBar - Determinate</span></span>**

![Beispiel für ein bestimmtes ProgressBar-Element](images/PB_DeterminateExample.png)

<span data-ttu-id="c1e6e-159">Beim ersten Beispiel handelt es sich um ein bestimmtes ProgressBar-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-159">The first example is the determinate ProgressBar.</span></span> <span data-ttu-id="c1e6e-160">Wenn die Dauer des Vorgangs bekannt ist, etwa beim Installieren, Herunterladen oder Einrichten, eignet sich ein bestimmtes ProgressBar-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-160">When the duration of the operation is known, when installing, downloading, setting up, etc; a determinate ProgressBar is best.</span></span>

**<span data-ttu-id="c1e6e-161">ProgressBar – unbestimmt</span><span class="sxs-lookup"><span data-stu-id="c1e6e-161">ProgressBar - Indeterminate</span></span>**

![Beispiel für ein unbestimmtes ProgressBar-Element](images/PB_IndeterminateExample.png)

<span data-ttu-id="c1e6e-163">Wenn die Dauer des Vorgangs nicht bekannt ist, verwenden Sie ein unbestimmtes ProgressBar-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-163">When it is not known how long the operation will take, use an indeterminate ProgressBar.</span></span> <span data-ttu-id="c1e6e-164">Unbestimmte ProgressBar-Elemente können auch beim Ausfüllen virtualisierter Listen verwendet werden oder um einen glatten visuellen Übergang von einem unbestimmten zu einem bestimmten ProgressBar-Element zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-164">Indeterminate ProgressBars are also good when filling a virtualized list, and creating a smooth visual transition between an indeterminate to determinate ProgressBar.</span></span>

-   **<span data-ttu-id="c1e6e-165">Befindet sich der Vorgang in einer virtualisierten Sammlung?</span><span class="sxs-lookup"><span data-stu-id="c1e6e-165">Is the operation in a virtualized collection?</span></span>**

    <span data-ttu-id="c1e6e-166">In diesem Fall legen Sie nicht für jedes angezeigte Listenelement eine Statusanzeige fest.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-166">If so, do not put a progress indicator on each list item as they appear.</span></span> <span data-ttu-id="c1e6e-167">Positionieren Sie stattdessen ein ProgressBar-Element am Anfang der Auflistung der zu ladenden Elemente, um anzuzeigen, dass die Elemente geladen werden.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-167">Instead, use a ProgressBar and place it at the top of the collection of items being loaded in, to show that the items are being fetched.</span></span>

**<span data-ttu-id="c1e6e-168">ProgressRing – unbestimmt</span><span class="sxs-lookup"><span data-stu-id="c1e6e-168">ProgressRing - Indeterminate</span></span>**

![Beispiel für ein unbestimmtes ProgressRing-Steuerelement](images/PR_IndeterminateExample.png)

<span data-ttu-id="c1e6e-170">Unbestimmte ProgressRing-Elemente werden verwendet, wenn jegliche Benutzerinteraktion mit der App ausgesetzt ist oder die App auf eine Benutzereingabe wartet, um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-170">The indeterminate ProgressRing is used when any further user interaction with the app is halted, or the app is waiting for the user’s input to continue.</span></span> <span data-ttu-id="c1e6e-171">Das „Anmelden...“-</span><span class="sxs-lookup"><span data-stu-id="c1e6e-171">The “signing in…”</span></span> <span data-ttu-id="c1e6e-172">Beispiel oben ist ein optimales Szenario für das ProgressRing-Steuerelement, da der Benutzer die App erst weiterverwenden kann, nachdem der Anmeldevorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-172">example above is a perfect scenario for the ProgressRing, the user cannot continue using the app until the sign is has completed.</span></span>

## <a name="customizing-a-progress-control"></a><span data-ttu-id="c1e6e-173">Anpassen eines Statussteuerelements</span><span class="sxs-lookup"><span data-stu-id="c1e6e-173">Customizing a progress control</span></span>

<span data-ttu-id="c1e6e-174">Die beiden Statussteuerelemente sind recht einfach gehalten. Bei verschiedenen visuellen Features der Steuerelemente sind jedoch deren Anpassungsoptionen nicht offensichtlich.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-174">Both progress controls are rather simple; but some visual features of the controls are not obvious to customize.</span></span>

**<span data-ttu-id="c1e6e-175">Ändern der Größe des ProgressRing-Elements</span><span class="sxs-lookup"><span data-stu-id="c1e6e-175">Sizing the ProgressRing</span></span>**

<span data-ttu-id="c1e6e-176">Sie können das ProgressRing-Element so groß gestalten, wie Sie möchten. Die Mindestgröße beträgt jedoch 20x20Epx.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-176">The ProgressRing can be sized as large as you want, but can only be as small as 20x20epx.</span></span> <span data-ttu-id="c1e6e-177">Um die Größe eines ProgressRing-Elements zu ändern, müssen Sie dessen Höhe und Breite festlegen.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-177">In order to resize a ProgressRing, you must set its height and width.</span></span> <span data-ttu-id="c1e6e-178">Wenn nur die Höhe oder nur die Breite festgelegt wird, erhält das Steuerelement die Mindestgröße (20x20Epx). Wenn die Höhe und die Breite auf zwei verschiedene Größen festgelegt sind, wird die kleinere Größen verwendet.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-178">If only height or width are set, the control will assume minimum sizing (20x20epx) – conversely if the height and width are set to two different sizes, the smaller of the sizes will be assumed.</span></span>
<span data-ttu-id="c1e6e-179">Um sicherzustellen, dass Ihr ProgressRing-Steuerelement seinen Zweck erfüllt, legen Sie für die Höhe und die Breite denselben Wert fest:</span><span class="sxs-lookup"><span data-stu-id="c1e6e-179">To ensure your ProgressRing is correct for your needs, set both the height and the width to the same value:</span></span>

```XAML
<ProgressRing Height="100" Width="100"/>
```

<span data-ttu-id="c1e6e-180">Wenn das ProgressRing-Element sichtbar und animiert sein soll, legen Sie die IsActive-Eigenschaft auf „true“ fest:</span><span class="sxs-lookup"><span data-stu-id="c1e6e-180">To make your ProgressRing visible, and animate, you must set the IsActive property to true:</span></span>

```XAML
<ProgressRing IsActive="True" Height="100" Width="100"/>
```

```C#
progressRing.IsActive = true;
```

**<span data-ttu-id="c1e6e-181">Farben der Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="c1e6e-181">Coloring the progress controls</span></span>**

<span data-ttu-id="c1e6e-182">Standardmäßig ist die Grundfarbe der Statussteuerelemente auf die Akzentfarbe des Systems festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-182">By default, the main coloring of the progress controls is set to the accent color of the system.</span></span> <span data-ttu-id="c1e6e-183">Dies können Sie anpassen, indem Sie einfach die „Foreground“-Eigenschaft der Steuerelemente ändern.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-183">To override this brush simply change the foreground property on either control.</span></span>

```XAML
<ProgressRing IsActive="True" Height="100" Width="100" Foreground="Blue"/>
<ProgressBar Width="100" Foreground="Green"/>
```

<span data-ttu-id="c1e6e-184">Durch das Ändern die Vordergrundfarbe des ProgressRing-Elements ändern sich die Farben der Punkte.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-184">Changing the foreground color for the ProgressRing will change the colors of the dots.</span></span> <span data-ttu-id="c1e6e-185">Die „Foreground“-Eigenschaft des ProgressBar-Elements ändert dann die Füllfarbe der Leiste. Um den ungefüllten Teil der Leiste zu ändern, überschreiben Sie einfach die „Background“-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-185">The foreground property for the ProgressBar will change the fill color of the bar – to alter the unfilled portion of the bar, simply override the background property.</span></span>

**<span data-ttu-id="c1e6e-186">Anzeigen eines Wartecursors</span><span class="sxs-lookup"><span data-stu-id="c1e6e-186">Showing a wait cursor</span></span>**

<span data-ttu-id="c1e6e-187">Manchmal ist es am besten, nur kurz einen Wartecursor anzuzeigen, wenn eine App oder ein Vorgang etwas Zeit erfordert und Sie dem Benutzer anzeigen müssen, dass mit der App oder dem Bereich, in dem sich der Wartecursor befindet, bis zu dessen Ausblenden nicht interagiert werden sollte.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-187">Sometimes it’s best to just show a brief wait cursor, when the app or operation needs time to think, and you need to indicate to the user that the app or area where the wait cursor is visible should not be interacted with until the wait cursor has disappeared.</span></span>

```C#
Window.Current.CoreWindow.PointerCursor = new Windows.UI.Core.CoreCursor(Windows.UI.Core.CoreCursorType.Wait, 10);
```

## <a name="get-the-sample-code"></a><span data-ttu-id="c1e6e-188">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="c1e6e-188">Get the sample code</span></span>

- <span data-ttu-id="c1e6e-189">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c1e6e-189">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="c1e6e-190">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c1e6e-190">Related articles</span></span>

- [<span data-ttu-id="c1e6e-191">ProgressBar-Klasse</span><span class="sxs-lookup"><span data-stu-id="c1e6e-191">ProgressBar class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227529)
- [<span data-ttu-id="c1e6e-192">ProgressRing-Klasse</span><span class="sxs-lookup"><span data-stu-id="c1e6e-192">ProgressRing class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227538)

**<span data-ttu-id="c1e6e-193">Für Entwickler (XAML)</span><span class="sxs-lookup"><span data-stu-id="c1e6e-193">For developers (XAML)</span></span>**
- [<span data-ttu-id="c1e6e-194">Hinzufügen von Statussteuerelementen</span><span class="sxs-lookup"><span data-stu-id="c1e6e-194">Adding progress controls</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh780651)
- [<span data-ttu-id="c1e6e-195">So wird's gemacht: Erstellen einer benutzerdefinierten unbestimmten Statusleiste für Windows Phone</span><span class="sxs-lookup"><span data-stu-id="c1e6e-195">How to create a custom indeterminate progress bar for Windows Phone</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=392426)
