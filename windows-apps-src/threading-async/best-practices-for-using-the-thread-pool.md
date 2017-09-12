---
author: normesta
ms.assetid: 95CF7F3D-9E3A-40AC-A083-D8A375272181
title: "Bewährte Methoden zum Verwenden des Threadpools"
description: "In diesem Thema werden bewährte Methoden für die Verwendung des Threadpools beschrieben."
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Thread, Threadpool
ms.openlocfilehash: e4203a613fdc1af64a8234ac6fef6b248c01e15c
ms.sourcegitcommit: 378382419f1fda4e4df76ffa9c8cea753d271e6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="best-practices-for-using-the-thread-pool"></a><span data-ttu-id="69ab9-104">Bewährte Methoden zum Verwenden des Threadpools</span><span class="sxs-lookup"><span data-stu-id="69ab9-104">Best practices for using the thread pool</span></span>

<span data-ttu-id="69ab9-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="69ab9-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="69ab9-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="69ab9-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="69ab9-107">In diesem Thema werden bewährte Methoden für die Verwendung des Threadpools beschrieben.</span><span class="sxs-lookup"><span data-stu-id="69ab9-107">This topic describes best practices for working with the thread pool.</span></span>

## <a name="dos"></a><span data-ttu-id="69ab9-108">Empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="69ab9-108">Do's</span></span>


-   <span data-ttu-id="69ab9-109">Verwenden Sie den Threadpool, um parallele Vorgänge in Ihrer App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="69ab9-109">Use the thread pool to do parallel work in your app.</span></span>

-   <span data-ttu-id="69ab9-110">Verwenden Sie Arbeitsaufgaben, um längere Aufgaben auszuführen, ohne den UI-Thread zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="69ab9-110">Use work items to accomplish extended tasks without blocking the UI thread.</span></span>

-   <span data-ttu-id="69ab9-111">Erstellen Sie kurzlebige und unabhängige Arbeitsaufgaben.</span><span class="sxs-lookup"><span data-stu-id="69ab9-111">Create work items that are short-lived and independent.</span></span> <span data-ttu-id="69ab9-112">Arbeitsaufgaben werden asynchron ausgeführt und können in beliebiger Reihenfolge von der Warteschlange an den Pool gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="69ab9-112">Work items run asynchronously and they can be submitted to the pool in any order from the queue.</span></span>

-   <span data-ttu-id="69ab9-113">Verwenden Sie [**Windows.UI.Core.CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/BR208211), um Updates an den UI-Thread zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="69ab9-113">Dispatch updates to the UI thread with the [**Windows.UI.Core.CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/BR208211).</span></span>

-   <span data-ttu-id="69ab9-114">Verwenden Sie [**ThreadPoolTimer.CreateTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967921) anstelle der **Sleep**-Funktion.</span><span class="sxs-lookup"><span data-stu-id="69ab9-114">Use [**ThreadPoolTimer.CreateTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967921) instead of the **Sleep** function.</span></span>

-   <span data-ttu-id="69ab9-115">Verwenden Sie den Threadpool, anstatt ein eigenes Threadverwaltungssystem zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="69ab9-115">Use the thread pool instead of creating your own thread management system.</span></span> <span data-ttu-id="69ab9-116">Der Threadpool wird auf Betriebssystemebene ausgeführt, bietet erweiterte Funktionen und ist für die dynamische Skalierung je nach Geräteressourcen und Aktivitäten innerhalb des Prozesses und im gesamten System optimiert.</span><span class="sxs-lookup"><span data-stu-id="69ab9-116">The thread pool runs at the OS level with advanced capability and is optimized to dynamically scale according to device resources and activity within the process and across the system.</span></span>

-   <span data-ttu-id="69ab9-117">Stellen Sie in C++ sicher, dass Arbeitsaufgabendelegate das Agile-Threadingmodell verwenden (C++-Delegate sind standardmäßig agil).</span><span class="sxs-lookup"><span data-stu-id="69ab9-117">In C++, ensure that work item delegates use the agile threading model (C++ delegates are agile by default).</span></span>

-   <span data-ttu-id="69ab9-118">Verwenden Sie vorab zugeordnete Arbeitsaufgaben, wenn Sie einen Fehler bei der Ressourcenzuweisung zum Zeitpunkt der Verwendung nicht tolerieren können.</span><span class="sxs-lookup"><span data-stu-id="69ab9-118">Use pre-allocated work items when you can't tolerate a resource allocation failure at time of use.</span></span>

## <a name="donts"></a><span data-ttu-id="69ab9-119">Nicht empfohlene Aktionen</span><span class="sxs-lookup"><span data-stu-id="69ab9-119">Dont's</span></span>


-   <span data-ttu-id="69ab9-120">Erstellen Sie keine regelmäßigen Timer mit einem *period*-Wert von &lt;1 Millisekunde (einschließlich0).</span><span class="sxs-lookup"><span data-stu-id="69ab9-120">Don't create periodic timers with a *period* value of &lt;1 millisecond (including 0).</span></span> <span data-ttu-id="69ab9-121">Andernfalls verhält sich die Arbeitsaufgabe wie ein einmaliger Timer.</span><span class="sxs-lookup"><span data-stu-id="69ab9-121">This will cause the work item to behave as a single-shot timer.</span></span>

-   <span data-ttu-id="69ab9-122">Senden Sie keine regelmäßigen Arbeitsaufgaben, deren Ausführung länger dauert als die im *period*-Parameter festgelegte Dauer.</span><span class="sxs-lookup"><span data-stu-id="69ab9-122">Don't submit periodic work items that take longer to complete than the amount of time you specified in the *period* parameter.</span></span>

-   <span data-ttu-id="69ab9-123">Senden Sie keine Benutzeroberflächenaktualisierungen (mit Ausnahme von Popups und Benachrichtigungen) von einer Arbeitsaufgabe, die von einer Hintergrundaufgabe übermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="69ab9-123">Don't try to send UI updates (other than toasts and notifications) from a work item dispatched from a background task.</span></span> <span data-ttu-id="69ab9-124">Verwenden Sie stattdessen Status- und Abschlusshandler für Hintergrundaufgaben, z.B. [**IBackgroundTaskInstance.Progress**](https://msdn.microsoft.com/library/windows/apps/BR224800).</span><span class="sxs-lookup"><span data-stu-id="69ab9-124">Instead, use background task progress and completion handlers - for example, [**IBackgroundTaskInstance.Progress**](https://msdn.microsoft.com/library/windows/apps/BR224800).</span></span>

-   <span data-ttu-id="69ab9-125">Beachten Sie bei der Verwendung von Arbeitsaufgabenhandlern mit dem **async**-Schlüsselwort, dass die Threadpool-Arbeitsaufgabe möglicherweise vor der Ausführung des gesamten Codes im Ereignishandler auf den Status „Abgeschlossen“ gesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="69ab9-125">When you use work-item handlers that use the **async** keyword, be aware that the thread pool work item may be set to the complete state before all of the code in the handler has executed.</span></span> <span data-ttu-id="69ab9-126">Code, der innerhalb des Handlers auf ein **await**-Schlüsselwort folgt, kann ausgeführt werden, nachdem die Arbeitsaufgabe auf den Status „Abgeschlossen“ gesetzt wurde.</span><span class="sxs-lookup"><span data-stu-id="69ab9-126">Code following an **await** keyword within the handler may execute after the work item has been set to the complete state.</span></span>

-   <span data-ttu-id="69ab9-127">Führen Sie eine vorab zugeordnete Arbeitsaufgabe nicht mehrmals aus, ohne sie erneut zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="69ab9-127">Don't try to run a pre-allocated work item more than once without reinitializing it.</span></span> [<span data-ttu-id="69ab9-128">Erstellen einer regelmäßigen Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="69ab9-128">Create a periodic work item</span></span>](create-a-periodic-work-item.md)

## <a name="related-topics"></a><span data-ttu-id="69ab9-129">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="69ab9-129">Related topics</span></span>


* [<span data-ttu-id="69ab9-130">Erstellen einer regelmäßigen Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="69ab9-130">Create a periodic work item</span></span>](create-a-periodic-work-item.md)
* [<span data-ttu-id="69ab9-131">Senden einer Arbeitsaufgabe an den Threadpool</span><span class="sxs-lookup"><span data-stu-id="69ab9-131">Submit a work item to the thread pool</span></span>](submit-a-work-item-to-the-thread-pool.md)
* [<span data-ttu-id="69ab9-132">Senden einer Arbeitsaufgabe mithilfe eines Timers</span><span class="sxs-lookup"><span data-stu-id="69ab9-132">Use a timer to submit a work item</span></span>](use-a-timer-to-submit-a-work-item.md)
