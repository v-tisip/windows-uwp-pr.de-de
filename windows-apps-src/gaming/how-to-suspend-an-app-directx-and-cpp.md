---
title: "So wird's gemacht: Anhalten einer App (DirectX und C++)"
description: In diesem Thema wird gezeigt, wie wichtige Systemzustände und App-Daten gespeichert werden, wenn das System Ihre DirectX-App für die Universelle Windows-Plattform (UWP) anhält.
ms.assetid: 5dd435e5-ec7e-9445-fed4-9c0d872a239e
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, anhalten, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: 0b588d6bf6e7cbf43651d94a7fd46e9a767c6f09
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8740305"
---
# <a name="how-to-suspend-an-app-directx-and-c"></a><span data-ttu-id="a76b1-104">So wird's gemacht: Anhalten einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="a76b1-104">How to suspend an app (DirectX and C++)</span></span>



<span data-ttu-id="a76b1-105">In diesem Thema wird gezeigt, wie wichtige Systemzustände und App-Daten gespeichert werden, wenn das System Ihre DirectX-App für die universelle Windows-Plattform (UWP) anhält.</span><span class="sxs-lookup"><span data-stu-id="a76b1-105">This topic shows how to save important system state and app data when the system suspends your Universal Windows Platform (UWP) DirectX app.</span></span>

## <a name="register-the-suspending-event-handler"></a><span data-ttu-id="a76b1-106">Registrieren des suspending-Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="a76b1-106">Register the suspending event handler</span></span>


<span data-ttu-id="a76b1-107">Registrieren Sie zuerst die Behandlung des [**CoreApplication::Suspending**](https://msdn.microsoft.com/library/windows/apps/br205860)-Ereignisses, das ausgelöst wird, wenn die App durch eine Aktion des Benutzers oder des Systems in den angehaltenen Zustand versetzt wird.</span><span class="sxs-lookup"><span data-stu-id="a76b1-107">First, register to handle the [**CoreApplication::Suspending**](https://msdn.microsoft.com/library/windows/apps/br205860) event, which is raised when your app is moved to a suspended state by a user or system action.</span></span>

<span data-ttu-id="a76b1-108">Fügen Sie Ihrer Implementierung der [**IFrameworkView::Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495)-Methode Ihres Ansichtsanbieters folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="a76b1-108">Add this code to your implementation of the [**IFrameworkView::Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495) method of your view provider:</span></span>

```cpp
void App::Initialize(CoreApplicationView^ applicationView)
{
  //...
  
    CoreApplication::Suspending +=
        ref new EventHandler<SuspendingEventArgs^>(this, &App::OnSuspending);

  //...
}
```

## <a name="save-any-app-data-before-suspending"></a><span data-ttu-id="a76b1-109">Speichern von App-Daten vor dem Anhalten</span><span class="sxs-lookup"><span data-stu-id="a76b1-109">Save any app data before suspending</span></span>


<span data-ttu-id="a76b1-110">Wenn die App das [**CoreApplication::Suspending**](https://msdn.microsoft.com/library/windows/apps/br205860)-Ereignis behandelt, kann sie die wichtigen App-Daten in der Handlerfunktion speichern.</span><span class="sxs-lookup"><span data-stu-id="a76b1-110">When your app handles the [**CoreApplication::Suspending**](https://msdn.microsoft.com/library/windows/apps/br205860) event, it has the opportunity to save its important application data in the handler function.</span></span> <span data-ttu-id="a76b1-111">Die App sollte die [**LocalSettings**](https://msdn.microsoft.com/library/windows/apps/br241622)-Speicher-API verwenden, um einfache Anwendungsdaten synchron zu speichern.</span><span class="sxs-lookup"><span data-stu-id="a76b1-111">The app should use the [**LocalSettings**](https://msdn.microsoft.com/library/windows/apps/br241622) storage API to save simple application data synchronously.</span></span> <span data-ttu-id="a76b1-112">Wenn sie ein Spiel entwickeln, speichern Sie alle wichtigen Informationen zum Spielstand.</span><span class="sxs-lookup"><span data-stu-id="a76b1-112">If you are developing a game, save any critical game state information.</span></span> <span data-ttu-id="a76b1-113">Vergessen Sie nicht, die Audioverarbeitung anzuhalten!</span><span class="sxs-lookup"><span data-stu-id="a76b1-113">Don't forget to suspend the audio processing!</span></span>

<span data-ttu-id="a76b1-114">Implementieren Sie nun den Rückruf.</span><span class="sxs-lookup"><span data-stu-id="a76b1-114">Now, implement the callback.</span></span> <span data-ttu-id="a76b1-115">Speichern Sie die Daten der App in dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="a76b1-115">Save the app data in this method.</span></span>

```cpp
void App::OnSuspending(Platform::Object^ sender, SuspendingEventArgs^ args)
{
    // Save app state asynchronously after requesting a deferral. Holding a deferral
    // indicates that the application is busy performing suspending operations. Be
    // aware that a deferral may not be held indefinitely. After about five seconds,
    // the app will be forced to exit.
    SuspendingDeferral^ deferral = args->SuspendingOperation->GetDeferral();

    create_task([this, deferral]()
    {
        m_deviceResources->Trim();

        // Insert your code here.

        deferral->Complete();
    });
}
```

<span data-ttu-id="a76b1-116">Dieser Rückruf muss nach 5 Sekunden beendet werden.</span><span class="sxs-lookup"><span data-stu-id="a76b1-116">This callback must complete with 5 seconds.</span></span> <span data-ttu-id="a76b1-117">Während des Rückrufs müssen Sie durch den Aufruf von [**SuspendingOperation::GetDeferral**](https://msdn.microsoft.com/library/windows/apps/br224690), der einen Countdown einleitet, eine Verzögerung anfordern.</span><span class="sxs-lookup"><span data-stu-id="a76b1-117">During this callback, you must request a deferral by calling [**SuspendingOperation::GetDeferral**](https://msdn.microsoft.com/library/windows/apps/br224690), which starts the countdown.</span></span> <span data-ttu-id="a76b1-118">Rufen Sie nach Abschluss des Speichervorgangs [**SuspendingDeferral::Complete**](https://msdn.microsoft.com/library/windows/apps/br224685) auf, um dem System mitzuteilen, dass die App nun zum Anhalten bereit ist.</span><span class="sxs-lookup"><span data-stu-id="a76b1-118">When your app completes the save operation, call [**SuspendingDeferral::Complete**](https://msdn.microsoft.com/library/windows/apps/br224685) to tell the system that your app is now ready to be suspended.</span></span> <span data-ttu-id="a76b1-119">Wenn Sie keine Verzögerung anfordern oder wenn die App mehr als fünf Sekunden zum Speichern der Daten benötigt, wird die App automatisch angehalten.</span><span class="sxs-lookup"><span data-stu-id="a76b1-119">If you do not request a deferral, or if your app takes longer than 5 seconds to save the data, your app is automatically suspended.</span></span>

<span data-ttu-id="a76b1-120">Dieser Rückruf tritt als Ereignismeldung auf, die vom [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211)-Element des [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Elements der App verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="a76b1-120">This callback occurs as an event message processed by the [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211) for the app's [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225).</span></span> <span data-ttu-id="a76b1-121">Dieser Rückruf wird nicht aufgerufen, wenn Sie in der Hauptschleife der App (in der [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505)-Methode des Ansichtsanbieters implementiert) [**CoreDispatcher::ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) nicht aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a76b1-121">This callback will not be invoked if you do not call [**CoreDispatcher::ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) from your app's main loop (implemented in the [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) method of your view provider).</span></span>

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

## <a name="call-trim"></a><span data-ttu-id="a76b1-122">Aufrufen von „Trim()“</span><span class="sxs-lookup"><span data-stu-id="a76b1-122">Call Trim()</span></span>


<span data-ttu-id="a76b1-123">Windows8.1 ab, müssen alle DirectX-UWP-apps [**Idxgidevice3**](https://msdn.microsoft.com/library/windows/desktop/dn280346) aufrufen anhalten.</span><span class="sxs-lookup"><span data-stu-id="a76b1-123">Starting in Windows8.1, all DirectX UWP apps must call [**IDXGIDevice3::Trim**](https://msdn.microsoft.com/library/windows/desktop/dn280346) when suspending.</span></span> <span data-ttu-id="a76b1-124">Dieser Aufruf weist den Grafiktreiber an, alle für die App zugeordneten temporären Puffer freizugeben. Dadurch wird die Wahrscheinlichkeit verringert, dass die angehaltene App beendet wird, um Arbeitsspeicherressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="a76b1-124">This call tells the graphics driver to release all temporary buffers allocated for the app, which reduces the chance that the app will be terminated to reclaim memory resources while in the suspend state.</span></span> <span data-ttu-id="a76b1-125">Dies ist eine zertifizierungsanforderung für Windows8.1.</span><span class="sxs-lookup"><span data-stu-id="a76b1-125">This is a certification requirement for Windows8.1.</span></span>

```cpp
void App::OnSuspending(Platform::Object^ sender, SuspendingEventArgs^ args)
{
    // Save app state asynchronously after requesting a deferral. Holding a deferral
    // indicates that the application is busy performing suspending operations. Be
    // aware that a deferral may not be held indefinitely. After about five seconds,
    // the app will be forced to exit.
    SuspendingDeferral^ deferral = args->SuspendingOperation->GetDeferral();

    create_task([this, deferral]()
    {
        m_deviceResources->Trim();

        // Insert your code here.

        deferral->Complete();
    });
}

// Call this method when the app suspends. It provides a hint to the driver that the app 
// is entering an idle state and that temporary buffers can be reclaimed for use by other apps.
void DX::DeviceResources::Trim()
{
    ComPtr<IDXGIDevice3> dxgiDevice;
    m_d3dDevice.As(&dxgiDevice);

    dxgiDevice->Trim();
}
```

## <a name="release-any-exclusive-resources-and-file-handles"></a><span data-ttu-id="a76b1-126">Freigeben exklusiver Ressourcen und Dateihandles</span><span class="sxs-lookup"><span data-stu-id="a76b1-126">Release any exclusive resources and file handles</span></span>


<span data-ttu-id="a76b1-127">Wenn Ihre App das [**CoreApplication::Suspending**](https://msdn.microsoft.com/library/windows/apps/br205860)-Ereignis behandelt, hat sie auch die Möglichkeit, exklusive Ressourcen und Dateihandles freizugeben.</span><span class="sxs-lookup"><span data-stu-id="a76b1-127">When your app handles the [**CoreApplication::Suspending**](https://msdn.microsoft.com/library/windows/apps/br205860) event, it also has the opportunity to release exclusive resources and file handles.</span></span> <span data-ttu-id="a76b1-128">Durch die explizite Freigabe von Ressourcen und Dateihandles kann sichergestellt werden, dass andere Apps auf die Ressourcen und Dateihandles zugreifen können, wenn Ihre App sie nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="a76b1-128">Explicitly releasing exclusive resources and file handles helps to ensure that other apps can access them while your app isn't using them.</span></span> <span data-ttu-id="a76b1-129">Wenn die App nach der Beendigung aktiviert ist, sollte sie ihre exklusiven Ressourcen und Dateihandles öffnen.</span><span class="sxs-lookup"><span data-stu-id="a76b1-129">When the app is activated after termination, it should open its exclusive resources and file handles.</span></span>

## <a name="remarks"></a><span data-ttu-id="a76b1-130">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="a76b1-130">Remarks</span></span>


<span data-ttu-id="a76b1-131">Das System hält Ihre App an, wenn der Benutzer zu einer anderen App oder zum Desktop wechselt.</span><span class="sxs-lookup"><span data-stu-id="a76b1-131">The system suspends your app whenever the user switches to another app or to the desktop.</span></span> <span data-ttu-id="a76b1-132">Wenn der Benutzer wieder zu Ihrer App wechselt, wird die App fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="a76b1-132">The system resumes your app whenever the user switches back to it.</span></span> <span data-ttu-id="a76b1-133">Beim Fortsetzen der App haben die Variablen und Datenstrukturen den gleichen Inhalt wie vor der Unterbrechung.</span><span class="sxs-lookup"><span data-stu-id="a76b1-133">When the system resumes your app, the content of your variables and data structures is the same as it was before the system suspended the app.</span></span> <span data-ttu-id="a76b1-134">Das System stellt die App exakt so wieder her, wie sie unterbrochen wurde. Dadurch entsteht für den Benutzer der Eindruck, die App wäre im Hintergrund weiter ausgeführt worden.</span><span class="sxs-lookup"><span data-stu-id="a76b1-134">The system restores the app exactly where it left off, so that it appears to the user as if it's been running in the background.</span></span>

<span data-ttu-id="a76b1-135">Das System versucht, die App und die dazugehörigen Daten zu speichern, während sie angehalten ist.</span><span class="sxs-lookup"><span data-stu-id="a76b1-135">The system attempts to keep your app and its data in memory while it's suspended.</span></span> <span data-ttu-id="a76b1-136">Wenn das System aber nicht über die notwendigen Ressourcen verfügt, um die App im Arbeitsspeicher zu behalten, beendet es die App.</span><span class="sxs-lookup"><span data-stu-id="a76b1-136">However, if the system does not have the resources to keep your app in memory, the system will terminate your app.</span></span> <span data-ttu-id="a76b1-137">Wenn der Benutzer wieder zu einer angehaltenen App wechselt, die beendet wurde, sendet das System ein [**Activated**](https://msdn.microsoft.com/library/windows/apps/br225018)-Ereignis und sollte die App-Daten im Handler für das **CoreApplicationView::Activated**-Ereignis wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="a76b1-137">When the user switches back to a suspended app that has been terminated, the system sends an [**Activated**](https://msdn.microsoft.com/library/windows/apps/br225018) event and should restore its application data in its handler for the **CoreApplicationView::Activated** event.</span></span>

<span data-ttu-id="a76b1-138">Das System benachrichtigt eine App nicht, wenn sie beendet wird. Wenn Ihre App angehalten wird, muss sie daher die App-Daten speichern und die exklusiven Ressourcen und Dateihandles freigeben, damit diese beim erneuten Aktivieren der App nach der Beendigung wiederhergestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="a76b1-138">The system doesn't notify an app when it's terminated, so your app must save its application data and release exclusive resources and file handles when it's suspended, and restore them when the app is activated after termination.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a76b1-139">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a76b1-139">Related topics</span></span>

* [<span data-ttu-id="a76b1-140">So wird's gemacht: Reaktivieren einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="a76b1-140">How to resume an app (DirectX and C++)</span></span>](how-to-resume-an-app-directx-and-cpp.md)
* [<span data-ttu-id="a76b1-141">So wird's gemacht: Aktivieren einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="a76b1-141">How to activate an app (DirectX and C++)</span></span>](how-to-activate-an-app-directx-and-cpp.md)

 

 




