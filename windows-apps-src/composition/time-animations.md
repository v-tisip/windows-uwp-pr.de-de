---
title: Zeitanimationen
description: Verwenden Sie die KeyFrameAnimation-Klassen, um Ihre Benutzeroberfläche mit der Zeit ändern.
ms.date: 12/12/2018
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: 838a8c3a6dfe89de49fddefd28c53cea563408cf
ms.sourcegitcommit: dcff44885956094e0a7661b69d54a8983921ce62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "8968574"
---
# <a name="time-based-animations"></a>Zeitbasierte Animationen

Wenn sich eine Komponente oder ein ganzes Benutzererlebnis ändert, sehen Endbenutzer diese häufig auf zwei Arten: zeitbasiert oder augenblicklich. Auf der Windows-Plattform das Erstere dem letzteren vorgezogen – benutzererfahrungen, die sofort häufig ändern verwirrt und Endbenutzer verwirren, da es nicht ist folgen, was passiert ist nicht möglich. Der Benutzer empfindet das Erlebnis dann als ruckelnd und unnatürlich.

Stattdessen können Sie Ihre Benutzeroberfläche im Laufe der Zeit ändern, um den Endbenutzer durch die Benutzeroberfläche zu führen oder ihn über Änderungen an der Erfahrung zu informieren. Unter der Windows-Plattform geschieht dies durch zeitbasierte Animationen, auch KeyFrameAnimations genannt. Mit KeyFrameAnimations können Sie eine Benutzeroberfläche im Laufe der Zeit ändern und jeden Aspekt der Animation steuern, einschließlich wie und wann sie startet und wie sie ihren Endzustand erreicht. Beispielsweise ist es angenehmer, ein Objekt über 300 Millisekunden hinweg auf eine neue Position zu animieren, als es dort sofort „teleportieren“. Wenn Animationen anstelle von blitzschnellen Änderungen verwendet werden, ist das Endergebnis ein angenehmeres und ansprechenderes Erlebnis.

## <a name="types-of-time-based-animations"></a>Arten von zeitbasierten Animationen

Es gibt zwei Kategorien von zeitbasierten Animationen, mit denen Sie unter Windows schöne Benutzererlebnisse erstellen können:

**Explizite Animationen** – Wie der Name schon sagt, starten Sie die Animation explizit, um Updates durchzuführen.
**Implizite Animationen** – Diese Animationen werden vom System in Ihrem Namen ausgelöst, wenn eine Bedingung erfüllt ist.

In diesem Artikel werden wir erklären, wie man _explizite_ zeitbasierte Animationen mit KeyFrameAnimations erstellt und verwendet.

Für explizite und implizite zeitbasierte Animationen gibt es verschiedene Arten von Animationen, die den verschiedenen Eigenschaften von CompositionObjects entsprechen, die Sie animieren können.

- ColorKeyFrameAnimation
- QuaternionKeyFrameAnimation
- ScalarKeyFrameAnimation
- Vector2KeyFrameAnimation
- Vector3KeyFrameAnimation
- Vector4KeyFrameAnimation

## <a name="create-time-based-animations-with-keyframeanimations"></a>Zeitbasierte Animationen mit KeyFrameAnimations erstellen

Bevor wir beschreiben, wie man explizit zeitbasierte Animationen mit KeyFrameAnimations erstellt, gehen wir ein paar Konzepte durch.

- KeyFrames – Das sind die einzelnen „Schnappschüsse“, die eine Animation durchlaufen soll.
  - Definiert als Schlüssel- und Wertepaar. Der Schlüssel stellt den Fortschritt zwischen 0 und 1 dar, auch bekannt Animationsdauer für diesen „Schnappschuss“. Der andere Parameter stellt den Eigenschaftswert zu diesem Zeitpunkt dar.
- KeyFrameAnimation-Eigenschaften – Anpassungsoptionen, die Sie anwenden können, um die Anforderungen der Benutzeroberfläche zu erfüllen.
  - DelayTime – Zeit vor dem Starten einer Animation, nachdem StartAnimation aufgerufen wurde.
  - Duration – Dauer der Animation.
  - Iterationsverhalten – Anzahl bzw. unendliches Wiederholungsverhalten einer Animation.
  - Iterationsanzahl – Anzahl der finiten Wiederholungen einer Keyframeanimation.
  - Keyframeanzahl – Anzahl von Keyframes in einer bestimmten Keyframeanimation.
  - Stoppverhalten – legt das Verhalten eines Animationseigenschaftswerts fest, wenn „StopAnimation“ aufgerufen wird.
  - Direction – Gibt die Richtung der Animation für die Wiedergabe an.
- Animation Group – Mehrere Animationen gleichzeitig starten.
  - Wird häufig verwendet, wenn mehrere Eigenschaften gleichzeitig animiert werden sollen.

Weitere Informationen finden Sie unter [CompositionAnimationGroup](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionanimationgroup).

Mit diesen Konzepten im Hinterkopf, lassen Sie uns die allgemeine Formel für die Konstruktion einer KeyFrameAnimation durchsprechen:

1. Identifizieren Sie das CompositionObject und seine jeweilige Eigenschaft, die Sie animieren möchten.
1. Erstellen Sie eine KeyFrameAnimation-Vorlage des Compositors, die dem Typ der zu animierenden Eigenschaft entspricht.
1. Verwenden Sie die Animationsvorlage und fügen Sie KeyFrames hinzu und definieren Sie die Eigenschaften der Animation.
    - Mindestens ein KeyFrame (das 100%- oder 1f-KeyFrame) ist erforderlich.
    - Es wird empfohlen, auch eine Dauer zu definieren.
1. Einmal können Sie sich, diese Animation auszuführen, rufen Sie Startanimation auf das CompositionObject auf die Eigenschaft, die Sie animieren möchten. Zum Beispiel:
    - `visual.StartAnimation("targetProperty", CompositionAnimation animation);`
    - `visual.StartAnimationGroup(AnimationGroup animationGroup);`
1. Wenn Sie eine laufende Animation haben und Sie die Animation oder Animationsgruppe anhalten möchten, können Sie diese APIs verwenden:
    - `visual.StopAnimation("targetProperty");`
    - `visual.StopAnimationGroup(AnimationGroup AnimationGroup);`

Schauen wir uns ein Beispiel an, um diese Formel in Aktion zu sehen.

## <a name="example"></a>Beispiel

In diesem Beispiel wird ein, die den Offset eines visuellen Elements von < 0,0,0 > zu < 200,0,0 > über 1 Sekunde animiert werden soll. Zusätzlich möchten Sie die visuelle Animation zwischen diesen Positionen 10 mal sehen.

![Keyframe-Animation](images/animation/animated-rectangle.gif)

Sie beginnen zunächst mit der Auswahl des CompositionObjects und der Eigenschaft, die Sie animieren möchten. In diesem Fall wird das rote Quadrat durch ein Composition-Visual mit dem Namen `redVisual` dargestellt. Sie starten Ihre Animation von diesem Objekt aus.

Als nächstes müssen Sie eine Vector3KeyFrameAnimation (Offset ist vom Typ Vector3) erstellen, da Sie die Offset-Eigenschaft animieren möchten. Zusätzlich definieren Sie die entsprechenden KeyFrames für die KeyFrameAnimation.

```csharp
    Vector3KeyFrameAnimation animation = compositor.CreateVector3KeyFrameAnimation();
    animation.InsertKeyFrame(1f, new Vector3(200f, 0f, 0f));
```

Dann definieren Sie die Eigenschaften der KeyFrameAnimation, um dessen Dauer sowie das Animationsverhalten zwischen den zwei Positionen (aktuelle und < 200,0,0 >) 10 Mal zu beschreiben.

```csharp
    animation.Duration = TimeSpan.FromSeconds(2);
    animation.Direction = Windows.UI.Composition.AnimationDirection.Alternate;
    // Run animation for 10 times
    animation.IterationCount = 10;
```

Um schließlich eine Animation auszuführen, müssen Sie diese auf einer Eigenschaft eines CompositionObjects starten.

```csharp
redVisual.StartAnimation("Offset", animation);
```

Hier ist der komplette Code.

```csharp
private void AnimateSquare(Compositor compositor, SpriteVisual redVisual)
{ 
    Vector3KeyFrameAnimation animation = compositor.CreateVector3KeyFrameAnimation();
    animation.InsertKeyFrame(1f, new Vector3(200f, 0f, 0f));
    animation.Duration = TimeSpan.FromSeconds(2);
    animation.Direction = Windows.UI.Composition.AnimationDirection.Alternate;
    // Run animation for 10 times
    animation.IterationCount = 10;
    redVisual.StartAnimation("Offset", animation);
} 
```
