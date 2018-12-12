---
ms.assetid: 386faf59-8f22-2e7c-abc9-d04216e78894
title: Kompositionsanimationen
description: Viele Eigenschaften von Kompositionsobjekten und Effekten können mit Keyframeanimationen und Ausdrucksanimationen animiert werden. Dadurch können sich Eigenschaften eines UI-Elements im Laufe der Zeit oder auf der Grundlage einer Berechnung verändern.
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b94f14b32c5dd74e0aefb9b9a99f64bbd905a05d
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8937339"
---
# <a name="composition-animations"></a>Kompositionsanimationen

Mit der Windows.UI.Composition API können Sie Kompositorobjekte in einer einheitlichen API-Ebene erstellen, animieren, umwandeln und bearbeiten. Kompositionsanimationen bieten eine leistungsstarke und effiziente Möglichkeit, Animationen auf der Benutzeroberfläche Ihrer Anwendung auszuführen. Sie wurden von Grund auf neu entwickelt, um sicherzustellen, dass Ihre Animationen mit 60 F/s unabhängig vom UI-Thread ausgeführt werden, und um Ihnen die Flexibilität zu bieten, tolle Funktionen zu erstellen, die zur Steuerung von Animationen nicht nur Zeit, sondern auch Eingaben und andere Eigenschaften verwenden.

## <a name="motion-in-windows"></a>Animationin Windows

Stellen Sie sich Motion-Design wie einen Film vor. Nahtlose Übergänge halten Sie auf die Geschichte konzentriert und erwecken Erlebnisse zum Leben. Wir können dieses Gefühl in unsere Entwürfe einladen führende Kontakte aus einer Aufgabe zur nächsten führen. Bewegung ist häufig der ausschlaggebende Faktor zwischen einer Benutzeroberfläche und eine Benutzeroberfläche.

Als ein wesentlicher Baustein der Windows-Plattform-Benutzeroberfläche bieten CompositionAnimations eine leistungsstarke und effiziente Möglichkeit, bewegungserlebnisse in der Benutzeroberfläche Ihrer Anwendung zu erstellen. Die Animationsmodul wurde von Grund auf neu entwickelt, um sicherzustellen, dass die Bewegung mit 60 FPS, unabhängig vom UI-Thread ausgeführt wird. Diese Animationen sollen die Flexibilität, um basierend auf der Zeit, Eingabe und andere Eigenschaften innovative bewegungserlebnisse zu erstellen.

### <a name="examples-of-motion"></a>Beispiele für Bewegung

Im Folgenden finden Sie einige Beispiele für Bewegung in einer App.

Hier verwendet eine App eine verbundene Animation, um ein Elementbild zu animieren, wenn es als Teil der Überschrift der nächsten Seite weiterbesteht. Dieser Effekt trägt dazu bei, Benutzerkontext beim Übergang beizubehalten.

![Ein Beispiel für verbundene Animation](images/animation/connected-animation-example.gif)

Hier werden bei einem Bildlauf oder Schwenken der UI verschiedene Objekte mithilfe eines Parallax-Effekts unterschiedlich schnell verschoben. Dadurch entsteht ein Gefühl von Tiefe, Perspektive und Bewegung.

![Beispiel für Parallax mit einer Liste und einem Hintergrundbild](images/animation/parallax-example.gif)

## <a name="using-compositionanimations-to-create-motion"></a>Verwenden CompositionAnimations zum Erstellen von Bewegung

Um Bewegung in der Benutzeroberfläche zu generieren, können Entwickler Animationen in XAML (Link zu Storyboards hier) oder der visuellen Ebene zugreifen. Animationen in der visuellen Ebene bieten Entwicklern eine Reihe von Vorteilen:

- Leistung – anstelle der herkömmlichen UI-Thread-gebunden-Animation, Animationen auf der Benutzeroberfläche von Windows-Plattform ausgeführt werden in einem unabhängigen Thread mit 60 FPS reibungslose bewegungserlebnisse zu aktivieren.
- Templating-Modell – Animationen in der Windows-UI-Ebene sind Vorlagen, Bedeutung kann eine einzelne Animation auf mehreren Objekten und Optimierungseigenschaften Eigenschaften oder Parameter, ohne sich Gedanken machen durchzuführen vorherigen verwendet.
- Anpassung – Windows-UI-Ebene nicht nur erleichtert schöne UI vornehmen, aber mit einer Vielzahl von Animationstypen, Funktionen zum Erstellen von neuen und beeindruckende möglich mit einem Farbverlauf von Anpassungen

Als Entwickler Funktionen der Windows-UI-Ebene erstellen haben Sie Zugriff auf eine Vielzahl von Animationskonzepten Sie Ihre Entwürfe zum Leben zu erwecken. Sie können diese Konzepte verwenden, eine Eigenschaft animieren, oder für die Komponente (falls zutreffend) für alle compositionobjects subchannel.

> [!NOTE]
> Nicht alle Eigenschaften eines compositionobjects sind animiert. Finden Sie in der Dokumentation der einzelnen compositionobjects, um festzustellen, ob eine Eigenschaft animiert werden kann.

> [!NOTE]
> Der Begriff _unterkanal_ bezieht sich auf ein Formular Komponente einer Eigenschaft. Beispielsweise wird der X oder XY einer Vector3-Offset-Eigenschaft für subchannel.

| Animation Konzept | Beschreibung |
| ----------------- | ----------- |
| [Zeitbasierte Bewegung mit KeyFrameAnimations](time-animations.md)  | KeyFrameAnimations werden verwendet, um den gesamten ein bewegungserlebnis über einen Zeitraum direkt zu steuern. Entwickler, die einer Bewegung Anfang, Ende, Interpolation zwischen und Dauer in einer herkömmlichen Keyframe beschreiben. |
| [Relative Bewegung mit ExpressionAnimations](relation-animations.md)  | ExpressionAnimations werden verwendet, um wird beschrieben, wie eine Bewegung der Eigenschaft eines Objekts relativ zu einem anderen Objekt-Eigenschaft gesteuert werden soll. Entwickler definieren eine mathematische Formel, die die Referenz-basierte Beziehung definiert. |
| ImplicitAnimations | Diese Animationen sind Trigger-basierte und werden separat von der zentralen app-Logik definiert. ImplicitAnimations wird beschrieben, wie und wann Animationen als Reaktion auf eigenschaftsänderungen der direkte auftreten. |
| [Eingabegesteuerte bewegungserlebnisse mit Eingaben Animationen](input-driven-animations.md)  | Eingabeanimationen umfasst eine Reihe von Szenarien, die Entwickler beschreiben, Manipulation-basierte Bewegung per Toucheingabe oder anderen eingabemodalitäten zu ermöglichen. Diese Animationen werden basierend auf aktive Benutzereingaben oder Gesten gesteuert. |
| [Strategiespiele Bewegung mit NaturalMotionAnimations](natural-animations.md)  | NaturalMotionAnimations werden verwendet, um die gewohnte Bewegung, dass erzwingen, basierte auf der realen Welt Umgebungen gesteuerte Bewegung zu beschreiben. Anstatt der Zeit definieren, definieren Entwickler Merkmale der Bewegung (z. B. damping Ratio für Federanimationen) |