---
author: PatrickFarley
ms.assetid: e04ebe3f-479c-4b48-99d8-3dd4bb9bfaf4
title: Bereitstellen eines Geräteportals mit einem benutzerdefinierten SSL-Zertifikat
description: TBD
ms.author: pafarley
ms.date: 07/11/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: 1192c200cd42ab28cc7e763c06fd8a5638aa3400
ms.sourcegitcommit: 1938851dc132c60348f9722daf994b86f2ead09e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "4265029"
---
# <a name="provision-device-portal-with-a-custom-ssl-certificate"></a>Bereitstellen eines Geräteportals mit einem benutzerdefinierten SSL-Zertifikat
In Windows 10 Creators Update hinzugefügt Windows Device Portal eine Möglichkeit für Administratoren das Gerät ein Zertifikat für die Verwendung in HTTPS-Kommunikation zu installieren. 

Während Sie dies auf Ihrem eigenen PC tun können, ist dieses Feature hauptsächlich für Unternehmen vorgesehen, die eine vorhandene Zertifikatinfrastruktur verfügen.  

Z. B. möglicherweise ein Unternehmen eine Zertifizierungsstelle (CA), die verwendet wird zum Signieren von Zertifikaten für Intranetsites über HTTPS bereitgestellt. Dieses Feature steht oben in diesem Infrastruktur. 

## <a name="overview"></a>Übersicht
In der Standardeinstellung Device Portal generiert eine selbstsignierte Stammzertifizierungsstelle, und dann verwendet, die Sie um SSL-Zertifikate für jeden Endpunkt zu signieren, die er auf überwacht. Dazu gehören `localhost`, `127.0.0.1`, und `::1` (IPv6 Localhost).

Ebenfalls enthalten sind Hostnamen des Geräts (z. B. `https://LivingRoomPC`) und jede Link-lokale IP-Adresse, die dem Gerät zugewiesene (bis zu zwei [IPv4, IPv6] pro Netzwerkadapter). Sie können die Link-lokale IP-Adressen für ein Gerät anzeigen, indem Sie das Netzwerk-Tool im Device Portal betrachten. Beginnen sie mit `10.` oder `192.` für IPv4 oder `fe80:` für IPv6. 

In der Standardeinstellung möglicherweise eine zertifikatwarnung aufgrund der nicht vertrauenswürdigen Stammzertifizierungsstelle in Ihrem Browser angezeigt. Insbesondere wird das SSL-Zertifikat von Device Portal bereitgestellt von einer Stammzertifizierungsstelle signiert, die den Browser oder PC nicht vertraut. Dies kann durch Erstellen einer neuen vertrauenswürdigen Stammzertifizierungsstelle behoben werden.

## <a name="create-a-root-ca"></a>Erstellen einer Stammzertifizierungsstelle

Dies sollte nur durchgeführt werden, wenn Ihr Unternehmen (oder Home) eine Zertifikatinfrastruktur einrichten besitzt und sollten nur einmal ausgeführt werden. Das folgende PowerShell-Skript erstellt eine Stammzertifizierungsstelle _WdpTestCA.cer_aufgerufen. Installieren diese Datei auf des lokalen Computers vertrauenswürdige Stammzertifizierungsstellen bewirkt, dass das Gerät für SSL-Zertifikate zu vertrauen, die von diesem Stammzertifizierungsstelle signiert sind. Sie können (und sollten) dieses CER-Datei auf jedem PC installieren, die Sie Windows Device Portal herstellen möchten.  

```PowerShell
$CN = "PickAName"
$OutputPath = "c:\temp\"

# Create root certificate authority
$FilePath = $OutputPath + "WdpTestCA.cer"
$Subject =  "CN="+$CN
$rootCA = New-SelfSignedCertificate -certstorelocation cert:\currentuser\my -Subject $Subject -HashAlgorithm "SHA512" -KeyUsage CertSign,CRLSign
$rootCAFile = Export-Certificate -Cert $rootCA -FilePath $FilePath
```

Nach erstellt wurden, können Sie die Datei _WdpTestCA.cer_ verwenden, um SSL-Zertifikate zu signieren. 

## <a name="create-an-ssl-certificate-with-the-root-ca"></a>Erstellen Sie ein SSL-Zertifikat mit der Stammzertifizierungsstelle

SSL-Zertifikate verfügen über zwei wichtige Funktionen: schützen Ihre Verbindung über Verschlüsselung und überprüfen, dass Sie tatsächlich mit der in der Browser-Leiste angezeigten kommunizieren (Bing.com, 192.168.1.37, usw.) und keine schädliche von Drittanbietern.

Das folgende PowerShell-Skript erstellt ein SSL-Zertifikat für die `localhost` Endpunkt. Jeden Endpunkt, die Device Portal überwacht benötigt ihr eigenes Zertifikat. Ersetzen Sie die `$IssuedTo` Argument im Skript für die einzelnen die andere Endpunkte für Ihr Gerät: der Hostname, Localhost und die IP-Adressen.

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

Wenn Sie über mehrere Geräte verfügen, können Sie die Localhost-PFX-Dateien wiederverwenden, aber Sie müssen weiterhin IP-Adresse und den Hostnamen Zertifikate für jedes Gerät separat zu erstellen.

Wenn im Bündel PFX-Dateien generiert wird, müssen Sie diese in Windows Device Portal zu laden. 

## <a name="provision-device-portal-with-the-certifications"></a>Bereitstellen eines Geräteportals mit der Zertifizierung(en)

Für jede PFX-Datei, die Sie erstellt haben für ein Gerät, müssen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten den folgenden Befehl aus.

```
WebManagement.exe -SetCert <Path to .pfx file> <password for pfx> 
```

Finden Sie unter Verwendung des beispielsweise:
```
WebManagement.exe -SetCert localhost.pfx PickAPassword
WebManagement.exe -SetCert --1.pfx PickAPassword
WebManagement.exe -SetCert MyLivingRoomPC.pfx PickAPassword
```

Nachdem Sie die Zertifikate installiert haben, starten Sie den Dienst einfach, damit die Änderungen wirksam werden können:

```
sc stop webmanagement
sc start webmanagement
```

> [!TIP]
> IP-Adressen können im Laufe der Zeit ändern.
Viele Netzwerke verwenden DHCP um IP-Adressen zu geben, damit Geräte nicht immer die IP-Adresse erhalten, die sie zuvor hatten. Wenn Sie ein Zertifikat für eine IP-Adresse auf einem Gerät erstellt haben und, die die Adresse des Geräts geändert hat, Windows Device Portal generiert ein neues Zertifikat mit der vorhandenen selbstsigniertes Zertifikat, und wird der Löschvorgang mit der, die Sie erstellt haben. Dadurch wird die Zertifikat-Warnseite in Ihrem Browser erneut angezeigt werden. Aus diesem Grund wird empfohlen, Herstellen einer Verbindung mit Ihrer Geräte über ihre Hostnamen, die Sie im Device Portal festlegen können. Diese bleibt unabhängig von der IP-Adressen.
