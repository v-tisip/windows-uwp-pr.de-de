---
author: normesta
Description: This guide explains how to configure your Visual Studio Solution to edit, debug, and package desktop application.
Search.Product: eADQiWindows 10XVcnh
title: Verpacken Sie eine desktop-Anwendung mit Visual Studio
ms.author: normesta
ms.date: 08/30/2017
ms.topic: article
keywords: windows10, UWP
ms.assetid: 807a99a7-d285-46e7-af6a-7214da908907
ms.localizationpriority: medium
ms.openlocfilehash: cc71a58594c8794369bedd7f415518100892ff67
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6970574"
---
# <a name="package-a-desktop-application-by-using-visual-studio"></a><span data-ttu-id="02ff2-103">Verpacken Sie eine desktop-Anwendung mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="02ff2-103">Package a desktop application by using Visual Studio</span></span>

<span data-ttu-id="02ff2-104">Sie können Visual Studio verwenden, um ein Paket für Ihre Desktop-App zu generieren.</span><span class="sxs-lookup"><span data-stu-id="02ff2-104">You can use Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="02ff2-105">Anschließend können Sie veröffentlichen, die auf den Microsoft Store oder querladen es auf einem oder mehreren PCs verpacken.</span><span class="sxs-lookup"><span data-stu-id="02ff2-105">Then, you can publish that package to the Microsoft Store or sideload it onto one or more PCs.</span></span>

<span data-ttu-id="02ff2-106">Die aktuelle Version von Visual Studio bietet ein neue Version des Paketprojekts, um manuelle Schritte zu eliminieren, die beim Verpacken Ihrer App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="02ff2-106">The latest version of Visual Studio provides a new version of the packaging project that eliminates all of the manual steps that used to be necessary to package your app.</span></span> <span data-ttu-id="02ff2-107">Sie müssen nur Ihr Paketprojekt hinzufügen, auf das Desktopprojekt verweisen und F5 drücken, um Ihre App zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="02ff2-107">Just add a packaging project, reference your desktop project, and then press F5 to debug your app.</span></span> <span data-ttu-id="02ff2-108">Es sind keine manuellen Optimierungsmethoden mehr erforderlich.</span><span class="sxs-lookup"><span data-stu-id="02ff2-108">No manual tweaks necessary.</span></span> <span data-ttu-id="02ff2-109">Das neue optimierte Design ist eine enorme Verbesserung über die Benutzeroberfläche, die in der vorherigen Version von Visual Studio verfügbar war.</span><span class="sxs-lookup"><span data-stu-id="02ff2-109">This new streamlined experience is a vast improvement over the experience that was available in the previous version of Visual Studio.</span></span>

>[!IMPORTANT]
><span data-ttu-id="02ff2-110">Die Fähigkeit zum Erstellen eines Windows-app-Pakets für Ihre desktop-Anwendung (auch bekannt als der Desktop-Brücke) wurde in Windows 10, Version 1607, eingeführt und kann nur in Projekten für die Windows 10 Anniversary Update (10.0; verwendet werden Build 14393) oder einer neueren Version in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="02ff2-110">The ability to create a Windows app package for your desktop application (otherwise known as the Desktop Bridge) was introduced in Windows 10, version 1607, and it can only be used in projects that target Windows 10 Anniversary Update (10.0; Build 14393) or a later release in Visual Studio.</span></span>

## <a name="first-prepare-your-application"></a><span data-ttu-id="02ff2-111">Vorbereiten Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="02ff2-111">First, prepare your application</span></span>

<span data-ttu-id="02ff2-112">Lesen Sie dieses Handbuch, bevor Sie mit der paketerstellung für Ihre Anwendung beginnen: [Vorbereiten eine desktop-Anwendung zu verpacken](desktop-to-uwp-prepare.md).</span><span class="sxs-lookup"><span data-stu-id="02ff2-112">Review this guide before you begin creating a package for your application: [Prepare to package a desktop application](desktop-to-uwp-prepare.md).</span></span>

<a id="new-packaging-project"/>

## <a name="create-a-package"></a><span data-ttu-id="02ff2-113">Erstellen eines Pakets</span><span class="sxs-lookup"><span data-stu-id="02ff2-113">Create a package</span></span>

1. <span data-ttu-id="02ff2-114">Öffnen Sie in Visual Studio die Lösung mit Ihrem Desktopanwendungsprojekt.</span><span class="sxs-lookup"><span data-stu-id="02ff2-114">In Visual Studio, open the solution that contains your desktop application project.</span></span>

2. <span data-ttu-id="02ff2-115">Fügen Sie der Projektmappe ein Projekt **Paketerstellungsprojekt für Windows-Anwendungen** hinzu.</span><span class="sxs-lookup"><span data-stu-id="02ff2-115">Add a **Windows Application Packaging Project** project to your solution.</span></span>

   <span data-ttu-id="02ff2-116">Sie müssen keinen Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="02ff2-116">You won't have to add any code to it.</span></span> <span data-ttu-id="02ff2-117">Es dient nur, um ein Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="02ff2-117">It's just there to generate a package for you.</span></span> <span data-ttu-id="02ff2-118">Wir nennen das Projekt „Paketprojekt“.</span><span class="sxs-lookup"><span data-stu-id="02ff2-118">We'll refer to this project as the "packaging project".</span></span>

   ![Paketprojekt](images/desktop-to-uwp/packaging-project.png)

   >[!NOTE]
   ><span data-ttu-id="02ff2-120">Dieses Projekt wird nur in Visual Studio2017 ab Version 15.5 oder höher angezeigt.</span><span class="sxs-lookup"><span data-stu-id="02ff2-120">This project appears only in Visual Studio 2017 version 15.5 or higher.</span></span>

3. <span data-ttu-id="02ff2-121">Legen Sie die **Zielversion** des Projekts auf eine beliebige Version fest, stellen Sie jedoch sicher, dass die **Mindestens erforderliche Version** auf **Windows10 Anniversary Update** eingestellt ist.</span><span class="sxs-lookup"><span data-stu-id="02ff2-121">Set the **Target Version** of this project to any version that you want, but make sure to set the **Minimum Version** to **Windows 10 Anniversary Update**.</span></span>

   ![Das Dialogfeld zur Auswahl der Paketversion](images/desktop-to-uwp/packaging-version.png)

4. <span data-ttu-id="02ff2-123">Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="02ff2-123">In the packaging project, right-click the **Applications** folder, and then choose **Add Reference**.</span></span>

   ![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-project-reference.png)

5. <span data-ttu-id="02ff2-125">Wählen Sie Ihr Desktopanwendungsprojekt aus, und klicken Sie dann auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ff2-125">Choose your desktop application project, and then choose the **OK** button.</span></span>

   ![Desktopprojekt](images/desktop-to-uwp/reference-project.png)

   <span data-ttu-id="02ff2-127">Sie können mehrere Desktopanwendungen im Paket miteinbeziehen, aber nur eines kann gestartet werden, wenn Benutzer Ihre App-Kachel auswählen.</span><span class="sxs-lookup"><span data-stu-id="02ff2-127">You can include multiple desktop applications in your package, but only one of them can start when users choose your app tile.</span></span> <span data-ttu-id="02ff2-128">Klicken Sie mit der rechten Maustaste im Knoten **Anwendungen** auf die Anwendung, die die Benutzer starten sollen, wenn sie die App-Kachel auswählen, und wählen Sie dann **Als Einstiegspunkt festlegen** aus.</span><span class="sxs-lookup"><span data-stu-id="02ff2-128">In the **Applications** node, right-click the application that you want users to start when they choose the app's tile, and then choose **Set as Entry Point**.</span></span>

   ![Als Einstiegspunkt festlegen](images/desktop-to-uwp/entry-point-set.png)

6. <span data-ttu-id="02ff2-130">Erstellen Sie das Paketprojekt, um sicherzustellen, dass keine Fehler angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="02ff2-130">Build the packaging project to ensure that no errors appear.</span></span>  <span data-ttu-id="02ff2-131">Wenn Sie Fehler zu erhalten, öffnen Sie den **Konfigurations-Manager** , und stellen, dass sicher Plattform Ihre Projekte dieselbe.</span><span class="sxs-lookup"><span data-stu-id="02ff2-131">If you receive errors, open **Configuration Manager** and ensure that your projects target the same platform.</span></span>

   ![Konfigurations-manager](images/desktop-to-uwp/config-manager.png)

7. <span data-ttu-id="02ff2-133">Verwenden Sie den Assistenten [App-Pakete erstellen](../packaging/packaging-uwp-apps.md), um eine appxupload-Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="02ff2-133">Use the [Create App Packages](../packaging/packaging-uwp-apps.md) wizard to generate an appxupload file.</span></span>

   <span data-ttu-id="02ff2-134">Sie können diese Datei direkt an den Store hochladen.</span><span class="sxs-lookup"><span data-stu-id="02ff2-134">You can upload that file directly to the Store.</span></span>

**<span data-ttu-id="02ff2-135">Video</span><span class="sxs-lookup"><span data-stu-id="02ff2-135">Video</span></span>**

&nbsp;
> [!VIDEO https://www.youtube.com/embed/fJkbYPyd08w]

## <a name="next-steps"></a><span data-ttu-id="02ff2-136">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="02ff2-136">Next steps</span></span>

**<span data-ttu-id="02ff2-137">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="02ff2-137">Find answers to your questions</span></span>**

<span data-ttu-id="02ff2-138">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="02ff2-138">Have questions?</span></span> <span data-ttu-id="02ff2-139">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="02ff2-139">Ask us on Stack Overflow.</span></span> <span data-ttu-id="02ff2-140">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="02ff2-140">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="02ff2-141">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="02ff2-141">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="02ff2-142">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="02ff2-142">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="02ff2-143">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="02ff2-143">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>

**<span data-ttu-id="02ff2-144">Führen Sie aus, Debuggen Sie oder testen Sie Ihre desktop-Anwendung</span><span class="sxs-lookup"><span data-stu-id="02ff2-144">Run, debug or test your desktop application</span></span>**

<span data-ttu-id="02ff2-145">Finden Sie unter [ausführen, Debuggen und testen eine verpackte desktop-Anwendung](desktop-to-uwp-debug.md)</span><span class="sxs-lookup"><span data-stu-id="02ff2-145">See [Run, debug, and test a packaged desktop application](desktop-to-uwp-debug.md)</span></span>

**<span data-ttu-id="02ff2-146">Verbessern Sie Ihre desktop-Anwendung durch Hinzufügen von UWP-APIs</span><span class="sxs-lookup"><span data-stu-id="02ff2-146">Enhance your desktop application by adding UWP APIs</span></span>**

<span data-ttu-id="02ff2-147">Siehe [Verbessern Sie Ihre Desktopanwendung für Windows10](desktop-to-uwp-enhance.md)</span><span class="sxs-lookup"><span data-stu-id="02ff2-147">See [Enhance your desktop application for Windows 10](desktop-to-uwp-enhance.md)</span></span>

**<span data-ttu-id="02ff2-148">Erweitern Sie Ihre desktop-Anwendung durch Hinzufügen von UWP-Projekten und Komponenten für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="02ff2-148">Extend your desktop application by adding UWP projects and Windows Runtime Components</span></span>**

<span data-ttu-id="02ff2-149">Weitere Informationen finden Sie unter [Erweitern Ihrer Desktopanwendung mit modernen UWP-Komponenten](desktop-to-uwp-extend.md).</span><span class="sxs-lookup"><span data-stu-id="02ff2-149">See [Extend your desktop application with modern UWP components](desktop-to-uwp-extend.md).</span></span>

**<span data-ttu-id="02ff2-150">Verteilen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="02ff2-150">Distribute your app</span></span>**

<span data-ttu-id="02ff2-151">Finden Sie unter [Verteilen einer verpackten desktop-Anwendung](desktop-to-uwp-distribute.md)</span><span class="sxs-lookup"><span data-stu-id="02ff2-151">See [Distribute a packaged desktop application](desktop-to-uwp-distribute.md)</span></span>
