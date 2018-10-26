---
author: TylerMSFT
title: Umwandeln eines App-Diensts für die Ausführung im gleichen Prozess wie die Host-App
description: Konvertieren Sie App-Dienstcode, der in einem separaten Hintergrundvorgang auf Code gestoßen ist, der im selben Prozess wie Ihr App-Dienstanbieter ausgeführt wird.
ms.author: twhitney
ms.date: 11/03/2017
ms.topic: article
keywords: Windows 10, Uwp, app-Dienst
ms.assetid: 30aef94b-1b83-4897-a2f1-afbb4349696a
ms.localizationpriority: medium
ms.openlocfilehash: 272102f08b145c0681b0e036be4d41bc7c9ad9ff
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5560872"
---
# <a name="convert-an-app-service-to-run-in-the-same-process-as-its-host-app"></a><span data-ttu-id="7c790-104">Umwandeln eines App-Diensts für die Ausführung im gleichen Prozess wie die Host-App</span><span class="sxs-lookup"><span data-stu-id="7c790-104">Convert an app service to run in the same process as its host app</span></span>

<span data-ttu-id="7c790-105">Eine [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appservice.appserviceconnection.aspx) ermöglicht einer anderen Anwendung, Ihre App im Hintergrund zu aktivieren und einen direkten Kommunikationsweg mit ihr zu starten.</span><span class="sxs-lookup"><span data-stu-id="7c790-105">An [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appservice.appserviceconnection.aspx) enables another application to wake up your app in the background and start a direct line of communication with it.</span></span>

<span data-ttu-id="7c790-106">Mit der Einführung von In-Process-App-Diensten können zwei ausgeführte Vordergrundanwendungen einen direkten Kommunikationsweg über eine App-Dienst-Verbindung aufweisen.</span><span class="sxs-lookup"><span data-stu-id="7c790-106">With the introduction of in-process App Services, two running foreground applications can have a direct line of communication via an app service connection.</span></span> <span data-ttu-id="7c790-107">App-Dienste können jetzt im gleichen Prozess wie die Vordergrundanwendung ausgeführt werden. Die Kommunikation zwischen Apps wird dadurch sehr viel einfacher, während gleichzeitig die Notwendigkeit entfällt, den Dienstcode in ein separates Projekt zu trennen.</span><span class="sxs-lookup"><span data-stu-id="7c790-107">App Services can now run in the same process as the foreground application which makes communication between apps much easier and removes the need to separate the service code into a separate project.</span></span>

<span data-ttu-id="7c790-108">Um einen Out-of-Process-App-Dienst in ein In-Process-Modell zu konvertieren, sind zwei Änderungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7c790-108">Turning an out-of-process model App Service into an in-process model requires two changes.</span></span> <span data-ttu-id="7c790-109">Die erste ist eine Manifest-Änderung.</span><span class="sxs-lookup"><span data-stu-id="7c790-109">The first is a manifest change.</span></span>

> ```xml
> <Package
>    ...
>   <Applications>
>       <Application Id=...
>           ...
>           EntryPoint="...">
>           <Extensions>
>               <uap:Extension Category="windows.appService">
>                   <uap:AppService Name="InProcessAppService" />
>               </uap:Extension>
>           </Extensions>
>           ...
>       </Application>
>   </Applications>
> ```

<span data-ttu-id="7c790-110">Entfernen Sie die `EntryPoint` -Attribut aus der `<Extension>` Element da nun [OnBackgroundActivated()](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx) den Einstiegspunkt ist, das verwendet wird, wenn der app-Dienst aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="7c790-110">Remove the `EntryPoint` attribute from the `<Extension>` element because now [OnBackgroundActivated()](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx) is the entry point that will be used when the app service is invoked.</span></span>

<span data-ttu-id="7c790-111">Die zweite Änderung besteht darin, die Dienstlogik aus ihrem eigenen Hintergrundaufgabenprojekt in Methoden zu verschieben, die über **OnBackgroundActivated()** aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="7c790-111">The second change is to move the service logic from its separate background task project into methods that can be called from **OnBackgroundActivated()**.</span></span>

<span data-ttu-id="7c790-112">Jetzt kann Ihre Anwendung den App-Dienst direkt ausführen.</span><span class="sxs-lookup"><span data-stu-id="7c790-112">Now your application can directly run your App Service.</span></span> <span data-ttu-id="7c790-113">Z. B. in "App.Xaml.cs":</span><span class="sxs-lookup"><span data-stu-id="7c790-113">For example, in App.xaml.cs:</span></span>

[!NOTE] <span data-ttu-id="7c790-114">Der folgende Code unterscheidet sich z. B. 1 (Out-of-Process-Dienst) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7c790-114">The code below is different than the one provided for example 1 (out-of-process service).</span></span> <span data-ttu-id="7c790-115">Der folgende Code wird nur zur Veranschaulichung bereitgestellt und sollte nicht als Teil des Beispiel 2 (in-Process-Dienst) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7c790-115">The code below is provided for illustration purposes only and should not be used as part of example 2 (in-process service).</span></span>  <span data-ttu-id="7c790-116">Um den Vorgang fortzusetzen Übergang aus dem Beispiel im Artikel weiterhin 1 (Out-of-Process-Dienst) in Beispiel 2 (in-Process-Service) den Code zur Verfügung gestellt, z. B. 1 anstatt zur Veranschaulichung der folgende Code verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c790-116">To continue the article’s transition from example 1 (out-of-process service) into example 2 (in-process service) continue to use the code provided  for example 1 instead of the illustrative code below.</span></span>

``` cs
using Windows.ApplicationModel.AppService;
using Windows.ApplicationModel.Background;
...

sealed partial class App : Application
{
  private AppServiceConnection _appServiceConnection;
  private BackgroundTaskDeferral _appServiceDeferral;

  ...

  protected override void OnBackgroundActivated(BackgroundActivatedEventArgs args)
  {
      base.OnBackgroundActivated(args);
      IBackgroundTaskInstance taskInstance = args.TaskInstance;
      AppServiceTriggerDetails appService = taskInstance.TriggerDetails as AppServiceTriggerDetails;
      _appServiceDeferral = taskInstance.GetDeferral();
      taskInstance.Canceled += OnAppServicesCanceled;
      _appServiceConnection = appService.AppServiceConnection;
      _appServiceConnection.RequestReceived += OnAppServiceRequestReceived;
      _appServiceConnection.ServiceClosed += AppServiceConnection_ServiceClosed;
  }

  private async void OnAppServiceRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
  {
      AppServiceDeferral messageDeferral = args.GetDeferral();
      ValueSet message = args.Request.Message;
      string text = message["Request"] as string;

      if ("Value" == text)
      {
          ValueSet returnMessage = new ValueSet();
          returnMessage.Add("Response", "True");
          await args.Request.SendResponseAsync(returnMessage);
      }
      messageDeferral.Complete();
  }

  private void OnAppServicesCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
  {
      _appServiceDeferral.Complete();
  }

  private void AppServiceConnection_ServiceClosed(AppServiceConnection sender, AppServiceClosedEventArgs args)
  {
      _appServiceDeferral.Complete();
  }
}
```

<span data-ttu-id="7c790-117">Im obigen Code steuert die `OnBackgroundActivated`-Methode die App-Dienst-Aktivierung.</span><span class="sxs-lookup"><span data-stu-id="7c790-117">In the code above the `OnBackgroundActivated` method handles the app service activation.</span></span> <span data-ttu-id="7c790-118">Alle Ereignisse, die für die Kommunikation über eine [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appservice.appserviceconnection.aspx) erforderlich sind, werden registriert, und das Aufgaben-Verzögerungsobjekt wird gespeichert, damit es nach Abschluss der Kommunikation zwischen den Anwendungen als abgeschlossen gekennzeichnet werden kann.</span><span class="sxs-lookup"><span data-stu-id="7c790-118">All of the events required for communication through an [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appservice.appserviceconnection.aspx) are registered, and the task deferral object is stored so that it can be marked as complete when the communication between the applications is done.</span></span>

<span data-ttu-id="7c790-119">Wenn die App eine Anforderung empfängt, liest sie das zur Verfügung gestellte [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx), um festzustellen, ob die Zeichenfolgen `Key` und `Value` vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="7c790-119">When the app receives a request and reads the [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx) provided to see if the `Key` and `Value` strings are present.</span></span> <span data-ttu-id="7c790-120">Wenn sie vorhanden sind, gibt der App-Dienst ein Wertepaar von Zeichenfolgen `Response` und `True` an die App auf der anderen Seite der **AppServiceConnection** zurück.</span><span class="sxs-lookup"><span data-stu-id="7c790-120">If they are present then the app service returns a pair of `Response` and `True` string values back to the app on the other side of the **AppServiceConnection**.</span></span>

<span data-ttu-id="7c790-121">Weitere Informationen zum Herstellen einer Verbindung und Kommunizieren mit anderen Apps finden Sie unter [Erstellen und Verwenden eines App-Diensts](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service?f=255&MSPPError=-2147217396).</span><span class="sxs-lookup"><span data-stu-id="7c790-121">Learn more about connecting and communicating with other apps at [Create and Consume an App Service](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service?f=255&MSPPError=-2147217396).</span></span>
