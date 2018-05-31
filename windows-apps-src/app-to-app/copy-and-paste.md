---
description: In diesem Artikel wird erläutert, wie in Apps für die universelle Windows-Plattform (UWP) das Kopieren und Einfügen über die Zwischenablage unterstützt wird.
title: Kopieren und Einfügen
ms.assetid: E882DC15-E12D-4420-B49D-F495BB484BEE
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: ca01be87619dc88cc39b0c2906d9689768c0fa46
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1662570"
---
# <a name="copy-and-paste"></a><span data-ttu-id="5efc3-104">Kopieren und Einfügen</span><span class="sxs-lookup"><span data-stu-id="5efc3-104">Copy and paste</span></span>

<span data-ttu-id="5efc3-105">In diesem Artikel wird erläutert, wie Kopieren und Einfügen mit der Zwischenablage in Apps der universellen Windows-Plattform unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="5efc3-105">This article explains how to support copy and paste in Universal Windows Platform (UWP) apps using the clipboard.</span></span> <span data-ttu-id="5efc3-106">Kopieren und Einfügen ist die klassische Methode zum Austausch von Daten zwischen Apps oder in einer App, und nahezu jede App kann Zwischenablageaktionen bis zu einem gewissen Grad unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5efc3-106">Copy and paste is the classic way to exchange data either between apps, or within an app, and almost every app can support clipboard operations to some degree.</span></span>

## <a name="check-for-built-in-clipboard-support"></a><span data-ttu-id="5efc3-107">Überprüfen der integrierten Unterstützung für die Zwischenablage</span><span class="sxs-lookup"><span data-stu-id="5efc3-107">Check for built-in clipboard support</span></span>

<span data-ttu-id="5efc3-108">In vielen Fällen müssen Sie keinen Code für die Unterstützung von Zwischenablageaktionen schreiben.</span><span class="sxs-lookup"><span data-stu-id="5efc3-108">In many cases, you do not need to write code to support clipboard operations.</span></span> <span data-ttu-id="5efc3-109">Viele der Standard-XAML-Steuerelemente, die Sie beim Erstellen Ihrer Apps verwenden können, unterstützen bereits Zwischenablageaktionen.</span><span class="sxs-lookup"><span data-stu-id="5efc3-109">Many of the default XAML controls you can use to create apps already support clipboard operations.</span></span> 

## <a name="get-set-up"></a><span data-ttu-id="5efc3-110">Vorbereiten</span><span class="sxs-lookup"><span data-stu-id="5efc3-110">Get set up</span></span>

<span data-ttu-id="5efc3-111">Schließen Sie zunächst den [**Windows.ApplicationModel.DataTransfer**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer)-Namespace in Ihre App ein.</span><span class="sxs-lookup"><span data-stu-id="5efc3-111">First, include the [**Windows.ApplicationModel.DataTransfer**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer) namespace in your app.</span></span> <span data-ttu-id="5efc3-112">Fügen Sie dann eine Instanz des [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekts hinzu.</span><span class="sxs-lookup"><span data-stu-id="5efc3-112">Then, add an instance of the [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) object.</span></span> <span data-ttu-id="5efc3-113">Dieses Objekt enthält sowohl die vom Benutzer kopierten Daten als auch alle Eigenschaften (z.B. eine Beschreibung), die Sie einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="5efc3-113">This object contains both the data the user wants to copy and any properties (such as a description) that you want to include.</span></span>

<!-- For some reason, the snippets in this file are all inline in the WDCML topic. Suggest moving to VS project with rest of snippets. -->
```cs
DataPackage dataPackage = new DataPackage();
```

<!-- AuthenticateAsync-->

## <a name="copy-and-cut"></a><span data-ttu-id="5efc3-114">Kopieren und Ausschneiden</span><span class="sxs-lookup"><span data-stu-id="5efc3-114">Copy and cut</span></span>

<span data-ttu-id="5efc3-115">Kopieren und Ausschneiden (auch als *Verschieben* bezeichnet) funktionieren nahezu identisch.</span><span class="sxs-lookup"><span data-stu-id="5efc3-115">Copy and cut (also referred to as *move*) work almost exactly the same.</span></span> <span data-ttu-id="5efc3-116">Wählen Sie mit der [**RequestedOperation**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage.RequestedOperation)-Eigenschaft den gewünschten Vorgang aus.</span><span class="sxs-lookup"><span data-stu-id="5efc3-116">Choose which operation you want by using the [**RequestedOperation**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage.RequestedOperation) property.</span></span>

```cs
// copy 
dataPackage.RequestedOperation = DataPackageOperation.Copy;
// or cut
dataPackage.RequestedOperation = DataPackageOperation.Move;
```
## <a name="drag-and-drop"></a><span data-ttu-id="5efc3-117">Drag & Drop</span><span class="sxs-lookup"><span data-stu-id="5efc3-117">Drag and drop</span></span>

<span data-ttu-id="5efc3-118">Anschließend können Sie die vom Benutzer ausgewählten Daten in das [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekt einfügen.</span><span class="sxs-lookup"><span data-stu-id="5efc3-118">Next, you can add the data that a user has selected to the [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) object.</span></span> <span data-ttu-id="5efc3-119">Wenn die Daten von der **DataPackage**-Klasse unterstützt werden, können Sie die entsprechenden Methoden aus dem **DataPackage**-Objekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="5efc3-119">If this data is supported by the **DataPackage** class, you can use one of the corresponding methods in the **DataPackage** object.</span></span> <span data-ttu-id="5efc3-120">Gehen Sie zum Hinzufügen von Text wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="5efc3-120">Here's how to add text:</span></span>

```cs
dataPackage.SetText("Hello World!");
```

<span data-ttu-id="5efc3-121">Im letzten Schritt wird das [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekt durch Aufrufen der statischen [**SetContent**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.SetContent(Windows.ApplicationModel.DataTransfer.DataPackage))-Methode zur Zwischenablage hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5efc3-121">The last step is to add the [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) to the clipboard by calling the static [**SetContent**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.SetContent(Windows.ApplicationModel.DataTransfer.DataPackage)) method.</span></span>

```cs
Clipboard.SetContent(dataPackage);
```
## <a name="paste"></a><span data-ttu-id="5efc3-122">Einfügen</span><span class="sxs-lookup"><span data-stu-id="5efc3-122">Paste</span></span>

<span data-ttu-id="5efc3-123">Rufen Sie zum Abrufen des Inhalts der Zwischenablage die statische [**GetContent**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.GetContent)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="5efc3-123">To get the contents of the clipboard, call the static [**GetContent**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.GetContent) method.</span></span> <span data-ttu-id="5efc3-124">Die Methode gibt eine [**DataPackageView**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView) mit dem Inhalt zurück.</span><span class="sxs-lookup"><span data-stu-id="5efc3-124">This method returns a [**DataPackageView**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView) that contains the content.</span></span> <span data-ttu-id="5efc3-125">Dieses Objekt ist mit dem [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekt nahezu identisch, der Inhalt ist allerdings schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="5efc3-125">This object is almost identical to a [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) object, except that its contents are read-only.</span></span> <span data-ttu-id="5efc3-126">Anhand dieses Objekts können Sie dann entweder mit der [**AvailableFormats**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView.AvailableFormats)-Methode oder mit der [**Contains**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView.Contains(System.String))-Methode ermitteln, welche Formate verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="5efc3-126">With that object, you can use either the [**AvailableFormats**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView.AvailableFormats) or the [**Contains**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView.Contains(System.String)) method to identify what formats are available.</span></span> <span data-ttu-id="5efc3-127">Rufen Sie anschließend die entsprechende [**DataPackageView**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView)-Methode auf, um die Daten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5efc3-127">Then, you can call the corresponding [**DataPackageView**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView) method to get the data.</span></span>

```cs
async void OutputClipboardText()
{
    DataPackageView dataPackageView = Clipboard.GetContent();
    if (dataPackageView.Contains(StandardDataFormats.Text))
    {
        string text = await dataPackageView.GetTextAsync();
        // To output the text from this example, you need a TextBlock control
        TextOutput.Text = "Clipboard now contains: " + text;
    }
}
```

## <a name="track-changes-to-the-clipboard"></a><span data-ttu-id="5efc3-128">Nachverfolgen von Änderungen an der Zwischenablage</span><span class="sxs-lookup"><span data-stu-id="5efc3-128">Track changes to the clipboard</span></span>

<span data-ttu-id="5efc3-129">Zusätzlich zu den Befehlen zum Kopieren und Einfügen empfiehlt es sich unter Umständen, auch Änderungen an der Zwischenablage nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="5efc3-129">In addition to copy and paste commands, you may also want to track clipboard changes.</span></span> <span data-ttu-id="5efc3-130">Behandeln Sie dafür das [**ContentChanged**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.ContentChanged)-Ereignis der Zwischenablage.</span><span class="sxs-lookup"><span data-stu-id="5efc3-130">Do this by handling the clipboard's [**ContentChanged**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.ContentChanged) event.</span></span>

```cs
Clipboard.ContentChanged += async (s, e) => 
{
    DataPackageView dataPackageView = Clipboard.GetContent();
    if (dataPackageView.Contains(StandardDataFormats.Text))
    {
        string text = await dataPackageView.GetTextAsync();
        // To output the text from this example, you need a TextBlock control
        TextOutput.Text = "Clipboard now contains: " + text;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="5efc3-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5efc3-131">See also</span></span>

* [<span data-ttu-id="5efc3-132">App-zu-App-Kommunikation</span><span class="sxs-lookup"><span data-stu-id="5efc3-132">App-to-app communication</span></span>](index.md)
* [<span data-ttu-id="5efc3-133">DataTransfer</span><span class="sxs-lookup"><span data-stu-id="5efc3-133">DataTransfer</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.aspx)
* [<span data-ttu-id="5efc3-134">DataPackage</span><span class="sxs-lookup"><span data-stu-id="5efc3-134">DataPackage</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackage.aspx)
* [<span data-ttu-id="5efc3-135">DataPackageView</span><span class="sxs-lookup"><span data-stu-id="5efc3-135">DataPackageView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackageview.aspx)
* [<span data-ttu-id="5efc3-136">DataPackagePropertySet</span><span class="sxs-lookup"><span data-stu-id="5efc3-136">DataPackagePropertySet</span></span>]( https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackagepropertyset.aspx)
* [<span data-ttu-id="5efc3-137">DataRequest</span><span class="sxs-lookup"><span data-stu-id="5efc3-137">DataRequest</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datarequest.aspx) 
* [<span data-ttu-id="5efc3-138">DataRequested</span><span class="sxs-lookup"><span data-stu-id="5efc3-138">DataRequested</span></span>]( https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.datarequested.aspx)
* [<span data-ttu-id="5efc3-139">FailWithDisplayText</span><span class="sxs-lookup"><span data-stu-id="5efc3-139">FailWithDisplayText</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datarequest.failwithdisplaytext.aspx)
* [<span data-ttu-id="5efc3-140">ShowShareUi</span><span class="sxs-lookup"><span data-stu-id="5efc3-140">ShowShareUi</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.showshareui.aspx)
* [<span data-ttu-id="5efc3-141">RequestedOperation</span><span class="sxs-lookup"><span data-stu-id="5efc3-141">RequestedOperation</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackage.requestedoperation.aspx) 
* [<span data-ttu-id="5efc3-142">ControlsList</span><span class="sxs-lookup"><span data-stu-id="5efc3-142">ControlsList</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/mt185406.aspx)
* [<span data-ttu-id="5efc3-143">SetContent</span><span class="sxs-lookup"><span data-stu-id="5efc3-143">SetContent</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.datatransfer.clipboard.setcontent.aspx)
* [<span data-ttu-id="5efc3-144">GetContent</span><span class="sxs-lookup"><span data-stu-id="5efc3-144">GetContent</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.datatransfer.clipboard.getcontent.aspx)
* [<span data-ttu-id="5efc3-145">AvailableFormats</span><span class="sxs-lookup"><span data-stu-id="5efc3-145">AvailableFormats</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackageview.availableformats.aspx)
* [<span data-ttu-id="5efc3-146">Contains</span><span class="sxs-lookup"><span data-stu-id="5efc3-146">Contains</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackageview.contains.aspx)
* [<span data-ttu-id="5efc3-147">ContentChanged</span><span class="sxs-lookup"><span data-stu-id="5efc3-147">ContentChanged</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.datatransfer.clipboard.contentchanged.aspx)

