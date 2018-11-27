---
Description: Learn how to send a local toast notification and handle the user clicking the toast.
title: Senden einer lokalen Popupbenachrichtigung
ms.assetid: E9AB7156-A29E-4ED7-B286-DA4A6E683638
label: Send a local toast notification
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP, Senden von Popupbenachrichtigungen, Benachrichtigungen, Benachrichtigungen senden, Popupbenachrichtigungen, Vorgehensweise, Schnellstart, erste Schritte, Codebeispiel, exemplarische Vorgehensweise
ms.localizationpriority: medium
ms.openlocfilehash: dd7dfb621d84a3ce1d934c358ab60683caee9238
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7703014"
---
# <a name="send-a-local-toast-notification"></a><span data-ttu-id="9e2a5-103">Senden einer lokalen Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-103">Send a local toast notification</span></span>


<span data-ttu-id="9e2a5-104">Eine Popupbenachrichtigung ist eine Nachricht, die eine App erstellen und an den Benutzer übermitteln kann, während diese(r) Ihre App aktuell nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-104">A toast notification is a message that an app can construct and deliver to the user while they are not currently inside your app.</span></span> <span data-ttu-id="9e2a5-105">Diese Schnellstartanleitung führt Sie durch die Schritteder Erstellung, Übermittlung und Anzeige einer Windows10-Popupbenachrichtigung mit den neuen adaptiven Vorlagen und interaktiven Aktionen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-105">This Quickstart walks you through the steps to create, deliver, and display a Windows 10 toast notification with the new adaptive templates and interactive actions.</span></span> <span data-ttu-id="9e2a5-106">Diese Aktionen werden mit einer lokalen Benachrichtigung demonstriert– der einfachsten Benachrichtigung, die Sie implementieren können.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-106">These actions are demonstrated through a local notification, which is the simplest notification to implement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e2a5-107">Desktopanwendungen (Desktop-Brücke- und klassische Win32-Apps) haben verschiedene Schritte zum Senden von Benachrichtigungen und Behandeln der Aktivierung.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-107">Desktop applications (both Desktop Bridge and classic Win32) have different steps for sending notifications and handling activation.</span></span> <span data-ttu-id="9e2a5-108">Weitere Informationen zum Implementieren von Popups finden Sie in der Dokumentation zu [Desktop-Apps](toast-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="9e2a5-108">Please see the [Desktop apps](toast-desktop-apps.md) documentation to learn how to implement toasts.</span></span>

<span data-ttu-id="9e2a5-109">Wir werden die folgenden Schrittedurchlaufen:</span><span class="sxs-lookup"><span data-stu-id="9e2a5-109">We will go through the following things:</span></span>

### <a name="sending-a-toast"></a><span data-ttu-id="9e2a5-110">Senden eines Popups</span><span class="sxs-lookup"><span data-stu-id="9e2a5-110">Sending a toast</span></span>

* <span data-ttu-id="9e2a5-111">Erstellen des visuellen Teils (Text und Bilder) der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-111">Constructing the visual part (text and image) of the notification</span></span>
* <span data-ttu-id="9e2a5-112">Hinzufügen von Aktionen zur Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-112">Adding actions to the notification</span></span>
* <span data-ttu-id="9e2a5-113">Festlegen einer Ablaufzeit für das Popup</span><span class="sxs-lookup"><span data-stu-id="9e2a5-113">Setting an expiration time on the toast</span></span>
* <span data-ttu-id="9e2a5-114">Festlegen von Tag/Group, sodass Sie das Popup zu einem späteren Zeitpunkt ersetzen/entfernen können</span><span class="sxs-lookup"><span data-stu-id="9e2a5-114">Setting tag/group so you can replace/remove the toast at a later time</span></span>
* <span data-ttu-id="9e2a5-115">Senden Ihres Popups mithilfe der lokalen APIs</span><span class="sxs-lookup"><span data-stu-id="9e2a5-115">Sending your toast using the local APIs</span></span>

### <a name="handling-activation"></a><span data-ttu-id="9e2a5-116">Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-116">Handling activation</span></span>

* <span data-ttu-id="9e2a5-117">Behandeln der Aktivierung beim Klicken auf den Text oder Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="9e2a5-117">Handling activation when the body or buttons are clicked</span></span>
* <span data-ttu-id="9e2a5-118">Behandeln der Vordergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-118">Handling foreground activation</span></span>
* <span data-ttu-id="9e2a5-119">Behandeln der Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-119">Handling background activation</span></span>

> <span data-ttu-id="9e2a5-120">**Wichtige APIs**: [ToastNotification-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification), [ToastNotificationActivatedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Activation.ToastNotificationActivatedEventArgs)</span><span class="sxs-lookup"><span data-stu-id="9e2a5-120">**Important APIs**: [ToastNotification Class](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification), [ToastNotificationActivatedEventArgs Class](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Activation.ToastNotificationActivatedEventArgs)</span></span>


## <a name="prerequisites"></a><span data-ttu-id="9e2a5-121">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="9e2a5-121">Prerequisites</span></span>

<span data-ttu-id="9e2a5-122">Um dieses Thema vollständig zu verstehen, ist Folgendes hilfreich...</span><span class="sxs-lookup"><span data-stu-id="9e2a5-122">To fully understand this topic, the following will be helpful...</span></span>

* <span data-ttu-id="9e2a5-123">Ein grundlegendes Verständnis der Begriffe und Konzepte rund um Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-123">A working knowledge of toast notification terms and concepts.</span></span> <span data-ttu-id="9e2a5-124">Weitere Informationen finden Sie in der[Popup und Info-center (Übersicht)](https://blogs.msdn.microsoft.com/tiles_and_toasts/2015/07/08/toast-notification-and-action-center-overview-for-windows-10/).</span><span class="sxs-lookup"><span data-stu-id="9e2a5-124">For more information, see[Toast and action center overview](https://blogs.msdn.microsoft.com/tiles_and_toasts/2015/07/08/toast-notification-and-action-center-overview-for-windows-10/).</span></span>
* <span data-ttu-id="9e2a5-125">Kenntnisse in Bezug auf den Inhalt von Windows10-Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-125">A familiarity with Windows 10 toast notification content.</span></span> <span data-ttu-id="9e2a5-126">Weitere Informationen finden Sie in der [Dokumentation zu Popup-Inhalt](adaptive-interactive-toasts.md).</span><span class="sxs-lookup"><span data-stu-id="9e2a5-126">For more information, see [toast content documentation](adaptive-interactive-toasts.md).</span></span>
* <span data-ttu-id="9e2a5-127">Ein Windows10-UWP-App-Projekt</span><span class="sxs-lookup"><span data-stu-id="9e2a5-127">A Windows 10 UWP app project</span></span>

> [!NOTE]
> <span data-ttu-id="9e2a5-128">Im Gegensatz zu Windows8/8.1 müssen Sie in Ihrem App-Manifest nicht mehr deklarieren, dass Ihre App Popupbenachrichtigungen anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-128">Unlike Windows 8/8.1, you no longer need to declare in your app's manifest that your app is capable of showing toast notifications.</span></span> <span data-ttu-id="9e2a5-129">Alle Apps können Popupbenachrichtigungen senden und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-129">All apps are capable of sending and displaying toast notifications.</span></span>

> [!NOTE]
> <span data-ttu-id="9e2a5-130">**Windows8/8.1-Apps**: Verwenden Sie die [archivierte Dokumentation](https://msdn.microsoft.com/library/windows/apps/xaml/hh868254.aspx).</span><span class="sxs-lookup"><span data-stu-id="9e2a5-130">**Windows 8/8.1 apps**: Please use the [archived documentation](https://msdn.microsoft.com/library/windows/apps/xaml/hh868254.aspx).</span></span>


## <a name="install-nuget-packages"></a><span data-ttu-id="9e2a5-131">Installieren von NuGet-Paketen</span><span class="sxs-lookup"><span data-stu-id="9e2a5-131">Install NuGet packages</span></span>

<span data-ttu-id="9e2a5-132">Wir empfehlen die Installation der beiden folgenden NuGet-Pakete für Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-132">We recommend installing the two following NuGet packages to your project.</span></span> <span data-ttu-id="9e2a5-133">In unserem Codebeispiel werden diese Pakete verwendet.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-133">Our code sample will use these packages.</span></span> <span data-ttu-id="9e2a5-134">Am Ende des Artikels finden Sie die „Vanilla“-Codeausschnitte, die keine NuGet-Pakete verwenden.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-134">At the end of the article we'll provide the "Vanilla" code snippets that don't use any NuGet packages.</span></span>

* <span data-ttu-id="9e2a5-135">[Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/): Generieren von Popup-Nutzlasten über Objekte anstelle von unformatiertem XML.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-135">[Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/): Generate toast payloads via objects instead of raw XML.</span></span>
* <span data-ttu-id="9e2a5-136">[QueryString.NET](https://www.nuget.org/packages/QueryString.NET/): Generieren und Analysieren von Abfragezeichenfolgen mit C#</span><span class="sxs-lookup"><span data-stu-id="9e2a5-136">[QueryString.NET](https://www.nuget.org/packages/QueryString.NET/): Generate and parse query strings with C#</span></span>


## <a name="add-namespace-declarations"></a><span data-ttu-id="9e2a5-137">Hinzufügen von Namespacedeklarationen</span><span class="sxs-lookup"><span data-stu-id="9e2a5-137">Add namespace declarations</span></span>

`Windows.UI.Notifications` <span data-ttu-id="9e2a5-138">enthält die Popup-APIs.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-138">includes the toast APIs.</span></span>

```csharp
using Windows.UI.Notifications;
using Microsoft.Toolkit.Uwp.Notifications; // Notifications library
using Microsoft.QueryStringDotNET; // QueryString.NET
```


## <a name="send-a-toast"></a><span data-ttu-id="9e2a5-139">Senden eines Popups</span><span class="sxs-lookup"><span data-stu-id="9e2a5-139">Send a toast</span></span>

<span data-ttu-id="9e2a5-140">In Windows10 wird der Inhalt der Popupbenachrichtigung mithilfe einer adaptiven Sprache beschrieben, die eine sehr flexible Darstellung Ihrer Benachrichtigung erlaubt.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-140">In Windows 10, your toast notification content is described using an adaptive language that allows great flexibility with how your notification looks.</span></span> <span data-ttu-id="9e2a5-141">Weitere Informationen finden Sie in der [Dokumentation zu Popupinhalt](adaptive-interactive-toasts.md).</span><span class="sxs-lookup"><span data-stu-id="9e2a5-141">See the [toast content documentation](adaptive-interactive-toasts.md) for more information.</span></span>

### <a name="constructing-the-visual-part-of-the-content"></a><span data-ttu-id="9e2a5-142">Erstellen des visuellen Teils des Inhalts</span><span class="sxs-lookup"><span data-stu-id="9e2a5-142">Constructing the visual part of the content</span></span>

<span data-ttu-id="9e2a5-143">Beginnen wir mit der Erstellung des visuellen Teils des Inhalts, der den Text und Bilder umfasst, der dem Benutzer angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-143">Let's start by constructing the visual part of the content, which includes the text and images you want the user to see.</span></span>

<span data-ttu-id="9e2a5-144">Dank der benachrichtigungsbibliothek ist das Generierung des XML-Inhalts einfach.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-144">Thanks to the Notifications library, generating the XML content is straightforward.</span></span> <span data-ttu-id="9e2a5-145">Wenn Sie die Benachrichtigungsbibliothek von NuGet nicht installieren, müssen Sie den XML-Code manuell erstellen, was zu Fehlern führen kann.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-145">If you don't install the Notifications library from NuGet, you have to construct the XML manually, which leaves room for errors.</span></span>

> [!NOTE]
> <span data-ttu-id="9e2a5-146">Die verwendeten Bilder können aus dem App-Paket, dem lokalen Speicher der App oder aus dem Web stammen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-146">Images can be used from the app's package, the app's local storage, or from the web.</span></span> <span data-ttu-id="9e2a5-147">Im Fall Creators Update kann die Größe der Webbilder 3MB für normale Verbindungen und 1MB für getaktete Verbindungen betragen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-147">As of the Fall Creators Update, web images can be up to 3 MB on normal connections and 1 MB on metered connections.</span></span> <span data-ttu-id="9e2a5-148">Auf Geräten, die noch nicht das Fall Creators Update haben, dürfen Webbilder nicht größer als 200KB sein.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-148">On devices not yet running the Fall Creators Update, web images must be no larger than 200 KB.</span></span>

```csharp
// In a real app, these would be initialized with actual data
string title = "Andrew sent you a picture";
string content = "Check this out, Happy Canyon in Utah!";
string image = "https://picsum.photos/360/202?image=883";
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


### <a name="constructing-actions-part-of-the-content"></a><span data-ttu-id="9e2a5-149">Erstellen des Aktionsteils des Inhalts</span><span class="sxs-lookup"><span data-stu-id="9e2a5-149">Constructing actions part of the content</span></span>

<span data-ttu-id="9e2a5-150">Lassen Sie uns nun Aktionen zum Inhalt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-150">Now let's add actions to the content.</span></span>

<span data-ttu-id="9e2a5-151">Im folgenden Beispiel haben wir ein Eingabeelement hinzugefügt, das dem Benutzer ermöglicht, Text einzugeben, der an die App zurückgegeben wird, wenn der Benutzer auf eine der Schaltflächen oder das Popup selbst klickt.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-151">In the below example, we included an input element that allows the user to input text, which is returned to the app when the user clicks one of the buttons or the toast itself.</span></span>

<span data-ttu-id="9e2a5-152">Wir haben dann zwei Schaltflächen hinzugefügt, die jeweils einen eigenen Aktivierungstyp, eigenen Inhalt und eigene Argumente angeben.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-152">We then added two buttons, each with its own activation type, content, and arguments.</span></span>
* <span data-ttu-id="9e2a5-153">**ActivationType** wird verwendet, um anzugeben, wie Ihre App aktiviert werden soll, wenn diese Aktion vom Benutzer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-153">**ActivationType** is used to specify how your app wants to be activated when this action is performed by the user.</span></span> <span data-ttu-id="9e2a5-154">Sie können entscheiden, Ihre App im Vordergrund zu starten, eine Hintergrundaufgabe zu starten oder eine andere App per Protokollstart zu starten.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-154">You can choose to launch your app in the foreground, launch a background task, or protocol launch another app.</span></span> <span data-ttu-id="9e2a5-155">Egal ob Ihre App im Vordergrund oder Hintergrund ist, Sie erhalten immer die Benutzereingaben und die Argumente, die Sie angegeben haben, damit Ihre App die richtigen Maßnahmen durchführen kann, wie das Senden der Nachricht oder das Öffnen einer Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-155">Whether your app chooses foreground or background, you will always receive the user input and the arguments you specified, so your app can perform the correct action, like sending the message or opening a conversation.</span></span>

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


### <a name="combining-the-above-to-construct-the-full-content"></a><span data-ttu-id="9e2a5-156">Kombinieren der obigen Ausführungen zum Erstellen des gesamten Inhalts</span><span class="sxs-lookup"><span data-stu-id="9e2a5-156">Combining the above to construct the full content</span></span>

<span data-ttu-id="9e2a5-157">Die Erstellung des Inhalts ist jetzt fertig und wir können diesen verwenden, um Ihr [**ToastNotification**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification)-Objekt zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-157">The construction of the content is now complete, and we can use it to instantiate your [**ToastNotification**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification) object.</span></span>

<span data-ttu-id="9e2a5-158">**Hinweis:**: Sie können auch einen Aktivierungstyp innerhalb des Stammelements angeben, um festzulegen, welche Art von Aktivierung erfolgen muss, wenn der Benutzer auf den Text der Popupbenachrichtigung tippt.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-158">**Note**: you can also provide an activation type inside the root element, to specify what type of activation needs to happen when the user taps on the body of the toast notification.</span></span> <span data-ttu-id="9e2a5-159">Normalerweise sollte durch Tippen auf den Text des Popups Ihre App im Vordergrund gestartet werden, um eine konsistente Benutzererfahrung zu schaffen. In Fällen, in denen es sinnvoll ist, können Sie jedoch andere Aktivierungstypen verwenden, die für Ihr spezielles Szenario geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-159">Normally, tapping the body of the toast should launch your app in the foreground to create a consistent user experience, but you can use other activation types to fit your specific scenario where it makes most sense to the user.</span></span>

<span data-ttu-id="9e2a5-160">Sie sollten die **Start**-Eigenschaft immer angeben, um festzulegen, welche Art von Aktivierung erfolgen muss, wenn der Benutzer auf den Text der Popupbenachrichtigung tippt.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-160">You should always set the **Launch** property, so when user taps the body of the toast and your app is launched, your app knows what content it should display.</span></span>

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


## <a name="set-an-expiration-time"></a><span data-ttu-id="9e2a5-161">Festlegen einer Ablaufzeit</span><span class="sxs-lookup"><span data-stu-id="9e2a5-161">Set an expiration time</span></span>

<span data-ttu-id="9e2a5-162">In Windows10 werden alle Popupbenachrichtigungen ins Info-Center verschoben, nachdem sie vom Benutzer geschlossen oder ignoriert wurden, sodass Benutzer sich Ihre Benachrichtigung ansehen können, nachdem das Popup ausgeblendet wurde.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-162">In Windows 10, all toast notifications go in Action Center after they are dismissed or ignored by the user, so users can look at your notification after the popup is gone.</span></span>

<span data-ttu-id="9e2a5-163">Wenn die Nachricht in Ihrer Benachrichtigung jedoch nur für einen bestimmten Zeitraum relevant ist, sollten Sie für die Popupbenachrichtigung eine Ablaufzeit festlegen, damit dem Benutzer keine veralteten Informationen von Ihrer App angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-163">However, if the message in your notification is only relevant for a period of time, you should set an expiration time on the toast notification so the users do not see stale information from your app.</span></span> <span data-ttu-id="9e2a5-164">Wenn beispielsweise ein Angebot nur 12 Stunden gültig ist, legen Sie die Ablaufzeit auf 12 Stunden fest.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-164">For example, if a promotion is only valid for 12 hours, set the expiration time to 12 hours.</span></span> <span data-ttu-id="9e2a5-165">Im folgenden Code legen wir die Ablaufzeit auf 2Tage fest.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-165">In the code below, we set the expiration time to be 2 days.</span></span>

> [!NOTE]
> <span data-ttu-id="9e2a5-166">Die standardmäßige und maximale Ablaufzeit für lokale Popupbenachrichtigungen ist 3Tage.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-166">The default and maximum expiration time for local toast notifications is 3 days.</span></span>

```csharp
toast.ExpirationTime = DateTime.Now.AddDays(2);
```


## <a name="provide-a-primary-key-for-your-toast"></a><span data-ttu-id="9e2a5-167">Angeben eines primären Schlüssels für das Popup</span><span class="sxs-lookup"><span data-stu-id="9e2a5-167">Provide a primary key for your toast</span></span>

<span data-ttu-id="9e2a5-168">Wenn Sie die Benachrichtigung, die Sie senden, programmgesteuert entfernen oder ersetzen möchten, müssen Sie die Tag-Eigenschaft (und optional die Group-Eigenschaft) verwenden, um einen primären Schlüssel für die Benachrichtigung anzugeben.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-168">If you want to programmatically remove or replace the notification you send, you need to use the Tag property (and optionally the Group property) to provide a primary key for your notification.</span></span> <span data-ttu-id="9e2a5-169">Sie können diesen primären Schlüssel dann zukünftig verwenden, um die Benachrichtigung zu entfernen oder zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-169">Then, you can use this primary key in the future to remove or replace the notification.</span></span>

<span data-ttu-id="9e2a5-170">Weitere Informationen zum Ersetzen/Entfernen bereits übermittelter Popupbenachrichtigungen finden Sie unter [Schnellstart: Verwalten von Popupbenachrichtigungen im Info-Center (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/dn631260.aspx).</span><span class="sxs-lookup"><span data-stu-id="9e2a5-170">To see more details on replacing/removing already delivered toast notifications, please see [Quickstart: Managing toast notifications in action center (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/dn631260.aspx).</span></span>

<span data-ttu-id="9e2a5-171">Tag und Group fungieren kombiniert als ein zusammengesetzter primärer Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-171">Tag and Group combined act as a composite primary key.</span></span> <span data-ttu-id="9e2a5-172">Group ist die allgemeinere ID, wobei Sie Gruppen wie „WallPosts“, „Nachrichten“, „FriendRequests“ etc. zuweisen können. Und Tag sollte dann die Benachrichtigung selbst innerhalb der Gruppe eindeutig identifizieren.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-172">Group is the more generic identifier, where you can assign groups like "wallPosts", "messages", "friendRequests", etc. And then Tag should uniquely identify the notification itself from within the group.</span></span> <span data-ttu-id="9e2a5-173">Unter Verwendung einer allgemeinen Gruppe können Sie dann mithilfe der [RemoveGroup-API](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotificationHistory#Windows_UI_Notifications_ToastNotificationHistory_RemoveGroup_System_String_) alle Benachrichtigungen aus dieser Gruppe entfernen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-173">By using a generic group, you can then remove all notifications from that group by using the [RemoveGroup API](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotificationHistory#Windows_UI_Notifications_ToastNotificationHistory_RemoveGroup_System_String_).</span></span>

```csharp
toast.Tag = "18365";
toast.Group = "wallPosts";
```


## <a name="send-the-notification"></a><span data-ttu-id="9e2a5-174">Senden der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-174">Send the notification</span></span>

<span data-ttu-id="9e2a5-175">Wenn Sie das Popup initialisiert haben, erstellen Sie einfach einen [ToastNotifier](https://docs.microsoft.com/uwp/api/windows.ui.notifications.toastnotifier), und rufen Sie Show() auf, um Ihre Popupbenachrichtigung zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-175">Once you have initialized your toast, simply create a [ToastNotifier](https://docs.microsoft.com/uwp/api/windows.ui.notifications.toastnotifier) and call Show(), passing in your toast notification.</span></span>

```csharp
ToastNotificationManager.CreateToastNotifier().Show(toast);
```


## <a name="clear-your-notifications"></a><span data-ttu-id="9e2a5-176">Löschen der Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="9e2a5-176">Clear your notifications</span></span>

<span data-ttu-id="9e2a5-177">UWP-Apps sind verantwortlich für das Entfernen und Löschen ihrer eigenen Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-177">UWP apps are responsible for removing and clearing their own notifications.</span></span> <span data-ttu-id="9e2a5-178">Wenn Ihre App gestartet wird, löschen wir NICHT automatisch Ihre Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-178">When your app is launched, we do NOT automatically clear your notifications.</span></span>

<span data-ttu-id="9e2a5-179">Windows entfernt nur dann automatisch eine Benachrichtigung, wenn der Benutzer explizit auf die Benachrichtigung klickt.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-179">Windows will only automatically remove a notification if the user explicitly clicks the notification.</span></span>

<span data-ttu-id="9e2a5-180">Hier ist ein Beispiel dafür, was eine Nachrichten-App tun sollte...</span><span class="sxs-lookup"><span data-stu-id="9e2a5-180">Here's an example of what a messaging app should do…</span></span>

1. <span data-ttu-id="9e2a5-181">Benutzer erhält mehrere Popups über neue Nachrichten in einer Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-181">User receives multiple toasts about new messages in a conversation</span></span>
2. <span data-ttu-id="9e2a5-182">Benutzer tippt auf eines dieser Popups, um die Unterhaltung zu öffnen</span><span class="sxs-lookup"><span data-stu-id="9e2a5-182">User taps one of those toasts to open the conversation</span></span>
3. <span data-ttu-id="9e2a5-183">Die App öffnet die Unterhaltung und löscht dann alle Popups für die Unterhaltung (mithilfe von [RemoveGroup](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotificationHistory#Windows_UI_Notifications_ToastNotificationHistory_RemoveGroup_System_String_) für die von der App bereitgestellte Gruppe für diese Unterhaltung)</span><span class="sxs-lookup"><span data-stu-id="9e2a5-183">The app opens the conversation and then clears all toasts for that conversation (by using [RemoveGroup](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotificationHistory#Windows_UI_Notifications_ToastNotificationHistory_RemoveGroup_System_String_) on the app-supplied group for that conversation)</span></span>
4. <span data-ttu-id="9e2a5-184">Im Info-Center des Benutzers wird jetzt ordnungsgemäß der Zustand der Benachrichtigung angegeben, da im Info-Center keine veralteten Benachrichtigungen für die Unterhaltung vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-184">User's Action Center now properly reflects the notification state, since there are no stale notifications for that conversation left in Action Center.</span></span>

<span data-ttu-id="9e2a5-185">Informationen zum Löschen aller Benachrichtigungen oder Entfernen bestimmter Benachrichtigungen finden Sie unter [Schnellstart: Verwalten von Popupbenachrichtigungen im Info-Center (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/dn631260.aspx).</span><span class="sxs-lookup"><span data-stu-id="9e2a5-185">To learn about clearing all notifications or removing specific notifications, see [Quickstart: Managing toast notifications in action center (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/dn631260.aspx).</span></span>


## <a name="handling-activation"></a><span data-ttu-id="9e2a5-186">Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-186">Handling activation</span></span>

<span data-ttu-id="9e2a5-187">Wenn der Benutzer in Windows10 auf das Popup klickt, haben Sie zwei Möglichkeiten der Aktivierung Ihrer App durch das Popup...</span><span class="sxs-lookup"><span data-stu-id="9e2a5-187">In Windows 10, when the user clicks on your toast, you can have the toast activate your app in two different ways...</span></span>

* <span data-ttu-id="9e2a5-188">Vordergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-188">Foreground activation</span></span>
* <span data-ttu-id="9e2a5-189">Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-189">Background activation</span></span>

> [!NOTE]
> <span data-ttu-id="9e2a5-190">Wenn Sie die älteren Popupvorlagen von Windows8.1 verwenden, wird statt **OnActivated** **OnLaunched** aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-190">If you are using the legacy toast templates from Windows 8.1, **OnLaunched** will be called instead of **OnActivated**.</span></span> <span data-ttu-id="9e2a5-191">Die folgende Dokumentation gilt nur für moderne Windows10-Benachrichtigungen, die die Benachrichtigungsbibliothek (oder die ToastGeneric-Vorlage bei Verwendung von XML-Rohdaten) verwenden.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-191">The following documentation only applies to modern Windows 10 notifications utilizing the Notifications library (or the ToastGeneric template if using raw XML).</span></span>


### <a name="handling-foreground-activation"></a><span data-ttu-id="9e2a5-192">Behandeln der Vordergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-192">Handling foreground activation</span></span>

<span data-ttu-id="9e2a5-193">Wenn ein Benutzer in Windows10 auf ein modernes Popup (oder eine Schaltfläche im Popup) klickt, wird anstelle von **OnLaunched** **OnActivated** mit der neuen Art der Aktivierung– **ToastNotification**– aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-193">In Windows 10, when a user clicks a modern toast (or a button on the toast), **OnActivated** is invoked instead of **OnLaunched**, with a new activation kind – **ToastNotification**.</span></span> <span data-ttu-id="9e2a5-194">Dadurch kann der Entwickler eine Popupaktivierung auf einfache Weise erkennen und Aufgaben entsprechend ausführen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-194">Thus, the developer is able to easily distinguish a toast activation and perform tasks accordingly.</span></span>

<span data-ttu-id="9e2a5-195">Im Beispiel unten können Sie die Argumentzeichenfolge abrufen, die Sie ursprünglich im Popupinhalt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-195">In the example you see below, you can retrieve the arguments string you initially provided in the toast content.</span></span> <span data-ttu-id="9e2a5-196">Sie können auch die Eingabe des Benutzers in Ihren Textfeldern und Auswahlfeldern abrufen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-196">You can also retrieve the input the user provided in your text boxes and selection boxes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e2a5-197">Sie müssen Ihren Frame initialisieren und Ihr Fenster aktivieren, wie Ihren **OnLaunched**-Code.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-197">You must initialize your frame and activate your window just like your **OnLaunched** code.</span></span> <span data-ttu-id="9e2a5-198">**OnLaunched wird NICHT aufgerufen, wenn der Benutzer auf das Popup klickt**, auch wenn die App geschlossen war und zum ersten Mal gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-198">**OnLaunched is NOT called if the user clicks on your toast**, even if your app was closed and is launching for the first time.</span></span> <span data-ttu-id="9e2a5-199">Wir empfehlen häufig, **OnLaunched** und **OnActivated** zu Ihrer eigenen `OnLaunchedOrActivated`-Methode zu kombinieren, da für beide die gleiche Initialisierung erfolgen muss.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-199">We often recommend combining **OnLaunched** and **OnActivated** into your own `OnLaunchedOrActivated` method since the same initialization needs to occur in both.</span></span>

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


## <a name="handling-background-activation"></a><span data-ttu-id="9e2a5-200">Behandeln der Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="9e2a5-200">Handling background activation</span></span>

<span data-ttu-id="9e2a5-201">Wenn Sie für das Popup (oder eine Schaltfläche in dem Popup) Hintergrundaktivierung angeben, wird anstelle einer Aktivierung Ihrer Vordergrund-App die Hintergrundaufgabe ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-201">When you specify background activation on your toast (or on a button inside the toast), your background task will be executed instead of activating your foreground app.</span></span>

<span data-ttu-id="9e2a5-202">Weitere Informationen zu Hintergrundaufgaben finden Sie unter [Unterstützen Ihrer App mit Hintergrundaufgaben](/launch-resume/support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="9e2a5-202">For more information on background tasks, please see [Support your app with background tasks](/launch-resume/support-your-app-with-background-tasks.md).</span></span>

<span data-ttu-id="9e2a5-203">Wenn Sie Build 14393 oder höher verwenden möchten, können Sie Hintergrundaufgaben innerhalb von Prozessen verwenden, was den Vorgang erheblich vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-203">If you are targeting build 14393 or higher, you can use in-process background tasks, which greatly simplify things.</span></span> <span data-ttu-id="9e2a5-204">Beachten Sie, dass Hintergrundaufgaben innerhalb von Prozessen nicht auf älteren Versionen von Windows ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-204">Note that in-process background tasks will fail to run on older versions of Windows.</span></span> <span data-ttu-id="9e2a5-205">Wir verwenden in diesem Codebeispiel eine Hintergrundaufgabe innerhalb von Prozessen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-205">We'll use an in-process background task in this code sample.</span></span>

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
    Name = taskName
};

// Assign the toast action trigger
builder.SetTrigger(new ToastNotificationActionTrigger());

// And register the task
BackgroundTaskRegistration registration = builder.Register();
```


<span data-ttu-id="9e2a5-206">Wenn Sie dann in Ihrer App.xaml.cs-Datei die OnBackgroundActivated-Methode überschreiben, können Sie die vordefinierten Argumente und Benutzereingaben ähnlich wie bei der Vordergrundaktivierung abrufen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-206">Then in your App.xaml.cs, override the OnBackgroundActivated method you can retrieve the pre-defined arguments and user input, similar to the foreground activation.</span></span>

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



## <a name="plain-vanilla-code-snippets"></a><span data-ttu-id="9e2a5-207">Einfache „Vanilla“-Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="9e2a5-207">Plain "Vanilla" code snippets</span></span>

<span data-ttu-id="9e2a5-208">Wenn Sie die Benachrichtigungsbibliothek von NuGet nicht verwenden, können Sie den XML-Code manuell erstellen, wie unten dargestellt, um eine [ToastNotification](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9e2a5-208">If you're not using the Notifications library from NuGet, you can manually construct your XML as seen below to create a [ToastNotification](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification).</span></span>

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


## <a name="resources"></a><span data-ttu-id="9e2a5-209">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9e2a5-209">Resources</span></span>

* [<span data-ttu-id="9e2a5-210">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="9e2a5-210">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-sending-local-toast)
* [<span data-ttu-id="9e2a5-211">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="9e2a5-211">Toast content documentation</span></span>](adaptive-interactive-toasts.md)
* [<span data-ttu-id="9e2a5-212">ToastNotification-Klasse</span><span class="sxs-lookup"><span data-stu-id="9e2a5-212">ToastNotification Class</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification)
* [<span data-ttu-id="9e2a5-213">ToastNotificationActivatedEventArgs-Klasse</span><span class="sxs-lookup"><span data-stu-id="9e2a5-213">ToastNotificationActivatedEventArgs Class</span></span>](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Activation.ToastNotificationActivatedEventArgs)
