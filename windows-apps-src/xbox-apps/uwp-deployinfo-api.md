---
title: 'Referenz zur API für Bereitstellungsinformationen des Geräteportals '
description: Erfahren Sie, wie Sie programmgesteuert auf die API für die Bereitstellung von Informationen zugreifen.
ms.localizationpriority: medium
ms.topic: article
ms.date: 02/08/2017
ms.openlocfilehash: 7543b41c6ee1d9c07f4540012f84dccc10bb4d76
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8784509"
---
# <a name="requests-deployment-information-for-one-or-more-installed-packages"></a>Fordert Bereitstellungsinformationen für ein oder mehrere installierte Pakete an.

**Anforderung**

Methode      | Anforderungs-URI
:------     | :------
POST | /ext/app/deployinfo
<br />
**URI-Parameter**

 - Keine

**Anforderungsheader**

- Keiner

**Anforderungstext**

Ein JSON-Array im folgenden Format:

* DeployInfo
  * PackageFullName: Name des Pakets, zu dem wir Informationen anfordern
  * OverlayFolder: Optionaler Pfad zu einem Overlay-Ordnerpfad, wenn dieses Feature verwendet wird

###<a name="response"></a>Response

**Antworttext**

Ein JSON-Array in folgendem Format (einige Felder sind optional):

* DeployInfo
  * PackageFullName: Name des Pakets, zu dem wir Informationen erhalten.
  * DeployType: Der Bereitstellungstyp.
  * DeployPathOrSpecifiers: Ein Bereitstellungspfad für lose Bereitstellungen oder installierte Bezeichner für Bereitstellungen in Paketen.
  * DeployDrive: Das Laufwerk, für das das Paket für die entsprechenden Bereitstellungstypen bereitgestellt wird
  * DeploySizeInBytes: Die Größe des Pakets in Byte für die entsprechenden Bereitstellungstypen
  * OverlayFolder: Der Overlay-Ordner für Bereitstellungen, die dieses Feature unterstützen

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