---
title: Installieren einer verwandten Gruppe mithilfe einer App-Installer-Datei
description: In diesem Abschnitt überprüfen wir die erforderlichen Schritte, damit die Installation von verwandten Gruppen über den App-Installer möglich ist. Wir durchlaufen ebenfalls die notwendigen Schritte zum Erstellen einer *.appinstaller-Datei, die Ihre verwandten Gruppen definieren.
ms.date: 1/4/2018
ms.topic: article
keywords: Windows10, UWP, App-Installer, AppInstaller, querladen, verwandte Gruppe, optionale Pakete
ms.localizationpriority: medium
ms.openlocfilehash: c90fffeee7003159f58cf2e108286f4fe7732fd6
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7839245"
---
# <a name="install-a-related-set-using-an-app-installer-file"></a>Installieren einer verwandten Gruppe mithilfe einer App-Installer-Datei

Wenn Sie am Anfang der Entwicklung mit optionalen UWP-Paketen oder verwandten Gruppen sind, sind die folgenden Artikel gute Ressourcen für den Einstieg. 

1.  [Erweitern der Anwendung mit optionalen Paketen](https://blogs.msdn.microsoft.com/appinstaller/2017/04/05/uwpoptionalpackages/)
2.  [Erstellen Ihres ersten optionalen Pakets](https://blogs.msdn.microsoft.com/appinstaller/2017/05/09/build-your-first-optional-package/)
3.  [Laden von Code über ein optionales Paket](https://blogs.msdn.microsoft.com/appinstaller/2017/05/11/loading-code-from-an-optional-package/)
4.  [Tool zum Erstellen einer verwandten Gruppe](https://blogs.msdn.microsoft.com/appinstaller/2017/05/12/tooling-to-create-a-related-set/)
5.  [Optionale Pakete und die Erstellung zugehöriger Sets](https://docs.microsoft.com/windows/uwp/packaging/optional-packages)

Mit dem Windows 10 Fall Creators Update können verwandte Gruppen jetzt über App-Installer installiert werden. Dies ermöglicht die Verteilung und Bereitstellung der mit App-Paketen verwandten Gruppen für die Benutzer. 

## <a name="how-to-install-a-related-set"></a>Installieren einer verwandten Gruppe 
Eine verwandte Gruppe ist keine Entität, sondern eine Kombination aus einem Hauptpaket und optionalen Paketen. Um eine verwandte Gruppe als eine Einheit installieren zu können, muss das Hauptpaket und ein optionales Paket als ein einziges Paket angegeben werden. Zu diesem Zweck müssen wir eine XML-Datei mit der Erweiterung ".appinstaller" erstellen, um die verwandte Gruppe zu definieren. Der App-Installer beansprucht die *.appinstaller-Datei und ermöglicht dem Benutzer, alle definierten Pakete mit nur einem Klick zu installieren. 

Bevor wir weitere ins Detail gehen, sehen Sie hier eine vollständige *.appinstaller-Beispieldatei:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017/2"
    Version="1.0.0.0" 
    Uri="http://mywebservice.azurewebsites.net/appset.appinstaller" > 
   
    <MainBundle 
        Name="Contoso.MainApp"
        Publisher="CN=Contoso"
        Version="2.23.12.43"
        Uri="http://mywebservice.azurewebsites.net/mainapp.appxbundle" />
        
    <OptionalPackages>
        <Bundle
            Name="Contoso.OptionalApp1"
            Publisher="CN=Contoso"
            Version="2.23.12.43"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp1.appxbundle" />

        <Bundle
            Name="Contoso.OptionalApp2"
            Publisher="CN=Contoso"
            Version="2.23.12.43"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp2.appxbundle" />

        <Package
            Name="Fabrikam.OptionalApp3"
            Publisher="CN=Fabrikam"
            Version="10.34.54.23"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp3.appx" />

    </OptionalPackages>

</AppInstaller>
```

Während der Bereitstellung wird die App-Installer-Datei mit den App-Paketen im `Uri`-Element abgestimmt. Das bedeutet, der `Name`, `Publisher` und die `Version` sollten dem [Package/Identity](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity)-Element im App-Paketmanifest entsprechen. 

## <a name="how-to-create-an-app-installer-file"></a>So erstellen Sie eine App-Installer-Datei 

Um die verwandte Gruppe als eine Entität zu verteilen, erstellen Sie eine App-Installer-Datei im [Appinstaller-Schema](https://docs.microsoft.com/uwp/schemas/appinstallerschema/app-installer-file), die die erforderlichen Elemente enthält.

### <a name="step-1-create-the-appinstaller-file"></a>Schritt 1. Erstellen der *.appinstaller-Datei
Verwenden Sie einen Text-Editor, um eine Datei zu erstellen (die XML enthält), und nennen Sie sie &lt;Dateiname&gt;.appinstaller. 

### <a name="step-2-add-the-basic-template"></a>Schritt 2: Hinzufügen der einfachen Vorlage
Die einfache Vorlage enthält die Informationen der App-Installer-Datei. 
```xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017/2"
    Version="1.0.0.0" 
    Uri="http://mywebservice.azurewebsites.net/appset.appinstaller" > 
</AppInstaller>
```

### <a name="step-3-add-the-main-package-information"></a>Schritt3: Hinzufügen der Hauptpaket-Informationen 
Wenn das Haupt-app-Paket eine .appxbundle oder .msixbundle-Datei ist, verwenden Sie die `<MainBundle>` unten dargestellt. Wenn das Haupt-app-Paket eine .appx oder .msix-Datei ist, verwenden Sie `<MainPackage>` anstelle von `<MainBundle>` im Codeausschnitt. 

```xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017/2"
    Version="1.0.0.0" 
    Uri="http://mywebservice.azurewebsites.net/appset.appinstaller" > 
   
    <MainBundle 
        Name="Contoso.MainApp"
        Publisher="CN=Contoso"
        Version="2.23.12.43"
        Uri="http://mywebservice.azurewebsites.net/mainapp.appxbundle" />

</AppInstaller>
```
Die Informationen des `<MainBundle>` oder `<MainPackage>`-Attributs sollte mit dem [Package/Identity](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity)-Element im App-Bündelmanifest oder im App-Paket-Manifest übereinstimmen. 

### <a name="step-4-add-the-optional-packages"></a>Schritt4: Hinzufügen von optionalen Paketen 
Ähnlich wie beim Haupt-App-Paket-Attribut, wenn das optionale Paket entweder ein App-Paket oder ein App-Bündel ist, sollte das untergeordnete Element innerhalb des `<OptionalPackages>`-Attributs ein `<Package>` oder `<Bundle>` sein. Die Paketinformationen in den untergeordneten Elementen sollten mit dem identity-Element im Bündel oder im Paketmanifest übereinstimmen. 

``` xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017/2"
    Version="1.0.0.0" 
    Uri="http://mywebservice.azurewebsites.net/appset.appinstaller" > 
   
    <MainBundle 
        Name="Contoso.MainApp"
        Publisher="CN=Contoso"
        Version="2.23.12.43"
        Uri="http://mywebservice.azurewebsites.net/mainapp.appxbundle" />
        
    <OptionalPackages>
        <Bundle
            Name="Contoso.OptionalApp1"
            Publisher="CN=Contoso"
            Version="2.23.12.43"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp1.appxbundle" />

        <Bundle
            Name="Contoso.OptionalApp2"
            Publisher="CN=Contoso"
            Version="2.23.12.43"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp2.appxbundle" />

        <Package
            Name="Fabrikam.OptionalApp3"
            Publisher="CN=Fabrikam"
            Version="10.34.54.23"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp3.appx" />

    </OptionalPackages>

</AppInstaller>
```

### <a name="step-5-add-dependencies"></a>Schritt 5: Hinzufügen von Abhängigkeiten 
Si können im Element der Abhängigkeiten das erforderliche Framework-Pakete für das Hauptpaket oder die optionalen Pakete angeben. 

``` xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017/2"
    Version="1.0.0.0" 
    Uri="http://mywebservice.azurewebsites.net/appset.appinstaller" > 
   
    <MainBundle 
        Name="Contoso.MainApp"
        Publisher="CN=Contoso"
        Version="2.23.12.43"
        Uri="http://mywebservice.azurewebsites.net/mainapp.appxbundle" />
        
    <OptionalPackages>
        <Bundle
            Name="Contoso.OptionalApp1"
            Publisher="CN=Contoso"
            Version="2.23.12.43"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp1.appxbundle" />

        <Bundle
            Name="Contoso.OptionalApp2"
            Publisher="CN=Contoso"
            Version="2.23.12.43"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp2.appxbundle" />

        <Package
            Name="Fabrikam.OptionalApp3"
            Publisher="CN=Fabrikam"
            Version="10.34.54.23"
            ProcessorArchitecture="x86"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp3.appx" />

    </OptionalPackages>

    <Dependencies>
        <Package Name="Microsoft.VCLibs.140.00" Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" Version="14.0.24605.0" ProcessorArchitecture="x86" Uri="http://foobarbaz.com/fwkx86.appx" />
        <Package Name="Microsoft.VCLibs.140.00" Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" Version="14.0.24605.0" ProcessorArchitecture="x64" Uri="http://foobarbaz.com/fwkx64.appx" />
    </Dependencies>

</AppInstaller>
```

### <a name="step-6-add-update-setting"></a>Schritt6: Hinzufügen von Update-Einstellungen 
Die App-Installer-Datei kann auch Update-Einstellung angeben, damit die verwandten Gruppen automatisch aktualisiert werden können, wenn eine neuere App-Installer-Datei veröffentlicht wird. **<UpdateSettings>** ist ein optionales Element. In **<UpdateSettings>** gibt die OnLaunch Option an, dass Update-Prüfungen beim Start der App durchgeführt werden sollen, und HoursBetweenUpdateChecks="12" gibt an, dass alle 12 Stunden eine Update-Prüfung durchgeführt werden soll. Wenn „HoursBetweenUpdateChecks” nicht angegeben ist, beträgt das Standardintervall für die Suche nach Updates 24 Stunden.
``` xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017/2"
    Version="1.0.0.0" 
    Uri="http://mywebservice.azurewebsites.net/appset.appinstaller" > 
   
    <MainBundle 
        Name="Contoso.MainApp"
        Publisher="CN=Contoso"
        Version="2.23.12.43"
        Uri="http://mywebservice.azurewebsites.net/mainapp.appxbundle" />
        
    <OptionalPackages>
        <Bundle
            Name="Contoso.OptionalApp1"
            Publisher="CN=Contoso"
            Version="2.23.12.43"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp1.appxbundle" />

        <Bundle
            Name="Contoso.OptionalApp2"
            Publisher="CN=Contoso"
            Version="2.23.12.43"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp2.appxbundle" />

        <Package
            Name="Fabrikam.OptionalApp3"
            Publisher="CN=Fabrikam"
            Version="10.34.54.23"
            ProcessorArchitecture="x86"
            Uri="http://mywebservice.azurewebsites.net/OptionalApp3.appx" />

    </OptionalPackages>

    <Dependencies>
        <Package Name="Microsoft.VCLibs.140.00" Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" Version="14.0.24605.0" ProcessorArchitecture="x86" Uri="http://foobarbaz.com/fwkx86.appx" />
        <Package Name="Microsoft.VCLibs.140.00" Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" Version="14.0.24605.0" ProcessorArchitecture="x64" Uri="http://foobarbaz.com/fwkx64.appx" />
    </Dependencies>
    
    <UpdateSettings>
        <OnLaunch HoursBetweenUpdateChecks="12" />
    </UpdateSettings>

</AppInstaller>
```

Alle Details für das XML-Schema finden Sie unter [Referenz für die App-Installer-Datei](https://docs.microsoft.com/uwp/schemas/appinstallerschema/app-installer-file).

> [!NOTE]
> 
> Der Typ der App-Installer-Datei ist neu im Windows 10 Fall Creators Update. Es ist keine Unterstützung für die Bereitstellung von UWP-Apps durch eine App-Installer-Datei für frühere Versionen von Windows10.
> Außerdem muss darauf hingewiesen werden, dass das **HoursBetweenUpdateChecks**-Element im nächsten wichtigen Update für Windows 10 neu ist.
