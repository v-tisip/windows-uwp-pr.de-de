---
Description: You can use the SendRequestAsync method to send requests to the Microsoft Store for operations that do not yet have an API available in the Windows SDK.
title: Senden von Anforderungen an den Microsoft Store
ms.assetid: 070B9CA4-6D70-4116-9B18-FBF246716EF0
ms.date: 03/22/2018
ms.topic: article
keywords: Windows10, UWP, StoreRequestHelper, SendRequestAsync
ms.localizationpriority: medium
ms.openlocfilehash: d492bc7dde990404552689516731850974c31a7c
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7692511"
---
# <a name="send-requests-to-the-microsoft-store"></a><span data-ttu-id="739b1-103">Senden von Anforderungen an den Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="739b1-103">Send requests to the Microsoft Store</span></span>

<span data-ttu-id="739b1-104">Ab Windows10, Version 1607, bietet das Windows SDK im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace APIs für Store-bezogene Vorgänge (z.B. In-App-Einkäufe).</span><span class="sxs-lookup"><span data-stu-id="739b1-104">Starting in Windows 10, version 1607, the Windows SDK provides APIs for Store-related operations (such as in-app purchases) in the [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) namespace.</span></span> <span data-ttu-id="739b1-105">Obwohl die Dienste, die den Store unterstützen, zwischen den verschiedenen Betriebssystemversionen kontinuierlich aktualisiert, erweitert und verbessert werden, werden neue APIs in der Regel nur bei Hauptversionen des Betriebssystems zum Windows SDK hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="739b1-105">However, although the services that support the Store are constantly being updated, expanded, and improved between OS releases, new APIs are typically added to the Windows SDK only during major OS releases.</span></span>

<span data-ttu-id="739b1-106">Unsere [SendRequestAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper.sendrequestasync)-Methode ist eine flexible Lösung zur Bereitstellung neuer Store-Vorgänge für UWP (Universelle Windows-Plattform)-Apps vor der Veröffentlichung einer neuen Windows SDK-Version.</span><span class="sxs-lookup"><span data-stu-id="739b1-106">We provide the [SendRequestAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper.sendrequestasync) method as a flexible way to make new Store operations available to Universal Windows Platform (UWP) apps before a new version of the Windows SDK is released.</span></span> <span data-ttu-id="739b1-107">Sie können mithilfe dieser Methode Anforderungen an den Windows Store für Vorgänge senden, für die in der neuesten Windows SDK-Version noch keine entsprechende API zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="739b1-107">You can use this method to send requests to the Store for new operations that do not yet have a corresponding API available in the latest release of the Windows SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="739b1-108">Die **SendRequestAsync**-Methode ist nur für Apps für Windows 10, Version 1607 oder höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="739b1-108">The **SendRequestAsync** method is available only to apps that target Windows 10, version 1607, or later.</span></span> <span data-ttu-id="739b1-109">Einige Anforderungen, die von dieser Methode unterstützt werden, werden nur in Versionen nach Windows10, Version 1607 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="739b1-109">Some of the requests supported by this method are only supported in releases after Windows 10, version 1607.</span></span>

<span data-ttu-id="739b1-110">**SendRequestAsync** ist eine statische Methode der [StoreRequestHelper](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="739b1-110">**SendRequestAsync** is a static method of the [StoreRequestHelper](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper) class.</span></span> <span data-ttu-id="739b1-111">Um diese Methode aufzurufen, müssen Sie die folgenden Informationen an diese Methode übergeben:</span><span class="sxs-lookup"><span data-stu-id="739b1-111">To call this method, you must pass the following information to the method:</span></span>
* <span data-ttu-id="739b1-112">Ein [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Objekt, das Informationen zum Benutzer bereitstellt, für den Sie den Vorgang ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="739b1-112">A [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext) object that provides information about the user for which you want to perform the operation.</span></span> <span data-ttu-id="739b1-113">Weitere Informationen zu diesem Objekt finden Sie unter [Erste Schrittemit der StoreContext-Klasse](in-app-purchases-and-trials.md#get-started-with-the-storecontext-class).</span><span class="sxs-lookup"><span data-stu-id="739b1-113">For more information about this object, see [Get started with the StoreContext class](in-app-purchases-and-trials.md#get-started-with-the-storecontext-class).</span></span>
* <span data-ttu-id="739b1-114">Eine Ganzzahl, die die Anforderung identifiziert, die Sie an den Store senden möchten.</span><span class="sxs-lookup"><span data-stu-id="739b1-114">An integer that identifies the request that you want to send to the Store.</span></span>
* <span data-ttu-id="739b1-115">Wenn die Anforderung keine Argumente unterstützt, können Sie auch eine Zeichenfolge im JSON-Format übergeben, die die Argumente enthält, die zusammen mit der Anforderung übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="739b1-115">If the request supports any arguments, you can also pass a JSON-formatted string that contains the arguments to pass along with the request.</span></span>

<span data-ttu-id="739b1-116">Das folgende Beispiel veranschaulicht, wie diese Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="739b1-116">The following example demonstrates how to call this method.</span></span> <span data-ttu-id="739b1-117">In diesem Beispiel werden using-Anweisungen für die Namespaces **Windows.Services.Store** und **System.Threading.Tasks** benötigt.</span><span class="sxs-lookup"><span data-stu-id="739b1-117">This example requires using statements for the **Windows.Services.Store** and **System.Threading.Tasks** namespaces.</span></span>

```csharp
public async Task<bool> AddUserToFlightGroup()
{
    StoreSendRequestResult result = await StoreRequestHelper.SendRequestAsync(
        StoreContext.GetDefault(), 8,
        "{ \"type\": \"AddToFlightGroup\", \"parameters\": \"{ \"flightGroupId\": \"your group ID\" }\" }");

    if (result.ExtendedError == null)
    {
        return true;
    }

    return false;
}
```

<span data-ttu-id="739b1-118">Informationen zu den Anforderungen, die derzeit für die **SendRequestAsync**-Methode verfügbar sind, finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="739b1-118">See the following sections for information about the requests that are currently available via the **SendRequestAsync** method.</span></span> <span data-ttu-id="739b1-119">Dieser Artikel wird aktualisiert, wenn Unterstützung für neue Anforderungen hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="739b1-119">We will update this article when support for new requests are added.</span></span>

## <a name="request-for-in-app-ratings-and-reviews"></a><span data-ttu-id="739b1-120">Anfordern von In-App-Bewertungen und Prüfungen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="739b1-120">Request for in-app ratings and reviews</span></span>

<span data-ttu-id="739b1-121">Sie können programmgesteuert ein Dialogfeld von Ihrer App aus starten, das Ihre Kunden auffordert, Ihre App zu bewerten und eine Rezension zu senden, indem Sie die Anforderungsganzzahl 16 an die **SendRequestAsync**-Methode übergeben.</span><span class="sxs-lookup"><span data-stu-id="739b1-121">You can programmatically launch a dialog from your app that asks your customer to rate your app and submit a review by passing the request integer 16 to the **SendRequestAsync** method.</span></span> <span data-ttu-id="739b1-122">Weitere Informationen finden Sie unter [Ein Bewertungs- und Rezensionsdialogfeld in Ihrer App anzeigen](request-ratings-and-reviews.md#show-a-rating-and-review-dialog-in-your-app).</span><span class="sxs-lookup"><span data-stu-id="739b1-122">For more information, see [Show a rating and review dialog in your app](request-ratings-and-reviews.md#show-a-rating-and-review-dialog-in-your-app).</span></span>

## <a name="requests-for-flight-group-scenarios"></a><span data-ttu-id="739b1-123">Anforderungen für Test-Flight-Gruppenszenarien</span><span class="sxs-lookup"><span data-stu-id="739b1-123">Requests for flight group scenarios</span></span>

> [!IMPORTANT]
> <span data-ttu-id="739b1-124">Alle in diesem Abschnittbeschriebenen Anforderungen für Test-Flight-Gruppen sind derzeit für die meisten Entwicklerkonten nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="739b1-124">All of the flight group requests described in this section are currently not available to most developer accounts.</span></span> <span data-ttu-id="739b1-125">Diese Anforderungen werden fehlschlagen, es sei denn, Ihr Entwicklerkonto wird speziell von Microsoft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="739b1-125">These requests will fail unless your developer account is specially provisioned by Microsoft.</span></span>

<span data-ttu-id="739b1-126">Die **SendRequestAsync**-Methode unterstützt eine Reihe von Anforderungen für Test-Flight-Gruppenszenarien wie das Hinzufügen von Benutzern oder Geräten zu einer Test-Flight-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="739b1-126">The **SendRequestAsync** method supports a set of requests for flight group scenarios, such as adding a user or device to a flight group.</span></span> <span data-ttu-id="739b1-127">Um diese Anforderungen zu senden, übergeben Sie den Wert7 oder8 an den *RequestKind*-Parameter und die Zeichenfolge im JSON-Format an den *ParametersAsJson*-Parameter, der die Anforderung angibt, die Sie zusammen mit allen zugehörigen Argumenten übermitteln möchten.</span><span class="sxs-lookup"><span data-stu-id="739b1-127">To submit these requests, pass the value 7 or 8 to the *requestKind* parameter along with a JSON-formatted string to the *parametersAsJson* parameter that indicates the request you want to submit along with any related arguments.</span></span> <span data-ttu-id="739b1-128">Diese *RequestKind*-Werte unterscheiden sich folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="739b1-128">These *requestKind* values differ in the following ways.</span></span>

|  <span data-ttu-id="739b1-129">RequestKind-Wert</span><span class="sxs-lookup"><span data-stu-id="739b1-129">Request kind value</span></span>  |  <span data-ttu-id="739b1-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="739b1-130">Description</span></span>  |
|----------------------|---------------|
|  <span data-ttu-id="739b1-131">7</span><span class="sxs-lookup"><span data-stu-id="739b1-131">7</span></span>                   |  <span data-ttu-id="739b1-132">Die Anforderungen werden im Kontext des aktuellen Geräts ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="739b1-132">The requests are performed in the context of the current device.</span></span> <span data-ttu-id="739b1-133">Dieser Wert kann nur unter Windows10, Version 1703 oder höher verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="739b1-133">This value can only be used on Windows 10, version 1703, or later.</span></span>  |
|  <span data-ttu-id="739b1-134">8</span><span class="sxs-lookup"><span data-stu-id="739b1-134">8</span></span>                   |  <span data-ttu-id="739b1-135">Die Anforderungen werden im Kontext des Benutzers ausgeführt, der aktuell beim Store angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="739b1-135">The requests are performed in the context of the user who is currently signed in to the Store.</span></span> <span data-ttu-id="739b1-136">Dieser Wert kann unter Windows10, Version 1607 oder höher verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="739b1-136">This value can be used on Windows 10, version 1607, or later.</span></span>  |

<span data-ttu-id="739b1-137">Die folgenden Anforderungen für Test-Flight-Gruppen werden derzeit implementiert.</span><span class="sxs-lookup"><span data-stu-id="739b1-137">The following flight group requests are currently implemented.</span></span>

### <a name="retrieve-remote-variables-for-the-highest-ranked-flight-group"></a><span data-ttu-id="739b1-138">Abrufen von Remotevariablen für Test-Flight-Gruppen mit dem höchsten Rang</span><span class="sxs-lookup"><span data-stu-id="739b1-138">Retrieve remote variables for the highest-ranked flight group</span></span>

> [!IMPORTANT]
> <span data-ttu-id="739b1-139">Diese Anforderung ist derzeit für die meisten Entwicklerkonten nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="739b1-139">This request is currently not available to most developer accounts.</span></span> <span data-ttu-id="739b1-140">Diese Anforderung wird fehlschlagen, es sei denn, Ihr Entwicklerkonto wird speziell von Microsoft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="739b1-140">This request will fail unless your developer account is specially provisioned by Microsoft.</span></span>

<span data-ttu-id="739b1-141">Diese Anforderung ruft die Remotevariablen für die Test-Flight-Gruppe mit dem höchsten Rang für den aktuellen Benutzer oder das aktuelle Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="739b1-141">This request retrieves the remote variables for the highest-ranked flight group for the current user or device.</span></span> <span data-ttu-id="739b1-142">Um diese Anforderung zu senden, übergeben Sie die folgenden Informationen an den *RequestKind*- und *ParametersAsJson*-Parameter der **SendRequestAsync**-Methode.</span><span class="sxs-lookup"><span data-stu-id="739b1-142">To send this request, pass the following information to the *requestKind* and *parametersAsJson* parameters of the **SendRequestAsync** method.</span></span>

|  <span data-ttu-id="739b1-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="739b1-143">Parameter</span></span>  |  <span data-ttu-id="739b1-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="739b1-144">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="739b1-145">requestKind</span><span class="sxs-lookup"><span data-stu-id="739b1-145">requestKind</span></span>*                   |  <span data-ttu-id="739b1-146">Geben Sie die Ziffer7 ein, um die Test-Flight-Gruppe mit dem höchsten Rang für das Gerät zurückzugeben, oder geben Sie8 ein, um die Test-Flight-Gruppe mit dem höchsten Rang für den aktuellen Benutzer und das aktuelle Gerät zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="739b1-146">Specify 7 to return the highest-ranked flight group for the device, or specify 8 to return the highest-ranked flight group for the current user and device.</span></span> <span data-ttu-id="739b1-147">Wir empfehlen die Verwendung des Werts8 für den *RequestKind*-Parameter, da dieser Wert die Test-Flight-Gruppe mit dem höchsten Rang innerhalb der Mitgliedschaft für den aktuellen Benutzer und das aktuelle Gerät zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="739b1-147">We recommend using the value 8 for the *requestKind* parameter, because this value will return the highest-ranked flight group across the membership for both the current user and device.</span></span>  |
|  *<span data-ttu-id="739b1-148">parametersAsJson</span><span class="sxs-lookup"><span data-stu-id="739b1-148">parametersAsJson</span></span>*                   |  <span data-ttu-id="739b1-149">Übergeben Sie eine Zeichenfolge im JSON-Format, die die im folgenden Beispiel angezeigten Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="739b1-149">Pass a JSON-formatted string that contains the data shown in the example below.</span></span>  |

<span data-ttu-id="739b1-150">Das folgende Beispiel zeigt das Format der JSON-Daten, die an den *ParametersAsJson*-Parameter übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="739b1-150">The following example shows the format of the JSON data to pass to *parametersAsJson*.</span></span> <span data-ttu-id="739b1-151">Das Feld *type* muss der Zeichenfolge *GetRemoteVariables* zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="739b1-151">The *type* field must be assigned to the string *GetRemoteVariables*.</span></span> <span data-ttu-id="739b1-152">Weisen Sie das Feld *ProjectId* auf die ID des Projekts, in dem Sie die remotevariablen im Partner Center definiert.</span><span class="sxs-lookup"><span data-stu-id="739b1-152">Assign the *projectId* field to the ID of the project in which you defined the remote variables in Partner Center.</span></span>

```json
{ 
    "type": "GetRemoteVariables", 
    "parameters": "{ \"projectId\": \"your project ID\" }" 
}
```

<span data-ttu-id="739b1-153">Nach Übermittlung dieser Anforderung enthält die [Response](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.Response)-Eigenschaft des [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult)-Rückgabewerts eine Zeichenfolge im JSON-Format mit den folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="739b1-153">After you submit this request, the [Response](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.Response) property of the [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult) return value contains a JSON-formatted string with the following fields.</span></span>

|  <span data-ttu-id="739b1-154">Feld</span><span class="sxs-lookup"><span data-stu-id="739b1-154">Field</span></span>  |  <span data-ttu-id="739b1-155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="739b1-155">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="739b1-156">anonymous</span><span class="sxs-lookup"><span data-stu-id="739b1-156">anonymous</span></span>*                   |  <span data-ttu-id="739b1-157">Ein boolescher Wert, wobei **true** angibt, dass die Identität des Benutzers oder Geräts in der Anforderung nicht vorhanden war; **false** bedeutet, dass die Identität des Benutzers oder Geräts in der Anforderung vorhanden war.</span><span class="sxs-lookup"><span data-stu-id="739b1-157">A Boolean value, where **true** indicates that the user or device identity was not present in the request, and **false** indicates that user or device identity was present in the request.</span></span>  |
|  *<span data-ttu-id="739b1-158">name</span><span class="sxs-lookup"><span data-stu-id="739b1-158">name</span></span>*                   |  <span data-ttu-id="739b1-159">Eine Zeichenfolge, die den Namen der Test-Flight-Gruppe mit dem höchsten Rang enthält, der das Gerät oder der Benutzer angehört.</span><span class="sxs-lookup"><span data-stu-id="739b1-159">A string that contains the name of the highest-ranked flight group to which the device or user belongs.</span></span>  |
|  *<span data-ttu-id="739b1-160">settings</span><span class="sxs-lookup"><span data-stu-id="739b1-160">settings</span></span>*                   |  <span data-ttu-id="739b1-161">Ein Wörterbuch mit Schlüssel-Wert-Paaren, die den Namen und den Wert der Remotevariablen enthalten, die der Entwickler für die Test-Flight-Gruppe konfiguriert hat.</span><span class="sxs-lookup"><span data-stu-id="739b1-161">A dictionary of key/value pairs that contain the name and value of the remote variables that the developer has configured for the flight group.</span></span>  |

<span data-ttu-id="739b1-162">Das folgende Beispiel zeigt einen Rückgabewert für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="739b1-162">The following example demonstrates a return value for this request.</span></span>

```json
{ 
  "anonymous": false, 
  "name": "Insider Slow",
  "settings":
  {
      "Audience": "Slow"
      ...
  }
}
```

### <a name="add-the-current-device-or-user-to-a-flight-group"></a><span data-ttu-id="739b1-163">Hinzufügen des aktuellen Geräts oder Benutzers zu einer Test-Flight-Gruppe</span><span class="sxs-lookup"><span data-stu-id="739b1-163">Add the current device or user to a flight group</span></span>

> [!IMPORTANT]
> <span data-ttu-id="739b1-164">Diese Anforderung ist derzeit für die meisten Entwicklerkonten nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="739b1-164">This request is currently not available to most developer accounts.</span></span> <span data-ttu-id="739b1-165">Diese Anforderung wird fehlschlagen, es sei denn, Ihr Entwicklerkonto wird speziell von Microsoft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="739b1-165">This request will fail unless your developer account is specially provisioned by Microsoft.</span></span>

<span data-ttu-id="739b1-166">Um diese Anforderung zu senden, übergeben Sie die folgenden Informationen an die *RequestKind*- und *ParametersAsJson*-Parameter der **SendRequestAsync**-Methode.</span><span class="sxs-lookup"><span data-stu-id="739b1-166">To send this request, pass the following information to the *requestKind* and *parametersAsJson* parameters of the **SendRequestAsync** method.</span></span>

|  <span data-ttu-id="739b1-167">Parameter</span><span class="sxs-lookup"><span data-stu-id="739b1-167">Parameter</span></span>  |  <span data-ttu-id="739b1-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="739b1-168">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="739b1-169">requestKind</span><span class="sxs-lookup"><span data-stu-id="739b1-169">requestKind</span></span>*                   |  <span data-ttu-id="739b1-170">Geben Sie den Wert7 ein, um das Gerät zu einer Test-Flight-Gruppe hinzufügen; geben Sie alternativ den Wert8 ein, um den Benutzer hinzuzufügen, der derzeit im Store einer Test-Flight-Gruppe angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="739b1-170">Specify 7 to add the device to a flight group, or specify 8 to add the user who is currently signed in to the Store to a flight group.</span></span>  |
|  *<span data-ttu-id="739b1-171">parametersAsJson</span><span class="sxs-lookup"><span data-stu-id="739b1-171">parametersAsJson</span></span>*                   |  <span data-ttu-id="739b1-172">Übergeben Sie eine Zeichenfolge im JSON-Format, die die im folgenden Beispiel angezeigten Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="739b1-172">Pass a JSON-formatted string that contains the data shown in the example below.</span></span>  |

<span data-ttu-id="739b1-173">Das folgende Beispiel zeigt das Format der JSON-Daten, die an den *ParametersAsJson*-Parameter übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="739b1-173">The following example shows the format of the JSON data to pass to *parametersAsJson*.</span></span> <span data-ttu-id="739b1-174">Das Feld *type* muss der Zeichenfolge *AddToFlightGroup* zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="739b1-174">The *type* field must be assigned to the string *AddToFlightGroup*.</span></span> <span data-ttu-id="739b1-175">Weisen Sie das Feld *FlightGroupId* der ID der Test-Flight-Gruppe zu, zu der Sie das Gerät oder den Benutzer hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="739b1-175">Assign the *flightGroupId* field to the ID of the flight group to which you want to add the device or user.</span></span>

```json
{ 
    "type": "AddToFlightGroup", 
    "parameters": "{ \"flightGroupId\": \"your group ID\" }" 
}
```

<span data-ttu-id="739b1-176">Wenn ein Fehler bei der Anforderung vorliegt, enthält die [HttpStatusCode](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.HttpStatusCode)-Eigenschaft des [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult)-Rückgabewerts den Antwortcode.</span><span class="sxs-lookup"><span data-stu-id="739b1-176">If there is an error with the request, the [HttpStatusCode](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.HttpStatusCode) property of the [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult) return value contains the response code.</span></span>

### <a name="remove-the-current-device-or-user-from-a-flight-group"></a><span data-ttu-id="739b1-177">Entfernen des aktuellen Geräts oder Benutzers aus einer Test-Flight-Gruppe</span><span class="sxs-lookup"><span data-stu-id="739b1-177">Remove the current device or user from a flight group</span></span>

> [!IMPORTANT]
> <span data-ttu-id="739b1-178">Diese Anforderung ist derzeit für die meisten Entwicklerkonten nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="739b1-178">This request is currently not available to most developer accounts.</span></span> <span data-ttu-id="739b1-179">Diese Anforderung wird fehlschlagen, es sei denn, Ihr Entwicklerkonto wird speziell von Microsoft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="739b1-179">This request will fail unless your developer account is specially provisioned by Microsoft.</span></span>

<span data-ttu-id="739b1-180">Um diese Anforderung zu senden, übergeben Sie die folgenden Informationen an die *RequestKind*- und *ParametersAsJson*-Parameter der **SendRequestAsync**-Methode.</span><span class="sxs-lookup"><span data-stu-id="739b1-180">To send this request, pass the following information to the *requestKind* and *parametersAsJson* parameters of the **SendRequestAsync** method.</span></span>

|  <span data-ttu-id="739b1-181">Parameter</span><span class="sxs-lookup"><span data-stu-id="739b1-181">Parameter</span></span>  |  <span data-ttu-id="739b1-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="739b1-182">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="739b1-183">requestKind</span><span class="sxs-lookup"><span data-stu-id="739b1-183">requestKind</span></span>*                   |  <span data-ttu-id="739b1-184">Geben Sie den Wert7 ein, um das Gerät aus einer Test-Flight-Gruppe zu entfernen; geben Sie alternativ den Wert8 ein, um den Benutzer zu entfernen, der derzeit im Store einer Test-Flight-Gruppe angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="739b1-184">Specify 7 to remove the device from a flight group, or specify 8 to remove the user who is currently signed in to the Store from a flight group.</span></span>  |
|  *<span data-ttu-id="739b1-185">parametersAsJson</span><span class="sxs-lookup"><span data-stu-id="739b1-185">parametersAsJson</span></span>*                   |  <span data-ttu-id="739b1-186">Übergeben Sie eine Zeichenfolge im JSON-Format, die die im folgenden Beispiel angezeigten Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="739b1-186">Pass a JSON-formatted string that contains the data shown in the example below.</span></span>  |

<span data-ttu-id="739b1-187">Das folgende Beispiel zeigt das Format der JSON-Daten, die an den *ParametersAsJson*-Parameter übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="739b1-187">The following example shows the format of the JSON data to pass to *parametersAsJson*.</span></span> <span data-ttu-id="739b1-188">Das Feld *type* muss der Zeichenfolge *RemoveFromFlightGroup* zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="739b1-188">The *type* field must be assigned to the string *RemoveFromFlightGroup*.</span></span> <span data-ttu-id="739b1-189">Weisen Sie das Feld *flightGroupId* der ID der Test-Flight-Gruppe zu, aus der Sie das Gerät oder den Benutzer entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="739b1-189">Assign the *flightGroupId* field to the ID of the flight group from which you want to remove the device or user.</span></span>

```json
{ 
    "type": "RemoveFromFlightGroup", 
    "parameters": "{ \"flightGroupId\": \"your group ID\" }" 
}
```

<span data-ttu-id="739b1-190">Wenn ein Fehler bei der Anforderung vorliegt, enthält die [HttpStatusCode](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.HttpStatusCode)-Eigenschaft des [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult)-Rückgabewerts den Antwortcode.</span><span class="sxs-lookup"><span data-stu-id="739b1-190">If there is an error with the request, the [HttpStatusCode](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.HttpStatusCode) property of the [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult) return value contains the response code.</span></span>

## <a name="related-topics"></a><span data-ttu-id="739b1-191">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="739b1-191">Related topics</span></span>

* [<span data-ttu-id="739b1-192">Ein Bewertungs- und Rezensionsdialogfeld in Ihrer App anzeigen</span><span class="sxs-lookup"><span data-stu-id="739b1-192">Show a rating and review dialog in your app</span></span>](request-ratings-and-reviews.md#show-a-rating-and-review-dialog-in-your-app)
* [<span data-ttu-id="739b1-193">SendRequestAsync</span><span class="sxs-lookup"><span data-stu-id="739b1-193">SendRequestAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper.sendrequestasync)
