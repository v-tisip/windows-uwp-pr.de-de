---
author: normesta
Description: This guide explains how to configure your Visual Studio Solution to edit, debug, and package desktop app for the Desktop Bridge.
Search.Product: eADQiWindows 10XVcnh
title: Verpacken einer App mit Visual Studio (Desktop-Brücke)
ms.author: normesta
ms.date: 08/30/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 807a99a7-d285-46e7-af6a-7214da908907
ms.localizationpriority: medium
ms.openlocfilehash: d7ae77c499cb8398aa5557f0d422899fbe8b252d
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816255"
---
# <a name="package-an-app-by-using-visual-studio-desktop-bridge"></a><span data-ttu-id="7adca-103">Verpacken einer App mit Visual Studio (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="7adca-103">Package an app by using Visual Studio (Desktop Bridge)</span></span>

<span data-ttu-id="7adca-104">Sie können Visual Studio verwenden, um ein Paket für Ihre Desktop-App zu generieren.</span><span class="sxs-lookup"><span data-stu-id="7adca-104">You can use Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="7adca-105">Anschließend können Sie das Paket im Windows Store veröffentlichen oder es auf einem oder mehreren PCs querladen.</span><span class="sxs-lookup"><span data-stu-id="7adca-105">Then, you can publish that package to the Windows store or sideload it onto one or more PCs.</span></span>

<span data-ttu-id="7adca-106">Die aktuelle Version von Visual Studio bietet ein neue Version des Paketprojekts, um manuelle Schritte zu eliminieren, die beim Verpacken Ihrer App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="7adca-106">The latest version of Visual Studio provides a new version of the packaging project that eliminates all of the manual steps that used to be necessary to package your app.</span></span> <span data-ttu-id="7adca-107">Sie müssen nur Ihr Paketprojekt hinzufügen, auf das Desktopprojekt verweisen und F5 drücken, um Ihre App zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="7adca-107">Just add a packaging project, reference your desktop project, and then press F5 to debug your app.</span></span> <span data-ttu-id="7adca-108">Es sind keine manuellen Optimierungsmethoden mehr erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7adca-108">No manual tweaks necessary.</span></span> <span data-ttu-id="7adca-109">Das neue optimierte Design ist eine enorme Verbesserung über die Benutzeroberfläche, die in der vorherigen Version von Visual Studio verfügbar war.</span><span class="sxs-lookup"><span data-stu-id="7adca-109">This new streamlined experience is a vast improvement over the experience that was available in the previous version of Visual Studio.</span></span>

>[!IMPORTANT]
><span data-ttu-id="7adca-110">Der Desktop-Brücke wurde in Windows10, Version 1607, eingeführt und kann nur in Projekten für das Windows10 Anniversary Update (10.0; Build 14393) oder einer neueren Version in Visual Studio verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7adca-110">The Desktop Bridge was introduced in Windows 10, version 1607, and it can only be used in projects that target Windows 10 Anniversary Update (10.0; Build 14393) or a later release in Visual Studio.</span></span>

## <a name="first-consider-how-youll-distribute-your-app"></a><span data-ttu-id="7adca-111">Überlegen Sie zunächst, wie Sie Ihre App verteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="7adca-111">First, consider how you'll distribute your app</span></span>

<span data-ttu-id="7adca-112">Wenn Sie Ihre App im [Microsoft Store](https://www.microsoft.com/store/apps) veröffentlichen möchten, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="7adca-112">If you plan to publish your app to the [Microsoft Store](https://www.microsoft.com/store/apps), start by filling out [this form](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span></span> <span data-ttu-id="7adca-113">Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess.</span><span class="sxs-lookup"><span data-stu-id="7adca-113">Microsoft will contact you to start the onboarding process.</span></span> <span data-ttu-id="7adca-114">Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um Ihre App zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="7adca-114">As part of this process, you'll reserve a name in the store, and obtain information that you'll need to package your app.</span></span>

<span data-ttu-id="7adca-115">Lesen Sie außerdem unbedingt dieses Handbuch lesen, bevor Sie mit der Paketerstellung für Ihre Anwendung beginnen: [Vorbereiten der Verpackung einer App (Desktop-Brücke)](desktop-to-uwp-prepare.md).</span><span class="sxs-lookup"><span data-stu-id="7adca-115">Also, make sure to review this guide before you begin creating a package for your application: [Prepare to package an app (Desktop Bridge)](desktop-to-uwp-prepare.md).</span></span>

<a id="new-packaging-project"/>

## <a name="create-a-package"></a><span data-ttu-id="7adca-116">Erstellen eines Pakets</span><span class="sxs-lookup"><span data-stu-id="7adca-116">Create a package</span></span>

1. <span data-ttu-id="7adca-117">Öffnen Sie in Visual Studio die Lösung mit Ihrem Desktopanwendungsprojekt.</span><span class="sxs-lookup"><span data-stu-id="7adca-117">In Visual Studio, open the solution that contains your desktop application project.</span></span>

2. <span data-ttu-id="7adca-118">Fügen Sie der Projektmappe ein Projekt **Paketerstellungsprojekt für Windows-Anwendungen** hinzu.</span><span class="sxs-lookup"><span data-stu-id="7adca-118">Add a **Windows Application Packaging Project** project to your solution.</span></span>

   <span data-ttu-id="7adca-119">Sie müssen keinen Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7adca-119">You won't have to add any code to it.</span></span> <span data-ttu-id="7adca-120">Es dient nur, um ein Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="7adca-120">It's just there to generate a package for you.</span></span> <span data-ttu-id="7adca-121">Wir nennen das Projekt „Paketprojekt“.</span><span class="sxs-lookup"><span data-stu-id="7adca-121">We'll refer to this project as the "packaging project".</span></span>

   ![Paketprojekt](images/desktop-to-uwp/packaging-project.png)

   >[!NOTE]
   ><span data-ttu-id="7adca-123">Dieses Projekt wird nur in Visual Studio2017 ab Version 15.5 oder höher angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7adca-123">This project appears only in Visual Studio 2017 version 15.5 or higher.</span></span>

3. <span data-ttu-id="7adca-124">Legen Sie die **Zielversion** des Projekts auf eine beliebige Version fest, stellen Sie jedoch sicher, dass die **Mindestens erforderliche Version** auf **Windows10 Anniversary Update** eingestellt ist.</span><span class="sxs-lookup"><span data-stu-id="7adca-124">Set the **Target Version** of this project to any version that you want, but make sure to set the **Minimum Version** to **Windows 10 Anniversary Update**.</span></span>

   ![Das Dialogfeld zur Auswahl der Paketversion](images/desktop-to-uwp/packaging-version.png)

4. <span data-ttu-id="7adca-126">Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="7adca-126">In the packaging project, right-click the **Applications** folder, and then choose **Add Reference**.</span></span>

   ![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-project-reference.png)

5. <span data-ttu-id="7adca-128">Wählen Sie Ihr Desktopanwendungsprojekt aus, und klicken Sie dann auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="7adca-128">Choose your desktop application project, and then choose the **OK** button.</span></span>

   ![Desktopprojekt](images/desktop-to-uwp/reference-project.png)

   <span data-ttu-id="7adca-130">Sie können mehrere Desktopanwendungen im Paket miteinbeziehen, aber nur eines kann gestartet werden, wenn Benutzer Ihre App-Kachel auswählen.</span><span class="sxs-lookup"><span data-stu-id="7adca-130">You can include multiple desktop applications in your package, but only one of them can start when users choose your app tile.</span></span> <span data-ttu-id="7adca-131">Klicken Sie mit der rechten Maustaste im Knoten **Anwendungen** auf die Anwendung, die die Benutzer starten sollen, wenn sie die App-Kachel auswählen, und wählen Sie dann **Als Einstiegspunkt festlegen** aus.</span><span class="sxs-lookup"><span data-stu-id="7adca-131">In the **Applications** node, right-click the application that you want users to start when they choose the app's tile, and then choose **Set as Entry Point**.</span></span>

   ![Als Einstiegspunkt festlegen](images/desktop-to-uwp/entry-point-set.png)

6. <span data-ttu-id="7adca-133">Erstellen Sie das Paketprojekt, um sicherzustellen, dass keine Fehler angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7adca-133">Build the packaging project to ensure that no errors appear.</span></span>

7. <span data-ttu-id="7adca-134">Verwenden Sie den Assistenten [App-Pakete erstellen](../packaging/packaging-uwp-apps.md), um eine appxupload-Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7adca-134">Use the [Create App Packages](../packaging/packaging-uwp-apps.md) wizard to generate an appxupload file.</span></span>

   <span data-ttu-id="7adca-135">Sie können diese Datei direkt in den Store hochladen.</span><span class="sxs-lookup"><span data-stu-id="7adca-135">You can upload that file directly to the store.</span></span>

**<span data-ttu-id="7adca-136">Video</span><span class="sxs-lookup"><span data-stu-id="7adca-136">Video</span></span>**

<iframe src="https://www.youtube.com/embed/fJkbYPyd08w" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a><span data-ttu-id="7adca-137">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="7adca-137">Next steps</span></span>

**<span data-ttu-id="7adca-138">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="7adca-138">Find answers to your questions</span></span>**

<span data-ttu-id="7adca-139">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="7adca-139">Have questions?</span></span> <span data-ttu-id="7adca-140">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="7adca-140">Ask us on Stack Overflow.</span></span> <span data-ttu-id="7adca-141">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="7adca-141">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="7adca-142">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="7adca-142">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="7adca-143">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="7adca-143">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="7adca-144">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="7adca-144">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>

**<span data-ttu-id="7adca-145">Ausführen, Debuggen oder Testen der App</span><span class="sxs-lookup"><span data-stu-id="7adca-145">Run, debug or test your app</span></span>**

<span data-ttu-id="7adca-146">Siehe [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md)</span><span class="sxs-lookup"><span data-stu-id="7adca-146">See [Run, debug, and test a packaged desktop app (Desktop Bridge)](desktop-to-uwp-debug.md)</span></span>

**<span data-ttu-id="7adca-147">Verbessern Sie Ihre Desktop-App durch Hinzufügen von UWP-APIs</span><span class="sxs-lookup"><span data-stu-id="7adca-147">Enhance your desktop app by adding UWP APIs</span></span>**

<span data-ttu-id="7adca-148">Siehe [Verbessern Sie Ihre Desktopanwendung für Windows10](desktop-to-uwp-enhance.md)</span><span class="sxs-lookup"><span data-stu-id="7adca-148">See [Enhance your desktop application for Windows 10](desktop-to-uwp-enhance.md)</span></span>

**<span data-ttu-id="7adca-149">Erweitern der Desktop-App durch Hinzufügen von UWP-Projekten und Komponenten für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="7adca-149">Extend your desktop app by adding UWP projects and Windows Runtime Components</span></span>**

<span data-ttu-id="7adca-150">Weitere Informationen finden Sie unter [Erweitern Ihrer Desktopanwendung mit modernen UWP-Komponenten](desktop-to-uwp-extend.md).</span><span class="sxs-lookup"><span data-stu-id="7adca-150">See [Extend your desktop application with modern UWP components](desktop-to-uwp-extend.md).</span></span>

**<span data-ttu-id="7adca-151">Verteilen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="7adca-151">Distribute your app</span></span>**

<span data-ttu-id="7adca-152">Weitere Informationen finden Sie in [Verteilen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)</span><span class="sxs-lookup"><span data-stu-id="7adca-152">See [Distribute a packaged desktop app (Desktop Bridge)](desktop-to-uwp-distribute.md)</span></span>
