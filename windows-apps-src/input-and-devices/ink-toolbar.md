---
author: Karl-Bridge-Microsoft
Description: "Fügen Sie einer App für die Freihandeingabe in der universellen Windows-Plattform (UWP) eine Standard-InkToolbar hinzu. Fügen Sie der InkToolbar einen anpassbaren Stift hinzu und binden Sie diesen an eine benutzerdefinierte Definition für den Stift."
title: "Hinzufügen von InkToolbar zu einer App für die universelle Windows-Plattform (UWP)"
label: Add an InkToolbar to a Universal Windows Platform (UWP) app
template: detail.hbs
keywords: Windows Ink, Windows-Freihandeingabe, DirectInk, InkPresenter, InkCanvas, InkToolbar, Universelle Windows-Platform, UWP, Benutzerinteraktion, Eingabe
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.assetid: d888f75f-c2a0-4134-81db-907b5e24fcc5
ms.openlocfilehash: a4bff46c2ab0f0f1f9a689f2744c9a77ac90630d
ms.sourcegitcommit: c519e3d34bef37f87bb44f02b295187849bb5eea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2017
---
# <a name="add-an-inktoolbar-to-a-universal-windows-platform-uwp-app"></a><span data-ttu-id="5114b-104">Hinzufügen von InkToolbar zu einer App für die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="5114b-104">Add an InkToolbar to a Universal Windows Platform (UWP) app</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">


<span data-ttu-id="5114b-105">Es gibt zwei verschiedene Steuerelemente, die die Freihandeingabe in Apps in der universellen Windows-Plattform (UWP) vereinfachen: [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx) und [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx).</span><span class="sxs-lookup"><span data-stu-id="5114b-105">There are two different controls that facilitate inking in Universal Windows Platform (UWP) apps: [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx) and [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx).</span></span>

<span data-ttu-id="5114b-106">Über das [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx)-Steuerelement werden grundlegende Windows Ink-Funktionen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="5114b-106">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx) control provides basic Windows Ink functionality.</span></span> <span data-ttu-id="5114b-107">Rendern Sie damit die Stifteingabe entweder als letzten Strich (mit den Standardeinstellungen für Farbe und Stärke) oder ausradierten Strich.</span><span class="sxs-lookup"><span data-stu-id="5114b-107">Use it to render pen input as either an ink stroke (using default settings for color and thickness) or an erase stroke.</span></span>

> <span data-ttu-id="5114b-108">Details zur Implementierung von InkCanvas finden Sie unter [Zeichen- und Eingabestiftinteraktionen in UWP-Apps](pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="5114b-108">For InkCanvas implementation details, see [Pen and stylus interactions in UWP apps](pen-and-stylus-interactions.md).</span></span>

<span data-ttu-id="5114b-109">Als vollständig transparente Überlagerung bietet InkCanvas keine integrierte Benutzeroberfläche zum Festlegen von Freihandstricheinstellungen.</span><span class="sxs-lookup"><span data-stu-id="5114b-109">As a completely transparent overlay, the InkCanvas does not provide any built-in UI for setting ink stroke properties.</span></span> <span data-ttu-id="5114b-110">Wenn Sie die Standard-Freihandfunktionen ändern, Benutzern das Festlegen von Freihandstricheinstellungen ermöglichen und andere benutzerdefinierte Freihandeingabefeatures unterstützen möchten, haben Sie zwei Optionen:</span><span class="sxs-lookup"><span data-stu-id="5114b-110">If you want to change the default inking experience, let users set ink stroke properties, and support other custom inking features, you have two options:</span></span>

- <span data-ttu-id="5114b-111">Verwenden Sie im CodeBehind das an InkCanvas gebundene zugrunde liegende [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="5114b-111">In code-behind, use the underlying [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx) object bound to the InkCanvas.</span></span>

  <span data-ttu-id="5114b-112">Die InkPresenter-APIs unterstützen die umfassende Anpassung der Freihandfunktionen.</span><span class="sxs-lookup"><span data-stu-id="5114b-112">The InkPresenter APIs support extensive customization of the inking experience.</span></span> <span data-ttu-id="5114b-113">Weitere Informationen finden Sie unter [Zeichen- und Eingabestiftinteraktionen in UWP-Apps](pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="5114b-113">For more detail, see [Pen and stylus interactions in UWP apps](pen-and-stylus-interactions.md).</span></span>

- <span data-ttu-id="5114b-114">Binden Sie [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) an InkCanvas.</span><span class="sxs-lookup"><span data-stu-id="5114b-114">Bind an [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) to the InkCanvas.</span></span> <span data-ttu-id="5114b-115">InkToolbar bietet standardmäßig eine anpassbare und erweiterbare Sammlung von Schaltflächen zum Aktivieren von Freihandfunktionen wie Strichgröße, Freihandfarbe und Form der Stiftspitze.</span><span class="sxs-lookup"><span data-stu-id="5114b-115">By default, the InkToolbar provides a customizable and extensible collection of buttons for activating ink-related features such as stroke size, ink color, and pen tip.</span></span>

  <span data-ttu-id="5114b-116">InkToolbar wird in diesem Thema erläutert.</span><span class="sxs-lookup"><span data-stu-id="5114b-116">We discuss the InkToolbar in this topic.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="5114b-117">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="5114b-117">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="5114b-118">InkCanvas-Klasse</span><span class="sxs-lookup"><span data-stu-id="5114b-118">InkCanvas class</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx)</li>
<li>[**<span data-ttu-id="5114b-119">InkToolbar-Klasse</span><span class="sxs-lookup"><span data-stu-id="5114b-119">InkToolbar class</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)</li>
<li>[**<span data-ttu-id="5114b-120">InkPresenter-Klasse</span><span class="sxs-lookup"><span data-stu-id="5114b-120">InkPresenter class</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx)</li>
<li>[**<span data-ttu-id="5114b-121">Windows.UI.Input.Inking</span><span class="sxs-lookup"><span data-stu-id="5114b-121">Windows.UI.Input.Inking</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208524)</li>
</ul>
</div>

## <a name="default-inktoolbar"></a><span data-ttu-id="5114b-122">Standard-InkToolbar</span><span class="sxs-lookup"><span data-stu-id="5114b-122">Default InkToolbar</span></span>

<span data-ttu-id="5114b-123">Das [**InkToolbar-Steuerelement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) enthält standardmäßig Schaltflächen zum Zeichnen, Löschen, Hervorheben sowie zum Anzeigen einer Schablone(Lineal oder Winkelmesser).</span><span class="sxs-lookup"><span data-stu-id="5114b-123">By default, the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) includes buttons for drawing, erasing, highlighting, and displaying a stencil (ruler or protractor).</span></span> <span data-ttu-id="5114b-124">Abhängig vom Feature werden in einem Flyout weitere Einstellungen und Befehle bereitgestellt, beispielsweise für Freihandfarbe, Strichstärke und das Löschen aller Freihandeingaben.</span><span class="sxs-lookup"><span data-stu-id="5114b-124">Depending on the feature, other settings and commands, such as ink color, stroke thickness, erase all ink, are provided in a flyout.</span></span>

![InkToolbar](.\images\ink\ink-tools-invoked-toolbar-small.png)  
*<span data-ttu-id="5114b-126">Standardmäßige Windows Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="5114b-126">Default Windows Ink toolbar</span></span>*

<span data-ttu-id="5114b-127">Um eine standardmäßige [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) zu einer App für die Freihandeingabe hinzuzufügen, platzieren Sie sie einfach auf derselben Seite wie Ihr [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), und verbinden Sie die beiden Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="5114b-127">To add a default [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) to an inking app, just place it on the same page as your [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) and associate the two controls.</span></span>

1. <span data-ttu-id="5114b-128">Deklarieren Sie in „MainPage.xaml“ ein Containerobjekt (in diesem Beispiel verwenden wir ein Grid-Steuerelement) für die Freihand-Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="5114b-128">In MainPage.xaml, declare a container object (for this example, we use a Grid control) for the inking surface.</span></span>
2. <span data-ttu-id="5114b-129">Deklarieren Sie ein InkCanvas-Objekt als untergeordnetes Element des Containers.</span><span class="sxs-lookup"><span data-stu-id="5114b-129">Declare an InkCanvas object as a child of the container.</span></span> <span data-ttu-id="5114b-130">(Die InkCanvas-Größe wird vom Container geerbt.)</span><span class="sxs-lookup"><span data-stu-id="5114b-130">(The InkCanvas size is inherited from the container.)</span></span>
3. <span data-ttu-id="5114b-131">Deklarieren Sie eine InkToolbar, und verwenden Sie das TargetInkCanvas-Attribut zum Binden an InkCanvas.</span><span class="sxs-lookup"><span data-stu-id="5114b-131">Declare an InkToolbar and use the TargetInkCanvas attribute to bind it to the InkCanvas.</span></span>
    > [!NOTE]  
    > <span data-ttu-id="5114b-132">Stellen Sie sicher, dass die InkToolbar nach InkCanvas deklariert wird.</span><span class="sxs-lookup"><span data-stu-id="5114b-132">Ensure the InkToolbar is declared after the InkCanvas.</span></span> <span data-ttu-id="5114b-133">Andernfalls verhindert die InkCanvas-Überlagerung den Zugriff auf die InkToolbar.</span><span class="sxs-lookup"><span data-stu-id="5114b-133">If not, the InkCanvas overlay renders the InkToolbar inaccessible.</span></span>

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
        <TextBlock x:Name="Header"
                   Text="Basic ink sample"
                   Style="{ThemeResource HeaderTextBlockStyle}"
                   Margin="10,0,0,0" />
    </StackPanel>
    <Grid Grid.Row="1">
        <Image Source="Assets\StoreLogo.png" />
        <InkCanvas x:Name="inkCanvas" />
        <InkToolbar x:Name="inkToolbar"
          VerticalAlignment="Top"
          TargetInkCanvas="{x:Bind inkCanvas}" />
    </Grid>
</Grid>
```

## <a name="basic-customization"></a><span data-ttu-id="5114b-134">Einfache Anpassung</span><span class="sxs-lookup"><span data-stu-id="5114b-134">Basic customization</span></span>

<span data-ttu-id="5114b-135">In diesem Abschnitt behandeln wir einige grundlegende Anpassungsszenarien der Windows Ink-Symbolleiste.</span><span class="sxs-lookup"><span data-stu-id="5114b-135">In this section, we cover some basic Windows Ink toolbar customization scenarios.</span></span>

### <a name="specify-the-selected-button"></a><span data-ttu-id="5114b-136">Angeben der ausgewählten Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="5114b-136">Specify the selected button</span></span>  
![Bei der Initialisierung ausgewählte Stiftschaltfläche](.\images\ink\ink-tools-default-toolbar.png)  
*<span data-ttu-id="5114b-138">Windows Ink-Symbolleiste mit bei der Initialisierung ausgewählter Stiftschaltfläche</span><span class="sxs-lookup"><span data-stu-id="5114b-138">Windows Ink toolbar with pencil button selected at initialization</span></span>*

<span data-ttu-id="5114b-139">Standardmäßig wird die erste (oder äußerste linke) Schaltfläche aktiviert, wenn die App gestartet und die Symbolleiste initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="5114b-139">By default, the first (or leftmost) button is selected when your app is launched and the toolbar is initialized.</span></span> <span data-ttu-id="5114b-140">In der standardmäßigen Windows Ink-Symbolleiste ist dies die Kugelschreiberschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="5114b-140">In the default Windows Ink toolbar, this is the ballpoint pen button.</span></span>

<span data-ttu-id="5114b-141">Da das Framework die Reihenfolge der integrierten Schaltflächen definiert, ist möglicherweise die erste Schaltfläche nicht der Stift oder das Tool, das Sie standardmäßig aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="5114b-141">Because the framework defines the order of the built-in buttons, the first button might not be the pen or tool you want to activate by default.</span></span>

<span data-ttu-id="5114b-142">Sie können das Standardverhalten überschreiben und die ausgewählte Schaltfläche auf der Symbolleiste angeben.</span><span class="sxs-lookup"><span data-stu-id="5114b-142">You can override this default behavior and specify the selected button on the toolbar.</span></span>

<span data-ttu-id="5114b-143">In diesem Beispiel initialisieren wir die standardmäßige Symbolleiste mit ausgewählter Stiftschaltfläche und aktiviertem Stift (anstelle des Kugelschreibers).</span><span class="sxs-lookup"><span data-stu-id="5114b-143">For this example, we initialize the default toolbar with the pencil button selected and the pencil activated (instead of the ballpoint pen).</span></span>

1. <span data-ttu-id="5114b-144">Verwenden Sie die XAML-Deklaration für InkCanvas und InkToolbar aus dem vorherigen Beispiel.</span><span class="sxs-lookup"><span data-stu-id="5114b-144">Use the XAML declaration for the InkCanvas and InkToolbar from the previous example.</span></span>
2. <span data-ttu-id="5114b-145">Richten Sie im CodeBehind einen Handler für das [Loaded](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loaded.aspx)-Ereignis des [InkToolbar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)-Objekts ein.</span><span class="sxs-lookup"><span data-stu-id="5114b-145">In code-behind, set up a handler for the [Loaded](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loaded.aspx) event of the [InkToolbar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) object.</span></span>

  ```csharp
  /// <summary>
  /// An empty page that can be used on its own or navigated to within a Frame.
  /// Here, we set up InkToolbar event listeners.
  /// </summary>
  public MainPage_CodeBehind()
  {
      this.InitializeComponent();
      // Add handlers for InkToolbar events.
      inkToolbar.Loaded += inkToolbar_Loaded;
  }
  ```

3. <span data-ttu-id="5114b-146">Im Handler für das [Loaded](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loaded.aspx)-Ereignis:</span><span class="sxs-lookup"><span data-stu-id="5114b-146">In the handler for the [Loaded](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loaded.aspx) event:</span></span>
  1. <span data-ttu-id="5114b-147">Rufen Sie einen Verweis auf die integrierte [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx) ab.</span><span class="sxs-lookup"><span data-stu-id="5114b-147">Get a reference to the built-in [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx).</span></span>

    <span data-ttu-id="5114b-148">Das Übergeben eines [InkToolbarTool.Pencil](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbartool.aspx)-Objekts in der [GetToolButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.gettoolbutton.aspx)-Methode gibt ein [InkToolbarToolButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbartoolbutton.aspx)-Objekt für [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx) zurück.</span><span class="sxs-lookup"><span data-stu-id="5114b-148">Passing an [InkToolbarTool.Pencil](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbartool.aspx) object in the [GetToolButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.gettoolbutton.aspx) method returns an [InkToolbarToolButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbartoolbutton.aspx) object for the [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx).</span></span>

  2. <span data-ttu-id="5114b-149">Legen Sie [ActiveTool](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.activetool.aspx) auf das im vorherigen Schritt zurückgegebene Objekt fest.</span><span class="sxs-lookup"><span data-stu-id="5114b-149">Set [ActiveTool](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.activetool.aspx) to the object returned in the previous step.</span></span>

```CSharp
/// <summary>
/// Handle the Loaded event of the InkToolbar.
/// By default, the active tool is set to the first tool on the toolbar.
/// Here, we set the active tool to the pencil button.
/// </summary>
/// <param name="sender"></param>
/// <param name="e"></param>
private void inkToolbar_Loaded(object sender, RoutedEventArgs e)
{
    InkToolbarToolButton pencilButton = inkToolbar.GetToolButton(InkToolbarTool.Pencil);
    inkToolbar.ActiveTool = pencilButton;
}
```

### <a name="specify-the-built-in-buttons"></a><span data-ttu-id="5114b-150">Angeben der integrierten Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="5114b-150">Specify the built-in buttons</span></span>

![Bei der Initialisierung vorhandene Schaltflächen](.\images\ink\ink-tools-specific.png)  
*<span data-ttu-id="5114b-152">Bei der Initialisierung vorhandene Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="5114b-152">Specific buttons included at initialization</span></span>*

<span data-ttu-id="5114b-153">Wie bereits erwähnt, enthält die Windows Ink-Symbolleiste eine Sammlung von standardmäßigen, integrierten Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="5114b-153">As mentioned, the Windows Ink toolbar includes a collection of default, built-in buttons.</span></span> <span data-ttu-id="5114b-154">Diese Schaltflächen werden in der folgenden Reihenfolge angezeigt (von links nach rechts):</span><span class="sxs-lookup"><span data-stu-id="5114b-154">These buttons are displayed in the following order (from left to right):</span></span>

- [<span data-ttu-id="5114b-155">InkToolbarBallpointPenButton</span><span class="sxs-lookup"><span data-stu-id="5114b-155">InkToolbarBallpointPenButton</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarballpointpenbutton.aspx)
- [<span data-ttu-id="5114b-156">InkToolbarPencilButton</span><span class="sxs-lookup"><span data-stu-id="5114b-156">InkToolbarPencilButton</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx)
- [<span data-ttu-id="5114b-157">InkToolbarHighlighterButton</span><span class="sxs-lookup"><span data-stu-id="5114b-157">InkToolbarHighlighterButton</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarhighlighterbutton.aspx)
- [<span data-ttu-id="5114b-158">InkToolbarEraserButton</span><span class="sxs-lookup"><span data-stu-id="5114b-158">InkToolbarEraserButton</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbareraserbutton.aspx)
- [<span data-ttu-id="5114b-159">InkToolbarRulerButton</span><span class="sxs-lookup"><span data-stu-id="5114b-159">InkToolbarRulerButton</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarrulerbutton.aspx)

<span data-ttu-id="5114b-160">In diesem Beispiel initialisieren wir die Symbolleiste nur mit den integrierten Schaltflächen für Kugelschreiber, Stift und Radierer.</span><span class="sxs-lookup"><span data-stu-id="5114b-160">For this example, we initialize the toolbar with only the built-in ballpoint pen, pencil, and eraser buttons.</span></span>

<span data-ttu-id="5114b-161">Verwenden Sie hierzu XAML oder CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="5114b-161">You can do this using either XAML or code-behind.</span></span>

**<span data-ttu-id="5114b-162">XAML</span><span class="sxs-lookup"><span data-stu-id="5114b-162">XAML</span></span>**

<span data-ttu-id="5114b-163">Ändern Sie die XAML-Deklaration für InkCanvas und InkToolbar aus dem ersten Beispiel.</span><span class="sxs-lookup"><span data-stu-id="5114b-163">Modify the XAML declaration for the InkCanvas and InkToolbar from the first example.</span></span>
- <span data-ttu-id="5114b-164">Fügen Sie ein [InitialControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.initialcontrols.aspx)-Attribut hinzu, und legen Sie dessen Wert auf „[None](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarinitialcontrols.aspx)“ fest.</span><span class="sxs-lookup"><span data-stu-id="5114b-164">Add an [InitialControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.initialcontrols.aspx) attribute and set its value to "[None](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarinitialcontrols.aspx)".</span></span> <span data-ttu-id="5114b-165">Damit löschen Sie die Standardsammlung der integrierten Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="5114b-165">This clears the default collection of built-in buttons.</span></span>
- <span data-ttu-id="5114b-166">Fügen Sie die für Ihre App erforderlichen spezifischen InkToolbar-Schaltflächen hinzu.</span><span class="sxs-lookup"><span data-stu-id="5114b-166">Add the specific InkToolbar buttons required by your app.</span></span> <span data-ttu-id="5114b-167">Hier fügen wir nur [InkToolbarBallpointPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarballpointpenbutton.aspx), [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx) und [InkToolbarEraserButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbareraserbutton.aspx) hinzu.</span><span class="sxs-lookup"><span data-stu-id="5114b-167">Here, we add [InkToolbarBallpointPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarballpointpenbutton.aspx), [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx), and [InkToolbarEraserButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbareraserbutton.aspx) only.</span></span>
> [!NOTE]
> <span data-ttu-id="5114b-168">Schaltflächen werden der Symbolleiste in der vom Framework definierten Reihenfolge hinzugefügt, nicht in der hier angegebenen Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="5114b-168">Buttons are added to the toolbar in the order defined by the framework, not the order specified here.</span></span>

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
        <TextBlock x:Name="Header"
                   Text="Basic ink sample"
                   Style="{ThemeResource HeaderTextBlockStyle}"
                   Margin="10,0,0,0" />
    </StackPanel>
    <Grid Grid.Row="1">
        <Image Source="Assets\StoreLogo.png" />
        <!-- Clear the default InkToolbar buttons by setting InitialControls to None. -->
        <!-- Set the active tool to the pencil button. -->
        <InkCanvas x:Name="inkCanvas" />
        <InkToolbar x:Name="inkToolbar"
                    VerticalAlignment="Top"
                    TargetInkCanvas="{x:Bind inkCanvas}"
                    InitialControls="None">
            <!--
             Add only the ballpoint pen, pencil, and eraser.
             Note that the buttons are added to the toolbar in the order
             defined by the framework, not the order we specify here.
            -->
            <InkToolbarEraserButton />
            <InkToolbarBallpointPenButton />
            <InkToolbarPencilButton/>
        </InkToolbar>
    </Grid>
</Grid>
```

**<span data-ttu-id="5114b-169">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="5114b-169">Code-behind</span></span>**
1. <span data-ttu-id="5114b-170">Verwenden Sie die XAML-Deklaration für InkCanvas und InkToolbar aus dem ersten Beispiel.</span><span class="sxs-lookup"><span data-stu-id="5114b-170">Use the XAML declaration for the InkCanvas and InkToolbar from the first example.</span></span>

  ```xaml
  <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      <Grid.RowDefinitions>
          <RowDefinition Height="Auto"/>
          <RowDefinition Height="*"/>
      </Grid.RowDefinitions>
      <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
          <TextBlock x:Name="Header"
                     Text="Basic ink sample"
                     Style="{ThemeResource HeaderTextBlockStyle}"
                     Margin="10,0,0,0" />
      </StackPanel>
      <Grid Grid.Row="1">
          <Image Source="Assets\StoreLogo.png" />
          <InkCanvas x:Name="inkCanvas" />
          <InkToolbar x:Name="inkToolbar"
          VerticalAlignment="Top"
          TargetInkCanvas="{x:Bind inkCanvas}" />
      </Grid>
  </Grid>
  ```

2. <span data-ttu-id="5114b-171">Richten Sie im CodeBehind einen Handler für das [Loading](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loading.aspx)-Ereignis des [InkToolbar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)-Objekts ein.</span><span class="sxs-lookup"><span data-stu-id="5114b-171">In code-behind, set up a handler for the [Loading](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loading.aspx) event of the [InkToolbar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) object.</span></span>

  ```csharp
  /// <summary>
  /// An empty page that can be used on its own or navigated to within a Frame.
  /// Here, we set up InkToolbar event listeners.
  /// </summary>
  public MainPage_CodeBehind()
  {
      this.InitializeComponent();
      // Add handlers for InkToolbar events.
      inkToolbar.Loading += inkToolbar_Loading;
  }
  ```

3. <span data-ttu-id="5114b-172">Legen Sie [InitialControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.initialcontrols.aspx) auf „[None](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarinitialcontrols.aspx)“ fest.</span><span class="sxs-lookup"><span data-stu-id="5114b-172">Set [InitialControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.initialcontrols.aspx) to "[None](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarinitialcontrols.aspx)".</span></span>
4. <span data-ttu-id="5114b-173">Erstellen Sie Objektverweise für die für Ihre App erforderlichen Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="5114b-173">Create object references for the buttons required by your app.</span></span> <span data-ttu-id="5114b-174">Hier fügen wir nur [InkToolbarBallpointPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarballpointpenbutton.aspx), [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx) und [InkToolbarEraserButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbareraserbutton.aspx) hinzu.</span><span class="sxs-lookup"><span data-stu-id="5114b-174">Here, we add [InkToolbarBallpointPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarballpointpenbutton.aspx), [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx), and [InkToolbarEraserButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbareraserbutton.aspx) only.</span></span>
  > [!NOTE]
  > <span data-ttu-id="5114b-175">Schaltflächen werden der Symbolleiste in der vom Framework definierten Reihenfolge hinzugefügt, nicht in der hier angegebenen Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="5114b-175">Buttons are added to the toolbar in the order defined by the framework, not the order specified here.</span></span>

5. <span data-ttu-id="5114b-176">[Fügen Sie](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyobjectcollection.add.aspx) die Schaltflächen der InkToolbar hinzu.</span><span class="sxs-lookup"><span data-stu-id="5114b-176">[Add](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyobjectcollection.add.aspx) the buttons to the InkToolbar.</span></span>

  ```csharp
  /// <summary>
  /// Handles the Loading event of the InkToolbar.
  /// Here, we identify the buttons to include on the InkToolbar.
  /// </summary>
  /// <param name="sender">The InkToolbar</param>
  /// <param name="args">The InkToolbar event data.
  /// If there is no event data, this parameter is null</param>
  private void inkToolbar_Loading(FrameworkElement sender, object args)
  {
      // Clear all built-in buttons from the InkToolbar.
      inkToolbar.InitialControls = InkToolbarInitialControls.None;

      // Add only the ballpoint pen, pencil, and eraser.
      // Note that the buttons are added to the toolbar in the order
      // defined by the framework, not the order we specify here.
      InkToolbarBallpointPenButton ballpoint = new InkToolbarBallpointPenButton();
      InkToolbarPencilButton pencil = new InkToolbarPencilButton();
      InkToolbarEraserButton eraser = new InkToolbarEraserButton();
      inkToolbar.Children.Add(eraser);
      inkToolbar.Children.Add(ballpoint);
      inkToolbar.Children.Add(pencil);
  }
  ```

<!--
### Support touch input
By default, the InkToolbar supports both pen and mouse input, you have to enable support for touch input.
-->

## <a name="custom-buttons-and-inking-features"></a><span data-ttu-id="5114b-177">Benutzerdefinierte Schaltflächen und Freihandeingabefeatures</span><span class="sxs-lookup"><span data-stu-id="5114b-177">Custom buttons and inking features</span></span>

<span data-ttu-id="5114b-178">Sie können die Sammlung von Schaltflächen (und zugehörige Freihandeingabefeatures) anpassen und erweitern, die über die InkToolbar bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-178">You can customize and extend the collection of buttons (and associated inking features) that are provided through the InkToolbar.</span></span>

<span data-ttu-id="5114b-179">Das InkToolbar-Steuerelement besteht aus zwei unterschiedlichen Gruppen von Schaltflächentypen:</span><span class="sxs-lookup"><span data-stu-id="5114b-179">The InkToolbar consists of two distinct groups of button types:</span></span>

1. <span data-ttu-id="5114b-180">Eine Gruppe von „Toolschaltflächen“ mit den integrierten Schaltflächen zum Zeichnen, Radieren und Hervorheben.</span><span class="sxs-lookup"><span data-stu-id="5114b-180">A group of "tool" buttons containing the built-in drawing, erasing, and highlighting buttons.</span></span> <span data-ttu-id="5114b-181">Hier werden benutzerdefinierte Stifte und Tools hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5114b-181">Custom pens and tools are added here.</span></span>
> <span data-ttu-id="5114b-182">**Hinweis**&nbsp;&nbsp;Die ausgewählten Features schließen sich gegenseitig aus.</span><span class="sxs-lookup"><span data-stu-id="5114b-182">**Note**&nbsp;&nbsp;Feature selection is mutually exclusive.</span></span>

2. <span data-ttu-id="5114b-183">Eine Gruppe von „Umschaltflächen“ mit der integrierten Linealschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="5114b-183">A group of "toggle" buttons containing the built-in ruler button.</span></span> <span data-ttu-id="5114b-184">Hier werden benutzerdefinierte Umschaltflächen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5114b-184">Custom toggles are added here.</span></span>
> <span data-ttu-id="5114b-185">**Hinweis**&nbsp;&nbsp;Die Features schließen sich nicht gegenseitig aus und können gleichzeitig mit anderen aktiven Tools verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-185">**Note**&nbsp;&nbsp;Features are not mutually exclusive and can be used concurrently with other active tools.</span></span>

<span data-ttu-id="5114b-186">Je nach Anwendung und erforderlicher Freihandfunktion können Sie dem InkToolbar-Steuerelement eine der folgenden Schaltflächen (die an die benutzerdefinierten Freihandfunktionen gebunden sind) hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="5114b-186">Depending on your application and the inking functionality required, you can add any of the following buttons (bound to your custom ink features) to the InkToolbar:</span></span>

- <span data-ttu-id="5114b-187">Benutzerdefinierter Stift: Ein Stift, für den die Farbpaletten- und Stiftspitzeneigenschaften der Freihandeingabe wie Form, Drehung und Größe von der Host-App definiert werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-187">Custom pen – a pen for which the ink color palette and pen tip properties, such as shape, rotation, and size, are defined by the host app.</span></span>
- <span data-ttu-id="5114b-188">Benutzerdefiniertes Tool: Ein Tool ohne Stift, das von der Host-App definiert wird.</span><span class="sxs-lookup"><span data-stu-id="5114b-188">Custom tool – a non-pen tool, defined by the host app.</span></span>
- <span data-ttu-id="5114b-189">Benutzerdefiniertes Umschalten: Legt den Zustand eines durch die App definierten Features auf „aktiviert“ oder „deaktiviert“ fest.</span><span class="sxs-lookup"><span data-stu-id="5114b-189">Custom toggle – Sets the state of an app-defined feature to on or off.</span></span> <span data-ttu-id="5114b-190">Wenn die Schaltfläche aktiviert ist, funktioniert das Feature in Verbindung mit dem aktiven Tool.</span><span class="sxs-lookup"><span data-stu-id="5114b-190">When turned on, the feature works in conjunction with the active tool.</span></span>

> <span data-ttu-id="5114b-191">**Hinweis**&nbsp;&nbsp;Die Anzeigereihenfolge der integrierten Schaltflächen kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-191">**Note**&nbsp;&nbsp;You cannot change the display order of the built-in buttons.</span></span> <span data-ttu-id="5114b-192">Die standardmäßige Anzeigereihenfolge lautet wie folgt: Kugelschreiber, Stift, Textmarker, Radierer und Lineal.</span><span class="sxs-lookup"><span data-stu-id="5114b-192">The default display order is: Ballpoint pen, pencil, highlighter, eraser, and ruler.</span></span> <span data-ttu-id="5114b-193">Benutzerdefinierte Stifte werden an den letzten Standardstift angefügt, benutzerdefinierte Tool-Schaltflächen werden zwischen der letzten Stiftschaltfläche und der Radiererschaltfläche hinzugefügt, und benutzerdefinierte Umschaltflächen werden nach der Linealschaltfläche hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5114b-193">Custom pens are appended to the last default pen, custom tool buttons are added between the last pen button and the eraser button and custom toggle buttons are added after the ruler button.</span></span> <span data-ttu-id="5114b-194">(Benutzerdefinierte Schaltflächen werden in der Reihenfolge hinzugefügt, in der sie angegeben werden.)</span><span class="sxs-lookup"><span data-stu-id="5114b-194">(Custom buttons are added in the order they are specified.)</span></span>

### <a name="custom-pen"></a><span data-ttu-id="5114b-195">Benutzerdefinierter Stift</span><span class="sxs-lookup"><span data-stu-id="5114b-195">Custom pen</span></span>

<span data-ttu-id="5114b-196">Sie können einen benutzerdefinierten Stift (zur Aktivierung über eine entsprechende Schaltfläche) erstellen, wobei Sie die Tintenfarbpalette und die Eigenschaften der Stiftspitze (Form, Rotation, Größe) definieren.</span><span class="sxs-lookup"><span data-stu-id="5114b-196">You can create a custom pen (activated through a custom pen button) where you define the ink color palette and pen tip properties, such as shape, rotation, and size.</span></span>

![Benutzerdefinierte Kalligrafiefeder-Schaltfläche](.\images\ink\ink-tools-custompen.png)  
*<span data-ttu-id="5114b-198">Benutzerdefinierte Kalligrafiefeder-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="5114b-198">Custom calligraphic pen button</span></span>*

<span data-ttu-id="5114b-199">In diesem Beispiel legen wir einen benutzerdefinierten Stift mit einer breiten Spitze fest, die einfache kalligrafische Freihandstriche ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="5114b-199">For this example, we define a custom pen with a broad tip that enables basic calligraphic ink strokes.</span></span> <span data-ttu-id="5114b-200">Wir passen außerdem die Sammlung der Pinsel in der auf dem Schaltflächen-Flyout angezeigten Palette an.</span><span class="sxs-lookup"><span data-stu-id="5114b-200">We also customize the collection of brushes in the palette displayed on the button flyout.</span></span>

**<span data-ttu-id="5114b-201">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="5114b-201">Code-behind</span></span>**

<span data-ttu-id="5114b-202">Zuerst definieren wir unseren benutzerdefinierten Stift und geben die Zeichnungsattribute im CodeBehind an.</span><span class="sxs-lookup"><span data-stu-id="5114b-202">First, we define our custom pen and specify the drawing attributes in code-behind.</span></span> <span data-ttu-id="5114b-203">Wir verweisen später aus XAML auf diesen benutzerdefinierten Stift.</span><span class="sxs-lookup"><span data-stu-id="5114b-203">We reference this custom pen from XAML later.</span></span>

1. <span data-ttu-id="5114b-204">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie „Hinzufügen > Neues Element“ aus.</span><span class="sxs-lookup"><span data-stu-id="5114b-204">Right click the project in Solution Explorer and select Add -> New item.</span></span>
2. <span data-ttu-id="5114b-205">Fügen Sie unter „Visual C# -> Code“ eine neue Klassendatei hinzu, und nennen Sie sie „CalligraphicPen.cs“.</span><span class="sxs-lookup"><span data-stu-id="5114b-205">Under Visual C# -> Code, add a new Class file and call it CalligraphicPen.cs.</span></span>
3. <span data-ttu-id="5114b-206">Ersetzen Sie in „CalligraphicPen.cs“ den standardmäßigen using-Block durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="5114b-206">In Calligraphic.cs, replace the default using block with the following:</span></span>
```csharp
using System.Numerics;
using Windows.UI;
using Windows.UI.Input.Inking;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Media;
```

4. <span data-ttu-id="5114b-207">Geben Sie an, dass die CalligraphicPen-Klasse von [InkToolbarCustomPen](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompen.aspx) abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="5114b-207">Specify that the CalligraphicPen class is derived from [InkToolbarCustomPen](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompen.aspx).</span></span>
```csharp
class CalligraphicPen : InkToolbarCustomPen
{
}
```

5. <span data-ttu-id="5114b-208">Überschreiben Sie [CreateInkDrawingAttributesCore](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompen.createinkdrawingattributescore.aspx), um Ihre eigene Pinsel- und Strichgröße anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5114b-208">Override  [CreateInkDrawingAttributesCore](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompen.createinkdrawingattributescore.aspx)  to specify your own brush and stroke size.</span></span>
```csharp
class CalligraphicPen : InkToolbarCustomPen
{
    protected override InkDrawingAttributes
      CreateInkDrawingAttributesCore(Brush brush, double strokeWidth)
    {
    }
}
```

6. <span data-ttu-id="5114b-209">Erstellen Sie ein [InkDrawingAttributes](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.aspx)-Objekt, und legen Sie die [Form der Stiftspitze](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.pentip.aspx), [Drehung der Spitze](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.pentiptransform.aspx), [Strichgröße](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.size.aspx) und [Freihandfarbe](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.color.aspx) fest.</span><span class="sxs-lookup"><span data-stu-id="5114b-209">Create an [InkDrawingAttributes](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.aspx) object and set the [pen tip shape](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.pentip.aspx), [tip rotation](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.pentiptransform.aspx), [stroke size](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.size.aspx), and [ink color](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.color.aspx).</span></span>
```csharp
class CalligraphicPen : InkToolbarCustomPen
{
    protected override InkDrawingAttributes
      CreateInkDrawingAttributesCore(Brush brush, double strokeWidth)
    {
        InkDrawingAttributes inkDrawingAttributes =
          new InkDrawingAttributes();
        inkDrawingAttributes.PenTip = PenTipShape.Circle;
        inkDrawingAttributes.Size =
          new Windows.Foundation.Size(strokeWidth, strokeWidth * 20);
        SolidColorBrush solidColorBrush = brush as SolidColorBrush;
        if (solidColorBrush != null)
        {
            inkDrawingAttributes.Color = solidColorBrush.Color;
        }
        else
        {
            inkDrawingAttributes.Color = Colors.Black;
        }

        Matrix3x2 matrix = Matrix3x2.CreateRotation(45);
        inkDrawingAttributes.PenTipTransform = matrix;

        return inkDrawingAttributes;
    }
}
```

**<span data-ttu-id="5114b-210">XAML</span><span class="sxs-lookup"><span data-stu-id="5114b-210">XAML</span></span>**

<span data-ttu-id="5114b-211">Als Nächstes fügen wir die erforderlichen Verweise auf den benutzerdefinierten Stift in „MainPage.xaml“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="5114b-211">Next, we add the necessary references to the custom pen in MainPage.xaml.</span></span>

1. <span data-ttu-id="5114b-212">Wir deklarieren ein lokales Seitenressourcenverzeichnis, das einen Verweis auf den in „CalligraphicPen.cs“ festgelegten benutzerdefinierten Stift (`CalligraphicPen`) und eine [Pinselsammlung](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Media.BrushCollection.aspx) erstellt, die vom benutzerdefinierten Stift unterstützt wird (`CalligraphicPenPalette`).</span><span class="sxs-lookup"><span data-stu-id="5114b-212">We declare a local page resource dictionary that creates a reference to the custom pen (`CalligraphicPen`) defined in CalligraphicPen.cs, and a [brush collection](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Media.BrushCollection.aspx) supported by the custom pen (`CalligraphicPenPalette`).</span></span>
```xaml
<Page.Resources>
    <!-- Add the custom CalligraphicPen to the page resources. -->
    <local:CalligraphicPen x:Key="CalligraphicPen" />
    <!-- Specify the colors for the palette of the custom pen. -->
    <BrushCollection x:Key="CalligraphicPenPalette">
        <SolidColorBrush Color="Blue" />
        <SolidColorBrush Color="Red" />
    </BrushCollection>
</Page.Resources>
```

2. <span data-ttu-id="5114b-213">Wir fügen dann eine InkToolbar mit einem untergeordneten [InkToolbarCustomPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompenbutton.aspx)-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="5114b-213">We then add an InkToolbar with a child [InkToolbarCustomPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompenbutton.aspx) element.</span></span>

  <span data-ttu-id="5114b-214">Die benutzerdefinierte Stiftschaltfläche enthält zwei in den Seitenressourcen deklarierte statische Ressourcenverweise: `CalligraphicPen` und `CalligraphicPenPalette`.</span><span class="sxs-lookup"><span data-stu-id="5114b-214">The custom pen button includes the two static resource references declared in the page resources: `CalligraphicPen` and `CalligraphicPenPalette`.</span></span>

  <span data-ttu-id="5114b-215">Wir geben außerdem den Bereich für den Strichgröße-Schieberegler ([MinStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.minstrokewidth.aspx), [MaxStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.maxstrokewidth.aspx) und [SelectedStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.selectedstrokewidthproperty.aspx)), den ausgewählten Pinsel ([SelectedBrushIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.selectedbrushindex.aspx)) und das Symbol für die benutzerdefinierte Stiftschaltfläche ([SymbolIcon](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.symbolicon.aspx)) an.</span><span class="sxs-lookup"><span data-stu-id="5114b-215">We also specify the range for the stroke size slider ([MinStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.minstrokewidth.aspx), [MaxStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.maxstrokewidth.aspx), and [SelectedStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.selectedstrokewidthproperty.aspx)), the selected brush ([SelectedBrushIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.selectedbrushindex.aspx)), and the icon for the custom pen button ([SymbolIcon](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.symbolicon.aspx)).</span></span>
```xaml
<Grid Grid.Row="1">
    <InkCanvas x:Name="inkCanvas" />
    <InkToolbar x:Name="inkToolbar"
                VerticalAlignment="Top"
                TargetInkCanvas="{x:Bind inkCanvas}">
        <InkToolbarCustomPenButton
            CustomPen="{StaticResource CalligraphicPen}"
            Palette="{StaticResource CalligraphicPenPalette}"
            MinStrokeWidth="1" MaxStrokeWidth="3" SelectedStrokeWidth="2"
            SelectedBrushIndex ="1">
            <SymbolIcon Symbol="Favorite" />
            <InkToolbarCustomPenButton.ConfigurationContent>
                <InkToolbarPenConfigurationControl />
            </InkToolbarCustomPenButton.ConfigurationContent>
        </InkToolbarCustomPenButton>
    </InkToolbar>
</Grid>
```

### <a name="custom-toggle"></a><span data-ttu-id="5114b-216">Benutzerdefiniertes Umschalten</span><span class="sxs-lookup"><span data-stu-id="5114b-216">Custom toggle</span></span>

<span data-ttu-id="5114b-217">Sie können eine benutzerdefinierte Umschaltung (zur Aktivierung über eine entsprechende Schaltfläche) erstellen, um den Zustand eines von der App definierten Features als „aktiviert“ oder „nicht aktiviert“ einzurichten.</span><span class="sxs-lookup"><span data-stu-id="5114b-217">You can create a custom toggle (activated through a custom toggle button) to set the state of an app-defined feature to on or off.</span></span> <span data-ttu-id="5114b-218">Wenn die Schaltfläche aktiviert ist, funktioniert das Feature in Verbindung mit dem aktiven Tool.</span><span class="sxs-lookup"><span data-stu-id="5114b-218">When turned on, the feature works in conjunction with the active tool.</span></span>

<span data-ttu-id="5114b-219">In diesem Beispiel definieren wir eine Schaltfläche für das benutzerdefinierte Umschalten, die das Freihandzeichnen mit Toucheingabe ermöglicht (standardmäßig ist die Touch-Freihandeingabe nicht aktiviert).</span><span class="sxs-lookup"><span data-stu-id="5114b-219">In this example, we define a custom toggle button that enables inking with touch input (by default, touch inking is not enabled).</span></span>

> [!NOTE]  
> <span data-ttu-id="5114b-220">Wenn Sie das Freihandzeichnen mit der Toucheingabe unterstützen müssen, sollten Sie es mit einem CustomToggleButton mit dem in diesem Beispiel angegebenen Symbol und der QuickInfo aktivieren.</span><span class="sxs-lookup"><span data-stu-id="5114b-220">If you need to support inking with touch, we recommended that you enable it using a CustomToggleButton, with the icon and tooltip specified in this example.</span></span>

<span data-ttu-id="5114b-221">Typischerweise wird die Toucheingabe für die direkte Manipulation eines Objekts oder der Benutzeroberfläche der App verwendet.</span><span class="sxs-lookup"><span data-stu-id="5114b-221">Typically, touch input is used for direct manipulation of an object or the app UI.</span></span> <span data-ttu-id="5114b-222">Zur Demonstration der Unterschiede in der Verhaltensweise bei aktiviertem Freihandzeichen mit Toucheingabe setzen wir den InkCanvas in einen ScrollView-Container und stellen die ScrollViewer-Abmessungen kleiner als die des InkCanvas ein.</span><span class="sxs-lookup"><span data-stu-id="5114b-222">To demonstrate the differences in behavior when touch inking is enabled, we place the InkCanvas within a ScrollViewer container and set the dimensions of the ScrollViewer to be smaller than the InkCanvas.</span></span> 

<span data-ttu-id="5114b-223">Beim Starten der App wird nur die Stift-Freihandeingabe unterstützt, und die Toucheingabe wird zum Schwenken oder Zoomen der Freihand-Oberfläche verwendet.</span><span class="sxs-lookup"><span data-stu-id="5114b-223">When the app starts, only pen inking is supported and touch is used to pan or zoom the inking surface.</span></span> <span data-ttu-id="5114b-224">Wenn die Touch-Freihandeingabe aktiviert ist, kann die Freihand-Oberfläche nicht über die Toucheingabe geschwenkt oder gezoomt werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-224">When touch inking is enabled, the inking surface cannot be panned or zoomed through touch input.</span></span>

> [!NOTE]
> <span data-ttu-id="5114b-225">Unter [Freihand-Steuerelemente](..\controls-and-patterns\inking-controls.md) finden Sie Anleitungen zu [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkCanvas) und [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbar) UX.</span><span class="sxs-lookup"><span data-stu-id="5114b-225">See [Inking controls](..\controls-and-patterns\inking-controls.md) for both [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkCanvas) and [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbar) UX guidelines.</span></span> <span data-ttu-id="5114b-226">Für dieses Beispiel gelten die folgenden Empfehlungen:</span><span class="sxs-lookup"><span data-stu-id="5114b-226">The following recommendations are relevant to this example:</span></span>
> - <span data-ttu-id="5114b-227">Die [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbar) und die Freihandeingabe allgemein werden am besten über einen aktiven Stift bedient.</span><span class="sxs-lookup"><span data-stu-id="5114b-227">The [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbar), and inking in general, is best experienced through an active pen.</span></span> <span data-ttu-id="5114b-228">Die Freihandeingabe mit Maus- und Toucheingabe kann aber unterstützt werden, wenn dies für Ihre App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="5114b-228">However, inking with mouse and touch can be supported if required by your app.</span></span> 
> - <span data-ttu-id="5114b-229">Bei Unterstützung der Freihandfunktion per Toucheingabe wird empfohlen, das Symbol „ED5F“ aus der Schriftart „Segoe MLD2 Assets” für die Umschaltfläche mit einer QuickInfo „Schreiben durch Berühren” zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5114b-229">If supporting inking with touch input, we recommend using the "ED5F" icon from the "Segoe MLD2 Assets" font for the toggle button, with a "Touch writing" tooltip.</span></span> 

**<span data-ttu-id="5114b-230">XAML</span><span class="sxs-lookup"><span data-stu-id="5114b-230">XAML</span></span>**

1. <span data-ttu-id="5114b-231">Zuerst deklarieren wir ein [**InkToolbarCustomToggleButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToggleButton)-Element (toggleButton) mit einem Klickereignis-Listener, der den Ereignishandler (Toggle_Custom) angibt.</span><span class="sxs-lookup"><span data-stu-id="5114b-231">First, we declare an [**InkToolbarCustomToggleButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToggleButton) element (toggleButton) with a Click event listener that specifies the event handler (Toggle_Custom).</span></span>

```xaml 
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>

    <StackPanel Grid.Row="0" 
                x:Name="HeaderPanel" 
                Orientation="Horizontal">
        <TextBlock x:Name="Header" 
                   Text="Basic ink sample" 
                   Style="{ThemeResource HeaderTextBlockStyle}" 
                   Margin="10" />
    </StackPanel>

    <ScrollViewer Grid.Row="1" 
                  HorizontalScrollBarVisibility="Auto" 
                  VerticalScrollBarVisibility="Auto">
        
        <Grid HorizontalAlignment="Left" VerticalAlignment="Top">
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*"/>
            </Grid.RowDefinitions>
            
            <InkToolbar Grid.Row="0" 
                        Margin="10"
                        x:Name="inkToolbar" 
                        VerticalAlignment="Top"
                        TargetInkCanvas="{x:Bind inkCanvas}">
                <InkToolbarCustomToggleButton 
                x:Name="toggleButton" 
                Click="CustomToggle_Click" 
                ToolTipService.ToolTip="Touch Writing">
                    <SymbolIcon Symbol="{x:Bind TouchWritingIcon}"/>
                </InkToolbarCustomToggleButton>
            </InkToolbar>
            
            <ScrollViewer Grid.Row="1" 
                          Height="500"
                          Width="500"
                          x:Name="scrollViewer" 
                          ZoomMode="Enabled" 
                          MinZoomFactor=".1" 
                          VerticalScrollMode="Enabled" 
                          VerticalScrollBarVisibility="Auto" 
                          HorizontalScrollMode="Enabled" 
                          HorizontalScrollBarVisibility="Auto">
                
                <Grid x:Name="outputGrid" 
                      Height="1000"
                      Width="1000"
                      Background="{ThemeResource SystemControlBackgroundChromeWhiteBrush}">
                    <InkCanvas x:Name="inkCanvas"/>
                </Grid>
                
            </ScrollViewer>
        </Grid>
    </ScrollViewer>
</Grid>
```

**<span data-ttu-id="5114b-232">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="5114b-232">Code-behind</span></span>**

2. <span data-ttu-id="5114b-233">Im vorigen Codeausschnitt haben wir einen Klickereignis-Listener und -Handler (Toggle_Custom) auf der Schaltfläche für benutzerdefiniertes Umschalten für die benutzerdefinierte Schaltfläche für die Touch-Freihandeingabe (toggleButton) deklariert.</span><span class="sxs-lookup"><span data-stu-id="5114b-233">In the previous snippet, we declared a Click event listener and handler (Toggle_Custom) on the custom toggle button for touch inking (toggleButton).</span></span> <span data-ttu-id="5114b-234">Dieser Handler wechselt einfach die Unterstützung für CoreInputDeviceTypes.Touch über die Eigenschaft InputDeviceTypes des InkPresenter.</span><span class="sxs-lookup"><span data-stu-id="5114b-234">This handler simply toggles support for CoreInputDeviceTypes.Touch through the InputDeviceTypes property of the InkPresenter.</span></span>

   <span data-ttu-id="5114b-235">Hierzu haben wir ein Symbol für die Schaltfläche angegeben, wobei das SymbolIcon-Element und die Markuperweiterung [x:Bind], die dieses an ein in der CodeBehind-Datei (TouchWritingIcon) definiertes Feld bindet, verwendet wurden.</span><span class="sxs-lookup"><span data-stu-id="5114b-235">We also specified an icon for the button using the SymbolIcon element and the {x:Bind} markup extension that binds it to a field defined in the code-behind file (TouchWritingIcon).</span></span>

   <span data-ttu-id="5114b-236">Der folgende Codeausschnitt enthält den Klickereignis-Handler und die Definition von TouchWritingIcon.</span><span class="sxs-lookup"><span data-stu-id="5114b-236">The following snippet includes both the Click event handler and the definition of TouchWritingIcon.</span></span>

```csharp 
namespace Ink_Basic_InkToolbar
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage_AddCustomToggle : Page
    {
        Symbol TouchWritingIcon = (Symbol)0xED5F;

        public MainPage_AddCustomToggle()
        {
            this.InitializeComponent();
        }

        // Handler for the custom toggle button that enables touch inking.
        private void CustomToggle_Click(object sender, RoutedEventArgs e)
        {
            if (toggleButton.IsChecked == true)
            {
                inkCanvas.InkPresenter.InputDeviceTypes |= CoreInputDeviceTypes.Touch;
            }
            else
            {
                inkCanvas.InkPresenter.InputDeviceTypes &= ~CoreInputDeviceTypes.Touch;
            }
        }
    }
}
```

### <a name="custom-tool"></a><span data-ttu-id="5114b-237">Benutzerdefiniertes Tool</span><span class="sxs-lookup"><span data-stu-id="5114b-237">Custom tool</span></span>

<span data-ttu-id="5114b-238">Sie können eine Schaltfläche für ein benutzerdefiniertes Tool erstellen, die ein von Ihrer App definiertes Nicht-Stift-Tool aufruft.</span><span class="sxs-lookup"><span data-stu-id="5114b-238">You can create a custom tool button to invoke a non-pen tool that is defined by your app.</span></span>

<span data-ttu-id="5114b-239">Standardmäßig verarbeitet ein [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) sämtliche Eingaben als Freihandstrich oder als Radierstrich.</span><span class="sxs-lookup"><span data-stu-id="5114b-239">By default, an [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) processes all input as either an ink stroke or an erase stroke.</span></span> <span data-ttu-id="5114b-240">Hierzu zählen auch Eingaben, die durch ein sekundäres Hardwareangebot wie etwa eine Zeichenstift-Drucktaste, eine rechte Maustaste oder ein ähnliches Element geändert werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-240">This includes input modified by a secondary hardware affordance such as a pen barrel button, a right mouse button, or similar.</span></span> <span data-ttu-id="5114b-241">Allerdings kann ein [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) so konfiguriert werden, dass bestimmte Eingaben unverarbeitet gelassen werden. Diese können dann für die benutzerdefinierte Verarbeitung an Ihre App weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-241">However, [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) can be configured to leave specific input unprocessed, which can then be passed through to your app for custom processing.</span></span>

<span data-ttu-id="5114b-242">In diesem Beispiel definieren wir eine Schaltfläche für ein benutzerdefiniertes Tool, das bei Auswahl bewirkt, dass nachfolgende Striche verarbeitet und als Auswahllasso (gestrichelte Linie) und nicht als Freihandeingabe wiedergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-242">In this example, we define a custom tool button that, when selected, causes subsequent strokes to be processed and rendered as a selection lasso (dashed line) instead of ink.</span></span> <span data-ttu-id="5114b-243">Alle Freihandstriche innerhalb der Grenzen des Auswahlbereichs werden auf [**Ausgewählt**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkStroke.Selected) gesetzt.</span><span class="sxs-lookup"><span data-stu-id="5114b-243">All ink strokes within the bounds of the selection area are set to [**Selected**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkStroke.Selected).</span></span>

> [!NOTE]
> <span data-ttu-id="5114b-244">Weitere Informationen zu InkCanvas und InkToolbar UX finden Sie in den Anleitungen zu Freihandsteuerelementen.</span><span class="sxs-lookup"><span data-stu-id="5114b-244">See Inking controls for both InkCanvas and InkToolbar UX guidelines.</span></span> <span data-ttu-id="5114b-245">Für dieses Beispiel gilt die folgende Empfehlung:</span><span class="sxs-lookup"><span data-stu-id="5114b-245">The following recommendation is relevant to this example:</span></span>
> - <span data-ttu-id="5114b-246">Für die Bereitstellung der Strichauswahl empfehlen wir die Verwendung des „EF20“-Symbols aus der Schriftart „Segoe MLD2 Assets“ für die Toolschaltfläche, mit einer QuickInfo „Auswahltool“.</span><span class="sxs-lookup"><span data-stu-id="5114b-246">If providing stroke selection, we recommend using the "EF20" icon from the "Segoe MLD2 Assets" font for the tool button, with a "Selection tool" tooltip.</span></span> 
 
**<span data-ttu-id="5114b-247">XAML</span><span class="sxs-lookup"><span data-stu-id="5114b-247">XAML</span></span>**

1. <span data-ttu-id="5114b-248">Zunächst deklarieren wir ein [**InkToolbarCustomToolButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToolButton)-Element (CustomToolButton) mit einem Klickereignis-Listener, der den Ereignishandler (customToolButton_Click) angibt, in dem die Strichauswahl konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="5114b-248">First, we declare an [**InkToolbarCustomToolButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToolButton) element (customToolButton) with a Click event listener that specifies the event handler (customToolButton_Click) where stroke selection is configured.</span></span> <span data-ttu-id="5114b-249">(Es wurden außerdem verschiedene Schaltflächen zum Kopieren, Ausschneiden und Einfügen der Strichauswahl hinzugefügt.)</span><span class="sxs-lookup"><span data-stu-id="5114b-249">(We've also added a set of buttons for copying, cutting, and pasting the stroke selection.)</span></span>

2. <span data-ttu-id="5114b-250">Ebenfalls hinzu kommt ein Zeichenbereichelement zum Zeichnen unseres Auswahlstrichs.</span><span class="sxs-lookup"><span data-stu-id="5114b-250">We also add a Canvas element for drawing our selection stroke.</span></span> <span data-ttu-id="5114b-251">Durch die Verwendung einer eigenen Ebene zum Zeichnen der Strichauswahl bleiben der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkCanvas) und dessen Inhalt unverändert.</span><span class="sxs-lookup"><span data-stu-id="5114b-251">Using a separate layer to draw the selection stroke ensures the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkCanvas) and its content remain untouched.</span></span> 

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
        <TextBlock x:Name="Header" 
                   Text="Basic ink sample" 
                   Style="{ThemeResource HeaderTextBlockStyle}" 
                   Margin="10,0,0,0" />
    </StackPanel>
    <StackPanel x:Name="ToolPanel" Orientation="Horizontal" Grid.Row="1">
        <InkToolbar x:Name="inkToolbar" 
                    VerticalAlignment="Top" 
                    TargetInkCanvas="{x:Bind inkCanvas}">
            <InkToolbarCustomToolButton 
                x:Name="customToolButton" 
                Click="customToolButton_Click" 
                ToolTipService.ToolTip="Selection tool">
                <SymbolIcon Symbol="{x:Bind SelectIcon}"/>
            </InkToolbarCustomToolButton>
        </InkToolbar>
        <Button x:Name="cutButton" 
                Content="Cut" 
                Click="cutButton_Click"
                Width="100"
                Margin="5,0,0,0"/>
        <Button x:Name="copyButton" 
                Content="Copy"  
                Click="copyButton_Click"
                Width="100"
                Margin="5,0,0,0"/>
        <Button x:Name="pasteButton" 
                Content="Paste"  
                Click="pasteButton_Click"
                Width="100"
                Margin="5,0,0,0"/>
    </StackPanel>
    <Grid Grid.Row="2" x:Name="outputGrid" 
              Background="{ThemeResource SystemControlBackgroundChromeWhiteBrush}" 
              Height="Auto">
        <!-- Canvas for displaying selection UI. -->
        <Canvas x:Name="selectionCanvas"/>
        <!-- Canvas for displaying ink. -->
        <InkCanvas x:Name="inkCanvas" />
    </Grid>
</Grid>
```

**<span data-ttu-id="5114b-252">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="5114b-252">Code-behind</span></span>**

2. <span data-ttu-id="5114b-253">Anschließend behandeln wir das Klickereignis für [**InkToolbarCustomToolButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToolButton) in der CodeBehind-Datei MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="5114b-253">We then handle the Click event for the [**InkToolbarCustomToolButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToolButton) in the MainPage.xaml.cs code-behind file.</span></span>

   <span data-ttu-id="5114b-254">Dieser Handler konfiguriert den [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) so, dass unverarbeitete Eingaben an die App weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="5114b-254">This handler configures the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) to pass unprocessed input through to the app.</span></span> 

   <span data-ttu-id="5114b-255">Eine ausführlichere Schritt-für-Schritt-Anleitung zu diesem Code finden Sie im Abschnitt „Weitergabe der Eingabe für die erweiterte Verarbeitung“ von [Stiftinteraktionen und Windows Ink in UWP-Apps](pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="5114b-255">For a more detailed step through of this code:  See the Pass-through input for advanced processing section of [Pen interactions and Windows Ink in UWP apps](pen-and-stylus-interactions.md).</span></span>

   <span data-ttu-id="5114b-256">Hierzu haben wir ein Symbol für die Schaltfläche angegeben, wobei das SymbolIcon-Element und die Markuperweiterung [x:Bind], die dieses an ein in der CodeBehind-Datei (SelectIcon) definiertes Feld bindet, verwendet wurden.</span><span class="sxs-lookup"><span data-stu-id="5114b-256">We also specified an icon for the button using the SymbolIcon element and the {x:Bind} markup extension that binds it to a field defined in the code-behind file (SelectIcon).</span></span>

   <span data-ttu-id="5114b-257">Der folgende Codeausschnitt enthält den Klickereignis-Handler und die Definition von SelectIcon.</span><span class="sxs-lookup"><span data-stu-id="5114b-257">The following snippet includes both the Click event handler and the definition of SelectIcon.</span></span>

```csharp
namespace Ink_Basic_InkToolbar
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage_AddCustomTool : Page
    {
        // Icon for custom selection tool button.
        Symbol SelectIcon = (Symbol)0xEF20;

        // Stroke selection tool.
        private Polyline lasso;
        // Stroke selection area.
        private Rect boundingRect;

        public MainPage_AddCustomTool()
        {
            this.InitializeComponent();

            // Listen for new ink or erase strokes to clean up selection UI.
            inkCanvas.InkPresenter.StrokeInput.StrokeStarted +=
                StrokeInput_StrokeStarted;
            inkCanvas.InkPresenter.StrokesErased +=
                InkPresenter_StrokesErased;
        }

        private void customToolButton_Click(object sender, RoutedEventArgs e)
        {
            // By default, the InkPresenter processes input modified by 
            // a secondary affordance (pen barrel button, right mouse 
            // button, or similar) as ink.
            // To pass through modified input to the app for custom processing 
            // on the app UI thread instead of the background ink thread, set 
            // InputProcessingConfiguration.RightDragAction to LeaveUnprocessed.
            inkCanvas.InkPresenter.InputProcessingConfiguration.RightDragAction =
                InkInputRightDragAction.LeaveUnprocessed;

            // Listen for unprocessed pointer events from modified input.
            // The input is used to provide selection functionality.
            inkCanvas.InkPresenter.UnprocessedInput.PointerPressed +=
                UnprocessedInput_PointerPressed;
            inkCanvas.InkPresenter.UnprocessedInput.PointerMoved +=
                UnprocessedInput_PointerMoved;
            inkCanvas.InkPresenter.UnprocessedInput.PointerReleased +=
                UnprocessedInput_PointerReleased;
        }

        // Handle new ink or erase strokes to clean up selection UI.
        private void StrokeInput_StrokeStarted(
            InkStrokeInput sender, Windows.UI.Core.PointerEventArgs args)
        {
            ClearSelection();
        }

        private void InkPresenter_StrokesErased(
            InkPresenter sender, InkStrokesErasedEventArgs args)
        {
            ClearSelection();
        }

        private void cutButton_Click(object sender, RoutedEventArgs e)
        {
            inkCanvas.InkPresenter.StrokeContainer.CopySelectedToClipboard();
            inkCanvas.InkPresenter.StrokeContainer.DeleteSelected();
            ClearSelection();
        }

        private void copyButton_Click(object sender, RoutedEventArgs e)
        {
            inkCanvas.InkPresenter.StrokeContainer.CopySelectedToClipboard();
        }

        private void pasteButton_Click(object sender, RoutedEventArgs e)
        {
            if (inkCanvas.InkPresenter.StrokeContainer.CanPasteFromClipboard())
            {
                inkCanvas.InkPresenter.StrokeContainer.PasteFromClipboard(
                    new Point(0, 0));
            }
            else
            {
                // Cannot paste from clipboard.
            }
        }

        // Clean up selection UI.
        private void ClearSelection()
        {
            var strokes = inkCanvas.InkPresenter.StrokeContainer.GetStrokes();
            foreach (var stroke in strokes)
            {
                stroke.Selected = false;
            }
            ClearBoundingRect();
        }

        private void ClearBoundingRect()
        {
            if (selectionCanvas.Children.Any())
            {
                selectionCanvas.Children.Clear();
                boundingRect = Rect.Empty;
            }
        }

        // Handle unprocessed pointer events from modifed input.
        // The input is used to provide selection functionality.
        // Selection UI is drawn on a canvas under the InkCanvas.
        private void UnprocessedInput_PointerPressed(
            InkUnprocessedInput sender, PointerEventArgs args)
        {
            // Initialize a selection lasso.
            lasso = new Polyline()
            {
                Stroke = new SolidColorBrush(Windows.UI.Colors.Blue),
                StrokeThickness = 1,
                StrokeDashArray = new DoubleCollection() { 5, 2 },
            };

            lasso.Points.Add(args.CurrentPoint.RawPosition);

            selectionCanvas.Children.Add(lasso);
        }

        private void UnprocessedInput_PointerMoved(
            InkUnprocessedInput sender, PointerEventArgs args)
        {
            // Add a point to the lasso Polyline object.
            lasso.Points.Add(args.CurrentPoint.RawPosition);
        }

        private void UnprocessedInput_PointerReleased(
            InkUnprocessedInput sender, PointerEventArgs args)
        {
            // Add the final point to the Polyline object and 
            // select strokes within the lasso area.
            // Draw a bounding box on the selection canvas 
            // around the selected ink strokes.
            lasso.Points.Add(args.CurrentPoint.RawPosition);

            boundingRect =
                inkCanvas.InkPresenter.StrokeContainer.SelectWithPolyLine(
                    lasso.Points);

            DrawBoundingRect();
        }

        // Draw a bounding rectangle, on the selection canvas, encompassing 
        // all ink strokes within the lasso area.
        private void DrawBoundingRect()
        {
            // Clear all existing content from the selection canvas.
            selectionCanvas.Children.Clear();

            // Draw a bounding rectangle only if there are ink strokes 
            // within the lasso area.
            if (!((boundingRect.Width == 0) ||
                (boundingRect.Height == 0) ||
                boundingRect.IsEmpty))
            {
                var rectangle = new Rectangle()
                {
                    Stroke = new SolidColorBrush(Windows.UI.Colors.Blue),
                    StrokeThickness = 1,
                    StrokeDashArray = new DoubleCollection() { 5, 2 },
                    Width = boundingRect.Width,
                    Height = boundingRect.Height
                };

                Canvas.SetLeft(rectangle, boundingRect.X);
                Canvas.SetTop(rectangle, boundingRect.Y);

                selectionCanvas.Children.Add(rectangle);
            }
        }
    }
}
```



### <a name="custom-ink-rendering"></a><span data-ttu-id="5114b-258">Benutzerdefiniertes Rendern von Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="5114b-258">Custom ink rendering</span></span>

<span data-ttu-id="5114b-259">Standardmäßig werden Freihandeingaben in einem Hintergrundthread mit geringer Wartezeit verarbeitet und während des Zeichnens „nass“ gerendert.</span><span class="sxs-lookup"><span data-stu-id="5114b-259">By default, ink input is processed on a low-latency background thread and rendered "wet" as it is drawn.</span></span> <span data-ttu-id="5114b-260">Wenn der Strich abgeschlossen ist (der Stift oder Finger wurde angehoben oder die Maustaste losgelassen), wird er im UI-Thread verarbeitet und auf der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Ebene „trocken“ gerendert (über dem Anwendungsinhalt, wo er die nasse Freihandeingabe ersetzt).</span><span class="sxs-lookup"><span data-stu-id="5114b-260">When the stroke is completed (pen or finger lifted, or mouse button released), the stroke is processed on the UI thread and rendered "dry" to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) layer (above the application content and replacing the wet ink).</span></span>

<span data-ttu-id="5114b-261">Die Freihandplattform ermöglicht es Ihnen, dieses Verhalten zu überschreiben und die Freihandfunktionen durch benutzerdefiniertes Trocknen der Freihandeingabe umfassend anzupassen.</span><span class="sxs-lookup"><span data-stu-id="5114b-261">The ink platform enables you to override this behavior and completely customize the inking experience by custom drying the ink input.</span></span>

<span data-ttu-id="5114b-262">Weitere Informationen zum benutzerdefinierten Trocknen finden Sie unter [Stiftinteraktionen und Windows Ink in UWP-Apps](https://msdn.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions#custom-ink-rendering).</span><span class="sxs-lookup"><span data-stu-id="5114b-262">For more info on custom drying, see [Pen interactions and Windows Ink in UWP apps](https://msdn.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions#custom-ink-rendering).</span></span>

> [!NOTE]
> <span data-ttu-id="5114b-263">Benutzerdefiniertes Trocknen und die [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="5114b-263">Custom drying and the [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)</span></span>  
> <span data-ttu-id="5114b-264">Wenn Ihre App das Standard-Renderverhalten für Freihandeingaben von [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) mit einer benutzerdefinierten Trockenimplementierung außer Kraft setzt, sind die gerenderten Freihandstriche für die InkToolbar nicht mehr verfügbar und die integrierten Löschbefehle der InkToolbar funktionieren nicht wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="5114b-264">If your app overrides the default ink rendering behavior of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) with a custom drying implementation, the rendered ink strokes are no longer available to the InkToolbar and the built-in erase commands of the InkToolbar do not work as expected.</span></span> <span data-ttu-id="5114b-265">Damit Sie Löschfunktionen bereitstellen können, müssen Sie alle Zeigerereignisse verarbeiten, für jeden Strich einen Treffertest ausführen und den integrierten Befehl „Freihand vollständig löschen“ überschreiben.</span><span class="sxs-lookup"><span data-stu-id="5114b-265">To provide erase functionality, you must handle all pointer events, perform hit-testing on each stroke, and override the built-in "Erase all ink" command.</span></span>

## <a name="related-articles"></a><span data-ttu-id="5114b-266">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="5114b-266">Related articles</span></span>

* [<span data-ttu-id="5114b-267">Zeichen- und Eingabestiftinteraktionen</span><span class="sxs-lookup"><span data-stu-id="5114b-267">Pen and stylus interactions</span></span>](pen-and-stylus-interactions.md)

**<span data-ttu-id="5114b-268">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5114b-268">Samples</span></span>**
* [<span data-ttu-id="5114b-269">Einfaches Freihandbeispiel (C#/C++)</span><span class="sxs-lookup"><span data-stu-id="5114b-269">Simple ink sample (C#/C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620312)
* [<span data-ttu-id="5114b-270">Komplexes Freihandbeispiel (C++)</span><span class="sxs-lookup"><span data-stu-id="5114b-270">Complex ink sample (C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620314)
* [<span data-ttu-id="5114b-271">Freihandbeispiel (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="5114b-271">Ink sample (JavaScript)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620308)
* [<span data-ttu-id="5114b-272">Lernprogramm „Erste Schritte:” Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="5114b-272">Get Started Tutorial: Support ink in your UWP app</span></span>](https://aka.ms/appsample-ink)
* [<span data-ttu-id="5114b-273">Malbuchbeispiel</span><span class="sxs-lookup"><span data-stu-id="5114b-273">Coloring book sample</span></span>](https://aka.ms/cpubsample-coloringbook)
* [<span data-ttu-id="5114b-274">Familiennotizbeispiel</span><span class="sxs-lookup"><span data-stu-id="5114b-274">Family notes sample</span></span>](https://aka.ms/cpubsample-familynotessample)

