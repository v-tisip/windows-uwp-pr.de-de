---
author: laurenhughes
ms.assetid: 27914C0A-2A02-473F-BDD5-C931E3943AA0
title: Erstellen, Schreiben und Lesen einer Datei
description: Lesen und Schreiben Sie eine Datei mithilfe eines StorageFile-Objekts.
ms.author: lahugh
ms.date: 06/28/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
- vb
ms.openlocfilehash: 9bc19460fe1b9b9c6b637606a737e1157d98feef
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6201365"
---
# <a name="create-write-and-read-a-file"></a>Erstellen, Schreiben und Lesen einer Datei

**Wichtige APIs**

-   [**StorageFolder-Klasse**](/uwp/api/windows.storage.storagefolder)
-   [**StorageFile-Klasse**](/uwp/api/windows.storage.storagefile)
-   [**FileIO-Klasse**](/uwp/api/windows.storage.fileio)

Lesen und Schreiben Sie eine Datei mithilfe eines [**StorageFile**](/uwp/api/windows.storage.storagefile)-Objekts.

> [!NOTE]
> Siehe auch das [Dateizugriff-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619995).

## <a name="prerequisites"></a>Voraussetzungen

-   **Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)**

    Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic). Informationen zum Schreiben von asynchronen apps in C++ / WinRT, finden Sie unter [Parallelität und asynchrone Vorgänge mit C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency). Informationen zum Schreiben von asynchronen apps in C++ / CX finden Sie unter [asynchrone Programmierung in C++ / CX](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

-   **Kenntnis, wie die Datei abgerufen wird, aus der Sie lesen und/oder in die Sie schreiben möchten**

    Unter [Öffnen von Dateien und Ordnern mit einer Auswahl](quickstart-using-file-and-folder-pickers.md) erfahren Sie, wie Sie eine Datei mit einer Dateiauswahl abrufen können.

## <a name="creating-a-file"></a>Erstellen einer Datei

Nachfolgend finden Sie Informationen zum Erstellen einer Datei im lokalen Ordner der App. Wenn sie bereits vorhanden ist, ersetzen Sie sie.

```csharp
// Create sample file; replace if exists.
Windows.Storage.StorageFolder storageFolder =
    Windows.Storage.ApplicationData.Current.LocalFolder;
Windows.Storage.StorageFile sampleFile =
    await storageFolder.CreateFileAsync("sample.txt",
        Windows.Storage.CreationCollisionOption.ReplaceExisting);
```

```cppwinrt
// MainPage.h
#include <winrt/Windows.Storage.h>
...
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    // Create a sample file; replace if exists.
    Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
    co_await storageFolder.CreateFileAsync(L"sample.txt", Windows::Storage::CreationCollisionOption::ReplaceExisting);
}
```

```cpp
// Create a sample file; replace if exists.
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
concurrency::create_task(storageFolder->CreateFileAsync("sample.txt", CreationCollisionOption::ReplaceExisting));
```

```vb
' Create sample file; replace if exists.
Dim storageFolder As StorageFolder = Windows.Storage.ApplicationData.Current.LocalFolder
Dim sampleFile As StorageFile = Await storageFolder.CreateFileAsync("sample.txt", CreationCollisionOption.ReplaceExisting)
```

## <a name="writing-to-a-file"></a>Schreiben in eine Datei

Im Folgenden finden Sie Informationen zum Schreiben in eine beschreibbare Datei auf dem Datenträger mithilfe der [**StorageFile**](/uwp/api/windows.storage.storagefile)-Klasse. Der allgemein erste Schritt für die verschiedenen Methoden zum Schreiben in eine Datei ist das Abrufen der Datei mit [**StorageFolder.GetFileAsync**](/uwp/api/windows.storage.storagefolder.getfileasync). (Es sei denn, Sie schreiben sofort nach dem Erstellen in die Datei.)

```csharp
Windows.Storage.StorageFolder storageFolder =
    Windows.Storage.ApplicationData.Current.LocalFolder;
Windows.Storage.StorageFile sampleFile =
    await storageFolder.GetFileAsync("sample.txt");
```

```cppwinrt
// MainPage.h
#include <winrt/Windows.Storage.h>
...
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
    auto sampleFile{ co_await storageFolder.CreateFileAsync(L"sample.txt", Windows::Storage::CreationCollisionOption::ReplaceExisting) };
    // Process sampleFile
}
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile) 
{
    // Process file
});
```

```vb
Dim storageFolder As StorageFolder = Windows.Storage.ApplicationData.Current.LocalFolder
Dim sampleFile As StorageFile = Await storageFolder.GetFileAsync("sample.txt")
```

**Schreiben von Text in eine Datei**

Schreiben von Text in der Datei durch Aufrufen der [**FileIO.WriteTextAsync**](/uwp/api/windows.storage.fileio.writetextasync) -Methode.

```csharp
await Windows.Storage.FileIO.WriteTextAsync(sampleFile, "Swift as a shadow");
```

```cppwinrt
// MainPage.h
#include <winrt/Windows.Storage.h>
...
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
    auto sampleFile{ co_await storageFolder.GetFileAsync(L"sample.txt") };
    // Write text to the file.
    co_await Windows::Storage::FileIO::WriteTextAsync(sampleFile, L"Swift as a shadow");
}
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile) 
{
    //Write text to a file
    create_task(FileIO::WriteTextAsync(sampleFile, "Swift as a shadow"));
});
```

```vb
Await Windows.Storage.FileIO.WriteTextAsync(sampleFile, "Swift as a shadow")
```

**Schreiben von Bytes in eine Datei mithilfe eines Puffers (2 Schritte)**

1.  Rufen Sie zuerst [**CryptographicBuffer.ConvertStringToBinary**](/uwp/api/windows.security.cryptography.cryptographicbuffer.convertstringtobinary) einen Puffer von Bytes (basierend auf einer Zeichenfolge) abrufen, die Sie in Ihrer Datei schreiben möchten.

```csharp
var buffer = Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(
    "What fools these mortals be", Windows.Security.Cryptography.BinaryStringEncoding.Utf8);
```

```cppwinrt
// MainPage.h
#include <winrt/Windows.Security.Cryptography.h>
#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
...
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
    auto sampleFile{ co_await storageFolder.GetFileAsync(L"sample.txt") };
    // Create the buffer.
    Windows::Storage::Streams::IBuffer buffer{
        Windows::Security::Cryptography::CryptographicBuffer::ConvertStringToBinary(
            L"What fools these mortals be", Windows::Security::Cryptography::BinaryStringEncoding::Utf8)};
    // The code in step 2 goes here.
}
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile)
{
    // Create the buffer
    IBuffer^ buffer = CryptographicBuffer::ConvertStringToBinary
    ("What fools these mortals be", BinaryStringEncoding::Utf8);
});
```

```vb
Dim buffer = Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(
    "What fools these mortals be",
    Windows.Security.Cryptography.BinaryStringEncoding.Utf8)
```

2.  Schreiben Sie dann die Bytes aus dem Puffer in die Datei durch Aufrufen der [**FileIO.WriteBufferAsync**](/uwp/api/windows.storage.fileio.writebufferasync) -Methode.

```csharp
await Windows.Storage.FileIO.WriteBufferAsync(sampleFile, buffer);
```

```cppwinrt
co_await Windows::Storage::FileIO::WriteBufferAsync(sampleFile, buffer);
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile)
{
    // Create the buffer
    IBuffer^ buffer = CryptographicBuffer::ConvertStringToBinary
    ("What fools these mortals be", BinaryStringEncoding::Utf8);      
    // Write bytes to a file using a buffer
    create_task(FileIO::WriteBufferAsync(sampleFile, buffer));
});
```

```vb
Await Windows.Storage.FileIO.WriteBufferAsync(sampleFile, buffer)
```

**Schreiben von Text in eine Datei mithilfe eines Datenstroms (4 Schritte)**

1.  Öffnen Sie zunächst die Datei durch Aufrufen der [**StorageFile.OpenAsync**](/uwp/api/windows.storage.storagefile.openasync)-Methode. Wenn der Vorgang zum Öffnen abgeschlossen ist, wird ein Datenstrom des Dateiinhalts zurückgegeben.

```csharp
var stream = await sampleFile.OpenAsync(Windows.Storage.FileAccessMode.ReadWrite);
```

```cppwinrt
// MainPage.h
#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
...
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
    auto sampleFile{ co_await storageFolder.GetFileAsync(L"sample.txt") };
    Windows::Storage::Streams::IRandomAccessStream stream{ co_await sampleFile.OpenAsync(Windows::Storage::FileAccessMode::ReadWrite) };
    // The code in step 2 goes here.
}
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile)
{
    create_task(sampleFile->OpenAsync(FileAccessMode::ReadWrite)).then([sampleFile](IRandomAccessStream^ stream)
    {
        // Process stream
    });
});
```

```vb
Dim stream = Await sampleFile.OpenAsync(Windows.Storage.FileAccessMode.ReadWrite)
```

2.  Als Nächstes rufen Sie einen Ausgabedatenstrom durch Aufrufen der Methode [**IRandomAccessStream.GetOutputStreamAt**](/uwp/api/windows.storage.streams.irandomaccessstream.getoutputstreamat) aus der `stream`. Wenn Sie c# verwenden, setzen Sie dies in einer **using** -Anweisung, um den Ausgabestream Lebensdauer zu verwalten. Wenn Sie verwenden [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), können Sie ihrer gesamten Lebensdauer steuern, indem Sie es in einem Block einzuschließen, oder auf `nullptr` Wenn Sie damit fertig sind.

```csharp
using (var outputStream = stream.GetOutputStreamAt(0))
{
    // We'll add more code here in the next step.
}
stream.Dispose(); // Or use the stream variable (see previous code snippet) with a using statement as well.
```

```cppwinrt
Windows::Storage::Streams::IOutputStream outputStream{ stream.GetOutputStreamAt(0) };
// The code in step 3 goes here.
```

```cpp
// Add to "Process stream" in part 1
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

```vb
Using outputStream = stream.GetOutputStreamAt(0)
' We'll add more code here in the next step.
End Using
```

3.  Jetzt fügen Sie code (Wenn Sie c#, innerhalb der vorhandenen **using** -Anweisung verwenden), um in den Ausgabedatenstrom zu schreiben, indem Sie ein neues [**DataWriter**](/uwp/api/windows.storage.streams.datawriter) -Objekt erstellt und die [**DataWriter.WriteString**](/uwp/api/windows.storage.streams.datawriter.writestring) -Methode aufrufen.

```csharp
using (var dataWriter = new Windows.Storage.Streams.DataWriter(outputStream))
{
    dataWriter.WriteString("DataWriter has methods to write to various types, such as DataTimeOffset.");
}
```

```cppwinrt
Windows::Storage::Streams::DataWriter dataWriter;
dataWriter.WriteString(L"DataWriter has methods to write to various types, such as DataTimeOffset.");
// The code in step 4 goes here.
```

```cpp
// Added after code from part 2
DataWriter^ dataWriter = ref new DataWriter(outputStream);
dataWriter->WriteString("DataWriter has methods to write to various types, such as DataTimeOffset.");
```

```vb
Dim dataWriter As New DataWriter(outputStream)
dataWriter.WriteString("DataWriter has methods to write to various types, such as DataTimeOffset.")
```

4.  Abschließend fügen Sie code (Wenn Sie c#, innerhalb der inneren **mithilfe von** -Anweisung verwenden), um den Text in die Datei mit [**DataWriter.StoreAsync**](/uwp/api/windows.storage.streams.datawriter.storeasync) speichern und schließen den Datenstrom mit [**IOutputStream.FlushAsync**](/uwp/api/windows.storage.streams.ioutputstream.flushasync).

```csharp
await dataWriter.StoreAsync();
await outputStream.FlushAsync();
```

```cppwinrt
dataWriter.StoreAsync();
outputStream.FlushAsync();
```

```cpp
// Added after code from part 3
dataWriter->StoreAsync();
outputStream->FlushAsync();
```

```vb
Await dataWriter.StoreAsync()
Await outputStream.FlushAsync()
```

## <a name="reading-from-a-file"></a>Lesen aus einer Datei

Nachfolgend finden Sie Informationen zum Lesen aus einer Datei auf dem Datenträger mithilfe der [**StorageFile**](/uwp/api/Windows.Storage.StorageFile)-Klasse. Der allgemein erste Schritt für die einzelnen Methoden zum Lesen von Daten aus einer Datei ist das Abrufen der Datei mit [**StorageFolder.GetFileAsync**](/uwp/api/windows.storage.storagefolder.getfileasync).

```csharp
Windows.Storage.StorageFolder storageFolder =
    Windows.Storage.ApplicationData.Current.LocalFolder;
Windows.Storage.StorageFile sampleFile =
    await storageFolder.GetFileAsync("sample.txt");
```

```cppwinrt
Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
auto sampleFile{ co_await storageFolder.GetFileAsync(L"sample.txt") };
// Process file
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile)
{
    // Process file
});
```

```vb
Dim storageFolder As StorageFolder = Windows.Storage.ApplicationData.Current.LocalFolder
Dim sampleFile As StorageFile = Await storageFolder.GetFileAsync("sample.txt")
```

**Lesen von Text aus einer Datei**

Lesen von Text aus einer Datei durch Aufrufen der [**FileIO.ReadTextAsync**](/uwp/api/windows.storage.fileio.readtextasync) -Methode.

```csharp
string text = await Windows.Storage.FileIO.ReadTextAsync(sampleFile);
```

```cppwinrt
Windows::Foundation::IAsyncOperation<winrt::hstring> ExampleCoroutineAsync()
{
    Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
    auto sampleFile{ co_await storageFolder.GetFileAsync(L"sample.txt") };
    co_return co_await Windows::Storage::FileIO::ReadTextAsync(sampleFile);
}
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile)
{
    return FileIO::ReadTextAsync(sampleFile);
});
```

```vb
Dim text As String = Await Windows.Storage.FileIO.ReadTextAsync(sampleFile)
```

**Lesen von Text aus einer Datei mithilfe eines Puffers (2 Schritte)**

1.  Rufen Sie zuerst die Methode [**FileIO.ReadBufferAsync**](/uwp/api/windows.storage.fileio.readbufferasync) .

```csharp
var buffer = await Windows.Storage.FileIO.ReadBufferAsync(sampleFile);
```

```cppwinrt
Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
auto sampleFile{ co_await storageFolder.GetFileAsync(L"sample.txt") };
Windows::Storage::Streams::IBuffer buffer{ co_await Windows::Storage::FileIO::ReadBufferAsync(sampleFile) };
// The code in step 2 goes here.
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile)
{
    return FileIO::ReadBufferAsync(sampleFile);

}).then([](Streams::IBuffer^ buffer)
{
    // Process buffer
});
```

```vb
Dim buffer = Await Windows.Storage.FileIO.ReadBufferAsync(sampleFile)
```

2.  Verwenden Sie dann ein [**DataReader**](/uwp/api/windows.storage.streams.datareader)-Objekt, um zunächst die Länge des Puffers und dann dessen Inhalt zu lesen.

```csharp
using (var dataReader = Windows.Storage.Streams.DataReader.FromBuffer(buffer))
{
    string text = dataReader.ReadString(buffer.Length);
}
```

```cppwinrt
auto dataReader{ Windows::Storage::Streams::DataReader::FromBuffer(buffer) };
winrt::hstring bufferText{ dataReader.ReadString(buffer.Length()) };
```

```cpp
// Add to "Process buffer" section from part 1
auto dataReader = DataReader::FromBuffer(buffer);
String^ bufferText = dataReader->ReadString(buffer->Length);
```

```vb
Dim dataReader As DataReader = Windows.Storage.Streams.DataReader.FromBuffer(buffer)
Dim text As String = dataReader.ReadString(buffer.Length)
```

**Lesen von Text aus einer Datei mithilfe eines Datenstroms (4 Schritte)**

1.  Öffnen Sie einen Datenstrom für die Datei, indem Sie die [**StorageFile.OpenAsync**](/uwp/api/windows.storage.storagefile.openasync)-Methode aufrufen. Wenn der Vorgang abgeschlossen ist, wird ein Datenstrom des Dateiinhalts zurückgegeben.

```csharp
var stream = await sampleFile.OpenAsync(Windows.Storage.FileAccessMode.Read);
```

```cppwinrt
Windows::Storage::StorageFolder storageFolder{ Windows::Storage::ApplicationData::Current().LocalFolder() };
auto sampleFile{ co_await storageFolder.GetFileAsync(L"sample.txt") };
Windows::Storage::Streams::IRandomAccessStream stream{ co_await sampleFile.OpenAsync(Windows::Storage::FileAccessMode::Read) };
// The code in step 2 goes here.
```

```cpp
StorageFolder^ storageFolder = ApplicationData::Current->LocalFolder;
create_task(storageFolder->GetFileAsync("sample.txt")).then([](StorageFile^ sampleFile)
{
    create_task(sampleFile->OpenAsync(FileAccessMode::Read)).then([sampleFile](IRandomAccessStream^ stream)
    {
        // Process stream
    });
});
```

```vb
Dim stream = Await sampleFile.OpenAsync(Windows.Storage.FileAccessMode.Read)
```

2.  Rufen Sie die Größe des Datenstroms zur späteren Verwendung ab.

```csharp
ulong size = stream.Size;
```

```cppwinrt
uint64_t size{ stream.Size() };
// The code in step 3 goes here.
```

```cpp
// Add to "Process stream" from part 1
UINT64 size = stream->Size;
```

```vb
Dim size = stream.Size
```

3.  Rufen Sie einen Eingabedatenstrom durch Aufrufen der [**IRandomAccessStream.GetInputStreamAt**](/uwp/api/windows.storage.streams.irandomaccessstream.getinputstreamat) -Methode. Fügen Sie ihn in eine **using**-Anweisung ein, um die Lebensdauer des Eingabedatenstroms zu verwalten. Geben Sie beim Aufrufen von **GetInputStreamAt** 0 an, um die Position auf den Anfang des Datenstroms festzulegen.

```csharp
using (var inputStream = stream.GetInputStreamAt(0))
{
    // We'll add more code here in the next step.
}
```

```cppwinrt
Windows::Storage::Streams::IInputStream inputStream{ stream.GetInputStreamAt(0) };
Windows::Storage::Streams::DataReader dataReader{ inputStream };
// The code in step 4 goes here.
```

```cpp
// Add after code from part 2
IInputStream^ inputStream = stream->GetInputStreamAt(0);
auto dataReader = ref new DataReader(inputStream);
```

```vb
Using inputStream = stream.GetInputStreamAt(0)
' We'll add more code here in the next step.
End Using
```

4.  Abschließend fügen Sie diesen Code in die vorhandene **using**-Anweisung zum Abrufen eines [**DataReader**](/uwp/api/windows.storage.streams.datareader)-Objekts im Datenstrom ein. Lesen Sie dann den Text durch den Aufruf von [**DataReader.LoadAsync**](/uwp/api/windows.storage.streams.datareader.loadasync) und [**DataReader.ReadString**](/uwp/api/windows.storage.streams.datareader.readstring).

```csharp
using (var dataReader = new Windows.Storage.Streams.DataReader(inputStream))
{
    uint numBytesLoaded = await dataReader.LoadAsync((uint)size);
    string text = dataReader.ReadString(numBytesLoaded);
}
```

```cppwinrt
unsigned int cBytesLoaded{ co_await dataReader.LoadAsync(size) };
winrt::hstring streamText{ dataReader.ReadString(cBytesLoaded) };
```

```cpp
// Add after code from part 3
create_task(dataReader->LoadAsync(size)).then([sampleFile, dataReader](unsigned int numBytesLoaded)
{
    String^ streamText = dataReader->ReadString(numBytesLoaded);
});
```

```vb
Dim dataReader As New DataReader(inputStream)
Dim numBytesLoaded As UInteger = Await dataReader.LoadAsync(CUInt(size))
Dim text As String = dataReader.ReadString(numBytesLoaded)
```
