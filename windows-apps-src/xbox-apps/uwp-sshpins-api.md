---
author: WilliamsJason
title: Geräteportal-SSH-PINs– API-Referenz
description: Hier erfahren Sie, wie alle vertrauenswürdigen SSH-PINs programmgesteuert entfernt werden.
ms.localizationpriority: medium
ms.openlocfilehash: 88ba9d3e35650c8c581b9ddb76911636fc18c72e
ms.sourcegitcommit: c104b653601d9b81cfc8bb6032ca434cff8fe9b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
ms.locfileid: "1921247"
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

