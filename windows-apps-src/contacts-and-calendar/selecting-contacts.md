---
author: normesta
description: Mit dem Windows.ApplicationModel.Contacts-Namespace verfügen Sie über mehrere Optionen zum Auswählen von Kontakten.
title: Auswählen von Kontakten
ms.assetid: 35FEDEE6-2B0E-4391-84BA-5E9191D4E442
keywords: Kontakte, auswählen, einzelnen Kontakt auswählen, mehrere Kontakte auswählen, Kontakte, mehrere auswählen; bestimmten Kontakt auswählen, Kontaktdaten, bestimmte auswählen, Kontaktdaten, bestimmte Felder auswählen
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a721e618864155e4eec66d222e8eeafa2e0ca038
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5557041"
---
# <a name="select-contacts"></a><span data-ttu-id="4173a-104">Auswählen von Kontakten</span><span class="sxs-lookup"><span data-stu-id="4173a-104">Select contacts</span></span>



<span data-ttu-id="4173a-105">Mit dem [**Windows.ApplicationModel.Contacts**](https://msdn.microsoft.com/library/windows/apps/BR225002)-Namespace verfügen Sie über mehrere Optionen zum Auswählen von Kontakten.</span><span class="sxs-lookup"><span data-stu-id="4173a-105">Through the [**Windows.ApplicationModel.Contacts**](https://msdn.microsoft.com/library/windows/apps/BR225002) namespace, you have several options for selecting contacts.</span></span> <span data-ttu-id="4173a-106">Wir zeigen Ihnen hier, wie Sie einen einzelnen Kontakt oder mehrere Kontakte auswählen und wie Sie die Kontaktauswahl so konfigurieren, dass nur die von der App benötigten Kontaktinformationen abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="4173a-106">Here, we'll show you how to select a single contact or multiple contacts, and we'll show you how to configure the contact picker to retrieve only the contact information that your app needs.</span></span>

## <a name="set-up-the-contact-picker"></a><span data-ttu-id="4173a-107">Einrichten der Kontaktauswahl</span><span class="sxs-lookup"><span data-stu-id="4173a-107">Set up the contact picker</span></span>

<span data-ttu-id="4173a-108">Erstellen Sie eine Instanz von [**Windows.ApplicationModel.Contacts.ContactPicker**](https://msdn.microsoft.com/library/windows/apps/BR224913), und weisen Sie sie einer Variablen zu.</span><span class="sxs-lookup"><span data-stu-id="4173a-108">Create an instance of [**Windows.ApplicationModel.Contacts.ContactPicker**](https://msdn.microsoft.com/library/windows/apps/BR224913) and assign it to a variable.</span></span>

```cs
var contactPicker = new Windows.ApplicationModel.Contacts.ContactPicker();
```

## <a name="set-the-selection-mode-optional"></a><span data-ttu-id="4173a-109">Festlegen des Auswahlmodus (optional)</span><span class="sxs-lookup"><span data-stu-id="4173a-109">Set the selection mode (optional)</span></span>

<span data-ttu-id="4173a-110">Standardmäßig ruft die Kontaktauswahl alle verfügbaren Daten für die von Benutzern ausgewählten Kontakte ab.</span><span class="sxs-lookup"><span data-stu-id="4173a-110">By default, the contact picker retrieves all of the available data for the contacts that the user selects.</span></span> <span data-ttu-id="4173a-111">Mithilfe der [**SelectionMode**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.contacts.contactpicker.selectionmode)-Eigenschaft können Sie die Kontaktauswahl so konfigurieren, dass nur die von der App benötigten Datenfelder abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="4173a-111">The [**SelectionMode**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.contacts.contactpicker.selectionmode) property lets you configure the contact picker to retrieve only the data fields that your app needs.</span></span> <span data-ttu-id="4173a-112">Diese effiziente Verwendungsweise der Kontaktauswahl eignet sich besonders dann, wenn Sie nur einen Teil der verfügbaren Kontaktdaten benötigen.</span><span class="sxs-lookup"><span data-stu-id="4173a-112">This is a more efficient way to use the contact picker if you only need a subset of the available contact data.</span></span>

<span data-ttu-id="4173a-113">Legen Sie zunächst die [**SelectionMode**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.contacts.contactpicker.selectionmode)-Eigenschaft auf **Fields** fest.</span><span class="sxs-lookup"><span data-stu-id="4173a-113">First, set the [**SelectionMode**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.contacts.contactpicker.selectionmode) property to **Fields**:</span></span>

```cs
contactPicker.SelectionMode = Windows.ApplicationModel.Contacts.ContactSelectionMode.Fields;
```

<span data-ttu-id="4173a-114">Geben Sie dann mithilfe der [**DesiredFieldsWithContactFieldType**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.contacts.contactpicker.desiredfieldswithcontactfieldtype)-Eigenschaft die Felder an, die von der Kontaktauswahl abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="4173a-114">Then, use the [**DesiredFieldsWithContactFieldType**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.contacts.contactpicker.desiredfieldswithcontactfieldtype) property to specify the fields that you want the contact picker to retrieve.</span></span> <span data-ttu-id="4173a-115">In diesem Beispiel wird die Kontaktauswahl so konfiguriert, dass E-Mail-Adressen abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="4173a-115">This example configures the contact picker to retrieve email addresses:</span></span>

``` cs
contactPicker.DesiredFieldsWithContactFieldType.Add(Windows.ApplicationModel.Contacts.ContactFieldType.Email);
```

## <a name="launch-the-picker"></a><span data-ttu-id="4173a-116">Starten der Auswahl</span><span class="sxs-lookup"><span data-stu-id="4173a-116">Launch the picker</span></span>

```cs
Contact contact = await contactPicker.PickContactAsync();
```

<span data-ttu-id="4173a-117">Verwenden Sie [**PickContactsAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.contacts.contactpicker.pickcontactsasync), wenn der Benutzer mindestens einen Kontakt auswählen soll.</span><span class="sxs-lookup"><span data-stu-id="4173a-117">Use [**PickContactsAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.contacts.contactpicker.pickcontactsasync) if you want the user to select one or more contacts.</span></span>

```cs
public IList<Contact> contacts;
contacts = await contactPicker.PickContactsAsync();
```

## <a name="process-the-contacts"></a><span data-ttu-id="4173a-118">Verarbeiten der Kontakte</span><span class="sxs-lookup"><span data-stu-id="4173a-118">Process the contacts</span></span>

<span data-ttu-id="4173a-119">Überprüfen Sie in der Auswahl, ob der Benutzer Kontakte ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="4173a-119">When the picker returns, check whether the user has selected any contacts.</span></span> <span data-ttu-id="4173a-120">Wenn ja, verarbeiten Sie die Kontaktinformationen.</span><span class="sxs-lookup"><span data-stu-id="4173a-120">If so, process the contact information.</span></span>

<span data-ttu-id="4173a-121">Dieses Beispiel zeigt, wie ein einzelner Kontakt verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="4173a-121">This example shows how to processes a single contact.</span></span> <span data-ttu-id="4173a-122">Hier wird der Name des Kontakts abgerufen und in ein [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Steuerelement namens *OutputName* kopiert.</span><span class="sxs-lookup"><span data-stu-id="4173a-122">Here we retrieve the contact's name and copy it into a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) control called *OutputName*.</span></span>

```cs
if (contact != null)
{
    OutputName.Text = contact.DisplayName;
}
else
{
    rootPage.NotifyUser("No contact was selected.", NotifyType.ErrorMessage);
}
```

<span data-ttu-id="4173a-123">Dieses Beispiel zeigt die Verarbeitung mehrerer Kontakte.</span><span class="sxs-lookup"><span data-stu-id="4173a-123">This example shows how to process multiple contacts.</span></span>

```cs
if (contacts != null && contacts.Count > 0)
{
    foreach (Contact contact in contacts)
    {
        // Do something with the contact information.
    }
}
```

## <a name="complete-example-single-contact"></a><span data-ttu-id="4173a-124">Vollständiges Beispiel (einzelner Kontakt)</span><span class="sxs-lookup"><span data-stu-id="4173a-124">Complete example (single contact)</span></span>

<span data-ttu-id="4173a-125">In diesem Beispiel werden mithilfe der Kontaktauswahl der Name sowie E-Mail-Adresse, Standort oder Telefonnummer eines einzelnen Kontakts abgerufen.</span><span class="sxs-lookup"><span data-stu-id="4173a-125">This example uses the contact picker to retrieve a single contact's name along with an email address, location or phone number.</span></span>

```cs
// ...
using Windows.ApplicationModel.Contacts;
// ...

private async void PickAContactButton-Click(object sender, RoutedEventArgs e)
{
    ContactPicker contactPicker = new ContactPicker();

    contactPicker.DesiredFieldsWithContactFieldType.Add(ContactFieldType.Email);
    contactPicker.DesiredFieldsWithContactFieldType.Add(ContactFieldType.Address);
    contactPicker.DesiredFieldsWithContactFieldType.Add(ContactFieldType.PhoneNumber);

    Contact contact = await contactPicker.PickContactAsync();

    if (contact != null)
    {
        OutputFields.Visibility = Visibility.Visible;
        OutputEmpty.Visibility = Visibility.Collapsed;

        OutputName.Text = contact.DisplayName;

        AppendContactFieldValues(OutputEmails, contact.Emails);
        AppendContactFieldValues(OutputPhoneNumbers, contact.Phones);
        AppendContactFieldValues(OutputAddresses, contact.Addresses);
    }
    else
    {
        OutputEmpty.Visibility = Visibility.Visible;
        OutputFields.Visibility = Visibility.Collapsed;
    }
}

private void AppendContactFieldValues<T>(TextBlock content, IList<T> fields)
{
    if (fields.Count > 0)
    {
        StringBuilder output = new StringBuilder();

        if (fields[0].GetType() == typeof(ContactEmail))
        {
            foreach (ContactEmail email in fields as IList<ContactEmail>)
            {
                output.AppendFormat("Email: {0} ({1})\n", email.Address, email.Kind);
            }
        }
        else if (fields[0].GetType() == typeof(ContactPhone))
        {
            foreach (ContactPhone phone in fields as IList<ContactPhone>)
            {
                output.AppendFormat("Phone: {0} ({1})\n", phone.Number, phone.Kind);
            }
        }
        else if (fields[0].GetType() == typeof(ContactAddress))
        {
            List<String> addressParts = null;
            string unstructuredAddress = "";

            foreach (ContactAddress address in fields as IList<ContactAddress>)
            {
                addressParts = (new List<string> { address.StreetAddress, address.Locality, address.Region, address.PostalCode });
                unstructuredAddress = string.Join(", ", addressParts.FindAll(s => !string.IsNullOrEmpty(s)));
                output.AppendFormat("Address: {0} ({1})\n", unstructuredAddress, address.Kind);
            }
        }

        content.Visibility = Visibility.Visible;
        content.Text = output.ToString();
    }
    else
    {
        content.Visibility = Visibility.Collapsed;
    }
}
```

## <a name="complete-example-multiple-contacts"></a><span data-ttu-id="4173a-126">Vollständiges Beispiel (mehrere Kontakte)</span><span class="sxs-lookup"><span data-stu-id="4173a-126">Complete example (multiple contacts)</span></span>

<span data-ttu-id="4173a-127">In diesem Beispiel werden mithilfe der Kontaktauswahl mehrere Kontakte abgerufen und einem [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)-Steuerelement namens `OutputContacts` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4173a-127">This example uses the contact picker to retrieve multiple contacts and then adds the contacts to a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) control called `OutputContacts`.</span></span>

```cs
MainPage rootPage = MainPage.Current;
public IList<Contact> contacts;

private async void PickContactsButton-Click(object sender, RoutedEventArgs e)
{
    var contactPicker = new Windows.ApplicationModel.Contacts.ContactPicker();
    contactPicker.CommitButtonText = "Select";
    contacts = await contactPicker.PickContactsAsync();

    // Clear the ListView.
    OutputContacts.Items.Clear();

    if (contacts != null && contacts.Count > 0)
    {
        OutputContacts.Visibility = Windows.UI.Xaml.Visibility.Visible;
        OutputEmpty.Visibility = Visibility.Collapsed;

        foreach (Contact contact in contacts)
        {
            // Add the contacts to the ListView.
            OutputContacts.Items.Add(new ContactItemAdapter(contact));
        }
    }
    else
    {
        OutputEmpty.Visibility = Visibility.Visible;
    }         
}
```

``` cs
public class ContactItemAdapter
{
    public string Name { get; private set; }
    public string SecondaryText { get; private set; }

    public ContactItemAdapter(Contact contact)
    {
        Name = contact.DisplayName;
        if (contact.Emails.Count > 0)
        {
            SecondaryText = contact.Emails[0].Address;
        }
        else if (contact.Phones.Count > 0)
        {
            SecondaryText = contact.Phones[0].Number;
        }
        else if (contact.Addresses.Count > 0)
        {
            List<string> addressParts = (new List<string> { contact.Addresses[0].StreetAddress,
              contact.Addresses[0].Locality, contact.Addresses[0].Region, contact.Addresses[0].PostalCode });
              string unstructuredAddress = string.Join(", ", addressParts.FindAll(s => !string.IsNullOrEmpty(s)));
            SecondaryText = unstructuredAddress;
        }
    }
}
```

## <a name="summary-and-next-steps"></a><span data-ttu-id="4173a-128">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="4173a-128">Summary and next steps</span></span>

<span data-ttu-id="4173a-129">Sie verfügen nun über grundlegende Kenntnisse zum Abrufen von Kontaktinformationen mithilfe der Kontaktauswahl.</span><span class="sxs-lookup"><span data-stu-id="4173a-129">Now you have a basic understanding of how to use the contact picker to retrieve contact information.</span></span> <span data-ttu-id="4173a-130">Laden Sie die [Beispiele für universelle Windows-Apps](http://go.microsoft.com/fwlink/p/?linkid=619979) von GitHub herunter, um sich weitere Beispiele für die Verwendung von Kontakten und Kontaktauswahl anzusehen.</span><span class="sxs-lookup"><span data-stu-id="4173a-130">Download the [Universal Windows app samples](http://go.microsoft.com/fwlink/p/?linkid=619979) from GitHub to see more examples of how to use contacts and the contact picker.</span></span>
