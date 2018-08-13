---
author: normesta
description: In diesem Thema erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer SMS starten, damit Benutzer eine SMS senden können. Sie können die Felder der SMS vor dem Anzeigen des Dialogfelds mit Daten füllen. Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.
title: Senden einer SMS
ms.assetid: 4D7B509B-1CF0-4852-9691-E96D8352A4D6
keywords: Kontakte, SMS, Senden
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: e5c3678e6c12a65b6821d2fc2a54e0710f7dcef3
ms.sourcegitcommit: 378382419f1fda4e4df76ffa9c8cea753d271e6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
ms.locfileid: "665360"
---
# <a name="send-an-sms-message"></a><span data-ttu-id="3954c-106">Senden einer SMS</span><span class="sxs-lookup"><span data-stu-id="3954c-106">Send an SMS message</span></span>

<span data-ttu-id="3954c-107">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="3954c-107">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="3954c-108">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="3954c-108">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="3954c-109">In diesem Thema erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer SMS starten, damit Benutzer eine SMS senden können.</span><span class="sxs-lookup"><span data-stu-id="3954c-109">This topic shows you how to launch the compose SMS dialog to allow the user to send an SMS message.</span></span> <span data-ttu-id="3954c-110">Sie können die Felder der SMS vor dem Anzeigen des Dialogfelds mit Daten füllen.</span><span class="sxs-lookup"><span data-stu-id="3954c-110">You can pre-populate the fields of the SMS with data before showing the dialog.</span></span> <span data-ttu-id="3954c-111">Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.</span><span class="sxs-lookup"><span data-stu-id="3954c-111">The message will not be sent until the user taps the send button.</span></span>

## <a name="launch-the-compose-sms-dialog"></a><span data-ttu-id="3954c-112">Starten des Dialogfelds zum Verfassen einer SMS</span><span class="sxs-lookup"><span data-stu-id="3954c-112">Launch the compose SMS dialog</span></span>

<span data-ttu-id="3954c-113">Erstellen Sie ein neues [**ChatMessage**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.chatmessage)-Objekt, und legen Sie die Daten fest, die im Dialogfeld zum Verfassen einer E-Mail bereits vorhanden sein sollen.</span><span class="sxs-lookup"><span data-stu-id="3954c-113">Create a new [**ChatMessage**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.chatmessage) object and set the data that you want to be pre-populated in the compose email dialog.</span></span> <span data-ttu-id="3954c-114">Rufen Sie [**ShowComposeSmsMessageAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.chatmessagemanager.showcomposesmsmessageasync) auf, um das Dialogfeld anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3954c-114">Call [**ShowComposeSmsMessageAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.chatmessagemanager.showcomposesmsmessageasync) to show the dialog.</span></span>

```cs
private async void ComposeSms(Windows.ApplicationModel.Contacts.Contact recipient,
    string messageBody,
    StorageFile attachmentFile,
    string mimeType)
{
    var chatMessage = new Windows.ApplicationModel.Chat.ChatMessage();
    chatMessage.Body = messageBody;

    if (attachmentFile != null)
    {
        var stream = Windows.Storage.Streams.RandomAccessStreamReference.CreateFromFile(attachmentFile);

        var attachment = new Windows.ApplicationModel.Chat.ChatMessageAttachment(
            mimeType,
            stream);

        chatMessage.Attachments.Add(attachment);
    }

    var phone = recipient.Phones.FirstOrDefault<Windows.ApplicationModel.Contacts.ContactPhone>();
    if (phone != null)
    {
        chatMessage.Recipients.Add(phone.Number);
    }
    await Windows.ApplicationModel.Chat.ChatMessageManager.ShowComposeSmsMessageAsync(chatMessage);
}
```

## <a name="summary-and-next-steps"></a><span data-ttu-id="3954c-115">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3954c-115">Summary and next steps</span></span>

<span data-ttu-id="3954c-116">In diesem Thema haben Sie erfahren, wie Sie das Dialogfeld zum Verfassen einer SMS starten.</span><span class="sxs-lookup"><span data-stu-id="3954c-116">This topic has shown you how to launch the compose SMS dialog.</span></span> <span data-ttu-id="3954c-117">Informationen zum Auswählen von Kontakten als SMS-Empfänger finden Sie unter [Auswählen von Kontakten](selecting-contacts.md).</span><span class="sxs-lookup"><span data-stu-id="3954c-117">For information on selecting contacts to use as recipients for an SMS message, see [Select contacts](selecting-contacts.md).</span></span> <span data-ttu-id="3954c-118">Laden Sie die [Beispiele für universelle Windows-Apps](http://go.microsoft.com/fwlink/p/?linkid=619979) von GitHub herunter, um sich weitere Beispiele zum Senden und Empfangen von SMS-Nachrichten unter Verwendung einer Hintergrundaufgabe anzusehen.</span><span class="sxs-lookup"><span data-stu-id="3954c-118">Download the [Universal Windows app samples](http://go.microsoft.com/fwlink/p/?linkid=619979) from GitHub to see more examples of how to send and receive SMS messages by using a background task.</span></span>

## <a name="related-topics"></a><span data-ttu-id="3954c-119">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3954c-119">Related topics</span></span>

* [<span data-ttu-id="3954c-120">Auswählen von Kontakten</span><span class="sxs-lookup"><span data-stu-id="3954c-120">Select contacts</span></span>](selecting-contacts.md)
