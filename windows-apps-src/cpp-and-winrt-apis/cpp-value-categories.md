---
author: stevewhims
description: Dieses Thema beschreibt die verschiedenen Kategorien von Werten, die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet kenne l-Werte und Rvalues, aber es gibt auch andere Arten.
title: Wertekategorien und Verweise auf diese
ms.author: stwhi
ms.date: 08/11/2018
ms.topic: article
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, verschieben, Weiterleitung, Wertekategorien, Move-Semantik, perfekte Weiterleitung, l-Wert, r-Wert, Glvalue, Prvalue, Xvalue
ms.localizationpriority: medium
ms.openlocfilehash: b600c09c3629ce52590daa42b9046fab3784a78f
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6987829"
---
# <a name="value-categories-and-references-to-them"></a>Wertekategorien und Verweise auf diese
Dieses Thema beschreibt die verschiedenen Kategorien der Werte (und Verweise auf Werte), die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet kenne *l-Werte* und *Rvalues*, aber möglicherweise nicht stellen diese in die Begriffe, die in diesem Thema wird vorgestellt. Und es gibt auch andere Arten von Werten.

Jeder Ausdruck in C++ ergibt einen Wert, der auf eine der in diesem Thema erläuterten Kategorien gehört. Es gibt Aspekte der Programmiersprache C++, dessen Facilies und Regeln, die das Verständnis der diese Wertekategorien und Verweise auf diese anfordern. Die Adresse eines Werts, einen Wert kopieren, verschieben einen Wert und einen Wert an eine andere Funktion Weiterleiten z. B. nehmen. In diesem Thema nicht in all diese Aspekte im Detail gehen, aber es enthält grundlegende Informationen für ein grundlegendes Verständnis davon.

Die Informationen in diesem Thema wird durch die zwei unabhängigen Eigenschaften der Identität und Movability [Stroustrup 2013] hinsichtlich Stroustrups Analyse der Wertekategorien dargestellt.

## <a name="an-lvalue-has-identity"></a>Ein l-Wert hat Identität
Was bedeutet es für einen Wert *Identität*? Wenn Sie haben die Speicheradresse eines Werts (oder geschaltet werden können), und sie problemlos, und klicken Sie dann der Wert Identität verfügt. Auf diese Weise möglich, mehr als vergleichen den Inhalt der Werte: Sie können vergleichen oder durch Identität zu unterscheiden.

Ein *l-Wert* hat Identität. Es ist jetzt eine Frage des nur rückwirkende Interesse an, dass die "l" in "l-Wert" Abkürzung für "Links" (wie, in der linken Seite einer Zuweisung) ist. In C++ kann ein l-Wert auf der linken *oder* auf der rechten Seite einer Zuweisung angezeigt. Die "l" in "l-Werte", unterstützen nicht dann tatsächlich Sie bei begreifen noch definieren, was sind. Sie müssen nur, um zu verstehen, was rufen wir ein l-Wert ein Wert ist, der Identität verfügt.

Beispiele für Ausdrücke, die l-Werte sind: einer benannten Variable oder Konstante; eine Funktion, die einen Verweis oder gibt. Beispiele für Ausdrücke, die *nicht* l-Werte sind: ein temporäres; oder eine Funktion, die durch einen Wert zurückgibt.

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

Nun, es zwar Aussagen, l-Werte Identität haben, also tun Xvalues. Gehen wir mehr in welche ein *Xvalue* weiter unten in diesem Thema wird. Für den Moment lediglich Beachten Sie, dass es eine Wert Kategorie Glvalue ist, für die "generalisiert l-Wert" bezeichnet. Die Übermenge von Glvalues enthält l-Werte (auch bekannt als *klassische l-Werte*) und Xvalues. Ja, während er sich "ein l-Wert besitzt Identität" ist "true", der vollständige Satz von Dinge, die Identität der Satz von Glvalues, wie in der folgenden Abbildung dargestellt.

![Ein l-Wert hat Identität](images/has-identity1.png)

## <a name="an-rvalue-is-movable-an-lvalue-is-not"></a>Ein r-Wert kann verschoben werden; ein l-Wert ist nicht
Aber es gibt Werte, die nicht Glvalues sind. Es gibt daher Werte, die Sie *kann nicht* zu eine Speicheradresse für erhalten (oder nicht verlässlich er gültig sein). Wir haben gesehen, einige dieser Werte im obigen Codebeispiel. Dies klingt wie einen Nachteil. Aber in der Tat können den Vorteil, einen Wert wie das heißt, dass Sie daraus *Verschieben* können (was in der Regel günstig ist), statt daraus (was in der Regel teuer ist) kopieren. Verschieben von einem Wert bedeutet, dass es nicht mehr an der Stelle, die sie verwendet werden. Also versuchen, darauf an der Stelle zugreifen, die sie verwendet werden, die vermieden werden. Eine Erläuterung der wann und *wie* verschieben, dass ein Wert außerhalb des Bereichs für dieses Thema ist. In diesem Thema benötigen wir lediglich wissen, dass ein Wert, der bewegliche ist, als ein *r-Wert* (oder *klassische r-Wert*) bezeichnet wird.

"R" in "r"-Wert ist eine Abkürzung für "rechts" (z. B. in, die rechte Seite einer Zuweisung). Sie können jedoch Rvalues und Verweise auf Rvalues, außerhalb Zuweisungen. Die "R" in "Rvalues", ist, nicht das, was konzentrieren. Sie müssen nur, um zu verstehen, dass was rufen wir ein r-Wert einen Wert, der bewegliche ist.

Ein l-Wert, es ist nicht umgekehrt bewegliche, wie in der folgenden Abbildung dargestellt. Ein l-Wert, die verschoben würde die Definition von *l-Wert*gibt, und es wäre ein unerwartetes Problem für Code, der erwartet sehr vernünftig weiterhin auf die l-Wert zugreifen können.

![Ein r-Wert kann verschoben werden; ein l-Wert ist nicht](images/is-movable.png)

Ein l-Wert kann nicht verschoben werden. Aber es *ist* eine Art von Glvalue (der Satz von Dinge mit Identität), die Sie verschieben können&mdash;, wenn Sie wissen, was Sie tun (einschließlich ohne dabei darauf zugreifen, nach dem Verschieben)&mdash;und die Xvalue ist. Wir werden diese Idee noch einmal unten, besuchen Sie Wenn wir die vollständiges Bild Wert Kategorien betrachten.

## <a name="rvalue-references-and-reference-binding-rules"></a>R-Wert Verweise und Referenz-Bindungsregeln
In diesem Abschnitt werden die Syntax für einen Verweis auf ein r-Wert. Wir müssen warten, bis ein anderes Thema, um einen erheblichen Behandlung von verschieben und weiterleiten zu starten, aber dies sind Probleme, die von r-Wert Verweise gelöst werden. Bevor wir r-Wert Verweise betrachten, jedoch müssen wir zunächst über deutlicher zu erkennen, `T&` &mdash;das, was wir haben früher wurden aufrufen einfach "einen Verweis". Es ist wirklich "ein l-Wert (nicht-Const) Referenz" bezieht sich auf einen Wert mit dem der Benutzer des Verweises schreiben kann.

```cppwinrt
template<typename T> T& get_by_lvalue_ref() { ... } // Get by lvalue (non-const) reference.
template<typename T> void set_by_lvalue_ref(T&) { ... } // Set by lvalue (non-const) reference.
```

Ein Verweis l-Wert kann ein l-Wert, aber nicht in ein r-Wert gebunden werden.

Anschließend gibt es const Verweise l-Wert (`T const&`), die auf Objekte, die mit dem Schreiben von der Benutzer über die Referenz *kann nicht* (z. B. eine Konstante) verweisen.

```cppwinrt
template<typename T> T const& get_by_lvalue_cref() { ... } // Get by lvalue const reference.
template<typename T> void set_by_lvalue_cref(T const&) { ... } // Set by lvalue const reference.
```

Ein l-Wert-Verweis kann ein l-Wert oder ein r-Wert binden.

Die Syntax für einen Verweis auf ein r-Wert vom Typ `T` wird als geschrieben `T&&`. Ein r-Wert-Verweis bezieht sich auf bewegliche Wert&mdash;einen Wert, deren Inhalt müssen wir nicht beibehalten, nachdem wir es (z. B. ein temporäres) verwendet haben. Seit der gesamte Punkt Verschieben von (wodurch ändern) der Wert gebunden ist, eine Referenz r-Wert `const` und `volatile` Qualifizierer (auch bekannt als cv-Qualifizierer) r-Wert-Verweise gelten nicht.

```cppwinrt
template<typename T> T&& get_by_rvalue_ref() { ... } // Get by rvalue reference.
struct A { A(A&& other) { ... } }; // A move constructor takes an rvalue reference.
```

Ein r-Wert-Verweis Bindung an ein r-Wert. In der Tat hinsichtlich der Überladung Auflösung ein r-Wert *ist* ein Verweis auf r-Wert Verweis als auf ein const l-Wert gebunden werden. Aber eine Referenz r-Wert kann nicht daran, wie bereits erwähnt haben, ein r-Wert-Verweis auf einen Wert, deren Inhalt bezieht sich davon ausgegangen wird, dass wir nicht beibehalten (beispielsweise der Parameter für einen Verschiebungskonstruktor) müssen auf eine l-Wert binden.

Sie können auch übergeben ein r-Wert, in denen ein Argument als Wert zu erwarten ist über Kopie Konstruktion (oder über verschieben Konstruktion, wenn der r-Wert einer Xvalue ist).

## <a name="a-glvalue-has-identity-a-prvalue-does-not"></a>Ein Glvalue hat Identität; ein Prvalue nicht
Zu diesem Zeitpunkt wissen wir, welche Identität verfügt. Und wir wissen, was bewegliche ist und was nicht. Aber wir noch, nicht mit dem Namen der Serie von Werten diese *nicht* haben Identität. Dieser Satz wird als *Prvalue*oder *reinen r-Wert*bezeichnet.

```cppwinrt
int& get_by_ref() { ... }
int get_by_val() { ... }

int main()
{
    int* addr3{ &(get_by_ref() + 1) }; // Error: get_by_ref() + 1 is a prvalue.
    int* addr4{ &get_by_val() }; // Error: get_by_val() is a prvalue.
}
```

![Ein l-Wert hat Identität; ein Prvalue nicht](images/has-identity2.png)

## <a name="the-complete-picture-of-value-categories"></a>Vollständige Übersicht der Wertekategorien
Es bleibt nur um die Informationen und Illustrationen oben in einer einzelnen, großen Bild zu kombinieren.

![Vollständige Übersicht der Wertekategorien](images/value-categories.png)

### <a name="glvalue-i"></a>Glvalue (i)
Ein Glvalue (generalisierten l-Wert) hat Identität.

### <a name="lvalue-im"></a>l-Wert (I\ & \!m)
Ein l-Wert (eine Art von Glvalue) Identität hat, aber nicht verschiebbare. Hierbei handelt es sich um in der Regel Lese-/ Schreibzugriff-Werte, die Sie um als Verweis oder als const Verweis oder nach Wert übergeben, wenn das Kopieren von günstig ist. Ein l-Wert kann nicht zu einer Referenz r-Wert gebunden werden.

### <a name="xvalue-im"></a>xValue (I\ & m)
Ein Xvalue (eine Art von Glvalue, aber auch eine Art von r-Wert) über Identität und kann auch verschoben werden. Dies möglicherweise eine sammelte l-Wert, der Sie entschieden haben, zu verschieben, da das Kopieren aufwendig ist, und sehen Achten Sie nicht, darauf aufwenden zugreifen. Hier sehen Sie, wie Sie ein l-Wert in einer Xvalue aktivieren können.

```cppwinrt
struct A { ... };
A a; // a is an lvalue...
static_cast<A&&>(a); // ...but this expression is an xvalue.
```

Im obigen Codebeispiel noch nicht wir etwas noch verschoben. Wir haben eine Xvalue durch das Umwandeln einer l-Wert zu einem unbenannten r-Wert-Verweis erstellt. Sie können weiterhin mit seinem Namen l-Wert bezeichnet werden. aber als eine Xvalue, ist es jetzt *fähig* verschoben wird. Die Gründe dafür angeben, welche verschieben tatsächlich, aussieht, warten Sie nach einem anderen Thema haben. Aber Sie können sich das "X" in "Xvalue" als Bedeutung "Experte nur" Wenn Ihnen dabei hilft, vorstellen. Durch das Umwandeln einer l-Wert in einer Xvalue (eine Art von r-Wert), wird der Wert anschließend kann an einem Verweis r-Wert gebunden wird.

Hier sind zwei weitere Beispiele für Xvalues&mdash;Aufrufen einer Funktion, die einen Verweis unbenannten r-Wert zurückgibt, und den Zugriff auf ein Mitglied einer Xvalue.

```cppwinrt
struct A { int m; };
A&& f();
f(); // This expression is an xvalue...
f().m; // ...and so is this.
```

### <a name="prvalue-im"></a>Prvalue (\!i\ & m)
Ein Prvalue (reine r-Wert; eine Art von r-Wert) zwar nicht Identität, aber kann verschoben werden. Diese in der Regel gegebebenfalls sind, gibt das Ergebnis des Aufrufs einer Funktion, die nach Wert oder das Ergebnis der Überprüfung alle anderen Ausdrucks, der keine Glvalue ist,

### <a name="rvalue-m"></a>r-Wert (m)
Ein r-Wert kann verschoben werden. Ein r-Wert- *Verweis* bezieht sich immer um ein r-Wert (ein Wert, deren Inhalt davon ausgegangen wird, die wir nicht beibehalten müssen).

Ist jedoch ein r-Wert-Verweis selbst ein r-Wert? Eine *unbenannten* r-Wert-Referenz (z. B. den angezeigten obigen Codebeispiele Xvalue) ist ein Xvalue, Ja, es ist also ein r-Wert. Bevorzugte ein r-Wert-Funktion Referenzparameter, z. B. die eines Konstruktors verschieben gebunden sein. Im Gegensatz dazu (und vielleicht counter-intuitively), wenn eine Referenz r-Wert einen Namen hat, wird der Ausdruck, der mit diesem Namen besteht ein l-Wert. Daher es *kann nicht* auf ein Referenzparameter r-Wert gebunden werden. Aber es ist einfach, es dazu machen&mdash;einfach erneut zu einer unbenannten r-Wert-Referenz (ein Xvalue) umgewandelt.

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
Die Art der Wert, der keine Identität und ist nicht verschiebbare ist die eine Kombination aus, die wir noch nicht besprochen wurden. Aber wir können, da dieser Kategorie ist eine nützliche Idee in der C++-Sprache nicht ignorieren.

## <a name="reference-collapsing-rules"></a>Referenz zu reduzieren von Regeln
Mehrere wie z. B. Verweise in einem Ausdruck (ein Verweis auf l-Wert Verweis auf ein l-Wert oder ein r-Wert-Verweis auf eine Referenz r-Wert) beenden eine einen anderen Out.

- `A& &` in reduziert `A&`.
- `A&& &&` in reduziert `A&&`.

Im Gegensatz zu Verweise in einem Ausdruck mehrere reduzieren zu einer Referenz l-Wert.

- `A& &&` in reduziert `A&`.
- `A&& &` in reduziert `A&`.

## <a name="forwarding-references"></a>Weiterleitung Verweise
In diesem letzten Abschnitt gegenübergestellt r-Wert Verweise, die bereits, mit dem unterschiedliche Konzept von einem *Verweis weiterleiten*erläutert.

```cppwinrt
void foo(A&& a) { ... }
```

- `A&&` ist eine Referenz r-Wert an, wie wir gesehen haben. Const und volatile gelten nicht für Verweise r-Wert.
- `foo` akzeptiert nur Rvalues vom Typ **A**.
- Verweist auf den Grund r-Wert (z. B. `A&&`) vorhanden ist, damit Sie eine Überladung erstellen können, die für den Fall ein temporäres (oder andere r-Wert) übergeben wird optimiert ist.

```cppwinrt
template <typename _Ty> void bar(_Ty&& ty) { ... }
```

- `_Ty&&` ist eine *Referenz weiterleiten*. Je nachdem, was Sie zum übergeben `bar`, Typ **_Ty** Const/nicht konstanter unabhängig Volatile/nicht flüchtigen werden konnte.
- `bar` Alle l-Wert oder r-Wert der Typ **_Ty**akzeptiert.
- Übergeben ein l-Wert bewirkt, dass die Weiterleitung Verweis werden `_Ty& &&`, die reduziert auf den Verweis l-Wert `_Ty&`.
- Übergeben ein r-Wert bewirkt, dass die Weiterleitung Verweis werden `_Ty&& &&`, die reduziert auf den r-Wert-Verweis `_Ty&&`.
- Der Grund weiterleiten Verweise (z. B. `_Ty&&`) vorhanden sind, ist *nicht* für die Optimierung jedoch zu nutzen, was Sie an Sie übergeben und auf transparent und effizient weiterleiten. Sie werden wahrscheinlich eine Weiterleitung-Referenz auftritt, nur dann, wenn Sie Bibliothekscodes schreiben (oder genauerer Betrachtung)&mdash;z. B. eine Factory-Funktion, die auf Konstruktorargumente weiterleitet.

## <a name="sources"></a>Quellen
* \[Stroustrup, 2013\] b Stroustrup: die Programmiersprache C++, das vierte Edition. Addison-Wesley. 2013.
