---
author: laurenhughes
ms.assetid: 4C59D5AC-58F7-4863-A884-E9E54228A5AD
title: Aufzählen und Abfragen von Dateien und Ordnern
description: Greifen Sie auf Dateien und Ordner zu, die sich in einem Ordner, in einer Bibliothek, auf einem Gerät oder an einer Netzwerkadresse befinden. Sie können auch durch Erstellen von Datei- und Ordnerabfragen Dateien und Ordner an bestimmten Speicherorten abrufen.
ms.author: lahugh
ms.date: 06/28/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
- vb
ms.openlocfilehash: 312e351a39bf291e1fcd21921230a73ed10cfd17
ms.sourcegitcommit: 49aab071aa2bd88f1c165438ee7e5c854b3e4f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "4468739"
---
# <a name="enumerate-and-query-files-and-folders"></a><span data-ttu-id="bd9ab-105">Aufzählen und Abfragen von Dateien und Ordnern</span><span class="sxs-lookup"><span data-stu-id="bd9ab-105">Enumerate and query files and folders</span></span>

<span data-ttu-id="bd9ab-106">Greifen Sie auf Dateien und Ordner zu, die sich in einem Ordner, in einer Bibliothek, auf einem Gerät oder an einer Netzwerkadresse befinden.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-106">Access files and folders in either a folder, library, device, or network location.</span></span> <span data-ttu-id="bd9ab-107">Sie können auch durch Erstellen von Datei- und Ordnerabfragen Dateien und Ordner an bestimmten Speicherorten abrufen.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-107">You can also query the files and folders in a location by constructing file and folder queries.</span></span>

<span data-ttu-id="bd9ab-108">Anleitungen zum Speichern der Daten Ihrer App für die Universelle Windows-Plattform finden Sie in der [ApplicationData](/uwp/api/windows.storage.applicationdata)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-108">For guidance on how to store your Universal Windows Platform app's data, see the [ApplicationData](/uwp/api/windows.storage.applicationdata) class.</span></span>

> [!NOTE]
> <span data-ttu-id="bd9ab-109">Siehe auch das [Beispiel für Ordnerenumeration](http://go.microsoft.com/fwlink/p/?linkid=619993).</span><span class="sxs-lookup"><span data-stu-id="bd9ab-109">Also see the [Folder enumeration sample](http://go.microsoft.com/fwlink/p/?linkid=619993).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd9ab-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="bd9ab-110">Prerequisites</span></span>

-   **<span data-ttu-id="bd9ab-111">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="bd9ab-111">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="bd9ab-112">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bd9ab-112">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).</span></span> <span data-ttu-id="bd9ab-113">Informationen zum Schreiben von asynchronen apps in C++ / WinRT, finden Sie unter [Parallelität und asynchrone Vorgänge mit C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency).</span><span class="sxs-lookup"><span data-stu-id="bd9ab-113">To learn how to write asynchronous apps in C++/WinRT, see [Concurrency and asynchronous operations with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency).</span></span> <span data-ttu-id="bd9ab-114">Informationen zum Schreiben von asynchronen apps in C++ / CX finden Sie unter [asynchrone Programmierung in C++ / CX](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span><span class="sxs-lookup"><span data-stu-id="bd9ab-114">To learn how to write asynchronous apps in C++/CX, see [Asynchronous programming in C++/CX](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span></span>

-   **<span data-ttu-id="bd9ab-115">Zugriffsberechtigungen für den Speicherort</span><span class="sxs-lookup"><span data-stu-id="bd9ab-115">Access permissions to the location</span></span>**

    <span data-ttu-id="bd9ab-116">Der Code in diesen Beispielen erfordert beispielsweise den Zugriff auf die **picturesLibrary**-Funktion, während Ihr Speicherort einen anderen Zugriffstyp oder keinen Zugriff voraussetzt.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-116">For example, the code in these examples require the **picturesLibrary** capability, but your location may require a different capability or no capability at all.</span></span> <span data-ttu-id="bd9ab-117">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](file-access-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="bd9ab-117">To learn more, see [File access permissions](file-access-permissions.md).</span></span>

## <a name="enumerate-files-and-folders-in-a-location"></a><span data-ttu-id="bd9ab-118">Auflisten der Dateien und Ordner an einem Speicherort</span><span class="sxs-lookup"><span data-stu-id="bd9ab-118">Enumerate files and folders in a location</span></span>

> [!NOTE]
> <span data-ttu-id="bd9ab-119">Denken Sie daran, die **picturesLibrary**-Funktion zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-119">Remember to declare the **picturesLibrary** capability.</span></span>

<span data-ttu-id="bd9ab-120">In diesem Beispiel verwenden wir zunächst die [**StorageFolder.GetFilesAsync**](/uwp/api/windows.storage.storagefolder.getfilesasync) -Methode, um alle Dateien im Stammordner der [**KnownFolders.PicturesLibrary**](/uwp/api/windows.storage.knownfolders.pictureslibrary) (nicht in den Unterordnern) abzurufen und die Namen der einzelnen Dateien aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-120">In this example we first use the [**StorageFolder.GetFilesAsync**](/uwp/api/windows.storage.storagefolder.getfilesasync) method to get all the files in the root folder of the [**KnownFolders.PicturesLibrary**](/uwp/api/windows.storage.knownfolders.pictureslibrary) (not in subfolders) and list the name of each file.</span></span> <span data-ttu-id="bd9ab-121">Als Nächstes verwenden wir die [**StorageFolder.GetFoldersAsync**](/uwp/api/windows.storage.storagefolder.getfoldersasync) -Methode, um alle Unterordner in der **PicturesLibrary** abrufen und die Namen der einzelnen Unterordner aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-121">Next, we use the [**StorageFolder.GetFoldersAsync**](/uwp/api/windows.storage.storagefolder.getfoldersasync) method to get all the subfolders in the **PicturesLibrary** and list the name of each subfolder.</span></span>

```csharp
StorageFolder picturesFolder = KnownFolders.PicturesLibrary;
StringBuilder outputText = new StringBuilder();

IReadOnlyList<StorageFile> fileList = await picturesFolder.GetFilesAsync();

outputText.AppendLine("Files:");
foreach (StorageFile file in fileList)
{
    outputText.Append(file.Name + "\n");
}

IReadOnlyList<StorageFolder> folderList = await picturesFolder.GetFoldersAsync();
           
outputText.AppendLine("Folders:");
foreach (StorageFolder folder in folderList)
{
    outputText.Append(folder.DisplayName + "\n");
}
```

```cppwinrt
// MainPage.h
// In MainPage.xaml: <TextBlock x:Name="OutputTextBlock"/>
#include <winrt/Windows.Storage.h>
#include <sstream>
...
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    // Be sure to specify the Pictures Folder capability in your Package.appxmanifest.
    Windows::Storage::StorageFolder picturesFolder{
        Windows::Storage::KnownFolders::PicturesLibrary()
    };

    std::wstringstream outputString;
    outputString << L"Files:" << std::endl;

    for (auto const& file : co_await picturesFolder.GetFilesAsync())
    {
        outputString << file.Name().c_str() << std::endl;
    }

    outputString << L"Folders:" << std::endl;
    for (auto const& folder : co_await picturesFolder.GetFoldersAsync())
    {
        outputString << folder.Name().c_str() << std::endl;
    }

    OutputTextBlock().Text(outputString.str().c_str());
}
```

```cpp
#include <ppltasks.h>
#include <string>
#include <memory>

using namespace Windows::Storage;
using namespace Platform::Collections;
using namespace concurrency;
using namespace std;

// Be sure to specify the Pictures Folder capability in the appxmanifext file.
StorageFolder^ picturesFolder = KnownFolders::PicturesLibrary;

// Use a shared_ptr so that the string stays in memory
// until the last task is complete.
auto outputString = make_shared<wstring>();
*outputString += L"Files:\n";

// Get a read-only vector of the file objects
// and pass it to the continuation.
create_task(picturesFolder->GetFilesAsync())        
   // outputString is captured by value, which creates a copy
   // of the shared_ptr and increments its reference count.
   .then ([outputString] (IVectorView\<StorageFile^>^ files)
   {        
       for ( unsigned int i = 0 ; i < files->Size; i++)
       {
           *outputString += files->GetAt(i)->Name->Data();
           *outputString += L"\n";
      }
   })
   // We need to explicitly state the return type
   // here: -IAsyncOperation<...>
   .then([picturesFolder]() -IAsyncOperation\<IVectorView\<StorageFolder^>^>^
   {
       return picturesFolder->GetFoldersAsync();
   })
   // Capture "this" to access m_OutputTextBlock from within the lambda.
   .then([this, outputString](IVectorView/<StorageFolder^>^ folders)
   {        
       *outputString += L"Folders:\n";

       for ( unsigned int i = 0; i < folders->Size; i++)
       {
          *outputString += folders->GetAt(i)->Name->Data();
          *outputString += L"\n";
       }

       // Assume m_OutputTextBlock is a TextBlock defined in the XAML.
       m_OutputTextBlock->Text = ref new String((*outputString).c_str());
    });
```

```vb
Dim picturesFolder As StorageFolder = KnownFolders.PicturesLibrary
Dim outputText As New StringBuilder

Dim fileList As IReadOnlyList(Of StorageFile) =
    Await picturesFolder.GetFilesAsync()

outputText.AppendLine("Files:")
For Each file As StorageFile In fileList

    outputText.Append(file.Name & vbLf)

Next file

Dim folderList As IReadOnlyList(Of StorageFolder) =
    Await picturesFolder.GetFoldersAsync()

outputText.AppendLine("Folders:")
For Each folder As StorageFolder In folderList

    outputText.Append(folder.DisplayName & vbLf)

Next folder
```

> [!NOTE]
> <span data-ttu-id="bd9ab-122">Denken Sie daran, dass in C# oder Visual Basic das **async**-Schlüsselwort in der Deklaration jeder Methode anzugeben ist, in der Sie den **await**-Operator verwenden.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-122">In C# or Visual Basic, remember to put the **async** keyword in the method declaration of any method in which you use the **await** operator.</span></span>

<span data-ttu-id="bd9ab-123">Alternativ können Sie die Methode [**StorageFolder.GetItemsAsync**](/uwp/api/windows.storage.storagefolder.getitemsasync) verwenden, um alle Elemente (Dateien und Unterordner) an einem bestimmten Speicherort abzurufen.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-123">Alternatively, you can use the [**StorageFolder.GetItemsAsync**](/uwp/api/windows.storage.storagefolder.getitemsasync) method to get all items (both files and subfolders) in a particular location.</span></span> <span data-ttu-id="bd9ab-124">Im folgenden Beispiel wird die **GetItemsAsync** -Methode, um alle Dateien und Unterordner im Stammordner der [**KnownFolders.PicturesLibrary**](/uwp/api/windows.storage.knownfolders.pictureslibrary) (nicht in den Unterordnern) abzurufen.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-124">The following example uses the **GetItemsAsync** method to get all files and subfolders in the root folder of the [**KnownFolders.PicturesLibrary**](/uwp/api/windows.storage.knownfolders.pictureslibrary) (not in subfolders).</span></span> <span data-ttu-id="bd9ab-125">Anschließend werden die Namen der einzelnen Dateien und Unterordner aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-125">Then the example lists the name of each file and subfolder.</span></span> <span data-ttu-id="bd9ab-126">Wenn das Element ein Unterordner ist, wird dem Namen die Zeichenfolge `"folder"` angefügt.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-126">If the item is a subfolder, the example appends `"folder"` to the name.</span></span>

```csharp
StorageFolder picturesFolder = KnownFolders.PicturesLibrary;
StringBuilder outputText = new StringBuilder();

IReadOnlyList<IStorageItem> itemsList = await picturesFolder.GetItemsAsync();

foreach (var item in itemsList)
{
    if (item is StorageFolder)
    {
        outputText.Append(item.Name + " folder\n");

    }
    else
    {
        outputText.Append(item.Name + "\n");
    }
}
```

```cppwinrt
// MainPage.h
// In MainPage.xaml: <TextBlock x:Name="OutputTextBlock"/>
#include <winrt/Windows.Storage.h>
#include <sstream>
...
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    // Be sure to specify the Pictures Folder capability in your Package.appxmanifest.
    Windows::Storage::StorageFolder picturesFolder{
        Windows::Storage::KnownFolders::PicturesLibrary()
    };

    std::wstringstream outputString;

    for (Windows::Storage::IStorageItem const& item : co_await picturesFolder.GetItemsAsync())
    {
        outputString << item.Name().c_str();

        if (item.IsOfType(Windows::Storage::StorageItemTypes::Folder))
        {
            outputString << L" folder" << std::endl;
        }
        else
        {
            outputString << std::endl;
        }

        OutputTextBlock().Text(outputString.str().c_str());
    }
}
```

```cpp
// See previous example for comments, namespace and #include info.
StorageFolder^ picturesFolder = KnownFolders::PicturesLibrary;
auto outputString = make_shared<wstring>();

create_task(picturesFolder->GetItemsAsync())        
    .then ([this, outputString] (IVectorView<IStorageItem^>^ items)
{        
    for ( unsigned int i = 0 ; i < items->Size; i++)
    {
        *outputString += items->GetAt(i)->Name->Data();
        if(items->GetAt(i)->IsOfType(StorageItemTypes::Folder))
        {
            *outputString += L"  folder\n";
        }
        else
        {
            *outputString += L"\n";
        }
        m_OutputTextBlock->Text = ref new String((*outputString).c_str());
    }
});
```

```vb
Dim picturesFolder As StorageFolder = KnownFolders.PicturesLibrary
Dim outputText As New StringBuilder

Dim itemsList As IReadOnlyList(Of IStorageItem) =
    Await picturesFolder.GetItemsAsync()

For Each item In itemsList

    If TypeOf item Is StorageFolder Then

        outputText.Append(item.Name & " folder" & vbLf)

    Else

        outputText.Append(item.Name & vbLf)

    End If

Next item
```

## <a name="query-files-in-a-location-and-enumerate-matching-files"></a><span data-ttu-id="bd9ab-127">Abfragen von Dateien an einem Speicherort und Auflisten der entsprechenden Dateien</span><span class="sxs-lookup"><span data-stu-id="bd9ab-127">Query files in a location and enumerate matching files</span></span>

<span data-ttu-id="bd9ab-128">In diesem Beispiel, dass wir für alle Dateien in den [**KnownFolders.PicturesLibrary**](/uwp/api/windows.storage.knownfolders.pictureslibrary) gruppiert nach dem Monat und zu diesem Zeitpunkt Abfragen rekursiv im Beispiel Unterordner bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-128">In this example we query for all the files in the [**KnownFolders.PicturesLibrary**](/uwp/api/windows.storage.knownfolders.pictureslibrary) grouped by the month, and this time the example recurses into subfolders.</span></span> <span data-ttu-id="bd9ab-129">Zunächst wird [**StorageFolder.CreateFolderQuery**](/uwp/api/windows.storage.storagefolder.createfolderquery) aufgerufen und der [**CommonFolderQuery.GroupByMonth**](/uwp/api/windows.storage.search.commonfolderquery)-Wert an die Methode übergeben.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-129">First, we call [**StorageFolder.CreateFolderQuery**](/uwp/api/windows.storage.storagefolder.createfolderquery) and pass the [**CommonFolderQuery.GroupByMonth**](/uwp/api/windows.storage.search.commonfolderquery) value to the method.</span></span> <span data-ttu-id="bd9ab-130">Dadurch erhalten wir ein [**StorageFolderQueryResult**](/uwp/api/windows.storage.search.storagefolderqueryresult)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-130">That gives us a [**StorageFolderQueryResult**](/uwp/api/windows.storage.search.storagefolderqueryresult) object.</span></span>

<span data-ttu-id="bd9ab-131">Als Nächstes wird [**StorageFolderQueryResult.GetFoldersAsync**](/uwp/api/windows.storage.search.storagefolderqueryresult.getfoldersasync) aufgerufen, das [**StorageFolder**](/uwp/api/windows.storage.storagefolder)-Objekte zurückgibt, die virtuelle Ordner darstellen.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-131">Next we call [**StorageFolderQueryResult.GetFoldersAsync**](/uwp/api/windows.storage.search.storagefolderqueryresult.getfoldersasync) which returns [**StorageFolder**](/uwp/api/windows.storage.storagefolder) objects representing virtual folders.</span></span> <span data-ttu-id="bd9ab-132">In diesem Fall wird nach Monat gruppiert, sodass die virtuellen Ordner jeweils eine Gruppe von Dateien mit der gleichen Monatsangabe darstellen.</span><span class="sxs-lookup"><span data-stu-id="bd9ab-132">In this case we're grouping by month, so the virtual folders each represent a group of files with the same month.</span></span>

```csharp
StorageFolder picturesFolder = KnownFolders.PicturesLibrary;

StorageFolderQueryResult queryResult =
    picturesFolder.CreateFolderQuery(CommonFolderQuery.GroupByMonth);
        
IReadOnlyList<StorageFolder> folderList =
    await queryResult.GetFoldersAsync();

StringBuilder outputText = new StringBuilder();

foreach (StorageFolder folder in folderList)
{
    IReadOnlyList<StorageFile> fileList = await folder.GetFilesAsync();

    // Print the month and number of files in this group.
    outputText.AppendLine(folder.Name + " (" + fileList.Count + ")");

    foreach (StorageFile file in fileList)
    {
        // Print the name of the file.
        outputText.AppendLine("   " + file.Name);
    }
}
```

```cppwinrt
// MainPage.h
// In MainPage.xaml: <TextBlock x:Name="OutputTextBlock"/>
#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Search.h>
#include <sstream>
...
Windows::Foundation::IAsyncAction ExampleCoroutineAsync()
{
    // Be sure to specify the Pictures Folder capability in your Package.appxmanifest.
    Windows::Storage::StorageFolder picturesFolder{
        Windows::Storage::KnownFolders::PicturesLibrary()
    };

    Windows::Storage::Search::StorageFolderQueryResult queryResult{
        picturesFolder.CreateFolderQuery(Windows::Storage::Search::CommonFolderQuery::GroupByMonth)
    };

    std::wstringstream outputString;

    for (Windows::Storage::StorageFolder const& folder : co_await queryResult.GetFoldersAsync())
    {
        auto files{ co_await folder.GetFilesAsync() };
        outputString << folder.Name().c_str() << L" (" << files.Size() << L")" << std::endl;

        for (Windows::Storage::StorageFile const& file : files)
        {
            outputString << L"    " << file.Name().c_str() << std::endl;
        }
    }

    OutputTextBlock().Text(outputString.str().c_str());
}
```

```cpp
#include <ppltasks.h>
#include <string>
#include <memory>
using namespace Windows::Storage;
using namespace Windows::Storage::Search;
using namespace concurrency;
using namespace Platform::Collections;
using namespace Windows::Foundation::Collections;
using namespace std;

StorageFolder^ picturesFolder = KnownFolders::PicturesLibrary;

StorageFolderQueryResult^ queryResult =
    picturesFolder->CreateFolderQuery(CommonFolderQuery::GroupByMonth);

// Use shared_ptr so that outputString remains in memory
// until the task completes, which is after the function goes out of scope.
auto outputString = std::make_shared<wstring>();

create_task( queryResult->GetFoldersAsync()).then([this, outputString] (IVectorView<StorageFolder^>^ view)
{        
    for ( unsigned int i = 0; i < view->Size; i++)
    {
        create_task(view->GetAt(i)->GetFilesAsync()).then([this, i, view, outputString](IVectorView<StorageFile^>^ files)
        {
            *outputString += view->GetAt(i)->Name->Data();
            *outputString += L" (";
            *outputString += to_wstring(files->Size);
            *outputString += L")\r\n";
            for (unsigned int j = 0; j < files->Size; j++)
            {
                *outputString += L"     ";
                *outputString += files->GetAt(j)->Name->Data();
                *outputString += L"\r\n";
            }
        }).then([this, outputString]()
        {
            m_OutputTextBlock->Text = ref new String((*outputString).c_str());
        });
    }    
});
```

```vb
Dim picturesFolder As StorageFolder = KnownFolders.PicturesLibrary
Dim outputText As New StringBuilder

Dim queryResult As StorageFolderQueryResult =
    picturesFolder.CreateFolderQuery(CommonFolderQuery.GroupByMonth)

Dim folderList As IReadOnlyList(Of StorageFolder) =
    Await queryResult.GetFoldersAsync()

For Each folder As StorageFolder In folderList

    Dim fileList As IReadOnlyList(Of StorageFile) =
        Await folder.GetFilesAsync()

    ' Print the month and number of files in this group.
    outputText.AppendLine(folder.Name & " (" & fileList.Count & ")")

    For Each file As StorageFile In fileList

        ' Print the name of the file.
        outputText.AppendLine("   " & file.Name)

    Next file

Next folder
```

<span data-ttu-id="bd9ab-133">Die Ausgabe des Beispiels sieht in etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="bd9ab-133">The output of the example looks similar to the following.</span></span>

```syntax
July ‎2015 (2)
   MyImage3.png
   MyImage4.png
‎December ‎2014 (2)
   MyImage1.png
   MyImage2.png
```
