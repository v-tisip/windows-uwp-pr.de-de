---
description: In diesem Thema erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer SMS starten, damit Benutzer eine SMS senden können. Sie können die Felder der SMS vor dem Anzeigen des Dialogfelds mit Daten füllen. Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.
title: Senden einer SMS
ms.assetid: 4D7B509B-1CF0-4852-9691-E96D8352A4D6
keywords: Kontakte, SMS, Senden
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 427eb1b895269727d82e42d5abc3ae1f1da1a35d
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7706086"
---
# <a name="send-an-sms-message"></a><span data-ttu-id="dc9ce-106">Senden einer SMS</span><span class="sxs-lookup"><span data-stu-id="dc9ce-106">Send an SMS message</span></span>

<span data-ttu-id="dc9ce-107">In diesem Thema erfahren Sie, wie Sie das Dialogfeld zum Verfassen einer SMS starten, damit Benutzer eine SMS senden können.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-107">This topic shows you how to launch the compose SMS dialog to allow the user to send an SMS message.</span></span> <span data-ttu-id="dc9ce-108">Sie können die Felder der SMS vor dem Anzeigen des Dialogfelds mit Daten füllen.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-108">You can pre-populate the fields of the SMS with data before showing the dialog.</span></span> <span data-ttu-id="dc9ce-109">Die Nachricht wird erst gesendet, wenn Benutzer auf die Schaltfläche „Senden“ tippen.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-109">The message will not be sent until the user taps the send button.</span></span>

<span data-ttu-id="dc9ce-110">Um diesen Code jeweils aufzurufen, deklarieren Sie die **Chat**, **SmsSend**und **ChatSystem** Funktionen im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-110">To call this code, declare the **chat**, **smsSend**, and **chatSystem** capabilities in your package manifest.</span></span> <span data-ttu-id="dc9ce-111">Hierbei handelt es sich um [eingeschränkte Funktionen](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations#special-and-restricted-capabilities) , aber Sie können diese in Ihrer app verwenden.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-111">These are [restricted capabilities](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations#special-and-restricted-capabilities) but you can use them in your app.</span></span> <span data-ttu-id="dc9ce-112">Sie benötigen die konzeptgenehmigung nur dann, wenn Sie Ihre app im Store veröffentlichen möchten.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-112">You need approval only if you intend to publish your app to the Store.</span></span> <span data-ttu-id="dc9ce-113">Finden Sie unter [Kontotypen, Standorte und Gebühren](https://docs.microsoft.com/windows/uwp/publish/account-types-locations-and-fees).</span><span class="sxs-lookup"><span data-stu-id="dc9ce-113">See [Account types, locations, and fees](https://docs.microsoft.com/windows/uwp/publish/account-types-locations-and-fees).</span></span>

## <a name="launch-the-compose-sms-dialog"></a><span data-ttu-id="dc9ce-114">Starten des Dialogfelds zum Verfassen einer SMS</span><span class="sxs-lookup"><span data-stu-id="dc9ce-114">Launch the compose SMS dialog</span></span>

<span data-ttu-id="dc9ce-115">Erstellen Sie ein neues [**ChatMessage**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.chatmessage)-Objekt, und legen Sie die Daten fest, die im Dialogfeld zum Verfassen einer E-Mail bereits vorhanden sein sollen.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-115">Create a new [**ChatMessage**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.chatmessage) object and set the data that you want to be pre-populated in the compose email dialog.</span></span> <span data-ttu-id="dc9ce-116">Rufen Sie [**ShowComposeSmsMessageAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.chatmessagemanager.showcomposesmsmessageasync) auf, um das Dialogfeld anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-116">Call [**ShowComposeSmsMessageAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.chatmessagemanager.showcomposesmsmessageasync) to show the dialog.</span></span>

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

<span data-ttu-id="dc9ce-117">Den folgenden Code können Sie ermitteln, ob das Gerät, das Ihre app ausgeführt wird zum Senden von SMS-Nachrichten werden kann.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-117">You can use the following code to determine whether the device that is running your app is able to send SMS messages.</span></span>

```csharp
if (Windows.Foundation.Metadata.ApiInformation.IsTypePresent("Windows.ApplicationModel.Chat"))
{
   // Call code here.
}
```

## <a name="summary-and-next-steps"></a><span data-ttu-id="dc9ce-118">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="dc9ce-118">Summary and next steps</span></span>

<span data-ttu-id="dc9ce-119">In diesem Thema haben Sie erfahren, wie Sie das Dialogfeld zum Verfassen einer SMS starten.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-119">This topic has shown you how to launch the compose SMS dialog.</span></span> <span data-ttu-id="dc9ce-120">Informationen zum Auswählen von Kontakten als SMS-Empfänger finden Sie unter [Auswählen von Kontakten](selecting-contacts.md).</span><span class="sxs-lookup"><span data-stu-id="dc9ce-120">For information on selecting contacts to use as recipients for an SMS message, see [Select contacts](selecting-contacts.md).</span></span> <span data-ttu-id="dc9ce-121">Laden Sie die [Beispiele für universelle Windows-Apps](http://go.microsoft.com/fwlink/p/?linkid=619979) von GitHub herunter, um sich weitere Beispiele zum Senden und Empfangen von SMS-Nachrichten unter Verwendung einer Hintergrundaufgabe anzusehen.</span><span class="sxs-lookup"><span data-stu-id="dc9ce-121">Download the [Universal Windows app samples](http://go.microsoft.com/fwlink/p/?linkid=619979) from GitHub to see more examples of how to send and receive SMS messages by using a background task.</span></span>

## <a name="related-topics"></a><span data-ttu-id="dc9ce-122">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="dc9ce-122">Related topics</span></span>

* [<span data-ttu-id="dc9ce-123">Auswählen von Kontakten</span><span class="sxs-lookup"><span data-stu-id="dc9ce-123">Select contacts</span></span>](selecting-contacts.md)
