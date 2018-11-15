---
author: WilliamsJason
title: Geräteportal-Controller– API-Referenz
description: Hier erfahren Sie, wie Sie die Anzahl der angeschlossenen physischen Controller abrufen und sie programmgesteuert deaktivieren.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5e0b85293ada8619246c3c23ef2103ead5f40c23
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "6860881"
---
# <a name="controller-api-reference"></a>Controller– API-Referenz   
Mit dieser REST-API können Sie die Anzahl der angeschlossenen physischen Controller abrufen und deaktivieren.

## <a name="determine-the-number-of-attached-physical-controllers"></a>Bestimmen der Anzahl der angeschlossenen physischen Controller

**Anforderung**

Sie können die Anzahl der angeschlossenen physischen Controller auf dem Gerät mit der folgenden Anforderung überprüfen.

Methode      | Anforderungs-URI
:------     | :-----
GET | /ext/remoteinput/controllers
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keiner

**Anforderungstext**   

- Keine

**Antwort**   

- Die JSON-Number-Eigenschaft ConnectedControllerCount, die die Anzahl der angeschlossenen physischen Controller angibt.

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Erfolg
4XX | Fehlercodes
5XX | Fehlercodes

## <a name="disconnect-all-physical-controllers-on-the-devkit"></a>Trennen aller physischen Controller im Entwickler-Kit

**Anforderung**

Sie können alle physischen Controller auf dem Gerät mithilfe der folgenden Anforderung trennen.

Methode      | Anforderungs-URI
:------     | :-----
DELETE | /ext/remoteinput/controllers
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
204 | Die Anforderung zum Trennen der Controller war erfolgreich.
4XX | Fehlercodes
5XX | Fehlercodes

<br />
**Verfügbare Gerätefamilien**

* Windows Xbox
