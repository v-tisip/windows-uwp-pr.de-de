---
author: WilliamsJason
title: Gerät Portal Netzwerk Anmeldeinformationen-API-Referenz
description: Informationen Sie zum Hinzufügen, entfernen oder aktualisieren die Anmeldeinformationen für das Netzwerk Anzeigeformats.
ms.localizationpriority: medium
ms.openlocfilehash: 7e00169f92ee6f0aa48df64ec4a1186f9682b358
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "410174"
---
# <a name="network-credentials-api-reference"></a>Netzwerk-Anmeldeinformationen-API-Referenz
Sie können hinzufügen, entfernen oder Aktualisieren von gespeicherten Netzwerkanmeldeinformationen auf Ihre Devkit verwenden dieses REST-API.

## <a name="get-existing-credentials"></a>Abrufen von vorhandenen Anmeldeinformationen

**Anforderung**

Sie können eine Liste der gespeicherten Freigaben zusammen mit den Benutzernamen des Benutzers abrufen, die Anmeldeinformationen für diese Netzwerkfreigabe verfügt.

Methode      | Anforderungs-URI
:------     | :-----
GET | /ext/networkcredential
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keine

**Anforderungstext**   

- Keine

**Antwort**   

- JSON-Array im folgenden Format:
* Anmeldeinformationen
  * NetworkPath - den Pfad der Netzwerkfreigabe.
  * UserName - den Benutzernamen, der Anmeldeinformationen gespeichert hat.

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Erfolg
4XX | Fehlercodes
5XX | Fehlercodes

## <a name="add-or-update-stored-credentials-for-a-user"></a>Hinzufügen oder Aktualisieren von gespeicherten Anmeldeinformationen für einen Benutzer

**Anforderung**

Methode      | Anforderungs-URI
:------     | :-----
POST | /ext/networkcredential
<br />
**URI-Parameter**

Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:

| URI-Parameter      | Beschreibung     | 
| ------------------ |-----------------|
| NetworkPath        | Der Netzwerkpfad zur Freigabe möchten Sie Anmeldeinformationen für den Zugriff auf Hinzufügen. |
<br>

**Anforderungsheader**

- Keine

**Anforderungstext**

- Die folgenden JSON-Elemente:
* NetworkPath - den Pfad der Netzwerkfreigabe.
* Benutzername - der Benutzername zum Speichern von Anmeldeinformationen unter.
* Kennwort: das neue oder aktualisierte Kennwort für diesen Benutzer.

**Antwort**   

- Keine  

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
204 | Erfolg
4XX | Fehlercodes
5XX | Fehlercodes

## <a name="remove-stored-credentials-for-a-share"></a>Gespeicherte Anmeldeinformationen für eine Freigabe zu entfernen.

**Anforderung**

Methode      | Anforderungs-URI
:------     | :-----
DELETE | /ext/networkcredential
<br />
**URI-Parameter**

Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:

| URI-Parameter      | Beschreibung     | 
| ------------------ |-----------------|
| NetworkPath        | Der Netzwerkpfad zur Freigabe aus der Sie die gespeicherte Anmeldeinformationen entfernen. |
<br>

**Anforderungsheader**

- Keine

**Anforderungstext**   

- Keine

**Antwort**   

- Keine 

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
204 | Die Anforderung an die Anmeldeinformationen war erfolgreich.
4XX | Fehlercodes
5XX | Fehlercodes

<br />
**Verfügbare Gerätefamilien**

* Windows Xbox


