---
description: Dieses Thema beschreibt die verschiedenen Kategorien von Werten, die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet l-Werte und Rvalues gehört haben, jedoch sind andere Arten zu.
title: Wertekategorien und Verweise auf diese
ms.date: 08/11/2018
ms.topic: article
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, verschieben, Weiterleitung, Wertekategorien, Verschiebungssemantik, perfekte Weiterleitung, l-Wert, r-Wert, Glvalue, Prvalue, Xvalue
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 1860f562233ceefa6d9ebb3741378b3265b4c3a9
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8874177"
---
# <a name="value-categories-and-references-to-them"></a>Wertekategorien und Verweise auf diese
Dieses Thema beschreibt die verschiedenen Kategorien der Werte (und Verweise auf Werte), die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet *l-Werte* und *Rvalues*gehört haben, aber möglicherweise nicht stellen sie in die Begriffe, die in diesem Thema werden. Und andere Arten von Werten, zu.

Jeder Ausdruck in C++ ergibt einen Wert, der auf eine der Kategorien, die in diesem Thema erläuterten gehört. Es gibt Aspekte der C++-Sprache, Facilies und Regeln, die das Verständnis der diese Wertekategorien und Verweise auf diese anfordern. Beispielsweise nehmen die Adresse eines Werts, der einen Wert kopieren, verschieben einen Wert und einen Wert an eine andere Funktion weiterleiten. In diesem Thema nicht in all diese Aspekte im Detail gehen, aber es enthält grundlegende Informationen für ein grundlegendes Verständnis davon.

Die Informationen in diesem Thema wird durch die zwei unabhängigen Eigenschaften der Identität und Movability [Stroustrup 2013] hinsichtlich Stroustrups Analyse der Wertekategorien dargestellt.

## <a name="an-lvalue-has-identity"></a>Ein l-Wert hat Identität
Was bedeutet es für einen Wert *Identität*? Wenn die Adresse des Arbeitsspeichers eines Werts Sie haben (oder können), und sie problemlos, und klicken Sie dann der Wert Identität verfügt. Auf diese Weise möglich mehr als vergleichen den Inhalt der Werte: Sie können vergleichen oder Identität zu unterscheiden.

Ein *l-Wert* hat Identität. Es ist jetzt eine Frage des nur rückwirkende Interesse an, dass die "l" in "l-Wert" Abkürzung für "Links" (in der linken Seite einer Zuordnung) ist. In C++ kann ein l-Wert in der nach links *oder* rechts auf der eine Zuordnung angezeigt. "L" in "l-Werte", können nicht dann tatsächlich Sie verstehen, oder definieren Sie. Sie müssen nur zu verstehen, was rufen wir ein l-Wert ein Wert ist, der Identität verfügt.

Beispiele für Ausdrücke, die l-Werte sind: einer benannten Variable oder Konstante; oder eine Funktion, die einen Verweis zurückgibt. Beispiele für Ausdrücke, die *nicht* l-Werte sind: ein temporäres; oder eine Funktion, die durch einen Wert zurückgibt.

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

Jetzt können zwar, l-Werte Identität haben Aussagen werden, also tun Xvalues. Gehen wir mehr in welche ein *Xvalue* weiter unten in diesem Thema wird. Für den Moment nur Beachten Sie, dass der Wert Kategorie Glvalue, für die "generalisiert l-Wert" vorhanden ist. Die Obermenge von Glvalues enthält l-Werte (auch bekannt als *klassische l-Werte*) und Xvalues. Daher while "Identität hat eine l-Wert" true ist, der vollständige Satz von Dinge, die Identität ist der Satz von Glvalues, wie in der folgenden Abbildung dargestellt.

![Ein l-Wert hat Identität](images/has-identity1.png)

## <a name="an-rvalue-is-movable-an-lvalue-is-not"></a>Ein r-Wert ist verschoben. ein l-Wert ist nicht
Aber es gibt Werte, die nicht Glvalues sind. Es gibt daher Werte, die Sie *kann nicht* für eine Speicheradresse erhalten (oder Sie können nicht verlassen Sie sich auf sie gültig). Wir haben gesehen, einige dieser Werte im obigen Codebeispiel. Dies klingt wie einen Nachteil. Aber in der Tat der Vorteil, einen Wert ist, können Sie *Verschieben* , wird (was in der Regel gering ist), anstatt kopieren wird (was in der Regel teuer ist). Verschieben von einem Wert bedeutet, dass es nicht mehr an der Stelle, die sie verwendet werden. Daher ist das Versuch, die sie an der Stelle zugreifen, die sie verwendet werden, die vermieden werden. Eine Erläuterung der wann und *wie* , ein Wert außerhalb des Bereichs für dieses Thema ist zu verschieben. Für dieses Thema müssen wir wissen, dass ein Wert, der bewegliche ist als ein *r-Wert* (oder *klassische r-Wert*) bezeichnet wird.

"R" in "r"-Wert ist eine Abkürzung für "rechts" (wie die rechte Seite einer Zuordnung). Sie können jedoch Rvalues und Verweise auf Rvalues, außerhalb von Aufgaben. In "Rvalues", "R" ist nicht das, was zu konzentrieren. Sie müssen nur zu verstehen, dass wir ein r-Wert aufrufen einen Wert, der bewegliche ist.

Ein l-Wert ist dagegen bewegliche, nicht, wie in der folgenden Abbildung dargestellt. Ein l-Wert, die verschoben würde die Definition von *l-Wert*gibt, und es wäre ein unerwarteter Fehler für Code, der erwartet sehr vernünftig weiterhin auf die l-Wert zugreifen können.

![Ein r-Wert ist verschoben. ein l-Wert ist nicht](images/is-movable.png)

Ein l-Wert kann nicht verschoben werden. Aber es *ist* eine Art von Glvalue (die Gruppe Dinge, die mit der Identität), die Sie verschieben können&mdash;, wenn Sie wissen, was Sie tun (einschließlich ohne dabei darauf zugreifen, nach dem Verschieben)&mdash;und die Xvalue ist. Wir werden diese Idee noch einmal unten, besuchen Sie Wenn wir die vollständiges Bild Wert Kategorien betrachten.

## <a name="rvalue-references-and-reference-binding-rules"></a>R-Wert Verweise und Referenz-Binding-Regeln
In diesem Abschnitt werden die Syntax für einen Verweis auf ein r-Wert. Wir müssen warten, bis ein anderes Thema, um einen erheblichen Behandlung von verschieben und weiterleiten zu starten, aber dies sind die Probleme, die durch r-Wert Verweise behoben werden. Bevor wir r-Wert Verweise betrachten, jedoch müssen wir zunächst über deutlicher zu erkennen, `T&` &mdash;das, was wir haben bisher wurden aufrufen einfach "einen Verweis". Es ist wirklich "ein l-Wert (nicht-Const) Verweis auf", der auf einen Wert bezieht sich auf die der Benutzer des Verweises schreiben kann.

```cppwinrt
template<typename T> T& get_by_lvalue_ref() { ... } // Get by lvalue (non-const) reference.
template<typename T> void set_by_lvalue_ref(T&) { ... } // Set by lvalue (non-const) reference.
```

Eine Referenz l-Wert kann ein l-Wert, aber nicht in ein r-Wert gebunden werden.

L-Wert const Verweise sind (`T const&`), die auf Objekte, die mit dem Schreiben von der Benutzer über die Referenz *kann nicht* (z. B. eine Konstante) verweisen.

```cppwinrt
template<typename T> T const& get_by_lvalue_cref() { ... } // Get by lvalue const reference.
template<typename T> void set_by_lvalue_cref(T const&) { ... } // Set by lvalue const reference.
```

Ein l-Wert-Verweis kann ein l-Wert oder ein r-Wert binden.

Die Syntax für einen Verweis auf ein r-Wert vom Typ `T` wird als geschrieben `T&&`. Ein r-Wert-Verweis bezieht sich auf bewegliche Wert&mdash;einen Wert, deren Inhalt müssen wir nicht beibehalten wird, nachdem wir sie (z. B. ein temporäres) verwendet haben. Seit der gesamte Punkt Verschieben von (wodurch ändern) der Wert gebunden ist, eine Referenz r-Wert `const` und `volatile` Qualifizierer (auch bekannt als cv-Qualifizierer) auf r-Wert gelten nicht.

```cppwinrt
template<typename T> T&& get_by_rvalue_ref() { ... } // Get by rvalue reference.
struct A { A(A&& other) { ... } }; // A move constructor takes an rvalue reference.
```

Ein r-Wert-Verweis Bindung an ein r-Wert. In der Tat hinsichtlich der Überladung Auflösung ein r-Wert *ist* ein Verweis auf r-Wert Verweis als auf ein const l-Wert gebunden werden. Aber eine Referenz r-Wert kann nicht an ein l-Wert binden, daran, wie bereits erwähnt haben, ein r-Wert-Verweis auf einen Wert, deren Inhalt bezieht sich davon, dass wir benötigen ausgegangen wird (beispielsweise der Parameter für einen) zu erhalten.

Sie können auch übergeben ein r-Wert, in denen ein Argument-Wert zu erwarten ist über Kopie erstellen (oder verschieben Konstruktion, die r-Wert ist eine Xvalue).

## <a name="a-glvalue-has-identity-a-prvalue-does-not"></a>Ein Glvalue hat Identität. eine Prvalue nicht
Zu diesem Zeitpunkt wissen wir, welche Identität verfügt. Und wir wissen, was bewegliche ist und was nicht. Aber wir noch, nicht mit dem Namen der Serie von Werten, *nicht* haben Identität. Dieser Satz wird als *Prvalue*oder *reinen r-Wert*bezeichnet.

```cppwinrt
int& get_by_ref() { ... }
int get_by_val() { ... }

int main()
{
    int* addr3{ &(get_by_ref() + 1) }; // Error: get_by_ref() + 1 is a prvalue.
    int* addr4{ &get_by_val() }; // Error: get_by_val() is a prvalue.
}
```

![Ein l-Wert hat Identität. eine Prvalue nicht](images/has-identity2.png)

## <a name="the-complete-picture-of-value-categories"></a>Vollständiges Bild Wert Kategorien
Es bleibt nur um die Informationen und Illustrationen oben in einer einzelnen, großen Bild zu kombinieren.

![Vollständiges Bild Wert Kategorien](images/value-categories.png)

### <a name="glvalue-i"></a>Glvalue (i)
Eine Glvalue (generalisierten l-Wert) hat Identität.

### <a name="lvalue-im"></a>l-Wert (I\ & \!m)
Ein l-Wert (eine Art von Glvalue) Identität hat, jedoch nicht verschoben. Hierbei handelt es sich um in der Regel Lese-/ Schreibzugriff-Werte, die Sie um Verweis oder-Verweis oder Wert übergeben, wenn das Kopieren von günstig ist. Ein l-Wert kann nicht zu einer Referenz r-Wert gebunden werden.

### <a name="xvalue-im"></a>xValue (I\ & m)
Ein Xvalue (eine Art von Glvalue, aber auch eine Art von r-Wert) über Identität und kann auch verschoben werden. Dies möglicherweise eine sammelte l-Wert, die Sie sich entschieden haben, zu verschieben, da kopieren aufwendig ist, und Sie werden nicht für den Zugriff darauf später achten. Hier sehen Sie, wie Sie ein l-Wert in einer Xvalue aktivieren können.

```cppwinrt
struct A { ... };
A a; // a is an lvalue...
static_cast<A&&>(a); // ...but this expression is an xvalue.
```

Im obigen Codebeispiel noch nicht wir etwas noch verschoben. Wir haben eine Xvalue durch das Umwandeln einer l-Wert zu einer unbenannten r-Wert-Referenz erstellt. Sie können weiterhin mit seinem Namen l-Wert bezeichnet werden. aber als eine Xvalue ist es jetzt *kann* verschoben wird. Der Grund dafür, und welche verschieben tatsächlich sieht wie, müssen Sie warten, bis ein anderes Thema. Aber Sie können sich das "X" in "Xvalue" als Bedeutung "Experte nur" Wenn Ihnen dabei hilft, vorstellen. Durch das Umwandeln einer l-Wert in einer Xvalue (eine Art von r-Wert), wird der Wert anschließend kann an einem Verweis r-Wert gebunden wird.

Hier sind zwei weitere Beispiele für Xvalues&mdash;Aufrufen einer Funktion, die eine Referenz unbenannten r-Wert zurückgibt, und den Zugriff auf ein Mitglied einer Xvalue.

```cppwinrt
struct A { int m; };
A&& f();
f(); // This expression is an xvalue...
f().m; // ...and so is this.
```

### <a name="prvalue-im"></a>Prvalue (\!i\ & m)
Eine Prvalue (reine r-Wert; eine Art von r-Wert) bewegliche ist jedoch nicht Identität haben. Diese in der Regel gegebebenfalls sind, gibt das Ergebnis des Aufrufs einer Funktion, die nach Wert oder das Ergebnis der Überprüfung alle anderen Ausdrucks, der keine Glvalue ist,

### <a name="rvalue-m"></a>r-Wert (m)
Ein r-Wert kann verschoben werden. Ein r-Wert- *Verweis* bezieht sich immer um ein r-Wert (ein Wert, deren Inhalt davon ausgegangen wird, die wir nicht beibehalten müssen).

Aber ein r-Wert-Verweis selbst ein r-Wert ist? Eine *unbenannten* r-Wert-Referenz (z. B. den angezeigten obigen Codebeispiele Xvalue) ist eine Xvalue, Ja, es ist also ein r-Wert. Es ist ein r-Wert-Funktion Referenzparameter, z. B. der einen gebunden werden. Im Gegensatz dazu (und möglicherweise counter-intuitively), wenn eine Referenz r-Wert einen Namen hat, wird der Ausdruck, der mit diesem Namen besteht ein l-Wert. Daher es *kann nicht* auf ein Referenzparameter r-Wert gebunden werden. Aber es ist einfach, es dazu machen&mdash;einfach erneut in einem Verweis unbenannten r-Wert (eine Xvalue) umgewandelt.

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
Die Art der Wert, der keine Identität und ist nicht verschiebbare ist, die eine Kombination aus, der wir noch nicht erläutert noch nicht. Aber wir können, da dieser Kategorie ist hilfreich, sich in der C++-Sprache nicht ignorieren.

## <a name="reference-collapsing-rules"></a>Das Reduzieren der Referenz-Regeln
Mehrere wie z. B. Verweise in einem Ausdruck (ein l-Wert-Verweis auf eine Referenz l-Wert oder ein r-Wert-Verweis auf eine Referenz r-Wert) beenden eine eine andere Out.

- `A& &` in reduziert `A&`.
- `A&& &&` in reduziert `A&&`.

Mehrere im Gegensatz zu Verweise in einem Ausdruck zu einer Referenz l-Wert reduzieren.

- `A& &&` in reduziert `A&`.
- `A&& &` in reduziert `A&`.

## <a name="forwarding-references"></a>Weiterleitung Verweise
In diesem letzten Abschnitt gegenübergestellt r-Wert-Verweise, die wir bereits, mit dem anderen Konzept eine *Referenz weiterleiten erwähnt wurden*.

```cppwinrt
void foo(A&& a) { ... }
```

- `A&&` ist eine Referenz r-Wert, wie wir gesehen haben. Const und volatile gelten nicht für Verweise r-Wert.
- `foo` akzeptiert nur Rvalues vom Typ **ein**.
- Der Grund r-Wert verweist (z. B. `A&&`) vorhanden ist, damit Sie eine Überladung erstellen können, die für den Fall, in eine temporäre (oder andere r-Wert) übergeben wird optimiert ist.

```cppwinrt
template <typename _Ty> void bar(_Ty&& ty) { ... }
```

- `_Ty&&` ist eine *Referenz weiterleiten*. Je nachdem, was Sie zum übergeben `bar`, Typ **_Ty** Const/nicht konstanter unabhängig von Volatile/nicht flüchtigen werden konnte.
- `bar` akzeptiert l-Wert oder der Typ **_Ty**r-Wert.
- Übergeben ein l-Wert bewirkt, dass die Weiterleitung Verweis werden `_Ty& &&`, die an der l-Wert zu reduziert `_Ty&`.
- Übergeben ein r-Wert bewirkt, dass die Weiterleitung Verweis werden `_Ty&& &&`, die an der r-Wert zu reduziert `_Ty&&`.
- Der Grund weiterleiten Verweise (z. B. `_Ty&&`) vorhanden sind, ist *nicht* für die Optimierung, jedoch wird, was Sie an Sie übergeben und auf transparent und effizient weiterleiten. Sie werden wahrscheinlich eine Weiterleitung-Referenz auftritt, nur dann, wenn Sie Bibliothekscode schreiben (oder genauerer Betrachtung)&mdash;z. B. eine Factory-Funktion, die auf Konstruktorargumente weiterleitet.

## <a name="sources"></a>Quellen
* \[Stroustrup, 2013\] b Stroustrup: die C++-Programmiersprache, die vierte Edition. Addison-Wesley. 2013.
