---
author: kbridge
Description: "Erfahren Sie, wie Sie Benutzerfreundlichkeit und Barrierefreiheit Ihrer UWP-App verbessern, indem Sie Benutzern eine intuitive Möglichkeit bereitstellen, schnell in der sichtbaren UI einer App über eine Tastatur statt per Eingabe mit dem Finger oder der Maus zu navigieren und zu interagieren."
title: "Zugriffstasten – Designrichtlinien"
label: Access keys design guidelines
keywords: Tastatur, Zugriffstaste, Zugriffstasteninfo, Barrierefreiheit, Navigation, Fokus, Text, Eingabe, Benutzerinteraktion
template: detail.hbs
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
pm-contact: miguelrb
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.openlocfilehash: ae8bd60311bc7ead44ee3c9a137a233888be55f3
ms.sourcegitcommit: 0fa9ae00117e8e6b04ed38956e605bb74c1261c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2017
---
# <a name="access-keys"></a><span data-ttu-id="803f8-104">Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="803f8-104">Access keys</span></span>

<span data-ttu-id="803f8-105">Zugriffstasten können die Benutzerfreundlichkeit und Barrierefreiheit Ihrer Windows-App verbessern, indem sie Benutzern eine intuitive Möglichkeit bereitstellen, schnell in der sichtbaren UI einer App über eine Tastatur statt per Eingabe mit dem Finger oder der Maus zu navigieren und zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="803f8-105">Access keys can improve both the usability and the accessibility of your Windows app by providing an intuitive way for users to quickly navigate and interact with an app's visible UI through a keyboard instead of a pointer device (such as touch or mouse).</span></span>

> [!NOTE]
> <span data-ttu-id="803f8-106">Eine Tastatur ist unentbehrlich für Benutzer mit bestimmten körperlichen Einschränkungen (siehe [Barrierefreiheit der Tastaturnavigation](https://docs.microsoft.com/windows/uwp/accessibility/keyboard-accessibility)) und auch ein wichtiges Tool für Benutzer, die effizienter mit einer App interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="803f8-106">A keyboard is indispensable for users with certain disabilities (see [Keyboard accessibility](https://docs.microsoft.com/windows/uwp/accessibility/keyboard-accessibility)), and is also an important tool for users who prefer it as a more efficient way to interact with an app.</span></span>

<span data-ttu-id="803f8-107">Die Universelle Windows-Plattform (UWP) bietet integrierte Unterstützung für Plattformsteuerelemente für tastaturbasierte Zugriffstasten und zugehöriges UI-Feedback über optische Hinweise namens Zugriffstasteninfos.</span><span class="sxs-lookup"><span data-stu-id="803f8-107">The Universal Windows Platform (UWP) provides built-in support across platform controls for both keyboard-based access keys and associated UI feedback through visual cues called key tips.</span></span>

## <a name="overview"></a><span data-ttu-id="803f8-108">Übersicht</span><span class="sxs-lookup"><span data-stu-id="803f8-108">Overview</span></span>

<span data-ttu-id="803f8-109">Eine Zugriffstaste ist eine Kombination aus der Alt-Taste und einer oder mehreren alphanumerischen Tasten (manchmal als *mnemonisches Zeichen* bezeichnet). Die Tasten werden in der Regel nacheinander und nicht gleichzeitig gedrückt.</span><span class="sxs-lookup"><span data-stu-id="803f8-109">An access key is a combination of the Alt key and one or more alphanumeric keys—sometimes called a *mnemonic*—typically pressed sequentially, rather than simultaneously.</span></span>

<span data-ttu-id="803f8-110">Zugriffstasteninfos sind Signale, die neben den Steuerelementen angezeigt werden, die Zugriffstasten unterstützen, wenn der Benutzer die Alt-Taste drückt.</span><span class="sxs-lookup"><span data-stu-id="803f8-110">Key tips are badges displayed next to controls that support access keys when the user presses the Alt key.</span></span> <span data-ttu-id="803f8-111">Jede Zugriffstasteninfo enthält die alphanumerischen Tasten, die das zugeordnete Steuerelement aktivieren.</span><span class="sxs-lookup"><span data-stu-id="803f8-111">Each key tip contains the alphanumeric keys that activate the associated control.</span></span>

> [!NOTE]
> <span data-ttu-id="803f8-112">Tastenkombinationen werden für Zugriffstasten mit einem einzelnen alphanumerischen Zeichen automatisch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="803f8-112">Keyboard shortcuts are automatically supported for access keys with a single alphanumeric character.</span></span> <span data-ttu-id="803f8-113">Durch gleichzeitiges Drücken von Alt+F in Word wird z.B. das Menü „Datei“ ohne Zugriffstasteninfos angezeigt.</span><span class="sxs-lookup"><span data-stu-id="803f8-113">For example, simultaneously pressing Alt+F in Word opens the File menu without displaying key tips.</span></span>

<span data-ttu-id="803f8-114">Durch Drücken der Alt-Taste wird die Zugrifftastenfunktionalität initialisiert. Zudem werden alle derzeit verfügbaren Tastenkombinationen in Zugriffstasteninfos angezeigt.</span><span class="sxs-lookup"><span data-stu-id="803f8-114">Pressing the Alt key initializes access key functionality and displays all currently available key combinations in key tips.</span></span> <span data-ttu-id="803f8-115">Nachfolgende Tastaturanschläge werden durch das Zugriffstasten-Framework verarbeitet, das ungültige Tasten ablehnt, bis eine gültige Zugriffstaste oder die Eingabetaste, Esc-Taste, Tabulatortaste oder Pfeiltaste gedrückt wird, um Zugriffstasten zu deaktivieren und die Behandlung von Tastaturanschlägen an die App zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="803f8-115">Subsequent keystrokes are handled by the access key framework, which rejects invalid keys until either a valid access key is pressed, or the Enter, Esc, Tab, or Arrow keys are pressed to deactivate access keys and return keystroke handling to the app.</span></span>

<span data-ttu-id="803f8-116">Microsoft Office-Apps bieten umfassende Unterstützung für Zugriffstasten.</span><span class="sxs-lookup"><span data-stu-id="803f8-116">Microsoft Office apps provide extensive support for access keys.</span></span> <span data-ttu-id="803f8-117">Die folgende Abbildungzeigt die Registerkarte „Start“ von Word mit aktivierten Zugriffstasten. (Beachten Sie die Unterstützung für Zahlen und mehrere Tastaturanschläge.)</span><span class="sxs-lookup"><span data-stu-id="803f8-117">The following image shows the Home tab of Word with access keys activated (note the support for both numbers and multiple keystrokes).</span></span>

![Zugriffstasteninfo-Signale für Zugriffstasten in Microsoft Word](images/accesskeys/keytip-badges-word.png)

_<span data-ttu-id="803f8-119">Zugriffstasteninfo-Signale für Zugriffstasten in Microsoft Word</span><span class="sxs-lookup"><span data-stu-id="803f8-119">KeyTip badges for access keys in Microsoft Word</span></span>_

<span data-ttu-id="803f8-120">Um eine Zugriffstaste zu einem Steuerelement hinzuzufügen, verwenden Sie die **AccessKey-Eigenschaft**.</span><span class="sxs-lookup"><span data-stu-id="803f8-120">To add an access key to a control, use the **AccessKey property**.</span></span> <span data-ttu-id="803f8-121">Der Wert dieser Eigenschaft gibt die Zugriffstastensequenz, die Verknüpfung (bei einem einzelnen alphanumerischen Zeichen) und die Zugriffstasteninfo an.</span><span class="sxs-lookup"><span data-stu-id="803f8-121">The value of this property specifies the access key sequence, the shortcut (if a single alphanumeric), and the key tip.</span></span>

``` xaml
<Button Content="Accept" AccessKey="A" Click="AcceptButtonClick" />
```

## <a name="when-to-use-access-keys"></a><span data-ttu-id="803f8-122">Verwenden von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="803f8-122">When to use access keys</span></span>

<span data-ttu-id="803f8-123">Es wird empfohlen, dass Sie Zugriffstasten überall in Ihrer UI angegeben, wo dies sinnvoll ist, und Zugriffstasten für alle benutzerdefinierten Steuerelemente unterstützen.</span><span class="sxs-lookup"><span data-stu-id="803f8-123">We recommend that you specify access keys wherever appropriate in your UI, and support access keys in all custom controls.</span></span>

1.  <span data-ttu-id="803f8-124">**Zugriffstasten erleichtern den Zugriff auf Ihre App** für Benutzer mit motorischen Einschränkungen, einschließlich der Benutzer, die jeweils nur eine Taste drücken können oder Probleme bei der Verwendung einer Maus haben.</span><span class="sxs-lookup"><span data-stu-id="803f8-124">**Access keys make your app more accessible** for users with motor disabilities, including those users who can press only one key at a time or have difficulty using a mouse.</span></span>

    <span data-ttu-id="803f8-125">Eine gut durchdachte Tastatur-UI ist ein wichtiger Aspekt für die Barrierefreiheit von Software.</span><span class="sxs-lookup"><span data-stu-id="803f8-125">A well-designed keyboard UI is an important aspect of software accessibility.</span></span> <span data-ttu-id="803f8-126">Sie ermöglicht es Benutzern mit einer Sehbeeinträchtigung oder mit bestimmten motorischen Einschränkungen, in einer App zu navigieren und mit deren Features zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="803f8-126">It enables users with vision impairments or who have certain motor disabilities to navigate an app and interact with its features.</span></span> <span data-ttu-id="803f8-127">Diese Benutzer können u.U. keine Maus bedienen und sind auf verschiedene Hilfstechnologien wie etwa Tastaturerweiterungstools, Bildschirmtastaturen, Bildschirmlupen, Bildschirmleseprogramme oder die Möglichkeit der Spracheingabe angewiesen.</span><span class="sxs-lookup"><span data-stu-id="803f8-127">Such users might not be able to operate a mouse and instead rely on various assistive technologies such as keyboard enhancement tools, on-screen keyboards, screen enlargers, screen readers, and voice input utilities.</span></span> <span data-ttu-id="803f8-128">Für diese Benutzer ist eine vollständige Befehlsabdeckung entscheidend.</span><span class="sxs-lookup"><span data-stu-id="803f8-128">For these users, comprehensive command coverage is crucial.</span></span>

2.  <span data-ttu-id="803f8-129">**Zugriffstasten machen Ihre App benutzerfreundlicher** für erfahrene Benutzer, die über die Tastatur interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="803f8-129">**Access keys make your app more usable** for power users who prefer to interact through the keyboard.</span></span>

    <span data-ttu-id="803f8-130">Erfahrene Benutzer haben oftmals eine starke Vorliebe für die Verwendung der Tastatur, da tastaturbasierte Befehle viel schneller eingegeben werden können. Zudem ist es dafür nicht erforderlich, die Hände von der Tastatur wegzubewegen.</span><span class="sxs-lookup"><span data-stu-id="803f8-130">Experienced users often have a strong preference for using the keyboard, because keyboard-based commands can be entered more quickly and don't require them to remove their hands from the keyboard.</span></span> <span data-ttu-id="803f8-131">Für diese Benutzer sind Effizienz und Konsistenz entscheidend. Die Vollständigkeit hingegen ist nur für die am häufigsten verwendeten Befehle wichtig.</span><span class="sxs-lookup"><span data-stu-id="803f8-131">For these users, efficiency and consistency are crucial; comprehensiveness is important only for the most frequently used commands.</span></span>

## <a name="set-access-key-scope"></a><span data-ttu-id="803f8-132">Festlegen des Zugriffstastenbereichs</span><span class="sxs-lookup"><span data-stu-id="803f8-132">Set access key scope</span></span>

<span data-ttu-id="803f8-133">Wenn viele Elemente auf dem Bildschirm vorhanden sind, die Zugriffstasten unterstützen, empfehlen wir die Bereichsdefinition für Zugriffstasten, um den Benutzer **kognitiv zu entlasten**.</span><span class="sxs-lookup"><span data-stu-id="803f8-133">When there are many elements on the screen that support access keys, we recommend scoping the access keys to reduce **cognitive load**.</span></span> <span data-ttu-id="803f8-134">Dies reduziert die Anzahl der Zugriffstasten auf dem Bildschirm, wodurch sie leichter zu finden sind, und verbessert die Effizienz und Produktivität.</span><span class="sxs-lookup"><span data-stu-id="803f8-134">This minimizes the number of access keys on the screen, which makes them easier to locate, and improves efficiency and productivity.</span></span>

<span data-ttu-id="803f8-135">Microsoft Word bietet beispielsweise zwei Zugriffstastenbereiche: einen primären Bereich für die Menüband-Registerkarten und einen sekundären Bereich für Befehle auf der ausgewählten Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="803f8-135">For example, Microsoft Word provides two access key scopes: a primary scope for the Ribbon tabs and a secondary scope for commands on the selected tab.</span></span>

<span data-ttu-id="803f8-136">Die folgenden Abbildungen zeigen die zwei Zugriffstastenbereiche in Word.</span><span class="sxs-lookup"><span data-stu-id="803f8-136">The following images demonstrate the two access key scopes in Word.</span></span> <span data-ttu-id="803f8-137">Das erste Beispiel zeigt die primären Zugriffstasten, mit denen ein Benutzer eine Registerkarte und andere Befehle auf oberster Ebene auswählen kann. Das zweite zeigt die sekundären Zugriffstasten für die Registerkarte „Start“.</span><span class="sxs-lookup"><span data-stu-id="803f8-137">The first shows the primary access keys that let a user select a tab and other top level commands, and the second shows the secondary access keys for the Home tab.</span></span>

![Primäre Zugriffstasten in Microsoft Word](images/accesskeys/primary-access-keys-word.png)

_<span data-ttu-id="803f8-139">Primäre Zugriffstasten in Microsoft Word</span><span class="sxs-lookup"><span data-stu-id="803f8-139">Primary access keys in Microsoft Word</span></span>_

![Sekundäre Zugriffstasten in Microsoft Word](images/accesskeys/secondary-access-keys-word.png)

<span data-ttu-id="803f8-141">Sekundäre Zugriffstasten in Microsoft Word</span><span class="sxs-lookup"><span data-stu-id="803f8-141">Secondary access keys in Microsoft Word</span></span>

<span data-ttu-id="803f8-142">Zugriffstasten können für Elemente in verschiedenen Bereichen dupliziert werden.</span><span class="sxs-lookup"><span data-stu-id="803f8-142">Access keys can be duplicated for elements in different scopes.</span></span> <span data-ttu-id="803f8-143">Im obigen Beispiel ist „2“ die Zugriffstaste für „Rückgängig“ im primären Bereich und „Kursiv“ im sekundären Bereich.</span><span class="sxs-lookup"><span data-stu-id="803f8-143">In the preceding example, “2” is the access key for Undo in the primary scope, and also “Italics” in the secondary scope.</span></span>

<span data-ttu-id="803f8-144">Einige Steuerelemente, z.B. die Befehlsleiste, unterstützen integrierte Zugriffstastenbereiche noch nicht. Daher müssen Sie die Implementierung selbst vornehmen.</span><span class="sxs-lookup"><span data-stu-id="803f8-144">Some controls, such as the CommandBar, don’t support built-in access key scopes yet and, as a consequence, it is needed to implement it by yourself.</span></span> <span data-ttu-id="803f8-145">Im folgenden Beispiel wird veranschaulicht, wie Sie die sekundären Befehle der Befehlsleiste mit Zugriffstasten unterstützen, die verfügbar sind, sobald ein übergeordneter Befehl aufgerufen wird (vergleichbar mit dem Menüband in Word).</span><span class="sxs-lookup"><span data-stu-id="803f8-145">The following example demonstrates how to support the CommandBar’s SecondaryCommands with access keys available once a parent command is invoked (similar to the Ribbon in Word).</span></span>

``` C#
public class CommandBarHack : CommandBar
{
    CommandBarOverflowPresenter secondaryItemsControl;
    Popup overflowPopup;

    public CommandBarHack()
    {
        this.ExitDisplayModeOnAccessKeyInvoked = false;
        AccessKeyInvoked += OnAccessKeyInvoked;
    }

    protected override void OnApplyTemplate()
    {
        base.OnApplyTemplate();

        Button moreButton = GetTemplateChild("MoreButton") as Button;
        moreButton.SetValue(Control.IsTemplateKeyTipTargetProperty, true);
        moreButton.IsAccessKeyScope = true;

        // SecondaryItemsControl changes
        secondaryItemsControl = GetTemplateChild("SecondaryItemsControl") as CommandBarOverflowPresenter;
        secondaryItemsControl.AccessKeyScopeOwner = moreButton;

        overflowPopup = GetTemplateChild("OverflowPopup") as Popup;

    }
    private void OnAccessKeyInvoked(UIElement sender, AccessKeyInvokedEventArgs args)
    {

        if (overflowPopup != null)
        {
            overflowPopup.Opened += SecondaryMenuOpened;
        }
    }

    private void SecondaryMenuOpened(object sender, object e)
    {
        //This is not neccesay given we are automatically pushing the scope.
        var item = secondaryItemsControl.Items.First();
        if (item != null && item is Control)
        {
            (item as Control).Focus(FocusState.Keyboard);
        }
        overflowPopup.Opened -= SecondaryMenuOpened;
    }
}
```


``` xaml
<local:CommandBarHack x:Name="MainCommandBar" AccessKey="M" >
    <AppBarButton AccessKey="G" Icon="Globe" Label="Go"/>
    <AppBarButton AccessKey="S" Icon="Stop" Label="Stop"/>
    <AppBarSeparator/>
    <AppBarButton AccessKey="R" Icon="Refresh" Label="Refresh" IsAccessKeyScope="True">
        <AppBarButton.Flyout>
            <MenuFlyout>
                <MenuFlyoutItem AccessKey="A" Icon="Globe" Text="Refresh A" />
                <MenuFlyoutItem AccessKey="B" Icon="Globe" Text="Refresh B" />
                <MenuFlyoutItem AccessKey="C" Icon="Globe" Text="Refresh C" />
                <MenuFlyoutItem AccessKey="D" Icon="Globe" Text="Refresh D" />
            </MenuFlyout>
        </AppBarButton.Flyout>
    </AppBarButton>
    <AppBarButton AccessKey="B" Icon="Back" Label="Back"/>
    <AppBarButton AccessKey="F" Icon="Forward" Label="Forward"/>
    <AppBarSeparator/>
    <AppBarToggleButton AccessKey="V" Icon="Favorite" Label="Favorite"/>
    <CommandBar.SecondaryCommands>
        <AppBarToggleButton Icon="Like" AccessKey="L" Label="Like"/>
        <AppBarButton Icon="Setting" AccessKey="T" Label="Settings" />
    </CommandBar.SecondaryCommands>
</local:CommandBarHack>
```

![Primäre Zugriffstasten für Befehlsleiste](images/accesskeys/primary-access-keys-commandbar.png)

_<span data-ttu-id="803f8-147">Primärer Bereich der Befehlsleiste und unterstützte Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="803f8-147">CommandBar primary scope and supported access keys</span></span>_

![Sekundäre Zugriffstasten für Befehlsleiste](images/accesskeys/secondary-access-keys-commandbar.png)

_<span data-ttu-id="803f8-149">Sekundärer Bereich der Befehlsleiste und unterstützte Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="803f8-149">CommandBar secondary scope and supported access keys</span></span>_

## <a name="avoid-access-key-collisions"></a><span data-ttu-id="803f8-150">Vermeiden von Zugriffstastenkonflikten</span><span class="sxs-lookup"><span data-stu-id="803f8-150">Avoid access key collisions</span></span>

<span data-ttu-id="803f8-151">Zugriffstastenkonflikte treten auf, wenn zwei oder mehr Elemente im selben Bereich duplizierte Zugriffstasten aufweisen oder mit denselben alphanumerischen Zeichen beginnen.</span><span class="sxs-lookup"><span data-stu-id="803f8-151">Access key collisions occur when two or more elements in the same scope have duplicate access keys, or start with the same alphanumeric characters.</span></span>

<span data-ttu-id="803f8-152">Das System löst duplizierte Zugriffstasten auf, indem die Zugriffstaste des ersten zur visuellen Struktur hinzugefügten Elements verarbeitet wird und alle anderen ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="803f8-152">The system resolves duplicate access keys by processing the access key of the first element added to the visual tree, ignoring all others.</span></span>

<span data-ttu-id="803f8-153">Wenn mehrere Zugriffstasten mit demselben Zeichen (z.B. „A“, „A1“ und „AB“) beginnen, verarbeitet das System die Zugriffstaste mit einem einzelnen Zeichen und ignoriert alle anderen.</span><span class="sxs-lookup"><span data-stu-id="803f8-153">When multiple access keys start with the same character (for example, “A”, “A1”, and “AB”), the system processes the single character access key and ignores all others.</span></span>

<span data-ttu-id="803f8-154">Vermeiden Sie Konflikte durch die Verwendung eindeutiger Zugriffstasten oder die Bereichsdefinition für Befehle.</span><span class="sxs-lookup"><span data-stu-id="803f8-154">Avoid collisions by using unique access keys or by scoping commands.</span></span>

## <a name="choose-access-keys"></a><span data-ttu-id="803f8-155">Wählen von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="803f8-155">Choose access keys</span></span>

<span data-ttu-id="803f8-156">Berücksichtigen Sie Folgendes, wenn Sie Zugriffstasten wählen:</span><span class="sxs-lookup"><span data-stu-id="803f8-156">Consider the following when choosing access keys:</span></span>

-   <span data-ttu-id="803f8-157">Verwenden Sie ein einzelnes Zeichen zur Minimierung von Tastaturanschlägen und unterstützen Sie standardmäßig Tastenkombinationen (Alt + Zugriffstaste).</span><span class="sxs-lookup"><span data-stu-id="803f8-157">Use a single character to minimize keystrokes and support accelerator keys by default (Alt+AccessKey)</span></span>
-   <span data-ttu-id="803f8-158">Vermeiden Sie die Verwendung von mehr als zwei Zeichen.</span><span class="sxs-lookup"><span data-stu-id="803f8-158">Avoid using more than two characters</span></span>
-   <span data-ttu-id="803f8-159">Vermeiden Sie Zugriffstastenkonflikte.</span><span class="sxs-lookup"><span data-stu-id="803f8-159">Avoid access keys collisions</span></span>
-   <span data-ttu-id="803f8-160">Vermeiden Sie Zeichen, die nur schwer von anderen Zeichen zu unterscheiden sind, z.B. den Buchstaben „I“ und die Zahl „1“ oder den Buchstaben „O“ und die Zahl „0“.</span><span class="sxs-lookup"><span data-stu-id="803f8-160">Avoid characters that are difficult to differentiate from other characters, such as the letter “I” and the number “1” or the letter “O” and the number “0”</span></span>
-   <span data-ttu-id="803f8-161">Verwenden Sie bekannte Vorgänger anderer beliebter Apps wie Word („D“ für „Datei“, „S“ für „Startseite“ usw.).</span><span class="sxs-lookup"><span data-stu-id="803f8-161">Use well-known precedents from other popular apps such as Word (“F” for “File”, “H” for “Home”, and so on)</span></span>
-   <span data-ttu-id="803f8-162">Verwenden Sie das erste Zeichen des Befehlsnamens oder ein Zeichen mit einer engen Assoziation zum Befehl, das man sich gut merken kann.</span><span class="sxs-lookup"><span data-stu-id="803f8-162">Use the first character of the command name, or a character with a close association to the command that helps with recall</span></span>
    -   <span data-ttu-id="803f8-163">Wenn der erste Buchstaben bereits zugewiesen ist, verwenden Sie einen Buchstaben, der dem ersten Buchstaben des Befehlsnamens so nah wie möglich ist („I“ für Einfügen).</span><span class="sxs-lookup"><span data-stu-id="803f8-163">If the first letter is already assigned, use a letter that is as close as possible to the first letter of the command name (“N” for Insert)</span></span>
    -   <span data-ttu-id="803f8-164">Verwenden Sie einen markanten Konsonant aus dem Befehlsnamen („X“ für Extras).</span><span class="sxs-lookup"><span data-stu-id="803f8-164">Use a distinctive consonant from the command name (“W” for View)</span></span>
    -   <span data-ttu-id="803f8-165">Verwenden Sie einen Vokal aus dem Befehlsnamen.</span><span class="sxs-lookup"><span data-stu-id="803f8-165">Use a vowel from the command name.</span></span>

## <a name="localize-access-keys"></a><span data-ttu-id="803f8-166">Lokalisieren von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="803f8-166">Localize access keys</span></span>

<span data-ttu-id="803f8-167">Wenn Ihre App in mehrere Sprachen lokalisiert wird, sollten Sie auch **die Lokalisierung der Zugriffstasten in Betracht ziehen**.</span><span class="sxs-lookup"><span data-stu-id="803f8-167">If your app is going to be localized in multiple languages, you should also **consider localizing the access keys**.</span></span> <span data-ttu-id="803f8-168">Beispielsweise „H“ für „Home“ in en-US und „I“ für „Inicio“ in es-ES.</span><span class="sxs-lookup"><span data-stu-id="803f8-168">For example, for “H” for “Home” in en-US and “I” for “Incio” in es-ES.</span></span>

<span data-ttu-id="803f8-169">Verwenden Sie die x:Uid-Erweiterung im Markup, um lokalisierte Ressourcen wie hier gezeigt anzuwenden:</span><span class="sxs-lookup"><span data-stu-id="803f8-169">Use the x:Uid extension in markup to apply localized resources as shown here:</span></span>

``` xaml
<Button Content="Home" AccessKey="H" x:Uid="HomeButton" />
```
<span data-ttu-id="803f8-170">Ressourcen für die einzelnen Sprachen werden in entsprechenden Zeichenfolgenordnern im Projekt hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="803f8-170">Resources for each language are added to corresponding String folders in the project:</span></span>

![Ressourcen-Zeichenfolgenordner für Englisch und Spanisch](images/accesskeys/resource-string-folders.png)

_<span data-ttu-id="803f8-172">Ressourcen-Zeichenfolgenordner für Englisch und Spanisch</span><span class="sxs-lookup"><span data-stu-id="803f8-172">English and Spanish resource string folders</span></span>_

<span data-ttu-id="803f8-173">Lokalisierte Zugriffstasten werden in der Datei projects resources.resw angegeben:</span><span class="sxs-lookup"><span data-stu-id="803f8-173">Localized access keys are specified in your projects resources.resw file:</span></span>

![Geben Sie die AccessKey-Eigenschaft an, die in der Datei resources.resw angegeben ist.](images/accesskeys/resource-resw-file.png)

_<span data-ttu-id="803f8-175">Geben Sie die AccessKey-Eigenschaft an, die in der Datei resources.resw angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="803f8-175">Specify the AccessKey property specified in the resources.resw file</span></span>_

<span data-ttu-id="803f8-176">Weitere Informationen finden Sie unter [Übersetzen von UI-Ressourcen ](https://msdn.microsoft.com/library/windows/apps/xaml/Hh965329(v=win.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="803f8-176">For more info, see [Translating UI resources ](https://msdn.microsoft.com/library/windows/apps/xaml/Hh965329(v=win.10).aspx)</span></span>

## <a name="position-key-tips"></a><span data-ttu-id="803f8-177">Positionieren von Zugriffstasteninfos</span><span class="sxs-lookup"><span data-stu-id="803f8-177">Position key tips</span></span>

<span data-ttu-id="803f8-178">Zugriffstasteninfos werden als Gleitkommawertsignale relativ zu ihrem entsprechenden UI-Element angezeigt. Dabei wird das Vorhandensein anderer UI-Elemente, anderer Zugriffstasteninfos und des Bildschirmrands berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="803f8-178">Key tips are displayed as floating badges relative to their corresponding UI element, taking into account the presence of other UI elements, other key tips, and the screen edge.</span></span>

<span data-ttu-id="803f8-179">In der Regel ist die Standardposition der Zugriffstasteninfo ausreichend und bietet integrierte Unterstützung für die adaptive UI.</span><span class="sxs-lookup"><span data-stu-id="803f8-179">Typically, the default key tip location is sufficient and provides built-in support for adaptive UI.</span></span>

![Beispiel für die automatische Platzierung der Zugriffstasteninfo](images/accesskeys/auto-keytip-position.png)

_<span data-ttu-id="803f8-181">Beispiel für die automatische Platzierung der Zugriffstasteninfo</span><span class="sxs-lookup"><span data-stu-id="803f8-181">Example of automatic key tip placement</span></span>_

<span data-ttu-id="803f8-182">Falls Sie jedoch mehr Kontrolle über die Positionierung der Zugriffstasteninfo benötigen, empfehlen wir Folgendes:</span><span class="sxs-lookup"><span data-stu-id="803f8-182">However, should you need more control over key tip positioning, we recommend the following:</span></span>

1.  <span data-ttu-id="803f8-183">**Offensichtliches Zuordnungsprinzip**: Der Benutzer kann das Steuerelement einfach der Zugriffstasteninfo zuordnen.</span><span class="sxs-lookup"><span data-stu-id="803f8-183">**Obvious association principle**: The user can associate the control with the key tip easily.</span></span>

    <span data-ttu-id="803f8-184">a.</span><span class="sxs-lookup"><span data-stu-id="803f8-184">a.</span></span>  <span data-ttu-id="803f8-185">Die Zugriffstasteninfo sollte sich **in der Nähe** des Elements mit der Zugriffstaste befinden (Besitzer).</span><span class="sxs-lookup"><span data-stu-id="803f8-185">The KeyTip should be **close** to the element who have the access key (the owner).</span></span>  
    <span data-ttu-id="803f8-186">b.</span><span class="sxs-lookup"><span data-stu-id="803f8-186">b.</span></span>  <span data-ttu-id="803f8-187">Die Zugriffstasteninfo sollte **aktivierte Elemente nicht verdecken**, die Zugriffstasten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="803f8-187">The KeyTip should **avoid covering enabled elements** that have access keys.</span></span>   
    <span data-ttu-id="803f8-188">c.</span><span class="sxs-lookup"><span data-stu-id="803f8-188">c.</span></span>  <span data-ttu-id="803f8-189">Wenn eine Zugriffstasteninfo nicht in der Nähe des Besitzers platziert werden kann, sollte sie mit dem Besitzer überlappen.</span><span class="sxs-lookup"><span data-stu-id="803f8-189">If a KeyTip can’t be placed close to its owner, it should overlap the owner.</span></span> 

2.  <span data-ttu-id="803f8-190">**Auffindbarkeit**: Der Benutzer kann das Steuerelement mit der Zugriffstasteninfo schnell auffinden.</span><span class="sxs-lookup"><span data-stu-id="803f8-190">**Discoverability**: The user can discover the control with the key tip quickly.</span></span>

    <span data-ttu-id="803f8-191">a.</span><span class="sxs-lookup"><span data-stu-id="803f8-191">a.</span></span>  <span data-ttu-id="803f8-192">Die Zugriffstasteninfo **überlappt** nie mit anderen Zugriffstasteninfos.</span><span class="sxs-lookup"><span data-stu-id="803f8-192">The KeyTip never **overlaps** other key tips.</span></span>  

3.  <span data-ttu-id="803f8-193">**Lesbarkeit:** Der Benutzer kann die Zugriffstasteninfos einfach überfliegen.</span><span class="sxs-lookup"><span data-stu-id="803f8-193">**Easy scanning:** The user can skim the key tips easily.</span></span>

    <span data-ttu-id="803f8-194">a.</span><span class="sxs-lookup"><span data-stu-id="803f8-194">a.</span></span>  <span data-ttu-id="803f8-195">Zugriffstasteninfos sollten aneinander und am UI-Element **ausgerichtet** sein.</span><span class="sxs-lookup"><span data-stu-id="803f8-195">KeyTips should be **aligned** with each other and with the UI Element.</span></span>
    <span data-ttu-id="803f8-196">b.</span><span class="sxs-lookup"><span data-stu-id="803f8-196">b.</span></span>  <span data-ttu-id="803f8-197">Zugriffstasteninfos sollten so umfassend wie möglich **gruppiert** sein.</span><span class="sxs-lookup"><span data-stu-id="803f8-197">KeyTips should be **grouped** as much as possible.</span></span> 

### <a name="relative-position"></a><span data-ttu-id="803f8-198">Relative Position</span><span class="sxs-lookup"><span data-stu-id="803f8-198">Relative position</span></span>

<span data-ttu-id="803f8-199">Verwenden Sie die **KeyTipPlacementMode**-Eigenschaft, um die Platzierung der Zugriffstasteninfo auf Element- oder Gruppenbasis anzupassen.</span><span class="sxs-lookup"><span data-stu-id="803f8-199">Use the **KeyTipPlacementMode** property to customize the placement of the key tip on a per element or per group basis.</span></span>

<span data-ttu-id="803f8-200">Die Platzierungsmodi sind: Top, Bottom, Right, Left, Hidden, Center und Auto.</span><span class="sxs-lookup"><span data-stu-id="803f8-200">The Placement modes are: Top, Bottom, Right, Left, Hidden, Center, and Auto.</span></span>

![Platzierungsmodi für Zugriffstasteninfo](images/accesskeys/keytip-postion-modes.png)

_<span data-ttu-id="803f8-202">Platzierungsmodi für Zugriffstasteninfo</span><span class="sxs-lookup"><span data-stu-id="803f8-202">Key tip placement modes</span></span>_

<span data-ttu-id="803f8-203">Die Mittellinie des Steuerelements wird verwendet, um die vertikale und horizontale Ausrichtung der Zugriffstasteninfo zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="803f8-203">The center line of the control is used to calculate the vertical and horizontal alignment of the KeyTip.</span></span>

<span data-ttu-id="803f8-204">Das folgende Beispiel zeigt, wie Sie die Zugriffstasteninfo-Platzierung einer Gruppe von Steuerelementen mit der KeyTipPlacementMode-Eigenschaft eines StackPanel-Containers festlegen.</span><span class="sxs-lookup"><span data-stu-id="803f8-204">They following example shows how to set the key tip placement of a group of controls using the KeyTipPlacementMode property of a StackPanel container.</span></span>

``` xaml
<StackPanel Background="{ThemeResource ApplicationPageBackgroundThemeBrush}" KeyTipPlacementMode="Top">
  <Button Content="File" AccessKey="F" />
  <Button Content="Home" AccessKey="H" />
  <Button Content="Insert" AccessKey="N" />
</StackPanel>
```

### <a name="offsets"></a><span data-ttu-id="803f8-205">Offsets</span><span class="sxs-lookup"><span data-stu-id="803f8-205">Offsets</span></span>

<span data-ttu-id="803f8-206">Verwenden Sie die Eigenschaften KeyTipHorizontalOffset und KeyTipVerticalOffset eines Elements für eine noch genauere Kontrolle der Zugriffstasteninfo-Position.</span><span class="sxs-lookup"><span data-stu-id="803f8-206">Use the KeyTipHorizontalOffset and KeyTipVerticalOffset properties of an element for even more granular control of the key tip location.</span></span>

> [!NOTE]
> <span data-ttu-id="803f8-207">Offsets können nicht festgelegt werden, wenn KeyTipPlacementMode auf Auto festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="803f8-207">Offsets cannot be set when KeyTipPlacementMode is set to Auto.</span></span>

<span data-ttu-id="803f8-208">Die KeyTipHorizontalOffset-Eigenschaft gibt an, wie weit die Zugriffstasteninfo nach links oder rechts verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="803f8-208">The KeyTipHorizontalOffset property indicates how far to move the key tip left or right.</span></span> <span data-ttu-id="803f8-209">Das Beispiel veranschaulicht, wie die Offsets der Zugriffstasteninfo für eine Schaltfläche festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="803f8-209">example shows how to set the key tip offsets for a button.</span></span>

![Platzierungsmodi für Zugriffstasteninfo](images/accesskeys/keytip-offsets.png)

_<span data-ttu-id="803f8-211">Festlegen der vertikalen und horizontalen Offsets für eine Zugriffstasteninfo</span><span class="sxs-lookup"><span data-stu-id="803f8-211">Set vertical and horizontal offsets for a key tip</span></span>_

``` xaml
<Button
  Content="File"
  AccessKey="F"
  KeyTipPlacementMode="Bottom"
  KeyTipHorizontalOffset="20"
  KeyTipVerticalOffset="-8" />
```

### <a name="screen-edge-alignment-screen-edge-alignment-listparagraph"></a><span data-ttu-id="803f8-212">Ausrichtung des Bildschirmrands {#screen-edge-alignment .ListParagraph}</span><span class="sxs-lookup"><span data-stu-id="803f8-212">Screen edge alignment {#screen-edge-alignment .ListParagraph}</span></span>

<span data-ttu-id="803f8-213">Die Position einer Zugriffstasteninfo wird automatisch am Bildschirmrand ausgerichtet, um sicherzustellen, dass die Zugriffstasteninfo vollständig sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="803f8-213">The location of a key tip is automatically adjusted based on the screen edge to ensure the key tip is fully visible.</span></span> <span data-ttu-id="803f8-214">In diesem Fall kann der Abstand zwischen dem Steuerelement und dem Zugriffstasten-Ausrichtungspunkt von den Werten für die horizontalen und vertikalen Offsets abweichen.</span><span class="sxs-lookup"><span data-stu-id="803f8-214">When this occurs, the distance between the control and key tip alignment point might differ from the values specified for the horizontal and vertical offsets .</span></span>

![Platzierungsmodi für Zugriffstasteninfo](images/accesskeys/keytips-screen-edge.png)

_<span data-ttu-id="803f8-216">Der Bildschirmrand bewirkt, dass sich die Zugriffstasteninfo automatisch selbst neu positioniert.</span><span class="sxs-lookup"><span data-stu-id="803f8-216">The screen edge causes the key tip to automatically reposition itself</span></span>_

## <a name="style-key-tips"></a><span data-ttu-id="803f8-217">Zugriffstasteninfos – Stil</span><span class="sxs-lookup"><span data-stu-id="803f8-217">Style key tips</span></span>

<span data-ttu-id="803f8-218">Wir empfehlen die Verwendung der integrierten Zugriffstasteninfo-Unterstützung für Plattformdesigns, einschließlich hoher Kontrast.</span><span class="sxs-lookup"><span data-stu-id="803f8-218">We recommend using the built-in key tip support for platform themes, including high contrast.</span></span>

<span data-ttu-id="803f8-219">Wenn Sie Ihre eigenen Stile für Zugriffstasteninfos angeben müssen, verwenden Sie Anwendungsressourcen wie KeyTipFontSize (Schriftgröße), KeyTipFontFamily (Schriftfamilie), KeyTipBackground (Hintergrund), KeyTipForeground (Vordergrund), KeyTipPadding (Abstand), KeyTipBorderBrush (Rahmenfarbe) und KeyTipBorderThemeThickness (Rahmendicke).</span><span class="sxs-lookup"><span data-stu-id="803f8-219">If you need to specify your own key tip styles, use application resources such as KeyTipFontSize (font size), KeyTipFontFamily (font family), KeyTipBackground (background), KeyTipForeground (foreground), KeyTipPadding (padding), KeyTipBorderBrush(Border color), and KeyTipBorderThemeThickness (border thickness).</span></span>

![Platzierungsmodi für Zugriffstasteninfo](images/accesskeys/keytip-customization.png)

_<span data-ttu-id="803f8-221">Zugriffstasteninfo – Anpassungsoptionen</span><span class="sxs-lookup"><span data-stu-id="803f8-221">Key tip customization options</span></span>_

<span data-ttu-id="803f8-222">In diesem Beispiel wird veranschaulicht, wie Sie diese Anwendungsressourcen ändern:</span><span class="sxs-lookup"><span data-stu-id="803f8-222">This example demonstrates how to change these application resources:</span></span>

 ```xaml  
<Application.Resources>
  <SolidColorBrush Color="DarkGray" x:Key="MyBackgroundColor" />
  <SolidColorBrush Color="White" x:Key="MyForegroundColor" />
  <SolidColorBrush Color="Black" x:Key="MyBorderColor" />
  <StaticResource x:Key="KeyTipBackground" ResourceKey="MyBackgroundColor" />
  <StaticResource x:Key="KeyTipForeground" ResourceKey="MyForegroundColor" />
  <StaticResource x:Key="KeyTipBorderBrush" ResourceKey="MyBorderColor"/>
  <FontFamily x:Key="KeyTipFontFamily">Consolas</FontFamily>
  <x:Double x:Key="KeyTipContentThemeFontSize">18</x:Double>
  <Thickness x:Key="KeyTipBorderThemeThickness">2</Thickness>
  <Thickness x:Key="KeyTipThemePadding">4,4,4,4</Thickness>
</Application.Resources>
```

## <a name="access-keys-and-narrator"></a><span data-ttu-id="803f8-223">Zugriffstasten und Sprachausgabe</span><span class="sxs-lookup"><span data-stu-id="803f8-223">Access keys and Narrator</span></span>

<span data-ttu-id="803f8-224">Das XAML-Framework stellt Automatisierungseigenschaften bereit, mit denen UI-Automatisierungsclients Informationen zu Elementen in der Benutzeroberfläche ermitteln können.</span><span class="sxs-lookup"><span data-stu-id="803f8-224">The XAML framework exposes Automation Properties that enable UI Automation clients to discover information about elements in the user interface.</span></span>

<span data-ttu-id="803f8-225">Wenn Sie die AccessKey-Eigenschaft für ein UIElement- oder TextElement-Steuerelement angeben, können Sie mithilfe der [AutomationProperties.AccessKey](https://msdn.microsoft.com/library/windows/apps/hh759763)-Eigenschaft diesen Wert abrufen.</span><span class="sxs-lookup"><span data-stu-id="803f8-225">If you specify the AccessKey property on a UIElement or TextElement control, you can use the [AutomationProperties.AccessKey](https://msdn.microsoft.com/library/windows/apps/hh759763) property to get this value.</span></span> <span data-ttu-id="803f8-226">Barrierefreiheitclients, z.B. die Sprachausgabe, lesen den Wert dieser Eigenschaft jedes Mal, wenn ein Element den Fokus erhält.</span><span class="sxs-lookup"><span data-stu-id="803f8-226">Accessibility clients, such as Narrator, read the value of this property each time an element gets focus.</span></span>
