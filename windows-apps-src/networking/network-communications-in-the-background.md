---
author: stevewhims
description: Um die Netzwerkkommunikation fortzusetzen, während sie sich nicht im Vordergrund befindet, kann eine App Hintergrundaufgaben und entweder Socketbroker- oder Steuerkanaltrigger verwenden.
title: Netzwerkkommunikation im Hintergrund
ms.assetid: 537F8E16-9972-435D-85A5-56D5764D3AC2
ms.author: stwhi
ms.date: 06/14/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 34fad804bb36ad1b4ce92a56772c33318e10faa8
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6655544"
---
# <a name="network-communications-in-the-background"></a><span data-ttu-id="3f431-104">Netzwerkkommunikation im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="3f431-104">Network communications in the background</span></span>
<span data-ttu-id="3f431-105">Um die Netzwerkkommunikation fortzusetzen, während Sie sich nicht im Vordergrund befindet, kann Ihre app Hintergrundaufgaben und eine der folgenden zwei Optionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="3f431-105">To continue network communication while it's not in the foreground, your app can use background tasks and one of these two options.</span></span>
- <span data-ttu-id="3f431-106">Socketbroker.</span><span class="sxs-lookup"><span data-stu-id="3f431-106">Socket broker.</span></span> <span data-ttu-id="3f431-107">Wenn Ihre app Sockets für dauerhafte Verbindungen verwendet, wenn sie den Vordergrund verlässt, können sie den Besitz eines Sockets an einen System-socketbroker delegieren.</span><span class="sxs-lookup"><span data-stu-id="3f431-107">If your app uses sockets for long-term connections then, when it leaves the foreground, it can delegate ownership of a socket to a system socket broker.</span></span> <span data-ttu-id="3f431-108">Der Broker dann: Ihre app aktiviert, wenn Datenverkehr, auf dem Socket eingeht; überträgt den Besitz zurück an Ihre app; und die app dann verarbeitet den eingehenden Datenverkehr.</span><span class="sxs-lookup"><span data-stu-id="3f431-108">The broker then: activates your app when traffic arrives on the socket; transfers ownership back to your app; and your app then processes the arriving traffic.</span></span>
- <span data-ttu-id="3f431-109">Steuerkanaltrigger.</span><span class="sxs-lookup"><span data-stu-id="3f431-109">Control channel triggers.</span></span> 

## <a name="performing-network-operations-in-background-tasks"></a><span data-ttu-id="3f431-110">Netzwerkvorgänge in Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="3f431-110">Performing network operations in background tasks</span></span>
- <span data-ttu-id="3f431-111">Verwenden Sie einen [SocketActivityTrigger](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.socketactivitytrigger), um die Hintergrundaufgabe zu aktivieren, wenn ein Paket empfangen wird und Sie eine kurzlebige Aufgabe ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="3f431-111">Use a [SocketActivityTrigger](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.socketactivitytrigger) to activate the background task when a packet is received and you need to perform a short-lived task.</span></span> <span data-ttu-id="3f431-112">Nach dem Ausführen der Aufgabe sollte die Hintergrundaufgabe beendet werden, um Energie zu sparen.</span><span class="sxs-lookup"><span data-stu-id="3f431-112">After performing the task, the background task should terminate in order to save power.</span></span>
- <span data-ttu-id="3f431-113">Verwenden Sie einen [ControlChannelTrigger](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.ControlChannelTrigger), um die Hintergrundaufgabe zu aktivieren, wenn ein Paket empfangen wird und Sie eine langlebige Aufgabe ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="3f431-113">Use a [ControlChannelTrigger](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.ControlChannelTrigger) to activate the background task when a packet is received and you need to perform a long-lived task.</span></span>

**<span data-ttu-id="3f431-114">Netzwerkbezogene Bedingungen und flags</span><span class="sxs-lookup"><span data-stu-id="3f431-114">Network-related conditions and flags</span></span>**

- <span data-ttu-id="3f431-115">Fügen Sie die **InternetAvailable**-Bedingung zur Hintergrundaufgabe [BackgroundTaskBuilder.AddCondition](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskBuilder) hinzu, um die Hintergrundaufgabe zu verzögern, bis der Netzwerkstapel ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-115">Add the **InternetAvailable** condition to your background task [BackgroundTaskBuilder.AddCondition](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskBuilder) to delay triggering the background task until the network stack is running.</span></span> <span data-ttu-id="3f431-116">Dies spart Energie, da die Hintergrundaufgabe nicht ausgeführt wird, bis das Netzwerk verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="3f431-116">This condition saves power because the background task won't execute until the network is up.</span></span> <span data-ttu-id="3f431-117">Diese Bedingung stellt keine Aktivierung in Echtzeit bereit.</span><span class="sxs-lookup"><span data-stu-id="3f431-117">This condition does not provide real-time activation.</span></span>

<span data-ttu-id="3f431-118">Unabhängig vom verwendeten Auslöser, legen Sie [IsNetworkRequested](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.backgroundtaskbuilder) für die Hintergrundaufgabe fest, um sicherzustellen, dass das Netzwerk während der Ausführung der Hintergrundaufgabe unterbrechungsfreie ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-118">Regardless of the trigger you use, set [IsNetworkRequested](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.backgroundtaskbuilder) on your background task to ensure that the network stays up while the background task runs.</span></span> <span data-ttu-id="3f431-119">Dies weist die Infrastruktur für Hintergrundaufgaben an, die Netzwerkverbindung für die Ausführung der Aufgabe auch dann beizubehalten, wenn sich das Gerät im verbundenen Standbymodus befindet.</span><span class="sxs-lookup"><span data-stu-id="3f431-119">This tells the background task infrastructure to keep the network up while the task is executing, even if the device has entered Connected Standby mode.</span></span> <span data-ttu-id="3f431-120">Wenn Ihre Hintergrundaufgabe keine **IsNetworkRequested**verwendet werden, klicken Sie dann kann Ihre Hintergrundaufgabe nicht Zugriff auf das Netzwerk, wenn sich dieses im verbundenen Standbymodus befindet (z. B. wenn der Bildschirm eines Smartphones ausgeschaltet ist).</span><span class="sxs-lookup"><span data-stu-id="3f431-120">If your background task does not use **IsNetworkRequested**, then your background task will not be able to access the network when in Connected Standby mode (for example, when a phone's screen is turned off).</span></span>

## <a name="socket-broker-and-the-socketactivitytrigger"></a><span data-ttu-id="3f431-121">Socketbroker und SocketActivityTrigger</span><span class="sxs-lookup"><span data-stu-id="3f431-121">Socket broker and the SocketActivityTrigger</span></span>
<span data-ttu-id="3f431-122">Wenn Ihre App eine [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319)-, [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)- oder [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906)-Verbindung verwendet, sollten Sie mithilfe von [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) und Socketbroker Benachrichtigungen einrichten, um über eingehenden Datenverkehr für ihre App informiert zu werden, wenn diese im Hintergrund ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-122">If your app uses [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319), [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882), or [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906) connections, then you should use [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) and the socket broker to be notified when traffic arrives for your app while it's not in the foreground.</span></span>

<span data-ttu-id="3f431-123">Damit die App Daten, die auf einem Socket empfangen werden, auch bei Inaktivität empfangen und verarbeiten kann, muss die App beim Start eine einmalige Einrichtung vornehmen und den Socket-Besitz dann an den Socketbroker übertragen, wenn sie in einen nicht aktiven Zustand wechselt.</span><span class="sxs-lookup"><span data-stu-id="3f431-123">In order for your app to receive and process data received on a socket when your app is not active, your app must perform some one-time setup at startup, and then transfer socket ownership to the socket broker when it is transitioning to a state where it is not active.</span></span>

<span data-ttu-id="3f431-124">Bei den Schritten für die einmalige Einrichtung handelt es sich um das Erstellen eines Triggers, das Registrieren einer Hintergrundaufgabe für den Trigger und das Aktivieren des Sockets für den Socketbroker:</span><span class="sxs-lookup"><span data-stu-id="3f431-124">The one-time setup steps are to create a trigger, to register a background task for the trigger, and to enable the socket for the socket broker:</span></span>
  - <span data-ttu-id="3f431-125">Erstellen Sie einen **SocketActivityTrigger**, und registrieren Sie eine Hintergrundaufgabe für den Trigger, wobei der TaskEntryPoint-Parameter auf den Code zum Verarbeiten des empfangenen Pakets festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="3f431-125">Create a **SocketActivityTrigger** and register a background task for the trigger with the TaskEntryPoint parameter set to your code for processing a received packet.</span></span>
```csharp
            var socketTaskBuilder = new BackgroundTaskBuilder();
            socketTaskBuilder.Name = _backgroundTaskName;
            socketTaskBuilder.TaskEntryPoint = _backgroundTaskEntryPoint;
            var trigger = new SocketActivityTrigger();
            socketTaskBuilder.SetTrigger(trigger);
            _task = socketTaskBuilder.Register();
```
  - <span data-ttu-id="3f431-126">Rufen Sie **EnableTransferOwnership** für den Socket auf, bevor Sie die Bindung für den Socket festlegen.</span><span class="sxs-lookup"><span data-stu-id="3f431-126">Call **EnableTransferOwnership** on the socket, before you bind the socket.</span></span>
```csharp
           _tcpListener = new StreamSocketListener();

           // Note that EnableTransferOwnership() should be called before bind,
           // so that tcpip keeps required state for the socket to enable connected
           // standby action. Background task Id is taken as a parameter to tie wake pattern
           // to a specific background task.  
           _tcpListener. EnableTransferOwnership(_task.TaskId,SocketActivityConnectedStandbyAction.Wake);
           _tcpListener.ConnectionReceived += OnConnectionReceived;
           await _tcpListener.BindServiceNameAsync("my-service-name");
```

<span data-ttu-id="3f431-127">Nachdem der Socket ordnungsgemäß eingerichtet ist, rufen Sie vor Anhalten der App für den Socket **TransferOwnership** auf, um ihn an einen Socketbroker zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="3f431-127">Once your socket is properly set up, when your app is about to suspend, call **TransferOwnership** on the socket to transfer it to a socket broker.</span></span> <span data-ttu-id="3f431-128">Der Broker überwacht den Socket und aktiviert die Hintergrundaufgabe, wenn Daten empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-128">The broker monitors the socket and activates your background task when data is received.</span></span> <span data-ttu-id="3f431-129">Im folgenden Beispiel wird die **TransferOwnership**-Hilfsfunktion verwendet, um die Übertragung für **StreamSocketListener**-Sockets auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3f431-129">The following example includes a utility **TransferOwnership** function to perform the transfer for **StreamSocketListener** sockets.</span></span> <span data-ttu-id="3f431-130">(Beachten Sie, dass unterschiedliche Sockettypen jeweils eine eigene **TransferOwnership**-Methode besitzen. Sie müssen daher für die Besitzübertragung des Sockets die richtige Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="3f431-130">(Note that the different types of sockets each have their own **TransferOwnership** method, so you must call the method appropriate for the socket whose ownership you are transferring.</span></span> <span data-ttu-id="3f431-131">In der Regel enthält der Code eine überladene **TransferOwnership**-Hilfsfunktion mit einer einzelnen Implementierung für jeden verwendeten Sockettyp, damit der **OnSuspending**-Code gut lesbar bleibt.)</span><span class="sxs-lookup"><span data-stu-id="3f431-131">Your code would probably contain an overloaded **TransferOwnership** helper with one implementation for each socket type you use, so that the **OnSuspending** code remains easy to read.)</span></span>

<span data-ttu-id="3f431-132">Eine App überträgt den Besitz eines Sockets an einen Socketbroker und übergibt die ID für die Hintergrundaufgabe mit der entsprechenden Methode:</span><span class="sxs-lookup"><span data-stu-id="3f431-132">An app transfers ownership of a socket to a socket broker and passes the ID for the background task using the appropriate one of the following methods:</span></span>
-   <span data-ttu-id="3f431-133">Einer der [**TransferOwnership**](https://msdn.microsoft.com/library/windows/apps/dn804256)-Methoden für einen [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319).</span><span class="sxs-lookup"><span data-stu-id="3f431-133">One of the [**TransferOwnership**](https://msdn.microsoft.com/library/windows/apps/dn804256) methods on a [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319).</span></span>
-   <span data-ttu-id="3f431-134">Einer der [**TransferOwnership**](https://msdn.microsoft.com/library/windows/apps/dn781433)-Methoden für einen [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882).</span><span class="sxs-lookup"><span data-stu-id="3f431-134">One of the [**TransferOwnership**](https://msdn.microsoft.com/library/windows/apps/dn781433) methods on a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882).</span></span>
-   <span data-ttu-id="3f431-135">Einer der [**TransferOwnership**](https://msdn.microsoft.com/library/windows/apps/dn804407)-Methoden für einen [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906).</span><span class="sxs-lookup"><span data-stu-id="3f431-135">One of the [**TransferOwnership**](https://msdn.microsoft.com/library/windows/apps/dn804407) methods on a [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906).</span></span>

```csharp

// declare int _transferOwnershipCount as a field.

private void TransferOwnership(StreamSocketListener tcpListener)
{
    await tcpListener.CancelIOAsync();

    var dataWriter = new DataWriter();
    ++_transferOwnershipCount;
    dataWriter.WriteInt32(transferOwnershipCount);
    var context = new SocketActivityContext(dataWriter.DetachBuffer());
    tcpListener.TransferOwnership(_socketId, context);
}

private void OnSuspending(object sender, SuspendingEventArgs e)
{
    var deferral = e.SuspendingOperation.GetDeferral();

    TransferOwnership(_tcpListener);
    deferral.Complete();
}
```
<span data-ttu-id="3f431-136">Im Ereignishandler für die Hintergrundaufgabe:</span><span class="sxs-lookup"><span data-stu-id="3f431-136">In your background task's event handler:</span></span>
   -  <span data-ttu-id="3f431-137">Rufen Sie zunächst eine Hintergrundaufgabenverzögerung ab, damit Sie das Ereignis mit asynchronen Methoden behandeln können.</span><span class="sxs-lookup"><span data-stu-id="3f431-137">First, get a background task deferral so that you can handle the event using asynchronous methods.</span></span>
```csharp
var deferral = taskInstance.GetDeferral();
```
   -  <span data-ttu-id="3f431-138">Als Nächstes extrahieren Sie die SocketActivityTriggerDetails aus den Ereignisargumenten und suchen den Grund für das Auslösen des Ereignisses:</span><span class="sxs-lookup"><span data-stu-id="3f431-138">Next, extract the SocketActivityTriggerDetails from the event arguments, and find the reason that the event was raised:</span></span>
```csharp
var details = taskInstance.TriggerDetails as SocketActivityTriggerDetails;
    var socketInformation = details.SocketInformation;
    switch (details.Reason)
```
   -   <span data-ttu-id="3f431-139">Wenn das Ereignis aufgrund der Socket-Aktivität ausgelöst wurde, erstellen Sie einen DataReader für den Socket, laden den Reader asynchron und verwenden die Daten entsprechend der Logik der App.</span><span class="sxs-lookup"><span data-stu-id="3f431-139">If the event was raised because of socket activity, create a DataReader on the socket, load the reader asynchronously, and then use the data according to your app's design.</span></span> <span data-ttu-id="3f431-140">Beachten Sie, dass Sie den Besitz des Sockets wieder an Socketbroker zurückgeben müssen, um bei weiterer Socket-Aktivität erneut benachrichtigt zu werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-140">Note that you must return ownership of the socket back to the socket broker, in order to be notified of further socket activity again.</span></span>

   <span data-ttu-id="3f431-141">Im folgenden Beispiel wird der vom Socket empfangene Text in einem Popup angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3f431-141">In the following example, the text received on the socket is displayed in a toast.</span></span>

```csharp
case SocketActivityTriggerReason.SocketActivity:
            var socket = socketInformation.StreamSocket;
            DataReader reader = new DataReader(socket.InputStream);
            reader.InputStreamOptions = InputStreamOptions.Partial;
            await reader.LoadAsync(250);
            var dataString = reader.ReadString(reader.UnconsumedBufferLength);
            ShowToast(dataString);
            socket.TransferOwnership(socketInformation.Id); /* Important! */
            break;
```

   -   <span data-ttu-id="3f431-142">Wenn das Ereignis ausgelöst wurde, weil ein Keep-Alive-Zeitgeber abgelaufen ist, sollte der Code Daten über den Socket senden, damit der Socket geöffnet bleibt und der Keep-Alive-Zeitgeber neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-142">If the event was raised because a keep alive timer expired, then your code should send some data over the socket in order to keep the socket alive and restart the keep alive timer.</span></span> <span data-ttu-id="3f431-143">Dabei ist es wiederum wichtig, den Besitz des Sockets zurück an den Socketbroker zu übertragen, um weitere Ereignisbenachrichtigungen zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="3f431-143">Again, it is important to return ownership of the socket back to the socket broker in order to receive further event notifications:</span></span>

```csharp
case SocketActivityTriggerReason.KeepAliveTimerExpired:
            socket = socketInformation.StreamSocket;
            DataWriter writer = new DataWriter(socket.OutputStream);
            writer.WriteBytes(Encoding.UTF8.GetBytes("Keep alive"));
            await writer.StoreAsync();
            writer.DetachStream();
            writer.Dispose();
            socket.TransferOwnership(socketInformation.Id); /* Important! */
            break;
```

   -   <span data-ttu-id="3f431-144">Wenn das Ereignis durch das Schließen des Sockets ausgelöst wurde, richten Sie den Socket erneut ein und stellen sicher, anschließend den Besitz des neuen Sockets an den Socketbroker zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="3f431-144">If the event was raised because the socket was closed, re-establish the socket, making sure that after you create the new socket, you transfer ownership of it to the socket broker.</span></span> <span data-ttu-id="3f431-145">In diesem Beispiel werden der Hostname und -port in den lokalen Einstellungen gespeichert, damit sie zum Einrichten einer neuen Socketverbindung verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="3f431-145">In this sample, the hostname and port are stored in local settings so that they can be used to establish a new socket connection:</span></span>

```csharp
case SocketActivityTriggerReason.SocketClosed:
            socket = new StreamSocket();
            socket.EnableTransferOwnership(taskInstance.Task.TaskId, SocketActivityConnectedStandbyAction.Wake);
            if (ApplicationData.Current.LocalSettings.Values["hostname"] == null)
            {
                break;
            }
            var hostname = (String)ApplicationData.Current.LocalSettings.Values["hostname"];
            var port = (String)ApplicationData.Current.LocalSettings.Values["port"];
            await socket.ConnectAsync(new HostName(hostname), port);
            socket.TransferOwnership(socketId);
            break;
```

   -   <span data-ttu-id="3f431-146">Denken Sie daran, die Verzögerung abzuschließen, sobald die Verarbeitung der Ereignisbenachrichtigung beendet wurde:</span><span class="sxs-lookup"><span data-stu-id="3f431-146">Don't forget to Complete your deferral, once you have finished processing the event notification:</span></span>

```csharp
  deferral.Complete();
```

<span data-ttu-id="3f431-147">Ein vollständiges Beispiel zur Verwendung des [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) und des Socketbroker finden Sie im [Beispiel für einen SocketActivityStreamSocket](http://go.microsoft.com/fwlink/p/?LinkId=620606).</span><span class="sxs-lookup"><span data-stu-id="3f431-147">For a complete sample demonstrating the use of the [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) and socket broker, see the [SocketActivityStreamSocket sample](http://go.microsoft.com/fwlink/p/?LinkId=620606).</span></span> <span data-ttu-id="3f431-148">Die Initialisierung des Sockets wird in „Scenario1\_Connect.xaml.cs“ und die Implementierung der Hintergrundaufgabe in „SocketActivityTask.cs“ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="3f431-148">The initialization of the socket is performed in Scenario1\_Connect.xaml.cs, and the background task implementation is in SocketActivityTask.cs.</span></span>

<span data-ttu-id="3f431-149">Wahrscheinlich wird Ihnen auffallen, dass im Beispiel beim Erstellen eines neuen Sockets oder beim Aufrufen eines vorhandenen Sockets **TransferOwnership** aufgerufen wird und dazu nicht der in diesem Thema beschriebene **OnSuspending**-Ereignishandler verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-149">You will probably notice that the sample calls **TransferOwnership** as soon as it creates a new socket or acquires an existing socket, rather than using the **OnSuspending** even handler to do so as described in this topic.</span></span> <span data-ttu-id="3f431-150">Dies liegt daran, dass in diesem Beispiel schwerpunktmäßig der [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) veranschaulicht werden soll und der Socket während der Ausführung für keine weiteren Aktivitäten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-150">This is because the sample focuses on demonstrating the [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009), and doesn't use the socket for any other activity while it is running.</span></span> <span data-ttu-id="3f431-151">In der Regel wird Ihre App komplexer sein, sodass Sie mit **OnSuspending** bestimmen sollten, wann **TransferOwnership** aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-151">Your app will probably be more complex, and should use **OnSuspending** to determine when to call **TransferOwnership**.</span></span>

## <a name="control-channel-triggers"></a><span data-ttu-id="3f431-152">Steuerkanaltrigger</span><span class="sxs-lookup"><span data-stu-id="3f431-152">Control channel triggers</span></span>
<span data-ttu-id="3f431-153">Stellen Sie zunächst sicher, dass Steuerkanaltrigger korrekt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-153">First, ensure that you're using control channel triggers (CCTs) appropriately.</span></span> <span data-ttu-id="3f431-154">Wenn Sie [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319)oder [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882), [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906) Verbindungen verwenden, empfehlen wir, dass Sie [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009)verwenden.</span><span class="sxs-lookup"><span data-stu-id="3f431-154">If you're using [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319), [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882), or [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906) connections, then we recommend that you use [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009).</span></span> <span data-ttu-id="3f431-155">Sie können Steuerkanaltrigger für **StreamSocket** verwenden, wobei diese jedoch mehr Ressourcen belegen und möglicherweise nicht im verbundenen Standbymodus funktionieren.</span><span class="sxs-lookup"><span data-stu-id="3f431-155">You can use CCTs for **StreamSocket**, but they use more resources and might not work in Connected Standby mode.</span></span>

<span data-ttu-id="3f431-156">Wenn Sie WebSockets, [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151), [**System.Net.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639)oder [**Windows.Web.Http.HttpClient**](/uwp/api/windows.web.http.httpclient)verwenden, müssen Sie [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)verwenden.</span><span class="sxs-lookup"><span data-stu-id="3f431-156">If you are using WebSockets, [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151), [**System.Net.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639), or [**Windows.Web.Http.HttpClient**](/uwp/api/windows.web.http.httpclient), then you must use [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span>

## <a name="controlchanneltrigger-with-websockets"></a><span data-ttu-id="3f431-157">ControlChannelTrigger mit WebSockets</span><span class="sxs-lookup"><span data-stu-id="3f431-157">ControlChannelTrigger with WebSockets</span></span>
<span data-ttu-id="3f431-158">Bei Verwendung von [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) oder [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) sind einige wichtige Punkte zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="3f431-158">Some special considerations apply when using [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) or [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span> <span data-ttu-id="3f431-159">Bei Verwendung von **MessageWebSocket** oder **StreamWebSocket** mit **ControlChannelTrigger** sollten Sie transportspezifische Verwendungsmuster und bewährte Methoden nutzen.</span><span class="sxs-lookup"><span data-stu-id="3f431-159">There are some transport-specific usage patterns and best practices that should be followed when using a **MessageWebSocket** or **StreamWebSocket** with **ControlChannelTrigger**.</span></span> <span data-ttu-id="3f431-160">Diese Aspekte beeinflussen, wie Anforderungen für den Paketempfang über **StreamWebSocket** verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-160">In addition, these considerations affect the way that requests to receive packets on the **StreamWebSocket** are handled.</span></span> <span data-ttu-id="3f431-161">Anforderungen für den Paketempfang über **MessageWebSocket** sind davon nicht betroffen.</span><span class="sxs-lookup"><span data-stu-id="3f431-161">Requests to receive packets on the **MessageWebSocket** are not affected.</span></span>

<span data-ttu-id="3f431-162">Beachten Sie bei Verwendung von [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) oder [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) die folgenden Verwendungsmuster und bewährten Methoden:</span><span class="sxs-lookup"><span data-stu-id="3f431-162">The following usage patterns and best practices should be followed when using [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) or [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032):</span></span>

-   <span data-ttu-id="3f431-163">Ein ausstehender Socketempfang muss immer bereitgestellt bleiben.</span><span class="sxs-lookup"><span data-stu-id="3f431-163">An outstanding socket receive must be kept posted at all times.</span></span> <span data-ttu-id="3f431-164">Das ist erforderlich, damit die Pushbenachrichtigungsaufgaben auftreten können.</span><span class="sxs-lookup"><span data-stu-id="3f431-164">This is required to allow the push notification tasks to occur.</span></span>
-   <span data-ttu-id="3f431-165">Das WebSocket-Protokoll definiert ein Standardmodell für Keep-Alive-Meldungen.</span><span class="sxs-lookup"><span data-stu-id="3f431-165">The WebSocket protocol defines a standard model for keep-alive messages.</span></span> <span data-ttu-id="3f431-166">Die [**WebSocketKeepAlive**](https://msdn.microsoft.com/library/windows/apps/hh701531)-Klasse kann vom Client initiierte WebSocket-Protokoll-Keep-Alive-Meldungen an den Server senden.</span><span class="sxs-lookup"><span data-stu-id="3f431-166">The [**WebSocketKeepAlive**](https://msdn.microsoft.com/library/windows/apps/hh701531) class can send client-initiated WebSocket protocol keep-alive messages to the server.</span></span> <span data-ttu-id="3f431-167">Die **WebSocketKeepAlive**-Klasse muss von der App als „TaskEntryPoint“ für einen „KeepAliveTrigger“ registriert werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-167">The **WebSocketKeepAlive** class should be registered as the TaskEntryPoint for a KeepAliveTrigger by the app.</span></span>

<span data-ttu-id="3f431-168">Die Verarbeitung von Anforderungen für den Paketempfang über [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) wird durch eine Reihe besonderer Faktoren beeinflusst.</span><span class="sxs-lookup"><span data-stu-id="3f431-168">Some special considerations affect the way that requests to receive packets on the [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) are handled.</span></span> <span data-ttu-id="3f431-169">Insbesondere gilt, dass die App bei Verwendung von **StreamWebSocket** mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) für Lesevorgänge statt des **await**-Modells in C# und VB.NET oder Aufgaben in C++ ein asynchrones Rohmuster verwenden muss.</span><span class="sxs-lookup"><span data-stu-id="3f431-169">In particular, when using a **StreamWebSocket** with the [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032), your app must use a raw async pattern for handling reads instead of the **await** model in C# and VB.NET or Tasks in C++.</span></span> <span data-ttu-id="3f431-170">Ein asynchrones Rohmuster wird im folgenden Codebeispiel weiter unten in diesem Abschnitt veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="3f431-170">The raw async pattern is illustrated in a code sample later in this section.</span></span>

<span data-ttu-id="3f431-171">Bei Verwendung eines asynchronen Rohmusters kann Windows die [**IBackgroundTask.Run**](https://msdn.microsoft.com/library/windows/apps/br224811)-Methode für die Hintergrundaufgabe für [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) mit der Rückgabe des Empfangsabschlussrückrufs synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="3f431-171">Using the raw async pattern allows Windows to synchronize the [**IBackgroundTask.Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method on the background task for the [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) with the return of the receive completion callback.</span></span> <span data-ttu-id="3f431-172">Die **Run**-Methode wird nach Rückgabe des Abschlussrückrufs aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="3f431-172">The **Run** method is invoked after the completion callback returns.</span></span> <span data-ttu-id="3f431-173">Dies stellt sicher, dass die App die Daten/Fehler vor Aufruf der **Run**-Methode empfängt.</span><span class="sxs-lookup"><span data-stu-id="3f431-173">This ensures that the app has received the data/errors before the **Run** method is invoked.</span></span>

<span data-ttu-id="3f431-174">Beachten Sie, dass die App einen weiteren Lesevorgang bereitstellen muss, bevor sie die Steuerung vom Abschlussrückruf zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="3f431-174">It is important to note that the app has to post another read before it returns control from the completion callback.</span></span> <span data-ttu-id="3f431-175">Berücksichtigen Sie außerdem, dass [**DataReader**](https://msdn.microsoft.com/library/windows/apps/br208119) nicht direkt mit dem [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842)- oder [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923)-Transport verwendet werden kann, da hierdurch die oben beschriebene Synchronisierung unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-175">It is also important to note that the [**DataReader**](https://msdn.microsoft.com/library/windows/apps/br208119) cannot be directly used with the [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) or [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) transport since that breaks the synchronization described above.</span></span> <span data-ttu-id="3f431-176">Die direkte Verwendung der [**DataReader.LoadAsync**](https://msdn.microsoft.com/library/windows/apps/br208135)-Methode zusätzlich zum Transport wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3f431-176">It is not supported to use the [**DataReader.LoadAsync**](https://msdn.microsoft.com/library/windows/apps/br208135) method directly on top of the transport.</span></span> <span data-ttu-id="3f431-177">Stattdessen kann die von der [**IInputStream.ReadAsync**](https://msdn.microsoft.com/library/windows/apps/br241719)-Methode für die [**StreamWebSocket.InputStream**](https://msdn.microsoft.com/library/windows/apps/br226936)-Eigenschaft zurückgegebene [**IBuffer**](https://msdn.microsoft.com/library/windows/apps/br241656)-Schnittstelle später zur weiteren Verarbeitung an die [**DataReader.FromBuffer**](https://msdn.microsoft.com/library/windows/apps/br208133)-Methode übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-177">Instead, the [**IBuffer**](https://msdn.microsoft.com/library/windows/apps/br241656) returned by the [**IInputStream.ReadAsync**](https://msdn.microsoft.com/library/windows/apps/br241719) method on the [**StreamWebSocket.InputStream**](https://msdn.microsoft.com/library/windows/apps/br226936) property can be later passed to [**DataReader.FromBuffer**](https://msdn.microsoft.com/library/windows/apps/br208133) method for further processing.</span></span>

<span data-ttu-id="3f431-178">Im folgenden Beispiel wird ein asynchrones Rohmuster zur Verarbeitung von Lesevorgängen für [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) verwendet.</span><span class="sxs-lookup"><span data-stu-id="3f431-178">The following sample shows how to use a raw async pattern for handling reads on the [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923).</span></span>

```csharp
void PostSocketRead(int length)
{
    try
    {
        var readBuf = new Windows.Storage.Streams.Buffer((uint)length);
        var readOp = socket.InputStream.ReadAsync(readBuf, (uint)length, InputStreamOptions.Partial);
        readOp.Completed = (IAsyncOperationWithProgress<IBuffer, uint>
            asyncAction, AsyncStatus asyncStatus) =>
        {
            switch (asyncStatus)
            {
                case AsyncStatus.Completed:
                case AsyncStatus.Error:
                    try
                    {
                        // GetResults in AsyncStatus::Error is called as it throws a user friendly error string.
                        IBuffer localBuf = asyncAction.GetResults();
                        uint bytesRead = localBuf.Length;
                        readPacket = DataReader.FromBuffer(localBuf);
                        OnDataReadCompletion(bytesRead, readPacket);
                    }
                    catch (Exception exp)
                    {
                        Diag.DebugPrint("Read operation failed:  " + exp.Message);
                    }
                    break;
                case AsyncStatus.Canceled:

                    // Read is not cancelled in this sample.
                    break;
           }
       };
   }
   catch (Exception exp)
   {
       Diag.DebugPrint("failed to post a read failed with error:  " + exp.Message);
   }
}
```

<span data-ttu-id="3f431-179">Der Handler für den Abschluss des Lesevorgangs wird auf jeden Fall ausgelöst, bevor die [**IBackgroundTask.Run**](https://msdn.microsoft.com/library/windows/apps/br224811)-Methode für die Hintergrundaufgabe für [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-179">The read completion handler is guaranteed to fire before the [**IBackgroundTask.Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method on the background task for the [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) is invoked.</span></span> <span data-ttu-id="3f431-180">Windows hält die interne Synchronisierung an, um auf die Rückgabe einer App vom Rückruf des Lesevorgangabschlusses zu warten.</span><span class="sxs-lookup"><span data-stu-id="3f431-180">Windows has internal synchronization to wait for an app to return from the read completion callback.</span></span> <span data-ttu-id="3f431-181">Meist kann die App die Daten oder den Fehler für [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) oder [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) im Rückruf des Lesevorgangsabschlusses in kurzer Zeit verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="3f431-181">The app typically quickly processes the data or the error from the [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) or [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) in the read completion callback.</span></span> <span data-ttu-id="3f431-182">Die Meldung als solche wird im Kontext der **IBackgroundTask.Run**-Methode verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="3f431-182">The message itself is processed within the context of the **IBackgroundTask.Run** method.</span></span> <span data-ttu-id="3f431-183">Im Beispiel unten wird dieser Aspekt anhand einer Meldungswarteschlange veranschaulicht, in die der Handler für den Lesevorgangsabschluss die Meldung einfügt, die später von der Hintergrundaufgabe verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-183">In this sample below, this point is illustrated by using a message queue that the read completion handler inserts the message into and the background task later processes.</span></span>

<span data-ttu-id="3f431-184">Im folgenden Beispiel wird der Handler für den Lesevorgangsabschluss zusammen mit einem asynchronen Rohmuster zur Verarbeitung von Lesevorgängen für [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) verwendet.</span><span class="sxs-lookup"><span data-stu-id="3f431-184">The following sample shows the read completion handler to use with a raw async pattern for handling reads on the [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923).</span></span>

```csharp
public void OnDataReadCompletion(uint bytesRead, DataReader readPacket)
{
    if (readPacket == null)
    {
        Diag.DebugPrint("DataReader is null");

        // Ideally when read completion returns error,
        // apps should be resilient and try to
        // recover if there is an error by posting another recv
        // after creating a new transport, if required.
        return;
    }
    uint buffLen = readPacket.UnconsumedBufferLength;
    Diag.DebugPrint("bytesRead: " + bytesRead + ", unconsumedbufflength: " + buffLen);

    // check if buffLen is 0 and treat that as fatal error.
    if (buffLen == 0)
    {
        Diag.DebugPrint("Received zero bytes from the socket. Server must have closed the connection.");
        Diag.DebugPrint("Try disconnecting and reconnecting to the server");
        return;
    }

    // Perform minimal processing in the completion
    string message = readPacket.ReadString(buffLen);
    Diag.DebugPrint("Received Buffer : " + message);

    // Enqueue the message received to a queue that the push notify
    // task will pick up.
    AppContext.messageQueue.Enqueue(message);

    // Post another receive to ensure future push notifications.
    PostSocketRead(MAX_BUFFER_LENGTH);
}
```

<span data-ttu-id="3f431-185">Ein weiteres Detail für WebSockets ist der Keep-Alive-Handler.</span><span class="sxs-lookup"><span data-stu-id="3f431-185">An additional detail for Websockets is the keep-alive handler.</span></span> <span data-ttu-id="3f431-186">Das WebSocket-Protokoll definiert ein Standardmodell für Keep-Alive-Meldungen.</span><span class="sxs-lookup"><span data-stu-id="3f431-186">The WebSocket protocol defines a standard model for keep-alive messages.</span></span>

<span data-ttu-id="3f431-187">Bei Verwendung der Klasse [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) oder [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) muss eine [**WebSocketKeepAlive**](https://msdn.microsoft.com/library/windows/apps/hh701531)-Klasseninstanz als [**TaskEntryPoint**](https://msdn.microsoft.com/library/windows/apps/br224774) für KeepAliveTrigger registriert werden. Dies ist erforderlich, damit die App fortgesetzt werden kann und regelmäßig Keep-Alive-Meldungen an den Server (Remoteendpunkt) gesendet werden können.</span><span class="sxs-lookup"><span data-stu-id="3f431-187">When using [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) or [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923), register a [**WebSocketKeepAlive**](https://msdn.microsoft.com/library/windows/apps/hh701531) class instance as the [**TaskEntryPoint**](https://msdn.microsoft.com/library/windows/apps/br224774) for a KeepAliveTrigger to allow the app to be unsuspended and send keep-alive messages to the server (remote endpoint) periodically.</span></span> <span data-ttu-id="3f431-188">Dieser Vorgang muss sowohl im App-Code für die Hintergrundregistrierung als auch im Paketmanifest enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="3f431-188">This should be done as part of the background registration app code as well as in the package manifest.</span></span>

<span data-ttu-id="3f431-189">Der Aufgabeneinstiegspunkt für [**Windows.Sockets.WebSocketKeepAlive**](https://msdn.microsoft.com/library/windows/apps/hh701531) muss an zwei Stellen angegeben werden:</span><span class="sxs-lookup"><span data-stu-id="3f431-189">This task entry point of [**Windows.Sockets.WebSocketKeepAlive**](https://msdn.microsoft.com/library/windows/apps/hh701531) needs to be specified in two places:</span></span>

-   <span data-ttu-id="3f431-190">Beim Erstellen des „KeepAliveTrigger“-Triggers im Quellcode (siehe Beispiel unten).</span><span class="sxs-lookup"><span data-stu-id="3f431-190">When creating KeepAliveTrigger trigger in the source code (see example below).</span></span>
-   <span data-ttu-id="3f431-191">Im App-Paketmanifest für die Keepalive-Hintergrundaufgabendeklaration.</span><span class="sxs-lookup"><span data-stu-id="3f431-191">In the app package manifest for the keepalive background task declaration.</span></span>

<span data-ttu-id="3f431-192">Im folgenden Beispiel werden eine Netzwerktrigger-Benachrichtigung und ein Keep-Alive-Trigger unter dem &lt;Application&gt;-Element in einem App-Manifest hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3f431-192">The following sample adds a network trigger notification and a keepalive trigger under the &lt;Application&gt; element in an app manifest.</span></span>

```xml
  <Extensions>
    <Extension Category="windows.backgroundTasks"
         Executable="$targetnametoken$.exe"
         EntryPoint="Background.PushNotifyTask">
      <BackgroundTasks>
        <Task Type="controlChannel" />
      </BackgroundTasks>
    </Extension>
    <Extension Category="windows.backgroundTasks"
         Executable="$targetnametoken$.exe"
         EntryPoint="Windows.Networking.Sockets.WebSocketKeepAlive">
      <BackgroundTasks>
        <Task Type="controlChannel" />
      </BackgroundTasks>
    </Extension>
  </Extensions>
```

<span data-ttu-id="3f431-193">Besondere Sorgfalt ist geboten, wenn eine App eine **await**-Anweisung im Kontext einer [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)-Klasse und eines asynchronen Vorgangs für eine [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923)-, [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842)- oder [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Klasse verwendet.</span><span class="sxs-lookup"><span data-stu-id="3f431-193">An app must be extremely careful when using an **await** statement in the context of a [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) and an asynchronous operation on a [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923), [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842), or [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882).</span></span> <span data-ttu-id="3f431-194">Ein **Task&lt;bool&gt;**-Objekt kann verwendet werden, um eine **ControlChannelTrigger**-Klasse für Pushbenachrichtigungen und WebSocket-Keep-Alive-Meldungen in der **StreamWebSocket**-Klasse zu registrieren und die Transportverbindung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="3f431-194">A **Task&lt;bool&gt;** object can be used to register a **ControlChannelTrigger** for push notification and WebSocket keep-alives on the **StreamWebSocket** and connect the transport.</span></span> <span data-ttu-id="3f431-195">Im Rahmen der Registrierung wird der **StreamWebSocket**-Transport als Transport für **ControlChannelTrigger** festgelegt, und es wird ein Lesevorgang bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="3f431-195">As part of the registration, the **StreamWebSocket** transport is set as the transport for the **ControlChannelTrigger** and a read is posted.</span></span> <span data-ttu-id="3f431-196">**Task.Result** blockiert den aktuellen Thread, bis alle Schritte der Aufgabe ausgeführt und Anweisungen im Nachrichtentext zurückgegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="3f431-196">The **Task.Result** will block the current thread until all steps in the task execute and return statements in message body.</span></span> <span data-ttu-id="3f431-197">Die Aufgabe ist erst gelöst, wenn die Methode „true“ oder „false“ zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="3f431-197">The task is not resolved until the method returns either true or false.</span></span> <span data-ttu-id="3f431-198">So wird die vollständige Ausführung der Methode sichergestellt.</span><span class="sxs-lookup"><span data-stu-id="3f431-198">This guarantees that the whole method is executed.</span></span> <span data-ttu-id="3f431-199">Die **Task**-Klasse kann mehrere **await** -Anweisungen erhalten, die durch die **Task**-Klasse geschützt werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-199">The **Task** can contain multiple **await** statements that are protected by the **Task**.</span></span> <span data-ttu-id="3f431-200">Diese Vorgehensweise sollte bei Nutzung eines **StreamWebSocket**- oder **MessageWebSocket**-Transports mit dem **ControlChannelTrigger**-Objekt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-200">This pattern should be used with the **ControlChannelTrigger** object when a **StreamWebSocket** or **MessageWebSocket** is used as the transport.</span></span> <span data-ttu-id="3f431-201">Für Vorgänge, deren Durchführung u. U. längere Zeit in Anspruch nimmt, (z. B. ein typischer asynchroner Lesevorgang) sollte die App das zuvor erläuterte asynchrone Rohmuster verwenden.</span><span class="sxs-lookup"><span data-stu-id="3f431-201">For those operations that may take a long period of time to complete (a typical async read operation, for example), the app should use the raw async pattern discussed previously.</span></span>

<span data-ttu-id="3f431-202">Im folgenden Beispiel wird die [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)-Klasse für Pushbenachrichtigungen registriert. Die Registrierung von WebSocket-Keep-Alive-Meldungen erfolgt über die [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="3f431-202">The following sample registers [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) for push notification and WebSocket keep-alives on the [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923).</span></span>

```csharp
private bool RegisterWithControlChannelTrigger(string serverUri)
{
    // Make sure the objects are created in a system thread
    // Demonstrate the core registration path
    // Wait for the entire operation to complete before returning from this method.
    // The transport setup routine can be triggered by user control, by network state change
    // or by keepalive task
    Task<bool> registerTask = RegisterWithCCTHelper(serverUri);
    return registerTask.Result;
}

async Task<bool> RegisterWithCCTHelper(string serverUri)
{
    bool result = false;
    socket = new StreamWebSocket();

    // Specify the keepalive interval expected by the server for this app
    // in order of minutes.
    const int serverKeepAliveInterval = 30;

    // Specify the channelId string to differentiate this
    // channel instance from any other channel instance.
    // When background task fires, the channel object is provided
    // as context and the channel id can be used to adapt the behavior
    // of the app as required.
    const string channelId = "channelOne";

    // For websockets, the system does the keepalive on behalf of the app
    // But the app still needs to specify this well known keepalive task.
    // This should be done here in the background registration as well
    // as in the package manifest.
    const string WebSocketKeepAliveTask = "Windows.Networking.Sockets.WebSocketKeepAlive";

    // Try creating the controlchanneltrigger if this has not been already
    // created and stored in the property bag.
    ControlChannelTriggerStatus status;

    // Create the ControlChannelTrigger object and request a hardware slot for this app.
    // If the app is not on LockScreen, then the ControlChannelTrigger constructor will
    // fail right away.
    try
    {
        channel = new ControlChannelTrigger(channelId, serverKeepAliveInterval,
                                   ControlChannelTriggerResourceType.RequestHardwareSlot);
    }
    catch (UnauthorizedAccessException exp)
    {
        Diag.DebugPrint("Is the app on lockscreen? " + exp.Message);
        return result;
    }

    Uri serverUriInstance;
    try
    {
        serverUriInstance = new Uri(serverUri);
    }
    catch (Exception exp)
    {
        Diag.DebugPrint("Error creating URI: " + exp.Message);
        return result;
    }

    // Register the apps background task with the trigger for keepalive.
    var keepAliveBuilder = new BackgroundTaskBuilder();
    keepAliveBuilder.Name = "KeepaliveTaskForChannelOne";
    keepAliveBuilder.TaskEntryPoint = WebSocketKeepAliveTask;
    keepAliveBuilder.SetTrigger(channel.KeepAliveTrigger);
    keepAliveBuilder.Register();

    // Register the apps background task with the trigger for push notification task.
    var pushNotifyBuilder = new BackgroundTaskBuilder();
    pushNotifyBuilder.Name = "PushNotificationTaskForChannelOne";
    pushNotifyBuilder.TaskEntryPoint = "Background.PushNotifyTask";
    pushNotifyBuilder.SetTrigger(channel.PushNotificationTrigger);
    pushNotifyBuilder.Register();

    // Tie the transport method to the ControlChannelTrigger object to push enable it.
    // Note that if the transport' s TCP connection is broken at a later point of time,
    // the ControlChannelTrigger object can be reused to plug in a new transport by
    // calling UsingTransport API again.
    try
    {
        channel.UsingTransport(socket);

        // Connect the socket
        //
        // If connect fails or times out it will throw exception.
        // ConnectAsync can also fail if hardware slot was requested
        // but none are available
        await socket.ConnectAsync(serverUriInstance);

        // Call WaitForPushEnabled API to make sure the TCP connection has
        // been established, which will mean that the OS will have allocated
        // any hardware slot for this TCP connection.
        //
        // In this sample, the ControlChannelTrigger object was created by
        // explicitly requesting a hardware slot.
        //
        // On systems that without connected standby, if app requests hardware slot as above,
        // the system will fallback to a software slot automatically.
        //
        // On systems that support connected standby,, if no hardware slot is available, then app
        // can request a software slot by re-creating the ControlChannelTrigger object.
        status = channel.WaitForPushEnabled();
        if (status != ControlChannelTriggerStatus.HardwareSlotAllocated
            && status != ControlChannelTriggerStatus.SoftwareSlotAllocated)
        {
            throw new Exception(string.Format("Neither hardware nor software slot could be allocated. ChannelStatus is {0}", status.ToString()));
        }

        // Store the objects created in the property bag for later use.
        CoreApplication.Properties.Remove(channel.ControlChannelTriggerId);

        var appContext = new AppContext(this, socket, channel, channel.ControlChannelTriggerId);
        ((IDictionary<string, object>)CoreApplication.Properties).Add(channel.ControlChannelTriggerId, appContext);
        result = true;

        // Almost done. Post a read since we are using streamwebsocket
        // to allow push notifications to be received.
        PostSocketRead(MAX_BUFFER_LENGTH);
    }
    catch (Exception exp)
    {
         Diag.DebugPrint("RegisterWithCCTHelper Task failed with: " + exp.Message);

         // Exceptions may be thrown for example if the application has not
         // registered the background task class id for using real time communications
         // broker in the package manifest.
    }
    return result
}
```

<span data-ttu-id="3f431-203">Weitere Informationen zur Verwendung von [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) oder [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) finden Sie im [Beispiel für einen ControlChannelTrigger-StreamSocket](http://go.microsoft.com/fwlink/p/?linkid=251232).</span><span class="sxs-lookup"><span data-stu-id="3f431-203">For more information on using [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) or [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032), see the [ControlChannelTrigger StreamWebSocket sample](http://go.microsoft.com/fwlink/p/?linkid=251232).</span></span>

## <a name="controlchanneltrigger-with-httpclient"></a><span data-ttu-id="3f431-204">ControlChannelTrigger mit HttpClient</span><span class="sxs-lookup"><span data-stu-id="3f431-204">ControlChannelTrigger with HttpClient</span></span>
<span data-ttu-id="3f431-205">Bei Verwendung von [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) müssen einige besondere Punkte berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-205">Some special considerations apply when using [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span> <span data-ttu-id="3f431-206">Bei Verwendung von [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) mit **ControlChannelTrigger** sollten Sie sich an einige transportspezifische Verwendungsmuster und bewährte Methoden halten.</span><span class="sxs-lookup"><span data-stu-id="3f431-206">There are some transport-specific usage patterns and best practices that should be followed when using a [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) with **ControlChannelTrigger**.</span></span> <span data-ttu-id="3f431-207">Diese Aspekte beeinflussen, wie Anforderungen für den Paketempfang in der [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Klasse verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-207">In addition, these considerations affect the way that requests to receive packets on the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) are handled.</span></span>

<span data-ttu-id="3f431-208">**Hinweis:** [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) mit SSL wird derzeit nicht unterstützt unter Verwendung des netzwerktriggerfeatures und [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span><span class="sxs-lookup"><span data-stu-id="3f431-208">**Note**[HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) using SSL is not currently supported using the network trigger feature and [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span>
 
<span data-ttu-id="3f431-209">Beachten Sie bei Verwendung von [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) die folgenden Verwendungsmuster und bewährten Methoden:</span><span class="sxs-lookup"><span data-stu-id="3f431-209">The following usage patterns and best practices should be followed when using [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032):</span></span>

-   <span data-ttu-id="3f431-210">Die App muss möglicherweise verschiedene Eigenschaften und Header für das [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)- oder [HttpClientHandler](http://go.microsoft.com/fwlink/p/?linkid=241638)-Objekt im [System.Net.Http](http://go.microsoft.com/fwlink/p/?linkid=227894)-Namespace festlegen, bevor die Anforderung an den entsprechenden URI gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-210">The app may need to set various properties and headers on the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) or [HttpClientHandler](http://go.microsoft.com/fwlink/p/?linkid=241638) object in the [System.Net.Http](http://go.microsoft.com/fwlink/p/?linkid=227894) namespace before sending the request to the specific URI.</span></span>
-   <span data-ttu-id="3f431-211">Eine App muss ggf. zu Beginn eine Anforderung senden, um den Transport zu testen und richtig einzurichten, bevor der [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Transport zur Verwendung mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-211">An app may need to make need to an initial request to test and setup the transport properly before creating the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) transport to be used with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span> <span data-ttu-id="3f431-212">Nachdem die App festgestellt hat, dass der Transport richtig eingerichtet ist, kann ein [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Objekt als Transportobjekt zur Verwendung mit dem **ControlChannelTrigger**-Objekt konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-212">Once the app determines that the transport can be properly setup, an [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) object can be configured as the transport object used with the **ControlChannelTrigger** object.</span></span> <span data-ttu-id="3f431-213">Dieser Vorgang soll verhindern, dass die über den Transport hergestellte Verbindung in manchen Szenarien abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-213">This process is designed prevent some scenarios from breaking the connection established over the transport.</span></span> <span data-ttu-id="3f431-214">Bei Verwendung von SSL mit einem Zertifikat kann für eine App die Anzeige eines Dialogfelds für die Eingabe einer PIN oder – bei mehreren Zertifikaten – für die Auswahl eines Zertifikats erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="3f431-214">Using SSL with a certificate, an app may require a dialog to be displayed for PIN entry or if there are multiple certificates to choose from.</span></span> <span data-ttu-id="3f431-215">Proxyauthentifizierung und Serverauthentifizierung können ebenfalls erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="3f431-215">Proxy authentication and server authentication may be required.</span></span> <span data-ttu-id="3f431-216">Wenn die Proxy- oder Serverauthentifizierung abläuft, wird die Verbindung möglicherweise geschlossen.</span><span class="sxs-lookup"><span data-stu-id="3f431-216">If the proxy or server authentication expires, the connection may be closed.</span></span> <span data-ttu-id="3f431-217">Eine Möglichkeit, wie eine App mit dem Problem des Authentifizierungsablaufs umgehen kann, besteht in der Verwendung eines Zeitgebers.</span><span class="sxs-lookup"><span data-stu-id="3f431-217">One way an app can deal with these authentication expiration issues is to set a timer.</span></span> <span data-ttu-id="3f431-218">Wenn eine HTTP-Umleitung erforderlich ist, ist nicht sichergestellt, dass die zweite Verbindung verlässlich hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3f431-218">When an HTTP redirect is required, it is not guaranteed that the second connection can be established reliably.</span></span> <span data-ttu-id="3f431-219">Eine anfängliche Testanforderung stellt sicher, dass die App die neueste umgeleitete URL verwenden kann, bevor das [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Objekt als Transport mit dem **ControlChannelTrigger**-Objekt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-219">An initial test request will ensure that the app can use the most up-to-date redirected URL before using the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) object as the transport with the **ControlChannelTrigger** object.</span></span>

<span data-ttu-id="3f431-220">Im Unterschied zu anderen Netzwerktransporten kann das [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Objekt nicht direkt an die [**UsingTransport**](https://msdn.microsoft.com/library/windows/apps/hh701175)-Methode des [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)-Objekts übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-220">Unlike other network transports, the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) object cannot be directly passed into the [**UsingTransport**](https://msdn.microsoft.com/library/windows/apps/hh701175) method of the [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) object.</span></span> <span data-ttu-id="3f431-221">Sie müssen vielmehr ein [HttpRequestMessage](http://go.microsoft.com/fwlink/p/?linkid=259153)-Objekt speziell für die Verwendung mit dem [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Objekt und **ControlChannelTrigger** erstellen.</span><span class="sxs-lookup"><span data-stu-id="3f431-221">Instead, an [HttpRequestMessage](http://go.microsoft.com/fwlink/p/?linkid=259153) object must be specially constructed for use with the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) object and the **ControlChannelTrigger**.</span></span> <span data-ttu-id="3f431-222">Das [HttpRequestMessage](http://go.microsoft.com/fwlink/p/?linkid=259153)-Objekt wird mithilfe der [RtcRequestFactory.Create](http://go.microsoft.com/fwlink/p/?linkid=259154)-Methode erstellt.</span><span class="sxs-lookup"><span data-stu-id="3f431-222">The [HttpRequestMessage](http://go.microsoft.com/fwlink/p/?linkid=259153) object is created using the [RtcRequestFactory.Create](http://go.microsoft.com/fwlink/p/?linkid=259154) method.</span></span> <span data-ttu-id="3f431-223">Das erstellte [HttpRequestMessage](http://go.microsoft.com/fwlink/p/?linkid=259153)-Objekt wird dann an die **UsingTransport**-Methode übergeben.</span><span class="sxs-lookup"><span data-stu-id="3f431-223">The [HttpRequestMessage](http://go.microsoft.com/fwlink/p/?linkid=259153) object that is created is then passed to **UsingTransport** method.</span></span>

<span data-ttu-id="3f431-224">Das folgende Beispiel zeigt, wie Sie ein [HttpRequestMessage](http://go.microsoft.com/fwlink/p/?linkid=259153)-Objekt für die Verwendung mit dem [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Objekt und [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) erstellen können.</span><span class="sxs-lookup"><span data-stu-id="3f431-224">The following sample shows how to construct an [HttpRequestMessage](http://go.microsoft.com/fwlink/p/?linkid=259153) object for use with the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) object and the [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span>

```csharp
using System;
using System.Net;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
using Windows.Networking.Sockets;

public HttpRequestMessage httpRequest;
public HttpClient httpClient;
public HttpRequestMessage httpRequest;
public ControlChannelTrigger channel;
public Uri serverUri;

private void SetupHttpRequestAndSendToHttpServer()
{
    try
    {
        // For HTTP based transports that use the RTC broker, whenever we send next request, we will abort the earlier
        // outstanding http request and start new one.
        // For example in case when http server is taking longer to reply, and keep alive trigger is fired in-between
        // then keep alive task will abort outstanding http request and start a new request which should be finished
        // before next keep alive task is triggered.
        if (httpRequest != null)
        {
            httpRequest.Dispose();
        }

        httpRequest = RtcRequestFactory.Create(HttpMethod.Get, serverUri);

        SendHttpRequest();
    }
        catch (Exception e)
    {
        Diag.DebugPrint("Connect failed with: " + e.ToString());
        throw;
    }
}
```

<span data-ttu-id="3f431-225">Für die Behandlung von Anforderungen zum Senden von HTTP-Anforderungen über [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) zur Initiierung des Antwortempfangs müssen einige besondere Punkte berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-225">Some special considerations affect the way that requests to send HTTP requests on the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) to initiate receiving a response are handled.</span></span> <span data-ttu-id="3f431-226">Insbesondere muss die App bei Verwendung von [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) Sendevorgänge mithilfe einer Aufgabe statt des **await**-Modells behandeln.</span><span class="sxs-lookup"><span data-stu-id="3f431-226">In particular, when using a [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) with the [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032), your app must use a Task for handling sends instead of the **await** model.</span></span>

<span data-ttu-id="3f431-227">Bei Verwendung von [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) erfolgt keine Synchronisierung der [**IBackgroundTask.Run**](https://msdn.microsoft.com/library/windows/apps/br224811)-Methode der Hintergrundaufgabe für [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) mit der Rückgabe des Empfangsabschlussrückrufs.</span><span class="sxs-lookup"><span data-stu-id="3f431-227">Using [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637), there is no synchronization with the [**IBackgroundTask.Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method on the background task for the [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) with the return of the receive completion callback.</span></span> <span data-ttu-id="3f431-228">Die App kann daher nur das „HttpResponseMessage“-Blockierverfahren für die **Run**-Methode verwenden und auf den Empfang der vollständigen Antwort warten.</span><span class="sxs-lookup"><span data-stu-id="3f431-228">For this reason, the app can only use the blocking HttpResponseMessage technique in the **Run** method and wait until the whole response is received.</span></span>

<span data-ttu-id="3f431-229">Die Verwendung von [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) unterscheidet sich deutlich von den [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-, [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842)- oder [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923)-Transporten.</span><span class="sxs-lookup"><span data-stu-id="3f431-229">Using [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) is noticeably different from the [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882), [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) or [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) transports .</span></span> <span data-ttu-id="3f431-230">Der [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Empfangsrückruf wird ab dem [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637)-Code mithilfe einer Aufgabe an die App übermittelt.</span><span class="sxs-lookup"><span data-stu-id="3f431-230">The [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) receive callback is delivered via a Task to the app since the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) code.</span></span> <span data-ttu-id="3f431-231">Dies impliziert, dass die **ControlChannelTrigger**-Pushbenachrichtigungsaufgabe ausgelöst wird, sobald die Daten oder der Fehler an die App übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-231">This means that the **ControlChannelTrigger** push notification task will fire as soon as the data or error is dispatched to the app.</span></span> <span data-ttu-id="3f431-232">Im nachfolgenden Beispiel speichert der Code die von der [HttpClient.SendAsync](http://go.microsoft.com/fwlink/p/?linkid=241637)-Methode zurückgegebene „responseTask“ im globalen Speicher. Die Pushbenachrichtigungsaufgabe übernimmt diese dann für die Inline-Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="3f431-232">In the sample below, the code stores the responseTask returned by [HttpClient.SendAsync](http://go.microsoft.com/fwlink/p/?linkid=241637) method into global storage that the push notify task will pick up and process inline.</span></span>

<span data-ttu-id="3f431-233">Das folgende Beispiel zeigt, wie Sie Sendeanforderungen für [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) bei Verwendung mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) behandeln.</span><span class="sxs-lookup"><span data-stu-id="3f431-233">The following sample shows how to handle send requests on the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) when used with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span>

```csharp
using System;
using System.Net;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
using Windows.Networking.Sockets;

private void SendHttpRequest()
{
    if (httpRequest == null)
    {
        throw new Exception("HttpRequest object is null");
    }

    // Tie the transport method to the controlchanneltrigger object to push enable it.
    // Note that if the transport' s TCP connection is broken at a later point of time,
    // the controlchanneltrigger object can be reused to plugin a new transport by
    // calling UsingTransport API again.
    channel.UsingTransport(httpRequest);

    // Call the SendAsync function to kick start the TCP connection establishment
    // process for this http request.
    Task<HttpResponseMessage> httpResponseTask = httpClient.SendAsync(httpRequest);

    // Call WaitForPushEnabled API to make sure the TCP connection has been established,
    // which will mean that the OS will have allocated any hardware slot for this TCP connection.
    ControlChannelTriggerStatus status = channel.WaitForPushEnabled();
    Diag.DebugPrint("WaitForPushEnabled() completed with status: " + status);
    if (status != ControlChannelTriggerStatus.HardwareSlotAllocated
        && status != ControlChannelTriggerStatus.SoftwareSlotAllocated)
    {
        throw new Exception("Hardware/Software slot not allocated");
    }

    // The HttpClient receive callback is delivered via a Task to the app.
    // The notification task will fire as soon as the data or error is dispatched
    // Enqueue the responseTask returned by httpClient.sendAsync
    // into a queue that the push notify task will pick up and process inline.
    AppContext.messageQueue.Enqueue(httpResponseTask);
}
```

<span data-ttu-id="3f431-234">Das folgende Beispiel zeigt, wie Sie empfangene Antworten für [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) bei Verwendung mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) lesen.</span><span class="sxs-lookup"><span data-stu-id="3f431-234">The following sample shows how to read responses received on the [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) when used with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span>

```csharp
using System.Net;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;

public string ReadResponse(Task<HttpResponseMessage> httpResponseTask)
{
    string message = null;
    try
    {
        if (httpResponseTask.IsCanceled || httpResponseTask.IsFaulted)
        {
            Diag.DebugPrint("Task is cancelled or has failed");
            return message;
        }
        // We' ll wait until we got the whole response.
        // This is the only supported scenario for HttpClient for ControlChannelTrigger.
        HttpResponseMessage httpResponse = httpResponseTask.Result;
        if (httpResponse == null || httpResponse.Content == null)
        {
            Diag.DebugPrint("Cannot read from httpresponse, as either httpResponse or its content is null. try to reset connection.");
        }
        else
        {
            // This is likely being processed in the context of a background task and so
            // synchronously read the Content' s results inline so that the Toast can be shown.
            // before we exit the Run method.
            message = httpResponse.Content.ReadAsStringAsync().Result;
        }
    }
    catch (Exception exp)
    {
        Diag.DebugPrint("Failed to read from httpresponse with error:  " + exp.ToString());
    }
    return message;
}
```

<span data-ttu-id="3f431-235">Weitere Informationen zur Verwendung von [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) finden Sie im [Beispiel für einen ControlChannelTrigger-HttpClient](http://go.microsoft.com/fwlink/p/?linkid=258323).</span><span class="sxs-lookup"><span data-stu-id="3f431-235">For more information on using [HttpClient](http://go.microsoft.com/fwlink/p/?linkid=241637) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032), see the [ControlChannelTrigger HttpClient sample](http://go.microsoft.com/fwlink/p/?linkid=258323).</span></span>

## <a name="controlchanneltrigger-with-ixmlhttprequest2"></a><span data-ttu-id="3f431-236">ControlChannelTrigger mit IXMLHttpRequest2</span><span class="sxs-lookup"><span data-stu-id="3f431-236">ControlChannelTrigger with IXMLHttpRequest2</span></span>
<span data-ttu-id="3f431-237">Bei Verwendung von [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) müssen einige besondere Punkte berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-237">Some special considerations apply when using [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span> <span data-ttu-id="3f431-238">Bei Verwendung von **IXMLHTTPRequest2** mit **ControlChannelTrigger** sollten Sie sich an einige transportspezifische Verwendungsmuster und bewährte Methoden halten.</span><span class="sxs-lookup"><span data-stu-id="3f431-238">There are some transport-specific usage patterns and best practices that should be followed when using a **IXMLHTTPRequest2** with **ControlChannelTrigger**.</span></span> <span data-ttu-id="3f431-239">Die Verwendung von **ControlChannelTrigger** wirkt sich nicht auf die Behandlung von Anforderungen zum Senden oder Empfangen von HTTP-Anforderungen über **IXMLHTTPRequest2** aus.</span><span class="sxs-lookup"><span data-stu-id="3f431-239">Using **ControlChannelTrigger** does not affect the way that requests to send or receive HTTP requests on the **IXMLHTTPRequest2** are handled.</span></span>

<span data-ttu-id="3f431-240">Verwendungsmuster und bewährte Methoden für die Verwendung von [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)</span><span class="sxs-lookup"><span data-stu-id="3f431-240">Usage patterns and best practices when using [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)</span></span>

-   <span data-ttu-id="3f431-241">Ein als Transport verwendetes [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151)-Objekt ist für nur eine Anforderung/Antwort gültig.</span><span class="sxs-lookup"><span data-stu-id="3f431-241">An [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151) object when used as the transport has a lifetime of only one request/response.</span></span> <span data-ttu-id="3f431-242">Bei Verwendung mit dem [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032)-Objekt sollte das **ControlChannelTrigger**-Objekt einmalig erstellt und eingerichtet werden. Rufen Sie anschließend jedes Mal die [**UsingTransport**](https://msdn.microsoft.com/library/windows/apps/hh701175)-Methode auf, und ordnen Sie jedes Mal ein neues **IXMLHTTPRequest2**-Objekt zu.</span><span class="sxs-lookup"><span data-stu-id="3f431-242">When used with the [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) object, it is convenient to create and set up the **ControlChannelTrigger** object once and then call the [**UsingTransport**](https://msdn.microsoft.com/library/windows/apps/hh701175) method repeatedly, each time associating a new **IXMLHTTPRequest2** object.</span></span> <span data-ttu-id="3f431-243">Die App sollte vor der Bereitstellung eines neuen **IXMLHTTPRequest2**-Objekts das vorherige **IXMLHTTPRequest2**-Objekt löschen, damit sie die zugeordneten Ressourcenbeschränkungen nicht überschreitet.</span><span class="sxs-lookup"><span data-stu-id="3f431-243">An app should delete the previous **IXMLHTTPRequest2** object before supplying a new **IXMLHTTPRequest2** object to ensure that the app does not exceed the allocated resource limits.</span></span>
-   <span data-ttu-id="3f431-244">Die App muss ggf. die Methoden [**SetProperty**](https://msdn.microsoft.com/library/windows/desktop/hh831167) und [**SetRequestHeader**](https://msdn.microsoft.com/library/windows/desktop/hh831168) aufrufen, um den HTTP-Transport vor dem Aufruf der [**Send**](https://msdn.microsoft.com/library/windows/desktop/hh831164)-Methode einzurichten.</span><span class="sxs-lookup"><span data-stu-id="3f431-244">The app may need to call the [**SetProperty**](https://msdn.microsoft.com/library/windows/desktop/hh831167) and [**SetRequestHeader**](https://msdn.microsoft.com/library/windows/desktop/hh831168) methods to set up the HTTP transport before calling [**Send**](https://msdn.microsoft.com/library/windows/desktop/hh831164) method.</span></span>
-   <span data-ttu-id="3f431-245">Die App muss zu Beginn gegebenenfalls eine [**Send**](https://msdn.microsoft.com/library/windows/desktop/hh831164)-Anforderung senden, um den Transport zu testen und richtig einzurichten, bevor der Transport zur Verwendung mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-245">An app may need to make need to an initial [**Send**](https://msdn.microsoft.com/library/windows/desktop/hh831164) request to test and setup the transport properly before creating the transport to be used with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span> <span data-ttu-id="3f431-246">Nachdem die App festgestellt hat, dass der Transport richtig eingerichtet ist, kann das [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151)-Objekt als Transportobjekt zur Verwendung mit **ControlChannelTrigger** konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="3f431-246">Once the app determines that the transport is properly setup, the [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151) object can be configured as the transport object used with the **ControlChannelTrigger**.</span></span> <span data-ttu-id="3f431-247">Dieser Vorgang soll verhindern, dass die über den Transport hergestellte Verbindung in manchen Szenarien abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-247">This process is designed prevent some scenarios from breaking the connection established over the transport.</span></span> <span data-ttu-id="3f431-248">Bei Verwendung von SSL mit einem Zertifikat kann für eine App die Anzeige eines Dialogfelds für die Eingabe einer PIN oder – bei mehreren Zertifikaten – für die Auswahl eines Zertifikats erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="3f431-248">Using SSL with a certificate, an app may require a dialog to be displayed for PIN entry or if there are multiple certificates to choose from.</span></span> <span data-ttu-id="3f431-249">Proxyauthentifizierung und Serverauthentifizierung können ebenfalls erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="3f431-249">Proxy authentication and server authentication may be required.</span></span> <span data-ttu-id="3f431-250">Wenn die Proxy- oder Serverauthentifizierung abläuft, wird die Verbindung möglicherweise geschlossen.</span><span class="sxs-lookup"><span data-stu-id="3f431-250">If the proxy or server authentication expires, the connection may be closed.</span></span> <span data-ttu-id="3f431-251">Eine Möglichkeit, wie eine App mit dem Problem des Authentifizierungsablaufs umgehen kann, besteht in der Verwendung eines Zeitgebers.</span><span class="sxs-lookup"><span data-stu-id="3f431-251">One way an app can deal with these authentication expiration issues is to set a timer.</span></span> <span data-ttu-id="3f431-252">Wenn eine HTTP-Umleitung erforderlich ist, ist nicht sichergestellt, dass die zweite Verbindung verlässlich hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3f431-252">When an HTTP redirect is required, it is not guaranteed that the second connection can be established reliably.</span></span> <span data-ttu-id="3f431-253">Eine anfängliche Testanforderung stellt sicher, dass die App die neueste umgeleitete URL verwenden kann, bevor das **IXMLHTTPRequest2**-Objekt als Transport mit dem **ControlChannelTrigger**-Objekt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3f431-253">An initial test request will ensure that the app can use the most up-to-date redirected URL before using the **IXMLHTTPRequest2** object as the transport with the **ControlChannelTrigger** object.</span></span>

<span data-ttu-id="3f431-254">Weitere Informationen zur Verwendung von [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151) mit [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) finden Sie im [Beispiel für ControlChannelTrigger mit IXMLHTTPRequest2](http://go.microsoft.com/fwlink/p/?linkid=258538).</span><span class="sxs-lookup"><span data-stu-id="3f431-254">For more information on using [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151) with [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032), see the [ControlChannelTrigger with IXMLHTTPRequest2 sample](http://go.microsoft.com/fwlink/p/?linkid=258538).</span></span>

## <a name="important-apis"></a><span data-ttu-id="3f431-255">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="3f431-255">Important APIs</span></span>
* [<span data-ttu-id="3f431-256">SocketActivityTrigger</span><span class="sxs-lookup"><span data-stu-id="3f431-256">SocketActivityTrigger</span></span>](/uwp/api/Windows.ApplicationModel.Background.SocketActivityTrigger)
* [<span data-ttu-id="3f431-257">ControlChannelTrigger</span><span class="sxs-lookup"><span data-stu-id="3f431-257">ControlChannelTrigger</span></span>](/uwp/api/Windows.Networking.Sockets.ControlChannelTrigger)
