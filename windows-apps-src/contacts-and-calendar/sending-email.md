---
description: Hier erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten, damit Benutzer eine E-Mail senden können. Sie können die Felder der E-Mail vor dem Anzeigen des Dialogfelds mit Daten füllen. Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.
title: E-Mail senden
ms.assetid: 74511E90-9438-430E-B2DE-24E196A111E5
keywords: Kontakte, E-Mail, Senden
ms.date: 10/11/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 1593ab8b547a464492a35aa7d49d38f667a8210b
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8487162"
---
# <a name="send-email"></a><span data-ttu-id="3d738-106">Senden von E-Mails</span><span class="sxs-lookup"><span data-stu-id="3d738-106">Send email</span></span>

<span data-ttu-id="3d738-107">Hier erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten, damit Benutzer eine E-Mail senden können.</span><span class="sxs-lookup"><span data-stu-id="3d738-107">Shows how to launch the compose email dialog to allow the user to send an email message.</span></span> <span data-ttu-id="3d738-108">Sie können die Felder der E-Mail vor dem Anzeigen des Dialogfelds mit Daten füllen.</span><span class="sxs-lookup"><span data-stu-id="3d738-108">You can pre-populate the fields of the email with data before showing the dialog.</span></span> <span data-ttu-id="3d738-109">Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.</span><span class="sxs-lookup"><span data-stu-id="3d738-109">The message will not be sent until the user taps the send button.</span></span>

**<span data-ttu-id="3d738-110">Inhalt dieses Artikels</span><span class="sxs-lookup"><span data-stu-id="3d738-110">In this article</span></span>**

-   [<span data-ttu-id="3d738-111">Starten des Dialogfelds zum Verfassen einer E-Mail</span><span class="sxs-lookup"><span data-stu-id="3d738-111">Launch the compose email dialog</span></span>](#launch-the-compose-email-dialog)
-   [<span data-ttu-id="3d738-112">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3d738-112">Summary and next steps</span></span>](#summary-and-next-steps)
-   [<span data-ttu-id="3d738-113">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3d738-113">Related topics</span></span>](#related-topics)

## <a name="launch-the-compose-email-dialog"></a><span data-ttu-id="3d738-114">Starten des Dialogfelds zum Verfassen einer E-Mail</span><span class="sxs-lookup"><span data-stu-id="3d738-114">Launch the compose email dialog</span></span>

<span data-ttu-id="3d738-115">Erstellen Sie ein neues [**EmailMessage**](https://msdn.microsoft.com/library/windows/apps/Dn631270)-Objekt, und legen Sie die Daten fest, die im Dialogfeld zum Verfassen einer E-Mail bereits vorhanden sein sollen.</span><span class="sxs-lookup"><span data-stu-id="3d738-115">Create a new [**EmailMessage**](https://msdn.microsoft.com/library/windows/apps/Dn631270) object and set the data that you want to be pre-populated in the compose email dialog.</span></span> <span data-ttu-id="3d738-116">Rufen Sie [**ShowComposeNewEmailAsync**](https://msdn.microsoft.com/library/windows/apps/Dn631269) auf, um das Dialogfeld anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3d738-116">Call [**ShowComposeNewEmailAsync**](https://msdn.microsoft.com/library/windows/apps/Dn631269) to show the dialog.</span></span>

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
> <span data-ttu-id="3d738-117">Anlagen, die Sie eine e-Mail mit der Klasse [EmailAttachment](https://docs.microsoft.com/uwp/api/windows.applicationmodel.email.emailattachment) hinzufügen werden nur in der Mail-app angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3d738-117">Attachments that you add to an email by using the [EmailAttachment](https://docs.microsoft.com/uwp/api/windows.applicationmodel.email.emailattachment) class will appear only in the Mail app.</span></span> <span data-ttu-id="3d738-118">Wenn Benutzer andere e-Mail-Anwendung, als das standardmäßige e-Mail-Programm konfiguriert haben, wird das Fenster zum Verfassen einer ohne den Anhang angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3d738-118">If users have any other mail program configured as their default mail program, the compose window will appear without the attachment.</span></span> <span data-ttu-id="3d738-119">Dies ist ein bekanntes Problem.</span><span class="sxs-lookup"><span data-stu-id="3d738-119">This is a known issue.</span></span>

## <a name="summary-and-next-steps"></a><span data-ttu-id="3d738-120">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3d738-120">Summary and next steps</span></span>

<span data-ttu-id="3d738-121">In diesem Thema haben Sie erfahren, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten.</span><span class="sxs-lookup"><span data-stu-id="3d738-121">This topic has shown you how to launch the compose email dialog.</span></span> <span data-ttu-id="3d738-122">Informationen zum Auswählen von Kontakten als E-Mail-Empfänger finden Sie unter [Auswählen von Kontakten](selecting-contacts.md).</span><span class="sxs-lookup"><span data-stu-id="3d738-122">For information on selecting contacts to use as recipients for an email message, see [Select contacts](selecting-contacts.md).</span></span> <span data-ttu-id="3d738-123">Informationen zum Auswählen einer Datei als E-Mail-Anlage finden Sie unter [**PickSingleFileAsync**](https://msdn.microsoft.com/library/windows/apps/JJ635275).</span><span class="sxs-lookup"><span data-stu-id="3d738-123">See [**PickSingleFileAsync**](https://msdn.microsoft.com/library/windows/apps/JJ635275) to select a file to use as an email attachment.</span></span>

## <a name="related-topics"></a><span data-ttu-id="3d738-124">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3d738-124">Related topics</span></span>

* [<span data-ttu-id="3d738-125">Auswählen von Kontakten</span><span class="sxs-lookup"><span data-stu-id="3d738-125">Selecting contacts</span></span>](selecting-contacts.md)
* [<span data-ttu-id="3d738-126">Fortsetzen von Windows Phone-Apps nach dem Aufrufen einer Dateiauswahl</span><span class="sxs-lookup"><span data-stu-id="3d738-126">How to continue your Windows Phone app after calling a file picker</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/Dn614994)
 

 
