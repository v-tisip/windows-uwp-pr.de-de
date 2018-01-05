---
author: laurenhughes
title: Installieren einer verwandten Gruppe mithilfe einer App-Installer-Datei
description: "In diesem Abschnitt überprüfen wir die erforderlichen Schritte, damit die Installation von verwandten Gruppen über den App-Installer möglich ist. Wir durchlaufen ebenfalls die notwendigen Schritte zum Erstellen einer *.appinstaller-Datei, die Ihre verwandten Gruppen definieren."
ms.author: lahugh
ms.date: 10/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, App-Installer, AppInstaller, querladen, verwandte Gruppe, optionale Pakete
ms.localizationpriority: medium
ms.openlocfilehash: 484d69f5f9f0b15b765f6f92eaad787af37134cf
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="install-a-related-set-using-an-app-installer-file"></a><span data-ttu-id="840d7-105">Installieren einer verwandten Gruppe mithilfe einer App-Installer-Datei</span><span class="sxs-lookup"><span data-stu-id="840d7-105">Install a related set using an App Installer file</span></span>

<span data-ttu-id="840d7-106">Wenn Sie am Anfang der Entwicklung mit optionalen UWP-Paketen oder verwandten Gruppen sind, sind die folgenden Artikel gute Ressourcen für den Einstieg.</span><span class="sxs-lookup"><span data-stu-id="840d7-106">If you're just starting out with UWP optional packages or related sets, the following articles are good resources to get started.</span></span> 

1.  [<span data-ttu-id="840d7-107">Erweitern der Anwendung mit optionalen Paketen</span><span class="sxs-lookup"><span data-stu-id="840d7-107">Extend your application using Optional Packages</span></span>](https://blogs.msdn.microsoft.com/appinstaller/2017/04/05/uwpoptionalpackages/)
2.  [<span data-ttu-id="840d7-108">Erstellen Ihres ersten optionalen Pakets</span><span class="sxs-lookup"><span data-stu-id="840d7-108">Build your first Optional Package</span></span>](https://blogs.msdn.microsoft.com/appinstaller/2017/05/09/build-your-first-optional-package/)
3.  [<span data-ttu-id="840d7-109">Laden von Code über ein optionales Paket</span><span class="sxs-lookup"><span data-stu-id="840d7-109">Loading code from an optional package</span></span>](https://blogs.msdn.microsoft.com/appinstaller/2017/05/11/loading-code-from-an-optional-package/)
4.  [<span data-ttu-id="840d7-110">Tool zum Erstellen einer verwandten Gruppe</span><span class="sxs-lookup"><span data-stu-id="840d7-110">Tooling to create a Related Set</span></span>](https://blogs.msdn.microsoft.com/appinstaller/2017/05/12/tooling-to-create-a-related-set/)
5.  [<span data-ttu-id="840d7-111">Optionale Pakete und die Erstellung zugehöriger Sets</span><span class="sxs-lookup"><span data-stu-id="840d7-111">Optional packages and related set authoring</span></span>](https://docs.microsoft.com/windows/uwp/packaging/optional-packages)

<span data-ttu-id="840d7-112">Mit dem Windows 10 Fall Creators Update können verwandte Gruppen jetzt über App-Installer installiert werden.</span><span class="sxs-lookup"><span data-stu-id="840d7-112">With the Windows 10 Fall Creators Update, related sets can now be installed via App Installer.</span></span> <span data-ttu-id="840d7-113">Dies ermöglicht die Verteilung und Bereitstellung der mit App-Paketen verwandten Gruppen für die Benutzer.</span><span class="sxs-lookup"><span data-stu-id="840d7-113">This allows distribution and deployment of related set app packages to users.</span></span> 

## <a name="how-to-install-a-related-set"></a><span data-ttu-id="840d7-114">Installieren einer verwandten Gruppe</span><span class="sxs-lookup"><span data-stu-id="840d7-114">How to install a related set</span></span> 
<span data-ttu-id="840d7-115">Eine verwandte Gruppe ist keine Entität, sondern eine Kombination aus einem Hauptpaket und optionalen Paketen.</span><span class="sxs-lookup"><span data-stu-id="840d7-115">A related set is not one entity, but rather a combination of a main package and optional packages.</span></span> <span data-ttu-id="840d7-116">Um eine verwandte Gruppe als eine Einheit installieren zu können, muss das Hauptpaket und ein optionales Paket als ein einziges Paket angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="840d7-116">To be able to install a related set as one entity, we must be able to specify the main package and optional package as one.</span></span> <span data-ttu-id="840d7-117">Zu diesem Zweck müssen wir eine XML-Datei mit der Erweiterung ".appinstaller" erstellen, um die verwandte Gruppe zu definieren.</span><span class="sxs-lookup"><span data-stu-id="840d7-117">To do this, we will need to create an XML file with a ".appinstaller" extension to define a related set.</span></span> <span data-ttu-id="840d7-118">Der App-Installer beansprucht die *.appinstaller-Datei und ermöglicht dem Benutzer, alle definierten Pakete mit nur einem Klick zu installieren.</span><span class="sxs-lookup"><span data-stu-id="840d7-118">App Installer consumes the *.appinstaller file and allows the user to install all of the defined packages with a single click.</span></span> 

<span data-ttu-id="840d7-119">Bevor wir weitere ins Detail gehen, sehen Sie hier eine vollständige *.appinstaller-Beispieldatei:</span><span class="sxs-lookup"><span data-stu-id="840d7-119">Before we go in to more detail, here is a complete sample *.appinstaller file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017"
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

<span data-ttu-id="840d7-120">Während der Bereitstellung wird die App-Installer-Datei mit den App-Paketen im `Uri`-Element abgestimmt.</span><span class="sxs-lookup"><span data-stu-id="840d7-120">During deployment, the App Installer file is validated against the app packages referenced in the `Uri` element.</span></span> <span data-ttu-id="840d7-121">Das bedeutet, der `Name`, `Publisher` und die `Version` sollten dem [Package/Identity](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity)-Element im App-Paketmanifest entsprechen.</span><span class="sxs-lookup"><span data-stu-id="840d7-121">So, the `Name`, `Publisher` and `Version` should match the [Package/Identity](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity) element in the app package manifest.</span></span> 

## <a name="how-to-create-an-app-installer-file"></a><span data-ttu-id="840d7-122">So erstellen Sie eine App-Installer-Datei</span><span class="sxs-lookup"><span data-stu-id="840d7-122">How to create an App Installer file</span></span> 

<span data-ttu-id="840d7-123">Um die verwandte Gruppe als eine Entität zu verteilen, erstellen Sie eine App-Installer-Datei im [Appinstaller-Schema](https://docs.microsoft.com/uwp/schemas/appinstallerschema/app-installer-file), die die erforderlichen Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="840d7-123">To distribute your related set as one entity, you must create an App Installer file that contains the elements that are required by that [appinstaller schema](https://docs.microsoft.com/uwp/schemas/appinstallerschema/app-installer-file).</span></span>

### <a name="step-1-create-the-appinstaller-file"></a><span data-ttu-id="840d7-124">Schritt 1. Erstellen der *.appinstaller-Datei</span><span class="sxs-lookup"><span data-stu-id="840d7-124">Step 1: Create the *.appinstaller file</span></span>
<span data-ttu-id="840d7-125">Verwenden Sie einen Text-Editor, um eine Datei zu erstellen (die XML enthält), und nennen Sie sie &lt;Dateiname&gt;.appinstaller.</span><span class="sxs-lookup"><span data-stu-id="840d7-125">Using a text editor, create a file (which will contain XML) and name it &lt;filename&gt;.appinstaller</span></span> 

### <a name="step-2-add-the-basic-template"></a><span data-ttu-id="840d7-126">Schritt 2: Hinzufügen der einfachen Vorlage</span><span class="sxs-lookup"><span data-stu-id="840d7-126">Step 2: Add the basic template</span></span>
<span data-ttu-id="840d7-127">Die einfache Vorlage enthält die Informationen der App-Installer-Datei.</span><span class="sxs-lookup"><span data-stu-id="840d7-127">The basic template includes the App Installer file information.</span></span> 
```xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017"
    Version="1.0.0.0" 
    Uri="http://mywebservice.azurewebsites.net/appset.appinstaller" > 
</AppInstaller>
```

### <a name="step-3-add-the-main-package-information"></a><span data-ttu-id="840d7-128">Schritt3: Hinzufügen der Hauptpaket-Informationen</span><span class="sxs-lookup"><span data-stu-id="840d7-128">Step 3: Add the main package information</span></span> 
<span data-ttu-id="840d7-129">Wenn das Haupt-App-Paket eine .appxbundle-Datei ist, verwenden Sie das unten angezeigte `<MainBundle>`.</span><span class="sxs-lookup"><span data-stu-id="840d7-129">If the main app package is an .appxbundle file, then use the `<MainBundle>` shown below.</span></span> <span data-ttu-id="840d7-130">Wenn das Haupt-App-Paket eine .appx-Datei ist, verwenden Sie das `<MainPackage>` anstelle des `<MainBundle>` im Codeausschnitt.</span><span class="sxs-lookup"><span data-stu-id="840d7-130">If the main app package is an .appx file, then use `<MainPackage>` in place of `<MainBundle>` in the snippet.</span></span> 

```xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017"
    Version="1.0.0.0" 
    Uri="http://mywebservice.azurewebsites.net/appset.appinstaller" > 
   
    <MainBundle 
        Name="Contoso.MainApp"
        Publisher="CN=Contoso"
        Version="2.23.12.43"
        Uri="http://mywebservice.azurewebsites.net/mainapp.appxbundle" />

</AppInstaller>
```
<span data-ttu-id="840d7-131">Die Informationen des `<MainBundle>` oder `<MainPackage>`-Attributs sollte mit dem [Package/Identity](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity)-Element im App-Bündelmanifest oder im App-Paket-Manifest übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="840d7-131">The information in the `<MainBundle>` or `<MainPackage>` attribute should match the [Package/Identity](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity) element in the app bundle manifest or app package manifest respectively.</span></span> 

### <a name="step-4-add-the-optional-packages"></a><span data-ttu-id="840d7-132">Schritt4: Hinzufügen von optionalen Paketen</span><span class="sxs-lookup"><span data-stu-id="840d7-132">Step 4: Add the optional packages</span></span> 
<span data-ttu-id="840d7-133">Ähnlich wie beim Haupt-App-Paket-Attribut, wenn das optionale Paket entweder ein App-Paket oder ein App-Bündel ist, sollte das untergeordnete Element innerhalb des `<OptionalPackages>`-Attributs ein `<Package>` oder `<Bundle>` sein.</span><span class="sxs-lookup"><span data-stu-id="840d7-133">Similar to the main app package attribute, if the optional package can be either an app package or an app bundle, the child element within the `<OptionalPackages>` attribute should be `<Package>` or `<Bundle>` respectively.</span></span> <span data-ttu-id="840d7-134">Die Paketinformationen in den untergeordneten Elementen sollten mit dem identity-Element im Bündel oder im Paketmanifest übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="840d7-134">The package information in the child elements should match the identity element in the bundle or package manifest.</span></span> 

``` xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017"
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

### <a name="step-5-add-dependencies"></a><span data-ttu-id="840d7-135">Schritt 5: Hinzufügen von Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="840d7-135">Step 5: Add dependencies</span></span> 
<span data-ttu-id="840d7-136">Si können im Element der Abhängigkeiten das erforderliche Framework-Pakete für das Hauptpaket oder die optionalen Pakete angeben.</span><span class="sxs-lookup"><span data-stu-id="840d7-136">In the dependencies element, you can specify the required framework packages for the main package or the optional packages.</span></span> 

``` xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017"
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

### <a name="step-6-add-update-setting"></a><span data-ttu-id="840d7-137">Schritt6: Hinzufügen von Update-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="840d7-137">Step 6: Add Update setting</span></span> 
<span data-ttu-id="840d7-138">Die App-Installer-Datei kann auch Update-Einstellung angeben, damit die verwandten Gruppen automatisch aktualisiert werden können, wenn eine neuere App-Installer-Datei veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="840d7-138">The App Installer file can also specify update setting so that the related sets can be automatically updated when a newer App Installer file is published.</span></span> <span data-ttu-id="840d7-139">**<UpdateSettings>** ist ein optionales Element.</span><span class="sxs-lookup"><span data-stu-id="840d7-139">**<UpdateSettings>** is an optional element.</span></span> 
``` xml
<?xml version="1.0" encoding="utf-8"?>
<AppInstaller
    xmlns="http://schemas.microsoft.com/appx/appinstaller/2017"
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
        <OnLaunch />
    </UpdateSettings>

</AppInstaller>
```

<span data-ttu-id="840d7-140">Alle Details für das XML-Schema finden Sie unter [Referenz für die App-Installer-Datei](https://docs.microsoft.com/uwp/schemas/appinstallerschema/app-installer-file).</span><span class="sxs-lookup"><span data-stu-id="840d7-140">For all of the details on the XML schema, see [App Installer file reference](https://docs.microsoft.com/uwp/schemas/appinstallerschema/app-installer-file).</span></span>

> [!NOTE]
> 
> <span data-ttu-id="840d7-141">Der Typ der App-Installer-Datei ist neu im Windows 10 Fall Creators Update.</span><span class="sxs-lookup"><span data-stu-id="840d7-141">The App Installer file type is new in the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="840d7-142">Es ist keine Unterstützung für die Bereitstellung von UWP-Apps durch eine App-Installer-Datei für frühere Versionen von Windows10.</span><span class="sxs-lookup"><span data-stu-id="840d7-142">There is no support for deployment of UWP apps using an App Installer file on previous versions of Windows 10.</span></span> 