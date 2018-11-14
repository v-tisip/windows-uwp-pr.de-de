---
author: Karl-Bridge-Microsoft
title: Fokusnavigation für Tastatur, Gamepad, Fernbedienung und Bedienungshilfen
Description: ''
label: ''
template: detail.hbs
keywords: Tastatur, Gamecontroller, Fernbedienung, Navigation, direktionale interne Navigation, direktionaler Bereich, Navigationsstrategie, Eingabe, Benutzerinteraktion, Bedienungshilfen, Verwendbarkeit
ms.date: 03/02/2018
ms.author: kbridge
ms.topic: article
pm-contact: miguelrb
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: f4c86847e02c4ba987f8b1dcc42016145b175193
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6269337"
---
# <a name="focus-navigation-for-keyboard-gamepad-remote-control-and-accessibility-tools"></a><span data-ttu-id="bbba8-103">Fokusnavigation für Tastatur, Gamepad, Fernbedienung und Bedienungshilfen</span><span class="sxs-lookup"><span data-stu-id="bbba8-103">Focus navigation for keyboard, gamepad, remote control, and accessibility tools</span></span>

![Tastatur, Fernbedienung und Steuerkreuz](images/dpad-remote/dpad-remote-keyboard.png)

<span data-ttu-id="bbba8-105">Verwenden Sie die Fokusnavigation, um umfassende und einheitliche Interaktionserfahrungen in Ihren UWP-Apps, benutzerdefinierte Steuerelemente für erfahrene Tastaturbenutzer und Personen mit Einschränkungen und anderen Anforderungen an die Barrierefreiheit sowie die 3-Meter-Erfahrung von Fernsehbildschirmen und der Xbox One bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-105">Use focus navigation to provide comprehensive and consistent interaction experiences in your UWP apps and custom controls for keyboard power users, those with disabilities and other accessibility requirements, as well as the 10-foot experience of television screens and the Xbox One.</span></span>

## <a name="overview"></a><span data-ttu-id="bbba8-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="bbba8-106">Overview</span></span>

<span data-ttu-id="bbba8-107">Fokusnavigation bezieht sich auf den zugrunde liegende Mechanismus, mit dem Benutzer mithilfe einer Tastatur, eines Gamepads oder einer Fernbedienung durch die Benutzeroberfläche einer UWP-Anwendung navigieren und mit dieser interagieren können.</span><span class="sxs-lookup"><span data-stu-id="bbba8-107">Focus navigation refers to the underlying mechanism that enables users to navigate and interact with the UI of a UWP application using a keyboard, gamepad, or remote control.</span></span>

> [!NOTE] 
> <span data-ttu-id="bbba8-108">Eingabegeräte werden in der Regel als Zeigegeräte, z.B. Toucheingabe, Touchpad, Stift und Maus, und Nicht-Zeigegeräte wie Tastatur, Gamepad und Fernbedienung klassifiziert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-108">Input devices are typically classified as pointing devices, such as touch, touchpad, pen, and mouse, and non-pointing devices, such as keyboard, gamepad, and remote control.</span></span>

<span data-ttu-id="bbba8-109">In diesem Thema wird beschrieben, wie Sie eine UWP-Anwendung optimieren und benutzerdefinierte Interaktionserfahrungen für Benutzer aufbauen, die nicht zeigenden Eingabetypen verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbba8-109">This topic describes how to optimize a UWP application and build custom interaction experiences for users that rely on non-pointing input types.</span></span> 

<span data-ttu-id="bbba8-110">Auch wenn wir uns auf Tastatureingaben für benutzerdefinierte Steuerelemente in UWP-Apps auf PCs konzentrieren, ist eine gut durchdachte Tastaturerfahrung ebenso wichtig für Softwaretastaturen wie die Touch- und Bildschirmtastatur, die Eingabehilfen wie die Windows-Sprachausgabe und die 3-Meter-Erfahrung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-110">Even though we focus on keyboard input for custom controls in UWP apps on PCs, a well-designed keyboard experience is also important for software keyboards such as the touch keyboard and the On-Screen Keyboard (OSK), supporting accessibility tools such as Windows Narrator, and supporting the 10-foot experience.</span></span>

<span data-ttu-id="bbba8-111">Anweisungen zum Entwickeln von benutzerdefinierten Erfahrungen in UWP-Anwendungen für Zeigegeräte finden Sie unter [Behandeln von Zeigereingaben](handle-pointer-input.md).</span><span class="sxs-lookup"><span data-stu-id="bbba8-111">See [Handle pointer input](handle-pointer-input.md) for guidance on building custom experiences in UWP applications for pointing devices.</span></span>

<span data-ttu-id="bbba8-112">Allgemeinere Informationen zum Erstellen von Apps und Erfahrungen für die Tastatur finden Sie unter [Tastaturinteraktion](keyboard-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="bbba8-112">For more general information on building apps and experiences for keyboard, see [Keyboard Interaction](keyboard-interactions.md).</span></span>

## <a name="general-guidance"></a><span data-ttu-id="bbba8-113">Allgemeiner Leitfaden</span><span class="sxs-lookup"><span data-stu-id="bbba8-113">General guidance</span></span>
<span data-ttu-id="bbba8-114">Nur die UI-Elemente, die eine Benutzerinteraktion erfordern, sollten die Fokusnavigation unterstützen. Elemente, für die keine Aktion erforderlich ist, z.B. statische Bilder, benötigen keinen Tastaturfokus.</span><span class="sxs-lookup"><span data-stu-id="bbba8-114">Only those UI elements that require user interaction should support focus navigation, elements that don’t require an action, such as static images, do not need keyboard focus.</span></span> <span data-ttu-id="bbba8-115">Sprachausgaben und ähnliche Bedienungshilfen geben diese statischen Elemente dennoch bekannt, auch wenn sie nicht in der Fokusnavigation enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="bbba8-115">Screen readers and similar accessibility tools still announce these static elements, even when they are not included in focus navigation.</span></span> 

<span data-ttu-id="bbba8-116">Es ist wichtig, zu beachten, dass im Gegensatz zur Navigation mit einem Zeigegerät wie einer Maus oder einer Toucheingabe die Fokusnavigation linear ist.</span><span class="sxs-lookup"><span data-stu-id="bbba8-116">It is important to remember that unlike navigating with a pointer device such as a mouse or touch, focus navigation is linear.</span></span> <span data-ttu-id="bbba8-117">Bei der Implementierung der Fokusnavigation sollten Sie überlegen, wie ein Benutzer mit Ihrer Anwendung interagiert und wie die logische Navigation aussehen sollte.</span><span class="sxs-lookup"><span data-stu-id="bbba8-117">When implementing focus navigation, consider how a user will interact with your application and what the logical navigation should be.</span></span> <span data-ttu-id="bbba8-118">In den meisten Fällen ist es empfehlenswert, das Verhalten der benutzerdefinierten Fokusnavigation an das bevorzugte Lesemuster der Kultur des Benutzers anzupassen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-118">In most cases, we recommend custom focus navigation behavior follows the preferred reading pattern of the user's culture.</span></span>

<span data-ttu-id="bbba8-119">Folgende Überlegungen zur Fokusnavigation müssen ebenfalls berücksichtigt werden:</span><span class="sxs-lookup"><span data-stu-id="bbba8-119">Some other focus navigation considerations include:</span></span>
- <span data-ttu-id="bbba8-120">Sind Steuerelemente logisch gruppiert?</span><span class="sxs-lookup"><span data-stu-id="bbba8-120">Are controls grouped logically?</span></span>
- <span data-ttu-id="bbba8-121">Gibt es Gruppen von Steuerelementen mit größerer Bedeutung?</span><span class="sxs-lookup"><span data-stu-id="bbba8-121">Are there groups of controls with greater importance?</span></span> 
   - <span data-ttu-id="bbba8-122">Falls ja, enthalten diese Gruppen Untergruppen?</span><span class="sxs-lookup"><span data-stu-id="bbba8-122">If yes, do those groups contain sub-groups?</span></span>
- <span data-ttu-id="bbba8-123">Sind für das Layout eine benutzerdefinierte direktionale Navigation (Pfeiltasten) und eine Aktivierreihenfolge erforderlich?</span><span class="sxs-lookup"><span data-stu-id="bbba8-123">Does the layout require custom directional navigation (arrow keys) and tab order?</span></span>

<span data-ttu-id="bbba8-124">Das E-Book [Entwickeln von barrierefreier Software](https://www.microsoft.com/download/details.aspx?id=19262) enthält ein hervorragendes Kapitel zum Thema *Entwerfen der logischen Hierarchie*.</span><span class="sxs-lookup"><span data-stu-id="bbba8-124">The [Engineering Software for Accessibility](https://www.microsoft.com/download/details.aspx?id=19262) eBook has an excellent chapter on *Designing the Logical Hierarchy*.</span></span>

## <a name="2d-directional-navigation-for-keyboard"></a><span data-ttu-id="bbba8-125">Direktionale 2D-Navigation für die Tastatur</span><span class="sxs-lookup"><span data-stu-id="bbba8-125">2D directional navigation for keyboard</span></span>

<span data-ttu-id="bbba8-126">Der interne 2D-Navigationsbereich eines Steuerelements oder einer Steuerelementgruppe wird als „direktionaler Bereich“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="bbba8-126">The 2D inner navigation region of a control, or control group, is referred to as its "directional area".</span></span> <span data-ttu-id="bbba8-127">Wenn der Fokus auf dieses Objekt verschoben wird, können die Pfeiltasten der Tastatur (links, rechts, oben und unten) verwendet werden, um zwischen untergeordneten Elementen im direktionalen Bereich zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="bbba8-127">When focus shifts to this object, the keyboard arrow keys (left, right, up, and down) can be used to navigate between child elements within the directional area.</span></span>

![direktionaler Bereich](images/keyboard/directional-area-small.png)

*<span data-ttu-id="bbba8-129">Interner 2D-Navigationsbereich oder direktionaler Bereich einer Steuerelementgruppe</span><span class="sxs-lookup"><span data-stu-id="bbba8-129">2D Inner navigation region, or directional area, of a control group</span></span>*

<span data-ttu-id="bbba8-130">Die können die Eigenschaft [XYFocusKeyboardNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_XYFocusKeyboardNavigation) (mit den möglichen Werten [Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode), [Enabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode) oder [Disabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode)) verwenden, um die interne 2D-Navigation mit den Pfeiltasten der Tastatur zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="bbba8-130">You can use the [XYFocusKeyboardNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_XYFocusKeyboardNavigation) property (which has possible values of [Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode), [Enabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode), or [Disabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode)) to manage 2D inner navigation with the keyboard arrow keys.</span></span>

> [!NOTE]  
> <span data-ttu-id="bbba8-131">Die Aktivierreihenfolge ist von dieser Eigenschaft nicht betroffen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-131">Tab order is not affected by this property.</span></span> <span data-ttu-id="bbba8-132">Um eine unübersichtliche Navigationserfahrung zu vermeiden, sollten untergeordnete Elemente eines direktionalen Bereichs *nicht* ausdrücklich in der Aktivierreihenfolge der Navigation Ihrer Anwendung angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="bbba8-132">To avoid a confusing navigation experience, we recommend that child elements of a directional area *not* be explicitly specified in the tab navigation order of your application.</span></span> <span data-ttu-id="bbba8-133">Weitere Informationen zum Verhalten der Aktivierreihenfolge für ein Element finden Sie unter den Eigenschaften [UIElement.TabFocusNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_TabFocusNavigation) und [TabIndex](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabIndex).</span><span class="sxs-lookup"><span data-stu-id="bbba8-133">See the [UIElement.TabFocusNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_TabFocusNavigation) and [TabIndex](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabIndex) properties for more detail on tabbing behavior for an element.</span></span>  

### <a name="autohttpsdocsmicrosoftcomuwpapiwindowsuixamlinputxyfocuskeyboardnavigationmode-default-behavior"></a><span data-ttu-id="bbba8-134">[Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode) (Standardverhalten)</span><span class="sxs-lookup"><span data-stu-id="bbba8-134">[Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode) (default behavior)</span></span>

<span data-ttu-id="bbba8-135">Bei Festlegung auf Auto wird das Verhalten der direktionalen Navigation von der Herkunft oder Vererbungshierarchie eines Elements bestimmt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-135">When set to Auto, directional navigation behavior is determined by the element’s ancestry, or inheritance hierarchy.</span></span> <span data-ttu-id="bbba8-136">Wenn sich alle Vorgänger im Standardmodus (Festlegung auf **Auto**) befinden, wird die direktionale Navigation mit der Tastatur *nicht* unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-136">If all ancestors are in default mode (set to **Auto**), directional navigation with the keyboard is *not* supported.</span></span>

### [<a name="disabled"></a><span data-ttu-id="bbba8-137">Disabled</span><span class="sxs-lookup"><span data-stu-id="bbba8-137">Disabled</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode)

<span data-ttu-id="bbba8-138">Legen Sie **XYFocusKeyboardNavigation** auf **Disabled** fest, um die direktionale Navigation für das Steuerelement und seine untergeordneten Elemente zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="bbba8-138">Set **XYFocusKeyboardNavigation** to **Disabled** to block directional navigation to the control and its child elements.</span></span>

![XYFocusKeyboardNavigation-Verhalten deaktiviert](images/keyboard/xyfocuskeyboardnav-disabled.gif)

*<span data-ttu-id="bbba8-140">XYFocusKeyboardNavigation-Verhalten deaktiviert</span><span class="sxs-lookup"><span data-stu-id="bbba8-140">XYFocusKeyboardNavigation disabled behavior</span></span>*

<span data-ttu-id="bbba8-141">In diesem Beispiel ist beim primären [StackPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.StackPanel) (ContainerPrimary) für **XYFocusKeyboardNavigation** der Wert **Enabled** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-141">In this example, the primary [StackPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.StackPanel) (ContainerPrimary) has **XYFocusKeyboardNavigation** set to **Enabled**.</span></span> <span data-ttu-id="bbba8-142">Alle untergeordneten Elemente erben diese Einstellung, und Sie können mit den Pfeiltasten zu diesen navigieren.</span><span class="sxs-lookup"><span data-stu-id="bbba8-142">All child elements inherit this setting, and can be navigated to with the arrow keys.</span></span> <span data-ttu-id="bbba8-143">Die Elemente B3 und B4 befinden sich jedoch in einem sekundären [StackPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.StackPanel) (ContainerSecondary), für den **XYFocusKeyboardNavigation** auf **Disabled** festgelegt wurde, wodurch der primäre Container überschrieben und die Pfeiltastennavigation zu sich selbst und zwischen den untergeordneten Elementen deaktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-143">However, the B3 and B4 elements are in a secondary [StackPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.StackPanel) (ContainerSecondary) with **XYFocusKeyboardNavigation** set to **Disabled**, which overrides the primary container and disables arrow key navigation to itself and between its child elements.</span></span>

```XAML
<Grid 
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}" 
    TabFocusNavigation="Cycle">
    <Grid.RowDefinitions>
        <RowDefinition Height="40"/>
        <RowDefinition Height="75"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <TextBlock Name="KeyPressed"
                Grid.Row="0" 
                FontWeight="ExtraBold" 
                HorizontalTextAlignment="Center"
                TextWrapping="Wrap" 
                Padding="10" />
    <StackPanel Name="ContainerPrimary" 
                XYFocusKeyboardNavigation="Enabled" 
                KeyDown="ContainerPrimary_KeyDown" 
                Orientation="Horizontal" 
                BorderBrush="Green" 
                BorderThickness="2" 
                Grid.Row="1" 
                Padding="10" 
                MaxWidth="200">
        <Button Name="B1" 
                Content="B1" 
                GettingFocus="Btn_GettingFocus" />
        <Button Name="B2" 
                Content="B2" 
                GettingFocus="Btn_GettingFocus" />
        <StackPanel Name="ContainerSecondary" 
                    XYFocusKeyboardNavigation="Disabled" 
                    Orientation="Horizontal" 
                    BorderBrush="Red" 
                    BorderThickness="2">
            <Button Name="B3" 
                    Content="B3" 
                    GettingFocus="Btn_GettingFocus" />
            <Button Name="B4" 
                    Content="B4" 
                    GettingFocus="Btn_GettingFocus" />
        </StackPanel>
    </StackPanel>
</Grid>
```

### [<a name="enabled"></a><span data-ttu-id="bbba8-144">Enabled</span><span class="sxs-lookup"><span data-stu-id="bbba8-144">Enabled</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocuskeyboardnavigationmode)

<span data-ttu-id="bbba8-145">Legen Sie **XYFocusKeyboardNavigation** auf **Enabled** fest, um die direktionale 2D-Navigation zu einem Steuerelement und jedem seiner untergeordneten [UIElement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement)-Objekte zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-145">Set **XYFocusKeyboardNavigation** to **Enabled** to support 2D directional navigation to a control and each of its [UIElement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement) child objects.</span></span>

<span data-ttu-id="bbba8-146">Bei Festlegung ist die Navigation mit den Pfeiltasten auf Elemente innerhalb des direktionalen Bereichs beschränkt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-146">When set, navigation with the arrow keys is restricted to elements within the directional area.</span></span> <span data-ttu-id="bbba8-147">Die TAB-Navigation ist nicht betroffen, da alle Steuerelemente über eine Hierarchie für die Aktivierreihenfolge zugänglich bleiben.</span><span class="sxs-lookup"><span data-stu-id="bbba8-147">Tab navigation is not affected, as all controls remain accessible through their tab order hierarchy.</span></span>

![XYFocusKeyboardNavigation-Verhalten aktiviert](images/keyboard/xyfocuskeyboardnav-enabled.gif)

*<span data-ttu-id="bbba8-149">XYFocusKeyboardNavigation-Verhalten aktiviert</span><span class="sxs-lookup"><span data-stu-id="bbba8-149">XYFocusKeyboardNavigation enabled behavior</span></span>*

<span data-ttu-id="bbba8-150">In diesem Beispiel ist beim primären [StackPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.StackPanel) (ContainerPrimary) für **XYFocusKeyboardNavigation** der Wert **Enabled** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-150">In this example, the primary [StackPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.StackPanel) (ContainerPrimary) has **XYFocusKeyboardNavigation** set to **Enabled**.</span></span> <span data-ttu-id="bbba8-151">Alle untergeordneten Elemente erben diese Einstellung, und Sie können mit den Pfeiltasten zu diesen navigieren.</span><span class="sxs-lookup"><span data-stu-id="bbba8-151">All child elements inherit this setting, and can be navigated to with the arrow keys.</span></span> <span data-ttu-id="bbba8-152">Die Elemente B3 und B4 befinden sich in einem sekundären [StackPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.StackPanel) (ContainerSecondary), in dem **XYFocusKeyboardNavigation** nicht festgelegt ist und dann die Einstellung des primären Containers erbt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-152">The B3 and B4 elements are in a secondary [StackPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.StackPanel) (ContainerSecondary) where **XYFocusKeyboardNavigation** is not set, which then inherits the primary container setting.</span></span> <span data-ttu-id="bbba8-153">Das Element B5 befindet sich nicht in einem deklarierten direktionalen Bereich und bietet keine Unterstützung für die Pfeiltastennavigation, unterstützt jedoch das Standardverhalten für die TAB-Navigation.</span><span class="sxs-lookup"><span data-stu-id="bbba8-153">The B5 element is not within a declared directional area, and does not support arrow key navigation but does support standard tab navigation behavior.</span></span>

```xaml
<Grid
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
    TabFocusNavigation="Cycle">
    <Grid.RowDefinitions>
        <RowDefinition Height="40"/>
        <RowDefinition Height="100"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <TextBlock Name="KeyPressed"
               Grid.Row="0"
               FontWeight="ExtraBold"
               HorizontalTextAlignment="Center"
               TextWrapping="Wrap"
               Padding="10" />
    <StackPanel Grid.Row="1"
                Orientation="Horizontal"
                HorizontalAlignment="Center">
        <StackPanel Name="ContainerPrimary"
                    XYFocusKeyboardNavigation="Enabled"
                    KeyDown="ContainerPrimary_KeyDown"
                    Orientation="Horizontal"
                    BorderBrush="Green"
                    BorderThickness="2"
                    Padding="5" Margin="5">
            <Button Name="B1"
                    Content="B1"
                    GettingFocus="Btn_GettingFocus" Margin="5" />
            <Button Name="B2"
                    Content="B2"
                    GettingFocus="Btn_GettingFocus" />
            <StackPanel Name="ContainerSecondary"
                        Orientation="Horizontal"
                        BorderBrush="Red"
                        BorderThickness="2"
                        Margin="5">
                <Button Name="B3"
                        Content="B3"
                        GettingFocus="Btn_GettingFocus"
                        Margin="5" />
                <Button Name="B4"
                        Content="B4"
                        GettingFocus="Btn_GettingFocus"
                        Margin="5" />
            </StackPanel>
        </StackPanel>
        <Button Name="B5"
                Content="B5"
                GettingFocus="Btn_GettingFocus"
                Margin="5" />
    </StackPanel>
</Grid>
```

<span data-ttu-id="bbba8-154">Sie können auf mehreren Ebenen verschachtelte direktionale Bereiche verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbba8-154">You can have multiple levels of nested directional areas.</span></span> <span data-ttu-id="bbba8-155">Wenn für alle übergeordneten Elemente XYFocusKeyboardNavigation auf Aktiviert gesetzt ist, werden die Regionsgrenzen bei der internen Navigation ignoriert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-155">If all parent elements have XYFocusKeyboardNavigation set to Enabled, inner navigation region boundaries are ignored.</span></span>

<span data-ttu-id="bbba8-156">Im Folgenden sehen Sie ein Beispiel für zwei geschachtelte direktionale Bereiche innerhalb eines Elements, das die direktionale 2D-Navigation nicht ausdrücklich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-156">Here's an example of two nested directional areas within an element that does not explicitly support 2D directional navigation.</span></span> <span data-ttu-id="bbba8-157">In diesem Fall wird direktionale Navigation zwischen den zwei geschachtelten Bereichen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-157">In this case, directional navigation is not supported between the two nested areas.</span></span>

![Verhalten bei aktivierter und verschachtelter XYFocusKeyboardNavigation](images/keyboard/xyfocuskeyboardnav-enabled-nested1.gif)

*<span data-ttu-id="bbba8-159">Verhalten bei aktivierter und verschachtelter XYFocusKeyboardNavigation</span><span class="sxs-lookup"><span data-stu-id="bbba8-159">XYFocusKeyboardNavigation enabled and nested behavior</span></span>*

<span data-ttu-id="bbba8-160">Nachfolgend sehen Sie ein komplexeres Beispiel für drei verschachtelte direktionale Bereiche, wobei Folgendes gilt:</span><span class="sxs-lookup"><span data-stu-id="bbba8-160">Here’s a more complex example of three nested directional areas where:</span></span>

-   <span data-ttu-id="bbba8-161">Wenn der Fokus auf B1 gesetzt ist, können Sie nur zu B5 navigieren (und umgekehrt), da es eine direktionale Bereichsgrenze gibt, in der XYFocusKeyboardNavigation auf Disabled festgelegt ist, die es unmöglich macht, B2, B3 und B4 mit den Pfeiltasten zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-161">When B1 has focus, only B5 can be navigated to (and vice versa) because there is a directional area boundary where XYFocusKeyboardNavigation set to Disabled, making B2, B3, and B4 unreachable with the arrow keys</span></span>
-   <span data-ttu-id="bbba8-162">Wenn der Fokus auf B2 gesetzt ist, können Sie nur zu B3 navigieren (und umgekehrt), da die direktionale Bereichsgrenze die Navigation mit den Pfeiltasten zu B1, B4 und B5 verhindert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-162">When B2 has focus, only B3 can be navigated to (and vice versa) because the directional area boundary prevents arrow key navigation to B1, B4, and B5</span></span>
-   <span data-ttu-id="bbba8-163">Wenn der Fokus auf B4 gesetzt ist, muss die TAB-Taste verwendet werden, um zwischen Steuerelementen zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="bbba8-163">When B4 has focus, the Tab key must be used to navigate between controls</span></span>

![Verhalten bei aktivierter und komplex verschachtelter XYFocusKeyboardNavigation](images/keyboard/xyfocuskeyboardnav-enabled-nested2.gif)

*<span data-ttu-id="bbba8-165">Verhalten bei aktivierter und komplex verschachtelter XYFocusKeyboardNavigation</span><span class="sxs-lookup"><span data-stu-id="bbba8-165">XYFocusKeyboardNavigation enabled and complex nested behavior</span></span>*

## <a name="tab-navigation"></a><span data-ttu-id="bbba8-166">TAB-Navigation</span><span class="sxs-lookup"><span data-stu-id="bbba8-166">Tab navigation</span></span>

<span data-ttu-id="bbba8-167">Während die Pfeiltasten für die direktionale 2D-Navigation innerhalb eines Steuerelements oder einer Steuerelementgruppe verwendet werden können, können Sie mit der TAB-Taste zwischen allen Steuerelementen in einer UWP-Anwendung navigieren.</span><span class="sxs-lookup"><span data-stu-id="bbba8-167">While the arrow keys can be used for 2D directional navigation witin a control, or control group, the Tab key can be used to navigate between all controls in a UWP application.</span></span> 

<span data-ttu-id="bbba8-168">Alle interaktiven Steuerelemente unterstützen standardmäßig die Navigation mit der TAB-Taste (Eigenschaften [IsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_IsEnabled) und [IsTabStop](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_IsTabStop) sind ist auf **true** festgelegt), wobei die logische TAB-Reihenfolge aus dem Steuerelementlayout in der Anwendung abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-168">All interactive controls support Tab key navigation by default ([IsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_IsEnabled) and [IsTabStop](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_IsTabStop) property are **true**), with the logical tab order derived from the control layout in your application.</span></span> <span data-ttu-id="bbba8-169">Die Standardreihenfolge ist jedoch nicht notwendigerweise mit der visuellen Reihenfolge identisch.</span><span class="sxs-lookup"><span data-stu-id="bbba8-169">However, the default order does not necessarily correspond to the visual order.</span></span> <span data-ttu-id="bbba8-170">Die tatsächliche Anzeigeposition kann vom übergeordneten Layoutcontainer und bestimmten Eigenschaften abhängen, die Sie für die untergeordneten Elemente festlegen können, um das Layout zu beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-170">The actual display position might depend on the parent layout container and certain properties that you can set on the child elements to influence the layout.</span></span>

<span data-ttu-id="bbba8-171">Vermeiden Sie eine benutzerdefinierte Aktivierreihenfolge, durch die der Fokus in Ihrer Anwendung wechselt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-171">Avoid a custom tab order that makes the focus jump around in your application.</span></span> <span data-ttu-id="bbba8-172">Beispielsweise sollte eine Liste mit Steuerelementen in einem Formular eine Aktivierreihenfolge aufweisen, die von oben nach unten und von links nach rechts (je nach Gebietsschema) verläuft.</span><span class="sxs-lookup"><span data-stu-id="bbba8-172">For example, a list of controls in a form should have a tab order that flows from top to bottom and left to right (depending on locale).</span></span>

<span data-ttu-id="bbba8-173">In diesem Abschnitt wird beschrieben, wie diese Aktivierreihenfolge vollständig an Ihre App angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="bbba8-173">In this section we describe how this tab order can be fully customized to suit your app.</span></span>

### <a name="set-the-tab-navigation-behavior"></a><span data-ttu-id="bbba8-174">Festlegen des Verhaltens der TAB-Navigation</span><span class="sxs-lookup"><span data-stu-id="bbba8-174">Set the tab navigation behavior</span></span>

<span data-ttu-id="bbba8-175">Die Eigenschaft [TabFocusNavigation](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_TabFocusNavigation) von [UIElement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement) bestimmt das Verhalten der TAB-Navigation für die gesamte zugehörige Objektstruktur (bzw. den direktionalen Bereich).</span><span class="sxs-lookup"><span data-stu-id="bbba8-175">The [TabFocusNavigation](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_TabFocusNavigation) property of [UIElement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement) specifies the tab navigation behavior for its entire object tree (or directional area).</span></span>

> [!NOTE]
> <span data-ttu-id="bbba8-176">Verwenden Sie diese Eigenschaft anstelle der Eigenschaft [Control.TabNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabNavigation) für Objekte, die Ihr Erscheinungsbild nicht über eine [ControlTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.controltemplate) definieren.</span><span class="sxs-lookup"><span data-stu-id="bbba8-176">Use this property instead of the [Control.TabNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabNavigation) property for objects that do not use a [ControlTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.controltemplate) to define their appearance.</span></span>

<span data-ttu-id="bbba8-177">Wie im vorherigen Abschnitt erwähnt, sollten untergeordnete Elemente eines direktionalen Bereichs *nicht* ausdrücklich in der Aktivierreihenfolge der Navigation Ihrer Anwendung angegeben werden, um eine unübersichtliche Navigationserfahrung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="bbba8-177">As we mentioned in the previous section, to avoid a confusing navigation experience, we recommend that child elements of a directional area *not* be explicitly specified in the tab navigation order of your application.</span></span> <span data-ttu-id="bbba8-178">Weitere Informationen zum Verhalten der Aktivierreihenfolge für ein Element finden Sie unter den Eigenschaften [UIElement.TabFocusNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_TabFocusNavigation) und [TabIndex](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabIndex).</span><span class="sxs-lookup"><span data-stu-id="bbba8-178">See the [UIElement.TabFocusNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_TabFocusNavigation) and the [TabIndex](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabIndex) properties for more detail on tabbing behavior for an element.</span></span>   
> <span data-ttu-id="bbba8-179">Für Versionen vor Windows10 Creators Update (Build 10.0.15063) waren TAB-Einstellungen auf [ControlTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.controltemplate)-Objekte beschränkt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-179">For versions older than Windows 10 Creators Update (build 10.0.15063), tab settings were limited to [ControlTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.controltemplate) objects.</span></span> <span data-ttu-id="bbba8-180">Weitere Informationen finden Sie unter [Control.TabNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabNavigation).</span><span class="sxs-lookup"><span data-stu-id="bbba8-180">For more info, see [Control.TabNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabNavigation).</span></span>

<span data-ttu-id="bbba8-181">[TabFocusNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_TabFocusNavigation) hat einen Wert vom Typ [KeyboardNavigationMode](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardnavigationmode) mit den folgenden möglichen Werten (beachten Sie, dass diese Beispiele keine benutzerdefinierten Steuerelementgruppen sind und keine interne Navigation mit den Pfeiltasten erfordern):</span><span class="sxs-lookup"><span data-stu-id="bbba8-181">[TabFocusNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_TabFocusNavigation) has a value of type [KeyboardNavigationMode](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardnavigationmode) with the following possible values (note that these examples are not custom control groups and do not require inner navigation with the arrow keys):</span></span>

- <span data-ttu-id="bbba8-182">**Local** (Standard)</span><span class="sxs-lookup"><span data-stu-id="bbba8-182">**Local** (default)</span></span>   
  <span data-ttu-id="bbba8-183">Tabindizes werden für die lokale Unterstruktur innerhalb des Containers erkannt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-183">Tab indexes are recognized on the local subtree inside the container.</span></span> <span data-ttu-id="bbba8-184">In diesem Beispiel ist die Aktivierreihenfolge B1, B2, B3, B4, B5, B6, B7, B1.</span><span class="sxs-lookup"><span data-stu-id="bbba8-184">For this example, the tab order is B1, B2, B3, B4, B5, B6, B7, B1.</span></span>

   ![Verhalten bei der TAB-Navigation mit der Option „Local“](images/keyboard/tabnav-local.gif)

   *<span data-ttu-id="bbba8-186">Verhalten bei der TAB-Navigation mit der Option „Local“</span><span class="sxs-lookup"><span data-stu-id="bbba8-186">"Local" tab navigation behavior</span></span>*

- **<span data-ttu-id="bbba8-187">Once</span><span class="sxs-lookup"><span data-stu-id="bbba8-187">Once</span></span>**  
  <span data-ttu-id="bbba8-188">Der Fokus wird einmal auf den Container und alle untergeordneten Elemente gesetzt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-188">The container and all child elements receive focus once.</span></span> <span data-ttu-id="bbba8-189">In diesem Beispiel ist die Aktivierreihenfolge B1, B2, B7, B1 (die interne Navigation mit Pfeiltasten wird ebenfalls gezeigt).</span><span class="sxs-lookup"><span data-stu-id="bbba8-189">For this example, the tab order is B1, B2, B7, B1 (inner navigation with arrow key is also demonstrated).</span></span>

   ![Verhalten bei der TAB-Navigation mit der Option „Once“](images/keyboard/tabnav-once.gif)

   *<span data-ttu-id="bbba8-191">Verhalten bei der TAB-Navigation mit der Option „Once“</span><span class="sxs-lookup"><span data-stu-id="bbba8-191">"Once" tab navigation behavior</span></span>*

- **<span data-ttu-id="bbba8-192">Cycle</span><span class="sxs-lookup"><span data-stu-id="bbba8-192">Cycle</span></span>**   
  <span data-ttu-id="bbba8-193">Der Fokus wird wieder auf das erste fokussierbare Element in einem Container gesetzt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-193">Focus cycles back to the initial focusable element inside a container.</span></span> <span data-ttu-id="bbba8-194">In diesem Beispiel ist die Aktivierreihenfolge B1, B2, B3, B4, B5, B6, B2...</span><span class="sxs-lookup"><span data-stu-id="bbba8-194">For this example, the tab order is B1, B2, B3, B4, B5, B6, B2...</span></span>

   ![Verhalten bei der TAB-Navigation mit der Option „Cycle“](images/keyboard/tabnav-cycle.gif)

   *<span data-ttu-id="bbba8-196">Verhalten bei der TAB-Navigation mit der Option „Cycle“</span><span class="sxs-lookup"><span data-stu-id="bbba8-196">"Cycle" tab navigation behavior</span></span>*

<span data-ttu-id="bbba8-197">Im Folgenden sehen Sie den Code für die vorherigen Beispiele (mit TabFocusNavigation = Cycle).</span><span class="sxs-lookup"><span data-stu-id="bbba8-197">Here's the code for the preceding examples (with TabFocusNavigation ="Cycle").</span></span>

```XAML
<Grid 
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}" 
    TabFocusNavigation="Cycle">
    <Grid.RowDefinitions>
        <RowDefinition Height="40"/>
        <RowDefinition Height="300"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <TextBlock Name="KeyPressed"
               Grid.Row="0" 
               FontWeight="ExtraBold" 
               HorizontalTextAlignment="Center"
               TextWrapping="Wrap" 
               Padding="10" />
    <StackPanel Name="ContainerPrimary"
                KeyDown="Container_KeyDown" 
                Orientation="Horizontal" 
                HorizontalAlignment="Center"
                BorderBrush="Green" 
                BorderThickness="2" 
                Grid.Row="1" 
                Padding="10" 
                MaxWidth="200">
        <Button Name="B1" 
                Content="B1" 
                GettingFocus="Btn_GettingFocus" 
                Margin="5"/>
        <StackPanel Name="ContainerSecondary" 
                    KeyDown="Container_KeyDown"
                    XYFocusKeyboardNavigation="Enabled" 
                    TabFocusNavigation ="Cycle"
                    Orientation="Vertical" 
                    VerticalAlignment="Center"
                    BorderBrush="Red" 
                    BorderThickness="2"
                    Padding="5" Margin="5">
            <Button Name="B2" 
                    Content="B2" 
                    GettingFocus="Btn_GettingFocus" 
                    Margin="5"/>
            <Button Name="B3" 
                    Content="B3" 
                    GettingFocus="Btn_GettingFocus" 
                    Margin="5"/>
            <Button Name="B4" 
                    Content="B4" 
                    GettingFocus="Btn_GettingFocus" 
                    Margin="5"/>
            <Button Name="B5" 
                    Content="B5" 
                    GettingFocus="Btn_GettingFocus" 
                    Margin="5"/>
            <Button Name="B6" 
                    Content="B6" 
                    GettingFocus="Btn_GettingFocus" 
                    Margin="5"/>
        </StackPanel>
        <Button Name="B7" 
                Content="B7" 
                GettingFocus="Btn_GettingFocus" 
                Margin="5"/>
    </StackPanel>
</Grid>
```

### [<a name="tabindex"></a><span data-ttu-id="bbba8-198">TabIndex</span><span class="sxs-lookup"><span data-stu-id="bbba8-198">TabIndex</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabIndex)

<span data-ttu-id="bbba8-199">Verwenden Sie [TabIndex](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabIndex), um die Reihenfolge anzugeben, in der der Fokus auf Elemente gesetzt wird, wenn der Benutzer mithilfe der TAB-Taste durch Steuerelemente navigiert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-199">Use [TabIndex](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabIndex) to specify the order in which elements receive focus when the user navigates through controls using the Tab key.</span></span> <span data-ttu-id="bbba8-200">Auf ein Steuerelement mit einem niedrigeren Tabindex wird der Fokus vor einem Steuerelement mit einem höheren Index gesetzt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-200">A control with a lower tab index receives focus before a control with a higher index.</span></span>

<span data-ttu-id="bbba8-201">Wenn für ein Steuerelement kein [TabIndex](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_TabIndex) angegeben ist, wird ihm ein Indexwert zugewiesen, der über dem aktuell höchsten Indexwert (und der niedrigsten Priorität) aller interaktiven Steuerelemente in der visuellen Struktur basierend auf dem Bereich liegt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-201">When a control has no [TabIndex](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_TabIndex) specified, it is assigned a higher index value than the current highest index value (and the lowest priority) of all interactive controls in the visual tree, based on scope.</span></span> 

<span data-ttu-id="bbba8-202">Alle untergeordneten Elemente eines Steuerelements gelten als ein Bereich; wenn eins dieser Elemente über weitere untergeordnete Elemente verfügt, werden diese als ein anderer Bereich betrachtet.</span><span class="sxs-lookup"><span data-stu-id="bbba8-202">All child elements of a control are considered a scope, and if one of these elements also has child elements, they are considered another scope.</span></span> <span data-ttu-id="bbba8-203">Alle Unklarheiten werden beseitigt, indem das erste Element in der visuellen Struktur des Bereichs ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-203">Any ambiguity is resolved by choosing the first element on the visual tree of the scope.</span></span> 

<span data-ttu-id="bbba8-204">Um ein Steuerelement aus der Aktivierreihenfolge auszuschließen, legen Sie die Eigenschaft [IsTabStop](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_IsTabStop) auf **false** fest.</span><span class="sxs-lookup"><span data-stu-id="bbba8-204">To exclude a control from the tab order, set the [IsTabStop](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_IsTabStop) property to **false**.</span></span>

<span data-ttu-id="bbba8-205">Überschreiben Sie die Standardaktivierreihenfolge, indem Sie die Eigenschaft [TabIndex](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_TabIndex) festlegen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-205">Override the default tab order by setting the [TabIndex](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_TabIndex) property.</span></span>

> [!NOTE] 
> <span data-ttu-id="bbba8-206">[TabIndex](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_TabIndex) funktioniert mit [UIElement.TabFocusNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_TabFocusNavigation) und [Control.TabNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabNavigation) auf dieselbe Weise.</span><span class="sxs-lookup"><span data-stu-id="bbba8-206">[TabIndex](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_TabIndex) works the same way with both [UIElement.TabFocusNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_TabFocusNavigation) and [Control.TabNavigation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_TabNavigation).</span></span>


<span data-ttu-id="bbba8-207">Im Folgenden sehen Sie, wie die Fokusnavigation von der Eigenschaft [TabIndex](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_TabIndex) für bestimmte Elemente beeinflusst wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-207">Here, we show how focus navigation can be affected by the [TabIndex](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_TabIndex) property on specific elements.</span></span> 

![Verhalten bei der TAB-Navigation mit der Option „Local“ und TabIndex](images/keyboard/tabnav-tabindex.gif)

*<span data-ttu-id="bbba8-209">Verhalten bei der TAB-Navigation mit der Option „Local“ und TabIndex</span><span class="sxs-lookup"><span data-stu-id="bbba8-209">"Local" tab navigation with TabIndex behavior</span></span>*

<span data-ttu-id="bbba8-210">Im vorherigen Beispiel gibt es zwei Bereiche:</span><span class="sxs-lookup"><span data-stu-id="bbba8-210">In the preceding example, there are two scopes:</span></span> 
- <span data-ttu-id="bbba8-211">B1, direktionaler Bereich (B2–B6) und B7</span><span class="sxs-lookup"><span data-stu-id="bbba8-211">B1, directional area (B2 - B6), and B7</span></span>
- <span data-ttu-id="bbba8-212">direktionaler Bereich (B2–B6)</span><span class="sxs-lookup"><span data-stu-id="bbba8-212">directional area (B2 - B6)</span></span>

<span data-ttu-id="bbba8-213">Wenn der Fokus auf B3 (im direktionalen Bereich) gesetzt wird, ändert sich der Bereich und die TAB-Navigation überträgt an den direktionalen Bereich, in dem der beste Kandidat für einen nachfolgenden Fokus identifiziert wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-213">When B3 (in the directional area) gets focus, the scope changes and tab navigation transfers to the directional area where the best candidate for subsequent focus is identified.</span></span> <span data-ttu-id="bbba8-214">In diesem Fall heißt das B2, gefolgt von B4, B5 und B6.</span><span class="sxs-lookup"><span data-stu-id="bbba8-214">In this case, B2 followed by B4, B5, and B6.</span></span> <span data-ttu-id="bbba8-215">Der Bereich ändert sich dann erneut, und der Fokus verschiebt sich auf B1.</span><span class="sxs-lookup"><span data-stu-id="bbba8-215">Scope then changes again, and focus moves to B1.</span></span>

<span data-ttu-id="bbba8-216">Hier sehen Sie den Code für dieses Beispiel.</span><span class="sxs-lookup"><span data-stu-id="bbba8-216">Here's the code for this example.</span></span>

```xaml
<Grid
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
    TabFocusNavigation="Cycle">
    <Grid.RowDefinitions>
        <RowDefinition Height="40"/>
        <RowDefinition Height="300"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <TextBlock Name="KeyPressed"
               Grid.Row="0"
               FontWeight="ExtraBold"
               HorizontalTextAlignment="Center"
               TextWrapping="Wrap"
               Padding="10" />
    <StackPanel Name="ContainerPrimary"
                KeyDown="Container_KeyDown"
                Orientation="Horizontal"
                HorizontalAlignment="Center"
                BorderBrush="Green"
                BorderThickness="2"
                Grid.Row="1"
                Padding="10"
                MaxWidth="200">
        <Button Name="B1"
                Content="B1"
                TabIndex="1"
                ToolTipService.ToolTip="TabIndex = 1"
                GettingFocus="Btn_GettingFocus"
                Margin="5"/>
        <StackPanel Name="ContainerSecondary"
                    KeyDown="Container_KeyDown"
                    TabFocusNavigation ="Local"
                    Orientation="Vertical"
                    VerticalAlignment="Center"
                    BorderBrush="Red"
                    BorderThickness="2"
                    Padding="5" Margin="5">
            <Button Name="B2"
                    Content="B2"
                    GettingFocus="Btn_GettingFocus"
                    Margin="5"/>
            <Button Name="B3"
                    Content="B3"
                    TabIndex="3"
                    ToolTipService.ToolTip="TabIndex = 3"
                    GettingFocus="Btn_GettingFocus"
                    Margin="5"/>
            <Button Name="B4"
                    Content="B4"
                    GettingFocus="Btn_GettingFocus"
                    Margin="5"/>
            <Button Name="B5"
                    Content="B5"
                    GettingFocus="Btn_GettingFocus"
                    Margin="5"/>
            <Button Name="B6"
                    Content="B6"
                    GettingFocus="Btn_GettingFocus"
                    Margin="5"/>
        </StackPanel>
        <Button Name="B7"
                Content="B7"
                TabIndex="2"
                ToolTipService.ToolTip="TabIndex = 2"
                GettingFocus="Btn_GettingFocus"
                Margin="5"/>
    </StackPanel>
</Grid>
```

## <a name="2d-directional-navigation-for-keyboard-gamepad-and-remote-control"></a><span data-ttu-id="bbba8-217">Direktionale 2D-Navigation für Tastatur, Gamepad und Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="bbba8-217">2D directional navigation for keyboard, gamepad, and remote control</span></span>

<span data-ttu-id="bbba8-218">Nicht zeigerorientierte Eingabetypen wie Tastatur, Gamepad, Fernbedienung und Bedienungshilfen wie die Windows-Sprachausgabe teilen Sie einen gemeinsamen zugrunde liegende Mechanismus für die Navigation und Interaktion mit der Benutzeroberfläche Ihrer UWP-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="bbba8-218">Non-pointer input types such as keyboard, gamepad, remote control, and accessibility tools like Windows Narrator, share a common, underlying mechanism for navigating and interacting with the UI of your UWP application.</span></span>

<span data-ttu-id="bbba8-219">In diesem Abschnitt wird erläutert, wie Sie eine bevorzugte Navigationsstrategie angeben und die Fokusnavigation in Ihrer Anwendung durch eine Reihe von Navigationsstrategieeigenschaften optimieren, die alle fokusbasierten, nicht zeigerorientierten Eingabetypen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-219">In this section, we cover how to specify a preferred navigation strategy and fine tune focus navigation within your application through a set of navigation strategy properties that support all focus-based, non-pointer input types.</span></span>

<span data-ttu-id="bbba8-220">Allgemeinere Informationen zum Erstellen von Apps und Erfahrungen für Xbox/TV finden Sie unter [Tastaturinteraktion](keyboard-interactions.md) und [Entwerfen für Xbox und Fernsehgeräte](../devices/designing-for-tv.md#xy-focus-navigation-and-interaction).</span><span class="sxs-lookup"><span data-stu-id="bbba8-220">For more general information on building apps and experiences for Xbox/TV, see [Keyboard Interaction](keyboard-interactions.md) and [Designing for Xbox and TV](../devices/designing-for-tv.md#xy-focus-navigation-and-interaction).</span></span>

### <a name="navigation-strategies"></a><span data-ttu-id="bbba8-221">Navigationsstrategien</span><span class="sxs-lookup"><span data-stu-id="bbba8-221">Navigation Strategies</span></span>

> <span data-ttu-id="bbba8-222">Navigationsstrategien gelten für Tastatur, Gamepad, Fernbedienung und verschiedene Bedienungshilfen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-222">Navigation strategies are applicable to keyboard, gamepad, remote control, and various accessibility tools.</span></span>

<span data-ttu-id="bbba8-223">Mit den folgenden Navigationsstrategieeigenschaften können Sie beeinflussen, auf welches Steuerelement der Fokus gesetzt wird, wenn eine Pfeiltaste, eine Steuerkreuztaste oder ähnliches gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-223">The following navigation strategy properties let you influence which control receives focus based on the arrow key, directional pad (D-pad) button, or similar pressed.</span></span> 

-   <span data-ttu-id="bbba8-224">XYFocusUpNavigationStrategy</span><span class="sxs-lookup"><span data-stu-id="bbba8-224">XYFocusUpNavigationStrategy</span></span>
-   <span data-ttu-id="bbba8-225">XYFocusDownNavigationStrategy</span><span class="sxs-lookup"><span data-stu-id="bbba8-225">XYFocusDownNavigationStrategy</span></span>
-   <span data-ttu-id="bbba8-226">XYFocusLeftNavigationStrategy</span><span class="sxs-lookup"><span data-stu-id="bbba8-226">XYFocusLeftNavigationStrategy</span></span>
-   <span data-ttu-id="bbba8-227">XYFocusRightNavigationStrategy</span><span class="sxs-lookup"><span data-stu-id="bbba8-227">XYFocusRightNavigationStrategy</span></span>

<span data-ttu-id="bbba8-228">Diese Eigenschaften können die Werte [Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocusnavigationstrategy) (Standard), [NavigationDirectionDistance](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocusnavigationstrategy), [Projection](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocusnavigationstrategy) oder [RectilinearDistance ](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocusnavigationstrategy)aufweisen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-228">These properties have possible values of [Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocusnavigationstrategy) (default), [NavigationDirectionDistance](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocusnavigationstrategy), [Projection](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocusnavigationstrategy), or [RectilinearDistance ](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.xyfocusnavigationstrategy).</span></span>

<span data-ttu-id="bbba8-229">Wenn **Auto** festgelegt wird, basiert das Verhalten des Elements auf den Vorgängern des Elements.</span><span class="sxs-lookup"><span data-stu-id="bbba8-229">If set to **Auto**, the behavior of the element is based on the ancestors of the element.</span></span> <span data-ttu-id="bbba8-230">Wenn alle Elemente auf **Auto** festgelegt werden, wird **Projection** verwendet.</span><span class="sxs-lookup"><span data-stu-id="bbba8-230">If all elements are set to **Auto**, **Projection** is used.</span></span>

> [!NOTE]
> <span data-ttu-id="bbba8-231">Andere Faktoren, wie das zuvor fokussierte Element oder die Nähe zur Achse der Navigationsrichtung, können das Ergebnis beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="bbba8-231">Other factors, such as the previously focused element or proximity to the axis of the navigation direction, can influence the result.</span></span>

### <a name="projection"></a><span data-ttu-id="bbba8-232">Projection</span><span class="sxs-lookup"><span data-stu-id="bbba8-232">Projection</span></span>

<span data-ttu-id="bbba8-233">Die Projection-Strategie verlagert den Fokus auf das erste Element, das beim *Projizieren* des Rands des aktuell fokussierten Elements in der Navigationsrichtung aufgefunden wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-233">The Projection strategy moves focus to the first element encountered when the edge of the currently focused element is *projected* in the direction of navigation.</span></span>

<span data-ttu-id="bbba8-234">In diesem Beispiel ist jede Fokusnavigationsrichtung auf Projection festgelegt.</span><span class="sxs-lookup"><span data-stu-id="bbba8-234">In this example, each focus navigation direction is set to Projection.</span></span> <span data-ttu-id="bbba8-235">Beachten Sie, wie sich der Fokus von B1 bis B4 nach unten verschiebt, wobei B3 umgangen wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-235">Notice how focus moves down from B1 to B4, bypassing B3.</span></span> <span data-ttu-id="bbba8-236">Das liegt daran, dass sich B3 nicht in der Projektionszone befindet.</span><span class="sxs-lookup"><span data-stu-id="bbba8-236">This is because, B3 is not in the projection zone.</span></span> <span data-ttu-id="bbba8-237">Beachten Sie außerdem, wie ein Fokuskandidat beim Verschieben nach links von B1 nicht identifiziert wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-237">Also notice how a focus candidate is not identified when moving left from B1.</span></span> <span data-ttu-id="bbba8-238">Das liegt daran, dass die relative Position von B2 zu B1 B3 als Kandidat eliminiert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-238">This is because the position of B2 relative to B1 eliminates B3 as a candidate.</span></span> <span data-ttu-id="bbba8-239">Wenn sich B3 in derselben Zeile wie B2 befinden würde, wäre es ein geeigneter Kandidat für die linke Navigation.</span><span class="sxs-lookup"><span data-stu-id="bbba8-239">If B3 was in the same row as B2, it would be a viable candidate for left navigation.</span></span> <span data-ttu-id="bbba8-240">B2 ist ein geeigneter Kandidat aufgrund der uneingeschränkten Nähe zur Achse der Navigationsrichtung.</span><span class="sxs-lookup"><span data-stu-id="bbba8-240">B2 is a viable candidate due to its unobstructed proximity to the axis of navigation direction.</span></span>

![Projection-Navigationsstrategie](images/keyboard/xyfocusnavigationstrategy-projection.gif)

*<span data-ttu-id="bbba8-242">Projection-Navigationsstrategie</span><span class="sxs-lookup"><span data-stu-id="bbba8-242">Projection navigation strategy</span></span>*

### <a name="navigationdirectiondistance"></a><span data-ttu-id="bbba8-243">NavigationDirectionDistance</span><span class="sxs-lookup"><span data-stu-id="bbba8-243">NavigationDirectionDistance</span></span>

<span data-ttu-id="bbba8-244">Die NavigationDirectionDistance-Strategie verlagert den Fokus auf das Element, das sich am nächsten zur Achse der Navigationsrichtung befindet.</span><span class="sxs-lookup"><span data-stu-id="bbba8-244">The NavigationDirectionDistance strategy moves focus to the element closest to the axis of the navigation direction.</span></span>

<span data-ttu-id="bbba8-245">Der Rand des umgebenden Rechtecks, das der Richtung der Navigation entspricht, wird *erweitert* und *projiziert*, um Kandidatenziele zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="bbba8-245">The edge of the bounding rect corresponding to the navigation direction is *extended* and *projected* to identify candidate targets.</span></span> <span data-ttu-id="bbba8-246">Das erste gefundene Element wird als Ziel identifiziert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-246">The first element encountered is identified as the target.</span></span> <span data-ttu-id="bbba8-247">Wenn mehrere Kandidaten vorhanden sind, wird das nächste Element als Ziel identifiziert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-247">In the case of multiple candidates, the closest element is identified as the target.</span></span> <span data-ttu-id="bbba8-248">Sind weiterhin mehrere Kandidaten vorhanden, wird das oberste/ganz linke Element als der Kandidat identifiziert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-248">If there are still multiple candidates, the topmost/leftmost element is identified as the candidate.</span></span>

![NavigationDirectionDistance-Navigationsstrategie](images/keyboard/xyfocusnavigationstrategy-navigationdirectiondistance.gif)

*<span data-ttu-id="bbba8-250">NavigationDirectionDistance-Navigationsstrategie</span><span class="sxs-lookup"><span data-stu-id="bbba8-250">NavigationDirectionDistance navigation strategy</span></span>*

### <a name="rectilineardistance"></a><span data-ttu-id="bbba8-251">RectilinearDistance</span><span class="sxs-lookup"><span data-stu-id="bbba8-251">RectilinearDistance</span></span>

<span data-ttu-id="bbba8-252">Die RectilinearDistance-Strategie verlagert den Fokus zum nächsten Element basierend auf dem gradlinigen 2D-Abstand ([Manhattan-Metrik](https://en.wikipedia.org/wiki/Taxicab_geometry)).</span><span class="sxs-lookup"><span data-stu-id="bbba8-252">The RectilinearDistance strategy moves focus to the closest element based on 2D rectilinear distance ([Taxicab geometry](https://en.wikipedia.org/wiki/Taxicab_geometry)).</span></span>

<span data-ttu-id="bbba8-253">Der beste Kandidat wird durch Hinzufügen des primären und sekundären Abstands zu jedem möglichen Kandidaten identifiziert.</span><span class="sxs-lookup"><span data-stu-id="bbba8-253">The sum of the primary distance and the secondary distance to each potential candidate is used to identify the best candidtate.</span></span> <span data-ttu-id="bbba8-254">Bei einem Gleichstand wird das erste Element links ausgewählt, wenn die angeforderte Richtung oben oder unten ist, oder das erste Element oben ausgewählt, wenn die angeforderte Richtung links oder rechts ist.</span><span class="sxs-lookup"><span data-stu-id="bbba8-254">In a tie, the first element to the left is selected if the requested direction is up or down, and the first element to the top is selected if the requested direction is left or right.</span></span>

![RectilinearDistance-Navigationsstrategie](images/keyboard/xyfocusnavigationstrategy-rectilineardistance.gif)

*<span data-ttu-id="bbba8-256">RectilinearDistance-Navigationsstrategie</span><span class="sxs-lookup"><span data-stu-id="bbba8-256">RectilinearDistance navigation strategy</span></span>*

<span data-ttu-id="bbba8-257">Diese Abbildung zeigt, dass B3 der RectilinearDistance-Fokuskandidat ist, wenn der Fokus auf B1 gesetzt ist und eine Richtung nach unten angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="bbba8-257">This image shows how, when B1 has focus and down is the requested direction, B3 is the RectilinearDistance focus candidate.</span></span> <span data-ttu-id="bbba8-258">Das basiert auf den folgenden Berechnungen für dieses Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bbba8-258">This is based on the following calcualations for this example:</span></span>
-   <span data-ttu-id="bbba8-259">Abstand (B1, B3, nach unten) = 10 + 0 = 10</span><span class="sxs-lookup"><span data-stu-id="bbba8-259">Distance (B1, B3, Down) is 10 + 0 = 10</span></span>
-   <span data-ttu-id="bbba8-260">Abstand (B1, B2, nach unten) = 0 + 40 = 30</span><span class="sxs-lookup"><span data-stu-id="bbba8-260">Distance (B1, B2, Down) is 0 + 40 = 30</span></span>
-   <span data-ttu-id="bbba8-261">Abstand (B1, D, nach unten) = 30 + 0 = 30</span><span class="sxs-lookup"><span data-stu-id="bbba8-261">Distance (B1, D, Down) is 30 + 0 = 30</span></span>


## <a name="related-articles"></a><span data-ttu-id="bbba8-262">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bbba8-262">Related articles</span></span>
- [<span data-ttu-id="bbba8-263">Programmgesteuerte Fokusnavigation</span><span class="sxs-lookup"><span data-stu-id="bbba8-263">Programmatic focus navigation</span></span>](focus-navigation-programmatic.md)
- [<span data-ttu-id="bbba8-264">Tastaturinteraktionen</span><span class="sxs-lookup"><span data-stu-id="bbba8-264">Keyboard interactions</span></span>](keyboard-interactions.md)
- [<span data-ttu-id="bbba8-265">Barrierefreiheit der Tastaturnavigation</span><span class="sxs-lookup"><span data-stu-id="bbba8-265">Keyboard accessibility</span></span>](../accessibility/keyboard-accessibility.md) 



