---
author: Xansky
description: Verwenden Sie die Java-Codebeispiele in diesem Abschnitt, um mehr über das Einreichen von Spieloptionen und Trailern über die Verwendung der Microsoft Store-Übermittlungs-API zu erfahren.
title: 'Java-Beispiel: App-Übermittlung mit Spieloptionen und Trailer'
ms.author: mhopkins
ms.date: 07/10/2017
ms.topic: article
keywords: Windows10, Uwp, Microsoft Store-Übermittlungs-API, Codebeispiele, Spieloptionen, Trailer, erweiterte Angebote, Java
ms.localizationpriority: medium
ms.openlocfilehash: d6d64e317d2ff75be4aeb1f0e7df512287ae914a
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5754210"
---
# <a name="java-sample-app-submission-with-game-options-and-trailers"></a><span data-ttu-id="4e727-104">Java-Beispiel: App-Übermittlung mit Spieloptionen und Trailer</span><span class="sxs-lookup"><span data-stu-id="4e727-104">Java sample: app submission with game options and trailers</span></span>

<span data-ttu-id="4e727-105">Dieser Artikel enthält Java-Codebeispiele zeigt das Verwenden der [Microsoft Store-Übermittlungs-API](create-and-manage-submissions-using-windows-store-services.md) für diese Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="4e727-105">This article provides Java code examples that demonstrate how to use the [Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md) for these tasks:</span></span>

* <span data-ttu-id="4e727-106">Abrufen eines Azure AD-Zugriffstokens zur Nutzung mit der Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="4e727-106">Obtain an Azure AD access token to use with the Microsoft Store submission API.</span></span>
* <span data-ttu-id="4e727-107">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="4e727-107">Create an app submission</span></span>
* <span data-ttu-id="4e727-108">Konfigurieren von Store-Eintragsdateien für die App-Übermittlung, einschließlich der erweiterten Eintragsoptionen [Spiele](manage-app-submissions.md#gaming-options-object) und [Trailer](manage-app-submissions.md#trailer-object).</span><span class="sxs-lookup"><span data-stu-id="4e727-108">Configure Store listing data for the app submission, including the [gaming](manage-app-submissions.md#gaming-options-object) and [trailers](manage-app-submissions.md#trailer-object) advanced listing options.</span></span>
* <span data-ttu-id="4e727-109">Hochladen der ZIP-Datei mit den Paketen, Eintragsbildern und Trailerdateien für die App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="4e727-109">Upload the ZIP file containing the packages, listing images, and trailer files for the app submission.</span></span>
* <span data-ttu-id="4e727-110">Ausführen des Commit für eine App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="4e727-110">Commit the app submission.</span></span>

<span id="create-app-submission" />

## <a name="create-an-app-submission"></a><span data-ttu-id="4e727-111">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="4e727-111">Create an app submission</span></span>

<span data-ttu-id="4e727-112">Die ```CreateAndSubmitSubmissionExample```-Klasse implementiert ein ```main```-Programm, das andere Beispielmethoden aufruft, um die Microsoft Store-Übermittlungs-API zum Erstellen und Ausführen eines Commits einer App-Übermittlung mit Optionen und einem Trailer verwendet.</span><span class="sxs-lookup"><span data-stu-id="4e727-112">The ```CreateAndSubmitSubmissionExample``` class implements a ```main``` program that calls other example methods to use the Microsoft Store submission API to create and commit an app submission that contains game options and a trailer.</span></span> <span data-ttu-id="4e727-113">So passen Sie den Code für eigene Zwecke an:</span><span class="sxs-lookup"><span data-stu-id="4e727-113">To adapt this code for your own use:</span></span>

* <span data-ttu-id="4e727-114">Weisen Sie die ```tenantId```-Variable zur Mandanten-ID für Ihre App zu und weisen Sie die Variablen ```clientId``` und ```clientSecret``` zur Client-ID und dem Schlüssel für die App zu.</span><span class="sxs-lookup"><span data-stu-id="4e727-114">Assign the ```tenantId``` variable to the tenant ID for your app, and assign the ```clientId``` and ```clientSecret``` variables to the client ID and key for your app.</span></span> <span data-ttu-id="4e727-115">Weitere Informationen finden Sie unter [Zuordnen einer Azure AD-Anwendung zu Ihrem Windows Dev Center-Konto](create-and-manage-submissions-using-windows-store-services.md#how-to-associate-an-azure-ad-application-with-your-windows-dev-center-account).</span><span class="sxs-lookup"><span data-stu-id="4e727-115">For more information, see [How to associate an Azure AD application with your Windows Dev Center account](create-and-manage-submissions-using-windows-store-services.md#how-to-associate-an-azure-ad-application-with-your-windows-dev-center-account)</span></span>
* <span data-ttu-id="4e727-116">Weisen Sie die ```applicationId```-Variable zur [Store-ID](in-app-purchases-and-trials.md#store-ids) der App zu, für die eine Übermittlung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="4e727-116">Assign the ```applicationId``` variable to the [Store ID](in-app-purchases-and-trials.md#store-ids) of the app for which you want to create a submission.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code[SubmissionApi](./code/StoreServicesExamples_SubmissionAdvancedListings/java/CreateAndSubmitSubmissionExample.java#L1-L313)]

<span id="token" />

## <a name="obtain-an-azure-ad-access-token"></a><span data-ttu-id="4e727-117">Abrufen eines Azure AD-Zugriffstokens</span><span class="sxs-lookup"><span data-stu-id="4e727-117">Obtain an Azure AD access token</span></span>

<span data-ttu-id="4e727-118">Die ```DevCenterAccessTokenClient```-Klasse definiert eine Hilfsmethode, die Ihre ```tenantId```, ```clientId``` und ```clientSecret``` Werte zum Erstellen eines Azure AD-Zugriffstokens zur Verwendung mit Microsoft Store-Übermittlungs-API verwendet.</span><span class="sxs-lookup"><span data-stu-id="4e727-118">The ```DevCenterAccessTokenClient``` class defines a helper method that uses the your ```tenantId```, ```clientId``` and ```clientSecret``` values to create an Azure AD access token to use with the Microsoft Store submission API.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code[SubmissionApi](./code/StoreServicesExamples_SubmissionAdvancedListings/java/DevCenterAccessTokenClient.java#L1-L69)]

<span id="utilities" />

## <a name="helper-methods-to-invoke-the-submission-api-and-upload-submission-files"></a><span data-ttu-id="4e727-119">Hilfsmethoden zum Aufrufen von der Übermittlungs-API und zum Hochladen von Übermittlungsdateien</span><span class="sxs-lookup"><span data-stu-id="4e727-119">Helper methods to invoke the submission API and upload submission files</span></span>

<span data-ttu-id="4e727-120">Die ```DevCenterClient``` Klasse definiert Hilfsmethoden, die eine Vielzahl von Methoden in der Microsoft Store-Übermittlungs-API aufrufen und die ZIP-Datei mit den Paketen, Bildern und Trailerdateien für die App-Übermittlung hochladen.</span><span class="sxs-lookup"><span data-stu-id="4e727-120">The ```DevCenterClient``` class defines helper methods that invoke a variety of methods in the Microsoft Store submission API and upload the ZIP file containing the packages, listing images, and trailer files for the app submission.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code[SubmissionApi](./code/StoreServicesExamples_SubmissionAdvancedListings/java/DevCenterClient.java#L1-L224)]

## <a name="related-topics"></a><span data-ttu-id="4e727-121">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="4e727-121">Related topics</span></span>

* [<span data-ttu-id="4e727-122">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="4e727-122">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
