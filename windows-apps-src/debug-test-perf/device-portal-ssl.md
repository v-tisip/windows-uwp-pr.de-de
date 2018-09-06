---
author: PatrickFarley
ms.assetid: e04ebe3f-479c-4b48-99d8-3dd4bb9bfaf4
title: Bereitstellung Gerät Portal ein SSL-Zertifikat
description: TBD
ms.author: pafarley
ms.date: 07/11/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Device-portal
ms.localizationpriority: medium
ms.openlocfilehash: 1192c200cd42ab28cc7e763c06fd8a5638aa3400
ms.sourcegitcommit: 7aa1933e6970f878faf50d59e1f799b90afd7cc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "3373672"
---
# <a name="provision-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="c14eb-104">Bereitstellung Gerät Portal ein SSL-Zertifikat</span><span class="sxs-lookup"><span data-stu-id="c14eb-104">Provision Device Portal with a custom SSL certificate</span></span>
<span data-ttu-id="c14eb-105">Windows 10 Autoren Update hinzugefügt Windows Gerät Portal Gerät Administratoren installieren Sie ein Zertifikat für die Verwendung in HTTPS-Kommunikation.</span><span class="sxs-lookup"><span data-stu-id="c14eb-105">In the Windows 10 Creators Update, Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span> 

<span data-ttu-id="c14eb-106">Während Sie Ihren Computer hierzu wird dieses Feature hauptsächlich für Unternehmen vorgesehen, die ein vorhandenes Zertifikat Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="c14eb-106">While you can do this on your own PC, this feature is mostly intended for enterprises that have an existing certificate infrastructure in place.</span></span>  

<span data-ttu-id="c14eb-107">Beispielsweise müssen Unternehmen eine Zertifizierungsstelle (CA), die Zertifikate für Intranetwebsites über HTTPS bedient sich verwendet.</span><span class="sxs-lookup"><span data-stu-id="c14eb-107">For example, a company might have a certificate authority (CA) that it uses to sign certificates for intranet websites served over HTTPS.</span></span> <span data-ttu-id="c14eb-108">Dieses Feature steht, Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="c14eb-108">This feature stands on top of that infrastructure.</span></span> 

## <a name="overview"></a><span data-ttu-id="c14eb-109">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c14eb-109">Overview</span></span>
<span data-ttu-id="c14eb-110">Standardmäßig Gerät Portal selbstsignierte Stammzertifizierungsstelle generiert und verwendet, die Zertifikate für jeden Endpunkt anmelden abgehört wird.</span><span class="sxs-lookup"><span data-stu-id="c14eb-110">By default, Device Portal generates a self-signed root CA, and then uses that to sign SSL certificates for every endpoint it is listening on.</span></span> <span data-ttu-id="c14eb-111">Dies schließt `localhost`, `127.0.0.1`, und `::1` (IPv6 Localhost).</span><span class="sxs-lookup"><span data-stu-id="c14eb-111">This includes `localhost`, `127.0.0.1`, and `::1` (IPv6 localhost).</span></span>

<span data-ttu-id="c14eb-112">Ferner sind Hostname des Geräts (z. B. `https://LivingRoomPC`) und jeder Link-lokale IP-Adresse für das Gerät (bis zu zwei [IPv4, IPv6] pro Netzwerkadapter).</span><span class="sxs-lookup"><span data-stu-id="c14eb-112">Also included are the device's hostname (for example, `https://LivingRoomPC`) and each link-local IP address assigned to the device (up to two [IPv4, IPv6] per network adaptor).</span></span> <span data-ttu-id="c14eb-113">Die Link-lokale Adressen ein sehen mit dem Netzwerk in Gerät ansehen.</span><span class="sxs-lookup"><span data-stu-id="c14eb-113">You can see the link-local IP addresses for a device by looking at the Networking tool in Device Portal.</span></span> <span data-ttu-id="c14eb-114">Sie beginnen mit `10.` oder `192.` für IPv4 oder `fe80:` für IPv6.</span><span class="sxs-lookup"><span data-stu-id="c14eb-114">They'll start with `10.` or `192.` for IPv4, or `fe80:` for IPv6.</span></span> 

<span data-ttu-id="c14eb-115">In der Standardeinstellung kann eine zertifikatswarnung aufgrund der nicht vertrauenswürdigen Stammzertifizierungsstelle im Browser angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c14eb-115">In the default setup, a certificate warning may appear in your browser because of the untrusted root CA.</span></span> <span data-ttu-id="c14eb-116">Insbesondere wird Gerät Portal bereitgestellte SSL-Zertifikat von einer Stammzertifizierungsstelle signiert, das Browser oder Computer nicht vertrauen.</span><span class="sxs-lookup"><span data-stu-id="c14eb-116">Specifically, the SSL cert provided by Device Portal is signed by a root CA that the browser or PC doesn't trust.</span></span> <span data-ttu-id="c14eb-117">Dies kann durch Erstellen einer neuen vertrauenswürdigen Stammzertifizierungsstelle behoben werden.</span><span class="sxs-lookup"><span data-stu-id="c14eb-117">This can be fixed by creating a new trusted root CA.</span></span>

## <a name="create-a-root-ca"></a><span data-ttu-id="c14eb-118">Erstellen einer Stammzertifizierungsstelle</span><span class="sxs-lookup"><span data-stu-id="c14eb-118">Create a root CA</span></span>

<span data-ttu-id="c14eb-119">Dies sollte nur ausgeführt werden, wenn Ihr Unternehmen (oder Home) eine Zertifikatinfrastruktur eingerichtet und sollte nur einmal durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c14eb-119">This should only be done if your company (or home) doesn't have a certificate infrastructure set up, and should only be done once.</span></span> <span data-ttu-id="c14eb-120">PowerShell-Skript erstellt eine Stammzertifizierungsstelle _WdpTestCA.cer_aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="c14eb-120">The following PowerShell script creates a root CA called _WdpTestCA.cer_.</span></span> <span data-ttu-id="c14eb-121">Installieren diese Datei auf dem lokalen Computer vertrauenswürdige Stammzertifizierungsstellen führen Ihr Gerät SSL-Zertifikate zu vertrauen, die diese Zertifizierungsstelle signiert sind.</span><span class="sxs-lookup"><span data-stu-id="c14eb-121">Installing this file to the local machine's Trusted Root Certification Authorities will cause your device to trust SSL certs that are signed by this root CA.</span></span> <span data-ttu-id="c14eb-122">Sie können (und sollten) diese CER-Datei auf jedem PC installieren, die Windows-Geräte-Portal eine Verbindung herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="c14eb-122">You can (and should) install this .cer file on each PC that you want to connect to Windows Device Portal.</span></span>  

```PowerShell
$CN = "PickAName"
$OutputPath = "c:\temp\"

# Create root certificate authority
$FilePath = $OutputPath + "WdpTestCA.cer"
$Subject =  "CN="+$CN
$rootCA = New-SelfSignedCertificate -certstorelocation cert:\currentuser\my -Subject $Subject -HashAlgorithm "SHA512" -KeyUsage CertSign,CRLSign
$rootCAFile = Export-Certificate -Cert $rootCA -FilePath $FilePath
```

<span data-ttu-id="c14eb-123">Das erstellte _WdpTestCA.cer_ -Datei können Sie um SSL-Zertifikate zu signieren.</span><span class="sxs-lookup"><span data-stu-id="c14eb-123">Once this is created, you can use the _WdpTestCA.cer_ file to sign SSL certs.</span></span> 

## <a name="create-an-ssl-certificate-with-the-root-ca"></a><span data-ttu-id="c14eb-124">Erstellen Sie ein SSL-Zertifikat mit der Stamm-CA</span><span class="sxs-lookup"><span data-stu-id="c14eb-124">Create an SSL certificate with the root CA</span></span>

<span data-ttu-id="c14eb-125">Zertifikate haben zwei wichtige Funktionen: die Verbindung durch Verschlüsselung sichern und überprüfen, ob Sie tatsächlich mit der Browser-Leiste angezeigten kommunizieren (Bing.com, 192.168.1.37, usw.) und nicht böswillige Dritte.</span><span class="sxs-lookup"><span data-stu-id="c14eb-125">SSL certificates have two critical functions: securing your connection through encryption and verifying that you are actually communicating with the address displayed in the browser bar (Bing.com, 192.168.1.37, etc.) and not a malicious third party.</span></span>

<span data-ttu-id="c14eb-126">Das folgende PowerShell-Skript erstellt ein SSL-Zertifikat für die `localhost` Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="c14eb-126">The following PowerShell script creates an SSL certificate for the `localhost` endpoint.</span></span> <span data-ttu-id="c14eb-127">Jedes Gerät Portal überwacht Endpunkt benötigt ein eigenes Zertifikat. Ersetzen Sie die `$IssuedTo` Argument im Skript mit jedem der anderen Endpunkte für Ihr Gerät: den Hostnamen Localhost und die IP-Adressen.</span><span class="sxs-lookup"><span data-stu-id="c14eb-127">Each endpoint that Device Portal listens on needs its own certificate; you can replace the `$IssuedTo` argument in the script with each of the different endpoints for your device: the hostname, localhost, and the IP addresses.</span></span>

```PowerShell
$IssuedTo = "localhost"
$Password = "PickAPassword"
$OutputPath = "c:\temp\"
$rootCA = Import-Certificate -FilePath C:\temp\WdpTestCA.cer -CertStoreLocation Cert:\CurrentUser\My\

# Create SSL cert signed by certificate authority
$IssuedToClean = $IssuedTo.Replace(":", "-").Replace(" ", "_")
$FilePath = $OutputPath + $IssuedToClean + ".pfx"
$Subject = "CN="+$IssuedTo
$cert = New-SelfSignedCertificate -certstorelocation cert:\localmachine\my -Subject $Subject -DnsName $IssuedTo -Signer $rootCA -HashAlgorithm "SHA512"
$certFile = Export-PfxCertificate -cert $cert -FilePath $FilePath -Password (ConvertTo-SecureString -String $Password -Force -AsPlainText)
```

<span data-ttu-id="c14eb-128">Haben mehrere Geräte Localhost PFX-Dateien verwenden, aber Sie müssen noch IP-Adresse und Hostname Zertifikate für jedes Gerät separat erstellen.</span><span class="sxs-lookup"><span data-stu-id="c14eb-128">If you have multiple devices, you can reuse the localhost .pfx files, but you'll still need to create IP address and hostname certificates for each device separately.</span></span>

<span data-ttu-id="c14eb-129">Wenn das Bundle PFX-Dateien generiert, müssen Sie in Windows Gerät zu laden.</span><span class="sxs-lookup"><span data-stu-id="c14eb-129">When the bundle of .pfx files is generated, you will need to load them into Windows Device Portal.</span></span> 

## <a name="provision-device-portal-with-the-certifications"></a><span data-ttu-id="c14eb-130">Bereitstellung Gerät Portal mit der Zertifizierungen</span><span class="sxs-lookup"><span data-stu-id="c14eb-130">Provision Device Portal with the certification(s)</span></span>

<span data-ttu-id="c14eb-131">Für jede PFX-Datei, die Sie erstellt haben ein, müssen Sie den folgenden Befehl in ein Eingabeaufforderungsfenster mit erhöhten Rechten ausführen.</span><span class="sxs-lookup"><span data-stu-id="c14eb-131">For each .pfx file that you've created for a device, you'll need to run the following command from an elevated command prompt.</span></span>

```
WebManagement.exe -SetCert <Path to .pfx file> <password for pfx> 
```

<span data-ttu-id="c14eb-132">Siehe beispielsweise Verwendung:</span><span class="sxs-lookup"><span data-stu-id="c14eb-132">See below for example usage:</span></span>
```
WebManagement.exe -SetCert localhost.pfx PickAPassword
WebManagement.exe -SetCert --1.pfx PickAPassword
WebManagement.exe -SetCert MyLivingRoomPC.pfx PickAPassword
```

<span data-ttu-id="c14eb-133">Nachdem Sie die Zertifikate installiert haben, starten Sie den Dienst, damit die Änderungen wirksam werden können:</span><span class="sxs-lookup"><span data-stu-id="c14eb-133">Once you have installed the certificates, simply restart the service so the changes can take effect:</span></span>

```
sc stop webmanagement
sc start webmanagement
```

> [!TIP]
> <span data-ttu-id="c14eb-134">IP-Adressen können sich ändern.</span><span class="sxs-lookup"><span data-stu-id="c14eb-134">IP addresses can change over time.</span></span>
<span data-ttu-id="c14eb-135">Viele Netzwerke verwenden DHCP zu IP-Adressen, so dass Geräte immer dieselbe IP-Adresse nicht zuvor hatte.</span><span class="sxs-lookup"><span data-stu-id="c14eb-135">Many networks use DHCP to give out IP addresses, so devices don't always get the same IP address they had previously.</span></span> <span data-ttu-id="c14eb-136">Erstellte Zertifikat für IP-Adresse auf einem Gerät und die Adresse des Geräts geändert hat Windows Gerät Portal mit vorhandenen selbstsignierte Zertifikat ein neues Zertifikat generiert und mit dem erstellten wird beendet.</span><span class="sxs-lookup"><span data-stu-id="c14eb-136">If you've created a certificate for an IP address on a device and that device's address has changed, Windows Device Portal will generate a new certificate using the existing self-signed cert, and it will stop using the one you created.</span></span> <span data-ttu-id="c14eb-137">Dadurch wird der Warnseite Zertifikat erneut im Browser angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c14eb-137">This will cause the cert warning page to appear in your browser again.</span></span> <span data-ttu-id="c14eb-138">Aus diesem Grund wird empfohlen, mit der Geräte über ihre Hostnamen, der im Gerät Portal festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="c14eb-138">For this reason, we recommend connecting to your devices through their hostnames, which you can set in Device Portal.</span></span> <span data-ttu-id="c14eb-139">Diese werden IP-Adressen gleich bleiben.</span><span class="sxs-lookup"><span data-stu-id="c14eb-139">These will stay the same regardless of IP addresses.</span></span>
