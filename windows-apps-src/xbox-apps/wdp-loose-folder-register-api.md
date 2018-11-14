---
author: WilliamsJason
title: Device Portal - Referenz zu den APIs zum Registrieren loser Ordner
description: Erfahren Sie, wie Sie programmgesteuert auf die APIs zum Registrieren loser Ordner zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: efdf4214-9738-4df6-bf1f-ed7141696ef6
ms.localizationpriority: medium
ms.openlocfilehash: cb80e2dbd7ebdfbb05bd642b9875a9cd7cc356f3
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6190563"
---
# <a name="register-an-app-in-a-loose-folder"></a>Registrieren einer App in einem losen Ordner  

**Anforderung**

Mithilfe des folgenden Anforderungsformats können Sie eine App in einem losen Ordner registrieren.

Methode      | Anforderungs-URI
:------     | :------
POST | /api/app/packagemanager/register
<br />
**URI-Parameter**

Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:

URI-Parameter      | Beschreibung
:------     | :-----
folder (erforderlich) | Der Name des Zielordners für das Paket, das registriert werden soll. Dieser Ordner muss unter „d:\developmentfiles\LooseApps“ auf der Konsole gespeichert sein. Der Ordnername muss base64-codiert sein, da er Pfadtrennzeichen enthalten kann, wenn der Ordner in einem Unterordner unter „LooseApps“ enthalten ist.
<br />

**Anforderungsheader**

- Keine

**Anforderungstext**

- Keine

**Antwort**

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Bereitstellungsanforderung akzeptiert und wird verarbeitet
4XX | Fehlercodes
5XX | Fehlercodes
<br />
**Verfügbare Gerätefamilien**

* Windows Xbox

**Hinweise**

Es gibt mindestens drei verschiedene Möglichkeiten, die lose App in den gewünschten Ordner auf der Konsole einzufügen. Die einfachste Möglichkeit besteht darin, die Dateien einfach über SMB in „\\<IP_Address>\DevelopmentFiles\LooseApps“ zu kopieren. Dazu sind ein Benutzername und Kennwort für UWA-Kits erforderlich, die über [/ext/smb/developerfolder](wdp-smb-api.md) abgerufen werden können. 

Die zweite Möglichkeit besteht darin, einzelne Dateien mithilfe eines POST-Befehls für „/api/filesystem/apps/file“ in den richtigen Ordner zu kopieren. „knownfolderid“ entspricht dabei „DevelopmentFiles“, „packagefullname“ ist leer, und der Dateiname und Pfad sind ordnungsgemäß angegeben (der Pfad muss mit „LooseApps“ beginnen).

Die dritte Möglichkeit besteht darin, einen vollständigen Ordner über [/api/app/packagemanager/upload](wdp-folder-upload.md) auf einmal zu kopieren. Dabei entspricht „destinationFolder“ dem Namen des Ordners, der unter „d:\developmentfiles\looseapps“ gespeichert werden soll, und die Nutzlast einem multipart-konformen HTTP-Text des Verzeichnisinhalts.

