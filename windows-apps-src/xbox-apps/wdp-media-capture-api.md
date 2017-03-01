---
author: WilliamsJason
title: Referenz zur Medienerfassungs-API
description: Erfahren Sie, wie Sie programmgesteuert auf die Medienerfassungs-API zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 3f92c8fd-4096-4972-97da-01ae5db6423c
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 9819e632ab6de58eee4358866d3186c0fa31f69f
ms.lasthandoff: 02/08/2017

---

# <a name="media-capture-api-reference"></a>Referenz zur Medienerfassungs-API #

**Anfordern**

Mithilfe des folgenden Anforderungsformats können Sie eine PNG-Darstellung des aktuellen Bildschirms erfassen.

| Methode        | Anforderungs-URI     | 
| ------------- |-----------------|
| GET           | /ext/screenshot |
<br>

**URI-Parameter**

Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:


| URI-Parameter      | Beschreibung     | 
| ------------------ |-----------------|
| download (optional)| Ein boolescher Wert, der angibt, ob HTTP-Antwortheader festgelegt werden sollen, die angeben, dass der Hostbrowser den Screenshot als Anhang herunterladen soll, anstatt ihn im Browser zu rendern.  |
<br>

**Anforderungsheader**

* Keine

**Anforderungstext**

* Keiner

###<a name="response"></a>Antwort###

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes:

| HTTP-Statuscode   | Beschreibung     | 
| ------------------ |-----------------|
| 200                | Die Screenshotanforderung war erfolgreich, und der erfasste Inhalt wurde zurückgegeben. |
| 5XX                | Fehlercodes für unerwartete Fehler |
<br>

**Verfügbare Gerätefamilien**

* Windows Xbox


