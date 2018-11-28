---
title: Längere Anzeige des Begrüßungsbildschirms
description: Verlängern Sie die Anzeige eines Begrüßungsbildschirms, indem Sie für die App einen erweiterten Begrüßungsbildschirm erstellen. Mit diesem erweiterten Bildschirm wird der beim Starten der App angezeigte Begrüßungsbildschirm imitiert. Er kann aber angepasst werden.
ms.assetid: CD3053EB-7F86-4D74-9C5A-950303791AE3
ms.date: 11/08/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 142ee642806ebba41d6ddb4d49fe55217e7a0e2e
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7837770"
---
# <a name="display-a-splash-screen-for-more-time"></a><span data-ttu-id="43118-105">Längere Anzeige des Begrüßungsbildschirms</span><span class="sxs-lookup"><span data-stu-id="43118-105">Display a splash screen for more time</span></span>

**<span data-ttu-id="43118-106">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="43118-106">Important APIs</span></span>**

-   [**<span data-ttu-id="43118-107">SplashScreen-Klasse</span><span class="sxs-lookup"><span data-stu-id="43118-107">SplashScreen class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224763)
-   [**<span data-ttu-id="43118-108">Window.SizeChanged-Ereignis</span><span class="sxs-lookup"><span data-stu-id="43118-108">Window.SizeChanged event</span></span>**](https://msdn.microsoft.com/library/windows/apps/br209055)
-   [**<span data-ttu-id="43118-109">Application.OnLaunched-Methode</span><span class="sxs-lookup"><span data-stu-id="43118-109">Application.OnLaunched method</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242335)

<span data-ttu-id="43118-110">Verlängern Sie die Anzeige eines Begrüßungsbildschirms, indem Sie für die App einen erweiterten Begrüßungsbildschirm erstellen.</span><span class="sxs-lookup"><span data-stu-id="43118-110">Display a splash screen for more time by creating an extended splash screen for your app.</span></span> <span data-ttu-id="43118-111">Mit diesem erweiterten Bildschirm wird der beim Starten der App angezeigte Begrüßungsbildschirm imitiert. Er kann aber angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="43118-111">This extended screen imitates the splash screen shown when your app is launched, but can be customized.</span></span> <span data-ttu-id="43118-112">Mit einem erweiterten Begrüßungsbildschirm können Sie das Startverhalten unabhängig davon definieren, ob Sie Echtzeitinformationen zum Ladevorgang anzeigen oder der App lediglich zusätzliche Zeit zum Vorbereiten der UI-Anfangselemente geben möchten.</span><span class="sxs-lookup"><span data-stu-id="43118-112">Whether you want to show real-time loading information or simply give your app extra time to prepare its initial UI, an extended splash screen lets you define the launch experience.</span></span>

> [!NOTE]
> <span data-ttu-id="43118-113">Der Begriff "erweiterten Begrüßungsbildschirm" in diesem Thema bezieht sich auf einen Begrüßungsbildschirm, der auf dem Bildschirm für längere Zeit bleibt.</span><span class="sxs-lookup"><span data-stu-id="43118-113">The phrase "extended splash screen" in this topic refers to a splash screen that stays on the screen for an extended period of time.</span></span> <span data-ttu-id="43118-114">Sie bezieht sich nicht auf eine Unterklasse, die von der [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763)-Klasse abgeleitet ist.</span><span class="sxs-lookup"><span data-stu-id="43118-114">It does not mean a subclass that derives from the [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763) class.</span></span>

<span data-ttu-id="43118-115">Stellen Sie sicher, dass der erweiterte Begrüßungsbildschirm den standardmäßigen Begrüßungsbildschirm genau imitiert, indem Sie sich an die folgenden Empfehlungen halten:</span><span class="sxs-lookup"><span data-stu-id="43118-115">Make sure your extended splash screen accurately imitates the default splash screen by following these recommendations:</span></span>

-   <span data-ttu-id="43118-116">Sie sollten für die Seite mit dem erweiterten Begrüßungsbildschirm ein Bild mit 620x300 Pixeln verwenden. Es sollte zudem mit dem Bild übereinstimmen, das im App-Manifest für den Begrüßungsbildschirm angegeben ist (dem Bild des App-Begrüßungsbildschirms).</span><span class="sxs-lookup"><span data-stu-id="43118-116">Your extended splash screen page should use a 620 x 300 pixel image that is consistent with the image specified for your splash screen in your app manifest (your app's splash screen image).</span></span> <span data-ttu-id="43118-117">In Microsoft Visual Studio2015 werden die Einstellungen für den Begrüßungsbildschirm im Abschnitt **Begrüßungsbildschirm** der Registerkarte " **Visuelle Anlagen** " in Ihrem app-Manifest (Datei "Package.appxmanifest") gespeichert.</span><span class="sxs-lookup"><span data-stu-id="43118-117">In Microsoft Visual Studio2015, splash screen settings are stored in the **Splash Screen** section of the **Visual Assets** tab in your app manifest (Package.appxmanifest file).</span></span>
-   <span data-ttu-id="43118-118">Sie sollten für den erweiterten Begrüßungsbildschirm eine Hintergrundfarbe verwenden, die mit der in Ihrem App-Manifest für Ihren Begrüßungsbildschirm angegebenen Hintergrundfarbe konsistent ist (dem Hintergrund des Begrüßungsbildschirms Ihrer App).</span><span class="sxs-lookup"><span data-stu-id="43118-118">Your extended splash screen should use a background color that is consistent with the background color specified for your splash screen in your app manifest (your app's splash screen background).</span></span>
-   <span data-ttu-id="43118-119">Sie müssen im Code die [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763)-Klasse verwenden, um das Bild des App-Begrüßungsbildschirms an den gleichen Koordinaten zu positionieren, an denen der standardmäßige Begrüßungsbildschirms positioniert wird.</span><span class="sxs-lookup"><span data-stu-id="43118-119">Your code should use the [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763) class to position your app's splash screen image at the same screen coordinates as the default splash screen.</span></span>
-   <span data-ttu-id="43118-120">Der Code sollte mithilfe der [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763)-Klasse auf Ereignisse zur Änderung der Fenstergröße (beispielsweise beim Drehen des Bildschirms oder Verschieben der App neben eine andere App auf dem Bildschirm) reagieren, um die Elemente auf dem erweiterten Begrüßungsbildschirm neu anzuordnen.</span><span class="sxs-lookup"><span data-stu-id="43118-120">Your code should respond to window resize events (such as when the screen is rotated or your app is moved next to another app onscreen) by using the [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763) class to reposition items on your extended splash screen.</span></span>

<span data-ttu-id="43118-121">Erstellen Sie mit den folgenden Schritten einen erweiterten Begrüßungsbildschirm, der den standardmäßigen Begrüßungsbildschirm wirkungsvoll imitiert.</span><span class="sxs-lookup"><span data-stu-id="43118-121">Use the following steps to create an extended splash screen that effectively imitates the default splash screen.</span></span>

## <a name="add-a-blank-page-item-to-your-existing-app"></a><span data-ttu-id="43118-122">Hinzufügen des Elements **Leere Seite** zur vorhandenen App</span><span class="sxs-lookup"><span data-stu-id="43118-122">Add a **Blank Page** item to your existing app</span></span>


<span data-ttu-id="43118-123">In diesem Thema wird davon ausgegangen, dass Sie einem vorhandenen App-Projekt für die universelle Windows-Plattform (UWP) mit C#, Visual Basic oder C++ einen erweiterten Begrüßungsbildschirm hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="43118-123">This topic assumes you want to add an extended splash screen to an existing Universal Windows Platform (UWP) app project using C#, Visual Basic, or C++.</span></span>

-   <span data-ttu-id="43118-124">Öffnen Sie Ihre app in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="43118-124">Open your app in Visual Studio.</span></span>
-   <span data-ttu-id="43118-125">Öffnen Sie in der Menüleiste **Projekt**, und klicken Sie auf **Neues Element hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="43118-125">Press or open **Project** from the menu bar and click **Add New Item**.</span></span> <span data-ttu-id="43118-126">Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="43118-126">An **Add New Item** dialog box will appear.</span></span>
-   <span data-ttu-id="43118-127">Fügen Sie der App in diesem Dialogfeld ein neues Element **Leere Seite** hinzu.</span><span class="sxs-lookup"><span data-stu-id="43118-127">From this dialog box, add a new **Blank Page** to your app.</span></span> <span data-ttu-id="43118-128">In diesem Thema erhält die Seite mit dem erweiterten Begrüßungsbildschirm den Namen „ExtendedSplash“.</span><span class="sxs-lookup"><span data-stu-id="43118-128">This topic names the extended splash screen page "ExtendedSplash".</span></span>

<span data-ttu-id="43118-129">Beim Hinzufügen des Elements **Leere Seite** werden zwei Dateien erstellt: eine für Markup (ExtendedSplash.xaml) und eine für Code (ExtendedSplash.xaml.cs).</span><span class="sxs-lookup"><span data-stu-id="43118-129">Adding a **Blank Page** item generates two files, one for markup (ExtendedSplash.xaml) and another for code (ExtendedSplash.xaml.cs).</span></span>

## <a name="essential-xaml-for-an-extended-splash-screen"></a><span data-ttu-id="43118-130">Grundlegender XAML-Code für einen erweiterten Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="43118-130">Essential XAML for an extended splash screen</span></span>


<span data-ttu-id="43118-131">Führen Sie diese Schritte aus, um dem erweiterten Begrüßungsbildschirm ein Bild und ein Statussteuerelement hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="43118-131">Follow these steps to add an image and progress control to your extended splash screen.</span></span>

<span data-ttu-id="43118-132">In der Datei „ExtendedSplash.xaml“:</span><span class="sxs-lookup"><span data-stu-id="43118-132">In your ExtendedSplash.xaml file:</span></span>

-   <span data-ttu-id="43118-133">Ändern Sie die [**Background**](https://msdn.microsoft.com/library/windows/apps/br209396)-Eigenschaft des [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704)-Standardelements, um sie an die Hintergrundfarbe anzupassen, die Sie im App-Manifest für den Begrüßungsbildschirm der App festgelegt haben (im Abschnitt **Visuelle Anlagen** der Datei „Package.appxmanifest“).</span><span class="sxs-lookup"><span data-stu-id="43118-133">Change the [**Background**](https://msdn.microsoft.com/library/windows/apps/br209396) property of the default [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704) element to match the background color you set for your app's splash screen in your app manifest (in the **Visual Assets** section of your Package.appxmanifest file).</span></span> <span data-ttu-id="43118-134">Die Standardfarbe des Begrüßungsbildschirms ist Hellgrau (Hexadezimalwert \#464646).</span><span class="sxs-lookup"><span data-stu-id="43118-134">The default splash screen color is a light gray (hex value \#464646).</span></span> <span data-ttu-id="43118-135">Beachten Sie, dass dieses **Grid**-Element standardmäßig bereitgestellt wird, wenn Sie eine neues Element **Leere Seite** erstellen.</span><span class="sxs-lookup"><span data-stu-id="43118-135">Note that this **Grid** element is provided by default when you create a new **Blank Page**.</span></span> <span data-ttu-id="43118-136">Sie müssen nicht zwingend ein **Grid**-Element verwenden. Es handelt sich dabei lediglich um eine gut geeignete Basis zum Erstellen eines erweiterten Begrüßungsbildschirms.</span><span class="sxs-lookup"><span data-stu-id="43118-136">You don't have to use a **Grid**; it's just a convenient base for building an extended splash screen.</span></span>
-   <span data-ttu-id="43118-137">Fügen Sie dem [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704)-Element ein [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267)-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="43118-137">Add a [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267) element to the [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704).</span></span> <span data-ttu-id="43118-138">Sie verwenden dieses **Canvas**-Element zum Positionieren des Bilds für den erweiterten Begrüßungsbildschirm.</span><span class="sxs-lookup"><span data-stu-id="43118-138">You'll use this **Canvas** to position your extended splash screen image.</span></span>
-   <span data-ttu-id="43118-139">Fügen Sie dem [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267)-Element ein [**Image**](https://msdn.microsoft.com/library/windows/apps/br242752)-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="43118-139">Add an [**Image**](https://msdn.microsoft.com/library/windows/apps/br242752) element to the [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267).</span></span> <span data-ttu-id="43118-140">Verwenden Sie für den erweiterten Begrüßungsbildschirm das gleiche Bild mit einer Größe von 600 x 320 Pixeln, das Sie für den standardmäßigen Begrüßungsbildschirm gewählt haben.</span><span class="sxs-lookup"><span data-stu-id="43118-140">Use the same 600 x 320 pixel image for your extended splash screen that you chose for the default splash screen.</span></span>
-   <span data-ttu-id="43118-141">(Optional) Fügen Sie ein Statussteuerelement hinzu, um Benutzern anzuzeigen, dass die App geladen wird.</span><span class="sxs-lookup"><span data-stu-id="43118-141">(Optional) Add a progress control to show users that your app is loading.</span></span> <span data-ttu-id="43118-142">In diesem Thema wird anstelle eines bestimmten oder unbestimmten [**ProgressBar**](https://msdn.microsoft.com/library/windows/apps/br227529)-Elements ein [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/br227538)-Element hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="43118-142">This topic adds a [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/br227538), instead of a determinate or indeterminate [**ProgressBar**](https://msdn.microsoft.com/library/windows/apps/br227529).</span></span>

<span data-ttu-id="43118-143">Das folgende Beispiel zeigt ein [**Raster**](https://msdn.microsoft.com/library/windows/apps/br242704) mit diesen neuen und geänderten.</span><span class="sxs-lookup"><span data-stu-id="43118-143">The following example demonstrates a [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704) with these additions and changes.</span></span>

```xaml
    <Grid Background="#464646">
        <Canvas>
            <Image x:Name="extendedSplashImage" Source="Assets/SplashScreen.png"/>
            <ProgressRing Name="splashProgressRing" IsActive="True" Width="20" HorizontalAlignment="Center"></ProgressRing>
        </Canvas>
    </Grid>
```

> [!NOTE]
> <span data-ttu-id="43118-144">In diesem Beispiel wird die Breite des dem [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/br227538) und 20 Pixel.</span><span class="sxs-lookup"><span data-stu-id="43118-144">This example sets the width of the [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/br227538) to 20 pixels.</span></span> <span data-ttu-id="43118-145">Sie können die Breite manuell auf einen Wert festlegen, der für Ihre App geeignet ist. Das Steuerelement wird jedoch nicht für Breiten unterhalb von 20Pixel gerendert.</span><span class="sxs-lookup"><span data-stu-id="43118-145">You can manually set its width to a value that works for your app, however, the control will not render at widths of less than 20 pixels.</span></span>

## <a name="essential-code-for-an-extended-splash-screen-class"></a><span data-ttu-id="43118-146">Grundlegender Code für die Klasse eines erweiterten Begrüßungsbildschirms</span><span class="sxs-lookup"><span data-stu-id="43118-146">Essential code for an extended splash screen class</span></span>


<span data-ttu-id="43118-147">Der erweiterte Begrüßungsbildschirm muss entsprechend reagieren, wenn sich die Fenstergröße (nur Windows) oder die Ausrichtung ändert.</span><span class="sxs-lookup"><span data-stu-id="43118-147">Your extended splash screen needs to respond whenever the window size (Windows only) or orientation changes.</span></span> <span data-ttu-id="43118-148">Die Position des verwendeten Bilds muss aktualisiert werden, damit der erweiterte Begrüßungsbildschirm unabhängig von der Änderung des Fensters gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="43118-148">The position of the image you use must be updated so that your extended splash screen looks good no matter how the window changes.</span></span>

<span data-ttu-id="43118-149">Führen Sie die folgenden Schritte aus, um Methoden zu definieren, damit der erweiterte Begrüßungsbildschirm richtig dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="43118-149">Use these steps to define methods to correctly display your extended splash screen.</span></span>

1.  **<span data-ttu-id="43118-150">Hinzufügen von erforderlichen Namespaces</span><span class="sxs-lookup"><span data-stu-id="43118-150">Add required namespaces</span></span>**

    <span data-ttu-id="43118-151">Sie müssen „ExtendedSplash.xaml.cs“ die folgenden Namespaces hinzufügen, um auf die [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763)-Klasse und [**Window.SizeChanged**](https://msdn.microsoft.com/library/windows/apps/br209055)-Ereignisse zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="43118-151">You'll need to add the following namespaces to ExtendedSplash.xaml.cs to access the [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763) class, [**Window.SizeChanged**](https://msdn.microsoft.com/library/windows/apps/br209055) events.</span></span>

    ```cs
    using Windows.ApplicationModel.Activation;
    using Windows.UI.Core;
    ```

2.  **<span data-ttu-id="43118-152">Erstellen Sie eine partielle Klasse, und deklarieren Sie Klassenvariablen.</span><span class="sxs-lookup"><span data-stu-id="43118-152">Create a partial class and declare class variables</span></span>**

    <span data-ttu-id="43118-153">Fügen Sie den folgenden Code in die Datei „ExtendedSplash.xaml.cs“ ein, um eine partielle Klasse zum Darstellen eines erweiterten Begrüßungsbildschirms zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="43118-153">Include the following code in ExtendedSplash.xaml.cs to create a partial class to represent an extended splash screen.</span></span>

    ```cs
    partial class ExtendedSplash : Page
    {
        internal Rect splashImageRect; // Rect to store splash screen image coordinates.
        private SplashScreen splash; // Variable to hold the splash screen object.
        internal bool dismissed = false; // Variable to track splash screen dismissal status.
        internal Frame rootFrame;

       // Define methods and constructor
    }
    ```

    <span data-ttu-id="43118-154">Diese Klassenvariablen werden von verschiedenen Methoden verwendet.</span><span class="sxs-lookup"><span data-stu-id="43118-154">These class variables are used by several methods.</span></span> <span data-ttu-id="43118-155">Die `splashImageRect`-Variable speichert die Koordinaten der Position, an der das System das Begrüßungsbildschirmbild für die App angezeigt hat.</span><span class="sxs-lookup"><span data-stu-id="43118-155">The `splashImageRect` variable stores the coordinates where the system displayed the splash screen image for the app.</span></span> <span data-ttu-id="43118-156">Die `splash`-Variable speichert ein [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763)-Objekt, und die `dismissed`-Variable verfolgt, ob der vom System angezeigte Begrüßungsbildschirm geschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="43118-156">The `splash` variable stores a [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763) object, and the `dismissed` variable tracks whether or not the splash screen that is displayed by the system has been dismissed.</span></span>

3.  **<span data-ttu-id="43118-157">Definieren eines Konstruktors für die Klasse, der das Bild richtig positioniert</span><span class="sxs-lookup"><span data-stu-id="43118-157">Define a constructor for your class that correctly positions the image</span></span>**

    <span data-ttu-id="43118-158">Mit dem folgenden Code wird ein Konstruktor für die Klasse des erweiterten Begrüßungsbildschirms definiert, der eine Überprüfung auf Ereignisse zum Ändern der Fenstergröße durchführt, das Bild und (optional) das Statussteuerelement auf dem erweiterten Begrüßungsbildschirm positioniert, einen Rahmen für die Navigation erstellt und eine asynchrone Methode zum Wiederherstellen eines gespeicherten Sitzungszustands aufruft.</span><span class="sxs-lookup"><span data-stu-id="43118-158">The following code defines a constructor for the extended splash screen class that listens for window resizing events, positions the image and (optional) progress control on the extended splash screen, creates a frame for navigation, and calls an asynchronous method to restore a saved session state.</span></span>

    ```cs
    public ExtendedSplash(SplashScreen splashscreen, bool loadState)
    {
        InitializeComponent();

        // Listen for window resize events to reposition the extended splash screen image accordingly.
        // This ensures that the extended splash screen formats properly in response to window resizing.
        Window.Current.SizeChanged += new WindowSizeChangedEventHandler(ExtendedSplash_OnResize);

        splash = splashscreen;
        if (splash != null)
        {
            // Register an event handler to be executed when the splash screen has been dismissed.
            splash.Dismissed += new TypedEventHandler<SplashScreen, Object>(DismissedEventHandler);

            // Retrieve the window coordinates of the splash screen image.
            splashImageRect = splash.ImageLocation;
            PositionImage();

            // If applicable, include a method for positioning a progress control.
            PositionRing();
        }

        // Create a Frame to act as the navigation context
        rootFrame = new Frame();            
    }
    ```

    <span data-ttu-id="43118-159">Registrieren Sie den [**Window.SizeChanged**](https://msdn.microsoft.com/library/windows/apps/br209055)-Handler (in diesem Beispiel `ExtendedSplash_OnResize`) im Klassenkonstruktor, damit das Bild von der App auf dem erweiterten Begrüßungsbildschirm richtig positioniert wird.</span><span class="sxs-lookup"><span data-stu-id="43118-159">Make sure to register your [**Window.SizeChanged**](https://msdn.microsoft.com/library/windows/apps/br209055) handler (`ExtendedSplash_OnResize` in the example) in your class constructor so that your app positions the image correctly in your extended splash screen.</span></span>

4.  **<span data-ttu-id="43118-160">Definieren Sie eine Klassenmethode, um das Bild auf dem erweiterten Begrüßungsbildschirm zu positionieren</span><span class="sxs-lookup"><span data-stu-id="43118-160">Define a class method to position the image in your extended splash screen</span></span>**

    <span data-ttu-id="43118-161">Mit diesem Code wird veranschaulicht, wie das Bild mithilfe der `splashImageRect`-Klassenvariablen auf dem erweiterten Begrüßungsbildschirm positioniert wird.</span><span class="sxs-lookup"><span data-stu-id="43118-161">This code demonstrates how to position the image on the extended splash screen page with the `splashImageRect` class variable.</span></span>

    ```cs
    void PositionImage()
    {
        extendedSplashImage.SetValue(Canvas.LeftProperty, splashImageRect.X);
        extendedSplashImage.SetValue(Canvas.TopProperty, splashImageRect.Y);
        extendedSplashImage.Height = splashImageRect.Height;
        extendedSplashImage.Width = splashImageRect.Width;
    }
    ```

5.  **<span data-ttu-id="43118-162">(Optional) Definieren einer Klassenmethode, um ein Statussteuerelement auf dem erweiterten Begrüßungsbildschirm zu positionieren</span><span class="sxs-lookup"><span data-stu-id="43118-162">(Optional) Define a class method to position a progress control in your extended splash screen</span></span>**

    <span data-ttu-id="43118-163">Wenn Sie sich für das Hinzufügen eines [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/br227538)-Elements zum erweiterten Begrüßungsbildschirm entscheiden, sollten Sie es relativ zum Bild des Begrüßungsbildschirms positionieren.</span><span class="sxs-lookup"><span data-stu-id="43118-163">If you chose to add a [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/br227538) to your extended splash screen, position it relative to the splash screen image.</span></span> <span data-ttu-id="43118-164">Fügen Sie der Datei „ExtendedSplash.xaml.cs“ den folgenden Code hinzu, um das **ProgressRing**-Element 32Pixel unter dem Bild zu zentrieren.</span><span class="sxs-lookup"><span data-stu-id="43118-164">Add the following code to ExtendedSplash.xaml.cs to center the **ProgressRing** 32 pixels below the image.</span></span>

    ```cs
    void PositionRing()
    {
        splashProgressRing.SetValue(Canvas.LeftProperty, splashImageRect.X + (splashImageRect.Width*0.5) - (splashProgressRing.Width*0.5));
        splashProgressRing.SetValue(Canvas.TopProperty, (splashImageRect.Y + splashImageRect.Height + splashImageRect.Height*0.1));
    }
    ```

6.  **<span data-ttu-id="43118-165">Definieren Sie innerhalb der Klasse einen Handler für das Dismissed-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="43118-165">Inside the class, define a handler for the Dismissed event</span></span>**

    <span data-ttu-id="43118-166">Legen Sie in der Datei „ExtendedSplash.xaml.cs“ die `dismissed`-Klassenvariable als Reaktion auf das [**SplashScreen.Dismissed**](https://msdn.microsoft.com/library/windows/apps/br224764)-Ereignis auf „true“ fest.</span><span class="sxs-lookup"><span data-stu-id="43118-166">In ExtendedSplash.xaml.cs, respond when the [**SplashScreen.Dismissed**](https://msdn.microsoft.com/library/windows/apps/br224764) event occurs by setting the `dismissed` class variable to true.</span></span> <span data-ttu-id="43118-167">Falls Ihre App über Setupvorgänge verfügt, fügen Sie sie diesem Ereignishandler hinzu.</span><span class="sxs-lookup"><span data-stu-id="43118-167">If your app has setup operations, add them to this event handler.</span></span>

    ```cs
    // Include code to be executed when the system has transitioned from the splash screen to the extended splash screen (application's first view).
    void DismissedEventHandler(SplashScreen sender, object e)
    {
        dismissed = true;

        // Complete app setup operations here...
    }
    ```

    <span data-ttu-id="43118-168">Führen Sie nach Abschluss des App-Setups eine Navigation weg vom erweiterten Begrüßungsbildschirm durch.</span><span class="sxs-lookup"><span data-stu-id="43118-168">After app setup is complete, navigate away from your extended splash screen.</span></span> <span data-ttu-id="43118-169">Mit dem folgenden Code wird eine Methode mit dem Namen `DismissExtendedSplash` definiert. Diese dient der Navigation zur `MainPage`, die in der Datei „MainPage.xaml“ der App definiert ist.</span><span class="sxs-lookup"><span data-stu-id="43118-169">The following code defines a method called `DismissExtendedSplash` that navigates to the `MainPage` defined in your app's MainPage.xaml file.</span></span>

    ```cs
    async void DismissExtendedSplash()
      {
         await Windows.ApplicationModel.Core.CoreApplication.MainView.CoreWindow.Dispatcher.RunAsync(CoreDispatcherPriority.Normal,() =>            {
              rootFrame = new Frame();
              rootFrame.Content = new MainPage(); Window.Current.Content = rootFrame;
            });
      }
      ```

7.  **<span data-ttu-id="43118-170">Definieren Sie innerhalb der Klasse einen Handler für Windows.SizeChanged-Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="43118-170">Inside the class, define a handler for Window.SizeChanged events</span></span>**

    <span data-ttu-id="43118-171">Bereiten Sie den erweiterten Begrüßungsbildschirm so vor, dass die Elemente neu angeordnet werden, wenn Benutzer die Größe des Fensters ändern.</span><span class="sxs-lookup"><span data-stu-id="43118-171">Prepare your extended splash screen to reposition its elements if a user resizes the window.</span></span> <span data-ttu-id="43118-172">Mit diesem Code wird beim Auftreten eines [**Window.SizeChanged**](https://msdn.microsoft.com/library/windows/apps/br209055)-Ereignisses reagiert, indem die neuen Koordinaten erfasst werden und das Bild neu positioniert wird.</span><span class="sxs-lookup"><span data-stu-id="43118-172">This code responds when a [**Window.SizeChanged**](https://msdn.microsoft.com/library/windows/apps/br209055) event occurs by capturing the new coordinates and repositioning the image.</span></span> <span data-ttu-id="43118-173">Wenn Sie dem erweiterten Begrüßungsbildschirm ein Statussteuerelement hinzugefügt haben, sollten Sie es in diesem Ereignishandler ebenfalls neu positionieren.</span><span class="sxs-lookup"><span data-stu-id="43118-173">If you added a progress control to your extended splash screen, reposition it inside this event handler as well.</span></span>

    ```cs
    void ExtendedSplash_OnResize(Object sender, WindowSizeChangedEventArgs e)
    {
        // Safely update the extended splash screen image coordinates. This function will be executed when a user resizes the window.
        if (splash != null)
        {
            // Update the coordinates of the splash screen image.
            splashImageRect = splash.ImageLocation;
            PositionImage();

            // If applicable, include a method for positioning a progress control.
            // PositionRing();
        }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="43118-174">Bevor Sie versuchen, erhalten die Bildposition stellen Sie sicher die Klassenvariable (`splash`) ein gültiges [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763) -Objekt enthält, wie im Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="43118-174">Before you try to get the image location make sure the class variable (`splash`) contains a valid [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763) object, as shown in the example.</span></span>

     

8.  **<span data-ttu-id="43118-175">(Optional) Hinzufügen einer Klassenmethode zum Wiederherstellen eines gespeicherten Sitzungszustands</span><span class="sxs-lookup"><span data-stu-id="43118-175">(Optional) Add a class method to restore a saved session state</span></span>**

    <span data-ttu-id="43118-176">Der Code, den Sie der [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)-Methode unter „Schritt4: [Ändern Sie den Startaktivierungshandler](#modify-the-launch-activation-handler)“ hinzugefügt haben, führt dazu, dass die App beim Starten einen erweiterten Begrüßungsbildschirm anzeigt.</span><span class="sxs-lookup"><span data-stu-id="43118-176">The code you added to the [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) method in Step 4: [Modify the launch activation handler](#modify-the-launch-activation-handler) causes your app to display an extended splash screen when it launches.</span></span> <span data-ttu-id="43118-177">Um alle Methoden, die im Zusammenhang mit app-Starts in Klasse für den erweiterten Begrüßungsbildschirm zusammenzufassen, Sie sollten erwägen, eine Methode zur Datei "extendedsplash.Xaml.cs" den Status der app wiederhergestellt.</span><span class="sxs-lookup"><span data-stu-id="43118-177">To consolidate all methods related to app launch in your extended splash screen class, you could consider adding a method to your ExtendedSplash.xaml.cs file to restore the app's state.</span></span>

    ```cs
    void RestoreState(bool loadState)
    {
        if (loadState)
        {
             // code to load your app's state here
        }
    }
    ```

    <span data-ttu-id="43118-178">Beim Ändern des Startaktivierungshandlers in „App.xaml.cs“ sollten Sie zusätzlich `loadstate` auf „true“ festlegen, wenn das vorherige [**ApplicationExecutionState**](https://msdn.microsoft.com/library/windows/apps/br224694)-Element der App **Terminated** lautete.</span><span class="sxs-lookup"><span data-stu-id="43118-178">When you modify the launch activation handler in App.xaml.cs, you'll also set `loadstate` to true if the previous [**ApplicationExecutionState**](https://msdn.microsoft.com/library/windows/apps/br224694) of your app was **Terminated**.</span></span> <span data-ttu-id="43118-179">Ist dies der Fall, stellt die `RestoreState`-Methode den vorherigen Zustand der App wieder her.</span><span class="sxs-lookup"><span data-stu-id="43118-179">If so, the `RestoreState` method restores the app to its previous state.</span></span> <span data-ttu-id="43118-180">Eine Übersicht über das Starten, Anhalten und Beenden einer App finden Sie unter [App-Lebenszyklus](app-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="43118-180">For an overview of app launch, suspension, and termination, see [App lifecycle](app-lifecycle.md).</span></span>

## <a name="modify-the-launch-activation-handler"></a><span data-ttu-id="43118-181">Ändern Sie den Startaktivierungshandler</span><span class="sxs-lookup"><span data-stu-id="43118-181">Modify the launch activation handler</span></span>


<span data-ttu-id="43118-182">Beim Starten Ihrer App übergibt das System Begrüßungsbildschirminformationen an den Handler für das Startaktivierungsereignis.</span><span class="sxs-lookup"><span data-stu-id="43118-182">When your app is launched, the system passes splash screen information to the app's launch activation event handler.</span></span> <span data-ttu-id="43118-183">Sie können diese Informationen verwenden, um das Bild auf der Seite mit dem erweiterten Begrüßungsbildschirm richtig zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="43118-183">You can use this information to correctly position the image on your extended splash screen page.</span></span> <span data-ttu-id="43118-184">Sie können diese Begrüßungsbildschirminformationen aus den Argumenten des Aktivierungsereignisses abrufen, die an den [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)-Handler der App übergeben werden (siehe `args`-Variable im folgenden Code).</span><span class="sxs-lookup"><span data-stu-id="43118-184">You can get this splash screen information from the activation event arguments that are passed to your app's [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) handler (see the `args` variable in the following code).</span></span>

<span data-ttu-id="43118-185">Wenn Sie den [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)-Handler für Ihre App noch nicht außer Kraft gesetzt haben, finden Sie unter [App-Lebenszyklus](app-lifecycle.md) Informationen zum Behandeln von Aktivierungsereignissen.</span><span class="sxs-lookup"><span data-stu-id="43118-185">If you have not already overridden the [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) handler for your app, see [App lifecycle](app-lifecycle.md) to learn how to handle activation events.</span></span>

<span data-ttu-id="43118-186">Fügen Sie in der Datei „App.xaml.cs“ den folgenden Code zum Erstellen und Anzeigen eines erweiterten Begrüßungsbildschirms hinzu.</span><span class="sxs-lookup"><span data-stu-id="43118-186">In App.xaml.cs, add the following code to create and display an extended splash screen.</span></span>

```cs
protected override void OnLaunched(LaunchActivatedEventArgs args)
{
    if (args.PreviousExecutionState != ApplicationExecutionState.Running)
    {
        bool loadState = (args.PreviousExecutionState == ApplicationExecutionState.Terminated);
        ExtendedSplash extendedSplash = new ExtendedSplash(args.SplashScreen, loadState);
        Window.Current.Content = extendedSplash;
    }

    Window.Current.Activate();
}
```

## <a name="complete-code"></a><span data-ttu-id="43118-187">Vollständiger Code</span><span class="sxs-lookup"><span data-stu-id="43118-187">Complete code</span></span>

<span data-ttu-id="43118-188">Der folgende Code unterscheidet sich leicht von den Codeausschnitten der vorherigen Schritte.</span><span class="sxs-lookup"><span data-stu-id="43118-188">The following code slightly differs from the snippets shown in the previous steps.</span></span>
-   <span data-ttu-id="43118-189">„ExtendedSplash.xaml“ enthält eine `DismissSplash`-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="43118-189">ExtendedSplash.xaml includes a `DismissSplash` button.</span></span> <span data-ttu-id="43118-190">Beim Klicken auf diese Schaltfläche wird mit dem `DismissSplashButton_Click`-Ereignishandler die `DismissExtendedSplash`-Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="43118-190">When this button is clicked, an event handler, `DismissSplashButton_Click`, calls the `DismissExtendedSplash` method.</span></span> <span data-ttu-id="43118-191">Rufen Sie in der App `DismissExtendedSplash` auf, wenn das Laden von Ressourcen oder Initialisieren der UI in der App abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="43118-191">In your app, call `DismissExtendedSplash` when your app is done loading resources or initializing its UI.</span></span>
-   <span data-ttu-id="43118-192">Für diese App wird auch eine Projektvorlage für eine UWP-App verwendet, bei der die [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682)-Navigation zum Einsatz kommt.</span><span class="sxs-lookup"><span data-stu-id="43118-192">This app also uses a UWP app project template, which uses [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) navigation.</span></span> <span data-ttu-id="43118-193">Der Startaktivierungshandler ([**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)) definiert in „App.xaml.cs“ dann ein `rootFrame`-Element und verwendet es zum Festlegen des Inhalts für das App-Fenster.</span><span class="sxs-lookup"><span data-stu-id="43118-193">As a result, in App.xaml.cs, the launch activation handler ([**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)) defines a `rootFrame` and uses it to set the content of the app window.</span></span>

### <a name="extendedsplashxaml"></a><span data-ttu-id="43118-194">"Extendedsplash.xaml"</span><span class="sxs-lookup"><span data-stu-id="43118-194">ExtendedSplash.xaml</span></span>

<span data-ttu-id="43118-195">Dieses Beispiel enthält ein `DismissSplash` Schaltfläche, da keine app-Ressourcen geladen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="43118-195">This example includes a `DismissSplash` button because it doesn't have app resources to load.</span></span> <span data-ttu-id="43118-196">Blenden Sie den erweiterten Begrüßungsbildschirm in der App automatisch aus, wenn das Laden von Ressourcen oder Vorbereiten der UI-Anfangselemente in der App abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="43118-196">In your app, dismiss the extended splash screen automatically when your app is done loading resources or preparing its initial UI.</span></span>

```xml
<Page
    x:Class="SplashScreenExample.ExtendedSplash"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:SplashScreenExample"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="#464646">
        <Canvas>
            <Image x:Name="extendedSplashImage" Source="Assets/SplashScreen.png"/>
            <ProgressRing Name="splashProgressRing" IsActive="True" Width="20" HorizontalAlignment="Center"/>
        </Canvas>
        <StackPanel HorizontalAlignment="Center" VerticalAlignment="Bottom">
            <Button x:Name="DismissSplash" Content="Dismiss extended splash screen" HorizontalAlignment="Center" Click="DismissSplashButton_Click" />
        </StackPanel>
    </Grid>
</Page>
```

### <a name="extendedsplashxamlcs"></a><span data-ttu-id="43118-197">Datei "extendedsplash.Xaml.cs"</span><span class="sxs-lookup"><span data-stu-id="43118-197">ExtendedSplash.xaml.cs</span></span>

<span data-ttu-id="43118-198">Beachten Sie, dass die `DismissExtendedSplash` -Methode wird aufgerufen, aus dem Click-Ereignishandler für die `DismissSplash` Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="43118-198">Note that the `DismissExtendedSplash` method is called from the click event handler for the `DismissSplash` button.</span></span> <span data-ttu-id="43118-199">In der App benötigen Sie keine `DismissSplash`-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="43118-199">In your app, you won't need a `DismissSplash` button.</span></span> <span data-ttu-id="43118-200">Rufen Sie stattdessen `DismissExtendedSplash` auf, wenn das Laden der Ressourcen in der App abgeschlossen ist und Sie die Navigation zur Hauptseite durchführen möchten.</span><span class="sxs-lookup"><span data-stu-id="43118-200">Instead, call `DismissExtendedSplash` when your app is done loading resources and you want to navigate to its main page.</span></span>

```cs
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Runtime.InteropServices.WindowsRuntime;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;

using Windows.ApplicationModel.Activation;
using SplashScreenExample.Common;
using Windows.UI.Core;

// The Blank Page item template is documented at http://go.microsoft.com/fwlink/p/?LinkID=234238

namespace SplashScreenExample
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    partial class ExtendedSplash : Page
    {
        internal Rect splashImageRect; // Rect to store splash screen image coordinates.
        private SplashScreen splash; // Variable to hold the splash screen object.
        internal bool dismissed = false; // Variable to track splash screen dismissal status.
        internal Frame rootFrame;

        public ExtendedSplash(SplashScreen splashscreen, bool loadState)
        {
            InitializeComponent();

            // Listen for window resize events to reposition the extended splash screen image accordingly.
            // This is important to ensure that the extended splash screen is formatted properly in response to snapping, unsnapping, rotation, etc...
            Window.Current.SizeChanged += new WindowSizeChangedEventHandler(ExtendedSplash_OnResize);

            splash = splashscreen;

            if (splash != null)
            {
                // Register an event handler to be executed when the splash screen has been dismissed.
                splash.Dismissed += new TypedEventHandler<SplashScreen, Object>(DismissedEventHandler);

                // Retrieve the window coordinates of the splash screen image.
                splashImageRect = splash.ImageLocation;
                PositionImage();

                // Optional: Add a progress ring to your splash screen to show users that content is loading
                PositionRing();
            }

            // Create a Frame to act as the navigation context
            rootFrame = new Frame();

            // Restore the saved session state if necessary
            RestoreState(loadState);
        }

        void RestoreState(bool loadState)
        {
            if (loadState)
            {
                // TODO: write code to load state
            }
        }

        // Position the extended splash screen image in the same location as the system splash screen image.
        void PositionImage()
        {
            extendedSplashImage.SetValue(Canvas.LeftProperty, splashImageRect.X);
            extendedSplashImage.SetValue(Canvas.TopProperty, splashImageRect.Y);
            extendedSplashImage.Height = splashImageRect.Height;
            extendedSplashImage.Width = splashImageRect.Width;

        }

        void PositionRing()
        {
            splashProgressRing.SetValue(Canvas.LeftProperty, splashImageRect.X + (splashImageRect.Width*0.5) - (splashProgressRing.Width*0.5));
            splashProgressRing.SetValue(Canvas.TopProperty, (splashImageRect.Y + splashImageRect.Height + splashImageRect.Height*0.1));
        }

        void ExtendedSplash_OnResize(Object sender, WindowSizeChangedEventArgs e)
        {
            // Safely update the extended splash screen image coordinates. This function will be fired in response to snapping, unsnapping, rotation, etc...
            if (splash != null)
            {
                // Update the coordinates of the splash screen image.
                splashImageRect = splash.ImageLocation;
                PositionImage();
                PositionRing();
            }
        }

        // Include code to be executed when the system has transitioned from the splash screen to the extended splash screen (application's first view).
        void DismissedEventHandler(SplashScreen sender, object e)
        {
            dismissed = true;

            // Complete app setup operations here...
        }

        void DismissExtendedSplash()
        {
            // Navigate to mainpage
            rootFrame.Navigate(typeof(MainPage));
            // Place the frame in the current Window
            Window.Current.Content = rootFrame;
        }

        void DismissSplashButton_Click(object sender, RoutedEventArgs e)
        {
            DismissExtendedSplash();
        }
    }
}
```

### <a name="appxamlcs"></a><span data-ttu-id="43118-201">"App.Xaml.cs"</span><span class="sxs-lookup"><span data-stu-id="43118-201">App.xaml.cs</span></span>

<span data-ttu-id="43118-202">Dieses Projekt wurde mit der UWP-app **Leere App (XAML)** -Projektvorlage in Visual Studio erstellt.</span><span class="sxs-lookup"><span data-stu-id="43118-202">This project was created using the UWP app **Blank App (XAML)** project template in Visual Studio.</span></span> <span data-ttu-id="43118-203">Die Ereignishandler `OnNavigationFailed` und `OnSuspending` werden automatisch erstellt und müssen nicht geändert werden, um einen erweiterten Begrüßungsbildschirm zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="43118-203">Both the `OnNavigationFailed` and `OnSuspending` event handlers are automatically generated and don't need to be changed to implement an extended splash screen.</span></span> <span data-ttu-id="43118-204">In diesem Thema wird nur `OnLaunched` geändert.</span><span class="sxs-lookup"><span data-stu-id="43118-204">This topic only modifies `OnLaunched`.</span></span>

<span data-ttu-id="43118-205">Falls Sie für Ihre App keine Projektvorlage verwendet haben, finden Sie unter „Schritt4: [Ändern Sie den Startaktivierungshandler](#modify-the-launch-activation-handler) ein Beispiel für die Änderung von `OnLaunched` ohne [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682)-Navigation.</span><span class="sxs-lookup"><span data-stu-id="43118-205">If you didn't use a project template for your app, see Step 4: [Modify the launch activation handler](#modify-the-launch-activation-handler) for an example of a modified `OnLaunched` that doesn't use [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) navigation.</span></span>

```cs
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Runtime.InteropServices.WindowsRuntime;
using Windows.ApplicationModel;
using Windows.ApplicationModel.Activation;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;

// The Blank Application template is documented at http://go.microsoft.com/fwlink/p/?LinkID=234227

namespace SplashScreenExample
{
    /// <summary>
    /// Provides application-specific behavior to supplement the default Application class.
    /// </summary>
    sealed partial class App : Application
    {
        /// <summary>
        /// Initializes the singleton application object.  This is the first line of authored code
        /// executed, and as such is the logical equivalent of main() or WinMain().
        /// </summary>
        public App()
        {
            Microsoft.ApplicationInsights.WindowsAppInitializer.InitializeAsync(
            Microsoft.ApplicationInsights.WindowsCollectors.Metadata |
            Microsoft.ApplicationInsights.WindowsCollectors.Session);
            this.InitializeComponent();
            this.Suspending += OnSuspending;
        }

        /// <summary>
        /// Invoked when the application is launched normally by the end user.  Other entry points
        /// will be used such as when the application is launched to open a specific file.
        /// </summary>
        /// <param name="e">Details about the launch request and process.</param>
        protected override void OnLaunched(LaunchActivatedEventArgs e)
        {
#if DEBUG
            if (System.Diagnostics.Debugger.IsAttached)
            {
                this.DebugSettings.EnableFrameRateCounter = true;
            }
#endif

            Frame rootFrame = Window.Current.Content as Frame;

            // Do not repeat app initialization when the Window already has content,
            // just ensure that the window is active
            if (rootFrame == null)
            {
                // Create a Frame to act as the navigation context and navigate to the first page
                rootFrame = new Frame();
                // Set the default language
                rootFrame.Language = Windows.Globalization.ApplicationLanguages.Languages[0];

                rootFrame.NavigationFailed += OnNavigationFailed;

                //  Display an extended splash screen if app was not previously running.
                if (e.PreviousExecutionState != ApplicationExecutionState.Running)
                {
                    bool loadState = (e.PreviousExecutionState == ApplicationExecutionState.Terminated);
                    ExtendedSplash extendedSplash = new ExtendedSplash(e.SplashScreen, loadState);
                    rootFrame.Content = extendedSplash;
                    Window.Current.Content = rootFrame;
                }
            }

            if (rootFrame.Content == null)
            {
                // When the navigation stack isn't restored navigate to the first page,
                // configuring the new page by passing required information as a navigation
                // parameter
                rootFrame.Navigate(typeof(MainPage), e.Arguments);
            }
            // Ensure the current window is active
            Window.Current.Activate();
        }

        /// <summary>
        /// Invoked when Navigation to a certain page fails
        /// </summary>
        /// <param name="sender">The Frame which failed navigation</param>
        /// <param name="e">Details about the navigation failure</param>
        void OnNavigationFailed(object sender, NavigationFailedEventArgs e)
        {
            throw new Exception("Failed to load Page " + e.SourcePageType.FullName);
        }

        /// <summary>
        /// Invoked when application execution is being suspended.  Application state is saved
        /// without knowing whether the application will be terminated or resumed with the contents
        /// of memory still intact.
        /// </summary>
        /// <param name="sender">The source of the suspend request.</param>
        /// <param name="e">Details about the suspend request.</param>
        private void OnSuspending(object sender, SuspendingEventArgs e)
        {
            var deferral = e.SuspendingOperation.GetDeferral();
            // TODO: Save applicaiton state and stop any background activity
            deferral.Complete();
        }
    }
}
```

## <a name="related-topics"></a><span data-ttu-id="43118-206">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="43118-206">Related topics</span></span>


* [<span data-ttu-id="43118-207">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="43118-207">App lifecycle</span></span>](app-lifecycle.md)

**<span data-ttu-id="43118-208">Referenz</span><span class="sxs-lookup"><span data-stu-id="43118-208">Reference</span></span>**

* [**<span data-ttu-id="43118-209">Windows.ApplicationModel.Activation-Namespace</span><span class="sxs-lookup"><span data-stu-id="43118-209">Windows.ApplicationModel.Activation namespace</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224766)
* [**<span data-ttu-id="43118-210">Windows.ApplicationModel.Activation.SplashScreen-Klasse</span><span class="sxs-lookup"><span data-stu-id="43118-210">Windows.ApplicationModel.Activation.SplashScreen class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224763)
* [**<span data-ttu-id="43118-211">Windows.ApplicationModel.Activation.SplashScreen.ImageLocation-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="43118-211">Windows.ApplicationModel.Activation.SplashScreen.ImageLocation property</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224765)
* [**<span data-ttu-id="43118-212">Windows.ApplicationModel.Core.CoreApplicationView.Activated-Ereignis</span><span class="sxs-lookup"><span data-stu-id="43118-212">Windows.ApplicationModel.Core.CoreApplicationView.Activated event</span></span>**](https://msdn.microsoft.com/library/windows/apps/br225018)

 

 
