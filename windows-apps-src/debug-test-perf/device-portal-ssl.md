---
author: PatrickFarley
ms.assetid: e04ebe3f-479c-4b48-99d8-3dd4bb9bfaf4
title: Bestimmung Gerät Portal mit einem benutzerdefinierten SSL-Zertifikat
description: TBD
ms.author: pafarley
ms.date: 07/11/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 2ccdef5c9462f18c1a7044fcc3a683c749177349
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1070903"
---
# <a name="provision-device-portal-with-a-custom-ssl-certificate"></a>Bestimmung Gerät Portal mit einem benutzerdefinierten SSL-Zertifikat
In der Windows-10 Ersteller Update hinzugefügt Windows Gerät Portal eine Möglichkeit für Administratoren zum Installieren eines benutzerdefinierten Zertifikats für die Verwendung in HTTPS-Kommunikation Gerät. 

Während Sie dies auf Ihrem eigenen Computer ausführen können, ist dieses Feature hauptsächlich für Unternehmen vorgesehen, die eine vorhandene Zertifikatinfrastruktur mit verfügen.  

Angenommen, haben ein Unternehmen eine Zertifizierungsstelle (CA), die zum Signieren von Zertifikaten für Intranetwebsites bedient über HTTPS verwendet. Dieses Feature steht oben in diesem Infrastruktur. 

## <a name="overview"></a>Übersicht
Standardmäßig Gerät Portal generiert eine selbstsignierte Stammzertifizierungsstelle, und klicken Sie dann zum Signieren von SSL-Zertifikaten für jede Endpunkt, den abgehört wird, verwendet. Dazu gehören `localhost`, `127.0.0.1`, und `::1` (Localhost IPv6).

Hostname des Geräts ebenfalls enthalten sind (beispielsweise `https://LivingRoomPC`) und jeder Link-Local-IP-Adresse zugewiesen, an dem Gerät (bis zu zwei [IPv4, IPv6] pro Netzwerkadapter). Sie können die Link-Local-IP-Adressen für ein Gerät verfolgen das Tool Networking im Portal Gerät sehen. Sie beginnen mit `10.` oder `192.` für IPv4 oder `fe80:` für IPv6. 

In der Standardeinstellung möglicherweise eine Warnung Zertifikat aufgrund der nicht vertrauenswürdigen Stammzertifizierungsstelle im Browser angezeigt. Insbesondere wird von Gerät Portal bereitgestellten SSL-Zertifikat von einer Stammzertifizierungsstelle signiert, das dem Browser oder PC vertrauen nicht. Dies kann durch Erstellen einer neuen vertrauenswürdigen Stammzertifizierungsstelle behoben werden.

## <a name="create-a-root-ca"></a>Erstellen einer Stammzertifizierungsstelle

Dies sollte nur ausgeführt werden, wenn Ihr Unternehmen (oder zu Hause) eine Zertifikatinfrastruktur eingerichtet hat und nur einmal ausgeführt werden soll. Das folgende PowerShell-Skript erstellt eine Stammzertifizierungsstelle _WdpTestCA.cer_aufgerufen. Installieren diese Datei auf des lokalen Computers vertrauenswürdige Stammzertifizierungsstellen bewirkt, dass Ihr Gerät, SSL-Zertifikate zu vertrauen, die von diesem Stammzertifikat der Zertifizierungsstelle signiert werden. Sie können (und sollten) dieser CER-Datei auf jedem Computer installieren, die Sie mit Windows-Gerät Portal verbinden möchten.  

```PowerShell
$CN = "PickAName"
$OutputPath = "c:\temp\"

# Create root certificate authority
$FilePath = $OutputPath + "WdpTestCA.cer"
$Subject =  "CN="+$CN
$rootCA = New-SelfSignedCertificate -certstorelocation cert:\currentuser\my -Subject $Subject -HashAlgorithm "SHA512" -KeyUsage CertSign,CRLSign
$rootCAFile = Export-Certificate -Cert $rootCA -FilePath $FilePath
```

Sobald diese erstellt wurde, können Sie die Datei _WdpTestCA.cer_ zum Signieren von SSL-Zertifikate verwenden. 

## <a name="create-an-ssl-certificate-with-the-root-ca"></a>Erstellen Sie ein SSL-Zertifikat mit der Stammzertifizierungsstelle

SSL-Zertifikate haben Sie zwei wichtige Funktionen: Sichern Ihrer Verbindung durch Verschlüsselung und überprüfen, dass die Kommunikation tatsächlich mit der Adresse im Browser Balken angezeigt werden (Bing.com, 192.168.1.37, usw.) und nicht böswillige Dritte.

Das folgende PowerShell-Skript erstellt ein SSL-Zertifikat für die `localhost` Endpunkt. Jeder Endpunkt, die überwacht Gerät Portal benötigt ihr eigenes Zertifikat. Ersetzen Sie die `$IssuedTo` Argument in das Skript mit jeder der verschiedenen Endpunkte für Ihr Gerät: der Hostname, Localhost und die IP-Adressen.

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

Wenn Sie mehrere Geräte verfügen, können Sie die Localhost PFX-Dateien wiederverwenden, aber Sie müssen weiterhin IP-Adresse und den Hostnamen Zertifikate für jedes Gerät separat zu erstellen.

Wenn das Bundle PFX-Dateien generiert wird, müssen Sie sie in Windows-Gerät Portal zu laden. 

## <a name="provision-device-portal-with-the-certifications"></a>Gerät-Portal mit der Zertifizierung(en) bereitgestellt werden soll

Für jede PFX-Datei, die Sie erstellt haben für ein Gerät, müssen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten ausführen.

```
WebManagement.exe -SetCert <Path to .pfx file> <password for pfx> 
```

Finden Sie unter Verwendung des beispielsweise:
```
WebManagement.exe -SetCert localhost.pfx PickAPassword
WebManagement.exe -SetCert --1.pfx PickAPassword
WebManagement.exe -SetCert MyLivingRoomPC.pfx PickAPassword
```

Nachdem Sie die Zertifikate installiert haben, starten Sie den Dienst, damit die Änderungen wirksam werden:

```
sc stop webmanagement
sc start webmanagement
```

> [!TIP]
> IP-Adressen können mit der Zeit ändern.
Viele Netzwerke verwenden DHCP, um IP-Adressen, sodass Geräte nicht immer dieselbe IP-Adresse erhalten, die sie zuvor hatten vergeben. Wenn Sie ein Zertifikat für eine IP-Adresse auf einem Gerät erstellt haben und, die die Adresse des Geräts geändert wurde, Windows Gerät Portal generiert ein neues Zertifikat mithilfe des vorhandenen selbstsignierten Zertifikats, und wird beendet die Schriftart, die Sie erstellt haben. Dadurch wird die Cert Warnung Seite im Browser erneut angezeigt. Aus diesem Grund wird empfohlen, eine Verbindung mit Ihrer Geräte über ihre Hostnamen, die Sie im Portal Gerät festlegen können. Diese bleiben gleich, unabhängig von der IP-Adressen.
