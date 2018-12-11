---
ms.assetid: a56156e4-7adb-bf37-527b-fc3243e04b46
title: Entwickler-Startbildschirm auf der Konsole (Dev Home)
description: Enthält Informationen zu Dev Home-app für Xbox One.
ms.date: 08/09/2017
ms.topic: article
keywords: Windows10, UWP
permalink: en-us/docs/xdk/dev-home.html
ms.localizationpriority: medium
ms.openlocfilehash: 4113df37446d93883cf395e7c1e86b1de6c1b328
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8885158"
---
# <a name="developer-home-on-the-console-dev-home"></a><span data-ttu-id="3a863-104">Entwickler-Startbildschirm auf der Konsole (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="3a863-104">Developer Home on the Console (Dev Home)</span></span>
   
  
<span data-ttu-id="3a863-105">Dev Home ist ein Tool im Xbox One Development Kit von Produktivität von Entwicklern unterstützen soll.</span><span class="sxs-lookup"><span data-stu-id="3a863-105">Dev Home is a tools experience on the Xbox One development kit designed to aid developer productivity.</span></span> <span data-ttu-id="3a863-106">Dev Home bietet Funktionen zum Verwalten und Konfigurieren Ihres Development Kit, Verwalten von Benutzern, installierte Titel starten und Ausführen erfasst und erfasst.</span><span class="sxs-lookup"><span data-stu-id="3a863-106">Dev Home offers functionality to manage and configure your development kit, manage users, launch installed titles and perform captures and traces.</span></span> <span data-ttu-id="3a863-107">In zukünftigen Versionen, die wir erweitern Sie die Funktionalität weiterhin, um zusätzliche Funktionen, die basierend auf Ihr Feedback zu aktivieren und auch Erweiterbarkeit und das Hinzufügen der eigene Tools zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="3a863-107">In future releases we will continue to expand the functionality to enable additional features based on your feedback, and also to enable extensibility and the addition of your own tools.</span></span>   
   
  
<span data-ttu-id="3a863-108">Wir sind sehr in Ihr Feedback zu Dev Home und die Szenarien, die Sie am besten sehen sie unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="3a863-108">We are very interested in your feedback on Dev Home and the scenarios you are most interested in seeing it support.</span></span> <span data-ttu-id="3a863-109">Geben Sie Ihre Kommentare, über die Methoden in der app im Hauptmenü unter **Feedback senden** beschriebenen oder über Ihre Entwickler-Konto-Manager (Mutter).</span><span class="sxs-lookup"><span data-stu-id="3a863-109">Please provide your comments through the methods described under **Send Feedback** in the main menu of the app or through your Developer Account Manager (DAM).</span></span>   
   
  
<span data-ttu-id="3a863-110">So starten Sie Dev Home auf der November 2015 oder höher Wiederherstellung</span><span class="sxs-lookup"><span data-stu-id="3a863-110">To launch Dev Home on the November 2015 or later recovery:</span></span>  
 
   1. <span data-ttu-id="3a863-111">Öffnen Sie die Anleitung durch Verschieben nach links auf der Startseite, oder klicken auf die Schaltfläche Nexus double</span><span class="sxs-lookup"><span data-stu-id="3a863-111">Open the guide by moving left on Home, or double clicking the Nexus button</span></span>  
   1. <span data-ttu-id="3a863-112">Nach unten, um **Einstellungen** (das Zahnradsymbol)</span><span class="sxs-lookup"><span data-stu-id="3a863-112">Move down to **Settings** (the gear icon)</span></span>   
   1. <span data-ttu-id="3a863-113">Wählen Sie **Alle Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="3a863-113">Select **All settings**</span></span>  
   1. <span data-ttu-id="3a863-114">Wählen Sie auf **der Standard-Entwicklerseite** **Entwickler-Startbildschirm** (Symbol für die Startseite)</span><span class="sxs-lookup"><span data-stu-id="3a863-114">From the default **Developer** page, select **Developer Home** (the home icon)</span></span>   

 ![](images/dev_home_icons.png)   
  
<span data-ttu-id="3a863-115">Zeigen Sie auf früheren benötigt wählen Sie die Dev Home-Kachel auf der rechten Seite des der Startseite im **Inhalt angeboten** oder die Liste der Anwendung im Xbox One-Manager und starten Sie **Dev Home**.</span><span class="sxs-lookup"><span data-stu-id="3a863-115">On earlier recoveries select the Dev Home tile on the right side of the home screen in **featured content** or view the application list in Xbox One Manager and launch **Dev Home**.</span></span>   
 ![](images/dev_home_1.png) 
<a id="ID4EBC"></a>

   

## <a name="user-interface"></a><span data-ttu-id="3a863-116">Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="3a863-116">User Interface</span></span>  
   
  
<span data-ttu-id="3a863-117">Der Header der Dev Home-Benutzeroberfläche enthält die folgenden "auf einen Blick" wichtige Informationen über die Entwicklung-Verwaltungskonsole:</span><span class="sxs-lookup"><span data-stu-id="3a863-117">The header of the Dev Home user interface contains the following important "at a glance" info about the development console:</span></span>   
 
   *  <span data-ttu-id="3a863-118">**Konsolen-IP:** Die aktuelle IP-Adresse der Konsole.</span><span class="sxs-lookup"><span data-stu-id="3a863-118">**Console IP:** The current IP address of the console.</span></span>   
   *  <span data-ttu-id="3a863-119">**Konsolenname:** Die aktuelle Hostnamen der Konsole.</span><span class="sxs-lookup"><span data-stu-id="3a863-119">**Console name:** The current hostname of the console.</span></span>  
   *  <span data-ttu-id="3a863-120">**Sandbox:** Der Name der Sandbox, der in die Konsole ist.</span><span class="sxs-lookup"><span data-stu-id="3a863-120">**Sandbox:** The name of the sandbox that the console is in.</span></span>  
   *  <span data-ttu-id="3a863-121">**Version des Betriebssystems:** Die aktuelle Recovery-Version, die auf der Konsole ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3a863-121">**OS version:** The current recovery version that is running on the console.</span></span>
   *  <span data-ttu-id="3a863-122">Aktuelle Systemzeit.</span><span class="sxs-lookup"><span data-stu-id="3a863-122">Current system time.</span></span>   

   
  
<span data-ttu-id="3a863-123">Der Rest der Dev Home-Benutzeroberfläche ist in den folgenden Seiten unterteilt.</span><span class="sxs-lookup"><span data-stu-id="3a863-123">The rest of the Dev Home UI is divided into the following pages.</span></span> <span data-ttu-id="3a863-124">Weitere Informationen zu den Tools auf diesen Seiten finden Sie die einzelnen Themen.</span><span class="sxs-lookup"><span data-stu-id="3a863-124">For more information about the tools on these pages, see their individual topics.</span></span>   
 
   *  [<span data-ttu-id="3a863-125">Startseite</span><span class="sxs-lookup"><span data-stu-id="3a863-125">Home</span></span>](devhome-home.md)  
   *  [<span data-ttu-id="3a863-126">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="3a863-126">Xbox Live</span></span>](devhome-live.md)  
   *  [<span data-ttu-id="3a863-127">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="3a863-127">Settings</span></span>](devhome-settings.md)  
   *  [<span data-ttu-id="3a863-128">Medienaufzeichnung</span><span class="sxs-lookup"><span data-stu-id="3a863-128">Media capture</span></span>](devhome-capture.md)  
   *  [<span data-ttu-id="3a863-129">Networking</span><span class="sxs-lookup"><span data-stu-id="3a863-129">Networking</span></span>](devhome-networking.md)  
   *  [<span data-ttu-id="3a863-130">Leistung</span><span class="sxs-lookup"><span data-stu-id="3a863-130">Performance</span></span>](devhome-performance.md)  

  
<a id="ID4EKE"></a>

   

## <a name="main-menu"></a><span data-ttu-id="3a863-131">Hauptmenü</span><span class="sxs-lookup"><span data-stu-id="3a863-131">Main Menu</span></span>  
   
  
<span data-ttu-id="3a863-132">Drücken Sie **die Menütaste** auf Ihrem Controller, können Sie das Hauptmenü zugreifen, das Konfiguration von den app-Workspace, die Verwaltung von Anmeldeinformationen für den Zugriff auf Netzwerkressourcen und Informationen zum Bereitstellen von Feedback für die app ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="3a863-132">By pressing the **menu** button on your controller, you can access the main menu that allows configuration of the app workspace, the ability to manage credentials for accessing network locations and information on providing feedback on the app.</span></span>   
  
<a id="ID4EUE"></a>

   

## <a name="snap-mode-ux"></a><span data-ttu-id="3a863-133">Andockmodus UX</span><span class="sxs-lookup"><span data-stu-id="3a863-133">Snap Mode UX</span></span>  
   
  
<span data-ttu-id="3a863-134">Verschiedene vorhandene und zukünftige Tools in Dev Home, z. B. Netzwerk- und Multiplayer-Spiele, dienen zur verwendet werden, angedockt auf der Seite, während Sie den Titel ausführen, damit Sie einfachen Zugriff auf Tools beim Testen haben.</span><span class="sxs-lookup"><span data-stu-id="3a863-134">Several existing and upcoming tools in Dev Home, such as Networking and Multiplayer, are designed to be used snapped to the side while you are running your title, so that you can have easy access to tools while you are testing.</span></span>   
   
  
<span data-ttu-id="3a863-135">Snap Modus den Zugriff auf Markieren Sie den Titel des entsprechenden Tools, drücken Sie die **Ansicht** -Taste auf dem Controller, und wählen Sie im Kontextmenü **Ausrichten** :</span><span class="sxs-lookup"><span data-stu-id="3a863-135">To access Snap mode, highlight the title of the appropriate tool, press the **view** button on your controller, and select **snap** from the context menu:</span></span>  
 ![](images/dev_home_4.png)   
  
<span data-ttu-id="3a863-136">Dev Home wird rechts angedockt.</span><span class="sxs-lookup"><span data-stu-id="3a863-136">Dev Home will snap right.</span></span> <span data-ttu-id="3a863-137">Sie können den Kontext umschalten, indem Sie wie gewohnt auf die Schaltfläche Nexus doppeltippen.</span><span class="sxs-lookup"><span data-stu-id="3a863-137">You can switch context by double tapping the Nexus button as usual.</span></span>  
 ![](images/dev_home_5.png)  
<a id="ID4EKF"></a>

   

## <a name="customizing-dev-home"></a><span data-ttu-id="3a863-138">Anpassen von Dev Home</span><span class="sxs-lookup"><span data-stu-id="3a863-138">Customizing Dev Home</span></span>  
   
  
<span data-ttu-id="3a863-139">Dev Home kann angepasst und personalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="3a863-139">Dev Home has been designed to be customizable and personal.</span></span> <span data-ttu-id="3a863-140">Sie können die app Ihrem Workflow entsprechend konfigurieren, und speichern, die als Arbeitsbereich.</span><span class="sxs-lookup"><span data-stu-id="3a863-140">You can configure the app to suit your workflow, and then save that as a workspace.</span></span> <span data-ttu-id="3a863-141">Diesen Arbeitsbereich kann exportiert und importiert, sodass Sie das Layout auf andere Konsolen als kopieren erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3a863-141">This workspace can be exported and imported, allowing you to copy the layout to other consoles as needed.</span></span> <span data-ttu-id="3a863-142">Diese Optionen finden Sie im Hauptmenü unter **Arbeitsbereich**.</span><span class="sxs-lookup"><span data-stu-id="3a863-142">These options are found in the main menu under **workspace**.</span></span> <span data-ttu-id="3a863-143">Auf dem Systemlaufwerk neu in die exportierte Datei befinden sich die `Dev Home\Workspaces` Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="3a863-143">The exported file will be located on the system scratch drive in the `Dev Home\Workspaces` directory.</span></span>   
 
<a id="ID4EVF"></a>

   

### <a name="resizing-and-reordering-tools"></a><span data-ttu-id="3a863-144">Ändern der Größe und Neuanordnen von Tools</span><span class="sxs-lookup"><span data-stu-id="3a863-144">Resizing and Reordering Tools</span></span>  
   
  
<span data-ttu-id="3a863-145">Ändern der Größe oder Position eines Tools, verwenden die Kontextmenüschaltfläche (Ansichtsschaltfläche auf dem Controller), während des Titels hat den Fokus.</span><span class="sxs-lookup"><span data-stu-id="3a863-145">To change the size or position of a tool, use the context menu button (view button on your controller) while the title has focus.</span></span> <span data-ttu-id="3a863-146">Wählen Sie im Kontextmenü **Verschieben** oder **Größe ändern**.</span><span class="sxs-lookup"><span data-stu-id="3a863-146">From the context menu select **Move** or **Resize**.</span></span>   
 ![](images/dev_home_6.png)  
<a id="ID4EEG"></a>

   

### <a name="changing-theme-color-and-background-image"></a><span data-ttu-id="3a863-147">Ändern der Designfarbe und des Hintergrundbilds</span><span class="sxs-lookup"><span data-stu-id="3a863-147">Changing theme color and background image</span></span>  
   
  
<span data-ttu-id="3a863-148">Im Hauptmenü können Sie den **Arbeitsbereich** , und klicken Sie dann **Designfarbe ändern**auswählen.</span><span class="sxs-lookup"><span data-stu-id="3a863-148">From the Main Menu, you can select **Workspace** and then **Change theme color**.</span></span> <span data-ttu-id="3a863-149">Wählen Sie eine neue Farbe, und wählen Sie die **zu speichern** , um die Designfarbe zum Hervorheben des Fokus zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3a863-149">Select a new color and select **Save** to update the theme color used for focus highlighting.</span></span>   
 ![](images/dev_home_7.png)  
<a id="ID4EVG"></a>

   

### <a name="setting-the-default-application-for-a-package"></a><span data-ttu-id="3a863-150">Festlegen der Standard-Anwendungs für ein Paket</span><span class="sxs-lookup"><span data-stu-id="3a863-150">Setting the default application for a package</span></span>  
   
  
<span data-ttu-id="3a863-151">Wenn ein Paket mehrere Anwendungen enthält, können Dev Home Sie festlegen, die standardanwendung.</span><span class="sxs-lookup"><span data-stu-id="3a863-151">If a package contains multiple applications, Dev Home will allow you to set the default application to be launched.</span></span> <span data-ttu-id="3a863-152">Markieren Sie das Paket in-Start, und drücken Sie die **A** -Taste, um die Liste der verfügbaren Anwendungen zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3a863-152">Highlight the package in the launcher and press the **A** button to open the list of available applications.</span></span> <span data-ttu-id="3a863-153">Markieren Sie das Konto ein, die, das Sie als Standardeinstellung festlegen und drücken die **Ansicht** -Taste, und wählen Sie dann im Kontextmenü die Option **als Standard festlegen** möchten.</span><span class="sxs-lookup"><span data-stu-id="3a863-153">Highlight the one you wish to set as the default and press the **view** button, and then choose **Set as Default** from the context menu.</span></span>   
 ![](images/dev_home_setdefault.png)  
<a id="ID4EGH"></a>

   

### <a name="using-dev-home-to-register-and-launch-titles-from-a-network-share"></a><span data-ttu-id="3a863-154">Verwenden von Dev Home zu registrieren und starten die Titel von einer Netzwerkfreigabe</span><span class="sxs-lookup"><span data-stu-id="3a863-154">Using Dev Home to register and launch titles from a network share</span></span>  
   
  
<span data-ttu-id="3a863-155">Aus dem Launcher, am unteren Rand der installierten apps und Spieleliste können Sie die Option **Registrieren Sie ein Spiel von einer Netzwerkfreigabe** für die Remoteausführung einer registrieren loser Dateiversion eines Titels auswählen.</span><span class="sxs-lookup"><span data-stu-id="3a863-155">From the launcher, at the bottom of the installed apps and games list, you can select the option **Register a game from a network share** to run a loose file version of a title remotely.</span></span>   
 ![](images/dev_home_8.png)   
  
<span data-ttu-id="3a863-156">Sie können auf die Datei "appxmanifest.xml" für den Titel den Netzwerkpfad geben, die Sie registrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="3a863-156">You can then enter the network path to the appxmanifest.xml file for the title you wish to register.</span></span> <span data-ttu-id="3a863-157">Dev Home versucht, den Titel mit anderen vorhandenen Anmeldeinformationen für diese Freigabe registrieren und, wenn erforderlich für neue Netzwerkanmeldeinformationen fordert.</span><span class="sxs-lookup"><span data-stu-id="3a863-157">Dev Home will attempt to register the title using any existing credentials for that share, and if needed will prompt for new network credentials.</span></span> <span data-ttu-id="3a863-158">Wenn Sie zusätzliche Freigaben (z. B. um auf einem anderen Server auf Ressourcen zuzugreifen, die symbolisch verknüpft) zugreifen müssen, müssen Sie diese über die folgenden Option hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3a863-158">If you need to access additional shares (for example to access symbolically linked resources on a separate server) then you will need to add those via the option below.</span></span>   
   
  
<span data-ttu-id="3a863-159">Sie können diese gespeicherten Anmeldeinformationen verwalten (und Hinzufügen von weiteren) auf der Konsole über das Hauptmenü **Verwalten der Netzwerkanmeldeinformationen** Option.</span><span class="sxs-lookup"><span data-stu-id="3a863-159">You can manage these stored credentials (and add additional ones) on the console via the main menu's **Manage network credentials** option.</span></span>   
 ![](images/dev_home_9.png)   
  
<span data-ttu-id="3a863-160">Die Anmeldeinformationen derzeit auf der Konsole anzeigen, bearbeiten Anmeldeinformationen, indem Sie den Pfad der Anmeldeinformationen auswählen und auf **eine** Schaltfläche klicken, und Entfernen von Anmeldeinformationen den Link entfernen und durch Klicken auf **eine** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="3a863-160">You can view the credentials currently on the console, edit credentials by selecting the path of the credential and clicking **A** button and remove a credential by selecting the remove link and clicking **A** button.</span></span>   
   
<a id="ID4EGAAC"></a>

   

## <a name="in-this-section"></a><span data-ttu-id="3a863-161">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="3a863-161">In this section</span></span>  
  
[<span data-ttu-id="3a863-162">Startseite (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="3a863-162">Home Page (Dev Home)</span></span>](devhome-home.md)  


<span data-ttu-id="3a863-163">&nbsp;&nbsp;Bietet schnellen Zugriff auf die Aufgaben, die die Entwicklung auf einer routinemäßig ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="3a863-163">&nbsp;&nbsp;Provides quick access to the tasks that are routinely performed on a development console.</span></span> 
  
  
[<span data-ttu-id="3a863-164">Xbox Live-Seite (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="3a863-164">Xbox Live Page (Dev Home)</span></span>](devhome-live.md)  


<span data-ttu-id="3a863-165">&nbsp;&nbsp;Multiplayer-Informationen erfasst und zeigt den aktuellen Status des Xbox Live-Diensts.</span><span class="sxs-lookup"><span data-stu-id="3a863-165">&nbsp;&nbsp;Captures multiplayer information and displays the current status of the Xbox Live service.</span></span> 
  
  
[<span data-ttu-id="3a863-166">Seite "Einstellungen" (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="3a863-166">Settings Page (Dev Home)</span></span>](devhome-settings.md)  


<span data-ttu-id="3a863-167">&nbsp;&nbsp;Bietet Zugriff auf verschiedene Einstellungen für die entwicklungskonsole.</span><span class="sxs-lookup"><span data-stu-id="3a863-167">&nbsp;&nbsp;Provides access to various settings for the development console.</span></span> 
  
  
[<span data-ttu-id="3a863-168">Aufzeichnen von Medien Seite (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="3a863-168">Media Capture Page (Dev Home)</span></span>](devhome-capture.md)  


<span data-ttu-id="3a863-169">&nbsp;&nbsp;Die Seite **für die medienaufnahme** von Dev Home erfasst Video des Titels, die derzeit auf der Konsole ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3a863-169">&nbsp;&nbsp;The **Media capture** page of Dev Home captures video of the title that is currently running on the console.</span></span> 
  
  
[<span data-ttu-id="3a863-170">Netzwerkseite (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="3a863-170">Networking Page (Dev Home)</span></span>](devhome-networking.md)  


<span data-ttu-id="3a863-171">&nbsp;&nbsp;Simuliert verschiedene Netzwerke Bedingungen für die Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="3a863-171">&nbsp;&nbsp;Simulates various networking conditions for troubleshooting purposes.</span></span> 
  
  
[<span data-ttu-id="3a863-172">Seite "Performance" (Dev Home)</span><span class="sxs-lookup"><span data-stu-id="3a863-172">Performance Page (Dev Home)</span></span>](devhome-performance.md)  


<span data-ttu-id="3a863-173">&nbsp;&nbsp;Verschiedene Festplatten-Aktivität und CPU-Nutzung Bedingungen für die Problembehandlung simuliert.</span><span class="sxs-lookup"><span data-stu-id="3a863-173">&nbsp;&nbsp;Simulates various disk activity and CPU usage conditions for troubleshooting purposes.</span></span> 
 