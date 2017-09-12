---
description: "In diesem Artikel wird erläutert, wie in Apps für die universelle Windows-Plattform (UWP) das Kopieren und Einfügen über die Zwischenablage unterstützt wird."
title: "Kopieren und Einfügen"
ms.assetid: E882DC15-E12D-4420-B49D-F495BB484BEE
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: f49a417e87199a625a023f7aa867f855cbd5d3c9
ms.sourcegitcommit: 23cda44f10059bcaef38ae73fd1d7c8b8330c95e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2017
---
#<a name="copy-and-paste"></a><span data-ttu-id="8fef2-104">Kopieren und Einfügen</span><span class="sxs-lookup"><span data-stu-id="8fef2-104">Copy and paste</span></span>

<span data-ttu-id="8fef2-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="8fef2-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="8fef2-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="8fef2-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="8fef2-107">In diesem Artikel wird erläutert, wie das Kopieren und Einfügen mit der Zwischenablage in Apps der universellen Windows-Plattform unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="8fef2-107">This article explains how to support copy and paste in Universal Windows Platform (UWP) apps using the clipboard.</span></span> <span data-ttu-id="8fef2-108">Kopieren und Einfügen ist die klassische Methode zum Austausch von Daten zwischen Apps oder in einer App, und nahezu jede App kann Zwischenablageaktionen bis zu einem gewissen Grad unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8fef2-108">Copy and paste is the classic way to exchange data either between apps, or within an app, and almost every app can support clipboard operations to some degree.</span></span>

## <a name="check-for-built-in-clipboard-support"></a><span data-ttu-id="8fef2-109">Überprüfen der integrierten Unterstützung für die Zwischenablage</span><span class="sxs-lookup"><span data-stu-id="8fef2-109">Check for built-in clipboard support</span></span>

<span data-ttu-id="8fef2-110">In vielen Fällen müssen Sie keinen Code für die Unterstützung von Zwischenablageaktionen schreiben.</span><span class="sxs-lookup"><span data-stu-id="8fef2-110">In many cases, you do not need to write code to support clipboard operations.</span></span> <span data-ttu-id="8fef2-111">Viele der Standard-XAML-Steuerelemente, die Sie beim Erstellen Ihrer Apps verwenden können, unterstützen bereits Zwischenablageaktionen.</span><span class="sxs-lookup"><span data-stu-id="8fef2-111">Many of the default XAML controls you can use to create apps already support clipboard operations.</span></span> 

## <a name="get-set-up"></a><span data-ttu-id="8fef2-112">Vorbereiten</span><span class="sxs-lookup"><span data-stu-id="8fef2-112">Get set up</span></span>

<span data-ttu-id="8fef2-113">Schließen Sie zunächst den [**Windows.ApplicationModel.DataTransfer**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer)-Namespace in Ihre App ein.</span><span class="sxs-lookup"><span data-stu-id="8fef2-113">First, include the [**Windows.ApplicationModel.DataTransfer**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer) namespace in your app.</span></span> <span data-ttu-id="8fef2-114">Fügen Sie dann eine Instanz des [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekts hinzu.</span><span class="sxs-lookup"><span data-stu-id="8fef2-114">Then, add an instance of the [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) object.</span></span> <span data-ttu-id="8fef2-115">Dieses Objekt enthält sowohl die vom Benutzer kopierten Daten als auch alle Eigenschaften (z.B. eine Beschreibung), die Sie einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="8fef2-115">This object contains both the data the user wants to copy and any properties (such as a description) that you want to include.</span></span>

<!-- For some reason, the snippets in this file are all inline in the WDCML topic. Suggest moving to VS project with rest of snippets. -->
```cs
DataPackage dataPackage = new DataPackage();
```

<!-- AuthenticateAsync-->

## <a name="copy-and-cut"></a><span data-ttu-id="8fef2-116">Kopieren und Ausschneiden</span><span class="sxs-lookup"><span data-stu-id="8fef2-116">Copy and cut</span></span>

<span data-ttu-id="8fef2-117">Kopieren und Ausschneiden (auch als *Verschieben* bezeichnet) funktionieren nahezu identisch.</span><span class="sxs-lookup"><span data-stu-id="8fef2-117">Copy and cut (also referred to as *move*) work almost exactly the same.</span></span> <span data-ttu-id="8fef2-118">Wählen Sie mit der [**RequestedOperation**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage.RequestedOperation)-Eigenschaft den gewünschten Vorgang aus.</span><span class="sxs-lookup"><span data-stu-id="8fef2-118">Choose which operation you want by using the [**RequestedOperation**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage.RequestedOperation) property.</span></span>

```cs
// copy 
dataPackage.RequestedOperation = DataPackageOperation.Copy;
// or cut
dataPackage.RequestedOperation = DataPackageOperation.Move;
```
## <a name="drag-and-drop"></a><span data-ttu-id="8fef2-119">Drag & Drop</span><span class="sxs-lookup"><span data-stu-id="8fef2-119">Drag and drop</span></span>

<span data-ttu-id="8fef2-120">Anschließend können Sie die vom Benutzer ausgewählten Daten in das [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekt einfügen.</span><span class="sxs-lookup"><span data-stu-id="8fef2-120">Next, you can add the data that a user has selected to the [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) object.</span></span> <span data-ttu-id="8fef2-121">Wenn die Daten von der **DataPackage**-Klasse unterstützt werden, können Sie die entsprechenden Methoden aus dem **DataPackage**-Objekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="8fef2-121">If this data is supported by the **DataPackage** class, you can use one of the corresponding methods in the **DataPackage** object.</span></span> <span data-ttu-id="8fef2-122">Gehen Sie zum Hinzufügen von Text wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="8fef2-122">Here's how to add text:</span></span>

```cs
dataPackage.SetText("Hello World!");
```

<span data-ttu-id="8fef2-123">Im letzten Schritt wird das [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekt durch Aufrufen der statischen [**SetContent**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.SetContent(Windows.ApplicationModel.DataTransfer.DataPackage))-Methode zur Zwischenablage hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8fef2-123">The last step is to add the [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) to the clipboard by calling the static [**SetContent**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.SetContent(Windows.ApplicationModel.DataTransfer.DataPackage)) method.</span></span>

```cs
Clipboard.SetContent(dataPackage);
```
## <a name="paste"></a><span data-ttu-id="8fef2-124">Einfügen</span><span class="sxs-lookup"><span data-stu-id="8fef2-124">Paste</span></span>

<span data-ttu-id="8fef2-125">Rufen Sie zum Abrufen des Inhalts der Zwischenablage die statische [**GetContent**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.GetContent)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="8fef2-125">To get the contents of the clipboard, call the static [**GetContent**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.GetContent) method.</span></span> <span data-ttu-id="8fef2-126">Die Methode gibt eine [**DataPackageView**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView) mit dem Inhalt zurück.</span><span class="sxs-lookup"><span data-stu-id="8fef2-126">This method returns a [**DataPackageView**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView) that contains the content.</span></span> <span data-ttu-id="8fef2-127">Dieses Objekt ist mit dem [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekt nahezu identisch, der Inhalt ist allerdings schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="8fef2-127">This object is almost identical to a [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) object, except that its contents are read-only.</span></span> <span data-ttu-id="8fef2-128">Anhand dieses Objekts können Sie dann entweder mit der [**AvailableFormats**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView.AvailableFormats)-Methode oder mit der [**Contains**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView.Contains(System.String))-Methode ermitteln, welche Formate verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8fef2-128">With that object, you can use either the [**AvailableFormats**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView.AvailableFormats) or the [**Contains**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView.Contains(System.String)) method to identify what formats are available.</span></span> <span data-ttu-id="8fef2-129">Rufen Sie anschließend die entsprechende [**DataPackageView**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView)-Methode auf, um die Daten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8fef2-129">Then, you can call the corresponding [**DataPackageView**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackageView) method to get the data.</span></span>

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

## <a name="track-changes-to-the-clipboard"></a><span data-ttu-id="8fef2-130">Nachverfolgen von Änderungen an der Zwischenablage</span><span class="sxs-lookup"><span data-stu-id="8fef2-130">Track changes to the clipboard</span></span>

<span data-ttu-id="8fef2-131">Zusätzlich zu den Befehlen zum Kopieren und Einfügen empfiehlt es sich unter Umständen, auch Änderungen an der Zwischenablage nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="8fef2-131">In addition to copy and paste commands, you may also want to track clipboard changes.</span></span> <span data-ttu-id="8fef2-132">Behandeln Sie dafür das [**ContentChanged**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.ContentChanged)-Ereignis der Zwischenablage.</span><span class="sxs-lookup"><span data-stu-id="8fef2-132">Do this by handling the clipboard's [**ContentChanged**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.Clipboard.ContentChanged) event.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8fef2-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8fef2-133">See also</span></span>

* [<span data-ttu-id="8fef2-134">App-zu-App-Kommunikation</span><span class="sxs-lookup"><span data-stu-id="8fef2-134">App-to-app communication</span></span>](index.md)
* [<span data-ttu-id="8fef2-135">DataTransfer</span><span class="sxs-lookup"><span data-stu-id="8fef2-135">DataTransfer</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.aspx)
* [<span data-ttu-id="8fef2-136">DataPackage</span><span class="sxs-lookup"><span data-stu-id="8fef2-136">DataPackage</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackage.aspx)
* [<span data-ttu-id="8fef2-137">DataPackageView</span><span class="sxs-lookup"><span data-stu-id="8fef2-137">DataPackageView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackageview.aspx)
* [<span data-ttu-id="8fef2-138">DataPackagePropertySet</span><span class="sxs-lookup"><span data-stu-id="8fef2-138">DataPackagePropertySet</span></span>]( https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackagepropertyset.aspx)
* [<span data-ttu-id="8fef2-139">DataRequest</span><span class="sxs-lookup"><span data-stu-id="8fef2-139">DataRequest</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datarequest.aspx) 
* [<span data-ttu-id="8fef2-140">DataRequested</span><span class="sxs-lookup"><span data-stu-id="8fef2-140">DataRequested</span></span>]( https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.datarequested.aspx)
* [<span data-ttu-id="8fef2-141">FailWithDisplayText</span><span class="sxs-lookup"><span data-stu-id="8fef2-141">FailWithDisplayText</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datarequest.failwithdisplaytext.aspx)
* [<span data-ttu-id="8fef2-142">ShowShareUi</span><span class="sxs-lookup"><span data-stu-id="8fef2-142">ShowShareUi</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.showshareui.aspx)
* [<span data-ttu-id="8fef2-143">RequestedOperation</span><span class="sxs-lookup"><span data-stu-id="8fef2-143">RequestedOperation</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackage.requestedoperation.aspx) 
* [<span data-ttu-id="8fef2-144">ControlsList</span><span class="sxs-lookup"><span data-stu-id="8fef2-144">ControlsList</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/mt185406.aspx)
* [<span data-ttu-id="8fef2-145">SetContent</span><span class="sxs-lookup"><span data-stu-id="8fef2-145">SetContent</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.datatransfer.clipboard.setcontent.aspx)
* [<span data-ttu-id="8fef2-146">GetContent</span><span class="sxs-lookup"><span data-stu-id="8fef2-146">GetContent</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.datatransfer.clipboard.getcontent.aspx)
* [<span data-ttu-id="8fef2-147">AvailableFormats</span><span class="sxs-lookup"><span data-stu-id="8fef2-147">AvailableFormats</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackageview.availableformats.aspx)
* [<span data-ttu-id="8fef2-148">Contains</span><span class="sxs-lookup"><span data-stu-id="8fef2-148">Contains</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackageview.contains.aspx)
* [<span data-ttu-id="8fef2-149">ContentChanged</span><span class="sxs-lookup"><span data-stu-id="8fef2-149">ContentChanged</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.datatransfer.clipboard.contentchanged.aspx)

