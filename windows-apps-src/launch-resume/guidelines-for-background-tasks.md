---
author: TylerMSFT
title: "Richtlinien für Hintergrundaufgaben"
description: "Stellen Sie sicher, dass Ihre App die Anforderungen für die Ausführung von Hintergrundaufgaben erfüllt."
ms.assetid: 18FF1104-1F73-47E1-9C7B-E2AA036C18ED
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: c9bf682e6818f7c9854604448e52aa0111605a05
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="guidelines-for-background-tasks"></a>Richtlinien für Hintergrundaufgaben

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Stellen Sie sicher, dass Ihre App die für die Ausführung von Hintergrundaufgaben erforderlichen Anforderungen erfüllt.

## <a name="background-task-guidance"></a>Ratschläge zu Hintergrundaufgaben

Beachten Sie beim Entwickeln Ihrer Hintergrundaufgabe und vor dem Veröffentlichen Ihrer App die folgenden Empfehlungen.

Wenn Sie eine Hintergrundaufgabe zur Medienwiedergabe im Hintergrund verwenden, finden Sie unter [Wiedergeben von Medien im Hintergrund](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio) Informationen zu Verbesserungen in Windows 10, Version 1607, die dies erleichtern.

**Hintergrundaufgaben innerhalb von Prozessen im Vergleich zu Hintergrundaufgaben außerhalb von Prozessen:** Mit Windows10, Version1607, wurden [Hintergrundaufgaben innerhalb von Prozessen](create-and-register-an-inproc-background-task.md) eingeführt. Dadurch kann Hintergrundcode im selben Prozess ausgeführt werden wie die Vordergrund-App. Beachten Sie bei der Entscheidung für Hintergrundaufgaben innerhalb oder außerhalb von Prozessen folgende Faktoren:

|Überlegung | Auswirkungen |
|--------------|--------|
|Flexibilität   | Wenn der Hintergrundprozess in einem anderen Prozess ausgeführt wird, hat ein Absturz im Hintergrundprozess keine Auswirkungen auf Ihre Vordergrund-Anwendung. Außerdem kann die Hintergrundaktivität beendet werden, sogar innerhalb Ihrer App, wenn Ausführungszeitlimits überschritten werden. Das Trennen der Hintergrundarbeit in eine Aufgabe separat von der Vordergrund-App ist möglicherweise die bessere Wahl, wenn Vordergrund- und Hintergrundprozess nicht miteinander kommunizieren müssen (ein wesentlicher Vorteil von Hintergrundaufgaben innerhalb von Prozessen ist nämlich der, dass keine Kommunikation zwischen Prozessen erforderlich ist). |
|Einfachheit    | Hintergrundaufgaben innerhalb von Prozessen erfordern keine prozessübergreifende Kommunikation und sind einfacher zu schreiben.  |
|Verfügbare Trigger | Hintergrundaufgaben innerhalb von Prozessen unterstützen nicht die folgenden Trigger: [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) und **IoTStartupTask** |
|VoIP | Hintergrundaufgaben innerhalb von Prozessen unterstützen nicht die Aktivierung einer VoIP-Hintergrundaufgabe in Ihrer Anwendung. |  

**CPU-Kontingente:** Hintergrundaufgaben sind durch die Gesamtbetrachtungszeit eingeschränkt, die ihnen basierend auf dem Triggertyp zugeteilt wird. Die meisten Trigger sind auf 30Sekunden der Gesamtbetrachtungszeit beschränkt. Einige können jedoch bis zu 10Minuten ausgeführt werden, um rechenintensive Aufgaben abschließen zu können. Hintergrundaufgaben sollten klein bleiben, um den Akku zu schonen und ein besseres Benutzererlebnis für die Apps im Vordergrund zu ermöglichen. Die für Hintergrundaufgaben geltenden Ressourcenbeschränkungen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

**Verwalten von Hintergrundaufgaben:** Ihre App muss eine Liste mit registrierten Hintergrundaufgaben abrufen, sich für Fortschritts- und Vervollständigungshandler registrieren und diese Ereignisse angemessen behandeln. Ihre Hintergrundaufgabenklassen müssen Fortschritt, Abbruch und Abschluss berichten. Weitere Informationen finden Sie unter [Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md) und [Überwachen des Status und Abschlusses von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md).

**Verwenden Sie [BackgroundTaskDeferral](https://msdn.microsoft.com/library/windows/apps/hh700499):**: Wenn Ihre Hintergrundaufgabenklasse asynchronen Code ausführt, müssen Sie Verzögerungen verwenden. Andernfalls kann Ihre Hintergrundaufgabe vorzeitig beendet werden, wenn die [Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx)-Methode (oder die [OnBackgroundActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx)-Methode bei Hintergrundaufgaben innerhalb von Prozessen) abgeschlossen wird. Weitere Informationen finden Sie unter [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](create-and-register-a-background-task.md).

Alternativ können Sie eine Verzögerung bewirken und asynchrone Methodenaufrufe mit **async/await** abschließen. Schließen Sie die Verzögerung nach den **await**-Methodenaufrufen.

**Aktualisieren des App-Manifests:** Deklarieren Sie für Hintergrundaufgaben außerhalb von Prozessen, die in einem separaten Prozess ausgeführt werden, im Anwendungsmanifest die einzelnen Hintergrundaufgaben gemeinsam mit dem verwendeten Triggertyp. Andernfalls kann Ihre App die Hintergrundaufgaben zur Laufzeit nicht registrieren.

Hintergrundaufgaben, die im gleichen Prozess wie die Vordergrund-App ausgeführt werden, müssen sich im Anwendungsmanifest nicht selbst deklarieren. Weitere Informationen zum Deklarieren von Hintergrundaufgaben außerhalb von Prozessen, die in einem separaten Prozess im Manifest ausgeführt werden, finden Sie unter [Deklarieren von Hintergrundaufgaben im Anwendungsmanifest](declare-background-tasks-in-the-application-manifest.md).

**Vorbereiten von App-Updates:** Wenn Ihre App aktualisiert werden soll, erstellen und registrieren Sie eine **ServicingComplete**-Hintergrundaufgabe (siehe [SystemTriggerType](https://msdn.microsoft.com/library/windows/apps/br224839)), um die Registrierung von Hintergrundaufgaben für die vorherige Version der App aufzuheben und die Hintergrundaufgaben für die neue Version zu registrieren. Dies ist auch ein geeigneter Zeitpunkt, um App-Updates durchzuführen, die möglicherweise außerhalb des Kontexts der Ausführung im Vordergrund erforderlich sind.

**Anfordern der Ausführung von Hintergrundaufgaben:**

> **Wichtig**  Ab Windows 10 ist es keine Voraussetzung mehr, dass sich Apps auf dem Sperrbildschirm befinden, um Hintergrundaufgaben auszuführen.

UWP (Universelle Windows-Plattform)-Apps können alle unterstützten Aufgabentypen ausführen, ohne auf dem Sperrbildschirm angeheftet zu sein. Apps müssen jedoch vor dem Registrieren einer Hintergrundaufgabe [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen. Diese Methode gibt [**BackgroundAccessStatus.Denied**](https://msdn.microsoft.com/library/windows/apps/hh700439) zurück, wenn der Benutzer Berechtigungen für Hintergrundaufgaben für Ihre App in den Geräteeinstellungen explizit verweigert hat.
## <a name="background-task-checklist"></a>Prüfliste für Hintergrundaufgaben

*Gilt sowohl für Hintergrundaufgaben innerhalb als auch außerhalb von Prozessen*

-   Verknüpfen Sie Ihre Hintergrundaufgabe mit dem korrekten Trigger.
-   Fügen Sie Bedingungen hinzu, die für das erfolgreiche Ausführen Ihrer Hintergrundaufgabe sorgen.
-   Behandeln Sie Status, Abschluss und Abbruch von Hintergrundaufgaben.
-   Registrieren Sie Ihre Hintergrundaufgaben während des App-Starts erneut. Dadurch wird sichergestellt, dass sie beim ersten Start der App registriert sind. Zudem können Sie mit dieser Methode feststellen, ob der Benutzer die Ausführung von Hintergrundaufgaben in Ihrer App deaktiviert hat (falls die Registrierung fehlschlägt)
-   Prüfen Sie Ihre App auf Fehler bei der Registrierung von Hintergrundaufgaben. Führen Sie die Registrierung der Hintergrundaufgabe ggf. mit anderen Parameterwerten erneut durch.
-   Für alle Gerätefamilien mit Ausnahme von Desktops können Hintergrundaufgaben beendet werden, wenn der Arbeitsspeicher des Geräts knapp wird. Wenn eine Ausnahme über wenig Arbeitsspeicher nicht angezeigt oder von der App nicht behandelt wird, wird die Hintergrundaufgabe ohne Warnung und ohne Auslösen des OnCanceled-Ereignisses beendet. Dadurch soll die Benutzerfreundlichkeit der App im Vordergrund sichergestellt werden. Entwerfen Sie die Hintergrundaufgabe so, dass dieses Szenario behandelt werden kann.

*Gilt nur für Hintergrundaufgaben außerhalb von Prozessen*

-   Erstellen Sie Ihre Hintergrundaufgabe in einer Komponente für Windows-Runtime.
-   Zeigen Sie keine UI außer Popup-, Kachel- und Signalupdates von der Hintergrundaufgabe an.
-   Fordern Sie in der [Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx)-Methode Verzögerungen für jeden asynchronen Methodenaufruf an, und schließen Sie diese, wenn die Methode abgeschlossen wurde. Sie können auch eine Verzögerung mit **async/await** verwenden.
-   Verwenden Sie den dauerhaften Speicher, um Daten für die Hintergrundaufgabe und die App freizugeben.
-   Deklarieren Sie jede Hintergrundaufgabe im Anwendungsmanifest zusammen mit dem Triggertyp, mit dem sie verwendet wird. Überprüfen Sie die Korrektheit von Einstiegspunkten und Triggertypen.
-   Geben Sie im Manifest nur dann ein Executable-Element an, wenn Sie einen Trigger nutzen, der im selben Kontext wie die App ausgeführt werden soll (z.B. [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)).

*Gilt nur für Hintergrundaufgaben innerhalb von Prozessen*

- Stellen Sie beim Abbrechen einer Aufgabe sicher, dass der `BackgroundActivated`-Ereignishandler vorhanden ist, bevor der Abbruch eintritt, oder der gesamte Prozess wird beendet.
-   Schreiben Sie Hintergrundaufgaben mit kurzer Laufzeit. Hintergrundaufgaben sind auf 30 Sekunden der Gesamtbetrachtungszeit beschränkt.
-   Verlassen Sie sich bei Hintergrundaufgaben nicht auf Benutzerinteraktionen.

## <a name="windows-background-task-checklist-for-lock-screen-capable-apps"></a>Windows: Prüfliste für Hintergrundaufgaben für sperrbildschirmfähige Apps

Befolgen Sie diese Richtlinien bei der Entwicklung von Hintergrundaufgaben, die auch auf dem Sperrbildschirm verwendet werden könnten. Befolgen Sie die Richtlinien in [Richtlinien und Prüfliste für Kacheln auf dem Sperrbildschirm](https://msdn.microsoft.com/library/windows/apps/hh465403).

-   Überprüfen Sie, ob Ihre App überhaupt auf dem Sperrbildschirm erscheinen muss, bevor Sie sie als sperrbildschirmfähige App entwickeln. Weitere Informationen hierzu finden Sie in der [Übersicht über den Sperrbildschirm](https://msdn.microsoft.com/library/windows/apps/hh779720).

-   Stellen Sie sicher, dass Ihre App auch ohne auf dem Sperrbildschirm zu erscheinen funktioniert.

-   Fügen Sie eine mit [**PushNotificationTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700543), [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) oder [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843) registrierte Hintergrundaufgabe ein, und deklarieren Sie sie im App-Manifest. Überprüfen Sie die Korrektheit von Einstiegspunkten und Triggertypen. Dies wird für die Zertifizierung benötigt und damit der Benutzer die App auf dem Sperrbildschirm platzieren kann.

**Hinweis**  
Dieser Artikel ist für Windows10-Entwickler bestimmt, die Apps für die universelle Windows-Plattform (UWP) schreiben. Wenn Sie für Windows8.x oder Windows Phone8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md)
* [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](create-and-register-a-background-task.md)
* [Deklarieren von Hintergrundaufgaben im Anwendungsmanifest](declare-background-tasks-in-the-application-manifest.md)
* [Wiedergeben von Medien im Hintergrund](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio)
* [Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md)
* [Überwachen des Status und Abschlusses von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md)
* [Registrieren einer Hintergrundaufgabe](register-a-background-task.md)
* [Reagieren auf Systemereignisse mit Hintergrundaufgaben](respond-to-system-events-with-background-tasks.md)
* [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md)
* [Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe](update-a-live-tile-from-a-background-task.md)
* [Verwenden eines Wartungsauslösers](use-a-maintenance-trigger.md)
* [Ausführen einer Hintergrundaufgabe für einen Timer](run-a-background-task-on-a-timer-.md)
* [Debuggen einer Hintergrundaufgabe](debug-a-background-task.md)
* [So wird's gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in Windows Store-Apps (beim Debuggen)](http://go.microsoft.com/fwlink/p/?linkid=254345)

 

 
