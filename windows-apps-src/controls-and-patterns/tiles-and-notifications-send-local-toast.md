---
author: mijacobs
Description: Hier erfahren Sie, wie Sie eine lokale Popupbenachrichtigung senden und mit dem Benutzer umgehen, der auf das Popup klickt.
title: Senden einer lokalen Popupbenachrichtigung
ms.assetid: E9AB7156-A29E-4ED7-B286-DA4A6E683638
label: Send a local toast notification
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 7f21c6a72c00ae2677adb0c1196030997ed48491
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="send-a-local-toast-notification"></a><span data-ttu-id="e8290-104">Senden einer lokalen Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="e8290-104">Send a local toast notification</span></span>

<span data-ttu-id="e8290-105">Eine Popupbenachrichtigung ist eine Nachricht, die eine App erstellen und an den Benutzer übermitteln kann, während dieser Ihre App aktuell nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="e8290-105">A toast notification is a message that an app can construct and deliver to the user while he/she is not currently inside your app.</span></span> <span data-ttu-id="e8290-106">Diese Schnellstartanleitung führt Sie durch die Schritteder Erstellung, Übermittlung und Anzeige einer Windows10-Popupbenachrichtigung mit den neuen adaptiven Vorlagen und interaktiven Aktionen.</span><span class="sxs-lookup"><span data-stu-id="e8290-106">This Quickstart walks you through the steps to create, deliver, and display a Windows 10 toast notification with the new adaptive templates and interactive actions.</span></span> <span data-ttu-id="e8290-107">Diese Aktionen werden mit einer lokalen Benachrichtigung demonstriert– der einfachsten Benachrichtigung, die Sie implementieren können.</span><span class="sxs-lookup"><span data-stu-id="e8290-107">These actions are demonstrated through a local notification, which is the simplest notification to implement.</span></span> <span data-ttu-id="e8290-108">Wir werden die folgenden Schrittedurchlaufen:</span><span class="sxs-lookup"><span data-stu-id="e8290-108">We will go through the following things:</span></span>

### <a name="sending-a-toast"></a><span data-ttu-id="e8290-109">Senden eines Popups</span><span class="sxs-lookup"><span data-stu-id="e8290-109">Sending a toast</span></span>

* <span data-ttu-id="e8290-110">Erstellen des visuellen Teils (Text und Bilder) der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="e8290-110">Constructing the visual part (text and image) of the notification</span></span>
* <span data-ttu-id="e8290-111">Hinzufügen von Aktionen zur Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="e8290-111">Adding actions to the notification</span></span>
* <span data-ttu-id="e8290-112">Festlegen einer Ablaufzeit für das Popup</span><span class="sxs-lookup"><span data-stu-id="e8290-112">Setting an expiration time on the toast</span></span>
* <span data-ttu-id="e8290-113">Festlegen von Tag/Group, sodass Sie das Popup zu einem späteren Zeitpunkt ersetzen/entfernen können</span><span class="sxs-lookup"><span data-stu-id="e8290-113">Setting tag/group so you can replace/remove the toast at a later time</span></span>
* <span data-ttu-id="e8290-114">Senden Ihres Popups mithilfe der lokalen APIs</span><span class="sxs-lookup"><span data-stu-id="e8290-114">Sending your toast using the local APIs</span></span>

### <a name="handling-activation"></a><span data-ttu-id="e8290-115">Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="e8290-115">Handling activation</span></span>

* <span data-ttu-id="e8290-116">Behandeln der Aktivierung beim Klicken auf den Text oder Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="e8290-116">Handling activation when the body or buttons are clicked</span></span>
* <span data-ttu-id="e8290-117">Behandeln der Vordergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="e8290-117">Handling foreground activation</span></span>
* <span data-ttu-id="e8290-118">Behandeln der Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="e8290-118">Handling background activation</span></span>


## <a name="prerequisites"></a><span data-ttu-id="e8290-119">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e8290-119">Prerequisites</span></span>

<span data-ttu-id="e8290-120">Um dieses Thema vollständig zu verstehen, ist Folgendes hilfreich...</span><span class="sxs-lookup"><span data-stu-id="e8290-120">To fully understand this topic, the following will be helpful...</span></span>

* <span data-ttu-id="e8290-121">Ein grundlegendes Verständnis der Begriffe und Konzepte rund um Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="e8290-121">A working knowledge of toast notification terms and concepts.</span></span> <span data-ttu-id="e8290-122">Weitere Informationen finden Sie unter [Popup und Info-Center (Übersicht)](https://blogs.msdn.microsoft.com/tiles_and_toasts/2015/07/08/toast-notification-and-action-center-overview-for-windows-10/).</span><span class="sxs-lookup"><span data-stu-id="e8290-122">For more information, see [Toast and action center overview](https://blogs.msdn.microsoft.com/tiles_and_toasts/2015/07/08/toast-notification-and-action-center-overview-for-windows-10/).</span></span>
* <span data-ttu-id="e8290-123">Kenntnisse in Bezug auf den Inhalt von Windows10-Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="e8290-123">A familiarity with Windows 10 toast notification content.</span></span> <span data-ttu-id="e8290-124">Weitere Informationen finden Sie in der [Dokumentation zu Popup-Inhalt](tiles-and-notifications-adaptive-interactive-toasts.md).</span><span class="sxs-lookup"><span data-stu-id="e8290-124">For more information, see [toast content documentation](tiles-and-notifications-adaptive-interactive-toasts.md).</span></span>
* <span data-ttu-id="e8290-125">Ein Windows10-UWP-App-Projekt</span><span class="sxs-lookup"><span data-stu-id="e8290-125">A Windows 10 UWP app project</span></span>

<span data-ttu-id="e8290-126">**Hinweis:**: Im Gegensatz zu Windows8/8.1 müssen Sie in Ihrem App-Manifest nicht mehr deklarieren, dass Ihre App Popupbenachrichtigungen anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="e8290-126">**Note**: Unlike Windows 8/8.1, you no longer need to declare in your app’s manifest that your app is capable of showing toast notifications.</span></span> <span data-ttu-id="e8290-127">Alle Apps können Popupbenachrichtigungen senden und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e8290-127">All apps are capable of sending and displaying toast notifications.</span></span>

<span data-ttu-id="e8290-128">**Windows8/8.1-Apps**: Verwenden Sie stattdessen die [archivierte Dokumentation](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh868254.aspx).</span><span class="sxs-lookup"><span data-stu-id="e8290-128">**Windows 8/8.1 apps**: Please instead use the [archived documentation](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh868254.aspx).</span></span>


## <a name="install-nuget-packages"></a><span data-ttu-id="e8290-129">Installieren von NuGet-Paketen</span><span class="sxs-lookup"><span data-stu-id="e8290-129">Install NuGet packages</span></span>

<span data-ttu-id="e8290-130">Wir empfehlen die Installation der beiden folgenden NuGet-Pakete für Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="e8290-130">We recommend installing the two following NuGet packages to your project.</span></span> <span data-ttu-id="e8290-131">In unserem Codebeispiel werden diese Pakete verwendet.</span><span class="sxs-lookup"><span data-stu-id="e8290-131">Our code sample will use these packages.</span></span> <span data-ttu-id="e8290-132">Am Ende des Artikels finden Sie die „Vanilla“-Codeausschnitte, die keine NuGet-Pakete verwenden.</span><span class="sxs-lookup"><span data-stu-id="e8290-132">At the end of the article we’ll provide the “Vanilla” code snippets that don’t use any NuGet packages.</span></span>

* <span data-ttu-id="e8290-133">[Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/): Generieren von Popup-Nutzlasten über Objekte anstelle von unformatiertem XML.</span><span class="sxs-lookup"><span data-stu-id="e8290-133">[Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/): Generate toast payloads via objects instead of raw XML.</span></span>
* <span data-ttu-id="e8290-134">[QueryString.NET](https://www.nuget.org/packages/QueryString.NET/): Generieren und Analysieren von Abfragezeichenfolgen mit C#</span><span class="sxs-lookup"><span data-stu-id="e8290-134">[QueryString.NET](https://www.nuget.org/packages/QueryString.NET/): Generate and parse query strings with C#</span></span>


## <a name="add-namespace-declarations"></a><span data-ttu-id="e8290-135">Hinzufügen von Namespacedeklarationen</span><span class="sxs-lookup"><span data-stu-id="e8290-135">Add namespace declarations</span></span>

<span data-ttu-id="e8290-136">Windows.UI.Notifications umfasst die Popup-APIs.</span><span class="sxs-lookup"><span data-stu-id="e8290-136">Windows.UI.Notifications includes the toast APIs.</span></span>

```csharp
using Windows.UI.Notifications;
using Microsoft.Toolkit.Uwp.Notifications; // Notifications library
using Microsoft.QueryStringDotNET; // QueryString.NET
```


## <a name="send-a-toast"></a><span data-ttu-id="e8290-137">Senden eines Popups</span><span class="sxs-lookup"><span data-stu-id="e8290-137">Send a toast</span></span>

<span data-ttu-id="e8290-138">In Windows10 wird der Inhalt der Popupbenachrichtigung mithilfe einer adaptiven Sprache beschrieben, die eine sehr flexible Darstellung Ihrer Benachrichtigung erlaubt.</span><span class="sxs-lookup"><span data-stu-id="e8290-138">In Windows 10, your toast notification content is described using an adaptive language that allows great flexibility with how your notification looks.</span></span> <span data-ttu-id="e8290-139">Weitere Informationen finden Sie in der [Dokumentation zu Popupinhalt](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/07/02/adaptive-and-interactive-toast-notifications-for-windows-10.aspx).</span><span class="sxs-lookup"><span data-stu-id="e8290-139">See the [toast content documentation](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/07/02/adaptive-and-interactive-toast-notifications-for-windows-10.aspx) for more information.</span></span>

### <a name="constructing-the-visual-part-of-the-content"></a><span data-ttu-id="e8290-140">Erstellen des visuellen Teils des Inhalts</span><span class="sxs-lookup"><span data-stu-id="e8290-140">Constructing the visual part of the content</span></span>

<span data-ttu-id="e8290-141">Beginnen wir mit der Erstellung des visuellen Teils des Inhalts, der den Text- und Bildinhalt umfasst, der dem Benutzer angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e8290-141">Let’s start by constructing the visual part of the content, which includes the text and image content you want the user to see.</span></span>

<span data-ttu-id="e8290-142">Dank der Benachrichtigungsbibliothek ist das Generierung des XML-Inhalts einfach.</span><span class="sxs-lookup"><span data-stu-id="e8290-142">Thanks to the the Notifications library, generating the XML content is straightforward.</span></span> <span data-ttu-id="e8290-143">Wenn Sie die Benachrichtigungsbibliothek von NuGet nicht installieren, müssen Sie den XML-Code manuell erstellen, was zu Fehlern führen kann.</span><span class="sxs-lookup"><span data-stu-id="e8290-143">If you don’t install the Notifications library from NuGet, you have to construct the XML manually, which leaves room for errors.</span></span>

<span data-ttu-id="e8290-144">Hinweis: Bilder können aus dem Paket der App, dem lokalen Speicher der App oder aus dem Web verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e8290-144">Note: Images can be used from the app’s package, the app’s local storage, or from the web.</span></span> <span data-ttu-id="e8290-145">Webbilder müssen kleiner als 200KB sein.</span><span class="sxs-lookup"><span data-stu-id="e8290-145">Web images must be less than 200 KB in size.</span></span>

```csharp
// In a real app, these would be initialized with actual data
string title = "Andrew sent you a picture";
string content = "Check this out, Happy Canyon in Utah!";
string image = "https://unsplash.it/360/202?image=883";
string logo = "ms-appdata:///local/Andrew.jpg";
 
// Construct the visuals of the toast
ToastVisual visual = new ToastVisual()
{
    BindingGeneric = new ToastBindingGeneric()
    {
        Children =
        {
            new AdaptiveText()
            {
                Text = title
            },
 
            new AdaptiveText()
            {
                Text = content
            },
 
            new AdaptiveImage()
            {
                Source = image
            }
        },
 
        AppLogoOverride = new ToastGenericAppLogo()
        {
            Source = logo,
            HintCrop = ToastGenericAppLogoCrop.Circle
        }
    }
};
```


### <a name="constructing-actions-part-of-the-content"></a><span data-ttu-id="e8290-146">Erstellen des Aktionsteils des Inhalts</span><span class="sxs-lookup"><span data-stu-id="e8290-146">Constructing actions part of the content</span></span>

<span data-ttu-id="e8290-147">Lassen Sie uns nun Aktionen zum Inhalt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e8290-147">Now let’s add actions to the content.</span></span>

<span data-ttu-id="e8290-148">In dem Beispiel unten haben wir ein Eingabeelement verwendet, mit dem der Benutzer Text eingeben kann, der dann mithilfe dessen ID von der App abgerufen werden kann, nachdem sie im Vordergrund oder Hintergrund aktiviert wurde– je nachdem, wie die Interaktionen für die einzelnen Aktionen definiert sind.</span><span class="sxs-lookup"><span data-stu-id="e8290-148">In the below example, we included an input element that allows the user to input text, which can then be retrieved by the app using its id, once it is activated in the foreground or background – depending on how the interactions are defined for each of the actions.</span></span>

<span data-ttu-id="e8290-149">Wir haben dann zwei Schaltflächen erstellt, die jeweils einen eigenen Aktivierungstyp, eigenen Inhalt und eigene Argumente angeben.</span><span class="sxs-lookup"><span data-stu-id="e8290-149">We then created two buttons, each specifying its own activation type, content, and arguments.</span></span>
* <span data-ttu-id="e8290-150">ActivationType wird verwendet, um anzugeben, wie die App aktiviert werden soll, wenn diese Aktion vom Benutzer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e8290-150">ActivationType is used to specify how the app wants to be activated when this action is performed by the user.</span></span> <span data-ttu-id="e8290-151">Sie können entscheiden, Ihre App im Vordergrund zu starten, eine Hintergrundaufgabe zu starten oder eine andere App per Protokollstart zu starten.</span><span class="sxs-lookup"><span data-stu-id="e8290-151">You can choose to launch your app in the foreground, launch a background task, or protocol launch another app.</span></span> <span data-ttu-id="e8290-152">Unabhängig davon, ob Ihre App den Aktivierungstyp Vordergrund oder Hintergrund wählt, ist es Ihnen stets möglich, die Eingabe des Benutzers sowie die im Argument-Attribut vordefinierten Argumente abzurufen. So steht Ihnen der gesamte Kontext dessen zur Verfügung, was der Benutzer mit der Benachrichtigung gemacht hat.</span><span class="sxs-lookup"><span data-stu-id="e8290-152">Whether your app chooses the activation type to be foreground or background, there is always a way for you to retrieve the user input, as well as the args you pre-defined in the arguments attribute, so you have the full context of what the user did to the notification.</span></span>

```csharp
// In a real app, these would be initialized with actual data
int conversationId = 384928;
 
// Construct the actions for the toast (inputs and buttons)
ToastActionsCustom actions = new ToastActionsCustom()
{
    Inputs =
    {
        new ToastTextBox("tbReply")
        {
            PlaceholderContent = "Type a response"
        }
    },
 
    Buttons =
    {
        new ToastButton("Reply", new QueryString()
        {
            { "action", "reply" },
            { "conversationId", conversationId.ToString() }
 
        }.ToString())
        {
            ActivationType = ToastActivationType.Background,
            ImageUri = "Assets/Reply.png",
 
            // Reference the text box's ID in order to
            // place this button next to the text box
            TextBoxId = "tbReply"
        },
 
        new ToastButton("Like", new QueryString()
        {
            { "action", "like" },
            { "conversationId", conversationId.ToString() }
 
        }.ToString())
        {
            ActivationType = ToastActivationType.Background
        },
 
        new ToastButton("View", new QueryString()
        {
            { "action", "viewImage" },
            { "imageUrl", image }
 
        }.ToString())
    }
};
```


### <a name="combining-the-above-to-construct-the-full-content"></a><span data-ttu-id="e8290-153">Kombinieren der obigen Ausführungen zum Erstellen des gesamten Inhalts</span><span class="sxs-lookup"><span data-stu-id="e8290-153">Combining the above to construct the full content</span></span>

<span data-ttu-id="e8290-154">Die Erstellung des Inhalts ist jetzt fertig und wir können diesen verwenden, um Ihr ToastNotification-Objekt zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="e8290-154">The construction of the content is now complete, and we can use it to instantiate your ToastNotification object.</span></span>

<span data-ttu-id="e8290-155">**Hinweis:**: Sie können auch einen Aktivierungstyp innerhalb des Stammelements angeben, um festzulegen, welche Art von Aktivierung erfolgen muss, wenn der Benutzer auf den Text der Popupbenachrichtigung tippt.</span><span class="sxs-lookup"><span data-stu-id="e8290-155">**Note**: you can also provide an activation type inside the root element, to specify what type of activation needs to happen when the user taps on the body of the toast notification.</span></span> <span data-ttu-id="e8290-156">Normalerweise sollte durch Tippen auf den Text des Popups Ihre App im Vordergrund gestartet werden, um eine konsistente Benutzererfahrung zu schaffen. In Fällen, in denen es sinnvoll ist, können Sie jedoch andere Aktivierungstypen verwenden, die für Ihr spezielles Szenario geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="e8290-156">Normally, tapping the body of the toast should launch your app in the foreground to create a consistent user experience, but you can use other activation types to fit your specific scenario where it makes most sense to the user.</span></span>

<span data-ttu-id="e8290-157">Wie zuvor können und sollten Sie zum Stammelement immer einen Startparameter hinzufügen, sodass Ihre App weiterhin mit einer Ansicht gestartet werden kann, die sich auf den Inhalt der Benachrichtigung bezieht, wenn der Benutzer auf den Text des Popups klickt.</span><span class="sxs-lookup"><span data-stu-id="e8290-157">Just like before, you can and should always add a launch parameter to the root element, so when user taps the body of the toast, your app can still be launched with a view that relates to the content of the notification.</span></span>

```csharp
// Now we can construct the final toast content
ToastContent toastContent = new ToastContent()
{
    Visual = visual,
    Actions = actions,
 
    // Arguments when the user taps body of toast
    Launch = new QueryString()
    {
        { "action", "viewConversation" },
        { "conversationId", conversationId.ToString() }
 
    }.ToString()
};
 
// And create the toast notification
var toast = new ToastNotification(toastContent.GetXml());
```


## <a name="set-an-expiration-time"></a><span data-ttu-id="e8290-158">Festlegen einer Ablaufzeit</span><span class="sxs-lookup"><span data-stu-id="e8290-158">Set an expiration time</span></span>

<span data-ttu-id="e8290-159">In Windows10 werden alle Popupbenachrichtigungen ins Info-Center (das zuvor nur für Handys verfügbar war, jetzt aber auf allen Windows-Geräten verfügbar ist) verschoben, nachdem sie vom Benutzer geschlossen oder ignoriert wurden, sodass Benutzer sich Ihre Benachrichtigung ansehen können, nachdem das Popup ausgeblendet wurde.</span><span class="sxs-lookup"><span data-stu-id="e8290-159">In Windows 10, all toast notifications go in Action Center (which was previously only available on phone, but now available on all Windows devices) after they are dismissed or ignored by the user, so users can look at your notification after the popup is gone.</span></span>

<span data-ttu-id="e8290-160">Wenn die Nachricht in Ihrer Benachrichtigung jedoch nur für einen bestimmten Zeitraum relevant ist, sollten Sie für die Popupbenachrichtigung eine Ablaufzeit festlegen, damit dem Benutzer keine veralteten Informationen von Ihrer App angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e8290-160">However, if the message in your notification is only relevant for a period of time, you should set an expiration time on the toast notification so the users do not see stale information from your app.</span></span> <span data-ttu-id="e8290-161">Im folgenden Code legen wir die Ablaufzeit auf 2Tage fest.</span><span class="sxs-lookup"><span data-stu-id="e8290-161">In the code below we set the expiration time to be 2 days.</span></span>

<span data-ttu-id="e8290-162">**Hinweis:**: Die standardmäßige und maximale Ablaufzeit für lokale Popupbenachrichtigungen ist 3Tage.</span><span class="sxs-lookup"><span data-stu-id="e8290-162">**Note**: The default and maximum expiration time for local toast notifications is 3 days.</span></span>

```csharp
toast.ExpirationTime = DateTime.Now.AddDays(2);
```


## <a name="provide-a-primary-key-for-your-toast"></a><span data-ttu-id="e8290-163">Angeben eines primären Schlüssels für das Popup</span><span class="sxs-lookup"><span data-stu-id="e8290-163">Provide a primary key for your toast</span></span>

<span data-ttu-id="e8290-164">Wenn Sie die Benachrichtigung, die Sie senden, jemals programmgesteuert entfernen oder ersetzen möchten, müssen Sie die Tag-Eigenschaft (und optional die Group-Eigenschaft) verwenden, um einen primären Schlüssel für die Benachrichtigung anzugeben.</span><span class="sxs-lookup"><span data-stu-id="e8290-164">If you ever want to programmatically remove or replace the notification you send, you need to use the Tag property (and optionally the Group property) to provide a primary key for your notification.</span></span> <span data-ttu-id="e8290-165">Sie können diesen primären Schlüssel dann zukünftig verwenden, um die Benachrichtigung zu entfernen oder zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="e8290-165">Then, you can use this primary key in the future to remove or replace the notification.</span></span>

<span data-ttu-id="e8290-166">Weitere Informationen zum Ersetzen/Entfernen bereits übermittelter Popupbenachrichtigungen finden Sie unter [Schnellstart: Verwalten von Popupbenachrichtigungen im Info-Center (XAML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/dn631260.aspx).</span><span class="sxs-lookup"><span data-stu-id="e8290-166">To see more details on replacing/removing already delivered toast notifications, please see [Quickstart: Managing toast notifications in action center (XAML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/dn631260.aspx).</span></span>

<span data-ttu-id="e8290-167">Tag und Group fungieren kombiniert als ein zusammengesetzter primärer Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="e8290-167">Tag and Group combined act as a composite primary key.</span></span> <span data-ttu-id="e8290-168">Group ist die allgemeinere ID, wobei Sie Gruppen wie „WallPosts“, „Nachrichten“, „FriendRequests“ etc. zuweisen können. Und Tag sollte dann die Benachrichtigung selbst innerhalb der Gruppe eindeutig identifizieren.</span><span class="sxs-lookup"><span data-stu-id="e8290-168">Group is the more generic identifier, where you can assign groups like "wallPosts", "messages", "friendRequests", etc. And then Tag should uniquely identify the notification itself from within the group.</span></span> <span data-ttu-id="e8290-169">Unter Verwendung einer allgemeinen Gruppe können Sie dann mithilfe der [RemoveGroup-API](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Notifications.ToastNotificationHistory#Windows_UI_Notifications_ToastNotificationHistory_RemoveGroup_System_String_) alle Benachrichtigungen aus dieser Gruppe entfernen.</span><span class="sxs-lookup"><span data-stu-id="e8290-169">By using a generic group, you can then remove all notifications from that group by using the [RemoveGroup API](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Notifications.ToastNotificationHistory#Windows_UI_Notifications_ToastNotificationHistory_RemoveGroup_System_String_).</span></span>

```csharp
toast.Tag = "18365";
toast.Group = "wallPosts";
```


## <a name="send-the-notification"></a><span data-ttu-id="e8290-170">Senden der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="e8290-170">Send the notification</span></span>

<span data-ttu-id="e8290-171">Wenn Sie das Popup erstellt haben, erstellen Sie einfach einen ToastNotifier, und rufen Sie Show() auf, um Ihre Popupbenachrichtigung zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="e8290-171">Once you have your toast constructed, simply create a ToastNotifier and call Show(), passing in your toast notification.</span></span>

```
ToastNotificationManager.CreateToastNotifier().Show(toast);
```


## <a name="clear-your-notifications"></a><span data-ttu-id="e8290-172">Löschen der Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="e8290-172">Clear your notifications</span></span>

<span data-ttu-id="e8290-173">UWP-Apps sind verantwortlich für das Entfernen und Löschen ihrer eigenen Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="e8290-173">UWP apps are responsible for removing and clearing their own notifications.</span></span> <span data-ttu-id="e8290-174">Wenn Ihre App gestartet wird, löschen wir NICHT automatisch Ihre Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="e8290-174">When your app is launched, we do NOT automatically clear your notifications.</span></span>

<span data-ttu-id="e8290-175">Windows entfernt nur dann automatisch eine Benachrichtigung, wenn der Benutzer explizit auf die Benachrichtigung klickt.</span><span class="sxs-lookup"><span data-stu-id="e8290-175">Windows will only automatically remove a notification if the user explicitly clicks the notification.</span></span>

<span data-ttu-id="e8290-176">Hier ist ein Beispiel dafür, was eine Nachrichten-App tun sollte...</span><span class="sxs-lookup"><span data-stu-id="e8290-176">Here’s an example of what a messaging app should do…</span></span>

1. <span data-ttu-id="e8290-177">Benutzer erhält mehrere Popups über neue Nachrichten in einer Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="e8290-177">User receives multiple toasts about new messages in a conversation</span></span>
2. <span data-ttu-id="e8290-178">Benutzer tippt auf eines dieser Popups, um die Unterhaltung zu öffnen</span><span class="sxs-lookup"><span data-stu-id="e8290-178">User taps one of those toasts to open the conversation</span></span>
3. <span data-ttu-id="e8290-179">Die App öffnet die Unterhaltung und löscht dann alle Popups für die Unterhaltung (mithilfe von [RemoveGroup](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Notifications.ToastNotificationHistory#Windows_UI_Notifications_ToastNotificationHistory_RemoveGroup_System_String_) für die von der App bereitgestellte Gruppe für diese Unterhaltung)</span><span class="sxs-lookup"><span data-stu-id="e8290-179">The app opens the conversation and then clears all toasts for that conversation (by using [RemoveGroup](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Notifications.ToastNotificationHistory#Windows_UI_Notifications_ToastNotificationHistory_RemoveGroup_System_String_) on the app-supplied group for that conversation)</span></span>
4. <span data-ttu-id="e8290-180">Im Info-Center des Benutzers wird jetzt ordnungsgemäß der Zustand der Benachrichtigung angegeben, da im Info-Center keine veralteten Benachrichtigungen für die Unterhaltung vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="e8290-180">User’s Action Center now properly reflects the notification state, since there are no stale notifications for that conversation left in Action Center.</span></span>

<span data-ttu-id="e8290-181">Informationen zum Löschen aller Benachrichtigungen oder Entfernen bestimmter Benachrichtigungen finden Sie unter [Schnellstart: Verwalten von Popupbenachrichtigungen im Info-Center (XAML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/dn631260.aspx).</span><span class="sxs-lookup"><span data-stu-id="e8290-181">To learn about clearing all notifications or removing specific notifications, see [Quickstart: Managing toast notifications in action center (XAML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/dn631260.aspx).</span></span>


## <a name="handling-activation"></a><span data-ttu-id="e8290-182">Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="e8290-182">Handling activation</span></span>

<span data-ttu-id="e8290-183">Wenn der Benutzer in Windows10 auf das Popup klickt, haben Sie zwei Möglichkeiten der Aktivierung Ihrer App durch das Popup...</span><span class="sxs-lookup"><span data-stu-id="e8290-183">In Windows 10, when the user clicks on your toast, you can have the toast activate your app in two different ways...</span></span>

* <span data-ttu-id="e8290-184">Vordergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="e8290-184">Foreground activation</span></span>
* <span data-ttu-id="e8290-185">Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="e8290-185">Background activation</span></span>

<span data-ttu-id="e8290-186">**Hinweis:**: Wenn Sie die älteren Popupvorlagen von Windows8.1 verwenden, wird stattdessen OnLaunched aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="e8290-186">**Note**: If you are using the legacy toast templates from Windows 8.1, OnLaunched will be called instead.</span></span> <span data-ttu-id="e8290-187">Die folgende Dokumentation gilt nur für moderne Windows10-Benachrichtigungen, die die Benachrichtigungsbibliothek (oder die ToastGeneric-Vorlage bei Verwendung von XML-Rohdaten) verwenden.</span><span class="sxs-lookup"><span data-stu-id="e8290-187">The following documentation only applies to modern Windows 10 notifications utilizing the Notifications library (or the ToastGeneric template if using raw XML).</span></span>


### <a name="handling-foreground-activation"></a><span data-ttu-id="e8290-188">Behandeln der Vordergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="e8290-188">Handling foreground activation</span></span>

<span data-ttu-id="e8290-189">Wenn ein Benutzer in Windows10 auf ein modernes Popup (oder eine Schaltfläche im Popup) klickt, wird anstelle von OnLaunched OnActivated mit der neuen Art der Aktivierung– ToastNotification– aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="e8290-189">In Windows 10, when a user clicks a modern toast (or a button on the toast), OnActivated is invoked instead of OnLaunched, with a new activation kind – ToastNotification.</span></span> <span data-ttu-id="e8290-190">Dadurch kann der Entwickler eine Popupaktivierung auf einfache Weise erkennen und Aufgaben entsprechend ausführen.</span><span class="sxs-lookup"><span data-stu-id="e8290-190">Thus, the developer is able to easily distinguish a toast activation and perform tasks accordingly.</span></span>

<span data-ttu-id="e8290-191">Im Beispiel unten können Sie die Argumentzeichenfolge abrufen, die Sie ursprünglich im Popupinhalt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="e8290-191">In the example you see below, you can retrieve the arguments string you initially provided in the toast content.</span></span> <span data-ttu-id="e8290-192">Sie können auch die Eingabe des Benutzers in Ihren Textfeldern und Auswahlfeldern abrufen.</span><span class="sxs-lookup"><span data-stu-id="e8290-192">You can also retrieve the input the user provided in your text boxes and selection boxes.</span></span>

<span data-ttu-id="e8290-193">**Hinweis:**: Sie müssen Ihren Frame initialisieren und Ihr Fenster aktivieren, wie Ihren OnLaunched-Code.</span><span class="sxs-lookup"><span data-stu-id="e8290-193">**Note**: You must initialize your frame and activate your window just like your OnLaunched code.</span></span> <span data-ttu-id="e8290-194">**OnLaunched wird NICHT aufgerufen, wenn der Benutzer auf das Popup klickt**, auch wenn die App geschlossen war und zum ersten Mal gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="e8290-194">**OnLaunched is NOT called if the user clicks on your toast**, even if your app was closed and is launching for the first time.</span></span> <span data-ttu-id="e8290-195">Wir empfehlen häufig, OnLaunched und OnActivated zu Ihrer eigenen OnLaunchedOrActivated-Methode zu kombinieren, da für beide die gleiche Initialisierung erfolgen muss.</span><span class="sxs-lookup"><span data-stu-id="e8290-195">We often recommend combining OnLaunched and OnActivated into your own OnLaunchedOrActivated method since the same initialization needs to occur in both.</span></span>

```csharp
protected override void OnActivated(IActivatedEventArgs e)
{
    // Get the root frame
    Frame rootFrame = Window.Current.Content as Frame;
 
    // TODO: Initialize root frame just like in OnLaunched
 
    // Handle toast activation
    if (e is ToastNotificationActivatedEventArgs)
    {
        var toastActivationArgs = e as ToastNotificationActivatedEventArgs;
                 
        // Parse the query string (using QueryString.NET)
        QueryString args = QueryString.Parse(toastActivationArgs.Argument);
 
        // See what action is being requested 
        switch (args["action"])
        {
            // Open the image
            case "viewImage":
 
                // The URL retrieved from the toast args
                string imageUrl = args["imageUrl"];
 
                // If we're already viewing that image, do nothing
                if (rootFrame.Content is ImagePage && (rootFrame.Content as ImagePage).ImageUrl.Equals(imageUrl))
                    break;
 
                // Otherwise navigate to view it
                rootFrame.Navigate(typeof(ImagePage), imageUrl);
                break;
                             
 
            // Open the conversation
            case "viewConversation":
 
                // The conversation ID retrieved from the toast args
                int conversationId = int.Parse(args["conversationId"]);
 
                // If we're already viewing that conversation, do nothing
                if (rootFrame.Content is ConversationPage && (rootFrame.Content as ConversationPage).ConversationId == conversationId)
                    break;
 
                // Otherwise navigate to view it
                rootFrame.Navigate(typeof(ConversationPage), conversationId);
                break;
        }
 
        // If we're loading the app for the first time, place the main page on
        // the back stack so that user can go back after they've been
        // navigated to the specific page
        if (rootFrame.BackStack.Count == 0)
            rootFrame.BackStack.Add(new PageStackEntry(typeof(MainPage), null, null));
    }
 
    // TODO: Handle other types of activation
 
    // Ensure the current window is active
    Window.Current.Activate();
}
```


## <a name="handling-background-activation"></a><span data-ttu-id="e8290-196">Behandeln der Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="e8290-196">Handling background activation</span></span>

<span data-ttu-id="e8290-197">Wenn Sie für das Popup (oder eine Schaltfläche in dem Popup) Hintergrundaktivierung angeben, wird anstelle einer Aktivierung Ihrer Vordergrund-App die Hintergrundaufgabe ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="e8290-197">When you specify background activation on your toast (or on a button inside the toast), your background task will be executed instead of activating your foreground app.</span></span>

<span data-ttu-id="e8290-198">Weitere Informationen zu Hintergrundaufgaben finden Sie unter [Unterstützen Ihrer App mit Hintergrundaufgaben](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/support-your-app-with-background-tasks).</span><span class="sxs-lookup"><span data-stu-id="e8290-198">For more information on background tasks, please see [Support your app with background tasks](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/support-your-app-with-background-tasks).</span></span>

<span data-ttu-id="e8290-199">Wenn Sie Build 14393 oder höher verwenden möchten, können Sie Hintergrundaufgaben innerhalb von Prozessen verwenden, was den Vorgang erheblich vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="e8290-199">If you are targeting build 14393 or higher, you can use in-process background tasks, which greatly simplify things.</span></span> <span data-ttu-id="e8290-200">Beachten Sie, dass Hintergrundaufgaben innerhalb von Prozessen nicht auf älteren Computern ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="e8290-200">Note that in-process background tasks will fail to run on older machines.</span></span> <span data-ttu-id="e8290-201">Wir verwenden in diesem Codebeispiel eine Hintergrundaufgabe innerhalb von Prozessen.</span><span class="sxs-lookup"><span data-stu-id="e8290-201">We'll use an in-process background task in this code sample.</span></span>

```csharp
const string taskName = "ToastBackgroundTask";

// If background task is already registered, do nothing
if (BackgroundTaskRegistration.AllTasks.Any(i => i.Value.Name.Equals(taskName)))
    return;

// Otherwise request access
BackgroundAccessStatus status = await BackgroundExecutionManager.RequestAccessAsync();

// Create the background task
BackgroundTaskBuilder builder = new BackgroundTaskBuilder()
{
    Name = "MyToastNotificationActionTrigger",
};

// Assign the toast action trigger
builder.SetTrigger(new ToastNotificationActionTrigger());

// And register the task
BackgroundTaskRegistration registration = builder.Register();
```


<span data-ttu-id="e8290-202">Wenn Sie dann in Ihrer App.xaml.cs-Datei die OnBackgroundActivated-Methode überschreiben, können Sie die vordefinierten Argumente und Benutzereingaben ähnlich wie bei der Vordergrundaktivierung abrufen.</span><span class="sxs-lookup"><span data-stu-id="e8290-202">Then in your App.xaml.cs, override the OnBackgroundActivated method you can retrieve the pre-defined arguments and user input, similar to the foreground activation.</span></span>

```csharp
protected override async void OnBackgroundActivated(BackgroundActivatedEventArgs args)
{
    var deferral = args.TaskInstance.GetDeferral();
 
    switch (args.TaskInstance.Task.Name)
    {
        case "ToastBackgroundTask":
            var details = args.TaskInstance.TriggerDetails as ToastNotificationActionTriggerDetail;
            if (details != null)
            {
                string arguments = details.Argument;
                var userInput = details.UserInput;

                // Perform tasks
            }
            break;
    }
 
    deferral.Complete();
}
```



## <a name="plain-vanilla-code-snippets"></a><span data-ttu-id="e8290-203">Einfache „Vanilla“-Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="e8290-203">Plain "Vanilla" code snippets</span></span>

<span data-ttu-id="e8290-204">Wenn Sie die Benachrichtigungsbibliothek von NuGet nicht verwenden, können Sie den XML-Code manuell erstellen, wie unten dargestellt, um eine ToastNotification zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e8290-204">If you're not using the Notifications library from NuGet, you can manually construct your XML as seen below to create a ToastNotification.</span></span>

```csharp
using Windows.UI.Notifications;
using Windows.Data.Xml.Dom;

// In a real app, these would be initialized with actual data
string title = "Andrew sent you a picture";
string content = "Check this out, Happy Canyon in Utah!";
string image = "http://blogs.msdn.com/cfs-filesystemfile.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-01-71-81-permanent/2727.happycanyon1_5B00_1_5D00_.jpg";
string logo = "ms-appdata:///local/Andrew.jpg";
 
// TODO: all values need to be XML escaped
 
// Construct the visuals of the toast
string toastVisual =
$@"<visual>
  <binding template='ToastGeneric'>
    <text>{title}</text>
    <text>{content}</text>
    <image src='{image}'/>
    <image src='{logo}' placement='appLogoOverride' hint-crop='circle'/>
  </binding>
</visual>";

// In a real app, these would be initialized with actual data
int conversationId = 384928;
 
// Generate the arguments we'll be passing in the toast
string argsReply = $"action=reply&conversationId={conversationId}";
string argsLike = $"action=like&conversationId={conversationId}";
string argsView = $"action=viewImage&imageUrl={Uri.EscapeDataString(image)}";
 
// TODO: all args need to be XML escaped
 
string toastActions =
$@"<actions>
 
  <input
      type='text'
      id='tbReply'
      placeHolderContent='Type a response'/>
 
  <action
      content='Reply'
      arguments='{argsReply}'
      activationType='background'
      imageUri='Assets/Reply.png'
      hint-inputId='tbReply'/>
 
  <action
      content='Like'
      arguments='{argsLike}'
      activationType='background'/>
 
  <action
      content='View'
      arguments='{argsView}'/>
 
</actions>";

// Now we can construct the final toast content
string argsLaunch = $"action=viewConversation&conversationId={conversationId}";
 
// TODO: all args need to be XML escaped
 
string toastXmlString =
$@"<toast launch='{argsLaunch}'>
    {toastVisual}
    {toastActions}
</toast>";
 
// Parse to XML
XmlDocument toastXml = new XmlDocument();
toastXml.LoadXml(toastXmlString);
 
// Generate toast
var toast = new ToastNotification(toastXml);
```


## <a name="resources"></a><span data-ttu-id="e8290-205">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="e8290-205">Resources</span></span>

* [<span data-ttu-id="e8290-206">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="e8290-206">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-sending-local-toast)
* [<span data-ttu-id="e8290-207">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="e8290-207">Toast content documentation</span></span>](tiles-and-notifications-adaptive-interactive-toasts.md)