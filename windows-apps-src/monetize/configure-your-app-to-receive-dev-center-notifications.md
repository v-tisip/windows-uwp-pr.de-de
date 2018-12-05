---
Description: Learn how to register your UWP app to receive push notifications that you send from Partner Center.
title: Konfigurieren Ihrer App für benutzerorientierte Pushbenachrichtigungen
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Microsoft Store Services SDK, benutzerorientierte Pushbenachrichtigungen, Partner Center
ms.assetid: 30c832b7-5fbe-4852-957f-7941df8eb85a
ms.localizationpriority: medium
ms.openlocfilehash: f60780186256e7f78a9596c979c79bfc704ae4c2
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8708882"
---
# <a name="configure-your-app-for-targeted-push-notifications"></a>Konfigurieren der App für benutzerorientierte Pushbenachrichtigungen

Sie können die **Pushbenachrichtigungen** Seite im Partner Center direkt besser mit Kunden interagieren durch das Senden von benutzerorientierten Pushbenachrichtigungen an die Geräte auf denen Ihre universelle Windows-Plattform (UWP)-app installiert ist. So können Sie beispielsweise Ihre Kunden mithilfe von benutzerorientierten Pushbenachrichtigungen auffordern, aktiv zu werden, etwa Ihre App zu bewerten oder ein neues Feature auszuprobieren. Sie können verschiedene Arten von Pushbenachrichtigungen verwenden, darunter Popupbenachrichtigungen, Kachelbenachrichtigungen und reine XML-Benachrichtigungen. Sie können auch die Rate der App-Starts nachverfolgen, die durch Ihre Pushbenachrichtigungen ausgelöst wurden. Weitere Informationen zu diesem Feature finden Sie unter [Senden von Pushbenachrichtigungen an den Kunden Ihrer App](../publish/send-push-notifications-to-your-apps-customers.md).

Bevor Sie benutzerorientierte Pushbenachrichtigungen an Ihre Kunden aus dem Partner Center senden können, müssen Sie eine Methode der Klasse [StoreServicesEngagementManager](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager) im Microsoft Store Services SDK verwenden, um Ihre app zum Empfangen von Benachrichtigungen zu registrieren. Sie können weitere Methoden dieser Klasse verwenden, um das Partner Center zu benachrichtigen, dass Ihre app in Reaktion auf eine benutzerorientierte Pushbenachrichtigung gestartet wurde (Wenn Sie die Rate der app-Starts Ihrer Benachrichtigungen aufgrund nachverfolgen möchten) und den Erhalt von Benachrichtigungen.

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Gehen Sie vor dem Schreiben von Code wie folgt vor, um in Ihrem Projekt einen Verweis auf das Microsoft Store Services SDK hinzuzufügen:

1. Falls noch nicht geschehen, [installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk) auf Ihrem Entwicklungscomputer. 
2. Öffnen Sie das Projekt in Visual Studio.
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Verweise** für Ihr Projekt, und wählen Sie anschließend **Verweis hinzufügen** aus.
4. Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.
5. Klicken Sie in der Liste der SDKs auf das Kontrollkästchen neben **Microsoft Engagement Framework** und anschließend auf **OK**.

## <a name="register-for-push-notifications"></a>Registrierung für Pushbenachrichtigungen

So registrieren Sie Ihre app für benutzerorientierte Pushbenachrichtigungen von Partner Center zu erhalten:

1. Suchen Sie in Ihrem Projekt einen Codeabschnitt, der während des Starts ausgeführt wird und in dem Sie Ihre App zum Empfangen von Benachrichtigungen registrieren können.
2. Fügen Sie zu Beginn der Codedatei die folgende Anweisung ein:

    [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#EngagementNamespace)]

3. Rufen Sie ein [StoreServicesEngagementManager](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager)-Objekt ab, und rufen Sie eine der [RegisterNotificationChannelAsync](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.registernotificationchannelasync)-Überladungen in dem vorher identifizierten Startcode auf. Diese Methode sollte bei jedem Start Ihrer App aufgerufen werden.

  * Wenn Sie Partner Center, um einen eigenen Kanal-URI für die Benachrichtigungen erstellen möchten, rufen Sie die Überladung [RegisterNotificationChannelAsync()](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.registernotificationchannelasync) .

      [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#RegisterNotificationChannelAsync1)]
      > [!IMPORTANT]
      > Wenn Ihre App auch [CreatePushNotificationChannelForApplicationAsync](https://docs.microsoft.com/uwp/api/windows.networking.pushnotifications.pushnotificationchannelmanager.createpushnotificationchannelforapplicationasync) zur Erstellung eines Benachrichtigungskanals für WNS aufruft, achten Sie darauf, dass Ihr Code nicht gleichzeitig die Überladungen [CreatePushNotificationChannelForApplicationAsync](https://docs.microsoft.com/uwp/api/windows.networking.pushnotifications.pushnotificationchannelmanager.createpushnotificationchannelforapplicationasync) und [RegisterNotificationChannelAsync()](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.registernotificationchannelasync) aufruft. Wenn Sie beide Methoden aufrufen müssen, stellen Sie sicher, dass Sie sie nacheinander aufrufen und dass die Rückgabe einer der Methoden abgewartet wird, bevor die andere aufgerufen wird.

  * Wenn Sie den Kanal-URI für benutzerorientierte Pushbenachrichtigungen von Partner Center verwenden angeben möchten, rufen Sie die Überladung [RegisterNotificationChannelAsync(StoreServicesNotificationChannelParameters)](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.registernotificationchannelasync) . Sie sollten dies beispielsweise tun, wenn Ihre App den Windows-Pushbenachrichtigungsdienst (WNS) bereits verwendet und Sie dieselbe Kanal-URI verwenden möchten. Erstellen Sie zuerst ein [StoreServicesNotificationChannelParameters](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesnotificationchannelparameters)-Objekt, und weisen Sie die [CustomNotificationChannelUri](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesnotificationchannelparameters.customnotificationchanneluri)-Eigenschaft dem Kanal-URI zu.

      [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#RegisterNotificationChannelAsync2)]

> [!NOTE]
> Beim Aufrufen der **RegisterNotificationChannelAsync**-Methode wird eine Datei mit dem Namen MicrosoftStoreEngagementSDKId.txt im lokalen App-Datenspeicher für Ihre App erstellt. (Dies ist der von der Eigenschaft [ApplicationData.LocalFolder](https://docs.microsoft.com/uwp/api/Windows.Storage.ApplicationData.LocalFolder) zurückgegebene Ordner.) Diese Datei enthält eine ID, die von der Infrastruktur der benutzerorientierten Pushbenachrichtigungen verwendet wird. Stellen Sie sicher, dass Ihre App diese Datei nicht ändert oder löscht. Andernfalls erhalten die Benutzer möglicherweise mehrere Instanzen von Benachrichtigungen, oder die Benachrichtigungen verhalten sich auf andere Weise nicht ordnungsgemäß.

<span id="notification-customers" />

### <a name="how-targeted-push-notifications-are-routed-to-customers"></a>Wie benutzerorientierte Pushbenachrichtigungen an Kunden weitergeleitet werden

Wenn Ihre App **RegisterNotificationChannelAsync** aufruft, erfasst diese Methode das Microsoft-Konto des Kunden, der derzeit bei dem Gerät angemeldet ist. Wenn Sie eine benutzerorientierte Pushbenachrichtigung an ein Segment, die diesen Kunden enthält senden, sendet Partner Center die Benachrichtigung später an Geräte, die mit Microsoft-Konto dieses Kunden verknüpft sind.

Beachten Sie Folgendes: Wenn der Kunde, der Ihre App gestartet hat, das Gerät an eine anderen Person übergibt, jedoch noch mit seinem Microsoft-Konto bei diesem Gerät angemeldet ist, sieht die andere Person möglicherweise die Benachrichtigung, die für den ursprünglichen Kunden bestimmt war. Dies kann unerwünschte Folgen nach sich ziehen, insbesondere im Fall von Apps, die Dienste anbieten, für deren Nutzung Kunden sich anmelden müssen. Um zu verhindern, dass andere Benutzer in diesem Szenario Ihre benutzerorientierte Benachrichtigungen sehen können, rufen Sie die [UnregisterNotificationChannelAsync](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.unregisternotificationchannelasync)-Methode auf, wenn Kunden sich von Ihrer App abmelden. Weitere Informationen finden Sie unter [Aufheben der Registrierung für Pushbenachrichtigungen](#unregister) weiter unten in diesem Artikel.

### <a name="how-your-app-responds-when-the-user-launches-your-app"></a>Reaktionsweise Ihrer App, wenn der Benutzer die App startet

Nachdem Ihre app zum Empfangen von Benachrichtigungen und [Senden Sie eine Pushbenachrichtigung an die Kunden Ihrer app aus dem Partner Center](../publish/send-push-notifications-to-your-apps-customers.md)registriert wurde, wird eine der folgenden Einstiegspunkte in Ihrer app aufgerufen, wenn der Benutzer Ihre app in Reaktion auf Ihre Pushbenachrichtigung startet Benachrichtigung. Wenn Sie Code haben, der ausgeführt werden soll, wenn der Benutzer die App startet, können Sie ihn einem dieser Einstiegspunkte in Ihrer App hinzufügen.

  * Hat die Pushbenachrichtigung einen Vordergrund-Aktivierungstyp, übergehen Sie die [OnActivated](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.onactivated)-Methode der **App**-Klasse in Ihrem Projekt, und fügen Sie Ihren Code dieser Methode hinzu.

  * Hat die Pushbenachrichtigung einen Hintergrund-Aktivierungstyp, fügen Sie Ihren Code der [Run](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.ibackgroundtask.run)-Methode für Ihre [Hintergrundaufgabe](../launch-resume/support-your-app-with-background-tasks.md) hinzu.

So können Sie beispielsweise die Benutzer Ihrer App, die kostenpflichtige Add-Ons gekauft haben, mit einem kostenlosen Add-On belohnen. In diesem Fall können Sie eine Pushbenachrichtigung an ein [Kundensegment](../publish/create-customer-segments.md) senden, die auf diese Benutzer ausgerichtet ist. Dann können Sie in einem der oben aufgeführten Einstiegspunkte Code hinzufügen, um diesen Kunden einen kostenlosen [In-App-Kauf](in-app-purchases-and-trials.md) zu gewähren.

## <a name="notify-partner-center-of-your-app-launch"></a>Benachrichtigen des Partner Centers über den Start Ihrer app

Wenn Sie die Option **Track app Launch Rate** für Ihre benutzerorientierte Pushbenachrichtigung im Partner Center auswählen, rufen Sie die [ParseArgumentsAndTrackAppLaunch](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.parseargumentsandtrackapplaunch) -Methode aus dem entsprechenden Einstiegspunkt in Ihrer app zum Partner Center zu benachrichtigen, die Ihre app wurde in Reaktion auf eine Pushbenachrichtigung gestartet.

Diese Methode gibt auch die ursprünglichen Startargumente für Ihre App zurück. Wenn die app-startrate für Ihre Pushbenachrichtigung werden soll, eine nicht transparente nachverfolgungs, ID hinzugefügt wird, den startargumenten verfolgen, die app im Partner Center. Sie müssen die Startargumente für Ihre app an die [ParseArgumentsAndTrackAppLaunch](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.parseargumentsandtrackapplaunch) -Methode übergeben, und diese Methode sendet die Tracking-ID für das Partner Center, entfernt die Tracking-ID aus den startargumenten und gibt die ursprünglichen Startargumente für Ihre Code.

Die Art und Weise des Aufrufs der Methode hängt von dem Aktivierungstyp der Pushbenachrichtigung ab.

* Hat die Pushbenachrichtigung einen Vordergrund-Aktivierungstyp, rufen Sie diese Methode aus der [OnActivated](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.onactivated)-Methodenüberschreibung in Ihrer App auf, und übergeben Sie die Argumente, die im [ToastNotificationActivatedEventArgs](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Activation.ToastNotificationActivatedEventArgs)-Objekt verfügbar sind, an das Objekt, das an diese Methode übergeben wird. Im folgenden Codebeispiel wird davon ausgegangen, dass Ihre Codedatei **using**-Anweisungen für die Namespaces **Microsoft.Services.Store.Engagement** und **Windows.ApplicationModel.Activation** enthält.

  [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/App.xaml.cs#OnActivated)]

* Wenn die Pushbenachrichtigung einen Hintergrundaktivierungstyp hat, rufen Sie diese Methode aus der [Run](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.ibackgroundtask.run)-Methode für Ihre [Hintergrundaufgabe](../launch-resume/support-your-app-with-background-tasks.md) auf, und übergeben Sie die Argumente, die im [ToastNotificationActionTriggerDetail](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotificationActionTriggerDetail)-Objekt verfügbar sind, das an diese Methode übergeben wird. Im folgenden Codebeispiel wird davon ausgegangen, dass Ihre Codedatei **using**-Anweisungen für die Namespaces **Microsoft.Services.Store.Engagement**, **Windows.ApplicationModel.Background** und **Windows.UI.Notifications** enthält.

  [!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#Run)]

<span id="unregister" />

## <a name="unregister-for-push-notifications"></a>Aufheben der Registrierung für Pushbenachrichtigungen

Wenn Sie Ihre app keine benutzerorientierte Pushbenachrichtigungen von Partner Center möchten, rufen Sie die [UnregisterNotificationChannelAsync](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.unregisternotificationchannelasync) -Methode.

[!code-cs[DevCenterNotifications](./code/StoreSDKSamples/cs/DevCenterNotifications.cs#UnregisterNotificationChannelAsync)]

Beachten Sie, dass diese Methode den Kanal, der für Benachrichtigungen verwendet wird, ungültig macht, damit die App keine Pushbenachrichtigungen *irgendwelcher* Dienste mehr empfängt. Nachdem er geschlossen wurde, kann nicht mehr der Kanal für alle Dienste, einschließlich benutzerorientierter Pushbenachrichtigungen von Partner Center und anderer Benachrichtigungen über WNS verwendet werden. Damit wieder Pushbenachrichtigungen an diese App gesendet werden können, muss die App einen neuen Kanal anfragen.

## <a name="related-topics"></a>Verwandte Themen

* [Senden von Pushbenachrichtigungen an die Kunden Ihrer App](../publish/send-push-notifications-to-your-apps-customers.md)
* [Übersicht über die Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)
* [So wird's gemacht: Anfordern, Erstellen und Speichern eines Benachrichtigungskanals](https://docs.microsoft.com/previous-versions/windows/apps/hh868221(v=win.10))
* [Microsoft Store Services SDK](https://docs.microsoft.com/windows/uwp/monetize/microsoft-store-services-sdk)
