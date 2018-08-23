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
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2814672"
---
# <a name="value-categories-and-references-to-them"></a><span data-ttu-id="98e5c-105">Wert Kategorien und Verweise auf diese</span><span class="sxs-lookup"><span data-stu-id="98e5c-105">Value categories, and references to them</span></span>
<span data-ttu-id="98e5c-106">In diesem Thema werden die verschiedenen Kategorien von Werte (und Verweise auf Werte), die in C++ vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="98e5c-106">This topic describes the various categories of values (and references to values) that exist in C++.</span></span> <span data-ttu-id="98e5c-107">Sie werden Ausrichtungsattributs verwendet der *l-Werte* und *Rvalues*gehört haben, aber möglicherweise nicht stellen sie in der Begriffe, die in diesem Thema wird.</span><span class="sxs-lookup"><span data-stu-id="98e5c-107">You will doubtless have heard of *lvalues* and *rvalues*, but you may not think of them in the terms that this topic presents.</span></span> <span data-ttu-id="98e5c-108">Und sind andere Arten der Werte zu.</span><span class="sxs-lookup"><span data-stu-id="98e5c-108">And there are other kinds of values, too.</span></span>

<span data-ttu-id="98e5c-109">Jeder Ausdruck in C++ ergibt ein Werts, das eine der in diesem Thema behandelten Kategorien gehört.</span><span class="sxs-lookup"><span data-stu-id="98e5c-109">Every expression in C++ yields a value that belongs to one of the categories discussed in this topic.</span></span> <span data-ttu-id="98e5c-110">Aspekte der Programmiersprache C++, seine Facilies und Regeln, die gefordert wird das richtige Verständnis dieser Wert Kategorien und die Verweise darauf sind vorhanden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-110">There are aspects of the C++ language, its facilies, and rules, that demand a proper understanding of these value categories, and references to them.</span></span> <span data-ttu-id="98e5c-111">Die Adresse eines Werts, Kopieren eines Werts, verschieben einen Wert und einen Wert an eine andere Funktion Weiterleiten beispielsweise nehmen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-111">For example, taking the address of a value, copying a value, moving a value, and forwarding a value on to another function.</span></span> <span data-ttu-id="98e5c-112">In diesem Thema nicht in alle Aspekte im Detail gehen, aber es enthält grundlegende Informationen zu verstehen und einen einfarbigen davon.</span><span class="sxs-lookup"><span data-stu-id="98e5c-112">This topic doesn't go into all of those aspects in depth, but it provides foundational information for a solid understanding of them.</span></span>

<span data-ttu-id="98e5c-113">Die Informationen in diesem Thema wird durch die zwei unabhängigen Eigenschaften der Identität und Movability [Stroustrup 2013] im Hinblick auf Stroustrups Analyse der Wert Kategorien eingerahmt.</span><span class="sxs-lookup"><span data-stu-id="98e5c-113">The info in this topic is framed in terms of Stroustrup's analysis of value categories by the two independent properties of identity and movability [Stroustrup, 2013].</span></span>

## <a name="an-lvalue-has-identity"></a><span data-ttu-id="98e5c-114">Ein l-Wert hat Identität.</span><span class="sxs-lookup"><span data-stu-id="98e5c-114">An lvalue has identity</span></span>
<span data-ttu-id="98e5c-115">Was bedeutet es für einen Wert *Identität*?</span><span class="sxs-lookup"><span data-stu-id="98e5c-115">What does it mean for a value to have *identity*?</span></span> <span data-ttu-id="98e5c-116">Wenn die Arbeitsspeicher-Adresse eines Werts Sie haben (oder können) herunter, und sicher, und klicken Sie dann den Wert Identität hat.</span><span class="sxs-lookup"><span data-stu-id="98e5c-116">If you have (or you can take) the memory address of a value and use it safely, then the value has identity.</span></span> <span data-ttu-id="98e5c-117">Auf diese Weise können Sie Aktionen ausführen mehr als Compare den Inhalt der Werte: Sie können vergleichen oder Identity zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-117">That way, you can do more than compare the contents of values: you can compare or distinguish them by identity.</span></span>

<span data-ttu-id="98e5c-118">Ein *l-Wert* hat Identität.</span><span class="sxs-lookup"><span data-stu-id="98e5c-118">An *lvalue* has identity.</span></span> <span data-ttu-id="98e5c-119">Es ist nun eine Frage der nur zurückliegenden Interesse, dass das "l" in "l"-Wert eine Abkürzung von "Left" (wie, in der linken Seite einer Zuweisung) ist.</span><span class="sxs-lookup"><span data-stu-id="98e5c-119">It's now a matter of only historical interest that the "l" in "lvalue" is an abbreviation of "left" (as in, the left-hand-side of an assignment).</span></span> <span data-ttu-id="98e5c-120">In C++ kann ein l-Wert auf der linken *oder* auf der rechten Seite einer Zuweisung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-120">In C++, an lvalue can appear on the left *or* on the right of an assignment.</span></span> <span data-ttu-id="98e5c-121">"L" in "l-Werte", klicken Sie dann hilft tatsächlich nicht Sie verstehen noch definieren, was sind.</span><span class="sxs-lookup"><span data-stu-id="98e5c-121">The "l" in "lvalues", then, doesn't actually help you to comprehend nor define what they are.</span></span> <span data-ttu-id="98e5c-122">Sie müssen nur wissen, dass wir ein l-Wert aufrufen, wird ein Wert, der Identität hat.</span><span class="sxs-lookup"><span data-stu-id="98e5c-122">You need only to understand that what we call an lvalue is a value that has identity.</span></span>

<span data-ttu-id="98e5c-123">Beispiele für Ausdrücke, die l-Werte sind: einer benannten Variablen oder Konstanten; oder eine Funktion, die einen Verweis zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="98e5c-123">Examples of expressions that are lvalues include: a named variable or constant; or a function that returns a reference.</span></span> <span data-ttu-id="98e5c-124">Beispiele für Ausdrücke, die *nicht* l-Werte sind: ein temporäres; oder eine Funktion, die durch einen Wert zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="98e5c-124">Examples of expressions that are *not* lvalues include: a temporary; or a function that returns by value.</span></span>

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

<span data-ttu-id="98e5c-125">Nun, es zwar Aussagen, l-Werte Identität haben, also tun Xvalues.</span><span class="sxs-lookup"><span data-stu-id="98e5c-125">Now, while it's a true statement that lvalues have identity, so do xvalues.</span></span> <span data-ttu-id="98e5c-126">Gehen wir mehr in welche ein *Xvalue* weiter unten in diesem Thema wird.</span><span class="sxs-lookup"><span data-stu-id="98e5c-126">We'll go more into what an *xvalue* is later in this topic.</span></span> <span data-ttu-id="98e5c-127">Jetzt nur Beachten Sie, dass es eine Wert Kategorie Glvalue ist, für die "Allgemeiner (engl.) l-Wert" aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-127">For now, just be aware that there is a value category called glvalue, for "generalized lvalue".</span></span> <span data-ttu-id="98e5c-128">Die Obermenge von Glvalues enthält l-Werte (auch bekannt als *klassische l-Werte*) und Xvalues.</span><span class="sxs-lookup"><span data-stu-id="98e5c-128">The superset of glvalues contains both lvalues (also known as *classical lvalues*) and xvalues.</span></span> <span data-ttu-id="98e5c-129">Ja, während er sich "Identität hat ein l-Wert" true festgelegt ist, der vollständige Satz von Features, mit denen Identitätswert wird der Satz von Glvalues, wie in dieser Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="98e5c-129">So, while "an lvalue has identity" is true, the complete set of things that have identity is the set of glvalues, as shown in this illustration.</span></span>

![Ein l-Wert hat Identität.](images/has-identity1.png)

## <a name="an-rvalue-is-movable-an-lvalue-is-not"></a><span data-ttu-id="98e5c-131">Ein r-Wert ist verschiebbar. ein l-Wert ist nicht</span><span class="sxs-lookup"><span data-stu-id="98e5c-131">An rvalue is movable; an lvalue is not</span></span>
<span data-ttu-id="98e5c-132">Es gibt jedoch Werte, die nicht Glvalues sind.</span><span class="sxs-lookup"><span data-stu-id="98e5c-132">But there are values that are not glvalues.</span></span> <span data-ttu-id="98e5c-133">Daher sind Werte, die Sie *kann nicht* für eine Adresse Arbeitsspeicher erhalten (oder Sie können nicht verlassen, um gültig sein).</span><span class="sxs-lookup"><span data-stu-id="98e5c-133">Consequently, there are values that you *can't* obtain a memory address for (or you can't rely on it to be valid).</span></span> <span data-ttu-id="98e5c-134">Wir haben gesehen, einige dieser Werte im obigen Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="98e5c-134">We saw some such values in the code example above.</span></span> <span data-ttu-id="98e5c-135">Das klingt ein Nachteil.</span><span class="sxs-lookup"><span data-stu-id="98e5c-135">This sounds like a disadvantage.</span></span> <span data-ttu-id="98e5c-136">Aber tatsächlich der Vorteil eines Werts wie d. h., dass Sie daraus *Verschieben* können (die im Allgemeinen billig ist), statt daraus (die in der Regel teuer ist) kopieren.</span><span class="sxs-lookup"><span data-stu-id="98e5c-136">But in fact the advantage of a value like that is that you can *move* from it (which is generally cheap), rather than copy from it (which is generally expensive).</span></span> <span data-ttu-id="98e5c-137">Umstellen von einem Wert bedeutet, dass es nicht mehr an der Stelle, die verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-137">Moving from a value means that it's no longer in the place it used to be.</span></span> <span data-ttu-id="98e5c-138">Ist es an der Stelle zugreifen werden verwendeten möchte etwas vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-138">So, trying to access it in the place it used to be is something to be avoided.</span></span> <span data-ttu-id="98e5c-139">Eine Erläuterung der wann und *wie* , wird ein Wert außerhalb des Gültigkeitsbereichs für dieses Thema zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="98e5c-139">A discussion of when and *how* to move a value is out of scope for this topic.</span></span> <span data-ttu-id="98e5c-140">Zu diesem Thema müssen wir wissen, dass ein Wert, der verschiebbar ist als ein *r-Wert* (oder *klassische r-Wert*) bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="98e5c-140">For this topic, we just need to know that a value that is movable is known as an *rvalue* (or *classical rvalue*).</span></span>

<span data-ttu-id="98e5c-141">"R" in "r"-Wert ist eine Abkürzung des "rechts" (wie, in der rechten Seite einer Zuweisung).</span><span class="sxs-lookup"><span data-stu-id="98e5c-141">The "r" in "rvalue" is an abbreviation of "right" (as in, the right-hand-side of an assignment).</span></span> <span data-ttu-id="98e5c-142">Jedoch können Rvalues und Verweise auf Rvalues, außerhalb von Zuordnungen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-142">But you can use rvalues, and references to rvalues, outside of assignments.</span></span> <span data-ttu-id="98e5c-143">"R" in "Rvalues," ist, nicht das, was konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="98e5c-143">The "r" in "rvalues", then, is not the thing to focus on.</span></span> <span data-ttu-id="98e5c-144">Sie müssen nur wissen, dass wir ein r-Wert aufrufen, wird ein Wert, der verschiebbar ist.</span><span class="sxs-lookup"><span data-stu-id="98e5c-144">You need only to understand that what we call an rvalue is a value that is movable.</span></span>

<span data-ttu-id="98e5c-145">Ein l-Wert nicht umgekehrt bewegliche, wie in der Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="98e5c-145">An lvalue, conversely, isn't movable, as shown in this illustration.</span></span> <span data-ttu-id="98e5c-146">Ein l-Wert, die verschoben würde die Definition der *l-Wert*setzen, und es wäre ein unerwarteter Fehler für Code, die nach vernünftigem Ermessen sehr erwartet, weiterhin dass auf die l-Wert zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="98e5c-146">An lvalue that moved would defy the definition of *lvalue*, and it would be an unexpected problem for code that very reasonably expected to be able to continue to access the lvalue.</span></span>

![Ein r-Wert ist verschiebbar. ein l-Wert ist nicht](images/is-movable.png)

<span data-ttu-id="98e5c-148">Ein l-Wert kann nicht verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-148">You can't move an lvalue.</span></span> <span data-ttu-id="98e5c-149">Aber es *ist* eine Art von Glvalue (der Satz von Aufgaben mit der Identität), die Sie verschieben können&mdash;Wenn Sie genau wissen, was Sie tun (einschließlich, ohne dabei darauf zugreifen, nach dem Verschieben)&mdash;und die Xvalue ist.</span><span class="sxs-lookup"><span data-stu-id="98e5c-149">But there *is* a kind of glvalue (the set of things with identity) that you can move&mdash;if you know what you're doing (including being careful not to access it after the move)&mdash;and that's the xvalue.</span></span> <span data-ttu-id="98e5c-150">Wenn das vollständige Bild des Wert Kategorien Wir betrachten, werden wir noch einmal weiter unten diese Idee erneut.</span><span class="sxs-lookup"><span data-stu-id="98e5c-150">We'll revisit this idea one more time below, when we look at the complete picture of value categories.</span></span>

## <a name="rvalue-references-and-reference-binding-rules"></a><span data-ttu-id="98e5c-151">R-Wert-Referenzen und Verweis Bindung Regeln</span><span class="sxs-lookup"><span data-stu-id="98e5c-151">Rvalue references, and reference-binding rules</span></span>
<span data-ttu-id="98e5c-152">In diesem Abschnitt werden die Syntax für einen Verweis auf ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-152">This section introduces the syntax for a reference to an rvalue.</span></span> <span data-ttu-id="98e5c-153">Wir müssen warten, bis eine andere Thema aus, um eine erhebliche Behandlung verschieben und Weiterleiten von eingefügt, aber dies sind Probleme, die durch Verweise r-Wert gelöst werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-153">We'll have to wait for another topic to go into a substantial treatment of moving and forwarding, but those are problems that are solved by rvalue references.</span></span> <span data-ttu-id="98e5c-154">Bevor wir uns r-Wert Verweise ansehen, allerdings müssen Sie zuerst zur besseren werden `T&` &mdash;das, was wir haben früher wurden aufrufen nur "einen Verweis".</span><span class="sxs-lookup"><span data-stu-id="98e5c-154">Before we look at rvalue references, though, we first need to be clearer about `T&`&mdash;the thing we've formerly been calling just "a reference".</span></span> <span data-ttu-id="98e5c-155">Es ist wirklich so "ein l-Wert (nicht-Const) Referenz", die auf einen Wert bezieht sich auf die der Benutzer des Verweises schreiben kann.</span><span class="sxs-lookup"><span data-stu-id="98e5c-155">It's really "an lvalue (non-const) reference", which refers to an value to which the user of the reference can write.</span></span>

```cppwinrt
template<typename T> T& get_by_lvalue_ref() { ... } // Get by lvalue (non-const) reference.
template<typename T> void set_by_lvalue_ref(T&) { ... } // Set by lvalue (non-const) reference.
```

<span data-ttu-id="98e5c-156">Ein Verweis l-Wert kann auf einen l-Wert, jedoch nicht auf ein r-Wert binden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-156">An lvalue reference can bind to an lvalue, but not to an rvalue.</span></span>

<span data-ttu-id="98e5c-157">L-Wert Konstante Verweise sind (`T const&`), die auf Objekte, der der Benutzer über den Verweis *kann nicht* geschrieben (beispielsweise eine Konstante) verweisen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-157">Then there are lvalue const references (`T const&`), which refer to objects to which the user of the reference *can't* write (for example, a constant).</span></span>

```cppwinrt
template<typename T> T const& get_by_lvalue_cref() { ... } // Get by lvalue const reference.
template<typename T> void set_by_lvalue_cref(T const&) { ... } // Set by lvalue const reference.
```

<span data-ttu-id="98e5c-158">Ein l-Wert-Verweis kann an einer l-Wert oder ein r-Wert binden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-158">An lvalue const reference can bind to an lvalue or to an rvalue.</span></span>

<span data-ttu-id="98e5c-159">Die Syntax für einen Verweis auf ein r-Wert vom Typ `T` wird als geschrieben `T&&`.</span><span class="sxs-lookup"><span data-stu-id="98e5c-159">The syntax for a reference to an rvalue of type `T` is written as `T&&`.</span></span> <span data-ttu-id="98e5c-160">Ein Verweis r-Wert bezieht sich auf einen Wert bewegliche&mdash;einen Wert dar, deren Inhalt wir nicht beibehalten, nachdem wir (beispielsweise ein temporäres) verwendet haben müssen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-160">An rvalue reference refers to a movable value&mdash;an value whose contents we don't need to preserve after we've used it (for example, a temporary).</span></span> <span data-ttu-id="98e5c-161">Seit der gesamten Punkt zum Wechsel von (wodurch ändern) der Wert an gebunden ist ein Verweis r-Wert `const` und `volatile` Qualifizierer (auch bekannt als cv-Qualifizierer) gelten nicht für r-Wert verweisen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-161">Since the whole point is to move from (thereby modifying) the value bound to an rvalue reference, `const` and `volatile` qualifiers (also known as cv-qualifiers) don't apply to rvalue references.</span></span>

```cppwinrt
template<typename T> T&& get_by_rvalue_ref() { ... } // Get by rvalue reference.
struct A { A(A&& other) { ... } }; // A move constructor takes an rvalue reference.
```

<span data-ttu-id="98e5c-162">Ein Verweis r-Wert bindet ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-162">An rvalue reference binds to an rvalue.</span></span> <span data-ttu-id="98e5c-163">Tatsächlich im Hinblick auf Überladung Auflösung ein r-Wert *bevorzugt* ein Verweis auf r-Wert Verweis als auf eine Konstante l-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-163">In fact, in terms of overload resolution, an rvalue *prefers* to be bound to an rvalue reference than to an lvalue const reference.</span></span> <span data-ttu-id="98e5c-164">Aber ein r-Wert-Verweis kann nicht an ein l-Wert gebunden werden, da Sie, wie wir gesagt haben, ein r-Wert einen Wert, dessen Inhalt bezieht sich Reference auf davon ausgegangen wird, dass wir nicht beibehalten (sag, die Parameter für einen Konstruktor Move) müssen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-164">But an rvalue reference can't bind to an lvalue because, as we've said, an rvalue reference refers to a value whose contents it's assumed we don't need to preserve (say, the parameter for a move constructor).</span></span>

<span data-ttu-id="98e5c-165">Sie können auch übergeben ein r-Wert, auf dem ein Argumentwert zu erwarten ist über Kopie Konstruktion (oder Move Konstruktion, wenn der r-Wert ein Xvalue ist).</span><span class="sxs-lookup"><span data-stu-id="98e5c-165">You can also pass an rvalue where a by-value argument is expected, via copy construction (or via move construction, if the rvalue is an xvalue).</span></span>

## <a name="a-glvalue-has-identity-a-prvalue-does-not"></a><span data-ttu-id="98e5c-166">Ein Glvalue hat Identität. nicht der Fall ist eine prvalue</span><span class="sxs-lookup"><span data-stu-id="98e5c-166">A glvalue has identity; a prvalue does not</span></span>
<span data-ttu-id="98e5c-167">In dieser Phase wissen wir, was Identität hat.</span><span class="sxs-lookup"><span data-stu-id="98e5c-167">At this stage, we know what has identity.</span></span> <span data-ttu-id="98e5c-168">Und wir wissen, was verschiebbar ist und was nicht.</span><span class="sxs-lookup"><span data-stu-id="98e5c-168">And we know what's movable and what isn't.</span></span> <span data-ttu-id="98e5c-169">Aber wir noch nicht noch mit dem Namen der Gruppe von Werten, die diese *nicht* verfügen Identität.</span><span class="sxs-lookup"><span data-stu-id="98e5c-169">But we haven't yet named the set of values that *don't* have identity.</span></span> <span data-ttu-id="98e5c-170">Die Gruppe als *Prvalue*oder *reine r-Wert*bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="98e5c-170">That set is known as the *prvalue*, or *pure rvalue*.</span></span>

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

## <a name="the-complete-picture-of-value-categories"></a><span data-ttu-id="98e5c-172">Das vollständige Bild des Wert Kategorien</span><span class="sxs-lookup"><span data-stu-id="98e5c-172">The complete picture of value categories</span></span>
<span data-ttu-id="98e5c-173">Es wird nur um den Info und Abbildungen oben in einer einzelnen, großen Bild zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="98e5c-173">It only remains to combine the info and illustrations above into a single, big picture.</span></span>

![Das vollständige Bild des Wert Kategorien](images/value-categories.png)

### <a name="glvalue-i"></a><span data-ttu-id="98e5c-175">Glvalue (i)</span><span class="sxs-lookup"><span data-stu-id="98e5c-175">glvalue (i)</span></span>
<span data-ttu-id="98e5c-176">Eine Glvalue (Allgemeine l-Wert) hat Identität.</span><span class="sxs-lookup"><span data-stu-id="98e5c-176">A glvalue (generalized lvalue) has identity.</span></span>

### <a name="lvalue-im"></a><span data-ttu-id="98e5c-177">l-Wert (I\ & \!m)</span><span class="sxs-lookup"><span data-stu-id="98e5c-177">lvalue (i\&\!m)</span></span>
<span data-ttu-id="98e5c-178">Ein l-Wert (eine Art von Glvalue) Identität hat, aber nicht verschiebbar.</span><span class="sxs-lookup"><span data-stu-id="98e5c-178">An lvalue (a kind of glvalue) has identity, but isn't movable.</span></span> <span data-ttu-id="98e5c-179">Dies sind in der Regel Lese-/ Schreibzugriff-Werten, die Sie um Verweis oder-Verweis oder Wert übergeben, wenn das Kopieren kostengünstig ist.</span><span class="sxs-lookup"><span data-stu-id="98e5c-179">These are typically read-write values that you pass around by reference or by const reference, or by value if copying is cheap.</span></span> <span data-ttu-id="98e5c-180">Ein l-Wert kann nicht in einen Bezug r-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-180">An lvalue can't be bound to an rvalue reference.</span></span>

### <a name="xvalue-im"></a><span data-ttu-id="98e5c-181">xValue (I\ & m)</span><span class="sxs-lookup"><span data-stu-id="98e5c-181">xvalue (i\&m)</span></span>
<span data-ttu-id="98e5c-182">Ein Xvalue (eine Art von Glvalue, sondern auch eine Art von r-Wert) über Identität und kann auch verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-182">An xvalue (a kind of glvalue, but also a kind of rvalue) has identity, and is also movable.</span></span> <span data-ttu-id="98e5c-183">Möglicherweise ein sammelte l-Wert, der Sie sich entschieden haben, verschieben, da das Kopieren teuer ist und Sie vermutlich nicht die ihn danach aufrufen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-183">This might be an erstwhile lvalue that you've decided to move because copying is expensive, and you'll be careful not to access it afterward.</span></span> <span data-ttu-id="98e5c-184">Nachfolgend finden Sie, wie Sie ein l-Wert in einer Xvalue aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="98e5c-184">Here's how you can turn an lvalue into an xvalue.</span></span>

```cppwinrt
struct A { ... };
A a; // a is an lvalue...
static_cast<A&&>(a); // ...but this expression is an xvalue.
```

<span data-ttu-id="98e5c-185">Im obigen Codebeispiel hatte keine wir nichts noch verschoben.</span><span class="sxs-lookup"><span data-stu-id="98e5c-185">In the code example above, we haven't moved anything yet.</span></span> <span data-ttu-id="98e5c-186">Durch das Umwandeln eines l-Wert in einen Bezug unbenannte r-Wert haben wir eine Xvalue erstellt.</span><span class="sxs-lookup"><span data-stu-id="98e5c-186">We've just created an xvalue by casting an lvalue to an unnamed rvalue reference.</span></span> <span data-ttu-id="98e5c-187">Sie können weiterhin anhand des Namens der l-Wert bezeichnet werden. befindet sich jedoch, als ein Xvalue jetzt *fähig* verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="98e5c-187">It can still be identified by its lvalue name; but, as an xvalue, it is now *capable* of being moved.</span></span> <span data-ttu-id="98e5c-188">Der Grund dafür, und welche verschieben tatsächlich, aussieht nach einem anderen Thema warten müssen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-188">The reasons for doing so, and what moving actually looks like, will have to wait for another topic.</span></span> <span data-ttu-id="98e5c-189">Jedoch können Sie sich das "X" in "Xvalue" als Bedeutung "Expert-only" Wenn Ihnen dabei hilft, vorstellen.</span><span class="sxs-lookup"><span data-stu-id="98e5c-189">But you can think of the "x" in "xvalue" as meaning "expert-only" if that helps.</span></span> <span data-ttu-id="98e5c-190">Durch das Umwandeln eines l-Wert in einer Xvalue (eine Art von r-Wert), wird der Wert der Bindung an ein Verweis r-Wert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-190">By casting an lvalue into an xvalue (a kind of rvalue), the value then becomes capable of being bound to an rvalue reference.</span></span>

<span data-ttu-id="98e5c-191">Es folgen zwei weitere Beispiele für Xvalues&mdash;Aufrufen einer Funktion, die einen Verweis unbenannte r-Wert zurückgibt, und den Zugriff auf ein Mitglied einer Xvalue.</span><span class="sxs-lookup"><span data-stu-id="98e5c-191">Here are two other examples of xvalues&mdash;calling a function that returns an unnamed rvalue reference, and accessing a member of an xvalue.</span></span>

```cppwinrt
struct A { int m; };
A&& f();
f(); // This expression is an xvalue...
f().m; // ...and so is this.
```

### <a name="prvalue-im"></a><span data-ttu-id="98e5c-192">Prvalue (\!i\ & m)</span><span class="sxs-lookup"><span data-stu-id="98e5c-192">prvalue (\!i\&m)</span></span>
<span data-ttu-id="98e5c-193">Eine Prvalue (reine r-Wert; eine Art von r-Wert) verfügt nicht über Identität, aber kann verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-193">A prvalue (pure rvalue; a kind of rvalue) doesn't have identity, but is movable.</span></span> <span data-ttu-id="98e5c-194">Dies in der Regel gegebebenfalls sind, gibt das Ergebnis des Aufrufs einer Funktion, die nach Wert oder das Ergebnis der Auswertung eines anderen Ausdrucks, der ein Glvalue nicht ist,</span><span class="sxs-lookup"><span data-stu-id="98e5c-194">These are typically temporaries, the result of calling a function that returns by value, or the result of evaluating any other expression that's not a glvalue,</span></span>

### <a name="rvalue-m"></a><span data-ttu-id="98e5c-195">r-Wert (m)</span><span class="sxs-lookup"><span data-stu-id="98e5c-195">rvalue (m)</span></span>
<span data-ttu-id="98e5c-196">Ein r-Wert kann verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-196">An rvalue is movable.</span></span> <span data-ttu-id="98e5c-197">Ein r-Wert- *Verweis* bezieht sich immer um ein r-Wert (ein Wert, dessen Inhalt davon ausgegangen wird, die wir nicht beibehalten müssen).</span><span class="sxs-lookup"><span data-stu-id="98e5c-197">An rvalue *reference* always refers to an rvalue (a value whose contents it's assumed we don't need to preserve).</span></span>

<span data-ttu-id="98e5c-198">Aber ein r-Wert-Verweis selbst ein r-Wert ist?</span><span class="sxs-lookup"><span data-stu-id="98e5c-198">But, is an rvalue reference itself an rvalue?</span></span> <span data-ttu-id="98e5c-199">Ein *unbenannte* r-Wert Verweis (wie in den oben genannten Xvalue Codebeispielen dargestellt) ist ein Xvalue Ja, es ist also ein r-Wert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-199">An *unnamed* rvalue reference (like the ones shown in the xvalue code examples above) is an xvalue so, yes, it's an rvalue.</span></span> <span data-ttu-id="98e5c-200">Bevorzugte ein r-Wert Funktion Verweisparameter, wie der Move-Konstruktor gebunden sein.</span><span class="sxs-lookup"><span data-stu-id="98e5c-200">It prefers to be bound to an rvalue reference function parameter, such as that of a move constructor.</span></span> <span data-ttu-id="98e5c-201">Umgekehrt (und möglicherweise counter-intuitively), wenn ein Verweis r-Wert einen Namen hat, wird des Ausdrucks, der mit diesem Namen besteht ein l-Wert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-201">Conversely (and perhaps counter-intuitively), if an rvalue reference has a name, then the expression consisting of that name is an lvalue.</span></span> <span data-ttu-id="98e5c-202">So es *kann nicht* an einen Verweisparameter r-Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-202">So it *can't* be bound to an rvalue reference parameter.</span></span> <span data-ttu-id="98e5c-203">Aber es ist einfach zu vereinfachen dazu&mdash;einfach wieder in einen Bezug unbenannte r-Wert (eine Xvalue) umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="98e5c-203">But it's easy to make it do so&mdash;just cast it to an unnamed rvalue reference (an xvalue) again.</span></span>

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

### <a name="im"></a><span data-ttu-id="98e5c-204">\!i\ & \!m</span><span class="sxs-lookup"><span data-stu-id="98e5c-204">\!i\&\!m</span></span>
<span data-ttu-id="98e5c-205">Die Art des Werts, der keinen Identität und ist nicht verschiebbar ist die eine Kombination aus, der wir noch nicht besprochen wurden.</span><span class="sxs-lookup"><span data-stu-id="98e5c-205">The kind of value that doesn't have identity and isn't movable is the one combination that we haven't yet discussed.</span></span> <span data-ttu-id="98e5c-206">Jedoch können wir, ignorieren, da dieser Kategorie ist nützlich, sich in der Sprache C++ nicht.</span><span class="sxs-lookup"><span data-stu-id="98e5c-206">But we can disregard it, because that category isn't a useful idea in the C++ language.</span></span>

## <a name="reference-collapsing-rules"></a><span data-ttu-id="98e5c-207">Verweis Reduzieren von Regeln</span><span class="sxs-lookup"><span data-stu-id="98e5c-207">Reference-collapsing rules</span></span>
<span data-ttu-id="98e5c-208">Mehrere like Verweise in einem Ausdruck (einem l-Wert Verweis Verweis auf ein l-Wert oder ein Verweis auf r-Wert Verweis auf ein r-Wert) beenden eine einer anderen Out.</span><span class="sxs-lookup"><span data-stu-id="98e5c-208">Multiple like references in an expression (an lvalue reference to an lvalue reference, or an rvalue reference to an rvalue reference) cancel one another out.</span></span>

- `A& &` <span data-ttu-id="98e5c-209">Blendet in `A&`.</span><span class="sxs-lookup"><span data-stu-id="98e5c-209">collapses into `A&`.</span></span>
- `A&& &&` <span data-ttu-id="98e5c-210">Blendet in `A&&`.</span><span class="sxs-lookup"><span data-stu-id="98e5c-210">collapses into `A&&`.</span></span>

<span data-ttu-id="98e5c-211">Im Gegensatz zu verweisen in einem Ausdruck mehrere reduzieren in einen Bezug l-Wert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-211">Multiple unlike references in an expression collapse to an lvalue reference.</span></span>

- `A& &&` <span data-ttu-id="98e5c-212">Blendet in `A&`.</span><span class="sxs-lookup"><span data-stu-id="98e5c-212">collapses into `A&`.</span></span>
- `A&& &` <span data-ttu-id="98e5c-213">Blendet in `A&`.</span><span class="sxs-lookup"><span data-stu-id="98e5c-213">collapses into `A&`.</span></span>

## <a name="forwarding-references"></a><span data-ttu-id="98e5c-214">Weiterleiten von Verweise</span><span class="sxs-lookup"><span data-stu-id="98e5c-214">Forwarding references</span></span>
<span data-ttu-id="98e5c-215">In diesem letzten Abschnitt gegenübergestellt Verweise auf r-Wert, der bereits, mit dem verschiedene Konzept einer *Weiterleitung Verweis*erläutert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-215">This final section contrasts rvalue references, which we've already discussed, with the different concept of a *forwarding reference*.</span></span>

```cppwinrt
void foo(A&& a) { ... }
```

- `A&&` <span data-ttu-id="98e5c-216">ist ein Verweis r-Wert an, wie wir gesehen haben.</span><span class="sxs-lookup"><span data-stu-id="98e5c-216">is an rvalue reference, as we've seen.</span></span> <span data-ttu-id="98e5c-217">Const und volatile gelten nicht für Verweise r-Wert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-217">Const and volatile don't apply to rvalue references.</span></span>
- `foo` <span data-ttu-id="98e5c-218">nur Rvalues vom Typ **A**akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="98e5c-218">accepts only rvalues of type **A**.</span></span>
- <span data-ttu-id="98e5c-219">Verweist auf den Grund r-Wert (z. B. `A&&`) vorhanden ist, sodass Sie eine Überladung erstellen können, die für die Groß-/Kleinschreibung ein temporäres (oder andere r-Wert) übergebenen optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="98e5c-219">The reason rvalue references (such as `A&&`) exist is so that you can author an overload that's optimized for the case of a temporary (or other rvalue) being passed.</span></span>

```cppwinrt
template <typename _Ty> void bar(_Ty&& ty) { ... }
```

- `_Ty&&` <span data-ttu-id="98e5c-220">ist ein *Verweis weiterleiten*.</span><span class="sxs-lookup"><span data-stu-id="98e5c-220">is a *forwarding reference*.</span></span> <span data-ttu-id="98e5c-221">Je nachdem, was übergebene `bar`, Typ **_Ty** Const/nicht konstanter unabhängig veränderlich/unveränderliche werden konnte.</span><span class="sxs-lookup"><span data-stu-id="98e5c-221">Depending what you pass to `bar`, type **_Ty** could be const/non-const independently of volatile/non-volatile.</span></span>
- `bar` <span data-ttu-id="98e5c-222">akzeptiert alle l-Wert oder r-Wert des Typs **_Ty**.</span><span class="sxs-lookup"><span data-stu-id="98e5c-222">accepts any lvalue or rvalue of type **_Ty**.</span></span>
- <span data-ttu-id="98e5c-223">Übergeben eines l-Wert bewirkt, dass die Weiterleitung Referenz zu `_Ty& &&`, die zur Referenz l-Wert wird reduziert `_Ty&`.</span><span class="sxs-lookup"><span data-stu-id="98e5c-223">Passing an lvalue causes the forwarding reference to become `_Ty& &&`, which collapses to the lvalue reference `_Ty&`.</span></span>
- <span data-ttu-id="98e5c-224">Übergabe ein r-Wert bewirkt, dass die Weiterleitung Referenz zu `_Ty&& &&`, die zur Referenz r-Wert wird reduziert `_Ty&&`.</span><span class="sxs-lookup"><span data-stu-id="98e5c-224">Passing an rvalue causes the forwarding reference to become `_Ty&& &&`, which collapses to the rvalue reference `_Ty&&`.</span></span>
- <span data-ttu-id="98e5c-225">Der Grund dafür weiterleiten Verweise (z. B. `_Ty&&`) vorhanden ist *nicht* zur Optimierung der aber was Sie an Sie übergeben werden und auf transparent und effizientes weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="98e5c-225">The reason forwarding references (such as `_Ty&&`) exist is *not* for optimization, but to take what you pass to them and to forward it on transparently and efficiently.</span></span> <span data-ttu-id="98e5c-226">Sie wahrscheinlich einen Verweis Weiterleitung auftreten nur, wenn Sie Library Code schreiben (oder eng Studie)&mdash;beispielsweise eine Factory-Funktion, die auf Konstruktorargumente weiterleitet.</span><span class="sxs-lookup"><span data-stu-id="98e5c-226">You're likely to encounter a forwarding reference only if you write (or closely study) library code&mdash;for example, a factory function that forwards on constructor arguments.</span></span>

## <a name="sources"></a><span data-ttu-id="98e5c-227">Quellen</span><span class="sxs-lookup"><span data-stu-id="98e5c-227">Sources</span></span>
* <span data-ttu-id="98e5c-228">\[Stroustrup, 2013\] b Stroustrup: die Programmiersprache C++, das vierte Edition.</span><span class="sxs-lookup"><span data-stu-id="98e5c-228">\[Stroustrup, 2013\] B. Stroustrup: The C++ Programming Language, Fourth Edition.</span></span> <span data-ttu-id="98e5c-229">ISBN-Wesley.</span><span class="sxs-lookup"><span data-stu-id="98e5c-229">Addison-Wesley.</span></span> <span data-ttu-id="98e5c-230">2013.</span><span class="sxs-lookup"><span data-stu-id="98e5c-230">2013.</span></span>
