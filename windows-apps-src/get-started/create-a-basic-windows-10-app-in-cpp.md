---
author: GrantMeStrength
ms.assetid: DC235C16-8DAF-4078-9365-6612A10F3EC3
title: "Erstellen der App „Hello World“ in C++ (Windows 10)"
description: "In Microsoft Visual Studio 2015 können Sie mithilfe von C++ eine App entwickeln, die unter Windows 10 sowie auf Smartphones mit Windows 10 ausgeführt werden kann. Die Benutzeroberfläche dieser Apps ist in XAML (Extensible Application Markup Language) definiert."
ms.author: jken
ms.date: 03/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: c6c351227eacf924314cfaa2157135a8a893704d
ms.sourcegitcommit: 968187e803a866b60cda0528718a3d31f07dc54c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="create-a-hello-world-app-in-c"></a><span data-ttu-id="c2397-105">Erstellen der App „Hello World“ (C++)</span><span class="sxs-lookup"><span data-stu-id="c2397-105">Create a "Hello world" app in C++</span></span>

<span data-ttu-id="c2397-106">Mit Microsoft Visual Studio2017 können Sie eine App in C++ entwickeln, die unter Windows10 mit einer Benutzeroberfläche ausgeführt wird, die in Extensible Application Markup Language (XAML) definiert ist.</span><span class="sxs-lookup"><span data-stu-id="c2397-106">With Microsoft Visual Studio 2017, you can use C++ to develop an app that runs on Windows 10 with a UI that's defined in Extensible Application Markup Language (XAML).</span></span>

> [!NOTE]
> <span data-ttu-id="c2397-107">In diesem Lernprogramm wird Visual Studio Community 2017 verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2397-107">This tutorial is using Visual Studio Community 2017.</span></span> <span data-ttu-id="c2397-108">Wenn Sie eine andere Version von Visual Studio verwenden, kann das Programm für Sie etwas anders aussehen.</span><span class="sxs-lookup"><span data-stu-id="c2397-108">If you are using a different version of Visual Studio, it may look a little different for you.</span></span>


## <a name="before-you-start"></a><span data-ttu-id="c2397-109">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="c2397-109">Before you start...</span></span>

-   <span data-ttu-id="c2397-110">Für dieses Lernprogramm benötigen Sie Visual Studio Community 2017 oder eine der anderen Versionen von Visual Studio 2017 sowie einen Computer mit Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c2397-110">To complete this tutorial, you must use Visual Studio Community 2017, or one of the non-Community versions of Visual Studio 2017, on a computer that's running Windows 10.</span></span> <span data-ttu-id="c2397-111">Informationen zum Herunterladen finden Sie unter [Herunterladen der Tools](http://go.microsoft.com/fwlink/p/?LinkId=532666).</span><span class="sxs-lookup"><span data-stu-id="c2397-111">To download, see [Get the tools](http://go.microsoft.com/fwlink/p/?LinkId=532666).</span></span>
-   <span data-ttu-id="c2397-112">Es wird vorausgesetzt, dass Sie über grundlegende Kenntnisse in Standard C++, XAML und den in der [XAML-Übersicht](https://msdn.microsoft.com/library/windows/apps/Mt185595) erläuterten Konzepten verfügen.</span><span class="sxs-lookup"><span data-stu-id="c2397-112">We assume you have a basic understanding of standard C++, XAML, and the concepts in the [XAML overview](https://msdn.microsoft.com/library/windows/apps/Mt185595).</span></span>
-   <span data-ttu-id="c2397-113">Wir gehen davon aus, dass Sie das Standardfensterlayout in Visual Studio verwenden.</span><span class="sxs-lookup"><span data-stu-id="c2397-113">We assume you're using the default window layout in Visual Studio.</span></span> <span data-ttu-id="c2397-114">Um das Layout auf das Standardlayout zurückzusetzen, klicken Sie in der Menüleiste auf **Fenster** > **Fensterlayout zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="c2397-114">To reset to the default layout, on the menu bar, choose **Window** > **Reset Window Layout**.</span></span>


## <a name="comparing-c-desktop-apps-to-windows-apps"></a><span data-ttu-id="c2397-115">Vergleich zwischen C++-Desktop-Apps und Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="c2397-115">Comparing C++ desktop apps to Windows apps</span></span>

<span data-ttu-id="c2397-116">Wenn Sie bereits Windows-Desktop-Apps mit C++ programmiert haben, werden Ihnen einige Aspekte der Programmierung von UWP-Apps bekannt sein, einige aber auch nicht.</span><span class="sxs-lookup"><span data-stu-id="c2397-116">If you're coming from a background in Windows desktop programming in C++, you'll probably find that some aspects of writing apps for the UWP are familiar, but other aspects require some learning.</span></span>

### <a name="whats-the-same"></a><span data-ttu-id="c2397-117">Gemeinsamkeiten</span><span class="sxs-lookup"><span data-stu-id="c2397-117">What's the same?</span></span>

-   <span data-ttu-id="c2397-118">Sie können die STL-, CRT- (mit ein paar Ausnahmen) und jede andere C++-Bibliothek verwenden, solange der Code nicht versucht, Windows-Funktionen aufzurufen, die in der Windows-Runtime-Umgebung nicht zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c2397-118">You can use the STL, the CRT (with some exceptions), and any other C++ library as long as the code does not attempt to call Windows functions that are not accessible from the Windows Runtime environment.</span></span>

-   <span data-ttu-id="c2397-119">Wenn Sie es gewohnt sind, visuelle Designer zu verwenden, können Sie immer noch den in Microsoft Visual Studio integrierten Designer verwenden, oder Sie können das Tool Blend für Visual Studio nutzen, das einen umfassenderen Umfang an Features bietet.</span><span class="sxs-lookup"><span data-stu-id="c2397-119">If you're accustomed to visual designers, you can still use the designer built into Microsoft Visual Studio, or you can use the more full-featured Blend for Visual Studio.</span></span> <span data-ttu-id="c2397-120">Wenn Sie es gewohnt sind, UI manuell zu codieren, können Sie Ihren XAML-Code manuell programmieren.</span><span class="sxs-lookup"><span data-stu-id="c2397-120">If you're accustomed to coding UI by hand, you can hand-code your XAML.</span></span>

-   <span data-ttu-id="c2397-121">Sie erstellen wie gehabt Apps, die Windows-Betriebssystemtypen und Ihre eigenen benutzerdefinierten Typen verwenden.</span><span class="sxs-lookup"><span data-stu-id="c2397-121">You're still creating apps that use Windows operating system types and your own custom types.</span></span>

-   <span data-ttu-id="c2397-122">Sie verwenden weiterhin Debugger, Profiler und andere Entwicklungstools von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c2397-122">You're still using the Visual Studio debugger, profiler, and other development tools.</span></span>

-   <span data-ttu-id="c2397-123">Sie erstellen weiterhin Apps, die mit dem Visual C++-Compiler in systemeigenem Computercode kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="c2397-123">You're still creating apps that are compiled to native machine code by the Visual C++ compiler.</span></span> <span data-ttu-id="c2397-124">Windows Store-Apps in C++ können in einer verwalteten Laufzeitumgebung nicht ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c2397-124">Windows Store apps in C++ don't execute in a managed runtime environment.</span></span>

### <a name="whats-new"></a><span data-ttu-id="c2397-125">Das ist neu:</span><span class="sxs-lookup"><span data-stu-id="c2397-125">What's new?</span></span>

-   <span data-ttu-id="c2397-126">Die Designprinzipien für Windows Store- und universelleWindows-Apps unterscheiden sich erheblich von denen für Desktop-Apps.</span><span class="sxs-lookup"><span data-stu-id="c2397-126">The design principles for Windows Store apps and Universal Windows apps are very different from those for desktop apps.</span></span> <span data-ttu-id="c2397-127">Der Schwerpunkt liegt nicht mehr auf Fensterrahmen, Bezeichnungen, Dialogfeldern usw.</span><span class="sxs-lookup"><span data-stu-id="c2397-127">Window borders, labels, dialog boxes, and so on, are de-emphasized.</span></span> <span data-ttu-id="c2397-128">Der Inhalt steht im Vordergrund.</span><span class="sxs-lookup"><span data-stu-id="c2397-128">Content is foremost.</span></span> <span data-ttu-id="c2397-129">Eindrucksvolle universelleWindows-Apps folgen diesen Prinzipien schon mit Beginn der Planungsphase.</span><span class="sxs-lookup"><span data-stu-id="c2397-129">Great Universal Windows apps incorporate these principles from the very beginning of the planning stage.</span></span>

-   <span data-ttu-id="c2397-130">Die gesamte UI wird in XAML definiert.</span><span class="sxs-lookup"><span data-stu-id="c2397-130">You're using XAML to define the entire UI.</span></span> <span data-ttu-id="c2397-131">Die Trennung zwischen UI und Kernprogrammlogik ist bei UniversalWindows-Apps viel eindeutiger als bei einer MFC- oder Win32-App.</span><span class="sxs-lookup"><span data-stu-id="c2397-131">The separation between UI and core program logic is much clearer in a Windows Universal app than in an MFC or Win32 app.</span></span> <span data-ttu-id="c2397-132">Designer können in der XAML-Datei am Erscheinungsbild der UI feilen, während Sie sich mit dem Verhalten in der Codedatei beschäftigen.</span><span class="sxs-lookup"><span data-stu-id="c2397-132">Other people can work on the appearance of the UI in the XAML file while you're working on the behavior in the code file.</span></span>

-   <span data-ttu-id="c2397-133">Sie programmieren in erster Linie für die Windows-Runtime – eine neue, navigationsfreundliche, objektorientierte API. Auf Windows-Geräten ist für einige Funktionen aber auch weiterhin Win32 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c2397-133">You're primarily programming against a new, easy-to-navigate, object-oriented API, the Windows Runtime, although on Windows devices Win32 is still available for some functionality.</span></span>

-   <span data-ttu-id="c2397-134">Sie verwenden C++/CX zum Verwenden oder Erstellen von Windows-Runtime-Objekten.</span><span class="sxs-lookup"><span data-stu-id="c2397-134">You use C++/CX to consume and create Windows Runtime objects.</span></span> <span data-ttu-id="c2397-135">C++/CX ermöglicht die Behandlung von C++-Ausnahmen, die Verwendung von Delegaten und Ereignissen sowie die automatische Verweiszählung dynamisch erstellter Objekte.</span><span class="sxs-lookup"><span data-stu-id="c2397-135">C++/CX enables C++ exception handling, delegates, events, and automatic reference counting of dynamically created objects.</span></span> <span data-ttu-id="c2397-136">Bei Verwendung von C++/CX bleibt die zugrunde liegende COM- und Windows-Architektur vor dem Code der App verborgen.</span><span class="sxs-lookup"><span data-stu-id="c2397-136">When you use C++/CX, the details of the underlying COM and Windows architecture are hidden from your app code.</span></span> <span data-ttu-id="c2397-137">Weitere Informationen finden Sie in der [Programmiersprachenreferenz für C++/CX](https://msdn.microsoft.com/library/windows/apps/hh699871.aspx).</span><span class="sxs-lookup"><span data-stu-id="c2397-137">For more information, see [C++/CX Language Reference](https://msdn.microsoft.com/library/windows/apps/hh699871.aspx).</span></span>

-   <span data-ttu-id="c2397-138">Ihre App wird zu einem Paket kompiliert, das auch Metadaten zu den in der App enthaltenen Typen, den verwendeten Ressourcen und den benötigten Funktionen (Datei-, Internet- und Kamerazugriff usw.) enthält.</span><span class="sxs-lookup"><span data-stu-id="c2397-138">Your app is compiled into a package that also contains metadata about the types that your app contains, the resources that it uses, and the capabilities that it requires (file access, internet access, camera access, and so forth).</span></span>

-   <span data-ttu-id="c2397-139">Im Windows Store und dem WindowsPhone Store wird die Sicherheit Ihrer App anhand eines Zertifizierungsprozesses geprüft, und die App kann von Millionen potenzieller Kunden entdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="c2397-139">In the Windows Store and Windows Phone Store your app is verified as safe by a certification process and made discoverable to millions of potential customers.</span></span>

## <a name="hello-world-store-app-in-c"></a><span data-ttu-id="c2397-140">Store-App „Hello, world“ in C++</span><span class="sxs-lookup"><span data-stu-id="c2397-140">Hello World Store app in C++</span></span>

<span data-ttu-id="c2397-141">Unsere erste App ist „Hello World“. Sie veranschaulicht einige grundlegende Interaktivitätsfunktionen, Layouts und Stile.</span><span class="sxs-lookup"><span data-stu-id="c2397-141">Our first app is a "Hello World" that demonstrates some basic features of interactivity, layout, and styles.</span></span> <span data-ttu-id="c2397-142">Wir erstellen eine App auf der Grundlage der Projektvorlage für universelleWindows-Apps.</span><span class="sxs-lookup"><span data-stu-id="c2397-142">We'll create an app from the Windows Universal app project template.</span></span> <span data-ttu-id="c2397-143">Wenn Sie bereits Apps für Windows8.1 und Windows Phone8.1 entwickelt haben, erinnern Sie sich wahrscheinlich daran, dass Sie drei Projekte in Visual Studio verwendet haben: eins für die Windows-App, eins für die Phone-App und ein weiteres mit gemeinsam genutztem Code.</span><span class="sxs-lookup"><span data-stu-id="c2397-143">If you've developed apps for Windows 8.1 and Windows Phone 8.1 before, you might remember that you had to have three projects in Visual Studio, one for the Windows app, one for the phone app, and another with shared code.</span></span> <span data-ttu-id="c2397-144">Die Universelle Windows-Plattform (UWP) von Windows10 ermöglicht die Verwendung eines einzelnen Projekts, das auf allen Geräten (Desktop- und Laptop-PCs mit Windows10, Tablets, Smartphones, VR-Geräte usw.) ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c2397-144">The Windows 10 Universal Windows Platform (UWP) makes it possible to have just one project, which runs on all devices, including desktop and laptop computers running Windows 10, devices such as tablets, mobile phones, VR devices and so on.</span></span>

<span data-ttu-id="c2397-145">Wir beginnen mit den Grundlagen:</span><span class="sxs-lookup"><span data-stu-id="c2397-145">We'll start with the basics:</span></span>

-   <span data-ttu-id="c2397-146">Erstellen eines universellen Windows-Projekts in Visual Studio2017.</span><span class="sxs-lookup"><span data-stu-id="c2397-146">How to create a Universal Windows project in Visual Studio 2017.</span></span>

-   <span data-ttu-id="c2397-147">Kennenlernen der erstellten Projekte und Dateien</span><span class="sxs-lookup"><span data-stu-id="c2397-147">How to understand the projects and files that are created.</span></span>

-   <span data-ttu-id="c2397-148">Kennenlernen der Erweiterungen in Visual C++-Komponentenerweiterungen (C++/CX) und ihrer Verwendungsmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="c2397-148">How to understand the extensions in Visual C++ component extensions (C++/CX), and when to use them.</span></span>

**<span data-ttu-id="c2397-149">Erstellen einer Lösung in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c2397-149">First, create a solution in Visual Studio</span></span>**

1.  <span data-ttu-id="c2397-150">Wählen Sie in der Menüleiste von Visual Studio **Datei** > **Neu** > **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="c2397-150">In Visual Studio, on the menu bar, choose **File** > **New** > **Project**.</span></span>

2.  <span data-ttu-id="c2397-151">Erweitern Sie im Dialogfeld **Neues Projekt** im linken Bereich **Installiert** > **Visual C++** > **Windows Universal**.</span><span class="sxs-lookup"><span data-stu-id="c2397-151">In the **New Project** dialog box, in the left pane, expand **Installed** > **Visual C++** > **Windows Universal**.</span></span>

> [!NOTE]
> <span data-ttu-id="c2397-152">Sie werden möglicherweise aufgefordert, die universellen Windows-Tools für die C++-Entwicklung zu installieren.</span><span class="sxs-lookup"><span data-stu-id="c2397-152">You may be prompted to install the Windows Universal tools for C++ development.</span></span>

3.  <span data-ttu-id="c2397-153">Wählen Sie im mittleren Bereich **Leere App (universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="c2397-153">In the center pane, select **Blank App (Universal Windows)**.</span></span>

   <span data-ttu-id="c2397-154">(Sollten diese Optionen nicht angezeigt werden, vergewissern Sie sich, dass die Entwicklungstools für universelle Windows-Apps installiert sind.</span><span class="sxs-lookup"><span data-stu-id="c2397-154">(If you don't see these options, make sure you have the Universal Windows App Development Tools installed.</span></span> <span data-ttu-id="c2397-155">Weitere Informationen finden Sie unter [Vorbereiten](get-set-up.md).)</span><span class="sxs-lookup"><span data-stu-id="c2397-155">See [Get set up](get-set-up.md) for more info.)</span></span>

4.  <span data-ttu-id="c2397-156">Geben Sie einen Namen für das Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="c2397-156">Enter a name for the project.</span></span> <span data-ttu-id="c2397-157">Wir nennen unser Projekt „HelloWorld“.</span><span class="sxs-lookup"><span data-stu-id="c2397-157">We'll name it HelloWorld.</span></span>

 ![<span data-ttu-id="c2397-158">C++-Projektvorlagen im Dialogfeld „Neues Projekt“</span><span class="sxs-lookup"><span data-stu-id="c2397-158">C++ project templates in the New Project dialog box</span></span> ](images/vs2017-uwp-01.png)

5.  <span data-ttu-id="c2397-159">Klicken Sie auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="c2397-159">Choose the **OK** button.</span></span>

> [!NOTE]
> <span data-ttu-id="c2397-160">Wenn Sie Visual Studio zum ersten Mal verwenden, wird möglicherweise das Dialogfeld „Einstellungen“ angezeigt, in dem Sie aufgefordert werden, **Entwicklermodus** zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c2397-160">If this is the first time you have used Visual Studio, you might see a Settings dialog asking you to enable **Developer mode**.</span></span> <span data-ttu-id="c2397-161">Der Entwicklermodus ist eine spezielle Einstellung, die bestimmte Features ermöglicht, z.B. die Berechtigung zum Ausführen von Apps, direkt und nicht nur aus dem Store.</span><span class="sxs-lookup"><span data-stu-id="c2397-161">Developer mode is a special setting that enables certain features, such as permission to run apps directly, rather than only from the Store.</span></span> <span data-ttu-id="c2397-162">Weitere Informationen finden Sie in [Aktivieren Ihres Geräts für die Entwicklung](enable-your-device-for-development.md).</span><span class="sxs-lookup"><span data-stu-id="c2397-162">For more information, please read [Enable your device for development](enable-your-device-for-development.md).</span></span> <span data-ttu-id="c2397-163">Wählen Sie **Entwicklermodus** aus, klicken Sie auf **Ja**, und schließen Sie das Dialogfeld, um mit dem Lernprogramm fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="c2397-163">To continue with this guide, select **Developer mode**, click **Yes**, and close the dialog.</span></span>

   <span data-ttu-id="c2397-164">Ihre Projektdateien werden erstellt.</span><span class="sxs-lookup"><span data-stu-id="c2397-164">Your project files are created.</span></span>

<span data-ttu-id="c2397-165">Werfen wir einen Blick darauf, was sich in der Lösung befindet, bevor wir fortfahren.</span><span class="sxs-lookup"><span data-stu-id="c2397-165">Before we go on, let’s look at what's in the solution.</span></span>

![Projektmappe der universellen App mit reduzierten Knoten](images/vs2017-uwp-02.png)

### <a name="about-the-project-files"></a><span data-ttu-id="c2397-167">Informationen zu Projektdateien</span><span class="sxs-lookup"><span data-stu-id="c2397-167">About the project files</span></span>

<span data-ttu-id="c2397-168">Jede XAML-Datei in einem Projektordner verfügt über eine zugehörige XAML.H- und eine XAML.CPP-Datei im selben Ordner und eine G- und eine G.HPP-Datei im Ordner „Generierte Dateien“, der auf dem Datenträger vorhanden ist, jedoch nicht zum Projekt gehört.</span><span class="sxs-lookup"><span data-stu-id="c2397-168">Every .xaml file in a project folder has a corresponding .xaml.h file and .xaml.cpp file in the same folder and a .g file and a .g.hpp file in the Generated Files folder, which is on disk but not part of the project.</span></span> <span data-ttu-id="c2397-169">Sie können die XAML-Dateien modifizieren, um Benutzeroberflächenelemente zu erstellen und sie mit Datenquellen zu verbinden (DataBinding).</span><span class="sxs-lookup"><span data-stu-id="c2397-169">You modify the XAML files to create UI elements and connect them to data sources (DataBinding).</span></span> <span data-ttu-id="c2397-170">Sie können die „.h“- und „.cpp“-Dateien modifizieren, um benutzerdefinierte Logik für Ereignishandler hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c2397-170">You modify the .h and .cpp files to add custom logic for event handlers.</span></span> <span data-ttu-id="c2397-171">Die automatisch erstellten Dateien stellen die Umwandlung von XAML-Markup in C++ dar.</span><span class="sxs-lookup"><span data-stu-id="c2397-171">The auto-generated files represent the transformation of the XAML markup into C++.</span></span> <span data-ttu-id="c2397-172">Verändern Sie diese Dateien nicht, sehen Sie sich die Dateien jedoch genauer an, um den CodeBehind besser zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="c2397-172">Don't modify these files, but you can study them to better understand how the code-behind works.</span></span> <span data-ttu-id="c2397-173">Im Grunde genommen enthält die generierte Datei eine partielle Klassendefinition für ein XAML-Stammelement. Diese Klasse ist die gleiche Klasse, die Sie in den XAML.H- und CPP-Dateien bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="c2397-173">Basically, the generated file contains a partial class definition for a XAML root element; this class is the same class that you modify in the \*.xaml.h and .cpp files.</span></span> <span data-ttu-id="c2397-174">Die generierten Dateien deklarieren die untergeordneten XAML-UI-Elemente als Klassenmember, sodass Sie in Ihrem Code auf sie verweisen können.</span><span class="sxs-lookup"><span data-stu-id="c2397-174">The generated files declare the XAML UI child elements as class members so that you can reference them in the code you write.</span></span> <span data-ttu-id="c2397-175">Beim Erstellen des Builds werden der generierte Code und Ihr Code zu einer vollständigen Klassendefinition zusammengeführt und anschließend kompiliert.</span><span class="sxs-lookup"><span data-stu-id="c2397-175">At build time, the generated code and your code are merged into a complete class definition and then compiled.</span></span>

<span data-ttu-id="c2397-176">Befassen wir uns zuerst mit den Projektdateien.</span><span class="sxs-lookup"><span data-stu-id="c2397-176">Let's look first at the project files.</span></span>

-   <span data-ttu-id="c2397-177">**App.xaml, App.xaml.h, App.xaml.cpp:** Stellen das Application-Objekt dar, das als Einstiegspunkt einer App fungiert.</span><span class="sxs-lookup"><span data-stu-id="c2397-177">**App.xaml, App.xaml.h, App.xaml.cpp:** Represent the Application object, which is an app's entry point.</span></span> <span data-ttu-id="c2397-178">„App.xaml“ enthält kein seitenspezifisches UI-Markup, Sie können jedoch UI-Formate und andere Elemente hinzufügen, die auf allen Seiten verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="c2397-178">App.xaml contains no page-specific UI markup, but you can add UI styles and other elements that you want to be accessible from any page.</span></span> <span data-ttu-id="c2397-179">Die CodeBehind-Dateien enthalten Handler für die Ereignisse **OnLaunched** und **OnSuspending**.</span><span class="sxs-lookup"><span data-stu-id="c2397-179">The code-behind files contain handlers for the **OnLaunched** and **OnSuspending** events.</span></span> <span data-ttu-id="c2397-180">In der Regel können Sie hier benutzerdefinierten Code hinzufügen, um Ihre App zu initialisieren, wenn sie gestartet wird, und eine Bereinigung durchzuführen, wenn sie unterbrochen oder beendet wird.</span><span class="sxs-lookup"><span data-stu-id="c2397-180">Typically, you add custom code here to initialize your app when it starts and perform cleanup when it's suspended or terminated.</span></span>
-   <span data-ttu-id="c2397-181">**MainPage.xaml, MainPage.xaml.h, MainPage.xaml.cpp:**Enthalten das XAML-Markup und den CodeBehind für die standardmäßige Startseite in einer App.</span><span class="sxs-lookup"><span data-stu-id="c2397-181">**MainPage.xaml, MainPage.xaml.h, MainPage.xaml.cpp:**Contain the XAML markup and code-behind for the default "start" page in an app.</span></span> <span data-ttu-id="c2397-182">Sie bietet keine Unterstützung für Navigation oder integrierte Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="c2397-182">It has no navigation support or built-in controls.</span></span>
-   <span data-ttu-id="c2397-183">**pch.h, pch.cpp:** Eine vorkompilierte Headerdatei und die Datei, die sie in Ihr Projekt einfügt.</span><span class="sxs-lookup"><span data-stu-id="c2397-183">**pch.h, pch.cpp:** A precompiled header file and the file that includes it in your project.</span></span> <span data-ttu-id="c2397-184">In „pch.h“ können Sie alle Header einfügen, die sich nur selten ändern und sich in anderen Dateien in der Lösung befinden.</span><span class="sxs-lookup"><span data-stu-id="c2397-184">In pch.h, you can include any headers that do not change often and are included in other files in the solution.</span></span>
-   <span data-ttu-id="c2397-185">**Package.appxmanifest:** Eine XML-Datei, in der die von Ihrer App benötigten Gerätefunktionen sowie die App-Versionsinformationen und andere Metadaten beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="c2397-185">**Package.appxmanifest:** An XML file that describes the device capabilities that your app requires, and the app version info and other metadata.</span></span> <span data-ttu-id="c2397-186">Doppelklicken Sie auf die Datei, um sie im **Manifest-Designer** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c2397-186">To open this file in the **Manifest Designer**, just double-click it.</span></span>
-   <span data-ttu-id="c2397-187">**HelloWorld\_TemporaryKey.pfx:**Ein Schlüssel von Visual Studio, der die Bereitstellung der App auf diesem Gerät ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c2397-187">**HelloWorld\_TemporaryKey.pfx:**A key that enables deployment of the app on this machine, from Visual Studio.</span></span>

## <a name="a-first-look-at-the-code"></a><span data-ttu-id="c2397-188">Ein erster Blick auf den Code</span><span class="sxs-lookup"><span data-stu-id="c2397-188">A first look at the code</span></span>

<span data-ttu-id="c2397-189">Wenn Sie den Code in den Dateien „App.Xaml.h“ und „App.Xaml.cpp“ im freigegebenen Projekt untersuchen, werden Sie feststellen, dass es sich meistens um C++-Code handelt.</span><span class="sxs-lookup"><span data-stu-id="c2397-189">If you examine the code in App.xaml.h, App.xaml.cpp in the shared project, you'll notice that it's mostly C++ code that looks familiar.</span></span> <span data-ttu-id="c2397-190">Einige Syntaxelemente kennen Sie jedoch möglicherweise nicht, wenn Sie noch nicht mit Windows-Runtime-Apps vertraut sind oder wenn Sie mit C++/CLI gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="c2397-190">However, some syntax elements might not be as familiar if you are new to Windows Runtime apps, or you've worked with C++/CLI.</span></span> <span data-ttu-id="c2397-191">Die häufigsten nicht standardmäßigen Syntaxelemente, die in C++/CX auftauchen, sind die folgenden:</span><span class="sxs-lookup"><span data-stu-id="c2397-191">Here are the most common non-standard syntax elements you'll see in C++/CX:</span></span>

**<span data-ttu-id="c2397-192">Referenzklassen</span><span class="sxs-lookup"><span data-stu-id="c2397-192">Ref classes</span></span>**

<span data-ttu-id="c2397-193">Nahezu alle Windows-Runtime-Klassen, zu denen alle Typen in der Windows-API zählen (XAML-Steuerelemente, die Seiten in Ihrer App, die App-Klasse selbst, alle Geräte- und Netzwerkobjekte sowie alle Containertypen), werden als **ref class** deklariert.</span><span class="sxs-lookup"><span data-stu-id="c2397-193">Almost all Windows Runtime classes, which includes all the types in the Windows API--XAML controls, the pages in your app, the App class itself, all device and network objects, all container types--are declared as a **ref class**.</span></span> <span data-ttu-id="c2397-194">(Einige Windows-Typen werden als **value class** oder **value struct** deklariert.)</span><span class="sxs-lookup"><span data-stu-id="c2397-194">(A few Windows types are **value class** or **value struct**).</span></span> <span data-ttu-id="c2397-195">Eine Referenzklasse (ref class) kann von beliebigen Programmiersprachen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2397-195">A ref class is consumable from any language.</span></span> <span data-ttu-id="c2397-196">In C++ wird der Lebenszyklus dieser Typen von der automatischen Verweiszählung (nicht Garbage Collection) bestimmt, sodass Sie diese Objekte niemals explizit löschen.</span><span class="sxs-lookup"><span data-stu-id="c2397-196">In C++, the lifetime of these types is governed by automatic reference counting (not garbage collection) so that you never explicitly delete these objects.</span></span> <span data-ttu-id="c2397-197">Sie können auch Ihre eigenen Referenzklassen erstellen.</span><span class="sxs-lookup"><span data-stu-id="c2397-197">You can create your own ref classes as well.</span></span>

```cpp
namespace HelloWorld
{
   /// <summary>
   /// An empty page that can be used on its own or navigated to within a Frame.
   /// </summary>
   public ref class MainPage sealed
   {
      public:
      MainPage();
   };
}
```    

<span data-ttu-id="c2397-198">Alle Windows-Runtime-Typen müssen innerhalb eines Namespace deklariert sein, und anders als bei ISOC++ haben die Typen selbst einen Zugriffsmodifikator.</span><span class="sxs-lookup"><span data-stu-id="c2397-198">All Windows Runtime types must be declared within a namespace and unlike in ISO C++ the types themselves have an accessibility modifier.</span></span> <span data-ttu-id="c2397-199">Der Modifikator **public** macht die Klasse für Komponenten für Windows-Runtime außerhalb des Namespace sichtbar.</span><span class="sxs-lookup"><span data-stu-id="c2397-199">The **public** modifier makes the class visible to Windows Runtime components outside the namespace.</span></span> <span data-ttu-id="c2397-200">Das Schlüsselwort **sealed** bedeutet, dass die Klasse nicht als Basisklasse dienen kann.</span><span class="sxs-lookup"><span data-stu-id="c2397-200">The **sealed** keyword means the class cannot serve as a base class.</span></span> <span data-ttu-id="c2397-201">Nahezu alle Referenzklassen sind „sealed“. Klassenvererbung wird häufig nicht verwendet, da JavaScript sie nicht versteht.</span><span class="sxs-lookup"><span data-stu-id="c2397-201">Almost all ref classes are sealed; class inheritance is not broadly used because Javascript does not understand it.</span></span>

<span data-ttu-id="c2397-202">**ref new** und **^ (Hütchen)**</span><span class="sxs-lookup"><span data-stu-id="c2397-202">**ref new** and **^ (hats)**</span></span>

<span data-ttu-id="c2397-203">Sie können eine Variable einer Referenzklasse deklarieren, indem Sie den Operator ^ (Hütchen) verwenden, und Sie können das Objekt mit dem Schlüsselwort „ref new“ instanziieren.</span><span class="sxs-lookup"><span data-stu-id="c2397-203">You declare a variable of a ref class by using the ^ (hat) operator, and you instantiate the object with the ref new keyword.</span></span> <span data-ttu-id="c2397-204">Danach greifen Sie auf die Instanzmethoden des Objekts mit dem Operator -> zu, wie bei einem C++-Zeiger.</span><span class="sxs-lookup"><span data-stu-id="c2397-204">Thereafter you access the object's instance methods with the -> operator just like a C++ pointer.</span></span> <span data-ttu-id="c2397-205">Auf statische Methoden kann mit dem Operator :: zugegriffen werden, genau wie in ISO C++.</span><span class="sxs-lookup"><span data-stu-id="c2397-205">Static methods are accessed with the :: operator just as in ISO C++.</span></span>

<span data-ttu-id="c2397-206">Im folgenden Code verwenden wir den vollständig qualifizierten Namen, um ein Objekt zu instanziieren, und verwenden den Operator -> zum Aufrufen einer Instanzmethode.</span><span class="sxs-lookup"><span data-stu-id="c2397-206">In the following code, we use the fully qualified name to instantiate an object, and use the -> operator to call an instance method.</span></span>

```cpp
Windows::UI::Xaml::Media::Imaging::BitmapImage^ bitmapImage =
     ref new Windows::UI::Xaml::Media::Imaging::BitmapImage();
      
bitmapImage->SetSource(fileStream);
```

<span data-ttu-id="c2397-207">In einer CPP-Datei würden wir in der Regel eine `using namespace  Windows::UI::Xaml::Media::Imaging`-Direktive und das automatische Schlüsselwort hinzufügen, sodass derselbe Code wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="c2397-207">Typically, in a .cpp file we would add a `using namespace  Windows::UI::Xaml::Media::Imaging` directive and the auto keyword, so that the same code would look like this:</span></span>

```cpp
auto bitmapImage = ref new BitmapImage();
bitmapImage->SetSource(fileStream);
```

**<span data-ttu-id="c2397-208">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="c2397-208">Properties</span></span>**

<span data-ttu-id="c2397-209">Eine Referenzklasse kann Eigenschaften haben, die, ebenso wie bei verwalteten Sprachen, spezielle Memberfunktionen darstellen, die für verwendenden Code als Felder erscheinen.</span><span class="sxs-lookup"><span data-stu-id="c2397-209">A ref class can have properties, which, just as in managed languages, are special member functions that appear as fields to consuming code.</span></span>

```cpp
public ref class SaveStateEventArgs sealed
{
   public:
   // Declare the property
   property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^>^ PageState
   {
      Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^>^ get();
   }
   ...
};

   ...
   // consume the property like a public field
   void PhotoPage::SaveState(Object^ sender, Common::SaveStateEventArgs^ e)
   {    
      if (mruToken != nullptr && !mruToken->IsEmpty())
   {
      e->PageState->Insert("mruToken", mruToken);
   }
}
```

**<span data-ttu-id="c2397-210">Delegaten</span><span class="sxs-lookup"><span data-stu-id="c2397-210">Delegates</span></span>**

<span data-ttu-id="c2397-211">Ebenso wie bei verwalteten Sprachen stellt ein Delegat einen Referenztyp dar, der eine Funktion mit einer bestimmten Signatur umschließt.</span><span class="sxs-lookup"><span data-stu-id="c2397-211">Just as in managed languages, a delegate is a reference type that encapsulates a function with a specific signature.</span></span> <span data-ttu-id="c2397-212">Sie kommen meistens mit Ereignissen und Ereignishandlern zum Einsatz.</span><span class="sxs-lookup"><span data-stu-id="c2397-212">They are most often used with events and event handlers</span></span>

```cpp
// Delegate declaration (within namespace scope)
public delegate void LoadStateEventHandler(Platform::Object^ sender, LoadStateEventArgs^ e);

// Event declaration (class scope)
public ref class NavigationHelper sealed
{
   public:
   event LoadStateEventHandler^ LoadState;
};

// Create the event handler in consuming class
MainPage::MainPage()
{
   auto navigationHelper = ref new Common::NavigationHelper(this);
   navigationHelper->LoadState += ref new Common::LoadStateEventHandler(this, &MainPage::LoadState);
}
```

## <a name="adding-content-to-the-app"></a><span data-ttu-id="c2397-213">Hinzufügen von Inhalt zur App</span><span class="sxs-lookup"><span data-stu-id="c2397-213">Adding content to the app</span></span>

<span data-ttu-id="c2397-214">Lassen Sie uns der App einige Inhalte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c2397-214">Let's add some content to the app.</span></span>

**<span data-ttu-id="c2397-215">Schritt1: Anpassen der Startseite</span><span class="sxs-lookup"><span data-stu-id="c2397-215">Step 1: Modify your start page</span></span>**

1.  <span data-ttu-id="c2397-216">Öffnen Sie im **Projektmappen-Explorer** die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="c2397-216">In **Solution Explorer**, open MainPage.xaml.</span></span>
2.  <span data-ttu-id="c2397-217">Erstellen Sie Steuerelemente für die Benutzeroberfläche, indem Sie den folgenden XAML-Code direkt vor dem schließenden Tag zum [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Stammelement hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c2397-217">Create controls for the UI by adding the following XAML to the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), immediately before its closing tag.</span></span> <span data-ttu-id="c2397-218">Er enthält ein [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) mit einem [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652), in dem der Benutzer zur Eingabe seines Namens aufgefordert wird, ein [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Element, in das der Name eingegeben wird, sowie ein [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)- und ein weiteres **TextBlock**-Element.</span><span class="sxs-lookup"><span data-stu-id="c2397-218">It contains a [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) that has a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) that asks the user's name, a [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683) element that accepts the user's name, a [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265), and another **TextBlock** element.</span></span>

    ```xaml
    <StackPanel x:Name="contentPanel" Margin="120,30,0,0">
        <TextBlock HorizontalAlignment="Left" Text="Hello World" FontSize="36"/>
        <TextBlock Text="What's your name?"/>
        <StackPanel x:Name="inputPanel" Orientation="Horizontal" Margin="0,20,0,20">
            <TextBox x:Name="nameInput" Width="300" HorizontalAlignment="Left"/>
            <Button x:Name="inputButton" Content="Say &quot;Hello&quot;"/>
        </StackPanel>
        <TextBlock x:Name="greetingOutput"/>
    </StackPanel>
    ```

3.  <span data-ttu-id="c2397-219">Sie haben nun eine sehr einfache universelle Windows-App erstellt.</span><span class="sxs-lookup"><span data-stu-id="c2397-219">At this point, you have created a very basic Universal Windows app.</span></span> <span data-ttu-id="c2397-220">Falls Sie wissen möchten, wie die UWP-App aussieht, drücken Sie F5, um die App zu erstellen, bereitzustellen und im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c2397-220">To see what the UWP app looks like, press F5 to build, deploy, and run the app in debugging mode.</span></span>

<span data-ttu-id="c2397-221">Zunächst erscheint der standardmäßige Begrüßungsbildschirm.</span><span class="sxs-lookup"><span data-stu-id="c2397-221">The default splash screen appears first.</span></span> <span data-ttu-id="c2397-222">Er setzt sich aus einem Bild (Assets\\SplashScreen.scale-100.png) und einer Hintergrundfarbe zusammen, die in der Manifestdatei der App angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="c2397-222">It has an image—Assets\\SplashScreen.scale-100.png—and a background color that are specified in the app's manifest file.</span></span> <span data-ttu-id="c2397-223">Weitere Informationen zur Anpassung des Begrüßungsbildschirms finden Sie unter [Hinzufügen eines Begrüßungsbildschirms](https://msdn.microsoft.com/library/windows/apps/Hh465332).</span><span class="sxs-lookup"><span data-stu-id="c2397-223">To learn how to customize the splash screen, see [Adding a splash screen](https://msdn.microsoft.com/library/windows/apps/Hh465332).</span></span>

<span data-ttu-id="c2397-224">Wenn der Begrüßungsbildschirm verschwindet, wird Ihre App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2397-224">When the splash screen disappears, your app appears.</span></span> <span data-ttu-id="c2397-225">Die Hauptseite der App wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2397-225">It displays the main page of the App.</span></span>

![Windows Store-App-Bildschirm mit Steuerelementen](images/xaml-hw-app2.png)

<span data-ttu-id="c2397-227">Viel zu bieten hat sie zwar noch nicht, aber trotzdem: Herzlichen Glückwunsch! Sie haben Ihre erste UWP-App erstellt!</span><span class="sxs-lookup"><span data-stu-id="c2397-227">It doesn't do much—yet—but congratulations, you've built your first Universal Windows Platform app!</span></span>

<span data-ttu-id="c2397-228">Kehren Sie zu Visual Studio zurück, und drücken Sie Umschalt+F5, um den Debugmodus zu beenden und die App zu schließen.</span><span class="sxs-lookup"><span data-stu-id="c2397-228">To stop debugging and close the app, return to Visual Studio and press Shift+F5.</span></span>

<span data-ttu-id="c2397-229">Weitere Informationen finden Sie unter [Ausführen einer Store-App über Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=619619).</span><span class="sxs-lookup"><span data-stu-id="c2397-229">For more information, see [Run a Store app from Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=619619).</span></span>

<span data-ttu-id="c2397-230">In der App können Sie etwas in das [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Element eingeben, das Klicken auf [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) hat jedoch keinerlei Auswirkung.</span><span class="sxs-lookup"><span data-stu-id="c2397-230">In the app, you can type in the [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683), but clicking the [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) doesn't do anything.</span></span> <span data-ttu-id="c2397-231">In späteren Schritten erstellen wir daher einen Ereignishandler für das [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignis der Schaltfläche, um eine personalisierte Begrüßung einzublenden.</span><span class="sxs-lookup"><span data-stu-id="c2397-231">In later steps, you create an event handler for the button's [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737) event, which displays a personalized greeting.</span></span>

## <a name="step-2-create-an-event-handler"></a><span data-ttu-id="c2397-232">Schritt2: Erstellen eines Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="c2397-232">Step 2: Create an event handler</span></span>

1.  <span data-ttu-id="c2397-233">Wählen Sie in „MainPage.xaml“ entweder in der XAML- oder in der Entwurfsansicht das [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)-Element „Say Hello“ aus dem zuvor hinzugefügten [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635)-Element aus.</span><span class="sxs-lookup"><span data-stu-id="c2397-233">In MainPage.xaml, in either XAML or design view, select the "Say Hello" [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) in the [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) you added earlier.</span></span>
2.  <span data-ttu-id="c2397-234">Öffnen Sie durch Drücken von ALT-EINGABETASTE das **Eigenschaftenfenster**, und wählen Sie anschließend die Ereignisschaltfläche (![Ereignisschaltfläche](images/eventsbutton.png)) aus.</span><span class="sxs-lookup"><span data-stu-id="c2397-234">Open the **Properties Window** by pressing Alt+Enter, and then choose the Events button (![Events button](images/eventsbutton.png)).</span></span>
3.  <span data-ttu-id="c2397-235">Suchen Sie das [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="c2397-235">Find the [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737) event.</span></span> <span data-ttu-id="c2397-236">Geben Sie im Textfeld den Namen der Funktion ein, die das **Click**-Ereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="c2397-236">In its text box, type the name of the function that handles the **Click** event.</span></span> <span data-ttu-id="c2397-237">Geben Sie für dieses Beispiel „Button\_Click“ ein.</span><span class="sxs-lookup"><span data-stu-id="c2397-237">For this example, type "Button\_Click".</span></span>

    ![Eigenschaftenfenster, Ereignisansicht](images/xaml-hw-event.png)

4.  <span data-ttu-id="c2397-239">Drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="c2397-239">Press Enter.</span></span> <span data-ttu-id="c2397-240">Die Ereignishandlermethode wird in „MainPage.xaml.cpp“ erstellt und im Code-Editor geöffnet, sodass Sie den Code hinzufügen können, der beim Auftreten des Ereignisses ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c2397-240">The event handler method is created in MainPage.xaml.cpp and opened so that you can add the code that's executed when the event occurs.</span></span>

   <span data-ttu-id="c2397-241">Gleichzeitig wird in „MainPage.xaml“ der XAML-Code für das [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)-Element aktualisiert, um den [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignishandler wie folgt zu deklarieren:</span><span class="sxs-lookup"><span data-stu-id="c2397-241">At the same time, in MainPage.xaml, the XAML for the [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) is updated to declare the [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737) event handler, like this:</span></span>

    ```xaml
    <Button Content="Say &quot;Hello&quot;" Click="Button_Click"/>
    ```

    <span data-ttu-id="c2397-242">Sie können dies auch einfach manuell zum XAML-Code hinzufügen, was vor allem dann hilfreich ist, wenn der Designer nicht geladen wird.</span><span class="sxs-lookup"><span data-stu-id="c2397-242">You could also have simply added this to the xaml code manually, which can be helpful if the designer doesn't load.</span></span> <span data-ttu-id="c2397-243">Wenn Sie dies manuell eingeben, geben Sie „Click“ ein, und warten Sie, bis IntelliSense die Option zum Hinzufügen eines neuen Ereignishandlers anzeigt.</span><span class="sxs-lookup"><span data-stu-id="c2397-243">If you enter this manually, type "Click" and then let IntelliSense pop up the option to add a new event handler.</span></span> <span data-ttu-id="c2397-244">Auf diese Weise erstellt Visual Studio die erforderliche Methodendeklaration und den erforderlichen Stub.</span><span class="sxs-lookup"><span data-stu-id="c2397-244">That way, Visual Studio creates the necessary method declaration and stub.</span></span>

    <span data-ttu-id="c2397-245">Im Designer tritt ein Fehler beim Laden auf, wenn eine unbehandelte Ausnahme während des Renderns auftritt.</span><span class="sxs-lookup"><span data-stu-id="c2397-245">The designer fails to load if an unhandled exception occurs during rendering.</span></span> <span data-ttu-id="c2397-246">Für das Rendern im Designer muss eine Entwurfszeitversion der Seite ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c2397-246">Rendering in the designer involves running a design-time version of the page.</span></span> <span data-ttu-id="c2397-247">Es ist möglicherweise hilfreich, den ausgeführten Benutzercode zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="c2397-247">It can be helpful to disable running user code.</span></span> <span data-ttu-id="c2397-248">Ändern Sie dazu die Einstellung im Dialogfeld **Tools, Optionen**.</span><span class="sxs-lookup"><span data-stu-id="c2397-248">You can do this by changing the setting in the **Tools, Options** dialog box.</span></span> <span data-ttu-id="c2397-249">Deaktivieren Sie unter **XAML-Designer** die Option **Projektcode im XAML-Designer ausführen (falls unterstützt)**.</span><span class="sxs-lookup"><span data-stu-id="c2397-249">Under **XAML Designer**, uncheck **Run project code in XAML designer (if supported)**.</span></span>

5.  <span data-ttu-id="c2397-250">Fügen Sie dem gerade erstellten **Button\_Click**-Ereignishandler in „MainPage.xaml.cpp“ den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="c2397-250">In MainPage.xaml.cpp, add the following code to the **Button\_Click** event handler that you just created.</span></span> <span data-ttu-id="c2397-251">Dieser Code ruft den Namen des Benutzers aus dem [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Steuerelement `nameInput` ab und erstellt damit eine Begrüßung.</span><span class="sxs-lookup"><span data-stu-id="c2397-251">This code retrieves the user's name from the `nameInput` [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683) control and uses it to create a greeting.</span></span> <span data-ttu-id="c2397-252">Das [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element `greetingOutput` zeigt das Ergebnis an.</span><span class="sxs-lookup"><span data-stu-id="c2397-252">The `greetingOutput` [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) displays the result.</span></span>

    ```cpp
    void HelloWorld::MainPage::Button_Click(Platform::Object^ sender, Windows::UI::Xaml::RoutedEventArgs^ e)
    {
        greetingOutput->Text = "Hello, " + nameInput->Text + "!";
    }
    ```

6.  <span data-ttu-id="c2397-253">Legen Sie das Projekt als Startprojekt fest, und drücken Sie anschließend F5, um die App zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c2397-253">Set the project as the startup, and then press F5 to build and run the app.</span></span> <span data-ttu-id="c2397-254">Wenn Sie einen Namen in das Textfeld eingeben und anschließend auf die Schaltfläche klicken, zeigt die App eine personalisierte Begrüßung an.</span><span class="sxs-lookup"><span data-stu-id="c2397-254">When you type a name in the text box and click the button, the app displays a personalized greeting.</span></span>

![App-Bildschirm mit angezeigter Meldung](images/xaml-hw-app4.png)

## <a name="step-3-style-the-start-page"></a><span data-ttu-id="c2397-256">Schritt3: Gestalten der Startseite</span><span class="sxs-lookup"><span data-stu-id="c2397-256">Step 3: Style the start page</span></span>

### <a name="choosing-a-theme"></a><span data-ttu-id="c2397-257">Auswählen eines Designs</span><span class="sxs-lookup"><span data-stu-id="c2397-257">Choosing a theme</span></span>

<span data-ttu-id="c2397-258">Das Erscheinungsbild Ihrer App lässt sich ganz einfach anpassen.</span><span class="sxs-lookup"><span data-stu-id="c2397-258">It's easy to customize the look and feel of your app.</span></span> <span data-ttu-id="c2397-259">Standardmäßig verwendet die App Ressourcen mit hellem Design.</span><span class="sxs-lookup"><span data-stu-id="c2397-259">By default, your app uses resources that have a light style.</span></span> <span data-ttu-id="c2397-260">Die Systemressourcen enthalten auch ein helles Design.</span><span class="sxs-lookup"><span data-stu-id="c2397-260">The system resources also include a light theme.</span></span> <span data-ttu-id="c2397-261">Probieren wir doch einmal aus, wie das aussieht.</span><span class="sxs-lookup"><span data-stu-id="c2397-261">Let's try it out and see what it looks like.</span></span>

**<span data-ttu-id="c2397-262">So wechseln Sie zum dunklen Design</span><span class="sxs-lookup"><span data-stu-id="c2397-262">To switch to the dark theme</span></span>**

1.  <span data-ttu-id="c2397-263">Öffnen Sie „App.xaml“.</span><span class="sxs-lookup"><span data-stu-id="c2397-263">Open App.xaml.</span></span>
2.  <span data-ttu-id="c2397-264">Bearbeiten Sie im öffnenden [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324)-Tag die [**RequestedTheme**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.requestedtheme)-Eigenschaft, und legen Sie ihren Wert auf **Dark** fest:</span><span class="sxs-lookup"><span data-stu-id="c2397-264">In the opening [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324) tag, edit the [**RequestedTheme**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.requestedtheme) property and set its value to **Dark**:</span></span>

    ```xaml
    RequestedTheme="Dark"
    ```

    <span data-ttu-id="c2397-265">Hier sehen Sie das gesamte [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324)-Tag mit dunklem Design:</span><span class="sxs-lookup"><span data-stu-id="c2397-265">Here's the full [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324) tag with the dark theme :</span></span>

    ```xaml 
        <Application
        x:Class="HelloWorld.App"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:HelloWorld"
        RequestedTheme="Dark">
    ```

3.  <span data-ttu-id="c2397-266">Drücken Sie F5, um die App zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c2397-266">Press F5 to build and run it.</span></span> <span data-ttu-id="c2397-267">Wie Sie sehen, wird nun das dunkle Design verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2397-267">Notice that it uses the dark theme.</span></span>

![App-Bildschirm mit dunklem Design](images/xaml-hw-app3.png)

<span data-ttu-id="c2397-269">Welches Design sollten Sie verwenden?</span><span class="sxs-lookup"><span data-stu-id="c2397-269">Which theme should you use?</span></span> <span data-ttu-id="c2397-270">Das bleibt ganz Ihnen überlassen.</span><span class="sxs-lookup"><span data-stu-id="c2397-270">Whichever one you want.</span></span> <span data-ttu-id="c2397-271">Bei Apps, die hauptsächlich Bilder oder Videos anzeigen, sollten Sie das dunkle Design verwenden, während sich bei Apps mit viel Text die Verwendung des hellen Designs empfiehlt.</span><span class="sxs-lookup"><span data-stu-id="c2397-271">Here's our take: for apps that mostly display images or video, we recommend the dark theme; for apps that contain a lot of text, we recommend the light theme.</span></span> <span data-ttu-id="c2397-272">Falls Sie ein benutzerdefiniertes Farbschema verwenden, wählen Sie das Design, das am besten zum Erscheinungsbild Ihrer App passt.</span><span class="sxs-lookup"><span data-stu-id="c2397-272">If you're using a custom color scheme, use the theme that goes best with your app's look and feel.</span></span> <span data-ttu-id="c2397-273">Im verbleibenden Teil dieses Lernprogramms verwenden wir in Screenshots das helle Design.</span><span class="sxs-lookup"><span data-stu-id="c2397-273">In the rest of this tutorial, we use the Light theme in screenshots.</span></span>

<span data-ttu-id="c2397-274">**Hinweis:** Das Design wird beim Aktivieren der App angewendet und kann nicht geändert werden, während die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c2397-274">**Note**  The theme is applied when the app is started and can't be changed while the app is running.</span></span>

### <a name="using-system-styles"></a><span data-ttu-id="c2397-275">Verwenden von Systemstilen</span><span class="sxs-lookup"><span data-stu-id="c2397-275">Using system styles</span></span>

<span data-ttu-id="c2397-276">Momentan ist der Text in der Windows-App ziemlich klein und nur schwer lesbar.</span><span class="sxs-lookup"><span data-stu-id="c2397-276">Right now, in the Windows app the text is very small and difficult to read.</span></span> <span data-ttu-id="c2397-277">Lassen Sie uns dies ändern, indem wir einen Systemstil anwenden.</span><span class="sxs-lookup"><span data-stu-id="c2397-277">Let's fix that by applying a system style.</span></span>

**<span data-ttu-id="c2397-278">So ändern Sie den Stil eines Elements</span><span class="sxs-lookup"><span data-stu-id="c2397-278">To change the style of an element</span></span>**

1.  <span data-ttu-id="c2397-279">Öffnen Sie „MainPage.xaml“ im Windows-Projekt.</span><span class="sxs-lookup"><span data-stu-id="c2397-279">In the Windows project, open MainPage.xaml.</span></span>
2.  <span data-ttu-id="c2397-280">Wählen Sie in der XAML- oder Entwurfsansicht das von Ihnen hinzugefügte [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element „What’s your name?“ aus.</span><span class="sxs-lookup"><span data-stu-id="c2397-280">In either XAML or design view, select the "What's your name?"[**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) that you added earlier.</span></span>
3.  <span data-ttu-id="c2397-281">Wählen Sie im Dialogfeld **Eigenschaften** (**F4**) rechts oben die Schaltfläche „Eigenschaften“ (![Schaltfläche „Eigenschaften“](images/propertiesbutton.png)) aus.</span><span class="sxs-lookup"><span data-stu-id="c2397-281">In the **Properties** window (**F4**), choose the Properties button (![Properties button](images/propertiesbutton.png)) in the upper right.</span></span>
4.  <span data-ttu-id="c2397-282">Erweitern Sie die Gruppe **Text** , und legen Sie den Schriftgrad auf „18px“ fest.</span><span class="sxs-lookup"><span data-stu-id="c2397-282">Expand the **Text** group and set the font size to 18 px.</span></span>
5.  <span data-ttu-id="c2397-283">Erweitern Sie die Gruppe **Sonstiges**, und suchen Sie dort nach der Eigenschaft **Style**.</span><span class="sxs-lookup"><span data-stu-id="c2397-283">Expand the **Miscellaneous** group and find the **Style** property.</span></span>
6.  <span data-ttu-id="c2397-284">Klicken Sie auf den Eigenschaftenmarker (das grüne Feld rechts neben der Eigenschaft **Style**), und wählen Sie anschließend **Systemressource** > **BaseTextBlockStyle** im Menü aus.</span><span class="sxs-lookup"><span data-stu-id="c2397-284">Click the property marker (the green box to the right of the **Style** property), and then, on the menu, choose **System Resource** > **BaseTextBlockStyle**.</span></span>

     <span data-ttu-id="c2397-285">**BaseTextBlockStyle** ist eine Ressource, die im [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/BR208794) unter „<root>\\Programme\\Windows Kits\\10\\Include\\winrt\\xaml\\design\\generic.xaml“ definiert ist.</span><span class="sxs-lookup"><span data-stu-id="c2397-285">**BaseTextBlockStyle** is a resource that's defined in the [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/BR208794) in <root>\\Program Files\\Windows Kits\\10\\Include\\winrt\\xaml\\design\\generic.xaml.</span></span>

    ![Eigenschaftenfenster, Eigenschaftenansicht](images/xaml-hw-style-cpp.png)

     <span data-ttu-id="c2397-287">Auf der XAML-Entwurfsoberfläche ändert sich die Textdarstellung.</span><span class="sxs-lookup"><span data-stu-id="c2397-287">On the XAML design surface, the appearance of the text changes.</span></span> <span data-ttu-id="c2397-288">Im XAML-Editor wird der XAML-Code für [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) aktualisiert:</span><span class="sxs-lookup"><span data-stu-id="c2397-288">In the XAML editor, the XAML for the [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) is updated:</span></span>

    ```xaml
    <TextBlock Text="What's your name?" Style="{StaticResource BaseTextStyle}"/>
    ```

7.  <span data-ttu-id="c2397-289">Wiederholen Sie den Vorgang, um den Schriftgrad festzulegen und **BaseTextBlockStyle** dem [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element `greetingOutput` zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="c2397-289">Repeat the process to set the font size and assign the **BaseTextBlockStyle** to the `greetingOutput`[**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) element.</span></span>

    <span data-ttu-id="c2397-290">**Tipp:** Obwohl sich in diesem [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) kein Text befindet, zeigt eine blaue Umrandung seine Position an, wenn Sie den Mauszeiger über die XAML-Entwurfsoberfläche bewegen, sodass Sie ihn auswählen können.</span><span class="sxs-lookup"><span data-stu-id="c2397-290">**Tip**  Although there's no text in this [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652), when you move the pointer over the XAML design surface, a blue outline shows where it is so that you can select it.</span></span>  

    <span data-ttu-id="c2397-291">Ihr XAML-Code sieht nun so aus:</span><span class="sxs-lookup"><span data-stu-id="c2397-291">Your XAML now looks like this:</span></span>

    ```xaml
    <StackPanel x:Name="contentPanel" Margin="120,30,0,0">
        <TextBlock Style="{ThemeResource BaseTextBlockStyle}" FontSize="18" Text="What's your name?"/>
        <StackPanel x:Name="inputPanel" Orientation="Horizontal" Margin="0,20,0,20">
            <TextBox x:Name="nameInput" Width="300" HorizontalAlignment="Left"/>
            <Button x:Name="inputButton" Content="Say &quot;Hello&quot;" Click="Button_Click"/>
        </StackPanel>
        <TextBlock Style="{ThemeResource BaseTextBlockStyle}" FontSize="18" x:Name="greetingOutput"/>
    </StackPanel>
    ```

8.  <span data-ttu-id="c2397-292">Drücken Sie F5, um die App zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c2397-292">Press F5 to build and run the app.</span></span> <span data-ttu-id="c2397-293">Sie sieht jetzt so aus:</span><span class="sxs-lookup"><span data-stu-id="c2397-293">It now looks like this:</span></span>

![App-Bildschirm mit größerem Text](images/xaml-hw-app5.png)

### <a name="step-4-adapt-the-ui-to-different-window-sizes"></a><span data-ttu-id="c2397-295">Schritt4: Anpassen der UI an verschiedene Fenstergrößen</span><span class="sxs-lookup"><span data-stu-id="c2397-295">Step 4: Adapt the UI to different window sizes</span></span>

<span data-ttu-id="c2397-296">Als Nächstes sorgen wir dafür, dass sich die UI verschiedenen Bildschirmgrößen anpasst, damit sie auch auf mobilen Geräten gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="c2397-296">Now we'll make the UI adapt to different screen sizes so it looks good on mobile devices.</span></span> <span data-ttu-id="c2397-297">Dazu fügen Sie ein [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021)-Element hinzu und legen Eigenschaften fest, die für die unterschiedlichen Ansichtszustände angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2397-297">To do this, you add a [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) and set properties that are applied for different visual states.</span></span>

**<span data-ttu-id="c2397-298">So passen Sie das UI-Layout an</span><span class="sxs-lookup"><span data-stu-id="c2397-298">To adjust the UI layout</span></span>**

1.  <span data-ttu-id="c2397-299">Fügen Sie im XAML-Editor nach dem Starttag des [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Stammelements den folgenden XAML-Block hinzu:</span><span class="sxs-lookup"><span data-stu-id="c2397-299">In the XAML editor, add this block of XAML after the opening tag of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704) element.</span></span>

    ```xaml
    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState x:Name="wideState">
                <VisualState.StateTriggers>
                    <AdaptiveTrigger MinWindowWidth="641" />
                </VisualState.StateTriggers>
            </VisualState>
            <VisualState x:Name="narrowState">
                <VisualState.StateTriggers>
                    <AdaptiveTrigger MinWindowWidth="0" />
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Target="contentPanel.Margin" Value="20,30,0,0"/>
                    <Setter Target="inputPanel.Orientation" Value="Vertical"/>
                    <Setter Target="inputButton.Margin" Value="0,4,0,0"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
    ```

2.  <span data-ttu-id="c2397-300">Debuggen Sie die App auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="c2397-300">Debug the app on the local machine.</span></span> <span data-ttu-id="c2397-301">Sie sehen, dass die UI genauso aussieht wie vorher, es sei denn, die Fensterbreite beträgt weniger als 641DIP (geräteunabhängige Pixel).</span><span class="sxs-lookup"><span data-stu-id="c2397-301">Notice that the UI looks the same as before unless the window gets narrower than 641 device-independent pixels (DIPs).</span></span>
3.  <span data-ttu-id="c2397-302">Debuggen Sie die App auf dem Emulator für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="c2397-302">Debug the app on the mobile device emulator.</span></span> <span data-ttu-id="c2397-303">Beachten Sie, dass für die UI die Eigenschaften verwendet werden, die Sie unter `narrowState` definiert haben, und dass die Benutzeroberfläche auf dem kleinen Bildschirm korrekt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c2397-303">Notice that the UI uses the properties you defined in the `narrowState` and appears correctly on the small screen.</span></span>

![Bildschirm der mobilen App mit Textdesign](images/hw10-screen2-mob.png)

<span data-ttu-id="c2397-305">Wenn Sie bereits in früheren Versionen von XAML ein [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021)-Element genutzt haben, fällt Ihnen vielleicht auf, dass hier für den XAML-Code eine vereinfachte Syntax verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c2397-305">If you've used a [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) in previous versions of XAML, you might notice that the XAML here uses a simplified syntax.</span></span>

<span data-ttu-id="c2397-306">Das [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007)-Element mit dem Namen `wideState` verfügt über ein [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382)-Element, für das die [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth)-Eigenschaft auf den Wert641 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c2397-306">The [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007) named `wideState` has an [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382) with its [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth) property set to 641.</span></span> <span data-ttu-id="c2397-307">Das bedeutet, dass der Zustand nur angewendet wird, wenn die Fensterbreite nicht geringer als die Mindestgröße von 641DIP ist.</span><span class="sxs-lookup"><span data-stu-id="c2397-307">This means that the state is to be applied only when the window width is not less than the minimum of 641 DIPs.</span></span> <span data-ttu-id="c2397-308">Da Sie keine [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817)-Objekte für diesen Zustand definieren, werden die Layouteigenschaften verwendet, die Sie im XAML-Code für den Seiteninhalt festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="c2397-308">You don't define any [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817) objects for this state, so it uses the layout properties you defined in the XAML for the page content.</span></span>

<span data-ttu-id="c2397-309">Das zweite [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007)-Element `narrowState` verfügt über ein [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382)-Element, für das die [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth)-Eigenschaft auf0 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c2397-309">The second [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007), `narrowState`, has an [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382) with its [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth) property set to 0.</span></span> <span data-ttu-id="c2397-310">Dieser Zustand wird angewendet, wenn die Fensterbreite größer0, aber kleiner als 641DIP ist.</span><span class="sxs-lookup"><span data-stu-id="c2397-310">This state is applied when the window width is greater than 0, but less than 641 DIPs.</span></span> <span data-ttu-id="c2397-311">(Bei 641DIP wird `wideState` angewendet.) In diesem Zustand definieren Sie einige [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817)-Objekte, um die Layouteigenschaften der Steuerelemente in der UI zu ändern:</span><span class="sxs-lookup"><span data-stu-id="c2397-311">(At 641 DIPs, the `wideState` is applied.) In this state, you do define some [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817) objects to change the layout properties of controls in the UI:</span></span>

-   <span data-ttu-id="c2397-312">Verringern Sie den linken Rand des `contentPanel`-Elements von120 auf20.</span><span class="sxs-lookup"><span data-stu-id="c2397-312">You reduce the left margin of the `contentPanel` element from 120 to 20.</span></span>
-   <span data-ttu-id="c2397-313">Ändern Sie das [**Orientation**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.orientation)-Element des `inputPanel`-Elements von **Horizontal** in **Vertical**.</span><span class="sxs-lookup"><span data-stu-id="c2397-313">You change the [**Orientation**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.orientation) of the `inputPanel` element from **Horizontal** to **Vertical**.</span></span>
-   <span data-ttu-id="c2397-314">Fügen Sie dem `inputButton`-Element einen oberen Rand mit einer Breite von 4DIP hinzu.</span><span class="sxs-lookup"><span data-stu-id="c2397-314">You add a top margin of 4 DIPs to the `inputButton` element.</span></span>

### <a name="summary"></a><span data-ttu-id="c2397-315">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="c2397-315">Summary</span></span>

<span data-ttu-id="c2397-316">Herzlichen Glückwunsch! Sie haben das erste Lernprogramm abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="c2397-316">Congratulations, you've completed the first tutorial!</span></span> <span data-ttu-id="c2397-317">Darin haben Sie gelernt, wie Sie Inhalte zu universellen Windows-Apps hinzufügen, wie Sie sie interaktiv machen und wie Sie ihr Erscheinungsbild ändern.</span><span class="sxs-lookup"><span data-stu-id="c2397-317">It taught how to add content to Windows Universal apps, how to add interactivity to them, and how to change their appearance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2397-318">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="c2397-318">Next steps</span></span>

<span data-ttu-id="c2397-319">Wenn Sie ein Projekt für universelle Windows-Apps für Windows8.1 und/oder Windows Phone8.1 besitzen, können Sie es zu Windows10 portieren.</span><span class="sxs-lookup"><span data-stu-id="c2397-319">If you have a Windows Universal app project that targets Windows 8.1 and/or Windows Phone 8.1, you can port it to Windows 10.</span></span> <span data-ttu-id="c2397-320">Es gibt keinen automatischen Prozess dafür, Sie können das Projekt jedoch manuell portieren.</span><span class="sxs-lookup"><span data-stu-id="c2397-320">There is no automatic process for this, but you can do it manually.</span></span> <span data-ttu-id="c2397-321">Beginnen Sie mit einem neuen universellen Windows-Projekt, um die aktuelle Projektsystemstruktur und Manifestdateien abzurufen. Kopieren Sie dann die Codedateien in die Verzeichnisstruktur des Projekts, fügen Sie Ihrem Projekt Elemente hinzu, und schreiben Sie Ihren XAML-Code mithilfe von [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) gemäß den Anweisungen in diesem Thema um.</span><span class="sxs-lookup"><span data-stu-id="c2397-321">Start with a new Windows Universal project to get the latest project system structure and manifest files, copy your code files into the project's directory structure, add the items to your project, and rewrite your XAML using the [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) according to the guidance in this topic.</span></span> <span data-ttu-id="c2397-322">Weitere Informationen finden Sie unter [Portieren eines Windows-Runtime 8-Projekts zu einem UWP-Projekt (Universelle Windows-Plattform)](https://msdn.microsoft.com/library/windows/apps/Mt188203) sowie unter [Portieren zur Universellen Windows-Plattform (C++)](http://go.microsoft.com/fwlink/p/?LinkId=619525).</span><span class="sxs-lookup"><span data-stu-id="c2397-322">For more information, see [Porting a Windows Runtime 8 project to a Universal Windows Platform (UWP) project](https://msdn.microsoft.com/library/windows/apps/Mt188203) and [Porting to the Universal Windows Platform (C++)](http://go.microsoft.com/fwlink/p/?LinkId=619525).</span></span>

<span data-ttu-id="c2397-323">Wenn Sie über C++-Code verfügen, den Sie mit einer UWP-App integrieren möchten, um beispielsweise eine neue UWP-Benutzeroberfläche für eine vorhandene Anwendung zu erstellen, finden Sie unter [Gewusst wie: Verwenden von vorhandenem C++-Code in einem universellen Windows-Projekt](http://go.microsoft.com/fwlink/p/?LinkId=619623) entsprechende Anweisungen dazu.</span><span class="sxs-lookup"><span data-stu-id="c2397-323">If you have existing C++ code that you want to integrate with a UWP app, such as to create a new UWP UI for an existing application, see [How to: Use existing C++ code in a Universal Windows project](http://go.microsoft.com/fwlink/p/?LinkId=619623).</span></span>

