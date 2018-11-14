---
author: normesta
Description: Shows how to manually package a Windows desktop application (like Win32, WPF, and Windows Forms) for Windows 10.
Search.Product: eADQiWindows 10XVcnh
title: Eine Anwendung manuell Verpacken (Desktop-Brücke)
ms.author: normesta
ms.date: 05/18/2018
ms.topic: article
keywords: windows10, UWP
ms.assetid: e8c2a803-9803-47c5-b117-73c4af52c5b6
ms.localizationpriority: medium
ms.openlocfilehash: 6b063bf5997bbb1fc082c8d9fefcf0f435262bf1
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6143654"
---
# <a name="package-a-desktop-application-manually"></a><span data-ttu-id="948f9-103">Manuelles Verpacken einer desktop-Anwendungs</span><span class="sxs-lookup"><span data-stu-id="948f9-103">Package a desktop application manually</span></span>

<span data-ttu-id="948f9-104">Dieses Thema zeigt, wie Sie Ihre Anwendung ohne Tools wie Visual Studio oder den Desktop App Converter (DAC) verpacken.</span><span class="sxs-lookup"><span data-stu-id="948f9-104">This topic shows you how to package your application without using tools such as Visual Studio or the Desktop App Converter (DAC).</span></span>

<span data-ttu-id="948f9-105">Um Ihre App manuell zu verpacken, erstellen Sie eine Paketmanifestdatei, und führen Sie dann ein Befehlszeilentool aus, um ein Windows-App-Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="948f9-105">To manually package your app, create a package manifest file, and then run a command line tool to generate a Windows app package.</span></span>

<span data-ttu-id="948f9-106">Berücksichtigen Sie die manuelle Verpackung, wenn Sie die Anwendung mithilfe des Befehls Xcopy installieren, oder Sie mit den auf dem System Ihren app Installer vorgenommenen Änderungen vertraut sind und genauere Kontrolle über den Prozess.</span><span class="sxs-lookup"><span data-stu-id="948f9-106">Consider manual packaging if you install your application by using the xcopy command, or you're familiar with the changes that your app's installer makes to the system and want more granular control over the process.</span></span>

<span data-ttu-id="948f9-107">Wenn Sie sich nicht darüber sicher sind, welche Änderungen an das System durch Ihren Installer vorgenommen werden oder wenn Sie lieber automatisierte Tools für das Generieren Ihres Paketmanifestes verwenden möchten, sollten Sie eine [dieser](desktop-to-uwp-root.md#convert) Optionen erwägen.</span><span class="sxs-lookup"><span data-stu-id="948f9-107">If you're uncertain about what changes your installer makes to the system, or if you'd rather use automated tools to generate your package manifest, consider any of [these](desktop-to-uwp-root.md#convert) options.</span></span>

>[!IMPORTANT]
><span data-ttu-id="948f9-108">Die Fähigkeit zum Erstellen eines Windows-app-Pakets für Ihre desktop-Anwendung (auch bekannt als der Desktop-Brücke) wurde in Windows 10, Version 1607, eingeführt und kann nur in Projekten für die Windows 10 Anniversary Update (10.0; verwendet werden Build 14393) oder einer neueren Version in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="948f9-108">The ability to create a Windows app package for your desktop application (otherwise known as the Desktop Bridge) was introduced in Windows 10, version 1607, and it can only be used in projects that target Windows 10 Anniversary Update (10.0; Build 14393) or a later release in Visual Studio.</span></span>

## <a name="first-prepare-your-application"></a><span data-ttu-id="948f9-109">Vorbereiten Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="948f9-109">First, prepare your application</span></span>

<span data-ttu-id="948f9-110">Lesen Sie dieses Handbuch, bevor Sie mit der paketerstellung für Ihre Anwendung beginnen: [Vorbereiten eine desktop-Anwendung zu verpacken](desktop-to-uwp-prepare.md).</span><span class="sxs-lookup"><span data-stu-id="948f9-110">Review this guide before you begin creating a package for your application: [Prepare to package a desktop application](desktop-to-uwp-prepare.md).</span></span>

## <a name="create-a-package-manifest"></a><span data-ttu-id="948f9-111">Erstellen eines Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="948f9-111">Create a package manifest</span></span>

<span data-ttu-id="948f9-112">Erstellen Sie eine Datei, nennen Sie sie **appxmanifest.xml**, und fügen Sie diese XML-Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="948f9-112">Create a file, name it **appxmanifest.xml**, and then add this XML to it.</span></span>

<span data-ttu-id="948f9-113">Es ist eine einfache Vorlage, die die vom Paket benötigten Elemente und Attribute enthält.</span><span class="sxs-lookup"><span data-stu-id="948f9-113">It's a basic template that contains the elements and attributes that your package needs.</span></span> <span data-ttu-id="948f9-114">Wir werden im nächsten Abschnittdie Werte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="948f9-114">We'll add values to these in the next section.</span></span>

```XML
<?xml version="1.0" encoding="utf-8"?>
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities">
  <Identity Name="" Version="" Publisher="" ProcessorArchitecture="" />
    <Properties>
       <DisplayName></DisplayName>
       <PublisherDisplayName></PublisherDisplayName>
             <Description></Description>
      <Logo></Logo>
    </Properties>
    <Resources>
      <Resource Language="" />
    </Resources>
      <Dependencies>
      <TargetDeviceFamily Name="Windows.Desktop" MinVersion="" MaxVersionTested="" />
      </Dependencies>
      <Capabilities>
        <rescap:Capability Name="runFullTrust"/>
      </Capabilities>
    <Applications>
      <Application Id="" Executable="" EntryPoint="Windows.FullTrustApplication">
        <uap:VisualElements DisplayName="" Description=""   Square150x150Logo=""
                   Square44x44Logo=""   BackgroundColor="" />
      </Application>
     </Applications>
  </Package>
```

## <a name="fill-in-the-package-level-elements-of-your-file"></a><span data-ttu-id="948f9-115">Füllen Sie die Paketelemente in der Datei aus.</span><span class="sxs-lookup"><span data-stu-id="948f9-115">Fill in the package-level elements of your file</span></span>

<span data-ttu-id="948f9-116">Geben Sie in diese Vorlage Informationen ein, die das Paket beschreiben.</span><span class="sxs-lookup"><span data-stu-id="948f9-116">Fill in this template with information that describes your package.</span></span>

### <a name="identity-information"></a><span data-ttu-id="948f9-117">Identitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="948f9-117">Identity information</span></span>

<span data-ttu-id="948f9-118">Hier ist ein Beispiel für ein **Identitäts**-Element mit Platzhaltertext für die Attribute.</span><span class="sxs-lookup"><span data-stu-id="948f9-118">Here's an example **Identity** element with placeholder text for the attributes.</span></span> <span data-ttu-id="948f9-119">Sie können das ``ProcessorArchitecture``-Attributs auf ``x64``oder ``x86`` festlegen.</span><span class="sxs-lookup"><span data-stu-id="948f9-119">You can set the ``ProcessorArchitecture`` attribute to ``x64`` or ``x86``.</span></span>

```XML
<Identity Name="MyCompany.MySuite.MyApp"
          Version="1.0.0.0"
          Publisher="CN=MyCompany, O=MyCompany, L=MyCity, S=MyState, C=MyCountry"
                ProcessorArchitecture="x64">
```
> [!NOTE]
> <span data-ttu-id="948f9-120">Wenn Sie den Anwendungsnamen Ihrer im Windows Store reserviert haben, können Sie den Namen und Herausgeber abrufen, mit dem Windows Dev Center-Dashboard.</span><span class="sxs-lookup"><span data-stu-id="948f9-120">If you've reserved your application name in the Windows store, you can obtain the Name and Publisher by using the Windows Dev Center dashboard.</span></span> <span data-ttu-id="948f9-121">Wenn Sie Ihre Anwendung auf andere Systeme querladen möchten, können Sie für diese Ihre eigenen Namen bereitstellen, solange der Name des Herausgebers, die Sie auswählen, mit dem Namen des Zertifikats übereinstimmt, die Sie zum Signieren Ihrer app verwenden.</span><span class="sxs-lookup"><span data-stu-id="948f9-121">If you plan to sideload your application onto other systems, you can provide your own names for these as long as the publisher name that you choose matches the name on the certificate you use to sign your app.</span></span>

### <a name="properties"></a><span data-ttu-id="948f9-122">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="948f9-122">Properties</span></span>

<span data-ttu-id="948f9-123">Das [Eigenschaften](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-properties)-Element hat 3 erforderliche untergeordnete Elemente.</span><span class="sxs-lookup"><span data-stu-id="948f9-123">The [Properties](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-properties) element has 3 required child elements.</span></span> <span data-ttu-id="948f9-124">Hier ist ein Beispiel für einen **Eigenschaften**-Knoten mit Platzhaltertext für die Elemente.</span><span class="sxs-lookup"><span data-stu-id="948f9-124">Here is an example **Properties** node with placeholder text for the elements.</span></span> <span data-ttu-id="948f9-125">**DisplayName** ist der Name der Anwendung, die Sie im Store für apps reservieren, die an den Store hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="948f9-125">The **DisplayName** is the name of your application that you reserve in the store, for apps which are uploaded to the store.</span></span>

```XML
<Properties>
  <DisplayName>MyApp</DisplayName>
  <PublisherDisplayName>MyCompany</PublisherDisplayName>
  <Logo>images\icon.png</Logo>
</Properties>
```

### <a name="resources"></a><span data-ttu-id="948f9-126">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="948f9-126">Resources</span></span>

<span data-ttu-id="948f9-127">Hier ist ein Beispiel für einen [Ressourcen](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-resources)-Knoten.</span><span class="sxs-lookup"><span data-stu-id="948f9-127">Here is an example [Resources](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-resources) node.</span></span>

```XML
<Resources>
  <Resource Language="en-us" />
</Resources>
```
### <a name="dependencies"></a><span data-ttu-id="948f9-128">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="948f9-128">Dependencies</span></span>

<span data-ttu-id="948f9-129">Für desktop-apps, die Sie ein Paket erstellen, legen Sie immer die ``Name`` -Attribut auf ``Windows.Desktop``.</span><span class="sxs-lookup"><span data-stu-id="948f9-129">For desktop apps that you create a package for, always set the ``Name`` attribute to ``Windows.Desktop``.</span></span>

```XML
<Dependencies>
<TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14316.0" MaxVersionTested="10.0.15063.0" />
</Dependencies>
```

### <a name="capabilities"></a><span data-ttu-id="948f9-130">Funktionen</span><span class="sxs-lookup"><span data-stu-id="948f9-130">Capabilities</span></span>
<span data-ttu-id="948f9-131">Für desktop-apps, die Sie ein Paket erstellen, für, müssen Sie das Hinzufügen der ``runFullTrust`` Funktion.</span><span class="sxs-lookup"><span data-stu-id="948f9-131">For desktop apps that you create a package for, you'll have to add the ``runFullTrust`` capability.</span></span>

```XML
<Capabilities>
  <rescap:Capability Name="runFullTrust"/>
</Capabilities>
```
## <a name="fill-in-the-application-level-elements"></a><span data-ttu-id="948f9-132">Ausfüllen der Elemente auf Anwendungsebene</span><span class="sxs-lookup"><span data-stu-id="948f9-132">Fill in the application-level elements</span></span>

<span data-ttu-id="948f9-133">Geben Sie in diese Vorlage Informationen ein, die Ihre App beschreiben.</span><span class="sxs-lookup"><span data-stu-id="948f9-133">Fill in this template with information that describes your app.</span></span>

### <a name="application-element"></a><span data-ttu-id="948f9-134">Anwendungselemente</span><span class="sxs-lookup"><span data-stu-id="948f9-134">Application element</span></span>

<span data-ttu-id="948f9-135">Für desktop-apps, die Sie erstellen Sie ein Paket, das ``EntryPoint`` -Attribut des Application-Elements ist immer ``Windows.FullTrustApplication``.</span><span class="sxs-lookup"><span data-stu-id="948f9-135">For desktop apps that you create a package for, the ``EntryPoint`` attribute of the Application element is always ``Windows.FullTrustApplication``.</span></span>

```XML
<Applications>
  <Application Id="MyApp"     
        Executable="MyApp.exe" EntryPoint="Windows.FullTrustApplication">
   </Application>
</Applications>
```

### <a name="visual-elements"></a><span data-ttu-id="948f9-136">Visuelle Elemente</span><span class="sxs-lookup"><span data-stu-id="948f9-136">Visual elements</span></span>

<span data-ttu-id="948f9-137">Hier ist ein Beispiel für einen [VisualElements](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements)-Knoten.</span><span class="sxs-lookup"><span data-stu-id="948f9-137">Here is an example [VisualElements](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements) node.</span></span>

```XML
<uap:VisualElements
    BackgroundColor="#464646"
    DisplayName="My App"
    Square150x150Logo="images\icon.png"
    Square44x44Logo="images\small_icon.png"
    Description="A useful description" />
```
<a id="target-based-assets" />

## <a name="optional-add-target-based-unplated-assets"></a><span data-ttu-id="948f9-138">(Optional) Zielbasierte Ressourcen ohne Anpassung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="948f9-138">(Optional) Add Target-based unplated assets</span></span>

<span data-ttu-id="948f9-139">Zielbasierte Ressourcen gelten für Symbole und Kacheln, die in der Windows-Taskleiste, in der Aufgabenansicht, über ALT+TAB, in der Andockhilfe und in der unteren rechten Ecke von Startkacheln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="948f9-139">Target-based assets are for icons and tiles that appear on the Windows taskbar, task view, ALT+TAB, snap-assist, and the lower-right corner of Start tiles.</span></span> <span data-ttu-id="948f9-140">Erhalten Sie [hier](https://docs.microsoft.com/windows/uwp/design/style/app-icons-and-logos#unplated-assets) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="948f9-140">You can read more about them [here](https://docs.microsoft.com/windows/uwp/design/style/app-icons-and-logos#unplated-assets).</span></span>

1. <span data-ttu-id="948f9-141">Rufen Sie die richtigen 44x44-Bilder ab, und kopieren Sie sie dann in den Ordner, der Ihre Bilder (d.h. Ressourcen) enthält.</span><span class="sxs-lookup"><span data-stu-id="948f9-141">Obtain the correct 44x44 images and then copy them into the folder that contains your images (i.e., Assets).</span></span>

2. <span data-ttu-id="948f9-142">Erstellen Sie für jedes 44x44-Bild eine Kopie im selben Ordner, und hängen Sie **.targetsize-44_altform-unplated** an den Dateinamen an.</span><span class="sxs-lookup"><span data-stu-id="948f9-142">For each 44x44 image, create a copy in the same folder and append **.targetsize-44_altform-unplated** to the file name.</span></span> <span data-ttu-id="948f9-143">Sie sollten zwei Kopien von jedem Symbol haben, jeweils spezifisch benannt.</span><span class="sxs-lookup"><span data-stu-id="948f9-143">You should have two copies of each icon, each named in a specific way.</span></span> <span data-ttu-id="948f9-144">Nach Abschluss des Prozesses könnte Ihr Ressourcen-Ordner beispielsweise **MYAPP_44x44.png** und **MYAPP_44x44.targetsize-44_altform-unplated.png** enthalten.</span><span class="sxs-lookup"><span data-stu-id="948f9-144">For example, after completing the process, your assets folder might contain **MYAPP_44x44.png** and **MYAPP_44x44.targetsize-44_altform-unplated.png**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="948f9-145">In diesem Beispiel ist das Symbol mit dem Namen **MYAPP_44x44.png** das Symbol, auf das Sie im ``Square44x44Logo`` -Logo-Attribut des Windows-App-Pakets verweisen.</span><span class="sxs-lookup"><span data-stu-id="948f9-145">In this example, the icon named **MYAPP_44x44.png** is the icon that you'll reference in the ``Square44x44Logo`` logo attribute of your Windows app package.</span></span>

3.  <span data-ttu-id="948f9-146">Legen Sie im Windows-App-Paket die ``BackgroundColor`` für jedes Symbol, das Sie transparent machen, fest.</span><span class="sxs-lookup"><span data-stu-id="948f9-146">In the Windows app package, set the ``BackgroundColor`` for every icon you are making transparent.</span></span>

4. <span data-ttu-id="948f9-147">Fahren Sie mit dem nächste Unterabschnitt fort, um eine neue Paketressourcendateien zu generieren.</span><span class="sxs-lookup"><span data-stu-id="948f9-147">Continue to the next subsection to generate a new Package Resource Index file.</span></span>

<a id="make-pri" />

### <a name="generate-a-package-resource-index-pri-file"></a><span data-ttu-id="948f9-148">Paketressourcendateien (Package Resource Index, PRI) generieren</span><span class="sxs-lookup"><span data-stu-id="948f9-148">Generate a Package Resource Index (PRI) file</span></span>

<span data-ttu-id="948f9-149">Wenn Sie zielbasierte Ressourcen erstellen, wie im vorherigen Abschnitt beschrieben, oder Sie ändern die visuellen Ressourcen Ihrer Anwendung, nachdem Sie das Paket erstellt haben, müssen Sie eine neue PRI-Datei generieren.</span><span class="sxs-lookup"><span data-stu-id="948f9-149">If you create target-based assets as described in the section above, or you modify any of the visual assets of your application after you've created the package, you'll have to generate a new PRI file.</span></span>

1.  <span data-ttu-id="948f9-150">Öffnen Sie eine **Developer-Eingabeaufforderung für VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="948f9-150">Open a **Developer Command Prompt for VS 2017**.</span></span>

    ![Developer-Eingabeaufforderung](images/desktop-to-uwp/developer-command-prompt.png)

2.  <span data-ttu-id="948f9-152">Ändern Sie das Verzeichnis in den Stammordner des Pakets, und erstellen Sie dann mit dem Befehl ``makepri createconfig /cf priconfig.xml /dq en-US`` eine priconfig.xml-Datei.</span><span class="sxs-lookup"><span data-stu-id="948f9-152">Change directory to the package's root folder, and then create a priconfig.xml file by running the command ``makepri createconfig /cf priconfig.xml /dq en-US``.</span></span>

5.  <span data-ttu-id="948f9-153">Erstellen Sie die resources.pri-Dateien mit dem Befehl ``makepri new /pr <PHYSICAL_PATH_TO_FOLDER> /cf <PHYSICAL_PATH_TO_FOLDER>\priconfig.xml``.</span><span class="sxs-lookup"><span data-stu-id="948f9-153">Create the resources.pri file(s) by using the command ``makepri new /pr <PHYSICAL_PATH_TO_FOLDER> /cf <PHYSICAL_PATH_TO_FOLDER>\priconfig.xml``.</span></span>

    <span data-ttu-id="948f9-154">Der Befehl für Ihre Anwendung könnte z. B. wie folgt aussehen: ``makepri new /pr c:\MYAPP /cf c:\MYAPP\priconfig.xml``.</span><span class="sxs-lookup"><span data-stu-id="948f9-154">For example, the command for your application might look like this: ``makepri new /pr c:\MYAPP /cf c:\MYAPP\priconfig.xml``.</span></span>

6.  <span data-ttu-id="948f9-155">Verpacken Sie Ihre Windows-App-Datei mithilfe der Anweisungen im nächsten Schritt.</span><span class="sxs-lookup"><span data-stu-id="948f9-155">Package your Windows app package by using the instructions in the next step.</span></span>

<a id="make-appx" />

## <a name="generate-a-windows-app-package"></a><span data-ttu-id="948f9-156">Erstellen eines Windows-App-Pakets</span><span class="sxs-lookup"><span data-stu-id="948f9-156">Generate a Windows app package</span></span>

<span data-ttu-id="948f9-157">Verwenden Sie **MakeAppx.exe**, um ein Windows-App-Paket für Ihr Projekt zu generieren.</span><span class="sxs-lookup"><span data-stu-id="948f9-157">Use **MakeAppx.exe** to generate a Windows app package for your project.</span></span> <span data-ttu-id="948f9-158">Ist es mit im Windows10 SDK enthalten, und wenn Sie Visual Studio installiert haben, können Sie ganz einfach über Developer-Eingabeaufforderung für Visual Studio zugreifen.</span><span class="sxs-lookup"><span data-stu-id="948f9-158">It's included with the Windows 10 SDK, and if you have Visual Studio installed, it can be easily accessed through the Developer Command Prompt for your Visual Studio version.</span></span>

<span data-ttu-id="948f9-159">Weitere Informationen finden Sie in [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool)</span><span class="sxs-lookup"><span data-stu-id="948f9-159">See [Create an app package with the MakeAppx.exe tool](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool)</span></span>

## <a name="run-the-packaged-app"></a><span data-ttu-id="948f9-160">Ausführung der verpackten App</span><span class="sxs-lookup"><span data-stu-id="948f9-160">Run the packaged app</span></span>

<span data-ttu-id="948f9-161">Sie können Ihre Anwendung zu testen, lokal ohne Erwerb eines Zertifikats und signieren Sie es ausführen.</span><span class="sxs-lookup"><span data-stu-id="948f9-161">You can run your application to test it out locally without having to obtain a certificate and sign it.</span></span> <span data-ttu-id="948f9-162">Führen Sie einfach dieses PowerShell-Cmdlet aus:</span><span class="sxs-lookup"><span data-stu-id="948f9-162">Just run this PowerShell cmdlet:</span></span>

```Add-AppxPackage –Register AppxManifest.xml```

<span data-ttu-id="948f9-163">Ersetzen Sie zum Aktualisieren der EXE- oder DLL-Dateien Ihrer App die vorhandenen Dateien in Ihrem Paket durch die neuen, vergrößern Sie die Versionsnummer in der Datei „AppxManifest.xml“, und führen Sie den oben genannten Befehl erneut aus.</span><span class="sxs-lookup"><span data-stu-id="948f9-163">To update your app's .exe or .dll files, replace the existing files in your package with the new ones, increase the version number in AppxManifest.xml, and then run the above command again.</span></span>

> [!NOTE]
> <span data-ttu-id="948f9-164">Ein Anwendungspaket immer als interaktiver Benutzer ausgeführt wird, und jedes Laufwerk durch die Installation Ihres Anwendungspakets unter muss NTFS-Format formatiert werden.</span><span class="sxs-lookup"><span data-stu-id="948f9-164">A packaged application always runs as an interactive user, and any drive that you install your packaged application on to must be formatted to NTFS format.</span></span>

## <a name="next-steps"></a><span data-ttu-id="948f9-165">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="948f9-165">Next steps</span></span>

**<span data-ttu-id="948f9-166">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="948f9-166">Find answers to your questions</span></span>**

<span data-ttu-id="948f9-167">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="948f9-167">Have questions?</span></span> <span data-ttu-id="948f9-168">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="948f9-168">Ask us on Stack Overflow.</span></span> <span data-ttu-id="948f9-169">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Sie können [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D) Fragen dazu stellen.</span><span class="sxs-lookup"><span data-stu-id="948f9-169">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="948f9-170">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="948f9-170">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="948f9-171">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="948f9-171">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>

**<span data-ttu-id="948f9-172">Schrittweise Ausführung von Code / Suchen und Beheben von Problemen</span><span class="sxs-lookup"><span data-stu-id="948f9-172">Step through code / find and fix issues</span></span>**

<span data-ttu-id="948f9-173">Finden Sie unter [ausführen, Debuggen und testen eine verpackte desktop-Anwendung](desktop-to-uwp-debug.md)</span><span class="sxs-lookup"><span data-stu-id="948f9-173">See [Run, debug, and test a packaged desktop application](desktop-to-uwp-debug.md)</span></span>

**<span data-ttu-id="948f9-174">Signieren Sie Ihre Anwendung und verteilen Sie es</span><span class="sxs-lookup"><span data-stu-id="948f9-174">Sign your application and then distribute it</span></span>**

<span data-ttu-id="948f9-175">Finden Sie unter [Verteilen einer verpackten desktop-Anwendung](desktop-to-uwp-distribute.md)</span><span class="sxs-lookup"><span data-stu-id="948f9-175">See [Distribute a packaged desktop application](desktop-to-uwp-distribute.md)</span></span>
