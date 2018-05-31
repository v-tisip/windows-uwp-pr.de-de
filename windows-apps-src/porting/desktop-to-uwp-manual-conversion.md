---
author: normesta
Description: Shows how to manually package a Windows desktop application (like Win32, WPF, and Windows Forms) for Windows 10.
Search.Product: eADQiWindows 10XVcnh
title: Manuelles Verpacken einer App (Desktop-Brücke)
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: e8c2a803-9803-47c5-b117-73c4af52c5b6
ms.localizationpriority: medium
ms.openlocfilehash: 81d5b9b0b52ef0f7529b277215e7fe0b95683f0a
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1689766"
---
# <a name="package-an-app-manually-desktop-bridge"></a><span data-ttu-id="ff312-103">Verpacken Sie eine App manuell (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="ff312-103">Package an app manually (Desktop Bridge)</span></span>

<span data-ttu-id="ff312-104">In diesem Thema erfahren Sie, wie Sie Ihre App ohne Tools wie Visual Studio oder den Desktop App Converter (DAC) verpacken.</span><span class="sxs-lookup"><span data-stu-id="ff312-104">This topic shows you how to package your app without using tools such as Visual Studio or the Desktop App Converter (DAC).</span></span>

<span data-ttu-id="ff312-105">Um Ihre App manuell zu verpacken, erstellen Sie eine Paketmanifestdatei, und führen Sie dann ein Befehlszeilentool aus, um ein Windows-App-Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="ff312-105">To manually package your app, create a package manifest file, and then run a command line tool to generate a Windows app package.</span></span>

<span data-ttu-id="ff312-106">Berücksichtigen Sie die manuelle Verpackung, wenn Sie Ihre App mithilfe des Befehls „Xcopy” installieren oder wenn Sie mit den durch Ihren App-Installer vorgenommenen Änderungen des Systems vertraut sind und eine genauere Kontrolle über den Prozess haben möchten.</span><span class="sxs-lookup"><span data-stu-id="ff312-106">Consider manual packaging if you install your app by using the xcopy command, or you're familiar with the changes that your app's installer makes to the system and want more granular control over the process.</span></span>

<span data-ttu-id="ff312-107">Wenn Sie sich nicht darüber sicher sind, welche Änderungen an das System durch Ihren Installer vorgenommen werden oder wenn Sie lieber automatisierte Tools für das Generieren Ihres Paketmanifestes verwenden möchten, sollten Sie eine [dieser](desktop-to-uwp-root.md#convert) Optionen erwägen.</span><span class="sxs-lookup"><span data-stu-id="ff312-107">If you're uncertain about what changes your installer makes to the system, or if you'd rather use automated tools to generate your package manifest, consider any of [these](desktop-to-uwp-root.md#convert) options.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ff312-108">Der Desktop-Brücke wurde in Windows10, Version 1607, eingeführt und kann nur in Projekten für das Windows10 Anniversary Update (10.0; Build 14393) oder einer neueren Version in Visual Studio verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ff312-108">The Desktop Bridge was introduced in Windows 10, version 1607, and it can only be used in projects that target Windows 10 Anniversary Update (10.0; Build 14393) or a later release in Visual Studio.</span></span>

## <a name="first-consider-how-youll-distribute-your-app"></a><span data-ttu-id="ff312-109">Überlegen Sie zunächst, wie Sie Ihre App verteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="ff312-109">First, consider how you'll distribute your app</span></span>
<span data-ttu-id="ff312-110">Wenn Sie Ihre App im [Microsoft Store](https://www.microsoft.com/store/apps) veröffentlichen möchten, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="ff312-110">If you plan to publish your app to the [Microsoft Store](https://www.microsoft.com/store/apps), start by filling out [this form](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span></span> <span data-ttu-id="ff312-111">Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess.</span><span class="sxs-lookup"><span data-stu-id="ff312-111">Microsoft will contact you to start the onboarding process.</span></span> <span data-ttu-id="ff312-112">Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um Ihre App zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="ff312-112">As part of this process, you'll reserve a name in the store, and obtain information that you'll need to package your app.</span></span>

## <a name="create-a-package-manifest"></a><span data-ttu-id="ff312-113">Erstellen eines Paketmanifests.</span><span class="sxs-lookup"><span data-stu-id="ff312-113">Create a package manifest</span></span>

<span data-ttu-id="ff312-114">Erstellen Sie eine Datei, nennen Sie sie **appxmanifest.xml**, und fügen Sie diese XML-Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="ff312-114">Create a file, name it **appxmanifest.xml**, and then add this XML to it.</span></span>

<span data-ttu-id="ff312-115">Es ist eine einfache Vorlage, die die vom Paket benötigten Elemente und Attribute enthält.</span><span class="sxs-lookup"><span data-stu-id="ff312-115">It's a basic template that contains the elements and attributes that your package needs.</span></span> <span data-ttu-id="ff312-116">Wir werden im nächsten Abschnittdie Werte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ff312-116">We'll add values to these in the next section.</span></span>

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

## <a name="fill-in-the-package-level-elements-of-your-file"></a><span data-ttu-id="ff312-117">Füllen Sie die Paketelemente in der Datei aus.</span><span class="sxs-lookup"><span data-stu-id="ff312-117">Fill in the package-level elements of your file</span></span>

<span data-ttu-id="ff312-118">Geben Sie in diese Vorlage Informationen ein, die das Paket beschreiben.</span><span class="sxs-lookup"><span data-stu-id="ff312-118">Fill in this template with information that describes your package.</span></span>

### <a name="identity-information"></a><span data-ttu-id="ff312-119">Identitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="ff312-119">Identity information</span></span>

<span data-ttu-id="ff312-120">Hier ist ein Beispiel für ein **Identitäts**-Element mit Platzhaltertext für die Attribute.</span><span class="sxs-lookup"><span data-stu-id="ff312-120">Here's an example **Identity** element with placeholder text for the attributes.</span></span> <span data-ttu-id="ff312-121">Sie können das ``ProcessorArchitecture``-Attributs auf ``x64``oder ``x86`` festlegen.</span><span class="sxs-lookup"><span data-stu-id="ff312-121">You can set the ``ProcessorArchitecture`` attribute to ``x64`` or ``x86``.</span></span>

```XML
<Identity Name="MyCompany.MySuite.MyApp"
          Version="1.0.0.0"
          Publisher="CN=MyCompany, O=MyCompany, L=MyCity, S=MyState, C=MyCountry"
                ProcessorArchitecture="x64">
```
> [!NOTE]
> <span data-ttu-id="ff312-122">Wenn Sie den Namen Ihrer App im Windows Store reserviert haben, können Sie den Namen und Herausgeber mit dem Windows Dev Center-Dashboard abrufen.</span><span class="sxs-lookup"><span data-stu-id="ff312-122">If you've reserved your app name in the Windows store, you can obtain the Name and Publisher by using the Windows Dev Center dashboard.</span></span> <span data-ttu-id="ff312-123">Wenn Sie Ihre App auf andere Systeme querladen möchten, können Sie für diese Ihre eigenen Namen bereitstellen, sofern der von Ihnen gewählte Name des Herausgebers mit dem Namen des Zertifikats übereinstimmt, das Sie zum Signieren Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="ff312-123">If you plan to sideload your app onto other systems, you can provide your own names for these as long as the publisher name that you choose matches the name on the certificate you use to sign your app.</span></span>

### <a name="properties"></a><span data-ttu-id="ff312-124">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ff312-124">Properties</span></span>

<span data-ttu-id="ff312-125">Das [Eigenschaften](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-properties)-Element hat 3 erforderliche untergeordnete Elemente.</span><span class="sxs-lookup"><span data-stu-id="ff312-125">The [Properties](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-properties) element has 3 required child elements.</span></span> <span data-ttu-id="ff312-126">Hier ist ein Beispiel für einen **Eigenschaften**-Knoten mit Platzhaltertext für die Elemente.</span><span class="sxs-lookup"><span data-stu-id="ff312-126">Here is an example **Properties** node with placeholder text for the elements.</span></span> <span data-ttu-id="ff312-127">Der **Anzeigename** ist der Name Ihrer App, den Sie im Store reservieren, für Apps, die in den Store hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="ff312-127">The **DisplayName** is the name of your app that you reserve in the store, for apps which are uploaded to the store.</span></span>

```XML
<Properties>
  <DisplayName>MyApp</DisplayName>
  <PublisherDisplayName>MyCompany</PublisherDisplayName>
  <Logo>images\icon.png</Logo>
</Properties>
```

### <a name="resources"></a><span data-ttu-id="ff312-128">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="ff312-128">Resources</span></span>

<span data-ttu-id="ff312-129">Hier ist ein Beispiel für einen [Ressourcen](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-resources)-Knoten.</span><span class="sxs-lookup"><span data-stu-id="ff312-129">Here is an example [Resources](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-resources) node.</span></span>

```XML
<Resources>
  <Resource Language="en-us" />
</Resources>
```
### <a name="dependencies"></a><span data-ttu-id="ff312-130">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="ff312-130">Dependencies</span></span>

<span data-ttu-id="ff312-131">Legen Sie für Desktop-Brücke-Apps die ``Name`` Attribute immer auf ``Windows.Desktop``.</span><span class="sxs-lookup"><span data-stu-id="ff312-131">For desktop bridge apps, always set the ``Name`` attribute to ``Windows.Desktop``.</span></span>

```XML
<Dependencies>
<TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14316.0" MaxVersionTested="10.0.15063.0" />
</Dependencies>
```

### <a name="capabilities"></a><span data-ttu-id="ff312-132">Funktionen</span><span class="sxs-lookup"><span data-stu-id="ff312-132">Capabilities</span></span>
<span data-ttu-id="ff312-133">Für Desktop-Brücke-Apps müssen Sie die ``runFullTrust``-Funktion hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ff312-133">For desktop bridge apps, you'll have to add the ``runFullTrust`` capability.</span></span>

```XML
<Capabilities>
  <rescap:Capability Name="runFullTrust"/>
</Capabilities>
```
## <a name="fill-in-the-application-level-elements"></a><span data-ttu-id="ff312-134">Füllen Sie die Elemente auf Anwendungsebene aus.</span><span class="sxs-lookup"><span data-stu-id="ff312-134">Fill in the application-level elements</span></span>

<span data-ttu-id="ff312-135">Geben Sie in diese Vorlage Informationen ein, die Ihre App beschreiben.</span><span class="sxs-lookup"><span data-stu-id="ff312-135">Fill in this template with information that describes your app.</span></span>

### <a name="application-element"></a><span data-ttu-id="ff312-136">Anwendungselemente</span><span class="sxs-lookup"><span data-stu-id="ff312-136">Application element</span></span>

<span data-ttu-id="ff312-137">Für Desktop-Brücke-Apps sind die ``EntryPoint``-Attribute des Anwendungselements immer ``Windows.FullTrustApplication``.</span><span class="sxs-lookup"><span data-stu-id="ff312-137">For desktop bridge apps, the ``EntryPoint`` attribute of the Application element is always ``Windows.FullTrustApplication``.</span></span>

```XML
<Applications>
  <Application Id="MyApp"     
        Executable="MyApp.exe" EntryPoint="Windows.FullTrustApplication">
   </Application>
</Applications>
```

### <a name="visual-elements"></a><span data-ttu-id="ff312-138">Visuelle Elemente</span><span class="sxs-lookup"><span data-stu-id="ff312-138">Visual elements</span></span>

<span data-ttu-id="ff312-139">Hier ist ein Beispiel für einen [VisualElements](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements)-Knoten.</span><span class="sxs-lookup"><span data-stu-id="ff312-139">Here is an example [VisualElements](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements) node.</span></span>

```XML
<uap:VisualElements
    BackgroundColor="#464646"
    DisplayName="My App"
    Square150x150Logo="images\icon.png"
    Square44x44Logo="images\small_icon.png"
    Description="A useful description" />
```
<a id="target-based-assets" />

## <a name="optional-add-target-based-unplated-assets"></a><span data-ttu-id="ff312-140">(Optional) Zielbasierte Ressourcen ohne Anpassung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ff312-140">(Optional) Add Target-based unplated assets</span></span>

<span data-ttu-id="ff312-141">Zielbasierte Ressourcen gelten für Symbole und Kacheln, die in der Windows-Taskleiste, in der Aufgabenansicht, über ALT+TAB, in der Andockhilfe und in der unteren rechten Ecke von Startkacheln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ff312-141">Target-based assets are for icons and tiles that appear on the Windows taskbar, task view, ALT+TAB, snap-assist, and the lower-right corner of Start tiles.</span></span> <span data-ttu-id="ff312-142">Erhalten Sie [hier](https://docs.microsoft.com/windows/uwp/shell/tiles-and-notifications/app-assets#target-based-assets) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="ff312-142">You can read more about them [here](https://docs.microsoft.com/windows/uwp/shell/tiles-and-notifications/app-assets#target-based-assets).</span></span>

1. <span data-ttu-id="ff312-143">Rufen Sie die richtigen 44x44-Bilder ab, und kopieren Sie sie dann in den Ordner, der Ihre Bilder (d.h. Ressourcen) enthält.</span><span class="sxs-lookup"><span data-stu-id="ff312-143">Obtain the correct 44x44 images and then copy them into the folder that contains your images (i.e., Assets).</span></span>

2. <span data-ttu-id="ff312-144">Erstellen Sie für jedes 44x44-Bild eine Kopie im selben Ordner, und hängen Sie **.targetsize-44_altform-unplated** an den Dateinamen an.</span><span class="sxs-lookup"><span data-stu-id="ff312-144">For each 44x44 image, create a copy in the same folder and append **.targetsize-44_altform-unplated** to the file name.</span></span> <span data-ttu-id="ff312-145">Sie sollten zwei Kopien von jedem Symbol haben, jeweils spezifisch benannt.</span><span class="sxs-lookup"><span data-stu-id="ff312-145">You should have two copies of each icon, each named in a specific way.</span></span> <span data-ttu-id="ff312-146">Nach Abschluss des Prozesses könnte Ihr Ressourcen-Ordner beispielsweise **MYAPP_44x44.png** und **MYAPP_44x44.targetsize-44_altform-unplated.png** enthalten.</span><span class="sxs-lookup"><span data-stu-id="ff312-146">For example, after completing the process, your assets folder might contain **MYAPP_44x44.png** and **MYAPP_44x44.targetsize-44_altform-unplated.png**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="ff312-147">In diesem Beispiel ist das Symbol mit dem Namen **MYAPP_44x44.png** das Symbol, auf das Sie im ``Square44x44Logo`` -Logo-Attribut des Windows-App-Pakets verweisen.</span><span class="sxs-lookup"><span data-stu-id="ff312-147">In this example, the icon named **MYAPP_44x44.png** is the icon that you'll reference in the ``Square44x44Logo`` logo attribute of your Windows app package.</span></span>

3.  <span data-ttu-id="ff312-148">Legen Sie im Windows-App-Paket die ``BackgroundColor`` für jedes Symbol, das Sie transparent machen, fest.</span><span class="sxs-lookup"><span data-stu-id="ff312-148">In the Windows app package, set the ``BackgroundColor`` for every icon you are making transparent.</span></span>

4. <span data-ttu-id="ff312-149">Fahren Sie mit dem nächste Unterabschnitt fort, um eine neue Paketressourcendateien zu generieren.</span><span class="sxs-lookup"><span data-stu-id="ff312-149">Continue to the next subsection to generate a new Package Resource Index file.</span></span>

<a id="make-pri" />

### <a name="generate-a-package-resource-index-pri-file"></a><span data-ttu-id="ff312-150">Paketressourcendateien (Package Resource Index, PRI) generieren</span><span class="sxs-lookup"><span data-stu-id="ff312-150">Generate a Package Resource Index (PRI) file</span></span>

<span data-ttu-id="ff312-151">Wenn Sie zielbasierte Ressourcen erstellen, wie im vorherigen Abschnitt beschrieben, oder Sie die visuellen Ressourcen Ihrer App nach der Erstellung des Pakets ändern, müssen Sie eine neue PRI-Datei generieren.</span><span class="sxs-lookup"><span data-stu-id="ff312-151">If you create target-based assets as described in the section above, or you modify any of the visual assets of your app after you've created the package, you'll have to generate a new PRI file.</span></span>

1.  <span data-ttu-id="ff312-152">Öffnen Sie eine **Developer-Eingabeaufforderung für VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="ff312-152">Open a **Developer Command Prompt for VS 2017**.</span></span>

    ![Developer-Eingabeaufforderung](images/desktop-to-uwp/developer-command-prompt.png)

2.  <span data-ttu-id="ff312-154">Ändern Sie das Verzeichnis in den Stammordner des Pakets, und erstellen Sie dann mit dem Befehl ``makepri createconfig /cf priconfig.xml /dq en-US`` eine priconfig.xml-Datei.</span><span class="sxs-lookup"><span data-stu-id="ff312-154">Change directory to the package's root folder, and then create a priconfig.xml file by running the command ``makepri createconfig /cf priconfig.xml /dq en-US``.</span></span>

5.  <span data-ttu-id="ff312-155">Erstellen Sie die resources.pri-Dateien mit dem Befehl ``makepri new /pr <PHYSICAL_PATH_TO_FOLDER> /cf <PHYSICAL_PATH_TO_FOLDER>\priconfig.xml``.</span><span class="sxs-lookup"><span data-stu-id="ff312-155">Create the resources.pri file(s) by using the command ``makepri new /pr <PHYSICAL_PATH_TO_FOLDER> /cf <PHYSICAL_PATH_TO_FOLDER>\priconfig.xml``.</span></span>

    <span data-ttu-id="ff312-156">Der Befehl für Ihre App könnte beispielsweise wie folgt aussehen: ``makepri new /pr c:\MYAPP /cf c:\MYAPP\priconfig.xml``.</span><span class="sxs-lookup"><span data-stu-id="ff312-156">For example, the command for your app might look like this: ``makepri new /pr c:\MYAPP /cf c:\MYAPP\priconfig.xml``.</span></span>

6.  <span data-ttu-id="ff312-157">Verpacken Sie Ihre Windows-App-Datei mithilfe der Anweisungen im nächsten Schritt.</span><span class="sxs-lookup"><span data-stu-id="ff312-157">Package your Windows app package by using the instructions in the next step.</span></span>

<a id="make-appx" />

## <a name="generate-a-windows-app-package"></a><span data-ttu-id="ff312-158">Erstellen eines Windows-App-Pakets</span><span class="sxs-lookup"><span data-stu-id="ff312-158">Generate a Windows app package</span></span>

<span data-ttu-id="ff312-159">Verwenden Sie **MakeAppx.exe**, um ein Windows-App-Paket für Ihr Projekt zu generieren.</span><span class="sxs-lookup"><span data-stu-id="ff312-159">Use **MakeAppx.exe** to generate a Windows app package for your project.</span></span> <span data-ttu-id="ff312-160">Ist es mit im Windows10 SDK enthalten, und wenn Sie Visual Studio installiert haben, können Sie ganz einfach über Developer-Eingabeaufforderung für Visual Studio zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ff312-160">It's included with the Windows 10 SDK, and if you have Visual Studio installed, it can be easily accessed through the Developer Command Prompt for your Visual Studio version.</span></span>

<span data-ttu-id="ff312-161">Weitere Informationen finden Sie in [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool)</span><span class="sxs-lookup"><span data-stu-id="ff312-161">See [Create an app package with the MakeAppx.exe tool](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool)</span></span>

## <a name="run-the-packaged-app"></a><span data-ttu-id="ff312-162">Ausführung der verpackten App</span><span class="sxs-lookup"><span data-stu-id="ff312-162">Run the packaged app</span></span>

<span data-ttu-id="ff312-163">Sie können Ihre App lokal testen, ohne dass Sie ein Zertifikat benötigen und es signieren müssen.</span><span class="sxs-lookup"><span data-stu-id="ff312-163">You can run your app to test it out locally without having to obtain a certificate and sign it.</span></span> <span data-ttu-id="ff312-164">Führen Sie einfach dieses PowerShell-Cmdlet aus:</span><span class="sxs-lookup"><span data-stu-id="ff312-164">Just run this PowerShell cmdlet:</span></span>

```Add-AppxPackage –Register AppxManifest.xml```

<span data-ttu-id="ff312-165">Ersetzen Sie zum Aktualisieren der EXE- oder DLL-Dateien Ihrer App die vorhandenen Dateien in Ihrem Paket durch die neuen, vergrößern Sie die Versionsnummer in der Datei „AppxManifest.xml“, und führen Sie den oben genannten Befehl erneut aus.</span><span class="sxs-lookup"><span data-stu-id="ff312-165">To update your app's .exe or .dll files, replace the existing files in your package with the new ones, increase the version number in AppxManifest.xml, and then run the above command again.</span></span>

> [!NOTE]
> <span data-ttu-id="ff312-166">Eine verpackte App wird immer als ein interaktiver Benutzer ausgeführt, und jedes Laufwerk, auf das Sie die verpackte App installieren, muss auf das NTFS-Format formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="ff312-166">A packaged app always runs as an interactive user, and any drive that you install your packaged app on to must be formatted to NTFS format.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ff312-167">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="ff312-167">Next steps</span></span>

**<span data-ttu-id="ff312-168">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="ff312-168">Find answers to your questions</span></span>**

<span data-ttu-id="ff312-169">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="ff312-169">Have questions?</span></span> <span data-ttu-id="ff312-170">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="ff312-170">Ask us on Stack Overflow.</span></span> <span data-ttu-id="ff312-171">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Sie können [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D) Fragen dazu stellen.</span><span class="sxs-lookup"><span data-stu-id="ff312-171">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="ff312-172">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="ff312-172">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="ff312-173">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="ff312-173">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>

**<span data-ttu-id="ff312-174">Schrittweise Ausführung von Code / Suchen und Beheben von Problemen</span><span class="sxs-lookup"><span data-stu-id="ff312-174">Step through code / find and fix issues</span></span>**

<span data-ttu-id="ff312-175">Siehe [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md)</span><span class="sxs-lookup"><span data-stu-id="ff312-175">See [Run, debug, and test a packaged desktop app (Desktop Bridge)](desktop-to-uwp-debug.md)</span></span>

**<span data-ttu-id="ff312-176">Signieren Sie Ihre App, und verteilen Sie sie</span><span class="sxs-lookup"><span data-stu-id="ff312-176">Sign your app and then distribute it</span></span>**

<span data-ttu-id="ff312-177">Weitere Informationen finden Sie in [Verteilen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)</span><span class="sxs-lookup"><span data-stu-id="ff312-177">See [Distribute a packaged desktop app (Desktop Bridge)](desktop-to-uwp-distribute.md)</span></span>
