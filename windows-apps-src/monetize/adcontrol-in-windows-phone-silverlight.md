---
author: mcleanbyron
ms.assetid: c0450f7b-5c81-4d8c-92ef-2b1190d18af7
description: "Hier erfahren Sie, wie Sie die AdControl-Klasse nutzen können, um Werbebanner in einer Silverlight-App für Windows Phone 8.1 oder Windows Phone 8.0 anzuzeigen."
title: "„AdControl“ in Windows Phone Silverlight"
ms.author: mcleans
ms.date: 07/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, Silverlight, Windows Phone
ms.openlocfilehash: f1582639757abfb6de156bf88ce8af71ba3eaacd
ms.sourcegitcommit: a9e4be98688b3a6125fd5dd126190fcfcd764f95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2017
---
# <a name="adcontrol-in-windows-phone-silverlight"></a>„AdControl“ in Windows Phone Silverlight

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie die [AdControl](https://msdn.microsoft.com/library/windows/apps/hh524191.aspx)-Klasse nutzen können, um Werbebanner in einer Silverlight-App für Windows Phone8.1 oder Windows Phone8.0 anzuzeigen.

<span id="silverlight_support"/>
## <a name="advertising-support-for-windows-phone-8x-silverlight-projects"></a>Anzeigenunterstützung für Windows Phone8.x Silverlight-Projekte

Einige Entwicklerszenarien werden für Windows Phone8.x Silverlight-Projekte nicht mehr unterstützt. Weitere Informationen finden Sie in der folgenden Tabelle.

|  Plattformversion  |  Vorhandene Projekte    |   Neue Projekte  |
|-----------------|----------------|--------------|
| Windows Phone8.0 Silverlight     |  Wenn Sie über ein vorhandenes Windows Phone8.0 Silverlight-Projekt verfügen, das bereits eine **AdControl** bzw. **AdMediatorControl** einer früheren Version des Universal Ad Client SDK oder Microsoft Advertising SDK verwendet, und die App bereits im Windows Store veröffentlicht wurde, können Sie das Projekt bearbeiten und neu erstellen. Zudem können Sie Ihre Änderungen auf einem Gerät debuggen oder testen. Das Debuggen und Testen des Projekts im Emulator wird nicht unterstützt.  |  Nicht unterstützt  |
| Windows Phone8.1 Silverlight    |  Wenn Sie über ein vorhandenes Windows Phone8.1 Silverlight-Projekt verfügen, das ein **AdControl** oder **AdMediatorControl** einer früheren SDK verwendet, können Sie es ändern und neu erstellen. Zum Debuggen oder Testen der App müssen Sie die App jedoch im Emulator ausführen und für die Anwendungs- und Anzeigeneinheits-ID die [Testmoduswerte](test-mode-values.md) verwenden. Das Debuggen oder Testen der App auf einem Gerät wird nicht unterstützt.  |   Sie können ein **AdControl** oder **AdMediatorControl** zu einem neuen Windows Phone8.1 Silverlight-Projekt hinzufügen. Zum Debuggen oder Testen der App müssen Sie die App jedoch im Emulator ausführen und für die Anwendungs- und Anzeigeneinheits-ID die [Testmoduswerte](test-mode-values.md) verwenden. Das Debuggen oder Testen der App auf einem Gerät wird nicht unterstützt. |

## <a name="add-the-advertising-assemblies-to-your-project"></a>Hinzufügen der Advertising-Assemblys zum Projekt

Laden Sie zuerst das NuGet-Paket mit den Microsoft Advertising-Assemblys für Windows Phone Silverlight herunter, und installieren Sie es für Ihr Projekt.

1.  Öffnen Sie das Projekt in Visual Studio.

2.  Klicken Sie auf **Extras**, zeigen Sie auf **NuGet-Paket-Manager**, und klicken Sie auf **Paket-Manager-Konsole**.

3.  Geben Sie im Fenster **Paket-Manager-Konsole** einen dieser Befehle ein.

  * Geben Sie diesen Befehl ein, wenn Ihr Projekt für Windows Phone8.0 bestimmt ist.

      ```syntax
      Install-Package Microsoft.Advertising.WindowsPhone.SL80 -Version 6.2.40501.1
      ```

  * Geben Sie diesen Befehl ein, wenn Ihr Projekt für Windows Phone8.1 bestimmt ist.

      ```syntax
      Install-Package Microsoft.Advertising.WindowsPhone.SL81 -Version 8.1.50112
      ```

    Nach der Eingabe des Befehls werden alle erforderlichen Microsoft Advertising-Assemblys für Silverlight für Ihr lokales Projekt als NuGet-Pakete heruntergeladen. Verweise auf diese Assemblys werden dem Projekt automatisch hinzugefügt.

## <a name="code-your-app"></a>Ihr App-Code


1.  Füge Sie in Ihrer Datei „WMAppManifest.xml“ dem Knoten **Funktionen** die folgenden Funktionen hinzu.

  ``` syntax
  <Capability Name="ID_CAP_IDENTITY_USER"/>
  <Capability Name="ID_CAP_MEDIALIB_PHOTO"/>
  <Capability Name="ID_CAP_PHONEDIALER"/>
  ```

  In diesem Beispiel sieht Ihr Knoten **Funktionen** wie folgt aus:

  ``` syntax
  <Capabilities>
      <Capability Name="ID_CAP_NETWORKING"/>
      <Capability Name="ID_CAP_MEDIALIB_AUDIO"/>
      <Capability Name="ID_CAP_MEDIALIB_PLAYBACK"/>
      <Capability Name="ID_CAP_SENSORS"/>
      <Capability Name="ID_CAP_WEBBROWSERCOMPONENT"/>
      <Capability Name="ID_CAP_IDENTITY_USER"/>
      <Capability Name="ID_CAP_MEDIALIB_PHOTO"/>
      <Capability Name="ID_CAP_PHONEDIALER"/>
  </Capabilities>
  ```

2.  Optional: Speichern Sie Ihr Projekt. Klicken Sie auf das Symbol **Alles speichern** oder klicken Sie im Menü **Datei** auf **Alles speichern**.

3.  Fügen Sie die Funktion **Internet (Client und Server)**zur Package.appxmanifest-Datei in Ihrem Projekt hinzu. Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **appxmanifest**.

    ![wp81silverlightmarkup\-Solutionexplorer\-packageappxmanifest](images/13-b98c2a1a-69c3-4018-be0a-6ce010e703e7.jpg)

    Klicken Sie im **Editor** auf die Registerkarte **Funktionen**. Überprüfen Sie das Feld **Internet (Client und Server)**.

4.  Optional: Speichern Sie Ihr Projekt. Klicken Sie auf das Symbol **Alles speichern** oder klicken Sie im Menü **Datei** auf **Alles speichern**.

5.  Ändern Sie das Silverlight-Markup in der Datei „MainPage.xaml“, sodass es den **Microsoft.Advertising.Mobile.UI**- Namespace enthält.

  ``` xml
  xmlns:UI="clr-namespace:Microsoft.Advertising.Mobile.UI;assembly=Microsoft.Advertising.Mobile.UI"
  ```

  Die Kopfzeile Ihrer Seite enthält den folgenden Code:

  ``` xml
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
  xmlns:UI="clr-namespace:Microsoft.Advertising.Mobile.UI;assembly=Microsoft.Advertising.Mobile.UI"
  x:Class="PhoneApp1.MainPage"
  ```

6.  Fügen Sie im **Raster**-Tag den folgenden Code für die **AdControl** ein. Weisen Sie den Eigenschaften **ApplicationId** und **AdUnitId** die unter [Testmoduswerte](test-mode-values.md) bereitgestellten Testwerte zu und passen Sie die Eigenschaften **Höhe** und **Breite** auf eines der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) an.

  > **Hinweis**&nbsp;&nbsp;Sie ersetzen die Testwerte **ApplicationId** und **AdUnitId** durch Livewerte, bevor Sie Ihre App übermitteln.

  ``` xml
  <Grid x:Name="ContentPanel" Grid.Row="1">
      <UI:AdControl
          ApplicationId="3f83fe91-d6be-434d-a0ae-7351c5a997f1"
          AdUnitId="10865270"
          HorizontalAlignment="Left"
          Height="80"
          VerticalAlignment="Top"
          Width="480"/>
  </Grid>
  ```

7.  Erstellen und Ausführen des Projekts Stellen Sie sicher, dass Ihre App eine Anzeige zeigt, die in etwa wie folgt aussieht:

  ![wp81silverlight\-emulatorwithad](images/13-8db1492f-ae1d-439b-9b78-bed8e22fe996.jpg)

## <a name="release-your-app-with-live-ads-using-dev-center"></a>Veröffentlichen der App mit Live-Werbung mithilfe von Dev Center

1.  Rufen Sie für Ihre App im Dev Center-Dashboard die Seite **Monetarisierung** &gt; **Gewinnbringende Nutzung mit Anzeigen** auf, und [erstellen Sie eine eigenständige Anzeigeneinheit](../publish/monetize-with-ads.md). Geben Sie als Einheitentyp **Banner** an. Notieren Sie sich die Anzeigeeinheits-ID und die Anwendungs-ID.

2.  Ersetzen Sie in Ihrem Code die Testwerte der Anzeigenheit (**applicationId** und **adUnitId**) mit den Live-Werten, die Sie in Dev Center generiert haben.

3.  [Übermitteln Sie Ihre App](../publish/app-submissions.md) mithilfe des Dev Center-Dashboards an den Store.

4.  Überprüfen Sie die [Anzeigenvermittlungsberichte](../publish/advertising-performance-report.md) auf dem Dev Center-Dashboard.


 
