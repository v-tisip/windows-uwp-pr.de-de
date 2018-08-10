---
author: stevewhims
description: In diesem Thema werden die verschiedenen Kategorien der Werte, die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet der l-Werte und Rvalues gehört haben, aber sind andere Arten zu.
title: Wert Kategorien
ms.author: stwhi
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c ++, Cpp, Winrt, Projektion, verschieben, Weiterleitung, Wert Kategorien, Move Semantik, perfekte Weiterleitung, l-Wert, r-Wert, Glvalue, Prvalue, Xvalue
ms.localizationpriority: medium
ms.openlocfilehash: 75176334909e0e6bcf81763b543a19b70a4cba73
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2018
ms.locfileid: "2739086"
---
# <a name="value-categories"></a>Wert Kategorien
In diesem Thema werden die verschiedenen Kategorien der Werte, die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet der *l-Werte* und *Rvalues*gehört haben, aber sind andere Arten zu. Jeder Ausdruck in C++ ergibt ein Werts, das eine der in diesem Thema behandelten Kategorien gehört. Aspekte der Programmiersprache C++, dessen Facilies und Regeln, die das Verständnis der Wert Kategorien fordern sind vorhanden.

## <a name="an-lvalue-has-identity"></a>Ein l-Wert hat Identität.
Was bedeutet es für einen Wert *Identität*? Wenn Sie (oder können) die Adresse des Arbeitsspeichers eines Werts, hat der Wert der Identität. Auf diese Weise können Sie Aktionen ausführen mehr als Compare den Inhalt der Werte: Sie können vergleichen oder Identity zu unterscheiden.

Ein *l-Wert* hat Identität. Es ist nun eine Frage der nur zurückliegenden Interesse, dass das "l" in "l"-Wert eine Abkürzung von "Left" (wie, in der linken Seite einer Zuweisung) ist. In C++ kann ein l-Wert auf der linken *oder* auf der rechten Seite einer Zuweisung angezeigt werden. "L" in "l-Werte", klicken Sie dann hilft tatsächlich nicht Sie verstehen noch definieren, was sind. Sie müssen nur wissen, dass wir ein l-Wert aufrufen, wird ein Wert, der Identität hat.

Nun, es zwar Aussagen, l-Werte Identität haben, also tun Xvalues. Gehen wir einige zusätzliche in welche ein *Xvalue* weiter unten in diesem Thema wird (obwohl sie eine ausführliche Beschreibung nicht im Gültigkeitsbereich hier ist). Jetzt nur Beachten Sie, dass es eine Wert Kategorie Glvalue ist, für die "Allgemeiner (engl.) l-Wert" aufgerufen. Die Obermenge von Glvalues enthält l-Werte (auch bekannt als "klassische l-Werte") und Xvalues. Ja, während er sich "Identität hat ein l-Wert" true festgelegt ist, der vollständige Satz von Features, mit denen Identitätswert wird der Satz von Glvalues, wie in dieser Abbildung dargestellt.

![Ein l-Wert hat Identität.](images/has-identity1.png)

## <a name="an-rvalue-is-movable-an-lvalue-is-not"></a>Ein r-Wert ist verschiebbar. ein l-Wert ist nicht
Es gibt jedoch Werte, die nicht Glvalues sind. Daher sind Werte, die Sie *kann nicht* für eine Adresse Arbeitsspeicher erhalten (oder Sie können nicht verlassen, um gültig sein). Die Sounds wie einen Nachteil. Aber tatsächlich der Vorteil eines Werts d. h., dass er (die im Allgemeinen billig ist), sondern Kopie *Verschieben* können It (die in der Regel teuer ist). Verschieben einen Wert bedeutet, dass es nicht mehr an der Stelle, die verwendet werden. Ist es an der Stelle zugreifen werden verwendeten möchte etwas vermieden werden. Eine Erläuterung der wann und *wie* , wird ein Wert außerhalb des Gültigkeitsbereichs für dieses Thema zu verschieben. Zu diesem Thema müssen wir wissen, dass ein Wert, der verschiebbar ist als einen *r-Wert*bezeichnet wird.

"R" in "r"-Wert ist eine Abkürzung des "rechts" (wie, in der rechten Seite einer Zuweisung). Jedoch können Rvalues und Verweise auf Rvalues, außerhalb von Zuordnungen. "R" in "Rvalues," ist, nicht das, was konzentrieren. Sie müssen nur wissen, dass wir ein r-Wert aufrufen, wird ein Wert, der verschiebbar ist.

Ein l-Wert nicht umgekehrt bewegliche, wie in der Abbildung gezeigt. Ein l-Wert kann nicht verschoben werden, da, wenn Sie konnte, klicken Sie dann unsichere (oder sogar katastrophale) Es wäre, weiterhin später darauf zugreifen. Beachten Sie, dass Sie ihre Identität verfügen.

![Ein r-Wert ist verschiebbar. ein l-Wert ist nicht](images/is-movable.png)

Ein l-Wert kann nicht verschoben werden. Aber es *ist* eine Art von Glvalue (der Satz von Aufgaben mit der Identität), die Sie verschieben können&mdash;Wenn Sie genau wissen, was Sie tun&mdash;und die Xvalue ist. Wenn das vollständige Bild des Wert Kategorien Wir betrachten, werden wir noch einmal weiter unten diese Idee erneut.

## <a name="an-lvalue-has-identity-a-prvalue-does-not"></a>Ein l-Wert hat Identität. nicht der Fall ist eine prvalue
In dieser Phase wissen wir, was Identität hat. Und wir wissen, was verschiebbar ist und was nicht. Aber wir noch nicht noch mit dem Namen der Gruppe von Werten, die diese *nicht* verfügen Identität. Die Gruppe als *Prvalue*oder "reine r-Wert" bekannt ist.

![Ein l-Wert hat Identität. nicht der Fall ist eine prvalue](images/has-identity2.png)

## <a name="the-complete-picture-of-value-categories"></a>Das vollständige Bild des Wert Kategorien
Es wird nur um den Info und Abbildungen oben in einer einzelnen, großen Bild zu kombinieren.

![Das vollständige Bild des Wert Kategorien](images/value-categories.png)

- Eine Glvalue (Allgemeine l-Wert) hat Identität.
- Ein l-Wert (eine Art von Glvalue) Identität hat, aber nicht verschiebbar. Dies sind in der Regel Lese-/ Schreibzugriff-Werten, die Sie um Verweis oder-Verweis oder Wert übergeben, wenn das Kopieren kostengünstig ist.
- Ein Xvalue (eine Art von Glvalue, sondern auch eine Art von r-Wert) über Identität und kann auch verschoben werden. Möglicherweise ein sammelte l-Wert, der Sie sich entschieden haben, verschieben, da das Kopieren teuer ist und Sie vermutlich nicht die ihn danach aufrufen. Wie Sie ein l-Wert in einer Xvalue und die Gründe für das Verschieben, umwandeln müssen warten, bis ein anderes Thema. Aber Sie können das "X" in "Xvalue" sich als vorstellen Bedeutung "Experten", wenn Ihnen dabei hilft.
- Eine Prvalue (reine r-Wert; eine Art von r-Wert) verfügt nicht über Identität, aber kann verschoben werden. Dies sind in der Regel Literalen, gegebebenfalls, zurückgeben Werte&mdash;alles, was ist das Ergebnis der Auswertung eines Ausdrucks (ein Ausdruck, der ein Glvalue nicht ist) oder eines anderen durch einen Wert von einer Funktion zurückgegeben.
- Ein r-Wert kann verschoben werden.
