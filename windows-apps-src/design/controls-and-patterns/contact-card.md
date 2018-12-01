---
Description: A button gives the user a way to trigger an immediate action.
title: Visitenkarte
ms.date: 03/07/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: kele
design-contact: tbd
dev-contact: tbd
doc-status: not-published
ms.localizationpriority: medium
ms.openlocfilehash: b04a8f616e9f6c7726a222f4a7264b9580ddee3a
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8335723"
---
# <a name="contact-card"></a><span data-ttu-id="51bb1-103">Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="51bb1-103">Contact card</span></span>

<span data-ttu-id="51bb1-104">Die Visitenkarte zeigt Kontaktinformationen wie Name, Telefonnummer und Adresse für einen [Kontakt](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact) (der Mechanismus, den UWP zum Darstellen von Personen und Unternehmen verwendet).</span><span class="sxs-lookup"><span data-stu-id="51bb1-104">The contact card displays contact information, such as the name, phone number, and address, for a [Contact](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact) (the mechanism UWP uses to represent people and businesses).</span></span>  <span data-ttu-id="51bb1-105">Die Visitenkarte ermöglicht dem Benutzer auch die Bearbeitung von Kontaktinformationen.</span><span class="sxs-lookup"><span data-stu-id="51bb1-105">The contact card also lets the user edit contact info.</span></span> <span data-ttu-id="51bb1-106">Sie können eine kompakte Visitenkarte oder eine vollständige Visitenkarte anzeigen, die zusätzliche Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="51bb1-106">You can choose to display a compact contact card, or a full contact card that contains additional information.</span></span>

> <span data-ttu-id="51bb1-107">**Wichtige APIs**: [ShowContactCard-Methode](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_),   [ShowFullContactCard-Methode](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_ApplicationModel_Contacts_FullContactCardOptions_),  [IsShowContactCardSupported-Methode](/uwp/api/windows.applicationmodel.contacts.contactmanager.IsShowContactCardSupported),  [Contact-Klasse](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact)</span><span class="sxs-lookup"><span data-stu-id="51bb1-107">**Important APIs**: [ShowContactCard method](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_),   [ShowFullContactCard method](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_ApplicationModel_Contacts_FullContactCardOptions_),  [IsShowContactCardSupported method](/uwp/api/windows.applicationmodel.contacts.contactmanager.IsShowContactCardSupported),  [Contact class](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact)</span></span>  

<span data-ttu-id="51bb1-108">Es gibt zwei Möglichkeiten, die Visitenkarte anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="51bb1-108">There are two ways to display the contact card:</span></span>  
* <span data-ttu-id="51bb1-109">Als standardmäßige Visitenkarte, die in einem ausblendbaren Flyout angezeigt wird (die Visitenkarte wird ausgeblendet, wenn der Benutzer auf eine Stelle außerhalb der Visitenkarte klickt).</span><span class="sxs-lookup"><span data-stu-id="51bb1-109">As a standard contact card that appears in a flyout that is light-dismissable--the contact card dissapears when the user clicks outside of it.</span></span> 
* <span data-ttu-id="51bb1-110">Als vollständige Visitenkarte, die der mehr Platz in Anspruch nimmt und nicht ausgeblendet werden kann (der Benutzer muss auf **Schließen** klicken, um sie zu schließen).</span><span class="sxs-lookup"><span data-stu-id="51bb1-110">As a full contact card that takes up more space and is not light-dismissable--the user must click **close** to close it.</span></span> 


<figure>
    <img src="images/contact-card/contact-card-standard.png" alt="The full contact card">
    <figcaption><span data-ttu-id="51bb1-111">Die standardmäßige Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="51bb1-111">The standard contact card</span></span></figcaption>
</figure>

<figure>
    <img src="images/contact-card/contact-card-full.png" alt="The full contact card">
    <figcaption><span data-ttu-id="51bb1-112">Die vollständige Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="51bb1-112">The full contact card</span></span></figcaption>
</figure>


## <a name="is-this-the-right-control"></a><span data-ttu-id="51bb1-113">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="51bb1-113">Is this the right control?</span></span>

<span data-ttu-id="51bb1-114">Verwenden Sie die Visitenkarte, wenn Kontaktinformationen zu einem Kontakt angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="51bb1-114">Use the contact card when you want to display contact info for a contact.</span></span> <span data-ttu-id="51bb1-115">Wenn Sie nur den Namen und das Bild des Kontakts anzeigen möchten, verwenden Sie die das [Personenbild-Steuerelement](person-picture.md).</span><span class="sxs-lookup"><span data-stu-id="51bb1-115">If you only want to display the contact's name and picture, use the [person picture control](person-picture.md).</span></span> 


<!-- TODO: Add examples back when the contact card has been added. -->

<!-- ## Examples

<table>
<th align="left">XAML Controls Gallery<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Button">open the app and see the Button in action</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a></li>
    </ul>
</td>
</tr>
</table> -->

## <a name="show-a-standard-contact-card"></a><span data-ttu-id="51bb1-116">Anzeigen einer standardmäßigen Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="51bb1-116">Show a standard contact card</span></span>

1. <span data-ttu-id="51bb1-117">Eine Visitenkarte wird in der Regel angezeigt, da der Benutzer auf ein Element geklickt hat: eine Schaltfläche oder vielleicht das [Personenbild-Steuerelement](person-picture.md).</span><span class="sxs-lookup"><span data-stu-id="51bb1-117">Typically, you show a contact card because the user clicked something: a button or perhaps the [person picture control](person-picture.md).</span></span> <span data-ttu-id="51bb1-118">Wir möchten das Element nicht ausblenden.</span><span class="sxs-lookup"><span data-stu-id="51bb1-118">We don't want to hide the element.</span></span> <span data-ttu-id="51bb1-119">Um zu vermeiden, dass es ausgeblendet wird, müssen wir ein [Rect](/uwp/api/windows.foundation.rect) erstellen, das die Position und Größe des Elements beschreibt.</span><span class="sxs-lookup"><span data-stu-id="51bb1-119">To avoid hiding it, we need to create a [Rect](/uwp/api/windows.foundation.rect) that describes the location and size of the element.</span></span> 

    <span data-ttu-id="51bb1-120">Wir erstellen eine Hilfsfunktion, die dies automatisch ausführt (diese wird später verwendet).</span><span class="sxs-lookup"><span data-stu-id="51bb1-120">Let's create a utility function that does that for us--we'll use it later.</span></span>
    ```csharp
    // Gets the rectangle of the element 
    public static Rect GetElementRectHelper(FrameworkElement element) 
    { 
        // Passing "null" means set to root element. 
        GeneralTransform elementTransform = element.TransformToVisual(null); 
        Rect rect = elementTransform.TransformBounds(new Rect(0, 0, element.ActualWidth, element.ActualHeight)); 
        return rect; 
    } 

    ```

2. <span data-ttu-id="51bb1-121">Ermitteln Sie, ob Sie die Visitenkarte anzeigen können, indem Sie die [ContactManager.IsShowContactCardSupported](/uwp/api/windows.applicationmodel.contacts.contactmanager.IsShowContactCardSupported)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="51bb1-121">Determine whether you can display the contact card by calling the [ContactManager.IsShowContactCardSupported](/uwp/api/windows.applicationmodel.contacts.contactmanager.IsShowContactCardSupported) method.</span></span> <span data-ttu-id="51bb1-122">Wenn sie nicht unterstützt wird, wird eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="51bb1-122">If it's not supported, display an error message.</span></span> <span data-ttu-id="51bb1-123">(In diesem Beispiel wird davon ausgegangen, dass Sie die Visitenkarte als Reaktion auf ein Click-Ereignis anzeigen.)</span><span class="sxs-lookup"><span data-stu-id="51bb1-123">(This example assumes that you'll be showing the contact card in response to a click event .)</span></span>
    ```csharp
    // Contact and Contact Managers are existing classes 
    private void OnUserClickShowContactCard(object sender, RoutedEventArgs e) 
    { 
        if (ContactManager.IsShowContactCardSupported()) 
        { 

    ```

3. <span data-ttu-id="51bb1-124">Verwenden Sie die in Schritt1 erstellte Hilfsfunktion, um die Grenzen des Steuerelements abzurufen, von dem das Ereignis ausgelöst wurde (damit es nicht von der Visitenkarte verdeckt wird).</span><span class="sxs-lookup"><span data-stu-id="51bb1-124">Use the utility function you created in step 1 to get the bounds of the control that fired the event (so we don't cover it up with the contact card).</span></span>

    ```csharp
            Rect selectionRect = GetElementRect((FrameworkElement)sender); 
    ```

4. <span data-ttu-id="51bb1-125">Rufen Sie das [Kontakt](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact)-Objekt auf, das angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="51bb1-125">Get the [Contact](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact) object you want to display.</span></span> <span data-ttu-id="51bb1-126">In diesem Beispiel wird lediglich ein einfacher Kontakt erstellt, Ihr Code sollte jedoch einen tatsächlichen Kontakt abrufen.</span><span class="sxs-lookup"><span data-stu-id="51bb1-126">This example just creates a simple contact, but your code should retrieve an actual contact.</span></span> 

    ```csharp
                // Retrieve the contact to display
                var contact = new Contact(); 
                var email = new ContactEmail(); 
                email.Address = "jsmith@contoso.com"; 
                contact.Emails.Add(email); 
    ```
5. <span data-ttu-id="51bb1-127">Zeigen Sie die Visitenkarte durch Aufrufen der [ShowContactCard](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_)-Methode an.</span><span class="sxs-lookup"><span data-stu-id="51bb1-127">Show the contact card by calling the  [ShowContactCard](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_) method.</span></span> 

    ```csharp
            ContactManager.ShowFullContactCard(
                contact, selectionRect, Placement.Default); 
        } 
    } 
    ```

<span data-ttu-id="51bb1-128">Hier sehen sie den vollständigen Beispielcode:</span><span class="sxs-lookup"><span data-stu-id="51bb1-128">Here's the complete code example:</span></span>

```csharp
// Gets the rectangle of the element 
public static Rect GetElementRect(FrameworkElement element) 
{ 
    // Passing "null" means set to root element. 
    GeneralTransform elementTransform = element.TransformToVisual(null); 
    Rect rect = elementTransform.TransformBounds(new Rect(0, 0, element.ActualWidth, element.ActualHeight)); 
    return rect; 
} 
 
// Display a contact in response to an event
private void OnUserClickShowContactCard(object sender, RoutedEventArgs e) 
{ 
    if (ContactManager.IsShowContactCardSupported()) 
    { 
        Rect selectionRect = GetElementRect((FrameworkElement)sender);

        // Retrieve the contact to display
        var contact = new Contact(); 
        var email = new ContactEmail(); 
        email.Address = "jsmith@contoso.com"; 
        contact.Emails.Add(email); 
    
        ContactManager.ShowContactCard(
            contact, selectionRect, Placement.Default); 
    } 
} 

```

## <a name="show-a-full-contact-card"></a><span data-ttu-id="51bb1-129">Anzeigen einer vollständigen Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="51bb1-129">Show a full contact card</span></span>

<span data-ttu-id="51bb1-130">Rufen Sie zum Anzeigen der vollständigen Visitenkarte die [ShowFullContactCard](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_ApplicationModel_Contacts_FullContactCardOptions_)-Methode anstelle der [ShowContactCard ](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="51bb1-130">To show the full contact card, call the [ShowFullContactCard](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_ApplicationModel_Contacts_FullContactCardOptions_) method instead of [ShowContactCard](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_).</span></span>

```csharp
private void onUserClickShowContactCard() 
{ 
   
    Contact contact = new Contact(); 
    ContactEmail email = new ContactEmail(); 
    email.Address = "jsmith@hotmail.com"; 
    contact.Emails.Add(email); 
 
 
    // Setting up contact options.     
    FullContactCardOptions fullContactCardOptions = new FullContactCardOptions(); 
 
    // Display full contact card on mouse click.   
    // Launch the People’s App with full contact card  
    fullContactCardOptions.DesiredRemainingView = ViewSizePreference.UseLess; 
     
 
    // Shows the full contact card by launching the People App. 
    ContactManager.ShowFullContactCard(contact, fullContactCardOptions); 
} 

```

## <a name="retrieving-real-contacts"></a><span data-ttu-id="51bb1-131">Abrufen von „echten“ Kontakten</span><span class="sxs-lookup"><span data-stu-id="51bb1-131">Retrieving "real" contacts</span></span>

<span data-ttu-id="51bb1-132">Die Beispiele in diesem Artikel zeigen die Erstellung eines einfachen Kontakts.</span><span class="sxs-lookup"><span data-stu-id="51bb1-132">The examples in this article create a simple contact.</span></span> <span data-ttu-id="51bb1-133">In einer echten App würden Sie wahrscheinlich einen vorhandenen Kontakt abrufen.</span><span class="sxs-lookup"><span data-stu-id="51bb1-133">In a real app, you'd probably want to retrieve an existing contact.</span></span> <span data-ttu-id="51bb1-134">Anweisungen finden Sie in den [Artikeln zu Kontakten und Kalendern](/windows/uwp/contacts-and-calendar/).</span><span class="sxs-lookup"><span data-stu-id="51bb1-134">For instructions, see the [Contacts and calendar article](/windows/uwp/contacts-and-calendar/).</span></span>




## <a name="related-articles"></a><span data-ttu-id="51bb1-135">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="51bb1-135">Related articles</span></span>
- [<span data-ttu-id="51bb1-136">Kontakte und Kalender</span><span class="sxs-lookup"><span data-stu-id="51bb1-136">Contacts and calendar</span></span>](/windows/uwp/contacts-and-calendar/)
- [<span data-ttu-id="51bb1-137">Beispiel für Visitenkarten</span><span class="sxs-lookup"><span data-stu-id="51bb1-137">Contact cards sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=624040)
- [<span data-ttu-id="51bb1-138">Personenbild-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="51bb1-138">People picture control</span></span>](/windows/uwp/controls-and-patterns/person-picture/)
