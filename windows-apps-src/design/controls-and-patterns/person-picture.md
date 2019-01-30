---
description: Zeigt das Avatar-Bild für eine Person an, sofern ein solches Bild verfügbar ist. Andernfalls werden die Initialen der Person oder eine allgemeine Glyphe angezeigt.
title: Personenbild-Steuerelement
template: detail.hbs
label: Parallax View
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: trestar
design-contact: kimsea
dev-contact: kefodero
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 1e03da83d4045c570490a26cb2e111d12f709ee0
ms.sourcegitcommit: a60ab85e9f2f9690e0141050ec3aa51f18ec61ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "9037152"
---
# <a name="person-picture-control"></a><span data-ttu-id="c50f8-104">Personenbild-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="c50f8-104">Person picture control</span></span>

<span data-ttu-id="c50f8-105">Das Personenbild-Steuerelement zeigt das Avatar-Bild für eine Person an, sofern ein solches Bild verfügbar ist. Andernfalls werden die Initialen der Person oder eine allgemeine Glyphe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c50f8-105">The person picture control displays the avatar image for a person, if one is available; if not, it displays the person's initials or a generic glyph.</span></span> <span data-ttu-id="c50f8-106">Sie können das Steuerelement zum Anzeigen eines [Contact-Objekts](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact)– eines Objekts, das die Kontaktinformationen einer Person verwaltet– verwenden, oder Sie können manuell Kontaktinformationen wie einen Anzeigenamen und ein Profilbild angeben.</span><span class="sxs-lookup"><span data-stu-id="c50f8-106">You can use the control to display a [Contact object](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact),  an object that manages a person's contact info, or you can manually provide contact information, such as a display name and profile picture.</span></span>  

> <span data-ttu-id="c50f8-107">**Wichtige APIs**: [PersonPicture-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.personpicture), [Contact-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact), [ContactManager-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.ContactManager)</span><span class="sxs-lookup"><span data-stu-id="c50f8-107">**Important APIs**: [PersonPicture class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.personpicture), [Contact class](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact), [ContactManager class](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.ContactManager)</span></span>

<span data-ttu-id="c50f8-108">Diese Abbildungzeigt zwei Steuerelement für Bilder von Personen zusammen mit zwei [TextBlock](text-block.md)-Elementen, die Namen der Benutzer anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c50f8-108">This illustration shows two person picture controls accompanied by two [text block](text-block.md) elements that display the users' names.</span></span> 
![Das Personenbild-Steuerelement](images/person-picture/person-picture_hero.png)


## <a name="is-this-the-right-control"></a><span data-ttu-id="c50f8-110">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="c50f8-110">Is this the right control?</span></span>

<span data-ttu-id="c50f8-111">Verwenden Sie das Personenbild, wenn Sie eine Person und deren Kontaktinformationen darstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="c50f8-111">Use the person picture when you want to represent a person and their contact information.</span></span> <span data-ttu-id="c50f8-112">Es folgen einige Beispiele für mögliche Verwendungszwecke dieses Steuerelements:</span><span class="sxs-lookup"><span data-stu-id="c50f8-112">Here are some examples of when you might use the control:</span></span>
* <span data-ttu-id="c50f8-113">Zur Anzeige des aktuellen Benutzers</span><span class="sxs-lookup"><span data-stu-id="c50f8-113">To display the current user</span></span>
* <span data-ttu-id="c50f8-114">Zur Anzeige von Kontakten in einem Adressbuch</span><span class="sxs-lookup"><span data-stu-id="c50f8-114">To display contacts in an address book</span></span>
* <span data-ttu-id="c50f8-115">Zur Anzeige des Absenders einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="c50f8-115">To display the sender of a message</span></span> 
* <span data-ttu-id="c50f8-116">Zur Anzeige eines Social-Media-Kontakts</span><span class="sxs-lookup"><span data-stu-id="c50f8-116">To display a social media contact</span></span>

<span data-ttu-id="c50f8-117">Die Abbildungzeigt das Personenbild-Steuerelement in einer Kontaktliste: ![das Personenbild-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="c50f8-117">The illustration shows person picture control in a list of contacts: ![The person picture control</span></span>](images/person-picture/person-picture-control.png)

## <a name="examples"></a><span data-ttu-id="c50f8-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c50f8-118">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="c50f8-119">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="c50f8-119">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="c50f8-120">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/PersonPicture">die App zu öffnen und PersonPicture in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="c50f8-120">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/PersonPicture">open the app and see the PersonPicture in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="c50f8-121">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="c50f8-121">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Xaml-Controls-Gallery"><span data-ttu-id="c50f8-122">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c50f8-122">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="how-to-use-the-person-picture-control"></a><span data-ttu-id="c50f8-123">Verwenden des Personenbild-Steuerelements</span><span class="sxs-lookup"><span data-stu-id="c50f8-123">How to use the person picture control</span></span>

<span data-ttu-id="c50f8-124">Zum Erstellen eines Personenbilds verwenden Sie die PersonPicture-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c50f8-124">To create a person picture, you use the PersonPicture class.</span></span> <span data-ttu-id="c50f8-125">In diesem Beispiel wird ein PersonPicture-Steuerelement erstellt, und der Anzeigename, das Profilbild und die Initialen der Person werden manuell angegeben:</span><span class="sxs-lookup"><span data-stu-id="c50f8-125">This example creates a PersonPicture control and manually provides the person's display name, profile picture, and initials:</span></span>

```xaml
<Page
    x:Class="App2.ExamplePage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:App2"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <StackPanel Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <PersonPicture
            DisplayName="Betsy Sherman"
            ProfilePicture="Assets\BetsyShermanProfile.png"
            Initials="BS" />
    </StackPanel>
</Page>
```

## <a name="using-the-person-picture-control-to-display-a-contact-object"></a><span data-ttu-id="c50f8-126">Verwenden des Personenbild-Steuerelements zum Anzeigen eines Contact-Objekts</span><span class="sxs-lookup"><span data-stu-id="c50f8-126">Using the person picture control to display a Contact object</span></span>

<span data-ttu-id="c50f8-127">Sie können das Personenauswahl-Steuerelement zum Anzeigen eines [Contact](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact)-Objekts verwenden:</span><span class="sxs-lookup"><span data-stu-id="c50f8-127">You can use the person picker control to display a [Contact](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact) object:</span></span> 

```xaml
<Page
    x:Class="SampleApp.PersonPictureContactExample"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:SampleApp"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <StackPanel Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <PersonPicture
            Contact="{x:Bind CurrentContact, Mode=OneWay}" />
            
        <Button Click="LoadContactButton_Click">Load contact</Button>
    </StackPanel>
</Page>
```

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Runtime.InteropServices.WindowsRuntime;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;
using Windows.ApplicationModel.Contacts;

namespace SampleApp
{
    public sealed partial class PersonPictureContactExample : Page, System.ComponentModel.INotifyPropertyChanged
    {
        public PersonPictureContactExample()
        {
            this.InitializeComponent();
        }

        private Windows.ApplicationModel.Contacts.Contact _currentContact; 
        public Windows.ApplicationModel.Contacts.Contact CurrentContact
        {
            get => _currentContact;
            set
            {
                _currentContact = value;
                PropertyChanged?.Invoke(this,
                    new System.ComponentModel.PropertyChangedEventArgs(nameof(CurrentContact)));
            }

        }
        public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;

        public static async System.Threading.Tasks.Task<Windows.ApplicationModel.Contacts.Contact> CreateContact()
        {

            var contact = new Windows.ApplicationModel.Contacts.Contact();
            contact.FirstName = "Betsy";
            contact.LastName = "Sherman";

            // Get the app folder where the images are stored.
            var appInstalledFolder = 
                Windows.ApplicationModel.Package.Current.InstalledLocation;
            var assets = await appInstalledFolder.GetFolderAsync("Assets");
            var imageFile = await assets.GetFileAsync("betsy.png");
            contact.SourceDisplayPicture = imageFile;

            return contact;
        }

        private async void LoadContactButton_Click(object sender, RoutedEventArgs e)
        {
            CurrentContact = await CreateContact();
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="c50f8-128">Um den Code einfach zu halten, wird in diesem Beispiel ein neues Contact-Objekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="c50f8-128">To keep the code simple, this example creates a new Contact object.</span></span> <span data-ttu-id="c50f8-129">In einer echten App würden Sie dem Benutzer die Auswahl eines Kontakts überlassen, oder Sie würden einen [ContactManager](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.ContactManager) verwenden, um eine Liste der Kontakte abzufragen.</span><span class="sxs-lookup"><span data-stu-id="c50f8-129">In a real app, you'd let the user select a contact or you'd use a [ContactManager](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.ContactManager) to query for a list of contacts.</span></span> <span data-ttu-id="c50f8-130">Informationen zum Abrufen und Verwalten von Kontakten finden Sie in den [Artikeln zu Kontakten und Kalendern](../../contacts-and-calendar/index.md).</span><span class="sxs-lookup"><span data-stu-id="c50f8-130">For info on retrieving and managing contacts, see the [Contacts and calendar articles](../../contacts-and-calendar/index.md).</span></span> 

## <a name="determining-which-info-to-display"></a><span data-ttu-id="c50f8-131">Festlegen der anzuzeigenden Informationen</span><span class="sxs-lookup"><span data-stu-id="c50f8-131">Determining which info to display</span></span>

<span data-ttu-id="c50f8-132">Wenn Sie ein [Contact](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact)-Objekt angeben, wertet das Personenbild-Steuerelement dieses aus, um zu ermitteln, welche Informationen angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="c50f8-132">When you provide a [Contact](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact) object, the person picture control evaluates it to determine which info it can display.</span></span> 

<span data-ttu-id="c50f8-133">Wenn ein Bild verfügbar ist, zeigt das Steuerelement in der folgenden Reihenfolge das erste Bild an, das es findet:</span><span class="sxs-lookup"><span data-stu-id="c50f8-133">If an image is available, the control displays the first image it finds, in this order:</span></span>

1. <span data-ttu-id="c50f8-134">LargeDisplayPicture</span><span class="sxs-lookup"><span data-stu-id="c50f8-134">LargeDisplayPicture</span></span>
1. <span data-ttu-id="c50f8-135">SmallDisplayPicture</span><span class="sxs-lookup"><span data-stu-id="c50f8-135">SmallDisplayPicture</span></span>
1. <span data-ttu-id="c50f8-136">Miniaturansicht</span><span class="sxs-lookup"><span data-stu-id="c50f8-136">Thumbnail</span></span>

<span data-ttu-id="c50f8-137">Sie können ändern, welches Bild ausgewählt wird, indem Sie die PreferSmallImage-Eigenschaft auf „true“ festlegen. Dadurch erhält das SmallDisplayPicture eine höhere Priorität als das LargeDisplayPicture.</span><span class="sxs-lookup"><span data-stu-id="c50f8-137">You can change which image is chosen by setting the PreferSmallImage property to true; this gives the SmallDisplayPicture a higher priority than LargeDisplayPicture.</span></span>

<span data-ttu-id="c50f8-138">Ist kein Bild vorhanden, zeigt das Steuerelement den Namen oder die Initialen des Kontakts an. Sind überhaupt keine Namensdaten vorhanden, zeigt das Steuerelement Kontaktdaten wie eine E-Mail-Adresse oder eine Telefonnummer an.</span><span class="sxs-lookup"><span data-stu-id="c50f8-138">If there isn't an image, the control displays the contact's name or initials; if there's isn't any name data, the control displays contact data, such as an email address or phone number.</span></span> 

## <a name="get-the-sample-code"></a><span data-ttu-id="c50f8-139">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="c50f8-139">Get the sample code</span></span>

- <span data-ttu-id="c50f8-140">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Xaml-Controls-Gallery) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c50f8-140">[XAML Controls Gallery sample](https://github.com/Microsoft/Xaml-Controls-Gallery) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="c50f8-141">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c50f8-141">Related articles</span></span>

* [<span data-ttu-id="c50f8-142">Kontakte und Kalender</span><span class="sxs-lookup"><span data-stu-id="c50f8-142">Contacts and calendar</span></span>](../../contacts-and-calendar/index.md)
* [<span data-ttu-id="c50f8-143">Beispiel für Visitenkarten</span><span class="sxs-lookup"><span data-stu-id="c50f8-143">Contact cards sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=624040)
