---
author: jnHs
Description: Review this list to help avoid issues that frequently prevent apps from getting certified, or that might be identified during a spot check after the app is published.
title: Vermeiden allgemeiner Zertifizierungsfehler
ms.assetid: 9E9E3841-2F9B-42D4-B5F8-4C7C31E42E3D
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 283856ad163d2e67078c61559f6f8ec667e92b87
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4503811"
---
# <a name="avoid-common-certification-failures"></a><span data-ttu-id="17786-103">Vermeiden allgemeiner Zertifizierungsfehler</span><span class="sxs-lookup"><span data-stu-id="17786-103">Avoid common certification failures</span></span>


<span data-ttu-id="17786-104">Lesen Sie diese Liste, und vermeiden Sie dadurch Probleme, die häufig die Zertifizierung von Apps verhindern oder nach der Veröffentlichung der App bei einer Stichprobenkontrolle auftreten können.</span><span class="sxs-lookup"><span data-stu-id="17786-104">Review this list to help avoid issues that frequently prevent apps from getting certified, or that might be identified during a spot check after the app is published.</span></span>

> [!NOTE]
> <span data-ttu-id="17786-105">Achten Sie darauf, überprüfen Sie die [Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies) , um sicherzustellen, dass Ihre app alle darin aufgeführten Anforderungen erfüllt.</span><span class="sxs-lookup"><span data-stu-id="17786-105">Be sure to review the [Microsoft Store Policies](https://docs.microsoft.com/legal/windows/agreements/store-policies) to ensure your app meets all of the requirements listed there.</span></span>

-   <span data-ttu-id="17786-106">Reichen Sie die App erst ein, wenn sie fertig ist.</span><span class="sxs-lookup"><span data-stu-id="17786-106">Submit your app only when it's finished.</span></span> <span data-ttu-id="17786-107">Sie können die Beschreibung Ihrer App gern nutzen, um auf geplante Features hinzuweisen. Achten Sie jedoch darauf, dass Ihre App keine unvollständigen Abschnitte, Links zu unfertigen Webseiten oder andere Elemente enthält, die Kunden darauf schließen lassen, dass sich die App in einem unvollständigen Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="17786-107">You're welcome to use your app's description to mention upcoming features, but make sure that your app doesn't contain incomplete sections, links to web pages that are under construction, or anything else that would give a customer the impression that your app is incomplete.</span></span>

-   <span data-ttu-id="17786-108">[Testen Sie die App vor dem Einreichen mit dem Zertifizierungskit für Windows-Apps](../debug-test-perf/windows-app-certification-kit.md).</span><span class="sxs-lookup"><span data-stu-id="17786-108">[Test your app with the Windows App Certification Kit](../debug-test-perf/windows-app-certification-kit.md) before you submit your app.</span></span>

-   <span data-ttu-id="17786-109">Testen Sie die App unter verschiedenen Konfigurationen, um größtmögliche Stabilität sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="17786-109">Test your app on several different configurations to ensure that it's as stable as possible.</span></span>

-   <span data-ttu-id="17786-110">Vergewissern Sie sich, dass die App nicht abstürzt, wenn keine Netzwerkkonnektivität besteht!</span><span class="sxs-lookup"><span data-stu-id="17786-110">Ensure that your app doesn't crash without network connectivity.</span></span> <span data-ttu-id="17786-111">Auch wenn für die eigentliche Verwendung der App eine Verbindung erforderlich ist, muss sie richtig ausgeführt werden, wenn keine Verbindung besteht.</span><span class="sxs-lookup"><span data-stu-id="17786-111">Even if a connection is required to actually use your app, it needs to perform appropriately when no connection is present.</span></span>

-   <span data-ttu-id="17786-112">[Stellen Sie die erforderlichen Infos](notes-for-certification.md) zum Verwenden der App bereit, z.B. Benutzername und Kennwort für ein Testkonto, wenn sich Benutzer bei einem Dienst anmelden müssen, oder geben Sie die erforderlichen Schritte zum Zugreifen auf versteckte oder gesperrte Features an.</span><span class="sxs-lookup"><span data-stu-id="17786-112">[Provide any necessary info](notes-for-certification.md) required to use your app, such as the user name and password for a test account if your app requires users to log in to a service, or any steps required to access hidden or locked features.</span></span>

-   <span data-ttu-id="17786-113">Fügen Sie eine [Datenschutzrichtlinie](create-app-store-listings.md#privacy-policy) hinzu, wenn Ihre App eine benötigt, z.B. wenn die App auf alle Arten von persönlichen Informationen zugreift oder dies anderweitig gesetzlich vorgeschrieben ist.</span><span class="sxs-lookup"><span data-stu-id="17786-113">Include a [privacy policy](create-app-store-listings.md#privacy-policy) if your app requires one; for example, if your app accesses any kind of personal information in any way or is otherwise required by law.</span></span> <span data-ttu-id="17786-114">Um zu ermitteln, ob Ihre app eine Datenschutzrichtlinie benötigt, überprüfen Sie die [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) und die [Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies).</span><span class="sxs-lookup"><span data-stu-id="17786-114">To help determine if your app requires a privacy policy, review the [App Developer Agreement](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) and the [Microsoft Store Policies](https://docs.microsoft.com/legal/windows/agreements/store-policies).</span></span>

-   <span data-ttu-id="17786-115">Formulieren Sie die Beschreibung der App so, dass sie den Funktionsumfang der App genau darstellt.</span><span class="sxs-lookup"><span data-stu-id="17786-115">Make sure that your app's description clearly represents what your app does.</span></span> <span data-ttu-id="17786-116">Unterstützung erhalten Sie in den Richtlinien zum [Verfassen einer ansprechenden App-Beschreibung](write-a-great-app-description.md).</span><span class="sxs-lookup"><span data-stu-id="17786-116">For help, see our guidance on [writing a great app description](write-a-great-app-description.md).</span></span>

-   <span data-ttu-id="17786-117">Beantworten Sie alle Fragen im Bereich [Altersfreigaben](age-ratings.md) vollständig und richtig.</span><span class="sxs-lookup"><span data-stu-id="17786-117">Provide complete and accurate responses to all of the questions in the [Age ratings](age-ratings.md) section.</span></span>

-   <span data-ttu-id="17786-118">[Deklarieren Sie die App nur dann als barrierefrei](app-declarations.md#this-app-has-been-tested-to-meet-accessibility-guidelines), wenn Sie sie ausdrücklich für Barrierefreiheitsszenarien entwickelt und getestet haben.</span><span class="sxs-lookup"><span data-stu-id="17786-118">Don't [declare your app as accessible](app-declarations.md#this-app-has-been-tested-to-meet-accessibility-guidelines) unless you have specifically engineered and tested it for accessibility scenarios.</span></span>

-   <span data-ttu-id="17786-119">Wenn die App die E-Commerce-APIs für den Windows Store aus dem [**Windows.ApplicationModel.Store**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store)-Namespace verwendet, müssen Sie die App testen und sich vergewissern, dass sie typische Ausnahmen behandelt.</span><span class="sxs-lookup"><span data-stu-id="17786-119">If your app uses the commerce APIs from the [**Windows.ApplicationModel.Store**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store) namespace, make sure to test the app and verify that it handles typical exceptions.</span></span> <span data-ttu-id="17786-120">Stellen Sie außerdem sicher, dass die App die [**CurrentApp**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentApp)-Klasse verwendet und nicht die [**CurrentAppSimulator**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentAppSimulator)-Klasse, die nur zu Testzwecken gedacht ist.</span><span class="sxs-lookup"><span data-stu-id="17786-120">Also, make sure that your app uses the [**CurrentApp**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentApp) class and not the [**CurrentAppSimulator**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentAppSimulator) class, which is for testing purposes only.</span></span> <span data-ttu-id="17786-121">(Wenn Ihre App auf Windows10, Version1607 oder höher ausgerichtet ist, wird empfohlen, Mitglieder des [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace statt des Windows.ApplicationModel.Store-Namespace zu verwenden).</span><span class="sxs-lookup"><span data-stu-id="17786-121">(Note that if your app targets Windows 10, version 1607 or later, we recommend that you use members of the [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) namespace instead of the Windows.ApplicationModel.Store namespace.)</span></span>


 

 




