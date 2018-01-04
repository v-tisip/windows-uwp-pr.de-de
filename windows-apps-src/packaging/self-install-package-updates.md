---
author: mcleanbyron
ms.assetid: 414ACC73-2A72-465C-BD15-1B51CB2334F2
title: "Herunterladen und Installieren von Paketupdates für Ihre App"
description: Erfahren Sie, wie Sie Pakete im Dev Center-Dashboard als obligatorisch kennzeichnen und Code in Ihrer App zum Herunterladen und Installieren von Paketupdates schreiben.
ms.author: mcleans
ms.date: 03/15/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: high
ms.openlocfilehash: 62dc1cf81bd26ca5ba4adf181cc9f710e41565c2
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="download-and-install-package-updates-for-your-app"></a>Herunterladen und Installieren von Paketupdates für Ihre App


Ab Windows10 (Version 1607) können Sie eine API im Namespace [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) verwenden, um programmgesteuert nach Paketupdates für die aktuelle App zu suchen und diese herunterzuladen und zu installieren. Sie können auch Abfragen für Pakete ausführen, die [im Windows Dev Center-Dashboard als obligatorisch gekennzeichnet](#mandatory-dashboard) wurden, und Funktionen in Ihrer App deaktivieren, bis das erforderliche Update installiert wurde.

Mithilfe dieser Features können Sie Benutzer automatisch mit der neuesten Version Ihrer App und der zugehörigen Dienste auf dem neuesten Stand halten.

## <a name="api-overview"></a>API-Übersicht

In Apps für Windows10 (ab Version1607) können Sie die folgenden Methoden der [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Klasse verwenden, um Paketupdates herunterzuladen und zu installieren.

|  Methode  |  Beschreibung  |
|----------|---------------|
| [GetAppAndOptionalStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext#Windows_Services_Store_StoreContext_GetAppAndOptionalStorePackageUpdatesAsync) | Rufen Sie diese Methode auf, um die Liste der verfügbaren Paketupdates abzurufen. Hinweis: Zwischen dem Zeitpunkt, an dem ein Paket den Zertifizierungsprozess durchläuft, und dem Zeitpunkt, an dem die Methode **GetAppAndOptionalStorePackageUpdatesAsync** erkennt, dass das Paketupdate für die App zur Verfügung steht, kann eine Verzögerung von bis zu einem Tag auftreten. |
| [RequestDownloadStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext#Windows_Services_Store_StoreContext_RequestDownloadStorePackageUpdatesAsync_Windows_Foundation_Collections_IIterable_Windows_Services_Store_StorePackageUpdate__) | Rufen Sie diese Methode auf, um die verfügbaren Paketupdates herunterzuladen (jedoch nicht zu installieren). Unter diesem Betriebssystem wird ein Dialogfeld angezeigt, in dem der Benutzer dem Herunterladen der Updates zustimmen muss. |
| [RequestDownloadAndInstallStorePackageUpdatesAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext#Windows_Services_Store_StoreContext_RequestDownloadAndInstallStorePackageUpdatesAsync_Windows_Foundation_Collections_IIterable_Windows_Services_Store_StorePackageUpdate__) | Rufen Sie diese Methode auf, um die verfügbaren Paketupdates herunterzuladen und zu installieren. Unter dem Betriebssystem werden Dialogfelder angezeigt, in denen der Benutzer dem Herunterladen und Installieren der Updates zustimmen muss. Wenn Sie die Paketupdates durch Aufrufen von **RequestDownloadStorePackageUpdatesAsync** bereits heruntergeladen haben, überspringt diese Methode den Downloadvorgang und installiert nur die Updates.  |

<span/>

Diese Methoden verwenden [StorePackageUpdate](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdate)-Objekte, die den verfügbaren Updatepaketen entsprechen. Verwenden Sie die folgenden **StorePackageUpdate**-Eigenschaften zum Abrufen von Informationen über ein Updatepaket.

|  Eigenschaft  |  Beschreibung  |
|----------|---------------|
| [Mandatory](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdate#Windows_Services_Store_StorePackageUpdate_Mandatory) | Verwenden Sie diese Eigenschaft, um zu ermitteln, ob das Paket im Dev Center-Dashboard als obligatorisch gekennzeichnet ist. |
| [Package](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdate#Windows_Services_Store_StorePackageUpdate_Package) | Verwenden Sie diese Eigenschaft, um die zugrunde liegenden paketbezogenen Daten abzurufen. |

<span/>

## <a name="code-examples"></a>Codebeispiele

Die folgenden Codebeispiele zeigen, wie Paketupdates in Ihrer App heruntergeladen und installiert werden. In diesem Beispiel wird Folgendes vorausgesetzt:
* Der Code wird im Kontext einer [Seite](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx) ausgeführt.
* Die **Seite** enthält eine [ProgressBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressbar.aspx) mit dem Namen ```downloadProgressBar```, um einen Status für den Downloadvorgang bereitzustellen.
* Die Codedatei enthält eine **using**-Anweisung für die Namespaces **Windows.Services.Store**, **Windows.Threading.Tasks** und **Windows.UI.Popups**.
* Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat. Verwenden Sie für eine [Multi-User-App](https://msdn.microsoft.com/windows/uwp/xbox-apps/multi-user-applications) die [GetForUser](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext#Windows_Services_Store_StoreContext_GetForUser_Windows_System_User_)-Methode, um ein **StoreContext**-Objekt anstelle der [GetDefault](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext#Windows_Services_Store_StoreContext_GetDefault)-Methode abzurufen.

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

### <a name="display-progress-info-for-the-download-and-install"></a>Anzeigen von Statusinformationen für das Herunterladen und Installieren

Wenn Sie **RequestDownloadStorePackageUpdatesAsync** oder **RequestDownloadAndInstallStorePackageUpdatesAsync** aufrufen, können Sie einen [Progress](https://docs.microsoft.com/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_#Windows_Foundation_IAsyncOperationWithProgress_2_Progress)-Handler hinzufügen, der einmal für jeden Schrittim Downloadprozess (oder Download und Installation) für die einzelnen Pakete in dieser Anforderung aufgerufen wird. Der Handler empfängt ein [StorePackageUpdateStatus](https://docs.microsoft.com/uwp/api/windows.services.store.storepackageupdatestatus)-Objekt, das Informationen zum Updatepaket enthält, das die Statusbenachrichtigung ausgelöst hat. In den vorherigen Beispielen wird das Feld **PackageDownloadProgress** des **StorePackageUpdateStatus**-Objekts verwendet, um den Fortschritt des Download- und Installationsprozesses anzuzeigen.

Beachten Sie, dass sich beim Aufruf von **RequestDownloadAndInstallStorePackageUpdatesAsync** zum Herunterladen und Installieren der Paketupdates in einem einzigen Vorgang der Wert des **PackageDownloadProgress**-Felds während des Downloadvorgangs für ein Paket von 0,0 auf 0,8 und dann während der Installation von 0,8 auf 1,0 erhöht. Wenn Sie den auf Ihrer benutzerdefinierten Statusanzeige angezeigten Prozentsatz direkt dem Wert des **PackageDownloadProgress**-Felds zuordnen, zeigt die Anzeige daher 80% an, wenn das Paket fertig herunterladen ist, und das Betriebssystem zeigt das Installationsdialogfeld an. Wenn Ihre benutzerdefinierte Statusanzeige 100% anzeigen soll, wenn das Paket heruntergeladen und bereit zum Installieren ist, können Sie den Code so ändern, dass der Statusanzeige 100% zugewiesen werden, wenn das **PackageDownloadProgress**-Feld 0,8 erreicht.

<span id="mandatory-dashboard" />
## <a name="make-a-package-submission-mandatory-in-the-dev-center-dashboard"></a>Kennzeichnen einer Paketübermittlung als obligatorisch im Dev Center-Dashboard

Wenn Sie eine Paketübermittlung für eine App für Windows10 (Version 1607 oder höher) erstellen, können Sie das Paket als obligatorisch kennzeichnen und das Datum/die Uhrzeit angeben, wann es obligatorisch wird. Wenn diese Eigenschaft festgelegt wurde und Ihre App mithilfe der oben in diesem Artikel beschriebenen API erkennt, dass das Paketupdate verfügbar ist, kann die App ermitteln, ob das Updatepaket obligatorisch ist, und ihr Verhalten ändern, bis das Update installiert ist (z.B. kann Ihre App Features deaktivieren).

> [!NOTE]
> Der obligatorische Status eines Pakets wird von Microsoft nicht erzwungen, und das Betriebssystem verfügt über keine Benutzeroberfläche, die den Benutzer darauf hinweist, dass ein erforderliches App-Update installiert werden muss. Entwickler sollten die Einstellung „Obligatorisch” verwenden, um erforderliche App-Updates in ihrem eigenen Code zu erzwingen.  

So kennzeichnen Sie eine Paketübermittlung als obligatorisch:

1. Melden Sie sich beim [Dev Center-Dashboard](https://dev.windows.com/overview) an, und navigieren Sie zur Übersichtsseite für Ihre App.
2. Klicken Sie auf den Namen der Übermittlung, die das Paketupdate enthält, das Sie erforderlich machen möchten.
3. Navigieren Sie zu der **Pakete**-Seite für die Übermittlung. Wählen Sie im unteren Bereich der Seite **Dieses Update als obligatorisch kennzeichnen** aus, und wählen Sie dann den Tag und die Uhrzeit aus, wann das Paketupdate obligatorisch wird. Diese Option gilt für alle UWP-Pakete in der Übermittlung.

Weitere Informationen zum Konfigurieren von Paketen im Dev Center-Dashboard finden Sie unter [Hochladen von App-Paketen](../publish/upload-app-packages.md).

  > [!NOTE]
  > Wenn Sie ein [Flight-Paket](../publish/package-flights.md) erstellen, können Sie die Pakete mit einer ähnlichen Benutzeroberfläche auf der **Pakete**-Seite für das Test-Flight als obligatorisch kennzeichnen. In diesem Fall gilt das obligatorische Paketupdate nur für die Kunden, die Teil der Flight-Gruppe sind.
