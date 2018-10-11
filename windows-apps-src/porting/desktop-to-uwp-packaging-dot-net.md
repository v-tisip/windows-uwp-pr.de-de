---
author: normesta
Description: This guide explains how to configure your Visual Studio Solution to edit, debug, and package desktop application.
Search.Product: eADQiWindows 10XVcnh
title: Verpacken einer desktop-Anwendungs mit Visual Studio
ms.author: normesta
ms.date: 08/30/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 807a99a7-d285-46e7-af6a-7214da908907
ms.localizationpriority: medium
ms.openlocfilehash: 2c9b7a30a50c26d2dbdaf6df04e85549addaf181
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4535652"
---
# <a name="package-a-desktop-application-by-using-visual-studio"></a><span data-ttu-id="b01ae-103">Verpacken einer desktop-Anwendungs mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b01ae-103">Package a desktop application by using Visual Studio</span></span>

<span data-ttu-id="b01ae-104">Sie können Visual Studio verwenden, um ein Paket für Ihre Desktop-App zu generieren.</span><span class="sxs-lookup"><span data-stu-id="b01ae-104">You can use Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="b01ae-105">Anschließend können Sie das Paket im Windows Store veröffentlichen oder es auf einem oder mehreren PCs querladen.</span><span class="sxs-lookup"><span data-stu-id="b01ae-105">Then, you can publish that package to the Windows store or sideload it onto one or more PCs.</span></span>

<span data-ttu-id="b01ae-106">Die aktuelle Version von Visual Studio bietet ein neue Version des Paketprojekts, um manuelle Schritte zu eliminieren, die beim Verpacken Ihrer App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="b01ae-106">The latest version of Visual Studio provides a new version of the packaging project that eliminates all of the manual steps that used to be necessary to package your app.</span></span> <span data-ttu-id="b01ae-107">Sie müssen nur Ihr Paketprojekt hinzufügen, auf das Desktopprojekt verweisen und F5 drücken, um Ihre App zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="b01ae-107">Just add a packaging project, reference your desktop project, and then press F5 to debug your app.</span></span> <span data-ttu-id="b01ae-108">Es sind keine manuellen Optimierungsmethoden mehr erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b01ae-108">No manual tweaks necessary.</span></span> <span data-ttu-id="b01ae-109">Das neue optimierte Design ist eine enorme Verbesserung über die Benutzeroberfläche, die in der vorherigen Version von Visual Studio verfügbar war.</span><span class="sxs-lookup"><span data-stu-id="b01ae-109">This new streamlined experience is a vast improvement over the experience that was available in the previous version of Visual Studio.</span></span>

>[!IMPORTANT]
><span data-ttu-id="b01ae-110">Die Fähigkeit zum Erstellen einer Windows-app-Paket für Ihre desktop-Anwendung (andernfalls wird auch als der Desktop-Brücke wurde in Windows 10, Version 1607, eingeführt und kann nur in Projekten für die Windows 10 Anniversary Update (10.0; verwendet werden Build 14393) oder einer neueren Version in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b01ae-110">The ability to create a Windows app package for your desktop application (Otherwise known as the Desktop Bridge, was introduced in Windows 10, version 1607, and it can only be used in projects that target Windows 10 Anniversary Update (10.0; Build 14393) or a later release in Visual Studio.</span></span>

## <a name="first-prepare-your-application"></a><span data-ttu-id="b01ae-111">Vorbereiten Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="b01ae-111">First, prepare your application</span></span>

<span data-ttu-id="b01ae-112">Dieses Handbuch lesen, bevor Sie mit der paketerstellung für Ihre Anwendung beginnen: [Vorbereiten eine desktop-Anwendung zu verpacken](desktop-to-uwp-prepare.md).</span><span class="sxs-lookup"><span data-stu-id="b01ae-112">Review this guide before you begin creating a package for your application: [Prepare to package a desktop application](desktop-to-uwp-prepare.md).</span></span>

<a id="new-packaging-project"/>

## <a name="create-a-package"></a><span data-ttu-id="b01ae-113">Erstellen eines Pakets</span><span class="sxs-lookup"><span data-stu-id="b01ae-113">Create a package</span></span>

1. <span data-ttu-id="b01ae-114">Öffnen Sie in Visual Studio die Lösung mit Ihrem Desktopanwendungsprojekt.</span><span class="sxs-lookup"><span data-stu-id="b01ae-114">In Visual Studio, open the solution that contains your desktop application project.</span></span>

2. <span data-ttu-id="b01ae-115">Fügen Sie der Projektmappe ein Projekt **Paketerstellungsprojekt für Windows-Anwendungen** hinzu.</span><span class="sxs-lookup"><span data-stu-id="b01ae-115">Add a **Windows Application Packaging Project** project to your solution.</span></span>

   <span data-ttu-id="b01ae-116">Sie müssen keinen Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b01ae-116">You won't have to add any code to it.</span></span> <span data-ttu-id="b01ae-117">Es dient nur, um ein Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="b01ae-117">It's just there to generate a package for you.</span></span> <span data-ttu-id="b01ae-118">Wir nennen das Projekt „Paketprojekt“.</span><span class="sxs-lookup"><span data-stu-id="b01ae-118">We'll refer to this project as the "packaging project".</span></span>

   ![Paketprojekt](images/desktop-to-uwp/packaging-project.png)

   >[!NOTE]
   ><span data-ttu-id="b01ae-120">Dieses Projekt wird nur in Visual Studio2017 ab Version 15.5 oder höher angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b01ae-120">This project appears only in Visual Studio 2017 version 15.5 or higher.</span></span>

3. <span data-ttu-id="b01ae-121">Legen Sie die **Zielversion** des Projekts auf eine beliebige Version fest, stellen Sie jedoch sicher, dass die **Mindestens erforderliche Version** auf **Windows10 Anniversary Update** eingestellt ist.</span><span class="sxs-lookup"><span data-stu-id="b01ae-121">Set the **Target Version** of this project to any version that you want, but make sure to set the **Minimum Version** to **Windows 10 Anniversary Update**.</span></span>

   ![Das Dialogfeld zur Auswahl der Paketversion](images/desktop-to-uwp/packaging-version.png)

4. <span data-ttu-id="b01ae-123">Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="b01ae-123">In the packaging project, right-click the **Applications** folder, and then choose **Add Reference**.</span></span>

   ![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-project-reference.png)

5. <span data-ttu-id="b01ae-125">Wählen Sie Ihr Desktopanwendungsprojekt aus, und klicken Sie dann auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="b01ae-125">Choose your desktop application project, and then choose the **OK** button.</span></span>

   ![Desktopprojekt](images/desktop-to-uwp/reference-project.png)

   <span data-ttu-id="b01ae-127">Sie können mehrere Desktopanwendungen im Paket miteinbeziehen, aber nur eines kann gestartet werden, wenn Benutzer Ihre App-Kachel auswählen.</span><span class="sxs-lookup"><span data-stu-id="b01ae-127">You can include multiple desktop applications in your package, but only one of them can start when users choose your app tile.</span></span> <span data-ttu-id="b01ae-128">Klicken Sie mit der rechten Maustaste im Knoten **Anwendungen** auf die Anwendung, die die Benutzer starten sollen, wenn sie die App-Kachel auswählen, und wählen Sie dann **Als Einstiegspunkt festlegen** aus.</span><span class="sxs-lookup"><span data-stu-id="b01ae-128">In the **Applications** node, right-click the application that you want users to start when they choose the app's tile, and then choose **Set as Entry Point**.</span></span>

   ![Als Einstiegspunkt festlegen](images/desktop-to-uwp/entry-point-set.png)

6. <span data-ttu-id="b01ae-130">Erstellen Sie das Paketprojekt, um sicherzustellen, dass keine Fehler angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b01ae-130">Build the packaging project to ensure that no errors appear.</span></span>

7. <span data-ttu-id="b01ae-131">Verwenden Sie den Assistenten [App-Pakete erstellen](../packaging/packaging-uwp-apps.md), um eine appxupload-Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b01ae-131">Use the [Create App Packages](../packaging/packaging-uwp-apps.md) wizard to generate an appxupload file.</span></span>

   <span data-ttu-id="b01ae-132">Sie können diese Datei direkt in den Store hochladen.</span><span class="sxs-lookup"><span data-stu-id="b01ae-132">You can upload that file directly to the store.</span></span>

**<span data-ttu-id="b01ae-133">Video</span><span class="sxs-lookup"><span data-stu-id="b01ae-133">Video</span></span>**

&nbsp;
> [!VIDEO https://www.youtube.com/embed/fJkbYPyd08w]

## <a name="next-steps"></a><span data-ttu-id="b01ae-134">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b01ae-134">Next steps</span></span>

**<span data-ttu-id="b01ae-135">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="b01ae-135">Find answers to your questions</span></span>**

<span data-ttu-id="b01ae-136">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="b01ae-136">Have questions?</span></span> <span data-ttu-id="b01ae-137">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="b01ae-137">Ask us on Stack Overflow.</span></span> <span data-ttu-id="b01ae-138">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="b01ae-138">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="b01ae-139">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="b01ae-139">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="b01ae-140">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="b01ae-140">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="b01ae-141">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="b01ae-141">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>

**<span data-ttu-id="b01ae-142">Führen Sie aus, Debuggen Sie oder testen Sie Ihre desktop-Anwendung</span><span class="sxs-lookup"><span data-stu-id="b01ae-142">Run, debug or test your desktop application</span></span>**

<span data-ttu-id="b01ae-143">Finden Sie unter [ausführen, Debuggen und testen eine verpackte desktop-Anwendung](desktop-to-uwp-debug.md)</span><span class="sxs-lookup"><span data-stu-id="b01ae-143">See [Run, debug, and test a packaged desktop application](desktop-to-uwp-debug.md)</span></span>

**<span data-ttu-id="b01ae-144">Verbessern Sie Ihre desktop-Anwendung durch Hinzufügen von UWP-APIs</span><span class="sxs-lookup"><span data-stu-id="b01ae-144">Enhance your desktop application by adding UWP APIs</span></span>**

<span data-ttu-id="b01ae-145">Siehe [Verbessern Sie Ihre Desktopanwendung für Windows10](desktop-to-uwp-enhance.md)</span><span class="sxs-lookup"><span data-stu-id="b01ae-145">See [Enhance your desktop application for Windows 10](desktop-to-uwp-enhance.md)</span></span>

**<span data-ttu-id="b01ae-146">Erweitern Sie Ihre desktop-Anwendung durch Hinzufügen von UWP-Projekten und Komponenten für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="b01ae-146">Extend your desktop application by adding UWP projects and Windows Runtime Components</span></span>**

<span data-ttu-id="b01ae-147">Weitere Informationen finden Sie unter [Erweitern Ihrer Desktopanwendung mit modernen UWP-Komponenten](desktop-to-uwp-extend.md).</span><span class="sxs-lookup"><span data-stu-id="b01ae-147">See [Extend your desktop application with modern UWP components](desktop-to-uwp-extend.md).</span></span>

**<span data-ttu-id="b01ae-148">Verteilen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="b01ae-148">Distribute your app</span></span>**

<span data-ttu-id="b01ae-149">Finden Sie unter [Verteilen einer verpackten desktop-Anwendung](desktop-to-uwp-distribute.md)</span><span class="sxs-lookup"><span data-stu-id="b01ae-149">See [Distribute a packaged desktop application](desktop-to-uwp-distribute.md)</span></span>
