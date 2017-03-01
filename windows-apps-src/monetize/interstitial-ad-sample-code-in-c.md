---
author: mcleanbyron
ms.assetid: 7a16b0ca-6b8e-4ade-9853-85690e06bda6
description: "Erfahren Sie, wie Sie mithilfe von C# Interstitialwerbung veröffentlichen."
title: "Beispielcode für Interstitialwerbung in C#"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Anzeigen, Werbung, Interstitial, C#, Beispielcode
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 4c57cf4909028d5aa81c75d9e1b6f1bf28d41ad7
ms.lasthandoff: 02/07/2017

---

# <a name="interstitial-ad-sample-code-in-c"></a>Beispielcode für Interstitialwerbung in C\# #  

Dieses Thema enthält den vollständigen Beispielcode für eine grundlegende C#- und XAML-App für die universelle Windows-Plattform (UWP), in der Interstitialwerbung angezeigt wird. Eine schrittweise Anleitung dazu, wie Sie Ihr Projekt zur Verwendung dieses Codes konfigurieren, finden Sie unter [Interstitialwerbung](interstitial-ads.md). Ein vollständiges Beispielprojekt finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).

## <a name="code-example"></a>Codebeispiel

In diesem Abschnitt wird der Inhalt der Dateien „MainPage.xaml“ und „MainPage.xaml.cs“ in einer einfachen App veranschaulicht, in der eine Interstitialwerbung angezeigt wird. Um die Beispiele zu verwenden, kopieren Sie den Code in ein Visual C#-Projekt **Leere App (Universelle Windows-App)** in Visual Studio 2015.

Diese Beispiel-App verwendet zwei Schaltflächen, um eine Interstitialwerbung anzufordern und dann zu starten. Ersetzen Sie die Werte der Felder ```myAppId``` und ```myAdUnitId``` durch Livewerte aus dem Windows Dev Center, bevor Sie Ihre App an den Store übermitteln. Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md).

### <a name="mainpagexaml"></a>MainPage.xaml

> [!div class="tabbedCodeSnippets"]
[!code-xml[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml#L1-L13)]

### <a name="mainpagexamlcs"></a>MainPage.xaml.cs

> [!div class="tabbedCodeSnippets"]
[!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#CompleteSample)]

 
## <a name="related-topics"></a>Verwandte Themen

* [Anzeigenbeispiele auf GitHub](http://aka.ms/githubads)
 

