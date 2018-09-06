---
author: Karl-Bridge-Microsoft
Description: Learn how accelerator keys can improve the usability and accessibility of UWP apps.
title: Zugriffstasten
label: Keyboard accelerators
template: detail.hbs
keywords: Tastatur, Zugriffstaste, Zugriffstasten, Tastenkombinationen, Barrierefreiheit, Navigation, Fokus, Text, Eingabe, Benutzerinteraktionen, Gamepad, Fernbedienung
ms.author: kbridge
ms.date: 10/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
pm-contact: chigy
design-contact: miguelrb
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: ce84debc3422f923c7c88aae1fa216665ef1ef0f
ms.sourcegitcommit: 914b38559852aaefe7e9468f6f53a7465bf36e30
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3399544"
---
# <a name="keyboard-accelerators"></a><span data-ttu-id="471df-103">Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-103">Keyboard accelerators</span></span>

![Surface Tastatur](images/accelerators/accelerators_hero2.png)

<span data-ttu-id="471df-105">Zugriffstasten (oder Tastaturkürzel) sind Tastenkombinationen, die die Benutzerfreundlichkeit und Barrierefreiheit Ihrer Windows-Anwendungen verbessern, indem Sie eine intuitive Möglichkeit für Benutzer bereitstellen, häufige Aktionen oder Befehle aufzurufen, ohne die App-Benutzeroberfläche zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="471df-105">Accelerator keys (or keyboard accelerators) are keyboard shortcuts that improve the usability and accessibility of your Windows applications by providing an intuitive way for users to invoke common actions or commands without navigating the app UI.</span></span>

<span data-ttu-id="471df-106">Weitere Details über die Navigation der Benutzeroberfläche einer Windows-Anwendung mit Tastenkombinationen finden Sie im Thema [Zugriffstasten](access-keys.md).</span><span class="sxs-lookup"><span data-stu-id="471df-106">See the [Access keys](access-keys.md) topic for details on navigating the UI of a Windows application with keyboard shortcuts.</span></span>

> [!NOTE]
> <span data-ttu-id="471df-107">Eine Tastatur ist unentbehrlich für Benutzer mit bestimmten körperlichen Einschränkungen (siehe [Barrierefreiheit der Tastaturnavigation](https://docs.microsoft.com/windows/uwp/accessibility/keyboard-accessibility)) und auch ein wichtiges Tool für Benutzer, die effizienter mit einer App interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="471df-107">A keyboard is indispensable for users with certain disabilities (see [Keyboard accessibility](https://docs.microsoft.com/windows/uwp/accessibility/keyboard-accessibility)), and is also an important tool for users who prefer it as a more efficient way to interact with an app.</span></span>

## <a name="overview"></a><span data-ttu-id="471df-108">Übersicht</span><span class="sxs-lookup"><span data-stu-id="471df-108">Overview</span></span>

<span data-ttu-id="471df-109">Zugriffstasten umfassen generell die Funktionstasten F1 bis F12 oder eine Kombination aus einer Standardtaste zusammen mit einer oder mehreren Zusatztasten (STRG, UMSCHALTTASTE).</span><span class="sxs-lookup"><span data-stu-id="471df-109">Accelerators typically include the function keys F1 through F12 or some combination of a standard key paired with one or more modifier keys (CTRL, Shift).</span></span>

> [!NOTE]
> <span data-ttu-id="471df-110">Die UWP-Plattform-Steuerelemente verfügen über integrierte Zugriffstasten.</span><span class="sxs-lookup"><span data-stu-id="471df-110">The UWP platform controls have built-in keyboard accelerators.</span></span> <span data-ttu-id="471df-111">ListView unterstützt beispielsweise STRG+A zum Auswählen aller Elemente der Liste und RichEditBox unterstützt STRG+TAB zum Einfügen eines Tabstopps in das Textfeld.</span><span class="sxs-lookup"><span data-stu-id="471df-111">For example, ListView supports Ctrl+A for selecting all the items in the list, and RichEditBox supports Ctrl+Tab for inserting a Tab in the text box.</span></span> <span data-ttu-id="471df-112">Diese integrierten Zugriffstasten werden als **Steuerungsabkürzungen** bezeichnet und werden nur ausgeführt, wenn der Fokus auf einem Element oder einem seiner untergeordneten Elemente liegt.</span><span class="sxs-lookup"><span data-stu-id="471df-112">These built-in keyboard accelerators are referred to as **control accelerators** and are executed only if the focus is on the element or one of its children.</span></span> <span data-ttu-id="471df-113">Von Ihnen definierte Zugriffstaste, die mithilfe der hier erläuterten Zugriffstasten APIs verwendet werden, werden als **App-Zugriffstasten** bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="471df-113">Accelerators defined by you using the keyboard accelerator APIs discussed here are referred to as **app accelerators**.</span></span>

<span data-ttu-id="471df-114">Zugriffstasten sind nicht für jede Aktion verfügbar, gehören allerdings häufig zu Befehlen, die in Menüs verfügbar gemacht werden (und sollten im Inhalt des Menüelements angegeben werden).</span><span class="sxs-lookup"><span data-stu-id="471df-114">Keyboard accelerators are not available for every action but are often associated with commands exposed in menus (and should be specified with the menu item content).</span></span> <span data-ttu-id="471df-115">Zugriffstasten können ebenfalls Aktionen zugeordnet werden, die nicht über entsprechende Menüelemente verfügen.</span><span class="sxs-lookup"><span data-stu-id="471df-115">Accelerators can also be associated with actions that do not have equivalent menu items.</span></span> <span data-ttu-id="471df-116">Da der Benutzer von den Menüs der Anwendungen abhängt, um den verfügbaren Befehlssatz zu ermitteln und zu erfahren, sollten Sie die Ermittlung der Zugriffstasten so einfach wie möglich machen (die Verwendung von Beschriftungen oder festgelegten Mustern kann dabei hilfreich sein).</span><span class="sxs-lookup"><span data-stu-id="471df-116">However, because users rely on an application's menus to discover and learn the available command set, you should try to make discovery of accelerators as easy as possible (using labels or established patterns can help with this).</span></span>

![In einer Menüelementbeschriftungen beschriebene Zugriffstasten](images/accelerators/accelerators_menuitemlabel.png)  
*<span data-ttu-id="471df-118">In einer Menüelementbeschriftungen beschriebene Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-118">Keyboard accelerators described in a menu item label</span></span>*

## <a name="when-to-use-keyboard-accelerators"></a><span data-ttu-id="471df-119">Verwendung von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-119">When to use keyboard accelerators</span></span>

<span data-ttu-id="471df-120">Es wird empfohlen, dass Sie Zugriffstasten überall in Ihrer UI angegeben, wo dies sinnvoll ist, und Zugriffstasten für alle benutzerdefinierten Steuerelemente unterstützen.</span><span class="sxs-lookup"><span data-stu-id="471df-120">We recommend that you specify keyboard accelerators wherever appropriate in your UI, and support accelerators in all custom controls.</span></span>

- <span data-ttu-id="471df-121">Zugriffstasten erleichtern den Zugriff auf Ihre App für Benutzer mit motorischen Einschränkungen, einschließlich der Benutzer, die jeweils nur eine Taste drücken können oder Probleme bei der Verwendung einer Maus haben.\*\*</span><span class="sxs-lookup"><span data-stu-id="471df-121">Keyboard accelerators make your app more accessible for users with motor disabilities, including those users who can press only one key at a time or have difficulty using a mouse.\*\*</span></span>

  <span data-ttu-id="471df-122">Eine gut durchdachte Tastatur-UI ist ein wichtiger Aspekt für die Barrierefreiheit von Software.</span><span class="sxs-lookup"><span data-stu-id="471df-122">A well-designed keyboard UI is an important aspect of software accessibility.</span></span> <span data-ttu-id="471df-123">Sie ermöglicht es Benutzern mit einer Sehbeeinträchtigung oder mit bestimmten motorischen Einschränkungen, in einer App zu navigieren und mit deren Features zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="471df-123">It enables users with vision impairments or who have certain motor disabilities to navigate an app and interact with its features.</span></span> <span data-ttu-id="471df-124">Diese Benutzer können u.U. keine Maus bedienen und sind auf verschiedene Hilfstechnologien wie etwa Tastaturerweiterungstools, Bildschirmtastaturen, Bildschirmlupen, Bildschirmleseprogramme oder die Möglichkeit der Spracheingabe angewiesen.</span><span class="sxs-lookup"><span data-stu-id="471df-124">Such users might not be able to operate a mouse and instead rely on various assistive technologies such as keyboard enhancement tools, on-screen keyboards, screen enlargers, screen readers, and voice input utilities.</span></span> <span data-ttu-id="471df-125">Für diese Benutzer ist eine vollständige Befehlsabdeckung entscheidend.</span><span class="sxs-lookup"><span data-stu-id="471df-125">For these users, comprehensive command coverage is crucial.</span></span>

- <span data-ttu-id="471df-126">Zugriffstasten machen Ihre App benutzerfreundlicher für erfahrene Benutzer, die über die Tastatur interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="471df-126">Keyboard accelerators make your app more usable for power users who prefer to interact through the keyboard.</span></span>

  <span data-ttu-id="471df-127">Erfahrene Benutzer haben oftmals eine starke Vorliebe für die Verwendung der Tastatur, da tastaturbasierte Befehle viel schneller eingegeben werden können. Zudem ist es dafür nicht erforderlich, die Hände von der Tastatur wegzubewegen.</span><span class="sxs-lookup"><span data-stu-id="471df-127">Experienced users often have a strong preference for using the keyboard because keyboard-based commands can be entered more quickly and don't require them to remove their hands from the keyboard.</span></span> <span data-ttu-id="471df-128">Für diese Benutzer sind Effizienz und Konsistenz entscheidend. Die Vollständigkeit hingegen ist nur für am häufigsten verwendeten Befehle wichtig.</span><span class="sxs-lookup"><span data-stu-id="471df-128">For these users, efficiency and consistency are crucial; comprehensiveness is important only for the most frequently used commands.</span></span>

## <a name="specify-a-keyboard-accelerator"></a><span data-ttu-id="471df-129">Angeben einer Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="471df-129">Specify a keyboard accelerator</span></span>

<span data-ttu-id="471df-130">Verwenden Sie die [KeyboardAccelerator](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.input.keyboardaccelerator.-ctor)-APIs zum Erstellen von Zugriffstasten in UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="471df-130">Use the [KeyboardAccelerator](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.input.keyboardaccelerator.-ctor) APIs to create keyboard accelerators in UWP apps.</span></span> <span data-ttu-id="471df-131">Mit diesen APIs müssen Sie keine verschiedenen KeyDown-Ereignisse behandeln, um die gedrückte Tastenkombination zu entdecken, und Sie können die Zugriffstasten in ihren App-Ressourcen lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="471df-131">With these APIs, you don't have to handle multiple KeyDown events to detect the key combination pressed, and you can localize accelerators in the app resources.</span></span>

<span data-ttu-id="471df-132">Es wird empfohlen, dass Sie Zugriffstasten für die am häufigsten verwendeten Aktionen in Ihrer App festlegen und sie mit den Bezeichnungen des Menüelements oder durch QuickInfos dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="471df-132">We recommend that you set keyboard accelerators for the most common actions in your app and document them using the menu item label or tooltip.</span></span> <span data-ttu-id="471df-133">In diesem Beispiel deklarieren wir Zugriffstasten nur für die Befehle „Umbenennen” und „Kopieren”.</span><span class="sxs-lookup"><span data-stu-id="471df-133">In this example, we declare keyboard accelerators only for the Rename and Copy commands.</span></span>

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
***<span data-ttu-id="471df-135">In einer QuickInfo beschriebene Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-135">Keyboard accelerator described in a tooltip</span></span>***

<span data-ttu-id="471df-136">Das [UIElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement)-Objekt verfügt über eine Sammlung an [Zugriffstasten](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator), d. h. [Zugriffstasten](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.KeyboardAccelerators), über die Sie Ihre benutzerdefinierten Zugriffstasten-Objekte angeben und die Tastenkombinationen für die Zugriffstaste festlegen:</span><span class="sxs-lookup"><span data-stu-id="471df-136">The [UIElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) object has a [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator) collection, [KeyboardAccelerators](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.KeyboardAccelerators), where you specify your custom KeyboardAccelerator objects and define the keystrokes for the keyboard accelerator:</span></span>

-   <span data-ttu-id="471df-137">**[Taste](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Key)** : ‑ der für die Zugriffstaste verwendete [VirtualKey](https://docs.microsoft.com/uwp/api/windows.system.virtualkey).</span><span class="sxs-lookup"><span data-stu-id="471df-137">**[Key](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Key)** - the [VirtualKey](https://docs.microsoft.com/uwp/api/windows.system.virtualkey) used for the keyboard accelerator.</span></span>

-   <span data-ttu-id="471df-138">**[Zusatztasten](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Modifiers)** : ‑ die für die Zugriffstaste verwendeten [VirtualKeyModifiers](https://docs.microsoft.com/uwp/api/windows.system.virtualkeymodifiers).</span><span class="sxs-lookup"><span data-stu-id="471df-138">**[Modifiers](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Modifiers)** – the [VirtualKeyModifiers](https://docs.microsoft.com/uwp/api/windows.system.virtualkeymodifiers) used for the keyboard accelerator.</span></span> <span data-ttu-id="471df-139">Wird der Modifizierer nicht angegeben, ist der Standardwert „None“.</span><span class="sxs-lookup"><span data-stu-id="471df-139">If Modifiers is not set, the default value is None.</span></span>

> [!NOTE]
> <span data-ttu-id="471df-140">Es werden Zugriffstasten, die aus einer einzelnen Taste bestehen (A, Löschen, F2, Leertaste, Esc, Multimediataste) und Zugriffstasten mit mehreren Tasten (STRG+UMSCHALT+M) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="471df-140">Single key (A, Delete, F2, Spacebar, Esc, Multimedia Key) accelerators and multi-key accelerators (Ctrl+Shift+M) are supported.</span></span> <span data-ttu-id="471df-141">Virtuelle Tasten in Gamepad werden jedoch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="471df-141">However, Gamepad virtual keys are not supported.</span></span>

## <a name="scoped-accelerators"></a><span data-ttu-id="471df-142">Bereichsbezogene Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-142">Scoped accelerators</span></span>

<span data-ttu-id="471df-143">Einige Zugriffstasten können nur in bestimmten Bereichen verwendet werden, während andere auf App-Ebene funktionieren.</span><span class="sxs-lookup"><span data-stu-id="471df-143">Some accelerators work only in specific scopes while others work app-wide.</span></span>

<span data-ttu-id="471df-144">Microsoft Outlook enthält beispielsweise die folgenden Zugriffstasten:</span><span class="sxs-lookup"><span data-stu-id="471df-144">For example, Microsoft Outlook includes the following accelerators:</span></span>
-   <span data-ttu-id="471df-145">Die Tasten STRG+B, STRG+I und ESC funktionieren nur für den Bereich des Formulars „E-Mail senden”</span><span class="sxs-lookup"><span data-stu-id="471df-145">Ctrl+B, Ctrl+I and ESC work only on the scope of the send email form</span></span>
-   <span data-ttu-id="471df-146">Die Tasten STRG+1 und STRG+2 funktionieren auf App-Ebene</span><span class="sxs-lookup"><span data-stu-id="471df-146">Ctrl+1 and Ctrl+2 work app-wide</span></span>

### <a name="context-menus"></a><span data-ttu-id="471df-147">Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="471df-147">Context menus</span></span>

<span data-ttu-id="471df-148">Aktionen im Kontextmenü beeinflussen nur bestimmte Bereiche oder Elemente wie z.B. ausgewählte Zeichen in einem Text-Editor oder Musiktitel in einer Wiedergabeliste.</span><span class="sxs-lookup"><span data-stu-id="471df-148">Context menu actions affect only specific areas or elements, such as the selected characters in a text editor or a song in a playlist.</span></span> <span data-ttu-id="471df-149">Aus diesem Grund wird empfohlen, den Umfang der Zugriffstasten für Elemente des Kontextmenüs auf das übergeordnete Element des Kontextmenüs festzulegen.</span><span class="sxs-lookup"><span data-stu-id="471df-149">For this reason, we recommend setting the scope of keyboard accelerators for context menu items to the parent of the context menu.</span></span>

<span data-ttu-id="471df-150">Verwenden Sie die [ScopeOwner](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.ScopeOwner)-Eigenschaft, um den Bereich der Zugriffstaste anzugeben.</span><span class="sxs-lookup"><span data-stu-id="471df-150">Use the [ScopeOwner](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.ScopeOwner) property to specify the scope of the keyboard accelerator.</span></span> <span data-ttu-id="471df-151">Dieser Code veranschaulicht, wie Sie ein Kontextmenü auf ListView mit bereichsbezogenen Zugriffstasten implementieren:</span><span class="sxs-lookup"><span data-stu-id="471df-151">This code demonstrates how to implement a context menu on a ListView with scoped keyboard accelerators:</span></span>

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

<span data-ttu-id="471df-152">Das ScopeOwner-Attribut des Elements MenuFlyoutItem.KeyboardAccelerators kennzeichnet die Zugriffstaste als bereichsbezogen, anstatt als global (der Standard ist null oder global).</span><span class="sxs-lookup"><span data-stu-id="471df-152">The ScopeOwner attribute of the MenuFlyoutItem.KeyboardAccelerators element marks the accelerator as scoped instead of global (the default is null, or global).</span></span> <span data-ttu-id="471df-153">Weitere Details finden Sie im Abschnitt **Beseitigen von Zugriffstasten** weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="471df-153">For more detail, see the **Resolving accelerators** section later in this topic.</span></span>

## <a name="invoke-a-keyboard-accelerator"></a><span data-ttu-id="471df-154">Aufrufen einer Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="471df-154">Invoke a keyboard accelerator</span></span> 

<span data-ttu-id="471df-155">Das [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator)-Objekt verwendet das [Steuerungsmuster der Benutzeroberflächenautomatisierung (UIA)](https://msdn.microsoft.com/library/windows/desktop/ee671194(v=vs.85).aspx), um Maßnahmen zu ergreifen, wenn eine Zugriffstaste aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="471df-155">The [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator) object uses the [UI Automation (UIA) control pattern](https://msdn.microsoft.com/library/windows/desktop/ee671194(v=vs.85).aspx) to take action when an accelerator is invoked.</span></span>

<span data-ttu-id="471df-156">Die UIA-Steuerungsmuster machen die häufig verwendeten Steuerelement-Funktionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="471df-156">The UIA [control patterns] expose common control functionality.</span></span> <span data-ttu-id="471df-157">Das „Button“-Steuerelement implementiert beispielsweise das [Invoke](https://msdn.microsoft.com/library/windows/desktop/ee671279(v=vs.85).aspx)-Steuerungsmuster, um den Klickvorgang zu unterstützen (generell wird ein Steuerelement durch klicken, doppelklicken oder drücken der Eingabetaste, einer vordefinierte Tastenkombination oder einer alternative Tastenkombination aufgerufen).</span><span class="sxs-lookup"><span data-stu-id="471df-157">For example, the Button control implements the [Invoke](https://msdn.microsoft.com/library/windows/desktop/ee671279(v=vs.85).aspx) control pattern to support the Click event (typically a control is invoked by clicking, double-clicking, or pressing Enter, a predefined keyboard shortcut, or some alternate combination of keystrokes).</span></span> <span data-ttu-id="471df-158">Wenn eine Zugriffstaste verwendet wird, um ein Steuerelement aufzurufen, sucht das XAML-Framework danach, ob das Steuerelement das Invoke-Steuerungsmuster implementiert und wenn dies der Fall ist, wird es aktiviert (es ist nicht erforderlich, das KeyboardAcceleratorInvoked-Ereignis durchzuführen).</span><span class="sxs-lookup"><span data-stu-id="471df-158">When a keyboard accelerator is used to invoke a control, the XAML framework looks up whether the control implements the Invoke control pattern and, if so, activates it (it is not necessary to listen for the KeyboardAcceleratorInvoked event).</span></span>

<span data-ttu-id="471df-159">Im folgenden Beispiel löst STRG+S das Click-Ereignis aus, da die Schaltfläche das Invoke-Muster implementiert.</span><span class="sxs-lookup"><span data-stu-id="471df-159">In the following example, Control+S triggers the Click event because the button implements the Invoke pattern.</span></span>

``` xaml 
<Button Content="Save" Click="OnSave">
  <Button.KeyboardAccelerators>
    <KeyboardAccelerator Key="S" Modifiers="Control" />
  </Button.KeyboardAccelerators>
</Button>
```

<span data-ttu-id="471df-160">Wenn ein Element mehrere Steuerungsmuster implementiert, kann nur ein einziges über die Zugriffstaste aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="471df-160">If an element implements multiple control patterns, only one can be activated through an accelerator.</span></span> <span data-ttu-id="471df-161">Die Prioritätsstufe der Steuerungsmuster ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="471df-161">The control patterns are prioritized as follows:</span></span>
1.  <span data-ttu-id="471df-162">Aufrufen (Taste)</span><span class="sxs-lookup"><span data-stu-id="471df-162">Invoke (Button)</span></span>
2.  <span data-ttu-id="471df-163">Ein-/Ausschalten (Kontrollkästchen)</span><span class="sxs-lookup"><span data-stu-id="471df-163">Toggle (Checkbox)</span></span>
3.  <span data-ttu-id="471df-164">Auswahl (ListView)</span><span class="sxs-lookup"><span data-stu-id="471df-164">Selection (ListView)</span></span>
4.  <span data-ttu-id="471df-165">Erweitern/Reduzieren (ComboBox)</span><span class="sxs-lookup"><span data-stu-id="471df-165">Expand/Collapse (ComboBox)</span></span> 

<span data-ttu-id="471df-166">Wenn keine Übereinstimmung identifiziert wird, wird die Zugriffstaste ungültig und es wird eine Debugmeldung angezeigt („Es wurden keine Automatisierungsmuster für diese Komponente gefunden.</span><span class="sxs-lookup"><span data-stu-id="471df-166">If no match is identified, the accelerator is invalid and a debug message is provided ("No automation patterns for this component found.</span></span> <span data-ttu-id="471df-167">Implementieren Sie das gewünschte Verhalten im Invoke-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="471df-167">Implement all desired behavior in the Invoked event.</span></span> <span data-ttu-id="471df-168">Wenn Sie „Handled“ im Ereignishandler auf „true“ festlegen, wird diese Meldung unterdrückt.“)</span><span class="sxs-lookup"><span data-stu-id="471df-168">Setting Handled to true in your event handler suppresses this message.")</span></span>

## <a name="custom-keyboard-accelerator-behavior"></a><span data-ttu-id="471df-169">Benutzerdefiniertes Verhalten der Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-169">Custom keyboard accelerator behavior</span></span>

<span data-ttu-id="471df-170">Das Invoke-Ereignis des [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator)-Objekts wird ausgelöst, wenn die Zugriffstaste ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="471df-170">The Invoked event of the [KeyboardAccelerator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator) object is fired when the accelerator is executed.</span></span> <span data-ttu-id="471df-171">Das [KeyboardAcceleratorInvokedEventArgs](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs)-Ereignisobjekt enthält die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="471df-171">The [KeyboardAcceleratorInvokedEventArgs](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorinvokedeventargs) event object includes the following properties:</span></span>
- <span data-ttu-id="471df-172">**Handled** (Boolesch): Bei Festlegen dieser Einstellung auf "true" wird verhindert, dass das Ereignis das Steuerungsmuster auslöst und das Eventbubbling der Zugriffstaste unterbricht.</span><span class="sxs-lookup"><span data-stu-id="471df-172">**Handled** (Boolean): Setting this to true prevents the event triggering the control pattern and stops accelerator event bubbling.</span></span> <span data-ttu-id="471df-173">Der Standard ist "False".</span><span class="sxs-lookup"><span data-stu-id="471df-173">The default is false.</span></span>
- <span data-ttu-id="471df-174">**Element** (DependencyObject): Das Objekt, das die Zugriffstaste enthält.</span><span class="sxs-lookup"><span data-stu-id="471df-174">**Element** (DependencyObject): The object that contains the accelerator.</span></span>

<span data-ttu-id="471df-175">Im Folgenden wird das Definieren einer Sammlung an Zugriffstasten und das Behandeln des aufgerufenen Ereignisses veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="471df-175">Here we demonstrate how to define a collection of keyboard accelerators and how to handle the Invoked event.</span></span>

``` xaml
<ListView x:Name="MyListView">
  <ListView.KeyboardAccelerators>
    <KeyboardAccelerator Key="A" Modifiers="Control,Shift" Invoked="SelectAllInvoked" />
    <KeyboardAccelerator Key="F5" Invoked="RefreshInvoked"  />
  </ListView.KeyboardAccelerators>
</ListView>   
```

``` csharp
void SelectAllInvoked (KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
  CustomSelectAll(MyListView);
  args.Handled = true;
}

void RefreshInvoked(KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
  Refresh(MyListView);
  args.Handled = true;
}
```

## <a name="disable-a-keyboard-accelerator"></a><span data-ttu-id="471df-176">Deaktivieren einer Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="471df-176">Disable a keyboard accelerator</span></span> 

<span data-ttu-id="471df-177">Wenn ein Steuerelement deaktiviert ist, wird die zugehörige Zugriffstaste ebenfalls deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="471df-177">If a control is disabled, the associated accelerator is also disabled.</span></span> <span data-ttu-id="471df-178">Im folgenden Beispiel ist die IsEnabled-Eigenschaft von ListView auf "false" festgelegt. Daher kann die zugehörige STRG+A-Zugriffstaste nicht aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="471df-178">In the following example, because the IsEnabled property of the ListView is set to false, the associated Control+A accelerator can't be invoked.</span></span>

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
        IsEnabled="False" />
    </TextBox.KeyboardAccelerators>
  </TextBox>

<ListView>
```

<span data-ttu-id="471df-179">Übergeordnete und untergeordnete Steuerelemente können die gleiche Zugriffstaste haben.</span><span class="sxs-lookup"><span data-stu-id="471df-179">Parent and child controls can share the same accelerator.</span></span> <span data-ttu-id="471df-180">In diesem Fall kann das übergeordnete Steuerelement auch aufgerufen werden, wenn das untergeordnete Element den Fokus hat und die Zugriffstaste deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="471df-180">In this case, the parent control can be invoked even if the child has focus and its accelerator is disabled.</span></span>

## <a name="screen-readers-and-keyboard-accelerators"></a><span data-ttu-id="471df-181">Sprachausgaben und Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-181">Screen readers and keyboard accelerators</span></span> 

<span data-ttu-id="471df-182">Bildschirmleseprogramme wie die die Sprachausgabe können dem Benutzer die Tastenkombination für die Zugriffstasten melden.</span><span class="sxs-lookup"><span data-stu-id="471df-182">Screen readers such as Narrator can announce the keyboard accelerator key combination to users.</span></span> <span data-ttu-id="471df-183">Standardmäßig ist dies jeder Modifizierer (in der Reihenfolge der VirtualModifiers-Enumeration), gefolgt von der Taste (und durch das "+"-Zeichen getrennt).</span><span class="sxs-lookup"><span data-stu-id="471df-183">By default, this is each modifier (in the VirtualModifiers enum order) followed by the key (and separated by "+" signs).</span></span> <span data-ttu-id="471df-184">Sie können dies durch die [AcceleratorKey](https://docs.microsoft.com/uwp/api/windows.ui.xaml.automation.automationproperties.AcceleratorKeyProperty) AutomationProperties angefügten Eigenschaft anpassen.</span><span class="sxs-lookup"><span data-stu-id="471df-184">You can customize this through the [AcceleratorKey](https://docs.microsoft.com/uwp/api/windows.ui.xaml.automation.automationproperties.AcceleratorKeyProperty) AutomationProperties attached property.</span></span> <span data-ttu-id="471df-185">Wenn mehr als eine Zugriffstaste angegeben wird, wird nur die erste Taste gemeldet.</span><span class="sxs-lookup"><span data-stu-id="471df-185">If more than one accelerator is specified, only the first is announced.</span></span>

<span data-ttu-id="471df-186">In diesem Beispiel gibt AutomationProperty.AcceleratorKey die Zeichenfolge "STRG + UMSCHALT+A" zurück:</span><span class="sxs-lookup"><span data-stu-id="471df-186">In this example, the AutomationProperty.AcceleratorKey returns the string "Control+Shift+A":</span></span>

``` xaml
<ListView x:Name="MyListView">
  <ListView.KeyboardAccelerators>

    <KeyboardAccelerator 
      Key="A" 
      Modifiers="Control,Shift" 
      Invoked="CustomSelectAllInvoked" />
      
    <KeyboardAccelerator 
      Key="F5" 
      Modifiers="None" 
      Invoked="RefreshInvoked" />

  </ListView.KeyboardAccelerators>

</ListView>   
```

> [!NOTE] 
> <span data-ttu-id="471df-187">Das Festlegen der AutomationProperties.AcceleratorKey-Funktion aktiviert nicht die Tastaturfunktion, es gibt es nur der UIA-Framework an, welche Tasten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="471df-187">Setting AutomationProperties.AcceleratorKey doesn't enable keyboard functionality, it only indicates to the UIA framework which keys are used.</span></span>

## <a name="common-keyboard-accelerators"></a><span data-ttu-id="471df-188">Allgemeine Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-188">Common Keyboard Accelerators</span></span>

<span data-ttu-id="471df-189">Es wird empfohlen, dass Sie Zugriffstasten für UWP-Apps konsistent sind.</span><span class="sxs-lookup"><span data-stu-id="471df-189">We recommend that you make keyboard accelerators consistent across UWP applications.</span></span> <span data-ttu-id="471df-190">Benutzer müssen sich die Zugriffstasten merken und das gleiche (oder ähnliche) Ergebnis erwarten.</span><span class="sxs-lookup"><span data-stu-id="471df-190">Users have to memorize keyboard accelerators and expect the same (or similar) results.</span></span>

<span data-ttu-id="471df-191">Aufgrund der unterschiedlichen Funktionen ist dies allerdings nicht immer in allen Apps möglich.</span><span class="sxs-lookup"><span data-stu-id="471df-191">This might not always be possible due to differences in functionality across apps.</span></span>

| **<span data-ttu-id="471df-192">Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="471df-192">Editing</span></span>** | **<span data-ttu-id="471df-193">Allgemeine Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="471df-193">Common Keyboard Accelerator</span></span>** |
| ------------- | ----------------------------------- |
| <span data-ttu-id="471df-194">Den Bearbeitungsmodus beginnen</span><span class="sxs-lookup"><span data-stu-id="471df-194">Begin editing mode</span></span> | <span data-ttu-id="471df-195">STRG+E</span><span class="sxs-lookup"><span data-stu-id="471df-195">Ctrl + E</span></span> |
| <span data-ttu-id="471df-196">Alle Elemente in einem Steuerelement mit angezeigtem Fokus oder Fenster auswählen</span><span class="sxs-lookup"><span data-stu-id="471df-196">Select all items in a focused control or window</span></span> | <span data-ttu-id="471df-197">STRG+A</span><span class="sxs-lookup"><span data-stu-id="471df-197">Ctrl + A</span></span> |
| <span data-ttu-id="471df-198">Suchen und Ersetzen</span><span class="sxs-lookup"><span data-stu-id="471df-198">Search and replace</span></span> | <span data-ttu-id="471df-199">STRG+H</span><span class="sxs-lookup"><span data-stu-id="471df-199">Ctrl + H</span></span> |
| <span data-ttu-id="471df-200">Rückgängig machen</span><span class="sxs-lookup"><span data-stu-id="471df-200">Undo</span></span> | <span data-ttu-id="471df-201">STRG+Z</span><span class="sxs-lookup"><span data-stu-id="471df-201">Ctrl + Z</span></span> |
| <span data-ttu-id="471df-202">Wiederholen</span><span class="sxs-lookup"><span data-stu-id="471df-202">Redo</span></span> | <span data-ttu-id="471df-203">STRG+Y</span><span class="sxs-lookup"><span data-stu-id="471df-203">Ctrl + Y</span></span> |
| <span data-ttu-id="471df-204">Die Auswahl löschen und in die Zwischenablage kopieren</span><span class="sxs-lookup"><span data-stu-id="471df-204">Delete selection and copy it to the clipboard</span></span> | <span data-ttu-id="471df-205">STRG+X</span><span class="sxs-lookup"><span data-stu-id="471df-205">Ctrl + X</span></span> |
| <span data-ttu-id="471df-206">Auswahl in die Zwischenablage kopieren</span><span class="sxs-lookup"><span data-stu-id="471df-206">Copy selection to the clipboard</span></span> | <span data-ttu-id="471df-207">STRG+C, STRG+EINFG</span><span class="sxs-lookup"><span data-stu-id="471df-207">Ctrl + C, Ctrl + Insert</span></span> |
| <span data-ttu-id="471df-208">Inhalte aus der Zwischenablage einfügen</span><span class="sxs-lookup"><span data-stu-id="471df-208">Paste the contents of the clipboard</span></span> | <span data-ttu-id="471df-209">STRG+V, UMSCHALT+EINFG</span><span class="sxs-lookup"><span data-stu-id="471df-209">Ctrl + V, Shift + Insert</span></span> |
| <span data-ttu-id="471df-210">Den Inhalt der Zwischenablage einfügen (mit Optionen).</span><span class="sxs-lookup"><span data-stu-id="471df-210">Paste the contents of the clipboard (with options)</span></span> | <span data-ttu-id="471df-211">STRG+ALT+V</span><span class="sxs-lookup"><span data-stu-id="471df-211">Ctrl + Alt + V</span></span> |
| <span data-ttu-id="471df-212">Element umzubenennen</span><span class="sxs-lookup"><span data-stu-id="471df-212">Rename an item</span></span> | <span data-ttu-id="471df-213">F2</span><span class="sxs-lookup"><span data-stu-id="471df-213">F2</span></span> |
| <span data-ttu-id="471df-214">Neues Element hinzufügen</span><span class="sxs-lookup"><span data-stu-id="471df-214">Add a new item</span></span> | <span data-ttu-id="471df-215">STRG+N</span><span class="sxs-lookup"><span data-stu-id="471df-215">Ctrl + N</span></span> |
| <span data-ttu-id="471df-216">Neues zweites Element hinzufügen</span><span class="sxs-lookup"><span data-stu-id="471df-216">Add a new secondary item</span></span> | <span data-ttu-id="471df-217">STRG+UMSCHALT+N</span><span class="sxs-lookup"><span data-stu-id="471df-217">Ctrl + Shift + N</span></span> |
| <span data-ttu-id="471df-218">Ausgewähltes Element löschen (mit Rückgängigmachen)</span><span class="sxs-lookup"><span data-stu-id="471df-218">Delete selected item (with undo)</span></span> | <span data-ttu-id="471df-219">ENTF, STRG+D</span><span class="sxs-lookup"><span data-stu-id="471df-219">Del, Ctrl+D</span></span> |
| <span data-ttu-id="471df-220">Ausgewähltes Element löschen (ohne Rückgängigmachen)</span><span class="sxs-lookup"><span data-stu-id="471df-220">Delete selected item (without undo)</span></span> | <span data-ttu-id="471df-221">UMSCHALT+ENTF</span><span class="sxs-lookup"><span data-stu-id="471df-221">Shift + Del</span></span> |
| <span data-ttu-id="471df-222">Fett</span><span class="sxs-lookup"><span data-stu-id="471df-222">Bold</span></span> | <span data-ttu-id="471df-223">STRG+B</span><span class="sxs-lookup"><span data-stu-id="471df-223">Ctrl + B</span></span> |
| <span data-ttu-id="471df-224">Unterstreichen</span><span class="sxs-lookup"><span data-stu-id="471df-224">Underline</span></span> | <span data-ttu-id="471df-225">STRG+U</span><span class="sxs-lookup"><span data-stu-id="471df-225">Ctrl + U</span></span> |
| <span data-ttu-id="471df-226">Kursiv</span><span class="sxs-lookup"><span data-stu-id="471df-226">Italic</span></span> | <span data-ttu-id="471df-227">STRG+I</span><span class="sxs-lookup"><span data-stu-id="471df-227">Ctrl + I</span></span> |

| **<span data-ttu-id="471df-228">Navigation</span><span class="sxs-lookup"><span data-stu-id="471df-228">Navigation</span></span>** | |
| ------------- | ----------------------------------- |
| <span data-ttu-id="471df-229">Nach Inhalten in einem Steuerelement mit Fokus oder Fenster suchen</span><span class="sxs-lookup"><span data-stu-id="471df-229">Find content in a focused control or Window</span></span> | <span data-ttu-id="471df-230">STRG+F</span><span class="sxs-lookup"><span data-stu-id="471df-230">Ctrl + F</span></span> |
| <span data-ttu-id="471df-231">Das nächste Suchergebnis anzeigen</span><span class="sxs-lookup"><span data-stu-id="471df-231">Go to the next search result</span></span> | <span data-ttu-id="471df-232">F3</span><span class="sxs-lookup"><span data-stu-id="471df-232">F3</span></span> |

| **<span data-ttu-id="471df-233">Andere Aktionen</span><span class="sxs-lookup"><span data-stu-id="471df-233">Other Actions</span></span>** | |
| ------------- | ----------------------------------- |
| <span data-ttu-id="471df-234">Favoriten hinzufügen</span><span class="sxs-lookup"><span data-stu-id="471df-234">Add favorites</span></span> | <span data-ttu-id="471df-235">STRG+D</span><span class="sxs-lookup"><span data-stu-id="471df-235">Ctrl + D</span></span> | 
| <span data-ttu-id="471df-236">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="471df-236">Refresh</span></span> | <span data-ttu-id="471df-237">F5 oder STRG+R</span><span class="sxs-lookup"><span data-stu-id="471df-237">F5 or Ctrl + R</span></span> | 
| <span data-ttu-id="471df-238">Vergrößern</span><span class="sxs-lookup"><span data-stu-id="471df-238">Zoom In</span></span> | <span data-ttu-id="471df-239">STRG++</span><span class="sxs-lookup"><span data-stu-id="471df-239">Ctrl + +</span></span> | 
| <span data-ttu-id="471df-240">Verkleinern</span><span class="sxs-lookup"><span data-stu-id="471df-240">Zoom out</span></span> | <span data-ttu-id="471df-241">STRG+-</span><span class="sxs-lookup"><span data-stu-id="471df-241">Ctrl + -</span></span> | 
| <span data-ttu-id="471df-242">Auf Standardansicht zoomen</span><span class="sxs-lookup"><span data-stu-id="471df-242">Zoom to default view</span></span> | <span data-ttu-id="471df-243">STRG + 0</span><span class="sxs-lookup"><span data-stu-id="471df-243">Ctrl + 0</span></span> | 
| <span data-ttu-id="471df-244">Speichern</span><span class="sxs-lookup"><span data-stu-id="471df-244">Save</span></span> | <span data-ttu-id="471df-245">STRG+S</span><span class="sxs-lookup"><span data-stu-id="471df-245">Ctrl + S</span></span> | 
| <span data-ttu-id="471df-246">Schließen</span><span class="sxs-lookup"><span data-stu-id="471df-246">Close</span></span> | <span data-ttu-id="471df-247">STRG+W</span><span class="sxs-lookup"><span data-stu-id="471df-247">Ctrl + W</span></span> | 
| <span data-ttu-id="471df-248">Drucken</span><span class="sxs-lookup"><span data-stu-id="471df-248">Print</span></span> | <span data-ttu-id="471df-249">STRG+P</span><span class="sxs-lookup"><span data-stu-id="471df-249">Ctrl + P</span></span> | 

<span data-ttu-id="471df-250">Beachten Sie, dass einige der Kombinationen nicht für lokalisierte Versionen von Windows gelten.</span><span class="sxs-lookup"><span data-stu-id="471df-250">Notice that some of the combinations are not valid for localized versions of Windows.</span></span> <span data-ttu-id="471df-251">In der spanischen Version von Windows wird STRG+N anstelle von STRG+B zur Fettformatierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="471df-251">For example, in the Spanish version of Windows, Ctrl+N is used for bold instead of Ctrl+B.</span></span> <span data-ttu-id="471df-252">Es wird empfohlen, lokalisierte Zugriffstasten bereitzustellen, wenn die App lokalisiert ist.</span><span class="sxs-lookup"><span data-stu-id="471df-252">We recommend providing localized keyboard accelerators if the app is localized.</span></span>

## <a name="usability-affordances-for-keyboard-accelerators"></a><span data-ttu-id="471df-253">Nutzbarkeitsangebote für Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-253">Usability affordances for keyboard accelerators</span></span>

### <a name="tooltips"></a><span data-ttu-id="471df-254">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="471df-254">Tooltips</span></span>

<span data-ttu-id="471df-255">Da Zugriffstasten in der Regel nicht direkt in der Benutzeroberfläche Ihrer UWP-Anwendung beschrieben sind, können Sie die Auffindbarkeit durch [QuickInfos](../controls-and-patterns/tooltips.md) verbessern, die automatisch angezeigt werden, wenn der Benutzer den Fokus auf ein Steuerelement setzt bzw. die Maus drückt und hält oder mit dem Mauszeiger darauf zeigt.</span><span class="sxs-lookup"><span data-stu-id="471df-255">As keyboard accelerators are not typically described directly in the UI of your UWP application, you can improve discoverability through [tooltips](../controls-and-patterns/tooltips.md), which display automatically when the user moves focus to, presses and holds, or hovers the mouse pointer over a control.</span></span> <span data-ttu-id="471df-256">Die QuickInfo kann erkennen, ob ein Steuerelement über eine zugeordnete Zugriffstaste verfügt und, wenn ja, welche Tastenkombination als Zugriffstaste verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="471df-256">The tooltip can identify whether a control has an associated keyboard accelerator and, if so, what the accelerator key combination is.</span></span>

**<span data-ttu-id="471df-257">Windows 10, Version 1803 (April 2018 Update) und höher</span><span class="sxs-lookup"><span data-stu-id="471df-257">Windows 10, Version 1803 (April 2018 Update) and newer</span></span>**

<span data-ttu-id="471df-258">Standardmäßig wenn Zugriffstasten deklariert sind, stellen Sie alle Steuerelemente (außer [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem) und [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem)) die entsprechenden Tastenkombination in einer QuickInfo.</span><span class="sxs-lookup"><span data-stu-id="471df-258">By default, When keyboard accelerators are declared, all controls (except [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem) and [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem)) present the corresponding key combinations in a tooltip.</span></span>

> [!NOTE] 
> <span data-ttu-id="471df-259">Wenn ein Steuerelement mehrere Zugriffstasten definiert ist, wird nur die erste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="471df-259">If a control has more than one accelerator defined, only the first is presented.</span></span>

![QuickInfo für Zugriffstasten](images/accelerators/accelerators_tooltip_savebutton_small.png)

*<span data-ttu-id="471df-261">Zugriffstastenkombination in QuickInfo</span><span class="sxs-lookup"><span data-stu-id="471df-261">Accelerator key combo in tooltip</span></span>*

<span data-ttu-id="471df-262">Für die [Schaltfläche](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button), [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton)und [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) -Objekte die Zugriffstaste des Steuerelements Standard-Tooltip angefügt.</span><span class="sxs-lookup"><span data-stu-id="471df-262">For [Button](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button), [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton), and [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) objects, the keyboard accelerator is appended to the control's default tooltip.</span></span> <span data-ttu-id="471df-263">Für [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) und [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem)) Objekte, die Zugriffstaste wird mit den Flyout-Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="471df-263">For [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) and [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem)) objects, the keyboard accelerator is displayed with the flyout text.</span></span>

> [!NOTE]
> <span data-ttu-id="471df-264">Die Angabe einer QuickInfos setzt (Siehe Button1 im folgenden Beispiel) dieses Verhalten.</span><span class="sxs-lookup"><span data-stu-id="471df-264">Specifying a tooltip (see Button1 in the following example) overrides this behavior.</span></span>

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

*<span data-ttu-id="471df-266">Schaltfläche standardmäßig QuickInfo angefügte Zugriffstastenkombination</span><span class="sxs-lookup"><span data-stu-id="471df-266">Accelerator key combo appended to Button's default tooltip</span></span>*

```xaml
<AppBarButton Icon="Save" Label="Save">
    <AppBarButton.KeyboardAccelerators>
        <KeyboardAccelerator Key="S" Modifiers="Control"/>
    </AppBarButton.KeyboardAccelerators>
</AppBarButton>
```

![QuickInfo für Zugriffstasten](images/accelerators/accelerators-appbarbutton-small.png)

*<span data-ttu-id="471df-268">AppBarButton Standard QuickInfo angefügte Zugriffstastenkombination</span><span class="sxs-lookup"><span data-stu-id="471df-268">Accelerator key combo appended to AppBarButton's default tooltip</span></span>*

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

*<span data-ttu-id="471df-270">In MenuFlyoutItems Text angefügte Zugriffstastenkombination</span><span class="sxs-lookup"><span data-stu-id="471df-270">Accelerator key combo appended to MenuFlyoutItem's text</span></span>*

<span data-ttu-id="471df-271">Sie können das Darstellungsverhalten über die Eigenschaft [KeyboardAcceleratorPlacementMode](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.KeyboardAcceleratorPlacementMode) steuern, die zwei Werte akzeptiert: [Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorplacementmode) oder [Hidden](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorplacementmode).</span><span class="sxs-lookup"><span data-stu-id="471df-271">Control the presentation behavior by using the [KeyboardAcceleratorPlacementMode](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.KeyboardAcceleratorPlacementMode) property, which accepts two values: [Auto](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorplacementmode) or [Hidden](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardacceleratorplacementmode).</span></span>    

```xaml
<Button Content="Save" Click="OnSave" KeyboardAcceleratorPlacementMode="Auto">
    <Button.KeyboardAccelerators>
        <KeyboardAccelerator Key="S" Modifiers="Control" />
    </Button.KeyboardAccelerators>
</Button>
```

<span data-ttu-id="471df-272">In einigen Fällen müssen Sie möglicherweise eine QuickInfo in Bezug zu einem anderen Element darstellen (in der Regel ein Containerobjekt).</span><span class="sxs-lookup"><span data-stu-id="471df-272">In some cases, you might need to present a tooltip relative to another element (typically a container object).</span></span> <span data-ttu-id="471df-273">Beispielsweise ein Pivot-Steuerelement, das die QuickInfo für ein PivotItem mit dem Pivot-Header anzeigt.</span><span class="sxs-lookup"><span data-stu-id="471df-273">For example, a Pivot control that displays the tooltip for a PivotItem with the Pivot header.</span></span> 

<span data-ttu-id="471df-274">Im Folgenden ist gezeigt, wie Sie die Eigenschaft KeyboardAcceleratorPlacementTarget verwenden, um die Tastenkombination für die Zugriffstaste für eine Schaltfläche zum Speichern mit dem Grid-Container anstelle der Schaltfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="471df-274">Here, we show how to use the KeyboardAcceleratorPlacementTarget property to display the keyboard accelerator key combination for a Save button with the Grid container instead of the button.</span></span>

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

### <a name="labels"></a><span data-ttu-id="471df-275">Beschriftungen</span><span class="sxs-lookup"><span data-stu-id="471df-275">Labels</span></span>

<span data-ttu-id="471df-276">In einigen Fällen wird empfohlen, die Beschriftung eines Steuerelements zu verwenden, um zu identifizieren, ob das Steuerelement über eine zugeordnete Zugriffstaste verfügt und, wenn ja, welche Tastenkombination als Zugriffstaste verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="471df-276">In some cases, we recommend using a control's label to identify whether the control has an associated keyboard accelerator and, if so, what the accelerator key combination is.</span></span> 

<span data-ttu-id="471df-277">Bei einigen Plattformsteuerelementen geschieht dies standardmäßig, insbesondere bei den Objekten [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem) und [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem), während es bei [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) und [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) dazu kommt, wenn sie im Überlaufmenü der [CommandBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="471df-277">Some platform controls do this by default, specifically the [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem) and [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem) objects, while the [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) and the [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) do it when they appear in the overflow menu of the [CommandBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar).</span></span>

![In einer Menüelementbeschriftungen beschriebene Zugriffstasten](images/accelerators/accelerators_menuitemlabel.png)  
*<span data-ttu-id="471df-279">In einer Menüelementbeschriftungen beschriebene Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-279">Keyboard accelerators described in a menu item label</span></span>*

<span data-ttu-id="471df-280">Sie können den Standardtext für die Beschriftung der Zugriffstaste über die Eigenschaft [KeyboardAcceleratorTextOverride](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton.KeyboardAcceleratorTextOverride) der Steuerelemente [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem), [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem), [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton) und [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) überschreiben (verwenden Sie ein Leerzeichen, wenn kein Text vorhanden sein soll).</span><span class="sxs-lookup"><span data-stu-id="471df-280">You can override the default accelerator text for the label through the [KeyboardAcceleratorTextOverride](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton.KeyboardAcceleratorTextOverride) property of the [MenuFlyoutItem](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyoutItem), [ToggleMenuFlyoutItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.togglemenuflyoutitem), [AppBarButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton), and [AppBarToggleButton](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbartogglebutton) controls (use a single space for no text).</span></span> 

> [!NOTE] 
> <span data-ttu-id="471df-281">Der überschreibende Text wird nicht angezeigt, wenn das System keine angeschlossene Tastatur erkennen kann (Sie können dies selbst über die Eigenschaft [KeyboardPresent](https://docs.microsoft.com/uwp/api/windows.devices.input.keyboardcapabilities.KeyboardPresent) überprüfen).</span><span class="sxs-lookup"><span data-stu-id="471df-281">The override text is not be presented if the system cannot detect an attached keyboard (you can check this yourself through the [KeyboardPresent](https://docs.microsoft.com/uwp/api/windows.devices.input.keyboardcapabilities.KeyboardPresent) property).</span></span>

## <a name="advanced-concepts"></a><span data-ttu-id="471df-282">Erweiterte Konzepte</span><span class="sxs-lookup"><span data-stu-id="471df-282">Advanced Concepts</span></span>

<span data-ttu-id="471df-283">In diesem Abschnitt erläutern wir einige einfache Aspekte der Zugriffstasten.</span><span class="sxs-lookup"><span data-stu-id="471df-283">Here, we review some low-level aspects of keyboard accelerators.</span></span>

### <a name="when-an-accelerator-is-invoked"></a><span data-ttu-id="471df-284">Wenn eine Zugriffstaste aufgerufen wird</span><span class="sxs-lookup"><span data-stu-id="471df-284">When an accelerator is invoked</span></span>

<span data-ttu-id="471df-285">Zugriffstasten bestehen aus zwei Arten von Tasten: Modifizierer und Nicht-Modifizierer.</span><span class="sxs-lookup"><span data-stu-id="471df-285">Accelerators are composed of two types of keys: modifiers and non-modifiers.</span></span> <span data-ttu-id="471df-286">Zu den Zusatztasten gehören die Umschalttaste, Menü, STRG und die Windows-Taste, die über [VirtualKeyModifiers](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.System.VirtualKeyModifiers) verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="471df-286">Modifier keys include Shift, Menu, Control, and the Windows key, which are exposed through [VirtualKeyModifiers](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.System.VirtualKeyModifiers).</span></span> <span data-ttu-id="471df-287">Nichtzusatztasten sind alle virtuellen Schlüssel wie z.B. Löschen, F3, die Leertaste, Esc und alle alphanumerischen und Satzzeichen-Tasten.</span><span class="sxs-lookup"><span data-stu-id="471df-287">Non-modifiers are any virtual key, such as Delete, F3, Spacebar, Esc, and all alphanumeric and punctuation keys.</span></span> <span data-ttu-id="471df-288">Eine Zugriffstaste wird aufgerufen, wenn Benutzer eine andere Taste drücken, während sie eine oder mehrere Zusatztasten gedrückt halten.</span><span class="sxs-lookup"><span data-stu-id="471df-288">A keyboard accelerator is invoked when the user presses a non-modifier key while they press and hold one or more modifier keys.</span></span> <span data-ttu-id="471df-289">Wenn der Benutzer beispielsweise STRG+UMSCHALT+M drückt und dann M drückt, überprüft das Framework die Modifizierer (STRG und UMSCHALTTASTE) und die Zugriffstaste wird ausgelöst, wenn sie vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="471df-289">For example, if the user presses Ctrl+Shift+M, when the user presses M, the framework checks the modifiers (Ctrl and Shift) and fires the accelerator, if it exists.</span></span>

> [!NOTE]
> <span data-ttu-id="471df-290">Standardmäßig wird die Zugriffstaste automatisch wiederholt (z.B., wenn der Benutzer STRG+UMSCHALT drückt und dann M gedrückt hält, wird die Zugriffstaste wiederholt aufgerufen, bis M losgelassen wird).</span><span class="sxs-lookup"><span data-stu-id="471df-290">By design, the accelerator autorepeats (for example, when the user presses Ctrl+Shift and then holds down M, the accelerator is invoked repeatedly until M is released).</span></span> <span data-ttu-id="471df-291">Dieses Verhalten kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="471df-291">This behavior cannot be modified.</span></span>

### <a name="input-event-priority"></a><span data-ttu-id="471df-292">Priorität des Eingabeereignises</span><span class="sxs-lookup"><span data-stu-id="471df-292">Input event priority</span></span>
<span data-ttu-id="471df-293">Eingabeereignisse treten in einer bestimmten Reihenfolge auf, die Sie je nach Anforderungen der App abfangen und behandeln können.</span><span class="sxs-lookup"><span data-stu-id="471df-293">Input events occur in a specific sequence that you can intercept and handle based on the requirements of your app.</span></span> 

#### <a name="the-keydownkeyup-bubbling-event"></a><span data-ttu-id="471df-294">Das KeyDown/KeyUp-Bubbling-Ereignis</span><span class="sxs-lookup"><span data-stu-id="471df-294">The KeyDown/KeyUp bubbling event</span></span> 

<span data-ttu-id="471df-295">Im XAML wird ein Tastendruck so behandelt, als ob es nur eine Eingabe-Bubblingpipeline gibt.</span><span class="sxs-lookup"><span data-stu-id="471df-295">In XAML, a keystroke is processed as if there is just one input bubbling pipeline.</span></span> <span data-ttu-id="471df-296">Diese Eingabepipeline wird vom KeyDown/KeyUp-Ereignis und der Zeicheneingabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="471df-296">This input pipeline is used by the KeyDown/KeyUp events and character input.</span></span> <span data-ttu-id="471df-297">Wenn ein Element den Fokus hat, und der Benutzer eine NACH-UNTEN-TASTE drückt, wird ein KeyDown-Ereignis für das Element ausgelöst, gefolgt vom übergeordneten Element des Elements, und so weiter bis ganz nach oben in der Struktur, bis die args.Handle-Eigenschaft auf "true" gelangt.</span><span class="sxs-lookup"><span data-stu-id="471df-297">For example, if an element has focus and the user presses a key down, a KeyDown event is raised on the element, followed by the parent of the element, and so on up the tree, until the args.Handled property is true.</span></span>

<span data-ttu-id="471df-298">Das KeyDown-Ereignis wird auch von einigen Steuerelementen verwendet, um die integrierten Steuerungszugriffstasten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="471df-298">The KeyDown event is also used by some controls to implement the built-in control accelerators.</span></span> <span data-ttu-id="471df-299">Wenn eine Steuerung über eine Zugriffstaste verfügt, verarbeitet sie das KeyDown-Ereignis, das bedeutet, dass kein KeyDown-Eventbubbling auftritt.</span><span class="sxs-lookup"><span data-stu-id="471df-299">When a control has a keyboard accelerator, it handles the KeyDown event, which means that there won't be KeyDown event bubbling.</span></span> <span data-ttu-id="471df-300">Beispielsweise unterstützt die RichEditBox das Kopieren mit STRG+C.</span><span class="sxs-lookup"><span data-stu-id="471df-300">For example, the RichEditBox supports copy with Ctrl+C.</span></span> <span data-ttu-id="471df-301">Wenn STRG gedrückt wird, wird das KeyDown-Ereignis ausgelöst, und durchläuft ein Bubbling. Wenn der Benutzer allerdings gleichzeitig C drückt, wird das KeyDown-Ereignis als „Handled” gekennzeichnet und nicht mehr ausgelöst (es sei denn, der handledEventsToo-Parameter des [UIElement.AddHandler](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Xaml.UIElement.AddHandler) ist auf "true" festgelegt).</span><span class="sxs-lookup"><span data-stu-id="471df-301">When Ctrl is pressed, the KeyDown event is fired and bubbles, but when the user presses C at the same time, the KeyDown event is marked Handled and is not raised (unless the handledEventsToo parameter of [UIElement.AddHandler](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Xaml.UIElement.AddHandler) is set to true).</span></span>

#### <a name="the-characterreceived-event"></a><span data-ttu-id="471df-302">CharacterReceived-Ereignis</span><span class="sxs-lookup"><span data-stu-id="471df-302">The CharacterReceived event</span></span>

<span data-ttu-id="471df-303">Wenn das [CharacterReceived](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.CharacterReceived)-Ereignis nach dem [KeyDown](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.KeyDown) -Ereignis für Textsteuerelemente wie z.B. TextBox ausgelöst wird, können Sie die Zeicheneingabe im KeyDown-Ereignishandler abbrechen.</span><span class="sxs-lookup"><span data-stu-id="471df-303">As the [CharacterReceived](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.CharacterReceived) event is fired after the [KeyDown](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.KeyDown) event for text controls such as TextBox, you can cancel character input in the KeyDown event handler.</span></span>

#### <a name="the-previewkeydown-and-previewkeyup-events"></a><span data-ttu-id="471df-304">Die PreviewKeyDown- und PreviewKeyUp-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="471df-304">The PreviewKeyDown and PreviewKeyUp events</span></span>

<span data-ttu-id="471df-305">Die Vorschaueingabeereignisse werden vor allen anderen Ereignissen ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="471df-305">The preview input events are fired before any other events.</span></span> <span data-ttu-id="471df-306">Wenn Sie diese Ereignisse nicht behandeln, wird die Zugriffstaste für das Element, das den Fokus hat ausgelöst, gefolgt vom KeyDown-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="471df-306">If you don't handle these events, the accelerator for the element that has the focus is fired, followed by the KeyDown event.</span></span> <span data-ttu-id="471df-307">Beide Ereignisse durchlaufen ein Bubbling, bis der Vorgang durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="471df-307">Both events bubble until handled.</span></span>


![<span data-ttu-id="471df-308">Tastenereignissequenz](images/accelerators/accelerators_keyevents.png)
***Tastenereignissequenz***</span><span class="sxs-lookup"><span data-stu-id="471df-308">Key event sequence](images/accelerators/accelerators_keyevents.png)
***Key event sequence***</span></span>

<span data-ttu-id="471df-309">Reihenfolge der Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="471df-309">Order of events:</span></span>

<span data-ttu-id="471df-310">KeyDown-Vorschauereignisse...</span><span class="sxs-lookup"><span data-stu-id="471df-310">Preview KeyDown events …</span></span>
<span data-ttu-id="471df-311">App-Zugriffstaste OnKeyDown-Methode KeyDown-Ereignis App-Zugriffstaste auf die übergeordnete OnKeyDown-Methode für das übergeordnete KeyDown-Ereignis für das übergeordnete Ereignis (Bubbling bis zum Stammverzeichnis)...</span><span class="sxs-lookup"><span data-stu-id="471df-311">App accelerator OnKeyDown method KeyDown event App accelerators on the parent OnKeyDown method on the parent KeyDown event on the parent (Bubbles to the root) …</span></span>
<span data-ttu-id="471df-312">CharacterReceived-Ereignis PreviewKeyUp-Ereignis KeyUpEvents</span><span class="sxs-lookup"><span data-stu-id="471df-312">CharacterReceived event PreviewKeyUp events KeyUpEvents</span></span>

<span data-ttu-id="471df-313">Wenn das Zugriffstasten-Ereignis behandelt wird, wird das KeyDown-Ereignis ebenfalls als behandelt markiert.</span><span class="sxs-lookup"><span data-stu-id="471df-313">When the accelerator event is handled, the KeyDown event is also marked as handled.</span></span> <span data-ttu-id="471df-314">Das KeyUp-Ereignis wird nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="471df-314">The KeyUp event remains unhandled.</span></span>

### <a name="resolving-accelerators"></a><span data-ttu-id="471df-315">Beseitigen von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-315">Resolving accelerators</span></span>

<span data-ttu-id="471df-316">Das Zugriffstasten-Ereignis durchläuft ein Bubblingereignis vom Element mit Fokus bis hin zum Stammverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="471df-316">A keyboard accelerator event bubbles from the element that has focus up to the root.</span></span> <span data-ttu-id="471df-317">Wenn das Ereignis nicht behandelt wird, sucht das XAML-Framework unbegrenzte App-Zugriffstasten außerhalb des Bereichs der App außerhalb der Bubbling-Pfads.</span><span class="sxs-lookup"><span data-stu-id="471df-317">If the event isn't handled, the XAML framework looks for other unscoped app accelerators outside of the bubbling path.</span></span>

<span data-ttu-id="471df-318">Wenn zwei Zugriffstasten mit der gleichen Tastenkombination definiert sind, wird die erste Zugriffstaste der visuellen Struktur aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="471df-318">When two keyboard accelerators are defined with the same key combination, the first keyboard accelerator found on the visual tree is invoked.</span></span>

<span data-ttu-id="471df-319">Bereichsbezogene Zugriffstasten werden nur aufgerufen, wenn sich der Fokus innerhalb eines bestimmten Bereichs befindet.</span><span class="sxs-lookup"><span data-stu-id="471df-319">Scoped keyboard accelerators are invoked only when focus is inside a specific scope.</span></span> <span data-ttu-id="471df-320">In einem Raster, das zahlreiche Steuerelemente enthält, kann z.B. eine Zugriffstaste für ein Steuerelement nur dann aufgerufen werden, wenn sich der Fokus innerhalb des Rasters („Bereichsbesitzer“) befindet.</span><span class="sxs-lookup"><span data-stu-id="471df-320">For example, in a Grid that contains dozens of controls, a keyboard accelerator can be invoked for a control only when focus is within the Grid (the scope owner).</span></span>

### <a name="scoping-accelerators-programmatically"></a><span data-ttu-id="471df-321">Eingrenzen programmgesteuerter Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-321">Scoping accelerators programmatically</span></span>

<span data-ttu-id="471df-322">Die [UIElement.TryInvokeKeyboardAccelerator](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.tryinvokekeyboardaccelerator)-Methode ruft alle übereinstimmenden Zugriffstasten in die Unterstruktur des Elements auf.</span><span class="sxs-lookup"><span data-stu-id="471df-322">The [UIElement.TryInvokeKeyboardAccelerator](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.tryinvokekeyboardaccelerator) method invokes any matching accelerators in the subtree of the element.</span></span>

<span data-ttu-id="471df-323">Die [UIElement.OnProcessKeyboardAccelerators](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.onprocesskeyboardaccelerators) -Methode wird vor der Zugriffstaste ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="471df-323">The [UIElement.OnProcessKeyboardAccelerators](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.onprocesskeyboardaccelerators) method is executed before the keyboard accelerator.</span></span> <span data-ttu-id="471df-324">Diese Methode übergibt ein [ProcessKeyboardAcceleratorArgs](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.processkeyboardacceleratoreventargs)-Objekt, das die Taste, den Modifizierer und einen booleschen Wert enthält, der angibt, ob die Zugriffstaste behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="471df-324">This method passes a [ProcessKeyboardAcceleratorArgs](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.processkeyboardacceleratoreventargs) object that contains the key, the modifier, and a Boolean indicating whether the keyboard accelerator is handled.</span></span> <span data-ttu-id="471df-325">Wenn dieser als behandelt markiert ist, durchläuft die Zugriffstaste ein Bubbling (wobei der externe Tastenkürzel nie aufgerufen wird).</span><span class="sxs-lookup"><span data-stu-id="471df-325">If marked as handled, the keyboard accelerator bubbles (so the outside keyboard accelerator is never invoked).</span></span>

> [!NOTE]
> <span data-ttu-id="471df-326">OnProcessKeyboardAccelerators werden immer ausgelöst, ob behandelt oder nicht (ähnlich wie das OnKeyDown-Ereignis).</span><span class="sxs-lookup"><span data-stu-id="471df-326">OnProcessKeyboardAccelerators always fires, whether handled or not (similar to the OnKeyDown event).</span></span> <span data-ttu-id="471df-327">Sie müssen überprüfen, ob das Ereignis als behandelt markiert wurde.</span><span class="sxs-lookup"><span data-stu-id="471df-327">You must check whether the event was marked as handled.</span></span>

<span data-ttu-id="471df-328">In diesem Beispiel verwenden wir OnProcessKeyboardAccelerators und TryInvokeKeyboardAccelerator, um den Bereich der Zugriffstasten auf das Seitenobjekt auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="471df-328">In this example, we use OnProcessKeyboardAccelerators and TryInvokeKeyboardAccelerator to scope keyboard accelerators to the Page object:</span></span>

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

### <a name="localize-the-accelerators"></a><span data-ttu-id="471df-329">Lokalisieren der Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-329">Localize the accelerators</span></span>

<span data-ttu-id="471df-330">Es wird empfohlen, alle Zugriffstasten zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="471df-330">We recommend localizing all keyboard accelerators.</span></span> <span data-ttu-id="471df-331">Sie können dies anhand der standardmäßigen UWP-Ressourcendatei (.resw) und des x: Uid-Attributs in Ihrer XAML-Deklarationen durchführen.</span><span class="sxs-lookup"><span data-stu-id="471df-331">You can do this with the standard UWP resources (.resw) file and the x:Uid attribute in your XAML declarations.</span></span> <span data-ttu-id="471df-332">In diesem Beispiel lädt Windows-Runtime automatisch die Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="471df-332">In this example, the Windows Runtime automatically loads the resources.</span></span>

![<span data-ttu-id="471df-333">Lokalisierung der Zugriffstasten mit der UWP-Ressourcendatei](images/accelerators/accelerators_localization.png)
***Lokalisierung der Zugriffstasten mit der UWP-Ressourcendatei***</span><span class="sxs-lookup"><span data-stu-id="471df-333">Keyboard accelerator localization with UWP resources file](images/accelerators/accelerators_localization.png)
***Keyboard accelerator localization with UWP resources file***</span></span>

``` xaml
<Button x:Uid="myButton" Click="OnSave">
  <Button.KeyboardAccelerators>
    <KeyboardAccelerator x:Uid="myKeyAccelerator" Modifiers="Control"/>
  </Button.KeyboardAccelerators>
</Button>
```

### <a name="setup-an-accelerator-programmatically"></a><span data-ttu-id="471df-334">Einrichten einer programmgesteuerten Zugriffstaste</span><span class="sxs-lookup"><span data-stu-id="471df-334">Setup an accelerator programmatically</span></span>

<span data-ttu-id="471df-335">Hier ist ein Beispiel für das Definieren einer programmgesteuerten Zugriffstaste:</span><span class="sxs-lookup"><span data-stu-id="471df-335">Here is an example of programmatically defining an accelerator:</span></span>

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
> <span data-ttu-id="471df-336">KeyboardAccelerator kann nicht freigegeben werden, der gleiche KeyboardAccelerator kann nicht mehreren Elementen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="471df-336">KeyboardAccelerator is not shareable, the same KeyboardAccelerator can't be added to multiple elements.</span></span>

### <a name="override-keyboard-accelerator-behavior"></a><span data-ttu-id="471df-337">Außerkraftsetzen des Verhaltens von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-337">Override keyboard accelerator behavior</span></span>

<span data-ttu-id="471df-338">Sie können das Ereignis [KeyboardAccelerator.Invoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Invoked) bearbeiten, um das KeyboardAccelerator-Standardverhalten außer Kraft zu setzen.</span><span class="sxs-lookup"><span data-stu-id="471df-338">You can handle the [KeyboardAccelerator.Invoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.keyboardaccelerator.Invoked) event to override the default KeyboardAccelerator behavior.</span></span>

<span data-ttu-id="471df-339">In diesem Beispiel wird veranschaulicht, wie Sie den Befehl „Alle auswählen“ (Zugriffstaste STRG+A) in einem benutzerdefinierten ListView-Steuerelement außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="471df-339">This example shows how to override the "Select all" command (Ctrl+A keyboard accelerator) in a custom ListView control.</span></span> <span data-ttu-id="471df-340">Wir haben außerdem die Handled-Eigenschaft auf „true“ festgelegt, um das weitere Bubbling des Ereignisses zu beenden.</span><span class="sxs-lookup"><span data-stu-id="471df-340">We also set the Handled property to true to stop the event bubbling further.</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="471df-341">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="471df-341">Related articles</span></span>

* [<span data-ttu-id="471df-342">Tastaturinteraktionen</span><span class="sxs-lookup"><span data-stu-id="471df-342">Keyboard interactions</span></span>](keyboard-interactions.md)
* [<span data-ttu-id="471df-343">Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="471df-343">Access keys</span></span>](access-keys.md)

**<span data-ttu-id="471df-344">Beispiele</span><span class="sxs-lookup"><span data-stu-id="471df-344">Samples</span></span>**
* [<span data-ttu-id="471df-345">XAML-Steuerelementekatalog (auch bekannt als XamlUiBasics)</span><span class="sxs-lookup"><span data-stu-id="471df-345">XAML Controls Gallery (aka XamlUiBasics)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/c2aeaa588d9b134466bbd2cc387c8ff4018f151e/Samples/XamlUIBasics)


 

