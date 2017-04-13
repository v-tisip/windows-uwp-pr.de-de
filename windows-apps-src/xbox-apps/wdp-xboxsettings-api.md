---
author: payzer
title: "Device Portal - Referenz zur API für Xbox-Entwicklereinstellungen"
description: Erfahren Sie, wie Sie auf Xbox-Entwicklereinstellungen zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 6ab12b99-2944-49c9-92d9-f995efc4f6ce
ms.openlocfilehash: 43e4bb289d12439bbc0f6de347d187b067288d51
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="developer-settings-api-reference"></a>Referenz zur API für Entwicklereinstellungen   
Mit dieser API können Sie auf Xbox One-Einstellungen zugreifen, die für die Entwicklung nützlich sind.

## <a name="get-all-developer-settings-at-once"></a>Gleichzeitiges Abrufen aller Entwicklereinstellungen

**Anforderung**

Mithilfe der folgenden Anforderung können Sie alle Entwicklereinstellungen in einer einzigen Anforderung abrufen.

Methode      | Anforderungs-URI
:------     | :-----
GET | /ext/settings
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keine

**Anforderungstext**

- Keine

**Antwort**   
Die Antwort ist ein JSON-Einstellungsarray mit allen Einstellungen. Jedes Einstellungsobjekt enthält die folgenden Felder:   

Name (Zeichenfolge): Der Name der Einstellung.   
Value (Zeichenfolge): Der Wert der Einstellung.   
RequiresReboot („Yes“|„No“): Dieses Feld gibt an, ob ein Neustart erforderlich ist, damit die Einstellung wirksam wird.
Kategorie (Zeichenfolge): Die Kategorie der Einstellung.

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Die Anforderung war erfolgreich.
4XX | Fehlercodes
5XX | Fehlercodes

## <a name="get-settings-one-at-a-time"></a>Abrufen einzelner Einstellungen
Einstellungen können auch einzeln abgerufen werden.

**Anforderung**

Mit der folgenden Anforderung können Sie Informationen zu einer einzelnen Einstellung abrufen.

Methode      | Anforderungs-URI
:------     | :-----
GET | /ext/settings/\<setting name\>
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keine

**Anforderungstext**

- Keine

**Antwort**   
Die Antwort ist ein JSON-Objekt mit folgenden Feldern:   

Name (Zeichenfolge): Der Name der Einstellung.   
Value (Zeichenfolge): Der Wert der Einstellung.   
RequiresReboot („Yes“|„No“): Dieses Feld gibt an, ob ein Neustart erforderlich ist, damit die Einstellung wirksam wird.
Kategorie (Zeichenfolge): Die Kategorie der Einstellung.

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Die Anforderung war erfolgreich.
4XX | Fehlercodes
5XX | Fehlercodes

## <a name="set-the-value-of-a-setting"></a>Festlegen des Werts einer Einstellung
Sie können den Wert einer Einstellung festlegen.

**Anforderung**

Mit der folgenden Anforderung können Sie den Wert für eine Einstellung festlegen.

Methode      | Anforderungs-URI
:------     | :-----
PUT | /ext/settings/\<setting name\>
<br />
**URI-Parameter**

- Keine

**Anforderungsheader**

- Keine

**Anforderungstext**   
Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:   
Value (Zeichenfolge): Der neue Wert für die Einstellung.

**Antwort**   

- Keine

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

HTTP-Statuscode      | Beschreibung
:------     | :-----
200 | Die Anforderung war erfolgreich.
4XX | Fehlercodes
5XX | Fehlercodes

<br />
**Verfügbare Gerätefamilien**

* Windows Xbox

