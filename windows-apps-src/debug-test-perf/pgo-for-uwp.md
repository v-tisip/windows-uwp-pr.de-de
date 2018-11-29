---
title: Ausführung der Profile Guided Optimization (PGO) auf Universal Windows Platform- (UWP) Apps
ms.localizationpriority: medium
ms.openlocfilehash: 1d7321f0ef49c12ac4506fb72fab937fde77f740
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "7989197"
---
# <a name="running-profile-guided-optimization-on-universal-windows-platform-apps"></a><span data-ttu-id="83929-102">Ausführung der Profile Guided Optimization auf Universal Windows Platform-Apps</span><span class="sxs-lookup"><span data-stu-id="83929-102">Running Profile Guided Optimization on Universal Windows Platform apps</span></span> 
 
<span data-ttu-id="83929-103">Dieses Thema enthält eine schrittweise Anleitung zum Anwenden von Profile Guided Optimization (PGO) auf Universal Windows Platform- (UWP) Apps.</span><span class="sxs-lookup"><span data-stu-id="83929-103">This topic provides a step-by-step guide to applying Profile Guided Optimization (PGO) to Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="83929-104">Nicht alle Schrittefür klassische Win32-Anwendungen sind für UWP-Apps verfügbar, wir verfolgen daher das Ziel, den Prozess zu erläutern, der zur Einbeziehung von PGO erforderlich ist, um die Optimierung einfacher und zugänglicher für UWP-Entwickler zu machen.</span><span class="sxs-lookup"><span data-stu-id="83929-104">Not all of the steps available to classic win32 applications are available to UWP apps, so our goal is to explain the process necessary to incorporate PGO to make optimizing easier and more accessible to UWP developers.</span></span>

<span data-ttu-id="83929-105">Im folgenden finden eine grundlegende exemplarische Vorgehensweise für die Anwendung von PGO für die Standard-DirectX11-App (UWP)-Vorlage mit Visual Studio2015 Update 3.</span><span class="sxs-lookup"><span data-stu-id="83929-105">The following is a basic walkthrough of applying PGO to the default DirectX 11 app (UWP) template by using Visual Studio 2015 Update 3.</span></span>
 
<span data-ttu-id="83929-106">Die Bildschirmfotos in dieser Anleitung basieren auf dem folgenden neuen Projekt: ![Dialogfeld „Neues Projekt“</span><span class="sxs-lookup"><span data-stu-id="83929-106">The screenshots throughout this guide are based on the following new project: ![New Project dialog</span></span>](images/pgo-001.png)

<span data-ttu-id="83929-107">So wenden Sie PGO auf die DirectX11-App-Vorlage an:</span><span class="sxs-lookup"><span data-stu-id="83929-107">To apply PGO to the DirectX 11 app template:</span></span>

1. <span data-ttu-id="83929-108">Legen Sie die Lösungskonfiguration auf **Freigabe** fest, oder wählen Sie eine Lösungskonfiguration, in der Sie zur Freigabe bestimmten optimierten Code generieren.</span><span class="sxs-lookup"><span data-stu-id="83929-108">Set your solution configuration to **Release** or choose a solution configuration where you are generating optimized code intended for release.</span></span> <span data-ttu-id="83929-109">Zwar können Sie PGO theoretisch auf einem Debug-Build ausführen, es wäre jedoch ineffektiv, PGO für die Optimierung eines ansonsten nicht optimierten Builds zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="83929-109">While you could theoretically run PGO on a debug build, it would be ineffective to use PGO to optimize an otherwise unoptimized build.</span></span> 
 
 ![App1-Fenster](images/pgo-002.png)
 
2. <span data-ttu-id="83929-111">Überprüfen Sie in den Eigenschaften ihres Projekts (**Eigenschaften** > **C/C++** > **Optimierung**), ob Sie mit dem /GL-Flag für **Optimierung des ganzen Programms** arbeiten (dies ist möglicherweise bereits durch Ihre Konfiguration festgelegt).</span><span class="sxs-lookup"><span data-stu-id="83929-111">Verify in your project’s properties (**Properties** > **C/C++** > **Optimization**) that you are building with the /GL flag for **Whole Program Optimization** (this may already be set by your configuration).</span></span>

 ![Optimierung des ganzen Programms](images/pgo-003.png)

3. <span data-ttu-id="83929-113">Gehen Sie zu Ihren Linker-Eigenschaften (**Eigenschaften** > **Linker** > **Optimierung**), und setzen Sie **Link-Zeitcode-Generierung** auf **Profilgeführte Optimierung - Instrument (LTCG:PGInstrument)**.</span><span class="sxs-lookup"><span data-stu-id="83929-113">Go into your linker properties (**Properties** > **Linker** > **Optimization**) and set **Link Time Code Generation** to **Profile Guided Optimization - Instrument (LTCG:PGInstrument)**.</span></span>
 
 ![Link-Zeitcode-Generierung](images/pgo-004.png)

4. <span data-ttu-id="83929-115">Wählen Sie **Projektmappe**, und wählen Sie dann **Projektmappe bereitstellen**.</span><span class="sxs-lookup"><span data-stu-id="83929-115">Select **Build Solution**, and then select **Deploy Solution**.</span></span> 

 ![Dialogfeld „Neues Projekt“](images/pgo-005.png)
 
 <span data-ttu-id="83929-117">Sie können sich vergewissern, dass alles korrekt funktioniert hat, indem Sie den Ausgabespeicherort des Builds betrachten und prüfen, ob eine.pgd-Datei generiert wurde.</span><span class="sxs-lookup"><span data-stu-id="83929-117">You can double check that everything has worked properly by looking at the build output location and verifying that a .pgd file has been generated.</span></span> <span data-ttu-id="83929-118">In diesem Beispielfall bedeutet dies, dass die folgenden Datei zusammen mit der Build-Ausgabe generiert wurde.</span><span class="sxs-lookup"><span data-stu-id="83929-118">In this example case, this meant that the following file was generated alongside the build output:</span></span>
 
 `C:\Users\<USER>\Documents\Visual Studio 2015\Projects\App1\Release\App1\App1.pgd`

 <span data-ttu-id="83929-119">Standardmäßig hat die PGD-Datei den gleichen Namen wie die .exe-Datei.</span><span class="sxs-lookup"><span data-stu-id="83929-119">By default, the .pgd file will have the same name as your executable.</span></span> <span data-ttu-id="83929-120">Sie können den Namen der generierten .pgd-Datei ändern, indem Sie die Linker-Option **Profilegeführte Datenbank** ändern.</span><span class="sxs-lookup"><span data-stu-id="83929-120">You can also change the name of the .pgd file that is generated by changing the **Profile Guided Database** linker option.</span></span> 
 
5. <span data-ttu-id="83929-121">Navigieren Sie zu Ihrem Visual Studio-VC-Binärdateien-Verzeichnis (standardmäßig sieht dies wie folgt aus `C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin`).</span><span class="sxs-lookup"><span data-stu-id="83929-121">Navigate to your Visual Studio VC binaries directory (by default this looks like `C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin`).</span></span> <span data-ttu-id="83929-122">Kopieren Sie für x86-.exe-Dateien `pgort140.dll`; für x64-.exe-Dateien die x64-Version von `amd64\pgort140.dll`.</span><span class="sxs-lookup"><span data-stu-id="83929-122">For x86 executables, copy `pgort140.dll`; for x64 executables, copy the x64 version from `amd64\pgort140.dll`.</span></span> <span data-ttu-id="83929-123">Fügen Sie die entsprechende Version von `pgort140.dll`in das Stammverzeichnis des bereitgestellten Pakets ein.</span><span class="sxs-lookup"><span data-stu-id="83929-123">Paste the appropriate version of `pgort140.dll` into the root of your deployed package.</span></span> <span data-ttu-id="83929-124">Für dieses Beispiel lautet der Pfad:</span><span class="sxs-lookup"><span data-stu-id="83929-124">For this sample the path is:</span></span>

 `C:\Users\<USER>\Documents\Visual Studio 2015\Projects\App1\Release\App1\AppX\`

 <span data-ttu-id="83929-125">Dieser Schrittist erforderlich, da UWP-Apps nur Bibliotheken laden können, die in ihrem Paket vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="83929-125">This step is necessary because UWP apps can only load libraries that exist within their package.</span></span>

 ![Dialogfeld „Neues Projekt“](images/pgo-006.png)
 
6. <span data-ttu-id="83929-127">Führen Sie die App aus dem Menü Start-Menü oder aus dem Visual Studio **Debug**-Menü mit der Option **Starten ohne Debugging**.</span><span class="sxs-lookup"><span data-stu-id="83929-127">Run the app either from the Start menu or from the Visual Studio **Debug** menu with the **Start Without Debugging** option.</span></span> 

 ![Dialogfeld „Neues Projekt“](images/pgo-007.png)
 
7. <span data-ttu-id="83929-129">Der Build, der jetzt ausgeführt wird, ist instrumentiert und generiert PGO Daten.</span><span class="sxs-lookup"><span data-stu-id="83929-129">The build that is now running is instrumented and generating PGO data.</span></span> <span data-ttu-id="83929-130">An dieser Stelle sollten Sie die Anwendung mit einem der üblichsten Szenarien ausführen, das Sie optimieren möchten.</span><span class="sxs-lookup"><span data-stu-id="83929-130">At this point, you should run the application through some of the most common scenarios that you intend to optimize.</span></span> <span data-ttu-id="83929-131">Nach Ausführung des Programms mit den beabsichtigten Szenarien finden Sie das pgosweep.exe-Tool im selben Ordner, in dem Sie die entsprechende Version von `pgort140.dll` gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="83929-131">After the program has run through the intended scenarios, find the pgosweep.exe tool located in the same folder where you found the appropriate version of `pgort140.dll`.</span></span> <span data-ttu-id="83929-132">Alternativ hat eine native Visual Studio (x86/x64)-Eingabeaufforderung die korrekte Version bereits in ihrem Pfad.</span><span class="sxs-lookup"><span data-stu-id="83929-132">Alternately, a Visual Studio (x86/x64) Native Tools command prompt will already have the appropriate version in its path.</span></span> <span data-ttu-id="83929-133">Um die PGO Daten zu erfassen, führen Sie den folgenden Befehl durch, während die Anwendung noch läuft, um eine .pgc-Datei zu erstellen, die die Profilierungsdaten enthält:</span><span class="sxs-lookup"><span data-stu-id="83929-133">To gather the PGO data, run the following command while the application is still running to generate a .pgc file that will contain the profiling data:</span></span>
 
  `pgosweep.exe <executable name> <output file>` 
 
  <span data-ttu-id="83929-134">Sie können auch die pgosweep.exe-Hilfe konsultieren (`pgosweep.exe /help`), um andere optionale Argumente für die Steuerung der Erfassung von PGO-Daten zu finden.</span><span class="sxs-lookup"><span data-stu-id="83929-134">You can also look at the pgosweep.exe help (`pgosweep.exe /help`) to view other optional arguments for controlling the way you gather PGO data.</span></span>
 
  <span data-ttu-id="83929-135">Es ist sinnvoll, die .pgc-Dateien an dem Build-Speicherort auszugeben, an dem sich die .pgd-Datei befindet, und die Dateien als `<PGDName>!<RunIdentifier>.pgc` zu bezeichnen.</span><span class="sxs-lookup"><span data-stu-id="83929-135">It is a good idea to output the .pgc files into the build location where the .pgd is located, and also to name the files `<PGDName>!<RunIdentifier>.pgc`.</span></span> <span data-ttu-id="83929-136">In diesem Beispiel bedeutet dies:</span><span class="sxs-lookup"><span data-stu-id="83929-136">For this example, this meant:</span></span>
 
  ```
  pgosweep.exe App1.exe “C:\Users\<USER>\Documents\Visual Studio 2015\Projects\App1\Release\App1\App1!1.pgc”
  ```
 
  <span data-ttu-id="83929-137">Die weitere Sammlung könnte auch `App1!CoreScenario.pgc`, `App1!UseCase5.pgc` u.dgl. sein. Wenn die .pgc-Dateien auf diese Weise benannt werden und sich zusammen mit der .pgd-Datei am Build-Speicherort befinden, werden Sie bei der Verknüpfung in Schritt 9 automatisch verknüpft.</span><span class="sxs-lookup"><span data-stu-id="83929-137">Further gathering could also be `App1!CoreScenario.pgc`, `App1!UseCase5.pgc`, etc. If the .pgc files are named in this way and in the build output location alongside the .pgd, they will be automatically merged when linking in step 9.</span></span>
 
8. <span data-ttu-id="83929-138">OPTIONAL: Standardmäßig werden alle .pgc-Dateien, die wie in Schritt 7 angegeben benannt und neben der .pgd-Datei abgelegt sind, bei der Verknüpfung zusammengeführt und gleich gewichtet, Sie können jedoch weiter steuern, wie bestimmte Durchläufe gewichtet werden.</span><span class="sxs-lookup"><span data-stu-id="83929-138">OPTIONAL: By default, all .pgc files named as specified in step 7 and placed next to the .pgd will be merged when linking and weighted equally, but you can also have greater control over how particular runs are weighted.</span></span> <span data-ttu-id="83929-139">Zu diesem Zweck verwenden Sie das **pgomgr.exe**-Tool, das sich im selben Ordner befindet, in dem Sie zuerst die Kopie von `pgort140.dll` gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="83929-139">To do this, you will use the **pgomgr.exe** tool also located in the same folder where you first found the copy of `pgort140.dll`.</span></span> <span data-ttu-id="83929-140">Um beispielsweise den `CoreScenario`-Durchlauf mit der dreifachen Priorität anderer Durchläufe zusammenzuführen, kann der folgende Befehl verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="83929-140">For example, to merge the `CoreScenario` run with 3 times the priority of other runs, I can use the following command:</span></span>
 
 ```
 pgomgr.exe -merge:3 “C:\Users\<USER>\Documents\Visual Studio 2015\Projects\App1\Release\App1\App1!CoreScenario.pgc” “C:\Users\<USER>\Documents\Visual Studio 2015\Projects\App1\Release\App1\App1.pgd”
 ```
 
9. <span data-ttu-id="83929-141">Nachdem Sie eine oder mehrere .pgc-Dateien generiert und sie entweder neben Ihre .pgd-Datei gesetzt oder manuell zusammengeführt haben (Schritt 8), können Sie mit dem Linker den abschließenden optimierten Build erstellen.</span><span class="sxs-lookup"><span data-stu-id="83929-141">After you have generated one or more .pgc files and either placed them alongside your .pgd or manually merged them (step 8), we can now use the linker to create the final optimized build.</span></span> <span data-ttu-id="83929-142">Wechseln Sie zurück zu Ihren Linker-Eigenschaften (**Eigenschaften** > **Linker** > **Optimierung**) und setzen Sie **Link-Zeitcode-Generierung** auf **Profilgeführte Optimierung - Optimierung (LTCG: PGOPTIMIZE)**; stellen Sie sicher, dass **Profilgeführte Datenbank** auf die .pgd-Datei verweist, die Sie verwenden möchten (wenn Sie dies nicht geändert haben, sollte alles in Ordnung sein).</span><span class="sxs-lookup"><span data-stu-id="83929-142">Go back into your linker properties (**Properties** > **Linker** > **Optimization**) and set **Link Time Code Generation** to **Profile Guided Optimization - Optimization (LTCG:PGOptimize)** and verify that **Profile Guided Database** is pointing at the .pgd that you intend to use (if you have not changed this, everything should be in order).</span></span>

 ![Dialogfeld „Neues Projekt“](images/pgo-009.png)
 
10. <span data-ttu-id="83929-144">Nachdem das Projekt erstellt wurde, ruft der Linker pgomgr.exe zur Zusammenführung aller `<PGDName>!*.pgc`-Datei in die .pgd-Datei mit dem Standard-Gewicht 1 auf, und die resultierende Anwendung wird auf der Grundlage der Profilierungsdaten optimiert.</span><span class="sxs-lookup"><span data-stu-id="83929-144">Now when the project is built, the linker will call pgomgr.exe to merge any `<PGDName>!*.pgc` files into the .pgd with the default weight of 1, and the resulting application will be optimized based on the profiling data.</span></span>

## <a name="see-also"></a><span data-ttu-id="83929-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="83929-145">See also</span></span>
- [<span data-ttu-id="83929-146">Leistung</span><span class="sxs-lookup"><span data-stu-id="83929-146">Performance</span></span>](performance-and-xaml-ui.md)

 

