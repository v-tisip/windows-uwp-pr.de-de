---
author: stevewhims
description: Dieses Thema beschreibt die verschiedenen Kategorien von Werten, die in C++ vorhanden sind. Sie werden Ausrichtungsattributs verwendet kenne l-Werte und Rvalues, es stehen jedoch andere Arten auch.
title: Wert Kategorien und Verweise auf diese
ms.author: stwhi
ms.date: 08/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, verschieben, Weiterleitung, Wert Kategorien, Move-Semantik, perfekte Weiterleitung, l-Wert, r-Wert, Glvalue, Prvalue, Xvalue
ms.localizationpriority: medium
ms.openlocfilehash: cbccaf78b45d85d93619977d149431c4eec9e10a
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4536423"
---
# <a name="value-categories-and-references-to-them"></a><span data-ttu-id="c14f4-105">Wert Kategorien und Verweise auf diese</span><span class="sxs-lookup"><span data-stu-id="c14f4-105">Value categories, and references to them</span></span>
<span data-ttu-id="c14f4-106">Dieses Thema beschreibt die verschiedenen Kategorien von Werten (und Verweise auf Werte), die in C++ vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="c14f4-106">This topic describes the various categories of values (and references to values) that exist in C++.</span></span> <span data-ttu-id="c14f4-107">Sie werden Ausrichtungsattributs verwendet kenne *l-Werte* und *Rvalues*, aber möglicherweise nicht stellen sie in die Begriffe, die in diesem Thema wird vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-107">You will doubtless have heard of *lvalues* and *rvalues*, but you may not think of them in the terms that this topic presents.</span></span> <span data-ttu-id="c14f4-108">Und es gibt andere Arten von Werten, zu.</span><span class="sxs-lookup"><span data-stu-id="c14f4-108">And there are other kinds of values, too.</span></span>

<span data-ttu-id="c14f4-109">Jeder Ausdruck in C++ ergibt einen Wert, der auf eine der in diesem Thema erläuterten Kategorien gehört.</span><span class="sxs-lookup"><span data-stu-id="c14f4-109">Every expression in C++ yields a value that belongs to one of the categories discussed in this topic.</span></span> <span data-ttu-id="c14f4-110">Es gibt Aspekte der Programmiersprache C++, dessen Facilies und Regeln festgelegt, die Verständnis dieser Wert Kategorien und Verweise auf diese anfordern.</span><span class="sxs-lookup"><span data-stu-id="c14f4-110">There are aspects of the C++ language, its facilies, and rules, that demand a proper understanding of these value categories, and references to them.</span></span> <span data-ttu-id="c14f4-111">Die Adresse eines Werts, einen Wert kopieren, verschieben einen Wert und einen Wert an eine andere Funktion Weiterleiten z. B. nehmen.</span><span class="sxs-lookup"><span data-stu-id="c14f4-111">For example, taking the address of a value, copying a value, moving a value, and forwarding a value on to another function.</span></span> <span data-ttu-id="c14f4-112">In diesem Thema nicht in all diese Aspekte im Detail gehen, aber es enthält grundlegende Informationen für ein grundlegendes Verständnis davon.</span><span class="sxs-lookup"><span data-stu-id="c14f4-112">This topic doesn't go into all of those aspects in depth, but it provides foundational information for a solid understanding of them.</span></span>

<span data-ttu-id="c14f4-113">Die Informationen in diesem Thema wird durch die zwei unabhängigen Eigenschaften der Identität und Movability [Stroustrup 2013] hinsichtlich des Stroustrups Analyse der Wert Kategorien dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-113">The info in this topic is framed in terms of Stroustrup's analysis of value categories by the two independent properties of identity and movability [Stroustrup, 2013].</span></span>

## <a name="an-lvalue-has-identity"></a><span data-ttu-id="c14f4-114">Ein l-Wert hat Identität</span><span class="sxs-lookup"><span data-stu-id="c14f4-114">An lvalue has identity</span></span>
<span data-ttu-id="c14f4-115">Was bedeutet es für einen Wert *Identität*?</span><span class="sxs-lookup"><span data-stu-id="c14f4-115">What does it mean for a value to have *identity*?</span></span> <span data-ttu-id="c14f4-116">Wenn die Adresse des Arbeitsspeichers eines Werts Sie haben (oder geschaltet werden können), und sie sicher, und klicken Sie dann der Wert Identität verfügt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-116">If you have (or you can take) the memory address of a value and use it safely, then the value has identity.</span></span> <span data-ttu-id="c14f4-117">Auf diese Weise können Sie erreichen mehr als Vergleichen der Inhalt der Werte: Sie können vergleichen oder Identität zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-117">That way, you can do more than compare the contents of values: you can compare or distinguish them by identity.</span></span>

<span data-ttu-id="c14f4-118">Ein *l-Wert* hat Identität.</span><span class="sxs-lookup"><span data-stu-id="c14f4-118">An *lvalue* has identity.</span></span> <span data-ttu-id="c14f4-119">Es ist jetzt eine Frage des nur historisch Interesse an, dass das "l" in "l-Wert" Abkürzung für "Links" (wie, in der linken Seite einer Zuordnung) ist.</span><span class="sxs-lookup"><span data-stu-id="c14f4-119">It's now a matter of only historical interest that the "l" in "lvalue" is an abbreviation of "left" (as in, the left-hand-side of an assignment).</span></span> <span data-ttu-id="c14f4-120">In C++ kann ein l-Wert auf der linken *oder* auf der rechten Seite einer Zuordnung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-120">In C++, an lvalue can appear on the left *or* on the right of an assignment.</span></span> <span data-ttu-id="c14f4-121">Das "l" in "l-Werte", unterstützen nicht dann, tatsächlich Sie bei verstehen noch definieren, was sind.</span><span class="sxs-lookup"><span data-stu-id="c14f4-121">The "l" in "lvalues", then, doesn't actually help you to comprehend nor define what they are.</span></span> <span data-ttu-id="c14f4-122">Müssen Sie nur wissen, dass was rufen wir ein l-Wert einen Wert, der Identität verfügt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-122">You need only to understand that what we call an lvalue is a value that has identity.</span></span>

<span data-ttu-id="c14f4-123">Beispiele für Ausdrücke, die l-Werte sind: einer benannten Variable oder Konstante; eine Funktion, die einen Verweis oder gibt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-123">Examples of expressions that are lvalues include: a named variable or constant; or a function that returns a reference.</span></span> <span data-ttu-id="c14f4-124">Beispiele für Ausdrücke, die *nicht* l-Werte sind: ein temporäres; oder eine Funktion, die durch einen Wert zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-124">Examples of expressions that are *not* lvalues include: a temporary; or a function that returns by value.</span></span>

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

<span data-ttu-id="c14f4-125">Nun, es zwar Aussagen, l-Werte Identität haben, also tun Xvalues.</span><span class="sxs-lookup"><span data-stu-id="c14f4-125">Now, while it's a true statement that lvalues have identity, so do xvalues.</span></span> <span data-ttu-id="c14f4-126">Gehen wir mehr in welche ein *Xvalue* weiter unten in diesem Thema wird.</span><span class="sxs-lookup"><span data-stu-id="c14f4-126">We'll go more into what an *xvalue* is later in this topic.</span></span> <span data-ttu-id="c14f4-127">Seien Sie für den Moment Beachten Sie, dass der Wert Kategorie Glvalue, für die "generalisiert l-Wert".</span><span class="sxs-lookup"><span data-stu-id="c14f4-127">For now, just be aware that there is a value category called glvalue, for "generalized lvalue".</span></span> <span data-ttu-id="c14f4-128">Die Übermenge von Glvalues enthält l-Werte (auch bekannt als *klassische l-Werte*) und Xvalues.</span><span class="sxs-lookup"><span data-stu-id="c14f4-128">The superset of glvalues contains both lvalues (also known as *classical lvalues*) and xvalues.</span></span> <span data-ttu-id="c14f4-129">Ja, während er sich "ein l-Wert besitzt Identität" ist "true", der vollständige Satz von Dinge, die Identität der Satz von Glvalues, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-129">So, while "an lvalue has identity" is true, the complete set of things that have identity is the set of glvalues, as shown in this illustration.</span></span>

![Ein l-Wert hat Identität](images/has-identity1.png)

## <a name="an-rvalue-is-movable-an-lvalue-is-not"></a><span data-ttu-id="c14f4-131">Ein r-Wert ist verschoben. ein l-Wert ist nicht</span><span class="sxs-lookup"><span data-stu-id="c14f4-131">An rvalue is movable; an lvalue is not</span></span>
<span data-ttu-id="c14f4-132">Aber es gibt Werte, die nicht Glvalues sind.</span><span class="sxs-lookup"><span data-stu-id="c14f4-132">But there are values that are not glvalues.</span></span> <span data-ttu-id="c14f4-133">Daher sind Werte, die Sie *kann nicht* zu eine Speicheradresse für erhalten (oder nicht verlässlich er gültig sein).</span><span class="sxs-lookup"><span data-stu-id="c14f4-133">Consequently, there are values that you *can't* obtain a memory address for (or you can't rely on it to be valid).</span></span> <span data-ttu-id="c14f4-134">Wir haben gesehen, einige dieser Werte im obigen Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="c14f4-134">We saw some such values in the code example above.</span></span> <span data-ttu-id="c14f4-135">Dies klingt wie einen Nachteil.</span><span class="sxs-lookup"><span data-stu-id="c14f4-135">This sounds like a disadvantage.</span></span> <span data-ttu-id="c14f4-136">Aber in der Tat können den Vorteil, einen Wert wie das heißt, dass Sie daraus *Verschieben* können (was in der Regel günstig ist), statt kopieren (was in der Regel teuer ist).</span><span class="sxs-lookup"><span data-stu-id="c14f4-136">But in fact the advantage of a value like that is that you can *move* from it (which is generally cheap), rather than copy from it (which is generally expensive).</span></span> <span data-ttu-id="c14f4-137">Wechseln von einem Wert bedeutet, dass es nicht mehr an der Stelle, die verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-137">Moving from a value means that it's no longer in the place it used to be.</span></span> <span data-ttu-id="c14f4-138">Also versuchen, an der Stelle auf Sie zugreifen, werden Sie verwendet, etwas vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-138">So, trying to access it in the place it used to be is something to be avoided.</span></span> <span data-ttu-id="c14f4-139">Eine Erläuterung der wann und *wie* , ein Wert außerhalb des Bereichs für dieses Thema ist zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="c14f4-139">A discussion of when and *how* to move a value is out of scope for this topic.</span></span> <span data-ttu-id="c14f4-140">In diesem Thema benötigen wir lediglich wissen, dass ein Wert, der bewegliche ist als ein *r-Wert* (oder *klassische r-Wert*) bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="c14f4-140">For this topic, we just need to know that a value that is movable is known as an *rvalue* (or *classical rvalue*).</span></span>

<span data-ttu-id="c14f4-141">Die "R" in "r"-Wert ist eine Abkürzung des "rechts" (wie, die rechte Seite einer Zuordnung).</span><span class="sxs-lookup"><span data-stu-id="c14f4-141">The "r" in "rvalue" is an abbreviation of "right" (as in, the right-hand-side of an assignment).</span></span> <span data-ttu-id="c14f4-142">Sie können jedoch Rvalues und Verweise auf Rvalues außerhalb von Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="c14f4-142">But you can use rvalues, and references to rvalues, outside of assignments.</span></span> <span data-ttu-id="c14f4-143">Die "R" in "Rvalues" ist, nicht das, was zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="c14f4-143">The "r" in "rvalues", then, is not the thing to focus on.</span></span> <span data-ttu-id="c14f4-144">Sie müssen nur zu verstehen, dass was rufen wir ein r-Wert einen Wert bewegliche ist.</span><span class="sxs-lookup"><span data-stu-id="c14f4-144">You need only to understand that what we call an rvalue is a value that is movable.</span></span>

<span data-ttu-id="c14f4-145">Ein l-Wert ist dagegen bewegliche, nicht, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-145">An lvalue, conversely, isn't movable, as shown in this illustration.</span></span> <span data-ttu-id="c14f4-146">Ein l-Wert, die verschoben würde die Definition von *l-Wert*gibt, und es wäre ein unerwarteter Fehler für Code, der sehr vernünftig weiterhin auf die l-Wert zugreifen können soll.</span><span class="sxs-lookup"><span data-stu-id="c14f4-146">An lvalue that moved would defy the definition of *lvalue*, and it would be an unexpected problem for code that very reasonably expected to be able to continue to access the lvalue.</span></span>

![Ein r-Wert ist verschoben. ein l-Wert ist nicht](images/is-movable.png)

<span data-ttu-id="c14f4-148">Ein l-Wert kann nicht verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-148">You can't move an lvalue.</span></span> <span data-ttu-id="c14f4-149">Aber es *ist* eine Art von Glvalue (die Gruppe Dinge, die mit der Identität), die Sie verschieben können&mdash;Wenn Sie wissen, was Sie tun (einschließlich Achten Sie nicht für den Zugriff darauf nach dem Verschieben)&mdash;und die Xvalue.</span><span class="sxs-lookup"><span data-stu-id="c14f4-149">But there *is* a kind of glvalue (the set of things with identity) that you can move&mdash;if you know what you're doing (including being careful not to access it after the move)&mdash;and that's the xvalue.</span></span> <span data-ttu-id="c14f4-150">Wir werden diese Idee noch einmal unten, besuchen Sie bei der vollständiges Bild Wert Kategorien Wir betrachten.</span><span class="sxs-lookup"><span data-stu-id="c14f4-150">We'll revisit this idea one more time below, when we look at the complete picture of value categories.</span></span>

## <a name="rvalue-references-and-reference-binding-rules"></a><span data-ttu-id="c14f4-151">R-Wert Verweise und Referenz-Bindungsregeln</span><span class="sxs-lookup"><span data-stu-id="c14f4-151">Rvalue references, and reference-binding rules</span></span>
<span data-ttu-id="c14f4-152">In diesem Abschnitt werden die Syntax für einen Verweis auf ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-152">This section introduces the syntax for a reference to an rvalue.</span></span> <span data-ttu-id="c14f4-153">Wir müssen warten, bis ein anderes Thema das Aufrufen einer erheblichen Behandlung verschieben und weiterleiten, allerdings sind Probleme, die durch r-Wert Verweise behoben werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-153">We'll have to wait for another topic to go into a substantial treatment of moving and forwarding, but those are problems that are solved by rvalue references.</span></span> <span data-ttu-id="c14f4-154">Bevor wir r-Wert Verweise betrachten, jedoch müssen wir zunächst über deutlicher werden `T&` &mdash;das, was wir haben bisher wurden aufrufen einfach "einen Verweis".</span><span class="sxs-lookup"><span data-stu-id="c14f4-154">Before we look at rvalue references, though, we first need to be clearer about `T&`&mdash;the thing we've formerly been calling just "a reference".</span></span> <span data-ttu-id="c14f4-155">Es ist wirklich "ein l-Wert (non-Const) Verweis" bezieht sich auf einen Wert, der Benutzer über den Verweis schreiben kann.</span><span class="sxs-lookup"><span data-stu-id="c14f4-155">It's really "an lvalue (non-const) reference", which refers to an value to which the user of the reference can write.</span></span>

```cppwinrt
template<typename T> T& get_by_lvalue_ref() { ... } // Get by lvalue (non-const) reference.
template<typename T> void set_by_lvalue_ref(T&) { ... } // Set by lvalue (non-const) reference.
```

<span data-ttu-id="c14f4-156">Ein Verweis l-Wert kann ein l-Wert, aber nicht in ein r-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-156">An lvalue reference can bind to an lvalue, but not to an rvalue.</span></span>

<span data-ttu-id="c14f4-157">L-Wert const Verweise sind (`T const&`), die auf Objekte, die in das der Benutzer die Referenz *kann nicht* schreiben (z. B. eine Konstante) verweisen.</span><span class="sxs-lookup"><span data-stu-id="c14f4-157">Then there are lvalue const references (`T const&`), which refer to objects to which the user of the reference *can't* write (for example, a constant).</span></span>

```cppwinrt
template<typename T> T const& get_by_lvalue_cref() { ... } // Get by lvalue const reference.
template<typename T> void set_by_lvalue_cref(T const&) { ... } // Set by lvalue const reference.
```

<span data-ttu-id="c14f4-158">Ein l-Wert-Verweis kann an ein l-Wert oder ein r-Wert binden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-158">An lvalue const reference can bind to an lvalue or to an rvalue.</span></span>

<span data-ttu-id="c14f4-159">Die Syntax für einen Verweis auf ein r-Wert vom Typ `T` lautet `T&&`.</span><span class="sxs-lookup"><span data-stu-id="c14f4-159">The syntax for a reference to an rvalue of type `T` is written as `T&&`.</span></span> <span data-ttu-id="c14f4-160">Ein r-Wert-Verweis bezieht sich auf einen verschiebbare Wert&mdash;einen Wert, deren Inhalt müssen wir nicht beibehalten, nachdem wir (z. B. ein temporäres) verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="c14f4-160">An rvalue reference refers to a movable value&mdash;an value whose contents we don't need to preserve after we've used it (for example, a temporary).</span></span> <span data-ttu-id="c14f4-161">Seit dem gesamten Punkt Wechsels vom (wodurch ändern) der Wert gebunden ist, einen Verweis r-Wert `const` und `volatile` Qualifizierer (auch bekannt als cv-Qualifizierer) gelten nicht für Verweise r-Wert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-161">Since the whole point is to move from (thereby modifying) the value bound to an rvalue reference, `const` and `volatile` qualifiers (also known as cv-qualifiers) don't apply to rvalue references.</span></span>

```cppwinrt
template<typename T> T&& get_by_rvalue_ref() { ... } // Get by rvalue reference.
struct A { A(A&& other) { ... } }; // A move constructor takes an rvalue reference.
```

<span data-ttu-id="c14f4-162">Ein r-Wert-Verweis Bindung an ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-162">An rvalue reference binds to an rvalue.</span></span> <span data-ttu-id="c14f4-163">In der Tat hinsichtlich der Überladung Auflösung ein r-Wert *bevorzugt* einen Verweis r-Wert als für ein-Verweis l-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-163">In fact, in terms of overload resolution, an rvalue *prefers* to be bound to an rvalue reference than to an lvalue const reference.</span></span> <span data-ttu-id="c14f4-164">Aber ein Verweis r-Wert kann nicht an ein l-Wert binden, daran, wie bereits erwähnt haben, ein r-Wert-Verweis auf einen Wert, deren Inhalt bezieht sich davon, dass wir benötigen ausgegangen wird (beispielsweise der Parameter für einen Verschiebungskonstruktor) zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c14f4-164">But an rvalue reference can't bind to an lvalue because, as we've said, an rvalue reference refers to a value whose contents it's assumed we don't need to preserve (say, the parameter for a move constructor).</span></span>

<span data-ttu-id="c14f4-165">Sie können auch übergeben ein r-Wert, in denen ein Argument als Wert zu erwarten ist über Kopie erstellen (oder verschieben Konstruktion, ist die r-Wert ein Xvalue).</span><span class="sxs-lookup"><span data-stu-id="c14f4-165">You can also pass an rvalue where a by-value argument is expected, via copy construction (or via move construction, if the rvalue is an xvalue).</span></span>

## <a name="a-glvalue-has-identity-a-prvalue-does-not"></a><span data-ttu-id="c14f4-166">Ein Glvalue hat Identität. ein Prvalue nicht</span><span class="sxs-lookup"><span data-stu-id="c14f4-166">A glvalue has identity; a prvalue does not</span></span>
<span data-ttu-id="c14f4-167">Zu diesem Zeitpunkt wissen wir, welche Identität verfügt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-167">At this stage, we know what has identity.</span></span> <span data-ttu-id="c14f4-168">Und wir wissen, was bewegliche ist und was nicht.</span><span class="sxs-lookup"><span data-stu-id="c14f4-168">And we know what's movable and what isn't.</span></span> <span data-ttu-id="c14f4-169">Aber wir noch, nicht mit dem Namen der Serie von Werten, *nicht* haben Identität.</span><span class="sxs-lookup"><span data-stu-id="c14f4-169">But we haven't yet named the set of values that *don't* have identity.</span></span> <span data-ttu-id="c14f4-170">Set als *Prvalue*oder *reine r-Wert*bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="c14f4-170">That set is known as the *prvalue*, or *pure rvalue*.</span></span>

```cppwinrt
int& get_by_ref() { ... }
int get_by_val() { ... }

int main()
{
    int* addr3{ &(get_by_ref() + 1) }; // Error: get_by_ref() + 1 is a prvalue.
    int* addr4{ &get_by_val() }; // Error: get_by_val() is a prvalue.
}
```

![Ein l-Wert hat Identität. ein Prvalue nicht](images/has-identity2.png)

## <a name="the-complete-picture-of-value-categories"></a><span data-ttu-id="c14f4-172">Vollständiges Bild Wert Kategorien</span><span class="sxs-lookup"><span data-stu-id="c14f4-172">The complete picture of value categories</span></span>
<span data-ttu-id="c14f4-173">Es bleibt nur um die Informationen und Illustrationen oben in einer einzelnen, großen Bild zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="c14f4-173">It only remains to combine the info and illustrations above into a single, big picture.</span></span>

![Vollständiges Bild Wert Kategorien](images/value-categories.png)

### <a name="glvalue-i"></a><span data-ttu-id="c14f4-175">Glvalue (i)</span><span class="sxs-lookup"><span data-stu-id="c14f4-175">glvalue (i)</span></span>
<span data-ttu-id="c14f4-176">Ein Glvalue (generalisierten l-Wert) hat Identität.</span><span class="sxs-lookup"><span data-stu-id="c14f4-176">A glvalue (generalized lvalue) has identity.</span></span>

### <a name="lvalue-im"></a><span data-ttu-id="c14f4-177">l-Wert (I\ & \!m)</span><span class="sxs-lookup"><span data-stu-id="c14f4-177">lvalue (i\&\!m)</span></span>
<span data-ttu-id="c14f4-178">Ein l-Wert (eine Art von Glvalue) Identität hat, jedoch nicht verschoben.</span><span class="sxs-lookup"><span data-stu-id="c14f4-178">An lvalue (a kind of glvalue) has identity, but isn't movable.</span></span> <span data-ttu-id="c14f4-179">Hierbei handelt es sich um in der Regel Lese-/ Schreibzugriff-Werte, die Sie um durch einen Verweis durch-Verweis, oder per Wert übergeben, wenn das Kopieren von günstig ist.</span><span class="sxs-lookup"><span data-stu-id="c14f4-179">These are typically read-write values that you pass around by reference or by const reference, or by value if copying is cheap.</span></span> <span data-ttu-id="c14f4-180">Ein l-Wert kann nicht zu einer Referenz r-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-180">An lvalue can't be bound to an rvalue reference.</span></span>

### <a name="xvalue-im"></a><span data-ttu-id="c14f4-181">xValue (I\ & m)</span><span class="sxs-lookup"><span data-stu-id="c14f4-181">xvalue (i\&m)</span></span>
<span data-ttu-id="c14f4-182">Ein Xvalue (eine Art von Glvalue, aber auch eine Art von r-Wert) Identität hat, und kann auch verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-182">An xvalue (a kind of glvalue, but also a kind of rvalue) has identity, and is also movable.</span></span> <span data-ttu-id="c14f4-183">Möglicherweise ein sammelte l-Wert, die Sie sich entschieden haben, verschieben, da das Kopieren aufwendig ist, und Sie werden nicht für den Zugriff darauf später achten.</span><span class="sxs-lookup"><span data-stu-id="c14f4-183">This might be an erstwhile lvalue that you've decided to move because copying is expensive, and you'll be careful not to access it afterward.</span></span> <span data-ttu-id="c14f4-184">Hier sehen Sie, wie Sie ein l-Wert in einem Xvalue aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="c14f4-184">Here's how you can turn an lvalue into an xvalue.</span></span>

```cppwinrt
struct A { ... };
A a; // a is an lvalue...
static_cast<A&&>(a); // ...but this expression is an xvalue.
```

<span data-ttu-id="c14f4-185">Im obigen Codebeispiel noch nicht wir etwas noch verschoben.</span><span class="sxs-lookup"><span data-stu-id="c14f4-185">In the code example above, we haven't moved anything yet.</span></span> <span data-ttu-id="c14f4-186">Wir haben eine Xvalue durch das Umwandeln einer l-Wert zu einer unbenannten r-Wert-Referenz erstellt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-186">We've just created an xvalue by casting an lvalue to an unnamed rvalue reference.</span></span> <span data-ttu-id="c14f4-187">Sie können weiterhin anhand des l-Wert namens identifiziert werden; aber als ein Xvalue ist es jetzt *fähig* verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="c14f4-187">It can still be identified by its lvalue name; but, as an xvalue, it is now *capable* of being moved.</span></span> <span data-ttu-id="c14f4-188">Der Grund dafür, und welche verschieben tatsächlich, aussieht, müssen Sie warten, bis ein anderes Thema.</span><span class="sxs-lookup"><span data-stu-id="c14f4-188">The reasons for doing so, and what moving actually looks like, will have to wait for another topic.</span></span> <span data-ttu-id="c14f4-189">Aber Sie können sich das "X" in "Xvalue" als Bedeutung "Experte nur" Wenn Ihnen dabei hilft, vorstellen.</span><span class="sxs-lookup"><span data-stu-id="c14f4-189">But you can think of the "x" in "xvalue" as meaning "expert-only" if that helps.</span></span> <span data-ttu-id="c14f4-190">Durch das Umwandeln einer l-Wert in einem Xvalue (eine Art von r-Wert), wird der Wert anschließend kann zu einer Referenz r-Wert gebunden wird.</span><span class="sxs-lookup"><span data-stu-id="c14f4-190">By casting an lvalue into an xvalue (a kind of rvalue), the value then becomes capable of being bound to an rvalue reference.</span></span>

<span data-ttu-id="c14f4-191">Hier sind zwei weitere Beispiele für Xvalues&mdash;Aufrufen einer Funktion, die einen Verweis unbenannten r-Wert zurückgibt, und den Zugriff auf ein Mitglied einer Xvalue.</span><span class="sxs-lookup"><span data-stu-id="c14f4-191">Here are two other examples of xvalues&mdash;calling a function that returns an unnamed rvalue reference, and accessing a member of an xvalue.</span></span>

```cppwinrt
struct A { int m; };
A&& f();
f(); // This expression is an xvalue...
f().m; // ...and so is this.
```

### <a name="prvalue-im"></a><span data-ttu-id="c14f4-192">Prvalue (\!i\ & m)</span><span class="sxs-lookup"><span data-stu-id="c14f4-192">prvalue (\!i\&m)</span></span>
<span data-ttu-id="c14f4-193">Ein Prvalue (reiner r-Wert; eine Art von r-Wert) zwar nicht Identität, aber kann verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-193">A prvalue (pure rvalue; a kind of rvalue) doesn't have identity, but is movable.</span></span> <span data-ttu-id="c14f4-194">Diese in der Regel gegebebenfalls sind, gibt das Ergebnis des Aufrufs einer Funktion, die nach Wert oder das Ergebnis der Auswertung eines anderen Ausdrucks, der keine Glvalue,</span><span class="sxs-lookup"><span data-stu-id="c14f4-194">These are typically temporaries, the result of calling a function that returns by value, or the result of evaluating any other expression that's not a glvalue,</span></span>

### <a name="rvalue-m"></a><span data-ttu-id="c14f4-195">r-Wert (m)</span><span class="sxs-lookup"><span data-stu-id="c14f4-195">rvalue (m)</span></span>
<span data-ttu-id="c14f4-196">Ein r-Wert kann verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-196">An rvalue is movable.</span></span> <span data-ttu-id="c14f4-197">Ein r-Wert- *Verweis* bezieht sich immer um ein r-Wert (ein Wert, deren Inhalt davon ausgegangen wird, die wir nicht beibehalten müssen).</span><span class="sxs-lookup"><span data-stu-id="c14f4-197">An rvalue *reference* always refers to an rvalue (a value whose contents it's assumed we don't need to preserve).</span></span>

<span data-ttu-id="c14f4-198">Allerdings ist ein r-Wert-Verweis selbst ein r-Wert?</span><span class="sxs-lookup"><span data-stu-id="c14f4-198">But, is an rvalue reference itself an rvalue?</span></span> <span data-ttu-id="c14f4-199">Eine *unbenannten* r-Wert-Referenz (z. B. den angezeigten obigen Codebeispiele Xvalue) ist ein Xvalue, Ja, es ist also ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-199">An *unnamed* rvalue reference (like the ones shown in the xvalue code examples above) is an xvalue so, yes, it's an rvalue.</span></span> <span data-ttu-id="c14f4-200">Bevorzugte ein r-Wert-Funktion Referenzparameter, z. B. von einem Verschiebungskonstruktor gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-200">It prefers to be bound to an rvalue reference function parameter, such as that of a move constructor.</span></span> <span data-ttu-id="c14f4-201">Im Gegensatz dazu (und möglicherweise counter-intuitively), wenn ein r-Wert-Verweis einen Namen hat, wird der Ausdruck mit diesem Namen besteht ein l-Wert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-201">Conversely (and perhaps counter-intuitively), if an rvalue reference has a name, then the expression consisting of that name is an lvalue.</span></span> <span data-ttu-id="c14f4-202">Daher es *kann nicht* auf ein Referenzparameter r-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="c14f4-202">So it *can't* be bound to an rvalue reference parameter.</span></span> <span data-ttu-id="c14f4-203">Es ist jedoch ganz einfach zu vereinfachen dazu&mdash;einfach erneut zu einer unbenannten r-Wert-Referenz (ein Xvalue) umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="c14f4-203">But it's easy to make it do so&mdash;just cast it to an unnamed rvalue reference (an xvalue) again.</span></span>

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

### <a name="im"></a><span data-ttu-id="c14f4-204">\!i\ & \!m</span><span class="sxs-lookup"><span data-stu-id="c14f4-204">\!i\&\!m</span></span>
<span data-ttu-id="c14f4-205">Die Art der Wert, der keine Identität und ist nicht verschiebbare ist die eine Kombination aus, der wir noch nicht erläutert noch nicht.</span><span class="sxs-lookup"><span data-stu-id="c14f4-205">The kind of value that doesn't have identity and isn't movable is the one combination that we haven't yet discussed.</span></span> <span data-ttu-id="c14f4-206">Aber wir können, da dieser Kategorie ist hilfreich, sich in der C++-Sprache nicht ignorieren.</span><span class="sxs-lookup"><span data-stu-id="c14f4-206">But we can disregard it, because that category isn't a useful idea in the C++ language.</span></span>

## <a name="reference-collapsing-rules"></a><span data-ttu-id="c14f4-207">Referenz zu reduzieren von Regeln</span><span class="sxs-lookup"><span data-stu-id="c14f4-207">Reference-collapsing rules</span></span>
<span data-ttu-id="c14f4-208">Mehrere wie z. B. Verweise in einem Ausdruck (ein Verweis auf l-Wert Verweis auf ein l-Wert oder ein r-Wert-Verweis auf einen Verweis r-Wert) Abbrechen einer anderen Out.</span><span class="sxs-lookup"><span data-stu-id="c14f4-208">Multiple like references in an expression (an lvalue reference to an lvalue reference, or an rvalue reference to an rvalue reference) cancel one another out.</span></span>

- `A& &` <span data-ttu-id="c14f4-209">in reduziert `A&`.</span><span class="sxs-lookup"><span data-stu-id="c14f4-209">collapses into `A&`.</span></span>
- `A&& &&` <span data-ttu-id="c14f4-210">in reduziert `A&&`.</span><span class="sxs-lookup"><span data-stu-id="c14f4-210">collapses into `A&&`.</span></span>

<span data-ttu-id="c14f4-211">Mehrere anders als Verweise in einem Ausdruck reduzieren zu einer Referenz l-Wert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-211">Multiple unlike references in an expression collapse to an lvalue reference.</span></span>

- `A& &&` <span data-ttu-id="c14f4-212">in reduziert `A&`.</span><span class="sxs-lookup"><span data-stu-id="c14f4-212">collapses into `A&`.</span></span>
- `A&& &` <span data-ttu-id="c14f4-213">in reduziert `A&`.</span><span class="sxs-lookup"><span data-stu-id="c14f4-213">collapses into `A&`.</span></span>

## <a name="forwarding-references"></a><span data-ttu-id="c14f4-214">Weiterleitung Verweise</span><span class="sxs-lookup"><span data-stu-id="c14f4-214">Forwarding references</span></span>
<span data-ttu-id="c14f4-215">In diesem letzten Abschnitt gegenübergestellt r-Wert-Referenzen, die bereits, mit dem anderen Konzept eine *Weiterleitung Verweis*erläutert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-215">This final section contrasts rvalue references, which we've already discussed, with the different concept of a *forwarding reference*.</span></span>

```cppwinrt
void foo(A&& a) { ... }
```

- `A&&` <span data-ttu-id="c14f4-216">ist ein Verweis r-Wert an, wie wir gesehen haben.</span><span class="sxs-lookup"><span data-stu-id="c14f4-216">is an rvalue reference, as we've seen.</span></span> <span data-ttu-id="c14f4-217">Const und volatile gelten nicht für Verweise r-Wert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-217">Const and volatile don't apply to rvalue references.</span></span>
- `foo` <span data-ttu-id="c14f4-218">akzeptiert nur Rvalues vom Typ **A**.</span><span class="sxs-lookup"><span data-stu-id="c14f4-218">accepts only rvalues of type **A**.</span></span>
- <span data-ttu-id="c14f4-219">Verweist auf den Grund r-Wert (z. B. `A&&`) vorhanden ist, damit Sie eine Überladung erstellen können, die für den Fall ein temporäres (oder andere r-Wert) übergebenen optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="c14f4-219">The reason rvalue references (such as `A&&`) exist is so that you can author an overload that's optimized for the case of a temporary (or other rvalue) being passed.</span></span>

```cppwinrt
template <typename _Ty> void bar(_Ty&& ty) { ... }
```

- `_Ty&&` <span data-ttu-id="c14f4-220">ist eine *Weiterleitung Referenz*.</span><span class="sxs-lookup"><span data-stu-id="c14f4-220">is a *forwarding reference*.</span></span> <span data-ttu-id="c14f4-221">Je nachdem, was Sie zum übergeben `bar`, Typ **_Ty** Const/nicht konstanter unabhängig von Volatile/nichtflüchtigen werden konnte.</span><span class="sxs-lookup"><span data-stu-id="c14f4-221">Depending what you pass to `bar`, type **_Ty** could be const/non-const independently of volatile/non-volatile.</span></span>
- `bar` <span data-ttu-id="c14f4-222">Alle l-Wert oder r-Wert der Typ **_Ty**akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="c14f4-222">accepts any lvalue or rvalue of type **_Ty**.</span></span>
- <span data-ttu-id="c14f4-223">Übergeben ein l-Wert bewirkt, dass die Weiterleitung Referenz zu `_Ty& &&`, die reduziert, um den Verweis l-Wert `_Ty&`.</span><span class="sxs-lookup"><span data-stu-id="c14f4-223">Passing an lvalue causes the forwarding reference to become `_Ty& &&`, which collapses to the lvalue reference `_Ty&`.</span></span>
- <span data-ttu-id="c14f4-224">Übergeben ein r-Wert bewirkt, dass die Weiterleitung Referenz zu `_Ty&& &&`, die reduziert auf den r-Wert-Verweis `_Ty&&`.</span><span class="sxs-lookup"><span data-stu-id="c14f4-224">Passing an rvalue causes the forwarding reference to become `_Ty&& &&`, which collapses to the rvalue reference `_Ty&&`.</span></span>
- <span data-ttu-id="c14f4-225">Der Grund weiterleiten Verweise (wie z. B. `_Ty&&`) vorhanden sind, ist *nicht* für die Optimierung, jedoch zu nutzen, was Sie darauf übergeben und auf transparent und effizient weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="c14f4-225">The reason forwarding references (such as `_Ty&&`) exist is *not* for optimization, but to take what you pass to them and to forward it on transparently and efficiently.</span></span> <span data-ttu-id="c14f4-226">Sie werden wahrscheinlich eine Weiterleitung-Referenz auftritt, nur dann, wenn Sie Bibliothekscodes schreiben (oder genauerer Betrachtung)&mdash;z. B. eine Factory-Funktion, die auf Konstruktorargumente weiterleitet.</span><span class="sxs-lookup"><span data-stu-id="c14f4-226">You're likely to encounter a forwarding reference only if you write (or closely study) library code&mdash;for example, a factory function that forwards on constructor arguments.</span></span>

## <a name="sources"></a><span data-ttu-id="c14f4-227">Quellen</span><span class="sxs-lookup"><span data-stu-id="c14f4-227">Sources</span></span>
* <span data-ttu-id="c14f4-228">\[Stroustrup, 2013\] b Stroustrup: die Programmiersprache C++, vierte Edition.</span><span class="sxs-lookup"><span data-stu-id="c14f4-228">\[Stroustrup, 2013\] B. Stroustrup: The C++ Programming Language, Fourth Edition.</span></span> <span data-ttu-id="c14f4-229">Addison-Wesley.</span><span class="sxs-lookup"><span data-stu-id="c14f4-229">Addison-Wesley.</span></span> <span data-ttu-id="c14f4-230">2013.</span><span class="sxs-lookup"><span data-stu-id="c14f4-230">2013.</span></span>
