---
author: PatrickFarley
title: Verbinden von Geräten über Remotesitzungen
description: Ermöglichen Sie die gemeinsame Nutzung auf verbundenen Geräten, indem Sie diese in einer Remotesitzung vereinen.
ms.assetid: 1c8dba9f-c933-4e85-829e-13ad784dd3e2
ms.author: pafarley
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, verbundenen Geräten, remote-Systemen, "ROME" Projekt "ROME"
ms.localizationpriority: medium
ms.openlocfilehash: 8e5226b23a454bf48add22d590a3ff247c629e4f
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "4148739"
---
# <a name="connect-devices-through-remote-sessions"></a><span data-ttu-id="1baa3-104">Verbinden von Geräten über Remotesitzungen</span><span class="sxs-lookup"><span data-stu-id="1baa3-104">Connect devices through remote sessions</span></span>

<span data-ttu-id="1baa3-105">Die Remotesitzungsfunktion ermöglicht einer App, eine Verbindung mit anderen Geräten über eine Sitzung herzustellen, entweder für explizite App-Nachrichten oder für im Broker gespeicherte ausgetauschte Daten, die vom System verwaltet werden, wie z.B. der **[SpatialEntityStore](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialentitystore)** für ein eine gemeinsame holografische Nutzung von Windows Holographic-Geräten.</span><span class="sxs-lookup"><span data-stu-id="1baa3-105">The Remote Sessions feature allows an app to connect to other devices through a session, either for explicit app messaging or for brokered exchange of system-managed data, such as the **[SpatialEntityStore](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialentitystore)** for holographic sharing between Windows Holographic devices.</span></span>

<span data-ttu-id="1baa3-106">Remotesitzungen können von jedem Windows-Gerät erstellt werden, und jedes Windows-Gerät kann einen Beitritt anfordern (obwohl Sitzungen ausschließlich per Einladung aufgerufen werden können), einschließlich Geräte, auf denen andere Benutzer angemeldet sind.</span><span class="sxs-lookup"><span data-stu-id="1baa3-106">Remote sessions can be created by any Windows device, and any Windows device can request to join (although sessions can have invite-only visibility), including devices signed in by other users.</span></span> <span data-ttu-id="1baa3-107">Dieses Handbuch enthält einen grundlegenden Beispielcode für alle wichtigen Szenarien, die Remotesitzungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="1baa3-107">This guide provides basic sample code for all of the major scenarios that make use of remote sessions.</span></span> <span data-ttu-id="1baa3-108">Dieser Code kann in ein vorhandenes App-Projekt integriert und nach Bedarf geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1baa3-108">This code can be incorporated into an existing app project and modified as necessary.</span></span> <span data-ttu-id="1baa3-109">Informationen über eine End-to-End-Implementierung finden Sie unter [Beispiel-App für ein Quizspiel](https://github.com/microsoft/Windows-appsample-remote-system-sessions)).</span><span class="sxs-lookup"><span data-stu-id="1baa3-109">For an end-to-end implementation, see the [Quiz Game sample app](https://github.com/microsoft/Windows-appsample-remote-system-sessions)).</span></span>

## <a name="preliminary-setup"></a><span data-ttu-id="1baa3-110">Vorläufige Einrichtung</span><span class="sxs-lookup"><span data-stu-id="1baa3-110">Preliminary setup</span></span>

### <a name="add-the-remotesystem-capability"></a><span data-ttu-id="1baa3-111">Hinzufügen der Funktionen „remoteSystem“</span><span class="sxs-lookup"><span data-stu-id="1baa3-111">Add the remoteSystem capability</span></span>

<span data-ttu-id="1baa3-112">Damit Ihre App eine App auf einem Remotegerät starten kann, müssen Sie Ihrem App-Paketmanifest die Funktion `remoteSystem` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1baa3-112">In order for your app to launch an app on a remote device, you must add the `remoteSystem` capability to your app package manifest.</span></span> <span data-ttu-id="1baa3-113">Sie können den Paketmanifest-Designer verwenden, um die Funktion hinzuzufügen, indem Sie auf der Registerkarte **Funktionen** die Option **Remotesystem** auswählen. Sie können auch der Datei _Package.appxmanifest_ Ihres Projekts die folgende Zeile manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1baa3-113">You can use the package manifest designer to add it by selecting **Remote System** on the **Capabilities** tab, or you can manually add the following line to your project's _Package.appxmanifest_ file.</span></span>

``` xml
<Capabilities>
   <uap3:Capability Name="remoteSystem"/>
</Capabilities>
```

### <a name="enable-cross-user-discovering-on-the-device"></a><span data-ttu-id="1baa3-114">Aktivieren der benutzerübergreifenden Ermittlung auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="1baa3-114">Enable cross-user discovering on the device</span></span>
<span data-ttu-id="1baa3-115">Remotesitzungen ermöglichen das Herstellen einer Verbindung von mehreren verschiedenen Benutzern, daher muss auf den betreffenden Geräten die benutzerübergreifende Freigabe aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="1baa3-115">Remote Sessions is geared toward connecting multiple different users, so the devices involved will need to have Cross-User Sharing enabled.</span></span> <span data-ttu-id="1baa3-116">Dies ist eine Systemeinstellung, die über eine statische Methode in der **RemoteSystem**-Klasse abgefragt werden kann:</span><span class="sxs-lookup"><span data-stu-id="1baa3-116">This is a system setting that can be queried with a static method in the **RemoteSystem** class:</span></span>

```csharp
if (!RemoteSystem.IsAuthorizationKindEnabled(RemoteSystemAuthorizationKind.Anonymous)) {
    // The system is not authorized to connect to cross-user devices. 
    // Inform the user that they can discover more devices if they
    // update the setting to "Everyone nearby".
}
```

<span data-ttu-id="1baa3-117">Um diese Einstellung zu ändern, muss der Benutzer die Anwendung **Einstellungen** öffnen.</span><span class="sxs-lookup"><span data-stu-id="1baa3-117">To change this setting, the user must open the **Settings** app.</span></span> <span data-ttu-id="1baa3-118">Im Menü **System** > **Geteilte Umgebungen** > **Auf Geräten freigeben** befindet sich ein Dropdown-Feld, in dem der Benutzer angeben kann, mit welchen Geräten sein System teilen kann.</span><span class="sxs-lookup"><span data-stu-id="1baa3-118">In the **System** > **Shared experiences** > **Share across devices** menu, there is a drop-down box where the user can specify which devices their system can share with.</span></span>

![Einstellungsseite geteilter Umgebungen](images/shared-experiences-settings.png)

### <a name="include-the-necessary-namespaces"></a><span data-ttu-id="1baa3-120">Angeben des erforderlichen Namespace</span><span class="sxs-lookup"><span data-stu-id="1baa3-120">Include the necessary namespaces</span></span>
<span data-ttu-id="1baa3-121">Um alle Codeausschnitte in diesem Handbuch zu verwenden, benötigen Sie die folgenden `using`-Anweisungen in Ihrer Dateien.</span><span class="sxs-lookup"><span data-stu-id="1baa3-121">In order to use all of the code snippets in this guide, you will need the following `using` statements in your class file(s).</span></span>

```csharp
using System.Runtime.Serialization.Json;
using Windows.Foundation.Collections;
using Windows.System.RemoteSystems;
```

## <a name="create-a-remote-session"></a><span data-ttu-id="1baa3-122">Erstellen einer Remotesitzung</span><span class="sxs-lookup"><span data-stu-id="1baa3-122">Create a remote session</span></span>

<span data-ttu-id="1baa3-123">Um eine Remotesitzungsinstanz zu erstellen, müssen Sie mit einem **[RemoteSystemSessionController](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessioncontroller)**-Objekt beginnen.</span><span class="sxs-lookup"><span data-stu-id="1baa3-123">To create a remote session instance, you must start with a **[RemoteSystemSessionController](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessioncontroller)** object.</span></span> <span data-ttu-id="1baa3-124">Verwenden Sie das folgende Framework, um eine neue Sitzung zu erstellen und Teilnehmeranfragen von anderen Geräten zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="1baa3-124">Use the following framework to create a new session and handle join requests from other devices.</span></span>

```csharp
public async void CreateSession() {
    
    // create a session controller
    RemoteSystemSessionController manager = new RemoteSystemSessionController("Bob’s Minecraft game");
    
    // register the following code to handle the JoinRequested event
    manager.JoinRequested += async (sender, args) => {
        // Get the deferral
        var deferral = args.GetDeferral();
        
        // display the participant (args.JoinRequest.Participant) on UI, giving the 
        // user an opportunity to respond
        // ...
        
        // If the user chooses "accept", accept this remote system as a participant
        args.JoinRequest.Accept();
    };
    
    // create and start the session
    RemoteSystemSessionCreationResult createResult = await manager.CreateSessionAsync();
    
    // handle the creation result
    if (createResult.Status == RemoteSystemSessionCreationStatus.Success) {
        // creation was successful, get a reference to the session
        RemoteSystemSession currentSession = createResult.Session;
        
        // optionally subscribe to the disconnection event
        currentSession.Disconnected += async (sender, args) => {
            // update the UI, using args.Reason
            //...
        };
    
        // Use session (see later section)
        //...
    
    } else if (createResult.Status == RemoteSystemSessionCreationStatus.SessionLimitsExceeded) {
        // creation failed. Optionally update UI to indicate that there are too many sessions in progress
    } else {
        // creation failed for an unknown reason. Optionally update UI
    }
}
```

### <a name="make-a-remote-session-invite-only"></a><span data-ttu-id="1baa3-125">Erstellen einer ausschließlich per Einladung aufgerufenen Remotesitzung</span><span class="sxs-lookup"><span data-stu-id="1baa3-125">Make a remote session invite-only</span></span>

<span data-ttu-id="1baa3-126">Wenn Sie verhindern möchten, dass Ihre Remotesitzung öffentlich sichtbar ist, können Sie diese ausschließlich per Einladung anmelden.</span><span class="sxs-lookup"><span data-stu-id="1baa3-126">If you wish to keep your remote session from being publicly discoverable, you can make it invite-only.</span></span> <span data-ttu-id="1baa3-127">Nur die Geräte, die eine Einladung erhalten, können Beitrittsanfragen senden.</span><span class="sxs-lookup"><span data-stu-id="1baa3-127">Only the devices that receive an invitation will be able to send join requests.</span></span> 

<span data-ttu-id="1baa3-128">Das Verfahren ist größtenteils identisch wie oben, aber beim Erstellen der **[RemoteSystemSessionController](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessioncontroller)**-Instanz übergeben Sie ein konfiguriertes **[RemoteSystemSessionOptions](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.RemoteSystemSessionOptions)**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="1baa3-128">The procedure is mostly the same as above, but when constructing the **[RemoteSystemSessionController](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessioncontroller)** instance, you will pass in a configured **[RemoteSystemSessionOptions](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.RemoteSystemSessionOptions)** object.</span></span>

```csharp
// define the session options with the invite-only designation
RemoteSystemSessionOptions sessionOptions = new RemoteSystemSessionOptions();
sessionOptions.IsInviteOnly = true;

// create the session controller
RemoteSystemSessionController manager = new RemoteSystemSessionController("Bob's Minecraft game", sessionOptions);

//...
```

<span data-ttu-id="1baa3-129">Um eine Einladung zu senden, müssen Sie einen Verweis auf das Empfänger-Remotesystem (durch die normale Remotesystemermittlung) haben.</span><span class="sxs-lookup"><span data-stu-id="1baa3-129">To send an invitation, you must have a reference to the receiving remote system (acquired through normal remote system discovery).</span></span> <span data-ttu-id="1baa3-130">Übergeben Sie einfach diesen Verweis in die **[SendInvitationAsync](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsession.sendinvitationasync)**-Methode des Sitzungsobjekts.</span><span class="sxs-lookup"><span data-stu-id="1baa3-130">Simply pass this reference into the session object's **[SendInvitationAsync](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsession.sendinvitationasync)** method.</span></span> <span data-ttu-id="1baa3-131">Alle Teilnehmer in einer Sitzung verfügen über einen Verweis auf die Remotesitzung (siehe nächster Abschnitt), damit alle Teilnehmer eine Einladung senden können.</span><span class="sxs-lookup"><span data-stu-id="1baa3-131">All of the participants in a session have a reference to the remote session (see next section), so any participant can send an invitation.</span></span>

```csharp
// "currentSession" is a reference to a RemoteSystemSession.
// "guestSystem" is a previously discovered RemoteSystem instance
currentSession.SendInvitationAsync(guestSystem); 
```

## <a name="discover-and-join-a-remote-session"></a><span data-ttu-id="1baa3-132">Ermitteln und Beitreten einer Remotesitzung</span><span class="sxs-lookup"><span data-stu-id="1baa3-132">Discover and join a remote session</span></span>

<span data-ttu-id="1baa3-133">Der Prozess der Ermittlung von Remotesitzungen wird von der **[RemoteSystemSessionWatcher](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessionwatcher)**-Klasse behandelt und ähnelt der Ermittlung einzelner Remote-Systeme.</span><span class="sxs-lookup"><span data-stu-id="1baa3-133">The process of discovering remote sessions is handled by the **[RemoteSystemSessionWatcher](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessionwatcher)** class and is similar to discovering individual remote systems.</span></span>

```csharp
public void DiscoverSessions() {
    
    // create a watcher for remote system sessions
    RemoteSystemSessionWatcher sessionWatcher = RemoteSystemSession.CreateWatcher();
    
    // register a handler for the "added" event
    sessionWatcher.Added += async (sender, args) => {
        
        // get a reference to the info about the discovered session
        RemoteSystemSessionInfo sessionInfo = args.SessionInfo;
        
        // Optionally update the UI with the sessionInfo.DisplayName and 
        // sessionInfo.ControllerDisplayName strings. 
        // Save a reference to this RemoteSystemSessionInfo to use when the
        // user selects this session from the UI
        //...
    };
    
    // Begin watching
    sessionWatcher.Start();
}
```

<span data-ttu-id="1baa3-134">Wenn eine **[RemoteSystemSessionInfo](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessioninfo)**-Instanz abgerufen wurde, kann damit eine Beitrittsanfrage an das Gerät ausgestellt werden, das die entsprechende Sitzung steuert.</span><span class="sxs-lookup"><span data-stu-id="1baa3-134">When a **[RemoteSystemSessionInfo](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessioninfo)** instance is obtained, it can be used to issue a join request to the device that controls the corresponding session.</span></span> <span data-ttu-id="1baa3-135">Eine akzeptierte Beitrittsanfrage gibt asynchron ein **[RemoteSystemSessionJoinResult](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessionjoinresult)**-Objekt zurück, das einen Verweis auf die verbundene Sitzung enthält.</span><span class="sxs-lookup"><span data-stu-id="1baa3-135">An accepted join request will asynchronously return a **[RemoteSystemSessionJoinResult](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessionjoinresult)** object that contains a reference to the joined session.</span></span>

```csharp
public async void JoinSession(RemoteSystemSessionInfo sessionInfo) {

    // issue a join request and wait for result.
    RemoteSystemSessionJoinResult joinResult = await sessionInfo.JoinAsync();
    if (joinResult.Status == RemoteSystemSessionJoinStatus.Success) {
        // Join request was approved

        // RemoteSystemSession instance "currentSession" was declared at class level.
        // Assign the value obtained from the join result.
        currentSession = joinResult.Session;
        
        // note connection and register to handle disconnection event
        bool isConnected = true;
        currentSession.Disconnected += async (sender, args) => {
            isConnected = false;

            // update the UI with args.Reason value
        };
        
        if (isConnected) {
            // optionally use the session here (see next section)
            //...
        }
    } else {
        // Join was unsuccessful.
        // Update the UI, using joinResult.Status value to show cause of failure.
    }
}
```

<span data-ttu-id="1baa3-136">Ein Gerät kann mehreren Sitzungen gleichzeitig angehören.</span><span class="sxs-lookup"><span data-stu-id="1baa3-136">A device can be joined to multiple sessions at the same time.</span></span> <span data-ttu-id="1baa3-137">Aus diesem Grund ist es wünschenswert, die Beitrittsfunktion von der tatsächlichen Interaktion mit jeder Sitzung zu trennen.</span><span class="sxs-lookup"><span data-stu-id="1baa3-137">For this reason, it may be desirable to separate the joining functionality from the actual interaction with each session.</span></span> <span data-ttu-id="1baa3-138">So lange ein Verweis auf die **[RemoteSystemSession](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsession)**-Instanz in der App besteht, kann die Kommunikation über diese Sitzung versucht werden.</span><span class="sxs-lookup"><span data-stu-id="1baa3-138">As long as a reference to the **[RemoteSystemSession](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsession)** instance is maintained in the app, communication can be attempted over that session.</span></span>

## <a name="share-messages-and-data-through-a-remote-session"></a><span data-ttu-id="1baa3-139">Teilen von Nachrichten und Daten über eine Remotesitzung</span><span class="sxs-lookup"><span data-stu-id="1baa3-139">Share messages and data through a remote session</span></span>

### <a name="receive-messages"></a><span data-ttu-id="1baa3-140">Empfangen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="1baa3-140">Receive messages</span></span>

<span data-ttu-id="1baa3-141">Sie können Nachrichten und Daten mit anderen teilnehmenden Geräten in der Sitzung mithilfe einer **[RemoteSystemSessionMessageChannel](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessionmessagechannel)**-Instanz austauschen, den einzigen Kommunikationskanal für die ganze Sitzung.</span><span class="sxs-lookup"><span data-stu-id="1baa3-141">You can exchange messages and data with other participant devices in the session by using a **[RemoteSystemSessionMessageChannel](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessionmessagechannel)** instance, which represents a single session-wide communication channel.</span></span> <span data-ttu-id="1baa3-142">Sobald dieser initialisiert wird, wartet er auf eingehende Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="1baa3-142">As soon as it's initialized, it begins listening for incoming messages.</span></span>

>[!NOTE]
><span data-ttu-id="1baa3-143">Nachrichten müssen beim Senden und Empfangen aus Bytearrays serialisiert und deserialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="1baa3-143">Messages must be serialized and deserialized from byte arrays upon sending and receiving.</span></span> <span data-ttu-id="1baa3-144">Diese Funktion ist in den folgenden Beispielen enthalten, sie kann jedoch separat für eine bessere Code-Modularität implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="1baa3-144">This functionality is included in the following examples, but it can be implemented separately for better code modularity.</span></span> <span data-ttu-id="1baa3-145">Ein Beispiel dafür finden Sie in der [Beispiel-App](https://github.com/microsoft/Windows-appsample-remote-system-sessions).</span><span class="sxs-lookup"><span data-stu-id="1baa3-145">See the [sample app](https://github.com/microsoft/Windows-appsample-remote-system-sessions)) for an example of this.</span></span>

```csharp
public async void StartReceivingMessages() {
    
    // Initialize. The channel name must be known by all participant devices 
    // that will communicate over it.
    RemoteSystemSessionMessageChannel messageChannel = new RemoteSystemSessionMessageChannel(currentSession, 
        "Everyone in Bob's Minecraft game", 
        RemoteSystemSessionMessageChannelReliability.Reliable);
    
    // write the handler for incoming messages on this channel
    messageChannel.ValueSetReceived += async (sender, args) => {
        
        // Update UI: a message was received from the participant args.Sender
        
        // Deserialize the message 
        // (this app must know what key to use and what object type the value is expected to be)
        ValueSet receivedMessage = args.Message;
        object rawData = receivedMessage["appKey"]);
        object value = new ExpectedType(); // this must be whatever type is expected

        using (var stream = new MemoryStream((byte[])rawData)) {
            value = new DataContractJsonSerializer(value.GetType()).ReadObject(stream);
        }
        
        // do something with the "value" object
        //...
    };
}
```

### <a name="send-messages"></a><span data-ttu-id="1baa3-146">Senden von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="1baa3-146">Send messages</span></span>

<span data-ttu-id="1baa3-147">Wenn der Kanal eingerichtet ist, ist das Senden einer Nachricht an alle Sitzungsteilnehmer einfach.</span><span class="sxs-lookup"><span data-stu-id="1baa3-147">When the channel is established, sending a message to all of the session participants is straightforward.</span></span>

```csharp
public async void SendMessageToAllParticipantsAsync(RemoteSystemSessionMessageChannel messageChannel, object value){

    // define a ValueSet message to send
    ValueSet message = new ValueSet();
    
    // serialize the "value" object to send
    using (var stream = new MemoryStream()){
        new DataContractJsonSerializer(value.GetType()).WriteObject(stream, value);
        byte[] rawData = stream.ToArray();
            message["appKey"] = rawData;
    }
    
    // Send message to all participants. Ordering is not guaranteed.
    await messageChannel.BroadcastValueSetAsync(message);
}
```

<span data-ttu-id="1baa3-148">Um eine Nachricht nur an bestimmte Teilnehmer zu senden, müssen Sie zunächst einen Ermittlungsprozess starten, um Verweise auf die Remotesysteme zu erhalten, die an der Sitzung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="1baa3-148">In order to send a message to only certain participant(s), you must first initiate a discovery process to acquire references to the remote systems participating in the session.</span></span> <span data-ttu-id="1baa3-149">Dies ist vergleichbar mit dem Prozess der Ermittlung von Remotesystemen außerhalb einer Sitzung.</span><span class="sxs-lookup"><span data-stu-id="1baa3-149">This is similar to the process of discovering remote systems outside of a session.</span></span> <span data-ttu-id="1baa3-150">Verwenden Sie die **[RemoteSystemSessionParticipantWatcher](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessionparticipantwatcher)**-Instanz, um das Gerät des Teilnehmers an einer Sitzung zu finden</span><span class="sxs-lookup"><span data-stu-id="1baa3-150">Use a **[RemoteSystemSessionParticipantWatcher](https://docs.microsoft.com/uwp/api/windows.system.remotesystems.remotesystemsessionparticipantwatcher)** instance to find a session's participant devices.</span></span>

```csharp
public void WatchForParticipants() {
    // "currentSession" is a reference to a RemoteSystemSession.
    RemoteSystemSessionParticipantWatcher watcher = currentSession.CreateParticipantWatcher();

    watcher.Added += (sender, participant) => {
        // save a reference to "participant"
        // optionally update UI
    };   

    watcher.Removed += (sender, participant) => {
        // remove reference to "participant"
        // optionally update UI
    };

    watcher.EnumerationCompleted += (sender, args) => {
        // Apps can delay data model render up until this point if they wish.
    };

    // Begin watching for session participants
    watcher.Start();
}
```

<span data-ttu-id="1baa3-151">Beim Abrufen der Verweisliste der Sitzungsteilnehmer können Sie eine Nachricht an alle senden.</span><span class="sxs-lookup"><span data-stu-id="1baa3-151">When a list of references to session participants is obtained you can send a message to any set of them.</span></span>

<span data-ttu-id="1baa3-152">Um eine Nachricht an einen einzelnen Teilnehmer zu senden (im Idealfall wird dieser auf dem Bildschirm vom Benutzer ausgewählt), übergeben Sie einfach den Verweis an eine Methode, die folgendermaßen aussieht:</span><span class="sxs-lookup"><span data-stu-id="1baa3-152">To send a message to a single participant (ideally selected on-screen by the user), simply pass the reference into a method like the following.</span></span>

```csharp
public async void SendMessageToParticipantAsync(RemoteSystemSessionMessageChannel messageChannel, RemoteSystemSessionParticipant participant, object value) {
    
    // define a ValueSet message to send
    ValueSet message = new ValueSet();
    
    // serialize the "value" object to send
    using (var stream = new MemoryStream()){
        new DataContractJsonSerializer(value.GetType()).WriteObject(stream, value);
        byte[] rawData = stream.ToArray();
            message["appKey"] = rawData;
    }

    // Send message to the participant
    await messageChannel.SendValueSetAsync(message,participant);
}
```

<span data-ttu-id="1baa3-153">Um eine Nachricht an mehrere Teilnehmer zu senden (im Idealfall wird dieser auf dem Bildschirm vom Benutzer ausgewählt), fügen Sie diese einem Listenobjekt hinzu und übergeben Sie die Liste an eine Methode, die folgendermaßen aussieht:</span><span class="sxs-lookup"><span data-stu-id="1baa3-153">To send a message to multiple participants (ideally selected on-screen by the user), add them to a list object and pass the list into a method like the following.</span></span>

```csharp
public async void SendMessageToListAsync(RemoteSystemSessionMessageChannel messageChannel, IReadOnlyList<RemoteSystemSessionParticipant> myTeam, object value){

    // define a ValueSet message to send
    ValueSet message = new ValueSet();
    
    // serialize the "value" object to send
    using (var stream = new MemoryStream()){
        new DataContractJsonSerializer(value.GetType()).WriteObject(stream, value);
        byte[] rawData = stream.ToArray();
            message["appKey"] = rawData;
    }

    // Send message to specific participants. Ordering is not guaranteed.
    await messageChannel.SendValueSetToParticipantsAsync(message, myTeam);   
}
```

## <a name="related-topics"></a><span data-ttu-id="1baa3-154">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1baa3-154">Related topics</span></span>
* [<span data-ttu-id="1baa3-155">Verbundene Apps und Geräte (Projekt „Rome”)</span><span class="sxs-lookup"><span data-stu-id="1baa3-155">Connected apps and devices (Project Rome)</span></span>](connected-apps-and-devices.md)
* [<span data-ttu-id="1baa3-156">API-Referenz für Remotesysteme</span><span class="sxs-lookup"><span data-stu-id="1baa3-156">Remote Systems API reference</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems)
