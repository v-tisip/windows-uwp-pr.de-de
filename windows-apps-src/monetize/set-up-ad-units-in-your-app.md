---
author: mcleanbyron
ms.assetid: bb105fbe-bbbd-4d78-899b-345af2757720
description: "Erfahren Sie, wie Sie Ihrer App die Anwendungs-ID und die Anzeigeneinheits-ID aus dem Windows Dev Center-Dashboard hinzufügen, bevor Sie die App an den Store übermitteln."
title: Einrichten von Anzeigeneinheiten in der App
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Anzeigen, Werbung, Anzeigeeinheiten
ms.openlocfilehash: daf0887462a4c84aa827a6261793a0eaf4d512ca
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="set-up-ad-units-in-your-app"></a>Einrichten von Anzeigeneinheiten in der App




Bei Verwendung von [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) oder [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) zum Anzeigen von Werbung in Ihrer App müssen Sie eine Anwendungs-ID und eine Anzeigeneinheits-ID angeben. Während Sie Ihre App entwickeln, verwenden Sie die entsprechende [Testanwendungs-ID und Anzeigeneinheits-ID](test-mode-values.md), um zu beobachten, wie die Werbung während der Testphase von Ihrer App gerendert wird.

Nachdem Sie Ihre App getestet haben und bereit sind, sie an das Windows Dev Center zu übermitteln, müssen Sie Ihren App-Code so ändern, dass er die Anwendungs-ID und die Anzeigeneinheits-ID aus dem [Windows Dev Center-Dashboard](https://msdn.microsoft.com/library/windows/apps/mt170658.aspx) enthält. Wenn Sie Testwerte in einer veröffentlichten App verwenden, wird die App keine Livewerbung empfangen.

So richten Sie Anwendungs-ID und Anzeigeblöcke für die endgültige App ein:

1.  Wählen Sie Ihre App im Windows Dev Center-Dashboard und klicken Sie dann auf **Monetisierung > Gewinnbringende Nutzung mit Anzeigen**.

2.  Im Abschnitt **Microsoft Advertising-Anzeigeneinheiten** auf dieser Seite erstellen Sie eine Anzeigeneinheit. Wählen Sie als Anzeigeneinheitentyp eine der folgenden Optionen aus:

  * Wenn Sie in Ihrer App ein **AdControl** zum Anzeigen von Banneranzeigen verwenden, wählen Sie für den Anzeigeneinheitentyp **Banner** aus.

  * Wenn Sie in Ihrer App ein **InterstitialAd** zum Anzeigen von Interstitialvideos oder von Interstitial-Banneranzeigen verwenden, wählen Sie **Interstitialvideo** oder **Interstitialbanner** aus (achten Sie darauf, dass Sie die der Art der Interstitialwerbung, die Sie anzeigen möchten, entsprechende Option auswählen).

3.  Für jede generierte Anzeigeneinheit werden auf der Seite eine **Anwendungs-ID** und eine **Anzeigeneinheits-ID** angezeigt. Zum Einblenden von Anzeigen in Ihrer App müssen Sie diese Werte in dem Code Ihrer App verwenden:

  * Wenn Ihre App Werbebanner anzeigt, weisen Sie diese Werte den Eigenschaften [ApplicationId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.applicationid.aspx) und [AdUnitId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.adunitid.aspx) Ihres **AdControl**-Objekts hinzu. Weitere Informationen finden Sie unter [AdControl in XAML und .NET](adcontrol-in-xaml-and--net.md) und [AdControl in HTML 5 und JavaScript](adcontrol-in-html-5-and-javascript.md).

  * Wenn Ihre App Interstitialanzeigen anzeigt, übergeben Sie diese Werte an die [RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.requestad.aspx)-Methode Ihres **InterstitialAd**-Objekts. Weitere Informationen finden Sie unter [Interstitialanzeigen](interstitial-ads.md).

Weitere Informationen zur Seite **Gewinnbringende Nutzung mit Anzeigen** finden Sie unter [Gewinnbringende Nutzung mit Anzeigen](../publish/monetize-with-ads.md).

## <a name="related-topics"></a>Verwandte Themen

* [Testmoduswerte](test-mode-values.md)
* [AdControl in XAML und .NET](adcontrol-in-xaml-and--net.md)
* [AdControl in HTML 5 und Javascript](adcontrol-in-html-5-and-javascript.md)
* [Interstitialwerbung](interstitial-ads.md)


 

 
