---
title: Geräteportal-SSH-PINs– API-Referenz
description: Hier erfahren Sie, wie alle vertrauenswürdigen SSH-PINs programmgesteuert entfernt werden.
ms.localizationpriority: medium
ms.openlocfilehash: 1ddf15d3cdb4089a8ef010a4ae46d247a06a10d7
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8478017"
---
# <a name="ssh-pins-api-reference"></a>SSH-PINs– API-Referenz
Sie können alle vertrauenswürdigen SSH-PINs in Ihrem Entwickler-Kit mit dieser REST-API entfernen.

## <a name="remove-trusted-ssh-pins"></a>Entfernen von vertrauenswürdigen SSH-PINs

**Anforderung**

Methode      | Anforderungs-URI
:------     | :-----
DELETE | /ext/App/sshpins
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keiner

**Anforderungstext**   

- Keine

**Antwort**   

- Keine 

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
204 | Die Anforderung zum Löschen der PINs war erfolgreich.
4XX | Fehlercodes
5XX | Fehlercodes

<br />
**Verfügbare Gerätefamilien**

* Windows Xbox

