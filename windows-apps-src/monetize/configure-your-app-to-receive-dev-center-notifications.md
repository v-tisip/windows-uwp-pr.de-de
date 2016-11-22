---
author: mcleanbyron
Description: Erfahren Sie, wie Sie Ihre UWP-App registrieren, um Pushbenachrichtigungen zu erhalten, die Sie vom Windows Dev Center erhalten.
title: Konfigurieren Sie Ihre App zum Empfangen von Dev Center-Pushbenachrichtigungen
translationtype: Human Translation
ms.sourcegitcommit: 126fee708d82f64fd2a49b844306c53bb3d4cc86
ms.openlocfilehash: 0e6ac52f1e76c0f59cc428b2ff26dc524e93cbde

---

# Konfigurieren Sie Ihre App zum Empfangen von Dev Center-Pushbenachrichtigungen

Sie können die Seite **Pushbenachrichtigungen** im Windows Dev Center-Dashboard verwenden, um durch das Senden benutzerorientierter Pushbenachrichtigungen an die Geräte, auf denen Ihre universelle Windows-Plattform (UWP)-App installiert ist, direkt mit Kunden zu interagieren. So können Sie beispielsweise Ihre Kunden mithilfe von benutzerorientierten Pushbenachrichtigungen auffordern, aktiv zu werden, etwa Ihre App zu bewerten oder ein neues Feature auszuprobieren. Sie können verschiedene Arten von Pushbenachrichtigungen verwenden, darunter Popupbenachrichtigungen, Kachelbenachrichtigungen und reine XML-Benachrichtigungen. Sie können auch die Rate der App-Starts nachverfolgen, die durch Ihre Pushbenachrichtigungen ausgelöst wurden. Weitere Informationen zu diesem Feature finden Sie unter [Senden von Pushbenachrichtigungen an den Kunden Ihrer App](../publish/send-push-notifications-to-your-apps-customers.md).

Bevor Sie Ihren Kunden benutzerorientierte Pushbenachrichtigungen von Dev Center senden können, müssen Sie eine Methode der [StoreServicesEngagementManager](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.aspx)-Klasse im Microsoft Store Services SDK verwenden, um Ihre App zum Empfang von Benachrichtigungen zu registrieren. Sie können weitere Methoden dieser Klasse verwenden, um Dev Center zu benachrichtigen, dass Ihre App in Reaktion auf eine benutzerorientierte Pushbenachrichtigung gestartet wurde (wenn Sie die Rate der App-Starts aufgrund Ihrer Benachrichtigungen nachverfolgen möchten), oder um den Empfang von Benachrichtigungen zu beenden.

## Konfigurieren des Projekts

Gehen Sie vor dem Schreiben von Code wie folgt vor, um in Ihrem Projekt einen Verweis auf das Microsoft Store Services SDK hinzuzufügen:

1. Falls noch nicht geschehen, [installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk) auf Ihrem Entwicklungscomputer. Neben der API zur Registrierung der App zum Empfang von Benachrichtigungen bietet dieses SDK auch APIs für andere Features, wie beispielsweise das Durchführen von Experimenten in Ihren Apps mit A/B-Tests und das Einblenden von Anzeigen. 
2. Öffnen Sie das Projekt in Visual Studio.
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Verweise** für Ihr Projekt, und wählen Sie anschließend **Verweis hinzufügen** aus.
4. Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.
5. Klicken Sie in der Liste der SDKs auf das Kontrollkästchen neben **Microsoft Engagement Framework** und anschließend auf **OK**.

## Registrierung für Pushbenachrichtigungen

So registrieren Sie Ihre App für den Empfang benutzerorientierter Pushbenachrichtigungen von Dev Center

1. Suchen Sie in Ihrem Projekt einen Codeabschnitt, der während des Starts ausgeführt wird und in dem Sie Ihre App zum Empfangen von Dev Center-Benachrichtigungen registrieren können.
2. Fügen Sie oben in der Codedatei die folgende Anweisung ein:

  ```csharp
  using Microsoft.Services.Store.Engagement;
  ```

3. Rufen Sie ein [StoreServicesEngagementManager](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.aspx)-Objekt ab, und rufen Sie eine der [RegisterNotificationChannelAsync](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.registernotificationchannelasync.aspx)-Überladungen in dem vorher identifizierten Startcode auf. Diese Methode sollte bei jedem Start Ihrer App aufgerufen werden.

  * Wenn Sie möchten, dass Dev Center seine eigene Kanal-URI für die Benachrichtigungen erstellt, rufen Sie die [RegisterNotificationChannelAsync()](https://msdn.microsoft.com/library/windows/apps/mt771190.aspx)-Überladung auf.

    ```csharp
    StoreServicesEngagementManager engagementManager = StoreServicesEngagementManager.GetDefault();
    await engagementManager.RegisterNotificationChannelAsync();
    ```

    >**Wichtig**&nbsp;&nbsp;Wenn Ihre App auch [CreatePushNotificationChannelForApplicationAsync](https://msdn.microsoft.com/library/windows/apps/windows.networking.pushnotifications.pushnotificationchannelmanager.createpushnotificationchannelforapplicationasync.aspx) zur Erstellung eines Benachrichtigungskanals für WNS aufruft, achten Sie darauf, dass Ihr Code nicht gleichzeitig die Überladungen [CreatePushNotificationChannelForApplicationAsync](https://msdn.microsoft.com/library/windows/apps/windows.networking.pushnotifications.pushnotificationchannelmanager.createpushnotificationchannelforapplicationasync.aspx) und [RegisterNotificationChannelAsync()](https://msdn.microsoft.com/library/windows/apps/mt771190.aspx) aufruft. Wenn Sie beide Methoden aufrufen müssen, stellen Sie sicher, dass Sie sie nacheinander aufrufen und dass die Rückgabe einer der Methoden abgewartet wird, bevor die andere aufgerufen wird.

  * Wenn Sie den Kanal-URI für benutzerorientierte Pushbenachrichtigungen von Dev Center, angeben möchten, rufen Sie die Überladung [RegisterNotificationChannelAsync(StoreServicesNotificationChannelParameters)](https://msdn.microsoft.com/library/windows/apps/mt771191.aspx) auf. Sie sollten dies beispielsweise tun, wenn Ihre App den Windows-Pushbenachrichtigungsdienst (WNS) bereits verwendet und Sie dieselbe Kanal-URI verwenden möchten. Erstellen Sie zuerst ein [StoreServicesNotificationChannelParameters](https://msdns.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesnotificationchannelparameters.aspx)-Objekt, und weisen Sie die [CustomNotificationChannelUri](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesnotificationchannelparameters.customnotificationchanneluri.aspx)-Eigenschaft Ihrer Kanal-URI zu.

    ```csharp
    StoreServicesNotificationChannelParameters parameters =
        new StoreServicesNotificationChannelParameters();
    parameters.CustomNotificationChannelUri = "Assign your channel URI here";

    StoreServicesEngagementManager engagementManager = StoreServicesEngagementManager.GetDefault();
    await engagementManager.RegisterNotificationChannelAsync(parameters);
    ```

  >#### Verständnis der Reaktionsweise Ihrer App, wenn der Benutzer die App startet

  >Nachdem Ihre App registriert ist, um Benachrichtigungen zu empfangen, und Sie [eine Pushbenachrichtigung an den Kunden Ihrer App aus Dev Center senden](../publish/send-push-notifications-to-your-apps-customers.md), wird einer der folgenden Einstiegspunkte in Ihre App aufgerufen, wenn der Benutzer die App in Reaktion auf Ihre Pushbenachrichtigung startet. Wenn Sie Code haben, der ausgeführt werden soll, wenn der Benutzer die App startet, können Sie ihn einem dieser Einstiegspunkte in Ihrer App hinzufügen.

  >* Hat die Pushbenachrichtigung einen Vordergrund-Aktivierungstyp, übergehen Sie die [OnActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onactivated.aspx)-Methode der **App**-Klasse in Ihrem Projekt, und fügen Sie Ihren Code dieser Methode hinzu.

  >* Hat die Pushbenachrichtigung einen Hintergrund-Aktivierungstyp, fügen Sie Ihren Code der [Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx)-Methode für Ihre [Hintergrundaufgabe](../launch-resume/support-your-app-with-background-tasks.md) hinzu.

  >So können Sie beispielsweise die Benutzer Ihrer App, die kostenpflichtige Add-Ons gekauft haben, mit einem kostenlosen Add-On belohnen. In diesem Fall können Sie eine Pushbenachrichtigung an ein [Kundensegment](../publish/create-customer-segments.md) senden, die auf diese Benutzer ausgerichtet ist. Dann können Sie in einem der oben aufgeführten Einstiegspunkte Code hinzufügen, um diesen Kunden einen kostenlosen [In-App-Kauf](in-app-purchases-and-trials.md) zu gewähren.

## Benachrichtigen des Dev Centers über den Start Ihrer App

Bei Auswahl der Option zur **Nachverfolgung der App-Startrate** für eine Dev Center-Pushbenachrichtigung rufen Sie die [ParseArgumentsAndTrackAppLaunch](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.parseargumentsandtrackapplaunch.aspx)-Methode aus dem entsprechenden Einstiegspunkt in die App auf, um Dev Center zu benachrichtigen, dass Ihre App in Reaktion auf eine Pushbenachrichtigung gestartet wurde.

Diese Methode gibt auch die ursprünglichen Startargumente für Ihre App zurück. Nachdem Sie sich für die Nachverfolgung der App-Startrate für eine Dev Center-Pushbenachrichtigung entschieden haben, wird den Startargumenten eine nicht transparente Nachverfolgungs-ID hinzugefügt, um die Nachverfolgung der App-Starts in Dev Center zu unterstützen. Sie müssen die Startargumente für Ihre App der [ParseArgumentsAndTrackAppLaunch](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.parseargumentsandtrackapplaunch.aspx)-Methode übergeben, und diese Methode sendet die Nachverfolgungs-ID an Dev Center, entfernt sie aus den Startargumenten und gibt die ursprünglichen Startargumente an Ihren Code weiter.

Die Art und Weise des Aufrufs der Methode hängt von dem Aktivierungstyp der benutzerorientierten Pushbenachrichtigung ab.

* Hat die Pushbenachrichtigung einen Vordergrund-Aktivierungstyp, rufen Sie diese Methode aus der [OnActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onactivated.aspx)-Methodenüberschreibung in Ihrer App auf, und übergeben Sie die Argumente, die im [ToastNotificationActivatedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.activation.toastnotificationactivatedeventargs.aspx)-Objekt verfügbar sind, an das Objekt, das an diese Methode übergeben wird. Im folgenden Codebeispiel wird davon ausgegangen, dass Ihre Codedatei **using**-Anweisungen für die Namespaces **Microsoft.Services.Store.Engagement** und **Windows.ApplicationModel.Activation** enthält.

  ```csharp
  protected override void OnActivated(IActivatedEventArgs args)
  {
       base.OnActivated(args);   

       if (args is ToastNotificationActivatedEventArgs)
       {
             var toastActivationArgs = args as ToastNotificationActivatedEventArgs;

             StoreServicesEngagementManager engagementManager = StoreServicesEngagementManager.GetDefault();
             string originalArgs = engagementManager.ParseArgumentsAndTrackAppLaunch(
                 toastActivationArgs.Argument);

             // Use the originalArgs variable to access the original arguments
             // that were passed to the app.
       }
  }
  ```

* Hat die Pushbenachrichtigung einen Hintergrund-Aktivierungstyp, rufen Sie diese Methode aus der [Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx)-Methode für Ihre [Hintergrundaufgabe](../launch-resume/support-your-app-with-background-tasks.md) auf, und übergeben Sie die Argumente, die im [ToastNotificationActionTriggerDetail](https://msdn.microsoft.com/library/windows/apps/windows.ui.notifications.toastnotificationactiontriggerdetail.aspx)-Objekt verfügbar sind, das an diese Methode übergeben wird. Im folgenden Codebeispiel wird davon ausgegangen, dass Ihre Codedatei **using**-Anweisungen für die Namespaces **Microsoft.Services.Store.Engagement**, **Windows.ApplicationModel.Background** und **Windows.UI.Notifications** enthält.

  ```csharp
  public void Run(IBackgroundTaskInstance taskInstance)
  {
       var details = taskInstance.TriggerDetails as ToastNotificationActionTriggerDetail;

       if (details != null)
       {
            StoreServicesEngagementManager engagementManager = StoreServicesEngagementManager.GetDefault();
            string originalArgs = engagementManager.ParseArgumentsAndTrackAppLaunch(details.Argument);

            // Use the originalArgs variable to access the original arguments
            // that were passed to the app.
       }
  }
  ```

## Aufhebung der Registrierung für Pushbenachrichtigungen

Wenn Sie möchten dass App keine benutzerorientierten Windows Dev Center-Pushbenachrichtigungen mehr empfängt, rufen Sie die [UnregisterNotificationChannelAsync](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.unregisternotificationchannelasync)-Methode auf.

```csharp
StoreServicesEngagementManager engagementManager = StoreServicesEngagementManager.GetDefault();
await engagementManager.UnregisterNotificationChannelAsync();
```

Beachten Sie, dass diese Methode den Kanal, der für Benachrichtigungen verwendet wird, ungültig macht, damit die App keine Pushbenachrichtigungen *irgendwelcher* Dienste mehr empfängt. Nachdem er geschlossen wurde, kann der Kanal nicht mehr für irgendwelche Dienste verwendet werden, einschließlich benutzerorientierter Windows Dev Center-Pushbenachrichtigungen und anderer Benachrichtigungen über WNS. Damit wieder Pushbenachrichtigungen an diese App gesendet werden können, muss die App einen neuen Kanal anfragen.

## Verwandte Themen

* [Senden von Pushbenachrichtigungen an die Kunden Ihrer App](../publish/send-push-notifications-to-your-apps-customers.md)
* [Übersicht über die Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-windows-push-notification-services--wns--overview)
* [So wird's gemacht: Anfordern, Erstellen und Speichern eines Benachrichtigungskanals](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh868221)
* [Microsoft Store Services SDK](https://msdn.microsoft.com/windows/uwp/monetize/microsoft-store-services-sdk)



<!--HONumber=Nov16_HO1-->


