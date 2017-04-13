---
author: mcleanbyron
Description: Erfahren Sie, wie Sie Ihre UWP-App registrieren, um Pushbenachrichtigungen zu erhalten, die Sie vom Windows Dev Center senden.
title: "Konfigurieren Ihrer App für benutzerorientierte Pushbenachrichtigungen"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store Services SDK, benutzerorientierte Pushbenachrichtigungen, Dev Center
ms.assetid: 30c832b7-5fbe-4852-957f-7941df8eb85a
ms.openlocfilehash: fb8541c45c11668edb0241e530b79387531a631f
ms.sourcegitcommit: d053f28b127e39bf2aee616aa52bb5612194dc53
translationtype: HT
---
# <a name="configure-your-app-for-targeted-push-notifications"></a>Konfigurieren Ihrer App für benutzerorientierte Pushbenachrichtigungen

Sie können die Seite **Pushbenachrichtigungen** im Windows Dev Center-Dashboard verwenden, um durch das Senden benutzerorientierter Pushbenachrichtigungen an die Geräte, auf denen Ihre universelle Windows-Plattform (UWP)-App installiert ist, direkt mit Kunden zu interagieren. So können Sie beispielsweise Ihre Kunden mithilfe von benutzerorientierten Pushbenachrichtigungen auffordern, aktiv zu werden, etwa Ihre App zu bewerten oder ein neues Feature auszuprobieren. Sie können verschiedene Arten von Pushbenachrichtigungen verwenden, darunter Popupbenachrichtigungen, Kachelbenachrichtigungen und reine XML-Benachrichtigungen. Sie können auch die Rate der App-Starts nachverfolgen, die durch Ihre Pushbenachrichtigungen ausgelöst wurden. Weitere Informationen zu diesem Feature finden Sie unter [Senden von Pushbenachrichtigungen an den Kunden Ihrer App](../publish/send-push-notifications-to-your-apps-customers.md).

Bevor Sie Ihren Kunden benutzerorientierte Pushbenachrichtigungen von Dev Center senden können, müssen Sie eine Methode der [StoreServicesEngagementManager](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.aspx)-Klasse im Microsoft Store Services SDK verwenden, um Ihre App zum Empfang von Benachrichtigungen zu registrieren. Sie können weitere Methoden dieser Klasse verwenden, um Dev Center zu benachrichtigen, dass Ihre App in Reaktion auf eine benutzerorientierte Pushbenachrichtigung gestartet wurde (wenn Sie die Rate der App-Starts aufgrund Ihrer Benachrichtigungen nachverfolgen möchten), oder um den Empfang von Benachrichtigungen zu beenden.

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Gehen Sie vor dem Schreiben von Code wie folgt vor, um in Ihrem Projekt einen Verweis auf das Microsoft Store Services SDK hinzuzufügen:

1. Falls noch nicht geschehen, [installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk) auf Ihrem Entwicklungscomputer. Neben der API zur Registrierung der App zum Empfang von Benachrichtigungen bietet dieses SDK auch APIs für andere Features, wie beispielsweise das Durchführen von Experimenten in Ihren Apps mit A/B-Tests und das Einblenden von Anzeigen.
2. Öffnen Sie das Projekt in Visual Studio.
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Verweise** für Ihr Projekt, und wählen Sie anschließend **Verweis hinzufügen** aus.
4. Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.
5. Klicken Sie in der Liste der SDKs auf das Kontrollkästchen neben **Microsoft Engagement Framework** und anschließend auf **OK**.

## <a name="register-for-push-notifications"></a>Registrierung für Pushbenachrichtigungen

So registrieren Sie Ihre App für den Empfang benutzerorientierter Pushbenachrichtigungen von Dev Center

1. Suchen Sie in Ihrem Projekt einen Codeabschnitt, der während des Starts ausgeführt wird und in dem Sie Ihre App zum Empfangen von Benachrichtigungen registrieren können.
2. Fügen Sie zu Beginn der Codedatei die folgende Anweisung ein:

  [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#EngagementNamespace)]

3. Rufen Sie ein [StoreServicesEngagementManager](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.aspx)-Objekt ab, und rufen Sie eine der [RegisterNotificationChannelAsync](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.registernotificationchannelasync.aspx)-Überladungen in dem zuvor identifizierten Startcode auf. Diese Methode sollte bei jedem Start Ihrer App aufgerufen werden.

  * Wenn Sie möchten, dass Dev Center einen eigenen Kanal-URI für die Benachrichtigungen erstellt, rufen Sie die [RegisterNotificationChannelAsync()](https://msdn.microsoft.com/library/windows/apps/mt771190.aspx)-Überladung auf.

    [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#RegisterNotificationChannelAsync1)]
        > [!IMPORTANT]
        > If your app also calls [CreatePushNotificationChannelForApplicationAsync](https://msdn.microsoft.com/library/windows/apps/windows.networking.pushnotifications.pushnotificationchannelmanager.createpushnotificationchannelforapplicationasync.aspx) to create a notification channel for WNS, make sure that your code does not call [CreatePushNotificationChannelForApplicationAsync](https://msdn.microsoft.com/library/windows/apps/windows.networking.pushnotifications.pushnotificationchannelmanager.createpushnotificationchannelforapplicationasync.aspx) and the [RegisterNotificationChannelAsync()](https://msdn.microsoft.com/library/windows/apps/mt771190.aspx) overload simultaneously. If you need to call both of these methods, make sure that you call them sequentially and await the return of one method before calling the other.

  * Wenn Sie den Kanal-URI für benutzerorientierte Pushbenachrichtigungen aus Dev Center angeben möchten, rufen Sie die Überladung [RegisterNotificationChannelAsync(StoreServicesNotificationChannelParameters)](https://msdn.microsoft.com/library/windows/apps/mt771191.aspx) auf. Sie sollten dies beispielsweise tun, wenn Ihre App den Windows-Pushbenachrichtigungsdienst (WNS) bereits verwendet und Sie dieselbe Kanal-URI verwenden möchten. Erstellen Sie zuerst ein [StoreServicesNotificationChannelParameters](https://msdn.microsoft.com/en-us/library/windows/apps/microsoft.services.store.engagement.storeservicesnotificationchannelparameters.aspx)-Objekt, und weisen Sie die [CustomNotificationChannelUri](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesnotificationchannelparameters.customnotificationchanneluri.aspx)-Eigenschaft dem Kanal-URI zu.

    [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#RegisterNotificationChannelAsync2)]

> [!NOTE]
> Beim Aufrufen der **RegisterNotificationChannelAsync**-Methode wird eine Datei mit dem Namen MicrosoftStoreEngagementSDKId.txt im lokalen App-Datenspeicher für Ihre App erstellt. (Dies ist der von der Eigenschaft [ApplicationData.LocalFolder](https://docs.microsoft.com/uwp/api/Windows.Storage.ApplicationData#Windows_Storage_ApplicationData_LocalFolder) zurückgegebene Ordner.) Diese Datei enthält eine ID, die von der Infrastruktur der benutzerorientierten Pushbenachrichtigungen verwendet wird. Stellen Sie sicher, dass Ihre App diese Datei nicht ändert oder löscht. Andernfalls erhalten die Benutzer möglicherweise mehrere Instanzen von Benachrichtigungen, oder die Benachrichtigungen verhalten sich auf andere Weise nicht ordnungsgemäß.

<span id="notification-customers" />
### <a name="how-targeted-push-notifications-are-routed-to-customers"></a>Wie benutzerorientierte Pushbenachrichtigungen an Kunden weitergeleitet werden

Wenn Ihre App **RegisterNotificationChannelAsync** aufruft, erfasst diese Methode das Microsoft-Konto des Kunden, der derzeit bei dem Gerät angemeldet ist. Wenn Sie später eine benutzerorientierte Pushbenachrichtigung an ein Segment senden, in dem dieser Kunden vorhanden ist, sendet Dev Center die Benachrichtigung an Geräte, die mit dem Microsoft-Konto dieses Kunden verknüpft sind.

Beachten Sie Folgendes: Wenn der Kunde, der Ihre App gestartet hat, das Gerät an eine anderen Person übergibt, jedoch noch mit seinem Microsoft-Konto bei diesem Gerät angemeldet ist, sieht die andere Person möglicherweise die Benachrichtigung, die für den ursprünglichen Kunden bestimmt war. Dies kann unerwünschte Folgen nach sich ziehen, insbesondere im Fall von Apps, die Dienste anbieten, für deren Nutzung Kunden sich anmelden müssen. Um zu verhindern, dass andere Benutzer in diesem Szenario Ihre benutzerorientierte Benachrichtigungen sehen können, rufen Sie die [UnregisterNotificationChannelAsync](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.unregisternotificationchannelasync)-Methode auf, wenn Kunden sich von Ihrer App abmelden. Weitere Informationen finden Sie unter [Aufheben der Registrierung für Pushbenachrichtigungen](#unregister) weiter unten in diesem Artikel.

### <a name="how-your-app-responds-when-the-user-launches-your-app"></a>Reaktionsweise Ihrer App, wenn der Benutzer die App startet

Nachdem Ihre App registriert ist, um Benachrichtigungen zu empfangen, und Sie [eine Pushbenachrichtigung an den Kunden Ihrer App aus Dev Center senden](../publish/send-push-notifications-to-your-apps-customers.md), wird einer der folgenden Einstiegspunkte in Ihre App aufgerufen, wenn der Benutzer die App in Reaktion auf Ihre Pushbenachrichtigung startet. Wenn Sie Code haben, der ausgeführt werden soll, wenn der Benutzer die App startet, können Sie ihn einem dieser Einstiegspunkte in Ihrer App hinzufügen.

  * Hat die Pushbenachrichtigung einen Vordergrund-Aktivierungstyp, übergehen Sie die [OnActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onactivated.aspx)-Methode der **App**-Klasse in Ihrem Projekt, und fügen Sie Ihren Code dieser Methode hinzu.

  * Hat die Pushbenachrichtigung einen Hintergrund-Aktivierungstyp, fügen Sie Ihren Code der [Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx)-Methode für Ihre [Hintergrundaufgabe](../launch-resume/support-your-app-with-background-tasks.md) hinzu.

So können Sie beispielsweise die Benutzer Ihrer App, die kostenpflichtige Add-Ons gekauft haben, mit einem kostenlosen Add-On belohnen. In diesem Fall können Sie eine Pushbenachrichtigung an ein [Kundensegment](../publish/create-customer-segments.md) senden, die auf diese Benutzer ausgerichtet ist. Dann können Sie in einem der oben aufgeführten Einstiegspunkte Code hinzufügen, um diesen Kunden einen kostenlosen [In-App-Kauf](in-app-purchases-and-trials.md) zu gewähren.

## <a name="notify-dev-center-of-your-app-launch"></a>Benachrichtigen des Dev Centers über den Start Ihrer App

Bei Auswahl der Option zur **Nachverfolgung der App-Startrate** für Ihre benutzerorientierte Pushbenachrichtigung in Dev Center rufen Sie die [ParseArgumentsAndTrackAppLaunch](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.parseargumentsandtrackapplaunch.aspx)-Methode aus dem entsprechenden Einstiegspunkt in die App auf, um Dev Center zu benachrichtigen, dass Ihre App in Reaktion auf eine Pushbenachrichtigung gestartet wurde.

Diese Methode gibt auch die ursprünglichen Startargumente für Ihre App zurück. Wenn Sie sich für die Nachverfolgung der App-Startrate für Ihre Pushbenachrichtigung entschieden haben, wird den Startargumenten eine nicht transparente Nachverfolgungs-ID hinzugefügt, um die Nachverfolgung der App-Starts in Dev Center zu unterstützen. Sie müssen die Startargumente für Ihre App der [ParseArgumentsAndTrackAppLaunch](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.parseargumentsandtrackapplaunch.aspx)-Methode übergeben, und diese Methode sendet die Nachverfolgungs-ID an Dev Center, entfernt sie aus den Startargumenten und gibt die ursprünglichen Startargumente an Ihren Code weiter.

Die Art und Weise des Aufrufs der Methode hängt von dem Aktivierungstyp der Pushbenachrichtigung ab.

* Hat die Pushbenachrichtigung einen Vordergrund-Aktivierungstyp, rufen Sie diese Methode aus der [OnActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onactivated.aspx)-Methodenüberschreibung in Ihrer App auf, und übergeben Sie die Argumente, die im [ToastNotificationActivatedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.activation.toastnotificationactivatedeventargs.aspx)-Objekt verfügbar sind, an das Objekt, das an diese Methode übergeben wird. Im folgenden Codebeispiel wird davon ausgegangen, dass Ihre Codedatei **using**-Anweisungen für die Namespaces **Microsoft.Services.Store.Engagement** und **Windows.ApplicationModel.Activation** enthält.

  [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/App.xaml.cs#OnActivated)]

* Wenn die Pushbenachrichtigung einen Hintergrundaktivierungstyp hat, rufen Sie diese Methode aus der [Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx)-Methode für Ihre [Hintergrundaufgabe](../launch-resume/support-your-app-with-background-tasks.md) auf, und übergeben Sie die Argumente, die im [ToastNotificationActionTriggerDetail](https://msdn.microsoft.com/library/windows/apps/windows.ui.notifications.toastnotificationactiontriggerdetail.aspx)-Objekt verfügbar sind, das an diese Methode übergeben wird. Im folgenden Codebeispiel wird davon ausgegangen, dass Ihre Codedatei **using**-Anweisungen für die Namespaces **Microsoft.Services.Store.Engagement**, **Windows.ApplicationModel.Background** und **Windows.UI.Notifications** enthält.

  [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#Run)]

<span id="unregister" />
## <a name="unregister-for-push-notifications"></a>Aufheben der Registrierung für Pushbenachrichtigungen

Wenn Sie möchten, dass die App keine weiteren benutzerorientierten Pushbenachrichtigungen von Dev Center empfängt, rufen Sie die [UnregisterNotificationChannelAsync](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.unregisternotificationchannelasync)-Methode auf.

[!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#UnregisterNotificationChannelAsync)]

Beachten Sie, dass diese Methode den Kanal, der für Benachrichtigungen verwendet wird, ungültig macht, damit die App keine Pushbenachrichtigungen *irgendwelcher* Dienste mehr empfängt. Nachdem der Kanal geschlossen wurde, kann er nicht mehr für Dienste verwendet werden, einschließlich benutzerorientierter Pushbenachrichtigungen von Dev Center und anderer Benachrichtigungen über WNS. Damit wieder Pushbenachrichtigungen an diese App gesendet werden können, muss die App einen neuen Kanal anfragen.

## <a name="related-topics"></a>Verwandte Themen

* [Senden von Pushbenachrichtigungen an die Kunden Ihrer App](../publish/send-push-notifications-to-your-apps-customers.md)
* [Übersicht über die Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-windows-push-notification-services--wns--overview)
* [So wird's gemacht: Anfordern, Erstellen und Speichern eines Benachrichtigungskanals](https://msdn.microsoft.com/library/windows/apps/xaml/hh868221)
* [Microsoft Store Services SDK](https://msdn.microsoft.com/windows/uwp/monetize/microsoft-store-services-sdk)
