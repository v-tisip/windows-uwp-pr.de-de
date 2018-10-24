---
author: laurenhughes
title: Signieren eines App-Pakets mit SignTool
description: Verwenden Sie SignTool, um ein App-Paket manuell mit einem Zertifikat zu signieren.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 171f332d-2a54-4c68-8aa0-52975d975fb1
ms.localizationpriority: medium
ms.openlocfilehash: c238855f4f018e8e3142509842221c6b9d97fae3
ms.sourcegitcommit: 4b97117d3aff38db89d560502a3c372f12bb6ed5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "5440744"
---
# <a name="sign-an-app-package-using-signtool"></a><span data-ttu-id="4bbfa-104">Signieren eines App-Pakets mit SignTool</span><span class="sxs-lookup"><span data-stu-id="4bbfa-104">Sign an app package using SignTool</span></span>


<span data-ttu-id="4bbfa-105">**SignTool** ist ein Befehlszeilentool, mit dem ein App-Paket oder -Bündel mit einem Zertifikat digital signiert wird.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-105">**SignTool** is a command line tool used to digitally sign an app package or bundle with a certificate.</span></span> <span data-ttu-id="4bbfa-106">Das Zertifikat kann vom Benutzer (zu Testzwecken) erstellt oder von einem Unternehmen (für die Verteilung) ausgestellt sein.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-106">The certificate can either be created by the user (for testing purposes) or issued by a company (for distribution).</span></span> <span data-ttu-id="4bbfa-107">Die Signierung eines App-Pakets bietet dem Benutzer den Nachweis, dass die App-Daten nach der Signierung nicht geändert wurden, sowie die Bestätigung der Identität des Benutzers oder Unternehmens, die es signiert haben.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-107">Signing an app package provides the user with verification that the app's data has not been modified after it was signed while also confirming the identity of the user or company that signed it.</span></span> <span data-ttu-id="4bbfa-108">**SignTool** kann verschlüsselte oder unverschlüsselte App-Pakete und -Bündel signieren.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-108">**SignTool** can sign encrypted or unencrypted app packages and bundles.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="4bbfa-109">Wenn Sie Visual Studio zum Entwickeln der App verwendet haben, wird empfohlen, dass Sie den Visual Studio-Assistenten zum Erstellen und Signieren des App-Pakets verwenden.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-109">If you used Visual Studio to develop your app, it's recommended that you use the Visual Studio wizard to create and sign your app package.</span></span> <span data-ttu-id="4bbfa-110">Weitere Informationen finden Sie unter [Verpacken einer UWP-App mit Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="4bbfa-110">For more information, see [Package a UWP app with Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span></span>

<span data-ttu-id="4bbfa-111">Weitere Informationen zur Codesignatur und zu Zertifikaten im Allgemeinen finden Sie unter [Einführung in die Codesignatur](https://msdn.microsoft.com/library/windows/desktop/aa380259.aspx#introduction_to_code_signing).</span><span class="sxs-lookup"><span data-stu-id="4bbfa-111">For more information about code signing and certificates in general, see [Introduction to Code Signing](https://msdn.microsoft.com/library/windows/desktop/aa380259.aspx#introduction_to_code_signing).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4bbfa-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="4bbfa-112">Prerequisites</span></span>
- **<span data-ttu-id="4bbfa-113">Ein App-Paket</span><span class="sxs-lookup"><span data-stu-id="4bbfa-113">A packaged app</span></span>**  
    <span data-ttu-id="4bbfa-114">Weitere Informationen über das manuelle Erstellen eines App-Pakets finden Sie unter [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](https://msdn.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool).</span><span class="sxs-lookup"><span data-stu-id="4bbfa-114">To learn more about manually creating an app package, see [Create an app package with the MakeAppx.exe tool](https://msdn.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool).</span></span> 

- **<span data-ttu-id="4bbfa-115">Ein gültiges Signaturzertifikat</span><span class="sxs-lookup"><span data-stu-id="4bbfa-115">A valid signing certificate</span></span>**  
    <span data-ttu-id="4bbfa-116">Weitere Informationen zum Erstellen oder Importieren ein gültiges Signaturzertifikats finden Sie unter [Erstellen oder Importieren eines Zertifikats für die Paketsignierung](https://msdn.microsoft.com/windows/uwp/packaging/create-certificate-package-signing).</span><span class="sxs-lookup"><span data-stu-id="4bbfa-116">For more information about creating or importing a valid signing certificate, see [Create or import a certificate for package signing](https://msdn.microsoft.com/windows/uwp/packaging/create-certificate-package-signing).</span></span>

- **<span data-ttu-id="4bbfa-117">SignTool.exe</span><span class="sxs-lookup"><span data-stu-id="4bbfa-117">SignTool.exe</span></span>**  
    <span data-ttu-id="4bbfa-118">Abhängig vom Installationspfad des SDK befindet sich **SignTool** an folgenden Speicherorten auf Ihrem Windows10-PC:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-118">Based on your installation path of the SDK, this is where **SignTool** is on your Windows 10 PC:</span></span>
    - <span data-ttu-id="4bbfa-119">x86: C:\Programme (x86)\Windows Kits\10\bin\x86\SignTool.exe</span><span class="sxs-lookup"><span data-stu-id="4bbfa-119">x86: C:\Program Files (x86)\Windows Kits\10\bin\x86\SignTool.exe</span></span>
    - <span data-ttu-id="4bbfa-120">x64: C:\Programme (x86)\Windows Kits\10\bin\x64\SignTool.exe</span><span class="sxs-lookup"><span data-stu-id="4bbfa-120">x64: C:\Program Files (x86)\Windows Kits\10\bin\x64\SignTool.exe</span></span>

## <a name="using-signtool"></a><span data-ttu-id="4bbfa-121">Verwenden von SignTool</span><span class="sxs-lookup"><span data-stu-id="4bbfa-121">Using SignTool</span></span>

<span data-ttu-id="4bbfa-122">**SignTool** kann zum Signieren von Dateien, Überprüfen von Signaturen oder Zeitstempeln, Entfernen von Signaturen und mehr verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-122">**SignTool** can be used to sign files, verify signatures or timestamps, remove signatures, and more.</span></span> <span data-ttu-id="4bbfa-123">Um ein App-Paket zu signieren, benötigen Sie den Befehl **sign**.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-123">For the purpose of signing an app package, we will focus on the **sign** command.</span></span> <span data-ttu-id="4bbfa-124">Vollständige Informationen zu **SignTool** finden Sie auf der [SignTool](https://msdn.microsoft.com/library/windows/desktop/aa387764.aspx)-Referenzseite.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-124">For full information on **SignTool**, see the [SignTool](https://msdn.microsoft.com/library/windows/desktop/aa387764.aspx) reference page.</span></span> 

### <a name="determine-the-hash-algorithm"></a><span data-ttu-id="4bbfa-125">Ermitteln des Hashalgorithmus</span><span class="sxs-lookup"><span data-stu-id="4bbfa-125">Determine the hash algorithm</span></span>
<span data-ttu-id="4bbfa-126">Wenn Sie mit **SignTool** Ihr App-Paket oder -Bündel signieren, muss der in **SignTool** verwendete Hashalgorithmus derselbe Algorithmus sein, den Sie beim Packen Ihre App verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-126">When using **SignTool** to sign your app package or bundle, the hash algorithm used in **SignTool** must be the same algorithm you used to package your app.</span></span> <span data-ttu-id="4bbfa-127">Wenn Sie z.B. **MakeAppx.exe** verwendet haben, um Ihr App-Paket mit den Standardeinstellungen zu erstellen, müssen Sie SHA256 in **SignTool** angeben, da das der von **MakeAppx.exe** verwendete Standardalgorithmus ist.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-127">For example, if you used **MakeAppx.exe** to create your app package with the default settings, you must specify SHA256 when using **SignTool** since that's the default algorithm used by **MakeAppx.exe**.</span></span>

<span data-ttu-id="4bbfa-128">Um herauszufinden, welcher Hashalgorithmus beim Packen einer App verwendet wurde, extrahieren Sie den Inhalt des App-Pakets und überprüfen die Datei AppxBlockMap.xml.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-128">To find out which hash algorithm was used while packaging your app, extract the contents of the app package and inspect the AppxBlockMap.xml file.</span></span> <span data-ttu-id="4bbfa-129">Weitere Informationen zum Entpacken/Extrahieren eines App-Pakets finden Sie unter [Extrahieren von Dateien aus einem Paket oder Bündel](https://msdn.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool#extract-files-from-a-package-or-bundle).</span><span class="sxs-lookup"><span data-stu-id="4bbfa-129">To learn how to unpack/extract an app package, see [Extract files from a package or bundle](https://msdn.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool#extract-files-from-a-package-or-bundle).</span></span> <span data-ttu-id="4bbfa-130">Die Hashmethode befindet sich im BlockMap-Element und besitzt dieses Format:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-130">The hash method is in the BlockMap element and has this format:</span></span>
```
<BlockMap xmlns="http://schemas.microsoft.com/appx/2010/blockmap" 
HashMethod="http://www.w3.org/2001/04/xmlenc#sha256">
```

<span data-ttu-id="4bbfa-131">Die folgende Tabelle enthält alle HashMethod-Werte und den entsprechenden Hashalgorithmus:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-131">This table shows each HashMethod value and its corresponding hash algorithm:</span></span>


| <span data-ttu-id="4bbfa-132">HashMethod-Wert</span><span class="sxs-lookup"><span data-stu-id="4bbfa-132">HashMethod value</span></span>                              | <span data-ttu-id="4bbfa-133">Hashalgorithmus</span><span class="sxs-lookup"><span data-stu-id="4bbfa-133">Hash Algorithm</span></span> |
|-----------------------------------------------|----------------|
| http://www.w3.org/2001/04/xmlenc#sha256       | <span data-ttu-id="4bbfa-134">SHA256</span><span class="sxs-lookup"><span data-stu-id="4bbfa-134">SHA256</span></span>         |
| http://www.w3.org/2001/04/xmldsig-more#sha384 | <span data-ttu-id="4bbfa-135">SHA384</span><span class="sxs-lookup"><span data-stu-id="4bbfa-135">SHA384</span></span>         |
| http://www.w3.org/2001/04/xmlenc#sha512       | <span data-ttu-id="4bbfa-136">SHA512</span><span class="sxs-lookup"><span data-stu-id="4bbfa-136">SHA512</span></span>         |

> [!NOTE]
> <span data-ttu-id="4bbfa-137">Da der Standardalgorithmus von **SignTool** SHA1 ist (nicht verfügbar in **MakeAppx.exe**), müssen Sie immer einen Hashalgorithmus angeben, wenn Sie **SignTool** verwenden.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-137">Since **SignTool**'s default algorithm is SHA1 (not available in **MakeAppx.exe**), you must always specify a hash algorithm when using **SignTool**.</span></span>

### <a name="sign-the-app-package"></a><span data-ttu-id="4bbfa-138">Signieren des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="4bbfa-138">Sign the app package</span></span>

<span data-ttu-id="4bbfa-139">Wenn Sie über alle benötigten Voraussetzungen verfügen und festgestellt haben, welcher Hashalgorithmus beim Packen der App verwendet wurde, können Sie mit dem Signieren der App beginnen.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-139">Once you have all of the prerequisites and you've determined which hash algorithm was used to package your app, you're ready to sign it.</span></span> 

<span data-ttu-id="4bbfa-140">Die allgemeine Befehlszeilensyntax für die Paketsignierung mit **SignTool** lautet:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-140">The general command line syntax for **SignTool** package signing is:</span></span>
```
SignTool sign [options] <filename(s)>
```

<span data-ttu-id="4bbfa-141">Das Zertifikat zum Signieren Ihrer App muss entweder eine PFX-Datei sein oder in einem Zertifikatspeicher installiert sein.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-141">The certificate used to sign your app must be either a .pfx file or be installed in a certificate store.</span></span>

<span data-ttu-id="4bbfa-142">Um Ihr App-Paket mit einem Zertifikat aus einer PFX-Datei zu signieren, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-142">To sign your app package with a certificate from a .pfx file, use the following syntax:</span></span>
```
SignTool sign /fd <Hash Algorithm> /a /f <Path to Certificate>.pfx /p <Your Password> <File path>.appx
```
```
SignTool sign /fd <Hash Algorithm> /a /f <Path to Certificate>.pfx /p <Your Password> <File path>.msix
```
<span data-ttu-id="4bbfa-143">Beachten Sie, dass **SignTool** mit der Option `/a` automatisch das beste Zertifikat auswählt.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-143">Note that the `/a` option allows **SignTool** to choose the best certificate automatically.</span></span>

<span data-ttu-id="4bbfa-144">Wenn das Zertifikat keine PFX-Datei ist, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-144">If your certificate is not a .pfx file, use the following syntax:</span></span>
```
SignTool sign /fd <Hash Algorithm> /n <Name of Certificate> <File Path>.appx
```
```
SignTool sign /fd <Hash Algorithm> /n <Name of Certificate> <File Path>.msix
```

<span data-ttu-id="4bbfa-145">Alternativ können Sie den SHA1-Hash des gewünschten Zertifikats anstelle von &lt;Name of Certificate&gt; mit der folgenden Syntax angeben:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-145">Alternatively, you can specify the SHA1 hash of the desired certificate instead of &lt;Name of Certificate&gt; using this syntax:</span></span>
```
SignTool sign /fd <Hash Algorithm> /sha1 <SHA1 hash> <File Path>.appx
```
```
SignTool sign /fd <Hash Algorithm> /sha1 <SHA1 hash> <File Path>.msix
```

<span data-ttu-id="4bbfa-146">Beachten Sie, dass einige Zertifikate kein Kennwort verwenden.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-146">Note that some certificates do not use a password.</span></span> <span data-ttu-id="4bbfa-147">Wenn Ihr Zertifikat über kein Kennwort verfügt, geben Sie „/p &lt;Your Password&gt;” in der Beispielbefehle nicht an.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-147">If your certificate does not have a password, omit "/p &lt;Your Password&gt;" from the sample commands.</span></span>

<span data-ttu-id="4bbfa-148">Wenn Ihr App-Paket mit einem gültigen Zertifikat signiert ist, können Sie das Paket in den Store hochladen.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-148">Once your app package is signed with a valid certificate, you're ready to upload your package to the Store.</span></span> <span data-ttu-id="4bbfa-149">Weitere Informationen zum Hochladen und Übermitteln von Apps an den Store finden Sie unter [App-Übermittlungen](https://msdn.microsoft.com/windows/uwp/publish/app-submissions).</span><span class="sxs-lookup"><span data-stu-id="4bbfa-149">For more guidance on uploading and submitting apps to the Store, see [App submissions](https://msdn.microsoft.com/windows/uwp/publish/app-submissions).</span></span>

## <a name="common-errors-and-troubleshooting"></a><span data-ttu-id="4bbfa-150">Häufige Fehler und Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="4bbfa-150">Common errors and troubleshooting</span></span>
<span data-ttu-id="4bbfa-151">Die häufigsten Fehlertypen bei der Verwendung von **SignTool** sind interne Fehler, die in der Regel wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-151">The most common types of errors when using **SignTool** are internal and typically look something like this:</span></span>

```
SignTool Error: An unexpected internal error has occurred.
Error information: "Error: SignerSign() failed." (-2147024885 / 0x8007000B) 
```

<span data-ttu-id="4bbfa-152">Wenn der Fehlercode mit 0x8008 beginnt, z.B. 0x80080206 (APPX_E_CORRUPT_CONTENT), ist das Paket, das gerade signiert wird, nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-152">If the error code starts with 0x8008, such as 0x80080206 (APPX_E_CORRUPT_CONTENT), the package being signed is invalid.</span></span> <span data-ttu-id="4bbfa-153">Wenn Sie diesen Fehlertyp erhalten, müssen Sie das Paket neu erstellen und **SignTool** erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-153">If you get this type of error you must rebuild the package and run **SignTool** again.</span></span>

<span data-ttu-id="4bbfa-154">**SignTool** verfügt über eine Debugoption, um Zertifikatfehler anzuzeigen und zu filtern.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-154">**SignTool** has a debug option available to show certificate errors and filtering.</span></span> <span data-ttu-id="4bbfa-155">Um die Debugfunktion zu verwenden, geben Sie die Option `/debug` direkt hinter `sign` und dann den vollständigen **SignTool**-Befehl an.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-155">To use the debugging feature, place the `/debug` option directly after `sign`, followed by the full **SignTool** command.</span></span>
```
SignTool sign /debug [options]
``` 

<span data-ttu-id="4bbfa-156">Ein allgemeinerer Fehler ist 0x8007000B.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-156">A more common error is 0x8007000B.</span></span> <span data-ttu-id="4bbfa-157">Zu diesem Fehlertyp finden Sie weitere Informationen im Ereignisprotokoll.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-157">For this type of error, you can find more information in the event log.</span></span>
 
<span data-ttu-id="4bbfa-158">So suchen Sie weitere Informationen im Ereignisprotokoll</span><span class="sxs-lookup"><span data-stu-id="4bbfa-158">To find more information in the event log:</span></span>
- <span data-ttu-id="4bbfa-159">Führen Sie Eventvwr.msc aus.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-159">Run Eventvwr.msc</span></span>
- <span data-ttu-id="4bbfa-160">Öffnen Sie das Ereignisprotokoll: Ereignisanzeige (Lokal) -> Anwendungs- und Dienstprotokolle -> Microsoft -> Windows--> AppxPackagingOM -> Microsoft-Windows-AppxPackaging/Operational.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-160">Open the event log: Event Viewer (Local) -> Applications and Services Logs -> Microsoft -> Windows -> AppxPackagingOM -> Microsoft-Windows-AppxPackaging/Operational</span></span>
- <span data-ttu-id="4bbfa-161">Suchen Sie das letzte Fehlerereignis.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-161">Find the most recent error event</span></span>

<span data-ttu-id="4bbfa-162">Der interne Fehler 0x8007000B entspricht in der Regel einem der folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="4bbfa-162">The internal error 0x8007000B usually corresponds to one of these values:</span></span>

| **<span data-ttu-id="4bbfa-163">Ereignis-ID</span><span class="sxs-lookup"><span data-stu-id="4bbfa-163">Event ID</span></span>** | **<span data-ttu-id="4bbfa-164">Beispiel der Ereigniszeichenfolge</span><span class="sxs-lookup"><span data-stu-id="4bbfa-164">Example event string</span></span>** | **<span data-ttu-id="4bbfa-165">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="4bbfa-165">Suggestion</span></span>** |
|--------------|--------------------------|----------------|
| <span data-ttu-id="4bbfa-166">150</span><span class="sxs-lookup"><span data-stu-id="4bbfa-166">150</span></span>          | <span data-ttu-id="4bbfa-167">Fehler 0x8007000B: Der Name des Herausgebers des App-Manifests (CN=Contoso) muss mit dem Namen des Antragstellers des Signaturzertifikats (CN=Contoso, C=US) übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-167">error 0x8007000B: The app manifest publisher name (CN=Contoso) must match the subject name of the signing certificate (CN=Contoso, C=US).</span></span> | <span data-ttu-id="4bbfa-168">Der Name des Herausgebers des App-Manifests muss exakt mit dem Namen des Antragstellers der Signatur übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-168">The app manifest publisher name must exactly match the subject name of the signing.</span></span>               |
| <span data-ttu-id="4bbfa-169">151.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-169">151</span></span>          | <span data-ttu-id="4bbfa-170">Fehler 0x8007000B: Die angegebene Hashmethode der Signatur (SHA512) muss mit der Hashmethode, die in der App-Paketblockzuordnung (SHA256) verwendet wurde, übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-170">error 0x8007000B: The signature hash method specified (SHA512) must match the hash method used in the app package block map (SHA256).</span></span>     | <span data-ttu-id="4bbfa-171">Der im Parameter /fd angegebene Hashalgorithmus ist falsch.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-171">The hashAlgorithm specified in the /fd parameter is incorrect.</span></span> <span data-ttu-id="4bbfa-172">Führen Sie **SignTool** erneut mit dem Hashalgorithmus aus, der mit der App-Paketblockzuordnung übereinstimmt (mit dem das App-Paket erstellt wurde).</span><span class="sxs-lookup"><span data-stu-id="4bbfa-172">Rerun **SignTool** using hashAlgorithm that matches the app package block map (used to create the app package)</span></span>  |
| <span data-ttu-id="4bbfa-173">152</span><span class="sxs-lookup"><span data-stu-id="4bbfa-173">152</span></span>          | <span data-ttu-id="4bbfa-174">Fehler 0x8007000B: Der Inhalt des App-Pakets muss für die Blockzuordnung gültig sein.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-174">error 0x8007000B: The app package contents must validate against its block map.</span></span>                                                           | <span data-ttu-id="4bbfa-175">Das App-Paket ist beschädigt und muss neu erstellt werden, um eine neue Blockzuordnung zu generieren.</span><span class="sxs-lookup"><span data-stu-id="4bbfa-175">The app package is corrupt and needs to be rebuilt to generate a new block map.</span></span> <span data-ttu-id="4bbfa-176">Weitere Informationen zum Erstellen eines App-Pakets finden Sie unter [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](https://msdn.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool).</span><span class="sxs-lookup"><span data-stu-id="4bbfa-176">For more about creating an app package, see [Create an app package with the MakeAppx.exe tool](https://msdn.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool)</span></span> |