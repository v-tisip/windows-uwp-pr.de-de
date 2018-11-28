---
title: Portal Xbox Geräteinformationen-API-Referenz
description: Erfahren Sie mehr über das Xbox-Geräte-Informationen zugreifen.
ms.date: 11/7/2017
ms.topic: article
keywords: Windows 10, Uwp, Xbox-geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: d7901890e1cc8fab24742e8785562d13d2fe182a
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7850639"
---
# <a name="xbox-info-api-reference"></a>Xbox-Info-API-Referenz   
Sie können die Xbox One Geräteinformationen mithilfe dieser API zugreifen.

## <a name="get-xbox-one-device-information"></a>Abrufen von Xbox One Geräteinformationen

**Anforderung**

Informationen erhalten zu Ihrer Xbox One.

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

* OsVersion - (Zeichenfolge) die Version des Betriebssystems.
* OsEdition - (Zeichenfolge) die Edition des Betriebssystems, z. B. "März 2017" oder "März 2017 QFE 1".
* ConsoleId - (Zeichenfolge) die Konsole des-ID.
* Geräte-ID - (Zeichenfolge) die Konsole des Xbox Live Gerät ID ein.
* Seriennummer - (Zeichenfolge) die Konsole des Seriennummer.
* DevMode - (Zeichenfolge) die Konsole des aktuellen Entwicklermodus, z. B. "None" oder "Retail".
* ConsoleType - (Zeichenfolge) die Konsole des Typ, z. B. "Xbox One" oder "Xbox One S".
* DevkitCertificateExpirationTime – (Number) der UTC-Zeit in Sekunden, wenn die Konsole Developer Kit Zertifikat abläuft.

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