---
title: Erstellen und Verwenden eines App-Diensts
description: Hier erfahren Sie, wie Sie eine App für die Universelle Windows-Plattform (UWP) erstellen, die Dienste für andere UWP-Apps bereitstellen kann, und wie Sie diese Dienste nutzen.
ms.assetid: 6E48B8B6-D3BF-4AE2-85FB-D463C448C9D3
keywords: App-zu-app-Kommunikation, prozessübergreifende Kommunikation, IPC, Hintergrund Kommunikation, app zu app-app-Dienst
ms.date: 1/16/2019
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 5239bff53bb0e5383bce28b4d781a0ab6a41c3af
ms.sourcegitcommit: cfdc854fede8e586202523cdb59d3d0a2f5b4b36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "9013959"
---
# <a name="create-and-consume-an-app-service"></a>Erstellen und Verwenden eines App-Diensts

App-Dienste sind UWP-Apps, die Dienste für andere UWP-Apps bereitstellen. Sie entsprechen Webdiensten auf einem Gerät. Ein App-Dienst wird als Hintergrundaufgabe in der Host-App ausgeführt und kann seine Dienste auch anderen Apps bereitstellen. Beispielsweise kann der Barcode-Scanner eines App-Dienstes auch anderen Apps nützlich sein. Oder möglicherweise verfügt eine Enterprise-Suite von Apps über einen gemeinschaftlichen App-Dienst für die Rechtschreibprüfung, der auch den anderen Apps in der Suite zur Verfügung steht.  App-Dienste ermöglichen Ihnen, Dienste ohne UI zu erstellen, die von Apps auf demselben Gerät aufgerufen werden können. Ab Windows 10, Version 1607 ist dies auch für Remote-Geräte möglich.

Ab Windows10, Version 1607, können Sie App-Dienste erstellen, die im gleichen Prozess wie die Vordergrund-App ausgeführt werden. In diesem Artikel geht es um das Erstellen und Verwenden von App-Diensten, die in einem separaten Hintergrundprozess ausgeführt werden. Unter [Konvertieren eines App-Diensts für die Ausführung im gleichen Prozess wie seine Host-App](convert-app-service-in-process.md) finden Sie weitere Informationen zum Ausführen eines App-Dienstes, der im gleichen Prozess wie der Anbieter ausgeführt werden.

Den Code für einen App-Dienst finden Sie unter [Beispiel-Apps für die Universelle Windows-Plattform (UWP)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices).

## <a name="create-a-new-app-service-provider-project"></a>Erstellen eines neuen App-Dienstanbieterprojekts

In dieser Anleitung erstellen wir der Einfachheit halber alles in einer Projektmappe.

1. Erstellen Sie in Visual Studio 2015 oder höher ein neues UWP-app-Projekt, und nennen Sie sie **"AppServiceProvider"**.
    1. Wählen Sie die **Datei > neue > Projekt...** 
    2. Wählen Sie im Dialogfeld " **Neues Projekt** " **installiert > Visual C#-> leere App (Universal Windows)**. Dies ist die App, die den App-Dienst für andere UWP-Apps verfügbar macht.
    3. Geben Sie dem Projekt **"AppServiceProvider"**, wählen Sie einen Speicherort für sie, und klicken Sie auf **OK**.

2. Wenn Sie gefragt werden, wählen eine **Ziel-** und **Mindestversion** für das Projekt, wählen Sie mindestens **10.0.14393**. Wenn Sie das neuen Attribut **"supportsmultipleinstances"** verwenden möchten, Sie müssen werden mithilfe von Visual Studio 2017 und Ziel **10.0.15063** (**Windows 10 Creators Update**) oder höher.

<span id="appxmanifest"/>

## <a name="add-an-app-service-extension-to-packageappxmanifest"></a>Hinzufügen einer app-diensterweiterung zu "Package.appxmanifest"

Öffnen Sie im Projekt **"AppServiceProvider"** die Datei **"Package.appxmanifest"** in einem Text-Editor: 

1. Maustaste darauf im **Projektmappen-Explorer**. 
2. Wählen Sie **Öffnen mit**. 
3. Wählen Sie den **XML (Text) Editor**. 

Fügen Sie die folgenden `AppService` Erweiterung innerhalb der `<Application>` Element. Durch dieses Beispiel wird der `com.microsoft.inventory`-Dienst angekündigt, und die App wird als App-Dienstanbieter identifiziert. Der eigentliche Dienst wird als Hintergrundaufgabe implementiert. Das Projekt, das den App-Dienst bereitstellt, macht den Dienst für andere Apps verfügbar. Wir empfehlen, einen umgekehrten Domänennamen für den Dienstnamen zu verwenden.

Beachten Sie, dass der Namespacepräfix `xmlns:uap4` und das Attribut `uap4:SupportsMultipleInstances` nur dann gültig sind, wenn Sie die Windows SDK-Version 10.0.15063 oder höher als Ziel setzen. Sie können diese sicher entfernen, wenn Sie ältere SDK-Versionen als Zielgruppe setzen.

``` xml
<Package
    ...
    xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
    xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4"
    ...
    <Applications>
        <Application Id="AppServiceProvider.App"
          Executable="$targetnametoken$.exe"
          EntryPoint="AppServiceProvider.App">
          ...
          <Extensions>
            <uap:Extension Category="windows.appService" EntryPoint="MyAppService.Inventory">
              <uap3:AppService Name="com.microsoft.inventory" uap4:SupportsMultipleInstances="true"/>
            </uap:Extension>
          </Extensions>
          ...
        </Application>
    </Applications>
```

Das `Category`-Attribut identifiziert die App als App-Dienstanbieter.

Die `EntryPoint` -Attribut identifiziert die Namespace-qualifizierte Klasse, die den Dienst wir als Nächstes implementieren implementiert.

Die `SupportsMultipleInstances` -Attribut gibt an, dass es sich bei jedem Aufruf des app-Diensts, die sie in einem neuen Prozess ausgeführt werden soll. Dies ist nicht erforderlich, jedoch ist Sie verfügbar, wenn Sie diese Funktionalität erfordern und die 10.0.15063 Ziel als SDK (**Windows 10 Creators Update**) oder höher. Der Präfix `uap4` Namespace sollte dabei angegeben werden.

## <a name="create-the-app-service"></a>Erstellen des App-Diensts

1.  Ein App-Dienst kann als Hintergrundaufgabe implementiert werden. Dadurch kann eine Vordergrund-App einen App-Dienst in einer anderen App aufrufen. Um ein app-Dienst als Hintergrundaufgabe zu erstellen, fügen Sie ein neues Komponente für Windows-Runtime-Projekt der Projektmappe (**Datei &gt; hinzufügen &gt; neues Projekt**) mit dem Namen **"myappservice"**. Wählen Sie im Dialogfeld " **Neues Projekt hinzufügen** " **installiert > Visual C#-> Komponente für Windows-Runtime (Universal Windows)**.
2.  Fügen Sie im Projekt **"AppServiceProvider"** einen Projekt-zu-Projekt-Verweis auf das neue **Projekt "myappservice"** hinzu (klicken Sie im **Projektmappen-Explorer**mit der Maustaste auf das **"AppServiceProvider"** Projekt > **Hinzufügen**  >  ** Verweisen auf** > **Projekte** > **Lösung**, wählen Sie **"myappservice"** > **OK**). Dieser Schritt ist unerlässlich, da der App-Dienst ohne das Hinzufügen der Referenz keine Laufzeit damit verbindet.
3.  Fügen Sie die folgenden Anweisungen zur **Verwendung** im Projekt **"myappservice"** am Anfang von **"Class1.cs"**:
    ```cs
    using Windows.ApplicationModel.AppService;
    using Windows.ApplicationModel.Background;
    using Windows.Foundation.Collections;
    ```

4.  Benennen Sie **"Class1.cs"** in **Inventory.cs**, und Ersetzen Sie den Stubcode für **Class1** durch eine neue hintergrundaufgabenklasse **mit dem Namen**:

    ```cs
    public sealed class Inventory : IBackgroundTask
    {
        private BackgroundTaskDeferral backgroundTaskDeferral;
        private AppServiceConnection appServiceconnection;
        private String[] inventoryItems = new string[] { "Robot vacuum", "Chair" };
        private double[] inventoryPrices = new double[] { 129.99, 88.99 };

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            // Get a deferral so that the service isn't terminated.
            this.backgroundTaskDeferral = taskInstance.GetDeferral();

            // Associate a cancellation handler with the background task.
            taskInstance.Canceled += OnTaskCanceled;

            // Retrieve the app service connection and set up a listener for incoming app service requests.
            var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
            appServiceconnection = details.AppServiceConnection;
            appServiceconnection.RequestReceived += OnRequestReceived;
        }

        private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            // This function is called when the app service receives a request.
        }

        private void OnTaskCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
        {
            if (this.backgroundTaskDeferral != null)
            {
                // Complete the service deferral.
                this.backgroundTaskDeferral.Complete();
            }
        }
    }
    ```

    In dieser Klasse wird der App-Dienst ausgeführt.

    **Führen Sie** wird aufgerufen, wenn die Hintergrundaufgabe erstellt wird. Da Hintergrundaufgaben nach Abschluss von **Run** beendet werden, implementiert der Code eine Verzögerung, damit die Hintergrundaufgabe zum Verarbeiten von Anforderungen aktiv bleibt. Ein App-Dienst, der als Hintergrundaufgabe implementiert ist, bleibt für ungefähr 30Sekunden aktiv, nachdem er einen Anruf erhält, es sei denn, er wird innerhalb dieses Zeitraums erneut aufgerufen oder es wird eine Verzögerung entnommen. Wenn der App-Dienst im gleichen Prozess wie der Aufrufer implementiert ist, ist die Lebensdauer des App-Diensts an die Lebensdauer des Aufrufers gebunden.

    Die Lebensdauer des App-Diensts hängt vom Aufrufer ab:

    * Wenn der Aufrufer im Vordergrund ausgeführt wird, ist die app-Dienst-Lebensdauer des Aufrufers.
    * Wenn der Aufrufer im Hintergrund ist, erhält der app-Dienst nach 30 Sekunden ausgeführt. Das Entfernen einer Verzögerung stellt ein Mal zusätzlich 5Sekunden bereit.

    **OnTaskCanceled** wird aufgerufen, wenn die Aufgabe abgebrochen wird. Die Aufgabe wird abgebrochen, wenn die Client-app gibt den [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/dn921704)frei, die Client-app angehalten wird, das Betriebssystem heruntergefahren oder in den Ruhemodus geht oder das Betriebssystem nicht Ressourcen zum Ausführen der Aufgabe genügend.

## <a name="write-the-code-for-the-app-service"></a>Schreiben des Codes für den App-Dienst

**OnRequestReceived** wird in der Code für den app-Dienst. Ersetzen Sie den Stub **OnRequestReceived** im **Projekt "myappservice"** **Inventory.cs** , mit dem Code aus diesem Beispiel. Dieser Code ruft einen Index für ein Bestandselement ab und übergibt ihn zusammen mit einer Befehlszeichenfolge an den Dienst, um den Namen und Preis des angegebenen Bestandselements abzurufen. Fügen Sie Ihren eigenen Projekten einen Code zur Fehlerbehandlung hinzu.

```cs
private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
{
    // Get a deferral because we use an awaitable API below to respond to the message
    // and we don't want this call to get canceled while we are waiting.
    var messageDeferral = args.GetDeferral();

    ValueSet message = args.Request.Message;
    ValueSet returnData = new ValueSet();

    string command = message["Command"] as string;
    int? inventoryIndex = message["ID"] as int?;

    if (inventoryIndex.HasValue &&
        inventoryIndex.Value >= 0 &&
        inventoryIndex.Value < inventoryItems.GetLength(0))
    {
        switch (command)
        {
            case "Price":
            {
                returnData.Add("Result", inventoryPrices[inventoryIndex.Value]);
                returnData.Add("Status", "OK");
                break;
            }

            case "Item":
            {
                returnData.Add("Result", inventoryItems[inventoryIndex.Value]);
                returnData.Add("Status", "OK");
                break;
            }

            default:
            {
                returnData.Add("Status", "Fail: unknown command");
                break;
            }
        }
    }
    else
    {
        returnData.Add("Status", "Fail: Index out of range");
    }

    try
    {
        // Return the data to the caller.
        await args.Request.SendResponseAsync(returnData);
    }
    catch (Exception e)
    {
        // Your exception handling code here.
    }
    finally
    {
        // Complete the deferral so that the platform knows that we're done responding to the app service call.
        // Note for error handling: this must be called even if SendResponseAsync() throws an exception.
        messageDeferral.Complete();
    }
}
```

Beachten Sie, dass **OnRequestReceived** **Async** ist, da wir eine awaitable [SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) in diesem Beispiel Methodenaufruf.

Damit der Dienst **asynchronen** Methoden im **OnRequestReceived** -Handler verwenden kann, wird eine Verzögerung entnommen. Dadurch wird sichergestellt, dass der Aufruf von **OnRequestReceived** erst abgeschlossen wird, wenn die Nachricht verarbeitet wurde.  [SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) sendet das Ergebnis an den Aufrufer. **SendResponseAsync** signalisiert nicht den Abschluss des Aufrufs. [SendMessageAsync](https://msdn.microsoft.com/library/windows/apps/dn921712) wird durch den Abschluss der Verzögerung signalisiert, dass **OnRequestReceived** abgeschlossen wurde. Der Aufruf von **SendResponseAsync** ist in einem Versuch/final-Block eingeschlossen, da die Verzögerung abgeschlossen werden muss, auch wenn **SendResponseAsync** eine Ausnahme auslöst.

App-Dienste verwenden [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) Objekte zum Austauschen von Informationen. Die Größe der Daten, die übergeben werden können, ist nur durch die Systemressourcen begrenzt. Es gibt keine vordefinierten Schlüssel zur Verwendung in Ihrem **ValueSet**. Sie müssen bestimmen, welche Schlüsselwerte Sie zum Definieren des Protokolls für Ihren App-Dienst verwenden. Dieses Protokoll muss beim Schreiben des Aufrufers berücksichtigt werden. In diesem Beispiel haben wir einen Schlüssel namens `Command` ausgewählt, dessen Wert angibt, ob der App-Dienst den Namen des Bestandselements oder seinen Preis bereitstellen soll. Der Index des Bestandsnamens wird unter dem Schlüssel `ID` gespeichert. Der Rückgabewert wird unter dem Schlüssel `Result` gespeichert.

An den Aufrufer wird eine [AppServiceClosedStatus](https://msdn.microsoft.com/library/windows/apps/dn921703)-Enumeration zurückgegeben, um anzugeben, ob der Aufruf des App-Diensts erfolgreich war. Beim Aufruf des App-Diensts könnte z.B. ein Fehler auftreten, wenn das Betriebssystem den Dienstendpunkt abbricht, da keine Ressourcen mehr verfügbar sind. Sie können über [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) zusätzliche Fehlerinformationen zurückgeben. In diesem Beispiel verwenden wir einen Schlüssel mit dem Namen `Status`, um detailliertere Fehlerinformationen an den Aufrufer zurückzugeben.

Der Aufruf von [SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) gibt [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) an den Aufrufer zurück.

## <a name="deploy-the-service-app-and-get-the-package-family-name"></a>Bereitstellen der Dienstanbieter-App und Abrufen des Paketfamiliennamens

Die app-Dienstanbieter muss bereitgestellt werden, bevor Sie sie von einem Client aus aufrufen können. Sie können durch die Auswahl **Erstellen > bereitstellen Lösung** in Visual Studio bereitstellen.

Sie benötigen auch den paketfamiliennamen des app-Dienstanbieters, um sie aufrufen. Sie erhalten sie durch Öffnen des Projekts **"AppServiceProvider"** **Datei "Package.appxmanifest** " in der Entwurfsansicht (Doppelklicken Sie im **Projektmappen-Explorer**). Wählen Sie die Registerkarte " **Verpacken** ", kopieren Sie den Wert neben **-paketfamiliennamen ein,** und fügen Sie sie an einer beliebigen Stelle wie beispielsweise Editor für den Moment.

## <a name="write-a-client-to-call-the-app-service"></a>Schreiben eines Clients zum Aufrufen des App-Diensts

1.  Fügen Sie der Projektmappe ein neues leeres Projekt für eine Universelle Windows-App mit dem Namen **Datei &gt; Hinzufügen &gt; Neues Projekt** hinzu. Klicken Sie im Dialogfeld " **Neues Projekt hinzufügen** " Wählen Sie **installiert > Visual C#-> leere App (Universal Windows)** , und nennen Sie sie **"ClientApp"**.

2.  Fügen Sie im Projekt **"ClientApp"** am Anfang der **Datei "MainPage.Xaml.cs"** die folgende Anweisung **verwenden** hinzu:
    ```cs
    using Windows.ApplicationModel.AppService;
    ```

3.  Fügen Sie ein Textfeld **TextBox** und eine Schaltfläche, um **"MainPage.xaml"** genannt.

4.  Fügen Sie eine Schaltfläche click-Ereignishandler für die Schaltfläche **Button_Click**aufgerufen und Signatur des schaltflächenhandlers das Schlüsselwort **Async** hinzugefügt.

5. Ersetzen Sie den Stub des Klickhandlers für die Schaltfläche durch den folgenden Code. Vergessen Sie nicht die `inventoryService`-Felddeklaration.
    ```cs
   private AppServiceConnection inventoryService;

   private async void button_Click(object sender, RoutedEventArgs e)
   {
       // Add the connection.
       if (this.inventoryService == null)
       {
           this.inventoryService = new AppServiceConnection();

           // Here, we use the app service name defined in the app service 
           // provider's Package.appxmanifest file in the <Extension> section.
           this.inventoryService.AppServiceName = "com.microsoft.inventory";

           // Use Windows.ApplicationModel.Package.Current.Id.FamilyName 
           // within the app service provider to get this value.
           this.inventoryService.PackageFamilyName = "Replace with the package family name";

           var status = await this.inventoryService.OpenAsync();

           if (status != AppServiceConnectionStatus.Success)
           {
               textBox.Text= "Failed to connect";
               this.inventoryService = null;
               return;
           }
       }

       // Call the service.
       int idx = int.Parse(textBox.Text);
       var message = new ValueSet();
       message.Add("Command", "Item");
       message.Add("ID", idx);
       AppServiceResponse response = await this.inventoryService.SendMessageAsync(message);
       string result = "";

       if (response.Status == AppServiceResponseStatus.Success)
       {
           // Get the data  that the service sent to us.
           if (response.Message["Status"] as string == "OK")
           {
               result = response.Message["Result"] as string;
           }
       }

       message.Clear();
       message.Add("Command", "Price");
       message.Add("ID", idx);
       response = await this.inventoryService.SendMessageAsync(message);

       if (response.Status == AppServiceResponseStatus.Success)
       {
           // Get the data that the service sent to us.
           if (response.Message["Status"] as string == "OK")
           {
               result += " : Price = " + response.Message["Result"] as string;
           }
       }

       textBox.Text = result;
   }
   ```
    
    Ersetzen Sie den Paketfamiliennamen in der Zeile `this.inventoryService.PackageFamilyName = "Replace with the package family name";` durch den Paketfamiliennamen des **AppServiceProvider**-Projekts, das Sie in [Bereitstellen der Dienstanbieter-App und Abrufen des Paketfamiliennamens](#deploy-the-service-app-and-get-the-package-family-name) erhalten haben.

    > [!NOTE]
    > Achten Sie darauf, dass Sie in das String-Literal, anstatt sie in einer Variablen einfügen. Es wird nicht funktionieren, wenn Sie eine Variable verwenden.

    Der Code richtet zunächst eine Verbindung mit dem App-Dienst ein. Die Verbindung bleibt offen, bis Sie `this.inventoryService` verwerfen. Name des app-Dienst muss übereinstimmen die `AppService` des Elements `Name` -Attribut, das Sie die **Datei "Package.appxmanifest** " des Projekts **"AppServiceProvider"** hinzugefügt. In diesem Beispiel ist dies `<uap3:AppService Name="com.microsoft.inventory"/>`.

    Ein [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) mit dem Namen `message` wird erstellt, um den Befehl angeben, die wir an der app-Dienst senden möchten. Der Beispiel-App-Dienst erwartet einen Befehl, der angibt, welche der beiden Aktionen ausgeführt werden soll. Wir erhalten den Index aus dem Textfeld in der Client-app, und rufen Sie dann den Dienst mit den `Item` Befehl aus, um die Beschreibung des Elements zu erhalten. Anschließend wird der Aufruf mit dem Befehl `Price` ausgeführt, um den Preis des Artikels zu erhalten. Der Text der Schaltfläche wird auf das Ergebnis festgelegt.

    Da [AppServiceResponseStatus](https://msdn.microsoft.com/library/windows/apps/dn921724) nur angibt, ob das Betriebssystem den Aufruf mit dem App-Dienst verknüpfen konnte, muss der Schlüssel `Status` im [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) geprüft werden, den wir vom App-Dienst erhalten, um sicherzustellen, dass die Anforderung erfüllt werden konnte.

6. Das Projekt **"ClientApp"** als Startprojekt festlegen (mit der rechten Maustaste im **Projektmappen-Explorer**- > **als Startprojekt festlegen**), und führen Sie die Lösung. Geben Sie 1 in das Textfeld ein, und klicken Sie auf die Schaltfläche. Der Dienst sollte „Stuhl: Preis = 88,99“ zurückgeben.

    ![Beispiel-App, die Stuhlpreis = 88,99 anzeigt](images/appserviceclientapp.png)

Wenn der Aufruf des app-Diensts ein Fehler auftritt, überprüfen Sie in das Projekt **"ClientApp"** Folgendes:

1.  Stellen Sie sicher, dass der paketfamilienname, der der bestandsdienstverbindung zugewiesen den paketfamiliennamen der app **"AppServiceProvider"** übereinstimmt. Finden Sie unter der Zeile in **Button\_Click** mit `this.inventoryService.PackageFamilyName = "...";`.
2.  In **Button\_Click**stellen Sie sicher, dass der Name der app-Dienst, der der bestandsdienstverbindung zugewiesen ist den Namen des app-Diensts in der **"AppServiceProvider"** **Datei "Package.appxmanifest** " entspricht. Weitere Informationen finden Sie unter `this.inventoryService.AppServiceName = "com.microsoft.inventory";`.
3.  Stellen Sie sicher, dass die app **"AppServiceProvider"** bereitgestellt wurde. (Im **Projektmappen-Explorer**mit der rechten Maustaste der Projektmappe, und wählen Sie die **Projektmappe bereitstellen**).

## <a name="debug-the-app-service"></a>Debuggen des App-Diensts

1.  Stellen Sie vor dem Debuggen sicher, dass die Projektmappe bereitgestellt wurde. Die App Dienstanbieter-App muss bereitgestellt werden, bevor der Dienst aufgerufen werden kann. (Klicken Sie in Visual Studio auf **Erstellen &gt; Projektmappe bereitstellen**.)
2.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste in des Projekts **"AppServiceProvider"** , und wählen Sie **Eigenschaften**. Ändern Sie auf der Registerkarte **Debuggen** die **Startaktion** in **Eigenen Code zunächst nicht starten, sondern debuggen**. (Hinweis: wenn Sie nicht C++ zum Implementieren Ihres App-Dienstanbieters verwenden, müssen Sie auf der Registerkarte **Debuggen** die Option **Anwendung starten** auf **Nein** ändern).
3.  Legen Sie im Projekt **"myappservice"** in der Datei **Inventory.cs** einen Haltepunkt im **OnRequestReceived**.
4.  Legen Sie das Projekt **"AppServiceProvider"** Startprojekt aus, und drücken **F5**.
5.  Starten Sie **"ClientApp"** über das Startmenü (nicht über Visual Studio).
6.  Geben Sie 1 in das Textfeld ein, und klicken Sie auf die Schaltfläche. Der Debugger stoppt im App-Dienstaufruf am Haltepunkt in Ihrem App-Dienst.

## <a name="debug-the-client"></a>Debuggen des Clients

1.  Folgen Sie zum Debuggen des Clients, der den App-Dienst aufruft, den Anweisungen im vorherigen Schritt.
2.  Starten Sie **"ClientApp"** über das Startmenü.
3.  Fügen Sie den Debugger an den Prozess **ClientApp.exe** (nicht der Prozess " **ApplicationFrameHost.exe** "). (Klicken Sie in Visual Studio auf **Debuggen &gt; An den Prozess anhängen**.)
4.  Legen Sie im Projekt **"ClientApp"** einen Haltepunkt in **Button\_Click**.
5.  Die Haltepunkte in der Client und der app-Dienst werden jetzt erreicht werden, wenn Sie geben Sie 1 in das Textfeld von **"ClientApp"** , und klicken Sie auf die Schaltfläche.

## <a name="general-app-service-troubleshooting"></a>Allgemeine Problembehandlung von App-Diensten

Wenn nach einem app-Dienst herstellen einer Verbindung mit den Status **AppUnavailable** auftritt, überprüfen Sie Folgendes:

- Stellen Sie sicher, dass das App-Dienstanbieterprojekt und das App-Dienstprojekt bereitgestellt sind. Beide müssen bereitgestellt werden, bevor der Client ausgeführt werden kann, da andernfalls der Client keine Verbindung zulassen kann. Sie können von Visual Studio aus mithilfe von **Erstellen** > **Projektmappe bereitstellen** bereitstellen.
- Klicken Sie im **Projektmappen-Explorer**sicher, dass Ihr app-dienstanbieterprojekt einen Projekt-zu-Projekt-Verweis auf das Projekt hat, das den app-Dienst implementiert.
- Überprüfen Sie, ob die `<Extensions>` Eintrag, und die untergeordneten Elemente der Datei **"Package.appxmanifest"** in der app-dienstanbieterprojekts wie oben [Hinzufügen einer app-diensterweiterung zu "Package.appxmanifest"](#appxmanifest)angegeben hinzugefügt wurde.
- Stellen Sie sicher, dass die [AppServiceConnection.AppServiceName](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appservice.appserviceconnection.appservicename) -Zeichenfolge in Ihrem Client, der die app-Dienstanbieter aufruft entspricht der `<uap3:AppService Name="..." />` in der app-dienstanbieterprojekt der **Datei "Package.appxmanifest** " angegeben.
- Stellen Sie sicher, dass die [AppServiceConnection.PackageFamilyName](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appservice.appserviceconnection.packagefamilyname) der paketfamilienname, der die app-dienstanbieterkomponente wie oben angegeben [Hinzufügen eine app-diensterweiterung zu "Package.appxmanifest"](#appxmanifest) entspricht
- Für Out-of-Proc app-Diensten wie in diesem Beispiel wird, überprüfen Sie, dass die `EntryPoint` Angabe in der `<uap:Extension ...>` Element der Ihr app-dienstanbieterprojekt der **Datei "Package.appxmanifest** " entspricht den Namespace und Klassennamen der öffentliche Klasse, die implementiert [IBackgroundTask](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.ibackgroundtask) in Ihrem app-Dienst-Projekt.

### <a name="troubleshoot-debugging"></a>Problembehandlung beim Debuggen

Wenn der Debugger nicht an Haltepunkten in Ihrem App-Dienstanbieter oder App-Dienst-Projekte beendet wird, überprüfen Sie Folgendes:

- Stellen Sie sicher, dass das App-Dienstanbieterprojekt und das App-Dienstprojekt bereitgestellt sind. Beide müssen bereitgestellt werden, bevor der Client ausgeführt wird. Sie können diese von Visual Studio aus mithilfe von **Erstellen** > **Projektmappe bereitstellen** bereitstellen.
- Stellen Sie sicher, dass das Projekt, das Sie debuggen möchten als Startprojekt festgelegt ist und dass die debugging-Eigenschaften für das Projekt festgelegt sind, um das Projekt nicht ausgeführt, wenn **F5** gedrückt wird. Klicken Sie mit der rechten Maustaste auf **Eigenschaften** und dann **Debug** (oder **Debugging** in C++). In C#, ändern Sie die **Startaktion** in **Eigenen Code zunächst nicht starten, sondern debuggen**. Legen Sie in C++ **Anwendung starten** auf **Nein** fest.

## <a name="remarks"></a>Anmerkungen

Dieses Beispiel ist eine Einführung in das Erstellen eines App-Diensts, das als Hintergrundaufgabe ausgeführt wird, und Aufrufen des Diensts in einer anderen App. Die wichtigsten Punkte zu beachten sind:

* Erstellen Sie eine Hintergrundaufgabe zum Hosten des app-Diensts.
* Hinzufügen der `windows.appService` Erweiterung für die **Datei "Package.appxmanifest** " des app-Dienstanbieters.
* Erhalten Sie den paketfamiliennamen des app-Dienstanbieters, damit wir von der Client-app herstellen können.
* Fügen Sie einen Projekt-zu-Projekt-Verweis von der app-dienstanbieterprojekt auf das app-Dienst-Projekt hinzu.
* Verwenden Sie [Windows.ApplicationModel.AppService.AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/dn921704) zum Aufrufen des Diensts.

## <a name="full-code-for-myappservice"></a>Vollständiger Code für „MyAppService”

```cs
using System;
using Windows.ApplicationModel.AppService;
using Windows.ApplicationModel.Background;
using Windows.Foundation.Collections;

namespace MyAppService
{
    public sealed class Inventory : IBackgroundTask
    {
        private BackgroundTaskDeferral backgroundTaskDeferral;
        private AppServiceConnection appServiceconnection;
        private String[] inventoryItems = new string[] { "Robot vacuum", "Chair" };
        private double[] inventoryPrices = new double[] { 129.99, 88.99 };

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            // Get a deferral so that the service isn't terminated.
            this.backgroundTaskDeferral = taskInstance.GetDeferral();

            // Associate a cancellation handler with the background task.
            taskInstance.Canceled += OnTaskCanceled;

            // Retrieve the app service connection and set up a listener for incoming app service requests.
            var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
            appServiceconnection = details.AppServiceConnection;
            appServiceconnection.RequestReceived += OnRequestReceived;
        }

        private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            // Get a deferral because we use an awaitable API below to respond to the message
            // and we don't want this call to get canceled while we are waiting.
            var messageDeferral = args.GetDeferral();

            ValueSet message = args.Request.Message;
            ValueSet returnData = new ValueSet();

            string command = message["Command"] as string;
            int? inventoryIndex = message["ID"] as int?;

            if (inventoryIndex.HasValue &&
                 inventoryIndex.Value >= 0 &&
                 inventoryIndex.Value < inventoryItems.GetLength(0))
            {
                switch (command)
                {
                    case "Price":
                        {
                            returnData.Add("Result", inventoryPrices[inventoryIndex.Value]);
                            returnData.Add("Status", "OK");
                            break;
                        }

                    case "Item":
                        {
                            returnData.Add("Result", inventoryItems[inventoryIndex.Value]);
                            returnData.Add("Status", "OK");
                            break;
                        }

                    default:
                        {
                            returnData.Add("Status", "Fail: unknown command");
                            break;
                        }
                }
            }
            else
            {
                returnData.Add("Status", "Fail: Index out of range");
            }

            // Return the data to the caller.
            await args.Request.SendResponseAsync(returnData);

            // Complete the deferral so that the platform knows that we're done responding to the app service call.
            // Note for error handling: this must be called even if SendResponseAsync() throws an exception.
            messageDeferral.Complete();
        }


        private void OnTaskCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
        {
            if (this.backgroundTaskDeferral != null)
            {
                // Complete the service deferral.
                this.backgroundTaskDeferral.Complete();
            }
        }
    }
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Umwandeln eines App-Diensts für die Ausführung im gleichen Prozess wie die Host-App](convert-app-service-in-process.md)
* [Unterstützen Ihrer App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md)
* [Codebeispiel für App-Dienst (C#, C++ und VB)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices)
