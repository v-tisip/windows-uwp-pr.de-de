---
author: mcleanbyron
ms.assetid: 414ACC73-2A72-465C-BD15-1B51CB2334F2
title: "Herunterladen und Installieren von Paketupdates für Ihre App"
description: Erfahren Sie, wie Sie Pakete im Dev Center-Dashboard als obligatorisch kennzeichnen und Code in Ihrer App zum Herunterladen und Installieren von Paketupdates schreiben.
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: ffd1af9475791b8190f9364d85f7a7fa23548856
ms.lasthandoff: 02/07/2017

---
# <a name="download-and-install-package-updates-for-your-app"></a>Herunterladen und Installieren von Paketupdates für Ihre App

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \].

Ab Windows 10 (Version 1607) können Sie eine API im Namespace [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx) verwenden, um programmgesteuert nach Paketupdates für die aktuelle App zu suchen und diese herunterzuladen und zu installieren. Sie können auch Abfragen für Pakete ausführen, die [im Windows Dev Center-Dashboard als obligatorisch gekennzeichnet](#mandatory-dashboard) wurden, und Funktionen in Ihrer App deaktivieren, bis das erforderliche Update installiert wurde.

Mithilfe dieser Features können Sie Benutzer automatisch mit der neuesten Version Ihrer App und der zugehörigen Dienste auf dem neuesten Stand halten.

## <a name="api-overview"></a>API-Übersicht

In Apps für Windows 10 (ab Version 1607) können Sie die folgenden Methoden der [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Klasse verwenden, um Paketupdates herunterzuladen und zu installieren.

|  Methode  |  Beschreibung  |
|----------|---------------|
| [GetAppAndOptionalStorePackageUpdatesAsync](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.getappandoptionalstorepackageupdatesasync.aspx) | Rufen Sie diese Methode auf, um die Liste der verfügbaren Paketupdates abzurufen.<br/><br/>**Wichtig**&nbsp;&nbsp;Es besteht eine Wartezeit von bis zu einem Tag zwischen dem Zeitpunkt, an dem ein Paket den Zertifizierungsprozess durchläuft, und dem Zeitpunkt, an dem die [GetAppAndOptionalStorePackageUpdatesAsync](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.getappandoptionalstorepackageupdatesasync.aspx)-Methode erkennt, dass das Paketupdate für die App zur Verfügung steht. |
| [RequestDownloadStorePackageUpdatesAsync](https://msdn.microsoft.com/library/windows/apps/mt706586.aspx) | Rufen Sie diese Methode auf, um die verfügbaren Paketupdates herunterzuladen (jedoch nicht zu installieren). Unter diesem Betriebssystem wird ein Dialogfeld angezeigt, in dem der Benutzer dem Herunterladen der Updates zustimmen muss. |
| [RequestDownloadAndInstallStorePackageUpdatesAsync](https://msdn.microsoft.com/library/windows/apps/mt706585.aspx) | Rufen Sie diese Methode auf, um die verfügbaren Paketupdates herunterzuladen und zu installieren. Unter dem Betriebssystem werden Dialogfelder angezeigt, in denen der Benutzer dem Herunterladen und Installieren der Updates zustimmen muss. Wenn Sie die Paketupdates durch Aufrufen von [RequestDownloadStorePackageUpdatesAsync](https://msdn.microsoft.com/library/windows/apps/mt706586.aspx) bereits heruntergeladen haben, überspringt diese Methode den Downloadvorgang und installiert nur die Updates.  |

<span/>

Diese Methoden verwenden [StorePackageUpdate](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storepackageupdate.aspx)-Objekte, die den verfügbaren Updatepaketen entsprechen. Verwenden Sie die folgenden [StorePackageUpdate](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storepackageupdate.aspx)-Eigenschaften zum Abrufen von Informationen über ein Updatepaket.

|  Eigenschaft  |  Beschreibung  |
|----------|---------------|
| [Mandatory](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storepackageupdate.mandatory.aspx) | Verwenden Sie diese Eigenschaft, um zu ermitteln, ob das Paket im Dev Center-Dashboard als obligatorisch gekennzeichnet ist. |
| [Package](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storepackageupdate.package.aspx) | Verwenden Sie diese Eigenschaft, um die zugrunde liegenden paketbezogenen Daten abzurufen. |

<span/>

## <a name="code-examples"></a>Codebeispiele

Die folgenden Codebeispiele zeigen, wie Paketupdates in Ihrer App heruntergeladen und installiert werden. In diesem Beispiel wird Folgendes vorausgesetzt:
* Der Code wird im Kontext einer [Seite](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx) ausgeführt.
* Die **Seite** enthält eine [ProgressBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressbar.aspx) mit dem Namen ```downloadProgressBar```, um einen Status für den Downloadvorgang bereitzustellen.
* Die Codedatei enthält eine **using**-Anweisung für den Namespace [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx).
* Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat. Verwenden Sie für eine [Multi-User-App](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications) die [GetForUser](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.getforuser.aspx)-Methode, um ein [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Objekt anstelle der [GetDefault](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.getdefault.aspx)-Methode abzurufen.

<span/>

### <a name="download-and-install-all-package-updates"></a>Herunterladen und Installieren aller Paketupdates

Im folgenden Codebeispiel wird veranschaulicht, wie alle verfügbaren Paketupdates heruntergeladen und installiert werden.  

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

### <a name="handle-mandatory-package-updates"></a>Behandeln von obligatorischen Paketupdates

Im folgenden Codebeispiel, das sich vom vorherigen Beispiel ableitet, wird veranschaulicht, wie Sie ermitteln, ob Updatepakete [im Windows Dev Center-Dashboard als obligatorisch gekennzeichnet](#mandatory-dashboard) wurden. In der Regel sollten Sie Ihre App-Funktionen kontrolliert für den Benutzer herabstufen, wenn ein obligatorisches Paketupdate nicht erfolgreich heruntergeladen oder installiert werden kann.

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

<span id="mandatory-dashboard" />
## <a name="make-a-package-submission-mandatory-in-the-dev-center-dashboard"></a>Kennzeichnen einer Paketübermittlung als obligatorisch im Dev Center-Dashboard

Wenn Sie eine Paketübermittlung für eine App für Windows 10 (Version 1607 oder höher) erstellen, können Sie das Paket als obligatorisch kennzeichnen und das Datum/die Uhrzeit angeben, wann es obligatorisch wird. Wenn diese Eigenschaft festgelegt wurde und Ihre App mithilfe der oben in diesem Artikel beschriebenen API erkennt, dass das Paketupdate verfügbar ist, kann die App ermitteln, ob das Updatepaket obligatorisch ist, und ihr Verhalten ändern, bis das Update installiert ist (z. B. kann Ihre App Features deaktivieren).

>**Hinweis**&nbsp;&nbsp;Der obligatorische Status eines Pakets wird von Microsoft nicht erzwungen, und das Betriebssystem verfügt über keine Benutzeroberfläche, die den Benutzer darauf hinweist, dass ein erforderliches App-Update installiert werden muss. Entwickler sollten die Einstellung „Obligatorisch” verwenden, um erforderliche App-Updates in ihrem eigenen Code zu erzwingen.  

So kennzeichnen Sie eine Paketübermittlung als obligatorisch:

1. Melden Sie sich beim [Dev Center-Dashboard](https://dev.windows.com/overview) an, und navigieren Sie zur Übersichtsseite für Ihre App.
2. Klicken Sie auf den Namen der Übermittlung, die das Paketupdate enthält, das Sie erforderlich machen möchten.
3. Navigieren Sie zu der **Pakete**-Seite für die Übermittlung. Wählen Sie im unteren Bereich der Seite **Dieses Update als obligatorisch kennzeichnen** aus, und wählen Sie dann den Tag und die Uhrzeit aus, wann das Paketupdate obligatorisch wird. Diese Option gilt für alle UWP-Pakete in der Übermittlung.

Weitere Informationen zum Konfigurieren von Paketen im Dev Center-Dashboard finden Sie unter [Hochladen von App-Paketen](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages).

  >**Hinweis**&nbsp;&nbsp;Wenn Sie ein [Flight-Paket](https://msdn.microsoft.com/windows/uwp/publish/package-flights) erstellen, können Sie die Pakete mit einer ähnlichen Benutzeroberfläche auf der **Pakete**-Seite für das Flight als obligatorisch kennzeichnen. In diesem Fall gilt das obligatorische Paketupdate nur für die Kunden, die Teil der Flight-Gruppe sind.

