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
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7300135"
---
# <a name="developer-home-on-the-console-dev-home"></a>Entwickler-Startbildschirm auf der Konsole (Dev Home)
   
  
Dev Home ist ein Tool im Xbox One Development Kit entwickelt, um die Produktivität von Entwicklern unterstützen soll. Dev Home bietet Funktionen zum Verwalten und Konfigurieren Ihres Development Kit, Verwalten von Benutzern, installierten Titel starten und durchführen erfasst und erfasst. In zukünftigen Versionen, die wir weiterhin die Funktionalität zusätzliche Features, die basierend auf Ihr Feedback zu aktivieren und auch zum Aktivieren der Erweiterbarkeit und das Hinzufügen von eigene Tools zu erweitern.   
   
  
Wir sind sehr in Ihr Feedback zu Dev Home und die Szenarien, die Sie am besten sehen sie unterstützen möchten. Geben Sie Ihre Kommentare über das Menü der app unter **Feedback senden** beschriebenen Methoden oder über Ihre Entwickler Account Manager (Mutter).   
   
  
So starten Sie Dev Home auf der November 2015 oder höher Wiederherstellung  
 
   1. Öffnen Sie die Anleitung durch Verschieben nach links auf der Startseite, oder klicken auf die Schaltfläche Nexus double  
   1. Nach unten, um **Einstellungen** (das Zahnradsymbol)   
   1. Wählen Sie **Alle Einstellungen**  
   1. Wählen Sie auf **der Standard-Entwicklerseite** **Entwickler-Startbildschirm** (Symbol für die Startseite)   

 ![](images/dev_home_icons.png)   
  
Zeigen Sie auf frühere Recovery wählen Sie die Dev Home-Kachel auf der rechten Seite im Startbildschirm im **Inhalt ausgewähltes** oder die Anwendungsliste im Xbox One-Manager und starten Sie **Dev Home**.   
 ![](images/dev_home_1.png) 
<a id="ID4EBC"></a>

   

## <a name="user-interface"></a>Benutzeroberfläche  
   
  
Der Header der Dev Home-Benutzeroberfläche enthält die folgenden "auf einen Blick" wichtige Informationen zu den entwicklungskonsole:   
 
   *  **Konsolen-IP:** Die aktuelle IP-Adresse der Konsole.   
   *  **Konsolenname:** Die aktuelle Hostnamen der Konsole.  
   *  **Sandbox:** Der Name der Sandbox, der in die Konsole ist.  
   *  **Betriebssystemversion:** Die aktuelle Recovery-Version, die auf der Konsole ausgeführt wird.
   *  Aktuelle Systemzeit.   

   
  
Der Rest der Dev Home-Benutzeroberfläche ist in den folgenden Seiten unterteilt. Weitere Informationen zu den Tools auf diesen Seiten finden Sie die einzelnen Themen.   
 
   *  [Startseite](devhome-home.md)  
   *  [Xbox Live](devhome-live.md)  
   *  [Einstellungen](devhome-settings.md)  
   *  [Medienaufzeichnung](devhome-capture.md)  
   *  [Networking](devhome-networking.md)  
   *  [Leistung](devhome-performance.md)  

  
<a id="ID4EKE"></a>

   

## <a name="main-menu"></a>Hauptmenü  
   
  
Drücken Sie **die Menütaste** auf Ihrem Controller, können Sie das Hauptmenü zugreifen, das Konfiguration von den app-Workspace, die Verwaltung von Anmeldeinformationen für den Zugriff auf Netzwerkressourcen und Informationen zum Übermitteln von Feedback an die app ermöglicht.   
  
<a id="ID4EUE"></a>

   

## <a name="snap-mode-ux"></a>Andockmodus UX  
   
  
Mehrere vorhandene und zukünftige Tools in Dev Home, z. B. Netzwerke und Multiplayer-Spiele, dienen zur verwendet werden, angedockt auf der Seite, während Sie Ihre Titel ausgeführt werden, damit Sie haben einfachen Zugriff auf Tools beim Testen.   
   
  
Um Snap-Modus zuzugreifen, markieren Sie den Titel des entsprechenden Tools, drücken Sie die **Ansicht** -Taste auf dem Controller und wählen Sie aus dem Kontextmenü **Einrasten** :  
 ![](images/dev_home_4.png)   
  
Dev Home wird rechts angedockt. Sie können den Kontext umschalten, indem Sie wie gewohnt auf die Schaltfläche Nexus doppeltippen.  
 ![](images/dev_home_5.png)  
<a id="ID4EKF"></a>

   

## <a name="customizing-dev-home"></a>Anpassen von Dev Home  
   
  
Dev Home kann angepasst und personalisiert werden. Sie können die app entsprechend Ihren Workflow zu konfigurieren und speichern, die dann als Arbeitsbereich. Diesen Arbeitsbereich exportiert werden kann, und importierte, sodass Sie das Layout auf andere Konsolen als kopieren benötigt. Diese Optionen finden Sie im Hauptmenü unter **Arbeitsbereich**. Die Exportdatei befinden sich auf dem Systemlaufwerk neu in der `Dev Home\Workspaces` Verzeichnis.   
 
<a id="ID4EVF"></a>

   

### <a name="resizing-and-reordering-tools"></a>Ändern der Größe und Neuanordnen von Tools  
   
  
Ändern der Größe oder Position eines Tools, verwenden die Kontextmenüschaltfläche (Ansichtsschaltfläche auf dem Controller) während des Titels hat den Fokus. Wählen Sie im Kontextmenü **Verschieben** oder **Größe ändern**.   
 ![](images/dev_home_6.png)  
<a id="ID4EEG"></a>

   

### <a name="changing-theme-color-and-background-image"></a>Ändern der Designfarbe und des Hintergrundbilds  
   
  
Im Hauptmenü können Sie den **Arbeitsbereich** und dann **Designfarbe ändern**auswählen. Wählen Sie eine neue Farbe, und wählen Sie **Speichern** , um die Designfarbe zum Hervorheben des Fokus zu aktualisieren.   
 ![](images/dev_home_7.png)  
<a id="ID4EVG"></a>

   

### <a name="setting-the-default-application-for-a-package"></a>Festlegen der Standard-Anwendungs für ein Paket  
   
  
Enthält ein Paket mehrere Anwendungen, können Dev Home Sie festlegen, die standardanwendung gestartet werden. Markieren Sie das Paket in das Startprogramm, und drücken Sie die **A** -Taste, um die Liste der verfügbaren Anwendungen zu öffnen. Markieren Sie das Konto, die, das Sie als Standard festlegen und drücken die **Ansicht** -Taste und wählen Sie dann im Kontextmenü die Option **als Standard festlegen** möchten.   
 ![](images/dev_home_setdefault.png)  
<a id="ID4EGH"></a>

   

### <a name="using-dev-home-to-register-and-launch-titles-from-a-network-share"></a>Verwenden von Dev Home zu registrieren und starten die Titel von einer Netzwerkfreigabe  
   
  
Aus dem Launcher, am unteren Rand der installierten apps und Spieleliste können Sie die Option **Registrieren Sie ein Spiel von einer Netzwerkfreigabe** für die Remoteausführung einer losen Dateiversion eines Titels auswählen.   
 ![](images/dev_home_8.png)   
  
Sie können dann den Netzwerkpfad der Datei "appxmanifest.xml" für den Titel eingeben, die Sie registrieren möchten. Dev Home wird versucht, den Titel über alle vorhandenen Anmeldeinformationen für diese Freigabe registrieren und, wenn für die neuen Netzwerkanmeldeinformationen fordert erforderlich. Wenn Sie zusätzliche Freigaben (z. B. auf Ressourcen zugreifen, die symbolisch verknüpft auf einem anderen Server) zugreifen müssen, müssen Sie diese über die Option unterhalb hinzufügen.   
   
  
Sie können diese gespeicherten Anmeldeinformationen verwalten (und Hinzufügen von weiteren) auf der Konsole über das Hauptmenü **Verwalten der Netzwerkanmeldeinformationen** Option.   
 ![](images/dev_home_9.png)   
  
Sie können die Anmeldeinformationen derzeit auf der Konsole anzeigen, zu bearbeiten Anmeldeinformationen durch auswählen den Pfad der Anmeldeinformationen, und klicken auf **eine** Schaltfläche und Anmeldeinformationen zu entfernen, indem den Link entfernen und dann auf **eine** Schaltfläche.   
   
<a id="ID4EGAAC"></a>

   

## <a name="in-this-section"></a>In diesem Abschnitt  
  
[Startseite (Dev Home)](devhome-home.md)  


&nbsp;&nbsp;Bietet schnellen Zugriff auf die Aufgaben, die für eine entwicklungskonsole routinemäßig durchgeführt werden. 
  
  
[Xbox Live-Seite (Dev Home)](devhome-live.md)  


&nbsp;&nbsp;Multiplayer-Informationen erfasst und zeigt den aktuellen Status des Xbox Live-Diensts. 
  
  
[Seite "Einstellungen" (Dev Home)](devhome-settings.md)  


&nbsp;&nbsp;Bietet Zugriff auf verschiedene Einstellungen für die entwicklungskonsole. 
  
  
[Aufzeichnen von Medien Seite (Dev Home)](devhome-capture.md)  


&nbsp;&nbsp;Der Seite " **medienerfassung** " von Dev Home erfasst Video des Titels, die derzeit auf der Konsole ausgeführt wird. 
  
  
[Netzwerkseite (Dev Home)](devhome-networking.md)  


&nbsp;&nbsp;Simuliert verschiedene Netzwerke Bedingungen für die Problembehandlung. 
  
  
[Seite "Performance" (Dev Home)](devhome-performance.md)  


&nbsp;&nbsp;Simuliert verschiedene Festplatten-Aktivität und CPU-Nutzung Bedingungen für die Problembehandlung. 
 