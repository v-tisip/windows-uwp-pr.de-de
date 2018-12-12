---
title: Device Portal Netzwerk Anmeldeinformationen API-Referenz
description: Enthält Informationen zum Hinzufügen, entfernen oder Aktualisieren der Netzwerkanmeldeinformationen programmgesteuert.
ms.localizationpriority: medium
ms.topic: article
ms.date: 02/08/2017
ms.openlocfilehash: ac30d8db830c51ee40653feb49b443ed44502617
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8934685"
---
# <a name="network-credentials-api-reference"></a>Netzwerk-Anmeldeinformationen-API-Referenz
Sie können hinzufügen, entfernen Sie oder aktualisieren Sie gespeicherten Netzwerkanmeldeinformationen auf Ihr dev Kit mittels dieser REST-API.

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
  * NetworkPath - den Pfad zu der Netzwerkfreigabe.
  * UserName: der Benutzername die Anmeldeinformationen gespeichert hat.

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
| NetworkPath        | Die Netzwerkpfad für die Freigabe Sie Anmeldeinformationen für den Zugriff auf Hinzufügen. |
<br>

**Anforderungsheader**

- Keine

**Anforderungstext**

- Die folgenden JSON-Elemente:
* NetworkPath - den Pfad zu der Netzwerkfreigabe.
* UserName: der Benutzername, um die Anmeldeinformationen zu speichern.
* Password: das neue oder aktualisierte Kennwort für diesen Benutzer.

**Antwort**   

- Keine  

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
204 | Erfolg
4XX | Fehlercodes
5XX | Fehlercodes

## <a name="remove-stored-credentials-for-a-share"></a>Entfernen Sie die gespeicherte Anmeldeinformationen für eine Bereitstellungsfreigabe.

**Anforderung**

Methode      | Anforderungs-URI
:------     | :-----
DELETE | /ext/networkcredential
<br />
**URI-Parameter**

Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:

| URI-Parameter      | Beschreibung     | 
| ------------------ |-----------------|
| NetworkPath        | Der Netzwerkpfad für die Freigabe aus der Sie die gespeicherte Anmeldeinformationen entfernen. |
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
204 | Die Anforderung von Anmeldeinformationen war erfolgreich.
4XX | Fehlercodes
5XX | Fehlercodes

<br />
**Verfügbare Gerätefamilien**

* Windows Xbox


