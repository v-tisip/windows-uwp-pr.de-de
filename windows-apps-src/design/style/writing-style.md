---
author: QuinnRadich
title: Schreibstil
description: Die Verwendung der richtigen Sprache und Tonfall ist entscheidend dafür, dass der Text Ihrer App als natürlicher Teil des Designs erscheint.
keywords: UWP, Windows10, Text, schreiben, Sprache, Tonfall, Design, Benutzeroberfläche, UX
ms.author: quradic
ms.date: 1/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: d38f22f896e31a925f07c5d6dffd357c211b3336
ms.sourcegitcommit: d780e3a087ab5240ea643346480a1427bea9e29b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
ms.locfileid: "1573249"
---
# <a name="writing-style"></a>Schreibstil

Die Art und Weise, in der Sie eine Fehlermeldung formulieren oder eine Hilfedokumentation schreiben und sogar der Text, den Sie für eine Schaltfläche auswählen, haben einen großen Einfluss auf die Verwendbarkeit Ihrer App. 

Der Schreibstil kann einen großen Unterschied zwischen einer üblen Darstellung der Benutzeroberfläche...

![Windows7 "Blue Screen of Death"](images/writing/bluescreen_old.png)

... Und einer guten Darstellung machen.

![Windows10 "Blue Screen of Death"](images/writing/bluescreen_new.png)


## <a name="writing-with-a-natural-voice-and-tone"></a>Schreiben Sie mit natürlicher Sprache und natürlichem Tonfall

Recherchen haben ergeben, dass Benutzer am besten auf einen Schreibstil reagieren, der freundlich, hilfreich und präzise ist. 

## <a name="be-friendly"></a>Freundlichkeit

Sie möchten auf keinen Fall den Benutzer abschrecken. Seien Sie informell, ungezwungen und verwenden Sie keine Bedingungen, mit denen Sie nicht vertraut sind. Auch wenn die Dinge schief gehen, geben Sie dem Benutzer nicht die Schuld für das Problem. Ihre App sollte stattdessen die Verantwortung übernehmen und dabei helfen, die Aktionen des Benutzers in den Mittelpunkt zu stellen.

![Vorher: Es ist ein Fehler aufgetreten, und das Bild konnte nicht hochgeladen werden. Wenn auch weitere Versuche fehlschlagen, muss die App erneut initialisiert werden. Danach: Wir konnten Ihr Bild nicht hochladen, da ein Fehler aufgetreten ist. Versuchen Sie es bitte erneut – Wenn dies immer noch nicht funktioniert, starten Sie die App erneut.](images/writing/friendly_example.png)

## <a name="be-helpful"></a>Seien Sie behilflich

Legen Sie den Schwerpunkt auf die Erklärung, was passiert ist, und geben Sie relevante Informationen an, die der Benutzer benötigt, ohne unübersichtliche, unnötige Informationen zu vermitteln.

![Vorher: Es konnte keine Verbindung mit dem Netzwerk hergestellt werden. Danach: Ihr Gerät ist mit einem Netzwerk verbunden, das Netzwerk ist jedoch nicht mit dem Internet verbunden. Starten Sie Ihren Router oder das Modem neu. Wenn Sie einen öffentlichen Hotspot verwenden, stellen Sie sicher, dass Sie angemeldet sind.](images/writing/helpful_example.png)

## <a name="be-clear-and-concise"></a>Seien Sie klar und präzise

In den meisten Fällen ist der Text nicht der Fokus der App. Er hilft dem Benutzer, zu vermitteln, was passiert ist, und was er als Nächstes tun sollte. Verlieren Sie dies nicht beim Schreiben des Texts Ihrer App aus den Augen. Verwenden Sie eine Sprache, mit der Ihre Zielgruppe vertraut ist. Dies bedeutet generell die Wahl alltäglicher und gesprochener Worte, obwohl Apps für spezielle Zwecke ihre eigenen Standards haben. Die Benutzer sollten sich niemals fragen, was Ihr Text bedeutet . Bevorzugen Sie daher eine einfache Wortwahl, wenn Sie nicht genau wissen, welchen Ton Sie verwenden sollen.

![Vorher: Es ist ein Fehler aufgetreten, und wir konnten die Datei nicht speichern. Auf den Speicherort kann möglicherweise nicht auf diesem Gerät zugegriffen werden, oder es ist möglicherweise nicht genügend Speicherplatz vorhanden. Danach: Wir konnten die Datei nicht an diesem Speicherort speichern. Wiederholen Sie den Vorgang erneut mit einem anderen Speicherort.](images/writing/concise_example.png)

## <a name="writing-tips"></a>Schreibtipps

Es gibt viele Möglichkeiten, diese Grundsätze im begrenzten Rahmen zu implementieren, über den Ihre App verfügt. Im folgenden finden Sie einige Strategien, die bei der Umsetzung der Prinzipien hilfreich sind:

### <a name="lead-with-whats-important"></a>Das Wichtigste kommt zuerst

Benutzer müssen in der Lage sein, den Text auf einen Blick zu lesen und zu verstehen. Fügen Sie Ihren Worten keine unnötige Einführung hinzu. Stellen Sie die wichtigsten Punkte in den Vordergrund und stellen Sie die Hauptideen immer zuerst vor, bevor Sie ihnen etwas hinzufügen.

**Richtig:** Wählen Sie "Filter", um Ihrem Bild Effekte hinzuzufügen.

**Falsch:** Wenn Sie Ihrem Bild visuelle Effekte oder Änderungen hinzufügen möchten, wählen Sie "Filter".

### <a name="emphasize-action"></a>Betonen Sie die Aktion

Apps werden durch Aktionen definiert. Benutzer führen Aktionen aus, wenn sie die App verwenden, und die App führt Aktion aus, wenn der Benutzer reagiert. Stellen Sie sicher, dass Ihr Text eine *aktive Stimme* in der gesamten App verwendet. Benutzer und Funktionen sollten als ausführbare Aktionen anstatt als auf Aufgaben, die einem zugeteilt werden, beschrieben werden.

**Richtig:** Starten Sie die App, um die Änderungen anzuzeigen.

**Falsch:** Die Änderungen werden angewendet, wenn die App neu gestartet wird.

### <a name="short-and-sweet"></a>Kurz und bündig

Benutzer überfliegen den Text und überspringen häufig gesamte Textblöcke. Machen Sie bei den erforderlichen Informationen und Darstellung keine Zugeständnisse, verwenden Sie allerdings nicht mehr Worte, als notwendig. In manchen Fällen bedeutet dies viele kürzere Sätze oder Satzfragmente. In anderen Fällen bedeutet dies, bei Wörtern und Strukturen in längeren Sätzen besonders wählerisch zu sein.

**Richtig:** Leider konnte wir das Bild nicht hochladen. Wenn dieses Problem erneut auftritt, starten Sie die App erneut. Aber keine Sorge – Ihr Bild wartet auf Sie, wenn Sie zurückkehren.

**Falsch:** Es ist ein Fehler aufgetreten, und das Bild konnte nicht hochgeladen werden. Versuchen Sie erneut, und wenn Sie dieses Problem erneut auftritt, müssen Sie die App erneut starten. Aber keine Sorge – wir haben Ihre Arbeit lokal gespeichert, und Ihre Arbeit wird auch dann noch da sein, wenn Sie zurückkehren.

## <a name="style-conventions"></a>Stilkonventionen

Wenn Sie nicht selbst ein Autor sind, kann es Sie einschüchtern, diese Prinzipien und Empfehlungen zu implementieren. Aber keine Sorge – einfach und unkompliziert Sprache ist eine hervorragende Möglichkeit, eine gute Benutzererfahrung bereitzustellen. Und wenn Sie sich noch nicht sicher sind, welche Worte Sie verwenden möchten, gibt es hier einige nützliche Richtlinien.

### <a name="addressing-the-user"></a>Sprechen Sie den Benutzer an

Wenden Sie sich direkt an den Benutzer.

* Sprechen Sie den Benutzer immer mit "Sie" an.

* Verwenden Sie "Wir", um Ihre eigene Perspektive zu verdeutlichen. Es wirkt einladend und hilft dem Benutzer, sich als Teil der Erfahrung zu fühlen.

* Verwenden Sie nicht "Ich" oder "meine", um auf die App-Perspektive zu verweisen, auch wenn Sie diese erstellt haben.

> Wir konnten die Datei nicht an diesem Speicherort speichern.

### <a name="abbreviations"></a>Abkürzungen

Abkürzungen können nützlich sein, wenn Sie auf Produkte, Orte oder technische Konzepte mehrmals in der gesamten App verweisen möchten. Sie können Platz sparen und natürlich wirken, solange der Benutzer sie versteht.

* Gehen Sie nicht davon aus, dass der Benutzer bereits mit allen Abkürzungen vertraut ist, auch wenn Sie vermuten, dass diese häufig verwendet werden.

* Definieren Sie immer, was eine neue Abkürzung bedeutet, wenn diese für den Benutzer das erste Mal angezeigt wird.

* Verwenden Sie keine Abkürzungen, die anderen Abkürzungen ähneln.

> Der universelle Windows-Plattform (UWP)-Designleitfaden ist eine Ressource, um ansprechende, optimierte Apps zu entwerfen und erstellen. Mit den Design-Funktionen, die in jeder UWP-App enthalten sind, können Sie Benutzeroberflächen (UI) erstellen, die für eine Vielzahl von Geräten geeignet sind.

### <a name="contractions"></a>Zusammenziehungen

Benutzer verwenden Zusammenziehungen und erwarten, diese zu sehen. Ein Vermeiden lässt die App zu formell oder sogar unnatürlich erscheinen.

* Verwenden Sie Zusammenziehungen, wenn sie für den Text passend sind.

* Verwenden Sie keine ungewöhnlichen Zusammenziehungen, um Platz zu sparen, oder wenn diese Ihre Worte weniger konventionell erscheinen lassen.

> Wenn Sie mit Ihrem Bild zufrieden sind, drücken Sie "Speichern", um es der Galerie hinzuzufügen. Von dort aus können Sie es mit Freunden teilen.

### <a name="periods"></a>Punkt

Wenn der Text mit einem Punkt endet impliziert das, dass der Text ein vollständiger Satz ist. Verwenden Sie einen Punkt für größere Textblöcke, und vermeiden sie diese für Text, der kürzer als ein vollständiger Satz ist.

* Verwenden Sie einen Punkt, um vollständige Sätze in QuickInfos, Fehlermeldungen und Dialogfeldern zu beenden.

* Enden Sie den Text für Schaltflächen, Optionsfelder, Etikette oder Kontrollkästchen nicht mit einem Punkt.

> **Sie haben keine Verbindung**
> * Überprüfen Sie, dass die Netzwerkkabel angeschlossen sind.
> * Stellen Sie sicher, dass Sie nicht im Flugzeugmodus sind.
> * Stellen Sie sicher, dass Ihr Drahtlosswitch aktiviert ist.
> * Starten Sie den Router neu.

### <a name="capitalization"></a>Großschreibung

Auch wenn Großbuchstaben wichtig sind, werden diese oft übermäßige verwendet.

* Eigennamen werden großgeschrieben.

* Verwenden Sie die Großschreibung am Anfang jeder Zeichenfolge von Text in Ihrer App: am Anfang jedes Satzes, Bezeichnung und Titel.

> **Welcher Teil ist problematisch?**
> * Ich habe mein Kennwort vergessen
> * Mein Kennwort wird nicht akzeptiert.
> * Eine andere Person verwendet eventuell mein Konto

## <a name="error-messages"></a>Fehlermeldungen

Wenn ein Fehler in Ihrer App auftritt, werden Benutzer aufmerksam. Da Benutzer möglicherweise verwirrt oder unzufrieden oder frustriert sind, wenn sie eine Fehlermeldung erhalten, ist dies ein Bereich, in dem gute Ausdrucksweise und guter Tonfall sich besonders auswirken können.

Es ist vor allem wichtig, dass die Fehlermeldung den Benutzer nicht dafür verantwortlich macht. Es ist aber auch wichtig, dass sie diese nicht mit Informationen überlasten, die sie nicht verstehen. In den meisten Fällen möchte ein Benutzer, wenn ein Fehler auftritt, so schnell und so einfach wie möglich wieder zu seiner Aufgabe zurückkehren. Aus diesem Grund sollten von Ihnen verfasste Fehlermeldung folgendes beachten:

* **Freundlicher Ton** mit Verantwortung für das Geschehen, vermeiden Sie unbekannte Begriffe und Fachjargon.

* **Hilfreich** in den Informationen über aufgetretene Fehler, indem Sie das Geschehen so gut wie möglich mitteilen und nächste Schritte sowie realistische Lösungen anbieten.

* **Seien Sie klar und präzise** und lassen Sie überflüssige Informationen aus.

![Beispiel für gute Fehlermeldungen](images/writing/connection_error.png)

## <a name="buttons"></a>Schaltflächen

Der Text der Schaltflächen muss präzise genug sein, damit Benutzer ihn auf einen Blick lesen können und klar sein, damit die Funktion der Schaltfläche sofort offensichtlich ist. Die längste Text auf einer Schaltfläche sollte ein paar kurze Worte enthalten, und viele sollte sogar kürzer sein.

Wenn Sie den Text für Schaltflächen schreiben, denken Sie daran, dass jede Schaltfläche eine Aktion darstellt. Verwenden Sie die *aktive Stimme* im Text der Schaltfläche, um Worte zu verwenden, die Aktionen anstelle von Reaktionen darstellen.

![Beispiel für eine gute Schaltfläche](images/writing/install_button.png)

## <a name="dialogs"></a>Dialogfelder

Viele Ratschläge zum Schreiben von Fehlermeldungen gelten ebenfalls für die Erstellung von Text für alle Dialogfelder in Ihrer App. Während Dialogfelder vom Benutzer erwartet werden, unterbrechen sie weiterhin die normalen Funktion der App und sollten daher hilfreich und präzise sein, damit der Benutzer wieder auf das zurückkehren kann, was er gerade tun muss.

Besonders wichtig ist das "Aufrufen und Antworten" zwischen dem Titel eines Dialogfelds und seiner Schaltflächen. Stellen Sie sicher, dass Ihre Schaltflächen klare Antworten auf die Fragen im Titel enthalten, und deren Format in der gesamten App konsistent ist.

![Beispiel für ein gutes Dialogfeld](images/writing/password_dialog.png)

## <a name="spoken-experiences"></a>Gesprochene Erfahrung

Die gleichen Prinzipien und Empfehlungen gelten beim Schreiben von Text für gesprochene Funktionen wie Cortana. In dieser Features sind die Prinzipien eines guten Schreibstils sogar noch wichtiger, da der Benutzer keine anderen Elemente mit visuellem Design erhält, und der gesprochenen Text nicht ergänzt werden kann.

* **Freundlicher Ton**, durch gesprochene Interaktionen mit dem Benutzer. Mehr als in jedem anderen Bereich ist es hier wichtig, dass eine gesprochene Erfahrung warm und zugänglich ist und der Benutzer keine Angst hat, damit zu interagieren.

* **Hilfreicher Ton** durch ein Bereitstellen alternativer Vorschläge, wenn der Benutzer eine unmögliche Anfrage stellt. Ähnlich wie bei einer Fehlermeldung sollten Sie bei einem Fehler, für den Ihre App die Anforderung nicht erfüllen kann, eine realistische Alternative haben, die der Benutzer stattdessen ausprobieren kann.

* **Seien Sie klar und präzise**, indem Sie die Sprache einfach gestalten. Gesprochene Funktionen sollten keine langen Sätze oder komplizierte Wörtern enthalten.

## <a name="accessibility-and-localization"></a>Lokalisierung und Bedienungshilfen

Ihre App kann eine größere Zielgruppe erreichen, wenn sie die Bedienungshilfen und Lokalisierung beim Schreiben berücksichtigen. Dies ist etwas, das nur durch Text erreicht werden kann, wobei eine unkomplizierte und freundliche Sprache ein guter Anfang ist. Weitere Informationen finden Sie in unserer [Übersicht über die Eingabehilfen](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-overview) und [Richtlinien für die Lokalisierung](https://docs.microsoft.com/windows/uwp/design/globalizing/globalizing-portal).

* **Freundlich und hilfreich sein**, indem Sie unterschiedliche Funktionen berücksichtigen. Vermeiden Sie Ausdrücke, die möglicherweise nicht sinnvoll für ein internationales Publikum sind, und verwenden Sie keine Wörter, die Annahmen darübermachen, was der Benutzer nicht tun kann.

* **Seien Sie klar und präzise**, indem Sie ungewöhnliche und spezielle Wörter vermeiden, wenn sie nicht erforderlich sind. Je einfacher der Text ist, desto einfacher ist er zu lokalisieren.


## <a name="techniques-for-non-writers"></a>Verfahren für Nicht-Autoren

Sie müssen kein geschulter oder erfahrener Autor sein, um Ihren Benutzern ein hohes Maß an Benutzerfreundlichkeit bereitzustellen. Wählen Sie die Wörter, die angenehm klingen – damit diese für den Benutzer ebenfalls angenehm sind. Aber manchmal ist das nicht so einfach, wie es klingt. Wenn Sie Probleme haben, können Ihnen diese Techniken helfen. 

* Angenommen, Sie sprechen mit einem Freund über Ihre App. Wie würden Sie Ihm die App erklären? Wie würden Sie über die Funktionen sprechen oder Anweisungen geben? Besser noch, sprechen Sie mit einer Person über die App, die diese noch nie verwendet hat. 

* Stellen Sie sich vor, Sie würden eine völlig andere App beschreiben. Wenn Sie beispielsweise ein Spiel beschreiben, denken Sie darüber nach, was Sie sagen oder schreiben würden, um eine finanzielle oder eine Nachrichten-App zu beschreiben. Der Kontrast in Sprache und Struktur, den Sie verwenden können, gibt Ihnen einen besseren Einblick für die richtigen Worte, die Sie schreiben.

* Sehen Sie sich ähnliche Apps zur Inspiration an. 

Die richtigen Worte zu finden ist ein Problem, mit dem viele Personen kämpfen, fühlen Sie sich daher nicht schlecht, wenn Sie einen Kompromiss für eine Wortwahl finden, die nicht ganz perfekt ist.