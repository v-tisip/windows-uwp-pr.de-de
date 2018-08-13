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
ms.openlocfilehash: 1bc02780808d5b9fca09576165f428eca1cce715
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "234988"
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

- Keine

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
