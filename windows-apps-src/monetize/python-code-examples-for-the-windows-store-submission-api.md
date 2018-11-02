---
author: Xansky
ms.assetid: 8AC56AAF-8D8C-4193-A6B3-BB5D0669D994
description: Verwenden Sie die Python-Codebeispiele in diesem Abschnitt, um mehr über die Verwendung der Microsoft Store-Übermittlungs-API zu erfahren.
title: 'Python-Beispiel: Übermittlungen für Apps, Add-Ons und Flights'
ms.author: mhopkins
ms.date: 07/10/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Codebeispiele, Python
ms.localizationpriority: medium
ms.openlocfilehash: 34d686b8e20d384da4a3db1ea3805ad082d5f8a8
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5968694"
---
# <a name="python-sample-submissions-for-apps-add-ons-and-flights"></a><span data-ttu-id="27f99-104">Python-Beispiel: Übermittlungen für Apps, Add-Ons und Flights</span><span class="sxs-lookup"><span data-stu-id="27f99-104">Python sample: submissions for apps, add-ons, and flights</span></span>

<span data-ttu-id="27f99-105">Dieser Artikel enthält Python-Codebeispiele zeigt das Verwenden der [Microsoft Store-Übermittlungs-API](create-and-manage-submissions-using-windows-store-services.md) für diese Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="27f99-105">This article provides Python code examples that demonstrate how to use the [Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md) for these tasks:</span></span>

* [<span data-ttu-id="27f99-106">Abrufen eines Azure AD-Zugriffstokens</span><span class="sxs-lookup"><span data-stu-id="27f99-106">Obtain an Azure AD access token</span></span>](#token)
* [<span data-ttu-id="27f99-107">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="27f99-107">Create an add-on</span></span>](#create-add-on)
* [<span data-ttu-id="27f99-108">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="27f99-108">Create a package flight</span></span>](#create-package-flight)
* [<span data-ttu-id="27f99-109">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="27f99-109">Create an app submission</span></span>](#create-app-submission)
* [<span data-ttu-id="27f99-110">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="27f99-110">Create an add-on submission</span></span>](#create-add-on-submission)
* [<span data-ttu-id="27f99-111">Erstellen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="27f99-111">Create a package flight submission</span></span>](#create-flight-submission)

<span id="token" />

## <a name="obtain-an-azure-ad-access-token"></a><span data-ttu-id="27f99-112">Abrufen eines Azure AD-Zugriffstokens</span><span class="sxs-lookup"><span data-stu-id="27f99-112">Obtain an Azure AD access token</span></span>

<span data-ttu-id="27f99-113">Im folgenden Beispiel wird gezeigt, wie Sie ein [Azure AD-Zugriffstoken abrufen](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), mit dem Sie Methoden in der Microsoft Store-Übermittlungs-API aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="27f99-113">The following example demonstrates how to [obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) that you can use to call methods in the Microsoft Store submission API.</span></span> <span data-ttu-id="27f99-114">Nach dem Abruf eines Tokens können Sie es für einen Zeitraum von 60Minuten in Aufrufen der Microsoft Store-Übermittlungs-API verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="27f99-114">After you obtain a token, you have 60 minutes to use this token in calls to the Microsoft Store submission API before the token expires.</span></span> <span data-ttu-id="27f99-115">Nach Ablauf des Tokens können Sie ein neues Token generieren.</span><span class="sxs-lookup"><span data-stu-id="27f99-115">After the token expires, you can generate a new token..</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L1-L20)]

<span id="create-add-on" />

## <a name="create-an-add-on"></a><span data-ttu-id="27f99-116">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="27f99-116">Create an add-on</span></span>

<span data-ttu-id="27f99-117">Das folgende Beispiel zeigt, wie Sie EIN Flight-Paket [erstellen](create-an-add-on.md) und anschließend ein Add-On [löschen](delete-an-add-on.md).</span><span class="sxs-lookup"><span data-stu-id="27f99-117">The following example demonstrates how to [create](create-an-add-on.md) and then [delete](delete-an-add-on.md) an add-on.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L26-L52)]

<span id="create-package-flight" />

## <a name="create-a-package-flight"></a><span data-ttu-id="27f99-118">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="27f99-118">Create a package flight</span></span>

<span data-ttu-id="27f99-119">Das folgende Beispiel zeigt, wie Sie EIN Flight-Paket [erstellen](create-a-flight.md) und anschließend [löschen](delete-a-flight.md).</span><span class="sxs-lookup"><span data-stu-id="27f99-119">The following example demonstrates how to [create](create-a-flight.md) and then [delete](delete-a-flight.md) a package flight.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L58-L87)]

<span id="create-app-submission" />

## <a name="create-an-app-submission"></a><span data-ttu-id="27f99-120">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="27f99-120">Create an app submission</span></span>

<span data-ttu-id="27f99-121">Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Microsoft Store-Übermittlungs-API verwenden, um eine App-Übermittlung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="27f99-121">The following example shows how to use several methods in the Microsoft Store submission API to create an app submission.</span></span> <span data-ttu-id="27f99-122">Zu diesem Zweck der Code erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, und aktualisiert anschließend und sendet die geklonte Übermittlung für das Partner Center.</span><span class="sxs-lookup"><span data-stu-id="27f99-122">To do this, the code creates a new submission as a clone of the last published submission, and then updates and commits the cloned submission to Partner Center.</span></span> <span data-ttu-id="27f99-123">Insbesondere werden im Beispiel folgende Aufgaben gezeigt:</span><span class="sxs-lookup"><span data-stu-id="27f99-123">Specifically, the example performs these tasks:</span></span>

1. <span data-ttu-id="27f99-124">Zunächst [werden Daten für die angegebene App abgerufen](get-an-app.md).</span><span class="sxs-lookup"><span data-stu-id="27f99-124">To begin, the example [gets data for the specified app](get-an-app.md).</span></span>
2. <span data-ttu-id="27f99-125">Als Nächstes [wird eine ausstehende Übermittlung für die App gelöscht](delete-an-app-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="27f99-125">Next, it [deletes the pending submission for the app](delete-an-app-submission.md), if one exists.</span></span>
3. <span data-ttu-id="27f99-126">Anschließend [wird eine neue Übermittlung für die App erstellt](create-an-app-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="27f99-126">It then [creates a new submission for the app](create-an-app-submission.md) (the new submission is a copy of the last published submission).</span></span>
4. <span data-ttu-id="27f99-127">Es werden einige Details für die neue Übermittlung geändert und ein neues Paket für die Übermittlung zu Azure Blob Storage hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="27f99-127">It changes some details for the new submission and upload a new package for the submission to Azure Blob storage.</span></span>
5. <span data-ttu-id="27f99-128">Als Nächstes wird es [Updates](update-an-app-submission.md) und anschließend auf die neue Übermittlung für das Partner Center [committet](commit-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="27f99-128">Next, it [updates](update-an-app-submission.md) and then [commits](commit-an-app-submission.md) the new submission to Partner Center.</span></span>
6. <span data-ttu-id="27f99-129">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-app-submission.md), bis die Übermittlung erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="27f99-129">Finally, it periodically [checks the status of the new submission](get-status-for-an-app-submission.md) until the submission is successfully committed.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L93-L166)]

<span id="create-add-on-submission" />

## <a name="create-an-add-on-submission"></a><span data-ttu-id="27f99-130">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="27f99-130">Create an add-on submission</span></span>

<span data-ttu-id="27f99-131">Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Microsoft Store-Übermittlungs-API verwenden, um eine Add-On-Übermittlung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="27f99-131">The following example shows how to use several methods in the Microsoft Store submission API to create an add-on submission.</span></span> <span data-ttu-id="27f99-132">Zu diesem Zweck der Code erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, und aktualisiert anschließend und sendet die geklonte Übermittlung für das Partner Center.</span><span class="sxs-lookup"><span data-stu-id="27f99-132">To do this, the code creates a new submission as a clone of the last published submission, and then updates and commits the cloned submission to Partner Center.</span></span> <span data-ttu-id="27f99-133">Insbesondere werden im Beispiel folgende Aufgaben gezeigt:</span><span class="sxs-lookup"><span data-stu-id="27f99-133">Specifically, the example performs these tasks:</span></span>

1. <span data-ttu-id="27f99-134">Zunächst [werden Daten für das angegebene Add-On abgerufen](get-an-add-on.md).</span><span class="sxs-lookup"><span data-stu-id="27f99-134">To begin, the example [gets data for the specified add-on](get-an-add-on.md).</span></span>
2. <span data-ttu-id="27f99-135">Als Nächstes [wird eine ausstehende Übermittlung für das Add-On gelöscht](delete-an-add-on-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="27f99-135">Next, it [deletes the pending submission for the add-on](delete-an-add-on-submission.md), if one exists.</span></span>
3. <span data-ttu-id="27f99-136">Anschließend [wird eine neue Übermittlung für das Add-On erstellt](create-an-add-on-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="27f99-136">It then [creates a new submission for the add-on](create-an-add-on-submission.md) (the new submission is a copy of the last published submission).</span></span>
4. <span data-ttu-id="27f99-137">Es wird ein ZIP-Archiv hochgeladen, das Symbole für die Übermittlung an Azure Blob Storage enthält.</span><span class="sxs-lookup"><span data-stu-id="27f99-137">It uploads a ZIP archive that contains icons for the submission to Azure Blob storage.</span></span> <span data-ttu-id="27f99-138">Weitere Informationen finden Sie in den entsprechenden Anweisungen zum Hochladen von ZIP-Archiven zu Azure Blob Storage in [Erstellen einer Add-On-Übermittlung](manage-add-on-submissions.md#create-an-add-on-submission).</span><span class="sxs-lookup"><span data-stu-id="27f99-138">For more information, see the relevant instructions about uploading a ZIP archive to Azure Blob storage in [Create an add-on submission](manage-add-on-submissions.md#create-an-add-on-submission).</span></span>
5. <span data-ttu-id="27f99-139">Als Nächstes wird es [Updates](update-an-add-on-submission.md) und anschließend auf die neue Übermittlung für das Partner Center [committet](commit-an-add-on-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="27f99-139">Next, it [updates](update-an-add-on-submission.md) and then [commits](commit-an-add-on-submission.md) the new submission to Partner Center.</span></span>
6. <span data-ttu-id="27f99-140">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-add-on-submission.md), bis die Übermittlung erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="27f99-140">Finally, it periodically [checks the status of the new submission](get-status-for-an-add-on-submission.md) until the submission is successfully committed.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L172-L245)]

<span id="create-flight-submission" />

## <a name="create-a-package-flight-submission"></a><span data-ttu-id="27f99-141">Erstellen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="27f99-141">Create a package flight submission</span></span>

<span data-ttu-id="27f99-142">Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Microsoft Store-Übermittlungs-API verwenden, um eine Flight-Paket-Übermittlung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="27f99-142">The following example shows how to use several methods in the Microsoft Store submission API to create a package flight submission.</span></span> <span data-ttu-id="27f99-143">Zu diesem Zweck der Code erstellt eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, und aktualisiert anschließend und sendet die geklonte Übermittlung für das Partner Center.</span><span class="sxs-lookup"><span data-stu-id="27f99-143">To do this, the code creates a new submission as a clone of the last published submission, and then updates and commits the cloned submission to Partner Center.</span></span> <span data-ttu-id="27f99-144">Insbesondere werden im Beispiel folgende Aufgaben gezeigt:</span><span class="sxs-lookup"><span data-stu-id="27f99-144">Specifically, the example performs these tasks:</span></span>

1. <span data-ttu-id="27f99-145">Zunächst [werden Daten für das angegebene Flight-Paket abgerufen](get-a-flight.md).</span><span class="sxs-lookup"><span data-stu-id="27f99-145">To begin, the example [gets data for the specified package flight](get-a-flight.md).</span></span>
2. <span data-ttu-id="27f99-146">Als Nächstes [wird eine ausstehende Übermittlung für das Flight-Paket gelöscht](delete-a-flight-submission.md), wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="27f99-146">Next, it [deletes the pending submission for the package flight](delete-a-flight-submission.md), if one exists.</span></span>
3. <span data-ttu-id="27f99-147">Anschließend [wird eine neue Übermittlung für das Flight-Paket erstellt](create-a-flight-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)</span><span class="sxs-lookup"><span data-stu-id="27f99-147">It then [creates a new submission for the package flight](create-a-flight-submission.md) (the new submission is a copy of the last published submission).</span></span>
4. <span data-ttu-id="27f99-148">Es wird ein neues Paket für die Übermittlung an Azure Blob Storage hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="27f99-148">It uploads a new package for the submission to Azure Blob storage.</span></span> <span data-ttu-id="27f99-149">Weitere Informationen finden Sie in den entsprechenden Anweisungen zum Hochladen von ZIP-Archiven zu Azure Blob Storage in [Erstellen einer Flight-Paket-Übermittlung](manage-flight-submissions.md#create-a-package-flight-submission).</span><span class="sxs-lookup"><span data-stu-id="27f99-149">For more information, see the relevant instructions about uploading a ZIP archive to Azure Blob storage in [Create a package flight submission](manage-flight-submissions.md#create-a-package-flight-submission).</span></span>
5. <span data-ttu-id="27f99-150">Als Nächstes wird es [Updates](update-a-flight-submission.md) und anschließend auf die neue Übermittlung für das Partner Center [committet](commit-a-flight-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="27f99-150">Next, it [updates](update-a-flight-submission.md) and then [commits](commit-a-flight-submission.md) the new submission to Partner Center.</span></span>
6. <span data-ttu-id="27f99-151">Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-a-flight-submission.md), bis die Übermittlung erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="27f99-151">Finally, it periodically [checks the status of the new submission](get-status-for-a-flight-submission.md) until the submission is successfully committed.</span></span>

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L251-L325)]

## <a name="related-topics"></a><span data-ttu-id="27f99-152">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="27f99-152">Related topics</span></span>

* [<span data-ttu-id="27f99-153">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="27f99-153">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
