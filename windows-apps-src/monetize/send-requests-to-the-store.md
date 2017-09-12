---
author: mcleanbyron
Description: "Sie können mithilfe der SendRequestAsync-Methode Anforderungen an den Windows Store für Vorgänge senden, für die im Windows SDK noch keine API zur Verfügung steht."
title: Senden von Anforderungen an den Windows Store
ms.assetid: 070B9CA4-6D70-4116-9B18-FBF246716EF0
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, StoreRequestHelper, SendRequestAsync
ms.openlocfilehash: a949b3c93bb5b4a056f9e1fa4679e8ddca05d899
ms.sourcegitcommit: a9e4be98688b3a6125fd5dd126190fcfcd764f95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2017
---
# <a name="send-requests-to-the-windows-store"></a><span data-ttu-id="388e0-104">Senden von Anforderungen an den Windows Store</span><span class="sxs-lookup"><span data-stu-id="388e0-104">Send requests to the Windows Store</span></span>

<span data-ttu-id="388e0-105">Ab Windows10, Version 1607, bietet das Windows SDK im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace APIs für Store-bezogene Vorgänge (z.B. In-App-Einkäufe).</span><span class="sxs-lookup"><span data-stu-id="388e0-105">Starting in Windows 10, version 1607, the Windows SDK provides APIs for Store-related operations (such as in-app purchases) in the [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) namespace.</span></span> <span data-ttu-id="388e0-106">Obwohl die Dienste, die den Store unterstützen, zwischen den verschiedenen Betriebssystemversionen kontinuierlich aktualisiert, erweitert und verbessert werden, werden neue APIs in der Regel nur bei Hauptversionen des Betriebssystems zum Windows SDK hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="388e0-106">However, although the services that support the Store are constantly being updated, expanded, and improved between OS releases, new APIs are typically added to the Windows SDK only during major OS releases.</span></span>

<span data-ttu-id="388e0-107">Unsere [SendRequestAsync](https://docs.microsoft.com/uwp/api/Windows.Services.Store.StoreRequestHelper#Windows_Services_Store_StoreRequestHelper_SendRequestAsync_Windows_Services_Store_StoreContext_System_UInt32_System_String_)-Methode ist eine flexible Lösung zur Bereitstellung neuer Store-Vorgänge für UWP (Universelle Windows-Plattform)-Apps vor der Veröffentlichung einer neuen Windows SDK-Version.</span><span class="sxs-lookup"><span data-stu-id="388e0-107">We provide the [SendRequestAsync](https://docs.microsoft.com/uwp/api/Windows.Services.Store.StoreRequestHelper#Windows_Services_Store_StoreRequestHelper_SendRequestAsync_Windows_Services_Store_StoreContext_System_UInt32_System_String_) method as a flexible way to make new Store operations available to Universal Windows Platform (UWP) apps before a new version of the Windows SDK is released.</span></span> <span data-ttu-id="388e0-108">Sie können mithilfe dieser Methode Anforderungen an den Windows Store für Vorgänge senden, für die in der neuesten Windows SDK-Version noch keine entsprechende API zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="388e0-108">You can use this method to send requests to the Store for new operations that do not yet have a corresponding API available in the latest release of the Windows SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="388e0-109">Die **SendRequestAsync**-Methode ist nur für Apps für Windows 10, Version 1607 oder höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="388e0-109">The **SendRequestAsync** method is available only to apps that target Windows 10, version 1607, or later.</span></span> <span data-ttu-id="388e0-110">Einige Anforderungen, die von dieser Methode unterstützt werden, werden nur in Versionen nach Windows10, Version 1607 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="388e0-110">Some of the requests supported by this method are only supported in releases after Windows 10, version 1607.</span></span>

<span data-ttu-id="388e0-111">**SendRequestAsync** ist eine statische Methode der [StoreRequestHelper](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="388e0-111">**SendRequestAsync** is a static method of the [StoreRequestHelper](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper) class.</span></span> <span data-ttu-id="388e0-112">Um diese Methode aufzurufen, müssen Sie die folgenden Informationen an diese Methode übergeben:</span><span class="sxs-lookup"><span data-stu-id="388e0-112">To call this method, you must pass the following information to the method:</span></span>
* <span data-ttu-id="388e0-113">Ein [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Objekt, das Informationen zum Benutzer bereitstellt, für den Sie den Vorgang ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="388e0-113">A [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext) object that provides information about the user for which you want to perform the operation.</span></span> <span data-ttu-id="388e0-114">Weitere Informationen zu diesem Objekt finden Sie unter [Erste Schrittemit der StoreContext-Klasse](in-app-purchases-and-trials.md#get-started-with-the-storecontext-class).</span><span class="sxs-lookup"><span data-stu-id="388e0-114">For more information about this object, see [Get started with the StoreContext class](in-app-purchases-and-trials.md#get-started-with-the-storecontext-class).</span></span>
* <span data-ttu-id="388e0-115">Eine Ganzzahl, die die Anforderung identifiziert, die Sie an den Store senden möchten.</span><span class="sxs-lookup"><span data-stu-id="388e0-115">An integer that identifies the request that you want to send to the Store.</span></span>
* <span data-ttu-id="388e0-116">Wenn die Anforderung keine Argumente unterstützt, können Sie auch eine Zeichenfolge im JSON-Format übergeben, die die Argumente enthält, die zusammen mit der Anforderung übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="388e0-116">If the request supports any arguments, you can also pass a JSON-formatted string that contains the arguments to pass along with the request.</span></span>

<span data-ttu-id="388e0-117">Das folgende Beispiel veranschaulicht, wie diese Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="388e0-117">The following example demonstrates how to call this method.</span></span> <span data-ttu-id="388e0-118">In diesem Beispiel werden using-Anweisungen für die Namespaces **Windows.Services.Store** und **System.Threading.Tasks** benötigt.</span><span class="sxs-lookup"><span data-stu-id="388e0-118">This example requires using statements for the **Windows.Services.Store** and **System.Threading.Tasks** namespaces.</span></span>

```csharp
public async Task<bool> AddUserToFlightGroup()
{
    StoreSendRequestResult result = await StoreRequestHelper.SendRequestAsync(
        StoreContext.GetDefault(), 8,
        "{ \"type\": \"AddToFlightGroup\", \"parameters\": \"{ \"flightGroupId\": \"your group ID\" }\" }");

    if (result.ExtendedError == null)
    {
        return true;
    }

    return false;
}
```

<span data-ttu-id="388e0-119">Informationen zu den Anforderungen, die derzeit für die **SendRequestAsync**-Methode verfügbar sind, finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="388e0-119">See the following sections for information about the requests that are currently available via the **SendRequestAsync** method.</span></span> <span data-ttu-id="388e0-120">Dieser Artikel wird aktualisiert, wenn Unterstützung für neue Anforderungen hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="388e0-120">We will update this article when support for new requests are added.</span></span>

## <a name="requests-for-flight-group-scenarios"></a><span data-ttu-id="388e0-121">Anforderungen für Test-Flight-Gruppenszenarien</span><span class="sxs-lookup"><span data-stu-id="388e0-121">Requests for flight group scenarios</span></span>

> [!IMPORTANT]
> <span data-ttu-id="388e0-122">Alle in diesem Abschnittbeschriebenen Anforderungen für Test-Flight-Gruppen sind derzeit für die meisten Entwicklerkonten nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="388e0-122">All of the flight group requests described in this section are currently not available to most developer accounts.</span></span> <span data-ttu-id="388e0-123">Diese Anforderungen werden fehlschlagen, es sei denn, Ihr Entwicklerkonto wird speziell von Microsoft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="388e0-123">These requests will fail unless your developer account is specially provisioned by Microsoft.</span></span>

<span data-ttu-id="388e0-124">Die **SendRequestAsync**-Methode unterstützt eine Reihe von Anforderungen für Test-Flight-Gruppenszenarien wie das Hinzufügen von Benutzern oder Geräten zu einer Test-Flight-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="388e0-124">The **SendRequestAsync** method supports a set of requests for flight group scenarios, such as adding a user or device to a flight group.</span></span> <span data-ttu-id="388e0-125">Um diese Anforderungen zu senden, übergeben Sie den Wert7 oder8 an den *RequestKind*-Parameter und die Zeichenfolge im JSON-Format an den *ParametersAsJson*-Parameter, der die Anforderung angibt, die Sie zusammen mit allen zugehörigen Argumenten übermitteln möchten.</span><span class="sxs-lookup"><span data-stu-id="388e0-125">To submit these requests, pass the value 7 or 8 to the *requestKind* parameter along with a JSON-formatted string to the *parametersAsJson* parameter that indicates the request you want to submit along with any related arguments.</span></span> <span data-ttu-id="388e0-126">Diese *RequestKind*-Werte unterscheiden sich folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="388e0-126">These *requestKind* values differ in the following ways.</span></span>

|  <span data-ttu-id="388e0-127">RequestKind-Wert</span><span class="sxs-lookup"><span data-stu-id="388e0-127">Request kind value</span></span>  |  <span data-ttu-id="388e0-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="388e0-128">Description</span></span>  |
|----------------------|---------------|
|  <span data-ttu-id="388e0-129">7</span><span class="sxs-lookup"><span data-stu-id="388e0-129">7</span></span>                   |  <span data-ttu-id="388e0-130">Die Anforderungen werden im Kontext des aktuellen Geräts ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="388e0-130">The requests are performed in the context of the current device.</span></span> <span data-ttu-id="388e0-131">Dieser Wert kann nur unter Windows10, Version 1703 oder höher verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="388e0-131">This value can only be used on Windows 10, version 1703, or later.</span></span>  |
|  <span data-ttu-id="388e0-132">8</span><span class="sxs-lookup"><span data-stu-id="388e0-132">8</span></span>                   |  <span data-ttu-id="388e0-133">Die Anforderungen werden im Kontext des Benutzers ausgeführt, der aktuell beim Store angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="388e0-133">The requests are performed in the context of the user who is currently signed in to the Store.</span></span> <span data-ttu-id="388e0-134">Dieser Wert kann unter Windows10, Version 1607 oder höher verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="388e0-134">This value can be used on Windows 10, version 1607, or later.</span></span>  |

<span data-ttu-id="388e0-135">Die folgenden Anforderungen für Test-Flight-Gruppen werden derzeit implementiert.</span><span class="sxs-lookup"><span data-stu-id="388e0-135">The following flight group requests are currently implemented.</span></span>

### <a name="retrieve-remote-variables-for-the-highest-ranked-flight-group"></a><span data-ttu-id="388e0-136">Abrufen von Remotevariablen für Test-Flight-Gruppen mit dem höchsten Rang</span><span class="sxs-lookup"><span data-stu-id="388e0-136">Retrieve remote variables for the highest-ranked flight group</span></span>

> [!IMPORTANT]
> <span data-ttu-id="388e0-137">Diese Anforderung ist derzeit für die meisten Entwicklerkonten nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="388e0-137">This request is currently not available to most developer accounts.</span></span> <span data-ttu-id="388e0-138">Diese Anforderung wird fehlschlagen, es sei denn, Ihr Entwicklerkonto wird speziell von Microsoft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="388e0-138">This request will fail unless your developer account is specially provisioned by Microsoft.</span></span>

<span data-ttu-id="388e0-139">Diese Anforderung ruft die Remotevariablen für die Test-Flight-Gruppe mit dem höchsten Rang für den aktuellen Benutzer oder das aktuelle Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="388e0-139">This request retrieves the remote variables for the highest-ranked flight group for the current user or device.</span></span> <span data-ttu-id="388e0-140">Um diese Anforderung zu senden, übergeben Sie die folgenden Informationen an den *RequestKind*- und *ParametersAsJson*-Parameter der **SendRequestAsync**-Methode.</span><span class="sxs-lookup"><span data-stu-id="388e0-140">To send this request, pass the following information to the *requestKind* and *parametersAsJson* parameters of the **SendRequestAsync** method.</span></span>

|  <span data-ttu-id="388e0-141">Parameter</span><span class="sxs-lookup"><span data-stu-id="388e0-141">Parameter</span></span>  |  <span data-ttu-id="388e0-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="388e0-142">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="388e0-143">requestKind</span><span class="sxs-lookup"><span data-stu-id="388e0-143">requestKind</span></span>*                   |  <span data-ttu-id="388e0-144">Geben Sie die Ziffer7 ein, um die Test-Flight-Gruppe mit dem höchsten Rang für das Gerät zurückzugeben, oder geben Sie8 ein, um die Test-Flight-Gruppe mit dem höchsten Rang für den aktuellen Benutzer und das aktuelle Gerät zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="388e0-144">Specify 7 to return the highest-ranked flight group for the device, or specify 8 to return the highest-ranked flight group for the current user and device.</span></span> <span data-ttu-id="388e0-145">Wir empfehlen die Verwendung des Werts8 für den *RequestKind*-Parameter, da dieser Wert die Test-Flight-Gruppe mit dem höchsten Rang innerhalb der Mitgliedschaft für den aktuellen Benutzer und das aktuelle Gerät zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="388e0-145">We recommend using the value 8 for the *requestKind* parameter, because this value will return the highest-ranked flight group across the membership for both the current user and device.</span></span>  |
|  *<span data-ttu-id="388e0-146">parametersAsJson</span><span class="sxs-lookup"><span data-stu-id="388e0-146">parametersAsJson</span></span>*                   |  <span data-ttu-id="388e0-147">Übergeben Sie eine Zeichenfolge im JSON-Format, die die im folgenden Beispiel angezeigten Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="388e0-147">Pass a JSON-formatted string that contains the data shown in the example below.</span></span>  |

<span data-ttu-id="388e0-148">Das folgende Beispiel zeigt das Format der JSON-Daten, die an den *ParametersAsJson*-Parameter übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="388e0-148">The following example shows the format of the JSON data to pass to *parametersAsJson*.</span></span> <span data-ttu-id="388e0-149">Das Feld *type* muss der Zeichenfolge *GetRemoteVariables* zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="388e0-149">The *type* field must be assigned to the string *GetRemoteVariables*.</span></span> <span data-ttu-id="388e0-150">Weisen Sie das Feld *projectId* der ID des Projekts zu, bei dem Sie die Remotevariablen im Windows Dev Center-Dashboard definiert haben.</span><span class="sxs-lookup"><span data-stu-id="388e0-150">Assign the *projectId* field to the ID of the project in which you defined the remote variables in the Windows Dev Center dashboard.</span></span>

```json
{ 
    "type": "GetRemoteVariables", 
    "parameters": "{ \"projectId\": \"your project ID\" }" 
}
```

<span data-ttu-id="388e0-151">Nach Übermittlung dieser Anforderung enthält die [Response](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult#Windows_Services_Store_StoreSendRequestResult_Response)-Eigenschaft des [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult)-Rückgabewerts eine Zeichenfolge im JSON-Format mit den folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="388e0-151">After you submit this request, the [Response](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult#Windows_Services_Store_StoreSendRequestResult_Response) property of the [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult) return value contains a JSON-formatted string with the following fields.</span></span>

|  <span data-ttu-id="388e0-152">Feld</span><span class="sxs-lookup"><span data-stu-id="388e0-152">Field</span></span>  |  <span data-ttu-id="388e0-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="388e0-153">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="388e0-154">anonymous</span><span class="sxs-lookup"><span data-stu-id="388e0-154">anonymous</span></span>*                   |  <span data-ttu-id="388e0-155">Ein boolescher Wert, wobei **true** angibt, dass die Identität des Benutzers oder Geräts in der Anforderung nicht vorhanden war; **false** bedeutet, dass die Identität des Benutzers oder Geräts in der Anforderung vorhanden war.</span><span class="sxs-lookup"><span data-stu-id="388e0-155">A Boolean value, where **true** indicates that the user or device identity was not present in the request, and **false** indicates that user or device identity was present in the request.</span></span>  |
|  *<span data-ttu-id="388e0-156">name</span><span class="sxs-lookup"><span data-stu-id="388e0-156">name</span></span>*                   |  <span data-ttu-id="388e0-157">Eine Zeichenfolge, die den Namen der Test-Flight-Gruppe mit dem höchsten Rang enthält, der das Gerät oder der Benutzer angehört.</span><span class="sxs-lookup"><span data-stu-id="388e0-157">A string that contains the name of the highest-ranked flight group to which the device or user belongs.</span></span>  |
|  *<span data-ttu-id="388e0-158">settings</span><span class="sxs-lookup"><span data-stu-id="388e0-158">settings</span></span>*                   |  <span data-ttu-id="388e0-159">Ein Wörterbuch mit Schlüssel-Wert-Paaren, die den Namen und den Wert der Remotevariablen enthalten, die der Entwickler für die Test-Flight-Gruppe konfiguriert hat.</span><span class="sxs-lookup"><span data-stu-id="388e0-159">A dictionary of key/value pairs that contain the name and value of the remote variables that the developer has configured for the flight group.</span></span>  |

<span data-ttu-id="388e0-160">Das folgende Beispiel zeigt einen Rückgabewert für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="388e0-160">The following example demonstrates a return value for this request.</span></span>

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

### <a name="add-the-current-device-or-user-to-a-flight-group"></a><span data-ttu-id="388e0-161">Hinzufügen des aktuellen Geräts oder Benutzers zu einer Test-Flight-Gruppe</span><span class="sxs-lookup"><span data-stu-id="388e0-161">Add the current device or user to a flight group</span></span>

> [!IMPORTANT]
> <span data-ttu-id="388e0-162">Diese Anforderung ist derzeit für die meisten Entwicklerkonten nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="388e0-162">This request is currently not available to most developer accounts.</span></span> <span data-ttu-id="388e0-163">Diese Anforderung wird fehlschlagen, es sei denn, Ihr Entwicklerkonto wird speziell von Microsoft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="388e0-163">This request will fail unless your developer account is specially provisioned by Microsoft.</span></span>

<span data-ttu-id="388e0-164">Um diese Anforderung zu senden, übergeben Sie die folgenden Informationen an den *RequestKind*- und *ParametersAsJson*-Parameter der **SendRequestAsync**-Methode.</span><span class="sxs-lookup"><span data-stu-id="388e0-164">To send this request, pass the following information to the *requestKind* and *parametersAsJson* parameters of the **SendRequestAsync** method.</span></span>

|  <span data-ttu-id="388e0-165">Parameter</span><span class="sxs-lookup"><span data-stu-id="388e0-165">Parameter</span></span>  |  <span data-ttu-id="388e0-166">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="388e0-166">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="388e0-167">requestKind</span><span class="sxs-lookup"><span data-stu-id="388e0-167">requestKind</span></span>*                   |  <span data-ttu-id="388e0-168">Geben Sie den Wert7 ein, um das Gerät zu einer Test-Flight-Gruppe hinzufügen; geben Sie alternativ den Wert8 ein, um den Benutzer hinzuzufügen, der derzeit im Store einer Test-Flight-Gruppe angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="388e0-168">Specify 7 to add the device to a flight group, or specify 8 to add the user who is currently signed in to the Store to a flight group.</span></span>  |
|  *<span data-ttu-id="388e0-169">parametersAsJson</span><span class="sxs-lookup"><span data-stu-id="388e0-169">parametersAsJson</span></span>*                   |  <span data-ttu-id="388e0-170">Übergeben Sie eine Zeichenfolge im JSON-Format, die die im folgenden Beispiel angezeigten Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="388e0-170">Pass a JSON-formatted string that contains the data shown in the example below.</span></span>  |

<span data-ttu-id="388e0-171">Das folgende Beispiel zeigt das Format der JSON-Daten, die an den *ParametersAsJson*-Parameter übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="388e0-171">The following example shows the format of the JSON data to pass to *parametersAsJson*.</span></span> <span data-ttu-id="388e0-172">Das Feld *type* muss der Zeichenfolge *AddToFlightGroup* zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="388e0-172">The *type* field must be assigned to the string *AddToFlightGroup*.</span></span> <span data-ttu-id="388e0-173">Weisen Sie das Feld *FlightGroupId* der ID der Test-Flight-Gruppe zu, zu der Sie das Gerät oder den Benutzer hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="388e0-173">Assign the *flightGroupId* field to the ID of the flight group to which you want to add the device or user.</span></span>

```json
{ 
    "type": "AddToFlightGroup", 
    "parameters": "{ \"flightGroupId\": \"your group ID\" }" 
}
```

<span data-ttu-id="388e0-174">Wenn ein Fehler bei der Anforderung vorliegt, enthält die [HttpStatusCode](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult#Windows_Services_Store_StoreSendRequestResult_HttpStatusCode)-Eigenschaft des [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult)-Rückgabewerts den Antwortcode.</span><span class="sxs-lookup"><span data-stu-id="388e0-174">If there is an error with the request, the [HttpStatusCode](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult#Windows_Services_Store_StoreSendRequestResult_HttpStatusCode) property of the [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult) return value contains the response code.</span></span>

### <a name="remove-the-current-device-or-user-from-a-flight-group"></a><span data-ttu-id="388e0-175">Entfernen des aktuellen Geräts oder Benutzers aus einer Test-Flight-Gruppe</span><span class="sxs-lookup"><span data-stu-id="388e0-175">Remove the current device or user from a flight group</span></span>

> [!IMPORTANT]
> <span data-ttu-id="388e0-176">Diese Anforderung ist derzeit für die meisten Entwicklerkonten nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="388e0-176">This request is currently not available to most developer accounts.</span></span> <span data-ttu-id="388e0-177">Diese Anforderung wird fehlschlagen, es sei denn, Ihr Entwicklerkonto wird speziell von Microsoft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="388e0-177">This request will fail unless your developer account is specially provisioned by Microsoft.</span></span>

<span data-ttu-id="388e0-178">Um diese Anforderung zu senden, übergeben Sie die folgenden Informationen an die *RequestKind*- und *ParametersAsJson*-Parameter der **SendRequestAsync**-Methode.</span><span class="sxs-lookup"><span data-stu-id="388e0-178">To send this request, pass the following information to the *requestKind* and *parametersAsJson* parameters of the **SendRequestAsync** method.</span></span>

|  <span data-ttu-id="388e0-179">Parameter</span><span class="sxs-lookup"><span data-stu-id="388e0-179">Parameter</span></span>  |  <span data-ttu-id="388e0-180">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="388e0-180">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="388e0-181">requestKind</span><span class="sxs-lookup"><span data-stu-id="388e0-181">requestKind</span></span>*                   |  <span data-ttu-id="388e0-182">Geben Sie den Wert7 ein, um das Gerät aus einer Test-Flight-Gruppe zu entfernen; geben Sie alternativ den Wert8 ein, um den Benutzer zu entfernen, der derzeit im Store einer Test-Flight-Gruppe angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="388e0-182">Specify 7 to remove the device from a flight group, or specify 8 to remove the user who is currently signed in to the Store from a flight group.</span></span>  |
|  *<span data-ttu-id="388e0-183">parametersAsJson</span><span class="sxs-lookup"><span data-stu-id="388e0-183">parametersAsJson</span></span>*                   |  <span data-ttu-id="388e0-184">Übergeben Sie eine Zeichenfolge im JSON-Format, die die im folgenden Beispiel angezeigten Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="388e0-184">Pass a JSON-formatted string that contains the data shown in the example below.</span></span>  |

<span data-ttu-id="388e0-185">Das folgende Beispiel zeigt das Format der JSON-Daten, die an den *ParametersAsJson*-Parameter übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="388e0-185">The following example shows the format of the JSON data to pass to *parametersAsJson*.</span></span> <span data-ttu-id="388e0-186">Das Feld *type* muss der Zeichenfolge *RemoveFromFlightGroup* zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="388e0-186">The *type* field must be assigned to the string *RemoveFromFlightGroup*.</span></span> <span data-ttu-id="388e0-187">Weisen Sie das Feld *flightGroupId* der ID der Test-Flight-Gruppe zu, aus der Sie das Gerät oder den Benutzer entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="388e0-187">Assign the *flightGroupId* field to the ID of the flight group from which you want to remove the device or user.</span></span>

```json
{ 
    "type": "RemoveFromFlightGroup", 
    "parameters": "{ \"flightGroupId\": \"your group ID\" }" 
}
```

<span data-ttu-id="388e0-188">Wenn ein Fehler bei der Anforderung vorliegt, enthält die [HttpStatusCode](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult#Windows_Services_Store_StoreSendRequestResult_HttpStatusCode)-Eigenschaft des [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult)-Rückgabewerts den Antwortcode.</span><span class="sxs-lookup"><span data-stu-id="388e0-188">If there is an error with the request, the [HttpStatusCode](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult#Windows_Services_Store_StoreSendRequestResult_HttpStatusCode) property of the [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult) return value contains the response code.</span></span>

## <a name="related-topics"></a><span data-ttu-id="388e0-189">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="388e0-189">Related topics</span></span>

* [<span data-ttu-id="388e0-190">SendRequestAsync</span><span class="sxs-lookup"><span data-stu-id="388e0-190">SendRequestAsync</span></span>](https://docs.microsoft.com/uwp/api/Windows.Services.Store.StoreRequestHelper#Windows_Services_Store_StoreRequestHelper_SendRequestAsync_Windows_Services_Store_StoreContext_System_UInt32_System_String_)
