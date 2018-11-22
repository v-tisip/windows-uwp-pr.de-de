---
author: Karl-Bridge-Microsoft
ms.assetid: ''
title: Unterstützen von Freihandeingaben in Ihrer UWP-App
description: Ein ausführliches Lernprogramm für das Hinzufügen der Freihandeingabeunterstützung in Ihrer UWP-App.
keywords: Freihand, Freihandeingabe, Lernprogramm
ms.author: kbridge
ms.date: 01/25/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 62c62aacd894163ef2c65b9ddfe6d8299733a2e5
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "7579108"
---
# <a name="tutorial-support-ink-in-your-uwp-app"></a><span data-ttu-id="702d8-104">Lernprogramm: Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="702d8-104">Tutorial: Support ink in your UWP app</span></span>

![Surface Pen](images/ink/ink-hero-small.png)  
<span data-ttu-id="702d8-106">*Surface Pen* (zum Kauf im [Microsoft Store](https://aka.ms/purchasesurfacepen) verfügbar).</span><span class="sxs-lookup"><span data-stu-id="702d8-106">*Surface Pen* (available for purchase at the [Microsoft Store](https://aka.ms/purchasesurfacepen)).</span></span>

<span data-ttu-id="702d8-107">Dieses Lernprogramm zeigt Ihnen, wie Sie eine einfachen Universelle Windows-Plattform-App (UWP-App) erstellen, die das Schreiben und Zeichnen mit Windows Ink unterstützt.</span><span class="sxs-lookup"><span data-stu-id="702d8-107">This tutorial steps through how to create a basic Universal Windows Platform (UWP) app that supports writing and drawing with Windows Ink.</span></span> <span data-ttu-id="702d8-108">Wir verwenden Ausschnitte aus einer Beispiel-App, die Sie von GitHub herunterladen können (unter [Beispielcode](#sample-code)), um die in den einzelnen Schritten erläuterten, verschiedenen Features und zugehörigen Windows Ink-APIs (siehe [Komponenten der Windows-Freihandplattform](#components-of-the-windows-ink-platform)) zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="702d8-108">We use snippets from a sample app, which you can download from GitHub (see [Sample code](#sample-code)), to demonstrate the various features and associated Windows Ink APIs (see [Components of the Windows Ink platform](#components-of-the-windows-ink-platform)) discussed in each step.</span></span>

<span data-ttu-id="702d8-109">Wir konzentrieren uns auf Folgendes:</span><span class="sxs-lookup"><span data-stu-id="702d8-109">We focus on the following:</span></span>
* <span data-ttu-id="702d8-110">Hinzufügen einer einfachen Freihandeingabe-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="702d8-110">Adding basic ink support</span></span>
* <span data-ttu-id="702d8-111">Hinzufügen einer Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="702d8-111">Adding an ink toolbar</span></span>
* <span data-ttu-id="702d8-112">Unterstützung von Schrifterkennung</span><span class="sxs-lookup"><span data-stu-id="702d8-112">Supporting handwriting recognition</span></span>
* <span data-ttu-id="702d8-113">Unterstützung der Erkennung von grundlegenden Formen</span><span class="sxs-lookup"><span data-stu-id="702d8-113">Supporting basic shape recognition</span></span>
* <span data-ttu-id="702d8-114">Speichern und Laden von Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="702d8-114">Saving and loading ink</span></span>

<span data-ttu-id="702d8-115">Weitere Informationen zur Implementierung dieser Features finden Sie unter [Zeichenstift-Interaktionen und Windows Ink in UWP-Apps](https://docs.microsoft.com/windows/uwp/input/pen-and-stylus-interactions).</span><span class="sxs-lookup"><span data-stu-id="702d8-115">For more detail about implementing these features, see [Pen interactions and Windows Ink in UWP apps](https://docs.microsoft.com/windows/uwp/input/pen-and-stylus-interactions).</span></span>

## <a name="introduction"></a><span data-ttu-id="702d8-116">Einführung</span><span class="sxs-lookup"><span data-stu-id="702d8-116">Introduction</span></span>

<span data-ttu-id="702d8-117">Mit Windows Ink können Sie Ihren Kunden fast alle erdenklichen schriftlichen Erfahrungen bieten, von schnellen handgeschriebenen Notizen und Anmerkungen bis zu Whiteboard-Demos, und von Architektur- und Ingenieurzeichnungen bis zu persönliche Meisterwerke.</span><span class="sxs-lookup"><span data-stu-id="702d8-117">With Windows Ink, you can provide your customers with the digital equivalent of almost any pen-and-paper experience imaginable, from quick, handwritten notes and annotations to whiteboard demos, and from architectural and engineering drawings to personal masterpieces.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="702d8-118">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="702d8-118">Prerequisites</span></span>

* <span data-ttu-id="702d8-119">Einen Computer (oder einen virtuellen Computer) mit der aktuellen Version von Windows10.</span><span class="sxs-lookup"><span data-stu-id="702d8-119">A computer (or a virtual machine) running the current version of Windows 10</span></span>
* [<span data-ttu-id="702d8-120">Visual Studio2017 und die RS2 SDK</span><span class="sxs-lookup"><span data-stu-id="702d8-120">Visual Studio 2017 and the RS2 SDK</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="702d8-121">Windows 10 SDK (10.0.15063.0)</span><span class="sxs-lookup"><span data-stu-id="702d8-121">Windows10 SDK (10.0.15063.0)</span></span>](https://developer.microsoft.com/windows/downloads/windows-10-sdk)
* <span data-ttu-id="702d8-122">Je nach Konfiguration, Sie möglicherweise die [Microsoft.NETCore.UniversalWindowsPlatform](https://www.nuget.org/packages/Microsoft.NETCore.UniversalWindowsPlatform/6.1.9) NuGet-Paket installieren und aktivieren **des Entwicklermodus** in den Systemeinstellungen (Einstellungen -> Update und Sicherheit für Entwickler -> -> Verwenden von Entwicklerfeatures).</span><span class="sxs-lookup"><span data-stu-id="702d8-122">Depending on your configuration, you might have to install the [Microsoft.NETCore.UniversalWindowsPlatform](https://www.nuget.org/packages/Microsoft.NETCore.UniversalWindowsPlatform/6.1.9) NuGet package and enable **Developer mode** in your system settings (Settings -> Update & Security -> For developers -> Use developer features).</span></span>
* <span data-ttu-id="702d8-123">Wenn Sie noch keine Erfahrung mit der App-Entwicklung in der Universellen Windows-Plattform (UWP) mit Visual Studio haben, werfen Sie einen Blick in diese Themen, bevor Sie dieses Lernprogramm starten:</span><span class="sxs-lookup"><span data-stu-id="702d8-123">If you're new to Universal Windows Platform (UWP) app development with Visual Studio, have a look through these topics before you start this tutorial:</span></span>  
    * [<span data-ttu-id="702d8-124">Vorbereiten</span><span class="sxs-lookup"><span data-stu-id="702d8-124">Get set up</span></span>](https://docs.microsoft.com/windows/uwp/get-started/get-set-up)
    * [<span data-ttu-id="702d8-125">Erstellen der App „Hello, world“ (XAML)</span><span class="sxs-lookup"><span data-stu-id="702d8-125">Create a "Hello, world" app (XAML)</span></span>](https://docs.microsoft.com/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
* <span data-ttu-id="702d8-126">**[OPTIONAL]** Ein digitaler Stift und ein Computer mit einer Anzeige, die die Eingaben eines digitalen Stifts unterstützt.</span><span class="sxs-lookup"><span data-stu-id="702d8-126">**[OPTIONAL]** A digital pen and a computer with a display that supports input from that digital pen.</span></span>

> [!NOTE] 
> <span data-ttu-id="702d8-127">Während Windows Ink das Zeichnen mit einer Maus und Fingereingabe (erfahren in Schritt3 dieses Lernprogramms wie dies funktioniert) für eine optimale Windows Ink-Erfahrung unterstützt, empfehlen wir, dass Sie über einen digitalen Stift und einem Computer mit einer Anzeige verfügen, die die Eingaben von diesem digitalen Stift unterstützt.</span><span class="sxs-lookup"><span data-stu-id="702d8-127">While Windows Ink can support drawing with a mouse and touch (we show how to do this in Step 3 of this tutorial) for an optimal Windows Ink experience, we recommend that you have a digital pen and a computer with a display that supports input from that digital pen.</span></span>

## <a name="sample-code"></a><span data-ttu-id="702d8-128">Beispielcode</span><span class="sxs-lookup"><span data-stu-id="702d8-128">Sample code</span></span>
<span data-ttu-id="702d8-129">In diesem Lernprogramm verwenden wir eine Beispiels-App für die Freihandeingabe, um die erläuterten Konzepte und Funktionen zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="702d8-129">Throughout this tutorial, we use a sample ink app to demonstrate the concepts and functionality discussed.</span></span>

<span data-ttu-id="702d8-130">Laden Sie dieses Visual Studio-Beispiel und den Quellecode von [GitHub](https://github.com/) unter [Windows-Appsample-Erste-Schritte-Freihandbeispiel](https://aka.ms/appsample-ink) herunter:</span><span class="sxs-lookup"><span data-stu-id="702d8-130">Download this Visual Studio sample and source code from [GitHub](https://github.com/) at [windows-appsample-get-started-ink sample](https://aka.ms/appsample-ink):</span></span>

1. <span data-ttu-id="702d8-131">Wählen Sie die grüne **Klonen oder herunterladen**-Schaltfläche aus</span><span class="sxs-lookup"><span data-stu-id="702d8-131">Select the green **Clone or download** button</span></span>  
![Klonen des Repositorys](images/ink/ink-clone.png)
2. <span data-ttu-id="702d8-133">Wenn Sie ein GitHub-Konto haben, können Sie das Repository auf Ihrem lokalen Computer mit der Option **In Visual Studio öffnen** klonen.</span><span class="sxs-lookup"><span data-stu-id="702d8-133">If you have a GitHub account, you can clone the repo to your local machine by choosing **Open in Visual Studio**</span></span> 
3. <span data-ttu-id="702d8-134">Wenn Sie kein GitHub-Konto haben, oder wenn Sie einfach eine lokale Kopie des Projekts möchten, wählen Sie **Herunterladen der ZIP-Datei** (Sie müssen regelmäßig auf neues Updates prüfen)</span><span class="sxs-lookup"><span data-stu-id="702d8-134">If you don't have a GitHub account, or you just want a local copy of the project, choose **Download ZIP** (you'll have to check back regularly to download the latest updates)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="702d8-135">Der Großteil des Codes im Beispiel ist als Kommentar formatiert. Bei den einzelnen Schritten werden Sie aufgefordert, die Kommentare der verschiedenen Codeabschnitte zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="702d8-135">Most of the code in the sample is commented out. As we go through each step, you'll be asked to uncomment various sections of the code.</span></span> <span data-ttu-id="702d8-136">Markieren Sie einfach in Visual Studio die Codezeilen und drücken Sie STRG+K und anschließend STRG + U.</span><span class="sxs-lookup"><span data-stu-id="702d8-136">In Visual Studio, just highlight the lines of code, and press CTRL-K and then CTRL-U.</span></span>

## <a name="components-of-the-windows-ink-platform"></a><span data-ttu-id="702d8-137">Komponenten der WindowsInk-Plattform</span><span class="sxs-lookup"><span data-stu-id="702d8-137">Components of the Windows Ink platform</span></span>

<span data-ttu-id="702d8-138">Diese Objekte bieten den Großteil der Freihandfunktionen für UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="702d8-138">These objects provide the bulk of the inking experience for UWP apps.</span></span>

| <span data-ttu-id="702d8-139">Komponente</span><span class="sxs-lookup"><span data-stu-id="702d8-139">Component</span></span> | <span data-ttu-id="702d8-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="702d8-140">Description</span></span> |
| --- | --- |
| [**<span data-ttu-id="702d8-141">InkCanvas</span><span class="sxs-lookup"><span data-stu-id="702d8-141">InkCanvas</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) | <span data-ttu-id="702d8-142">Ein XAMLUI-Plattform-Steuerelement, das in der Standardeinstellung empfängt und anzeigt alle Eingaben von einem Stift als letzten Strich oder ausradierten Strich.</span><span class="sxs-lookup"><span data-stu-id="702d8-142">A XAMLUI platform control that, by default, receives and displays all input from a pen as either an ink stroke or an erase stroke.</span></span> |
| [**<span data-ttu-id="702d8-143">InkPresenter</span><span class="sxs-lookup"><span data-stu-id="702d8-143">InkPresenter</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn922011) | <span data-ttu-id="702d8-144">Ein CodeBehind-Objekt, das zusammen mit einem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement instanziiert wird (über die [**InkCanvas.InkPresenter**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas.InkPresenter)-Eigenschaft verfügbar gemacht).</span><span class="sxs-lookup"><span data-stu-id="702d8-144">A code-behind object, instantiated along with an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control (exposed through the [**InkCanvas.InkPresenter**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas.InkPresenter) property).</span></span> <span data-ttu-id="702d8-145">Dieses Objekt stellt alle Standardfreihandfunktionen bereit, die vom [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)-Steuerelement zur Verfügung gestellt werden, sowie einen umfassenden Satz von APIs für zusätzliche Anpassung und Personalisierung.</span><span class="sxs-lookup"><span data-stu-id="702d8-145">This object provides all default inking functionality exposed by the [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), along with a comprehensive set of APIs for additional customization and personalization.</span></span> |
| [**<span data-ttu-id="702d8-146">InkToolbar</span><span class="sxs-lookup"><span data-stu-id="702d8-146">InkToolbar</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.inktoolbar.aspx) | <span data-ttu-id="702d8-147">Ein XAMLUI-Steuerelement, enthält eine anpassbare und erweiterbare Sammlung von Schaltflächen, die Freihand-Features in einem verknüpften [**InkCanvas-Steuerelement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)aktivieren.</span><span class="sxs-lookup"><span data-stu-id="702d8-147">A XAMLUI platform control containing a customizable and extensible collection of buttons that activate ink-related features in an associated [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas).</span></span> |
| [**<span data-ttu-id="702d8-148">IInkD2DRenderer</span><span class="sxs-lookup"><span data-stu-id="702d8-148">IInkD2DRenderer</span></span>**](https://msdn.microsoft.com/library/mt147263)<br/><span data-ttu-id="702d8-149">Diese Funktionalität wird von uns hier nicht erläutert. Weitere Informationen finden Sie unter [Komplexes Freihandbeispiel](http://go.microsoft.com/fwlink/p/?LinkID=620314).</span><span class="sxs-lookup"><span data-stu-id="702d8-149">We do not cover this functionality here, for more information, see the [Complex ink sample](http://go.microsoft.com/fwlink/p/?LinkID=620314).</span></span> | <span data-ttu-id="702d8-150">Ermöglicht das Rendern von Freihandstrichen im angegebenen Direct2D-Gerätekontext einer universellen Windows-App statt im standardmäßigen [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="702d8-150">Enables the rendering of ink strokes onto the designated Direct2D device context of a Universal Windows app, instead of the default [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span> |

## <a name="step-1-run-the-sample"></a><span data-ttu-id="702d8-151">Schritt1: Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="702d8-151">Step 1: Run the sample</span></span>

<span data-ttu-id="702d8-152">Nachdem Sie die RadialController-Beispiel-App heruntergeladen haben, stellen Sie sicher, dass sie ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="702d8-152">After you've downloaded the RadialController sample app, verify that it runs:</span></span>
1. <span data-ttu-id="702d8-153">Öffnen Sie das Beispielprojekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="702d8-153">Open the sample project in Visual Studio.</span></span>
2. <span data-ttu-id="702d8-154">Legen Sie das **Lösungsplattformen**-Dropdownmenü für eine nicht ARM-Auswahl fest.</span><span class="sxs-lookup"><span data-stu-id="702d8-154">Set the **Solution Platforms** dropdown to a non-ARM selection.</span></span>
3. <span data-ttu-id="702d8-155">Drücken Sie F5, um zu kompilieren, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="702d8-155">Press F5 to compile, deploy, and run.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="702d8-156">Alternativ können Sie **Debuggen** > **Debuggen starten** Menüelement auswählen, oder wählen Sie die hier dargestellte Ausführungsschaltfläche für die **Lokale Maschine** aus.</span><span class="sxs-lookup"><span data-stu-id="702d8-156">Alternatively, you can select **Debug** > **Start debugging** menu item, or select the **Local Machine** Run button shown here.</span></span>
   > ![Visual Studio-Schaltfläche „Projekt erstellen”](images/ink/ink-vsrun-small.png)

<span data-ttu-id="702d8-158">Das App-Fenster wird geöffnet und nach einem Begrüßungsbildschirm wird der Startbildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="702d8-158">The app window opens, and after a splash screen appears for a few seconds, you’ll see this initial screen.</span></span>

![Leere App](images/ink/ink-app-step1-empty-small.png)

<span data-ttu-id="702d8-160">OK, nun haben wir die grundlegende UWP-App, die wir im verbleibenden Teil dieses Lernprogramms verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="702d8-160">Okay, we now have the basic UWP app that we’ll use throughout the rest of this tutorial.</span></span> <span data-ttu-id="702d8-161">In den folgenden Schritten fügen wir unsere Freihandfunktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="702d8-161">In the following steps, we add our ink functionality.</span></span>

## <a name="step-2-use-inkcanvas-to-support-basic-inking"></a><span data-ttu-id="702d8-162">Schritt2: Verwendung von InkCanvas zur Unterstützung von einfachen Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="702d8-162">Step 2: Use InkCanvas to support basic inking</span></span>

<span data-ttu-id="702d8-163">Vielleicht haben Sie bereits bemerkt, dass Sie in der App in ihrer ursprünglichen Form nicht mit dem Stift zeichnen können (auch wenn Sie den Stift als ein Standardzeigergerät für die Interaktion mit der App festgelegt haben).</span><span class="sxs-lookup"><span data-stu-id="702d8-163">Perhaps you've probably already noticed that the app, in it's initial form, doesn't let you draw anything with the pen (although you can use the pen as a standard pointer device to interact with the app).</span></span> 

<span data-ttu-id="702d8-164">Beheben wir dieses Problem in diesem Schritt.</span><span class="sxs-lookup"><span data-stu-id="702d8-164">Let's fix that little shortcoming in this step.</span></span>

<span data-ttu-id="702d8-165">Um einfaches Freihandzeichen hinzuzufügen, platzieren Sie einfach ein [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-UWP-Steuerelement auf der entsprechenden Seite in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="702d8-165">To add basic inking functionality, just place an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) UWP platform control on the appropriate page in your app.</span></span>

> [!NOTE]
> <span data-ttu-id="702d8-166">Ein InkCanvas verfügt standardmäßig über [**Höhe.**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.Height) und [**Breite-**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.Width)-Eigenschaften von null, sofern es sich um ein untergeordnetes Element eines Elements handelt, das die Größe seiner untergeordneten Elemente automatisch festlegt.</span><span class="sxs-lookup"><span data-stu-id="702d8-166">An InkCanvas has default [**Height**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.Height) and [**Width**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.Width) properties of zero, unless it is the child of an element that automatically sizes its child elements.</span></span> 

### <a name="in-the-sample"></a><span data-ttu-id="702d8-167">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="702d8-167">In the sample:</span></span>
1. <span data-ttu-id="702d8-168">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="702d8-168">Open the MainPage.xaml.cs file.</span></span>
2. <span data-ttu-id="702d8-169">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („// Schritt2: Verwendung InkCanvas für die Unterstützung einfacher Freihandeingabe”).</span><span class="sxs-lookup"><span data-stu-id="702d8-169">Find the code marked with the title of this step ("// Step 2: Use InkCanvas to support basic inking").</span></span>
3. <span data-ttu-id="702d8-170">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="702d8-170">Uncomment the following lines.</span></span> <span data-ttu-id="702d8-171">(Diese Verweise sind für die Funktionen erforderlich, die in den nachfolgenden Schritten verwendet werden).</span><span class="sxs-lookup"><span data-stu-id="702d8-171">(These references are required for the functionality used in the subsequent steps).</span></span>  

``` csharp
    using Windows.UI.Input.Inking;
    using Windows.UI.Input.Inking.Analysis;
    using Windows.UI.Xaml.Shapes;
    using Windows.Storage.Streams;
```

4. <span data-ttu-id="702d8-172">Öffnen Sie die Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="702d8-172">Open the MainPage.xaml file.</span></span>
5. <span data-ttu-id="702d8-173">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt2: Einfache Freihandeingabe mit InkCanvas -->”).</span><span class="sxs-lookup"><span data-stu-id="702d8-173">Find the code marked with the title of this step ("\<!-- Step 2: Basic inking with InkCanvas -->").</span></span>
6. <span data-ttu-id="702d8-174">Entfernen Sie aus der folgenden Zeile die Kommentare.</span><span class="sxs-lookup"><span data-stu-id="702d8-174">Uncomment the following line.</span></span>  

``` xaml
    <InkCanvas x:Name="inkCanvas" />
```

<span data-ttu-id="702d8-175">Das war's.</span><span class="sxs-lookup"><span data-stu-id="702d8-175">That's it!</span></span> 

<span data-ttu-id="702d8-176">Führen Sie nun erneut die App aus.</span><span class="sxs-lookup"><span data-stu-id="702d8-176">Now run the app again.</span></span> <span data-ttu-id="702d8-177">Machen Sie nun eine Skizze, schreiben Sie Ihren Namen, oder (wenn Sie einen Spiegel zur Hand oder ein sehr ausgeprägtes Gedächtnis haben) zeichnen Sie ein Selbstporträt.</span><span class="sxs-lookup"><span data-stu-id="702d8-177">Go ahead and scribble, write your name, or (if you're holding a mirror or have a very good memory) draw your self-portrait.</span></span>

![Einfache Freihandeingabe](images/ink/ink-app-step1-name-small.png)

## <a name="step-3-support-inking-with-touch-and-mouse"></a><span data-ttu-id="702d8-179">Schritt3: Unterstützung von Freihandzeichnen mit Touch- und Mauseingabe</span><span class="sxs-lookup"><span data-stu-id="702d8-179">Step 3: Support inking with touch and mouse</span></span>

<span data-ttu-id="702d8-180">Sie werden feststellen, dass Freihandeingaben standardmäßig nur für Stifteingaben unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="702d8-180">You'll notice that, by default, ink is supported for pen input only.</span></span> <span data-ttu-id="702d8-181">Wenn Sie versuchen, mit Ihrem Finger, Maus oder Ihrem Touchpad zu schreiben oder zu zeichnen, werden Sie enttäuscht sein.</span><span class="sxs-lookup"><span data-stu-id="702d8-181">If you try to write or draw with your finger, your mouse, or your touchpad, you'll be disappointed.</span></span>

<span data-ttu-id="702d8-182">Um das zu beheben, müssen Sie eine zweite Codezeile hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="702d8-182">To turn that frown upside down , you need to add a second line of code.</span></span> <span data-ttu-id="702d8-183">Dieses Mal befindet sie sich im CodeBehind für die XAML-Datei, in der Sie Ihren [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="702d8-183">This time it’s in the code-behind for the XAML file in which you declared your [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas).</span></span> 

<span data-ttu-id="702d8-184">In diesem Schritt führen wir das [**InkPresenter**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter) -Objekt ein, das eine differenziertere Verwaltung der Eingabe, Verarbeitung und Rendering der Freihandeingabe (standard und verändert) auf Ihrem [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) bietet.</span><span class="sxs-lookup"><span data-stu-id="702d8-184">In this step, we introduce the [**InkPresenter**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter) object, which provides finer-grained management of the input, processing, and rendering of ink input (standard and modified) on your [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas).</span></span>

> [!NOTE]
> <span data-ttu-id="702d8-185">Standardmäßige Freihandeingabe (Stiftspitze oder Radiererspitze/-schaltfläche) wird mit einem sekundären Hardware-Angebot nicht geändert, wie z.B. eine Zeichenstift-Drucktaste, rechte Maustaste oder einem ähnlichen Mechanismus.</span><span class="sxs-lookup"><span data-stu-id="702d8-185">Standard ink input (pen tip or eraser tip/button) is not modified with a secondary hardware affordance, such as a pen barrel button, right mouse button, or similar mechanism.</span></span> 

<span data-ttu-id="702d8-186">Legen Sie zum Aktivieren der Maus- und Touch-Freihandeingabe die [**InputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter.InputDeviceTypes)-Eigenschaft des [**InkPresenter**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter) auf die Kombination aus den gewünschten [**CoreInputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.core.coreinputdevicetypes)-Werten fest.</span><span class="sxs-lookup"><span data-stu-id="702d8-186">To enable mouse and touch inking, set the [**InputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter.InputDeviceTypes) property of the [**InkPresenter**](https://docs.microsoft.com/uwp/api/windows.ui.input.inking.inkpresenter) to the combination of [**CoreInputDeviceTypes**](https://docs.microsoft.com/uwp/api/windows.ui.core.coreinputdevicetypes) values that you want.</span></span>

### <a name="in-the-sample"></a><span data-ttu-id="702d8-187">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="702d8-187">In the sample:</span></span>
1. <span data-ttu-id="702d8-188">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="702d8-188">Open the MainPage.xaml.cs file.</span></span>
2. <span data-ttu-id="702d8-189">Finden Sie den Code, der mit dem Titel dieses Schrittsgekennzeichnet ist („// Schritt3: Freihandzeichnen mit Touch- und Mauseingabe unterstützen”).</span><span class="sxs-lookup"><span data-stu-id="702d8-189">Find the code marked with the title of this step ("// Step 3: Support inking with touch and mouse").</span></span>
3. <span data-ttu-id="702d8-190">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="702d8-190">Uncomment the following lines.</span></span>  

``` csharp
    inkCanvas.InkPresenter.InputDeviceTypes =
        Windows.UI.Core.CoreInputDeviceTypes.Mouse | 
        Windows.UI.Core.CoreInputDeviceTypes.Touch | 
        Windows.UI.Core.CoreInputDeviceTypes.Pen;
```

<span data-ttu-id="702d8-191">Führen Sie die App erneut aus und Sie werden feststellen, dass Sie endlich mit Ihren Fingern auf dem Computerbildschirm zeichnen können!</span><span class="sxs-lookup"><span data-stu-id="702d8-191">Run the app again and you'll find that all your finger-painting-on-a-computer-screen dreams have come true!</span></span>

> [!NOTE]
> <span data-ttu-id="702d8-192">Sie müssen beim Festlegen von Eingabegerätetypen die Unterstützung für jeden spezifischen Eingabetyp angeben (einschließlich Stift), da diese Einstellung standardmäßig die [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)-Einstellung überschreibt.</span><span class="sxs-lookup"><span data-stu-id="702d8-192">When specifying input device types, you must indicate support for each specific input type (including pen), because setting this property overrides the default [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) setting.</span></span>

## <a name="step-4-add-an-ink-toolbar"></a><span data-ttu-id="702d8-193">Schritt4: Hinzufügen einer Freihandsymbolleiste</span><span class="sxs-lookup"><span data-stu-id="702d8-193">Step 4: Add an ink toolbar</span></span>

<span data-ttu-id="702d8-194">Die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) ist ein UWP-Steuerelement, das eine anpassbare und erweiterbare Sammlung an Schaltflächen für die Aktivierung von freihandbezogenen Funktionen bietet.</span><span class="sxs-lookup"><span data-stu-id="702d8-194">The [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) is a UWP platform control that provides a customizable and extensible collection of buttons for activating ink-related features.</span></span> 

<span data-ttu-id="702d8-195">Die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) enthält standardmäßig eine Reihe von Schaltflächen, mit denen Benutzer schnell zwischen einem Kugelschreiber, Stift, Textmarker oder Radierer wechseln können, die alle zusammen mit einer Schablone (Lineal oder Winkelmesser) verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="702d8-195">By default, the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) includes a basic set of buttons that let users quickly select between a pen, a pencil, a highlighter, or an eraser, any of which can be used together with a stencil (ruler or protractor).</span></span> <span data-ttu-id="702d8-196">Mit den Schaltflächen Kugelschreiber, Bleistift und Textmarker bieten auch jeweils ein Flyout zum Auswählen von Farben und Strichgrößen.</span><span class="sxs-lookup"><span data-stu-id="702d8-196">The pen, pencil, and highlighter buttons each also provide a flyout for selecting ink color and stroke size.</span></span>

<span data-ttu-id="702d8-197">Um eine standardmäßige [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) zu einer App für die Freihandeingabe hinzuzufügen, platzieren Sie sie einfach auf derselben Seite wie Ihr [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), und verbinden Sie die beiden Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="702d8-197">To add a default [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) to an inking app, just place it on the same page as your [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) and associate the two controls.</span></span>

### <a name="in-the-sample"></a><span data-ttu-id="702d8-198">Im Beispiel</span><span class="sxs-lookup"><span data-stu-id="702d8-198">In the sample</span></span>
1. <span data-ttu-id="702d8-199">Öffnen Sie die Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="702d8-199">Open the MainPage.xaml file.</span></span>
2. <span data-ttu-id="702d8-200">Suchen Sie den Code, mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt4: Hinzufügen einer Symbolleiste-->”).</span><span class="sxs-lookup"><span data-stu-id="702d8-200">Find the code marked with the title of this step ("\<!-- Step 4: Add an ink toolbar -->").</span></span>
3. <span data-ttu-id="702d8-201">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="702d8-201">Uncomment the following lines.</span></span>  

``` xaml
    <InkToolbar x:Name="inkToolbar" 
                        VerticalAlignment="Top" 
                        Margin="10,0,10,0"
                        TargetInkCanvas="{x:Bind inkCanvas}">
    </InkToolbar>
```

> [!NOTE]
> <span data-ttu-id="702d8-202">Um die Benutzeroberfläche und den Code so übersichtlich und einfach wie möglich zu gestalten, verwenden wir ein einfaches Rasterlayout und deklarieren die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) nach dem [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) in einer Rasterzeile.</span><span class="sxs-lookup"><span data-stu-id="702d8-202">To keep the UI and code as uncluttered and simple as possible, we use a basic Grid layout and declare the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) after the [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) in a grid row.</span></span> <span data-ttu-id="702d8-203">Wenn Sie sie vor dem [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas) deklarieren, wird die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) als erstes unterhalb der Canvas und für den Benutzer unzugänglich gerendert.</span><span class="sxs-lookup"><span data-stu-id="702d8-203">If you declare it before the [**InkCanvas**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) is rendered first, below the canvas and inaccessible to the user.</span></span>  

<span data-ttu-id="702d8-204">Führen Sie jetzt die App erneut aus, um die [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) anzuzeigen und einige dieser Tools auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="702d8-204">Now run the app again to see the [**InkToolbar**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) and try out some of the tools.</span></span>

![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/ink/ink-inktoolbar-default-small.png)

### <a name="challenge-add-a-custom-button"></a><span data-ttu-id="702d8-206">Die Herausforderung: Hinzufügen einer benutzerdefinierten Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="702d8-206">Challenge: Add a custom button</span></span>
<table class="wdg-noborder">
<tr>
<td>

![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/challenge-icon.png)

</td>
<td>

<span data-ttu-id="702d8-208">Hier ist ein Beispiel für eine benutzerdefinierte **[InkToolbar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar)** (von Skizzenblock im Windows Ink-Arbeitsbereich).</span><span class="sxs-lookup"><span data-stu-id="702d8-208">Here's an example of a custom **[InkToolbar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar)** (from Sketchpad in the Windows Ink Workspace).</span></span>

![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/ink/ink-inktoolbar-sketchpad-small.png)

<span data-ttu-id="702d8-210">Weitere Informationen zur Anpassung einer [InkToolbar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar) finden Sie unter [Hinzufügen einer InkToolbar zu einer App für die Universelle Windows-Plattform (UWP) für die Freihandeingabe](ink-toolbar.md).</span><span class="sxs-lookup"><span data-stu-id="702d8-210">For more details about customizing an [InkToolbar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar), see [Add an InkToolbar to a Universal Windows Platform (UWP) inking app](ink-toolbar.md).</span></span>

</td>
</tr>
</table>

## <a name="step-5-support-handwriting-recognition"></a><span data-ttu-id="702d8-211">Schritt5: Unterstützung der Handschrifterkennung</span><span class="sxs-lookup"><span data-stu-id="702d8-211">Step 5: Support handwriting recognition</span></span>

<span data-ttu-id="702d8-212">Nun, da Sie in Ihrer App zeichnen und schreiben können, versuchen wir aus diesen Skizzen etwas Nutzen zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="702d8-212">Now that you can write and draw in your app, let's try to do something useful with those scribbles.</span></span>

<span data-ttu-id="702d8-213">In diesem Schritt verwenden wir die Handschrifterkennungsfunktionen von Windows Ink, um das von Ihnen Geschriebene zu entziffern.</span><span class="sxs-lookup"><span data-stu-id="702d8-213">In this step, we use the handwriting recognition features of Windows Ink to try to decipher what you've written.</span></span>

> [!NOTE]
> <span data-ttu-id="702d8-214">Die Handschrifterkennung kann anhand der **Stift & Windows Ink**-Einstellungen verbessert werden:</span><span class="sxs-lookup"><span data-stu-id="702d8-214">Handwriting recognition can be improved through the **Pen & Windows Ink** settings:</span></span>
> 1. <span data-ttu-id="702d8-215">Öffnen Sie das Startmenü und wählen Sie **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="702d8-215">Open the Start menu and select **Settings**.</span></span>
> 2. <span data-ttu-id="702d8-216">Wählen Sie auf dem Bildschirm „Einstellungen” **Geräte** > **Stift & Windows Ink**.</span><span class="sxs-lookup"><span data-stu-id="702d8-216">From the Settings screen select **Devices** > **Pen & Windows Ink**.</span></span>
> ![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/ink/ink-settings-small.png)
> 3. <span data-ttu-id="702d8-218">Wählen Sie **Meine Handschrift erkennen**, um das Dialogfeld **Handschriftanpassung** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="702d8-218">Select **Get to know my handwriting** to open the **Handwriting Personalization** dialog.</span></span>
> ![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/ink/ink-settings-handwritingpersonalization-small.png)

### <a name="in-the-sample"></a><span data-ttu-id="702d8-220">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="702d8-220">In the sample:</span></span>
1. <span data-ttu-id="702d8-221">Öffnen Sie die Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="702d8-221">Open the MainPage.xaml file.</span></span>
2. <span data-ttu-id="702d8-222">Suchen Sie den Code, mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt5: schrifterkennung Unterstützung-->”).</span><span class="sxs-lookup"><span data-stu-id="702d8-222">Find the code marked with the title of this step ("\<!-- Step 5: Support handwriting recognition -->").</span></span>
3. <span data-ttu-id="702d8-223">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="702d8-223">Uncomment the following lines.</span></span>  

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

4. <span data-ttu-id="702d8-224">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="702d8-224">Open the MainPage.xaml.cs file.</span></span>
5. <span data-ttu-id="702d8-225">Suchen Sie den Code, mit dem Titel dieses Schritts gekennzeichnet ist („Schritt5: schrifterkennung Unterstützung”).</span><span class="sxs-lookup"><span data-stu-id="702d8-225">Find the code marked with the title of this step (" Step 5: Support handwriting recognition").</span></span>
6. <span data-ttu-id="702d8-226">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="702d8-226">Uncomment the following lines.</span></span>  

- <span data-ttu-id="702d8-227">Dies sind die globalen Variablen, die für diesen Schritt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="702d8-227">These are the global variables required for this step.</span></span>

``` csharp
    InkAnalyzer analyzerText = new InkAnalyzer();
    IReadOnlyList<InkStroke> strokesText = null;
    InkAnalysisResult resultText = null;
    IReadOnlyList<IInkAnalysisNode> words = null;
```

- <span data-ttu-id="702d8-228">Dies ist der Handler für die Schaltfläche **Text erkennen**, wo die Verarbeitung der Erkennung erfolgt.</span><span class="sxs-lookup"><span data-stu-id="702d8-228">This is the handler for the **Recognize text** button, where we do the recognition processing.</span></span>

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

7. <span data-ttu-id="702d8-229">Führen Sie die App erneut aus, schreiben Sie etwas und klicken Sie dann auf die Schaltfläche **Text erkennen**.</span><span class="sxs-lookup"><span data-stu-id="702d8-229">Run the app again, write something, and then click the **Recognize text** button</span></span>
8. <span data-ttu-id="702d8-230">Die Ergebnisse der Erkennung werden neben der Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="702d8-230">The results of the recognition are displayed beside the button</span></span>

### <a name="challenge-1-international-recognition"></a><span data-ttu-id="702d8-231">Herausforderung 1: Internationale Erkennung</span><span class="sxs-lookup"><span data-stu-id="702d8-231">Challenge 1: International recognition</span></span>
<table class="wdg-noborder">
<tr>
<td>

![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/challenge-icon.png)

</td>
<td>

<span data-ttu-id="702d8-233">Windows Ink unterstützt Texterkennung für viele der von Windows unterstützten Sprachen.</span><span class="sxs-lookup"><span data-stu-id="702d8-233">Windows Ink supports text recognition for many of the of the languages supported by Windows.</span></span> <span data-ttu-id="702d8-234">Jedes Sprachpaket enthält ein Schrifterkennungsmodul, das mit dem Language Pack installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="702d8-234">Each language pack includes a handwriting recognition engine that can be installed with the language pack.</span></span>

<span data-ttu-id="702d8-235">Zielen Sie auf eine bestimmte Sprache ab, indem Sie die installierten Handschrifterkennungsmodule abfragen.</span><span class="sxs-lookup"><span data-stu-id="702d8-235">Target a specific language by querying the installed handwriting recognition engines.</span></span>

<span data-ttu-id="702d8-236">Weitere Informationen zur internationalen Handschrifterkennung finden Sie unter [Windows Ink-Striche als Text erkennen](convert-ink-to-text.md).</span><span class="sxs-lookup"><span data-stu-id="702d8-236">For more details about international handwriting recognition, see [Recognize Windows Ink strokes as text](convert-ink-to-text.md).</span></span>

</td>
</tr>
</table>

### <a name="challenge-2-dynamic-recognition"></a><span data-ttu-id="702d8-237">Herausforderung 2: Dynamische Erkennung</span><span class="sxs-lookup"><span data-stu-id="702d8-237">Challenge 2: Dynamic recognition</span></span>
<table class="wdg-noborder">
<tr>
<td>

![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/challenge-icon.png)

</td>
<td>

<span data-ttu-id="702d8-239">Für dieses Lernprogramm muss eine Schaltfläche zum Initiieren der Erkennung gedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="702d8-239">For this tutorial, we require that a button be pressed to initiate recognition.</span></span> <span data-ttu-id="702d8-240">Sie können auch dynamische Erkennung mithilfe einer einfachen Timing-Funktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="702d8-240">You can also perform dynamic recognition by using a basic timing function.</span></span>

<span data-ttu-id="702d8-241">Weitere Informationen zur dynamischen Handschrifterkennung finden Sie unter [Windows Ink-Striche als Text erkennen](convert-ink-to-text.md).</span><span class="sxs-lookup"><span data-stu-id="702d8-241">For more details about dynamic recognition, see [Recognize Windows Ink strokes as text](convert-ink-to-text.md).</span></span>

</td>
</tr>
</table>

## <a name="step-6-recognize-shapes"></a><span data-ttu-id="702d8-242">Schritt6: Erkennen von Formen</span><span class="sxs-lookup"><span data-stu-id="702d8-242">Step 6: Recognize shapes</span></span>

<span data-ttu-id="702d8-243">OK, nun können Sie also Ihre handschriftlichen Notizen in etwas umwandeln, das etwas lesbarer ist.</span><span class="sxs-lookup"><span data-stu-id="702d8-243">Ok, so now you can convert your handwritten notes into something a little more legible.</span></span> <span data-ttu-id="702d8-244">Aber was ist mit diesem verwackelten Gekritzel aus Ihrem Meeting?</span><span class="sxs-lookup"><span data-stu-id="702d8-244">But what about those shaky, caffeinated doodles from your morning Flowcharters Anonymous meeting?</span></span>

<span data-ttu-id="702d8-245">Anhand einer Freihandeingabenanalyse kann Ihre App auch eine Reihe von Kernformen erkenne, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="702d8-245">Using ink analysis, your app can also recognize a set of core shapes, including:</span></span>

- <span data-ttu-id="702d8-246">Kreis</span><span class="sxs-lookup"><span data-stu-id="702d8-246">Circle</span></span>
- <span data-ttu-id="702d8-247">Diamant</span><span class="sxs-lookup"><span data-stu-id="702d8-247">Diamond</span></span>
- <span data-ttu-id="702d8-248">Zeichnung</span><span class="sxs-lookup"><span data-stu-id="702d8-248">Drawing</span></span>
- <span data-ttu-id="702d8-249">Ellipse</span><span class="sxs-lookup"><span data-stu-id="702d8-249">Ellipse</span></span>
- <span data-ttu-id="702d8-250">Gleichseitiges Dreieck</span><span class="sxs-lookup"><span data-stu-id="702d8-250">EquilateralTriangle</span></span>
- <span data-ttu-id="702d8-251">Sechseck</span><span class="sxs-lookup"><span data-stu-id="702d8-251">Hexagon</span></span>
- <span data-ttu-id="702d8-252">Gleichschenkliges Dreieck</span><span class="sxs-lookup"><span data-stu-id="702d8-252">IsoscelesTriangle</span></span>
- <span data-ttu-id="702d8-253">Parallelogramm</span><span class="sxs-lookup"><span data-stu-id="702d8-253">Parallelogram</span></span>
- <span data-ttu-id="702d8-254">Richtungspfeil</span><span class="sxs-lookup"><span data-stu-id="702d8-254">Pentagon</span></span>
- <span data-ttu-id="702d8-255">Viereckig</span><span class="sxs-lookup"><span data-stu-id="702d8-255">Quadrilateral</span></span>
- <span data-ttu-id="702d8-256">Rechteck</span><span class="sxs-lookup"><span data-stu-id="702d8-256">Rectangle</span></span>
- <span data-ttu-id="702d8-257">Rechtes Dreieck</span><span class="sxs-lookup"><span data-stu-id="702d8-257">RightTriangle</span></span>
- <span data-ttu-id="702d8-258">Quadrat</span><span class="sxs-lookup"><span data-stu-id="702d8-258">Square</span></span>
- <span data-ttu-id="702d8-259">Trapez</span><span class="sxs-lookup"><span data-stu-id="702d8-259">Trapezoid</span></span>
- <span data-ttu-id="702d8-260">Dreieck</span><span class="sxs-lookup"><span data-stu-id="702d8-260">Triangle</span></span>

<span data-ttu-id="702d8-261">In diesem Schritt verwenden wir die Formerkennungsfunktionen von Windows Ink, um unser Gekritzel zu bereinigen.</span><span class="sxs-lookup"><span data-stu-id="702d8-261">In this step, we use the shape-recognition features of Windows Ink to try to clean up your doodles.</span></span>

<span data-ttu-id="702d8-262">In diesem Beispiel werden wir nicht, Freihandstriche nachzuzeichnen (obwohl dies möglich ist).</span><span class="sxs-lookup"><span data-stu-id="702d8-262">For this example, we don't attempt to redraw ink strokes (although that's possible).</span></span> <span data-ttu-id="702d8-263">Stattdessen fügen wir eine standardmäßige Canvas unter der „InkCanvas” ein, in der wir aus den ursprünglichen Freihandstrichen abgeleitete und entsprechende Ellipse- und Polygon-Objekte zeichnen.</span><span class="sxs-lookup"><span data-stu-id="702d8-263">Instead, we add a standard canvas under the InkCanvas where we draw equivalent Ellipse or Polygon objects derived from the original ink.</span></span> <span data-ttu-id="702d8-264">Wir löschen dann die dazugehörigen Freihandstriche.</span><span class="sxs-lookup"><span data-stu-id="702d8-264">We then delete the corresponding ink strokes.</span></span>

### <a name="in-the-sample"></a><span data-ttu-id="702d8-265">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="702d8-265">In the sample:</span></span>
1. <span data-ttu-id="702d8-266">Öffnen Sie die Datei „MainPage.xaml“</span><span class="sxs-lookup"><span data-stu-id="702d8-266">Open the MainPage.xaml file</span></span>
2. <span data-ttu-id="702d8-267">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt6: Erkennen von Formen-->”)</span><span class="sxs-lookup"><span data-stu-id="702d8-267">Find the code marked with the title of this step ("\<!-- Step 6: Recognize shapes -->")</span></span>
3. <span data-ttu-id="702d8-268">Löschen Sie die Kommentare in dieser Zeile.</span><span class="sxs-lookup"><span data-stu-id="702d8-268">Uncomment this line.</span></span>  

``` xaml
   <Canvas x:Name="canvas" />

   And these lines.

    <Button Grid.Row="1" x:Name="recognizeShape" Click="recognizeShape_ClickAsync"
        Content="Recognize shape" 
        Margin="10,10,10,10" />
```

4. <span data-ttu-id="702d8-269">Öffnen Sie die Datei „MainPage.xaml.cs“</span><span class="sxs-lookup"><span data-stu-id="702d8-269">Open the MainPage.xaml.cs file</span></span>
5. <span data-ttu-id="702d8-270">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („Schritt6: Erkennen von Formen”)</span><span class="sxs-lookup"><span data-stu-id="702d8-270">Find the code marked with the title of this step ("// Step 6: Recognize shapes")</span></span>
6. <span data-ttu-id="702d8-271">Löschen Sie die Kommentare in den folgende Zeilen:</span><span class="sxs-lookup"><span data-stu-id="702d8-271">Uncomment these lines:</span></span>  

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

7. <span data-ttu-id="702d8-272">Führen Sie die App aus, zeichnen Sie einige Formen und klicken Sie auf die Schaltfläche **Form erkennen**</span><span class="sxs-lookup"><span data-stu-id="702d8-272">Run the app, draw some shapes, and click the **Recognize shape** button</span></span>

<span data-ttu-id="702d8-273">Hier ist ein Beispiel für ein einfaches Flussdiagramm aus der digitalen Konzeptplanung.</span><span class="sxs-lookup"><span data-stu-id="702d8-273">Here's an example of a rudimentary flowchart from a digital napkin.</span></span>

![Ursprüngliches Freihand-Flussdiagramm](images/ink/ink-app-step6-shapereco1-small.png)

<span data-ttu-id="702d8-275">Hier ist das gleiche Flussdiagramm nach der Formerkennung.</span><span class="sxs-lookup"><span data-stu-id="702d8-275">Here's the same flowchart after shape recognition.</span></span>

![Ursprüngliches Freihand-Flussdiagramm](images/ink/ink-app-step6-shapereco2-small.png)


## <a name="step-7-save-and-load-ink"></a><span data-ttu-id="702d8-277">Schritt7: Speichern und Laden der Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="702d8-277">Step 7: Save and load ink</span></span>

<span data-ttu-id="702d8-278">Sie sind mit dem Kritzeln fertig und Ihnen gefällt, was Sie sehen, würden aber gerne später noch ein paar Änderungen vornehmen?</span><span class="sxs-lookup"><span data-stu-id="702d8-278">So, you're done doodling and you like what you see, but think you might like to tweak a couple of things later?</span></span> <span data-ttu-id="702d8-279">Sie können Ihre Freihandstriche in einer serialisierten Freihandformat-Datei (ISF-Datei) speichern und sie jederzeit für die Bearbeitung erneut laden.</span><span class="sxs-lookup"><span data-stu-id="702d8-279">You can save your ink strokes to an Ink Serialized Format (ISF) file and load them for editing whenever the inspiration strikes.</span></span> 

<span data-ttu-id="702d8-280">Die ISF-Datei ist ein einfaches GIF-Bild mit zusätzlichen Metadaten für alle Eigenschaften und Verhaltensweisen von Freihandstrichen.</span><span class="sxs-lookup"><span data-stu-id="702d8-280">The ISF file is a basic GIF image that includes additional metadata describing ink-stroke properties and behaviors.</span></span> <span data-ttu-id="702d8-281">Apps, die nicht für die Freihandeingabe aktiviert sind, können die zusätzlichen Metadaten ignorieren und trotzdem das einfache GIF-Bild (einschließlich Alphakanal-Hintergrundtransparenz) laden.</span><span class="sxs-lookup"><span data-stu-id="702d8-281">Apps that are not ink enabled can ignore the extra metadata and still load the basic GIF image (including alpha-channel background transparency).</span></span>

<span data-ttu-id="702d8-282">In diesem Schritt verknüpfen wir die Schaltflächen **Speichern** und **Laden**, die sich neben der Symbolleiste befinden.</span><span class="sxs-lookup"><span data-stu-id="702d8-282">In this step, we hook up the **Save** and **Load** buttons located beside the ink toolbar.</span></span>

### <a name="in-the-sample"></a><span data-ttu-id="702d8-283">Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="702d8-283">In the sample:</span></span>
1. <span data-ttu-id="702d8-284">Öffnen Sie die Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="702d8-284">Open the MainPage.xaml file.</span></span>
2. <span data-ttu-id="702d8-285">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt7: Speichern und Laden von Freihanddaten-->”).</span><span class="sxs-lookup"><span data-stu-id="702d8-285">Find the code marked with the title of this step ("\<!-- Step 7: Saving and loading ink -->").</span></span>
3. <span data-ttu-id="702d8-286">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="702d8-286">Uncomment the following lines.</span></span> 

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

4. <span data-ttu-id="702d8-287">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="702d8-287">Open the MainPage.xaml.cs file.</span></span>
5. <span data-ttu-id="702d8-288">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („// Schritt7: Speichern und Laden von Freihanddaten”).</span><span class="sxs-lookup"><span data-stu-id="702d8-288">Find the code marked with the title of this step ("// Step 7: Save and load ink").</span></span>
6. <span data-ttu-id="702d8-289">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="702d8-289">Uncomment the following lines.</span></span>  

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

7. <span data-ttu-id="702d8-290">Führen Sie die App aus und zeichnen Sie etwas.</span><span class="sxs-lookup"><span data-stu-id="702d8-290">Run the app and draw something.</span></span>
8. <span data-ttu-id="702d8-291">Wählen Sie die Schaltfläche **Speichern** und speichern Sie die Zeichnung.</span><span class="sxs-lookup"><span data-stu-id="702d8-291">Select the **Save** button and save your drawing.</span></span>
9. <span data-ttu-id="702d8-292">Löschen Sie die Freihandeingabe, oder starten Sie die App neu.</span><span class="sxs-lookup"><span data-stu-id="702d8-292">Erase the ink or restart the app.</span></span>
10. <span data-ttu-id="702d8-293">Wählen Sie die Schaltfläche **Laden** und öffnen Sie die Freihandeingabedatei, die Sie gerade gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="702d8-293">Select the **Load** button and open the ink file you just saved.</span></span>

### <a name="challenge-use-the-clipboard-to-copy-and-paste-ink-strokes"></a><span data-ttu-id="702d8-294">Herausforderung: Verwenden Sie die Zwischenablage, um die Freihandstriche zu kopieren und einzufügen.</span><span class="sxs-lookup"><span data-stu-id="702d8-294">Challenge: Use the clipboard to copy and paste ink strokes</span></span> 
<table class="wdg-noborder">
<tr>
<td>

![InkToolbar aus dem Skizzenblock im Ink-Arbeitsbereich](images/challenge-icon.png)

</td>

<td>

<span data-ttu-id="702d8-296">Windows-Freihandeingabe unterstützt auch das Kopieren und Einfügen von Freihandstrichen zur und aus der Zwischenablage.</span><span class="sxs-lookup"><span data-stu-id="702d8-296">Windows ink also supports copying and pasting ink strokes to and from the clipboard.</span></span>

<span data-ttu-id="702d8-297">Weitere Informationen zur Verwendung der Zwischenablage mit Freihandeingabe finden Sie unter [Speichern und Abrufen von Windows Ink](save-and-load-ink.md).</span><span class="sxs-lookup"><span data-stu-id="702d8-297">For more details about using the clipboard with ink, see [Store and retrieve Windows Ink stroke data](save-and-load-ink.md).</span></span>

</td>
</tr>
</table>

## <a name="summary"></a><span data-ttu-id="702d8-298">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="702d8-298">Summary</span></span>

<span data-ttu-id="702d8-299">Herzlichen Glückwunsch, Sie haben das Lernprogramm **Eingaben: Unterstützen von Freihanddaten in Ihrer UWP-App** abgeschlossen!</span><span class="sxs-lookup"><span data-stu-id="702d8-299">Congratulations, you've completed the **Input: Support ink in your UWP app** tutorial !</span></span> <span data-ttu-id="702d8-300">Ihnen wurde der grundlegende Code gezeigt, der für die Unterstützung von Freihanddaten in Ihren UWP-Apps erforderlich ist, und wie Sie Ihren Benutzern umfangreichere Erfahrungen in der Windows Ink-Plattform bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="702d8-300">We showed you the basic code required for supporting ink in your UWP apps, and how to provide some of the richer user experiences supported by the Windows Ink platform.</span></span>

## <a name="related-articles"></a><span data-ttu-id="702d8-301">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="702d8-301">Related articles</span></span>

* [<span data-ttu-id="702d8-302">Stiftinteraktionen und Windows Ink in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="702d8-302">Pen interactions and Windows Ink in UWP apps</span></span>](pen-and-stylus-interactions.md)

### <a name="samples"></a><span data-ttu-id="702d8-303">Beispiele</span><span class="sxs-lookup"><span data-stu-id="702d8-303">Samples</span></span>

* [<span data-ttu-id="702d8-304">Freihandeingabenanalyse (einfach) (C#)</span><span class="sxs-lookup"><span data-stu-id="702d8-304">Ink analysis sample (basic) (C#)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-analysis-basic.zip)
* [<span data-ttu-id="702d8-305">Beispiel für Freihandschrifterkennung (C#)</span><span class="sxs-lookup"><span data-stu-id="702d8-305">Ink handwriting recognition sample (C#)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-handwriting-reco.zip)
* [<span data-ttu-id="702d8-306">Speichern und Laden von Freihandstrichen aus einer ISF-Datei (Ink Serialized Format)</span><span class="sxs-lookup"><span data-stu-id="702d8-306">Save and load ink strokes from an Ink Serialized Format (ISF) file</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store.zip)
* [<span data-ttu-id="702d8-307">Speichern und Laden von Freihandstrichen aus der Zwischenablage</span><span class="sxs-lookup"><span data-stu-id="702d8-307">Save and load ink strokes from the clipboard</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store-clipboard.zip)
* [<span data-ttu-id="702d8-308">Beispiel für Position und Ausrichtung der Freihandsymbolleiste (einfach)</span><span class="sxs-lookup"><span data-stu-id="702d8-308">Ink toolbar location and orientation sample (basic)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness.zip)
* [<span data-ttu-id="702d8-309">Beispiel für Position und Ausrichtung der Freihandsymbolleiste (dynamisch)</span><span class="sxs-lookup"><span data-stu-id="702d8-309">Ink toolbar location and orientation sample (dynamic)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness-dynamic.zip)
* [<span data-ttu-id="702d8-310">Einfaches Freihandbeispiel (C#/C++)</span><span class="sxs-lookup"><span data-stu-id="702d8-310">Simple ink sample (C#/C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620312)
* [<span data-ttu-id="702d8-311">Komplexes Freihandbeispiel (C++)</span><span class="sxs-lookup"><span data-stu-id="702d8-311">Complex ink sample (C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620314)
* [<span data-ttu-id="702d8-312">Freihandbeispiel (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="702d8-312">Ink sample (JavaScript)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620308)
* [<span data-ttu-id="702d8-313">Lernprogramm „Erste Schritte:” Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="702d8-313">Get Started Tutorial: Support ink in your UWP app</span></span>](https://aka.ms/appsample-ink)
* [<span data-ttu-id="702d8-314">Malbuchbeispiel</span><span class="sxs-lookup"><span data-stu-id="702d8-314">Coloring book sample</span></span>](https://aka.ms/cpubsample-coloringbook)
* [<span data-ttu-id="702d8-315">Familiennotizbeispiel</span><span class="sxs-lookup"><span data-stu-id="702d8-315">Family notes sample</span></span>](https://aka.ms/cpubsample-familynotessample)
