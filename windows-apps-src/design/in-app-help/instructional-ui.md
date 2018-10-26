---
author: QuinnRadich
Description: Design an instructional user interface (UI) that teaches users how to work with your UWP app.
title: Richtlinien für das Entwerfen von Benutzeroberflächen mit Anleitungen
label: Instructional UI
template: detail.hbs
ms.author: quradic
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: c87e2f06-339d-4413-b585-172752964f56
ms.localizationpriority: medium
ms.openlocfilehash: 9c97b6b5eca82d309a4b65a914041adeb1e782db
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5559104"
---
# <a name="instructional-ui-guidelines"></a><span data-ttu-id="66600-103">Richtlinien für Benutzeroberflächen mit Anleitungen</span><span class="sxs-lookup"><span data-stu-id="66600-103">Instructional UI guidelines</span></span>



<span data-ttu-id="66600-104">In gewissen Fällen kann es hilfreich sein, Anleitungen bereitzustellen, um Benutzern die Funktionen in Ihrer App zu demonstrieren, die möglicherweise nicht offensichtlich sind, z. B. bestimmte Touch-Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="66600-104">In some circumstances it can be helpful to teach the user about functions in your app that might not be obvious to them, such as specific touch interactions.</span></span> <span data-ttu-id="66600-105">In diesen Fällen müssen Sie Anleitungen auf der Benutzeroberfläche für den Benutzer bereitstellen, damit sie diese Funktionen, die sie möglicherweise übersehen haben, nutzen können.</span><span class="sxs-lookup"><span data-stu-id="66600-105">In these cases, you need to present instructions to the user through the user interface (UI), so that they can use those features they might have missed.</span></span>

## <a name="when-to-use-instructional-ui"></a><span data-ttu-id="66600-106">Gründe für die Verwendung einer Benutzeroberfläche mit Anleitungen</span><span class="sxs-lookup"><span data-stu-id="66600-106">When to use instructional UI</span></span>

<span data-ttu-id="66600-107">Benutzeroberflächen mit Anleitungen sollten Sie sparsam einsetzen.</span><span class="sxs-lookup"><span data-stu-id="66600-107">Instructional UI has to be used carefully.</span></span> <span data-ttu-id="66600-108">Bei übermäßiger Nutzung werden die Anleitungen leicht ignoriert oder verärgern die Benutzer und sind somit wirkungslos.</span><span class="sxs-lookup"><span data-stu-id="66600-108">When overused, it can be easily ignored or annoy the user, causing it to be ineffective.</span></span>

<span data-ttu-id="66600-109">Benutzeroberflächen mit Anleitungen sollten dazu dienen, dass Benutzer auf wichtige und nicht offensichtliche Funktionen Ihrer App hingewiesen werden, wie z. B. Touchgesten oder Einstellungen, die für sie von Interesse sind.</span><span class="sxs-lookup"><span data-stu-id="66600-109">Instructional UI should be used to help the user discover important and non-obvious features of your app, such as touch gestures or settings they may be interested in.</span></span> <span data-ttu-id="66600-110">Sie können auch dazu verwendet werden, Benutzer über neue Funktionen und Änderungen in der App aufmerksam zu machen, die sie andernfalls möglicherweise übersehen.</span><span class="sxs-lookup"><span data-stu-id="66600-110">It can also be used to inform users about new features or changes in your app that they might have otherwise overlooked.</span></span>

<span data-ttu-id="66600-111">Benuteroberflächen mit Anleitungen sollten nur dann zum Vermitteln grundlegender Funktionen Ihrer App verwendet werden, wenn Ihre App von Touchgesten abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="66600-111">Unless your app is dependent on touch gestures, instructional UI should not be used to teach users the fundamental features of your app.</span></span>

## <a name="principles-of-writing-instructional-ui"></a><span data-ttu-id="66600-112">Grundsätze für das Entwerfen von Benutzeroberflächen mit Anleitungen</span><span class="sxs-lookup"><span data-stu-id="66600-112">Principles of writing instructional UI</span></span>

<span data-ttu-id="66600-113">Gute Benutzeroberflächen mit Anleitungen sind hilfreich und lehrreich für Benutzer und optimieren die Benutzerfreundlichkeit.</span><span class="sxs-lookup"><span data-stu-id="66600-113">Good instructional UI is relevant and educational to the user, and enhances the user experience.</span></span> <span data-ttu-id="66600-114">Folgende Merkmale sollten diese Benutzeroberflächen ausmachen:</span><span class="sxs-lookup"><span data-stu-id="66600-114">It should be:</span></span>

-   <span data-ttu-id="66600-115">**Einfach:** Benutzer möchten nicht durch komplizierte Informationen unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="66600-115">**Simple:** Users don't want their experience to be interrupted with complicated information</span></span>
-   <span data-ttu-id="66600-116">**Einprägsam:** Benutzer möchten nicht, dass bei jedem Versuch, eine Aufgabe auszuführen, die gleichen Anleitungen angezeigt werden. Die Anleitungen müssen daher leicht einprägsam sein.</span><span class="sxs-lookup"><span data-stu-id="66600-116">**Memorable:** Users don't want to see the same instructions every time they attempt a task, so instructions need to be something they'll remember.</span></span>
-   <span data-ttu-id="66600-117">**Unmittelbar relevant:** Wenn die Anleitungen auf der Benutzeroberfläche sich nicht auf eine Aktion beziehen, die die Benutzer gerade ausführen möchten, sehen sie keinen Grund, diesen ihre Aufmerksamkeit zu schenken.</span><span class="sxs-lookup"><span data-stu-id="66600-117">**Immediately relevant:** If the instructional UI doesn't teach a user about something that they immediately want to do, they won't have a reason to pay attention to it.</span></span>

<span data-ttu-id="66600-118">Setzen Sie Benutzeroberflächen mit Anleitungen nicht übermäßig ein, und achten Sie darauf, die richtigen Themen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="66600-118">Avoid overusing instructional UI, and be sure to choose the right topics.</span></span> <span data-ttu-id="66600-119">Stellen Sie sicher, dass Folgendes nicht mithilfe von Benutzeroberflächen mit Anleitungen vermittelt wird:</span><span class="sxs-lookup"><span data-stu-id="66600-119">Do not teach:</span></span>

-   <span data-ttu-id="66600-120">**Grundlegende Features:** Wenn Benutzer Anleitungen zum Verwenden Ihrer App benötigen, sollten Sie das App-Design intuitiver gestalten.</span><span class="sxs-lookup"><span data-stu-id="66600-120">**Fundamental features:** If a user needs instructions to use your app, consider making the app design more intuitive.</span></span>
-   <span data-ttu-id="66600-121">**Offensichtliche Features:** Wenn eine Funktion für einen Benutzer ohne Anleitung offensichtlich ist, wird ihn eine Benutzeroberfläche mit Anleitungen nur behindern.</span><span class="sxs-lookup"><span data-stu-id="66600-121">**Obvious features:** If a user can figure out a feature on their own without instruction, then the instructional UI will just get in the way.</span></span>
-   <span data-ttu-id="66600-122">**Komplexe Features:** Benutzeroberflächen mit Anleitungen müssen präzise sein. Benutzer, für die komplexe Funktionen von Interesse sind, sind in der Regel bereit, selbst nach Anleitungen zu suchen.</span><span class="sxs-lookup"><span data-stu-id="66600-122">**Complex features:** Instructional UI needs to be concise, and users interested in complex features are usually willing to seek out instructions and don't need to be given them.</span></span>

<span data-ttu-id="66600-123">Vermeiden Sie es, die Benutzererfahrung durch Ihre Benutzeroberfläche mit Anleitungen zu beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="66600-123">Avoid inconveniencing the user with your instructional UI.</span></span> <span data-ttu-id="66600-124">Nicht empfohlene Vorgehensweise:</span><span class="sxs-lookup"><span data-stu-id="66600-124">Do not:</span></span>

-   <span data-ttu-id="66600-125">**Überdecken wichtiger Informationen:** Benutzeroberflächen mit Anleitungen sollten niemals andere Features Ihrer App verdecken.</span><span class="sxs-lookup"><span data-stu-id="66600-125">**Obscure important information:** Instructional UI should never get in the way of other features of your app.</span></span>
-   <span data-ttu-id="66600-126">**Nutzungszwang für Benutzer:** Benutzer sollten in der Lage sein, Anleitungen in der Benutzeroberfläche zu ignorieren und mit der Verwendung der App fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="66600-126">**Force users to participate:** Users should be able to ignore instructional UI and still progress through the app.</span></span>
-   <span data-ttu-id="66600-127">**Wiederholte Anzeige von Informationen:** Behelligen Sie Benutzer nicht mit der wiederholten Anzeige von Anleitungen auf der Benutzeroberfläche, auch wenn diese bei der ersten Anzeige ignoriert wurden.</span><span class="sxs-lookup"><span data-stu-id="66600-127">**Displaying repeat information:** Don't harass the user with instructional UI, even if they ignore it the first time.</span></span> <span data-ttu-id="66600-128">Das Hinzufügen einer Einstellung, mit der Anleitungen erneut auf der Benutzeroberfläche angezeigt werden können, ist die bessere Lösung.</span><span class="sxs-lookup"><span data-stu-id="66600-128">Adding an setting to display instructional UI again is a better solution.</span></span>

## <a name="examples-of-instructional-ui"></a><span data-ttu-id="66600-129">Beispiele für Benutzeroberflächen mit Anleitungen</span><span class="sxs-lookup"><span data-stu-id="66600-129">Examples of instructional UI</span></span>

<span data-ttu-id="66600-130">Unten sind einige Fälle aufgeführt, in denen eine Benutzeroberfläche mit Anleitungen für Benutzer sinnvoll ist:</span><span class="sxs-lookup"><span data-stu-id="66600-130">Here are a few instances in which instructional UI can help your users learn:</span></span>

-   **<span data-ttu-id="66600-131">Unterstützen der Benutzer beim Kennenlernen der Interaktionen per Toucheingabe.</span><span class="sxs-lookup"><span data-stu-id="66600-131">Helping users discover touch interactions.</span></span>** <span data-ttu-id="66600-132">Der folgende Screenshot zeigt eine Benutzeroberfläche mit Anleitungen, mit deren Hilfe ein Spieler lernt, wie er im Spiel „Cut the Rope“ Touchgesten verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="66600-132">The following screen shot shows instructional UI teaching a player how to use touch gestures in the game, Cut the Rope.</span></span>

    ![Screenshot aus dem Spiel, der die Meldung „Slide across to cut the rope“ (Führen Sie zum Trennen des Seils eine Ziehbewegung aus.) der Benutzeroberfläche mit Anweisungen zeigt.](images/in-game-controls-3.png)

-   **<span data-ttu-id="66600-134">Erzielen eines ausgezeichneten ersten Eindrucks.</span><span class="sxs-lookup"><span data-stu-id="66600-134">Making a great first impression.</span></span>** <span data-ttu-id="66600-135">Beim ersten Starten von Movie Moments wird der Benutzer mithilfe von Anleitungen auf der Benutzeroberfläche dazu aufgefordert, mit der Erstellung von Filmen zu beginnen, ohne dass seine Benutzererfahrung beeinträchtig wird.</span><span class="sxs-lookup"><span data-stu-id="66600-135">When Movie Moments launches for the first time, instructional UI prompts the user to begin creating movies without obstructing their experience.</span></span>

    ![Startbildschirm für die App „Movie Moments“](images/instructional-ui-movie.png)

-   **<span data-ttu-id="66600-137">Führen der Benutzer zum nächsten Schritt einer komplizierten Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="66600-137">Guiding users to take the next step in a complicated task.</span></span>** <span data-ttu-id="66600-138">In der Windows Mail-App werden die Benutzer mithilfe eines Hinweises am unteren Rand des Posteingangs zu den **Einstellungen** für den Zugriff auf ältere Nachrichten geleitet.</span><span class="sxs-lookup"><span data-stu-id="66600-138">In the Windows Mail app, a hint at the bottom of the Inbox directs users to **Settings** to access older messages.</span></span>

    ![Zugeschnittener Screenshot der Windows Mail-App, der eine Meldung einer Benutzeroberfläche mit Anleitungen zeigt](images/instructional-ui-mail-inbox.png)

    <span data-ttu-id="66600-140">Wenn der Benutzer auf die Meldung klickt, wird auf der rechten Seite des Bildschirms das **Einstellungen**-Flyout der App angezeigt, in dem der Benutzer die Aufgabe ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="66600-140">When the user clicks the message, the app's **Settings** flyout appears on the right side of the screen, allowing the user to complete the task.</span></span> <span data-ttu-id="66600-141">Diese Screenshots zeigen die Mail-App vor und nach dem Klicken auf die Meldung der Benutzeroberfläche mit Anleitungen durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="66600-141">These screen shots show the Mail app before and after a user clicks the instructional UI message.</span></span>

    | <span data-ttu-id="66600-142">Vorher</span><span class="sxs-lookup"><span data-stu-id="66600-142">Before</span></span>                                                               | <span data-ttu-id="66600-143">Nachher</span><span class="sxs-lookup"><span data-stu-id="66600-143">After</span></span>                                                                                                        |
    |----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | ![Screenshot der Windows Mail-App](images/instructional-ui-mail.png) | ![Screenshot der Windows Mail-App mit einem erweiterten Einstellungen-Flyout](images/instructional-ui-mail-flyout.png) |

## <a name="related-articles"></a><span data-ttu-id="66600-146">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="66600-146">Related articles</span></span>

* [<span data-ttu-id="66600-147">Anleitungen für die App-Hilfe</span><span class="sxs-lookup"><span data-stu-id="66600-147">Guidelines for app help</span></span>](guidelines-for-app-help.md)
