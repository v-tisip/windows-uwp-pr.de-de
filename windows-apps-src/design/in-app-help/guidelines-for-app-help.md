---
Description: These guidelines describe how to design effective Help content for your app.
title: Anleitungen für die App-Hilfe
label: Guidelines for app help
template: detail.hbs
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: c3e73f9b-4839-4804-b379-c95b0ca4fbe8
ms.localizationpriority: medium
ms.openlocfilehash: bd2174c6bbfb84a3ea6c6956e1d0b02ed5c9be33
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7720028"
---
# <a name="guidelines-for-app-help"></a><span data-ttu-id="0d003-103">Anleitungen für die App-Hilfe</span><span class="sxs-lookup"><span data-stu-id="0d003-103">Guidelines for App Help</span></span>



<span data-ttu-id="0d003-104">Anwendungen können sehr komplex sein. Sie können die Erfahrung für die Benutzer durch die Bereitstellung einer effektiven Hilfe erheblich verbessern.</span><span class="sxs-lookup"><span data-stu-id="0d003-104">Applications can be complex, and providing effective help for your users can greatly improve their experience.</span></span> <span data-ttu-id="0d003-105">Nicht alle Anwendungen müssen Hilfe für ihre Benutzer bereitstellen, und welche Art von Hilfe bereitgestellt werden sollte, kann je nach Anwendung unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="0d003-105">Not all applications need to provide help for their users, and what sort of help should be provided can vary greatly, depending on the application.</span></span>

<span data-ttu-id="0d003-106">Wenn Sie Hilfe bereitstellen möchten, befolgen Sie diese Richtlinien beim Erstellen.</span><span class="sxs-lookup"><span data-stu-id="0d003-106">If you decide to provide help, follow these guidelines when creating it.</span></span> <span data-ttu-id="0d003-107">Hilfe, die nicht nützlich ist, kann schlimmer sein als gar keine Hilfe.</span><span class="sxs-lookup"><span data-stu-id="0d003-107">Help that isn't helpful can be worse than no help at all.</span></span>

## <a name="intuitive-design"></a><span data-ttu-id="0d003-108">Intuitives Design</span><span class="sxs-lookup"><span data-stu-id="0d003-108">Intuitive Design</span></span>

<span data-ttu-id="0d003-109">Hilfeinhalte können zwar nützlich sein, doch in Ihrer App darf dies nicht das einzige Merkmal für Benutzerfreundlichkeit sein.</span><span class="sxs-lookup"><span data-stu-id="0d003-109">As useful as help content can be, your app cannot rely on it to provide a good experience for the user.</span></span> <span data-ttu-id="0d003-110">Wenn der Benutzer die wichtigen Funktionen der App nicht sofort erkennen und nutzen kann, wird der Benutzer die App nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="0d003-110">If the user is unable to immediately discover and use the critical functions of your app, the user will not use your app.</span></span> <span data-ttu-id="0d003-111">Dieser erste Eindruck kann durch keine Hilfe geändert werden, so umfassend oder hochwertig sie auch sein mag.</span><span class="sxs-lookup"><span data-stu-id="0d003-111">No amount or quality help will change that first impression.</span></span>

<span data-ttu-id="0d003-112">Ein intuitives und benutzerfreundliches Design ist der erste Schritt beim Erstellen einer nützlichen Hilfe.</span><span class="sxs-lookup"><span data-stu-id="0d003-112">An intuitive and user-friendly design is the first step to writing useful help.</span></span> <span data-ttu-id="0d003-113">Dadurch bleibt nicht nur das Interesse des Benutzers lang genug erhalten, dass dieser anspruchsvollere Features nutzt, sondern es werden ihm außerdem Kenntnisse über die Kernfunktionen der App vermittelt, auf denen der Benutzer bei der weiteren Nutzung der App aufbauen und dazulernen kann.</span><span class="sxs-lookup"><span data-stu-id="0d003-113">Not only does it keep the user engaged for long enough for them to use more advanced features, but it also provides them with knowledge of an app's core functions, which they can build upon as they continue to use the app and learn.</span></span>

## <a name="general-instructions"></a><span data-ttu-id="0d003-114">Allgemeine Hinweise</span><span class="sxs-lookup"><span data-stu-id="0d003-114">General instructions</span></span>

<span data-ttu-id="0d003-115">Ein Benutzer wird erst dann nach Hilfeinhalten suchen, wenn bereits ein Problem aufgetreten ist. Daher muss die Hilfe eine schnelle und effektive Lösung für das jeweilige Problem liefern.</span><span class="sxs-lookup"><span data-stu-id="0d003-115">A user will not look for help content unless they already have a problem, so help needs to provide a quick and effective answer to that problem.</span></span> <span data-ttu-id="0d003-116">Wenn Hilfe nicht auf Anhieb sinnvoll oder sie zu kompliziert ist, neigen Benutzer dazu, sie zu ignorieren.</span><span class="sxs-lookup"><span data-stu-id="0d003-116">If help is not immediately useful, or if help is too complicated, then users are more likely to ignore it.</span></span>

<span data-ttu-id="0d003-117">Jede Hilfe sollte unabhängig von ihrer Art folgenden Prinzipien entsprechen:</span><span class="sxs-lookup"><span data-stu-id="0d003-117">All help, no matter what kind, should follow these principles:</span></span>

-   <span data-ttu-id="0d003-118">**Leicht verständlich:** Hilfe, die den Benutzer verwirrt, ist schlimmer als gar keine Hilfe.</span><span class="sxs-lookup"><span data-stu-id="0d003-118">**Easy to understand:** Help that confuses the user is worse than no help at all.</span></span>

-   <span data-ttu-id="0d003-119">**Geradlinig:** Benutzer, die Hilfe benötigen, möchten klare Antworten, die ihnen direkt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0d003-119">**Straightforward:** Users looking for help want clear answers presented directly to them.</span></span>

-   <span data-ttu-id="0d003-120">**Relevant:** Benutzer möchten nicht nach ihrem spezifischen Problem suchen müssen.</span><span class="sxs-lookup"><span data-stu-id="0d003-120">**Relevant:** Users do not want to have to search for their specific issue.</span></span> <span data-ttu-id="0d003-121">Sie möchten, dass ihnen möglichst relevante Hilfe unmittelbar angezeigt wird (man spricht von „kontextbezogener Hilfe“), oder sie möchten eine leicht zu bedienende Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="0d003-121">They want the most relevant help presented straight to them (this is called "Contextual Help"), or they want an easily navigated interface.</span></span>

-   <span data-ttu-id="0d003-122">**Direkt:** Wenn ein Benutzer nach Hilfe sucht, möchte er auch Hilfe bekommen.</span><span class="sxs-lookup"><span data-stu-id="0d003-122">**Direct:** When a user looks for help, they want to see help.</span></span> <span data-ttu-id="0d003-123">Enthält die App Seiten zum Melden von Fehlern, für Feedback, zum Anzeigen der Nutzungsbedingungen oder ähnliche Funktionen, ist es in Ordnung, wenn diese Seiten über die Hilfe aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="0d003-123">If your app includes pages for reporting bugs, giving feedback, viewing term of service, or similar functions, it is fine if your help links to those pages.</span></span> <span data-ttu-id="0d003-124">Aber sie sollten eine untergeordnete Position auf der Haupthilfeseite und nicht den gleichen oder einen höheren Stellenwert haben.</span><span class="sxs-lookup"><span data-stu-id="0d003-124">But they should be included as an afterthought on the main help page, and not as items of equal or greater importance.</span></span>

-   <span data-ttu-id="0d003-125">**Konsistent:** Die Hilfe ist unabhängig von ihrer Art ein Teil der App und sollte wie jeder andere Teil der Benutzeroberfläche behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="0d003-125">**Consistent:** No matter the type, help is still a part of your app, and should be treated as any other part of the UI.</span></span> <span data-ttu-id="0d003-126">Für die von Ihnen angebotene Hilfe sollten die gleichen Gestaltungsprinzipien gelten wie für die eigentliche App, nämlich Benutzerfreundlichkeit, Barrierefreiheit und Stil.</span><span class="sxs-lookup"><span data-stu-id="0d003-126">The same design principles of usability, accessibility, and style which are used throughout the rest of your app should also be present in the help you offer.</span></span>

## <a name="types-of-help"></a><span data-ttu-id="0d003-127">Arten von Hilfe</span><span class="sxs-lookup"><span data-stu-id="0d003-127">Types of help</span></span>

<span data-ttu-id="0d003-128">Es gibt drei grundlegende Kategorien von Hilfeinhalten, die jeweils mit unterschiedlichen Stärken verbunden sind und sich für unterschiedliche Zwecke eignen.</span><span class="sxs-lookup"><span data-stu-id="0d003-128">There are three primary categories of help content, each with varying strengths and suitable for different purposes.</span></span> <span data-ttu-id="0d003-129">Verwenden Sie in der App je nach Bedarf eine beliebige Kombination dieser Kategorien.</span><span class="sxs-lookup"><span data-stu-id="0d003-129">Use any combination of them in your app, depending on your needs.</span></span>

#### <a name="instructional-ui"></a><span data-ttu-id="0d003-130">Benutzeroberfläche mit Anleitungen</span><span class="sxs-lookup"><span data-stu-id="0d003-130">Instructional UI</span></span>

<span data-ttu-id="0d003-131">In der Regel sollten Benutzer die Kernfunktionen der App ohne Anweisungen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="0d003-131">Normally, users should be able to use all the core functions of your app without instruction.</span></span> <span data-ttu-id="0d003-132">Aber manchmal ist bei der App eine bestimmte Geste erforderlich, oder möglicherweise gibt es sekundäre Features, die nicht sofort offensichtlich sind.</span><span class="sxs-lookup"><span data-stu-id="0d003-132">But sometimes, your app will depend on use of a specific gesture, or there may be secondary features of your app which are not immediately obvious.</span></span> <span data-ttu-id="0d003-133">In diesem Fall sollte die Benutzeroberfläche Anweisungen enthalten, die Benutzern erklären, wie bestimmte Aufgaben ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0d003-133">In this case, instructional UI should be used to educate users with instructions on how to perform specific tasks.</span></span>

[<span data-ttu-id="0d003-134">Siehe „Richtlinien für Anweisungen auf Benutzeroberflächen“</span><span class="sxs-lookup"><span data-stu-id="0d003-134">See guidelines for instructional UI</span></span>](instructional-ui.md)

#### <a name="in-app-help"></a><span data-ttu-id="0d003-135">In-App-Hilfe</span><span class="sxs-lookup"><span data-stu-id="0d003-135">In-app help</span></span>

<span data-ttu-id="0d003-136">Die Standardmethode zur Darstellung von Hilfe ist das Anzeigen der Hilfe innerhalb der Anwendung auf Anforderung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="0d003-136">The standard method of presenting help is to display it within the application at the user's request.</span></span> <span data-ttu-id="0d003-137">Es gibt verschiedene Möglichkeiten, dies umzusetzen, z.B. durch Hilfeseiten oder informative Beschreibungen.</span><span class="sxs-lookup"><span data-stu-id="0d003-137">There are several ways in which this can be implemented, such as in help pages or informative descriptions.</span></span> <span data-ttu-id="0d003-138">Diese Methode ist ideal für allgemeine Hilfe, die Fragen eines Benutzers unkompliziert und unmittelbar beantwortet.</span><span class="sxs-lookup"><span data-stu-id="0d003-138">This method is ideal for general-purpose help, that directly answers a user's questions without complexity.</span></span>

[<span data-ttu-id="0d003-139">Siehe „Richtlinien für In-App-Hilfe“</span><span class="sxs-lookup"><span data-stu-id="0d003-139">See guidelines for in-app help</span></span>](in-app-help.md)

#### <a name="external-help"></a><span data-ttu-id="0d003-140">Externe Hilfe</span><span class="sxs-lookup"><span data-stu-id="0d003-140">External help</span></span>

<span data-ttu-id="0d003-141">Für ausführliche Lernprogramme, erweiterte Funktionen oder Bibliotheken mit Hilfethemen, die zu groß für die Anwendung sind, sind Links zu externen Webseiten ideal.</span><span class="sxs-lookup"><span data-stu-id="0d003-141">For detailed tutorials, advanced functions, or libraries of help topics too large to fit within your application, links to external web pages are ideal.</span></span> <span data-ttu-id="0d003-142">Diese Links sollten nach Möglichkeit sparsam verwendet werden, da sie die Anwendungsnutzung durch den Benutzer unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="0d003-142">These links should be used sparingly if possible, as they remove the user from the application experience.</span></span>

[<span data-ttu-id="0d003-143">Siehe „Richtlinien für externe Hilfe“</span><span class="sxs-lookup"><span data-stu-id="0d003-143">See guidelines for external help</span></span>](external-help.md)


