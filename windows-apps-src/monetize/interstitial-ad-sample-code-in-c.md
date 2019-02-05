---
ms.assetid: 7a16b0ca-6b8e-4ade-9853-85690e06bda6
description: Erfahren Sie, wie Sie mithilfe von C# Interstitialwerbung veröffentlichen.
title: Beispielcode für Interstitialwerbung in C#
ms.date: 03/22/2018
ms.topic: article
keywords: Windows 10, UWP, Anzeigen, Werbung, Interstitial, C#, Beispielcode
ms.localizationpriority: medium
ms.openlocfilehash: 075d98d49ba7e878abc7e800af84984bdb93e3a2
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2019
ms.locfileid: "9045086"
---
# <a name="interstitial-ad-sample-code-in-c"></a><span data-ttu-id="08694-104">Beispielcode für Interstitialwerbung in C\#</span><span class="sxs-lookup"><span data-stu-id="08694-104">Interstitial ad sample code in C\#</span></span> #  

<span data-ttu-id="08694-105">Dieses Thema enthält den vollständigen Beispielcode für eine grundlegende C#- und XAML-App für die universelle Windows-Plattform (UWP), in der Videointerstitialwerbung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="08694-105">This topic provides the complete sample code for a basic C# and XAML Universal Windows Platform (UWP) app that shows an interstitial video ad.</span></span> <span data-ttu-id="08694-106">Eine schrittweise Anleitung dazu, wie Sie Ihr Projekt zur Verwendung dieses Codes konfigurieren, finden Sie unter [Interstitialwerbung](interstitial-ads.md).</span><span class="sxs-lookup"><span data-stu-id="08694-106">For step-by-step instructions that show how to configure your project to use this code, see [Interstitial ads](interstitial-ads.md).</span></span> <span data-ttu-id="08694-107">Ein vollständiges Beispielprojekt finden Sie unter den [Anzeigenbeispielen auf GitHub](https://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="08694-107">For a complete sample project, see the [advertising samples on GitHub](https://aka.ms/githubads).</span></span>

## <a name="code-example"></a><span data-ttu-id="08694-108">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="08694-108">Code example</span></span>

<span data-ttu-id="08694-109">In diesem Abschnitt wird der Inhalt der Dateien „MainPage.xaml“ und „MainPage.xaml.cs“ in einer einfachen App veranschaulicht, in der eine Interstitialwerbung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="08694-109">This section shows the contents of the MainPage.xaml and MainPage.xaml.cs files in a basic app that shows an interstitial ad.</span></span> <span data-ttu-id="08694-110">Um die Beispiele zu verwenden, kopieren Sie den Code in ein Visual C#-Projekt **Leere App (Universelle Windows-App)** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08694-110">To use these examples, copy the code into a Visual C# **Blank App (Universal Windows)** project in Visual Studio.</span></span>

<span data-ttu-id="08694-111">Diese Beispiel-App verwendet zwei Schaltflächen, um eine Interstitialwerbung anzufordern und dann zu starten.</span><span class="sxs-lookup"><span data-stu-id="08694-111">This sample app uses two buttons to request and then launch an interstitial ad.</span></span> <span data-ttu-id="08694-112">Ersetzen Sie die Werte von der ```myAppId``` und ```myAdUnitId``` Felder durch livewerte aus dem Partner Center, bevor Sie Ihre app an den Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="08694-112">Replace the values of the ```myAppId``` and ```myAdUnitId``` fields with live values from Partner Center before submitting your app to the Store.</span></span> <span data-ttu-id="08694-113">Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md#live-ad-units).</span><span class="sxs-lookup"><span data-stu-id="08694-113">For more information, see [Set up ad units in your app](set-up-ad-units-in-your-app.md#live-ad-units).</span></span>

> [!NOTE]
> <span data-ttu-id="08694-114">Wenn Sie dieses Beispiel ändern möchten, um eine Interstitialwerbung mit Bannern anstelle einer Videointerstitialanzeige anzuzeigen, übergeben Sie den Wert **AdType.Display** an den ersten Parameter der [RequestAd](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.interstitialad.requestad)-Methode anstelle von **AdType.Video**.</span><span class="sxs-lookup"><span data-stu-id="08694-114">To alter this example to show an interstitial banner ad instead of an interstitial video ad, pass the value **AdType.Display** to the first parameter of the [RequestAd](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.interstitialad.requestad) method instead of **AdType.Video**.</span></span> <span data-ttu-id="08694-115">Weitere Informationen finden Sie unter [Interstitialanzeigen](interstitial-ads.md).</span><span class="sxs-lookup"><span data-stu-id="08694-115">For more information, see [Interstitial ads](interstitial-ads.md).</span></span>

### <a name="mainpagexaml"></a><span data-ttu-id="08694-116">MainPage.xaml</span><span class="sxs-lookup"><span data-stu-id="08694-116">MainPage.xaml</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-xml[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml#L1-L13)]

### <a name="mainpagexamlcs"></a><span data-ttu-id="08694-117">MainPage.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="08694-117">MainPage.xaml.cs</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#CompleteSample)]

 
## <a name="related-topics"></a><span data-ttu-id="08694-118">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="08694-118">Related topics</span></span>

* [<span data-ttu-id="08694-119">Anzeigenbeispiele bei GitHub</span><span class="sxs-lookup"><span data-stu-id="08694-119">Advertising samples on GitHub</span></span>](https://aka.ms/githubads)
 
