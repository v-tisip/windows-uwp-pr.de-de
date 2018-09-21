---
author: normesta
Description: Extend your desktop application with Windows UIs and components
Search.Product: eADQiWindows 10XVcnh
title: Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten
ms.author: normesta
ms.date: 06/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f3354dad1702d275fb7b2af53516689d2c5d5014
ms.sourcegitcommit: 5dda01da4702cbc49c799c750efe0e430b699502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4110642"
---
# <a name="extend-your-desktop-application-with-modern-uwp-components"></a>Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten

Einige Windows 10-Funktionen (z. B. eine touchfähige UI-Seite) müssen innerhalb eines Modern-App-Containers ausgeführt werden. Wenn Sie diese Funktionen hinzufügen möchten, erweitern Sie Ihre Desktopanwendung um UWP-Projekte und die Komponente für Windows-Runtime.

In vielen Fällen können Sie die UWP-APIs direkt aus Ihrer Desktopanwendung aufrufen. Bevor Sie dieses Handbuch lesen, lesen Sie [Für Windows10 verbessern](desktop-to-uwp-enhance.md).

>[!NOTE]
>Dieses Handbuch geht davon aus, dass Sie ein Windows-App-Paket mithilfe der Desktop-Brücke für Ihre Desktopanwendung erstellt haben. Falls dies noch nicht geschehen ist, lesen Sie [Desktop-Brücke](desktop-to-uwp-root.md).

Wenn Sie bereit sind, lassen Sie uns starten.

<a id="setup" />

## <a name="first-setup-your-solution"></a>Ihre Projektmappe einrichten

Fügen Sie Ihrer Projektmappe ein oder mehrere UWP-Projekte und Laufzeitkomponenten hinzu.

Beginnen Sie mit einer Projektmappe, die ein **Paketerstellungsprojekt für Windows-Anwendungen** mit einem Verweis auf Ihre Desktop-Anwendung enthält.

Diese Abbildung zeigt ein Beispiel für eine Projektmappe.

![Erweitern des Startprojekts](images/desktop-to-uwp/extend-start-project.png)

Wenn Ihre Projektmappe kein Paketerstellungsprojekt enthält, lesen Sie [Verpacken Ihrer App mit Visual Studio](desktop-to-uwp-packaging-dot-net.md).

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

Werfen wir einen Blick auf einige Dinge, die Sie mit Ihren UWP-Projekten und Laufzeitkomponenten tun können.

## <a name="show-a-modern-xaml-ui"></a>Anzeigen einer modernen XAML-Benutzeroberfläche

Als Teil Ihres Anwendungsflusses können Sie moderne XAML-basierte Benutzeroberflächen in Ihre Desktopanwendung integrieren. Diese Benutzeroberflächen passen sich natürlich an unterschiedliche Bildschirmgrößen und Auflösungen an und unterstützen moderne, interaktive Modelle, z.B. Touch- und Freihandeingaben.

Mit etwas XAML-Markup-Code können Sie z.B. Benutzern leistungsstarke Kartenvisualisierungsfunktionen bereitstellen.

Diese Abbildungzeigt eine Windows Forms-Anwendung, die eine XAML-basierte, moderne Benutzeroberfläche öffnet, die ein Kartensteuerelement enthält.

![adaptives Design](images/desktop-to-uwp/extend-xaml-ui.png)

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

Klicken Sie im **Projektmappen-Explorer**öffnen Sie die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe, und fügen Sie diese Erweiterung.

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

Überschreiben Sie die Methode ``OnNavigatedTo``, um die in die Seite übergebenen Parameter zu verwenden. In diesem Fall verwenden wir den Breiten- und Längengrad, die in diese Seite übergeben wurden, um einen Standort in einer Karte anzuzeigen.

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

### <a name="similar-samples"></a>Ähnliche Beispiele

[Hinzufügen einer UWP-XAML-Benutzererfahrung zu einer VB6-Anwendung](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/VB6withXaml)

[Northwind-Beispiel: End-to-end-Beispiel für UWA-UI- und Win32-Legacy-Code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/NorthwindSample)

[Northwind-Beispiel: UWP-App, die eine Verbindung zu SQL Server herstellt](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SQLServer)

## <a name="provide-services-to-other-apps"></a>Dienste für andere Apps

Sie fügen einen Dienst hinzu, der von anderen Apps genutzt werden kann. Beispielsweise können Sie einen Dienst hinzufügen, der anderen Apps kontrollierten Zugriff auf die Datenbank hinter der App bietet. Durch die Implementierung einer Hintergrundaufgabe können Apps den Dienst erreichen, selbst wenn Ihre Desktop-App nicht ausgeführt wird.

Hier ist ein Beispiel dafür.

![adaptives Design](images/desktop-to-uwp/winforms-app-service.png)

### <a name="have-a-closer-look-at-this-app"></a>Sehen Sie sich die App näher an

:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/winforms-appservice/9p7d9b6nk5tn)

:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinformsAppService)

### <a name="the-design-pattern"></a>Das Entwurfsmuster

Um einen Dienst bereitzustellen, gehen Sie folgendermaßen vor:

:one: [Implementieren des App-Diensts](#appservice)

:two: [Hinzufügen einer App-Diensterweiterung](#extension)

:three: [Testen des App-Dienstes](#test)

<a id="appservice" />

### <a name="implement-the-app-service"></a>Implementieren des App-Diensts

Hier erfahren Sie, wo Sie Anforderungen von anderen Apps überprüfen und behandeln. Fügen Sie diesen Code einer Komponente für Windows-Runtime in Ihrer Projektmappe hinzu.

```csharp
public sealed class AppServiceTask : IBackgroundTask
{
    private BackgroundTaskDeferral backgroundTaskDeferral;
 
    public void Run(IBackgroundTaskInstance taskInstance)
    {
        this.backgroundTaskDeferral = taskInstance.GetDeferral();
        taskInstance.Canceled += OnTaskCanceled;
        var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
        details.AppServiceConnection.RequestReceived += OnRequestReceived;
    }
 
    private async void OnRequestReceived(AppServiceConnection sender,
                                         AppServiceRequestReceivedEventArgs args)
    {
        var messageDeferral = args.GetDeferral();
        ValueSet message = args.Request.Message;
        string id = message["ID"] as string;
        ValueSet returnData = DataBase.GetData(id);
        await args.Request.SendResponseAsync(returnData);
        messageDeferral.Complete();
    }
 
 
    private void OnTaskCanceled(IBackgroundTaskInstance sender,
                                BackgroundTaskCancellationReason reason)
    {
        if (this.backgroundTaskDeferral != null)
        {
            this.backgroundTaskDeferral.Complete();
        }
    }
}
```

<a id="extension" />

### <a name="add-an-app-service-extension-to-the-packaging-project"></a>Hinzufügen einer app-diensterweiterung zum verpackungsprojekt

Öffnen Sie die Datei **"Package.appxmanifest"** des Verpackung-Projekts, und fügen Sie eine app-diensterweiterung zu den ``<Application>`` Element.

```xml
<Extensions>
      <uap:Extension
          Category="windows.appService"
          EntryPoint="AppServiceComponent.AppServiceTask">
        <uap:AppService Name="com.microsoft.samples.winforms" />
      </uap:Extension>
    </Extensions>    
```
Benennen Sie den App-Dienst und geben Sie den Namen der Einstiegspunkt-Klasse an. Dies ist die Klasse, in der Sie den Dienst implementiert haben.

<a id="test" />

### <a name="test-the-app-service"></a>Testen des App-Dienstes

Testen Sie Ihren Dienst durch Aufrufen aus einer anderen App. Dieser Code kann eine Desktop-Anwendung wie z.B. eine Windows Forms-App oder eine andere UWP-App sein.

> [!NOTE]
> Dieser Code funktioniert nur, wenn Sie die ``PackageFamilyName``-Eigenschaft der ``AppServiceConnection``-Klasse richtig festlegen. Sie erhalten diesen Namen, wenn Sie ``Windows.ApplicationModel.Package.Current.Id.FamilyName`` im Kontext des UWP-Projekts aufrufen. Siehe [Erstellen und Verwenden eines App-Dienstes](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).

```csharp
private async void button_Click(object sender, RoutedEventArgs e)
{
    AppServiceConnection dataService = new AppServiceConnection();
    dataService.AppServiceName = "com.microsoft.samples.winforms";
    dataService.PackageFamilyName = "Microsoft.SDKSamples.WinformWithAppService";
 
    var status = await dataService.OpenAsync();
    if (status == AppServiceConnectionStatus.Success)
    {
        string id = int.Parse(textBox.Text);
        var message = new ValueSet();
        message.Add("ID", id);
        AppServiceResponse response = await dataService.SendMessageAsync(message);
 
        if (response.Status == AppServiceResponseStatus.Success)
        {
            if (response.Message["Status"] as string == "OK")
            {
                DisplayResult(response.Message["Result"]);
            }
        }
    }
}
```

Erfahren Sie hier mehr über App-Dienste: [Erstellen und Verwenden eines App-Diensts](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).

### <a name="similar-samples"></a>Ähnliche Beispiele

[Beispiel für App-Dienst-Brücke](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/AppServiceBridgeSample)

[Beispiel für App-Dienst Brücke mit eine C++ Win32-App](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/AppServiceBridgeSample_C%2B%2B)

[MFC-Anwendung, die Pushbenachrichtigungen empfängt.](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/MFCwithPush)


## <a name="making-your-desktop-application-a-share-target"></a>Ihre Desktopanwendung als Freigabeziel gestalten

Sie können Ihre Desktopanwendung als Freigabeziel einrichten, damit Benutzer einfach Daten wie Bilder aus anderen Apps freigeben können, die Freigaben unterstützen.

Beispielsweise können Benutzer Ihre App zum Teilen von Bildern in Microsoft Edge auswählen. Hier ist eine WPF-Beispiel-App, die diese Funktion nutzt.

![Freigabeziel](images/desktop-to-uwp/share-target.png)

### <a name="have-a-closer-look-at-this-app"></a>Sehen Sie sich diese App näher an

:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/wpf-app-as-sharetarget/9pjcjljlck37)

:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WPFasShareTarget)

### <a name="the-design-pattern"></a>Das Entwurfsmuster

Damit einer Anwendung als Freigabeziel arbeitet, führen Sie folgende Aktionen aus:

:one: [Hinzufügen der Freigabezielerweiterung](#share-extension)

:two: [Überschreiben des OnNavigatedTo-Ereignishandlers](#override)

<a id="share-extension" />

### <a name="add-a-share-target-extension"></a>Hinzufügen der Freigabezielerweiterung

Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe und fügen Sie die Erweiterung hinzu.

```xml
<Extensions>
      <uap:Extension
          Category="windows.shareTarget"
          Executable="ShareTarget.exe"
          EntryPoint="ShareTarget.App">
        <uap:ShareTarget>
          <uap:SupportedFileTypes>
            <uap:SupportsAnyFileType />
          </uap:SupportedFileTypes>
          <uap:DataFormat>Bitmap</uap:DataFormat>
        </uap:ShareTarget>
      </uap:Extension>
</Extensions>  
```

Geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Namen der Einstiegspunkt-Klasse. Sie müssen außerdem angeben, welche Arten von Dateien mit Ihrer App freigegeben können.

<a id="override" />

### <a name="override-the-onnavigatedto-event-handler"></a>Überschreiben des OnNavigatedTo-Ereignisses

Überschreiben Sie den **OnNavigatedTo**-Ereignishandler in der **App** Klasse des UWP-Projekts.

Dieser Ereignishandler wird aufgerufen, wenn Benutzer Ihre App zum Teilen von Dateien auswählen.

```csharp
protected override async void OnNavigatedTo(NavigationEventArgs e)
{
  this.shareOperation = (ShareOperation)e.Parameter;
  if (this.shareOperation.Data.Contains(StandardDataFormats.StorageItems))
  {
      this.sharedStorageItems =
        await this.shareOperation.Data.GetStorageItemsAsync();
       
      foreach (StorageFile item in this.sharedStorageItems)
      {
          ProcessSharedFile(item);
      }
  }
}
```

## <a name="create-a-background-task"></a>Erstellen einer Hintergrundaufgabe

Sie fügen eine Hintergrundaufgaben hinzu, um selbst dann App-Code auszuführen, wenn die App angehalten wurde. Hintergrundaufgaben sind ideal für kleine Aufgaben, die keine Benutzerinteraktion erfordern. Beispielsweise kann Ihre Aufgabe E-Mails herunterladen, eine Popupbenachrichtigung über eine eingehende Chatnachricht zeigen oder auf eine Änderung in einer Systembedingung reagieren.

Hier sehen Sie ein Beispiel einer WPF-App, die eine Hintergrundaufgabe registriert.

![hintergrundaufgabe](images/desktop-to-uwp/sample-background-task.png)

Die Aufgabe stellt eine HTTP-Anforderung und misst die Zeit, die die Anforderung benötigt, um eine Antwort zurückzugeben. Ihre Aufgaben werden wahrscheinlich viel interessanter sein, aber dieses Beispiel eignet sich gut, um die grundlegende Funktionsweise einer Hintergrundaufgabe zu lernen.

### <a name="have-a-closer-look-at-this-app"></a>Sehen Sie sich diese App näher an

:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/BGTask)

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

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).
