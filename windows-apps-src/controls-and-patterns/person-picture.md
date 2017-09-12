---
author: mijacobs
description: 
title: Personenbild-Steuerelement
template: detail.hbs
label: Parallax View
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: kevjey
design-contact: kimsea
dev-contact: kefodero
doc-status: Published
ms.openlocfilehash: c71fdf3d19c8c8e43666620df53258825c4a8eb1
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="person-picture-control"></a>Personenbild-Steuerelement

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Das Personenbild-Steuerelement zeigt das Avatar-Bild für eine Person an, sofern ein solches Bild verfügbar ist. Andernfalls werden die Initialen der Person oder eine allgemeine Glyphe angezeigt. Sie können das Steuerelement zum Anzeigen eines [Contact-Objekts](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact)– eines Objekts, das die Kontaktinformationen einer Person verwaltet– verwenden, oder Sie können manuell Kontaktinformationen wie einen Anzeigenamen und ein Profilbild angeben.  

> **Wichtige APIs**: [PersonPicture-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.personpicture), [Contact-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact), [ContactManager-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.ContactManager)

![Das Personenbild-Steuerelement](images/person-picture/person-picture_hero.png)

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Verwenden Sie das Personenbild, wenn Sie eine Person und deren Kontaktinformationen darstellen möchten. Es folgen einige Beispiele für mögliche Verwendungszwecke dieses Steuerelements:
* Zur Anzeige des aktuellen Benutzers
* Zur Anzeige von Kontakten in einem Adressbuch
* Zur Anzeige des Absenders einer Nachricht 
* Zur Anzeige eines Social-Media-Kontakts

Die Abbildungzeigt das Personenbild-Steuerelement in einer Kontaktliste: ![das Personenbild-Steuerelement](images/person-picture/person-picture-control.png)

## <a name="how-to-use-the-person-picture-control"></a>Verwenden des Personenbild-Steuerelements

Zum Erstellen eines Personenbilds verwenden Sie die PersonPicture-Klasse. In diesem Beispiel wird ein PersonPicture-Steuerelement erstellt, und der Anzeigename, das Profilbild und die Initialen der Person werden manuell angegeben:

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

## <a name="using-the-person-picture-control-to-display-a-contact-object"></a>Verwenden des Personenbild-Steuerelements zum Anzeigen eines Contact-Objekts

Sie können das Personenauswahl-Steuerelement zum Anzeigen eines [Contact](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact)-Objekts verwenden: 

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
> Um den Code einfach zu halten, wird in diesem Beispiel ein neues Contact-Objekt erstellt. In einer echten App würden Sie dem Benutzer die Auswahl eines Kontakts überlassen, oder Sie würden einen [ContactManager](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.ContactManager) verwenden, um eine Liste der Kontakte abzufragen. Informationen zum Abrufen und Verwalten von Kontakten finden Sie in den [Artikeln zu Kontakten und Kalendern](../contacts-and-calendar/index.md). 

## <a name="determining-which-info-to-display"></a>Festlegen der anzuzeigenden Informationen

Wenn Sie ein [Contact](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Contacts.Contact)-Objekt angeben, wertet das Personenbild-Steuerelement dieses aus, um zu ermitteln, welche Informationen angezeigt werden können. 

Wenn ein Bild verfügbar ist, zeigt das Steuerelement in der folgenden Reihenfolge das erste Bild an, das es findet:

1.    LargeDisplayPicture
2.    SmallDisplayPicture
3.    Miniaturansicht

Sie können ändern, welches Bild ausgewählt wird, indem Sie die PreferSmallImage-Eigenschaft auf „true“ festlegen. Dadurch erhält das SmallDisplayPicture eine höhere Priorität als das LargeDisplayPicture.

Ist kein Bild vorhanden, zeigt das Steuerelement den Namen oder die Initialen des Kontakts an. Sind überhaupt keine Namensdaten vorhanden, zeigt das Steuerelement Kontaktdaten wie eine E-Mail-Adresse oder eine Telefonnummer an. 

## <a name="related-articles"></a>Verwandte Artikel

* [Kontakte und Kalender](../contacts-and-calendar/index.md)
* [Beispiel für Visitenkarten](http://go.microsoft.com/fwlink/p/?LinkId=624040)




