---
author: Xansky
ms.assetid: 646977ed-1705-4ea7-a3db-a6b9aac70703
description: Erfahren Sie, wie Sie Interstitialwerbung mithilfe von JavaScript/HTML veröffentlichen.
title: Beispielcode für Interstitialwerbung in JavaScript
ms.author: mhopkins
ms.date: 03/22/2018
ms.topic: article
keywords: Windows10, UWP, Anzeigen, Werbung, Interstitialwerbung, JavaScript, Beispielcode
ms.localizationpriority: medium
ms.openlocfilehash: 1921725e5b598a2e5e79ed90c607414e4efe574e
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "6454820"
---
# <a name="interstitial-ad-sample-code-in-javascript"></a>Beispielcode für Interstitialwerbung in JavaScript

Dieses Thema enthält den vollständigen Beispielcode für eine grundlegende JavaScript- und HTML-App für die universelle Windows-Plattform (UWP), in der Interstitialwerbung angezeigt wird. Eine schrittweise Anleitung dazu, wie Sie Ihr Projekt zur Verwendung dieses Codes konfigurieren, finden Sie unter [Interstitialwerbung](interstitial-ads.md). Ein vollständiges Beispielprojekt finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).

## <a name="code-example"></a>Codebeispiel

In diesem Abschnitt wird der Inhalt der HTML- und JavaScript-Dateien in einer einfachen App veranschaulicht, in der eine Interstitialwerbung angezeigt wird. Um die Beispiele zu verwenden, kopieren Sie diesen Code in ein JavaScript-Projekt **WinJS-App (universelles Windows)** in Visual Studio.

Diese Beispiel-App verwendet zwei Schaltflächen, um eine Interstitialwerbung anzufordern und dann zu starten. Die von Visual Studio generierten Dateien „main.js“ und „index.html“ wurden geändert und sind unten zu sehen. Die unten dargestellte Datei „script.js“ enthält den größten Teil des Beispielcodes. Diese Datei muss dem Ordner **js** in Ihrem Projekt hinzugefügt werden.

Ersetzen Sie die Werte für die ```applicationId``` und ```adUnitId``` Variablen durch livewerte aus dem Partner Center, bevor Sie Ihre app an den Store übermitteln. Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in Ihrer App](set-up-ad-units-in-your-app.md#live-ad-units).

> [!NOTE]
> Wenn Sie dieses Beispiel ändern möchten, um eine Interstitialwerbung mit Bannern anstelle einer Videointerstitialanzeige anzuzeigen, übergeben Sie den Wert **InterstitialAdType.display** an den ersten Parameter der [RequestAd](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.interstitialad.requestad)-Methode anstelle von **InterstitialAdType.video**. Weitere Informationen finden Sie unter [Interstitialanzeigen](interstitial-ads.md).

### <a name="indexhtml"></a>index.html

> [!div class="tabbedCodeSnippets"]
[!code-html[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/index.html#L1-L21)]

### <a name="scriptjs"></a>script.js

> [!div class="tabbedCodeSnippets"]
[!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/script.js#script)]

### <a name="mainjs"></a>main.js

> [!div class="tabbedCodeSnippets"]
[!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/main.js#main)]

## <a name="related-topics"></a>Verwandte Themen

* [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads)

 
