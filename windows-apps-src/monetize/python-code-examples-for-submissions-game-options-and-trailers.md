---
author: Xansky
description: Verwenden Sie die Python-Codebeispiele in diesem Abschnitt, um mehr über das Einreichen von Spieloptionen und Trailern über die Verwendung der Microsoft Store-Übermittlungs-API zu erfahren.
title: 'Python-Beispiel: App-Übermittlung mit Spieloptionen und Trailer'
ms.author: mhopkins
ms.date: 07/10/2017
ms.topic: article
keywords: Windows10, Uwp, Microsoft Store-Übermittlungs-API, Codebeispiele, Spieloptionen, Trailer, erweiterte Angebote, Python
ms.localizationpriority: medium
ms.openlocfilehash: 86c753e51d15b142cdcd7e54b3ed0304d13169b6
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6647080"
---
# <a name="python-sample-app-submission-with-game-options-and-trailers"></a><span data-ttu-id="cacc5-104">Python-Beispiel: App-Übermittlung mit Spieloptionen und Trailer</span><span class="sxs-lookup"><span data-stu-id="cacc5-104">Python sample: app submission with game options and trailers</span></span>

<span data-ttu-id="cacc5-105">Dieser Artikel enthält Python-Codebeispiele zeigt das Verwenden der [Microsoft Store-Übermittlungs-API](create-and-manage-submissions-using-windows-store-services.md) für diese Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="cacc5-105">This article provides Python code examples that demonstrate how to use the [Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md) for these tasks:</span></span>

* <span data-ttu-id="cacc5-106">Abrufen eines Azure AD-Zugriffstokens zur Nutzung mit der Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="cacc5-106">Obtain an Azure AD access token to use with the Microsoft Store submission API.</span></span>
* <span data-ttu-id="cacc5-107">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="cacc5-107">Create an app submission</span></span>
* <span data-ttu-id="cacc5-108">Konfigurieren von Store-Eintragsdateien für die App-Übermittlung, einschließlich der erweiterten Eintragsoptionen [Spiele](manage-app-submissions.md#gaming-options-object) und [Trailer](manage-app-submissions.md#trailer-object).</span><span class="sxs-lookup"><span data-stu-id="cacc5-108">Configure Store listing data for the app submission, including the [gaming](manage-app-submissions.md#gaming-options-object) and [trailers](manage-app-submissions.md#trailer-object) advanced listing options.</span></span>
* <span data-ttu-id="cacc5-109">Hochladen der ZIP-Datei mit den Paketen, Eintragsbildern und Trailerdateien für die App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="cacc5-109">Upload the ZIP file containing the packages, listing images, and trailer files for the app submission.</span></span>
* <span data-ttu-id="cacc5-110">Ausführen des Commit für eine App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="cacc5-110">Commit the app submission.</span></span>

<span id="create-app-submission" />

## <a name="create-an-app-submission"></a><span data-ttu-id="cacc5-111">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="cacc5-111">Create an app submission</span></span>

<span data-ttu-id="cacc5-112">Dieser Code ruft andere Beispielklassen und Funktionen auf, um die Microsoft Store-Übermittlungs-API zum Erstellen und Ausführen eines Commits einer App-Übermittlung mit Optionen und einem Trailer verwendet.</span><span class="sxs-lookup"><span data-stu-id="cacc5-112">This code calls other example classes and functions to use the Microsoft Store submission API to create and commit an app submission that contains game options and a trailer.</span></span> <span data-ttu-id="cacc5-113">So passen Sie den Code für eigene Zwecke an:</span><span class="sxs-lookup"><span data-stu-id="cacc5-113">To adapt this code for your own use:</span></span>

* <span data-ttu-id="cacc5-114">Weisen Sie die ```tenant```-Variable zur Mandanten-ID für Ihre App zu und weisen Sie die Variablen ```client``` und ```secret``` zur Client-ID und dem Schlüssel für die App zu.</span><span class="sxs-lookup"><span data-stu-id="cacc5-114">Assign the ```tenant``` variable to the tenant ID for your app, and assign the ```client``` and ```secret``` variables to the client ID and key for your app.</span></span> <span data-ttu-id="cacc5-115">Weitere Informationen finden Sie [eine Azure AD-Anwendung mit Ihrem Partner Center-Konto zuordnen](create-and-manage-submissions-using-windows-store-services.md#how-to-associate-an-azure-ad-application-with-your-partner-center-account)</span><span class="sxs-lookup"><span data-stu-id="cacc5-115">For more information, see [How to associate an Azure AD application with your Partner Center account](create-and-manage-submissions-using-windows-store-services.md#how-to-associate-an-azure-ad-application-with-your-partner-center-account)</span></span>
* <span data-ttu-id="cacc5-116">Weisen Sie die ```application_id```-Variable zur [Store-ID](in-app-purchases-and-trials.md#store-ids) der App zu, für die eine Übermittlung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="cacc5-116">Assign the ```application_id``` variable to the [Store ID](in-app-purchases-and-trials.md#store-ids) of the app for which you want to create a submission.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code[SubmissionApi](./code/StoreServicesExamples_SubmissionAdvancedListings/python/CreateAndSubmitAppSubmissionExample.py#L1-L74)]

<span id="token" />

## <a name="obtain-an-azure-ad-access-token-and-invoke-the-submission-api"></a><span data-ttu-id="cacc5-117">Ein Azure AD-Zugriffstoken abrufen und Aufrufen der Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="cacc5-117">Obtain an Azure AD access token and invoke the submission API</span></span>

<span data-ttu-id="cacc5-118">Das folgende Beispiel definiert die folgenden Klassen:</span><span class="sxs-lookup"><span data-stu-id="cacc5-118">The following example defines the following classes:</span></span>

* <span data-ttu-id="cacc5-119">Die ```DevCenterAccessTokenClient```-Klasse definiert eine Hilfsmethode, die Ihre ```tenantId```, ```clientId``` und ```clientSecret``` Werte zum Erstellen eines Azure AD-Zugriffstokens zur Verwendung mit Microsoft Store-Übermittlungs-API verwendet.</span><span class="sxs-lookup"><span data-stu-id="cacc5-119">The ```DevCenterAccessTokenClient``` class defines a helper method that uses the your ```tenantId```, ```clientId``` and ```clientSecret``` values to create an Azure AD access token to use with the Microsoft Store submission API.</span></span>
* <span data-ttu-id="cacc5-120">Die ```DevCenterClient``` Klasse definiert Hilfsmethoden, die eine Vielzahl von Methoden in der Microsoft Store-Übermittlungs-API aufrufen und die ZIP-Datei mit den Paketen, Bildern und Trailerdateien für die App-Übermittlung hochladen.</span><span class="sxs-lookup"><span data-stu-id="cacc5-120">The ```DevCenterClient``` class defines helper methods that invoke a variety of methods in the Microsoft Store submission API and upload the ZIP file containing the packages, listing images, and trailer files for the app submission.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code[SubmissionApi](./code/StoreServicesExamples_SubmissionAdvancedListings/python/devcenterclient.py#L1-L126)]

<span id="token" />

## <a name="get-app-submission-listing-data"></a><span data-ttu-id="cacc5-121">Abrufen von Eintragsdaten</span><span class="sxs-lookup"><span data-stu-id="cacc5-121">Get app submission listing data</span></span>

<span data-ttu-id="cacc5-122">Das folgende Beispiel definiert Hilfsfunktionen, die JSON-formatierte Eintrag Daten für eine neue Übermittlung der Beispiel-App zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="cacc5-122">The following example defines helper functions that return JSON-formatted listing data for a new sample app submission.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code[SubmissionApi](./code/StoreServicesExamples_SubmissionAdvancedListings/python/submissiondatasamples.py#L1-L170)]

## <a name="related-topics"></a><span data-ttu-id="cacc5-123">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="cacc5-123">Related topics</span></span>

* [<span data-ttu-id="cacc5-124">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="cacc5-124">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
