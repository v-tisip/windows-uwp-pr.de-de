---
author: stevewhims
description: Die Vorgehensweise zum Definieren einer Benutzeroberfläche in Form von deklarativem XAML-Markup lässt sich sehr gut von WindowsPhone Silverlight für universelle Windows-Plattform (UWP) apps.
title: Portieren von WindowsPhone Silverlight-XAML und UI zu UWP
ms.assetid: 49aade74-5dc6-46a5-89ef-316dbeabbebe
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d219a09ccca74c9fc513b7510c40ce0b90ad9f52
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6840326"
---
#  <a name="porting-windowsphone-silverlight-xaml-and-ui-to-uwp"></a>Portieren von WindowsPhone Silverlight-XAML und UI zu UWP



Im vorherigen Thema haben wir uns mit der [Problembehandlung](wpsl-to-uwp-troubleshooting.md) beschäftigt.

Die Vorgehensweise zum Definieren einer Benutzeroberfläche in Form von deklarativem XAML-Markup lässt sich sehr gut von WindowsPhone Silverlight für universelle Windows-Plattform (UWP) apps. Sie werden feststellen, dass große Abschnitte Ihres Markups kompatibel sind, sobald Sie Verweise auf Systemressourcenschlüssel aktualisiert, einige Namen von Elementtypen geändert und „clr-namespace“ in „using“ geändert haben. Ein Großteil des imperativen Codes in Ihrer Darstellungsschicht–Ansichtsmodelle und Code, der UI-Elemente ändert,–kann ebenfalls problemlos portiert werden.

## <a name="a-first-look-at-the-xaml-markup"></a>Ein erster Blick auf das XAML-Markup

Im vorherige Thema wurde gezeigt, wie Ihre XAML und Code-Behind kopiert Dateien in das neue Windows 10 Visual Studio-Projekt. Eines der ersten Probleme, das im XAML-Designer von Visual Studio hervorgehoben sein könnte, ist die Tatsache, dass das `PhoneApplicationPage`-Element im Stamm der XAML-Datei für ein Projekt der Universellen Windows-Plattform (UWP) ungültig ist. Im vorherigen Thema gespeichert wurde eine Kopie des XAML-Dateien, die Visual Studio generiert, wenn sie das Windows 10-Projekt erstellt wurde. Wenn Sie diese Version von „MainPage.xaml“ öffnen, sehen Sie im Stamm den Typ [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503), der im [**Windows.UI.Xaml.Controls**](https://msdn.microsoft.com/library/windows/apps/br227716)-Namespace enthalten ist. Sie können also alle `<phone:PhoneApplicationPage>`-Elemente in `<Page>` ändern (denken Sie an die Eigenschaftselementsyntax) und die `xmlns:phone` -Deklaration löschen.

Einen allgemeineren Ansatz zum Ermitteln des UWP-Typs, die eine WindowsPhone Silverlight-Typ entspricht, können Sie auf [Namespace und klassenzuordnungen](wpsl-to-uwp-namespace-and-class-mappings.md)verweisen.

## <a name="xaml-namespace-prefix-declarations"></a>XAML-Namespacepräfixdeklarationen


Falls Sie in Ihren Ansichten Instanzen von benutzerdefinierten Typen verwenden–vielleicht eine Ansichtsmodellinstanz oder einen Wertkonverter–, enthält Ihr XAML-Markup XAML-Namespacepräfixdeklarationen. Die Syntax dieser Deklarationen unterscheidet WindowsPhone Silverlight und der UWP. Einige Beispiele:

```xml
    xmlns:ContosoTradingCore="clr-namespace:ContosoTradingCore;assembly=ContosoTradingCore"
    xmlns:ContosoTradingLocal="clr-namespace:ContosoTradingLocal"
```

Ändern Sie „clr-namespace“ in „using“, und löschen Sie alle Assemblytokens und Semikolons (die Assembly wird abgeleitet). Das Ergebnis sieht wie folgt aus:

```xml
    xmlns:ContosoTradingCore="using:ContosoTradingCore"
    xmlns:ContosoTradingLocal="using:ContosoTradingLocal"
```

Sie haben vielleicht eine Ressource, deren Typ vom System definiert wird:

```xml
    xmlns:System="clr-namespace:System;assembly=mscorlib"
    /* ... */
    <System:Double x:Key="FontSizeLarge">40</System:Double>
```

Lassen Sie in der UWP die Präfixdeklaration „System“ weg, und verwenden Sie stattdessen das (bereits deklarierte) Präfix „x“:

```xml
    <x:Double x:Key="FontSizeLarge">40</x:Double>
```

## <a name="imperative-code"></a>Imperativer Code


Ihre Ansichtsmodelle sind eine der Stellen, an denen imperativer Code auf UI-Typen verweist. In CodeBehind-Dateien, die UI-Elemente direkt ändern, ist dies ebenfalls der Fall. Es kann beispielsweise vorkommen, dass das Kompilieren einer Codezeile wie der folgenden noch nicht möglich ist:


```csharp
    return new BitmapImage(new Uri(this.CoverImagePath, UriKind.Relative));
```

**BitmapImage** ist im Namespace **System.Windows.Media.Imaging** in WindowsPhone Silverlight und eine using-Direktive in derselben Datei ermöglicht **BitmapImage** wie im Codeausschnitt oben ohne Namespacequalifizierung verwendet werden. In einem solchen Fall können Sie in Visual Studio mit der rechten Maustaste auf den Typnamen (**BitmapImage**) klicken und der Datei mit dem Befehl **Resolve** im Kontextmenü eine neue Namespacedirektive hinzufügen. In diesem Fall wird der [**Windows.UI.Xaml.Media.Imaging**](https://msdn.microsoft.com/library/windows/apps/br243258)-Namespace hinzugefügt, in dem sich der Typ in der UWP befindet. Sie können die using-Direktive **System.Windows.Media.Imaging** entfernen. Mehr müssen Sie nicht tun, um Code wie den im obigen Codeausschnitt zu portieren. Wenn Sie fertig sind, müssen Sie alle WindowsPhone Silverlight-Namespaces entfernt haben.

In einfachen Fällen wie diesem, in denen Sie die Typen in einem alten Namespace den gleichen Typen in einem neuen Namespace zuordnen, können Sie mit dem Visual Studio-Befehl **Suchen und ersetzen** Massenänderungen an Ihrem Quellcode vornehmen. Der Befehl **Resolve** ist eine großartige Methode, um den neuen Namespace eines Typs zu ermitteln. Sie können beispielsweise auch alle Vorkommen von „System.Windows“ durch „Windows.UI.Xaml“ ersetzen. Dadurch werden im Grunde alle Direktiven und vollqualifizierten Typnamen portiert, die auf diesen Namespace verweisen.

Nachdem Sie alle alten using-Direktiven entfernt und die neuen Direktiven hinzugefügt haben, können Sie den Visual Studio-Befehl **Using-Direktiven organisieren** verwenden, um Ihre Direktiven zu sortieren und nicht verwendete Direktiven zu entfernen.

Manchmal müssen Sie zum Reparieren von imperativem Code nur den Typ eines Parameters ändern. In anderen Fällen müssen Sie UWP-APIs anstelle von .NET APIs für Windows-Runtime 8.x-apps zu verwenden. Identifizieren der unterstützten APIs, verwenden den Rest dieses Handbuchs für in Kombination mit [Übersicht über .NET für Windows-Runtime 8.x-apps](https://msdn.microsoft.com/library/windows/apps/xaml/br230302.aspx) und der [Windows-Runtime-Referenz](https://msdn.microsoft.com/library/windows/apps/br211377).

Falls Sie lediglich zu der Phase gelangen möchten, in der Ihr Projekt erstellt wird, können Sie allen nicht unbedingt erforderlichen Code auskommentieren. Gehen Sie anschließend nacheinander die einzelnen Probleme anhand der Informationen in den folgenden Themen dieses Abschnitts (einschließlich des vorherigen Themas [Problembehandlung](wpsl-to-uwp-troubleshooting.md)) durch, bis alle Erstellungs- und Laufzeitprobleme behoben sind und die Portierung abgeschlossen ist.

## <a name="adaptiveresponsive-ui"></a>Adaptive/reaktionsfähige Benutzeroberfläche

Da Ihre Windows 10-app auf eine potenziell Breite Palette von Geräten ausgeführt werden kann – jeweils mit eigener Bildschirmgröße und-Auflösung – sollten Sie die mindestens erforderlichen Schritte zum Portieren Ihrer app hinausgehen, und Sie Ihre Benutzeroberfläche, um die am besten auf diesen Geräten aussehen anpassen möchten. Sie können das adaptive Visual State-Manager-Feature nutzen, um die Fenstergröße dynamisch zu ermitteln und als Reaktion darauf das Layout zu ändern. Ein Beispiel zur Vorgehensweise finden Sie im Abschnitt [Adaptive UI](wpsl-to-uwp-case-study-bookstore2.md) im Thema mit der Bookstore2-Fallstudie.

## <a name="alarms-and-reminders"></a>Alarme und Erinnerungen

Code mit den Klassen **Alarm** oder **Reminder** sollte zur Verwendung der [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Klasse portiert werden, um eine Hintergrundaufgabe zu erstellen und zu registrieren und zum entsprechenden Zeitpunkt ein Popup anzuzeigen. Siehe [Hintergrundverarbeitung](wpsl-to-uwp-business-and-data.md) und [Popups](#toasts).

## <a name="animation"></a>Animation

Als bevorzugte Alternative zu Keyframeanimationen und Von/Zu-Animationen ist die UWP-Animationsbibliothek für UWP-Apps verfügbar. Diese Animationen wurden speziell entwickelt und optimiert, damit sie flüssig angezeigt werden, großartig aussehen und den Eindruck vermitteln, dass Ihre App in gleichem Maße in Windows integriert ist wie die standardmäßig integrierten Apps. Siehe [Schnellstart: Animieren der Benutzeroberfläche anhand von Bibliotheksanimationen](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703).

Falls Sie Keyframeanimationen oder Von/Zu-Animationen in Ihren UWP-Apps verwenden, sollten Sie sich mit der bei der neuen Plattform eingeführten Unterscheidung zwischen unabhängigen und abhängigen Animationen vertraut machen. Informationen finden Sie unter [Optimieren von Animationen und Medien](https://msdn.microsoft.com/library/windows/apps/mt204774). Im UI-Thread ausgeführte Animationen (z.B. zum Animieren von Layouteigenschaften) werden als abhängige Animationen bezeichnet. Damit diese Animationen auf der neuen Plattform funktionieren, müssen Sie ein oder zwei Schritte ausführen. Sie können sie zum Animieren anderer Eigenschaften (z.B. [**RenderTransform**](https://msdn.microsoft.com/library/windows/apps/br208980)) neu zuweisen und dadurch zu unabhängigen Animationen machen. Alternativ können Sie `EnableDependentAnimation="True"` für das Animationselement festlegen, um zu bestätigen, dass Sie eine Animation ausführen möchten, deren reibungslose Ausführung nicht garantiert werden kann. Wenn Sie Blend für Visual Studio zum Erstellen neuer Animationen verwenden, wird diese Eigenschaft bei Bedarf für Sie festgelegt.

## <a name="back-button-handling"></a>Behandeln der Schaltfläche „Zurück“

In einer Windows 10-app können Sie einen einheitlichen Ansatz für die Behandlung der Schaltfläche "zurück", und es funktioniert auf allen Geräten. Auf mobilen Geräten wird die Schaltfläche für Sie als kapazitive Schaltfläche auf dem Gerät oder als Schaltfläche in der Shell bereitgestellt. Auf einem Desktopgerät fügen Sie den Chromelementen der App eine Schaltfläche hinzu, wenn die Rückwärtsnavigation in der App möglich ist. Sie wird für Apps mit Fenstern in der Titelleiste und im Tabletmodus in der Taskleiste angezeigt. Das Ereignis der Schaltfläche „Zurück“ ist ein universelles Konzept, das für alle Gerätefamilien gilt. Für Schaltflächen, die in Hardware oder Software implementiert werden, wird das gleiche [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596)-Ereignis ausgelöst.

Das Beispiel unten funktioniert für alle Gerätefamilien und eignet sich gut für Fälle, in denen für alle Seiten die gleiche Verarbeitung gilt und in denen während der Navigation keine Bestätigung erforderlich ist (z. B. bei einer Warnung vor ungespeicherten Änderungen).

```csharp
   // app.xaml.cs

    protected override void OnLaunched(LaunchActivatedEventArgs e)
    {
        [...]

        Windows.UI.Core.SystemNavigationManager.GetForCurrentView().BackRequested += App_BackRequested;
        rootFrame.Navigated += RootFrame_Navigated;
    }

    private void RootFrame_Navigated(object sender, NavigationEventArgs e)
    {
        Frame rootFrame = Window.Current.Content as Frame;

        // Note: On device families that have no title bar, setting AppViewBackButtonVisibility can safely execute 
        // but it will have no effect. Such device families provide a back button UI for you.
        if (rootFrame.CanGoBack)
        {
            Windows.UI.Core.SystemNavigationManager.GetForCurrentView().AppViewBackButtonVisibility = 
                Windows.UI.Core.AppViewBackButtonVisibility.Visible;
        }
        else
        {
            Windows.UI.Core.SystemNavigationManager.GetForCurrentView().AppViewBackButtonVisibility = 
                Windows.UI.Core.AppViewBackButtonVisibility.Collapsed;
        }
    }

    private void App_BackRequested(object sender, Windows.UI.Core.BackRequestedEventArgs e)
    {
        Frame rootFrame = Window.Current.Content as Frame;

        if (rootFrame.CanGoBack)
        {
            rootFrame.GoBack();
        }
    }
```

Es gibt auch einen einheitlichen Ansatz zum programmgesteuerten Beenden der App für alle Gerätefamilien.

```csharp
   Windows.UI.Xaml.Application.Current.Exit();
```

## <a name="binding-and-compiled-bindings-with-xbind"></a>Bindungen und kompilierte Bindungen mit {x:Bind}

Folgende Punkte werden in diesem Thema behandelt:

-   Binden von UI-Elementen an „Daten“ (d.h. an die Eigenschaften und Befehle eines Ansichtsmodells)
-   Binden von UI-Elementen an andere UI-Elemente
-   Erstellen eines Ansichtsmodells, das feststellbar ist (d.h. das Benachrichtigungen auslöst, wenn ein Eigenschaftswert geändert wird und sich die Verfügbarkeit eines Befehls ändert)

All diese Aspekte werden zumeist weiter unterstützt, aber es gibt Unterschiede bei den Namespaces. **System.Windows.Data.Binding** entspricht beispielsweise [**Windows.UI.Xaml.Data.Binding**](https://msdn.microsoft.com/library/windows/apps/br209820), **System.ComponentModel.INotifyPropertyChanged** entspricht [**Windows.UI.Xaml.Data.INotifyPropertyChanged**](https://msdn.microsoft.com/library/windows/apps/br209899) und **System.Collections.Specialized.INotifyPropertyChanged** entspricht [**Windows.UI.Xaml.Interop.INotifyCollectionChanged**](https://msdn.microsoft.com/library/windows/apps/hh702001).

WindowsPhone Silverlight-app-leisten und Schaltflächen können nicht gebunden werden, wie sie in einer UWP-app können. Sie können imperativen Code verwenden, der die App-Leiste und die zugehörigen Schaltflächen erstellt, diese an Eigenschaften und lokalisierte Zeichenfolgen bindet und ihre Ereignisse behandelt. In diesem Fall haben Sie jetzt die Möglichkeit, den imperativen Code zu portieren, indem Sie ihn durch an Eigenschaften und Befehle gebundenes deklaratives Markup und statische Ressourcenverweise ersetzen. Dadurch können Sie die Sicherheit und Wartbarkeit der App inkrementell verbessern. Sie können UWP-App-Leisten-Schaltflächen wie alle anderen XAML-Elemente mithilfe von Visual Studio oder Blend für Visual Studio binden und formatieren. Beachten Sie, dass Sie in einer UWP-App die Typnamen [**CommandBar**](https://msdn.microsoft.com/library/windows/apps/dn279427) und [**AppBarButton**](https://msdn.microsoft.com/library/windows/apps/dn279244) verwenden.

Für bindungsbezogene Features von UWP-Apps gelten momentan die folgenden Einschränkungen:

-   Es gibt keine integrierte Unterstützung für die Überprüfung von Dateneingaben und die Schnittstellen [**IDataErrorInfo**](https://msdn.microsoft.com/library/system.componentmodel.idataerrorinfo.aspx) und [**INotifyDataErrorInfo**](https://msdn.microsoft.com/library/system.componentmodel.inotifydataerrorinfo.aspx).
-   Die [**Binding**](https://msdn.microsoft.com/library/windows/apps/br209820) -Klasse umfasst nicht die erweiterten Formatierungseigenschaften, die in WindowsPhone Silverlight verfügbar sind. Sie können jedoch weiterhin [**IValueConverter**](https://msdn.microsoft.com/library/windows/apps/br209903) implementieren, um eine benutzerdefinierte Formatierung bereitzustellen.
-   Die [**IValueConverter**](https://msdn.microsoft.com/library/windows/apps/br209903)-Methoden akzeptieren Sprachzeichenfolgen als Parameter anstelle von [**CultureInfo**](https://msdn.microsoft.com/library/system.globalization.cultureinfo.aspx)-Objekten.
-   Die [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/br209833)-Klasse bietet keine integrierte Unterstützung für Sortier- und Filtervorgänge, und das Gruppieren funktioniert anders. Weitere Informationen finden Sie unter [Datenbindung im Detail](https://msdn.microsoft.com/library/windows/apps/mt210946) und im [Beispiel zur Datenbindung](http://go.microsoft.com/fwlink/p/?linkid=226854).

Zwar weiterhin größtenteils die gleichen Features für die Bindung unterstützt, Windows 10 bietet die Möglichkeit, einen neuen und leistungsfähigeren Bindungsmechanismus aufgerufen kompilierten Bindungen, die die Markuperweiterung {X: Bind}. Informationen hierzu finden Sie unter [Datenbindung: Stärken der App-Performance dank neuer Verbesserungen bei der XAML-Datenbindung](http://channel9.msdn.com/Events/Build/2015/3-635) und [x:Bind-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619989).

## <a name="binding-an-image-to-a-view-model"></a>Binden eines Bilds an ein Ansichtsmodell

Sie können die [**Image.Source**](https://msdn.microsoft.com/library/windows/apps/br242760)-Eigenschaft an eine beliebige Eigenschaft eines Ansichtsmodells vom Typ [**ImageSource**](https://msdn.microsoft.com/library/windows/apps/br210107) binden. Hier ist eine typische Implementierung einer solchen Eigenschaft in einer WindowsPhone-Silverlight-app:

```csharp
    // this.BookCoverImagePath contains a path of the form "/Assets/CoverImages/one.png".
    return new BitmapImage(new Uri(this.CoverImagePath, UriKind.Relative));
```

In einer UWP-App verwenden Sie das [URI-Schema](https://msdn.microsoft.com/library/windows/apps/jj655406) „ms-appx“. Damit Sie den Rest des Codes beibehalten können, können Sie eine andere Überladung des **System.Uri**-Konstruktors verwenden, um das URI-Schema „ms-appx“ in einen Basis-URI einzufügen und den restlichen Pfad anzuhängen. Hier sehen Sie ein Beispiel:

```csharp
    // this.BookCoverImagePath contains a path of the form "/Assets/CoverImages/one.png".
    return new BitmapImage(new Uri(new Uri("ms-appx://"), this.CoverImagePath));
```

Auf diese Weise können der Rest des Ansichtsmodells, die Pfadwerte in der Bildpfadeigenschaft und die Bindungen im XAML-Markup unverändert bleiben.

## <a name="controls-and-control-stylestemplates"></a>Steuerelemente und Steuerelementstile/-vorlagen

WindowsPhone Silverlight-apps verwenden Sie Steuerelemente, die in den Namespace **Microsoft.Phone.Controls** und **System.Windows.Controls** -Namespace definiert. XAML-UWP-Apps verwenden im [**Windows.UI.Xaml.Controls**](https://msdn.microsoft.com/library/windows/apps/br227716)-Namespace definierte Steuerelemente. Die Architektur und das Design von XAML-Steuerelementen in der UWP ist nahezu identisch mit WindowsPhone Silverlight-Steuerelemente. Einige Änderungen wurden allerdings vorgenommen, um die verfügbaren Steuerelemente zu verbessern und mit Windows-Apps zu vereinheitlichen. Spezielle Beispiele:

| Name des Steuerelements | Ändern |
|--------------|--------|
| ApplicationBar | Die Eigenschaft [Page.TopAppBar](https://msdn.microsoft.com/library/windows/apps/hh702575). |
| ApplicationBarIconButton | Das UWP-Äquivalent ist die [Glyph](https://msdn.microsoft.com/library/windows/apps/dn279538)-Eigenschaft. PrimaryCommands ist die Inhaltseigenschaft von CommandBar. Der XAML-Parser interpretiert das innere XML des Elements als Wert der Inhaltseigenschaft. |
| ApplicationBarMenuItem | Die UWP-Entsprechung ist das auf den Menüelementtext festgelegte [AppBarButton.Label](https://msdn.microsoft.com/library/windows/apps/dn279261). |
| ContextMenu (im Windows Phone-Toolkit) | Verwenden Sie für ein einzelnes Auswahlflyout [Flyout](https://msdn.microsoft.com/library/windows/apps/dn279496). |
| ControlTiltEffect.TiltEffect-Klasse | Animationen aus der UWP-Animationsbibliothek sind in die Standardstile der allgemeinen Steuerelemente integriert. Siehe [Animieren von Zeigeraktionen](https://msdn.microsoft.com/library/windows/apps/xaml/jj649432). |
| LongListSelector mit gruppierten Daten | Die WindowsPhone Silverlight LongListSelector funktioniert auf zwei Arten, die zusammen verwendet werden können. Erstens kann es nach einem Schlüssel gruppierte Daten anzeigen, z. B. eine nach dem Anfangsbuchstaben gruppierte Liste mit Namen. Zweitens kann es zwischen zwei semantischen Ansichten „zoomen“: der gruppierten Liste von Elementen (z.B. Namen) und einer Liste, die nur die Gruppenschlüssel selbst enthält (z.B. Anfangsbuchstaben). Bei der UWP können Sie gruppierte Daten mit den [Richtlinien für Listenansicht- und Rasteransichtsteuerelementen anzeigen](https://msdn.microsoft.com/library/windows/apps/mt186889). |
| LongListSelector mit flachen Daten | Aus Leistungsgründen bei sehr langen Listen empfehlen wir LongListSelector anstelle einer WindowsPhone Silverlight-Listenfelds auch für flache, nicht gruppierte Daten. In einer UWP-App werden [GridView](https://msdn.microsoft.com/library/windows/apps/br242705) für lange Elementlisten bevorzugt, unabhängig davon, ob die Daten gruppiert werden können. |
| Panorama | Die WindowsPhone Silverlight Panorama-Steuerelement entspricht der [Richtlinien für Hub-Steuerelemente in Windows-Runtime 8.x-apps](https://msdn.microsoft.com/library/windows/apps/dn449149) und Richtlinien für das Hub-Steuerelement. <br/> Beachten Sie, dass ein Panorama-Steuerelement aus dem letzten Abschnitt in den ersten Abschnitt umbricht und dass das Hintergrundbild im Parallaxmodus relativ zu den Abschnitten verschoben wird. [Hub](https://msdn.microsoft.com/library/windows/apps/dn251843)-Abschnitte brechen nicht um, und es wird kein Parallax-Modus verwendet. |
| Pivot | Die UWP-Äquivalent des WindowsPhone Silverlight Pivot-Steuerelements ist [Windows.UI.Xaml.Controls.Pivot](https://msdn.microsoft.com/library/windows/apps/dn608241). Es ist für alle Gerätefamilien verfügbar. |

**Hinweis:**  der PointerOver-Ansichtszustand ist in benutzerdefinierten Stile/Vorlagen in Windows 10-apps, jedoch nicht im WindowsPhone Silverlight-apps relevant. Es gibt andere Gründe, warum Ihre vorhandenen benutzerdefinierten Stile/Vorlagen unter Umständen nicht für Windows 10-apps, einschließlich Systemressourcenschlüssel, die Sie verwenden, Änderungen an den verwendeten ansichtszustandgruppen und vorgenommene leistungsverbesserungen für die Standardstile Windows 10 geeignet / Vorlagen. Es wird empfohlen, dass Sie eine unbenutzte Kopie der Standardvorlage eines Steuerelements für Windows 10 bearbeiten und Ihre Stil- und vorlagenanpassung darauf neu anzuwenden.

Weitere Informationen zu UWP-Steuerelementen finden Sie unter [Steuerelemente nach Funktion](https://msdn.microsoft.com/library/windows/apps/mt185405), [Liste der Steuerelemente](https://msdn.microsoft.com/library/windows/apps/mt185406) und [Richtlinien für Steuerelemente](https://msdn.microsoft.com/library/windows/apps/dn611856).

##  <a name="design-language-in-windows10"></a>Design-Sprache in Windows 10

Es gibt einige Unterschiede bei der entwurfssprache WindowsPhone Silverlight-apps und Windows 10-apps. Alle Details finden Sie unter [Design](http://dev.windows.com/design). Trotz der Änderungen bei der Entwurfssprache gelten nach wie vor dieselben Designprinzipien: Gestalten Sie Ihre App mit Liebe zum Detail, versuchen Sie aber, alles möglichst einfach zu halten, indem Sie sich auf den Inhalt, nicht auf das Chrom konzentrieren, visuelle Elemente weitgehend reduzieren und für die digitale Welt authentisch bleiben. Nutzen Sie insbesondere bei der Typografie eine visuelle Hierarchie. Entwerfen Sie Ihre App basierend auf einem Raster, und erwecken Sie Ihre Benutzeroberflächen mit flüssigen Animationen zum Leben.

## <a name="localization-and-globalization"></a>Lokalisierung und Globalisierung

Für lokalisierte Zeichenfolgen können Sie die RESX-Datei aus dem WindowsPhone Silverlight-Projekt in Ihrem UWP-app-Projekt erneut verwenden. Kopieren Sie die Datei, fügen Sie sie dem Projekt hinzu, und benennen Sie sie in „Resources.resw“ um, damit sie standardmäßig vom Suchmechanismus gefunden wird. Legen Sie **BBuildvorgangn** auf **PRIResource** und **In Ausgabeverzeichnis kopieren** auf **Nicht kopieren** fest. Anschließend können Sie die Zeichenfolgen im Markup verwenden, indem Sie das **X:Uid**-Attribut für Ihre XAML-Elemente angeben. Siehe [Schnellstart: Verwenden von Zeichenfolgenressourcen](https://msdn.microsoft.com/library/windows/apps/xaml/hh965329).

WindowsPhone Silverlight-apps verwenden die **CultureInfo** -Klasse zum Globalisieren eine app. UWP-Apps verwenden MRT (Modern Resource Technology), wodurch App-Ressourcen (Lokalisierung, Skalierung und Design) sowohl zur Laufzeit als auch in der Visual Studio-Entwurfsoberfläche dynamisch geladen werden können. Weitere Informationen finden Sie unter [Richtlinien für Dateien, Daten und Globalisierung](https://msdn.microsoft.com/library/windows/apps/dn611859).

Im Thema [**ResourceContext.QualifierValues**](https://msdn.microsoft.com/library/windows/apps/br206071) wird beschrieben, wie Sie gerätefamilienspezifische Ressourcen auf der Grundlage des Ressourcenauswahlfaktors für die Gerätefamilie laden.

## <a name="media-and-graphics"></a>Medien und Grafiken

Bedenken Sie bei sämtlichen Informationen zu UWP-Medien und -Grafiken, dass die Windows-Designprinzipien eine radikale Reduktion überflüssiger Elemente nahelegen. Dazu zählen auch grafische Komplexität und unübersichtliche Darstellungen. Das Windows-Design zeichnet sich durch klare und verständliche visuelle Elemente, Typografie und Bewegung aus. Indem Sie diese Prinzipien befolgen, können Sie sicherstellen, dass Ihre App den integrierten Apps ähnelt.

WindowsPhone Silverlight verfügt über einen **RadialGradientBrush** -Typ, der nicht in der UWP vorhanden ist, auch wenn [**andere Pinseltypen**](/uwp/api/Windows.UI.Xaml.Media.Brush) sind. In einigen Fällen können Sie mit einer Bitmap einen ähnlichen Effekt erzielen. Beachten Sie, dass Sie mit Direct2D einen [radialen Farbverlaufspinsel](https://msdn.microsoft.com/library/windows/desktop/dd756679) in einer UWP mit [Microsoft DirectX](https://msdn.microsoft.com/library/windows/desktop/ee663274) , XAML und C++ erstellen können.

WindowsPhone Silverlight verfügt die **System.Windows.UIElement.OpacityMask** -Eigenschaft, aber diese Eigenschaft nicht Mitglied der UWP [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) -Typ ist. In einigen Fällen können Sie mit einer Bitmap einen ähnlichen Effekt erzielen. Und Sie können mit Direct2D eine [Deckkraftmaske](https://msdn.microsoft.com/library/windows/desktop/ee329947) in einer UWP-App mit [Microsoft DirectX](https://msdn.microsoft.com/library/windows/desktop/ee663274), XAML und C++ erstellen. Häufig wird für **OpacityMask** jedoch eine einzelne Bitmap verwendet, die sich an helle und dunkle Designs anpasst. Für Vektorgrafiken können Sie designabhängige Systempinsel verwenden (z.B. die unten dargestellten Kreisdiagramme). Zum Erstellen einer designabhängigen Bitmap (z. B. die unten dargestellten Häkchen) ist allerdings ein anderer Ansatz erforderlich.

![ein designabhängiges Bitmap](images/wpsl-to-uwp-case-studies/wpsl-to-uwp-theme-aware-bitmap.png)

In einer WindowsPhone-Silverlight-app ist das Verfahren zu verwenden, eine Alphamaske (in Form einer Bitmap) als die **OpacityMask** für ein **Rechteck** mit dem Vordergrundpinsel gefülltes gefüllt:

```xml
    <Rectangle Fill="{StaticResource PhoneForegroundBrush}" Width="26" Height="26">
        <Rectangle.OpacityMask>
            <ImageBrush ImageSource="/Assets/wpsl_check.png"/>
        </Rectangle.OpacityMask>
    </Rectangle>
```

Die einfachste Methode, um dies zu einer UWP-App zu portieren, besteht darin, wie hier gezeigt ein [**BitmapIcon**](https://msdn.microsoft.com/library/windows/apps/dn279306) zu verwenden:

```xml
    <BitmapIcon UriSource="Assets/winrt_check.png" Width="21" Height="21"/>
```

„winrt\_check.png“ ist hier eine Alphamaske in Form einer Bitmap wie „wpsl\_check.png“, die sich in derselben Datei befinden könnte. Sie können allerdings verschiedene Größen von „winrt\_check.png“ für unterschiedliche Skalierungsfaktoren bereitstellen. Weitere Informationen hierzu und eine Erläuterung der Änderungen an den Werten **Width** und **Height** finden Sie unter [Anzeigepixel oder effektive Pixel, Abstand zum Bildschirm und Skalierungsfaktoren](#view-or-effective-pixels-viewing-distance-and-scale-factors) in diesem Thema.

Eine allgemeinere Vorgehensweise, die sich eignet, wenn sich das helle und dunkle Design einer Bitmap unterscheiden, ist die Verwendung von zwei Bildressourcen–einer mit einem dunklen Vordergrund (für das helle Design) und einer mit einem hellen Vordergrund (für das dunkle Design). Weitere Informationen zum Benennen dieser Bitmapressourcen finden Sie unter [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und andere](../app-resources/tailor-resources-lang-scale-contrast.md). Sobald ein Satz von Bilddateien korrekt benannt wurde, können Sie wie folgt anhand des Stammnamens abstrakt auf sie verweisen:

```xml
    <Image Source="Assets/winrt_check.png" Stretch="None"/>
```

In WindowsPhone Silverlight kann die Eigenschaft **UIElement.Clip** eine beliebige Form sein, die Sie mit einer **Geometrie** express können und werden in der Regel im XAML-Markup in der Minisprache **StreamGeometry** serialisiert. In der UWP handelt es sich beim Typ der [**Clip**](https://msdn.microsoft.com/library/windows/apps/br208919)-Eigenschaft um [**RectangleGeometry**](https://msdn.microsoft.com/library/windows/apps/br210259), sodass Sie nur einen rechteckigen Bereich zuschneiden können. Das Definieren eines Rechtecks anhand einer Minisprache zuzulassen, wäre zu wenig einschränkend. Um einen Clippingbereich im Markup zu portieren, ersetzen Sie daher die **Clip**-Attributsyntax wie hier gezeigt durch eine Eigenschaftselementsyntax:

```xml
    <UIElement.Clip>
        <RectangleGeometry Rect="10 10 50 50"/>
    </UIElement.Clip>
```

Beachten Sie, dass Sie mit Direct2D [beliebige Geometrie als Maske in einer Ebene](https://msdn.microsoft.com/library/windows/desktop/dd756654) in einer UWP-App mit [Microsoft DirectX](https://msdn.microsoft.com/library/windows/desktop/ee663274), XAML und C++ verwenden können.

## <a name="navigation"></a>Navigation

Wenn Sie zu einer Seite in einer WindowsPhone-Silverlight-app navigieren, verwenden Sie ein Uniform Resource Identifier (URI)-Adressierungsschema:

```csharp
    NavigationService.Navigate(new Uri("/AnotherPage.xaml", UriKind.Relative)/*, navigationState*/);
```

In einer UWP-App rufen Sie die [**Frame.Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694)-Methode auf und geben den Typ der Zielseite (gemäß dem **x:Class**-Attribut der XAML-Markupdefinition der Seite) an:


```csharp
    // In a page:
    this.Frame.Navigate(typeof(AnotherPage)/*, parameter*/);

    // In a view model, perhaps inside an ICommand implementation:
    var rootFrame = Windows.UI.Xaml.Window.Current.Content as Windows.UI.Xaml.Controls.Frame;
    rootFrame.Navigate(typeof(AnotherPage)/*, parameter*/);
```

Sie definieren die Startseite für eine WindowsPhone-Silverlight-app in der Datei "WMAppManifest.xml":

```xml
    <DefaultTask Name="_default" NavigationPage="MainPage.xaml" />
```

In einer UWP-App verwenden Sie imperativen Code zum Definieren der Startseite. Hier sehen Sie Code aus „App.xaml.cs“, der dies veranschaulicht:

```csharp
    if (!rootFrame.Navigate(typeof(MainPage), e.Arguments))
```

URI-Zuordnung und Fragmentnavigation sind URI-Navigationstechniken und gelten daher nicht für UWP-Navigation, die nicht auf URIs basiert. Die URI-Zuordnung wird aufgrund der schwachen Typisierung der Identifizierung einer Zielseite mit einer URI-Zeichenfolge verwendet, die zu Fragilitäts- und Wartbarkeitsproblemen führt, wenn die Seite in einen anderen Ordner und somit an einen anderen relativen Pfad verschoben wird. UWP-Apps verwenden eine stark typisierte, durch einen Compiler überprüfte typbasierte Navigation, bei der das durch die URI-Zuordnung gelöste Problem nicht vorliegt. Fragmentnavigation wird verwendet, um Kontext an die Zielseite zu übergeben, damit ein bestimmtes Fragment des Inhalts der Seite per Bildlauf oder auf andere Weise angezeigt werden kann. Dasselbe Ergebnis erzielen Sie, indem Sie beim Aufrufen der [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694)-Methode einen Navigationsparameter übergeben.

Weitere Informationen finden Sie unter [Navigation](https://msdn.microsoft.com/library/windows/apps/mt187344).

## <a name="resource-key-reference"></a>Ressourcenschlüsselverweis

Die Design-Sprache wird für Windows 10 wurde weiterentwickelt und daher haben sich bestimmte Systemstile geändert, und viele Systemressourcenschlüssel wurden entfernt oder umbenannt. Der XAML-Markup-Editor in Visual Studio hebt Verweise auf Ressourcenschlüssel hervor, die nicht aufgelöst werden können. Der XAML-Markup-Editor unterstreicht z.B. einen Verweis auf den Stilschlüssel `PhoneTextNormalStyle` mit einer roten Wellenlinie. Wird dieser Fehler nicht behoben, wird die App sofort beendet, wenn Sie versuchen, sie im Emulator oder auf dem Gerät bereitzustellen. Daher ist es wichtig, die Richtigkeit des XAML-Markups sicherzustellen. Sie werden feststellen, dass sich solche Fehler mit Visual Studio hervorragend abfangen lassen.

Weitere Informationen finden Sie unten unter [Text](#text).

## <a name="status-bar-system-tray"></a>Statusleiste (Taskleiste)

Die Taskleiste (festgelegt im XAML-Markup mit `shell:SystemTray.IsVisible`) heißt jetzt Statusleiste und wird standardmäßig angezeigt. Sie können die Sichtbarkeit in imperativem Code steuern, indem Sie die Methoden [**Windows.UI.ViewManagement.StatusBar.ShowAsync**](https://msdn.microsoft.com/library/windows/apps/dn610343) und [**HideAsync**](https://msdn.microsoft.com/library/windows/apps/dn610339) aufrufen.

## <a name="text"></a>Text

Der Text (bzw. die Typografie) ist ein wichtiger Aspekt einer UWP-App. Beim Portieren ist es ratsam, das grafische Design Ihrer Ansichten noch einmal darauf zu prüfen, ob es zur neuen Entwurfssprache passt. Verwenden Sie die folgenden Abbildungen, um nach verfügbaren UWP- **TextBlock**-Systemstilen zu suchen. Suchen Sie nach den Stilen, die die WindowsPhone Silverlight-Stilen entsprechen, die Sie verwendet. Alternativ können Sie eigene universelle Stile erstellen und kopieren Sie die Eigenschaften aus den WindowsPhone Silverlight-systemstilen in diese.

![textblock-Systemstile für Windows 10-Apps](images/label-uwp10stylegallery.png)

TextBlock-Systemstile für Windows 10-apps

In einer WindowsPhone-Silverlight-app wird standardmäßig die Schriftfamilie Segoe WP verwendet. In einer Windows 10-app wird standardmäßig die Schriftfamilie Segoe UI verwendet. Daher kann die Schriftartmetrik in Ihrer App Unterschiede aufweisen. Wenn Sie die Darstellung Ihres WindowsPhone Silverlight-Texts reproduzieren möchten, können Sie Ihre eigene Metrik mit Eigenschaften wie [**LineHeight**](https://msdn.microsoft.com/library/windows/apps/br209671) und [**LineStackingStrategy**](https://msdn.microsoft.com/library/windows/apps/br244362)festlegen. Weitere Informationen finden Sie unter [Richtlinien für Schriftarten](https://msdn.microsoft.com/library/windows/apps/hh700394.aspx) und [Entwerfen von UWP-Apps](http://dev.windows.com/design).

## <a name="theme-changes"></a>Designänderungen

Bei einer WindowsPhone Silverlight-app ist das Standarddesign standardmäßig dunkel. Für Windows 10-Geräte hat sich das Standarddesign geändert, aber Sie können steuern, das Design verwendet, indem Sie in "App.xaml" ein angefordertes Design deklarieren. Wenn Sie z.B. auf allen Geräten ein dunkles Design verwenden möchten, fügen Sie dem Stammelement der App `RequestedTheme="Dark"` hinzu.

## <a name="tiles"></a>Kacheln

Kacheln für UWP-apps weisen Verhalten wie Live-Kacheln für WindowsPhone Silverlight-apps, es gibt einige Unterschiede. Code, der die **Microsoft.Phone.Shell.ShellTile.Create**-Methode zum Erstellen von sekundären Kacheln aufruft, sollte beispielsweise zum Aufrufen von [**SecondaryTile.RequestCreateAsync**](https://msdn.microsoft.com/library/windows/apps/br230606) portiert werden. Nachfolgend finden Sie ein vorher-nachher-Beispiel, zunächst die WindowsPhone Silverlight-Version:


```csharp
    var tileData = new IconicTileData()
    {
        Title = this.selectedBookSku.Title,
        WideContent1 = this.selectedBookSku.Title,
        WideContent2 = this.selectedBookSku.Author,
        SmallIconImage = this.SmallIconImageAsUri,
        IconImage = this.IconImageAsUri
    };

    ShellTile.Create(this.selectedBookSku.NavigationUri, tileData, true);
```

Und hier die UWP-Entsprechung:

```csharp
    var tile = new SecondaryTile(
        this.selectedBookSku.Title.Replace(" ", string.Empty),
        this.selectedBookSku.Title,
        this.selectedBookSku.ArgumentString,
        this.IconImageAsUri,
        TileSize.Square150x150);

    await tile.RequestCreateAsync();
```

Code, der eine Kachel mit der **Microsoft.Phone.Shell.ShellTile.Update**-Methode oder der **Microsoft.Phone.Shell.ShellTileSchedule**-Klasse aktualisiert, sollte zur Verwendung der Klassen [**TileUpdateManager**](https://msdn.microsoft.com/library/windows/apps/br208622), [**TileUpdater**](https://msdn.microsoft.com/library/windows/apps/br208628), [**TileNotification**](https://msdn.microsoft.com/library/windows/apps/br208616) und/oder [**ScheduledTileNotification**](https://msdn.microsoft.com/library/windows/apps/hh701637) portiert werden.

Weitere Informationen zu Kacheln, Popups, Signalen, Bannern und Benachrichtigungen finden Sie unter [Erstellen von Kacheln](https://msdn.microsoft.com/library/windows/apps/xaml/hh868260) und [Verwenden von Kacheln, Signalen und Popupbenachrichtigungen](https://msdn.microsoft.com/library/windows/apps/xaml/hh868259). Ausführliche Informationen zu den Größen von visuellen Ressourcen für UWP-Kacheln finden Sie unter [Visuelle Ressourcen für Kacheln und Popups](https://msdn.microsoft.com/library/windows/apps/hh781198).

## <a name="toasts"></a>Popups

Code, der ein Popup mit der **Microsoft.Phone.Shell.ShellToast**-Klasse anzeigt, sollte zur Verwendung der Klassen [**ToastNotificationManager**](https://msdn.microsoft.com/library/windows/apps/br208642), [**ToastNotifier**](https://msdn.microsoft.com/library/windows/apps/br208653), [**ToastNotification**](https://msdn.microsoft.com/library/windows/apps/br208641) und/der [**ScheduledToastNotification**](https://msdn.microsoft.com/library/windows/apps/br208607) portiert werden. Beachten Sie, dass der verbraucherorientierte Begriff für „Popup“ auf mobilen Geräten „Banner“ lautet.

Weitere Informationen finden Sie unter [Verwenden von Kacheln, Signalen und Popupbenachrichtigungen](https://msdn.microsoft.com/library/windows/apps/xaml/hh868259).

## <a name="view-or-effective-pixels-viewing-distance-and-scale-factors"></a>Anzeigepixel oder effektive Pixel, Abstand zum Bildschirm und Skalierungsfaktoren

WindowsPhone Silverlight-apps und Windows 10-apps unterscheiden sich darin, wie sie die Größe und Layout der UI-Elementen gegenüber der tatsächlichen physischen Größe und Auflösung der Geräte abstrahieren. Eine WindowsPhone-Silverlight-app werden hierfür Pixel zu diesem Zweck verwendet. Mit Windows 10 wurde das Konzept der Anzeigepixel, die von effektiven Pixeln verfeinert. Unten wird dieser Begriff erklärt und beschrieben, was er bedeutet und welcher zusätzliche Nutzen damit verbunden ist.

Der Begriff „Auflösung“ bezeichnet ein Maß für die Pixeldichte und nicht wie allgemein angenommen für die Pixelanzahl. Die „effektive Auflösung“ ist die Art und Weise, wie die physischen Pixel, aus denen sich ein Bild oder eine Glyphe zusammensetzt, je nach Abstand zum Bildschirm und physischer Pixelgröße des Geräts für das Auge des Betrachters aufgelöst werden (die Pixeldichte ist der Kehrwert der physischen Pixelgröße). Die effektive Auflösung ist benutzerorientiert und somit eine gute Metrik für die Erstellung einer Benutzeroberfläche. Wenn Sie diese Faktoren verstehen und die Größe von UI-Elementen entsprechend steuern, können Sie eine optimale Benutzerfreundlichkeit erreichen.

Für eine WindowsPhone Silverlight-app alle sind genau 480 Anzeigepixel breit, ohne Ausnahme, unabhängig davon, wie viele physischen Pixel der Bildschirm enthält, noch was der Pixeldichte oder die physische Größe ist. Dies bedeutet, dass ein **Image** -Element mit `Width="48"` werden genau ein Zehntel der Bildschirmbreite jedem Telefon, die die WindowsPhone-Silverlight-app ausgeführt werden können.

Für eine Windows 10-app ist *nicht* der Fall, dass alle Geräte einige sind eine feste Anzahl von effektiven Pixeln breit. Dies ist angesichts der Vielzahl von Geräten, auf denen eine UWP-App ausgeführt werden kann, auch einleuchtend. Unterschiedliche Geräte besitzen eine unterschiedliche effektive Breite (angegeben in der Anzahl von Pixeln) – von 320Epx bei besonders kleinen Geräten bis hin zu 1024Epx bei Monitoren mittlerer Größe (und weit darüber hinaus für eine noch größere Breite). Sie müssen lediglich weiterhin Elemente mit automatischer Größenanpassung und dynamische Layoutbereiche verwenden. Im bestimmten Fällen werden die Eigenschaften der UI-Elemente im XAML-Markup auf eine feste Größe festgelegt. Auf Ihre App wird abhängig davon, auf welchem Gerät sie ausgeführt wird und welche Anzeigeeinstellungen der Benutzer festgelegt hat, automatisch ein Skalierungsfaktor angewendet. Dieser Skalierungsfaktor bewirkt, dass UI-Elemente mit fester Größe trotz unterschiedlicher Bildschirmgröße als Touchziel (und Leseziel) mit mehr oder weniger konstanter Größe angezeigt werden. In Kombination mit dem dynamischen Layout wird Ihre Benutzeroberfläche nicht nur auf verschiedenen Geräten optisch skaliert, auch die Inhaltsmenge wird an den verfügbaren Platz angepasst.

Da 480 früher die feste Breite wurde in der Ansicht Pixel für einen Bildschirm Phone Größe und dieser Wert ist jetzt in effektiven Pixeln in der Regel kleiner, Faustregel alle Dimensionen im Markup Ihrer WindowsPhone Silverlight-app mit dem Faktor 0,8 multiplizieren.

Damit Ihre App auf allen Displays optimal funktioniert, empfiehlt es sich, die einzelnen Bitmap-Ressourcen in verschiedenen Größen zu erstellen, die jeweils für einen bestimmten Skalierungsfaktor geeignet sind. Durch die Bereitstellung von Ressourcen mit einer Skalierung von 100 %, 200 % und 400 % (in dieser Prioritätsreihenfolge) erhalten Sie in den meisten Fällen auch bei allen Skalierungsfaktoren dazwischen hervorragende Ergebnisse.

**Hinweis:** If, für aus irgendeinem Grund, Sie können keine Assets in mehr als einer Größe erstellen und dann Skalierung von 100 % Ressourcen erstellen. In Microsoft Visual Studio bietet die Standardprojektvorlage für UWP-Apps Brandingressourcen (Bilder für Kacheln und Logos) in nur einer Größe, jedoch nicht mit einer Skalierung von 100 %. Befolgen Sie bei der Erstellung von Ressourcen für Ihre eigene App die Informationen in diesem Abschnitt, stellen Sie die Ressourcen mit einer Skalierung von 100%, 200% und 400% bereit, und verwenden Sie Ressourcenpakete.

Falls Sie komplexe Grafiken verwenden, sollten Sie mehr Skalierungen bereitstellen. Wenn Sie mit Vektorgrafiken beginnen, ist es relativ einfach, qualitativ hochwertige Ressourcen für beliebige Skalierungsfaktoren zu generieren.

Es wird nicht empfohlen, dass Sie versuchen, alle Skalierungsfaktoren zu unterstützen, aber die vollständige Liste der Skalierungsfaktoren für Windows 10-apps 100 %, 125 %, 150 %, 200 %, 250 %, 300 % und 400 ist %. Wenn Sie sie bereitstellen, wählt der Store für jedes Gerät die Ressourcen mit der passenden Größe aus, und es werden nur diese Ressourcen heruntergeladen. Die Auswahl der herunterzuladenden Ressourcen erfolgt auf Grundlage des DPI-Werts eines Geräts.

Weitere Informationen finden Sie unter [Reaktionsfähiges Design – Grundlagen für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/dn958435).

## <a name="window-size"></a>Fenstergröße

In Ihrer UWP-App können Sie eine Mindestgröße (Breite und Höhe) mit imperativem Code angeben. Die Standardmindestgröße beträgt 500x320Epx. Dies ist auch die kleinste zulässige Mindestgröße. Die größte zulässige Mindestgröße ist 500 x 500 Epx.

```csharp
   Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().SetPreferredMinSize
        (new Size { Width = 500, Height = 500 });
```

Das nächste Thema ist [Portieren: E/A, Gerät und App-Modell](wpsl-to-uwp-input-and-sensors.md).

## <a name="related-topics"></a>Verwandte Themen

* [Namespace- und Klassenzuordnungen](wpsl-to-uwp-namespace-and-class-mappings.md)
