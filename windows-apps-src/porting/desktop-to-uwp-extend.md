---
Description: Extend your desktop application with Windows UIs and components
Search.Product: eADQiWindows 10XVcnh
title: Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten
ms.date: 06/08/2018
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 76e4b60e1cd25a205d6a304f12a0b04f5db693b5
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8709372"
---
# <a name="extend-your-desktop-application-with-modern-uwp-components"></a>Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten

Einige Windows 10-Funktionen (z. B. eine touchfähige UI-Seite) müssen innerhalb eines Modern-App-Containers ausgeführt werden. Wenn Sie diese Funktionen hinzufügen möchten, erweitern Sie Ihre Desktopanwendung um UWP-Projekte und die Komponente für Windows-Runtime.

In vielen Fällen können Sie Windows-Runtime-APIs direkt aus Ihrer Desktopanwendung aufrufen, also bevor Sie dieses Handbuch lesen, finden Sie unter [für Windows 10 verbessern](desktop-to-uwp-enhance.md).

>[!NOTE]
>Dieses Handbuch wird davon ausgegangen, dass Sie ein Windows-app-Paket für Ihre desktop-Anwendung erstellt haben. Wenn Sie dies noch nicht geschehen, finden Sie unter [Paket-desktopanwendungen](desktop-to-uwp-root.md).

Wenn Sie bereit sind, lassen Sie uns starten.

<a id="setup" />

## <a name="first-setup-your-solution"></a>Ihre Projektmappe einrichten

Fügen Sie Ihrer Projektmappe ein oder mehrere UWP-Projekte und Laufzeitkomponenten hinzu.

Beginnen Sie mit einer Projektmappe, die ein **Paketerstellungsprojekt für Windows-Anwendungen** mit einem Verweis auf Ihre Desktop-Anwendung enthält.

Diese Abbildung zeigt ein Beispiel für eine Projektmappe.

![Erweitern des Startprojekts](images/desktop-to-uwp/extend-start-project.png)

Wenn Ihre Lösung nicht paketprojekt enthält, finden Sie unter [Package Ihre desktop-Anwendung mit Visual Studio](desktop-to-uwp-packaging-dot-net.md).

### <a name="configure-the-desktop-application"></a>Konfigurieren der desktop-Anwendungs

Stellen Sie sicher, dass Ihre desktop-Anwendung Verweise auf die Dateien, die Sie benötigen, Windows-Runtime-APIs aufzurufen.

Zu diesem Zweck finden Sie im Abschnitt [Ihr Projekt einrichten](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-enhance#first-set-up-your-project) des Themas [Erweitern Ihrer Desktopanwendung für Windows 10](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-enhance#first-set-up-your-project).

### <a name="add-a-uwp-project"></a>Hinzufügen eines UWP-Projekts

Fügen Sie der Projektmappe eine **Leere App (Universelle Windows-App)** hinzu.

Hier erstellen Sie eine moderne XAML-Benutzeroberfläche oder verwenden APIs, die nur innerhalb eines UWP-Prozesses ausgeführt werden.

![UWP-Projekt](images/desktop-to-uwp/add-uwp-project-to-solution.png)

Klicken Sie in Ihrem Paketerstellungsprojekt mit der rechten Maustaste auf den Knoten **Anwendungen**, und klicken Sie dann auf **Verweis hinzufügen**.

![Referenzieren des UWP-Projekts](images/desktop-to-uwp/add-uwp-project-reference.png)

Fügen Sie einen Verweis auf das UWP-Projekt hinzu.

![Referenzieren des UWP-Projekts](images/desktop-to-uwp/choose-uwp-project.png)

Ihre Projektmappe sieht etwa wie folgt aus:

![Projektmappe mit UWP-Projekt](images/desktop-to-uwp/uwp-project-reference.png)

### <a name="optional-add-a-windows-runtime-component"></a>(Optional) Komponente für Windows-Runtime hinzufügen

Um einige Szenarien zu erreichen, müssen Sie einer Komponente für Windows-Runtime Code hinzufügen.

![Runtime-Komponente App-Dienst](images/desktop-to-uwp/add-runtime-component.png)

Fügen Sie dann in Ihrem UWP-Projekt einen Verweis auf die Laufzeitkomponente hinzu. Ihre Projektmappe sieht etwa wie folgt aus:

![Verweis auf die Laufzeitkomponente](images/desktop-to-uwp/runtime-component-reference.png)

### <a name="build-your-solution"></a>Erstellen Sie die Projektmappe

Erstellen Sie die Projektmappe, um sicherzustellen, dass keine Fehler angezeigt werden. Wenn Sie Fehlermeldungen, **Konfigurations-Manager** öffnen, und stellen, dass sicher Plattform Ihre Projekte dieselbe.

![Konfigurations-manager](images/desktop-to-uwp/config-manager.png)

Werfen wir einen Blick auf einige Dinge, die Sie mit Ihren UWP-Projekten und Laufzeitkomponenten tun können.

## <a name="show-a-modern-xaml-ui"></a>Anzeigen einer modernen XAML-Benutzeroberfläche

Als Teil Ihres Anwendungsflusses können Sie moderne XAML-basierte Benutzeroberflächen in Ihre Desktopanwendung integrieren. Diese Benutzeroberflächen passen sich natürlich an unterschiedliche Bildschirmgrößen und Auflösungen an und unterstützen moderne, interaktive Modelle, z.B. Touch- und Freihandeingaben.

Mit etwas XAML-Markup-Code können Sie z.B. Benutzern leistungsstarke Kartenvisualisierungsfunktionen bereitstellen.

Diese Abbildungzeigt eine Windows Forms-Anwendung, die eine XAML-basierte, moderne Benutzeroberfläche öffnet, die ein Kartensteuerelement enthält.

![adaptives Design](images/desktop-to-uwp/extend-xaml-ui.png)

>[!NOTE]
>Dieses Beispiel zeigt eine XAML-UI durch ein UWP-Projekt der Projektmappe hinzufügen. Dies ist der stabil unterstützten Ansatz zum Anzeigen von XAML-Benutzeroberflächen in einer desktop-Anwendung. Die Alternative dieses Ansatzes ist mithilfe einer XAML-Insel UWP-XAML-Steuerelemente direkt an Ihre desktop-Anwendung hinzufügen. XAML-Inseln sind als Entwicklervorschau verfügbar. Obwohl wir Sie Sie diese in Ihrem eigenen Code Prototyp ausprobieren können, jetzt dazu ermutigen, empfohlen nicht, dass Sie in Produktionscode zu diesem Zeitpunkt verwendet werden. Diese APIs und Steuerelemente werden weiterhin breiter und Stabilisierung in zukünftigen Windows-Versionen. Weitere Informationen zu XAML-Inseln, finden Sie in [UWP-Steuerelemente in desktop-Apps](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-host-controls)

### <a name="the-design-pattern"></a>Das Entwurfsmuster

Um eine XAML-basierte Benutzeroberfläche anzuzeigen, gehen Sie folgendermaßen vor:

:one: [Einrichten Ihrer Projektmappe](#solution-setup)

:two: [Erstellen einer XAML-Benutzeroberfläche](#xaml-UI)

:three: [Hinzufügen einer Protokollerweiterung zum UWP-Projekt](#protocol)

:four: [Starten der UWP-App aus Ihrer Desktop-App](#start)

:five: [Anzeigen der gewünschten Seite im UWP-Projekt](#parse)

<a id="solution-setup" />

### <a name="setup-your-solution"></a>Einrichten Ihrer Projektmappe

Allgemeine Anleitungen zum Einrichten Ihrer Projektmappe finden Sie im Abschnitt [Ihre Projektmappe einrichten](#setup) am Anfang dieses Handbuchs.

Ihre Projektmappe sieht in etwa wie folgt aus:

![Projektmappe für eine XAML-Benutzeroberfläche](images/desktop-to-uwp/xaml-ui-solution.png)

In diesem Beispiel heißt das Windows Forms-Projekt **Landmarks**, und das UWP-Projekt, das die XAML-Benutzeroberfläche enthält, heißt **MapUI**.

<a id="xaml-UI" />

### <a name="create-a-xaml-ui"></a>Erstellen einer XAML-Benutzeroberfläche

Fügen Sie Ihrem UWP-Projekt eine XAML-Benutzeroberfläche hinzu. Hier sehen Sie den XAML-Code für eine grundlegende Karte.

```xml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}" Margin="12,20,12,14">
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>
    <maps:MapControl x:Name="myMap" Grid.Column="0" Width="500" Height="500"
                     ZoomLevel="{Binding ElementName=zoomSlider,Path=Value, Mode=TwoWay}"
                     Heading="{Binding ElementName=headingSlider,Path=Value, Mode=TwoWay}"
                     DesiredPitch="{Binding ElementName=desiredPitchSlider,Path=Value, Mode=TwoWay}"
                     HorizontalAlignment="Left"
                     MapServiceToken="<Your Key Goes Here" />
    <Grid Grid.Column="1" Margin="12">
        <StackPanel>
            <Slider Minimum="1" Maximum="20" Header="ZoomLevel" Name="zoomSlider" Value="17.5"/>
            <Slider Minimum="0" Maximum="360" Header="Heading" Name="headingSlider" Value="0"/>
            <Slider Minimum="0" Maximum="64" Header=" DesiredPitch" Name="desiredPitchSlider" Value="32"/>
        </StackPanel>
    </Grid>
</Grid>
```

### <a name="add-a-protocol-extension"></a>Hinzufügen einer Protokollerweiterung

Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe und fügen Sie diese Erweiterung hinzu.

```xml
<Extensions>
  <uap:Extension Category="windows.protocol" Executable="MapUI.exe" EntryPoint="MapUI.App">
    <uap:Protocol Name="xamluidemo" />
  </uap:Extension>
</Extensions>
```

Benennen Sie dem Protokoll einen Namen, geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Name der Einstiegspunkt-Klasse an.

Sie können auch das **Package.appxmanifest** im Designer öffnen, die **Deklarationen** Registerkarte wählen und dann dort die Erweiterung hinzufügen.

![Deklarationen-Registerkarte](images/desktop-to-uwp/protocol-properties.png)

> [!NOTE]
> Kartensteuerelemente laden Daten aus dem Internet herunter. Wenn Sie eines verwenden, müssen Sie auch die Funktion „Internetclient“ in Ihrem Manifest hinzufügen.

<a id="start" />

### <a name="start-the-uwp-app"></a>Starten der UWP-App

Erstellen Sie zunächst in Ihrer Desktop-Anwendung eine [Uri](https://msdn.microsoft.com/library/system.uri.aspx), die den Protokollnamen und alle Parameter enthält, die an die UWP-App übergeben werden sollen. Rufen Sie dann die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync)-Methode auf.

```csharp

private void Statue_Of_Liberty_Click(object sender, EventArgs e)
{
    ShowMap(40.689247, -74.044502);
}

private async void ShowMap(double lat, double lon)
{
    string str = "xamluidemo://";

    Uri uri = new Uri(str + "location?lat=" +
        lat.ToString() + "&?lon=" + lon.ToString());

    var success = await Windows.System.Launcher.LaunchUriAsync(uri);

}
```

<a id="parse" />

### <a name="parse-parameters-and-show-a-page"></a>Analysieren von Parametern und Anzeigen einer Seite

In der **App** Klasse des UWP-Projekts überschreiben den **OnActivated**-Ereignishandler. Wenn die App durch Ihr Protokoll aktiviert wird, analysieren Sie die Parameter, und öffnen Sie die gewünschte Seite.

```csharp
protected override void OnActivated(Windows.ApplicationModel.Activation.IActivatedEventArgs e)
{
    if (e.Kind == ActivationKind.Protocol)
    {
        ProtocolActivatedEventArgs protocolArgs = (ProtocolActivatedEventArgs)e;
        Uri uri = protocolArgs.Uri;
        if (uri.Scheme == "xamluidemo")
        {
            Frame rootFrame = new Frame();
            Window.Current.Content = rootFrame;
            rootFrame.Navigate(typeof(MainPage), uri.Query);
            Window.Current.Activate();
        }
    }
}
```

Überschreiben Sie in der Code-behind der XAML-Seite, die ``OnNavigatedTo`` Methode, die die Parameter übergeben wird, auf der Seite. In diesem Fall verwenden wir den Breiten- und Längengrad, die in diese Seite übergeben wurden, um einen Standort in einer Karte anzuzeigen.

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
 {
     if (e.Parameter != null)
     {
         WwwFormUrlDecoder decoder = new WwwFormUrlDecoder(e.Parameter.ToString());

         double lat = Convert.ToDouble(decoder[0].Value);
         double lon = Convert.ToDouble(decoder[1].Value);

         BasicGeoposition pos = new BasicGeoposition();

         pos.Latitude = lat;
         pos.Longitude = lon;

         myMap.Center = new Geopoint(pos);

         myMap.Style = MapStyle.Aerial3D;

     }

     base.OnNavigatedTo(e);
 }
```

## <a name="making-your-desktop-application-a-share-target"></a>Ihre Desktopanwendung als Freigabeziel gestalten

Sie können Ihre Desktopanwendung als Freigabeziel einrichten, damit Benutzer einfach Daten wie Bilder aus anderen Apps freigeben können, die Freigaben unterstützen.

Beispielsweise können Benutzer Ihre Anwendung zum Teilen von Bildern in Microsoft Edge, der Fotos-app auswählen. Hier ist eine WPF-beispielanwendung, die diese Funktion verfügt.

![Freigabeziel](images/desktop-to-uwp/share-target.png).

Im vollständige Beispiel finden Sie [hier](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/ShareTarget)

### <a name="the-design-pattern"></a>Das Entwurfsmuster

Damit einer Anwendung als Freigabeziel arbeitet, führen Sie folgende Aktionen aus:

:one: [Hinzufügen der Freigabezielerweiterung](#share-extension)

: two: [Überschreiben des OnShareTargetActivated-Ereignisses](#override)

: three: [desktop Extensions zum UWP-Projekt hinzufügen](#desktop-extensions)

: four: [Hinzufügen der vollständig vertrauenswürdigen Prozess-Erweiterung](#full-trust)

: five: [Ändern der desktop-Anwendung zum Abrufen der freigegebenen Datei](#modify-desktop)

<a id="share-extension" />

Die folgenden Schritte  

### <a name="add-a-share-target-extension"></a>Hinzufügen der Freigabezielerweiterung

Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe und fügen Sie der Freigabe Ziel-Erweiterung hinzu.

```xml
<Extensions>
      <uap:Extension
          Category="windows.shareTarget"
          Executable="ShareTarget.exe"
          EntryPoint="App">
        <uap:ShareTarget>
          <uap:SupportedFileTypes>
            <uap:SupportsAnyFileType />
          </uap:SupportedFileTypes>
          <uap:DataFormat>Bitmap</uap:DataFormat>
        </uap:ShareTarget>
      </uap:Extension>
</Extensions>  
```

Geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Namen der Einstiegspunkt-Klasse. Dieses Markup wird davon ausgegangen, dass der Name der ausführbaren Datei für Ihre UWP-app ist `ShareTarget.exe`.

Sie müssen außerdem angeben, welche Arten von Dateien mit Ihrer App freigegeben können. In diesem Beispiel Wir stellen der [PhotoStoreDemo WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) -Desktopanwendung als Freigabeziel für Bitmap images, damit wir angeben `Bitmap` für den unterstützten Dateityp.

<a id="override" />

### <a name="override-the-onsharetargetactivated-event-handler"></a>Überschreiben des OnShareTargetActivated-Ereignisses

Überschreiben Sie den **OnShareTargetActivated** -Ereignishandler in der **App** -Klasse des UWP-Projekts.

Dieser Ereignishandler wird aufgerufen, wenn Benutzer Ihre App zum Teilen von Dateien auswählen.

```csharp

protected override void OnShareTargetActivated(ShareTargetActivatedEventArgs args)
{
    shareWithDesktopApplication(args.ShareOperation);
}

private async void shareWithDesktopApplication(ShareOperation shareOperation)
{
    if (shareOperation.Data.Contains(StandardDataFormats.StorageItems))
    {
        var items = await shareOperation.Data.GetStorageItemsAsync();
        StorageFile file = items[0] as StorageFile;
        IRandomAccessStreamWithContentType stream = await file.OpenReadAsync();

        await file.CopyAsync(ApplicationData.Current.LocalFolder);
            shareOperation.ReportCompleted();

        await FullTrustProcessLauncher.LaunchFullTrustProcessForCurrentAppAsync();
    }
}
```

In diesem Code speichern wir das Bild, das vom Benutzer in einem lokalen Speicher-Ordner apps freigegeben ist. Ändern Sie später die desktop-Anwendung Pull-Images aus diesem Ordner. Die desktop-Anwendung kann das tun, da es im gleichen Paket als UWP-app enthalten ist.

<a id="desktop-extensions" />

### <a name="add-desktop-extensions-to-the-uwp-project"></a>Hinzufügen von desktop Extensions zum UWP-Projekt

Fügen Sie die **Windows-Desktop-Erweiterungen für die UWP** -Erweiterung zum UWP-app-Projekt hinzu.

![Desktop-Erweiterung](images/desktop-to-uwp/desktop-extensions.png)

<a id="full-trust" />

### <a name="add-the-full-trust-process-extension"></a>Hinzufügen der Erweiterung für vollständig vertrauenswürdigen Prozess

Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe, und dann fügen Sie die voller Vertrauenswürdigkeit Prozess Erweiterung neben der Freigabe Ziel-Erweiterung, dass Sie diese Datei zuvor hinzufügen hinzu.

```xml
<Extensions>
  ...
      <desktop:Extension Category="windows.fullTrustProcess" Executable="PhotoStoreDemo\PhotoStoreDemo.exe" />
  ...
</Extensions>  
```

Diese Erweiterung ermöglicht die UWP-app, um die desktop-Anwendung zu starten, die Sie die Bereitstellungsfreigabe eine Datei möchten. Im Beispiel verweisen wir an die ausführbare Datei von [WPF-PhotoStoreDemo](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) -desktop-Anwendung.

<a id="modify-desktop" />

### <a name="modify-the-desktop-application-to-get-the-shared-file"></a>Ändern Sie die desktop-Anwendung zum Abrufen der freigegebenen Datei

Ändern Sie Ihre desktop-Anwendung zu suchen und zu verarbeiten die freigegebene Datei. In diesem Beispiel wird gespeichert, die UWP-app die freigegebene Datei in den Ordner des lokalen app-Daten. Daher möchten wir die [PhotoStoreDemo WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) -Desktopanwendung in Pull-Fotos aus diesem Ordner ändern.

```csharp
Photos.Path = Windows.Storage.ApplicationData.Current.LocalFolder.Path;
```

Für Instanzen der desktop-Anwendung, die bereits durch den Benutzer öffnen, können wir auch behandeln Sie das Ereignis [FileSystemWatcher](https://docs.microsoft.com/dotnet/api/system.io.filesystemwatcher?view=netframework-4.7.2) und übergeben Sie den Pfad zum Speicherort Datei. Auf diese Weise werden alle Instanzen von desktop-Anwendung freigegebenen Fotos angezeigt.

```csharp
...

   FileSystemWatcher watcher = new FileSystemWatcher(Photos.Path);

...

private void Watcher_Created(object sender, FileSystemEventArgs e)
{
    // new file got created, adding it to the list
    Dispatcher.BeginInvoke(System.Windows.Threading.DispatcherPriority.Normal, new Action(() =>
    {
        if (File.Exists(e.FullPath))
        {
            ImageFile item = new ImageFile(e.FullPath);
            Photos.Insert(0, item);
            PhotoListBox.SelectedIndex = 0;
            CurrentPhoto.Source = (BitmapSource)item.Image;
        }
    }));
}

```

## <a name="create-a-background-task"></a>Erstellen einer Hintergrundaufgabe

Sie fügen eine Hintergrundaufgaben hinzu, um selbst dann App-Code auszuführen, wenn die App angehalten wurde. Hintergrundaufgaben sind ideal für kleine Aufgaben, die keine Benutzerinteraktion erfordern. Beispielsweise kann Ihre Aufgabe E-Mails herunterladen, eine Popupbenachrichtigung über eine eingehende Chatnachricht zeigen oder auf eine Änderung in einer Systembedingung reagieren.

Hier ist eine WPF-beispielanwendung, die eine Hintergrundaufgabe registriert.

![hintergrundaufgabe](images/desktop-to-uwp/sample-background-task.png)

Die Aufgabe stellt eine HTTP-Anforderung und misst die Zeit, die die Anforderung benötigt, um eine Antwort zurückzugeben. Ihre Aufgaben werden wahrscheinlich viel interessanter sein, aber dieses Beispiel eignet sich gut, um die grundlegende Funktionsweise einer Hintergrundaufgabe zu lernen.

Im vollständige Beispiel finden Sie [hier](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/BGTask).

### <a name="the-design-pattern"></a>Das Entwurfsmuster

Um einen Hintergrunddienst zu erstellen, gehen Sie folgendermaßen vor:

:one: [Implementieren der Hintergrundaufgabe](#implement-task)

:two: [Konfigurieren der Hintergrundaufgabe](#configure-background-task)

:three: [Registrieren der Hintergrundaufgabe](#register-background-task)

<a id="implement-task" />

### <a name="implement-the-background-task"></a>Implementieren der Hintergrundaufgabe

Implementieren Sie die Hintergrundaufgabe, indem Sie einem Komponentenprojekt für Windows-Runtime Code hinzufügen.

```csharp
public sealed class SiteVerifier : IBackgroundTask
{
    public async void Run(IBackgroundTaskInstance taskInstance)
    {

        taskInstance.Canceled += TaskInstance_Canceled;
        BackgroundTaskDeferral deferral = taskInstance.GetDeferral();
        var msg = await MeasureRequestTime();
        ShowToast(msg);
        deferral.Complete();
    }

    private async Task<string> MeasureRequestTime()
    {
        string msg;
        try
        {
            var url = ApplicationData.Current.LocalSettings.Values["UrlToVerify"] as string;
            var http = new HttpClient();
            Stopwatch clock = Stopwatch.StartNew();
            var response = await http.GetAsync(new Uri(url));
            response.EnsureSuccessStatusCode();
            var elapsed = clock.ElapsedMilliseconds;
            clock.Stop();
            msg = $"{url} took {elapsed.ToString()} ms";
        }
        catch (Exception ex)
        {
            msg = ex.Message;
        }
        return msg;
    }
```

<a id="configure-background-task" />

### <a name="configure-the-background-task"></a>Konfigurieren der Hintergrundaufgabe

Öffnen Sie im manifest-Designer die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe.

Fügen Sie auf der Registerkarte **Deklarationen** eine **Hintergrundaufgaben**-Deklaration hinzu.

![Hintergrundaufgaben-Option](images/desktop-to-uwp/background-task-option.png)

Wählen Sie dann die gewünschten Eigenschaften aus. Unser Beispiel verwendet die **Timer**-Eigenschaft.

![Time-Eigenschaft](images/desktop-to-uwp/timer-property.png)

Geben Sie den vollqualifizierten Namen der Klasse in der Komponente für Windows-Runtime, die die Hintergrundaufgabe implementiert.

![Time-Eigenschaft](images/desktop-to-uwp/background-task-entry-point.png)

<a id="register-background-task" />

### <a name="register-the-background-task"></a>Registrieren der Hintergrundaufgabe

Fügen Sie Ihrem Projekt für die Desktop-Anwendung, das die Hintergrundaufgabe registriert, Code hinzu.

```csharp
public void RegisterBackgroundTask(String triggerName)
{
    var current = BackgroundTaskRegistration.AllTasks
        .Where(b => b.Value.Name == triggerName).FirstOrDefault().Value;

    if (current is null)
    {
        BackgroundTaskBuilder builder = new BackgroundTaskBuilder();
        builder.Name = triggerName;
        builder.SetTrigger(new MaintenanceTrigger(15, false));
        builder.TaskEntryPoint = "HttpPing.SiteVerifier";
        builder.Register();
        System.Diagnostics.Debug.WriteLine("BGTask registered:" + triggerName);
    }
    else
    {
        System.Diagnostics.Debug.WriteLine("Task already:" + triggerName);
    }
}
```

## <a name="support-and-feedback"></a>Support und Feedback

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](https://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).
