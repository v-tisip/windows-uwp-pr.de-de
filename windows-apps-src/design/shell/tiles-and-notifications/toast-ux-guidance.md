---
Description: Learn how to create effective and user-focused notifications that make your users productive and happy.
title: Popup-UX-Richtlinien
label: Toast UX Guidance
template: detail.hbs
ms.date: 05/18/2018
ms.topic: article
keywords: Windows 10, Uwp, Benachrichtigung, Sammlung, gruppieren, Ux, Ux-Richtlinien, Richtlinien, Aktion, Popup, Info-Center, Noninterruptive, effektive Benachrichtigungen, nicht zudringliche Benachrichtigungen, umsetzbare, verwalten, zu organisieren
ms.localizationpriority: medium
ms.openlocfilehash: 17861760ea5640eca01d3e69c1ed36a023c8f9d3
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8701491"
---
# <a name="toast-notification-ux-guidance"></a>Popup-Benachrichtigung-UX-Richtlinien
Benachrichtigungen sind notwendig, moderne Leben; Sie können Benutzer produktiver und erzwungenen mit apps und Websites sowie bleiben Sie auf dem aktuellen Updates werden. Benachrichtigungen können jedoch schnell Aktivieren von hilfreich sein, overbearing und aufdringlich, wenn sie nicht in einer benutzerorientiert Weise ausgelegt sind. Die Benachrichtigungen sind eine mit der rechten Maustaste Weg wird deaktiviert, und es ist unwahrscheinlich, sobald sie deaktiviert sind, sie werden aktiviert, erneut.  So stellen Sie sicher, dass Ihre Benachrichtigungen respektieren Bildschirmbereich des Benutzers und die Uhrzeit, damit Sie diesen Kanal Engagement geöffnet bleiben können.

> **Wichtige APIs**: [Windows Community Toolkit Benachrichtigungen Nuget-Paket](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)

Wir haben unser Windows-Telemetrie, als auch andere erste und Drittanbieter-Fallstudien, um mit vier Regeln um eine hervorragende Benachrichtigung Story woraus zusammengestellt analysiert.  Wir sind davon überzeugt diese Regeln gelten universell, unabhängig von der Plattform und hilft Ihre Benachrichtigungen, die sich positiv auf die Benutzer auswirken.

## <a name="1-actionable-notifications"></a>1. interaktiven Benachrichtigungen
Interaktiven Benachrichtigungen Benutzern Ihre Produktivität verhelfen, ohne Öffnen der app.  Während Sie sich gut, damit die app startet, ist dies nicht der einzige Maß Erfolg und ermöglicht, dass Benutzer zum Erreichen kleine befindet können Aufgaben ohne in Ihre app ein sehr leistungsfähiges Tool in Ihren Benutzern delighting sein.

![Umsetzbare Benachrichtigung mit den Schaltflächen Erinnerungen festlegen und reagieren auf die Benachrichtigung und Eingabe-Text-Feld](images/actionable-notification-example01.png)

Oben ist ein Beispiel für eine Benachrichtigung, die Aktionen nutzt. Der Effekt Schlichten Aufgaben ein Gefühl durchgehend positiv ist, und Sie können dieses Gefühl auf Ihre app oder Website schalten, durch das Senden von Benachrichtigungen, die interaktiven Inhalte enthalten. Interaktiven Benachrichtigungen können Ihnen auch die Produktivität steigern, sowohl im Enterprise- und Verbraucher Szenarien, die Zeit für die Aktion Benutzer verringern, indem Sie für diese kleinere Aufgaben durchlaufen. Es wird empfohlen, u. a. Aktionen, die Ihre Benutzer regelmäßig ausführen oder Dinge, die Sie Ihren Benutzern führen trainieren möchten.  Beispiele:
* Wie gewünscht, Favoriting, kennzeichnen oder starring Inhalt
* Genehmigen oder verweigern Ausgaben Berichte, Zeit aus, Berechtigungen usw..
* Inline Beantworten von Nachrichten, e-Mails, Gruppe chats, Kommentare usw..
* Fertigstellen des Aufträge mit [ausstehenden Updates](toast-pending-update.md)
* Alarme und Erinnerungen für einem späteren Zeitpunkt festlegen, als auch potenziell buchen Zeit in einem Kalender

Ctionable Benachrichtigungen sind sehr nützlich, damit Benutzer fühlen produktiv, Aufgaben und verfügen über eine großartige und effiziente Erfahrung mit der app oder Website.  Es gibt viele Möglichkeiten, hier! Wenn Sie Hilfe brainstorming Ideen möchten, passen Sie an das Windows-Team Benachrichtigungen wenden Sie sich zur Verfügung.  Sie 

## <a name="2-timing-and-urgency"></a>2. Timing und dringend
Im Gegensatz zu wie häufig zu Benachrichtigungen vorstellen empfiehlt sich Echtzeit nicht unbedingt! Daher wird empfohlen Entwickler denken Benutzer und wenn die Benachrichtigung, die sie senden möchten dringend Informationen ist oder nicht. Benutzer können problemlos mit zu vielen Informationen überladen werden und frustriert, wenn sie während sie, den Fokus versuchen unterbrochen werden. Windows bietet mehrere Optionen für das Ausmaß der Benachrichtigungen, die Sie senden möchten, sollten so:

**Unformatierte Benachrichtigungen:** Mithilfe von [unformatierten Benachrichtigungen](raw-notification-overview.md) kann hilfreich sein für viele Gründe, insbesondere bei Minimierung der Unterbrechung für den Benutzer hergestellt.  Senden von unformatierten Benachrichtigungen werden Ihre app im Hintergrund aktiviert, Sie überprüfen können, ob die Benachrichtigung, die eine sinnvolle, sofort in Ihrer app-Kontext bereitzustellen. Wenn es etwas Meinung angezeigt werden, wenn der Benutzer sofort ist, können Sie eine [lokale Popupbenachrichtigungen](send-local-toast.md) dort pop.  Wenn es etwas ist der Benutzer muss nicht finden jetzt, können Sie einen [geplanten Popups](https://blogs.msdn.microsoft.com/tiles_and_toasts/2016/09/30/quickstart-sending-an-alarm-in-windows-10/) zu erstellen, die zu einem späteren Zeitpunkt ausgelöst wird.

**Ghost Popup:** können Sie auch eine Benachrichtigung, der in der unteren rechten Ecke des Bildschirms etwa überspringen und stattdessen direkt an Info-Center senden die Benachrichtigung ausgelöst. Dies geschieht durch die [SuppressPopup-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastnotification.suppresspopup) auf "true" festlegen. Obwohl es möglicherweise einige Skepsis um ein einzublenden Benachrichtigungen nicht außerhalb Info-Center, wir finden Sie in einer 2-3 Mal höhere Engagement für Popups, die im Info-Center über live geholt Popup.  Benutzer sind schneller reagieren, wenn diese für den Empfang von Benachrichtigungen bereit und steuern können, wann sie unterbrochen werden deshalb Inhalte im Info-Center so viel effektiver noninvasively Benutzer benachrichtigt werden kann.

## <a name="3-clear-out-the-clutter"></a>3. löschen Sie die Übersichtlichkeit
Benachrichtigungen können für längere Zeit (standardmäßig drei Tage) im Info-Center beibehalten.  Es ist unbedingt notwendig, Sie sicher, dass der Inhalt, der hier befindet sich auf dem neuesten Stand und relevant ist stellen, jedes Mal, wenn der Benutzer Info-Center öffnet. Sie sind verschwendet Bildschirmbereich des Benutzers und belegen Steckplätze, die für etwas mehr auf dem neuesten Stand verwendet werden konnte.  Nehmen wir an der Benutzer Ihre e-Mail-Management-app installiert und empfängt zehn-e-Mails und zehn Benachrichtigungen zusammen mit diesen-e-Mails.  Je nach der gewünschten zu machen sollten Sie diese Benachrichtigungen löschen, wenn der Benutzer lesen die entsprechende e-Mail oder die App als eine Möglichkeit zum alten unübersichtliche Info-Center entfernen geöffnet hat.

Wir haben eine Reihe von [ToastNotificationHistory](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastnotificationhistory) APIs, mit denen Sie sehen, welche Inhalte im Info-Center ist, als auch diese Benachrichtigungen zu verwalten. Werden Sie respektieren Bildschirmbereich des Benutzers, und achten Sie darauf, dass Sie nur relevante und aktuelle Inhalte für Benutzer angezeigt werden.

## <a name="4-keeping-organized"></a>4. fernhalten organisiert
Wie bereits erwähnt, der Inhalt im Info-Center drei Tage beibehalten.  Organisieren Sie, können Sie die Benutzern, wählen Sie die Informationen, die sie schnell suchen, die Benachrichtigungen im Info-Center mit [Header](https://docs.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/toast-headers) oder [Sammlungen](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastcollection). Sie können ein Beispiel für einen Header unten sehen.

![Popup-Beispiele mit Header mit der Bezeichnung "Camping!!"](images/toast-headers-action-center.png)

Beide dieser Group Benachrichtigungen in einer Weise, sodass relevante Inhalte zusammen bleibt (d. h. wie getrennt werden verschiedene Sport Ligen in eine Sport-app oder Sortieren von Nachrichten nach Gruppenchat). Sammlungen sind eine deutlicher Möglichkeit, gruppenbenachrichtigungen, während die Header sind komplexer, aber beide ermöglichen Selektierung und wählen Sie Benachrichtigungen schneller. 

## <a name="other-resources"></a>Weitere Ressourcen
Diese vier oben genannten Punkte sind Richtlinien, die wir effektive über unseren eigenen Analyse der Telemetrie und über erste und Drittanbieter-Experimente gefunden haben. Denken Sie daran, jedoch, die diese Richtlinien sind: Richtlinien.  Wir sind davon überzeugt diese Regeln hilft Interaktion und Produktivität der Benachrichtigungen, aber nichts kann benutzerorientiert denken, und lernen Sie von Ihren eigenen Daten ersetzen.  

Wenn Sie noch heute Benachrichtigungen an Ihre UWP-app senden, können Sie Analytics anzeigen, auf wo sich Ihre Benachrichtigungen im [Partner Center befindet](https://partner.microsoft.com/dashboard)! Diese Daten stammt frei, wenn der [Store-Services-SDK](https://marketplace.visualstudio.com/items?itemName=AdMediator.MicrosoftStoreServicesSDK) oder die [WNS-APIs](https://docs.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)verwenden. Dieser Metriken erhalten Sie einen besseren Einblick in was, um Ihre Benachrichtigungen auf der Windows-Plattform geschieht ebenso wie Benutzer mit Benachrichtigungen interagiert werden. Diese Daten zugreifen, indem Sie auf das Menü auf der linken Seite einbeziehen > Benachrichtigungen, klicken auf der Registerkarte "Analyse" innerhalb der Seite "Notifications".  Dies befindet am gleichen Ort, den Sie zum Senden von Benachrichtigungen aus dem Partner Center wechseln möchten.

## <a name="related-topics"></a>Verwandte Themen

* [Popupinhalt](adaptive-interactive-toasts.md)
* [Unformatierte Benachrichtigungen](raw-notification-overview.md)
* [Ausstehendes Update](toast-pending-update.md)
* [Benachrichtigungsbibliothek auf GitHub (Teil des Windows-Community-Toolkit)](https://github.com/Microsoft/UWPCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.Notifications)
