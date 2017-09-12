---
author: mcleanbyron
description: "Erfahren Sie, wie Sie native Anzeigen zu Ihrer UWP-App hinzufügen."
title: Native Anzeigen
ms.author: mcleans
ms.date: 06/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, Ad-Steuerelement, native Anzeige
ms.openlocfilehash: 47a69e48f04c670a462c34083af1117d2c7908d8
ms.sourcegitcommit: 8c4d50ef819ed1a2f8cac4eebefb5ccdaf3fa898
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2017
---
# <a name="native-ads"></a>Native Anzeigen

Eine native Anzeige ist ein komponentenbasiertes Anzeigenformat, in denen jedes Element der Anzeige (wie Titel, Bild, Beschreibung und Handlungsaufforderungstext) als einzelnes Element übermittelt wird, das Sie in Ihre App integrieren können. Sie können diese Elemente mit eigenen Schriftarten, Farben, Animationen und andere Komponenten der Benutzeroberfläche in Ihrer App integrieren und so eine Benutzerfunktionalität schaffen, die perfekt in das Erscheinungsbild Ihrer App passt und hohe Einnahmen mit Anzeigen generieren.

Für Werbekunden bieten native anzeigen perfekte Platzierungen, da Anzeigen-Umgebung eng in die App integriert ist und die Benutzer daher dazu neigen, mehr Interaktion mit diesen Arten von anzeigen durchzuführen.

> [!NOTE]
> Um native anzeigen für die öffentliche Version Ihrer App im Store bereitzustellen, müssen Sie eine **native** Anzeigeneinheit über die Seite **Monetarisierung durch Anzeigen** im Dev Center-Dashboard erstellen. Die Möglichkeit zum Erstellen von **nativen** Anzeigeeinheiten steht derzeit nur für Entwickler zur Verfügung, die an einem Pilotprogramm teilnehmen, wir möchten dieses Feature allerdings bald für alle Entwickler zur Verfügung stellen. Wenn Sie an unserem Pilotprogramms teilnehmen möchten, wenden Sie sich an aiacare@microsoft.com.

> [!NOTE]
> Native Anzeigen werden derzeit nur für XAML-basierte UWP-Apps für Windows10 unterstützt. Die Unterstützung für UWP-Apps mit HTML und JavaScript ist für eine zukünftige Version des Microsoft Advertising-SDK geplant.

## <a name="prerequisites"></a>Voraussetzungen

* Installieren Sie das [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) (Version 10.0.4 oder höher) mit Visual Studio2015 oder einer neueren Version von Visual Studio. Installationsanweisungen finden Sie in [diesem Artikel](install-the-microsoft-advertising-libraries.md). Sie können das SDK auf Ihrem Entwicklungscomputer über das MSI-Installationsprogramm installieren, oder Sie können das SDK für die Verwendung in einem bestimmten Projekt über das NuGet-Paket installieren.

## <a name="integrate-a-native-ad-into-your-app"></a>Native Anzeigen in Ihrer App integrieren

Befolgen Sie diesen Anweisungen, um eine native Anzeige in Ihrer App zu integrieren und vergewissern Sie sich, dass der Implementierung der nativen Anzeige eine Test-Anzeige angezeigt.

1. Öffnen Sie in Visual Studio Ihr Projekt oder erstellen Sie ein neues Projekt.

2. Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, müssen Sie eine architekturspezifische Buildausgabe verwenden (z. B. **X86**) und das Projekt entsprechend aktualisieren. Sollte in Ihrem Projekt die Zielplattform **Jede CPU** definiert sein, können Sie bei den folgenden Schritten keinen Verweis auf das Microsoft Advertising-SDK hinzufügen. Weitere Informationen finden Sie unter [Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden](known-issues-for-the-advertising-libraries.md#reference_errors).

3.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.

4.  Erweitern Sie im **Verweis-Manager** den Knoten **Universal Windows**, klicken Sie auf **Erweiterungen**, und wählen Sie dann das Kontrollkästchen neben **Microsoft Advertising-SDK für XAML** (Version 10.0).

5.  Klicken Sie im **Verweis-Manager** auf „OK“.

6. Fügen Sie in der geeigneten Codedatei in Ihrer App (z.B. in „MainPage.xaml.cs“ oder einer Codedatei für eine andere Seite) den folgenden Namespaceverweis hinzu.

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#Namespaces)]

7.  Deklarieren Sie an einer geeigneten Stelle in Ihrer App (z.B. in ```MainPage``` oder einer anderen Seite) ein [NativeAdsManager](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.aspx)-Objekt und mehrere Zeichenfolgenfelder, die die Anwendungs-ID und Anzeigeneinheits-ID für die native Anzeige darstellen. Im folgenden Codebeispiel werden die Felder `myAppId` und `myAdUnitId` den [Testwerten](test-mode-values.md) für native Anzeigen zugewiesen.

    > [!NOTE]
    > Jedes **NativeAdsManager**-Objekt verfügt über eine entsprechende *Anzeigeneinheit* die durch unsere Dienste zum Anzeigen des nativen Anzeigensteuerelements verwendet wird, und jede Anzeigeneinheit besteht aus einer *Anzeigeneinheits-ID* und *Anwendungs-ID*. In den folgenden Schritten weisen Sie dem Steuerelement eine Anzeigeneinheits-ID und Anwendungs-ID zu. Dieser Test Werte können nur in einer Testversion Ihrer App verwendet werden. Bevor Sie Ihre App im Store veröffentlichen, müssen Sie [die Testwerte mit den Live-Werten](#release) aus dem Windows Dev Center ersetzen.

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#Variables)]

8.  Instanziieren Sie in Code, der beim Start ausgeführt wird (z.B. im Konstruktor der Seite) das **NativeAdsManager**-Objekt, und verbinden Sie Ereignishandler für die Ereignisse [AdReady](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.adready.aspx) und [ErrorOccurred](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.erroroccurred.aspx) des Objekts.

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#ConfigureNativeAd)]

9.  Wenn Sie bereit sind, einen native Anzeige anzuzeigen, rufen Sie die [RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.requestad.aspx)-Methode auf, um eine Anzeige abzurufen.

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#RequestAd)]

10.  Wenn eine native Anzeige für Ihre App bereit ist, wird Ihr **AdReady**-Ereignishandler aufgerufen und ein [NativeAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.aspx)-Objekt für die native Anzeige wird im *e*-Parameter übergeben. Verwenden Sie die **NativeAd**-Eigenschaften, um jedes Element der nativen Anzeige abrufen und diese Elemente auf der Seite anzuzeigen. Achten Sie darauf, dass Sie auch die [RegisterAdContainer](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.registeradcontainer.aspx)-Methode aufrufen, um die UI-Element zu registrieren, die als Container für die native Anzeige dienen. Dies ist erforderlich, um Anzeigenaufrufe und -klicks ordnungsgemäß nachzuverfolgen.
  > [!NOTE]
  > Einige Elemente der nativen Anzeige sind erforderlich und müssen immer in Ihrer App angezeigt werden. Weitere Informationen finden Sie im Abschnitt [Anforderungen und Richtlinien](#requirements-and-guidelines).

    Nehmen wir beispielsweise an, Ihre App enthält eine ```MainPage``` (oder eine andere Seite) mit dem folgenden **StackPanel**. Dies **StackPanel** enthält eine Reihe von Steuerelementen, die verschiedenen Elemente einer nativen Anzeige darstellen (z.B. Titel, Beschreibung, Bilder, *unterstützt von*-Text und eine Schaltfläche, die den *Handlungsaufforderung*-Text darstellt).

    ``` xml
    <StackPanel x:Name="NativeAdContainer" Background="#555555" Width="Auto" Height="Auto"
                Orientation="Vertical">
        <Image x:Name="AdIconImage" HorizontalAlignment="Left" VerticalAlignment="Center"
               Margin="20,20,20,20"/>
        <TextBlock x:Name="TitleTextBlock" HorizontalAlignment="Left" VerticalAlignment="Center"
               Text="The ad title will go here" FontSize="24" Foreground="White" Margin="20,0,0,10"/>
        <TextBlock x:Name="DescriptionTextBlock" HorizontalAlignment="Left" VerticalAlignment="Center"
                   Foreground="White" TextWrapping="Wrap" Text="The ad description will go here"
                   Margin="20,0,0,0" Visibility="Collapsed"/>
        <Image x:Name="MainImageImage" HorizontalAlignment="Left"
               VerticalAlignment="Center" Margin="20,20,20,20" Visibility="Collapsed"/>
        <Button x:Name="CallToActionButton" Background="Gray" Foreground="White"
                HorizontalAlignment="Left" VerticalAlignment="Center" Width="Auto" Height="Auto"
                Content="The call to action text will go here" Margin="20,20,20,20"
                Visibility="Collapsed"/>
        <StackPanel x:Name="SponsoredByStackPanel" Orientation="Horizontal" Margin="20,20,20,20">
            <TextBlock x:Name="SponsoredByTextBlock" Text="The ad sponsored by text will go here"
                       FontSize="24" Foreground="White" Margin="20,0,0,0" HorizontalAlignment="Left"
                       VerticalAlignment="Center" Visibility="Collapsed"/>
            <Image x:Name="IconImageImage" Margin="40,20,20,20" HorizontalAlignment="Left"
                   VerticalAlignment="Center" Visibility="Collapsed"/>
        </StackPanel>
    </StackPanel>
    ```

    Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen **AdReady**-Ereignishandler nutzen, der jedes Element der nativen Anzeige in den Steuerelementen im **StackPanel** angezeigt und dann die **RegisterAdContainer**-Methode zur Registrierung des **StackPanel** aufruft. In diesem Code wird davon ausgegangen, dass sie aus der CodeBehind-Datei für die Seite ausgeführt wird, die enthält **StackPanel** enthält.

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#AdReady)]

11.  Definiert einen Ereignishandler für das **ErrorOccurred**-Ereignis zum Behandeln von Fehlern im Zusammenhang mit der nativen Anzeige. Das folgende Beispiel schreibt Fehlerinformationen in das Visual Studio **Ausgabe**-Fenster während der Tests.

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#ErrorOccurred)]

12.  Kompilieren und Ausführen der App, um eine Testanzeige zu sehen.

<span id="release" />
## <a name="release-your-app-with-live-ads"></a>Veröffentlichen Ihrer App mit Live-Anzeigen

Nachdem Sie bestätigt, dass der Implementierung der nativen Anzeige erfolgreich eine Test-Anzeige angezeigt, befolgen Sie diese Anweisungen, um die Konfiguration der App für echte Anzeigen durchzuführen und die aktualisierte App an den Store zu übermitteln.

1.  Stellen Sie sicher, dass die Implementierung der nativen Anzeigen den [Anforderungen und Richtlinien](#requirements-and-guidelines) für native Anzeigen folgt.

2.  Rufen Sie im Dev Center-Dashboard die Seite [Monetarisierung mit Anzeigen](../publish/monetize-with-ads.md) für Ihre App auf, und [erstellen Sie eine Anzeigeneinheit](../monetize/set-up-ad-units-in-your-app.md). Geben Sie als Einheitentyp **Nativ** an. Notieren Sie sich die Anzeigeneinheits-ID und die Anwendungs-ID.
    > [!IMPORTANT]
    > Sie können jede Anzeigeneinheit in nur einer App verwenden. Wenn Sie eine Anzeigeneinheit in mehr als einer App verwenden, werden für die Ad-Einheit keine Anzeigen platziert.

3. Sie können optional die Anzeigenvermittlung für die nativen Anzeige durch das Konfigurieren der Einstellungen in der [Anzeigenvermittlung](../publish/monetize-with-ads.md#mediation) auf der Seite [Monetarisierung durch Anzeigen](../publish/monetize-with-ads.md) aktivieren. Mit der Anzeigenvermittlung können Sie Ihren Anzeigenumsatz und Funktionalitäten zur App-Bewerbung durch die Darstellung von Anzeigen aus mehreren Anzeigennetzwerken verbessern.

4.  Ersetzen Sie in Ihrem Code die Testwerte der Anzeigeneinheit (Parameter *applicationId* und *adUnitId* des [NativeAdsManager](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.nativeadsmanager.aspx)-Konstruktors) mit den Live-Werten, die Sie in Dev Center generiert haben.

5.  [Übermitteln Sie Ihre App](../publish/app-submissions.md) mithilfe des Dev Center-Dashboards an den Store.

6.  Überprüfen Sie die [Anzeigenvermittlungsberichte](../publish/advertising-performance-report.md) im Dev Center-Dashboard.

<span id="requirements-and-guidelines" />
## <a name="requirements-and-guidelines"></a>Anforderungen und Richtlinien

Mit nativen Anzeigen haben Sie eine hohe Kontrolle über die Darstellung von Werbeinhalten für Ihre Benutzer. Befolgen Sie diese Anforderungen und Richtlinien, um sicherzustellen, dass die Werbebotschaft Ihre Benutzer erreicht und gleichzeitig eine verwirrend Anzeigeerfahrung für Ihre Benutzer verhindert wird.

### <a name="register-the-container-for-your-native-ad"></a>Registrieren Sie den Container für die native Anzeige

In Ihrem Code müssen Sie die [RegisterAdContainer](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.registeradcontainer.aspx)-Methode des **NativeAd**-Objekts aufrufen, um das UI-Element zu registrieren, das als Container für die native Anzeige agiert und optional alle speziellen Steuerelemente, die Sie als klickbare Ziele für die Anzeige registrieren möchten. Dies ist erforderlich, um Anzeigenaufrufe und -klicks ordnungsgemäß nachzuverfolgen.

Es gibt zwei Überladungen für die **RegisterAdContainer**-Methode, die Sie verwenden können:

* Wenn Sie den gesamten Container für alle nativen Anzeigenelemente klickbar gestalten möchten, rufen Sie die [RegisterAdContainer(FrameworkElement)](https://msdn.microsoft.com/library/windows/apps/mt809188.aspx)-Methode auf und übergeben den zu steuernden Container an die Methode. Wenn Sie beispielsweise alle nativen Anzeigenelemente in separaten Steuerelementen anzeigen, die alle in einem **StackPanel** gehostet werden, und das gesamte **StackPanel** klickbar sein soll, übergeben Sie das **StackPanel** an diese Methode.

* Wenn Sie nur bestimmte native Anzeigenelemente klickbar gestalten möchten, rufen Sie die [RegisterAdContainer (FrameworkElement, IVector(FrameworkElement))](https://msdn.microsoft.com/library/windows/apps/mt809189.aspx)-Methode auf. Nur die Steuerelemente, die Sie über den zweiten Parameter übergeben, werden klickbar.

### <a name="required-native-ad-elements"></a>Erforderliche native Anzeigenelemente

Sie müssen mindestens folgenden Elemente der native Anzeigenelemente für den Benutzer anzeigen. Wenn Sie diese Elemente nicht einbeziehen, entsteht möglicherweise eine schlechte Leistung und es gibt wenige Aufrufe für Ihre Anzeigeneinheit.

1. Zeigen Sie immer den Titel der nativen Anzeige an (verfügbar in der [Titel](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.title.aspx)-Eigenschaft des **NativeAd**-Objekts). Bieten Sie ausreichend Platz zum Anzeigen von mindestens 25 Zeichen. Wenn der Titel länger ist, ersetzen Sie den zusätzlichen Text mit den Auslassungszeichen.
2. Zeigen Sie immer mindestens eines der folgenden Elemente an, um die native Anzeige vom Rest der App klar zu unterscheiden und die Herkunft der Inhalte von einem Werbepartner herauszustellen:
  * Das eindeutige *Anzeigen*-Symbol (verfügbar in der [AdIcon](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.adicon.aspx)-Eigenschaft des **NativeAd**-Objekts). Dieses Symbol wird von Microsoft bereitgestellt.
  * Der *unterstützt von*-Text (verfügbar in der [SponsoredBy](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.sponsoredby.aspx)-Eigenschaft des **NativeAd**-Objekts). Dieser Text wird vom Werbepartner bereitgestellt.
  * Als Alternative zum *unterstützt von*-Text können Sie einige andere Text anzeigen, die die native Anzeige vom Rest der App abgrenzen (z.B. „Gesponsert Inhalt“, „Werbeinhalte“, „Empfohlene Inhalte“).

### <a name="user-experience"></a>Benutzerfreundlichkeit

Ihre native Anzeige sollte von den restlichen Ihrer App klar abgegrenzt werden und mit einem Rand versehentliche Klicks verhindern. Verwenden Sie Rahmen, andere Hintergründen und andere UI-Elemente, um die Inhalte vom Rest der App zu trennen. Bedenken Sie, dass versehentlich Anzeigen-Klicks auf lange Sicht nicht für den Umsatz mit Anzeigen oder Ihre Endbenutzererfahrung von Vorteil sind.

### <a name="description"></a>Description

Wenn Sie die Beschreibung für die Anzeige anzeigen (verfügbar in der [Description](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.description.aspx) Eigenschaft des **NativeAd**-Objekts), bieten Sie ausreichend Platz zum Anzeigen von mindestens 75 Zeichen. Es wird empfohlen, dass Sie eine Animation verwenden, um den gesamten Inhalt der Anzeigenbeschreibung anzuzeigen.

### <a name="call-to-action"></a>Handlungsaufforderung

Der *Handlungsaufforderung*-Text (verfügbar in der [CallToAction](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.calltoaction.aspx)-Eigenschaft des **NativeAd**-Objekts) ist eine wichtige Komponente der Anzeige. Wenn Sie diesen Text anzeigen möchten, befolgen Sie diese Richtlinien:

* Zeigen Sie den *Handlungsaufforderung*-Text immer auf einen klickbaren Steuerelemente (z.B. eine Schaltfläche oder einen Link) für den Benutzer an.
* Zeigen Sie den *Handlungsaufforderung*-Text immer vollständig an.
* Stellen Sie sicher, dass der *Handlungsaufforderung*-Text vom restlichen Werbetext des Werbepartners getrennt ist.

### <a name="learn-and-optimize"></a>Lernen und Optimieren

Es wird empfohlen, dass Sie verschiedene Anzeigeeinheiten für jede andere native Anzeigenplatzierung in Ihrer App erstellen und verwenden. Dadurch können Sie separate Berichtsdaten für jede native Anzeigenplatzierung abrufen, und diese Daten zur Optimierung der Leistung der einzelnen einheitlichen Anzeigenplatzierungen verwenden.

## <a name="related-topics"></a>Verwandte Themen

* [Monetarisierung durch Anzeigen](../publish/monetize-with-ads.md)
* [Einrichten von Anzeigeneinheiten für die App](../monetize/set-up-ad-units-in-your-app.md)
