---
ms.assetid: AC96F645-1BDE-4316-85E0-2FBDE0A0A62A
title: Abrufen von Dateieigenschaften
description: Es werden Eigenschaften&\#8212;oberster Ebene, grundlegend und erweitert&\#8212;für eine Datei abgerufen, die durch ein StorageFile-Objekt dargestellt wird.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 0b0747dd3b8992ab456bdb00a4dc7157211eb8ba
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8470493"
---
# <a name="get-file-properties"></a><span data-ttu-id="d053e-104">Abrufen von Dateieigenschaften</span><span class="sxs-lookup"><span data-stu-id="d053e-104">Get file properties</span></span>



**<span data-ttu-id="d053e-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="d053e-105">Important APIs</span></span>**

-   [**<span data-ttu-id="d053e-106">StorageFile.GetBasicPropertiesAsync</span><span class="sxs-lookup"><span data-stu-id="d053e-106">StorageFile.GetBasicPropertiesAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701737)
-   [**<span data-ttu-id="d053e-107">StorageFile.Properties</span><span class="sxs-lookup"><span data-stu-id="d053e-107">StorageFile.Properties</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227225)
-   [**<span data-ttu-id="d053e-108">StorageItemContentProperties.RetrievePropertiesAsync</span><span class="sxs-lookup"><span data-stu-id="d053e-108">StorageItemContentProperties.RetrievePropertiesAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh770652)

<span data-ttu-id="d053e-109">Es werden Eigenschaften – oberste Ebene, grundlegend und erweitert – für eine Datei abgerufen, die durch ein [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekt dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d053e-109">Get properties—top-level, basic, and extended—for a file represented by a [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) object.</span></span>

> [!NOTE]
> <span data-ttu-id="d053e-110">Siehe auch das [Dateizugriff-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619995).</span><span class="sxs-lookup"><span data-stu-id="d053e-110">Also see the [File access sample](http://go.microsoft.com/fwlink/p/?linkid=619995).</span></span>

 


## <a name="prerequisites"></a><span data-ttu-id="d053e-111">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d053e-111">Prerequisites</span></span>

-   **<span data-ttu-id="d053e-112">Verstehen der asynchronen Programmierung für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="d053e-112">Understand async programming for Universal Windows Platform (UWP) apps</span></span>**

    <span data-ttu-id="d053e-113">Informationen zum Schreiben von asynchronen Apps in C# oder Visual Basic finden Sie unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span><span class="sxs-lookup"><span data-stu-id="d053e-113">You can learn how to write asynchronous apps in C# or Visual Basic, see [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/mt187337).</span></span> <span data-ttu-id="d053e-114">Informationen zum Schreiben von asynchronen Apps in C++ finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span><span class="sxs-lookup"><span data-stu-id="d053e-114">To learn how to write asynchronous apps in C++, see [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span></span>

-   **<span data-ttu-id="d053e-115">Zugriffsberechtigungen für den Speicherort</span><span class="sxs-lookup"><span data-stu-id="d053e-115">Access permissions to the location</span></span>**

    <span data-ttu-id="d053e-116">Der Code in diesen Beispielen erfordert beispielsweise den Zugriff auf die **picturesLibrary**-Funktion, während Ihr Speicherort einen anderen Zugriffstyp oder keinen Zugriff voraussetzt.</span><span class="sxs-lookup"><span data-stu-id="d053e-116">For example, the code in these examples require the **picturesLibrary** capability, but your location may require a different capability or no capability at all.</span></span> <span data-ttu-id="d053e-117">Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](file-access-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="d053e-117">To learn more, see [File access permissions](file-access-permissions.md).</span></span>

## <a name="getting-a-files-top-level-properties"></a><span data-ttu-id="d053e-118">Abrufen von Eigenschaften der obersten Ebene einer Datei</span><span class="sxs-lookup"><span data-stu-id="d053e-118">Getting a file's top-level properties</span></span>

<span data-ttu-id="d053e-119">Auf viele Dateieigenschaften der obersten Ebene kann in Form von Membern der [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Klasse zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="d053e-119">Many top-level file properties are accessible as members of the [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) class.</span></span> <span data-ttu-id="d053e-120">Diese Eigenschaften enthalten für eine Datei Attribute, Inhaltstyp, Erstellungsdatum, Anzeigename, Dateityp usw.</span><span class="sxs-lookup"><span data-stu-id="d053e-120">These properties include the files attributes, content type, creation date, display name, file type, and so on.</span></span>

<span data-ttu-id="d053e-121">**Hinweis:** Denken Sie daran, die **PicturesLibrary** -Funktion zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="d053e-121">**Note**Remember to declare the **picturesLibrary** capability.</span></span>

 

<span data-ttu-id="d053e-122">In diesem Beispiel werden alle Dateien der Bildbibliothek aufgezählt, wobei für jede Datei auf einige Eigenschaften der obersten Ebene zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="d053e-122">This example enumerates all of the files in the Pictures library, accessing a few of each file's top-level properties.</span></span>

```csharp
// Enumerate all files in the Pictures library.
var folder = Windows.Storage.KnownFolders.PicturesLibrary;
var query = folder.CreateFileQuery();
var files = await query.GetFilesAsync();

foreach (Windows.Storage.StorageFile file in files)
{
    StringBuilder fileProperties = new StringBuilder();

    // Get top-level file properties.
    fileProperties.AppendLine("File name: " + file.Name);
    fileProperties.AppendLine("File type: " + file.FileType);
}
```

## <a name="getting-a-files-basic-properties"></a><span data-ttu-id="d053e-123">Abrufen von grundlegenden Eigenschaften einer Datei</span><span class="sxs-lookup"><span data-stu-id="d053e-123">Getting a file's basic properties</span></span>

<span data-ttu-id="d053e-124">Viele grundlegende Dateieigenschaften werden abgerufen, indem zuerst die [**StorageFile.GetBasicPropertiesAsync**](https://msdn.microsoft.com/library/windows/apps/hh701737)-Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="d053e-124">Many basic file properties are obtained by first calling the [**StorageFile.GetBasicPropertiesAsync**](https://msdn.microsoft.com/library/windows/apps/hh701737) method.</span></span> <span data-ttu-id="d053e-125">Diese Methode gibt ein [**BasicProperties**](https://msdn.microsoft.com/library/windows/apps/br212113)-Objekt zurück, das Eigenschaften für die Größe des Elements (Datei oder Ordner) und das letzte Änderungsdatum des Elements definiert.</span><span class="sxs-lookup"><span data-stu-id="d053e-125">This method returns a [**BasicProperties**](https://msdn.microsoft.com/library/windows/apps/br212113) object, which defines properties for the size of the item (file or folder) as well as when the item was last modified.</span></span>

<span data-ttu-id="d053e-126">In diesem Beispiel werden alle Dateien der Bildbibliothek aufgezählt, wobei für jede Datei auf einige grundlegende Eigenschaften zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="d053e-126">This example enumerates all of the files in the Pictures library, accessing a few of each file's basic properties.</span></span>

```csharp
// Enumerate all files in the Pictures library.
var folder = Windows.Storage.KnownFolders.PicturesLibrary;
var query = folder.CreateFileQuery();
var files = await query.GetFilesAsync();

foreach (Windows.Storage.StorageFile file in files)
{
    StringBuilder fileProperties = new StringBuilder();

    // Get file's basic properties.
    Windows.Storage.FileProperties.BasicProperties basicProperties =
        await file.GetBasicPropertiesAsync();
    string fileSize = string.Format("{0:n0}", basicProperties.Size);
    fileProperties.AppendLine("File size: " + fileSize + " bytes");
    fileProperties.AppendLine("Date modified: " + basicProperties.DateModified);
}
 ```

## <a name="getting-a-files-extended-properties"></a><span data-ttu-id="d053e-127">Abrufen von erweiterten Eigenschaften einer Datei</span><span class="sxs-lookup"><span data-stu-id="d053e-127">Getting a file's extended properties</span></span>

<span data-ttu-id="d053e-128">Neben den Eigenschaften der obersten Ebene und den grundlegenden Eigenschaften sind dem Inhalt der Datei viele Eigenschaften zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="d053e-128">Aside from the top-level and basic file properties, there are many properties associated with the file's contents.</span></span> <span data-ttu-id="d053e-129">Auf diese erweiterten Eigenschaften wird zugegriffen, indem die [**BasicProperties.RetrievePropertiesAsync**](https://msdn.microsoft.com/library/windows/apps/br212124)-Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="d053e-129">These extended properties are accessed by calling the [**BasicProperties.RetrievePropertiesAsync**](https://msdn.microsoft.com/library/windows/apps/br212124) method.</span></span> <span data-ttu-id="d053e-130">(Ein [**BasicProperties**](https://msdn.microsoft.com/library/windows/apps/br212113)-Objekt wird durch den Aufruf einer [**StorageFile.Properties**](https://msdn.microsoft.com/library/windows/apps/br227225)-Eigenschaft abgerufen.) Während auf Dateieigenschaften der obersten Ebene und grundlegende Dateieigenschaften in Form von Eigenschaften einer Klasse zugegriffen werden kann – [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) und **BasicProperties**, werden erweiterte Eigenschaften abgerufen, indem eine [IEnumerable](http://go.microsoft.com/fwlink/p/?LinkID=313091) -Sammlung von [String](http://go.microsoft.com/fwlink/p/?LinkID=325032)-Objekten mit den Namen der abzurufenden Eigenschaften an die **BasicProperties.RetrievePropertiesAsync**-Methode übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="d053e-130">(A [**BasicProperties**](https://msdn.microsoft.com/library/windows/apps/br212113) object is obtained by calling the [**StorageFile.Properties**](https://msdn.microsoft.com/library/windows/apps/br227225) property.) While top-level and basic file properties are accessible as properties of a class—[**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) and **BasicProperties**, respectively—extended properties are obtained by passing an [IEnumerable](http://go.microsoft.com/fwlink/p/?LinkID=313091) collection of [String](http://go.microsoft.com/fwlink/p/?LinkID=325032) objects representing the names of the properties that are to be retrieved to the **BasicProperties.RetrievePropertiesAsync** method.</span></span> <span data-ttu-id="d053e-131">Diese Methode gibt dann eine [IDictionary](http://go.microsoft.com/fwlink/p/?LinkId=325238) -Sammlung zurück.</span><span class="sxs-lookup"><span data-stu-id="d053e-131">This method then returns an [IDictionary](http://go.microsoft.com/fwlink/p/?LinkId=325238) collection.</span></span> <span data-ttu-id="d053e-132">Anschließend werden die einzelnen erweiterten Eigenschaften anhand des Namens oder Indexes aus der Sammlung abgerufen.</span><span class="sxs-lookup"><span data-stu-id="d053e-132">Each extended property is then retrieved from the collection by name or by index.</span></span>

<span data-ttu-id="d053e-133">In diesem Beispiel werden alle Dateien der Bildbibliothek aufgezählt und die Namen der gewünschten Eigenschaften (**DataAccessed** und **FileOwner**) in einem [List](http://go.microsoft.com/fwlink/p/?LinkID=325246)-Objekt angegeben. Dieses [List](http://go.microsoft.com/fwlink/p/?LinkID=325246)-Objekt wird an [**BasicProperties.RetrievePropertiesAsync**](https://msdn.microsoft.com/library/windows/apps/br212124) übergeben, um die Eigenschaften abzurufen. Diese Eigenschaften werden dann anhand des Namens aus dem zurückgegebenen [IDictionary](http://go.microsoft.com/fwlink/p/?LinkId=325238)-Objekt abgerufen.</span><span class="sxs-lookup"><span data-stu-id="d053e-133">This example enumerates all of the files in the Pictures library, specifies the names of desired properties (**DataAccessed** and **FileOwner**) in a [List](http://go.microsoft.com/fwlink/p/?LinkID=325246) object, passes that [List](http://go.microsoft.com/fwlink/p/?LinkID=325246) object to [**BasicProperties.RetrievePropertiesAsync**](https://msdn.microsoft.com/library/windows/apps/br212124) to retrieve those properties, and then retrieves those properties by name from the returned [IDictionary](http://go.microsoft.com/fwlink/p/?LinkId=325238) object.</span></span>

<span data-ttu-id="d053e-134">Weitere Informationen finden Sie unter der [Windows Core-Eigenschaften](https://msdn.microsoft.com/library/windows/desktop/mt805470) für eine vollständige Liste der erweiterten Eigenschaften einer Datei.</span><span class="sxs-lookup"><span data-stu-id="d053e-134">See the [Windows Core Properties](https://msdn.microsoft.com/library/windows/desktop/mt805470) for a complete list of a file's extended properties.</span></span>

```csharp
const string dateAccessedProperty = "System.DateAccessed";
const string fileOwnerProperty = "System.FileOwner";

// Enumerate all files in the Pictures library.
var folder = KnownFolders.PicturesLibrary;
var query = folder.CreateFileQuery();
var files = await query.GetFilesAsync();

foreach (Windows.Storage.StorageFile file in files)
{
    StringBuilder fileProperties = new StringBuilder();

    // Define property names to be retrieved.
    var propertyNames = new List<string>();
    propertyNames.Add(dateAccessedProperty);
    propertyNames.Add(fileOwnerProperty);

    // Get extended properties.
    IDictionary<string, object> extraProperties =
        await file.Properties.RetrievePropertiesAsync(propertyNames);

    // Get date-accessed property.
    var propValue = extraProperties[dateAccessedProperty];
    if (propValue != null)
    {
        fileProperties.AppendLine("Date accessed: " + propValue);
    }

    // Get file-owner property.
    propValue = extraProperties[fileOwnerProperty];
    if (propValue != null)
    {
        fileProperties.AppendLine("File owner: " + propValue);
    }
}
```

 

 
