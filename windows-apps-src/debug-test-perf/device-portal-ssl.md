---
author: PatrickFarley
ms.assetid: e04ebe3f-479c-4b48-99d8-3dd4bb9bfaf4
title: Bereitstellen eines Geräteportals mit einem benutzerdefinierten SSL-Zertifikat
description: TBD
ms.author: pafarley
ms.date: 07/11/2017
ms.topic: article
keywords: Windows 10, Uwp, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: 525c64ab289d26a4835168f410ac4ba3fc14343a
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7307277"
---
# <a name="provision-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="d9967-104">Bereitstellen eines Geräteportals mit einem benutzerdefinierten SSL-Zertifikat</span><span class="sxs-lookup"><span data-stu-id="d9967-104">Provision Device Portal with a custom SSL certificate</span></span>
<span data-ttu-id="d9967-105">In der Windows 10 Creators Update hinzugefügt Windows Device Portal eine Möglichkeit für Administratoren das Gerät ein benutzerdefiniertes Zertifikat für die Verwendung in HTTPS-Kommunikation zu installieren.</span><span class="sxs-lookup"><span data-stu-id="d9967-105">In the Windows 10 Creators Update, Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span> 

<span data-ttu-id="d9967-106">Während Sie dies auf Ihrem eigenen PC tun können, ist dieses Feature hauptsächlich für Unternehmen vorgesehen, die eine vorhandene Zertifikatinfrastruktur verfügen.</span><span class="sxs-lookup"><span data-stu-id="d9967-106">While you can do this on your own PC, this feature is mostly intended for enterprises that have an existing certificate infrastructure in place.</span></span>  

<span data-ttu-id="d9967-107">Z. B. möglicherweise ein Unternehmen eine Zertifizierungsstelle (CA), die verwendet wird zum Signieren von Zertifikaten für Intranetsites über HTTPS bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d9967-107">For example, a company might have a certificate authority (CA) that it uses to sign certificates for intranet websites served over HTTPS.</span></span> <span data-ttu-id="d9967-108">Dieses Feature steht oben in diesem Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="d9967-108">This feature stands on top of that infrastructure.</span></span> 

## <a name="overview"></a><span data-ttu-id="d9967-109">Übersicht</span><span class="sxs-lookup"><span data-stu-id="d9967-109">Overview</span></span>
<span data-ttu-id="d9967-110">Standardmäßig Device Portal generiert eine selbstsignierte Stammzertifizierungsstelle, und dann verwendet, die Sie um SSL-Zertifikate für jeden Endpunkt zu signieren, die er auf überwacht.</span><span class="sxs-lookup"><span data-stu-id="d9967-110">By default, Device Portal generates a self-signed root CA, and then uses that to sign SSL certificates for every endpoint it is listening on.</span></span> <span data-ttu-id="d9967-111">Dazu gehören `localhost`, `127.0.0.1`, und `::1` (IPv6 Localhost).</span><span class="sxs-lookup"><span data-stu-id="d9967-111">This includes `localhost`, `127.0.0.1`, and `::1` (IPv6 localhost).</span></span>

<span data-ttu-id="d9967-112">Ebenfalls enthalten sind Hostnamen des Geräts (z. B. `https://LivingRoomPC`) und jede Link-lokale IP-Adresse, die dem Gerät zugewiesene (bis zu zwei [IPv4, IPv6] pro Netzwerkadapter).</span><span class="sxs-lookup"><span data-stu-id="d9967-112">Also included are the device's hostname (for example, `https://LivingRoomPC`) and each link-local IP address assigned to the device (up to two [IPv4, IPv6] per network adaptor).</span></span> <span data-ttu-id="d9967-113">Sie sehen die Link-lokale IP-Adressen für ein Gerät, indem Sie das Netzwerk-Tool im Device Portal betrachten.</span><span class="sxs-lookup"><span data-stu-id="d9967-113">You can see the link-local IP addresses for a device by looking at the Networking tool in Device Portal.</span></span> <span data-ttu-id="d9967-114">Beginnen sie mit `10.` oder `192.` für IPv4 oder `fe80:` für IPv6.</span><span class="sxs-lookup"><span data-stu-id="d9967-114">They'll start with `10.` or `192.` for IPv4, or `fe80:` for IPv6.</span></span> 

<span data-ttu-id="d9967-115">In der Standardeinstellung möglicherweise eine Warnung zum Sicherheitszertifikat aufgrund der nicht vertrauenswürdigen Stammzertifizierungsstelle in Ihrem Browser angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d9967-115">In the default setup, a certificate warning may appear in your browser because of the untrusted root CA.</span></span> <span data-ttu-id="d9967-116">Genauer gesagt, ist das SSL-Zertifikat von Device Portal bereitgestellt von einer Stammzertifizierungsstelle signiert, die der Browser oder PC nicht vertraut.</span><span class="sxs-lookup"><span data-stu-id="d9967-116">Specifically, the SSL cert provided by Device Portal is signed by a root CA that the browser or PC doesn't trust.</span></span> <span data-ttu-id="d9967-117">Dies kann durch Erstellen einer neuen vertrauenswürdigen Stammzertifizierungsstelle behoben werden.</span><span class="sxs-lookup"><span data-stu-id="d9967-117">This can be fixed by creating a new trusted root CA.</span></span>

## <a name="create-a-root-ca"></a><span data-ttu-id="d9967-118">Erstellen einer Stammzertifizierungsstelle</span><span class="sxs-lookup"><span data-stu-id="d9967-118">Create a root CA</span></span>

<span data-ttu-id="d9967-119">Dies sollte nur erfolgen, wenn Ihr Unternehmen (oder Home) eine Zertifikatinfrastruktur einrichten besitzt und sollten nur einmal ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d9967-119">This should only be done if your company (or home) doesn't have a certificate infrastructure set up, and should only be done once.</span></span> <span data-ttu-id="d9967-120">Das folgende PowerShell-Skript erstellt eine Stammzertifizierungsstelle _WdpTestCA.cer_aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="d9967-120">The following PowerShell script creates a root CA called _WdpTestCA.cer_.</span></span> <span data-ttu-id="d9967-121">Installieren diese Datei auf des lokalen Computers vertrauenswürdige Stammzertifizierungsstellen bewirkt, dass das Gerät für SSL-Zertifikate zu vertrauen, die von diesem Stammzertifizierungsstelle signiert sind.</span><span class="sxs-lookup"><span data-stu-id="d9967-121">Installing this file to the local machine's Trusted Root Certification Authorities will cause your device to trust SSL certs that are signed by this root CA.</span></span> <span data-ttu-id="d9967-122">Sie können (und sollten) dieses CER-Datei auf jedem PC installieren, die Sie Windows Device Portal herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="d9967-122">You can (and should) install this .cer file on each PC that you want to connect to Windows Device Portal.</span></span>  

```PowerShell
$CN = "PickAName"
$OutputPath = "c:\temp\"

# Create root certificate authority
$FilePath = $OutputPath + "WdpTestCA.cer"
$Subject =  "CN="+$CN
$rootCA = New-SelfSignedCertificate -certstorelocation cert:\currentuser\my -Subject $Subject -HashAlgorithm "SHA512" -KeyUsage CertSign,CRLSign
$rootCAFile = Export-Certificate -Cert $rootCA -FilePath $FilePath
```

<span data-ttu-id="d9967-123">Nachdem diese erstellt wurde, können Sie die Datei _WdpTestCA.cer_ , SSL-Zertifikate zu signieren.</span><span class="sxs-lookup"><span data-stu-id="d9967-123">Once this is created, you can use the _WdpTestCA.cer_ file to sign SSL certs.</span></span> 

## <a name="create-an-ssl-certificate-with-the-root-ca"></a><span data-ttu-id="d9967-124">Erstellen Sie ein SSL-Zertifikat mit der Stammzertifizierungsstelle</span><span class="sxs-lookup"><span data-stu-id="d9967-124">Create an SSL certificate with the root CA</span></span>

<span data-ttu-id="d9967-125">SSL-Zertifikate verfügen über zwei wichtige Funktionen: schützen Ihre Verbindung über Verschlüsselung und überprüfen, ob Sie tatsächlich mit der in der Browser-Leiste angezeigten kommunizieren sind (Bing.com, 192.168.1.37, usw.) und keine schädliche von Drittanbietern.</span><span class="sxs-lookup"><span data-stu-id="d9967-125">SSL certificates have two critical functions: securing your connection through encryption and verifying that you are actually communicating with the address displayed in the browser bar (Bing.com, 192.168.1.37, etc.) and not a malicious third party.</span></span>

<span data-ttu-id="d9967-126">Das folgende PowerShell-Skript erstellt ein SSL-Zertifikat für die `localhost` Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="d9967-126">The following PowerShell script creates an SSL certificate for the `localhost` endpoint.</span></span> <span data-ttu-id="d9967-127">Jeden Endpunkt, die Device Portal überwacht benötigt ihr eigenes Zertifikat; Ersetzen Sie die `$IssuedTo` Argument im Skript mit jeweils unterschiedlichen Endpunkte für Ihr Gerät: der Hostname, Localhost und die IP-Adressen.</span><span class="sxs-lookup"><span data-stu-id="d9967-127">Each endpoint that Device Portal listens on needs its own certificate; you can replace the `$IssuedTo` argument in the script with each of the different endpoints for your device: the hostname, localhost, and the IP addresses.</span></span>

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

<span data-ttu-id="d9967-128">Wenn Sie über mehrere Geräte verfügen, können Sie die Localhost-PFX-Dateien wiederverwenden, aber Sie müssen dennoch IP-Adresse und den Hostnamen Zertifikate für jedes Gerät separat zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d9967-128">If you have multiple devices, you can reuse the localhost .pfx files, but you'll still need to create IP address and hostname certificates for each device separately.</span></span>

<span data-ttu-id="d9967-129">Wenn im Bündel PFX-Dateien generiert wird, müssen Sie diese in Windows Device Portal zu laden.</span><span class="sxs-lookup"><span data-stu-id="d9967-129">When the bundle of .pfx files is generated, you will need to load them into Windows Device Portal.</span></span> 

## <a name="provision-device-portal-with-the-certifications"></a><span data-ttu-id="d9967-130">Bereitstellen eines Geräteportals mit der Zertifizierung(en)</span><span class="sxs-lookup"><span data-stu-id="d9967-130">Provision Device Portal with the certification(s)</span></span>

<span data-ttu-id="d9967-131">Für jede PFX-Datei, die Sie erstellt haben für ein Gerät, müssen Sie den folgenden Befehl in einem Eingabeaufforderungsfenster mit erhöhten Rechten ausführen.</span><span class="sxs-lookup"><span data-stu-id="d9967-131">For each .pfx file that you've created for a device, you'll need to run the following command from an elevated command prompt.</span></span>

```
WebManagement.exe -SetCert <Path to .pfx file> <password for pfx> 
```

<span data-ttu-id="d9967-132">Finden Sie unter Verwendung des beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="d9967-132">See below for example usage:</span></span>
```
WebManagement.exe -SetCert localhost.pfx PickAPassword
WebManagement.exe -SetCert --1.pfx PickAPassword
WebManagement.exe -SetCert MyLivingRoomPC.pfx PickAPassword
```

<span data-ttu-id="d9967-133">Nachdem Sie die Zertifikate installiert haben, starten Sie den Dienst, damit die Änderungen wirksam werden können:</span><span class="sxs-lookup"><span data-stu-id="d9967-133">Once you have installed the certificates, simply restart the service so the changes can take effect:</span></span>

```
sc stop webmanagement
sc start webmanagement
```

> [!TIP]
> <span data-ttu-id="d9967-134">IP-Adressen können im Laufe der Zeit ändern.</span><span class="sxs-lookup"><span data-stu-id="d9967-134">IP addresses can change over time.</span></span>
<span data-ttu-id="d9967-135">Viele Netzwerke verwenden DHCP um IP-Adressen zu geben, damit Geräte keine immer die IP-Adresse erhalten, die sie zuvor verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d9967-135">Many networks use DHCP to give out IP addresses, so devices don't always get the same IP address they had previously.</span></span> <span data-ttu-id="d9967-136">Wenn Sie ein Zertifikat für eine IP-Adresse auf einem Gerät erstellt haben, die die Adresse des Geräts geändert hat, Windows Device Portal generiert ein neues Zertifikat mit der vorhandenen selbstsigniertes Zertifikat, und wird der Löschvorgang mit der, die Sie erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="d9967-136">If you've created a certificate for an IP address on a device and that device's address has changed, Windows Device Portal will generate a new certificate using the existing self-signed cert, and it will stop using the one you created.</span></span> <span data-ttu-id="d9967-137">Dadurch wird die Zertifikat-Warnseite in Ihrem Browser erneut angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d9967-137">This will cause the cert warning page to appear in your browser again.</span></span> <span data-ttu-id="d9967-138">Aus diesem Grund wird empfohlen, Herstellen einer Verbindung mit Ihren Geräten über ihrer Hostnamen, die Sie im Device Portal festlegen können.</span><span class="sxs-lookup"><span data-stu-id="d9967-138">For this reason, we recommend connecting to your devices through their hostnames, which you can set in Device Portal.</span></span> <span data-ttu-id="d9967-139">Diese bleibt unabhängig von der IP-Adressen.</span><span class="sxs-lookup"><span data-stu-id="d9967-139">These will stay the same regardless of IP addresses.</span></span>
