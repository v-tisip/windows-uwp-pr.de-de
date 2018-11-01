---
author: normesta
description: Hier erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten, damit Benutzer eine E-Mail senden können. Sie können die Felder der E-Mail vor dem Anzeigen des Dialogfelds mit Daten füllen. Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.
title: E-Mail senden
ms.assetid: 74511E90-9438-430E-B2DE-24E196A111E5
keywords: Kontakte, E-Mail, Senden
ms.author: normesta
ms.date: 10/11/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 0a28809210f71bf523e3cc5f9c8da1db9fbcc90c
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5883917"
---
# <a name="send-email"></a>Senden von E-Mails

Hier erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten, damit Benutzer eine E-Mail senden können. Sie können die Felder der E-Mail vor dem Anzeigen des Dialogfelds mit Daten füllen. Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.

**Inhalt dieses Artikels**

-   [Starten des Dialogfelds zum Verfassen einer E-Mail](#launch-the-compose-email-dialog)
-   [Zusammenfassung und nächste Schritte](#summary-and-next-steps)
-   [Verwandte Themen](#related-topics)

## <a name="launch-the-compose-email-dialog"></a>Starten des Dialogfelds zum Verfassen einer E-Mail

Erstellen Sie ein neues [**EmailMessage**](https://msdn.microsoft.com/library/windows/apps/Dn631270)-Objekt, und legen Sie die Daten fest, die im Dialogfeld zum Verfassen einer E-Mail bereits vorhanden sein sollen. Rufen Sie [**ShowComposeNewEmailAsync**](https://msdn.microsoft.com/library/windows/apps/Dn631269) auf, um das Dialogfeld anzuzeigen.

``` cs
private async Task ComposeEmail(Windows.ApplicationModel.Contacts.Contact recipient,
    string subject, string messageBody)
{
    var emailMessage = new Windows.ApplicationModel.Email.EmailMessage();
    emailMessage.Body = messageBody;

    var email = recipient.Emails.FirstOrDefault<Windows.ApplicationModel.Contacts.ContactEmail>();
    if (email != null)
    {
        var emailRecipient = new Windows.ApplicationModel.Email.EmailRecipient(email.Address);
        emailMessage.To.Add(emailRecipient);
        emailMessage.Subject = subject;
    }

    await Windows.ApplicationModel.Email.EmailManager.ShowComposeNewEmailAsync(emailMessage);
}
```

>[!NOTE]
> Anlagen, die Sie eine e-Mail mit der Klasse [EmailAttachment](https://docs.microsoft.com/uwp/api/windows.applicationmodel.email.emailattachment) hinzufügen werden nur in der Mail-app angezeigt. Wenn Benutzer alle anderen e-Mail-Programm als das standardmäßige e-Mail-Programm konfiguriert haben, wird das Fenster zum Verfassen einer ohne den Anhang angezeigt. Dies ist ein bekanntes Problem.

## <a name="summary-and-next-steps"></a>Zusammenfassung und nächste Schritte

In diesem Thema haben Sie erfahren, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten. Informationen zum Auswählen von Kontakten als E-Mail-Empfänger finden Sie unter [Auswählen von Kontakten](selecting-contacts.md). Informationen zum Auswählen einer Datei als E-Mail-Anlage finden Sie unter [**PickSingleFileAsync**](https://msdn.microsoft.com/library/windows/apps/JJ635275).

## <a name="related-topics"></a>Verwandte Themen

* [Auswählen von Kontakten](selecting-contacts.md)
* [Fortsetzen von Windows Phone-Apps nach dem Aufrufen einer Dateiauswahl](https://msdn.microsoft.com/library/windows/apps/xaml/Dn614994)
 

 
