---
author: mcleanbyron
ms.assetid: bb105fbe-bbbd-4d78-899b-345af2757720
description: "Erfahren Sie, wie Sie Ihrer App die Anwendungs-ID und die Anzeigeneinheits-ID aus dem Windows Dev Center-Dashboard hinzufügen, bevor Sie die App an den Store übermitteln."
title: Einrichten von Anzeigeneinheiten in der App
ms.author: mcleans
ms.date: 06/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Anzeigen, Werbung, Anzeigeeinheiten
ms.openlocfilehash: f96e81079764682a9f603fe93a9c123a69690507
ms.sourcegitcommit: 8c4d50ef819ed1a2f8cac4eebefb5ccdaf3fa898
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2017
---
# <a name="set-up-ad-units-in-your-app"></a>Einrichten von Anzeigeneinheiten in der App

Jedes Steuerelement für eine Banneranzeige, Interstitialwerbung oder native Anzeige in Ihrer App verfügt über eine entsprechende *Anzeigeneinheit*. Diese wird von unseren Diensten verwendet, um Werbung auf das Steuerelement zu leiten. Jede Anzeigeneinheit besteht aus einer *Anzeigeneinheit-ID* und einer *Anwendungs-ID*. Während Sie Ihre App entwickeln, weisen Sie eine [Testanwendungs-ID und Anzeigeneinheits-ID](test-mode-values.md) zu, um zu beobachten, wie die Werbung während der Testphase von Ihrer App gerendert wird. Diese Testwerte können nur in einer Testversion Ihrer App verwendet werden.

Nachdem Sie Ihre App getestet haben und bereit sind, sie an das Windows Dev Center zu übermitteln, müssen Sie Ihren App-Code so ändern, dass er die Anwendungs-ID und die Anzeigeneinheits-ID auf der Seite [Monetarisierung mit Anzeigen](../publish/monetize-with-ads.md) im Windows Dev Center-Dashboard enthält. Wenn Sie Testwerte in einer veröffentlichten App verwenden, wird die App keine Livewerbung empfangen.

So richten Sie Anzeigeblöcke für die endgültige App ein:

1.  Wählen Sie Ihre App im Windows Dev Center-Dashboard und klicken Sie dann auf **Monetisierung > Gewinnbringende Nutzung mit Anzeigen**.

2.  Geben Sie im Abschnitt **Erstellen von Anzeigeneinheiten** einen Namen für die Anzeigeneinheit im Feld **Name der Anzeigeneinheit** ein.

3. Wählen Sie in der Dropdownliste **Art der Anzeigeneinheit** den Typ einer Anzeigeneinheit aus, der den in Ihrem Steuerelement angezeigten Anzeigen entspricht:

    -   Wenn Sie in Ihrer App ein [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) zum Anzeigen von Banneranzeigen verwenden, wählen Sie **Banner** aus.

    -   Wenn Sie in Ihrer App ein [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) zum Anzeigen von Interstitialvideos oder von Interstitial-Banneranzeigen verwenden, wählen Sie **Interstitialvideo** oder **Interstitialbanner** aus (achten Sie darauf, dass Sie die der Art der Interstitialwerbung, die Sie anzeigen möchten, entsprechende Option auswählen).

    -   Wenn Sie in Ihrer App ein [NativeAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.aspx) zum Anzeigen von nativen Anzeigen verwenden, wählen Sie **Nativ** aus.
      > [!NOTE]
      > Die Möglichkeit zum Erstellen von **nativen** Anzeigeeinheiten steht derzeit nur für Entwickler zur Verfügung, die an einem Pilotprogramm teilnehmen, wir möchten dieses Feature allerdings bald für alle Entwickler zur Verfügung stellen. Wenn Sie an unserem Pilotprogramms teilnehmen möchten, wenden Sie sich an aiacare@microsoft.com.

4.  Wählen Sie in der Dropdownliste **Gerätefamilie** die Gerätefamilie aus, auf die Ihre App ausgerichtet ist, in der die Anzeigeneinheit verwendet werden. Folgende Optionen sind verfügbar: **UWP (Windows 10)**, **PC/Tablet (Windows 8.1)** oder **Mobile (Windows Phone 8.x)**.

5.  Klicken Sie auf **Anzeigeneinheit erstellen**. Die neue Anzeigeneinheit wird oben in der Liste des Abschnitts **Verfügbare Anzeigeneinheiten** auf dieser Seite angezeigt.

6.  Für jede generierte Anzeigeneinheit werden eine **Anwendungs-ID** und eine **Anzeigeneinheits-ID** angezeigt. Zum Einblenden von Anzeigen in Ihrer App müssen Sie diese Werte in dem Code Ihrer App verwenden:

    -   Wenn Ihre App Werbebanner anzeigt, weisen Sie diese Werte den Eigenschaften [ApplicationId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.applicationid.aspx) und [AdUnitId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.adunitid.aspx) Ihres **AdControl**-Objekts hinzu. Weitere Informationen finden Sie unter [AdControl in XAML und .NET](adcontrol-in-xaml-and--net.md) und [AdControl in HTML 5 und JavaScript](adcontrol-in-html-5-and-javascript.md).

    -   Wenn Ihre App Interstitialanzeigen anzeigt, übergeben Sie diese Werte an die [RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.requestad.aspx)-Methode Ihres **InterstitialAd**-Objekts. Weitere Informationen finden Sie unter [Interstitialwerbungen](interstitial-ads.md).

    -   Wenn Ihre App native Anzeigen anzeigt, weisen Sie diese Werte die Parameter *applicationId* und *adUnitId* des [NativeAdsManager](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.nativeadsmanager.aspx)-Konstruktors zu. Weitere Informationen finden Sie unter [Native Anzeigen](../monetize/native-ads.md).

7. Wenn Ihre App eine UWP-App für Windows10 ist, können Sie optional die Anzeigenvermittlung für **AdControl** durch Konfigurieren der Einstellungen im Abschnitt [Anzeigenvermittlung](../publish/monetize-with-ads.md#mediation) aktivieren. Mit der Anzeigenvermittlung können Sie Ihre Anzeigenumsätze maximieren und Werbefunktionen optimal nutzen, indem Sie Anzeigen aus mehreren Anzeigennetzwerken anzeigen, einschließlich Anzeigen aus anderen kostenpflichtigen Anzeigennetzwerken wie Taboola und Smaato sowie Anzeigen zu Werbekampagnen für Microsoft-Apps. Wir wählen standardmäßig die Einstellungen der Anzeigenvermittlung für Ihre App mithilfe von Machine Learning Algorithmen aus, um Ihnen beim Optimieren der Anzeigenumsätze in den verschiedenen Märkten zu helfen, die Ihre App unterstützt. Sie können optional die Einstellungen für die Anzeigenvermittlung auch manuell konfigurieren.

<span id="manage" />
## <a name="manage-ad-units-for-multiple-ad-controls-in-your-app"></a>Verwalten von Anzeigeeinheiten für mehrere Steuerelemente von Anzeigen in Ihrer App

Können mehrere Steuerelemente für Banner-, Interstitialwerbungen und native Anzeigen in einer einzelnen App verwenden. In diesem Fall wird empfohlen, dass Sie jedem Steuerelement eine andere Anzeigeneinheit zuweisen. Durch das Verwenden verschiedener Anzeigeeinheiten für jedes Steuerelement können Sie für jedes Steuerelement [die Einstellungen für die Anzeigenvermittlung konfigurieren](../publish/monetize-with-ads.md#mediation) und diskrete [Berichtsdaten](../publish/advertising-performance-report.md). Außerdem können unsere Dienste so die Werbung optimieren, die wir in Ihrer App anzeigen.

> [!IMPORTANT]
> Sie können jede Anzeigeneinheit in nur einer App verwenden. Wenn Sie eine Anzeigeneinheit in mehr als einer App verwenden, werden für die Ad-Einheit keine Anzeigen platziert.

## <a name="related-topics"></a>Verwandte Themen

* [Testmoduswerte](test-mode-values.md)
* [AdControl in XAML und .NET](adcontrol-in-xaml-and--net.md)
* [AdControl in HTML 5 und Javascript](adcontrol-in-html-5-and-javascript.md)
* [Interstitialwerbung](interstitial-ads.md)
* [Native Anzeigen](../monetize/native-ads.md)


 

 
