---
author: normesta
description: Veranschaulicht das Hinzufügen Ihrer App neben Aktionen in einer Visitenkarte
MSHAttr: PreferredLib:/library/windows/apps
title: Verbinden der App mit Aktionen auf einer Visitenkarte
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Kontakte, Visitenkarte, Anmerkung
ms.assetid: 0edabd9c-ecfb-4525-bc38-53f219d744ff
ms.localizationpriority: medium
ms.openlocfilehash: eb1c01a4fe370f899da185dc39b7d3abe6a1904e
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5766752"
---
# <a name="connect-your-app-to-actions-on-a-contact-card"></a><span data-ttu-id="2eacb-104">Verbinden der App mit Aktionen auf einer Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="2eacb-104">Connect your app to actions on a contact card</span></span>

<span data-ttu-id="2eacb-105">Ihre App kann neben Aktionen auf einer Visitenkarte oder kleinen Kontaktkarte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2eacb-105">Your app can appear next to actions on a contact card or mini contact card.</span></span> <span data-ttu-id="2eacb-106">Benutzer können Ihre App auswählen, um eine Aktion auszuführen, z. B. eine Profilseite zu öffnen, einen Anruf zu tätigen oder eine Nachricht zu senden.</span><span class="sxs-lookup"><span data-stu-id="2eacb-106">Users can choose your app to perform an action such as open a profile page, place a call, or send a message.</span></span>

![Visitenkarte und kleine Kontaktkarte](images/all-contact-cards.png)

<span data-ttu-id="2eacb-108">Suchen Sie zunächst vorhandene Kontakte oder erstellen Sie neue.</span><span class="sxs-lookup"><span data-stu-id="2eacb-108">To get started, find existing contacts or create new ones.</span></span> <span data-ttu-id="2eacb-109">Erstellen Sie dann eine *Anmerkung* und einige Paketmanifesteinträge, die beschreiben, welche Aktionen die App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2eacb-109">Next, create an *annotation* and a few package manifest entries to describe which actions your app supports.</span></span> <span data-ttu-id="2eacb-110">Anschließend schreiben Sie Code, der die Aktionen ausführt.</span><span class="sxs-lookup"><span data-stu-id="2eacb-110">Then, write code that perform the actions.</span></span>

<span data-ttu-id="2eacb-111">Ein ausführlicheres Beispiel finden Sie unter [Beispiel für die Visitenkarte-Integration](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ContactCardIntegration).</span><span class="sxs-lookup"><span data-stu-id="2eacb-111">For a more complete sample, see [Contact Card Integration Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ContactCardIntegration).</span></span>

## <a name="find-or-create-a-contact"></a><span data-ttu-id="2eacb-112">Suchen oder Erstellen eines Kontakts</span><span class="sxs-lookup"><span data-stu-id="2eacb-112">Find or create a contact</span></span>

<span data-ttu-id="2eacb-113">Wenn Ihre App den Kontakt mit anderen Personen unterstützt, durchsuchen Sie Windows nach Kontakten, und versehen Sie sie mit Anmerkungen.</span><span class="sxs-lookup"><span data-stu-id="2eacb-113">If your app helps people connect with others, search Windows for contacts and then annotate them.</span></span> <span data-ttu-id="2eacb-114">Wenn Ihre App Kontakte verwaltet, können Sie sie einer Windows-Kontaktliste hinzufügen und mit Anmerkungen versehen.</span><span class="sxs-lookup"><span data-stu-id="2eacb-114">If your app manages contacts, you can add them to a Windows contact list and then annotate them.</span></span>

### <a name="find-a-contact"></a><span data-ttu-id="2eacb-115">Suchen nach einem Kontakt</span><span class="sxs-lookup"><span data-stu-id="2eacb-115">Find a contact</span></span>

<span data-ttu-id="2eacb-116">Suchen Sie Kontakte über Namen, E-Mail-Adresse oder Telefonnummer.</span><span class="sxs-lookup"><span data-stu-id="2eacb-116">Find contacts by using a name, email address, or phone number.</span></span>

```cs
ContactStore contactStore = await ContactManager.RequestStoreAsync();

IReadOnlyList<Contact> contacts = null;

contacts = await contactStore.FindContactsAsync(emailAddress);

Contact contact = contacts[0];
```

### <a name="create-a-contact"></a><span data-ttu-id="2eacb-117">Erstellen eines Kontakts</span><span class="sxs-lookup"><span data-stu-id="2eacb-117">Create a contact</span></span>

<span data-ttu-id="2eacb-118">Wenn Ihre App eher wie ein Adressbuch konzipiert ist, erstellen Sie Kontakte und fügen Sie sie dann einer Kontaktliste zu.</span><span class="sxs-lookup"><span data-stu-id="2eacb-118">If your app is more like an address book, create contacts and then add them to a contact list.</span></span>

```cs
Contact contact = new Contact();
contact.FirstName = "TestContact";

ContactEmail email = new ContactEmail();
email.Address = "TestContact@contoso.com";
email.Kind = ContactEmailKind.Other;
contact.Emails.Add(email);

ContactPhone phone = new ContactPhone();
phone.Number = "4255550101";
phone.Kind = ContactPhoneKind.Mobile;
contact.Phones.Add(phone);

ContactStore store = await
    ContactManager.RequestStoreAsync(ContactStoreAccessType.AppContactsReadWrite);

ContactList contactList;

IReadOnlyList<ContactList> contactLists = await store.FindContactListsAsync();

if (0 == contactLists.Count)
    contactList = await store.CreateContactListAsync("TestContactList");
else
    contactList = contactLists[0];

await contactList.SaveContactAsync(contact);

```

## <a name="tag-each-contact-with-an-annotation"></a><span data-ttu-id="2eacb-119">Kennzeichnen von Kontakten mit einer Anmerkung</span><span class="sxs-lookup"><span data-stu-id="2eacb-119">Tag each contact with an annotation</span></span>

<span data-ttu-id="2eacb-120">Kennzeichnen Sie alle Kontakte mit einer Liste von Aktionen (Vorgänge), die Ihre App ausführen kann (Beispiel: Videoanrufe und Messaging).</span><span class="sxs-lookup"><span data-stu-id="2eacb-120">Tag each contact with a list of actions (operations) that your app can perform (for example: video calls and messaging).</span></span>

<span data-ttu-id="2eacb-121">Ordnen Sie anschließend die ID der Kontakte einer ID zu, anhand derer Ihre App den Benutzer intern identifizieren kann.</span><span class="sxs-lookup"><span data-stu-id="2eacb-121">Then, associate the ID of a contact to an ID that your app uses internally to identify that user.</span></span>

```cs
ContactAnnotationStore annotationStore = await
   ContactManager.RequestAnnotationStoreAsync(ContactAnnotationStoreAccessType.AppAnnotationsReadWrite);

ContactAnnotationList annotationList;

IReadOnlyList<ContactAnnotationList> annotationLists = await annotationStore.FindAnnotationListsAsync();
if (0 == annotationLists.Count)
    annotationList = await annotationStore.CreateAnnotationListAsync();
else
    annotationList = annotationLists[0];

ContactAnnotation annotation = new ContactAnnotation();
annotation.ContactId = contact.Id;
annotation.RemoteId = "user22";

annotation.SupportedOperations = ContactAnnotationOperations.Message |
  ContactAnnotationOperations.AudioCall |
  ContactAnnotationOperations.VideoCall |
 ContactAnnotationOperations.ContactProfile;

await annotationList.TrySaveAnnotationAsync(annotation);
```

## <a name="register-for-each-operation"></a><span data-ttu-id="2eacb-122">Registrieren der Vorgänge</span><span class="sxs-lookup"><span data-stu-id="2eacb-122">Register for each operation</span></span>

<span data-ttu-id="2eacb-123">Registrieren Sie in Ihrem Paketmanifest alle Vorgänge, die Sie in der Anmerkung aufgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="2eacb-123">In your package manifest, register for each operation that you listed in your annotation.</span></span>

<span data-ttu-id="2eacb-124">Registrieren Sie die Vorgänge, indem Sie dem ``Extensions``-Element des Manifests Protokollhandler hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2eacb-124">Register by adding protocol handlers to the ``Extensions`` element of the manifest.</span></span>

```xml
<Extensions>
  <uap:Extension Category="windows.protocol">
    <uap:Protocol Name="ms-contact-profile">
      <uap:DisplayName>TestProfileApp</uap:DisplayName>
    </uap:Protocol>
  </uap:Extension>
  <uap:Extension Category="windows.protocol">
    <uap:Protocol Name="ms-ipmessaging">
      <uap:DisplayName>TestMsgApp</uap:DisplayName>
    </uap:Protocol>
  </uap:Extension>
  <uap:Extension Category="windows.protocol">
    <uap:Protocol Name="ms-voip-video">
      <uap:DisplayName>TestVideoApp</uap:DisplayName>
    </uap:Protocol>
  </uap:Extension>
  <uap:Extension Category="windows.protocol">
    <uap:Protocol Name="ms-voip-call">
      <uap:DisplayName>TestCallApp</uap:DisplayName>
    </uap:Protocol>
  </uap:Extension>
</Extensions>
```
<span data-ttu-id="2eacb-125">Sie können diese auch in der Registerkarte **Deklarationen** im Manifest-Designer in Visual Studio hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2eacb-125">You can also add these in the **Declarations** tab of the manifest designer in Visual Studio.</span></span>

![Registerkarte „Deklarationen“ im Manifest-Designer](images/manifest-designer-protocols.png)

## <a name="find-your-app-next-to-actions-in-a-contact-card"></a><span data-ttu-id="2eacb-127">Anzeigen Ihrer App neben Aktionen in einer Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="2eacb-127">Find your app next to actions in a contact card</span></span>

<span data-ttu-id="2eacb-128">Öffnen Sie die Kontakte-App.</span><span class="sxs-lookup"><span data-stu-id="2eacb-128">Open the People app.</span></span> <span data-ttu-id="2eacb-129">Ihre App wird neben den Aktionen (Operationen) angezeigt, die Sie in Ihrer Anmerkung und dem Paketmanifest angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="2eacb-129">Your app appears next to each action (operation) that you specified in your annotation and package manifest.</span></span>

![Visitenkarte](images/a-contact-card.png)

<span data-ttu-id="2eacb-131">Wenn Benutzer Ihre App für eine Aktion auswählen, wird diese App, wenn ein Benutzer das nächste Mal eine Visitenkarte öffnet, als Standard-App für diese Aktion angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2eacb-131">If users choose your app for an action, it appears as the default app for that action the next time users open a contact card.</span></span>

## <a name="find-your-app-next-to-actions-in-a-mini-contact-card"></a><span data-ttu-id="2eacb-132">Anzeigen Ihrer App neben Aktionen in einer kleinen Kontaktkarte</span><span class="sxs-lookup"><span data-stu-id="2eacb-132">Find your app next to actions in a mini contact card</span></span>

<span data-ttu-id="2eacb-133">In kleinen Kontaktkarten wird Ihre App in Registerkarten angezeigt, die Aktionen darstellen.</span><span class="sxs-lookup"><span data-stu-id="2eacb-133">In mini contact cards, your app appears in tabs that represent actions.</span></span>

![Kleine Kontaktkarte](images/mini-contact-card.png)

<span data-ttu-id="2eacb-135">Apps wie **Mail** können kleine Kontaktkarten öffnen.</span><span class="sxs-lookup"><span data-stu-id="2eacb-135">Apps such as the **Mail** app open mini contact cards.</span></span> <span data-ttu-id="2eacb-136">Ihre App kann sie auch öffnen.</span><span class="sxs-lookup"><span data-stu-id="2eacb-136">Your app can open them too.</span></span> <span data-ttu-id="2eacb-137">Dieser Code zeigt, wie dies geht:</span><span class="sxs-lookup"><span data-stu-id="2eacb-137">This code shows you how to do that.</span></span>

```cs
public async void OpenContactCard(object sender, RoutedEventArgs e)
{
    // Get the selection rect of the button pressed to show contact card.
    FrameworkElement element = (FrameworkElement)sender;

    Windows.UI.Xaml.Media.GeneralTransform buttonTransform = element.TransformToVisual(null);
    Windows.Foundation.Point point = buttonTransform.TransformPoint(new Windows.Foundation.Point());
    Windows.Foundation.Rect rect =
        new Windows.Foundation.Rect(point, new Windows.Foundation.Size(element.ActualWidth, element.ActualHeight));

   // helper method to find a contact just for illustrative purposes.
    Contact contact = await findContact("contoso@contoso.com");

    ContactManager.ShowContactCard(contact, rect, Windows.UI.Popups.Placement.Default);

}
```

<span data-ttu-id="2eacb-138">Weitere Beispiele mit kleinen Kontaktkarten finden Sie unter [Visitenkartenbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ContactCards).</span><span class="sxs-lookup"><span data-stu-id="2eacb-138">To see more examples with mini contact cards, see [Contact cards sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ContactCards).</span></span>

<span data-ttu-id="2eacb-139">Genau wie die Visitenkarte wird für jede Registerkarte die App vermerkt, die der Benutzer zuletzt verwendet hat, damit sie problemlos zu Ihrer App zurückkehren können.</span><span class="sxs-lookup"><span data-stu-id="2eacb-139">Just like the contact card, each tab remembers the app that the user last used so it's easy for them to return to your app.</span></span>

## <a name="perform-operations-when-users-select-your-app-in-a-contact-card"></a><span data-ttu-id="2eacb-140">Ausführen von Vorgängen, wenn Benutzer Ihre App in einer Visitenkarte auswählen</span><span class="sxs-lookup"><span data-stu-id="2eacb-140">Perform operations when users select your app in a contact card</span></span>

<span data-ttu-id="2eacb-141">Überschreiben Sie die [Application.OnActivated](https://msdn.microsoft.com/library/windows/apps/br242330)-Methode in Ihrer **App.cs**-Datei, und leiten Sie Benutzer zu einer Seite in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="2eacb-141">Override the [Application.OnActivated](https://msdn.microsoft.com/library/windows/apps/br242330) method  in your **App.cs** file and navigate users to a page in your app.</span></span> <span data-ttu-id="2eacb-142">Das [Beispiel für die Integration von Visitenkarten](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ContactCardIntegration) zeigt eine Möglichkeit, das zu tun.</span><span class="sxs-lookup"><span data-stu-id="2eacb-142">The [Contact Card Integration Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ContactCardIntegration) shows one way to do that.</span></span>

<span data-ttu-id="2eacb-143">Überschreiben Sie in dem Code für die Datei der Seite, die [Page.OnNavigatedTo](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.onnavigatedto.aspx)-Methode.</span><span class="sxs-lookup"><span data-stu-id="2eacb-143">In the code behind file of the page, override the [Page.OnNavigatedTo](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.onnavigatedto.aspx) method.</span></span> <span data-ttu-id="2eacb-144">Die Visitenkarte übergibt dieser Methode den Namen des Vorgangs und die ID des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="2eacb-144">The contact card passes this method the name of operation and the ID of the user.</span></span>

<span data-ttu-id="2eacb-145">Informationen zum Starten eines Video- oder Audioanrufs finden Sie in dem [VoIP-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/VoIP).</span><span class="sxs-lookup"><span data-stu-id="2eacb-145">To start a video or audio call, see this sample: [VoIP sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/VoIP).</span></span> <span data-ttu-id="2eacb-146">Sie finden die vollständige API im Namespace [Windows.ApplicationModel.Calls](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.calls.aspx).</span><span class="sxs-lookup"><span data-stu-id="2eacb-146">You'll find the complete API in the [WIndows.ApplicationModel.Calls](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.calls.aspx) namespace.</span></span>

<span data-ttu-id="2eacb-147">Informationen zur Vereinfachung des Messaging finden Sie im Namespace [Windows.ApplicationModel.Chat](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.aspx).</span><span class="sxs-lookup"><span data-stu-id="2eacb-147">To facilitate messaging, see the [Windows.ApplicationModel.Chat](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.chat.aspx) namespace.</span></span>

<span data-ttu-id="2eacb-148">Sie können auch eine andere App starten.</span><span class="sxs-lookup"><span data-stu-id="2eacb-148">You can also start another app.</span></span> <span data-ttu-id="2eacb-149">Dieser Code führt folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="2eacb-149">That's what this code does.</span></span>

```cs
protected override async void OnNavigatedTo(NavigationEventArgs e)
{
    base.OnNavigatedTo(e);

    var args = e.Parameter as ProtocolActivatedEventArgs;
    // Display the result of the protocol activation if we got here as a result of being activated for a protocol.

    if (args != null)
    {
        var options = new Windows.System.LauncherOptions();
        options.DisplayApplicationPicker = true;

        options.TargetApplicationPackageFamilyName = “ContosoApp”;

        string launchString = args.uri.Scheme + ":" + args.uri.Query;
        var launchUri = new Uri(launchString);
        await Windows.System.Launcher.LaunchUriAsync(launchUri, options);
    }
}
```

<span data-ttu-id="2eacb-150">Die ```args.uri.scheme```-Eigenschaft enthält den Namen des Vorgangs, und die ```args.uri.Query```-Eigenschaft enthält die ID des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="2eacb-150">The ```args.uri.scheme``` property contains the name of the operation, and the ```args.uri.Query``` property contains the ID of the user.</span></span>
