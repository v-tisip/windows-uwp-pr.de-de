---
description: WebSockets stellt einen Mechanismus für die schnelle und sichere bidirektionale Kommunikation zwischen einem Client und einem Server über das Web mithilfe von HTTP(S) bereit und unterstützt sowohl UTF-8- als auch binäre Nachrichten.
title: WebSockets
ms.assetid: EAA9CB3E-6A3A-4C13-9636-CCD3DE46E7E2
ms.date: 06/04/2018
ms.topic: article
keywords: windows10, uwp, netzwerk, websocket, messagewebsocket, streamwebsocket
ms.localizationpriority: medium
ms.openlocfilehash: 05f56f07aed0c9f97daffe3842952ce142f8159a
ms.sourcegitcommit: 1901a43b9e40a05c28c7799e0f9b08ce92f8c8a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2019
ms.locfileid: "9035411"
---
# <a name="websockets"></a><span data-ttu-id="a265b-104">WebSockets</span><span class="sxs-lookup"><span data-stu-id="a265b-104">WebSockets</span></span>
<span data-ttu-id="a265b-105">WebSockets stellt einen Mechanismus für die schnelle und sichere bidirektionale Kommunikation zwischen einem Client und einem Server über das Web mithilfe von HTTP(S) bereit und unterstützt sowohl UTF-8- als auch binäre Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="a265b-105">WebSockets provide a mechanism for fast, secure, two-way communication between a client and a server over the web using HTTP(S), and supporting both UTF-8 and binary messages.</span></span>

<span data-ttu-id="a265b-106">Mit dem [WebSocket-Protokoll](http://tools.ietf.org/html/rfc6455) werden Daten unmittelbar über eine Vollduplex-Einzelsocketverbindung übertragen, wodurch Nachrichten von beiden Endpunkten in Echtzeit gesendet und empfangen werden können.</span><span class="sxs-lookup"><span data-stu-id="a265b-106">Under the [WebSocket Protocol](http://tools.ietf.org/html/rfc6455), data is transferred immediately over a full-duplex single socket connection, allowing messages to be sent and received from both endpoints in real time.</span></span> <span data-ttu-id="a265b-107">WebSockets eignen sich ideal für den Einsatz in Multiplayer-Spielen (einschließlich Echtzeit- und rundenbasierter Spiele), Sofortbenachrichtigungen aus sozialen Netzwerken oder die aktuelle Anzeige von Aktien- oder Wetterdaten einschließen, sowie für Apps, für die die sichere und schnelle Datenübertragung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="a265b-107">WebSockets are ideal for use in multiplayer gaming (both real-time and turn-based), instant social network notifications, up-to-date displays of stock or weather information, and other apps requiring secure and fast data transfer.</span></span>

<span data-ttu-id="a265b-108">Zum Herstellen einer WebSocket-Verbindung wird zwischen dem Client und dem Server ein spezieller HTTP-basierter Handshake ausgetauscht.</span><span class="sxs-lookup"><span data-stu-id="a265b-108">To establish a WebSocket connection, a specific, HTTP-based handshake is exchanged between the client and the server.</span></span> <span data-ttu-id="a265b-109">Wenn dies erfolgreich war, wird das Anwendungsebenenprotokoll mithilfe der zuvor hergestellten TCP-Verbindung von HTTP auf WebSockets "aktualisiert".</span><span class="sxs-lookup"><span data-stu-id="a265b-109">If successful, the application-layer protocol is "upgraded" from HTTP to WebSockets, using the previously established TCP connection.</span></span> <span data-ttu-id="a265b-110">Sobald dies erfolgt ist, ist HTTP nicht mehr relevant. Daten können jederzeit mithilfe des WebSocket-Protokolls von beiden Endpunkten gesendet und empfangen werden, bis die WebSocket-Verbindung geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="a265b-110">Once this occurs, HTTP is completely out of the picture; data can be sent or received using the WebSocket protocol by both endpoints, until the WebSocket connection is closed.</span></span>

<span data-ttu-id="a265b-111">**Hinweis** Ein Client kann WebSockets nur zum Übertragen von Daten verwenden, wenn der Server auch das WebSocket-Protokoll verwendet.</span><span class="sxs-lookup"><span data-stu-id="a265b-111">**Note** A client cannot use WebSockets to transfer data unless the server also uses the WebSocket protocol.</span></span> <span data-ttu-id="a265b-112">Wenn der Server WebSockets nicht unterstützt, dann müssen Sie eine andere Datenübertragungsmethode verwenden.</span><span class="sxs-lookup"><span data-stu-id="a265b-112">If the server does not support WebSockets, then you must use another method of data transfer.</span></span>

<span data-ttu-id="a265b-113">Die Universelle Windows-Plattform (UWP) bietet Unterstützung für die Client- und Serververwendung von WebSockets.</span><span class="sxs-lookup"><span data-stu-id="a265b-113">The Universal Windows Platform (UWP) provides support for both client and server use of WebSockets.</span></span> <span data-ttu-id="a265b-114">Der [**Windows.Networking.Sockets**](/uwp/api/windows.networking.sockets)-Namespace definiert zwei WebSocket-Klassen für die Verwendung durch Clients&mdash;[**MessageWebSocket**](/uwp/api/windows.networking.sockets.messagewebsocket) und [**StreamWebSocket**](/uwp/api/windows.networking.sockets.streamwebsocket).</span><span class="sxs-lookup"><span data-stu-id="a265b-114">The [**Windows.Networking.Sockets**](/uwp/api/windows.networking.sockets) namespace defines two WebSocket classes for use by clients&mdash;[**MessageWebSocket**](/uwp/api/windows.networking.sockets.messagewebsocket), and [**StreamWebSocket**](/uwp/api/windows.networking.sockets.streamwebsocket).</span></span> <span data-ttu-id="a265b-115">Hier sehen Sie einen Vergleich dieser beiden WebSocket-Klassen.</span><span class="sxs-lookup"><span data-stu-id="a265b-115">Here's a comparison of these two WebSocket classes.</span></span>

| [<span data-ttu-id="a265b-116">MessageWebSocket</span><span class="sxs-lookup"><span data-stu-id="a265b-116">MessageWebSocket</span></span>](/uwp/api/windows.networking.sockets.messagewebsocket) | [<span data-ttu-id="a265b-117">StreamWebSocket</span><span class="sxs-lookup"><span data-stu-id="a265b-117">StreamWebSocket</span></span>](/uwp/api/windows.networking.sockets.streamwebsocket) |
| - | - |
| <span data-ttu-id="a265b-118">Eine gesamte WebSocket-Nachricht wird in einem einzigen Vorgang gelesen/geschrieben.</span><span class="sxs-lookup"><span data-stu-id="a265b-118">An entire WebSocket message is read/written in a single operation.</span></span> | <span data-ttu-id="a265b-119">Abschnitte einer Nachricht können bei jedem Lesevorgang gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="a265b-119">Sections of a message can be read with each read operation.</span></span> |
| <span data-ttu-id="a265b-120">Geeignet, wenn Nachrichten nicht sehr groß sind.</span><span class="sxs-lookup"><span data-stu-id="a265b-120">Suitable when messages are not very large.</span></span> | <span data-ttu-id="a265b-121">Geeignet, wenn sehr große Dateien (z.B. Fotos oder Videos) übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="a265b-121">Suitable when very large files (such as photos or videos) are being transferred.</span></span> |
| <span data-ttu-id="a265b-122">Unterstützt UTF-8-Nachrichten und binäre Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="a265b-122">Supports both UTF-8 and binary messages.</span></span> | <span data-ttu-id="a265b-123">Unterstützt nur binäre Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="a265b-123">Supports only binary messages.</span></span> |
| <span data-ttu-id="a265b-124">Ähnlich wie ein [UDP- oder Datagrammsocket](sockets.md#build-a-basic-udp-socket-client-and-server) (in dem Sinne, dass es für häufige, kleine Nachrichten bestimmt ist), jedoch mit der Zuverlässigkeit von TCP, Garantien für die Paketreihenfolge und Überlastungssteuerung.</span><span class="sxs-lookup"><span data-stu-id="a265b-124">Similar to a [UDP or datagram socket](sockets.md#build-a-basic-udp-socket-client-and-server) (in the sense of being intended for frequent, small messages), but with TCP's reliability, packet order guarantees, and congestion control.</span></span> | <span data-ttu-id="a265b-125">Ähnlich wie ein [TCP oder Streamsocket](sockets.md#build-a-basic-tcp-socket-client-and-server).</span><span class="sxs-lookup"><span data-stu-id="a265b-125">Similar to a [TCP or stream socket](sockets.md#build-a-basic-tcp-socket-client-and-server).</span></span> |

## <a name="secure-your-connection-with-tlsssl"></a><span data-ttu-id="a265b-126">Sichern Sie Ihre Verbindung mit TLS/SSL</span><span class="sxs-lookup"><span data-stu-id="a265b-126">Secure your connection with TLS/SSL</span></span>
<span data-ttu-id="a265b-127">In den meisten Fällen sollten Sie eine sichere WebSocket-Verbindung verwenden, damit Ihre gesendeten und empfangenen Daten verschlüsselt sind.</span><span class="sxs-lookup"><span data-stu-id="a265b-127">In most cases, you'll want to  use a secure WebSocket connection so that the data you send and receive is encrypted.</span></span> <span data-ttu-id="a265b-128">Dadurch ist es wahrscheinlicher, dass die Verbindung funktioniert, da andernfalls viele Vermittler wie beispielsweise Firewalls und Proxys unverschlüsselte WebSocket-Verbindungen ablehnen.</span><span class="sxs-lookup"><span data-stu-id="a265b-128">This will also increase the chances that your connection will succeed, because many intermediaries such as firewalls and proxies reject unencrypted WebSocket connections.</span></span> <span data-ttu-id="a265b-129">Das [WebSocket-Protokoll](https://tools.ietf.org/html/rfc6455#section-3) definiert die folgenden zwei URI-Schemata.</span><span class="sxs-lookup"><span data-stu-id="a265b-129">The [WebSocket protocol](https://tools.ietf.org/html/rfc6455#section-3) defines these two URI schemes.</span></span>

| <span data-ttu-id="a265b-130">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="a265b-130">URI scheme</span></span> | <span data-ttu-id="a265b-131">Zweck</span><span class="sxs-lookup"><span data-stu-id="a265b-131">Purpose</span></span> |
| - | - |
| <span data-ttu-id="a265b-132">wss:</span><span class="sxs-lookup"><span data-stu-id="a265b-132">wss:</span></span> | <span data-ttu-id="a265b-133">Wird für sichere Verbindungen verwendet, die verschlüsselt werden sollten.</span><span class="sxs-lookup"><span data-stu-id="a265b-133">Use for secure connections that should be encrypted.</span></span> |
| <span data-ttu-id="a265b-134">ws:</span><span class="sxs-lookup"><span data-stu-id="a265b-134">ws:</span></span> | <span data-ttu-id="a265b-135">Wird für unverschlüsselte Verbindungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="a265b-135">Use for unencrypted connections.</span></span> |

<span data-ttu-id="a265b-136">Verwenden Sie zum Sichern Ihrer WebSocket-Verbindung das URI-Schema `wss:`.</span><span class="sxs-lookup"><span data-stu-id="a265b-136">To encrypt your WebSocket connection, use the `wss:` URI scheme.</span></span> <span data-ttu-id="a265b-137">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="a265b-137">Here's an example.</span></span>

```csharp
protected override async void OnNavigatedTo(NavigationEventArgs e)
{
    var webSocket = new Windows.Networking.Sockets.MessageWebSocket();
    await webSocket.ConnectAsync(new Uri("wss://www.contoso.com/mywebservice"));
}
```

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.UI.Xaml.Navigation.h>
#include <sstream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::UI::Xaml::Navigation;
...
IAsyncAction OnNavigatedTo(NavigationEventArgs /* e */)
{
    Windows::Networking::Sockets::MessageWebSocket webSocket;
    co_await webSocket.ConnectAsync(Uri{ L"wss://www.contoso.com/mywebservice" });
}
```

## <a name="use-messagewebsocket-to-connect"></a><span data-ttu-id="a265b-138">Verwenden von MessageWebSocket zum Herstellen einer Verbindung</span><span class="sxs-lookup"><span data-stu-id="a265b-138">Use MessageWebSocket to connect</span></span>
<span data-ttu-id="a265b-139">Mit [**MessageWebSocket**](/uwp/api/windows.networking.sockets.messagewebsocket) kann eine gesamte WebSocket-Nachricht in einem einzigen Vorgang gelesen/geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="a265b-139">[**MessageWebSocket**](/uwp/api/windows.networking.sockets.messagewebsocket) allows an entire WebSocket message to be read/written in a single operation.</span></span> <span data-ttu-id="a265b-140">Folglich ist es geeignet, wenn Nachrichten nicht sehr groß sind.</span><span class="sxs-lookup"><span data-stu-id="a265b-140">Consequently, it's suitable when messages are not very large.</span></span> <span data-ttu-id="a265b-141">Die Klasse unterstützt UTF-8- und binäre Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="a265b-141">The class supports both UTF-8 and binary messages.</span></span>

<span data-ttu-id="a265b-142">Der nachstehende Beispielcode verwendet den WebSocket.org-Echoserver&mdash;einen Dienst, der Nachrichten zurück an den Absender sendet.</span><span class="sxs-lookup"><span data-stu-id="a265b-142">The example code below uses the WebSocket.org echo server&mdash;a service that echoes back to the sender any message sent to it.</span></span>

```csharp
private Windows.Networking.Sockets.MessageWebSocket messageWebSocket;

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    this.messageWebSocket = new Windows.Networking.Sockets.MessageWebSocket();

    // In this example, we send/receive a string, so we need to set the MessageType to Utf8.
    this.messageWebSocket.Control.MessageType = Windows.Networking.Sockets.SocketMessageType.Utf8;

    this.messageWebSocket.MessageReceived += WebSocket_MessageReceived;
    this.messageWebSocket.Closed += WebSocket_Closed;

    try
    {
        Task connectTask = this.messageWebSocket.ConnectAsync(new Uri("wss://echo.websocket.org")).AsTask();
        connectTask.ContinueWith(_ => this.SendMessageUsingMessageWebSocketAsync("Hello, World!"));
    }
    catch (Exception ex)
    {
        Windows.Web.WebErrorStatus webErrorStatus = Windows.Networking.Sockets.WebSocketError.GetStatus(ex.GetBaseException().HResult);
        // Add additional code here to handle exceptions.
    }
}

private async Task SendMessageUsingMessageWebSocketAsync(string message)
{
    using (var dataWriter = new DataWriter(this.messageWebSocket.OutputStream))
    {
        dataWriter.WriteString(message);
        await dataWriter.StoreAsync();
        dataWriter.DetachStream();
    }
    Debug.WriteLine("Sending message using MessageWebSocket: " + message);
}

private void WebSocket_MessageReceived(Windows.Networking.Sockets.MessageWebSocket sender, Windows.Networking.Sockets.MessageWebSocketMessageReceivedEventArgs args)
{
    try
    {
        using (DataReader dataReader = args.GetDataReader())
        {
            dataReader.UnicodeEncoding = Windows.Storage.Streams.UnicodeEncoding.Utf8;
            string message = dataReader.ReadString(dataReader.UnconsumedBufferLength);
            Debug.WriteLine("Message received from MessageWebSocket: " + message);
            this.messageWebSocket.Dispose();
        }
    }
    catch (Exception ex)
    {
        Windows.Web.WebErrorStatus webErrorStatus = Windows.Networking.Sockets.WebSocketError.GetStatus(ex.GetBaseException().HResult);
        // Add additional code here to handle exceptions.
    }
}

private void WebSocket_Closed(Windows.Networking.Sockets.IWebSocket sender, Windows.Networking.Sockets.WebSocketClosedEventArgs args)
{
    Debug.WriteLine("WebSocket_Closed; Code: " + args.Code + ", Reason: \"" + args.Reason + "\"");
    // Add additional code here to handle the WebSocket being closed.
}
```

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.UI.Xaml.Navigation.h>
#include <sstream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::MessageWebSocket m_messageWebSocket;
    winrt::event_token m_messageReceivedEventToken;
    winrt::event_token m_closedEventToken;

public:
    IAsyncAction OnNavigatedTo(NavigationEventArgs /* e */)
    {
        // In this example, we send/receive a string, so we need to set the MessageType to Utf8.
        m_messageWebSocket.Control().MessageType(Windows::Networking::Sockets::SocketMessageType::Utf8);

        m_messageReceivedEventToken = m_messageWebSocket.MessageReceived({ this, &MessageWebSocketPage::OnWebSocketMessageReceived });
        m_closedEventToken = m_messageWebSocket.Closed({ this, &MessageWebSocketPage::OnWebSocketClosed });

        try
        {
            co_await m_messageWebSocket.ConnectAsync(Uri{ L"wss://echo.websocket.org" });
            SendMessageUsingMessageWebSocketAsync(L"Hello, World!");
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus{ Windows::Networking::Sockets::WebSocketError::GetStatus(ex.to_abi()) };
            // Add additional code here to handle exceptions.
        }
    }

private:
    IAsyncAction SendMessageUsingMessageWebSocketAsync(std::wstring message)
    {
        DataWriter dataWriter{ m_messageWebSocket.OutputStream() };
        dataWriter.WriteString(message);

        co_await dataWriter.StoreAsync();
        dataWriter.DetachStream();
        std::wstringstream wstringstream;
        wstringstream << L"Sending message using MessageWebSocket: " << message.c_str() << std::endl;
        ::OutputDebugString(wstringstream.str().c_str());
    }

    void OnWebSocketMessageReceived(Windows::Networking::Sockets::MessageWebSocket const& /* sender */, Windows::Networking::Sockets::MessageWebSocketMessageReceivedEventArgs const& args)
    {
        try
        {
            DataReader dataReader{ args.GetDataReader() };

            dataReader.UnicodeEncoding(Windows::Storage::Streams::UnicodeEncoding::Utf8);
            auto message = dataReader.ReadString(dataReader.UnconsumedBufferLength());
            std::wstringstream wstringstream;
            wstringstream << L"Message received from MessageWebSocket: " << message.c_str() << std::endl;
            ::OutputDebugString(wstringstream.str().c_str());
            m_messageWebSocket.Close(1000, L"");
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus{ Windows::Networking::Sockets::WebSocketError::GetStatus(ex.to_abi()) };
            // Add additional code here to handle exceptions.
        }
    }

    void OnWebSocketClosed(Windows::Networking::Sockets::IWebSocket const& /* sender */, Windows::Networking::Sockets::WebSocketClosedEventArgs const& args)
    {
        std::wstringstream wstringstream;
        wstringstream << L"WebSocket_Closed; Code: " << args.Code() << ", Reason: \"" << args.Reason().c_str() << "\"" << std::endl;
        ::OutputDebugString(wstringstream.str().c_str());
        // Add additional code here to handle the WebSocket being closed.
    }
```

```cpp
#include <ppltasks.h>
#include <sstream>
...
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::MessageWebSocket^ messageWebSocket;

protected:
    virtual void OnNavigatedTo(NavigationEventArgs^ e) override
    {
        this->messageWebSocket = ref new Windows::Networking::Sockets::MessageWebSocket();

        // In this example, we send/receive a string, so we need to set the MessageType to Utf8.
        this->messageWebSocket->Control->MessageType = Windows::Networking::Sockets::SocketMessageType::Utf8;

        this->messageWebSocket->MessageReceived += ref new TypedEventHandler<Windows::Networking::Sockets::MessageWebSocket^, Windows::Networking::Sockets::MessageWebSocketMessageReceivedEventArgs^>(this, &MessageWebSocketPage::WebSocket_MessageReceived);
        this->messageWebSocket->Closed += ref new TypedEventHandler<Windows::Networking::Sockets::IWebSocket^, Windows::Networking::Sockets::WebSocketClosedEventArgs^>(this, &MessageWebSocketPage::WebSocket_Closed);

        try
        {
            auto connectTask = Concurrency::create_task(this->messageWebSocket->ConnectAsync(ref new Uri(L"wss://echo.websocket.org")));
            connectTask.then([this] { this->SendMessageUsingMessageWebSocketAsync(L"Hello, World!"); });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus = Windows::Networking::Sockets::WebSocketError::GetStatus(ex->HResult);
            // Add additional code here to handle exceptions.
        }
    }

private:
    void SendMessageUsingMessageWebSocketAsync(Platform::String^ message)
    {
        auto dataWriter = ref new DataWriter(this->messageWebSocket->OutputStream);
        dataWriter->WriteString(message);

        Concurrency::create_task(dataWriter->StoreAsync()).then(
            [=](unsigned int)
        {
            dataWriter->DetachStream();
            std::wstringstream wstringstream;
            wstringstream << L"Sending message using MessageWebSocket: " << message->Data() << std::endl;
            ::OutputDebugString(wstringstream.str().c_str());
        });
    }

    void WebSocket_MessageReceived(Windows::Networking::Sockets::MessageWebSocket^ sender, Windows::Networking::Sockets::MessageWebSocketMessageReceivedEventArgs^ args)
    {
        try
        {
            DataReader^ dataReader = args->GetDataReader();

            dataReader->UnicodeEncoding = Windows::Storage::Streams::UnicodeEncoding::Utf8;
            Platform::String^ message = dataReader->ReadString(dataReader->UnconsumedBufferLength);
            std::wstringstream wstringstream;
            wstringstream << L"Message received from MessageWebSocket: " << message->Data() << std::endl;
            ::OutputDebugString(wstringstream.str().c_str());
            this->messageWebSocket->Close(1000, L"");
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus = Windows::Networking::Sockets::WebSocketError::GetStatus(ex->HResult);
            // Add additional code here to handle exceptions.
        }
    }

    void WebSocket_Closed(Windows::Networking::Sockets::IWebSocket^ sender, Windows::Networking::Sockets::WebSocketClosedEventArgs^ args)
    {
        std::wstringstream wstringstream;
        wstringstream << L"WebSocket_Closed; Code: " << args->Code << ", Reason: \"" << args->Reason->Data() << "\"" << std::endl;
        ::OutputDebugString(wstringstream.str().c_str());
        // Add additional code here to handle the WebSocket being closed.
    }
```

### <a name="handle-the-messagewebsocketmessagereceived-and-messagewebsocketclosed-events"></a><span data-ttu-id="a265b-143">Behandeln der Ereignisse „MessageWebSocket.MessageReceived” und „MessageWebSocket.Closed”</span><span class="sxs-lookup"><span data-stu-id="a265b-143">Handle the MessageWebSocket.MessageReceived and MessageWebSocket.Closed events</span></span>
<span data-ttu-id="a265b-144">Wie im obigen Beispiel gezeigt, sollten Sie vor dem Herstellen einer Verbindung und Senden von Daten mit einem **MessageWebSocket** die Ereignisse [**MessageWebSocket.MessageReceived**](/uwp/api/windows.networking.sockets.messagewebsocket.MessageReceived) und [**MessageWebSocket.Closed**](/uwp/api/windows.networking.sockets.messagewebsocket.Closed) abonnieren.</span><span class="sxs-lookup"><span data-stu-id="a265b-144">As shown in the example above, before establishing a connection and sending data with a **MessageWebSocket**, you should subscribe to the [**MessageWebSocket.MessageReceived**](/uwp/api/windows.networking.sockets.messagewebsocket.MessageReceived) and  [**MessageWebSocket.Closed**](/uwp/api/windows.networking.sockets.messagewebsocket.Closed) events.</span></span>
 
<span data-ttu-id="a265b-145">**MessageReceived** wird ausgelöst, wenn Daten empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="a265b-145">**MessageReceived** is raised when data is received.</span></span> <span data-ttu-id="a265b-146">Der Zugriff auf die Daten erfolgt über [**MessageWebSocketMessageReceivedEventArgs**](/uwp/api/windows.networking.sockets.messagewebsocketmessagereceivedeventargs).</span><span class="sxs-lookup"><span data-stu-id="a265b-146">The data can be accessed via [**MessageWebSocketMessageReceivedEventArgs**](/uwp/api/windows.networking.sockets.messagewebsocketmessagereceivedeventargs).</span></span> <span data-ttu-id="a265b-147">**Closed** wird ausgelöst, wenn der Client oder Server den Socket schließt.</span><span class="sxs-lookup"><span data-stu-id="a265b-147">**Closed** is raised when the client or the server closes the socket.</span></span>
 
### <a name="send-data-on-a-messagewebsocket"></a><span data-ttu-id="a265b-148">Senden von Daten auf einem MessageWebSocket</span><span class="sxs-lookup"><span data-stu-id="a265b-148">Send data on a MessageWebSocket</span></span>
<span data-ttu-id="a265b-149">Sobald eine Verbindung hergestellt ist, können Sie Daten an den Server senden.</span><span class="sxs-lookup"><span data-stu-id="a265b-149">Once a connection is established, you can send data to the server.</span></span> <span data-ttu-id="a265b-150">Verwenden Sie hierzu die [**MessageWebSocket.OutputStream**](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.MessageWebSocket.OutputStream)-Eigenschaft und einen [**DataWriter**](/uwp/api/windows.storage.streams.datawriter), um die Daten zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="a265b-150">You do this by using the [**MessageWebSocket.OutputStream**](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.MessageWebSocket.OutputStream) property, and a [**DataWriter**](/uwp/api/windows.storage.streams.datawriter), to write the data.</span></span> 

<span data-ttu-id="a265b-151">**Hinweis** Der **DataWriter** übernimmt den Besitz am Ausgabestream.</span><span class="sxs-lookup"><span data-stu-id="a265b-151">**Note** The **DataWriter** takes ownership of the output stream.</span></span> <span data-ttu-id="a265b-152">Wenn der **DataWriter** den gültigen Bereich verlässt, gibt der **DataWriter** den Ausgabestream frei, wenn dieser an ihn angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="a265b-152">When the **DataWriter** goes out of scope, if the output stream is attached to it, the **DataWriter** deallocates the output stream.</span></span> <span data-ttu-id="a265b-153">Danach schlagen alle nachfolgenden Versuche, den Ausgabestream zu verwenden, mit einem HRESULT-Wert 0x80000013 fehl.</span><span class="sxs-lookup"><span data-stu-id="a265b-153">After that, subsequent attempts to use the output stream fail with an HRESULT value of 0x80000013.</span></span> <span data-ttu-id="a265b-154">Sie können jedoch [**DataWriter.DetachStream**](/uwp/api/windows.storage.streams.datawriter.DetachStream) aufrufen, um den Ausgabestream vom **DataWriter** zu trennen und den Besitz am Stream dem **MessageWebSocket** zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="a265b-154">But you can call [**DataWriter.DetachStream**](/uwp/api/windows.storage.streams.datawriter.DetachStream) to detach the output stream from the **DataWriter** and return ownership of the stream to the **MessageWebSocket**.</span></span>

## <a name="use-streamwebsocket-to-connect"></a><span data-ttu-id="a265b-155">Verwenden von StreamWebSocket zum Herstellen einer Verbindung</span><span class="sxs-lookup"><span data-stu-id="a265b-155">Use StreamWebSocket to connect</span></span>
<span data-ttu-id="a265b-156">[**StreamWebSocket**](/uwp/api/windows.networking.sockets.streamwebsocket) ermöglicht, dass bei jedem Lesevorgang Abschnitte einer Nachricht gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="a265b-156">[**StreamWebSocket**](/uwp/api/windows.networking.sockets.streamwebsocket) allows sections of a message to be read with each read operation.</span></span> <span data-ttu-id="a265b-157">Folglich ist es geeignet, wenn sehr große Dateien (z.B. Fotos oder Videos) übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="a265b-157">Consequently, it's suitable when very large files (such as photos or videos) are being transferred.</span></span> <span data-ttu-id="a265b-158">Die Klasse unterstützt nur binäre Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="a265b-158">The class supports only binary messages.</span></span>

<span data-ttu-id="a265b-159">Der nachstehende Beispielcode verwendet den WebSocket.org-Echoserver&mdash;einen Dienst, der Nachrichten zurück an den Absender sendet.</span><span class="sxs-lookup"><span data-stu-id="a265b-159">The example code below uses the WebSocket.org echo server&mdash;a service that echoes back to the sender any message sent to it.</span></span>

```csharp
private Windows.Networking.Sockets.StreamWebSocket streamWebSocket;

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    this.streamWebSocket = new Windows.Networking.Sockets.StreamWebSocket();

    this.streamWebSocket.Closed += WebSocket_Closed;

    try
    {
        Task connectTask = this.streamWebSocket.ConnectAsync(new Uri("wss://echo.websocket.org")).AsTask();

        connectTask.ContinueWith(_ =>
        {
            Task.Run(() => this.ReceiveMessageUsingStreamWebSocket());
            Task.Run(() => this.SendMessageUsingStreamWebSocket(new byte[] { 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09 }));
        });
    }
    catch (Exception ex)
    {
        Windows.Web.WebErrorStatus webErrorStatus = Windows.Networking.Sockets.WebSocketError.GetStatus(ex.GetBaseException().HResult);
        // Add code here to handle exceptions.
    }
}

private async void ReceiveMessageUsingStreamWebSocket()
{
    try
    {
        using (var dataReader = new DataReader(this.streamWebSocket.InputStream))
        {
            dataReader.InputStreamOptions = InputStreamOptions.Partial;
            await dataReader.LoadAsync(256);
            byte[] message = new byte[dataReader.UnconsumedBufferLength];
            dataReader.ReadBytes(message);
            Debug.WriteLine("Data received from StreamWebSocket: " + message.Length + " bytes");
        }
        this.streamWebSocket.Dispose();
    }
    catch (Exception ex)
    {
        Windows.Web.WebErrorStatus webErrorStatus = Windows.Networking.Sockets.WebSocketError.GetStatus(ex.GetBaseException().HResult);
        // Add code here to handle exceptions.
    }
}

private async void SendMessageUsingStreamWebSocket(byte[] message)
{
    try
    {
        using (var dataWriter = new DataWriter(this.streamWebSocket.OutputStream))
        {
            dataWriter.WriteBytes(message);
            await dataWriter.StoreAsync();
            dataWriter.DetachStream();
        }
        Debug.WriteLine("Sending data using StreamWebSocket: " + message.Length.ToString() + " bytes");
    }
    catch (Exception ex)
    {
        Windows.Web.WebErrorStatus webErrorStatus = Windows.Networking.Sockets.WebSocketError.GetStatus(ex.GetBaseException().HResult);
        // Add code here to handle exceptions.
    }
}

private void WebSocket_Closed(Windows.Networking.Sockets.IWebSocket sender, Windows.Networking.Sockets.WebSocketClosedEventArgs args)
{
    Debug.WriteLine("WebSocket_Closed; Code: " + args.Code + ", Reason: \"" + args.Reason + "\"");
    // Add additional code here to handle the WebSocket being closed.
}
```

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.UI.Xaml.Navigation.h>
#include <sstream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::StreamWebSocket m_streamWebSocket;
    winrt::event_token m_closedEventToken;

public:
    IAsyncAction OnNavigatedTo(NavigationEventArgs /* e */)
    {
        m_closedEventToken = m_streamWebSocket.Closed({ this, &StreamWebSocketPage::OnWebSocketClosed });

        try
        {
            co_await m_streamWebSocket.ConnectAsync(Uri{ L"wss://echo.websocket.org" });
            ReceiveMessageUsingStreamWebSocket();
            SendMessageUsingStreamWebSocket({ 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09 });
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus{ Windows::Networking::Sockets::WebSocketError::GetStatus(ex.to_abi()) };
            // Add additional code here to handle exceptions.
        }
    }

private:
    IAsyncAction SendMessageUsingStreamWebSocket(std::vector< byte > message)
    {
        try
        {
            DataWriter dataWriter{ m_streamWebSocket.OutputStream() };
            dataWriter.WriteBytes(message);

            co_await dataWriter.StoreAsync();
            dataWriter.DetachStream();
            std::wstringstream wstringstream;
            wstringstream << L"Sending data using StreamWebSocket: " << message.size() << L" bytes" << std::endl;
            ::OutputDebugString(wstringstream.str().c_str());
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus{ Windows::Networking::Sockets::WebSocketError::GetStatus(ex.to_abi()) };
            // Add additional code here to handle exceptions.
        }
    }

    IAsyncAction ReceiveMessageUsingStreamWebSocket()
    {
        try
        {
            DataReader dataReader{ m_streamWebSocket.InputStream() };
            dataReader.InputStreamOptions(InputStreamOptions::Partial);

            unsigned int bytesLoaded = co_await dataReader.LoadAsync(256);
            std::vector< byte > message(bytesLoaded);
            dataReader.ReadBytes(message);
            std::wstringstream wstringstream;
            wstringstream << L"Data received from StreamWebSocket: " << message.size() << " bytes" << std::endl;
            ::OutputDebugString(wstringstream.str().c_str());
            m_streamWebSocket.Close(1000, L"");
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus{ Windows::Networking::Sockets::WebSocketError::GetStatus(ex.to_abi()) };
            // Add additional code here to handle exceptions.
        }
    }

    void OnWebSocketClosed(Windows::Networking::Sockets::IWebSocket const&, Windows::Networking::Sockets::WebSocketClosedEventArgs const& args)
    {
        std::wstringstream wstringstream;
        wstringstream << L"WebSocket_Closed; Code: " << args.Code() << ", Reason: \"" << args.Reason().c_str() << "\"" << std::endl;
        ::OutputDebugString(wstringstream.str().c_str());
        // Add additional code here to handle the WebSocket being closed.
    }
```

```cpp
#include <ppltasks.h>
#include <sstream>
...
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::StreamWebSocket^ streamWebSocket;

protected:
    virtual void OnNavigatedTo(NavigationEventArgs^ e) override
    {
        this->streamWebSocket = ref new Windows::Networking::Sockets::StreamWebSocket();

        this->streamWebSocket->Closed += ref new TypedEventHandler<Windows::Networking::Sockets::IWebSocket^, Windows::Networking::Sockets::WebSocketClosedEventArgs^>(this, &StreamWebSocketPage::WebSocket_Closed);

        try
        {
            auto connectTask = Concurrency::create_task(this->streamWebSocket->ConnectAsync(ref new Uri(L"wss://echo.websocket.org")));

            connectTask.then(
                [=]
            {
                this->ReceiveMessageUsingStreamWebSocket();
                this->SendMessageUsingStreamWebSocket(ref new Platform::Array< byte >{ 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09 });
            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus = Windows::Networking::Sockets::WebSocketError::GetStatus(ex->HResult);
            // Add additional code here to handle exceptions.
        }
    }

private:
    void SendMessageUsingStreamWebSocket(const Platform::Array< byte >^ message)
    {
        try
        {
            auto dataWriter = ref new DataWriter(this->streamWebSocket->OutputStream);
            dataWriter->WriteBytes(message);

            Concurrency::create_task(dataWriter->StoreAsync()).then(
                [=](Concurrency::task< unsigned int >) // task< unsigned int > instead of unsigned int in order to handle any exceptions thrown in StoreAsync().
            {
                dataWriter->DetachStream();
                std::wstringstream wstringstream;
                wstringstream << L"Sending data using StreamWebSocket: " << message->Length << L" bytes" << std::endl;
                ::OutputDebugString(wstringstream.str().c_str());
            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus = Windows::Networking::Sockets::WebSocketError::GetStatus(ex->HResult);
            // Add additional code here to handle exceptions.
        }
    }

    void ReceiveMessageUsingStreamWebSocket()
    {
        try
        {
            DataReader^ dataReader = ref new DataReader(this->streamWebSocket->InputStream);
            dataReader->InputStreamOptions = InputStreamOptions::Partial;

            Concurrency::create_task(dataReader->LoadAsync(256)).then(
                [=](unsigned int bytesLoaded)
            {
                auto message = ref new Platform::Array< byte >(bytesLoaded);
                dataReader->ReadBytes(message);
                std::wstringstream wstringstream;
                wstringstream << L"Data received from StreamWebSocket: " << message->Length << " bytes" << std::endl;
                ::OutputDebugString(wstringstream.str().c_str());
                this->streamWebSocket->Close(1000, L"");
            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus = Windows::Networking::Sockets::WebSocketError::GetStatus(ex->HResult);
            // Add additional code here to handle exceptions.
        }
    }

    void WebSocket_Closed(Windows::Networking::Sockets::IWebSocket^ sender, Windows::Networking::Sockets::WebSocketClosedEventArgs^ args)
    {
        std::wstringstream wstringstream;
        wstringstream << L"WebSocket_Closed; Code: " << args->Code << ", Reason: \"" << args->Reason->Data() << "\"" << std::endl;
        ::OutputDebugString(wstringstream.str().c_str());
        // Add additional code here to handle the WebSocket being closed.
    }
```

### <a name="handle-the-streamwebsocketclosed-event"></a><span data-ttu-id="a265b-160">Behandeln des StreamWebSocket.Closed-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="a265b-160">Handle the StreamWebSocket.Closed event</span></span>
<span data-ttu-id="a265b-161">Vor dem Herstellen einer Verbindung und Senden von Daten mit einem **StreamWebSocket** sollten Sie das [**StreamWebSocket.Closed**](/uwp/api/windows.networking.sockets.streamwebsocket.Closed)-Ereignis abonnieren.</span><span class="sxs-lookup"><span data-stu-id="a265b-161">Before establishing a connection and sending data with a **StreamWebSocket**, you should subscribe to the [**StreamWebSocket.Closed**](/uwp/api/windows.networking.sockets.streamwebsocket.Closed) event.</span></span> <span data-ttu-id="a265b-162">**Closed** wird ausgelöst, wenn der Client oder Server den Socket schließt.</span><span class="sxs-lookup"><span data-stu-id="a265b-162">**Closed** is raised when the client or the server closes the socket.</span></span>
 
### <a name="send-data-on-a-streamwebsocket"></a><span data-ttu-id="a265b-163">Senden von Daten auf einem StreamWebSocket</span><span class="sxs-lookup"><span data-stu-id="a265b-163">Send data on a StreamWebSocket</span></span>
<span data-ttu-id="a265b-164">Sobald eine Verbindung hergestellt ist, können Sie Daten an den Server senden.</span><span class="sxs-lookup"><span data-stu-id="a265b-164">Once a connection is established, you can send data to the server.</span></span> <span data-ttu-id="a265b-165">Verwenden Sie hierzu die [**StreamWebSocket.OutputStream**](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.StreamWebSocket.OutputStream)-Eigenschaft und einen [**DataWriter**](/uwp/api/windows.storage.streams.datawriter), um die Daten zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="a265b-165">You do this by using the [**StreamWebSocket.OutputStream**](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.StreamWebSocket.OutputStream) property, and a [**DataWriter**](/uwp/api/windows.storage.streams.datawriter), to write the data.</span></span>

<span data-ttu-id="a265b-166">**Hinweis** Wenn Sie mehr Daten auf demselben Socket schreiben möchten, müssen Sie [**DataWriter.DetachStream**](/uwp/api/windows.storage.streams.datawriter.DetachStream) aufrufen, um den Ausgabestream vom **DataWriter** zu trennen, bevor der **DataWriter** den gültigen Bereich verlässt.</span><span class="sxs-lookup"><span data-stu-id="a265b-166">**Note** If you want to write more data on the same socket, then be sure to call [**DataWriter.DetachStream**](/uwp/api/windows.storage.streams.datawriter.DetachStream) to detach the output stream from the **DataWriter** before the **DataWriter** goes out of scope.</span></span> <span data-ttu-id="a265b-167">Dadurch wird der Besitz am Datenstrom an den **MessageWebSocket** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a265b-167">This returns ownership of the stream to the **MessageWebSocket**.</span></span>

### <a name="receive-data-on-a-streamwebsocket"></a><span data-ttu-id="a265b-168">Empfangen von Daten auf einem StreamWebSocket</span><span class="sxs-lookup"><span data-stu-id="a265b-168">Receive data on a StreamWebSocket</span></span>
<span data-ttu-id="a265b-169">Verwenden Sie die [**StreamWebSocket.InputStream**](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.StreamWebSocket.InputStream)-Eigenschaft und einen [**DataReader**](/uwp/api/windows.storage.streams.datareader), um die Daten zu lesen.</span><span class="sxs-lookup"><span data-stu-id="a265b-169">Use the [**StreamWebSocket.InputStream**](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.StreamWebSocket.InputStream) property, and a [**DataReader**](/uwp/api/windows.storage.streams.datareader), to read the data.</span></span>

## <a name="advanced-options-for-messagewebsocket-and-streamwebsocket"></a><span data-ttu-id="a265b-170">Erweiterte Optionen für MessageWebSocket und StreamWebSocket</span><span class="sxs-lookup"><span data-stu-id="a265b-170">Advanced options for MessageWebSocket and StreamWebSocket</span></span>
<span data-ttu-id="a265b-171">Vor dem Herstellen einer Verbindung können Sie erweiterte Optionen für einen Socket festlegen, indem Sie die Eigenschaften für entweder [**MessageWebSocketControl**](/uwp/api/windows.networking.sockets.messagewebsocketcontrol) oder [**StreamWebSocketControl**](/uwp/api/windows.networking.sockets.streamwebsocketcontrol) festlegen.</span><span class="sxs-lookup"><span data-stu-id="a265b-171">Before establishing a connection, you can set advanced options on a socket by setting properties on either [**MessageWebSocketControl**](/uwp/api/windows.networking.sockets.messagewebsocketcontrol) or [**StreamWebSocketControl**](/uwp/api/windows.networking.sockets.streamwebsocketcontrol).</span></span> <span data-ttu-id="a265b-172">Sie greifen auf eine Instanz dieser Klassen aus dem Socketobjekt selbst entweder über dessen [**MessageWebSocket.Control**](/uwp/api/windows.networking.sockets.messagewebsocket.control)- oder [**StreamWebSocket.Control**](/uwp/api/windows.networking.sockets.streamwebsocket.control)-Eigenschaft zu, je nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="a265b-172">You access an instance of those classes from the socket object itself either via its [**MessageWebSocket.Control**](/uwp/api/windows.networking.sockets.messagewebsocket.control) property or its [**StreamWebSocket.Control**](/uwp/api/windows.networking.sockets.streamwebsocket.control) property, as appropriate.</span></span>

<span data-ttu-id="a265b-173">Hier sehen Sie ein Beispiel zur Verwendung von **StreamWebSocket**.</span><span class="sxs-lookup"><span data-stu-id="a265b-173">Here's an example using **StreamWebSocket**.</span></span> <span data-ttu-id="a265b-174">Das gleiche Muster gilt für **MessageWebSocket**.</span><span class="sxs-lookup"><span data-stu-id="a265b-174">The same pattern applies to **MessageWebSocket**.</span></span>

```csharp
var streamWebSocket = new Windows.Networking.Sockets.StreamWebSocket();

// By default, the Nagle algorithm is not used. This overrides that, and causes it to be used.
streamWebSocket.Control.NoDelay = false;

await streamWebSocket.ConnectAsync(new Uri("wss://echo.websocket.org"));
```

```cppwinrt
Windows::Networking::Sockets::StreamWebSocket streamWebSocket;

// By default, the Nagle algorithm is not used. This overrides that, and causes it to be used.
streamWebSocket.Control().NoDelay(false);

auto connectAsyncAction = streamWebSocket.ConnectAsync(Uri{ L"wss://echo.websocket.org" });
```

```cpp
auto streamWebSocket = ref new Windows::Networking::Sockets::StreamWebSocket();

// By default, the Nagle algorithm is not used. This overrides that, and causes it to be used.
streamWebSocket->Control->NoDelay = false;

auto connectTask = Concurrency::create_task(streamWebSocket->ConnectAsync(ref new Uri(L"wss://echo.websocket.org")));
```

<span data-ttu-id="a265b-175">**Hinweis** Versuchen Sie nicht, eine Steuerelementeigenschaft zu ändern, *nachdem* Sie **ConnectAsync** angerufen haben.</span><span class="sxs-lookup"><span data-stu-id="a265b-175">**Note** Don't try to change a control property *after* you've called **ConnectAsync**.</span></span> <span data-ttu-id="a265b-176">Die einzige Ausnahme von dieser Regel ist [MessageWebSocketControl.MessageType](/uwp/api/windows.networking.sockets.messagewebsocketcontrol.MessageType).</span><span class="sxs-lookup"><span data-stu-id="a265b-176">The only exception to that rule is [MessageWebSocketControl.MessageType](/uwp/api/windows.networking.sockets.messagewebsocketcontrol.MessageType).</span></span>

## <a name="websocket-information-classes"></a><span data-ttu-id="a265b-177">WebSocket-Informationsklassen</span><span class="sxs-lookup"><span data-stu-id="a265b-177">WebSocket information classes</span></span>
<span data-ttu-id="a265b-178">[**MessageWebSocket**](/uwp/api/windows.networking.sockets.messagewebsocket) und [**StreamWebSocket**](/uwp/api/windows.networking.sockets.streamwebsocket) besitzen jeweils eine entsprechende Klasse, die zusätzliche Informationen über das Objekt bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="a265b-178">[**MessageWebSocket**](/uwp/api/windows.networking.sockets.messagewebsocket) and [**StreamWebSocket**](/uwp/api/windows.networking.sockets.streamwebsocket) each have a corresponding class that provides additional information about the object.</span></span>

<span data-ttu-id="a265b-179">[**MessageWebSocketInformation**](/uwp/api/windows.networking.sockets.messagewebsocketinformation) enthält Informationen zu einem **MessageWebSocket**, und Sie rufen eine seiner Instanzen mit der [**MessageWebSocket.Information**](/uwp/api/windows.networking.sockets.messagewebsocket.Information)-Eigenschaft ab.</span><span class="sxs-lookup"><span data-stu-id="a265b-179">[**MessageWebSocketInformation**](/uwp/api/windows.networking.sockets.messagewebsocketinformation) provides information about a **MessageWebSocket**, and you retrieve an instance of it using the [**MessageWebSocket.Information**](/uwp/api/windows.networking.sockets.messagewebsocket.Information) property.</span></span>

<span data-ttu-id="a265b-180">[**StreamWebSocketInformation**](/uwp/api/Windows.Networking.Sockets.StreamWebSocketInformation) enthält Informationen zu einem **StreamWebSocket**, und Sie rufen eine seiner Instanzen mit der [**StreamWebSocket.Information**](/uwp/api/Windows.Networking.Sockets.StreamWebSocket.Information)-Eigenschaft ab.</span><span class="sxs-lookup"><span data-stu-id="a265b-180">[**StreamWebSocketInformation**](/uwp/api/Windows.Networking.Sockets.StreamWebSocketInformation) provides information about a **StreamWebSocket**, and you retrieve an instance of it using the [**StreamWebSocket.Information**](/uwp/api/Windows.Networking.Sockets.StreamWebSocket.Information) property.</span></span>

<span data-ttu-id="a265b-181">Beachten Sie, dass die Eigenschaften für diese Informationsklassen schreibgeschützt sind, Sie können Sie jedoch verwenden, um Informationen zu einem beliebigen Zeitpunkt während der Lebensdauer eines Websocket-Objekts abzurufen.</span><span class="sxs-lookup"><span data-stu-id="a265b-181">Note that the properties on these information classes are read-only, but you can use them to retrieve information at any time during the lifetime of a web socket object.</span></span>

## <a name="handling-exceptions"></a><span data-ttu-id="a265b-182">Behandeln von Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="a265b-182">Handling exceptions</span></span>
<span data-ttu-id="a265b-183">Ein Fehler in einem [**MessageWebSocket**](/uwp/api/Windows.Networking.Sockets.MessageWebSocket)- oder [**StreamWebSocket**](/uwp/api/Windows.Networking.Sockets.StreamWebSocket)-Vorgang wird als **HRESULT**-Wert zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a265b-183">An error encountered on a [**MessageWebSocket**](/uwp/api/Windows.Networking.Sockets.MessageWebSocket) or [**StreamWebSocket**](/uwp/api/Windows.Networking.Sockets.StreamWebSocket) operation is returned as an **HRESULT** value.</span></span> <span data-ttu-id="a265b-184">Sie können diesen **HRESULT**-Wert der [**WebSocketError.GetStatus**](/uwp/api/windows.networking.sockets.websocketerror.getstatus) -Methode übergeben, um ihn in einen [**WebErrorStatus**](/uwp/api/Windows.Web.WebErrorStatus)-Enumerationswert zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="a265b-184">You can pass that **HRESULT** value to the [**WebSocketError.GetStatus**](/uwp/api/windows.networking.sockets.websocketerror.getstatus) method to convert it into a [**WebErrorStatus**](/uwp/api/Windows.Web.WebErrorStatus) enumeration value.</span></span>

<span data-ttu-id="a265b-185">Die meisten **WebErrorStatus**-Enumerationswerte entsprechen einem vom systemeigenen HTTP-Clientvorgang zurückgegebenen Fehler.</span><span class="sxs-lookup"><span data-stu-id="a265b-185">Most **WebErrorStatus** enumeration values correspond to an error returned by the native HTTP client operation.</span></span> <span data-ttu-id="a265b-186">Ihre App kann **WebErrorStatus**-Enumerationswerte einschalten, um das App-Verhalten je nach Ausnahmeursache zu ändern.</span><span class="sxs-lookup"><span data-stu-id="a265b-186">Your app can switch on **WebErrorStatus** enumeration values to modify app behavior depending on the cause of the exception.</span></span>

<span data-ttu-id="a265b-187">Bei Parameterprüfungsfehlern können Sie den **HRESULT**-Wert aus der Ausnahme verwenden, um ausführlichere Informationen zum Fehler zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a265b-187">For parameter validation errors, you can use the **HRESULT** from the exception to learn more detailed information about the error.</span></span> <span data-ttu-id="a265b-188">Mögliche **HRESULT**-Werte sind in `Winerror.h` aufgelistet; dies finden Sie in Ihrer SDK-Installation (z.B. im Ordner `C:\Program Files (x86)\Windows Kits\10\Include\<VERSION>\shared`).</span><span class="sxs-lookup"><span data-stu-id="a265b-188">Possible **HRESULT** values are listed in `Winerror.h`, which can be found in your SDK installation (for example, in the folder `C:\Program Files (x86)\Windows Kits\10\Include\<VERSION>\shared`).</span></span> <span data-ttu-id="a265b-189">Für die meisten Parameterüberprüfungsfehler wird der **HRESULT**-Wert **E_INVALIDARG** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a265b-189">For most parameter validation errors, the **HRESULT** returned is **E_INVALIDARG**.</span></span>

## <a name="setting-timeouts-on-websocket-operations"></a><span data-ttu-id="a265b-190">Festlegen von Timeouts für WebSocket-Vorgänge</span><span class="sxs-lookup"><span data-stu-id="a265b-190">Setting timeouts on WebSocket operations</span></span>
<span data-ttu-id="a265b-191">**MessageWebSocket** und **StreamWebSocket** verwenden einen internen Systemdienst, um WebSocket-Clientanforderungen zu senden und Antworten von einem Server zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="a265b-191">**MessageWebSocket** and **StreamWebSocket** use an internal system service to send WebSocket client requests, and to receive responses from a server.</span></span> <span data-ttu-id="a265b-192">Der standardmäßige Timeoutwert, der für einen WebSocket-Verbindungsvorgang verwendet wird, beträgt 60Sekunden.</span><span class="sxs-lookup"><span data-stu-id="a265b-192">The default timeout value used for a WebSocket connect operation is 60 seconds.</span></span> <span data-ttu-id="a265b-193">Wenn der HTTP-Server, der WebSockets unterstützt, nicht auf die WebSocket-Verbindungsanforderung antwortet oder antworten kann (er ist vorübergehend nicht verfügbar oder durch einen Netzwerkausfall blockiert), wartet der interne Systemdienst die standardmäßig festgelegten 60Sekunden ab, bevor ein Fehler zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a265b-193">If the HTTP server that supports WebSockets doesn't or can't respond to the WebSocket connection request (it's temporarily down, or blocked by a network outage), then the internal system service waits the default 60 seconds before it returns an error.</span></span> <span data-ttu-id="a265b-194">Dieser Fehler führt dazu, dass eine Ausnahme in der WebSocket **ConnectAsync**-Methode ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="a265b-194">That error causes an exception to be thrown on the WebSocket **ConnectAsync** method.</span></span> <span data-ttu-id="a265b-195">Das Standardtimeout, das für Sende- und Empfangsvorgänge nach dem Herstellen einer WebSocket-Verbindung verwendet wird, beträgt 30Sekunden.</span><span class="sxs-lookup"><span data-stu-id="a265b-195">For send and receive operations after a WebSocket connection has been established, the default timeout is 30 seconds.</span></span>

<span data-ttu-id="a265b-196">Falls die Namensabfrage für einen HTTP-Servernamen im URI mehrere IP-Adressen für den Namen zurückgibt, testet der interne Systemdienst bis zu fünf IP-Adressen für die Website. Dabei wird jeweils das Standardtimeout von 60Sekunden eingehalten, bevor ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="a265b-196">If the name query for an HTTP server name in the URI returns multiple IP addresses for the name, then the internal system service tries up to 5 IP addresses for the site (each with a default timeout of 60 seconds) before it fails.</span></span> <span data-ttu-id="a265b-197">Folglich ist es möglich, dass Ihre App mehrere Minuten lang versucht, sich mit mehreren IP-Adressen zu verbinden, bevor eine Ausnahme behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="a265b-197">Consequently, your app could wait several minutes trying to connect to multiple IP addresses before it handles an exception.</span></span> <span data-ttu-id="a265b-198">Dieses Verhalten könnte für Benutzer den Anschein erwecken, als ob die App nicht mehr reagiert.</span><span class="sxs-lookup"><span data-stu-id="a265b-198">This behavior might appear to the user like the app has stopped working.</span></span> 

<span data-ttu-id="a265b-199">Damit Ihre App besser reagiert und diese Probleme minimiert werden, können Sie für Verbindungsanforderungen ein kürzeres Timeout festlegen.</span><span class="sxs-lookup"><span data-stu-id="a265b-199">To make your app more responsive and minimize these issues, you can set a shorter timeout on connection requests.</span></span> <span data-ttu-id="a265b-200">Ein Timeout wird für **MessageWebSocket** und **StreamWebSocket** auf ähnliche Weise festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a265b-200">You set a timeout in a similar way for both **MessageWebSocket** and **StreamWebSocket**.</span></span>

```csharp
private Windows.Networking.Sockets.MessageWebSocket messageWebSocket;

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    this.messageWebSocket = new Windows.Networking.Sockets.MessageWebSocket();

    try
    {
        var cancellationTokenSource = new CancellationTokenSource();
        var connectTask = this.messageWebSocket.ConnectAsync(new Uri("wss://echo.websocket.org")).AsTask(cancellationTokenSource.Token);

        // Cancel connectTask after 5 seconds.
        cancellationTokenSource.CancelAfter(TimeSpan.FromMilliseconds(5000));

        connectTask.ContinueWith((antecedent) =>
        {
            if (antecedent.Status == TaskStatus.RanToCompletion)
            {
                // connectTask ran to completion, so we know that the MessageWebSocket is connected.
                // Add additional code here to use the MessageWebSocket.
            }
            else
            {
                // connectTask timed out, or faulted.
            }
        });
    }
    catch (Exception ex)
    {
        Windows.Web.WebErrorStatus webErrorStatus = Windows.Networking.Sockets.WebSocketError.GetStatus(ex.GetBaseException().HResult);
        // Add additional code here to handle exceptions.
    }
}
```

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.UI.Xaml.Navigation.h>
#include <sstream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::MessageWebSocket m_messageWebSocket;

    IAsyncAction TimeoutAsync()
    {
        // Return control to the caller, and resume again to complete the async action after the timeout period.
        // 5 seconds, in this example.
        co_await(std::chrono::seconds{ 5 });
    }

public:
    IAsyncAction OnNavigatedTo(NavigationEventArgs /* e */)
    {
        try
        {
            // Return control to the caller, and then immediately resume on a thread pool thread.
            co_await winrt::resume_background();

            auto connectAsyncAction = m_messageWebSocket.ConnectAsync(Uri{ L"wss://echo.websocket.org" });

            TimeoutAsync().Completed([connectAsyncAction](IAsyncAction const& sender, AsyncStatus const)
            {
                // TimeoutAsync completes after the timeout period. After that period, it's safe
                // to cancel the ConnectAsync action even if it has already completed.
                connectAsyncAction.Cancel();
            });

            try
            {
                // Block until the ConnectAsync action completes or is canceled.
                connectAsyncAction.get();
            }
            catch (winrt::hresult_error const& ex)
            {
                std::wstringstream wstringstream;
                wstringstream << L"ConnectAsync threw an exception: " << ex.message().c_str() << std::endl;
                ::OutputDebugString(wstringstream.str().c_str());
            }

            if (connectAsyncAction.Status() == AsyncStatus::Completed)
            {
                // connectTask ran to completion, so we know that the MessageWebSocket is connected.
                // Add additional code here to use the MessageWebSocket.
            }
            else
            {
                // connectTask did not run to completion.
            }
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus{ Windows::Networking::Sockets::WebSocketError::GetStatus(ex.to_abi()) };
            // Add additional code here to handle exceptions.
        }
    }
```

```cpp
#include <agents.h>
#include <ppltasks.h>
#include <sstream>
...
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::MessageWebSocket^ messageWebSocket;

protected:
    virtual void OnNavigatedTo(NavigationEventArgs^ e) override
    {
        this->messageWebSocket = ref new Windows::Networking::Sockets::MessageWebSocket();

        try
        {
            Concurrency::cancellation_token_source cancellationTokenSource;
            Concurrency::cancellation_token cancellationToken = cancellationTokenSource.get_token();

            auto connectTask = Concurrency::create_task(this->messageWebSocket->ConnectAsync(ref new Uri(L"wss://echo.websocket.org")), cancellationToken);

            // This continuation task returns true should connectTask run to completion.
            Concurrency::task< bool > taskRanToCompletion = connectTask.then([](void)
            {
                return true;
            });

            // This task returns false after the specified timeout. 5 seconds, in this example.
            Concurrency::task< bool > taskTimedout = Concurrency::create_task([]() -> bool
            {
                Concurrency::task_completion_event< void > taskCompletionEvent;

                // A call object that sets the task completion event.
                auto call = std::make_shared< Concurrency::call< int > >([taskCompletionEvent](int)
                {
                    taskCompletionEvent.set();
                });

                // A non-repeating timer that calls the call object when the timer fires.
                auto nonRepeatingTimer = std::make_shared< Concurrency::timer < int > >(5000, 0, call.get(), false);
                nonRepeatingTimer->start();

                // A task that completes after the completion event is set.
                Concurrency::task< void > taskWaitForCompletionEvent(taskCompletionEvent);

                return taskWaitForCompletionEvent.then([]() {return false; }).get();
            });

            (taskRanToCompletion || taskTimedout).then([this, cancellationTokenSource](bool connectTaskRanToCompletion)
            {
                if (connectTaskRanToCompletion)
                {
                    // connectTask ran to completion, so we know that the MessageWebSocket is connected.
                    // Add additional code here to use the MessageWebSocket.
                }
                else
                {
                    // taskTimedout ran to completion, so we should cancel connectTask via the cancellation_token_source.
                    cancellationTokenSource.cancel();
                }
            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Web::WebErrorStatus webErrorStatus = Windows::Networking::Sockets::WebSocketError::GetStatus(ex->HResult);
            // Add additional code here to handle exceptions.
        }
    }
```

## <a name="important-apis"></a><span data-ttu-id="a265b-201">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="a265b-201">Important APIs</span></span>
* [<span data-ttu-id="a265b-202">DataReader</span><span class="sxs-lookup"><span data-stu-id="a265b-202">DataReader</span></span>](/uwp/api/Windows.Storage.Streams.DataReader)
* [<span data-ttu-id="a265b-203">DataWriter</span><span class="sxs-lookup"><span data-stu-id="a265b-203">DataWriter</span></span>](/uwp/api/Windows.Storage.Streams.DataWriter)
* [<span data-ttu-id="a265b-204">DataWriter.DetachStream</span><span class="sxs-lookup"><span data-stu-id="a265b-204">DataWriter.DetachStream</span></span>](/uwp/api/windows.storage.streams.datawriter.DetachStream)
* [<span data-ttu-id="a265b-205">MessageWebSocket</span><span class="sxs-lookup"><span data-stu-id="a265b-205">MessageWebSocket</span></span>](/uwp/api/windows.networking.sockets.messagewebsocket)
* [<span data-ttu-id="a265b-206">MessageWebSocket.Closed</span><span class="sxs-lookup"><span data-stu-id="a265b-206">MessageWebSocket.Closed</span></span>](/uwp/api/Windows.Networking.Sockets.MessageWebSocket.Closed)
* [<span data-ttu-id="a265b-207">MessageWebSocket.ConnectAsync</span><span class="sxs-lookup"><span data-stu-id="a265b-207">MessageWebSocket.ConnectAsync</span></span>](/uwp/api/windows.networking.sockets.messagewebsocket.connectasync)
* [<span data-ttu-id="a265b-208">MessageWebSocket.Control</span><span class="sxs-lookup"><span data-stu-id="a265b-208">MessageWebSocket.Control</span></span>](/uwp/api/windows.networking.sockets.messagewebsocket.control)
* [<span data-ttu-id="a265b-209">MessageWebSocket.Information</span><span class="sxs-lookup"><span data-stu-id="a265b-209">MessageWebSocket.Information</span></span>](/uwp/api/Windows.Networking.Sockets.MessageWebSocket.Information)
* [<span data-ttu-id="a265b-210">MessageWebSocket.MessageReceived</span><span class="sxs-lookup"><span data-stu-id="a265b-210">MessageWebSocket.MessageReceived</span></span>](/uwp/api/Windows.Networking.Sockets.MessageWebSocket.MessageReceived)
* [<span data-ttu-id="a265b-211">MessageWebSocket.OutputStream</span><span class="sxs-lookup"><span data-stu-id="a265b-211">MessageWebSocket.OutputStream</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.MessageWebSocket.OutputStream)
* [<span data-ttu-id="a265b-212">MessageWebSocketControl</span><span class="sxs-lookup"><span data-stu-id="a265b-212">MessageWebSocketControl</span></span>](/uwp/api/Windows.Networking.Sockets.MessageWebSocketControl)
* [<span data-ttu-id="a265b-213">MessageWebSocketControl.MessageType</span><span class="sxs-lookup"><span data-stu-id="a265b-213">MessageWebSocketControl.MessageType</span></span>](/uwp/api/Windows.Networking.Sockets.MessageWebSocketControl.MessageType)
* [<span data-ttu-id="a265b-214">MessageWebSocketInformation</span><span class="sxs-lookup"><span data-stu-id="a265b-214">MessageWebSocketInformation</span></span>](/uwp/api/Windows.Networking.Sockets.MessageWebSocketInformation)
* [<span data-ttu-id="a265b-215">MessageWebSocketMessageReceivedEventArgs</span><span class="sxs-lookup"><span data-stu-id="a265b-215">MessageWebSocketMessageReceivedEventArgs</span></span>](/uwp/api/Windows.Networking.Sockets.MessageWebSocketMessageReceivedEventArgs)
* [<span data-ttu-id="a265b-216">SocketMessageType</span><span class="sxs-lookup"><span data-stu-id="a265b-216">SocketMessageType</span></span>](/uwp/api/windows.networking.sockets.socketmessagetype)
* [<span data-ttu-id="a265b-217">StreamWebSocket</span><span class="sxs-lookup"><span data-stu-id="a265b-217">StreamWebSocket</span></span>](/uwp/api/Windows.Networking.Sockets.StreamWebSocket)
* [<span data-ttu-id="a265b-218">StreamWebSocket.Closed</span><span class="sxs-lookup"><span data-stu-id="a265b-218">StreamWebSocket.Closed</span></span>](/uwp/api/Windows.Networking.Sockets.StreamWebSocket.Closed)
* [<span data-ttu-id="a265b-219">StreamSocket.ConnectAsync</span><span class="sxs-lookup"><span data-stu-id="a265b-219">StreamSocket.ConnectAsync</span></span>](/uwp/api/windows.networking.sockets.streamsocket.connectasync)
* [<span data-ttu-id="a265b-220">StreamWebSocket.Control</span><span class="sxs-lookup"><span data-stu-id="a265b-220">StreamWebSocket.Control</span></span>](/uwp/api/windows.networking.sockets.streamwebsocket.control)
* [<span data-ttu-id="a265b-221">StreamWebSocket.Information</span><span class="sxs-lookup"><span data-stu-id="a265b-221">StreamWebSocket.Information</span></span>](/uwp/api/windows.networking.sockets.streamwebsocket.Information)
* [<span data-ttu-id="a265b-222">StreamWebSocket.InputStream</span><span class="sxs-lookup"><span data-stu-id="a265b-222">StreamWebSocket.InputStream</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.StreamWebSocket.InputStream)
* [<span data-ttu-id="a265b-223">StreamWebSocket.OutputStream</span><span class="sxs-lookup"><span data-stu-id="a265b-223">StreamWebSocket.OutputStream</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.Networking.Sockets.StreamWebSocket.OutputStream)
* [<span data-ttu-id="a265b-224">StreamWebSocketControl</span><span class="sxs-lookup"><span data-stu-id="a265b-224">StreamWebSocketControl</span></span>](/uwp/api/Windows.Networking.Sockets.StreamWebSocketControl)
* [<span data-ttu-id="a265b-225">StreamWebSocketInformation</span><span class="sxs-lookup"><span data-stu-id="a265b-225">StreamWebSocketInformation</span></span>](/uwp/api/Windows.Networking.Sockets.StreamWebSocketInformation)
* [<span data-ttu-id="a265b-226">WebErrorStatus</span><span class="sxs-lookup"><span data-stu-id="a265b-226">WebErrorStatus</span></span>](/uwp/api/Windows.Web.WebErrorStatus) 
* [<span data-ttu-id="a265b-227">WebSocketError.GetStatus</span><span class="sxs-lookup"><span data-stu-id="a265b-227">WebSocketError.GetStatus</span></span>](/uwp/api/windows.networking.sockets.websocketerror.getstatus)
* [<span data-ttu-id="a265b-228">Windows.Networking.Sockets</span><span class="sxs-lookup"><span data-stu-id="a265b-228">Windows.Networking.Sockets</span></span>](/uwp/api/Windows.Networking.Sockets)

## <a name="related-topics"></a><span data-ttu-id="a265b-229">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a265b-229">Related topics</span></span>
* [<span data-ttu-id="a265b-230">WebSocket-Protokoll</span><span class="sxs-lookup"><span data-stu-id="a265b-230">WebSocket Protocol</span></span>](http://tools.ietf.org/html/rfc6455)
* [<span data-ttu-id="a265b-231">Sockets</span><span class="sxs-lookup"><span data-stu-id="a265b-231">Sockets</span></span>](sockets.md)

## <a name="samples"></a><span data-ttu-id="a265b-232">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a265b-232">Samples</span></span>
* [<span data-ttu-id="a265b-233">WebSocket-Beispiel</span><span class="sxs-lookup"><span data-stu-id="a265b-233">WebSocket sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620623)
