---
author: Karl-Bridge-Microsoft
ms.assetid: ''
title: Unterstützen von Surface Dial (und anderen Radgeräten) in Ihrer UWP-App
description: Eine ausführliche Anleitung zum Hinzufügen der Unterstützung für das Surface Dial (und anderen Radgeräten) zu Ihrer UWP-App.
keywords: Drehsteuerung, radial, Lernprogramm
ms.author: kbridge
ms.date: 01/25/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: e08208b7086023654b0b2404cccc8664e123d9ec
ms.sourcegitcommit: ce45a2bc5ca6794e97d188166172f58590e2e434
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "1983615"
---
# <a name="tutorial-support-the-surface-dial-and-other-wheel-devices-in-your-uwp-app"></a><span data-ttu-id="27f2e-104">Lernprogramm: Unterstützen von Surface Dial (und anderen Radgeräten) in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="27f2e-104">Tutorial: Support the Surface Dial (and other wheel devices) in your UWP app</span></span>

![Abbildung: Surface Dial mit Surface Studio](images/radialcontroller/dial-pen-studio-600px.png)  
<span data-ttu-id="27f2e-106">*Surface Dial mit Surface Studio und Surface-Stift* (im [Microsoft Store](https://aka.ms/purchasesurfacedial) käuflich erhältlich).</span><span class="sxs-lookup"><span data-stu-id="27f2e-106">*Surface Dial with Surface Studio and Surface Pen* (available for purchase at the [Microsoft Store](https://aka.ms/purchasesurfacedial)).</span></span>

<span data-ttu-id="27f2e-107">In diesem Lernprogramm erfahren Sie, wie Sie die von Radgeräten wie Surface Dial unterstützte Benutzerinteraktionen anpassen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-107">This tutorial steps through how to customize the user interaction experiences supported by wheel devices such as the Surface Dial.</span></span> <span data-ttu-id="27f2e-108">Wie verwenden Codeausschnitte aus einer Beispiel-App, die Sie von GitHub herunterladen können (Siehe [Beispielcode](#sample-code)), um die verschiedenen Features und zugehörigen [**RadialController**](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller)-APIs zu veranschaulichen, die in den einzelnen Schrittenbeschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-108">We use snippets from a sample app, which you can download from GitHub (see [Sample code](#sample-code)), to demonstrate the various features and associated [**RadialController**](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller) APIs discussed in each step.</span></span>

<span data-ttu-id="27f2e-109">Wir konzentrieren uns auf Folgendes:</span><span class="sxs-lookup"><span data-stu-id="27f2e-109">We focus on the following:</span></span>
* <span data-ttu-id="27f2e-110">Angeben, welche integrierten Tools in dem [**RadialController**](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller)-Menü angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-110">Specifying which built-in tools are displayed on the [**RadialController**](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller) menu</span></span>
* <span data-ttu-id="27f2e-111">Hinzufügen eines benutzerdefinierten Tools zum Menü</span><span class="sxs-lookup"><span data-stu-id="27f2e-111">Adding a custom tool to the menu</span></span>
* <span data-ttu-id="27f2e-112">Steuern des haptischen Feedbacks</span><span class="sxs-lookup"><span data-stu-id="27f2e-112">Controlling haptic feedback</span></span>
* <span data-ttu-id="27f2e-113">Anpassen der Klick-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="27f2e-113">Customizing click interactions</span></span>
* <span data-ttu-id="27f2e-114">Anpassen der Drehinteraktionen</span><span class="sxs-lookup"><span data-stu-id="27f2e-114">Customizing rotation interactions</span></span>

<span data-ttu-id="27f2e-115">Weitere Informationen zur Implementierung dieser und anderer Features finden Sie unter [Surface Dial-Interaktionen in UWP-Apps](windows-wheel-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="27f2e-115">For more about implementing these and other features, see [Surface Dial interactions in UWP apps](windows-wheel-interactions.md).</span></span>

## <a name="introduction"></a><span data-ttu-id="27f2e-116">Einführung</span><span class="sxs-lookup"><span data-stu-id="27f2e-116">Introduction</span></span>

<span data-ttu-id="27f2e-117">Das Surface Dial ist ein sekundäres Eingabegerät, mit dem Benutzer zusammen mit einem primären Eingabegerät wie Stift, Toucheingabe oder Maus produktiver sein können.</span><span class="sxs-lookup"><span data-stu-id="27f2e-117">The Surface Dial is a secondary input device that helps users to be more productive when used together with a primary input device such as pen, touch, or mouse.</span></span> <span data-ttu-id="27f2e-118">Als sekundäres Eingabegerät wird das Dial in der Regel mit der nicht dominanten Hand verwendet, um den Zugriff auf Systembefehle und andere kontextbezogene Tools und Funktionen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-118">As a secondary input device, the Dial is typically used with the non-dominant hand to provide access both to system commands and to other, more contextual, tools and functionality.</span></span> 

<span data-ttu-id="27f2e-119">Das Dial unterstützt drei grundlegende Gesten:</span><span class="sxs-lookup"><span data-stu-id="27f2e-119">The Dial supports three basic gestures:</span></span> 
- <span data-ttu-id="27f2e-120">Drücken Sie und halten Sie, um das integrierte Menü mit Befehlen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-120">Press and hold to display the built-in menu of commands.</span></span>
- <span data-ttu-id="27f2e-121">Drehen Sie zum Markieren eines Menüelements (wenn das Menü aktiv ist) oder zum Ändern der aktuelle Aktion in der App (wenn das Menü nicht aktiv ist).</span><span class="sxs-lookup"><span data-stu-id="27f2e-121">Rotate to highlight a menu item (if the menu is active) or to modify the current action in the app (if the menu is not active).</span></span>
- <span data-ttu-id="27f2e-122">Klicken Sie, um das hervorgehobene Menüelement auswählen (wenn das Menü aktiv ist) oder um einen Befehl in der App aufzurufen (wenn das Menü nicht aktiv ist).</span><span class="sxs-lookup"><span data-stu-id="27f2e-122">Click to select the highlighted menu item (if the menu is active) or to invoke a command in the app (if the menu is not active).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27f2e-123">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="27f2e-123">Prerequisites</span></span>

* <span data-ttu-id="27f2e-124">Ein Computer (oder ein virtueller Computer) mit Windows 10 Creators Update oder höher</span><span class="sxs-lookup"><span data-stu-id="27f2e-124">A computer (or a virtual machine) running Windows 10 Creators Update, or newer</span></span>
* [<span data-ttu-id="27f2e-125">Visual Studio 2017 (10.0.15063.0)</span><span class="sxs-lookup"><span data-stu-id="27f2e-125">Visual Studio 2017 (10.0.15063.0)</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="27f2e-126">Windows 10 SDK (10.0.15063.0)</span><span class="sxs-lookup"><span data-stu-id="27f2e-126">Windows 10 SDK (10.0.15063.0)</span></span>](https://developer.microsoft.com/windows/downloads/windows-10-sdk)
* <span data-ttu-id="27f2e-127">Ein Radgerät (aktuell nur die [Surface Dial](https://aka.ms/purchasesurfacedial))</span><span class="sxs-lookup"><span data-stu-id="27f2e-127">A wheel device (only the [Surface Dial](https://aka.ms/purchasesurfacedial) at this time)</span></span>
* <span data-ttu-id="27f2e-128">Wenn Sie noch keine Erfahrung mit der App-Entwicklung in der Universellen Windows-Plattform (UWP) mit Visual Studio haben, werfen Sie einen Blick in diese Themen, bevor Sie dieses Lernprogramm starten:</span><span class="sxs-lookup"><span data-stu-id="27f2e-128">If you're new to Universal Windows Platform (UWP) app development with Visual Studio, have a look through these topics before you start this tutorial:</span></span>  
    * [<span data-ttu-id="27f2e-129">Vorbereiten</span><span class="sxs-lookup"><span data-stu-id="27f2e-129">Get set up</span></span>](https://docs.microsoft.com/windows/uwp/get-started/get-set-up)
    * [<span data-ttu-id="27f2e-130">Erstellen der App „Hello, world“ (XAML)</span><span class="sxs-lookup"><span data-stu-id="27f2e-130">Create a "Hello, world" app (XAML)</span></span>](https://docs.microsoft.com/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)

## <a name="set-up-your-devices"></a><span data-ttu-id="27f2e-131">Einrichten Ihrer Geräte</span><span class="sxs-lookup"><span data-stu-id="27f2e-131">Set up your devices</span></span>

1. <span data-ttu-id="27f2e-132">Stellen Sie sicher, dass Ihr Windows-Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="27f2e-132">Make sure your Windows device is on.</span></span>
2. <span data-ttu-id="27f2e-133">Wechseln Sie zu **Start** und wählen Sie **Einstellungen** > **Geräte** > **Bluetooth & andere Geräte** und schalten Sie **Bluetooth** an.</span><span class="sxs-lookup"><span data-stu-id="27f2e-133">Go to **Start**, select **Settings** > **Devices** > **Bluetooth & other devices**, and then turn **Bluetooth** on.</span></span>
3. <span data-ttu-id="27f2e-134">Entfernen Sie die Unterseite der Surface Dial, um das Batteriefach zu öffnen, und stellen Sie sicher, dass es zwei AAA-Batterien enthält.</span><span class="sxs-lookup"><span data-stu-id="27f2e-134">Remove the bottom of the Surface Dial to open the battery compartment, and make sure that there are two AAA batteries inside.</span></span>
4. <span data-ttu-id="27f2e-135">Entfernen Sie falls nötig an der Unterseite der Dial den Batteriedeckel.</span><span class="sxs-lookup"><span data-stu-id="27f2e-135">If the battery tab is present on the underside of the Dial, remove it.</span></span>
5. <span data-ttu-id="27f2e-136">Drücken und halten Sie den kleinen eingesetzten Knopf neben den Batterien, bis das Bluetooth-Licht aufleuchtet.</span><span class="sxs-lookup"><span data-stu-id="27f2e-136">Press and hold the small, inset button next to the batteries until the Bluetooth light flashes.</span></span>
6. <span data-ttu-id="27f2e-137">Wechseln Sie zurück zu Ihrem Windows-Gerät und wählen Sie **Bluetooth oder ein anderes Gerät hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="27f2e-137">Go back to your Windows device and select **Add Bluetooth or other device**.</span></span>
7. <span data-ttu-id="27f2e-138">Wählen Sie im Dialogfeld **Hinzufügen eines Geräts** **Bluetooth** > **Surface Dial**.</span><span class="sxs-lookup"><span data-stu-id="27f2e-138">In the **Add a device** dialog, select **Bluetooth** > **Surface Dial**.</span></span> <span data-ttu-id="27f2e-139">Ihre Surface Dial sollte jetzt eine Verbindung herstellen und der Liste der Geräte unter **Maus, Tastatur und Stift** auf der Einstellungsseite **Bluetooth & andere Geräte** hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-139">Your Surface Dial should now connect and be added to the list of devices under **Mouse, keyboard, & pen** on the **Bluetooth & other devices** settings page.</span></span>
8. <span data-ttu-id="27f2e-140">Testen Sie das Dial, indem Sie sie einige Sekunden lang gedrückt halten, um das integrierte Menü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-140">Test the Dial by pressing and holding it down for a few seconds to display the built-in menu.</span></span>
9. <span data-ttu-id="27f2e-141">Wenn das Menü nicht auf Ihrem Bildschirm angezeigt wird (das Dial sollte auch Vibrieren), wechseln Sie zurück zu den Bluetooth-Einstellungen, entfernen Sie das Gerät, und versuchen Sie, das Gerät erneut zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-141">If the the menu isn't displayed on your screen (the Dial should also vibrate), go back to the Bluetooth settings, remove the device, and try connecting the device again.</span></span>

> [!NOTE]
> <span data-ttu-id="27f2e-142">Wheel-Geräte können in den **Rad**-Einstellungen angepasst werden:</span><span class="sxs-lookup"><span data-stu-id="27f2e-142">Wheel devices can be configured through the **Wheel** settings:</span></span>
> 1. <span data-ttu-id="27f2e-143">Wählen Sie im **Startmenü** **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="27f2e-143">On the **Start** menu, select **Settings**.</span></span>
> 2. <span data-ttu-id="27f2e-144">Wählen Sie **Geräte** > **Rad**.</span><span class="sxs-lookup"><span data-stu-id="27f2e-144">Select **Devices** > **Wheel**.</span></span>    
> ![Bildschirm „Radeinstellungen”](images/radialcontroller/wheel-settings.png)

<span data-ttu-id="27f2e-146">Jetzt können Sie dieses Lernprogramm starten.</span><span class="sxs-lookup"><span data-stu-id="27f2e-146">Now you’re ready to start this tutorial.</span></span> 

## <a name="sample-code"></a><span data-ttu-id="27f2e-147">Beispielcode</span><span class="sxs-lookup"><span data-stu-id="27f2e-147">Sample code</span></span>
<span data-ttu-id="27f2e-148">In diesem Lernprogramm verwenden wir eine Beispiels-App, um die erläuterten Konzepte und Funktionen zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-148">Throughout this tutorial, we use a sample app to demonstrate the concepts and functionality discussed.</span></span>

<span data-ttu-id="27f2e-149">Laden Sie dieses Visual Studio-Beispiel und den Quellecode von [GitHub](https://github.com/) unter [Windows-App-Beispiel-Erste-Schritte-Radialcontroller-Beispiel](https://aka.ms/appsample-radialcontroller) herunter:</span><span class="sxs-lookup"><span data-stu-id="27f2e-149">Download this Visual Studio sample and source code from [GitHub](https://github.com/) at [windows-appsample-get-started-radialcontroller sample](https://aka.ms/appsample-radialcontroller):</span></span>

1. <span data-ttu-id="27f2e-150">Wählen Sie die grüne Schaltfläche **Klonen oder herunterladen** aus.</span><span class="sxs-lookup"><span data-stu-id="27f2e-150">Select the green **Clone or download** button.</span></span>  
![Klonen des Repositorys](images/radialcontroller/wheel-clone.png)
2. <span data-ttu-id="27f2e-152">Wenn Sie ein GitHub-Konto haben, können Sie das Repository auf Ihrem lokalen Computer mit der Option **In Visual Studio öffnen** klonen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-152">If you have a GitHub account, you can clone the repo to your local machine by choosing **Open in Visual Studio**.</span></span> 
3. <span data-ttu-id="27f2e-153">Wenn Sie kein GitHub-Konto haben, oder wenn Sie einfach eine lokale Kopie des Projekts möchten, wählen Sie **Herunterladen der ZIP-Datei** (Sie müssen regelmäßig auf neues Updates prüfen).</span><span class="sxs-lookup"><span data-stu-id="27f2e-153">If you don't have a GitHub account, or you just want a local copy of the project, choose **Download ZIP** (you'll have to check back regularly to download the latest updates).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27f2e-154">Der Großteil des Codes im Beispiel ist als Kommentar formatiert. Bei den einzelnen Schritten in diesem Thema werden Sie aufgefordert, die Kommentare der verschiedenen Codeabschnitte zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-154">Most of the code in the sample is commented out. As we go through each step in this topic, you'll be asked to uncomment various sections of the code.</span></span> <span data-ttu-id="27f2e-155">Markieren Sie einfach in Visual Studio die Codezeilen und drücken Sie STRG+K und anschließend STRG + U.</span><span class="sxs-lookup"><span data-stu-id="27f2e-155">In Visual Studio, just highlight the lines of code, and press CTRL-K and then CTRL-U.</span></span>

## <a name="components-that-support-wheel-functionality"></a><span data-ttu-id="27f2e-156">Komponenten, die Radfunktionen unterstützen</span><span class="sxs-lookup"><span data-stu-id="27f2e-156">Components that support wheel functionality</span></span>

<span data-ttu-id="27f2e-157">Diese Objekte bieten den Großteil der Radgerätefunktion für UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="27f2e-157">These objects provide the bulk of the wheel device experience for UWP apps.</span></span>

| <span data-ttu-id="27f2e-158">Komponente</span><span class="sxs-lookup"><span data-stu-id="27f2e-158">Component</span></span> | <span data-ttu-id="27f2e-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="27f2e-159">Description</span></span> |
| --- | --- |
| <span data-ttu-id="27f2e-160">[**RadialController**-Klasse](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController) und die zugehörigen</span><span class="sxs-lookup"><span data-stu-id="27f2e-160">[**RadialController** class](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController) and related</span></span> | <span data-ttu-id="27f2e-161">Stellt einen Radeingabegerät oder -Zubehör, z.B. das Surface Dial, dar.</span><span class="sxs-lookup"><span data-stu-id="27f2e-161">Represents a wheel input device or accessory such as the Surface Dial.</span></span> |
| <span data-ttu-id="27f2e-162">[**IRadialControllerConfigurationInterop**](https://msdn.microsoft.com/library/windows/desktop/mt790709) / [**IRadialControllerInterop**](https://msdn.microsoft.com/library/windows/desktop/mt790711)</span><span class="sxs-lookup"><span data-stu-id="27f2e-162">[**IRadialControllerConfigurationInterop**](https://msdn.microsoft.com/library/windows/desktop/mt790709) / [**IRadialControllerInterop**](https://msdn.microsoft.com/library/windows/desktop/mt790711)</span></span><br/><span data-ttu-id="27f2e-163">Wir gehen hier nicht auf diese Funktionalität ein. Weitere Informationen finden Sie unter der [Klassisches Windows-Desktopbeispiel](https://aka.ms/radialcontrollerclassicsample).</span><span class="sxs-lookup"><span data-stu-id="27f2e-163">We do not cover this functionality here, for more information, see the [Windows classic desktop sample](https://aka.ms/radialcontrollerclassicsample).</span></span> | <span data-ttu-id="27f2e-164">Ermöglicht die Interoperabilität mit einer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="27f2e-164">Enables interoperability with a UWP app.</span></span> |

## <a name="step-1-run-the-sample"></a><span data-ttu-id="27f2e-165">Schritt1: Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="27f2e-165">Step 1: Run the sample</span></span>

<span data-ttu-id="27f2e-166">Nachdem Sie die RadialController-Beispiel-App heruntergeladen haben, stellen Sie sicher, dass sie ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="27f2e-166">After you've downloaded the RadialController sample app, verify that it runs:</span></span>
1. <span data-ttu-id="27f2e-167">Öffnen Sie das Beispielprojekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27f2e-167">Open the sample project in Visual Studio .</span></span>
2. <span data-ttu-id="27f2e-168">Legen Sie das **Lösungsplattformen**-Dropdownmenü für eine nicht ARM-Auswahl fest.</span><span class="sxs-lookup"><span data-stu-id="27f2e-168">Set the **Solution Platforms** dropdown to a non-ARM selection.</span></span>
3. <span data-ttu-id="27f2e-169">Drücken Sie F5, um zu kompilieren, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-169">Press F5 to compile, deploy, and run.</span></span> 

> [!NOTE]
> <span data-ttu-id="27f2e-170">Alternativ können Sie das Menüelement **Debuggen** > **"Debuggen starten"** oder die Schaltfläche **lokale Maschine** ausführen, die hier dargestellt wird: ![Visual Studio-Projektschaltfläche</span><span class="sxs-lookup"><span data-stu-id="27f2e-170">Alternatively, you can select **Debug** > **Start debugging** menu item, or select the **Local Machine** Run button shown here: ![Visual Studio Build project button</span></span>](images/radialcontroller/wheel-vsrun.png)

<span data-ttu-id="27f2e-171">Das App-Fenster wird geöffnet und nach einem Begrüßungsbildschirm wird der Startbildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27f2e-171">The app window opens, and after a splash screen appears for a few seconds, you’ll see this initial screen.</span></span>

![Leere App](images/radialcontroller/wheel-app-step1-empty.png)

<span data-ttu-id="27f2e-173">OK, nun haben wir die grundlegende UWP-App, die wir im verbleibenden Teil dieses Lernprogramms verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-173">Okay, we now have the basic UWP app that we’ll use throughout the rest of this tutorial.</span></span> <span data-ttu-id="27f2e-174">In den folgenden Schrittenfügen wir unsere **RadialController**-Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="27f2e-174">In the following steps, we add our **RadialController** functionality.</span></span>

## <a name="step-2-basic-radialcontroller-functionality"></a><span data-ttu-id="27f2e-175">Schritt2: Grundlegende RadialController-Funktionen</span><span class="sxs-lookup"><span data-stu-id="27f2e-175">Step 2: Basic RadialController functionality</span></span>

<span data-ttu-id="27f2e-176">Halten Sie das Surface Dial gedrückt, während die App im Vordergrund ausgeführt wird, um das ** RadialController **-Menü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-176">With the app running and in the foreground, press and hold the Surface Dial to display the **RadialController ** menu.</span></span>

<span data-ttu-id="27f2e-177">Wir haben unsere App noch nicht angepasst, sodass das Menü einen Standardsatz von kontextbezogenen Tools enthält.</span><span class="sxs-lookup"><span data-stu-id="27f2e-177">We haven't done any customization for our app yet, so the menu contains a default set of contextual tools.</span></span> 

<span data-ttu-id="27f2e-178">Diese Abbildungen zeigen zwei Varianten des Standardmenüs.</span><span class="sxs-lookup"><span data-stu-id="27f2e-178">These images show two variations of the default menu.</span></span> <span data-ttu-id="27f2e-179">(Es gibt viele andere, einschließlich grundlegende Systemprogramme, wenn der Windows-Desktop aktiv ist und keine Apps im Vordergrund ausgeführt werden, zusätzliche Freihand-Tools, wenn eine InkToolbar vorhanden ist, und Zuordnungs-Tools, wenn Sie die Karten-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-179">(There are many others, including just basic system tools when the Windows Desktop is active and no apps are in the foreground, additional inking tools when an InkToolbar is present, and mapping tools when you’re using the Maps app.</span></span>

| <span data-ttu-id="27f2e-180">RadialController-Menü (Standard)</span><span class="sxs-lookup"><span data-stu-id="27f2e-180">RadialController menu (default)</span></span>  | <span data-ttu-id="27f2e-181">RadialController-Menü (Standard bei der Wiedergabe von Medien)</span><span class="sxs-lookup"><span data-stu-id="27f2e-181">RadialController menu (default with media playing)</span></span>  |
|---|---|
| ![RadialController-Standardmenü](images/radialcontroller/wheel-app-step2-basic-default.png) | ![RadialController-Standardmenü mit Musik](images/radialcontroller/wheel-app-step2-basic-withmusic.png) |

<span data-ttu-id="27f2e-184">Jetzt werden wir einige grundlegende Anpassungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-184">Now we'll start with some basic customization.</span></span>

## <a name="step-3-add-controls-for-wheel-input"></a><span data-ttu-id="27f2e-185">Schritt3: Hinzufügen von Steuerelementen für die Radeingabe</span><span class="sxs-lookup"><span data-stu-id="27f2e-185">Step 3: Add controls for wheel input</span></span>

<span data-ttu-id="27f2e-186">Fügen wir zunächst die Benutzeroberfläche für unsere App hinzu:</span><span class="sxs-lookup"><span data-stu-id="27f2e-186">First, let's add the UI for our app:</span></span>

1. <span data-ttu-id="27f2e-187">Öffnen Sie die Datei „MainPage_Basic.xaml“.</span><span class="sxs-lookup"><span data-stu-id="27f2e-187">Open the MainPage_Basic.xaml file.</span></span>
2. <span data-ttu-id="27f2e-188">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („\ <!--Schritt3: Hinzufügen von Steuerelementen für die Eingabe des Mausrads-->”).</span><span class="sxs-lookup"><span data-stu-id="27f2e-188">Find the code marked with the title of this step ("\<!-- Step 3: Add controls for wheel input -->").</span></span>
3. <span data-ttu-id="27f2e-189">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-189">Uncomment the following lines.</span></span>

    ```xaml
    <Button x:Name="InitializeSampleButton" 
            HorizontalAlignment="Center" 
            Margin="10" 
            Content="Initialize sample" />
    <ToggleButton x:Name="AddRemoveToggleButton"
                    HorizontalAlignment="Center" 
                    Margin="10" 
                    Content="Remove Item"
                    IsChecked="True" 
                    IsEnabled="False"/>
    <Button x:Name="ResetControllerButton" 
            HorizontalAlignment="Center" 
            Margin="10" 
            Content="Reset RadialController menu" 
            IsEnabled="False"/>
    <Slider x:Name="RotationSlider" Minimum="0" Maximum="10"
            Width="300"
            HorizontalAlignment="Center"/>
    <TextBlock Text="{Binding ElementName=RotationSlider, Mode=OneWay, Path=Value}"
                Margin="0,0,0,20"
                HorizontalAlignment="Center"/>
    <ToggleSwitch x:Name="ClickToggle"
                    MinWidth="0" 
                    Margin="0,0,0,20"
                    HorizontalAlignment="center"/>
    ```
<span data-ttu-id="27f2e-190">An dieser Stelle sind nur die **Initialisierungsbeispiel**-Schaltfläche, Schieberegler und Ein/Aus-Schalter aktiviert.</span><span class="sxs-lookup"><span data-stu-id="27f2e-190">At this point, only the **Initialize sample** button, slider, and toggle switch are enabled.</span></span> <span data-ttu-id="27f2e-191">Die anderen Schaltflächen werden in späteren Schritten verwendet, um **RadialController**-Menüelemente, die den Zugriff auf die Schieberegler und Umschalter bereitstellen, hinzuzufügen und zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-191">The other buttons are used in later steps to add and remove **RadialController** menu items that provide access to the slider and toggle switch.</span></span>

![Grundlegendes Beispiel für die App-UI](images/radialcontroller/wheel-app-step3-basicui.png)

## <a name="step-4-customize-the-basic-radialcontroller-menu"></a><span data-ttu-id="27f2e-193">Schritt 4: Anpassen des grundlegenden RadialController-Menüs</span><span class="sxs-lookup"><span data-stu-id="27f2e-193">Step 4: Customize the basic RadialController menu</span></span>

<span data-ttu-id="27f2e-194">Fügen wir nun den für den **RadialController**-Zugriff auf unsere Steuerelemente erforderlichen Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="27f2e-194">Now let's add the code required to enable **RadialController** access to our controls.</span></span>

1. <span data-ttu-id="27f2e-195">Öffnen Sie die Datei „MainPage_Basic.xaml.cs”.</span><span class="sxs-lookup"><span data-stu-id="27f2e-195">Open the MainPage_Basic.xaml.cs file.</span></span>
2. <span data-ttu-id="27f2e-196">Suchen Sie den Code, der mit dem Titel in dieses Schritts gekennzeichnet ist („/ / Schritt4: grundlegende RadialController Anpassung für das Menü”).</span><span class="sxs-lookup"><span data-stu-id="27f2e-196">Find the code marked with the title of this step ("// Step 4: Basic RadialController menu customization").</span></span>
3. <span data-ttu-id="27f2e-197">Entfernen Sie die Kommentare aus den folgenden Zeilen:</span><span class="sxs-lookup"><span data-stu-id="27f2e-197">Uncomment the following lines:</span></span>
    - <span data-ttu-id="27f2e-198">Die [Windows.UI.Input](https://docs.microsoft.com/uwp/api/windows.ui.input) und [Windows.Storage.Streams](https://docs.microsoft.com/uwp/api/windows.storage.streams)-Typenverweise werden für Funktionen in den folgenden Schritten verwendet:</span><span class="sxs-lookup"><span data-stu-id="27f2e-198">The [Windows.UI.Input](https://docs.microsoft.com/uwp/api/windows.ui.input) and [Windows.Storage.Streams](https://docs.microsoft.com/uwp/api/windows.storage.streams) type references are used for functionality in subsequent steps:</span></span>  
    
        ```csharp
        // Using directives for RadialController functionality.
        using Windows.UI.Input;
        ```

    - <span data-ttu-id="27f2e-199">Diese globalen Objekte ([RadialController](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller), [RadialControllerConfiguration](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollerconfiguration), [RadialControllerMenuItem](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollermenuitem)) werden in der App verwendet.</span><span class="sxs-lookup"><span data-stu-id="27f2e-199">These global objects ([RadialController](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller), [RadialControllerConfiguration](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollerconfiguration), [RadialControllerMenuItem](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollermenuitem)) are used throughout our app.</span></span>
    
        ```csharp
        private RadialController radialController;
        private RadialControllerConfiguration radialControllerConfig;
        private RadialControllerMenuItem radialControllerMenuItem;
        ```

    - <span data-ttu-id="27f2e-200">Hier geben wir den **Klick**-Ereignishandler für die Schaltfläche an, die unsere Steuerelemente aktiviert und das benutzerdefinierte **RadialController**-Menüelement initialisiert.</span><span class="sxs-lookup"><span data-stu-id="27f2e-200">Here, we specify the **Click** handler for the button that enables our controls and initializes our custom **RadialController** menu item.</span></span>

        ```csharp
        InitializeSampleButton.Click += (sender, args) =>
        { InitializeSample(sender, args); };
        ``` 

    - <span data-ttu-id="27f2e-201">Als Nächstes initialisieren wir unser [RadialController](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller)-Objekt, und richten Ereignishandler für die [RotationChanged](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.RotationChanged) und [ButtonClicked](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.ButtonClicked)-Ereignisse ein.</span><span class="sxs-lookup"><span data-stu-id="27f2e-201">Next, we initialize our [RadialController](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller) object and set up handlers for the [RotationChanged](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.RotationChanged) and [ButtonClicked](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.ButtonClicked) events.</span></span>

        ```csharp
        // Set up the app UI and RadialController.
        private void InitializeSample(object sender, RoutedEventArgs e)
        {
            ResetControllerButton.IsEnabled = true;
            AddRemoveToggleButton.IsEnabled = true;

            ResetControllerButton.Click += (resetsender, args) =>
            { ResetController(resetsender, args); };
            AddRemoveToggleButton.Click += (togglesender, args) =>
            { AddRemoveItem(togglesender, args); };

            InitializeController(sender, e);
        }
        ```

    - <span data-ttu-id="27f2e-202">Hier initialisieren wir unser benutzerdefiniertes RadialController-Menüelement.</span><span class="sxs-lookup"><span data-stu-id="27f2e-202">Here, we initialize our custom RadialController menu item.</span></span> <span data-ttu-id="27f2e-203">Wir verwenden [CreateForCurrentView](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.CreateForCurrentView), um einen Verweis auf unser [RadialController](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller)-Objekt zu erhalten, wir legen die Drehempfindlichkeit mit der [RotationResolutionInDegrees](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.RotationResolutionInDegrees)-Eigenschaft auf „1” fest, anschließend erstellen wir unser [RadialControllerMenuItem](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollermenuitem) mit [CreateFromFontGlyph](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollermenuitem.CreateFromFontGlyph), wir fügen das Menüelement zu der Sammlung von **RadialController**-Menüelementen und schließlich verwenden wir [SetDefaultMenuItems](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollerconfiguration.setdefaultmenuitems), um die Standard-Menüelemente zu löschen und lassen nur die benutzerdefinierten Tools bestehen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-203">We use [CreateForCurrentView](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.CreateForCurrentView) to get a reference to our [RadialController](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller) object, we set the rotation sensitivity to "1" by using the [RotationResolutionInDegrees](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.RotationResolutionInDegrees) property, we then create our [RadialControllerMenuItem](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollermenuitem) by using [CreateFromFontGlyph](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollermenuitem.CreateFromFontGlyph), we add the menu item to the **RadialController** menu item collection, and finally, we use [SetDefaultMenuItems](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontrollerconfiguration.setdefaultmenuitems) to clear the default menu items and leave only our custom tool.</span></span> 

        ```csharp
        // Configure RadialController menu and custom tool.
        private void InitializeController(object sender, RoutedEventArgs args)
        {
            // Create a reference to the RadialController.
            radialController = RadialController.CreateForCurrentView();
            // Set rotation resolution to 1 degree of sensitivity.
            radialController.RotationResolutionInDegrees = 1;

            // Create the custom menu items.
            // Here, we use a font glyph for our custom tool.
            radialControllerMenuItem =
                RadialControllerMenuItem.CreateFromFontGlyph("SampleTool", "\xE1E3", "Segoe MDL2 Assets");

            // Add the item to the RadialController menu.
            radialController.Menu.Items.Add(radialControllerMenuItem);

            // Remove built-in tools to declutter the menu.
            // NOTE: The Surface Dial menu must have at least one menu item. 
            // If all built-in tools are removed before you add a custom 
            // tool, the default tools are restored and your tool is appended 
            // to the default collection.
            radialControllerConfig =
                RadialControllerConfiguration.GetForCurrentView();
            radialControllerConfig.SetDefaultMenuItems(
                new RadialControllerSystemMenuItemKind[] { });

            // Declare input handlers for the RadialController.
            // NOTE: These events are only fired when a custom tool is active.
            radialController.ButtonClicked += (clicksender, clickargs) =>
            { RadialController_ButtonClicked(clicksender, clickargs); };
            radialController.RotationChanged += (rotationsender, rotationargs) =>
            { RadialController_RotationChanged(rotationsender, rotationargs); };
        }

        // Connect wheel device rotation to slider control.
        private void RadialController_RotationChanged(
            object sender, RadialControllerRotationChangedEventArgs args)
        {
            if (RotationSlider.Value + args.RotationDeltaInDegrees >= RotationSlider.Maximum)
            {
                RotationSlider.Value = RotationSlider.Maximum;
            }
            else if (RotationSlider.Value + args.RotationDeltaInDegrees < RotationSlider.Minimum)
            {
                RotationSlider.Value = RotationSlider.Minimum;
            }
            else
            {
                RotationSlider.Value += args.RotationDeltaInDegrees;
            }
        }

        // Connect wheel device click to toggle switch control.
        private void RadialController_ButtonClicked(
            object sender, RadialControllerButtonClickedEventArgs args)
        {
            ClickToggle.IsOn = !ClickToggle.IsOn;
        }
        ```
4. <span data-ttu-id="27f2e-204">Führen Sie nun erneut die App aus.</span><span class="sxs-lookup"><span data-stu-id="27f2e-204">Now, run the app again.</span></span>
5. <span data-ttu-id="27f2e-205">Wählen Sie die Schaltfläche **Initialisierung eines radialen Controllers**.</span><span class="sxs-lookup"><span data-stu-id="27f2e-205">Select the **Initialize radial controller** button.</span></span>  
6. <span data-ttu-id="27f2e-206">Halten Sie das Surface Dial gedrückt, während die App im Vordergrund ausgeführt wird, um das Menü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-206">With the app in the foreground, press and hold the Surface Dial to display the menu.</span></span> <span data-ttu-id="27f2e-207">Wie Sie sehen, wurden alle standardmäßigen Tools entfernt (unter Verwendung der **RadialControllerConfiguration.SetDefaultMenuItems**-Methode), sodass nur das benutzerdefinierte Tool übrig bleibt.</span><span class="sxs-lookup"><span data-stu-id="27f2e-207">Notice that all default tools have been removed (by using the **RadialControllerConfiguration.SetDefaultMenuItems** method), leaving only the custom tool.</span></span> <span data-ttu-id="27f2e-208">Hier sehen Sie das Menü mit unserem benutzerdefinierten Tool.</span><span class="sxs-lookup"><span data-stu-id="27f2e-208">Here’s the menu with our custom tool.</span></span> 

| <span data-ttu-id="27f2e-209">RadialController-Menü (benutzerdefiniert)</span><span class="sxs-lookup"><span data-stu-id="27f2e-209">RadialController menu (custom)</span></span>  | 
|---|
| ![Benutzerdefiniertes RadialController-Menü](images/radialcontroller/wheel-app-step3-custom.png) |

7. <span data-ttu-id="27f2e-211">Wählen Sie das benutzerdefinierte Tool aus und testen Sie die Interaktionen über die nun unterstützte Surface Dial:</span><span class="sxs-lookup"><span data-stu-id="27f2e-211">Select the custom tool and try out the interactions now supported through the Surface Dial:</span></span>
    * <span data-ttu-id="27f2e-212">Eine Drehaktion bewegt den Schieberegler.</span><span class="sxs-lookup"><span data-stu-id="27f2e-212">A rotate action moves the slider.</span></span> 
    * <span data-ttu-id="27f2e-213">Ein Klick legt den Umschalter auf aktiviert oder deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="27f2e-213">A click sets the toggle to on or off.</span></span>

<span data-ttu-id="27f2e-214">OK, verknüpfen wir nun diese Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-214">Ok, let's hook up those buttons.</span></span>

## <a name="step-5-configure-menu-at-runtime"></a><span data-ttu-id="27f2e-215">Schritt5: Konfigurieren des Menüs zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="27f2e-215">Step 5: Configure menu at runtime</span></span>

<span data-ttu-id="27f2e-216">In diesem Schritt verknüpfen wir die Schaltflächen **Element hinzufügen/entfernen** und **RadialController-Menü zurücksetzen**, um zu zeigen, wie Sie das Menü dynamisch anpassen können.</span><span class="sxs-lookup"><span data-stu-id="27f2e-216">In this step, we hook up the **Add/Remove item** and **Reset RadialController menu** buttons to show how you can dynamically customize the menu.</span></span>

1. <span data-ttu-id="27f2e-217">Öffnen Sie die Datei „MainPage_Basic.xaml.cs”.</span><span class="sxs-lookup"><span data-stu-id="27f2e-217">Open the MainPage_Basic.xaml.cs file.</span></span>
2. <span data-ttu-id="27f2e-218">Suchen Sie den Code, der mit dem Titel in dieses Schritts gekennzeichnet ist („// Schritt5: Konfigurieren von Menü zur Laufzeit”).</span><span class="sxs-lookup"><span data-stu-id="27f2e-218">Find the code marked with the title of this step ("// Step 5: Configure menu at runtime").</span></span>
3. <span data-ttu-id="27f2e-219">Löschen Sie die Kommentare in den folgenden Methoden und führen Sie die App erneut aus. Wählen Sie dabei jedoch keine Schaltflächen aus (sparen Sie sich das für den nächsten Schritt auf).</span><span class="sxs-lookup"><span data-stu-id="27f2e-219">Uncomment the code in the following methods and run the app again, but don't select any buttons (save that for the next step).</span></span>  

    ``` csharp
    // Add or remove the custom tool.
    private void AddRemoveItem(object sender, RoutedEventArgs args)
    {
        if (AddRemoveToggleButton?.IsChecked == true)
        {
            AddRemoveToggleButton.Content = "Remove item";
            if (!radialController.Menu.Items.Contains(radialControllerMenuItem))
            {
                radialController.Menu.Items.Add(radialControllerMenuItem);
            }
        }
        else if (AddRemoveToggleButton?.IsChecked == false)
        {
            AddRemoveToggleButton.Content = "Add item";
            if (radialController.Menu.Items.Contains(radialControllerMenuItem))
            {
                radialController.Menu.Items.Remove(radialControllerMenuItem);
                // Attempts to select and activate the previously selected tool.
                // NOTE: Does not differentiate between built-in and custom tools.
                radialController.Menu.TrySelectPreviouslySelectedMenuItem();
            }
        }
    }

    // Reset the RadialController to initial state.
    private void ResetController(object sender, RoutedEventArgs arg)
    {
        if (!radialController.Menu.Items.Contains(radialControllerMenuItem))
        {
            radialController.Menu.Items.Add(radialControllerMenuItem);
        }
        AddRemoveToggleButton.Content = "Remove item";
        AddRemoveToggleButton.IsChecked = true;
        radialControllerConfig.SetDefaultMenuItems(
            new RadialControllerSystemMenuItemKind[] { });
    }
    ```
4. <span data-ttu-id="27f2e-220">Wählen Sie die Schaltfläche **Element entfernen** halten Sie das Dial gedrückt, um das Menü erneut zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-220">Select the **Remove item** button and then press and hold the Dial to display the menu again.</span></span>

    <span data-ttu-id="27f2e-221">Wie sie sehen, enthält das Menü jetzt die Standard-Tools.</span><span class="sxs-lookup"><span data-stu-id="27f2e-221">Notice that the menu now contains the default collection of tools.</span></span> <span data-ttu-id="27f2e-222">Erinnern Sie sich daran, dass Sie in Schritt 3 beim Einrichten unseres benutzerdefinierten Menüs alle standardmäßigen Tools entfernt und nur unser benutzerdefiniertes Tool hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="27f2e-222">Recall that, in Step 3, while setting up our custom menu, we removed all the default tools and added just our custom tool.</span></span> <span data-ttu-id="27f2e-223">Wir haben außerdem festgestellt, dass die standardmäßigen Elemente für den aktuellen Kontext wiederhergestellt werden, wenn das Menü auf eine leere Auflistung festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="27f2e-223">We also noted that, when the menu is set to an empty collection, the default items for the current context are reinstated.</span></span> <span data-ttu-id="27f2e-224">(Wir haben unser benutzerdefiniertes Tool vor dem Entfernen der Standardtools hinzugefügt.)</span><span class="sxs-lookup"><span data-stu-id="27f2e-224">(We added our custom tool before removing the default tools.)</span></span>

5. <span data-ttu-id="27f2e-225">Wählen Sie die Schaltfläche **Element hinzufügen** und halten Sie dann das Dial gedrückt.</span><span class="sxs-lookup"><span data-stu-id="27f2e-225">Select the **Add item** button and then press and hold the Dial.</span></span>

    <span data-ttu-id="27f2e-226">Wie Sie sehen, beinhaltet das Menü jetzt sowohl die Standard-Tools und unser benutzerdefiniertes Tools.</span><span class="sxs-lookup"><span data-stu-id="27f2e-226">Notice that the menu now contains both the default collection of tools and our custom tool.</span></span>

6. <span data-ttu-id="27f2e-227">Wählen Sie die Schaltfläche **RadialController-Menü zurücksetzen** und halten Sie dann das Dial gedrückt.</span><span class="sxs-lookup"><span data-stu-id="27f2e-227">Select the **Reset RadialController menu** button and then press and hold the Dial.</span></span>

    <span data-ttu-id="27f2e-228">Wie Sie sehen, wurde das Menü auf den ursprünglichen Zustand zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="27f2e-228">Notice that the menu is back to its original state.</span></span>

## <a name="step-6-customize-the-device-haptics"></a><span data-ttu-id="27f2e-229">Schritt6: Anpassen der Gerätehaptik</span><span class="sxs-lookup"><span data-stu-id="27f2e-229">Step 6: Customize the device haptics</span></span>
<span data-ttu-id="27f2e-230">Das Surface Dial und andere Radgeräte können Benutzern haptisches Feedback für die aktuelle Interaktion (basierend auf den Klick oder die Drehung) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-230">The Surface Dial, and other wheel devices, can provide users with haptic feedback corresponding to the current interaction (based on either click or rotation).</span></span>

<span data-ttu-id="27f2e-231">In diesem Schritt wird gezeigt, wie Sie das haptische Feedback anpassen können, indem Sie die Steuerelemente für den Schieberegler und Umschalter zuordnen, sodass das haptische Feedbackverhalten dynamisch festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="27f2e-231">In this step, we show how you can customize haptic feedback by associating our slider and toggle switch controls and using them to dynamically specify haptic feedback behavior.</span></span> <span data-ttu-id="27f2e-232">In diesem Beispiel muss der Umschalter auf an gestellt sein, damit das Feedback aktiviert wird, während der Schiebereglerwert angibt, wie oft das Feedback wiederholt wird.</span><span class="sxs-lookup"><span data-stu-id="27f2e-232">For this example, the toggle switch must be set to on for feedback to be enabled while the slider value specifies how often the click feedback is repeated.</span></span> 

> [!NOTE]
> <span data-ttu-id="27f2e-233">Haptisches Feedback kann vom Benutzer auf der Seite **Einstellungen** >  **Geräte** > **Rad** deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-233">Haptic feedback can be disabled by the user in the **Settings** >  **Devices** > **Wheel** page.</span></span>

1. <span data-ttu-id="27f2e-234">Öffnen Sie die Datei „App.xaml.cs“:</span><span class="sxs-lookup"><span data-stu-id="27f2e-234">Open the App.xaml.cs file.</span></span>
2. <span data-ttu-id="27f2e-235">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („Schritt 6: Anpassen der Gerätehaptik”).</span><span class="sxs-lookup"><span data-stu-id="27f2e-235">Find the code marked with the title of this step ("Step 6: Customize the device haptics").</span></span>
3. <span data-ttu-id="27f2e-236">Kommentieren Sie die erste und dritte Zeile („MainPage_Basic” und „MainPage”), und entfernen Sie die Kommentare aus der zweiten Zeile („MainPage_Haptics”).</span><span class="sxs-lookup"><span data-stu-id="27f2e-236">Comment the first and third lines ("MainPage_Basic" and "MainPage") and uncomment the second ("MainPage_Haptics").</span></span>  

    ``` csharp
    rootFrame.Navigate(typeof(MainPage_Basic), e.Arguments);
    rootFrame.Navigate(typeof(MainPage_Haptics), e.Arguments);
    rootFrame.Navigate(typeof(MainPage), e.Arguments);
    ```
4. <span data-ttu-id="27f2e-237">Öffnen Sie die Datei „MainPage_Haptics.xaml“.</span><span class="sxs-lookup"><span data-stu-id="27f2e-237">Open the MainPage_Haptics.xaml file.</span></span>
5. <span data-ttu-id="27f2e-238">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („\<!-- Schritt 6: Anpassen der Gerätehaptik -->”).</span><span class="sxs-lookup"><span data-stu-id="27f2e-238">Find the code marked with the title of this step ("\<!-- Step 6: Customize the device haptics -->").</span></span>
6. <span data-ttu-id="27f2e-239">Entfernen Sie die Kommentare aus den folgenden Zeilen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-239">Uncomment the following lines.</span></span> <span data-ttu-id="27f2e-240">(Dieser UI-Code gibt lediglich an, welche Haptikfunktionen von dem aktuellen Gerät unterstützt werden.)</span><span class="sxs-lookup"><span data-stu-id="27f2e-240">(This UI code simply indicates what haptics features are supported by the current device.)</span></span>    

    ```xaml
    <StackPanel x:Name="HapticsStack" 
                Orientation="Vertical" 
                HorizontalAlignment="Center" 
                BorderBrush="Gray" 
                BorderThickness="1">
        <TextBlock Padding="10" 
                    Text="Supported haptics properties:" />
        <CheckBox x:Name="CBDefault" 
                    Content="Default" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsChecked="True" />
        <CheckBox x:Name="CBIntensity" 
                    Content="Intensity" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
        <CheckBox x:Name="CBPlayCount" 
                    Content="Play count" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
        <CheckBox x:Name="CBPlayDuration" 
                    Content="Play duration" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
        <CheckBox x:Name="CBReplayPauseInterval" 
                    Content="Replay/pause interval" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
        <CheckBox x:Name="CBBuzzContinuous" 
                    Content="Buzz continuous" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
        <CheckBox x:Name="CBClick" 
                    Content="Click" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
        <CheckBox x:Name="CBPress" 
                    Content="Press" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
        <CheckBox x:Name="CBRelease" 
                    Content="Release" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
        <CheckBox x:Name="CBRumbleContinuous" 
                    Content="Rumble continuous" 
                    Padding="10" 
                    IsEnabled="False" 
                    IsThreeState="True" 
                    IsChecked="{x:Null}" />
    </StackPanel>
    ```
7. <span data-ttu-id="27f2e-241">Öffnen Sie die Datei „MainPage_Haptics.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="27f2e-241">Open the MainPage_Haptics.xaml.cs file</span></span>
8. <span data-ttu-id="27f2e-242">Suchen Sie den Code, mit dem Titel dieses Schritts gekennzeichnet ist („Schritt6: Haptikeinstellungen”).</span><span class="sxs-lookup"><span data-stu-id="27f2e-242">Find the code marked with the title of this step ("Step 6: Haptics customization")</span></span>
9. <span data-ttu-id="27f2e-243">Entfernen Sie die Kommentare aus den folgenden Zeilen:</span><span class="sxs-lookup"><span data-stu-id="27f2e-243">Uncomment the following lines:</span></span>  

    - <span data-ttu-id="27f2e-244">Der [Windows.Devices.Haptics](https://docs.microsoft.com/uwp/api/windows.devices.haptics)-Typverweis wird für die Funktionen in den folgenden Schritten verwendet.</span><span class="sxs-lookup"><span data-stu-id="27f2e-244">The [Windows.Devices.Haptics](https://docs.microsoft.com/uwp/api/windows.devices.haptics) type reference is used for functionality in subsequent steps.</span></span>  
    
        ```csharp
        using Windows.Devices.Haptics;
        ```

    - <span data-ttu-id="27f2e-245">Hier geben wir den Handler für das [ControlAcquired](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.ControlAcquired)-Ereignis an, das ausgelöst wird, wenn das benutzerdefinierte **RadialController**-Menüelement ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="27f2e-245">Here, we specify the handler for the [ControlAcquired](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.ControlAcquired) event that is triggered when our custom **RadialController** menu item is selected.</span></span>

        ```csharp
        radialController.ControlAcquired += (rc_sender, args) =>
        { RadialController_ControlAcquired(rc_sender, args); };
        ``` 

    - <span data-ttu-id="27f2e-246">Als Nächstes definieren wir den [ControlAcquired](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.ControlAcquired)-Handler, in dem wir das standardmäßige Haptik-Feedback deaktivieren und unserer Haptik-UI initialisieren.</span><span class="sxs-lookup"><span data-stu-id="27f2e-246">Next, we define the [ControlAcquired](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.ControlAcquired) handler, where we disable default haptic feedback and initialize our haptics UI.</span></span>

        ```csharp
        private void RadialController_ControlAcquired(
            RadialController rc_sender,
            RadialControllerControlAcquiredEventArgs args)
        {
            // Turn off default haptic feedback.
            radialController.UseAutomaticHapticFeedback = false;

            SimpleHapticsController hapticsController =
                args.SimpleHapticsController;

            // Enumerate haptic support.
            IReadOnlyCollection<SimpleHapticsControllerFeedback> supportedFeedback =
                hapticsController.SupportedFeedback;

            foreach (SimpleHapticsControllerFeedback feedback in supportedFeedback)
            {
                if (feedback.Waveform == KnownSimpleHapticsControllerWaveforms.BuzzContinuous)
                {
                    CBBuzzContinuous.IsEnabled = true;
                    CBBuzzContinuous.IsChecked = true;
                }
                else if (feedback.Waveform == KnownSimpleHapticsControllerWaveforms.Click)
                {
                    CBClick.IsEnabled = true;
                    CBClick.IsChecked = true;
                }
                else if (feedback.Waveform == KnownSimpleHapticsControllerWaveforms.Press)
                {
                    CBPress.IsEnabled = true;
                    CBPress.IsChecked = true;
                }
                else if (feedback.Waveform == KnownSimpleHapticsControllerWaveforms.Release)
                {
                    CBRelease.IsEnabled = true;
                    CBRelease.IsChecked = true;
                }
                else if (feedback.Waveform == KnownSimpleHapticsControllerWaveforms.RumbleContinuous)
                {
                    CBRumbleContinuous.IsEnabled = true;
                    CBRumbleContinuous.IsChecked = true;
                }
            }

            if (hapticsController?.IsIntensitySupported == true)
            {
                CBIntensity.IsEnabled = true;
                CBIntensity.IsChecked = true;
            }
            if (hapticsController?.IsPlayCountSupported == true)
            {
                CBPlayCount.IsEnabled = true;
                CBPlayCount.IsChecked = true;
            }
            if (hapticsController?.IsPlayDurationSupported == true)
            {
                CBPlayDuration.IsEnabled = true;
                CBPlayDuration.IsChecked = true;
            }
            if (hapticsController?.IsReplayPauseIntervalSupported == true)
            {
                CBReplayPauseInterval.IsEnabled = true;
                CBReplayPauseInterval.IsChecked = true;
            }
        }
        ```

    - <span data-ttu-id="27f2e-247">In unseren [RotationChanged](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.RotationChanged) und [ButtonClicked](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.ButtonClicked)-Ereignishandlern verknüpfen wir die entsprechenden Schieberegler und Ein-/Aus-Steuerelemente mit unserer benutzerdefinierten Haptik.</span><span class="sxs-lookup"><span data-stu-id="27f2e-247">In our [RotationChanged](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.RotationChanged) and [ButtonClicked](https://docs.microsoft.com/uwp/api/windows.ui.input.radialcontroller.ButtonClicked) event handlers, we connect the corresponding slider and toggle button controls to our custom haptics.</span></span> 

        ```csharp
        // Connect wheel device rotation to slider control.
        private void RadialController_RotationChanged(
            object sender, RadialControllerRotationChangedEventArgs args)
        {
            ...
            if (ClickToggle.IsOn && 
                (RotationSlider.Value > RotationSlider.Minimum) && 
                (RotationSlider.Value < RotationSlider.Maximum))
            {
                SimpleHapticsControllerFeedback waveform = 
                    FindWaveform(args.SimpleHapticsController, 
                    KnownSimpleHapticsControllerWaveforms.BuzzContinuous);
                if (waveform != null)
                {
                    args.SimpleHapticsController.SendHapticFeedback(waveform);
                }
            }
        }

        private void RadialController_ButtonClicked(
            object sender, RadialControllerButtonClickedEventArgs args)
        {
            ...

            if (RotationSlider?.Value > 0)
            {
                SimpleHapticsControllerFeedback waveform = 
                    FindWaveform(args.SimpleHapticsController, 
                    KnownSimpleHapticsControllerWaveforms.Click);

                if (waveform != null)
                {
                    args.SimpleHapticsController.SendHapticFeedbackForPlayCount(
                        waveform, 1.0, 
                        (int)RotationSlider.Value, 
                        TimeSpan.Parse("1"));
                }
            }
        }
        ```
    - <span data-ttu-id="27f2e-248">Schließlich erhalten wir die angeforderte **[Waveform](https://docs.microsoft.com/uwp/api/windows.devices.haptics.simplehapticscontrollerfeedback.Waveform)** (falls unterstützt) für das Haptik-Feedback.</span><span class="sxs-lookup"><span data-stu-id="27f2e-248">Finally, we get the requested **[Waveform](https://docs.microsoft.com/uwp/api/windows.devices.haptics.simplehapticscontrollerfeedback.Waveform)** (if supported) for the haptic feedback.</span></span> 

        ```csharp
        // Get the requested waveform.
        private SimpleHapticsControllerFeedback FindWaveform(
            SimpleHapticsController hapticsController,
            ushort waveform)
        {
            foreach (var hapticInfo in hapticsController.SupportedFeedback)
            {
                if (hapticInfo.Waveform == waveform)
                {
                    return hapticInfo;
                }
            }
            return null;
        }
        ```

<span data-ttu-id="27f2e-249">Führen Sie nun die App erneut aus, um die benutzerdefinierte Haptik auszuprobieren, indem Sie den Schiebereglerwert und den Zustand des Ein-/Aus-Schalters ändern.</span><span class="sxs-lookup"><span data-stu-id="27f2e-249">Now run the app again to try out the custom haptics by changing the slider value and toggle-switch state.</span></span>

## <a name="step-7-define-on-screen-interactions-for-surface-studio-and-similar-devices"></a><span data-ttu-id="27f2e-250">Schritt7: Onscreen-Interaktionen auf dem Bildschirm für Surface Studio und ähnliche Geräte definieren</span><span class="sxs-lookup"><span data-stu-id="27f2e-250">Step 7: Define on-screen interactions for Surface Studio and similar devices</span></span>
<span data-ttu-id="27f2e-251">Im Zusammenspiel mit Surface Studio bietet das Surface Dial Benutzern ein noch innovativeres Bedienerlebnis.</span><span class="sxs-lookup"><span data-stu-id="27f2e-251">Paired with the Surface Studio, the Surface Dial can provide an even more distinctive user experience.</span></span> 

<span data-ttu-id="27f2e-252">Das Surface Dial unterstützt nicht nur die beschriebene Standardmenüaktion „Drücken und Halten“, sondern kann zusätzlich direkt auf dem Bildschirm des Surface Studio platziert werden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-252">In addition to the default press and hold menu experience described, the Surface Dial can also be placed directly on the screen of the Surface Studio.</span></span> <span data-ttu-id="27f2e-253">Dadurch wird ein spezielles Onscreen-Menü aktiviert.</span><span class="sxs-lookup"><span data-stu-id="27f2e-253">This enables a special "on-screen" menu.</span></span> 

<span data-ttu-id="27f2e-254">Das System erkennt sowohl die Auflageposition als auch die Begrenzungen des Surface Dial, kann anhand dieser Informationen auf die durch das Gerät verursachte Okklusion reagieren und eine größere Menüversion darstellen, die außen um die Drehsteuerung herum angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="27f2e-254">By detecting both the contact location and bounds of the Surface Dial, the system handles occlusion by the device and displays a larger version of the menu that wraps around the outside of the Dial.</span></span> <span data-ttu-id="27f2e-255">Auch die App kann diese Informationen nutzen, um die Benutzeroberfläche an das Vorhandensein des Geräts und dessen beabsichtigte Nutzung anzupassen, z.B. daran, wie der Benutzer seine Hand und seinen Arm platziert.</span><span class="sxs-lookup"><span data-stu-id="27f2e-255">This same info can also be used by your app to adapt the UI for both the presence of the device and its anticipated usage, such as the placement of the user's hand and arm.</span></span> 

<span data-ttu-id="27f2e-256">Das Beispiel, das mit diesem Lernprogramm einhergeht, enthält ein etwas komplexeres Beispiel, das einige dieser Funktionen veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="27f2e-256">The sample that accompanies this tutorial includes a slightly more complex example that demonstrates some of these capabilities.</span></span>

<span data-ttu-id="27f2e-257">Um dies in Aktion zu sehen (dafür ist Surface Studio erforderlich):</span><span class="sxs-lookup"><span data-stu-id="27f2e-257">To see this in action (you'll need a Surface Studio):</span></span>

1. <span data-ttu-id="27f2e-258">Laden Sie das Beispiel auf einem Surface Studio-Gerät (mit Visual Studio installiert) herunter</span><span class="sxs-lookup"><span data-stu-id="27f2e-258">Download the sample on a Surface Studio device (with Visual Studio installed)</span></span>
2. <span data-ttu-id="27f2e-259">Öffnen Sie das Beispiel in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27f2e-259">Open the sample in Visual Studio</span></span>
3. <span data-ttu-id="27f2e-260">Öffnen Sie die Datei „App.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="27f2e-260">Open the App.xaml.cs file</span></span>
4. <span data-ttu-id="27f2e-261">Suchen Sie den Code, der mit dem Titel dieses Schritts gekennzeichnet ist („Schritt7: Onscreen-Interaktionen für Surface Studio und ähnliche Geräte definieren”)</span><span class="sxs-lookup"><span data-stu-id="27f2e-261">Find the code marked with the title of this step ("Step 7: Define on-screen interactions for Surface Studio and similar devices")</span></span>
5. <span data-ttu-id="27f2e-262">Kommentieren Sie die zweite Zeile („MainPage_Basic” und „MainPage_Haptics”), und entfernen Sie die Kommentare aus der dritten Zeile („MainPage”).</span><span class="sxs-lookup"><span data-stu-id="27f2e-262">Comment the first and second lines ("MainPage_Basic" and "MainPage_Haptics") and uncomment the third ("MainPage")</span></span>  

    ``` csharp
    rootFrame.Navigate(typeof(MainPage_Basic), e.Arguments);
    rootFrame.Navigate(typeof(MainPage_Haptics), e.Arguments);
    rootFrame.Navigate(typeof(MainPage), e.Arguments);
    ```
6. <span data-ttu-id="27f2e-263">Führen Sie die App aus und legen Sie das Surface Dial die beiden Steuerungsbereiche, wechseln Sie zwischen ihnen.</span><span class="sxs-lookup"><span data-stu-id="27f2e-263">Run the app and place the Surface Dial in each of the two control regions, alternating between them.</span></span>    
![Onscreen RadialController](images/radialcontroller/wheel-app-step5-onscreen2.png) 

    <span data-ttu-id="27f2e-265">Hier sehen Sie ein Video zu diesem Beispiel in Aktion:</span><span class="sxs-lookup"><span data-stu-id="27f2e-265">Here's a video of this sample in action:</span></span>  

    <iframe src="https://channel9.msdn.com/Blogs/One-Dev-Minute/Programming-the-Microsoft-Surface-Dial/player" width="600" height="400" allowFullScreen frameBorder="0"></iframe>  

## <a name="summary"></a><span data-ttu-id="27f2e-266">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="27f2e-266">Summary</span></span>

<span data-ttu-id="27f2e-267">Herzlichen Glückwunsch, Sie haben das *Lernprogramm für die ersten Schritte: Unterstützung von Surface Dial (und anderen Radgeräten) in Ihrer UWP-App* abgeschlossen!</span><span class="sxs-lookup"><span data-stu-id="27f2e-267">Congratulations, you've completed the *Get Started Tutorial: Support the Surface Dial (and other wheel devices) in your UWP app*!</span></span> <span data-ttu-id="27f2e-268">Wir haben Ihnen den für die Unterstützung von einem Radgerät in Ihren UWP-Apps erforderlichen Code gezeigt. Außerdem haben Sie erfahren, wie Sie Ihren Benutzern umfangreichere Erfahrungen bereitstellen, die von **RadialController**-APIs unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="27f2e-268">We showed you the basic code required for supporting a wheel device in your UWP apps, and how to provide some of the richer user experiences supported by the **RadialController** APIs.</span></span>
