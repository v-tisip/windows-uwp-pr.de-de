---
author: manoskow
Description: Learn how to create effective and user-focused notifications that make your users productive and happy.
title: Popup-UX-Richtlinien
label: Toast UX Guidance
template: detail.hbs
ms.author: mijacobs
ms.date: 05/18/2018
ms.topic: article
keywords: Windows 10, Uwp, Benachrichtigung, Sammlung, gruppieren, Ux, Ux-Richtlinien, Richtlinien, Aktion, Popup, Info-Center, Noninterruptive, effektive Benachrichtigungen, nicht zudringliche Benachrichtigungen, umsetzbare, verwalten, zu organisieren
ms.localizationpriority: medium
ms.openlocfilehash: 4ac7eab73f2bcfa57ac37ea6da99e1da6b235159
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6032701"
---
# <a name="toast-notification-ux-guidance"></a>Popup-Benachrichtigung UX-Richtlinien
Benachrichtigungen sind notwendig, moderne Leben; Sie können Benutzer produktiver und erzwungenen mit apps und Websites sowie bleiben Sie auf dem aktuellen durch Updates werden. Benachrichtigungen können jedoch schnell Aktivieren von hilfreich sein, overbearing und aufdringlich, wenn sie nicht in einer benutzerorientiert Weise ausgelegt sind. Die Benachrichtigungen sind eine mit der rechten Maustaste Weg ausgeschaltet wird, und es ist unwahrscheinlich, sobald sie deaktiviert sind, sie werden aktiviert, erneut.  Stellen Sie daher sicher, dass Ihre Benachrichtigungen respektieren Bildschirmbereich des Benutzers und die Uhrzeit, sind, sodass Sie diesen Kanal Engagement geöffnet bleiben können.

> **Wichtige APIs**: [Windows Community Toolkit Benachrichtigungen Nuget-Paket](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)

Wir haben unser Windows-Telemetrie, als auch andere um mit vier Regeln um eine hervorragende Benachrichtigung Story woraus zusammengestellt erste und Drittanbieter-Fallstudien, analysiert.  Wir sind davon überzeugt diese Regeln sind universell anwendbar ist, unabhängig von der Plattform und hilft Ihrer Notificaitons eine positive Auswirkung auf Ihre Benutzer haben.

## <a name="1-actionable-notifications"></a>1. interaktiven Benachrichtigungen
Interaktiven Benachrichtigungen Benutzern Ihre Produktivität verhelfen, ohne Öffnen der app.  Während sie großartige startet app haben, ist dies nicht der einzige Maß Erfolg und ermöglicht, dass Benutzer zum Erreichen klein ist können Aufgaben ohne in Ihre app ein sehr leistungsfähiges Tool in Ihren Benutzern delighting sein.

![Umsetzbare Benachrichtigung mit den Schaltflächen Erinnerungen festlegen und reagieren auf die Benachrichtigung und Eingabe-Text-Feld](images/actionable-notification-example01.png)

Oben ist ein Beispiel für eine Benachrichtigung, die Aktionen nutzt. Das Gefühl von Schlichten Aufgaben ein Gefühl durchgehend positiv ist, und Sie können dieses Gefühl auf Ihre app oder Website schalten, durch das Senden von Benachrichtigungen, die umsetzbare Inhalte enthalten. Interaktiven Benachrichtigungen können Ihnen auch die Produktivität steigern, sowohl im Enterprise- und Consumer-Szenarien, die Zeit für die Aktion Benutzer verringern, indem Sie für diese kleinere Aufgaben durchlaufen. Es wird empfohlen, u. a. Aktionen, die Ihre Benutzer regelmäßig ausführen oder Dinge, die auf die Ihre Benutzer tun trainieren möchten.  Beispiele:
* Wie gewünscht, Favoriting, kennzeichnen oder starring Inhalt
* Genehmigen oder verweigern Ausgaben Berichte, Zeit aus, Berechtigungen usw..
* Beantworten von Nachrichten, e-Mails, chats Gruppe Kommentare usw. Inline.
* Fertigstellen des Aufträge mit [ausstehenden Updates](toast-pending-update.md)
* Alarme und Erinnerungen für einem späteren Zeitpunkt festlegen sowie buchen potenziell Zeit in einem Kalender

Ctionable Benachrichtigungen sind ein sehr leistungsfähiges Tool, damit Benutzer produktiv spüren, Aufgaben und verfügen über eine großartige und effiziente Erfahrung mit der app oder Website.  Es gibt viele Möglichkeiten, hier! Wenn Sie Hilfe brainstorming Ideen möchten, passen Sie wenden Sie sich an das Windows-Team Benachrichtigungen zur Verfügung.  Sie 

## <a name="2-timing-and-urgency"></a>2. Timing und dringend
Im Gegensatz zu wie unser häufig Benachrichtigungen denken ist Echtzeit nicht notwendigerweise die besten! Daher wird empfohlen Entwickler denken Benutzer und wenn die Benachrichtigung, die sie senden möchten dringend Informationen ist oder nicht. Benutzer können problemlos mit zu vielen Informationen überladen werden und frustriert, wenn sie während sie, den Fokus versuchen unterbrochen werden. Windows bietet mehrere Optionen für das Ausmaß der Benachrichtigungen, die Sie senden möchten, sollten so:

**Unformatierte Benachrichtigungen:** Mithilfe von [unformatierten Benachrichtigungen](raw-notification-overview.md) kann hilfreich sein für viele Gründe, insbesondere bei der Minimierung der Unterbrechung für den Benutzer hergestellt.  Senden von unformatierten Benachrichtigungen wird Ihre app im Hintergrund, reaktivieren damit Sie überprüfen können, ob die Benachrichtigung eine sinnvolle, sofort in Ihrer app-Kontext bereitzustellen. Wenn es etwas Meinung angezeigt werden, wenn der Benutzer sofort ist, können Sie von dort aus einer [lokalen Popupbenachrichtigung](send-local-toast.md) aufklappen.  Wenn es etwas ist der Benutzer muss nicht finden jetzt, können Sie zum Erstellen eines [geplanten Popups](https://blogs.msdn.microsoft.com/tiles_and_toasts/2016/09/30/quickstart-sending-an-alarm-in-windows-10/) , die zu einem späteren Zeitpunkt ausgelöst wird.

**Ghost Popup:** können Sie auch eine Benachrichtigung, der in der unteren rechten Ecke des Bildschirms quot überspringen und stattdessen direkt an Info-Center senden die Benachrichtigung ausgelöst. Dies geschieht durch die [SuppressPopup-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastnotification.suppresspopup) auf "true" festlegen. Obwohl möglicherweise gibt es einige Skepsis um ein nicht außerhalb Info-Center Benachrichtigungen einzublenden, sehen wir eine 2 – 3 Mal höheren Engagement für Popups, die im Info-Center über live geholt Popup.  Benutzer sind besser reagiert, wenn diese für den Empfang von Notificaitons bereit und steuern können, wann sie unterbrochen werden deshalb Inhalte im Info-Center so viel effektiver noninvasively Benutzer benachrichtigt werden kann.

## <a name="3-clear-out-the-clutter"></a>3. löschen Sie die unübersichtliche
Benachrichtigungen können für längere Zeit (standardmäßig drei Tage) im Info-Center beibehalten wird.  Es ist unbedingt notwendig, dass Sie Sie sicher, dass die Inhalte, die hier befindet sich auf dem neuesten Stand und relevant ist stellen, jedes Mal, wenn der Benutzer Info-Center öffnet. Sie sind vergeuden Bildschirmbereich des Benutzers und belegen Steckplätze, die für etwas mehr auf dem neuesten Stand verwendet werden konnte.  Nehmen wir an der Benutzer Ihre e-Mail-Management-app installiert und empfängt zehn-e-Mails und zehn Benachrichtigungen zusammen mit diesen-e-Mails.  Je nach der gewünschten zu machen sollten Sie diese Benachrichtigungen löschen, wenn der Benutzer lesen Sie die entsprechende e-Mail oder die App als eine Möglichkeit zum Entfernen von alten unübersichtliche Info-Center geöffnet hat.

Wir haben eine Reihe von [ToastNotificationHistory](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastnotificationhistory) APIs, mit denen Sie feststellen, welche Inhalte im Info-Center ist, als auch diese Benachrichtigungen zu verwalten. Werden Sie respektieren Bildschirmbereich des Benutzers, und achten Sie darauf, dass Sie nur relevante und aktuelle Inhalte für Benutzer zu sehen sind.

## <a name="4-keeping-organized"></a>4. fernhalten organisiert
Wie bereits erwähnt, der Inhalt im Info-Center für drei Tage beibehalten.  Organisieren Sie, können Sie die Benutzern, wählen Sie die Informationen, die sie schnell suchen, die Benachrichtigungen im Info-Center mit [Header](https://docs.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/toast-headers) oder [Sammlungen](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastcollection). Sie können ein Beispiel für einen Header unten sehen.

![Popup-Beispiele mit Headern mit der Bezeichnung "Camping!!"](images/toast-headers-action-center.png)

Beide dieser Group Benachrichtigungen in einer Weise, sodass relevante Inhalte zusammen bleibt (d. h. getrennt werden verschiedene Sport Ligen in eine Sport-app oder Sortieren von Nachrichten nach Gruppenchat denken). Sammlungen sind eine deutlicher Möglichkeit, Gruppe Notificaitons, während die Header sind subtilere, aber beide ermöglichen Selektierung und schneller, Benachrichtigungen auswählen. 

## <a name="other-resources"></a>Weitere Ressourcen
Diese vier oben genannten Punkte sind Richtlinien, die wir effektive über unseren eigenen Analyse der Telemetrie und über erste und Drittanbieter-Experimente gefunden haben. Denken Sie daran, jedoch, die diese Richtlinien sind: Richtlinien.  Wir sind davon überzeugt diese Regeln hilft Interaktion und Produktivität von Benachrichtigungen, aber nichts kann Benutzer-orientierte denken, und lernen Sie von Ihren eigenen Daten ersetzen.  

Wenn Sie noch heute Benachrichtigungen an Ihre UWP-app senden, können Sie Analytics anzeigen, auf was Ihre Benachrichtigungen im [Dev Center](https://developer.microsoft.com/en-us/windows)wurde aus! Diese Daten stammen frei, bei der Verwendung des [Store Services SDK](https://marketplace.visualstudio.com/items?itemName=AdMediator.MicrosoftStoreServicesSDK) oder die [WNS-APIs](https://docs.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview). Dieser Metriken erhalten Sie einen besseren Einblick in was, um Ihre Benachrichtigungen auf der Windows-Plattform geschieht ebenso wie Benutzer mit Benachrichtigungen interagiert werden. Auf diese Dashboard zugreifen, indem Sie auf das Menü auf der linken Seite einbeziehen > Benachrichtigungen, klicken Sie auf der Registerkarte "Analyse" innerhalb der Seite "Notifications".  Dies befindet am gleichen Ort, den Sie zum Senden von Benachrichtigungen aus dem Dev Center-Portal wechseln möchten.

## <a name="related-topics"></a>Verwandte Themen

* [Popupinhalt](adaptive-interactive-toasts.md)
* [Unformatierte Benachrichtigungen](raw-notification-overview.md)
* [Ausstehendes Update](toast-pending-update.md)
* [Benachrichtigungsbibliothek auf GitHub (Teil des Windows-Community-Toolkit)](https://github.com/Microsoft/UWPCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.Notifications)
