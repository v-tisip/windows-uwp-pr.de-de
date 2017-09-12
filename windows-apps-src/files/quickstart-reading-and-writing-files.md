---
author: laurenhughes
ms.assetid: 27914C0A-2A02-473F-BDD5-C931E3943AA0
title: Erstellen, Schreiben und Lesen einer Datei
description: Lesen und Schreiben Sie eine Datei mithilfe eines StorageFile-Objekts.
ms.author: lahugh
ms.date: 07/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: d566bac72b9e3a7e00adb9225342017168ca5f43
ms.sourcegitcommit: 90fbdc0e25e0dff40c571d6687143dd7e16ab8a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2017
---
# <a name="create-write-and-read-a-file"></a><span data-ttu-id="13c28-104">Erstellen, Schreiben und Lesen einer Datei</span><span class="sxs-lookup"><span data-stu-id="13c28-104">Create, write, and read a file</span></span>


<span data-ttu-id="13c28-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="13c28-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="13c28-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="13c28-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


**<span data-ttu-id="13c28-107">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="13c28-107">Important APIs</span></span>**

-   [**<span data-ttu-id="13c28-108">StorageFolder-Klasse</span><span class="sxs-lookup"><span data-stu-id="13c28-108">StorageFolder class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227230)
-   [**<span data-ttu-id="13c28-109">StorageFile-Klasse</span><span class="sxs-lookup"><span data-stu-id="13c28-109">StorageFile class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227171)
-   [**<span data-ttu-id="13c28-110">FileIO-Klasse</span><span class="sxs-lookup"><span data-stu-id="13c28-110">FileIO class</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701440)

<span data-ttu-id="13c28-111">Lesen und Schreiben Sie eine Datei mithilfe eines [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="13c28-111">Read and write a file using a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) object.</span></span>

> [!NOTE] 
> <span data-ttu-id="13c28-112">Siehe auch das [Dateizugriff-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619995).</span><span class="sxs-lookup"><span data-stu-id="13c28-112">Also see the [File access sample](http://go.microsoft.com/fwlink/p/?linkid=619995).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="13c28-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="13c28-113">Prerequisites</span></span>

-   **<span data-ttu-id="13c28-114">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="13c28-114">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="13c28-115">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span><span class="sxs-lookup"><span data-stu-id="13c28-115">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span></span> <span data-ttu-id="13c28-116">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span><span class="sxs-lookup"><span data-stu-id="13c28-116">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span></span>

-   **<span data-ttu-id="13c28-117">Kenntnis, wie die Datei abgerufen wird, aus der Sie lesen und/oder in die Sie schreiben möchten</span><span class="sxs-lookup"><span data-stu-id="13c28-117">Know how to get the file that you want to read from, write to, or both</span></span>**

    <span data-ttu-id="13c28-118">Unter [Öffnen von Dateien und Ordnern mit einer Auswahl](quickstart-using-file-and-folder-pickers.md) erfahren Sie, wie Sie eine Datei mit einer Dateiauswahl abrufen können.</span><span class="sxs-lookup"><span data-stu-id="13c28-118">You can learn how to get a file by using a file picker in [Open files and folders with a picker](quickstart-using-file-and-folder-pickers.md).</span></span>

## <a name="creating-a-file"></a><span data-ttu-id="13c28-119">Erstellen einer Datei</span><span class="sxs-lookup"><span data-stu-id="13c28-119">Creating a file</span></span>

<span data-ttu-id="13c28-120">Nachfolgend finden Sie Informationen zum Erstellen einer Datei im lokalen Ordner der App.</span><span class="sxs-lookup"><span data-stu-id="13c28-120">Here's how to create a file in the app's local folder.</span></span> <span data-ttu-id="13c28-121">Wenn sie bereits vorhanden ist, ersetzen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="13c28-121">If it already exists, we replace it.</span></span>

> [!div class="tabbedCodeSnippets"]
```cs  
// Create sample file; replace if exists.
Windows.Storage.StorageFolder storageFolder =
    Windows.Storage.ApplicationData.Current.LocalFolder;
Windows.Storage.StorageFile sampleFile =
    await storageFolder.CreateFileAsync("sample.txt",
        Windows.Storage.CreationCollisionOption.ReplaceExisting);
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

## <a name="writing-to-a-file"></a><span data-ttu-id="13c28-122">Schreiben in eine Datei</span><span class="sxs-lookup"><span data-stu-id="13c28-122">Writing to a file</span></span>

<span data-ttu-id="13c28-123">Im Folgenden finden Sie Informationen zum Schreiben in eine beschreibbare Datei auf dem Datenträger mithilfe der [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="13c28-123">Here's how to write to a writable file on disk using the [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) class.</span></span> <span data-ttu-id="13c28-124">Der allgemein erste Schritt für die verschiedenen Methoden zum Schreiben in eine Datei ist das Abrufen der Datei mit [**StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272). (Es sei denn, Sie schreiben sofort nach dem Erstellen in die Datei.)</span><span class="sxs-lookup"><span data-stu-id="13c28-124">The common first step for each of the ways of writing to a file (unless you're writing to the file immediately after creating it) is to get the file with [**StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272).</span></span>

> [!div class="tabbedCodeSnippets"]
```cs  
Windows.Storage.StorageFolder storageFolder =
    Windows.Storage.ApplicationData.Current.LocalFolder;
Windows.Storage.StorageFile sampleFile =
    await storageFolder.GetFileAsync("sample.txt");
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

**<span data-ttu-id="13c28-125">Schreiben von Text in eine Datei</span><span class="sxs-lookup"><span data-stu-id="13c28-125">Writing text to a file</span></span>**

<span data-ttu-id="13c28-126">Sie schreiben Text in die Datei, indem Sie die [**WriteTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701505)-Methode der [**FileIO**](https://msdn.microsoft.com/library/windows/apps/hh701440)-Klasse aufrufen.</span><span class="sxs-lookup"><span data-stu-id="13c28-126">Write text to your file by calling the [**WriteTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701505) method of the [**FileIO**](https://msdn.microsoft.com/library/windows/apps/hh701440) class.</span></span>

> [!div class="tabbedCodeSnippets"]
```cs  
await Windows.Storage.FileIO.WriteTextAsync(sampleFile, "Swift as a shadow");
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

**<span data-ttu-id="13c28-127">Schreiben von Bytes in eine Datei mithilfe eines Puffers (2 Schritte)</span><span class="sxs-lookup"><span data-stu-id="13c28-127">Writing bytes to a file by using a buffer (2 steps)</span></span>**

1.  <span data-ttu-id="13c28-128">Rufen Sie zuerst [**ConvertStringToBinary**](https://msdn.microsoft.com/library/windows/apps/br241385) auf, um einen Puffer der Bytes (basierend auf einer beliebigen Zeichenfolge) zu erhalten, die Sie in die Datei schreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="13c28-128">First, call [**ConvertStringToBinary**](https://msdn.microsoft.com/library/windows/apps/br241385) to get a buffer of the bytes (based on an arbitrary string) that you want to write to your file.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    var buffer = Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(
            "What fools these mortals be", Windows.Security.Cryptography.BinaryStringEncoding.Utf8);
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

2.  <span data-ttu-id="13c28-129">Schreiben Sie dann die Bytes aus dem Puffer in die Datei, indem Sie die [**WriteBufferAsync**](https://msdn.microsoft.com/library/windows/apps/hh701490)-Methode der [**FileIO**](https://msdn.microsoft.com/library/windows/apps/hh701440)-Klasse aufrufen.</span><span class="sxs-lookup"><span data-stu-id="13c28-129">Then write the bytes from your buffer to your file by calling the [**WriteBufferAsync**](https://msdn.microsoft.com/library/windows/apps/hh701490) method of the [**FileIO**](https://msdn.microsoft.com/library/windows/apps/hh701440) class.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    await Windows.Storage.FileIO.WriteBufferAsync(sampleFile, buffer);
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

**<span data-ttu-id="13c28-130">Schreiben von Text in eine Datei mithilfe eines Datenstroms (4 Schritte)</span><span class="sxs-lookup"><span data-stu-id="13c28-130">Writing text to a file by using a stream (4 steps)</span></span>**

1.  <span data-ttu-id="13c28-131">Öffnen Sie zunächst die Datei durch Aufrufen der [**StorageFile.OpenAsync**](https://msdn.microsoft.com/library/windows/apps/dn889851)-Methode.</span><span class="sxs-lookup"><span data-stu-id="13c28-131">First, open the file by calling the [**StorageFile.OpenAsync**](https://msdn.microsoft.com/library/windows/apps/dn889851) method.</span></span> <span data-ttu-id="13c28-132">Wenn der Vorgang zum Öffnen abgeschlossen ist, wird ein Datenstrom des Dateiinhalts zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="13c28-132">It returns a stream of the file's content when the open operation completes.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    var stream = await sampleFile.OpenAsync(Windows.Storage.FileAccessMode.ReadWrite);
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

2.  <span data-ttu-id="13c28-133">Rufen Sie dann einen Ausgabedatenstrom ab, indem Sie im `stream` die [**GetOutputStreamAt**](https://msdn.microsoft.com/library/windows/apps/br241738)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="13c28-133">Next, get an output stream by calling the [**GetOutputStreamAt**](https://msdn.microsoft.com/library/windows/apps/br241738) method from the `stream`.</span></span> <span data-ttu-id="13c28-134">Fügen Sie diesen in eine **using**-Anweisung ein, um die Lebensdauer des Ausgabedatenstroms zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="13c28-134">Put this in a **using** statement to manage the output stream's lifetime.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    using (var outputStream = stream.GetOutputStreamAt(0))
    {
        // We'll add more code here in the next step.
    }
    stream.Dispose(); // Or use the stream variable (see previous code snippet) with a using statement as well.
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

3.  <span data-ttu-id="13c28-135">Fügen Sie jetzt diesen Code in die vorhandene **using**-Anweisung ein, um in den Ausgabedatenstrom zu schreiben, indem Sie ein neues [**DataWriter**](https://msdn.microsoft.com/library/windows/apps/br208154)-Objekt erstellen und die [**DataWriter.WriteString**](https://msdn.microsoft.com/library/windows/apps/br241642)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="13c28-135">Now add this code within the existing **using** statement to write to the output stream by creating a new [**DataWriter**](https://msdn.microsoft.com/library/windows/apps/br208154) object and calling the [**DataWriter.WriteString**](https://msdn.microsoft.com/library/windows/apps/br241642) method.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    using (var dataWriter = new Windows.Storage.Streams.DataWriter(outputStream))
    {
        dataWriter.WriteString("DataWriter has methods to write to various types, such as DataTimeOffset.");
    }
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

4.  <span data-ttu-id="13c28-136">Abschließend fügen Sie diesen Code (innerhalb der inneren **using**-Anweisung) mit [**StoreAsync**](https://msdn.microsoft.com/library/windows/apps/br208171) hinzu, um den Text in der Datei zu speichern, und schließen Sie den Datenstrom mit [**FlushAsync**](https://msdn.microsoft.com/library/windows/apps/br241729).</span><span class="sxs-lookup"><span data-stu-id="13c28-136">Lastly, add this code (within the inner **using** statement) to save the text to your file with [**StoreAsync**](https://msdn.microsoft.com/library/windows/apps/br208171) and close the stream with [**FlushAsync**](https://msdn.microsoft.com/library/windows/apps/br241729).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    await dataWriter.StoreAsync();
        await outputStream.FlushAsync();
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

## <a name="reading-from-a-file"></a><span data-ttu-id="13c28-137">Lesen aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="13c28-137">Reading from a file</span></span>

<span data-ttu-id="13c28-138">Nachfolgend finden Sie Informationen zum Lesen aus einer Datei auf dem Datenträger mithilfe der [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="13c28-138">Here's how to read from a file on disk using the [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) class.</span></span> <span data-ttu-id="13c28-139">Der allgemein erste Schritt für die einzelnen Methoden zum Lesen von Daten aus einer Datei ist das Abrufen der Datei mit [**StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272).</span><span class="sxs-lookup"><span data-stu-id="13c28-139">The common first step for each of the ways of reading from a file is to get the file with [**StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272).</span></span>

> [!div class="tabbedCodeSnippets"]
```cs  
Windows.Storage.StorageFolder storageFolder =
    Windows.Storage.ApplicationData.Current.LocalFolder;
Windows.Storage.StorageFile sampleFile =
    await storageFolder.GetFileAsync("sample.txt");
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

**<span data-ttu-id="13c28-140">Lesen von Text aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="13c28-140">Reading text from a file</span></span>**

<span data-ttu-id="13c28-141">Lesen Sie Text aus einer Datei, indem Sie die [**ReadTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701482)-Methode der [**FileIO**](https://msdn.microsoft.com/library/windows/apps/hh701440)-Klasse aufrufen.</span><span class="sxs-lookup"><span data-stu-id="13c28-141">Read text from your file by calling the [**ReadTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701482) method of the [**FileIO**](https://msdn.microsoft.com/library/windows/apps/hh701440) class.</span></span>

> [!div class="tabbedCodeSnippets"]
```cs  
string text = await Windows.Storage.FileIO.ReadTextAsync(sampleFile);
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

**<span data-ttu-id="13c28-142">Lesen von Text aus einer Datei mithilfe eines Puffers (2 Schritte)</span><span class="sxs-lookup"><span data-stu-id="13c28-142">Reading text from a file by using a buffer (2 steps)</span></span>**

1.  <span data-ttu-id="13c28-143">Rufen Sie zuerst die [**ReadBufferAsync**](https://msdn.microsoft.com/library/windows/apps/hh701468)-Methode der [**FileIO**](https://msdn.microsoft.com/library/windows/apps/hh701440)-Klasse auf.</span><span class="sxs-lookup"><span data-stu-id="13c28-143">First, call the [**ReadBufferAsync**](https://msdn.microsoft.com/library/windows/apps/hh701468) method of the [**FileIO**](https://msdn.microsoft.com/library/windows/apps/hh701440) class.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    var buffer = await Windows.Storage.FileIO.ReadBufferAsync(sampleFile);
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

2.  <span data-ttu-id="13c28-144">Verwenden Sie dann ein [**DataReader**](https://msdn.microsoft.com/library/windows/apps/br208119)-Objekt, um zunächst die Länge des Puffers und dann dessen Inhalt zu lesen.</span><span class="sxs-lookup"><span data-stu-id="13c28-144">Then use a [**DataReader**](https://msdn.microsoft.com/library/windows/apps/br208119) object to read first the length of the buffer and then its contents.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    using (var dataReader = Windows.Storage.Streams.DataReader.FromBuffer(buffer))
    {
        string text = dataReader.ReadString(buffer.Length);
    }
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

**<span data-ttu-id="13c28-145">Lesen von Text aus einer Datei mithilfe eines Datenstroms (4 Schritte)</span><span class="sxs-lookup"><span data-stu-id="13c28-145">Reading text from a file by using a stream (4 steps)</span></span>**

1.  <span data-ttu-id="13c28-146">Öffnen Sie einen Datenstrom für die Datei, indem Sie die [**StorageFile.OpenAsync**](https://msdn.microsoft.com/library/windows/apps/dn889851)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="13c28-146">Open a stream for your file by calling the [**StorageFile.OpenAsync**](https://msdn.microsoft.com/library/windows/apps/dn889851) method.</span></span> <span data-ttu-id="13c28-147">Wenn der Vorgang abgeschlossen ist, wird ein Datenstrom des Dateiinhalts zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="13c28-147">It returns a stream of the file's content when the operation completes.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    var stream = await sampleFile.OpenAsync(Windows.Storage.FileAccessMode.Read);
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

2.  <span data-ttu-id="13c28-148">Rufen Sie die Größe des Datenstroms zur späteren Verwendung ab.</span><span class="sxs-lookup"><span data-stu-id="13c28-148">Get the size of the stream to use later.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    ulong size = stream.Size;
    ```
    ```cpp  
    // Add to "Process stream" from part 1
    UINT64 size = stream->Size;
    ```
    ```vb  
    Dim size = stream.Size
    ```

3.  <span data-ttu-id="13c28-149">Rufen Sie einen Eingabedatenstrom ab, indem Sie die [**GetInputStreamAt**](https://msdn.microsoft.com/library/windows/apps/br241737)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="13c28-149">Get an input stream by calling the [**GetInputStreamAt**](https://msdn.microsoft.com/library/windows/apps/br241737) method.</span></span> <span data-ttu-id="13c28-150">Fügen Sie ihn in eine **using**-Anweisung ein, um die Lebensdauer des Eingabedatenstroms zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="13c28-150">Put this in a **using** statement to manage the stream's lifetime.</span></span> <span data-ttu-id="13c28-151">Geben Sie beim Aufrufen von **GetInputStreamAt** 0 an, um die Position auf den Anfang des Datenstroms festzulegen.</span><span class="sxs-lookup"><span data-stu-id="13c28-151">Specify 0 when you call **GetInputStreamAt** to set the position to the beginning of the stream.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    using (var inputStream = stream.GetInputStreamAt(0))
    {
        // We'll add more code here in the next step.
    }
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

4.  <span data-ttu-id="13c28-152">Abschließend fügen Sie diesen Code in die vorhandene **using**-Anweisung zum Abrufen eines [**DataReader**](https://msdn.microsoft.com/library/windows/apps/br208119)-Objekts im Datenstrom ein. Lesen Sie dann den Text durch den Aufruf von [**DataReader.LoadAsync**](https://msdn.microsoft.com/library/windows/apps/br208135) und [**DataReader.ReadString**](https://msdn.microsoft.com/library/windows/apps/br208147).</span><span class="sxs-lookup"><span data-stu-id="13c28-152">Lastly, add this code within the existing **using** statement to get a [**DataReader**](https://msdn.microsoft.com/library/windows/apps/br208119) object on the stream then read the text by calling [**DataReader.LoadAsync**](https://msdn.microsoft.com/library/windows/apps/br208135) and [**DataReader.ReadString**](https://msdn.microsoft.com/library/windows/apps/br208147).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ```cs  
    using (var dataReader = new Windows.Storage.Streams.DataReader(inputStream))
    {
        uint numBytesLoaded = await dataReader.LoadAsync((uint)size);
        string text = dataReader.ReadString(numBytesLoaded);
    }
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

 

 
