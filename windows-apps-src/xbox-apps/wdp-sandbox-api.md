---
author: payzer
title: Device Portal - Referenz zur API für den Xbox Live-Sandkasten
description: Erfahren Sie, wie Sie programmgesteuert auf den Xbox Live-Sandkasten zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 72c7459c-420a-4da9-8afa-191a846185a5
ms.localizationpriority: medium
ms.openlocfilehash: 6f1729f07734b181dc5e0e8c97d702d8592302c2
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5875860"
---
# <a name="xbox-live-sandbox-api-reference"></a>Referenz zur API für den Xbox Live-Sandkasten   
Mit dieser REST-API können Sie den Xbox Live-Sandkasten abrufen und festlegen.

## <a name="get-the-xbox-live-sandbox"></a>Abrufen des Xbox Live-Sandkastens

**Anforderung**

Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts lesen:

Methode      | Anforderungs-URI
:------     | :-----
GET | /ext/xboxlive/sandbox
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keine

**Anforderungstext**

- Keine

**Antwort**   
Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.   

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.
4XX | Fehlercodes
5XX | Fehlercodes

## <a name="set-the-xbox-live-sandbox"></a>Festlegen des Xbox Live-Sandkastens
Mit der folgenden Anforderung können Sie den Xbox Live-Sandkasten des Geräts ändern. Bei der Xbox One muss das Gerät neu gestartet werden, damit die Einstellung wirksam wird.

**Anforderung**

Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts festlegen:

Methode      | Anforderungs-URI
:------     | :-----
PUT | /ext/xboxlive/sandbox
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keine

**Anforderungstext**   
Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:   
Sandbox (Zeichenfolge): Der neue Wert, auf den der Sandkasten des Geräts festgelegt werden soll.

**Antwort**   
Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.   

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.
4XX | Fehlercodes
5XX | Fehlercodes

<br />
**Verfügbare Gerätefamilien**

* Windows Xbox

