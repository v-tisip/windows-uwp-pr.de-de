---
author: mcleanbyron
ms.assetid: cc24ba75-a185-4488-b70c-fd4078bc4206
description: "Hier erfahren Sie, wie Sie die AdScheduler-Klasse verwenden, um Videoinhalten Werbung hinzuzufügen."
title: "Hinzufügen von Werbung zu Videoinhalten in HTML 5 und JavaScript"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Anzeigen, Werbung, Video, Planer, JavaScript"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: b42b57f385857301bb74037dbb5c0c7200653316
ms.lasthandoff: 02/07/2017

---

# <a name="add-advertisements-to-video-content-in-html-5-and-javascript"></a>Hinzufügen von Werbung zu Videoinhalten in HTML 5 und JavaScript


In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie die [AdScheduler](https://msdn.microsoft.com/library/windows/apps/mt732197.aspx)-Klasse zum Hinzufügen von Werbung zu Videoinhalten in einer App für die universelle Windows-Plattform (UWP) verwenden, die mit JavaScript und HTML geschrieben wurde.

>**Hinweis**&nbsp;&nbsp;Diese Funktion wird derzeit nur für UWP-Apps unterstützt, die mit JavaScript und HTML geschrieben wurden.

[AdScheduler](https://msdn.microsoft.com/library/windows/apps/mt732197.aspx) funktioniert mit progressiven Medien und Streamingmedien und nutzt Video Ad Serving Template (VAST) 2.0/3.0 nach IAB-Standard und VMAP-Nutzlastformate. Durch die Verwendung von Standards ist [AdScheduler](https://msdn.microsoft.com/library/windows/apps/mt732197.aspx) agnostisch gegenüber dem Anzeigendienst, mit dem die Interaktion erfolgt.

Werbung für Videoinhalte variiert in Abhängigkeit davon, ob das Programm kürzer als zehn Minuten (kurzes Format) oder länger als zehn Minuten (langes Format) ist. Die Einrichtung des letzteren Formats für den Dienst ist zwar komplizierter, aber es besteht eigentlich kein Unterschied darin, wie der clientseitige Code geschrieben wird. Wenn [AdScheduler](https://msdn.microsoft.com/library/windows/apps/mt732197.aspx) eine VAST-Nutzlast mit einer einzelnen Werbeanzeige anstelle eines Manifests empfängt, wird dies so behandelt, als ob das Manifest eine einzelne Pre-Roll-Anzeige (eine Unterbrechung bei 00:00) aufgerufen hat.

## <a name="prerequisites"></a>Voraussetzungen

* Installieren Sie das [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) mit Visual Studio 2015.

* In Ihrem Projekt muss das [MediaPlayer](https://github.com/Microsoft/TVHelpers/wiki/MediaPlayer-Overview)-Steuerelement verwendet werden, um die Videoinhalte bereitstellen zu können, für die die Anzeigen eingeplant werden. Dieses Steuerelement ist in der Bibliotheksammlung [TVHelpers](https://github.com/Microsoft/TVHelpers) von Microsoft auf GitHub verfügbar.

  Das folgende Beispiel zeigt, wie Sie einen [MediaPlayer](https://github.com/Microsoft/TVHelpers/wiki/MediaPlayer-Overview) im HTML-Markup deklarieren. Dieser Markupcode gehört normalerweise in den Abschnitt `<body>` in der Datei „index.html“ (oder einer anderen HTML-Datei, je nach Eignung für Ihr Projekt).

  > [!div class="tabbedCodeSnippets"]
  ``` html
  <div id="MediaPlayerDiv" data-win-control="TVJS.MediaPlayer">
    <video src="URL to your content">
    </video>
  </div>
  ```

  Im folgenden Beispiel wird veranschaulicht, wie Sie einen [MediaPlayer](https://github.com/Microsoft/TVHelpers/wiki/MediaPlayer-Overview) in JavaScript-Code einrichten.

  > [!div class="tabbedCodeSnippets"]
  [!code-javascript[TrialVersion](./code/AdvertisingSamples/AdSchedulerSamples/js/js/main.js#Snippet1)]

## <a name="how-to-use-the-adscheduler-class-in-your-code"></a>Verwenden der AdScheduler-Klasse im Code

1. Öffnen Sie in Visual Studio Ihr Projekt, oder erstellen Sie ein neues Projekt.

2. Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, müssen Sie eine architekturspezifische Buildausgabe verwenden (z. B. **X86**) und das Projekt entsprechend aktualisieren. Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, können Sie bei den folgenden Schritten keinen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen. Weitere Informationen finden Sie unter [Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden](known-issues-for-the-advertising-libraries.md#reference_errors).

3. Fügen Sie Ihrem Projekt einen Verweis auf die Bibliothek **Microsoft Advertising SDK für JavaScript** hinzu.

  a. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.

  b. Erweitern Sie im **Verweis-Manager** den Knoten **Universal Windows**, klicken Sie auf **Erweiterungen**, und wählen Sie dann das Kontrollkästchen neben **Microsoft Advertising SDK für JavaScript** (Version 10.0).

  c. Klicken Sie im **Verweis-Manager** auf „OK“.

4.  Fügen Sie dem Projekt die Datei „AdScheduler.js“ hinzu:

  a.  Klicken Sie in Visual Studio auf **Projekt** und **NuGet-Pakete verwalten**.

  b.  Geben Sie im Suchfeld den Suchbegriff **Microsoft.StoreServices.VideoAdScheduler** ein, und installieren Sie das Microsoft.StoreServices.VideoAdScheduler-Paket. Die Datei „AdScheduler.js“ wird dem Unterverzeichnis „../js“ Ihres Projekts hinzugefügt.

5.  Öffnen Sie die Datei „index.html“ (oder je nach Projekt eine andere HTML-Datei). Fügen Sie im Abschnitt `<head>` nach den JavaScript-Verweisen auf „default.css“ und „main.js“ des Projekts den Verweis auf „ad.js“ und „adscheduler.js“ hinzu.

  > [!div class="tabbedCodeSnippets"]
  ``` html
  <script src="//Microsoft.Advertising.JavaScript/ad.js"></script>
  <script src="/js/adscheduler.js"></script>
  ```

  <span/>
  > **Hinweis**&nbsp;&nbsp;Diese Zeile muss im Bereich `<head>` nach der Datei „main.js“ platziert werden. Andernfalls tritt bei der Erstellung des Projekts ein Fehler auf.

6.  Fügen Sie der Datei „main.js“ des Projekts Code hinzu, mit dem ein neues [AdScheduler](https://msdn.microsoft.com/library/windows/apps/mt732197.aspx)-Objekt erstellt wird. Übergeben Sie den **MediaPlayer**, mit dem Ihre Videoinhalte gehostet werden. Der Code muss so angeordnet werden, dass er nach [WinJS.UI.processAll](https://msdn.microsoft.com/library/windows/apps/hh440975.aspx) ausgeführt wird.

  > [!div class="tabbedCodeSnippets"]
  [!code-javascript[TrialVersion](./code/AdvertisingSamples/AdSchedulerSamples/js/js/main.js#Snippet2)]

7.  Verwenden Sie die Methode [requestSchedule](https://msdn.microsoft.com/library/windows/apps/mt732208.aspx) oder [requestScheduleByUrl](https://msdn.microsoft.com/library/windows/apps/mt732210.aspx), um einen Anzeigenzeitplan vom Server anzufordern und in die **MediaPlayer**-Zeitachse einzufügen. Anschließend werden die Videomedien wiedergegeben.

  * Wenn Sie Microsoft-Partner sind und eine Berechtigung zum Anfordern eines Anzeigenzeitplans vom Microsoft-Anzeigenserver erhalten haben, können Sie [requestSchedule](https://msdn.microsoft.com/library/windows/apps/mt732208.aspx) verwenden und die IDs für die Anwendung und die Anzeigeneinheit angeben, die von Ihrem Microsoft-Vertreter bereitgestellt wurden. Bei dieser Methode handelt es sich um eine **Zusage**. Dies ist ein asynchrones Konstrukt, bei dem zwei Funktionszeiger übergeben werden, um jeweils den Erfolgs- bzw. Fehlerfall zu verarbeiten. Weitere Informationen finden Sie unter [Asynchrone Muster in UWP mit JavaScript](https://msdn.microsoft.com/windows/uwp/threading-async/asynchronous-programming-universal-windows-platform-apps#asynchronous-patterns-in-uwp-using-javascript).

      > [!div class="tabbedCodeSnippets"]
      [!code-javascript[TrialVersion](./code/AdvertisingSamples/AdSchedulerSamples/js/js/main.js#Snippet3)]

  * Verwenden Sie zum Anfordern eines Anzeigenzeitplans von einem anderen Server als dem Microsoft-Anzeigenserver [requestScheduleByUrl](https://msdn.microsoft.com/library/windows/apps/mt732210.aspx), und übergeben Sie die Server-URL. Diese Methode ist ebenfalls eine **Zusage**.

      > [!div class="tabbedCodeSnippets"]
      [!code-javascript[TrialVersion](./code/AdvertisingSamples/AdSchedulerSamples/js/js/main.js#Snippet4)]

    <span/>
    >**Hinweis**&nbsp;&nbsp;Sie müssen **play** auch aufrufen, wenn für die Funktion ein Fehler auftritt. [AdScheduler](https://msdn.microsoft.com/library/windows/apps/mt732197.aspx) weist **MediaPlayer** nämlich an, dass die Anzeigen übersprungen werden sollen und direkt zum Inhalt navigiert werden soll. Unter Umständen besteht bei Ihnen auch eine andere geschäftliche Anforderung, z. B. das Einfügen einer integrierten Anzeige, falls eine Anzeige nicht erfolgreich von einem Remotestandort abgerufen werden kann.

8.  Während der Wiedergabe können Sie zusätzliche Ereignisse verarbeiten, mit denen Ihre App den Status bzw. Fehler nachverfolgen kann, die nach dem ersten Anzeigenabgleich auftreten. Der folgende Code zeigt einige dieser Ereignisse, einschließlich [onPodStart](https://msdn.microsoft.com/library/windows/apps/mt732206.aspx), [onPodEnd](https://msdn.microsoft.com/library/windows/apps/mt732205.aspx), [onPodCountdown](https://msdn.microsoft.com/library/windows/apps/mt732204.aspx), [onAdProgress](https://msdn.microsoft.com/library/windows/apps/mt732201.aspx), [onAllComplete](https://msdn.microsoft.com/library/windows/apps/mt732202.aspx) und [onErrorOccurred](https://msdn.microsoft.com/library/windows/apps/mt732203.aspx).

  > [!div class="tabbedCodeSnippets"]
  [!code-javascript[TrialVersion](./code/AdvertisingSamples/AdSchedulerSamples/js/js/main.js#Snippet5)]

