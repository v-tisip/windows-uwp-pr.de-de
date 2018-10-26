---
author: GrantMeStrength
ms.assetid: DC235C16-8DAF-4078-9365-6612A10F3EC3
title: Erstellen Sie ein Hello World "app" in C++ / CX (Windows 10)
description: Mit Microsoft Visual Studio2017, können Sie verwenden C++ / CX eine app entwickeln, die auf Windows 10, sowie auf Smartphones mit Windows 10 ausgeführt wird. Die Benutzeroberfläche dieser Apps ist in XAML (Extensible Application Markup Language) definiert.
ms.author: jken
ms.date: 06/11/2018
ms.topic: article
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: bc2258557c492956130424069e6e0c4b73f28056
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5571465"
---
# <a name="create-a-hello-world-app-in-ccx"></a><span data-ttu-id="bc38a-105">Erstellen Sie eine app "Hello World" in C++ / CX</span><span class="sxs-lookup"><span data-stu-id="bc38a-105">Create a "Hello world" app in C++/CX</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc38a-106">In diesem Lernprogramm verwendet C++ / CX.</span><span class="sxs-lookup"><span data-stu-id="bc38a-106">This tutorial uses C++/CX.</span></span> <span data-ttu-id="bc38a-107">Microsoft stellt C++ / WinRT: eine vollständig standardisierte moderne C ++ 17-Programmiersprache für Windows-Runtime-APIs (WinRT).</span><span class="sxs-lookup"><span data-stu-id="bc38a-107">Microsoft has released C++/WinRT: an entirely standard modern C++17 language projection for Windows Runtime (WinRT) APIs.</span></span> <span data-ttu-id="bc38a-108">Weitere Informationen zu dieser Sprache, finden Sie unter [C++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/).</span><span class="sxs-lookup"><span data-stu-id="bc38a-108">For more information on this language, please see [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/).</span></span> 

<span data-ttu-id="bc38a-109">Mit Microsoft Visual Studio2017, können Sie verwenden C++ / CX eine app entwickeln, die auf Windows 10 mit einer Benutzeroberfläche ausgeführt wird, die in Extensible Application Markup Language (XAML) definiert ist.</span><span class="sxs-lookup"><span data-stu-id="bc38a-109">With Microsoft Visual Studio2017, you can use C++/CX to develop an app that runs on Windows10 with a UI that's defined in Extensible Application Markup Language (XAML).</span></span>

> [!NOTE]
> <span data-ttu-id="bc38a-110">In diesem Lernprogramm wird Visual Studio Community 2017 verwendet.</span><span class="sxs-lookup"><span data-stu-id="bc38a-110">This tutorial uses Visual Studio Community 2017.</span></span> <span data-ttu-id="bc38a-111">Wenn Sie eine andere Version von Visual Studio verwenden, kann das Programm für Sie etwas anders aussehen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-111">If you are using a different version of Visual Studio, it may look a little different for you.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="bc38a-112">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="bc38a-112">Before you start</span></span>

-   <span data-ttu-id="bc38a-113">Zum Durcharbeiten dieses Lernprogramms müssen Sie Visual StudioCommunity 2017 oder eine der anderen Versionen von Visual Studio2017 auf einem Computer verwenden, auf denen Windows 10 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bc38a-113">To complete this tutorial, you must use Visual StudioCommunity 2017, or one of the non-Community versions of Visual Studio2017, on a computer that's running Windows10.</span></span> <span data-ttu-id="bc38a-114">Informationen zum Herunterladen finden Sie unter [Herunterladen der Tools](http://go.microsoft.com/fwlink/p/?LinkId=532666).</span><span class="sxs-lookup"><span data-stu-id="bc38a-114">To download, see [Get the tools](http://go.microsoft.com/fwlink/p/?LinkId=532666).</span></span>
-   <span data-ttu-id="bc38a-115">Angenommen Sie haben ein grundlegendes Verständnis der C++ / CX-, XAML, und die Konzepte im [XAML-Übersicht](https://msdn.microsoft.com/library/windows/apps/Mt185595).</span><span class="sxs-lookup"><span data-stu-id="bc38a-115">We assume you have a basic understanding of C++/CX, XAML, and the concepts in the [XAML overview](https://msdn.microsoft.com/library/windows/apps/Mt185595).</span></span>
-   <span data-ttu-id="bc38a-116">Wir gehen davon aus, dass Sie das Standardfensterlayout in Visual Studio verwenden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-116">We assume you're using the default window layout in Visual Studio.</span></span> <span data-ttu-id="bc38a-117">Um das Layout auf das Standardlayout zurückzusetzen, klicken Sie in der Menüleiste auf **Fenster** > **Fensterlayout zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-117">To reset to the default layout, on the menu bar, choose **Window** > **Reset Window Layout**.</span></span>

## <a name="comparing-c-desktop-apps-to-windows-apps"></a><span data-ttu-id="bc38a-118">Vergleich zwischen C++-Desktop-Apps und Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="bc38a-118">Comparing C++ desktop apps to Windows apps</span></span>

<span data-ttu-id="bc38a-119">Wenn Sie bereits Windows-Desktop-Apps mit C++ programmiert haben, werden Ihnen einige Aspekte der Programmierung von UWP-Apps bekannt sein, einige aber auch nicht.</span><span class="sxs-lookup"><span data-stu-id="bc38a-119">If you're coming from a background in Windows desktop programming in C++, you'll probably find that some aspects of writing apps for the UWP are familiar, but other aspects require some learning.</span></span>

### <a name="whats-the-same"></a><span data-ttu-id="bc38a-120">Gemeinsamkeiten</span><span class="sxs-lookup"><span data-stu-id="bc38a-120">What's the same?</span></span>

-   <span data-ttu-id="bc38a-121">Sie können die STL-, CRT-(mit einigen Ausnahmen) und jede andere C++-Bibliothek verwenden, solange ruft der Code nur Windows-Funktionen, die in der Windows-Runtime-Umgebung zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="bc38a-121">You can use the STL, the CRT (with some exceptions), and any other C++ library as long as the code only calls Windows functions that are accessible from the Windows Runtime environment.</span></span>

-   <span data-ttu-id="bc38a-122">Wenn Sie es gewohnt sind, visuelle Designer zu verwenden, können Sie immer noch den in Microsoft Visual Studio integrierten Designer verwenden, oder Sie können das Tool Blend für Visual Studio nutzen, das einen umfassenderen Umfang an Features bietet.</span><span class="sxs-lookup"><span data-stu-id="bc38a-122">If you're accustomed to visual designers, you can still use the designer built into Microsoft Visual Studio, or you can use the more full-featured Blend for Visual Studio.</span></span> <span data-ttu-id="bc38a-123">Wenn Sie es gewohnt sind, UI manuell zu codieren, können Sie Ihren XAML-Code manuell programmieren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-123">If you're accustomed to coding UI by hand, you can hand-code your XAML.</span></span>

-   <span data-ttu-id="bc38a-124">Sie erstellen wie gehabt Apps, die Windows-Betriebssystemtypen und Ihre eigenen benutzerdefinierten Typen verwenden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-124">You're still creating apps that use Windows operating system types and your own custom types.</span></span>

-   <span data-ttu-id="bc38a-125">Sie verwenden weiterhin Debugger, Profiler und andere Entwicklungstools von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc38a-125">You're still using the Visual Studio debugger, profiler, and other development tools.</span></span>

-   <span data-ttu-id="bc38a-126">Sie erstellen weiterhin Apps, die mit dem Visual C++-Compiler in systemeigenem Computercode kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-126">You're still creating apps that are compiled to native machine code by the Visual C++ compiler.</span></span> <span data-ttu-id="bc38a-127">UWP-apps in C++ / CX in einer verwalteten Laufzeitumgebung nicht ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-127">UWP apps in C++/CX don't execute in a managed runtime environment.</span></span>

### <a name="whats-new"></a><span data-ttu-id="bc38a-128">Das ist neu:</span><span class="sxs-lookup"><span data-stu-id="bc38a-128">What's new?</span></span>

-   <span data-ttu-id="bc38a-129">Die Designprinzipien für UWP- und UniverselleWindows-Apps unterscheiden sich erheblich von denen für Desktop-Apps.</span><span class="sxs-lookup"><span data-stu-id="bc38a-129">The design principles for UWP apps and Universal Windows apps are very different from those for desktop apps.</span></span> <span data-ttu-id="bc38a-130">Der Schwerpunkt liegt nicht mehr auf Fensterrahmen, Bezeichnungen, Dialogfeldern usw.</span><span class="sxs-lookup"><span data-stu-id="bc38a-130">Window borders, labels, dialog boxes, and so on, are de-emphasized.</span></span> <span data-ttu-id="bc38a-131">Der Inhalt steht im Vordergrund.</span><span class="sxs-lookup"><span data-stu-id="bc38a-131">Content is foremost.</span></span> <span data-ttu-id="bc38a-132">Eindrucksvolle universelleWindows-Apps folgen diesen Prinzipien schon mit Beginn der Planungsphase.</span><span class="sxs-lookup"><span data-stu-id="bc38a-132">Great Universal Windows apps incorporate these principles from the very beginning of the planning stage.</span></span>

-   <span data-ttu-id="bc38a-133">Die gesamte UI wird in XAML definiert.</span><span class="sxs-lookup"><span data-stu-id="bc38a-133">You're using XAML to define the entire UI.</span></span> <span data-ttu-id="bc38a-134">Die Trennung zwischen UI und Kernprogrammlogik ist bei UniversalWindows-Apps viel eindeutiger als bei einer MFC- oder Win32-App.</span><span class="sxs-lookup"><span data-stu-id="bc38a-134">The separation between UI and core program logic is much clearer in a Windows Universal app than in an MFC or Win32 app.</span></span> <span data-ttu-id="bc38a-135">Designer können in der XAML-Datei am Erscheinungsbild der UI feilen, während Sie sich mit dem Verhalten in der Codedatei beschäftigen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-135">Other people can work on the appearance of the UI in the XAML file while you're working on the behavior in the code file.</span></span>

-   <span data-ttu-id="bc38a-136">Sie programmieren in erster Linie für die Windows-Runtime – eine neue, navigationsfreundliche, objektorientierte API. Auf Windows-Geräten ist für einige Funktionen aber auch weiterhin Win32 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bc38a-136">You're primarily programming against a new, easy-to-navigate, object-oriented API, the Windows Runtime, although on Windows devices Win32 is still available for some functionality.</span></span>

-   <span data-ttu-id="bc38a-137">Sie verwenden C++/CX zum Verwenden oder Erstellen von Windows-Runtime-Objekten.</span><span class="sxs-lookup"><span data-stu-id="bc38a-137">You use C++/CX to consume and create Windows Runtime objects.</span></span> <span data-ttu-id="bc38a-138">C++/CX ermöglicht die Behandlung von C++-Ausnahmen, die Verwendung von Delegaten und Ereignissen sowie die automatische Verweiszählung dynamisch erstellter Objekte.</span><span class="sxs-lookup"><span data-stu-id="bc38a-138">C++/CX enables C++ exception handling, delegates, events, and automatic reference counting of dynamically created objects.</span></span> <span data-ttu-id="bc38a-139">Bei Verwendung von C++/CX bleibt die zugrunde liegende COM- und Windows-Architektur vor dem Code der App verborgen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-139">When you use C++/CX, the details of the underlying COM and Windows architecture are hidden from your app code.</span></span> <span data-ttu-id="bc38a-140">Weitere Informationen finden Sie in der [Programmiersprachenreferenz für C++/CX](https://msdn.microsoft.com/library/windows/apps/hh699871.aspx).</span><span class="sxs-lookup"><span data-stu-id="bc38a-140">For more information, see [C++/CX Language Reference](https://msdn.microsoft.com/library/windows/apps/hh699871.aspx).</span></span>

-   <span data-ttu-id="bc38a-141">Ihre App wird zu einem Paket kompiliert, das auch Metadaten zu den in der App enthaltenen Typen, den verwendeten Ressourcen und den benötigten Funktionen (Datei-, Internet- und Kamerazugriff usw.) enthält.</span><span class="sxs-lookup"><span data-stu-id="bc38a-141">Your app is compiled into a package that also contains metadata about the types that your app contains, the resources that it uses, and the capabilities that it requires (file access, internet access, camera access, and so forth).</span></span>

-   <span data-ttu-id="bc38a-142">Im Microsoft Store und dem WindowsPhone Store wird die Sicherheit Ihrer App anhand eines Zertifizierungsprozesses geprüft, und die App kann von Millionen potenzieller Kunden entdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-142">In the Microsoft Store and Windows Phone Store your app is verified as safe by a certification process and made discoverable to millions of potential customers.</span></span>

## <a name="hello-world-store-app-in-ccx"></a><span data-ttu-id="bc38a-143">Hello World Store-app in C++ / CX</span><span class="sxs-lookup"><span data-stu-id="bc38a-143">Hello World Store app in C++/CX</span></span>

<span data-ttu-id="bc38a-144">Unsere erste App ist „Hello World“. Sie veranschaulicht einige grundlegende Interaktivitätsfunktionen, Layouts und Stile.</span><span class="sxs-lookup"><span data-stu-id="bc38a-144">Our first app is a "Hello World" that demonstrates some basic features of interactivity, layout, and styles.</span></span> <span data-ttu-id="bc38a-145">Wir erstellen eine App auf der Grundlage der Projektvorlage für universelleWindows-Apps.</span><span class="sxs-lookup"><span data-stu-id="bc38a-145">We'll create an app from the Windows Universal app project template.</span></span> <span data-ttu-id="bc38a-146">Wenn Sie apps für Windows8.1 und Windows Phone 8.1 vor entwickelt haben, können Sie bedenken, dass mussten Sie drei Projekte in Visual Studio, eins für die Windows-app, eins für die Phone-app und ein weiteres mit gemeinsam genutztem Code vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="bc38a-146">If you've developed apps for Windows8.1 and Windows Phone 8.1 before, you might remember that you had to have three projects in Visual Studio, one for the Windows app, one for the phone app, and another with shared code.</span></span> <span data-ttu-id="bc38a-147">Die Windows 10 Universal Windows Platform (UWP) ermöglicht es, haben nur ein Projekt, das auf allen Geräten, einschließlich Desktop- und Laptop-Computern Windows 10, Geräten wie Tablets, Smartphones, VR-Geräte und so weiter ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="bc38a-147">The Windows10 Universal Windows Platform (UWP) makes it possible to have just one project, which runs on all devices, including desktop and laptop computers running Windows10, devices such as tablets, mobile phones, VR devices and so on.</span></span>

<span data-ttu-id="bc38a-148">Wir beginnen mit den Grundlagen:</span><span class="sxs-lookup"><span data-stu-id="bc38a-148">We'll start with the basics:</span></span>

-   <span data-ttu-id="bc38a-149">So erstellen Sie eine universelle Windows-Projekt in Visual Studio2017.</span><span class="sxs-lookup"><span data-stu-id="bc38a-149">How to create a Universal Windows project in Visual Studio2017.</span></span>

-   <span data-ttu-id="bc38a-150">Kennenlernen der erstellten Projekte und Dateien</span><span class="sxs-lookup"><span data-stu-id="bc38a-150">How to understand the projects and files that are created.</span></span>

-   <span data-ttu-id="bc38a-151">Kennenlernen die Erweiterungen in für VisualC++-komponentenerweiterungen (C++ / CX), und deren Verwendung.</span><span class="sxs-lookup"><span data-stu-id="bc38a-151">How to understand the extensions in VisualC++ component extensions (C++/CX), and when to use them.</span></span>

**<span data-ttu-id="bc38a-152">Erstellen einer Lösung in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc38a-152">First, create a solution in Visual Studio</span></span>**

1.  <span data-ttu-id="bc38a-153">Wählen Sie in der Menüleiste von Visual Studio **Datei** > **Neu** > **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-153">In Visual Studio, on the menu bar, choose **File** > **New** > **Project**.</span></span>

2.  <span data-ttu-id="bc38a-154">Erweitern Sie im Dialogfeld **Neues Projekt** im linken Bereich **Installiert** > **Visual C++** > **Windows Universal**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-154">In the **New Project** dialog box, in the left pane, expand **Installed** > **Visual C++** > **Windows Universal**.</span></span>

> [!NOTE]
> <span data-ttu-id="bc38a-155">Sie werden möglicherweise aufgefordert, die universellen Windows-Tools für die C++-Entwicklung zu installieren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-155">You may be prompted to install the Windows Universal tools for C++ development.</span></span>

3.  <span data-ttu-id="bc38a-156">Wählen Sie im mittleren Bereich **Leere App (universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="bc38a-156">In the center pane, select **Blank App (Universal Windows)**.</span></span>

   <span data-ttu-id="bc38a-157">(Sollten diese Optionen nicht angezeigt werden, vergewissern Sie sich, dass die Entwicklungstools für universelle Windows-Apps installiert sind.</span><span class="sxs-lookup"><span data-stu-id="bc38a-157">(If you don't see these options, make sure you have the Universal Windows App Development Tools installed.</span></span> <span data-ttu-id="bc38a-158">Weitere Informationen finden Sie unter [Vorbereiten](get-set-up.md).)</span><span class="sxs-lookup"><span data-stu-id="bc38a-158">See [Get set up](get-set-up.md) for more info.)</span></span>

4.  <span data-ttu-id="bc38a-159">Geben Sie einen Namen für das Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="bc38a-159">Enter a name for the project.</span></span> <span data-ttu-id="bc38a-160">Wir nennen unser Projekt „HelloWorld“.</span><span class="sxs-lookup"><span data-stu-id="bc38a-160">We'll name it HelloWorld.</span></span>

 ![<span data-ttu-id="bc38a-161">C++ / CX-Projektvorlagen im Dialogfeld "Neues Projekt"</span><span class="sxs-lookup"><span data-stu-id="bc38a-161">C++/CX project templates in the New Project dialog box</span></span> ](images/vs2017-uwp-01.png)

5.  <span data-ttu-id="bc38a-162">Klicken Sie auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-162">Choose the **OK** button.</span></span>

> [!NOTE]
> <span data-ttu-id="bc38a-163">Wenn Sie Visual Studio zum ersten Mal verwenden, wird möglicherweise das Dialogfeld „Einstellungen“ angezeigt, in dem Sie aufgefordert werden, **Entwicklermodus** zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-163">If this is the first time you have used Visual Studio, you might see a Settings dialog asking you to enable **Developer mode**.</span></span> <span data-ttu-id="bc38a-164">Der Entwicklermodus ist eine spezielle Einstellung, die bestimmte Features ermöglicht, z.B. die Berechtigung zum Ausführen von Apps, direkt und nicht nur aus dem Store.</span><span class="sxs-lookup"><span data-stu-id="bc38a-164">Developer mode is a special setting that enables certain features, such as permission to run apps directly, rather than only from the Store.</span></span> <span data-ttu-id="bc38a-165">Weitere Informationen finden Sie in [Aktivieren Ihres Geräts für die Entwicklung](enable-your-device-for-development.md).</span><span class="sxs-lookup"><span data-stu-id="bc38a-165">For more information, please read [Enable your device for development](enable-your-device-for-development.md).</span></span> <span data-ttu-id="bc38a-166">Wählen Sie **Entwicklermodus** aus, klicken Sie auf **Ja**, und schließen Sie das Dialogfeld, um mit dem Lernprogramm fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-166">To continue with this guide, select **Developer mode**, click **Yes**, and close the dialog.</span></span>

   <span data-ttu-id="bc38a-167">Ihre Projektdateien werden erstellt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-167">Your project files are created.</span></span>

<span data-ttu-id="bc38a-168">Werfen wir einen Blick darauf, was sich in der Lösung befindet, bevor wir fortfahren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-168">Before we go on, let’s look at what's in the solution.</span></span>

![Projektmappe der universellen App mit reduzierten Knoten](images/vs2017-uwp-02.png)

### <a name="about-the-project-files"></a><span data-ttu-id="bc38a-170">Informationen zu Projektdateien</span><span class="sxs-lookup"><span data-stu-id="bc38a-170">About the project files</span></span>

<span data-ttu-id="bc38a-171">Jede XAML-Datei in einem Projektordner verfügt über eine zugehörige XAML.H- und eine XAML.CPP-Datei im selben Ordner und eine G- und eine G.HPP-Datei im Ordner „Generierte Dateien“, der auf dem Datenträger vorhanden ist, jedoch nicht zum Projekt gehört.</span><span class="sxs-lookup"><span data-stu-id="bc38a-171">Every .xaml file in a project folder has a corresponding .xaml.h file and .xaml.cpp file in the same folder and a .g file and a .g.hpp file in the Generated Files folder, which is on disk but not part of the project.</span></span> <span data-ttu-id="bc38a-172">Sie können die XAML-Dateien modifizieren, um Benutzeroberflächenelemente zu erstellen und sie mit Datenquellen zu verbinden (DataBinding).</span><span class="sxs-lookup"><span data-stu-id="bc38a-172">You modify the XAML files to create UI elements and connect them to data sources (DataBinding).</span></span> <span data-ttu-id="bc38a-173">Sie können die „.h“- und „.cpp“-Dateien modifizieren, um benutzerdefinierte Logik für Ereignishandler hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-173">You modify the .h and .cpp files to add custom logic for event handlers.</span></span> <span data-ttu-id="bc38a-174">Die automatisch generierte Dateien darstellen, die Umwandlung von XAML-Markup in C++ / CX.</span><span class="sxs-lookup"><span data-stu-id="bc38a-174">The auto-generated files represent the transformation of the XAML markup into C++/CX.</span></span> <span data-ttu-id="bc38a-175">Verändern Sie diese Dateien nicht, sehen Sie sich die Dateien jedoch genauer an, um den CodeBehind besser zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-175">Don't modify these files, but you can study them to better understand how the code-behind works.</span></span> <span data-ttu-id="bc38a-176">Im Grunde genommen enthält die generierte Datei eine partielle Klassendefinition für ein XAML-Stammelement. Diese Klasse ist die gleiche Klasse, die Sie in den XAML.H- und CPP-Dateien bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="bc38a-176">Basically, the generated file contains a partial class definition for a XAML root element; this class is the same class that you modify in the \*.xaml.h and .cpp files.</span></span> <span data-ttu-id="bc38a-177">Die generierten Dateien deklarieren die untergeordneten XAML-UI-Elemente als Klassenmember, sodass Sie in Ihrem Code auf sie verweisen können.</span><span class="sxs-lookup"><span data-stu-id="bc38a-177">The generated files declare the XAML UI child elements as class members so that you can reference them in the code you write.</span></span> <span data-ttu-id="bc38a-178">Beim Erstellen des Builds werden der generierte Code und Ihr Code zu einer vollständigen Klassendefinition zusammengeführt und anschließend kompiliert.</span><span class="sxs-lookup"><span data-stu-id="bc38a-178">At build time, the generated code and your code are merged into a complete class definition and then compiled.</span></span>

<span data-ttu-id="bc38a-179">Befassen wir uns zuerst mit den Projektdateien.</span><span class="sxs-lookup"><span data-stu-id="bc38a-179">Let's look first at the project files.</span></span>

-   <span data-ttu-id="bc38a-180">**App.xaml, App.xaml.h, App.xaml.cpp:** Stellen das Application-Objekt dar, das als Einstiegspunkt einer App fungiert.</span><span class="sxs-lookup"><span data-stu-id="bc38a-180">**App.xaml, App.xaml.h, App.xaml.cpp:** Represent the Application object, which is an app's entry point.</span></span> <span data-ttu-id="bc38a-181">„App.xaml“ enthält kein seitenspezifisches UI-Markup, Sie können jedoch UI-Formate und andere Elemente hinzufügen, die auf allen Seiten verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-181">App.xaml contains no page-specific UI markup, but you can add UI styles and other elements that you want to be accessible from any page.</span></span> <span data-ttu-id="bc38a-182">Die CodeBehind-Dateien enthalten Handler für die Ereignisse **OnLaunched** und **OnSuspending**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-182">The code-behind files contain handlers for the **OnLaunched** and **OnSuspending** events.</span></span> <span data-ttu-id="bc38a-183">In der Regel können Sie hier benutzerdefinierten Code hinzufügen, um Ihre App zu initialisieren, wenn sie gestartet wird, und eine Bereinigung durchzuführen, wenn sie unterbrochen oder beendet wird.</span><span class="sxs-lookup"><span data-stu-id="bc38a-183">Typically, you add custom code here to initialize your app when it starts and perform cleanup when it's suspended or terminated.</span></span>
-   <span data-ttu-id="bc38a-184">**MainPage.xaml, MainPage.xaml.h, MainPage.xaml.cpp:** Enthalten das XAML-Markup und den CodeBehind für die standardmäßige Startseite in einer App.</span><span class="sxs-lookup"><span data-stu-id="bc38a-184">**MainPage.xaml, MainPage.xaml.h, MainPage.xaml.cpp:** Contain the XAML markup and code-behind for the default "start" page in an app.</span></span> <span data-ttu-id="bc38a-185">Sie bietet keine Unterstützung für Navigation oder integrierte Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="bc38a-185">It has no navigation support or built-in controls.</span></span>
-   <span data-ttu-id="bc38a-186">**pch.h, pch.cpp:** Eine vorkompilierte Headerdatei und die Datei, die sie in Ihr Projekt einfügt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-186">**pch.h, pch.cpp:** A precompiled header file and the file that includes it in your project.</span></span> <span data-ttu-id="bc38a-187">In „pch.h“ können Sie alle Header einfügen, die sich nur selten ändern und sich in anderen Dateien in der Lösung befinden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-187">In pch.h, you can include any headers that do not change often and are included in other files in the solution.</span></span>
-   <span data-ttu-id="bc38a-188">**Package.appxmanifest:** Eine XML-Datei, in der die von Ihrer App benötigten Gerätefunktionen sowie die App-Versionsinformationen und andere Metadaten beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-188">**Package.appxmanifest:** An XML file that describes the device capabilities that your app requires, and the app version info and other metadata.</span></span> <span data-ttu-id="bc38a-189">Doppelklicken Sie auf die Datei, um sie im **Manifest-Designer** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-189">To open this file in the **Manifest Designer**, just double-click it.</span></span>
-   <span data-ttu-id="bc38a-190">**HelloWorld\_TemporaryKey.pfx:** Ein Schlüssel von Visual Studio, der die Bereitstellung der App auf diesem Gerät ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="bc38a-190">**HelloWorld\_TemporaryKey.pfx:** A key that enables deployment of the app on this machine, from Visual Studio.</span></span>

## <a name="a-first-look-at-the-code"></a><span data-ttu-id="bc38a-191">Ein erster Blick auf den Code</span><span class="sxs-lookup"><span data-stu-id="bc38a-191">A first look at the code</span></span>

<span data-ttu-id="bc38a-192">Wenn Sie den Code in den Dateien „App.Xaml.h“ und „App.Xaml.cpp“ im freigegebenen Projekt untersuchen, werden Sie feststellen, dass es sich meistens um C++-Code handelt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-192">If you examine the code in App.xaml.h, App.xaml.cpp in the shared project, you'll notice that it's mostly C++ code that looks familiar.</span></span> <span data-ttu-id="bc38a-193">Einige Syntaxelemente kennen Sie jedoch möglicherweise nicht, wenn Sie noch nicht mit Windows-Runtime-Apps vertraut sind oder wenn Sie mit C++/CLI gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="bc38a-193">However, some syntax elements might not be as familiar if you are new to Windows Runtime apps, or you've worked with C++/CLI.</span></span> <span data-ttu-id="bc38a-194">Die häufigsten nicht standardmäßigen Syntaxelemente, die in C++/CX auftauchen, sind die folgenden:</span><span class="sxs-lookup"><span data-stu-id="bc38a-194">Here are the most common non-standard syntax elements you'll see in C++/CX:</span></span>

**<span data-ttu-id="bc38a-195">Referenzklassen</span><span class="sxs-lookup"><span data-stu-id="bc38a-195">Ref classes</span></span>**

<span data-ttu-id="bc38a-196">Nahezu alle Windows-Runtime-Klassen, zu denen alle Typen in der Windows-API zählen (XAML-Steuerelemente, die Seiten in Ihrer App, die App-Klasse selbst, alle Geräte- und Netzwerkobjekte sowie alle Containertypen), werden als **ref class** deklariert.</span><span class="sxs-lookup"><span data-stu-id="bc38a-196">Almost all Windows Runtime classes, which includes all the types in the Windows API--XAML controls, the pages in your app, the App class itself, all device and network objects, all container types--are declared as a **ref class**.</span></span> <span data-ttu-id="bc38a-197">(Einige Windows-Typen werden als **value class** oder **value struct** deklariert.)</span><span class="sxs-lookup"><span data-stu-id="bc38a-197">(A few Windows types are **value class** or **value struct**).</span></span> <span data-ttu-id="bc38a-198">Eine Referenzklasse (ref class) kann von beliebigen Programmiersprachen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-198">A ref class is consumable from any language.</span></span> <span data-ttu-id="bc38a-199">In C++ / CX unterliegt die Lebensdauer dieser Typen durch automatische verweiszählung einführt (nicht der Garbagecollection), damit Sie diese Objekte nie explizit löschen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-199">In C++/CX, the lifetime of these types is governed by automatic reference counting (not garbage collection) so that you never explicitly delete these objects.</span></span> <span data-ttu-id="bc38a-200">Sie können auch Ihre eigenen Referenzklassen erstellen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-200">You can create your own ref classes as well.</span></span>

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

<span data-ttu-id="bc38a-201">Alle Windows-Runtime-Typen müssen innerhalb eines Namespace deklariert sein, und anders als bei ISOC++ haben die Typen selbst einen Zugriffsmodifikator.</span><span class="sxs-lookup"><span data-stu-id="bc38a-201">All Windows Runtime types must be declared within a namespace and unlike in ISO C++ the types themselves have an accessibility modifier.</span></span> <span data-ttu-id="bc38a-202">Der Modifikator **public** macht die Klasse für Komponenten für Windows-Runtime außerhalb des Namespace sichtbar.</span><span class="sxs-lookup"><span data-stu-id="bc38a-202">The **public** modifier makes the class visible to Windows Runtime components outside the namespace.</span></span> <span data-ttu-id="bc38a-203">Das Schlüsselwort **sealed** bedeutet, dass die Klasse nicht als Basisklasse dienen kann.</span><span class="sxs-lookup"><span data-stu-id="bc38a-203">The **sealed** keyword means the class cannot serve as a base class.</span></span> <span data-ttu-id="bc38a-204">Nahezu alle Referenzklassen sind „sealed“. Klassenvererbung wird häufig nicht verwendet, da JavaScript sie nicht versteht.</span><span class="sxs-lookup"><span data-stu-id="bc38a-204">Almost all ref classes are sealed; class inheritance is not broadly used because Javascript does not understand it.</span></span>

<span data-ttu-id="bc38a-205">**ref new** und **^ (Hütchen)**</span><span class="sxs-lookup"><span data-stu-id="bc38a-205">**ref new** and **^ (hats)**</span></span>

<span data-ttu-id="bc38a-206">Sie können eine Variable einer Referenzklasse deklarieren, indem Sie den Operator ^ (Hütchen) verwenden, und Sie können das Objekt mit dem Schlüsselwort „ref new“ instanziieren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-206">You declare a variable of a ref class by using the ^ (hat) operator, and you instantiate the object with the ref new keyword.</span></span> <span data-ttu-id="bc38a-207">Danach greifen Sie auf die Instanzmethoden des Objekts mit dem Operator -> zu, wie bei einem C++-Zeiger.</span><span class="sxs-lookup"><span data-stu-id="bc38a-207">Thereafter you access the object's instance methods with the -> operator just like a C++ pointer.</span></span> <span data-ttu-id="bc38a-208">Auf statische Methoden kann mit dem Operator :: zugegriffen werden, genau wie in ISO C++.</span><span class="sxs-lookup"><span data-stu-id="bc38a-208">Static methods are accessed with the :: operator just as in ISO C++.</span></span>

<span data-ttu-id="bc38a-209">Im folgenden Code verwenden wir den vollständig qualifizierten Namen, um ein Objekt zu instanziieren, und verwenden den Operator -> zum Aufrufen einer Instanzmethode.</span><span class="sxs-lookup"><span data-stu-id="bc38a-209">In the following code, we use the fully qualified name to instantiate an object, and use the -> operator to call an instance method.</span></span>

```cpp
Windows::UI::Xaml::Media::Imaging::BitmapImage^ bitmapImage =
     ref new Windows::UI::Xaml::Media::Imaging::BitmapImage();
      
bitmapImage->SetSource(fileStream);
```

<span data-ttu-id="bc38a-210">In einer CPP-Datei würden wir in der Regel eine `using namespace  Windows::UI::Xaml::Media::Imaging`-Direktive und das automatische Schlüsselwort hinzufügen, sodass derselbe Code wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="bc38a-210">Typically, in a .cpp file we would add a `using namespace  Windows::UI::Xaml::Media::Imaging` directive and the auto keyword, so that the same code would look like this:</span></span>

```cpp
auto bitmapImage = ref new BitmapImage();
bitmapImage->SetSource(fileStream);
```

**<span data-ttu-id="bc38a-211">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="bc38a-211">Properties</span></span>**

<span data-ttu-id="bc38a-212">Eine Referenzklasse kann Eigenschaften haben, die, ebenso wie bei verwalteten Sprachen, spezielle Memberfunktionen darstellen, die für verwendenden Code als Felder erscheinen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-212">A ref class can have properties, which, just as in managed languages, are special member functions that appear as fields to consuming code.</span></span>

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

**<span data-ttu-id="bc38a-213">Delegaten</span><span class="sxs-lookup"><span data-stu-id="bc38a-213">Delegates</span></span>**

<span data-ttu-id="bc38a-214">Ebenso wie bei verwalteten Sprachen stellt ein Delegat einen Referenztyp dar, der eine Funktion mit einer bestimmten Signatur umschließt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-214">Just as in managed languages, a delegate is a reference type that encapsulates a function with a specific signature.</span></span> <span data-ttu-id="bc38a-215">Sie kommen meistens mit Ereignissen und Ereignishandlern zum Einsatz.</span><span class="sxs-lookup"><span data-stu-id="bc38a-215">They are most often used with events and event handlers</span></span>

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

## <a name="adding-content-to-the-app"></a><span data-ttu-id="bc38a-216">Hinzufügen von Inhalt zur App</span><span class="sxs-lookup"><span data-stu-id="bc38a-216">Adding content to the app</span></span>

<span data-ttu-id="bc38a-217">Lassen Sie uns der App einige Inhalte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-217">Let's add some content to the app.</span></span>

**<span data-ttu-id="bc38a-218">Schritt1: Anpassen der Startseite</span><span class="sxs-lookup"><span data-stu-id="bc38a-218">Step 1: Modify your start page</span></span>**

1.  <span data-ttu-id="bc38a-219">Öffnen Sie im **Projektmappen-Explorer** die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="bc38a-219">In **Solution Explorer**, open MainPage.xaml.</span></span>
2.  <span data-ttu-id="bc38a-220">Erstellen Sie Steuerelemente für die Benutzeroberfläche, indem Sie den folgenden XAML-Code direkt vor dem schließenden Tag zum [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Stammelement hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-220">Create controls for the UI by adding the following XAML to the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), immediately before its closing tag.</span></span> <span data-ttu-id="bc38a-221">Er enthält ein [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) mit einem [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652), in dem der Benutzer zur Eingabe seines Namens aufgefordert wird, ein [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Element, in das der Name eingegeben wird, sowie ein [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)- und ein weiteres **TextBlock**-Element.</span><span class="sxs-lookup"><span data-stu-id="bc38a-221">It contains a [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) that has a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) that asks the user's name, a [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683) element that accepts the user's name, a [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265), and another **TextBlock** element.</span></span>

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

3.  <span data-ttu-id="bc38a-222">Sie haben nun eine sehr einfache universelle Windows-App erstellt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-222">At this point, you have created a very basic Universal Windows app.</span></span> <span data-ttu-id="bc38a-223">Falls Sie wissen möchten, wie die UWP-App aussieht, drücken Sie F5, um die App zu erstellen, bereitzustellen und im Debugmodus auszuführen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-223">To see what the UWP app looks like, press F5 to build, deploy, and run the app in debugging mode.</span></span>

<span data-ttu-id="bc38a-224">Zunächst erscheint der standardmäßige Begrüßungsbildschirm.</span><span class="sxs-lookup"><span data-stu-id="bc38a-224">The default splash screen appears first.</span></span> <span data-ttu-id="bc38a-225">Er setzt sich aus einem Bild (Assets\\SplashScreen.scale-100.png) und einer Hintergrundfarbe zusammen, die in der Manifestdatei der App angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="bc38a-225">It has an image—Assets\\SplashScreen.scale-100.png—and a background color that are specified in the app's manifest file.</span></span> <span data-ttu-id="bc38a-226">Weitere Informationen zur Anpassung des Begrüßungsbildschirms finden Sie unter [Hinzufügen eines Begrüßungsbildschirms](https://msdn.microsoft.com/library/windows/apps/Hh465332).</span><span class="sxs-lookup"><span data-stu-id="bc38a-226">To learn how to customize the splash screen, see [Adding a splash screen](https://msdn.microsoft.com/library/windows/apps/Hh465332).</span></span>

<span data-ttu-id="bc38a-227">Wenn der Begrüßungsbildschirm verschwindet, wird Ihre App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-227">When the splash screen disappears, your app appears.</span></span> <span data-ttu-id="bc38a-228">Die Hauptseite der App wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-228">It displays the main page of the App.</span></span>

![UWP-App-Bildschirm mit Steuerelementen](images/xaml-hw-app2.png)

<span data-ttu-id="bc38a-230">Viel zu bieten hat sie zwar noch nicht, aber trotzdem: Herzlichen Glückwunsch! Sie haben Ihre erste App für die Universelle Windows-Plattform erstellt!</span><span class="sxs-lookup"><span data-stu-id="bc38a-230">It doesn't do much—yet—but congratulations, you've built your first Universal Windows Platform app!</span></span>

<span data-ttu-id="bc38a-231">Kehren Sie zu Visual Studio zurück, und drücken Sie Umschalt+F5, um den Debugmodus zu beenden und die App zu schließen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-231">To stop debugging and close the app, return to Visual Studio and press Shift+F5.</span></span>

<span data-ttu-id="bc38a-232">Weitere Informationen finden Sie unter [Ausführen einer Store-App über Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=619619).</span><span class="sxs-lookup"><span data-stu-id="bc38a-232">For more information, see [Run a Store app from Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=619619).</span></span>

<span data-ttu-id="bc38a-233">In der App können Sie etwas in das [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Element eingeben, das Klicken auf [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) hat jedoch keinerlei Auswirkung.</span><span class="sxs-lookup"><span data-stu-id="bc38a-233">In the app, you can type in the [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683), but clicking the [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) doesn't do anything.</span></span> <span data-ttu-id="bc38a-234">In späteren Schritten erstellen wir daher einen Ereignishandler für das [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignis der Schaltfläche, um eine personalisierte Begrüßung einzublenden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-234">In later steps, you create an event handler for the button's [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737) event, which displays a personalized greeting.</span></span>

## <a name="step-2-create-an-event-handler"></a><span data-ttu-id="bc38a-235">Schritt2: Erstellen eines Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="bc38a-235">Step 2: Create an event handler</span></span>

1.  <span data-ttu-id="bc38a-236">Wählen Sie in „MainPage.xaml“ entweder in der XAML- oder in der Entwurfsansicht das [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)-Element „Say Hello“ aus dem zuvor hinzugefügten [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635)-Element aus.</span><span class="sxs-lookup"><span data-stu-id="bc38a-236">In MainPage.xaml, in either XAML or design view, select the "Say Hello" [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) in the [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) you added earlier.</span></span>
2.  <span data-ttu-id="bc38a-237">Öffnen Sie durch Drücken von F4 das **Eigenschaftenfenster**, und wählen Sie anschließend die Ereignisschaltfläche (![Ereignisschaltfläche](images/eventsbutton.png)) aus.</span><span class="sxs-lookup"><span data-stu-id="bc38a-237">Open the **Properties Window** by pressing F4, and then choose the Events button (![Events button](images/eventsbutton.png)).</span></span>
3.  <span data-ttu-id="bc38a-238">Suchen Sie das [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="bc38a-238">Find the [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737) event.</span></span> <span data-ttu-id="bc38a-239">Geben Sie im Textfeld den Namen der Funktion ein, die das **Click**-Ereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-239">In its text box, type the name of the function that handles the **Click** event.</span></span> <span data-ttu-id="bc38a-240">Geben Sie für dieses Beispiel „Button\_Click“ ein.</span><span class="sxs-lookup"><span data-stu-id="bc38a-240">For this example, type "Button\_Click".</span></span>

    ![Eigenschaftenfenster, Ereignisansicht](images/xaml-hw-event.png)

4.  <span data-ttu-id="bc38a-242">Drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="bc38a-242">Press Enter.</span></span> <span data-ttu-id="bc38a-243">Die Ereignishandlermethode wird in „MainPage.xaml.cpp“ erstellt und im Code-Editor geöffnet, sodass Sie den Code hinzufügen können, der beim Auftreten des Ereignisses ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bc38a-243">The event handler method is created in MainPage.xaml.cpp and opened so that you can add the code that's executed when the event occurs.</span></span>

   <span data-ttu-id="bc38a-244">Gleichzeitig wird in „MainPage.xaml“ der XAML-Code für das [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)-Element aktualisiert, um den [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignishandler wie folgt zu deklarieren:</span><span class="sxs-lookup"><span data-stu-id="bc38a-244">At the same time, in MainPage.xaml, the XAML for the [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) is updated to declare the [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737) event handler, like this:</span></span>

    ```xaml
    <Button Content="Say &quot;Hello&quot;" Click="Button_Click"/>
    ```

   <span data-ttu-id="bc38a-245">Sie können dies auch einfach manuell zum XAML-Code hinzufügen, was vor allem dann hilfreich ist, wenn der Designer nicht geladen wird.</span><span class="sxs-lookup"><span data-stu-id="bc38a-245">You could also have simply added this to the xaml code manually, which can be helpful if the designer doesn't load.</span></span> <span data-ttu-id="bc38a-246">Wenn Sie dies manuell eingeben, geben Sie „Click“ ein, und warten Sie, bis IntelliSense die Option zum Hinzufügen eines neuen Ereignishandlers anzeigt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-246">If you enter this manually, type "Click" and then let IntelliSense pop up the option to add a new event handler.</span></span> <span data-ttu-id="bc38a-247">Auf diese Weise erstellt Visual Studio die erforderliche Methodendeklaration und den erforderlichen Stub.</span><span class="sxs-lookup"><span data-stu-id="bc38a-247">That way, Visual Studio creates the necessary method declaration and stub.</span></span>

   <span data-ttu-id="bc38a-248">Im Designer tritt ein Fehler beim Laden auf, wenn eine unbehandelte Ausnahme während des Renderns auftritt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-248">The designer fails to load if an unhandled exception occurs during rendering.</span></span> <span data-ttu-id="bc38a-249">Für das Rendern im Designer muss eine Entwurfszeitversion der Seite ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-249">Rendering in the designer involves running a design-time version of the page.</span></span> <span data-ttu-id="bc38a-250">Es ist möglicherweise hilfreich, den ausgeführten Benutzercode zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-250">It can be helpful to disable running user code.</span></span> <span data-ttu-id="bc38a-251">Ändern Sie dazu die Einstellung im Dialogfeld **Tools, Optionen**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-251">You can do this by changing the setting in the **Tools, Options** dialog box.</span></span> <span data-ttu-id="bc38a-252">Deaktivieren Sie unter **XAML-Designer** die Option **Projektcode im XAML-Designer ausführen (falls unterstützt)**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-252">Under **XAML Designer**, uncheck **Run project code in XAML designer (if supported)**.</span></span>

5.  <span data-ttu-id="bc38a-253">Fügen Sie dem gerade erstellten **Button\_Click**-Ereignishandler in „MainPage.xaml.cpp“ den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="bc38a-253">In MainPage.xaml.cpp, add the following code to the **Button\_Click** event handler that you just created.</span></span> <span data-ttu-id="bc38a-254">Dieser Code ruft den Namen des Benutzers aus dem [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Steuerelement `nameInput` ab und erstellt damit eine Begrüßung.</span><span class="sxs-lookup"><span data-stu-id="bc38a-254">This code retrieves the user's name from the `nameInput` [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683) control and uses it to create a greeting.</span></span> <span data-ttu-id="bc38a-255">Das [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element `greetingOutput` zeigt das Ergebnis an.</span><span class="sxs-lookup"><span data-stu-id="bc38a-255">The `greetingOutput` [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) displays the result.</span></span>

    ```cpp
    void HelloWorld::MainPage::Button_Click(Platform::Object^ sender, Windows::UI::Xaml::RoutedEventArgs^ e)
    {
        greetingOutput->Text = "Hello, " + nameInput->Text + "!";
    }
    ```

6.  <span data-ttu-id="bc38a-256">Legen Sie das Projekt als Startprojekt fest, und drücken Sie anschließend F5, um die App zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-256">Set the project as the startup, and then press F5 to build and run the app.</span></span> <span data-ttu-id="bc38a-257">Wenn Sie einen Namen in das Textfeld eingeben und anschließend auf die Schaltfläche klicken, zeigt die App eine personalisierte Begrüßung an.</span><span class="sxs-lookup"><span data-stu-id="bc38a-257">When you type a name in the text box and click the button, the app displays a personalized greeting.</span></span>

![App-Bildschirm mit angezeigter Meldung](images/xaml-hw-app4.png)

## <a name="step-3-style-the-start-page"></a><span data-ttu-id="bc38a-259">Schritt3: Gestalten der Startseite</span><span class="sxs-lookup"><span data-stu-id="bc38a-259">Step 3: Style the start page</span></span>

### <a name="choosing-a-theme"></a><span data-ttu-id="bc38a-260">Auswählen eines Designs</span><span class="sxs-lookup"><span data-stu-id="bc38a-260">Choosing a theme</span></span>

<span data-ttu-id="bc38a-261">Das Erscheinungsbild Ihrer App lässt sich ganz einfach anpassen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-261">It's easy to customize the look and feel of your app.</span></span> <span data-ttu-id="bc38a-262">Standardmäßig verwendet die App Ressourcen mit hellem Design.</span><span class="sxs-lookup"><span data-stu-id="bc38a-262">By default, your app uses resources that have a light style.</span></span> <span data-ttu-id="bc38a-263">Die Systemressourcen enthalten auch ein helles Design.</span><span class="sxs-lookup"><span data-stu-id="bc38a-263">The system resources also include a light theme.</span></span> <span data-ttu-id="bc38a-264">Probieren wir doch einmal aus, wie das aussieht.</span><span class="sxs-lookup"><span data-stu-id="bc38a-264">Let's try it out and see what it looks like.</span></span>

**<span data-ttu-id="bc38a-265">So wechseln Sie zum dunklen Design</span><span class="sxs-lookup"><span data-stu-id="bc38a-265">To switch to the dark theme</span></span>**

1.  <span data-ttu-id="bc38a-266">Öffnen Sie „App.xaml“.</span><span class="sxs-lookup"><span data-stu-id="bc38a-266">Open App.xaml.</span></span>
2.  <span data-ttu-id="bc38a-267">Bearbeiten Sie im öffnenden [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324)-Tag die [**RequestedTheme**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.requestedtheme)-Eigenschaft, und legen Sie ihren Wert auf **Dark** fest:</span><span class="sxs-lookup"><span data-stu-id="bc38a-267">In the opening [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324) tag, edit the [**RequestedTheme**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.requestedtheme) property and set its value to **Dark**:</span></span>

    ```xaml
    RequestedTheme="Dark"
    ```

    <span data-ttu-id="bc38a-268">Hier sehen Sie das gesamte [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324)-Tag mit dunklem Design:</span><span class="sxs-lookup"><span data-stu-id="bc38a-268">Here's the full [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324) tag with the dark theme :</span></span>

    ```xaml 
        <Application
        x:Class="HelloWorld.App"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:HelloWorld"
        RequestedTheme="Dark">
    ```

3.  <span data-ttu-id="bc38a-269">Drücken Sie F5, um die App zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-269">Press F5 to build and run it.</span></span> <span data-ttu-id="bc38a-270">Wie Sie sehen, wird nun das dunkle Design verwendet.</span><span class="sxs-lookup"><span data-stu-id="bc38a-270">Notice that it uses the dark theme.</span></span>

![App-Bildschirm mit dunklem Design](images/xaml-hw-app3.png)

<span data-ttu-id="bc38a-272">Welches Design sollten Sie verwenden?</span><span class="sxs-lookup"><span data-stu-id="bc38a-272">Which theme should you use?</span></span> <span data-ttu-id="bc38a-273">Das bleibt ganz Ihnen überlassen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-273">Whichever one you want.</span></span> <span data-ttu-id="bc38a-274">Bei Apps, die hauptsächlich Bilder oder Videos anzeigen, sollten Sie das dunkle Design verwenden, während sich bei Apps mit viel Text die Verwendung des hellen Designs empfiehlt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-274">Here's our take: for apps that mostly display images or video, we recommend the dark theme; for apps that contain a lot of text, we recommend the light theme.</span></span> <span data-ttu-id="bc38a-275">Falls Sie ein benutzerdefiniertes Farbschema verwenden, wählen Sie das Design, das am besten zum Erscheinungsbild Ihrer App passt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-275">If you're using a custom color scheme, use the theme that goes best with your app's look and feel.</span></span> <span data-ttu-id="bc38a-276">Im verbleibenden Teil dieses Lernprogramms verwenden wir in Screenshots das helle Design.</span><span class="sxs-lookup"><span data-stu-id="bc38a-276">In the rest of this tutorial, we use the Light theme in screenshots.</span></span>

<span data-ttu-id="bc38a-277">**Hinweis:** das Design wird angewendet, wenn die app gestartet und kann nicht geändert werden, während die app ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bc38a-277">**Note**The theme is applied when the app is started and can't be changed while the app is running.</span></span>

### <a name="using-system-styles"></a><span data-ttu-id="bc38a-278">Verwenden von Systemstilen</span><span class="sxs-lookup"><span data-stu-id="bc38a-278">Using system styles</span></span>

<span data-ttu-id="bc38a-279">Momentan ist der Text in der Windows-App ziemlich klein und nur schwer lesbar.</span><span class="sxs-lookup"><span data-stu-id="bc38a-279">Right now, in the Windows app the text is very small and difficult to read.</span></span> <span data-ttu-id="bc38a-280">Lassen Sie uns dies ändern, indem wir einen Systemstil anwenden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-280">Let's fix that by applying a system style.</span></span>

**<span data-ttu-id="bc38a-281">So ändern Sie den Stil eines Elements</span><span class="sxs-lookup"><span data-stu-id="bc38a-281">To change the style of an element</span></span>**

1.  <span data-ttu-id="bc38a-282">Öffnen Sie „MainPage.xaml“ im Windows-Projekt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-282">In the Windows project, open MainPage.xaml.</span></span>
2.  <span data-ttu-id="bc38a-283">Wählen Sie in der XAML- oder Entwurfsansicht das von Ihnen hinzugefügte [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element „What’s your name?“ aus.</span><span class="sxs-lookup"><span data-stu-id="bc38a-283">In either XAML or design view, select the "What's your name?"[**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) that you added earlier.</span></span>
3.  <span data-ttu-id="bc38a-284">Wählen Sie im Dialogfeld **Eigenschaften** (**F4**) rechts oben die Schaltfläche „Eigenschaften“ (![Schaltfläche „Eigenschaften“](images/propertiesbutton.png)) aus.</span><span class="sxs-lookup"><span data-stu-id="bc38a-284">In the **Properties** window (**F4**), choose the Properties button (![Properties button](images/propertiesbutton.png)) in the upper right.</span></span>
4.  <span data-ttu-id="bc38a-285">Erweitern Sie die Gruppe **Text** , und legen Sie den Schriftgrad auf „18px“ fest.</span><span class="sxs-lookup"><span data-stu-id="bc38a-285">Expand the **Text** group and set the font size to 18 px.</span></span>
5.  <span data-ttu-id="bc38a-286">Erweitern Sie die Gruppe **Sonstiges**, und suchen Sie dort nach der Eigenschaft **Style**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-286">Expand the **Miscellaneous** group and find the **Style** property.</span></span>
6.  <span data-ttu-id="bc38a-287">Klicken Sie auf den Eigenschaftenmarker (das grüne Feld rechts neben der Eigenschaft **Style**), und wählen Sie anschließend **Systemressource** > **BaseTextBlockStyle** im Menü aus.</span><span class="sxs-lookup"><span data-stu-id="bc38a-287">Click the property marker (the green box to the right of the **Style** property), and then, on the menu, choose **System Resource** > **BaseTextBlockStyle**.</span></span>

     <span data-ttu-id="bc38a-288">**BaseTextBlockStyle** ist eine Ressource, die im [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/BR208794) unter „<root>\\Programme\\Windows Kits\\10\\Include\\winrt\\xaml\\design\\generic.xaml“ definiert ist.</span><span class="sxs-lookup"><span data-stu-id="bc38a-288">**BaseTextBlockStyle** is a resource that's defined in the [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/BR208794) in <root>\\Program Files\\Windows Kits\\10\\Include\\winrt\\xaml\\design\\generic.xaml.</span></span>

    ![Eigenschaftenfenster, Eigenschaftenansicht](images/xaml-hw-style-cpp.png)

     <span data-ttu-id="bc38a-290">Auf der XAML-Entwurfsoberfläche ändert sich die Textdarstellung.</span><span class="sxs-lookup"><span data-stu-id="bc38a-290">On the XAML design surface, the appearance of the text changes.</span></span> <span data-ttu-id="bc38a-291">Im XAML-Editor wird der XAML-Code für [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) aktualisiert:</span><span class="sxs-lookup"><span data-stu-id="bc38a-291">In the XAML editor, the XAML for the [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) is updated:</span></span>

    ```xaml
    <TextBlock Text="What's your name?" Style="{ThemeResource BaseTextBlockStyle}"/>
    ```

7.  <span data-ttu-id="bc38a-292">Wiederholen Sie den Vorgang, um den Schriftgrad festzulegen und **BaseTextBlockStyle** dem [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element `greetingOutput` zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-292">Repeat the process to set the font size and assign the **BaseTextBlockStyle** to the `greetingOutput`[**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) element.</span></span>

    <span data-ttu-id="bc38a-293">**Tipp:** es gibt, zwar keinen Text in diesem [**TextBlock-Element**](https://msdn.microsoft.com/library/windows/apps/BR209652), wenn Sie den Mauszeiger über die XAML-Entwurfsoberfläche bewegen eine blaue Umrandung seine Position zeigt, in denen es ist, damit Sie ihn auswählen können.</span><span class="sxs-lookup"><span data-stu-id="bc38a-293">**Tip**Although there's no text in this [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652), when you move the pointer over the XAML design surface, a blue outline shows where it is so that you can select it.</span></span>  

    <span data-ttu-id="bc38a-294">Ihr XAML-Code sieht nun so aus:</span><span class="sxs-lookup"><span data-stu-id="bc38a-294">Your XAML now looks like this:</span></span>

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

8.  <span data-ttu-id="bc38a-295">Drücken Sie F5, um die App zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-295">Press F5 to build and run the app.</span></span> <span data-ttu-id="bc38a-296">Sie sieht jetzt so aus:</span><span class="sxs-lookup"><span data-stu-id="bc38a-296">It now looks like this:</span></span>

![App-Bildschirm mit größerem Text](images/xaml-hw-app5.png)

### <a name="step-4-adapt-the-ui-to-different-window-sizes"></a><span data-ttu-id="bc38a-298">Schritt4: Anpassen der UI an verschiedene Fenstergrößen</span><span class="sxs-lookup"><span data-stu-id="bc38a-298">Step 4: Adapt the UI to different window sizes</span></span>

<span data-ttu-id="bc38a-299">Als Nächstes sorgen wir dafür, dass sich die UI verschiedenen Bildschirmgrößen anpasst, damit sie auch auf mobilen Geräten gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="bc38a-299">Now we'll make the UI adapt to different screen sizes so it looks good on mobile devices.</span></span> <span data-ttu-id="bc38a-300">Dazu fügen Sie ein [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021)-Element hinzu und legen Eigenschaften fest, die für die unterschiedlichen Ansichtszustände angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="bc38a-300">To do this, you add a [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) and set properties that are applied for different visual states.</span></span>

**<span data-ttu-id="bc38a-301">So passen Sie das UI-Layout an</span><span class="sxs-lookup"><span data-stu-id="bc38a-301">To adjust the UI layout</span></span>**

1.  <span data-ttu-id="bc38a-302">Fügen Sie im XAML-Editor nach dem Starttag des [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Stammelements den folgenden XAML-Block hinzu:</span><span class="sxs-lookup"><span data-stu-id="bc38a-302">In the XAML editor, add this block of XAML after the opening tag of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704) element.</span></span>

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

2.  <span data-ttu-id="bc38a-303">Debuggen Sie die App auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="bc38a-303">Debug the app on the local machine.</span></span> <span data-ttu-id="bc38a-304">Sie sehen, dass die UI genauso aussieht wie vorher, es sei denn, die Fensterbreite beträgt weniger als 641DIP (geräteunabhängige Pixel).</span><span class="sxs-lookup"><span data-stu-id="bc38a-304">Notice that the UI looks the same as before unless the window gets narrower than 641 device-independent pixels (DIPs).</span></span>
3.  <span data-ttu-id="bc38a-305">Debuggen Sie die App auf dem Emulator für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="bc38a-305">Debug the app on the mobile device emulator.</span></span> <span data-ttu-id="bc38a-306">Beachten Sie, dass für die UI die Eigenschaften verwendet werden, die Sie unter `narrowState` definiert haben, und dass die Benutzeroberfläche auf dem kleinen Bildschirm korrekt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bc38a-306">Notice that the UI uses the properties you defined in the `narrowState` and appears correctly on the small screen.</span></span>

![Bildschirm der mobilen App mit Textdesign](images/hw10-screen2-mob.png)

<span data-ttu-id="bc38a-308">Wenn Sie bereits in früheren Versionen von XAML ein [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021)-Element genutzt haben, fällt Ihnen vielleicht auf, dass hier für den XAML-Code eine vereinfachte Syntax verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bc38a-308">If you've used a [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) in previous versions of XAML, you might notice that the XAML here uses a simplified syntax.</span></span>

<span data-ttu-id="bc38a-309">Das [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007)-Element mit dem Namen `wideState` verfügt über ein [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382)-Element, für das die [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth)-Eigenschaft auf den Wert641 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="bc38a-309">The [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007) named `wideState` has an [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382) with its [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth) property set to 641.</span></span> <span data-ttu-id="bc38a-310">Das bedeutet, dass der Zustand nur angewendet wird, wenn die Fensterbreite nicht geringer als die Mindestgröße von 641DIP ist.</span><span class="sxs-lookup"><span data-stu-id="bc38a-310">This means that the state is to be applied only when the window width is not less than the minimum of 641 DIPs.</span></span> <span data-ttu-id="bc38a-311">Da Sie keine [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817)-Objekte für diesen Zustand definieren, werden die Layouteigenschaften verwendet, die Sie im XAML-Code für den Seiteninhalt festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="bc38a-311">You don't define any [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817) objects for this state, so it uses the layout properties you defined in the XAML for the page content.</span></span>

<span data-ttu-id="bc38a-312">Das zweite [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007)-Element `narrowState` verfügt über ein [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382)-Element, für das die [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth)-Eigenschaft auf0 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="bc38a-312">The second [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007), `narrowState`, has an [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382) with its [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth) property set to 0.</span></span> <span data-ttu-id="bc38a-313">Dieser Zustand wird angewendet, wenn die Fensterbreite größer0, aber kleiner als 641DIP ist.</span><span class="sxs-lookup"><span data-stu-id="bc38a-313">This state is applied when the window width is greater than 0, but less than 641 DIPs.</span></span> <span data-ttu-id="bc38a-314">(Bei 641DIP wird `wideState` angewendet.) In diesem Zustand definieren Sie einige [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817)-Objekte, um die Layouteigenschaften der Steuerelemente in der UI zu ändern:</span><span class="sxs-lookup"><span data-stu-id="bc38a-314">(At 641 DIPs, the `wideState` is applied.) In this state, you do define some [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817) objects to change the layout properties of controls in the UI:</span></span>

-   <span data-ttu-id="bc38a-315">Verringern Sie den linken Rand des `contentPanel`-Elements von120 auf20.</span><span class="sxs-lookup"><span data-stu-id="bc38a-315">You reduce the left margin of the `contentPanel` element from 120 to 20.</span></span>
-   <span data-ttu-id="bc38a-316">Ändern Sie das [**Orientation**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.orientation)-Element des `inputPanel`-Elements von **Horizontal** in **Vertical**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-316">You change the [**Orientation**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.orientation) of the `inputPanel` element from **Horizontal** to **Vertical**.</span></span>
-   <span data-ttu-id="bc38a-317">Fügen Sie dem `inputButton`-Element einen oberen Rand mit einer Breite von 4DIP hinzu.</span><span class="sxs-lookup"><span data-stu-id="bc38a-317">You add a top margin of 4 DIPs to the `inputButton` element.</span></span>

### <a name="summary"></a><span data-ttu-id="bc38a-318">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="bc38a-318">Summary</span></span>

<span data-ttu-id="bc38a-319">Herzlichen Glückwunsch! Sie haben das erste Lernprogramm abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-319">Congratulations, you've completed the first tutorial!</span></span> <span data-ttu-id="bc38a-320">Darin haben Sie gelernt, wie Sie Inhalte zu universellen Windows-Apps hinzufügen, wie Sie sie interaktiv machen und wie Sie ihr Erscheinungsbild ändern.</span><span class="sxs-lookup"><span data-stu-id="bc38a-320">It taught how to add content to Windows Universal apps, how to add interactivity to them, and how to change their appearance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bc38a-321">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="bc38a-321">Next steps</span></span>

<span data-ttu-id="bc38a-322">Wenn Sie ein universelle Windows-app-Projekt, das Windows8.1 und/oder Windows Phone 8.1 ausgerichtet ist verfügen, können Sie es zu Windows 10 portieren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-322">If you have a Windows Universal app project that targets Windows8.1 and/or Windows Phone 8.1, you can port it to Windows10.</span></span> <span data-ttu-id="bc38a-323">Es gibt keinen automatischen Prozess dafür, Sie können das Projekt jedoch manuell portieren.</span><span class="sxs-lookup"><span data-stu-id="bc38a-323">There is no automatic process for this, but you can do it manually.</span></span> <span data-ttu-id="bc38a-324">Beginnen Sie mit einem neuen universellen Windows-Projekt, um die aktuelle Projektsystemstruktur und Manifestdateien abzurufen. Kopieren Sie dann die Codedateien in die Verzeichnisstruktur des Projekts, fügen Sie Ihrem Projekt Elemente hinzu, und schreiben Sie Ihren XAML-Code mithilfe von [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) gemäß den Anweisungen in diesem Thema um.</span><span class="sxs-lookup"><span data-stu-id="bc38a-324">Start with a new Windows Universal project to get the latest project system structure and manifest files, copy your code files into the project's directory structure, add the items to your project, and rewrite your XAML using the [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) according to the guidance in this topic.</span></span> <span data-ttu-id="bc38a-325">Weitere Informationen finden Sie unter [Portieren eines Windows-Runtime 8-Projekts zu einem UWP-Projekt (Universelle Windows-Plattform)](https://msdn.microsoft.com/library/windows/apps/Mt188203) sowie unter [Portieren zur Universellen Windows-Plattform (C++)](http://go.microsoft.com/fwlink/p/?LinkId=619525).</span><span class="sxs-lookup"><span data-stu-id="bc38a-325">For more information, see [Porting a Windows Runtime 8 project to a Universal Windows Platform (UWP) project](https://msdn.microsoft.com/library/windows/apps/Mt188203) and [Porting to the Universal Windows Platform (C++)](http://go.microsoft.com/fwlink/p/?LinkId=619525).</span></span>

<span data-ttu-id="bc38a-326">Wenn Sie über C++-Code verfügen, den Sie mit einer UWP-App integrieren möchten, um beispielsweise eine neue UWP-Benutzeroberfläche für eine vorhandene Anwendung zu erstellen, finden Sie unter [Gewusst wie: Verwenden von vorhandenem C++-Code in einem universellen Windows-Projekt](http://go.microsoft.com/fwlink/p/?LinkId=619623) entsprechende Anweisungen dazu.</span><span class="sxs-lookup"><span data-stu-id="bc38a-326">If you have existing C++ code that you want to integrate with a UWP app, such as to create a new UWP UI for an existing application, see [How to: Use existing C++ code in a Universal Windows project](http://go.microsoft.com/fwlink/p/?LinkId=619623).</span></span>

