---
author: QuinnRadich
Description: Design effective help to be displayed reactively inside your app.
title: Richtlinien zum Entwerfen von In-App-Hilfe.
label: In-app help
template: detail.hbs
ms.author: quradic
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.assetid: 6208b71b-37a7-40f5-91b0-19b665e7458a
ms.localizationpriority: medium
ms.openlocfilehash: 089b71464234abe21d7dc8613d46ef6778f0f5a6
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5823550"
---
# <a name="in-app-help-pages"></a><span data-ttu-id="c1bdd-103">In-App-Hilfeseiten</span><span class="sxs-lookup"><span data-stu-id="c1bdd-103">In-app help pages</span></span>

<span data-ttu-id="c1bdd-104">In den meisten Fällen empfiehlt es sich, dass die Hilfe in der Anwendung angezeigt wird, wenn der Benutzer dies wünscht.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-104">Most of the time, it is best that help be displayed within the application and when the user chooses to view it.</span></span>

## <a name="when-to-use-in-app-help-pages"></a><span data-ttu-id="c1bdd-105">Gründe für die Verwendung von In-App-Hilfeseiten</span><span class="sxs-lookup"><span data-stu-id="c1bdd-105">When to use in-app help pages</span></span>

<span data-ttu-id="c1bdd-106">Die Hilfe für den Benutzer sollte standardmäßig als In-App-Hilfe angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-106">In-app help should be the default method of displaying help for the user.</span></span> <span data-ttu-id="c1bdd-107">Sie sollte für jede Hilfe eingesetzt werden, die einfach und unkompliziert ist und dem Benutzer keine neuen Inhalte vermittelt.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-107">It should be used for any help which is simple, straightforward, and does not introduce new content to the user.</span></span> <span data-ttu-id="c1bdd-108">Anweisungen, Ratschläge sowie Tipps & Tricks eignen sich für In-App-Hilfe.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-108">Instructions, advice, and tips & tricks are all suitable for in-app help.</span></span>

<span data-ttu-id="c1bdd-109">Komplexe Anweisungen oder Lernprogramme sind nicht schnell zu überblicken, und sie belegen viel Speicherplatz.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-109">Complex instructions or tutorials are not easy to reference quickly, and they take up large amounts of space.</span></span> <span data-ttu-id="c1bdd-110">Aus diesem Grund sollten sie extern gehostet und nicht in die App selbst integriert werden.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-110">Therefore, they should be hosted externally, and not incorporated into the app itself.</span></span>

<span data-ttu-id="c1bdd-111">Benutzer sollten nicht lange nach Hilfe für grundlegende Anweisungen oder nach neuen Features suchen müssen.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-111">Users should not have to seek out help for basic instructions or to discover new features.</span></span> <span data-ttu-id="c1bdd-112">Wenn Sie Hilfe benötigen, die den Benutzern Lerninhalte vermittelt, verwenden Sie Anweisungen auf der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-112">If you need to have help that educates users, use instructional UI.</span></span>

## <a name="types-of-in-app-help"></a><span data-ttu-id="c1bdd-113">Arten von In-App-Hilfe</span><span class="sxs-lookup"><span data-stu-id="c1bdd-113">Types of In-app help</span></span>

<span data-ttu-id="c1bdd-114">In-App-Hilfe kann unterschiedliche Formen annehmen, entspricht jedoch in Bezug auf Gestaltung und Benutzerfreundlichkeit den gleichen allgemeinen Grundsätzen.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-114">In-app help can come in several forms, though they all follow the same general principles of design and usability.</span></span>

#### <a name="help-pages"></a><span data-ttu-id="c1bdd-115">Hilfeseiten</span><span class="sxs-lookup"><span data-stu-id="c1bdd-115">Help Pages</span></span>

<span data-ttu-id="c1bdd-116">Nützliche Anweisungen können schnell und einfach auf einer oder mehreren separaten Hilfeseiten in Ihrer App angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-116">Having a separate page or pages of help within your app is a quick and easy way of displaying useful instructions.</span></span>

-   <span data-ttu-id="c1bdd-117">**Präzise sein:** Eine umfangreiche Bibliothek mit Hilfethemen ist umständlich und für eine In-App-Hilfe nicht geeignet.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-117">**Be concise:** A large library of help topics is unwieldy and unsuited for in-app help.</span></span>
-   <span data-ttu-id="c1bdd-118">**Seien Sie konsistent:** Stellen Sie sicher, dass Benutzer die Hilfeseiten in jedem Bereich der App auf die gleiche Weise aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-118">**Be consistent:** Make sure that users can reach your help pages the same way from any part of your app.</span></span> <span data-ttu-id="c1bdd-119">Sie sollten nie danach suchen müssen.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-119">They should never have to search for it.</span></span>
-   <span data-ttu-id="c1bdd-120">**Benutzer überfliegen Inhalte, anstatt sie zu lesen:** Da sich das Hilfethema, nach dem ein Benutzer sucht, möglicherweise auf derselben Seite wie andere Hilfethemen befindet, müssen Sie darauf achten, dass das gesuchte Hilfethema leicht zu erkennen ist.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-120">**Users scan, not read:** Because the help a user is looking for might be on the same page as other help topics, make sure they can easily tell which one they need to focus on.</span></span>


#### <a name="popups"></a><span data-ttu-id="c1bdd-121">Popups</span><span class="sxs-lookup"><span data-stu-id="c1bdd-121">Popups</span></span>

<span data-ttu-id="c1bdd-122">Popups bieten die Möglichkeit, stark kontextbezogene Hilfe einzublenden. Das heißt, es werden Anweisungen und Ratschläge angezeigt, die für die jeweilige Aufgabe des Benutzers relevant sind.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-122">Popups allow for highly contexual help, displaying instructions and advice that is relevant to the specific task that the user is attempting.</span></span>

-   <span data-ttu-id="c1bdd-123">**Auf ein Thema konzentrieren:** Ein Popup bietet noch weniger Platz als eine Hilfeseite.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-123">**Focus on one issue:** Space is even more restricted in a popup than a help page.</span></span> <span data-ttu-id="c1bdd-124">Hilfepopups müssen sich speziell auf eine einzelne Aufgabe beziehen, damit sie effektiv sind.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-124">Help popups needs to refer specifically a single task to be effective.</span></span>
-   <span data-ttu-id="c1bdd-125">**Sichtbarkeit ist wichtig:** Da Hilfepopups nur an einer Stelle angezeigt werden können, müssen Sie sicherstellen, dass sie für die Benutzer deutlich sichtbar sind, ohne zu stören.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-125">**Visibility is important:** Because help popups can only be viewed from one location, make sure that they're clearly visible to the user without being obstructive.</span></span> <span data-ttu-id="c1bdd-126">Wenn der Benutzer das Popup nicht sieht, ignoriert er es womöglich und sucht nach einer Hilfeseite.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-126">If the user misses it, they might move away from the popup in search of a help page.</span></span>
-   <span data-ttu-id="c1bdd-127">**Beanspruchen Sie nicht zu viele Ressourcen:** Die Hilfe sollte keine Verzögerungen verursachen oder langsam geladen werden.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-127">**Don't use too many resources:** Help shouldn't lag or be slow-loading.</span></span> <span data-ttu-id="c1bdd-128">Popups mit Videos oder Audiodateien oder Bildern mit hoher Auflösung führen beim Benutzer eher zur Verärgerung anstatt ihm zu helfen.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-128">Using videos or audio files or high resolution images in popups is more likely to frustrate the user than it is to help them.</span></span>

#### <a name="descriptions"></a><span data-ttu-id="c1bdd-129">Beschreibungen</span><span class="sxs-lookup"><span data-stu-id="c1bdd-129">Descriptions</span></span>

<span data-ttu-id="c1bdd-130">In manchen Fällen kann es hilfreich sein, weitere Informationen zu einem Feature bereitzustellen, wenn ein Benutzer es prüft.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-130">Sometimes, it can be useful to provide more information about a feature when a user inspects it.</span></span> <span data-ttu-id="c1bdd-131">Beschreibungen ähneln Anweisungen auf der Benutzeroberfläche. Doch der Hauptunterschied besteht darin, dass Anweisungen auf der Benutzeroberfläche versuchen, dem Benutzer Lerninhalte zu Features zu vermitteln, die er noch nicht kennt. Eine ausführliche Beschreibung dagegen vertieft die Kenntnisse des Benutzers über App-Features, an denen er bereits interessiert ist.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-131">Descriptions are similar to instructive UI, but the key difference is that instructional UI attempts to teach and educate the user about features that they don't know about, whereas detailed descriptions enhance a user's understanding of app features that they're already interested in.</span></span>

-   <span data-ttu-id="c1bdd-132">**Keine Grundlagen vermitteln:** Gehen Sie davon aus, dass der Benutzer grundsätzlich bereits weiß, wie das beschriebene Element verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-132">**Don't teach the basics:** Assume that the user already knows the fundamentals of how to use the item being described.</span></span> <span data-ttu-id="c1bdd-133">In dem Fall ist es hilfreich, etwas zu verdeutlichen oder weitere Informationen anzubieten.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-133">Clarifying or offering further information is useful.</span></span> <span data-ttu-id="c1bdd-134">Bereits Bekanntes zu vermitteln ist dagegen nicht sinnvoll.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-134">Telling them what they already know is not.</span></span>
-   <span data-ttu-id="c1bdd-135">**Beschreiben Sie interessante Interaktionen:** Beschreibungen sind ideal geeignet, um Benutzern zu zeigen, wie diesen bereits bekannte Features interagieren können.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-135">**Describe interesting interactions:** One of the best uses for descriptions is to educate the user on how a features that they already know about can interact.</span></span> <span data-ttu-id="c1bdd-136">Dadurch erfahren die Benutzer mehr über Funktionen, die sie bereits gerne verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-136">This helps users learn more about things they already like to use.</span></span>
-   <span data-ttu-id="c1bdd-137">**Stören Sie nicht:** Ähnlich wie Anweisungen in der Benutzeroberfläche dürfen Beschreibungen die Nutzung der App durch die Benutzer nicht behindern.</span><span class="sxs-lookup"><span data-stu-id="c1bdd-137">**Stay out of the way:** Much like instructional UI, descriptions need to avoid interfering with a user's enjoyment of the app.</span></span>

## <a name="related-articles"></a><span data-ttu-id="c1bdd-138">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c1bdd-138">Related articles</span></span>

* [<span data-ttu-id="c1bdd-139">Anleitungen für die App-Hilfe</span><span class="sxs-lookup"><span data-stu-id="c1bdd-139">Guidelines for app help</span></span>](guidelines-for-app-help.md)
