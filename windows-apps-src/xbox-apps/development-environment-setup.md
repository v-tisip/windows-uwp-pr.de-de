---
author: Mtoepke
title: "Einrichten der Umgebung für die UWP-Entwicklung auf Xbox"
description: "Schritte zum Einrichten und Testen der Umgebung für die UWP-Entwicklung auf Xbox"
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: 8801c0d9-94a5-41a2-bec3-14f523d230df
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 93319caaa16afe84a897dbc4bd6370a5cef3cdd1
ms.lasthandoff: 02/08/2017

---

# <a name="set-up-your-uwp-on-xbox-development-environment"></a>Einrichten der UWP-Entwicklungsumgebung auf Xbox

Die Umgebung für die UWP-Entwicklung (Universelle Windows-Plattform) auf Xbox besteht aus einem Entwicklungscomputer, der über ein lokales Netzwerk mit einer Xbox One-Konsole verbunden ist.
Der Entwicklungscomputer erfordert Windows 10, Visual Studio 2015 Update 2, Windows 10 SDK Preview Build 14295 und eine Reihe von Unterstützungstools.


In diesem Artikel werden die Schritte zum Einrichten und Testen der Entwicklungsumgebung beschrieben.

## <a name="visual-studio-setup"></a>Einrichten von Visual Studio

1. Installieren Sie Visual Studio 2015 Update 2 oder höher. Weitere Informationen und Downloads für die Installation finden Sie unter [Downloads und Tools für Windows 10](https://dev.windows.com/downloads).

1. Wenn Sie Visual Studio 2015 Update 2 installieren, stellen Sie sicher, dass das Kontrollkästchen **Entwicklungstools für universelle Windows-Apps** aktiviert ist.

  ![Installieren von Visual Studio 2015 Update 2](images/vs_install_tools.png)

## <a name="windows-10-sdk-setup"></a>Einrichten des Windows 10 SDK

Installieren Sie das aktuelle Windows 10 SDK Preview Build. Informationen zur Installation finden Sie unter [Herunterladen von Insider Preview-Updates für Entwickler](http://go.microsoft.com/fwlink/p/?LinkId=780552).

> [!IMPORTANT]
> Sie müssen das aktuelle SDK installieren, _nicht_ jedoch die aktuelle Windows Insider Preview-Version des Betriebssystems.

## <a name="enabling-developer-mode"></a>Aktivieren des Entwicklermodus

Bevor Sie Anwendungen von Ihrem Entwicklungscomputer bereitstellen können, müssen Sie den Entwicklermodus über das Windows-Menü aktivieren: Einstellungen/Update und Sicherheit/Für Entwickler/Entwicklermodus.

## <a name="setting-up-your-xbox-one"></a>Einrichten Ihrer Xbox One

Bevor Sie eine App auf Ihrer Xbox One bereitstellen können, muss ein Benutzer auf der Konsole angemeldet sein. Sie können entweder ein vorhandenes Xbox Live-Konto verwenden oder ein neues Konto für Ihre Konsole im Entwicklermodus erstellen. 

## <a name="create-your-first-application"></a>Erstellen Ihrer ersten Anwendung

1. Stellen Sie sicher, dass sich der Entwicklungscomputer in demselben lokalen Netzwerk wie die gewünschte Xbox One befindet. Dies bedeutet normalerweise, dass beide denselben Router verwenden und sich im gleichen Subnetz befinden. Es wird eine drahtgebundene Netzwerkverbindung empfohlen.

1. Stellen Sie sicher, dass sich die Xbox One-Konsole im Entwicklermodus befindet.  Weitere Informationen finden Sie unter [Aktivieren des Entwicklermodus auf Xbox One](devkit-activation.md).

1. Legen Sie die Programmiersprache fest, die Sie für Ihre UWP-App verwenden möchten.

1. Wählen Sie auf dem Entwicklungscomputer **Neues Projekt** und dann **Windows/Universell/Leere App** aus.

### <a name="starting-a-c-project"></a>Starten eines C#-Projekts

  ![Dialogfeld „Neues Projekt“](images/vs_universal_blank.jpg)

1. Wählen Sie im Dialogfeld **Neues universelle Windows-Projekt** die Standardoptionen aus. Wenn das Dialogfeld **Entwicklermodus** angezeigt wird, klicken Sie auf **OK**. Es wird eine neue leere App erstellt.

1. Konfigurieren Sie die Entwicklungsumgebung für das Remotedebuggen:

  1. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.
  1. Ändern Sie auf der Registerkarte **Debuggen** die Option **Plattform** in **Aktiv (x64)**. (x86 wird nicht mehr als Plattform auf Xbox unterstützt.)   
  1. Ändern Sie **Zielgerät** zu **Remotecomputer**.
  1. Geben Sie in **Remotecomputer** die System-IP-Adresse oder den Hostnamen der Xbox One-Konsole ein. Informationen zum Ermitteln der IP-Adresse oder des Hostnamens finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).
  1. Wählen Sie in der Dropdownliste **Authentifizierungsmodus** den Eintrag **Universell (unverschlüsseltes Protokoll)** aus.

    ![C#-Eigenschaftenseiten für „Leere App“](images/vs_remote.jpg)

### <a name="starting-a-c-project"></a>Starten eines C++-Projekts

  ![C++-Projekt](images/vs_universal_cpp_blank.jpg)

1. Wählen Sie im Dialogfeld **Neues universelle Windows-Projekt** die Standardoptionen aus. Wenn das Dialogfeld **Entwicklermodus** angezeigt wird, klicken Sie auf **OK**. Es wird eine neue leere App erstellt.

1. Konfigurieren Sie die Entwicklungsumgebung für das Remotedebuggen:

   1. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.
   1. Ändern Sie **Zu startender Debugger** auf der Registerkarte **Debuggen** in **Remotecomputer**.
   1. Geben Sie in **Computername** die System-IP-Adresse oder den Hostnamen der Xbox One-Konsole ein. Informationen zum Ermitteln der IP-Adresse oder des Hostnamens finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).
   1. Wählen Sie in der Dropdownliste **Authentifizierungstyp** den Eintrag **Universell (unverschlüsseltes Protokoll)** aus.

    ![C++-Eigenschaftenseiten für „Leere App“](images/vs_remote_cpp.jpg)

### <a name="pin-pair-your-device-with-visual-studio"></a>Koppeln des Geräts per PIN mit Visual Studio

1. Speichern Sie die Einstellungen, und stellen Sie sicher, dass sich die Xbox One-Konsole im Entwicklermodus befindet.

1. Drücken Sie F5.

1. Wenn dies Ihre erste Bereitstellung ist, werden Sie in einem Dialogfeld in Visual Studio aufgefordert, Ihr Gerät per PIN zu koppeln.

  1. Um eine PIN abzurufen, öffnen Sie auf der Startseite der Xbox One-Konsole **Dev Home**.
  1. Wählen Sie **Mit Visual Studio koppeln** aus.

    ![Dialogfeld „Mit Visual Studio koppeln“](images/devhome_visualstudio.png)

  1. Geben Sie im Dialogfeld **Mit Visual Studio koppeln** die PIN ein. Die folgende PIN ist nur ein Beispiel und stimmt nicht mit Ihrer PIN überein.

    ![Dialogfeld „Mit Visual Studio per PIN koppeln“](images/devhome_pin.png)

  1. Gegebenenfalls auftretende Bereitstellungsfehler werden im Fenster **Ausgabe** angezeigt.

Herzlichen Glückwunsch! Sie haben Ihre erste UWP-App auf Xbox erfolgreich erstellt und bereitgestellt!



## <a name="see-also"></a>Weitere Informationen
- [Aktivieren des Entwicklermodus auf Xbox One](devkit-activation.md)  
- [Downloads und Tools für Windows 10](https://dev.windows.com/downloads)  
- [Insider Preview-Updates für Entwickler herunterladen](http://go.microsoft.com/fwlink/?LinkId=780552)  
- [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md) 
- [UWP auf Xbox One](index.md)

----

