---
author: Karl-Bridge-Microsoft
pm-contact: miguelrb
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.openlocfilehash: 010663320b4011d853c53bc4121f86a14bfbfe0c
ms.sourcegitcommit: a2908889b3566882c7494dc81fa9ece7d1d19580
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2017
---
# <a name="custom-keyboard-interactions"></a><span data-ttu-id="29dd2-101">Benutzerdefinierte Tastaturinteraktionen</span><span class="sxs-lookup"><span data-stu-id="29dd2-101">Custom keyboard interactions</span></span>

<span data-ttu-id="29dd2-102">Stellen Sie in Ihren UWP-Apps umfassende und einheitliche Tastaturinteraktionen sowie benutzerdefinierte Steuerelemente für erfahrene Tastaturbenutzer und Personen mit Einschränkungen und anderen Anforderungen an die Barrierefreiheit zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="29dd2-102">Provide comprehensive and consistent keyboard interaction experiences in your UWP apps and custom controls for both keyboard power users and those with disabilities and other accessibility requirements.</span></span>

<span data-ttu-id="29dd2-103">Inhalt dieses Themas ist in erster Linie die Unterstützung von Tastatureingaben mit benutzerdefinierten Steuerelementen für UWP-Apps auf PCs.</span><span class="sxs-lookup"><span data-stu-id="29dd2-103">In this topic, our primary focus is on supporting keyboard input with custom controls for UWP apps on PCs.</span></span> <span data-ttu-id="29dd2-104">Zur Unterstützung von Werkzeugen für die Barrierefreiheit wie Windows Narrator ist jedoch eine gut konzipierte Tastatur wichtig, die auf einer Software-Tastatur basiert, wie z. B. einer Bildschirmtastatur.</span><span class="sxs-lookup"><span data-stu-id="29dd2-104">However, a well-designed keyboard experience is important for supporting accessibility tools such as Windows Narrator, using software keyboards such as the touch keyboard and the On-Screen Keyboard (OSK).</span></span>

## <a name="providing-2d-directional-inner-navigation-a-namexyfocuskeyboardnavigation"></a><span data-ttu-id="29dd2-105">Bereitstellen einer 2D gerichteten internen Navigation<a name="xyfocuskeyboardnavigation"></span><span class="sxs-lookup"><span data-stu-id="29dd2-105">Providing 2D directional inner navigation <a name="xyfocuskeyboardnavigation"></span></span>

<span data-ttu-id="29dd2-106">Verwenden Sie die Eigenschaft **XYFocusKeyboardNavigation** zur Unterstützung der 2D-direktionalen internen Navigation für benutzerdefinierte Steuerelemente und Steuerelementgruppen mit Tastatur (Pfeiltasten), Xbox-Gamepad, Steuerkreuz ((D-Pad)/linker Stick) und Xbox-Fernbedienung (D-Pad).</span><span class="sxs-lookup"><span data-stu-id="29dd2-106">Use the **XYFocusKeyboardNavigation** property to support 2D directional inner navigation of custom controls and control groups with keyboard (arrow keys), Xbox gamepad (D-pad and left stick buttons), and Xbox remote control (D-pad).</span></span>

<span data-ttu-id="29dd2-107">**HINWEIS:** Wir bezeichnen den internen Navigationsbereich eines Steuerelements bzw. einer Steuerelementgruppe als *direktionalen Bereich*.</span><span class="sxs-lookup"><span data-stu-id="29dd2-107">**NOTE** We refer to the inner navigation region of a control or control group as the *directional area*.</span></span>

<span data-ttu-id="29dd2-108">**XYFocusKeyboardNavigation** hat einen Wert vom Typ **XYFocusKeyboardNavigationMode** mit den möglichen Werten **Auto** (Standard), **Aktiviert** oder **Deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="29dd2-108">**XYFocusKeyboardNavigation** has a value of type **XYFocusKeyboardNavigationMode** with possible values of **Auto** (default), **Enabled** or **Disabled**.</span></span>

<span data-ttu-id="29dd2-109">Diese Eigenschaft wirkt sich nicht auf die Registerkartennavigation, sondern nur auf die interne Navigation der untergeordneten Elemente im Steuerelement bzw. in der Steuerelementgruppe aus.</span><span class="sxs-lookup"><span data-stu-id="29dd2-109">This property does not affect tab navigation, it only affects the inner navigation of child elements within your control or control group.</span></span> <span data-ttu-id="29dd2-110">Untergeordnete Elemente eines direktionalen Bereichs sollten nicht zur Registerkartennavigation hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="29dd2-110">Child elements of a directional area should not be included in tab navigation.</span></span>

### <a name="default-behavior"></a><span data-ttu-id="29dd2-111">Standardverhalten</span><span class="sxs-lookup"><span data-stu-id="29dd2-111">Default behavior</span></span>

<span data-ttu-id="29dd2-112">Das direktionale Gerichteter Navigationsverhalten basiert auf der Herkunft oder Vererbungshierarchie eines Elements.</span><span class="sxs-lookup"><span data-stu-id="29dd2-112">Directional navigation behavior is based on the element’s ancestry, or inheritance hierarchy.</span></span> <span data-ttu-id="29dd2-113">Wenn alle Vorgänger des Elements sich im Standardmodus befinden oder auf **Auto** gesetzt sind, wird das direktionale Navigationsverhalten für die Tastatur nicht unterstützt (Gamepads und Fernbedienungen unterstützen immer die direktionale Navigation, sofern die Option **Deaktiviert** nicht explizit festgelegt wurde).</span><span class="sxs-lookup"><span data-stu-id="29dd2-113">If all ancestors are in default mode, or set to **Auto**, directional navigation behavior is not supported for keyboard (gamepad and remote control always support directional navigation unless explicitly set to **Disabled**).</span></span>

### <a name="custom-behavior"></a><span data-ttu-id="29dd2-114">Benutzerdefiniertes Verhalten</span><span class="sxs-lookup"><span data-stu-id="29dd2-114">Custom behavior</span></span>

<span data-ttu-id="29dd2-115">Wenn diese Eigenschaft auf **Aktiviert** gesetzt wird, unterstützen die Steuerelement die interne 2D-Navigation (mithilfe Pfeiltasten auf der Tastatur) für jedes UIElement im Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="29dd2-115">Setting this property to **Enabled** lets your control support 2D inner navigation (using the keyboard arrow keys) over every UIElement within your control.</span></span>

<span data-ttu-id="29dd2-116">Bei Verwendung der Pfeiltasten auf der Tastatur ist die Navigation im direktionalen Bereich eingeschränkt (durch Drücken der Tabulatortaste wird der Fokus auf das nächste fokussierbare Element außerhalb des direktionalen Bereichs festgelegt).</span><span class="sxs-lookup"><span data-stu-id="29dd2-116">When using the keyboard arrow keys, navigation is constrained within the directional area (pressing the tab key sets focus to the next focusable element outside the directional area).</span></span>

<span data-ttu-id="29dd2-117">**HINWEIS:** Dies ist nicht der Fall, wenn Sie ein Gamepad oder eine Fernbedienung verwenden, bei dem bzw. bei der die Navigation außerhalb des direktionalen Bereichs auf dem nächsten fokussierbaren Steuerelement fortgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="29dd2-117">**NOTE** This is not the case when using a gamepad or remote, where navigation continues outside the directional area to the next focusable control.</span></span>

<span data-ttu-id="29dd2-118">Diese Eigenschaft wirkt sich nur auf die interne Navigation mit Pfeiltasten aus, nicht auf die Navigation mit der Tabulatortaste.</span><span class="sxs-lookup"><span data-stu-id="29dd2-118">This property affects only inner navigation with arrow keys, it does not affect tab key navigation.</span></span> <span data-ttu-id="29dd2-119">Bei allen Steuerelementen wird die erwartete Hierarchie für die Aktivierreihenfolge beibehalten.</span><span class="sxs-lookup"><span data-stu-id="29dd2-119">All controls maintain their expected tab order hierarchy.</span></span>

<span data-ttu-id="29dd2-120">Die folgende Abbildungzeigt drei Schaltflächen (A, B und C) in einem direktionalen Bereich und eine vierte Schaltfläche (D) außerhalb des direktionalen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="29dd2-120">The following image shows three buttons (A, B, and C) contained within a directional area and a fourth button (D) outside the directional area.</span></span>

![direktionaler Bereich](images/keyboard/directional-area.png)

*<span data-ttu-id="29dd2-122">Mit den Pfeiltasten auf der Tastatur können Sie den Fokus zwischen den Schaltflächen A-B-C, aber nicht zu D verschieben.</span><span class="sxs-lookup"><span data-stu-id="29dd2-122">Keyboard arrow keys can move focus between the buttons A-B-C, but not D</span></span>*

<span data-ttu-id="29dd2-123">Im folgenden Codebeispiel wird veranschaulicht, wie sich eine Aktivierung von **XYFocusKeyboardNavigation** auf die Navigation auswirkt.</span><span class="sxs-lookup"><span data-stu-id="29dd2-123">The following code example shows how navigation is affected when **XYFocusKeyboardNavigation** is enabled.</span></span> <span data-ttu-id="29dd2-124">In der vorherigen Abbildung liegt der anfängliche Fokus auf A und die Tabulatortaste durchläuft alle Steuerelemente (A -&gt; B- &gt;C -&gt; und wieder zurück zu D), während die Pfeiltasten auf den direktionalen Bereich beschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="29dd2-124">Using the previous image, A has initial focus and the tab key cycles through all controls (A -&gt; B -&gt; C -&gt; D and back to A) while the arrow keys are constrained to the directional area.</span></span>

```XAML
<StackPanel Orientation="Horizontal">
      <StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation="Enabled">
            <Button Content="A" />
            <Button Content="B" />
            <Button Content="C" />
      </StackPanel>
      <Button Content="D" />
</StackPanel>
```

#### <a name="override-directional-navigation"></a><span data-ttu-id="29dd2-125">Außer Kraft setzen der direktionalen Navigation</span><span class="sxs-lookup"><span data-stu-id="29dd2-125">Override directional navigation</span></span>

<span data-ttu-id="29dd2-126">Verwenden Sie die Eigenschaften XYFocusRight/XYFocusLeft/XYFocusTop/XYFocusDown, um das Standardnavigationsverhalten zu außer Kraft zu setzen.</span><span class="sxs-lookup"><span data-stu-id="29dd2-126">Use the XYFocusRight/XYFocusLeft/XYFocusTop/XYFocusDown properties to override the default navigation behaviors.</span></span>

<span data-ttu-id="29dd2-127">Hier sehen Sie dieselbe Abbildung wird im vorherigen Beispiel mit drei Schaltflächen (A, B und C) in einem direktionalen Bereich und einer vierten Schaltfläche (D) außerhalb des direktionalen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="29dd2-127">Here’s the same image as the previous example showing three buttons (A, B, and C) contained within a directional area and a fourth button (D) outside the directional area.</span></span>

![direktionaler Bereich](images/keyboard/directional-area.png)

*<span data-ttu-id="29dd2-129">Mit den Pfeiltasten auf der Tastatur können Sie den Fokus zwischen den Schaltflächen A-B-C, und nach außen zu D verschieben.</span><span class="sxs-lookup"><span data-stu-id="29dd2-129">Keyboard arrow keys can move focus between the buttons A-B-C, and out to D</span></span>*

<span data-ttu-id="29dd2-130">In diesem Codebeispiel wird veranschaulicht, wie das Standardnavigationsverhalten für die rechte Pfeiltaste außer Kraft gesetzt wird, indem zugelassen wird, dass die Pfeiltaste zu einem Steuerelement außerhalb des direktionalen Bereichs navigieren kann.</span><span class="sxs-lookup"><span data-stu-id="29dd2-130">This code example demonstrates how to override the default navigation behavior for the Right arrow key by allowing it to navigate to a control outside the directional area.</span></span> <span data-ttu-id="29dd2-131">Beachten Sie, dass Sie mit der linken Pfeiltaste nicht erneut in den direktionalen Bereich wechseln können.</span><span class="sxs-lookup"><span data-stu-id="29dd2-131">Note that the directional area cannot be re-entered using the left arrow key.</span></span>

```XAML
<StackPanel Orientation="Horizontal">
      <StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation="Enabled">
            <Button Content="A" />
            <Button Content="B" />
            <Button Content="C" XYFocusRight="{x:Bind ButtonD}" />
      </StackPanel>
      <Button Content="D" x:Name="ButtonD"/>
</StackPanel>
```

<span data-ttu-id="29dd2-132">Weitere Informationen finden Sie unter [XYFocus-Navigationsstrategien](#set-the-tab-navigation-behavior) im weiteren Verlauf dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="29dd2-132">For more detail, see [XYFocus Navigation Strategies](#set-the-tab-navigation-behavior) later in this topic.</span></span>

#### <a name="restrict-navigation-with-disabled"></a><span data-ttu-id="29dd2-133">Beschränken der Navigation mit der Option „Deaktiviert“</span><span class="sxs-lookup"><span data-stu-id="29dd2-133">Restrict navigation with Disabled</span></span>

<span data-ttu-id="29dd2-134">Legen Sie **XYFocusKeyboardNavigation** auf **Deaktiviert** fest, um die Navigation mithilfe der Pfeiltasten in einem direktionalen Bereich einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="29dd2-134">Set **XYFocusKeyboardNavigation** to **Disabled** to restrict arrow key navigation within a directional area.</span></span>

<span data-ttu-id="29dd2-135">**HINWEIS:** Das Festlegen dieser Eigenschaft wirkt sich nicht auf die Navigation per Tastatur zum Steuerelement selbst aus, sondern nur auf die untergeordneten Elemente des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="29dd2-135">**NOTE** Setting this property to does affect keyboard navigation to the control itself, just the control’s child elements.</span></span>

<span data-ttu-id="29dd2-136">Im folgenden Codebeispiel ist für das übergeordnete StackPanel **XYFocusKeyboardNavigation** auf **Aktiviert** gesetzt; für das untergeordnete Element „C“ ist **XYFocusKeyboardNavigation** auf **Deaktiviert** gesetzt.</span><span class="sxs-lookup"><span data-stu-id="29dd2-136">In the following code example, the parent StackPanel has **XYFocusKeyboardNavigation** set to **Enabled** and the child element, C, has **XYFocusKeyboardNavigation** set to **Disabled**.</span></span> <span data-ttu-id="29dd2-137">Die Navigation mit Pfeiltasten ist nur für die untergeordneten Elemente von C deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="29dd2-137">Only the child elements of C have arrow key navigation disabled.</span></span>

```XAML
<StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation="Enabled">
        <Button Content="A" />
        <Button Content="B" />
        <Button Content="C" XYFocusKeyboardNavigation="Disabled" >
            ...
        </Button>
</StackPanel>
```

#### <a name="use-nested-directional-areas"></a><span data-ttu-id="29dd2-138">Verwenden von verschachtelten direktionalen Bereichen</span><span class="sxs-lookup"><span data-stu-id="29dd2-138">Use nested directional areas</span></span>

<span data-ttu-id="29dd2-139">Sie können auf mehreren Ebenen verschachtelte direktionale Bereiche verwenden.</span><span class="sxs-lookup"><span data-stu-id="29dd2-139">You can have multiple levels of nested directional areas.</span></span> <span data-ttu-id="29dd2-140">Wenn für alle übergeordneten Elemente **XYFocusKeyboardNavigation** auf **Aktiviert** gesetzt ist, werden die Regionsgrenzen bei der Navigation mit Pfeiltasten ignoriert.</span><span class="sxs-lookup"><span data-stu-id="29dd2-140">If all parent elements have **XYFocusKeyboardNavigation** set to **Enabled**, region boundaries are ignored by arrow key navigation.</span></span>

<span data-ttu-id="29dd2-141">Diese Abbildungzeigt drei Schaltflächen (A, B und C) in einem verschachtelten direktionalen Bereich und eine vierte Schaltfläche (D) außerhalb des direktionalen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="29dd2-141">Here’s an image showing three buttons (A, B, and C) contained within a nested directional area and a fourth button (D) outside the directional area.</span></span>

![Verschachtelte direktionale Bereiche](images/keyboard/nested-directional-area.png)

*<span data-ttu-id="29dd2-143">Mit den Pfeiltasten auf der Tastatur können Sie den Fokus zwischen den Schaltflächen A-B-C, aber nicht zu D verschieben.</span><span class="sxs-lookup"><span data-stu-id="29dd2-143">Keyboard arrow keys can move focus between the buttons A-B-C, but not D</span></span>*

<span data-ttu-id="29dd2-144">In diesem Codebeispiel wird veranschaulicht, wie in verschachtelten direktionalen Bereichen die Navigation mit Pfeiltasten über Regionsgrenzen hinweg unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="29dd2-144">This code example demonstrates how to specify that nested directional areas support arrow key navigation across region boundaries.</span></span>

```XAML
<StackPanel Orientation="Horizontal">
        <StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation ="Enabled">
            <StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation ="Enabled">
                <Button Content="A" />
                <Button Content="B" />
            </StackPanel>
            <Button Content="C" />
        </StackPanel>
        <Button Content="D" />
 </StackPanel>
```

<span data-ttu-id="29dd2-145">Im Folgenden sehen Sie eine Abbildung mit vier Schaltflächen (A, B, C und D), wobei sich A und B innerhalb eines verschachtelten direktionalen Bereichs und C und D in einem anderen Bereich befinden.</span><span class="sxs-lookup"><span data-stu-id="29dd2-145">Here’s an image showing four buttons (A, B, C, and D) where A and B are contained within a nested directional area, and C and D are contained within a different area.</span></span> <span data-ttu-id="29dd2-146">Da für das übergeordnete Element **XYFocusKeyboardNavigation** auf **Deaktiviert** gesetzt ist, können die Grenzen der verschachtelten Bereiche mit den Pfeiltasten nicht überschritten werden.</span><span class="sxs-lookup"><span data-stu-id="29dd2-146">As the parent element has **XYFocusKeyboardNavigation** set to **Disabled**, the boundary of each nested area cannot be crossed using the arrow keys.</span></span>

![nichtdirektionaler Bereich](images/keyboard/non-directional-area.png)

*<span data-ttu-id="29dd2-148">Sie können mithilfe von Pfeiltasten den Fokus zwischen den Schaltflächen A-B und zwischen den Schaltflächen C-D verschieben, jedoch nicht zwischen Regionen.</span><span class="sxs-lookup"><span data-stu-id="29dd2-148">Keyboard arrow keys can move focus between buttons A-B and between buttons C-D, but not between regions</span></span>*

<span data-ttu-id="29dd2-149">In diesem Codebeispiel wird veranschaulicht, wie Sie verschachtelte direktionale Bereiche festlegen, die eine Navigation mit Pfeiltasten über Regionsgrenzen hinweg nicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="29dd2-149">This code example demonstrates how to specify nested directional areas that do not support arrow key navigation across region boundaries.</span></span>

```XAML
<StackPanel Orientation="Horizontal">
  <StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation="Enabled">
    <Button Content="A" />
    <Button Content="B" />
  </StackPanel>
  <StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation="Enabled">
    <Button Content="C" />
    <Button Content="D" />
  </StackPanel>
</StackPanel>
```

<span data-ttu-id="29dd2-150">Nachfolgend sehen Sie ein komplexeres Beispiel für verschachtelte direktionale Bereiche, wobei Folgendes gilt:</span><span class="sxs-lookup"><span data-stu-id="29dd2-150">Here’s a more complex example of nested directional areas where:</span></span>

-   <span data-ttu-id="29dd2-151">Wenn der Fokus auf A gesetzt ist, können Sie nur zu E navigieren (und umgekehrt), da es eine nichtdirektionale Bereichsgrenze gibt, die es unmöglich macht, B, C und D mit den Pfeiltasten zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="29dd2-151">if A has focus, only E can be navigated to (and vice versa) because there is a non-directional area boundary that makes B, C, and D unreachable with the arrow keys</span></span>
-   <span data-ttu-id="29dd2-152">Wenn der Fokus auf B gesetzt ist, können Sie nur zu C navigieren (und umgekehrt), da sich D außerhalb des direktionalen Bereichs befindet und die nichtdirektionale Bereichsgrenze den Zugriff auf A und E blockiert.</span><span class="sxs-lookup"><span data-stu-id="29dd2-152">If B has focus, only C can be navigated to (and vice versa) because D is outside the directional area and the non-directional area boundary blocks access to A and E</span></span>
-   <span data-ttu-id="29dd2-153">Wenn der Fokus auf D gesetzt ist, müssen Sie zum Navigieren zwischen den Steuerelementen die Tabulatortaste verwenden, da die Navigation mit Pfeiltasten nicht möglich ist.</span><span class="sxs-lookup"><span data-stu-id="29dd2-153">If D has focus, the Tab key must be used to navigate between controls as arrow key navigation is not possible</span></span>

![verschachtelte nichtdirektionale Bereiche](images/keyboard/nested-non-directional-area.png)

*<span data-ttu-id="29dd2-155">Sie können mithilfe von Pfeiltasten den Fokus zwischen den Schaltflächen A-E und zwischen den Schaltflächen B-C verschieben, jedoch nicht zwischen anderen Regionen.</span><span class="sxs-lookup"><span data-stu-id="29dd2-155">Keyboard arrow keys can move focus between buttons A-E and between buttons B-C, but not between other regions</span></span>*

<span data-ttu-id="29dd2-156">In diesem Codebeispiel wird veranschaulicht, wie Sie verschachtelte direktionale Bereiche festlegen, die eine komplexe Navigation mit Pfeiltasten über Regionsgrenzen hinweg unterstützen.</span><span class="sxs-lookup"><span data-stu-id="29dd2-156">This code example demonstrates how to specify nested directional areas that support complex arrow key navigation across region boundaries.</span></span>

```XAML
<StackPanel  Orientation="Horizontal" XYFocusKeyboardNavigation ="Enabled">
  <Button Content="A" />
    <StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation ="Disabled">
      <StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation ="Enabled">
        <Button Content="B" />
        <Button Content="C" />
      </StackPanel>
        <Button Content="D" />
    </StackPanel>
  <Button Content="E" />
</StackPanel>
```

## <a name="set-the-tab-navigation-behavior-a-nametab-navigation"></a><span data-ttu-id="29dd2-157">Legen Sie das Verhalten der Registerkartennavigation fest <a name="tab-navigation"></span><span class="sxs-lookup"><span data-stu-id="29dd2-157">Set the tab navigation behavior <a name="tab-navigation"></span></span>

<span data-ttu-id="29dd2-158">Die UIElement-Eigenschaft [TabFocusNavigation](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Controls.Control.TabNavigation) bestimmt das Verhalten der Registerkartennavigation für die gesamte zugehörige Objektstruktur (bzw. den direktionalen Bereich).</span><span class="sxs-lookup"><span data-stu-id="29dd2-158">The UIElement.[TabFocusNavigation](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Controls.Control.TabNavigation) property specifies the tab navigation behavior for its entire object tree (or directional area).</span></span>

<span data-ttu-id="29dd2-159">[TabFocusNavigation](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Controls.Control.TabNavigation) hat einen Wert vom Typ **TabFocusNavigationMode** mit den möglichen Werten **Einmal**, **Zyklus** oder **Lokal** (Standard).</span><span class="sxs-lookup"><span data-stu-id="29dd2-159">[TabFocusNavigation](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Controls.Control.TabNavigation) has a value of type **TabFocusNavigationMode** with possible values of **Once**, **Cycle,** **or Local** (default).</span></span>

<span data-ttu-id="29dd2-160">In der folgenden Abbildung wird der Fokus, abhängig von der Registerkartennavigation des direktionalen Bereichs, auf eine der folgenden Arten verschoben:</span><span class="sxs-lookup"><span data-stu-id="29dd2-160">In the following image, depending on the tab navigation of the directional area, focus is moved in the following ways:</span></span>

-   <span data-ttu-id="29dd2-161">Einmal: A, B1, C, A</span><span class="sxs-lookup"><span data-stu-id="29dd2-161">Once: A, B1, C, A</span></span>
-   <span data-ttu-id="29dd2-162">Lokal: A, B1, B2, B3, B4, B5, C, A</span><span class="sxs-lookup"><span data-stu-id="29dd2-162">Local: A, B1, B2, B3, B4, B5, C, A</span></span>
-   <span data-ttu-id="29dd2-163">Zyklus: A, B1, B2, B3, B4, B5, B1, B2, B3, B4, B5, (wobei die Bs durchlaufen werden)</span><span class="sxs-lookup"><span data-stu-id="29dd2-163">Cycle: A, B1, B2, B3, B4, B5, B1, B2, B3, B4, B5, (cycling on B’s)</span></span>

![Registerkartennavigation](images/keyboard/tab-navigation.png)

*<span data-ttu-id="29dd2-165">Fokusverhalten basierend auf dem Registerkartenmodus</span><span class="sxs-lookup"><span data-stu-id="29dd2-165">Focus behavior based on tab navigation mode</span></span>*

<span data-ttu-id="29dd2-166">Im folgenden Codebeispiel wird die Verwendung von TabFocusNavigation mit dem Modus „Einmal“ veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="29dd2-166">The following code example demonstrates using TabFocusNavigation with a mode of Once.</span></span>

```XAML
<Button Content="X" Click="OnAClick"/>
<StackPanel Orientation="Horizontal" XYFocusNavigation ="Local"
   TabFocusNavigation ="Local">
   <Button Content="A" Click="OnAClick"/>
   <StackPanel Orientation="Horizontal" TabFocusNavigation ="Once">
        <Button Content="B" Click="OnBClick"/>
        <Button Content="C" Click="OnCClick"/>
        <Button Content="D" Click="OnDClick"/>
   </StackPanel>
   <Button Content="E" Click="OnBClick"/>
</StackPanel>
```

*<span data-ttu-id="29dd2-167">Die Registerkartennavigation ist bei einem Fokus auf X: A, B, E, X</span><span class="sxs-lookup"><span data-stu-id="29dd2-167">The Tab Navigation when focus is on X is: A,B,E,X</span></span>*

#### <a name="about-tabfocusnavigation-and-tabindex"></a><span data-ttu-id="29dd2-168">Informationen zu TabFocusNavigation und TabIndex</span><span class="sxs-lookup"><span data-stu-id="29dd2-168">About TabFocusNavigation and TabIndex</span></span>

<span data-ttu-id="29dd2-169">Das Verhalten der Eigenschaft „UIElement.TabFocusNavigation“ ist mit dem Verhalten der Eigenschaft „Control.TabNavigation“ identisch, einschließlich der Funktionsweise mit TabIndex.</span><span class="sxs-lookup"><span data-stu-id="29dd2-169">The UIElement.TabFocusNavigation property has the same behavior as the Control.TabNavigation property, including how it works with TabIndex.</span></span>

<span data-ttu-id="29dd2-170">Wenn für ein Steuerelement kein TabIndex angegeben ist, weist das Framework ihm einen Indexwert zu, der über dem aktuell höchsten Indexwert liegt (und die niedrigste Priorität).</span><span class="sxs-lookup"><span data-stu-id="29dd2-170">When a control has no TabIndex specified, the framework assigns it a higher index value than the current highest index value (and the lowest priority).</span></span> <span data-ttu-id="29dd2-171">Die Unklarheit wird beseitigt, indem das erste Element in der visuellen Struktur ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="29dd2-171">It resolves the ambiguate by choosing the first element on the visual tree.</span></span> <span data-ttu-id="29dd2-172">Das Framework löst die Tabindizes nach Bereich auf.</span><span class="sxs-lookup"><span data-stu-id="29dd2-172">The framework resolves Tab indexes per scope.</span></span> <span data-ttu-id="29dd2-173">Die untergeordneten Elemente eines Steuerelements gelten als ein Bereich; wenn eines diese untergeordneten Elemente über weitere untergeordnete Elemente verfügt, sind diese Teil eines anderen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="29dd2-173">The children of a control are considered a scope, and if one of this child has children, those are part of another scope.</span></span>

<span data-ttu-id="29dd2-174">In der folgenden Abbildung wird der Fokus, abhängig von der Registerkartennavigation des direktionalen Bereichs und Tabindex der Elemente, auf eine der folgenden Arten verschoben:</span><span class="sxs-lookup"><span data-stu-id="29dd2-174">In the following image, depending on the tab navigation of the directional area and the tab index of the elements, focus is moved in the following ways:</span></span>

-   <span data-ttu-id="29dd2-175">Einmal: A, B3, C, A.</span><span class="sxs-lookup"><span data-stu-id="29dd2-175">Once: A, B3, C, A.</span></span>
-   <span data-ttu-id="29dd2-176">Lokal: A, B3, B4, B5, B1, B2, C, A.</span><span class="sxs-lookup"><span data-stu-id="29dd2-176">Local: A, B3, B4, B5, B1, B2, C, A.</span></span>
-   <span data-ttu-id="29dd2-177">Zyklus: A, B3, B4, B5, B1, B2, B3, B4, B5, B1, B2, (wobei die Bs durchlaufen werden)</span><span class="sxs-lookup"><span data-stu-id="29dd2-177">Cycle: A, B3, B4, B5, B1, B2, B3, B4, B5, B1, B2, (cycling on B’s)</span></span>

![Aktivierreihenfolge (Tabindex)](images/keyboard/tab-index.png)

*<span data-ttu-id="29dd2-179">Fokusverhalten basierend auf dem Registerkarten-Navigationsmodus und Tabindizes</span><span class="sxs-lookup"><span data-stu-id="29dd2-179">Focus behavior based on tab navigation mode and tab indexes</span></span>*

<span data-ttu-id="29dd2-180">Beachten Sie, dass der direktionale Bereich als ein Bereich eingestuft wird, und die Fokusnavigation zuerst zum Steuerelement mit der höchsten Priorität verschoben wird: B3.</span><span class="sxs-lookup"><span data-stu-id="29dd2-180">Notice how the directional area is considered a scope and how focus navigation moves to the control with the highest priority first: B3.</span></span> <span data-ttu-id="29dd2-181">Tatsächlich gibt zwei Bereiche: einen für A (direktionaler Bereich) und C sowie einen weiteren für den direktionalen Bereich.</span><span class="sxs-lookup"><span data-stu-id="29dd2-181">In fact, there are two scopes: One for A, Directional Area, and C. And another for the Directional area.</span></span> <span data-ttu-id="29dd2-182">Da der direktionale Bereich kein TabStop ist, sucht das Framework den geeignetsten Bereich und rekursiv nach allen untergeordneten Elementen.</span><span class="sxs-lookup"><span data-stu-id="29dd2-182">Because the directional area is not a TabStop, the framework switches the scope to look for the best candidate, and then recursively through any child elements.</span></span>
