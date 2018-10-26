---
author: Xansky
ms.assetid: 7a16b0ca-6b8e-4ade-9853-85690e06bda6
description: Erfahren Sie, wie Sie mithilfe von C# Interstitialwerbung veröffentlichen.
title: Beispielcode für Interstitialwerbung in C#
ms.author: mhopkins
ms.date: 03/22/2018
ms.topic: article
keywords: Windows 10, UWP, Anzeigen, Werbung, Interstitial, C#, Beispielcode
ms.localizationpriority: medium
ms.openlocfilehash: 94baaa490859baf57e0bd12bc5a3800ed3b2312a
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5545645"
---
# <a name="interstitial-ad-sample-code-in-c"></a>Beispielcode für Interstitialwerbung in C\# #  

Dieses Thema enthält den vollständigen Beispielcode für eine grundlegende C#- und XAML-App für die universelle Windows-Plattform (UWP), in der Videointerstitialwerbung angezeigt wird. Eine schrittweise Anleitung dazu, wie Sie Ihr Projekt zur Verwendung dieses Codes konfigurieren, finden Sie unter [Interstitialwerbung](interstitial-ads.md). Ein vollständiges Beispielprojekt finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).

## <a name="code-example"></a>Codebeispiel

In diesem Abschnitt wird der Inhalt der Dateien „MainPage.xaml“ und „MainPage.xaml.cs“ in einer einfachen App veranschaulicht, in der eine Interstitialwerbung angezeigt wird. Um die Beispiele zu verwenden, kopieren Sie den Code in ein Visual C#-Projekt **Leere App (Universelle Windows-App)** in Visual Studio.

Diese Beispiel-App verwendet zwei Schaltflächen, um eine Interstitialwerbung anzufordern und dann zu starten. Ersetzen Sie die Werte der Felder ```myAppId``` und ```myAdUnitId``` durch Livewerte aus dem Windows Dev Center, bevor Sie Ihre App an den Store übermitteln. Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md#live-ad-units).

> [!NOTE]
> Wenn Sie dieses Beispiel ändern möchten, um eine Interstitialwerbung mit Bannern anstelle einer Videointerstitialanzeige anzuzeigen, übergeben Sie den Wert **AdType.Display** an den ersten Parameter der [RequestAd](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.interstitialad.requestad)-Methode anstelle von **AdType.Video**. Weitere Informationen finden Sie unter [Interstitialanzeigen](interstitial-ads.md).

### <a name="mainpagexaml"></a>MainPage.xaml

> [!div class="tabbedCodeSnippets"]
[!code-xml[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml#L1-L13)]

### <a name="mainpagexamlcs"></a>MainPage.xaml.cs

> [!div class="tabbedCodeSnippets"]
[!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#CompleteSample)]

 
## <a name="related-topics"></a>Verwandte Themen

* [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads)
 
