---
author: TylerMSFT
title: "Umwandeln eines App-Diensts für die Ausführung im gleichen Prozess wie die Host-App"
description: "Konvertieren Sie App-Dienstcode, der in einem separaten Hintergrundvorgang auf Code gestoßen ist, der im selben Prozess wie Ihr App-Dienstanbieter ausgeführt wird."
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
ms.assetid: 30aef94b-1b83-4897-a2f1-afbb4349696a
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 1fea72237a9ac7d18fb415d5957f959542a833e8
ms.lasthandoff: 02/08/2017

---

# <a name="convert-an-app-service-to-run-in-the-same-process-as-its-host-app"></a>Umwandeln eines App-Diensts für die Ausführung im gleichen Prozess wie die Host-App

Eine [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appservice.appserviceconnection.aspx) ermöglicht einer anderen Anwendung, Ihre App im Hintergrund zu aktivieren und einen direkten Kommunikationsweg mit ihr zu starten.

Mit der Einführung von In-Process-App-Diensten können zwei ausgeführte Vordergrundanwendungen einen direkten Kommunikationsweg über eine App-Dienst-Verbindung aufweisen. App-Dienste können jetzt im gleichen Prozess wie die Vordergrundanwendung ausgeführt werden. Die Kommunikation zwischen Apps wird dadurch sehr viel einfacher, während gleichzeitig die Notwendigkeit entfällt, den Dienstcode in ein separates Projekt zu trennen.

Um einen Out-of-Process-App-Dienst in ein In-Process-Modell zu konvertieren, sind zwei Änderungen erforderlich. Die erste ist eine Manifest-Änderung.

> ```xml
>  <uap:Extension Category="windows.appService">
>          <uap:AppService Name="InProcessAppService" />
>  </uap:Extension>
> ```

Entfernen Sie das `EntryPoint`-Attribut. Jetzt wird beim Aufrufen des App-Dienstes der  [OnBackgroundActivated()](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx)-Rückruf als Rückrufmethode verwendet.

Die zweite Änderung besteht darin, die Dienstlogik aus ihrem eigenen Hintergrundaufgabenprojekt in Methoden zu verschieben, die über **OnBackgroundActivated()** aufgerufen werden können.

Jetzt kann Ihre Anwendung den App-Dienst direkt ausführen.  Beispiel:

> ``` cs
> private AppServiceConnection appServiceconnection;
> private BackgroundTaskDeferral appServiceDeferral;
> protected override async void OnBackgroundActivated(BackgroundActivatedEventArgs args)
> {
>     base.OnBackgroundActivated(args);
>     IBackgroundTaskInstance taskInstance = args.TaskInstance;
>     AppServiceTriggerDetails appService = taskInstance.TriggerDetails as AppServiceTriggerDetails;
>     appServiceDeferral = taskInstance.GetDeferral();
>     taskInstance.Canceled += OnAppServicesCanceled;
>     appServiceConnection = appService.AppServiceConnection;
>     appServiceConnection.RequestReceived += OnAppServiceRequestReceived;
>     appServiceConnection.ServiceClosed += AppServiceConnection_ServiceClosed;
> }
>
> private async void OnAppServiceRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
> {
>     AppServiceDeferral messageDeferral = args.GetDeferral();
>     ValueSet message = args.Request.Message;
>     string text = message["Request"] as string;
>              
>     if ("Value" == text)
>     {
>         ValueSet returnMessage = new ValueSet();
>         returnMessage.Add("Response", "True");
>         await args.Request.SendResponseAsync(returnMessage);
>     }
>     messageDeferral.Complete();
> }
>
> private void OnAppServicesCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
> {
>     appServiceDeferral.Complete();
> }
>
> private void AppServiceConnection_ServiceClosed(AppServiceConnection sender, AppServiceClosedEventArgs args)
> {
>     appServiceDeferral.Complete();
> }
> ```

Im obigen Code steuert die `OnBackgroundActivated`-Methode die App-Dienst-Aktivierung. Alle Ereignisse, die für die Kommunikation über eine [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appservice.appserviceconnection.aspx) erforderlich sind, werden registriert, und das Aufgaben-Verzögerungsobjekt wird gespeichert, damit es nach Abschluss der Kommunikation zwischen den Anwendungen als abgeschlossen gekennzeichnet werden kann.

Wenn die App eine Anforderung empfängt, liest sie das zur Verfügung gestellte [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx), um festzustellen, ob die Zeichenfolgen `Key` und `Value` vorhanden sind. Wenn sie vorhanden sind, gibt der App-Dienst ein Wertepaar von Zeichenfolgen `Response` und `True` an die App auf der anderen Seite der **AppServiceConnection** zurück.

Weitere Informationen zum Herstellen einer Verbindung und Kommunizieren mit anderen Apps finden Sie unter [Erstellen und Verwenden eines App-Diensts](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service?f=255&MSPPError=-2147217396).

