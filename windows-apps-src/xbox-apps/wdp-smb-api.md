---
author: payzer
title: Device Portal - Referenz zu SMB-APIs
description: Erfahren Sie, wie Sie programmgesteuert auf die SMB-APIs zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 1f0eb76e-fe3e-4674-a27e-229beec7e63d
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: fc52bd3d326a20d0b561ad06b9f4245e7b557f82
ms.lasthandoff: 02/08/2017

---

# <a name="developer-folder-api-reference"></a>Referenz zur API für den Entwicklerordner   
Für den Zugriff auf Dateien auf Ihrer Xbox One, die sich auf die Entwicklung beziehen, können Sie einen standardmäßigen Datei-Explorer verwenden. Dadurch können Sie problemlos Dateien von Ihrem PC anzeigen und auf der Konsole ersetzen.

**Anforderung**

Sie können mithilfe der folgenden Anforderung auf den Entwicklerordner zugreifen. Die Anforderung gibt Folgendes zurück:    
* Den Speicherort der Dateifreigabe. Dieser Speicherort kann in die Adressleiste eines Datei-Explorers eingegeben werden.
* Den Benutzernamen für den Zugriff auf die Dateifreigabe.
* Das Kennwort für den Zugriff auf die Dateifreigabe.

Methode      | Anforderungs-URI
:------     | :-----
GET | /ext/smb/developerfolder
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keine

**Anforderungstext**

- Keiner

**Antwort**   
Path: Der Pfad zur Dateifreigabe mit den Entwicklerdateien.   
Username: Der Benutzername für den Zugriff auf die Freigabe mit den Entwicklerdateien.   
Password: Das Kennwort für den Zugriff auf die Freigabe mit den Entwicklerdateien.   

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

