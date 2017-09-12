---
author: mijacobs
Description: "Dialogfelder und Flyouts zeigen vorübergehende UI-Elemente an, die angezeigt werden, wenn der Benutzer sie anfordert oder eine Aktion erfolgt, die eine Benachrichtigung oder Genehmigung erfordert."
title: Dialogfelder und Flyouts
label: Dialogs
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: ad6affd9-a3c0-481f-a237-9a1ecd561be8
pm-contact: yulikl
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.openlocfilehash: a1e7ecd60c960459d8d146bbda0fa6fba4bfc7f6
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="dialogs-and-flyouts"></a><span data-ttu-id="7fa50-104">Dialogfelder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="7fa50-104">Dialogs and flyouts</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="7fa50-105">Dialogfelder und Flyouts sind vorübergehende UI-Elemente, die angezeigt werden, wenn Ereignisse Benachrichtigungen, Genehmigungen oder zusätzliche Informationen vom Benutzer erfordern.</span><span class="sxs-lookup"><span data-stu-id="7fa50-105">Dialogs and flyouts are transient UI elements that appear when something happens that requires notification, approval, or additional information from the user.</span></span>

> <span data-ttu-id="7fa50-106">**Wichtige APIs**: [ContentDialog-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx), [Flyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn279496)</span><span class="sxs-lookup"><span data-stu-id="7fa50-106">**Important APIs**: [ContentDialog class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx), [Flyout class](https://msdn.microsoft.com/library/windows/apps/dn279496)</span></span>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b><span data-ttu-id="7fa50-107">Dialogfelder</span><span class="sxs-lookup"><span data-stu-id="7fa50-107">Dialogs</span></span></b> <br/><br/>
    ![Beispiel für ein Dialogfeld](images/dialogs/dialog_RS2_delete_file.png)</p>
<p><span data-ttu-id="7fa50-109">Dialogfelder sind modale Benutzeroberflächenüberlagerungen, die kontextbezogene App-Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="7fa50-109">Dialogs are modal UI overlays that provide contextual app information.</span></span> <span data-ttu-id="7fa50-110">Dialogfelder blockieren Interaktionen mit dem App-Fenster, bis sie explizit geschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-110">Dialogs block interactions with the app window until being explicitly dismissed.</span></span> <span data-ttu-id="7fa50-111">Sie verlangen häufig eine Aktion vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="7fa50-111">They often request some kind of action from the user.</span></span>   
</p><br/>

  </div>
  <div class="side-by-side-content-right">
   <p><b><span data-ttu-id="7fa50-112">Flyouts</span><span class="sxs-lookup"><span data-stu-id="7fa50-112">Flyouts</span></span></b> <br/><br/>
   ![Flyout-Beispiel](images/flyout-example2.png)</p>
<p><span data-ttu-id="7fa50-114">Ein Flyout ist ein einfaches, kontextbezogenes Popupmenü, das die UI entsprechend den Aktionen des Benutzers anzeigt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-114">A flyout is a lightweight contextual popup that displays UI related to what the user is doing.</span></span> <span data-ttu-id="7fa50-115">Es umfasst die Platzierungs- und Größenlogik und kann dazu verwendet werden, ein sekundäres Steuerelement oder weitere Einzelheiten zu einem Element anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-115">It includes placement and sizing logic, and can be used to reveal a secondary control or show more detail about an item.</span></span>
</p><p><span data-ttu-id="7fa50-116">Im Gegensatz zu einem Dialogfeld kann ein Flyout durch Tippen oder Klicken auf eine Stelle außerhalb des Flyouts schnell geschlossen werden. Das Drücken der ESC- oder Zurück-Taste sowie das Ändern der Größe des App-Fensters oder der Ausrichtung des Geräts haben denselben Effekt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-116">Unlike a dialog, a flyout can be quickly dismissed by tapping or clicking somewhere outside the flyout, pressing the Escape key or Back button, resizing the app window, or changing the device's orientation.</span></span>
</p><br/>

  </div>
</div>
</div>

## <a name="is-this-the-right-control"></a><span data-ttu-id="7fa50-117">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="7fa50-117">Is this the right control?</span></span>

* <span data-ttu-id="7fa50-118">Verwenden Sie Dialogfelder und Flyouts, um Benutzern wichtige Informationen mitzuteilen oder deren Bestätigung bzw. zusätzliche Informationen anzufordern, bevor eine Aktion abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="7fa50-118">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>
* <span data-ttu-id="7fa50-119">Verwenden Sie Flyouts nicht anstelle von [QuickInfos](tooltips.md) oder [Kontextmenüs](menus.md).</span><span class="sxs-lookup"><span data-stu-id="7fa50-119">Don't use a flyout instead of [tooltip](tooltips.md) or [context menu](menus.md).</span></span> <span data-ttu-id="7fa50-120">Verwenden Sie QuickInfos, um kurze Beschreibungen anzuzeigen, die nach einer festgelegten Zeit ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-120">Use a tooltip to show a short description that hides after a specified time.</span></span> <span data-ttu-id="7fa50-121">Verwenden Sie ein Kontextmenü für kontextbezogene Aktionen im Zusammenhang mit UI-Elementen (beispielsweise Kopieren und Einfügen).</span><span class="sxs-lookup"><span data-stu-id="7fa50-121">Use a context menu for contextual actions related to a UI element, such as copy and paste.</span></span>  


<span data-ttu-id="7fa50-122">Dialogfelder und Flyouts stellen sicher, dass den Benutzern wichtige Informationen bekannt sind, stellen jedoch auch eine Unterbrechung dar.</span><span class="sxs-lookup"><span data-stu-id="7fa50-122">Dialogs and flyouts make sure that users are aware of important information, but they also disrupt the user experience.</span></span> <span data-ttu-id="7fa50-123">Da Dialogfelder modal (blockierend) sind, werden die Benutzer unterbrochen und daran gehindert, andere Schritte durchzuführen, bis eine Interaktion mit dem Dialogfeld erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="7fa50-123">Because dialogs are modal (blocking), they interrupt users, preventing them from doing anything else until they interact with the dialog.</span></span> <span data-ttu-id="7fa50-124">Flyouts sind weniger störend. Zu viele Flyouts können jedoch als störend empfunden werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-124">Flyouts provide a less jarring experience, but displaying too many flyouts can be distracting.</span></span>

<span data-ttu-id="7fa50-125">Berücksichtigen Sie die Bedeutung der zu vermittelnden Informationen: Sind sie wichtig genug, um den Benutzer zu unterbrechen?</span><span class="sxs-lookup"><span data-stu-id="7fa50-125">Consider the importance of the information you want to share: is it important enough to interrupt the user?</span></span> <span data-ttu-id="7fa50-126">Berücksichtigen Sie zudem, wie häufig die Informationen angezeigt werden müssen. Wenn ein Dialogfeld oder eine Benachrichtigung alle paar Minuten angezeigt wird, sollten Sie diese Informationen stattdessen in die primäre UI einbinden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-126">Also consider how frequently the information needs to be shown; if you're showing a dialog or notification every few minutes, you might want to allocate space for this info in the primary UI instead.</span></span> <span data-ttu-id="7fa50-127">So können Sie z.B. in einem Chat-Client anstatt eines Flyouts, der jedes Mal angezeigt wird, wenn sich ein Freund anmeldet, eine Liste der Freunde anzeigen, die derzeit online sind, und diejenigen Freunde hervorheben, die sich gerade anmelden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-127">For example, in a chat client, rather than showing a flyout every time a friend logs in, you might display a list of friends who are online at the moment and highlight friends as they log on.</span></span>

<span data-ttu-id="7fa50-128">Dialogfelder werden häufig zum Bestätigen einer Aktion vor deren Ausführung verwendet (z.B. vor dem Löschen einer Datei).</span><span class="sxs-lookup"><span data-stu-id="7fa50-128">Dialogs are frequently used to confirm an action (such as deleting a file) before executing it.</span></span> <span data-ttu-id="7fa50-129">Wenn Sie davon ausgehen, dass die Benutzer häufig eine bestimmte Aktion ausführen, sollten Sie eine Möglichkeit bereitstellen, versehentliche Aktionen rückgängig zu machen, anstatt jedes Mal die Bestätigung der Aktion zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-129">If you expect the user to perform a particular action frequently, consider providing a way for the user to undo the action if it was a mistake, rather than forcing users to confirm the action every time.</span></span>

## <a name="dialogs-vs-flyouts"></a><span data-ttu-id="7fa50-130">Dialogfelder im Vergleich zu Flyouts</span><span class="sxs-lookup"><span data-stu-id="7fa50-130">Dialogs vs. flyouts</span></span>

<span data-ttu-id="7fa50-131">Wenn ein Dialogfeld oder Flyout eingesetzt werden soll, müssen Sie sich für eine der beiden Optionen entscheiden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-131">Once you've determined that you want to use a dialog or flyout, you need to choose which one to use.</span></span>

<span data-ttu-id="7fa50-132">Angesichts der Tatsache, dass Dialogfelder im Gegensatz zu Flyouts Interaktionen blockieren, sollten Dialogfelder auf Situationen beschränkt bleiben, in denen der Benutzer unterbrochen werden soll, um sich auf eine bestimmte Information oder die Beantwortung einer Frage zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="7fa50-132">Given that dialogs block interactions and flyouts do not, dialogs should be reserved for situations where you want the user to drop everything to focus on a specific bit of information or answer a question.</span></span> <span data-ttu-id="7fa50-133">Flyouts hingegen können verwendet werden, wenn Sie auf etwas aufmerksam machen möchten, das der Benutzer jedoch ignorieren kann.</span><span class="sxs-lookup"><span data-stu-id="7fa50-133">Flyouts, on the other hand, can be used when you want to call attention to something, but it's ok if the user wants to ignore it.</span></span>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b><span data-ttu-id="7fa50-134">Fälle, in denen ein Dialogfeld verwendet werden sollte:</span><span class="sxs-lookup"><span data-stu-id="7fa50-134">Use a dialog for...</span></span></b> <br/>
<ul>
<li><span data-ttu-id="7fa50-135">Für wichtige Informationen, die der Benutzer vor dem Fortsetzen lesen und bestätigen **muss**.</span><span class="sxs-lookup"><span data-stu-id="7fa50-135">Expressing important information that the user **must** read and acknowledge before proceeding.</span></span> <span data-ttu-id="7fa50-136">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="7fa50-136">Examples include:</span></span>
<ul>
  <li><span data-ttu-id="7fa50-137">Die Sicherheit des Benutzers ist möglicherweise gefährdet.</span><span class="sxs-lookup"><span data-stu-id="7fa50-137">When the user's security might be compromised</span></span></li>
  <li><span data-ttu-id="7fa50-138">Der Benutzer möchte eine wertvolle Ressource endgültig ändern.</span><span class="sxs-lookup"><span data-stu-id="7fa50-138">When the user is about to permanently alter a valuable asset</span></span></li>
  <li><span data-ttu-id="7fa50-139">Der Benutzer möchte eine wertvolle Ressource löschen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-139">When the user is about to delete a valuable asset</span></span></li>
  <li><span data-ttu-id="7fa50-140">Bestätigen eines In-App-Einkaufs</span><span class="sxs-lookup"><span data-stu-id="7fa50-140">To confirm an in-app purchase</span></span></li>
</ul>

</li>
<li><span data-ttu-id="7fa50-141">Fehlermeldungen, die sich auf den Gesamtkontext der App beziehen, z. B. Verbindungsfehler.</span><span class="sxs-lookup"><span data-stu-id="7fa50-141">Error messages that apply to the overall app context, such as a connectivity error.</span></span></li>
<li><span data-ttu-id="7fa50-142">Fragen, wenn dem Benutzer eine blockierende Frage gestellt werden muss, z. B. wenn die App nicht im Auftrag des Benutzers eine Auswahl treffen kann.</span><span class="sxs-lookup"><span data-stu-id="7fa50-142">Questions, when the app needs to ask the user a blocking question, such as when the app can't choose on the user's behalf.</span></span> <span data-ttu-id="7fa50-143">Eine blockierende Frage kann nicht ignoriert oder verschoben werden und sollte dem Benutzer klar definierte Auswahlmöglichkeiten bieten.</span><span class="sxs-lookup"><span data-stu-id="7fa50-143">A blocking question can't be ignored or postponed, and should offer the user well-defined choices.</span></span></li>
</ul>
</p>
  </div>
  <div class="side-by-side-content-right">
   <p><b><span data-ttu-id="7fa50-144">Fälle, in denen ein Flyout verwendet werden sollte:</span><span class="sxs-lookup"><span data-stu-id="7fa50-144">Use a flyout for...</span></span></b> <br/>
<ul>
<li><span data-ttu-id="7fa50-145">Erfassen zusätzlicher Informationen, die erforderlich sind, bevor eine Aktion abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="7fa50-145">Collecting additional information needed before an action can be completed.</span></span></li>
<li><span data-ttu-id="7fa50-146">Anzeigen von Informationen, die nur vorübergehend relevant sind.</span><span class="sxs-lookup"><span data-stu-id="7fa50-146">Displaying info that's only relevant some of the time.</span></span> <span data-ttu-id="7fa50-147">So können Sie z.B. in einer Fotogalerie-App ein Flyout einsetzen, damit eine große Version des Bilds angezeigt wird, wenn der Benutzer auf eine Miniaturansicht klickt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-147">For example, in a photo gallery app, when the user clicks an image thumbnail, you might use a flyout to display a large version of the image.</span></span></li>
<li><span data-ttu-id="7fa50-148">Anzeigen weiterer Informationen, z. B. von Details oder ausführlicheren Beschreibungen eines Elements auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="7fa50-148">Displaying more information, such as details or longer descriptions of an item on the page.</span></span></li>
</ul></p>
  </div>
</div>
</div>

## <a name="dialogs"></a><span data-ttu-id="7fa50-149">Dialogfelder</span><span class="sxs-lookup"><span data-stu-id="7fa50-149">Dialogs</span></span>
### <a name="general-guidelines"></a><span data-ttu-id="7fa50-150">Allgemeine Richtlinien</span><span class="sxs-lookup"><span data-stu-id="7fa50-150">General guidelines</span></span>

-   <span data-ttu-id="7fa50-151">Sie sollten das Problem oder das Ziel des Benutzers in der ersten Zeile des Dialogfeldtexts deutlich benennen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-151">Clearly identify the issue or the user's objective in the first line of the dialog's text.</span></span>
-   <span data-ttu-id="7fa50-152">Der Dialogfeldtitel ist die Hauptanweisung und optional.</span><span class="sxs-lookup"><span data-stu-id="7fa50-152">The dialog title is the main instruction and is optional.</span></span>
    -   <span data-ttu-id="7fa50-153">Verwenden Sie einen kurzen Titel, um dem Benutzer die erforderlichen Aktionen im Dialogfeld zu erklären.</span><span class="sxs-lookup"><span data-stu-id="7fa50-153">Use a short title to explain what people need to do with the dialog.</span></span>
    -   <span data-ttu-id="7fa50-154">Wenn Sie mit dem Dialogfeld eine einfache Meldung, einen Fehler oder eine Frage anzeigen möchten, können Sie den Titel optional auslassen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-154">If you're using the dialog to deliver a simple message, error or question, you can optionally omit the title.</span></span> <span data-ttu-id="7fa50-155">Vermitteln Sie dann im Inhalt die wichtigsten Informationen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-155">Rely on the content text to deliver that core information.</span></span>
    -   <span data-ttu-id="7fa50-156">Stellen Sie sicher, dass sich der Titel direkt auf die Auswahlmöglichkeiten der Schaltflächen bezieht.</span><span class="sxs-lookup"><span data-stu-id="7fa50-156">Make sure that the title relates directly to the button choices.</span></span>
-   <span data-ttu-id="7fa50-157">Der Inhalt des Dialogfelds enthält den beschreibenden Text und ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7fa50-157">The dialog content contains the descriptive text and is required.</span></span>
    -   <span data-ttu-id="7fa50-158">Stellen Sie die Meldung, den Fehler oder die blockierende Frage so einfach wie möglich dar.</span><span class="sxs-lookup"><span data-stu-id="7fa50-158">Present the message, error, or blocking question as simply as possible.</span></span>
    -   <span data-ttu-id="7fa50-159">Stellen Sie bei Verwendung eines Dialogfeldtitels mithilfe des Inhaltsbereichs weitere Details bereit, oder definieren Sie Terminologie.</span><span class="sxs-lookup"><span data-stu-id="7fa50-159">If a dialog title is used, use the content area to provide more detail or define terminology.</span></span> <span data-ttu-id="7fa50-160">Wiederholen Sie nicht den Titel mit anderen Worten.</span><span class="sxs-lookup"><span data-stu-id="7fa50-160">Don't repeat the title with slightly different wording.</span></span>
-   <span data-ttu-id="7fa50-161">Mindestens eine Dialogfeldschaltfläche muss angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-161">At least one dialog button must appear.</span></span>
    -   <span data-ttu-id="7fa50-162">Stellen Sie sicher, dass Ihr Dialogfeld mindestens eine Schaltfläche aufweist, die eine sichere, nicht-destruktive Aktion wie „Alles klar!“, „Schließen“ oder „Abbrechen“ auslöst.</span><span class="sxs-lookup"><span data-stu-id="7fa50-162">Ensure that your dialog has at least one button corresponding to a safe, nondestructive action like "Got it!", "Close", or "Cancel".</span></span> <span data-ttu-id="7fa50-163">Verwenden Sie die CloseButton-API, um diese Schaltfläche hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-163">Use the CloseButton API to add this button.</span></span>
    -   <span data-ttu-id="7fa50-164">Verwenden Sie für den Schaltflächentext konkrete Antworten auf die Hauptanweisung oder den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-164">Use specific responses to the main instruction or content as button text.</span></span> <span data-ttu-id="7fa50-165">Beispiel: „Möchten Sie AppName den Zugriff auf Ihren Standort erlauben?“, gefolgt von den Schaltflächen „Zulassen“ und „Blockieren“.</span><span class="sxs-lookup"><span data-stu-id="7fa50-165">An example is, "Do you want to allow AppName to access your location?", followed by "Allow" and "Block" buttons.</span></span> <span data-ttu-id="7fa50-166">Konkrete Antworten erleichtern das Verständnis und ermöglichen somit eine schnelle Entscheidungsfindung.</span><span class="sxs-lookup"><span data-stu-id="7fa50-166">Specific responses can be understood more quickly, resulting in efficient decision making.</span></span>
    - <span data-ttu-id="7fa50-167">Stellen Sie sicher, dass der Text der Aktionsschaltflächen kurz ist.</span><span class="sxs-lookup"><span data-stu-id="7fa50-167">Ensure that the text of the action buttons is concise.</span></span> <span data-ttu-id="7fa50-168">Kurze Anweisungen ermöglichen dem Benutzer, schnell und zuverlässig eine Entscheidung zu treffen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-168">Short strings enable the user to make a choice quickly and confidently.</span></span>
    - <span data-ttu-id="7fa50-169">Zusätzlich zur sicheren, nicht-destruktiven Aktion können Sie dem Benutzer optional ein oder zwei Aktionsschaltflächen anzeigen, die im Zusammenhang mit der Hauptanweisung stehen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-169">In addition to the safe, nondestructive action, you may optionally present the user with one or two action buttons related to the main instruction.</span></span> <span data-ttu-id="7fa50-170">Diese „bestätigenden“ Aktionsschaltflächen unterstreichen den Hauptgrund des Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="7fa50-170">These "do it" action buttons confirm the main point of the dialog.</span></span> <span data-ttu-id="7fa50-171">Verwenden Sie die PrimaryButton- und SecondaryButton-APIs, um diese „bestätigenden“ Aktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-171">Use the PrimaryButton and SecondaryButton APIs to add these "do it" actions.</span></span>
    - <span data-ttu-id="7fa50-172">Die „bestätigenden“ Aktionsschaltflächen sollten als die am weitesten links stehenden Schaltflächen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-172">The "do it" action button(s) should appears as the leftmost buttons.</span></span> <span data-ttu-id="7fa50-173">Die sichere, nicht-destruktive Aktion sollte als die am weitesten rechts stehende Schaltfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-173">The safe, nondestructive action should appear as the rightmost button.</span></span>
    - <span data-ttu-id="7fa50-174">Sie können optional eine der drei Schaltflächen als Standardschaltfläche des Dialogfelds festlegen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-174">You may optionally choose to differentiate one of the three buttons as the dialog's default button.</span></span> <span data-ttu-id="7fa50-175">Verwenden Sie die DefaultButton-API, um eine der Schaltflächen abzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-175">Use the DefaultButton API to differentiate one of the buttons.</span></span>  
-   <span data-ttu-id="7fa50-176">Verwenden Sie Dialogfelder nicht für kontextbezogene Fehler, die sich auf eine bestimmte Stelle auf der Seite beziehen, beispielsweise Validierungsfehler (wie in Kennwortfeldern). Verwenden Sie die Canvas der App selbst zum Anzeigen von Inlinefehlern.</span><span class="sxs-lookup"><span data-stu-id="7fa50-176">Don't use dialogs for errors that are contextual to a specific place on the page, such as validation errors (in password fields, for example), use the app's canvas itself to show inline errors.</span></span>
- <span data-ttu-id="7fa50-177">Verwenden Sie die [ContentDialog-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx), um Ihre Dialogfeldumgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-177">Use the [ContentDialog class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx) to build your dialog experience.</span></span> <span data-ttu-id="7fa50-178">Verwenden Sie nicht die veraltete MessageDialog-API.</span><span class="sxs-lookup"><span data-stu-id="7fa50-178">Don't use the deprecated MessageDialog API.</span></span>

### <a name="dialog-scenarios"></a><span data-ttu-id="7fa50-179">Dialogfeld-Szenarien</span><span class="sxs-lookup"><span data-stu-id="7fa50-179">Dialog scenarios</span></span>
<span data-ttu-id="7fa50-180">Da Dialogfelder Benutzerinteraktion blockieren, und Schaltflächen für die Benutzer das primäre Mittel sind, ein Dialogfeld zu schließen, sollten Sie sicherstellen, dass Ihr Dialogfeld mindestens eine „sichere“, nicht-destruktive Schaltfläche wie z.B. „Schließen“ oder „Alles klar!“ enthält.</span><span class="sxs-lookup"><span data-stu-id="7fa50-180">Because dialogs block user interaction, and because buttons are the primary mechanism for users to dismiss the dialog, ensure that your dialog contains at least one "safe" and nondestructive button such as "Close" or "Got it!".</span></span> **<span data-ttu-id="7fa50-181">Alle Dialogfelder sollten mindestens eine sichere Aktionsschaltfläche enthalten, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-181">All dialogs should contain at least one safe action button to close the dialog.</span></span>** <span data-ttu-id="7fa50-182">Dadurch wird sichergestellt, dass der Benutzer das Dialogfeld zuverlässig schließen kann, ohne eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-182">This ensures that the user can confidently close the dialog without performing an action.</span></span>
![Dialogfeld mit einer Schaltfläche](images/dialogs/dialog_RS2_one_button.png)

```csharp
private async void DisplayNoWifiDialog()
{
    ContentDialog noWifiDialog = new ContentDialog
    {
        Title = "No wifi connection",
        Content = "Check your connection and try again.",
        CloseButtonText = "Ok"
    };

    ContentDialogResult result = await noWifiDialog.ShowAsync();
}
```

<span data-ttu-id="7fa50-184">Wenn Dialogfelder dazu verwendet werden, eine blockierende Frage anzuzeigen, sollte Ihr Dialogfeld dem Benutzer Aktionsschaltflächen bieten, die im Zusammenhang mit der Frage stehen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-184">When dialogs are used to display a blocking question, your dialog should present the user with action buttons related to the question.</span></span> <span data-ttu-id="7fa50-185">Die „sichere“, nicht-destruktive Schaltfläche kann durch ein oder zwei „bestätigende“ Aktionsschaltflächen ergänzt werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-185">The "safe" and nondestructive button may be accompanied by one or two "do it" action buttons.</span></span> <span data-ttu-id="7fa50-186">Wenn dem Benutzer mehrere Optionen angezeigt werden, stellen Sie sicher, dass die Schaltflächen für die „bestätigende“ und die sichere/„ablehnende“ Aktion den Bezug zur Frage eindeutig darstellen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-186">When presenting the user with multiple options, ensure that the buttons clearly explain the "do it" and safe/"don’t do it" actions related to the question proposed.</span></span>

![Dialogfeld mit zwei Schaltflächen](images/dialogs/dialog_RS2_two_button.png)

```csharp
private async void DisplayLocationPromptDialog()
{
    ContentDialog locationPromptDialog = new ContentDialog
    {
        Title = "Allow AppName to access your location?",
        Content = "AppName uses this information to help you find places, connect with friends, and more.",
        CloseButtonText = "Block",
        PrimaryButtonText = "Allow"
    };

    ContentDialogResult result = await locationPromptDialog.ShowAsync();
}
```

<span data-ttu-id="7fa50-188">Dialogfelder mit drei Schaltflächen werden verwendet, wenn Sie dem Benutzer zwei „bestätigende“ und eine „ablehnende“ Aktion präsentierten möchten.</span><span class="sxs-lookup"><span data-stu-id="7fa50-188">Three button dialogs are used when you present the user with two "do it" actions and a "don’t do it" action.</span></span> <span data-ttu-id="7fa50-189">Dialogfelder mit drei Schaltflächen sollten sparsam verwendet werden und eine klare Unterscheidung zwischen der Sekundäraktion und der sicheren/ablehnenden Aktion enthalten.</span><span class="sxs-lookup"><span data-stu-id="7fa50-189">Three button dialogs should be used sparingly with clear distinctions between the secondary action and the safe/close action.</span></span>

![Dialogfeld mit drei Schaltflächen](images/dialogs/dialog_RS2_three_button.png)

```csharp
private async void DisplaySubscribeDialog()
{
    ContentDialog subscribeDialog = new ContentDialog
    {
        Title = "Subscribe to App Service?",
        Content = "Listen, watch, and play in high definition for only $9.99/month. Free to try, cancel anytime.",
        CloseButtonText = "Not Now",
        PrimaryButtonText = "Subscribe",
        SecondaryButtonText = "Try it"
    };

    ContentDialogResult result = await subscribeDialog.ShowAsync();
}
```

### <a name="the-three-dialog-buttons"></a><span data-ttu-id="7fa50-191">Die drei Schaltflächen des Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="7fa50-191">The three dialog buttons</span></span>
<span data-ttu-id="7fa50-192">Der ContentDialog umfasst drei unterschiedliche Arten von Schaltflächen, die Sie zur Erstellung einer Dialogfeldumgebung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7fa50-192">ContentDialog has three different types of buttons that you can use to build a dialog experience.</span></span>

- <span data-ttu-id="7fa50-193">**CloseButton** – erforderlich – Stellt die sichere, nicht-destruktive Aktion dar, die es dem Benutzer ermöglicht, das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-193">**CloseButton** - Required - Represents the safe, nondestructive action that enables the user to exit the dialog.</span></span> <span data-ttu-id="7fa50-194">Wird als die am weitesten rechts stehende Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-194">Appears as the rightmost button.</span></span>
- <span data-ttu-id="7fa50-195">**PrimaryButton** – optional – Stellt die erste „bestätigende“ Aktion dar.</span><span class="sxs-lookup"><span data-stu-id="7fa50-195">**PrimaryButton** - Optional - Represents the first "do it" action.</span></span> <span data-ttu-id="7fa50-196">Wird als die am weitesten links stehende Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-196">Appears as the leftmost button.</span></span>
- <span data-ttu-id="7fa50-197">**SecondaryButton** – optional – Stellt die zweite „bestätigende“ Aktion dar.</span><span class="sxs-lookup"><span data-stu-id="7fa50-197">**SecondaryButton** - Optional - Represents the second "do it" action.</span></span> <span data-ttu-id="7fa50-198">Wird als mittlere Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-198">Appears as the middle button.</span></span>

<span data-ttu-id="7fa50-199">Mithilfe der integrierten Schaltflächen kann das Dialogfeld optisch an andere Dialogfelder angepasst werden sowie die Position der Schaltflächen passend ausgerichtet werden. Stellen Sie sicher, dass die Schaltflächen entsprechend auf Tastaturbefehle reagieren und der Befehlsbereich sichtbar bleibt, auch wenn die Bildschirmtastatur aufgerufen ist.</span><span class="sxs-lookup"><span data-stu-id="7fa50-199">Using the built-in buttons will position the buttons appropriately, ensure that they correctly respond to keyboard events, ensure that the command area remains visible even when the on-screen keyboard is up, and will make the dialog look consistent with other dialogs.</span></span>

#### <a name="closebutton"></a><span data-ttu-id="7fa50-200">CloseButton</span><span class="sxs-lookup"><span data-stu-id="7fa50-200">CloseButton</span></span>
<span data-ttu-id="7fa50-201">Jedes Dialogfeld sollte eine sichere, nicht-destruktive Aktionsschaltfläche aufweisen, die dem Benutzer das zuverlässige Beenden des Dialogfelds ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="7fa50-201">Every dialog should contain a safe, nondestructive action button that enables the user to confidently exit the dialog.</span></span>

<span data-ttu-id="7fa50-202">Verwenden Sie die ContentDialog.CloseButton-API, um diese Schaltfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-202">Use the ContentDialog.CloseButton API to create this button.</span></span> <span data-ttu-id="7fa50-203">Dadurch schaffen Sie die jeweils richtige Benutzerumgebung für alle Eingabemöglichkeiten wie z.B. Maus, Tastatur, Fingereingabe und Gamepad.</span><span class="sxs-lookup"><span data-stu-id="7fa50-203">This allows you to create the right user experience for all inputs including mouse, keyboard, touch, and gamepad.</span></span> <span data-ttu-id="7fa50-204">Dies ist nötig, wenn:</span><span class="sxs-lookup"><span data-stu-id="7fa50-204">This experience will happen when:</span></span>
<ol>
    <li><span data-ttu-id="7fa50-205">Der Benutzer auf CloseButton klickt oder tippt</span><span class="sxs-lookup"><span data-stu-id="7fa50-205">The user clicks or taps on the CloseButton</span></span> </li>
    <li><span data-ttu-id="7fa50-206">Der Benutzer die Zurück-Taste des Systems betätigt</span><span class="sxs-lookup"><span data-stu-id="7fa50-206">The user presses the system back button</span></span> </li>
    <li><span data-ttu-id="7fa50-207">Der Benutzer auf der Tastatur die ESC-Taste betätigt</span><span class="sxs-lookup"><span data-stu-id="7fa50-207">The user presses the ESC button on the keyboard</span></span> </li>
    <li><span data-ttu-id="7fa50-208">Der Benutzer auf dem Gamepad die B-Taste betätigt</span><span class="sxs-lookup"><span data-stu-id="7fa50-208">The user presses Gamepad B</span></span> </li>
</ol>

<span data-ttu-id="7fa50-209">Wenn der Benutzer auf eine Dialogfeldschaltfläche klickt, gibt die Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) ein [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx) zurück, damit Sie wissen, auf welche Schaltfläche der Benutzer klickt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-209">When the user clicks a dialog button, the [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) method returns a [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx) to let you know which button the user clicks.</span></span> <span data-ttu-id="7fa50-210">Klicken auf CloseButton resultiert in ContentDialogResult.None.</span><span class="sxs-lookup"><span data-stu-id="7fa50-210">Pressing on the CloseButton returns ContentDialogResult.None.</span></span>

#### <a name="primarybutton-and-secondarybutton"></a><span data-ttu-id="7fa50-211">PrimaryButton und SecondaryButton</span><span class="sxs-lookup"><span data-stu-id="7fa50-211">PrimaryButton and SecondaryButton</span></span>
<span data-ttu-id="7fa50-212">Zusätzlich zu CloseButton können Sie dem Benutzer optional ein oder zwei Aktionsschaltflächen anbieten, die im Zusammenhang mit der Hauptanweisung stehen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-212">In addition to the CloseButton, you may optionally present the user with one or two action buttons related to the main instruction.</span></span>
<span data-ttu-id="7fa50-213">Nutzen Sie PrimaryButton für die erste „bestätigende“ Aktion und SecondaryButton für die zweite „bestätigende“ Aktion.</span><span class="sxs-lookup"><span data-stu-id="7fa50-213">Leverage PrimaryButton for the first "do it" action, and SecondaryButton for the second "do it" action.</span></span> <span data-ttu-id="7fa50-214">Bei Dialogfeldern mit drei Schaltflächen stellt PrimaryButton in der Regel eine eindeutig „bestätigende“ Aktion dar, während SecondaryButton in der Regel eine neutrale oder sekundäre, „bestätigende“ Aktion darstellt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-214">In three-button dialogs, the PrimaryButton generally represents the affirmative "do it" action, while the SecondaryButton generally represents a neutral or secondary "do it" action.</span></span>
<span data-ttu-id="7fa50-215">Beispielsweise kann eine App den Benutzer dazu auffordern, einen Dienst zu abonnieren.</span><span class="sxs-lookup"><span data-stu-id="7fa50-215">For example, an app may prompt the user to subscribe to a service.</span></span> <span data-ttu-id="7fa50-216">In diesem Fall ist PrimaryButton die eindeutig „bestätigende“ Aktion und enthält den Text „Abonnieren“, während SecondaryButton als neutrale, „bestätigende“ Aktion den Text „Testen“ aufweist.</span><span class="sxs-lookup"><span data-stu-id="7fa50-216">The PrimaryButton as the affirmative "do it" action would host the Subscribe text, while the SecondaryButton as the neutral "do it" action would host the Try it text.</span></span> <span data-ttu-id="7fa50-217">CloseButton ermöglicht dem Benutzer in diesem Fall, die Aktion ohne Interaktion abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-217">The CloseButton would allow the user to cancel without performing either action.</span></span>

<span data-ttu-id="7fa50-218">Klickt der Benutzer auf PrimaryButton, wird von der Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) ContentDialogResult.Primary zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7fa50-218">When the user clicks on the PrimaryButton, the [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) method returns ContentDialogResult.Primary.</span></span>
<span data-ttu-id="7fa50-219">Klickt der Benutzer auf die SecondaryButton, wird von der Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) ContentDialogResult.Primary zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7fa50-219">When the user clicks on the SecondaryButton, the [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) method returns ContentDialogResult.Secondary.</span></span>

![Dialogfeld mit drei Schaltflächen](images/dialogs/dialog_RS2_three_button.png)

#### <a name="defaultbutton"></a><span data-ttu-id="7fa50-221">DefaultButton</span><span class="sxs-lookup"><span data-stu-id="7fa50-221">DefaultButton</span></span>
<span data-ttu-id="7fa50-222">Sie können optional eine der drei Schaltflächen als Standardschaltfläche festlegen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-222">You may optionally choose to differentiate one of the three buttons as the default button.</span></span> <span data-ttu-id="7fa50-223">Das Festlegen einer Standardschaltfläche hat zur Folge, dass:</span><span class="sxs-lookup"><span data-stu-id="7fa50-223">Specifying the default button causes the following to happen:</span></span>
- <span data-ttu-id="7fa50-224">die Schaltfläche optisch als Akzentschaltfläche behandelt wird</span><span class="sxs-lookup"><span data-stu-id="7fa50-224">The button receives the Accent Button visual treatment</span></span>
- <span data-ttu-id="7fa50-225">die Schaltfläche automatisch auf die EINGABETASTE reagiert</span><span class="sxs-lookup"><span data-stu-id="7fa50-225">The button will respond to the ENTER key automatically</span></span>
    - <span data-ttu-id="7fa50-226">Drückt der Benutzer auf der Tastatur die EINGABETASTE, wird der mit der Standardschaltfläche verknüpfte Click-Handler ausgelöst und das ContentDialogResult gibt den mit der Standardschaltfläche verknüpften Wert zurück</span><span class="sxs-lookup"><span data-stu-id="7fa50-226">When the user presses the ENTER key on the keyboard, the click handler associated with the Default Button will fire and the ContentDialogResult will return the value associated with the Default Button</span></span>
    - <span data-ttu-id="7fa50-227">Wenn der Benutzer den Tastaturfokus auf ein Steuerelement gelegt hat, das die EINGABETASTE handhabt, reagiert die Standardschaltfläche nicht auf Drücken der EINGABETASTE</span><span class="sxs-lookup"><span data-stu-id="7fa50-227">If the user has placed Keyboard Focus on a control that handles ENTER, the Default Button will not respond to ENTER presses</span></span>
- <span data-ttu-id="7fa50-228">Die Schaltfläche erhält den Fokus automatisch, wenn das Dialogfeld geöffnet wird, es sei denn, der Inhalt des Dialogfelds enthält fokussierbare UI</span><span class="sxs-lookup"><span data-stu-id="7fa50-228">The button will receive focus automatically when the Dialog is opened unless the dialog’s content contains focusable UI</span></span>

<span data-ttu-id="7fa50-229">Verwenden Sie die ContentDialog.DefaultButton-Eigenschaft, um die Standardschaltfläche anzugeben.</span><span class="sxs-lookup"><span data-stu-id="7fa50-229">Use the ContentDialog.DefaultButton property to indicate the default button.</span></span> <span data-ttu-id="7fa50-230">Standardmäßig wird keine Standardschaltfläche festgelegt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-230">By default, no default button is set.</span></span>

![Ein Dialogfeld mit drei Schaltflächen mit einer Standardschaltfläche](images/dialogs/dialog_RS2_three_button_default.png)

```csharp
private async void DisplaySubscribeDialog()
{
    ContentDialog subscribeDialog = new ContentDialog
    {
        Title = "Subscribe to App Service?",
        Content = "Listen, watch, and play in high definition for only $9.99/month. Free to try, cancel anytime.",
        CloseButtonText = "Not Now",
        PrimaryButtonText = "Subscribe",
        SecondaryButtonText = "Try it",
        DefaultButton = ContentDialogButton.Primary
    };

    ContentDialogResult result = await subscribeDialog.ShowAsync();
}
```

### <a name="confirmation-dialogs-okcancel"></a><span data-ttu-id="7fa50-232">Bestätigungsdialogfelder (OK/Abbrechen)</span><span class="sxs-lookup"><span data-stu-id="7fa50-232">Confirmation dialogs (OK/Cancel)</span></span>
<span data-ttu-id="7fa50-233">In einem Bestätigungsdialogfeld können Benutzer bestätigen, dass sie eine Aktion ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="7fa50-233">A confirmation dialog gives users the chance to confirm that they want to perform an action.</span></span> <span data-ttu-id="7fa50-234">Sie können die Aktion bestätigen oder den Vorgang abbrechen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-234">They can affirm the action, or choose to cancel.</span></span>  
<span data-ttu-id="7fa50-235">Ein typisches Bestätigungsdialogfeld verfügt über zwei Schaltflächen: eine Schaltfläche zur Bestätigung („OK“) und eine Schaltfläche zum Abbrechen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-235">A typical confirmation dialog has two buttons: an affirmation ("OK") button and a cancel button.</span></span>  

<ul>
    <li>
        <p><span data-ttu-id="7fa50-236">Die Bestätigungsschaltfläche sollte sich im Allgemeinen auf der linken Seite (die primäre Schaltfläche) und die Abbruchschaltfläche (die sekundäre Schaltfläche) auf der rechten Seite befinden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-236">In general, the affirmation button should be on the left (the primary button) and the cancel button (the secondary button) should be on the right.</span></span></p>
         ![Dialogfeld zum Bestätigen/Abbrechen einer Aktion](images/dialogs/dialog_RS2_delete_file.png)

    </li>
    <li><span data-ttu-id="7fa50-238">Wie in den allgemeinen Empfehlungen erwähnt, sollten Sie Schaltflächen mit Text verwenden, der konkrete Antworten auf die Hauptanweisung bzw. den Hauptinhalt bietet.</span><span class="sxs-lookup"><span data-stu-id="7fa50-238">As noted in the general recommendations section, use buttons with text that identifies specific responses to the main instruction or content.</span></span>
    </li>
</ul>

> <span data-ttu-id="7fa50-239">Auf einigen Plattformen befindet sich die Bestätigungsschaltfläche auf der rechten anstatt auf der linken Seite.</span><span class="sxs-lookup"><span data-stu-id="7fa50-239">Some platforms put the affirmation button on the right instead of the left.</span></span> <span data-ttu-id="7fa50-240">Warum empfehlen wir die Platzierung auf der linken Seite?</span><span class="sxs-lookup"><span data-stu-id="7fa50-240">So why do we recommend putting it on the left?</span></span>  <span data-ttu-id="7fa50-241">Wenn Sie davon ausgehen, dass die meisten Benutzer Rechtshänder sind und ihr Telefon in dieser Hand halten, ist es bequemer, eine Bestätigungsschaltfläche zu drücken, die sich auf der linken Seite befindet, weil sie für den Benutzer wahrscheinlich einfacher mit dem Daumen erreichbar ist.</span><span class="sxs-lookup"><span data-stu-id="7fa50-241">If you assume that the majority of users are right-handed and they hold their phone with that hand, it's actually more comfortable to press the affirmation button when it's on the left, because the button is more likely to be within the user's thumb-arc.</span></span> <span data-ttu-id="7fa50-242">Bei Schaltflächen auf der rechten Bildschirmseite muss der Benutzer seinen Daumen in eine weniger bequeme Position nach innen bewegen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-242">Buttons on the right-side of the screen require the user to pull their thumb inward into a less-comfortable position.</span></span>

### <a name="create-a-dialog"></a><span data-ttu-id="7fa50-243">Erstellen eines Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="7fa50-243">Create a dialog</span></span>
<span data-ttu-id="7fa50-244">Um ein Dialogfeld zu erstellen, verwenden Sie die [ContentDialog-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx).</span><span class="sxs-lookup"><span data-stu-id="7fa50-244">To create a dialog, you use the [ContentDialog class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx).</span></span> <span data-ttu-id="7fa50-245">Sie können ein Dialogfeld im Code oder Markup erstellen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-245">You can create a dialog in code or markup.</span></span> <span data-ttu-id="7fa50-246">Obwohl es in der Regel leichter ist, UI-Elemente in XAML zu definieren, ist es bei einem einfachen Dialogfeld unkomplizierter, Code zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-246">Although its usually easier to define UI elements in XAML, in the case of a simple dialog, it's actually easier to just use code.</span></span> <span data-ttu-id="7fa50-247">In diesem Beispiel wird ein Dialogfeld erstellt, um dem Benutzer mitzuteilen, dass keine WLAN-Verbindung vorhanden ist. Für die Anzeige wird die Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) verwendet.</span><span class="sxs-lookup"><span data-stu-id="7fa50-247">This example creates a dialog to notify the user that there's no WiFi connection, and then uses the [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) method to display it.</span></span>

```csharp
private async void DisplayNoWifiDialog()
{
    ContentDialog noWifiDialog = new ContentDialog
    {
        Title = "No wifi connection",
        Content = "Check your connection and try again.",
        CloseButtonText = "Ok"
    };

    ContentDialogResult result = await noWifiDialog.ShowAsync();
}
```

<span data-ttu-id="7fa50-248">Wenn der Benutzer auf eine Dialogfeldschaltfläche klickt, gibt die Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) ein [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx) zurück, damit Sie wissen, auf welche Schaltfläche der Benutzer klickt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-248">When the user clicks a dialog button, the [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) method returns a [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx) to let you know which button the user clicks.</span></span>

<span data-ttu-id="7fa50-249">Das Dialogfeld in diesem Beispiel stellt eine Frage und verwendet das zurückgegebene [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx), um die Antwort des Benutzers zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="7fa50-249">The dialog in this example asks a question and uses the returned [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx) to determine the user's response.</span></span>

```csharp
private async void DisplayDeleteFileDialog()
{
    ContentDialog deleteFileDialog = new ContentDialog
    {
        Title = "Delete file permanently?",
        Content = "If you delete this file, you won't be able to recover it. Do you want to delete it?",
        PrimaryButtonText = "Delete",
        CloseButtonText = "Cancel"
    };

    ContentDialogResult result = await deleteFileDialog.ShowAsync();

    // Delete the file if the user clicked the primary button.
    /// Otherwise, do nothing.
    if (result == ContentDialogResult.Primary)
    {
        // Delete the file.
    }
    else
    {
        // The user clicked the CLoseButton, pressed ESC, Gamepad B, or the system back button.
        // Do nothing.
    }
}
```

## <a name="flyouts"></a><span data-ttu-id="7fa50-250">Flyouts</span><span class="sxs-lookup"><span data-stu-id="7fa50-250">Flyouts</span></span>
###  <a name="create-a-flyout"></a><span data-ttu-id="7fa50-251">Erstellen eines Flyouts</span><span class="sxs-lookup"><span data-stu-id="7fa50-251">Create a flyout</span></span>

<span data-ttu-id="7fa50-252">Ein Flyout ist ein einfach ausblendbarer Container, der beliebige UI als Inhalt anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="7fa50-252">A flyout is a light dismiss container that can show arbitrary UI as its content.</span></span> <span data-ttu-id="7fa50-253">Flyouts können andere Flyouts oder Kontextmenüs enthalten, um eine geschachtelte Umgebung zu kreieren.</span><span class="sxs-lookup"><span data-stu-id="7fa50-253">Flyouts can contain other flyouts or context menus to create a nested experience.</span></span>

![Kontextmenü geschachtelt in einem Flyout](images/flyout-nested.png)

<span data-ttu-id="7fa50-255">Flyouts sind an bestimmte Steuerelemente angefügt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-255">Flyouts are attached to specific controls.</span></span> <span data-ttu-id="7fa50-256">Sie können mit der [Placement](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.placement.aspx)-Eigenschaft angeben, wo das Flyout angezeigt werden soll: oben, links, unten, rechts oder als Vollbild.</span><span class="sxs-lookup"><span data-stu-id="7fa50-256">You can use the [Placement](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.placement.aspx) property to specify where a flyout appears: Top, Left, Bottom, Right, or Full.</span></span> <span data-ttu-id="7fa50-257">Wenn Sie den [vollständigen Platzierungsmodus](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutplacementmode.aspx) auswählen, streckt die App das Flyout und zentriert es innerhalb des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="7fa50-257">If you select the [Full placement mode](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutplacementmode.aspx), the app stretches the flyout and centers it inside the app window.</span></span> <span data-ttu-id="7fa50-258">Einige Steuerelemente wie z.B. [Schaltflächen](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx), verfügen über eine [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx)-Eigenschaft, mit der Sie ein Flyout oder [Kontextmenü](menus.md) zuordnen können.</span><span class="sxs-lookup"><span data-stu-id="7fa50-258">Some controls, such as [Button](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx), provide a [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx) property that you can use to associate a flyout or [context menu](menus.md).</span></span>

<span data-ttu-id="7fa50-259">In diesem Beispiel wird ein einfaches Flyout erstellt, das Text anzeigt, wenn die Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="7fa50-259">This example creates a simple flyout that displays some text when the button is pressed.</span></span>
````xaml
<Button Content="Click me">
  <Button.Flyout>
     <Flyout>
        <TextBlock Text="This is a flyout!"/>
     </Flyout>
  </Button.Flyout>
</Button>
````

<span data-ttu-id="7fa50-260">Wenn das Steuerelement nicht über eine Flyout-Eigenschaft verfügt, können Sie stattdessen die angefügte Eigenschaft [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) verwenden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-260">If the control doesn't have a flyout property, you can use the [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) attached property instead.</span></span> <span data-ttu-id="7fa50-261">In diesem Fall müssen Sie zudem die [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout)-Methode aufrufen, um das Flyout anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-261">When you do this, you also need to call the [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout) method to show the flyout.</span></span>

<span data-ttu-id="7fa50-262">In diesem Beispiel wird einem Bild ein einfaches Flyout hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-262">This example adds a simple flyout to an image.</span></span> <span data-ttu-id="7fa50-263">Wenn der Benutzer auf das Bild tippt, zeigt die App das Flyout an.</span><span class="sxs-lookup"><span data-stu-id="7fa50-263">When the user taps the image, the app shows the flyout.</span></span>

````xaml
<Image Source="Assets/cliff.jpg" Width="50" Height="50"
  Margin="10" Tapped="Image_Tapped">
  <FlyoutBase.AttachedFlyout>
    <Flyout>
      <TextBlock Text="This is some text in a flyout."  />
    </Flyout>        
  </FlyoutBase.AttachedFlyout>
</Image>
````

````csharp
private void Image_Tapped(object sender, TappedRoutedEventArgs e)
{
    FlyoutBase.ShowAttachedFlyout((FrameworkElement)sender);
}
````

<span data-ttu-id="7fa50-264">In den vorherigen Beispielen wurden die Flyouts inline definiert.</span><span class="sxs-lookup"><span data-stu-id="7fa50-264">The previous examples defined their flyouts inline.</span></span> <span data-ttu-id="7fa50-265">Sie können ein Flyout auch als statische Ressource definieren und sie dann mit mehreren Elementen verwenden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-265">You can also define a flyout as a static resource and then use it with multiple elements.</span></span> <span data-ttu-id="7fa50-266">In diesem Beispiel wird ein komplizierteres Flyout erstellt, mit dem eine größere Version eines Bilds angezeigt wird, wenn auf die Miniaturansicht getippt wird.</span><span class="sxs-lookup"><span data-stu-id="7fa50-266">This example creates a more complicated flyout that displays a larger version of an image when its thumbnail is tapped.</span></span>

````xaml
<!-- Declare the shared flyout as a resource. -->
<Page.Resources>
    <Flyout x:Key="ImagePreviewFlyout" Placement="Right">
        <!-- The flyout's DataContext must be the Image Source
             of the image the flyout is attached to. -->
        <Image Source="{Binding Path=Source}"
            MaxHeight="400" MaxWidth="400" Stretch="Uniform"/>
    </Flyout>
</Page.Resources>
````

````xaml
<!-- Assign the flyout to each element that shares it. -->
<StackPanel>
    <Image Source="Assets/cliff.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
    <Image Source="Assets/grapes.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
    <Image Source="Assets/rainier.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
</StackPanel>
````

````csharp
private void Image_Tapped(object sender, TappedRoutedEventArgs e)
{
    FlyoutBase.ShowAttachedFlyout((FrameworkElement)sender);  
}
````

### <a name="style-a-flyout"></a><span data-ttu-id="7fa50-267">Gestalten eines Flyouts</span><span class="sxs-lookup"><span data-stu-id="7fa50-267">Style a flyout</span></span>
<span data-ttu-id="7fa50-268">Um ein Flyout zu formatieren, ändern Sie den [FlyoutPresenterStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flyout.flyoutpresenterstyle.aspx).</span><span class="sxs-lookup"><span data-stu-id="7fa50-268">To style a Flyout, modify its [FlyoutPresenterStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flyout.flyoutpresenterstyle.aspx).</span></span> <span data-ttu-id="7fa50-269">In diesem Beispiel wird ein Absatz mit Textumbruch dargestellt, was den Textblock für Bildschirmleseprogramme zugänglich gemacht.</span><span class="sxs-lookup"><span data-stu-id="7fa50-269">This example shows a paragraph of wrapping text and makes the text block accessible to a screen reader.</span></span>

![Zugängliches Flyout mit Textumbruch](images/flyout-wrapping-text.png)

````xaml
<Flyout>
  <Flyout.FlyoutPresenterStyle>
    <Style TargetType="FlyoutPresenter">
      <Setter Property="ScrollViewer.HorizontalScrollMode"
          Value="Disabled"/>
      <Setter Property="ScrollViewer.HorizontalScrollBarVisibility" Value="Disabled"/>
      <Setter Property="IsTabStop" Value="True"/>
      <Setter Property="TabNavigation" Value="Cycle"/>
    </Style>
  </Flyout.FlyoutPresenterStyle>
  <TextBlock Style="{StaticResource BodyTextBlockStyle}" Text="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."/>
</Flyout>
````

#### <a name="styling-flyouts-for-10-foot-experience"></a><span data-ttu-id="7fa50-271">Formatieren von Flyouts für die 10 Fuß-Umgebung</span><span class="sxs-lookup"><span data-stu-id="7fa50-271">Styling flyouts for 10-foot experience</span></span>

<span data-ttu-id="7fa50-272">Einfach ausblendbare Steuerelemente wie Flyouts erhalten den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-272">Light dismiss controls like flyout trap keyboard and gamepad focus inside their transient UI until dismissed.</span></span> <span data-ttu-id="7fa50-273">Um dieses Verhalten optisch zu kennzeichnen, werden diese einfach ausblendbaren Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei der Kontrast und die Helligkeit bzw. Sichtbarkeit der umgebenden Benutzeroberfläche reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="7fa50-273">To provide a visual cue for this behavior, light dismiss controls on Xbox draw an overlay that dims the contrast and visibility of out of scope UI.</span></span> <span data-ttu-id="7fa50-274">Dieses Verhalten kann mit der Eigenschaft [`LightDismissOverlayMode`](https://msdn.microsoft.com/ library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) geändert werden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-274">This behavior can be modified with the [`LightDismissOverlayMode`](https://msdn.microsoft.com/ library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) property.</span></span> <span data-ttu-id="7fa50-275">Standardmäßig erhalten Flyouts auf der Xbox (jedoch nicht auf anderen Gerätefamilien) die einfach ausblendbare Überlagerung. Apps können jedoch durchsetzen, dass die Überlagerung stets **An** oder stets **Aus** ist.</span><span class="sxs-lookup"><span data-stu-id="7fa50-275">By default, flyouts will draw the light dismiss overlay on Xbox but not other device families, but apps can choose to force the overlay to be always **On** or always **Off**.</span></span>

![Flyout mit Abblend-Überlagerung](images/flyout-smoke.png)

```xaml
<MenuFlyout LightDismissOverlayMode="On">
```

### <a name="light-dismiss-behavior"></a><span data-ttu-id="7fa50-277">Verhalten für einfaches Ausblenden</span><span class="sxs-lookup"><span data-stu-id="7fa50-277">Light dismiss behavior</span></span>
<span data-ttu-id="7fa50-278">Flyouts können schnell mit einer einfachen Ausblend-Aktion geschlossen werden. Dazu zählen:</span><span class="sxs-lookup"><span data-stu-id="7fa50-278">Flyouts can be closed with a quick light dismiss action, including</span></span>
-    <span data-ttu-id="7fa50-279">Tippen außerhalb des Flyouts</span><span class="sxs-lookup"><span data-stu-id="7fa50-279">Tap outside the flyout</span></span>
-    <span data-ttu-id="7fa50-280">Drücken der ESC-Taste auf der Tastatur</span><span class="sxs-lookup"><span data-stu-id="7fa50-280">Press the Escape keyboard key</span></span>
-    <span data-ttu-id="7fa50-281">Drücken der Zurück-Taste des Systems (Hardware oder Software)</span><span class="sxs-lookup"><span data-stu-id="7fa50-281">Press the hardware or software system Back button</span></span>
-    <span data-ttu-id="7fa50-282">Drücken der B-Taste auf dem Gamepad</span><span class="sxs-lookup"><span data-stu-id="7fa50-282">Press the gamepad B button</span></span>

<span data-ttu-id="7fa50-283">Wird das Ausblenden durch Tippen vorgenommen, wird die Geste in der Regel absorbiert und nicht an die UI unterhalb weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="7fa50-283">When dismissing with a tap, this gesture is typically absorbed and not passed on to the UI underneath.</span></span> <span data-ttu-id="7fa50-284">Ist beispielsweise hinter einem geöffneten Flyout eine Schaltfläche sichtbar, wird durch einfaches Antippen durch den Benutzer das Flyout ausgeblendet, ohne jedoch diese Schaltfläche zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7fa50-284">For example, if there’s a button visible behind an open flyout, the user’s first tap dismisses the flyout but does not activate this button.</span></span> <span data-ttu-id="7fa50-285">Um die Schaltfläche zu drücken, ist ein weiteres Antippen nötig.</span><span class="sxs-lookup"><span data-stu-id="7fa50-285">Pressing the button requires a second tap.</span></span>

<span data-ttu-id="7fa50-286">Sie können dieses Verhalten ändern, indem Sie die Schaltfläche als Pass-Through-Eingabeelement für das Flyout gestalten.</span><span class="sxs-lookup"><span data-stu-id="7fa50-286">You can change this behavior by designating the button as an input pass-through element for the flyout.</span></span> <span data-ttu-id="7fa50-287">Das Flyout wird wie oben beschriebenen durch die einfache Ausblend-Aktion geschlossen, gibt den Antipp-Vorgang aber gleichzeitig an das entsprechende `OverlayInputPassThroughElement` weiter.</span><span class="sxs-lookup"><span data-stu-id="7fa50-287">The flyout will close as a result of the light dismiss actions described above and will also pass the tap event to its designated `OverlayInputPassThroughElement`.</span></span> <span data-ttu-id="7fa50-288">Erwägen Sie, dieses Verhalten zu übernehmen, um Interaktionen des Benutzers bei ähnlich funktionierenden Elementen zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="7fa50-288">Consider adopting this behavior to speed up user interactions on functionally similar items.</span></span> <span data-ttu-id="7fa50-289">Wenn Ihre App eine Sammlung von Favoriten beinhaltet und jedes Element der Sammlung ein angefügtes Flyout enthält, kann man davon auszugehen, dass die Benutzer mehrere Flyouts in schneller Abfolge abarbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="7fa50-289">If your app has a favorites collection and each item in the collection includes an attached flyout, it's reasonable to expect that users may want to interact with multiple flyouts in rapid succession.</span></span>

[!NOTE] <span data-ttu-id="7fa50-290">Achten Sie darauf, kein Überlagerungseingabeelement mit Pass-Through festzulegen, da dies in einer destruktiven Aktion resultiert.</span><span class="sxs-lookup"><span data-stu-id="7fa50-290">Be careful not to designate an overlay input pass-through element which results in a destructive action.</span></span> <span data-ttu-id="7fa50-291">Die Benutzer sind an diskrete, einfach ausblendbare Aktionen gewöhnt, die die Primär-UI nicht aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7fa50-291">Users have become habituated to discreet light dismiss actions which do not activate primary UI.</span></span> <span data-ttu-id="7fa50-292">Schließen, Löschen oder ähnlich destruktive Schaltflächen sollten nicht über einfach ausblendbare Elemente aktiviert werden, um unerwartetes und störendes Verhalten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="7fa50-292">Close, Delete or similarly destructive buttons should not activate on light dismiss to avoid unexpected and disruptive behavior.</span></span>

<span data-ttu-id="7fa50-293">Im folgenden Beispiel werden alle drei Schaltflächen in der Favoritenleiste durch einfaches Antippen aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7fa50-293">In the following example, all three buttons inside FavoritesBar will be activated on the first tap.</span></span>

````xaml
<Page>
    <Page.Resources>
        <Flyout x:Name="TravelFlyout" x:Key="TravelFlyout"
                OverlayInputPassThroughElement="{x:Bind FavoritesBar}">
            <StackPanel>
                <HyperlinkButton Content="Washington Trails Association"/>
                <HyperlinkButton Content="Washington Cascades - Go Northwest! A Travel Guide"/>  
            </StackPanel>
        </Flyout>
    </Page.Resources>

    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="FavoritesBar" Orientation="Horizontal">
            <HyperlinkButton x:Name="PageLinkBtn">Bing</HyperlinkButton>  
            <Button x:Name="Folder1" Content="Travel" Flyout="{StaticResource TravelFlyout}"/>
            <Button x:Name="Folder2" Content="Entertainment" Click="Folder2_Click"/>
        </StackPanel>
        <ScrollViewer Grid.Row="1">
            <WebView x:Name="WebContent"/>
        </ScrollViewer>
    </Grid>
</Page>
````
````csharp
private void Folder2_Click(object sender, RoutedEventArgs e)
{
     Flyout flyout = new Flyout();
     flyout.OverlayInputPassThroughElement = FavoritesBar;
     ...
     flyout.ShowAt(sender as FrameworkElement);
{
````

## <a name="get-the-samples"></a><span data-ttu-id="7fa50-294">Beispiele herunterladen</span><span class="sxs-lookup"><span data-stu-id="7fa50-294">Get the samples</span></span>
*   [<span data-ttu-id="7fa50-295">XAML-UI-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="7fa50-295">XAML UI basics</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)<br/>
    <span data-ttu-id="7fa50-296">Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7fa50-296">See all of the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="7fa50-297">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="7fa50-297">Related articles</span></span>
- [<span data-ttu-id="7fa50-298">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="7fa50-298">Tooltips</span></span>](tooltips.md)
- [<span data-ttu-id="7fa50-299">Menüs und Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="7fa50-299">Menus and context menu</span></span>](menus.md)
- [<span data-ttu-id="7fa50-300">Flyout-Klasse</span><span class="sxs-lookup"><span data-stu-id="7fa50-300">Flyout class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279496)
- [<span data-ttu-id="7fa50-301">ContentDialog-Klasse</span><span class="sxs-lookup"><span data-stu-id="7fa50-301">ContentDialog class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx)