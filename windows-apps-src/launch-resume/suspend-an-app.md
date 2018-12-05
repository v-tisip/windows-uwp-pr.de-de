---
title: Behandeln des Anhaltens von Apps
description: Hier erfahren Sie, wie Sie wichtige Anwendungsdaten speichern, wenn das System die App anhält.
ms.assetid: F84F1512-24B9-45EC-BF23-A09E0AC985B0
ms.date: 07/06/2018
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- vb
- cppwinrt
- cpp
ms.openlocfilehash: e765faeabc754581efc769804e2daf4bfe7f9671
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8690910"
---
# <a name="handle-app-suspend"></a><span data-ttu-id="a331a-104">Behandeln des Anhaltens von Apps</span><span class="sxs-lookup"><span data-stu-id="a331a-104">Handle app suspend</span></span>

**<span data-ttu-id="a331a-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="a331a-105">Important APIs</span></span>**

- [**<span data-ttu-id="a331a-106">Anhalten</span><span class="sxs-lookup"><span data-stu-id="a331a-106">Suspending</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242341)

<span data-ttu-id="a331a-107">Hier erfahren Sie, wie Sie wichtige Anwendungsdaten speichern, wenn das System die App anhält.</span><span class="sxs-lookup"><span data-stu-id="a331a-107">Learn how to save important application data when the system suspends your app.</span></span> <span data-ttu-id="a331a-108">Im Beispiel wird ein Ereignishandler für das [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341)-Ereignis registriert und eine Zeichenfolge in einer Datei gespeichert.</span><span class="sxs-lookup"><span data-stu-id="a331a-108">The example registers an event handler for the [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341) event and saves a string to a file.</span></span>

## <a name="register-the-suspending-event-handler"></a><span data-ttu-id="a331a-109">Registrieren des Suspending-Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="a331a-109">Register the suspending event handler</span></span>

<span data-ttu-id="a331a-110">Registrieren Sie die Behandlung des [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341)-Ereignisses, das angibt, dass die App ihre Anwendungsdaten speichern sollte, bevor sie vom System angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="a331a-110">Register to handle the [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341) event, which indicates that your app should save its application data before the system suspends it.</span></span>

```csharp
using System;
using Windows.ApplicationModel;
using Windows.ApplicationModel.Activation;
using Windows.UI.Xaml;

partial class MainPage
{
   public MainPage()
   {
      InitializeComponent();
      Application.Current.Suspending += new SuspendingEventHandler(App_Suspending);
   }
}
```

```vb
Public NotInheritable Class MainPage

   Public Sub New()
      InitializeComponent()
      AddHandler Application.Current.Suspending, AddressOf App_Suspending
   End Sub
   
End Class
```

```cppwinrt
MainPage::MainPage()
{
    InitializeComponent();
    Windows::UI::Xaml::Application::Current().Suspending({ this, &MainPage::App_Suspending });
}
```

```cpp
using namespace Windows::ApplicationModel;
using namespace Windows::ApplicationModel::Activation;
using namespace Windows::Foundation;
using namespace Windows::UI::Xaml;
using namespace AppName;

MainPage::MainPage()
{
   InitializeComponent();
   Application::Current->Suspending +=
       ref new SuspendingEventHandler(this, &MainPage::App_Suspending);
}
```

## <a name="save-application-data-before-suspension"></a><span data-ttu-id="a331a-111">Speichern von App-Daten vor dem Anhalten</span><span class="sxs-lookup"><span data-stu-id="a331a-111">Save application data before suspension</span></span>

<span data-ttu-id="a331a-112">Wenn die App das [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341)-Ereignis behandelt, kann sie die wichtigen App-Daten in der Handlerfunktion speichern.</span><span class="sxs-lookup"><span data-stu-id="a331a-112">When your app handles the [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341) event, it has the opportunity to save its important application data in the handler function.</span></span> <span data-ttu-id="a331a-113">Die App sollte die [**LocalSettings**](https://msdn.microsoft.com/library/windows/apps/br241622)-Speicher-API verwenden, um einfache Anwendungsdaten synchron zu speichern.</span><span class="sxs-lookup"><span data-stu-id="a331a-113">The app should use the [**LocalSettings**](https://msdn.microsoft.com/library/windows/apps/br241622) storage API to save simple application data synchronously.</span></span>

```csharp
partial class MainPage
{
    async void App_Suspending(
        Object sender,
        Windows.ApplicationModel.SuspendingEventArgs e)
    {
        // TODO: This is the time to save app data in case the process is terminated.
    }
}
```

```vb
Public NonInheritable Class MainPage

    Private Sub App_Suspending(
        sender As Object,
        e As Windows.ApplicationModel.SuspendingEventArgs) Handles OnSuspendEvent.Suspending

        ' TODO: This is the time to save app data in case the process is terminated.
    End Sub

End Class
```

```cppwinrt
void MainPage::App_Suspending(
    Windows::Foundation::IInspectable const& /* sender */,
    Windows::ApplicationModel::SuspendingEventArgs const& /* e */)
{
    // TODO: This is the time to save app data in case the process is terminated.
}
```

```cpp
void MainPage::App_Suspending(Object^ sender, SuspendingEventArgs^ e)
{
    // TODO: This is the time to save app data in case the process is terminated.
}
```

## <a name="release-resources"></a><span data-ttu-id="a331a-114">Freigeben von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="a331a-114">Release resources</span></span>

<span data-ttu-id="a331a-115">Sie sollten exklusive Ressourcen und Dateihandles freigeben, damit andere Apps darauf zugreifen können, während Ihre App angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="a331a-115">You should release exclusive resources and file handles so that other apps can access them while your app is suspended.</span></span> <span data-ttu-id="a331a-116">Beispiele für exklusive Ressourcen sind Kameras, E/A-Geräte, externe Geräte und Netzwerkressourcen.</span><span class="sxs-lookup"><span data-stu-id="a331a-116">Examples of exclusive resources include cameras, I/O devices, external devices, and network resources.</span></span> <span data-ttu-id="a331a-117">Durch die explizite Freigabe exklusiver Ressourcen und Dateihandles kann sichergestellt werden, dass andere Apps darauf zugreifen können, während Ihre App angehalten ist.</span><span class="sxs-lookup"><span data-stu-id="a331a-117">Explicitly releasing exclusive resources and file handles helps to ensure that other apps can access them while your app is suspended.</span></span> <span data-ttu-id="a331a-118">Wenn die App fortgesetzt wird, sollte sie ihre exklusiven Ressourcen und Dateihandles erneut abrufen.</span><span class="sxs-lookup"><span data-stu-id="a331a-118">When the app is resumed, it should reacquire  its exclusive resources and file handles.</span></span>

## <a name="remarks"></a><span data-ttu-id="a331a-119">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="a331a-119">Remarks</span></span>

<span data-ttu-id="a331a-120">Das System hält Ihre App an, wenn der Benutzer zu einer anderen App oder zum Desktop bzw. Startbildschirm wechselt.</span><span class="sxs-lookup"><span data-stu-id="a331a-120">The system suspends your app whenever the user switches to another app or to the desktop or Start screen.</span></span> <span data-ttu-id="a331a-121">Wenn der Benutzer wieder zu Ihrer App wechselt, wird diese vom System fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="a331a-121">The system resumes your app whenever the user switches back to it.</span></span> <span data-ttu-id="a331a-122">Beim Fortsetzen der App haben die Variablen und Datenstrukturen den gleichen Inhalt wie vor der Unterbrechung.</span><span class="sxs-lookup"><span data-stu-id="a331a-122">When the system resumes your app, the content of your variables and data structures is the same as it was before the system suspended the app.</span></span> <span data-ttu-id="a331a-123">Das System stellt die App exakt so wieder her, wie sie unterbrochen wurde. Dadurch entsteht für den Benutzer der Eindruck, die App wäre im Hintergrund weiter ausgeführt worden.</span><span class="sxs-lookup"><span data-stu-id="a331a-123">The system restores the app exactly where it left off, so that it appears to the user as if it's been running in the background.</span></span>

<span data-ttu-id="a331a-124">Das System versucht, die App und die dazugehörigen Daten zu speichern, während sie angehalten ist.</span><span class="sxs-lookup"><span data-stu-id="a331a-124">The system attempts to keep your app and its data in memory while it's suspended.</span></span> <span data-ttu-id="a331a-125">Wenn das System aber nicht über die notwendigen Ressourcen verfügt, um die App im Arbeitsspeicher zu behalten, beendet es die App.</span><span class="sxs-lookup"><span data-stu-id="a331a-125">However, if the system does not have the resources to keep your app in memory, the system will terminate your app.</span></span> <span data-ttu-id="a331a-126">Wenn der Benutzer wieder zu einer angehaltenen App wechselt, die beendet wurde, sendet das System ein [**Activated**](https://msdn.microsoft.com/library/windows/apps/br225018)-Ereignis, und es sollte die App-Daten in der [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)-Methode wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="a331a-126">When the user switches back to a suspended app that has been terminated, the system sends an [**Activated**](https://msdn.microsoft.com/library/windows/apps/br225018) event and should restore its application data in its [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) method.</span></span>

<span data-ttu-id="a331a-127">Das System benachrichtigt eine App nicht, wenn sie beendet wird. Wenn Ihre App angehalten wird, muss sie daher die App-Daten speichern und die exklusiven Ressourcen und Dateihandles freigeben, damit diese beim erneuten Aktivieren der App nach der Beendigung wiederhergestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="a331a-127">The system doesn't notify an app when it's terminated, so your app must save its application data and release exclusive resources and file handles when it's suspended, and restore them when the app is activated after termination.</span></span>

<span data-ttu-id="a331a-128">Wenn Sie innerhalb Ihres Handlers einen asynchronen Aufruf ausführen, wird die Steuerung sofort von diesem asynchronen Aufruf zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a331a-128">If you make an asynchronous call within your handler, control returns immediately from that asynchronous call.</span></span> <span data-ttu-id="a331a-129">Das bedeutet, dass die Ausführung dann vom Ereignishandler zurückgegeben werden kann und die App in den nächsten Zustand übergeht, obwohl der asynchrone Aufruf noch nicht abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="a331a-129">That means that execution can then return from your event handler and your app will move to the next state even though the asynchronous call hasn't completed yet.</span></span> <span data-ttu-id="a331a-130">Verwenden Sie die [**GetDeferral**](http://aka.ms/Kt66iv)-Methode für das an den Ereignishandler übergebene [**EnteredBackgroundEventArgs**](http://aka.ms/Ag2yh4)-Objekt, um das Anhalten zu verzögern, bis Sie für das zurückgegebene [**Windows.Foundation.Deferral**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.aspx)-Objekt die [**Complete**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.complete.aspx)-Methode aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="a331a-130">Use the [**GetDeferral**](http://aka.ms/Kt66iv) method on the [**EnteredBackgroundEventArgs**](http://aka.ms/Ag2yh4) object that is passed to your event handler to delay suspension until after you call the [**Complete**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.complete.aspx) method on the returned [**Windows.Foundation.Deferral**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.aspx) object.</span></span>

<span data-ttu-id="a331a-131">Durch eine Verzögerung verlängert sich nicht die Zeit, die Ihr Code ausgeführt werden muss, bevor die App beendet wird.</span><span class="sxs-lookup"><span data-stu-id="a331a-131">A deferral doesn't increase the amount you have to run your code before your app is terminated.</span></span> <span data-ttu-id="a331a-132">Dabei wird nur die Beendigung verzögert, bis die *Complete*-Methode der Verzögerung aufgerufen wird oder die Frist abläuft, *je nachdem, was zuerst eintritt*.</span><span class="sxs-lookup"><span data-stu-id="a331a-132">It only delays termination until either the deferral's *Complete* method is called, or the deadline passes-*whichever comes first*.</span></span> <span data-ttu-id="a331a-133">Zeit in die "Suspending" Zustand Verwendung [ **ExtendedExecutionSession** erweitern](run-minimized-with-extended-execution.md)</span><span class="sxs-lookup"><span data-stu-id="a331a-133">To extend time in the Suspending state use [**ExtendedExecutionSession**](run-minimized-with-extended-execution.md)</span></span>

> [!NOTE]
> <span data-ttu-id="a331a-134">Zum Verbessern der Reaktionsfähigkeit des Systems in Windows8.1 erhalten apps geringe Priorität beim Zugriff auf Ressourcen, nachdem sie angehalten wurden.</span><span class="sxs-lookup"><span data-stu-id="a331a-134">To improve system responsiveness in Windows8.1, apps are given low priority access to resources after they are suspended.</span></span> <span data-ttu-id="a331a-135">Zur Unterstützung dieser neuen Priorität wird das Timeout für den Anhaltevorgang ausgedehnt, sodass die App für normale Priorität unter Windows über einen 5-Sekunden-Timeout und unter WindowsPhone über einen Timeout von 1 bis 10Sekunden verfügt.</span><span class="sxs-lookup"><span data-stu-id="a331a-135">To support this new priority, the suspend operation timeout is extended so that the app has the equivalent of the 5-second timeout for normal priority on Windows or between 1 and 10 seconds on Windows Phone.</span></span> <span data-ttu-id="a331a-136">Dieses Timeout-Fenster kann weder verlängert noch geändert werden.</span><span class="sxs-lookup"><span data-stu-id="a331a-136">You cannot extend or alter this timeout window.</span></span>

<span data-ttu-id="a331a-137">**Hinweis zum Debuggen mit Visual Studio:** Visual Studio verhindert, dass in Windows eine an den Debugger angefügte App angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="a331a-137">**A note about debugging using Visual Studio:** Visual Studio prevents Windows from suspending an app that is attached to the debugger.</span></span> <span data-ttu-id="a331a-138">Dies hat den Zweck, dem Benutzer das Anzeigen der Debugging-Benutzeroberfläche von Visual Studio zu ermöglichen, während die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a331a-138">This is to allow the user to view the Visual Studio debug UI while the app is running.</span></span> <span data-ttu-id="a331a-139">Beim Debuggen einer App können Sie mit VisualStudio ein Anhalteereignis an die App senden.</span><span class="sxs-lookup"><span data-stu-id="a331a-139">When you're debugging an app, you can send it a suspend event using Visual Studio.</span></span> <span data-ttu-id="a331a-140">Stellen Sie sicher, dass die Symbolleiste **Debugspeicherort** angezeigt wird, und klicken Sie dann auf das Symbol **Anhalten**.</span><span class="sxs-lookup"><span data-stu-id="a331a-140">Make sure the **Debug Location** toolbar is being shown, then click the **Suspend** icon.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a331a-141">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a331a-141">Related topics</span></span>

* [<span data-ttu-id="a331a-142">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="a331a-142">App lifecycle</span></span>](app-lifecycle.md)
* [<span data-ttu-id="a331a-143">Behandeln der App-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="a331a-143">Handle app activation</span></span>](activate-an-app.md)
* [<span data-ttu-id="a331a-144">Behandeln der App-Fortsetzung</span><span class="sxs-lookup"><span data-stu-id="a331a-144">Handle app resume</span></span>](resume-an-app.md)
* [<span data-ttu-id="a331a-145">UX-Richtlinien für das Starten, Anhalten und Fortsetzen von Apps</span><span class="sxs-lookup"><span data-stu-id="a331a-145">UX guidelines for launch, suspend, and resume</span></span>](https://msdn.microsoft.com/library/windows/apps/dn611862)
* [<span data-ttu-id="a331a-146">Erweiterte Ausführung</span><span class="sxs-lookup"><span data-stu-id="a331a-146">Extended Execution</span></span>](run-minimized-with-extended-execution.md)

 

 
