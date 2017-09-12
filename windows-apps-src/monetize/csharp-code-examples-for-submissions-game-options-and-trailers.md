---
author: mcleanbyron
description: "Verwenden Sie die C#-Codebeispiele in diesem Abschnitt, um mehr über das Einreichen von Spieloptionen und Trailern über die Verwendung der Windows Store-Übermittlungs-API zu erfahren."
title: "C#-Beispiel – App-Übermittlung mit Spieloptionen und Trailer"
ms.author: mcleans
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, Uwp, Windows Store-Übermittlungs-API, Codebeispiele, Spieloptionen, Trailer, erweiterte Angebote, C#"
ms.openlocfilehash: 2020d280d7b4ffa3cede11b089f808920ddf46b9
ms.sourcegitcommit: a7a1b41c7dce6d56250ce3113137391d65d9e401
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2017
---
# <a name="c-sample-app-submission-with-game-options-and-trailers"></a><span data-ttu-id="b0b50-104">C\#-Beispiel: App-Übermittlung mit Spieloptionen und Trailer</span><span class="sxs-lookup"><span data-stu-id="b0b50-104">C\# sample: app submission with game options and trailers</span></span>

<span data-ttu-id="b0b50-105">Dieser Artikel enthält C#-Codebeispiele zeigt das Verwenden der [Windows Store-Übermittlungs-API](create-and-manage-submissions-using-windows-store-services.md) für diese Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="b0b50-105">This article provides C# code examples that demonstrate how to use the [Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md) for these tasks:</span></span>

* <span data-ttu-id="b0b50-106">Abrufen eines Azure AD-Zugriffstokens zur Nutzung mit der Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="b0b50-106">Obtain an Azure AD access token to use with the Windows Store submission API.</span></span>
* <span data-ttu-id="b0b50-107">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="b0b50-107">Create an app submission</span></span>
* <span data-ttu-id="b0b50-108">Konfigurieren von Store-Eintragsdateien für die App-Übermittlung, einschließlich der erweiterten Eintragsoptionen [Spiele](manage-app-submissions.md#gaming-options-object) und [Trailer](manage-app-submissions.md#trailer-object).</span><span class="sxs-lookup"><span data-stu-id="b0b50-108">Configure Store listing data for the app submission, including the [gaming](manage-app-submissions.md#gaming-options-object) and [trailers](manage-app-submissions.md#trailer-object) advanced listing options.</span></span>
* <span data-ttu-id="b0b50-109">Hochladen der ZIP-Datei mit den Paketen, Eintragsbildern und Trailerdateien für die App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="b0b50-109">Upload the ZIP file containing the packages, listing images, and trailer files for the app submission.</span></span>
* <span data-ttu-id="b0b50-110">Ausführen des Commit für eine App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="b0b50-110">Commit the app submission.</span></span>

<span data-ttu-id="b0b50-111">Sie können die einzelnen Beispiele prüfen, um mehr über die jeweilige Aufgabe zu erfahren. Zudem können Sie alle Codebeispiele in diesem Artikel in eine Konsolenanwendung einbinden.</span><span class="sxs-lookup"><span data-stu-id="b0b50-111">You can review each example to learn more about the task it demonstrates, or you can build all the code examples in this article into a console application.</span></span> <span data-ttu-id="b0b50-112">Um die Beispiele zu übernehmen, erstellen Sie in Visual Studio eine C#-Konsolenanwendung mit dem Namen **DevCenterApiSample**, kopieren Sie die einzelnen Beispiele in separate Codedateien des Projekts, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="b0b50-112">To build the examples, create a C# console application named **DevCenterApiSample** in Visual Studio, copy each example to a separate code file in the project, and build the project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0b50-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b0b50-113">Prerequisites</span></span>

<span data-ttu-id="b0b50-114">Für diese Beispiele gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="b0b50-114">These examples have the following requirements:</span></span>

* <span data-ttu-id="b0b50-115">Hinzufügen eines Verweises auf die the System.Web-Assembly zu Ihrem Projekt</span><span class="sxs-lookup"><span data-stu-id="b0b50-115">Add a reference to the System.Web assembly in your project.</span></span>
* <span data-ttu-id="b0b50-116">Installieren Sie das [Newtonsoft.Json](http://www.newtonsoft.com/json) NuGet-Paket von Newtonsoft für Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="b0b50-116">Install the [Newtonsoft.Json](http://www.newtonsoft.com/json) NuGet package from Newtonsoft to your project.</span></span>

<span id="create-app-submission" />
## <a name="create-an-app-submission"></a><span data-ttu-id="b0b50-117">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="b0b50-117">Create an app submission</span></span>

<span data-ttu-id="b0b50-118">Die ```CreateAndSubmitSubmissionExample```-Klasse definiert eine öffentliche ```Execute```-Methode, die anderen Beispielmethoden aufruft, um die Windows Store-Übermittlungs-API zum Erstellen und Ausführen eines Commits einer App-Übermittlung mit Optionen und einem Trailer verwendet.</span><span class="sxs-lookup"><span data-stu-id="b0b50-118">The ```CreateAndSubmitSubmissionExample``` class defines a public ```Execute``` method that calls other example methods to use the Windows Store submission API to create and commit an app submission that contains game options and a trailer.</span></span> <span data-ttu-id="b0b50-119">So passen Sie den Code für eigene Zwecke an:</span><span class="sxs-lookup"><span data-stu-id="b0b50-119">To adapt this code for your own use:</span></span>

* <span data-ttu-id="b0b50-120">Weisen Sie die ```tenantId```-Variable zur Mandanten-ID für Ihre App zu und weisen Sie die Variablen ```clientId``` und ```clientSecret``` zur Client-ID und dem Schlüssel für die App zu.</span><span class="sxs-lookup"><span data-stu-id="b0b50-120">Assign the ```tenantId``` variable to the tenant ID for your app, and assign the ```clientId``` and ```clientSecret``` variables to the client ID and key for your app.</span></span> <span data-ttu-id="b0b50-121">Weitere Informationen finden Sie unter [Zuordnen einer Azure AD-Anwendung zu Ihrem Windows Dev Center-Konto](create-and-manage-submissions-using-windows-store-services.md#how-to-associate-an-azure-ad-application-with-your-windows-dev-center-account).</span><span class="sxs-lookup"><span data-stu-id="b0b50-121">For more information, see [How to associate an Azure AD application with your Windows Dev Center account](create-and-manage-submissions-using-windows-store-services.md#how-to-associate-an-azure-ad-application-with-your-windows-dev-center-account)</span></span>
* <span data-ttu-id="b0b50-122">Weisen Sie die ```applicationId```-Variable zur [Store-ID](in-app-purchases-and-trials.md#store_ids) der App zu, für die eine Übermittlung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="b0b50-122">Assign the ```applicationId``` variable to the [Store ID](in-app-purchases-and-trials.md#store_ids) of the app for which you want to create a submission.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[<span data-ttu-id="b0b50-123">SubmissionApi</span><span class="sxs-lookup"><span data-stu-id="b0b50-123">SubmissionApi</span></span>](./code/StoreServicesExamples_SubmissionAdvancedListings/cs/CreateAndSubmitSubmissionExample.cs#CreateAndSubmitSubmissionExample)]

<span id="token" />
## <a name="obtain-an-azure-ad-access-token"></a><span data-ttu-id="b0b50-124">Abrufen eines Azure AD-Zugriffstokens</span><span class="sxs-lookup"><span data-stu-id="b0b50-124">Obtain an Azure AD access token</span></span>

<span data-ttu-id="b0b50-125">Die ```DevCenterAccessTokenClient```-Klasse definiert eine Hilfsmethode, die Ihre ```tenantId```, ```clientId``` und ```clientSecret``` Werte zum Erstellen eines Azure AD-Zugriffstokens zur Verwendung mit Windows Store-Übermittlungs-API verwendet.</span><span class="sxs-lookup"><span data-stu-id="b0b50-125">The ```DevCenterAccessTokenClient``` class defines a helper method that uses the your ```tenantId```, ```clientId``` and ```clientSecret``` values to create an Azure AD access token to use with the Windows Store submission API.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[<span data-ttu-id="b0b50-126">SubmissionApi</span><span class="sxs-lookup"><span data-stu-id="b0b50-126">SubmissionApi</span></span>](./code/StoreServicesExamples_SubmissionAdvancedListings/cs/DevCenterAccessTokenClient.cs#DevCenterAccessTokenClient)]

<span id="utilities" />
## <a name="helper-methods-to-invoke-the-submission-api-and-upload-submission-files"></a><span data-ttu-id="b0b50-127">Hilfsmethoden zum Aufrufen von der Übermittlungs-API und zum Hochladen von Übermittlungsdateien</span><span class="sxs-lookup"><span data-stu-id="b0b50-127">Helper methods to invoke the submission API and upload submission files</span></span>

<span data-ttu-id="b0b50-128">Die ```DevCenterClient``` Klasse definiert Hilfsmethoden, die eine Vielzahl von Methoden in der Windows Store-Übermittlungs-API aufrufen und die ZIP-Datei mit den Paketen, Bildern und Trailerdateien für die App-Übermittlung hochladen.</span><span class="sxs-lookup"><span data-stu-id="b0b50-128">The ```DevCenterClient``` class defines helper methods that invoke a variety of methods in the Windows Store submission API and upload the ZIP file containing the packages, listing images, and trailer files for the app submission.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[<span data-ttu-id="b0b50-129">SubmissionApi</span><span class="sxs-lookup"><span data-stu-id="b0b50-129">SubmissionApi</span></span>](./code/StoreServicesExamples_SubmissionAdvancedListings/cs/DevCenterClient.cs#DevCenterClient)]

## <a name="related-topics"></a><span data-ttu-id="b0b50-130">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b0b50-130">Related topics</span></span>

* [<span data-ttu-id="b0b50-131">Erstellen und Verwalten von Übermittlungen mit Windows Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="b0b50-131">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
