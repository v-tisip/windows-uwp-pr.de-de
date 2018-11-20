---
author: mtoepke
title: So wird's gemacht - Reaktivieren einer App (DirectX und C++)
description: In diesem Thema erfahren Sie, wie wichtige Anwendungsdaten wiederhergestellt werden, wenn das System Ihre DirectX-App für die Universelle Windows-Plattform (UWP) fortsetzt.
ms.assetid: 5e6bb673-6874-ace5-05eb-f88c045f2178
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, fortsetzen, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: 1149bebfd837e3d4051b5e0fca10aac248d909c5
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7307410"
---
# <a name="how-to-resume-an-app-directx-and-c"></a><span data-ttu-id="699f2-104">So wird's gemacht - Fortsetzen einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="699f2-104">How to resume an app (DirectX and C++)</span></span>



<span data-ttu-id="699f2-105">In diesem Thema erfahren Sie, wie wichtige Anwendungsdaten wiederhergestellt werden, wenn das System Ihre DirectX-App für die Universelle Windows-Plattform (UWP) fortsetzt.</span><span class="sxs-lookup"><span data-stu-id="699f2-105">This topic shows how to restore important application data when the system resumes your Universal Windows Platform (UWP) DirectX app.</span></span>

## <a name="register-the-resuming-event-handler"></a><span data-ttu-id="699f2-106">Registrieren des resuming-Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="699f2-106">Register the resuming event handler</span></span>


<span data-ttu-id="699f2-107">Registrieren Sie die Behandlung des [**CoreApplication::Resuming**](https://msdn.microsoft.com/library/windows/apps/br205859)-Ereignisses, mit dem angegeben wird, dass der Benutzer aus der App und wieder zurück gewechselt hat.</span><span class="sxs-lookup"><span data-stu-id="699f2-107">Register to handle the [**CoreApplication::Resuming**](https://msdn.microsoft.com/library/windows/apps/br205859) event, which indicates that the user switched away from your app and then back to it.</span></span>

<span data-ttu-id="699f2-108">Fügen Sie Ihrer Implementierung der [**IFrameworkView::Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495)-Methode Ihres Ansichtsanbieters folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="699f2-108">Add this code to your implementation of the [**IFrameworkView::Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495) method of your view provider:</span></span>

```cpp
// The first method is called when the IFrameworkView is being created.
void App::Initialize(CoreApplicationView^ applicationView)
{
  //...
  
    CoreApplication::Resuming +=
        ref new EventHandler<Platform::Object^>(this, &App::OnResuming);
    
  //...

}
```

## <a name="refresh-displayed-content-after-suspension"></a><span data-ttu-id="699f2-109">Aktualisieren der angezeigten Inhalte nach einer Unterbrechung</span><span class="sxs-lookup"><span data-stu-id="699f2-109">Refresh displayed content after suspension</span></span>


<span data-ttu-id="699f2-110">Wenn die App das Resuming-Ereignis behandelt, kann der angezeigte Inhalt aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="699f2-110">When your app handles the Resuming event, it has the opportunity to refresh its displayed content.</span></span> <span data-ttu-id="699f2-111">Stellen Sie alle mit dem Handler für [**CoreApplication::Suspending**](https://msdn.microsoft.com/library/windows/apps/br205860) gespeicherten Apps wieder her, und setzen Sie die Verarbeitung fort.</span><span class="sxs-lookup"><span data-stu-id="699f2-111">Restore any app you have saved with your handler for [**CoreApplication::Suspending**](https://msdn.microsoft.com/library/windows/apps/br205860), and restart processing.</span></span> <span data-ttu-id="699f2-112">Für Spieleentwickler: Wenn Sie das Audiomodul angehalten haben, muss es jetzt neu gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="699f2-112">Game devs: if you've suspended your audio engine, now's the time to restart it.</span></span>

```cpp
void App::OnResuming(Platform::Object^ sender, Platform::Object^ args)
{
    // Restore any data or state that was unloaded on suspend. By default, data
    // and state are persisted when resuming from suspend. Note that this event
    // does not occur if the app was previously terminated.

    // Insert your code here.
}
```

<span data-ttu-id="699f2-113">Dieser Rückruf tritt als Ereignismeldung auf, die vom [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211)-Element des [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Elements der App verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="699f2-113">This callback occurs as an event message processed by the [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211) for the app's [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225).</span></span> <span data-ttu-id="699f2-114">Dieser Rückruf wird nicht aufgerufen, wenn Sie in der Hauptschleife der App (in der [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505)-Methode des Ansichtsanbieters implementiert) [**CoreDispatcher::ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) nicht aufrufen.</span><span class="sxs-lookup"><span data-stu-id="699f2-114">This callback will not be invoked if you do not call [**CoreDispatcher::ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) from your app's main loop (implemented in the [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) method of your view provider).</span></span>

``` syntax
// This method is called after the window becomes active.
void App::Run()
{
    while (!m_windowClosed)
    {
        if (m_windowVisible)
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

            m_main->Update();

            if (m_main->Render())
            {
                m_deviceResources->Present();
            }
        }
        else
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
        }
    }
}
```

## <a name="remarks"></a><span data-ttu-id="699f2-115">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="699f2-115">Remarks</span></span>


<span data-ttu-id="699f2-116">Das System hält Ihre App an, wenn der Benutzer zu einer anderen App oder zum Desktop wechselt.</span><span class="sxs-lookup"><span data-stu-id="699f2-116">The system suspends your app whenever the user switches to another app or to the desktop.</span></span> <span data-ttu-id="699f2-117">Wenn der Benutzer wieder zu Ihrer App wechselt, wird die App fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="699f2-117">The system resumes your app whenever the user switches back to it.</span></span> <span data-ttu-id="699f2-118">Beim Fortsetzen der App haben die Variablen und Datenstrukturen den gleichen Inhalt wie vor der Unterbrechung.</span><span class="sxs-lookup"><span data-stu-id="699f2-118">When the system resumes your app, the content of your variables and data structures is the same as it was before the system suspended the app.</span></span> <span data-ttu-id="699f2-119">Das System stellt die App exakt so wieder her, wie sie unterbrochen wurde. Dadurch entsteht für den Benutzer der Eindruck, die App wäre im Hintergrund weiter ausgeführt worden.</span><span class="sxs-lookup"><span data-stu-id="699f2-119">The system restores the app exactly where it left off, so that it appears to the user as if it's been running in the background.</span></span> <span data-ttu-id="699f2-120">Da die App jedoch unter Umständen längere Zeit angehalten war, müssen sämtliche angezeigten Inhalte, die sich möglicherweise in der Zwischenzeit geändert haben, aktualisiert werden, und alle Rendering- und Audioverarbeitungs-Threads müssen neu gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="699f2-120">However, the app may have been suspended for a significant amount of time, so it should refresh any displayed content that might have changed while the app was suspended, and restart any rendering or audio processing threads.</span></span> <span data-ttu-id="699f2-121">Wenn Sie während eines vorherigen Anhalteereignisses Spielstände gespeichert haben, müssen Sie diese nun wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="699f2-121">If you've saved any game state data during a previous suspend event, restore it now.</span></span>

## <a name="related-topics"></a><span data-ttu-id="699f2-122">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="699f2-122">Related topics</span></span>

* [<span data-ttu-id="699f2-123">So wird's gemacht: Anhalten einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="699f2-123">How to suspend an app (DirectX and C++)</span></span>](how-to-suspend-an-app-directx-and-cpp.md)
* [<span data-ttu-id="699f2-124">So wird's gemacht: Aktivieren einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="699f2-124">How to activate an app (DirectX and C++)</span></span>](how-to-activate-an-app-directx-and-cpp.md)

 

 




