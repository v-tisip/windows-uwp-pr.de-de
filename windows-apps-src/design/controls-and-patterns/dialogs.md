---
author: mijacobs
Description: Dialogs and flyouts display transient UI elements that appear when the user requests them or when something happens that requires notification or approval.
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
ms.localizationpriority: medium
ms.openlocfilehash: 7b263fda1de798473f581e2191d3fa01385060e6
ms.sourcegitcommit: e4627686138ec8c885696c4c511f2f05195cf8ff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "1893845"
---
# <a name="dialogs-and-flyouts"></a><span data-ttu-id="daa6a-103">Dialogfelder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="daa6a-103">Dialogs and flyouts</span></span>



<span data-ttu-id="daa6a-104">Dialogfelder und Flyouts sind vorübergehende UI-Elemente, die angezeigt werden, wenn Ereignisse Benachrichtigungen, Genehmigungen oder zusätzliche Informationen vom Benutzer erfordern.</span><span class="sxs-lookup"><span data-stu-id="daa6a-104">Dialogs and flyouts are transient UI elements that appear when something happens that requires notification, approval, or additional information from the user.</span></span>

> <span data-ttu-id="daa6a-105">**Wichtige APIs**: [ContentDialog-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog), [Flyout-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout)</span><span class="sxs-lookup"><span data-stu-id="daa6a-105">**Important APIs**: [ContentDialog class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog), [Flyout class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout)</span></span>


<span data-ttu-id="daa6a-106">:::row::: :::column::: **Dialogfelder**</span><span class="sxs-lookup"><span data-stu-id="daa6a-106">:::row::: :::column::: **Dialogs**</span></span>
        
        ![Example of a dialog](images/dialogs/dialog_RS2_delete_file.png)

        Dialogs are modal UI overlays that provide contextual app information. Dialogs block interactions with the app window until being explicitly dismissed. They often request some kind of action from the user.
    :::column-end:::
    :::column::: 
        **Flyouts**

        ![Example of a flyout](images/flyout-example2.png)

        A flyout is a lightweight contextual popup that displays UI related to what the user is doing. It includes placement and sizing logic, and can be used to reveal a secondary control or show more detail about an item.

        Unlike a dialog, a flyout can be quickly dismissed by tapping or clicking somewhere outside the flyout, pressing the Escape key or Back button, resizing the app window, or changing the device's orientation.
    :::column-end:::
<span data-ttu-id="daa6a-107">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="daa6a-107">:::row-end:::</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="daa6a-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="daa6a-108">Is this the right control?</span></span>

* <span data-ttu-id="daa6a-109">Verwenden Sie Dialogfelder und Flyouts, um Benutzern wichtige Informationen mitzuteilen oder deren Bestätigung bzw. zusätzliche Informationen anzufordern, bevor eine Aktion abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="daa6a-109">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>
* <span data-ttu-id="daa6a-110">Verwenden Sie Flyouts nicht anstelle von [QuickInfos](tooltips.md) oder [Kontextmenüs](menus.md).</span><span class="sxs-lookup"><span data-stu-id="daa6a-110">Don't use a flyout instead of [tooltip](tooltips.md) or [context menu](menus.md).</span></span> <span data-ttu-id="daa6a-111">Verwenden Sie QuickInfos, um kurze Beschreibungen anzuzeigen, die nach einer festgelegten Zeit ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-111">Use a tooltip to show a short description that hides after a specified time.</span></span> <span data-ttu-id="daa6a-112">Verwenden Sie ein Kontextmenü für kontextbezogene Aktionen im Zusammenhang mit UI-Elementen (beispielsweise Kopieren und Einfügen).</span><span class="sxs-lookup"><span data-stu-id="daa6a-112">Use a context menu for contextual actions related to a UI element, such as copy and paste.</span></span>  


<span data-ttu-id="daa6a-113">Dialogfelder und Flyouts stellen sicher, dass den Benutzern wichtige Informationen bekannt sind, stellen jedoch auch eine Unterbrechung dar.</span><span class="sxs-lookup"><span data-stu-id="daa6a-113">Dialogs and flyouts make sure that users are aware of important information, but they also disrupt the user experience.</span></span> <span data-ttu-id="daa6a-114">Da Dialogfelder modal (blockierend) sind, werden die Benutzer unterbrochen und daran gehindert, andere Schritte durchzuführen, bis eine Interaktion mit dem Dialogfeld erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="daa6a-114">Because dialogs are modal (blocking), they interrupt users, preventing them from doing anything else until they interact with the dialog.</span></span> <span data-ttu-id="daa6a-115">Flyouts sind weniger störend. Zu viele Flyouts können jedoch als störend empfunden werden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-115">Flyouts provide a less jarring experience, but displaying too many flyouts can be distracting.</span></span>

<span data-ttu-id="daa6a-116">Berücksichtigen Sie die Bedeutung der zu vermittelnden Informationen: Sind sie wichtig genug, um den Benutzer zu unterbrechen?</span><span class="sxs-lookup"><span data-stu-id="daa6a-116">Consider the importance of the information you want to share: is it important enough to interrupt the user?</span></span> <span data-ttu-id="daa6a-117">Berücksichtigen Sie zudem, wie häufig die Informationen angezeigt werden müssen. Wenn ein Dialogfeld oder eine Benachrichtigung alle paar Minuten angezeigt wird, sollten Sie diese Informationen stattdessen in die primäre UI einbinden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-117">Also consider how frequently the information needs to be shown; if you're showing a dialog or notification every few minutes, you might want to allocate space for this info in the primary UI instead.</span></span> <span data-ttu-id="daa6a-118">So können Sie z.B. in einem Chat-Client anstatt eines Flyouts, der jedes Mal angezeigt wird, wenn sich ein Freund anmeldet, eine Liste der Freunde anzeigen, die derzeit online sind, und diejenigen Freunde hervorheben, die sich gerade anmelden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-118">For example, in a chat client, rather than showing a flyout every time a friend logs in, you might display a list of friends who are online at the moment and highlight friends as they log on.</span></span>

<span data-ttu-id="daa6a-119">Dialogfelder werden häufig zum Bestätigen einer Aktion vor deren Ausführung verwendet (z.B. vor dem Löschen einer Datei).</span><span class="sxs-lookup"><span data-stu-id="daa6a-119">Dialogs are frequently used to confirm an action (such as deleting a file) before executing it.</span></span> <span data-ttu-id="daa6a-120">Wenn Sie davon ausgehen, dass die Benutzer häufig eine bestimmte Aktion ausführen, sollten Sie eine Möglichkeit bereitstellen, versehentliche Aktionen rückgängig zu machen, anstatt jedes Mal die Bestätigung der Aktion zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-120">If you expect the user to perform a particular action frequently, consider providing a way for the user to undo the action if it was a mistake, rather than forcing users to confirm the action every time.</span></span>

## <a name="examples"></a><span data-ttu-id="daa6a-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="daa6a-121">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="daa6a-122">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="daa6a-122">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="daa6a-123">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> oder <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-123">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> or <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="daa6a-124">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="daa6a-124">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="daa6a-125">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="daa6a-125">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="dialogs-vs-flyouts"></a><span data-ttu-id="daa6a-126">Dialogfelder im Vergleich zu Flyouts</span><span class="sxs-lookup"><span data-stu-id="daa6a-126">Dialogs vs. flyouts</span></span>

<span data-ttu-id="daa6a-127">Wenn ein Dialogfeld oder Flyout eingesetzt werden soll, müssen Sie sich für eine der beiden Optionen entscheiden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-127">Once you've determined that you want to use a dialog or flyout, you need to choose which one to use.</span></span>

<span data-ttu-id="daa6a-128">Angesichts der Tatsache, dass Dialogfelder im Gegensatz zu Flyouts Interaktionen blockieren, sollten Dialogfelder auf Situationen beschränkt bleiben, in denen der Benutzer unterbrochen werden soll, um sich auf eine bestimmte Information oder die Beantwortung einer Frage zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="daa6a-128">Given that dialogs block interactions and flyouts do not, dialogs should be reserved for situations where you want the user to drop everything to focus on a specific bit of information or answer a question.</span></span> <span data-ttu-id="daa6a-129">Flyouts hingegen können verwendet werden, wenn Sie auf etwas aufmerksam machen möchten, das der Benutzer jedoch ignorieren kann.</span><span class="sxs-lookup"><span data-stu-id="daa6a-129">Flyouts, on the other hand, can be used when you want to call attention to something, but it's ok if the user wants to ignore it.</span></span>

<span data-ttu-id="daa6a-130">:::row::: :::column:::</span><span class="sxs-lookup"><span data-stu-id="daa6a-130">:::row::: :::column:::</span></span>
   <p><b><span data-ttu-id="daa6a-131">Fälle, in denen ein Dialogfeld verwendet werden sollte:</span><span class="sxs-lookup"><span data-stu-id="daa6a-131">Use a dialog for...</span></span></b> <br/>
<ul>
<li><span data-ttu-id="daa6a-132">Für wichtige Informationen, die der Benutzer vor dem Fortsetzen lesen und bestätigen <b>muss</b>.</span><span class="sxs-lookup"><span data-stu-id="daa6a-132">Expressing important information that the user <b>must</b> read and acknowledge before proceeding.</span></span> <span data-ttu-id="daa6a-133">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="daa6a-133">Examples include:</span></span>
<ul>
  <li><span data-ttu-id="daa6a-134">Die Sicherheit des Benutzers ist möglicherweise gefährdet.</span><span class="sxs-lookup"><span data-stu-id="daa6a-134">When the user's security might be compromised</span></span></li>
  <li><span data-ttu-id="daa6a-135">Der Benutzer möchte eine wertvolle Ressource endgültig ändern.</span><span class="sxs-lookup"><span data-stu-id="daa6a-135">When the user is about to permanently alter a valuable asset</span></span></li>
  <li><span data-ttu-id="daa6a-136">Der Benutzer möchte eine wertvolle Ressource löschen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-136">When the user is about to delete a valuable asset</span></span></li>
  <li><span data-ttu-id="daa6a-137">Bestätigen eines In-App-Einkaufs</span><span class="sxs-lookup"><span data-stu-id="daa6a-137">To confirm an in-app purchase</span></span></li>
</ul>

</li>
<li><span data-ttu-id="daa6a-138">Fehlermeldungen, die sich auf den Gesamtkontext der App beziehen, z. B. Verbindungsfehler.</span><span class="sxs-lookup"><span data-stu-id="daa6a-138">Error messages that apply to the overall app context, such as a connectivity error.</span></span></li>
<li><span data-ttu-id="daa6a-139">Fragen, wenn dem Benutzer eine blockierende Frage gestellt werden muss, z. B. wenn die App nicht im Auftrag des Benutzers eine Auswahl treffen kann.</span><span class="sxs-lookup"><span data-stu-id="daa6a-139">Questions, when the app needs to ask the user a blocking question, such as when the app can't choose on the user's behalf.</span></span> <span data-ttu-id="daa6a-140">Eine blockierende Frage kann nicht ignoriert oder verschoben werden und sollte dem Benutzer klar definierte Auswahlmöglichkeiten bieten.</span><span class="sxs-lookup"><span data-stu-id="daa6a-140">A blocking question can't be ignored or postponed, and should offer the user well-defined choices.</span></span></li>
</ul>
</p>
<span data-ttu-id="daa6a-141">:::column-end::: :::column:::</span><span class="sxs-lookup"><span data-stu-id="daa6a-141">:::column-end::: :::column:::</span></span> <p><b><span data-ttu-id="daa6a-142">Fälle, in denen ein Flyout verwendet werden sollte:</span><span class="sxs-lookup"><span data-stu-id="daa6a-142">Use a flyout for...</span></span></b> <br/>
<ul>
<li><span data-ttu-id="daa6a-143">Erfassen zusätzlicher Informationen, die erforderlich sind, bevor eine Aktion abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="daa6a-143">Collecting additional information needed before an action can be completed.</span></span></li>
<li><span data-ttu-id="daa6a-144">Anzeigen von Informationen, die nur vorübergehend relevant sind.</span><span class="sxs-lookup"><span data-stu-id="daa6a-144">Displaying info that's only relevant some of the time.</span></span> <span data-ttu-id="daa6a-145">So können Sie z.B. in einer Fotogalerie-App ein Flyout einsetzen, damit eine große Version des Bilds angezeigt wird, wenn der Benutzer auf eine Miniaturansicht klickt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-145">For example, in a photo gallery app, when the user clicks an image thumbnail, you might use a flyout to display a large version of the image.</span></span></li>
<li><span data-ttu-id="daa6a-146">Anzeigen weiterer Informationen, z. B. von Details oder ausführlicheren Beschreibungen eines Elements auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="daa6a-146">Displaying more information, such as details or longer descriptions of an item on the page.</span></span></li>
</ul></p>
<span data-ttu-id="daa6a-147">:::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="daa6a-147">:::column-end::: :::row-end:::</span></span>



## <a name="dialogs"></a><span data-ttu-id="daa6a-148">Dialogfelder</span><span class="sxs-lookup"><span data-stu-id="daa6a-148">Dialogs</span></span>
### <a name="general-guidelines"></a><span data-ttu-id="daa6a-149">Allgemeine Richtlinien</span><span class="sxs-lookup"><span data-stu-id="daa6a-149">General guidelines</span></span>

-   <span data-ttu-id="daa6a-150">Sie sollten das Problem oder das Ziel des Benutzers in der ersten Zeile des Dialogfeldtexts deutlich benennen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-150">Clearly identify the issue or the user's objective in the first line of the dialog's text.</span></span>
-   <span data-ttu-id="daa6a-151">Der Dialogfeldtitel ist die Hauptanweisung und optional.</span><span class="sxs-lookup"><span data-stu-id="daa6a-151">The dialog title is the main instruction and is optional.</span></span>
    -   <span data-ttu-id="daa6a-152">Verwenden Sie einen kurzen Titel, um dem Benutzer die erforderlichen Aktionen im Dialogfeld zu erklären.</span><span class="sxs-lookup"><span data-stu-id="daa6a-152">Use a short title to explain what people need to do with the dialog.</span></span>
    -   <span data-ttu-id="daa6a-153">Wenn Sie mit dem Dialogfeld eine einfache Meldung, einen Fehler oder eine Frage anzeigen möchten, können Sie den Titel optional auslassen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-153">If you're using the dialog to deliver a simple message, error or question, you can optionally omit the title.</span></span> <span data-ttu-id="daa6a-154">Vermitteln Sie dann im Inhalt die wichtigsten Informationen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-154">Rely on the content text to deliver that core information.</span></span>
    -   <span data-ttu-id="daa6a-155">Stellen Sie sicher, dass sich der Titel direkt auf die Auswahlmöglichkeiten der Schaltflächen bezieht.</span><span class="sxs-lookup"><span data-stu-id="daa6a-155">Make sure that the title relates directly to the button choices.</span></span>
-   <span data-ttu-id="daa6a-156">Der Inhalt des Dialogfelds enthält den beschreibenden Text und ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="daa6a-156">The dialog content contains the descriptive text and is required.</span></span>
    -   <span data-ttu-id="daa6a-157">Stellen Sie die Meldung, den Fehler oder die blockierende Frage so einfach wie möglich dar.</span><span class="sxs-lookup"><span data-stu-id="daa6a-157">Present the message, error, or blocking question as simply as possible.</span></span>
    -   <span data-ttu-id="daa6a-158">Stellen Sie bei Verwendung eines Dialogfeldtitels mithilfe des Inhaltsbereichs weitere Details bereit, oder definieren Sie Terminologie.</span><span class="sxs-lookup"><span data-stu-id="daa6a-158">If a dialog title is used, use the content area to provide more detail or define terminology.</span></span> <span data-ttu-id="daa6a-159">Wiederholen Sie nicht den Titel mit anderen Worten.</span><span class="sxs-lookup"><span data-stu-id="daa6a-159">Don't repeat the title with slightly different wording.</span></span>
-   <span data-ttu-id="daa6a-160">Mindestens eine Dialogfeldschaltfläche muss angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-160">At least one dialog button must appear.</span></span>
    -   <span data-ttu-id="daa6a-161">Stellen Sie sicher, dass Ihr Dialogfeld mindestens eine Schaltfläche aufweist, die eine sichere, nicht-destruktive Aktion wie „Alles klar!“, „Schließen“ oder „Abbrechen“ auslöst.</span><span class="sxs-lookup"><span data-stu-id="daa6a-161">Ensure that your dialog has at least one button corresponding to a safe, nondestructive action like "Got it!", "Close", or "Cancel".</span></span> <span data-ttu-id="daa6a-162">Verwenden Sie die CloseButton-API, um diese Schaltfläche hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-162">Use the CloseButton API to add this button.</span></span>
    -   <span data-ttu-id="daa6a-163">Verwenden Sie für den Schaltflächentext konkrete Antworten auf die Hauptanweisung oder den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-163">Use specific responses to the main instruction or content as button text.</span></span> <span data-ttu-id="daa6a-164">Beispiel: „Möchten Sie AppName den Zugriff auf Ihren Standort erlauben?“, gefolgt von den Schaltflächen „Zulassen“ und „Blockieren“.</span><span class="sxs-lookup"><span data-stu-id="daa6a-164">An example is, "Do you want to allow AppName to access your location?", followed by "Allow" and "Block" buttons.</span></span> <span data-ttu-id="daa6a-165">Konkrete Antworten erleichtern das Verständnis und ermöglichen somit eine schnelle Entscheidungsfindung.</span><span class="sxs-lookup"><span data-stu-id="daa6a-165">Specific responses can be understood more quickly, resulting in efficient decision making.</span></span>
    - <span data-ttu-id="daa6a-166">Stellen Sie sicher, dass der Text der Aktionsschaltflächen kurz ist.</span><span class="sxs-lookup"><span data-stu-id="daa6a-166">Ensure that the text of the action buttons is concise.</span></span> <span data-ttu-id="daa6a-167">Kurze Anweisungen ermöglichen dem Benutzer, schnell und zuverlässig eine Entscheidung zu treffen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-167">Short strings enable the user to make a choice quickly and confidently.</span></span>
    - <span data-ttu-id="daa6a-168">Zusätzlich zur sicheren, nicht-destruktiven Aktion können Sie dem Benutzer optional ein oder zwei Aktionsschaltflächen anzeigen, die im Zusammenhang mit der Hauptanweisung stehen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-168">In addition to the safe, nondestructive action, you may optionally present the user with one or two action buttons related to the main instruction.</span></span> <span data-ttu-id="daa6a-169">Diese „bestätigenden“ Aktionsschaltflächen unterstreichen den Hauptgrund des Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="daa6a-169">These "do it" action buttons confirm the main point of the dialog.</span></span> <span data-ttu-id="daa6a-170">Verwenden Sie die PrimaryButton- und SecondaryButton-APIs, um diese „bestätigenden“ Aktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-170">Use the PrimaryButton and SecondaryButton APIs to add these "do it" actions.</span></span>
    - <span data-ttu-id="daa6a-171">Die „bestätigenden“ Aktionsschaltflächen sollten als die am weitesten links stehenden Schaltflächen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-171">The "do it" action button(s) should appears as the leftmost buttons.</span></span> <span data-ttu-id="daa6a-172">Die sichere, nicht-destruktive Aktion sollte als die am weitesten rechts stehende Schaltfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-172">The safe, nondestructive action should appear as the rightmost button.</span></span>
    - <span data-ttu-id="daa6a-173">Sie können optional eine der drei Schaltflächen als Standardschaltfläche des Dialogfelds festlegen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-173">You may optionally choose to differentiate one of the three buttons as the dialog's default button.</span></span> <span data-ttu-id="daa6a-174">Verwenden Sie die DefaultButton-API, um eine der Schaltflächen abzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-174">Use the DefaultButton API to differentiate one of the buttons.</span></span>  
-   <span data-ttu-id="daa6a-175">Verwenden Sie Dialogfelder nicht für kontextbezogene Fehler, die sich auf eine bestimmte Stelle auf der Seite beziehen, beispielsweise Validierungsfehler (wie in Kennwortfeldern). Verwenden Sie die Canvas der App selbst zum Anzeigen von Inlinefehlern.</span><span class="sxs-lookup"><span data-stu-id="daa6a-175">Don't use dialogs for errors that are contextual to a specific place on the page, such as validation errors (in password fields, for example), use the app's canvas itself to show inline errors.</span></span>
- <span data-ttu-id="daa6a-176">Verwenden Sie die [ContentDialog-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog), um Ihre Dialogfeldumgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-176">Use the [ContentDialog class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog) to build your dialog experience.</span></span> <span data-ttu-id="daa6a-177">Verwenden Sie nicht die veraltete MessageDialog-API.</span><span class="sxs-lookup"><span data-stu-id="daa6a-177">Don't use the deprecated MessageDialog API.</span></span>

### <a name="dialog-scenarios"></a><span data-ttu-id="daa6a-178">Dialogfeld-Szenarien</span><span class="sxs-lookup"><span data-stu-id="daa6a-178">Dialog scenarios</span></span>
<span data-ttu-id="daa6a-179">Da Dialogfelder Benutzerinteraktion blockieren, und Schaltflächen für die Benutzer das primäre Mittel sind, ein Dialogfeld zu schließen, sollten Sie sicherstellen, dass Ihr Dialogfeld mindestens eine „sichere“, nicht-destruktive Schaltfläche wie z.B. „Schließen“ oder „Alles klar!“ enthält.</span><span class="sxs-lookup"><span data-stu-id="daa6a-179">Because dialogs block user interaction, and because buttons are the primary mechanism for users to dismiss the dialog, ensure that your dialog contains at least one "safe" and nondestructive button such as "Close" or "Got it!".</span></span> **<span data-ttu-id="daa6a-180">Alle Dialogfelder sollten mindestens eine sichere Aktionsschaltfläche enthalten, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-180">All dialogs should contain at least one safe action button to close the dialog.</span></span>** <span data-ttu-id="daa6a-181">Dadurch wird sichergestellt, dass der Benutzer das Dialogfeld zuverlässig schließen kann, ohne eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-181">This ensures that the user can confidently close the dialog without performing an action.</span></span><br>![Dialogfeld mit einer Schaltfläche](images/dialogs/dialog_RS2_one_button.png)

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

<span data-ttu-id="daa6a-183">Wenn Dialogfelder dazu verwendet werden, eine blockierende Frage anzuzeigen, sollte Ihr Dialogfeld dem Benutzer Aktionsschaltflächen bieten, die im Zusammenhang mit der Frage stehen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-183">When dialogs are used to display a blocking question, your dialog should present the user with action buttons related to the question.</span></span> <span data-ttu-id="daa6a-184">Die „sichere“, nicht-destruktive Schaltfläche kann durch ein oder zwei „bestätigende“ Aktionsschaltflächen ergänzt werden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-184">The "safe" and nondestructive button may be accompanied by one or two "do it" action buttons.</span></span> <span data-ttu-id="daa6a-185">Wenn dem Benutzer mehrere Optionen angezeigt werden, stellen Sie sicher, dass die Schaltflächen für die „bestätigende“ und die sichere/„ablehnende“ Aktion den Bezug zur Frage eindeutig darstellen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-185">When presenting the user with multiple options, ensure that the buttons clearly explain the "do it" and safe/"don’t do it" actions related to the question proposed.</span></span>

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

<span data-ttu-id="daa6a-187">Dialogfelder mit drei Schaltflächen werden verwendet, wenn Sie dem Benutzer zwei „bestätigende“ und eine „ablehnende“ Aktion präsentierten möchten.</span><span class="sxs-lookup"><span data-stu-id="daa6a-187">Three button dialogs are used when you present the user with two "do it" actions and a "don’t do it" action.</span></span> <span data-ttu-id="daa6a-188">Dialogfelder mit drei Schaltflächen sollten sparsam verwendet werden und eine klare Unterscheidung zwischen der Sekundäraktion und der sicheren/ablehnenden Aktion enthalten.</span><span class="sxs-lookup"><span data-stu-id="daa6a-188">Three button dialogs should be used sparingly with clear distinctions between the secondary action and the safe/close action.</span></span>

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

### <a name="the-three-dialog-buttons"></a><span data-ttu-id="daa6a-190">Die drei Schaltflächen des Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="daa6a-190">The three dialog buttons</span></span>
<span data-ttu-id="daa6a-191">Der ContentDialog umfasst drei unterschiedliche Arten von Schaltflächen, die Sie zur Erstellung einer Dialogfeldumgebung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="daa6a-191">ContentDialog has three different types of buttons that you can use to build a dialog experience.</span></span>

- <span data-ttu-id="daa6a-192">**CloseButton** – erforderlich – Stellt die sichere, nicht-destruktive Aktion dar, die es dem Benutzer ermöglicht, das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-192">**CloseButton** - Required - Represents the safe, nondestructive action that enables the user to exit the dialog.</span></span> <span data-ttu-id="daa6a-193">Wird als die am weitesten rechts stehende Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-193">Appears as the rightmost button.</span></span>
- <span data-ttu-id="daa6a-194">**PrimaryButton** – optional – Stellt die erste „bestätigende“ Aktion dar.</span><span class="sxs-lookup"><span data-stu-id="daa6a-194">**PrimaryButton** - Optional - Represents the first "do it" action.</span></span> <span data-ttu-id="daa6a-195">Wird als die am weitesten links stehende Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-195">Appears as the leftmost button.</span></span>
- <span data-ttu-id="daa6a-196">**SecondaryButton** – optional – Stellt die zweite „bestätigende“ Aktion dar.</span><span class="sxs-lookup"><span data-stu-id="daa6a-196">**SecondaryButton** - Optional - Represents the second "do it" action.</span></span> <span data-ttu-id="daa6a-197">Wird als mittlere Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-197">Appears as the middle button.</span></span>

<span data-ttu-id="daa6a-198">Mithilfe der integrierten Schaltflächen kann das Dialogfeld optisch an andere Dialogfelder angepasst werden sowie die Position der Schaltflächen passend ausgerichtet werden. Stellen Sie sicher, dass die Schaltflächen entsprechend auf Tastaturbefehle reagieren und der Befehlsbereich sichtbar bleibt, auch wenn die Bildschirmtastatur aufgerufen ist.</span><span class="sxs-lookup"><span data-stu-id="daa6a-198">Using the built-in buttons will position the buttons appropriately, ensure that they correctly respond to keyboard events, ensure that the command area remains visible even when the on-screen keyboard is up, and will make the dialog look consistent with other dialogs.</span></span>

#### <a name="closebutton"></a><span data-ttu-id="daa6a-199">CloseButton</span><span class="sxs-lookup"><span data-stu-id="daa6a-199">CloseButton</span></span>
<span data-ttu-id="daa6a-200">Jedes Dialogfeld sollte eine sichere, nicht-destruktive Aktionsschaltfläche aufweisen, die dem Benutzer das zuverlässige Beenden des Dialogfelds ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="daa6a-200">Every dialog should contain a safe, nondestructive action button that enables the user to confidently exit the dialog.</span></span>

<span data-ttu-id="daa6a-201">Verwenden Sie die ContentDialog.CloseButton-API, um diese Schaltfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-201">Use the ContentDialog.CloseButton API to create this button.</span></span> <span data-ttu-id="daa6a-202">Dadurch schaffen Sie die jeweils richtige Benutzerumgebung für alle Eingabemöglichkeiten wie z.B. Maus, Tastatur, Fingereingabe und Gamepad.</span><span class="sxs-lookup"><span data-stu-id="daa6a-202">This allows you to create the right user experience for all inputs including mouse, keyboard, touch, and gamepad.</span></span> <span data-ttu-id="daa6a-203">Dies ist nötig, wenn:</span><span class="sxs-lookup"><span data-stu-id="daa6a-203">This experience will happen when:</span></span>
<ol>
    <li><span data-ttu-id="daa6a-204">Der Benutzer auf CloseButton klickt oder tippt</span><span class="sxs-lookup"><span data-stu-id="daa6a-204">The user clicks or taps on the CloseButton</span></span> </li>
    <li><span data-ttu-id="daa6a-205">Der Benutzer die Zurück-Taste des Systems betätigt</span><span class="sxs-lookup"><span data-stu-id="daa6a-205">The user presses the system back button</span></span> </li>
    <li><span data-ttu-id="daa6a-206">Der Benutzer auf der Tastatur die ESC-Taste betätigt</span><span class="sxs-lookup"><span data-stu-id="daa6a-206">The user presses the ESC button on the keyboard</span></span> </li>
    <li><span data-ttu-id="daa6a-207">Der Benutzer auf dem Gamepad die B-Taste betätigt</span><span class="sxs-lookup"><span data-stu-id="daa6a-207">The user presses Gamepad B</span></span> </li>
</ol>

<span data-ttu-id="daa6a-208">Wenn der Benutzer auf eine Dialogfeldschaltfläche klickt, gibt die Methode [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) ein [ContentDialogResult](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) zurück, damit Sie wissen, auf welche Schaltfläche der Benutzer klickt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-208">When the user clicks a dialog button, the [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method returns a [ContentDialogResult](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) to let you know which button the user clicks.</span></span> <span data-ttu-id="daa6a-209">Klicken auf CloseButton resultiert in ContentDialogResult.None.</span><span class="sxs-lookup"><span data-stu-id="daa6a-209">Pressing on the CloseButton returns ContentDialogResult.None.</span></span>

#### <a name="primarybutton-and-secondarybutton"></a><span data-ttu-id="daa6a-210">PrimaryButton und SecondaryButton</span><span class="sxs-lookup"><span data-stu-id="daa6a-210">PrimaryButton and SecondaryButton</span></span>
<span data-ttu-id="daa6a-211">Zusätzlich zu CloseButton können Sie dem Benutzer optional ein oder zwei Aktionsschaltflächen anbieten, die im Zusammenhang mit der Hauptanweisung stehen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-211">In addition to the CloseButton, you may optionally present the user with one or two action buttons related to the main instruction.</span></span>
<span data-ttu-id="daa6a-212">Nutzen Sie PrimaryButton für die erste „bestätigende“ Aktion und SecondaryButton für die zweite „bestätigende“ Aktion.</span><span class="sxs-lookup"><span data-stu-id="daa6a-212">Leverage PrimaryButton for the first "do it" action, and SecondaryButton for the second "do it" action.</span></span> <span data-ttu-id="daa6a-213">Bei Dialogfeldern mit drei Schaltflächen stellt PrimaryButton in der Regel eine eindeutig „bestätigende“ Aktion dar, während SecondaryButton in der Regel eine neutrale oder sekundäre, „bestätigende“ Aktion darstellt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-213">In three-button dialogs, the PrimaryButton generally represents the affirmative "do it" action, while the SecondaryButton generally represents a neutral or secondary "do it" action.</span></span>
<span data-ttu-id="daa6a-214">Beispielsweise kann eine App den Benutzer dazu auffordern, einen Dienst zu abonnieren.</span><span class="sxs-lookup"><span data-stu-id="daa6a-214">For example, an app may prompt the user to subscribe to a service.</span></span> <span data-ttu-id="daa6a-215">In diesem Fall ist PrimaryButton die eindeutig „bestätigende“ Aktion und enthält den Text „Abonnieren“, während SecondaryButton als neutrale, „bestätigende“ Aktion den Text „Testen“ aufweist.</span><span class="sxs-lookup"><span data-stu-id="daa6a-215">The PrimaryButton as the affirmative "do it" action would host the Subscribe text, while the SecondaryButton as the neutral "do it" action would host the Try it text.</span></span> <span data-ttu-id="daa6a-216">CloseButton ermöglicht dem Benutzer in diesem Fall, die Aktion ohne Interaktion abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-216">The CloseButton would allow the user to cancel without performing either action.</span></span>

<span data-ttu-id="daa6a-217">Klickt der Benutzer auf PrimaryButton, wird von der Methode [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) ContentDialogResult.Primary zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="daa6a-217">When the user clicks on the PrimaryButton, the [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method returns ContentDialogResult.Primary.</span></span>
<span data-ttu-id="daa6a-218">Klickt der Benutzer auf die SecondaryButton, wird von der Methode [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) ContentDialogResult.Primary zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="daa6a-218">When the user clicks on the SecondaryButton, the [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method returns ContentDialogResult.Secondary.</span></span>

![Dialogfeld mit drei Schaltflächen](images/dialogs/dialog_RS2_three_button.png)

#### <a name="defaultbutton"></a><span data-ttu-id="daa6a-220">DefaultButton</span><span class="sxs-lookup"><span data-stu-id="daa6a-220">DefaultButton</span></span>
<span data-ttu-id="daa6a-221">Sie können optional eine der drei Schaltflächen als Standardschaltfläche festlegen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-221">You may optionally choose to differentiate one of the three buttons as the default button.</span></span> <span data-ttu-id="daa6a-222">Das Festlegen einer Standardschaltfläche hat zur Folge, dass:</span><span class="sxs-lookup"><span data-stu-id="daa6a-222">Specifying the default button causes the following to happen:</span></span>
- <span data-ttu-id="daa6a-223">die Schaltfläche optisch als Akzentschaltfläche behandelt wird</span><span class="sxs-lookup"><span data-stu-id="daa6a-223">The button receives the Accent Button visual treatment</span></span>
- <span data-ttu-id="daa6a-224">die Schaltfläche automatisch auf die EINGABETASTE reagiert</span><span class="sxs-lookup"><span data-stu-id="daa6a-224">The button will respond to the ENTER key automatically</span></span>
    - <span data-ttu-id="daa6a-225">Drückt der Benutzer auf der Tastatur die EINGABETASTE, wird der mit der Standardschaltfläche verknüpfte Click-Handler ausgelöst und das ContentDialogResult gibt den mit der Standardschaltfläche verknüpften Wert zurück</span><span class="sxs-lookup"><span data-stu-id="daa6a-225">When the user presses the ENTER key on the keyboard, the click handler associated with the Default Button will fire and the ContentDialogResult will return the value associated with the Default Button</span></span>
    - <span data-ttu-id="daa6a-226">Wenn der Benutzer den Tastaturfokus auf ein Steuerelement gelegt hat, das die EINGABETASTE handhabt, reagiert die Standardschaltfläche nicht auf Drücken der EINGABETASTE</span><span class="sxs-lookup"><span data-stu-id="daa6a-226">If the user has placed Keyboard Focus on a control that handles ENTER, the Default Button will not respond to ENTER presses</span></span>
- <span data-ttu-id="daa6a-227">Die Schaltfläche erhält den Fokus automatisch, wenn das Dialogfeld geöffnet wird, es sei denn, der Inhalt des Dialogfelds enthält fokussierbare UI</span><span class="sxs-lookup"><span data-stu-id="daa6a-227">The button will receive focus automatically when the Dialog is opened unless the dialog’s content contains focusable UI</span></span>

<span data-ttu-id="daa6a-228">Verwenden Sie die ContentDialog.DefaultButton-Eigenschaft, um die Standardschaltfläche anzugeben.</span><span class="sxs-lookup"><span data-stu-id="daa6a-228">Use the ContentDialog.DefaultButton property to indicate the default button.</span></span> <span data-ttu-id="daa6a-229">Standardmäßig wird keine Standardschaltfläche festgelegt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-229">By default, no default button is set.</span></span>

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

### <a name="confirmation-dialogs-okcancel"></a><span data-ttu-id="daa6a-231">Bestätigungsdialogfelder (OK/Abbrechen)</span><span class="sxs-lookup"><span data-stu-id="daa6a-231">Confirmation dialogs (OK/Cancel)</span></span>
<span data-ttu-id="daa6a-232">In einem Bestätigungsdialogfeld können Benutzer bestätigen, dass sie eine Aktion ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="daa6a-232">A confirmation dialog gives users the chance to confirm that they want to perform an action.</span></span> <span data-ttu-id="daa6a-233">Sie können die Aktion bestätigen oder den Vorgang abbrechen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-233">They can affirm the action, or choose to cancel.</span></span>  
<span data-ttu-id="daa6a-234">Ein typisches Bestätigungsdialogfeld verfügt über zwei Schaltflächen: eine Schaltfläche zur Bestätigung („OK“) und eine Schaltfläche zum Abbrechen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-234">A typical confirmation dialog has two buttons: an affirmation ("OK") button and a cancel button.</span></span>  

<ul>
    <li>
        <p><span data-ttu-id="daa6a-235">Die Bestätigungsschaltfläche sollte sich im Allgemeinen auf der linken Seite (die primäre Schaltfläche) und die Abbruchschaltfläche (die sekundäre Schaltfläche) auf der rechten Seite befinden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-235">In general, the affirmation button should be on the left (the primary button) and the cancel button (the secondary button) should be on the right.</span></span></p>
        <img alt="An OK/cancel dialog" src="images/dialogs/dialog_RS2_delete_file.png" />
    </li>
    <li><span data-ttu-id="daa6a-236">Wie in den allgemeinen Empfehlungen erwähnt, sollten Sie Schaltflächen mit Text verwenden, der konkrete Antworten auf die Hauptanweisung bzw. den Hauptinhalt bietet.</span><span class="sxs-lookup"><span data-stu-id="daa6a-236">As noted in the general recommendations section, use buttons with text that identifies specific responses to the main instruction or content.</span></span>
    </li>
</ul>

> <span data-ttu-id="daa6a-237">Auf einigen Plattformen befindet sich die Bestätigungsschaltfläche auf der rechten anstatt auf der linken Seite.</span><span class="sxs-lookup"><span data-stu-id="daa6a-237">Some platforms put the affirmation button on the right instead of the left.</span></span> <span data-ttu-id="daa6a-238">Warum empfehlen wir die Platzierung auf der linken Seite?</span><span class="sxs-lookup"><span data-stu-id="daa6a-238">So why do we recommend putting it on the left?</span></span>  <span data-ttu-id="daa6a-239">Wenn Sie davon ausgehen, dass die meisten Benutzer Rechtshänder sind und ihr Telefon in dieser Hand halten, ist es bequemer, eine Bestätigungsschaltfläche zu drücken, die sich auf der linken Seite befindet, weil sie für den Benutzer wahrscheinlich einfacher mit dem Daumen erreichbar ist. Bei Schaltflächen auf der rechten Bildschirmseite muss der Benutzer seinen Daumen in eine weniger bequeme Position nach innen bewegen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-239">If you assume that the majority of users are right-handed and they hold their phone with that hand, it's actually more comfortable to press the affirmation button when it's on the left, because the button is more likely to be within the user's thumb-arc. Buttons on the right-side of the screen require the user to pull their thumb inward into a less-comfortable position.</span></span>

### <a name="create-a-dialog"></a><span data-ttu-id="daa6a-240">Erstellen eines Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="daa6a-240">Create a dialog</span></span>
<span data-ttu-id="daa6a-241">Um ein Dialogfeld zu erstellen, verwenden Sie die [ContentDialog-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog).</span><span class="sxs-lookup"><span data-stu-id="daa6a-241">To create a dialog, you use the [ContentDialog class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog).</span></span> <span data-ttu-id="daa6a-242">Sie können ein Dialogfeld im Code oder Markup erstellen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-242">You can create a dialog in code or markup.</span></span> <span data-ttu-id="daa6a-243">Obwohl es in der Regel leichter ist, UI-Elemente in XAML zu definieren, ist es bei einem einfachen Dialogfeld unkomplizierter, Code zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-243">Although its usually easier to define UI elements in XAML, in the case of a simple dialog, it's actually easier to just use code.</span></span> <span data-ttu-id="daa6a-244">In diesem Beispiel wird ein Dialogfeld erstellt, um dem Benutzer mitzuteilen, dass keine WLAN-Verbindung vorhanden ist. Für die Anzeige wird die Methode [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) verwendet.</span><span class="sxs-lookup"><span data-stu-id="daa6a-244">This example creates a dialog to notify the user that there's no WiFi connection, and then uses the [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method to display it.</span></span>

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

<span data-ttu-id="daa6a-245">Wenn der Benutzer auf eine Dialogfeldschaltfläche klickt, gibt die Methode [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) ein [ContentDialogResult](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) zurück, damit Sie wissen, auf welche Schaltfläche der Benutzer klickt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-245">When the user clicks a dialog button, the [ShowAsync](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method returns a [ContentDialogResult](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) to let you know which button the user clicks.</span></span>

<span data-ttu-id="daa6a-246">Das Dialogfeld in diesem Beispiel stellt eine Frage und verwendet das zurückgegebene [ContentDialogResult](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult), um die Antwort des Benutzers zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="daa6a-246">The dialog in this example asks a question and uses the returned [ContentDialogResult](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) to determine the user's response.</span></span>

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

## <a name="flyouts"></a><span data-ttu-id="daa6a-247">Flyouts</span><span class="sxs-lookup"><span data-stu-id="daa6a-247">Flyouts</span></span>
###  <a name="create-a-flyout"></a><span data-ttu-id="daa6a-248">Erstellen eines Flyouts</span><span class="sxs-lookup"><span data-stu-id="daa6a-248">Create a flyout</span></span>

<span data-ttu-id="daa6a-249">Ein Flyout ist ein einfach ausblendbarer Container, der beliebige UI als Inhalt anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="daa6a-249">A flyout is a light dismiss container that can show arbitrary UI as its content.</span></span> <span data-ttu-id="daa6a-250">Flyouts können andere Flyouts oder Kontextmenüs enthalten, um eine geschachtelte Umgebung zu kreieren.</span><span class="sxs-lookup"><span data-stu-id="daa6a-250">Flyouts can contain other flyouts or context menus to create a nested experience.</span></span>

![Kontextmenü geschachtelt in einem Flyout](images/flyout-nested.png)

<span data-ttu-id="daa6a-252">Flyouts sind an bestimmte Steuerelemente angefügt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-252">Flyouts are attached to specific controls.</span></span> <span data-ttu-id="daa6a-253">Sie können mit der [Placement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase.Placement)-Eigenschaft angeben, wo das Flyout angezeigt werden soll: oben, links, unten, rechts oder als Vollbild.</span><span class="sxs-lookup"><span data-stu-id="daa6a-253">You can use the [Placement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase.Placement) property to specify where a flyout appears: Top, Left, Bottom, Right, or Full.</span></span> <span data-ttu-id="daa6a-254">Wenn Sie den [vollständigen Platzierungsmodus](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutPlacementMode) auswählen, streckt die App das Flyout und zentriert es innerhalb des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="daa6a-254">If you select the [Full placement mode](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutPlacementMode), the app stretches the flyout and centers it inside the app window.</span></span> <span data-ttu-id="daa6a-255">Einige Steuerelemente wie z.B. [Schaltflächen](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Button), verfügen über eine [Flyout](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Button.Flyout)-Eigenschaft, mit der Sie ein Flyout oder [Kontextmenü](menus.md) zuordnen können.</span><span class="sxs-lookup"><span data-stu-id="daa6a-255">Some controls, such as [Button](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Button), provide a [Flyout](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Button.Flyout) property that you can use to associate a flyout or [context menu](menus.md).</span></span>

<span data-ttu-id="daa6a-256">In diesem Beispiel wird ein einfaches Flyout erstellt, das Text anzeigt, wenn die Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="daa6a-256">This example creates a simple flyout that displays some text when the button is pressed.</span></span>
````xaml
<Button Content="Click me">
  <Button.Flyout>
     <Flyout>
        <TextBlock Text="This is a flyout!"/>
     </Flyout>
  </Button.Flyout>
</Button>
````

<span data-ttu-id="daa6a-257">Wenn das Steuerelement nicht über eine Flyout-Eigenschaft verfügt, können Sie stattdessen die angefügte Eigenschaft [FlyoutBase.AttachedFlyout](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.AttachedFlyoutProperty) verwenden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-257">If the control doesn't have a flyout property, you can use the [FlyoutBase.AttachedFlyout](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.AttachedFlyoutProperty) attached property instead.</span></span> <span data-ttu-id="daa6a-258">In diesem Fall müssen Sie zudem die [FlyoutBase.ShowAttachedFlyout](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase#Windows_UI_Xaml_Controls_Primitives_FlyoutBase_ShowAttachedFlyout_Windows_UI_Xaml_FrameworkElement_)-Methode aufrufen, um das Flyout anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-258">When you do this, you also need to call the [FlyoutBase.ShowAttachedFlyout](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase#Windows_UI_Xaml_Controls_Primitives_FlyoutBase_ShowAttachedFlyout_Windows_UI_Xaml_FrameworkElement_) method to show the flyout.</span></span>

<span data-ttu-id="daa6a-259">In diesem Beispiel wird einem Bild ein einfaches Flyout hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-259">This example adds a simple flyout to an image.</span></span> <span data-ttu-id="daa6a-260">Wenn der Benutzer auf das Bild tippt, zeigt die App das Flyout an.</span><span class="sxs-lookup"><span data-stu-id="daa6a-260">When the user taps the image, the app shows the flyout.</span></span>

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

<span data-ttu-id="daa6a-261">In den vorherigen Beispielen wurden die Flyouts inline definiert.</span><span class="sxs-lookup"><span data-stu-id="daa6a-261">The previous examples defined their flyouts inline.</span></span> <span data-ttu-id="daa6a-262">Sie können ein Flyout auch als statische Ressource definieren und sie dann mit mehreren Elementen verwenden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-262">You can also define a flyout as a static resource and then use it with multiple elements.</span></span> <span data-ttu-id="daa6a-263">In diesem Beispiel wird ein komplizierteres Flyout erstellt, mit dem eine größere Version eines Bilds angezeigt wird, wenn auf die Miniaturansicht getippt wird.</span><span class="sxs-lookup"><span data-stu-id="daa6a-263">This example creates a more complicated flyout that displays a larger version of an image when its thumbnail is tapped.</span></span>

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

### <a name="style-a-flyout"></a><span data-ttu-id="daa6a-264">Gestalten eines Flyouts</span><span class="sxs-lookup"><span data-stu-id="daa6a-264">Style a flyout</span></span>
<span data-ttu-id="daa6a-265">Um ein Flyout zu formatieren, ändern Sie den [FlyoutPresenterStyle](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout.FlyoutPresenterStyle).</span><span class="sxs-lookup"><span data-stu-id="daa6a-265">To style a Flyout, modify its [FlyoutPresenterStyle](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout.FlyoutPresenterStyle).</span></span> <span data-ttu-id="daa6a-266">In diesem Beispiel wird ein Absatz mit Textumbruch dargestellt, was den Textblock für Bildschirmleseprogramme zugänglich gemacht.</span><span class="sxs-lookup"><span data-stu-id="daa6a-266">This example shows a paragraph of wrapping text and makes the text block accessible to a screen reader.</span></span>

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

#### <a name="styling-flyouts-for-10-foot-experience"></a><span data-ttu-id="daa6a-268">Formatieren von Flyouts für die 10 Fuß-Umgebung</span><span class="sxs-lookup"><span data-stu-id="daa6a-268">Styling flyouts for 10-foot experience</span></span>

<span data-ttu-id="daa6a-269">Einfach ausblendbare Steuerelemente wie Flyouts erhalten den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-269">Light dismiss controls like flyout trap keyboard and gamepad focus inside their transient UI until dismissed.</span></span> <span data-ttu-id="daa6a-270">Um dieses Verhalten optisch zu kennzeichnen, werden diese einfach ausblendbaren Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei der Kontrast und die Helligkeit bzw. Sichtbarkeit der umgebenden Benutzeroberfläche reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="daa6a-270">To provide a visual cue for this behavior, light dismiss controls on Xbox draw an overlay that dims the contrast and visibility of out of scope UI.</span></span> <span data-ttu-id="daa6a-271">Dieses Verhalten kann mit der Eigenschaft [`LightDismissOverlayMode`](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase.LightDismissOverlayMode) geändert werden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-271">This behavior can be modified with the [`LightDismissOverlayMode`](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase.LightDismissOverlayMode) property.</span></span> <span data-ttu-id="daa6a-272">Standardmäßig erhalten Flyouts auf der Xbox (jedoch nicht auf anderen Gerätefamilien) die einfach ausblendbare Überlagerung. Apps können jedoch durchsetzen, dass die Überlagerung stets **An** oder stets **Aus** ist.</span><span class="sxs-lookup"><span data-stu-id="daa6a-272">By default, flyouts will draw the light dismiss overlay on Xbox but not other device families, but apps can choose to force the overlay to be always **On** or always **Off**.</span></span>

![Flyout mit Abblend-Überlagerung](images/flyout-smoke.png)

```xaml
<MenuFlyout LightDismissOverlayMode="On">
```

### <a name="light-dismiss-behavior"></a><span data-ttu-id="daa6a-274">Verhalten für einfaches Ausblenden</span><span class="sxs-lookup"><span data-stu-id="daa6a-274">Light dismiss behavior</span></span>
<span data-ttu-id="daa6a-275">Flyouts können schnell mit einer einfachen Ausblend-Aktion geschlossen werden. Dazu zählen:</span><span class="sxs-lookup"><span data-stu-id="daa6a-275">Flyouts can be closed with a quick light dismiss action, including</span></span>
-   <span data-ttu-id="daa6a-276">Tippen außerhalb des Flyouts</span><span class="sxs-lookup"><span data-stu-id="daa6a-276">Tap outside the flyout</span></span>
-   <span data-ttu-id="daa6a-277">Drücken der ESC-Taste auf der Tastatur</span><span class="sxs-lookup"><span data-stu-id="daa6a-277">Press the Escape keyboard key</span></span>
-   <span data-ttu-id="daa6a-278">Drücken der Zurück-Taste des Systems (Hardware oder Software)</span><span class="sxs-lookup"><span data-stu-id="daa6a-278">Press the hardware or software system Back button</span></span>
-   <span data-ttu-id="daa6a-279">Drücken der B-Taste auf dem Gamepad</span><span class="sxs-lookup"><span data-stu-id="daa6a-279">Press the gamepad B button</span></span>

<span data-ttu-id="daa6a-280">Wird das Ausblenden durch Tippen vorgenommen, wird die Geste in der Regel absorbiert und nicht an die UI unterhalb weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="daa6a-280">When dismissing with a tap, this gesture is typically absorbed and not passed on to the UI underneath.</span></span> <span data-ttu-id="daa6a-281">Ist beispielsweise hinter einem geöffneten Flyout eine Schaltfläche sichtbar, wird durch einfaches Antippen durch den Benutzer das Flyout ausgeblendet, ohne jedoch diese Schaltfläche zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="daa6a-281">For example, if there’s a button visible behind an open flyout, the user’s first tap dismisses the flyout but does not activate this button.</span></span> <span data-ttu-id="daa6a-282">Um die Schaltfläche zu drücken, ist ein weiteres Antippen nötig.</span><span class="sxs-lookup"><span data-stu-id="daa6a-282">Pressing the button requires a second tap.</span></span>

<span data-ttu-id="daa6a-283">Sie können dieses Verhalten ändern, indem Sie die Schaltfläche als Pass-Through-Eingabeelement für das Flyout gestalten.</span><span class="sxs-lookup"><span data-stu-id="daa6a-283">You can change this behavior by designating the button as an input pass-through element for the flyout.</span></span> <span data-ttu-id="daa6a-284">Das Flyout wird wie oben beschriebenen durch die einfache Ausblend-Aktion geschlossen, gibt den Antipp-Vorgang aber gleichzeitig an das entsprechende `OverlayInputPassThroughElement` weiter.</span><span class="sxs-lookup"><span data-stu-id="daa6a-284">The flyout will close as a result of the light dismiss actions described above and will also pass the tap event to its designated `OverlayInputPassThroughElement`.</span></span> <span data-ttu-id="daa6a-285">Erwägen Sie, dieses Verhalten zu übernehmen, um Interaktionen des Benutzers bei ähnlich funktionierenden Elementen zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="daa6a-285">Consider adopting this behavior to speed up user interactions on functionally similar items.</span></span> <span data-ttu-id="daa6a-286">Wenn Ihre App eine Sammlung von Favoriten beinhaltet und jedes Element der Sammlung ein angefügtes Flyout enthält, kann man davon auszugehen, dass die Benutzer mehrere Flyouts in schneller Abfolge abarbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="daa6a-286">If your app has a favorites collection and each item in the collection includes an attached flyout, it's reasonable to expect that users may want to interact with multiple flyouts in rapid succession.</span></span>

[!NOTE] <span data-ttu-id="daa6a-287">Achten Sie darauf, kein Überlagerungseingabeelement mit Pass-Through festzulegen, da dies in einer destruktiven Aktion resultiert.</span><span class="sxs-lookup"><span data-stu-id="daa6a-287">Be careful not to designate an overlay input pass-through element which results in a destructive action.</span></span> <span data-ttu-id="daa6a-288">Die Benutzer sind an diskrete, einfach ausblendbare Aktionen gewöhnt, die die Primär-UI nicht aktivieren.</span><span class="sxs-lookup"><span data-stu-id="daa6a-288">Users have become habituated to discreet light dismiss actions which do not activate primary UI.</span></span> <span data-ttu-id="daa6a-289">Schließen, Löschen oder ähnlich destruktive Schaltflächen sollten nicht über einfach ausblendbare Elemente aktiviert werden, um unerwartetes und störendes Verhalten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="daa6a-289">Close, Delete or similarly destructive buttons should not activate on light dismiss to avoid unexpected and disruptive behavior.</span></span>

<span data-ttu-id="daa6a-290">Im folgenden Beispiel werden alle drei Schaltflächen in der Favoritenleiste durch einfaches Antippen aktiviert.</span><span class="sxs-lookup"><span data-stu-id="daa6a-290">In the following example, all three buttons inside FavoritesBar will be activated on the first tap.</span></span>

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

## <a name="get-the-sample-code"></a><span data-ttu-id="daa6a-291">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="daa6a-291">Get the sample code</span></span>

- <span data-ttu-id="daa6a-292">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="daa6a-292">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="daa6a-293">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="daa6a-293">Related articles</span></span>
- [<span data-ttu-id="daa6a-294">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="daa6a-294">Tooltips</span></span>](tooltips.md)
- [<span data-ttu-id="daa6a-295">Menüs und Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="daa6a-295">Menus and context menu</span></span>](menus.md)
- [<span data-ttu-id="daa6a-296">Flyout-Klasse</span><span class="sxs-lookup"><span data-stu-id="daa6a-296">Flyout class</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout)
- [<span data-ttu-id="daa6a-297">ContentDialog-Klasse</span><span class="sxs-lookup"><span data-stu-id="daa6a-297">ContentDialog class</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ContentDialog)
