---
Description: Learn how to create effective and user-focused notifications that make your users productive and happy.
title: Popup-UX-Richtlinien
label: Toast UX Guidance
template: detail.hbs
ms.date: 05/18/2018
ms.topic: article
keywords: Windows 10, Uwp, Benachrichtigung, Sammlung, gruppieren, Ux, Ux-Richtlinien, Richtlinien, Aktion, Popup, Info-Center, Noninterruptive, effektive Benachrichtigungen, nicht zudringliche Benachrichtigungen, umsetzbare, verwalten, zu organisieren
ms.localizationpriority: medium
ms.openlocfilehash: 878df85db9ab0e33db06a86ddb726f07dc28f013
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8918849"
---
# <a name="toast-notification-ux-guidance"></a>Popup-Benachrichtigung-UX-Richtlinien
Benachrichtigungen sind notwendig, des modernen Lebenszyklus; Sie können Benutzer produktiver und erzwungenen mit apps und Websites sowie bleiben Sie auf dem aktuellen Updates werden. Benachrichtigungen können jedoch schnell Aktivieren von hilfreich sein, overbearing und aufdringlich, wenn sie nicht auf eine Weise benutzerorientiert ausgelegt sind. Die Benachrichtigungen sind eine mit der rechten Maustaste Weg wird deaktiviert, und es ist unwahrscheinlich, sobald sie deaktiviert sind, sie werden aktiviert, erneut.  Stellen Sie daher sicher, dass Ihre Benachrichtigungen respektieren Bildschirmbereich des Benutzers und die Uhrzeit ist, damit Sie diesen Kanal Engagement geöffnet bleiben können.

> **Wichtige APIs**: [Windows Community Toolkit Benachrichtigungen Nuget-Paket](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)

Wir haben unser Windows-Telemetrie, als auch andere erste und Drittanbieter-Fallstudien, um zusammengestellt, mit vier Regeln, um Was ist eine hervorragende Benachrichtigung Story an analysiert.  Wir sind davon überzeugt diese Regeln gelten universell, unabhängig von der Plattform und hilft, Ihre Benachrichtigungen, die sich positiv auf die Benutzer auswirken.

## <a name="1-actionable-notifications"></a>1. interaktiven Benachrichtigungen
Interaktiven Benachrichtigungen können Ihre Benutzer produktiv sein, ohne Öffnen der app.  Während sie großartige startet app haben, ist dies nicht der einzige Maß Erfolg und ermöglicht, dass Benutzer zum Erreichen klein ist können Aufgaben ohne in Ihre app ein sehr leistungsfähiges Tool in Ihren Benutzern delighting sein.

![Umsetzbare Benachrichtigung mit den eingegebenen Text ein, und Schaltflächen, um die Erinnerung und reagieren auf die Benachrichtigung](images/actionable-notification-example01.png)

Über wird ein Beispiel für eine Benachrichtigung, die Aktionen nutzt. Der Effekt der beendet Aufgaben ist ein Gefühl durchgehend positiv, und Sie können dieses Gefühl auf Ihre app oder Website schalten, durch das Senden von Benachrichtigungen, die interaktiven Inhalte enthalten. Interaktiven Benachrichtigungen können Ihnen auch die Produktivität steigern, sowohl in geschäftlichen und Szenarien, die Zeit für die Aktion Benutzer verringern, indem Sie für diese kleinere Aufgaben durchlaufen. Es wird empfohlen, u. a. Aktionen, die Ihre Benutzer regelmäßig ausführen oder Dinge, die Sie Ihre Benutzer tun trainieren möchten.  Beispiele:
* Wie gewünscht, Favoriting, kennzeichnen oder starring Inhalt
* Genehmigen oder verweigern Ausgaben Berichte, Zeit aus, Berechtigungen usw..
* Inline Beantworten von Nachrichten, e-Mails, Gruppe chats, Kommentare usw..
* Fertigstellen des Aufträge mit [ausstehenden Updates](toast-pending-update.md)
* Alarme und Erinnerungen für einem späteren Zeitpunkt festlegen sowie buchen potenziell Zeit in einem Kalender

Interaktiven Benachrichtigungen sind sehr nützlich sein, damit Benutzer produktiv arbeiten können, Aufgaben und hervorragende und effiziente Erfahrung mit der app oder Website.  Es gibt viele Möglichkeiten hier! Wenn Sie Hilfe brainstorming Ideen möchten, können Sie wenden Sie sich an das Windows-Team Benachrichtigungen.

## <a name="2-timing-and-urgency"></a>2. Timing und dringend
Im Gegensatz zu wie häufig zu Benachrichtigungen vorstellen empfiehlt sich Echtzeit nicht unbedingt! Daher wird empfohlen Entwickler denken Benutzer und ob die Benachrichtigung, die sie senden dringend Informationen ist oder nicht. Benutzer können mit zu vielen Informationen leicht überladen werden und frustriert, wenn sie während sie, den Fokus versuchen unterbrochen werden. Windows bietet mehrere Optionen für so das Ausmaß der Benachrichtigungen, die Sie senden möchten, sollten:

**Unformatierte Benachrichtigungen:** Mithilfe von [unformatierten Benachrichtigungen](raw-notification-overview.md) kann hilfreich sein für viele Gründe, insbesondere bei der Unterbrechung für den Benutzer minimieren hergestellt.  Senden von unformatierten Benachrichtigungen werden Ihre app im Hintergrund aktiviert, Sie überprüfen können, ob die Benachrichtigung, die eine sinnvolle, sofort in Ihrer app-Kontext bereitzustellen. Ist dies etwas Meinung angezeigt werden, wenn der Benutzer sofort, können Sie einer [lokalen Popupbenachrichtigung](send-local-toast.md) dort handelt.  Wenn es etwas ist der Benutzer muss nicht finden jetzt, können Sie einem [geplanten Popups](https://blogs.msdn.microsoft.com/tiles_and_toasts/2016/09/30/quickstart-sending-an-alarm-in-windows-10/) zu erstellen, die zu einem späteren Zeitpunkt ausgelöst werden.


**Ghost Popup:** können Sie auch eine Benachrichtigung, der in der unteren rechten Ecke des Bildschirms etwa überspringen und stattdessen direkt auf das Info-Center Senden der Benachrichtigung ausgelöst. Dies wird erreicht, indem Sie die [SupressPopup-Eigenschaft](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastnotification.suppresspopup) auf "true" festlegen. Obwohl es möglicherweise einige Skepsis um anzeigen nicht außerhalb der Info-Center Benachrichtigungen, wir finden Sie in einem 2-3 Mal höher Engagement für Popups, die im Info-Center über live geholt Popup.  Benutzer sind schneller reagieren, wenn diese für den Empfang von Benachrichtigungen bereit und steuern können, wenn sie unterbrochen werden deshalb Inhalte im Info-Center weitaus effektiver noninvasively Benutzer benachrichtigt werden kann.

## <a name="3-clear-out-the-clutter"></a>3. löschen Sie die unübersichtliche
Benachrichtigungen können für längere Zeit (standardmäßig drei Tage) im Info-Center beibehalten.  Es ist unbedingt notwendig, dass Sie stellen Sie sicher, dass auf dem neuesten Stand und relevant ist, Sie jedes Mal, wenn der Benutzer Info-Center öffnet, des Inhalts, der hier befindet. Sie sind verschwendet Bildschirmbereich des Benutzers und belegen Steckplätze, die für etwas mehr auf dem neuesten Stand verwendet werden können.  Nehmen wir an, die Benutzer Ihre e-Mail-Management-app installiert und empfängt zehn-e-Mails und zehn Benachrichtigungen zusammen mit diesen-e-Mails.  Je nach der gewünschten zu machen sollten Sie diese Benachrichtigungen löschen, wenn der Benutzer lesen die entsprechende e-Mail oder die App als eine Möglichkeit zum Entfernen von alten unübersichtliche Info-Center geöffnet hat.

Wir haben eine Reihe von [ToastNotificationHistory](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastnotificationhistory) APIs, mit denen Sie sehen, welche Inhalte im Info-Center ist, als auch diese Benachrichtigungen zu verwalten. Respektieren Bildschirmbereich des Benutzers werden, und achten Sie darauf, dass Sie nur relevante und aktuelle Inhalte für Benutzer angezeigt werden.

## <a name="4-keeping-organized"></a>4. fernhalten organisiert.
Wie bereits erwähnt, der Inhalt im Info-Center drei Tage beibehalten.  Organisieren Sie, können Sie die Benutzern, die Sie die Informationen auswählen, die sie schnell suchen, die Benachrichtigungen im Info-Center mit [Header](https://docs.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/toast-headers) oder [Sammlungen](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastcollection). Sie können ein Beispiel für einen Header, der unten sehen.

![Popup-Beispiele mit Header mit der Bezeichnung "Camping!!"](images/toast-headers-action-center.png)

Gruppieren Sie diese Benachrichtigungen in einer Weise, sodass relevante Inhalte zusammen bleibt (d. h. wie getrennt werden verschiedene Sport Ligen in eine Sport-app oder das Sortieren von Nachrichten nach Gruppenchat). Sammlungen sind eine deutlicher Möglichkeit, Gruppenrichtlinien-Benachrichtigungen, während Header komplexer sind, aber beide auswählen, und wählen Sie Benachrichtigungen schneller ermöglichen.

## <a name="other-resources"></a>Weitere Ressourcen
Diese vier oben genannten Punkte sind Richtlinien, die wir effektive durch unseren eigenen Analyse der Telemetrie und durch die erste und Drittanbieter-Experimente gefunden haben. Denken Sie daran, jedoch, die diese Richtlinien sind: Richtlinien.  Wir sind davon überzeugt diese Regeln hilft Interaktion und Produktivität der Benachrichtigungen, jedoch kann nichts benutzerorientiert denken, und lernen Sie von Ihren eigenen Daten ersetzen.  

Wenn Sie Ihre UWP-app heute Benachrichtigungen senden können Sie Analytics anzeigen, auf die wo sich Ihre Benachrichtigungen im [Partner Center befindet](https://partner.microsoft.com/dashboard)! Diese Daten stammt frei, wenn der [Store-Services-SDK](https://marketplace.visualstudio.com/items?itemName=AdMediator.MicrosoftStoreServicesSDK) oder die [WNS-APIs](https://docs.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)verwenden. Dieser Metriken erhalten Sie weitere Einblicke in Ihre Benachrichtigungen auf der Windows-Plattform passiert auch, wie Benutzer mit Benachrichtigungen interagiert werden. Diese Daten zugreifen, indem Sie auf das Menü auf der linken Seite einbeziehen > Benachrichtigungen, klicken auf der Registerkarte "Analyse" innerhalb der Seite "Notifications".  Dies befindet am gleichen Ort, den Sie zum Senden von Benachrichtigungen aus dem Partner Center wechseln möchten.

## <a name="related-topics"></a>Verwandte Themen

* [Popupinhalt](adaptive-interactive-toasts.md)
* [Unformatierte Benachrichtigungen](raw-notification-overview.md)
* [Ausstehendes Update](toast-pending-update.md)
* [Benachrichtigungsbibliothek auf GitHub (Teil des Windows-Community-Toolkit)](https://github.com/Microsoft/UWPCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.Notifications)
