---
author: normesta
Description: This article contains known issues with the Desktop Bridge.
Search.Product: eADQiWindows 10XVcnh
title: Bekannte Probleme (Desktop-Brücke)
ms.author: normesta
ms.date: 06/20/2018
ms.topic: article
keywords: windows10, UWP
ms.assetid: 71f8ffcb-8a99-4214-ae83-2d4b718a750e
ms.localizationpriority: medium
ms.openlocfilehash: 61803e3a4a18dee260b78468c7970a875d8aff73
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7289407"
---
# <a name="known-issues-with-packaged-desktop-applications"></a><span data-ttu-id="52949-103">Bekannte Probleme mit verpackten desktop-Apps</span><span class="sxs-lookup"><span data-stu-id="52949-103">Known Issues with packaged desktop applications</span></span>

<span data-ttu-id="52949-104">Dieser Artikel enthält bekannte Probleme, die auftreten können, wenn Sie ein Windows-app-Paket für Ihre desktop-Anwendung erstellen.</span><span class="sxs-lookup"><span data-stu-id="52949-104">This article contains known issues that can occur when you create a Windows app package for your desktop application.</span></span>

<a id="app-converter" />

## <a name="known-issues-with-the-desktop-app-converter"></a><span data-ttu-id="52949-105">Bekannte Probleme mit dem Desktop App Converter</span><span class="sxs-lookup"><span data-stu-id="52949-105">Known Issues with the Desktop App Converter</span></span>

### <a name="ecreatingisolatedenvfailed-an-estartingisolatedenvfailed-errors"></a><span data-ttu-id="52949-106">E_CREATING_ISOLATED_ENV_FAILED- und E_STARTING_ISOLATED_ENV_FAILED-Fehler</span><span class="sxs-lookup"><span data-stu-id="52949-106">E_CREATING_ISOLATED_ENV_FAILED an E_STARTING_ISOLATED_ENV_FAILED errors</span></span>    

<span data-ttu-id="52949-107">Wenn Sie eine dieser Fehlermeldungen erhalten, stellen Sie sicher, dass Sie ein gültiges Basisimage aus dem [Download Center](https://aka.ms/converterimages) verwenden.</span><span class="sxs-lookup"><span data-stu-id="52949-107">If you receive either of these errors, make sure that you're using a valid base image from the [download center](https://aka.ms/converterimages).</span></span>
<span data-ttu-id="52949-108">Wenn Sie ein gültiges Basisimage verwenden, versuchen Sie, ``-Cleanup All`` in Ihrem Befehl zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="52949-108">If you’re using a valid base image, try using ``-Cleanup All`` in your command.</span></span>
<span data-ttu-id="52949-109">Wenn dies nicht funktioniert, senden Sie uns unter converter@microsoft.com bitte Ihre Protokolle, damit wir den Vorgang untersuchen können.</span><span class="sxs-lookup"><span data-stu-id="52949-109">If that does not work, please send us your logs at converter@microsoft.com to help us investigate.</span></span>

### <a name="new-containernetwork-the-object-already-exists-error"></a><span data-ttu-id="52949-110">New-ContainerNetwork: Fehler „Das Objekt ist bereits vorhanden.”</span><span class="sxs-lookup"><span data-stu-id="52949-110">New-ContainerNetwork: The object already exists error</span></span>

<span data-ttu-id="52949-111">Dieser Fehler kann angezeigt werden, wenn Sie ein neues Basisimage einrichten.</span><span class="sxs-lookup"><span data-stu-id="52949-111">You might receive this error when you setup a new base image.</span></span> <span data-ttu-id="52949-112">Dies kann passieren, wenn Sie ein Windows-Insider-Test-Flight auf einem Entwicklercomputer erhalten, auf dem zuvor Desktop App Converter installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="52949-112">This can happen if you have a Windows Insider flight on a developer machine that previously had the Desktop App Converter installed.</span></span>

<span data-ttu-id="52949-113">Um dieses Problem zu beheben, versuchen Sie, den Befehl `Netsh int ipv4 reset` über eine Eingabeaufforderung mit erhöhten Rechten auszuführen, und starten Sie den Computer dann neu.</span><span class="sxs-lookup"><span data-stu-id="52949-113">To resolve this issue, try running the command `Netsh int ipv4 reset` from an elevated command prompt, and then reboot your machine.</span></span>

### <a name="your-net-application-is-compiled-with-the-anycpu-build-option-and-fails-to-install"></a><span data-ttu-id="52949-114">Ihre Anwendung .NET wird mit der Buildoption "AnyCPU" kompiliert und Fehler bei der Installation</span><span class="sxs-lookup"><span data-stu-id="52949-114">Your .NET application is compiled with the "AnyCPU" build option and fails to install</span></span>

<span data-ttu-id="52949-115">Dies kann vorkommen, wenn die ausführbare Hauptdatei oder eine Abhängigkeitsdatei in der Ordnerhierarchie **Programmdateien** oder **Windows\System32** abgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="52949-115">This can happen if the main executable or any of the dependencies were placed anywhere in the **Program Files** or **Windows\System32** folder hierarchy.</span></span>

<span data-ttu-id="52949-116">Um dieses Problem zu beheben, versuchen Sie, mithilfe Ihres architekturspezifischen Desktop-Installers (32 Bit oder 64 Bit) ein Windows-App-Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="52949-116">To resolve this issue, try using your architecture-specific desktop installer (32 bit or 64 bit) to generate a Windows app package.</span></span>

### <a name="publishing-public-side-by-side-fusion-assemblies-wont-work"></a><span data-ttu-id="52949-117">Die Veröffentlichung von öffentlichen parallelen Fusion-Assemblys ist nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="52949-117">Publishing public side-by-side Fusion assemblies won't work</span></span>

 <span data-ttu-id="52949-118">Während der Installation kann eine Anwendung öffentliche parallele Fusion-Assemblys veröffentlichen, auf die von jedem anderen Prozess zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="52949-118">During install, an application can publish public side-by-side Fusion assemblies, accessible to any other process.</span></span> <span data-ttu-id="52949-119">Während der Erstellung des Prozessaktivierungskontexts werden diese Assemblys von einem Systemprozess mit dem Namen CSRSS.exe abgerufen.</span><span class="sxs-lookup"><span data-stu-id="52949-119">During process activation context creation, these assemblies are retrieved by a system process named CSRSS.exe.</span></span> <span data-ttu-id="52949-120">Wenn dies für einen konvertierten Prozess erfolgt, tritt beim Erstellen des Aktivierungskontexts sowie beim Laden des Moduls dieser Assemblys ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="52949-120">When this is done for a converted process, activation context creation and module loading of these assemblies will fail.</span></span> <span data-ttu-id="52949-121">Die parallelen Fusion-Assemblys werden an folgenden Orten registriert:</span><span class="sxs-lookup"><span data-stu-id="52949-121">The side-by-side Fusion assemblies are registered in the following locations:</span></span>
  + <span data-ttu-id="52949-122">Registrierung:</span><span class="sxs-lookup"><span data-stu-id="52949-122">Registry:</span></span> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SideBySide\Winners`
  + <span data-ttu-id="52949-123">Dateisystem: %windir%\\SideBySide</span><span class="sxs-lookup"><span data-stu-id="52949-123">File System: %windir%\\SideBySide</span></span>

<span data-ttu-id="52949-124">Dies ist eine bekannte Einschränkung, und derzeit sind keine Umgehungen vorhanden.</span><span class="sxs-lookup"><span data-stu-id="52949-124">This is a known limitation and no workaround currently exists.</span></span> <span data-ttu-id="52949-125">Integrierte Assemblys wie z.B. ComCtl sind jedoch Teil des Betriebssystems, sodass entsprechende Abhängigkeiten sicher sind.</span><span class="sxs-lookup"><span data-stu-id="52949-125">That said, Inbox assemblies, like ComCtl, are shipped with the OS, so taking a dependency on them is safe.</span></span>

### <a name="error-found-in-xml-the-executable-attribute-is-invalid---the-value-myappexe-is-invalid-according-to-its-datatype"></a><span data-ttu-id="52949-126">Fehler in XML gefunden.</span><span class="sxs-lookup"><span data-stu-id="52949-126">Error found in XML.</span></span> <span data-ttu-id="52949-127">Das Attribut „Ausführbare Datei” ist ungültig. – Der Wert MyApp.EXE ist gemäß dem Datentyp ungültig.</span><span class="sxs-lookup"><span data-stu-id="52949-127">The 'Executable' attribute is invalid - The value 'MyApp.EXE' is invalid according to its datatype</span></span>

<span data-ttu-id="52949-128">Dies kann vorkommen, wenn die ausführbaren Dateien in Ihrer Anwendung die Erweiterung **. EXE** in Großbuchstaben aufweisen.</span><span class="sxs-lookup"><span data-stu-id="52949-128">This can happen if the executables in your application have a capitalized **.EXE** extension.</span></span> <span data-ttu-id="52949-129">Obwohl die Groß-/Kleinschreibung dieser Erweiterung keine Auswirkungen auf haben, ob die Anwendung ausgeführt wird, kann dies den DAC diesen Fehler generiert führen.</span><span class="sxs-lookup"><span data-stu-id="52949-129">Although, the casing of this extension shouldn't affect whether your application runs, this can cause the DAC to generate this error.</span></span>

<span data-ttu-id="52949-130">Um dieses Problem zu beheben, versuchen Sie, das **-AppExecutable**-Kennzeichen beim Verpacken festzulegen, und verwenden Sie als Erweiterung Ihrer wichtigsten ausführbaren Datei „.exe” in Kleinbuchstaben (z.B.: MYAPP.exe).</span><span class="sxs-lookup"><span data-stu-id="52949-130">To resolve this issue, try specifying the **-AppExecutable** flag when you package, and use the lower case ".exe" as the extension of your main executable (For example: MYAPP.exe).</span></span>    <span data-ttu-id="52949-131">Alternativ können Sie die Groß-/Kleinschreibung für alle ausführbaren Dateien in Ihrer Anwendung aus Kleinbuchstaben in Großbuchstaben ändern (z. B.: aus. EXE-Datei in .exe).</span><span class="sxs-lookup"><span data-stu-id="52949-131">Alternately you can change the casing for all executables in your application from lowercase to uppercase (For example: from .EXE to .exe).</span></span>

### <a name="corrupted-or-malformed-authenticode-signatures"></a><span data-ttu-id="52949-132">Beschädigte oder falsch formatierte Authenticode-Signaturen</span><span class="sxs-lookup"><span data-stu-id="52949-132">Corrupted or malformed Authenticode signatures</span></span>

<span data-ttu-id="52949-133">Dieser Abschnitt enthält ausführliche Informationen zum Identifizieren von Problemen mit übertragbaren ausführbaren Dateien in Ihrem Windows-App-Paket, die möglicherweise beschädigte oder falsch formatierte Authenticode-Signaturen enthalten.</span><span class="sxs-lookup"><span data-stu-id="52949-133">This section contains details on how to identify issues with Portable Executable (PE) files in your Windows app package that may contain corrupted or malformed Authenticode signatures.</span></span> <span data-ttu-id="52949-134">Ungültige Authenticode-Signaturen auf Ihren übertragbaren ausführbaren Dateien, die ein beliebiges binäres Format (z. B. .exe, .dll, chm usw.) aufweisen können, verhindern, dass Ihr Paket ordnungsgemäß signiert wird und aus einem Windows-App-Paket bereitgestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="52949-134">Invalid Authenticode signatures on your PE files, which may be in any binary format (e.g. .exe, .dll, .chm, etc.), will prevent your package from being signed properly, and thus prevent it from being deployable from an Windows app package.</span></span>

<span data-ttu-id="52949-135">Die Position der Authenticode-Signatur einer übertragbaren ausführbaren Datei wird durch den Zertifikat-Tabelleneintrag in den optionalen Kopfzeilen-Datenverzeichnissen und der zugehörigen Attributzertifikatstabelle angegeben.</span><span class="sxs-lookup"><span data-stu-id="52949-135">The location of the Authenticode signature of a PE file is specified by the Certificate Table entry in the Optional Header Data Directories and the associated Attribute Certificate Table.</span></span> <span data-ttu-id="52949-136">Während der Überprüfung der Signatur dienen die Angaben in diesen Strukturen dazu, die Signatur in einer übertragbaren ausführbaren Datei zu suchen.</span><span class="sxs-lookup"><span data-stu-id="52949-136">During signature verification, the information specified in these structures is used to locate the signature on a PE file.</span></span> <span data-ttu-id="52949-137">Wenn diese Werte beschädigt werden, kann es so aussehen, als ob eine Datei ungültig signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="52949-137">If these values get corrupted then it is possible for a file to appear to be invalidly signed.</span></span>

<span data-ttu-id="52949-138">Damit die Authenticode-Signatur korrekt ist, muss für die Authenticode-Signatur Folgendes gelten:</span><span class="sxs-lookup"><span data-stu-id="52949-138">For the Authenticode signature to be correct, the following must be true of the Authenticode signature:</span></span>

- <span data-ttu-id="52949-139">Der Anfang des **WIN_CERTIFICATE**-Eintrags in der übertragbaren ausführbaren Datei kann nicht über das Ende der ausführbaren Datei hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="52949-139">The start of the **WIN_CERTIFICATE** entry in the PE file cannot extend past the end of the executable</span></span>
- <span data-ttu-id="52949-140">Der **WIN_CERTIFCATE**-Eintrag sollte sich am Ende des Bilds befinden</span><span class="sxs-lookup"><span data-stu-id="52949-140">The **WIN_CERTIFCATE** entry should be located at the end of the image</span></span>
- <span data-ttu-id="52949-141">Die Größe des **WIN_CERTIFICATE**-Eintrags muss positiv sein</span><span class="sxs-lookup"><span data-stu-id="52949-141">The size of the **WIN_CERTIFICATE** entry must be positive</span></span>
- <span data-ttu-id="52949-142">Der **WIN_CERTIFICATE**-Eintrag muss bei ausführbaren 32-Bit-Dateien nach der **IMAGE_NT_HEADERS32**-Struktur und bei ausführbaren 64-Bit-Dateien nach der IMAGE_NT_HEADERS64-Struktur beginnen.</span><span class="sxs-lookup"><span data-stu-id="52949-142">The **WIN_CERTIFICATE**entry must start after the **IMAGE_NT_HEADERS32** structure for 32-bit executables and IMAGE_NT_HEADERS64 structure for 64-bit executables</span></span>

<span data-ttu-id="52949-143">Weitere Informationen finden Sie in der [Spezifikation zu übertragbaren ausführbaren Authenticode-Dateien](http://download.microsoft.com/download/9/c/5/9c5b2167-8017-4bae-9fde-d599bac8184a/Authenticode_PE.docx) und der [Spezifikation zum Format übertragbarer ausführbarer Dateien](https://msdn.microsoft.com/windows/hardware/gg463119.aspx).</span><span class="sxs-lookup"><span data-stu-id="52949-143">For more details, please refer to the [Authenticode Portal Executable specification](http://download.microsoft.com/download/9/c/5/9c5b2167-8017-4bae-9fde-d599bac8184a/Authenticode_PE.docx) and the [PE file format specification](https://msdn.microsoft.com/windows/hardware/gg463119.aspx).</span></span>

<span data-ttu-id="52949-144">Beachten Sie, dass SignTool.exe eine Liste der beschädigten oder falsch formatierten Binärdateien ausgeben kann, wenn Sie versuchen, ein Windows-App-Paket zu signieren.</span><span class="sxs-lookup"><span data-stu-id="52949-144">Note that SignTool.exe can output a list of the corrupted or malformed binaries when attempting to sign an Windows app package.</span></span> <span data-ttu-id="52949-145">Aktivieren Sie dazu ausführliche Protokollierung , indem Sie die Umgebungsvariable APPXSIP_LOG auf 1 (z. B. ```set APPXSIP_LOG=1```) festlegen und SignTool.exe erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="52949-145">To do this, enable verbose logging by setting the environment variable APPXSIP_LOG to 1 (e.g., ```set APPXSIP_LOG=1``` ) and re-run SignTool.exe.</span></span>

<span data-ttu-id="52949-146">Um diese falsch formatierten Binärdateien zu korrigieren, stellen Sie sicher, dass sie den oben angegebenen Anforderungen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="52949-146">To fix these malformed binaries, ensure they conform to the requirements above.</span></span>

## <a name="you-receive-the-error----msb4018-the-generateresource-task-failed-unexpectedly"></a><span data-ttu-id="52949-147">Sie erhalten die Fehlermeldung: MSB4018 „GenerateResource“ unerwarteter Taskfehler</span><span class="sxs-lookup"><span data-stu-id="52949-147">You receive the error    MSB4018 The "GenerateResource" task failed unexpectedly</span></span>

<span data-ttu-id="52949-148">Dies kann passieren, wenn Sie versuchen, Satellitenassemblys in Paketressourcendateien (Package Resource Index, PRI) zu konvertiert.</span><span class="sxs-lookup"><span data-stu-id="52949-148">This can happen when trying to convert satellite assemblies to Package Resource Index (PRI) files.</span></span>

<span data-ttu-id="52949-149">Wir kennen das Problem und arbeiten an einer Lösung.</span><span class="sxs-lookup"><span data-stu-id="52949-149">We are aware of this issue and are working on a more long term solution.</span></span> <span data-ttu-id="52949-150">Um dieses Problem temporäre zu umgehen, können Sie den Ressourcen-Generator durch Hinzufügen dieser XML-Zeile zum ersten PropertyGroup-Element in der Projektdatei deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="52949-150">As a temporary workaround, you can disable the resource generator by adding this line of XML to the first PropertyGroup element in hosting project file:</span></span>

``<AppxGeneratePrisForPortableLibrariesEnabled>false</AppxGeneratePrisForPortableLibrariesEnabled>``

## <a name="blue-screen-with-error-code-0x139-kernelsecuritycheckfailure"></a><span data-ttu-id="52949-151">Blauer Bildschirm mit dem Fehlercode 0x139 (KERNEL_SECURITY_CHECK_FAILURE)</span><span class="sxs-lookup"><span data-stu-id="52949-151">Blue screen with error code 0x139 (KERNEL_SECURITY_CHECK_FAILURE)</span></span>

<span data-ttu-id="52949-152">Nach dem Installieren oder Starten bestimmter Apps aus dem Microsoft Store wird Ihr Computer unter Umständen unerwartet mit folgendem Fehler neu gestartet: **0x139 (KERNEL\_SECURITY\_CHECK\_ FAILURE)**.</span><span class="sxs-lookup"><span data-stu-id="52949-152">After installing or launching certain apps from the Microsoft Store, your machine may unexpectedly reboot with the error: **0x139 (KERNEL\_SECURITY\_CHECK\_ FAILURE)**.</span></span>

<span data-ttu-id="52949-153">Bekannte betroffene Apps: Kodi, JT2Go, Ear Trumpet, Teslagrad usw.</span><span class="sxs-lookup"><span data-stu-id="52949-153">Known affected apps include Kodi, JT2Go, Ear Trumpet, Teslagrad, and others.</span></span>

<span data-ttu-id="52949-154">Am 27.10.2016 wurde ein [Windows-Update (Version 14393.351 - KB3197954)](https://support.microsoft.com/kb/3197954) veröffentlich, das wichtige Fehlerbehebungen für dieses Problem enthält.</span><span class="sxs-lookup"><span data-stu-id="52949-154">A [Windows update (Version 14393.351 - KB3197954)](https://support.microsoft.com/kb/3197954) was released on 10/27/16 that includes important fixes that address this issue.</span></span> <span data-ttu-id="52949-155">Falls bei Ihnen dieses Problem auftritt, aktualisieren Sie Ihren Computer.</span><span class="sxs-lookup"><span data-stu-id="52949-155">If you encounter this problem, update your machine.</span></span> <span data-ttu-id="52949-156">Falls Sie Ihren PC nicht aktualisieren können, weil er neu gestartet wird, bevor Sie sich anmelden können, müssen Sie die Systemwiederherstellung verwenden, um für Ihr System einen Zeitpunkt herzustellen, der vor der Installation einer der betroffenen Apps liegt.</span><span class="sxs-lookup"><span data-stu-id="52949-156">If you are not able to update your PC because your machine restarts before you can log in, you should use system restore to recover your system to a point earlier than when you installed one of the affected apps.</span></span> <span data-ttu-id="52949-157">Informationen zur Systemwiederherstellung finden Sie unter [Wiederherstellungsoptionen unter Windows 10](https://support.microsoft.com/help/12415/windows-10-recovery-options).</span><span class="sxs-lookup"><span data-stu-id="52949-157">For information on how to use system restore, see [Recovery options in Windows 10](https://support.microsoft.com/help/12415/windows-10-recovery-options).</span></span>

<span data-ttu-id="52949-158">Falls das Problem durch das Update nicht behoben werden kann oder Sie nicht sicher sind, wie Sie die Wiederherstellung für den PC ausführen, wenden Sie sich an den [Microsoft-Support](https://support.microsoft.com/contactus/).</span><span class="sxs-lookup"><span data-stu-id="52949-158">If updating does not fix the problem or you aren't sure how to recover your PC, please contact [Microsoft Support](https://support.microsoft.com/contactus/).</span></span>

<span data-ttu-id="52949-159">Wenn Sie Entwickler sind, möchten Sie die Installation Ihres Anwendungspakets unter Versionen von Windows vielleicht verhindern, die dieses Update nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="52949-159">If you are a developer, you may want to prevent the installation of your packaged application on versions of Windows that do not include this update.</span></span> <span data-ttu-id="52949-160">Beachten Sie, dass Ihre Anwendung dadurch nicht für Benutzer verfügbar ist, die das Update noch nicht installiert haben.</span><span class="sxs-lookup"><span data-stu-id="52949-160">Note that by doing this your application will not be available to users that have not yet installed the update.</span></span> <span data-ttu-id="52949-161">Um die Verfügbarkeit Ihrer Anwendung für Benutzer zu beschränken, die dieses Update installiert haben, ändern Sie die Datei "appxmanifest.xml" wie folgt:</span><span class="sxs-lookup"><span data-stu-id="52949-161">To limit the availability of your application to users that have installed this update, modify your AppxManifest.xml file as follows:</span></span>

```<TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14393.351" MaxVersionTested="10.0.14393.351"/>```

<span data-ttu-id="52949-162">Details zum Windows Update finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="52949-162">Details regarding the Windows Update can be found at:</span></span>
* https://support.microsoft.com/kb/3197954
* https://support.microsoft.com/help/12387/windows-10-update-history

## <a name="common-errors-that-can-appear-when-you-sign-your-app"></a><span data-ttu-id="52949-163">Häufige Fehler, die beim Signieren Ihrer App angezeigt werden können</span><span class="sxs-lookup"><span data-stu-id="52949-163">Common errors that can appear when you sign your app</span></span>

### <a name="publisher-and-cert-mismatch-causes-signtool-error-error-signersign-failed--21470248850x8007000b"></a><span data-ttu-id="52949-164">Nichtübereinstimmung von Herausgeber und Zertifikat führt zum Signtool-Fehler „Fehler: SignerSign() fehlgeschlagen“ (-2147024885/0x8007000b)</span><span class="sxs-lookup"><span data-stu-id="52949-164">Publisher and cert mismatch causes Signtool error "Error: SignerSign() Failed" (-2147024885/0x8007000b)</span></span>

<span data-ttu-id="52949-165">Der Herausgeber-Eintrag im Windows-App-Paket-Manifest muss dem Betreff des Zertifikats entsprechen, mit dem signiert wird.</span><span class="sxs-lookup"><span data-stu-id="52949-165">The Publisher entry in the Windows app package manifest must match the Subject of the certificate you are signing with.</span></span>  <span data-ttu-id="52949-166">Mit eine der folgenden Methoden können Sie den Betreff des Zertifikats anzeigen.</span><span class="sxs-lookup"><span data-stu-id="52949-166">You can use any of the following methods to view the subject of the cert.</span></span>

**<span data-ttu-id="52949-167">Option1: PowerShell</span><span class="sxs-lookup"><span data-stu-id="52949-167">Option 1: Powershell</span></span>**

<span data-ttu-id="52949-168">Führen Sie folgenden PowerShell-Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="52949-168">Run the following PowerShell command.</span></span> <span data-ttu-id="52949-169">Als Zertifikatdateien können CER- oder PFX-Dateien verwendet werden, da sie über identische Herausgeberinformationen verfügen.</span><span class="sxs-lookup"><span data-stu-id="52949-169">Either .cer or .pfx can be used as the certificate file, as they have the same publisher information.</span></span>

```ps
(Get-PfxCertificate <cert_file>).Subject
```

**<span data-ttu-id="52949-170">Option2: Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="52949-170">Option 2: File Explorer</span></span>**

<span data-ttu-id="52949-171">Doppelklicken Sie im Datei-Explorer auf das Zertifikat, wählen Sie die Registerkarte *Details* aus, und klicken Sie dann in der Liste auf das Feld *Betreff*.</span><span class="sxs-lookup"><span data-stu-id="52949-171">Double-click the certificate in File Explorer, select the *Details* tab, and then the *Subject* field in the list.</span></span> <span data-ttu-id="52949-172">Anschließend können Sie die Inhalte kopieren.</span><span class="sxs-lookup"><span data-stu-id="52949-172">You can then copy the contents.</span></span>

**<span data-ttu-id="52949-173">Option3: CertUtil</span><span class="sxs-lookup"><span data-stu-id="52949-173">Option 3: CertUtil</span></span>**

<span data-ttu-id="52949-174">Führen Sie **Certutil** über die Befehlszeile aus, für die PFX-Datei, und kopieren Sie das Feld *Betreff* der Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="52949-174">Run **certutil** from the command line on the PFX file and copy the *Subject* field from the output.</span></span>

```cmd
certutil -dump <cert_file.pfx>
```

<a id="bad-pe-cert" />

### <a name="bad-pe-certificate-0x800700c1"></a><span data-ttu-id="52949-175">Ungültiges PE-Zertifikat (0x800700C1)</span><span class="sxs-lookup"><span data-stu-id="52949-175">Bad PE certificate (0x800700C1)</span></span>

<span data-ttu-id="52949-176">Dies kann passieren, wenn das Paket eine Binärdatei mit ein beschädigten Zertifikat enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="52949-176">This can happen when your package contains a binary that has a corrupted certificate.</span></span> <span data-ttu-id="52949-177">Hier sehen Sie einige Gründe, warum dies geschieht:</span><span class="sxs-lookup"><span data-stu-id="52949-177">Here's some of the reasons why this can happen:</span></span>

* <span data-ttu-id="52949-178">Beginn des Zertifikats ist nicht am Ende eines Bilds.</span><span class="sxs-lookup"><span data-stu-id="52949-178">The start of the certificate is not at the end of an image.</span></span>  

* <span data-ttu-id="52949-179">Die Größe des Zertifikats ist nicht positiv.</span><span class="sxs-lookup"><span data-stu-id="52949-179">The size of the certificate isn't positive.</span></span>

* <span data-ttu-id="52949-180">Der Zertifikat-Start wird nicht nach der `IMAGE_NT_HEADERS32` Struktur für eine 32-Bit-ausführbare Datei oder nach der `IMAGE_NT_HEADERS64` Struktur für eine 64-Bit-ausführbare Datei.</span><span class="sxs-lookup"><span data-stu-id="52949-180">The certificate start isn't after the `IMAGE_NT_HEADERS32` structure for a 32-bit executable or after the `IMAGE_NT_HEADERS64` structure for a 64-bit executable.</span></span>

* <span data-ttu-id="52949-181">Der Zertifikat-Zeiger ist nicht ordnungsgemäß für eine Struktur WIN_CERTIFICATE ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="52949-181">The certificate pointer isn't properly aligned for a WIN_CERTIFICATE structure.</span></span>

<span data-ttu-id="52949-182">Zum Auffinden von Dateien, die einem fehlerhaften PE-Zertifikat enthalten, öffnen Sie ein **Eingabeaufforderungsfenster**, und legen Sie die Umgebungsvariable `APPXSIP_LOG` auf dem Wert 1.</span><span class="sxs-lookup"><span data-stu-id="52949-182">To find files that contain a bad PE cert, open a **Command Prompt**, and set the environment variable named `APPXSIP_LOG` to a value of 1.</span></span>

```
set APPXSIP_LOG=1
```

<span data-ttu-id="52949-183">Signieren Sie über die **Befehlszeile**dann die Anwendung erneut.</span><span class="sxs-lookup"><span data-stu-id="52949-183">Then, from the **Command Prompt**, sign your application again.</span></span> <span data-ttu-id="52949-184">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="52949-184">For example:</span></span>

```
signtool.exe sign /a /v /fd SHA256 /f APPX_TEST_0.pfx C:\Users\Contoso\Desktop\pe\VLC.appx
```

<span data-ttu-id="52949-185">Informationen zu Dateien, die einem fehlerhaften PE-Zertifikat enthalten, werden im **Konsolenfenster**angezeigt.</span><span class="sxs-lookup"><span data-stu-id="52949-185">Information about files that contain a bad PE cert will appear in the **Console Window**.</span></span> <span data-ttu-id="52949-186">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="52949-186">For example:</span></span>

```
...

ERROR: [AppxSipCustomLoggerCallback] File has malformed certificate: uninstall.exe

...   
```
## <a name="next-steps"></a><span data-ttu-id="52949-187">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="52949-187">Next Steps</span></span>

**<span data-ttu-id="52949-188">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="52949-188">Find answers to your questions</span></span>**

<span data-ttu-id="52949-189">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="52949-189">Have questions?</span></span> <span data-ttu-id="52949-190">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="52949-190">Ask us on Stack Overflow.</span></span> <span data-ttu-id="52949-191">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="52949-191">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="52949-192">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="52949-192">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="52949-193">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="52949-193">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="52949-194">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="52949-194">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
