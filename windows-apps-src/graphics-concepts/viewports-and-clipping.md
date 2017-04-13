---
title: Viewports und Zuschneiden
description: Ein Viewport ist ein zweidimensionales (2D) Rechteck, auf das eine 3D-Szene projiziert wird.
ms.assetid: D0DD646E-13AE-452A-AD22-8C35000D0BA9
keywords: Viewports und Zuschneiden
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: b392f267c370bd075d5c0d1ac953ee76a9cff0af
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="viewports-and-clipping"></a>Viewports und Zuschneiden


Ein *Viewport* ist ein zweidimensionales (2D) Rechteck, auf das eine 3D-Szene projiziert wird. In Direct3D ist das Rechteck eine Koordinate innerhalb einer Direct3D-Oberfläche, die das System als Renderziel verwendet. Die Projektionstransformation konvertiert Scheitelpunkte in das Koordinatensystem, das vom Viewport verwendet wird. Ein Viewport wird auch verwendet, um den Bereich der Tiefenwerte auf einer Renderzieloberfläche festzulegen, auf die eine Szene (in der Regel zwischen 0,0 und 1,0) gerendert wird.

## <a name="span-idtheviewingfrustumspanspan-idtheviewingfrustumspanspan-idtheviewingfrustumspanthe-viewing-frustum"></a><span id="The_Viewing_Frustum"></span><span id="the_viewing_frustum"></span><span id="THE_VIEWING_FRUSTUM"></span>Der Pyramidenstumpf


Ein Pyramidenstumpf ist ein 3D-Körper in einer Szene, der relativ zur Viewport-Kamera positioniert ist. Dessen Form wirkt sich darauf aus, wie Modelle vom Kamerabereich auf den Bildschirm projiziert werden. Die am häufigsten verwendete Projektion, eine Perspektivenprojektion, sorgt dafür, dass nahe der Kamera befindliche Objekte größer als entfernte Objekte erscheinen. Für eine perspektivische Ansicht kann der Pyramidenstumpf als Pyramide visualisiert werden, wobei die Kamera an deren Spitze positioniert ist, wie in der nachfolgenden Abbildung illustriert. Diese Pyramide wird vorn und hinten von einer Zuschneidungsebene geschnitten. Der Körper innerhalb der Pyramide zwischen der vorderen und der hinteren Zuschneidungsebene ist der Pyramidenstumpf. Objekte werden nur angezeigt, wenn sie sich innerhalb dieses Körpers befinden.

![Illustration eines Pyramidenstumpfs mit vorderer und hinterer Zuschneidungsebene](images/frustum.png)

Wenn Sie sich vorstellen, dass Sie in einem dunklen Raum stehen und durch ein quadratisches Fenster blicken, haben Sie einen Pyramidenstumpf vor sich. In diesem Beispiel ist die nahe Zuschneidungsebene das Fenster, und die hintere Zuschneidungsebene ist die letztliche Begrenzung Ihres Sichtfeldes – das Haus auf der gegenüberliegenden Straßenseite, die Berge am Horizont oder auch nichts. Sie sehen alles innerhalb des Pyramidenstumpfs vom Fenster bis zur letztlichen Sichtbegrenzung – und nichts sonst.

Der Pyramidenstumpf wird nach „fov“ (Field of View, Gesichtsfeld) und dem Abstand zwischen der vorderen und der hinteren Zuschneidungsebene definiert, angegeben in z-Koordinaten (vgl. das folgende Diagramm).

![Diagramm des Pyramidenstumpfs](images/fovdiag.png)

In diesem Diagramm ist die Variable D der Abstand zwischen der Kamera und dem Ursprung des Bereichs, der im letzten Teil der Geometriepipeline definiert wurde – der Ansichtstransformation. Dies ist der Bereich, um den herum Sie die grenzen Ihres Pyramidenstumpfs anordnen. Informationen zur Verwendung dieser D-Variablen für die Erstellung der Projektionsmatrix finden Sie unter [Projektionstransformation](projection-transform.md)

## <a name="span-idviewportrectanglespanspan-idviewportrectanglespanspan-idviewportrectanglespanviewport-rectangle"></a><span id="Viewport_Rectangle"></span><span id="viewport_rectangle"></span><span id="VIEWPORT_RECTANGLE"></span>Viewport-Rechteck


Eine Viewport-Struktur enthält vier Mitglieder (X, Y, Breite, Höhe), die den Bereich der Renderzieloberfläche definieren, in die die Szene gerendert wird. Diese Werte entsprechen dem Zielrechteck oder Viewport-Rechteck, wie im folgenden Diagramm dargestellt.

![Diagramm des Viewport-Rechtecks](images/destrect.png)

Die Werte, die Sie für die Mitglieder X, Y, Breite und Höhe angeben, sind Bildschirmkoordinaten relativ zur linken oberen Ecke der Renderzieloberfläche. Die Struktur definiert zwei zusätzliche Mitglieder (MinZ und MaxZ), die die Tiefenbereiche für das Rendern der Szene angeben.

Direct3D nimmt an, dass das Viewport-Zuschneidungsvolumen von -1,0 bis 1,0 in X und von 1,0 bis -1,0 in Y reicht. Dies sind die Einstellungen die in der Vergangenheit am häufigsten von Anwendungen verwendet wurden. Sie können das Viewport-Seitenverhältnis vor dem Zuschneiden mit der [Projektionstransformation](projection-transform.md) anpassen.

**Hinweis:**   MinZ und MaxZ geben die Tiefenbereiche für das Rendern der Szene an und werden nicht zum Zuschneiden verwendet. Die meisten Anwendungen setzen diese Werte zwischen 0,0 und 1,0, damit das System das Rendering für den gesamten Bereich der Tiefenwerte im Tiefenpuffer durchführen kann. In manchen Fällen können Sie durch die Verwendung anderer Tiefenbereiche besondere Effekte erzielen. So können Sie beispielsweise zum Rendern einer Heads-up-Ansicht in einem Spiel beide Werte auf 0,0 setzen, damit das System Objekte in einer Szene im Vordergrund rendert; oder Sie setzen beide Werte auf 1,0, um ein Objekt zu rendern, das sich immer im Hintergrund befinden soll.

 

Die Abmessungen, die für die Mitglieder X, Y, Breite und Höhe einer Viewport-Struktur verwendet werden, legen den Ort und die Abmessungen des Viewports auf der Renderzieloberfläche fest. Diese Werte sind in Bildschirmkoordinaten relativ zur oberen linken Ecke der Oberfläche ausgedrückt.

Direct3D verwendet Position und Abmessungen des Viewports zur Skalierung der Scheitelpunkte, so dass eine gerenderte Szene an den korrekte Ort auf der Zieloberfläche passt. Intern fügt Direct3D diese Werte in die folgende Matrix ein, die auf jeden Scheitelpunkt angewendet wird.

![Gleichung der Matrix, die auf alle Scheitelpunkte angewendet wird](images/vpscale.png)

Diese Matrix skaliert Scheitelpunkte gemäß den Viewport-Abmessungen und dem gewünschten Tiefenbereich und übersetzt sie zum jeweiligen Ort auf der Renderzieloberfläche. Die Matrix wechselt auch die y-Koordinate zur Reflexion eines Bildschirmursprungs in der linken oberen Ecke mit abwärts zunehmenden y-Werten. Nach der Anwendung der Matrix sind die Scheitelpunkte weiterhin homogen – das heißt, sie sind \[x,y,z,w\]-Scheitelpunkte – und müssen zu nicht-homogenen Koordinaten konvertiert werden, bevor sie an den Rasterizer gesendet werden.

**Hinweis**   Anwendungen setzen MinZ und MaxZ typischerweise auf 0,0 und 1,0, damit das System das Rendering für den gesamten Tiefenbereich durchführt. Sie können aber auch andere Werte verwenden, um besondere Effekte zu erzielen. So können Sie etwa beide Werte auf 0,0 setzen, um alle Objekte in den Vordergrund zu zwingen, oder auf 1,0, um alle Objekte im Hintergrund zu rendern.

 

## <a name="span-idclearingaviewportspanspan-idclearingaviewportspanspan-idclearingaviewportspanclearing-a-viewport"></a><span id="Clearing_a_Viewport"></span><span id="clearing_a_viewport"></span><span id="CLEARING_A_VIEWPORT"></span>Löschen eines Viewports


Durch das Löschen des Viewports werden die Inhalte des Viewportrechtecks auf der Renderzieloberfläche zurückgesetzt. Dies kann auch das Rechteck auf den Tiefen- und Schablonenpufferoberflächen löschen.

## <a name="span-idsetuptheviewportforclippingspanspan-idsetuptheviewportforclippingspanspan-idsetuptheviewportforclippingspanset-up-the-viewport-for-clipping"></a><span id="Set_Up_the_Viewport_for_Clipping"></span><span id="set_up_the_viewport_for_clipping"></span><span id="SET_UP_THE_VIEWPORT_FOR_CLIPPING"></span>Einrichten des Viewports zum Beschneiden


Die Ergebnisse der Projektionsmatrix bestimmen das Zuschneidungsvolumen im Projektionsbereich als:

-w<sub>c</sub>&lt;= x<sub>c</sub>&lt;= w<sub>c</sub>

-w<sub>c</sub>&lt;= y<sub>c</sub>&lt;= w<sub>c</sub>

0 &lt;= z<sub>c</sub>&lt;= w<sub>c</sub>

Dabei gilt: x, y, z und w stehen für die Scheitelpunktkoordinaten nach Anwendung der Projektionstransformation. Alle Scheitelpunkte mit einer x-, y- oder z-Komponente außerhalb dieser Bereiche werden abgeschnitten, wenn die Zuschneidung aktiviert ist (dies ist das Standardverhalten).

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Koordinatensysteme und Geometrie](coordinate-systems-and-geometry.md)

 

 




