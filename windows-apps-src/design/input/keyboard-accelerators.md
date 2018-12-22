---
Description: Learn how accelerator keys can improve the usability and accessibility of UWP apps.
title: Zugriffstasten
label: Keyboard accelerators
template: detail.hbs
keywords: Tastatur, Zugriffstaste, Zugriffstasten, Tastenkombinationen, Barrierefreiheit, Navigation, Fokus, Text, Eingabe, Benutzerinteraktionen, Gamepad, Fernbedienung
ms.date: 10/10/2017
ms.topic: article
pm-contact: chigy
design-contact: miguelrb
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 7e898b0552a9485cd15079a37940a2151e4bc9f9
ms.sourcegitcommit: 2ef3d22a30afe853de891280e11d96e5e1ab62d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2018
ms.locfileid: "8981879"
---
# <a name="keyboard-accelerators"></a><span data-ttu-id="4021f-103">Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-103">Keyboard accelerators</span></span>

![Surface Tastatur](images/accelerators/accelerators_hero2.png)

<span data-ttu-id="4021f-105">Zugriffstasten (oder Tastaturkürzel) sind Tastenkombinationen, die die Benutzerfreundlichkeit und Barrierefreiheit Ihrer Windows-Anwendungen verbessern, indem Sie eine intuitive Möglichkeit für Benutzer bereitstellen, häufige Aktionen oder Befehle aufzurufen, ohne die App-Benutzeroberfläche zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4021f-105">Accelerator keys (or keyboard accelerators) are keyboard shortcuts that improve the usability and accessibility of your Windows applications by providing an intuitive way for users to invoke common actions or commands without navigating the app UI.</span></span>

<span data-ttu-id="4021f-106">Weitere Details über die Navigation der Benutzeroberfläche einer Windows-Anwendung mit Tastenkombinationen finden Sie im Thema [Zugriffstasten](access-keys.md).</span><span class="sxs-lookup"><span data-stu-id="4021f-106">See the [Access keys](access-keys.md) topic for details on navigating the UI of a Windows application with keyboard shortcuts.</span></span>

> [!NOTE]
> <span data-ttu-id="4021f-107">Eine Tastatur ist unentbehrlich für Benutzer mit bestimmten körperlichen Einschränkungen (siehe [Barrierefreiheit der Tastaturnavigation](https://docs.microsoft.com/windows/uwp/accessibility/keyboard-accessibility)) und auch ein wichtiges Tool für Benutzer, die effizienter mit einer App interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="4021f-107">A keyboard is indispensable for users with certain disabilities (see [Keyboard accessibility](https://docs.microsoft.com/windows/uwp/accessibility/keyboard-accessibility)), and is also an important tool for users who prefer it as a more efficient way to interact with an app.</span></span>

## <a name="overview"></a><span data-ttu-id="4021f-108">Übersicht</span><span class="sxs-lookup"><span data-stu-id="4021f-108">Overview</span></span>

<span data-ttu-id="4021f-109">Zugriffstasten umfassen generell die Funktionstasten F1 bis F12 oder eine Kombination aus einer Standardtaste zusammen mit einer oder mehreren Zusatztasten (STRG, UMSCHALTTASTE).</span><span class="sxs-lookup"><span data-stu-id="4021f-109">Accelerators typically include the function keys F1 through F12 or some combination of a standard key paired with one or more modifier keys (CTRL, Shift).</span></span>

> [!NOTE]
> <span data-ttu-id="4021f-110">Die UWP-Plattform-Steuerelemente verfügen über integrierte Zugriffstasten.</span><span class="sxs-lookup"><span data-stu-id="4021f-110">The UWP platform controls have built-in keyboard accelerators.</span></span> <span data-ttu-id="4021f-111">ListView unterstützt beispielsweise STRG+A zum Auswählen aller Elemente der Liste und RichEditBox unterstützt STRG+TAB zum Einfügen eines Tabstopps in das Textfeld.</span><span class="sxs-lookup"><span data-stu-id="4021f-111">For example, ListView supports Ctrl+A for selecting all the items in the list, and RichEditBox supports Ctrl+Tab for inserting a Tab in the text box.</span></span> <span data-ttu-id="4021f-112">Diese integrierten Zugriffstasten werden als **Steuerungsabkürzungen** bezeichnet und werden nur ausgeführt, wenn der Fokus auf einem Element oder einem seiner untergeordneten Elemente liegt.</span><span class="sxs-lookup"><span data-stu-id="4021f-112">These built-in keyboard accelerators are referred to as **control accelerators** and are executed only if the focus is on the element or one of its children.</span></span> <span data-ttu-id="4021f-113">Von Ihnen definierte Zugriffstaste, die mithilfe der hier erläuterten Zugriffstasten APIs verwendet werden, werden als **App-Zugriffstasten** bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="4021f-113">Accelerators defined by you using the keyboard accelerator APIs discussed here are referred to as **app accelerators**.</span></span>

<span data-ttu-id="4021f-114">Zugriffstasten sind nicht für jede Aktion verfügbar, gehören allerdings häufig zu Befehlen, die in Menüs verfügbar gemacht werden (und sollten im Inhalt des Menüelements angegeben werden).</span><span class="sxs-lookup"><span data-stu-id="4021f-114">Keyboard accelerators are not available for every action but are often associated with commands exposed in menus (and should be specified with the menu item content).</span></span><span data-ttu-id="4021f-115">Zugriffstasten können ebenfalls Aktionen zugeordnet werden, die nicht über entsprechende Menüelemente verfügen.</span><span class="sxs-lookup"><span data-stu-id="4021f-115">Accelerators can also be associated with actions that do not have equivalent menu items.</span></span> <span data-ttu-id="4021f-116">Da der Benutzer von den Menüs der Anwendungen abhängt, um den verfügbaren Befehlssatz zu ermitteln und zu erfahren, sollten Sie die Ermittlung der Zugriffstasten so einfach wie möglich machen (die Verwendung von Beschriftungen oder festgelegten Mustern kann dabei hilfreich sein).</span><span class="sxs-lookup"><span data-stu-id="4021f-116">However, because users rely on an application's menus to discover and learn the available command set, you should try to make discovery of accelerators as easy as possible (using labels or established patterns can help with this).</span></span>

![In einer Menüelementbeschriftungen beschriebene Zugriffstasten](images/accelerators/accelerators_menuitemlabel.png)  
*<span data-ttu-id="4021f-118">In einer Menüelementbeschriftungen beschriebene Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-118">Keyboard accelerators described in a menu item label</span></span>*

## <a name="when-to-use-keyboard-accelerators"></a><span data-ttu-id="4021f-119">Verwendung von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-119">When to use keyboard accelerators</span></span>

<span data-ttu-id="4021f-120">Es wird empfohlen, dass Sie Zugriffstasten überall in Ihrer UI angegeben, wo dies sinnvoll ist, und Zugriffstasten für alle benutzerdefinierten Steuerelemente unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4021f-120">We recommend that you specify keyboard accelerators wherever appropriate in your UI, and support accelerators in all custom controls.</span></span>

- <span data-ttu-id="4021f-121">Zugriffstasten machen Ihre app mehr Accessiblefor Benutzer mit motorischen Einschränkungen, einschließlich der Benutzer, die jeweils nur eine Taste drücken können oder Probleme bei der Verwendung einer Zugriff \*</span><span class="sxs-lookup"><span data-stu-id="4021f-121">Keyboard accelerators make your app more accessiblefor users with motor disabilities, including those users who can press only one key at a time or have difficulty using a mouse.\*\*</span></span>

  <span data-ttu-id="4021f-122">Eine gut durchdachte Tastatur-UI ist ein wichtiger Aspekt für die Barrierefreiheit von Software.</span><span class="sxs-lookup"><span data-stu-id="4021f-122">A well-designed keyboard UI is an important aspect of software accessibility.</span></span> <span data-ttu-id="4021f-123">Sie ermöglicht es Benutzern mit einer Sehbeeinträchtigung oder mit bestimmten motorischen Einschränkungen, in einer App zu navigieren und mit deren Features zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="4021f-123">It enables users with vision impairments or who have certain motor disabilities to navigate an app and interact with its features.</span></span> <span data-ttu-id="4021f-124">Diese Benutzer können u.U. keine Maus bedienen und sind auf verschiedene Hilfstechnologien wie etwa Tastaturerweiterungstools, Bildschirmtastaturen, Bildschirmlupen, Bildschirmleseprogramme oder die Möglichkeit der Spracheingabe angewiesen.</span><span class="sxs-lookup"><span data-stu-id="4021f-124">Such users might not be able to operate a mouse and instead rely on various assistive technologies such as keyboard enhancement tools, on-screen keyboards, screen enlargers, screen readers, and voice input utilities.</span></span> <span data-ttu-id="4021f-125">Für diese Benutzer ist eine vollständige Befehlsabdeckung entscheidend.</span><span class="sxs-lookup"><span data-stu-id="4021f-125">For these users, comprehensive command coverage is crucial.</span></span>

- <span data-ttu-id="4021f-126">Zugriffstasten machen Ihre app mehr Usablefor erfahrene Benutzer, die über die Tastatur interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="4021f-126">Keyboard accelerators make your app more usablefor power users who prefer to interact through the keyboard.</span></span>

  <span data-ttu-id="4021f-127">Erfahrene Benutzer haben oftmals eine starke Vorliebe für die Verwendung der Tastatur, da tastaturbasierte Befehle viel schneller eingegeben werden können. Zudem ist es dafür nicht erforderlich, die Hände von der Tastatur wegzubewegen.</span><span class="sxs-lookup"><span data-stu-id="4021f-127">Experienced users often have a strong preference for using the keyboard because keyboard-based commands can be entered more quickly and don't require them to remove their hands from the keyboard.</span></span> <span data-ttu-id="4021f-128">Für diese Benutzer sind Effizienz und Konsistenz entscheidend. Die Vollständigkeit hingegen ist nur für am häufigsten verwendeten Befehle wichtig.</span><span class="sxs-lookup"><span data-stu-id="4021f-128">For these users, efficiency and consistency are crucial; comprehensiveness is important only for the most frequently used commands.</span></span>

## <a name="specify-a-keyboard-accelerator"></a><span data-ttu-id="4021f-129">Angeben einer Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="4021f-129">Specify a keyboard accelerator</span></span>

<span data-ttu-id="4021f-130">Verwenden Sie die [KeyboardAccelerator](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.input.keyboardaccelerator.-ctor)-APIs zum Erstellen von Zugriffstasten in UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="4021f-130">Use the [KeyboardAccelerator](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.input.keyboardaccelerator.-ctor) APIs to create keyboard accelerators in UWP apps.</span></span> <span data-ttu-id="4021f-131">Mit diesen APIs müssen Sie keine verschiedenen KeyDown-Ereignisse behandeln, um die gedrückte Tastenkombination zu entdecken, und Sie können die Zugriffstasten in ihren App-Ressourcen lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="4021f-131">With these APIs, you don't have to handle multiple KeyDown events to detect the key combination pressed, and you can localize accelerators in the app resources.</span></span>

<span data-ttu-id="4021f-132">Es wird empfohlen, dass Sie Zugriffstasten für die am häufigsten verwendeten Aktionen in Ihrer App festlegen und sie mit den Bezeichnungen des Menüelements oder durch QuickInfos dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="4021f-132">We recommend that you set keyboard accelerators for the most common actions in your app and document them using the menu item label or tooltip.</span></span> <span data-ttu-id="4021f-133">In diesem Beispiel deklarieren wir Zugriffstasten nur für die Befehle „Umbenennen” und „Kopieren”.</span><span class="sxs-lookup"><span data-stu-id="4021f-133">In this example, we declare keyboard accelerators only for the Rename and Copy commands.</span></span>

``` xaml
<CommandBar Margin="0,200" AccessKey="M">
  <AppBarButton 
    Icon="Share" 
    Label="Share" 
    Click="OnShare" 
    AccessKey="S" />
  <AppBarButton 
    Icon="Copy" 
    Label="Copy" 
    ToolTipService.ToolTip="Copy (Ctrl+C)" 
    Click="OnCopy" 
    AccessKey="C">
    <AppBarButton.KeyboardAccelerators>
      <KeyboardAccelerator 
        Modifiers="Control" 
        Key="C" />
    </AppBarButton.KeyboardAccelerators>
  </AppBarButton>

  <AppBarButton 
    Icon="Delete" 
    Label="Delete" 
    Click="OnDelete" 
    AccessKey="D" />
  <AppBarSeparator/>
  <AppBarButton 
    Icon="Rename" 
    Label="Rename" 
    ToolTipService.ToolTip="Rename (F2)" 
    Click="OnRename" 
    AccessKey="R">
    <AppBarButton.KeyboardAccelerators>
      <KeyboardAccelerator 
        Modifiers="None" Key="F2" />
    </AppBarButton.KeyboardAccelerators>
  </AppBarButton>

  <AppBarButton 
    Icon="SelectAll" 
    Label="Select" 
    Click="OnSelect" 
    AccessKey="A" />
  
  <CommandBar.SecondaryCommands>
    <AppBarButton 
      Icon="OpenWith" 
      Label="Sources" 
      AccessKey="S">
      <AppBarButton.Flyout>
        <MenuFlyout>
          <ToggleMenuFlyoutItem Text="OneDrive" />
          <ToggleMenuFlyoutItem Text="Contacts" />
          <ToggleMenuFlyoutItem Text="Photos"/>
          <ToggleMenuFlyoutItem Text="Videos"/>
        </MenuFlyout>
      </AppBarButton.Flyout>
    </AppBarButton>
    <AppBarToggleButton 
      Icon="Save" 
      Label="Auto Save" 
      IsChecked="True" 
      AccessKey="A"/>
  </CommandBar.SecondaryCommands>

</CommandBar>
```

![In einer QuickInfo beschriebene Zugriffstasten](images/accelerators/accelerators_tooltip.png)  
***<span data-ttu-id="4021f-135">In einer QuickInfo beschriebene Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-135">Keyboard accelerator described in a tooltip</span></span>***

<span data-ttu-id="4021f-136">Das [UIElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement)-Objekt verfügt über eine Sammlung an [Zugriffstasten](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator), d. h. [Zugriffstasten](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.KeyboardAccelerators), über die Sie Ihre benutzerdefinierten Zugriffstasten-Objekte angeben und die Tastenkombinationen für die Zugriffstaste festlegen:</span><span class="sxs-lookup"><span data-stu-id="4021f-136">The [UIElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) object has a [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator) collection, [KeyboardAccelerators](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.KeyboardAccelerators), where you specify your custom KeyboardAccelerator objects and define the keystrokes for the keyboard accelerator:</span></span>

-   <span data-ttu-id="4021f-137">**[Taste](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Key)** : ‑ der für die Zugriffstaste verwendete [VirtualKey](https://docs.microsoft.com/uwp/api/windows.system.virtualkey).</span><span class="sxs-lookup"><span data-stu-id="4021f-137">**[Key](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Key)** - the [VirtualKey](https://docs.microsoft.com/uwp/api/windows.system.virtualkey) used for the keyboard accelerator.</span></span>

-   <span data-ttu-id="4021f-138">**[Zusatztasten](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Modifiers)** : ‑ die für die Zugriffstaste verwendeten [VirtualKeyModifiers](https://docs.microsoft.com/uwp/api/windows.system.virtualkeymodifiers).</span><span class="sxs-lookup"><span data-stu-id="4021f-138">**[Modifiers](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Modifiers)** – the [VirtualKeyModifiers](https://docs.microsoft.com/uwp/api/windows.system.virtualkeymodifiers) used for the keyboard accelerator.</span></span> <span data-ttu-id="4021f-139">Wird der Modifizierer nicht angegeben, ist der Standardwert „None“.</span><span class="sxs-lookup"><span data-stu-id="4021f-139">If Modifiers is not set, the default value is None.</span></span>

> [!NOTE]
> <span data-ttu-id="4021f-140">Es werden Zugriffstasten, die aus einer einzelnen Taste bestehen (A, Löschen, F2, Leertaste, Esc, Multimediataste) und Zugriffstasten mit mehreren Tasten (STRG+UMSCHALT+M) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4021f-140">Single key (A, Delete, F2, Spacebar, Esc, Multimedia Key) accelerators and multi-key accelerators (Ctrl+Shift+M) are supported.</span></span> <span data-ttu-id="4021f-141">Virtuelle Tasten in Gamepad werden jedoch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4021f-141">However, Gamepad virtual keys are not supported.</span></span>

## <a name="scoped-accelerators"></a><span data-ttu-id="4021f-142">Bereichsbezogene Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-142">Scoped accelerators</span></span>

<span data-ttu-id="4021f-143">Einige Zugriffstasten können nur in bestimmten Bereichen verwendet werden, während andere auf App-Ebene funktionieren.</span><span class="sxs-lookup"><span data-stu-id="4021f-143">Some accelerators work only in specific scopes while others work app-wide.</span></span>

<span data-ttu-id="4021f-144">Microsoft Outlook enthält beispielsweise die folgenden Zugriffstasten:</span><span class="sxs-lookup"><span data-stu-id="4021f-144">For example, Microsoft Outlook includes the following accelerators:</span></span>
-   <span data-ttu-id="4021f-145">Die Tasten STRG+B, STRG+I und ESC funktionieren nur für den Bereich des Formulars „E-Mail senden”</span><span class="sxs-lookup"><span data-stu-id="4021f-145">Ctrl+B, Ctrl+I and ESC work only on the scope of the send email form</span></span>
-   <span data-ttu-id="4021f-146">Die Tasten STRG+1 und STRG+2 funktionieren auf App-Ebene</span><span class="sxs-lookup"><span data-stu-id="4021f-146">Ctrl+1 and Ctrl+2 work app-wide</span></span>

### <a name="context-menus"></a><span data-ttu-id="4021f-147">Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="4021f-147">Context menus</span></span>

<span data-ttu-id="4021f-148">Aktionen im Kontextmenü beeinflussen nur bestimmte Bereiche oder Elemente wie z.B. ausgewählte Zeichen in einem Text-Editor oder Musiktitel in einer Wiedergabeliste.</span><span class="sxs-lookup"><span data-stu-id="4021f-148">Context menu actions affect only specific areas or elements, such as the selected characters in a text editor or a song in a playlist.</span></span> <span data-ttu-id="4021f-149">Aus diesem Grund wird empfohlen, den Umfang der Zugriffstasten für Elemente des Kontextmenüs auf das übergeordnete Element des Kontextmenüs festzulegen.</span><span class="sxs-lookup"><span data-stu-id="4021f-149">For this reason, we recommend setting the scope of keyboard accelerators for context menu items to the parent of the context menu.</span></span>

<span data-ttu-id="4021f-150">Verwenden Sie die [ScopeOwner](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.ScopeOwner)-Eigenschaft, um den Bereich der Zugriffstaste anzugeben.</span><span class="sxs-lookup"><span data-stu-id="4021f-150">Use the [ScopeOwner](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.ScopeOwner) property to specify the scope of the keyboard accelerator.</span></span> <span data-ttu-id="4021f-151">Dieser Code veranschaulicht, wie Sie ein Kontextmenü auf ListView mit bereichsbezogenen Zugriffstasten implementieren:</span><span class="sxs-lookup"><span data-stu-id="4021f-151">This code demonstrates how to implement a context menu on a ListView with scoped keyboard accelerators:</span></span>

``` xaml
<ListView x:Name="MyList">
  <ListView.ContextFlyout>
    <MenuFlyout>
      <MenuFlyoutItem Text="Share" Icon="Share"/>
      <MenuFlyoutItem Text="Copy" Icon="Copy">
        <MenuFlyoutItem.KeyboardAccelerators>
          <KeyboardAccelerator 
            Modifiers="Control" 
            Key="C" 
            ScopeOwner="{x:Bind MyList }" />
        </MenuFlyoutItem.KeyboardAccelerators>
      </MenuFlyoutItem>
      
      <MenuFlyoutItem Text="Delete" Icon="Delete" />
      <MenuFlyoutSeparator />
      
      <MenuFlyoutItem Text="Rename">
        <MenuFlyoutItem.KeyboardAccelerators>
          <KeyboardAccelerator 
            Modifiers="None" 
            Key="F2" 
            ScopeOwner="{x:Bind MyList}" />
        </MenuFlyoutItem.KeyboardAccelerators>
      </MenuFlyoutItem>
      
      <MenuFlyoutItem Text="Select" />
    </MenuFlyout>
    
  </ListView.ContextFlyout>
    
  <ListViewItem>Track 1</ListViewItem>
  <ListViewItem>Alternative Track 1</ListViewItem>

</ListView>
```

<span data-ttu-id="4021f-152">Das ScopeOwner-Attribut des Elements MenuFlyoutItem.KeyboardAccelerators kennzeichnet die Zugriffstaste als bereichsbezogen, anstatt als global (der Standard ist null oder global).</span><span class="sxs-lookup"><span data-stu-id="4021f-152">The ScopeOwner attribute of the MenuFlyoutItem.KeyboardAccelerators element marks the accelerator as scoped instead of global (the default is null, or global).</span></span> <span data-ttu-id="4021f-153">Weitere Details finden Sie im Abschnitt **Beseitigen von Zugriffstasten** weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="4021f-153">For more detail, see the **Resolving accelerators** section later in this topic.</span></span>

## <a name="invoke-a-keyboard-accelerator"></a><span data-ttu-id="4021f-154">Aufrufen einer Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="4021f-154">Invoke a keyboard accelerator</span></span> 

<span data-ttu-id="4021f-155">Das [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator)-Objekt verwendet das [Steuerungsmuster der Benutzeroberflächenautomatisierung (UIA)](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-controlpatternsoverview), um Maßnahmen zu ergreifen, wenn eine Zugriffstaste aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="4021f-155">The [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator) object uses the [UI Automation (UIA) control pattern](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-controlpatternsoverview) to take action when an accelerator is invoked.</span></span>

<span data-ttu-id="4021f-156">Die UIA-Steuerungsmuster machen die häufig verwendeten Steuerelement-Funktionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4021f-156">The UIA [control patterns] expose common control functionality.</span></span> <span data-ttu-id="4021f-157">Das Schaltflächen-Steuerelement implementiert z. B. das [Invoke](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-implementinginvoke) -Steuerungsmuster zur Unterstützung der des Click-Ereignis (in der Regel wird ein Steuerelement durch Klicken, doppelklicken oder Drücken der EINGABETASTE, einer vordefinierte Tastenkombination oder einige andere Tastenkombination aufgerufen).</span><span class="sxs-lookup"><span data-stu-id="4021f-157">For example, the Button control implements the [Invoke](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-implementinginvoke) control pattern to support the Click event (typically a control is invoked by clicking, double-clicking, or pressing Enter, a predefined keyboard shortcut, or some other combination of keystrokes).</span></span> <span data-ttu-id="4021f-158">Wenn eine Zugriffstaste verwendet wird, um ein Steuerelement aufzurufen, sucht das XAML-Framework danach, ob das Steuerelement das Invoke-Steuerungsmuster implementiert und wenn dies der Fall ist, wird es aktiviert (es ist nicht erforderlich, das KeyboardAcceleratorInvoked-Ereignis durchzuführen).</span><span class="sxs-lookup"><span data-stu-id="4021f-158">When a keyboard accelerator is used to invoke a control, the XAML framework looks up whether the control implements the Invoke control pattern and, if so, activates it (it is not necessary to listen for the KeyboardAcceleratorInvoked event).</span></span>

<span data-ttu-id="4021f-159">Im folgenden Beispiel löst STRG+S das Click-Ereignis aus, da die Schaltfläche das Invoke-Muster implementiert.</span><span class="sxs-lookup"><span data-stu-id="4021f-159">In the following example, Control+S triggers the Click event because the button implements the Invoke pattern.</span></span>

``` xaml 
<Button Content="Save" Click="OnSave">
  <Button.KeyboardAccelerators>
    <KeyboardAccelerator Key="S" Modifiers="Control" />
  </Button.KeyboardAccelerators>
</Button>
```

<span data-ttu-id="4021f-160">Wenn ein Element mehrere Steuerungsmuster implementiert, kann nur ein einziges über die Zugriffstaste aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="4021f-160">If an element implements multiple control patterns, only one can be activated through an accelerator.</span></span> <span data-ttu-id="4021f-161">Die Prioritätsstufe der Steuerungsmuster ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4021f-161">The control patterns are prioritized as follows:</span></span>
1.  <span data-ttu-id="4021f-162">Aufrufen (Taste)</span><span class="sxs-lookup"><span data-stu-id="4021f-162">Invoke (Button)</span></span>
2.  <span data-ttu-id="4021f-163">Ein-/Ausschalten (Kontrollkästchen)</span><span class="sxs-lookup"><span data-stu-id="4021f-163">Toggle (Checkbox)</span></span>
3.  <span data-ttu-id="4021f-164">Auswahl (ListView)</span><span class="sxs-lookup"><span data-stu-id="4021f-164">Selection (ListView)</span></span>
4.  <span data-ttu-id="4021f-165">Erweitern/Reduzieren (ComboBox)</span><span class="sxs-lookup"><span data-stu-id="4021f-165">Expand/Collapse (ComboBox)</span></span> 

<span data-ttu-id="4021f-166">Wenn keine Übereinstimmung identifiziert wird, wird die Zugriffstaste ungültig und es wird eine Debugmeldung angezeigt („Es wurden keine Automatisierungsmuster für diese Komponente gefunden.</span><span class="sxs-lookup"><span data-stu-id="4021f-166">If no match is identified, the accelerator is invalid and a debug message is provided ("No automation patterns for this component found.</span></span> <span data-ttu-id="4021f-167">Implementieren Sie das gewünschte Verhalten im Invoke-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="4021f-167">Implement all desired behavior in the Invoked event.</span></span> <span data-ttu-id="4021f-168">Wenn Sie „Handled“ im Ereignishandler auf „true“ festlegen, wird diese Meldung unterdrückt.“)</span><span class="sxs-lookup"><span data-stu-id="4021f-168">Setting Handled to true in your event handler suppresses this message.")</span></span>

## <a name="custom-keyboard-accelerator-behavior"></a><span data-ttu-id="4021f-169">Benutzerdefiniertes Verhalten der Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-169">Custom keyboard accelerator behavior</span></span>

<span data-ttu-id="4021f-170">Das Invoke-Ereignis des [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator)-Objekts wird ausgelöst, wenn die Zugriffstaste ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4021f-170">The Invoked event of the [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator) object is fired when the accelerator is executed.</span></span> <span data-ttu-id="4021f-171">Das [KeyboardAcceleratorInvokedEventArgs](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs)-Ereignisobjekt enthält die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="4021f-171">The [KeyboardAcceleratorInvokedEventArgs](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs) event object includes the following properties:</span></span>

- <span data-ttu-id="4021f-172">[**Behandelt**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs.handled) (Boolesch): verhindert, dass das Ereignis das Steuerungsmuster auslöst und Eventbubbling der Zugriffstaste Festlegen dieser Einstellung auf "true" fest.</span><span class="sxs-lookup"><span data-stu-id="4021f-172">[**Handled**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs.handled) (Boolean): Setting this to true prevents the event triggering the control pattern and stops accelerator event bubbling.</span></span> <span data-ttu-id="4021f-173">Der Standard ist "False".</span><span class="sxs-lookup"><span data-stu-id="4021f-173">The default is false.</span></span>
- <span data-ttu-id="4021f-174">[**Element**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs.element) (DependencyObject): das Objekt, das die Zugriffstaste zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="4021f-174">[**Element**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs.element) (DependencyObject): The object associated with the accelerator.</span></span>
- <span data-ttu-id="4021f-175">[**KeyboardAccelerator**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs.keyboardaccelerator): die Zugriffstaste zum Auslösen des Ereignisses aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="4021f-175">[**KeyboardAccelerator**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs.keyboardaccelerator): The keyboard accelerator used to raise the Invoked event.</span></span>

<span data-ttu-id="4021f-176">Hier gezeigt, wie Sie eine Sammlung von Zugriffstasten für Elemente in einer ListView definieren und zum Behandeln des aufgerufenen Ereignisses für jede Zugriffstaste.</span><span class="sxs-lookup"><span data-stu-id="4021f-176">Here we demonstrate how to define a collection of keyboard accelerators for items in a ListView, and how to handle the Invoked event for each accelerator.</span></span>

``` xaml
<ListView x:Name="MyListView">
  <ListView.KeyboardAccelerators>
    <KeyboardAccelerator Key="A" Modifiers="Control,Shift" Invoked="SelectAllInvoked" />
    <KeyboardAccelerator Key="F5" Invoked="RefreshInvoked"  />
  </ListView.KeyboardAccelerators>
</ListView>
```

``` csharp
void SelectAllInvoked(KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
  MyListView.SelectAll();
  args.Handled = true;
}

void RefreshInvoked(KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
  MyListView.SelectionMode = ListViewSelectionMode.None;
  MyListView.SelectionMode = ListViewSelectionMode.Multiple;
  args.Handled = true;
}
```

## <a name="override-default-keyboard-behavior"></a><span data-ttu-id="4021f-177">Standardverhalten überschreiben</span><span class="sxs-lookup"><span data-stu-id="4021f-177">Override default keyboard behavior</span></span>

<span data-ttu-id="4021f-178">In einigen Fällen müssen Sie das Standardverhalten der bestimmte Schlüssel wie z. B. die RÜCKTASTE oder die EINGABETASTE außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="4021f-178">In some cases, you might need to override the default behavior of specific keys such as the Backspace key or the Enter key.</span></span> <span data-ttu-id="4021f-179">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4021f-179">For example,</span></span> 

## <a name="disable-a-keyboard-accelerator"></a><span data-ttu-id="4021f-180">Deaktivieren einer Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="4021f-180">Disable a keyboard accelerator</span></span> 

<span data-ttu-id="4021f-181">Wenn ein Steuerelement deaktiviert ist, wird die zugehörige Zugriffstaste ebenfalls deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="4021f-181">If a control is disabled, the associated accelerator is also disabled.</span></span> <span data-ttu-id="4021f-182">Im folgenden Beispiel ist die IsEnabled-Eigenschaft von ListView auf "false" festgelegt. Daher kann die zugehörige STRG+A-Zugriffstaste nicht aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="4021f-182">In the following example, because the IsEnabled property of the ListView is set to false, the associated Control+A accelerator can't be invoked.</span></span>

``` xaml
<ListView >
  <ListView.KeyboardAccelerators>
    <KeyboardAccelerator Key="A"
      Modifiers="Control"
      Invoked="CustomListViewSelecAllInvoked" />
  </ListView.KeyboardAccelerators>
  
  <TextBox>
    <TextBox.KeyboardAccelerators>
      <KeyboardAccelerator 
        Key="A" 
        Modifiers="Control" 
        Invoked="CustomTextSelecAllInvoked" 
        IsEnabled="False" />
    </TextBox.KeyboardAccelerators>
  </TextBox>

<ListView>
```

<span data-ttu-id="4021f-183">Übergeordnete und untergeordnete Steuerelemente können die gleiche Zugriffstaste haben.</span><span class="sxs-lookup"><span data-stu-id="4021f-183">Parent and child controls can share the same accelerator.</span></span> <span data-ttu-id="4021f-184">In diesem Fall kann das übergeordnete Steuerelement auch aufgerufen werden, wenn das untergeordnete Element den Fokus hat und die Zugriffstaste deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="4021f-184">In this case, the parent control can be invoked even if the child has focus and its accelerator is disabled.</span></span>

## <a name="screen-readers-and-keyboard-accelerators"></a><span data-ttu-id="4021f-185">Sprachausgaben und Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-185">Screen readers and keyboard accelerators</span></span> 

<span data-ttu-id="4021f-186">Bildschirmleseprogramme wie die die Sprachausgabe können dem Benutzer die Tastenkombination für die Zugriffstasten melden.</span><span class="sxs-lookup"><span data-stu-id="4021f-186">Screen readers such as Narrator can announce the keyboard accelerator key combination to users.</span></span> <span data-ttu-id="4021f-187">Standardmäßig ist dies jeder Modifizierer (in der Reihenfolge der VirtualModifiers-Enumeration), gefolgt von der Taste (und durch das "+"-Zeichen getrennt).</span><span class="sxs-lookup"><span data-stu-id="4021f-187">By default, this is each modifier (in the VirtualModifiers enum order) followed by the key (and separated by "+" signs).</span></span> <span data-ttu-id="4021f-188">Sie können dies durch die [AcceleratorKey](https://docs.microsoft.com/uwp/api/windows.ui.xaml.automation.automationproperties.AcceleratorKeyProperty) AutomationProperties angefügten Eigenschaft anpassen.</span><span class="sxs-lookup"><span data-stu-id="4021f-188">You can customize this through the [AcceleratorKey](https://docs.microsoft.com/uwp/api/windows.ui.xaml.automation.automationproperties.AcceleratorKeyProperty) AutomationProperties attached property.</span></span> <span data-ttu-id="4021f-189">Wenn mehr als eine Zugriffstaste angegeben wird, wird nur die erste Taste gemeldet.</span><span class="sxs-lookup"><span data-stu-id="4021f-189">If more than one accelerator is specified, only the first is announced.</span></span>

<span data-ttu-id="4021f-190">In diesem Beispiel gibt AutomationProperty.AcceleratorKey die Zeichenfolge "STRG + UMSCHALT+A" zurück:</span><span class="sxs-lookup"><span data-stu-id="4021f-190">In this example, the AutomationProperty.AcceleratorKey returns the string "Control+Shift+A":</span></span>

``` xaml
<ListView x:Name="MyListView">
  <ListView.KeyboardAccelerators>

    <KeyboardAccelerator 
      Key="A" 
      Modifiers="Control,Shift" 
      Invoked="CustomSelectAllInvoked" />
      
    <KeyboardAccelerator 
      Key="F5" 
      Modifiers="None" 
      Invoked="RefreshInvoked" />

  </ListView.KeyboardAccelerators>

</ListView>   
```

> [!NOTE] 
> <span data-ttu-id="4021f-191">Das Festlegen der AutomationProperties.AcceleratorKey-Funktion aktiviert nicht die Tastaturfunktion, es gibt es nur der UIA-Framework an, welche Tasten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4021f-191">Setting AutomationProperties.AcceleratorKey doesn't enable keyboard functionality, it only indicates to the UIA framework which keys are used.</span></span>

## <a name="common-keyboard-accelerators"></a><span data-ttu-id="4021f-192">Allgemeine Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-192">Common Keyboard Accelerators</span></span>

<span data-ttu-id="4021f-193">Es wird empfohlen, dass Sie Zugriffstasten für UWP-Apps konsistent sind.</span><span class="sxs-lookup"><span data-stu-id="4021f-193">We recommend that you make keyboard accelerators consistent across UWP applications.</span></span> <span data-ttu-id="4021f-194">Benutzer müssen sich die Zugriffstasten merken und das gleiche (oder ähnliche) Ergebnis erwarten.</span><span class="sxs-lookup"><span data-stu-id="4021f-194">Users have to memorize keyboard accelerators and expect the same (or similar) results.</span></span>

<span data-ttu-id="4021f-195">Aufgrund der unterschiedlichen Funktionen ist dies allerdings nicht immer in allen Apps möglich.</span><span class="sxs-lookup"><span data-stu-id="4021f-195">This might not always be possible due to differences in functionality across apps.</span></span>

| **<span data-ttu-id="4021f-196">Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="4021f-196">Editing</span></span>** | **<span data-ttu-id="4021f-197">Allgemeine Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="4021f-197">Common Keyboard Accelerator</span></span>** |
| ------------- | ----------------------------------- |
| <span data-ttu-id="4021f-198">Den Bearbeitungsmodus beginnen</span><span class="sxs-lookup"><span data-stu-id="4021f-198">Begin editing mode</span></span> | <span data-ttu-id="4021f-199">STRG+E</span><span class="sxs-lookup"><span data-stu-id="4021f-199">Ctrl + E</span></span> |
| <span data-ttu-id="4021f-200">Alle Elemente in einem Steuerelement mit angezeigtem Fokus oder Fenster auswählen</span><span class="sxs-lookup"><span data-stu-id="4021f-200">Select all items in a focused control or window</span></span> | <span data-ttu-id="4021f-201">STRG+A</span><span class="sxs-lookup"><span data-stu-id="4021f-201">Ctrl + A</span></span> |
| <span data-ttu-id="4021f-202">Suchen und Ersetzen</span><span class="sxs-lookup"><span data-stu-id="4021f-202">Search and replace</span></span> | <span data-ttu-id="4021f-203">STRG+H</span><span class="sxs-lookup"><span data-stu-id="4021f-203">Ctrl + H</span></span> |
| <span data-ttu-id="4021f-204">Rückgängig machen</span><span class="sxs-lookup"><span data-stu-id="4021f-204">Undo</span></span> | <span data-ttu-id="4021f-205">STRG+Z</span><span class="sxs-lookup"><span data-stu-id="4021f-205">Ctrl + Z</span></span> |
| <span data-ttu-id="4021f-206">Wiederholen</span><span class="sxs-lookup"><span data-stu-id="4021f-206">Redo</span></span> | <span data-ttu-id="4021f-207">STRG+Y</span><span class="sxs-lookup"><span data-stu-id="4021f-207">Ctrl + Y</span></span> |
| <span data-ttu-id="4021f-208">Die Auswahl löschen und in die Zwischenablage kopieren</span><span class="sxs-lookup"><span data-stu-id="4021f-208">Delete selection and copy it to the clipboard</span></span> | <span data-ttu-id="4021f-209">STRG+X</span><span class="sxs-lookup"><span data-stu-id="4021f-209">Ctrl + X</span></span> |
| <span data-ttu-id="4021f-210">Auswahl in die Zwischenablage kopieren</span><span class="sxs-lookup"><span data-stu-id="4021f-210">Copy selection to the clipboard</span></span> | <span data-ttu-id="4021f-211">STRG+C, STRG+EINFG</span><span class="sxs-lookup"><span data-stu-id="4021f-211">Ctrl + C, Ctrl + Insert</span></span> |
| <span data-ttu-id="4021f-212">Inhalte aus der Zwischenablage einfügen</span><span class="sxs-lookup"><span data-stu-id="4021f-212">Paste the contents of the clipboard</span></span> | <span data-ttu-id="4021f-213">STRG+V, UMSCHALT+EINFG</span><span class="sxs-lookup"><span data-stu-id="4021f-213">Ctrl + V, Shift + Insert</span></span> |
| <span data-ttu-id="4021f-214">Den Inhalt der Zwischenablage einfügen (mit Optionen).</span><span class="sxs-lookup"><span data-stu-id="4021f-214">Paste the contents of the clipboard (with options)</span></span> | <span data-ttu-id="4021f-215">STRG+ALT+V</span><span class="sxs-lookup"><span data-stu-id="4021f-215">Ctrl + Alt + V</span></span> |
| <span data-ttu-id="4021f-216">Element umzubenennen</span><span class="sxs-lookup"><span data-stu-id="4021f-216">Rename an item</span></span> | <span data-ttu-id="4021f-217">F2</span><span class="sxs-lookup"><span data-stu-id="4021f-217">F2</span></span> |
| <span data-ttu-id="4021f-218">Neues Element hinzufügen</span><span class="sxs-lookup"><span data-stu-id="4021f-218">Add a new item</span></span> | <span data-ttu-id="4021f-219">STRG+N</span><span class="sxs-lookup"><span data-stu-id="4021f-219">Ctrl + N</span></span> |
| <span data-ttu-id="4021f-220">Neues zweites Element hinzufügen</span><span class="sxs-lookup"><span data-stu-id="4021f-220">Add a new secondary item</span></span> | <span data-ttu-id="4021f-221">STRG+UMSCHALT+N</span><span class="sxs-lookup"><span data-stu-id="4021f-221">Ctrl + Shift + N</span></span> |
| <span data-ttu-id="4021f-222">Ausgewähltes Element löschen (mit Rückgängigmachen)</span><span class="sxs-lookup"><span data-stu-id="4021f-222">Delete selected item (with undo)</span></span> | <span data-ttu-id="4021f-223">ENTF, STRG+D</span><span class="sxs-lookup"><span data-stu-id="4021f-223">Del, Ctrl+D</span></span> |
| <span data-ttu-id="4021f-224">Ausgewähltes Element löschen (ohne Rückgängigmachen)</span><span class="sxs-lookup"><span data-stu-id="4021f-224">Delete selected item (without undo)</span></span> | <span data-ttu-id="4021f-225">UMSCHALT+ENTF</span><span class="sxs-lookup"><span data-stu-id="4021f-225">Shift + Del</span></span> |
| <span data-ttu-id="4021f-226">Fett</span><span class="sxs-lookup"><span data-stu-id="4021f-226">Bold</span></span> | <span data-ttu-id="4021f-227">STRG+B</span><span class="sxs-lookup"><span data-stu-id="4021f-227">Ctrl + B</span></span> |
| <span data-ttu-id="4021f-228">Unterstreichen</span><span class="sxs-lookup"><span data-stu-id="4021f-228">Underline</span></span> | <span data-ttu-id="4021f-229">STRG+U</span><span class="sxs-lookup"><span data-stu-id="4021f-229">Ctrl + U</span></span> |
| <span data-ttu-id="4021f-230">Kursiv</span><span class="sxs-lookup"><span data-stu-id="4021f-230">Italic</span></span> | <span data-ttu-id="4021f-231">STRG+I</span><span class="sxs-lookup"><span data-stu-id="4021f-231">Ctrl + I</span></span> |

| **<span data-ttu-id="4021f-232">Navigation</span><span class="sxs-lookup"><span data-stu-id="4021f-232">Navigation</span></span>** | |
| ------------- | ----------------------------------- |
| <span data-ttu-id="4021f-233">Nach Inhalten in einem Steuerelement mit Fokus oder Fenster suchen</span><span class="sxs-lookup"><span data-stu-id="4021f-233">Find content in a focused control or Window</span></span> | <span data-ttu-id="4021f-234">STRG+F</span><span class="sxs-lookup"><span data-stu-id="4021f-234">Ctrl + F</span></span> |
| <span data-ttu-id="4021f-235">Das nächste Suchergebnis anzeigen</span><span class="sxs-lookup"><span data-stu-id="4021f-235">Go to the next search result</span></span> | <span data-ttu-id="4021f-236">F3</span><span class="sxs-lookup"><span data-stu-id="4021f-236">F3</span></span> |

| **<span data-ttu-id="4021f-237">Andere Aktionen</span><span class="sxs-lookup"><span data-stu-id="4021f-237">Other Actions</span></span>** | |
| ------------- | ----------------------------------- |
| <span data-ttu-id="4021f-238">Favoriten hinzufügen</span><span class="sxs-lookup"><span data-stu-id="4021f-238">Add favorites</span></span> | <span data-ttu-id="4021f-239">STRG+D</span><span class="sxs-lookup"><span data-stu-id="4021f-239">Ctrl + D</span></span> | 
| <span data-ttu-id="4021f-240">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="4021f-240">Refresh</span></span> | <span data-ttu-id="4021f-241">F5 oder STRG+R</span><span class="sxs-lookup"><span data-stu-id="4021f-241">F5 or Ctrl + R</span></span> | 
| <span data-ttu-id="4021f-242">Vergrößern</span><span class="sxs-lookup"><span data-stu-id="4021f-242">Zoom In</span></span> | <span data-ttu-id="4021f-243">STRG++</span><span class="sxs-lookup"><span data-stu-id="4021f-243">Ctrl + +</span></span> | 
| <span data-ttu-id="4021f-244">Verkleinern</span><span class="sxs-lookup"><span data-stu-id="4021f-244">Zoom out</span></span> | <span data-ttu-id="4021f-245">STRG+-</span><span class="sxs-lookup"><span data-stu-id="4021f-245">Ctrl + -</span></span> | 
| <span data-ttu-id="4021f-246">Auf Standardansicht zoomen</span><span class="sxs-lookup"><span data-stu-id="4021f-246">Zoom to default view</span></span> | <span data-ttu-id="4021f-247">STRG + 0</span><span class="sxs-lookup"><span data-stu-id="4021f-247">Ctrl + 0</span></span> | 
| <span data-ttu-id="4021f-248">Speichern</span><span class="sxs-lookup"><span data-stu-id="4021f-248">Save</span></span> | <span data-ttu-id="4021f-249">STRG+S</span><span class="sxs-lookup"><span data-stu-id="4021f-249">Ctrl + S</span></span> | 
| <span data-ttu-id="4021f-250">Schließen</span><span class="sxs-lookup"><span data-stu-id="4021f-250">Close</span></span> | <span data-ttu-id="4021f-251">STRG+W</span><span class="sxs-lookup"><span data-stu-id="4021f-251">Ctrl + W</span></span> | 
| <span data-ttu-id="4021f-252">Drucken</span><span class="sxs-lookup"><span data-stu-id="4021f-252">Print</span></span> | <span data-ttu-id="4021f-253">STRG+P</span><span class="sxs-lookup"><span data-stu-id="4021f-253">Ctrl + P</span></span> | 

<span data-ttu-id="4021f-254">Beachten Sie, dass einige der Kombinationen nicht für lokalisierte Versionen von Windows gelten.</span><span class="sxs-lookup"><span data-stu-id="4021f-254">Notice that some of the combinations are not valid for localized versions of Windows.</span></span> <span data-ttu-id="4021f-255">In der spanischen Version von Windows wird STRG+N anstelle von STRG+B zur Fettformatierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="4021f-255">For example, in the Spanish version of Windows, Ctrl+N is used for bold instead of Ctrl+B.</span></span> <span data-ttu-id="4021f-256">Es wird empfohlen, lokalisierte Zugriffstasten bereitzustellen, wenn die App lokalisiert ist.</span><span class="sxs-lookup"><span data-stu-id="4021f-256">We recommend providing localized keyboard accelerators if the app is localized.</span></span>

## <a name="usability-affordances-for-keyboard-accelerators"></a><span data-ttu-id="4021f-257">Nutzbarkeitsangebote für Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-257">Usability affordances for keyboard accelerators</span></span>

### <a name="tooltips"></a><span data-ttu-id="4021f-258">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="4021f-258">Tooltips</span></span>

<span data-ttu-id="4021f-259">Da Zugriffstasten in der Regel nicht direkt in der Benutzeroberfläche Ihrer UWP-Anwendung beschrieben sind, können Sie die Auffindbarkeit durch [QuickInfos](../controls-and-patterns/tooltips.md) verbessern, die automatisch angezeigt werden, wenn der Benutzer den Fokus auf ein Steuerelement setzt bzw. die Maus drückt und hält oder mit dem Mauszeiger darauf zeigt.</span><span class="sxs-lookup"><span data-stu-id="4021f-259">As keyboard accelerators are not typically described directly in the UI of your UWP application, you can improve discoverability through [tooltips](../controls-and-patterns/tooltips.md), which display automatically when the user moves focus to, presses and holds, or hovers the mouse pointer over a control.</span></span> <span data-ttu-id="4021f-260">Die QuickInfo kann erkennen, ob ein Steuerelement über eine zugeordnete Zugriffstaste verfügt und, wenn ja, welche Tastenkombination als Zugriffstaste verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4021f-260">The tooltip can identify whether a control has an associated keyboard accelerator and, if so, what the accelerator key combination is.</span></span>

**<span data-ttu-id="4021f-261">Windows 10, Version 1803 (April 2018 Update) und höher</span><span class="sxs-lookup"><span data-stu-id="4021f-261">Windows 10, Version 1803 (April 2018 Update) and newer</span></span>**

<span data-ttu-id="4021f-262">Standardmäßig wenn Zugriffstasten deklariert sind, stellen Sie alle Steuerelemente (außer [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem) und [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem)) die entsprechenden Tastenkombination in einer QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="4021f-262">By default, When keyboard accelerators are declared, all controls (except [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem) and [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem)) present the corresponding key combinations in a tooltip.</span></span>

> [!NOTE] 
> <span data-ttu-id="4021f-263">Wenn ein Steuerelement mehrere Zugriffstasten definiert ist, wird nur die erste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4021f-263">If a control has more than one accelerator defined, only the first is presented.</span></span>

![QuickInfo für Zugriffstasten](images/accelerators/accelerators_tooltip_savebutton_small.png)

*<span data-ttu-id="4021f-265">Zugriffstastenkombination in QuickInfo</span><span class="sxs-lookup"><span data-stu-id="4021f-265">Accelerator key combo in tooltip</span></span>*

<span data-ttu-id="4021f-266">Für die [Schaltfläche](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button), [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton)und [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) -Objekte die Zugriffstaste des Steuerelements Standard QuickInfo angefügt.</span><span class="sxs-lookup"><span data-stu-id="4021f-266">For [Button](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button), [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton), and [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) objects, the keyboard accelerator is appended to the control's default tooltip.</span></span> <span data-ttu-id="4021f-267">Für [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) und [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem)) Objekte, die Zugriffstaste wird mit den Flyout-Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4021f-267">For [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) and [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem)) objects, the keyboard accelerator is displayed with the flyout text.</span></span>

> [!NOTE]
> <span data-ttu-id="4021f-268">Geben Sie eine QuickInfo wird (Siehe Button1 im folgenden Beispiel) dieses Verhalten überschrieben.</span><span class="sxs-lookup"><span data-stu-id="4021f-268">Specifying a tooltip (see Button1 in the following example) overrides this behavior.</span></span>

```xaml
<StackPanel x:Name="Container" Grid.Row="0" Background="AliceBlue">
    <Button Content="Button1" Margin="20"
            Click="OnSave" 
            KeyboardAcceleratorPlacementMode="Auto" 
            ToolTipService.ToolTip="Tooltip">
        <Button.KeyboardAccelerators>
            <KeyboardAccelerator  Key="A" Modifiers="Windows"/>
        </Button.KeyboardAccelerators>
    </Button>
    <Button Content="Button2"  Margin="20"
            Click="OnSave" 
            KeyboardAcceleratorPlacementMode="Auto">
        <Button.KeyboardAccelerators>
            <KeyboardAccelerator  Key="B" Modifiers="Windows"/>
        </Button.KeyboardAccelerators>
    </Button>
    <Button Content="Button3"  Margin="20"
            Click="OnSave" 
            KeyboardAcceleratorPlacementMode="Auto">
        <Button.KeyboardAccelerators>
            <KeyboardAccelerator  Key="C" Modifiers="Windows"/>
        </Button.KeyboardAccelerators>
    </Button>
</StackPanel>
```

![QuickInfo für Zugriffstasten](images/accelerators/accelerators-button-small.png)

*<span data-ttu-id="4021f-270">Schaltfläche standardmäßig QuickInfo angefügte Zugriffstastenkombination</span><span class="sxs-lookup"><span data-stu-id="4021f-270">Accelerator key combo appended to Button's default tooltip</span></span>*

```xaml
<AppBarButton Icon="Save" Label="Save">
    <AppBarButton.KeyboardAccelerators>
        <KeyboardAccelerator Key="S" Modifiers="Control"/>
    </AppBarButton.KeyboardAccelerators>
</AppBarButton>
```

![QuickInfo für Zugriffstasten](images/accelerators/accelerators-appbarbutton-small.png)

*<span data-ttu-id="4021f-272">AppBarButton Standard QuickInfo angefügte Zugriffstastenkombination</span><span class="sxs-lookup"><span data-stu-id="4021f-272">Accelerator key combo appended to AppBarButton's default tooltip</span></span>*

```xaml
<AppBarButton AccessKey="R" Icon="Refresh" Label="Refresh" IsAccessKeyScope="True">
    <AppBarButton.Flyout>
        <MenuFlyout>
            <MenuFlyoutItem AccessKey="A" Icon="Refresh" Text="Refresh A">
                <MenuFlyoutItem.KeyboardAccelerators>
                    <KeyboardAccelerator Key="R" Modifiers="Control"/>
                </MenuFlyoutItem.KeyboardAccelerators>
            </MenuFlyoutItem>
            <MenuFlyoutItem AccessKey="B" Icon="Globe" Text="Refresh B" />
            <MenuFlyoutItem AccessKey="C" Icon="Globe" Text="Refresh C" />
            <MenuFlyoutItem AccessKey="D" Icon="Globe" Text="Refresh D" />
            <ToggleMenuFlyoutItem AccessKey="E" Icon="Globe" Text="ToggleMe">
                <MenuFlyoutItem.KeyboardAccelerators>
                    <KeyboardAccelerator Key="Q" Modifiers="Control"/>
                </MenuFlyoutItem.KeyboardAccelerators>
            </ToggleMenuFlyoutItem>
        </MenuFlyout>
    </AppBarButton.Flyout>
</AppBarButton>
```

![QuickInfo für Zugriffstasten](images/accelerators/accelerators-appbar-menuflyoutitem-small.png)

*<span data-ttu-id="4021f-274">In MenuFlyoutItems Text angefügte Zugriffstastenkombination</span><span class="sxs-lookup"><span data-stu-id="4021f-274">Accelerator key combo appended to MenuFlyoutItem's text</span></span>*

<span data-ttu-id="4021f-275">Sie können das Darstellungsverhalten über die Eigenschaft [KeyboardAcceleratorPlacementMode](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.KeyboardAcceleratorPlacementMode) steuern, die zwei Werte akzeptiert: [Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorplacementmode) oder [Hidden](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorplacementmode).</span><span class="sxs-lookup"><span data-stu-id="4021f-275">Control the presentation behavior by using the [KeyboardAcceleratorPlacementMode](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.KeyboardAcceleratorPlacementMode) property, which accepts two values: [Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorplacementmode) or [Hidden](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorplacementmode).</span></span>    

```xaml
<Button Content="Save" Click="OnSave" KeyboardAcceleratorPlacementMode="Auto">
    <Button.KeyboardAccelerators>
        <KeyboardAccelerator Key="S" Modifiers="Control" />
    </Button.KeyboardAccelerators>
</Button>
```

<span data-ttu-id="4021f-276">In einigen Fällen müssen Sie möglicherweise eine QuickInfo in Bezug zu einem anderen Element darstellen (in der Regel ein Containerobjekt).</span><span class="sxs-lookup"><span data-stu-id="4021f-276">In some cases, you might need to present a tooltip relative to another element (typically a container object).</span></span> <span data-ttu-id="4021f-277">Beispielsweise ein Pivot-Steuerelement, das die QuickInfo für ein PivotItem mit dem Pivot-Header anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4021f-277">For example, a Pivot control that displays the tooltip for a PivotItem with the Pivot header.</span></span> 

<span data-ttu-id="4021f-278">Im Folgenden ist gezeigt, wie Sie die Eigenschaft KeyboardAcceleratorPlacementTarget verwenden, um die Tastenkombination für die Zugriffstaste für eine Schaltfläche zum Speichern mit dem Grid-Container anstelle der Schaltfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4021f-278">Here, we show how to use the KeyboardAcceleratorPlacementTarget property to display the keyboard accelerator key combination for a Save button with the Grid container instead of the button.</span></span>

```xaml
<Grid x:Name="Container" Padding="30">
  <Button Content="Save"
    Click="OnSave"
    KeyboardAcceleratorPlacementMode="Auto"
    KeyboardAcceleratorPlacementTarget="{x:Bind Container}">
    <Button.KeyboardAccelerators>
      <KeyboardAccelerator  Key="S" Modifiers="Control" />
    </Button.KeyboardAccelerators>
  </Button>
</Grid>
```

### <a name="labels"></a><span data-ttu-id="4021f-279">Beschriftungen</span><span class="sxs-lookup"><span data-stu-id="4021f-279">Labels</span></span>

<span data-ttu-id="4021f-280">In einigen Fällen wird empfohlen, die Beschriftung eines Steuerelements zu verwenden, um zu identifizieren, ob das Steuerelement über eine zugeordnete Zugriffstaste verfügt und, wenn ja, welche Tastenkombination als Zugriffstaste verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4021f-280">In some cases, we recommend using a control's label to identify whether the control has an associated keyboard accelerator and, if so, what the accelerator key combination is.</span></span> 

<span data-ttu-id="4021f-281">Bei einigen Plattformsteuerelementen geschieht dies standardmäßig, insbesondere bei den Objekten [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem) und [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem), während es bei [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) und [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) dazu kommt, wenn sie im Überlaufmenü der [CommandBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4021f-281">Some platform controls do this by default, specifically the [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem) and [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem) objects, while the [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) and the [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) do it when they appear in the overflow menu of the [CommandBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar).</span></span>

![In einer Menüelementbeschriftungen beschriebene Zugriffstasten](images/accelerators/accelerators_menuitemlabel.png)  
*<span data-ttu-id="4021f-283">In einer Menüelementbeschriftungen beschriebene Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-283">Keyboard accelerators described in a menu item label</span></span>*

<span data-ttu-id="4021f-284">Sie können den Standardtext für die Beschriftung der Zugriffstaste über die Eigenschaft [KeyboardAcceleratorTextOverride](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton.KeyboardAcceleratorTextOverride) der Steuerelemente [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem), [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem), [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) und [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) überschreiben (verwenden Sie ein Leerzeichen, wenn kein Text vorhanden sein soll).</span><span class="sxs-lookup"><span data-stu-id="4021f-284">You can override the default accelerator text for the label through the [KeyboardAcceleratorTextOverride](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton.KeyboardAcceleratorTextOverride) property of the [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem), [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem), [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton), and [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) controls (use a single space for no text).</span></span> 

> [!NOTE] 
> <span data-ttu-id="4021f-285">Der überschreibende Text wird nicht angezeigt, wenn das System keine angeschlossene Tastatur erkennen kann (Sie können dies selbst über die Eigenschaft [KeyboardPresent](https://docs.microsoft.com/uwp/api/windows.devices.input.keyboardcapabilities.KeyboardPresent) überprüfen).</span><span class="sxs-lookup"><span data-stu-id="4021f-285">The override text is not be presented if the system cannot detect an attached keyboard (you can check this yourself through the [KeyboardPresent](https://docs.microsoft.com/uwp/api/windows.devices.input.keyboardcapabilities.KeyboardPresent) property).</span></span>

## <a name="advanced-concepts"></a><span data-ttu-id="4021f-286">Erweiterte Konzepte</span><span class="sxs-lookup"><span data-stu-id="4021f-286">Advanced Concepts</span></span>

<span data-ttu-id="4021f-287">In diesem Abschnitt erläutern wir einige einfache Aspekte der Zugriffstasten.</span><span class="sxs-lookup"><span data-stu-id="4021f-287">Here, we review some low-level aspects of keyboard accelerators.</span></span>

### <a name="when-an-accelerator-is-invoked"></a><span data-ttu-id="4021f-288">Wenn eine Zugriffstaste aufgerufen wird</span><span class="sxs-lookup"><span data-stu-id="4021f-288">When an accelerator is invoked</span></span>

<span data-ttu-id="4021f-289">Zugriffstasten bestehen aus zwei Arten von Tasten: Modifizierer und Nicht-Modifizierer.</span><span class="sxs-lookup"><span data-stu-id="4021f-289">Accelerators are composed of two types of keys: modifiers and non-modifiers.</span></span> <span data-ttu-id="4021f-290">Zu den Zusatztasten gehören die Umschalttaste, Menü, STRG und die Windows-Taste, die über [VirtualKeyModifiers](https://docs.microsoft.com/uwp/api/Windows.System.VirtualKeyModifiers) verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="4021f-290">Modifier keys include Shift, Menu, Control, and the Windows key, which are exposed through [VirtualKeyModifiers](https://docs.microsoft.com/uwp/api/Windows.System.VirtualKeyModifiers).</span></span> <span data-ttu-id="4021f-291">Nichtzusatztasten sind alle virtuellen Schlüssel wie z.B. Löschen, F3, die Leertaste, Esc und alle alphanumerischen und Satzzeichen-Tasten.</span><span class="sxs-lookup"><span data-stu-id="4021f-291">Non-modifiers are any virtual key, such as Delete, F3, Spacebar, Esc, and all alphanumeric and punctuation keys.</span></span> <span data-ttu-id="4021f-292">Eine Zugriffstaste wird aufgerufen, wenn Benutzer eine andere Taste drücken, während sie eine oder mehrere Zusatztasten gedrückt halten.</span><span class="sxs-lookup"><span data-stu-id="4021f-292">A keyboard accelerator is invoked when the user presses a non-modifier key while they press and hold one or more modifier keys.</span></span> <span data-ttu-id="4021f-293">Wenn der Benutzer beispielsweise STRG+UMSCHALT+M drückt und dann M drückt, überprüft das Framework die Modifizierer (STRG und UMSCHALTTASTE) und die Zugriffstaste wird ausgelöst, wenn sie vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="4021f-293">For example, if the user presses Ctrl+Shift+M, when the user presses M, the framework checks the modifiers (Ctrl and Shift) and fires the accelerator, if it exists.</span></span>

> [!NOTE]
> <span data-ttu-id="4021f-294">Standardmäßig wird die Zugriffstaste automatisch wiederholt (z.B., wenn der Benutzer STRG+UMSCHALT drückt und dann M gedrückt hält, wird die Zugriffstaste wiederholt aufgerufen, bis M losgelassen wird).</span><span class="sxs-lookup"><span data-stu-id="4021f-294">By design, the accelerator autorepeats (for example, when the user presses Ctrl+Shift and then holds down M, the accelerator is invoked repeatedly until M is released).</span></span> <span data-ttu-id="4021f-295">Dieses Verhalten kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="4021f-295">This behavior cannot be modified.</span></span>

### <a name="input-event-priority"></a><span data-ttu-id="4021f-296">Priorität des Eingabeereignises</span><span class="sxs-lookup"><span data-stu-id="4021f-296">Input event priority</span></span>
<span data-ttu-id="4021f-297">Eingabeereignisse treten in einer bestimmten Reihenfolge auf, die Sie je nach Anforderungen der App abfangen und behandeln können.</span><span class="sxs-lookup"><span data-stu-id="4021f-297">Input events occur in a specific sequence that you can intercept and handle based on the requirements of your app.</span></span> 

#### <a name="the-keydownkeyup-bubbling-event"></a><span data-ttu-id="4021f-298">Das KeyDown/KeyUp-Bubbling-Ereignis</span><span class="sxs-lookup"><span data-stu-id="4021f-298">The KeyDown/KeyUp bubbling event</span></span> 

<span data-ttu-id="4021f-299">Im XAML wird ein Tastendruck so behandelt, als ob es nur eine Eingabe-Bubblingpipeline gibt.</span><span class="sxs-lookup"><span data-stu-id="4021f-299">In XAML, a keystroke is processed as if there is just one input bubbling pipeline.</span></span> <span data-ttu-id="4021f-300">Diese Eingabepipeline wird vom KeyDown/KeyUp-Ereignis und der Zeicheneingabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="4021f-300">This input pipeline is used by the KeyDown/KeyUp events and character input.</span></span> <span data-ttu-id="4021f-301">Wenn ein Element den Fokus hat, und der Benutzer eine NACH-UNTEN-TASTE drückt, wird ein KeyDown-Ereignis für das Element ausgelöst, gefolgt vom übergeordneten Element des Elements, und so weiter bis ganz nach oben in der Struktur, bis die args.Handle-Eigenschaft auf "true" gelangt.</span><span class="sxs-lookup"><span data-stu-id="4021f-301">For example, if an element has focus and the user presses a key down, a KeyDown event is raised on the element, followed by the parent of the element, and so on up the tree, until the args.Handled property is true.</span></span>

<span data-ttu-id="4021f-302">Das KeyDown-Ereignis wird auch von einigen Steuerelementen verwendet, um die integrierten Steuerungszugriffstasten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="4021f-302">The KeyDown event is also used by some controls to implement the built-in control accelerators.</span></span> <span data-ttu-id="4021f-303">Wenn eine Steuerung über eine Zugriffstaste verfügt, verarbeitet sie das KeyDown-Ereignis, das bedeutet, dass kein KeyDown-Eventbubbling auftritt.</span><span class="sxs-lookup"><span data-stu-id="4021f-303">When a control has a keyboard accelerator, it handles the KeyDown event, which means that there won't be KeyDown event bubbling.</span></span> <span data-ttu-id="4021f-304">Beispielsweise unterstützt die RichEditBox das Kopieren mit STRG+C.</span><span class="sxs-lookup"><span data-stu-id="4021f-304">For example, the RichEditBox supports copy with Ctrl+C.</span></span> <span data-ttu-id="4021f-305">Wenn STRG gedrückt wird, wird das KeyDown-Ereignis ausgelöst, und durchläuft ein Bubbling. Wenn der Benutzer allerdings gleichzeitig C drückt, wird das KeyDown-Ereignis als „Handled” gekennzeichnet und nicht mehr ausgelöst (es sei denn, der handledEventsToo-Parameter des [UIElement.AddHandler](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.addhandler) ist auf "true" festgelegt).</span><span class="sxs-lookup"><span data-stu-id="4021f-305">When Ctrl is pressed, the KeyDown event is fired and bubbles, but when the user presses C at the same time, the KeyDown event is marked Handled and is not raised (unless the handledEventsToo parameter of [UIElement.AddHandler](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.addhandler) is set to true).</span></span>

#### <a name="the-characterreceived-event"></a><span data-ttu-id="4021f-306">CharacterReceived-Ereignis</span><span class="sxs-lookup"><span data-stu-id="4021f-306">The CharacterReceived event</span></span>

<span data-ttu-id="4021f-307">Wenn das [CharacterReceived](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.CharacterReceived)-Ereignis nach dem [KeyDown](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.KeyDown) -Ereignis für Textsteuerelemente wie z.B. TextBox ausgelöst wird, können Sie die Zeicheneingabe im KeyDown-Ereignishandler abbrechen.</span><span class="sxs-lookup"><span data-stu-id="4021f-307">As the [CharacterReceived](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.CharacterReceived) event is fired after the [KeyDown](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.KeyDown) event for text controls such as TextBox, you can cancel character input in the KeyDown event handler.</span></span>

#### <a name="the-previewkeydown-and-previewkeyup-events"></a><span data-ttu-id="4021f-308">Die PreviewKeyDown- und PreviewKeyUp-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="4021f-308">The PreviewKeyDown and PreviewKeyUp events</span></span>

<span data-ttu-id="4021f-309">Die Vorschaueingabeereignisse werden vor allen anderen Ereignissen ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4021f-309">The preview input events are fired before any other events.</span></span> <span data-ttu-id="4021f-310">Wenn Sie diese Ereignisse nicht behandeln, wird die Zugriffstaste für das Element, das den Fokus hat ausgelöst, gefolgt vom KeyDown-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="4021f-310">If you don't handle these events, the accelerator for the element that has the focus is fired, followed by the KeyDown event.</span></span> <span data-ttu-id="4021f-311">Beide Ereignisse durchlaufen ein Bubbling, bis der Vorgang durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4021f-311">Both events bubble until handled.</span></span>


![<span data-ttu-id="4021f-312">Tastenereignissequenz](images/accelerators/accelerators_keyevents.png)
***Tastenereignissequenz***</span><span class="sxs-lookup"><span data-stu-id="4021f-312">Key event sequence](images/accelerators/accelerators_keyevents.png)
***Key event sequence***</span></span>

<span data-ttu-id="4021f-313">Reihenfolge der Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="4021f-313">Order of events:</span></span>

<span data-ttu-id="4021f-314">KeyDown-Vorschauereignisse...</span><span class="sxs-lookup"><span data-stu-id="4021f-314">Preview KeyDown events …</span></span>
<span data-ttu-id="4021f-315">App-Zugriffstaste OnKeyDown-Methode KeyDown-Ereignis App-Zugriffstaste auf die übergeordnete OnKeyDown-Methode für das übergeordnete KeyDown-Ereignis für das übergeordnete Ereignis (Bubbling bis zum Stammverzeichnis)...</span><span class="sxs-lookup"><span data-stu-id="4021f-315">App accelerator OnKeyDown method KeyDown event App accelerators on the parent OnKeyDown method on the parent KeyDown event on the parent (Bubbles to the root) …</span></span>
<span data-ttu-id="4021f-316">CharacterReceived-Ereignis PreviewKeyUp-Ereignis KeyUpEvents</span><span class="sxs-lookup"><span data-stu-id="4021f-316">CharacterReceived event PreviewKeyUp events KeyUpEvents</span></span>

<span data-ttu-id="4021f-317">Wenn das Zugriffstasten-Ereignis behandelt wird, wird das KeyDown-Ereignis ebenfalls als behandelt markiert.</span><span class="sxs-lookup"><span data-stu-id="4021f-317">When the accelerator event is handled, the KeyDown event is also marked as handled.</span></span> <span data-ttu-id="4021f-318">Das KeyUp-Ereignis wird nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="4021f-318">The KeyUp event remains unhandled.</span></span>

### <a name="resolving-accelerators"></a><span data-ttu-id="4021f-319">Beseitigen von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-319">Resolving accelerators</span></span>

<span data-ttu-id="4021f-320">Das Zugriffstasten-Ereignis durchläuft ein Bubblingereignis vom Element mit Fokus bis hin zum Stammverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="4021f-320">A keyboard accelerator event bubbles from the element that has focus up to the root.</span></span> <span data-ttu-id="4021f-321">Wenn das Ereignis nicht behandelt wird, sucht das XAML-Framework unbegrenzte App-Zugriffstasten außerhalb des Bereichs der App außerhalb der Bubbling-Pfads.</span><span class="sxs-lookup"><span data-stu-id="4021f-321">If the event isn't handled, the XAML framework looks for other unscoped app accelerators outside of the bubbling path.</span></span>

<span data-ttu-id="4021f-322">Wenn zwei Zugriffstasten mit der gleichen Tastenkombination definiert sind, wird die erste Zugriffstaste der visuellen Struktur aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="4021f-322">When two keyboard accelerators are defined with the same key combination, the first keyboard accelerator found on the visual tree is invoked.</span></span>

<span data-ttu-id="4021f-323">Bereichsbezogene Zugriffstasten werden nur aufgerufen, wenn sich der Fokus innerhalb eines bestimmten Bereichs befindet.</span><span class="sxs-lookup"><span data-stu-id="4021f-323">Scoped keyboard accelerators are invoked only when focus is inside a specific scope.</span></span> <span data-ttu-id="4021f-324">In einem Raster, das zahlreiche Steuerelemente enthält, kann z.B. eine Zugriffstaste für ein Steuerelement nur dann aufgerufen werden, wenn sich der Fokus innerhalb des Rasters („Bereichsbesitzer“) befindet.</span><span class="sxs-lookup"><span data-stu-id="4021f-324">For example, in a Grid that contains dozens of controls, a keyboard accelerator can be invoked for a control only when focus is within the Grid (the scope owner).</span></span>

### <a name="scoping-accelerators-programmatically"></a><span data-ttu-id="4021f-325">Eingrenzen programmgesteuerter Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-325">Scoping accelerators programmatically</span></span>

<span data-ttu-id="4021f-326">Die [UIElement.TryInvokeKeyboardAccelerator](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.tryinvokekeyboardaccelerator)-Methode ruft alle übereinstimmenden Zugriffstasten in die Unterstruktur des Elements auf.</span><span class="sxs-lookup"><span data-stu-id="4021f-326">The [UIElement.TryInvokeKeyboardAccelerator](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.tryinvokekeyboardaccelerator) method invokes any matching accelerators in the subtree of the element.</span></span>

<span data-ttu-id="4021f-327">Die [UIElement.OnProcessKeyboardAccelerators](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.onprocesskeyboardaccelerators) -Methode wird vor der Zugriffstaste ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4021f-327">The [UIElement.OnProcessKeyboardAccelerators](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.onprocesskeyboardaccelerators) method is executed before the keyboard accelerator.</span></span> <span data-ttu-id="4021f-328">Diese Methode übergibt ein [ProcessKeyboardAcceleratorArgs](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.processkeyboardacceleratoreventargs)-Objekt, das die Taste, den Modifizierer und einen booleschen Wert enthält, der angibt, ob die Zugriffstaste behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="4021f-328">This method passes a [ProcessKeyboardAcceleratorArgs](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.processkeyboardacceleratoreventargs) object that contains the key, the modifier, and a Boolean indicating whether the keyboard accelerator is handled.</span></span> <span data-ttu-id="4021f-329">Wenn dieser als behandelt markiert ist, durchläuft die Zugriffstaste ein Bubbling (wobei der externe Tastenkürzel nie aufgerufen wird).</span><span class="sxs-lookup"><span data-stu-id="4021f-329">If marked as handled, the keyboard accelerator bubbles (so the outside keyboard accelerator is never invoked).</span></span>

> [!NOTE]
> <span data-ttu-id="4021f-330">OnProcessKeyboardAccelerators werden immer ausgelöst, ob behandelt oder nicht (ähnlich wie das OnKeyDown-Ereignis).</span><span class="sxs-lookup"><span data-stu-id="4021f-330">OnProcessKeyboardAccelerators always fires, whether handled or not (similar to the OnKeyDown event).</span></span> <span data-ttu-id="4021f-331">Sie müssen überprüfen, ob das Ereignis als behandelt markiert wurde.</span><span class="sxs-lookup"><span data-stu-id="4021f-331">You must check whether the event was marked as handled.</span></span>

<span data-ttu-id="4021f-332">In diesem Beispiel verwenden wir OnProcessKeyboardAccelerators und TryInvokeKeyboardAccelerator, um den Bereich der Zugriffstasten auf das Seitenobjekt auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="4021f-332">In this example, we use OnProcessKeyboardAccelerators and TryInvokeKeyboardAccelerator to scope keyboard accelerators to the Page object:</span></span>

``` csharp
protected override void OnProcessKeyboardAccelerators(
  ProcessKeyboardAcceleratorArgs args)
{
  if(args.Handled != true)
  {
    this.TryInvokeKeyboardAccelerator(args);
    args.Handled = true;
  }
}
```

### <a name="localize-the-accelerators"></a><span data-ttu-id="4021f-333">Lokalisieren der Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-333">Localize the accelerators</span></span>

<span data-ttu-id="4021f-334">Es wird empfohlen, alle Zugriffstasten zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="4021f-334">We recommend localizing all keyboard accelerators.</span></span> <span data-ttu-id="4021f-335">Sie können dies anhand der standardmäßigen UWP-Ressourcendatei (.resw) und des x: Uid-Attributs in Ihrer XAML-Deklarationen durchführen.</span><span class="sxs-lookup"><span data-stu-id="4021f-335">You can do this with the standard UWP resources (.resw) file and the x:Uid attribute in your XAML declarations.</span></span> <span data-ttu-id="4021f-336">In diesem Beispiel lädt Windows-Runtime automatisch die Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="4021f-336">In this example, the Windows Runtime automatically loads the resources.</span></span>

![<span data-ttu-id="4021f-337">Lokalisierung der Zugriffstasten mit der UWP-Ressourcendatei](images/accelerators/accelerators_localization.png)
***Lokalisierung der Zugriffstasten mit der UWP-Ressourcendatei***</span><span class="sxs-lookup"><span data-stu-id="4021f-337">Keyboard accelerator localization with UWP resources file](images/accelerators/accelerators_localization.png)
***Keyboard accelerator localization with UWP resources file***</span></span>

``` xaml
<Button x:Uid="myButton" Click="OnSave">
  <Button.KeyboardAccelerators>
    <KeyboardAccelerator x:Uid="myKeyAccelerator" Modifiers="Control"/>
  </Button.KeyboardAccelerators>
</Button>
```

### <a name="setup-an-accelerator-programmatically"></a><span data-ttu-id="4021f-338">Einrichten einer programmgesteuerten Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="4021f-338">Setup an accelerator programmatically</span></span>

<span data-ttu-id="4021f-339">Hier ist ein Beispiel für das Definieren einer programmgesteuerten Zugriffstaste:</span><span class="sxs-lookup"><span data-stu-id="4021f-339">Here is an example of programmatically defining an accelerator:</span></span>

``` csharp
void AddAccelerator(
  VirtualKeyModifiers keyModifiers, 
  VirtualKey key, 
  TypedEventHandler<KeyboardAccelerator, KeyboardAcceleratorInvokedEventArgs> handler )
  {
    var accelerator = 
      new KeyboardAccelerator() 
      { 
        Modifiers = keyModifiers, Key = key
      };
    accelerator.Invoked = handler;
    this.KeyAccelerators.Add(accelerator);
  }
```

> [!NOTE]
> <span data-ttu-id="4021f-340">KeyboardAccelerator kann nicht freigegeben werden, der gleiche KeyboardAccelerator kann nicht mehreren Elementen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="4021f-340">KeyboardAccelerator is not shareable, the same KeyboardAccelerator can't be added to multiple elements.</span></span>

### <a name="override-keyboard-accelerator-behavior"></a><span data-ttu-id="4021f-341">Außerkraftsetzen des Verhaltens von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-341">Override keyboard accelerator behavior</span></span>

<span data-ttu-id="4021f-342">Sie können das Ereignis [KeyboardAccelerator.Invoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Invoked) bearbeiten, um das KeyboardAccelerator-Standardverhalten außer Kraft zu setzen.</span><span class="sxs-lookup"><span data-stu-id="4021f-342">You can handle the [KeyboardAccelerator.Invoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Invoked) event to override the default KeyboardAccelerator behavior.</span></span>

<span data-ttu-id="4021f-343">In diesem Beispiel wird veranschaulicht, wie Sie den Befehl „Alle auswählen“ (Zugriffstaste STRG+A) in einem benutzerdefinierten ListView-Steuerelement außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="4021f-343">This example shows how to override the "Select all" command (Ctrl+A keyboard accelerator) in a custom ListView control.</span></span> <span data-ttu-id="4021f-344">Wir haben außerdem die Handled-Eigenschaft auf „true“ festgelegt, um das weitere Bubbling des Ereignisses zu beenden.</span><span class="sxs-lookup"><span data-stu-id="4021f-344">We also set the Handled property to true to stop the event bubbling further.</span></span>

```csharp
public class MyListView : ListView
{
  …
  protected override void OnKeyboardAcceleratorInvoked(KeyboardAcceleratorInvokedEventArgs args) 
  {
    if(args.Accelerator.Key == VirtualKey.A 
      && args.Accelerator.Modifiers == KeyboardModifiers.Control)
    {
      CustomSelectAll(TypeOfSelection.OnlyNumbers); 
      args.Handled = true;
    }
  }
  …
}
```

## <a name="related-articles"></a><span data-ttu-id="4021f-345">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="4021f-345">Related articles</span></span>

* [<span data-ttu-id="4021f-346">Tastaturinteraktionen</span><span class="sxs-lookup"><span data-stu-id="4021f-346">Keyboard interactions</span></span>](keyboard-interactions.md)
* [<span data-ttu-id="4021f-347">Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="4021f-347">Access keys</span></span>](access-keys.md)

**<span data-ttu-id="4021f-348">Beispiele</span><span class="sxs-lookup"><span data-stu-id="4021f-348">Samples</span></span>**
* [<span data-ttu-id="4021f-349">XAML-Steuerelementekatalog (auch bekannt als XamlUiBasics)</span><span class="sxs-lookup"><span data-stu-id="4021f-349">XAML Controls Gallery (aka XamlUiBasics)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/c2aeaa588d9b134466bbd2cc387c8ff4018f151e/Samples/XamlUIBasics)


 

