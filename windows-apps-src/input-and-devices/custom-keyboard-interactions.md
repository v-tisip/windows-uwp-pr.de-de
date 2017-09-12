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
# <a name="custom-keyboard-interactions"></a>Benutzerdefinierte Tastaturinteraktionen

Stellen Sie in Ihren UWP-Apps umfassende und einheitliche Tastaturinteraktionen sowie benutzerdefinierte Steuerelemente für erfahrene Tastaturbenutzer und Personen mit Einschränkungen und anderen Anforderungen an die Barrierefreiheit zur Verfügung.

Inhalt dieses Themas ist in erster Linie die Unterstützung von Tastatureingaben mit benutzerdefinierten Steuerelementen für UWP-Apps auf PCs. Zur Unterstützung von Werkzeugen für die Barrierefreiheit wie Windows Narrator ist jedoch eine gut konzipierte Tastatur wichtig, die auf einer Software-Tastatur basiert, wie z. B. einer Bildschirmtastatur.

## <a name="providing-2d-directional-inner-navigation-a-namexyfocuskeyboardnavigation"></a>Bereitstellen einer 2D gerichteten internen Navigation<a name="xyfocuskeyboardnavigation">

Verwenden Sie die Eigenschaft **XYFocusKeyboardNavigation** zur Unterstützung der 2D-direktionalen internen Navigation für benutzerdefinierte Steuerelemente und Steuerelementgruppen mit Tastatur (Pfeiltasten), Xbox-Gamepad, Steuerkreuz ((D-Pad)/linker Stick) und Xbox-Fernbedienung (D-Pad).

**HINWEIS:** Wir bezeichnen den internen Navigationsbereich eines Steuerelements bzw. einer Steuerelementgruppe als *direktionalen Bereich*.

**XYFocusKeyboardNavigation** hat einen Wert vom Typ **XYFocusKeyboardNavigationMode** mit den möglichen Werten **Auto** (Standard), **Aktiviert** oder **Deaktiviert**.

Diese Eigenschaft wirkt sich nicht auf die Registerkartennavigation, sondern nur auf die interne Navigation der untergeordneten Elemente im Steuerelement bzw. in der Steuerelementgruppe aus. Untergeordnete Elemente eines direktionalen Bereichs sollten nicht zur Registerkartennavigation hinzugefügt werden.

### <a name="default-behavior"></a>Standardverhalten

Das direktionale Gerichteter Navigationsverhalten basiert auf der Herkunft oder Vererbungshierarchie eines Elements. Wenn alle Vorgänger des Elements sich im Standardmodus befinden oder auf **Auto** gesetzt sind, wird das direktionale Navigationsverhalten für die Tastatur nicht unterstützt (Gamepads und Fernbedienungen unterstützen immer die direktionale Navigation, sofern die Option **Deaktiviert** nicht explizit festgelegt wurde).

### <a name="custom-behavior"></a>Benutzerdefiniertes Verhalten

Wenn diese Eigenschaft auf **Aktiviert** gesetzt wird, unterstützen die Steuerelement die interne 2D-Navigation (mithilfe Pfeiltasten auf der Tastatur) für jedes UIElement im Steuerelement.

Bei Verwendung der Pfeiltasten auf der Tastatur ist die Navigation im direktionalen Bereich eingeschränkt (durch Drücken der Tabulatortaste wird der Fokus auf das nächste fokussierbare Element außerhalb des direktionalen Bereichs festgelegt).

**HINWEIS:** Dies ist nicht der Fall, wenn Sie ein Gamepad oder eine Fernbedienung verwenden, bei dem bzw. bei der die Navigation außerhalb des direktionalen Bereichs auf dem nächsten fokussierbaren Steuerelement fortgesetzt wird.

Diese Eigenschaft wirkt sich nur auf die interne Navigation mit Pfeiltasten aus, nicht auf die Navigation mit der Tabulatortaste. Bei allen Steuerelementen wird die erwartete Hierarchie für die Aktivierreihenfolge beibehalten.

Die folgende Abbildungzeigt drei Schaltflächen (A, B und C) in einem direktionalen Bereich und eine vierte Schaltfläche (D) außerhalb des direktionalen Bereichs.

![direktionaler Bereich](images/keyboard/directional-area.png)

*Mit den Pfeiltasten auf der Tastatur können Sie den Fokus zwischen den Schaltflächen A-B-C, aber nicht zu D verschieben.*

Im folgenden Codebeispiel wird veranschaulicht, wie sich eine Aktivierung von **XYFocusKeyboardNavigation** auf die Navigation auswirkt. In der vorherigen Abbildung liegt der anfängliche Fokus auf A und die Tabulatortaste durchläuft alle Steuerelemente (A -&gt; B- &gt;C -&gt; und wieder zurück zu D), während die Pfeiltasten auf den direktionalen Bereich beschränkt sind.

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

#### <a name="override-directional-navigation"></a>Außer Kraft setzen der direktionalen Navigation

Verwenden Sie die Eigenschaften XYFocusRight/XYFocusLeft/XYFocusTop/XYFocusDown, um das Standardnavigationsverhalten zu außer Kraft zu setzen.

Hier sehen Sie dieselbe Abbildung wird im vorherigen Beispiel mit drei Schaltflächen (A, B und C) in einem direktionalen Bereich und einer vierten Schaltfläche (D) außerhalb des direktionalen Bereichs.

![direktionaler Bereich](images/keyboard/directional-area.png)

*Mit den Pfeiltasten auf der Tastatur können Sie den Fokus zwischen den Schaltflächen A-B-C, und nach außen zu D verschieben.*

In diesem Codebeispiel wird veranschaulicht, wie das Standardnavigationsverhalten für die rechte Pfeiltaste außer Kraft gesetzt wird, indem zugelassen wird, dass die Pfeiltaste zu einem Steuerelement außerhalb des direktionalen Bereichs navigieren kann. Beachten Sie, dass Sie mit der linken Pfeiltaste nicht erneut in den direktionalen Bereich wechseln können.

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

Weitere Informationen finden Sie unter [XYFocus-Navigationsstrategien](#set-the-tab-navigation-behavior) im weiteren Verlauf dieses Themas.

#### <a name="restrict-navigation-with-disabled"></a>Beschränken der Navigation mit der Option „Deaktiviert“

Legen Sie **XYFocusKeyboardNavigation** auf **Deaktiviert** fest, um die Navigation mithilfe der Pfeiltasten in einem direktionalen Bereich einzuschränken.

**HINWEIS:** Das Festlegen dieser Eigenschaft wirkt sich nicht auf die Navigation per Tastatur zum Steuerelement selbst aus, sondern nur auf die untergeordneten Elemente des Steuerelements.

Im folgenden Codebeispiel ist für das übergeordnete StackPanel **XYFocusKeyboardNavigation** auf **Aktiviert** gesetzt; für das untergeordnete Element „C“ ist **XYFocusKeyboardNavigation** auf **Deaktiviert** gesetzt. Die Navigation mit Pfeiltasten ist nur für die untergeordneten Elemente von C deaktiviert.

```XAML
<StackPanel Orientation="Horizontal" XYFocusKeyboardNavigation="Enabled">
        <Button Content="A" />
        <Button Content="B" />
        <Button Content="C" XYFocusKeyboardNavigation="Disabled" >
            ...
        </Button>
</StackPanel>
```

#### <a name="use-nested-directional-areas"></a>Verwenden von verschachtelten direktionalen Bereichen

Sie können auf mehreren Ebenen verschachtelte direktionale Bereiche verwenden. Wenn für alle übergeordneten Elemente **XYFocusKeyboardNavigation** auf **Aktiviert** gesetzt ist, werden die Regionsgrenzen bei der Navigation mit Pfeiltasten ignoriert.

Diese Abbildungzeigt drei Schaltflächen (A, B und C) in einem verschachtelten direktionalen Bereich und eine vierte Schaltfläche (D) außerhalb des direktionalen Bereichs.

![Verschachtelte direktionale Bereiche](images/keyboard/nested-directional-area.png)

*Mit den Pfeiltasten auf der Tastatur können Sie den Fokus zwischen den Schaltflächen A-B-C, aber nicht zu D verschieben.*

In diesem Codebeispiel wird veranschaulicht, wie in verschachtelten direktionalen Bereichen die Navigation mit Pfeiltasten über Regionsgrenzen hinweg unterstützt wird.

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

Im Folgenden sehen Sie eine Abbildung mit vier Schaltflächen (A, B, C und D), wobei sich A und B innerhalb eines verschachtelten direktionalen Bereichs und C und D in einem anderen Bereich befinden. Da für das übergeordnete Element **XYFocusKeyboardNavigation** auf **Deaktiviert** gesetzt ist, können die Grenzen der verschachtelten Bereiche mit den Pfeiltasten nicht überschritten werden.

![nichtdirektionaler Bereich](images/keyboard/non-directional-area.png)

*Sie können mithilfe von Pfeiltasten den Fokus zwischen den Schaltflächen A-B und zwischen den Schaltflächen C-D verschieben, jedoch nicht zwischen Regionen.*

In diesem Codebeispiel wird veranschaulicht, wie Sie verschachtelte direktionale Bereiche festlegen, die eine Navigation mit Pfeiltasten über Regionsgrenzen hinweg nicht unterstützen.

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

Nachfolgend sehen Sie ein komplexeres Beispiel für verschachtelte direktionale Bereiche, wobei Folgendes gilt:

-   Wenn der Fokus auf A gesetzt ist, können Sie nur zu E navigieren (und umgekehrt), da es eine nichtdirektionale Bereichsgrenze gibt, die es unmöglich macht, B, C und D mit den Pfeiltasten zu erreichen.
-   Wenn der Fokus auf B gesetzt ist, können Sie nur zu C navigieren (und umgekehrt), da sich D außerhalb des direktionalen Bereichs befindet und die nichtdirektionale Bereichsgrenze den Zugriff auf A und E blockiert.
-   Wenn der Fokus auf D gesetzt ist, müssen Sie zum Navigieren zwischen den Steuerelementen die Tabulatortaste verwenden, da die Navigation mit Pfeiltasten nicht möglich ist.

![verschachtelte nichtdirektionale Bereiche](images/keyboard/nested-non-directional-area.png)

*Sie können mithilfe von Pfeiltasten den Fokus zwischen den Schaltflächen A-E und zwischen den Schaltflächen B-C verschieben, jedoch nicht zwischen anderen Regionen.*

In diesem Codebeispiel wird veranschaulicht, wie Sie verschachtelte direktionale Bereiche festlegen, die eine komplexe Navigation mit Pfeiltasten über Regionsgrenzen hinweg unterstützen.

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

## <a name="set-the-tab-navigation-behavior-a-nametab-navigation"></a>Legen Sie das Verhalten der Registerkartennavigation fest <a name="tab-navigation">

Die UIElement-Eigenschaft [TabFocusNavigation](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Controls.Control.TabNavigation) bestimmt das Verhalten der Registerkartennavigation für die gesamte zugehörige Objektstruktur (bzw. den direktionalen Bereich).

[TabFocusNavigation](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Controls.Control.TabNavigation) hat einen Wert vom Typ **TabFocusNavigationMode** mit den möglichen Werten **Einmal**, **Zyklus** oder **Lokal** (Standard).

In der folgenden Abbildung wird der Fokus, abhängig von der Registerkartennavigation des direktionalen Bereichs, auf eine der folgenden Arten verschoben:

-   Einmal: A, B1, C, A
-   Lokal: A, B1, B2, B3, B4, B5, C, A
-   Zyklus: A, B1, B2, B3, B4, B5, B1, B2, B3, B4, B5, (wobei die Bs durchlaufen werden)

![Registerkartennavigation](images/keyboard/tab-navigation.png)

*Fokusverhalten basierend auf dem Registerkartenmodus*

Im folgenden Codebeispiel wird die Verwendung von TabFocusNavigation mit dem Modus „Einmal“ veranschaulicht.

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

*Die Registerkartennavigation ist bei einem Fokus auf X: A, B, E, X*

#### <a name="about-tabfocusnavigation-and-tabindex"></a>Informationen zu TabFocusNavigation und TabIndex

Das Verhalten der Eigenschaft „UIElement.TabFocusNavigation“ ist mit dem Verhalten der Eigenschaft „Control.TabNavigation“ identisch, einschließlich der Funktionsweise mit TabIndex.

Wenn für ein Steuerelement kein TabIndex angegeben ist, weist das Framework ihm einen Indexwert zu, der über dem aktuell höchsten Indexwert liegt (und die niedrigste Priorität). Die Unklarheit wird beseitigt, indem das erste Element in der visuellen Struktur ausgewählt wird. Das Framework löst die Tabindizes nach Bereich auf. Die untergeordneten Elemente eines Steuerelements gelten als ein Bereich; wenn eines diese untergeordneten Elemente über weitere untergeordnete Elemente verfügt, sind diese Teil eines anderen Bereichs.

In der folgenden Abbildung wird der Fokus, abhängig von der Registerkartennavigation des direktionalen Bereichs und Tabindex der Elemente, auf eine der folgenden Arten verschoben:

-   Einmal: A, B3, C, A.
-   Lokal: A, B3, B4, B5, B1, B2, C, A.
-   Zyklus: A, B3, B4, B5, B1, B2, B3, B4, B5, B1, B2, (wobei die Bs durchlaufen werden)

![Aktivierreihenfolge (Tabindex)](images/keyboard/tab-index.png)

*Fokusverhalten basierend auf dem Registerkarten-Navigationsmodus und Tabindizes*

Beachten Sie, dass der direktionale Bereich als ein Bereich eingestuft wird, und die Fokusnavigation zuerst zum Steuerelement mit der höchsten Priorität verschoben wird: B3. Tatsächlich gibt zwei Bereiche: einen für A (direktionaler Bereich) und C sowie einen weiteren für den direktionalen Bereich. Da der direktionale Bereich kein TabStop ist, sucht das Framework den geeignetsten Bereich und rekursiv nach allen untergeordneten Elementen.
