---
author: PatrickFarley
title: Kommunikation mit einem App-Remotedienst
description: Tauschen Sie Nachrichten mit einem App-Dienst aus, der auf einem Remotegerät mit Project Rome ausgeführt wird.
ms.assetid: a0261e7a-5706-4f9a-b79c-46a3c81b136f
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: a40b48df9f9d8fe740795d6af0d71ba70a34c469
ms.sourcegitcommit: d780e3a087ab5240ea643346480a1427bea9e29b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
ms.locfileid: "1572767"
---
# <a name="communicate-with-a-remote-app-service"></a><span data-ttu-id="a3606-104">Kommunikation mit einem App-Remotedienst</span><span class="sxs-lookup"><span data-stu-id="a3606-104">Communicate with a remote app service</span></span>

<span data-ttu-id="a3606-105">Sie können nicht nur eine App auf einem Remotegerät mithilfe eines URI starten, sondern auch *App-Dienste* auf Remotegeräten ausführen und mit ihnen kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="a3606-105">In addition to launching an app on a remote device using a URI, you can run and communicate with *app services* on remote devices as well.</span></span> <span data-ttu-id="a3606-106">Jedes Windows-basierte Gerät kann als Client- oder Hostgerät verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a3606-106">Any Windows-based device can be used as either the client or host device.</span></span> <span data-ttu-id="a3606-107">Dies bietet Ihnen eine nahezu unbegrenzte Anzahl von Möglichkeiten zur Interaktion mit verbundenen Geräten, ohne eine App in den Vordergrund bringen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="a3606-107">This gives you an almost limitless number of ways to interact with connected devices without needing to bring an app to the foreground.</span></span>

## <a name="set-up-the-app-service-on-the-host-device"></a><span data-ttu-id="a3606-108">Einrichten des App-Diensts auf dem Hostgerät</span><span class="sxs-lookup"><span data-stu-id="a3606-108">Set up the app service on the host device</span></span>
<span data-ttu-id="a3606-109">Um einen App-Dienst auf einem Remotegerät ausführen zu können, muss bereits ein Anbieter dieses App-Diensts auf dem Hostgerät installiert sein.</span><span class="sxs-lookup"><span data-stu-id="a3606-109">In order to run an app service on a remote device, you must already have a provider of that app service installed on that device.</span></span> <span data-ttu-id="a3606-110">In dieser Anleitung wird die CSharp-Version des [Beispiels für den App-Dienst für die Generierung von Zufallszahlen](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices) verwendet, das im [universellen Windows-Beispielrepository](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices) verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="a3606-110">This guide will use CSharp version of the [Random Number Generator app service sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices), which is available on the [Windows universal samples repo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices).</span></span> <span data-ttu-id="a3606-111">Anleitungen zum Schreiben eines eigenen App-Diensts finden Sie unter [Erstellen und Verwenden eines App-Diensts](how-to-create-and-consume-an-app-service.md).</span><span class="sxs-lookup"><span data-stu-id="a3606-111">For instructions on how to write your own app service, see [Create and consume an app service](how-to-create-and-consume-an-app-service.md).</span></span>

<span data-ttu-id="a3606-112">Gleichgültig, ob Sie einen bereits erstellten App-Dienst verwenden oder einen eigenen schreiben, Sie müssen einige Änderungen vornehmen, um den Dienst mit Remotesystemen kompatibel zu machen.</span><span class="sxs-lookup"><span data-stu-id="a3606-112">Whether you are using an already-made app service or writing your own, you will need to make a few edits in order to make the service compatible with remote systems.</span></span> <span data-ttu-id="a3606-113">Wechseln Sie in Visual Studio zum Projekt des App-Dienstanbieters (im Beispiel „AppServicesProvider”genannt), und wählen Sie die Datei _Package.appxmanifest_ aus.</span><span class="sxs-lookup"><span data-stu-id="a3606-113">In Visual Studio, go to the app service provider's project (called "AppServicesProvider" in the sample) and select its _Package.appxmanifest_ file.</span></span> <span data-ttu-id="a3606-114">Klicken Sie mit der rechten Maustaste, und wählen Sie **Code anzeigen** aus, um den gesamten Inhalt der Datei anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a3606-114">Right-click and select **View Code** to view the full contents of the file.</span></span> <span data-ttu-id="a3606-115">Suchen Sie das Element **Erweiterung**, das das Projekt als App-Dienst definiert und das übergeordnete Projekt benennt.</span><span class="sxs-lookup"><span data-stu-id="a3606-115">Find the **Extension** element that defines the project as an app service and names its parent project.</span></span>

``` xml
...
<Extensions>
    <uap:Extension Category="windows.appService" EntryPoint="RandomNumberService.RandomNumberGeneratorTask">
        <uap3:AppService Name="com.microsoft.randomnumbergenerator"/>
    </uap:Extension>
</Extensions>
...
```

<span data-ttu-id="a3606-116">Fügen Sie das Attribut **SupportsRemoteSystems** hinzu, wenn es nicht bereits vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="a3606-116">Add the **SupportsRemoteSystems** attribute if it is not already present:</span></span>

``` xml
...
<uap3:AppService Name="com.microsoft.randomnumbergenerator" SupportsRemoteSystems="true"/>
...
```

<span data-ttu-id="a3606-117">Erstellen Sie Ihr App-Dienstanbieterprojekt, und stellen Sie es auf dem Hostgerät/den Hostgeräten bereit.</span><span class="sxs-lookup"><span data-stu-id="a3606-117">Build your app service provider project and deploy it to the host device(s).</span></span>

## <a name="target-the-app-service-from-the-client-device"></a><span data-ttu-id="a3606-118">Aufrufen des App-Diensts vom Clientgerät</span><span class="sxs-lookup"><span data-stu-id="a3606-118">Target the app service from the client device</span></span>
<span data-ttu-id="a3606-119">Das Gerät, von dem der App-Remotedienst aufgerufen werden soll, muss über eine App mit Remotesystemfunktionen verfügen.</span><span class="sxs-lookup"><span data-stu-id="a3606-119">The device from which the remote app service is to be called needs an app with Remote Systems functionality.</span></span> <span data-ttu-id="a3606-120">Diese können der gleichen App hinzugefügt werden, die den App-Dienst auf dem Hostgerät bereitstellt (in diesem Fall installieren Sie gleiche App auf beiden Geräten), oder in einer völlig anderen App implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="a3606-120">This can be added into the same app that provides the app service on the host device (in which case you would install the same app on both devices), or implemented in a completely different app.</span></span>

<span data-ttu-id="a3606-121">Die folgenden **using**-Anweisungen werden für den Code in diesem Abschnitt benötigt, damit er wie gezeigt ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="a3606-121">The following **using** statements are needed for the code in this section to run as-is:</span></span>

[!code-cs[Main](./code/RemoteAppService/MainPage.xaml.cs#SnippetUsings)]


<span data-ttu-id="a3606-122">Instanziieren Sie zunächst ein [**AppServiceConnection**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.AppService.AppServiceConnection)-Objekt, als ob Sie einen App-Dienst lokal aufrufen würden.</span><span class="sxs-lookup"><span data-stu-id="a3606-122">You must first instantiate an [**AppServiceConnection**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.AppService.AppServiceConnection) object, just as if you were to call an app service locally.</span></span> <span data-ttu-id="a3606-123">Dieser Vorgang wird in [Erstellen und Verwenden eines App-Diensts](how-to-create-and-consume-an-app-service.md) ausführlicher behandelt.</span><span class="sxs-lookup"><span data-stu-id="a3606-123">This process is covered in more detail in [Create and consume an app service](how-to-create-and-consume-an-app-service.md).</span></span> <span data-ttu-id="a3606-124">In diesem Beispiel ist der aufzurufende App-Dienst der Dienst für die Generierung von Zufallszahlen.</span><span class="sxs-lookup"><span data-stu-id="a3606-124">In this example, the app service to target is the Random Number Generator service.</span></span>

> [!NOTE]
> <span data-ttu-id="a3606-125">Es wird angenommen, dass ein [RemoteSystem](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems.RemoteSystem)-Objekt bereits innerhalb des Codes geladen wurde, der die folgende Methode aufruft.</span><span class="sxs-lookup"><span data-stu-id="a3606-125">It is assumed that a [RemoteSystem](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems.RemoteSystem) object has already been acquired by some means within the code that would call the following method.</span></span> <span data-ttu-id="a3606-126">Anleitungen dazu, wie Sie dies einrichten können, finden Sie unter [Starten einer Remote-App](launch-a-remote-app.md).</span><span class="sxs-lookup"><span data-stu-id="a3606-126">See [Launch a remote app](launch-a-remote-app.md) for instructions on how to set this up.</span></span>

[!code-cs[Main](./code/RemoteAppService/MainPage.xaml.cs#SnippetAppService)]

<span data-ttu-id="a3606-127">Als Nächstes wird ein [**RemoteSystemConnectionRequest**](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems.RemoteSystemConnectionRequest)-Objekt für das vorgesehene Remotegerät erstellt.</span><span class="sxs-lookup"><span data-stu-id="a3606-127">Next, a [**RemoteSystemConnectionRequest**](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems.RemoteSystemConnectionRequest) object is created for the intended remote device.</span></span> <span data-ttu-id="a3606-128">Es wird dann zum Öffnen der **AppServiceConnection** zu diesem Gerät verwendet.</span><span class="sxs-lookup"><span data-stu-id="a3606-128">It is then used to open the **AppServiceConnection** to that device.</span></span> <span data-ttu-id="a3606-129">Beachten Sie, dass im folgenden Beispiel Fehlerbehandlung und Berichte erheblich vereinfacht dargestellt werden, um das Beispiel kurz zu halten.</span><span class="sxs-lookup"><span data-stu-id="a3606-129">Note that in the example below, error handling and reporting is greatly simplified for brevity.</span></span>

[!code-cs[Main](./code/RemoteAppService/MainPage.xaml.cs#SnippetRemoteConnection)]

<span data-ttu-id="a3606-130">An diesem Punkt sollten Sie über eine offene Verbindung zu einem App-Dienst auf einem Remotecomputer verfügen.</span><span class="sxs-lookup"><span data-stu-id="a3606-130">At this point, you should have an open connection to an app service on a remote machine.</span></span>

## <a name="exchange-service-specific-messages-over-the-remote-connection"></a><span data-ttu-id="a3606-131">Exchange-Dienst-spezifische Nachrichten über die Remoteverbindung</span><span class="sxs-lookup"><span data-stu-id="a3606-131">Exchange service-specific messages over the remote connection</span></span>

<span data-ttu-id="a3606-132">Hier können Sie Nachrichten in Form von [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset)-Objekten an den Dienst senden und von dem Dienst empfangen (weitere Informationen finden Sie unter [Erstellen und Verwenden eines App-Diensts](how-to-create-and-consume-an-app-service.md)).</span><span class="sxs-lookup"><span data-stu-id="a3606-132">From here, you can send and receive messages to and from the service in the form of [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objects (for more information, see [Create and consume an app service](how-to-create-and-consume-an-app-service.md)).</span></span> <span data-ttu-id="a3606-133">Der Dienst für die Generierung von Zufallszahlen verwendet zwei Ganzzahlen mit den Schlüsseln `"minvalue"` und `"maxvalue"` als Eingaben, wählt nach dem Zufallsprinzip innerhalb dieses Bereichs eine Ganzzahl aus und gibt diese an den aufrufenden Prozess mit dem Schlüssel `"Result"` zurück.</span><span class="sxs-lookup"><span data-stu-id="a3606-133">The Random number generator service takes two integers with the keys `"minvalue"` and `"maxvalue"` as inputs, randomly selects an integer within their range, and returns it to the calling process with the key `"Result"`.</span></span>

[!code-cs[Main](./code/RemoteAppService/MainPage.xaml.cs#SnippetSendMessage)]

<span data-ttu-id="a3606-134">Sie haben jetzt eine Verbindung zu einem App-Dienst auf einem aufgerufenen Hostgerät hergestellt, einen Vorgang auf diesem Gerät ausgeführt und auf dem Clientgerät als Antwort Daten empfangen.</span><span class="sxs-lookup"><span data-stu-id="a3606-134">Now you have connected to an app service on a targeted host device, run an operation on that device, and received data to your client device in response.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a3606-135">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a3606-135">Related topics</span></span>

[<span data-ttu-id="a3606-136">Übersicht über verbundene Apps und Geräte (Project Rome)</span><span class="sxs-lookup"><span data-stu-id="a3606-136">Connected apps and devices (Project Rome) overview</span></span>](connected-apps-and-devices.md)  
[<span data-ttu-id="a3606-137">Starten einer Remote-App</span><span class="sxs-lookup"><span data-stu-id="a3606-137">Launch a remote app</span></span>](launch-a-remote-app.md)  
[<span data-ttu-id="a3606-138">Erstellen und Verwenden eines App-Diensts</span><span class="sxs-lookup"><span data-stu-id="a3606-138">Create and consume an app service</span></span>](how-to-create-and-consume-an-app-service.md)  
[<span data-ttu-id="a3606-139">API-Referenz für Remotesysteme</span><span class="sxs-lookup"><span data-stu-id="a3606-139">Remote Systems API reference</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems)  
[<span data-ttu-id="a3606-140">Beispiel für Remotesysteme</span><span class="sxs-lookup"><span data-stu-id="a3606-140">Remote Systems sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)
