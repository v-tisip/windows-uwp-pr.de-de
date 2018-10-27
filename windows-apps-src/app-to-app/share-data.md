---
description: In diesem Artikel wird erläutert, wie der Freigabe-Vertrag in einer UWP-App (Universelle Windows-Plattform) unterstützt wird.
title: Freigeben von Daten
ms.assetid: 32287F5E-EB86-4B98-97FF-8F6228D06782
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 63e07e56acc8767e4acbad3688c13d75527e9c6f
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5682788"
---
# <a name="share-data"></a><span data-ttu-id="e1cf8-104">Freigeben von Daten</span><span class="sxs-lookup"><span data-stu-id="e1cf8-104">Share data</span></span>


<span data-ttu-id="e1cf8-105">In diesem Artikel wird erläutert, wie der Freigabe-Vertrag in einer UWP-App (Universelle Windows-Plattform) unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-105">This article explains how to support the Share contract in a Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="e1cf8-106">Der Freigabe-Vertrag ist eine einfache Möglichkeit, Daten wie z.B. Text, Links, Fotos und Videos schnell für andere Apps freizugeben.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-106">The Share contract is an easy way to quickly share data, such as text, links, photos, and videos, between apps.</span></span> <span data-ttu-id="e1cf8-107">Ein Benutzer möchte beispielsweise mit einer App für ein soziales Netzwerk eine Webseite mit seinen Freunden teilen, oder er möchte in einer Notiz-App einen Link für später speichern.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-107">For example, a user might want to share a webpage with their friends using a social networking app, or save a link in a notes app to refer to later.</span></span>

## <a name="set-up-an-event-handler"></a><span data-ttu-id="e1cf8-108">Einrichten eines Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="e1cf8-108">Set up an event handler</span></span>

<span data-ttu-id="e1cf8-109">Fügen Sie einen [**DataRequested**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.DataRequested)-Ereignishandler hinzu, der aufgerufen werden soll, wenn der Benutzer das Teilen-Feature verwendet.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-109">Add a [**DataRequested**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.DataRequested) event handler to be called whenever a user invokes share.</span></span> <span data-ttu-id="e1cf8-110">Dies kann durch Tippen auf ein Steuerelement in Ihrer App (etwa eine Schaltfläche oder ein App-Leistenbefehl) oder automatisch in einem bestimmten Szenario geschehen (etwa wenn der Benutzer einen Level mit einer hohen Punktzahl abschließt).</span><span class="sxs-lookup"><span data-stu-id="e1cf8-110">This can occur either when the user taps a control in your app (such as a button or app bar command) or automatically in a specific scenario (if the user finishes a level and gets a high score, for example).</span></span>

[!code-cs[Main](./code/share_data/cs/MainPage.xaml.cs#SnippetPrepareToShare)]

<span data-ttu-id="e1cf8-111">Wenn ein [**DataRequested**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.DataRequested)-Ereignis eintritt, empfängt Ihre App ein [**DataRequest**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataRequest)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-111">When a [**DataRequested**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.DataRequested) event occurs, your app receives a [**DataRequest**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataRequest) object.</span></span> <span data-ttu-id="e1cf8-112">Dieses enthält ein [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage), mit dem Sie den Inhalt bereitstellen können, den der Benutzer freigeben möchte.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-112">This contains a [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) that you can use to provide the content that the user wants to share.</span></span> <span data-ttu-id="e1cf8-113">Sie müssen einen Titel und die freizugebenden Daten angeben.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-113">You must provide a title and data to share.</span></span> <span data-ttu-id="e1cf8-114">Eine Beschreibung ist optional, wird aber empfohlen.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-114">A description is optional, but recommended.</span></span>

[!code-cs[Main](./code/share_data/cs/MainPage.xaml.cs#SnippetCreateRequest)]

## <a name="choose-data"></a><span data-ttu-id="e1cf8-115">Wählen von Daten</span><span class="sxs-lookup"><span data-stu-id="e1cf8-115">Choose data</span></span>

<span data-ttu-id="e1cf8-116">Sie können verschiedene Arten von Daten freigeben, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="e1cf8-116">You can share various types of data, including:</span></span>

-   <span data-ttu-id="e1cf8-117">Nur-Text</span><span class="sxs-lookup"><span data-stu-id="e1cf8-117">Plain text</span></span>
-   <span data-ttu-id="e1cf8-118">URIs (Uniform Resource Identifiers)</span><span class="sxs-lookup"><span data-stu-id="e1cf8-118">Uniform Resource Identifiers (URIs)</span></span>
-   <span data-ttu-id="e1cf8-119">HTML</span><span class="sxs-lookup"><span data-stu-id="e1cf8-119">HTML</span></span>
-   <span data-ttu-id="e1cf8-120">Formatierter Text</span><span class="sxs-lookup"><span data-stu-id="e1cf8-120">Formatted text</span></span>
-   <span data-ttu-id="e1cf8-121">Bitmaps</span><span class="sxs-lookup"><span data-stu-id="e1cf8-121">Bitmaps</span></span>
-   <span data-ttu-id="e1cf8-122">Dateien</span><span class="sxs-lookup"><span data-stu-id="e1cf8-122">Files</span></span>
-   <span data-ttu-id="e1cf8-123">Vom Entwickler definierte Daten</span><span class="sxs-lookup"><span data-stu-id="e1cf8-123">Custom developer-defined data</span></span>

<span data-ttu-id="e1cf8-124">Das [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekt kann mehrere dieser Formate in beliebiger Kombination enthalten.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-124">The [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) object can contain one or more of these formats, in any combination.</span></span> <span data-ttu-id="e1cf8-125">Im folgenden Beispiel wird das Freigeben von Text veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-125">The following example demonstrates sharing text.</span></span>

[!code-cs[Main](./code/share_data/cs/MainPage.xaml.cs#SnippetSetContent)]

## <a name="set-properties"></a><span data-ttu-id="e1cf8-126">Festlegen von Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e1cf8-126">Set properties</span></span>

<span data-ttu-id="e1cf8-127">Beim Verpacken von Daten für die Freigabe können Sie eine Vielzahl von Eigenschaften angeben, die weitere Informationen zum freigegebenen Inhalt enthalten.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-127">When you package data for sharing, you can supply a variety of properties that provide additional information about the content being shared.</span></span> <span data-ttu-id="e1cf8-128">Mit diesen Eigenschaften kann die Benutzererfahrung für Ziel-Apps verbessert werden.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-128">These properties help target apps improve the user experience.</span></span> <span data-ttu-id="e1cf8-129">Die Angabe einer Beschreibung kann beispielsweise nützlich sein, wenn der Benutzer Inhalte für mehrere Apps freigibt.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-129">For example, a description helps when the user is sharing content with more than one app.</span></span> <span data-ttu-id="e1cf8-130">Eine Miniaturansicht beim Freigeben eines Bilds oder eines Links für eine Webseite stellt eine visuelle Referenz für den Benutzer dar.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-130">Adding a thumbnail when sharing an image or a link to a web page provides a visual reference to the user.</span></span> <span data-ttu-id="e1cf8-131">Weitere Informationen finden Sie unter [**DataPackagePropertySet**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackagePropertySet).</span><span class="sxs-lookup"><span data-stu-id="e1cf8-131">For more information, see [**DataPackagePropertySet**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackagePropertySet).</span></span>

<span data-ttu-id="e1cf8-132">Alle Eigenschaften mit Ausnahme des Titels sind optional.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-132">All properties except the title are optional.</span></span> <span data-ttu-id="e1cf8-133">Die title-Eigenschaft ist erforderlich und muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-133">The title property is mandatory and must be set.</span></span>

[!code-cs[Main](./code/share_data/cs/MainPage.xaml.cs#SnippetSetProperties)]

## <a name="launch-the-share-ui"></a><span data-ttu-id="e1cf8-134">Starten der Benutzeroberfläche für das Freigeben</span><span class="sxs-lookup"><span data-stu-id="e1cf8-134">Launch the share UI</span></span>

<span data-ttu-id="e1cf8-135">Eine Benutzeroberfläche für das Freigeben wird vom System bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-135">A UI for sharing is provided by the system.</span></span> <span data-ttu-id="e1cf8-136">Zum Starten rufen Sie die [**ShowShareUI**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.ShowShareUI)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-136">To launch it, call the [**ShowShareUI**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.ShowShareUI) method.</span></span>

[!code-cs[Main](./code/share_data/cs/MainPage.xaml.cs#SnippetShowUI)]

## <a name="handle-errors"></a><span data-ttu-id="e1cf8-137">Behandeln von Fehlern</span><span class="sxs-lookup"><span data-stu-id="e1cf8-137">Handle errors</span></span>

<span data-ttu-id="e1cf8-138">In den meisten Fällen ist das Freigeben von Inhalten ein einfacher Prozess.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-138">In most cases, sharing content is a straightforward process.</span></span> <span data-ttu-id="e1cf8-139">Es besteht jedoch immer die Möglichkeit, dass unerwartet ein Problem auftritt.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-139">However, there's always a chance that something unexpected could happen.</span></span> <span data-ttu-id="e1cf8-140">Es kann z.B. sein, dass die App voraussetzt, dass Inhalt ausgewählt wird, der Benutzer aber nichts ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-140">For example, the app might require the user to select content for sharing but the user didn't select any.</span></span> <span data-ttu-id="e1cf8-141">Um diese Situationen zu behandeln, verwenden Sie die [**FailWithDisplayText**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataRequest.FailWithDisplayText(System.String))-Methode, die dem Benutzer eine Meldung anzeigt, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-141">To handle these situations, use the [**FailWithDisplayText**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataRequest.FailWithDisplayText(System.String)) method, which will display a message to the user if something goes wrong.</span></span>

## <a name="delay-share-with-delegates"></a><span data-ttu-id="e1cf8-142">Verzögern der Freigabe mit Delegaten</span><span class="sxs-lookup"><span data-stu-id="e1cf8-142">Delay share with delegates</span></span>

<span data-ttu-id="e1cf8-143">Manchmal ist es nicht sinnvoll, die Daten, die der Benutzer freigeben möchte, direkt vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-143">Sometimes, it might not make sense to prepare the data that the user wants to share right away.</span></span> <span data-ttu-id="e1cf8-144">Wenn Ihre App z. B. das Senden von großen Bilddateien in verschiedenen Formaten unterstützt, ist es ineffizient, alle diese Bilder zu erstellen, bevor der Benutzer seine Auswahl trifft.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-144">For example, if your app supports sending a large image file in several different possible formats, it's inefficient to create all those images before the user makes their selection.</span></span>

<span data-ttu-id="e1cf8-145">Zum Lösen dieses Problems kann ein [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) einen Delegaten enthalten. Dabei handelt es sich um eine Funktion, die aufgerufen wird, wenn die empfangende App Daten anfordert.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-145">To solve this problem, a [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) can contain a delegate — a function that is called when the receiving app requests data.</span></span> <span data-ttu-id="e1cf8-146">Es wird empfohlen, einen Delegaten immer dann zu verwenden, wenn die von einem Benutzer freigegebenen Daten ressourcenintensiv sind.</span><span class="sxs-lookup"><span data-stu-id="e1cf8-146">We recommend using a delegate any time that the data a user wants to share is resource-intensive.</span></span>

<!-- For some reason, this snippet was inline in the WDCML topic. Suggest moving to VS project with rest of snippets. -->
```cs
async void OnDeferredImageRequestedHandler(DataProviderRequest request)
{
    // Provide updated bitmap data using delayed rendering
    if (this.imageStream != null)
    {
        DataProviderDeferral deferral = request.GetDeferral();
        InMemoryRandomAccessStream inMemoryStream = new InMemoryRandomAccessStream();

        // Decode the image.
        BitmapDecoder imageDecoder = await BitmapDecoder.CreateAsync(this.imageStream);

        // Re-encode the image at 50% width and height.
        BitmapEncoder imageEncoder = await BitmapEncoder.CreateForTranscodingAsync(inMemoryStream, imageDecoder);
        imageEncoder.BitmapTransform.ScaledWidth = (uint)(imageDecoder.OrientedPixelHeight * 0.5);
        imageEncoder.BitmapTransform.ScaledHeight = (uint)(imageDecoder.OrientedPixelHeight * 0.5);
        await imageEncoder.FlushAsync();

        request.SetData(RandomAccessStreamReference.CreateFromStream(inMemoryStream));
        deferral.Complete();
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e1cf8-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e1cf8-147">See also</span></span> 

* [<span data-ttu-id="e1cf8-148">App-zu-App-Kommunikation</span><span class="sxs-lookup"><span data-stu-id="e1cf8-148">App-to-app communication</span></span>](index.md)
* [<span data-ttu-id="e1cf8-149">Empfangen von Daten</span><span class="sxs-lookup"><span data-stu-id="e1cf8-149">Receive data</span></span>](receive-data.md)
* [<span data-ttu-id="e1cf8-150">DataPackage</span><span class="sxs-lookup"><span data-stu-id="e1cf8-150">DataPackage</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackage.aspx)
* [<span data-ttu-id="e1cf8-151">DataPackagePropertySet</span><span class="sxs-lookup"><span data-stu-id="e1cf8-151">DataPackagePropertySet</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackagepropertyset.aspx)
* [<span data-ttu-id="e1cf8-152">DataRequest</span><span class="sxs-lookup"><span data-stu-id="e1cf8-152">DataRequest</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datarequest.aspx)
* [<span data-ttu-id="e1cf8-153">DataRequested</span><span class="sxs-lookup"><span data-stu-id="e1cf8-153">DataRequested</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.datarequested.aspx)
* [<span data-ttu-id="e1cf8-154">FailWithDisplayText</span><span class="sxs-lookup"><span data-stu-id="e1cf8-154">FailWithDisplayText</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datarequest.failwithdisplaytext.aspx)
* [<span data-ttu-id="e1cf8-155">ShowShareUi</span><span class="sxs-lookup"><span data-stu-id="e1cf8-155">ShowShareUi</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.showshareui.aspx)
 

