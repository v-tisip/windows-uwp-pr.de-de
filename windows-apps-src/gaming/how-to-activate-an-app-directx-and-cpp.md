---
author: mtoepke
title: So wird's gemacht - Aktivieren einer App (DirectX und C++)
description: In diesem Thema erfahren Sie, wie Sie die Aktivierungsbenutzeroberfläche für eine DirectX-App für die Universelle Windows-Plattform (UWP) definieren.
ms.assetid: b07c7da1-8a5e-5b57-6f77-6439bf653a53
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, DirectX, Aktivierung
ms.localizationpriority: medium
ms.openlocfilehash: b7f700ab97566ad9ec03d0595c55721dd9a9be98
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5768209"
---
# <a name="how-to-activate-an-app-directx-and-c"></a><span data-ttu-id="a228b-104">So wird's gemacht - Aktivieren einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="a228b-104">How to activate an app (DirectX and C++)</span></span>



<span data-ttu-id="a228b-105">In diesem Thema erfahren Sie, wie Sie die Aktivierungsbenutzeroberfläche für eine DirectX-App für die Universelle Windows-Plattform (UWP) definieren.</span><span class="sxs-lookup"><span data-stu-id="a228b-105">This topic shows how to define the activation experience for a Universal Windows Platform (UWP) DirectX app.</span></span>

## <a name="register-the-app-activation-event-handler"></a><span data-ttu-id="a228b-106">Registrieren des Ereignishandlers für die Aktivierung der App</span><span class="sxs-lookup"><span data-stu-id="a228b-106">Register the app activation event handler</span></span>


<span data-ttu-id="a228b-107">Registrieren Sie zuerst die Behandlung des [**CoreApplicationView::Activated**](https://msdn.microsoft.com/library/windows/apps/br225018)-Ereignisses, das ausgelöst wird, wenn die App vom Betriebssystem gestartet und initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="a228b-107">First, register to handle the [**CoreApplicationView::Activated**](https://msdn.microsoft.com/library/windows/apps/br225018) event, which is raised when your app is started and initialized by the operating system.</span></span>

<span data-ttu-id="a228b-108">Fügen Sie Ihrer Implementierung der [**IFrameworkView::Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495)-Methode Ihres Ansichtsanbieters (in diesem Beispiel **MyViewProvider**) folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="a228b-108">Add this code to your implementation of the [**IFrameworkView::Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495) method of your view provider (named **MyViewProvider** in the example):</span></span>

```cpp
void App::Initialize(CoreApplicationView^ applicationView)
{
    // Register event handlers for the app lifecycle. This example includes Activated, so that we
    // can make the CoreWindow active and start rendering on the window.
    applicationView->Activated +=
        ref new TypedEventHandler<CoreApplicationView^, IActivatedEventArgs^>(this, &App::OnActivated);
  
  //...

}
```

## <a name="activate-the-corewindow-instance-for-the-app"></a><span data-ttu-id="a228b-109">Aktivieren der CoreWindow-Instanz für die App</span><span class="sxs-lookup"><span data-stu-id="a228b-109">Activate the CoreWindow instance for the app</span></span>


<span data-ttu-id="a228b-110">Beim Start der App müssen Sie einen Verweis auf die [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Instanz für Ihre App abrufen.</span><span class="sxs-lookup"><span data-stu-id="a228b-110">When your app starts, you must obtain a reference to the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) for your app.</span></span> <span data-ttu-id="a228b-111">**CoreWindow** enthält den Meldungsverteiler für Fensterereignisse, mit dem die App Fensterereignisse verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="a228b-111">**CoreWindow** contains the window event message dispatcher that your app uses to process window events.</span></span> <span data-ttu-id="a228b-112">Rufen Sie diesen Verweis im Rückruf für das App-Aktivierungsereignis durch Aufrufen von [**CoreWindow::GetForCurrentThread**](https://msdn.microsoft.com/library/windows/apps/hh701589) ab.</span><span class="sxs-lookup"><span data-stu-id="a228b-112">Obtain this reference in your callback for the app activation event by calling [**CoreWindow::GetForCurrentThread**](https://msdn.microsoft.com/library/windows/apps/hh701589).</span></span> <span data-ttu-id="a228b-113">Wenn Sie diesen Verweis abgerufen haben, aktivieren Sie das Hauptfenster der App durch Aufrufen von [**CoreWindow::Activate**](https://msdn.microsoft.com/library/windows/apps/br208254).</span><span class="sxs-lookup"><span data-stu-id="a228b-113">Once you have obtained this reference, activate the main app window by calling [**CoreWindow::Activate**](https://msdn.microsoft.com/library/windows/apps/br208254).</span></span>

```cpp
void App::OnActivated(CoreApplicationView^ applicationView, IActivatedEventArgs^ args)
{
    // Run() won't start until the CoreWindow is activated.
    CoreWindow::GetForCurrentThread()->Activate();
}
```

## <a name="start-processing-event-message-for-the-main-app-window"></a><span data-ttu-id="a228b-114">Beginn der Verarbeitung von Ereignismeldungen für das Hauptfenster der App</span><span class="sxs-lookup"><span data-stu-id="a228b-114">Start processing event message for the main app window</span></span>


<span data-ttu-id="a228b-115">Ihre Rückrufe treten als Ereignismeldungen auf, die vom [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211)-Element des [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Elements der App verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="a228b-115">Your callbacks occur as event messages are processed by the [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211) for the app's [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225).</span></span> <span data-ttu-id="a228b-116">Dieser Rückruf wird nicht aufgerufen, wenn Sie in der Hauptschleife der App (in der [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505)-Methode des Ansichtsanbieters implementiert) [**CoreDispatcher::ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) nicht aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a228b-116">This callback will not be invoked if you do not call [**CoreDispatcher::ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) from your app's main loop (implemented in the [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) method of your view provider).</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="a228b-117">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a228b-117">Related topics</span></span>


* [<span data-ttu-id="a228b-118">So wird's gemacht: Anhalten einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="a228b-118">How to suspend an app (DirectX and C++)</span></span>](how-to-suspend-an-app-directx-and-cpp.md)
* [<span data-ttu-id="a228b-119">So wird's gemacht: Reaktivieren einer App (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="a228b-119">How to resume an app (DirectX and C++)</span></span>](how-to-resume-an-app-directx-and-cpp.md)

 

 




