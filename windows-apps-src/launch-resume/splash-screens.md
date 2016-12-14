---
author: PatrickFarley
title: "Begrüßungsbildschirme"
description: "In diesem Abschnitt werden Einrichten und Konfigurieren des Begrüßungsbildschirm einer App beschrieben."
translationtype: Human Translation
ms.sourcegitcommit: 023e37bb6f9b8d8d780bb0a536cb469c87a31ed4
ms.openlocfilehash: bb0f3ff68b7dc15623e4f337e589989354e08b65

---

# <a name="splash-screens"></a>Begrüßungsbildschirme

Alle UWP-Apps müssen einen Begrüßungsbildschirm besitzen, der sich aus einem Bild und einer Hintergrundfarbe zusammensetzt. Beide Komponenten können angepasst werden.

Ihr Begrüßungsbildschirm wird sofort angezeigt, wenn Benutzer die App starten. Dadurch erhalten die Benutzer eine sofortige Rückmeldung, während die App-Ressourcen initialisiert werden. Sobald die App bereit für Interaktionen ist, wird der Begrüßungsbildschirm geschlossen.

Durch einen gut gestalteten Begrüßungsbildschirm kann Ihre App einladender wirken. Hier ist ein einfacher unauffälliger Begrüßungsbildschirm:

![Eine auf 75 % skalierte Bildschirmaufnahme des Begrüßungsbildschirms aus dem Begrüßungsbildschirmbeispiel.](images/regularsplashscreen.png)

Dieser Begrüßungsbildschirm wird durch Kombinieren eines grünen Hintergrunds mit einem transparenten Hintergrundbild im PNG-Format erstellt.

Ein einfaches Bild mit einer Hintergrundfarbe sieht unabhängig von dem Gerät, auf dem Ihre App ausgeführt wird, gut aus. Nur die Größe des Hintergrunds wird verändert, um verschiedene Bildschirmgrößen zu berücksichtigen. Ihr Bild bleibt stets unverändert.

Außerdem können Sie mit der [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763)-Klasse den Start Ihrer App anpassen. Sie können einen erweiterten, von Ihnen erstellten Begrüßungsbildschirm platzieren, damit Ihre App mehr Zeit für das Ausführen zusätzlicher Aufgaben, wie Vorbereiten der UI oder Abschließen von Netzwerkvorgängen, hat. Mit der **SplashScreen**-Klasse können Sie sich auch über das Schließen des Begrüßungsbildschirms benachrichtigen lassen, damit Sie Einführungsanimationen starten können.

| Thema | Beschreibung |
|-------|-------------|
| [Hinzufügen eines Begrüßungsbildschirms](add-a-splash-screen.md) | Legen Sie das Bild und die Hintergrundfarbe des Begrüßungsbildschirms Ihrer App fest. |
| [Längere Anzeige des Begrüßungsbildschirms](create-a-customized-splash-screen.md) | Verlängern Sie die Anzeige eines Begrüßungsbildschirms, indem Sie für die App einen erweiterten Begrüßungsbildschirm erstellen. Mit diesem erweiterten Bildschirm wird der beim Starten der App angezeigte Begrüßungsbildschirm imitiert, der angepasst werden kann. |


<!--HONumber=Dec16_HO1-->


