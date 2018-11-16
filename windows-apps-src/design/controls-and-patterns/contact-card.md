---
author: mijacobs
Description: A button gives the user a way to trigger an immediate action.
title: Visitenkarte
ms.author: mijacobs
ms.date: 03/07/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: kele
design-contact: tbd
dev-contact: tbd
doc-status: not-published
ms.localizationpriority: medium
ms.openlocfilehash: 7b20ac0692aef0e4809bb879747551e049a26df7
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6850256"
---
# <a name="contact-card"></a>Visitenkarte

Die Visitenkarte zeigt Kontaktinformationen wie Name, Telefonnummer und Adresse für einen [Kontakt](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact) (der Mechanismus, den UWP zum Darstellen von Personen und Unternehmen verwendet).  Die Visitenkarte ermöglicht dem Benutzer auch die Bearbeitung von Kontaktinformationen. Sie können eine kompakte Visitenkarte oder eine vollständige Visitenkarte anzeigen, die zusätzliche Informationen enthält.

> **Wichtige APIs**: [ShowContactCard-Methode](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_),   [ShowFullContactCard-Methode](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_ApplicationModel_Contacts_FullContactCardOptions_),  [IsShowContactCardSupported-Methode](/uwp/api/windows.applicationmodel.contacts.contactmanager.IsShowContactCardSupported),  [Contact-Klasse](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact)  

Es gibt zwei Möglichkeiten, die Visitenkarte anzuzeigen:  
* Als standardmäßige Visitenkarte, die in einem ausblendbaren Flyout angezeigt wird (die Visitenkarte wird ausgeblendet, wenn der Benutzer auf eine Stelle außerhalb der Visitenkarte klickt). 
* Als vollständige Visitenkarte, die der mehr Platz in Anspruch nimmt und nicht ausgeblendet werden kann (der Benutzer muss auf **Schließen** klicken, um sie zu schließen). 


<figure>
    <img src="images/contact-card/contact-card-standard.png" alt="The full contact card">
    <figcaption>Die standardmäßige Visitenkarte</figcaption>
</figure>

<figure>
    <img src="images/contact-card/contact-card-full.png" alt="The full contact card">
    <figcaption>Die vollständige Visitenkarte</figcaption>
</figure>


## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Verwenden Sie die Visitenkarte, wenn Kontaktinformationen zu einem Kontakt angezeigt werden sollen. Wenn Sie nur den Namen und das Bild des Kontakts anzeigen möchten, verwenden Sie die das [Personenbild-Steuerelement](person-picture.md). 


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

## <a name="show-a-standard-contact-card"></a>Anzeigen einer standardmäßigen Visitenkarte

1. Eine Visitenkarte wird in der Regel angezeigt, da der Benutzer auf ein Element geklickt hat: eine Schaltfläche oder vielleicht das [Personenbild-Steuerelement](person-picture.md). Wir möchten das Element nicht ausblenden. Um zu vermeiden, dass es ausgeblendet wird, müssen wir ein [Rect](/uwp/api/windows.foundation.rect) erstellen, das die Position und Größe des Elements beschreibt. 

    Wir erstellen eine Hilfsfunktion, die dies automatisch ausführt (diese wird später verwendet).
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

2. Ermitteln Sie, ob Sie die Visitenkarte anzeigen können, indem Sie die [ContactManager.IsShowContactCardSupported](/uwp/api/windows.applicationmodel.contacts.contactmanager.IsShowContactCardSupported)-Methode aufrufen. Wenn sie nicht unterstützt wird, wird eine Fehlermeldung angezeigt. (In diesem Beispiel wird davon ausgegangen, dass Sie die Visitenkarte als Reaktion auf ein Click-Ereignis anzeigen.)
    ```csharp
    // Contact and Contact Managers are existing classes 
    private void OnUserClickShowContactCard(object sender, RoutedEventArgs e) 
    { 
        if (ContactManager.IsShowContactCardSupported()) 
        { 

    ```

3. Verwenden Sie die in Schritt1 erstellte Hilfsfunktion, um die Grenzen des Steuerelements abzurufen, von dem das Ereignis ausgelöst wurde (damit es nicht von der Visitenkarte verdeckt wird).

    ```csharp
            Rect selectionRect = GetElementRect((FrameworkElement)sender); 
    ```

4. Rufen Sie das [Kontakt](//docs.microsoft.com/uwp/api/Windows.ApplicationModel.Contacts.Contact)-Objekt auf, das angezeigt werden soll. In diesem Beispiel wird lediglich ein einfacher Kontakt erstellt, Ihr Code sollte jedoch einen tatsächlichen Kontakt abrufen. 

    ```csharp
                // Retrieve the contact to display
                var contact = new Contact(); 
                var email = new ContactEmail(); 
                email.Address = "jsmith@contoso.com"; 
                contact.Emails.Add(email); 
    ```
5. Zeigen Sie die Visitenkarte durch Aufrufen der [ShowContactCard](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_)-Methode an. 

    ```csharp
            ContactManager.ShowFullContactCard(
                contact, selectionRect, Placement.Default); 
        } 
    } 
    ```

Hier sehen sie den vollständigen Beispielcode:

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

## <a name="show-a-full-contact-card"></a>Anzeigen einer vollständigen Visitenkarte

Rufen Sie zum Anzeigen der vollständigen Visitenkarte die [ShowFullContactCard](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_ApplicationModel_Contacts_FullContactCardOptions_)-Methode anstelle der [ShowContactCard ](/uwp/api/windows.applicationmodel.contacts.contactmanager#Windows_ApplicationModel_Contacts_ContactManager_ShowFullContactCard_Windows_ApplicationModel_Contacts_Contact_Windows_Foundation_Rect_)-Methode auf.

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

## <a name="retrieving-real-contacts"></a>Abrufen von „echten“ Kontakten

Die Beispiele in diesem Artikel zeigen die Erstellung eines einfachen Kontakts. In einer echten App würden Sie wahrscheinlich einen vorhandenen Kontakt abrufen. Anweisungen finden Sie in den [Artikeln zu Kontakten und Kalendern](/windows/uwp/contacts-and-calendar/).




## <a name="related-articles"></a>Verwandte Artikel
- [Kontakte und Kalender](/windows/uwp/contacts-and-calendar/)
- [Beispiel für Visitenkarten](http://go.microsoft.com/fwlink/p/?LinkId=624040)
- [Personenbild-Steuerelement](/windows/uwp/controls-and-patterns/person-picture/)
