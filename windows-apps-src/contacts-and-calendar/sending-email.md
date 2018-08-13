---
author: normesta
description: Hier erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten, damit Benutzer eine E-Mail senden können. Sie können die Felder der E-Mail vor dem Anzeigen des Dialogfelds mit Daten füllen. Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.
title: E-Mail senden
ms.assetid: 74511E90-9438-430E-B2DE-24E196A111E5
keywords: Kontakte, E-Mail, Senden
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: bfeec341b0b4e63b4fe37118c1f7daac67929018
ms.sourcegitcommit: 378382419f1fda4e4df76ffa9c8cea753d271e6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
ms.locfileid: "665390"
---
# <a name="send-email"></a><span data-ttu-id="589ab-106">E-Mail senden</span><span class="sxs-lookup"><span data-stu-id="589ab-106">Send email</span></span>

<span data-ttu-id="589ab-107">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="589ab-107">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="589ab-108">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="589ab-108">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="589ab-109">Hier erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten, damit Benutzer eine E-Mail senden können.</span><span class="sxs-lookup"><span data-stu-id="589ab-109">Shows how to launch the compose email dialog to allow the user to send an email message.</span></span> <span data-ttu-id="589ab-110">Sie können die Felder der E-Mail vor dem Anzeigen des Dialogfelds mit Daten füllen.</span><span class="sxs-lookup"><span data-stu-id="589ab-110">You can pre-populate the fields of the email with data before showing the dialog.</span></span> <span data-ttu-id="589ab-111">Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.</span><span class="sxs-lookup"><span data-stu-id="589ab-111">The message will not be sent until the user taps the send button.</span></span>

**<span data-ttu-id="589ab-112">Inhalt dieses Artikels</span><span class="sxs-lookup"><span data-stu-id="589ab-112">In this article</span></span>**

-   [<span data-ttu-id="589ab-113">Starten des Dialogfelds zum Verfassen einer E-Mail</span><span class="sxs-lookup"><span data-stu-id="589ab-113">Launch the compose email dialog</span></span>](#launch-the-compose-email-dialog)
-   [<span data-ttu-id="589ab-114">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="589ab-114">Summary and next steps</span></span>](#summary-and-next-steps)
-   [<span data-ttu-id="589ab-115">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="589ab-115">Related topics</span></span>](#related-topics)

## <a name="launch-the-compose-email-dialog"></a><span data-ttu-id="589ab-116">Starten des Dialogfelds zum Verfassen einer E-Mail</span><span class="sxs-lookup"><span data-stu-id="589ab-116">Launch the compose email dialog</span></span>

<span data-ttu-id="589ab-117">Erstellen Sie ein neues [**EmailMessage**](https://msdn.microsoft.com/library/windows/apps/Dn631270)-Objekt, und legen Sie die Daten fest, die im Dialogfeld zum Verfassen einer E-Mail bereits vorhanden sein sollen.</span><span class="sxs-lookup"><span data-stu-id="589ab-117">Create a new [**EmailMessage**](https://msdn.microsoft.com/library/windows/apps/Dn631270) object and set the data that you want to be pre-populated in the compose email dialog.</span></span> <span data-ttu-id="589ab-118">Rufen Sie [**ShowComposeNewEmailAsync**](https://msdn.microsoft.com/library/windows/apps/Dn631269) auf, um das Dialogfeld anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="589ab-118">Call [**ShowComposeNewEmailAsync**](https://msdn.microsoft.com/library/windows/apps/Dn631269) to show the dialog.</span></span>

``` cs
private async Task ComposeEmail(Windows.ApplicationModel.Contacts.Contact recipient,
    string messageBody,
    StorageFile attachmentFile)
{
    var emailMessage = new Windows.ApplicationModel.Email.EmailMessage();
    emailMessage.Body = messageBody;

    if (attachmentFile != null)
    {
        var stream = Windows.Storage.Streams.RandomAccessStreamReference.CreateFromFile(attachmentFile);

        var attachment = new Windows.ApplicationModel.Email.EmailAttachment(
            attachmentFile.Name,
            stream);

        emailMessage.Attachments.Add(attachment);
    }

    var email = recipient.Emails.FirstOrDefault<Windows.ApplicationModel.Contacts.ContactEmail>();
    if (email != null)
    {
        var emailRecipient = new Windows.ApplicationModel.Email.EmailRecipient(email.Address);
        emailMessage.To.Add(emailRecipient);
    }

    await Windows.ApplicationModel.Email.EmailManager.ShowComposeNewEmailAsync(emailMessage);

}
```

## <a name="summary-and-next-steps"></a><span data-ttu-id="589ab-119">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="589ab-119">Summary and next steps</span></span>

<span data-ttu-id="589ab-120">In diesem Thema haben Sie erfahren, wie Sie das Dialogfeld zum Verfassen einer E-Mail starten.</span><span class="sxs-lookup"><span data-stu-id="589ab-120">This topic has shown you how to launch the compose email dialog.</span></span> <span data-ttu-id="589ab-121">Informationen zum Auswählen von Kontakten als E-Mail-Empfänger finden Sie unter [Auswählen von Kontakten](selecting-contacts.md).</span><span class="sxs-lookup"><span data-stu-id="589ab-121">For information on selecting contacts to use as recipients for an email message, see [Select contacts](selecting-contacts.md).</span></span> <span data-ttu-id="589ab-122">Informationen zum Auswählen einer Datei als E-Mail-Anlage finden Sie unter [**PickSingleFileAsync**](https://msdn.microsoft.com/library/windows/apps/JJ635275).</span><span class="sxs-lookup"><span data-stu-id="589ab-122">See [**PickSingleFileAsync**](https://msdn.microsoft.com/library/windows/apps/JJ635275) to select a file to use as an email attachment.</span></span>

## <a name="related-topics"></a><span data-ttu-id="589ab-123">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="589ab-123">Related topics</span></span>

* [<span data-ttu-id="589ab-124">Auswählen von Kontakten</span><span class="sxs-lookup"><span data-stu-id="589ab-124">Selecting contacts</span></span>](selecting-contacts.md)
* [<span data-ttu-id="589ab-125">Fortsetzen von Windows Phone-Apps nach dem Aufrufen einer Dateiauswahl</span><span class="sxs-lookup"><span data-stu-id="589ab-125">How to continue your Windows Phone app after calling a file picker</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/Dn614994)
 

 
