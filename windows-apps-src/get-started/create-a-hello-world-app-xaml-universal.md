---
author: GrantMeStrength
ms.assetid: 03A74239-D4B6-4E41-B2FA-6C04F225B844
title: Hier erfahren Sie, wie Sie eine „Hallo Welt“-App (XAML) erstellen
description: Verwenden Sie Extensible Application Markup Language (XAML) mit c#, um eine einfache Hello, World-app für die universelle Windows-Plattform (UWP) auf Windows 10 erstellen.
ms.author: jken
ms.date: 03/06/2017
ms.topic: article
keywords: Windows10, UWP, erste App, Hallo Welt
ms.localizationpriority: medium
ms.openlocfilehash: 28b30a592951017fb4a0b3803261cb0258be6ae3
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6844549"
---
# <a name="create-a-hello-world-app-xaml"></a><span data-ttu-id="f0398-104">Erstellen der App „Hello, world“ (XAML)</span><span class="sxs-lookup"><span data-stu-id="f0398-104">Create a "Hello, world" app (XAML)</span></span>

<span data-ttu-id="f0398-105">In diesem Lernprogramm erfahren Sie, wie Sie XAML und c# zum Erstellen einer einfachen "Hello, World" app für die universelle Windows-Plattform (UWP) auf Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f0398-105">This tutorial teaches you how to use XAML and C# to create a simple "Hello, world" app for the Universal Windows Platform (UWP) on Windows10.</span></span> <span data-ttu-id="f0398-106">Mit einem einzigen Projekt in Microsoft Visual Studio können Sie eine app erstellen, die auf jedem Windows 10-Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f0398-106">With a single project in Microsoft Visual Studio, you can build an app that runs on any Windows10 device.</span></span>

<span data-ttu-id="f0398-107">Hier erfahren Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f0398-107">Here you'll learn how to:</span></span>

-   <span data-ttu-id="f0398-108">Erstellen Sie ein neues **Visual Studio 2017** -Projekt, das auf **Windows 10** und die **UWP**abzielt.</span><span class="sxs-lookup"><span data-stu-id="f0398-108">Create a new **Visual Studio 2017** project that targets **Windows10** and the **UWP**.</span></span>
-   <span data-ttu-id="f0398-109">Schreiben Sie XAML zum Ändern der UI auf der Startseite.</span><span class="sxs-lookup"><span data-stu-id="f0398-109">Write XAML to change the UI on your start page.</span></span>
-   <span data-ttu-id="f0398-110">Führen Sie das Projekt auf dem lokalen Desktop in Visual Studio aus.</span><span class="sxs-lookup"><span data-stu-id="f0398-110">Run the project on the local desktop in Visual Studio.</span></span>
-   <span data-ttu-id="f0398-111">Verwenden Sie einen SpeechSynthesizer, um die App sprechen zu lassen, wenn Sie auf eine Schaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="f0398-111">Use a SpeechSynthesizer to make the app talk when you press a button.</span></span>


## <a name="before-you-start"></a><span data-ttu-id="f0398-112">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="f0398-112">Before you start...</span></span>

-   [<span data-ttu-id="f0398-113">Was ist eine universelle Windows-App?</span><span class="sxs-lookup"><span data-stu-id="f0398-113">What's a Universal Windows app?</span></span>](universal-application-platform-guide.md)
-   <span data-ttu-id="f0398-114">[Visual Studio 2017 (und Windows 10) herunterladen](https://developer.microsoft.com/windows/downloads).</span><span class="sxs-lookup"><span data-stu-id="f0398-114">[Download Visual Studio 2017 (and Windows 10)](https://developer.microsoft.com/windows/downloads).</span></span> <span data-ttu-id="f0398-115">Hier erfahren Sie weitere Informationen über die [Vorbereitung](get-set-up.md).</span><span class="sxs-lookup"><span data-stu-id="f0398-115">If you need a hand, learn how to [get set up](get-set-up.md).</span></span>
-   <span data-ttu-id="f0398-116">Außerdem wird davon ausgegangen, dass Sie das Standardfensterlayout in Visual Studio verwenden.</span><span class="sxs-lookup"><span data-stu-id="f0398-116">We also assume you're using the default window layout in Visual Studio.</span></span> <span data-ttu-id="f0398-117">Wenn Sie das Standardlayout ändern, können Sie es im Menü **Fenster** mit dem Befehl **Fensterlayout zurücksetzen** wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="f0398-117">If you change the default layout, you can reset it in the **Window** menu by using the **Reset Window Layout** command.</span></span>

> [!NOTE]
> <span data-ttu-id="f0398-118">In diesem Lernprogramm wird Visual Studio Community 2017 verwendet.</span><span class="sxs-lookup"><span data-stu-id="f0398-118">This tutorial is using Visual Studio Community 2017.</span></span> <span data-ttu-id="f0398-119">Wenn Sie eine andere Version von Visual Studio verwenden, kann das Programm für Sie etwas anders aussehen.</span><span class="sxs-lookup"><span data-stu-id="f0398-119">If you are using a different version of Visual Studio, it may look a little different for you.</span></span>

## <a name="video-summary"></a><span data-ttu-id="f0398-120">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="f0398-120">Video summary</span></span>

<iframe src="https://channel9.msdn.com/Blogs/One-Dev-Minute/Writing-Your-First-Windows-10-App/player" width="640" height="360" allowFullScreen frameBorder="0"></iframe>



## <a name="step-1-create-a-new-project-in-visual-studio"></a><span data-ttu-id="f0398-121">Schritt 1: Erstellen eines neuen Projekts in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f0398-121">Step 1: Create a new project in Visual Studio.</span></span>

1.  <span data-ttu-id="f0398-122">Starten Sie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f0398-122">Launch Visual Studio 2017.</span></span>

2.  <span data-ttu-id="f0398-123">Wählen Sie aus dem Menü " **Datei** " **Neu > Projekt** um das Dialogfeld " *Neues Projekt* " zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f0398-123">From the **File** menu, select **New > Project** to open the *New Project* dialog.</span></span>

3.  <span data-ttu-id="f0398-124">Wählen Sie aus der Liste der Vorlagen auf der linken Seite, **installiert > Visual C#-> Windows Universal** um eine Liste der UWP-Projektvorlagen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f0398-124">From the list of templates on the left, choose **Installed > Visual C# > Windows Universal** to see the list of UWP project templates.</span></span>

    <span data-ttu-id="f0398-125">(Wenn keine universellen Vorlagen angezeigt werden, fehlen möglicherweise die Komponenten zum Erstellen von UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="f0398-125">(If you don't see any Universal templates, you might be missing the components for creating UWP apps.</span></span> <span data-ttu-id="f0398-126">Sie können die Installation wiederholen und UWP-Unterstützung hinzufügen, indem Sie im Dialogfeld *Neues Projekt* auf **Visual Studio-Installer öffnen** klicken.</span><span class="sxs-lookup"><span data-stu-id="f0398-126">You can repeat the installation process and add UWP support by clicking **Open Visual Studio installer** on the *New Project* dialog.</span></span> <span data-ttu-id="f0398-127">Siehe [Vorbereiten](get-set-up.md).)</span><span class="sxs-lookup"><span data-stu-id="f0398-127">See [Get set up](get-set-up.md).)</span></span>

    ![So wiederholen Sie den Installationsvorgang](images/win10-cs-install.png)

4.  <span data-ttu-id="f0398-129">Wählen Sie die Vorlage **Leere App (universelle Windows-App)** aus, und geben Sie „HelloWorld“ als **Name** ein.</span><span class="sxs-lookup"><span data-stu-id="f0398-129">Choose the **Blank App (Universal Windows)** template, and enter "HelloWorld" as the **Name**.</span></span> <span data-ttu-id="f0398-130">Wählen Sie **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="f0398-130">Select **OK**.</span></span>

    ![Das Fenster für ein neues Projekt](images/win10-cs-01.png)

> [!NOTE]
> <span data-ttu-id="f0398-132">Wenn Sie Visual Studio zum ersten Mal verwenden, wird möglicherweise das Dialogfeld „Einstellungen“ angezeigt, in dem Sie aufgefordert werden, **Entwicklermodus** zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f0398-132">If this is the first time you have used Visual Studio, you might see a Settings dialog asking you to enable **Developer mode**.</span></span> <span data-ttu-id="f0398-133">Der Entwicklermodus ist eine spezielle Einstellung, die bestimmte Features ermöglicht, z.B. die Berechtigung zum Ausführen von Apps, direkt und nicht nur aus dem Store.</span><span class="sxs-lookup"><span data-stu-id="f0398-133">Developer mode is a special setting that enables certain features, such as permission to run apps directly, rather than only from the Store.</span></span> <span data-ttu-id="f0398-134">Weitere Informationen finden Sie in [Aktivieren Ihres Geräts für die Entwicklung](enable-your-device-for-development.md).</span><span class="sxs-lookup"><span data-stu-id="f0398-134">For more information, please read [Enable your device for development](enable-your-device-for-development.md).</span></span> <span data-ttu-id="f0398-135">Wählen Sie **Entwicklermodus** aus, klicken Sie auf **Ja**, und schließen Sie das Dialogfeld, um mit dem Lernprogramm fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="f0398-135">To continue with this guide, select **Developer mode**, click **Yes**, and close the dialog.</span></span>

 ![Aktivieren des Dialogfelds für Entwicklermodus](images/win10-cs-00.png)

5.  <span data-ttu-id="f0398-137">Das Dialogfeld für die Zielversion/mindestens erforderliche Version wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f0398-137">The target version/minimum version dialog appears.</span></span> <span data-ttu-id="f0398-138">Die Standardeinstellungen sind für dieses Lernprogramm in Ordnung, wählen Sie daher **OK** aus, um das Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f0398-138">The default settings are fine for this tutorial, so select **OK** to create the project.</span></span>

    ![Das Fenster „Projektmappen-Explorer“](images/win10-cs-02.png)

6.  <span data-ttu-id="f0398-140">Wenn das neue Projekt geöffnet wird, werden die Dateien im Bereich **Projektmappen-Explorer** auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f0398-140">When your new project opens, its files are displayed in the **Solution Explorer** pane on the right.</span></span> <span data-ttu-id="f0398-141">Möglicherweise müssen Sie die Registerkarte **Projektmappen-Explorer** anstelle der Registerkarte **Eigenschaften** auswählen, um die Dateien anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f0398-141">You may need to choose the **Solution Explorer** tab instead of the **Properties** tab to see your files.</span></span>

    ![Das Fenster „Projektmappen-Explorer“](images/win10-cs-03.png)

<span data-ttu-id="f0398-143">**Leere App (universelle Windows-App)** ist zwar nur eine Minimalvorlage, umfasst aber trotzdem eine Reihe von Dateien.</span><span class="sxs-lookup"><span data-stu-id="f0398-143">Although the **Blank App (Universal Window)** is a minimal template, it still contains a lot of files.</span></span> <span data-ttu-id="f0398-144">Diese Dateien werden für alle UWP-Apps mit C# benötigt.</span><span class="sxs-lookup"><span data-stu-id="f0398-144">These files are essential to all UWP apps using C#.</span></span> <span data-ttu-id="f0398-145">Sie sind Teil jedes Projekts, das Sie mit Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="f0398-145">Every project that you create in Visual Studio contains them.</span></span>


### <a name="whats-in-the-files"></a><span data-ttu-id="f0398-146">Inhalt der Dateien</span><span class="sxs-lookup"><span data-stu-id="f0398-146">What's in the files?</span></span>

<span data-ttu-id="f0398-147">Doppelklicken Sie zum Anzeigen und Bearbeiten einer Datei im Projekt im **Projektmappen-Explorer** auf die gewünschte Datei.</span><span class="sxs-lookup"><span data-stu-id="f0398-147">To view and edit a file in your project, double-click the file in the **Solution Explorer**.</span></span> <span data-ttu-id="f0398-148">Erweitern Sie eine XAML-Datei genau wie einen Ordner, um die zugeordnete Codedatei anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f0398-148">Expand a XAML file just like a folder to see its associated code file.</span></span> <span data-ttu-id="f0398-149">XAML-Dateien werden in einer geteilten Ansicht geöffnet, die sowohl die Entwurfsoberfläche als auch den XAML-Editor enthält.</span><span class="sxs-lookup"><span data-stu-id="f0398-149">XAML files open in a split view that shows both the design surface and the XAML editor.</span></span>
> [!NOTE]
> <span data-ttu-id="f0398-150">Was ist XAML?</span><span class="sxs-lookup"><span data-stu-id="f0398-150">What is XAML?</span></span> <span data-ttu-id="f0398-151">Extensible Application Markup Language (XAML) ist die Sprache, die zum Definieren der Benutzeroberfläche Ihrer App verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f0398-151">Extensible Application Markup Language (XAML) is the language used to define your app's user interface.</span></span> <span data-ttu-id="f0398-152">Sie kann manuell eingegeben oder mit den Visual Studio-Entwicklungstools erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="f0398-152">It can be entered manually, or created using the Visual Studio design tools.</span></span> <span data-ttu-id="f0398-153">Eine XAML-Datei verfügt über eine CodeBehind-Datei („.xaml.cs“), die die Logik enthält.</span><span class="sxs-lookup"><span data-stu-id="f0398-153">A .xaml file has a .xaml.cs code-behind file which contains the logic.</span></span> <span data-ttu-id="f0398-154">Zusammen bilden XAML und CodeBehind eine vollständige Klasse.</span><span class="sxs-lookup"><span data-stu-id="f0398-154">Together, the XAML and code-behind make a complete class.</span></span> <span data-ttu-id="f0398-155">Weitere Informationen finden Sie in der [XAML-Übersicht](https://msdn.microsoft.com/library/windows/apps/Mt185595).</span><span class="sxs-lookup"><span data-stu-id="f0398-155">For more information, see [XAML overview](https://msdn.microsoft.com/library/windows/apps/Mt185595).</span></span>

*<span data-ttu-id="f0398-156">„App.xaml“ und „App.xaml.cs“</span><span class="sxs-lookup"><span data-stu-id="f0398-156">App.xaml and App.xaml.cs</span></span>*

-   <span data-ttu-id="f0398-157">In „App.xaml“ deklarieren Sie Ressourcen, die in der gesamten App zur Anwendung kommen.</span><span class="sxs-lookup"><span data-stu-id="f0398-157">App.xaml is where you declare resources that are used across the app.</span></span>
-   <span data-ttu-id="f0398-158">„App.xaml.cs“ ist die CodeBehind-Datei für „App.xaml“.</span><span class="sxs-lookup"><span data-stu-id="f0398-158">App.xaml.cs is the code-behind file for App.xaml.</span></span> <span data-ttu-id="f0398-159">Sie enthält wie alle CodeBehind-Seiten einen Konstruktor, der die `InitializeComponent`-Methode aufruft.</span><span class="sxs-lookup"><span data-stu-id="f0398-159">Like all code-behind pages, it contains a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="f0398-160">Die `InitializeComponent`-Methode wird nicht von Ihnen geschrieben.</span><span class="sxs-lookup"><span data-stu-id="f0398-160">You don't write the `InitializeComponent` method.</span></span> <span data-ttu-id="f0398-161">Sie wird von Visual Studio generiert und dient in erster Linie dazu, die in der XAML-Datei deklarierten Elemente zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="f0398-161">It's generated by Visual Studio, and its main purpose is to initialize the elements declared in the XAML file.</span></span>
-   <span data-ttu-id="f0398-162">„App.xaml.cs“ ist der Einstiegspunkt für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="f0398-162">App.xaml.cs is the entry point for your app.</span></span>
-   <span data-ttu-id="f0398-163">"App.Xaml.cs" enthält außerdem Methoden zum Behandeln der [Aktivierung](../launch-resume/activate-an-app.md) und [Unterbrechung](../launch-resume/suspend-an-app.md) der app.</span><span class="sxs-lookup"><span data-stu-id="f0398-163">App.xaml.cs also contains methods to handle [activation](../launch-resume/activate-an-app.md) and [suspension](../launch-resume/suspend-an-app.md) of the app.</span></span>

*<span data-ttu-id="f0398-164">MainPage.xaml</span><span class="sxs-lookup"><span data-stu-id="f0398-164">MainPage.xaml</span></span>*

-   <span data-ttu-id="f0398-165">In „MainPage.xaml“ definieren Sie die Benutzeroberfläche für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="f0398-165">MainPage.xaml is where you define the UI for your app.</span></span> <span data-ttu-id="f0398-166">Sie können Elemente direkt per XAML-Markup hinzufügen oder die Designtools von Visual Studio verwenden.</span><span class="sxs-lookup"><span data-stu-id="f0398-166">You can add elements directly using XAML markup, or you can use the design tools provided by Visual Studio.</span></span>
-   <span data-ttu-id="f0398-167">„MainPage.xaml.cs“ ist die CodeBehind-Seite für „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="f0398-167">MainPage.xaml.cs is the code-behind page for MainPage.xaml.</span></span> <span data-ttu-id="f0398-168">Hier fügen Sie Ihre App-Logik und Ereignishandler hinzu.</span><span class="sxs-lookup"><span data-stu-id="f0398-168">It's where you add your app logic and event handlers.</span></span>
-   <span data-ttu-id="f0398-169">Zusammen definieren diese beiden Dateien im `HelloWorld`-Namespace eine neue Klasse mit dem Namen `MainPage`, die von [**Page**](https://msdn.microsoft.com/library/windows/apps/BR227503) erbt.</span><span class="sxs-lookup"><span data-stu-id="f0398-169">Together these two files define a new class called `MainPage`, which inherits from [**Page**](https://msdn.microsoft.com/library/windows/apps/BR227503), in the `HelloWorld` namespace.</span></span>

*<span data-ttu-id="f0398-170">Package.appxmanifest</span><span class="sxs-lookup"><span data-stu-id="f0398-170">Package.appxmanifest</span></span>*
-   <span data-ttu-id="f0398-171">Eine Manifestdatei, die Ihre App beschreibt (Name, Beschreibung, Kachel, Startseite usw.)</span><span class="sxs-lookup"><span data-stu-id="f0398-171">A manifest file that describes your app: its name, description, tile, start page, etc.</span></span>
-   <span data-ttu-id="f0398-172">Enthält eine Liste von Abhängigkeiten, Ressourcen und Dateien, die Ihre app enthält.</span><span class="sxs-lookup"><span data-stu-id="f0398-172">Includes a list of dependencies, resources and files that your app contains.</span></span>

*<span data-ttu-id="f0398-173">Ein Satz mit Logobildern</span><span class="sxs-lookup"><span data-stu-id="f0398-173">A set of logo images</span></span>*
-   <span data-ttu-id="f0398-174">Assets/Square150x150Logo.scale-200.png und Wide310x150Logo.scale-200.png stellen Sie Ihre app (entweder "Mittel" oder "Wide-Größe) im Startmenü dar.</span><span class="sxs-lookup"><span data-stu-id="f0398-174">Assets/Square150x150Logo.scale-200.png and Wide310x150Logo.scale-200.png represent your app (either Medium or Wide size) in the start menu.</span></span>
-   <span data-ttu-id="f0398-175">Assets/Square44x44Logo.png stellt Ihre app in der app-Liste der Startmenü, Taskleiste und Task-Manager dar.</span><span class="sxs-lookup"><span data-stu-id="f0398-175">Assets/Square44x44Logo.png represents your app in the app list of the start menu, task bar and task manager.</span></span>
-   <span data-ttu-id="f0398-176">„Assets/StoreLogo.png“ stellt Ihre App im Microsoft Store dar.</span><span class="sxs-lookup"><span data-stu-id="f0398-176">Assets/StoreLogo.png represents your app in the Microsoft Store.</span></span>
-   <span data-ttu-id="f0398-177">„Assets/SplashScreen.scale-200.png“ ist der Begrüßungsbildschirm, der beim Start der App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f0398-177">Assets/SplashScreen.scale-200.png is the splash screen that appears when your app starts.</span></span>
-   <span data-ttu-id="f0398-178">Assets/LockScreenLogo.scale-200.png kann verwendet werden, um die app auf dem Sperrbildschirm darzustellen, wenn das System gesperrt ist.</span><span class="sxs-lookup"><span data-stu-id="f0398-178">Assets/LockScreenLogo.scale-200.png can be used to represent the app on the lock screen, when the system is locked.</span></span>

## <a name="step-2-adding-a-button"></a><span data-ttu-id="f0398-179">Schritt 2: Hinzufügen von Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="f0398-179">Step 2: Adding a button</span></span>

### <a name="using-the-designer-view"></a><span data-ttu-id="f0398-180">Mithilfe der Entwurfsansicht</span><span class="sxs-lookup"><span data-stu-id="f0398-180">Using the designer view</span></span>

<span data-ttu-id="f0398-181">Fügen wir nun der Seite eine Schaltfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="f0398-181">Let's add a button to our page.</span></span> <span data-ttu-id="f0398-182">In diesem Lernprogramm verwenden Sie lediglich einige der zuvor aufgeführten Dateien: „App.xaml“, „MainPage.xaml“ und „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="f0398-182">In this tutorial, you work with just a few of the files listed previously: App.xaml, MainPage.xaml, and MainPage.xaml.cs.</span></span>

1.  <span data-ttu-id="f0398-183">Doppelklicken Sie auf die Datei **MainPage.xaml**, um sie in der Entwurfsansicht zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f0398-183">Double-click on **MainPage.xaml** to open it in the Design view.</span></span>

    <span data-ttu-id="f0398-184">Sie werden feststellen, dass eine grafische Ansicht im oberen Teil des Bildschirms und die XAML-Codeansicht darunter vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="f0398-184">You'll notice there is a graphical view on the top part of the screen, and the XAML code view underneath.</span></span> <span data-ttu-id="f0398-185">Sie können jeweils Änderungen vornehmen, wir verwenden jetzt jedoch die grafische Ansicht.</span><span class="sxs-lookup"><span data-stu-id="f0398-185">You can make changes to either, but for now we'll use the graphical view.</span></span>

    ![Das Fenster „Projektmappen-Explorer“](images/win10-cs-04.png)

2.  <span data-ttu-id="f0398-187">Klicken Sie auf die vertikale Registerkarte **Toolbox** auf der linken Seite, um die Liste der UI-Steuerelemente zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f0398-187">Click on the vertical **Toolbox** tab on the left to open the list of UI controls.</span></span> <span data-ttu-id="f0398-188">(Sie können auf das Reißzweckensymbol in der Titelleiste klicken, damit sie sichtbar bleibt.)</span><span class="sxs-lookup"><span data-stu-id="f0398-188">(You can click the pin icon in its title bar to keep it visible.)</span></span>

    ![Das Fenster „Projektmappen-Explorer“](images/win10-cs-05.png)

3.  <span data-ttu-id="f0398-190">Erweitern Sie **Häufig verwendete XAML-Steuerelemente**, und ziehen Sie die **Schaltfläche** in die Mitte der Design-Canvas.</span><span class="sxs-lookup"><span data-stu-id="f0398-190">Expand **Common XAML Controls**, and drag the **Button** out to the middle of the design canvas.</span></span>

    ![Das Fenster „Projektmappen-Explorer“](images/win10-cs-06.png)

    <span data-ttu-id="f0398-192">Wenn Sie das Fenster mit dem XAML-Code betrachten, sehen Sie, dass die Schaltfläche auch dort hinzugefügt wurde:</span><span class="sxs-lookup"><span data-stu-id="f0398-192">If you look at the XAML code window, you'll see that the Button has been added there too:</span></span>

 ```XAML
<Button x:name="button" Content="Button" HorizontalAlignment="Left" Margin = "152,293,0,0" VerticalAlignment="Top"/>
 ```

4.  <span data-ttu-id="f0398-193">Ändern Sie den Text der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f0398-193">Change the button's text.</span></span>

    <span data-ttu-id="f0398-194">Klicken Sie in der XAML-Codeansicht, und ändern Sie den Inhalt von „Schaltfläche“ in „Hello, World!“.</span><span class="sxs-lookup"><span data-stu-id="f0398-194">Click in the XAML code view, and change the Content from "Button" to "Hello, world!".</span></span>

```XAML
<Button x:name="button" Content="Hello, world!" HorizontalAlignment="Left" Margin = "152,293,0,0" VerticalAlignment="Top"/>
```

<span data-ttu-id="f0398-195">Beachten Sie, wie die in der Design-Canvas angezeigte Schaltfläche aktualisiert wird, um den neuen Text anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f0398-195">Notice how the button displayed in the design canvas updates to display the new text.</span></span>

![Das Fenster „Projektmappen-Explorer“](images/win10-cs-07.png)

## <a name="step-3-start-the-app"></a><span data-ttu-id="f0398-197">Schritt3: Starten der App</span><span class="sxs-lookup"><span data-stu-id="f0398-197">Step 3: Start the app</span></span>


<span data-ttu-id="f0398-198">Sie haben nun eine sehr einfache App erstellt.</span><span class="sxs-lookup"><span data-stu-id="f0398-198">At this point, you've created a very simple app.</span></span> <span data-ttu-id="f0398-199">Dies ist ein guter Zeitpunkt zum Erstellen, Bereitstellen und Starten Ihrer App, um sie in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="f0398-199">This is a good time to build, deploy, and launch your app and see what it looks like.</span></span> <span data-ttu-id="f0398-200">Sie können Ihre App auf dem lokalen Computer, in einem Simulator oder Emulator oder auf einem Remotegerät debuggen.</span><span class="sxs-lookup"><span data-stu-id="f0398-200">You can debug your app on the local machine, in a simulator or emulator, or on a remote device.</span></span> <span data-ttu-id="f0398-201">Dies ist das Zielgerätmenü in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f0398-201">Here's the target device menu in Visual Studio.</span></span>

![Dropdownliste mit Zielgeräten zum Debuggen Ihrer App](images/uap-debug.png)

### <a name="start-the-app-on-a-desktop-device"></a><span data-ttu-id="f0398-203">Starten der App auf einem Desktop-Gerät</span><span class="sxs-lookup"><span data-stu-id="f0398-203">Start the app on a Desktop device</span></span>

<span data-ttu-id="f0398-204">Standardmäßig wird die App auf dem lokalen Computer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f0398-204">By default, the app runs on the local machine.</span></span> <span data-ttu-id="f0398-205">Das Menü mit den Zielgeräten enthält mehrere Optionen zum Debuggen Ihrer App auf Geräten der Desktopfamilie.</span><span class="sxs-lookup"><span data-stu-id="f0398-205">The target device menu provides several options for debugging your app on devices from the desktop device family.</span></span>

-   **<span data-ttu-id="f0398-206">Simulator</span><span class="sxs-lookup"><span data-stu-id="f0398-206">Simulator</span></span>**
-   **<span data-ttu-id="f0398-207">Lokaler Computer</span><span class="sxs-lookup"><span data-stu-id="f0398-207">Local Machine</span></span>**
-   **<span data-ttu-id="f0398-208">Remotecomputer</span><span class="sxs-lookup"><span data-stu-id="f0398-208">Remote Machine</span></span>**

**<span data-ttu-id="f0398-209">So beginnen Sie mit dem Debuggen auf dem lokalen Computer</span><span class="sxs-lookup"><span data-stu-id="f0398-209">To start debugging on the local machine</span></span>**

1.  <span data-ttu-id="f0398-210">Stellen Sie sicher, dass auf der **Standardsymbolleiste** im Menü mit den Zielgeräten (![Menü „Debuggen starten“](images/startdebug-full.png)) die Option **Lokaler Computer** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="f0398-210">In the target device menu (![Start debugging menu](images/startdebug-full.png)) on the **Standard** toolbar, make sure that **Local Machine** is selected.</span></span> <span data-ttu-id="f0398-211">(Dies ist die Standardeinstellung.)</span><span class="sxs-lookup"><span data-stu-id="f0398-211">(It's the default selection.)</span></span>
2.  <span data-ttu-id="f0398-212">Klicken Sie auf der Symbolleiste auf die Schaltfläche **Debuggen starten** (![Schaltfläche „Debuggen starten“](images/startdebug-sm.png)).</span><span class="sxs-lookup"><span data-stu-id="f0398-212">Click the **Start Debugging** button (![Start debugging button](images/startdebug-sm.png)) on the toolbar.</span></span>

   <span data-ttu-id="f0398-213">oder</span><span class="sxs-lookup"><span data-stu-id="f0398-213">–or–</span></span>

   <span data-ttu-id="f0398-214">Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.</span><span class="sxs-lookup"><span data-stu-id="f0398-214">From the **Debug** menu, click **Start Debugging**.</span></span>

   <span data-ttu-id="f0398-215">oder</span><span class="sxs-lookup"><span data-stu-id="f0398-215">–or–</span></span>

   <span data-ttu-id="f0398-216">Drücken Sie F5.</span><span class="sxs-lookup"><span data-stu-id="f0398-216">Press F5.</span></span>

<span data-ttu-id="f0398-217">Die App wird in einem Fenster geöffnet, und zuerst wird ein standardmäßiger Begrüßungsbildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f0398-217">The app opens in a window, and a default splash screen appears first.</span></span> <span data-ttu-id="f0398-218">Der Begrüßungsbildschirm setzt sich aus einem Bild (SplashScreen.png) und einer Hintergrundfarbe (in der Manifestdatei der App angegeben) zusammen.</span><span class="sxs-lookup"><span data-stu-id="f0398-218">The splash screen is defined by an image (SplashScreen.png) and a background color (specified in your app's manifest file).</span></span>

<span data-ttu-id="f0398-219">Nach dem Ausblenden des Begrüßungsbildschirms wird Ihre App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f0398-219">The splash screen disappears, and then your app appears.</span></span> <span data-ttu-id="f0398-220">Sie sieht ungefähr wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="f0398-220">It looks like this.</span></span>

![Erster App-Bildschirm](images/win10-cs-08.png)

<span data-ttu-id="f0398-222">Drücken Sie die WINDOWS-TASTE, um das Menü **Start** zu öffnen, und zeigen Sie alle Apps an.</span><span class="sxs-lookup"><span data-stu-id="f0398-222">Press the Windows key to open the **Start** menu, then show all apps.</span></span> <span data-ttu-id="f0398-223">Beachten Sie, dass beim lokalen Bereitstellen der App dem Menü **Start** die dazugehörige Kachel hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="f0398-223">Notice that deploying the app locally adds its tile to the **Start** menu.</span></span> <span data-ttu-id="f0398-224">Wenn Sie die App später erneut ausführen möchten (nicht im Debugmodus), tippen oder klicken Sie im Menü **Start** auf die Kachel.</span><span class="sxs-lookup"><span data-stu-id="f0398-224">To run the app again later (not in debugging mode), tap or click its tile in the **Start** menu.</span></span>

<span data-ttu-id="f0398-225">Viel zu bieten hat die App zwar noch nicht, aber trotzdem: Herzlichen Glückwunsch! Sie haben Ihre erste UWP-App erstellt!</span><span class="sxs-lookup"><span data-stu-id="f0398-225">It doesn't do much—yet—but congratulations, you've built your first UWP app!</span></span>

**<span data-ttu-id="f0398-226">So beenden Sie das Debuggen</span><span class="sxs-lookup"><span data-stu-id="f0398-226">To stop debugging</span></span>**

   <span data-ttu-id="f0398-227">Klicken Sie auf der Symbolleiste auf die Schaltfläche **Debuggen beenden** (![Schaltfläche „Debuggen beenden“](images/stopdebug.png)).</span><span class="sxs-lookup"><span data-stu-id="f0398-227">Click the **Stop Debugging** button (![Stop debugging button](images/stopdebug.png)) in the toolbar.</span></span>

   <span data-ttu-id="f0398-228">oder</span><span class="sxs-lookup"><span data-stu-id="f0398-228">–or–</span></span>

   <span data-ttu-id="f0398-229">Klicken Sie im Menü **Debuggen** auf **Debuggen beenden**.</span><span class="sxs-lookup"><span data-stu-id="f0398-229">From the **Debug** menu, click **Stop debugging**.</span></span>

   <span data-ttu-id="f0398-230">oder</span><span class="sxs-lookup"><span data-stu-id="f0398-230">–or–</span></span>

   <span data-ttu-id="f0398-231">Schließen Sie das App-Fenster.</span><span class="sxs-lookup"><span data-stu-id="f0398-231">Close the app window.</span></span>

## <a name="step-4-event-handlers"></a><span data-ttu-id="f0398-232">Schritt4: Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="f0398-232">Step 4: Event handlers</span></span>

<span data-ttu-id="f0398-233">„Ereignishandler“ klingt kompliziert, dies ist jedoch nur ein anderer Namen für den Code, der aufgerufen wird, wenn ein Ereignis auftritt (z.B. wenn der Benutzer auf die Schaltfläche klickt).</span><span class="sxs-lookup"><span data-stu-id="f0398-233">An "event handler" sounds complicated, but it's just another name for the code that is called when an event happens (such as the user clicking on your button).</span></span>

1.  <span data-ttu-id="f0398-234">Beenden Sie die Ausführung der App, sofern nicht bereits geschehen.</span><span class="sxs-lookup"><span data-stu-id="f0398-234">Stop the app from running, if you haven't already.</span></span>

2.  <span data-ttu-id="f0398-235">Doppelklicken Sie auf das Schaltflächen-Steuerelement auf die Design-Canvas, damit Visual Studio einen Ereignishandler für die Schaltfläche erstellt.</span><span class="sxs-lookup"><span data-stu-id="f0398-235">Double-click on the button control on the design canvas to make Visual Studio create an event handler for your button.</span></span>

  <span data-ttu-id="f0398-236">Natürlich können Sie den gesamten Code auch manuell erstellen.</span><span class="sxs-lookup"><span data-stu-id="f0398-236">You can of course, create all the code manually too.</span></span> <span data-ttu-id="f0398-237">Oder Sie klicken zum Auswählen auf die Schaltfläche und suchen im Bereich **Eigenschaften** unten rechts.</span><span class="sxs-lookup"><span data-stu-id="f0398-237">Or you can click on the button to select it, and look in the **Properties** pane on the lower right.</span></span> <span data-ttu-id="f0398-238">Wenn Sie zu **Ereignisse** (kleiner Gewitterblitz) wechseln, können Sie den Namen des Ereignishandlers hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f0398-238">If you switch to **Events** (the little lightning bolt) you can add the name of your event handler.</span></span>

3.  <span data-ttu-id="f0398-239">Bearbeiten Sie den Ereignishandlercode in *MainPage.xaml.cs*, der CodeBehind-Seite.</span><span class="sxs-lookup"><span data-stu-id="f0398-239">Edit the event handler code in *MainPage.xaml.cs*, the code-behind page.</span></span> <span data-ttu-id="f0398-240">An dieser Stelle wird die Sache interessant.</span><span class="sxs-lookup"><span data-stu-id="f0398-240">This is where things get interesting.</span></span> <span data-ttu-id="f0398-241">Der Standard-Ereignishandler sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="f0398-241">The default event handler looks like this:</span></span>

```cs
private void Button_Click(object sender, RoutedEventArgs e)
{

}
```

  <span data-ttu-id="f0398-242">Wir ändern ihn, damit er wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="f0398-242">Let's change it, so it looks like this:</span></span>

```cs
private async void Button_Click(object sender, RoutedEventArgs e)
{
    MediaElement mediaElement = new MediaElement();
    var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
    Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
    mediaElement.SetSource(stream, stream.ContentType);
    mediaElement.Play();
}
```

<span data-ttu-id="f0398-243">Stellen Sie sicher, dass die Methodensignatur enthält nun u. a. die **Async** -Schlüsselwort, oder Sie erhalten einen Fehler auf, wenn Sie versuchen, die app ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f0398-243">Make sure the method signature now includes the **async** keyword, or you'll get an error when you try to run the app.</span></span>

### <a name="what-did-we-just-do"></a><span data-ttu-id="f0398-244">Was haben wir gerade gemacht?</span><span class="sxs-lookup"><span data-stu-id="f0398-244">What did we just do?</span></span>

<span data-ttu-id="f0398-245">Dieser Code verwendet Windows-APIs zum Erstellen eines Sprachsyntheseobjekts und gibt dann zu sprechenden Text an.</span><span class="sxs-lookup"><span data-stu-id="f0398-245">This code uses some Windows APIs to create a speech synthesis object, and then gives it some text to say.</span></span> <span data-ttu-id="f0398-246">(Weitere Informationen zur Verwendung von SpeechSynthesis finden Sie in den Dokumenten zum [SpeechSynthesis-Namespace](https://msdn.microsoft.com/library/windows/apps/windows.media.speechsynthesis.aspx).)</span><span class="sxs-lookup"><span data-stu-id="f0398-246">(For more information on using SpeechSynthesis, see the [SpeechSynthesis namespace](https://msdn.microsoft.com/library/windows/apps/windows.media.speechsynthesis.aspx) docs.)</span></span>

<span data-ttu-id="f0398-247">Wenn Sie die App ausführen und auf die Schaltfläche klicken, sagt Ihr Computer (oder das Handy) wörtlich „Hello, World!“.</span><span class="sxs-lookup"><span data-stu-id="f0398-247">When you run the app and click on the button, your computer (or phone) will literally say "Hello, World!".</span></span>


## <a name="summary"></a><span data-ttu-id="f0398-248">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="f0398-248">Summary</span></span>

<span data-ttu-id="f0398-249">Herzlichen Glückwunsch, Sie haben Ihre erste app für Windows 10 und die UWP erstellt!</span><span class="sxs-lookup"><span data-stu-id="f0398-249">Congratulations, you've created your first app for Windows10 and the UWP!</span></span>

<span data-ttu-id="f0398-250">Informationen dazu, wie Sie XAML für die Gestaltung der Steuerelemente in Ihrer App verwenden, finden Sie im [Rasterlernprogramm](../design/layout/grid-tutorial.md). Sie können auch direkt mit den [nächsten Schritten](learn-more.md) fortfahren.</span><span class="sxs-lookup"><span data-stu-id="f0398-250">To learn how to use XAML for laying out the controls your app will use, try the [grid tutorial](../design/layout/grid-tutorial.md), or jump straight to [next steps](learn-more.md)?</span></span>

## <a name="see-also"></a><span data-ttu-id="f0398-251">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f0398-251">See Also</span></span>

* [<span data-ttu-id="f0398-252">Ihre erste App</span><span class="sxs-lookup"><span data-stu-id="f0398-252">Your first app</span></span>](your-first-app.md)
* <span data-ttu-id="f0398-253">[Veröffentlichen Sie Ihre UWP-App](https://developer.microsoft.com/store/publish-apps).</span><span class="sxs-lookup"><span data-stu-id="f0398-253">[Publishing your UWP app](https://developer.microsoft.com/store/publish-apps).</span></span>
* [<span data-ttu-id="f0398-254">Anleitungen zur Entwicklung von UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="f0398-254">How-to articles on developing UWP apps</span></span>](https://developer.microsoft.com/windows/apps/develop)
* [<span data-ttu-id="f0398-255">Codebeispiele für UWP-Entwickler</span><span class="sxs-lookup"><span data-stu-id="f0398-255">Code Samples for UWP developers</span></span>](https://developer.microsoft.com/windows/samples)
* [<span data-ttu-id="f0398-256">Was ist eine universelle Windows-App?</span><span class="sxs-lookup"><span data-stu-id="f0398-256">What's a Universal Windows app?</span></span>](universal-application-platform-guide.md)
* [<span data-ttu-id="f0398-257">Für Windows-Konto anmelden</span><span class="sxs-lookup"><span data-stu-id="f0398-257">Sign up for Windows account</span></span>](sign-up.md)
