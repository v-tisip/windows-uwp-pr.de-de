---
ms.assetid: e04ebe3f-479c-4b48-99d8-3dd4bb9bfaf4
title: Bereitstellen eines Geräteportals mit einem benutzerdefinierten SSL-Zertifikat
description: TBD
ms.date: 07/11/2017
ms.topic: article
keywords: Windows 10, Uwp, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: faef15d523f56b6e45f77e0ccdbb2f5846f7a15a
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8786485"
---
# <a name="provision-device-portal-with-a-custom-ssl-certificate"></a>Bereitstellen eines Geräteportals mit einem benutzerdefinierten SSL-Zertifikat
In Windows 10 Creators Update hinzugefügt Windows Device Portal eine Möglichkeit für Administratoren das Gerät ein Zertifikat für die Verwendung in HTTPS-Kommunikation zu installieren. 

Während Sie dies auf Ihrem eigenen PC tun können, ist dieses Feature hauptsächlich für Unternehmen vorgesehen, die eine vorhandene Zertifikatinfrastruktur verfügen.  

Beispielsweise möglicherweise ein Unternehmen eine Zertifizierungsstelle (CA), die verwendet wird, zum Signieren von Zertifikaten für Intranetsites über HTTPS bereitgestellt. Dieses Feature steht, Infrastruktur. 

## <a name="overview"></a>Übersicht
Standardmäßig Device Portal selbstsignierte Stammzertifizierungsstelle generiert, und dann verwendet, die Sie um SSL-Zertifikate für jeden Endpunkt zu signieren, die es überwacht. Dazu gehören `localhost`, `127.0.0.1`, und `::1` (IPv6 Localhost).

Ebenfalls enthalten sind Hostnamen des Geräts (z. B. `https://LivingRoomPC`) und jede Link-lokale IP-Adresse, die dem Gerät zugewiesene (bis zu zwei [IPv4, IPv6] pro Netzwerkadapter). Sie können die Link-lokale IP-Adressen für ein Gerät anzeigen, indem Sie die auf das Netzwerk-Tool im Device Portal. Beginnen sie mit `10.` oder `192.` für IPv4 oder `fe80:` für IPv6. 

In der Standardeinstellung möglicherweise eine Warnung zum Sicherheitszertifikat aufgrund der nicht vertrauenswürdigen Stammzertifizierungsstelle in Ihrem Browser angezeigt. Genauer gesagt, ist das SSL-Zertifikat von Device Portal bereitgestellt von einer Stammzertifizierungsstelle signiert, die der Browser oder PC nicht vertraut. Dies kann durch Erstellen einer neuen vertrauenswürdigen Stammzertifizierungsstelle behoben werden.

## <a name="create-a-root-ca"></a>Erstellen Sie eine Stammzertifizierungsstelle.

Dies sollte nur durchgeführt werden, wenn Ihr Unternehmen (oder Home) eine Zertifikatinfrastruktur einrichten besitzt und sollten nur einmal ausgeführt werden. Das folgende PowerShell-Skript erstellt eine Stammzertifizierungsstelle _WdpTestCA.cer_aufgerufen. Installieren diese Datei auf des lokalen Computers vertrauenswürdige Stammzertifizierungsstellen bewirkt, dass das Gerät für SSL-Zertifikate zu vertrauen, die von diesem Stammzertifizierungsstelle signiert sind. Sie können (und sollten) dieses CER-Datei auf den einzelnen PCs installieren, die Sie Windows Device Portal herstellen möchten.  

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

## <a name="create-an-ssl-certificate-with-the-root-ca"></a>Erstellen Sie ein SSL-Zertifikat mit der Stammzertifizierungsstelle.

SSL-Zertifikate verfügen über zwei wichtige Funktionen: schützen Ihre Verbindung über Verschlüsselung und überprüfen, dass Sie tatsächlich mit der in der Browser-Leiste angezeigten kommunizieren (Bing.com, 192.168.1.37, usw.) und nicht auf eine schädliche von Drittanbietern.

Das folgende PowerShell-Skript erstellt ein SSL-Zertifikat für die `localhost` Endpunkt. Jeden Endpunkt, die Device Portal überwacht benötigt ihr eigenes Zertifikat. Ersetzen Sie die `$IssuedTo` Argument im Skript für die einzelnen die verschiedenen Endpunkte für Ihr Gerät: der Hostname, Localhost und die IP-Adressen.

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

Wenn Sie über mehrere Geräte verfügen, können Sie die Localhost-PFX-Dateien verwenden, aber Sie müssen weiterhin IP-Adresse und den Hostnamen Zertifikate für jedes Gerät separat zu erstellen.

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

Nachdem Sie die Zertifikate installiert haben, starten Sie den Dienst, damit die Änderungen wirksam werden können:

```
sc stop webmanagement
sc start webmanagement
```

> [!TIP]
> IP-Adressen können im Laufe der Zeit ändern.
Viele Netzwerke verwenden DHCP, um IP-Adressen zu geben, damit Geräte nicht immer die IP-Adresse erhalten, die sie zuvor verwendet wurde. Wenn Sie ein Zertifikat für eine IP-Adresse auf einem Gerät erstellt haben und, die die Adresse des Geräts geändert hat, Windows Device Portal generiert ein neues Zertifikat mit der vorhandenen selbstsigniertes Zertifikat, und wird der Löschvorgang mit der, die Sie erstellt haben. Dadurch wird die Zertifikat-Warnseite in Ihrem Browser erneut angezeigt werden. Aus diesem Grund empfehlen wir, Herstellen einer Verbindung mit Ihrer Geräte über ihre Hostnamen, die Sie im Device Portal festlegen können. Diese bleibt unabhängig von der IP-Adressen.
