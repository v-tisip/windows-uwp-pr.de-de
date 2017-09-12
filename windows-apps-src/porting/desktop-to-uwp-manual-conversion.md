---
author: normesta
Description: "Zeigt, wie Sie eine Windows-Desktopanwendung (z. B. Win32, WPF und Windows Forms) für Windows 10 manuell verpacken."
Search.Product: eADQiWindows 10XVcnh
title: "Verpacken Sie eine App manuell (Desktop-Brücke)"
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: e8c2a803-9803-47c5-b117-73c4af52c5b6
ms.openlocfilehash: e8a09b6e362662b9bb207117d8a3fcc905da6ef4
ms.sourcegitcommit: ae93435e1f9c010a054f55ed7d6bd2f268223957
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2017
---
# <a name="package-an-app-manually-desktop-bridge"></a><span data-ttu-id="330de-104">Verpacken Sie eine App manuell (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="330de-104">Package an app manually (Desktop Bridge)</span></span>

<span data-ttu-id="330de-105">In diesem Thema erfahren Sie, wie Sie Ihre App ohne Tools wie Visual Studio oder den Desktop App Converter (DAC) verpacken.</span><span class="sxs-lookup"><span data-stu-id="330de-105">This topic shows you how to package your app without using tools such as Visual Studio or the Desktop App Converter (DAC).</span></span>

<div style="float: left; padding: 10px">
    ![Manuelle Steuerung](images/desktop-to-uwp/manual-flow.png)
</div>

<span data-ttu-id="330de-107">Um Ihre App manuell zu verpacken, erstellen Sie eine Paketmanifestdatei, und führen Sie dann ein Befehlszeilentool aus, um ein Windows-App-Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="330de-107">To manually package your app, create a package manifest file, and then run a command line tool to generate a Windows app package.</span></span>

<span data-ttu-id="330de-108">Berücksichtigen Sie die manuelle Verpackung, wenn Sie Ihre App mithilfe des Befehls „Xcopy” installieren oder wenn Sie mit den durch Ihren App-Installer vorgenommenen Änderungen des Systems vertraut sind und eine genauere Kontrolle über den Prozess haben möchten.</span><span class="sxs-lookup"><span data-stu-id="330de-108">Consider manual packaging if you install your app by using the xcopy command, or you're familiar with the changes that your app's installer makes to the system and want more granular control over the process.</span></span>

<span data-ttu-id="330de-109">Wenn Sie sich nicht darüber sicher sind, welche Änderungen an das System durch Ihren Installer vorgenommen werden oder wenn Sie lieber automatisierte Tools für das Generieren Ihres Paketmanifestes verwenden möchten, sollten Sie eine [dieser](desktop-to-uwp-root.md#convert) Optionen erwägen.</span><span class="sxs-lookup"><span data-stu-id="330de-109">If you're uncertain about what changes your installer makes to the system, or if you'd rather use automated tools to generate your package manifest, consider any of [these](desktop-to-uwp-root.md#convert) options.</span></span>

## <a name="first-consider-how-youll-distribute-your-app"></a><span data-ttu-id="330de-110">Überlegen Sie zunächst, wie Sie Ihre App verteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="330de-110">First, consider how you'll distribute your app</span></span>
<span data-ttu-id="330de-111">Wenn Sie Ihre App im [Windows Store-](https://www.microsoft.com/store/apps) veröffentlichen möchten, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="330de-111">If you plan to publish your app to the [Windows Store](https://www.microsoft.com/store/apps), start by filling out [this form](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span></span> <span data-ttu-id="330de-112">Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess.</span><span class="sxs-lookup"><span data-stu-id="330de-112">Microsoft will contact you to start the onboarding process.</span></span> <span data-ttu-id="330de-113">Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um Ihre App zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="330de-113">As part of this process, you'll reserve a name in the store, and obtain information that you'll need to package your app.</span></span>

## <a name="create-a-package-manifest"></a><span data-ttu-id="330de-114">Erstellen eines Paketmanifests.</span><span class="sxs-lookup"><span data-stu-id="330de-114">Create a package manifest</span></span>

<span data-ttu-id="330de-115">Erstellen Sie eine Datei, nennen Sie sie **appxmanifest.xml**, und fügen Sie diese XML-Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="330de-115">Create a file, name it **appxmanifest.xml**, and then add this XML to it.</span></span>

<span data-ttu-id="330de-116">Es ist eine einfache Vorlage, die die vom Paket benötigten Elemente und Attribute enthält.</span><span class="sxs-lookup"><span data-stu-id="330de-116">It's a basic template that contains the elements and attributes that your package needs.</span></span> <span data-ttu-id="330de-117">Wir werden im nächsten Abschnittdie Werte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="330de-117">We'll add values to these in the next section.</span></span>

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

## <a name="fill-in-the-package-level-elements-of-your-file"></a><span data-ttu-id="330de-118">Füllen Sie die Paketelemente in der Datei aus.</span><span class="sxs-lookup"><span data-stu-id="330de-118">Fill in the package-level elements of your file</span></span>

<span data-ttu-id="330de-119">Geben Sie in diese Vorlage Informationen ein, die das Paket beschreiben.</span><span class="sxs-lookup"><span data-stu-id="330de-119">Fill in this template with information that describes your package.</span></span>

### <a name="identity-information"></a><span data-ttu-id="330de-120">Identitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="330de-120">Identity information</span></span>

<span data-ttu-id="330de-121">Hier ist ein Beispiel für ein **Identitäts**-Element mit Platzhaltertext für die Attribute.</span><span class="sxs-lookup"><span data-stu-id="330de-121">Here's an example **Identity** element with placeholder text for the attributes.</span></span> <span data-ttu-id="330de-122">Sie können das ``ProcessorArchitecture``-Attributs auf ``x64``oder ``x86`` festlegen.</span><span class="sxs-lookup"><span data-stu-id="330de-122">You can set the ``ProcessorArchitecture`` attribute to ``x64`` or ``x86``.</span></span>

```XML
<Identity Name="MyCompany.MySuite.MyApp"
          Version="1.0.0.0"
          Publisher="CN=MyCompany, O=MyCompany, L=MyCity, S=MyState, C=MyCountry"
                ProcessorArchitecture="x64">
```
> [!NOTE]
> <span data-ttu-id="330de-123">Wenn Sie den Namen Ihrer App im Windows Store reserviert haben, können Sie den Namen und Herausgeber mit dem Windows Dev Center-Dashboard abrufen.</span><span class="sxs-lookup"><span data-stu-id="330de-123">If you've reserved your app name in the Windows store, you can obtain the Name and Publisher by using the Windows Dev Center dashboard.</span></span> <span data-ttu-id="330de-124">Wenn Sie Ihre App auf andere Systeme querladen möchten, können Sie für diese Ihre eigenen Namen bereitstellen, sofern der von Ihnen gewählte Name des Herausgebers mit dem Namen des Zertifikats übereinstimmt, das Sie zum Signieren Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="330de-124">If you plan to sideload your app onto other systems, you can provide your own names for these as long as the publisher name that you choose matches the name on the certificate you use to sign your app.</span></span>

### <a name="properties"></a><span data-ttu-id="330de-125">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="330de-125">Properties</span></span>

<span data-ttu-id="330de-126">Das [Eigenschaften](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-properties)-Element hat 3 erforderliche untergeordnete Elemente.</span><span class="sxs-lookup"><span data-stu-id="330de-126">The [Properties](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-properties) element has 3 required child elements.</span></span> <span data-ttu-id="330de-127">Hier ist ein Beispiel für einen **Eigenschaften**-Knoten mit Platzhaltertext für die Elemente.</span><span class="sxs-lookup"><span data-stu-id="330de-127">Here is an example **Properties** node with placeholder text for the elements.</span></span> <span data-ttu-id="330de-128">Der **Anzeigename** ist der Name Ihrer App, den Sie im Store reservieren, für Apps, die in den Store hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="330de-128">The **DisplayName** is the name of your app that you reserve in the store, for apps which are uploaded to the store.</span></span>

```XML
<Properties>
  <DisplayName>MyApp</DisplayName>
  <PublisherDisplayName>MyCompany</PublisherDisplayName>
  <Logo>images\icon.png</Logo>
</Properties>
```

### <a name="resources"></a><span data-ttu-id="330de-129">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="330de-129">Resources</span></span>

<span data-ttu-id="330de-130">Hier ist ein Beispiel für einen [Ressourcen](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-resources)-Knoten.</span><span class="sxs-lookup"><span data-stu-id="330de-130">Here is an example [Resources](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-resources) node.</span></span>

```XML
<Resources>
  <Resource Language="en-us" />
</Resources>
```
### <a name="dependencies"></a><span data-ttu-id="330de-131">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="330de-131">Dependencies</span></span>

<span data-ttu-id="330de-132">Legen Sie für Desktop-Brücke-Apps die ``Name`` Attribute immer auf ``Windows.Desktop``.</span><span class="sxs-lookup"><span data-stu-id="330de-132">For desktop bridge apps, always set the ``Name`` attribute to ``Windows.Desktop``.</span></span>

```XML
<Dependencies>
<TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14316.0" MaxVersionTested="10.0.15063.0" />
</Dependencies>
```

### <a name="capabilities"></a><span data-ttu-id="330de-133">Funktionen</span><span class="sxs-lookup"><span data-stu-id="330de-133">Capabilities</span></span>
<span data-ttu-id="330de-134">Für Desktop-Brücke-Apps müssen Sie die ``runFullTrust``-Funktion hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="330de-134">For desktop bridge apps, you'll have to add the ``runFullTrust`` capability.</span></span>

```XML
<Capabilities>
  <rescap:Capability Name="runFullTrust"/>
</Capabilities>
```
## <a name="fill-in-the-application-level-elements"></a><span data-ttu-id="330de-135">Füllen Sie die Elemente auf Anwendungsebene aus.</span><span class="sxs-lookup"><span data-stu-id="330de-135">Fill in the application-level elements</span></span>

<span data-ttu-id="330de-136">Geben Sie in diese Vorlage Informationen ein, die Ihre App beschreiben.</span><span class="sxs-lookup"><span data-stu-id="330de-136">Fill in this template with information that describes your app.</span></span>

### <a name="application-element"></a><span data-ttu-id="330de-137">Anwendungselemente</span><span class="sxs-lookup"><span data-stu-id="330de-137">Application element</span></span>

<span data-ttu-id="330de-138">Für Desktop-Brücke-Apps sind die ``EntryPoint``-Attribute des Anwendungselements immer ``Windows.FullTrustApplication``.</span><span class="sxs-lookup"><span data-stu-id="330de-138">For desktop bridge apps, the ``EntryPoint`` attribute of the Application element is always ``Windows.FullTrustApplication``.</span></span>

```XML
<Applications>
  <Application Id="MyApp"     
        Executable="MyApp.exe" EntryPoint="Windows.FullTrustApplication">
   </Application>
</Applications>
```

### <a name="visual-elements"></a><span data-ttu-id="330de-139">Visuelle Elemente</span><span class="sxs-lookup"><span data-stu-id="330de-139">Visual elements</span></span>

<span data-ttu-id="330de-140">Hier ist ein Beispiel für einen [VisualElements](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements)-Knoten.</span><span class="sxs-lookup"><span data-stu-id="330de-140">Here is an example [VisualElements](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements) node.</span></span>

```XML
<uap:VisualElements
    BackgroundColor="#464646"
    DisplayName="My App"
    Square150x150Logo="images\icon.png"
    Square44x44Logo="images\small_icon.png"
    Description="A useful description" />
```

## <a name="optional-add-target-based-unplated-assets"></a><span data-ttu-id="330de-141">(Optional) Zielbasierte Ressourcen ohne Anpassung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="330de-141">(Optional) Add Target-based unplated assets</span></span>

<span data-ttu-id="330de-142">Zielbasierte Ressourcen gelten für Symbole und Kacheln, die in der Windows-Taskleiste, in der Aufgabenansicht, über ALT+TAB, in der Andockhilfe und in der unteren rechten Ecke von Startkacheln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="330de-142">Target-based assets are for icons and tiles that appear on the Windows taskbar, task view, ALT+TAB, snap-assist, and the lower-right corner of Start tiles.</span></span> <span data-ttu-id="330de-143">Erhalten Sie [hier](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-app-assets#target-based-assets) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="330de-143">You can read more about them [here](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-app-assets#target-based-assets).</span></span>

1. <span data-ttu-id="330de-144">Rufen Sie die richtigen 44x44-Bilder ab, und kopieren Sie sie dann in den Ordner, der Ihre Bilder (d.h. Ressourcen) enthält.</span><span class="sxs-lookup"><span data-stu-id="330de-144">Obtain the correct 44x44 images and then copy them into the folder that contains your images (i.e., Assets).</span></span>

2. <span data-ttu-id="330de-145">Erstellen Sie für jedes 44x44-Bild eine Kopie im selben Ordner, und hängen Sie **.targetsize-44_altform-unplated** an den Dateinamen an.</span><span class="sxs-lookup"><span data-stu-id="330de-145">For each 44x44 image, create a copy in the same folder and append **.targetsize-44_altform-unplated** to the file name.</span></span> <span data-ttu-id="330de-146">Sie sollten zwei Kopien von jedem Symbol haben, jeweils spezifisch benannt.</span><span class="sxs-lookup"><span data-stu-id="330de-146">You should have two copies of each icon, each named in a specific way.</span></span> <span data-ttu-id="330de-147">Nach Abschluss des Prozesses könnte Ihr Ressourcen-Ordner beispielsweise **MYAPP_44x44.png** und **MYAPP_44x44.targetsize-44_altform-unplated.png** enthalten.</span><span class="sxs-lookup"><span data-stu-id="330de-147">For example, after completing the process, your assets folder might contain **MYAPP_44x44.png** and **MYAPP_44x44.targetsize-44_altform-unplated.png**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="330de-148">In diesem Beispiel ist das Symbol mit dem Namen **MYAPP_44x44.png** das Symbol, auf das Sie im ``Square44x44Logo`` -Logo-Attribut des Windows-App-Pakets verweisen.</span><span class="sxs-lookup"><span data-stu-id="330de-148">In this example, the icon named **MYAPP_44x44.png** is the icon that you'll reference in the ``Square44x44Logo`` logo attribute of your Windows app package.</span></span>

3.  <span data-ttu-id="330de-149">Legen Sie im Windows-App-Paket die ``BackgroundColor`` für jedes Symbol, das Sie transparent machen, fest.</span><span class="sxs-lookup"><span data-stu-id="330de-149">In the Windows app package, set the ``BackgroundColor`` for every icon you are making transparent.</span></span>

4.  <span data-ttu-id="330de-150">Öffnen Sie CMD, ändern Sie das Verzeichnis in den Stammordner des Pakets, und erstellen Sie dann mit dem Befehl ``makepri createconfig /cf priconfig.xml /dq en-US`` eine priconfig.xml-Datei.</span><span class="sxs-lookup"><span data-stu-id="330de-150">Open CMD, change directory to the package's root folder, and then create a priconfig.xml file by running the command ``makepri createconfig /cf priconfig.xml /dq en-US``.</span></span>

5.  <span data-ttu-id="330de-151">Erstellen Sie die resources.pri-Dateien mit dem Befehl ``makepri new /pr <PHYSICAL_PATH_TO_FOLDER> /cf <PHYSICAL_PATH_TO_FOLDER>\priconfig.xml``.</span><span class="sxs-lookup"><span data-stu-id="330de-151">Create the resources.pri file(s) by using the command ``makepri new /pr <PHYSICAL_PATH_TO_FOLDER> /cf <PHYSICAL_PATH_TO_FOLDER>\priconfig.xml``.</span></span>

    <span data-ttu-id="330de-152">Der Befehl für Ihre App könnte beispielsweise wie folgt aussehen: ``makepri new /pr c:\MYAPP /cf c:\MYAPP\priconfig.xml``.</span><span class="sxs-lookup"><span data-stu-id="330de-152">For example, the command for your app might look like this: ``makepri new /pr c:\MYAPP /cf c:\MYAPP\priconfig.xml``.</span></span>

6.  <span data-ttu-id="330de-153">Verpacken Sie Ihre Windows-App-Datei mithilfe der Anweisungen im nächsten Schritt, um die Ergebnisse anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="330de-153">Package your Windows app package by using the instructions in the next step to see the results.</span></span>

<span id="make-appx" />
## <a name="generate-a-windows-app-package"></a><span data-ttu-id="330de-154">Erstellen eines Windows-App-Pakets</span><span class="sxs-lookup"><span data-stu-id="330de-154">Generate a Windows app package</span></span>

<span data-ttu-id="330de-155">Verwenden Sie **MakeAppx.exe**, um ein Windows-App-Paket für Ihr Projekt zu generieren.</span><span class="sxs-lookup"><span data-stu-id="330de-155">Use **MakeAppx.exe** to generate a Windows app package for your project.</span></span> <span data-ttu-id="330de-156">Ist es mit im Windows10 SDK enthalten, und wenn Sie Visual Studio installiert haben, können Sie ganz einfach über Developer-Eingabeaufforderung für Visual Studio zugreifen.</span><span class="sxs-lookup"><span data-stu-id="330de-156">It's included with the Windows 10 SDK, and if you have Visual Studio installed, it can be easily accessed through the Developer Command Prompt for your Visual Studio version.</span></span>

<span data-ttu-id="330de-157">Weitere Informationen finden Sie in [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool)</span><span class="sxs-lookup"><span data-stu-id="330de-157">See [Create an app package with the MakeAppx.exe tool](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool)</span></span>

## <a name="run-the-packaged-app"></a><span data-ttu-id="330de-158">Ausführung der verpackten App</span><span class="sxs-lookup"><span data-stu-id="330de-158">Run the packaged app</span></span>

<span data-ttu-id="330de-159">Sie können Ihre App lokal testen, ohne dass Sie ein Zertifikat benötigen und es signieren müssen.</span><span class="sxs-lookup"><span data-stu-id="330de-159">You can run your app to test it out locally without having to obtain a certificate and sign it.</span></span> <span data-ttu-id="330de-160">Führen Sie einfach dieses PowerShell-Cmdlet aus:</span><span class="sxs-lookup"><span data-stu-id="330de-160">Just run this PowerShell cmdlet:</span></span>

```Add-AppxPackage –Register AppxManifest.xml```

<span data-ttu-id="330de-161">Ersetzen Sie zum Aktualisieren der EXE- oder DLL-Dateien Ihrer App die vorhandenen Dateien in Ihrem Paket durch die neuen, vergrößern Sie die Versionsnummer in der Datei „AppxManifest.xml“, und führen Sie den oben genannten Befehl erneut aus.</span><span class="sxs-lookup"><span data-stu-id="330de-161">To update your app's .exe or .dll files, replace the existing files in your package with the new ones, increase the version number in AppxManifest.xml, and then run the above command again.</span></span>

> [!NOTE]
> <span data-ttu-id="330de-162">Eine verpackte App wird immer als ein interaktiver Benutzer ausgeführt, und jedes Laufwerk, auf das Sie die verpackte App installieren, muss auf das NTFS-Format formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="330de-162">A packaged app always runs as an interactive user, and any drive that you install your packaged app on to must be formatted to NTFS format.</span></span>

## <a name="next-steps"></a><span data-ttu-id="330de-163">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="330de-163">Next steps</span></span>

**<span data-ttu-id="330de-164">Schrittweise Ausführung von Code / Suchen und Beheben von Problemen</span><span class="sxs-lookup"><span data-stu-id="330de-164">Step through code / find and fix issues</span></span>**

<span data-ttu-id="330de-165">Siehe [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md)</span><span class="sxs-lookup"><span data-stu-id="330de-165">See [Run, debug, and test a packaged desktop app (Desktop Bridge)](desktop-to-uwp-debug.md)</span></span>

**<span data-ttu-id="330de-166">Signieren Sie Ihre App, und verteilen Sie sie</span><span class="sxs-lookup"><span data-stu-id="330de-166">Sign your app and then distribute it</span></span>**

<span data-ttu-id="330de-167">Weitere Informationen finden Sie in [Verteilen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)</span><span class="sxs-lookup"><span data-stu-id="330de-167">See [Distribute a packaged desktop app (Desktop Bridge)](desktop-to-uwp-distribute.md)</span></span>

**<span data-ttu-id="330de-168">Antworten auf bestimmte Fragen finden</span><span class="sxs-lookup"><span data-stu-id="330de-168">Find answers to specific questions</span></span>**

<span data-ttu-id="330de-169">Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="330de-169">Our team monitors these [StackOverflow tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

**<span data-ttu-id="330de-170">Geben Sie Feedback zu diesem Artikel</span><span class="sxs-lookup"><span data-stu-id="330de-170">Give feedback about this article</span></span>**

<span data-ttu-id="330de-171">Verwenden Sie den Kommentarabschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="330de-171">Use the comments section below.</span></span>
