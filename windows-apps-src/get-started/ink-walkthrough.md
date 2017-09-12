---
author: kbridge
ms.assetid: 
title: "UWP Academy – Eingabeverfolgung – Unterstützung Freihandeingaben in Ihrer UWP-App"
description: "UWP-Academy Eingabeverfolgung. Ein ausführliches Lernprogramm zur das Hinzufügen der Freihandeingabeunterstützung in Ihrer UWP-App."
keywords: UWP-Academy
ms.author: kbridge
ms.date: 04/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: a70ac88773907edb7e5d02708be19fb9feec01a9
ms.sourcegitcommit: 7540962003b38811e6336451bb03d46538b35671
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2017
---
# <a name="support-ink-in-your-uwp-app"></a><span data-ttu-id="bd6d4-106">Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="bd6d4-106">Support ink in your UWP app</span></span>

![Surface-Stift](images/ink/ink-hero-small.png)  
<span data-ttu-id="bd6d4-108">*Surface-Stift* (zum Kauf im [Microsoft Store](https://aka.ms/purchasesurfacepen) verfügbar).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-108">*Surface Pen* (available for purchase at the [Microsoft Store](https://aka.ms/purchasesurfacepen)).</span></span>

<span data-ttu-id="bd6d4-109">Dieses Lernprogramm zeigt Ihnen, wie Sie eine einfachen Universelle Windows-Plattform-App (UWP-App) erstellen, die das Schreiben und Zeichnen mit Windows Ink unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-109">This tutorial steps through how to create a basic Universal Windows Platform (UWP) app that supports writing and drawing with Windows Ink.</span></span> <span data-ttu-id="bd6d4-110">Wir verwenden Ausschnitte aus einer Beispiel-App, die Sie von GitHub herunterladen können (unter [Beispielcode](#sample-code)), um die in den einzelnen Schritten erläuterten, verschiedenen Features und zugehörigen Windows Ink-APIs (siehe [Komponenten der Windows-Freihandplattform](#components-of-the-windows-ink-platform)) zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-110">We use snippets from a sample app, which you can download from GitHub (see [Sample code](#sample-code)), to demonstrate the various features and associated Windows Ink APIs (see [Components of the Windows Ink platform](#components-of-the-windows-ink-platform)) discussed in each step.</span></span>

<span data-ttu-id="bd6d4-111">Wir konzentrieren uns auf Folgendes:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-111">We focus on the following:</span></span>
* <span data-ttu-id="bd6d4-112">Hinzufügen einer einfachen Freihandeingabe-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-112">Adding basic ink support</span></span>
* <span data-ttu-id="bd6d4-113">Hinzufügen einer Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="bd6d4-113">Adding an ink toolbar</span></span>
* <span data-ttu-id="bd6d4-114">Unterstützung von Schrifterkennung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-114">Supporting handwriting recognition</span></span>
* <span data-ttu-id="bd6d4-115">Unterstützung der Erkennung von grundlegenden Formen</span><span class="sxs-lookup"><span data-stu-id="bd6d4-115">Supporting basic shape recognition</span></span>
* <span data-ttu-id="bd6d4-116">Speichern und Laden von Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="bd6d4-116">Saving and loading ink</span></span>

<span data-ttu-id="bd6d4-117">Weitere Informationen zur Implementierung dieser Features finden Sie unter [Zeichenstift-Interaktionen und Windows Ink in UWP-Apps](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-117">For more detail about implementing these features, see [Pen interactions and Windows Ink in UWP apps](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions).</span></span>

## <a name="introduction"></a><span data-ttu-id="bd6d4-118">Einführung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-118">Introduction</span></span>

<span data-ttu-id="bd6d4-119">Mit Windows Ink können Sie Ihren Kunden fast alle erdenklichen schriftlichen Erfahrungen bieten, von schnellen handgeschriebenen Notizen und Anmerkungen bis zu Whiteboard-Demos, und von Architektur- und Ingenieurzeichnungen bis zu persönliche Meisterwerke.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-119">With Windows Ink, you can provide your customers with the digital equivalent of almost any pen-and-paper experience imaginable, from quick, handwritten notes and annotations to whiteboard demos, and from architectural and engineering drawings to personal masterpieces.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd6d4-120">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="bd6d4-120">Prerequisites</span></span>

* <span data-ttu-id="bd6d4-121">Einen Computer (oder einen virtuellen Computer) mit der aktuellen Version von Windows10.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-121">A computer (or a virtual machine) running the current version of Windows 10</span></span>
* [<span data-ttu-id="bd6d4-122">Visual Studio2017 und die RS2 SDK</span><span class="sxs-lookup"><span data-stu-id="bd6d4-122">Visual Studio 2017 and the RS2 SDK</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="bd6d4-123">Windows 10 SDK (10.0.15063.0)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-123">Windows 10 SDK (10.0.15063.0)</span></span>](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)
* <span data-ttu-id="bd6d4-124">Wenn Sie noch keine Erfahrung mit der App-Entwicklung in der Universellen Windows-Plattform (UWP) mit Visual Studio haben, werfen Sie einen Blick in diese Themen, bevor Sie dieses Lernprogramm starten:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-124">If you're new to Universal Windows Platform (UWP) app development with Visual Studio, have a look through these topics before you start this tutorial:</span></span>  
    * [<span data-ttu-id="bd6d4-125">Vorbereiten</span><span class="sxs-lookup"><span data-stu-id="bd6d4-125">Get set up</span></span>](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up)
    * [<span data-ttu-id="bd6d4-126">Erstellen der App „Hello, world“ (XAML)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-126">Create a "Hello, world" app (XAML)</span></span>](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
* <span data-ttu-id="bd6d4-127">**[OPTIONAL]** Ein digitaler Stift und ein Computer mit einer Anzeige, die die Eingaben eines digitalen Stifts unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-127">**[OPTIONAL]** A digital pen and a computer with a display that supports input from that digital pen.</span></span>  
   > [!NOTE] 
   > <span data-ttu-id="bd6d4-128">Während Windows Ink das Zeichnen mit einer Maus und Fingereingabe (erfahren in Schritt3 dieses Lernprogramms wie dies funktioniert) für eine optimale Windows Ink-Erfahrung unterstützt, empfehlen wir, dass Sie über einen digitalen Stift und einem Computer mit einer Anzeige verfügen, die die Eingaben von diesem digitalen Stift unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-128">While Windows Ink can support drawing with a mouse and touch (we show how to do this in Step 3 of this tutorial) for an optimal Windows Ink experience, we recommend that you have a digital pen and a computer with a display that supports input from that digital pen.</span></span>

## <a name="sample-code"></a><span data-ttu-id="bd6d4-129">Beispielcode</span><span class="sxs-lookup"><span data-stu-id="bd6d4-129">Sample code</span></span>
<span data-ttu-id="bd6d4-130">In diesem Lernprogramm verwenden wir eine Beispiels-App für die Freihandeingabe, um die erläuterten Konzepte und Funktionen zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-130">Throughout this tutorial, we use a sample ink app to demonstrate the concepts and functionality discussed.</span></span>

<span data-ttu-id="bd6d4-131">Laden Sie dieses Visual Studio-Beispiel und den Quellecode von [GitHub](https://github.com/) unter [Windows-Appsample-Erste-Schritte-Freihandbeispiel](https://aka.ms/appsample-ink) herunter:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-131">Download this Visual Studio sample and source code from [GitHub](https://github.com/) at [windows-appsample-get-started-ink sample](https://aka.ms/appsample-ink):</span></span>

1. <span data-ttu-id="bd6d4-132">Wählen Sie die grüne **Klonen oder herunterladen**-Schaltfläche aus</span><span class="sxs-lookup"><span data-stu-id="bd6d4-132">Select the green **Clone or download** button</span></span>  
![Klonen des Repositorys](images/ink/ink-clone.png)
2. <span data-ttu-id="bd6d4-134">Wenn Sie ein GitHub-Konto haben, können Sie das Repository auf Ihrem lokalen Computer mit der Option **In Visual Studio öffnen** klonen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-134">If you have a GitHub account, you can clone the repo to your local machine by choosing **Open in Visual Studio**</span></span> 
3. <span data-ttu-id="bd6d4-135">Wenn Sie kein GitHub-Konto haben, oder wenn Sie einfach eine lokale Kopie des Projekts möchten, wählen Sie **Herunterladen der ZIP-Datei** (Sie müssen regelmäßig auf neues Updates prüfen)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-135">If you don't have a GitHub account, or you just want a local copy of the project, choose **Download ZIP** (you'll have to check back regularly to download the latest updates)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd6d4-136">Der Großteil des Codes im Beispiel ist als Kommentar formatiert.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-136">Most of the code in the sample is commented out.</span></span> <span data-ttu-id="bd6d4-137">Bei den einzelnen Schritten werden Sie aufgefordert, die Kommentare der verschiedenen Codeabschnitte zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-137">As we go through each step, you'll be asked to uncomment various sections of the code.</span></span> <span data-ttu-id="bd6d4-138">Markieren Sie einfach in Visual Studio die Codezeilen und drücken Sie STRG+K und anschließend STRG + U.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-138">In Visual Studio, just highlight the lines of code, and press CTRL-K and then CTRL-U.</span></span>

## <a name="components-of-the-windows-ink-platform"></a><span data-ttu-id="bd6d4-139">Komponenten der WindowsInk-Plattform</span><span class="sxs-lookup"><span data-stu-id="bd6d4-139">Components of the Windows Ink platform</span></span>

<span data-ttu-id="bd6d4-140">Diese Objekte bieten den Großteil der Freihandfunktionen für UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-140">These objects provide the bulk of the inking experience for UWP apps.</span></span>

| <span data-ttu-id="bd6d4-141">Komponente</span><span class="sxs-lookup"><span data-stu-id="bd6d4-141">Component</span></span> | <span data-ttu-id="bd6d4-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-142">Description</span></span> |
| --- | --- |
| [**<span data-ttu-id="bd6d4-143">InkCanvas</span><span class="sxs-lookup"><span data-stu-id="bd6d4-143">InkCanvas</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) | <span data-ttu-id="bd6d4-144">Ein XAML-UI-Plattformsteuerelement, das standardmäßig alle Eingaben von einem Stift als Freihandstriche oder Löschen von Freihandstrichen empfängt und anzeigt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-144">A XAML UI platform control that, by default, receives and displays all input from a pen as either an ink stroke or an erase stroke.</span></span> |
| [**<span data-ttu-id="bd6d4-145">InkPresenter</span><span class="sxs-lookup"><span data-stu-id="bd6d4-145">InkPresenter</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn922011) | <span data-ttu-id="bd6d4-146">Ein CodeBehind-Objekt, das zusammen mit einem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement instanziiert wird (über die [**InkCanvas.InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.inkcanvas#Windows_UI_Xaml_Controls_InkCanvas_InkPresenter)-Eigenschaft verfügbar gemacht).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-146">A code-behind object, instantiated along with an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control (exposed through the [**InkCanvas.InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.inkcanvas#Windows_UI_Xaml_Controls_InkCanvas_InkPresenter) property).</span></span> <span data-ttu-id="bd6d4-147">Dieses Objekt stellt alle Standardfreihandfunktionen bereit, die vom [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)-Steuerelement zur Verfügung gestellt werden, sowie einen umfassenden Satz von APIs für zusätzliche Anpassung und Personalisierung.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-147">This object provides all default inking functionality exposed by the [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), along with a comprehensive set of APIs for additional customization and personalization.</span></span> |
| [**<span data-ttu-id="bd6d4-148">InkToolbar</span><span class="sxs-lookup"><span data-stu-id="bd6d4-148">InkToolbar</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) | <span data-ttu-id="bd6d4-149">Ein XAML-UI-Plattformsteuerelement enthält eine anpassbare und erweiterbare Sammlung von Schaltflächen, die Features für Freihandeingaben in einem verknüpften [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)-Steuerelement aktivieren.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-149">A XAML UI platform control containing a customizable and extensible collection of buttons that activate ink-related features in an associated [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas).</span></span> |
| [**<span data-ttu-id="bd6d4-150">IInkD2DRenderer</span><span class="sxs-lookup"><span data-stu-id="bd6d4-150">IInkD2DRenderer</span></span>**](https://msdn.microsoft.com/library/mt147263)<br/><span data-ttu-id="bd6d4-151">Diese Funktionalität wird von uns hier nicht erläutert. Weitere Informationen finden Sie unter [Komplexes Freihandbeispiel](http://go.microsoft.com/fwlink/p/?LinkID=620314).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-151">We do not cover this functionality here, for more information, see the [Complex ink sample](http://go.microsoft.com/fwlink/p/?LinkID=620314).</span></span> | <span data-ttu-id="bd6d4-152">Ermöglicht das Rendern von Freihandstrichen im angegebenen Direct2D-Gerätekontext einer universellen Windows-App statt im standardmäßigen [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-152">Enables the rendering of ink strokes onto the designated Direct2D device context of a Universal Windows app, instead of the default [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span> |

## <a name="step-1-run-the-sample"></a><span data-ttu-id="bd6d4-153">Schritt1: Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="bd6d4-153">Step 1: Run the sample</span></span>

<span data-ttu-id="bd6d4-154">Nachdem Sie die RadialController-Beispiel-App heruntergeladen haben, stellen Sie sicher, dass sie ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-154">After you've downloaded the RadialController sample app, verify that it runs:</span></span>
1. <span data-ttu-id="bd6d4-155">Öffnen Sie das Beispielprojekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-155">Open the sample project in Visual Studio.</span></span>
2. <span data-ttu-id="bd6d4-156">Legen Sie das **Lösungsplattformen**-Dropdownmenü für eine nicht ARM-Auswahl fest.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-156">Set the **Solution Platforms** dropdown to a non-ARM selection.</span></span>
3. <span data-ttu-id="bd6d4-157">Drücken Sie F5, um zu kompilieren, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-157">Press F5 to compile, deploy, and run.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="bd6d4-158">Alternativ können Sie **Debuggen** > **Debuggen starten** Menüelement auswählen, oder wählen Sie die hier dargestellte Ausführungsschaltfläche für die **Lokale Maschine** aus.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-158">Alternatively, you can select **Debug** > **Start debugging** menu item, or select the **Local Machine** Run button shown here.</span></span>
   > ![Visual Studio-Schaltfläche „Projekt erstellen”](images/ink/ink-vsrun.png)

<span data-ttu-id="bd6d4-160">Das App-Fenster wird geöffnet und nach einem Begrüßungsbildschirm wird der Startbildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-160">The app window opens, and after a splash screen appears for a few seconds, you’ll see this initial screen.</span></span>

![Leere App](images/ink/ink-app-step1-empty.png)

<span data-ttu-id="bd6d4-162">OK, nun haben wir die grundlegende UWP-App, die wir im verbleibenden Teil dieses Lernprogramms verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-162">Okay, we now have the basic UWP app that we’ll use throughout the rest of this tutorial.</span></span> <span data-ttu-id="bd6d4-163">In den folgenden Schritten fügen wir unsere Freihandfunktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-163">In the following steps, we add our ink functionality.</span></span>

## <a name="step-2-use-inkcanvas-to-support-basic-inking"></a><span data-ttu-id="bd6d4-164">Schritt2: Verwendung von InkCanvas zur Unterstützung von einfachen Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="bd6d4-164">Step 2: Use InkCanvas to support basic inking</span></span>

<span data-ttu-id="bd6d4-165">Vielleicht haben Sie bereits bemerkt, dass Sie in der App in ihrer ursprünglichen Form nicht mit dem Stift zeichnen können (auch wenn Sie den Stift als ein Standardzeigergerät für die Interaktion mit der App festgelegt haben).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-165">Perhaps you've probably already noticed that the app, in it's initial form, doesn't let you draw anything with the pen (although you can use the pen as a standard pointer device to interact with the app).</span></span> 

<span data-ttu-id="bd6d4-166">Beheben wir dieses Problem in diesem Schritt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-166">Let's fix that little shortcoming in this step.</span></span>

<span data-ttu-id="bd6d4-167">Um einfaches Freihandzeichen hinzuzufügen, platzieren Sie einfach ein [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-UWP-Steuerelement auf der entsprechenden Seite in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-167">To add basic inking functionality, just place an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) UWP platform control on the appropriate page in your app.</span></span>

> [!NOTE]
> <span data-ttu-id="bd6d4-168">Ein InkCanvas verfügt standardmäßig über [**Höhe.**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Height) und [**Breite-**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Width)-Eigenschaften von null, sofern es sich um ein untergeordnetes Element eines Elements handelt, das die Größe seiner untergeordneten Elemente automatisch festlegt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-168">An InkCanvas has default [**Height**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Height) and [**Width**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Width) properties of zero, unless it is the child of an element that automatically sizes its child elements.</span></span> 

### <a name="in-the-sample"></a><span data-ttu-id="bd6d4-169">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-169">In the sample:</span></span>
1. <span data-ttu-id="bd6d4-170">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-170">Open the MainPage.xaml.cs file.</span></span>
2. <span data-ttu-id="bd6d4-171">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („// Schritt2: Verwendung InkCanvas für die Unterstützung einfacher Freihandeingabe”).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-171">Find the code marked with the title of this step ("// Step 2: Use InkCanvas to support basic inking").</span></span>
3. <span data-ttu-id="bd6d4-172">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-172">Uncomment the following lines.</span></span> <span data-ttu-id="bd6d4-173">(Diese Verweise sind für die Funktionen erforderlich, die in den nachfolgenden Schritten verwendet werden).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-173">(These references are required for the functionality used in the subsequent steps).</span></span>  

``` csharp
    using Windows.UI.Input.Inking;
    using Windows.UI.Input.Inking.Analysis;
    using Windows.UI.Xaml.Shapes;
    using Windows.Storage.Streams;
```

4. <span data-ttu-id="bd6d4-174">Öffnen Sie die Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-174">Open the MainPage.xaml file.</span></span>
5. <span data-ttu-id="bd6d4-175">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt2: Einfache Freihandeingabe mit InkCanvas -->”).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-175">Find the code marked with the title of this step ("\<!-- Step 2: Basic inking with InkCanvas -->").</span></span>
6. <span data-ttu-id="bd6d4-176">Entfernen Sie aus der folgenden Zeile die Kommentare.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-176">Uncomment the following line.</span></span>  

``` xaml
    <InkCanvas x:Name="inkCanvas" />
```

<span data-ttu-id="bd6d4-177">Das war's.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-177">That's it!</span></span> 

<span data-ttu-id="bd6d4-178">Führen Sie nun erneut die App aus.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-178">Now run the app again.</span></span> <span data-ttu-id="bd6d4-179">Machen Sie nun eine Skizze, schreiben Sie Ihren Namen, oder (wenn Sie einen Spiegel zur Hand oder ein sehr ausgeprägtes Gedächtnis haben) zeichnen Sie ein Selbstporträt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-179">Go ahead and scribble, write your name, or (if you're holding a mirror or have a very good memory) draw your self-portrait.</span></span>

![Einfache Freihandeingabe](images/ink/ink-app-step1-name.png)

## <a name="step-3-support-inking-with-touch-and-mouse"></a><span data-ttu-id="bd6d4-181">Schritt3: Unterstützung von Freihandzeichnen mit Touch- und Mauseingabe</span><span class="sxs-lookup"><span data-stu-id="bd6d4-181">Step 3: Support inking with touch and mouse</span></span>

<span data-ttu-id="bd6d4-182">Sie werden feststellen, dass Freihandeingaben standardmäßig nur für Stifteingaben unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-182">You'll notice that, by default, ink is supported for pen input only.</span></span> <span data-ttu-id="bd6d4-183">Wenn Sie versuchen, mit Ihrem Finger, Maus oder Ihrem Touchpad zu schreiben oder zu zeichnen, werden Sie enttäuscht sein.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-183">If you try to write or draw with your finger, your mouse, or your touchpad, you'll be disappointed.</span></span>

<span data-ttu-id="bd6d4-184">Um das zu beheben, müssen Sie eine zweite Codezeile hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-184">To turn that frown upside down , you need to add a second line of code.</span></span> <span data-ttu-id="bd6d4-185">Dieses Mal befindet sie sich im CodeBehind für die XAML-Datei, in der Sie Ihren [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-185">This time it’s in the code-behind for the XAML file in which you declared your [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas).</span></span> 

<span data-ttu-id="bd6d4-186">In diesem Schritt führen wir das [**InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter) -Objekt ein, das eine differenziertere Verwaltung der Eingabe, Verarbeitung und Rendering der Freihandeingabe (standard und verändert) auf Ihrem [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) bietet.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-186">In this step, we introduce the [**InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter) object, which provides finer-grained management of the input, processing, and rendering of ink input (standard and modified) on your [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas).</span></span>

> [!NOTE]
> <span data-ttu-id="bd6d4-187">Standardmäßige Freihandeingabe (Stiftspitze oder Radiererspitze/-schaltfläche) wird mit einem sekundären Hardware-Angebot nicht geändert, wie z.B. eine Zeichenstift-Drucktaste, rechte Maustaste oder einem ähnlichen Mechanismus.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-187">Standard ink input (pen tip or eraser tip/button) is not modified with a secondary hardware affordance, such as a pen barrel button, right mouse button, or similar mechanism.</span></span> 

<span data-ttu-id="bd6d4-188">Legen Sie zum Aktivieren der Maus- und Touch-Freihandeingabe die [**InputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter#Windows_UI_Input_Inking_InkPresenter_InputDeviceTypes)-Eigenschaft des [**InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter) auf die Kombination aus den gewünschten [**CoreInputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.core.coreinputdevicetypes)-Werten fest.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-188">To enable mouse and touch inking, set the [**InputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter#Windows_UI_Input_Inking_InkPresenter_InputDeviceTypes) property of the [**InkPresenter**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.inking.inkpresenter) to the combination of [**CoreInputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.core.coreinputdevicetypes) values that you want.</span></span>

### <a name="in-the-sample"></a><span data-ttu-id="bd6d4-189">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-189">In the sample:</span></span>
1. <span data-ttu-id="bd6d4-190">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-190">Open the MainPage.xaml.cs file.</span></span>
2. <span data-ttu-id="bd6d4-191">Finden Sie den Code, der mit dem Titel dieses Schrittsgekennzeichnet ist („// Schritt3: Freihandzeichnen mit Touch- und Mauseingabe unterstützen”).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-191">Find the code marked with the title of this step ("// Step 3: Support inking with touch and mouse").</span></span>
3. <span data-ttu-id="bd6d4-192">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-192">Uncomment the following lines.</span></span>  

``` csharp
    inkCanvas.InkPresenter.InputDeviceTypes =
        Windows.UI.Core.CoreInputDeviceTypes.Mouse | 
        Windows.UI.Core.CoreInputDeviceTypes.Touch | 
        Windows.UI.Core.CoreInputDeviceTypes.Pen;
```

<span data-ttu-id="bd6d4-193">Führen Sie die App erneut aus und Sie werden feststellen, dass Sie endlich mit Ihren Fingern auf dem Computerbildschirm zeichnen können!</span><span class="sxs-lookup"><span data-stu-id="bd6d4-193">Run the app again and you'll find that all your finger-painting-on-a-computer-screen dreams have come true!</span></span>

> [!NOTE]
> <span data-ttu-id="bd6d4-194">Sie müssen beim Festlegen von Eingabegerätetypen die Unterstützung für jeden spezifischen Eingabetyp angeben (einschließlich Stift), da diese Einstellung standardmäßig die [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)-Einstellung überschreibt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-194">When specifying input device types, you must indicate support for each specific input type (including pen), because setting this property overrides the default [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) setting.</span></span>

## <a name="step-4-add-an-ink-toolbar"></a><span data-ttu-id="bd6d4-195">Schritt4: Hinzufügen einer Freihandsymbolleiste</span><span class="sxs-lookup"><span data-stu-id="bd6d4-195">Step 4: Add an ink toolbar</span></span>

<span data-ttu-id="bd6d4-196">Die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) ist ein UWP-Steuerelement, das eine anpassbare und erweiterbare Sammlung an Schaltflächen für die Aktivierung von freihandbezogenen Funktionen bietet.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-196">The [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) is a UWP platform control that provides a customizable and extensible collection of buttons for activating ink-related features.</span></span> 

<span data-ttu-id="bd6d4-197">Die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) enthält standardmäßig eine Reihe von Schaltflächen, mit denen Benutzer schnell zwischen einem Kugelschreiber, Stift, Textmarker oder Radierer wechseln können, die alle zusammen mit einer Schablone (Lineal oder Winkelmesser) verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-197">By default, the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) includes a basic set of buttons that let users quickly select between a pen, a pencil, a highlighter, or an eraser, any of which can be used together with a stencil (ruler or protractor).</span></span> <span data-ttu-id="bd6d4-198">Mit den Schaltflächen Kugelschreiber, Bleistift und Textmarker bieten auch jeweils ein Flyout zum Auswählen von Farben und Strichgrößen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-198">The pen, pencil, and highlighter buttons each also provide a flyout for selecting ink color and stroke size.</span></span>

<span data-ttu-id="bd6d4-199">Um eine standardmäßige [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) zu einer App für die Freihandeingabe hinzuzufügen, platzieren Sie sie einfach auf derselben Seite wie Ihr [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), und verbinden Sie die beiden Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-199">To add a default [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) to an inking app, just place it on the same page as your [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) and associate the two controls.</span></span>

### <a name="in-the-sample"></a><span data-ttu-id="bd6d4-200">Im Beispiel</span><span class="sxs-lookup"><span data-stu-id="bd6d4-200">In the sample</span></span>
1. <span data-ttu-id="bd6d4-201">Öffnen Sie die Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-201">Open the MainPage.xaml file.</span></span>
2. <span data-ttu-id="bd6d4-202">Suchen Sie den Code, mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt4: Hinzufügen einer Symbolleiste-->”).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-202">Find the code marked with the title of this step ("\<!-- Step 4: Add an ink toolbar -->").</span></span>
3. <span data-ttu-id="bd6d4-203">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-203">Uncomment the following lines.</span></span>  

``` xaml
    <InkToolbar x:Name="inkToolbar" 
                        VerticalAlignment="Top" 
                        Margin="10,0,10,0"
                        TargetInkCanvas="{x:Bind inkCanvas}">
    </InkToolbar>
```

> [!NOTE]
> <span data-ttu-id="bd6d4-204">Um die Benutzeroberfläche und den Code so übersichtlich und einfach wie möglich zu gestalten, verwenden wir ein einfaches Rasterlayout und deklarieren die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) nach dem [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) in einer Rasterzeile.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-204">To keep the UI and code as uncluttered and simple as possible, we use a basic Grid layout and declare the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) after the [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) in a grid row.</span></span> <span data-ttu-id="bd6d4-205">Wenn Sie sie vor dem [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) deklarieren, wird die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) als erstes unterhalb der Canvas und für den Benutzer unzugänglich gerendert.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-205">If you declare it before the [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) is rendered first, below the canvas and inaccessible to the user.</span></span>  

<span data-ttu-id="bd6d4-206">Führen Sie jetzt die App erneut aus, um die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) anzuzeigen und einige dieser Tools auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-206">Now run the app again to see the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) and try out some of the tools.</span></span>

![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/ink/ink-inktoolbar-default.png)

### <a name="challenge-add-a-custom-button"></a><span data-ttu-id="bd6d4-208">Die Herausforderung: Hinzufügen einer benutzerdefinierten Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="bd6d4-208">Challenge: Add a custom button</span></span>
<table class="wdg-noborder">
<tr>
 <td width=125><img src="images/challenge-icon.png"></td>
    <td width=500><span data-ttu-id="bd6d4-209">Hier ist ein Beispiel für eine benutzerdefinierte <strong><a href="https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar">InkToolbar</a></strong> (von Skizzenblock im Windows Ink-Arbeitsbereich).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-209">Here's an example of a custom <strong><a href="https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar">InkToolbar</a></strong> (from Sketchpad in the Windows Ink Workspace).</span></span>

![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/ink/ink-inktoolbar-sketchpad.png)

<span data-ttu-id="bd6d4-211">Weitere Informationen zur Anpassung einer [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) finden Sie unter [Hinzufügen einer InkToolbar zu einer Universellen Windows-Platform-App (UWP) für die Freihandeingabe](https://docs.microsoft.com/en-us/windows/uwp/input-and-devices/ink-toolbar)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-211">For more details about customizing an [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar), see [Add an InkToolbar to a Universal Windows Platform (UWP) inking app](https://docs.microsoft.com/en-us/windows/uwp/input-and-devices/ink-toolbar).</span></span>

</tr>
</table>

## <a name="step-5-support-handwriting-recognition"></a><span data-ttu-id="bd6d4-212">Schritt5: Unterstützung der Handschrifterkennung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-212">Step 5: Support handwriting recognition</span></span>

<span data-ttu-id="bd6d4-213">Nun, da Sie in Ihrer App zeichnen und schreiben können, versuchen wir aus diesen Skizzen etwas Nutzen zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-213">Now that you can write and draw in your app, let's try to do something useful with those scribbles.</span></span>

<span data-ttu-id="bd6d4-214">In diesem Schritt verwenden wir die Handschrifterkennungsfunktionen von Windows Ink, um das von Ihnen Geschriebene zu entziffern.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-214">In this step, we use the handwriting recognition features of Windows Ink to try to decipher what you've written.</span></span>

> [!NOTE]
> <span data-ttu-id="bd6d4-215">Die Handschrifterkennung kann anhand der **Stift & Windows Ink**-Einstellungen verbessert werden:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-215">Handwriting recognition can be improved through the **Pen & Windows Ink** settings:</span></span>
> 1. <span data-ttu-id="bd6d4-216">Öffnen Sie das Startmenü und wählen Sie **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-216">Open the Start menu and select **Settings**.</span></span>
> 2. <span data-ttu-id="bd6d4-217">Wählen Sie auf dem Bildschirm „Einstellungen” **Geräte** > **Stift & Windows Ink**.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-217">From the Settings screen select **Devices** > **Pen & Windows Ink**.</span></span>
> ![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/ink/ink-settings-large.png)
> 3. <span data-ttu-id="bd6d4-219">Wählen Sie **Meine Handschrift erkennen**, um das Dialogfeld **Handschriftanpassung** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-219">Select **Get to know my handwriting** to open the **Handwriting Personalization** dialog.</span></span>
> ![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/ink/ink-settings-handwritingpersonalization-large.png)

### <a name="in-the-sample"></a><span data-ttu-id="bd6d4-221">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-221">In the sample:</span></span>
1. <span data-ttu-id="bd6d4-222">Öffnen Sie die Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-222">Open the MainPage.xaml file.</span></span>
2. <span data-ttu-id="bd6d4-223">Suchen Sie den Code, mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt5: schrifterkennung Unterstützung-->”).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-223">Find the code marked with the title of this step ("\<!-- Step 5: Support handwriting recognition -->").</span></span>
3. <span data-ttu-id="bd6d4-224">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-224">Uncomment the following lines.</span></span>  

``` xaml
    <Button x:Name="recognizeText" 
            Content="Recognize text"  
            Grid.Row="0" Grid.Column="0"
            Margin="10,10,10,10"
            Click="recognizeText_ClickAsync"/>
    <TextBlock x:Name="recognitionResult" 
                Text="Recognition results: "
                VerticalAlignment="Center" 
                Grid.Row="0" Grid.Column="1"
                Margin="50,0,0,0" />
```

4. <span data-ttu-id="bd6d4-225">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-225">Open the MainPage.xaml.cs file.</span></span>
5. <span data-ttu-id="bd6d4-226">Suchen Sie den Code, mit dem Titel dieses Schritts gekennzeichnet ist („Schritt5: schrifterkennung Unterstützung”).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-226">Find the code marked with the title of this step (" Step 5: Support handwriting recognition").</span></span>
6. <span data-ttu-id="bd6d4-227">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-227">Uncomment the following lines.</span></span>  

- <span data-ttu-id="bd6d4-228">Dies sind die globalen Variablen, die für diesen Schritt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-228">These are the global variables required for this step.</span></span>

``` csharp
    InkAnalyzer analyzerText = new InkAnalyzer();
    IReadOnlyList<InkStroke> strokesText = null;
    InkAnalysisResult resultText = null;
    IReadOnlyList<IInkAnalysisNode> words = null;
```

- <span data-ttu-id="bd6d4-229">Dies ist der Handler für die Schaltfläche **Text erkennen**, wo die Verarbeitung der Erkennung erfolgt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-229">This is the handler for the **Recognize text** button, where we do the recognition processing.</span></span>

``` csharp
    private async void recognizeText_ClickAsync(object sender, RoutedEventArgs e)
    {
        strokesText = inkCanvas.InkPresenter.StrokeContainer.GetStrokes();
        // Ensure an ink stroke is present.
        if (strokesText.Count > 0)
        {
            analyzerText.AddDataForStrokes(strokesText);

            resultText = await analyzerText.AnalyzeAsync();

            if (resultText.Status == InkAnalysisStatus.Updated)
            {
                words = analyzerText.AnalysisRoot.FindNodes(InkAnalysisNodeKind.InkWord);
                foreach (var word in words)
                {
                    InkAnalysisInkWord concreteWord = (InkAnalysisInkWord)word;
                    foreach (string s in concreteWord.TextAlternates)
                    {
                        recognitionResult.Text += s;
                    }
                }
            }
            analyzerText.ClearDataForAllStrokes();
        }
    }
```

7. <span data-ttu-id="bd6d4-230">Führen Sie die App erneut aus, schreiben Sie etwas und klicken Sie dann auf die Schaltfläche **Text erkennen**.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-230">Run the app again, write something, and then click the **Recognize text** button</span></span>
8. <span data-ttu-id="bd6d4-231">Die Ergebnisse der Erkennung werden neben der Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-231">The results of the recognition are displayed beside the button</span></span>

### <a name="challenge-1-international-recognition"></a><span data-ttu-id="bd6d4-232">Herausforderung 1: Internationale Erkennung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-232">Challenge 1: International recognition</span></span>
<table class="wdg-noborder">
<tr>
 <td width=125><img src="images/challenge-icon.png"></td>
    <td width=500><p><span data-ttu-id="bd6d4-233">Windows Ink unterstützt Texterkennung für viele der von Windows unterstützten Sprachen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-233">Windows Ink supports text recognition for many of the of the languages supported by Windows.</span></span> <span data-ttu-id="bd6d4-234">Jedes Sprachpaket enthält ein Schrifterkennungsmodul, das mit dem Language Pack installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-234">Each language pack includes a handwriting recognition engine that can be installed with the language pack.</span></span></p>
    <p><span data-ttu-id="bd6d4-235">Zielen Sie auf eine bestimmte Sprache ab, indem Sie die installierten Handschrifterkennungsmodule abfragen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-235">Target a specific language by querying the installed handwriting recognition engines.</span></span></p>
    <p><span data-ttu-id="bd6d4-236">Weitere Informationen zur internationalen Handschrifterkennung finden Sie unter <a href="https://docs.microsoft.com/windows/uwp/input-and-devices/convert-ink-to-text">Windows Ink-Striche als Text erkennen</a>.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-236">For more details about international handwriting recognition, see <a href="https://docs.microsoft.com/windows/uwp/input-and-devices/convert-ink-to-text">Recognize Windows Ink strokes as text</a>.</span></span></p>
</tr>
</table>

### <a name="challenge-2-dynamic-recognition"></a><span data-ttu-id="bd6d4-237">Herausforderung 2: Dynamische Erkennung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-237">Challenge 2: Dynamic recognition</span></span>
<table class="wdg-noborder">
<tr>
 <td width=125><img src="images/challenge-icon.png"></td>
    <td width=500><p><span data-ttu-id="bd6d4-238">Für dieses Lernprogramm muss eine Schaltfläche zum Initiieren der Erkennung gedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-238">For this tutorial, we require that a button be pressed to initiate recognition.</span></span> <span data-ttu-id="bd6d4-239">Sie können auch dynamische Erkennung mithilfe einer einfachen Timing-Funktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-239">You can also perform dynamic recognition by using a basic timing function.</span></span></p>

<span data-ttu-id="bd6d4-240">Weitere Informationen zur dynamischen Handschrifterkennung finden Sie unter [Windows Ink-Striche als Text erkennen](https://docs.microsoft.com/en-us/windows/uwp/input-and-devices/convert-ink-to-text).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-240">For more details about dynamic recognition, see [Recognize Windows Ink strokes as text](https://docs.microsoft.com/en-us/windows/uwp/input-and-devices/convert-ink-to-text).</span></span>
</tr>
</table>

## <a name="step-6-recognize-shapes"></a><span data-ttu-id="bd6d4-241">Schritt6: Erkennen von Formen</span><span class="sxs-lookup"><span data-stu-id="bd6d4-241">Step 6: Recognize shapes</span></span>

<span data-ttu-id="bd6d4-242">OK, nun können Sie also Ihre handschriftlichen Notizen in etwas umwandeln, das etwas lesbarer ist.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-242">Ok, so now you can convert your handwritten notes into something a little more legible.</span></span> <span data-ttu-id="bd6d4-243">Aber was ist mit diesem verwackelten Gekritzel aus Ihrem Meeting?</span><span class="sxs-lookup"><span data-stu-id="bd6d4-243">But what about those shaky, caffeinated doodles from your morning Flowcharters Anonymous meeting?</span></span>

<span data-ttu-id="bd6d4-244">Anhand einer Freihandeingabenanalyse kann Ihre App auch eine Reihe von Kernformen erkenne, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-244">Using ink analysis, your app can also recognize a set of core shapes, including:</span></span>
- <span data-ttu-id="bd6d4-245">Kreis</span><span class="sxs-lookup"><span data-stu-id="bd6d4-245">Circle</span></span>
- <span data-ttu-id="bd6d4-246">Diamant</span><span class="sxs-lookup"><span data-stu-id="bd6d4-246">Diamond</span></span>
- <span data-ttu-id="bd6d4-247">Zeichnung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-247">Drawing</span></span>
- <span data-ttu-id="bd6d4-248">Ellipse</span><span class="sxs-lookup"><span data-stu-id="bd6d4-248">Ellipse</span></span>
- <span data-ttu-id="bd6d4-249">Gleichseitiges Dreieck</span><span class="sxs-lookup"><span data-stu-id="bd6d4-249">EquilateralTriangle</span></span>
- <span data-ttu-id="bd6d4-250">Sechseck</span><span class="sxs-lookup"><span data-stu-id="bd6d4-250">Hexagon</span></span>
- <span data-ttu-id="bd6d4-251">Gleichschenkliges Dreieck</span><span class="sxs-lookup"><span data-stu-id="bd6d4-251">IsoscelesTriangle</span></span>
- <span data-ttu-id="bd6d4-252">Parallelogramm</span><span class="sxs-lookup"><span data-stu-id="bd6d4-252">Parallelogram</span></span>
- <span data-ttu-id="bd6d4-253">Richtungspfeil</span><span class="sxs-lookup"><span data-stu-id="bd6d4-253">Pentagon</span></span>
- <span data-ttu-id="bd6d4-254">Viereckig</span><span class="sxs-lookup"><span data-stu-id="bd6d4-254">Quadrilateral</span></span>
- <span data-ttu-id="bd6d4-255">Rechteck</span><span class="sxs-lookup"><span data-stu-id="bd6d4-255">Rectangle</span></span>
- <span data-ttu-id="bd6d4-256">Rechtes Dreieck</span><span class="sxs-lookup"><span data-stu-id="bd6d4-256">RightTriangle</span></span>
- <span data-ttu-id="bd6d4-257">Quadrat</span><span class="sxs-lookup"><span data-stu-id="bd6d4-257">Square</span></span>
- <span data-ttu-id="bd6d4-258">Trapez</span><span class="sxs-lookup"><span data-stu-id="bd6d4-258">Trapezoid</span></span>
- <span data-ttu-id="bd6d4-259">Dreieck</span><span class="sxs-lookup"><span data-stu-id="bd6d4-259">Triangle</span></span>

<span data-ttu-id="bd6d4-260">In diesem Schritt verwenden wir die Formerkennungsfunktionen von Windows Ink, um unser Gekritzel zu bereinigen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-260">In this step, we use the shape-recognition features of Windows Ink to try to clean up your doodles.</span></span>

<span data-ttu-id="bd6d4-261">In diesem Beispiel werden wir nicht, Freihandstriche nachzuzeichnen (obwohl dies möglich ist).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-261">For this example, we don't attempt to redraw ink strokes (although that's possible).</span></span> <span data-ttu-id="bd6d4-262">Stattdessen fügen wir eine standardmäßige Canvas unter der „InkCanvas” ein, in der wir aus den ursprünglichen Freihandstrichen abgeleitete und entsprechende Ellipse- und Polygon-Objekte zeichnen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-262">Instead, we add a standard canvas under the InkCanvas where we draw equivalent Ellipse or Polygon objects derived from the original ink.</span></span> <span data-ttu-id="bd6d4-263">Wir löschen dann die dazugehörigen Freihandstriche.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-263">We then delete the corresponding ink strokes.</span></span>

### <a name="in-the-sample"></a><span data-ttu-id="bd6d4-264">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-264">In the sample:</span></span>
1. <span data-ttu-id="bd6d4-265">Öffnen Sie die Datei „MainPage.xaml“</span><span class="sxs-lookup"><span data-stu-id="bd6d4-265">Open the MainPage.xaml file</span></span>
2. <span data-ttu-id="bd6d4-266">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt6: Erkennen von Formen-->”)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-266">Find the code marked with the title of this step ("\<!-- Step 6: Recognize shapes -->")</span></span>
3. <span data-ttu-id="bd6d4-267">Löschen Sie die Kommentare in dieser Zeile.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-267">Uncomment this line.</span></span>  

``` xaml
   <Canvas x:Name="canvas" />

   And these lines.

    <Button Grid.Row="1" x:Name="recognizeShape" Click="recognizeShape_ClickAsync"
        Content="Recognize shape" 
        Margin="10,10,10,10" />
```

4. <span data-ttu-id="bd6d4-268">Öffnen Sie die Datei „MainPage.xaml.cs“</span><span class="sxs-lookup"><span data-stu-id="bd6d4-268">Open the MainPage.xaml.cs file</span></span>
5. <span data-ttu-id="bd6d4-269">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („Schritt6: Erkennen von Formen”)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-269">Find the code marked with the title of this step ("// Step 6: Recognize shapes")</span></span>
6. <span data-ttu-id="bd6d4-270">Löschen Sie die Kommentare in den folgende Zeilen:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-270">Uncomment these lines:</span></span>  

``` csharp
    private async void recognizeShape_ClickAsync(object sender, RoutedEventArgs e)
    {
        ...
    }

    private void DrawEllipse(InkAnalysisInkDrawing shape)
    {
        ...
    }

    private void DrawPolygon(InkAnalysisInkDrawing shape)
    {
        ...
    }
```

7. <span data-ttu-id="bd6d4-271">Führen Sie die App aus, zeichnen Sie einige Formen und klicken Sie auf die Schaltfläche **Form erkennen**</span><span class="sxs-lookup"><span data-stu-id="bd6d4-271">Run the app, draw some shapes, and click the **Recognize shape** button</span></span>

<span data-ttu-id="bd6d4-272">Hier ist ein Beispiel für ein einfaches Flussdiagramm aus der digitalen Konzeptplanung.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-272">Here's an example of a rudimentary flowchart from a digital napkin.</span></span>

![Ursprüngliches Freihand-Flussdiagramm](images/ink/ink-app-step6-shapereco1.png)

<span data-ttu-id="bd6d4-274">Hier ist das gleiche Flussdiagramm nach der Formerkennung.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-274">Here's the same flowchart after shape recognition.</span></span>

![Ursprüngliches Freihand-Flussdiagramm](images/ink/ink-app-step6-shapereco2.png)


## <a name="step-7-save-and-load-ink"></a><span data-ttu-id="bd6d4-276">Schritt7: Speichern und Laden der Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="bd6d4-276">Step 7: Save and load ink</span></span>

<span data-ttu-id="bd6d4-277">Sie sind mit dem Kritzeln fertig und Ihnen gefällt, was Sie sehen, würden aber gerne später noch ein paar Änderungen vornehmen?</span><span class="sxs-lookup"><span data-stu-id="bd6d4-277">So, you're done doodling and you like what you see, but think you might like to tweak a couple of things later?</span></span> <span data-ttu-id="bd6d4-278">Sie können Ihre Freihandstriche in einer serialisierten Freihandformat-Datei (ISF-Datei) speichern und sie jederzeit für die Bearbeitung erneut laden.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-278">You can save your ink strokes to an Ink Serialized Format (ISF) file and load them for editing whenever the inspiration strikes.</span></span> 

<span data-ttu-id="bd6d4-279">Die ISF-Datei ist ein einfaches GIF-Bild mit zusätzlichen Metadaten für alle Eigenschaften und Verhaltensweisen von Freihandstrichen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-279">The ISF file is a basic GIF image that includes additional metadata describing ink-stroke properties and behaviors.</span></span> <span data-ttu-id="bd6d4-280">Apps, die nicht für die Freihandeingabe aktiviert sind, können die zusätzlichen Metadaten ignorieren und trotzdem das einfache GIF-Bild (einschließlich Alphakanal-Hintergrundtransparenz) laden.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-280">Apps that are not ink enabled can ignore the extra metadata and still load the basic GIF image (including alpha-channel background transparency).</span></span>

<span data-ttu-id="bd6d4-281">In diesem Schritt verknüpfen wir die Schaltflächen **Speichern** und **Laden**, die sich neben der Symbolleiste befinden.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-281">In this step, we hook up the **Save** and **Load** buttons located beside the ink toolbar.</span></span>

### <a name="in-the-sample"></a><span data-ttu-id="bd6d4-282">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd6d4-282">In the sample:</span></span>
1. <span data-ttu-id="bd6d4-283">Öffnen Sie die Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-283">Open the MainPage.xaml file.</span></span>
2. <span data-ttu-id="bd6d4-284">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt7: Speichern und Laden von Freihanddaten-->”).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-284">Find the code marked with the title of this step ("\<!-- Step 7: Saving and loading ink -->").</span></span>
3. <span data-ttu-id="bd6d4-285">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-285">Uncomment the following lines.</span></span> 

``` xaml
    <Button x:Name="buttonSave" 
            Content="Save" 
            Click="buttonSave_ClickAsync"
            Width="100"
            Margin="5,0,0,0"/>
    <Button x:Name="buttonLoad" 
            Content="Load"  
            Click="buttonLoad_ClickAsync"
            Width="100"
            Margin="5,0,0,0"/>
```

4. <span data-ttu-id="bd6d4-286">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-286">Open the MainPage.xaml.cs file.</span></span>
5. <span data-ttu-id="bd6d4-287">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („// Schritt7: Speichern und Laden von Freihanddaten”).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-287">Find the code marked with the title of this step ("// Step 7: Save and load ink").</span></span>
6. <span data-ttu-id="bd6d4-288">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-288">Uncomment the following lines.</span></span>  

``` csharp
    private async void buttonSave_ClickAsync(object sender, RoutedEventArgs e)
    {
        ...
    }

    private async void buttonLoad_ClickAsync(object sender, RoutedEventArgs e)
    {
        ...
    }
```

7. <span data-ttu-id="bd6d4-289">Führen Sie die App aus und zeichnen Sie etwas.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-289">Run the app and draw something.</span></span>
8. <span data-ttu-id="bd6d4-290">Wählen Sie die Schaltfläche **Speichern** und speichern Sie die Zeichnung.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-290">Select the **Save** button and save your drawing.</span></span>
9. <span data-ttu-id="bd6d4-291">Löschen Sie die Freihandeingabe, oder starten Sie die App neu.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-291">Erase the ink or restart the app.</span></span>
10. <span data-ttu-id="bd6d4-292">Wählen Sie die Schaltfläche **Laden** und öffnen Sie die Freihandeingabedatei, die Sie gerade gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-292">Select the **Load** button and open the ink file you just saved.</span></span>

### <a name="challenge-use-the-clipboard-to-copy-and-paste-ink-strokes"></a><span data-ttu-id="bd6d4-293">Herausforderung: Verwenden Sie die Zwischenablage, um die Freihandstriche zu kopieren und einzufügen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-293">Challenge: Use the clipboard to copy and paste ink strokes</span></span> 
<table class="wdg-noborder">
<tr>
 <td width=125><img src="images/challenge-icon.png"></td>
    <td width=500><p><span data-ttu-id="bd6d4-294">Windows-Freihandeingabe unterstützt auch das Kopieren und Einfügen von Freihandstrichen zur und aus der Zwischenablage.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-294">Windows ink also supports copying and pasting ink strokes to and from the clipboard.</span></span>

<span data-ttu-id="bd6d4-295">Weitere Informationen zur Verwendung der Zwischenablage mit Freihandeingabe finden Sie unter [Speichern und Abrufen von Windows Ink](https://docs.microsoft.com/en-us/windows/uwp/input-and-devices/save-and-load-ink).</span><span class="sxs-lookup"><span data-stu-id="bd6d4-295">For more details about using the clipboard with ink, see [Store and retrieve Windows Ink stroke data](https://docs.microsoft.com/en-us/windows/uwp/input-and-devices/save-and-load-ink).</span></span>
</tr>
</table>

## <a name="summary"></a><span data-ttu-id="bd6d4-296">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="bd6d4-296">Summary</span></span>

<span data-ttu-id="bd6d4-297">Herzlichen Glückwunsch, Sie haben das Lernprogramm **Eingaben: Unterstützen von Freihanddaten in Ihrer UWP-App** abgeschlossen!</span><span class="sxs-lookup"><span data-stu-id="bd6d4-297">Congratulations, you've completed the **Input: Support ink in your UWP app** tutorial !</span></span> <span data-ttu-id="bd6d4-298">Ihnen wurde der grundlegende Code gezeigt, der für die Unterstützung von Freihanddaten in Ihren UWP-Apps erforderlich ist, und wie Sie Ihren Benutzern umfangreichere Erfahrungen in der Windows Ink-Plattform bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bd6d4-298">We showed you the basic code required for supporting ink in your UWP apps, and how to provide some of the richer user experiences supported by the Windows Ink platform.</span></span>

## <a name="related-articles"></a><span data-ttu-id="bd6d4-299">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bd6d4-299">Related articles</span></span>

* [<span data-ttu-id="bd6d4-300">Stiftinteraktionen und Windows Ink in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="bd6d4-300">Pen interactions and Windows Ink in UWP apps</span></span>](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions)

**<span data-ttu-id="bd6d4-301">Beispiele</span><span class="sxs-lookup"><span data-stu-id="bd6d4-301">Samples</span></span>**
* [<span data-ttu-id="bd6d4-302">Einfaches Freihandbeispiel (C#/C++)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-302">Simple ink sample (C#/C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620312)
* [<span data-ttu-id="bd6d4-303">Komplexes Freihandbeispiel (C++)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-303">Complex ink sample (C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620314)
* [<span data-ttu-id="bd6d4-304">Freihandbeispiel (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="bd6d4-304">Ink sample (JavaScript)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620308)
* [<span data-ttu-id="bd6d4-305">Lernprogramm „Erste Schritte:” Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="bd6d4-305">Get Started Tutorial: Support ink in your UWP app</span></span>](https://aka.ms/appsample-ink)
* [<span data-ttu-id="bd6d4-306">Malbuchbeispiel</span><span class="sxs-lookup"><span data-stu-id="bd6d4-306">Coloring book sample</span></span>](https://aka.ms/cpubsample-coloringbook)
* [<span data-ttu-id="bd6d4-307">Familiennotizbeispiel</span><span class="sxs-lookup"><span data-stu-id="bd6d4-307">Family notes sample</span></span>](https://aka.ms/cpubsample-familynotessample)
