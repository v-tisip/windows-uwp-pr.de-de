---
title: "Abrufen der Beispiele für die Universelle Windows-Plattform (UWP) von GitHub"
description: "Erfahren Sie, wie Sie die Beispiele für UWP-Features von GitHub herunterladen können."
author: JoshuaPartlow
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
ms.assetid: 393c5a81-ee14-45e7-acd7-495e5d916909
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 93dde6fe68275987c16562370ba277072e5467a9
ms.lasthandoff: 02/08/2017

---

#<a name="get-the-universal-windows-platform-uwp-samples-from-github"></a>Abrufen der Beispiele für die Universelle Windows-Plattform (UWP) von GitHub
Die Beispiele für UWP-Apps sind über Repositorys auf GitHub verfügbar. Wenn Sie zum ersten Mal mit UWP arbeiten, sollten Sie mit dem Repository für [Microsoft-/universelle Windows-Beispiele](https://github.com/Microsoft/Windows-universal-samples "Universal Windows Platform app samples GitHub repository") beginnen. In dessen Beispielen werden alle UWP-Features und ihre API-Verwendungsmuster veranschaulicht.  
![GitHub-UWP-Beispiel-Repository](images/GitHubUWPSamplesPage.png) Weitere Beispiele finden Sie im Bereich [Beispiele](https://developer.microsoft.com/windows/samples "Dev Center samples") im Dev Center.  

##<a name="download-the-code"></a>Code herunterladen
Informationen zum Herunterladen der Beispiele finden Sie unter [Repository](https://github.com/Microsoft/Windows-universal-samples "GitHub-Repository mit App-Beispielen für die Universelle Windows-Plattform"). Wählen Sie **Clone or download** und dann **Herunterladen der ZIP-Datei**. Oder klicken Sie einfach [hier](https://github.com/Microsoft/Windows-universal-samples/archive/master.zip "ZIP-Datei mit App-Beispielen für die Universelle Windows-Plattform herunterladen").

Die ZIP-Datei enthält stets die neuesten Beispiele. Sie benötigen zum Herunterladen kein GitHub-Konto. Wenn ein SDK-Update veröffentlicht wird oder wenn Sie alle aktuellen Änderungen/Ergänzungen übernehmen möchten, suchen Sie einfach nach der neuesten ZIP-Datei.

![Beispieldownload](images/SamplesDownloadButton.png)


> **Hinweis**: Für das Öffnen, Erstellen und Ausführen der UWP-Beispiele sind Visual Studio 2015 und das Windows SDK erforderlich. Wenn Visual Studio noch nicht installiert wurde, können Sie eine kostenlose Kopie von Visual Studio 2015 Community Edition mit Unterstützung für das Erstellen von UWP-Apps abrufen. Klicken Sie [hier](http://go.microsoft.com/fwlink/p/?LinkID=280676 "Windows-Entwicklungstools herunterladen").  
>
> Zudem sollten Sie sicherstellen, dass nicht nur einzelne Beispiele, sondern das gesamte Archiv entpackt wurde. Alle Beispiele erfordern den Archivordner „SharedContent“. Die Beispiele für UWP-Features verfügen über verknüpfte Dateien in Visual Studio, um das Duplizieren gemeinsam verwendeter Dateien zu vermeiden, z. B. von Beispieldateien für Vorlagen und Bildressourcen. Diese gemeinsamen Dateien werden im Ordner „SharedContent“ im Stammverzeichnis des Repositorys gespeichert. Der Verweis in den Projektdateien erfolgt über Links.

Öffnen Sie nach dem Herunterladen der ZIP-Datei die Beispiele in Visual Studio:

1.  Klicken Sie vor dem Extrahieren des Archivs mit der rechten Maustaste darauf, und wählen Sie **Eigenschaften** > **Blockierung aufheben** > **Übernehmen** aus. Entpacken Sie anschließend das Archiv in einen lokalen Ordner auf Ihrem Computer.

    ![Entpacktes Archiv](images/SamplesUnzip1.png)
2.  Im Beispielordner wird eine Reihe von Ordnern angezeigt, die jeweils ein Beispiel für UWP-Features enthalten.

    ![Beispielordner](images/SamplesUnzip2.png)

3.  Wählen Sie ein Beispiel wie z. B. Höhenmesser aus, um mehrere Ordner mit den unterstützten Sprachen anzuzeigen.

    ![Sprachordner](images/SamplesUnzip3.png)

4.  Wählen Sie die gewünschte Sprache (z. B. CS für C\#) aus. Es wird eine Visual Studio-Projektmappendatei angezeigt, die Sie in Visual Studio öffnen können.

    ![VS-Projektmappe](images/SamplesUnzip4.png)

## <a name="give-feedback-ask-questions-and-report-issues"></a>Geben Sie Feedback, stellen Sie Fragen und melden Sie Probleme

Wenn Sie Fragen oder Probleme haben, klicken Sie einfach auf die Registerkarte „Probleme“ im Repository, um ein neues Problem zu erstellen. Wir werden versuchen, zu helfen.

![Feedback-Bild](images/GitHubUWPSamplesFeedback.png)

