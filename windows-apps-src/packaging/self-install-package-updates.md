---
author: mcleanbyron
ms.assetid: 414ACC73-2A72-465C-BD15-1B51CB2334F2
title: Herunterladen und Installieren von Paketupdates aus dem Store
description: Erfahren Sie, wie Sie Pakete im Dev Center-Dashboard als obligatorisch kennzeichnen und Code in Ihrer App zum Herunterladen und Installieren von Paketupdates schreiben.
ms.author: mcleans
ms.date: 04/04/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 39b3ba05b06b6d484804999a935accc7223b5c60
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4540972"
---
# <a name="download-and-install-package-updates-from-the-store"></a><span data-ttu-id="89b65-104">Herunterladen und Installieren von Paketupdates aus dem Store</span><span class="sxs-lookup"><span data-stu-id="89b65-104">Download and install package updates from the Store</span></span>

<span data-ttu-id="89b65-105">Ab Windows10 (Version 1607) können Sie Methoden der [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Klasse im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace verwenden, um programmgesteuert nach Paketupdates für die aktuelle App im Microsoft Store zu suchen und diese herunterzuladen und zu installieren.</span><span class="sxs-lookup"><span data-stu-id="89b65-105">Starting in Windows 10, version 1607, you can use methods of the [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext) class in the [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) namespace to programmatically check for package updates for the current app from the Microsoft Store, and download and install the updated packages.</span></span> <span data-ttu-id="89b65-106">Sie können auch Abfragen für Pakete ausführen, die im Windows Dev Center-Dashboard als obligatorisch gekennzeichnet wurden, und Funktionen in Ihrer App deaktivieren, bis das erforderliche Update installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="89b65-106">You can also query for packages that you have marked as mandatory on the Windows Dev Center dashboard and disable functionality in your app until the mandatory update is installed.</span></span>

<span data-ttu-id="89b65-107">Mithilfe von zusätzlichen [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Methoden, die in Version 1803 von Windows10 eingeführt wurden, können Sie Paketupdates im Hintergrund herunterladen und installieren (ohne dem Benutzer eine Benachrichtigung anzuzeigen), ein [optionales Paket](optional-packages.md) deinstallieren und Informationen zu Paketen im Download und zur Installationswarteschlange für Ihre App erhalten.</span><span class="sxs-lookup"><span data-stu-id="89b65-107">Additional [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext) methods introduced in Windows 10, version 1803 enable you to download and install package updates silently (without displaying a notification UI to the user), uninstall an [optional package](optional-packages.md), and get info about packages in the download and install queue for your app.</span></span>

<span data-ttu-id="89b65-108">Mithilfe dieser Features können Sie Ihre Benutzerbasis automatisch mit der neuesten Version Ihrer App, optionalen Paketen und verwandten Diensten im Store auf dem neuesten Stand halten.</span><span class="sxs-lookup"><span data-stu-id="89b65-108">These features help you automatically keep your user base up to date with the latest version of your app, optional packages, and related services in the Store.</span></span>

## <a name="download-and-install-package-updates-with-the-users-permission"></a><span data-ttu-id="89b65-109">Herunterladen und Installieren von Paketupdates mit Zustimmung des Benutzers</span><span class="sxs-lookup"><span data-stu-id="89b65-109">Download and install package updates with the user's permission</span></span>

<span data-ttu-id="89b65-110">In diesem Codebeispiel wird veranschaulicht, wie Sie die [GetAppAndOptionalStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getappandoptionalstorepackageupdatesasync)-Methode verwenden, um alle verfügbaren Updates im Store zu ermitteln und dann die [RequestDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadandinstallstorepackageupdatesasync)-Methode aufzurufen, um die Updates herunterzuladen und zu installieren.</span><span class="sxs-lookup"><span data-stu-id="89b65-110">This code example demonstrates how to use the [GetAppAndOptionalStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getappandoptionalstorepackageupdatesasync) method to discover all available package updates from the Store and then call the [RequestDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadandinstallstorepackageupdatesasync) method to download and install the updates.</span></span> <span data-ttu-id="89b65-111">Bei Verwendung dieser Methode zum Herunterladen und Installieren von Updates zeigt das Betriebssystem ein Dialogfeld an, in dem die Berechtigung des Benutzers vor dem Herunterladen der Updates angefragt wird.</span><span class="sxs-lookup"><span data-stu-id="89b65-111">When using this method to download and install updates, the OS displays a dialog that asks the user's permission before downloading the updates.</span></span>

> [!NOTE]
> <span data-ttu-id="89b65-112">Diese Methoden unterstützen erforderliche [optionale Paketen](optional-packages.md) für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="89b65-112">These methods support required and [optional packages](optional-packages.md) for your app.</span></span> <span data-ttu-id="89b65-113">Optionale Pakete sind nützlich für herunterladbare Inhalte (DLC)-Add-Ons, da große Apps so im Hinblick auf Größenbeschränkungen geteilt werden, oder auch, um zusätzliche Inhalte getrennt von der Haupt-App zu liefern.</span><span class="sxs-lookup"><span data-stu-id="89b65-113">Optional packages are useful for downloadable content (DLC) add-ons, dividing your large app for size constraints, or for shipping additional content separate from your core app.</span></span> <span data-ttu-id="89b65-114">Informationen zum Erhalt einer Berechtigung, eine App in den Store zu übermitteln, die optionale Pakete (einschließlich DLC-Add-Ons) verwendet, finden Sie unter [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support).</span><span class="sxs-lookup"><span data-stu-id="89b65-114">To get permission to submit an app that uses optional packages (including DLC add-ons) to the Store, see [Windows developer support](https://developer.microsoft.com/windows/support).</span></span>

<span data-ttu-id="89b65-115">In diesem Codebeispiel wird von Folgendem ausgegangen:</span><span class="sxs-lookup"><span data-stu-id="89b65-115">This code example assumes:</span></span>

* <span data-ttu-id="89b65-116">Der Code wird im Kontext einer [Seite](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx) ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="89b65-116">The code runs in the context of a [Page](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx).</span></span>
* <span data-ttu-id="89b65-117">Die **Seite** enthält eine [ProgressBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressbar.aspx) mit dem Namen ```downloadProgressBar```, um einen Status für den Downloadvorgang bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="89b65-117">The **Page** contains a [ProgressBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressbar.aspx) named ```downloadProgressBar``` to provide status for the download operation.</span></span>
* <span data-ttu-id="89b65-118">Die Codedatei enthält eine **using**-Anweisung für die Namespaces **Windows.Services.Store**, **Windows.Threading.Tasks** und **Windows.UI.Popups**.</span><span class="sxs-lookup"><span data-stu-id="89b65-118">The code file has a **using** statement for the **Windows.Services.Store**, **Windows.Threading.Tasks**, and **Windows.UI.Popups** namespaces.</span></span>
* <span data-ttu-id="89b65-119">Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="89b65-119">The app is a single-user app that runs only in the context of the user that launched the app.</span></span> <span data-ttu-id="89b65-120">Verwenden Sie für eine [Multi-User-App](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications) die [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User)-Methode, um ein **StoreContext**-Objekt anstelle der [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault)-Methode abzurufen.</span><span class="sxs-lookup"><span data-stu-id="89b65-120">For a [multi-user app](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications), use the [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User) method to get a **StoreContext** object instead of the [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault) method.</span></span>

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

> [!NOTE]
> <span data-ttu-id="89b65-121">Verwenden Sie die [RequestDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadstorepackageupdatesasync)-Methode, um die verfügbare Paketupdates nur herunterzuladen (jedoch nicht zu installieren).</span><span class="sxs-lookup"><span data-stu-id="89b65-121">To only download (but not install) the available package updates, use the [RequestDownloadStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadstorepackageupdatesasync) method.</span></span>

### <a name="display-download-and-install-progress-info"></a><span data-ttu-id="89b65-122">Anzeigen von Statusinformationen für das Herunterladen und Installieren</span><span class="sxs-lookup"><span data-stu-id="89b65-122">Display download and install progress info</span></span>

<span data-ttu-id="89b65-123">Wenn Sie die [RequestDownloadStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadstorepackageupdatesasync)-Methode oder [RequestDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadandinstallstorepackageupdatesasync)-Methode aufrufen, können Sie einen [Progress](https://docs.microsoft.com/uwp/api/windows.foundation.iasyncoperationwithprogress-2.progress)-Handler hinzufügen, der einmal für jeden Schrittim Downloadprozess (oder Download und Installation) für die einzelnen Pakete in dieser Anforderung aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="89b65-123">When you call the [RequestDownloadStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadstorepackageupdatesasync) or [RequestDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestdownloadandinstallstorepackageupdatesasync) method, you can assign a [Progress](https://docs.microsoft.com/uwp/api/windows.foundation.iasyncoperationwithprogress-2.progress) handler that is called one time for each step in the download (or download and install) process for each package in this request.</span></span> <span data-ttu-id="89b65-124">Der Handler empfängt ein [StorePackageUpdateStatus](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdatestatus)-Objekt, das Informationen zum Updatepaket enthält, das die Statusbenachrichtigung ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="89b65-124">The handler receives a [StorePackageUpdateStatus](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdatestatus) object that provides info about the update package that raised the progress notification.</span></span> <span data-ttu-id="89b65-125">Im vorherigen Beispiel wird das Feld **PackageDownloadProgress** des **StorePackageUpdateStatus**-Objekts verwendet, um den Fortschritt des Download- und Installationsprozesses anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="89b65-125">The previous example uses the **PackageDownloadProgress** field of the **StorePackageUpdateStatus** object to display the progress of the download and install process.</span></span>

<span data-ttu-id="89b65-126">Beachten Sie, dass sich beim Aufruf von **RequestDownloadAndInstallStorePackageUpdatesAsync** zum Herunterladen und Installieren der Paketupdates in einem einzigen Vorgang der Wert des **PackageDownloadProgress**-Felds während des Downloadvorgangs für ein Paket von 0,0 auf 0,8 und dann während der Installation von 0,8 auf 1,0 erhöht.</span><span class="sxs-lookup"><span data-stu-id="89b65-126">Be aware that when you call **RequestDownloadAndInstallStorePackageUpdatesAsync** to download and install package updates in a single operation, the **PackageDownloadProgress** field increases from 0.0 to 0.8 during the download process for a package, and then it increases from 0.8 to 1.0 during the install.</span></span> <span data-ttu-id="89b65-127">Wenn Sie den auf Ihrer benutzerdefinierten Statusanzeige angezeigten Prozentsatz direkt dem Wert des **PackageDownloadProgress**-Felds zuordnen, zeigt die Anzeige daher 80% an, wenn das Paket fertig herunterladen ist, und das Betriebssystem zeigt das Installationsdialogfeld an.</span><span class="sxs-lookup"><span data-stu-id="89b65-127">Therefore, if you map the percentage shown in your custom progress UI directly to the value of the **PackageDownloadProgress** field, your UI will show 80% when the package is finished downloading and the OS displays the installation dialog.</span></span> <span data-ttu-id="89b65-128">Wenn Ihre benutzerdefinierte Statusanzeige 100% anzeigen soll, wenn das Paket heruntergeladen und bereit zum Installieren ist, können Sie den Code so ändern, dass der Statusanzeige 100% zugewiesen werden, wenn das **PackageDownloadProgress**-Feld 0,8 erreicht.</span><span class="sxs-lookup"><span data-stu-id="89b65-128">If you want your custom progress UI to display 100% when the package is downloaded and ready to be installed, you can modify your code to assign 100% to your progress UI when the **PackageDownloadProgress** field reaches 0.8.</span></span>

## <a name="download-and-install-package-updates-silently"></a><span data-ttu-id="89b65-129">Herunterladen und Installieren aller Paketupdates im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="89b65-129">Download and install package updates silently</span></span>

<span data-ttu-id="89b65-130">Ab Windows10, Version 1803, können Sie die Methoden [TrySilentDownloadStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.trysilentdownloadstorepackageupdatesasync) und [TrySilentDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.trysilentdownloadandinstallstorepackageupdatesasync) verwenden, Paketupdates im Hintergrund herunterzuladen und zu installieren, ohne dem Benutzer eine Benachrichtigung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="89b65-130">Starting in Windows 10, version 1803, you can use the [TrySilentDownloadStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.trysilentdownloadstorepackageupdatesasync) and [TrySilentDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.trysilentdownloadandinstallstorepackageupdatesasync) methods to download and install package updates silently, without displaying a notification UI to the user.</span></span> <span data-ttu-id="89b65-131">Dieser Vorgang wird nur erfolgreich ausgeführt, wenn der Benutzer die Einstellung **Apps automatisch aktualisieren** im Store aktiviert hat und der Benutzer nicht in einem getakteten Netzwerk ist.</span><span class="sxs-lookup"><span data-stu-id="89b65-131">This operation will succeed only if the user has enabled the **Update apps automatically** setting in the Store and the user is not on a metered network.</span></span> <span data-ttu-id="89b65-132">Bevor Sie diese Methoden aufrufen, können Sie zunächst die [CanSilentlyDownloadStorePackageUpdates](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.cansilentlydownloadstorepackageupdates)-Eigenschaft überprüfen, um festzustellen, ob diese Bedingungen derzeit erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="89b65-132">Before calling these methods, you can first check the [CanSilentlyDownloadStorePackageUpdates](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.cansilentlydownloadstorepackageupdates) property to determine whether these conditions are currently met.</span></span>

<span data-ttu-id="89b65-133">In diesem Codebeispiel wird veranschaulicht, wie Sie die [GetAppAndOptionalStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getappandoptionalstorepackageupdatesasync)-Methode verwenden, um alle verfügbaren Paketupdates zu ermitteln und dann die Methoden [TrySilentDownloadStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.trysilentdownloadstorepackageupdatesasync) und [TrySilentDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.trysilentdownloadandinstallstorepackageupdatesasync) zum Herunterladen und Installieren im Hintergrund zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="89b65-133">This code example demonstrates how to use the [GetAppAndOptionalStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getappandoptionalstorepackageupdatesasync) method to discover all available package updates and then call the [TrySilentDownloadStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.trysilentdownloadstorepackageupdatesasync) and [TrySilentDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.trysilentdownloadandinstallstorepackageupdatesasync) methods to download and install the updates silently.</span></span>

<span data-ttu-id="89b65-134">In diesem Codebeispiel wird von Folgendem ausgegangen:</span><span class="sxs-lookup"><span data-stu-id="89b65-134">This code example assumes:</span></span>
* <span data-ttu-id="89b65-135">Die Codedatei enthält eine **using**-Anweisung für die Namespaces **Windows.Services.Store** und **System.Threading.Tasks**.</span><span class="sxs-lookup"><span data-stu-id="89b65-135">The code file has a **using** statement for the **Windows.Services.Store** and  **System.Threading.Tasks** namespaces.</span></span>
* <span data-ttu-id="89b65-136">Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="89b65-136">The app is a single-user app that runs only in the context of the user that launched the app.</span></span> <span data-ttu-id="89b65-137">Verwenden Sie für eine [Multi-User-App](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications) die [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User)-Methode, um ein **StoreContext**-Objekt anstelle der [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault)-Methode abzurufen.</span><span class="sxs-lookup"><span data-stu-id="89b65-137">For a [multi-user app](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications), use the [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User) method to get a **StoreContext** object instead of the [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault) method.</span></span>

> [!NOTE]
> <span data-ttu-id="89b65-138">Die Methoden **IsNowAGoodTimeToRestartApp**, **RetryDownloadAndInstallLater** und **RetryInstallLater**, die in diesem Code aufgerufen werden, sind Platzhaltermethoden, die gemäß den Anforderungen Ihres eigenen App-Designs implementiert werden können.</span><span class="sxs-lookup"><span data-stu-id="89b65-138">The **IsNowAGoodTimeToRestartApp**, **RetryDownloadAndInstallLater**, and **RetryInstallLater** methods called by the code in this example are placeholder methods that are intended to be implemented as needed according to your own app's design.</span></span>

```csharp
private StoreContext context = null;

public async Task DownloadAndInstallAllUpdatesInBackgroundAsync()
{
    if (context == null)
    {
        context = StoreContext.GetDefault();
    }

    // Get the updates that are available.
    IReadOnlyList<StorePackageUpdate> storePackageUpdates =
        await context.GetAppAndOptionalStorePackageUpdatesAsync();

    if (storePackageUpdates.Count > 0)
    {

        if (!context.CanSilentlyDownloadStorePackageUpdates)
        {
            return;
        }

        // Start the silent downloads and wait for the downloads to complete.
        StorePackageUpdateResult downloadResult =
            await context.TrySilentDownloadStorePackageUpdatesAsync(storePackageUpdates);

        switch (downloadResult.OverallState)
        {
            case StorePackageUpdateState.Completed:
                // The download has completed successfully. At this point, confirm whether your app
                // can restart now and then install the updates (for example, you might only install
                // packages silently if your app has been idle for a certain period of time). The
                // IsNowAGoodTimeToRestartApp method is not implemented in this example, you should
                // implement it as needed for your own app.
                if (IsNowAGoodTimeToRestartApp())
                {
                    await InstallUpdate(storePackageUpdates);
                }
                else
                {
                    // Retry/reschedule the installation later. The RetryInstallLater method is not  
                    // implemented in this example, you should implement it as needed for your own app.
                    RetryInstallLater();
                    return;
                }
                break;
            // If the user cancelled the download or you can't perform the download for some other
            // reason (for example, Wi-Fi might have been turned off and the device is now on
            // a metered network) try again later. The RetryDownloadAndInstallLater method is not  
            // implemented in this example, you should implement it as needed for your own app.
            case StorePackageUpdateState.Canceled:
            case StorePackageUpdateState.ErrorLowBattery:
            case StorePackageUpdateState.ErrorWiFiRecommended:
            case StorePackageUpdateState.ErrorWiFiRequired:
            case StorePackageUpdateState.OtherError:
                RetryDownloadAndInstallLater();
                return;
            default:
                break;
        }
    }
}

private async Task InstallUpdate(IReadOnlyList<StorePackageUpdate> storePackageUpdates)
{
    // Start the silent installation of the packages. Because the packages have already
    // been downloaded in the previous method, the following line of code just installs
    // the downloaded packages.
    StorePackageUpdateResult downloadResult =
        await context.TrySilentDownloadAndInstallStorePackageUpdatesAsync(storePackageUpdates);

    switch (downloadResult.OverallState)
    {
        // If the user cancelled the installation or you can't perform the installation  
        // for some other reason, try again later. The RetryInstallLater method is not  
        // implemented in this example, you should implement it as needed for your own app.
        case StorePackageUpdateState.Canceled:
        case StorePackageUpdateState.ErrorLowBattery:
        case StorePackageUpdateState.OtherError:
            RetryInstallLater();
            return;
        default:
            break;
    }
}
```

## <a name="mandatory-package-updates"></a><span data-ttu-id="89b65-139">Obligatorische Paketupdates</span><span class="sxs-lookup"><span data-stu-id="89b65-139">Mandatory package updates</span></span>

<span data-ttu-id="89b65-140">Wenn Sie eine Paketübermittlung für eine App für Windows10 (Version 1607 oder höher) erstellen, können Sie das [Paket als obligatorisch kennzeichnen](../publish/upload-app-packages.md#mandatory-update) und das Datum und die Uhrzeit angeben, wann es obligatorisch wird.</span><span class="sxs-lookup"><span data-stu-id="89b65-140">When you create a package submission for an app that targets Windows 10, version 1607 or later, you can [mark the package as mandatory](../publish/upload-app-packages.md#mandatory-update) and the date and time on which it becomes mandatory.</span></span> <span data-ttu-id="89b65-141">Wenn diese Eigenschaft festgelegt wurde und Ihre App erkennt, dass das Paketupdate verfügbar ist, kann die App ermitteln, ob das Updatepaket obligatorisch ist, und ihr Verhalten ändern, bis das Update installiert ist (z.B. kann Ihre App Features deaktivieren).</span><span class="sxs-lookup"><span data-stu-id="89b65-141">When this property is set and your app discovers that the package update is available, your app can determine whether the update package is mandatory and alter its behavior until the update is installed (for example, your app can disable features).</span></span>

> [!NOTE]
> <span data-ttu-id="89b65-142">Der obligatorische Status eines Pakets wird von Microsoft nicht erzwungen, und das Betriebssystem verfügt über keine Benutzeroberfläche, die den Benutzer darauf hinweist, dass ein erforderliches App-Update installiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="89b65-142">The mandatory status of a package update is not enforced by Microsoft, and the OS does not provide a UI to indicate to users that a mandatory app update must be installed.</span></span> <span data-ttu-id="89b65-143">Entwickler sollten die Einstellung „Obligatorisch” verwenden, um erforderliche App-Updates in ihrem eigenen Code zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="89b65-143">Developers are intended to use the mandatory setting to enforce mandatory app updates in their own code.</span></span>  

<span data-ttu-id="89b65-144">So kennzeichnen Sie eine Paketübermittlung als obligatorisch:</span><span class="sxs-lookup"><span data-stu-id="89b65-144">To mark a package submission as mandatory:</span></span>

1. <span data-ttu-id="89b65-145">Melden Sie sich beim [Dev Center-Dashboard](https://dev.windows.com/overview) an, und navigieren Sie zur Übersichtsseite für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="89b65-145">Sign in to the [Dev Center dashboard](https://dev.windows.com/overview) and navigate to the overview page for your app.</span></span>
2. <span data-ttu-id="89b65-146">Klicken Sie auf den Namen der Übermittlung, die das Paketupdate enthält, das Sie erforderlich machen möchten.</span><span class="sxs-lookup"><span data-stu-id="89b65-146">Click the name of the submission that contains the package update you want to make mandatory.</span></span>
3. <span data-ttu-id="89b65-147">Navigieren Sie zu der **Pakete**-Seite für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="89b65-147">Navigate to the **Packages** page for the submission.</span></span> <span data-ttu-id="89b65-148">Wählen Sie im unteren Bereich der Seite **Dieses Update als obligatorisch kennzeichnen** aus, und wählen Sie dann den Tag und die Uhrzeit aus, wann das Paketupdate obligatorisch wird.</span><span class="sxs-lookup"><span data-stu-id="89b65-148">Near the bottom of this page, select **Make this update mandatory** and then choose the day and time on which the package update becomes mandatory.</span></span> <span data-ttu-id="89b65-149">Diese Option gilt für alle UWP-Pakete in der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="89b65-149">This option applies to all UWP packages in the submission.</span></span>

<span data-ttu-id="89b65-150">Weitere Informationen finden Sie unter [Hochladen von App-Paketen](../publish/upload-app-packages.md).</span><span class="sxs-lookup"><span data-stu-id="89b65-150">For more information, see [Upload app packages](../publish/upload-app-packages.md).</span></span>

> [!NOTE]
> <span data-ttu-id="89b65-151">Wenn Sie ein [Flight-Paket](../publish/package-flights.md) erstellen, können Sie die Pakete mit einer ähnlichen Benutzeroberfläche auf der **Pakete**-Seite für das Test-Flight als obligatorisch kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="89b65-151">If you create a [package flight](../publish/package-flights.md), you can mark the packages as mandatory using a similar UI on the **Packages** page for the flight.</span></span> <span data-ttu-id="89b65-152">In diesem Fall gilt das obligatorische Paketupdate nur für die Kunden, die Teil der Flight-Gruppe sind.</span><span class="sxs-lookup"><span data-stu-id="89b65-152">In this case, the mandatory package update applies only to the customers who are part of the flight group.</span></span>

### <a name="code-example-for-mandatory-packages"></a><span data-ttu-id="89b65-153">Codebeispiel für obligatorische Pakete</span><span class="sxs-lookup"><span data-stu-id="89b65-153">Code example for mandatory packages</span></span>

<span data-ttu-id="89b65-154">Im folgenden Codebeispiel wird veranschaulicht, wie Sie feststellen, ob Updatepakete verpflichtend sind.</span><span class="sxs-lookup"><span data-stu-id="89b65-154">The following code example demonstrates how to determine whether any update packages are mandatory.</span></span> <span data-ttu-id="89b65-155">In der Regel sollten Sie Ihre App-Funktionen kontrolliert für den Benutzer herabstufen, wenn ein obligatorisches Paketupdate nicht erfolgreich heruntergeladen oder installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="89b65-155">Typically, you should downgrade your app experience gracefully for the user if a mandatory package update does not successfully download or install.</span></span>

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

## <a name="uninstall-optional-packages"></a><span data-ttu-id="89b65-156">Deinstallieren optionaler Pakete</span><span class="sxs-lookup"><span data-stu-id="89b65-156">Uninstall optional packages</span></span>

<span data-ttu-id="89b65-157">Ab Windows10, Version 1803, können Sie die Methoden [RequestUninstallStorePackageAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestuninstallstorepackageasync) oder [RequestUninstallStorePackageByStoreIdAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestuninstallstorepackagebystoreidasync) verwenden, um ein [Optionales Paket](optional-packages.md) (einschließlich eines DLC-Pakets) für die aktuelle App zu deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="89b65-157">Starting in Windows 10, version 1803, you can use the [RequestUninstallStorePackageAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestuninstallstorepackageasync) or [RequestUninstallStorePackageByStoreIdAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestuninstallstorepackagebystoreidasync) methods to uninstall an [optional package](optional-packages.md) (including a DLC package) for the current app.</span></span> <span data-ttu-id="89b65-158">Wenn Sie beispielsweise eine App mit Inhalten haben, die über optionale Pakete installiert wurden, sollten Sie z.B. eine Benutzeroberfläche bereitstellen, die Benutzern ermöglicht, die optionalen Pakete zu deinstallieren, um Speicherplatz freizugeben.</span><span class="sxs-lookup"><span data-stu-id="89b65-158">For example, if you have an app with content that is installed via optional packages, you might want to provide a UI that enables users to uninstall the optional packages to free up disk space.</span></span>

<span data-ttu-id="89b65-159">Das folgende Codebeispiel veranschaulicht, wie Sie die [RequestUninstallStorePackageAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestuninstallstorepackageasync)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="89b65-159">The following code example demonstrates how to call [RequestUninstallStorePackageAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestuninstallstorepackageasync).</span></span> <span data-ttu-id="89b65-160">In diesem Beispiel wird von Folgendem ausgegangen:</span><span class="sxs-lookup"><span data-stu-id="89b65-160">This example assumes:</span></span>
* <span data-ttu-id="89b65-161">Die Codedatei enthält eine **using**-Anweisung für die Namespaces **Windows.Services.Store** und **System.Threading.Tasks**.</span><span class="sxs-lookup"><span data-stu-id="89b65-161">The code file has a **using** statement for the **Windows.Services.Store** and  **System.Threading.Tasks** namespaces.</span></span>
* <span data-ttu-id="89b65-162">Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="89b65-162">The app is a single-user app that runs only in the context of the user that launched the app.</span></span> <span data-ttu-id="89b65-163">Verwenden Sie für eine [Multi-User-App](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications) die [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User)-Methode, um ein **StoreContext**-Objekt anstelle der [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault)-Methode abzurufen.</span><span class="sxs-lookup"><span data-stu-id="89b65-163">For a [multi-user app](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications), use the [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User) method to get a **StoreContext** object instead of the [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault) method.</span></span>

```csharp
public async Task UninstallPackage(Windows.ApplicationModel.Package package)
{
    if (context == null)
    {
        context = StoreContext.GetDefault();
    }

    var storeContext = StoreContext.GetDefault();
    IAsyncOperation<StoreUninstallStorePackageResult> uninstallOperation =
        storeContext.RequestUninstallStorePackageAsync(package);

    // At this point, you can update your app UI to show that the package
    // is installing.

    uninstallOperation.Completed += (asyncInfo, status) =>
    {
        StoreUninstallStorePackageResult result = uninstallOperation.GetResults();
        switch (result.Status)
        {
            case StoreUninstallStorePackageStatus.Succeeded:
                {
                    // Update your app UI to show the package as uninstalled.
                    break;
                }
            default:
                {
                    // Update your app UI to show that the package uninstall failed.
                    break;
                }
        }
    };
}
```

## <a name="get-download-queue-info"></a><span data-ttu-id="89b65-164">Abrufen von Informationen für Downloadwarteschlangen</span><span class="sxs-lookup"><span data-stu-id="89b65-164">Get download queue info</span></span>

<span data-ttu-id="89b65-165">Ab Windows10, Version 1803, können Sie die Methoden [GetAssociatedStoreQueueItemsAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getassociatedstorequeueitemsasync) und [GetStoreQueueItemsAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getstorequeueitemsasync) zum Abrufen von Informationen zu den Paketen verwenden, die sich in der aktuellen Download- und Installationswarteschlange des Store befinden.</span><span class="sxs-lookup"><span data-stu-id="89b65-165">Starting in Windows 10, version 1803, you can use the [GetAssociatedStoreQueueItemsAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getassociatedstorequeueitemsasync) and [GetStoreQueueItemsAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getstorequeueitemsasync) methods to get info about the packages that are in the current download and installation queue from the Store.</span></span> <span data-ttu-id="89b65-166">Diese Methoden sind hilfreich, wenn die App oder das Spiel große optionale Pakete (einschließlich DLCs) unterstützt, deren Download und Installation Stunden oder Tage dauern kann, und Sie möchten problemlos auf den Fall reagieren, wenn ein Kunde Ihre App oder Ihr Spiel vor dem Abschluss des Downloads und der Installation schließt.</span><span class="sxs-lookup"><span data-stu-id="89b65-166">These methods are useful if your app or game supports large optional packages (including DLCs) that can take hours or days to download and install, and you want to gracefully handle the case where a customer closes your app or game before the download and installation process is complete.</span></span> <span data-ttu-id="89b65-167">Wenn der Kunde die App oder das Spiel erneut startet, kann Ihr Code diese Methoden zum Abrufen von Informationen über den Zustand der Pakete verwenden, die noch in der Download- und Installationswarteschlange sind, damit Sie dem Kunden den Status der einzelnen Pakete anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="89b65-167">When the customer starts your app or game again, your code can use these methods to get info about the state of the packages that are still in the download and installation queue so you can display the status of each package to the customer.</span></span>

<span data-ttu-id="89b65-168">Im folgenden Codebeispiel wird veranschaulicht, wie [GetAssociatedStoreQueueItemsAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getassociatedstorequeueitemsasync) zum Abrufen der Liste der aktiven Paketupdates für die aktuelle App sowie der Statusinformationen für die einzelnen Pakete verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="89b65-168">The following code example demonstrates how to call [GetAssociatedStoreQueueItemsAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.getassociatedstorequeueitemsasync) to get the list of in-progress package updates for the current app and retrieve status info for each package.</span></span> <span data-ttu-id="89b65-169">In diesem Beispiel wird von Folgendem ausgegangen:</span><span class="sxs-lookup"><span data-stu-id="89b65-169">This example assumes:</span></span>
* <span data-ttu-id="89b65-170">Die Codedatei enthält eine **using**-Anweisung für die Namespaces **Windows.Services.Store** und **System.Threading.Tasks**.</span><span class="sxs-lookup"><span data-stu-id="89b65-170">The code file has a **using** statement for the **Windows.Services.Store** and  **System.Threading.Tasks** namespaces.</span></span>
* <span data-ttu-id="89b65-171">Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="89b65-171">The app is a single-user app that runs only in the context of the user that launched the app.</span></span> <span data-ttu-id="89b65-172">Verwenden Sie für eine [Multi-User-App](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications) die [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User)-Methode, um ein **StoreContext**-Objekt anstelle der [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault)-Methode abzurufen.</span><span class="sxs-lookup"><span data-stu-id="89b65-172">For a [multi-user app](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications), use the [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.User) method to get a **StoreContext** object instead of the [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.GetDefault) method.</span></span>

> [!NOTE]
> <span data-ttu-id="89b65-173">Die Methoden **MarkUpdateInProgressInUI**, **RemoveItemFromUI**, **MarkInstallCompleteInUI**, **MarkInstallErrorInUI** und **MarkInstallPausedInUI**, die vom Code in diesem Beispiel aufgerufen werden, sind Platzhaltermethoden, die bei Bedarf entsprechend in Ihren eigenen App-Entwurf implementiert werden können.</span><span class="sxs-lookup"><span data-stu-id="89b65-173">The **MarkUpdateInProgressInUI**, **RemoveItemFromUI**, **MarkInstallCompleteInUI**, **MarkInstallErrorInUI**, and **MarkInstallPausedInUI** methods called by the code in this example are placeholder methods that are intended to be implemented as needed according to your own app's design.</span></span>

```csharp
private StoreContext context = null;

private async Task GetQueuedInstallItemsAndBuildInitialStoreUI()
{
    if (context == null)
    {
        context = StoreContext.GetDefault();
    }

    // Get the Store packages in the install queue.
    IReadOnlyList<StoreQueueItem> storeUpdateItems = await context.GetAssociatedStoreQueueItemsAsync();

    foreach (StoreQueueItem storeItem in storeUpdateItems)
    {
        // In this example we only care about package updates.
        if (storeItem.InstallKind != StoreQueueItemKind.Update)
            continue;

        StoreQueueItemStatus currentStatus = storeItem.GetCurrentStatus();
        StoreQueueItemState installState = currentStatus.PackageInstallState;
        StoreQueueItemExtendedState extendedInstallState =
            currentStatus.PackageInstallExtendedState;

        // Handle the StatusChanged event to display current status to the customer.
        storeItem.StatusChanged += StoreItem_StatusChanged;

        switch (installState)
        {
            // Download and install are still in progress, so update the status for this  
            // item and provide the extended state info. The following methods are not
            // implemented in this example; you should implement them as needed for your
            // app's UI.
            case StoreQueueItemState.Active:
                MarkUpdateInProgressInUI(storeItem, extendedInstallState);
                break;
            case StoreQueueItemState.Canceled:
                RemoveItemFromUI(storeItem);
                break;
            case StoreQueueItemState.Completed:
                MarkInstallCompleteInUI(storeItem);
                break;
            case StoreQueueItemState.Error:
                MarkInstallErrorInUI(storeItem);
                break;
            case StoreQueueItemState.Paused:
                MarkInstallPausedInUI(storeItem, installState, extendedInstallState);
                break;
        }
    }
}

private void StoreItem_StatusChanged(StoreQueueItem sender, object args)
{
    StoreQueueItemStatus currentStatus = sender.GetCurrentStatus();
    StoreQueueItemState installState = currentStatus.PackageInstallState;
    StoreQueueItemExtendedState extendedInstallState = currentStatus.PackageInstallExtendedState;

    switch (installState)
    {
        // Download and install are still in progress, so update the status for this  
        // item and provide the extended state info. The following methods are not
        // implemented in this example; you should implement them as needed for your
        // app's UI.
        case StoreQueueItemState.Active:
            MarkUpdateInProgressInUI(sender, extendedInstallState);
            break;
        case StoreQueueItemState.Canceled:
            RemoveItemFromUI(sender);
            break;
        case StoreQueueItemState.Completed:
            MarkInstallCompleteInUI(sender);
            break;
        case StoreQueueItemState.Error:
            MarkInstallErrorInUI(sender);
            break;
        case StoreQueueItemState.Paused:
            MarkInstallPausedInUI(sender, installState, extendedInstallState);
            break;
    }
}
```

## <a name="related-topics"></a><span data-ttu-id="89b65-174">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="89b65-174">Related topics</span></span>

* [<span data-ttu-id="89b65-175">Optionale Pakete und die Erstellung zugehöriger Sets</span><span class="sxs-lookup"><span data-stu-id="89b65-175">Optional packages and related set authoring</span></span>](optional-packages.md)
