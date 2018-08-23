---
author: JnHs
Description: Learn how to send notifications from Windows Dev Center to your app to encourage groups of customers to take an action, such as rating an app or buying an add-on.
title: Senden benutzerorientierter Pushbenachrichtigungen an die Kunden Ihrer App
ms.author: wdg-dev-content
ms.date: 08/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, zielgruppenorientierte Benachrichtigungen, Push-Benachrichtigungen, Popups, Kachel
ms.assetid: 16386c81-702d-47cd-9f91-67659f5dca73
ms.localizationpriority: medium
ms.openlocfilehash: 9d62f46ad1b55fbad3ab7c21a593625a2538b68f
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2817532"
---
# <a name="send-notifications-to-your-apps-customers"></a>Senden von Benachrichtigungen an die Kunden Ihrer App

Ihr Erfolg als App-Entwickler hängt davon ab, Ihre Sie Ihre Kunden zum richtigen Zeitpunkt und mit der richtigen Nachricht erreichen. Mit Benachrichtigungen können Sie Ihre Kunden zu einer Aktion animieren, z.B. eine App bewerten, ein Add-On kaufen, ein neues Feature ausprobieren oder eine andere App herunterladen (beispielsweise kostenlos mit einem von Ihnen bereitgestellten [Werbecode](generate-promotional-codes.md)).

Windows Dev Center bietet eine datengestützte Kundenbindungsplattform, über die Sie allen App-Kunden oder nur einer bestimmten Gruppe von Windows10-App-Kunden, die den von Ihnen für ein [Kundensegment](create-customer-segments.md) definierten Kriterien entsprechen, Benachrichtigungen senden können. <!-- You can also send a single notification to all of the customers for multiple apps. -->

> [!IMPORTANT]
> Diese Benachrichtigungen können nur mit UWP-Apps verwendet werden.

Beachten Sie beim Inhalt der Benachrichtigungen Folgendes:
- Der Inhalt Ihrer Benachrichtigungen muss den [Inhaltsrichtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies#content_policies) des Store entsprechen.
- Der Inhalt Ihrer Benachrichtigung sollte keine vertraulichen oder potenziell vertraulichen Informationen enthalten.
- Obgleich wir bemüht sind, Ihre Benachrichtigung wie geplant zu übermitteln, treten gelegentlich möglicherweise Latenzprobleme auf, die sich auf die Zustellung auswirken.
- Achten Sie darauf, nicht zu häufig Benachrichtigungen zu senden. Mehr als einmal alle 30Minuten kann aufdringlich wirken (und in vielen Fällen ist es vorzuziehen, seltener als alle 30 Minuten eine Benachrichtigung zu senden).
- Beachten Sie Folgendes: Wenn ein Kunde, der Ihre App verwendet (und zum Zeitpunkt, zu dem die Segmentmitgliedschaft bestimmt wird, mit seinem Microsoft-Konto angemeldet ist) das Gerät später an eine andere Person übergibt, sieht die andere Person unter Umständen die Benachrichtigung, die für den ursprünglichen Kunden bestimmt war. Weitere Informationen finden Sie unter [Konfigurieren Ihrer App für benutzerorientierte Pushbenachrichtigungen](../monetize/configure-your-app-to-receive-dev-center-notifications.md#notification-customers).
- Wenn Sie die gleiche Benachrichtigung an die Kunden mehrerer Apps senden, können Sie nicht auf ein bestimmtes Segment abzielen. Die Benachrichtigung wird an die Kunden aller ausgewählten Apps gesendet.


## <a name="getting-started-with-notifications"></a>Erste Schritte mit Benachrichtigungen

Sie müssen drei übergeordnete Schritte durchführen, um Ihre Kunden mithilfe von Benachrichtigungen zu erreichen.

1. **Registrieren Sie Ihre App für den Empfang von Pushbenachrichtigungen.** Fügen Sie hierzu Ihrer App einen Verweis auf das Microsoft Store Services SDK hinzu, und ergänzen Sie anschließend einige wenige Codezeilen, mit denen ein Benachrichtigungskanal zwischen dem Dev Center und Ihrer App registriert wird. Über diesen Kanal übermitteln wir Ihre Benachrichtigungen an Ihre Kunden. Details finden Sie unter [Konfigurieren Ihrer App für benutzerorientierte Pushbenachrichtigungen](../monetize/configure-your-app-to-receive-dev-center-notifications.md).
2. **Entscheiden Sie, welche Kunden Ihre Zielgruppe ist.** Sie können Ihre Benachrichtigung an alle Kunden Ihrer App senden, oder (für Benachrichtigungen für eine einzelne App) an eine Gruppe von Kunden, die ein *Segment* genannt werden und diese basierend auf demografischen oder Umsatz-Kriterien definieren. Weitere Informationen finden Sie unter [Erstellen von Kundensegmenten](create-customer-segments.md).
3. **Erstellen Sie den Inhalt der Benachrichtigung und versenden sie diesen. **Sie möchten möglicherweise eine Benachrichtigung erstellen, die Ihre Kunden dazu auffordert, Ihre App zu bewerten oder eine Benachrichtigung mit einem Sonderangebot für den Kauf eines Add-On senden.


## <a name="to-create-and-send-a-notification"></a>So erstellen und senden Sie eine Benachrichtigung

Befolgen Sie diese Schritte, um eine Benachrichtigung im Dashboard zu erstellen und an ein bestimmtes Kundensegment zu senden.

> [!NOTE]
> Bevor die App von Dev Center Benachrichtigungen empfangen kann, müssen Sie zuerst die Methode [RegisterNotificationChannelAsync](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.registernotificationchannelasync) in Ihrer App aufrufen, um Ihre App für den Empfang von Benachrichtigungen zu registrieren. Diese Methode ist im [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) verfügbar. Weitere Informationen zum Aufrufen dieser Methode, einschließlich eines Codebeispiels, finden Sie unter [Konfigurieren Ihrer App für benutzerorientierte Pushbenachrichtigungen](../monetize/configure-your-app-to-receive-dev-center-notifications.md).

1. Erweitern Sie im [Windows Dev Center-Dashboard](https://partner.microsoft.com/dashboard/) den Abschnitt **Bewerten** und wählen Sie dann **Benachrichtigungen** aus.
2. Wählen Sie auf der Seite **Benachrichtigungen** die Option **Neue Benachrichtigung** aus.
3. Wählen Sie im Abschnitt **Wählen Sie eine Vorlage aus** den [Typ der Benachrichtigung](#notification-template-types) zu senden, und klicken Sie dann auf **OK**.
4. Verwenden Sie auf der nächsten Seite das Dropdownmenü, um entweder **Einzelne App** oder **Mehrere Apps** auszuwählen, für die Sie eine Benachrichtigung generieren möchten. Sie können nur apps auswählen, die [Erhalt von Benachrichtigungen mithilfe des Microsoft Store Services SDK konfiguriert](../monetize/configure-your-app-to-receive-dev-center-notifications.md)wurden.
5. Wählen Sie im Abschnitt **Benachrichtigungseinstellungen** einen **Namen** für die Benachrichtigung aus, und wählen Sie (falls zutreffend) anschließend die **Kundengruppe** aus, an die die Benachrichtigung gesendet werden soll. (Benachrichtigungen, die an mehrere Apps gesendet werden, können nur an alle Kunden dieser Apps gesendet werden.) Wenn Sie ein Segment verwenden möchten, das Sie noch nicht bereits erstellt haben, wählen Sie **Neue Kundengruppe erstellen** aus. Beachten Sie, dass es 24Stunden dauert, bis ein neues Segmentfür Benachrichtigungen verfügbar ist. Weitere Informationen finden Sie unter [Erstellen von Kundensegmenten](create-customer-segments.md).
6. Wenn Sie das Senden der Benachrichtigung festlegen möchten, löschen Sie das Kontrollkästchen **Benachrichtigung sofort senden** und wählen Sie ein bestimmtes Datum und die Uhrzeit aus (in UTC für alle Kunden, es sei denn, Sie geben die lokale Zeitzone jedes Kunden an).
7. Wenn die Benachrichtigung zu einem bestimmten Zeitpunkt ablaufen soll, deaktivieren Sie das Kontrollkästchen **Notification never expires**, und wählen Sie ein bestimmtes Ablaufdatum und eine Uhrzeit aus (in UTC).
8. **Für Benachrichtigungen an eine einzelne App:** Wenn Sie die Empfänger filtern möchten, damit die Benachrichtigung nur an Personen übermittelt werden, die bestimmte Sprachen verwenden oder sich in bestimmten Zeitzonen befinden, aktivieren Sie das Kontrollkästchen **Filter verwenden**. Sie können anschließend die Sprache und/oder die Zeitzonenoptionen angeben, die Sie verwenden möchten.
8. **Für Benachrichtigungen an mehrere Apps:** Legen Sie fest, ob die Benachrichtigung nur an die zuletzt aktive App auf jedem Gerät (pro Kunde) oder an alle Apps auf jedem Gerät gesendet werden soll.
10. Wählen Sie im Abschnitt der **Benachrichtigungsinhalt** im Menü **Sprache** die Sprachen aus, in denen die Benachrichtigung angezeigt werden soll. Weitere Informationen finden Sie unter [Übersetzen Ihrer Benachrichtigungen](#translate-your-notifications).
11. Geben Sie im Abschnitt **Optionen** Text ein, und konfigurieren Sie alle weiteren gewünschten Optionen. Wenn Sie mit einer Vorlage begonnen haben, sind einige Optionen standardmäßig ausgewählt, die Sie jedoch beliebig ändern können.

    Die verfügbaren Optionen variieren je nach Art der Benachrichtigung. Einige Optionen lauten:

    * **Aktivierungstyp** (interaktiver Popup-Typ). Sie können **Vordergrund**, **Hintergrund** oder **Protokoll** auswählen.
    * **Start** (interaktiver Popup-Typ). Sie können auswählen, ob die Benachrichtigung eine App oder Website öffnet.
    * **Track app launch rate** (interaktiver Popup-Typ). Wenn Sie messen möchten, wie gut Sie Ihre Kunden mithilfe der einzelnen Benachrichtigungen erreichen, aktivieren Sie dieses Kontrollkästchen. Weitere Informationen finden Sie unter [Messen der Benachrichtigungsleistung](#measure-notification-performance).
    * **Dauer** (interaktiver Popup-Typ). Sie können **Kurz** oder **Lang** auswählen.
    * **Szenario** (interaktiver Popup-Typ). Sie können **Standard**, **Alarm**, **Erinnerung** oder **Eingehender Anruf** auswählen.
    * **Basis-URI** (interaktiver Popup-Typ). Weitere Informationen finden Sie unter [BaseURI](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.baseuri#Windows_UI_Xaml_FrameworkElement_BaseUri).
    * **Add image query** (interaktiver Popup-Typ). Weitere Informationen finden Sie unter [addImageQuery](https://docs.microsoft.com/uwp/schemas/tiles/toastschema/element-visual#attributes-and-elements).
    * **Visuell**. Ein Bild, Video und Sound. Ausführlichere Informationen finden Sie unter [visual](https://docs.microsoft.com/uwp/schemas/tiles/toastschema/element-visual).
    * **Eingabe**/**Aktion**/**Auswahl** (interaktiver Popup-Typ). Ermöglicht den Benutzern die Interaktion mit der Benachrichtigung. Weitere Informationen finden Sie unter [Adaptive und interaktive Popupbenachrichtigungen](../design/shell/tiles-and-notifications/adaptive-interactive-toasts.md).
    * **Bindung** (interaktiver Kacheltyp). Die Popup-Vorlage. Ausführlichere Informationen finden Sie unter [binding](https://docs.microsoft.com/uwp/schemas/tiles/toastschema/element-binding).

    > [!TIP]
    > Versuchen Sie, mit der App [Notifications Visualizer](https://www.microsoft.com/store/apps/9nblggh5xsl1) adaptive Kacheln und interaktive Popupbenachrichtigungen zu entwerfen und zu testen.

12. Wählen Sie **Als Entwurf speichern** aus, um später weiter an der Benachrichtigung zu arbeiten, oder wählen Sie **Senden** aus, wenn Sie fertig sind.


## <a name="notification-template-types"></a>Benachrichtigungsvorlagentypen

Sie können aus einer Vielzahl von Benachrichtigungsvorlagen auswählen.

-   **Leer (Popup).** Beginnen Sie mit einer leeren Popupbenachrichtigung, die Sie anpassen können. Eine Popupbenachrichtigung ist eine auf dem Bildschirm angezeigte Popupbenutzeroberfläche, die es Ihrer App ermöglicht, immer mit dem Kunden zu kommunizieren, unabhängig davon, ob dieser gerade eine andere App, die Startseite oder den Desktop anzeigt.
-   **Leer (Kachel).** Beginnen Sie mit einer leeren Kachelbenachrichtigung, die Sie anpassen können. Kacheln stellen die Apps auf der Startseite dar. Es gibt Live-Kacheln, d.h., der angezeigte Inhalt kann sich aufgrund von Benachrichtigungen ändern.
-   **Bitten um Bewertungen (Popup).** Eine Popupbenachrichtigung, die Ihre Kunden bittet, die App zu bewerten. Wenn der Kunde die Benachrichtigung auswählt, wird die Store-Bewertungsseite für Ihre App angezeigt.
-   **Um Feedback bitten (Popup).** Eine Popupbenachrichtigung, die Ihre Kunden um Feedback zur App bittet. Wenn der Kunde die Benachrichtigung auswählt, wird die Feedback-Hub-Seite für Ihre App angezeigt.
    > [!NOTE]
    > Wenn Sie diesen Vorlagentyp auswählen, müssen Sie im Feld **Start** den Platzhalterwert {PACKAGE_FAMILY_NAME} durch den tatsächlichen Paketfamiliennamen (PFN) Ihrer App ersetzen. Sie finden den PFN Ihrer App auf der Seite [App-Identität](view-app-identity-details.md) (**App-Verwaltung** > **App-Identität**).

    ![Feld „Start“ für Feedback-Popup](images/push-notifications-feedback-toast-launch-box.png)

-   **Bewerben (Popup).** Eine Popupbenachrichtigung, mit der Sie für eine andere App Ihrer Wahl werben können. Wenn der Kunde die Benachrichtigung auswählt, wird der Store-Eintrag der anderen App angezeigt.
    > [!NOTE]
    > Wenn Sie diesen Vorlagentyp auswählen, müssen Sie im Feld **Start** den Platzhalterwert **{Hier zu bewerbende ProductId}** durch die tatsächliche Store-ID des zu bewerbenden Artikels ersetzen. Die Store-ID finden Sie auf der Seite [App-Identität](view-app-identity-details.md) (**App-Verwaltung** > **App-Identität**).

    ![Feld „Start“ des Werbepopups](images/push-notifications-promote-toast-launch-box.png)

-   **Sonderangebot (Popup).** Eine Popupbenachrichtigung, mit der Sie ein Sonderangebot für Ihre App ankündigen können. Wenn der Kunde die Benachrichtigung auswählt, wird der Store-Eintrag Ihrer App angezeigt.
-   **Aktualisierungsaufforderung (Popup).** Eine Popupbenachrichtigung, die Kunden mit einer älteren Version der App zur Installation der neuesten Version auffordert. Wenn der Kunde die Benachrichtigung auswählt, wird die Liste **Downloads und Updates** der Store-App angezeigt. Beachten Sie, dass diese Vorlage nur mit einer einzigen App und nicht als Ziel für ein bestimmtes Kundensegment verwendet werden kann oder legen Sie eine andere Sendezeit fest. Wir planen, diese Benachrichtigung innerhalb von 24 Stunden an alle Benutzer zu senden, die noch nicht die neueste Version Ihrer App ausführen.


## <a name="measure-notification-performance"></a>Messen der Benachrichtigungsleistung

Sie können ermitteln, wie gut Sie mit den einzelnen Benachrichtigungen Ihre Kunden erreichen.


### <a name="to-measure-notification-performance"></a>So messen Sie die Benachrichtigungsleistung

1.  Aktivieren Sie beim Erstellen einer Benachrichtigung im Abschnitt **Benachrichtigungsinhalt** das Kontrollkästchen **Track app launch rate**.
2.  Rufen Sie in Ihrer App die [ParseArgumentsAndTrackAppLaunch](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.parseargumentsandtrackapplaunch)-Methode auf, um Dev Center mitzuteilen, dass Ihre App als Reaktion auf eine benutzerorientierte Benachrichtigung gestartet wurde. Diese Methode wird vom Microsoft Store Services SDK bereitgestellt. Weitere Informationen zum Aufrufen dieser Methode finden Sie unter [Konfigurieren Ihrer App zum Empfangen von Dev Center-Benachrichtigungen](../monetize/configure-your-app-to-receive-dev-center-notifications.md).


### <a name="to-view-notification-performance"></a>So zeigen Sie die Benachrichtigungsleistung an

Wenn Sie die Benachrichtigung und Ihre App wie oben beschrieben für das Messen der Benachrichtigungsleistung konfiguriert haben, können Sie auf dem Dashboard anzeigen, wie gut Ihre Benachrichtigungen ihren Zweck erfüllen.

Ausführliche Daten für jede Benachrichtigung zu überprüfen:

1.  Erweitern Sie im Windows Dev Center-Dashboard den Abschnitt **Bewerten** und wählen Sie dann **Benachrichtigungen** aus.
2.  Wählen Sie in der Tabelle der vorhandenen Benachrichtigungen **In Bearbeitung** oder **abgeschlossen**, und suchen Sie die allgemeine Leistung der einzelnen Benachrichtigung finden in das **Ziel** und die **App starten Rate** -Spalte.
3.  Um detailliertere Leistungsdetails anzuzeigen, wählen Sie einen Benachrichtigungsnamen aus. Im Abschnitt **Lieferstatistik** sehen Sie Daten zu **Anzahl** und **Prozentsatz** für die folgenden **Status**-Typen der Benachrichtigung angezeigt:
    * **Fehlgeschlagen**: Die Benachrichtigung wurde aus einem bestimmten Grund nicht übermittelt. Dies kann z.B. bei einem Problem im Windows-Benachrichtigungsdienst der Fall sein.
    * **Channel expiration failure**: Die Benachrichtigung konnte nicht übermittelt werden, da der Kanal zwischen der App und Dev Center abgelaufen ist. Dies kann beispielsweise vorkommen, wenn der Kunde Ihre App seit längerem nicht mehr geöffnet hat.
    * **Senden**: Die Benachrichtigung befindet sich in der Warteschlange für das Senden.
    * **Gesendet**: Die Benachrichtigung wurde gesendet.
    * **Startet**: Die Benachrichtigung wurde gesendet, der Kunde hat darauf geklickt, und Ihre App wurde daher geöffnet. Beachten Sie, dass hiermit nur das Starten der Apps nachverfolgt wird. Benachrichtigungen, die den Kunden zu weiteren Aktionen wie z.B. dem Öffnen des Store zum Hinterlassen einer Bewertung auffordern, sind nicht Teil dieses Status.
    * **Unbekannt**: Wir konnten den Status dieser Benachrichtigung nicht ermitteln.

Aktivität Benutzerdaten für alle Ihre Benachrichtigung zu analysieren:

1.  Erweitern Sie im Windows Dev Center-Dashboard den Abschnitt **Bewerten** und wählen Sie dann **Benachrichtigungen** aus.
2.  Klicken Sie auf der Seite **Benachrichtigungen** auf der Registerkarte **Analyse** . Auf dieser Registerkarte wird angezeigt, die folgenden Daten:
    * Diagramm Ansichten für die verschiedenen Benutzerstatus-Aktion für die Popups und Aktion Center-Benachrichtigungen.
    * World Kartenansichten der Click-über-Sätzen für das Popups und die Aktion zentriert Benachrichtigungen.
3. Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen. Die Standardeinstellung ist 30D (30Tage), aber Sie können Daten für 3, 6 oder 12Monate anzeigen, oder für einen benutzerdefinierten Zeitraum, den Sie angeben. Sie können auch **Filter** an, um alle Daten von der app und Land/Ihrer Region Filtern erweitern.

## <a name="translate-your-notifications"></a>Übersetzen Ihrer Benachrichtigungen

Um die Wirkung von Benachrichtigungen zu maximieren, sollten Sie sie in die von den Kunden bevorzugten Sprachen übersetzen. Dev Center erleichtert Ihnen die Übersetzung Ihrer Benachrichtigungen, denn dies erfolgt mithilfe des Diensts [Microsoft Translator](https://www.microsoft.com/translator/home.aspx) automatisch.

1.  Nachdem Sie die Benachrichtigung in der Standardsprache geschrieben haben, wählen Sie **Sprachen hinzufügen** aus (unterhalb des Menüs **Sprachen** im Abschnitt **Benachrichtigungsinhalt**).
2.  Wählen Sie im Fenster **Sprachen hinzufügen** die weiteren Sprachen aus, in denen Ihre Benachrichtigungen angezeigt werden sollen, und wählen Sie anschließend **Aktualisieren** aus.
Die Benachrichtigung wird automatisch in die im Fenster **Sprachen hinzufügen** ausgewählten Sprachen übersetzt. Zudem werden diese Sprachen zum Menü **Sprache** hinzugefügt.
3.  Um die Übersetzung Ihrer Benachrichtigung anzuzeigen, wählen Sie im Menü **Sprache** die gerade hinzugefügte Sprache aus.

Beachten Sie im Zusammenhang mit Übersetzungen Folgendes:
 - Sie können die automatische Übersetzung überschreiben, indem Sie im Feld **Inhalt** etwas anderes für die jeweilige Sprache eingeben.
 - Wenn Sie der englischen Version der Benachrichtigung ein weiteres Textfeld hinzufügen, nachdem Sie eine automatische Übersetzung überschrieben haben, wird das neue Textfeld nicht zur übersetzten Benachrichtigung hinzugefügt. In diesem Fall müssen Sie das neue Textfeld manuell zu den einzelnen übersetzten Benachrichtigungen hinzufügen.
 - Wenn Sie den englischen Text nach dem Übersetzen der Benachrichtigung ändern, aktualisieren wir automatisch die übersetzten Benachrichtigungen entsprechend der Änderung. Dies erfolgt jedoch nicht, wenn Sie zuvor die ursprüngliche Übersetzung überschrieben haben.

## <a name="related-topics"></a>Verwandte Themen
- [Kacheln für UWP-Apps](../design/shell/tiles-and-notifications/creating-tiles.md)
- [Übersicht über Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)](../design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview.md)
- [App „Notifications Visualizer”](https://www.microsoft.com/store/apps/9nblggh5xsl1)
- [StoreServicesEngagementManager.RegisterNotificationChannelAsync() | registerNotificationChannelAsync()-Methode](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager.registernotificationchannelasync)
