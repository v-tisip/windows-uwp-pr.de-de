---
title: Xbox-Portal Geräteinformationen-API-Referenz
description: Erfahren Sie, wie auf Xbox-Informationen zugreifen.
ms.date: 11/072017
ms.topic: article
keywords: Windows 10, Uwp, Xbox, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: 85c2c139aa8064e1f0769064b95eeb531086b8c1
ms.sourcegitcommit: 079801609165bc7eb69670d771a05bffe236d483
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "9115980"
---
# <a name="xbox-info-api-reference"></a>Xbox-Info-API-Referenz   
Sie können die Xbox One Geräteinformationen mithilfe dieser API zugreifen.

## <a name="get-xbox-one-device-information"></a>Abrufen von Xbox One Geräteinformationen

**Anforderung**

Sie erhalten Informationen über Ihre Xbox One.

Methode      | Anforderungs-URI
:------     | :-----
GET | /ext/xbox/info
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keiner

**Anforderungstext**

- Keine

**Antwort**   
Ein JSON-Objekt mit den folgenden Feldern:

* OsVersion - (Zeichenfolge) die Version des Betriebssystems.
* OsEdition - (Zeichenfolge) die Edition des Betriebssystems, z. B. "März 2017" oder "März 2017 QFE 1".
* ConsoleId - (Zeichenfolge) die Konsole des-ID.
* Geräte-ID - (Zeichenfolge) die Konsole des Xbox Live Gerät ID
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