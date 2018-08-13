---
author: v-angraf
ms.assetid: a56156e4-7adb-bf37-527b-fc3243e04b46
title: Entwickler-Homepage in der Konsole (Dev-Startseite)
description: Enthält Informationen zu der app Dev-Startseite für Xbox ein.
ms.author: v-angraf@microsoft.com
ms.date: 08/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
permalink: en-us/docs/xdk/dev-home.html
ms.localizationpriority: medium
ms.openlocfilehash: 3b802b9b53811e03e11ee3afd78f69db4bfd9986
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1015359"
---
# <a name="developer-home-on-the-console-dev-home"></a><span data-ttu-id="a2d7f-104">Entwickler-Homepage in der Konsole (Dev-Startseite)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-104">Developer Home on the Console (Dev Home)</span></span>
   
  
<span data-ttu-id="a2d7f-105">Dev-Startseite ist eine Tools bei im Xbox ein Development Kit Developer Produktivität unterstützen soll.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-105">Dev Home is a tools experience on the Xbox One development kit designed to aid developer productivity.</span></span> <span data-ttu-id="a2d7f-106">Dev-Startseite bietet Funktionen zum Verwalten und Konfigurieren Ihrer Development Kit, Verwalten von Benutzern, Starten der installierten Titel und durchführen erfasst und verfolgt.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-106">Dev Home offers functionality to manage and configure your development kit, manage users, launch installed titles and perform captures and traces.</span></span> <span data-ttu-id="a2d7f-107">In zukünftigen Versionen, die wir weiterhin erweitern die Funktionalität zum Aktivieren von zusätzlichen Features basierend auf Ihrem Feedback und Erweiterbarkeit und das Hinzufügen von eigene Tools zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-107">In future releases we will continue to expand the functionality to enable additional features based on your feedback, and also to enable extensibility and the addition of your own tools.</span></span>   
   
  
<span data-ttu-id="a2d7f-108">Wir sind sehr Ihr Feedback Dev Home und die Szenarien, die Sie am häufigsten interessiert es unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-108">We are very interested in your feedback on Dev Home and the scenarios you are most interested in seeing it support.</span></span> <span data-ttu-id="a2d7f-109">Geben Sie Ihre Kommentare über unter **Feedback senden** in der app im Hauptmenü beschriebenen Methoden oder über Developer Konto-Manager (DAM).</span><span class="sxs-lookup"><span data-stu-id="a2d7f-109">Please provide your comments through the methods described under **Send Feedback** in the main menu of the app or through your Developer Account Manager (DAM).</span></span>   
   
  
<span data-ttu-id="a2d7f-110">So starten Sie Dev Home auf die November 2015 oder höher Wiederherstellung:</span><span class="sxs-lookup"><span data-stu-id="a2d7f-110">To launch Dev Home on the November 2015 or later recovery:</span></span>  
 
   1. <span data-ttu-id="a2d7f-111">Öffnen Sie im Handbuch durch Verschieben links auf der Startseite oder auf die Schaltfläche Nexus double</span><span class="sxs-lookup"><span data-stu-id="a2d7f-111">Open the guide by moving left on Home, or double clicking the Nexus button</span></span>  
   1. <span data-ttu-id="a2d7f-112">Nach unten, um **Einstellungen** (Zahnradsymbol)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-112">Move down to **Settings** (the gear icon)</span></span>   
   1. <span data-ttu-id="a2d7f-113">Wählen Sie **Alle Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-113">Select **All settings**</span></span>  
   1. <span data-ttu-id="a2d7f-114">Wählen Sie aus der Standardseite **Developer** **Developer – Startseite** (Symbol für die Startseite)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-114">From the default **Developer** page, select **Developer Home** (the home icon)</span></span>   

 ![](images/dev_home_icons.png)   
  
<span data-ttu-id="a2d7f-115">Zeigen Sie auf früheren Recovery wählen Sie die Kachel Dev-Homepage auf der rechten Seite des die Startseite in **wichtige Inhalte** oder der Liste in Xbox ein Manager und **Dev Start**zu starten.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-115">On earlier recoveries select the Dev Home tile on the right side of the home screen in **featured content** or view the application list in Xbox One Manager and launch **Dev Home**.</span></span>   
 ![](images/dev_home_1.png) 
<a id="ID4EBC"></a>

   

## <a name="user-interface"></a><span data-ttu-id="a2d7f-116">Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="a2d7f-116">User Interface</span></span>  
   
  
<span data-ttu-id="a2d7f-117">Die Kopfzeile der Benutzeroberfläche Dev-Startseite enthält die folgenden wichtigen "auf einen Blick" Info über die Entwicklung-Verwaltungskonsole:</span><span class="sxs-lookup"><span data-stu-id="a2d7f-117">The header of the Dev Home user interface contains the following important "at a glance" info about the development console:</span></span>   
 
   *  <span data-ttu-id="a2d7f-118">**IP-Konsole:** Die aktuelle IP-Adresse der Konsole.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-118">**Console IP:** The current IP address of the console.</span></span>   
   *  <span data-ttu-id="a2d7f-119">**Konsole Name:** Der aktuelle Hostname der Konsole.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-119">**Console name:** The current hostname of the console.</span></span>  
   *  <span data-ttu-id="a2d7f-120">**Sandkasten:** Der Name des Sandkastens besteht, dem in die Konsole ist.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-120">**Sandbox:** The name of the sandbox that the console is in.</span></span>  
   *  <span data-ttu-id="a2d7f-121">**Version des Betriebssystems:** Die aktuelle Recovery-Version, die in der Konsole ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-121">**OS version:** The current recovery version that is running on the console.</span></span>
   *  <span data-ttu-id="a2d7f-122">Aktuelle Systemzeit.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-122">Current system time.</span></span>   

   
  
<span data-ttu-id="a2d7f-123">Die restlichen Dev Home Benutzeroberfläche ist in den folgenden Seiten unterteilt.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-123">The rest of the Dev Home UI is divided into the following pages.</span></span> <span data-ttu-id="a2d7f-124">Weitere Informationen zu den Tools auf diesen Seiten finden Sie unter ihre einzelnen Themen.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-124">For more information about the tools on these pages, see their individual topics.</span></span>   
 
   *  [<span data-ttu-id="a2d7f-125">Startseite</span><span class="sxs-lookup"><span data-stu-id="a2d7f-125">Home</span></span>](devhome-home.md)  
   *  [<span data-ttu-id="a2d7f-126">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="a2d7f-126">Xbox Live</span></span>](devhome-live.md)  
   *  [<span data-ttu-id="a2d7f-127">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="a2d7f-127">Settings</span></span>](devhome-settings.md)  
   *  [<span data-ttu-id="a2d7f-128">Medienaufzeichnung</span><span class="sxs-lookup"><span data-stu-id="a2d7f-128">Media capture</span></span>](devhome-capture.md)  
   *  [<span data-ttu-id="a2d7f-129">Networking</span><span class="sxs-lookup"><span data-stu-id="a2d7f-129">Networking</span></span>](devhome-networking.md)  
   *  [<span data-ttu-id="a2d7f-130">Leistung</span><span class="sxs-lookup"><span data-stu-id="a2d7f-130">Performance</span></span>](devhome-performance.md)  

  
<a id="ID4EKE"></a>

   

## <a name="main-menu"></a><span data-ttu-id="a2d7f-131">Klicken Sie im Hauptmenü</span><span class="sxs-lookup"><span data-stu-id="a2d7f-131">Main Menu</span></span>  
   
  
<span data-ttu-id="a2d7f-132">Drücken Sie die Schaltfläche **Menü** , auf dem Domänencontroller, können Sie im Hauptmenü zugreifen, die Konfiguration des Arbeitsbereichs app, die Möglichkeit zur Verwaltung von Anmeldeinformationen für den Zugriff auf Netzwerkressourcen und Informationen zum Bereitstellen von Feedback für die app ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-132">By pressing the **menu** button on your controller, you can access the main menu that allows configuration of the app workspace, the ability to manage credentials for accessing network locations and information on providing feedback on the app.</span></span>   
  
<a id="ID4EUE"></a>

   

## <a name="snap-mode-ux"></a><span data-ttu-id="a2d7f-133">Modus UX ausrichten</span><span class="sxs-lookup"><span data-stu-id="a2d7f-133">Snap Mode UX</span></span>  
   
  
<span data-ttu-id="a2d7f-134">Mehrere vorhandenen und zukünftigen Tools in Dev Ihnen zu Hause, wie Netzwerk- und Multiplayer, dienen zu verwendende ausgerichtet auf der Seite, während Sie Ihr Titel ausgeführt werden, damit für einfachen Zugriff auf Tools beim Testen verwendet.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-134">Several existing and upcoming tools in Dev Home, such as Networking and Multiplayer, are designed to be used snapped to the side while you are running your title, so that you can have easy access to tools while you are testing.</span></span>   
   
  
<span data-ttu-id="a2d7f-135">Snap Zugriffsmodus, markieren Sie den Titel des entsprechenden Tools, drücken die Schaltfläche **Ansicht** auf Ihrem Domänencontroller und wählen im Kontextmenü die Option **Ausrichten** :</span><span class="sxs-lookup"><span data-stu-id="a2d7f-135">To access Snap mode, highlight the title of the appropriate tool, press the **view** button on your controller, and select **snap** from the context menu:</span></span>  
 ![](images/dev_home_4.png)   
  
<span data-ttu-id="a2d7f-136">Dev Home wird rechts angedockt.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-136">Dev Home will snap right.</span></span> <span data-ttu-id="a2d7f-137">Sie können den Kontext umschalten, indem Sie wie gewohnt auf die Schaltfläche Nexus doppeltippen.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-137">You can switch context by double tapping the Nexus button as usual.</span></span>  
 ![](images/dev_home_5.png)  
<a id="ID4EKF"></a>

   

## <a name="customizing-dev-home"></a><span data-ttu-id="a2d7f-138">Anpassen von Dev Home</span><span class="sxs-lookup"><span data-stu-id="a2d7f-138">Customizing Dev Home</span></span>  
   
  
<span data-ttu-id="a2d7f-139">Dev Home kann angepasst und personalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-139">Dev Home has been designed to be customizable and personal.</span></span> <span data-ttu-id="a2d7f-140">Sie können die app entsprechend Ihrem Workflow konfigurieren, und speichern, die Sie als Arbeitsbereich.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-140">You can configure the app to suit your workflow, and then save that as a workspace.</span></span> <span data-ttu-id="a2d7f-141">Dieser Arbeitsbereich exportiert werden kann, und importiert, sodass Sie das Layout auf andere Konsolen als kopieren benötigt.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-141">This workspace can be exported and imported, allowing you to copy the layout to other consoles as needed.</span></span> <span data-ttu-id="a2d7f-142">Diese Optionen befinden sich im Hauptmenü unter **Arbeitsbereich**.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-142">These options are found in the main menu under **workspace**.</span></span> <span data-ttu-id="a2d7f-143">Die exportierte Datei befinden sich auf dem Systemlaufwerk Scratch in der `Dev Home\Workspaces` Directory.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-143">The exported file will be located on the system scratch drive in the `Dev Home\Workspaces` directory.</span></span>   
 
<a id="ID4EVF"></a>

   

### <a name="resizing-and-reordering-tools"></a><span data-ttu-id="a2d7f-144">Ändern der Größe und Neuanordnen von Tools</span><span class="sxs-lookup"><span data-stu-id="a2d7f-144">Resizing and Reordering Tools</span></span>  
   
  
<span data-ttu-id="a2d7f-145">Ändern der Größe oder Position eines Tools, verwenden Sie die Schaltfläche Kontextmenü (Ansichtsschaltfläche auf dem Domänencontroller) während des Titels hat den Fokus.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-145">To change the size or position of a tool, use the context menu button (view button on your controller) while the title has focus.</span></span> <span data-ttu-id="a2d7f-146">Wählen Sie im Kontextmenü die Option **Verschieben** oder **Ändern der Größe**.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-146">From the context menu select **Move** or **Resize**.</span></span>   
 ![](images/dev_home_6.png)  
<a id="ID4EEG"></a>

   

### <a name="changing-theme-color-and-background-image"></a><span data-ttu-id="a2d7f-147">Ändern der Designfarbe und des Hintergrundbilds</span><span class="sxs-lookup"><span data-stu-id="a2d7f-147">Changing theme color and background image</span></span>  
   
  
<span data-ttu-id="a2d7f-148">Im Hauptmenü können Sie den **Arbeitsbereich** , und klicken Sie dann **Designfarbe ändern**auswählen.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-148">From the Main Menu, you can select **Workspace** and then **Change theme color**.</span></span> <span data-ttu-id="a2d7f-149">Wählen Sie eine neue Farbe, und wählen Sie **Speichern** , so aktualisieren Sie die Designfarbe für die Hervorhebung von Fokus verwendet.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-149">Select a new color and select **Save** to update the theme color used for focus highlighting.</span></span>   
 ![](images/dev_home_7.png)  
<a id="ID4EVG"></a>

   

### <a name="setting-the-default-application-for-a-package"></a><span data-ttu-id="a2d7f-150">Festlegen der standardanwendung für ein Paket</span><span class="sxs-lookup"><span data-stu-id="a2d7f-150">Setting the default application for a package</span></span>  
   
  
<span data-ttu-id="a2d7f-151">Wenn ein Paket mehrere Clientanwendungen enthält, können Dev-Startseite Sie legen Sie die Standard-Anwendung gestartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-151">If a package contains multiple applications, Dev Home will allow you to set the default application to be launched.</span></span> <span data-ttu-id="a2d7f-152">Markieren Sie das Paket in das Startprogramm für, und drücken Sie die Taste **A** , um die Liste der verfügbaren Anwendungen öffnen.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-152">Highlight the package in the launcher and press the **A** button to open the list of available applications.</span></span> <span data-ttu-id="a2d7f-153">Markieren Sie das Konto als Standard festgelegt und drücken die Schaltfläche **Ansicht** , und wählen Sie dann im Kontextmenü die Option **als Standard festlegen** möchten.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-153">Highlight the one you wish to set as the default and press the **view** button, and then choose **Set as Default** from the context menu.</span></span>   
 ![](images/dev_home_setdefault.png)  
<a id="ID4EGH"></a>

   

### <a name="using-dev-home-to-register-and-launch-titles-from-a-network-share"></a><span data-ttu-id="a2d7f-154">Verwenden Dev Home registrieren und starten Sie Titel über eine Netzwerkfreigabe</span><span class="sxs-lookup"><span data-stu-id="a2d7f-154">Using Dev Home to register and launch titles from a network share</span></span>  
   
  
<span data-ttu-id="a2d7f-155">Wählen Sie aus der Launcher am unteren Rand der installierten apps und Spiele-Liste die Option **registrieren ein Spiels von einer Netzwerkfreigabe** auf eine weit Dateiversion eines Titels Remote ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-155">From the launcher, at the bottom of the installed apps and games list, you can select the option **Register a game from a network share** to run a loose file version of a title remotely.</span></span>   
 ![](images/dev_home_8.png)   
  
<span data-ttu-id="a2d7f-156">Sie können den Netzwerkpfad klicken Sie dann auf die Datei appxmanifest.xml für den Titel eingeben, die Sie registrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-156">You can then enter the network path to the appxmanifest.xml file for the title you wish to register.</span></span> <span data-ttu-id="a2d7f-157">Dev Home wird versucht, den Titel über alle vorhandenen Anmeldeinformationen für diese Freigabe zu registrieren und wenn für neue Netzwerkanmeldeinformationen fordert benötigt.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-157">Dev Home will attempt to register the title using any existing credentials for that share, and if needed will prompt for new network credentials.</span></span> <span data-ttu-id="a2d7f-158">Wenn Sie zusätzliche Freigaben (beispielsweise auf Ressourcen zugreifen, die symbolisch verknüpft auf einem separaten Server) zugreifen möchten, müssen Sie die über die Option unterhalb hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-158">If you need to access additional shares (for example to access symbolically linked resources on a separate server) then you will need to add those via the option below.</span></span>   
   
  
<span data-ttu-id="a2d7f-159">Sie können diese gespeicherten Anmeldeinformationen verwalten (und Hinzufügen zusätzlicher) in der Konsole über das Hauptmenü **Verwalten Netzwerkanmeldeinformationen** Option.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-159">You can manage these stored credentials (and add additional ones) on the console via the main menu's **Manage network credentials** option.</span></span>   
 ![](images/dev_home_9.png)   
  
<span data-ttu-id="a2d7f-160">Die Anmeldeinformationen derzeit in der Konsole anzuzeigen, Anmeldeinformationen auswählen den Pfad der Anmeldeinformationen und auf **eine** Schaltfläche Bearbeiten, und entfernen einen Satz von Anmeldeinformationen, indem Sie den Link entfernen auswählen und auf **eine** Schaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-160">You can view the credentials currently on the console, edit credentials by selecting the path of the credential and clicking **A** button and remove a credential by selecting the remove link and clicking **A** button.</span></span>   
   
<a id="ID4EGAAC"></a>

   

## <a name="in-this-section"></a><span data-ttu-id="a2d7f-161">Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="a2d7f-161">In this section</span></span>  
  
[<span data-ttu-id="a2d7f-162">Homepage (Dev-Startseite)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-162">Home Page (Dev Home)</span></span>](devhome-home.md)  


<span data-ttu-id="a2d7f-163">&nbsp;&nbsp;Bietet schnellen Zugriff auf die Aufgaben, die auf einer Konsole Entwicklung regelmäßig ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-163">&nbsp;&nbsp;Provides quick access to the tasks that are routinely performed on a development console.</span></span> 
  
  
[<span data-ttu-id="a2d7f-164">Xbox Live Seite (Dev-Startseite)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-164">Xbox Live Page (Dev Home)</span></span>](devhome-live.md)  


<span data-ttu-id="a2d7f-165">&nbsp;&nbsp;Mehrere Spieler Informationen erfasst und zeigt den aktuellen Status des Xbox Live-Dienstes.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-165">&nbsp;&nbsp;Captures multiplayer information and displays the current status of the Xbox Live service.</span></span> 
  
  
[<span data-ttu-id="a2d7f-166">Einstellungsseite (Dev-Startseite)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-166">Settings Page (Dev Home)</span></span>](devhome-settings.md)  


<span data-ttu-id="a2d7f-167">&nbsp;&nbsp;Ermöglicht den Zugriff auf verschiedene Einstellungen für die Entwicklung-Konsole.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-167">&nbsp;&nbsp;Provides access to various settings for the development console.</span></span> 
  
  
[<span data-ttu-id="a2d7f-168">Media erfassen Seite (Dev-Startseite)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-168">Media Capture Page (Dev Home)</span></span>](devhome-capture.md)  


<span data-ttu-id="a2d7f-169">&nbsp;&nbsp;Die Seite **Medien erfassen** der Dev Home nimmt Video des Titels, die derzeit in der Konsole ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-169">&nbsp;&nbsp;The **Media capture** page of Dev Home captures video of the title that is currently running on the console.</span></span> 
  
  
[<span data-ttu-id="a2d7f-170">Netzwerkseite (Dev-Startseite)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-170">Networking Page (Dev Home)</span></span>](devhome-networking.md)  


<span data-ttu-id="a2d7f-171">&nbsp;&nbsp;Simuliert verschiedene Netzwerke Ursachen für die Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-171">&nbsp;&nbsp;Simulates various networking conditions for troubleshooting purposes.</span></span> 
  
  
[<span data-ttu-id="a2d7f-172">Seite "Leistung" (Dev-Startseite)</span><span class="sxs-lookup"><span data-stu-id="a2d7f-172">Performance Page (Dev Home)</span></span>](devhome-performance.md)  


<span data-ttu-id="a2d7f-173">&nbsp;&nbsp;Simuliert verschiedene Datenträgeraktivität und CPU-Auslastung Bedingungen für die Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="a2d7f-173">&nbsp;&nbsp;Simulates various disk activity and CPU usage conditions for troubleshooting purposes.</span></span> 
 