---
author: WilliamsJason
title: Device Portal - Referenz zu den APIs zum Hochladen von Ordnern
description: Erfahren Sie, wie Sie programmgesteuert auf die APIs zum Hochladen von Ordnern zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: e1a2c7f0-0040-4ce7-94de-17224736e20b
ms.localizationpriority: medium
ms.openlocfilehash: 481ec666c327b15088d8e60577c51fa1697918fe
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7424767"
---
# <a name="upload-a-folder-to-the-development-directory"></a>Hochladen eines Ordners in das Entwicklungsverzeichnis

**Anforderung**

Sie können einen vollständigen Ordner unter der ID für bekannte Ordner in den Ordner „DevelopmentFiles“ (oder in einen Unterordner innerhalb dieses Ordners) auf einmal hochladen.

Methode      | Anforderungs-URI
:------     | :------
POST | /api/app/packagemanager/upload 
<br />
**URI-Parameter**

Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:

URI-Parameter      | Beschreibung
:------     | :-----
destinationFolder (erforderlich) | Der Name des Zielordners für den Ordner, der hochgeladen werden soll. Dieser Ordner wird unter „d:\developmentfiles\LooseApps“ auf der Konsole gespeichert. Der Ordnername muss base64-codiert sein, da er Pfadtrennzeichen enthalten kann, wenn der Ordner ein Unterordner unter „LooseApps“ ist.
<br />

**Anforderungsheader**

- Keine

**Anforderungstext**

- Multipart-konformer HTTP-Text des Verzeichnisinhalts.

**Antwort**

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Erfolg
4XX | Fehlercodes
5XX | Fehlercodes
<br />
**Verfügbare Gerätefamilien**

* Windows Xbox

