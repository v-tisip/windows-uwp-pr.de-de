---
author: Xansky
ms.assetid: 14C23FE6-3EAF-445E-85C1-DF188A7822CA
description: Verwenden Sie die Codebeispiele in diesem Abschnitt erfahren Sie mehr über die Verwendung der Microsoft Store-Übermittlungs-API.
title: Codebeispiele für die Übermittlungs-API
ms.author: mhopkins
ms.date: 07/10/2017
ms.topic: article
keywords: Windows 10, Uwp, Microsoft Store-Übermittlungs-API, Codebeispiele
ms.localizationpriority: medium
ms.openlocfilehash: 2b9c2acbdd6c45c00ba96bdc11a8273a66a67116
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7444528"
---
# <a name="code-examples-for-the-submission-api"></a><span data-ttu-id="5d09b-104">Codebeispiele für die Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="5d09b-104">Code examples for the submission API</span></span>

<span data-ttu-id="5d09b-105">Dieser Abschnitt enthält Codebeispiele für die Verwendung der [Microsoft Store-Übermittlungs-API](create-and-manage-submissions-using-windows-store-services.md) in verschiedenen Programmiersprachen.</span><span class="sxs-lookup"><span data-stu-id="5d09b-105">This section provides code examples for using the [Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md) in several different programming languages.</span></span>

> [!NOTE]
> <span data-ttu-id="5d09b-106">Zusätzlich zu den unten aufgeführten Codebeispielen bieten wir auch ein Open-Source-PowerShell-Modul, das neben der Microsoft Store-Übermittlungs-API eine Befehlszeilenschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5d09b-106">In addition to the code examples listed below, we also provide an open-source PowerShell module which implements a command-line interface on top of the Microsoft Store submission API.</span></span> <span data-ttu-id="5d09b-107">Dieses Modul heißt [StoreBroker](https://aka.ms/storebroker).</span><span class="sxs-lookup"><span data-stu-id="5d09b-107">This module is called [StoreBroker](https://aka.ms/storebroker).</span></span> <span data-ttu-id="5d09b-108">Sie können dieses Modul verwenden, um Ihre App-, Flight- und Add-On-Übermittlungen über die Befehlszeile anstatt über die Microsoft Store-Übermittlungs-API direkt zu verwalten. Sie können auch ganz einfach die Quelle durchsuchen, um weitere Beispiele für das Aufrufen dieser API zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5d09b-108">You can use this module to manage your app, flight, and add-on submissions from the command line instead of calling the Microsoft Store submission API directly, or you can simply browse the source to see more examples for how to call this API.</span></span> <span data-ttu-id="5d09b-109">Das StoreBroker-Modul wird innerhalb von Microsoft aktiv als primäre Methode verwendet, durch die viele Erstanbieter-Apps an den Store übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="5d09b-109">The StoreBroker module is actively used within Microsoft as the primary way that many first-party applications are submitted to the Store.</span></span> <span data-ttu-id="5d09b-110">Weitere Informationen finden Sie in auf der [StoreBroker-Seite auf GitHub](https://aka.ms/storebroker).</span><span class="sxs-lookup"><span data-stu-id="5d09b-110">For more information, see our [StoreBroker page on GitHub](https://aka.ms/storebroker).</span></span>

## <a name="app-submissions-add-on-submissions-and-package-flight-submissions"></a><span data-ttu-id="5d09b-111">App-Übermittlungen, Add-On-Übermittlungen und Flight-Paket-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="5d09b-111">App submissions, add-on submissions, and package flight submissions</span></span>

<span data-ttu-id="5d09b-112">Die folgenden Artikel enthalten Codebeispiele für die Verwendung der Übermittlungs-API zum Erstellen von App-Übermittlungen, Add-On-Übermittlungen und Flight-Paket-Übermittlungen.</span><span class="sxs-lookup"><span data-stu-id="5d09b-112">The following articles provide code examples for using the submission API to create app submissions, add-on submissions, and package flight submissions.</span></span>

* [<span data-ttu-id="5d09b-113">C#-Beispiel: Übermittlungen für Apps, Add-Ons und Flights</span><span class="sxs-lookup"><span data-stu-id="5d09b-113">C# sample: submissions for apps, add-ons, and flights</span></span>](csharp-code-examples-for-the-windows-store-submission-api.md)
* [<span data-ttu-id="5d09b-114">Java-Beispiel: Übermittlungen für Apps, Add-Ons und Flights</span><span class="sxs-lookup"><span data-stu-id="5d09b-114">Java sample: submissions for apps, add-ons, and flights</span></span>](java-code-examples-for-the-windows-store-submission-api.md)
* [<span data-ttu-id="5d09b-115">Python-Beispiel: Übermittlungen für Apps, Add-Ons und Flights</span><span class="sxs-lookup"><span data-stu-id="5d09b-115">Python sample: submissions for apps, add-ons, and flights</span></span>](python-code-examples-for-the-windows-store-submission-api.md)

## <a name="game-options-and-trailers"></a><span data-ttu-id="5d09b-116">Spieloptionen und Trailer</span><span class="sxs-lookup"><span data-stu-id="5d09b-116">Game options and trailers</span></span>

<span data-ttu-id="5d09b-117">Die folgenden Artikel enthalten Codebeispiele für die Verwendung der Übermittlungs-API zum Definieren von spielspezifischen Optionen und Übermitteln von Videotrailern für Apps.</span><span class="sxs-lookup"><span data-stu-id="5d09b-117">The following articles provide code examples for using the submission API to define game-specific options and to submit video trailers for apps.</span></span>

* [<span data-ttu-id="5d09b-118">C#-Beispiel: App-Übermittlung mit Spieloptionen und Trailer</span><span class="sxs-lookup"><span data-stu-id="5d09b-118">C# sample: app submission with game options and trailers</span></span>](csharp-code-examples-for-submissions-game-options-and-trailers.md)
* [<span data-ttu-id="5d09b-119">Java-Beispiel: App-Übermittlung mit Spieloptionen und Trailer</span><span class="sxs-lookup"><span data-stu-id="5d09b-119">Java sample: app submission with game options and trailers</span></span>](java-code-examples-for-submissions-game-options-and-trailers.md)
* [<span data-ttu-id="5d09b-120">Python-Beispiel: App-Übermittlung mit Spieloptionen und Trailer</span><span class="sxs-lookup"><span data-stu-id="5d09b-120">Python sample: app submission with game options and trailers</span></span>](python-code-examples-for-submissions-game-options-and-trailers.md)

## <a name="related-topics"></a><span data-ttu-id="5d09b-121">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5d09b-121">Related topics</span></span>

* [<span data-ttu-id="5d09b-122">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="5d09b-122">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
