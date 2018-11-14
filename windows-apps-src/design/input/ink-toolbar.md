---
author: Karl-Bridge-Microsoft
Description: Add a default InkToolbar to a Universal Windows Platform (UWP) inking app, add a custom pen button to the InkToolbar, and bind the custom pen button to a custom pen definition.
title: Hinzufügen von InkToolbar zu einer App für die Universelle Windows-Plattform (UWP)
label: Add an InkToolbar to a Universal Windows Platform (UWP) app
template: detail.hbs
keywords: Windows Ink, Windows-Freihandeingabe, DirectInk, InkPresenter, InkCanvas, InkToolbar, Universelle Windows-Platform, UWP, Benutzerinteraktion, Eingabe
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.assetid: d888f75f-c2a0-4134-81db-907b5e24fcc5
ms.localizationpriority: medium
ms.openlocfilehash: b6896a4c149084dd5609f2ac6737c803a18d14ac
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6183795"
---
# <a name="add-an-inktoolbar-to-a-universal-windows-platform-uwp-app"></a><span data-ttu-id="2aa7c-103">Hinzufügen von InkToolbar zu einer App für die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="2aa7c-103">Add an InkToolbar to a Universal Windows Platform (UWP) app</span></span>



<span data-ttu-id="2aa7c-104">Es gibt zwei verschiedene Steuerelemente, die die Freihandeingabe in Apps in der universellen Windows-Plattform (UWP) vereinfachen: [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx) und [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-104">There are two different controls that facilitate inking in Universal Windows Platform (UWP) apps: [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx) and [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx).</span></span>

<span data-ttu-id="2aa7c-105">Über das [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx)-Steuerelement werden grundlegende Windows Ink-Funktionen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-105">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx) control provides basic Windows Ink functionality.</span></span> <span data-ttu-id="2aa7c-106">Rendern Sie damit die Stifteingabe entweder als letzten Strich (mit den Standardeinstellungen für Farbe und Stärke) oder ausradierten Strich.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-106">Use it to render pen input as either an ink stroke (using default settings for color and thickness) or an erase stroke.</span></span>

> <span data-ttu-id="2aa7c-107">Details zur Implementierung von InkCanvas finden Sie unter [Zeichen- und Eingabestiftinteraktionen in UWP-Apps](pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-107">For InkCanvas implementation details, see [Pen and stylus interactions in UWP apps](pen-and-stylus-interactions.md).</span></span>

<span data-ttu-id="2aa7c-108">Als vollständig transparente Überlagerung bietet InkCanvas keine integrierte Benutzeroberfläche zum Festlegen von Freihandstricheinstellungen.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-108">As a completely transparent overlay, the InkCanvas does not provide any built-in UI for setting ink stroke properties.</span></span> <span data-ttu-id="2aa7c-109">Wenn Sie die Standard-Freihandfunktionen ändern, Benutzern das Festlegen von Freihandstricheinstellungen ermöglichen und andere benutzerdefinierte Freihandeingabefeatures unterstützen möchten, haben Sie zwei Optionen:</span><span class="sxs-lookup"><span data-stu-id="2aa7c-109">If you want to change the default inking experience, let users set ink stroke properties, and support other custom inking features, you have two options:</span></span>

- <span data-ttu-id="2aa7c-110">Verwenden Sie im CodeBehind das an InkCanvas gebundene zugrunde liegende [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-110">In code-behind, use the underlying [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx) object bound to the InkCanvas.</span></span>

  <span data-ttu-id="2aa7c-111">Die InkPresenter-APIs unterstützen die umfassende Anpassung der Freihandfunktionen.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-111">The InkPresenter APIs support extensive customization of the inking experience.</span></span> <span data-ttu-id="2aa7c-112">Weitere Informationen finden Sie unter [Zeichen- und Eingabestiftinteraktionen in UWP-Apps](pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-112">For more detail, see [Pen and stylus interactions in UWP apps](pen-and-stylus-interactions.md).</span></span>

- <span data-ttu-id="2aa7c-113">Binden Sie [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) an InkCanvas.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-113">Bind an [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) to the InkCanvas.</span></span> <span data-ttu-id="2aa7c-114">InkToolbar bietet standardmäßig eine anpassbare und erweiterbare Sammlung von Schaltflächen zum Aktivieren von Freihandfunktionen wie Strichgröße, Freihandfarbe und Form der Stiftspitze.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-114">By default, the InkToolbar provides a customizable and extensible collection of buttons for activating ink-related features such as stroke size, ink color, and pen tip.</span></span>

  <span data-ttu-id="2aa7c-115">InkToolbar wird in diesem Thema erläutert.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-115">We discuss the InkToolbar in this topic.</span></span>

> <span data-ttu-id="2aa7c-116">**Wichtige APIs**: [**InkCanvas class**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx), [**InkToolbar class**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx), [**InkPresenter class**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx), [**Windows.UI.Input.Inking**](https://msdn.microsoft.com/library/windows/apps/br208524)</span><span class="sxs-lookup"><span data-stu-id="2aa7c-116">**Important APIs**: [**InkCanvas class**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inkcanvas.aspx), [**InkToolbar class**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx), [**InkPresenter class**](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkpresenter.aspx), [**Windows.UI.Input.Inking**](https://msdn.microsoft.com/library/windows/apps/br208524)</span></span>

## <a name="default-inktoolbar"></a><span data-ttu-id="2aa7c-117">Standard-InkToolbar</span><span class="sxs-lookup"><span data-stu-id="2aa7c-117">Default InkToolbar</span></span>

<span data-ttu-id="2aa7c-118">Das [**InkToolbar-Steuerelement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) enthält standardmäßig Schaltflächen zum Zeichnen, Löschen, Hervorheben sowie zum Anzeigen einer Schablone(Lineal oder Winkelmesser).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-118">By default, the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) includes buttons for drawing, erasing, highlighting, and displaying a stencil (ruler or protractor).</span></span> <span data-ttu-id="2aa7c-119">Abhängig vom Feature werden in einem Flyout weitere Einstellungen und Befehle bereitgestellt, beispielsweise für Freihandfarbe, Strichstärke und das Löschen aller Freihandeingaben.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-119">Depending on the feature, other settings and commands, such as ink color, stroke thickness, erase all ink, are provided in a flyout.</span></span>

![InkToolbar](./images/ink/ink-tools-invoked-toolbar-small.png)  
*<span data-ttu-id="2aa7c-121">Standardmäßige Windows Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="2aa7c-121">Default Windows Ink toolbar</span></span>*

<span data-ttu-id="2aa7c-122">Um eine standardmäßige [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) zu einer App für die Freihandeingabe hinzuzufügen, platzieren Sie sie einfach auf derselben Seite wie Ihr [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), und verbinden Sie die beiden Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-122">To add a default [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) to an inking app, just place it on the same page as your [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) and associate the two controls.</span></span>

1. <span data-ttu-id="2aa7c-123">Deklarieren Sie in „MainPage.xaml“ ein Containerobjekt (in diesem Beispiel verwenden wir ein Grid-Steuerelement) für die Freihand-Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-123">In MainPage.xaml, declare a container object (for this example, we use a Grid control) for the inking surface.</span></span>
2. <span data-ttu-id="2aa7c-124">Deklarieren Sie ein InkCanvas-Objekt als untergeordnetes Element des Containers.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-124">Declare an InkCanvas object as a child of the container.</span></span> <span data-ttu-id="2aa7c-125">(Die InkCanvas-Größe wird vom Container geerbt.)</span><span class="sxs-lookup"><span data-stu-id="2aa7c-125">(The InkCanvas size is inherited from the container.)</span></span>
3. <span data-ttu-id="2aa7c-126">Deklarieren Sie eine InkToolbar, und verwenden Sie das TargetInkCanvas-Attribut zum Binden an InkCanvas.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-126">Declare an InkToolbar and use the TargetInkCanvas attribute to bind it to the InkCanvas.</span></span>

> [!NOTE]
> <span data-ttu-id="2aa7c-127">Stellen Sie sicher, dass die InkToolbar nach InkCanvas deklariert wird.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-127">Ensure the InkToolbar is declared after the InkCanvas.</span></span> <span data-ttu-id="2aa7c-128">Andernfalls verhindert die InkCanvas-Überlagerung den Zugriff auf die InkToolbar.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-128">If not, the InkCanvas overlay renders the InkToolbar inaccessible.</span></span>

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

## <a name="basic-customization"></a><span data-ttu-id="2aa7c-129">Einfache Anpassung</span><span class="sxs-lookup"><span data-stu-id="2aa7c-129">Basic customization</span></span>

<span data-ttu-id="2aa7c-130">In diesem Abschnitt behandeln wir einige grundlegende Anpassungsszenarien der Windows Ink-Symbolleiste.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-130">In this section, we cover some basic Windows Ink toolbar customization scenarios.</span></span>

### <a name="specify-location-and-orientation"></a><span data-ttu-id="2aa7c-131">Ort und Ausrichtung angeben</span><span class="sxs-lookup"><span data-stu-id="2aa7c-131">Specify location and orientation</span></span>

<span data-ttu-id="2aa7c-132">Wenn Sie eine Freihandsymbolleiste zu Ihrer App hinzufügen, können Sie Standardstandort und -ausrichtung der Symbolleiste übernehmen oder diese gemäß den Anforderungen Ihrer App oder Benutzer festlegen.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-132">When you add an ink toolbar to your app, you can accept the default location and orientaion of the toolbar or set them as required by your app or user.</span></span>

**<span data-ttu-id="2aa7c-133">XAML</span><span class="sxs-lookup"><span data-stu-id="2aa7c-133">XAML</span></span>**

<span data-ttu-id="2aa7c-134">Geben Sie den Standort und die Ausrichtung der Symbolleiste explizit über die Eigenschaften [VerticalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.VerticalAlignment), [HorizontalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.HorizontalAlignment) und [Orientation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar?branch=rs3.Orientation) an.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-134">Explicitly specify the location and orientation of the toolbar through its [VerticalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.VerticalAlignment), [HorizontalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.HorizontalAlignment), and [Orientation](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar?branch=rs3.Orientation) properties.</span></span>

| <span data-ttu-id="2aa7c-135">Standard</span><span class="sxs-lookup"><span data-stu-id="2aa7c-135">Default</span></span> | <span data-ttu-id="2aa7c-136">Explizit</span><span class="sxs-lookup"><span data-stu-id="2aa7c-136">Explicit</span></span> |
| --- | --- |
| ![Standardstandort und -ausrichtung der Freihandsymbolleiste](./images/ink/location-default-small.png) | ![Explizite Angabe für Standort und Ausrichtung der Freihandsymbolleiste](./images/ink/location-explicit-small.png) |
| *<span data-ttu-id="2aa7c-139">Standardstandort und -ausrichtung der Windows Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="2aa7c-139">Windows Ink toolbar default location and orientation</span></span>* | *<span data-ttu-id="2aa7c-140">Explizite Angabe für Standort und Ausrichtung der Windows Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="2aa7c-140">Windows Ink toolbar explicit location and orientation</span></span>* |

<span data-ttu-id="2aa7c-141">Im Folgenden sehen Sie den Code, mit dem Sie den Standort und die Ausrichtung der Freihandsymbolleiste explizit in XAML festlegen.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-141">Here's the code for explicitly setting the location and orientation of the ink toolbar in XAML.</span></span>
```xaml
<InkToolbar x:Name="inkToolbar" 
    VerticalAlignment="Center" 
    HorizontalAlignment="Right" 
    Orientation="Vertical" 
    TargetInkCanvas="{x:Bind inkCanvas}" />
```

**<span data-ttu-id="2aa7c-142">Initialisierung basierend auf Benutzereinstellungen oder Gerätestatus</span><span class="sxs-lookup"><span data-stu-id="2aa7c-142">Initialize based on user preferences or device state</span></span>**

<span data-ttu-id="2aa7c-143">In einigen Fällen möchten Sie möglicherweise den Standort und die Ausrichtung der Freihandsymbolleiste basierend auf Benutzereinstellungen oder Gerätestatus festlegen.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-143">In some cases, you might want to set the location and orientation of the ink toolbar based on user preference or device state.</span></span> <span data-ttu-id="2aa7c-144">Das folgende Beispiel veranschaulicht, wie Sie den Standort und die Ausrichtung der Freihandsymbolleiste basierend auf den Einstellungen für Rechts- oder Linkshänder festlegen, die über **Einstellungen > Geräte > Stift & Windows Ink > Stift > Schreibhand auswählen** angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-144">The following example demonstrates how to set the location and orientation of the ink toolbar based on the left or right-hand writing preferences specified through **Settings > Devices > Pen & Windows Ink > Pen > Choose which hand you write with**.</span></span>

![Einstellung für die dominante Hand](./images/ink/location-handedness-setting.png)  
*<span data-ttu-id="2aa7c-146">Einstellung für die dominante Hand</span><span class="sxs-lookup"><span data-stu-id="2aa7c-146">Dominant hand setting</span></span>*

<span data-ttu-id="2aa7c-147">Sie können diese Einstellung über die HandPreference-Eigenschaft von Windows.UI.ViewManagement abfragen und [HorizontalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.HorizontalAlignment) basierend auf dem zurückgegebenen Wert festlegen.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-147">You can query this setting through the HandPreference property of Windows.UI.ViewManagement and set the [HorizontalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.HorizontalAlignment) based on the value returned.</span></span> <span data-ttu-id="2aa7c-148">In diesem Beispiel platzieren wir die Symbolleiste auf der linken Seite der App für einen Linkshänder und auf der rechten Seite für einen Rechtshänder.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-148">In this example, we locate the toolbar on the left side of the app for a left-handed person and on the right side for a right-handed person.</span></span>

**<span data-ttu-id="2aa7c-149">Laden Sie dieses Beispiel unter [Beispiel für Standort und Ausrichtung der Freihandsymbolleiste (einfach)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-149">Download this sample from [Ink toolbar location and orientation sample (basic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness.zip)</span></span>**

```csharp
public MainPage()
{
    this.InitializeComponent();

    Windows.UI.ViewManagement.UISettings settings = 
        new Windows.UI.ViewManagement.UISettings();
    HorizontalAlignment alignment = 
        (settings.HandPreference == 
            Windows.UI.ViewManagement.HandPreference.LeftHanded) ? 
            HorizontalAlignment.Left : HorizontalAlignment.Right;
    inkToolbar.HorizontalAlignment = alignment;
}
```

**<span data-ttu-id="2aa7c-150">Dynamische Anpassung an Benutzer oder Gerätestatus</span><span class="sxs-lookup"><span data-stu-id="2aa7c-150">Dynamically adjust to user or device state</span></span>**

<span data-ttu-id="2aa7c-151">Sie können auch eine Bindung verwenden, um nach Aktualisierungen der Benutzeroberfläche basierend auf Benutzereinstellungen, Geräteeinstellungen oder Gerätestatus zu suchen.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-151">You can also use binding to look after UI updates based on changes to user preferences, device settings, or device states.</span></span> <span data-ttu-id="2aa7c-152">Im folgenden Beispiel wird das vorherige Beispiel erweitert und gezeigt, wie Sie die Freihandsymbolleiste basierend auf der Ausrichtung des Geräts mithilfe von Bindung, einem ViewMOdel-Objekt und der [INotifyPropertyChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.data.inotifypropertychanged)-Schnittstelle dynamisch positionieren.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-152">In the following example, we expand on the previous example and show how to dynamically position the ink toolbar based on device orientation using binding, a ViewMOdel object, and the [INotifyPropertyChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.data.inotifypropertychanged) interface.</span></span> 

**<span data-ttu-id="2aa7c-153">Laden Sie dieses Beispiel unter [Beispiel für Standort und Ausrichtung der Freihandsymbolleiste (dynamisch)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness-dynamic.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-153">Download this sample from [Ink toolbar location and orientation sample (dynamic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness-dynamic.zip)</span></span>**

1. <span data-ttu-id="2aa7c-154">Zuerst fügen wir unser ViewModel hinzu.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-154">First, let's add our ViewModel.</span></span>
    1. <span data-ttu-id="2aa7c-155">Fügen Sie Ihrem Projekt einen neuen Ordner hinzu, und nennen Sie ihn **ViewModels**.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-155">Add a new folder to your project and call it **ViewModels**.</span></span>
    1. <span data-ttu-id="2aa7c-156">Fügen Sie eine neue Klasse zum ViewModels-Ordner hinzu (für dieses Beispiel nennen wir sie **InkToolbarSnippetHostViewModel.cs**).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-156">Add a new class to the ViewModels folder (for this example, we called it **InkToolbarSnippetHostViewModel.cs**).</span></span>
        > [!NOTE] 
        > <span data-ttu-id="2aa7c-157">Wir haben das [Singleton-Muster](https://msdn.microsoft.com/library/ff650849.aspx) verwendet, da wir nur ein Objekt dieses Typs für die Lebensdauer der Anwendung benötigen.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-157">We used the [Singleton pattern](https://msdn.microsoft.com/library/ff650849.aspx) as we only need one object of this type for the life of the application</span></span>

    1. <span data-ttu-id="2aa7c-158">Fügen Sie den `using System.ComponentModel`-Namespace zu der Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-158">Add `using System.ComponentModel` namespace to the file.</span></span>
    1. <span data-ttu-id="2aa7c-159">Fügen Sie eine statische Membervariable namens **instance** und eine statische schreibgeschützte Eigenschaft namens **Instance** hinzu.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-159">Add a static member variable called **instance**, and a static read only property named **Instance**.</span></span> <span data-ttu-id="2aa7c-160">Sorgen Sie dafür, dass der Konstruktor privat ist, um sicherzustellen, dass nur über die Instance-Eigenschaft auf diese Klasse zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-160">Make the constructor private to ensure this class can only be accessed via the Instance property.</span></span>   
        > [!NOTE] 
        > <span data-ttu-id="2aa7c-161">Diese Klasse erbt von der [INotifyPropertyChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.data.inotifypropertychanged)-Schnittstelle, die verwendet wird, um Clients, die in der Regel Bindungsclients sind, zu benachrichtigen, dass sich ein Eigenschaftswert geändert hat.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-161">This class inherits from [INotifyPropertyChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.data.inotifypropertychanged) interface, which is used to notify clients, typically binding clients, that a property value has changed.</span></span> <span data-ttu-id="2aa7c-162">Wir verwenden dies, um Änderungen an der Geräteausrichtung zu verarbeiten (dieser Code wird in einem späteren Schritt erweitert und weiter erläutert).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-162">We'll be using this to handle changes to the device orientation (we'll expand this code and explain further in a later step).</span></span>  

        ```csharp
        using System.ComponentModel;

        namespace locationandorientation.ViewModels
        {
            public class InkToolbarSnippetHostViewModel : INotifyPropertyChanged
            {
                private static InkToolbarSnippetHostViewModel instance;
                
                public static InkToolbarSnippetHostViewModel Instance
                {
                    get
                    {
                        if (null == instance)
                        {
                            instance = new InkToolbarSnippetHostViewModel();
                        }
                        return instance;
                    }
                }
            }

            private InkToolbarSnippetHostViewModel() { }
        }
        ```

    1. <span data-ttu-id="2aa7c-163">Fügen Sie zwei boolesche Eigenschaften zur Klasse InkToolbarSnippetHostViewModel hinzu: **LeftHandedLayout** (dieselbe Funktion wie im vorherigen Beispiel reinen XAML-Beispiel) und **PortraitLayout** (Ausrichtung des Geräts).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-163">Add two bool properties to the InkToolbarSnippetHostViewModel class: **LeftHandedLayout** (same functionality as the previous XAML-only example) and **PortraitLayout** (orientation of the device).</span></span>
        >[!NOTE] 
        > <span data-ttu-id="2aa7c-164">Die Eigenschaft PortraitLayout ist einstellbar und enthält die Definition für das Ereignis [PropertyChanged](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-164">The PortraitLayout property is settable and includes the defintion for the [PropertyChanged](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) event.</span></span>

        ```csharp
        public bool LeftHandedLayout
        {
            get
            {
                bool leftHandedLayout = false;
                Windows.UI.ViewManagement.UISettings settings =
                    new Windows.UI.ViewManagement.UISettings();
                leftHandedLayout = (settings.HandPreference ==
                    Windows.UI.ViewManagement.HandPreference.LeftHanded);
                return leftHandedLayout;
            }
        }

        public bool portraitLayout = false;
        public bool PortraitLayout
        {
            get
            {
                Windows.UI.ViewManagement.ApplicationViewOrientation winOrientation = 
                    Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().Orientation;
                portraitLayout = 
                    (winOrientation == 
                        Windows.UI.ViewManagement.ApplicationViewOrientation.Portrait);
                return portraitLayout;
            }
            set
            {
                if (value.Equals(portraitLayout)) return;
                portraitLayout = value;
                PropertyChanged?.Invoke(this, new PropertyChangedEventArgs("PortraitLayout"));
            }
        }
        ```

1. <span data-ttu-id="2aa7c-165">Nun fügen wir unserem Projekt verschiedene Klassen des Konverters hinzu.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-165">Now, let's add a couple of converter classes to our project.</span></span> <span data-ttu-id="2aa7c-166">Jede Klasse enthält ein Convert-Objekt, das einen Ausrichtungswert zurückgibt (entweder [HorizontalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.horizontalalignment) oder [VerticalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.verticalalignment)).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-166">Each class contains a Convert object that returns an alignment value (either [HorizontalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.horizontalalignment) or [VerticalAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.verticalalignment)).</span></span>
    1. <span data-ttu-id="2aa7c-167">Fügen Sie Ihrem Projekt einen neuen Ordner hinzu, und nennen Sie ihn **Converters**.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-167">Add a new folder to your project and call it **Converters**.</span></span>
    1. <span data-ttu-id="2aa7c-168">Fügen Sie zwei neue Klassen zum Converters-Ordner hinzu (für dieses Beispiel nennen wir diese **HorizontalAlignmentFromHandednessConverter.cs** und **VerticalAlignmentFromAppViewConverter.cs**).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-168">Add two new classes to the Converters folder (for this example, we call them **HorizontalAlignmentFromHandednessConverter.cs** and **VerticalAlignmentFromAppViewConverter.cs**).</span></span>
    1. <span data-ttu-id="2aa7c-169">Fügen Sie die Namespaces `using Windows.UI.Xaml` und `using Windows.UI.Xaml.Data` zu jeder Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-169">Add `using Windows.UI.Xaml` and `using Windows.UI.Xaml.Data` namespaces to each file.</span></span>
    1. <span data-ttu-id="2aa7c-170">Ändern Sie jede Klasse in `public`, und geben Sie an, dass damit die [IValueConverter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.data.ivalueconverter)-Schnittstelle implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-170">Change each class to `public` and specify that it implements the [IValueConverter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.data.ivalueconverter) interface.</span></span>
    1. <span data-ttu-id="2aa7c-171">Fügen Sie die Methoden [Convert](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.data.ivalueconverter.convert) und [ConvertBack](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.data.ivalueconverter.convertback) zu jeder Datei hinzu, wie hier gezeigt (die ConvertBack-Methode wird nicht implementiert).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-171">Add the [Convert](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.data.ivalueconverter.convert) and [ConvertBack](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.data.ivalueconverter.convertback) methods to each file, as shown here (we leave the ConvertBack method unimplemented).</span></span>
        - <span data-ttu-id="2aa7c-172">HorizontalAlignmentFromHandednessConverter positioniert die Freihandsymbolleiste auf der rechten Seite der App für Rechtshänder und auf der linken Seite der App für Linkshänder.</span><span class="sxs-lookup"><span data-stu-id="2aa7c-172">HorizontalAlignmentFromHandednessConverter positions the ink toolbar to the right side of the app for right-handed users and to the left side of the app for left-handed users.</span></span>
        ```csharp
        using System;

        using Windows.UI.Xaml;
        using Windows.UI.Xaml.Data;

        namespace locationandorientation.Converters
        {
            public class HorizontalAlignmentFromHandednessConverter : IValueConverter
            {
                public object Convert(object value, Type targetType,
                    object parameter, string language)
                {
                    bool leftHanded = (bool)value;
                    HorizontalAlignment alignment = HorizontalAlignment.Right;
                    if (leftHanded)
                    {
                        alignment = HorizontalAlignment.Left;
                    }
                    return alignment;
                }

                public object ConvertBack(object value, Type targetType,
                    object parameter, string language)
                {
                    throw new NotImplementedException();
                }
            }
        }
        ```

        - <span data-ttu-id="2aa7c-173">VerticalAlignmentFromAppViewConverter positioniert die Freihandsymbolleiste in der Mitte der App für das Hochformat und an den Anfang der App für das Querformat (auch wenn dies die Verwendbarkeit verbessern soll, ist es nur eine zufällige Wahl für Demonstrationszwecke).</span><span class="sxs-lookup"><span data-stu-id="2aa7c-173">VerticalAlignmentFromAppViewConverter positions the ink toolbar to the center of the app for portrait orientation and to the top of the app for landscape orientation (while intended to improve usability, this is just an arbitrary choice for demonstration purposes).</span></span>
        ````csharp
        using System;

        using Windows.UI.Xaml;
        using Windows.UI.Xaml.Data;

        namespace locationandorientation.Converters
        {
            public class VerticalAlignmentFromAppViewConverter : IValueConverter
            {
                public object Convert(object value, Type targetType,
                    object parameter, string language)
                {
                    bool portraitOrientation = (bool)value;
                    VerticalAlignment alignment = VerticalAlignment.Top;
                    if (portraitOrientation)
                    {
                        alignment = VerticalAlignment.Center;
                    }
                    return alignment;
                }

                public object ConvertBack(object value, Type targetType,
                    object parameter, string language)
                {
                    throw new NotImplementedException();
                }
            }
        }
        ```

1. Now, open the MainPage.xaml.cs file.
    1. Add `using using locationandorientation.ViewModels` to the list of namespaces to associate our ViewModel.
    1. Add `using Windows.UI.ViewManagement` to the list of namespaces to enable listening for changes to the device orientation.
    1. Add the [WindowSizeChangedEventHandler](https://docs.microsoft.com/uwp/api/windows.ui.xaml.windowsizechangedeventhandler) code.
    1. Set the [DataContext](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.FrameworkElement.DataContext) for the view to the singleton instance of the InkToolbarSnippetHostViewModel class. 
    ```csharp
    using Windows.UI.Xaml;
    using Windows.UI.Xaml.Controls;

    using locationandorientation.ViewModels;
    using Windows.UI.ViewManagement;

    namespace locationandorientation
    {
        public sealed partial class MainPage : Page
        {
            public MainPage()
            {
                this.InitializeComponent();

                Window.Current.SizeChanged += (sender, args) =>
                {
                    ApplicationView currentView = ApplicationView.GetForCurrentView();

                    if (currentView.Orientation == ApplicationViewOrientation.Landscape)
                    {
                        InkToolbarSnippetHostViewModel.Instance.PortraitLayout = false;
                    }
                    else if (currentView.Orientation == ApplicationViewOrientation.Portrait)
                    {
                        InkToolbarSnippetHostViewModel.Instance.PortraitLayout = true;
                    }
                };

                DataContext = InkToolbarSnippetHostViewModel.Instance;
            }
        }
    }
    ```

1. Next, open the MainPage.xaml file.
    1. Add `xmlns:converters="using:locationandorientation.Converters"` to the `Page` element for binding to our converters.
        ```xaml
        <Page
        x:Class="locationandorientation.MainPage"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:locationandorientation"
        xmlns:converters="using:locationandorientation.Converters"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">
        ```

    1. Add a `PageResources` element and specify references to our converters.
        ```xaml
        <Page.Resources>
            <converters:HorizontalAlignmentFromHandednessConverter x:Key="HorizontalAlignmentConverter"/>
            <converters:VerticalAlignmentFromAppViewConverter x:Key="VerticalAlignmentConverter"/>
        </Page.Resources>
        ```

    1. Add the InkCanvas and InkToolbar elements and bind the VerticalAlignment and HorizontalAlignment properties of the InkToolbar.
        ```xaml
        <InkCanvas x:Name="inkCanvas" />
        <InkToolbar x:Name="inkToolbar" 
                    VerticalAlignment="{Binding PortraitLayout, Converter={StaticResource VerticalAlignmentConverter} }" 
                    HorizontalAlignment="{Binding LeftHandedLayout, Converter={StaticResource HorizontalAlignmentConverter} }" 
                    Orientation="Vertical" 
                    TargetInkCanvas="{x:Bind inkCanvas}" />
        ```

1. Return to the InkToolbarSnippetHostViewModel.cs file to add our `PortraitLayout` and `LeftHandedLayout` bool properties to the `InkToolbarSnippetHostViewModel` class, along with support for rebinding `PortraitLayout` when that property value changes. 
    ```csharp
    public bool LeftHandedLayout
    {
        get
        {
            bool leftHandedLayout = false;
            Windows.UI.ViewManagement.UISettings settings =
                new Windows.UI.ViewManagement.UISettings();
            leftHandedLayout = (settings.HandPreference ==
                Windows.UI.ViewManagement.HandPreference.LeftHanded);
            return leftHandedLayout;
        }
    }

    public bool portraitLayout = false;
    public bool PortraitLayout
    {
        get
        {
            Windows.UI.ViewManagement.ApplicationViewOrientation winOrientation = 
                Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().Orientation;
            portraitLayout = 
                (winOrientation == 
                    Windows.UI.ViewManagement.ApplicationViewOrientation.Portrait);
            return portraitLayout;
        }
        set
        {
            if (value.Equals(portraitLayout)) return;
            portraitLayout = value;
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs("PortraitLayout"));
        }
    }

    #region INotifyPropertyChanged Members

    public event PropertyChangedEventHandler PropertyChanged;

    protected void OnPropertyChanged(string property)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(property));
    }

    #endregion
    ```

You should now have an inking app that adapts to both the dominant hand preference of the user and dynamically responds to the orientation of the user's device.

### Specify the selected button  
![Pencil button selected at initialization](./images/ink/ink-tools-default-toolbar.png)  
*Windows Ink toolbar with pencil button selected at initialization*

By default, the first (or leftmost) button is selected when your app is launched and the toolbar is initialized. In the default Windows Ink toolbar, this is the ballpoint pen button.

Because the framework defines the order of the built-in buttons, the first button might not be the pen or tool you want to activate by default.

You can override this default behavior and specify the selected button on the toolbar.

For this example, we initialize the default toolbar with the pencil button selected and the pencil activated (instead of the ballpoint pen).

1. Use the XAML declaration for the InkCanvas and InkToolbar from the previous example.
2. In code-behind, set up a handler for the [Loaded](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loaded.aspx) event of the [InkToolbar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) object.

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

3. In the handler for the [Loaded](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loaded.aspx) event:
    1. Get a reference to the built-in [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx).

    Passing an [InkToolbarTool.Pencil](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbartool.aspx) object in the [GetToolButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.gettoolbutton.aspx) method returns an [InkToolbarToolButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbartoolbutton.aspx) object for the [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx).

    2. Set [ActiveTool](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.activetool.aspx) to the object returned in the previous step.

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

### Specify the built-in buttons

![Specific buttons included at initialization](./images/ink/ink-tools-specific.png)  
*Specific buttons included at initialization*

As mentioned, the Windows Ink toolbar includes a collection of default, built-in buttons. These buttons are displayed in the following order (from left to right):

- [InkToolbarBallpointPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarballpointpenbutton.aspx)
- [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx)
- [InkToolbarHighlighterButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarhighlighterbutton.aspx)
- [InkToolbarEraserButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbareraserbutton.aspx)
- [InkToolbarRulerButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarrulerbutton.aspx)

For this example, we initialize the toolbar with only the built-in ballpoint pen, pencil, and eraser buttons.

You can do this using either XAML or code-behind.

**XAML**

Modify the XAML declaration for the InkCanvas and InkToolbar from the first example.
- Add an [InitialControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.initialcontrols.aspx) attribute and set its value to "[None](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarinitialcontrols.aspx)". This clears the default collection of built-in buttons.
- Add the specific InkToolbar buttons required by your app. Here, we add [InkToolbarBallpointPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarballpointpenbutton.aspx), [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx), and [InkToolbarEraserButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbareraserbutton.aspx) only.
> [!NOTE]
> Buttons are added to the toolbar in the order defined by the framework, not the order specified here.

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

**Code-behind**
1. Use the XAML declaration for the InkCanvas and InkToolbar from the first example.

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

2. In code-behind, set up a handler for the [Loading](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.loading.aspx) event of the [InkToolbar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) object.

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

3. Set [InitialControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.initialcontrols.aspx) to "[None](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarinitialcontrols.aspx)".
4. Create object references for the buttons required by your app. Here, we add [InkToolbarBallpointPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarballpointpenbutton.aspx), [InkToolbarPencilButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpencilbutton.aspx), and [InkToolbarEraserButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbareraserbutton.aspx) only.
  > [!NOTE]
  > Buttons are added to the toolbar in the order defined by the framework, not the order specified here.

5. [Add](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyobjectcollection.add.aspx) the buttons to the InkToolbar.

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

## Custom buttons and inking features

You can customize and extend the collection of buttons (and associated inking features) that are provided through the InkToolbar.

The InkToolbar consists of two distinct groups of button types:

1. A group of "tool" buttons containing the built-in drawing, erasing, and highlighting buttons. Custom pens and tools are added here.
> **Note**&nbsp;&nbsp;Feature selection is mutually exclusive.

2. A group of "toggle" buttons containing the built-in ruler button. Custom toggles are added here.
> **Note**&nbsp;&nbsp;Features are not mutually exclusive and can be used concurrently with other active tools.

Depending on your application and the inking functionality required, you can add any of the following buttons (bound to your custom ink features) to the InkToolbar:

- Custom pen – a pen for which the ink color palette and pen tip properties, such as shape, rotation, and size, are defined by the host app.
- Custom tool – a non-pen tool, defined by the host app.
- Custom toggle – Sets the state of an app-defined feature to on or off. When turned on, the feature works in conjunction with the active tool.

> **Note**&nbsp;&nbsp;You cannot change the display order of the built-in buttons. The default display order is: Ballpoint pen, pencil, highlighter, eraser, and ruler. Custom pens are appended to the last default pen, custom tool buttons are added between the last pen button and the eraser button and custom toggle buttons are added after the ruler button. (Custom buttons are added in the order they are specified.)

### Custom pen

You can create a custom pen (activated through a custom pen button) where you define the ink color palette and pen tip properties, such as shape, rotation, and size.

![Custom calligraphic pen button](./images/ink/ink-tools-custompen.png)  
*Custom calligraphic pen button*

For this example, we define a custom pen with a broad tip that enables basic calligraphic ink strokes. We also customize the collection of brushes in the palette displayed on the button flyout.

**Code-behind**

First, we define our custom pen and specify the drawing attributes in code-behind. We reference this custom pen from XAML later.

1. Right click the project in Solution Explorer and select Add -> New item.
2. Under Visual C# -> Code, add a new Class file and call it CalligraphicPen.cs.
3. In Calligraphic.cs, replace the default using block with the following:
```csharp
using System.Numerics;
using Windows.UI;
using Windows.UI.Input.Inking;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Media;
```

4. Specify that the CalligraphicPen class is derived from [InkToolbarCustomPen](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompen.aspx).
```csharp
class CalligraphicPen : InkToolbarCustomPen
{
}
```

5. Override  [CreateInkDrawingAttributesCore](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompen.createinkdrawingattributescore.aspx)  to specify your own brush and stroke size.
```csharp
class CalligraphicPen : InkToolbarCustomPen
{
    protected override InkDrawingAttributes
      CreateInkDrawingAttributesCore(Brush brush, double strokeWidth)
    {
    }
}
```

6. Create an [InkDrawingAttributes](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.aspx) object and set the [pen tip shape](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.pentip.aspx), [tip rotation](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.pentiptransform.aspx), [stroke size](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.size.aspx), and [ink color](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.inking.inkdrawingattributes.color.aspx).
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

**XAML**

Next, we add the necessary references to the custom pen in MainPage.xaml.

1. We declare a local page resource dictionary that creates a reference to the custom pen (`CalligraphicPen`) defined in CalligraphicPen.cs, and a [brush collection](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Media.BrushCollection.aspx) supported by the custom pen (`CalligraphicPenPalette`).
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

2. We then add an InkToolbar with a child [InkToolbarCustomPenButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarcustompenbutton.aspx) element.

  The custom pen button includes the two static resource references declared in the page resources: `CalligraphicPen` and `CalligraphicPenPalette`.

  We also specify the range for the stroke size slider ([MinStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.minstrokewidth.aspx), [MaxStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.maxstrokewidth.aspx), and [SelectedStrokeWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.selectedstrokewidthproperty.aspx)), the selected brush ([SelectedBrushIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbarpenbutton.selectedbrushindex.aspx)), and the icon for the custom pen button ([SymbolIcon](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.symbolicon.aspx)).
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

### Custom toggle

You can create a custom toggle (activated through a custom toggle button) to set the state of an app-defined feature to on or off. When turned on, the feature works in conjunction with the active tool.

In this example, we define a custom toggle button that enables inking with touch input (by default, touch inking is not enabled).

> [!NOTE]  
> If you need to support inking with touch, we recommended that you enable it using a CustomToggleButton, with the icon and tooltip specified in this example.

Typically, touch input is used for direct manipulation of an object or the app UI. To demonstrate the differences in behavior when touch inking is enabled, we place the InkCanvas within a ScrollViewer container and set the dimensions of the ScrollViewer to be smaller than the InkCanvas. 

When the app starts, only pen inking is supported and touch is used to pan or zoom the inking surface. When touch inking is enabled, the inking surface cannot be panned or zoomed through touch input.

> [!NOTE]
> See [Inking controls](../controls-and-patterns/inking-controls.md) for both [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkCanvas) and [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbar) UX guidelines. The following recommendations are relevant to this example:
> - The [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbar), and inking in general, is best experienced through an active pen. However, inking with mouse and touch can be supported if required by your app. 
> - If supporting inking with touch input, we recommend using the "ED5F" icon from the "Segoe MLD2 Assets" font for the toggle button, with a "Touch writing" tooltip. 

**XAML**

1. First, we declare an [**InkToolbarCustomToggleButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToggleButton) element (toggleButton) with a Click event listener that specifies the event handler (Toggle_Custom).

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

**Code-behind**

2. In the previous snippet, we declared a Click event listener and handler (Toggle_Custom) on the custom toggle button for touch inking (toggleButton). This handler simply toggles support for CoreInputDeviceTypes.Touch through the InputDeviceTypes property of the InkPresenter.

   We also specified an icon for the button using the SymbolIcon element and the {x:Bind} markup extension that binds it to a field defined in the code-behind file (TouchWritingIcon).

   The following snippet includes both the Click event handler and the definition of TouchWritingIcon.

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

### Custom tool

You can create a custom tool button to invoke a non-pen tool that is defined by your app.

By default, an [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) processes all input as either an ink stroke or an erase stroke. This includes input modified by a secondary hardware affordance such as a pen barrel button, a right mouse button, or similar. However, [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) can be configured to leave specific input unprocessed, which can then be passed through to your app for custom processing.

In this example, we define a custom tool button that, when selected, causes subsequent strokes to be processed and rendered as a selection lasso (dashed line) instead of ink. All ink strokes within the bounds of the selection area are set to [**Selected**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkStroke.Selected).

> [!NOTE]
> See Inking controls for both InkCanvas and InkToolbar UX guidelines. The following recommendation is relevant to this example:
> - If providing stroke selection, we recommend using the "EF20" icon from the "Segoe MLD2 Assets" font for the tool button, with a "Selection tool" tooltip. 
 
**XAML**

1. First, we declare an [**InkToolbarCustomToolButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToolButton) element (customToolButton) with a Click event listener that specifies the event handler (customToolButton_Click) where stroke selection is configured. (We've also added a set of buttons for copying, cutting, and pasting the stroke selection.)

2. We also add a Canvas element for drawing our selection stroke. Using a separate layer to draw the selection stroke ensures the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkCanvas) and its content remain untouched. 

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

**Code-behind**

2. We then handle the Click event for the [**InkToolbarCustomToolButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbarCustomToolButton) in the MainPage.xaml.cs code-behind file.

   This handler configures the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.Inking.InkPresenter) to pass unprocessed input through to the app. 

   For a more detailed step through of this code:  See the Pass-through input for advanced processing section of [Pen interactions and Windows Ink in UWP apps](pen-and-stylus-interactions.md).

   We also specified an icon for the button using the SymbolIcon element and the {x:Bind} markup extension that binds it to a field defined in the code-behind file (SelectIcon).

   The following snippet includes both the Click event handler and the definition of SelectIcon.

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



### Custom ink rendering

By default, ink input is processed on a low-latency background thread and rendered "wet" as it is drawn. When the stroke is completed (pen or finger lifted, or mouse button released), the stroke is processed on the UI thread and rendered "dry" to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) layer (above the application content and replacing the wet ink).

The ink platform enables you to override this behavior and completely customize the inking experience by custom drying the ink input.

For more info on custom drying, see [Pen interactions and Windows Ink in UWP apps](https://msdn.microsoft.com/windows/uwp/input/pen-and-stylus-interactions#custom-ink-rendering).

> [!NOTE]
> Custom drying and the [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)  
> If your app overrides the default ink rendering behavior of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) with a custom drying implementation, the rendered ink strokes are no longer available to the InkToolbar and the built-in erase commands of the InkToolbar do not work as expected. To provide erase functionality, you must handle all pointer events, perform hit-testing on each stroke, and override the built-in "Erase all ink" command.

## Related articles

* [Pen and stylus interactions](pen-and-stylus-interactions.md)

**Topic samples**
* [Ink toolbar location and orientation sample (basic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness.zip)
* [Ink toolbar location and orientation sample (dynamic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness-dynamic.zip)

**Other samples**
* [Simple ink sample (C#/C++)](http://go.microsoft.com/fwlink/p/?LinkID=620312)
* [Complex ink sample (C++)](http://go.microsoft.com/fwlink/p/?LinkID=620314)
* [Ink sample (JavaScript)](http://go.microsoft.com/fwlink/p/?LinkID=620308)
* [Get Started Tutorial: Support ink in your UWP app](https://aka.ms/appsample-ink)
* [Coloring book sample](https://aka.ms/cpubsample-coloringbook)
* [Family notes sample](https://aka.ms/cpubsample-familynotessample)

