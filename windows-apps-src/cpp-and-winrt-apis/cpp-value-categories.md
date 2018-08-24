---
author: stevewhims
description: In diesem Thema werden die verschiedenen Kategorien der Werte, die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet der l-Werte und Rvalues gehört haben, aber sind andere Arten zu.
title: Wert Kategorien und Verweise auf diese
ms.author: stwhi
ms.date: 08/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c ++, Cpp, Winrt, Projektion, verschieben, Weiterleitung, Wert Kategorien, Move Semantik, perfekte Weiterleitung, l-Wert, r-Wert, Glvalue, Prvalue, Xvalue
ms.localizationpriority: medium
ms.openlocfilehash: cbccaf78b45d85d93619977d149431c4eec9e10a
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2835032"
---
# <a name="value-categories-and-references-to-them"></a>Wert Kategorien und Verweise auf diese
In diesem Thema werden die verschiedenen Kategorien von Werte (und Verweise auf Werte), die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet der *l-Werte* und *Rvalues*gehört haben, aber möglicherweise nicht stellen sie in der Begriffe, die in diesem Thema wird. Und sind andere Arten der Werte zu.

Jeder Ausdruck in C++ ergibt ein Werts, das eine der in diesem Thema behandelten Kategorien gehört. Aspekte der Programmiersprache C++, seine Facilies und Regeln, die gefordert wird das richtige Verständnis dieser Wert Kategorien und die Verweise darauf sind vorhanden. Die Adresse eines Werts, Kopieren eines Werts, verschieben einen Wert und einen Wert an eine andere Funktion Weiterleiten beispielsweise nehmen. In diesem Thema nicht in alle Aspekte im Detail gehen, aber es enthält grundlegende Informationen zu verstehen und einen einfarbigen davon.

Die Informationen in diesem Thema wird durch die zwei unabhängigen Eigenschaften der Identität und Movability [Stroustrup 2013] im Hinblick auf Stroustrups Analyse der Wert Kategorien eingerahmt.

## <a name="an-lvalue-has-identity"></a>Ein l-Wert hat Identität.
Was bedeutet es für einen Wert *Identität*? Wenn die Arbeitsspeicher-Adresse eines Werts Sie haben (oder können) herunter, und sicher, und klicken Sie dann den Wert Identität hat. Auf diese Weise können Sie Aktionen ausführen mehr als Compare den Inhalt der Werte: Sie können vergleichen oder Identity zu unterscheiden.

Ein *l-Wert* hat Identität. Es ist nun eine Frage der nur zurückliegenden Interesse, dass das "l" in "l"-Wert eine Abkürzung von "Left" (wie, in der linken Seite einer Zuweisung) ist. In C++ kann ein l-Wert auf der linken *oder* auf der rechten Seite einer Zuweisung angezeigt werden. "L" in "l-Werte", klicken Sie dann hilft tatsächlich nicht Sie verstehen noch definieren, was sind. Sie müssen nur wissen, dass wir ein l-Wert aufrufen, wird ein Wert, der Identität hat.

Beispiele für Ausdrücke, die l-Werte sind: einer benannten Variablen oder Konstanten; oder eine Funktion, die einen Verweis zurückgibt. Beispiele für Ausdrücke, die *nicht* l-Werte sind: ein temporäres; oder eine Funktion, die durch einen Wert zurückgibt.

```cppwinrt
int& get_by_ref() { ... }
int get_by_val() { ... }

int main()
{
    std::vector<byte> vec{ 99, 98, 97 };
    std::vector<byte>* addr1{ &vec }; // ok: vec is an lvalue.
    int* addr2{ &get_by_ref() }; // ok: get_by_ref() is an lvalue.

    int* addr3{ &(get_by_ref() + 1) }; // Error: get_by_ref() + 1 is not an lvalue.
    int* addr4{ &get_by_val() }; // Error: get_by_val() is not an lvalue.
}
```

Nun, es zwar Aussagen, l-Werte Identität haben, also tun Xvalues. Gehen wir mehr in welche ein *Xvalue* weiter unten in diesem Thema wird. Jetzt nur Beachten Sie, dass es eine Wert Kategorie Glvalue ist, für die "Allgemeiner (engl.) l-Wert" aufgerufen. Die Obermenge von Glvalues enthält l-Werte (auch bekannt als *klassische l-Werte*) und Xvalues. Ja, während er sich "Identität hat ein l-Wert" true festgelegt ist, der vollständige Satz von Features, mit denen Identitätswert wird der Satz von Glvalues, wie in dieser Abbildung dargestellt.

![Ein l-Wert hat Identität.](images/has-identity1.png)

## <a name="an-rvalue-is-movable-an-lvalue-is-not"></a>Ein r-Wert ist verschiebbar. ein l-Wert ist nicht
Es gibt jedoch Werte, die nicht Glvalues sind. Daher sind Werte, die Sie *kann nicht* für eine Adresse Arbeitsspeicher erhalten (oder Sie können nicht verlassen, um gültig sein). Wir haben gesehen, einige dieser Werte im obigen Codebeispiel. Das klingt ein Nachteil. Aber tatsächlich der Vorteil eines Werts wie d. h., dass Sie daraus *Verschieben* können (die im Allgemeinen billig ist), statt daraus (die in der Regel teuer ist) kopieren. Umstellen von einem Wert bedeutet, dass es nicht mehr an der Stelle, die verwendet werden. Ist es an der Stelle zugreifen werden verwendeten möchte etwas vermieden werden. Eine Erläuterung der wann und *wie* , wird ein Wert außerhalb des Gültigkeitsbereichs für dieses Thema zu verschieben. Zu diesem Thema müssen wir wissen, dass ein Wert, der verschiebbar ist als ein *r-Wert* (oder *klassische r-Wert*) bezeichnet wird.

"R" in "r"-Wert ist eine Abkürzung des "rechts" (wie, in der rechten Seite einer Zuweisung). Jedoch können Rvalues und Verweise auf Rvalues, außerhalb von Zuordnungen. "R" in "Rvalues," ist, nicht das, was konzentrieren. Sie müssen nur wissen, dass wir ein r-Wert aufrufen, wird ein Wert, der verschiebbar ist.

Ein l-Wert nicht umgekehrt bewegliche, wie in der Abbildung gezeigt. Ein l-Wert, die verschoben würde die Definition der *l-Wert*setzen, und es wäre ein unerwarteter Fehler für Code, die nach vernünftigem Ermessen sehr erwartet, weiterhin dass auf die l-Wert zugreifen können.

![Ein r-Wert ist verschiebbar. ein l-Wert ist nicht](images/is-movable.png)

Ein l-Wert kann nicht verschoben werden. Aber es *ist* eine Art von Glvalue (der Satz von Aufgaben mit der Identität), die Sie verschieben können&mdash;Wenn Sie genau wissen, was Sie tun (einschließlich, ohne dabei darauf zugreifen, nach dem Verschieben)&mdash;und die Xvalue ist. Wenn das vollständige Bild des Wert Kategorien Wir betrachten, werden wir noch einmal weiter unten diese Idee erneut.

## <a name="rvalue-references-and-reference-binding-rules"></a>R-Wert-Referenzen und Verweis Bindung Regeln
In diesem Abschnitt werden die Syntax für einen Verweis auf ein r-Wert. Wir müssen warten, bis eine andere Thema aus, um eine erhebliche Behandlung verschieben und Weiterleiten von eingefügt, aber dies sind Probleme, die durch Verweise r-Wert gelöst werden. Bevor wir uns r-Wert Verweise ansehen, allerdings müssen Sie zuerst zur besseren werden `T&` &mdash;das, was wir haben früher wurden aufrufen nur "einen Verweis". Es ist wirklich so "ein l-Wert (nicht-Const) Referenz", die auf einen Wert bezieht sich auf die der Benutzer des Verweises schreiben kann.

```cppwinrt
template<typename T> T& get_by_lvalue_ref() { ... } // Get by lvalue (non-const) reference.
template<typename T> void set_by_lvalue_ref(T&) { ... } // Set by lvalue (non-const) reference.
```

Ein Verweis l-Wert kann auf einen l-Wert, jedoch nicht auf ein r-Wert binden.

L-Wert Konstante Verweise sind (`T const&`), die auf Objekte, der der Benutzer über den Verweis *kann nicht* geschrieben (beispielsweise eine Konstante) verweisen.

```cppwinrt
template<typename T> T const& get_by_lvalue_cref() { ... } // Get by lvalue const reference.
template<typename T> void set_by_lvalue_cref(T const&) { ... } // Set by lvalue const reference.
```

Ein l-Wert-Verweis kann an einer l-Wert oder ein r-Wert binden.

Die Syntax für einen Verweis auf ein r-Wert vom Typ `T` wird als geschrieben `T&&`. Ein Verweis r-Wert bezieht sich auf einen Wert bewegliche&mdash;einen Wert dar, deren Inhalt wir nicht beibehalten, nachdem wir (beispielsweise ein temporäres) verwendet haben müssen. Seit der gesamten Punkt zum Wechsel von (wodurch ändern) der Wert an gebunden ist ein Verweis r-Wert `const` und `volatile` Qualifizierer (auch bekannt als cv-Qualifizierer) gelten nicht für r-Wert verweisen.

```cppwinrt
template<typename T> T&& get_by_rvalue_ref() { ... } // Get by rvalue reference.
struct A { A(A&& other) { ... } }; // A move constructor takes an rvalue reference.
```

Ein Verweis r-Wert bindet ein r-Wert. Tatsächlich im Hinblick auf Überladung Auflösung ein r-Wert *bevorzugt* ein Verweis auf r-Wert Verweis als auf eine Konstante l-Wert gebunden werden. Aber ein r-Wert-Verweis kann nicht an ein l-Wert gebunden werden, da Sie, wie wir gesagt haben, ein r-Wert einen Wert, dessen Inhalt bezieht sich Reference auf davon ausgegangen wird, dass wir nicht beibehalten (sag, die Parameter für einen Konstruktor Move) müssen.

Sie können auch übergeben ein r-Wert, auf dem ein Argumentwert zu erwarten ist über Kopie Konstruktion (oder Move Konstruktion, wenn der r-Wert ein Xvalue ist).

## <a name="a-glvalue-has-identity-a-prvalue-does-not"></a>Ein Glvalue hat Identität. nicht der Fall ist eine prvalue
In dieser Phase wissen wir, was Identität hat. Und wir wissen, was verschiebbar ist und was nicht. Aber wir noch nicht noch mit dem Namen der Gruppe von Werten, die diese *nicht* verfügen Identität. Die Gruppe als *Prvalue*oder *reine r-Wert*bekannt ist.

```cppwinrt
int& get_by_ref() { ... }
int get_by_val() { ... }

int main()
{
    int* addr3{ &(get_by_ref() + 1) }; // Error: get_by_ref() + 1 is a prvalue.
    int* addr4{ &get_by_val() }; // Error: get_by_val() is a prvalue.
}
```

![Ein l-Wert hat Identität. nicht der Fall ist eine prvalue](images/has-identity2.png)

## <a name="the-complete-picture-of-value-categories"></a>Das vollständige Bild des Wert Kategorien
Es wird nur um den Info und Abbildungen oben in einer einzelnen, großen Bild zu kombinieren.

![Das vollständige Bild des Wert Kategorien](images/value-categories.png)

### <a name="glvalue-i"></a>Glvalue (i)
Eine Glvalue (Allgemeine l-Wert) hat Identität.

### <a name="lvalue-im"></a>l-Wert (I\ & \!m)
Ein l-Wert (eine Art von Glvalue) Identität hat, aber nicht verschiebbar. Dies sind in der Regel Lese-/ Schreibzugriff-Werten, die Sie um Verweis oder-Verweis oder Wert übergeben, wenn das Kopieren kostengünstig ist. Ein l-Wert kann nicht in einen Bezug r-Wert gebunden werden.

### <a name="xvalue-im"></a>xValue (I\ & m)
Ein Xvalue (eine Art von Glvalue, sondern auch eine Art von r-Wert) über Identität und kann auch verschoben werden. Möglicherweise ein sammelte l-Wert, der Sie sich entschieden haben, verschieben, da das Kopieren teuer ist und Sie vermutlich nicht die ihn danach aufrufen. Nachfolgend finden Sie, wie Sie ein l-Wert in einer Xvalue aktivieren können.

```cppwinrt
struct A { ... };
A a; // a is an lvalue...
static_cast<A&&>(a); // ...but this expression is an xvalue.
```

Im obigen Codebeispiel hatte keine wir nichts noch verschoben. Durch das Umwandeln eines l-Wert in einen Bezug unbenannte r-Wert haben wir eine Xvalue erstellt. Sie können weiterhin anhand des Namens der l-Wert bezeichnet werden. befindet sich jedoch, als ein Xvalue jetzt *fähig* verschoben wird. Der Grund dafür, und welche verschieben tatsächlich, aussieht nach einem anderen Thema warten müssen. Jedoch können Sie sich das "X" in "Xvalue" als Bedeutung "Expert-only" Wenn Ihnen dabei hilft, vorstellen. Durch das Umwandeln eines l-Wert in einer Xvalue (eine Art von r-Wert), wird der Wert der Bindung an ein Verweis r-Wert.

Es folgen zwei weitere Beispiele für Xvalues&mdash;Aufrufen einer Funktion, die einen Verweis unbenannte r-Wert zurückgibt, und den Zugriff auf ein Mitglied einer Xvalue.

```cppwinrt
struct A { int m; };
A&& f();
f(); // This expression is an xvalue...
f().m; // ...and so is this.
```

### <a name="prvalue-im"></a>Prvalue (\!i\ & m)
Eine Prvalue (reine r-Wert; eine Art von r-Wert) verfügt nicht über Identität, aber kann verschoben werden. Dies in der Regel gegebebenfalls sind, gibt das Ergebnis des Aufrufs einer Funktion, die nach Wert oder das Ergebnis der Auswertung eines anderen Ausdrucks, der ein Glvalue nicht ist,

### <a name="rvalue-m"></a>r-Wert (m)
Ein r-Wert kann verschoben werden. Ein r-Wert- *Verweis* bezieht sich immer um ein r-Wert (ein Wert, dessen Inhalt davon ausgegangen wird, die wir nicht beibehalten müssen).

Aber ein r-Wert-Verweis selbst ein r-Wert ist? Ein *unbenannte* r-Wert Verweis (wie in den oben genannten Xvalue Codebeispielen dargestellt) ist ein Xvalue Ja, es ist also ein r-Wert. Bevorzugte ein r-Wert Funktion Verweisparameter, wie der Move-Konstruktor gebunden sein. Umgekehrt (und möglicherweise counter-intuitively), wenn ein Verweis r-Wert einen Namen hat, wird des Ausdrucks, der mit diesem Namen besteht ein l-Wert. So es *kann nicht* an einen Verweisparameter r-Wert gebunden werden. Aber es ist einfach zu vereinfachen dazu&mdash;einfach wieder in einen Bezug unbenannte r-Wert (eine Xvalue) umgewandelt.

```cppwinrt
void foo(A&) { ... }
void foo(A&&) { ... }
void bar(A&& a) // a is a named rvalue reference; it's an lvalue.
{
    foo(a); // Calls foo(A&).
    foo(static_cast<A&&>(a)); // Calls foo(A&&).
}
A&& get_by_rvalue_ref() { ... } // This unnamed rvalue reference is an xvalue.
```

### <a name="im"></a>\!i\ & \!m
Die Art des Werts, der keinen Identität und ist nicht verschiebbar ist die eine Kombination aus, der wir noch nicht besprochen wurden. Jedoch können wir, ignorieren, da dieser Kategorie ist nützlich, sich in der Sprache C++ nicht.

## <a name="reference-collapsing-rules"></a>Verweis Reduzieren von Regeln
Mehrere like Verweise in einem Ausdruck (einem l-Wert Verweis Verweis auf ein l-Wert oder ein Verweis auf r-Wert Verweis auf ein r-Wert) beenden eine einer anderen Out.

- `A& &` Blendet in `A&`.
- `A&& &&` Blendet in `A&&`.

Im Gegensatz zu verweisen in einem Ausdruck mehrere reduzieren in einen Bezug l-Wert.

- `A& &&` Blendet in `A&`.
- `A&& &` Blendet in `A&`.

## <a name="forwarding-references"></a>Weiterleiten von Verweise
In diesem letzten Abschnitt gegenübergestellt Verweise auf r-Wert, der bereits, mit dem verschiedene Konzept einer *Weiterleitung Verweis*erläutert.

```cppwinrt
void foo(A&& a) { ... }
```

- `A&&` ist ein Verweis r-Wert an, wie wir gesehen haben. Const und volatile gelten nicht für Verweise r-Wert.
- `foo` nur Rvalues vom Typ **A**akzeptiert.
- Verweist auf den Grund r-Wert (z. B. `A&&`) vorhanden ist, sodass Sie eine Überladung erstellen können, die für die Groß-/Kleinschreibung ein temporäres (oder andere r-Wert) übergebenen optimiert ist.

```cppwinrt
template <typename _Ty> void bar(_Ty&& ty) { ... }
```

- `_Ty&&` ist ein *Verweis weiterleiten*. Je nachdem, was übergebene `bar`, Typ **_Ty** Const/nicht konstanter unabhängig veränderlich/unveränderliche werden konnte.
- `bar` akzeptiert alle l-Wert oder r-Wert des Typs **_Ty**.
- Übergeben eines l-Wert bewirkt, dass die Weiterleitung Referenz zu `_Ty& &&`, die zur Referenz l-Wert wird reduziert `_Ty&`.
- Übergabe ein r-Wert bewirkt, dass die Weiterleitung Referenz zu `_Ty&& &&`, die zur Referenz r-Wert wird reduziert `_Ty&&`.
- Der Grund dafür weiterleiten Verweise (z. B. `_Ty&&`) vorhanden ist *nicht* zur Optimierung der aber was Sie an Sie übergeben werden und auf transparent und effizientes weiterleiten. Sie wahrscheinlich einen Verweis Weiterleitung auftreten nur, wenn Sie Library Code schreiben (oder eng Studie)&mdash;beispielsweise eine Factory-Funktion, die auf Konstruktorargumente weiterleitet.

## <a name="sources"></a>Quellen
* \[Stroustrup, 2013\] b Stroustrup: die Programmiersprache C++, das vierte Edition. ISBN-Wesley. 2013.
