---
author: mcleanbyron
ms.assetid: adb2fa45-e18f-4254-bd8b-a749a386e3b4
description: "Hier erfahren Sie, wie Sie die AdControl-Klasse nutzen können, um Werbebanner in einer JavaScript/HTML-App für Windows 10 (UWP), Windows 8.1 oder Windows Phone 8.1 anzuzeigen."
title: "„AdControl“ in HTML 5 und JavaScript"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Anzeigen, Werbung, AdControl, JavaScript, HTML"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: cda74aaf6301f0cc04c5a9ae5c2aad5cf43d8b7e
ms.lasthandoff: 02/07/2017

---

# <a name="adcontrol-in-html-5-and-javascript"></a>„AdControl“ in HTML 5 und JavaScript

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie die [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Klasse nutzen können, um Werbebanner in einer JavaScript/HTML-App für Windows 10 (UWP), Windows 8.1 oder Windows Phone 8.1 anzuzeigen. In dieser exemplarischen Vorgehensweise wird die **AdMediatorControl** oder die Anzeigenvermittlung nicht verwendet.

Ein vollständiges Beispiel-Projekt mit einer Veranschaulichung, wie Sie mithilfe von C# und C++ Werbebanner einer JavaScript/HTML-App hinzufügen, finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).

## <a name="prerequisites"></a>Voraussetzungen


* Für UWP-Apps: Installieren Sie das [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) mit Visual Studio 2015.
* Für Windows 8.1- oder Windows Phone 8.1-Apps: Installieren Sie das [Microsoft Advertising SDK für Windows und Windows Phone 8.x](http://aka.ms/store-8-sdk) mit Visual Studio 2015 oder Visual Studio 2013.

> **Hinweis**&nbsp;&nbsp;Wenn Sie Windows 10 Anniversary SDK Preview Build 14295 oder höher mit Visual Studio 2015 installiert haben, müssen Sie außerdem die WinJS-Bibliothek installieren. Diese Bibliothek war in den früheren Versionen von Windows SDK für Windows 10 enthalten, aber ab Windows 10 Anniversary SDK Preview Build 14295 muss diese Bibliothek separat installiert werden. Informationen zur Installation von WinJS finden Sie unter [WinJS herunterladen](http://try.buildwinjs.com/download/GetWinJS/).

## <a name="code-development"></a>Codeentwicklung

1. Öffnen Sie in Visual Studio Ihr Projekt oder erstellen Sie ein neues Projekt.

2. Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, müssen Sie eine architekturspezifische Buildausgabe verwenden (z. B. **X86**) und das Projekt entsprechend aktualisieren. Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, können Sie bei den folgenden Schritten keinen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen. Weitere Informationen finden Sie unter [Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden](known-issues-for-the-advertising-libraries.md#reference_errors).

3.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.

4.  Wählen Sie im **Verweis-Manager** je nach Projekttyp einen der folgenden Verweise aus:

    -   Für ein Projekt für die Universelle Windows-Plattform (UWP): Erweitern Sie **Universelles Windows**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für JavaScript** (Version 10.0).

    -   Für ein Windows 8.1-Projekt: Erweitern Sie **Windows 8.1**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für Windows 8.1 Native (JS)**.

    -   Für ein Windows 8.1-Projekt: Erweitern Sie **Windows 8.1**, klicken Sie auf **Erweiterungen** und aktivieren Sie dann das Kontrollkästchen neben **Microsoft Advertising SDK for Windows Phone 8.1 Systemeigen (JS)**.

    ![javascriptaddreference](images/13-f7f6d6a6-161e-4f17-995d-1236d0b5d9f2.png)

    > **Hinweis**&nbsp;&nbsp;Diese Abbildung bezieht sich auf die Erstellung eines UWP-Projekts für Windows 10 mit Visual Studio 2015. Wenn Sie eine Windows 8.1- oder Windows Phone 8.1-App erstellen oder Visual Studio 2013 verwenden, sieht Ihr Bildschirm anders aus.

5.  Klicken Sie im **Verweis-Manager** auf „OK“.

6.  Öffnen Sie die Datei „index.html“ (oder je nach Projekt eine andere HTML-Datei).

7.  Fügen Sie im Abschnitt **&lt;Head&gt;** nach den JavaScript-Verweisen auf default.css und main.js des Projekts den Verweis auf ad.js ein.

  Fügen Sie im UWP-Projekt den folgenden Code hinzu.

  > [!div class="tabbedCodeSnippets"]
  ``` html
  <!-- Microsoft advertising required references -->
  <script src="//Microsoft.Advertising.JavaScript/ad.js"></script>
  ```

  Fügen Sie bei einem Windows 8.1- oder Windows Phone 8.1-Projekt den folgenden Code hinzu.

  > [!div class="tabbedCodeSnippets"]
  ``` html
  <!-- Microsoft advertising required references -->
  <script src="/MSAdvertisingJS/ads/ad.js"></script>
  ```

  <span/>
  >**Hinweis**&nbsp;&nbsp;Diese Zeile muss im Bereich **&lt;Head&gt;** nach der Datei „main.js“ platziert werden. Andernfalls tritt ein Fehler auf, wenn Sie Ihr Projekt erstellen. Wenn Ihr Projekt auf Windows 8.1 oder Windows Phone 8.1 ausgerichtet ist, ist die standardmäßige HTML-Datei in Ihrem Projekt default.html und nicht index.html, und die standardmäßige JavaScript-Datei in Ihrem Projekt ist default.js anstelle von main.js.

8.  Ändern Sie den Bereich **&lt;Body&gt;** in der Datei „default.HTML“ (oder je nach Projekt einer anderen html-Datei), sodass sie das DIV-Element für die **AdControl** enthält. Weisen Sie den Eigenschaften **ApplicationId** und **AdUnitId** Eigenschaften in der **AdControl** die unter [Testmoduswerte](test-mode-values.md) bereitgestellten Testwerte zu. Passen Sie Höhe und Breite des Steuerelements an, damit es einer der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) entspricht.

  > **Hinweis**&nbsp;&nbsp;Sie ersetzen die Testwerte **applicationId** und **adUnitId** durch Livewerte, bevor Sie Ihre App übermitteln.

  > [!div class="tabbedCodeSnippets"]
  ``` html
  <div id="myAd" style="position: absolute; top: 50px; left: 0px; width: 300px; height: 250px; z-index: 1"
        data-win-control="MicrosoftNSJS.Advertising.AdControl"
        data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: '10865270'}">
  </div>
  ```

9.  Kompilieren und Ausführen der App, um sie mit einer Anzeige zu sehen

## <a name="release-your-app-with-live-ads-using-windows-dev-center"></a>Veröffentlichen der App mit Live-Werbung mithilfe von Windows Dev Center


1.  Rufen Sie für Ihre App im Dev Center-Dashboard die Seite **Monetarisierung** &gt; **Gewinnbringende Nutzung mit Anzeigen** auf, und [erstellen Sie eine eigenständige Microsoft Advertising-Einheit](../publish/monetize-with-ads.md). Geben Sie als Einheitentyp **Banner** an. Notieren Sie sich die Anzeigeeinheits-ID und die Anwendungs-ID.

2.  Ersetzen Sie in Ihrem Code die Testwerte der Anzeigenheit (**applicationId** und **adUnitId**) mit den Live-Werten, die Sie in Dev Center generiert haben.

3.  [Übermitteln Sie Ihre App](../publish/app-submissions.md) mithilfe des Dev Center-Dashboards an den Store.

4.  Überprüfen Sie die [Anzeigenvermittlungsberichte](../publish/advertising-performance-report.md) im Dev Center-Dashboard.

## <a name="complete-indexhtml-for-a-sample-uwp-project"></a>Vollständige index.html für ein Beispielprojekt für UWP

> [!div class="tabbedCodeSnippets"]
``` html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>AdControlExampleApp</title>
    <!-- WinJS references -->
    <link href="lib/winjs-4.0.1/css/ui-light.css" rel="stylesheet" />
    <script src="lib/winjs-4.0.1/js/base.js"></script>
    <script src="lib/winjs-4.0.1/js/ui.js"></script>
    <!-- AdControlExampleApp references -->
    <link href="css/default.css" rel="stylesheet" />
    <script src="js/main.js"></script>
    <!-- Required reference for AdControl -->
    <script src="//Microsoft.Advertising.JavaScript/ad.js"></script>
</head>
<body>
    <div id="myAd" style="position: absolute; top: 50px; left: 0px; width: 300px; height: 250px; z-index: 1"
      data-win-control="MicrosoftNSJS.Advertising.AdControl"
      data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: '10865270'}">
    </div>
    <p>Content goes here</p>
</body>
</html>
```

## <a name="related-topics"></a>Verwandte Themen

* [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads)
 

 

