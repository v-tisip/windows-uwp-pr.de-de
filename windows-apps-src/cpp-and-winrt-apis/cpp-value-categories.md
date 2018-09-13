---
author: stevewhims
description: Dieses Thema beschreibt die verschiedenen Kategorien von Werten, die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet l-Werte und Rvalues gehört haben, jedoch sind andere Arten zu.
title: Wert Kategorien und Verweise auf diese
ms.author: stwhi
ms.date: 08/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, verschieben, Weiterleitung, Wert Kategorien, Move-Semantik, perfekte Weiterleitung, l-Wert, r-Wert, Glvalue, Prvalue, Xvalue
ms.localizationpriority: medium
ms.openlocfilehash: cbccaf78b45d85d93619977d149431c4eec9e10a
ms.sourcegitcommit: c8f6866100a4b38fdda8394ea185b02d7af66411
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "3962972"
---
# <a name="value-categories-and-references-to-them"></a>Wert Kategorien und Verweise auf diese
Dieses Thema beschreibt die verschiedenen Kategorien der Werte (und Verweise auf Werte), die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet *l-Werte* und *Rvalues*gehört haben, aber möglicherweise nicht stellen sie in die Begriffe, die in diesem Thema wird vorgestellt. Und andere Arten von Werten, es zu werden.

Jeder Ausdruck in C++ ergibt einen Wert, der eine der Kategorien, die in diesem Thema erläuterten gehört. Es gibt Aspekte der Programmiersprache C++, Facilies sowie Regeln festgelegt, die Verständnis dieser Wert Kategorien und Verweise auf diese anfordern. Beispielsweise nehmen die Adresse eines Werts, einen Wert kopieren, verschieben einen Wert und einen Wert an eine andere Funktion weiterleiten. In diesem Thema nicht in all diese Aspekte im Detail gehen, aber es enthält grundlegende Informationen für ein grundlegendes Verständnis davon.

Die Informationen in diesem Thema wird durch die zwei unabhängigen Eigenschaften der Identität und Movability [Stroustrup 2013] hinsichtlich des Stroustrups Analyse der Wert Kategorien dargestellt.

## <a name="an-lvalue-has-identity"></a>Ein l-Wert hat Identität
Was bedeutet es für einen Wert *Identität*? Wenn die Adresse des Arbeitsspeichers eines Werts Sie haben (oder geschaltet werden können), und sie sicher, und klicken Sie dann der Wert Identität verfügt. Auf diese Weise möglich mehr als vergleichen den Inhalt der Werte: Sie können vergleichen oder Identität zu unterscheiden.

Ein *l-Wert* hat Identität. Es ist jetzt eine Frage nur rückwirkende Orte, dass das "l" in "l-Wert" Abkürzung für "Links" (wie der linken Seite einer Zuweisung) ist. In C++ kann ein l-Wert auf der linken *oder* auf der rechten Seite einer Zuordnung angezeigt werden. Das "l" in "l-Werte", unterstützen nicht dann, tatsächlich Sie bei verstehen noch definieren, was sind. Sie müssen nur zu verstehen, was rufen wir l-ein Wert ein Wert ist, der Identität verfügt.

Beispiele für Ausdrücke, die l-Werte sind: eine benannten Variable oder Konstante; oder eine Funktion, die einen Verweis zurückgibt. Beispiele für Ausdrücke, die *nicht* l-Werte sind: ein temporäres; oder eine Funktion, die durch einen Wert zurückgibt.

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

Nun, während sie Aussagen, l-Werte Identität haben befindet, also tun Xvalues. Gehen wir mehr in welche ein *Xvalue* weiter unten in diesem Thema wird. Für den Moment einfach Beachten Sie, dass der Wert Kategorie Glvalue, für die "generalisiert l-Wert" vorhanden ist. Die Übermenge von Glvalues enthält l-Werte (auch bekannt als *klassische l-Werte*) und Xvalues. Daher while "Identität hat ein l-Wert" ist "true", der vollständige Satz von Dinge, die Identität der Satz von Glvalues, wie in der folgenden Abbildung dargestellt.

![Ein l-Wert hat Identität](images/has-identity1.png)

## <a name="an-rvalue-is-movable-an-lvalue-is-not"></a>Ein r-Wert ist bewegliche. ein l-Wert ist nicht
Aber es gibt Werte, die nicht Glvalues sind. Es gibt daher Werte, die Sie *kann nicht* für eine Speicheradresse zu erhalten (oder nicht verlässlich er gültig sein). Wir konnten uns einige dieser Werte im obigen Codebeispiel. Dies klingt wie einen Nachteil. Aber in der Tat können den Vorteil, einen Wert wie das heißt, dass Sie daraus *Verschieben* können (was in der Regel gering ist), statt kopieren (was in der Regel teuer ist). Verschieben von einem Wert bedeutet, dass es nicht mehr an der Stelle, die verwendet werden. Daher ist das versuchen, an der Stelle auf Sie zugreifen, die verwendet werden, die vermieden werden. Eine Erläuterung der wann und *wie* , ein Wert nicht zum Umfang dieses Thema ist zu verschieben. Für dieses Thema müssen wir wissen, dass ein Wert, der bewegliche ist als ein *r-Wert* (oder *klassische r-Wert*) bezeichnet wird.

Das "R" in "r"-Wert ist eine Abkürzung des "rechts", (wie, die rechte Seite einer Zuweisung). Sie können jedoch Rvalues und Verweise auf Rvalues, außerhalb von Aufgaben. In "Rvalues", "R" ist, nicht das, was zu konzentrieren. Sie müssen nur zu verstehen, dass was rufen wir ein r-Wert einen Wert, der bewegliche ist.

Ein l-Wert ist dagegen bewegliche, nicht, wie in der folgenden Abbildung dargestellt. Ein l-Wert, die verschoben würde die Definition von *l-Wert*gibt, und es wäre ein unerwarteter Fehler für Code, der erwartet sehr vernünftig weiterhin auf die l-Wert zugreifen können.

![Ein r-Wert ist bewegliche. ein l-Wert ist nicht](images/is-movable.png)

Ein l-Wert kann nicht verschoben werden. Aber es *ist* eine Art von Glvalue (die Gruppe Dinge, die mit der Identität), die Sie verschieben können&mdash;Wenn Sie wissen, was Sie tun (einschließlich ohne dabei darauf zugreifen, nach dem Verschieben)&mdash;und das ist der Xvalue. Wir werden diese Idee noch einmal unten, besuchen Sie Wenn wir uns das vollständige Bild Wert Kategorien nun an.

## <a name="rvalue-references-and-reference-binding-rules"></a>R-Wert Verweise und Referenz-Binding-Regeln
In diesem Abschnitt werden die Syntax für einen Verweis auf ein r-Wert. Wir müssen warten, bis ein anderes Thema das Aufrufen einer erheblichen Behandlung verschieben und weiterleiten, allerdings sind Probleme, die durch r-Wert Verweise behoben werden. Bevor wir r-Wert Verweise betrachten, jedoch müssen wir zunächst über klarer werden `T&` &mdash;das, was wir haben bisher wurden aufrufen einfach "einen Verweis". Es ist wirklich "ein l-Wert (non-Const) Verweis auf", der auf einen Wert bezieht sich auf die der Benutzer des Verweises schreiben kann.

```cppwinrt
template<typename T> T& get_by_lvalue_ref() { ... } // Get by lvalue (non-const) reference.
template<typename T> void set_by_lvalue_ref(T&) { ... } // Set by lvalue (non-const) reference.
```

Ein l-Wert-Verweis kann ein l-Wert, aber nicht in ein r-Wert binden.

L-Wert Konstante Verweise sind (`T const&`), die auf Objekte, die in das Schreiben der Benutzer *kann nicht* Referenz (z. B. eine Konstante) verweisen.

```cppwinrt
template<typename T> T const& get_by_lvalue_cref() { ... } // Get by lvalue const reference.
template<typename T> void set_by_lvalue_cref(T const&) { ... } // Set by lvalue const reference.
```

Ein l-Wert-Verweis kann an ein l-Wert oder ein r-Wert binden.

Die Syntax für einen Verweis auf ein r-Wert vom Typ `T` als geschrieben `T&&`. Ein r-Wert-Verweis bezieht sich auf einen verschiebbare Wert&mdash;einen Wert, deren Inhalt müssen wir nicht beibehalten, nachdem wir es (z. B. ein temporäres) verwendet haben. Seit dem gesamten Punkt Wechsels vom (wodurch ändern) der Wert gebunden ist, einen Verweis r-Wert `const` und `volatile` Qualifizierer (auch bekannt als cv-Qualifizierer) gelten nicht für Verweise r-Wert.

```cppwinrt
template<typename T> T&& get_by_rvalue_ref() { ... } // Get by rvalue reference.
struct A { A(A&& other) { ... } }; // A move constructor takes an rvalue reference.
```

Ein r-Wert-Verweis Bindung an ein r-Wert. In der Tat Bezug auf die Überladung Auflösung ein r-Wert *bevorzugt* ein Verweis auf r-Wert Verweis als auf ein const l-Wert gebunden werden. Aber ein Verweis r-Wert kann nicht an ein l-Wert binden, da wie gesagt haben, ein r-Wert-Verweis auf einen Wert, deren Inhalt bezieht sich davon, dass wir benötigen ausgegangen wird (beispielsweise der Parameter für einen Verschiebungskonstruktor) zu erhalten.

Sie können auch übergeben ein r-Wert, in denen ein Argument als Wert zu erwarten ist über Kopie Konstruktion (oder verschieben Konstruktion, wenn der r-Wert ein Xvalue ist).

## <a name="a-glvalue-has-identity-a-prvalue-does-not"></a>Eine Glvalue hat Identität; eine Prvalue nicht
In dieser Phase wissen wir, was Identität verfügt. Und wir wissen, was bewegliche ist und was nicht. Aber wir noch, nicht mit dem Namen der Serie von Werten, *nicht* haben Identität. Satz als *Prvalue*oder *reine r-Wert*bekannt ist.

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
Ein l-Wert (eine Art von Glvalue) Identität hat, aber nicht verschoben. Hierbei handelt es sich um in der Regel Lese-/ Schreibzugriff-Werte, die Sie um Verweis oder-Verweis oder Wert übergeben, wenn das Kopieren von günstig ist. Ein l-Wert kann nicht zu einer Referenz r-Wert gebunden werden.

### <a name="xvalue-im"></a>xValue (I\ & m)
Ein Xvalue (eine Art von Glvalue, aber auch eine Art von r-Wert) Identität hat, und kann auch verschoben werden. Möglicherweise ein sammelte l-Wert, die Sie entschieden haben, zu verschieben, da kopieren aufwendig ist, und Sie werden Achten Sie darauf später zugreifen. Hier sehen Sie, wie Sie ein l-Wert in einer Xvalue aktivieren können.

```cppwinrt
struct A { ... };
A a; // a is an lvalue...
static_cast<A&&>(a); // ...but this expression is an xvalue.
```

Im obigen Codebeispiel noch nicht wir etwas noch verschoben. Wir haben eine Xvalue durch Umwandeln einer l-Wert zu einer unbenannten r-Wert-Referenz erstellt. Sie können weiterhin anhand des l-Wert namens identifiziert werden; aber als ein Xvalue ist es jetzt *fähig* verschoben wird. Der Grund dafür, und welche verschieben tatsächlich, aussieht müssen warten, bis ein anderes Thema. Aber Sie können sich das "X" in "Xvalue" als Bedeutung "Experte nur" Wenn Ihnen dabei hilft, vorstellen. Durch das Umwandeln einer l-Wert in einer Xvalue (eine Art von r-Wert), wird der Wert anschließend kann zu einer Referenz r-Wert gebunden wird.

Hier sind zwei weitere Beispiele für Xvalues&mdash;Aufrufen einer Funktion, die einen Verweis unbenannten r-Wert zurückgibt, und den Zugriff auf ein Mitglied einer Xvalue.

```cppwinrt
struct A { int m; };
A&& f();
f(); // This expression is an xvalue...
f().m; // ...and so is this.
```

### <a name="prvalue-im"></a>Prvalue (\!i\ & m)
Eine Prvalue (reine r-Wert; eine Art von r-Wert) nicht Identität, aber kann verschoben werden. Diese in der Regel gegebebenfalls sind, gibt das Ergebnis des Aufrufs einer Funktion, die nach Wert oder das Ergebnis der Auswertung eines anderen Ausdrucks, der keine Glvalue ist,

### <a name="rvalue-m"></a>r-Wert (m)
Ein r-Wert kann verschoben werden. Ein r-Wert- *Verweis* bezieht sich immer um ein r-Wert (ein Wert, deren Inhalt davon ausgegangen wird, die wir nicht beibehalten müssen).

Ist jedoch ein r-Wert-Verweis selbst ein r-Wert? Eine *unbenannten* r-Wert-Referenz (z. B. den angezeigten obigen Codebeispiele Xvalue) ist ein Xvalue, Ja, es ist also ein r-Wert. Bevorzugte ein r-Wert-Funktion Referenzparameter, z. B., eines Konstruktors verschieben gebunden werden. Im Gegensatz dazu (und möglicherweise counter-intuitively), wenn ein Verweis r-Wert einen Namen hat, wird des Ausdrucks, der mit diesem Namen besteht ein l-Wert. Daher es *kann nicht* auf ein Referenzparameter r-Wert gebunden werden. Aber es ist einfach zu vereinfachen dazu&mdash;einfach erneut zu einer unbenannten r-Wert-Referenz (ein Xvalue) umgewandelt.

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
Die Art der Wert, der keine Identität und ist nicht verschiebbare ist, die eine Kombination aus, der bisher noch erwähnt noch nicht. Aber wir können, da dieser Kategorie ist hilfreich, sich in der C++-Sprache nicht ignorieren.

## <a name="reference-collapsing-rules"></a>Referenz zu reduzieren von Regeln
Mehrere wie z. B. Verweise in einem Ausdruck (ein Verweis auf l-Wert Verweis auf ein l-Wert oder ein r-Wert-Verweis auf einen Verweis r-Wert) beenden eine eine andere Out.

- `A& &` in reduziert `A&`.
- `A&& &&` in reduziert `A&&`.

Mehrere im Gegensatz zu Verweise in einem Ausdruck zu einer Referenz l-Wert reduzieren.

- `A& &&` in reduziert `A&`.
- `A&& &` in reduziert `A&`.

## <a name="forwarding-references"></a>Weiterleitung Verweise
In diesem letzten Abschnitt gegenübergestellt r-Wert Verweise auf, die wir bereits, mit dem anderen Konzept eine *Weiterleitung Referenz erwähnt wurden*.

```cppwinrt
void foo(A&& a) { ... }
```

- `A&&` ist ein Verweis r-Wert an, wie wir gesehen haben. Const und volatile gelten nicht für Verweise r-Wert.
- `foo` akzeptiert nur Rvalues vom Typ **A**.
- Verweist auf den Grund r-Wert (z. B. `A&&`) vorhanden ist, damit Sie eine Überladung erstellen können, die für den Fall ein temporäres (oder andere r-Wert) übergebenen optimiert ist.

```cppwinrt
template <typename _Ty> void bar(_Ty&& ty) { ... }
```

- `_Ty&&` ist eine *Weiterleitung Referenz*. Je nachdem, was Sie übergeben `bar`, Typ **_Ty** Const/nicht konstanter unabhängig von Volatile/nicht flüchtigen werden konnte.
- `bar` Alle l-Wert oder r-Wert der Typ **_Ty**akzeptiert.
- Übergeben ein l-Wert führt dazu, dass die Weiterleitung Referenz zu `_Ty& &&`, die an der l-Wert zu reduziert `_Ty&`.
- Übergeben ein r-Wert wird die Weiterleitung Referenz zu werden `_Ty&& &&`, die an der r-Wert zu reduziert `_Ty&&`.
- Der Grund weiterleiten Verweise (z. B. `_Ty&&`) vorhanden ist *nicht* für die Optimierung, jedoch wird, was Sie an Sie übergeben und auf transparent und effizient weiterleiten. Sie werden wahrscheinlich einen Verweis Weiterleitung auftreten, nur dann, wenn Sie Bibliothekscodes schreiben (oder genauerer Betrachtung)&mdash;z. B. eine Factory-Funktion, die auf Konstruktorargumente weiterleitet.

## <a name="sources"></a>Quellen
* \[Stroustrup, 2013\] b Stroustrup: die C++-Programmiersprache, die vierte Edition. Addison-Wesley. 2013.
