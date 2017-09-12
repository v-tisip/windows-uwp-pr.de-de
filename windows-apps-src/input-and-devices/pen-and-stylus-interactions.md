---
author: Karl-Bridge-Microsoft
Description: "Erstellen Sie Apps für die Universelle Windows-Plattform (UWP-Apps), die benutzerdefinierte Interaktionen über Stifte und Tabletstifte unterstützen, einschließlich Freihandeingabe für das Schreiben und Zeichnen wie auf Papier."
title: Stiftinteraktionen und Windows Ink in UWP-Apps
ms.assetid: 3DA4F2D2-5405-42A1-9ED9-3A87BCD84C43
label: Pen interactions and Windows Ink in UWP apps
template: detail.hbs
keywords: Windows Ink, Windows-Freihandeingabe, DirectInk, InkPresenter, InkCanvas, Handschrifterkennung, Benutzerinteraktion, Eingabe
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: af89a515e7d59c735bb4499c3602eef7570fe03a
ms.sourcegitcommit: 11664964e548a2af30d6e176c515cdbf330934ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2017
---
# <a name="pen-interactions-and-windows-ink-in-uwp-apps"></a><span data-ttu-id="32cf7-104">Stiftinteraktionen und Windows Ink in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="32cf7-104">Pen interactions and Windows Ink in UWP apps</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<!--
![touchpad](images/input-patterns/input-pen.jpg)
-->

<!--
![Surface Pen](images/ink/hero2-small.png)  
*Surface Studio with Surface Pen* (available for purchase at the [Microsoft Store](https://aka.ms/purchasesurfacepen)).
-->

![Surface-Stift](images/ink/hero-small.png)  
<span data-ttu-id="32cf7-106">*Surface-Stift* (zum Kauf im [Microsoft Store](https://aka.ms/purchasesurfacepen) verfügbar).</span><span class="sxs-lookup"><span data-stu-id="32cf7-106">*Surface Pen* (available for purchase at the [Microsoft Store](https://aka.ms/purchasesurfacepen)).</span></span>

## <a name="overview"></a><span data-ttu-id="32cf7-107">Übersicht</span><span class="sxs-lookup"><span data-stu-id="32cf7-107">Overview</span></span>

<span data-ttu-id="32cf7-108">Optimieren Sie Ihre App für die Universelle Windows-Plattform (UWP-App) für Stifteingaben, um sowohl Standardfunktionalität für [**Zeigergeräte**](https://msdn.microsoft.com/library/windows/apps/br225633) als auch optimale Windows Ink-Funktionalität für Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-108">Optimize your Universal Windows Platform (UWP) app for pen input to provide both standard [**pointer device**](https://msdn.microsoft.com/library/windows/apps/br225633) functionality and the best Windows Ink experience for your users.</span></span>

> [!NOTE]
> <span data-ttu-id="32cf7-109">Der Schwerpunkt dieses Themas liegt auf der Windows Ink-Plattform.</span><span class="sxs-lookup"><span data-stu-id="32cf7-109">This topic focuses on the Windows Ink platform.</span></span> <span data-ttu-id="32cf7-110">Informationen zur allgemeinen Behandlung von Zeigereingaben (ähnlich Maus-, Touch- und Touchpadeingaben) finden Sie unter [Behandeln von Zeigereingaben](handle-pointer-input.md).</span><span class="sxs-lookup"><span data-stu-id="32cf7-110">For general pointer input handling (similar to mouse, touch, and touchpad), see [Handle pointer input](handle-pointer-input.md).</span></span>

| <span data-ttu-id="32cf7-111">Videos</span><span class="sxs-lookup"><span data-stu-id="32cf7-111">Videos</span></span> |   |
| --- | --- |
| <iframe src="https://channel9.msdn.com/Blogs/One-Dev-Minute/Using-Ink-in-Your-UWP-App/player" width="300" height="200" allowFullScreen frameBorder="0"></iframe> | <iframe src="https://channel9.msdn.com/Events/Ignite/2016/BRK2060/player" width="300" height="200" allowFullScreen frameBorder="0"></iframe> |
| *<span data-ttu-id="32cf7-112">Verwenden von Ink in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="32cf7-112">Using ink in your UWP app</span></span>* | *<span data-ttu-id="32cf7-113">Verwenden von Windows Pen und Ink zum Erstellen von stärker interaktiven Unternehmens-Apps</span><span class="sxs-lookup"><span data-stu-id="32cf7-113">Use Windows Pen and Ink to build more engaging enterprise apps</span></span>* |

<span data-ttu-id="32cf7-114">In Verbindung mit einem Zeichengerät bietet die Windows Ink-Plattform eine natürliche Möglichkeit, digitale handschriftliche Notizen, Zeichnungen und Anmerkungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-114">The Windows Ink platform, together with a pen device, provides a natural way to create digital handwritten notes, drawings, and annotations.</span></span> <span data-ttu-id="32cf7-115">Sie können auf der Plattform Freihanddaten aus einem Eingabedigitalisierungsgerät erfassen, Freihanddaten generieren, verwalten und als letzte Striche auf dem Ausgabegerät rendern sowie über die Schrifterkennung in Text umwandeln.</span><span class="sxs-lookup"><span data-stu-id="32cf7-115">The platform supports capturing digitizer input as ink data, generating ink data, managing ink data, rendering ink data as ink strokes on the output device, and converting ink to text through handwriting recognition.</span></span>

<span data-ttu-id="32cf7-116">Ihre App kann nicht nur die grundlegende Position und Bewegung des Stifts aufzeichnen, während der Benutzer schreibt oder zeichnet, sondern auch den variierenden Druck während des gesamten Strichs nachverfolgen und erfassen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-116">In addition to capturing the basic position and movement of the pen as the user writes or draws, your app can also track and collect the varying amounts of pressure used throughout a stroke.</span></span> <span data-ttu-id="32cf7-117">Mit diesen Informationen, zusammen mit Einstellungen für Form und Größe der Stiftspitze, Drehung, Freihandfarbe und Zweck (einfache Freihandeingabe, Löschen, Hervorheben und Auswählen), können Sie dem Benutzer ermöglichen, auf ähnliche Weise wie mit einem Stift, Bleistift oder Pinsel auf Papier zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="32cf7-117">This information, along with settings for pen tip shape, size, and rotation, ink color, and purpose (plain ink, erasing, highlighting, and selecting), enables you to provide user experiences that closely resemble writing or drawing on paper with a pen, pencil, or brush.</span></span>

> [!NOTE]
> <span data-ttu-id="32cf7-118">Ihre App kann auch Freihandeingaben von anderen zeigerbasierten Geräten, z.B. Touchdigitalisierungs- und Mausgeräte, unterstützen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-118">Your app can also support ink input from other pointer-based devices, including touch digitizers and mouse devices.</span></span> 

<span data-ttu-id="32cf7-119">Die Freihandplattform ist sehr flexibel.</span><span class="sxs-lookup"><span data-stu-id="32cf7-119">The ink platform is very flexible.</span></span> <span data-ttu-id="32cf7-120">Je nach Ihren Anforderungen unterstützt sie verschiedene Funktionalitätsgrade.</span><span class="sxs-lookup"><span data-stu-id="32cf7-120">It is designed to support various levels of functionality, depending on your requirements.</span></span>

<span data-ttu-id="32cf7-121">Richtlinien für die Benutzeroberfläche von WindowsInk finden Sie unter [Inking controls](../controls-and-patterns/inking-controls.md).</span><span class="sxs-lookup"><span data-stu-id="32cf7-121">For Windows Ink UX guidelines, see [Inking controls](../controls-and-patterns/inking-controls.md).</span></span>

## <a name="components-of-the-windows-ink-platform"></a><span data-ttu-id="32cf7-122">Komponenten der WindowsInk-Plattform</span><span class="sxs-lookup"><span data-stu-id="32cf7-122">Components of the Windows Ink platform</span></span>

| <span data-ttu-id="32cf7-123">Komponente</span><span class="sxs-lookup"><span data-stu-id="32cf7-123">Component</span></span> | <span data-ttu-id="32cf7-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="32cf7-124">Description</span></span> |
| --- | --- |
| [**<span data-ttu-id="32cf7-125">InkCanvas</span><span class="sxs-lookup"><span data-stu-id="32cf7-125">InkCanvas</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn858535) | <span data-ttu-id="32cf7-126">Ein XAML-UI-Plattformsteuerelement, das standardmäßig alle Eingaben von einem Stift als Freihandstriche oder Löschen von Freihandstrichen empfängt und anzeigt.</span><span class="sxs-lookup"><span data-stu-id="32cf7-126">A XAML UI platform control that, by default, receives and displays all input from a pen as either an ink stroke or an erase stroke.</span></span><br/><span data-ttu-id="32cf7-127">Weitere Informationen zur Verwendung von InkCanvas finden Sie unter [Erkennen von Windows Ink-Strichen als Text](convert-ink-to-text.md) und [Speichern und Abrufen der Daten von Windows Ink-Strichen](save-and-load-ink.md).</span><span class="sxs-lookup"><span data-stu-id="32cf7-127">For more information about how to use the InkCanvas, see [Recognize Windows Ink strokes as text](convert-ink-to-text.md) and [Store and retrieve Windows Ink stroke data](save-and-load-ink.md).</span></span> |
| [**<span data-ttu-id="32cf7-128">InkPresenter</span><span class="sxs-lookup"><span data-stu-id="32cf7-128">InkPresenter</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn922011) | <span data-ttu-id="32cf7-129">Ein CodeBehind-Objekt, das zusammen mit einem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement instanziiert wird (über die [**InkCanvas.InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Eigenschaft verfügbar gemacht).</span><span class="sxs-lookup"><span data-stu-id="32cf7-129">A code-behind object, instantiated along with an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control (exposed through the [**InkCanvas.InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) property).</span></span> <span data-ttu-id="32cf7-130">Dieses Objekt stellt alle Standardfreihandfunktionen bereit, die vom **InkCanvas**-Steuerelement zur Verfügung gestellt werden, sowie einen umfassenden Satz von APIs für zusätzliche Anpassung und Personalisierung.</span><span class="sxs-lookup"><span data-stu-id="32cf7-130">This object provides all default inking functionality exposed by the **InkCanvas**, along with a comprehensive set of APIs for additional customization and personalization.</span></span><br/><span data-ttu-id="32cf7-131">Weitere Informationen zur Verwendung von InkPresenter finden Sie unter [Erkennen von Windows Ink-Strichen als Text](convert-ink-to-text.md) und [Speichern und Abrufen der Daten von Windows Ink-Strichen](save-and-load-ink.md).</span><span class="sxs-lookup"><span data-stu-id="32cf7-131">For more information about how to use the InkPresenter, see [Recognize Windows Ink strokes as text](convert-ink-to-text.md) and [Store and retrieve Windows Ink stroke data](save-and-load-ink.md).</span></span> |
| [**<span data-ttu-id="32cf7-132">InkToolbar</span><span class="sxs-lookup"><span data-stu-id="32cf7-132">InkToolbar</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) | <span data-ttu-id="32cf7-133">Ein XAML-UI-Plattformsteuerelement enthält eine anpassbare und erweiterbare Sammlung von Schaltflächen, die Features für Freihandeingaben in einem verknüpften [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)-Steuerelement aktivieren.</span><span class="sxs-lookup"><span data-stu-id="32cf7-133">A XAML UI platform control containing a customizable and extensible collection of buttons that activate ink-related features in an associated [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas).</span></span><br/><span data-ttu-id="32cf7-134">Weitere Informationen zur Verwendung von InkToolbar finden Sie unter [Add an InkToolbar to a Universal Windows Platform (UWP) inking app](ink-toolbar.md).</span><span class="sxs-lookup"><span data-stu-id="32cf7-134">For more information about how to use the InkToolbar, see [Add an InkToolbar to a Universal Windows Platform (UWP) inking app](ink-toolbar.md).</span></span> |
| [**<span data-ttu-id="32cf7-135">IInkD2DRenderer</span><span class="sxs-lookup"><span data-stu-id="32cf7-135">IInkD2DRenderer</span></span>**](https://msdn.microsoft.com/library/mt147263) | <span data-ttu-id="32cf7-136">Ermöglicht das Rendern von Freihandstrichen im angegebenen Direct2D-Gerätekontext einer universellen Windows-App statt im standardmäßigen [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="32cf7-136">Enables the rendering of ink strokes onto the designated Direct2D device context of a Universal Windows app, instead of the default [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span> <span data-ttu-id="32cf7-137">Dies ermöglicht die umfassende Anpassung der Freihandfunktionen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-137">This enables full customization of the inking experience.</span></span><br/><span data-ttu-id="32cf7-138">Weitere Informationen finden Sie in diesem [komplexen Freihandbeispiel](http://go.microsoft.com/fwlink/p/?LinkID=620314).</span><span class="sxs-lookup"><span data-stu-id="32cf7-138">For more information, see the [Complex ink sample](http://go.microsoft.com/fwlink/p/?LinkID=620314).</span></span> |

## <a name="basic-inking-with-inkcanvas"></a><span data-ttu-id="32cf7-139">Einfaches Freihandzeichnen mit „InkCanvas“</span><span class="sxs-lookup"><span data-stu-id="32cf7-139">Basic inking with InkCanvas</span></span>

<span data-ttu-id="32cf7-140">Um einfaches Freihandzeichen hinzuzufügen, platzieren Sie einfach ein [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-UWP-Steuerelement auf der entsprechenden Seite in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="32cf7-140">To add basic inking functionality, just place an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) UWP platform control on the appropriate page in your app.</span></span>

<span data-ttu-id="32cf7-141">Das [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement unterstützt standardmäßig nur Freihandeingaben mit einem Stift.</span><span class="sxs-lookup"><span data-stu-id="32cf7-141">By default, the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) supports ink input only from a pen.</span></span> <span data-ttu-id="32cf7-142">Die Eingabe wird entweder als Strich mit den Standardeinstellungen für Farbe und Stärke gerendert (ein schwarzer Kugelschreiber mit einer Stärke von 2Pixeln) oder als Strichradierer behandelt (wenn die Eingabe von einer mit einer Löschschaltfläche geänderten Radiergummi- oder Stiftspitze stammt).</span><span class="sxs-lookup"><span data-stu-id="32cf7-142">The input is either rendered as an ink stroke using default settings for color and thickness (a black ballpoint pen with a thickness of 2 pixels), or treated as a stroke eraser (when input is from an eraser tip or the pen tip modified with an erase button).</span></span>

> [!NOTE]
> <span data-ttu-id="32cf7-143">Falls keine Radiergummispitze bzw. -schaltfläche vorhanden ist, kann InkCanvas so konfiguriert werden, dass Eingaben mit der Stiftspitze wie Radierstriche behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-143">If an eraser tip or button is not present, the InkCanvas can be configured to process input from the pen tip as an erase stroke.</span></span>

<span data-ttu-id="32cf7-144">In diesem Beispiel überlagert ein [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement ein Hintergrundbild.</span><span class="sxs-lookup"><span data-stu-id="32cf7-144">In this example, an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) overlays a background image.</span></span>

> [!NOTE]
> <span data-ttu-id="32cf7-145">Ein InkCanvas verfügt standardmäßig über [**Höhe.**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Height) und [**Breite-**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Width)-Eigenschaften von null, sofern es sich um ein untergeordnetes Element eines Elements handelt, das die Größe seiner untergeordneten Elemente automatisch festlegt.</span><span class="sxs-lookup"><span data-stu-id="32cf7-145">An InkCanvas has default [**Height**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Height) and [**Width**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Width) properties of zero, unless it is the child of an element that automatically sizes its child elements.</span></span> 

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
    </Grid>
</Grid>
```

<span data-ttu-id="32cf7-146">Diese Serie von Bildern zeigt, wie die Stifteingabe von diesem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="32cf7-146">This series of images shows how pen input is rendered by this [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span>

| ![Der leere „InkCanvas“ mit einem Hintergrundbild](images/ink_basic_1_small.png) | ![Der „InkCanvas“ mit letzten Strichen](images/ink_basic_2_small.png) | ![Der „InkCanvas“ mit einem ausradierten Strich](images/ink_basic_3_small.png) |
| --- | --- | ---|
| <span data-ttu-id="32cf7-150">Der leere [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) mit einem Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="32cf7-150">The blank [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with a background image.</span></span> | <span data-ttu-id="32cf7-151">Der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) mit letzten Strichen</span><span class="sxs-lookup"><span data-stu-id="32cf7-151">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with ink strokes.</span></span> | <span data-ttu-id="32cf7-152">Der [**InkCanvas** ](https://msdn.microsoft.com/library/windows/apps/dn858535) mit einem ausradierten Strich (beachten Sie, dass jeweils der gesamte Strich und nicht nur auf einen Teil davon ausradiert wird).</span><span class="sxs-lookup"><span data-stu-id="32cf7-152">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with one stroke erased (note how erase operates on an entire stroke, not a portion).</span></span> |

<span data-ttu-id="32cf7-153">Die vom [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement unterstützte Freihandfunktion wird von einem CodeBehind-Objekt mit dem Namen [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="32cf7-153">The inking functionality supported by the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control is provided by a code-behind object called the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011).</span></span>

<span data-ttu-id="32cf7-154">Für die einfache Freihandeingabe müssen Sie sich nicht mit dem [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011)-Objekt befassen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-154">For basic inking, you don't have to concern yourself with the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011).</span></span> <span data-ttu-id="32cf7-155">Wenn Sie jedoch das Freihandverhalten des [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements anpassen und konfigurieren möchten, müssen Sie auf das entsprechende **InkPresenter**-Objekt zugreifen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-155">However, to customize and configure inking behavior on the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535), you must access its corresponding **InkPresenter** object.</span></span>

## <a name="basic-customization-with-inkpresenter"></a><span data-ttu-id="32cf7-156">Einfache Anpassung mit „InkPresenter“</span><span class="sxs-lookup"><span data-stu-id="32cf7-156">Basic customization with InkPresenter</span></span>

<span data-ttu-id="32cf7-157">Für jedes [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement wird ein [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011)-Objekt instanziiert.</span><span class="sxs-lookup"><span data-stu-id="32cf7-157">An [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) object is instantiated with each [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span>

> [!NOTE]
> <span data-ttu-id="32cf7-158">Das [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011)-Objekt kann nicht direkt instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-158">The [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) cannot be instantiated directly.</span></span> <span data-ttu-id="32cf7-159">Stattdessen erfolgt der Zugriff darauf über die [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Eigenschaft des [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="32cf7-159">Instead, it is accessed through the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) property of the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span> 

<span data-ttu-id="32cf7-160">Das [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011)-Objekt stellt nicht nur das gesamte Standard-Freihandeingabeverhalten des entsprechenden [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements bereit, sondern bietet auch einen umfassenden Satz von APIs für die zusätzliche Strichanpassung und eine differenzierte Verwaltung des Stifts (standardmäßig und verändert).</span><span class="sxs-lookup"><span data-stu-id="32cf7-160">Along with providing all default inking behaviors of its corresponding [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control, the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) provides a comprehensive set of APIs for additional stroke customization and finer-grained management of the pen input (standard and modified).</span></span> <span data-ttu-id="32cf7-161">Hierzu zählen Stricheigenschaften, unterstützte Eingabegerätetypen und die Möglichkeit festzulegen, ob die Eingabe vom Objekt verarbeitet oder zur Verarbeitung an die App übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="32cf7-161">This includes stroke properties, supported input device types, and whether input is processed by the object or passed to the app for processing.</span></span>

> [!NOTE]
> <span data-ttu-id="32cf7-162">Standardmäßige Freihandeingabe (entweder Stiftspitze oder Radiererspitze/-schaltfläche) wird mit einem sekundären Hardware-Angebot nicht geändert, wie z.B. eine Zeichenstift-Drucktaste, rechte Maustaste oder einem ähnlichen Mechanismus.</span><span class="sxs-lookup"><span data-stu-id="32cf7-162">Standard ink input (from either pen tip or eraser tip/button) is not modified with a secondary hardware affordance, such as a pen barrel button, right mouse button, or similar mechanism.</span></span> 

<span data-ttu-id="32cf7-163">Standardmäßig werden Freihandstriche für nur die Stifteingabe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="32cf7-163">By default, ink is supported for pen input only.</span></span> <span data-ttu-id="32cf7-164">Hier konfigurieren wir [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081), damit Eingabedaten von Stift und Maus als letzte Striche interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-164">Here, we configure the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) to interpret input data from both pen and mouse as ink strokes.</span></span> <span data-ttu-id="32cf7-165">Außerdem legen wir einige anfängliche Freihandstrichattribute fest, die zum Rendern von Strichen mit dem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-165">We also set some initial ink stroke attributes used for rendering strokes to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span>

<span data-ttu-id="32cf7-166">Legen Sie zum Aktivieren der Maus- und Touch-Freihandeingabe die [**InputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter#Windows_UI_Input_Inking_InkPresenter_InputDeviceTypes)-Eigenschaft des [**InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter) auf die Kombination aus den gewünschten [**CoreInputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.core.coreinputdevicetypes)-Werten fest.</span><span class="sxs-lookup"><span data-stu-id="32cf7-166">To enable mouse and touch inking, set the [**InputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter#Windows_UI_Input_Inking_InkPresenter_InputDeviceTypes) property of the [**InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter) to the combination of [**CoreInputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.core.coreinputdevicetypes) values that you want.</span></span>

```csharp
public MainPage()
{
    this.InitializeComponent();

    // Set supported inking device types.
    inkCanvas.InkPresenter.InputDeviceTypes =
        Windows.UI.Core.CoreInputDeviceTypes.Mouse |
        Windows.UI.Core.CoreInputDeviceTypes.Pen;

    // Set initial ink stroke attributes.
    InkDrawingAttributes drawingAttributes = new InkDrawingAttributes();
    drawingAttributes.Color = Windows.UI.Colors.Black;
    drawingAttributes.IgnorePressure = false;
    drawingAttributes.FitToCurve = true;
    inkCanvas.InkPresenter.UpdateDefaultDrawingAttributes(drawingAttributes);
}
```

<span data-ttu-id="32cf7-167">Attribute für letzte Striche können dynamisch entsprechend den Benutzereinstellungen oder App-Anforderungen festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-167">Ink stroke attributes can be set dynamically to accommodate user preferences or app requirements.</span></span>

<span data-ttu-id="32cf7-168">Hier kann der Benutzer aus einer Liste von Freihandfarben auswählen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-168">Here, we let a user choose from a list of ink colors.</span></span>

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
        <TextBlock x:Name="Header"
                   Text="Basic ink customization sample"
                   VerticalAlignment="Center"
                   Style="{ThemeResource HeaderTextBlockStyle}"
                   Margin="10,0,0,0" />
        <TextBlock Text="Color:"
                   Style="{StaticResource SubheaderTextBlockStyle}"
                   VerticalAlignment="Center"
                   Margin="50,0,10,0"/>
        <ComboBox x:Name="PenColor"
                  VerticalAlignment="Center"
                  SelectedIndex="0"
                  SelectionChanged="OnPenColorChanged">
            <ComboBoxItem Content="Black"/>
            <ComboBoxItem Content="Red"/>
        </ComboBox>
    </StackPanel>
    <Grid Grid.Row="1">
        <Image Source="Assets\StoreLogo.png" />
        <InkCanvas x:Name="inkCanvas" />
    </Grid>
</Grid>
```

<span data-ttu-id="32cf7-169">Anschließend behandeln wir Änderungen an der ausgewählten Farbe und aktualisieren die Attribute für letzte Striche entsprechend.</span><span class="sxs-lookup"><span data-stu-id="32cf7-169">We then handle changes to the selected color and update the ink stroke attributes accordingly.</span></span>

```csharp
// Update ink stroke color for new strokes.
private void OnPenColorChanged(object sender, SelectionChangedEventArgs e)
{
    if (inkCanvas != null)
    {
        InkDrawingAttributes drawingAttributes =
            inkCanvas.InkPresenter.CopyDefaultDrawingAttributes();

        string value = ((ComboBoxItem)PenColor.SelectedItem).Content.ToString();

        switch (value)
        {
            case "Black":
                drawingAttributes.Color = Windows.UI.Colors.Black;
                break;
            case "Red":
                drawingAttributes.Color = Windows.UI.Colors.Red;
                break;
            default:
                drawingAttributes.Color = Windows.UI.Colors.Black;
                break;
        };

        inkCanvas.InkPresenter.UpdateDefaultDrawingAttributes(drawingAttributes);
    }
}
```

<span data-ttu-id="32cf7-170">Diese Bilder zeigen, wie die Stifteingabe vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt verarbeitet und angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="32cf7-170">These images shows how pen input is processed and customized by the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081).</span></span>

| ![InkCanvas mit standardmäßigen schwarzen Freihandstrichen](images/ink-basic-custom-1-small.png) | ![InkCanvas mit vom Benutzer ausgewählten roten Freihandstrichen](images/ink-basic-custom-2-small.png) |
| --- | --- |
| <span data-ttu-id="32cf7-173">Das [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement mit standardmäßigen schwarzen letzten Strichen</span><span class="sxs-lookup"><span data-stu-id="32cf7-173">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with default black ink strokes.</span></span> | <span data-ttu-id="32cf7-174">Das [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement mit vom Benutzer ausgewählten roten letzten Strichen</span><span class="sxs-lookup"><span data-stu-id="32cf7-174">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with user selected red ink strokes.</span></span> | 

<span data-ttu-id="32cf7-175">Um zusätzlich zur Freihandeingabe und zum Löschen weitere Funktionen wie etwa die Strichauswahl bereitzustellen, muss die App bestimmte Eingaben identifizieren, die vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt ohne Verarbeitung zur Behandlung an die App weitergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-175">To provide functionality beyond inking and erasing, such as stroke selection, your app must identify specific input for the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) to pass through unprocessed for handling by your app.</span></span>

## <a name="pass-through-input-for-advanced-processing"></a><span data-ttu-id="32cf7-176">Weitergabe der Eingabe für die erweiterte Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="32cf7-176">Pass-through input for advanced processing</span></span>

<span data-ttu-id="32cf7-177">Standardmäßig verarbeitet [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) sämtliche Eingaben als letzten Strich oder ausradierten Strich.</span><span class="sxs-lookup"><span data-stu-id="32cf7-177">By default, [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) processes all input as either an ink stroke or an erase stroke.</span></span> <span data-ttu-id="32cf7-178">Hierzu zählen auch Eingaben, die durch ein sekundäres Hardwareangebot wie etwa eine Zeichenstift-Drucktaste, eine rechte Maustaste oder ein ähnliches Element geändert werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-178">This includes input modified by a secondary hardware affordance such as a pen barrel button, a right mouse button, or similar.</span></span>

<span data-ttu-id="32cf7-179">Wenn Benutzer diese sekundären Angebote verwenden, erwarten sie in der Regel zusätzliche Funktionalität oder ein geändertes Verhalten.</span><span class="sxs-lookup"><span data-stu-id="32cf7-179">When using these secondary affordances, users typically expect some additional functionality or a modified behavior.</span></span>

<span data-ttu-id="32cf7-180">In einigen Fällen müssen Sie eventuell basierend auf der Benutzerauswahl auf der App-UI grundlegende Freihandfunktionen für Stifte ohne sekundäre Angebote (Funktionalität, die in der Regel nicht der Stiftspitze zugeordnet ist), andere Eingabegerätetypen, zusätzliche Funktionalität oder geändertes Verhalten verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-180">In some cases, you might need to expose basic ink functionality for pens without secondary affordances (functionality not usually associated with the pen tip), other input device types, additional functionality, or modified behavior, based on a user selection in your app's UI.</span></span>

<span data-ttu-id="32cf7-181">Das [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt kann zu diesem Zweck so konfiguriert werden, dass bestimmte Eingaben unverarbeitet bleiben.</span><span class="sxs-lookup"><span data-stu-id="32cf7-181">To support this, [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) can be configured to leave specific input unprocessed.</span></span> <span data-ttu-id="32cf7-182">Diese unverarbeiteten Eingaben werden dann zur Verarbeitung an die App weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="32cf7-182">This unprocessed input is then passed through to your app for processing.</span></span>

<span data-ttu-id="32cf7-183">Im folgenden Codebeispiel werden die Schritte zum Aktivieren der Strichauswahl gezeigt, wenn die Eingabe mit einer Zeichenstift-Drucktaste (oder rechten Maustaste) geändert wird.</span><span class="sxs-lookup"><span data-stu-id="32cf7-183">The following code example steps through how to enable stroke selection when input is modified with a pen barrel button (or right mouse button).</span></span>

<span data-ttu-id="32cf7-184">In diesem Beispiel verwenden wir die Dateien „MainPage.xaml“ und „MainPage.Xaml.cs“, um den gesamten Code zu hosten.</span><span class="sxs-lookup"><span data-stu-id="32cf7-184">For this example, we use the MainPage.xaml and MainPage.xaml.cs files to host all code.</span></span>

1.  <span data-ttu-id="32cf7-185">Zunächst richten wir in „MainPage.xaml“ die Benutzeroberfläche ein.</span><span class="sxs-lookup"><span data-stu-id="32cf7-185">First, we set up the UI in MainPage.xaml.</span></span>

    <span data-ttu-id="32cf7-186">Hier fügen wir einen Zeichenbereich (unterhalb des [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements) zum Zeichnen der Strichauswahl hinzu.</span><span class="sxs-lookup"><span data-stu-id="32cf7-186">Here, we add a canvas (below the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)) to draw the selection stroke.</span></span> <span data-ttu-id="32cf7-187">Durch die Verwendung einer eigenen Ebene zum Zeichnen der Strichauswahl bleiben das **InkCanvas**-Steuerelement und dessen Inhalt unverändert.</span><span class="sxs-lookup"><span data-stu-id="32cf7-187">Using a separate layer to draw the selection stroke leaves the **InkCanvas** and its content untouched.</span></span>

    ![Das leere InkCanvas-Steuerelement mit einem darunterliegenden Auswahlzeichenbereich](images/ink-unprocessed-1-small.png)

      ```xaml
        <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
          <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
          </Grid.RowDefinitions>
          <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
            <TextBlock x:Name="Header"
              Text="Advanced ink customization sample"
              VerticalAlignment="Center"
              Style="{ThemeResource HeaderTextBlockStyle}"
              Margin="10,0,0,0" />
          </StackPanel>
          <Grid Grid.Row="1">
            <!-- Canvas for displaying selection UI. -->
            <Canvas x:Name="selectionCanvas"/>
            <!-- Inking area -->
            <InkCanvas x:Name="inkCanvas"/>
          </Grid>
        </Grid>
      ```

2.  <span data-ttu-id="32cf7-189">In „MainPage.xaml.cs“ deklarieren wir eine Reihe von globalen Variablen zum Speichern von Verweisen auf Aspekte der Auswahl-UI.</span><span class="sxs-lookup"><span data-stu-id="32cf7-189">In MainPage.xaml.cs, we declare a couple of global variables for keeping references to aspects of the selection UI.</span></span> <span data-ttu-id="32cf7-190">Dies gilt insbesondere für den Auswahllassostrich und das umgebende Rechteck, das die ausgewählten Striche hervorhebt.</span><span class="sxs-lookup"><span data-stu-id="32cf7-190">Specifically, the selection lasso stroke and the bounding rectangle that highlights the selected strokes.</span></span>

      ```csharp
        // Stroke selection tool.
        private Polyline lasso;
        // Stroke selection area.
        private Rect boundingRect;
      ```

3.  <span data-ttu-id="32cf7-191">Anschließend konfigurieren wir das [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt so, dass es Eingabedaten von Stift und Maus als Freihandstriche interpretiert. Zudem legen wir anfängliche Freihandstrichattribute zum Rendern von Freihandstrichen mit dem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement fest.</span><span class="sxs-lookup"><span data-stu-id="32cf7-191">Next, we configure the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) to interpret input data from both pen and mouse as ink strokes, and set some initial ink stroke attributes used for rendering strokes to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span>

    <span data-ttu-id="32cf7-192">Vor allem geben wir mithilfe der [**InputProcessingConfiguration**](https://msdn.microsoft.com/library/windows/apps/dn948764)-Eigenschaft des [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekts an, dass alle geänderten Eingaben von der App verarbeitet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-192">Most importantly, we use the [**InputProcessingConfiguration**](https://msdn.microsoft.com/library/windows/apps/dn948764) property of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) to indicate that any modified input should be processed by the app.</span></span> <span data-ttu-id="32cf7-193">Geänderte Eingaben geben wir an, indem wir **InputProcessingConfiguration.RightDragAction** den Wert [**InkInputRightDragAction.LeaveUnprocessed**](https://msdn.microsoft.com/library/windows/apps/dn948760) zuweisen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-193">Modified input is specified by assigning **InputProcessingConfiguration.RightDragAction** a value of [**InkInputRightDragAction.LeaveUnprocessed**](https://msdn.microsoft.com/library/windows/apps/dn948760).</span></span>

    <span data-ttu-id="32cf7-194">Anschließend weisen wir Listener für die nicht verarbeiteten Ereignisse [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/dn914712), [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/dn914711) und [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/dn914713) zu, die vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt weitergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-194">We then assign listeners for the unprocessed [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/dn914712), [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/dn914711), and [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/dn914713) events passed through by the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081).</span></span> <span data-ttu-id="32cf7-195">Sämtliche Auswahlfunktionalität wird in den Handlern für diese Ereignisse implementiert.</span><span class="sxs-lookup"><span data-stu-id="32cf7-195">All selection functionality is implemented in the handlers for these events.</span></span>

    <span data-ttu-id="32cf7-196">Schließlich weisen wir Listener für die Ereignisse [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702) und [**StrokesErased**](https://msdn.microsoft.com/library/windows/apps/dn948767) des [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekts zu.</span><span class="sxs-lookup"><span data-stu-id="32cf7-196">Finally, we assign listeners for the [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702) and [**StrokesErased**](https://msdn.microsoft.com/library/windows/apps/dn948767) events of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081).</span></span> <span data-ttu-id="32cf7-197">Wir verwenden die Handler für diese Ereignisse, um die Auswahl-UI zu bereinigen, wenn ein neuer Strich begonnen oder ein vorhandener Strich ausradiert wird.</span><span class="sxs-lookup"><span data-stu-id="32cf7-197">We use the handlers for these events to clean up the selection UI if a new stroke is started or an existing stroke is erased.</span></span>

    ![InkCanvas mit standardmäßigen schwarzen letzten Strichen](images/ink-unprocessed-2-small.png)

      ```csharp
        public MainPage()
        {
          this.InitializeComponent();

          // Set supported inking device types.
          inkCanvas.InkPresenter.InputDeviceTypes =
            Windows.UI.Core.CoreInputDeviceTypes.Mouse |
            Windows.UI.Core.CoreInputDeviceTypes.Pen;

          // Set initial ink stroke attributes.
          InkDrawingAttributes drawingAttributes = new InkDrawingAttributes();
          drawingAttributes.Color = Windows.UI.Colors.Black;
          drawingAttributes.IgnorePressure = false;
          drawingAttributes.FitToCurve = true;
          inkCanvas.InkPresenter.UpdateDefaultDrawingAttributes(drawingAttributes);

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

          // Listen for new ink or erase strokes to clean up selection UI.
          inkCanvas.InkPresenter.StrokeInput.StrokeStarted +=
              StrokeInput_StrokeStarted;
          inkCanvas.InkPresenter.StrokesErased +=
              InkPresenter_StrokesErased;
        }
      ```

4.  <span data-ttu-id="32cf7-199">Anschließend definieren wir Handler für die nicht verarbeiteten Ereignisse [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/dn914712), [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/dn914711) und [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/dn914713), die vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt weitergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-199">We then define handlers for the unprocessed [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/dn914712), [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/dn914711), and [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/dn914713) events passed through by the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081).</span></span>

    <span data-ttu-id="32cf7-200">Sämtliche Auswahlfunktionalität, einschließlich des Lassostrichs und des umgebenden Rechtecks, wird in diesen Handlern implementiert.</span><span class="sxs-lookup"><span data-stu-id="32cf7-200">All selection functionality is implemented in these handlers, including the lasso stroke and the bounding rectangle.</span></span>

    ![Auswahllasso](images/ink-unprocessed-3-small.png)

      ```csharp
        // Handle unprocessed pointer events from modified input.
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
      ```

5.  <span data-ttu-id="32cf7-202">Um den PointerReleased-Ereignishandler abzuschließen, löschen wir sämtlichen Inhalt (den Lassostrich) aus der Auswahlebene und zeichnen dann ein einzelnes umgebendes Rechteck um die letzten Striche, die sich im Lassobereich befinden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-202">To conclude the PointerReleased event handler, we clear the selection layer of all content (the lasso stroke) and then draw a single bounding rectangle around the ink strokes encompassed by the lasso area.</span></span>

    ![Das umgebende Auswahlrechteck](images/ink-unprocessed-4-small.png)

      ```csharp
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
      ```

6.  <span data-ttu-id="32cf7-204">Schließlich definieren wir Handler für die InkPresenter-Ereignisse [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702) und [**StrokesErased**](https://msdn.microsoft.com/library/windows/apps/dn948767).</span><span class="sxs-lookup"><span data-stu-id="32cf7-204">Finally, we define handlers for the [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702) and [**StrokesErased**](https://msdn.microsoft.com/library/windows/apps/dn948767) InkPresenter events.</span></span>

    <span data-ttu-id="32cf7-205">Diese beiden rufen einfach die gleiche Bereinigungsfunktion auf, um bei jeder Erkennung eines neuen Strichs die aktuelle Auswahl zu löschen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-205">These both just call the same cleanup function to clear the current selection whenever a new stroke is detected.</span></span>

      ```csharp
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
      ```

7.  <span data-ttu-id="32cf7-206">Dies ist die Funktion zum Entfernen der gesamten Auswahl-UI aus dem Auswahlzeichenbereich, wenn ein neuer Strich begonnen oder ein vorhandener Strich ausradiert wird.</span><span class="sxs-lookup"><span data-stu-id="32cf7-206">Here's the function to remove all selection UI from the selection canvas when a new stroke is started or an existing stroke is erased.</span></span>

      ```csharp
        // Clean up selection UI.
        private void ClearSelection()
        {
          var strokes = inkCanvas.InkPresenter.StrokeContainer.GetStrokes();
          foreach (var stroke in strokes)
          {
            stroke.Selected = false;
          }
          ClearDrawnBoundingRect();
         }

        private void ClearDrawnBoundingRect()
        {
          if (selectionCanvas.Children.Any())
          {
            selectionCanvas.Children.Clear();
            boundingRect = Rect.Empty;
          }
        }
      ```

## <a name="custom-ink-rendering"></a><span data-ttu-id="32cf7-207">Benutzerdefiniertes Rendern von Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="32cf7-207">Custom ink rendering</span></span>

<span data-ttu-id="32cf7-208">Standardmäßig werden Freihandeingaben in einem Hintergrundthread mit geringer Wartezeit verarbeitet und während des Zeichnens „nass“ gerendert.</span><span class="sxs-lookup"><span data-stu-id="32cf7-208">By default, ink input is processed on a low-latency background thread and rendered "wet" as it is drawn.</span></span> <span data-ttu-id="32cf7-209">Wenn der Strich abgeschlossen ist (der Stift oder Finger wurde angehoben oder die Maustaste losgelassen), wird er im UI-Thread verarbeitet und auf der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Ebene „trocken“ gerendert (über dem Anwendungsinhalt, wo er die nasse Freihandeingabe ersetzt).</span><span class="sxs-lookup"><span data-stu-id="32cf7-209">When the stroke is completed (pen or finger lifted, or mouse button released), the stroke is processed on the UI thread and rendered "dry" to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) layer (above the application content and replacing the wet ink).</span></span>

<span data-ttu-id="32cf7-210">Die Freihandplattform ermöglicht es Ihnen, dieses Verhalten zu überschreiben und die Freihandfunktionen durch benutzerdefiniertes Trocknen der Freihandeingabe umfassend anzupassen und bietet eine effizienten Verwaltung großer und komplexer Listen von Freihandstrichen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-210">The ink platform enables you to override this behavior and completely customize the inking experience by custom drying the ink input and providing more efficient management of large, or complex, collections of ink strokes.</span></span> 

<span data-ttu-id="32cf7-211">Benutzerdefiniertes Trocknen erfordert anstelle des standardmäßigen [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements ein [**IInkD2DRenderer**](https://msdn.microsoft.com/library/mt147263)-Objekt, um die Freihandeingabe zu verwalten und im Direct2D-Gerätekontext der universellen Windows-App zu rendern.</span><span class="sxs-lookup"><span data-stu-id="32cf7-211">Custom drying requires an [**IInkD2DRenderer**](https://msdn.microsoft.com/library/mt147263) object to manage the ink input and render it to the Direct2D device context of your Universal Windows app, instead of the default [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span>

<span data-ttu-id="32cf7-212">Eine App erstellt durch Aufruf von [**ActivateCustomDrying**](https://msdn.microsoft.com/library/windows/apps/dn922012) (vor dem Laden des [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements) ein [**InkSynchronizer**](https://msdn.microsoft.com/library/windows/apps/dn903979)-Objekt, um zu definieren, wie ein letzter Strich trocken in einer [**SurfaceImageSource**](https://msdn.microsoft.com/library/windows/apps/hh702041)- oder [**VirtualSurfaceImageSource**](https://msdn.microsoft.com/library/windows/apps/hh702050)-Klasse gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="32cf7-212">By calling [**ActivateCustomDrying**](https://msdn.microsoft.com/library/windows/apps/dn922012) (before the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) is loaded), an app creates an [**InkSynchronizer**](https://msdn.microsoft.com/library/windows/apps/dn903979) object to customize how an ink stroke is rendered dry to a [**SurfaceImageSource**](https://msdn.microsoft.com/library/windows/apps/hh702041) or [**VirtualSurfaceImageSource**](https://msdn.microsoft.com/library/windows/apps/hh702050).</span></span> <span data-ttu-id="32cf7-213">Beispielsweise kann ein letzter Strich gerastert und in den Anwendungsinhalt integriert werden, statt auf einer separaten **InkCanvas**-Ebene gerendert zu werden.</span><span class="sxs-lookup"><span data-stu-id="32cf7-213">For example, an ink stroke could be rasterized and integrated into application content instead of as a separate **InkCanvas** layer.</span></span> 

<span data-ttu-id="32cf7-214">Ein vollständiges Beispiel für diese Funktion finden Sie unter [Komplexes Freihandbeispiel](http://go.microsoft.com/fwlink/p/?LinkID=620314).</span><span class="sxs-lookup"><span data-stu-id="32cf7-214">For a full example of this functionality, see the [Complex ink sample](http://go.microsoft.com/fwlink/p/?LinkID=620314).</span></span>

> [!NOTE]
> <span data-ttu-id="32cf7-215">Benutzerdefiniertes Trocknen und die [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="32cf7-215">Custom drying and the [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)</span></span>  
> <span data-ttu-id="32cf7-216">Wenn Ihre App das Standard-Renderverhalten für Freihandeingaben von [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) mit einer benutzerdefinierten Trockenimplementierung außer Kraft setzt, sind die gerenderten Freihandstriche für die InkToolbar nicht mehr verfügbar und die integrierten Löschbefehle der InkToolbar funktionieren nicht wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="32cf7-216">If your app overrides the default ink rendering behavior of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) with a custom drying implementation, the rendered ink strokes are no longer available to the InkToolbar and the built-in erase commands of the InkToolbar do not work as expected.</span></span> <span data-ttu-id="32cf7-217">Damit Sie Löschfunktionen bereitstellen können, müssen Sie alle Zeigerereignisse verarbeiten, für jeden Strich einen Treffertest ausführen und den integrierten Befehl „Freihand vollständig löschen“ außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-217">To provide erase functionality, you must handle all pointer events, perform hit-testing on each stroke, and override the built-in "Erase all ink" command.</span></span>

## <a name="other-articles-in-this-section"></a><span data-ttu-id="32cf7-218">Andere Artikel in diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="32cf7-218">Other articles in this section</span></span>

| <span data-ttu-id="32cf7-219">Thema</span><span class="sxs-lookup"><span data-stu-id="32cf7-219">Topic</span></span> | <span data-ttu-id="32cf7-220">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="32cf7-220">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="32cf7-221">Erkennen von Freihandstrichen</span><span class="sxs-lookup"><span data-stu-id="32cf7-221">Recognize ink strokes</span></span>](convert-ink-to-text.md) | <span data-ttu-id="32cf7-222">Konvertieren Sie letzte Striche mit der Schrifterkennung in Text oder mit der benutzerdefinierten Erkennung in Formen.</span><span class="sxs-lookup"><span data-stu-id="32cf7-222">Convert ink strokes to text using handwriting recognition, or to shapes using custom recognition.</span></span> |
| [<span data-ttu-id="32cf7-223">Speichern und Abrufen von letzten Strichen</span><span class="sxs-lookup"><span data-stu-id="32cf7-223">Store and retrieve ink strokes</span></span>](save-and-load-ink.md) | <span data-ttu-id="32cf7-224">Speichern Sie Freihandstrichdaten mithilfe eingebetteter serialisierter Freihandformat-Metadaten (Ink Serialized Format, ISF) in einer GIF-Datei (Graphics Interchange Format).</span><span class="sxs-lookup"><span data-stu-id="32cf7-224">Store ink stroke data in a Graphics Interchange Format (GIF) file using embedded Ink Serialized Format (ISF) metadata.</span></span> |
| [<span data-ttu-id="32cf7-225">Hinzufügen eines InkToolbar-Elements zu einer UWP-App für die Freihandeingabe</span><span class="sxs-lookup"><span data-stu-id="32cf7-225">Add an InkToolbar to a UWP inking app</span></span>](ink-toolbar.md) | <span data-ttu-id="32cf7-226">Fügen Sie einer App für die Freihandeingabe in der universellen Windows-Plattform (UWP) eine Standard-InkToolbar hinzu. Fügen Sie der InkToolbar einen anpassbaren Stift hinzu und binden Sie diesen an eine benutzerdefinierte Definition für den Stift.</span><span class="sxs-lookup"><span data-stu-id="32cf7-226">Add a default InkToolbar to a Universal Windows Platform (UWP) inking app, add a custom pen button to the InkToolbar, and bind the custom pen button to a custom pen definition.</span></span> |

## <a name="related-articles"></a><span data-ttu-id="32cf7-227">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="32cf7-227">Related articles</span></span>

* [<span data-ttu-id="32cf7-228">Erste Schritte: Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="32cf7-228">Get started: Support ink in your UWP app</span></span>](../get-started/ink-walkthrough.md)
* [<span data-ttu-id="32cf7-229">Behandeln von Zeigereingaben</span><span class="sxs-lookup"><span data-stu-id="32cf7-229">Handle pointer input</span></span>](handle-pointer-input.md)
* [<span data-ttu-id="32cf7-230">Identifizieren von Eingabegeräten</span><span class="sxs-lookup"><span data-stu-id="32cf7-230">Identify input devices</span></span>](identify-input-devices.md)

**<span data-ttu-id="32cf7-231">APIs</span><span class="sxs-lookup"><span data-stu-id="32cf7-231">APIs</span></span>**

* [**<span data-ttu-id="32cf7-232">Windows.Devices.Input</span><span class="sxs-lookup"><span data-stu-id="32cf7-232">Windows.Devices.Input</span></span>**](https://msdn.microsoft.com/library/windows/apps/br225648)
* [**<span data-ttu-id="32cf7-233">Windows.UI.Input.Inking</span><span class="sxs-lookup"><span data-stu-id="32cf7-233">Windows.UI.Input.Inking</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208524)
* [**<span data-ttu-id="32cf7-234">Windows.UI.Input.Inking.Core</span><span class="sxs-lookup"><span data-stu-id="32cf7-234">Windows.UI.Input.Inking.Core</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn958452)

**<span data-ttu-id="32cf7-235">Beispiele</span><span class="sxs-lookup"><span data-stu-id="32cf7-235">Samples</span></span>**
* [<span data-ttu-id="32cf7-236">Lernprogramm „Erste Schritte:” Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="32cf7-236">Get Started Tutorial: Support ink in your UWP app</span></span>](https://aka.ms/appsample-ink)
* [<span data-ttu-id="32cf7-237">Einfaches Freihandbeispiel (C#/C++)</span><span class="sxs-lookup"><span data-stu-id="32cf7-237">Simple ink sample (C#/C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620312)
* [<span data-ttu-id="32cf7-238">Komplexes Freihandbeispiel (C++)</span><span class="sxs-lookup"><span data-stu-id="32cf7-238">Complex ink sample (C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620314)
* [<span data-ttu-id="32cf7-239">Freihandbeispiel (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="32cf7-239">Ink sample (JavaScript)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620308)
* [<span data-ttu-id="32cf7-240">Malbuchbeispiel</span><span class="sxs-lookup"><span data-stu-id="32cf7-240">Coloring book sample</span></span>](https://aka.ms/cpubsample-coloringbook)
* [<span data-ttu-id="32cf7-241">Familiennotizbeispiel</span><span class="sxs-lookup"><span data-stu-id="32cf7-241">Family notes sample</span></span>](https://aka.ms/cpubsample-familynotessample)
* [<span data-ttu-id="32cf7-242">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="32cf7-242">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="32cf7-243">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="32cf7-243">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="32cf7-244">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="32cf7-244">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="32cf7-245">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="32cf7-245">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="32cf7-246">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="32cf7-246">Archive Samples</span></span>**
* [<span data-ttu-id="32cf7-247">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="32cf7-247">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="32cf7-248">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="32cf7-248">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="32cf7-249">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="32cf7-249">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="32cf7-250">Eingabe: Gesten und Manipulationen mit GestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="32cf7-250">Input: Gestures and manipulations with GestureRecognizer</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231605)
