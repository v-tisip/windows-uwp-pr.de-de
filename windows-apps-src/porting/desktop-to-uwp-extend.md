---
author: normesta
Description: "Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten"
Search.Product: eADQiWindows 10XVcnh
title: "Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten"
ms.author: normesta
ms.date: 07/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: fce6076f07957b50e83cf80e8d12350630b99456
ms.sourcegitcommit: ba0d20f6fad75ce98c25ceead78aab6661250571
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2017
---
# <a name="extend-your-desktop-application-with-modern-uwp-components"></a>Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten

Einige Windows 10-Funktionen (z. B. eine touchfähige UI-Seite) müssen innerhalb eines Modern-App-Containers ausgeführt werden. Wenn Sie diese Funktionen hinzufügen möchten, erweitern Sie Ihre Desktopanwendung um die UWP-Komponente.

In vielen Fällen können Sie die UWP-APIs direkt aus Ihrer Desktopanwendung aufrufen. Bevor Sie dieses Handbuch lesen, lesen Sie [Für Windows10 verbessern](desktop-to-uwp-enhance.md).

>[!NOTE]
>Dieses Handbuch geht davon aus, dass Sie ein Windows-App-Paket mithilfe der Desktop-Brücke für Ihre Desktopanwendung erstellt haben. Falls dies noch nicht geschehen ist, lesen Sie [Desktop-Brücke](desktop-to-uwp-root.md).

Wenn Sie bereit sind, lassen Sie uns starten.

## <a name="show-a-modern-xaml-ui"></a>Anzeigen einer modernen XAML-Benutzeroberfläche

Als Teil Ihres Anwendungsflusses können Sie moderne XAML-basierte Benutzeroberflächen in Ihre Desktopanwendung integrieren. Diese Benutzeroberflächen passen sich natürlich an unterschiedliche Bildschirmgrößen und Auflösungen an und unterstützen moderne, interaktive Modelle, z.B. Touch- und Freihandeingaben.

Mit etwas XAML-Markup-Code können Sie z.B. Benutzern leistungsstarke Kartenvisualisierungsfunktionen bereitstellen.

Diese Abbildungzeigt eine VB6-Anwendung, die eine XAML-basierte, moderne Benutzeroberfläche öffnet, die ein Kartensteuerelement enthält.

![adaptives Design](images\desktop-to-uwp\extend-xaml-ui.png)

### <a name="have-a-closer-look-at-this-app"></a>Sehen Sie sich die App näher an

:heavy_check_mark: [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Add-a-XAML-UI-and-Toast-Notification-to-a-VB6-Application-OsJHC7WhD_8006218965)

:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/vb6-app-with-xaml-sample/9n191ncxf2f6)

:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/VB6withXaml)

### <a name="the-design-pattern"></a>Das Entwurfsmuster

Um eine XAML-basierte Benutzeroberfläche anzuzeigen, gehen Sie folgendermaßen vor:

:one: [Hinzufügen eines UWP-Projekts zur Lösung](#project)

:two: [Eine Protokollerweiterung zum Projekt hinzufügen](#protocol)

:three: [Starten der UWP-App aus Ihrer Desktop-App](#start)

:four: [Im UWP-Projekt gewünschte Seite anzeigen](#parse)

<span id="project" />
### <a name="add-a-uwp-project"></a>Hinzufügen eines UWP-Projekts

Fügen Sie der Projektmappe ein **Leere App (Universal Windows)**-Projekt hinzu.

<span id="protocol" />
### <a name="add-a-protocol-extension"></a>Fügen Sie eine Protokollerweiterung hinzu.

In **Projektmappen-Explorer** öffnen Sie die **package.appxmanifest** Datei des Projekts und fügen die Erweiterung hinzu.

```xml
<Extensions>
      <uap:Extension
          Category="windows.protocol"
          Executable="MapUI.exe"
          EntryPoint=" MapUI.App">
        <uap:Protocol Name="desktopbridgemapsample" />
      </uap:Extension>
    </Extensions>     
```

Benennen Sie dem Protokoll einen Namen, geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Name der Einstiegspunkt-Klasse an.

Sie können auch das **Package.appxmanifest** im Designer öffnen, die **Deklarationen** Registerkarte wählen und dann dort die Erweiterung hinzufügen.

![Deklarationen-Registerkarte](images\desktop-to-uwp\protocol-properties.png)



> [!NOTE]
> Kartensteuerelemente laden Daten aus dem Internet herunter. Wenn Sie eines verwenden, müssen Sie auch die Funktion „Internetclient“ in Ihrem Manifest hinzufügen.

<span id="start" />
### <a name="start-the-uwp-app"></a>Starten Sie UWP-App

Erstellen Sie zunächst eine [Uri](https://msdn.microsoft.com/library/system.uri.aspx) die den Protokollnamen und alle Parameter enthält, die an die UWP-App übergeben werden sollen. Rufen Sie dann die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)-Methode auf.

Hier ist ein einfaches Beispiel in C#.

```csharp

private async void showMap(double lat, double lon)
{
    string str = "desktopbridgemapsample://";

    Uri uri = new Uri(str + "location?lat=" +
        lat.ToString() + "&?lon=" + lon.ToString());

    var success = await Windows.System.Launcher.LaunchUriAsync(uri);

    if (success)
    {
        // URI launched
    }
    else
    {
        // URI launch failed
    }
}
```
In unserem Beispiel gehen wir etwas indirekter vor. Wir haben den Aufruf in eine über VB6-aufrufbare Interop-Funktion mit dem Namen ``LaunchMap`` verpackt. Diese Funktion ist in C++ geschrieben.

Hier ist der VB-Block:

```VB
Private Declare Function LaunchMap Lib "UWPWrappers.dll" _
  (ByVal lat As Double, ByVal lon As Double) As Boolean
 
Private Sub EiffelTower_Click()
    LaunchMap 48.858222, 2.2945
End Sub
```

Dies ist die C++-Funktion:

```C++

DllExport bool __stdcall LaunchMap(double lat, double lon)
{
  try
  {
    String ^str = ref new String(L"desktopbridgemapsample://");
    Uri ^uri = ref new Uri(
      str + L"location?lat=" + lat.ToString() + L"&?lon=" + lon.ToString());
 
    // now launch the UWP component
    Launcher::LaunchUriAsync(uri);
  }
  catch (Exception^ ex) { return false; }
  return true;
}

```

<span id="parse" />
### <a name="parse-parameters-and-show-a-page"></a>Analysieren von Parametern und Anzeigen einer Seite

In der **App** Klasse des UWP-Projekts überschreiben den **OnActivated**-Ereignishandler. Wenn die App durch Ihr Protokoll aktiviert wird, analysieren Sie die Parameter und öffnen Sie die Seite, die Sie benötigen.

```C++
void App::OnActivated(Windows::ApplicationModel::Activation::IActivatedEventArgs^ e)
{
  if (e->Kind == ActivationKind::Protocol)
  {
    ProtocolActivatedEventArgs^ protocolArgs = (ProtocolActivatedEventArgs^)e;
    Uri ^uri = protocolArgs->Uri;
    if (uri->SchemeName == "desktopbridgemapsample")
    {
      Frame ^rootFrame = ref new Frame();
      Window::Current->Content = rootFrame;
      rootFrame->Navigate(TypeName(MainPage::typeid), uri->Query);
      Window::Current->Activate();
    }
  }
}
```

### <a name="similar-samples"></a>Ähnliche Beispiele

[Northwind-Beispiel: End-to-end-Beispiel für UWA-UI- und Win32-Legacy-Code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/NorthwindSample)

[Northwind-Beispiel: UWP-App, die eine Verbindung zu SQL Server herstellt](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SQLServer)

## <a name="provide-services-to-other-apps"></a>Dienste für andere Apps

Sie fügen einen Dienst hinzu, der von anderen Apps genutzt werden kann. Beispielsweise können Sie einen Dienst hinzufügen, der anderen Apps kontrollierten Zugriff auf die Datenbank hinter der App bietet. Durch die Implementierung einer Hintergrundaufgabe können Apps den Dienst erreichen, selbst wenn Ihre Desktop-App nicht ausgeführt wird.

Hier ist ein Beispiel dafür.

![adaptives Design](images\desktop-to-uwp\winforms-app-service.png)

### <a name="have-a-closer-look-at-this-app"></a>Sehen Sie sich die App näher an

:heavy_check_mark: [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Expose-an-AppService-from-a-Windows-Forms-Data-Application-GiqNS7WhD_706218965)

:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/winforms-appservice/9p7d9b6nk5tn)

:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinformsAppService)

### <a name="the-design-pattern"></a>Das Entwurfsmuster

Um einen Dienst bereitzustellen, gehen Sie folgendermaßen vor:

:one: [Komponente für Windows-Runtime hinzufügen](#component)

:two: [Hinzufügen einer App-Diensterweiterung](#extension)

:three: [Implementieren des App-Diensts](#appservice)

:four: [Testen des App-Dienstes](#test)

<span id="component" />

### <a name="add-a-windows-runtime-component"></a>Komponente für Windows-Runtime hinzufügen

Fügen Sie der Projektmappe ein **Komponente für Windows-Runtime (Universal-Windows)**-Projekt hinzu.

Verweisen Sie dann auf das Projekt der Runtime-Komponente Ihres UWP-Packaging-Projektes.

<span id="extension" />
### <a name="add-an-app-service-extension"></a>Hinzufügen einer App-Diensterweiterung

In **Projektmappen-Explorer** öffnen Sie die **package.appxmanifest** Datei des Verpackungs-Projekts und fügen die App-Diensterweiterung hinzu.

```xml
<Extensions>
      <uap:Extension
          Category="windows.appService"
          EntryPoint="MyAppService.AppServiceTask">
        <uap:AppService Name="com.microsoft.samples.winforms" />
      </uap:Extension>
    </Extensions>    
```

Benennen Sie den App-Dienst und geben Sie den Namen der Einstiegspunkt-Klasse an. Dies ist die Klasse, die Sie zum Implementieren Ihres App-Diensts verwenden.

<span id="appservice" />
### <a name="implement-the-app-service"></a>Implementieren des App-Diensts

Hier erfahren Sie, wo Sie Anforderungen von anderen Apps überprüfen und behandeln.

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

<span id="test" />
### <a name="test-the-app-service"></a>Testen des App-Dienstes

Testen Sie Ihren Dienst durch Aufrufen aus einer anderen App.

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
        string result = "";
 
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

![Freigabeziel](images\desktop-to-uwp\share-target.png)

### <a name="have-a-closer-look-at-this-app"></a>Sehen Sie sich die App näher an

:heavy_check_mark: [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Make-a-WPF-Application-a-Share-Target-xd6Fu6WhD_8406218965)

:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/wpf-app-as-sharetarget/9pjcjljlck37)

:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WPFasShareTarget)

### <a name="the-design-pattern"></a>Das Entwurfsmuster

Damit einer Anwendung als Freigabeziel arbeitet, führen Sie folgende Aktionen aus:

:one: [Hinzufügen eines UWP-Projekts zur Lösung](#project2)

:two: [Fügen Sie die Freigabezielerweiterung hinzu](#share-extension)

:three: [Überschreiben des OnNavigatedTo-Ereignisses](#override)

<span id="project2" />
### <a name="add-a-uwp-project-to-your-solution"></a>Hinzufügen eines UWP-Projekts zur Lösung

Fügen Sie der Projektmappe ein **Leere App (Universal Windows)**-Projekt hinzu.

<span id="share-extension" />
### <a name="add-a-share-target-extension"></a>Fügen Sie die Freigabezielerweiterung hinzu

In **Projektmappen-Explorer** öffnen Sie die **package.appxmanifest** Datei des Projekts und fügen die Erweiterung hinzu.

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

<span id="override" />
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

## <a name="support-and-feedback"></a>Support und Feedback

**Antworten auf bestimmte Fragen finden**

Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).

**Geben Sie Feedback zu diesem Artikel**

Verwenden Sie den Kommentarabschnitt weiter unten.
