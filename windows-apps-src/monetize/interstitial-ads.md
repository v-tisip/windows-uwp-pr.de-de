---
author: mcleanbyron
ms.assetid: 1f970d38-2338-470e-b5ba-811402752fc4
description: "Erfahren Sie mehr über die Verwendung von Interstitialwerbung in Windows 10-, Windows 8.1- oder Windows Phone 8.1-Apps mithilfe der Microsoft Advertising-Bibliotheken im Microsoft Store Services SDK."
title: Interstitialwerbung
translationtype: Human Translation
ms.sourcegitcommit: 2b5dbf872dd7aad48373f6a6df3dffbcbaee8090
ms.openlocfilehash: fae0fc57eca3477bf46a6f3ac43ec35781241a6e

---

# <a name="interstitial-ads"></a>Interstitialwerbung

In dieser Schritt-für-Schritt-Einführung wird die Verwendung von Interstitialwerbung in Windows 10-, Windows 8.1- oder Windows Phone 8.1-Apps mithilfe der Micrsosoft Advertising-Bibliotheken im Microsoft Store Services SDK gezeigt.

Vollständige Beispielprojekte, die das Hinzufügen von Interstitialwerbung zu JavaScript-/HTML- und XAML-Apps unter Verwendung von C# und C++ zeigen, finden Sie in den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).

<span id="whatareinterstitialads10"/>
## <a name="what-are-interstitial-ads"></a>Was ist Interstitialwerbung?

Im Gegensatz zu Banneranzeigen wird Interstitialwerbung (oder *Interstitialanzeigen*) auf dem gesamten Bildschirm der App angezeigt. In Spielen werden häufig zwei grundlegende Formen verwendet.

* Bei *Paywall*-Anzeigen muss der Benutzer eine Anzeige in regelmäßigen Intervallen ansehen. Dies findet beispielsweise zwischen Spiellevels statt:

    ![whatisaninterstitial](images/13-ed0a333b-0fc8-4ca9-a4c8-11e8b4392831.png)

* Bei *prämienbasierten* Anzeigen möchte der Benutzer ausdrücklich einen Vorteil nutzen, z. B. einen Hinweis oder zusätzliche Zeit zum Abschließen eines Levels erhalten, und initialisiert daher über die Benutzeroberfläche der App die Videoanzeige.

    Es ist wichtig, zu beachten, dass dieses SDK keine Benutzeroberfläche behandelt, ausgenommen zum Zeitpunkt der Videowiedergabe. Informieren Sie sich in den [bewährten Methoden für Interstitialwerbung](ui-and-user-experience-guidelines.md#interstitialbestpractices10) über Richtlinien für das, was Sie tun und was Sie vermeiden sollten, wenn Sie sich überlegen, wie Sie Interstitialwerbung in Ihre App integrieren können.

## <a name="build-an-app-with-interstitial-ads"></a>Erstellen einer App mit Interstitialwerbung

Befolgen Sie zum Anzeigen von Interstitialwerbung in Ihrer App die Anweisungen für den jeweiligen Projekttyp:

* [XAML/.NET](#interstitialadsxaml10)
* [HTML/JavaScript](#interstitialadshtml10)
* [C++ (DirectX Interop)](#interstitialadsdirectx10)

<span/>
### <a name="prerequisites"></a>Voraussetzungen

* Für UWP-Apps: Installieren Sie das [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) mit Visual Studio 2015.
* Für Windows 8.1- oder Windows Phone 8.1-Apps: Installieren Sie das [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk) mit Visual Studio 2015 oder Visual Studio 2013.

<span id="interstitialadsxaml10"/>
###<a name="xamlnet"></a>XAML/.NET

Dieser Abschnitt enthält Beispiele für C#. Visual Basic und C++ werden jedoch ebenfalls für XAML-/.NET-Projekte unterstützt. Ein vollständiges C#-Codebeispiel finden Sie unter [Beispielcode für Interstitialwerbung in C#](interstitial-ad-sample-code-in-c.md).

1. Öffnen Sie das Projekt in Visual Studio.

2. Wählen Sie im **Verweis-Manager** je nach Projekttyp einen der folgenden Verweise aus:

  * Für ein Projekt für die Universelle Windows-Plattform (UWP): Erweitern Sie **Universelles Windows**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für XAML** (Version 10.0).

  * Für ein Windows 8.1-Projekt: Erweitern Sie **Windows 8.1**, klicken Sie auf **Erweiterungen**, und aktivieren Sie anschließend das Kontrollkästchen neben **Ad Mediator SDK für Windows 8.1 XAML**. Mit dieser Option werden die Microsoft Advertising- und Ad Mediator-Bibliotheken dem Projekt hinzugefügt. Die Ad Mediator-Bibliotheken können Sie jedoch außer Acht lassen.

  * Für ein Windows Phone 8.1-Projekt: Erweitern Sie **Windows Phone 8.1**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Ad Mediator SDK für Windows Phone 8.1 XAML**. Mit dieser Option werden die Microsoft Advertising- und Ad Mediator-Bibliotheken dem Projekt hinzugefügt. Die Ad Mediator-Bibliotheken können Sie jedoch außer Acht lassen.

3.  Fügen Sie in der geeigneten Codedatei in Ihrer App (z. B. in „MainPage.xaml.cs“ oder einer Codedatei für eine andere Seite) den folgenden Namespaceverweis hinzu.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#Snippet1)]

4.  Deklarieren Sie an einer geeigneten Stelle in Ihrer App (z. B. in ```MainPage``` oder einer anderen Seite) ein [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx)-Objekt und mehrere Zeichenfolgenfelder, die die Anwendungs-ID und Anzeigeneinheits-ID für die Interstitialwerbung darstellen. Im folgenden Codebeispiel werden die Felder `myAppId` und `myAdUnitId` den unter [Testmoduswerte](test-mode-values.md) bereitgestellten Testwerten zugewiesen. Diese Werte werden nur zu Testzwecken verwendet. Sie müssen sie vor der Veröffentlichung Ihrer App durch Livewerte aus dem Windows Dev Center ersetzen.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#Snippet2)]

5.  Instanziieren Sie in Code, der beim Start ausgeführt wird (z. B. im Konstruktor der Seite) das **InterstitialAd**-Objekt, und verbinden Sie Ereignishandler für die Ereignisse des Objekts.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#Snippet3)]

6.  Verwenden Sie ungefähr 30 bis 60 Sekunden, bevor Sie die Interstitialwerbung benötigen, die [RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.requestad.aspx)-Methode, um die Anzeige vorab abzurufen. Dadurch bleibt genügend Zeit, um die Anzeige anzufordern und vorzubereiten, bevor sie angezeigt werden soll.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#Snippet4)]

6.  Bestätigen Sie an der Stelle im Code, an der die Anzeige angezeigt werden soll, dass **InterstitialAd** bereit zum Einblenden ist, und zeigen Sie sie dann mit der [Show](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.show.aspx)-Methode an.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#Snippet5)]

7.  Definieren Sie die Ereignishandler für das **InterstitialAd**-Objekt.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cs/MainPage.xaml.cs#Snippet6)]

8.  Erstellen und testen Sie Ihre App, um zu überprüfen, ob sie Testanzeigen anzeigt.

<span id="interstitialadshtml10"/>
###<a name="htmljavascript"></a>HTML/JavaScript

Bei den folgenden Anweisungen wird davon ausgegangen, dass Sie ein universelles Windows-Projekt für JavaScript in Visual Studio 2015 erstellt haben und dieses auf eine bestimmte CPU ausgerichtet ist. Ein vollständiges Codebeispiel finden Sie unter [Beispielcode für Interstitialwerbung in JavaScript](interstitial-ad-sample-code-in-javascript.md).

1. Öffnen Sie das Projekt in Visual Studio.

2.  Wählen Sie im **Verweis-Manager** je nach Projekttyp einen der folgenden Verweise aus:

  * Für ein Projekt für die Universelle Windows-Plattform (UWP): Erweitern Sie **Universelles Windows**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für JavaScript** (Version 10.0).

  * Für ein Windows 8.1-Projekt: Erweitern Sie **Windows 8.1**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für Windows 8.1 Native (JS)**.

  * Für ein Windows 8.1-Projekt: Erweitern Sie **Windows 8.1**, klicken Sie auf **Erweiterungen**, und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK for Windows Phone 8.1 Native (JS)**.

3.  Fügen Sie im Abschnitt **&lt;head&gt;** der HTML-Datei im Projekt nach den JavaScript-Projektverweisen von „default.css“ und „default.js“ den Verweis auf „ad.js“ ein. Fügen Sie in einem UWP-Projekt den folgenden Verweis hinzu.

  > [!div class="tabbedCodeSnippets"]
  ``` html
  <script src="//Microsoft.Advertising.JavaScript/ad.js"></script>
  ```

  Fügen Sie in einem Windows 8.1- oder Windows Phone 8.1-Projekt den folgenden Verweis hinzu.

  > [!div class="tabbedCodeSnippets"]
  ``` html
  <script src="/MSAdvertisingJS/ads/ad.js"></script>
  ```

4.  Deklarieren Sie in einer JS-Datei in Ihrem Projekt ein [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx)-Objekt und mehrere Felder, die die Anwendungs-ID und Anzeigeneinheits-ID für die Interstitialwerbung enthalten. Im folgenden Codebeispiel werden die Felder `applicationId` und `adUnitId` den unter [Testmoduswerte](test-mode-values.md) bereitgestellten Testwerten zugewiesen. Diese Werte werden nur zu Testzwecken verwendet. Sie müssen sie vor der Veröffentlichung Ihrer App durch Livewerte aus dem Windows Dev Center ersetzen.

  > [!div class="tabbedCodeSnippets"]
  [!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/script.js#Snippet1)]

5.  Instanziieren Sie in Code, der beim Start ausgeführt wird (z. B. im Konstruktor der Seite) das **InterstitialAd**-Objekt, und verbinden Sie Ereignishandler für das Objekt.

  > [!div class="tabbedCodeSnippets"]
  [!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/script.js#Snippet2)]

5. Verwenden Sie ungefähr 30 bis 60 Sekunden, bevor Sie die Interstitialwerbung benötigen, die [RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.requestad.aspx)-Methode, um die Anzeige vorab abzurufen. Dadurch bleibt genügend Zeit, um die Anzeige anzufordern und vorzubereiten, bevor sie angezeigt werden soll.

  > [!div class="tabbedCodeSnippets"]
  [!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/script.js#Snippet3)]

6.  Bestätigen Sie an der Stelle im Code, an der die Anzeige angezeigt werden soll, dass **InterstitialAd** bereit zum Einblenden ist, und zeigen Sie sie dann mit der [Show](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.show.aspx)-Methode an.

  > [!div class="tabbedCodeSnippets"]
  [!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/samples.js#Snippet4)]

7.  Definieren Sie die Ereignishandler für das **InterstitialAd**-Objekt.

  > [!div class="tabbedCodeSnippets"]
  [!code-javascript[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/js/samples.js#Snippet5)]

9.  Erstellen und testen Sie Ihre App, um zu überprüfen, ob sie Testanzeigen anzeigt.

<span id="interstitialadsdirectx10"/>
###<a name="c-directx-interop"></a>C++ (DirectX Interop)

In diesem Beispiel wird angenommen, dass Sie ein C++-Projekt **DirectX- und XAML-App (Universelle Windows-App)** in Visual Studio 2015 erstellt haben, das auf eine bestimmte CPU-Architektur ausgerichtet ist.
 
1. Öffnen Sie das Projekt in Visual Studio.

1.  Wählen Sie im **Verweis-Manager** je nach Projekttyp einen der folgenden Verweise aus:

  * Für ein Projekt für die Universelle Windows-Plattform (UWP): Erweitern Sie **Universelles Windows**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für XAML** (Version 10.0).

  * Für ein Windows 8.1-Projekt: Erweitern Sie **Windows 8.1**, klicken Sie auf **Erweiterungen**, und aktivieren Sie anschließend das Kontrollkästchen neben **Ad Mediator SDK für Windows 8.1 XAML**. Mit dieser Option werden die Microsoft Advertising- und Ad Mediator-Bibliotheken dem Projekt hinzugefügt. Die Ad Mediator-Bibliotheken können Sie jedoch außer Acht lassen.

  * Für ein Windows Phone 8.1-Projekt: Erweitern Sie **Windows Phone 8.1**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Ad Mediator SDK für Windows Phone 8.1 XAML**. Mit dieser Option werden die Microsoft Advertising- und Ad Mediator-Bibliotheken dem Projekt hinzugefügt. Die Ad Mediator-Bibliotheken können Sie jedoch außer Acht lassen.

2.  Deklarieren Sie in einer geeigneten Headerdatei für Ihre App (z. B. „DirectXPage.xaml.h“) ein [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx)-Objekt und verwandte Ereignishandlermethoden.  

  > [!div class="tabbedCodeSnippets"]
  [!code-cpp[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cpp/DirectXPage.xaml.h#Snippet1)]

3.  Deklarieren Sie in derselben Headerdatei mehrere Zeichenfolgenfelder, die die Anwendungs-ID und Anzeigeneinheits-ID für die Interstitialwerbung darstellen. Im folgenden Codebeispiel werden die Felder `myAppId` und `myAdUnitId` den unter [Testmoduswerte](test-mode-values.md) bereitgestellten Testwerten zugewiesen. Diese Werte werden nur zu Testzwecken verwendet. Sie müssen sie vor der Veröffentlichung Ihrer App durch Livewerte aus dem Windows Dev Center ersetzen.

  > [!div class="tabbedCodeSnippets"]
  [!code-cpp[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cpp/DirectXPage.xaml.h#Snippet2)]

4.  Fügen Sie in der CPP-Datei, an der Stelle, an der Sie Code zum Anzeigen einer Interstitialwerbung hinzufügen möchten, den folgenden Namespaceverweis hinzu. In den folgenden Beispielen wird davon ausgegangen, dass Sie den Code der Datei „DirectXPage.xaml.cpp“ in Ihrer App hinzufügen.

  > [!div class="tabbedCodeSnippets"]
  [!code-cpp[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cpp/DirectXPage.xaml.cpp#Snippet3)]

6.  Instanziieren Sie in Code, der beim Start ausgeführt wird (z. B. im Konstruktor der Seite) das **InterstitialAd**-Objekt, und verbinden Sie Ereignishandler für die Ereignisse des Objekts. Im folgenden Beispiel entspricht ```InterstitialAdSamplesCpp``` dem Namespace für Ihr Projekt. Ändern Sie diesen Namen nach Bedarf für Ihren Code.

  > [!div class="tabbedCodeSnippets"]
  [!code-cpp[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cpp/DirectXPage.xaml.cpp#Snippet4)]

7. Verwenden Sie ungefähr 30 bis 60 Sekunden, bevor Sie die Interstitialwerbung benötigen, die [RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.requestad.aspx)-Methode, um die Anzeige vorab abzurufen. Dadurch bleibt genügend Zeit, um die Anzeige anzufordern und vorzubereiten, bevor sie angezeigt werden soll.

  > [!div class="tabbedCodeSnippets"]
  [!code-cpp[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cpp/DirectXPage.xaml.cpp#Snippet5)]

7.  Bestätigen Sie an der Stelle im Code, an der die Anzeige angezeigt werden soll, dass **InterstitialAd** bereit zum Einblenden ist, und zeigen Sie sie dann mit der [Show](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.show.aspx)-Methode an.

  > [!div class="tabbedCodeSnippets"]
  [!code-cpp[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cpp/DirectXPage.xaml.cpp#Snippet6)]

8.  Definieren Sie die Ereignishandler für das **InterstitialAd**-Objekt.

  > [!div class="tabbedCodeSnippets"]
  [!code-cpp[InterstitialAd](./code/AdvertisingSamples/InterstitialAdSamples/cpp/DirectXPage.xaml.cpp#Snippet7)]

9. Erstellen und testen Sie Ihre App, um zu überprüfen, ob sie Testanzeigen anzeigt.

<span/>
### <a name="release-your-app-with-live-ads-using-windows-dev-center"></a>Veröffentlichen von Apps mit Liveanzeigen mithilfe von Windows Dev Center

1.  Rufen Sie im Dev Center-Dashboard die Seite **Monetarisierung** &gt; **Gewinnbringende Nutzung mit Anzeigen** für Ihre App auf, und [erstellen Sie eine Anzeigeneinheit](../publish/monetize-with-ads.md). Geben Sie für den Anzeigeneinheitentyp **Interstitialvideo** an. Notieren Sie sich die Anzeigeneinheits-ID und die Anwendungs-ID.

2.  Ersetzen Sie in Ihrem Code die Testanzeigen-Einheitenwerte mit den Livewerten, die Sie in Dev Center generiert haben.

3.  [Übermitteln Sie Ihre App](../publish/app-submissions.md) mithilfe des Windows Dev Center-Dashboards an den Store.

4.  Überprüfen Sie die [Anzeigenvermittlungsberichte](../publish/advertising-performance-report.md) im Dev Center-Dashboard.

<span id="interstitialbestpractices10"/>
## <a name="interstitial-best-practices-and-policies"></a>Richtlinien und bewährte Methoden für Interstitialwerbung


Weitere Informationen zur effizienten Nutzung von Interstitialwerbung und zu Richtlinien, die Sie befolgen müssen, finden Sie unter [Richtlinien und bewährte Methoden für Interstitialwerbung](ui-and-user-experience-guidelines.md#interstitialbestpractices10).

<span id="targetplatform10"/>
## <a name="remove-reference-errors-target-a-specific-cpu-platform-xaml-and-html"></a>Entfernen von Verweisfehlern: Ausrichtung auf eine bestimmte CPU-Plattform (XAML und HTML)


Wenn Sie die Microsoft Advertising-Bibliotheken verwenden, können Sie in Ihrem Projekt als Ziel nicht **Any CPU** angeben. Sollte in Ihrem Projekt die Zielplattform **Any CPU** definiert sein, wird in Ihrem Projekt eine Warnung ausgegeben, sobald Sie einen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen. Um diese Warnung zu entfernen, müssen Sie eine architekturspezifische Buildausgabe verwenden (beispielsweise **x86**) und das Projekt entsprechend aktualisieren. Weitere Informationen finden Sie unter [Bekannte Probleme](known-issues-for-the-advertising-libraries.md).

## <a name="related-topics"></a>Verwandte Themen


* [Beispielcode für Interstitialwerbung in C##](interstitial-ad-sample-code-in-c.md)
* [Beispielcode für Interstitialwerbung in JavaScript](interstitial-ad-sample-code-in-javascript.md)
* [Anzeigenbeispiele auf GitHub](http://aka.ms/githubads)

 

 



<!--HONumber=Dec16_HO2-->


