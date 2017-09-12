---
author: normesta
Description: "Dieser Artikel enthält bekannte Probleme mit der Desktop-Brücke."
Search.Product: eADQiWindows 10XVcnh
title: "Bekannte Probleme (Desktop-Brücke)"
ms.author: normesta
ms.date: 07/18/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 71f8ffcb-8a99-4214-ae83-2d4b718a750e
ms.openlocfilehash: bf0e81d4a6ff7bd091f25963b1cf26cdecc93636
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="known-issues-desktop-bridge"></a><span data-ttu-id="637c0-104">Bekannte Probleme (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="637c0-104">Known Issues (Desktop Bridge)</span></span>

<span data-ttu-id="637c0-105">Dieser Artikel enthält bekannte Probleme mit der Desktop-Brücke.</span><span class="sxs-lookup"><span data-stu-id="637c0-105">This article contains known issues with the Desktop Bridge.</span></span>

## <a name="blue-screen-with-error-code-0x139-kernelsecuritycheckfailure"></a><span data-ttu-id="637c0-106">Blauer Bildschirm mit dem Fehlercode 0x139 (KERNEL_SECURITY_CHECK_FAILURE)</span><span class="sxs-lookup"><span data-stu-id="637c0-106">Blue screen with error code 0x139 (KERNEL_SECURITY_CHECK_FAILURE)</span></span>

<span data-ttu-id="637c0-107">Nach dem Installieren oder Starten bestimmter Apps aus dem Windows Store wird Ihr Computer unter Umständen unerwartet mit folgendem Fehler neu gestartet: **0x139 (KERNEL\_SECURITY\_CHECK\_ FAILURE)**.</span><span class="sxs-lookup"><span data-stu-id="637c0-107">After installing or launching certain apps from the Windows Store, your machine may unexpectedly reboot with the error: **0x139 (KERNEL\_SECURITY\_CHECK\_ FAILURE)**.</span></span>

<span data-ttu-id="637c0-108">Bekannte betroffene Apps: Kodi, JT2Go, Ear Trumpet, Teslagrad usw.</span><span class="sxs-lookup"><span data-stu-id="637c0-108">Known affected apps include Kodi, JT2Go, Ear Trumpet, Teslagrad, and others.</span></span>

<span data-ttu-id="637c0-109">Am 27.10.2016 wurde ein [Windows-Update (Version 14393.351 - KB3197954)](https://support.microsoft.com/kb/3197954) veröffentlich, das wichtige Fehlerbehebungen für dieses Problem enthält.</span><span class="sxs-lookup"><span data-stu-id="637c0-109">A [Windows update (Version 14393.351 - KB3197954)](https://support.microsoft.com/kb/3197954) was released on 10/27/16 that includes important fixes that address this issue.</span></span> <span data-ttu-id="637c0-110">Falls bei Ihnen dieses Problem auftritt, aktualisieren Sie Ihren Computer.</span><span class="sxs-lookup"><span data-stu-id="637c0-110">If you encounter this problem, update your machine.</span></span> <span data-ttu-id="637c0-111">Falls Sie Ihren PC nicht aktualisieren können, weil er neu gestartet wird, bevor Sie sich anmelden können, müssen Sie die Systemwiederherstellung verwenden, um für Ihr System einen Zeitpunkt herzustellen, der vor der Installation einer der betroffenen Apps liegt.</span><span class="sxs-lookup"><span data-stu-id="637c0-111">If you are not able to update your PC because your machine restarts before you can log in, you should use system restore to recover your system to a point earlier than when you installed one of the affected apps.</span></span> <span data-ttu-id="637c0-112">Informationen zur Systemwiederherstellung finden Sie unter [Wiederherstellungsoptionen unter Windows 10](https://support.microsoft.com/help/12415/windows-10-recovery-options).</span><span class="sxs-lookup"><span data-stu-id="637c0-112">For information on how to use system restore, see [Recovery options in Windows 10](https://support.microsoft.com/help/12415/windows-10-recovery-options).</span></span>

<span data-ttu-id="637c0-113">Falls das Problem durch das Update nicht behoben werden kann oder Sie nicht sicher sind, wie Sie die Wiederherstellung für den PC ausführen, wenden Sie sich an den [Microsoft-Support](https://support.microsoft.com/contactus/).</span><span class="sxs-lookup"><span data-stu-id="637c0-113">If updating does not fix the problem or you aren't sure how to recover your PC, please contact [Microsoft Support](https://support.microsoft.com/contactus/).</span></span>

<span data-ttu-id="637c0-114">Wenn Sie Entwickler sind, möchten Sie die Installation der Desktop-Brücken-Apps unter Versionen von Windows vielleicht verhindern, die dieses Update nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="637c0-114">If you are a developer, you may want to prevent the installation of your Desktop Bridge apps on versions of Windows that do not include this update.</span></span> <span data-ttu-id="637c0-115">Beachten Sie, dass Ihre App dadurch nicht für Kunden verfügbar ist, die das Update noch nicht installiert haben.</span><span class="sxs-lookup"><span data-stu-id="637c0-115">Note that by doing this your app will not be available to users that have not yet installed the update.</span></span> <span data-ttu-id="637c0-116">Um die Verfügbarkeit Ihrer App auf Benutzer zu beschränken, die dieses Update installiert haben, ändern Sie die Datei „AppxManifest.xml“ wie folgt:</span><span class="sxs-lookup"><span data-stu-id="637c0-116">To limit the availability of your app to users that have installed this update, modify your AppxManifest.xml file as follows:</span></span>

```<TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14393.351" MaxVersionTested="10.0.14393.351"/>```

<span data-ttu-id="637c0-117">Details zum Windows-Update finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="637c0-117">Details regarding the Windows Update can be found at:</span></span>
* <span data-ttu-id="637c0-118">https://support.microsoft.com/kb/3197954</span><span class="sxs-lookup"><span data-stu-id="637c0-118">https://support.microsoft.com/kb/3197954</span></span>
* <span data-ttu-id="637c0-119">https://support.microsoft.com/help/12387/windows-10-update-history</span><span class="sxs-lookup"><span data-stu-id="637c0-119">https://support.microsoft.com/help/12387/windows-10-update-history</span></span>

## <a name="common-errors-that-can-appear-when-you-sign-your-app"></a><span data-ttu-id="637c0-120">Häufige Fehler, die beim Signieren Ihrer App angezeigt werden können</span><span class="sxs-lookup"><span data-stu-id="637c0-120">Common errors that can appear when you sign your app</span></span>

### <a name="publisher-and-cert-mismatch-causes-signtool-error-error-signersign-failed--21470248850x8007000b"></a><span data-ttu-id="637c0-121">Nichtübereinstimmung von Herausgeber und Zertifikat führt zum Signtool-Fehler „Fehler: SignerSign() fehlgeschlagen“ (-2147024885/0x8007000b)</span><span class="sxs-lookup"><span data-stu-id="637c0-121">Publisher and cert mismatch causes Signtool error "Error: SignerSign() Failed" (-2147024885/0x8007000b)</span></span>

<span data-ttu-id="637c0-122">Der Herausgeber-Eintrag im Windows-App-Paket-Manifest muss dem Betreff des Zertifikats entsprechen, mit dem signiert wird.</span><span class="sxs-lookup"><span data-stu-id="637c0-122">The Publisher entry in the Windows app package manifest must match the Subject of the certificate you are signing with.</span></span>  <span data-ttu-id="637c0-123">Mit eine der folgenden Methoden können Sie den Betreff des Zertifikats anzeigen.</span><span class="sxs-lookup"><span data-stu-id="637c0-123">You can use any of the following methods to view the subject of the cert.</span></span>

**<span data-ttu-id="637c0-124">Option1: PowerShell</span><span class="sxs-lookup"><span data-stu-id="637c0-124">Option 1: Powershell</span></span>**

<span data-ttu-id="637c0-125">Führen Sie folgenden PowerShell-Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="637c0-125">Run the following PowerShell command.</span></span> <span data-ttu-id="637c0-126">Als Zertifikatdateien können CER- oder PFX-Dateien verwendet werden, da sie über identische Herausgeberinformationen verfügen.</span><span class="sxs-lookup"><span data-stu-id="637c0-126">Either .cer or .pfx can be used as the certificate file, as they have the same publisher information.</span></span>

```ps
(Get-PfxCertificate <cert_file>).Subject
```

**<span data-ttu-id="637c0-127">Option2: Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="637c0-127">Option 2: File Explorer</span></span>**

<span data-ttu-id="637c0-128">Doppelklicken Sie im Datei-Explorer auf das Zertifikat, wählen Sie die Registerkarte *Details* aus, und klicken Sie dann in der Liste auf das Feld *Betreff*.</span><span class="sxs-lookup"><span data-stu-id="637c0-128">Double-click the certificate in File Explorer, select the *Details* tab, and then the *Subject* field in the list.</span></span> <span data-ttu-id="637c0-129">Anschließend können Sie die Inhalte kopieren.</span><span class="sxs-lookup"><span data-stu-id="637c0-129">You can then copy the contents.</span></span>

**<span data-ttu-id="637c0-130">Option3: CertUtil</span><span class="sxs-lookup"><span data-stu-id="637c0-130">Option 3: CertUtil</span></span>**

<span data-ttu-id="637c0-131">Führen Sie **CertUtil** über die Befehlszeile für die PFX-Datei aus, und kopieren Sie das Feld *Betreff* der Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="637c0-131">Run **certutil** from the the command line on the PFX file and copy the *Subject* field from the output.</span></span>

```cmd
certutil -dump <cert_file.pfx>
```

### <a name="corrupted-or-malformed-authenticode-signatures"></a><span data-ttu-id="637c0-132">Beschädigte oder falsch formatierte Authenticode-Signaturen</span><span class="sxs-lookup"><span data-stu-id="637c0-132">Corrupted or malformed Authenticode signatures</span></span>

<span data-ttu-id="637c0-133">Dieser Abschnitt enthält ausführliche Informationen zum Identifizieren von Problemen mit übertragbaren ausführbaren Dateien in Ihrem Windows-App-Paket, die möglicherweise beschädigte oder falsch formatierte Authenticode-Signaturen enthalten.</span><span class="sxs-lookup"><span data-stu-id="637c0-133">This section contains details on how to identify issues with Portable Executable (PE) files in your Windows app package that may contain corrupted or malformed Authenticode signatures.</span></span> <span data-ttu-id="637c0-134">Ungültige Authenticode-Signaturen auf Ihren übertragbaren ausführbaren Dateien, die ein beliebiges binäres Format (z. B. .exe, .dll, chm usw.) aufweisen können, verhindern, dass Ihr Paket ordnungsgemäß signiert wird und aus einem Windows-App-Paket bereitgestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="637c0-134">Invalid Authenticode signatures on your PE files, which may be in any binary format (e.g. .exe, .dll, .chm, etc.), will prevent your package from being signed properly, and thus prevent it from being deployable from an Windows app package.</span></span>

<span data-ttu-id="637c0-135">Die Position der Authenticode-Signatur einer übertragbaren ausführbaren Datei wird durch den Zertifikat-Tabelleneintrag in den optionalen Kopfzeilen-Datenverzeichnissen und der zugehörigen Attributzertifikatstabelle angegeben.</span><span class="sxs-lookup"><span data-stu-id="637c0-135">The location of the Authenticode signature of a PE file is specified by the Certificate Table entry in the Optional Header Data Directories and the associated Attribute Certificate Table.</span></span> <span data-ttu-id="637c0-136">Während der Überprüfung der Signatur dienen die Angaben in diesen Strukturen dazu, die Signatur in einer übertragbaren ausführbaren Datei zu suchen.</span><span class="sxs-lookup"><span data-stu-id="637c0-136">During signature verification, the information specified in these structures is used to locate the signature on a PE file.</span></span> <span data-ttu-id="637c0-137">Wenn diese Werte beschädigt werden, kann es so aussehen, als ob eine Datei ungültig signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="637c0-137">If these values get corrupted then it is possible for a file to appear to be invalidly signed.</span></span>

<span data-ttu-id="637c0-138">Damit die Authenticode-Signatur korrekt ist, muss für die Authenticode-Signatur Folgendes gelten:</span><span class="sxs-lookup"><span data-stu-id="637c0-138">For the Authenticode signature to be correct, the following must be true of the Authenticode signature:</span></span>

- <span data-ttu-id="637c0-139">Der Anfang des **WIN_CERTIFICATE**-Eintrags in der übertragbaren ausführbaren Datei kann nicht über das Ende der ausführbaren Datei hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="637c0-139">The start of the **WIN_CERTIFICATE** entry in the PE file cannot extend past the end of the executable</span></span>
- <span data-ttu-id="637c0-140">Der **WIN_CERTIFCATE**-Eintrag sollte sich am Ende des Bilds befinden</span><span class="sxs-lookup"><span data-stu-id="637c0-140">The **WIN_CERTIFCATE** entry should be located at the end of the image</span></span>
- <span data-ttu-id="637c0-141">Die Größe des **WIN_CERTIFICATE**-Eintrags muss positiv sein</span><span class="sxs-lookup"><span data-stu-id="637c0-141">The size of the **WIN_CERTIFICATE** entry must be positive</span></span>
- <span data-ttu-id="637c0-142">Der **WIN_CERTIFICATE**-Eintrag muss bei ausführbaren 32-Bit-Dateien nach der **IMAGE_NT_HEADERS32**-Struktur und bei ausführbaren 64-Bit-Dateien nach der IMAGE_NT_HEADERS64-Struktur beginnen.</span><span class="sxs-lookup"><span data-stu-id="637c0-142">The **WIN_CERTIFICATE**entry must start after the **IMAGE_NT_HEADERS32** structure for 32-bit executables and IMAGE_NT_HEADERS64 structure for 64-bit executables</span></span>

<span data-ttu-id="637c0-143">Weitere Informationen finden Sie in der [Spezifikation zu übertragbaren ausführbaren Authenticode-Dateien](http://download.microsoft.com/download/9/c/5/9c5b2167-8017-4bae-9fde-d599bac8184a/Authenticode_PE.docx) und der [Spezifikation zum Format übertragbarer ausführbarer Dateien](https://msdn.microsoft.com/windows/hardware/gg463119.aspx).</span><span class="sxs-lookup"><span data-stu-id="637c0-143">For more details, please refer to the [Authenticode Portal Executable specification](http://download.microsoft.com/download/9/c/5/9c5b2167-8017-4bae-9fde-d599bac8184a/Authenticode_PE.docx) and the [PE file format specification](https://msdn.microsoft.com/windows/hardware/gg463119.aspx).</span></span>

<span data-ttu-id="637c0-144">Beachten Sie, dass SignTool.exe eine Liste der beschädigten oder falsch formatierten Binärdateien ausgeben kann, wenn Sie versuchen, ein Windows-App-Paket zu signieren.</span><span class="sxs-lookup"><span data-stu-id="637c0-144">Note that SignTool.exe can output a list of the corrupted or malformed binaries when attempting to sign an Windows app package.</span></span> <span data-ttu-id="637c0-145">Aktivieren Sie dazu ausführliche Protokollierung , indem Sie die Umgebungsvariable APPXSIP_LOG auf 1 (z. B. ```set APPXSIP_LOG=1```) festlegen und SignTool.exe erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="637c0-145">To do this, enable verbose logging by setting the environment variable APPXSIP_LOG to 1 (e.g., ```set APPXSIP_LOG=1``` ) and re-run SignTool.exe.</span></span>

<span data-ttu-id="637c0-146">Um diese falsch formatierten Binärdateien zu korrigieren, stellen Sie sicher, dass sie den oben angegebenen Anforderungen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="637c0-146">To fix these malformed binaries, ensure they conform to the requirements above.</span></span>

<span id="known-issues-anchor" />
## <a name="known-issues-with-cvbnet-and-c-uwp-projects"></a><span data-ttu-id="637c0-147">Bekannte Probleme mit C#/VB.NET und C++ UWP-Projekten</span><span class="sxs-lookup"><span data-stu-id="637c0-147">Known issues with C#/VB.NET and C++ UWP projects</span></span>

<span data-ttu-id="637c0-148">Wenn Sie ein C#-Projekt zum Verpacken der App verwenden möchten, müssen Sie die folgenden bekannten Probleme berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="637c0-148">If you prefer to use a C# project to package your app, you need to be aware of the following known issues.</span></span>

- <span data-ttu-id="637c0-149">Erstellen der App im Debugging-Modus führt zum Fehler: _Microsoft.Net. CoreRuntime.targets(235,5): Fehler: Anwendungen mit benutzerdefinierten Eintrag Punkt ausführbaren Dateien werden nicht unterstützt. Überprüfen Sie die ausführbare Attribut des Application-Elements im Paketmanifest._</span><span class="sxs-lookup"><span data-stu-id="637c0-149">Building the app in Debug mode results in the error: _Microsoft.Net.CoreRuntime.targets(235,5): error : Applications with custom entry point executables are not supported. Check Executable attribute of the Application element in the package manifest._</span></span>

  <span data-ttu-id="637c0-150">Um dieses Problem zu beheben, verwenden Sie stattdessen den Releasemodus.</span><span class="sxs-lookup"><span data-stu-id="637c0-150">To resolve this issue, use Release mode instead.</span></span>

- <span data-ttu-id="637c0-151">Im Stammordner des UWP-Projekts gespeichert gespeicherte Win32-Binärdateien werden in der Relaseversion entfernt.</span><span class="sxs-lookup"><span data-stu-id="637c0-151">Win32 Binaries stored in the root folder of the UWP project are removed in Release.</span></span> <span data-ttu-id="637c0-152">Der .NET Native-Compiler entfernt diese aus dem fertigen Paket. Dies führt zu einem Manifest-Validierungsfehler, da der Einstiegspunkt für die ausführbare Datei nicht gefunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="637c0-152">The .NET Native compiler will remove those from the final package, resulting in a manifest validation error since the executable entry point can't be found.</span></span>

  <span data-ttu-id="637c0-153">Um dieses Problem zu beheben, erstellen Sie einen Unterordner in Ihrem Projekt zum Speichern von Win32-Binärdateien.</span><span class="sxs-lookup"><span data-stu-id="637c0-153">To resolve this issue, create a subfolder in your project to store win32 binaries.</span></span>


## <a name="you-receive-the-error----msb4018-the-generateresource-task-failed-unexpectedly"></a><span data-ttu-id="637c0-154">Sie erhalten die Fehlermeldung: MSB4018 „GenerateResource“ unerwarteter Taskfehler</span><span class="sxs-lookup"><span data-stu-id="637c0-154">You receive the error    MSB4018 The "GenerateResource" task failed unexpectedly</span></span>

<span data-ttu-id="637c0-155">Dies kann passieren, wenn Sie versuchen, Satellitenassemblys in Paketressourcendateien (Package Resource Index, PRI) zu konvertiert.</span><span class="sxs-lookup"><span data-stu-id="637c0-155">This can happen when trying to convert satellite assemblies to Package Resource Index (PRI) files.</span></span>

<span data-ttu-id="637c0-156">Wir kennen das Problem und arbeiten an einer Lösung.</span><span class="sxs-lookup"><span data-stu-id="637c0-156">We are aware of this issue and are working on a more long term solution.</span></span> <span data-ttu-id="637c0-157">Um dieses Problem temporäre zu umgehen, können Sie den Ressourcen-Generator durch Hinzufügen dieser XML-Zeile zum ersten PropertyGroup-Element in der Projektdatei deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="637c0-157">As a temporary workaround, you can disable the resource generator by adding this line of XML to the first PropertyGroup element in hosting project file:</span></span>

``<AppxGeneratePrisForPortableLibrariesEnabled>false</AppxGeneratePrisForPortableLibrariesEnabled>``
