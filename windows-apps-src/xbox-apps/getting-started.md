---
author: Mtoepke
title: Erste Schritte bei der Entwicklung von UWP-Apps auf Xbox One
description: Einrichten des Computers und der Xbox One für die UWP-Entwicklung
ms.author: scotmi
ms.date: 10/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: da260b4f9f5f50d97d39af883217dfbae91a566e
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4564957"
---
# <a name="getting-started-with-uwp-app-development-on-xbox-one"></a>Erste Schritte bei der Entwicklung von UWP-Apps auf Xbox One

Führen Sie die folgenden Schritte **sorgfältig** aus, um Ihren PC und Xbox One erfolgreich für die Entwicklung für die Universelle Windows-Plattform einzurichten. Lesen Sie nach der Einrichtung die Seite [UWP für Xbox One](index.md), um mehr über den Entwicklermodus auf Xbox One und das Erstellen von UWP-Apps zu erfahren. 

## <a name="before-you-start"></a>Vorbereitung

Bevor Sie beginnen, müssen Sie die folgenden Schritte ausführen:
-   Richten Sie einen PC mit der neuesten Version von Windows 10.
<!-- -  Install Microsoft Visual Studio 2015 Update 3 or Microsoft Visual Studio 2017.

    > [!NOTE]
    > Visual Studio 2017 is required if you are using the Windows 10, build 15063 SDK. -->

- Sorgen Sie für mindestens 5GB freien Speicherplatz auf Ihrer Xbox One.

## <a name="setting-up-your-development-pc"></a>Einrichten des Entwicklungs-PCs

1.  Installieren Sie Visual Studio 2015 Update 3 oder Visual Studio 2017.

    Wenn Sie Visual Studio 2015 Update 3 installieren, stellen Sie sicher, dass Sie **benutzerdefinierte** Installation auswählen und aktivieren Sie das Kontrollkästchen **Entwicklungstools für universelle Windows App** – es nicht Teil der Standardinstallation ist. Achten Sie als C++-Entwickler darauf, **Benutzerdefinierte Installation** auszuwählen. Wählen Sie **C++** aus.

    Wenn Sie Visual Studio2017 erneut installieren, stellen Sie sicher, dass Sie die Arbeitsauslastung **Entwicklung für die universelle Windows-Plattform** auswählen. Wenn Sie C++-Entwickler im Bereich " **Zusammenfassung** " auf der rechten Seite sind in der **Entwicklung von universellen Windows-Plattform**, stellen Sie sicher, dass Sie die Kontrollkästchen für die **universelle Windows-Plattform C++-Tools** auswählen. Es ist nicht Teil der Standardinstallation.

    Weitere Informationen finden Sie in der [Einrichten Ihrer UWP-Entwicklungsumgebung auf Xbox](development-environment-setup.md).

2.  Installieren Sie das neueste [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

3.  Aktivieren des Entwicklermodus für Ihren Entwicklungs-PC (**Einstellungen / Update und Sicherheit / für Entwickler / Entwicklerfunktionen / Entwicklermodus**).

Nachdem Ihr Entwicklungs-PC nun bereit ist, können Sie sich dieses Video ansehen oder weiterlesen, um zu erfahren, wie Sie Ihre Xbox One für die Entwicklung einrichten und darauf eine UWP-App erstellen und bereitstellen.
</br>
</br>
<iframe src="https://channel9.msdn.com/Events/Xbox/App-Dev-on-Xbox/Get-started-with-App-Dev-on-Xbox/player#time=51s:paused" width="600" height="338"  allowFullScreen frameBorder="0"></iframe>

## <a name="setting-up-your-xbox-one-console"></a>Einrichten Ihrer Xbox One-Konsole

1.  Aktivieren Sie den Entwicklermodus auf der Xbox One. Herunterladen Sie die app, erhalten Sie den Aktivierungscode, und geben Sie ihn in das [Verwalten von Xbox One-Konsolen](https://partner.microsoft.com/xboxactivate) -Seite im Dev Center-Konto. Weitere Informationen finden Sie unter [Aktivierung des Xbox One-Entwicklermodus](devkit-activation.md). 

2.  Öffnen Sie die **DEVMODE-Aktivierungs** -app, und wählen Sie **wechseln und neu starten**. Herzlichen Glückwunsch! Ihre Xbox One befindet sich nun im Entwicklermodus.
  
  > [!NOTE]
  > Ihre Einzelhandelsspiele und -Apps werden im Entwicklermodus nicht ausgeführt, die von Ihnen erstellten Apps oder Spiele werden jedoch ausgeführt. Wechseln Sie zurück in den Einzelhandelsmodus, um Ihre Lieblingsspiele und -Apps auszuführen.
    
  > [!NOTE]
  > Damit Sie eine App auf der Xbox One-Konsole im Entwicklermodus bereitstellen können, muss ein Benutzer an der Konsole angemeldet sein. Sie können entweder ein vorhandenes Xbox Live-Konto verwenden oder ein neues Konto für Ihre Konsole im Entwicklermodus erstellen. 

## <a name="creating-your-first-project-in-visual-studio"></a>Erstellen Ihres ersten Projekts in Visual Studio

Ausführlichere Informationen finden Sie in der [Einrichten Ihrer UWP-Entwicklungsumgebung auf Xbox](development-environment-setup.md).

1.  **Für c#**: Erstellen eines neuen universellen Windows-Projekts, und klicken Sie im **Projektmappen-Explorer**mit der Maustaste des Projekts, und wählen Sie **Eigenschaften**. Wählen Sie die Registerkarte " **Debuggen** ", ändern Sie **Zielgerät** auf **Remotecomputer**, geben Sie die IP-Adresse oder den Hostnamen der Xbox One-Konsole in das Feld **Remotecomputer** und wählen Sie in der ** **universell (unverschlüsseltes Protokoll)** Authentifizierungsmodus** Dropdown-Liste.   

    Die IP-Adresse Ihrer Xbox One finden Sie, indem Sie Dev Home auf der Konsole starten (die große Kachel auf der rechten Seite der Startseite) und in der oberen linken Ecke suchen. Weitere Informationen zu Dev Home finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).  

2.  **Für C++ und HTML/Javascript-Projekte**: Sie folgen einen ähnlichen Pfad zu C#-Projekten, aber in den Projekteigenschaften wechseln Sie zu der Registerkarte " **Debuggen** ", wählen Sie in den Debugger so öffnen Sie die Dropdown-Liste, geben Sie die IP-Adresse oder den Hostnamen der **Remotecomputer** die die Konsole in das Namensfeld **Computer** , und wählen **universell (unverschlüsseltes Protokoll)** im Feld **Authentifizierungstyp** .

3. Wählen Sie links neben die grüne Wiedergabeschaltfläche in der oberen Menüleiste **X64** aus der Dropdownliste.
   
4.  Wenn Sie F5 drücken, wird Ihre App erstellt, und die Bereitstellung auf der Xbox One wird gestartet.
  
5.  Wenn Sie diesen Vorgang zum ersten Mal durchführen, fordert Visual Studio Sie zur Eingabe einer PIN für Ihre Xbox One auf. Indem Sie Dev Home auf Ihrer Xbox One starten und die Schaltfläche " **Visual Studio-Pin anzeigen** " auswählen, können Sie eine PIN abrufen.
  
6.  Nach der Kopplung wird die Bereitstellung der App gestartet. Beim ersten Mal kann diese Bereitstellung ein wenig langsam sein (da alle Tools auf Ihre Xbox kopiert werden müssen). Wenn dieser Vorgang jedoch länger als wenige Minuten dauert, ist wahrscheinlich ein Problem aufgetreten. Stellen Sie sicher, dass Sie alle oben genannten Schritte ausgeführt haben – haben Sie den **Authentifizierungsmodus** auf **Universell** festgelegt? Vergewissern Sie sich außerdem, dass Sie eine drahtgebundene Netzwerkverbindung mit der Xbox One verwenden.  

7. Lehnen Sie sich nun ganz entspannt zurück. Viel Spaß mit Ihrer ersten App auf der Konsole!  

## <a name="thats-it"></a>Das war's.

![Hello World](images/getting-started-hello-world.png)

## <a name="see-also"></a>Weitere Informationen  
- [Häufig gestellte Fragen](frequently-asked-questions.md)  
- [Bekannte Probleme mit UWP im Zusammenhang mit dem Xbox One-Entwicklerprogramm](known-issues.md)
- [UWP auf Xbox One](index.md) 
