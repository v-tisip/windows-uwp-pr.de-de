---
author: QuinnRadich
Description: Design external help pages for detailed instructions and advice about your app.
title: Richtlinien zum Entwerfen von externen Hilfeseiten
label: External help
template: detail.hbs
ms.author: quradic
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: 56afd553-c520-4a28-b63d-2e1b3c1d3606
ms.localizationpriority: medium
ms.openlocfilehash: 88e6fb03ccefca0e6067db58b9343ee76fa72ba3
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6039252"
---
# <a name="external-help-pages"></a><span data-ttu-id="f0df6-103">Externe Hilfeseiten</span><span class="sxs-lookup"><span data-stu-id="f0df6-103">External help pages</span></span>



<span data-ttu-id="f0df6-104">Wenn für Ihre App eine ausführliche Hilfe für komplexe Inhalte erforderlich ist, sollten Sie diese Anweisungen auf einer Webseite hosten.</span><span class="sxs-lookup"><span data-stu-id="f0df6-104">If your app requires detailed help for complex content, consider hosting these instructions on a web page.</span></span>

## <a name="when-to-use-external-help-pages"></a><span data-ttu-id="f0df6-105">Gründe für die Verwendung von externen Hilfeseiten</span><span class="sxs-lookup"><span data-stu-id="f0df6-105">When to use external help pages</span></span>

<span data-ttu-id="f0df6-106">Externe Hilfeseiten sind für die allgemeine Verwendung oder als Kurzreferenz eher unpraktisch.</span><span class="sxs-lookup"><span data-stu-id="f0df6-106">External help pages are less convenient for general use or quick reference.</span></span> <span data-ttu-id="f0df6-107">Sie eignen sich für Hilfeinhalte, die für die Einbindung in die App selbst zu umfangreich sind, sowie für Lernprogramme und Anweisungen für erweiterte Funktionen einer App, die die allgemeinen Benutzer nicht benötigen.</span><span class="sxs-lookup"><span data-stu-id="f0df6-107">They are suitable for help content that is too extensive to be incorporated into the app itself, as well as for tutorials and instructions for advanced functions of an app that won't be used by its general audience.</span></span>

<span data-ttu-id="f0df6-108">Wenn die Inhalte der Hilfe kurz oder spezifisch genug sind, um sie in der App anzuzeigen, sollten Sie dies vorziehen.</span><span class="sxs-lookup"><span data-stu-id="f0df6-108">If your help content is brief or specific enough to be displayed in-app, you should do so.</span></span> <span data-ttu-id="f0df6-109">Leiten Sie die Benutzer für Anweisungen nur dann zu Zielen außerhalb der App weiter, wenn dies unbedingt nötig ist.</span><span class="sxs-lookup"><span data-stu-id="f0df6-109">Do not direct users outside of the app for help unless it is necessary.</span></span>

## <a name="navigating-external-help-pages"></a><span data-ttu-id="f0df6-110">Navigation auf externen Hilfeseiten</span><span class="sxs-lookup"><span data-stu-id="f0df6-110">Navigating external help pages</span></span>

<span data-ttu-id="f0df6-111">Wenn ein Benutzer zu einer externen Hilfeseite weitergeleitet wird, halten Sie sich an eines von zwei Szenarien:</span><span class="sxs-lookup"><span data-stu-id="f0df6-111">When a user is directed to an external help page, follow one of two scenarios:</span></span>
-   <span data-ttu-id="f0df6-112">Er wird direkt auf die Seite geführt, die dem bekannten Problem zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="f0df6-112">They are linked directly to the page that corresponds with their known issue.</span></span> <span data-ttu-id="f0df6-113">Dies ist die kontextbezogene Hilfe und sollte wann immer möglich verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f0df6-113">This is contextual help, and should be used when possible.</span></span>
-   <span data-ttu-id="f0df6-114">Er wird zu einer allgemeinen Hilfeseite geleitet, auf der übersichtlich Kategorien und Unterkategorien zur Auswahl angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="f0df6-114">They are linked to a general help page, with a clear display of categories and subcategories to choose from.</span></span>

<span data-ttu-id="f0df6-115">Es kann hilfreich sein, für die Benutzer eine Möglichkeit zum Durchsuchen der Hilfe bereitzustellen, diese Suche sollte jedoch nicht die einzige Möglichkeit für die Navigation in der Hilfe darstellen.</span><span class="sxs-lookup"><span data-stu-id="f0df6-115">Providing users with a way to search your help can be useful, but do not make this search the only way of navigating your help.</span></span> <span data-ttu-id="f0df6-116">In einigen Fällen ist es für die Benutzer schwierig, ihre Probleme zu beschreiben, was die Suche erschweren kann.</span><span class="sxs-lookup"><span data-stu-id="f0df6-116">It can sometimes be difficult for users to describe their problems, which can make searching difficult.</span></span> <span data-ttu-id="f0df6-117">Die Benutzer sollten schnell die relevanten Seiten für ihre Probleme finden können, ohne sie suchen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="f0df6-117">Users should be able to quickly find pages relevant to their problems without needing to search.</span></span>

## <a name="tutorials-and-detailed-walkthroughs"></a><span data-ttu-id="f0df6-118">Lernprogramme und ausführliche exemplarische Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="f0df6-118">Tutorials and detailed walkthroughs</span></span>

<span data-ttu-id="f0df6-119">Externe Hilfeseiten sind ideal, um für die Benutzer Lernprogramme und exemplarische Vorgehensweisen in Video- oder Textform bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f0df6-119">External help pages are the ideal place to provide users with tutorials and walkthroughs, whether video or textual.</span></span>
-   <span data-ttu-id="f0df6-120">Der Schwerpunkt von Lernprogrammen sollte auf komplizierteren Konzepten und erweiterten Funktionen liegen.</span><span class="sxs-lookup"><span data-stu-id="f0df6-120">Tutorials should focus on more complicated ideas and advanced functions.</span></span> <span data-ttu-id="f0df6-121">Die Benutzer sollten kein Lernprogramm benötigen, um Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f0df6-121">Users shouldn't need a tutorial to use your app.</span></span>
-   <span data-ttu-id="f0df6-122">Achten Sie darauf, dass diese Lernprogramme sich von den Standardanweisungen in der Hilfe abheben.</span><span class="sxs-lookup"><span data-stu-id="f0df6-122">Make sure that these tutorials are displayed differently from standard help instructions.</span></span> <span data-ttu-id="f0df6-123">Benutzer, die detailliertere Anweisungen benötigen, sind eher bereit, diese zu suchen, als Benutzer, die einfache Lösungen für ihre Probleme suchen.</span><span class="sxs-lookup"><span data-stu-id="f0df6-123">Users who are looking for advanced instructions are more eager to search for them than users who want straightforward solutions to their problems.</span></span>
-   <span data-ttu-id="f0df6-124">Sie sollten Lernprogramme über ein Verzeichnis und von einzelnen Hilfeseiten verknüpfen, die dem jeweiligen Lernprogramm entsprechen.</span><span class="sxs-lookup"><span data-stu-id="f0df6-124">Consider linking to tutorials from both a directory and from individual help pages that correspond to each tutorial.</span></span>

## <a name="related-articles"></a><span data-ttu-id="f0df6-125">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="f0df6-125">Related articles</span></span>

* [<span data-ttu-id="f0df6-126">Anleitungen für die App-Hilfe</span><span class="sxs-lookup"><span data-stu-id="f0df6-126">Guidelines for app help</span></span>](guidelines-for-app-help.md)
