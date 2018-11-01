---
author: M-Stahl
title: Geräteinformationen Portal Xbox-API-Referenz
description: Erfahren Sie mehr über das Xbox-Geräteinformationen zuzugreifen.
ms.author: mstahl
ms.date: 11/7/2017
ms.topic: article
keywords: Windows 10 Uwp Xbox, Gerät portal
ms.localizationpriority: medium
ms.openlocfilehash: 4b0e2bab0ce7d5525e8032809954ff656a74a61c
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5919893"
---
# <a name="xbox-info-api-reference"></a>Xbox-Info-API-Referenz   
Sie können eine Xbox mit dieser API Informationen zugreifen.

## <a name="get-xbox-one-device-information"></a>Erhalten Sie eine Xbox Geräteinformationen.

**Anforderung**

Sie erhalten Informationen über Ihre Xbox ein.

Methode      | Anforderungs-URI
:------     | :-----
GET | /ext/xbox/info
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keine

**Anforderungstext**

- Keine

**Antwort**   
Ein JSON-Objekt mit den folgenden Feldern:

* OsVersion - (Zeichenfolge) Version des Betriebssystems.
* OsEdition - (Zeichenfolge) der Edition des Betriebssystems, wie "März 2017" oder "März 2017 QFE 1".
* ConsoleId - ID (Zeichenfolge) der Konsole
* DeviceId - (Zeichenfolge) der Konsole Xbox Live Device ID
* SerialNumber - Seriennummer (Zeichenfolge) der Konsole.
* DevMode - (Zeichenfolge) der Konsole des aktuellen Entwicklermodus wie "None" oder "Retail".
* ConsoleType - Typ (Zeichenfolge) der Konsole "Xbox 1" oder "Die Xbox".
* DevkitCertificateExpirationTime - (Anzahl) der UTC-Zeit in Sekunden, wenn die Konsole Developer Kit Zertifikat abläuft.

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Die Anforderung war erfolgreich.
4XX | Fehlercodes
5XX | Fehlercodes

<br />
**Verfügbare Gerätefamilien**

* Windows Xbox