---
author: Xansky
ms.assetid: FABA802F-9CB2-4894-9848-9BB040F9851F
description: Verwenden Sie die C#-Codebeispiele in diesem Abschnitt, um mehr über die Verwendung der Microsoft Store-Übermittlungs-API zu erfahren.
title: 'C#-Beispiel: Übermittlungen für Apps, Add-Ons und Flights'
ms.author: mhopkins
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Codebeispiele, C#
ms.localizationpriority: medium
ms.openlocfilehash: f5e508bd89c06841009576a0a69cb960a20faa83
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "4962588"
---
# <a name="c-sample-submissions-for-apps-add-ons-and-flights"></a><span data-ttu-id="58f64-104">C\#-Beispiel: Übermittlungen für Apps, Add-Ons und Flights</span><span class="sxs-lookup"><span data-stu-id="58f64-104">C\# sample: submissions for apps, add-ons, and flights</span></span>

<span data-ttu-id="58f64-105">Dieser Artikel enthält C#-Codebeispiele zeigt das Verwenden der [Microsoft Store-Übermittlungs-API](create-and-manage-submissions-using-windows-store-services.md) für diese Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="58f64-105">This article provides C# code examples that demonstrate how to use the [Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md) for these tasks:</span></span>

* [<span data-ttu-id="58f64-106">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="58f64-106">Create an app submission</span></span>](#create-app-submission)
* [<span data-ttu-id="58f64-107">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="58f64-107">Create an add-on submission</span></span>](#create-add-on-submission)
* [<span data-ttu-id="58f64-108">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="58f64-108">Update an add-on submission</span></span>](#update-add-on-submission)
* [<span data-ttu-id="58f64-109">Erstellen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="58f64-109">Create a package flight submission</span></span>](#create-flight-submission)

<span data-ttu-id="58f64-110">Sie können die einzelnen Beispiele prüfen, um mehr über die jeweilige Aufgabe zu erfahren. Zudem können Sie alle Codebeispiele in diesem Artikel in eine Konsolenanwendung einbinden.</span><span class="sxs-lookup"><span data-stu-id="58f64-110">You can review each example to learn more about the task it demonstrates, or you can build all the code examples in this article into a console application.</span></span> <span data-ttu-id="58f64-111">Um die Beispiele zu übernehmen, erstellen Sie in Visual Studio eine C#-Konsolenanwendung mit dem Namen **DeveloperApiCSharpSample**, kopieren Sie die einzelnen Beispiele in separate Codedateien des Projekts, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="58f64-111">To build the examples, create a C# console application named **DeveloperApiCSharpSample** in Visual Studio, copy each example to a separate code file in the project, and build the project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58f64-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="58f64-112">Prerequisites</span></span>

<span data-ttu-id="58f64-113">Für diese Beispiele werden die folgenden Bibliotheken verwendet:</span><span class="sxs-lookup"><span data-stu-id="58f64-113">These examples use the following libraries:</span></span>

* <span data-ttu-id="58f64-114">Microsoft.WindowsAzure.Storage.dll.</span><span class="sxs-lookup"><span data-stu-id="58f64-114">Microsoft.WindowsAzure.Storage.dll.</span></span> <span data-ttu-id="58f64-115">Diese Bibliothek ist im [Azure SDK für.NET](https://azure.microsoft.com/downloads/) verfügbar. Sie können jedoch auch das [WindowsAzure.Storage NuGet-Paket](https://www.nuget.org/packages/WindowsAzure.Storage) installieren.</span><span class="sxs-lookup"><span data-stu-id="58f64-115">This library is available in the [Azure SDK for .NET](https://azure.microsoft.com/downloads/), or you can obtain it by installing the [WindowsAzure.Storage NuGet package](https://www.nuget.org/packages/WindowsAzure.Storage).</span></span>
* <span data-ttu-id="58f64-116">[Newtonsoft.Json](http://www.newtonsoft.com/json) NuGet-Paket von Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="58f64-116">[Newtonsoft.Json](http://www.newtonsoft.com/json) NuGet package from Newtonsoft.</span></span>

## <a name="main-program"></a><span data-ttu-id="58f64-117">Hauptprogramm</span><span class="sxs-lookup"><span data-stu-id="58f64-117">Main program</span></span>

<span data-ttu-id="58f64-118">Mit dem folgenden Beispiel wird ein Befehlszeilenprogramm implementiert, das die anderen Beispielmethoden in diesem Artikel aufruft, um die verschiedenen Verwendungsmethoden der Microsoft Store-Übermittlungs-API aufzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="58f64-118">The following example implements a command line program that calls the other example methods in this article to demonstrate different ways to use the Microsoft Store submission API.</span></span> <span data-ttu-id="58f64-119">So passen Sie dieses Programm für eigene Zwecke an:</span><span class="sxs-lookup"><span data-stu-id="58f64-119">To adapt this program for your own use:</span></span>

* <span data-ttu-id="58f64-120">Weisen Sie die Eigenschaften ```ApplicationId```, ```InAppProductId``` und ```FlightId``` der ID der App, des Add-Ons und des Flight-Pakets zu, die bzw. das Sie verwalten möchten.</span><span class="sxs-lookup"><span data-stu-id="58f64-120">Assign the ```ApplicationId```, ```InAppProductId```, and ```FlightId``` properties to the ID of the app, add-on, and package flight you want to manage.</span></span>
* <span data-ttu-id="58f64-121">Weisen Sie die Eigenschaften ```ClientId``` und ```ClientSecret``` der Client-ID und dem Schlüssel für Ihre App zu, und ersetzen Sie die *tenantid*-Zeichenfolge in der ```TokenEndpoint```-URL durch die Mandanten-ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="58f64-121">Assign the ```ClientId``` and ```ClientSecret``` properties to the client ID and key for your app, and replace the *tenantid* string in the ```TokenEndpoint``` URL with the tenant ID for your app.</span></span> <span data-ttu-id="58f64-122">Weitere Informationen finden Sie unter [Zuordnen einer Azure AD-Anwendung zu Ihrem Windows Dev Center-Konto](create-and-manage-submissions-using-windows-store-services.md#how-to-associate-an-azure-ad-application-with-your-windows-dev-center-account).</span><span class="sxs-lookup"><span data-stu-id="58f64-122">For more information, see [How to associate an Azure AD application with your Windows Dev Center account](create-and-manage-submissions-using-windows-store-services.md#how-to-associate-an-azure-ad-application-with-your-windows-dev-center-account)</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[SubmissionApi](./code/StoreServicesExamples_Submission/cs/Program.cs#Main)]

<span id="clientconfiguration" />

## <a name="clientconfiguration-helper-class"></a><span data-ttu-id="58f64-123">ClientConfiguration-Hilfsklasse</span><span class="sxs-lookup"><span data-stu-id="58f64-123">ClientConfiguration helper class</span></span>

<span data-ttu-id="58f64-124">Die Beispiel-App verwendet die ```ClientConfiguration```-Hilfsklasse zum Übergeben von Azure Active Directory-Daten und App-Daten an die einzelnen Beispielmethoden, die die Microsoft Store-Übermittlungs-API verwenden.</span><span class="sxs-lookup"><span data-stu-id="58f64-124">The sample app uses the ```ClientConfiguration``` helper class to pass Azure Active Directory data and app data to each of the example methods that use the Microsoft Store submission API.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[SubmissionApi](./code/StoreServicesExamples_Submission/cs/ClientConfiguration.cs#ClientConfiguration)]

<span id="create-app-submission" />

## <a name="create-an-app-submission"></a><span data-ttu-id="58f64-125">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="58f64-125">Create an app submission</span></span>

<span data-ttu-id="58f64-126">Das folgende Beispiel implementiert eine Klasse, die mehrere Methoden in der Microsoft Store-Übermittlungs-API verwendet, um eine App-Übermittlung zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="58f64-126">The following example implements a class that uses several methods in the Microsoft Store submission API to update an app submission.</span></span> <span data-ttu-id="58f64-127">Die ```RunAppSubmissionUpdateSample```-Methode in der Klasse erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, aktualisiert sie und sendet die geklonte Übermittlung an Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="58f64-127">The ```RunAppSubmissionUpdateSample``` method in the class creates a new submission as a clone of the last published submission, and then it updates and commits the cloned submission to Windows Dev Center.</span></span> <span data-ttu-id="58f64-128">Genauer gesagt führt die ```RunAppSubmissionUpdateSample```-Methode diese Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="58f64-128">Specifically, the ```RunAppSubmissionUpdateSample``` method performs these tasks:</span></span>

1. <span data-ttu-id="58f64-129">Zunächst [ruft die Methode Daten für die angegebene App ab](get-an-app.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-129">To begin, the method [gets data for the specified app](get-an-app.md).</span></span>
2. <span data-ttu-id="58f64-130">Als Nächstes [löscht sie die ausstehende Übermittlung für die App](delete-an-app-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="58f64-130">Next, it [deletes the pending submission for the app](delete-an-app-submission.md), if one exists.</span></span>
3. <span data-ttu-id="58f64-131">Anschließend [wird eine neue Übermittlung für die App erstellt](create-an-app-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="58f64-131">It then [creates a new submission for the app](create-an-app-submission.md) (the new submission is a copy of the last published submission).</span></span>
4. <span data-ttu-id="58f64-132">Es werden einige Details für die neue Übermittlung geändert und ein neues Paket für die Übermittlung zu Azure Blob Storage hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="58f64-132">It changes some details for the new submission and upload a new package for the submission to Azure Blob storage.</span></span>
5. <span data-ttu-id="58f64-133">Als Nächstes wird die neue Übermittlung [aktualisiert](update-an-app-submission.md) und anschließend an Windows Dev Center [gesendet](commit-an-app-submission.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-133">Next, it [updates](update-an-app-submission.md) and then [commits](commit-an-app-submission.md) the new submission to Windows Dev Center.</span></span>
6. <span data-ttu-id="58f64-134">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-app-submission.md), bis die Übermittlung erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="58f64-134">Finally, it periodically [checks the status of the new submission](get-status-for-an-app-submission.md) until the submission is successfully committed.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[SubmissionApi](./code/StoreServicesExamples_Submission/cs/AppSubmissionUpdateSample.cs#AppSubmissionUpdateSample)]

<span id="create-add-on-submission" />

## <a name="create-an-add-on-submission"></a><span data-ttu-id="58f64-135">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="58f64-135">Create an add-on submission</span></span>

<span data-ttu-id="58f64-136">Das folgende Beispiel implementiert eine Klasse, die mehrere Methoden in der Microsoft Store-Übermittlungs-API verwendet, um eine neue Add-On-Übermittlung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="58f64-136">The following example implements a class that uses several methods in the Microsoft Store submission API to create a new add-on submission.</span></span> <span data-ttu-id="58f64-137">Die ```RunInAppProductSubmissionCreateSample```-Methode in der Klasse führt diese Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="58f64-137">The ```RunInAppProductSubmissionCreateSample``` method in the class performs these tasks:</span></span>

1. <span data-ttu-id="58f64-138">Zunächst [erstellt die Methode ein neues Add-On](create-an-add-on.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-138">To begin, the method [creates a new add-on](create-an-add-on.md).</span></span>
2. <span data-ttu-id="58f64-139">Als Nächstes [erstellt sie eine neue Übermittlung für das Add-On](create-an-add-on-submission.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-139">Next, it [creates a new submission for the add-on](create-an-add-on-submission.md).</span></span>
3. <span data-ttu-id="58f64-140">Es wird ein ZIP-Archiv hochgeladen, das Symbole für die Übermittlung in Azure Blob Storage enthält.</span><span class="sxs-lookup"><span data-stu-id="58f64-140">It uploads a ZIP archive that contains icons for the submission to Azure Blob storage.</span></span>
4. <span data-ttu-id="58f64-141">Anschließend [wird die neue Übermittlung an Windows Dev Center gesendet](commit-an-add-on-submission.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-141">Next, it [commits the new submission to Windows Dev Center](commit-an-add-on-submission.md).</span></span>
5. <span data-ttu-id="58f64-142">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-add-on-submission.md), bis die Übermittlung erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="58f64-142">Finally, it periodically [checks the status of the new submission](get-status-for-an-add-on-submission.md) until the submission is successfully committed.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[SubmissionApi](./code/StoreServicesExamples_Submission/cs/InAppProductSubmissionCreateSample.cs#InAppProductSubmissionCreateSample)]

<span id="update-add-on-submission" />

## <a name="update-an-add-on-submission"></a><span data-ttu-id="58f64-143">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="58f64-143">Update an add-on submission</span></span>

<span data-ttu-id="58f64-144">Das folgende Beispiel implementiert eine Klasse, die mehrere Methoden in der Microsoft Store-Übermittlungs-API verwendet, um eine vorhandene Add-On-Übermittlung zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="58f64-144">The following example implements a class that uses several methods in the Microsoft Store submission API to update an existing add-on submission.</span></span> <span data-ttu-id="58f64-145">Die ```RunInAppProductSubmissionUpdateSample```-Methode in der Klasse erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, aktualisiert sie und sendet die geklonte Übermittlung an Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="58f64-145">The ```RunInAppProductSubmissionUpdateSample``` method in the class creates a new submission as a clone of the last published submission, and then it updates and commits the cloned submission to Windows Dev Center.</span></span> <span data-ttu-id="58f64-146">Genauer gesagt führt die ```RunInAppProductSubmissionUpdateSample```-Methode diese Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="58f64-146">Specifically, the ```RunInAppProductSubmissionUpdateSample``` method performs these tasks:</span></span>

1. <span data-ttu-id="58f64-147">Zunächst [ruft die Methode Daten für das angegebene Add-On ab](get-an-add-on.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-147">To begin, the method [gets data for the specified add-on](get-an-add-on.md).</span></span>
2. <span data-ttu-id="58f64-148">Als Nächstes [wird eine ausstehende Übermittlung für das Add-On gelöscht](delete-an-add-on-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="58f64-148">Next, it [deletes the pending submission for the add-on](delete-an-add-on-submission.md), if one exists.</span></span>
3. <span data-ttu-id="58f64-149">Anschließend [wird eine neue Übermittlung für das Add-On erstellt](create-an-add-on-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="58f64-149">It then [creates a new submission for the add-on](create-an-add-on-submission.md) (the new submission is a copy of the last published submission).</span></span>
5. <span data-ttu-id="58f64-150">Als Nächstes wird die neue Übermittlung [aktualisiert](update-an-add-on-submission.md) und anschließend an Windows Dev Center [gesendet](commit-an-add-on-submission.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-150">Next, it [updates](update-an-add-on-submission.md) and then [commits](commit-an-add-on-submission.md) the new submission to Windows Dev Center.</span></span>
6. <span data-ttu-id="58f64-151">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-add-on-submission.md), bis die Übermittlung erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="58f64-151">Finally, it periodically [checks the status of the new submission](get-status-for-an-add-on-submission.md) until the submission is successfully committed.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[SubmissionApi](./code/StoreServicesExamples_Submission/cs/InAppProductSubmissionUpdateSample.cs#InAppProductSubmissionUpdateSample)]

<span id="create-flight-submission" />

## <a name="create-a-package-flight-submission"></a><span data-ttu-id="58f64-152">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="58f64-152">Create a package flight submission</span></span>

<span data-ttu-id="58f64-153">Das folgende Beispiel implementiert eine Klasse, die mehrere Methoden in der Microsoft Store-Übermittlungs-API verwendet, um eine Flight-Paketübermittlung zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="58f64-153">The following example implements a class that uses several methods in the Microsoft Store submission API to update a package flight submission.</span></span> <span data-ttu-id="58f64-154">Die ```RunFlightSubmissionUpdateSample```-Methode in der Klasse erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, aktualisiert sie und sendet die geklonte Übermittlung an Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="58f64-154">The ```RunFlightSubmissionUpdateSample``` method in the class creates a new submission as a clone of the last published submission, and then it updates and commits the cloned submission to Windows Dev Center.</span></span> <span data-ttu-id="58f64-155">Genauer gesagt führt die ```RunFlightSubmissionUpdateSample```-Methode diese Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="58f64-155">Specifically, the ```RunFlightSubmissionUpdateSample``` method performs these tasks:</span></span>

1. <span data-ttu-id="58f64-156">Zunächst [ruft die Methode Daten für das angegebene Flight-Paket ab](get-a-flight.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-156">To begin, the method [gets data for the specified package flight](get-a-flight.md).</span></span>
2. <span data-ttu-id="58f64-157">Als Nächstes [wird eine ausstehende Übermittlung für das Flight-Paket gelöscht](delete-a-flight-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="58f64-157">Next, it [deletes the pending submission for the package flight](delete-a-flight-submission.md), if one exists.</span></span>
3. <span data-ttu-id="58f64-158">Anschließend [wird eine neue Übermittlung für das Flight-Paket erstellt](create-a-flight-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="58f64-158">It then [creates a new submission for the package flight](create-a-flight-submission.md) (the new submission is a copy of the last published submission).</span></span>
4. <span data-ttu-id="58f64-159">Es wird ein neues Paket für die Übermittlung auf Azure Blob Storage hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="58f64-159">It uploads a new package for the submission to Azure Blob storage.</span></span>
5. <span data-ttu-id="58f64-160">Als Nächstes wird die neue Übermittlung [aktualisiert](update-a-flight-submission.md) und anschließend an Windows Dev Center [gesendet](commit-a-flight-submission.md).</span><span class="sxs-lookup"><span data-stu-id="58f64-160">Next, it [updates](update-a-flight-submission.md) and then [commits](commit-a-flight-submission.md) the new submission to Windows Dev Center.</span></span>
6. <span data-ttu-id="58f64-161">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-a-flight-submission.md), bis die Übermittlung erfolgreich committet wurde.</span><span class="sxs-lookup"><span data-stu-id="58f64-161">Finally, it periodically [checks the status of the new submission](get-status-for-a-flight-submission.md) until the submission is successfully committed.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[SubmissionApi](./code/StoreServicesExamples_Submission/cs/FlightSubmissionUpdateSample.cs#FlightSubmissionUpdateSample)]

<span id="ingestionclient" />

## <a name="ingestionclient-helper-class"></a><span data-ttu-id="58f64-162">IngestionClient-Hilfsklasse</span><span class="sxs-lookup"><span data-stu-id="58f64-162">IngestionClient helper class</span></span>

<span data-ttu-id="58f64-163">Die ```IngestionClient```-Klasse stellt Hilfsmethoden bereit, die von anderen Methoden in der Beispiel-App verwendet werden, um die folgenden Aufgaben auszuführen:</span><span class="sxs-lookup"><span data-stu-id="58f64-163">The ```IngestionClient``` class provides helper methods that are used by other methods in the sample app to perform the following tasks:</span></span>

* <span data-ttu-id="58f64-164">[Abrufen eines Azure AD-Zugriffstokens](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das zum Aufrufen von Methoden in der Microsoft Store-Übermittlungs-API verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="58f64-164">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) that can be used to call methods in the Microsoft Store submission API.</span></span> <span data-ttu-id="58f64-165">Nach dem Abruf eines Tokens können Sie es für einen Zeitraum von 60Minuten in Aufrufen der Microsoft Store-Übermittlungs-API verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="58f64-165">After you obtain a token, you have 60 minutes to use this token in calls to the Microsoft Store submission API before the token expires.</span></span> <span data-ttu-id="58f64-166">Nach dem Ablauf des Tokens können Sie ein neues Token generieren.</span><span class="sxs-lookup"><span data-stu-id="58f64-166">After the token expires, you can generate a new token.</span></span>
* <span data-ttu-id="58f64-167">Hochladen eines ZIP-Archivs mit neuen Ressourcen für eine App- oder Add-On-Übermittlung in Azure Blob Storage.</span><span class="sxs-lookup"><span data-stu-id="58f64-167">Upload a ZIP archive containing new assets for an app or add-on submission to Azure Blob storage.</span></span> <span data-ttu-id="58f64-168">Weitere Informationen zum Hochladen eines ZIP-Archivs in Azure Blob Storage für App- und Add-On-Übermittlungen finden Sie unter [Erstellen einer App-Übermittlung](manage-app-submissions.md#create-an-app-submission) und [Erstellen einer Add-On-Übermittlung](manage-add-on-submissions.md#create-an-add-on-submission).</span><span class="sxs-lookup"><span data-stu-id="58f64-168">For more information about uploading a ZIP archive to Azure Blob storage for app and add-on submissions, see the relevant instructions in [Create an app submission](manage-app-submissions.md#create-an-app-submission) and [Create an add-on submission](manage-add-on-submissions.md#create-an-add-on-submission).</span></span>
* <span data-ttu-id="58f64-169">Verarbeiten der HTTP-Anforderungen für die Microsoft Store-Übermittlung API</span><span class="sxs-lookup"><span data-stu-id="58f64-169">Process the HTTP requests for the Microsoft Store submission API.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[SubmissionApi](./code/StoreServicesExamples_Submission/cs/IngestionClient.cs#IngestionClient)]

## <a name="related-topics"></a><span data-ttu-id="58f64-170">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="58f64-170">Related topics</span></span>

* [<span data-ttu-id="58f64-171">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="58f64-171">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
