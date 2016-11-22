---
author: shawjohn
Description: "Erfahren Sie, wie Sie benutzerorientierte Pushbenachrichtigungen vom Windows Dev Center an die Kunden Ihrer App senden können, um diese zu einer Aktion zu animieren, z.B. eine App bewerten oder ein Add-On kaufen."
title: Senden von benutzerorientierten Pushbenachrichtigung an die Kunden Ihrer App
translationtype: Human Translation
ms.sourcegitcommit: 3e3c9737784c81f5eb882296a82a4dcd879363e1
ms.openlocfilehash: 817043579cfd068267c54f2eab9210ef303ca364

---

# Senden von benutzerorientierten Pushbenachrichtigung an die Kunden Ihrer App

Ihr Erfolg als App-Entwickler hängt davon ab, Ihre Kunden zum richtigen Zeitpunkt und mit der richtigen Botschaft zu erreichen. Windows Dev Center bietet eine datengestützte Kundenbindungsplattform, über die Sie allen Kunden oder nur einer bestimmten Gruppe von Windows10-Kunden, die den von Ihnen für ein [Kundensegment](create-customer-segments.md) definierten Kriterien entsprechen, Pushbenachrichtigungen senden können.

Mit benutzerorientierten Pushbenachrichtigungen können Sie Ihre Kunden zu einer Aktion animiern, z.B. eine App bewerten, ein Add-On kaufen, ein neues Feature ausprobieren oder eine andere App herunterladen.

> **Wichtig** Benutzerorientierte Pushbenachrichtigungen können nur mit UWP-Apps verwendet werden.

## Erste Schritte mit Pushbenachrichtigungen

Sie müssen drei übergeordnete Schritte durchführen, um Ihre Kunden mithilfe von Pushbenachrichtigungen zu erreichen.
1. **Registrieren Sie Ihre App für den Empfang von Pushbenachrichtigungen.** Fügen Sie hierzu Ihrer App einen Verweis auf das Microsoft Store Services SDK hinzu, und ergänzen Sie anschließend einige wenige Codezeilen, mit denen ein Benachrichtigungskanal zwischen dem Dev Center und Ihrer App registriert wird. Über diesen Kanal übermitteln wir Ihre Pushbenachrichtigungen an Ihre Kunden. Weitere Informationen finden Sie unter [Registrieren eines Benachrichtigungskanals](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.engagementclient.registernotificationchannelasync.aspx).
2. **Erstellen Sie mindestens ein Kundensegment, das Sie ansprechen möchten.** Sie können Ihre Kunden auf demografischen oder Einkommenskriterien basierend in Segmente gruppieren. Weitere Informationen finden Sie unter [Erstellen von Kundensegmenten](create-customer-segments.md).
3. **Erstellen Sie eine Pushbenachrichtigung, und senden Sie sie an ein bestimmtes Kundensegment.** So können Sie beispielsweise eine Benachrichtigung senden, die neue Kunden zu einer Bewertung Ihrer App animiert oder die ein Sonderangebot für den Kauf eines Add-Ons enthält.

## So erstellen und senden Sie eine benutzerorientierte Pushbenachrichtigung

1. Installieren Sie ggf. das [Microsoft Store Services SDK](http://aka.ms/store-em-sdk), und rufen Sie die [RegisterNotificationChannelAsync](https://msdn.microsoft.com/library/windows/apps/mt771190.aspx)Methode im Startcode Ihrer App auf, um Ihre App für den Empfang von Benachrichtigungen zu registrieren. Weitere Informationen zum Aufrufen dieser Methode finden Sie unter [Konfigurieren Ihrer App zum Empfangen von Dev Center-Benachrichtigungen](../monetize/configure-your-app-to-receive-dev-center-notifications.md).
2.  Wählen Sie im [WindowsDevCenter-Dashboard](https://developer.microsoft.com/dashboard/overview) Ihre App aus.
3.  Erweitern Sie im linken Navigationsmenü **Dienste**, und wählen Sie **Pushbenachrichtigungen** aus.
4.  Wählen Sie auf der Seite **Benutzerorientierte Pushbenachrichtigungen** die Option **Neue Benachrichtigung** aus.
5.  Wählen Sie im Abschnitt **Vorlage auswählen** den zu sendenden Benachrichtigungstyp aus. Weitere Informationen finden Sie unter [Vorlagenbenachrichtigungstypen](#notification-template-types).
  ![Benachrichtigungsvorlagen](images/push-notifications-template.png)
6.  Wählen Sie im Abschnitt **Benachrichtigungseinstellungen** einen **Namen** für die Benachrichtigung aus, und wählen Sie anschließend die **Kundengruppe** aus, an die die Benachrichtigung gesendet werden soll.
Wenn Sie noch kein Segment erstellt haben, wählen Sie **Neue Kundengruppe erstellen** aus. Beachten Sie, dass es 24Stunden dauert, bis ein neues Segmentfür Benachrichtigungen verfügbar ist. Weitere Informationen finden Sie unter [Erstellen von Kundensegmenten](create-customer-segments.md).
7.  Wenn Sie festlegen möchten, wann eine Benachrichtigung gesendet werden soll, deaktivieren Sie das Kontrollkästchen **Benachrichtigung sofort senden**, und wählen Sie ein bestimmtes Datum und eine Uhrzeit aus.
8.  Wenn die Benachrichtigung zu einem bestimmten Zeitpunkt ablaufen soll, deaktivieren Sie das Kontrollkästchen **Notification never expires**, und wählen Sie ein bestimmtes Ablaufdatum und eine Uhrzeit aus.
9.  Wählen Sie im Abschnitt der **Benachrichtigungsinhalt** im Menü **Sprache** die Sprachen aus, in denen die Benachrichtigung angezeigt werden soll. Weitere Informationen finden Sie unter [Übersetzen Ihrer Benachrichtigungen](#translate-your-notifications).
10. Geben Sie im Abschnitt **Optionen** Text ein, und konfigurieren Sie alle weiteren gewünschten Optionen. Wenn Sie mit einer Vorlage begonnen haben, sind einige Optionen standardmäßig ausgewählt, die Sie jedoch beliebig ändern können.
   Die verfügbaren Optionen variieren je nach Art der Benachrichtigung. Einige Optionen lauten:
   - **Aktivierungstyp** (interaktiver Popup-Typ). Sie können **Vordergrund**, **Hintergrund** oder **Protokoll** auswählen.
   - **Start** (interaktiver Popup-Typ). Sie können auswählen, ob die Benachrichtigung eine App oder Website öffnet.
   - **Track app launch rate** (interaktiver Popup-Typ). Wenn Sie messen möchten, wie gut Sie Ihre Kunden mithilfe der einzelnen Benachrichtigungen erreichen, aktivieren Sie dieses Kontrollkästchen. Weitere Informationen finden Sie unter [Messen der Benachrichtigungsleistung](#measure-notification-performance).
   - **Dauer** (interaktiver Popup-Typ). Sie können **Kurz** oder **Lang** auswählen.
   - **Szenario** (interaktiver Popup-Typ). Sie können **Standard**, **Alarm**, **Erinnerung** oder **Eingehender Anruf** auswählen.
   - **Basis-URI** (interaktiver Popup-Typ). Weitere Informationen finden Sie unter [BaseURI](https://msdn.microsoft.com/library/windows/apps/br208712).
   - **Add image query** (interaktiver Popup-Typ). Weitere Informationen finden Sie unter [addImageQuery](https://msdn.microsoft.com/library/windows/apps/br230847).
   - **Visuell**. Ein Bild, Video und Sound. Ausführlichere Informationen finden Sie unter [visual](https://msdn.microsoft.com/library/windows/apps/br230847).
   - **Eingabe**/**Aktion**/**Auswahl** (interaktiver Popup-Typ). Ermöglicht den Benutzern die Interaktion mit der Benachrichtigung. Weitere Informationen finden Sie unter [Adaptive und interaktive Popupbenachrichtigungen](../controls-and-patterns/tiles-and-notifications-adaptive-interactive-toasts.md#actions)
   - **Bindung** (interaktiver Kacheltyp). Die Popup-Vorlage. Ausführlichere Informationen finden Sie unter [binding](https://msdn.microsoft.com/en-us/library/windows/apps/br230843).

   > **Tipp** Versuchen Sie, mit der App [Notifications Visualizer](https://www.microsoft.com/store/apps/9nblggh5xsl1) adaptive Kacheln und interaktive Popupbenachrichtigungen zu entwerfen und zu testen.

11. Wählen Sie **Als Entwurf speichern** aus, um später weiter an der Benachrichtigung zu arbeiten, oder wählen Sie **Senden** aus, wenn Sie fertig sind.

> **Hinweis** Der Inhalt Ihrer Benachrichtigungen muss den [Inhaltsrichtlinien](https://msdn.microsoft.com/library/windows/apps/dn764944.aspx#content_policies) des Store entsprechen.

## Benachrichtigungsvorlagentypen

Sie können aus einer Vielzahl von Benachrichtigungsvorlagen auswählen.

-   **Leer (Popup).** Beginnen Sie mit einer leeren Popupbenachrichtigung, die Sie anpassen können. Eine Popupbenachrichtigung ist eine auf dem Bildschirm angezeigte Popupbenutzeroberfläche, die es Ihrer App ermöglicht, immer mit dem Kunden zu kommunizieren, unabhängig davon, ob dieser gerade eine andere App, die Startseite oder den Desktop anzeigt.
-   **Leer (Kachel).** Beginnen Sie mit einer leeren Kachelbenachrichtigung, die Sie anpassen können. Kacheln stellen die Apps auf der Startseite dar. Es gibt Live-Kacheln, d.h., der angezeigte Inhalt kann sich aufgrund von Benachrichtigungen ändern.
-   **Bitten um Bewertungen (Popup).** Eine Popupbenachrichtigung, die Ihre Kunden bittet, die App zu bewerten. Wenn der Kunde die Benachrichtigung auswählt, wird die Store-Bewertungsseite für Ihre App angezeigt.
-   **Um Feedback bitten (Popup).** Eine Popupbenachrichtigung, die Ihre Kunden um Feedback zur App bittet. Wenn der Kunde die Benachrichtigung auswählt, wird die Feedback-Hub-Seite für Ihre App angezeigt.
   > **Hinweis** Wenn Sie diesen Vorlagentyp auswählen, müssen Sie im Feld **Start** den Platzhalterwert {PACKAGE_FAMILY_NAME} durch den tatsächlichen Paketfamiliennamen (PFN) Ihrer App ersetzen. Sie finden den PFN Ihrer App auf der Seite [App-Identität](view-app-identity-details.md) (**App-Verwaltung** > **App-Identität**).

   ![Feld „Start“ für Feedback-Popup](images/push-notifications-feedback-toast-launch-box.png)
-   **Bewerben (Popup).** Eine Popupbenachrichtigung, mit der Sie für eine andere App Ihrer Wahl werben können. Wenn der Kunde die Benachrichtigung auswählt, wird der Store-Eintrag der anderen App angezeigt.
  > **Hinweis** Wenn Sie diesen Vorlagentyp auswählen, müssen Sie im Feld **Start** den Platzhalterwert **{Hier zu bewerbende ProductId}** durch die tatsächliche Store-ID des zu bewerbenden Artikels ersetzen. Die Store-ID finden Sie auf der Seite [App-Identität](view-app-identity-details.md) (**App-Verwaltung** > **App-Identität**).

  ![Feld „Start“ des Werbepopups](images/push-notifications-promote-toast-launch-box.png)
-   **Sonderangebot (Popup).** Eine Popupbenachrichtigung, mit der Sie ein Sonderangebot für Ihre App ankündigen können. Wenn der Kunde die Benachrichtigung auswählt, wird der Store-Eintrag Ihrer App angezeigt.
- **Aktualisierungsaufforderung (Popup).** Eine Popupbenachrichtigung, die Kunden mit einer älteren Version der App zur Installation der neuesten Version auffordert. Wenn der Kunde die Benachrichtigung auswählt, wird die Liste **Downloads und Updates** der Store-App angezeigt. Beachten Sie, dass Sie für diese Vorlage keine Kundensegmente erstellen müssen. Wir werden diese Benachrichtigung innerhalb von 24Stunden einplanen und nach Möglichkeit an alle Benutzer senden, die noch nicht die neueste Version Ihrer App ausführen.

## Messen der Benachrichtigungsleistung

Sie können ermitteln, wie gut Sie mit den einzelnen Benachrichtigungen Ihre Kunden erreichen.

###So messen Sie die Benachrichtigungsleistung

1.  Aktivieren Sie beim Erstellen einer Benachrichtigung im Abschnitt **Benachrichtigungsinhalt** das Kontrollkästchen **Track app launch rate**.
2.  Rufen Sie in Ihrer App die [ParseArgumentsAndTrackAppLaunch](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.parseargumentsandtrackapplaunch.aspx)-Methode auf, um Dev Center mitzuteilen, dass Ihre App als Reaktion auf eine benutzerorientierte Benachrichtigung gestartet wurde. Diese Methode wird vom Microsoft Store SDK bereitgestellt. Weitere Informationen zum Aufrufen dieser Methode finden Sie unter [Konfigurieren Ihrer App zum Empfangen von Dev Center-Benachrichtigungen](../monetize/configure-your-app-to-receive-dev-center-notifications.md).

###So zeigen Sie die Benachrichtigungsleistung an

Wenn Sie die Benachrichtigung und Ihre App wie oben beschrieben für das [Messen der Benachrichtigungsleistung](#to-measure-notification-performance) konfiguriert haben, können Sie auf dem Dashboard anzeigen, wie gut Ihre Benachrichtigungen ihren Zweck erfüllen.

1.  Wählen Sie im Dashboard eine Ihrer Apps aus.
2.  Erweitern Sie den Abschnitt **Dienste** im linken Menü, und wählen Sie dann **Pushbenachrichtigungen** aus, um die dieser App zugeordneten Benachrichtigungen anzuzeigen.
3.  Wählen Sie auf der Seite **Benutzerorientierte Pushbenachrichtigungen** die Option **In Bearbeitung** oder **Abgeschlossen** aus, und prüfen Sie die Spalten **Übermittlungsrate** und **App launch rate**, um die allgemeine Leistung der einzelnen Benachrichtigungen zu ermitteln.
4.  Um detailliertere Leistungsdetails anzuzeigen, wählen Sie einen Benachrichtigungsnamen aus. Im Abschnitt **Lieferstatistik** werden Daten zu **Anzahl** und **Prozentsatz** für die folgenden **Status**-Typen der Benachrichtigung angezeigt:
 - **Fehlgeschlagen**: Die Benachrichtigung wurde aus einem bestimmten Grund nicht übermittelt. Dies kann z.B. bei einem Problem im Windows-Benachrichtigungsdienst der Fall sein.
 - **Channel expiration failure**: Die Benachrichtigung konnte nicht übermittelt werden, da der Kanal zwischen der App und Dev Center abgelaufen ist. Dies kann beispielsweise vorkommen, wenn der Kunde Ihre App seit längerem nicht mehr geöffnet hat.
 - **Senden**: Die Benachrichtigung befindet sich in der Warteschlange für das Senden.
 - **Gesendet**: Die Benachrichtigung wurde gesendet.
 - **Startet**: Die Benachrichtigung wurde gesendet, der Kunde hat darauf geklickt, und Ihre App wurde daher geöffnet. Beachten Sie, dass hiermit nur das Starten der Apps nachverfolgt wird. Benachrichtigungen, die den Kunden zu weiteren Aktionen wie z.B. dem Öffnen des Store zum Hinterlassen einer Bewertung auffordern, sind nicht Teil dieses Status.
 - **Unbekannt**: Wir konnten den Status dieser Benachrichtigung nicht ermitteln.

## Übersetzen Ihrer Benachrichtigungen

Um die Wirkung von Benachrichtigungen zu maximieren, sollten Sie sie in die von den Kunden bevorzugten Sprachen übersetzen. Dev Center erleichtert Ihnen die Übersetzung Ihrer Benachrichtigungen, denn dies erfolgt mithilfe des Diensts [Microsoft Translator](https://msdn.microsoft.com/library/dd576287.aspx) automatisch.

1.  Nachdem Sie die Benachrichtigung in der Standardsprache geschrieben haben, wählen Sie **Sprachen hinzufügen** aus (unterhalb des Menüs **Sprachen** im Abschnitt **Benachrichtigungsinhalt**).
2.  Wählen Sie im Fenster **Sprachen hinzufügen** die weiteren Sprachen aus, in denen Ihre Benachrichtigungen angezeigt werden sollen, und wählen Sie anschließend **Aktualisieren** aus.
Die Benachrichtigung wird automatisch in die im Fenster **Sprachen hinzufügen** ausgewählten Sprachen übersetzt. Zudem werden diese Sprachen zum Menü **Sprache** hinzugefügt.
3.  Um die Übersetzung Ihrer Benachrichtigung anzuzeigen, wählen Sie im Menü **Sprache** die gerade hinzugefügte Sprache aus.

Beachten Sie im Zusammenhang mit Übersetzungen Folgendes:
 - Sie können die automatische Übersetzung überschreiben, indem Sie im Feld **Inhalt** etwas anderes für die jeweilige Sprache eingeben.
 - Wenn Sie der englischen Version der Benachrichtigung ein weiteres Textfeld hinzufügen, nachdem Sie eine automatische Übersetzung überschrieben haben, wird das neue Textfeld nicht zur übersetzten Benachrichtigung hinzugefügt. In diesem Fall müssen Sie das neue Textfeld manuell zu den einzelnen übersetzten Benachrichtigungen hinzufügen.
 - Wenn Sie den englischen Text nach dem Übersetzen der Benachrichtigung ändern, aktualisieren wir automatisch die übersetzten Benachrichtigungen entsprechend der Änderung. Dies erfolgt jedoch nicht, wenn Sie zuvor die ursprüngliche Übersetzung überschrieben haben.

## Verwandte Themen
- [Kacheln, Signale und Benachrichtigungen für UWP-Apps](../controls-and-patterns/tiles-badges-notifications.md)
- [Übersicht über die Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)](../controls-and-patterns/tiles-and-notifications-windows-push-notification-services--wns--overview.md)
- [Übersicht über Windows-Pushbenachrichtigungsdienst (Windows Push Notification Service, WNS) (Windows-Runtime-Apps)](https://msdn.microsoft.com/en-us/library/windows/apps/hh913756.aspx)
- [App „Notifications Visualizer”](https://www.microsoft.com/store/apps/9nblggh5xsl1)
- [StoreServicesEngagementManager.RegisterNotificationChannelAsync() | registerNotificationChannelAsync()-Methode](https://msdn.microsoft.com/library/windows/apps/mt771190.aspx)
- [Kundensegmentierung und Pushbenachrichtigungen: Eine neue Funktion des Windows Dev Center-Insider-Programms (Blogbeitrag)](https://blogs.windows.com/buildingapps/2016/08/17/customer-segmentation-and-push-notifications-a-new-windows-dev-center-insider-program-feature/#XTuCqrG8G5IMgWew.97)



<!--HONumber=Nov16_HO1-->


