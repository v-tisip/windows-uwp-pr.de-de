---
author: TylerMSFT
title: Unterstützen Ihrer App mit Hintergrundaufgaben
description: In den Themen in diesem Abschnitt wird gezeigt, wie Sie einfachen Code im Hintergrund ausführen, um auf Auslöser zu reagieren.
ms.assetid: EFF7CBFB-D309-4ACB-A2A5-28E19D447E32
ms.author: twhitney
ms.date: 08/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
ms.openlocfilehash: 9e5db1e03ac86768e2b1b1181cd2cc416a151a80
ms.sourcegitcommit: 7efffcc715a4be26f0cf7f7e249653d8c356319b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "3124073"
---
# <a name="support-your-app-with-background-tasks"></a>Unterstützen Ihrer App mit Hintergrundaufgaben


In den Themen in diesem Abschnitt wird gezeigt, wie Sie einfachen Code im Hintergrund ausführen, um auf Auslöser zu reagieren. Sie können mit Hintergrundaufgaben Funktionen bereitstellen, wenn Ihre App gerade ausgesetzt ist oder nicht ausgeführt wird. Sie können Hintergrundaufgaben auch für Echtzeitkommunikations-Apps wie VOIP, E-Mail und Sofortnachrichten verwenden.

## <a name="playing-media-in-the-background"></a>Wiedergeben von Medien im Hintergrund

Ab Windows 10 (Version 1607) ist die Wiedergabe von Audio im Hintergrund sehr viel einfacher. Weitere Informationen finden Sie unter [Wiedergeben von Medien im Hintergrund](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio).

## <a name="in-process-and-out-of-process-background-tasks"></a>Hintergrundaufgaben innerhalb und außerhalb von Prozessen

Es gibt zwei Ansätze für das Implementieren von Hintergrundaufgaben:

* In-Process: die app und der Hintergrundprozess ausgeführt, im gleichen Prozess
* Out-of-Process-: die app und der Hintergrundprozess in separaten Prozessen ausgeführt.

Die Unterstützung für Hintergrundaufgaben innerhalb von Prozessen wurde mit Windows 10 (Version 1607) eingeführt, um das Schreiben von Hintergrundaufgaben zu vereinfachen. Es ist jedoch weiterhin möglich, Hintergrundaufgaben außerhalb von Prozessen zu schreiben. Unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md) finden Sie Empfehlungen dazu, wann Sie eine Hintergrundaufgabe innerhalb eines Prozesses und wann außerhalb eines Prozesses schreiben sollten.

Out-of-Process-Hintergrundaufgaben sind stabiler, da der Hintergrundprozess Ihren app-Prozess Ausfall bringen kann, wenn ein Fehler auftritt. Höhere Stabilität geht jedoch mit einer höheren Komplexität der zum Verwalten der prozessübergreifenden Kommunikation zwischen der app und die Hintergrundaufgabe.

Out-of-Process-Hintergrundaufgaben werden als einfache Klassen implementiert, die [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794) Schnittstelle implementieren, die das Betriebssystem in einem separaten Prozess (backgroundtaskhost.exe) ausführt. Registrieren einer Hintergrundaufgabe mithilfe der [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) -Klasse. Der Klassenname wird beim Registrieren der Hintergrundaufgabe zum Angeben des Einstiegspunkts verwendet.

In Windows 10 (Version 1607) können Sie Hintergrundaktivitäten aktivieren, ohne eine Hintergrundaufgabe zu erstellen. Sie können stattdessen den hintergrundcode direkt in die Vordergrund-App-Prozess im ausführen.

Erste Schritte für das schnelle Erstellen von Hintergrundaufgaben finden Sie unter [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen](create-and-register-an-inproc-background-task.md).

Erste Schritte für das schnelle Erstellen von Hintergrundaufgaben außerhalb von Prozessen finden Sie unter [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](create-and-register-a-background-task.md).

> [!TIP]
> Ab Windows 10 müssen Sie eine App nicht mehr auf dem Sperrbildschirm platzieren, damit eine Hintergrundaufgabe dafür registriert werden kann.

## <a name="background-tasks-for-system-events"></a>Hintergrundaufgaben für Systemereignisse

Ihre App kann auf Systemereignisse reagieren, indem mit der [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224838)-Klasse eine Hintergrundaufgabe registriert wird. Eine App kann jeden der folgenden Systemereignistrigger verwenden (definiert in [**SystemTriggerType**](https://msdn.microsoft.com/library/windows/apps/br224839))

| Auslösername                     | Beschreibung                                                                                                    |
|----------------------------------|----------------------------------------------------------------------------------------------------------------|
| **InternetAvailable**            | Das Internet wird verfügbar.                                                                                |
| **NetworkStateChange**           | Eine Netzwerkänderung findet statt, z.B. werden die Kosten oder Verbindungsoptionen geändert.                                              |
| **OnlineIdConnectedStateChange** | Die mit dem Konto verbundene Online-ID wird geändert.                                                                 |
| **SmsReceived**                  | Auf einem installierten mobilen Breitbandgerät geht eine SMS ein.                                         |
| **TimeZoneChange**               | Die Zeitzone auf dem Gerät ändert sich (z.B. wenn das System die Uhrzeit auf die Sommerzeit umstellt). |

Weitere Informationen finden Sie unter [Reagieren auf Systemereignisse mit Hintergrundaufgaben](respond-to-system-events-with-background-tasks.md).

## <a name="conditions-for-background-tasks"></a>Bedingungen für Hintergrundaufgaben

Über Bedingungen können Sie steuern, wann die Hintergrundaufgaben ausgeführt werden, selbst nachdem sie ausgelöst wurde. Nach dem Auslösen wird die Hintergrundaufgabe erst ausgeführt, wenn alle ihre Bedingungen erfüllt sind. Sie können die folgenden Bedingungen verwenden (dargestellt durch die [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835)-Enumeration).

| Bedingungsname           | Beschreibung                       |
|--------------------------|-----------------------------------|
| **InternetAvailable**    | Das Internet muss verfügbar sein.   |
| **InternetNotAvailable** | Das Internet darf nicht verfügbar sein. |
| **SessionConnected**     | Die Sitzung muss verbunden sein.    |
| **SessionDisconnected**  | Die Sitzung darf nicht verbunden sein. |
| **UserNotPresent**       | Der Benutzer muss abwesend sein.            |
| **UserPresent**          | Der Benutzer muss anwesend sein.         |

Fügen Sie die **InternetAvailable**-Bedingung zur Hintergrundaufgabe [BackgroundTaskBuilder.AddCondition](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskBuilder) hinzu, um die Hintergrundaufgabe zu verzögern, bis der Netzwerkstapel ausgeführt wird. Dies spart Energie, da die Hintergrundaufgabe nicht ausgeführt, bis das Netzwerk verfügbar ist. Diese Bedingung stellt keine Aktivierung in Echtzeit bereit.

Wenn Ihre Hintergrundaufgabe Netzwerkkonnektivität erforderlich ist, legen Sie [IsNetworkRequested](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskBuilder) , um sicherzustellen, dass das Netzwerk während der Ausführung der Hintergrundaufgabe unterbrechungsfreie fest. Dies weist die Infrastruktur für Hintergrundaufgaben an, die Netzwerkverbindung für die Ausführung der Aufgabe auch dann beizubehalten, wenn sich das Gerät im verbundenen Standbymodus befindet. Wenn die Hintergrundaufgabe nicht **IsNetworkRequested**festgelegt wird, klicken Sie dann kann die Hintergrundaufgabe nicht Zugriff auf das Netzwerk, wenn sich dieses im verbundenen Standbymodus befindet (z. B., wenn der Bildschirm eines Smartphones ausgeschaltet ist).
 
[Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md)finden Sie weitere Informationen zu Bedingungen für Hintergrundaufgaben.

## <a name="application-manifest-requirements"></a>App-Manifestanforderungen

Damit Ihre App eine Hintergrundaufgabe registrieren kann, die außerhalb eines Prozesses ausgeführt wird, muss sie im Anwendungsmanifest deklariert werden. Hintergrundaufgaben, die im gleichen Prozess wie ihre Host-App ausgeführt werden, müssen nicht im Anwendungsmanifest deklariert werden. Weitere Informationen finden Sie unter [Deklarieren von Hintergrundaufgaben im Anwendungsmanifest](declare-background-tasks-in-the-application-manifest.md).

## <a name="background-tasks"></a>Hintergrundaufgaben

Die folgenden Echtzeitauslöser können verwendet werden, um einfachen benutzerdefinierten Code im Hintergrund auszuführen:

| Echtzeitauslöser  | Beschreibung |
|--------------------|-------------|
| **Steuerkanal** | Hintergrundaufgaben können eine Verbindung aufrechterhalten und Nachrichten auf dem Steuerkanal mithilfe des [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) empfangen. Wenn Ihre App ein Socket überwacht, können Sie den Socketbroker statt **ControlChannelTrigger** verwenden. Weitere Informationen zur Verwendung der Socketbroker finden Sie unter [SocketActivityTrigger](https://msdn.microsoft.com/library/windows/apps/dn806009). **ControlChannelTrigger** wird unter WindowsPhone nicht unterstützt. |
| **Timer** | Hintergrundaufgaben können in einem Intervall von bis zu 15 Minuten ausgeführt werden, und sie können mithilfe des [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843) auf die Ausführung zu einer bestimmten Zeit festgelegt werden. Weitere Informationen finden Sie im Thema [Ausführen einer Hintergrundaufgabe mit einem Timer](run-a-background-task-on-a-timer-.md). |
| **Push-Benachrichtigung** | Hintergrundaufgaben reagieren auf den [**PushNotificationTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700543), um unformatierte Pushbenachrichtigungen zu empfangen. |

**Hinweis**  

Universelle Windows-Apps müssen jedoch [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor Hintergrundtriggertypen registriert werden.

Rufen Sie [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) und anschließend [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) auf, wenn die App nach der Aktualisierung gestartet wird, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird. Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).

**Beschränkung der Anzahl an Triggerinstanzen:** Die Anzahl, wie viele Instanzen einiger Trigger eine App registrieren kann, ist begrenzt. Eine App kann   [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger), [MediaProcessingTrigger](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.mediaprocessingtrigger) und [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396) nur einmal pro Instanz der App registrieren. Wenn eine App dieses Limit überschreitet, wird von der Registrierung eine Ausnahme ausgelöst.

## <a name="system-event-triggers"></a>Systemereignistrigger

Die [**SystemTriggerType**](https://msdn.microsoft.com/library/windows/apps/br224839)-Enumeration stellt die folgenden Systemereignistrigger dar:

| Auslösername            | Beschreibung                                                       |
|-------------------------|-------------------------------------------------------------------|
| **UserPresent**         | Die Hintergrundaufgabe wird ausgelöst, wenn der Benutzer anwesend ist.   |
| **UserAway**            | Die Hintergrundaufgabe wird ausgelöst, wenn der Benutzer abwesend ist.    |
| **ControlChannelReset** | Die Hintergrundaufgabe wird ausgelöst, wenn ein Steuerkanal zurückgesetzt wird. |
| **SessionConnected**    | Die Hintergrundaufgabe wird ausgelöst, wenn die Sitzung eine Verbindung herstellt.   |

   
Das folgende Systemereignis löst ein Signal aus, wenn der Benutzer eine App auf den oder aus dem Sperrbildschirm verschoben hat.

| Auslösername                     | Beschreibung                                  |
|----------------------------------|----------------------------------------------|
| **LockScreenApplicationAdded**   | Dem Sperrbildschirm wird eine App-Kachel hinzugefügt.     |
| **LockScreenApplicationRemoved** | Eine App-Kachel wird vom Sperrbildschirm entfernt. |

 
## <a name="background-task-resource-constraints"></a>Ressourcenbeschränkungen für Hintergrundaufgaben

Hintergrundaufgaben sind einfach. Beschränken Sie die Ausführung von Hintergrundaufgaben auf ein Minimum, um die beste Benutzererfahrung für Vordergrund-Apps und Akkulaufzeit sicherzustellen. Dies wird erzwungen, indem auf Hintergrundaufgaben Ressourcenbeschränkungen angewendet werden.

Hintergrundaufgaben sind auf 30 Sekunden der Gesamtbetrachtungszeit beschränkt.

### <a name="memory-constraints"></a>Arbeitsspeicherbeschränkungen

Aufgrund der Ressourcenbeschränkungen für Geräte mit wenig Arbeitsspeicher kann für Hintergrundaufgaben ein Arbeitsspeicherlimit gelten. Dieses gibt die maximale Menge von Arbeitsspeicher an, der von der Hintergrundaufgabe verwendet werden kann. Wenn die Hintergrundaufgabe einen Vorgang ausführt, der dieses Limit überschreiten würde, tritt ein Fehler und ggf. eine Ausnahme über zu wenig Arbeitsspeicher auf, die von der Aufgabe behandelt werden kann. Wenn die Ausnahme über wenig Arbeitsspeicher von der Aufgabe nicht behandelt wird oder eine solche Ausnahme je nach Vorgang überhaupt nicht generiert wird, wird die Aufgabe sofort beendet.  

Sie können die [**MemoryManager**](https://msdn.microsoft.com/library/windows/apps/dn633831)-APIs verwenden, um durch Abfrage von aktueller Speicherauslastung und Limit die Obergrenze (falls vorhanden) zu ermitteln und die fortlaufende Speichernutzung der Hintergrundaufgabe zu überwachen.

### <a name="per-device-limit-for-apps-with-background-tasks-for-low-memory-devices"></a>Limit pro Gerät für Apps mit Hintergrundaufgaben für Geräte mit wenig Arbeitsspeicher

Geräte mit beschränktem Arbeitsspeicher haben ein Limit für die Anzahl von Apps, die gleichzeitig auf einem Gerät installierbar sind und Hintergrundaufgaben nutzen können. Wenn diese Zahl überschritten wird, tritt für den Aufruf von [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485), der zum Registrieren aller Hintergrundaufgaben erforderlich ist, ein Fehler auf.

### <a name="battery-saver"></a>Stromsparmodus

Solange Sie die App nicht davon befreien, bei aktiviertem Stromsparmodus Hintergrundaufgaben auszuführen und Pushbenachrichtigungen zu empfangen, verhindert der Stromsparmodus (falls aktiviert) die Ausführung von Hintergrundaufgaben, falls das Gerät nicht mit einer externen Stromquelle verbunden ist und der Akku eine angegebene Restmenge unterschreitet. Sie können Hintergrundaufgaben aber weiterhin registrieren.

Allerdings Unternehmens-apps und apps, die nicht im Microsoft Store veröffentlicht werden, finden Sie [im Hintergrund auf unbestimmte Zeit ausgeführt werden](run-in-the-background-indefinetly.md) , erfahren, wie Sie eine Funktionen verwenden, um eine Hintergrundaufgabe oder eine erweiterte ausführungssitzung ohne zeitliche Begrenzung im Hintergrund auszuführen.

## <a name="background-task-resource-guarantees-for-real-time-communication"></a>Die Ressourcen für Hintergrundaufgabe erlauben die Kommunikation in Echtzeit.

Um zu verhindern, dass Ressourcenkontingente die Echtzeitkommunikation stören, erhalten Hintergrundaufgaben, die den [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) und den [**PushNotificationTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700543) verwenden, garantierte Ressourcenkontingente (CPU) für jede ausgeführte Aufgabe. Die Ressourcenkontingente sind wie oben erwähnt und bleiben für diese Hintergrundaufgaben unverändert.

Ihre App benötigt keine anderen Funktionen, um die garantierten Ressourcenkontingente für [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)- und [**PushNotificationTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700543)-Hintergrundaufgaben zu erhalten. Das System behandelt sie immer als kritische Hintergrundaufgaben.

## <a name="maintenance-trigger"></a>Wartungsauslöser

Wartungsaufgaben werden nur ausgeführt, wenn das Gerät an die Stromversorgung angeschlossen ist. Weitere Informationen finden Sie unter [Verwenden von Wartungsauslösern](use-a-maintenance-trigger.md).

## <a name="background-tasks-for-sensors-and-devices"></a>Hintergrundaufgaben für Sensoren und Geräte

Ihre App kann über eine Hintergrundaufgabe mit der [**DeviceUseTrigger**](https://msdn.microsoft.com/library/windows/apps/dn297337)-Klasse auf Sensoren und Peripheriegeräte zugreifen. Dieser Auslöser ist für zeitaufwändige Vorgänge wie Datensynchronisierung oder Überwachung geeignet. Im Gegensatz zu Aufgaben für Systemereignisse kann eine **DeviceUseTrigger**-Aufgabe nur ausgelöst werden, wenn Ihre App im Vordergrund ausgeführt wird, und es können keine Bedingungen festgelegt werden.

> [!IMPORTANT]
> **DeviceUseTrigger** und **DeviceServicingTrigger** können nicht für prozessinterne Hintergrundaufgaben verwendet werden.

Einige kritische Gerätevorgänge (wie etwa zeitaufwändige Firmwareupdates) können mithilfe von [**DeviceUseTrigger**](https://msdn.microsoft.com/library/windows/apps/dn297337) nicht durchgeführt werden. Diese Vorgänge können nur auf dem PC und nur von einer privilegierten App durchgeführt werden, für die [**DeviceServicingTrigger**](https://msdn.microsoft.com/library/windows/apps/dn297315) verwendet wird. Eine *privilegierte App* ist eine App, die vom Gerätehersteller dafür autorisiert wurde, diese Vorgänge auszuführen. Mithilfe von Metadaten wird angegeben, welche App, falls zutreffend, als privilegierte App für ein Gerät festgelegt wurde. Weitere Informationen finden Sie unter [gerätesynchronisierung und-Update für Microsoft Store-Geräte-apps](http://go.microsoft.com/fwlink/p/?LinkId=306619)

## <a name="managing-background-tasks"></a>Verwalten von Hintergrundaufgaben

Hintergrundaufgaben können mit Ereignissen und lokalem Speicher Fortschritt, Beendigung und Abbruch an die App melden. Eine App kann außerdem die von einer Hintergrundaufgabe ausgelösten Ausnahmen auffangen und die Registrierung von Hintergrundaufgaben während eines App-Updates verwalten. Weitere Informationen:

[Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md)  
[Überwachen des Status und Abschlusses von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md)

Überprüfen Sie die Registrierung von Hintergrundaufgaben während des app-Starts. Stellen Sie sicher, dass Ihre app nicht gruppierten Hintergrundaufgaben in BackgroundTaskBuilder.AllTasks vorhanden sind. Registrieren Sie erneut diejenigen, die nicht vorhanden sind. Heben Sie die Registrierung alle Aufgaben, die nicht mehr benötigt werden. Dadurch wird sichergestellt, dass alle Hintergrund Aufgaben-Registrierung auf dem neuesten Stand sind, jedes Mal, wenn die app gestartet wird.

## <a name="related-topics"></a>Verwandte Themen

**Konzeptionelle Richtlinien für Multitasking in Windows 10**

* [Starten, Fortsetzen und Multitasking](index.md)

**Ratschläge für zugehörige Hintergrundaufgaben**

* [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md)
* [Zugreifen auf Sensoren und Geräte von einer Hintergrundaufgabe](access-sensors-and-devices-from-a-background-task.md)
* [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen](create-and-register-an-inproc-background-task.md)
* [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](create-and-register-a-background-task.md)
* [Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe](convert-out-of-process-background-task.md)
* [Debuggen einer Hintergrundaufgabe](debug-a-background-task.md)
* [Deklarieren von Hintergrundaufgaben im Anwendungsmanifest](declare-background-tasks-in-the-application-manifest.md)
* [Registrieren von Gruppen-Hintergrundaufgaben](group-background-tasks.md)
* [Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md)
* [So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)](https://docs.microsoft.com/visualstudio/debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio)
* [Überwachen des Status und Abschlusses von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md)
* [Wiedergeben von Medien im Hintergrund](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio)
* [Registrieren einer Hintergrundaufgabe](register-a-background-task.md)
* [Reagieren auf Systemereignisse mit Hintergrundaufgaben](respond-to-system-events-with-background-tasks.md)
* [Ausführen einer Hintergrundaufgabe für einen Timer](run-a-background-task-on-a-timer-.md)
* [Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird](run-a-background-task-during-updatetask.md)
* [Unbegrenzte Ausführung im Hintergrund](run-in-the-background-indefinetly.md)
* [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md)
* [Auslösen einer Hintergrundaufgabe in Ihrer App](trigger-background-task-from-app.md)
* [Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe](update-a-live-tile-from-a-background-task.md)
* [Verwenden eines Wartungsauslösers](use-a-maintenance-trigger.md)
