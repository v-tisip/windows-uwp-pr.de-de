---
author: Jwmsft
Description: "Ein Muster mit einem Inhalts- und einem Befehlsbereich für Apps mit einer einzelnen Ansicht oder modalen Benutzeroberflächen wie etwa Fotoanzeige-/Fotobearbeitungs-Apps, Dokumentviewer-Apps, Karten-Apps, Zeichen-Apps oder andere Apps, die eine Ansicht mit freiem Bildlauf nutzen."
title: "Layoutmuster „Aktive Canvas“"
ms.assetid: 4D768472-64D6-406C-9E87-F750F6B981A0
label: TBD
template: detail.hbs
op-migration-status: ready
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 1782540069254f30b241022b687f493110d3b280
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="active-canvas-layout-pattern"></a>Layoutmuster „Aktive Canvas“

Eine aktive Canvas ist ein Muster mit einem Inhalts- und einem Befehlsbereich. Sie ist für Apps mit einer einzigen Ansicht oder modalen Benutzeroberflächen wie z. B. Fotoanzeige-/Fotobearbeitungs-Apps, Dokumentviewer-Apps, Karten-Apps, Zeichen-Apps oder andere Apps gedacht, die eine Ansicht mit freiem Bildlauf nutzen. Zum Ausführen von Aktionen kann eine aktive Canvas – je nach Anzahl und Art der erforderlichen Aktionen – mit einer Befehlsleiste oder nur mit Schaltflächen kombiniert werden.

## <a name="examples"></a>Beispiele

Dieser Entwurf einer Fotobearbeitungs-App enthält das Muster „Aktive Canvas“ mit einem Beispiel für Mobilgeräte auf der linken und einem Beispiel für Desktops auf der rechten Seite. Die Bildbearbeitungsoberfläche ist eine Canvas, und die Befehlsleiste im unteren Bereich enthält alle kontextbezogenen Aktionen für die App.

![Beispiel für einen Foto-Editor mit dem Muster „Aktive Canvas“](images/uap-photo-pc-phone-700.png)

Dieser Entwurf einer App für einen U-Bahn-Fahrplan verwendet ein aktives Canvas-Element mit einer einfachen UI-Leiste am oberen Rand, die nur zwei Aktionen und ein Suchfeld enthält. Kontextbezogene Aktionen werden im Kontextmenü angezeigt (wie in der rechten Abbildung zu sehen).

![Beispiel für eine Karten-App mit dem Muster „Aktive Canvas“](images/uap-subway-pc-phone-700.png)


## <a name="implementing-this-pattern"></a>Implementieren des Musters

Das Muster der aktiven Canvas besteht aus einem Inhaltsbereich und einem Befehlsbereich.

**Inhaltsbereich.**  Der Inhaltsbereich ist in der Regel eine Canvas mit freiem Bildlauf. Eine App kann mehrere Inhaltsbereiche enthalten.

**Befehlsbereich.**  Falls Sie zahlreiche Befehle anzeigen möchten, wäre eine auf die Bildschirmgröße reagierende Befehlsleiste eine Option. Wenn Sie nicht so viele Befehle anzeigen möchten und nicht unbedingt Wert auf eine reaktionsfähige Benutzeroberfläche legen, bieten sich platzsparende Schaltflächen an.



## <a name="related-articles"></a>Verwandte Artikel

-   [**App-Leiste und Befehlsleiste**](../controls-and-patterns/app-bars.md)
