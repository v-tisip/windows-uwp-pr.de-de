---
author: normesta
ms.assetid: E2A1200C-9583-40FA-AE4D-C9E6F6C32BCF
title: Senden einer Arbeitsaufgabe an den Threadpool
description: Hier erfahren Sie, wie Sie Arbeit in einem separaten Thread erledigen können, indem Sie eine Arbeitsaufgabe an den Threadpool übermitteln.
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Threads, Threadpool
ms.localizationpriority: medium
ms.openlocfilehash: 29d7fc361e446207c8e14f83ca3f663bd5072e6e
ms.sourcegitcommit: 63cef0a7805f1594984da4d4ff2f76894f12d942
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2018
ms.locfileid: "4393758"
---
# <a name="submit-a-work-item-to-the-thread-pool"></a><span data-ttu-id="03818-104">Übermitteln einer Arbeitsaufgabe an den Threadpool</span><span class="sxs-lookup"><span data-stu-id="03818-104">Submit a work item to the thread pool</span></span>

<span data-ttu-id="03818-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="03818-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="03818-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="03818-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="03818-107">\*\* Wichtige APIs \*\*</span><span class="sxs-lookup"><span data-stu-id="03818-107">\*\* Important APIs \*\*</span></span>

-   [**<span data-ttu-id="03818-108">RunAsync</span><span class="sxs-lookup"><span data-stu-id="03818-108">RunAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR230593)
-   [**<span data-ttu-id="03818-109">IAsyncAction</span><span class="sxs-lookup"><span data-stu-id="03818-109">IAsyncAction</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206580)

<span data-ttu-id="03818-110">Hier erfahren Sie, wie Sie Arbeit in einem separaten Thread erledigen können, indem Sie eine Arbeitsaufgabe an den Threadpool übermitteln.</span><span class="sxs-lookup"><span data-stu-id="03818-110">Learn how to do work in a separate thread by submitting a work item to the thread pool.</span></span> <span data-ttu-id="03818-111">Somit sorgen Sie dafür, dass die Benutzeroberfläche bei der Erledigung von Arbeit, die viel Zeit in Anspruch nimmt, reaktionsfähig bleibt, und Sie können mehrere Aufgaben parallel bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="03818-111">Use this to maintain a responsive UI while still completing work that takes a noticeable amount of time, and use it to complete multiple tasks in parallel.</span></span>

## <a name="create-and-submit-the-work-item"></a><span data-ttu-id="03818-112">Erstellen und Senden der Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="03818-112">Create and submit the work item</span></span>

<span data-ttu-id="03818-113">Erstellen Sie eine Arbeitsaufgabe, indem Sie [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/BR230593) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="03818-113">Create a work item by calling [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/BR230593).</span></span> <span data-ttu-id="03818-114">Stellen Sie einen Delegaten zur Durchführung der Arbeit bereit (Sie können eine Lambda-Funktion oder Delegatfunktion verwenden).</span><span class="sxs-lookup"><span data-stu-id="03818-114">Supply a delegate to do the work (you can use a lambda, or a delegate function).</span></span> <span data-ttu-id="03818-115">**RunAsync** gibt ein [**IAsyncAction**](https://msdn.microsoft.com/library/windows/apps/BR206580)-Objekt zurück. Speichern Sie dieses Objekt, da es im nächsten Schritt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="03818-115">Note that **RunAsync** returns an [**IAsyncAction**](https://msdn.microsoft.com/library/windows/apps/BR206580) object; store this object for use in the next step.</span></span>

<span data-ttu-id="03818-116">Drei Versionen von [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/BR230593) sind verfügbar. Damit können Sie optional die Priorität der Arbeitsaufgabe angeben und steuern, ob sie gleichzeitig mit anderen Arbeitsaufgaben ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="03818-116">Three versions of [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/BR230593) are available so that you can optionally specify the priority of the work item, and control whether it runs concurrently with other work items.</span></span>

>[!NOTE]
><span data-ttu-id="03818-117">Verwenden Sie [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) , um Zugriff auf den UI-Thread und den Fortschritt der Arbeitsaufgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="03818-117">Use [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) to access the UI thread and show progress from the work item.</span></span>

<span data-ttu-id="03818-118">Im folgenden Beispiel werden eine Arbeitsaufgabe erstellt und ein Lambda für die Verarbeitung angegeben:</span><span class="sxs-lookup"><span data-stu-id="03818-118">The following example creates a work item and supplies a lambda to do the work:</span></span>

```csharp
// The nth prime number to find.
const uint n = 9999;

// A shared pointer to the result.
// We use a shared pointer to keep the result alive until the
// thread is done.
ulong nthPrime = 0;

// Simulates work by searching for the nth prime number. Uses a
// naive algorithm and counts 2 as the first prime number.
IAsyncAction asyncAction = Windows.System.Threading.ThreadPool.RunAsync(
    (workItem) =>
{
    uint  progress = 0; // For progress reporting.
    uint  primes = 0;   // Number of primes found so far.
    ulong i = 2;        // Number iterator.

    if ((n >= 0) && (n <= 2))
    {
        nthPrime = n;
        return;
    }

    while (primes < (n - 1))
    {
        if (workItem.Status == AsyncStatus.Canceled)
        {
            break;
        }

        // Go to the next number.
        i++;

        // Check for prime.
        bool prime = true;
        for (uint j = 2; j < i; ++j)
        {
            if ((i % j) == 0)
            {
                prime = false;
                break;
            }
        };

        if (prime)
        {
            // Found another prime number.
            primes++;

            // Report progress at every 10 percent.
            uint temp = progress;
            progress = (uint)(10.0*primes/n);

            if (progress != temp)
            {
                String updateString;
                updateString = "Progress to " + n + "th prime: "
                    + (10 * progress) + "%\n";

                // Update the UI thread with the CoreDispatcher.
                CoreApplication.MainView.CoreWindow.Dispatcher.RunAsync(
                    CoreDispatcherPriority.High,
                    new DispatchedHandler(() =>
                {
                    UpdateUI(updateString);
                }));
            }
        }
    }

    // Return the nth prime number.
    nthPrime = i;
});

// A reference to the work item is cached so that we can trigger a
// cancellation when the user presses the Cancel button.
m_workItem = asyncAction;
```

```cppwinrt
// The nth prime number to find.
const unsigned int n{ 9999 };

unsigned long nthPrime{ 0 };

// Simulates work by searching for the nth prime number. Uses a
// naive algorithm and counts 2 as the first prime number.

// A reference to the work item is cached so that we can trigger a
// cancellation when the user presses the Cancel button.
m_workItem = Windows::System::Threading::ThreadPool::RunAsync([&](Windows::Foundation::IAsyncAction const& workItem)
{
    unsigned int progress = 0; // For progress reporting.
    unsigned int primes = 0;   // Number of primes found so far.
    unsigned long int i = 2;   // Number iterator.

    if ((n >= 0) && (n <= 2))
    {
        nthPrime = n;
        return;
    }

    while (primes < (n - 1))
    {
        if (workItem.Status() == Windows::Foundation::AsyncStatus::Canceled)
        {
            break;
        }

        // Go to the next number.
        i++;

        // Check for prime.
        bool prime = true;
        for (unsigned int j = 2; j < i; ++j)
        {
            if ((i % j) == 0)
            {
                prime = false;
                break;
            }
        };

        if (prime)
        {
            // Found another prime number.
            primes++;

            // Report progress at every 10 percent.
            unsigned int temp = progress;
            progress = static_cast<unsigned int>(10.f*primes / n);

            if (progress != temp)
            {
                std::wstringstream updateString;
                updateString << L"Progress to " << n << L"th prime: " << (10 * progress) << std::endl;

                // Update the UI thread with the CoreDispatcher.
                Windows::ApplicationModel::Core::CoreApplication::MainView().CoreWindow().Dispatcher().RunAsync(
                    Windows::UI::Core::CoreDispatcherPriority::High,
                    Windows::UI::Core::DispatchedHandler([&]()
                {
                    UpdateUI(updateString.str());
                }));
            }
        }
    }
    // Return the nth prime number.
    nthPrime = i;
});
```

```cpp
// The nth prime number to find.
const unsigned int n = 9999;

// A shared pointer to the result.
// We use a shared pointer to keep the result alive until the
// thread is done.
std::shared_ptr<unsigned long> nthPrime = make_shared<unsigned long int>(0);

// Simulates work by searching for the nth prime number. Uses a
// naive algorithm and counts 2 as the first prime number.
auto workItem = ref new WorkItemHandler(
    \[this, n, nthPrime](IAsyncAction^ workItem)
{
    unsigned int progress = 0; // For progress reporting.
    unsigned int primes = 0;   // Number of primes found so far.
    unsigned long int i = 2;   // Number iterator.

    if ((n >= 0) && (n <= 2))
    {
        *nthPrime = n;
        return;
    }

    while (primes < (n - 1))
    {
        if (workItem->Status == AsyncStatus::Canceled)
       {
           break;
       }

       // Go to the next number.
       i++;

       // Check for prime.
       bool prime = true;
       for (unsigned int j = 2; j < i; ++j)
       {
           if ((i % j) == 0)
           {
               prime = false;
               break;
           }
       };

       if (prime)
       {
           // Found another prime number.
           primes++;

           // Report progress at every 10 percent.
           unsigned int temp = progress;
           progress = static_cast<unsigned int>(10.f*primes / n);

           if (progress != temp)
           {
               String^ updateString;
               updateString = "Progress to " + n + "th prime: "
                   + (10 * progress).ToString() + "%\n";

               // Update the UI thread with the CoreDispatcher.
               CoreApplication::MainView->CoreWindow->Dispatcher->RunAsync(
                   CoreDispatcherPriority::High,
                   ref new DispatchedHandler([this, updateString]()
               {
                   UpdateUI(updateString);
               }));
           }
       }
   }
   // Return the nth prime number.
   *nthPrime = i;
});

auto asyncAction = ThreadPool::RunAsync(workItem);

// A reference to the work item is cached so that we can trigger a
// cancellation when the user presses the Cancel button.
m_workItem = asyncAction;
```

<span data-ttu-id="03818-119">Nach dem Aufruf von [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/BR230593) wird die Arbeitsaufgabe vom Threadpool in eine Warteschlange eingereiht und ausgeführt, wenn ein Thread verfügbar wird.</span><span class="sxs-lookup"><span data-stu-id="03818-119">Following the call to [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/BR230593), the work item is queued by the thread pool and runs when a thread becomes available.</span></span> <span data-ttu-id="03818-120">Arbeitsaufgaben im Threadpool werden asynchron und in einer beliebigen Reihenfolge ausgeführt. Stellen Sie daher sicher, dass Ihre Arbeitsaufgaben über eine unabhängige Funktionsweise funktionieren.</span><span class="sxs-lookup"><span data-stu-id="03818-120">Thread pool work items run asynchronously and they can run in any order, so make sure your work items function independently.</span></span>

<span data-ttu-id="03818-121">Beachten Sie, dass von der Arbeitsaufgabe die [**IAsyncInfo.Status**](https://msdn.microsoft.com/library/windows/apps/BR206593)-Eigenschaft überprüft und bei einem Abbruch der Arbeitsaufgabe beendet wird.</span><span class="sxs-lookup"><span data-stu-id="03818-121">Note that the work item checks the [**IAsyncInfo.Status**](https://msdn.microsoft.com/library/windows/apps/BR206593) property, and exits if the work item is cancelled.</span></span>

## <a name="handle-work-item-completion"></a><span data-ttu-id="03818-122">Behandeln der Vervollständigung der Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="03818-122">Handle work item completion</span></span>

<span data-ttu-id="03818-123">Stellen Sie einen Vervollständigungshandler zur Verfügung, indem Sie die [**IAsyncAction.Completed**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncaction.completed.aspx)-Eigenschaft der Arbeitsaufgabe festlegen.</span><span class="sxs-lookup"><span data-stu-id="03818-123">Provide a completion handler by setting the [**IAsyncAction.Completed**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncaction.completed.aspx) property of the work item.</span></span> <span data-ttu-id="03818-124">Geben Sie einen Delegaten an (Sie können eine Lambda-Funktion oder Delegatfunktion nutzen), mit dem die Arbeitsaufgabe durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="03818-124">Supply a delegate (you can use a lambda or a delegate function) to handle work item completion.</span></span> <span data-ttu-id="03818-125">Verwenden Sie z.B. [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317), um auf den Benutzeroberflächenthread zuzugreifen und das Ergebnis anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="03818-125">For example, use [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) to access the UI thread and show the result.</span></span>

<span data-ttu-id="03818-126">Im folgenden Beispiel wird die Benutzeroberfläche mit dem Ergebnis der in Schritt1 übermittelten Arbeitsaufgabe aktualisiert:</span><span class="sxs-lookup"><span data-stu-id="03818-126">The following example updates the UI with the result of the work item submitted in step 1:</span></span>

```cpp
asyncAction->Completed = ref new AsyncActionCompletedHandler(
    \[this, n, nthPrime](IAsyncAction^ asyncInfo, AsyncStatus asyncStatus)
{
    if (asyncStatus == AsyncStatus::Canceled)
    {
        return;
    }

    String^ updateString;
    updateString = "\n" + "The " + n + "th prime number is "
        + (*nthPrime).ToString() + ".\n";

    // Update the UI thread with the CoreDispatcher.
    CoreApplication::MainView->CoreWindow->Dispatcher->RunAsync(
        CoreDispatcherPriority::High,
        ref new DispatchedHandler([this, updateString]()
    {
        UpdateUI(updateString);
    }));
});
```

```cppwinrt
m_workItem.Completed([&](Windows::Foundation::IAsyncAction const& asyncInfo, Windows::Foundation::AsyncStatus const& asyncStatus)
{
    if (asyncStatus == Windows::Foundation::AsyncStatus::Canceled)
    {
        return;
    }

    std::wstringstream updateString;
    updateString << std::endl << L"The " << n << L"th prime number is " << nthPrime << std::endl;

    // Update the UI thread with the CoreDispatcher.
    Windows::ApplicationModel::Core::CoreApplication::MainView().CoreWindow().Dispatcher().RunAsync(
        Windows::UI::Core::CoreDispatcherPriority::High,
        Windows::UI::Core::DispatchedHandler([&]()
    {
        UpdateUI(updateString.str());
    }));
});
```

```c#
asyncAction.Completed = new AsyncActionCompletedHandler(
    (IAsyncAction asyncInfo, AsyncStatus asyncStatus) =>
{
    if (asyncStatus == AsyncStatus.Canceled)
    {
        return;
    }

    String updateString;
    updateString = "\n" + "The " + n + "th prime number is "
        + nthPrime + ".\n";

    // Update the UI thread with the CoreDispatcher.
    CoreApplication.MainView.CoreWindow.Dispatcher.RunAsync(
        CoreDispatcherPriority.High,
        new DispatchedHandler(()=>
    {
        UpdateUI(updateString);
    }));
});
```

<span data-ttu-id="03818-127">Beachten Sie, dass vom Vervollständigungshandler überprüft wird, ob die Arbeitsaufgabe abgebrochen wurde, bevor eine Aktualisierung der Benutzeroberfläche bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="03818-127">Note that the completion handler checks whether the work item was cancelled before dispatching a UI update.</span></span>

## <a name="summary-and-next-steps"></a><span data-ttu-id="03818-128">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="03818-128">Summary and next steps</span></span>

<span data-ttu-id="03818-129">Weitere Informationen erhalten Sie durch das Herunterladen des Codes in dieser Schnellstartanleitung unter [Beispiel für das Erstellen einer Threadpool-Arbeitsaufgabe](http://go.microsoft.com/fwlink/p/?LinkID=328569) für Windows 8.1 und die erneute Verwendung des Quellcodes in einer win\_unap Windows10-App.</span><span class="sxs-lookup"><span data-stu-id="03818-129">You can learn more by downloading the code from this quickstart in the [Creating a ThreadPool work item sample](http://go.microsoft.com/fwlink/p/?LinkID=328569) written for Windows 8.1, and re-using the source code in a win\_unap Windows 10 app.</span></span>

## <a name="related-topics"></a><span data-ttu-id="03818-130">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="03818-130">Related topics</span></span>

* [<span data-ttu-id="03818-131">Senden einer Arbeitsaufgabe an den Threadpool</span><span class="sxs-lookup"><span data-stu-id="03818-131">Submit a work item to the thread pool</span></span>](submit-a-work-item-to-the-thread-pool.md)
* [<span data-ttu-id="03818-132">Bewährte Methoden zum Verwenden des Threadpools</span><span class="sxs-lookup"><span data-stu-id="03818-132">Best practices for using the thread pool</span></span>](best-practices-for-using-the-thread-pool.md)
* [<span data-ttu-id="03818-133">Senden einer Arbeitsaufgabe mithilfe eines Timers</span><span class="sxs-lookup"><span data-stu-id="03818-133">Use a timer to submit a work item</span></span>](use-a-timer-to-submit-a-work-item.md)
 
