---
author: Karl-Bridge-Microsoft
Description: Build Universal Windows Platform (UWP) apps that support custom interactions from pen and stylus devices, including digital ink for natural writing and drawing experiences.
title: Stiftinteraktionen und Windows Ink in UWP-Apps
ms.assetid: 3DA4F2D2-5405-42A1-9ED9-3A87BCD84C43
label: Pen interactions and Windows Ink in UWP apps
template: detail.hbs
keywords: Windows Ink, Windows-Freihandeingabe, DirectInk, InkPresenter, InkCanvas, Handschrifterkennung, Benutzerinteraktion, Eingabe
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a9a9dd4347cc682f384c2d408d30820acf76ce34
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6855249"
---
# <a name="pen-interactions-and-windows-ink-in-uwp-apps"></a><span data-ttu-id="bad23-103">Stiftinteraktionen und Windows Ink in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="bad23-103">Pen interactions and Windows Ink in UWP apps</span></span>

![Surface Pen](images/ink/hero-small.png)  
<span data-ttu-id="bad23-105">*Surface Pen* (zum Kauf im [Microsoft Store](https://aka.ms/purchasesurfacepen) verfügbar).</span><span class="sxs-lookup"><span data-stu-id="bad23-105">*Surface Pen* (available for purchase at the [Microsoft Store](https://aka.ms/purchasesurfacepen)).</span></span>

## <a name="overview"></a><span data-ttu-id="bad23-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="bad23-106">Overview</span></span>

<span data-ttu-id="bad23-107">Optimieren Sie Ihre App für die Universelle Windows-Plattform (UWP-App) für Stifteingaben, um sowohl Standardfunktionalität für [**Zeigergeräte**](https://msdn.microsoft.com/library/windows/apps/br225633) als auch optimale Windows Ink-Funktionalität für Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="bad23-107">Optimize your Universal Windows Platform (UWP) app for pen input to provide both standard [**pointer device**](https://msdn.microsoft.com/library/windows/apps/br225633) functionality and the best Windows Ink experience for your users.</span></span>

> [!NOTE]
> <span data-ttu-id="bad23-108">Der Schwerpunkt dieses Themas liegt auf der Windows Ink-Plattform.</span><span class="sxs-lookup"><span data-stu-id="bad23-108">This topic focuses on the Windows Ink platform.</span></span> <span data-ttu-id="bad23-109">Informationen zur allgemeinen Behandlung von Zeigereingaben (ähnlich Maus-, Touch- und Touchpadeingaben) finden Sie unter [Behandeln von Zeigereingaben](handle-pointer-input.md).</span><span class="sxs-lookup"><span data-stu-id="bad23-109">For general pointer input handling (similar to mouse, touch, and touchpad), see [Handle pointer input](handle-pointer-input.md).</span></span>

| <span data-ttu-id="bad23-110">Videos</span><span class="sxs-lookup"><span data-stu-id="bad23-110">Videos</span></span> |   |
| --- | --- |
| <iframe src="https://channel9.msdn.com/Blogs/One-Dev-Minute/Using-Ink-in-Your-UWP-App/player" width="300" height="200" allowFullScreen frameBorder="0"></iframe> | <iframe src="https://channel9.msdn.com/Events/Ignite/2016/BRK2060/player" width="300" height="200" allowFullScreen frameBorder="0"></iframe> |
| *<span data-ttu-id="bad23-111">Verwenden von Ink in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="bad23-111">Using ink in your UWP app</span></span>* | *<span data-ttu-id="bad23-112">Verwenden von Windows Pen und Ink zum Erstellen von stärker interaktiven enterpriseapps</span><span class="sxs-lookup"><span data-stu-id="bad23-112">Use Windows Pen and Ink to build more engaging enterpriseapps</span></span>* |

<span data-ttu-id="bad23-113">In Verbindung mit einem Zeichengerät bietet die Windows Ink-Plattform eine natürliche Möglichkeit, digitale handschriftliche Notizen, Zeichnungen und Anmerkungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bad23-113">The Windows Ink platform, together with a pen device, provides a natural way to create digital handwritten notes, drawings, and annotations.</span></span> <span data-ttu-id="bad23-114">Sie können auf der Plattform Freihanddaten aus einem Eingabedigitalisierungsgerät erfassen, Freihanddaten generieren, verwalten und als letzte Striche auf dem Ausgabegerät rendern sowie über die Schrifterkennung in Text umwandeln.</span><span class="sxs-lookup"><span data-stu-id="bad23-114">The platform supports capturing digitizer input as ink data, generating ink data, managing ink data, rendering ink data as ink strokes on the output device, and converting ink to text through handwriting recognition.</span></span>

<span data-ttu-id="bad23-115">Ihre App kann nicht nur die grundlegende Position und Bewegung des Stifts aufzeichnen, während der Benutzer schreibt oder zeichnet, sondern auch den variierenden Druck während des gesamten Strichs nachverfolgen und erfassen.</span><span class="sxs-lookup"><span data-stu-id="bad23-115">In addition to capturing the basic position and movement of the pen as the user writes or draws, your app can also track and collect the varying amounts of pressure used throughout a stroke.</span></span> <span data-ttu-id="bad23-116">Mit diesen Informationen, zusammen mit Einstellungen für Form und Größe der Stiftspitze, Drehung, Freihandfarbe und Zweck (einfache Freihandeingabe, Löschen, Hervorheben und Auswählen), können Sie dem Benutzer ermöglichen, auf ähnliche Weise wie mit einem Stift, Bleistift oder Pinsel auf Papier zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="bad23-116">This information, along with settings for pen tip shape, size, and rotation, ink color, and purpose (plain ink, erasing, highlighting, and selecting), enables you to provide user experiences that closely resemble writing or drawing on paper with a pen, pencil, or brush.</span></span>

> [!NOTE]
> <span data-ttu-id="bad23-117">Ihre App kann auch Freihandeingaben von anderen zeigerbasierten Geräten, z.B. Touchdigitalisierungs- und Mausgeräte, unterstützen.</span><span class="sxs-lookup"><span data-stu-id="bad23-117">Your app can also support ink input from other pointer-based devices, including touch digitizers and mouse devices.</span></span> 

<span data-ttu-id="bad23-118">Die Freihandplattform ist sehr flexibel.</span><span class="sxs-lookup"><span data-stu-id="bad23-118">The ink platform is very flexible.</span></span> <span data-ttu-id="bad23-119">Je nach Ihren Anforderungen unterstützt sie verschiedene Funktionalitätsgrade.</span><span class="sxs-lookup"><span data-stu-id="bad23-119">It is designed to support various levels of functionality, depending on your requirements.</span></span>

<span data-ttu-id="bad23-120">Richtlinien für die Benutzeroberfläche von WindowsInk finden Sie unter [Inking controls](../controls-and-patterns/inking-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bad23-120">For Windows Ink UX guidelines, see [Inking controls](../controls-and-patterns/inking-controls.md).</span></span>

## <a name="components-of-the-windows-ink-platform"></a><span data-ttu-id="bad23-121">Komponenten der WindowsInk-Plattform</span><span class="sxs-lookup"><span data-stu-id="bad23-121">Components of the Windows Ink platform</span></span>

| <span data-ttu-id="bad23-122">Komponente</span><span class="sxs-lookup"><span data-stu-id="bad23-122">Component</span></span> | <span data-ttu-id="bad23-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bad23-123">Description</span></span> |
| --- | --- |
| [**<span data-ttu-id="bad23-124">InkCanvas</span><span class="sxs-lookup"><span data-stu-id="bad23-124">InkCanvas</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn858535) | <span data-ttu-id="bad23-125">Ein XAMLUI-Plattform-Steuerelement, das in der Standardeinstellung empfängt und anzeigt alle Eingaben von einem Stift als letzten Strich oder ausradierten Strich.</span><span class="sxs-lookup"><span data-stu-id="bad23-125">A XAMLUI platform control that, by default, receives and displays all input from a pen as either an ink stroke or an erase stroke.</span></span><br/><span data-ttu-id="bad23-126">Weitere Informationen zur Verwendung von InkCanvas finden Sie unter [Erkennen von Windows Ink-Strichen als Text](convert-ink-to-text.md) und [Speichern und Abrufen der Daten von Windows Ink-Strichen](save-and-load-ink.md).</span><span class="sxs-lookup"><span data-stu-id="bad23-126">For more information about how to use the InkCanvas, see [Recognize Windows Ink strokes as text](convert-ink-to-text.md) and [Store and retrieve Windows Ink stroke data](save-and-load-ink.md).</span></span> |
| [**<span data-ttu-id="bad23-127">InkPresenter</span><span class="sxs-lookup"><span data-stu-id="bad23-127">InkPresenter</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn922011) | <span data-ttu-id="bad23-128">Ein CodeBehind-Objekt, das zusammen mit einem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement instanziiert wird (über die [**InkCanvas.InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Eigenschaft verfügbar gemacht).</span><span class="sxs-lookup"><span data-stu-id="bad23-128">A code-behind object, instantiated along with an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control (exposed through the [**InkCanvas.InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) property).</span></span> <span data-ttu-id="bad23-129">Dieses Objekt stellt alle Standardfreihandfunktionen bereit, die vom **InkCanvas**-Steuerelement zur Verfügung gestellt werden, sowie einen umfassenden Satz von APIs für zusätzliche Anpassung und Personalisierung.</span><span class="sxs-lookup"><span data-stu-id="bad23-129">This object provides all default inking functionality exposed by the **InkCanvas**, along with a comprehensive set of APIs for additional customization and personalization.</span></span><br/><span data-ttu-id="bad23-130">Weitere Informationen zur Verwendung von InkPresenter finden Sie unter [Erkennen von Windows Ink-Strichen als Text](convert-ink-to-text.md) und [Speichern und Abrufen der Daten von Windows Ink-Strichen](save-and-load-ink.md).</span><span class="sxs-lookup"><span data-stu-id="bad23-130">For more information about how to use the InkPresenter, see [Recognize Windows Ink strokes as text](convert-ink-to-text.md) and [Store and retrieve Windows Ink stroke data](save-and-load-ink.md).</span></span> |
| [**<span data-ttu-id="bad23-131">InkToolbar</span><span class="sxs-lookup"><span data-stu-id="bad23-131">InkToolbar</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) | <span data-ttu-id="bad23-132">Ein XAMLUI-Steuerelement, enthält eine anpassbare und erweiterbare Sammlung von Schaltflächen, die Freihand-Features in einem verknüpften [**InkCanvas-Steuerelement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)aktivieren.</span><span class="sxs-lookup"><span data-stu-id="bad23-132">A XAMLUI platform control containing a customizable and extensible collection of buttons that activate ink-related features in an associated [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas).</span></span><br/><span data-ttu-id="bad23-133">Weitere Informationen zur Verwendung von InkToolbar finden Sie unter [Add an InkToolbar to a Universal Windows Platform (UWP) inking app](ink-toolbar.md).</span><span class="sxs-lookup"><span data-stu-id="bad23-133">For more information about how to use the InkToolbar, see [Add an InkToolbar to a Universal Windows Platform (UWP) inking app](ink-toolbar.md).</span></span> |
| [**<span data-ttu-id="bad23-134">IInkD2DRenderer</span><span class="sxs-lookup"><span data-stu-id="bad23-134">IInkD2DRenderer</span></span>**](https://msdn.microsoft.com/library/mt147263) | <span data-ttu-id="bad23-135">Ermöglicht das Rendern von Freihandstrichen im angegebenen Direct2D-Gerätekontext einer universellen Windows-App statt im standardmäßigen [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="bad23-135">Enables the rendering of ink strokes onto the designated Direct2D device context of a Universal Windows app, instead of the default [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span> <span data-ttu-id="bad23-136">Dies ermöglicht die umfassende Anpassung der Freihandfunktionen.</span><span class="sxs-lookup"><span data-stu-id="bad23-136">This enables full customization of the inking experience.</span></span><br/><span data-ttu-id="bad23-137">Weitere Informationen finden Sie in diesem [komplexen Freihandbeispiel](https://go.microsoft.com/fwlink/p/?LinkID=620314).</span><span class="sxs-lookup"><span data-stu-id="bad23-137">For more information, see the [Complex ink sample](https://go.microsoft.com/fwlink/p/?LinkID=620314).</span></span> |

## <a name="basic-inking-with-inkcanvas"></a><span data-ttu-id="bad23-138">Einfaches Freihandzeichnen mit „InkCanvas“</span><span class="sxs-lookup"><span data-stu-id="bad23-138">Basic inking with InkCanvas</span></span>

<span data-ttu-id="bad23-139">Um einfaches Freihandzeichen hinzuzufügen, platzieren Sie einfach ein [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-UWP-Steuerelement auf der entsprechenden Seite in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="bad23-139">To add basic inking functionality, just place an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) UWP platform control on the appropriate page in your app.</span></span>

<span data-ttu-id="bad23-140">Das [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement unterstützt standardmäßig nur Freihandeingaben mit einem Stift.</span><span class="sxs-lookup"><span data-stu-id="bad23-140">By default, the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) supports ink input only from a pen.</span></span> <span data-ttu-id="bad23-141">Die Eingabe wird entweder als Strich mit den Standardeinstellungen für Farbe und Stärke gerendert (ein schwarzer Kugelschreiber mit einer Stärke von 2Pixeln) oder als Strichradierer behandelt (wenn die Eingabe von einer mit einer Löschschaltfläche geänderten Radiergummi- oder Stiftspitze stammt).</span><span class="sxs-lookup"><span data-stu-id="bad23-141">The input is either rendered as an ink stroke using default settings for color and thickness (a black ballpoint pen with a thickness of 2 pixels), or treated as a stroke eraser (when input is from an eraser tip or the pen tip modified with an erase button).</span></span>

> [!NOTE]
> <span data-ttu-id="bad23-142">Falls keine Radiergummispitze bzw. -schaltfläche vorhanden ist, kann InkCanvas so konfiguriert werden, dass Eingaben mit der Stiftspitze wie Radierstriche behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-142">If an eraser tip or button is not present, the InkCanvas can be configured to process input from the pen tip as an erase stroke.</span></span>

<span data-ttu-id="bad23-143">In diesem Beispiel überlagert ein [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement ein Hintergrundbild.</span><span class="sxs-lookup"><span data-stu-id="bad23-143">In this example, an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) overlays a background image.</span></span>

> [!NOTE]
> <span data-ttu-id="bad23-144">Ein InkCanvas verfügt standardmäßig über [**Höhe.**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.Height) und [**Breite-**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.Width)-Eigenschaften von null, sofern es sich um ein untergeordnetes Element eines Elements handelt, das die Größe seiner untergeordneten Elemente automatisch festlegt.</span><span class="sxs-lookup"><span data-stu-id="bad23-144">An InkCanvas has default [**Height**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.Height) and [**Width**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.Width) properties of zero, unless it is the child of an element that automatically sizes its child elements.</span></span> 

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

<span data-ttu-id="bad23-145">Diese Serie von Bildern zeigt, wie die Stifteingabe von diesem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="bad23-145">This series of images shows how pen input is rendered by this [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span>

| ![Der leere „InkCanvas“ mit einem Hintergrundbild](images/ink_basic_1_small.png) | ![Der „InkCanvas“ mit letzten Strichen](images/ink_basic_2_small.png) | ![Der „InkCanvas“ mit einem ausradierten Strich](images/ink_basic_3_small.png) |
| --- | --- | ---|
| <span data-ttu-id="bad23-149">Der leere [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) mit einem Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="bad23-149">The blank [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with a background image.</span></span> | <span data-ttu-id="bad23-150">Der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) mit letzten Strichen</span><span class="sxs-lookup"><span data-stu-id="bad23-150">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with ink strokes.</span></span> | <span data-ttu-id="bad23-151">Der [**InkCanvas** ](https://msdn.microsoft.com/library/windows/apps/dn858535) mit einem ausradierten Strich (beachten Sie, dass jeweils der gesamte Strich und nicht nur auf einen Teil davon ausradiert wird).</span><span class="sxs-lookup"><span data-stu-id="bad23-151">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with one stroke erased (note how erase operates on an entire stroke, not a portion).</span></span> |

<span data-ttu-id="bad23-152">Die vom [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement unterstützte Freihandfunktion wird von einem CodeBehind-Objekt mit dem Namen [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="bad23-152">The inking functionality supported by the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control is provided by a code-behind object called the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011).</span></span>

<span data-ttu-id="bad23-153">Für die einfache Freihandeingabe müssen Sie sich nicht mit dem [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011)-Objekt befassen.</span><span class="sxs-lookup"><span data-stu-id="bad23-153">For basic inking, you don't have to concern yourself with the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011).</span></span> <span data-ttu-id="bad23-154">Wenn Sie jedoch das Freihandverhalten des [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements anpassen und konfigurieren möchten, müssen Sie auf das entsprechende **InkPresenter**-Objekt zugreifen.</span><span class="sxs-lookup"><span data-stu-id="bad23-154">However, to customize and configure inking behavior on the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535), you must access its corresponding **InkPresenter** object.</span></span>

## <a name="basic-customization-with-inkpresenter"></a><span data-ttu-id="bad23-155">Einfache Anpassung mit „InkPresenter“</span><span class="sxs-lookup"><span data-stu-id="bad23-155">Basic customization with InkPresenter</span></span>

<span data-ttu-id="bad23-156">Für jedes [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement wird ein [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011)-Objekt instanziiert.</span><span class="sxs-lookup"><span data-stu-id="bad23-156">An [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) object is instantiated with each [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span>

> [!NOTE]
> <span data-ttu-id="bad23-157">Das [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011)-Objekt kann nicht direkt instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-157">The [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) cannot be instantiated directly.</span></span> <span data-ttu-id="bad23-158">Stattdessen erfolgt der Zugriff darauf über die [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Eigenschaft des [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="bad23-158">Instead, it is accessed through the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) property of the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span> 

<span data-ttu-id="bad23-159">Das [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011)-Objekt stellt nicht nur das gesamte Standard-Freihandeingabeverhalten des entsprechenden [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements bereit, sondern bietet auch einen umfassenden Satz von APIs für die zusätzliche Strichanpassung und eine differenzierte Verwaltung des Stifts (standardmäßig und verändert).</span><span class="sxs-lookup"><span data-stu-id="bad23-159">Along with providing all default inking behaviors of its corresponding [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control, the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) provides a comprehensive set of APIs for additional stroke customization and finer-grained management of the pen input (standard and modified).</span></span> <span data-ttu-id="bad23-160">Hierzu zählen Stricheigenschaften, unterstützte Eingabegerätetypen und die Möglichkeit festzulegen, ob die Eingabe vom Objekt verarbeitet oder zur Verarbeitung an die App übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="bad23-160">This includes stroke properties, supported input device types, and whether input is processed by the object or passed to the app for processing.</span></span>

> [!NOTE]
> <span data-ttu-id="bad23-161">Standardmäßige Freihandeingabe (entweder Stiftspitze oder Radiererspitze/-schaltfläche) wird mit einem sekundären Hardware-Angebot nicht geändert, wie z.B. eine Zeichenstift-Drucktaste, rechte Maustaste oder einem ähnlichen Mechanismus.</span><span class="sxs-lookup"><span data-stu-id="bad23-161">Standard ink input (from either pen tip or eraser tip/button) is not modified with a secondary hardware affordance, such as a pen barrel button, right mouse button, or similar mechanism.</span></span> 

<span data-ttu-id="bad23-162">Standardmäßig werden Freihandstriche für nur die Stifteingabe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bad23-162">By default, ink is supported for pen input only.</span></span> <span data-ttu-id="bad23-163">Hier konfigurieren wir [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081), damit Eingabedaten von Stift und Maus als letzte Striche interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-163">Here, we configure the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) to interpret input data from both pen and mouse as ink strokes.</span></span> <span data-ttu-id="bad23-164">Außerdem legen wir einige anfängliche Freihandstrichattribute fest, die zum Rendern von Strichen mit dem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-164">We also set some initial ink stroke attributes used for rendering strokes to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span>

<span data-ttu-id="bad23-165">Legen Sie zum Aktivieren der Maus- und Touch-Freihandeingabe die [**InputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter.InputDeviceTypes)-Eigenschaft des [**InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter) auf die Kombination aus den gewünschten [**CoreInputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.core.coreinputdevicetypes)-Werten fest.</span><span class="sxs-lookup"><span data-stu-id="bad23-165">To enable mouse and touch inking, set the [**InputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter.InputDeviceTypes) property of the [**InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter) to the combination of [**CoreInputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.core.coreinputdevicetypes) values that you want.</span></span>

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

<span data-ttu-id="bad23-166">Attribute für letzte Striche können dynamisch entsprechend den Benutzereinstellungen oder App-Anforderungen festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-166">Ink stroke attributes can be set dynamically to accommodate user preferences or app requirements.</span></span>

<span data-ttu-id="bad23-167">Hier kann der Benutzer aus einer Liste von Freihandfarben auswählen.</span><span class="sxs-lookup"><span data-stu-id="bad23-167">Here, we let a user choose from a list of ink colors.</span></span>

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

<span data-ttu-id="bad23-168">Anschließend behandeln wir Änderungen an der ausgewählten Farbe und aktualisieren die Attribute für letzte Striche entsprechend.</span><span class="sxs-lookup"><span data-stu-id="bad23-168">We then handle changes to the selected color and update the ink stroke attributes accordingly.</span></span>

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

<span data-ttu-id="bad23-169">Diese Bilder zeigen, wie die Stifteingabe vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt verarbeitet und angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="bad23-169">These images shows how pen input is processed and customized by the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081).</span></span>

| ![InkCanvas mit standardmäßigen schwarzen Freihandstrichen](images/ink-basic-custom-1-small.png) | ![InkCanvas mit vom Benutzer ausgewählten roten Freihandstrichen](images/ink-basic-custom-2-small.png) |
| --- | --- |
| <span data-ttu-id="bad23-172">Das [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement mit standardmäßigen schwarzen letzten Strichen</span><span class="sxs-lookup"><span data-stu-id="bad23-172">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with default black ink strokes.</span></span> | <span data-ttu-id="bad23-173">Das [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement mit vom Benutzer ausgewählten roten letzten Strichen</span><span class="sxs-lookup"><span data-stu-id="bad23-173">The [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) with user selected red ink strokes.</span></span> | 

<span data-ttu-id="bad23-174">Um zusätzlich zur Freihandeingabe und zum Löschen weitere Funktionen wie etwa die Strichauswahl bereitzustellen, muss die App bestimmte Eingaben identifizieren, die vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt ohne Verarbeitung zur Behandlung an die App weitergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-174">To provide functionality beyond inking and erasing, such as stroke selection, your app must identify specific input for the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) to pass through unprocessed for handling by your app.</span></span>

## <a name="pass-through-input-for-advanced-processing"></a><span data-ttu-id="bad23-175">Weitergabe der Eingabe für die erweiterte Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="bad23-175">Pass-through input for advanced processing</span></span>

<span data-ttu-id="bad23-176">In der Standardeinstellung verarbeitet [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) sämtliche Eingaben als letzten Strich oder ausradierten Strich, einschließlich der Eingabe, die durch ein sekundäres Hardwareangebot wie einer Zeichenstift-Drucktaste, einer rechten Maustaste oder ähnlichem geändert wird.</span><span class="sxs-lookup"><span data-stu-id="bad23-176">By default, [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) processes all input as either an ink stroke or an erase stroke, including input modified by a secondary hardware affordance such as a pen barrel button, a right mouse button, or similar.</span></span> <span data-ttu-id="bad23-177">Wenn Benutzer diese sekundären Angebote verwenden, erwarten sie jedoch in der Regel zusätzliche Funktionalität oder ein geändertes Verhalten.</span><span class="sxs-lookup"><span data-stu-id="bad23-177">However, users typically expect some additional functionality or modified behavior with these secondary affordances.</span></span>

<span data-ttu-id="bad23-178">In einigen Fällen müssen Sie möglicherweise basierend auf der Benutzerauswahl auf der App-UI auch zusätzliche Freihandfunktionen für Stifte ohne sekundäre Angebote (Funktionalität, die in der Regel nicht der Stiftspitze zugeordnet ist), andere Eingabegerätetypen oder ein auf irgendeine Weise geändertes Verhalten zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="bad23-178">In some cases, you might also need to expose additional functionality for pens without secondary affordances (functionality not usually associated with the pen tip), other input device types, or some type of modified behavior based on a user selection in your app's UI.</span></span>

<span data-ttu-id="bad23-179">Das [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt kann zu diesem Zweck so konfiguriert werden, dass bestimmte Eingaben unverarbeitet bleiben.</span><span class="sxs-lookup"><span data-stu-id="bad23-179">To support this, [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) can be configured to leave specific input unprocessed.</span></span> <span data-ttu-id="bad23-180">Diese unverarbeiteten Eingaben werden dann zur Verarbeitung an die App weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="bad23-180">This unprocessed input is then passed through to your app for processing.</span></span>

### <a name="example---use-unprocessed-input-to-implement-stroke-selection"></a><span data-ttu-id="bad23-181">Beispiel: Verwendung unverarbeiteter Eingaben zum Implementieren der Strichauswahl</span><span class="sxs-lookup"><span data-stu-id="bad23-181">Example - Use unprocessed input to implement stroke selection</span></span> 

<span data-ttu-id="bad23-182">Die Windows Ink-Plattform bietet keine integrierte Unterstützung für die Aktionen, die geänderte Eingaben erfordern, z.B. die Strichauswahl.</span><span class="sxs-lookup"><span data-stu-id="bad23-182">The Windows Ink platform does not provide built-in support for actions that require modified input, such as stroke selection.</span></span> <span data-ttu-id="bad23-183">Zur Unterstützung derartiger Features müssen Sie eine benutzerdefinierte Lösung in Ihren Apps bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bad23-183">To support features like this, you must provide a custom solution in your apps.</span></span> 

<span data-ttu-id="bad23-184">Im folgenden Codebeispiel (der gesamte Code befindet sich in den Dateien MainPage.xaml und MainPage.xaml.cs) werden die Schritte zum Aktivieren der Strichauswahl gezeigt, wenn die Eingabe mit einer Zeichenstift-Drucktaste (oder der rechten Maustaste) geändert wird.</span><span class="sxs-lookup"><span data-stu-id="bad23-184">The following code example (all code is in the MainPage.xaml and MainPage.xaml.cs files) steps through how to enable stroke selection when input is modified with a pen barrel button (or right mouse button).</span></span>

1.  <span data-ttu-id="bad23-185">Zunächst richten wir in „MainPage.xaml“ die Benutzeroberfläche ein.</span><span class="sxs-lookup"><span data-stu-id="bad23-185">First, we set up the UI in MainPage.xaml.</span></span>

    <span data-ttu-id="bad23-186">Hier fügen wir einen Zeichenbereich (unterhalb des [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements) zum Zeichnen der Strichauswahl hinzu.</span><span class="sxs-lookup"><span data-stu-id="bad23-186">Here, we add a canvas (below the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)) to draw the selection stroke.</span></span> <span data-ttu-id="bad23-187">Durch die Verwendung einer eigenen Ebene zum Zeichnen der Strichauswahl bleiben das **InkCanvas**-Steuerelement und dessen Inhalt unverändert.</span><span class="sxs-lookup"><span data-stu-id="bad23-187">Using a separate layer to draw the selection stroke leaves the **InkCanvas** and its content untouched.</span></span>

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

2.  <span data-ttu-id="bad23-189">In „MainPage.xaml.cs“ deklarieren wir eine Reihe von globalen Variablen zum Speichern von Verweisen auf Aspekte der Auswahl-UI.</span><span class="sxs-lookup"><span data-stu-id="bad23-189">In MainPage.xaml.cs, we declare a couple of global variables for keeping references to aspects of the selection UI.</span></span> <span data-ttu-id="bad23-190">Dies gilt insbesondere für den Auswahllassostrich und das umgebende Rechteck, das die ausgewählten Striche hervorhebt.</span><span class="sxs-lookup"><span data-stu-id="bad23-190">Specifically, the selection lasso stroke and the bounding rectangle that highlights the selected strokes.</span></span>

      ```csharp
        // Stroke selection tool.
        private Polyline lasso;
        // Stroke selection area.
        private Rect boundingRect;
      ```

3.  <span data-ttu-id="bad23-191">Anschließend konfigurieren wir das [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt so, dass es Eingabedaten von Stift und Maus als Freihandstriche interpretiert. Zudem legen wir anfängliche Freihandstrichattribute zum Rendern von Freihandstrichen mit dem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement fest.</span><span class="sxs-lookup"><span data-stu-id="bad23-191">Next, we configure the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) to interpret input data from both pen and mouse as ink strokes, and set some initial ink stroke attributes used for rendering strokes to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span>

    <span data-ttu-id="bad23-192">Vor allem geben wir mithilfe der [**InputProcessingConfiguration**](https://msdn.microsoft.com/library/windows/apps/dn948764)-Eigenschaft des [InkPresenter](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekts an, dass alle geänderten Eingaben von der App verarbeitet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bad23-192">Most importantly, we use the [**InputProcessingConfiguration**](https://msdn.microsoft.com/library/windows/apps/dn948764) property of the [InkPresenter](https://msdn.microsoft.com/library/windows/apps/dn899081) to indicate that any modified input should be processed by the app.</span></span> <span data-ttu-id="bad23-193">Geänderte Eingaben geben wir an, indem wir **InputProcessingConfiguration.RightDragAction** den Wert [**InkInputRightDragAction.LeaveUnprocessed**](https://msdn.microsoft.com/library/windows/apps/dn948760) zuweisen.</span><span class="sxs-lookup"><span data-stu-id="bad23-193">Modified input is specified by assigning **InputProcessingConfiguration.RightDragAction** a value of [**InkInputRightDragAction.LeaveUnprocessed**](https://msdn.microsoft.com/library/windows/apps/dn948760).</span></span> <span data-ttu-id="bad23-194">Wenn dieser Wert festgelegt wird, übergibt [InkPresenter](https://msdn.microsoft.com/library/windows/apps/dn899081) eine Reihe von Zeigerereignissen zur Verarbeitung an die [InkUnprocessedInput](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkunprocessedinput)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="bad23-194">When this value is set, the [InkPresenter](https://msdn.microsoft.com/library/windows/apps/dn899081) passes through to the [InkUnprocessedInput](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkunprocessedinput) class, a set of pointer events for you to handle.</span></span>

    <span data-ttu-id="bad23-195">Wir weisen Listener für die nicht verarbeiteten Ereignisse [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/dn914712), [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/dn914711) und [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/dn914713) zu, die vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt weitergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-195">We assign listeners for the unprocessed [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/dn914712), [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/dn914711), and [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/dn914713) events passed through by the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081).</span></span> <span data-ttu-id="bad23-196">Sämtliche Auswahlfunktionalität wird in den Handlern für diese Ereignisse implementiert.</span><span class="sxs-lookup"><span data-stu-id="bad23-196">All selection functionality is implemented in the handlers for these events.</span></span>

    <span data-ttu-id="bad23-197">Schließlich weisen wir Listener für die Ereignisse [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702) und [**StrokesErased**](https://msdn.microsoft.com/library/windows/apps/dn948767) des [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekts zu.</span><span class="sxs-lookup"><span data-stu-id="bad23-197">Finally, we assign listeners for the [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702) and [**StrokesErased**](https://msdn.microsoft.com/library/windows/apps/dn948767) events of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081).</span></span> <span data-ttu-id="bad23-198">Wir verwenden die Handler für diese Ereignisse, um die Auswahl-UI zu bereinigen, wenn ein neuer Strich begonnen oder ein vorhandener Strich ausradiert wird.</span><span class="sxs-lookup"><span data-stu-id="bad23-198">We use the handlers for these events to clean up the selection UI if a new stroke is started or an existing stroke is erased.</span></span>

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

4.  <span data-ttu-id="bad23-200">Anschließend definieren wir Handler für die nicht verarbeiteten Ereignisse [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/dn914712), [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/dn914711) und [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/dn914713), die vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Objekt weitergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-200">We then define handlers for the unprocessed [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/dn914712), [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/dn914711), and [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/dn914713) events passed through by the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081).</span></span>

    <span data-ttu-id="bad23-201">Sämtliche Auswahlfunktionalität, einschließlich des Lassostrichs und des umgebenden Rechtecks, wird in diesen Handlern implementiert.</span><span class="sxs-lookup"><span data-stu-id="bad23-201">All selection functionality is implemented in these handlers, including the lasso stroke and the bounding rectangle.</span></span>

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

5.  <span data-ttu-id="bad23-203">Um den PointerReleased-Ereignishandler abzuschließen, löschen wir sämtlichen Inhalt (den Lassostrich) aus der Auswahlebene und zeichnen dann ein einzelnes umgebendes Rechteck um die letzten Striche, die sich im Lassobereich befinden.</span><span class="sxs-lookup"><span data-stu-id="bad23-203">To conclude the PointerReleased event handler, we clear the selection layer of all content (the lasso stroke) and then draw a single bounding rectangle around the ink strokes encompassed by the lasso area.</span></span>

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

6.  <span data-ttu-id="bad23-205">Schließlich definieren wir Handler für die InkPresenter-Ereignisse [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702) und [**StrokesErased**](https://msdn.microsoft.com/library/windows/apps/dn948767).</span><span class="sxs-lookup"><span data-stu-id="bad23-205">Finally, we define handlers for the [**StrokeStarted**](https://msdn.microsoft.com/library/windows/apps/dn914702) and [**StrokesErased**](https://msdn.microsoft.com/library/windows/apps/dn948767) InkPresenter events.</span></span>

    <span data-ttu-id="bad23-206">Diese beiden rufen einfach die gleiche Bereinigungsfunktion auf, um bei jeder Erkennung eines neuen Strichs die aktuelle Auswahl zu löschen.</span><span class="sxs-lookup"><span data-stu-id="bad23-206">These both just call the same cleanup function to clear the current selection whenever a new stroke is detected.</span></span>

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

7.  <span data-ttu-id="bad23-207">Dies ist die Funktion zum Entfernen der gesamten Auswahl-UI aus dem Auswahlzeichenbereich, wenn ein neuer Strich begonnen oder ein vorhandener Strich ausradiert wird.</span><span class="sxs-lookup"><span data-stu-id="bad23-207">Here's the function to remove all selection UI from the selection canvas when a new stroke is started or an existing stroke is erased.</span></span>

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

## <a name="custom-ink-rendering"></a><span data-ttu-id="bad23-208">Benutzerdefiniertes Rendern von Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="bad23-208">Custom ink rendering</span></span>

<span data-ttu-id="bad23-209">Standardmäßig werden Freihandeingaben in einem Hintergrundthread mit geringer Wartezeit verarbeitet und im Verlauf des Zeichnens „nass“ gerendert.</span><span class="sxs-lookup"><span data-stu-id="bad23-209">By default, ink input is processed on a low-latency background thread and rendered in-progress, or "wet", as it is drawn.</span></span> <span data-ttu-id="bad23-210">Wenn der Strich abgeschlossen ist (der Stift oder Finger wurde angehoben oder die Maustaste losgelassen), wird er im UI-Thread verarbeitet und auf der [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Ebene „trocken“ gerendert (über dem Anwendungsinhalt, wo er die nasse Freihandeingabe ersetzt).</span><span class="sxs-lookup"><span data-stu-id="bad23-210">When the stroke is completed (pen or finger lifted, or mouse button released), the stroke is processed on the UI thread and rendered "dry" to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) layer (above the application content and replacing the wet ink).</span></span>

<span data-ttu-id="bad23-211">Sie können dieses Standardverhalten überschreiben und die Freihandfunktionen durch benutzerdefiniertes Trocknen der Freihandeingabestriche vollständig steuern.</span><span class="sxs-lookup"><span data-stu-id="bad23-211">You can override this default behavior and completely control the inking experience by "custom drying" the wet ink strokes.</span></span> <span data-ttu-id="bad23-212">Das Standardverhalten ist zwar für die meisten Anwendungen in der Regel ausreichend, aber es gibt einige Fälle, in denen möglicherweise ein benutzerdefiniertes Trocknen erforderlich ist. Dazu gehören:</span><span class="sxs-lookup"><span data-stu-id="bad23-212">While the default behavior is typically sufficient for most applications, there are a few cases where custom drying might be required, these include:</span></span>
- <span data-ttu-id="bad23-213">Eine effizientere Verwaltung großer und komplexer Sammlungen von Freihandstrichen</span><span class="sxs-lookup"><span data-stu-id="bad23-213">More efficient management of large, or complex, collections of ink strokes</span></span>
- <span data-ttu-id="bad23-214">Effizientere Unterstützung für Schwenken und Zoomen in großen Freihandzeichenbereichen</span><span class="sxs-lookup"><span data-stu-id="bad23-214">More efficient panning and zooming support on large ink canvases</span></span>
- <span data-ttu-id="bad23-215">Überlappung von Freihand- und anderen Objekte, z.B. Formen oder Text, bei gleichzeitiger Aufrechterhaltung der Z-Reihenfolge</span><span class="sxs-lookup"><span data-stu-id="bad23-215">Interleaving ink and other objects, such as shapes or text, while maintaining z-order</span></span> 
- <span data-ttu-id="bad23-216">Synchrones Trocknen und Umwandeln von Freihandeingaben in eine DirectX-Form (z.B. eine gerade Linie oder Form, die im Anwendungsinhalt gerastert und integriert ist, statt als separate **InkCanvas**-Ebene).</span><span class="sxs-lookup"><span data-stu-id="bad23-216">Drying and converting ink synchronously into a DirectX shape (for example, a straight line or shape rasterized and integrated into application content instead of as a separate **InkCanvas** layer).</span></span>

<span data-ttu-id="bad23-217">Benutzerdefiniertes Trocknen erfordert anstelle des standardmäßigen [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements ein [**IInkD2DRenderer**](https://msdn.microsoft.com/library/mt147263)-Objekt, um die Freihandeingabe zu verwalten und im Direct2D-Gerätekontext der universellen Windows-App zu rendern.</span><span class="sxs-lookup"><span data-stu-id="bad23-217">Custom drying requires an [**IInkD2DRenderer**](https://msdn.microsoft.com/library/mt147263) object to manage the ink input and render it to the Direct2D device context of your Universal Windows app, instead of the default [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span>

<span data-ttu-id="bad23-218">Eine App erstellt durch Aufruf von [**ActivateCustomDrying**](https://msdn.microsoft.com/library/windows/apps/dn922012) (vor dem Laden des [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelements) ein [**InkSynchronizer**](https://msdn.microsoft.com/library/windows/apps/dn903979)-Objekt, um zu definieren, wie ein letzter Strich trocken in einer [**SurfaceImageSource**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Media.Imaging.SurfaceImageSource)- oder [**VirtualSurfaceImageSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.imaging.virtualsurfaceimagesource)-Klasse gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="bad23-218">By calling [**ActivateCustomDrying**](https://msdn.microsoft.com/library/windows/apps/dn922012) (before the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) is loaded), an app creates an [**InkSynchronizer**](https://msdn.microsoft.com/library/windows/apps/dn903979) object to customize how an ink stroke is rendered dry to a [**SurfaceImageSource**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Media.Imaging.SurfaceImageSource) or [**VirtualSurfaceImageSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.imaging.virtualsurfaceimagesource).</span></span> 

<span data-ttu-id="bad23-219">Sowohl [**SurfaceImageSource**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Media.Imaging.SurfaceImageSource) als auch [**VirtualSurfaceImageSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.imaging.virtualsurfaceimagesource) bieten eine gemeinsame DirectX-Oberfläche, auf die Ihre App zeichnen und Inhalte für Ihre Anwendung verfassen kann, obwohl VSIS eine virtuelle Oberfläche bereitstellt, die größer als der Bildschirm ist, um ein leistungsfähiges Schwenken und Zoomen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bad23-219">Both [**SurfaceImageSource**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Media.Imaging.SurfaceImageSource) and [**VirtualSurfaceImageSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.imaging.virtualsurfaceimagesource) provide a DirectX shared surface for your app to draw into and compose into your application's content, although VSIS provides a virtual surface that’s larger than the screen for performant panning and zooming.</span></span> <span data-ttu-id="bad23-220">Da visuelle Aktualisierungen an diesen Oberflächen beim Rendern von Freihandeingaben in beiden mit dem XAML-UI-Thread synchronisiert werden, kann die nasse Freihandeingabe gleichzeitig aus InkCanvas entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="bad23-220">Because visual updates to these surfaces are synchronized with the XAML UI thread, when ink is rendered to either, the wet ink can be removed from the InkCanvas  simultaneously.</span></span> 

<span data-ttu-id="bad23-221">Sie können Freihandeingaben auch an ein [SwapChainPanel](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.swapchainpanel) benutzerdefiniert trocknen, aber die Synchronisierung mit dem UI-Thread kann nicht garantiert werden, und es kommt möglicherweise zu einer Verzögerung zwischen dem Rendern der Freihandeingabe in Ihrem SwapChainPanel und dem Entfernen der Freihandeingabe aus InkCanvas.</span><span class="sxs-lookup"><span data-stu-id="bad23-221">You can also custom dry ink to a [SwapChainPanel](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.swapchainpanel), but synchronization with the UI thread is not guaranteed and there might be a delay between when the ink is rendered to your SwapChainPanel and when ink is removed from the InkCanvas.</span></span>

<span data-ttu-id="bad23-222">Ein vollständiges Beispiel für diese Funktion finden Sie unter [Komplexes Freihandbeispiel](https://go.microsoft.com/fwlink/p/?LinkID=620314).</span><span class="sxs-lookup"><span data-stu-id="bad23-222">For a full example of this functionality, see the [Complex ink sample](https://go.microsoft.com/fwlink/p/?LinkID=620314).</span></span>

> [!NOTE]
> <span data-ttu-id="bad23-223">Benutzerdefiniertes Trocknen und die [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="bad23-223">Custom drying and the [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx)</span></span>  
> <span data-ttu-id="bad23-224">Wenn Ihre App das Standard-Renderverhalten für Freihandeingaben von [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) mit einer benutzerdefinierten Trockenimplementierung außer Kraft setzt, sind die gerenderten Freihandstriche für die InkToolbar nicht mehr verfügbar und die integrierten Löschbefehle der InkToolbar funktionieren nicht wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="bad23-224">If your app overrides the default ink rendering behavior of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) with a custom drying implementation, the rendered ink strokes are no longer available to the InkToolbar and the built-in erase commands of the InkToolbar do not work as expected.</span></span> <span data-ttu-id="bad23-225">Damit Sie Löschfunktionen bereitstellen können, müssen Sie alle Zeigerereignisse verarbeiten, für jeden Strich einen Treffertest ausführen und den integrierten Befehl „Freihand vollständig löschen“ außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="bad23-225">To provide erase functionality, you must handle all pointer events, perform hit-testing on each stroke, and override the built-in "Erase all ink" command.</span></span>

## <a name="other-articles-in-this-section"></a><span data-ttu-id="bad23-226">Andere Artikel in diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="bad23-226">Other articles in this section</span></span>

| <span data-ttu-id="bad23-227">Thema</span><span class="sxs-lookup"><span data-stu-id="bad23-227">Topic</span></span> | <span data-ttu-id="bad23-228">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bad23-228">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="bad23-229">Erkennen von Freihandstrichen</span><span class="sxs-lookup"><span data-stu-id="bad23-229">Recognize ink strokes</span></span>](convert-ink-to-text.md) | <span data-ttu-id="bad23-230">Konvertieren Sie letzte Striche mit der Schrifterkennung in Text oder mit der benutzerdefinierten Erkennung in Formen.</span><span class="sxs-lookup"><span data-stu-id="bad23-230">Convert ink strokes to text using handwriting recognition, or to shapes using custom recognition.</span></span> |
| [<span data-ttu-id="bad23-231">Speichern und Abrufen von letzten Strichen</span><span class="sxs-lookup"><span data-stu-id="bad23-231">Store and retrieve ink strokes</span></span>](save-and-load-ink.md) | <span data-ttu-id="bad23-232">Speichern Sie Freihandstrichdaten mithilfe eingebetteter serialisierter Freihandformat-Metadaten (Ink Serialized Format, ISF) in einer GIF-Datei (Graphics Interchange Format).</span><span class="sxs-lookup"><span data-stu-id="bad23-232">Store ink stroke data in a Graphics Interchange Format (GIF) file using embedded Ink Serialized Format (ISF) metadata.</span></span> |
| [<span data-ttu-id="bad23-233">Hinzufügen eines InkToolbar-Elements zu einer UWP-App für die Freihandeingabe</span><span class="sxs-lookup"><span data-stu-id="bad23-233">Add an InkToolbar to a UWP inking app</span></span>](ink-toolbar.md) | <span data-ttu-id="bad23-234">Fügen Sie einer App für die Freihandeingabe in der universellen Windows-Plattform (UWP) eine Standard-InkToolbar hinzu. Fügen Sie der InkToolbar einen anpassbaren Stift hinzu und binden Sie diesen an eine benutzerdefinierte Definition für den Stift.</span><span class="sxs-lookup"><span data-stu-id="bad23-234">Add a default InkToolbar to a Universal Windows Platform (UWP) inking app, add a custom pen button to the InkToolbar, and bind the custom pen button to a custom pen definition.</span></span> |

## <a name="related-articles"></a><span data-ttu-id="bad23-235">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bad23-235">Related articles</span></span>

* [<span data-ttu-id="bad23-236">Erste Schritte: Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="bad23-236">Get started: Support ink in your UWP app</span></span>](../../get-started/ink-walkthrough.md)
* [<span data-ttu-id="bad23-237">Behandeln von Zeigereingaben</span><span class="sxs-lookup"><span data-stu-id="bad23-237">Handle pointer input</span></span>](handle-pointer-input.md)
* [<span data-ttu-id="bad23-238">Identifizieren von Eingabegeräten</span><span class="sxs-lookup"><span data-stu-id="bad23-238">Identify input devices</span></span>](identify-input-devices.md)

**<span data-ttu-id="bad23-239">APIs</span><span class="sxs-lookup"><span data-stu-id="bad23-239">APIs</span></span>**

* [**<span data-ttu-id="bad23-240">Windows.Devices.Input</span><span class="sxs-lookup"><span data-stu-id="bad23-240">Windows.Devices.Input</span></span>**](https://msdn.microsoft.com/library/windows/apps/br225648)
* [**<span data-ttu-id="bad23-241">Windows.UI.Input.Inking</span><span class="sxs-lookup"><span data-stu-id="bad23-241">Windows.UI.Input.Inking</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208524)
* [**<span data-ttu-id="bad23-242">Windows.UI.Input.Inking.Core</span><span class="sxs-lookup"><span data-stu-id="bad23-242">Windows.UI.Input.Inking.Core</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn958452)

**<span data-ttu-id="bad23-243">Beispiele</span><span class="sxs-lookup"><span data-stu-id="bad23-243">Samples</span></span>**
* [<span data-ttu-id="bad23-244">Lernprogramm „Erste Schritte:” Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="bad23-244">Get Started Tutorial: Support ink in your UWP app</span></span>](https://aka.ms/appsample-ink)
* [<span data-ttu-id="bad23-245">Einfaches Freihandbeispiel (C#/C++)</span><span class="sxs-lookup"><span data-stu-id="bad23-245">Simple ink sample (C#/C++)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620312)
* [<span data-ttu-id="bad23-246">Komplexes Freihandbeispiel (C++)</span><span class="sxs-lookup"><span data-stu-id="bad23-246">Complex ink sample (C++)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620314)
* [<span data-ttu-id="bad23-247">Freihandbeispiel (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="bad23-247">Ink sample (JavaScript)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620308)
* [<span data-ttu-id="bad23-248">Malbuchbeispiel</span><span class="sxs-lookup"><span data-stu-id="bad23-248">Coloring book sample</span></span>](https://aka.ms/cpubsample-coloringbook)
* [<span data-ttu-id="bad23-249">Familiennotizbeispiel</span><span class="sxs-lookup"><span data-stu-id="bad23-249">Family notes sample</span></span>](https://aka.ms/cpubsample-familynotessample)
* [<span data-ttu-id="bad23-250">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="bad23-250">Basic input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="bad23-251">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="bad23-251">Low latency input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="bad23-252">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="bad23-252">User interaction mode sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="bad23-253">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="bad23-253">Focus visuals sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="bad23-254">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="bad23-254">Archive Samples</span></span>**
* [<span data-ttu-id="bad23-255">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="bad23-255">Input: Device capabilities sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="bad23-256">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="bad23-256">Input: XAML user input events sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="bad23-257">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="bad23-257">XAML scrolling, panning, and zooming sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="bad23-258">Eingabe: Gesten und Manipulationen mit GestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="bad23-258">Input: Gestures and manipulations with GestureRecognizer</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=231605)
