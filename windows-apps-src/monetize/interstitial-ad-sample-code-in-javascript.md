---
author: mcleanbyron
ms.assetid: 646977ed-1705-4ea7-a3db-a6b9aac70703
description: "Erfahren Sie, wie Sie Interstitialwerbung mithilfe von JavaScript/HTML veröffentlichen."
title: "Beispielcode für Interstitialwerbung in JavaScript"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, Interstitialwerbung, JavaScript, Beispielcode
ms.openlocfilehash: 192ea42e9d55bbafcd6c6dbd463681832ac28c86
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="interstitial-ad-sample-code-in-javascript"></a>Beispielcode für Interstitialwerbung in JavaScript

Dieses Thema enthält den vollständigen Beispielcode für eine grundlegende JavaScript- und HTML-App für die universelle Windows-Plattform (UWP), in der Interstitialwerbung angezeigt wird. Eine schrittweise Anleitung dazu, wie Sie Ihr Projekt zur Verwendung dieses Codes konfigurieren, finden Sie unter [Interstitialwerbung](interstitial-ads.md). Ein vollständiges Beispielprojekt finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).

## <a name="code-example"></a>Codebeispiel

In diesem Abschnitt wird der Inhalt der HTML- und JavaScript-Dateien in einer einfachen App veranschaulicht, in der eine Interstitialwerbung angezeigt wird. Um die Beispiele zu verwenden, kopieren Sie diesen Code in ein JavaScript-Projekt **WinJS-App (universelles Windows)** in Visual Studio2015.

Diese Beispiel-App verwendet zwei Schaltflächen, um eine Interstitialwerbung anzufordern und dann zu starten. Die von Visual Studio generierten Dateien „main.js“ und „index.html“ wurden geändert und sind unten zu sehen. Die unten dargestellte Datei „script.js“ enthält den größten Teil des Beispielcodes. Diese Datei muss dem Ordner **js** in Ihrem Projekt hinzugefügt werden.

>**Hinweis für Windows 8.x und Windows Phone 8.1**&nbsp;&nbsp;Wenn Ihr Projekt auf Windows8.1 oder Windows Phone8.1 ausgerichtet ist, heißt die standardmäßige HTML-Datei in Ihrem Projekt „default.html“ und nicht „index.html“, und die standardmäßige JavaScript-Datei in Ihrem Projekt heißt „default.js“ anstatt „main.js“.

Ersetzen Sie die Werte der Variablen ```applicationId``` und ```adUnitId``` durch Livewerte aus dem Windows Dev Center, bevor Sie die App an den Store übermitteln. Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md).

>**Hinweis**&nbsp;&nbsp;Wenn Sie dieses Beispiel ändern möchten, um eine Interstitialwerbung mit Bannern anstelle einer Videointerstitialanzeige anzuzeigen, übergeben Sie den Wert **InterstitialAdType.display** an den ersten Parameter der [RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.requestad.aspx)-Methode anstelle von **InterstitialAdType.video**. Weitere Informationen finden Sie unter [Interstitialanzeigen](interstitial-ads.md).

### <a name="indexhtml"></a>index.html

> [!div class="tabbedCodeSnippets"]
[!code-html[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/index.html#L1-L21)]

<span/>
>**Hinweis für Windows8.x und Windows Phone8.1**&nbsp;&nbsp;Wenn Ihr Projekt auf Windows8.1 oder Windows Phone8.1 ausgerichtet ist, ersetzen Sie die Zeile ```<script src="//Microsoft.Advertising.JavaScript/ad.js"></script>``` im Beispiel durch ```<script src="/MSAdvertisingJS/ads/ad.js"></script>```.

### <a name="scriptjs"></a>script.js

> [!div class="tabbedCodeSnippets"]
[!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/script.js#script)]

### <a name="mainjs"></a>main.js

> [!div class="tabbedCodeSnippets"]
[!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/main.js#main)]

## <a name="related-topics"></a>Verwandte Themen

* [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads)

 
