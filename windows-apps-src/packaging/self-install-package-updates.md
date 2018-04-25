---
author: mcleanbyron
ms.assetid: 414ACC73-2A72-465C-BD15-1B51CB2334F2
title: Herunterladen und Installieren von Paketupdates für Ihre App
description: Erfahren Sie, wie Sie Pakete im Dev Center-Dashboard als obligatorisch kennzeichnen und Code in Ihrer App zum Herunterladen und Installieren von Paketupdates schreiben.
ms.author: mcleans
ms.date: 03/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: high
ms.openlocfilehash: ce2f6d6607f09186a3969f37b6808fa1f04fb338
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="download-and-install-package-updates-for-your-app"></a><span data-ttu-id="5a686-104">Herunterladen und Installieren von Paketupdates für Ihre App</span><span class="sxs-lookup"><span data-stu-id="5a686-104">Download and install package updates for your app</span></span>


<span data-ttu-id="5a686-105">Ab Windows10 (Version 1607) können Sie eine API im Namespace [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) verwenden, um programmgesteuert nach Paketupdates für die aktuelle App zu suchen und diese herunterzuladen und zu installieren.</span><span class="sxs-lookup"><span data-stu-id="5a686-105">Starting in Windows 10, version 1607, you can use an API in the [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) namespace to programmatically check for package updates for the current app, and download and install the updated packages.</span></span> <span data-ttu-id="5a686-106">Sie können auch Abfragen für Pakete ausführen, die [im Windows Dev Center-Dashboard als obligatorisch gekennzeichnet](#mandatory-dashboard) wurden, und Funktionen in Ihrer App deaktivieren, bis das erforderliche Update installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="5a686-106">You can also query for packages that have been [marked as mandatory on the Windows Dev Center dashboard](#mandatory-dashboard) and disable functionality in your app until the mandatory update is installed.</span></span>

<span data-ttu-id="5a686-107">Mithilfe dieser Features können Sie Benutzer automatisch mit der neuesten Version Ihrer App und der zugehörigen Dienste auf dem neuesten Stand halten.</span><span class="sxs-lookup"><span data-stu-id="5a686-107">These features help you to automatically keep your user base up to date with the latest version of your app and related services.</span></span>

## <a name="api-overview"></a><span data-ttu-id="5a686-108">API-Übersicht</span><span class="sxs-lookup"><span data-stu-id="5a686-108">API overview</span></span>

<span data-ttu-id="5a686-109">In Apps für Windows10 (ab Version1607) können Sie die folgenden Methoden der [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Klasse verwenden, um Paketupdates herunterzuladen und zu installieren.</span><span class="sxs-lookup"><span data-stu-id="5a686-109">Apps that targets Windows 10, version 1607 or later can use the following methods of the [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext) class to download and install package updates.</span></span>

|  <span data-ttu-id="5a686-110">Methode</span><span class="sxs-lookup"><span data-stu-id="5a686-110">Method</span></span>  |  <span data-ttu-id="5a686-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5a686-111">Description</span></span>  |
|----------|---------------|
| [<span data-ttu-id="5a686-112">GetAppAndOptionalStorePackageUpdatesAsync</span><span class="sxs-lookup"><span data-stu-id="5a686-112">GetAppAndOptionalStorePackageUpdatesAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetAppAndOptionalStorePackageUpdatesAsync) | <span data-ttu-id="5a686-113">Rufen Sie diese Methode auf, um die Liste der verfügbaren Paketupdates abzurufen.</span><span class="sxs-lookup"><span data-stu-id="5a686-113">Call this method to get the list of package updates that are available.</span></span> <span data-ttu-id="5a686-114">Hinweis: Zwischen dem Zeitpunkt, an dem ein Paket den Zertifizierungsprozess durchläuft, und dem Zeitpunkt, an dem die Methode **GetAppAndOptionalStorePackageUpdatesAsync** erkennt, dass das Paketupdate für die App zur Verfügung steht, kann eine Verzögerung von bis zu einem Tag auftreten.</span><span class="sxs-lookup"><span data-stu-id="5a686-114">Note that there can be a delay of up to a day between the time when a package passes the certification process and when the **GetAppAndOptionalStorePackageUpdatesAsync** method recognizes that the package update is available to the app.</span></span> |
| [<span data-ttu-id="5a686-115">RequestDownloadStorePackageUpdatesAsync</span><span class="sxs-lookup"><span data-stu-id="5a686-115">RequestDownloadStorePackageUpdatesAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadstorepackageupdatesasync) | <span data-ttu-id="5a686-116">Rufen Sie diese Methode auf, um die verfügbaren Paketupdates herunterzuladen (jedoch nicht zu installieren).</span><span class="sxs-lookup"><span data-stu-id="5a686-116">Call this method to download (but not install) the available package updates.</span></span> <span data-ttu-id="5a686-117">Unter diesem Betriebssystem wird ein Dialogfeld angezeigt, in dem der Benutzer dem Herunterladen der Updates zustimmen muss.</span><span class="sxs-lookup"><span data-stu-id="5a686-117">This OS displays a dialog that asks the user's permission to download the updates.</span></span> |
| [<span data-ttu-id="5a686-118">RequestDownloadAndInstallStorePackageUpdatesAsync</span><span class="sxs-lookup"><span data-stu-id="5a686-118">RequestDownloadAndInstallStorePackageUpdatesAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadandinstallstorepackageupdatesasync) | <span data-ttu-id="5a686-119">Rufen Sie diese Methode auf, um die verfügbaren Paketupdates herunterzuladen und zu installieren.</span><span class="sxs-lookup"><span data-stu-id="5a686-119">Call this method to download and install the available package updates.</span></span> <span data-ttu-id="5a686-120">Unter dem Betriebssystem werden Dialogfelder angezeigt, in denen der Benutzer dem Herunterladen und Installieren der Updates zustimmen muss.</span><span class="sxs-lookup"><span data-stu-id="5a686-120">The OS displays dialogs that ask the user's permission to download and install the updates.</span></span> <span data-ttu-id="5a686-121">Wenn Sie die Paketupdates durch Aufrufen von **RequestDownloadStorePackageUpdatesAsync** bereits heruntergeladen haben, überspringt diese Methode den Downloadvorgang und installiert nur die Updates.</span><span class="sxs-lookup"><span data-stu-id="5a686-121">If you already downloaded the package updates by calling **RequestDownloadStorePackageUpdatesAsync**, this method skips the download process and only installs the updates.</span></span>  |

<span/>

<span data-ttu-id="5a686-122">Diese Methoden verwenden [StorePackageUpdate](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdate)-Objekte, die den verfügbaren Updatepaketen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="5a686-122">These methods use [StorePackageUpdate](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdate) objects to represent available update packages.</span></span> <span data-ttu-id="5a686-123">Verwenden Sie die folgenden **StorePackageUpdate**-Eigenschaften zum Abrufen von Informationen über ein Updatepaket.</span><span class="sxs-lookup"><span data-stu-id="5a686-123">Use the following **StorePackageUpdate** properties to get information about an update package.</span></span>

|  <span data-ttu-id="5a686-124">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="5a686-124">Property</span></span>  |  <span data-ttu-id="5a686-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5a686-125">Description</span></span>  |
|----------|---------------|
| [<span data-ttu-id="5a686-126">Mandatory</span><span class="sxs-lookup"><span data-stu-id="5a686-126">Mandatory</span></span>](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdate.Mandatory) | <span data-ttu-id="5a686-127">Verwenden Sie diese Eigenschaft, um zu ermitteln, ob das Paket im Dev Center-Dashboard als obligatorisch gekennzeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="5a686-127">Use this property to determine whether the package is marked as mandatory in the Dev Center dashboard.</span></span> |
| [<span data-ttu-id="5a686-128">Package</span><span class="sxs-lookup"><span data-stu-id="5a686-128">Package</span></span>](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdate.Package) | <span data-ttu-id="5a686-129">Verwenden Sie diese Eigenschaft, um die zugrunde liegenden paketbezogenen Daten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="5a686-129">Use this property to access the underlying package-related data.</span></span> |

<span/>

## <a name="code-examples"></a><span data-ttu-id="5a686-130">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="5a686-130">Code examples</span></span>

<span data-ttu-id="5a686-131">Die folgenden Codebeispiele zeigen, wie Paketupdates in Ihrer App heruntergeladen und installiert werden.</span><span class="sxs-lookup"><span data-stu-id="5a686-131">The following code examples demonstrate how to download and install package updates in your app.</span></span> <span data-ttu-id="5a686-132">In diesem Beispiel wird Folgendes vorausgesetzt:</span><span class="sxs-lookup"><span data-stu-id="5a686-132">These example assume:</span></span>
* <span data-ttu-id="5a686-133">Der Code wird im Kontext einer [Seite](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx) ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5a686-133">The code runs in the context of a [Page](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx).</span></span>
* <span data-ttu-id="5a686-134">Die **Seite** enthält eine [ProgressBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressbar.aspx) mit dem Namen ```downloadProgressBar```, um einen Status für den Downloadvorgang bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="5a686-134">The **Page** contains a [ProgressBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressbar.aspx) named ```downloadProgressBar``` to provide status for the download operation.</span></span>
* <span data-ttu-id="5a686-135">Die Codedatei enthält eine **using**-Anweisung für die Namespaces **Windows.Services.Store**, **Windows.Threading.Tasks** und **Windows.UI.Popups**.</span><span class="sxs-lookup"><span data-stu-id="5a686-135">The code file has a **using** statement for the **Windows.Services.Store**, **Windows.Threading.Tasks**, and **Windows.UI.Popups** namespaces.</span></span>
* <span data-ttu-id="5a686-136">Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="5a686-136">The app is a single-user app that runs only in the context of the user that launched the app.</span></span> <span data-ttu-id="5a686-137">Verwenden Sie für eine [Multi-User-App](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications) die [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User)-Methode, um ein **StoreContext**-Objekt anstelle der [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault)-Methode abzurufen.</span><span class="sxs-lookup"><span data-stu-id="5a686-137">For a [multi-user app](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications), use the [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User) method to get a **StoreContext** object instead of the [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault) method.</span></span>

<span/>

### <a name="download-and-install-all-package-updates"></a><span data-ttu-id="5a686-138">Herunterladen und Installieren aller Paketupdates</span><span class="sxs-lookup"><span data-stu-id="5a686-138">Download and install all package updates</span></span>

<span data-ttu-id="5a686-139">Im folgenden Codebeispiel wird veranschaulicht, wie alle verfügbaren Paketupdates heruntergeladen und installiert werden.</span><span class="sxs-lookup"><span data-stu-id="5a686-139">The following code example demonstrates how to download and install all available package updates.</span></span>  

```csharp
private StoreContext context = null;

public async Task DownloadAndInstallAllUpdatesAsync()
{
    if (context == null)
    {
        context = StoreContext.GetDefault();
    }

    // Get the updates that are available.
    IReadOnlyList<StorePackageUpdate> updates =
        await context.GetAppAndOptionalStorePackageUpdatesAsync();

    if (updates.Count > 0)
    {
        // Alert the user that updates are available and ask for their consent
        // to start the updates.
        MessageDialog dialog = new MessageDialog(
            "Download and install updates now? This may cause the application to exit.", "Download and Install?");
        dialog.Commands.Add(new UICommand("Yes"));
        dialog.Commands.Add(new UICommand("No"));
        IUICommand command = await dialog.ShowAsync();

        if (command.Label.Equals("Yes", StringComparison.CurrentCultureIgnoreCase))
        {
            // Download and install the updates.
            IAsyncOperationWithProgress<StorePackageUpdateResult, StorePackageUpdateStatus> downloadOperation =
                context.RequestDownloadAndInstallStorePackageUpdatesAsync(updates);

            // The Progress async method is called one time for each step in the download
            // and installation process for each package in this request.
            downloadOperation.Progress = async (asyncInfo, progress) =>
            {
                await this.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,
                () =>
                {
                    downloadProgressBar.Value = progress.PackageDownloadProgress;
                });
            };

            StorePackageUpdateResult result = await downloadOperation.AsTask();
        }
    }
}
```

### <a name="handle-mandatory-package-updates"></a><span data-ttu-id="5a686-140">Behandeln von obligatorischen Paketupdates</span><span class="sxs-lookup"><span data-stu-id="5a686-140">Handle mandatory package updates</span></span>

<span data-ttu-id="5a686-141">Im folgenden Codebeispiel, das sich vom vorherigen Beispiel ableitet, wird veranschaulicht, wie Sie ermitteln, ob Updatepakete [im Windows Dev Center-Dashboard als obligatorisch gekennzeichnet](#mandatory-dashboard) wurden.</span><span class="sxs-lookup"><span data-stu-id="5a686-141">The following code example builds off the previous example, and demonstrates how to determine whether any update packages have been [marked as mandatory on the Windows Dev Center dashboard](#mandatory-dashboard).</span></span> <span data-ttu-id="5a686-142">In der Regel sollten Sie Ihre App-Funktionen kontrolliert für den Benutzer herabstufen, wenn ein obligatorisches Paketupdate nicht erfolgreich heruntergeladen oder installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="5a686-142">Typically, you should downgrade your app experience gracefully for the user if a mandatory package update does not successfully download or install.</span></span>

```csharp
private StoreContext context = null;

// Downloads and installs package updates in separate steps.
public async Task DownloadAndInstallAllUpdatesAsync()
{
    if (context == null)
    {
        context = StoreContext.GetDefault();
    }  
    // Get the updates that are available.
    IReadOnlyList<StorePackageUpdate> updates =
        await context.GetAppAndOptionalStorePackageUpdatesAsync();

    if (updates.Count != 0)
    {
        // Download the packages.
        bool downloaded = await DownloadPackageUpdatesAsync(updates);

        if (downloaded)
        {
            // Install the packages.
            await InstallPackageUpdatesAsync(updates);
        }
    }
}

// Helper method for downloading package updates.
private async Task<bool> DownloadPackageUpdatesAsync(IEnumerable<StorePackageUpdate> updates)
{
    bool downloadedSuccessfully = false;

    IAsyncOperationWithProgress<StorePackageUpdateResult, StorePackageUpdateStatus> downloadOperation =
        this.context.RequestDownloadStorePackageUpdatesAsync(updates);

    // The Progress async method is called one time for each step in the download process for each
    // package in this request.
    downloadOperation.Progress = async (asyncInfo, progress) =>
    {
        await this.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,
        () =>
        {
            downloadProgressBar.Value = progress.PackageDownloadProgress;
        });
    };

    StorePackageUpdateResult result = await downloadOperation.AsTask();

    switch (result.OverallState)
    {
        case StorePackageUpdateState.Completed:
            downloadedSuccessfully = true;
            break;
        default:
            // Get the failed updates.
            var failedUpdates = result.StorePackageUpdateStatuses.Where(
                status => status.PackageUpdateState != StorePackageUpdateState.Completed);

            // See if any failed updates were mandatory
            if (updates.Any(u => u.Mandatory && failedUpdates.Any(
                failed => failed.PackageFamilyName == u.Package.Id.FamilyName)))
            {
                // At least one of the updates is mandatory. Perform whatever actions you
                // want to take for your app: for example, notify the user and disable
                // features in your app.
                HandleMandatoryPackageError();
            }
            break;
    }

    return downloadedSuccessfully;
}

// Helper method for installing package updates.
private async Task InstallPackageUpdatesAsync(IEnumerable<StorePackageUpdate> updates)
{
    IAsyncOperationWithProgress<StorePackageUpdateResult, StorePackageUpdateStatus> installOperation =
        this.context.RequestDownloadAndInstallStorePackageUpdatesAsync(updates);

    // The package updates were already downloaded separately, so this method skips the download
    // operatation and only installs the updates; no download progress notifications are provided.
    StorePackageUpdateResult result = await installOperation.AsTask();

    switch (result.OverallState)
    {
        case StorePackageUpdateState.Completed:
            break;
        default:
            // Get the failed updates.
            var failedUpdates = result.StorePackageUpdateStatuses.Where(
                status => status.PackageUpdateState != StorePackageUpdateState.Completed);

            // See if any failed updates were mandatory
            if (updates.Any(u => u.Mandatory && failedUpdates.Any(failed => failed.PackageFamilyName == u.Package.Id.FamilyName)))
            {
                // At least one of the updates is mandatory, so tell the user.
                HandleMandatoryPackageError();
            }
            break;
    }
}

// Helper method for handling the scenario where a mandatory package update fails to
// download or install. Add code to this method to perform whatever actions you want
// to take, such as notifying the user and disabling features in your app.
private void HandleMandatoryPackageError()
{
}
```

### <a name="display-progress-info-for-the-download-and-install"></a><span data-ttu-id="5a686-143">Anzeigen von Statusinformationen für das Herunterladen und Installieren</span><span class="sxs-lookup"><span data-stu-id="5a686-143">Display progress info for the download and install</span></span>

<span data-ttu-id="5a686-144">Wenn Sie **RequestDownloadStorePackageUpdatesAsync** oder **RequestDownloadAndInstallStorePackageUpdatesAsync** aufrufen, können Sie einen [Progress](https://docs.microsoft.com/uwp/api/windows.foundation.iasyncoperationwithprogress-2.progress)-Handler hinzufügen, der einmal für jeden Schrittim Downloadprozess (oder Download und Installation) für die einzelnen Pakete in dieser Anforderung aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="5a686-144">When you call **RequestDownloadStorePackageUpdatesAsync** or **RequestDownloadAndInstallStorePackageUpdatesAsync**, you can assign a [Progress](https://docs.microsoft.com/uwp/api/windows.foundation.iasyncoperationwithprogress-2.progress) handler that is called one time for each step in the download (or download and install) process for each package in this request.</span></span> <span data-ttu-id="5a686-145">Der Handler empfängt ein [StorePackageUpdateStatus](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdatestatus)-Objekt, das Informationen zum Updatepaket enthält, das die Statusbenachrichtigung ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="5a686-145">The handler receives a [StorePackageUpdateStatus](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdatestatus) object that provides info about the update package that raised the progress notification.</span></span> <span data-ttu-id="5a686-146">In den vorherigen Beispielen wird das Feld **PackageDownloadProgress** des **StorePackageUpdateStatus**-Objekts verwendet, um den Fortschritt des Download- und Installationsprozesses anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5a686-146">The previous examples use the **PackageDownloadProgress** field of the **StorePackageUpdateStatus** object to display the progress of the download and install process.</span></span>

<span data-ttu-id="5a686-147">Beachten Sie, dass sich beim Aufruf von **RequestDownloadAndInstallStorePackageUpdatesAsync** zum Herunterladen und Installieren der Paketupdates in einem einzigen Vorgang der Wert des **PackageDownloadProgress**-Felds während des Downloadvorgangs für ein Paket von 0,0 auf 0,8 und dann während der Installation von 0,8 auf 1,0 erhöht.</span><span class="sxs-lookup"><span data-stu-id="5a686-147">Be aware that when you call **RequestDownloadAndInstallStorePackageUpdatesAsync** to download and install package updates in a single operation, the **PackageDownloadProgress** field increases from 0.0 to 0.8 during the download process for a package, and then it increases from 0.8 to 1.0 during the install.</span></span> <span data-ttu-id="5a686-148">Wenn Sie den auf Ihrer benutzerdefinierten Statusanzeige angezeigten Prozentsatz direkt dem Wert des **PackageDownloadProgress**-Felds zuordnen, zeigt die Anzeige daher 80% an, wenn das Paket fertig herunterladen ist, und das Betriebssystem zeigt das Installationsdialogfeld an.</span><span class="sxs-lookup"><span data-stu-id="5a686-148">Therefore, if you map the percentage shown in your custom progress UI directly to the value of the **PackageDownloadProgress** field, your UI will show 80% when the package is finished downloading and the OS displays the installation dialog.</span></span> <span data-ttu-id="5a686-149">Wenn Ihre benutzerdefinierte Statusanzeige 100% anzeigen soll, wenn das Paket heruntergeladen und bereit zum Installieren ist, können Sie den Code so ändern, dass der Statusanzeige 100% zugewiesen werden, wenn das **PackageDownloadProgress**-Feld 0,8 erreicht.</span><span class="sxs-lookup"><span data-stu-id="5a686-149">If you want your custom progress UI to display 100% when the package is downloaded and ready to be installed, you can modify your code to assign 100% to your progress UI when the **PackageDownloadProgress** field reaches 0.8.</span></span>

<span id="mandatory-dashboard" />

## <a name="make-a-package-submission-mandatory-in-the-dev-center-dashboard"></a><span data-ttu-id="5a686-150">Kennzeichnen einer Paketübermittlung als obligatorisch im Dev Center-Dashboard</span><span class="sxs-lookup"><span data-stu-id="5a686-150">Make a package submission mandatory in the Dev Center dashboard</span></span>

<span data-ttu-id="5a686-151">Wenn Sie eine Paketübermittlung für eine App für Windows10 (Version 1607 oder höher) erstellen, können Sie das Paket als obligatorisch kennzeichnen und das Datum/die Uhrzeit angeben, wann es obligatorisch wird.</span><span class="sxs-lookup"><span data-stu-id="5a686-151">When you create a package submission for an app that targets Windows 10, version 1607 or later, you can mark the package as mandatory and the date/time on which it becomes mandatory.</span></span> <span data-ttu-id="5a686-152">Wenn diese Eigenschaft festgelegt wurde und Ihre App mithilfe der oben in diesem Artikel beschriebenen API erkennt, dass das Paketupdate verfügbar ist, kann die App ermitteln, ob das Updatepaket obligatorisch ist, und ihr Verhalten ändern, bis das Update installiert ist (z.B. kann Ihre App Features deaktivieren).</span><span class="sxs-lookup"><span data-stu-id="5a686-152">When this property is set and your app discovers that the package update is available by using the API described earlier in this article, your app can determine whether the update package is mandatory and alter its behavior until the update is installed (for example, your app can disable features).</span></span>

> [!NOTE]
> <span data-ttu-id="5a686-153">Der obligatorische Status eines Pakets wird von Microsoft nicht erzwungen, und das Betriebssystem verfügt über keine Benutzeroberfläche, die den Benutzer darauf hinweist, dass ein erforderliches App-Update installiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="5a686-153">The mandatory status of a package update is not enforced by Microsoft, and the OS does not provide a UI to indicate to users that a mandatory app update must be installed.</span></span> <span data-ttu-id="5a686-154">Entwickler sollten die Einstellung „Obligatorisch” verwenden, um erforderliche App-Updates in ihrem eigenen Code zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="5a686-154">Developers are intended to use the mandatory setting to enforce mandatory app updates in their own code.</span></span>  

<span data-ttu-id="5a686-155">So kennzeichnen Sie eine Paketübermittlung als obligatorisch:</span><span class="sxs-lookup"><span data-stu-id="5a686-155">To mark a package submission as mandatory:</span></span>

1. <span data-ttu-id="5a686-156">Melden Sie sich beim [Dev Center-Dashboard](https://dev.windows.com/overview) an, und navigieren Sie zur Übersichtsseite für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="5a686-156">Sign in to the [Dev Center dashboard](https://dev.windows.com/overview) and navigate to the overview page for your app.</span></span>
2. <span data-ttu-id="5a686-157">Klicken Sie auf den Namen der Übermittlung, die das Paketupdate enthält, das Sie erforderlich machen möchten.</span><span class="sxs-lookup"><span data-stu-id="5a686-157">Click the name of the submission that contains the package update you want to make mandatory.</span></span>
3. <span data-ttu-id="5a686-158">Navigieren Sie zu der **Pakete**-Seite für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="5a686-158">Navigate to the **Packages** page for the submission.</span></span> <span data-ttu-id="5a686-159">Wählen Sie im unteren Bereich der Seite **Dieses Update als obligatorisch kennzeichnen** aus, und wählen Sie dann den Tag und die Uhrzeit aus, wann das Paketupdate obligatorisch wird.</span><span class="sxs-lookup"><span data-stu-id="5a686-159">Near the bottom of this page, select **Make this update mandatory** and then choose the day and time on which the package update becomes mandatory.</span></span> <span data-ttu-id="5a686-160">Diese Option gilt für alle UWP-Pakete in der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="5a686-160">This option applies to all UWP packages in the submission.</span></span>

<span data-ttu-id="5a686-161">Weitere Informationen zum Konfigurieren von Paketen im Dev Center-Dashboard finden Sie unter [Hochladen von App-Paketen](../publish/upload-app-packages.md).</span><span class="sxs-lookup"><span data-stu-id="5a686-161">For more information about configuring packages in the Dev Center dashboard, see [Upload app packages](../publish/upload-app-packages.md).</span></span>

  > [!NOTE]
  > <span data-ttu-id="5a686-162">Wenn Sie ein [Flight-Paket](../publish/package-flights.md) erstellen, können Sie die Pakete mit einer ähnlichen Benutzeroberfläche auf der **Pakete**-Seite für das Test-Flight als obligatorisch kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="5a686-162">If you create a [package flight](../publish/package-flights.md), you can mark the packages as mandatory using a similar UI on the **Packages** page for the flight.</span></span> <span data-ttu-id="5a686-163">In diesem Fall gilt das obligatorische Paketupdate nur für die Kunden, die Teil der Flight-Gruppe sind.</span><span class="sxs-lookup"><span data-stu-id="5a686-163">In this case, the mandatory package update applies only to the customers who are part of the flight group.</span></span>
