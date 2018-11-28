---
ms.assetid: 40122343-1FE3-4160-BABE-6A2DD9AF1E8E
title: Optimieren des Dateizugriffs
description: Erstellen Sie UWP-Apps (Universelle Windows-Plattform), die effizient auf das Dateisystem zugreifen und dadurch Leistungsprobleme aufgrund von Datenträgerlatenz und Arbeitsspeicher-/CPU-Zyklen vermeiden.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: cacd915530bb599936730ec404a6e524fef0105d
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7851859"
---
# <a name="optimize-file-access"></a><span data-ttu-id="b2e8a-104">Optimieren des Dateizugriffs</span><span class="sxs-lookup"><span data-stu-id="b2e8a-104">Optimize file access</span></span>


<span data-ttu-id="b2e8a-105">Erstellen Sie UWP-Apps (Universelle Windows-Plattform), die effizient auf das Dateisystem zugreifen und dadurch Leistungsprobleme aufgrund von Datenträgerlatenz und Arbeitsspeicher-/CPU-Zyklen vermeiden.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-105">Create Universal Windows Platform (UWP) apps that access the file system efficiently, avoiding performance issues due to disk latency and memory/CPU cycles.</span></span>

<span data-ttu-id="b2e8a-106">Wenn Sie auf eine große Sammlung von Dateien und auf andere Eigenschaftenwerte als die typischen Name-, FileType- und Path-Eigenschaften zugreifen möchten, empfiehlt es sich, hierzu [**QueryOptions**](https://msdn.microsoft.com/library/windows/apps/BR207995) zu erstellen und [**SetPropertyPrefetch**](https://msdn.microsoft.com/library/windows/apps/hh973319) aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-106">When you want to access a large collection of files and you want to access property values other than the typical Name, FileType, and Path properties, access them by creating [**QueryOptions**](https://msdn.microsoft.com/library/windows/apps/BR207995) and calling [**SetPropertyPrefetch**](https://msdn.microsoft.com/library/windows/apps/hh973319).</span></span> <span data-ttu-id="b2e8a-107">Mit der **SetPropertyPrefetch**-Methode kann die Leistung von Apps wesentlich gesteigert werden, in denen eine Sammlung von aus dem Dateisystem abgerufenen Elementen angezeigt wird (z. B. eine Sammlung von Bildern).</span><span class="sxs-lookup"><span data-stu-id="b2e8a-107">The **SetPropertyPrefetch** method can dramatically improve the performance of apps that display a collection of items obtained from the file system, such as a collection of images.</span></span> <span data-ttu-id="b2e8a-108">In den nächsten Beispielen werden einige Möglichkeiten veranschaulicht, auf mehrere Dateien zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-108">The next set of examples shows a few ways to access multiple files.</span></span>

<span data-ttu-id="b2e8a-109">Im ersten Beispiel werden mithilfe von [**Windows.Storage.StorageFolder.GetFilesAsync**](https://msdn.microsoft.com/library/windows/apps/BR227273) die Namensinformationen für eine Gruppe von Dateien abgerufen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-109">The first example uses [**Windows.Storage.StorageFolder.GetFilesAsync**](https://msdn.microsoft.com/library/windows/apps/BR227273) to retrieve the name info for a set of files.</span></span> <span data-ttu-id="b2e8a-110">Dieser Ansatz sorgt für eine gute Leistung, da im Beispiel lediglich auf die name-Eigenschaft zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-110">This approach provides good performance, because the example accesses only the name property.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> StorageFolder library = Windows.Storage.KnownFolders.PicturesLibrary;
> IReadOnlyList<StorageFile> files = await library.GetFilesAsync(Windows.Storage.Search.CommonFileQuery.OrderByDate);
> 
> for (int i = 0; i < files.Count; i++)
> {
>     // do something with the name of each file
>     string fileName = files[i].Name;
> }
> ```
> ```vb
> Dim library As StorageFolder = Windows.Storage.KnownFolders.PicturesLibrary
> Dim files As IReadOnlyList(Of StorageFile) =
>     Await library.GetFilesAsync(Windows.Storage.Search.CommonFileQuery.OrderByDate)
> 
> For i As Integer = 0 To files.Count - 1
>     ' do something with the name of each file
>     Dim fileName As String = files(i).Name
> Next i
> ```

<span data-ttu-id="b2e8a-111">Im zweiten Beispiel wird [**Windows.Storage.StorageFolder.GetFilesAsync**](https://msdn.microsoft.com/library/windows/apps/BR227273) verwendet. Anschließend werden die Bildeigenschaften für die einzelnen Dateien abgerufen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-111">The second example uses [**Windows.Storage.StorageFolder.GetFilesAsync**](https://msdn.microsoft.com/library/windows/apps/BR227273) and then retrieves the image properties for each file.</span></span> <span data-ttu-id="b2e8a-112">Bei dieser Vorgehensweise ist eine schlechte Leistung zu beobachten.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-112">This approach provides poor performance.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> StorageFolder library = Windows.Storage.KnownFolders.PicturesLibrary;
> IReadOnlyList<StorageFile> files = await library.GetFilesAsync(Windows.Storage.Search.CommonFileQuery.OrderByDate);
> for (int i = 0; i < files.Count; i++)
> {
>     ImageProperties imgProps = await files[i].Properties.GetImagePropertiesAsync();
> 
>     // do something with the date the image was taken
>     DateTimeOffset date = imgProps.DateTaken;
> }
> ```
> ```vb
> Dim library As StorageFolder = Windows.Storage.KnownFolders.PicturesLibrary
> Dim files As IReadOnlyList(Of StorageFile) = Await library.GetFilesAsync(Windows.Storage.Search.CommonFileQuery.OrderByDate)
> For i As Integer = 0 To files.Count - 1
>     Dim imgProps As ImageProperties =
>         Await files(i).Properties.GetImagePropertiesAsync()
> 
>     ' do something with the date the image was taken
>     Dim dateTaken As DateTimeOffset = imgProps.DateTaken
> Next i
> ```

<span data-ttu-id="b2e8a-113">Im dritten Beispiel werden mit [**QueryOptions**](https://msdn.microsoft.com/library/windows/apps/BR207995) Informationen für eine Gruppe von Dateien abgerufen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-113">The third example uses [**QueryOptions**](https://msdn.microsoft.com/library/windows/apps/BR207995) to get info about a set of files.</span></span> <span data-ttu-id="b2e8a-114">Diese Vorgehensweise bietet eine wesentlich bessere Leistung als das vorhergehende Beispiel.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-114">This approach provides much better performance than the previous example.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> // Set QueryOptions to prefetch our specific properties
> var queryOptions = new Windows.Storage.Search.QueryOptions(CommonFileQuery.OrderByDate, null);
> queryOptions.SetThumbnailPrefetch(ThumbnailMode.PicturesView, 100,
>         ThumbnailOptions.ReturnOnlyIfCached);
> queryOptions.SetPropertyPrefetch(PropertyPrefetchOptions.ImageProperties, 
>        new string[] {"System.Size"});
> 
> StorageFileQueryResult queryResults = KnownFolders.PicturesLibrary.CreateFileQueryWithOptions(queryOptions);
> IReadOnlyList<StorageFile> files = await queryResults.GetFilesAsync();
> 
> foreach (var file in files)
> {
>     ImageProperties imageProperties = await file.Properties.GetImagePropertiesAsync();
> 
>     // Do something with the date the image was taken.
>     DateTimeOffset dateTaken = imageProperties.DateTaken;
> 
>     // Performance gains increase with the number of properties that are accessed.
>     IDictionary<String, object> propertyResults =
>         await file.Properties.RetrievePropertiesAsync(
>               new string[] {"System.Size" });
> 
>     // Get/Set extra properties here
>     var systemSize = propertyResults["System.Size"];
> }
> ```
> ```vb
> ' Set QueryOptions to prefetch our specific properties
> Dim queryOptions = New Windows.Storage.Search.QueryOptions(CommonFileQuery.OrderByDate, Nothing)
> queryOptions.SetThumbnailPrefetch(ThumbnailMode.PicturesView,
>             100, Windows.Storage.FileProperties.ThumbnailOptions.ReturnOnlyIfCached)
> queryOptions.SetPropertyPrefetch(PropertyPrefetchOptions.ImageProperties,
>                                  New String() {"System.Size"})
> 
> Dim queryResults As StorageFileQueryResult = KnownFolders.PicturesLibrary.CreateFileQueryWithOptions(queryOptions)
> Dim files As IReadOnlyList(Of StorageFile) = Await queryResults.GetFilesAsync()
> 
> 
> For Each file In files
>     Dim imageProperties As ImageProperties = Await file.Properties.GetImagePropertiesAsync()
> 
>     ' Do something with the date the image was taken.
>     Dim dateTaken As DateTimeOffset = imageProperties.DateTaken
> 
>     ' Performance gains increase with the number of properties that are accessed.
>     Dim propertyResults As IDictionary(Of String, Object) =
>         Await file.Properties.RetrievePropertiesAsync(New String() {"System.Size"})
> 
>     ' Get/Set extra properties here
>     Dim systemSize = propertyResults("System.Size")
> 
> Next file
> ```
<span data-ttu-id="b2e8a-115">Wenn Sie mehrere Vorgänge an Windows.Storage-Objekten wie `Windows.Storage.ApplicationData.Current.LocalFolder` ausführen, erstellen Sie eine lokale Variable, die auf die Speicherquelle verweist, sodass nicht bei jedem Zugriff erneut Zwischenobjekte erstellt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-115">If you're performing multiple operations on Windows.Storage objects such as `Windows.Storage.ApplicationData.Current.LocalFolder`, create a local variable to reference that storage source so that you don't recreate intermediate objects each time you access it.</span></span>

## <a name="stream-performance-in-c-and-visual-basic"></a><span data-ttu-id="b2e8a-116">Streamleistung in C# und Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2e8a-116">Stream performance in C# and Visual Basic</span></span>

### <a name="buffering-between-uwp-and-net-streams"></a><span data-ttu-id="b2e8a-117">Puffern zwischen UWP- und .NET-Streams</span><span class="sxs-lookup"><span data-stu-id="b2e8a-117">Buffering between UWP and .NET streams</span></span>

<span data-ttu-id="b2e8a-118">Ein UWP-Stream (wie [**Windows.Storage.Streams.IInputStream**](https://msdn.microsoft.com/library/windows/apps/BR241718) oder [**IOutputStream**](https://msdn.microsoft.com/library/windows/apps/BR241728)) kann in zahlreichen Szenarien in .NET-Streams ([**System.IO.Stream**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.stream.aspx)) konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-118">There are many scenarios when you might want to convert a UWP stream (such as a [**Windows.Storage.Streams.IInputStream**](https://msdn.microsoft.com/library/windows/apps/BR241718) or [**IOutputStream**](https://msdn.microsoft.com/library/windows/apps/BR241728)) to a .NET stream ([**System.IO.Stream**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.stream.aspx)).</span></span> <span data-ttu-id="b2e8a-119">Dies ist beispielsweise hilfreich, wenn Sie eine UWP-App (Universelle Windows-Plattform) erstellen und vorhandenen .NET-Code für Streams im UWP-Dateisystem verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-119">For example, this is useful when you are writing a UWP app and want to use existing .NET code that works on streams with the UWP file system.</span></span> <span data-ttu-id="b2e8a-120">Um dies zu ermöglichen, bietet .NET APIs für UWP-apps Erweiterungsmethoden, mit die Sie zwischen .NET- und UWP-Stream konvertieren können.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-120">In order to enable this, .NET APIs for UWP apps provides extension methods that allow you to convert between .NET and UWP stream types.</span></span> <span data-ttu-id="b2e8a-121">Weitere Informationen finden Sie unter [**WindowsRuntimeStreamExtensions**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.aspx).</span><span class="sxs-lookup"><span data-stu-id="b2e8a-121">For more info, see [**WindowsRuntimeStreamExtensions**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.aspx).</span></span>

<span data-ttu-id="b2e8a-122">Beim Konvertieren eines UWP-Streams in einen .NET-Stream wird eigentlich ein Adapter für den zugrundeliegenden UWP-Stream erstellt.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-122">When you convert a UWP stream to a .NET stream, you effectively create an adapter for the underlying UWP stream.</span></span> <span data-ttu-id="b2e8a-123">Das Aufrufen von Methoden für UWP-Streams ist unter bestimmten Umständen mit einem Laufzeitaufwand verbunden.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-123">Under some circumstances, there is a runtime cost associated with invoking methods on UWP streams.</span></span> <span data-ttu-id="b2e8a-124">Dieser kann sich insbesondere in Szenarien mit vielen kleinen und häufig ausgeführten Lese- oder Schreibvorgängen auf die Geschwindigkeit Ihrer App auswirken.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-124">This may affect the speed of your app, especially in scenarios where you perform many small, frequent read or write operations.</span></span>

<span data-ttu-id="b2e8a-125">Damit entsprechende Geschwindigkeitseinbußen nach Möglichkeit vermieden werden, verfügen UWP-Streamadapter über einen Datenpuffer.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-125">In order to speed up apps, the UWP stream adapters contain a data buffer.</span></span> <span data-ttu-id="b2e8a-126">Im folgenden Codebeispiel werden kleine, aufeinander folgende Lesevorgänge unter Verwendung eines UWP-Streamadapters mit Standardpuffergröße veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-126">The following code sample demonstrates small consecutive reads using a UWP stream adapter with a default buffer size.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> StorageFile file = await Windows.Storage.ApplicationData.Current
>     .LocalFolder.GetFileAsync("example.txt");
> Windows.Storage.Streams.IInputStream windowsRuntimeStream = 
>     await file.OpenReadAsync();
> 
> byte[] destinationArray = new byte[8];
> 
> // Create an adapter with the default buffer size.
> using (var managedStream = windowsRuntimeStream.AsStreamForRead())
> {
> 
>     // Read 8 bytes into destinationArray.
>     // A larger block is actually read from the underlying 
>     // windowsRuntimeStream and buffered within the adapter.
>     await managedStream.ReadAsync(destinationArray, 0, 8);
> 
>     // Read 8 more bytes into destinationArray.
>     // This call may complete much faster than the first call
>     // because the data is buffered and no call to the 
>     // underlying windowsRuntimeStream needs to be made.
>     await managedStream.ReadAsync(destinationArray, 0, 8);
> }
> ```
> ```vb
> Dim file As StorageFile = Await Windows.Storage.ApplicationData.Current -
> .LocalFolder.GetFileAsync("example.txt")
> Dim windowsRuntimeStream As Windows.Storage.Streams.IInputStream =
>     Await file.OpenReadAsync()
> 
> Dim destinationArray() As Byte = New Byte(8) {}
> 
> ' Create an adapter with the default buffer size.
> Dim managedStream As Stream = windowsRuntimeStream.AsStreamForRead()
> Using (managedStream)
> 
>     ' Read 8 bytes into destinationArray.
>     ' A larger block is actually read from the underlying 
>     ' windowsRuntimeStream and buffered within the adapter.
>     Await managedStream.ReadAsync(destinationArray, 0, 8)
> 
>     ' Read 8 more bytes into destinationArray.
>     ' This call may complete much faster than the first call
>     ' because the data is buffered and no call to the 
>     ' underlying windowsRuntimeStream needs to be made.
>     Await managedStream.ReadAsync(destinationArray, 0, 8)
> 
> End Using
> ```

<span data-ttu-id="b2e8a-127">Das Verhalten des Standardpuffers eignet sich für die meisten Szenarien, in denen ein UWP-Stream in einen .NET-Stream konvertiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-127">This default buffering behavior is desirable in most scenarios where you convert a UWP stream to a .NET stream.</span></span> <span data-ttu-id="b2e8a-128">In einigen Szenarien kann es jedoch wünschenswert sein, das Pufferverhalten zu optimieren, um die Leistung zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-128">However, in some scenarios you may want to tweak the buffering behavior in order to increase performance.</span></span>

### <a name="working-with-large-data-sets"></a><span data-ttu-id="b2e8a-129">Arbeiten mit umfangreichen Datensätzen</span><span class="sxs-lookup"><span data-stu-id="b2e8a-129">Working with large data sets</span></span>

<span data-ttu-id="b2e8a-130">Beim Lesen oder Schreiben umfangreicher Datensätze können Sie den Durchsatz möglicherweise erhöhen, indem Sie den Puffer für die Erweiterungsmethoden [**AsStreamForRead**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstream.aspx), [**AsStreamForWrite**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx) und [**AsStream**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstream.aspx) vergrößern.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-130">When reading or writing larger sets of data you may be able to increase your read or write throughput by providing a large buffer size to the [**AsStreamForRead**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstream.aspx), [**AsStreamForWrite**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx), and [**AsStream**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstream.aspx) extension methods.</span></span> <span data-ttu-id="b2e8a-131">Dadurch enthält der Streamadapter einen größeren internen Puffer.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-131">This gives the stream adapter a larger internal buffer size.</span></span> <span data-ttu-id="b2e8a-132">So kann der Parser beim Übergeben eines Streams von einer großen Datei an einen XML-Parser eine Vielzahl von kleinen Lesevorgängen für den Stream ausführen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-132">For instance, when passing a stream that comes from a large file to an XML parser, the parser can make many sequential small reads from the stream.</span></span> <span data-ttu-id="b2e8a-133">Große Puffer können dafür sorgen, dass der zugrunde liegende UWP-Stream weniger oft aufgerufen und somit die Leistung gesteigert wird.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-133">A large buffer can reduce the number of calls to the underlying UWP stream and boost performance.</span></span>

> <span data-ttu-id="b2e8a-134">**Hinweis:**  vorsichtig beim Festlegen einer Puffergröße, die größer als ca. 80 KB, Fragmentierungen im Garbage Collector-Heap kann (siehe [verbessern Garbage Collection-Leistung](improve-garbage-collection-performance.md)).</span><span class="sxs-lookup"><span data-stu-id="b2e8a-134">**Note** You should be careful when setting a buffer size that is larger than approximately 80 KB, as this may cause fragmentation on the garbage collector heap (see [Improve garbage collection performance](improve-garbage-collection-performance.md)).</span></span> <span data-ttu-id="b2e8a-135">Im folgenden Codebeispiel wird ein verwalteter Datenstromadapter mit einem Puffer mit 81.920Bytes erstellt.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-135">The following code example creates a managed stream adapter with an 81,920 byte buffer.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
// Create a stream adapter with an 80 KB buffer.
Stream managedStream = nativeStream.AsStreamForRead(bufferSize: 81920);
```
```vb
' Create a stream adapter with an 80 KB buffer.
Dim managedStream As Stream = nativeStream.AsStreamForRead(bufferSize:=81920)
```

<span data-ttu-id="b2e8a-136">Die [**Stream.CopyTo**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.stream.copyto.aspx)- und die [**CopyToAsync**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.stream.copytoasync.aspx)-Methode weisen darüber hinaus einen lokalen Puffer für das Kopieren zwischen Datenströmen zu.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-136">The [**Stream.CopyTo**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.stream.copyto.aspx) and [**CopyToAsync**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.stream.copytoasync.aspx) methods also allocate a local buffer for copying between streams.</span></span> <span data-ttu-id="b2e8a-137">Analog zur [**AsStreamForRead**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstreamforread.aspx)-Erweiterungsmethode kann die Leistung beim Kopieren umfangreicher Streams durch Überschreiben der Standardpuffergröße u. U. verbessert werden.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-137">As with the [**AsStreamForRead**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstreamforread.aspx) extension method, you may be able to get better performance for large stream copies by overriding the default buffer size.</span></span> <span data-ttu-id="b2e8a-138">Im folgenden Codebeispiel wird das Ändern der Standardpuffergröße eines **CopyToAsync**-Aufrufs veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-138">The following code example demonstrates changing the default buffer size of a **CopyToAsync** call.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> MemoryStream destination = new MemoryStream();
> // copies the buffer into memory using the default copy buffer
> await managedStream.CopyToAsync(destination);
> 
> // Copy the buffer into memory using a 1 MB copy buffer.
> await managedStream.CopyToAsync(destination, bufferSize: 1024 * 1024);
> ```
> ```vb
> Dim destination As MemoryStream = New MemoryStream()
> ' copies the buffer into memory using the default copy buffer
> Await managedStream.CopyToAsync(destination)
> 
> ' Copy the buffer into memory using a 1 MB copy buffer.
> Await managedStream.CopyToAsync(destination, bufferSize:=1024 * 1024)
> ```

<span data-ttu-id="b2e8a-139">Die Puffergröße im Beispiel beträgt 1MB. Die empfohlene Puffergröße von 80KB wird somit deutlich übertroffen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-139">This example uses a buffer size of 1 MB, which is greater than the 80 KB previously recommended.</span></span> <span data-ttu-id="b2e8a-140">Durch die Verwendung eines entsprechend großen Puffers kann der Durchsatz des Kopiervorgangs bei umfangreichen Datensätzen (von mehreren Hundert Megabyte) verbessert werden.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-140">Using such a large buffer can improve throughput of the copy operation for very large data sets (that is, several hundred megabytes).</span></span> <span data-ttu-id="b2e8a-141">Da dieser Puffer jedoch für den Heap für große Objekte zugewiesen wird, kann die Leistung der Garbage Collection dadurch beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-141">However, this buffer is allocated on the large object heap and could potentially degrade garbage collection performance.</span></span> <span data-ttu-id="b2e8a-142">Große Puffergrößen sollten daher nur verwendet werden, wenn die Leistung der App dadurch spürbar verbessert werden kann.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-142">You should only use large buffer sizes if it will noticeably improve the performance of your app.</span></span>

<span data-ttu-id="b2e8a-143">Wenn Sie eine große Anzahl von Streams gleichzeitig verwenden, können Sie den Speichermehraufwand des Puffers verringern oder vermeiden.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-143">When you are working with a large number of streams simultaneously, you might want to reduce or eliminate the memory overhead of the buffer.</span></span> <span data-ttu-id="b2e8a-144">Sie können einen kleineren Puffer angeben oder den *bufferSize*-Parameter auf 0 festlegen, um den Puffer für den betreffenden Streamadapter vollständig zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-144">You can specify a smaller buffer, or set the *bufferSize* parameter to 0 to turn off buffering entirely for that stream adapter.</span></span> <span data-ttu-id="b2e8a-145">Auch ohne Puffer können Sie bei Lese- und Schreibvorgängen für den verwalteten Stream jedoch eine gute Durchsatzleistung erreichen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-145">You can still achieve good throughput performance without buffering if you perform large reads and writes to the managed stream.</span></span>

### <a name="performing-latency-sensitive-operations"></a><span data-ttu-id="b2e8a-146">Durchführen von Vorgängen, bei denen Latenz eine Rolle spielt</span><span class="sxs-lookup"><span data-stu-id="b2e8a-146">Performing latency-sensitive operations</span></span>

<span data-ttu-id="b2e8a-147">Das Vermeiden von Pufferungen kann ebenfalls wünschenswert sein, wenn Lese- und Schreibvorgänge mit geringer Latenz ausgeführt werden sollen, ohne große Blöcke aus dem zugrunde liegenden UWP-Stream zu lesen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-147">You might also want to avoid buffering if you want low-latency reads and writes and do not want to read in large blocks out of the underlying UWP stream.</span></span> <span data-ttu-id="b2e8a-148">Beispielsweise eignen sich Lese- und Schreibvorgänge mit geringer Latenz sehr gut für Netzwerkkommunikationsstreams.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-148">For example, you might want low-latency reads and writes if you are using the stream for network communications.</span></span>

<span data-ttu-id="b2e8a-149">In einer Chat-App können Sie Nachrichten mit einem Stream über eine Netzwerkschnittstelle senden und empfangen.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-149">In a chat app you might use a stream over a network interface to send messages back in forth.</span></span> <span data-ttu-id="b2e8a-150">Die Nachrichten sollen dabei unmittelbar nach dem Verfassen und nicht erst dann gesendet werden, wenn der Puffer voll ist.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-150">In this case you want to send messages as soon as they are ready and not wait for the buffer to fill up.</span></span> <span data-ttu-id="b2e8a-151">Wenn Sie die Puffergröße beim Aufrufen der Methoden [**AsStreamForRead**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstreamforread.aspx), [**AsStreamForWrite**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx) und [**AsStream**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstream.aspx) auf 0 festlegen, wird vom resultierenden Adapter kein Puffer zugewiesen. Außerdem wird der zugrunde liegende UWP-Datenstrom von allen Aufrufen direkt bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="b2e8a-151">If you set the buffer size to 0 when calling the [**AsStreamForRead**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstreamforread.aspx), [**AsStreamForWrite**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx), and [**AsStream**](https://msdn.microsoft.com/library/windows/apps/xaml/system.io.windowsruntimestreamextensions.asstream.aspx) extension methods, then the resulting adapter will not allocate a buffer, and all calls will manipulate the underlying UWP stream directly.</span></span>


