---
author: normesta
description: Erfahren Sie, wie Kontakte und Kalenderinformationen in Ihrer UWP-App verwendet werden.
title: Kontakte und Kalender
ms.assetid: b7e53ab5-2828-4fb7-8656-2bec70b3467f
ms.author: normesta
ms.date: 05/18/2018
ms.topic: article
keywords: Windows 10, UWP, Kontakte, Kalender, Termine, E-Mail-Nachrichten
ms.localizationpriority: medium
ms.openlocfilehash: c020a871863df6fac3dabc3ffab4bafc57227b50
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7301100"
---
# <a name="contacts-my-people-and-calendar"></a>Kontakte, Meine Kontakte und Kalender


Sie können Benutzern den Zugriff auf ihre Kontakte und Termine ermöglichen, sodass sie Inhalte, E-Mails, Kalenderinformationen oder Nachrichten mit anderen Benutzern oder beliebiger, von Ihnen entwickelter Funktionalität teilen können.

Die folgenden Themen enthalten Informationen zu verschiedenen Verfahren, wie Ihre App auf Kontakte und Termine zugreifen kann:

| Thema | Beschreibung |
|-------|-------------|
| [Auswählen von Kontakten](selecting-contacts.md) | Mit dem [<strong>Windows.ApplicationModel.Contacts</strong>](https://msdn.microsoft.com/library/windows/apps/BR225002)-Namespace verfügen Sie über mehrere Optionen zum Auswählen von Kontakten. Wir zeigen Ihnen hier, wie Sie einen einzelnen Kontakt oder mehrere Kontakte auswählen und wie Sie die Kontaktauswahl so konfigurieren, dass nur die von der App benötigten Kontaktinformationen abgerufen werden. |
| [Senden von E-Mails](sending-email.md) | Hier erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten, damit Benutzer eine E-Mail senden können. Sie können die Felder der E-Mail vor dem Anzeigen des Dialogfelds mit Daten füllen. Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen. |
| [Senden einer SMS](sending-an-sms-message.md) | In diesem Thema erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer SMS starten, damit Benutzer eine SMS senden können. Sie können die Felder der SMS vor dem Anzeigen des Dialogfelds mit Daten füllen. Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen. |
| [Verwalten von Terminen](managing-appointments.md) | Mit dem [<strong>Windows.ApplicationModel.Appointments</strong>](https://msdn.microsoft.com/library/windows/apps/Dn263359)-Namespace können Sie in der Kalender-App eines Benutzers Termine erstellen und verwalten. Hier erfahren Sie, wie Sie einen Termin erstellen, einer Kalender-App hinzufügen, in der Kalender-App ersetzen und aus der Kalender-App entfernen. Außerdem wird erläutert, wie Sie eine Zeitspanne für eine Kalender-App anzeigen und ein Terminwiederholungsobjekt erstellen. |
| [Verbinden der App mit Aktionen auf einer Visitenkarte](integrating-with-contacts.md) | Zeigt, wie Ihre App neben Aktionen auf einer Visitenkarte oder einer kleinen Visitenkarte angezeigt werden kann. Benutzer können Ihre App auswählen, um eine Aktion auszuführen, z. B. eine Profilseite zu öffnen, einen Anruf zu tätigen oder eine Nachricht zu senden. |
| [Support für Meine Kontakte zu einer Anwendung hinzufügen](my-people-support.md) | Zeigt, wie Sie einer Anwendung Support für „Meine Kontakte” hinzufügen, und wie Sie Kontakte auf der Taskleiste anheften und trennen. |
| [„Meine Kontakte” freigeben](my-people-sharing.md) | Zeigt, wie Sie Unterstützung für die Freigabe von „Meine Kontakte” hinzufügen, sodass Benutzer Inhalte für ihre angehefteten Kontakte freigeben können, indem sie Dateien aus dem Datei-Explorer auf die Startseite von „Meine Kontakte” anheften. |
| [Meine Kontakte – Benachrichtigungen](my-people-notifications.md) | Zeigt, wie Sie Benachrichtigungen für Meine Kontakte erstellen und verwenden. Dies ist eine neue Art von Popupbenachrichtigungen, die von einem angehefteten Kontakt gesendet werden. |

 

## <a name="related-topics"></a>Verwandte Themen

* [Beispiel zur Termin-API](http://go.microsoft.com/fwlink/p/?linkid=309836)
* [Beispiel zur Kontakt-Manager-API](http://go.microsoft.com/fwlink/p/?LinkID=310079)
* [Beispiel-App für die Kontaktauswahl](http://go.microsoft.com/fwlink/p/?linkid=231575)
* [Beispiel zum Behandeln von Kontaktaktionen](http://go.microsoft.com/fwlink/p/?LinkID=320151)
* [Beispiel für die Visitenkartenintegration](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ContactCardIntegration)
