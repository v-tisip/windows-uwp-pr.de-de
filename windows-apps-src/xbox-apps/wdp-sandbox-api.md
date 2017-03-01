---
author: payzer
title: "Device Portal - Referenz zur API für den Xbox Live-Sandkasten"
description: Erfahren Sie, wie Sie programmgesteuert auf den Xbox Live-Sandkasten zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 72c7459c-420a-4da9-8afa-191a846185a5
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 629e8c3d35c9b9730c07e9f810909298558ae700
ms.lasthandoff: 02/08/2017

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

- Keiner

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


