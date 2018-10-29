---
description: In diesem Artikel wird erläutert, wie Sie in Ihrer UWP-App (Universelle Windows-Plattform) Inhalte empfangen, die in einer anderen App mithilfe des Freigabe-Vertrags freigegeben wurden. Mit diesem Freigabe-Vertrag kann Ihre App als Option angezeigt werden, wenn der Benutzer „Freigeben“ aufruft.
title: Empfangen von Daten
ms.assetid: 0AFF9E0D-DFF4-4018-B393-A26B11AFDB41
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7d64e4a2d4251aca6bbce39b5f24e3e5f35295b8
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5743014"
---
# <a name="receive-data"></a><span data-ttu-id="6d9ac-105">Empfangen von Daten</span><span class="sxs-lookup"><span data-stu-id="6d9ac-105">Receive data</span></span>



<span data-ttu-id="6d9ac-106">In diesem Artikel wird erläutert, wie Sie in Ihrer UWP-App (Universelle Windows-Plattform) Inhalte empfangen, die in einer anderen App mithilfe des Freigabe-Vertrags freigegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-106">This article explains how to receive content in your Universal Windows Platform (UWP) app shared from another app by using Share contract.</span></span> <span data-ttu-id="6d9ac-107">Mit diesem Freigabe-Vertrag kann Ihre App als Option angezeigt werden, wenn der Benutzer „Freigeben“ aufruft.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-107">This Share contract allows your app to be presented as an option when the user invokes Share.</span></span>

## <a name="declare-your-app-as-a-share-target"></a><span data-ttu-id="6d9ac-108">Deklarieren der App als Freigabeziel</span><span class="sxs-lookup"><span data-stu-id="6d9ac-108">Declare your app as a share target</span></span>

<span data-ttu-id="6d9ac-109">Das System zeigt eine Liste der möglichen Ziel-Apps, wenn ein Benutzer „Freigeben“ aufruft.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-109">The system displays a list of possible target apps when a user invokes Share.</span></span> <span data-ttu-id="6d9ac-110">Damit sie in der Liste angezeigt wird, muss Ihre App deklarieren, dass sie den Freigabe-Vertrag unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-110">In order to appear on the list, your app needs to declare that it supports the Share contract.</span></span> <span data-ttu-id="6d9ac-111">Dies informiert das System darüber, dass Ihre App für das Empfangen von Inhalten zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-111">This lets the system know that your app is available to receive content.</span></span>

1.  <span data-ttu-id="6d9ac-112">Öffnen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-112">Open the manifest file.</span></span> <span data-ttu-id="6d9ac-113">Ihr Name lautet in etwa **package.appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-113">It should be called something like **package.appxmanifest**.</span></span>
2.  <span data-ttu-id="6d9ac-114">Öffnen Sie die Registerkarte **Deklarationen**.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-114">Open the **Declarations** tab.</span></span>
3.  <span data-ttu-id="6d9ac-115">Wählen Sie in der Liste **Verfügbare Deklarationen** die Option **Ziel freigeben** aus, und klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-115">Choose **Share Target** from the **Available Declarations** list, and then select **Add**.</span></span>

## <a name="choose-file-types-and-formats"></a><span data-ttu-id="6d9ac-116">Auswählen von Dateitypen und Formaten</span><span class="sxs-lookup"><span data-stu-id="6d9ac-116">Choose file types and formats</span></span>

<span data-ttu-id="6d9ac-117">Als Nächstes müssen Sie entscheiden, welche Dateitypen und Datenformate Sie unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-117">Next, decide what file types and data formats you support.</span></span> <span data-ttu-id="6d9ac-118">Die Freigabe-APIs unterstützen verschiedene Standardformate wie Text, HTML und Bitmaps.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-118">The Share APIs support several standard formats, such as Text, HTML, and Bitmap.</span></span> <span data-ttu-id="6d9ac-119">Sie können auch benutzerdefinierte Dateitypen und Datenformate angeben.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-119">You can also specify custom file types and data formats.</span></span> <span data-ttu-id="6d9ac-120">Denken Sie in solchen Fällen jedoch daran, dass die Quell-Apps wissen müssen, welcher Art diese Typen und Formate sind, da sie diese andernfalls nicht für das Freigeben von Daten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-120">If you do, remember that source apps have to know what those types and formats are; otherwise, those apps can't use the formats to share data.</span></span>

<span data-ttu-id="6d9ac-121">Führen Sie die Registrierung nur für Formate durch, die für Ihre App geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-121">Only register for formats that your app can handle.</span></span> <span data-ttu-id="6d9ac-122">Wenn der Benutzer „Freigeben“ aufruft, werden nur Ziel-Apps angezeigt, die die freigegebenen Daten auch unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-122">Only target apps that support the data being shared appear when the user invokes Share.</span></span>

<span data-ttu-id="6d9ac-123">So legen Sie Dateitypen fest</span><span class="sxs-lookup"><span data-stu-id="6d9ac-123">To set file types:</span></span>

1.  <span data-ttu-id="6d9ac-124">Öffnen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-124">Open the manifest file.</span></span> <span data-ttu-id="6d9ac-125">Ihr Name lautet in etwa **package.appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-125">It should be called something like **package.appxmanifest**.</span></span>
2.  <span data-ttu-id="6d9ac-126">Klicken Sie im Abschnitt **Unterstützte Dateitypen** der Seite **Deklarationen** auf **Neue Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-126">In the **Supported File Types** section of the **Declarations** page, select **Add New**.</span></span>
3.  <span data-ttu-id="6d9ac-127">Geben Sie die zu unterstützenden Dateierweiterungen ein, beispielsweise „.docx“,</span><span class="sxs-lookup"><span data-stu-id="6d9ac-127">Type the file name extension that you want to support, for example, ".docx."</span></span> <span data-ttu-id="6d9ac-128">Sie müssen den Punkt angeben.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-128">You need to include the period.</span></span> <span data-ttu-id="6d9ac-129">Wenn Sie alle Dateitypen unterstützen möchten, aktivieren Sie das Kontrollkästchen **SupportsAnyFileType**.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-129">If you want to support all file types, select the **SupportsAnyFileType** check box.</span></span>

<span data-ttu-id="6d9ac-130">So richten Sie Datenformate ein</span><span class="sxs-lookup"><span data-stu-id="6d9ac-130">To set data formats:</span></span>

1.  <span data-ttu-id="6d9ac-131">Öffnen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-131">Open the manifest file.</span></span>
2.  <span data-ttu-id="6d9ac-132">Öffnen Sie den Abschnitt **Datenformate** der Seite **Deklarationen**, und klicken Sie auf **Neue Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-132">Open the **Data Formats** section of the **Declarations** page, and then select **Add New**.</span></span>
3.  <span data-ttu-id="6d9ac-133">Geben Sie den Namen des Datenformats ein, das Sie unterstützen, zum Beispiel „Text“.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-133">Type the name of the data format you support, for example, "Text."</span></span>

## <a name="handle-share-activation"></a><span data-ttu-id="6d9ac-134">Handhabung der Freigabeaktivierung</span><span class="sxs-lookup"><span data-stu-id="6d9ac-134">Handle share activation</span></span>

<span data-ttu-id="6d9ac-135">Wenn ein Benutzer Ihre App auswählt (i.d.R. durch die Auswahl aus einer Liste verfügbarer Ziel-Apps auf der Benutzeroberfläche für das Freigeben), wird ein [**OnShareTargetActivated**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Application.OnShareTargetActivated(Windows.ApplicationModel.Activation.ShareTargetActivatedEventArgs))-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-135">When a user selects your app (usually by selecting it from a list of available target apps in the share UI), an [**OnShareTargetActivated**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Application.OnShareTargetActivated(Windows.ApplicationModel.Activation.ShareTargetActivatedEventArgs)) event is raised.</span></span> <span data-ttu-id="6d9ac-136">Ihre App muss dieses Ereignis behandeln, um die Daten, die der Benutzer freigeben möchte, verarbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-136">Your app needs to handle this event to process the data that the user wants to share.</span></span>

<!-- For some reason, the snippets in this file are all inline in the WDCML topic. Suggest moving to VS project with rest of snippets. -->
```cs
protected override async void OnShareTargetActivated(ShareTargetActivatedEventArgs args)
{
    // Code to handle activation goes here. 
} 
```

<span data-ttu-id="6d9ac-137">Die Daten, die ein Benutzer freigeben möchte, sind in einem [**ShareOperation**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation)-Objekt enthalten.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-137">The data that the user wants to share is contained in a [**ShareOperation**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation) object.</span></span> <span data-ttu-id="6d9ac-138">Mithilfe dieses Objekts können Sie das Format der enthaltenen Daten ermitteln.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-138">You can use this object to check the format of the data it contains.</span></span>

```cs
ShareOperation shareOperation = args.ShareOperation;
if (shareOperation.Data.Contains(StandardDataFormats.Text))
{
    string text = await shareOperation.Data.GetTextAsync();

    // To output the text from this example, you need a TextBlock control
    // with a name of "sharedContent".
    sharedContent.Text = "Text: " + text;
} 
```

## <a name="report-sharing-status"></a><span data-ttu-id="6d9ac-139">Bericht über den Freigabestatus</span><span class="sxs-lookup"><span data-stu-id="6d9ac-139">Report sharing status</span></span>

<span data-ttu-id="6d9ac-140">In einigen Fällen kann es eine Weile dauern, bis Ihre App die freizugebenden Daten verarbeitet hat.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-140">In some cases, it can take time for your app to process the data it wants to share.</span></span> <span data-ttu-id="6d9ac-141">Beispiele umfassen die Freigabe von Datei- oder Bildsammlungen.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-141">Examples include users sharing collections of files or images.</span></span> <span data-ttu-id="6d9ac-142">Diese Elemente sind größer als einfache Textzeichenfolgen, sodass auch ihre Verarbeitung länger dauert.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-142">These items are larger than a simple text string, so they take longer to process.</span></span>

```cs
shareOperation.ReportStarted(); 
```

<span data-ttu-id="6d9ac-143">Erwarten Sie nach dem Aufrufen von [**ReportStarted**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportStarted) keine Benutzerinteraktion mit der App mehr.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-143">After calling [**ReportStarted**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportStarted), don't expect any more user interaction with your app.</span></span> <span data-ttu-id="6d9ac-144">Führen Sie diesen Aufruf daher nur durch, wenn Ihre App vom Benutzer geschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-144">As a result, you shouldn't call it unless your app is at a point where it can be dismissed by the user.</span></span>

<span data-ttu-id="6d9ac-145">Bei einer erweiterten Freigabe ist es möglich, dass der Benutzer die Quell-App schließt, bevor Ihre App alle Daten aus dem DataPackage-Objekt abgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-145">With an extended share, it's possible that the user might dismiss the source app before your app has all the data from the DataPackage object.</span></span> <span data-ttu-id="6d9ac-146">Es wird daher empfohlen, dass Sie das System informieren, wenn Ihre App die erforderlichen Daten erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-146">As a result, we recommend that you let the system know when your app has acquired the data it needs.</span></span> <span data-ttu-id="6d9ac-147">So kann das System die Quell-App ggf. anhalten oder beenden.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-147">This way, the system can suspend or terminate the source app as necessary.</span></span>

```cs
shareOperation.ReportSubmittedBackgroundTask(); 
```

<span data-ttu-id="6d9ac-148">Rufen Sie [**ReportError**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportError(System.String)) auf, falls ein Fehler auftritt, um eine Fehlermeldung an das System zu senden.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-148">If something goes wrong, call [**ReportError**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportError(System.String)) to send an error message to the system.</span></span> <span data-ttu-id="6d9ac-149">Die Meldung wird angezeigt, wenn der Benutzer den Status der Freigabe überprüft.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-149">The user will see the message when they check on the status of the share.</span></span> <span data-ttu-id="6d9ac-150">An dieser Stelle wird die App heruntergefahren und die Freigabe beendet.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-150">At that point, your app is shut down and the share is ended.</span></span> <span data-ttu-id="6d9ac-151">Der Benutzer muss zum Freigeben des Inhalts für die App von vorn beginnen.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-151">The user will need to start again to share the content to your app.</span></span> <span data-ttu-id="6d9ac-152">In Abhängigkeit vom Szenario können Sie entscheiden, dass ein bestimmter Fehler nicht schwerwiegend genug ist, um den Freigabevorgang zu beenden.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-152">Depending on your scenario, you may decide that a particular error isn't serious enough to end the share operation.</span></span> <span data-ttu-id="6d9ac-153">In diesem Fall können Sie sich gegen das Aufrufen von **ReportError** entscheiden und mit dem Freigeben fortfahren.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-153">In that case, you can choose to not call **ReportError** and to continue with the share.</span></span>

```cs
shareOperation.ReportError("Could not reach the server! Try again later."); 
```

<span data-ttu-id="6d9ac-154">Rufen Sie zum Abschluss der erfolgreichen Verarbeitung der freigegebenen Daten durch Ihre App [**ReportCompleted**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportCompleted) auf, um das System zu informieren.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-154">Finally, when your app has successfully processed the shared content, you should call [**ReportCompleted**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportCompleted) to let the system know.</span></span>

```cs
shareOperation.ReportCompleted();
```

<span data-ttu-id="6d9ac-155">Halten Sie bei Verwendung dieser Methoden unbedingt die angegebene Reihenfolge ein, und rufen Sie die Methoden nicht mehrmals auf.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-155">When you use these methods, you usually call them in the order just described, and you don't call them more than once.</span></span> <span data-ttu-id="6d9ac-156">Unter bestimmten Umständen kann [**ReportDataRetrieved**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportDataRetrieved) von einer Ziel-App vor [**ReportStarted**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportStarted) aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-156">However, there are times when a target app can call [**ReportDataRetrieved**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportDataRetrieved) before [**ReportStarted**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportStarted).</span></span> <span data-ttu-id="6d9ac-157">Beispielweise können die Daten von der App im Rahmen einer Aufgabe des Aktivierungshandlers aufgerufen werden. **ReportStarted** wird jedoch erst aufgerufen, wenn der Benutzer auf eine **Freigeben**-Schaltfläche klickt.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-157">For example, the app might retrieve the data as part of a task in the activation handler, but not call **ReportStarted** until the user selects a **Share** button.</span></span>

## <a name="return-a-quicklink-if-sharing-was-successful"></a><span data-ttu-id="6d9ac-158">Zurückgeben eines QuickLink-Objekts nach erfolgreicher Freigabe</span><span class="sxs-lookup"><span data-stu-id="6d9ac-158">Return a QuickLink if sharing was successful</span></span>

<span data-ttu-id="6d9ac-159">Wählt ein Benutzer Ihre App aus, um Inhalte zu empfangen, sollten Sie einen [**QuickLink**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.QuickLink) erstellen.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-159">When a user selects your app to receive content, we recommend that you create a [**QuickLink**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.QuickLink).</span></span> <span data-ttu-id="6d9ac-160">Ein **QuickLink** ähnelt einer Verknüpfung, über die Benutzer leichter Informationen mit Ihrer App austauschen können.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-160">A **QuickLink** is like a shortcut that makes it easier for users to share information with your app.</span></span> <span data-ttu-id="6d9ac-161">Sie könnten beispielsweise einen **QuickLink** erstellen, der eine neue E-Mail erstellt, die bereits die E-Mail-Adresse eines Freundes enthält.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-161">For example, you could create a **QuickLink** that opens a new mail message pre-configured with a friend's email address.</span></span>

<span data-ttu-id="6d9ac-162">Ein **QuickLink** muss über einen Titel, ein Symbol und eine ID verfügen. Der Titel (z. B. „E-Mail an Mutter“) und das Symbol werden angezeigt, wenn der Benutzer auf den Charm „Teilen“ tippt.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-162">A **QuickLink** must have a title, an icon, and an Id. The title (like "Email Mom") and icon appear when the user taps the Share charm.</span></span> <span data-ttu-id="6d9ac-163">Die ID verwendet Ihre App für den Zugriff auf benutzerdefinierte Informationen wie eine E-Mail-Adresse oder Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-163">The Id is what your app uses to access any custom information, such as an email address or login credentials.</span></span> <span data-ttu-id="6d9ac-164">Wenn Ihre App einen **QuickLink** erstellt, gibt sie den **QuickLink** an das System zurück, indem sie [**ReportCompleted**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportCompleted) aufruft.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-164">When your app creates a **QuickLink**, the app returns the **QuickLink** to the system by calling [**ReportCompleted**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.ReportCompleted).</span></span>

<span data-ttu-id="6d9ac-165">Von einem **QuickLink** werden keine Daten gespeichert.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-165">A **QuickLink** does not actually store data.</span></span> <span data-ttu-id="6d9ac-166">Stattdessen enthält er eine ID, die beim Auswählen an die App gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-166">Instead, it contains an identifier that, when selected, is sent to your app.</span></span> <span data-ttu-id="6d9ac-167">Ihre App ist selbst für das Speichern der ID für den **QuickLink** und die damit zusammenhängenden Benutzerdaten verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-167">Your app is responsible for storing the Id of the **QuickLink** and the corresponding user data.</span></span> <span data-ttu-id="6d9ac-168">Wenn der Benutzer auf den **QuickLink** tippt, können Sie seine ID über die [**QuickLinkId**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.QuickLinkId)-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="6d9ac-168">When the user taps the **QuickLink**, you can get its Id through the [**QuickLinkId**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.DataTransfer.ShareTarget.ShareOperation.QuickLinkId) property.</span></span>

```cs
async void ReportCompleted(ShareOperation shareOperation, string quickLinkId, string quickLinkTitle)
{
    QuickLink quickLinkInfo = new QuickLink
    {
        Id = quickLinkId,
        Title = quickLinkTitle,

        // For quicklinks, the supported FileTypes and DataFormats are set 
        // independently from the manifest
        SupportedFileTypes = { "*" },
        SupportedDataFormats = { StandardDataFormats.Text, StandardDataFormats.Uri, 
                StandardDataFormats.Bitmap, StandardDataFormats.StorageItems }
    };

    StorageFile iconFile = await Windows.ApplicationModel.Package.Current.InstalledLocation.CreateFileAsync(
            "assets\\user.png", CreationCollisionOption.OpenIfExists);
    quickLinkInfo.Thumbnail = RandomAccessStreamReference.CreateFromFile(iconFile);
    shareOperation.ReportCompleted(quickLinkInfo);
}
```

## <a name="see-also"></a><span data-ttu-id="6d9ac-169">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6d9ac-169">See also</span></span> 

* [<span data-ttu-id="6d9ac-170">App-zu-App-Kommunikation</span><span class="sxs-lookup"><span data-stu-id="6d9ac-170">App-to-app communication</span></span>](index.md)
* [<span data-ttu-id="6d9ac-171">Freigeben von Daten</span><span class="sxs-lookup"><span data-stu-id="6d9ac-171">Share data</span></span>](share-data.md)
* [<span data-ttu-id="6d9ac-172">OnShareTargetActivated</span><span class="sxs-lookup"><span data-stu-id="6d9ac-172">OnShareTargetActivated</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onsharetargetactivated.aspx)
* [<span data-ttu-id="6d9ac-173">ReportStarted</span><span class="sxs-lookup"><span data-stu-id="6d9ac-173">ReportStarted</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharetarget.shareoperation.reportstarted.aspx)
* [<span data-ttu-id="6d9ac-174">ReportError</span><span class="sxs-lookup"><span data-stu-id="6d9ac-174">ReportError</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharetarget.shareoperation.reporterror.aspx)
* [<span data-ttu-id="6d9ac-175">ReportCompleted</span><span class="sxs-lookup"><span data-stu-id="6d9ac-175">ReportCompleted</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharetarget.shareoperation.reportcompleted.aspx)
* [<span data-ttu-id="6d9ac-176">ReportDataRetrieved</span><span class="sxs-lookup"><span data-stu-id="6d9ac-176">ReportDataRetrieved</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharetarget.shareoperation.reportdataretrieved.aspx)
* [<span data-ttu-id="6d9ac-177">ReportStarted</span><span class="sxs-lookup"><span data-stu-id="6d9ac-177">ReportStarted</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharetarget.shareoperation.reportstarted.aspx)
* [<span data-ttu-id="6d9ac-178">QuickLink</span><span class="sxs-lookup"><span data-stu-id="6d9ac-178">QuickLink</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharetarget.quicklink.aspx)
* [<span data-ttu-id="6d9ac-179">QuickLInkId</span><span class="sxs-lookup"><span data-stu-id="6d9ac-179">QuickLInkId</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.sharetarget.quicklink.id.aspx)
