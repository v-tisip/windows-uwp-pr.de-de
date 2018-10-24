---
author: PatrickFarley
ms.assetid: 78D833B9-E528-4BCA-9C48-A757F17E6C22
title: Zertifizierungskit für Windows-Apps
description: Ihre Anwendung die beste Chance, veröffentlicht Microsoft Store oder zertifizierten Windows überprüfen und Testen vor Ort vor dem Übermitteln für die Zertifizierung. In diesem Thema wird erläutert, wie Sie das Zertifizierungskit für Windows-Apps installieren und ausführen.
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10 Uwp, Zertifizierung
ms.localizationpriority: medium
ms.openlocfilehash: b7a72a89704aa3768cc43cdfbb75b620bae303e3
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5468937"
---
# <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps



Zu Ihre App [Windows zertifiziert](https://msdn.microsoft.com/windows/desktop/jj134964.aspx) für [Microsoft Store](https://msdn.microsoft.com/library/windows/apps/Hh694062)vorbereiten, sollten Sie überprüfen und testen es zuerst lokal. In diesem Thema wird das Installieren und Ausführen von [Windows Zertifizierungskit](http://go.microsoft.com/fwlink/p/?LinkID=309666) um sicherzustellen, dass Ihre Anwendung sicher und effizient veranschaulicht.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für das Testen einer universellen Windows-App:

-   Installieren und Ausführen von Windows10.
-   Sie installieren [Windows Zertifizierungskit Version 10]( http://go.microsoft.com/fwlink/p/?LinkID=309666)enthalten im Windows Software Development Kit (SDK) für Windows10.
-   Sie müssen [Ihr Gerät für die Entwicklung aktivieren](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development).
-   Sie müssen die zu testende Windows-App auf Ihrem Computer bereitstellen.

**Hinweis zu direkten Upgrades**

Beim Installieren einer neueren Version des [Zertifizierungskits für Windows-Apps]( http://go.microsoft.com/fwlink/p/?LinkID=309666) werden alle vorherigen Versionen des Kits ersetzt, die auf dem Computer installiert sind.

## <a name="validate-your-windows-app-using-the-windows-app-certification-kit-interactively"></a>Interaktive Überprüfung der Windows-App mit dem Zertifizierungskit für Windows-Apps

1.  Suchen Sie im Startmenü**** nach den Einträgen **Apps** und **Windows Kits**, und klicken Sie auf die Option für das Zertifizierungskit für Windows-Apps****.

2.  Wählen Sie im Zertifizierungskit für Windows-Apps die Kategorie der auszuführenden Überprüfung aus. Beispiel: Wenn Sie eine Windows-App überprüfen, wählen Sie die Option zum **Überprüfen einer Windows-App** aus.

    Sie können direkt zur jeweiligen App navigieren oder die App in einer Liste auf der Benutzeroberfläche auswählen. Bei der erstmaligen Ausführung des Zertifizierungskits für Windows-Apps werden auf der Benutzeroberfläche alle Windows-Apps aufgelistet, die auf dem Computer installiert sind. Bei nachfolgenden Ausführungen werden die Windows-Apps angezeigt, die Sie bereits überprüft haben. Falls die zu testende App nicht in der Liste enthalten ist, können Sie auf **Meine App ist nicht aufgeführt** klicken, um eine Liste aller installierten Apps im System anzuzeigen.

3.  Nachdem Sie die zu testende App eingegeben oder ausgewählt haben, klicken Sie auf **Weiter**.

4.  Auf dem nächsten Bildschirm sehen Sie den Testworkflow für die App, die Sie testen möchten. Wenn ein Test in der Liste deaktiviert ist, kann er nicht für Ihre Umgebung angewendet werden. Wenn Sie eine z.B. einer Windows10-App unter Windows7 testen, werden nur statische Tests für den Workflow angewendet. Beachten Sie, dass Microsoft Store alle Tests aus diesem Workflow gelten. Wählen Sie aus, welche Tests Sie ausführen möchten, und klicken Sie dann auf **Weiter**.

    Das Zertifizierungskit für Windows-Apps beginnt mit dem Überprüfen der App.

5.  Geben Sie den Pfad zu dem Ordner an, in dem der Testbericht gespeichert werden soll, wenn Sie nach dem Testen dazu aufgefordert werden.

    Vom Zertifizierungskit für Windows-Apps werden ein XML-Bericht und ein HTML-Bericht erstellt und in diesem Ordner gespeichert.

6.  Öffnen Sie die Berichtsdatei, und überprüfen Sie die Ergebnisse des Tests.

**Hinweis**Sie Visual Studio verwenden, können Sie Windows-Zertifizierungskit können ausführen, wenn app-Paket erstellen. Informationen zur Vorgehensweise finden Sie unter [Verpacken von UWP-Apps](https://msdn.microsoft.com/library/windows/apps/Mt627715).

 

## <a name="validate-your-windows-app-using-the-windows-app-certification-kit-from-a-command-line"></a>Überprüfung der Windows-App mit dem Zertifizierungskit für Windows-Apps über eine Befehlszeile

**Wichtige**Zertifizierungskit von Windows muss im Kontext einer aktiven Benutzer-Sitzung ausgeführt werden.

1.  Navigieren Sie im Befehlsfenster zum Verzeichnis mit dem Zertifizierungskit für Windows-Apps.

    **Hinweis**  der Standardpfad ist C:\\Program Files\\Windows Kits\\10\\App Zertifizierung Kit\\.

2.  Geben Sie die folgenden Befehle in dieser Reihenfolge ein, um eine App zu testen, die bereits auf dem Testcomputer installiert ist:

    `appcert.exe reset`

    `appcert.exe test -packagefullname [package full name] -reportoutputpath [report file name]`

    Wenn Sie App nicht installiert ist, können Sie die folgenden Befehle verwenden. Das Zertifizierungskit für Windows-Apps öffnet das Paket und wendet den entsprechenden Testworkflow an:

    `appcert.exe reset`

    `appcert.exe test -appxpackagepath [package path] -reportoutputpath [report file name]`

3.  Öffnen Sie nach dem Test die Berichtsdatei `[report file name]`, und überprüfen Sie die Testergebnisse.

**Hinweis**Zertifizierungskit von Windows von einem Dienst ausgeführt werden kann, aber der Dienst muss einleiten Kit innerhalb einer Sitzung aktiven Benutzer und kann nicht in Session0 ausgeführt werden.

**Hinweis**  Weitere Informationen zu den Windows-Zertifizierungskit Geben Sie den Befehl `appcert.exe /?`

## <a name="testing-with-a-low-power-computer"></a>Testen mit einem Computer mit geringem Energieverbrauch

Die Leistungstestgrenzen des Zertifizierungskits für Windows-Apps basieren auf der Leistung eines Computers mit geringem Energieverbrauch.

Die Eigenschaften des Computers, auf dem der Test ausgeführt wird, können die Testergebnisse beeinflussen. Um festzustellen, ob Ihre Anwendung [Microsoft Richtlinien](https://msdn.microsoft.com/library/windows/apps/Dn764944)entspricht, empfehlen wir, Ihre Anwendung auf einem Computer Energiesparmodus wie ein Intel Atom Prozessor mit einer Auflösung von 1366 x 768 (oder höher) und ein schwer zu testen Laufwerk (im Gegensatz zu einem Solid-State-Festplatte)

Da Computer mit geringem Energieverbrauch weiterentwickelt werden, können sich die Leistungsmerkmale im Laufe der Zeit ändern. Finden Sie aktuelle [Richtlinien für Microsoft](https://msdn.microsoft.com/library/windows/apps/Dn764944) , und Testen Sie Ihre Anwendung mit der aktuellsten Version der Zertifizierung Windows App, um sicherzustellen, dass Ihre Anwendung Leistung Erfordernissen entspricht.

## <a name="related-topics"></a>Verwandte Themen

* [Tests im Zertifizierungskit für Windows-Apps](windows-app-certification-kit-tests.md)
* [Microsoft Store-Richtlinien](https://msdn.microsoft.com/library/windows/apps/Dn764944)
 

 




