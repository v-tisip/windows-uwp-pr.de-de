---
description: Sockets sind eine einfache Datenübertragungstechnologie, auf der viele Netzwerkprotokolle implementiert sind. UWP bietet TCP- und UDP-Socketklassen für Client-Server oder Peer-to-Peer-Anwendungen, unabhängig davon, ob Verbindungen langlebig sind oder keine bestehende Verbindung erforderlich ist.
title: Sockets
ms.assetid: 23B10A3C-E33F-4CD6-92CB-0FFB491472D6
ms.date: 06/03/2018
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7d75afd17d5aa7edf64fda36b3a35b3a101c1d89
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7847787"
---
# <a name="sockets"></a><span data-ttu-id="ba98d-105">Sockets</span><span class="sxs-lookup"><span data-stu-id="ba98d-105">Sockets</span></span>
<span data-ttu-id="ba98d-106">Sockets sind eine einfache Datenübertragungstechnologie, auf der viele Netzwerkprotokolle implementiert sind.</span><span class="sxs-lookup"><span data-stu-id="ba98d-106">Sockets are a low-level data transfer technology on top of which many networking protocols are implemented.</span></span> <span data-ttu-id="ba98d-107">UWP bietet TCP- und UDP-Socketklassen für Client-Server oder Peer-to-Peer-Anwendungen, unabhängig davon, ob Verbindungen langlebig sind oder keine bestehende Verbindung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="ba98d-107">UWP offers TCP and UDP socket classes for client-server or peer-to-peer applications, whether connections are long-lived or an established connection is not required.</span></span>

<span data-ttu-id="ba98d-108">In diesem Thema geht es um die Verwendung der UWP (Universelle Windows-Plattform)-Socketklassen im [**Windows.Networking.Sockets**](/uwp/api/Windows.Networking.Sockets)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="ba98d-108">This topic focuses on how to use the Universal Windows Platform (UWP) socket classes that are in the [**Windows.Networking.Sockets**](/uwp/api/Windows.Networking.Sockets) namespace.</span></span> <span data-ttu-id="ba98d-109">Sie können jedoch auch [Windows Sockets 2 (Winsock)](https://msdn.microsoft.com/library/windows/desktop/ms740673) in einer UWP-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="ba98d-109">But you can also use [Windows Sockets 2 (Winsock)](https://msdn.microsoft.com/library/windows/desktop/ms740673) in a UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="ba98d-110">Aufgrund der [Netzwerkisolation](https://msdn.microsoft.com/library/windows/apps/hh770532.aspx) lässt Windows die Einrichtung einer Socketverbindung (Sockets oder WinSock) zwischen zwei UWP-Apps, die auf demselben Computer ausgeführt werden, weder über die lokale Loopbackadresse (127.0.0.0), noch durch explizite Angabe der lokalen IP-Adresse zu.</span><span class="sxs-lookup"><span data-stu-id="ba98d-110">As a consequence of [network isolation](https://msdn.microsoft.com/library/windows/apps/hh770532.aspx), Windows disallows establishing a socket connection (Sockets or WinSock) between two UWP apps running on the same machine; whether that's via the local loopback address (127.0.0.0), or by explicitly specifying the local IP address.</span></span> <span data-ttu-id="ba98d-111">Einzelheiten zu Mechanismen, mit denen UWP-Apps miteinander kommunizieren können, finden Sie unter [App-zu-App-Kommunikation](/windows/uwp/app-to-app/index).</span><span class="sxs-lookup"><span data-stu-id="ba98d-111">For details about mechanisms by which UWP apps can communicate with one another, see [App-to-app communication](/windows/uwp/app-to-app/index).</span></span>

## <a name="build-a-basic-tcp-socket-client-and-server"></a><span data-ttu-id="ba98d-112">Erstellen eines grundlegenden TCP-Socket-Clients und -Servers</span><span class="sxs-lookup"><span data-stu-id="ba98d-112">Build a basic TCP socket client and server</span></span>
<span data-ttu-id="ba98d-113">Ein TCP (Transmission Control Protocol)-Socket ermöglicht einfache Übertragungen von Netzwerkdaten in beide Richtungen für langlebige Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="ba98d-113">A TCP (Transmission Control Protocol) socket provides low-level network data transfers in either direction for connections that are long-lived.</span></span> <span data-ttu-id="ba98d-114">TCP-Sockets sind das zugrunde liegende Feature, das von den meisten im Internet genutzten Netzwerkprotokollen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ba98d-114">TCP sockets are the underlying feature used by most of the network protocols used on the Internet.</span></span> <span data-ttu-id="ba98d-115">Zur Veranschaulichung von grundlegenden TCP-Vorgängen zeigt der folgende Beispielcode, wie ein [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket) und ein [**StreamSocketListener**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener) Daten über TCP senden und empfangen, um einen Echo-Client und -Server zu bilden.</span><span class="sxs-lookup"><span data-stu-id="ba98d-115">To demonstrate basic TCP operations, the example code below shows a [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket) and a [**StreamSocketListener**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener) sending and receiving data over TCP to form an echo client and server.</span></span>

<span data-ttu-id="ba98d-116">Um mit möglichst wenigen Aspekten zu beginnen&mdash;und um Netzwerkisolationsprobleme vorerst zu umgehen&mdash;erstellen Sie ein neues Projekt und fügen Sie den nachstehenden Client- und Servercode in dasselbe Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="ba98d-116">To begin with as few moving parts as possible&mdash;and to sidestep network isolation issues for the present&mdash;create a new project, and put both the client and the server code below into the same project.</span></span>

<span data-ttu-id="ba98d-117">Sie müssen in Ihrem Projekt [eine App-Funktion](../packaging/app-capability-declarations.md) deklarieren.</span><span class="sxs-lookup"><span data-stu-id="ba98d-117">You'll need to [declare an app capability](../packaging/app-capability-declarations.md) in your project.</span></span> <span data-ttu-id="ba98d-118">Öffnen Sie die Quelldatei des App-Paketmanifests (die Datei `Package.appxmanifest`), und aktivieren Sie auf der Registerkarte „Funktionen” die Option **Private Netzwerke (Client und Server)**.</span><span class="sxs-lookup"><span data-stu-id="ba98d-118">Open your app package manifest source file (the `Package.appxmanifest` file) and, on the Capabilities tab, check **Private Networks (Client & Server)**.</span></span> <span data-ttu-id="ba98d-119">So sieht es im `Package.appxmanifest`-Markup aus.</span><span class="sxs-lookup"><span data-stu-id="ba98d-119">This is how that looks in the `Package.appxmanifest` markup.</span></span>

```xml
<Capability Name="privateNetworkClientServer" />
```

<span data-ttu-id="ba98d-120">Anstelle von `privateNetworkClientServer` können Sie `internetClientServer` deklarieren, wenn Sie eine Verbindung über das Internet herstellen.</span><span class="sxs-lookup"><span data-stu-id="ba98d-120">Instead of `privateNetworkClientServer`, you can declare `internetClientServer` if you're connecting over the internet.</span></span> <span data-ttu-id="ba98d-121">Irgendeine dieser App-Funktionen muss sowohl für **StreamSocket** als auch für **StreamSocketListener** deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="ba98d-121">Both **StreamSocket** and **StreamSocketListener** need one or other of these app capabilities to be declared.</span></span>

### <a name="an-echo-client-and-server-using-tcp-sockets"></a><span data-ttu-id="ba98d-122">TCP-Socket-basierte Echo-Clients und -Server</span><span class="sxs-lookup"><span data-stu-id="ba98d-122">An echo client and server, using TCP sockets</span></span>
<span data-ttu-id="ba98d-123">Erstellen Sie einen [**StreamSocketListener**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener) und beginnen Sie mit dem Überwachen eingehender TCP-Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="ba98d-123">Construct a [**StreamSocketListener**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener) and begin listening for incoming TCP connections.</span></span> <span data-ttu-id="ba98d-124">Das [**StreamSocketListener.ConnectionReceived**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener.ConnectionReceived)-Ereignis wird jedes Mal ausgelöst, wenn ein Client eine Verbindung mit dem **StreamSocketListener** herstellt.</span><span class="sxs-lookup"><span data-stu-id="ba98d-124">The [**StreamSocketListener.ConnectionReceived**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener.ConnectionReceived) event is raised each time a client establishes a connection with the **StreamSocketListener**.</span></span>

<span data-ttu-id="ba98d-125">Erstellen Sie desweiteren einen [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket), stellen Sie eine Verbindung mit dem Server her, senden Sie eine Anforderung und empfangen Sie eine Antwort.</span><span class="sxs-lookup"><span data-stu-id="ba98d-125">Also construct a [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket), establish a connection to the server, send a request, and receive a response.</span></span>

<span data-ttu-id="ba98d-126">Erstellen Sie eine neue **Seite** namens `StreamSocketAndListenerPage`.</span><span class="sxs-lookup"><span data-stu-id="ba98d-126">Create a new **Page** named `StreamSocketAndListenerPage`.</span></span> <span data-ttu-id="ba98d-127">Fügen Sie das XAML-Markup in `StreamSocketAndListenerPage.xaml` ein, und stellen Sie dann den imperativen Code innerhalb der `StreamSocketAndListenerPage`-Klasse bereit.</span><span class="sxs-lookup"><span data-stu-id="ba98d-127">Put the XAML markup in `StreamSocketAndListenerPage.xaml`, and the put the imperative code inside the `StreamSocketAndListenerPage` class.</span></span>

```XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>

    <StackPanel>
        <TextBlock Margin="9.6,0" Style="{StaticResource TitleTextBlockStyle}" Text="TCP socket example"/>
        <TextBlock Margin="7.2,0,0,0" Style="{StaticResource HeaderTextBlockStyle}" Text="StreamSocket &amp; StreamSocketListener"/>
    </StackPanel>

    <Grid Grid.Row="1">
        <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*"/>
            <ColumnDefinition Width="*"/>
        </Grid.ColumnDefinitions>
        <TextBlock Margin="9.6" Style="{StaticResource SubtitleTextBlockStyle}" Text="client"/>
        <ListBox x:Name="clientListBox" Grid.Row="1" Margin="9.6"/>
        <TextBlock Grid.Column="1" Margin="9.6" Style="{StaticResource SubtitleTextBlockStyle}" Text="server"/>
        <ListBox x:Name="serverListBox" Grid.Column="1" Grid.Row="1" Margin="9.6"/>
    </Grid>
</Grid>
```

```csharp
// Every protocol typically has a standard port number. For example, HTTP is typically 80, FTP is 20 and 21, etc.
// For this example, we'll choose an arbitrary port number.
static string PortNumber = "1337";

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    this.StartServer();
    this.StartClient();
}

private async void StartServer()
{
    try
    {
        var streamSocketListener = new Windows.Networking.Sockets.StreamSocketListener();

        // The ConnectionReceived event is raised when connections are received.
        streamSocketListener.ConnectionReceived += this.StreamSocketListener_ConnectionReceived;

        // Start listening for incoming TCP connections on the specified port. You can specify any port that's not currently in use.
        await streamSocketListener.BindServiceNameAsync(StreamSocketAndListenerPage.PortNumber);

        this.serverListBox.Items.Add("server is listening...");
    }
    catch (Exception ex)
    {
        Windows.Networking.Sockets.SocketErrorStatus webErrorStatus = Windows.Networking.Sockets.SocketError.GetStatus(ex.GetBaseException().HResult);
        this.serverListBox.Items.Add(webErrorStatus.ToString() != "Unknown" ? webErrorStatus.ToString() : ex.Message);
    }
}

private async void StreamSocketListener_ConnectionReceived(Windows.Networking.Sockets.StreamSocketListener sender, Windows.Networking.Sockets.StreamSocketListenerConnectionReceivedEventArgs args)
{
    string request;
    using (var streamReader = new StreamReader(args.Socket.InputStream.AsStreamForRead()))
    {
        request = await streamReader.ReadLineAsync();
    }

    await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () => this.serverListBox.Items.Add(string.Format("server received the request: \"{0}\"", request)));

    // Echo the request back as the response.
    using (Stream outputStream = args.Socket.OutputStream.AsStreamForWrite())
    {
        using (var streamWriter = new StreamWriter(outputStream))
        {
            await streamWriter.WriteLineAsync(request);
            await streamWriter.FlushAsync();
        }
    }

    await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () => this.serverListBox.Items.Add(string.Format("server sent back the response: \"{0}\"", request)));

    sender.Dispose();

    await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () => this.serverListBox.Items.Add("server closed its socket"));
}

private async void StartClient()
{
    try
    {
        // Create the StreamSocket and establish a connection to the echo server.
        using (var streamSocket = new Windows.Networking.Sockets.StreamSocket())
        {
            // The server hostname that we will be establishing a connection to. In this example, the server and client are in the same process.
            var hostName = new Windows.Networking.HostName("localhost");

            this.clientListBox.Items.Add("client is trying to connect...");

            await streamSocket.ConnectAsync(hostName, StreamSocketAndListenerPage.PortNumber);

            this.clientListBox.Items.Add("client connected");

            // Send a request to the echo server.
            string request = "Hello, World!";
            using (Stream outputStream = streamSocket.OutputStream.AsStreamForWrite())
            {
                using (var streamWriter = new StreamWriter(outputStream))
                {
                    await streamWriter.WriteLineAsync(request);
                    await streamWriter.FlushAsync();
                }
            }

            this.clientListBox.Items.Add(string.Format("client sent the request: \"{0}\"", request));

            // Read data from the echo server.
            string response;
            using (Stream inputStream = streamSocket.InputStream.AsStreamForRead())
            {
                using (StreamReader streamReader = new StreamReader(inputStream))
                {
                    response = await streamReader.ReadLineAsync();
                }
            }

            this.clientListBox.Items.Add(string.Format("client received the response: \"{0}\" ", response));
        }

        this.clientListBox.Items.Add("client closed its socket");
    }
    catch (Exception ex)
    {
        Windows.Networking.Sockets.SocketErrorStatus webErrorStatus = Windows.Networking.Sockets.SocketError.GetStatus(ex.GetBaseException().HResult);
        this.clientListBox.Items.Add(webErrorStatus.ToString() != "Unknown" ? webErrorStatus.ToString() : ex.Message);
    }
}
```

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.UI.Core.h>
#include <winrt/Windows.UI.Xaml.Navigation.h>
#include <sstream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Core;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::StreamSocketListener m_streamSocketListener;
    Windows::Networking::Sockets::StreamSocket m_streamSocket;

public:
    void OnNavigatedTo(NavigationEventArgs const& /* e */)
    {
        StartServer();
        StartClient();
    }

private:
    IAsyncAction StartServer()
    {
        try
        {
            // The ConnectionReceived event is raised when connections are received.
            m_streamSocketListener.ConnectionReceived({ this, &StreamSocketAndListenerPage::OnConnectionReceived });

            // Start listening for incoming TCP connections on the specified port. You can specify any port that's not currently in use.
            // Every protocol typically has a standard port number. For example, HTTP is typically 80, FTP is 20 and 21, etc.
            // For this example, we'll choose an arbitrary port number.
            co_await m_streamSocketListener.BindServiceNameAsync(L"1337");
            serverListBox().Items().Append(winrt::box_value(L"server is listening..."));
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus{ Windows::Networking::Sockets::SocketError::GetStatus(ex.to_abi()) };
            serverListBox().Items().Append(webErrorStatus != Windows::Networking::Sockets::SocketErrorStatus::Unknown ? winrt::box_value(winrt::to_hstring((int32_t)webErrorStatus)) : winrt::box_value(winrt::to_hstring(ex.to_abi())));
        }
    }

    IAsyncAction OnConnectionReceived(Windows::Networking::Sockets::StreamSocketListener /* sender */, Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs args)
    {
        try
        {
            auto socket{ args.Socket() }; // Keep the socket referenced, and alive.
            DataReader dataReader{ socket.InputStream() };

            unsigned int bytesLoaded = co_await dataReader.LoadAsync(sizeof(unsigned int));

            unsigned int stringLength = dataReader.ReadUInt32();
            bytesLoaded = co_await dataReader.LoadAsync(stringLength);
            winrt::hstring request = dataReader.ReadString(bytesLoaded);

            serverListBox().Dispatcher().RunAsync(CoreDispatcherPriority::Normal, [=]()
            {
                std::wstringstream wstringstream;
                wstringstream << L"server received the request: \"" << request.c_str() << L"\"";
                serverListBox().Items().Append(winrt::box_value(wstringstream.str().c_str()));
            });

            // Echo the request back as the response.
            DataWriter dataWriter{ socket.OutputStream() };
            dataWriter.WriteUInt32(request.size());
            dataWriter.WriteString(request);
            co_await dataWriter.StoreAsync();
            dataWriter.DetachStream();

            serverListBox().Dispatcher().RunAsync(CoreDispatcherPriority::Normal, [=]()
            {
                std::wstringstream wstringstream;
                wstringstream << L"server sent back the response: \"" << request.c_str() << L"\"";
                serverListBox().Items().Append(winrt::box_value(wstringstream.str().c_str()));
            });

            m_streamSocketListener = nullptr;

            serverListBox().Dispatcher().RunAsync(CoreDispatcherPriority::Normal, [=]()
            {
                serverListBox().Items().Append(winrt::box_value(L"server closed its socket"));
            });
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus{ Windows::Networking::Sockets::SocketError::GetStatus(ex.to_abi()) };
            serverListBox().Dispatcher().RunAsync(CoreDispatcherPriority::Normal, [=]()
            {
                serverListBox().Items().Append(webErrorStatus != Windows::Networking::Sockets::SocketErrorStatus::Unknown ? winrt::box_value(winrt::to_hstring((int32_t)webErrorStatus)) : winrt::box_value(winrt::to_hstring(ex.to_abi())));
            });
        }
    }

    IAsyncAction StartClient()
    {
        try
        {
            // Establish a connection to the echo server.

            // The server hostname that we will be establishing a connection to. In this example, the server and client are in the same process.
            Windows::Networking::HostName hostName{ L"localhost" };

            clientListBox().Items().Append(winrt::box_value(L"client is trying to connect..."));

            co_await m_streamSocket.ConnectAsync(hostName, L"1337");
            clientListBox().Items().Append(winrt::box_value(L"client connected"));

            // Send a request to the echo server.
            DataWriter dataWriter{ m_streamSocket.OutputStream() };
            winrt::hstring request{ L"Hello, World!" };
            dataWriter.WriteUInt32(request.size());
            dataWriter.WriteString(request);

            co_await dataWriter.StoreAsync();

            std::wstringstream wstringstream;
            wstringstream << L"client sent the request: \"" << request.c_str() << L"\"";
            clientListBox().Items().Append(winrt::box_value(wstringstream.str().c_str()));

            co_await dataWriter.FlushAsync();
            dataWriter.DetachStream();

            // Read data from the echo server.
            DataReader dataReader{ m_streamSocket.InputStream() };
            unsigned int bytesLoaded = co_await dataReader.LoadAsync(sizeof(unsigned int));
            unsigned int stringLength = dataReader.ReadUInt32();
            bytesLoaded = co_await dataReader.LoadAsync(stringLength);
            winrt::hstring response{ dataReader.ReadString(bytesLoaded) };

            wstringstream.str(L"");
            wstringstream << L"client received the response: \"" << response.c_str() << L"\"";
            clientListBox().Items().Append(winrt::box_value(wstringstream.str().c_str()));

            m_streamSocket = nullptr;

            clientListBox().Items().Append(winrt::box_value(L"client closed its socket"));
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus{ Windows::Networking::Sockets::SocketError::GetStatus(ex.to_abi()) };
            serverListBox().Items().Append(webErrorStatus != Windows::Networking::Sockets::SocketErrorStatus::Unknown ? winrt::box_value(winrt::to_hstring((int32_t)webErrorStatus)) : winrt::box_value(winrt::to_hstring(ex.to_abi())));
        }
    }
```

```cpp
#include <ppltasks.h>
#include <sstream>
...
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Core;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::StreamSocketListener^ streamSocketListener;
    Windows::Networking::Sockets::StreamSocket^ streamSocket;

protected:
    virtual void OnNavigatedTo(NavigationEventArgs^ e) override
    {
        this->StartServer();
        this->StartClient();
    }

private:
    void StartServer()
    {
        try
        {
            this->streamSocketListener = ref new Windows::Networking::Sockets::StreamSocketListener();

            // The ConnectionReceived event is raised when connections are received.
            streamSocketListener->ConnectionReceived += ref new TypedEventHandler<Windows::Networking::Sockets::StreamSocketListener^, Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs^>(this, &StreamSocketAndListenerPage::StreamSocketListener_ConnectionReceived);

            // Start listening for incoming TCP connections on the specified port. You can specify any port that's not currently in use.
            // Every protocol typically has a standard port number. For example, HTTP is typically 80, FTP is 20 and 21, etc.
            // For this example, we'll choose an arbitrary port number.
            Concurrency::create_task(streamSocketListener->BindServiceNameAsync(L"1337")).then(
                [=]
            {
                this->serverListBox->Items->Append(L"server is listening...");
            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus = Windows::Networking::Sockets::SocketError::GetStatus(ex->HResult);
            this->serverListBox->Items->Append(webErrorStatus.ToString() != L"Unknown" ? webErrorStatus.ToString() : ex->Message);
        }
    }

    void StreamSocketListener_ConnectionReceived(Windows::Networking::Sockets::StreamSocketListener^ sender, Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs^ args)
    {
        try
        {
            auto dataReader = ref new DataReader(args->Socket->InputStream);

            Concurrency::create_task(dataReader->LoadAsync(sizeof(unsigned int))).then(
                [=](unsigned int bytesLoaded)
            {
                unsigned int stringLength = dataReader->ReadUInt32();
                Concurrency::create_task(dataReader->LoadAsync(stringLength)).then(
                    [=](unsigned int bytesLoaded)
                {
                    Platform::String^ request = dataReader->ReadString(bytesLoaded);
                    this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler(
                        [=]
                    {
                        std::wstringstream wstringstream;
                        wstringstream << L"server received the request: \"" << request->Data() << L"\"";
                        this->serverListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));
                    }));

                    // Echo the request back as the response.
                    auto dataWriter = ref new DataWriter(args->Socket->OutputStream);
                    dataWriter->WriteUInt32(request->Length());
                    dataWriter->WriteString(request);
                    Concurrency::create_task(dataWriter->StoreAsync()).then(
                        [=](unsigned int)
                    {
                        dataWriter->DetachStream();

                        this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler(
                            [=]()
                        {
                            std::wstringstream wstringstream;
                            wstringstream << L"server sent back the response: \"" << request->Data() << L"\"";
                            this->serverListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));
                        }));

                        delete this->streamSocketListener;
                        this->streamSocketListener = nullptr;

                        this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler([=]() {this->serverListBox->Items->Append(L"server closed its socket"); }));
                    });
                });
            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus = Windows::Networking::Sockets::SocketError::GetStatus(ex->HResult);
            this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler([=]() {this->serverListBox->Items->Append(webErrorStatus.ToString() != L"Unknown" ? webErrorStatus.ToString() : ex->Message); }));
        }
    }

    void StartClient()
    {
        try
        {
            // Create the StreamSocket and establish a connection to the echo server.
            this->streamSocket = ref new Windows::Networking::Sockets::StreamSocket();

            // The server hostname that we will be establishing a connection to. In this example, the server and client are in the same process.
            auto hostName = ref new Windows::Networking::HostName(L"localhost");

            this->clientListBox->Items->Append(L"client is trying to connect...");

            Concurrency::create_task(this->streamSocket->ConnectAsync(hostName, L"1337")).then(
                [=](Concurrency::task< void >)
            {
                this->clientListBox->Items->Append(L"client connected");

                // Send a request to the echo server.
                auto dataWriter = ref new DataWriter(this->streamSocket->OutputStream);
                auto request = ref new Platform::String(L"Hello, World!");
                dataWriter->WriteUInt32(request->Length());
                dataWriter->WriteString(request);

                Concurrency::create_task(dataWriter->StoreAsync()).then(
                    [=](Concurrency::task< unsigned int >)
                {
                    std::wstringstream wstringstream;
                    wstringstream << L"client sent the request: \"" << request->Data() << L"\"";
                    this->clientListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));

                    Concurrency::create_task(dataWriter->FlushAsync()).then(
                        [=](Concurrency::task< bool >)
                    {
                        dataWriter->DetachStream();

                        // Read data from the echo server.
                        auto dataReader = ref new DataReader(this->streamSocket->InputStream);
                        Concurrency::create_task(dataReader->LoadAsync(sizeof(unsigned int))).then(
                            [=](unsigned int bytesLoaded)
                        {
                            unsigned int stringLength = dataReader->ReadUInt32();
                            Concurrency::create_task(dataReader->LoadAsync(stringLength)).then(
                                [=](unsigned int bytesLoaded)
                            {
                                Platform::String^ response = dataReader->ReadString(bytesLoaded);
                                this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler(
                                    [=]
                                {
                                    std::wstringstream wstringstream;
                                    wstringstream << L"client received the response: \"" << response->Data() << L"\"";
                                    this->clientListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));

                                    delete this->streamSocket;
                                    this->streamSocket = nullptr;

                                    this->clientListBox->Items->Append(L"client closed its socket");
                                }));
                            });
                        });
                    });
                });
            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus = Windows::Networking::Sockets::SocketError::GetStatus(ex->HResult);
            this->serverListBox->Items->Append(webErrorStatus.ToString() != L"Unknown" ? webErrorStatus.ToString() : ex->Message);
        }
    }
```

## <a name="references-to-streamsockets-in-c-ppl-continuations-applies-to-ccx-primarily"></a><span data-ttu-id="ba98d-128">Verweise auf StreamSockets in C++ PPL-Fortsetzungen (gilt hauptsächlich für C++/CX)</span><span class="sxs-lookup"><span data-stu-id="ba98d-128">References to StreamSockets in C++ PPL continuations (applies to C++/CX, primarily)</span></span>
> [!NOTE]
> <span data-ttu-id="ba98d-129">Wenn Sie C++/WinRT Coroutinen verwenden und Parameter nach Wert übergeben, gilt dieses Problem nicht.</span><span class="sxs-lookup"><span data-stu-id="ba98d-129">If you use C++/WinRT coroutines, and you pass parameters by value, then this issue doesn't apply.</span></span> <span data-ttu-id="ba98d-130">Empfehlungen zu Parameterübergaben finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency#parameter-passing).</span><span class="sxs-lookup"><span data-stu-id="ba98d-130">For parameter-passing recommendations, see [Concurrency and asynchronous operations with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency#parameter-passing).</span></span>

<span data-ttu-id="ba98d-131">Ein [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket?branch=live) bleibt solange aktiv, bis ein aktiver Lese-/Schreibzugriff auf seinem Ein-/Ausgabedatenstrom vorhanden ist (z.B. das [**StreamSocketListenerConnectionReceivedEventArgs.Socket**](/uwp/api/windows.networking.sockets.streamsocketlistenerconnectionreceivedeventargs.Socket), auf das Sie in Ihrem [**StreamSocketListener.ConnectionReceived**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener.ConnectionReceived)-Ereignishandler zugreifen können).</span><span class="sxs-lookup"><span data-stu-id="ba98d-131">A [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket?branch=live) remains alive as long as there's an active read/write on its input/output stream (let's take for example the [**StreamSocketListenerConnectionReceivedEventArgs.Socket**](/uwp/api/windows.networking.sockets.streamsocketlistenerconnectionreceivedeventargs.Socket) that you have access to in your [**StreamSocketListener.ConnectionReceived**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener.ConnectionReceived) event handler).</span></span> <span data-ttu-id="ba98d-132">Wenn Sie [**DataReader.LoadAsync**](/uwp/api/windows.storage.streams.datareader.loadasync) (oder `ReadAsync/WriteAsync/StoreAsync`) aufrufen, enthält es einen Verweis auf das Socket (über den Eingabedatenstrom des Sockets), bis der **Abschlusshandler** (falls vorhanden) von **LoadAsync** die Ausführung abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="ba98d-132">When you call [**DataReader.LoadAsync**](/uwp/api/windows.storage.streams.datareader.loadasync) (or `ReadAsync/WriteAsync/StoreAsync`), then that holds a reference to the socket (via the socket's input stream) until the **Completed** event handler (if any) of the **LoadAsync** is done executing.</span></span>

<span data-ttu-id="ba98d-133">Standardmäßig werden in der Parallel Patterns Library (PPL) keine Aufgabenfortsetzungen inline geplant.</span><span class="sxs-lookup"><span data-stu-id="ba98d-133">The Parallel Patterns Library (PPL) doesn't schedule task continuations inline by default.</span></span> <span data-ttu-id="ba98d-134">Mit anderen Worten garantiert das Hinzufügen einer Fortsetzungsaufgabe (mit `task::then()`) nicht, dass die Fortsetzungsaufgabe inline als Abschlusshandler ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ba98d-134">In other words, adding a continuation task (with `task::then()`) doesn't guarantee that the continuation task will execute inline as the completion handler.</span></span>

```cpp
void StreamSocketListener_ConnectionReceived(Windows::Networking::Sockets::StreamSocketListener^ sender, Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    auto dataReader = ref new DataReader(args->Socket->InputStream);
    Concurrency::create_task(dataReader->LoadAsync(sizeof(unsigned int))).then(
        [=](unsigned int bytesLoaded)
    {
        // Work in here isn't guaranteed to execute inline as the completion handler of the LoadAsync.
    });
}
```

<span data-ttu-id="ba98d-135">Aus der Perspektive des **StreamSocket** schließt der Abschlusshandler die Ausführung ab bzw. kann der Socket gelöscht werden, bevor der Fortsetzungstext ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ba98d-135">From the perspective of the **StreamSocket**, the completion handler is done executing (and the socket is eligible for disposal) before the continuation body runs.</span></span> <span data-ttu-id="ba98d-136">Um zu verhindern, dass das Socket gelöscht wird, wenn Sie es in dieser Fortsetzung verwenden möchten, müssen Sie entweder direkt auf das Socket verweisen (über Lambda-Capture) und es verwenden, oder indirekt darauf verweisen (indem Sie innerhalb der Fortsetzung weiterhin auf `args->Socket` zugreifen), oder erzwingen, dass die Fortsetzungsaufgaben inline sind.</span><span class="sxs-lookup"><span data-stu-id="ba98d-136">So, to keep your socket from being disposed if you want to use it inside that continuation, you need to either reference the socket directly (via lambda capture) and use it, or indirectly (by continuing to access `args->Socket` inside continuations), or force continuation tasks to be inline.</span></span> <span data-ttu-id="ba98d-137">Im [StreamSocket-Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=620609) sehen Sie die erste Methode (Lambda-Capture) in Aktion.</span><span class="sxs-lookup"><span data-stu-id="ba98d-137">You can see the first technique (lambda capture) in action in the [StreamSocket sample](http://go.microsoft.com/fwlink/p/?LinkId=620609).</span></span> <span data-ttu-id="ba98d-138">Im C++/CX-Code im Abschnitt [Erstellen eines grundlegenden TCP-Socket-Clients und -Servers](#build-a-basic-tcp-socket-client-and-server) oben wird die zweite Methode verwendet&mdash;sie gibt die Anforderung als Antwort zurück und greift auf `args->Socket` von innerhalb der innersten Fortsetzungen zu.</span><span class="sxs-lookup"><span data-stu-id="ba98d-138">The C++/CX code in the [Build a basic TCP socket client and server](#build-a-basic-tcp-socket-client-and-server) section above uses the second technique&mdash;it echoes the request back as a response, and it accesses `args->Socket` from within one of the innermost continuations.</span></span>

<span data-ttu-id="ba98d-139">Die dritte Methode ist geeignet, wenn Sie keine Antwort zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="ba98d-139">The third technique is appropriate when you're not echoing a response back.</span></span> <span data-ttu-id="ba98d-140">Verwenden Sie die `task_continuation_context::use_synchronous_execution()`-Option um zu erzwingen, dass PPL den Fortsetzungstext inline ausführt.</span><span class="sxs-lookup"><span data-stu-id="ba98d-140">You use the `task_continuation_context::use_synchronous_execution()` option to force PPL to execute the continuation body inline.</span></span> <span data-ttu-id="ba98d-141">Dieses Codebeispiel veranschaulicht, wie Sie dies durchführen.</span><span class="sxs-lookup"><span data-stu-id="ba98d-141">Here's a code example showing how to do it.</span></span>

```cpp
void StreamSocketListener_ConnectionReceived(Windows::Networking::Sockets::StreamSocketListener^ sender, Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    auto dataReader = ref new DataReader(args->Socket->InputStream);

    Concurrency::create_task(dataReader->LoadAsync(sizeof(unsigned int))).then(
        [=](unsigned int bytesLoaded)
    {
        unsigned int messageLength = dataReader->ReadUInt32();
        Concurrency::create_task(dataReader->LoadAsync(messageLength)).then(
            [=](unsigned int bytesLoaded)
        {
            Platform::String^ request = dataReader->ReadString(bytesLoaded);
            this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler(
                [=]
            {
                std::wstringstream wstringstream;
                wstringstream << L"server received the request: \"" << request->Data() << L"\"";
                this->serverListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));
            }));
        });
    }, Concurrency::task_continuation_context::use_synchronous_execution());
}
```

<span data-ttu-id="ba98d-142">Dieses Verhalten gilt für alle Sockets und WebSockets-Klassen im [**Windows.Networking.Sockets**](/uwp/api/Windows.Networking.Sockets?branch=live)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="ba98d-142">This behavior applies to all of the sockets and WebSockets classes in the [**Windows.Networking.Sockets**](/uwp/api/Windows.Networking.Sockets?branch=live) namespace.</span></span> <span data-ttu-id="ba98d-143">Bei clientseitigen Szenarien hingegen werden Sockets in Membervariablen gespeichert, daher trifft das Problem am ehesten auf das [**StreamSocketListener.ConnectionReceived**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener.ConnectionReceived)-Szenario zu, wie oben dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ba98d-143">But client-side scenarios usually store sockets in member variables, so the issue is most applicable to the [**StreamSocketListener.ConnectionReceived**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener.ConnectionReceived) scenario, as illustrated above.</span></span>

## <a name="build-a-basic-udp-socket-client-and-server"></a><span data-ttu-id="ba98d-144">Erstellen eines grundlegenden UDP-Socket-Clients und -Servers</span><span class="sxs-lookup"><span data-stu-id="ba98d-144">Build a basic UDP socket client and server</span></span>
<span data-ttu-id="ba98d-145">Ein UDP (User Datagram Protocol)-Socket ähnelt einem TCP-Socket insofern, als es ebenfalls einfache Übertragungen von Netzwerkdaten in beide Richtungen bietet.</span><span class="sxs-lookup"><span data-stu-id="ba98d-145">A UDP (User Datagram Protocol) socket is similar to a TCP socket in that it also provides low-level network data transfers in either direction.</span></span> <span data-ttu-id="ba98d-146">Während jedoch ein TCP-Socket für langlebige Verbindungen vorgesehen ist, ist ein UDP-Socket für Anwendungen konzipiert, für die keine bestehende Verbindung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="ba98d-146">But, while a TCP socket is for long-lived connections, a UDP socket is for applications where an established connection is not required.</span></span> <span data-ttu-id="ba98d-147">Da UDP-Sockets keine Verbindung auf beiden Endpunkten aufrechterhalten, stellen Sie eine schnelle und einfache Lösung für Netzwerkverbindungen zwischen Remotecomputern dar.</span><span class="sxs-lookup"><span data-stu-id="ba98d-147">Because UDP sockets don't maintain connection on both endpoints, they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="ba98d-148">Allerdings stellen UDP-Sockets weder die Integrität von Netzwerkpaketen, noch ob die Pakete das Remoteziel erreichen, sicher.</span><span class="sxs-lookup"><span data-stu-id="ba98d-148">But UDP sockets don't ensure integrity of the network packets nor even whether packets make it to the remote destination at all.</span></span> <span data-ttu-id="ba98d-149">Daher muss Ihre App so konzipiert sein, dass sie dies toleriert.</span><span class="sxs-lookup"><span data-stu-id="ba98d-149">So your app will need to be designed to tolerate that.</span></span> <span data-ttu-id="ba98d-150">Beispiele für Anwendungen, die UDP-Sockets verwenden, sind Clients für die Erkennung im lokalen Netzwerk und für lokalen Chat.</span><span class="sxs-lookup"><span data-stu-id="ba98d-150">Some examples of applications that use UDP sockets are local network discovery, and local chat clients.</span></span>

<span data-ttu-id="ba98d-151">Zur Veranschaulichung von grundlegenden UDP-Vorgängen zeigt der folgende Beispielcode, wie die [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket)-Klasse verwendet wird, um Daten über UDP sowohl zu senden als auch zu empfangen, um einen Echo-Client und -Server zu bilden.</span><span class="sxs-lookup"><span data-stu-id="ba98d-151">To demonstrate basic UDP operations, the example code below shows the [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket) class being used to both send and receive data over UDP to form an echo client and server.</span></span> <span data-ttu-id="ba98d-152">Erstellen Sie ein neues Projekt und fügen Sie den nachstehenden Client- und Servercode in dasselbe Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="ba98d-152">Create a new project, and put both the client and the server code below into the same project.</span></span> <span data-ttu-id="ba98d-153">Genau wie bei einem TCP-Socket, müssen Sie die App-Funktion **Private Netzwerke (Client und Server)** deklarieren.</span><span class="sxs-lookup"><span data-stu-id="ba98d-153">Just as for a TCP socket, you'll need to declare the **Private Networks (Client & Server)** app capability.</span></span>

### <a name="an-echo-client-and-server-using-udp-sockets"></a><span data-ttu-id="ba98d-154">UDP-Socket-basierte Echo-Clients und -Server</span><span class="sxs-lookup"><span data-stu-id="ba98d-154">An echo client and server, using UDP sockets</span></span>
<span data-ttu-id="ba98d-155">Erstellen Sie ein [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket) für die Rolle des Echo-Servers, binden Sie es an eine bestimmte Portnummer, lauschen Sie auf eine eingehende UDP-Nachricht und geben Sie sie zurück.</span><span class="sxs-lookup"><span data-stu-id="ba98d-155">Construct a [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket) to play the role of the echo server, bind it to a specific port number, listen for an incoming UDP message, and echo it back.</span></span> <span data-ttu-id="ba98d-156">Das [**DatagramSocket.MessageReceived**](/uwp/api/Windows.Networking.Sockets.DatagramSocket.MessageReceived) -Ereignis wird ausgelöst, wenn das Socket eine Nachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="ba98d-156">The [**DatagramSocket.MessageReceived**](/uwp/api/Windows.Networking.Sockets.DatagramSocket.MessageReceived) event is raised when a message is receieved on the socket.</span></span>

<span data-ttu-id="ba98d-157">Erstellen Sie ein anderes **DatagramSocket** für die Rolle des Echo-Clients, binden Sie es an eine bestimmte Portnummer, senden Sie eine UDP-Nachricht und empfangen Sie eine Antwort.</span><span class="sxs-lookup"><span data-stu-id="ba98d-157">Construct another **DatagramSocket** to play the role of the echo client, bind it to a specific port number, send a UDP message, and receive a response.</span></span>

<span data-ttu-id="ba98d-158">Erstellen Sie eine neue **Seite** namens `DatagramSocketPage`.</span><span class="sxs-lookup"><span data-stu-id="ba98d-158">Create a new **Page** named `DatagramSocketPage`.</span></span> <span data-ttu-id="ba98d-159">Fügen Sie das XAML-Markup in `DatagramSocketPage.xaml` ein und stellen Sie dann den imperativen Code innerhalb der `DatagramSocketPage`-Klasse bereit.</span><span class="sxs-lookup"><span data-stu-id="ba98d-159">Put the XAML markup in `DatagramSocketPage.xaml`, and the put the imperative code inside the `DatagramSocketPage` class.</span></span>

```XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>

    <StackPanel>
        <TextBlock Margin="9.6,0" Style="{StaticResource TitleTextBlockStyle}" Text="UDP socket example"/>
        <TextBlock Margin="7.2,0,0,0" Style="{StaticResource HeaderTextBlockStyle}" Text="DatagramSocket"/>
    </StackPanel>

    <Grid Grid.Row="1">
        <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*"/>
            <ColumnDefinition Width="*"/>
        </Grid.ColumnDefinitions>
        <TextBlock Margin="9.6" Style="{StaticResource SubtitleTextBlockStyle}" Text="client"/>
        <ListBox x:Name="clientListBox" Grid.Row="1" Margin="9.6"/>
        <TextBlock Grid.Column="1" Margin="9.6" Style="{StaticResource SubtitleTextBlockStyle}" Text="server"/>
        <ListBox x:Name="serverListBox" Grid.Column="1" Grid.Row="1" Margin="9.6"/>
    </Grid>
</Grid>
```

```csharp
// Every protocol typically has a standard port number. For example, HTTP is typically 80, FTP is 20 and 21, etc.
// For this example, we'll choose different arbitrary port numbers for client and server, since both will be running on the same machine.
static string ClientPortNumber = "1336";
static string ServerPortNumber = "1337";

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    this.StartServer();
    this.StartClient();
}

private async void StartServer()
{
    try
    {
        var serverDatagramSocket = new Windows.Networking.Sockets.DatagramSocket();

        // The ConnectionReceived event is raised when connections are received.
        serverDatagramSocket.MessageReceived += ServerDatagramSocket_MessageReceived;

        this.serverListBox.Items.Add("server is about to bind...");

        // Start listening for incoming TCP connections on the specified port. You can specify any port that's not currently in use.
        await serverDatagramSocket.BindServiceNameAsync(DatagramSocketPage.ServerPortNumber);

        this.serverListBox.Items.Add(string.Format("server is bound to port number {0}", DatagramSocketPage.ServerPortNumber));
    }
    catch (Exception ex)
    {
        Windows.Networking.Sockets.SocketErrorStatus webErrorStatus = Windows.Networking.Sockets.SocketError.GetStatus(ex.GetBaseException().HResult);
        this.serverListBox.Items.Add(webErrorStatus.ToString() != "Unknown" ? webErrorStatus.ToString() : ex.Message);
    }
}

private async void ServerDatagramSocket_MessageReceived(Windows.Networking.Sockets.DatagramSocket sender, Windows.Networking.Sockets.DatagramSocketMessageReceivedEventArgs args)
{
    string request;
    using (DataReader dataReader = args.GetDataReader())
    {
        request = dataReader.ReadString(dataReader.UnconsumedBufferLength).Trim();
    }

    await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () => this.serverListBox.Items.Add(string.Format("server received the request: \"{0}\"", request)));

    // Echo the request back as the response.
    using (Stream outputStream = (await sender.GetOutputStreamAsync(args.RemoteAddress, DatagramSocketPage.ClientPortNumber)).AsStreamForWrite())
    {
        using (var streamWriter = new StreamWriter(outputStream))
        {
            await streamWriter.WriteLineAsync(request);
            await streamWriter.FlushAsync();
        }
    }

    await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () => this.serverListBox.Items.Add(string.Format("server sent back the response: \"{0}\"", request)));

    sender.Dispose();

    await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () => this.serverListBox.Items.Add("server closed its socket"));
}

private async void StartClient()
{
    try
    {
        // Create the DatagramSocket and establish a connection to the echo server.
        var clientDatagramSocket = new Windows.Networking.Sockets.DatagramSocket();

        clientDatagramSocket.MessageReceived += ClientDatagramSocket_MessageReceived;

        // The server hostname that we will be establishing a connection to. In this example, the server and client are in the same process.
        var hostName = new Windows.Networking.HostName("localhost");

        this.clientListBox.Items.Add("client is about to bind...");

        await clientDatagramSocket.BindServiceNameAsync(DatagramSocketPage.ClientPortNumber);

        this.clientListBox.Items.Add(string.Format("client is bound to port number {0}", DatagramSocketPage.ClientPortNumber));

        // Send a request to the echo server.
        string request = "Hello, World!";
        using (var serverDatagramSocket = new Windows.Networking.Sockets.DatagramSocket())
        {
            using (Stream outputStream = (await serverDatagramSocket.GetOutputStreamAsync(hostName, DatagramSocketPage.ServerPortNumber)).AsStreamForWrite())
            {
                using (var streamWriter = new StreamWriter(outputStream))
                {
                    await streamWriter.WriteLineAsync(request);
                    await streamWriter.FlushAsync();
                }
            }
        }

        this.clientListBox.Items.Add(string.Format("client sent the request: \"{0}\"", request));
    }
    catch (Exception ex)
    {
        Windows.Networking.Sockets.SocketErrorStatus webErrorStatus = Windows.Networking.Sockets.SocketError.GetStatus(ex.GetBaseException().HResult);
        this.clientListBox.Items.Add(webErrorStatus.ToString() != "Unknown" ? webErrorStatus.ToString() : ex.Message);
    }
}

private async void ClientDatagramSocket_MessageReceived(Windows.Networking.Sockets.DatagramSocket sender, Windows.Networking.Sockets.DatagramSocketMessageReceivedEventArgs args)
{
    string response;
    using (DataReader dataReader = args.GetDataReader())
    {
        response = dataReader.ReadString(dataReader.UnconsumedBufferLength).Trim();
    }

    await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () => this.clientListBox.Items.Add(string.Format("client received the response: \"{0}\"", response)));

    sender.Dispose();

    await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () => this.clientListBox.Items.Add("client closed its socket"));
}
```

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.UI.Core.h>
#include <winrt/Windows.UI.Xaml.Navigation.h>
#include <sstream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Core;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::DatagramSocket m_clientDatagramSocket;
    Windows::Networking::Sockets::DatagramSocket m_serverDatagramSocket;

public:
    void OnNavigatedTo(NavigationEventArgs const& /* e */)
    {
        StartServer();
        StartClient();
    }

private:
    IAsyncAction StartServer()
    {
        try
        {
            // The ConnectionReceived event is raised when connections are received.
            m_serverDatagramSocket.MessageReceived({ this, &DatagramSocketPage::ServerDatagramSocket_MessageReceived });

            serverListBox().Items().Append(winrt::box_value(L"server is about to bind..."));

            // Start listening for incoming TCP connections on the specified port. You can specify any port that's not currently in use.
            co_await m_serverDatagramSocket.BindServiceNameAsync(L"1337");
            serverListBox().Items().Append(winrt::box_value(L"server is bound to port number 1337"));
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus{ Windows::Networking::Sockets::SocketError::GetStatus(ex.to_abi()) };
            serverListBox().Items().Append(webErrorStatus != Windows::Networking::Sockets::SocketErrorStatus::Unknown ? winrt::box_value(winrt::to_hstring((int32_t)webErrorStatus)) : winrt::box_value(winrt::to_hstring(ex.to_abi())));
        }
    }

    IAsyncAction ServerDatagramSocket_MessageReceived(Windows::Networking::Sockets::DatagramSocket sender, Windows::Networking::Sockets::DatagramSocketMessageReceivedEventArgs args)
    {
        DataReader dataReader{ args.GetDataReader() };
        winrt::hstring request{ dataReader.ReadString(dataReader.UnconsumedBufferLength()) };

        serverListBox().Dispatcher().RunAsync(CoreDispatcherPriority::Normal, [=]()
        {
            std::wstringstream wstringstream;
            wstringstream << L"server received the request: \"" << request.c_str() << L"\"";
            serverListBox().Items().Append(winrt::box_value(wstringstream.str().c_str()));
        });

        // Echo the request back as the response.
        IOutputStream outputStream = co_await sender.GetOutputStreamAsync(args.RemoteAddress(), L"1336");
        DataWriter dataWriter{ outputStream };
        dataWriter.WriteString(request);

        co_await dataWriter.StoreAsync();
        dataWriter.DetachStream();

        serverListBox().Dispatcher().RunAsync(CoreDispatcherPriority::Normal, [=]()
        {
            std::wstringstream wstringstream;
            wstringstream << L"server sent back the response: \"" << request.c_str() << L"\"";
            serverListBox().Items().Append(winrt::box_value(wstringstream.str().c_str()));

            m_serverDatagramSocket = nullptr;

            serverListBox().Items().Append(winrt::box_value(L"server closed its socket"));
        });
    }

    IAsyncAction StartClient()
    {
        try
        {
            m_clientDatagramSocket.MessageReceived({ this, &DatagramSocketPage::ClientDatagramSocket_MessageReceived });

            // Establish a connection to the echo server.
            // The server hostname that we will be establishing a connection to. In this example, the server and client are in the same process.
            Windows::Networking::HostName hostName{ L"localhost" };

            clientListBox().Items().Append(winrt::box_value(L"client is about to bind..."));

            co_await m_clientDatagramSocket.BindServiceNameAsync(L"1336");
            clientListBox().Items().Append(winrt::box_value(L"client is bound to port number 1336"));

            // Send a request to the echo server.
            Windows::Networking::Sockets::DatagramSocket serverDatagramSocket;
            IOutputStream outputStream = co_await m_serverDatagramSocket.GetOutputStreamAsync(hostName, L"1337");

            winrt::hstring request{ L"Hello, World!" };
            DataWriter dataWriter{ outputStream };
            dataWriter.WriteString(request);
            co_await dataWriter.StoreAsync();
            dataWriter.DetachStream();

            std::wstringstream wstringstream;
            wstringstream << L"client sent the request: \"" << request.c_str() << L"\"";
            clientListBox().Items().Append(winrt::box_value(wstringstream.str().c_str()));
        }
        catch (winrt::hresult_error const& ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus{ Windows::Networking::Sockets::SocketError::GetStatus(ex.to_abi()) };
            serverListBox().Items().Append(webErrorStatus != Windows::Networking::Sockets::SocketErrorStatus::Unknown ? winrt::box_value(winrt::to_hstring((int32_t)webErrorStatus)) : winrt::box_value(winrt::to_hstring(ex.to_abi())));
        }
    }

    void ClientDatagramSocket_MessageReceived(Windows::Networking::Sockets::DatagramSocket const& /* sender */, Windows::Networking::Sockets::DatagramSocketMessageReceivedEventArgs const& args)
    {
        DataReader dataReader{ args.GetDataReader() };
        winrt::hstring response{ dataReader.ReadString(dataReader.UnconsumedBufferLength()) };
        clientListBox().Dispatcher().RunAsync(CoreDispatcherPriority::Normal, [=]()
        {
            std::wstringstream wstringstream;
            wstringstream << L"client received the response: \"" << response.c_str() << L"\"";
            clientListBox().Items().Append(winrt::box_value(wstringstream.str().c_str()));
        });

        m_clientDatagramSocket = nullptr;

        clientListBox().Dispatcher().RunAsync(CoreDispatcherPriority::Normal, [=]()
        {
            clientListBox().Items().Append(winrt::box_value(L"client closed its socket"));
        });
    }
```

```cpp
#include <ppltasks.h>
#include <sstream>
...
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Core;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::DatagramSocket^ clientDatagramSocket;
    Windows::Networking::Sockets::DatagramSocket^ serverDatagramSocket;

protected:
    virtual void OnNavigatedTo(NavigationEventArgs^ e) override
    {
        this->StartServer();
        this->StartClient();
    }

private:
    void StartServer()
    {
        try
        {
            this->serverDatagramSocket = ref new Windows::Networking::Sockets::DatagramSocket();

            // The ConnectionReceived event is raised when connections are received.
            this->serverDatagramSocket->MessageReceived += ref new TypedEventHandler<Windows::Networking::Sockets::DatagramSocket^, Windows::Networking::Sockets::DatagramSocketMessageReceivedEventArgs^>(this, &DatagramSocketPage::ServerDatagramSocket_MessageReceived);

            this->serverListBox->Items->Append(L"server is about to bind...");

            // Start listening for incoming TCP connections on the specified port. You can specify any port that's not currently in use.
            Concurrency::create_task(this->serverDatagramSocket->BindServiceNameAsync("1337")).then(
                [=]
            {
                this->serverListBox->Items->Append(L"server is bound to port number 1337");
            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus = Windows::Networking::Sockets::SocketError::GetStatus(ex->HResult);
            this->serverListBox->Items->Append(webErrorStatus.ToString() != L"Unknown" ? webErrorStatus.ToString() : ex->Message);
        }
    }

    void ServerDatagramSocket_MessageReceived(Windows::Networking::Sockets::DatagramSocket^ sender, Windows::Networking::Sockets::DatagramSocketMessageReceivedEventArgs^ args)
    {
        DataReader^ dataReader = args->GetDataReader();
        Platform::String^ request = dataReader->ReadString(dataReader->UnconsumedBufferLength);
        this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler(
            [=]
        {
            std::wstringstream wstringstream;
            wstringstream << L"server received the request: \"" << request->Data() << L"\"";
            this->serverListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));
        }));

        // Echo the request back as the response.
        Concurrency::create_task(sender->GetOutputStreamAsync(args->RemoteAddress, "1336")).then(
            [=](IOutputStream^ outputStream)
        {
            auto dataWriter = ref new DataWriter(outputStream);
            dataWriter->WriteString(request);
            Concurrency::create_task(dataWriter->StoreAsync()).then(
                [=](unsigned int)
            {
                dataWriter->DetachStream();

                this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler(
                    [=]()
                {
                    std::wstringstream wstringstream;
                    wstringstream << L"server sent back the response: \"" << request->Data() << L"\"";
                    this->serverListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));

                    delete this->serverDatagramSocket;
                    this->serverDatagramSocket = nullptr;

                    this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler([=]() {this->serverListBox->Items->Append(L"server closed its socket"); }));
                }));
            });
        });
    }

    void StartClient()
    {
        try
        {
            // Create the DatagramSocket and establish a connection to the echo server.
            this->clientDatagramSocket = ref new Windows::Networking::Sockets::DatagramSocket();

            this->clientDatagramSocket->MessageReceived += ref new TypedEventHandler<Windows::Networking::Sockets::DatagramSocket^, Windows::Networking::Sockets::DatagramSocketMessageReceivedEventArgs^>(this, &DatagramSocketPage::ClientDatagramSocket_MessageReceived);

            // The server hostname that we will be establishing a connection to. In this example, the server and client are in the same process.
            auto hostName = ref new Windows::Networking::HostName(L"localhost");

            this->clientListBox->Items->Append(L"client is about to bind...");

            Concurrency::create_task(this->clientDatagramSocket->BindServiceNameAsync("1336")).then(
                [=]
            {
                this->clientListBox->Items->Append(L"client is bound to port number 1336");
            });

            // Send a request to the echo server.
            auto serverDatagramSocket = ref new Windows::Networking::Sockets::DatagramSocket();
            Concurrency::create_task(serverDatagramSocket->GetOutputStreamAsync(hostName, "1337")).then(
                [=](IOutputStream^ outputStream)
            {
                auto request = ref new Platform::String(L"Hello, World!");
                auto dataWriter = ref new DataWriter(outputStream);
                dataWriter->WriteString(request);
                Concurrency::create_task(dataWriter->StoreAsync()).then(
                    [=](unsigned int)
                {
                    dataWriter->DetachStream();
                    std::wstringstream wstringstream;
                    wstringstream << L"client sent the request: \"" << request->Data() << L"\"";
                    this->clientListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));
                });

            });
        }
        catch (Platform::Exception^ ex)
        {
            Windows::Networking::Sockets::SocketErrorStatus webErrorStatus = Windows::Networking::Sockets::SocketError::GetStatus(ex->HResult);
            this->serverListBox->Items->Append(webErrorStatus.ToString() != L"Unknown" ? webErrorStatus.ToString() : ex->Message);
        }
    }

    void ClientDatagramSocket_MessageReceived(Windows::Networking::Sockets::DatagramSocket^ sender, Windows::Networking::Sockets::DatagramSocketMessageReceivedEventArgs^ args)
    {
        DataReader^ dataReader = args->GetDataReader();
        Platform::String^ response = dataReader->ReadString(dataReader->UnconsumedBufferLength);
        this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler(
            [=]
        {
            std::wstringstream wstringstream;
            wstringstream << L"client received the response: \"" << response->Data() << L"\"";
            this->clientListBox->Items->Append(ref new Platform::String(wstringstream.str().c_str()));
        }));

        delete this->clientDatagramSocket;
        this->clientDatagramSocket = nullptr;

        this->Dispatcher->RunAsync(CoreDispatcherPriority::Normal, ref new DispatchedHandler([=]() {this->clientListBox->Items->Append(L"client closed its socket"); }));
    }
```

## <a name="background-operations-and-the-socket-broker"></a><span data-ttu-id="ba98d-160">Hintergrundvorgänge und der Socketbroker</span><span class="sxs-lookup"><span data-stu-id="ba98d-160">Background operations and the socket broker</span></span>
<span data-ttu-id="ba98d-161">Sie können den Socket-Broker und Steuerkanaltrigger verwenden, um sicherzustellen, dass Ihre App Verbindungen oder Daten für Sockets ordnungsgemäß empfängt, während sie sich nicht im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="ba98d-161">You can use the socket broker, and control channel triggers, to ensure that your app properly receives connections or data on sockets while it's not in the foreground.</span></span> <span data-ttu-id="ba98d-162">Weitere Informationen finden Sie unter [Netzwerkkommunikation im Hintergrund](network-communications-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="ba98d-162">For more info, see [Network communications in the background](network-communications-in-the-background.md).</span></span>

## <a name="batched-sends"></a><span data-ttu-id="ba98d-163">Sendevorgänge im Batch</span><span class="sxs-lookup"><span data-stu-id="ba98d-163">Batched sends</span></span>
<span data-ttu-id="ba98d-164">Immer wenn Sie in den Datenstrom schreiben, der einem Socket zugeordnet ist, erfolgt ein Übergang vom Benutzermodus (Ihrem Code) zum Kernelmodus (wo sich der Netzwerkstapel befindet).</span><span class="sxs-lookup"><span data-stu-id="ba98d-164">Whenever you write to the stream associated with a socket, a transition happens from user mode (your code) to kernel mode (where the network stack is).</span></span> <span data-ttu-id="ba98d-165">Wenn Sie gleichzeitig viele Puffer schreiben, ergeben diese wiederholten Übergänge einen erheblichen Mehraufwand.</span><span class="sxs-lookup"><span data-stu-id="ba98d-165">If you're writing many buffers at a time then these repeated transitions compound into substantial overhead.</span></span> <span data-ttu-id="ba98d-166">Durch die Batchverarbeitung Ihrer Sendevorgänge können Sie mehrere Datenpuffer zusammen senden und diesen Mehraufwand vermeiden.</span><span class="sxs-lookup"><span data-stu-id="ba98d-166">Batching your sends is a way to send multiple buffers of data together, and avoid that overhead.</span></span> <span data-ttu-id="ba98d-167">Dies ist besonders hilfreich, wenn Ihre App VoIP, VPN oder andere Aufgaben ausführt, die mit dem effizienten Verschieben großer Datenmengen verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="ba98d-167">It's especially useful if your app is doing VoIP, VPN, or other tasks that involve moving a lot of data as efficiently as possible.</span></span>

<span data-ttu-id="ba98d-168">In diesem Abschnittwerden einige Batchverarbeitungsmethoden gezeigt, die Sie mit [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket) oder einem verbundenen [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket) verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ba98d-168">This section demonstrates a couple of batched sends techniques that you can use with a [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket) or a connected [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket).</span></span>

<span data-ttu-id="ba98d-169">Sehen wir uns zunächst an, wie eine große Anzahl von Puffern auf eine ineffiziente Art und Weise gesendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="ba98d-169">To get a baseline, let's see how to send a large number of buffers in an inefficient way.</span></span> <span data-ttu-id="ba98d-170">Hier ist eine kleine Demo, die ein **StreamSocket** verwendet.</span><span class="sxs-lookup"><span data-stu-id="ba98d-170">Here's a minimal demo, using a **StreamSocket**.</span></span>

```csharp
protected override async void OnNavigatedTo(NavigationEventArgs e)
{
    var streamSocketListener = new Windows.Networking.Sockets.StreamSocketListener();
    streamSocketListener.ConnectionReceived += this.StreamSocketListener_ConnectionReceived;
    await streamSocketListener.BindServiceNameAsync("1337");

    var streamSocket = new Windows.Networking.Sockets.StreamSocket();
    await streamSocket.ConnectAsync(new Windows.Networking.HostName("localhost"), "1337");
    this.SendMultipleBuffersInefficiently(streamSocket, "Hello, World!");
    //this.BatchedSendsCSharpOnly(streamSocket, "Hello, World!");
    //this.BatchedSendsAnyUWPLanguage(streamSocket, "Hello, World!");
}

private async void StreamSocketListener_ConnectionReceived(Windows.Networking.Sockets.StreamSocketListener sender, Windows.Networking.Sockets.StreamSocketListenerConnectionReceivedEventArgs args)
{
    using (var dataReader = new DataReader(args.Socket.InputStream))
    {
        dataReader.InputStreamOptions = InputStreamOptions.Partial;
        while (true)
        {
            await dataReader.LoadAsync(256);
            if (dataReader.UnconsumedBufferLength == 0) break;
            IBuffer requestBuffer = dataReader.ReadBuffer(dataReader.UnconsumedBufferLength);
            string request = Windows.Security.Cryptography.CryptographicBuffer.ConvertBinaryToString(Windows.Security.Cryptography.BinaryStringEncoding.Utf8, requestBuffer);
            Debug.WriteLine(string.Format("server received the request: \"{0}\"", request));
        }
    }
}

// This implementation incurs kernel transition overhead for each packet written.
private async void SendMultipleBuffersInefficiently(Windows.Networking.Sockets.StreamSocket streamSocket, string message)
{
    var packetsToSend = new List<IBuffer>();
    for (int count = 0; count < 5; ++count) { packetsToSend.Add(Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(message, Windows.Security.Cryptography.BinaryStringEncoding.Utf8)); }

    foreach (IBuffer packet in packetsToSend)
    {
        await streamSocket.OutputStream.WriteAsync(packet);
    }
}
```

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.Security.Cryptography.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.UI.Core.h>
#include <winrt/Windows.UI.Xaml.Navigation.h>
#include <sstream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Core;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::StreamSocketListener m_streamSocketListener;
    Windows::Networking::Sockets::StreamSocket m_streamSocket;

public:
    IAsyncAction OnNavigatedTo(NavigationEventArgs /* e */)
    {
        m_streamSocketListener.ConnectionReceived({ this, &BatchedSendsPage::OnConnectionReceived });
        co_await m_streamSocketListener.BindServiceNameAsync(L"1337");

        co_await m_streamSocket.ConnectAsync(Windows::Networking::HostName{ L"localhost" }, L"1337");
        SendMultipleBuffersInefficientlyAsync(L"Hello, World!");
        //BatchedSendsAnyUWPLanguageAsync(L"Hello, World!");
    }

private:
    IAsyncAction OnConnectionReceived(Windows::Networking::Sockets::StreamSocketListener const& /* sender */, Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs const& args)
    {
        DataReader dataReader{ args.Socket().InputStream() };
        dataReader.InputStreamOptions(Windows::Storage::Streams::InputStreamOptions::Partial);

        while (true)
        {
            unsigned int bytesLoaded = co_await dataReader.LoadAsync(256);
            if (bytesLoaded == 0) break;
            winrt::hstring message{ dataReader.ReadString(bytesLoaded) };
            ::OutputDebugString(message.c_str());
        }
    }

    // This implementation incurs kernel transition overhead for each packet written.
    IAsyncAction SendMultipleBuffersInefficientlyAsync(winrt::hstring message)
    {
        co_await winrt::resume_background();

        std::vector< IBuffer > packetsToSend;
        for (unsigned int count = 0; count < 5; ++count)
        {
            packetsToSend.push_back(Windows::Security::Cryptography::CryptographicBuffer::ConvertStringToBinary(message, Windows::Security::Cryptography::BinaryStringEncoding::Utf8));
        }

        for (auto const& element : packetsToSend)
        {
            m_streamSocket.OutputStream().WriteAsync(element).get();
        }
    }
```

```cpp
#include <ppltasks.h>
#include <sstream>
...
using namespace Windows::Foundation;
using namespace Windows::Storage::Streams;
using namespace Windows::UI::Core;
using namespace Windows::UI::Xaml::Navigation;
...
private:
    Windows::Networking::Sockets::StreamSocketListener^ streamSocketListener;
    Windows::Networking::Sockets::StreamSocket^ streamSocket;

protected:
    virtual void OnNavigatedTo(NavigationEventArgs^ e) override
    {
        this->streamSocketListener = ref new Windows::Networking::Sockets::StreamSocketListener();
        streamSocketListener->ConnectionReceived += ref new TypedEventHandler<Windows::Networking::Sockets::StreamSocketListener^, Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs^>(this, &BatchedSendsPage::StreamSocketListener_ConnectionReceived);
        Concurrency::create_task(this->streamSocketListener->BindServiceNameAsync(L"1337")).then(
            [=]
        {
            this->streamSocket = ref new Windows::Networking::Sockets::StreamSocket();
            Concurrency::create_task(this->streamSocket->ConnectAsync(ref new Windows::Networking::HostName(L"localhost"), L"1337")).then(
                [=](Concurrency::task< void >)
            {
                this->SendMultipleBuffersInefficiently(L"Hello, World!");
                // this->BatchedSendsAnyUWPLanguage(L"Hello, World!");
            }, Concurrency::task_continuation_context::use_synchronous_execution());
        });
    }

private:
    void StreamSocketListener_ConnectionReceived(Windows::Networking::Sockets::StreamSocketListener^ sender, Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs^ args)
    {
        auto dataReader = ref new DataReader(args->Socket->InputStream);
        dataReader->InputStreamOptions = Windows::Storage::Streams::InputStreamOptions::Partial;
        this->ReceiveStringRecurse(dataReader, args->Socket);
    }

    void ReceiveStringRecurse(DataReader^ dataReader, Windows::Networking::Sockets::StreamSocket^ streamSocket)
    {
        Concurrency::create_task(dataReader->LoadAsync(256)).then(
            [this, dataReader, streamSocket](unsigned int bytesLoaded)
        {
            if (bytesLoaded == 0) return;
            Platform::String^ message = dataReader->ReadString(bytesLoaded);
            ::OutputDebugString(message->Data());
            this->ReceiveStringRecurse(dataReader, streamSocket);
        });
    }

    // This implementation incurs kernel transition overhead for each packet written.
    void SendMultipleBuffersInefficiently(Platform::String^ message)
    {
        std::vector< IBuffer^ > packetsToSend{};
        for (unsigned int count = 0; count < 5; ++count)
        {
            packetsToSend.push_back(Windows::Security::Cryptography::CryptographicBuffer::ConvertStringToBinary(message, Windows::Security::Cryptography::BinaryStringEncoding::Utf8));
        }

        for (auto element : packetsToSend)
        {
            Concurrency::create_task(this->streamSocket->OutputStream->WriteAsync(element)).wait();
        }
    }
```

<span data-ttu-id="ba98d-171">Dieses erste Beispiel einer effizienteren Methode ist nur dann geeignet, wenn Sie C# verwenden.</span><span class="sxs-lookup"><span data-stu-id="ba98d-171">This first example of a more efficient technique is only appropriate if you're using C#.</span></span> <span data-ttu-id="ba98d-172">Ändern Sie `OnNavigatedTo`, um `BatchedSendsCSharpOnly` anstelle von `SendMultipleBuffersInefficiently` oder `SendMultipleBuffersInefficientlyAsync` aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="ba98d-172">Change `OnNavigatedTo` to call `BatchedSendsCSharpOnly` instead of `SendMultipleBuffersInefficiently` or `SendMultipleBuffersInefficientlyAsync`.</span></span>

```csharp
// A C#-only technique for batched sends.
private async void BatchedSendsCSharpOnly(Windows.Networking.Sockets.StreamSocket streamSocket, string message)
{
    var packetsToSend = new List<IBuffer>();
    for (int count = 0; count < 5; ++count) { packetsToSend.Add(Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(message, Windows.Security.Cryptography.BinaryStringEncoding.Utf8)); }

    var pendingTasks = new System.Threading.Tasks.Task[packetsToSend.Count];

    for (int index = 0; index < packetsToSend.Count; ++index)
    {
        // track all pending writes as tasks, but don't wait on one before beginning the next.
        pendingTasks[index] = streamSocket.OutputStream.WriteAsync(packetsToSend[index]).AsTask();
        // Don't modify any buffer's contents until the pending writes are complete.
    }

    // Wait for all of the pending writes to complete.
    System.Threading.Tasks.Task.WaitAll(pendingTasks);
}
```

<span data-ttu-id="ba98d-173">Dieses nächste Beispiel ist für jede UWP-Sprache geeignet, nicht nur für C#.</span><span class="sxs-lookup"><span data-stu-id="ba98d-173">This next example is appropriate for any UWP language, not just for C#.</span></span> <span data-ttu-id="ba98d-174">Es basiert auf dem Verhalten in [**StreamSocket.OutputStream**](/uwp/api/windows.networking.sockets.streamsocket.OutputStream) und [**DatagramSocket.OutputStream**](/uwp/api/windows.networking.sockets.datagramsocket.OutputStream), das Sendevorgänge zusammen in Batches vornimmt.</span><span class="sxs-lookup"><span data-stu-id="ba98d-174">It relies on the behavior in [**StreamSocket.OutputStream**](/uwp/api/windows.networking.sockets.streamsocket.OutputStream) and [**DatagramSocket.OutputStream**](/uwp/api/windows.networking.sockets.datagramsocket.OutputStream) that batches sends together.</span></span> <span data-ttu-id="ba98d-175">Die Technik ruft [**FlushAsync**](/uwp/api/windows.storage.streams.ioutputstream.FlushAsync) auf diesem Ausgabedatenstrom, der ab Windows 10, garantiert zurück, nur, nachdem alle Vorgänge im Ausgabedatenstrom abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="ba98d-175">The technique calls [**FlushAsync**](/uwp/api/windows.storage.streams.ioutputstream.FlushAsync) on that output stream which, as of Windows10, is guaranteed to return only after all operations on the output stream have completed.</span></span>

```csharp
// An implementation of batched sends suitable for any UWP language.
private async void BatchedSendsAnyUWPLanguage(Windows.Networking.Sockets.StreamSocket streamSocket, string message)
{
    var packetsToSend = new List<IBuffer>();
    for (int count = 0; count < 5; ++count) { packetsToSend.Add(Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(message, Windows.Security.Cryptography.BinaryStringEncoding.Utf8)); }

    var pendingWrites = new IAsyncOperationWithProgress<uint, uint>[packetsToSend.Count];

    for (int index = 0; index < packetsToSend.Count; ++index)
    {
        // track all pending writes as tasks, but don't wait on one before beginning the next.
        pendingWrites[index] = streamSocket.OutputStream.WriteAsync(packetsToSend[index]);
        // Don't modify any buffer's contents until the pending writes are complete.
    }

    // Wait for all of the pending writes to complete. This step enables batched sends on the output stream.
    await streamSocket.OutputStream.FlushAsync();
}
```

```cppwinrt
// An implementation of batched sends suitable for any UWP language.
IAsyncAction BatchedSendsAnyUWPLanguageAsync(winrt::hstring message)
{
    std::vector< IBuffer > packetsToSend{};
    std::vector< IAsyncOperationWithProgress< unsigned int, unsigned int > > pendingWrites{};
    for (unsigned int count = 0; count < 5; ++count)
    {
        packetsToSend.push_back(Windows::Security::Cryptography::CryptographicBuffer::ConvertStringToBinary(message, Windows::Security::Cryptography::BinaryStringEncoding::Utf8));
    }

    for (auto const& element : packetsToSend)
    {
        // track all pending writes as tasks, but don't wait on one before beginning the next.
        pendingWrites.push_back(m_streamSocket.OutputStream().WriteAsync(element));
        // Don't modify any buffer's contents until the pending writes are complete.
    }

    // Wait for all of the pending writes to complete. This step enables batched sends on the output stream.
    co_await m_streamSocket.OutputStream().FlushAsync();
}
```

```cpp
private:
    // An implementation of batched sends suitable for any UWP language.
    void BatchedSendsAnyUWPLanguage(Platform::String^ message)
    {
        std::vector< IBuffer^ > packetsToSend{};
        std::vector< IAsyncOperationWithProgress< unsigned int, unsigned int >^ >pendingWrites{};
        for (unsigned int count = 0; count < 5; ++count)
        {
            packetsToSend.push_back(Windows::Security::Cryptography::CryptographicBuffer::ConvertStringToBinary(message, Windows::Security::Cryptography::BinaryStringEncoding::Utf8));
        }

        for (auto element : packetsToSend)
        {
            // track all pending writes as tasks, but don't wait on one before beginning the next.
            pendingWrites.push_back(this->streamSocket->OutputStream->WriteAsync(element));
            // Don't modify any buffer's contents until the pending writes are complete.
        }

        // Wait for all of the pending writes to complete. This step enables batched sends on the output stream.
        Concurrency::create_task(this->streamSocket->OutputStream->FlushAsync());
    }
```

<span data-ttu-id="ba98d-176">Es gibt einige wichtige Einschränkungen, die für Sendevorgänge im Batch in Ihrem Code gelten.</span><span class="sxs-lookup"><span data-stu-id="ba98d-176">There are some important limitations imposed by using batched sends in your code.</span></span>

-   <span data-ttu-id="ba98d-177">Sie können den Inhalt der zu schreibenden **IBuffer**-Instanzen nicht ändern, bis der asynchrone Schreibvorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="ba98d-177">You cannot modify the contents of the **IBuffer** instances being written until the asynchronous write is complete.</span></span>
-   <span data-ttu-id="ba98d-178">Das **FlushAsync**-Muster funktioniert nur bei **StreamSocket.OutputStream** und **DatagramSocket.OutputStream**.</span><span class="sxs-lookup"><span data-stu-id="ba98d-178">The **FlushAsync** pattern only works on **StreamSocket.OutputStream** and **DatagramSocket.OutputStream**.</span></span>
-   <span data-ttu-id="ba98d-179">Die **FlushAsync** -Muster funktioniert nur in Windows 10.</span><span class="sxs-lookup"><span data-stu-id="ba98d-179">The **FlushAsync** pattern only works in Windows10 and onward.</span></span>
-   <span data-ttu-id="ba98d-180">Verwenden Sie in anderen Fällen [**Task.WaitAll**](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.task.waitall?view=netcore-2.0#System_Threading_Tasks_Task_WaitAll_System_Threading_Tasks_Task___) statt des **FlushAsync**-Musters.</span><span class="sxs-lookup"><span data-stu-id="ba98d-180">In other cases, use [**Task.WaitAll**](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.task.waitall?view=netcore-2.0#System_Threading_Tasks_Task_WaitAll_System_Threading_Tasks_Task___) instead of the **FlushAsync** pattern.</span></span>

## <a name="port-sharing-for-datagramsocket"></a><span data-ttu-id="ba98d-181">Portfreigabe für DatagramSocket</span><span class="sxs-lookup"><span data-stu-id="ba98d-181">Port sharing for DatagramSocket</span></span>
<span data-ttu-id="ba98d-182">Sie können ein [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket) für die Koexistenz mit anderen Win32- oder UWP-Multicast Sockets konfigurieren, die an die gleiche Adresse oder den gleichen Port gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="ba98d-182">You can configure a [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket) to coexist with other Win32 or UWP multicast sockets bound to the same address/port.</span></span> <span data-ttu-id="ba98d-183">Legen Sie hierzu [**DatagramSocketControl.MulticastOnly**](/uwp/api/Windows.Networking.Sockets.DatagramSocketControl.MulticastOnly) auf `true` fest, bevor Sie die Bindung oder die Verbindung für das Socket festlegen.</span><span class="sxs-lookup"><span data-stu-id="ba98d-183">You do this by setting the [**DatagramSocketControl.MulticastOnly**](/uwp/api/Windows.Networking.Sockets.DatagramSocketControl.MulticastOnly) to `true` before binding or connecting the socket.</span></span> <span data-ttu-id="ba98d-184">Sie greifen auf eine Instanz von **DatagramSocketControl** aus dem **DatagramSocket**-Objekt selbst über seine [**DatagramSocket.Control**](/uwp/api/windows.networking.sockets.datagramsocket.Control)-Eigenschaft zu.</span><span class="sxs-lookup"><span data-stu-id="ba98d-184">You access an instance of **DatagramSocketControl** from the **DatagramSocket** object itself via its [**DatagramSocket.Control**](/uwp/api/windows.networking.sockets.datagramsocket.Control) property.</span></span>

## <a name="providing-a-client-certificate-with-the-streamsocket-class"></a><span data-ttu-id="ba98d-185">Bereitstellen eines Clientzertifikats mit der StreamSocket-Klasse</span><span class="sxs-lookup"><span data-stu-id="ba98d-185">Providing a client certificate with the StreamSocket class</span></span>
<span data-ttu-id="ba98d-186">[**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket) unterstützt die Verwendung von SSL/TLS zum Authentifizieren des Servers, mit dem der Client kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="ba98d-186">[**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket) supports using SSL/TLS to authenticate the server that the client app is talking to.</span></span> <span data-ttu-id="ba98d-187">In einigen Fällen muss die Client-App selbst mit einem SSL/TLS-Clientzertifikat am Server authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="ba98d-187">In some cases, the client app needs to authenticate itself to the server using an SSL/TLS client certificate.</span></span> <span data-ttu-id="ba98d-188">Sie können ein Clientzertifikat mit der [**StreamSocketControl.ClientCertificate**](/uwp/api/windows.networking.sockets.streamsocketcontrol.ClientCertificate)-Eigenschaft bereitstellen, bevor Sie die Bindung oder die Verbindung für das Socket festlegen (dies muss festgelegt werden, bevor der SSL/TLS-Handshake gestartet wird).</span><span class="sxs-lookup"><span data-stu-id="ba98d-188">You can provide a client certificate with the [**StreamSocketControl.ClientCertificate**](/uwp/api/windows.networking.sockets.streamsocketcontrol.ClientCertificate) property before binding or connecting the socket (it must be set before the SSL/TLS handshake is started).</span></span> <span data-ttu-id="ba98d-189">Sie greifen auf eine Instanz von **StreamSocketControl** aus dem **StreamSocket**-Objekt selbst über seine [**StreamSocket.Control**](/uwp/api/windows.networking.sockets.streamsocket.Control)-Eigenschaft zu.</span><span class="sxs-lookup"><span data-stu-id="ba98d-189">You access an instance of **StreamSocketControl** from the **StreamSocket** object itself via its [**StreamSocket.Control**](/uwp/api/windows.networking.sockets.streamsocket.Control) property.</span></span> <span data-ttu-id="ba98d-190">Wenn der Server das Clientzertifikat anfordert, reagiert Windows mit dem Clientzertifikat, das Sie bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="ba98d-190">If the server requests the client certificate then Windows will respond with the client certificate that you provided.</span></span>

<span data-ttu-id="ba98d-191">Verwenden Sie eine Außerkraftsetzung der [**StreamSocket.ConnectAsync**](/uwp/api/windows.networking.sockets.streamsocket.connectasync), die ein [**SocketProtectionLevel**](/uwp/api/windows.networking.sockets.socketprotectionlevel) annimmt, wie in diesem Beispiel mit minimalem Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ba98d-191">Use an override of [**StreamSocket.ConnectAsync**](/uwp/api/windows.networking.sockets.streamsocket.connectasync) that takes a [**SocketProtectionLevel**](/uwp/api/windows.networking.sockets.socketprotectionlevel), as shown in this minimal code example.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba98d-192">Wie durch den Kommentar in den folgenden Codebeispielen angegeben, muss Ihr Projekt die sharedUserCertificates-App-Funktion deklarieren, damit dieser Code funktioniert.</span><span class="sxs-lookup"><span data-stu-id="ba98d-192">As indicated by the comment in the code examples below, your project needs to declare the sharedUserCertificates app capability for this code to work.</span></span>

```csharp
// For this code to work, you need at least one certificate to be present in the user MY certificate store.
// Plugging a smartcard into a smartcard reader connected to your PC will achieve that.
// Also, your project needs to declare the sharedUserCertificates app capability.
var certificateQuery = new Windows.Security.Cryptography.Certificates.CertificateQuery();
certificateQuery.StoreName = "MY";
IReadOnlyList<Windows.Security.Cryptography.Certificates.Certificate> certificates = await Windows.Security.Cryptography.Certificates.CertificateStores.FindAllAsync(certificateQuery);
if (certificates.Count > 0)
{
    streamSocket.Control.ClientCertificate = certificates[0];
    await streamSocket.ConnectAsync(hostName, "1337", Windows.Networking.Sockets.SocketProtectionLevel.Tls12);
}
```

```cppwinrt
// For this code to work, you need at least one certificate to be present in the user MY certificate store.
// Plugging a smartcard into a smartcard reader connected to your PC will achieve that.
// Also, your project needs to declare the sharedUserCertificates app capability.
Windows::Security::Cryptography::Certificates::CertificateQuery certificateQuery;
certificateQuery.StoreName(L"MY");
IVectorView< Windows::Security::Cryptography::Certificates::Certificate > certificates = co_await Windows::Security::Cryptography::Certificates::CertificateStores::FindAllAsync(certificateQuery);

if (certificates.Size() > 0)
{
    m_streamSocket.Control().ClientCertificate(certificates.GetAt(0));
    co_await m_streamSocket.ConnectAsync(Windows::Networking::HostName{ L"localhost" }, L"1337", Windows::Networking::Sockets::SocketProtectionLevel::Tls12);
    ...
}
```

```cpp
// For this code to work, you need at least one certificate to be present in the user MY certificate store.
// Plugging a smartcard into a smartcard reader connected to your PC will achieve that.
// Also, your project needs to declare the sharedUserCertificates app capability.
auto certificateQuery = ref new Windows::Security::Cryptography::Certificates::CertificateQuery();
certificateQuery->StoreName = L"MY";
Concurrency::create_task(Windows::Security::Cryptography::Certificates::CertificateStores::FindAllAsync(certificateQuery)).then(
    [=](IVectorView< Windows::Security::Cryptography::Certificates::Certificate^ >^ certificates)
{
    if (certificates->Size > 0)
    {
        this->streamSocket->Control->ClientCertificate = certificates->GetAt(0);
        Concurrency::create_task(this->streamSocket->ConnectAsync(ref new Windows::Networking::HostName(L"localhost"), L"1337", Windows::Networking::Sockets::SocketProtectionLevel::Tls12)).then(
            [=]
        {
            ...
        });
    }
});
```

## <a name="handling-exceptions"></a><span data-ttu-id="ba98d-193">Behandeln von Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="ba98d-193">Handling exceptions</span></span>
<span data-ttu-id="ba98d-194">Ein Fehler in einem [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket)-, [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket)- oder [**StreamSocketListener**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener)-Vorgang wird als **HRESULT**-Wert zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ba98d-194">An error encountered on a [**DatagramSocket**](/uwp/api/Windows.Networking.Sockets.DatagramSocket), [**StreamSocket**](/uwp/api/Windows.Networking.Sockets.StreamSocket), or [**StreamSocketListener**](/uwp/api/Windows.Networking.Sockets.StreamSocketListener) operation is returned as an **HRESULT** value.</span></span> <span data-ttu-id="ba98d-195">Sie können diesen **HRESULT**-Wert der [**SocketError.GetStatus**](/uwp/api/windows.networking.sockets.socketerror.getstatus) -Methode übergeben, um ihn in einen [**SocketErrorStatus**](/uwp/api/Windows.Networking.Sockets.SocketErrorStatus)-Enumerationswert zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="ba98d-195">You can pass that **HRESULT** value to the [**SocketError.GetStatus**](/uwp/api/windows.networking.sockets.socketerror.getstatus) method to convert it into a [**SocketErrorStatus**](/uwp/api/Windows.Networking.Sockets.SocketErrorStatus) enumeration value.</span></span>

<span data-ttu-id="ba98d-196">Die meisten **SocketErrorStatus**-Enumerationswerte entsprechen einem vom systemeigenen WindowsSockets-Vorgang zurückgegebenen Fehler.</span><span class="sxs-lookup"><span data-stu-id="ba98d-196">Most **SocketErrorStatus** enumeration values correspond to an error returned by the native Windows sockets operation.</span></span> <span data-ttu-id="ba98d-197">Ihre App kann bestimmte **SocketErrorStatus**-Enumerationswerte einschalten, um das App-Verhalten je nach Ausnahmeursache zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ba98d-197">Your app can switch on **SocketErrorStatus** enumeration values to modify app behavior depending on the cause of the exception.</span></span>

<span data-ttu-id="ba98d-198">Bei Parameterprüfungsfehlern können Sie den **HRESULT**-Wert aus der Ausnahme verwenden, um ausführlichere Informationen zum Fehler zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ba98d-198">For parameter validation errors, you can use the **HRESULT** from the exception to learn more detailed information about the error.</span></span> <span data-ttu-id="ba98d-199">Mögliche **HRESULT**-Werte sind in `Winerror.h` aufgelistet; dies finden Sie in Ihrer SDK-Installation (z.B. im Ordner `C:\Program Files (x86)\Windows Kits\10\Include\<VERSION>\shared`).</span><span class="sxs-lookup"><span data-stu-id="ba98d-199">Possible **HRESULT** values are listed in `Winerror.h`, which can be found in your SDK installation (for example, in the folder `C:\Program Files (x86)\Windows Kits\10\Include\<VERSION>\shared`).</span></span> <span data-ttu-id="ba98d-200">Für die meisten Parameterüberprüfungsfehler wird der **HRESULT**-Wert **E_INVALIDARG** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ba98d-200">For most parameter validation errors, the **HRESULT** returned is **E_INVALIDARG**.</span></span>

<span data-ttu-id="ba98d-201">Der [**HostName**](/uwp/api/Windows.Networking.HostName)-Konstruktor kann eine Ausnahme auslösen, wenn die übergebene Zeichenfolge kein gültiger Hostname ist.</span><span class="sxs-lookup"><span data-stu-id="ba98d-201">The [**HostName**](/uwp/api/Windows.Networking.HostName) constructor can throw an exception if the string passed is not a valid host name.</span></span> <span data-ttu-id="ba98d-202">Beispielsweise enthält es Zeichen, die nicht zulässig sind, was wahrscheinlich ist, wenn der Hostname in Ihrer App vom Benutzer eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="ba98d-202">For example, it contains characters that are not allowed, which is likely if the host name is typed in to your app by the user.</span></span> <span data-ttu-id="ba98d-203">Erstellen Sie einen **HostName** in einem try/catch-Block.</span><span class="sxs-lookup"><span data-stu-id="ba98d-203">Construct a **HostName** inside a try/catch block.</span></span> <span data-ttu-id="ba98d-204">Auf diese Weise kann die App, wenn eine Ausnahme ausgelöst wird, den Benutzer benachrichtigen und einen neuen Hostnamen anfordern.</span><span class="sxs-lookup"><span data-stu-id="ba98d-204">That way, if an exception is thrown, the app can notify the user and request a new host name.</span></span>

## <a name="important-apis"></a><span data-ttu-id="ba98d-205">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="ba98d-205">Important APIs</span></span>
* [<span data-ttu-id="ba98d-206">CertificateQuery</span><span class="sxs-lookup"><span data-stu-id="ba98d-206">CertificateQuery</span></span>](/uwp/api/windows.security.cryptography.certificates.certificatequery)
* [<span data-ttu-id="ba98d-207">CertificateStores.FindAllAsync</span><span class="sxs-lookup"><span data-stu-id="ba98d-207">CertificateStores.FindAllAsync</span></span>](/uwp/api/windows.security.cryptography.certificates.certificatestores.findallasync)
* [<span data-ttu-id="ba98d-208">DatagramSocket</span><span class="sxs-lookup"><span data-stu-id="ba98d-208">DatagramSocket</span></span>](/uwp/api/Windows.Networking.Sockets.DatagramSocket)
* [<span data-ttu-id="ba98d-209">DatagramSocket.BindServiceNameAsync</span><span class="sxs-lookup"><span data-stu-id="ba98d-209">DatagramSocket.BindServiceNameAsync</span></span>](/uwp/api/windows.networking.sockets.datagramsocket.bindservicenameasync)
* [<span data-ttu-id="ba98d-210">DatagramSocket.Control</span><span class="sxs-lookup"><span data-stu-id="ba98d-210">DatagramSocket.Control</span></span>](/uwp/api/windows.networking.sockets.datagramsocket.Control)
* [<span data-ttu-id="ba98d-211">DatagramSocket.GetOutputStreamAsync</span><span class="sxs-lookup"><span data-stu-id="ba98d-211">DatagramSocket.GetOutputStreamAsync</span></span>](/uwp/api/windows.networking.sockets.datagramsocket.getoutputstreamasync)
* [<span data-ttu-id="ba98d-212">DatagramSocket.MessageReceived</span><span class="sxs-lookup"><span data-stu-id="ba98d-212">DatagramSocket.MessageReceived</span></span>](/uwp/api/Windows.Networking.Sockets.DatagramSocket.MessageReceived)
* [<span data-ttu-id="ba98d-213">DatagramSocketControl.MulticastOnly</span><span class="sxs-lookup"><span data-stu-id="ba98d-213">DatagramSocketControl.MulticastOnly</span></span>](/uwp/api/Windows.Networking.Sockets.DatagramSocketControl.MulticastOnly)
* [<span data-ttu-id="ba98d-214">DatagramSocketMessageReceivedEventArgs</span><span class="sxs-lookup"><span data-stu-id="ba98d-214">DatagramSocketMessageReceivedEventArgs</span></span>](/uwp/api/windows.networking.sockets.datagramsocketmessagereceivedeventargs)
* [<span data-ttu-id="ba98d-215">DatagramSocketMessageReceivedEventArgs.GetDataReader</span><span class="sxs-lookup"><span data-stu-id="ba98d-215">DatagramSocketMessageReceivedEventArgs.GetDataReader</span></span>](/uwp/api/windows.networking.sockets.datagramsocketmessagereceivedeventargs.GetDataReader)
* [<span data-ttu-id="ba98d-216">DataReader.LoadAsync</span><span class="sxs-lookup"><span data-stu-id="ba98d-216">DataReader.LoadAsync</span></span>](/uwp/api/windows.storage.streams.datareader.loadasync)
* [<span data-ttu-id="ba98d-217">IOutputStream.FlushAsync</span><span class="sxs-lookup"><span data-stu-id="ba98d-217">IOutputStream.FlushAsync</span></span>](/uwp/api/windows.storage.streams.ioutputstream.FlushAsync)
* [<span data-ttu-id="ba98d-218">SocketError.GetStatus</span><span class="sxs-lookup"><span data-stu-id="ba98d-218">SocketError.GetStatus</span></span>](/uwp/api/windows.networking.sockets.socketerror.getstatus)
* [<span data-ttu-id="ba98d-219">SocketErrorStatus</span><span class="sxs-lookup"><span data-stu-id="ba98d-219">SocketErrorStatus</span></span>](/uwp/api/Windows.Networking.Sockets.SocketErrorStatus)
* [<span data-ttu-id="ba98d-220">SocketProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="ba98d-220">SocketProtectionLevel</span></span>](/uwp/api/windows.networking.sockets.socketprotectionlevel)
* [<span data-ttu-id="ba98d-221">StreamSocket</span><span class="sxs-lookup"><span data-stu-id="ba98d-221">StreamSocket</span></span>](/uwp/api/Windows.Networking.Sockets.StreamSocket)
* [<span data-ttu-id="ba98d-222">StreamSocketControl.ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="ba98d-222">StreamSocketControl.ClientCertificate</span></span>](/uwp/api/windows.networking.sockets.streamsocketcontrol.ClientCertificate)
* [<span data-ttu-id="ba98d-223">StreamSocket.ConnectAsync</span><span class="sxs-lookup"><span data-stu-id="ba98d-223">StreamSocket.ConnectAsync</span></span>](/uwp/api/windows.networking.sockets.streamsocket.connectasync)
* [<span data-ttu-id="ba98d-224">StreamSocket.InputStream</span><span class="sxs-lookup"><span data-stu-id="ba98d-224">StreamSocket.InputStream</span></span>](/uwp/api/windows.networking.sockets.streamsocket.InputStream)
* [<span data-ttu-id="ba98d-225">StreamSocket.OutputStream</span><span class="sxs-lookup"><span data-stu-id="ba98d-225">StreamSocket.OutputStream</span></span>](/uwp/api/windows.networking.sockets.streamsocket.OutputStream)
* [<span data-ttu-id="ba98d-226">StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="ba98d-226">StreamSocketListener</span></span>](/uwp/api/Windows.Networking.Sockets.StreamSocketListener)
* [<span data-ttu-id="ba98d-227">StreamSocketListener.BindServiceNameAsync</span><span class="sxs-lookup"><span data-stu-id="ba98d-227">StreamSocketListener.BindServiceNameAsync</span></span>](/uwp/api/windows.networking.sockets.streamsocketlistener.bindservicenameasync)
* [<span data-ttu-id="ba98d-228">StreamSocketListener.ConnectionReceived</span><span class="sxs-lookup"><span data-stu-id="ba98d-228">StreamSocketListener.ConnectionReceived</span></span>](/uwp/api/Windows.Networking.Sockets.StreamSocketListener.ConnectionReceived)
* [<span data-ttu-id="ba98d-229">StreamSocketListenerConnectionReceivedEventArgs</span><span class="sxs-lookup"><span data-stu-id="ba98d-229">StreamSocketListenerConnectionReceivedEventArgs</span></span>](/uwp/api/windows.networking.sockets.streamsocketlistenerconnectionreceivedeventargs)
* [<span data-ttu-id="ba98d-230">Windows.Networking.Sockets</span><span class="sxs-lookup"><span data-stu-id="ba98d-230">Windows.Networking.Sockets</span></span>](/uwp/api/Windows.Networking.Sockets)

## <a name="related-topics"></a><span data-ttu-id="ba98d-231">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ba98d-231">Related topics</span></span>
* [<span data-ttu-id="ba98d-232">App zu App-Kommunikation</span><span class="sxs-lookup"><span data-stu-id="ba98d-232">App-to-app communication</span></span>](/windows/uwp/app-to-app/index)
* [<span data-ttu-id="ba98d-233">Parallelität und asynchrone Vorgänge mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="ba98d-233">Concurrency and asynchronous operations with C++/WinRT</span></span>](/windows/uwp/cpp-and-winrt-apis/concurrency)
* [<span data-ttu-id="ba98d-234">So wird's gemacht: Festlegen von Netzwerkfunktionen</span><span class="sxs-lookup"><span data-stu-id="ba98d-234">How to set network capabilities</span></span>](https://msdn.microsoft.com/library/windows/apps/hh770532.aspx)
* [<span data-ttu-id="ba98d-235">Windows Sockets 2 (Winsock)</span><span class="sxs-lookup"><span data-stu-id="ba98d-235">Windows Sockets 2 (Winsock)</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms740673)

## <a name="samples"></a><span data-ttu-id="ba98d-236">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ba98d-236">Samples</span></span>
* [<span data-ttu-id="ba98d-237">StreamSocket-Beispiel</span><span class="sxs-lookup"><span data-stu-id="ba98d-237">StreamSocket sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620609)
