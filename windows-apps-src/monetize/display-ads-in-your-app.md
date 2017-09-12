---
author: mcleanbyron
ms.assetid: 63A9EDCF-A418-476C-8677-D8770B45D1D7
description: "Mit dem Microsoft Advertising-SDK haben Sie mehrere Möglichkeiten zur Monetarisierung Ihrer App mit Anzeigen."
title: Zeigt Werbung mithilfe der Microsoft Advertising-SDK in Ihrer App an
ms.author: mcleans
ms.date: 07/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, banner, Anzeigensteuerelement,Interstitial
ms.openlocfilehash: 4730ebaf55af8e7063c444d5b3bbd973b0508db2
ms.sourcegitcommit: a9e4be98688b3a6125fd5dd126190fcfcd764f95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2017
---
# <a name="display-ads-in-your-app-with-the-microsoft-advertising-sdk"></a>Zeigt Werbung mithilfe der Microsoft Advertising-SDK in Ihrer App an

Erhöhen Sie Ihre Umsatzchancen, indem Sie mithilfe des Microsoft Advertising-SDKs Anzeigen in Ihren Apps einfügen. Unsere Anzeigen-Monetarisierungsplattform bietet verschiedene Anzeigentypen und unterstützt die Anzeigenvermittlung mit unterschiedlichen beliebten Anzeigennetzwerken.

Gehen Sie folgendermaßen vor, um Anzeigen in Ihren Apps anzuzeigen.

## <a name="step-1-install-the-microsoft-advertising-sdk"></a>Schritt 1: Installieren des Microsoft Advertising-SDK

Das Microsoft Advertising-SDK bietet eine Vielzahl von Steuerelementen, die Sie zum Anzeigen von verschiedenen Arten von Anzeigen in Ihren App verwenden können. Eine Installationsanleitung finden Sie in [diesem Artikel.](install-the-microsoft-advertising-libraries.md)

## <a name="step-2-choose-your-ad-type-and-add-code-to-display-test-ads-in-your-app"></a>Schritt2: Wählen Sie den Anzeigentyp und fügen Sie Code zum Testen in Ihre App hinzu.

Das Microsoft Advertising-SDK enthält verschiedene Arten von Anzeigen, die in Ihrer App angezeigt werden können. Wählen Sie, welche Arten von Anzeigen für Ihr Szenario am besten geeignet sind, und fügen Sie Code für Ihre App hinzu, um diese Anzeigen darzustellen.

Sie müssen eine Anwendungs-ID und Anzeigeneinheits-ID in Ihrem Code zum Anzeigen Ihrer App angeben. Während Sie Ihre App entwickeln, verwenden Sie die entsprechende [Testanwendungs-ID und Anzeigeneinheits-ID](test-mode-values.md), um zu beobachten, wie die Werbung während der Testphase von Ihrer App gerendert wird.

### <a name="banner-ads"></a>Banneranzeigen

Banneranzeigen sind statische Anzeigen, die einen Teil einer Seite in einer App verwenden, in der Regel am oberen oder unteren Rand der Seite.

Weitere Informationen und Codebeispiele finden Sie unter [AdControl in XAML und .NET](adcontrol-in-xaml-and--net.md) und [AdControl in HTML 5 und JavaScript](adcontrol-in-html-5-and-javascript.md). Vollständige Beispielprojekte, die das Hinzufügen von Banneranzeigen zu JavaScript-/HTML- und XAML-Apps unter Verwendung von C# und C++ zeigen, finden Sie in den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).

![addreferences](images/banner-ad.png)

### <a name="interstitial-ads"></a>Interstitialwerbung

Interstitialanzeigen sind Vollbildanzeigen, durch die der Benutzer in der Regel gezwungen wird, sich ein Video anzusehen oder sich durch die Anzeige zu klicken, um mit der App oder dem Spiel fortfahren zu können. Wir unterstützen zwei Arten von Interstitialanzeigen: Videos und Banner.

Anweisungen und Codebeispiele finden Sie unter [Interstitialanzeigen](interstitial-ads.md). Vollständige Beispielprojekte, die das Hinzufügen von Interstitialwerbung zu JavaScript-/HTML- und XAML-Apps unter Verwendung von C# und C++ zeigen, finden Sie in den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).

![addreferences](images/interstitial-ad.png)

### <a name="native-ads"></a>Native Anzeigen

Hierbei handelt es sich um komponentenbasierte Anzeigen anzeigen. Jeder Teil des Anzeigen-Creatives (z. B. Titel, Bild, Beschreibung und Handlungsaufforderungstext) wird als einzelnes Element an Ihre App übermittelt. Sie können die Elemente mit eigenen Schriften, Farben und anderen UI-Komponenten in Ihre App integrieren und so unterbrechungsfrei darstellen.

Anweisungen und Codebeispiele finden Sie unter [Native Anzeigen](native-ads.md).

![addreferences](images/native-ad.png)

## <a name="step-3-get-an-ad-unit-from-dev-center-and-configure-your-app-to-receive-live-ads"></a>Schritt3: Rufen Sie eine Anzeigeneinheit aus dem Dev Center ab, und konfigurieren Sie Ihre App zum Empfang von Liveanzeigen

Nachdem Sie Ihre App getestet haben und Sie sie an den Store übermitteln können, erstellen Sie eine Anzeigeneinheit auf der [Monetarisierung mit Anzeigen](../publish/monetize-with-ads.md) Seite im Windows Dev Center-Dashboard. Dann aktualisieren Sie Ihren App-Code, um die Anwendungs-ID und Anzeigeneinheits-ID für diese Anzeigeneinheit zu verwenden. Wenn Sie versuchen, die Test-Anwendungs-ID und Anzeigeneinheits-ID in der veröffentlichten Version Ihrer App im Store zu verwenden, erhält Ihre App keine Liveanzeigen. Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md).

<span id="ad-mediation"/>
### <a name="configure-ad-mediation"></a>Konfigurieren der Anzeigenvermittlung

Standardmäßig zeigen Banneranzeigen, Interstitial-Anzeigen und native Anzeigen Werbung aus dem Microsoft-Netzwerk für kostenpflichtige Werbeanzeigen an. Um Ihren Anzeigenumsatz zu maximieren, können Sie für Ihre Anzeigeneinheit die Anzeigenvermittlung aktivieren, um kostenpflichtige Anzeigen von weiteren Anzeigennetzwerken anzuzeigen (z. B. Taboola und Smaato). Sie können Ihrer App-Werbung auch steigern, indem Sie Anzeigen aus Microsoft App-Werbekampagnen darstellen.

Zum Starten der Anzeigenvermittlung in Ihrer UWP-App [Konfigurieren Sie die Anzeigenvermittlungseinstellungen](../publish/monetize-with-ads.md#mediation) für Ihre Anzeigeneinheit. Standardmäßig werden die Einstellungen für die Anzeigenvermittlung automatisch mithilfe von Machine Learning-Algorithmen konfiguriert, die ihnen bei der Optimierung der Anzeigenumsätze in den verschiedenen Märkten helfen, die Ihre App unterstützt. Sie haben jedoch auch die Möglichkeit, die gewünschten Netzwerke manuell auszuwählen. In beiden Fällen werden die Einstellungen für die Anzeigenvermittlung vollständig auf dem Dienst konfiguriert; Sie müssen keine Codes in Ihrer App ändern.    

<span id="8.x-mediation"/>
### <a name="mediation-in-windows-81-and-windows-phone-8x-apps"></a>Anzeigenvermittlung in Windows8.1- und Windows Phone8.x-Apps

In Windows8.1 und Windows Phone8.x-Apps ist die Anzeigenvermittlung nur für Werbebanner verfügbar. Um die Anzeigenvermittlung zu verwenden, müssen Sie anstelle der **AdControl**-Klasse die **AdMediatorControl**-Klasse in der [Microsoft Advertising-SDK für Windows und Windows Phone8.x](http://aka.ms/store-8-sdk) verwenden. Nach Hinzufügen dieses Steuerelements zu Ihrer App können Sie die Einstellungen für die Anzeigenvermittlung manuell konfigurieren.

Weitere Informationen zur Verwendung der Anzeigenvermittlung in einer Windows8.1- oder Windows Phone8.x-App finden Sie unter [Inhalt dieses Artikels](https://msdn.microsoft.com/library/windows/apps/xaml/dn864359.aspx).

> [!NOTE]
> Die Anzeigenvermittlung für Windows8.1- und Windows Phone8.x-Apps wird nicht mehr weiterentwickelt. Um den Umsatz mit Anzeigen zu maximieren, empfehlen wir die Entwicklung von UWP-Apps, die die Anzeigenvermittlung mit Banneranzeigen, Interstitial-Anzeigen oder nativen Anzeigen.

## <a name="step-4-submit-your-app-and-review-performance"></a>Schritt 4: Übermitteln der App und Überprüfen der Leistung

Nach Abschluss der Entwicklung Ihrer App mit Werbung können Sie Ihre [aktualisierte App über das Windows Dev Center-Dashboard](https://msdn.microsoft.com/windows/uwp/publish/app-submissions) senden, damit sie im Store verfügbar ist. Apps, die Anzeigen darstellen, müssen zusätzlich die Anforderungen erfüllen, die in [Abschnitt 10.10 der Windows Store-Richtlinien](https://msdn.microsoft.com/library/windows/apps/dn764944.aspx#pol_10_10) [Anlage E der Vereinbarung für App-Entwickler](https://msdn.microsoft.com/library/windows/apps/hh694058.aspx) angegeben sind.

Nach der Veröffentlichung Ihrer App und im Store können Sie Ihre [Werbeleistungsberichte](../publish/advertising-performance-report.md) im Dashboard überprüfen und Änderungen an den für die Anzeigenvermittlung zur Optimierung der Leistung Ihrer Anzeigen vornehmen. Der Umsatz befindet sich in der [Auszahlungszusammenfassung](../publish/payout-summary.md).

<span id="additional-help" />
## <a name="additional-help"></a>Zusätzliche Hilfe

Weitere Hilfe zum Microsoft Advertising-SDK finden Sie in den folgenden Ressourcen.

|  Aufgabe    | Ressource |               
|----------|-------|
| Melden eines Fehlers und Supportunterstützung für Werbung     | Besuchen Sie die [Supportseite](https://go.microsoft.com/fwlink/p/?LinkId=331508), und wählen Sie **Werbung in Apps**.        |
| Community-Support erhalten     | Besuchen Sie das [Forum](http://go.microsoft.com/fwlink/p/?LinkId=401266).       |
| Laden Sie Beispielprojekte herunter, die veranschaulichen, wie Sie Banner und Interstitialwerbung zu Apps hinzufügen.     | Weitere Informationen finden Sie unter [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads).       |
| Weitere Informationen zu den neuesten Umsatzchancen für Windows-Apps     | Besuchen Sie Seite [Monetarisierung Ihrer Apps](https://developer.microsoft.com/store/monetize).        |

## <a name="related-topics"></a>Verwandte Themen

* [MicrosoftAdvertising-SDK](http://aka.ms/ads-sdk-uwp)
* [Monetarisierung Ihrer App mit Werbeanzeigen](http://go.microsoft.com/fwlink/p/?LinkId=699559)
* [Bericht zur Anzeigen-Performance](../publish/advertising-performance-report.md)
