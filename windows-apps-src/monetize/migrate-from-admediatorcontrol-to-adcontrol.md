---
author: mcleanbyron
ms.assetid: 9621641A-7462-425D-84CC-101877A738DA
description: Lesen Sie, wie Sie Ihre UWP-Apps von AdMediatorControl auf AdControl umstellen.
title: Migrieren Ihrer UWP-Apps von AdMediatorControl zu AdControl
translationtype: Human Translation
ms.sourcegitcommit: 2b5dbf872dd7aad48373f6a6df3dffbcbaee8090
ms.openlocfilehash: 6e7e833327dce4b49e44b7485908c8a507b217ef

---

# <a name="migrate-from-admediatorcontrol-to-adcontrol-for-uwp-apps"></a>Migrieren Ihrer UWP-Apps von AdMediatorControl zu AdControl

In den Vorversionen des Advertising SDK von Microsoft konnten UWP- (Universelle Windows-Plattform-)Apps mit der Klasse **AdMediatorControl** Werbebanner anzeigen. Damit konnten Entwickler ihren Anzeigenumsatz optimieren, indem Sie Anzeigen von Werbebannern aus unseren Partnernetzwerken (AOL und AppNexus) sowie von AdDuplex anzeigen. Das [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) unterstützt die Klasse **AdMediatorControl** nicht mehr. Wenn Sie eine App haben, die die Klasse **AdMediatorControl** aus einem früheren SDK verwendet, und Sie diese App in eine UWP-Anwendung umwandeln möchten, die das [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) verwendet, folgen Sie den Anweisungen in diesem Artikel, um Ihren Quellcode so zu ändern, dass die Klasse **AdControl** anstelle von **AdMediatorControl** verwendet. Optional können Sie Ihre App so konfigurieren, das Werbung von AdDuplex eingeblendet wird, wobei ein gewichteter oder Rangfolgeansatz verwendet wird.

>**Note**&nbsp;&nbsp;Die in diesem Artikel verwendeten Codebeispiele dienen nur zur Veranschaulichung. Sie müssen die Codebeispiele möglicherweise anpassen, damit sie in Ihrer App funktionieren.

## <a name="prerequisites"></a>Voraussetzungen

* Eine UWP-App, die derzeit AdMediatorControl verwendet und in Windows Store veröffentlicht ist.
* Ein Entwicklungscomputer mit Visual Studio 2015 und installiertem [Microsoft Store Services SDK](http://aka.ms/store-em-sdk).
* Wenn Sie Werbung mit AdDuplex vermitteln möchten, muss auf dem Entwicklungscomputer auch das [AdDuplex-Windows 10-SDK](https://visualstudiogallery.msdn.microsoft.com/6930860a-e64b-4b46-9d72-62d7fddda077) installiert sein.

  >**Hinweis**&nbsp;&nbsp;Sie können den AdDuplex-SDK-Installer über den Link oben ausführen, Sie können jedoch stattdessen auch die AdDuplex-Bibliotheken für Ihr UWP-App-Projekt in Visual Studio 2015 installieren. Stellen Sie sicher, dass Ihr UWP-App-Projekt in Visual Studio 2015 geöffnet ist, klicken Sie dann auf **Projekt** > **NuGet-Pakete verwalten**, suchen Sie nach dem NuGet-Paket mit dem Namen **AdDuplexWin10**, und installieren Sie das Paket.

## <a name="step-1-retrieve-your-application-ids-and-ad-unit-ids"></a>Schritt 1: Abrufen Ihrer Anwendungs-IDs und Ihrer Anzeigeneinheits-IDs

Wenn Sie den Code so modifizieren, dass die Klasse **AdControl** verwendet wird, benötigen Sie Ihre Anwendungs-IDs und Anzeigeneinheits-IDs. Die beste Möglichkeit zum Abrufen der neuesten IDs ist, diese aus Ihrer Konfigurationsdatei für die Anzeigenvermittlung auszulesen.

1. Melden Sie sich am Windows Dev Center-Dashboard an, und klicken Sie auf der App, die derzeit noch **AdMediatorControl** verwendet.
2. Klicken Sie auf **Monetarisierung** und **Monetarisierung durch Anzeigen**.
3. Klicken Sie im Abschnitt **Windows-Anzeigenvermittlung** auf den Link **Vermittlungskonfiguration herunterladen**, und öffnen Sie die Datei „AdMediator.config“ in einem Texteditor wie Editor.
4. Suchen Sie in der Datei das Element ```<AdAdapterInfo>``` mit dem untergeordneten Element ```<Name>MicrosoftAdvertising</Name>```. Dieser Abschnitt enthält die Konfiguration für die kostenpflichtige Werbeanzeigen von Microsoft.
5. Suchen Sie in ```<AdAdapterInfo>``` die ```<Property>```-Elemente, die ```<Key>```-Elemente mit den Werten **WApplicationId** bzw. **WAdUnitId** enthalten. Im Beispiel unten sind die Werte der ```<Value>```-Elemente nur als Beispiel zu verstehen.

  > [!div class="tabbedCodeSnippets"]
  ```xml
  <Metadata>
      <Property>
          <Key>WApplicationId</Key>
          <Value>364d4938-c0f5-4c3d-8aae-090206211dc9</Value>
      </Property>
      <Property>
          <Key>WAdUnitId</Key>
          <Value>301568</Value>
      </Property>
  </Metadata>
  ```

6. Kopieren Sie die beiden Werte in diesen ```<Value>```-Elementen zur späteren Verwendung. Diese Werte enthalten die Anwendungs-ID und die Anzeigeneinheits-ID für die nicht-mobile Anzeigeneinheit für kostenpflichtige Werbeanzeigen von Microsoft.
5. Suchen Sie, ebenfalls im Element ```<AdAdapterInfo>```, die ```<Property>```-Elemente, die ```<Key>```-Elemente mit den Werten **MApplicationId** bzw. **MAdUnitId** enthalten. Im Beispiel unten sind die Werte der ```<Value>```-Elemente nur als Beispiel zu verstehen.

  > [!div class="tabbedCodeSnippets"]
  ```xml
  <Metadata>
      <Property>
          <Key>MApplicationId</Key>
          <Value>e2cf8388-7018-4a11-8ab0de90f2a7a401</Value>
      </Property>
      <Property>
          <Key>MAdUnitId</Key>
          <Value>301056</Value>
      </Property>
  </Metadata>
  ```

6. Kopieren Sie die beiden Werte in den ```<Value>```-Elementen zur späteren Verwendung. Diese Werte enthalten die Anwendungs-ID und die Anzeigeneinheits-ID für die mobile Anzeigeneinheit für kostenpflichtige Werbeanzeigen von Microsoft.
7. Wenn Sie [Eigenwerbung](../publish/about-house-ads.md) nutzen, suchen Sie das Element ```<AdAdapterInfo>``` mit dem untergeordneten Element ```<Name>MicrosoftAdvertisingHouse</Name>```. Suchen Sie in diesem Element nach ```<Key>```-Elementen mit den Werten **MAdUnitId** bzw. **WAdUnitId**, und speichern Sie die Werte der entsprechenden ```<Value>```-Elemente zur späteren Verwendung. Dies sind die mobile und die nicht-mobile Anzeigeneinheits-ID für Microsoft-Eigenwerbung.
8. Wenn Sie AdDuplex verwenden, suchen Sie das ```<AdAdapterInfo>```-Element mit dem untergeordneten Element ```<Name>AdDuplex</Name>```. Suchen Sie in diesem Element nach den ```<Key>```-Elementen mit den Werten **AppKey** bzw. **AdUnitId**, und speichern Sie die Werte der entsprechenden ```<Value>```-Elemente zur späteren Verwendung. Dies sind Ihr AdDuplex-App-Schlüssel und die Anzeigeneinheits-ID.

## <a name="step-2-update-your-app-code"></a>Schritt 2: Aktualisieren des App-Codes

Nun, da Sie Ihre Anwendungs-IDs und die Anzeigeneinheits-IDs haben, sind Sie bereit, den in Ihrer App verwenden Code so zu modifizieren, dass **AdControl** anstelle von **AdMediatorControl** verwendet wird.

### <a name="microsoft-paid-ads-only"></a>Nur kostenpflichtige Werbeanzeigen von Microsoft

Wenn Sie in Ihrer Konfiguration der Anzeigenvermittlung nur kostenpflichtige Werbeanzeigen von Microsoft verwenden, gehen Sie wie folgt vor:

  >**Hinweis**&nbsp;&nbsp;Bei den folgenden Anweisungen wird davon ausgegangen, dass die App-Seite, auf der Werbeanzeigen angezeigt werden sollen, ein leeres Raster mit dem Namen **myAdGrid** enthält. Beispiel: ```<Grid x:Name="myAdGrid"/>```. In den folgenden Schritten erstellen und konfigurieren Sie die Steuerelemente für die Werbeanzeigen im Quellcode, und nicht in XAML.

1. Öffnen Sie das UWP-App-Projekt in Visual Studio.
2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen** aus.
Erweitern Sie im **Verweis-Manager** den Knoten **Universal Windows**, klicken Sie auf **Erweiterungen**, und wählen Sie dann das Kontrollkästchen neben **Microsoft Advertising SDK für XAML** (Version 10.0).
3. Klicken Sie im **Verweis-Manager** auf „OK“.
4. Entfernen Sie die **AdMediatorControl**-Deklaration aus dem XAML-Code, und entfernen Sie weiter jeden Code, der dieses **AdMediatorControl**-Objekt verwendet, einschließlich der zugehörigen Ereignishandler.
5. Öffnen Sie die Codedatei für die App-**Seite**, auf der die Werbeanzeigen angezeigt werden sollen.
6. Fügen Sie die folgende Anweisung am Anfang der Codedatei ein, wenn noch nicht vorhanden.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[TrialVersion](./code/AdvertisingSamples/MigrateToAdControl/cs/MainPage.xaml.cs#Snippet1)]

7. Fügen Sie Ihrer **Page**-Klasse die folgenden Konstantendeklarationen hinzu.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[TrialVersion](./code/AdvertisingSamples/MigrateToAdControl/cs/MainPage.xaml.cs#Snippet2)]

7. Ersetzen Sie für jede dieser Konstantendeklarationen die Werte wie im Folgenden beschrieben:

  * **AD_WIDTH** und **AD_HEIGHT**: Weisen Sie diesen Konstanten eine der [unterstützten Anzeigengrößen für Werbebanner]( https://msdn.microsoft.com/windows/uwp/monetize/supported-ad-sizes-for-banner-ads) zu.
  * **WAPPLICATIONID** und **WADUNITID**: Weisen Sie diesen Konstanten die **WApplicationId**- bzw. **WAdUnitId**-Werte für kostenpflichtige Werbeanzeigen von Microsoft zu, die Sie zuvor aus der Konfigurationsdatei für die Anzeigenvermittlung ausgelesen haben (dies sind die Werte für die nicht-mobile Anzeigeneinheit für kostenpflichtige Werbeanzeigen).
  * **MAPPLICATIONID** und **MADUNITID**: Weisen Sie diesen Konstanten die **MApplicationId**- bzw. **MAdUnitId**-Werte für kostenpflichtige Werbeanzeigen von Microsoft zu, die Sie zuvor aus der Konfigurationsdatei für die Anzeigenvermittlung ausgelesen haben (dies sind die Werte für die mobile Anzeigeneinheit für kostenpflichtige Werbeanzeigen).

8. Fügen Sie Ihrer **Page**-Klasse die folgenden Variablendeklarationen hinzu.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[AdControl](./code/AdvertisingSamples/MigrateToAdControl/cs/MainPage.xaml.cs#Snippet3)]

5. Fügen Sie dem Konstruktor der **Page**-Klasse nach dem Aufruf der Methode **InitializeComponent()** folgenden Code hinzu.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[AdControl](./code/AdvertisingSamples/MigrateToAdControl/cs/MainPage.xaml.cs#Snippet4)]

### <a name="microsoft-paid-ads-house-ads-and-adduplex"></a>Kostenpflichtige Werbeanzeigen von Microsoft, Eigenwerbung und AdDuplex

Wenn Sie Microsoft-Eigenwerbung oder AdDuplex sowie kostenpflichtige Werbeanzeigen von Microsoft verwenden und weiterhin Werbung mit AdDuplex vermitteln möchten, folgen Sie den Anweisungen in diesem Abschnitt. Die Codebeispiele unterstützen sowohl AdDuplex als auch Microsoft-Eigenwerbung. Falls Sie AdDuplex, aber keine Microsoft-Eigenwerbung verwenden oder umgekehrt, entfernen Sie den Code, der für Ihr Szenario nicht zutrifft.

  >**Hinweis**&nbsp;&nbsp;Bei den folgenden Anweisungen wird davon ausgegangen, dass die App-Seite, auf der Werbeanzeigen angezeigt werden sollen, ein leeres Raster mit dem Namen **myAdGrid** enthält. Beispiel: ```<Grid x:Name="myAdGrid"/>```. In den folgenden Schritten erstellen und konfigurieren Sie die Steuerelemente für die Werbeanzeigen im Quellcode, und nicht in XAML.

1. Öffnen Sie das UWP-App-Projekt in Visual Studio.
2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen** aus.
Erweitern Sie im **Verweis-Manager** den Knoten **Universal Windows**, klicken Sie auf **Erweiterungen**, und wählen Sie dann das Kontrollkästchen neben **Microsoft Advertising SDK für XAML** (Version 10.0).
3. Klicken Sie im **Verweis-Manager** auf „OK“.
4. Entfernen Sie die **AdMediatorControl**-Deklaration aus dem XAML-Code, und entfernen Sie weiter jeden Code, der dieses **AdMediatorControl**-Objekt verwendet, einschließlich der zugehörigen Ereignishandler.
5. Öffnen Sie die Codedatei für die App-**Seite**, auf der die Werbeanzeigen angezeigt werden sollen.
6. Fügen Sie am Anfang der Codedatei die folgenden Anweisungen hinzu, wenn noch nicht vorhanden.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[AdControl](./code/AdvertisingSamples/MigrateToAdControl/cs/ExamplePage1.xaml.cs#Snippet1)]

7. Fügen Sie Ihrer **Page**-Klasse die folgenden Konstantendeklarationen hinzu.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[AdControl](./code/AdvertisingSamples/MigrateToAdControl/cs/ExamplePage1.xaml.cs#Snippet2)]

4. Ersetzen Sie für diese Konstantendeklarationen die Werte wie im Folgenden beschrieben:

  * **AD_WIDTH** und **AD_HEIGHT**: Weisen Sie diesen Konstanten eine der [unterstützten Anzeigengrößen für Werbebanner]( https://msdn.microsoft.com/windows/uwp/monetize/supported-ad-sizes-for-banner-ads) zu.
  * **HOUSE_AD_WEIGHT**: Weisen Sie dieser Konstante einen Integerwert zwischen 0 und 100 zu, der die Gewichtung für Microsoft-Eigenwerbung im Verhältnis zu den kostenpflichtigen Werbeanzeigen von Microsoft angibt (bei 0 wird keine Eigenwerbung angezeigt, bei 100 ausschließlich Eigenwerbung).
  * **WAPPLICATIONID** und **WADUNITID_PAID**: Weisen Sie diesen Konstanten die **WApplicationId**- bzw. **WAdUnitId**-Werte für kostenpflichtige Werbeanzeigen von Microsoft zu, die Sie zuvor aus der Konfigurationsdatei für die Anzeigenvermittlung ausgelesen haben (dies sind die Werte für die nicht-mobile Anzeigeneinheit für kostenpflichtige Werbeanzeigen).
  * **WADUNITID_HOUSE**: Weisen Sie dieser Konstante den **WAdUnitId**-Wert für Eigenwerbung zu, die Sie zuvor aus der Konfigurationsdatei für die Anzeigenvermittlung ausgelesen haben (dieser Wert ist für die nicht-mobile Anzeigeneinheit für Eigenwerbung).
  * **MAPPLICATIONID** und **MADUNITID_PAID**: Weisen Sie diesen Konstanten die **MApplicationId**- bzw. **MAdUnitId**-Werte für kostenpflichtige Werbeanzeigen von Microsoft zu, die Sie zuvor aus der Konfigurationsdatei für die Anzeigenvermittlung ausgelesen haben (dies sind die Werte für die mobile Anzeigeneinheit für kostenpflichtige Werbeanzeigen).
  * **MADUNITID_HOUSE**: Weisen Sie dieser Konstante den **MAdUnitId**-Wert für Eigenwerbung zu, die Sie zuvor aus der Konfigurationsdatei für die Anzeigenvermittlung ausgelesen haben (dieser Wert ist für die mobile Anzeigeneinheit für Eigenwerbung).
  * **ADDUPLEX_APPKEY** und **ADDUPLEX_ADUNIT**: Weisen Sie diese dem AdDuplex-App-Schlüssel und den ID-Werten der Anzeigeneinheit zu, die Sie zuvor aus der Konfigurationsdatei für die Anzeigenvermittlung abgerufen haben.

  >**Hinweis**&nbsp;&nbsp;Ändern Sie nicht die **AD_REFRESH_SECONDS**- und **MAX_ERRORS_PER_REFRESH**-Werte, die im vorherigen Beispiel gezeigt wurden.

5. Fügen Sie Ihrer **Page**-Klasse die folgenden Variablendeklarationen hinzu.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[AdControl](./code/AdvertisingSamples/MigrateToAdControl/cs/ExamplePage1.xaml.cs#Snippet3)]

5. Fügen Sie dem Konstruktor der **Page**-Klasse nach dem Aufruf der Methode **InitializeComponent()** folgenden Code hinzu.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[AdControl](./code/AdvertisingSamples/MigrateToAdControl/cs/ExamplePage1.xaml.cs#Snippet4)]

6. Fügen Sie schließlich der **Page**-Klasse die folgenden Methoden hinzu. Diese Methoden instanziieren die Microsoft **AdControl**- und AdDuplex **AdControl**-Objekte. Die Methoden verwenden einen Zufallszahlengenerator in Verbindung mit den angegebenen Gewichtungswerten, um in diesen Steuerelementen Werbebanner in regelmäßigen, von einem Zeitgeber vorgegebenen Intervallen zu aktualisieren.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[AdControl](./code/AdvertisingSamples/MigrateToAdControl/cs/ExamplePage1.xaml.cs#Snippet5)]



<!--HONumber=Dec16_HO2-->


