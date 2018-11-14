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
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6283002"
---
# <a name="create-write-and-read-a-file"></a><span data-ttu-id="52aa3-104">Erstellen, Schreiben und Lesen einer Datei</span><span class="sxs-lookup"><span data-stu-id="52aa3-104">Create, write, and read a file</span></span>

**<span data-ttu-id="52aa3-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="52aa3-105">Important APIs</span></span>**

-   [**<span data-ttu-id="52aa3-106">StorageFolder-Klasse</span><span class="sxs-lookup"><span data-stu-id="52aa3-106">StorageFolder class</span></span>**](/uwp/api/windows.storage.storagefolder)
-   [**<span data-ttu-id="52aa3-107">StorageFile-Klasse</span><span class="sxs-lookup"><span data-stu-id="52aa3-107">StorageFile class</span></span>**](/uwp/api/windows.storage.storagefile)
-   [**<span data-ttu-id="52aa3-108">FileIO-Klasse</span><span class="sxs-lookup"><span data-stu-id="52aa3-108">FileIO class</span></span>**](/uwp/api/windows.storage.fileio)

<span data-ttu-id="52aa3-109">Lesen und Schreiben Sie eine Datei mithilfe eines [**StorageFile**](/uwp/api/windows.storage.storagefile)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="52aa3-109">Read and write a file using a [**StorageFile**](/uwp/api/windows.storage.storagefile) object.</span></span>

> [!NOTE]
> <span data-ttu-id="52aa3-110">Siehe auch das [Dateizugriff-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619995).</span><span class="sxs-lookup"><span data-stu-id="52aa3-110">Also see the [File access sample](http://go.microsoft.com/fwlink/p/?linkid=619995).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52aa3-111">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="52aa3-111">Prerequisites</span></span>

-   **<span data-ttu-id="52aa3-112">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="52aa3-112">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="52aa3-113">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="52aa3-113">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).</span></span> <span data-ttu-id="52aa3-114">Informationen zum Schreiben von asynchronen apps in C++ / WinRT, finden Sie unter [Parallelität und asynchrone Vorgänge mit C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency).</span><span class="sxs-lookup"><span data-stu-id="52aa3-114">To learn how to write asynchronous apps in C++/WinRT, see [Concurrency and asynchronous operations with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency).</span></span> <span data-ttu-id="52aa3-115">Informationen zum Schreiben von asynchronen apps in C++ / CX finden Sie unter [asynchrone Programmierung in C++ / CX](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span><span class="sxs-lookup"><span data-stu-id="52aa3-115">To learn how to write asynchronous apps in C++/CX, see [Asynchronous programming in C++/CX](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span></span>

-   **<span data-ttu-id="52aa3-116">Kenntnis, wie die Datei abgerufen wird, aus der Sie lesen und/oder in die Sie schreiben möchten</span><span class="sxs-lookup"><span data-stu-id="52aa3-116">Know how to get the file that you want to read from, write to, or both</span></span>**

    <span data-ttu-id="52aa3-117">Unter [Öffnen von Dateien und Ordnern mit einer Auswahl](quickstart-using-file-and-folder-pickers.md) erfahren Sie, wie Sie eine Datei mit einer Dateiauswahl abrufen können.</span><span class="sxs-lookup"><span data-stu-id="52aa3-117">You can learn how to get a file by using a file picker in [Open files and folders with a picker](quickstart-using-file-and-folder-pickers.md).</span></span>

## <a name="creating-a-file"></a><span data-ttu-id="52aa3-118">Erstellen einer Datei</span><span class="sxs-lookup"><span data-stu-id="52aa3-118">Creating a file</span></span>

<span data-ttu-id="52aa3-119">Nachfolgend finden Sie Informationen zum Erstellen einer Datei im lokalen Ordner der App.</span><span class="sxs-lookup"><span data-stu-id="52aa3-119">Here's how to create a file in the app's local folder.</span></span> <span data-ttu-id="52aa3-120">Wenn sie bereits vorhanden ist, ersetzen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="52aa3-120">If it already exists, we replace it.</span></span>

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

## <a name="writing-to-a-file"></a><span data-ttu-id="52aa3-121">Schreiben in eine Datei</span><span class="sxs-lookup"><span data-stu-id="52aa3-121">Writing to a file</span></span>

<span data-ttu-id="52aa3-122">Im Folgenden finden Sie Informationen zum Schreiben in eine beschreibbare Datei auf dem Datenträger mithilfe der [**StorageFile**](/uwp/api/windows.storage.storagefile)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="52aa3-122">Here's how to write to a writable file on disk using the [**StorageFile**](/uwp/api/windows.storage.storagefile) class.</span></span> <span data-ttu-id="52aa3-123">Der allgemein erste Schritt für die verschiedenen Methoden zum Schreiben in eine Datei ist das Abrufen der Datei mit [**StorageFolder.GetFileAsync**](/uwp/api/windows.storage.storagefolder.getfileasync). (Es sei denn, Sie schreiben sofort nach dem Erstellen in die Datei.)</span><span class="sxs-lookup"><span data-stu-id="52aa3-123">The common first step for each of the ways of writing to a file (unless you're writing to the file immediately after creating it) is to get the file with [**StorageFolder.GetFileAsync**](/uwp/api/windows.storage.storagefolder.getfileasync).</span></span>

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

**<span data-ttu-id="52aa3-124">Schreiben von Text in eine Datei</span><span class="sxs-lookup"><span data-stu-id="52aa3-124">Writing text to a file</span></span>**

<span data-ttu-id="52aa3-125">Schreiben von Text in der Datei durch Aufrufen der [**FileIO.WriteTextAsync**](/uwp/api/windows.storage.fileio.writetextasync) -Methode.</span><span class="sxs-lookup"><span data-stu-id="52aa3-125">Write text to your file by calling the [**FileIO.WriteTextAsync**](/uwp/api/windows.storage.fileio.writetextasync) method.</span></span>

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

**<span data-ttu-id="52aa3-126">Schreiben von Bytes in eine Datei mithilfe eines Puffers (2 Schritte)</span><span class="sxs-lookup"><span data-stu-id="52aa3-126">Writing bytes to a file by using a buffer (2 steps)</span></span>**

1.  <span data-ttu-id="52aa3-127">Rufen Sie zuerst [**CryptographicBuffer.ConvertStringToBinary**](/uwp/api/windows.security.cryptography.cryptographicbuffer.convertstringtobinary) einen Puffer von Bytes (basierend auf einer Zeichenfolge) abrufen, die Sie in Ihrer Datei schreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="52aa3-127">First, call [**CryptographicBuffer.ConvertStringToBinary**](/uwp/api/windows.security.cryptography.cryptographicbuffer.convertstringtobinary) to get a buffer of the bytes (based on a string) that you want to write to your file.</span></span>

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

2.  <span data-ttu-id="52aa3-128">Schreiben Sie dann die Bytes aus dem Puffer in die Datei durch Aufrufen der [**FileIO.WriteBufferAsync**](/uwp/api/windows.storage.fileio.writebufferasync) -Methode.</span><span class="sxs-lookup"><span data-stu-id="52aa3-128">Then write the bytes from your buffer to your file by calling the [**FileIO.WriteBufferAsync**](/uwp/api/windows.storage.fileio.writebufferasync) method.</span></span>

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

**<span data-ttu-id="52aa3-129">Schreiben von Text in eine Datei mithilfe eines Datenstroms (4 Schritte)</span><span class="sxs-lookup"><span data-stu-id="52aa3-129">Writing text to a file by using a stream (4 steps)</span></span>**

1.  <span data-ttu-id="52aa3-130">Öffnen Sie zunächst die Datei durch Aufrufen der [**StorageFile.OpenAsync**](/uwp/api/windows.storage.storagefile.openasync)-Methode.</span><span class="sxs-lookup"><span data-stu-id="52aa3-130">First, open the file by calling the [**StorageFile.OpenAsync**](/uwp/api/windows.storage.storagefile.openasync) method.</span></span> <span data-ttu-id="52aa3-131">Wenn der Vorgang zum Öffnen abgeschlossen ist, wird ein Datenstrom des Dateiinhalts zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="52aa3-131">It returns a stream of the file's content when the open operation completes.</span></span>

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

2.  <span data-ttu-id="52aa3-132">Als Nächstes rufen Sie einen Ausgabedatenstrom durch Aufrufen der Methode [**IRandomAccessStream.GetOutputStreamAt**](/uwp/api/windows.storage.streams.irandomaccessstream.getoutputstreamat) aus der `stream`.</span><span class="sxs-lookup"><span data-stu-id="52aa3-132">Next, get an output stream by calling the [**IRandomAccessStream.GetOutputStreamAt**](/uwp/api/windows.storage.streams.irandomaccessstream.getoutputstreamat) method from the `stream`.</span></span> <span data-ttu-id="52aa3-133">Wenn Sie c# verwenden, setzen Sie dies in einer **using** -Anweisung, um den Ausgabestream Lebensdauer zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="52aa3-133">If you're using C#, then enclose this in a **using** statement to manage the output stream's lifetime.</span></span> <span data-ttu-id="52aa3-134">Wenn Sie verwenden [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), können Sie ihrer gesamten Lebensdauer steuern, indem Sie es in einem Block einzuschließen, oder auf `nullptr` Wenn Sie damit fertig sind.</span><span class="sxs-lookup"><span data-stu-id="52aa3-134">If you're using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), then you can control its lifetime by enclosing it in a block, or setting it to `nullptr` when you're done with it.</span></span>

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

3.  <span data-ttu-id="52aa3-135">Jetzt fügen Sie code (Wenn Sie c#, innerhalb der vorhandenen **using** -Anweisung verwenden), um in den Ausgabedatenstrom zu schreiben, indem Sie ein neues [**DataWriter**](/uwp/api/windows.storage.streams.datawriter) -Objekt erstellt und die [**DataWriter.WriteString**](/uwp/api/windows.storage.streams.datawriter.writestring) -Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="52aa3-135">Now add this code (if you're using C#, within the existing **using** statement) to write to the output stream by creating a new [**DataWriter**](/uwp/api/windows.storage.streams.datawriter) object and calling the [**DataWriter.WriteString**](/uwp/api/windows.storage.streams.datawriter.writestring) method.</span></span>

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

4.  <span data-ttu-id="52aa3-136">Abschließend fügen Sie code (Wenn Sie c#, innerhalb der inneren **mithilfe von** -Anweisung verwenden), um den Text in die Datei mit [**DataWriter.StoreAsync**](/uwp/api/windows.storage.streams.datawriter.storeasync) speichern und schließen den Datenstrom mit [**IOutputStream.FlushAsync**](/uwp/api/windows.storage.streams.ioutputstream.flushasync).</span><span class="sxs-lookup"><span data-stu-id="52aa3-136">Lastly, add this code (if you're using C#, within the inner **using** statement) to save the text to your file with [**DataWriter.StoreAsync**](/uwp/api/windows.storage.streams.datawriter.storeasync) and close the stream with [**IOutputStream.FlushAsync**](/uwp/api/windows.storage.streams.ioutputstream.flushasync).</span></span>

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

## <a name="reading-from-a-file"></a><span data-ttu-id="52aa3-137">Lesen aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="52aa3-137">Reading from a file</span></span>

<span data-ttu-id="52aa3-138">Nachfolgend finden Sie Informationen zum Lesen aus einer Datei auf dem Datenträger mithilfe der [**StorageFile**](/uwp/api/Windows.Storage.StorageFile)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="52aa3-138">Here's how to read from a file on disk using the [**StorageFile**](/uwp/api/Windows.Storage.StorageFile) class.</span></span> <span data-ttu-id="52aa3-139">Der allgemein erste Schritt für die einzelnen Methoden zum Lesen von Daten aus einer Datei ist das Abrufen der Datei mit [**StorageFolder.GetFileAsync**](/uwp/api/windows.storage.storagefolder.getfileasync).</span><span class="sxs-lookup"><span data-stu-id="52aa3-139">The common first step for each of the ways of reading from a file is to get the file with [**StorageFolder.GetFileAsync**](/uwp/api/windows.storage.storagefolder.getfileasync).</span></span>

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

**<span data-ttu-id="52aa3-140">Lesen von Text aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="52aa3-140">Reading text from a file</span></span>**

<span data-ttu-id="52aa3-141">Lesen von Text aus einer Datei durch Aufrufen der [**FileIO.ReadTextAsync**](/uwp/api/windows.storage.fileio.readtextasync) -Methode.</span><span class="sxs-lookup"><span data-stu-id="52aa3-141">Read text from your file by calling the [**FileIO.ReadTextAsync**](/uwp/api/windows.storage.fileio.readtextasync) method.</span></span>

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

**<span data-ttu-id="52aa3-142">Lesen von Text aus einer Datei mithilfe eines Puffers (2 Schritte)</span><span class="sxs-lookup"><span data-stu-id="52aa3-142">Reading text from a file by using a buffer (2 steps)</span></span>**

1.  <span data-ttu-id="52aa3-143">Rufen Sie zuerst die Methode [**FileIO.ReadBufferAsync**](/uwp/api/windows.storage.fileio.readbufferasync) .</span><span class="sxs-lookup"><span data-stu-id="52aa3-143">First, call the [**FileIO.ReadBufferAsync**](/uwp/api/windows.storage.fileio.readbufferasync) method.</span></span>

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

2.  <span data-ttu-id="52aa3-144">Verwenden Sie dann ein [**DataReader**](/uwp/api/windows.storage.streams.datareader)-Objekt, um zunächst die Länge des Puffers und dann dessen Inhalt zu lesen.</span><span class="sxs-lookup"><span data-stu-id="52aa3-144">Then use a [**DataReader**](/uwp/api/windows.storage.streams.datareader) object to read first the length of the buffer and then its contents.</span></span>

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

**<span data-ttu-id="52aa3-145">Lesen von Text aus einer Datei mithilfe eines Datenstroms (4 Schritte)</span><span class="sxs-lookup"><span data-stu-id="52aa3-145">Reading text from a file by using a stream (4 steps)</span></span>**

1.  <span data-ttu-id="52aa3-146">Öffnen Sie einen Datenstrom für die Datei, indem Sie die [**StorageFile.OpenAsync**](/uwp/api/windows.storage.storagefile.openasync)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="52aa3-146">Open a stream for your file by calling the [**StorageFile.OpenAsync**](/uwp/api/windows.storage.storagefile.openasync) method.</span></span> <span data-ttu-id="52aa3-147">Wenn der Vorgang abgeschlossen ist, wird ein Datenstrom des Dateiinhalts zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="52aa3-147">It returns a stream of the file's content when the operation completes.</span></span>

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

2.  <span data-ttu-id="52aa3-148">Rufen Sie die Größe des Datenstroms zur späteren Verwendung ab.</span><span class="sxs-lookup"><span data-stu-id="52aa3-148">Get the size of the stream to use later.</span></span>

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

3.  <span data-ttu-id="52aa3-149">Rufen Sie einen Eingabedatenstrom durch Aufrufen der [**IRandomAccessStream.GetInputStreamAt**](/uwp/api/windows.storage.streams.irandomaccessstream.getinputstreamat) -Methode.</span><span class="sxs-lookup"><span data-stu-id="52aa3-149">Get an input stream by calling the [**IRandomAccessStream.GetInputStreamAt**](/uwp/api/windows.storage.streams.irandomaccessstream.getinputstreamat) method.</span></span> <span data-ttu-id="52aa3-150">Fügen Sie ihn in eine **using**-Anweisung ein, um die Lebensdauer des Eingabedatenstroms zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="52aa3-150">Put this in a **using** statement to manage the stream's lifetime.</span></span> <span data-ttu-id="52aa3-151">Geben Sie beim Aufrufen von **GetInputStreamAt** 0 an, um die Position auf den Anfang des Datenstroms festzulegen.</span><span class="sxs-lookup"><span data-stu-id="52aa3-151">Specify 0 when you call **GetInputStreamAt** to set the position to the beginning of the stream.</span></span>

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

4.  <span data-ttu-id="52aa3-152">Abschließend fügen Sie diesen Code in die vorhandene **using**-Anweisung zum Abrufen eines [**DataReader**](/uwp/api/windows.storage.streams.datareader)-Objekts im Datenstrom ein. Lesen Sie dann den Text durch den Aufruf von [**DataReader.LoadAsync**](/uwp/api/windows.storage.streams.datareader.loadasync) und [**DataReader.ReadString**](/uwp/api/windows.storage.streams.datareader.readstring).</span><span class="sxs-lookup"><span data-stu-id="52aa3-152">Lastly, add this code within the existing **using** statement to get a [**DataReader**](/uwp/api/windows.storage.streams.datareader) object on the stream then read the text by calling [**DataReader.LoadAsync**](/uwp/api/windows.storage.streams.datareader.loadasync) and [**DataReader.ReadString**](/uwp/api/windows.storage.streams.datareader.readstring).</span></span>

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
