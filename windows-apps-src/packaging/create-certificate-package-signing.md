---
author: laurenhughes
title: Erstellen eines Paketsignaturzertifikats
description: PowerShell-Tools helfen bei der Erstellung und beim Export eines App-Paketsignaturzertifikats.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 7bc2006f-fc5a-4ff6-b573-60933882caf8
ms.localizationpriority: medium
ms.openlocfilehash: 448b4405381c3100f8b92abd0f2889799c0354fc
ms.sourcegitcommit: e6daa7ff878f2f0c7015aca9787e7f2730abcfbf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "4309902"
---
# <a name="create-a-certificate-for-package-signing"></a><span data-ttu-id="29448-104">Erstellen eines Paketsignaturzertifikats</span><span class="sxs-lookup"><span data-stu-id="29448-104">Create a certificate for package signing</span></span>


<span data-ttu-id="29448-105">In diesem Artikel wird die Erstellung und der Export eines App-Paketsignaturzertifikats mithilfe von PowerShell-Tools erläutert.</span><span class="sxs-lookup"><span data-stu-id="29448-105">This article explains how to create and export a certificate for app package signing using PowerShell tools.</span></span> <span data-ttu-id="29448-106">Es wird empfohlen, Visual Studio zum [Verpacken von UWP-Apps](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) zu verwenden. Sie können allerdings auch weiterhin App-Pakete für den Store manuell verpacken, wenn Sie Ihre App nicht mit Visual Studio erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="29448-106">It's recommended that you use Visual Studio for [Packaging UWP apps](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps), but you can still package a Store ready app manually if you did not use Visual Studio to develop your app.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="29448-107">Wenn Sie Visual Studio zum Entwickeln der App verwendet haben, wird empfohlen, dass Sie den Visual Studio-Assistenten zum Importieren eines Zertifikats und Signieren des App-Pakets verwenden.</span><span class="sxs-lookup"><span data-stu-id="29448-107">If you used Visual Studio to develop your app, it's recommended that you use the Visual Studio wizard to import a certificate and sign your app package.</span></span> <span data-ttu-id="29448-108">Weitere Informationen finden Sie unter [Verpacken einer UWP-App mit Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="29448-108">For more information, see [Package a UWP app with Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="29448-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="29448-109">Prerequisites</span></span>

- **<span data-ttu-id="29448-110">Verpackte oder unverpackte Apps</span><span class="sxs-lookup"><span data-stu-id="29448-110">A packaged or unpackaged app</span></span>**  
<span data-ttu-id="29448-111">Eine App mit einer AppxManifest.xml-Datei.</span><span class="sxs-lookup"><span data-stu-id="29448-111">An app containing an AppxManifest.xml file.</span></span> <span data-ttu-id="29448-112">Sie müssen während der Erstellung des Zertifikats auf die Manifestdatei verweisen, die zum Signieren der endgültigen Version des App-Pakets verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="29448-112">You will need to reference the manifest file while creating the certificate that will be used to sign the final app package.</span></span> <span data-ttu-id="29448-113">Details zum manuellen Verpacken von Apps finden Sie unter [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](https://msdn.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool).</span><span class="sxs-lookup"><span data-stu-id="29448-113">For details on how to manually package an app, see [Create an app package with the MakeAppx.exe tool](https://msdn.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool).</span></span>

- **<span data-ttu-id="29448-114">PKI-Cmdlets (Public Key-Infrastruktur)</span><span class="sxs-lookup"><span data-stu-id="29448-114">Public Key Infrastructure (PKI) Cmdlets</span></span>**  
<span data-ttu-id="29448-115">Sie benötigen die PKI-Cmdlets zum Erstellen und Exportieren Ihres Signaturzertifikats.</span><span class="sxs-lookup"><span data-stu-id="29448-115">You need PKI cmdlets to create and export your signing certificate.</span></span> <span data-ttu-id="29448-116">For more information, see [Public Key-Infrastruktur-Cmdlets](https://docs.microsoft.com/powershell/module/pkiclient/).</span><span class="sxs-lookup"><span data-stu-id="29448-116">For more information, see [Public Key Infrastructure Cmdlets](https://docs.microsoft.com/powershell/module/pkiclient/).</span></span>

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="29448-117">Erstellen eines selbstsignierten Zertifikats</span><span class="sxs-lookup"><span data-stu-id="29448-117">Create a self signed certificate</span></span>

<span data-ttu-id="29448-118">Ein selbstsigniertes Zertifikat eignet sich für das Testen Ihrer App, bevor es im Store veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="29448-118">A self signed certificate is useful for testing your app before you're ready to publish it to the store.</span></span> <span data-ttu-id="29448-119">Folgen Sie den in diesem Abschnitt beschriebenen Anweisungen zum Erstellen eines selbstsignierten Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="29448-119">Follow the steps outlined in this section to create a self signed certificate.</span></span>

### <a name="determine-the-subject-of-your-packaged-app"></a><span data-ttu-id="29448-120">Festlegen des Betreffs Ihres App-Pakets</span><span class="sxs-lookup"><span data-stu-id="29448-120">Determine the subject of your packaged app</span></span>  

<span data-ttu-id="29448-121">Zur Verwendung eines Zertifikats für die Signatur des App-Pakets **muss** der Betreff im Zertifikat dem Abschnitt „Herausgeber” des App-Manifests entsprechen.</span><span class="sxs-lookup"><span data-stu-id="29448-121">To use a certificate to sign your app package, the "Subject" in the certificate **must** match the "Publisher" section in your app's manifest.</span></span>

<span data-ttu-id="29448-122">Beispielsweise sollte der Abschnitt „Identität” in der „AppxManifest.xml”-Datei Ihrer App etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="29448-122">For example, the "Identity" section in your app's AppxManifest.xml file should look something like this:</span></span>
```
  <Identity Name="Contoso.AssetTracker" 
    Version="1.0.0.0" 
    Publisher="CN=Contoso Software, O=Contoso Corporation, C=US"/>
```

<span data-ttu-id="29448-123">Der „Herausgeber” ist in diesem Fall „CN=Contoso Software, O=Contoso Corporation, C=US", was zum Erstellen eines Zertifikats verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="29448-123">The "Publisher", in this case, is "CN=Contoso Software, O=Contoso Corporation, C=US" which needs to be used for creating your certificate.</span></span> 

### <a name="use-new-selfsignedcertificate-to-create-a-certificate"></a><span data-ttu-id="29448-124">Verwenden von **New-SelfSignedCertificate** zum Erstellen eines Zertifikats</span><span class="sxs-lookup"><span data-stu-id="29448-124">Use **New-SelfSignedCertificate** to create a certificate</span></span>
<span data-ttu-id="29448-125">Verwenden Sie das PowerShell-Cmdlet **New-SelfSignedCertificate** zum Erstellen eines selbstsignierten Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="29448-125">Use the **New-SelfSignedCertificate** PowerShell cmdlet to create a self signed certificate.</span></span> <span data-ttu-id="29448-126">**New-SelfSignedCertificate** verfügt über mehrere anpassbare Parameter. Bei diesem Artikel konzentrieren wir uns allerdings auf das Erstellen eines einfachen Zertifikats, das mit **SignTool** funktioniert.</span><span class="sxs-lookup"><span data-stu-id="29448-126">**New-SelfSignedCertificate** has several parameters for customization, but for the purpose of this article, we'll focus on creating a simple certificate that will work with **SignTool**.</span></span> <span data-ttu-id="29448-127">Weitere Beispiele und Verwendungen dieses Cmdlets finden Sie unter [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/New-SelfSignedCertificate).</span><span class="sxs-lookup"><span data-stu-id="29448-127">For more examples and uses of this cmdlet, see [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/New-SelfSignedCertificate).</span></span>

<span data-ttu-id="29448-128">Basierend auf der „AppxManifest.xml”-Datei aus dem vorherigen Beispiel, sollten Sie folgende Syntax verwenden, um ein Zertifikat zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="29448-128">Based on the AppxManifest.xml file from the previous example, you should use the following syntax to create a certificate.</span></span> <span data-ttu-id="29448-129">In einer PowerShell-Eingabeaufforderung mit erhöhten Rechten:</span><span class="sxs-lookup"><span data-stu-id="29448-129">In an elevated PowerShell prompt:</span></span>
```
New-SelfSignedCertificate -Type Custom -Subject "CN=Contoso Software, O=Contoso Corporation, C=US" -KeyUsage DigitalSignature -FriendlyName <Your Friendly Name> -CertStoreLocation "Cert:\LocalMachine\My"
```

<span data-ttu-id="29448-130">Nach dem Ausführen dieses Befehls wird das Zertifikat dem lokalen Zertifikatspeicher hinzugefügt, wie im Parameter ‑CertStoreLocation angegeben.</span><span class="sxs-lookup"><span data-stu-id="29448-130">After running this command, the certificate will be added to the local certificate store, as specified in the "-CertStoreLocation" parameter.</span></span> <span data-ttu-id="29448-131">Das Ergebnis des Befehls erzeugt auch der Fingerabdruck des Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="29448-131">The result of the command will also produce the certificate's thumbprint.</span></span>  

**<span data-ttu-id="29448-132">Hinweis:</span><span class="sxs-lookup"><span data-stu-id="29448-132">Note</span></span>**  
<span data-ttu-id="29448-133">Sie können das Zertifikat mithilfe der folgenden Befehle in einem PowerShell-Fenster anzeigen:</span><span class="sxs-lookup"><span data-stu-id="29448-133">You can view your certificate in a PowerShell window by using the following commands:</span></span>
```
Set-Location Cert:\LocalMachine\My
Get-ChildItem | Format-Table Subject, FriendlyName, Thumbprint
```
<span data-ttu-id="29448-134">Dies zeigt alle Zertifikate in Ihrem lokalen Speicher an.</span><span class="sxs-lookup"><span data-stu-id="29448-134">This will display all of the certificates in your local store.</span></span>

## <a name="export-a-certificate"></a><span data-ttu-id="29448-135">Exportieren eines Zertifikats</span><span class="sxs-lookup"><span data-stu-id="29448-135">Export a certificate</span></span> 

<span data-ttu-id="29448-136">Verwenden Sie das **Export-PfxCertificate**-Cmdlet, um das Zertifikat im lokalen Speicher auf eine private Informationsaustausch-Datei (PFX) zu exportieren.</span><span class="sxs-lookup"><span data-stu-id="29448-136">To export the certificate in the local store to a Personal Information Exchange (PFX) file, use the **Export-PfxCertificate** cmdlet.</span></span>

<span data-ttu-id="29448-137">Sie müssen bei der Verwendung von **Export-PfxCertificate** entweder ein Kennwort erstellen und verwenden oder den Parameter „‑ProtectTo” verwenden, um anzugeben, welche Benutzer oder Gruppen ohne Kennwort auf die Datei zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="29448-137">When using **Export-PfxCertificate**, you must either create and use a password or use the "-ProtectTo" parameter to specify which users or groups can access the file without a password.</span></span> <span data-ttu-id="29448-138">Es wird eine Fehlermeldung angezeigt, wenn Sie weder den „-Kennwort”-, noch den „-ProtectTo”-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="29448-138">Note that an error will be displayed if you don't use either the "-Password" or "-ProtectTo" parameter.</span></span>

- **<span data-ttu-id="29448-139">Verwendung von Kennwörtern</span><span class="sxs-lookup"><span data-stu-id="29448-139">Password usage</span></span>**
```
$pwd = ConvertTo-SecureString -String <Your Password> -Force -AsPlainText 
Export-PfxCertificate -cert "Cert:\LocalMachine\My\<Certificate Thumbprint>" -FilePath <FilePath>.pfx -Password $pwd
```

- **<span data-ttu-id="29448-140">Verwendung von „ProtectTo”</span><span class="sxs-lookup"><span data-stu-id="29448-140">ProtectTo usage</span></span>**
```
Export-PfxCertificate -cert Cert:\LocalMachine\My\<Certificate Thumbprint> -FilePath <FilePath>.pfx -ProtectTo <Username or group name>
```

<span data-ttu-id="29448-141">Nachdem Sie Ihr Zertifikat erstellt und exportiert haben, sind Sie zum Signieren des App-Pakets mit **SignTool** bereit.</span><span class="sxs-lookup"><span data-stu-id="29448-141">After you create and export your certificate, you're ready to sign your app package with **SignTool**.</span></span> <span data-ttu-id="29448-142">Informationen zum nächsten Schritt bei der manuellen Verpackung finden Sie unter [Signieren eines App-Pakets mithilfe von SignTool](https://msdn.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).</span><span class="sxs-lookup"><span data-stu-id="29448-142">For the next step in the manual packaging process, see [Sign an app package using SignTool](https://msdn.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).</span></span>

## <a name="security-considerations"></a><span data-ttu-id="29448-143">Sicherheitsüberlegungen</span><span class="sxs-lookup"><span data-stu-id="29448-143">Security Considerations</span></span> 
<span data-ttu-id="29448-144">Das Hinzufügen eines Zertifikats zum [Zertifikatspeicher des lokalen Computers](https://msdn.microsoft.com/windows/hardware/drivers/install/local-machine-and-current-user-certificate-stores) wirkt sich auf die Zertifikatvertrauensstellung für alle Benutzer des Computers aus.</span><span class="sxs-lookup"><span data-stu-id="29448-144">By adding a certificate to [local machine certificate stores](https://msdn.microsoft.com/windows/hardware/drivers/install/local-machine-and-current-user-certificate-stores), you affect the certificate trust of all users on the computer.</span></span> <span data-ttu-id="29448-145">Sie sollten die Zertifikate entfernen, wenn sie nicht mehr erforderlich sind, um zu verhindern, dass diese die Systemvertrauensstellung gefährden.</span><span class="sxs-lookup"><span data-stu-id="29448-145">It is recommended that you remove those certificates when they are no longer necessary to prevent them from being used to compromise system trust.</span></span>
