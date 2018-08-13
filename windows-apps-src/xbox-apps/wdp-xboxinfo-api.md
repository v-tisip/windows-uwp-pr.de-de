---
author: M-Stahl
title: Portal Xbox Geräteinformationen-API-Referenz
description: Erfahren Sie, wie Xbox Geräteinformationen zugreifen.
ms.author: mstahl
ms.date: 11/7/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Xbox Gerät portal
ms.localizationpriority: medium
ms.openlocfilehash: db1df2418a2bb60de4a72f51ad01a0bfd547ec20
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "406259"
---
# <a name="xbox-info-api-reference"></a>Xbox Info-API-Referenz   
Sie können eine Xbox Geräteinformationen mit dieser API zugreifen.

## <a name="get-xbox-one-device-information"></a>Abrufen von Informationen für eine Xbox Gerät

**Anforderung**

Sie können die Geräteinformationen zu Ihrer Xbox eine abrufen.

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
* OsEdition - (Zeichenfolge) die Version des Betriebssystems, beispielsweise "März 2017" oder "März 2017 QFE 1".
* ConsoleId - ID (Zeichenfolge) der Konsole des
* Geräte-ID - (String) der Konsole des Xbox Live Gerät Id.
* SerialNumber - Seriennummer (String) der Konsole des.
* DevMode - (String) der Konsole des aktuellen Entwicklermodus, beispielsweise "None" oder "Retail".
* ConsoleType - (String) der Konsole des Typs, beispielsweise "Xbox ein" oder "Xbox ein S".
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