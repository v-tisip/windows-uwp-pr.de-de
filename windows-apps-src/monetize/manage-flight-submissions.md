---
ms.assetid: 2A454057-FF14-40D2-8ED2-CEB5F27E0226
description: Verwenden Sie diese Methoden in der Microsoft Store-Übermittlungs-API, Flight-Paket-Übermittlungen für apps zu verwalten, die für Ihr Partner Center-Konto registriert wurden.
title: Verwalten von Flight-Paket-Übermittlungen
ms.date: 04/16/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight-Übermittlungen
ms.localizationpriority: medium
ms.openlocfilehash: 19ddd43d4e61480764882f1b10e6240aa2afeb8c
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8875492"
---
# <a name="manage-package-flight-submissions"></a><span data-ttu-id="45fc8-104">Verwalten von Flight-Paket-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="45fc8-104">Manage package flight submissions</span></span>

<span data-ttu-id="45fc8-105">Mithilfe der Methoden der Microsoft Store-Übermittlungs-API können Sie Flight-Paket-Übermittlungen für Ihre Apps verwalten, einschließlich gradueller Paketrollouts.</span><span class="sxs-lookup"><span data-stu-id="45fc8-105">The Microsoft Store submission API provides methods you can use to manage package flight submissions for your apps, including gradual package rollouts.</span></span> <span data-ttu-id="45fc8-106">Eine Einführung in die Microsoft Store-Übermittlungs-API einschließlich der Voraussetzungen für die Verwendung der API finden Sie unter [Erstellen und Verwalten von Übermittlungen mit MicrosoftStore-Diensten](create-and-manage-submissions-using-windows-store-services.md).</span><span class="sxs-lookup"><span data-stu-id="45fc8-106">For an introduction to the Microsoft Store submission API, including prerequisites for using the API, see [Create and manage submissions using Microsoft Store services](create-and-manage-submissions-using-windows-store-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45fc8-107">Wenn Sie die Microsoft Store-Übermittlungs-API zum Erstellen einer Flight-Paket-Übermittlung verwenden, achten Sie darauf, dass Sie Sie weitere Änderungen an der Übermittlung ausschließlich mithilfe der API und nicht Partner Center.</span><span class="sxs-lookup"><span data-stu-id="45fc8-107">If you use the Microsoft Store submission API to create a submission for a package flight, be sure to make further changes to the submission only by using the API, rather than Partner Center.</span></span> <span data-ttu-id="45fc8-108">Wenn Sie das Dashboard zum Ändern einer Übermittlung verwenden, die ursprünglich mit der API erstellt wurde, können Sie die Übermittlung nicht länger mithilfe der API ändern oder übermitteln.</span><span class="sxs-lookup"><span data-stu-id="45fc8-108">If you use the dashboard to change a submission that you originally created by using the API, you will no longer be able to change or commit that submission by using the API.</span></span> <span data-ttu-id="45fc8-109">In einigen Fällen kann der Fehlerstatus der Übermittlung belassen werden, mit dem die Übermittlung nicht fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="45fc8-109">In some cases, the submission could be left in an error state where it cannot proceed in the submission process.</span></span> <span data-ttu-id="45fc8-110">In diesem Fall müssen Sie die Übermittlung löschen und eine neue Übermittlung erstellen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-110">If this occurs, you must delete the submission and create a new submission.</span></span>

<span id="methods-for-package-flight-submissions" />

## <a name="methods-for-managing-package-flight-submissions"></a><span data-ttu-id="45fc8-111">Methoden zum Verwalten von Flight-Paket-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="45fc8-111">Methods for managing package flight submissions</span></span>

<span data-ttu-id="45fc8-112">Verwenden Sie die folgenden Methoden zum Abrufen, Erstellen, Aktualisieren, Übernehmen oder Löschen einer Flight-Paket-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-112">Use the following methods to get, create, update, commit, or delete a package flight submission.</span></span> <span data-ttu-id="45fc8-113">Bevor Sie diese Methoden verwenden können, muss das Flight-Paket bereits im Partner Center vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="45fc8-113">Before you can use these methods, the package flight must already exist in Partner Center.</span></span> <span data-ttu-id="45fc8-114">Sie können ein Paket erstellen flight [im Partner Center](https://msdn.microsoft.com/windows/uwp/publish/package-flights) oder mithilfe der Methoden der Microsoft Store-Übermittlungs-API, die in [Verwalten von Flight-Pakete](manage-flights.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="45fc8-114">You can create a package flight [in Partner Center](https://msdn.microsoft.com/windows/uwp/publish/package-flights) or by using the Microsoft Store submission API methods in described in [Manage package flights](manage-flights.md).</span></span>

<table>
<colgroup>
<col width="10%" />
<col width="30%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="45fc8-115">Methode</span><span class="sxs-lookup"><span data-stu-id="45fc8-115">Method</span></span></th>
<th align="left"><span data-ttu-id="45fc8-116">URI</span><span class="sxs-lookup"><span data-stu-id="45fc8-116">URI</span></span></th>
<th align="left"><span data-ttu-id="45fc8-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-117">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><span data-ttu-id="45fc8-118">GET</span><span class="sxs-lookup"><span data-stu-id="45fc8-118">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}</td>
<td align="left"><a href="get-a-flight-submission.md"><span data-ttu-id="45fc8-119">Abrufen einer vorhandenen Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-119">Get an existing package flight submission</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="45fc8-120">GET</span><span class="sxs-lookup"><span data-stu-id="45fc8-120">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/status</td>
<td align="left"><a href="get-status-for-a-flight-submission.md"><span data-ttu-id="45fc8-121">Abrufen des Status einer vorhandenen Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-121">Get the status of an existing package flight submission</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="45fc8-122">POST</span><span class="sxs-lookup"><span data-stu-id="45fc8-122">POST</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions</td>
<td align="left"><a href="create-a-flight-submission.md"><span data-ttu-id="45fc8-123">Erstellen einer neuen Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-123">Create a new package flight submission</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="45fc8-124">PUT</span><span class="sxs-lookup"><span data-stu-id="45fc8-124">PUT</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}</td>
<td align="left"><a href="update-a-flight-submission.md"><span data-ttu-id="45fc8-125">Aktualisieren einer vorhandenen Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-125">Update an existing package flight submission</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="45fc8-126">POST</span><span class="sxs-lookup"><span data-stu-id="45fc8-126">POST</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/commit</td>
<td align="left"><a href="commit-a-flight-submission.md"><span data-ttu-id="45fc8-127">Committen einer neuen oder aktualisierten Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-127">Commit a new or updated package flight submission</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="45fc8-128">DELETE</span><span class="sxs-lookup"><span data-stu-id="45fc8-128">DELETE</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}</td>
<td align="left"><a href="delete-a-flight-submission.md"><span data-ttu-id="45fc8-129">Löschen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-129">Delete a package flight submission</span></span></a></td>
</tr>
</tbody>
</table>

<span id="create-a-package-flight-submission">

## <a name="create-a-package-flight-submission"></a><span data-ttu-id="45fc8-130">Erstellen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-130">Create a package flight submission</span></span>

<span data-ttu-id="45fc8-131">Gehen Sie folgendermaßen vor, um eine Übermittlung für ein Flight-Paket zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-131">To create a submission for a package flight, follow this process.</span></span>

1. <span data-ttu-id="45fc8-132">Falls noch nicht geschehen, vollständige die erforderlichen Komponenten in beschriebenen [Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten](create-and-manage-submissions-using-windows-store-services.md), einschließlich des Verknüpfens einer Azure AD-Anwendung mit Ihr Partner Center-Konto und des Abrufens von Client-ID und Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="45fc8-132">If you have not yet done so, complete the prerequisites described in [Create and manage submissions using Microsoft Store services](create-and-manage-submissions-using-windows-store-services.md), including associating an Azure AD application with your Partner Center account and obtaining your client ID and key.</span></span> <span data-ttu-id="45fc8-133">Sie müssen dies nur einmal durchführen. nachdem Sie Client-ID und Schlüssel erhalten haben, können Sie diese jedes Mal wiederverwenden, wenn Sie ein neues Azure AD-Token erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-133">You only need to do this one time; after you have the client ID and key, you can reuse them any time you need to create a new Azure AD access token.</span></span>  

2. <span data-ttu-id="45fc8-134">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token).</span><span class="sxs-lookup"><span data-stu-id="45fc8-134">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token).</span></span> <span data-ttu-id="45fc8-135">Sie müssen dieses Zugriffstoken an die Methoden in der Microsoft Store-Übermittlungs-API übergeben.</span><span class="sxs-lookup"><span data-stu-id="45fc8-135">You must pass this access token to the methods in the Microsoft Store submission API.</span></span> <span data-ttu-id="45fc8-136">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="45fc8-136">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="45fc8-137">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-137">After the token expires, you can obtain a new one.</span></span>

3. <span data-ttu-id="45fc8-138">[Erstellen Sie eine Flight-Paket-Übermittlung](create-a-flight-submission.md) mithilfe der folgenden Methode in der Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="45fc8-138">[Create a package flight submission](create-a-flight-submission.md) by executing the following method in the Microsoft Store submission API.</span></span> <span data-ttu-id="45fc8-139">Diese Methode erstellt eine neue laufende Übermittlung, die eine Kopie der letzten veröffentlichten Übermittlung ist.</span><span class="sxs-lookup"><span data-stu-id="45fc8-139">This method creates a new in-progress submission, which is a copy of your last published submission.</span></span>

    ```
    POST https://manage.devcenter.microsoft.com/v1.0/my/applications{applicationId}/flights/{flightId}/submissions
    ```

    <span data-ttu-id="45fc8-140">Der Antworttext enthält eine [Flight-Übermittlung](#flight-submission-object)-ressource, die eine ID für die neue Übermittlung, die SAS-URI (Shared Access Signatur) zum Hochladen von Paketen für die Übermittlung an Azure Blob Storage und die Daten für die neue Übermittlung (inkl. alle Eintrags- und Preisinfos) enthält.</span><span class="sxs-lookup"><span data-stu-id="45fc8-140">The response body contains a [flight submission](#flight-submission-object) resource that includes the ID of the new submission, the shared access signature (SAS) URI for uploading any packages for the submission to Azure Blob storage, and the data for the new submission (including all the listings and pricing information).</span></span>

    > [!NOTE]
    > <span data-ttu-id="45fc8-141">Ein SAS-URI ermöglicht den Zugriff auf eine sichere Ressource in Azure Storage, ohne dass Kontoschlüssel benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="45fc8-141">A SAS URI provides access to a secure resource in Azure storage without requiring account keys.</span></span> <span data-ttu-id="45fc8-142">Hintergrundinformationen zu SAS-URIs und deren Verwendung mit Azure Blob Storage finden Sie unter [Shared Access Signatures, Teil 1: Verstehen des SAS-Modells](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1) und [Shared Access Signatures, Teil 2: Erstellen und Verwenden einer SAS mit BLOB-Speicher](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-2/).</span><span class="sxs-lookup"><span data-stu-id="45fc8-142">For background information about SAS URIs and their use with Azure Blob storage, see [Shared Access Signatures, Part 1: Understanding the SAS model](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1) and [Shared Access Signatures, Part 2: Create and use a SAS with Blob storage](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-2/).</span></span>

4. <span data-ttu-id="45fc8-143">Wenn Sie neue Pakete für die Übermittlung hinzufügen, müssen Sie [die Pakete vorbereiten](https://msdn.microsoft.com/windows/uwp/publish/app-package-requirements) und einem ZIP-Archiv hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-143">If you are adding new packages for the submission, [prepare the packages](https://msdn.microsoft.com/windows/uwp/publish/app-package-requirements) and add them to a ZIP archive.</span></span>

5. <span data-ttu-id="45fc8-144">Revidieren Sie die [Flight-Übermittlungsdaten](#flight-submission-object)mit allen erforderlichen Änderungen für die neue Übermittlung, und führen Sie die folgende Methode aus, um [die Flight-Paket-Übermittlung zu aktualisieren](update-a-flight-submission.md).</span><span class="sxs-lookup"><span data-stu-id="45fc8-144">Revise the [flight submission](#flight-submission-object) data with any required changes for the new submission, and execute the following method to [update the package flight submission](update-a-flight-submission.md).</span></span>

    ```
    PUT https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}
    ```
      > [!NOTE]
      > <span data-ttu-id="45fc8-145">Wenn Sie neue Pakete für die Übermittlung hinzufügen, müssen Sie die Übermittlungsdaten aktualisieren, damit diese auf den Namen und den relativen Pfad dieser Dateien im ZIP-Archiv verweisen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-145">If you are adding new packages for the submission, make sure you update the submission data to refer to the name and relative path of these files in the ZIP archive.</span></span>

4. <span data-ttu-id="45fc8-146">Wenn Sie neue Pakete für die Übermittlung hinzufügen, müssen Sie das ZIP-Archiv mit dem SAS-URI auf [Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-introduction#blob-storage) hochladen, der im Antworttext der POST-Methode bereitgestellt wurde, die Sie zuvor aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="45fc8-146">If you are adding new packages for the submission, upload the ZIP archive to [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-introduction#blob-storage) using the SAS URI that was provided in the response body of the POST method you called earlier.</span></span> <span data-ttu-id="45fc8-147">Zu diesem Zweck können Sie verschiedene Azure-Bibliotheken auf unterschiedlichen Plattformen verwenden, darunter:</span><span class="sxs-lookup"><span data-stu-id="45fc8-147">There are different Azure libraries you can use to do this on a variety of platforms, including:</span></span>

    * [<span data-ttu-id="45fc8-148">Azure Storage-Clientbibliothek für .NET</span><span class="sxs-lookup"><span data-stu-id="45fc8-148">Azure Storage Client Library for .NET</span></span>](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-blobs)
    * [<span data-ttu-id="45fc8-149">Azure Storage SDK für Java</span><span class="sxs-lookup"><span data-stu-id="45fc8-149">Azure Storage SDK for Java</span></span>](https://docs.microsoft.com/azure/storage/storage-java-how-to-use-blob-storage)
    * [<span data-ttu-id="45fc8-150">Azure Storage SDK für Python</span><span class="sxs-lookup"><span data-stu-id="45fc8-150">Azure Storage SDK for Python</span></span>](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-blob-storage)

    <span data-ttu-id="45fc8-151">Das folgende C#-Codebeispiel zeigt, wie Sie ein ZIP-Archiv mithilfe der [CloudBlockBlob](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.storage.blob.cloudblockblob.aspx)-Klasse in der Azure Storage-Clientbibliothek für .NET auf Azure Blob Storage hochladen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-151">The following C# code example demonstrates how to upload a ZIP archive to Azure Blob storage using the [CloudBlockBlob](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.storage.blob.cloudblockblob.aspx) class in the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="45fc8-152">Im Beispiel wird davon ausgegangen, dass das ZIP-Archiv bereits in ein Datenstromobjekt geschrieben wurde.</span><span class="sxs-lookup"><span data-stu-id="45fc8-152">This example assumes that the ZIP archive has already been written to a stream object.</span></span>

    ```csharp
    string sasUrl = "https://productingestionbin1.blob.core.windows.net/ingestion/26920f66-b592-4439-9a9d-fb0f014902ec?sv=2014-02-14&sr=b&sig=usAN0kNFNnYE2tGQBI%2BARQWejX1Guiz7hdFtRhyK%2Bog%3D&se=2016-06-17T20:45:51Z&sp=rwl";
    Microsoft.WindowsAzure.Storage.Blob.CloudBlockBlob blockBob =
        new Microsoft.WindowsAzure.Storage.Blob.CloudBlockBlob(new System.Uri(sasUrl));
    await blockBob.UploadFromStreamAsync(stream);
    ```

5. <span data-ttu-id="45fc8-153">Führen Sie folgende Methode aus, um [die Flight-Paket-Übermittlung zu committen](commit-a-flight-submission.md).</span><span class="sxs-lookup"><span data-stu-id="45fc8-153">[Commit the package flight submission](commit-a-flight-submission.md) by executing the following method.</span></span> <span data-ttu-id="45fc8-154">Dies wird Partner Center Warnung an, dass Sie Ihre Übermittlung fertig gestellt haben und die Updates für Ihr Konto jetzt angewendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-154">This will alert Partner Center that you are done with your submission and that your updates should now be applied to your account.</span></span>

    ```
    POST https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/commit
    ```

6. <span data-ttu-id="45fc8-155">Überprüfen Sie den Commit-Status, indem Sie die folgende Methode ausführen, um [den Status der Flight-Paket-Übermittlung abzurufen](get-status-for-a-flight-submission.md).</span><span class="sxs-lookup"><span data-stu-id="45fc8-155">Check on the commit status by executing the following method to [get the status of the package flight submission](get-status-for-a-flight-submission.md).</span></span>

    ```
    GET https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/status
    ```

    <span data-ttu-id="45fc8-156">Um den Status der Übermittlung zu überprüfen, zeigen Sie den Wert *status* im Antworttext an.</span><span class="sxs-lookup"><span data-stu-id="45fc8-156">To confirm the submission status, review the *status* value in the response body.</span></span> <span data-ttu-id="45fc8-157">Dieser Wert sollte von **CommitStarted** entweder in **PreProcessing** geändert worden sein, wenn die Anforderung erfolgreich war, oder in **CommitFailed**, wenn die Anforderung Fehler enthalten hat.</span><span class="sxs-lookup"><span data-stu-id="45fc8-157">This value should change from **CommitStarted** to either **PreProcessing** if the request succeeds or to **CommitFailed** if there are errors in the request.</span></span> <span data-ttu-id="45fc8-158">Wenn Fehler aufgetreten sind, enthält das Feld *StatusDetails* Feld weitere Details zu den Fehlern.</span><span class="sxs-lookup"><span data-stu-id="45fc8-158">If there are errors, the *statusDetails* field contains further details about the error.</span></span>

7. <span data-ttu-id="45fc8-159">Nachdem das Commit erfolgreich abgeschlossen wurde, wird die Übermittlung zur Aufnahme an den Store gesendet.</span><span class="sxs-lookup"><span data-stu-id="45fc8-159">After the commit has successfully completed, the submission is sent to the Store for ingestion.</span></span> <span data-ttu-id="45fc8-160">Sie können weiterhin die mithilfe der vorherigen Methode, oder besuchen die Partner Center überwachen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-160">You can continue to monitor the submission progress by using the previous method, or by visiting Partner Center.</span></span>

<span/>

## <a name="code-examples"></a><span data-ttu-id="45fc8-161">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="45fc8-161">Code examples</span></span>

<span data-ttu-id="45fc8-162">Die folgenden Artikel enthalten ausführliche Codebeispiele, die zeigen, wie Sie eine Flight-Paket-Übermittlung in verschiedenen Programmiersprachen erstellen:</span><span class="sxs-lookup"><span data-stu-id="45fc8-162">The following articles provide detailed code examples that demonstrate how to create a package flight submission in several different programming languages:</span></span>

* [<span data-ttu-id="45fc8-163">C#-Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="45fc8-163">C# code examples</span></span>](csharp-code-examples-for-the-windows-store-submission-api.md)
* [<span data-ttu-id="45fc8-164">Java-Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="45fc8-164">Java code examples</span></span>](java-code-examples-for-the-windows-store-submission-api.md)
* [<span data-ttu-id="45fc8-165">Python-Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="45fc8-165">Python code examples</span></span>](python-code-examples-for-the-windows-store-submission-api.md)

## <a name="storebroker-powershell-module"></a><span data-ttu-id="45fc8-166">StoreBroker PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="45fc8-166">StoreBroker PowerShell module</span></span>

<span data-ttu-id="45fc8-167">Als Alternative zum direkten Aufruf der Microsoft Store-Übermittlungs-API stellen wir ein PowerShell-Modul (Open Source) bereit, das eine Befehlszeilenschnittstelle über der API implementiert.</span><span class="sxs-lookup"><span data-stu-id="45fc8-167">As an alternative to calling the Microsoft Store submission API directly, we also provide an open-source PowerShell module which implements a command-line interface on top of the API.</span></span> <span data-ttu-id="45fc8-168">Dieses Modul heißt [StoreBroker](https://aka.ms/storebroker).</span><span class="sxs-lookup"><span data-stu-id="45fc8-168">This module is called [StoreBroker](https://aka.ms/storebroker).</span></span> <span data-ttu-id="45fc8-169">Sie können dieses Modul verwenden, um Ihre App-, Flight- und Add-On-Übermittlungen über die Befehlszeile anstatt über die Microsoft Store-Übermittlungs-API direkt zu verwalten. Sie können auch ganz einfach die Quelle durchsuchen, um weitere Beispiele für das Aufrufen dieser API zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="45fc8-169">You can use this module to manage your app, flight, and add-on submissions from the command line instead of calling the Microsoft Store submission API directly, or you can simply browse the source to see more examples for how to call this API.</span></span> <span data-ttu-id="45fc8-170">Das StoreBroker-Modul wird innerhalb von Microsoft aktiv als primäre Methode verwendet, durch die viele Erstanbieter-Apps an den Store übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="45fc8-170">The StoreBroker module is actively used within Microsoft as the primary way that many first-party applications are submitted to the Store.</span></span>

<span data-ttu-id="45fc8-171">Weitere Informationen finden Sie auf unserer [StoreBroker-Seite auf GitHub](https://aka.ms/storebroker).</span><span class="sxs-lookup"><span data-stu-id="45fc8-171">For more information, see our [StoreBroker page on GitHub](https://aka.ms/storebroker).</span></span>

<span id="manage-gradual-package-rollout">

## <a name="manage-a-gradual-package-rollout-for-a-package-flight-submission"></a><span data-ttu-id="45fc8-172">Verwalten eines graduellen Paketrollouts für eine Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-172">Manage a gradual package rollout for a package flight submission</span></span>

<span data-ttu-id="45fc8-173">Sie können die aktualisierten Pakete in einer Flight-Paket-Übermittlung graduell für einen bestimmten Prozentsatz der Kunden Ihrer App unter Windows10 einführen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-173">You can gradually roll out the updated packages in a package flight submission to a percentage of your app’s customers on Windows 10.</span></span> <span data-ttu-id="45fc8-174">So können Sie Feedback und Analysedaten für die jeweiligen Pakete überwachen und vor einem umfassenden Rollout sicherstellen, dass das Update ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="45fc8-174">This allows you to monitor feedback and analytic data for the specific packages to make sure you’re confident about the update before rolling it out more broadly.</span></span> <span data-ttu-id="45fc8-175">Sie können den Rollout-Prozentwert für eine veröffentlichte Übermittlung ändern (oder die Aktualisierung anhalten), ohne dass Sie eine neue Übermittlung erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-175">You can change the rollout percentage (or halt the update) for a published submission without having to create a new submission.</span></span> <span data-ttu-id="45fc8-176">Weitere Informationen, einschließlich Informationen zum Aktivieren und Verwalten einer graduellen paketrollouts im Partner Center finden Sie [in diesem Artikel](../publish/gradual-package-rollout.md).</span><span class="sxs-lookup"><span data-stu-id="45fc8-176">For more details, including instructions for how to enable and manage a gradual package rollout in Partner Center, see [this article](../publish/gradual-package-rollout.md).</span></span>

<span data-ttu-id="45fc8-177">Um ein graduelles Paketrollout für eine Flight-Paket-Übermittlung programmgesteuert zu aktivieren, gehen Sie wie folgt vor, und verwenden Sie dabei Methoden in der Microsoft Store-Übermittlungs-API:</span><span class="sxs-lookup"><span data-stu-id="45fc8-177">To programmatically enable a gradual package rollout for a package flight submission, follow this process using methods in the Microsoft Store submission API:</span></span>

  1. <span data-ttu-id="45fc8-178">[Erstellen Sie eine Flight-Paket-Übermittlung](create-a-flight-submission.md), oder [rufen Sie eine Flight-Paket-Übermittlung ab](get-a-flight-submission.md).</span><span class="sxs-lookup"><span data-stu-id="45fc8-178">[Create a package flight submission](create-a-flight-submission.md) or [get a package flight submission](get-a-flight-submission.md).</span></span>
  2. <span data-ttu-id="45fc8-179">Suchen Sie in den Antwortdaten die [packageRollout](#package-rollout-object)-Ressource, legen Sie das Feld *isPackageRollout* auf „true“ und das Feld *packageRolloutPercentage* auf den Prozentsatz der Kunden Ihrer App fest, die die aktualisierten Pakete erhalten sollen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-179">In the response data, locate the [packageRollout](#package-rollout-object) resource, set the *isPackageRollout* field to true, and set the *packageRolloutPercentage* field to the percentage of your app's customers who should get the updated packages.</span></span>
  3. <span data-ttu-id="45fc8-180">Übergeben Sie die aktualisierten Daten der Flight-Paket-Übermittlung an die Methode zur [Aktualisierung einer Flight-Paket-Übermittlung](update-a-flight-submission.md).</span><span class="sxs-lookup"><span data-stu-id="45fc8-180">Pass the updated package flight submission data to the [update a package flight submission](update-a-flight-submission.md) method.</span></span>

<span data-ttu-id="45fc8-181">Nachdem ein graduelles Paketrollout für eine Flight-Paket-Übermittlung aktiviert wurde, können Sie das graduelle Rollout mithilfe der folgenden Methoden programmgesteuert abrufen, aktualisieren, anhalten oder abschließen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-181">After a gradual package rollout is enabled for a package flight submission, you can use the following methods to programmatically get, update, halt, or finalize the gradual rollout.</span></span>

<table>
<colgroup>
<col width="10%" />
<col width="30%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="45fc8-182">Methode</span><span class="sxs-lookup"><span data-stu-id="45fc8-182">Method</span></span></th>
<th align="left"><span data-ttu-id="45fc8-183">URI</span><span class="sxs-lookup"><span data-stu-id="45fc8-183">URI</span></span></th>
<th align="left"><span data-ttu-id="45fc8-184">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-184">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><span data-ttu-id="45fc8-185">GET</span><span class="sxs-lookup"><span data-stu-id="45fc8-185">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/packagerollout</td>
<td align="left"><a href="get-package-rollout-info-for-a-flight-submission.md"><span data-ttu-id="45fc8-186">Abrufen der Informationen zu einem graduellen Rollout für eine Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-186">Get the gradual rollout info for a package flight submission</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="45fc8-187">POST</span><span class="sxs-lookup"><span data-stu-id="45fc8-187">POST</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/updatepackagerolloutpercentage</td>
<td align="left"><a href="update-the-package-rollout-percentage-for-a-flight-submission.md"><span data-ttu-id="45fc8-188">Aktualisieren des Prozentsatzes eines graduellen Rollouts für eine Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-188">Update the gradual rollout percentage for a package flight submission</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="45fc8-189">POST</span><span class="sxs-lookup"><span data-stu-id="45fc8-189">POST</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/haltpackagerollout</td>
<td align="left"><a href="halt-the-package-rollout-for-a-flight-submission.md"><span data-ttu-id="45fc8-190">Anhalten des graduellen Rollouts für eine Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-190">Halt the gradual rollout for a package flight submission</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="45fc8-191">POST</span><span class="sxs-lookup"><span data-stu-id="45fc8-191">POST</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/finalizepackagerollout</td>
<td align="left"><a href="finalize-the-package-rollout-for-a-flight-submission.md"><span data-ttu-id="45fc8-192">Abschließen des graduellen Rollouts für eine Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-192">Finalize the gradual rollout for a package flight submission</span></span></a></td>
</tr>
</tbody>
</table>

<span/>

## <a name="data-resources"></a><span data-ttu-id="45fc8-193">Datenressourcen</span><span class="sxs-lookup"><span data-stu-id="45fc8-193">Data resources</span></span>

<span data-ttu-id="45fc8-194">Die Methoden der Microsoft Store-Übermittlungs-API für das Verwalten von Flight-Paket-Übermittlungen verwenden die folgenden JSON-Datenressourcen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-194">The Microsoft Store submission API methods for managing package flight submissions use the following JSON data resources.</span></span>

<span id="flight-submission-object" />

### <a name="flight-submission-resource"></a><span data-ttu-id="45fc8-195">Ressource für Flight-Paket-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="45fc8-195">Flight submission resource</span></span>

<span data-ttu-id="45fc8-196">Diese Ressource beschreibt eine Flight-Paket-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-196">This resource describes a package flight submission.</span></span>

```json
{
  "id": "1152921504621243649",
  "flightId": "cd2e368a-0da5-4026-9f34-0e7934bc6f23",
  "status": "PendingCommit",
  "statusDetails": {
    "errors": [],
    "warnings": [],
    "certificationReports": []
  },
  "flightPackages": [
    {
      "fileName": "newPackage.appx",
      "fileStatus": "PendingUpload",
      "id": "",
      "version": "1.0.0.0",
      "languages": ["en-us"],
      "capabilities": [],
      "minimumDirectXVersion": "None",
      "minimumSystemRam": "None"
    }
  ],
  "packageDeliveryOptions": {
    "packageRollout": {
        "isPackageRollout": false,
        "packageRolloutPercentage": 0.0,
        "packageRolloutStatus": "PackageRolloutNotStarted",
        "fallbackSubmissionId": "0"
    },
    "isMandatoryUpdate": false,
    "mandatoryUpdateEffectiveDate": "1601-01-01T00:00:00.0000000Z"
  },
  "fileUploadUrl": "https://productingestionbin1.blob.core.windows.net/ingestion/8b389577-5d5e-4cbe-a744-1ff2e97a9eb8?sv=2014-02-14&sr=b&sig=wgMCQPjPDkuuxNLkeG35rfHaMToebCxBNMPw7WABdXU%3D&se=2016-06-17T21:29:44Z&sp=rwl",
  "targetPublishMode": "Immediate",
  "targetPublishDate": "",
  "notesForCertification": "No special steps are required for certification of this app."
}
```

<span data-ttu-id="45fc8-197">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="45fc8-197">This resource has the following values.</span></span>

| <span data-ttu-id="45fc8-198">Wert</span><span class="sxs-lookup"><span data-stu-id="45fc8-198">Value</span></span>      | <span data-ttu-id="45fc8-199">Typ</span><span class="sxs-lookup"><span data-stu-id="45fc8-199">Type</span></span>   | <span data-ttu-id="45fc8-200">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-200">Description</span></span>              |
|------------|--------|------------------------------|
| <span data-ttu-id="45fc8-201">id</span><span class="sxs-lookup"><span data-stu-id="45fc8-201">id</span></span>            | <span data-ttu-id="45fc8-202">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-202">string</span></span>  | <span data-ttu-id="45fc8-203">Die ID für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-203">The ID for the submission.</span></span>  |
| <span data-ttu-id="45fc8-204">flightId</span><span class="sxs-lookup"><span data-stu-id="45fc8-204">flightId</span></span>           | <span data-ttu-id="45fc8-205">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-205">string</span></span>  |  <span data-ttu-id="45fc8-206">Die ID des Flight-Pakets, dem die Übermittlung zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="45fc8-206">The ID of the package flight that the submission is associated with.</span></span>  |  
| <span data-ttu-id="45fc8-207">status</span><span class="sxs-lookup"><span data-stu-id="45fc8-207">status</span></span>           | <span data-ttu-id="45fc8-208">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-208">string</span></span>  | <span data-ttu-id="45fc8-209">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-209">The status of the submission.</span></span> <span data-ttu-id="45fc8-210">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="45fc8-210">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="45fc8-211">None</span><span class="sxs-lookup"><span data-stu-id="45fc8-211">None</span></span></li><li><span data-ttu-id="45fc8-212">Canceled</span><span class="sxs-lookup"><span data-stu-id="45fc8-212">Canceled</span></span></li><li><span data-ttu-id="45fc8-213">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="45fc8-213">PendingCommit</span></span></li><li><span data-ttu-id="45fc8-214">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="45fc8-214">CommitStarted</span></span></li><li><span data-ttu-id="45fc8-215">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="45fc8-215">CommitFailed</span></span></li><li><span data-ttu-id="45fc8-216">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="45fc8-216">PendingPublication</span></span></li><li><span data-ttu-id="45fc8-217">Publishing</span><span class="sxs-lookup"><span data-stu-id="45fc8-217">Publishing</span></span></li><li><span data-ttu-id="45fc8-218">Published</span><span class="sxs-lookup"><span data-stu-id="45fc8-218">Published</span></span></li><li><span data-ttu-id="45fc8-219">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="45fc8-219">PublishFailed</span></span></li><li><span data-ttu-id="45fc8-220">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="45fc8-220">PreProcessing</span></span></li><li><span data-ttu-id="45fc8-221">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="45fc8-221">PreProcessingFailed</span></span></li><li><span data-ttu-id="45fc8-222">Certification</span><span class="sxs-lookup"><span data-stu-id="45fc8-222">Certification</span></span></li><li><span data-ttu-id="45fc8-223">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="45fc8-223">CertificationFailed</span></span></li><li><span data-ttu-id="45fc8-224">Release</span><span class="sxs-lookup"><span data-stu-id="45fc8-224">Release</span></span></li><li><span data-ttu-id="45fc8-225">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="45fc8-225">ReleaseFailed</span></span></li></ul>   |
| <span data-ttu-id="45fc8-226">statusDetails</span><span class="sxs-lookup"><span data-stu-id="45fc8-226">statusDetails</span></span>           | <span data-ttu-id="45fc8-227">object</span><span class="sxs-lookup"><span data-stu-id="45fc8-227">object</span></span>  |  <span data-ttu-id="45fc8-228">Eine [Ressource für Statusdetails](#status-details-object), die zusätzliche Details über den Status der Übermittlung enthält, einschließlich Fehlerinformationen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-228">A [status details resource](#status-details-object) that contains additional details about the status of the submission, including information about any errors.</span></span>  |
| <span data-ttu-id="45fc8-229">flightPackages</span><span class="sxs-lookup"><span data-stu-id="45fc8-229">flightPackages</span></span>           | <span data-ttu-id="45fc8-230">array</span><span class="sxs-lookup"><span data-stu-id="45fc8-230">array</span></span>  | <span data-ttu-id="45fc8-231">Enthält [Ressourcen für Flight-Pakete](#flight-package-object), die Details über die einzelnen Pakete in der Übermittlung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-231">Contains [flight package resources](#flight-package-object) that provide details about each package in the submission.</span></span>   |
| <span data-ttu-id="45fc8-232">packageDeliveryOptions</span><span class="sxs-lookup"><span data-stu-id="45fc8-232">packageDeliveryOptions</span></span>    | <span data-ttu-id="45fc8-233">object</span><span class="sxs-lookup"><span data-stu-id="45fc8-233">object</span></span>  | <span data-ttu-id="45fc8-234">Eine [Ressource für Paketübermittlungsoptionen](#package-delivery-options-object), die Einstellungen zu graduellen Paketrollouts und zu verpflichtenden Updates für die Übermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="45fc8-234">A [package delivery options resource](#package-delivery-options-object) that contains gradual package rollout and mandatory update settings for the submission.</span></span>   |
| <span data-ttu-id="45fc8-235">fileUploadUrl</span><span class="sxs-lookup"><span data-stu-id="45fc8-235">fileUploadUrl</span></span>           | <span data-ttu-id="45fc8-236">String</span><span class="sxs-lookup"><span data-stu-id="45fc8-236">string</span></span>  | <span data-ttu-id="45fc8-237">Der Shared Access Signature (SAS)-URI für das Hochladen der Pakete für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-237">The shared access signature (SAS) URI for uploading any packages for the submission.</span></span> <span data-ttu-id="45fc8-238">Wenn Sie neue Pakete oder Bilder für die Übermittlung hinzufügen, müssen Sie das ZIP-Archiv, das die Pakete enthält, zu dieser URI hochladen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-238">If you are adding new packages for the submission, upload the ZIP archive that contains the packages to this URI.</span></span> <span data-ttu-id="45fc8-239">Weitere Informationen finden Sie unter [Erstellen einer Flight-Paket-Übermittlung](#create-a-package-flight-submission).</span><span class="sxs-lookup"><span data-stu-id="45fc8-239">For more information, see [Create a package flight submission](#create-a-package-flight-submission).</span></span>  |
| <span data-ttu-id="45fc8-240">targetPublishMode</span><span class="sxs-lookup"><span data-stu-id="45fc8-240">targetPublishMode</span></span>           | <span data-ttu-id="45fc8-241">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-241">string</span></span>  | <span data-ttu-id="45fc8-242">Der Publish-Modus für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-242">The publish mode for the submission.</span></span> <span data-ttu-id="45fc8-243">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="45fc8-243">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="45fc8-244">Immediate</span><span class="sxs-lookup"><span data-stu-id="45fc8-244">Immediate</span></span></li><li><span data-ttu-id="45fc8-245">Manual</span><span class="sxs-lookup"><span data-stu-id="45fc8-245">Manual</span></span></li><li><span data-ttu-id="45fc8-246">SpecificDate</span><span class="sxs-lookup"><span data-stu-id="45fc8-246">SpecificDate</span></span></li></ul> |
| <span data-ttu-id="45fc8-247">targetPublishDate</span><span class="sxs-lookup"><span data-stu-id="45fc8-247">targetPublishDate</span></span>           | <span data-ttu-id="45fc8-248">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-248">string</span></span>  | <span data-ttu-id="45fc8-249">Das Veröffentlichungsdatum der Übermittlung im ISO 8601-Format, wenn *TargetPublishMode* den Wert SpecificDate hat.</span><span class="sxs-lookup"><span data-stu-id="45fc8-249">The publish date for the submission in ISO 8601 format, if the *targetPublishMode* is set to SpecificDate.</span></span>  |
| <span data-ttu-id="45fc8-250">notesForCertification</span><span class="sxs-lookup"><span data-stu-id="45fc8-250">notesForCertification</span></span>           | <span data-ttu-id="45fc8-251">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-251">string</span></span>  |  <span data-ttu-id="45fc8-252">Enthält zusätzliche Informationen für Zertifizierungstester wie Anmeldeinformationen für Testkonten und Schritte zum Zugriff auf und zur Überprüfung von Features.</span><span class="sxs-lookup"><span data-stu-id="45fc8-252">Provides additional info for the certification testers, such as test account credentials and steps to access and verify features.</span></span> <span data-ttu-id="45fc8-253">Weitere Informationen finden Sie unter [Hinweise zur Zertifizierung](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification).</span><span class="sxs-lookup"><span data-stu-id="45fc8-253">For more information, see [Notes for certification](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification).</span></span> |

<span id="status-details-object" />

### <a name="status-details-resource"></a><span data-ttu-id="45fc8-254">Ressource für Statusdetails</span><span class="sxs-lookup"><span data-stu-id="45fc8-254">Status details resource</span></span>

<span data-ttu-id="45fc8-255">Diese Ressource enthält weitere Informationen über den Status einer Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-255">This resource contains additional details about the status of a submission.</span></span> <span data-ttu-id="45fc8-256">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="45fc8-256">This resource has the following values.</span></span>

| <span data-ttu-id="45fc8-257">Wert</span><span class="sxs-lookup"><span data-stu-id="45fc8-257">Value</span></span>           | <span data-ttu-id="45fc8-258">Typ</span><span class="sxs-lookup"><span data-stu-id="45fc8-258">Type</span></span>    | <span data-ttu-id="45fc8-259">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-259">Description</span></span>                   |
|-----------------|---------|------|
|  <span data-ttu-id="45fc8-260">errors</span><span class="sxs-lookup"><span data-stu-id="45fc8-260">errors</span></span>               |    <span data-ttu-id="45fc8-261">object</span><span class="sxs-lookup"><span data-stu-id="45fc8-261">object</span></span>     |   <span data-ttu-id="45fc8-262">Ein Array von [Ressourcen für einzelne Statusdetails](#status-detail-object), die Fehlerdetails zur Übermittlung enthalten.</span><span class="sxs-lookup"><span data-stu-id="45fc8-262">An array of [status detail resources](#status-detail-object) that contain error details for the submission.</span></span>   |     
|  <span data-ttu-id="45fc8-263">warnings</span><span class="sxs-lookup"><span data-stu-id="45fc8-263">warnings</span></span>               |   <span data-ttu-id="45fc8-264">object</span><span class="sxs-lookup"><span data-stu-id="45fc8-264">object</span></span>      | <span data-ttu-id="45fc8-265">Ein Array von [Ressourcen für einzelne Statusdetails](#status-detail-object), die Warnungsdetails zur Übermittlung enthalten.</span><span class="sxs-lookup"><span data-stu-id="45fc8-265">An array of [status detail resources](#status-detail-object) that contain warning details for the submission.</span></span>     |
|  <span data-ttu-id="45fc8-266">certificationReports</span><span class="sxs-lookup"><span data-stu-id="45fc8-266">certificationReports</span></span>               |     <span data-ttu-id="45fc8-267">object</span><span class="sxs-lookup"><span data-stu-id="45fc8-267">object</span></span>    |   <span data-ttu-id="45fc8-268">Ein Array von [Ressourcen für Zertifizierungsberichte](#certification-report-object), die den Zugriff auf die Zertifizierungsberichtsdaten für die Übermittlung ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-268">An array of [certification report resources](#certification-report-object) that provide access to the certification report data for the submission.</span></span> <span data-ttu-id="45fc8-269">Sie können diese Berichte auf weitere Informationen überprüfen, wenn die Zertifizierung nicht erfolgreich ist.</span><span class="sxs-lookup"><span data-stu-id="45fc8-269">You can examine these reports for more information if the certification fails.</span></span>    |  


<span id="status-detail-object" />

### <a name="status-detail-resource"></a><span data-ttu-id="45fc8-270">Ressource für einzelne Statusdetails</span><span class="sxs-lookup"><span data-stu-id="45fc8-270">Status detail resource</span></span>

<span data-ttu-id="45fc8-271">Diese Ressource enthält weitere Informationen zu Fehlern oder Warnungen für eine Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-271">This resource contains additional information about any related errors or warnings for a submission.</span></span> <span data-ttu-id="45fc8-272">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="45fc8-272">This resource has the following values.</span></span>

| <span data-ttu-id="45fc8-273">Wert</span><span class="sxs-lookup"><span data-stu-id="45fc8-273">Value</span></span>           | <span data-ttu-id="45fc8-274">Typ</span><span class="sxs-lookup"><span data-stu-id="45fc8-274">Type</span></span>    | <span data-ttu-id="45fc8-275">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-275">Description</span></span>       |
|-----------------|---------|------|
|  <span data-ttu-id="45fc8-276">code</span><span class="sxs-lookup"><span data-stu-id="45fc8-276">code</span></span>               |    <span data-ttu-id="45fc8-277">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-277">string</span></span>     |   <span data-ttu-id="45fc8-278">Ein [Übermittlungsstatuscode](#submission-status-code), der den Fehler- oder Warnungstyp beschreibt.</span><span class="sxs-lookup"><span data-stu-id="45fc8-278">A [submission status code](#submission-status-code) that describes the type of error or warning.</span></span> |  
|  <span data-ttu-id="45fc8-279">details</span><span class="sxs-lookup"><span data-stu-id="45fc8-279">details</span></span>               |     <span data-ttu-id="45fc8-280">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-280">string</span></span>    |  <span data-ttu-id="45fc8-281">Eine Meldung mit weiteren Details zum Problem.</span><span class="sxs-lookup"><span data-stu-id="45fc8-281">A message with more details about the issue.</span></span>     |


<span id="certification-report-object" />

### <a name="certification-report-resource"></a><span data-ttu-id="45fc8-282">Ressource für Zertifizierungsberichte</span><span class="sxs-lookup"><span data-stu-id="45fc8-282">Certification report resource</span></span>

<span data-ttu-id="45fc8-283">Diese Ressource stellt den Zugriff auf die Zertifizierungsberichtsdaten für eine Übermittlung bereit.</span><span class="sxs-lookup"><span data-stu-id="45fc8-283">This resource provides access to the certification report data for a submission.</span></span> <span data-ttu-id="45fc8-284">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="45fc8-284">This resource has the following values.</span></span>

| <span data-ttu-id="45fc8-285">Wert</span><span class="sxs-lookup"><span data-stu-id="45fc8-285">Value</span></span>           | <span data-ttu-id="45fc8-286">Typ</span><span class="sxs-lookup"><span data-stu-id="45fc8-286">Type</span></span>    | <span data-ttu-id="45fc8-287">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-287">Description</span></span>         |
|-----------------|---------|------|
|     <span data-ttu-id="45fc8-288">date</span><span class="sxs-lookup"><span data-stu-id="45fc8-288">date</span></span>            |    <span data-ttu-id="45fc8-289">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-289">string</span></span>     |  <span data-ttu-id="45fc8-290">Datum und Uhrzeit, die der Bericht, im Format ISO 8601 generiert wurde.</span><span class="sxs-lookup"><span data-stu-id="45fc8-290">The date and time the report was generated, in ISO 8601 format.</span></span>    |
|     <span data-ttu-id="45fc8-291">reportUrl</span><span class="sxs-lookup"><span data-stu-id="45fc8-291">reportUrl</span></span>            |    <span data-ttu-id="45fc8-292">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-292">string</span></span>     |  <span data-ttu-id="45fc8-293">Die URL, unter der Sie auf den Bericht zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="45fc8-293">The URL at which you can access the report.</span></span>    |


<span id="flight-package-object" />

### <a name="flight-package-resource"></a><span data-ttu-id="45fc8-294">Flight-Paket-Ressource</span><span class="sxs-lookup"><span data-stu-id="45fc8-294">Flight package resource</span></span>

<span data-ttu-id="45fc8-295">Diese Ressource enthält Details zu einem Paket in einer Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-295">This resource provides details about a package in a submission.</span></span>

```json
{
  "flightPackages": [
    {
      "fileName": "newPackage.appx",
      "fileStatus": "PendingUpload",
      "id": "",
      "version": "1.0.0.0",
      "languages": ["en-us"],
      "capabilities": [],
      "minimumDirectXVersion": "None",
      "minimumSystemRam": "None"
    }
  ],
}
```

<span data-ttu-id="45fc8-296">Diese Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="45fc8-296">This resource has the following values.</span></span>

> [!NOTE]
> <span data-ttu-id="45fc8-297">Beim Aufruf der Methode für das [Aktualisieren einer Flight-Paket-Übermittlung](update-a-flight-submission.md) sind im Anforderungstext nur die Werte *fileName*, *fileStatus*, *minimumDirectXVersion* und *minimumSystemRam* dieses Objekts erforderlich.</span><span class="sxs-lookup"><span data-stu-id="45fc8-297">When calling the [update a package flight submission](update-a-flight-submission.md) method, only the *fileName*, *fileStatus*, *minimumDirectXVersion*, and *minimumSystemRam* values of this object are required in the request body.</span></span> <span data-ttu-id="45fc8-298">Die anderen Werte werden von Partner Center aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="45fc8-298">The other values are populated by Partner Center.</span></span>

| <span data-ttu-id="45fc8-299">Wert</span><span class="sxs-lookup"><span data-stu-id="45fc8-299">Value</span></span>           | <span data-ttu-id="45fc8-300">Typ</span><span class="sxs-lookup"><span data-stu-id="45fc8-300">Type</span></span>    | <span data-ttu-id="45fc8-301">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-301">Description</span></span>              |
|-----------------|---------|------|
| <span data-ttu-id="45fc8-302">fileName</span><span class="sxs-lookup"><span data-stu-id="45fc8-302">fileName</span></span>   |   <span data-ttu-id="45fc8-303">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-303">string</span></span>      |  <span data-ttu-id="45fc8-304">Der Name des Pakets.</span><span class="sxs-lookup"><span data-stu-id="45fc8-304">The name of the package.</span></span>    |  
| <span data-ttu-id="45fc8-305">fileStatus</span><span class="sxs-lookup"><span data-stu-id="45fc8-305">fileStatus</span></span>    | <span data-ttu-id="45fc8-306">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-306">string</span></span>    |  <span data-ttu-id="45fc8-307">Der Status des Pakets.</span><span class="sxs-lookup"><span data-stu-id="45fc8-307">The status of the package.</span></span> <span data-ttu-id="45fc8-308">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="45fc8-308">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="45fc8-309">None</span><span class="sxs-lookup"><span data-stu-id="45fc8-309">None</span></span></li><li><span data-ttu-id="45fc8-310">PendingUpload</span><span class="sxs-lookup"><span data-stu-id="45fc8-310">PendingUpload</span></span></li><li><span data-ttu-id="45fc8-311">Uploaded</span><span class="sxs-lookup"><span data-stu-id="45fc8-311">Uploaded</span></span></li><li><span data-ttu-id="45fc8-312">PendingDelete</span><span class="sxs-lookup"><span data-stu-id="45fc8-312">PendingDelete</span></span></li></ul>    |  
| <span data-ttu-id="45fc8-313">id</span><span class="sxs-lookup"><span data-stu-id="45fc8-313">id</span></span>    |  <span data-ttu-id="45fc8-314">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-314">string</span></span>   |  <span data-ttu-id="45fc8-315">Eine ID, die das Paket eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="45fc8-315">An ID that uniquely identifies the package.</span></span> <span data-ttu-id="45fc8-316">Dieser Wert wird von Partner Center verwendet.</span><span class="sxs-lookup"><span data-stu-id="45fc8-316">This value is used by Partner Center.</span></span>   |     
| <span data-ttu-id="45fc8-317">version</span><span class="sxs-lookup"><span data-stu-id="45fc8-317">version</span></span>    |  <span data-ttu-id="45fc8-318">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-318">string</span></span>   |  <span data-ttu-id="45fc8-319">Die Version des App-Pakets.</span><span class="sxs-lookup"><span data-stu-id="45fc8-319">The version of the app package.</span></span> <span data-ttu-id="45fc8-320">Weitere Informationen finden Sie unter [Paketversionsnummern](https://msdn.microsoft.com/windows/uwp/publish/package-version-numbering).</span><span class="sxs-lookup"><span data-stu-id="45fc8-320">For more information, see [Package version numbering](https://msdn.microsoft.com/windows/uwp/publish/package-version-numbering).</span></span>   |   
| <span data-ttu-id="45fc8-321">architecture</span><span class="sxs-lookup"><span data-stu-id="45fc8-321">architecture</span></span>    |  <span data-ttu-id="45fc8-322">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-322">string</span></span>   |  <span data-ttu-id="45fc8-323">Die Architektur des App-Pakets (z.B. ARM).</span><span class="sxs-lookup"><span data-stu-id="45fc8-323">The architecture of the app package (for example, ARM).</span></span>   |     
| <span data-ttu-id="45fc8-324">languages</span><span class="sxs-lookup"><span data-stu-id="45fc8-324">languages</span></span>    | <span data-ttu-id="45fc8-325">array</span><span class="sxs-lookup"><span data-stu-id="45fc8-325">array</span></span>    |  <span data-ttu-id="45fc8-326">Ein Array von Sprachcodes für die Sprachen, die von der App unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="45fc8-326">An array of language codes for the languages the app supports.</span></span> <span data-ttu-id="45fc8-327">Weitere Informationen finden Sie unter [Unterstützte Sprachen](https://msdn.microsoft.com/windows/uwp/publish/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="45fc8-327">For more information, see For more information, see [Supported languages](https://msdn.microsoft.com/windows/uwp/publish/supported-languages).</span></span>    |     
| <span data-ttu-id="45fc8-328">capabilities</span><span class="sxs-lookup"><span data-stu-id="45fc8-328">capabilities</span></span>    |  <span data-ttu-id="45fc8-329">array</span><span class="sxs-lookup"><span data-stu-id="45fc8-329">array</span></span>   |  <span data-ttu-id="45fc8-330">Ein Array von Funktionen, die für das Paket erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="45fc8-330">An array of capabilities required by the package.</span></span> <span data-ttu-id="45fc8-331">Weitere Informationen zu Funktionen finden Sie unter [Deklaration der App-Funktionen](https://msdn.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span><span class="sxs-lookup"><span data-stu-id="45fc8-331">For more information about capabilities, see [App capability declarations](https://msdn.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span></span>   |     
| <span data-ttu-id="45fc8-332">minimumDirectXVersion</span><span class="sxs-lookup"><span data-stu-id="45fc8-332">minimumDirectXVersion</span></span>    |  <span data-ttu-id="45fc8-333">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-333">string</span></span>   |  <span data-ttu-id="45fc8-334">Die DirectX-Version, die vom App-Paket mindestens unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="45fc8-334">The minimum DirectX version that is supported by the app package.</span></span> <span data-ttu-id="45fc8-335">Dieser Wert kann nur für Apps festgelegt werden, die für Windows8.x bestimmt sind. Im Fall von Apps, die für andere Versionen bestimmt sind, wird er ignoriert.</span><span class="sxs-lookup"><span data-stu-id="45fc8-335">This can be set only for apps that target Windows 8.x; it is ignored for apps that target other versions.</span></span> <span data-ttu-id="45fc8-336">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="45fc8-336">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="45fc8-337">None</span><span class="sxs-lookup"><span data-stu-id="45fc8-337">None</span></span></li><li><span data-ttu-id="45fc8-338">DirectX93</span><span class="sxs-lookup"><span data-stu-id="45fc8-338">DirectX93</span></span></li><li><span data-ttu-id="45fc8-339">DirectX100</span><span class="sxs-lookup"><span data-stu-id="45fc8-339">DirectX100</span></span></li></ul>   |     
| <span data-ttu-id="45fc8-340">minimumSystemRam</span><span class="sxs-lookup"><span data-stu-id="45fc8-340">minimumSystemRam</span></span>    | <span data-ttu-id="45fc8-341">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-341">string</span></span>    |  <span data-ttu-id="45fc8-342">Die Menge an RAM, die für das App-Paket mindestens erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="45fc8-342">The minimum RAM that is required by the app package.</span></span> <span data-ttu-id="45fc8-343">Dieser Wert kann nur für Apps festgelegt werden, die für Windows8.x bestimmt sind. Im Fall von Apps, die für andere Versionen bestimmt sind, wird er ignoriert.</span><span class="sxs-lookup"><span data-stu-id="45fc8-343">This can be set only for apps that target Windows 8.x; it is ignored for apps that target other versions.</span></span> <span data-ttu-id="45fc8-344">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="45fc8-344">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="45fc8-345">None</span><span class="sxs-lookup"><span data-stu-id="45fc8-345">None</span></span></li><li><span data-ttu-id="45fc8-346">Memory2GB</span><span class="sxs-lookup"><span data-stu-id="45fc8-346">Memory2GB</span></span></li></ul>   |    


<span id="package-delivery-options-object" />

### <a name="package-delivery-options-resource"></a><span data-ttu-id="45fc8-347">Ressource für Paketübermittlungsoptionen</span><span class="sxs-lookup"><span data-stu-id="45fc8-347">Package delivery options resource</span></span>

<span data-ttu-id="45fc8-348">Diese Ressource enthält Einstellungen zu graduellen Paketrollouts und zu verpflichtenden Updates für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-348">This resource contains gradual package rollout and mandatory update settings for the submission.</span></span>

```json
{
  "packageDeliveryOptions": {
    "packageRollout": {
        "isPackageRollout": false,
        "packageRolloutPercentage": 0.0,
        "packageRolloutStatus": "PackageRolloutNotStarted",
        "fallbackSubmissionId": "0"
    },
    "isMandatoryUpdate": false,
    "mandatoryUpdateEffectiveDate": "1601-01-01T00:00:00.0000000Z"
  },
}
```

<span data-ttu-id="45fc8-349">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="45fc8-349">This resource has the following values.</span></span>

| <span data-ttu-id="45fc8-350">Wert</span><span class="sxs-lookup"><span data-stu-id="45fc8-350">Value</span></span>           | <span data-ttu-id="45fc8-351">Typ</span><span class="sxs-lookup"><span data-stu-id="45fc8-351">Type</span></span>    | <span data-ttu-id="45fc8-352">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-352">Description</span></span>        |
|-----------------|---------|------|
| <span data-ttu-id="45fc8-353">packageRollout</span><span class="sxs-lookup"><span data-stu-id="45fc8-353">packageRollout</span></span>   |   <span data-ttu-id="45fc8-354">object</span><span class="sxs-lookup"><span data-stu-id="45fc8-354">object</span></span>      |   <span data-ttu-id="45fc8-355">Eine [Ressource für Paketrollouts](#package-rollout-object), die Einstellungen zu graduellen Paketrollouts für die Übermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="45fc8-355">A [package rollout resource](#package-rollout-object) that contains gradual package rollout settings for the submission.</span></span>    |  
| <span data-ttu-id="45fc8-356">isMandatoryUpdate</span><span class="sxs-lookup"><span data-stu-id="45fc8-356">isMandatoryUpdate</span></span>    | <span data-ttu-id="45fc8-357">boolean</span><span class="sxs-lookup"><span data-stu-id="45fc8-357">boolean</span></span>    |  <span data-ttu-id="45fc8-358">Gibt an, ob die Pakete in dieser Übermittlung für automatisch installierte App-Updates als verpflichtend behandelt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-358">Indicates whether you want to treat the packages in this submission as mandatory for self-installing app updates.</span></span> <span data-ttu-id="45fc8-359">Weitere Informationen zu verpflichtenden Paketen für automatisch installierte App-Aktualisierungen finden Sie unter [Herunterladen und Installieren von Paketupdates für Ihre App](../packaging/self-install-package-updates.md).</span><span class="sxs-lookup"><span data-stu-id="45fc8-359">For more information about mandatory packages for self-installing app updates, see [Download and install package updates for your app](../packaging/self-install-package-updates.md).</span></span>    |  
| <span data-ttu-id="45fc8-360">mandatoryUpdateEffectiveDate</span><span class="sxs-lookup"><span data-stu-id="45fc8-360">mandatoryUpdateEffectiveDate</span></span>    |  <span data-ttu-id="45fc8-361">date</span><span class="sxs-lookup"><span data-stu-id="45fc8-361">date</span></span>   |  <span data-ttu-id="45fc8-362">Zeitpunkt (Datum und Uhrzeit), zu dem die Pakete in dieser Übermittlung verpflichtend werden, im ISO 8601-Format und gemäß UTC-Zeitzone.</span><span class="sxs-lookup"><span data-stu-id="45fc8-362">The date and time when the packages in this submission become mandatory, in ISO 8601 format and UTC time zone.</span></span>   |        

<span id="package-rollout-object" />

### <a name="package-rollout-resource"></a><span data-ttu-id="45fc8-363">Ressource für Paketrollouts</span><span class="sxs-lookup"><span data-stu-id="45fc8-363">Package rollout resource</span></span>

<span data-ttu-id="45fc8-364">Diese Ressource enthält [Einstellungen für graduelle Paketrollouts](#manage-gradual-package-rollout) für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45fc8-364">This resource contains gradual [package rollout settings](#manage-gradual-package-rollout) for the submission.</span></span> <span data-ttu-id="45fc8-365">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="45fc8-365">This resource has the following values.</span></span>

| <span data-ttu-id="45fc8-366">Wert</span><span class="sxs-lookup"><span data-stu-id="45fc8-366">Value</span></span>           | <span data-ttu-id="45fc8-367">Typ</span><span class="sxs-lookup"><span data-stu-id="45fc8-367">Type</span></span>    | <span data-ttu-id="45fc8-368">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-368">Description</span></span>        |
|-----------------|---------|------|
| <span data-ttu-id="45fc8-369">isPackageRollout</span><span class="sxs-lookup"><span data-stu-id="45fc8-369">isPackageRollout</span></span>   |   <span data-ttu-id="45fc8-370">boolean</span><span class="sxs-lookup"><span data-stu-id="45fc8-370">boolean</span></span>      |  <span data-ttu-id="45fc8-371">Gibt an, ob für die Übermittlung der graduelle Paketrollout aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="45fc8-371">Indicates whether gradual package rollout is enabled for the submission.</span></span>    |  
| <span data-ttu-id="45fc8-372">packageRolloutPercentage</span><span class="sxs-lookup"><span data-stu-id="45fc8-372">packageRolloutPercentage</span></span>    | <span data-ttu-id="45fc8-373">float</span><span class="sxs-lookup"><span data-stu-id="45fc8-373">float</span></span>    |  <span data-ttu-id="45fc8-374">Der Prozentsatz der Benutzer, die im Rahmen des graduellen Paketrollouts die Pakete erhalten.</span><span class="sxs-lookup"><span data-stu-id="45fc8-374">The percentage of users who will receive the packages in the gradual rollout.</span></span>    |  
| <span data-ttu-id="45fc8-375">packageRolloutStatus</span><span class="sxs-lookup"><span data-stu-id="45fc8-375">packageRolloutStatus</span></span>    |  <span data-ttu-id="45fc8-376">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-376">string</span></span>   |  <span data-ttu-id="45fc8-377">Eine der folgenden Zeichenfolgen, die den Status des graduellen Paketrollouts angeben:</span><span class="sxs-lookup"><span data-stu-id="45fc8-377">One of the following strings that indicates the status of the gradual package rollout:</span></span> <ul><li><span data-ttu-id="45fc8-378">PackageRolloutNotStarted</span><span class="sxs-lookup"><span data-stu-id="45fc8-378">PackageRolloutNotStarted</span></span></li><li><span data-ttu-id="45fc8-379">PackageRolloutInProgress</span><span class="sxs-lookup"><span data-stu-id="45fc8-379">PackageRolloutInProgress</span></span></li><li><span data-ttu-id="45fc8-380">PackageRolloutComplete</span><span class="sxs-lookup"><span data-stu-id="45fc8-380">PackageRolloutComplete</span></span></li><li><span data-ttu-id="45fc8-381">PackageRolloutStopped</span><span class="sxs-lookup"><span data-stu-id="45fc8-381">PackageRolloutStopped</span></span></li></ul>  |  
| <span data-ttu-id="45fc8-382">fallbackSubmissionId</span><span class="sxs-lookup"><span data-stu-id="45fc8-382">fallbackSubmissionId</span></span>    |  <span data-ttu-id="45fc8-383">string</span><span class="sxs-lookup"><span data-stu-id="45fc8-383">string</span></span>   |  <span data-ttu-id="45fc8-384">Die ID der Übermittlung, die die Kunden erhalten, die keine Pakete im Rahmen des graduellen Paketrollouts erhalten.</span><span class="sxs-lookup"><span data-stu-id="45fc8-384">The ID of the submission that will be received by customers who do not get the gradual rollout packages.</span></span>   |          

> [!NOTE]
> <span data-ttu-id="45fc8-385">Die *PackageRolloutStatus* und *FallbackSubmissionId* -Werte werden von Partner Center zugewiesen und sollen nicht vom Entwickler festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="45fc8-385">The *packageRolloutStatus* and *fallbackSubmissionId* values are assigned by Partner Center, and are not intended to be set by the developer.</span></span> <span data-ttu-id="45fc8-386">Wenn Sie diese Werte in einen Anforderungstext einfügen, werden diese Werte ignoriert.</span><span class="sxs-lookup"><span data-stu-id="45fc8-386">If you include these values in a request body, these values will be ignored.</span></span>

<span/>

## <a name="enums"></a><span data-ttu-id="45fc8-387">Enumerationen</span><span class="sxs-lookup"><span data-stu-id="45fc8-387">Enums</span></span>

<span data-ttu-id="45fc8-388">Diese Methoden verwenden die folgenden Enumerationen.</span><span class="sxs-lookup"><span data-stu-id="45fc8-388">These methods use the following enums.</span></span>

<span id="submission-status-code" />

### <a name="submission-status-code"></a><span data-ttu-id="45fc8-389">Übermittlungsstatuscode</span><span class="sxs-lookup"><span data-stu-id="45fc8-389">Submission status code</span></span>

<span data-ttu-id="45fc8-390">Die folgenden Codes stellen den Status einer Übermittlung dar.</span><span class="sxs-lookup"><span data-stu-id="45fc8-390">The following codes represent the status of a submission.</span></span>

| <span data-ttu-id="45fc8-391">Code</span><span class="sxs-lookup"><span data-stu-id="45fc8-391">Code</span></span>           |  <span data-ttu-id="45fc8-392">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45fc8-392">Description</span></span>      |
|-----------------|---------------|
|  <span data-ttu-id="45fc8-393">None</span><span class="sxs-lookup"><span data-stu-id="45fc8-393">None</span></span>            |     <span data-ttu-id="45fc8-394">Es wurde kein Code angegeben.</span><span class="sxs-lookup"><span data-stu-id="45fc8-394">No code was specified.</span></span>         |     
|      <span data-ttu-id="45fc8-395">InvalidArchive</span><span class="sxs-lookup"><span data-stu-id="45fc8-395">InvalidArchive</span></span>        |     <span data-ttu-id="45fc8-396">Das ZIP-Archiv, das das Paket enthält, ist ungültig oder hat ein unbekanntes Archivformat.</span><span class="sxs-lookup"><span data-stu-id="45fc8-396">The ZIP archive containing the package is invalid or has an unrecognized archive format.</span></span>  |
| <span data-ttu-id="45fc8-397">MissingFiles</span><span class="sxs-lookup"><span data-stu-id="45fc8-397">MissingFiles</span></span> | <span data-ttu-id="45fc8-398">Das ZIP-Archiv enthält nicht alle Dateien, die in den Übermittlungsdaten aufgeführt sind, oder sie befinden sich am falschen Speicherort im Archiv.</span><span class="sxs-lookup"><span data-stu-id="45fc8-398">The ZIP archive does not have all files which were listed in your submission data, or they are in the wrong location in the archive.</span></span> |
| <span data-ttu-id="45fc8-399">PackageValidationFailed</span><span class="sxs-lookup"><span data-stu-id="45fc8-399">PackageValidationFailed</span></span> | <span data-ttu-id="45fc8-400">Mindestens ein Paket in der Übermittlung konnte nicht überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="45fc8-400">One or more packages in your submission failed to validate.</span></span> |
| <span data-ttu-id="45fc8-401">InvalidParameterValue</span><span class="sxs-lookup"><span data-stu-id="45fc8-401">InvalidParameterValue</span></span> | <span data-ttu-id="45fc8-402">Einer der Parameter im Anforderungstext ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="45fc8-402">One of the parameters in the request body is invalid.</span></span> |
| <span data-ttu-id="45fc8-403">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="45fc8-403">InvalidOperation</span></span> | <span data-ttu-id="45fc8-404">Der von Ihnen versuchte Vorgang ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="45fc8-404">The operation you attempted is invalid.</span></span> |
| <span data-ttu-id="45fc8-405">InvalidState</span><span class="sxs-lookup"><span data-stu-id="45fc8-405">InvalidState</span></span> | <span data-ttu-id="45fc8-406">Der von Ihnen versuchte Vorgang ist für den aktuellen Zustand des Flight-Pakets ungültig.</span><span class="sxs-lookup"><span data-stu-id="45fc8-406">The operation you attempted is not valid for the current state of the package flight.</span></span> |
| <span data-ttu-id="45fc8-407">ResourceNotFound</span><span class="sxs-lookup"><span data-stu-id="45fc8-407">ResourceNotFound</span></span> | <span data-ttu-id="45fc8-408">Das angegebene Flight-Paket konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="45fc8-408">The specified package flight could not be found.</span></span> |
| <span data-ttu-id="45fc8-409">ServiceError</span><span class="sxs-lookup"><span data-stu-id="45fc8-409">ServiceError</span></span> | <span data-ttu-id="45fc8-410">Ein interner Dienstfehler hat verhindert, dass die Anforderung erfolgreich ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="45fc8-410">An internal service error prevented the request from succeeding.</span></span> <span data-ttu-id="45fc8-411">Führen Sie die Anforderung erneut aus.</span><span class="sxs-lookup"><span data-stu-id="45fc8-411">Try the request again.</span></span> |
| <span data-ttu-id="45fc8-412">ListingOptOutWarning</span><span class="sxs-lookup"><span data-stu-id="45fc8-412">ListingOptOutWarning</span></span> | <span data-ttu-id="45fc8-413">Der Entwickler hat einen Eintrag aus einer vorherigen Übermittlung entfernt oder Eintragsinformationen nicht hinzugefügt, die vom Paket unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="45fc8-413">The developer removed a listing from a previous submission, or did not include listing information that is supported by the package.</span></span> |
| <span data-ttu-id="45fc8-414">ListingOptInWarning</span><span class="sxs-lookup"><span data-stu-id="45fc8-414">ListingOptInWarning</span></span>  | <span data-ttu-id="45fc8-415">Der Entwickler hat einen Eintrag hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="45fc8-415">The developer added a listing.</span></span> |
| <span data-ttu-id="45fc8-416">UpdateOnlyWarning</span><span class="sxs-lookup"><span data-stu-id="45fc8-416">UpdateOnlyWarning</span></span> | <span data-ttu-id="45fc8-417">Der Entwickler versucht, etwas einzufügen, für das nur Aktualisierungsunterstützung verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="45fc8-417">The developer is trying to insert something that only has update support.</span></span> |
| <span data-ttu-id="45fc8-418">Other</span><span class="sxs-lookup"><span data-stu-id="45fc8-418">Other</span></span>  | <span data-ttu-id="45fc8-419">Die Übermittlung befindet sich in einem nicht erkannten oder nicht kategorisierten Zustand.</span><span class="sxs-lookup"><span data-stu-id="45fc8-419">The submission is in an unrecognized or uncategorized state.</span></span> |
| <span data-ttu-id="45fc8-420">PackageValidationWarning</span><span class="sxs-lookup"><span data-stu-id="45fc8-420">PackageValidationWarning</span></span> | <span data-ttu-id="45fc8-421">Der Paketüberprüfungsvorgang hat zu einer Warnung geführt.</span><span class="sxs-lookup"><span data-stu-id="45fc8-421">The package validation process resulted in a warning.</span></span> |

<span/>

## <a name="related-topics"></a><span data-ttu-id="45fc8-422">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="45fc8-422">Related topics</span></span>

* [<span data-ttu-id="45fc8-423">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="45fc8-423">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="45fc8-424">Verwalten von Flight-Paketen mithilfe der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="45fc8-424">Manage package flights using the Microsoft Store submission API</span></span>](manage-flights.md)
* [<span data-ttu-id="45fc8-425">Abrufen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-425">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="45fc8-426">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-426">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="45fc8-427">Aktualisieren einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-427">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="45fc8-428">Ausführen eines Commit für eine Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-428">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="45fc8-429">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-429">Delete a package flight submission</span></span>](delete-a-flight-submission.md)
* [<span data-ttu-id="45fc8-430">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="45fc8-430">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
