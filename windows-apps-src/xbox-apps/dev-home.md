---
author: v-angraf
ms.assetid: a56156e4-7adb-bf37-527b-fc3243e04b46
title: Entwickler-Startbildschirm auf der Konsole (Dev Home)
description: Enthält Informationen zu Dev Home-app für Xbox One.
ms.author: v-angraf@microsoft.com
ms.date: 08/09/2017
ms.topic: article
keywords: Windows10, UWP
permalink: en-us/docs/xdk/dev-home.html
ms.localizationpriority: medium
ms.openlocfilehash: 232770ab4b746663a105982605d1cedcb92adbe3
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5706743"
---
# <a name="developer-home-on-the-console-dev-home"></a><span data-ttu-id="a0e99-104">Entwickler-Startbildschirm auf der Konsole (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="a0e99-104">Developer Home on the Console (Dev Home)</span></span>
   
  
<span data-ttu-id="a0e99-105">Dev Home ist ein Tool im Xbox One Development Kit entwickelt, um die Produktivität von Entwicklern unterstützen soll.</span><span class="sxs-lookup"><span data-stu-id="a0e99-105">Dev Home is a tools experience on the Xbox One development kit designed to aid developer productivity.</span></span> <span data-ttu-id="a0e99-106">Dev Home bietet Funktionen zum Verwalten und Konfigurieren Ihres Development Kit, Verwalten von Benutzern, starten installierten Titel und durchführen erfasst und erfasst.</span><span class="sxs-lookup"><span data-stu-id="a0e99-106">Dev Home offers functionality to manage and configure your development kit, manage users, launch installed titles and perform captures and traces.</span></span> <span data-ttu-id="a0e99-107">In zukünftigen Versionen, die wir erweitern Sie die Funktionalität weiterhin, um zusätzliche Features basierend auf Ihr Feedback zu aktivieren, und auch Erweiterbarkeit und das Hinzufügen von eigene Tools aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a0e99-107">In future releases we will continue to expand the functionality to enable additional features based on your feedback, and also to enable extensibility and the addition of your own tools.</span></span>   
   
  
<span data-ttu-id="a0e99-108">Wir sind Ihr Feedback zu Dev Home und die Szenarien, die Sie sehen sie unterstützen die meisten interessiert sind sehr interessiert.</span><span class="sxs-lookup"><span data-stu-id="a0e99-108">We are very interested in your feedback on Dev Home and the scenarios you are most interested in seeing it support.</span></span> <span data-ttu-id="a0e99-109">Geben Sie Ihre Kommentare über das Menü der app unter **Feedback senden** beschriebenen Methoden oder über Ihre Entwickler Account Manager (Mutter).</span><span class="sxs-lookup"><span data-stu-id="a0e99-109">Please provide your comments through the methods described under **Send Feedback** in the main menu of the app or through your Developer Account Manager (DAM).</span></span>   
   
  
<span data-ttu-id="a0e99-110">So starten Sie Dev Home auf der November 2015 oder höher Wiederherstellung</span><span class="sxs-lookup"><span data-stu-id="a0e99-110">To launch Dev Home on the November 2015 or later recovery:</span></span>  
 
   1. <span data-ttu-id="a0e99-111">Öffnen Sie die Anleitung durch Verschieben nach links auf der Startseite oder klicken auf die Schaltfläche Nexus double</span><span class="sxs-lookup"><span data-stu-id="a0e99-111">Open the guide by moving left on Home, or double clicking the Nexus button</span></span>  
   1. <span data-ttu-id="a0e99-112">Nach unten, um **Einstellungen** (das Zahnradsymbol)</span><span class="sxs-lookup"><span data-stu-id="a0e99-112">Move down to **Settings** (the gear icon)</span></span>   
   1. <span data-ttu-id="a0e99-113">Wählen Sie **Alle Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="a0e99-113">Select **All settings**</span></span>  
   1. <span data-ttu-id="a0e99-114">Wählen Sie auf **der Standard-Entwicklerseite** **Entwickler-Startbildschirm** (das Symbol für die Startseite)</span><span class="sxs-lookup"><span data-stu-id="a0e99-114">From the default **Developer** page, select **Developer Home** (the home icon)</span></span>   

 ![](images/dev_home_icons.png)   
  
<span data-ttu-id="a0e99-115">Zeigen Sie auf früheren Recovery wählen Sie die Kachel "Dev Home" auf rechts neben dem Startbildschirm aus im **Inhalt funktionsfähigen** oder die Anwendungsliste im Xbox One-Manager und starten Sie **Dev Home**.</span><span class="sxs-lookup"><span data-stu-id="a0e99-115">On earlier recoveries select the Dev Home tile on the right side of the home screen in **featured content** or view the application list in Xbox One Manager and launch **Dev Home**.</span></span>   
 ![](images/dev_home_1.png) 
<a id="ID4EBC"></a>

   

## <a name="user-interface"></a><span data-ttu-id="a0e99-116">Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="a0e99-116">User Interface</span></span>  
   
  
<span data-ttu-id="a0e99-117">Der Header der Dev Home-Benutzeroberfläche enthält die folgenden "auf einen Blick" wichtige Informationen zu den entwicklungskonsole:</span><span class="sxs-lookup"><span data-stu-id="a0e99-117">The header of the Dev Home user interface contains the following important "at a glance" info about the development console:</span></span>   
 
   *  <span data-ttu-id="a0e99-118">**Konsolen-IP:** Die aktuelle IP-Adresse der Konsole.</span><span class="sxs-lookup"><span data-stu-id="a0e99-118">**Console IP:** The current IP address of the console.</span></span>   
   *  <span data-ttu-id="a0e99-119">**Konsolenname:** Die aktuelle Hostnamen der Konsole.</span><span class="sxs-lookup"><span data-stu-id="a0e99-119">**Console name:** The current hostname of the console.</span></span>  
   *  <span data-ttu-id="a0e99-120">**Sandbox:** Der Name der Sandbox, der in die Konsole ist.</span><span class="sxs-lookup"><span data-stu-id="a0e99-120">**Sandbox:** The name of the sandbox that the console is in.</span></span>  
   *  <span data-ttu-id="a0e99-121">**Version des Betriebssystems:** Die aktuelle Recovery-Version, die auf der Konsole ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a0e99-121">**OS version:** The current recovery version that is running on the console.</span></span>
   *  <span data-ttu-id="a0e99-122">Aktuelle Systemzeit.</span><span class="sxs-lookup"><span data-stu-id="a0e99-122">Current system time.</span></span>   

   
  
<span data-ttu-id="a0e99-123">Der Rest der Dev Home-Benutzeroberfläche ist in den folgenden Seiten unterteilt.</span><span class="sxs-lookup"><span data-stu-id="a0e99-123">The rest of the Dev Home UI is divided into the following pages.</span></span> <span data-ttu-id="a0e99-124">Weitere Informationen zu den Tools auf diesen Seiten finden Sie unter ihren einzelnen Themen.</span><span class="sxs-lookup"><span data-stu-id="a0e99-124">For more information about the tools on these pages, see their individual topics.</span></span>   
 
   *  [<span data-ttu-id="a0e99-125">Startseite</span><span class="sxs-lookup"><span data-stu-id="a0e99-125">Home</span></span>](devhome-home.md)  
   *  [<span data-ttu-id="a0e99-126">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="a0e99-126">Xbox Live</span></span>](devhome-live.md)  
   *  [<span data-ttu-id="a0e99-127">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="a0e99-127">Settings</span></span>](devhome-settings.md)  
   *  [<span data-ttu-id="a0e99-128">Medienaufzeichnung</span><span class="sxs-lookup"><span data-stu-id="a0e99-128">Media capture</span></span>](devhome-capture.md)  
   *  [<span data-ttu-id="a0e99-129">Networking</span><span class="sxs-lookup"><span data-stu-id="a0e99-129">Networking</span></span>](devhome-networking.md)  
   *  [<span data-ttu-id="a0e99-130">Leistung</span><span class="sxs-lookup"><span data-stu-id="a0e99-130">Performance</span></span>](devhome-performance.md)  

  
<a id="ID4EKE"></a>

   

## <a name="main-menu"></a><span data-ttu-id="a0e99-131">Hauptmenü</span><span class="sxs-lookup"><span data-stu-id="a0e99-131">Main Menu</span></span>  
   
  
<span data-ttu-id="a0e99-132">Durch Drücken der Schaltfläche " **Menü** " auf Ihrem Controller, können Sie das Hauptmenü zugreifen, das Konfiguration von den app-Workspace, die Möglichkeit zum Verwalten von Anmeldeinformationen für den Zugriff auf Netzwerkressourcen und Informationen zum Übermitteln von Feedback an die app ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a0e99-132">By pressing the **menu** button on your controller, you can access the main menu that allows configuration of the app workspace, the ability to manage credentials for accessing network locations and information on providing feedback on the app.</span></span>   
  
<a id="ID4EUE"></a>

   

## <a name="snap-mode-ux"></a><span data-ttu-id="a0e99-133">Andockmodus UX</span><span class="sxs-lookup"><span data-stu-id="a0e99-133">Snap Mode UX</span></span>  
   
  
<span data-ttu-id="a0e99-134">Mehrere vorhandene und zukünftige Tools in Dev Home, z. B. Netzwerk- und Multiplayer-Spiele, dienen zu verwendende angedockt auf der Seite, während Sie Ihre Titel ausgeführt werden, damit haben Sie einfachen Zugriff auf Tools beim Testen Sie.</span><span class="sxs-lookup"><span data-stu-id="a0e99-134">Several existing and upcoming tools in Dev Home, such as Networking and Multiplayer, are designed to be used snapped to the side while you are running your title, so that you can have easy access to tools while you are testing.</span></span>   
   
  
<span data-ttu-id="a0e99-135">Um Snap Zugriffsmodus, markieren Sie den Titel des entsprechenden Tools, drücken die **Ansicht** -Taste auf dem Controller und wählen aus dem Kontextmenü **Einrasten** :</span><span class="sxs-lookup"><span data-stu-id="a0e99-135">To access Snap mode, highlight the title of the appropriate tool, press the **view** button on your controller, and select **snap** from the context menu:</span></span>  
 ![](images/dev_home_4.png)   
  
<span data-ttu-id="a0e99-136">Dev Home wird rechts angedockt.</span><span class="sxs-lookup"><span data-stu-id="a0e99-136">Dev Home will snap right.</span></span> <span data-ttu-id="a0e99-137">Sie können den Kontext umschalten, indem Sie wie gewohnt auf die Schaltfläche Nexus doppeltippen.</span><span class="sxs-lookup"><span data-stu-id="a0e99-137">You can switch context by double tapping the Nexus button as usual.</span></span>  
 ![](images/dev_home_5.png)  
<a id="ID4EKF"></a>

   

## <a name="customizing-dev-home"></a><span data-ttu-id="a0e99-138">Anpassen von Dev Home</span><span class="sxs-lookup"><span data-stu-id="a0e99-138">Customizing Dev Home</span></span>  
   
  
<span data-ttu-id="a0e99-139">Dev Home kann angepasst und personalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="a0e99-139">Dev Home has been designed to be customizable and personal.</span></span> <span data-ttu-id="a0e99-140">Sie können die app entsprechend Ihren Workflow zu konfigurieren und speichern, die dann als Arbeitsbereich.</span><span class="sxs-lookup"><span data-stu-id="a0e99-140">You can configure the app to suit your workflow, and then save that as a workspace.</span></span> <span data-ttu-id="a0e99-141">In diesem Arbeitsbereich exportiert werden kann und importierten, sodass Sie das Layout auf andere Konsolen als kopieren erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a0e99-141">This workspace can be exported and imported, allowing you to copy the layout to other consoles as needed.</span></span> <span data-ttu-id="a0e99-142">Diese Optionen finden Sie im Hauptmenü unter **Arbeitsbereich**.</span><span class="sxs-lookup"><span data-stu-id="a0e99-142">These options are found in the main menu under **workspace**.</span></span> <span data-ttu-id="a0e99-143">Die Exportdatei befinden sich auf dem Systemlaufwerk neu in der `Dev Home\Workspaces` Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="a0e99-143">The exported file will be located on the system scratch drive in the `Dev Home\Workspaces` directory.</span></span>   
 
<a id="ID4EVF"></a>

   

### <a name="resizing-and-reordering-tools"></a><span data-ttu-id="a0e99-144">Ändern der Größe und Neuanordnen von Tools</span><span class="sxs-lookup"><span data-stu-id="a0e99-144">Resizing and Reordering Tools</span></span>  
   
  
<span data-ttu-id="a0e99-145">Ändern der Größe oder Position eines Tools, verwenden Sie die Kontextmenüschaltfläche (Ansichtsschaltfläche auf Ihrem Controller) während des Titels hat den Fokus.</span><span class="sxs-lookup"><span data-stu-id="a0e99-145">To change the size or position of a tool, use the context menu button (view button on your controller) while the title has focus.</span></span> <span data-ttu-id="a0e99-146">Wählen Sie im Kontextmenü **Verschieben** oder **Größe ändern**.</span><span class="sxs-lookup"><span data-stu-id="a0e99-146">From the context menu select **Move** or **Resize**.</span></span>   
 ![](images/dev_home_6.png)  
<a id="ID4EEG"></a>

   

### <a name="changing-theme-color-and-background-image"></a><span data-ttu-id="a0e99-147">Ändern der Designfarbe und des Hintergrundbilds</span><span class="sxs-lookup"><span data-stu-id="a0e99-147">Changing theme color and background image</span></span>  
   
  
<span data-ttu-id="a0e99-148">Im Hauptmenü können Sie **im Arbeitsbereich "** und dann **Designfarbe ändern**auswählen.</span><span class="sxs-lookup"><span data-stu-id="a0e99-148">From the Main Menu, you can select **Workspace** and then **Change theme color**.</span></span> <span data-ttu-id="a0e99-149">Wählen Sie eine neue Farbe, und wählen Sie **Speichern** , um die Designfarbe zum Hervorheben des Fokus zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a0e99-149">Select a new color and select **Save** to update the theme color used for focus highlighting.</span></span>   
 ![](images/dev_home_7.png)  
<a id="ID4EVG"></a>

   

### <a name="setting-the-default-application-for-a-package"></a><span data-ttu-id="a0e99-150">Festlegen der Standard-Anwendungs für ein Paket</span><span class="sxs-lookup"><span data-stu-id="a0e99-150">Setting the default application for a package</span></span>  
   
  
<span data-ttu-id="a0e99-151">Enthält ein Paket mehrere Anwendungen, können Dev Home Sie festlegen, die standardanwendung gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="a0e99-151">If a package contains multiple applications, Dev Home will allow you to set the default application to be launched.</span></span> <span data-ttu-id="a0e99-152">Markieren Sie das Paket in das Startprogramm, und drücken Sie die **A** -Taste, um die Liste der verfügbaren Anwendungen zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a0e99-152">Highlight the package in the launcher and press the **A** button to open the list of available applications.</span></span> <span data-ttu-id="a0e99-153">Markieren Sie das Konto, die, das Sie als Standard festlegen und drücken die **Ansicht** -Taste, und wählen Sie dann im Kontextmenü die Option **als Standard festlegen** möchten.</span><span class="sxs-lookup"><span data-stu-id="a0e99-153">Highlight the one you wish to set as the default and press the **view** button, and then choose **Set as Default** from the context menu.</span></span>   
 ![](images/dev_home_setdefault.png)  
<a id="ID4EGH"></a>

   

### <a name="using-dev-home-to-register-and-launch-titles-from-a-network-share"></a><span data-ttu-id="a0e99-154">Verwenden von Dev Home zu registrieren und starten die Titel von einer Netzwerkfreigabe</span><span class="sxs-lookup"><span data-stu-id="a0e99-154">Using Dev Home to register and launch titles from a network share</span></span>  
   
  
<span data-ttu-id="a0e99-155">Aus dem Launcher, am unteren Rand der installierten apps und Spieleliste können Sie die Möglichkeit, die **ein Spiel von einer Netzwerkfreigabe zu registrieren** , eine lose Dateiversion eines Titels Remote ausführen auswählen.</span><span class="sxs-lookup"><span data-stu-id="a0e99-155">From the launcher, at the bottom of the installed apps and games list, you can select the option **Register a game from a network share** to run a loose file version of a title remotely.</span></span>   
 ![](images/dev_home_8.png)   
  
<span data-ttu-id="a0e99-156">Sie können den Netzwerkpfad klicken Sie dann auf die Datei "appxmanifest.xml" für den Titel eingeben, die Sie registrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="a0e99-156">You can then enter the network path to the appxmanifest.xml file for the title you wish to register.</span></span> <span data-ttu-id="a0e99-157">Dev Home wird versucht, den Titel über alle vorhandenen Anmeldeinformationen für diese Freigabe registrieren und, wenn für die neuen Netzwerkanmeldeinformationen fordert erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a0e99-157">Dev Home will attempt to register the title using any existing credentials for that share, and if needed will prompt for new network credentials.</span></span> <span data-ttu-id="a0e99-158">Wenn Sie zusätzliche Freigaben (z. B. um Zugriff auf symbolisch verknüpft Ressourcen auf einem anderen Server) zugreifen müssen, müssen Sie diese über die Option unterhalb hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a0e99-158">If you need to access additional shares (for example to access symbolically linked resources on a separate server) then you will need to add those via the option below.</span></span>   
   
  
<span data-ttu-id="a0e99-159">Sie können diese gespeicherten Anmeldeinformationen verwalten (und zusätzliche hinzufügen) auf der Konsole über das Hauptmenü **Verwalten der Netzwerkanmeldeinformationen** Option.</span><span class="sxs-lookup"><span data-stu-id="a0e99-159">You can manage these stored credentials (and add additional ones) on the console via the main menu's **Manage network credentials** option.</span></span>   
 ![](images/dev_home_9.png)   
  
<span data-ttu-id="a0e99-160">Sie können die Anmeldeinformationen derzeit auf der Konsole anzeigen, Anmeldeinformationen bearbeiten, indem Sie den Pfad der Anmeldeinformationen auswählen und durch Klicken auf **eine** Schaltfläche und Entfernen von Anmeldeinformationen durch Auswählen des Links entfernen und durch Klicken auf **eine** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="a0e99-160">You can view the credentials currently on the console, edit credentials by selecting the path of the credential and clicking **A** button and remove a credential by selecting the remove link and clicking **A** button.</span></span>   
   
<a id="ID4EGAAC"></a>

   

## <a name="in-this-section"></a><span data-ttu-id="a0e99-161">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="a0e99-161">In this section</span></span>  
  
[<span data-ttu-id="a0e99-162">Startseite (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="a0e99-162">Home Page (Dev Home)</span></span>](devhome-home.md)  


<span data-ttu-id="a0e99-163">&nbsp;&nbsp;Bietet schnellen Zugriff auf die Aufgaben, die für eine entwicklungskonsole routinemäßig durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a0e99-163">&nbsp;&nbsp;Provides quick access to the tasks that are routinely performed on a development console.</span></span> 
  
  
[<span data-ttu-id="a0e99-164">Xbox Live-Seite (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="a0e99-164">Xbox Live Page (Dev Home)</span></span>](devhome-live.md)  


<span data-ttu-id="a0e99-165">&nbsp;&nbsp;Multiplayer-Informationen erfasst und zeigt den aktuellen Status des Xbox Live-Diensts.</span><span class="sxs-lookup"><span data-stu-id="a0e99-165">&nbsp;&nbsp;Captures multiplayer information and displays the current status of the Xbox Live service.</span></span> 
  
  
[<span data-ttu-id="a0e99-166">Seite "Einstellungen" (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="a0e99-166">Settings Page (Dev Home)</span></span>](devhome-settings.md)  


<span data-ttu-id="a0e99-167">&nbsp;&nbsp;Bietet Zugriff auf verschiedene Einstellungen für die entwicklungskonsole.</span><span class="sxs-lookup"><span data-stu-id="a0e99-167">&nbsp;&nbsp;Provides access to various settings for the development console.</span></span> 
  
  
[<span data-ttu-id="a0e99-168">Aufzeichnen von Medien Seite (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="a0e99-168">Media Capture Page (Dev Home)</span></span>](devhome-capture.md)  


<span data-ttu-id="a0e99-169">&nbsp;&nbsp;Der Seite " **medienerfassung** " von Dev Home nimmt Video des Titels, die derzeit auf der Konsole ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a0e99-169">&nbsp;&nbsp;The **Media capture** page of Dev Home captures video of the title that is currently running on the console.</span></span> 
  
  
[<span data-ttu-id="a0e99-170">Netzwerkseite (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="a0e99-170">Networking Page (Dev Home)</span></span>](devhome-networking.md)  


<span data-ttu-id="a0e99-171">&nbsp;&nbsp;Simuliert verschiedene Netzwerke Ursachen für die Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="a0e99-171">&nbsp;&nbsp;Simulates various networking conditions for troubleshooting purposes.</span></span> 
  
  
[<span data-ttu-id="a0e99-172">Seite "Performance" (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="a0e99-172">Performance Page (Dev Home)</span></span>](devhome-performance.md)  


<span data-ttu-id="a0e99-173">&nbsp;&nbsp;Simuliert verschiedene Festplatten-Aktivität und CPU-Auslastung Bedingungen für die Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="a0e99-173">&nbsp;&nbsp;Simulates various disk activity and CPU usage conditions for troubleshooting purposes.</span></span> 
 