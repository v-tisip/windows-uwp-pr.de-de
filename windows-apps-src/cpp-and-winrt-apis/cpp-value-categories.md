---
author: stevewhims
description: Dieses Thema beschreibt die verschiedenen Kategorien von Werten, die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet kenne l-Werte und Rvalues, jedoch sind andere Arten zu.
title: Wertekategorien und Verweise auf diese
ms.author: stwhi
ms.date: 08/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, verschieben, Weiterleitung, Wertekategorien, Move-Semantik, perfekte Weiterleitung, l-Wert, r-Wert, Glvalue, Prvalue, Xvalue
ms.localizationpriority: medium
ms.openlocfilehash: cbccaf78b45d85d93619977d149431c4eec9e10a
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5165229"
---
# <a name="value-categories-and-references-to-them"></a><span data-ttu-id="7f859-105">Wertekategorien und Verweise auf diese</span><span class="sxs-lookup"><span data-stu-id="7f859-105">Value categories, and references to them</span></span>
<span data-ttu-id="7f859-106">Dieses Thema beschreibt die verschiedenen Kategorien von Werten (und Verweise auf Werte), die in C++ vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="7f859-106">This topic describes the various categories of values (and references to values) that exist in C++.</span></span> <span data-ttu-id="7f859-107">Sie werden Ausrichtungsattributs verwendet kenne *l-Werte* und *Rvalues*, aber Sie können nicht von ihnen vorstellen, in die Begriffe, die in diesem Thema wird vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="7f859-107">You will doubtless have heard of *lvalues* and *rvalues*, but you may not think of them in the terms that this topic presents.</span></span> <span data-ttu-id="7f859-108">Und es gibt andere Arten von Werten, zu.</span><span class="sxs-lookup"><span data-stu-id="7f859-108">And there are other kinds of values, too.</span></span>

<span data-ttu-id="7f859-109">Jeder Ausdruck in C++ ergibt einen Wert, der auf eine der in diesem Thema erläuterten Kategorien gehört.</span><span class="sxs-lookup"><span data-stu-id="7f859-109">Every expression in C++ yields a value that belongs to one of the categories discussed in this topic.</span></span> <span data-ttu-id="7f859-110">Es gibt Aspekte der Programmiersprache C++, dessen Facilies und Regeln, die das Verständnis der diese Wertekategorien und Verweise auf diese anfordern.</span><span class="sxs-lookup"><span data-stu-id="7f859-110">There are aspects of the C++ language, its facilies, and rules, that demand a proper understanding of these value categories, and references to them.</span></span> <span data-ttu-id="7f859-111">Die Adresse eines Werts, einen Wert kopieren, verschieben einen Wert und einen Wert an eine andere Funktion Weiterleiten z. B. nehmen.</span><span class="sxs-lookup"><span data-stu-id="7f859-111">For example, taking the address of a value, copying a value, moving a value, and forwarding a value on to another function.</span></span> <span data-ttu-id="7f859-112">In diesem Thema nicht in all diese Aspekte im Detail gehen, aber es enthält grundlegende Informationen für ein grundlegendes Verständnis davon.</span><span class="sxs-lookup"><span data-stu-id="7f859-112">This topic doesn't go into all of those aspects in depth, but it provides foundational information for a solid understanding of them.</span></span>

<span data-ttu-id="7f859-113">Die Informationen in diesem Thema wird durch die zwei unabhängigen Eigenschaften Identitätsnachweis und Movability [Stroustrup 2013] hinsichtlich des Stroustrups Analyse der Wertekategorien dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7f859-113">The info in this topic is framed in terms of Stroustrup's analysis of value categories by the two independent properties of identity and movability [Stroustrup, 2013].</span></span>

## <a name="an-lvalue-has-identity"></a><span data-ttu-id="7f859-114">Einem l-Wert besitzt Identität</span><span class="sxs-lookup"><span data-stu-id="7f859-114">An lvalue has identity</span></span>
<span data-ttu-id="7f859-115">Was bedeutet es für einen Wert *Identität*?</span><span class="sxs-lookup"><span data-stu-id="7f859-115">What does it mean for a value to have *identity*?</span></span> <span data-ttu-id="7f859-116">Wenn die Adresse des Arbeitsspeichers eines Werts Sie haben (oder geschaltet werden können), und sie sicher, und klicken Sie dann der Wert Identität verfügt.</span><span class="sxs-lookup"><span data-stu-id="7f859-116">If you have (or you can take) the memory address of a value and use it safely, then the value has identity.</span></span> <span data-ttu-id="7f859-117">Auf diese Weise können Sie erreichen mehr als vergleichen den Inhalt der Werte: Sie können vergleichen oder Identität zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="7f859-117">That way, you can do more than compare the contents of values: you can compare or distinguish them by identity.</span></span>

<span data-ttu-id="7f859-118">Einem *l-Wert* hat Identität.</span><span class="sxs-lookup"><span data-stu-id="7f859-118">An *lvalue* has identity.</span></span> <span data-ttu-id="7f859-119">Es ist jetzt eine Frage des nur rückwirkende Interesse an, dass das "l" in "l-Wert" Abkürzung für "Links" (wie, in der linken Seite einer Zuordnung) ist.</span><span class="sxs-lookup"><span data-stu-id="7f859-119">It's now a matter of only historical interest that the "l" in "lvalue" is an abbreviation of "left" (as in, the left-hand-side of an assignment).</span></span> <span data-ttu-id="7f859-120">In C++ kann einem l-Wert auf den nach links *oder* rechts auf der eine Zuordnung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7f859-120">In C++, an lvalue can appear on the left *or* on the right of an assignment.</span></span> <span data-ttu-id="7f859-121">Das "l" in "l-Werte", unterstützen nicht dann, tatsächlich Sie bei der verstehen noch definieren, was sind.</span><span class="sxs-lookup"><span data-stu-id="7f859-121">The "l" in "lvalues", then, doesn't actually help you to comprehend nor define what they are.</span></span> <span data-ttu-id="7f859-122">Sie müssen nur zu verstehen, was rufen wir einem l-Wert ein Wert ist, der Identität verfügt.</span><span class="sxs-lookup"><span data-stu-id="7f859-122">You need only to understand that what we call an lvalue is a value that has identity.</span></span>

<span data-ttu-id="7f859-123">Beispiele für Ausdrücke, die l-Werte sind: einer benannten Variable oder Konstante; oder eine Funktion, die einen Verweis zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="7f859-123">Examples of expressions that are lvalues include: a named variable or constant; or a function that returns a reference.</span></span> <span data-ttu-id="7f859-124">Beispiele für Ausdrücke, die *nicht* l-Werte sind: ein temporäres; oder eine Funktion, die durch einen Wert zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="7f859-124">Examples of expressions that are *not* lvalues include: a temporary; or a function that returns by value.</span></span>

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

<span data-ttu-id="7f859-125">Nun, während es eine Anweisung "true" ist, dass l-Werte Identität, also tun Xvalues.</span><span class="sxs-lookup"><span data-stu-id="7f859-125">Now, while it's a true statement that lvalues have identity, so do xvalues.</span></span> <span data-ttu-id="7f859-126">Gehen wir mehr in welchen einer *Xvalue* weiter unten in diesem Thema wird.</span><span class="sxs-lookup"><span data-stu-id="7f859-126">We'll go more into what an *xvalue* is later in this topic.</span></span> <span data-ttu-id="7f859-127">Seien Sie für den Moment Beachten Sie, dass der Wert Kategorie Glvalue, für die "generalisiert l-Wert".</span><span class="sxs-lookup"><span data-stu-id="7f859-127">For now, just be aware that there is a value category called glvalue, for "generalized lvalue".</span></span> <span data-ttu-id="7f859-128">Die Übermenge von Glvalues enthält l-Werte (auch bekannt als *klassische l-Werte*) und Xvalues.</span><span class="sxs-lookup"><span data-stu-id="7f859-128">The superset of glvalues contains both lvalues (also known as *classical lvalues*) and xvalues.</span></span> <span data-ttu-id="7f859-129">Ja, während er sich "einem l-Wert besitzt Identität" ist "true", der vollständige Satz von Dinge, die Identität der Satz von Glvalues, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7f859-129">So, while "an lvalue has identity" is true, the complete set of things that have identity is the set of glvalues, as shown in this illustration.</span></span>

![Einem l-Wert besitzt Identität](images/has-identity1.png)

## <a name="an-rvalue-is-movable-an-lvalue-is-not"></a><span data-ttu-id="7f859-131">Ein r-Wert ist bewegliche. einem l-Wert ist nicht</span><span class="sxs-lookup"><span data-stu-id="7f859-131">An rvalue is movable; an lvalue is not</span></span>
<span data-ttu-id="7f859-132">Aber es gibt Werte, die nicht Glvalues sind.</span><span class="sxs-lookup"><span data-stu-id="7f859-132">But there are values that are not glvalues.</span></span> <span data-ttu-id="7f859-133">Daher sind Werte, die Sie *kann nicht* zu eine Speicheradresse für erhalten (oder Sie können nicht verlassen Sie sich auf er gültig sein).</span><span class="sxs-lookup"><span data-stu-id="7f859-133">Consequently, there are values that you *can't* obtain a memory address for (or you can't rely on it to be valid).</span></span> <span data-ttu-id="7f859-134">Wir haben gesehen, einige dieser Werte im obigen Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="7f859-134">We saw some such values in the code example above.</span></span> <span data-ttu-id="7f859-135">Dies klingt wie einen Nachteil.</span><span class="sxs-lookup"><span data-stu-id="7f859-135">This sounds like a disadvantage.</span></span> <span data-ttu-id="7f859-136">Aber in der Tat können den Vorteil, einen Wert wie das heißt, dass Sie daraus *Verschieben* können (was in der Regel günstig ist), anstatt Kopieren von ihm (was in der Regel teuer ist).</span><span class="sxs-lookup"><span data-stu-id="7f859-136">But in fact the advantage of a value like that is that you can *move* from it (which is generally cheap), rather than copy from it (which is generally expensive).</span></span> <span data-ttu-id="7f859-137">Wechsel von einem Wert bedeutet, dass diese nicht mehr an der Stelle wird, verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-137">Moving from a value means that it's no longer in the place it used to be.</span></span> <span data-ttu-id="7f859-138">Ist es an der Stelle zugreifen, die es verwendet, um werden möchte etwas vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-138">So, trying to access it in the place it used to be is something to be avoided.</span></span> <span data-ttu-id="7f859-139">Eine Erläuterung der wann und *wie* , ein Wert außerhalb des Bereichs für dieses Thema ist zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="7f859-139">A discussion of when and *how* to move a value is out of scope for this topic.</span></span> <span data-ttu-id="7f859-140">In diesem Thema benötigen wir lediglich wissen, dass ein Wert, der bewegliche ist als ein *r-Wert* (oder *klassische r-Wert*) bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="7f859-140">For this topic, we just need to know that a value that is movable is known as an *rvalue* (or *classical rvalue*).</span></span>

<span data-ttu-id="7f859-141">Die "R" in "r"-Wert ist eine Abkürzung des "rechts" (wie, die rechte Seite einer Zuordnung).</span><span class="sxs-lookup"><span data-stu-id="7f859-141">The "r" in "rvalue" is an abbreviation of "right" (as in, the right-hand-side of an assignment).</span></span> <span data-ttu-id="7f859-142">Sie können jedoch Rvalues und Verweise auf Rvalues außerhalb von Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="7f859-142">But you can use rvalues, and references to rvalues, outside of assignments.</span></span> <span data-ttu-id="7f859-143">Die "R" in "Rvalues" ist, nicht das, was zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="7f859-143">The "r" in "rvalues", then, is not the thing to focus on.</span></span> <span data-ttu-id="7f859-144">Sie müssen nur zu verstehen, dass was rufen wir ein r-Wert einen Wert, der bewegliche ist.</span><span class="sxs-lookup"><span data-stu-id="7f859-144">You need only to understand that what we call an rvalue is a value that is movable.</span></span>

<span data-ttu-id="7f859-145">Einem l-Wert ist dagegen bewegliche, nicht, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7f859-145">An lvalue, conversely, isn't movable, as shown in this illustration.</span></span> <span data-ttu-id="7f859-146">Einem l-Wert, die verschoben würde die Definition von *l-Wert*gibt, und es wäre ein unerwarteter Fehler für Code, der erwartet sehr vernünftig weiterhin auf die l-Wert zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="7f859-146">An lvalue that moved would defy the definition of *lvalue*, and it would be an unexpected problem for code that very reasonably expected to be able to continue to access the lvalue.</span></span>

![Ein r-Wert ist bewegliche. einem l-Wert ist nicht](images/is-movable.png)

<span data-ttu-id="7f859-148">Sie können keinem l-Wert verschieben.</span><span class="sxs-lookup"><span data-stu-id="7f859-148">You can't move an lvalue.</span></span> <span data-ttu-id="7f859-149">Aber es *ist* eine Art von Glvalue (Set Dinge, die mit der Identität), die Sie verschieben können&mdash;Wenn Sie wissen, was Sie tun (einschließlich Achten Sie nicht für den Zugriff darauf nach dem Verschieben)&mdash;und das ist der Xvalue.</span><span class="sxs-lookup"><span data-stu-id="7f859-149">But there *is* a kind of glvalue (the set of things with identity) that you can move&mdash;if you know what you're doing (including being careful not to access it after the move)&mdash;and that's the xvalue.</span></span> <span data-ttu-id="7f859-150">Wir werden diese Idee noch einmal unten, besuchen Sie Wenn wir uns das vollständige Bild des Wertekategorien nun an.</span><span class="sxs-lookup"><span data-stu-id="7f859-150">We'll revisit this idea one more time below, when we look at the complete picture of value categories.</span></span>

## <a name="rvalue-references-and-reference-binding-rules"></a><span data-ttu-id="7f859-151">R-Wert Verweise und Referenz-Bindungsregeln</span><span class="sxs-lookup"><span data-stu-id="7f859-151">Rvalue references, and reference-binding rules</span></span>
<span data-ttu-id="7f859-152">In diesem Abschnitt werden die Syntax für einen Verweis auf ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="7f859-152">This section introduces the syntax for a reference to an rvalue.</span></span> <span data-ttu-id="7f859-153">Wir müssen warten, bis ein anderes Thema in einen erheblichen Behandlung verschieben und Weiterleiten gehen, allerdings sind Probleme, die durch r-Wert Verweise behoben werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-153">We'll have to wait for another topic to go into a substantial treatment of moving and forwarding, but those are problems that are solved by rvalue references.</span></span> <span data-ttu-id="7f859-154">Bevor wir r-Wert Verweise betrachten, jedoch müssen wir zunächst über klarer werden `T&` &mdash;das, was wir haben bisher wurden aufrufen einfach "einen Verweis".</span><span class="sxs-lookup"><span data-stu-id="7f859-154">Before we look at rvalue references, though, we first need to be clearer about `T&`&mdash;the thing we've formerly been calling just "a reference".</span></span> <span data-ttu-id="7f859-155">Es ist wirklich "einem l-Wert (nicht konstanter) Verweis", bezieht sich auf einen Wert, der der Benutzer über den Verweis schreiben kann.</span><span class="sxs-lookup"><span data-stu-id="7f859-155">It's really "an lvalue (non-const) reference", which refers to an value to which the user of the reference can write.</span></span>

```cppwinrt
template<typename T> T& get_by_lvalue_ref() { ... } // Get by lvalue (non-const) reference.
template<typename T> void set_by_lvalue_ref(T&) { ... } // Set by lvalue (non-const) reference.
```

<span data-ttu-id="7f859-156">Ein l-Wert-Verweis kann einem l-Wert, aber nicht in ein r-Wert binden.</span><span class="sxs-lookup"><span data-stu-id="7f859-156">An lvalue reference can bind to an lvalue, but not to an rvalue.</span></span>

<span data-ttu-id="7f859-157">L-Wert const Verweise sind (`T const&`), die auf Objekte in das der Benutzer über die Referenz *kann nicht* schreiben (z. B. eine Konstante) verweisen.</span><span class="sxs-lookup"><span data-stu-id="7f859-157">Then there are lvalue const references (`T const&`), which refer to objects to which the user of the reference *can't* write (for example, a constant).</span></span>

```cppwinrt
template<typename T> T const& get_by_lvalue_cref() { ... } // Get by lvalue const reference.
template<typename T> void set_by_lvalue_cref(T const&) { ... } // Set by lvalue const reference.
```

<span data-ttu-id="7f859-158">Ein l-Wert-Verweis kann an einem l-Wert oder ein r-Wert binden.</span><span class="sxs-lookup"><span data-stu-id="7f859-158">An lvalue const reference can bind to an lvalue or to an rvalue.</span></span>

<span data-ttu-id="7f859-159">Die Syntax für einen Verweis auf ein r-Wert vom Typ `T` lautet `T&&`.</span><span class="sxs-lookup"><span data-stu-id="7f859-159">The syntax for a reference to an rvalue of type `T` is written as `T&&`.</span></span> <span data-ttu-id="7f859-160">Ein r-Wert-Verweis bezieht sich auf einen verschiebbare Wert&mdash;einen Wert, deren Inhalt müssen wir nicht beibehalten, nachdem wir es (z. B. ein temporäres) verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="7f859-160">An rvalue reference refers to a movable value&mdash;an value whose contents we don't need to preserve after we've used it (for example, a temporary).</span></span> <span data-ttu-id="7f859-161">Seit dem gesamten Punkt Wechsels vom (wodurch ändern) der Wert gebunden ist, einen Verweis r-Wert `const` und `volatile` Qualifizierer (auch bekannt als cv-Qualifizierer) gelten nicht für Verweise r-Wert.</span><span class="sxs-lookup"><span data-stu-id="7f859-161">Since the whole point is to move from (thereby modifying) the value bound to an rvalue reference, `const` and `volatile` qualifiers (also known as cv-qualifiers) don't apply to rvalue references.</span></span>

```cppwinrt
template<typename T> T&& get_by_rvalue_ref() { ... } // Get by rvalue reference.
struct A { A(A&& other) { ... } }; // A move constructor takes an rvalue reference.
```

<span data-ttu-id="7f859-162">Ein r-Wert-Verweis Bindung an ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="7f859-162">An rvalue reference binds to an rvalue.</span></span> <span data-ttu-id="7f859-163">In der Tat hinsichtlich der Überladung Auflösung ein r-Wert *bevorzugt* ein r-Wert-Verweis als auf einem l-Wert-Verweis gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-163">In fact, in terms of overload resolution, an rvalue *prefers* to be bound to an rvalue reference than to an lvalue const reference.</span></span> <span data-ttu-id="7f859-164">Aber ein Verweis r-Wert kann nicht an einem l-Wert binden, daran, wie bereits erwähnt haben, ein r-Wert-Verweis auf einen Wert, deren Inhalt bezieht sich davon, dass wir benötigen ausgegangen wird (beispielsweise der Parameter für einen Verschiebungskonstruktor) zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7f859-164">But an rvalue reference can't bind to an lvalue because, as we've said, an rvalue reference refers to a value whose contents it's assumed we don't need to preserve (say, the parameter for a move constructor).</span></span>

<span data-ttu-id="7f859-165">Sie können auch übergeben ein r-Wert, in denen ein Argument als Wert zu erwarten ist über Kopie Konstruktion (oder verschieben Konstruktion, wenn die r-Wert ein Xvalue ist).</span><span class="sxs-lookup"><span data-stu-id="7f859-165">You can also pass an rvalue where a by-value argument is expected, via copy construction (or via move construction, if the rvalue is an xvalue).</span></span>

## <a name="a-glvalue-has-identity-a-prvalue-does-not"></a><span data-ttu-id="7f859-166">Ein Glvalue hat Identität. ein Prvalue nicht</span><span class="sxs-lookup"><span data-stu-id="7f859-166">A glvalue has identity; a prvalue does not</span></span>
<span data-ttu-id="7f859-167">Zu diesem Zeitpunkt wissen wir, welche Identität verfügt.</span><span class="sxs-lookup"><span data-stu-id="7f859-167">At this stage, we know what has identity.</span></span> <span data-ttu-id="7f859-168">Und wir wissen, was bewegliche ist und was nicht.</span><span class="sxs-lookup"><span data-stu-id="7f859-168">And we know what's movable and what isn't.</span></span> <span data-ttu-id="7f859-169">Aber wir noch nicht mit dem Namen der Serie von Werten Identität haben, *nicht* .</span><span class="sxs-lookup"><span data-stu-id="7f859-169">But we haven't yet named the set of values that *don't* have identity.</span></span> <span data-ttu-id="7f859-170">Set als *Prvalue*oder *reine r-Wert*bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="7f859-170">That set is known as the *prvalue*, or *pure rvalue*.</span></span>

```cppwinrt
int& get_by_ref() { ... }
int get_by_val() { ... }

int main()
{
    int* addr3{ &(get_by_ref() + 1) }; // Error: get_by_ref() + 1 is a prvalue.
    int* addr4{ &get_by_val() }; // Error: get_by_val() is a prvalue.
}
```

![Einem l-Wert hat Identität. ein Prvalue nicht](images/has-identity2.png)

## <a name="the-complete-picture-of-value-categories"></a><span data-ttu-id="7f859-172">Vollständige Übersicht der Wertekategorien</span><span class="sxs-lookup"><span data-stu-id="7f859-172">The complete picture of value categories</span></span>
<span data-ttu-id="7f859-173">Es bleibt nur um die Informationen und Illustrationen oben in einer einzelnen, großen Bild zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="7f859-173">It only remains to combine the info and illustrations above into a single, big picture.</span></span>

![Vollständige Übersicht der Wertekategorien](images/value-categories.png)

### <a name="glvalue-i"></a><span data-ttu-id="7f859-175">Glvalue (i)</span><span class="sxs-lookup"><span data-stu-id="7f859-175">glvalue (i)</span></span>
<span data-ttu-id="7f859-176">Eine Glvalue (generalisierten l-Wert) hat Identität.</span><span class="sxs-lookup"><span data-stu-id="7f859-176">A glvalue (generalized lvalue) has identity.</span></span>

### <a name="lvalue-im"></a><span data-ttu-id="7f859-177">l-Wert (I\ & \!m)</span><span class="sxs-lookup"><span data-stu-id="7f859-177">lvalue (i\&\!m)</span></span>
<span data-ttu-id="7f859-178">Einem l-Wert (eine Art von Glvalue) Identität hat, aber nicht verschoben.</span><span class="sxs-lookup"><span data-stu-id="7f859-178">An lvalue (a kind of glvalue) has identity, but isn't movable.</span></span> <span data-ttu-id="7f859-179">Hierbei handelt es sich um in der Regel Lese-/ Schreibzugriff-Werte, die Sie um durch einen Verweis oder-Verweis oder Wert übergeben, wenn das Kopieren von günstig ist.</span><span class="sxs-lookup"><span data-stu-id="7f859-179">These are typically read-write values that you pass around by reference or by const reference, or by value if copying is cheap.</span></span> <span data-ttu-id="7f859-180">Einem l-Wert kann nicht zu einer Referenz r-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-180">An lvalue can't be bound to an rvalue reference.</span></span>

### <a name="xvalue-im"></a><span data-ttu-id="7f859-181">xValue (I\ & m)</span><span class="sxs-lookup"><span data-stu-id="7f859-181">xvalue (i\&m)</span></span>
<span data-ttu-id="7f859-182">Ein Xvalue (eine Art von Glvalue, sondern auch eine Art von r-Wert) Identität hat, und kann auch verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-182">An xvalue (a kind of glvalue, but also a kind of rvalue) has identity, and is also movable.</span></span> <span data-ttu-id="7f859-183">Möglicherweise ein sammelte l-Wert, die Sie sich entschieden haben, verschieben, da kopieren aufwendig ist, und Sie werden nicht für den Zugriff darauf später achten.</span><span class="sxs-lookup"><span data-stu-id="7f859-183">This might be an erstwhile lvalue that you've decided to move because copying is expensive, and you'll be careful not to access it afterward.</span></span> <span data-ttu-id="7f859-184">Hier sehen Sie, wie Sie einem l-Wert in einer Xvalue aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="7f859-184">Here's how you can turn an lvalue into an xvalue.</span></span>

```cppwinrt
struct A { ... };
A a; // a is an lvalue...
static_cast<A&&>(a); // ...but this expression is an xvalue.
```

<span data-ttu-id="7f859-185">Im obigen Codebeispiel noch nicht wir etwas noch verschoben.</span><span class="sxs-lookup"><span data-stu-id="7f859-185">In the code example above, we haven't moved anything yet.</span></span> <span data-ttu-id="7f859-186">Wir haben eine Xvalue gerade erstellt haben, durch das Umwandeln von einem l-Wert zu einer Referenz unbenannten r-Wert.</span><span class="sxs-lookup"><span data-stu-id="7f859-186">We've just created an xvalue by casting an lvalue to an unnamed rvalue reference.</span></span> <span data-ttu-id="7f859-187">Sie können weiterhin anhand des Namens l-Wert gekennzeichnet werden. aber als ein Xvalue ist es jetzt *fähig* verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="7f859-187">It can still be identified by its lvalue name; but, as an xvalue, it is now *capable* of being moved.</span></span> <span data-ttu-id="7f859-188">Der Grund dafür, und welche verschieben tatsächlich, aussieht, müssen Sie warten, bis ein anderes Thema.</span><span class="sxs-lookup"><span data-stu-id="7f859-188">The reasons for doing so, and what moving actually looks like, will have to wait for another topic.</span></span> <span data-ttu-id="7f859-189">Aber Sie können sich das "X" in "Xvalue" als Bedeutung "Experte reinen" Wenn Ihnen dabei hilft, vorstellen.</span><span class="sxs-lookup"><span data-stu-id="7f859-189">But you can think of the "x" in "xvalue" as meaning "expert-only" if that helps.</span></span> <span data-ttu-id="7f859-190">Durch das Umwandeln von einem l-Wert in einer Xvalue (eine Art von r-Wert), wird der Wert kann zu einer Referenz r-Wert gebunden wird.</span><span class="sxs-lookup"><span data-stu-id="7f859-190">By casting an lvalue into an xvalue (a kind of rvalue), the value then becomes capable of being bound to an rvalue reference.</span></span>

<span data-ttu-id="7f859-191">Hier sind zwei weitere Beispiele für Xvalues&mdash;Aufrufen einer Funktion, die einen Verweis unbenannten r-Wert zurückgibt, und den Zugriff auf ein Mitglied einer Xvalue.</span><span class="sxs-lookup"><span data-stu-id="7f859-191">Here are two other examples of xvalues&mdash;calling a function that returns an unnamed rvalue reference, and accessing a member of an xvalue.</span></span>

```cppwinrt
struct A { int m; };
A&& f();
f(); // This expression is an xvalue...
f().m; // ...and so is this.
```

### <a name="prvalue-im"></a><span data-ttu-id="7f859-192">Prvalue (\!i\ & m)</span><span class="sxs-lookup"><span data-stu-id="7f859-192">prvalue (\!i\&m)</span></span>
<span data-ttu-id="7f859-193">Eine Prvalue (reine r-Wert; eine Art von r-Wert) zwar nicht Identität, aber kann verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-193">A prvalue (pure rvalue; a kind of rvalue) doesn't have identity, but is movable.</span></span> <span data-ttu-id="7f859-194">Diese in der Regel gegebebenfalls sind, gibt das Ergebnis des Aufrufs einer Funktion, die nach Wert oder das Ergebnis der Überprüfung alle anderen Ausdrucks, der nicht um eine Glvalue handelt,</span><span class="sxs-lookup"><span data-stu-id="7f859-194">These are typically temporaries, the result of calling a function that returns by value, or the result of evaluating any other expression that's not a glvalue,</span></span>

### <a name="rvalue-m"></a><span data-ttu-id="7f859-195">r-Wert (m)</span><span class="sxs-lookup"><span data-stu-id="7f859-195">rvalue (m)</span></span>
<span data-ttu-id="7f859-196">Ein r-Wert kann verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-196">An rvalue is movable.</span></span> <span data-ttu-id="7f859-197">Ein r-Wert- *Verweis* bezieht sich immer um ein r-Wert (mit dem Wert, deren Inhalt davon ausgegangen wird, die wir nicht beibehalten müssen).</span><span class="sxs-lookup"><span data-stu-id="7f859-197">An rvalue *reference* always refers to an rvalue (a value whose contents it's assumed we don't need to preserve).</span></span>

<span data-ttu-id="7f859-198">Allerdings ist ein r-Wert-Verweis selbst ein r-Wert?</span><span class="sxs-lookup"><span data-stu-id="7f859-198">But, is an rvalue reference itself an rvalue?</span></span> <span data-ttu-id="7f859-199">Eine *unbenannten* r-Wert-Referenz (z. B. den angezeigten obigen Codebeispiele Xvalue) ist ein Xvalue, Ja, es ist also ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="7f859-199">An *unnamed* rvalue reference (like the ones shown in the xvalue code examples above) is an xvalue so, yes, it's an rvalue.</span></span> <span data-ttu-id="7f859-200">Bevorzugte ein r-Wert-Funktion Referenzparameter, z. B., eines Konstruktors verschieben gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-200">It prefers to be bound to an rvalue reference function parameter, such as that of a move constructor.</span></span> <span data-ttu-id="7f859-201">Im Gegensatz dazu (und möglicherweise counter-intuitively), wenn ein Verweis r-Wert einen Namen hat, wird des Ausdrucks bestehend aus diesen Namen einem l-Wert.</span><span class="sxs-lookup"><span data-stu-id="7f859-201">Conversely (and perhaps counter-intuitively), if an rvalue reference has a name, then the expression consisting of that name is an lvalue.</span></span> <span data-ttu-id="7f859-202">Daher es *kann nicht* auf ein Referenzparameter r-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="7f859-202">So it *can't* be bound to an rvalue reference parameter.</span></span> <span data-ttu-id="7f859-203">Aber es ist einfach zu vereinfachen dazu&mdash;einfach erneut zu einer unbenannten r-Wert-Referenz (ein Xvalue) umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="7f859-203">But it's easy to make it do so&mdash;just cast it to an unnamed rvalue reference (an xvalue) again.</span></span>

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

### <a name="im"></a><span data-ttu-id="7f859-204">\!i\ & \!m</span><span class="sxs-lookup"><span data-stu-id="7f859-204">\!i\&\!m</span></span>
<span data-ttu-id="7f859-205">Die Art der Wert, der keine Identität und ist nicht verschiebbare handelt es sich um eine Kombination, die wir noch nicht erläutert noch nicht.</span><span class="sxs-lookup"><span data-stu-id="7f859-205">The kind of value that doesn't have identity and isn't movable is the one combination that we haven't yet discussed.</span></span> <span data-ttu-id="7f859-206">Aber wir können, da dieser Kategorie ist hilfreich, sich in der C++-Sprache nicht ignorieren.</span><span class="sxs-lookup"><span data-stu-id="7f859-206">But we can disregard it, because that category isn't a useful idea in the C++ language.</span></span>

## <a name="reference-collapsing-rules"></a><span data-ttu-id="7f859-207">Referenz zu reduzieren von Regeln</span><span class="sxs-lookup"><span data-stu-id="7f859-207">Reference-collapsing rules</span></span>
<span data-ttu-id="7f859-208">Mehrere wie z. B. Verweise in einem Ausdruck (einem l-Wert Verweis Verweis auf einem l-Wert oder ein Verweis auf r-Wert Verweis auf ein r-Wert) beenden eine anderen Out.</span><span class="sxs-lookup"><span data-stu-id="7f859-208">Multiple like references in an expression (an lvalue reference to an lvalue reference, or an rvalue reference to an rvalue reference) cancel one another out.</span></span>

- `A& &` <span data-ttu-id="7f859-209">in reduziert `A&`.</span><span class="sxs-lookup"><span data-stu-id="7f859-209">collapses into `A&`.</span></span>
- `A&& &&` <span data-ttu-id="7f859-210">in reduziert `A&&`.</span><span class="sxs-lookup"><span data-stu-id="7f859-210">collapses into `A&&`.</span></span>

<span data-ttu-id="7f859-211">Mehrere im Gegensatz zu Verweise in einem Ausdruck reduzieren zu einem l-Wert verweisen.</span><span class="sxs-lookup"><span data-stu-id="7f859-211">Multiple unlike references in an expression collapse to an lvalue reference.</span></span>

- `A& &&` <span data-ttu-id="7f859-212">in reduziert `A&`.</span><span class="sxs-lookup"><span data-stu-id="7f859-212">collapses into `A&`.</span></span>
- `A&& &` <span data-ttu-id="7f859-213">in reduziert `A&`.</span><span class="sxs-lookup"><span data-stu-id="7f859-213">collapses into `A&`.</span></span>

## <a name="forwarding-references"></a><span data-ttu-id="7f859-214">Weiterleitung Verweise</span><span class="sxs-lookup"><span data-stu-id="7f859-214">Forwarding references</span></span>
<span data-ttu-id="7f859-215">In diesem letzten Abschnitt gegenübergestellt r-Wert-Referenzen, die bisher bereits, mit dem anderen Konzept eine *Weiterleitung Referenz erwähnt wurden*.</span><span class="sxs-lookup"><span data-stu-id="7f859-215">This final section contrasts rvalue references, which we've already discussed, with the different concept of a *forwarding reference*.</span></span>

```cppwinrt
void foo(A&& a) { ... }
```

- `A&&` <span data-ttu-id="7f859-216">ist eine Referenz r-Wert an, wie wir gesehen haben.</span><span class="sxs-lookup"><span data-stu-id="7f859-216">is an rvalue reference, as we've seen.</span></span> <span data-ttu-id="7f859-217">Const und volatile gelten nicht für Verweise r-Wert.</span><span class="sxs-lookup"><span data-stu-id="7f859-217">Const and volatile don't apply to rvalue references.</span></span>
- `foo` <span data-ttu-id="7f859-218">akzeptiert nur Rvalues vom Typ **A**.</span><span class="sxs-lookup"><span data-stu-id="7f859-218">accepts only rvalues of type **A**.</span></span>
- <span data-ttu-id="7f859-219">Verweist auf den Grund r-Wert (z. B. `A&&`) vorhanden ist, damit Sie eine Überladung erstellen können, die für den Fall, in eine temporäre (oder andere r-Wert) übergeben wird optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="7f859-219">The reason rvalue references (such as `A&&`) exist is so that you can author an overload that's optimized for the case of a temporary (or other rvalue) being passed.</span></span>

```cppwinrt
template <typename _Ty> void bar(_Ty&& ty) { ... }
```

- `_Ty&&` <span data-ttu-id="7f859-220">ist eine *Weiterleitung Referenz*.</span><span class="sxs-lookup"><span data-stu-id="7f859-220">is a *forwarding reference*.</span></span> <span data-ttu-id="7f859-221">Je nachdem, was Sie zum übergeben `bar`, Typ **_Ty** Const/nicht konstanter unabhängig von Volatile/nicht flüchtigen werden konnte.</span><span class="sxs-lookup"><span data-stu-id="7f859-221">Depending what you pass to `bar`, type **_Ty** could be const/non-const independently of volatile/non-volatile.</span></span>
- `bar` <span data-ttu-id="7f859-222">Alle l-Wert oder r-Wert der Typ **_Ty**akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="7f859-222">accepts any lvalue or rvalue of type **_Ty**.</span></span>
- <span data-ttu-id="7f859-223">Übergeben von einem l-Wert bewirkt, dass die Weiterleitung Referenz zu `_Ty& &&`, die reduziert auf den Verweis l-Wert `_Ty&`.</span><span class="sxs-lookup"><span data-stu-id="7f859-223">Passing an lvalue causes the forwarding reference to become `_Ty& &&`, which collapses to the lvalue reference `_Ty&`.</span></span>
- <span data-ttu-id="7f859-224">Ein r-Wert übergeben wird die Weiterleitung Referenz zu `_Ty&& &&`, die reduziert auf den r-Wert-Verweis `_Ty&&`.</span><span class="sxs-lookup"><span data-stu-id="7f859-224">Passing an rvalue causes the forwarding reference to become `_Ty&& &&`, which collapses to the rvalue reference `_Ty&&`.</span></span>
- <span data-ttu-id="7f859-225">Der Grund weiterleiten Verweise (wie z. B. `_Ty&&`) vorhanden ist *nicht* für die Optimierung, jedoch zu nutzen, was Sie an Sie übergeben und auf transparent und effizient weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="7f859-225">The reason forwarding references (such as `_Ty&&`) exist is *not* for optimization, but to take what you pass to them and to forward it on transparently and efficiently.</span></span> <span data-ttu-id="7f859-226">Sie werden wahrscheinlich eine Weiterleitung-Referenz auftritt, nur dann, wenn Sie Bibliothekscodes schreiben (oder genauerer Betrachtung)&mdash;z. B. eine Factory-Funktion, die auf Konstruktorargumente weiterleitet.</span><span class="sxs-lookup"><span data-stu-id="7f859-226">You're likely to encounter a forwarding reference only if you write (or closely study) library code&mdash;for example, a factory function that forwards on constructor arguments.</span></span>

## <a name="sources"></a><span data-ttu-id="7f859-227">Quellen</span><span class="sxs-lookup"><span data-stu-id="7f859-227">Sources</span></span>
* <span data-ttu-id="7f859-228">\[Stroustrup, 2013\] b Stroustrup: die C++-Programmiersprache, die vierte Edition.</span><span class="sxs-lookup"><span data-stu-id="7f859-228">\[Stroustrup, 2013\] B. Stroustrup: The C++ Programming Language, Fourth Edition.</span></span> <span data-ttu-id="7f859-229">Addison-Wesley.</span><span class="sxs-lookup"><span data-stu-id="7f859-229">Addison-Wesley.</span></span> <span data-ttu-id="7f859-230">2013.</span><span class="sxs-lookup"><span data-stu-id="7f859-230">2013.</span></span>
