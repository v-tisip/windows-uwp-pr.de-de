---
author: Xansky
ms.assetid: 4920D262-B810-409E-BA3A-F68AADF1B1BC
description: Verwenden Sie die Java-Codebeispiele in diesem Abschnitt, um mehr über die Verwendung der Microsoft Store-Übermittlungs-API zu erfahren.
title: 'Java-Beispiel: Übermittlungen für Apps, Add-Ons und Flights'
ms.author: mhopkins
ms.date: 07/10/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Codebeispiele, Java
ms.localizationpriority: medium
ms.openlocfilehash: 4a0df9fe873ab7d7330e06a18bb1816df3157d7a
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6039084"
---
# <a name="java-sample-submissions-for-apps-add-ons-and-flights"></a><span data-ttu-id="7c7de-104">Java-Beispiel: Übermittlungen für Apps, Add-Ons und Flights</span><span class="sxs-lookup"><span data-stu-id="7c7de-104">Java sample: submissions for apps, add-ons, and flights</span></span>

<span data-ttu-id="7c7de-105">Dieser Artikel enthält Java-Codebeispiele zeigt das Verwenden der [Microsoft Store-Übermittlungs-API](create-and-manage-submissions-using-windows-store-services.md) für diese Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="7c7de-105">This article provides Java code examples that demonstrate how to use the [Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md) for these tasks:</span></span>

* [<span data-ttu-id="7c7de-106">Abrufen eines Azure AD-Zugriffstokens</span><span class="sxs-lookup"><span data-stu-id="7c7de-106">Obtain an Azure AD access token</span></span>](#token)
* [<span data-ttu-id="7c7de-107">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="7c7de-107">Create an add-on</span></span>](#create-add-on)
* [<span data-ttu-id="7c7de-108">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="7c7de-108">Create a package flight</span></span>](#create-package-flight)
* [<span data-ttu-id="7c7de-109">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7c7de-109">Create an app submission</span></span>](#create-app-submission)
* [<span data-ttu-id="7c7de-110">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7c7de-110">Create an add-on submission</span></span>](#create-add-on-submission)
* [<span data-ttu-id="7c7de-111">Erstellen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7c7de-111">Create a package flight submission</span></span>](#create-flight-submission)

<span data-ttu-id="7c7de-112">Sie können die einzelnen Beispiele durchgehen, um mehr über die jeweilige Aufgabe zu erfahren. Zudem können Sie alle Codebeispiele in diesem Artikel in eine Konsolenanwendung einbinden.</span><span class="sxs-lookup"><span data-stu-id="7c7de-112">You can review each example to learn more about the task it demonstrates, or you can build all the code examples in this article into a console application.</span></span> <span data-ttu-id="7c7de-113">Die vollständige Codeauflistung finden Sie im Abschnitt [Codeauflistung](java-code-examples-for-the-windows-store-submission-api.md#code-listing) am Ende dieses Artikels.</span><span class="sxs-lookup"><span data-stu-id="7c7de-113">For the complete code listing, see the [code listing](java-code-examples-for-the-windows-store-submission-api.md#code-listing) section at the end of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c7de-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="7c7de-114">Prerequisites</span></span>

<span data-ttu-id="7c7de-115">Für diese Beispiele werden die folgenden Bibliotheken verwendet:</span><span class="sxs-lookup"><span data-stu-id="7c7de-115">These examples use the following libraries:</span></span>

* <span data-ttu-id="7c7de-116">[Apache Commons Logging 1.2](http://commons.apache.org/proper/commons-logging)  (commons-logging-1.2.jar)</span><span class="sxs-lookup"><span data-stu-id="7c7de-116">[Apache Commons Logging 1.2](http://commons.apache.org/proper/commons-logging)  (commons-logging-1.2.jar).</span></span>
* <span data-ttu-id="7c7de-117">[Apache HttpComponents Core 4.4.5 und Apache HttpComponents Client 4.5.2](https://hc.apache.org/) (httpcore-4.4.5.jar und httpclient-4.5.2.jar)</span><span class="sxs-lookup"><span data-stu-id="7c7de-117">[Apache HttpComponents Core 4.4.5 and Apache HttpComponents Client 4.5.2](https://hc.apache.org/) (httpcore-4.4.5.jar and httpclient-4.5.2.jar).</span></span>
* <span data-ttu-id="7c7de-118">[JSR 353 JSON Processing API 1.0](https://mvnrepository.com/artifact/javax.json/javax.json-api/1.0) und [JSR 353 JSON Processing Default Provider API 1.0.4](https://mvnrepository.com/artifact/org.glassfish/javax.json/1.0.4) (javax.json-api-1.0.jar und javax.json-1.0.4.jar)</span><span class="sxs-lookup"><span data-stu-id="7c7de-118">[JSR 353 JSON Processing API 1.0](https://mvnrepository.com/artifact/javax.json/javax.json-api/1.0) and [JSR 353 JSON Processing Default Provider API 1.0.4](https://mvnrepository.com/artifact/org.glassfish/javax.json/1.0.4) (javax.json-api-1.0.jar and javax.json-1.0.4.jar).</span></span>

## <a name="main-program-and-imports"></a><span data-ttu-id="7c7de-119">Hauptprogramm und Importe</span><span class="sxs-lookup"><span data-stu-id="7c7de-119">Main program and imports</span></span>

<span data-ttu-id="7c7de-120">Das folgende Beispiel zeigt die Importanweisungen, die von allen Codebeispielen verwendet werden, und implementiert ein Befehlszeilenprogramm, das die anderen Beispielmethoden aufruft.</span><span class="sxs-lookup"><span data-stu-id="7c7de-120">The following example shows the imports statements used by all of the code examples and implements a command line program that calls the other example methods.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/MainExample.java#L1-L64)]

<span id="token" />

## <a name="obtain-an-azure-ad-access-token"></a><span data-ttu-id="7c7de-121">Abrufen eines Azure AD-Zugriffstokens</span><span class="sxs-lookup"><span data-stu-id="7c7de-121">Obtain an Azure AD access token</span></span>

<span data-ttu-id="7c7de-122">Im folgenden Beispiel wird gezeigt, wie Sie ein [Azure AD-Zugriffstoken abrufen](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), mit dem Sie Methoden in der Microsoft Store-Übermittlungs-API aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="7c7de-122">The following example demonstrates how to [obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) that you can use to call methods in the Microsoft Store submission API.</span></span> <span data-ttu-id="7c7de-123">Nach dem Abruf eines Tokens können Sie es für einen Zeitraum von 60Minuten in Aufrufen der Microsoft Store-Übermittlungs-API verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="7c7de-123">After you obtain a token, you have 60 minutes to use this token in calls to the Microsoft Store submission API before the token expires.</span></span> <span data-ttu-id="7c7de-124">Nach dem Ablauf des Tokens können Sie ein neues Token generieren.</span><span class="sxs-lookup"><span data-stu-id="7c7de-124">After the token expires, you can generate a new token.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/CompleteExample.java#L65-L95)]

<span id="create-add-on" />

## <a name="create-an-add-on"></a><span data-ttu-id="7c7de-125">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="7c7de-125">Create an add-on</span></span>

<span data-ttu-id="7c7de-126">Das folgende Beispiel zeigt, wie Sie EIN Flight-Paket [erstellen](create-an-add-on.md) und anschließend ein Add-On [löschen](delete-an-add-on.md).</span><span class="sxs-lookup"><span data-stu-id="7c7de-126">The following example demonstrates how to [create](create-an-add-on.md) and then [delete](delete-an-add-on.md) an add-on.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/CompleteExample.java#L310-L345)]

<span id="create-package-flight" />

## <a name="create-a-package-flight"></a><span data-ttu-id="7c7de-127">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="7c7de-127">Create a package flight</span></span>

<span data-ttu-id="7c7de-128">Das folgende Beispiel zeigt, wie Sie EIN Flight-Paket [erstellen](create-a-flight.md) und anschließend [löschen](delete-a-flight.md).</span><span class="sxs-lookup"><span data-stu-id="7c7de-128">The following example demonstrates how to [create](create-a-flight.md) and then [delete](delete-a-flight.md) a package flight.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/CompleteExample.java#L185-L221)]

<span id="create-app-submission" />

## <a name="create-an-app-submission"></a><span data-ttu-id="7c7de-129">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7c7de-129">Create an app submission</span></span>

<span data-ttu-id="7c7de-130">Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Microsoft Store-Übermittlungs-API verwenden, um eine App-Übermittlung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c7de-130">The following example shows how to use several methods in the Microsoft Store submission API to create an app submission.</span></span> <span data-ttu-id="7c7de-131">Dazu die ```SubmitNewApplicationSubmission``` Methode erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung und anschließend aktualisiert und sendet die geklonte Übermittlung für das Partner Center.</span><span class="sxs-lookup"><span data-stu-id="7c7de-131">To do this, the ```SubmitNewApplicationSubmission``` method creates a new submission as a clone of the last published submission, and then it updates and commits the cloned submission to Partner Center.</span></span> <span data-ttu-id="7c7de-132">Genauer gesagt führt die ```SubmitNewApplicationSubmission```-Methode diese Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="7c7de-132">Specifically, the ```SubmitNewApplicationSubmission``` method performs these tasks:</span></span>

1. <span data-ttu-id="7c7de-133">Zunächst [ruft die Methode Daten für die angegebene App ab](get-an-app.md).</span><span class="sxs-lookup"><span data-stu-id="7c7de-133">To begin, the method [gets data for the specified app](get-an-app.md).</span></span>
2. <span data-ttu-id="7c7de-134">Als Nächstes [löscht sie die ausstehende Übermittlung für die App](delete-an-app-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="7c7de-134">Next, it [deletes the pending submission for the app](delete-an-app-submission.md), if one exists.</span></span>
3. <span data-ttu-id="7c7de-135">Anschließend [wird eine neue Übermittlung für die App erstellt](create-an-app-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="7c7de-135">It then [creates a new submission for the app](create-an-app-submission.md) (the new submission is a copy of the last published submission).</span></span>
4. <span data-ttu-id="7c7de-136">Es werden einige Details für die neue Übermittlung geändert und ein neues Paket für die Übermittlung zu Azure Blob Storage hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="7c7de-136">It changes some details for the new submission and upload a new package for the submission to Azure Blob storage.</span></span>
5. <span data-ttu-id="7c7de-137">Als Nächstes wird es [Updates](update-an-app-submission.md) und anschließend auf die neue Übermittlung für das Partner Center [committet](commit-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="7c7de-137">Next, it [updates](update-an-app-submission.md) and then [commits](commit-an-app-submission.md) the new submission to Partner Center.</span></span>
6. <span data-ttu-id="7c7de-138">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-app-submission.md), bis die Übermittlung erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="7c7de-138">Finally, it periodically [checks the status of the new submission](get-status-for-an-app-submission.md) until the submission is successfully committed.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/CompleteExample.java#L97-L183)]

<span id="create-add-on-submission" />

## <a name="create-an-add-on-submission"></a><span data-ttu-id="7c7de-139">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7c7de-139">Create an add-on submission</span></span>

<span data-ttu-id="7c7de-140">Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Microsoft Store-Übermittlungs-API verwenden, um eine Add-On-Übermittlung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c7de-140">The following example shows how to use several methods in the Microsoft Store submission API to create an add-on submission.</span></span> <span data-ttu-id="7c7de-141">Dazu die ```SubmitNewInAppProductSubmission``` Methode erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, und klicken Sie dann aktualisiert und sendet die geklonte Übermittlung für das Partner Center.</span><span class="sxs-lookup"><span data-stu-id="7c7de-141">To do this, the ```SubmitNewInAppProductSubmission``` method creates a new submission as a clone of the last published submission, and then updates and commits the cloned submission to Partner Center.</span></span> <span data-ttu-id="7c7de-142">Genauer gesagt führt die ```SubmitNewInAppProductSubmission```-Methode diese Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="7c7de-142">Specifically, the ```SubmitNewInAppProductSubmission``` method performs these tasks:</span></span>

1. <span data-ttu-id="7c7de-143">Zunächst [ruft die Methode Daten für das angegebene Add-On ab](get-an-add-on.md).</span><span class="sxs-lookup"><span data-stu-id="7c7de-143">To begin, the method [gets data for the specified add-on](get-an-add-on.md).</span></span>
2. <span data-ttu-id="7c7de-144">Als Nächstes [wird eine ausstehende Übermittlung für das Add-On gelöscht](delete-an-add-on-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="7c7de-144">Next, it [deletes the pending submission for the add-on](delete-an-add-on-submission.md), if one exists.</span></span>
3. <span data-ttu-id="7c7de-145">Anschließend [wird eine neue Übermittlung für das Add-On erstellt](create-an-add-on-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="7c7de-145">It then [creates a new submission for the add-on](create-an-add-on-submission.md) (the new submission is a copy of the last published submission).</span></span>
4. <span data-ttu-id="7c7de-146">Es wird ein ZIP-Archiv hochgeladen, das Symbole für die Übermittlung an Azure Blob Storage enthält.</span><span class="sxs-lookup"><span data-stu-id="7c7de-146">It uploads a ZIP archive that contains icons for the submission to Azure Blob storage.</span></span>
5. <span data-ttu-id="7c7de-147">Als Nächstes wird es [Updates](update-an-add-on-submission.md) und anschließend auf die neue Übermittlung für das Partner Center [committet](commit-an-add-on-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="7c7de-147">Next, it [updates](update-an-add-on-submission.md) and then [commits](commit-an-add-on-submission.md) the new submission to Partner Center.</span></span>
6. <span data-ttu-id="7c7de-148">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-add-on-submission.md), bis die Übermittlung erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="7c7de-148">Finally, it periodically [checks the status of the new submission](get-status-for-an-add-on-submission.md) until the submission is successfully committed.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/CompleteExample.java#L347-L431)]

<span id="create-flight-submission" />

## <a name="create-a-package-flight-submission"></a><span data-ttu-id="7c7de-149">Erstellen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7c7de-149">Create a package flight submission</span></span>

<span data-ttu-id="7c7de-150">Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Microsoft Store-Übermittlungs-API verwenden, um eine Flight-Paket-Übermittlung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c7de-150">The following example shows how to use several methods in the Microsoft Store submission API to create a package flight submission.</span></span> <span data-ttu-id="7c7de-151">Dazu die ```SubmitNewFlightSubmission``` Methode erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, und klicken Sie dann aktualisiert und sendet die geklonte Übermittlung für das Partner Center.</span><span class="sxs-lookup"><span data-stu-id="7c7de-151">To do this, the ```SubmitNewFlightSubmission``` method creates a new submission as a clone of the last published submission, and then updates and commits the cloned submission to Partner Center.</span></span> <span data-ttu-id="7c7de-152">Genauer gesagt führt die ```SubmitNewFlightSubmission```-Methode diese Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="7c7de-152">Specifically, the ```SubmitNewFlightSubmission``` method performs these tasks:</span></span>

1. <span data-ttu-id="7c7de-153">Zunächst [ruft die Methode Daten für das angegebene Flight-Paket ab](get-a-flight.md).</span><span class="sxs-lookup"><span data-stu-id="7c7de-153">To begin, the method [gets data for the specified package flight](get-a-flight.md).</span></span>
2. <span data-ttu-id="7c7de-154">Als Nächstes [wird eine ausstehende Übermittlung für das Flight-Paket gelöscht](delete-a-flight-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="7c7de-154">Next, it [deletes the pending submission for the package flight](delete-a-flight-submission.md), if one exists.</span></span>
3. <span data-ttu-id="7c7de-155">Anschließend [wird eine neue Übermittlung für das Flight-Paket erstellt](create-a-flight-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="7c7de-155">It then [creates a new submission for the package flight](create-a-flight-submission.md) (the new submission is a copy of the last published submission).</span></span>
4. <span data-ttu-id="7c7de-156">Es wird ein neues Paket für die Übermittlung an Azure Blob Storage hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="7c7de-156">It uploads a new package for the submission to Azure Blob storage.</span></span>
5. <span data-ttu-id="7c7de-157">Als Nächstes wird es [Updates](update-a-flight-submission.md) und [führt ein Commit für](commit-a-flight-submission.md) die neue Übermittlung an PartnerCenter.</span><span class="sxs-lookup"><span data-stu-id="7c7de-157">Next, it [updates](update-a-flight-submission.md) and then [commits](commit-a-flight-submission.md) the new submission to PartnerCenter.</span></span>
6. <span data-ttu-id="7c7de-158">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-a-flight-submission.md), bis die Übermittlung erfolgreich committet wurde.</span><span class="sxs-lookup"><span data-stu-id="7c7de-158">Finally, it periodically [checks the status of the new submission](get-status-for-a-flight-submission.md) until the submission is successfully committed.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/CompleteExample.java#L223-L308)]

<span id="utilities" />

## <a name="utility-methods-to-upload-submission-files-and-handle-request-responses"></a><span data-ttu-id="7c7de-159">Hilfsmethoden zum Hochladen von Übermittlungsdateien und Behandeln von Anforderungsantworten</span><span class="sxs-lookup"><span data-stu-id="7c7de-159">Utility methods to upload submission files and handle request responses</span></span>

<span data-ttu-id="7c7de-160">Die folgenden Hilfsmethoden veranschaulichen diese Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="7c7de-160">The following utility methods demonstrate these tasks:</span></span>

* <span data-ttu-id="7c7de-161">Hochladen eines ZIP-Archivs mit neuen Ressourcen für eine App- oder Add-On-Übermittlung auf Azure Blob Storage</span><span class="sxs-lookup"><span data-stu-id="7c7de-161">How to upload a ZIP archive containing new assets for an app or add-on submission to Azure Blob storage.</span></span> <span data-ttu-id="7c7de-162">Weitere Informationen zum Hochladen eines ZIP-Archivs auf Azure Blob Storage für App- und Add-On-Übermittlungen finden Sie unter [Erstellen einer App-Übermittlung](manage-app-submissions.md#create-an-app-submission), [Erstellen einer Add-On-Übermittlung](manage-add-on-submissions.md#create-an-add-on-submission) und [Erstellen einer Flight-Paket-Übermittlung](manage-flight-submissions.md#create-a-package-flight-submission).</span><span class="sxs-lookup"><span data-stu-id="7c7de-162">For more information about uploading a ZIP archive to Azure Blob storage for app and add-on submissions, see the relevant instructions in [Create an app submission](manage-app-submissions.md#create-an-app-submission), [Create an add-on submission](manage-add-on-submissions.md#create-an-add-on-submission), and [Create a package flight submission](manage-flight-submissions.md#create-a-package-flight-submission).</span></span>
* <span data-ttu-id="7c7de-163">Behandeln von Anforderungsantworten</span><span class="sxs-lookup"><span data-stu-id="7c7de-163">How to handle request responses.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/CompleteExample.java#L433-L490)]

<span id="code-listing" />

## <a name="complete-code-listing"></a><span data-ttu-id="7c7de-164">Vollständige Codeauflistung</span><span class="sxs-lookup"><span data-stu-id="7c7de-164">Complete code listing</span></span>

<span data-ttu-id="7c7de-165">Die folgende Codeauflistung enthält alle vorherigen Beispiele in einer einzigen Quelldatei organisiert.</span><span class="sxs-lookup"><span data-stu-id="7c7de-165">The following code listing contains all of the previous examples organized into one source file.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/java/CompleteExample.java#L1-L491)]

## <a name="related-topics"></a><span data-ttu-id="7c7de-166">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7c7de-166">Related topics</span></span>

* [<span data-ttu-id="7c7de-167">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="7c7de-167">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
