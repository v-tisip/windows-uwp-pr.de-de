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
# <a name="provision-device-portal-with-a-custom-ssl-certificate"></a>Bereitstellung Gerät Portal ein SSL-Zertifikat
Windows 10 Autoren Update hinzugefügt Windows Gerät Portal Gerät Administratoren installieren Sie ein Zertifikat für die Verwendung in HTTPS-Kommunikation. 

Während Sie Ihren Computer hierzu wird dieses Feature hauptsächlich für Unternehmen vorgesehen, die ein vorhandenes Zertifikat Infrastruktur.  

Beispielsweise müssen Unternehmen eine Zertifizierungsstelle (CA), die Zertifikate für Intranetwebsites über HTTPS bedient sich verwendet. Dieses Feature steht, Infrastruktur. 

## <a name="overview"></a>Übersicht
Standardmäßig Gerät Portal selbstsignierte Stammzertifizierungsstelle generiert und verwendet, die Zertifikate für jeden Endpunkt anmelden abgehört wird. Dies schließt `localhost`, `127.0.0.1`, und `::1` (IPv6 Localhost).

Ferner sind Hostname des Geräts (z. B. `https://LivingRoomPC`) und jeder Link-lokale IP-Adresse für das Gerät (bis zu zwei [IPv4, IPv6] pro Netzwerkadapter). Die Link-lokale Adressen ein sehen mit dem Netzwerk in Gerät ansehen. Sie beginnen mit `10.` oder `192.` für IPv4 oder `fe80:` für IPv6. 

In der Standardeinstellung kann eine zertifikatswarnung aufgrund der nicht vertrauenswürdigen Stammzertifizierungsstelle im Browser angezeigt. Insbesondere wird Gerät Portal bereitgestellte SSL-Zertifikat von einer Stammzertifizierungsstelle signiert, das Browser oder Computer nicht vertrauen. Dies kann durch Erstellen einer neuen vertrauenswürdigen Stammzertifizierungsstelle behoben werden.

## <a name="create-a-root-ca"></a>Erstellen einer Stammzertifizierungsstelle

Dies sollte nur ausgeführt werden, wenn Ihr Unternehmen (oder Home) eine Zertifikatinfrastruktur eingerichtet und sollte nur einmal durchgeführt werden. PowerShell-Skript erstellt eine Stammzertifizierungsstelle _WdpTestCA.cer_aufgerufen. Installieren diese Datei auf dem lokalen Computer vertrauenswürdige Stammzertifizierungsstellen führen Ihr Gerät SSL-Zertifikate zu vertrauen, die diese Zertifizierungsstelle signiert sind. Sie können (und sollten) diese CER-Datei auf jedem PC installieren, die Windows-Geräte-Portal eine Verbindung herstellen möchten.  

```PowerShell
$CN = "PickAName"
$OutputPath = "c:\temp\"

# Create root certificate authority
$FilePath = $OutputPath + "WdpTestCA.cer"
$Subject =  "CN="+$CN
$rootCA = New-SelfSignedCertificate -certstorelocation cert:\currentuser\my -Subject $Subject -HashAlgorithm "SHA512" -KeyUsage CertSign,CRLSign
$rootCAFile = Export-Certificate -Cert $rootCA -FilePath $FilePath
```

Das erstellte _WdpTestCA.cer_ -Datei können Sie um SSL-Zertifikate zu signieren. 

## <a name="create-an-ssl-certificate-with-the-root-ca"></a>Erstellen Sie ein SSL-Zertifikat mit der Stamm-CA

Zertifikate haben zwei wichtige Funktionen: die Verbindung durch Verschlüsselung sichern und überprüfen, ob Sie tatsächlich mit der Browser-Leiste angezeigten kommunizieren (Bing.com, 192.168.1.37, usw.) und nicht böswillige Dritte.

Das folgende PowerShell-Skript erstellt ein SSL-Zertifikat für die `localhost` Endpunkt. Jedes Gerät Portal überwacht Endpunkt benötigt ein eigenes Zertifikat. Ersetzen Sie die `$IssuedTo` Argument im Skript mit jedem der anderen Endpunkte für Ihr Gerät: den Hostnamen Localhost und die IP-Adressen.

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

Haben mehrere Geräte Localhost PFX-Dateien verwenden, aber Sie müssen noch IP-Adresse und Hostname Zertifikate für jedes Gerät separat erstellen.

Wenn das Bundle PFX-Dateien generiert, müssen Sie in Windows Gerät zu laden. 

## <a name="provision-device-portal-with-the-certifications"></a>Bereitstellung Gerät Portal mit der Zertifizierungen

Für jede PFX-Datei, die Sie erstellt haben ein, müssen Sie den folgenden Befehl in ein Eingabeaufforderungsfenster mit erhöhten Rechten ausführen.

```
WebManagement.exe -SetCert <Path to .pfx file> <password for pfx> 
```

Siehe beispielsweise Verwendung:
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
> IP-Adressen können sich ändern.
Viele Netzwerke verwenden DHCP zu IP-Adressen, so dass Geräte immer dieselbe IP-Adresse nicht zuvor hatte. Erstellte Zertifikat für IP-Adresse auf einem Gerät und die Adresse des Geräts geändert hat Windows Gerät Portal mit vorhandenen selbstsignierte Zertifikat ein neues Zertifikat generiert und mit dem erstellten wird beendet. Dadurch wird der Warnseite Zertifikat erneut im Browser angezeigt. Aus diesem Grund wird empfohlen, mit der Geräte über ihre Hostnamen, der im Gerät Portal festgelegt werden. Diese werden IP-Adressen gleich bleiben.
