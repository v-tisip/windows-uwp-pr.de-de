---
author: TylerMSFT
title: Erstellen und Verwenden eines App-Diensts
description: Hier erfahren Sie, wie Sie eine App für die Universelle Windows-Plattform (UWP) erstellen, die Dienste für andere UWP-Apps bereitstellen kann, und wie Sie diese Dienste nutzen.
ms.assetid: 6E48B8B6-D3BF-4AE2-85FB-D463C448C9D3
keywords: App-zu-app-Kommunikation, prozessübergreifende Kommunikation, IPC-Nachrichten, Hintergrund Kommunikation, app zu app-app-Dienst
ms.author: twhitney
ms.date: 09/18/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 7475ae8db964b23de89488d883c135158ea20e74
ms.sourcegitcommit: a160b91a554f8352de963d9fa37f7df89f8a0e23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4122137"
---
# <a name="create-and-consume-an-app-service"></a>Erstellen und Verwenden eines App-Diensts

App-Dienste sind UWP-Apps, die Dienste für andere UWP-Apps bereitstellen. Sie entsprechen Webdiensten auf einem Gerät. Ein App-Dienst wird als Hintergrundaufgabe in der Host-App ausgeführt und kann seine Dienste auch anderen Apps bereitstellen. Beispielsweise kann der Barcode-Scanner eines App-Dienstes auch anderen Apps nützlich sein. Oder möglicherweise verfügt eine Enterprise-Suite von Apps über einen gemeinschaftlichen App-Dienst für die Rechtschreibprüfung, der auch den anderen Apps in der Suite zur Verfügung steht.  App-Dienste ermöglichen Ihnen, Dienste ohne UI zu erstellen, die von Apps auf demselben Gerät aufgerufen werden können. Ab Windows 10, Version 1607 ist dies auch für Remote-Geräte möglich. 

Ab Windows10, Version 1607, können Sie App-Dienste erstellen, die im gleichen Prozess wie die Vordergrund-App ausgeführt werden. In diesem Artikel geht es um das Erstellen und Verwenden von App-Diensten, die in einem separaten Hintergrundprozess ausgeführt werden. Unter [Konvertieren eines App-Diensts für die Ausführung im gleichen Prozess wie seine Host-App](convert-app-service-in-process.md) finden Sie weitere Informationen zum Ausführen eines App-Dienstes, der im gleichen Prozess wie der Anbieter ausgeführt werden.

Den Code für einen App-Dienst finden Sie unter [Beispiel-Apps für die Universelle Windows-Plattform (UWP)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices).

## <a name="create-a-new-app-service-provider-project"></a>Erstellen eines neuen App-Dienstanbieterprojekts

In dieser Anleitung erstellen wir der Einfachheit halber alles in einer Projektmappe.

-   Erstellen Sie in Microsoft Visual Studio2015 ein neues UWP-App-Projekt mit dem Namen **AppServiceProvider**. (Wählen Sie im Dialogfeld **Neues Projekt** **Vorlagen &gt; Andere Sprachen &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Blank App (Windows Universal)** aus.) Dies ist die App, die den App-Dienst für andere UWP-Apps verfügbar macht.
-   Wenn Sie gefragt werden, wählen Sie eine **Zielversion** für das Projekt auszuwählen, wählen Sie mindestens **10.0.14393** aus. Wenn Sie das neue `SupportsMultipleInstances`-Attribut verwenden möchten, müssen Sie Visual Studio2017 verwenden und als Ziel **10.0.15063** (**Windows 10 Creators Update**) oder höher auswählen.

<span id="appxmanifest"/>

## <a name="add-an-app-service-extension-to-packageappxmanifest"></a>Hinzufügen einer App-Diensterweiterung zu „package.appxmanifest”

Fügen Sie innerhalb der Datei „Package.appxmanifest” des Projekts „AppServiceProvider” die folgende AppService-Erweiterung zum `&lt;Application&gt;`-Element hinzu. Durch dieses Beispiel wird der `com.Microsoft.Inventory`-Dienst angekündigt, und die App wird als App-Dienstanbieter identifiziert. Der eigentliche Dienst wird als Hintergrundaufgabe implementiert. Das Projekt, das den App-Dienst bereitstellt, macht den Dienst für andere Apps verfügbar. Wir empfehlen, einen umgekehrten Domänennamen für den Dienstnamen zu verwenden.

Beachten Sie, dass der Namespacepräfix `xmlns:uap4` und das Attribut `uap4:SupportsMultipleInstances` nur dann gültig sind, wenn Sie die Windows SDK-Version 10.0.15063 oder höher als Ziel setzen. Sie können diese sicher entfernen, wenn Sie ältere SDK-Versionen als Zielgruppe setzen.

``` xml
<Package
    ...
    xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
    xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4"
    ...
    <Applications>
        <Application Id="AppServicesProvider.App"
          Executable="$targetnametoken$.exe"
          EntryPoint="AppServicesProvider.App">
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

Das **Category**-Attribut identifiziert die App als App-Dienstanbieter.

Das **EntryPoint**-Attribut identifiziert die Namespace-qualifizierte Klasse, die den Dienst implementiert. Den Dienst implementieren wir als Nächstes.

Das **SupportsMultipleInstances** -Attribut gibt an, dass bei jedem Aufruf des App-Dienstes ein neuer Prozess ausgeführt werden soll. Dies ist nicht erforderlich, aber verfügbar, wenn Sie diese Funktionalität erfordern und als Ziel `10.0.15063` SDK (**Windows10 Creators Update**) oder höher haben. Der Präfix `uap4` Namespace sollte dabei angegeben werden.

## <a name="create-the-app-service"></a>Erstellen des App-Diensts

1.  Ein App-Dienst kann als Hintergrundaufgabe implementiert werden. Dadurch kann eine Vordergrund-App einen App-Dienst in einer anderen App aufrufen. Fügen Sie der Projektmappe ein neues Projekt vom Typ „Komponente für Windows-Runtime” (**Datei &gt; Hinzufügen &gt; Neues Projekt**) mit dem Namen „MyAppService” hinzu, um einen App-Dienst als Hintergrundaufgabe auszuführen. (Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** **Installiert &gt; Andere Sprachen &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Komponente für Windows-Runtime (Windows Universal)** aus.)
2.  Fügen Sie im Projekt **"AppServiceProvider"** einen Projekt-zu-Projekt-Verweis auf das neue Projekt **"myappservice"** hinzu. (Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt **"AppServiceProvider"** > **Hinzufügen** > **Verweis** > **Projekte** > **Lösung**. Anschließend wählen Sie **"myappservice"** > **OK** aus). Dieser Schritt ist unerlässlich, da der App-Dienst ohne das Hinzufügen der Referenz keine Laufzeit damit verbindet.
3.  Fügen Sie im Projekt „MyAppService” am Anfang von „Class1.cs” die folgenden **using**-Anweisungen hinzu:
    ```cs
    using Windows.ApplicationModel.AppService;
    using Windows.ApplicationModel.Background;
    using Windows.Foundation.Collections;
    ```

4.  Ersetzen Sie den Stubcode für **Class1** durch eine neue Hintergrundaufgabenklasse mit dem Namen **Inventory**:

    ```cs
    public sealed class Inventory : IBackgroundTask
    {
        private BackgroundTaskDeferral backgroundTaskDeferral;
        private AppServiceConnection appServiceconnection;
        private String[] inventoryItems = new string[] { "Robot vacuum", "Chair" };
        private double[] inventoryPrices = new double[] { 129.99, 88.99 };

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            this.backgroundTaskDeferral = taskInstance.GetDeferral(); // Get a deferral so that the service isn't terminated.
            taskInstance.Canceled += OnTaskCanceled; // Associate a cancellation handler with the background task.

            // Retrieve the app service connection and set up a listener for incoming app service requests.
            var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
            appServiceconnection = details.AppServiceConnection;
            appServiceconnection.RequestReceived += OnRequestReceived;
        }

        private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            // This function is called when the app service receives a request
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

    **Run()** wird aufgerufen, wenn die Hintergrundaufgabe erstellt wird. Da Hintergrundaufgaben nach Abschluss von **Run** beendet werden, implementiert der Code eine Verzögerung, damit die Hintergrundaufgabe zum Verarbeiten von Anforderungen aktiv bleibt. Ein App-Dienst, der als Hintergrundaufgabe implementiert ist, bleibt für ungefähr 30Sekunden aktiv, nachdem er einen Anruf erhält, es sei denn, er wird innerhalb dieses Zeitraums erneut aufgerufen oder es wird eine Verzögerung entnommen. Wenn der App-Dienst im gleichen Prozess wie der Aufrufer implementiert ist, ist die Lebensdauer des App-Diensts an die Lebensdauer des Aufrufers gebunden.

    Die Lebensdauer des App-Diensts hängt vom Aufrufer ab:

    1. Wenn der Aufrufer im Vordergrund ausgeführt wird, entspricht die Lebensdauer der App-Dienst der Lebensdauer des Aufrufers.
    2. Wenn der Aufrufer im Hintergrund ausgeführt wird, wird der App-Dienst nach 30Sekunden ausgeführt. Das Entfernen einer Verzögerung stellt ein Mal zusätzlich 5Sekunden bereit.

    **OnTaskCanceled()** wird aufgerufen, wenn die Aufgabe abgebrochen wird. Die Aufgabe wird abgebrochen, wenn die Client-App die [**AppServiceConnection**](https://msdn.microsoft.com/library/windows/apps/dn921704) löscht, die Client-App angehalten wird, das Betriebssystem heruntergefahren oder in den Ruhezustand geschaltet wird oder im Betriebssystem nicht genügend Ressourcen zum Ausführen der Aufgabe verfügbar sind.

## <a name="write-the-code-for-the-app-service"></a>Schreiben des Codes für den App-Dienst

Der Code für den App-Service wird unter **OnRequestReceived()** ausgeführt. Ersetzen Sie den Platzhalter **OnRequestedReceived()** in der Datei „Class1.cs” von „MyAppService” mit dem Code aus dem folgenden Beispiel. Dieser Code ruft einen Index für ein Bestandselement ab und übergibt ihn zusammen mit einer Befehlszeichenfolge an den Dienst, um den Namen und Preis des angegebenen Bestandselements abzurufen. Fügen Sie Ihren eigenen Projekten einen Code zur Fehlerbehandlung hinzu.

```cs
private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
{
    // Get a deferral because we use an awaitable API below to respond to the message
    // and we don't want this call to get cancelled while we are waiting.
    var messageDeferral = args.GetDeferral();

    ValueSet message = args.Request.Message;
    ValueSet returnData = new ValueSet();

    string command = message["Command"] as string;
    int? inventoryIndex = message["ID"] as int?;

    if ( inventoryIndex.HasValue &&
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
        await args.Request.SendResponseAsync(returnData); // Return the data to the caller.
    }
    catch (Exception e)
    {
        // your exception handling code here
    }
    finally
    {
        // Complete the deferral so that the platform knows that we're done responding to the app service call.
        // Note for error handling: this must be called even if SendResponseAsync() throws an exception.
        messageDeferral.Complete();
    }
}
```

**OnRequestReceived()** ist **async**, da wir in diesem Beispiel einen await-fähigen Methodenaufruf von [**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) verwenden.

Es wird eine Verzögerung implementiert, damit der Dienst **async**-Methoden im OnRequestReceived-Handler verwenden kann. Dadurch wird sichergestellt, dass der Aufruf von **OnRequestReceived** erst abgeschlossen wird, wenn die Nachricht verarbeitet wurde.  [**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) sendet das Ergebnis an den Aufrufer. **SendResponseAsync** signalisiert nicht den Abschluss des Aufrufs. [**SendMessageAsync**](https://msdn.microsoft.com/library/windows/apps/dn921712) wird durch den Abschluss der Verzögerung signalisiert, dass **OnRequestReceived** abgeschlossen wurde. **SendMessageAsync()** wird in einem Versuch/Final-Block aufgerufen, da die Verzögerung abgeschlossen werden muss, auch wenn **SendMessageAsync()** eine Ausnahme auslöst.

App-Dienste verwenden zum Austauschen von Informationen ein [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131). Die Größe der Daten, die übergeben werden können, ist nur durch die Systemressourcen begrenzt. Es gibt keine vordefinierten Schlüssel zur Verwendung in Ihrem **ValueSet**. Sie müssen bestimmen, welche Schlüsselwerte Sie zum Definieren des Protokolls für Ihren App-Dienst verwenden. Dieses Protokoll muss beim Schreiben des Aufrufers berücksichtigt werden. In diesem Beispiel haben wir einen Schlüssel namens `Command` ausgewählt, dessen Wert angibt, ob der App-Dienst den Namen des Bestandselements oder seinen Preis bereitstellen soll. Der Index des Bestandsnamens wird unter dem Schlüssel `ID` gespeichert. Der Rückgabewert wird unter dem Schlüssel `Result` gespeichert.

An den Aufrufer wird eine [**AppServiceClosedStatus**](https://msdn.microsoft.com/library/windows/apps/dn921703)-Enumeration zurückgegeben, um anzugeben, ob der Aufruf des App-Diensts erfolgreich war. Beim Aufruf des App-Diensts könnte z.B. ein Fehler auftreten, wenn das Betriebssystem den Dienstendpunkt abbricht, da keine Ressourcen mehr verfügbar sind. Sie können über [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) zusätzliche Fehlerinformationen zurückgeben. In diesem Beispiel verwenden wir einen Schlüssel mit dem Namen `Status`, um detailliertere Fehlerinformationen an den Aufrufer zurückzugeben.

Der Aufruf von [**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) gibt [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) an den Aufrufer zurück.

## <a name="deploy-the-service-app-and-get-the-package-family-name"></a>Bereitstellen der Dienstanbieter-App und Abrufen des Paketfamiliennamens

Die Dienstanbieter-App muss bereitgestellt werden, bevor Sie sie von einem Client aus aufrufen können. Außerdem benötigen Sie den Paketfamiliennamen der Dienstanbieter-App, um sie aufrufen zu können.

Eine Möglichkeit zum Abrufen des Paketfamiliennamens der Dienstanbieter-App besteht darin, [**Windows.ApplicationModel.Package.Current.Id.FamilyName**](https://msdn.microsoft.com/library/windows/apps/br224670) im Projekt **AppServiceProvider** aufzurufen (z.B. in `public App()` in „App.xaml.cs”) und das Ergebnis zu notieren. Um das Projekt „AppServiceProvider” in Microsoft Visual Studio auszuführen, legen Sie es im Projektmappen-Explorer als Startprojekt fest, und führen Sie das Projekt aus.

Eine weitere Möglichkeit zum Abrufen des Paketfamiliennamens ist das Bereitstellen der Projektmappe (**Erstellen &gt; Projektmappe bereitstellen**) und Notieren des vollständigen Paketnamens im Ausgabefenster (**Ansicht &gt; Ausgabe**). Sie müssen die Plattforminformationen aus der Zeichenfolge im Ausgabefenster entfernen, um den Paketnamen abzuleiten. Wenn beispielsweise im Ausgabefenster der vollständige Paketname `Microsoft.SDKSamples.AppServicesProvider.CPP_1.0.0.0_x86__8wekyb3d8bbwe` ist, extrahieren Sie `1.0.0.0\_x86\_\_" leaving "Microsoft.SDKSamples.AppServicesProvider.CPP_8wekyb3d8bbwe` als Paketfamilienname.

## <a name="write-a-client-to-call-the-app-service"></a>Schreiben eines Clients zum Aufrufen des App-Diensts

1.  Fügen Sie der Projektmappe ein neues leeres Projekt für eine Universelle Windows-App mit dem Namen **Datei &gt; Hinzufügen &gt; Neues Projekt** hinzu. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf **Installiert &gt; Andere Sprachen &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Leere App (Windows Universal)** und nennen Sie es **ClientApp**.
2.  Fügen Sie im Projekt „ClientApp” am Anfang von „MainPage.xaml.cs” die folgende **using**-Anweisung hinzu:
    ```cs
    >using Windows.ApplicationModel.AppService;
    ```
3.  Fügen Sie „MainPage.xaml” ein Textfeld und eine Schaltfläche hinzu.
4.  Fügen Sie einen Klickhandler für die Schaltfläche hinzu, und fügen Sie der Signatur des Schaltflächenhandlers das Schlüsselwort **async** hinzu.
5.  Ersetzen Sie den Stub des Klickhandlers für die Schaltfläche durch den folgenden Code. Vergessen Sie nicht die `inventoryService`-Felddeklaration.

   ```cs
   private AppServiceConnection inventoryService;
   private async void button_Click(object sender, RoutedEventArgs e)
   {
       // Add the connection.
       if (this.inventoryService == null)
       {
           this.inventoryService = new AppServiceConnection();

           // Here, we use the app service name defined in the app service provider's Package.appxmanifest file in the <Extension> section.
           this.inventoryService.AppServiceName = "com.microsoft.inventory";

           // Use Windows.ApplicationModel.Package.Current.Id.FamilyName within the app service provider to get this value.
           this.inventoryService.PackageFamilyName = "replace with the package family name";

           var status = await this.inventoryService.OpenAsync();
           if (status != AppServiceConnectionStatus.Success)
           {
               textBox.Text= "Failed to connect";
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
           // Get the data  that the service sent  to us.
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
Ersetzen Sie den Paketfamiliennamen in der Zeile `this.inventoryService.PackageFamilyName = "replace with the package family name";` durch den Paketfamiliennamen des **AppServiceProvider**-Projekts, das Sie in [Bereitstellen der Dienstanbieter-App und Abrufen des Paketfamiliennamens](#deploy-the-service-app-and-get-the-package-family-name) erhalten haben.

Der Code richtet zunächst eine Verbindung mit dem App-Dienst ein. Die Verbindung bleibt offen, bis Sie `this.inventoryService` verwerfen. Der Name des App-Diensts muss mit dem Attribut **AppService-Name** übereinstimmen, das Sie der Package.appxmanifest-Datei des AppServiceProvider-Projekts hinzugefügt haben. In diesem Beispiel ist dies `<uap:AppService Name="com.microsoft.inventory"/>`.

Es wird ein [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) mit dem Namen **message** erstellt, um den Befehl anzugeben, der an den App-Dienst gesendet werden soll. Der Beispiel-App-Dienst erwartet einen Befehl, der angibt, welche der beiden Aktionen ausgeführt werden soll. Sie erhalten den Index aus dem Textfeld in der Client-App. Anschließend wird der Dienst mithilfe des Befehls `Item` aufgerufen, um die Beschreibung des Elements zu erhalten. Anschließend wird der Aufruf mit dem Befehl `Price` ausgeführt, um den Preis des Artikels zu erhalten. Der Text der Schaltfläche wird auf das Ergebnis festgelegt.

Da [**AppServiceResponseStatus**](https://msdn.microsoft.com/library/windows/apps/dn921724) nur angibt, ob das Betriebssystem den Aufruf mit dem App-Dienst verknüpfen konnte, muss der Schlüssel `Status` im [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) geprüft werden, den wir vom App-Dienst erhalten, um sicherzustellen, dass die Anforderung erfüllt werden konnte.

6.  Legen Sie das Projekt „ClientApp” in Visual Studio im Projektmappen-Explorer als Startprojekt fest, und führen Sie die Projektmappe aus. Geben Sie 1 in das Textfeld ein, und klicken Sie auf die Schaltfläche. Der Dienst sollte „Stuhl: Preis = 88,99“ zurückgeben.

    ![Beispiel-App, die Stuhlpreis = 88,99 anzeigt](images/appserviceclientapp.png)

Wenn beim Aufruf des App-Diensts ein Fehler auftritt, überprüfen Sie in „ClientApp” Folgendes:

1.  Stellen Sie sicher, dass der Paketfamilienname, der der Bestandsdienstverbindung zugewiesen ist, mit dem Paketfamiliennamen der App „AppServiceProvider” übereinstimmt. Weitere Informationen finden Sie unter **button\_Click()**`this.inventoryService.PackageFamilyName = "...";`).
2.  Überprüfen Sie in **button\_Click()**, ob der App-Dienstname, der der Bestandsdienstverbindung zugewiesen ist, dem in der Datei „Package.appxmanifest” von „AppServiceProvider” angegebenen Namen des App-Diensts entspricht. Weitere Informationen finden Sie unter `this.inventoryService.AppServiceName = "com.microsoft.inventory";`.
3.  Stellen Sie sicher, dass die App „AppServiceProvider” bereitgestellt wurde (klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Bereitstellen** aus).

## <a name="debug-the-app-service"></a>Debuggen des App-Diensts

1.  Stellen Sie vor dem Debuggen sicher, dass die Projektmappe bereitgestellt wurde. Die App Dienstanbieter-App muss bereitgestellt werden, bevor der Dienst aufgerufen werden kann. (Klicken Sie in Visual Studio auf **Erstellen &gt; Projektmappe bereitstellen**.)
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt **AppServiceProvider**, und wählen Sie **Properties** aus. Ändern Sie auf der Registerkarte **Debuggen** die **Startaktion** in **Eigenen Code zunächst nicht starten, sondern debuggen**. (Hinweis: wenn Sie nicht C++ zum Implementieren Ihres App-Dienstanbieters verwenden, müssen Sie auf der Registerkarte **Debuggen** die Option **Anwendung starten** auf **Nein** ändern).
3.  Legen Sie im Projekt „MyAppService” in der Datei „Class1.cs” einen Haltepunkt in `OnRequestReceived()` fest.
4.  Legen Sie das Projekt „AppServiceProvider” als Startprojekt fest, und drücken Sie F5.
5.  Starten Sie „ClientApp” über das Startmenü (nicht über Visual Studio).
6.  Geben Sie 1 in das Textfeld ein, und klicken Sie auf die Schaltfläche. Der Debugger stoppt im App-Dienstaufruf am Haltepunkt in Ihrem App-Dienst.

## <a name="debug-the-client"></a>Debuggen des Clients

1.  Folgen Sie zum Debuggen des Clients, der den App-Dienst aufruft, den Anweisungen im vorherigen Schritt.
2.  Starten Sie „ClientApp” über das Startmenü.
3.  Hängen Sie den Debugger an den Prozess „ClientApp.exe” an (nicht an den Prozess „ApplicationFrameHost.exe”). (Klicken Sie in Visual Studio auf **Debuggen &gt; An den Prozess anhängen**.)
4.  Legen Sie im Projekt „ClientApp” einen Haltepunkt in **button\_Click()** fest.
5.  Die Haltepunkte in der Client-App und im App-Dienst werden jetzt erreicht, wenn Sie 1 in das Textfeld von „ClientApp” eingeben und auf die Schaltfläche klicken.

## <a name="general-app-service-troubleshooting"></a>Allgemeine Problembehandlung von App-Diensten ##

Wenn beim Versuch, eine App mit einem Dienst zu verbinden der Status **AppUnavailable** auftritt, überprüfen Sie Folgendes:

- Stellen Sie sicher, dass das App-Dienstanbieterprojekt und das App-Dienstprojekt bereitgestellt sind. Beide müssen bereitgestellt werden, bevor der Client ausgeführt werden kann, da andernfalls der Client keine Verbindung zulassen kann. Sie können von Visual Studio aus mithilfe von **Erstellen** > **Projektmappe bereitstellen** bereitstellen.
- Stellen Sie im Projektmappen-Explorer sicher, dass Ihr App-Dienstanbieterprojekt einen Projekt-zu-Projekt-Verweis auf das Projekt hat, das den App-Dienst implementiert.
- Vergewissern Sie sich, dass der Eintrag `<Extensions>` und sein untergeordnetes Elemente zur Datei "Package.appxmanifest" des App-Dienstanbieterprojekts wie oben angegeben hinzugefügt wurden [Hinzufügen einer App-Diensterweiterung zu „package.appxmanifest”](#appxmanifest).
- Vergewissern Sie sich, dass die Zeichenfolge `AppServiceConnection.AppServiceName` in Ihrem Client, das den App-Dienstanbieter aufruft der Zeichenfolge `<uap3:AppService Name="..." />` der „Package.appxmanifest”-Datei des App-Dienstanbieterprojekts entspricht.
- Stellen Sie sicher, dass `AppServiceConnection.PackageFamilyName` dem Paketfamiliennamen der App-Dienstanbieterkomponente wie in [Hinzufügen eine App-Diensterweiterung zu "Package.appxmanifest"](#appxmanifest) angegeben entspricht.
- Für App-Dienste außerhalb des Prozesses wie in diesem Beispiel wird ein, überprüfen Sie, dass der `EntryPoint` des `<uap:Extension ...>` Elements „Package.appxmanifest”-Datei des App-Dienstanbieterprojekts dem Namespace und dem Klassennamen der öffentliche Klasse entspricht, das der `IBackgroundTask` in Ihrem App-Dienst-Projekt entspricht.

### <a name="troubleshoot-debugging"></a>Problembehandlung beim Debuggen

Wenn der Debugger nicht an Haltepunkten in Ihrem App-Dienstanbieter oder App-Dienst-Projekte beendet wird, überprüfen Sie Folgendes:

- Stellen Sie sicher, dass das App-Dienstanbieterprojekt und das App-Dienstprojekt bereitgestellt sind. Beide müssen bereitgestellt werden, bevor der Client ausgeführt wird. Sie können diese von Visual Studio aus mithilfe von **Erstellen** > **Projektmappe bereitstellen** bereitstellen.
- Stellen Sie sicher, dass das Projekt, das Sie debuggen möchten, als Startprojekt festgelegt ist und dass die Debugging-Eigenschaften für das Projekt so festgelegt sind, das das Projekt nicht ausgeführt wird, wenn F5 gedrückt wird. Klicken Sie mit der rechten Maustaste auf **Eigenschaften** und dann **Debug** (oder **Debugging** in C++). In C#, ändern Sie die **Startaktion** in **Eigenen Code zunächst nicht starten, sondern debuggen**. Legen Sie in C++ **Anwendung starten** auf **Nein** fest.

## <a name="remarks"></a>Anmerkungen

Dieses Beispiel ist eine Einführung in das Erstellen eines App-Diensts, das als Hintergrundaufgabe ausgeführt wird, und Aufrufen des Diensts in einer anderen App. Die wichtigsten Punkte sind das Erstellen einer Hintergrundaufgabe zum Hosten des App-Diensts, das Hinzufügen der Erweiterung „windows.appservice” zur Datei „Package.appxmanifest” der App des App-Dienstanbieters, das Abrufen des Paketfamiliennamens der App des App-Dienstanbieters, sodass in der Client-App eine Verbindung damit hergestellt werden kann, indem ein Projekt-zu-Projekt-Verweis vom App-Dienstanbieterprojekt auf das App-Dienst-Projekt hergestellt wird und das Verwenden von [**Windows.ApplicationModel.AppService.AppServiceConnection**](https://msdn.microsoft.com/library/windows/apps/dn921704) zum Aufrufen des Diensts.

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
            this.backgroundTaskDeferral = taskInstance.GetDeferral(); // Get a deferral so that the service isn't terminated.
            taskInstance.Canceled += OnTaskCanceled; // Associate a cancellation handler with the background task.

            // Retrieve the app service connection and set up a listener for incoming app service requests.
            var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
            appServiceconnection = details.AppServiceConnection;
            appServiceconnection.RequestReceived += OnRequestReceived;
        }

        private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            // Get a deferral because we use an awaitable API below to respond to the message
            // and we don't want this call to get cancelled while we are waiting.
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

            await args.Request.SendResponseAsync(returnData); // Return the data to the caller.
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
