---
description: "In diesem Artikel wird erläutert, wie der Freigabe-Vertrag in einer UWP-App (Universelle Windows-Plattform) unterstützt wird."
title: Freigeben von Daten
ms.assetid: 32287F5E-EB86-4B98-97FF-8F6228D06782
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: fe6da350fbfe006b55e90aee8c12da90967f5711
ms.sourcegitcommit: 23cda44f10059bcaef38ae73fd1d7c8b8330c95e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2017
---
# <a name="share-data"></a><span data-ttu-id="ce468-104">Freigeben von Daten</span><span class="sxs-lookup"><span data-stu-id="ce468-104">Share data</span></span>

<span data-ttu-id="ce468-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="ce468-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="ce468-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="ce468-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="ce468-107">In diesem Artikel wird erläutert, wie der Freigabe-Vertrag in einer UWP-App (Universelle Windows-Plattform) unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="ce468-107">This article explains how to support the Share contract in a Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="ce468-108">Der Freigabe-Vertrag ist eine einfache Möglichkeit, Daten wie z.B. Text, Links, Fotos und Videos schnell für andere Apps freizugeben.</span><span class="sxs-lookup"><span data-stu-id="ce468-108">The Share contract is an easy way to quickly share data, such as text, links, photos, and videos, between apps.</span></span> <span data-ttu-id="ce468-109">Ein Benutzer möchte beispielsweise mit einer App für ein soziales Netzwerk eine Webseite mit seinen Freunden teilen, oder er möchte in einer Notiz-App einen Link für später speichern.</span><span class="sxs-lookup"><span data-stu-id="ce468-109">For example, a user might want to share a webpage with their friends using a social networking app, or save a link in a notes app to refer to later.</span></span>

## <a name="set-up-an-event-handler"></a><span data-ttu-id="ce468-110">Einrichten eines Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="ce468-110">Set up an event handler</span></span>

<span data-ttu-id="ce468-111">Fügen Sie einen [**DataRequested**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.DataRequested)-Ereignishandler hinzu, der aufgerufen werden soll, wenn der Benutzer das Teilen-Feature verwendet.</span><span class="sxs-lookup"><span data-stu-id="ce468-111">Add a [**DataRequested**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.DataRequested) event handler to be called whenever a user invokes share.</span></span> <span data-ttu-id="ce468-112">Dies kann durch Tippen auf ein Steuerelement in Ihrer App (etwa eine Schaltfläche oder ein App-Leistenbefehl) oder automatisch in einem bestimmten Szenario geschehen (etwa wenn der Benutzer einen Level mit einer hohen Punktzahl abschließt).</span><span class="sxs-lookup"><span data-stu-id="ce468-112">This can occur either when the user taps a control in your app (such as a button or app bar command) or automatically in a specific scenario (if the user finishes a level and gets a high score, for example).</span></span>

[!code-cs[<span data-ttu-id="ce468-113">Main</span><span class="sxs-lookup"><span data-stu-id="ce468-113">Main</span></span>](./code/share_data/cs/MainPage.xaml.cs#SnippetPrepareToShare)]

<span data-ttu-id="ce468-114">Wenn ein [**DataRequested**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.DataRequested)-Ereignis eintritt, empfängt Ihre App ein [**DataRequest**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataRequest)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="ce468-114">When a [**DataRequested**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.DataRequested) event occurs, your app receives a [**DataRequest**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataRequest) object.</span></span> <span data-ttu-id="ce468-115">Dieses enthält ein [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage), mit dem Sie den Inhalt bereitstellen können, den der Benutzer freigeben möchte.</span><span class="sxs-lookup"><span data-stu-id="ce468-115">This contains a [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) that you can use to provide the content that the user wants to share.</span></span> <span data-ttu-id="ce468-116">Sie müssen einen Titel und die freizugebenden Daten angeben.</span><span class="sxs-lookup"><span data-stu-id="ce468-116">You must provide a title and data to share.</span></span> <span data-ttu-id="ce468-117">Eine Beschreibung ist optional, wird aber empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ce468-117">A description is optional, but recommended.</span></span>

[!code-cs[<span data-ttu-id="ce468-118">Main</span><span class="sxs-lookup"><span data-stu-id="ce468-118">Main</span></span>](./code/share_data/cs/MainPage.xaml.cs#SnippetCreateRequest)]

## <a name="choose-data"></a><span data-ttu-id="ce468-119">Wählen von Daten</span><span class="sxs-lookup"><span data-stu-id="ce468-119">Choose data</span></span>

<span data-ttu-id="ce468-120">Sie können verschiedene Arten von Daten freigeben, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="ce468-120">You can share various types of data, including:</span></span>

-   <span data-ttu-id="ce468-121">Nur-Text</span><span class="sxs-lookup"><span data-stu-id="ce468-121">Plain text</span></span>
-   <span data-ttu-id="ce468-122">URIs (Uniform Resource Identifiers)</span><span class="sxs-lookup"><span data-stu-id="ce468-122">Uniform Resource Identifiers (URIs)</span></span>
-   <span data-ttu-id="ce468-123">HTML</span><span class="sxs-lookup"><span data-stu-id="ce468-123">HTML</span></span>
-   <span data-ttu-id="ce468-124">Formatierter Text</span><span class="sxs-lookup"><span data-stu-id="ce468-124">Formatted text</span></span>
-   <span data-ttu-id="ce468-125">Bitmaps</span><span class="sxs-lookup"><span data-stu-id="ce468-125">Bitmaps</span></span>
-   <span data-ttu-id="ce468-126">Nur-Text</span><span class="sxs-lookup"><span data-stu-id="ce468-126">Plain text</span></span>
-   <span data-ttu-id="ce468-127">Dateien</span><span class="sxs-lookup"><span data-stu-id="ce468-127">Files</span></span>
-   <span data-ttu-id="ce468-128">Vom Entwickler definierte Daten</span><span class="sxs-lookup"><span data-stu-id="ce468-128">Custom developer-defined data</span></span>

<span data-ttu-id="ce468-129">Das [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage)-Objekt kann mehrere dieser Formate in beliebiger Kombination enthalten.</span><span class="sxs-lookup"><span data-stu-id="ce468-129">The [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) object can contain one or more of these formats, in any combination.</span></span> <span data-ttu-id="ce468-130">Im folgenden Beispiel wird das Freigeben von Text veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="ce468-130">The following example demonstrates sharing text.</span></span>

[!code-cs[<span data-ttu-id="ce468-131">Main</span><span class="sxs-lookup"><span data-stu-id="ce468-131">Main</span></span>](./code/share_data/cs/MainPage.xaml.cs#SnippetSetContent)]

## <a name="set-properties"></a><span data-ttu-id="ce468-132">Festlegen von Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ce468-132">Set properties</span></span>

<span data-ttu-id="ce468-133">Beim Verpacken von Daten für die Freigabe können Sie eine Vielzahl von Eigenschaften angeben, die weitere Informationen zum freigegebenen Inhalt enthalten.</span><span class="sxs-lookup"><span data-stu-id="ce468-133">When you package data for sharing, you can supply a variety of properties that provide additional information about the content being shared.</span></span> <span data-ttu-id="ce468-134">Mit diesen Eigenschaften kann die Benutzererfahrung für Ziel-Apps verbessert werden.</span><span class="sxs-lookup"><span data-stu-id="ce468-134">These properties help target apps improve the user experience.</span></span> <span data-ttu-id="ce468-135">Die Angabe einer Beschreibung kann beispielsweise nützlich sein, wenn der Benutzer Inhalte für mehrere Apps freigibt.</span><span class="sxs-lookup"><span data-stu-id="ce468-135">For example, a description helps when the user is sharing content with more than one app.</span></span> <span data-ttu-id="ce468-136">Eine Miniaturansicht beim Freigeben eines Bilds oder eines Links für eine Webseite stellt eine visuelle Referenz für den Benutzer dar.</span><span class="sxs-lookup"><span data-stu-id="ce468-136">Adding a thumbnail when sharing an image or a link to a web page provides a visual reference to the user.</span></span> <span data-ttu-id="ce468-137">Weitere Informationen finden Sie unter [**DataPackagePropertySet**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackagePropertySet).</span><span class="sxs-lookup"><span data-stu-id="ce468-137">For more information, see [**DataPackagePropertySet**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackagePropertySet).</span></span>

<span data-ttu-id="ce468-138">Alle Eigenschaften mit Ausnahme des Titels sind optional.</span><span class="sxs-lookup"><span data-stu-id="ce468-138">All properties except the title are optional.</span></span> <span data-ttu-id="ce468-139">Die title-Eigenschaft ist erforderlich und muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="ce468-139">The title property is mandatory and must be set.</span></span>

[!code-cs[<span data-ttu-id="ce468-140">Main</span><span class="sxs-lookup"><span data-stu-id="ce468-140">Main</span></span>](./code/share_data/cs/MainPage.xaml.cs#SnippetSetProperties)]

## <a name="launch-the-share-ui"></a><span data-ttu-id="ce468-141">Starten der Benutzeroberfläche für das Freigeben</span><span class="sxs-lookup"><span data-stu-id="ce468-141">Launch the share UI</span></span>

<span data-ttu-id="ce468-142">Eine Benutzeroberfläche für das Freigeben wird vom System bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ce468-142">A UI for sharing is provided by the system.</span></span> <span data-ttu-id="ce468-143">Zum Starten rufen Sie die [**ShowShareUI**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.ShowShareUI)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="ce468-143">To launch it, call the [**ShowShareUI**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataTransferManager.ShowShareUI) method.</span></span>

[!code-cs[<span data-ttu-id="ce468-144">Main</span><span class="sxs-lookup"><span data-stu-id="ce468-144">Main</span></span>](./code/share_data/cs/MainPage.xaml.cs#SnippetShowUI)]

## <a name="handle-errors"></a><span data-ttu-id="ce468-145">Behandeln von Fehlern</span><span class="sxs-lookup"><span data-stu-id="ce468-145">Handle errors</span></span>

<span data-ttu-id="ce468-146">In den meisten Fällen ist das Freigeben von Inhalten ein einfacher Prozess.</span><span class="sxs-lookup"><span data-stu-id="ce468-146">In most cases, sharing content is a straightforward process.</span></span> <span data-ttu-id="ce468-147">Es besteht jedoch immer die Möglichkeit, dass unerwartet ein Problem auftritt.</span><span class="sxs-lookup"><span data-stu-id="ce468-147">However, there's always a chance that something unexpected could happen.</span></span> <span data-ttu-id="ce468-148">Es kann z.B. sein, dass die App voraussetzt, dass Inhalt ausgewählt wird, der Benutzer aber nichts ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="ce468-148">For example, the app might require the user to select content for sharing but the user didn't select any.</span></span> <span data-ttu-id="ce468-149">Um diese Situationen zu behandeln, verwenden Sie die [**FailWithDisplayText**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataRequest.FailWithDisplayText(System.String))-Methode, die dem Benutzer eine Meldung anzeigt, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="ce468-149">To handle these situations, use the [**FailWithDisplayText**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataRequest.FailWithDisplayText(System.String)) method, which will display a message to the user if something goes wrong.</span></span>

## <a name="delay-share-with-delegates"></a><span data-ttu-id="ce468-150">Verzögern der Freigabe mit Delegaten</span><span class="sxs-lookup"><span data-stu-id="ce468-150">Delay share with delegates</span></span>

<span data-ttu-id="ce468-151">Manchmal ist es nicht sinnvoll, die Daten, die der Benutzer freigeben möchte, direkt vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="ce468-151">Sometimes, it might not make sense to prepare the data that the user wants to share right away.</span></span> <span data-ttu-id="ce468-152">Wenn Ihre App z. B. das Senden von großen Bilddateien in verschiedenen Formaten unterstützt, ist es ineffizient, alle diese Bilder zu erstellen, bevor der Benutzer seine Auswahl trifft.</span><span class="sxs-lookup"><span data-stu-id="ce468-152">For example, if your app supports sending a large image file in several different possible formats, it's inefficient to create all those images before the user makes their selection.</span></span>

<span data-ttu-id="ce468-153">Zum Lösen dieses Problems kann ein [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) einen Delegaten enthalten. Dabei handelt es sich um eine Funktion, die aufgerufen wird, wenn die empfangende App Daten anfordert.</span><span class="sxs-lookup"><span data-stu-id="ce468-153">To solve this problem, a [**DataPackage**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.DataPackage) can contain a delegate — a function that is called when the receiving app requests data.</span></span> <span data-ttu-id="ce468-154">Es wird empfohlen, einen Delegaten immer dann zu verwenden, wenn die von einem Benutzer freigegebenen Daten ressourcenintensiv sind.</span><span class="sxs-lookup"><span data-stu-id="ce468-154">We recommend using a delegate any time that the data a user wants to share is resource-intensive.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ce468-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ce468-155">See also</span></span> 

* [<span data-ttu-id="ce468-156">App-zu-App-Kommunikation</span><span class="sxs-lookup"><span data-stu-id="ce468-156">App-to-app communication</span></span>](index.md)
* [<span data-ttu-id="ce468-157">Empfangen von Daten</span><span class="sxs-lookup"><span data-stu-id="ce468-157">Receive data</span></span>](receive-data.md)
* [<span data-ttu-id="ce468-158">DataPackage</span><span class="sxs-lookup"><span data-stu-id="ce468-158">DataPackage</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackage.aspx)
* [<span data-ttu-id="ce468-159">DataPackagePropertySet</span><span class="sxs-lookup"><span data-stu-id="ce468-159">DataPackagePropertySet</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datapackagepropertyset.aspx)
* [<span data-ttu-id="ce468-160">DataRequest</span><span class="sxs-lookup"><span data-stu-id="ce468-160">DataRequest</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datarequest.aspx)
* [<span data-ttu-id="ce468-161">DataRequested</span><span class="sxs-lookup"><span data-stu-id="ce468-161">DataRequested</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.datarequested.aspx)
* [<span data-ttu-id="ce468-162">FailWithDisplayText</span><span class="sxs-lookup"><span data-stu-id="ce468-162">FailWithDisplayText</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datarequest.failwithdisplaytext.aspx)
* [<span data-ttu-id="ce468-163">ShowShareUi</span><span class="sxs-lookup"><span data-stu-id="ce468-163">ShowShareUi</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.showshareui.aspx)
 

