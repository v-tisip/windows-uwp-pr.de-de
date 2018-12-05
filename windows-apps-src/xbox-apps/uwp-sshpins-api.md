---
title: Geräteportal-SSH-PINs– API-Referenz
description: Hier erfahren Sie, wie alle vertrauenswürdigen SSH-PINs programmgesteuert entfernt werden.
ms.localizationpriority: medium
ms.openlocfilehash: 1ddf15d3cdb4089a8ef010a4ae46d247a06a10d7
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8741208"
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

