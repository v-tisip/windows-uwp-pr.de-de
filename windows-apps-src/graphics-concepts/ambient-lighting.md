---
title: Umgebungslicht
description: "Das Umgebungslicht bietet konstante Beleuchtung für eine Szene."
ms.assetid: C34FA65A-3634-4A4B-B183-4CDA89F4DC95
keywords:
- Umgebungslicht
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 77865a483f226fba912c03e2f9abe17eaa7fbee0
ms.lasthandoff: 02/07/2017

---

# <a name="ambient-lighting"></a>Umgebungslicht


Das Umgebungslicht bietet konstante Beleuchtung für eine Szene. Es erhellt die Scheitelpunkte aller Objekt gleichermaßen, da es nicht von anderen Beleuchtungsfaktoren wie vertexspezifischen Normalen, Lichteinfallsrichtung, Position der Lichtquelle, Reichweite oder Dämpfung abhängt. Das Umgebungslicht bleibt in alle Richtungen hin unverändert und es versieht alle Pixel eines Objekts mit der gleichen Farbe. Obwohl die Berechnung schnell ist, sehen die Objekte flach und unrealistisch aus.

Das Umgebungslicht ist zwar der schnellste Beleuchtungstyp, es erzeugt allerdings die unrealistischsten Ergebnisse. Direct3D enthält eine einzige globale Umgebungslichteigenschaft, die Sie ohne Erstellen des Lichts verwenden können. Alternativ können Sie jede Lichtquellen als Umgebungslicht festlegen.

Das Umgebungslicht für eine Szene wird durch die folgende Gleichung beschrieben.

Umgebungslicht = Cₐ\*\[Gₐ + sum(Atten<sub>i</sub>\*Spot<sub>i</sub>\*L<sub>ai</sub>)\]

Dabei gilt:

| Parameter         | Standardwert | Typ          | Beschreibung                                                                                                       |
|-------------------|---------------|---------------|-------------------------------------------------------------------------------------------------------------------|
| Cₐ                | (0,0,0,0)     | D3DCOLORVALUE | Materielle Umgebungsfarbe                                                                                            |
| Gₐ                | (0,0,0,0)     | D3DCOLORVALUE | Globale Umgebungsfarbe                                                                                              |
| Atten<sub>i</sub> | (0,0,0,0)     | D3DCOLORVALUE | Dämpfung der ith-Beleuchtung. Unter [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md). |
| Spot<sub>i</sub>  | (0,0,0,0)     | D3DVECTOR     | Spotlight-Faktor der ith-Beleuchtung. Unter [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md).  |
| Summe               | Nicht zutreffend           | Nicht zutreffend           | Summe des Umgebungslichts                                                                                          |
| L<sub>ai</sub>    | (0,0,0,0)     | D3DVECTOR     | Helle Umgebungsfarbe der ith-Beleuchtung                                                                              |

 

Der Wert für Cₐ ist entweder:

-   Vertexfarbe1, wenn AMBIENTMATERIALSOURCE = D3DMCS\_FARBE1 und die erste Vertexfarbe in der Vertex-Deklaration angegeben wird.
-   Vertexfarbe2, wenn AMBIENTMATERIALSOURCE = D3DMCS\_FARBE2 und die zweite Vertexfarbe in der Vertex-Deklaration angegeben wird.
-   Materielle Umgebungsfarbe.

**Hinweis**   Wenn eine der beiden AMBIENTMATERIALSOURCE-Optionen verwendet wird und die Vertexfarbe nicht angegeben ist, wird die materielle Umgebungsfarbe verwendet.

 

Um die materielle Umgebungsfarbe anzuwenden, verwenden Sie „SetMaterial” wie im folgenden Beispielcode dargestellt.

Gₐ ist die globale Umgebungsfarbe. Sie wird mit „SetRenderState(D3DRS\_AMBIENT)” festgelegt. In einer Direct3D-Szene gibt es eine globale Umgebungsfarbe. Dieser Parameter ist keinem Direct3D-Lichtobjekt zugeordnet.

L<sub>ai</sub> ist die Umgebungsfarbe der ith-Beleuchtung in der Szene. Jedes Direct3D-Licht hat eine Reihe von Eigenschaften, von denen eine die Umgebungsfarbe ist. Der Begriff „Summe” (L<sub>Ai</sub>) beschreibt die Summe aller Umgebungsfarben in der Szene.

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


In diesem Beispiel wird das Objekt durch die Farbe des Umgebungslichts der Szene und einer materiellen Umgebungsfarbe hervorgehoben.

```
#define GRAY_COLOR  0x00bfbfbf

Ambient.r = 0.75f;
Ambient.g = 0.0f;
Ambient.b = 0.0f;
Ambient.a = 0.0f;
```

Gemäß der Gleichung ist die resultierende Farbe für die Objekt-Scheitelpunkte eine Kombination aus der materiellen Farbe und der Farbe des Lichts.

Die folgenden beiden Abbildungen zeigen die materielle Farbe (in Grau) und die Farbe des Lichts (hellrot).

![Abbildung einer grauen Kugel](images/amb1.jpg)![Abbildung einer roten Kugel](images/lightred.jpg)

Die resultierende Szene wird in der folgenden Abbildung dargestellt. Das einzige Objekt in der Szene ist eine Kugel. Das Umgebungslicht beleuchtet alle Objekt-Schnittpunkte mit derselben Farbe. Es ist nicht von der Vertexnormale oder Lichteinfallsrichtung abhängig. Die Kugel sieht wie ein 2D-Kreis aus, da es keinen Unterschied in der Schattierung der Oberfläche des Objekts gibt.

![Abbildung einer Kugel mit Umgebungslicht](images/lighta.jpg)

Verwenden Sie neben dem Umgebungslicht diffuses oder Glanzlicht, um Objekten ein realistischeres Aussehen zu verleihen.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Beleuchtungsmathematik](mathematics-of-lighting.md)

 

 





