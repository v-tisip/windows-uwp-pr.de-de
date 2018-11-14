---
author: mijacobs
Description: Dialogs and flyouts display transient UI elements that appear when the user requests them or when something happens that requires notification or approval.
title: Dialogfelder und Flyouts
template: detail.hbs
ms.author: mijacobs
ms.date: 07/06/2018
ms.topic: article
keywords: windows 10, uwp
ms.assetid: ad6affd9-a3c0-481f-a237-9a1ecd561be8
pm-contact: yulikl
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: d4ff66e988634cf1ba48809688ea6535e6e95b03
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6161111"
---
# <a name="dialogs-and-flyouts"></a><span data-ttu-id="5c0bf-103">Dialogfelder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="5c0bf-103">Dialogs and flyouts</span></span>



<span data-ttu-id="5c0bf-104">Dialogfelder und Flyouts sind vorübergehende UI-Elemente, die angezeigt werden, wenn Ereignisse Benachrichtigungen, Genehmigungen oder zusätzliche Informationen vom Benutzer erfordern.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-104">Dialogs and flyouts are transient UI elements that appear when something happens that requires notification, approval, or additional information from the user.</span></span>

> <span data-ttu-id="5c0bf-105">**Wichtige APIs**: [ContentDialog-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog), [Flyout-Klasse](/uwp/api/Windows.UI.Xaml.Controls.Flyout)</span><span class="sxs-lookup"><span data-stu-id="5c0bf-105">**Important APIs**: [ContentDialog class](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog), [Flyout class](/uwp/api/Windows.UI.Xaml.Controls.Flyout)</span></span>


:::row:::
    :::column:::
        **Dialogs**
        
        ![Example of a dialog](../images/dialogs/dialog_RS2_delete_file.png)

        Dialogs are modal UI overlays that provide contextual app information. Dialogs block interactions with the app window until being explicitly dismissed. They often request some kind of action from the user.
    :::column-end:::
    :::column::: 
        **Flyouts**

        ![Example of a flyout](../images/flyout-example2.png)

        A flyout is a lightweight contextual popup that displays UI related to what the user is doing. It includes placement and sizing logic, and can be used to reveal a secondary control or show more detail about an item.

        Unlike a dialog, a flyout can be quickly dismissed by tapping or clicking somewhere outside the flyout, pressing the Escape key or Back button, resizing the app window, or changing the device's orientation.
    :::column-end:::
:::row-end:::


## <a name="is-this-the-right-control"></a><span data-ttu-id="5c0bf-106">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="5c0bf-106">Is this the right control?</span></span>

<span data-ttu-id="5c0bf-107">Dialogfelder und Flyouts stellen sicher, dass den Benutzern wichtige Informationen bekannt sind, stellen jedoch auch eine Unterbrechung dar.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-107">Dialogs and flyouts make sure that users are aware of important information, but they also disrupt the user experience.</span></span> <span data-ttu-id="5c0bf-108">Da Dialogfelder modal (blockierend) sind, werden die Benutzer unterbrochen und daran gehindert, andere Schritte durchzuführen, bis eine Interaktion mit dem Dialogfeld erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-108">Because dialogs are modal (blocking), they interrupt users, preventing them from doing anything else until they interact with the dialog.</span></span> <span data-ttu-id="5c0bf-109">Flyouts sind weniger störend. Zu viele Flyouts können jedoch als störend empfunden werden.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-109">Flyouts provide a less jarring experience, but displaying too many flyouts can be distracting.</span></span>

<span data-ttu-id="5c0bf-110">Wenn ein Dialogfeld oder Flyout eingesetzt werden soll, müssen Sie sich für eine der beiden Optionen entscheiden.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-110">Once you've determined that you want to use a dialog or flyout, you need to choose which one to use.</span></span>

<span data-ttu-id="5c0bf-111">Angesichts der Tatsache, dass Dialogfelder im Gegensatz zu Flyouts Interaktionen blockieren, sollten Dialogfelder auf Situationen beschränkt bleiben, in denen der Benutzer unterbrochen werden soll, um sich auf eine bestimmte Information oder die Beantwortung einer Frage zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-111">Given that dialogs block interactions and flyouts do not, dialogs should be reserved for situations where you want the user to drop everything to focus on a specific bit of information or answer a question.</span></span> <span data-ttu-id="5c0bf-112">Flyouts hingegen können verwendet werden, wenn Sie auf etwas aufmerksam machen möchten, das der Benutzer jedoch ignorieren kann.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-112">Flyouts, on the other hand, can be used when you want to call attention to something, but it's ok if the user wants to ignore it.</span></span>

:::row:::
    :::column:::
   <p><b><span data-ttu-id="5c0bf-113">Fälle, in denen ein Dialogfeld verwendet werden sollte:</span><span class="sxs-lookup"><span data-stu-id="5c0bf-113">Use a dialog for...</span></span></b> <br/>
<ul>
<li><span data-ttu-id="5c0bf-114">Für wichtige Informationen, die der Benutzer vor dem Fortsetzen lesen und bestätigen <b>muss</b>.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-114">Expressing important information that the user <b>must</b> read and acknowledge before proceeding.</span></span> <span data-ttu-id="5c0bf-115">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="5c0bf-115">Examples include:</span></span>
<ul>
  <li><span data-ttu-id="5c0bf-116">Die Sicherheit des Benutzers ist möglicherweise gefährdet.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-116">When the user's security might be compromised</span></span></li>
  <li><span data-ttu-id="5c0bf-117">Der Benutzer möchte eine wertvolle Ressource endgültig ändern.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-117">When the user is about to permanently alter a valuable asset</span></span></li>
  <li><span data-ttu-id="5c0bf-118">Der Benutzer möchte eine wertvolle Ressource löschen.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-118">When the user is about to delete a valuable asset</span></span></li>
  <li><span data-ttu-id="5c0bf-119">Bestätigen eines In-App-Einkaufs</span><span class="sxs-lookup"><span data-stu-id="5c0bf-119">To confirm an in-app purchase</span></span></li>
</ul>

</li>
<li><span data-ttu-id="5c0bf-120">Fehlermeldungen, die sich auf den Gesamtkontext der App beziehen, z. B. Verbindungsfehler.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-120">Error messages that apply to the overall app context, such as a connectivity error.</span></span></li>
<li><span data-ttu-id="5c0bf-121">Fragen, wenn dem Benutzer eine blockierende Frage gestellt werden muss, z. B. wenn die App nicht im Auftrag des Benutzers eine Auswahl treffen kann.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-121">Questions, when the app needs to ask the user a blocking question, such as when the app can't choose on the user's behalf.</span></span> <span data-ttu-id="5c0bf-122">Eine blockierende Frage kann nicht ignoriert oder verschoben werden und sollte dem Benutzer klar definierte Auswahlmöglichkeiten bieten.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-122">A blocking question can't be ignored or postponed, and should offer the user well-defined choices.</span></span></li>
</ul>
</p>
    :::column-end:::
    :::column:::
   <p><b><span data-ttu-id="5c0bf-123">Fälle, in denen ein Flyout verwendet werden sollte:</span><span class="sxs-lookup"><span data-stu-id="5c0bf-123">Use a flyout for...</span></span></b> <br/>
<ul>
<li><span data-ttu-id="5c0bf-124">Erfassen zusätzlicher Informationen, die erforderlich sind, bevor eine Aktion abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-124">Collecting additional information needed before an action can be completed.</span></span></li>
<li><span data-ttu-id="5c0bf-125">Anzeigen von Informationen, die nur vorübergehend relevant sind.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-125">Displaying info that's only relevant some of the time.</span></span> <span data-ttu-id="5c0bf-126">So können Sie z.B. in einer Fotogalerie-App ein Flyout einsetzen, damit eine große Version des Bilds angezeigt wird, wenn der Benutzer auf eine Miniaturansicht klickt.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-126">For example, in a photo gallery app, when the user clicks an image thumbnail, you might use a flyout to display a large version of the image.</span></span></li>
<li><span data-ttu-id="5c0bf-127">Anzeigen weiterer Informationen, z. B. von Details oder ausführlicheren Beschreibungen eines Elements auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-127">Displaying more information, such as details or longer descriptions of an item on the page.</span></span></li>
</ul></p>
    :::column-end:::
:::row-end:::


## <a name="ways-to-avoid-using-dialogs-and-flyouts"></a><span data-ttu-id="5c0bf-128">Möglichkeiten, um zu vermeiden, Dialogfelder und flyouts</span><span class="sxs-lookup"><span data-stu-id="5c0bf-128">Ways to avoid using dialogs and flyouts</span></span>

<span data-ttu-id="5c0bf-129">Berücksichtigen Sie die Bedeutung der zu vermittelnden Informationen: Sind sie wichtig genug, um den Benutzer zu unterbrechen?</span><span class="sxs-lookup"><span data-stu-id="5c0bf-129">Consider the importance of the information you want to share: is it important enough to interrupt the user?</span></span> <span data-ttu-id="5c0bf-130">Berücksichtigen Sie zudem, wie häufig die Informationen angezeigt werden müssen. Wenn ein Dialogfeld oder eine Benachrichtigung alle paar Minuten angezeigt wird, sollten Sie diese Informationen stattdessen in die primäre UI einbinden.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-130">Also consider how frequently the information needs to be shown; if you're showing a dialog or notification every few minutes, you might want to allocate space for this info in the primary UI instead.</span></span> <span data-ttu-id="5c0bf-131">So können Sie z.B. in einem Chat-Client anstatt eines Flyouts, der jedes Mal angezeigt wird, wenn sich ein Freund anmeldet, eine Liste der Freunde anzeigen, die derzeit online sind, und diejenigen Freunde hervorheben, die sich gerade anmelden.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-131">For example, in a chat client, rather than showing a flyout every time a friend logs in, you might display a list of friends who are online at the moment and highlight friends as they log on.</span></span>

<span data-ttu-id="5c0bf-132">Dialogfelder werden häufig zum Bestätigen einer Aktion vor deren Ausführung verwendet (z.B. vor dem Löschen einer Datei).</span><span class="sxs-lookup"><span data-stu-id="5c0bf-132">Dialogs are frequently used to confirm an action (such as deleting a file) before executing it.</span></span> <span data-ttu-id="5c0bf-133">Wenn Sie davon ausgehen, dass die Benutzer häufig eine bestimmte Aktion ausführen, sollten Sie eine Möglichkeit bereitstellen, versehentliche Aktionen rückgängig zu machen, anstatt jedes Mal die Bestätigung der Aktion zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-133">If you expect the user to perform a particular action frequently, consider providing a way for the user to undo the action if it was a mistake, rather than forcing users to confirm the action every time.</span></span>

## <a name="how-to-create-a-dialog"></a><span data-ttu-id="5c0bf-134">So erstellen Sie ein Dialogfeld</span><span class="sxs-lookup"><span data-stu-id="5c0bf-134">How to create a dialog</span></span>

<span data-ttu-id="5c0bf-135">Finden Sie unter dem [Artikel Dialogfelder](dialogs.md).</span><span class="sxs-lookup"><span data-stu-id="5c0bf-135">See the [Dialogs article](dialogs.md).</span></span> 

## <a name="how-to-create-a-flyout"></a><span data-ttu-id="5c0bf-136">So erstellen Sie ein flyout</span><span class="sxs-lookup"><span data-stu-id="5c0bf-136">How to create a flyout</span></span>

<span data-ttu-id="5c0bf-137">Finden Sie im [Artikel Flyout](flyouts.md).</span><span class="sxs-lookup"><span data-stu-id="5c0bf-137">See the [Flyout article](flyouts.md).</span></span> 

## <a name="examples"></a><span data-ttu-id="5c0bf-138">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5c0bf-138">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="5c0bf-139">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="5c0bf-139">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="../images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="5c0bf-140">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> oder <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="5c0bf-140">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> or <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="5c0bf-141">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="5c0bf-141">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="5c0bf-142">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="5c0bf-142">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

