---
author: Xansky
ms.assetid: 37F2C162-4910-4336-BEED-8536C88DCA65
description: Verwenden Sie diese Methoden in der Microsoft Store-Übermittlungs-API, Flight-Pakete für apps zu verwalten, die für Ihr Partner Center-Konto registriert sind.
title: Verwalten von Flight-Paketen
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flights
ms.localizationpriority: medium
ms.openlocfilehash: 1f1300151d8b50a0a9e192c2090e9a3d72afa86e
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6652210"
---
# <a name="manage-package-flights"></a><span data-ttu-id="60044-104">Verwalten von Flight-Paketen</span><span class="sxs-lookup"><span data-stu-id="60044-104">Manage package flights</span></span>

<span data-ttu-id="60044-105">Mithilfe der folgenden Methoden in der Microsoft Store-Übermittlungs-API können Sie Flight-Pakete für Ihre Apps verwalten.</span><span class="sxs-lookup"><span data-stu-id="60044-105">Use the following methods in the Microsoft Store submission API to manage package flights for your apps.</span></span> <span data-ttu-id="60044-106">Eine Einführung in die Microsoft Store-Übermittlungs-API einschließlich der Voraussetzungen für die Verwendung der API finden Sie unter [Erstellen und Verwalten von Übermittlungen mit MicrosoftStore-Diensten](create-and-manage-submissions-using-windows-store-services.md).</span><span class="sxs-lookup"><span data-stu-id="60044-106">For an introduction to the Microsoft Store submission API, including prerequisites for using the API, see [Create and manage submissions using Microsoft Store services](create-and-manage-submissions-using-windows-store-services.md).</span></span>

<span data-ttu-id="60044-107">Diese Methoden können nur verwendet werden, um Flight-Pakete abzurufen, zu erstellen oder zu löschen.</span><span class="sxs-lookup"><span data-stu-id="60044-107">These methods can only be used to get, create, or delete package flights.</span></span> <span data-ttu-id="60044-108">Verwenden Sie zum Erstellen von Übermittlungen für Flight-Pakete die Methoden unter [Verwalten von Flight-Paket-Übermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="60044-108">To create submissions for package flights, see the methods in [Manage package flight submissions](manage-flight-submissions.md).</span></span>

<table>
<colgroup>
<col width="10%" />
<col width="30%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="60044-109">Methode</span><span class="sxs-lookup"><span data-stu-id="60044-109">Method</span></span></th>
<th align="left"><span data-ttu-id="60044-110">URI</span><span class="sxs-lookup"><span data-stu-id="60044-110">URI</span></span></th>
<th align="left"><span data-ttu-id="60044-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="60044-111">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><span data-ttu-id="60044-112">GET</span><span class="sxs-lookup"><span data-stu-id="60044-112">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}</td>
<td align="left"><a href="get-a-flight.md"><span data-ttu-id="60044-113">Abrufen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="60044-113">Get a package flight</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="60044-114">POST</span><span class="sxs-lookup"><span data-stu-id="60044-114">POST</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights</td>
<td align="left"><a href="create-a-flight.md"><span data-ttu-id="60044-115">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="60044-115">Create a package flight</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="60044-116">DELETE</span><span class="sxs-lookup"><span data-stu-id="60044-116">DELETE</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}</td>
<td align="left"><a href="delete-a-flight.md"><span data-ttu-id="60044-117">Löschen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="60044-117">Delete a package flight</span></span></a></td>
</tr>
</tbody>
</table>

## <a name="prerequisites"></a><span data-ttu-id="60044-118">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="60044-118">Prerequisites</span></span>

<span data-ttu-id="60044-119">Falls noch nicht geschehen, sorgen Sie vor der Verwendung dieser Methoden dafür, dass alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="60044-119">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API before trying to use any of these methods.</span></span>

## <a name="related-topics"></a><span data-ttu-id="60044-120">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="60044-120">Related topics</span></span>

* [<span data-ttu-id="60044-121">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="60044-121">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="60044-122">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="60044-122">Manage package flight submissions</span></span>](manage-flight-submissions.md)
