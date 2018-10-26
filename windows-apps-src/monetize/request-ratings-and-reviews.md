---
author: Xansky
Description: Learn about several ways you can programmatically enable customers to rate and review your app.
title: Anfordern von Bewertungen und Prüfungen für Ihre App
ms.author: mhopkins
ms.date: 06/15/2018
ms.topic: article
keywords: Windows10, UWP, Bewertungen, Rezensionen
ms.localizationpriority: medium
ms.openlocfilehash: d736fa47251c85491a29b324a3ed59181a5060c8
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5592935"
---
# <a name="request-ratings-and-reviews-for-your-app"></a><span data-ttu-id="eb60b-103">Anfordern von Bewertungen und Prüfungen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="eb60b-103">Request ratings and reviews for your app</span></span>

<span data-ttu-id="eb60b-104">Sie können Code zu Ihrer Universellen Windows-Plattform (UWP)-App hinzufügen, um Ihre Kunden programmgesteuert aufzufordern, Ihre App zu bewerten oder zu rezensieren.</span><span class="sxs-lookup"><span data-stu-id="eb60b-104">You can add code to your Universal Windows Platform (UWP) app to programmatically prompt your customers to rate or review your app.</span></span> <span data-ttu-id="eb60b-105">Hierfür stehen Ihnen mehrere Möglichkeiten zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="eb60b-105">There are several ways you can do this:</span></span>
* <span data-ttu-id="eb60b-106">Sie können ein Bewertungs- und Rezensionsdialogfeld direkt im Kontext Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="eb60b-106">You can show a rating and review dialog directly in the context of your app.</span></span>
* <span data-ttu-id="eb60b-107">Sie können programmgesteuert die Bewertungs- und Rezensionsseite für Ihre App im Microsoft Store öffnen.</span><span class="sxs-lookup"><span data-stu-id="eb60b-107">You can programmatically open the rating and review page for your app in the Microsoft Store.</span></span>

<span data-ttu-id="eb60b-108">Wenn Sie Ihre Bewertungs- und Rezensionsdaten analysieren möchten, können Sie die Daten im Windows Dev Center-Dashboard einsehen oder die Microsoft Store-Analyse-API zum programmgesteuerten Abrufen dieser Daten verwenden.</span><span class="sxs-lookup"><span data-stu-id="eb60b-108">When you are ready to analyze your ratings and reviews data, you can view the data in the Windows Dev Center dashboard or use the Microsoft Store analytics API to retrieve this data programmatically.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb60b-109">Wenn Sie eine Bewertung Funktion innerhalb Ihrer app hinzufügen, müssen alle Rezensionen der Benutzer auf den Store Bewertung Mechanismen, unabhängig von der Bewertung ausgewählte Star senden.</span><span class="sxs-lookup"><span data-stu-id="eb60b-109">When adding a rating function within your app, all reviews must send the user to the Store’s rating mechanisms, regardless of star rating chosen.</span></span> <span data-ttu-id="eb60b-110">Wenn Sie Feedback oder Kommentare von Benutzern erfassen, muss es deutlich gemacht werden, dass er bezieht sich nicht auf die app-Bewertung oder Rezensionen im Store jedoch direkt an die app-Entwickler gesendet.</span><span class="sxs-lookup"><span data-stu-id="eb60b-110">If you collect feedback or comments from users, it must be clear that it is not related to the app rating or reviews in the Store but is sent directly to the app developer.</span></span> <span data-ttu-id="eb60b-111">Finden Sie unter den Entwickler Verhaltensregeln für Weitere Informationen im Zusammenhang mit [Fraudulent oder unredliche Aktivitäten](https://docs.microsoft.com/legal/windows/agreements/store-developer-code-of-conduct#3-fraudulent-or-dishonest-activities).</span><span class="sxs-lookup"><span data-stu-id="eb60b-111">See the Developer Code of Conduct for more information related to [Fraudulent or Dishonest Activities](https://docs.microsoft.com/legal/windows/agreements/store-developer-code-of-conduct#3-fraudulent-or-dishonest-activities).</span></span>

## <a name="show-a-rating-and-review-dialog-in-your-app"></a><span data-ttu-id="eb60b-112">Ein Bewertungs- und Rezensionsdialogfeld in Ihrer App anzeigen</span><span class="sxs-lookup"><span data-stu-id="eb60b-112">Show a rating and review dialog in your app</span></span>

<span data-ttu-id="eb60b-113">Wenn Sie programmgesteuert ein Dialogfeld von Ihrer App aus anzeigen möchten, das Ihre Kunden auffordert, die App zu bewerten und eine Rezension zu senden, rufen Sie die [SendRequestAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper.sendrequestasync)-Methode im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace auf.</span><span class="sxs-lookup"><span data-stu-id="eb60b-113">To programmatically show a dialog from your app that asks your customer to rate your app and submit a review, call the [SendRequestAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper.sendrequestasync) method in the [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) namespace.</span></span> <span data-ttu-id="eb60b-114">Übergeben Sie die ganze Zahl 16 an den *requestKind*-Parameter und eine leere Zeichenfolge an den *parametersAsJson*-Parameter wie in diesem Codebeispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="eb60b-114">Pass the integer 16 to the *requestKind* parameter and an empty string to the *parametersAsJson* parameter as shown in this code example.</span></span> <span data-ttu-id="eb60b-115">Dieses Beispiel erfordert die [Json.NET](http://www.newtonsoft.com/json)-Bibliothek von Newtonsoft sowie die Verwendung von using-Anweisungen für die **Windows.Services.Store**-, **System.Threading.Tasks**- und \*\*Newtonsoft.Json.Linq \*\*-Namespaces.</span><span class="sxs-lookup"><span data-stu-id="eb60b-115">This example requires the [Json.NET](http://www.newtonsoft.com/json) library from Newtonsoft, and it requires using statements for the **Windows.Services.Store**, **System.Threading.Tasks**, and **Newtonsoft.Json.Linq** namespaces.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb60b-116">Die Anforderung zum Anzeigen des Bewertungs- und Rezensionsdialogfelds muss im UI-Thread in Ihrer App aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="eb60b-116">The request to show the rating and review dialog must be called on the UI thread in your app.</span></span>

```csharp
public async Task<bool> ShowRatingReviewDialog()
{
    StoreSendRequestResult result = await StoreRequestHelper.SendRequestAsync(
        StoreContext.GetDefault(), 16, String.Empty);

    if (result.ExtendedError == null)
    {
        JObject jsonObject = JObject.Parse(result.Response);
        if (jsonObject.SelectToken("status").ToString() == "success")
        {
            // The customer rated or reviewed the app.
            return true;
        }
    }

    // There was an error with the request, or the customer chose not to
    // rate or review the app.
    return false;
}
```

<span data-ttu-id="eb60b-117">Die **SendRequestAsync**-Methode verwendet ein einfaches ganzzahlig-basiertes Anforderungssystem und JSON-basierte-Datenparameter, um verschiedene Store-Vorgänge den Apps zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="eb60b-117">The **SendRequestAsync** method uses a simple integer-based request system and JSON-based data parameters to expose miscellaneous Store operations to apps.</span></span> <span data-ttu-id="eb60b-118">Wenn Sie die ganze Zahl 16 an den *requestKind*-Parameter übergeben, stellen Sie eine Anforderung zum Anzeigen des Bewertungs- und Rezensionsdialogfeldes aus und senden die zugehörigen Daten an den Store.</span><span class="sxs-lookup"><span data-stu-id="eb60b-118">When you pass the integer 16 to the *requestKind* parameter, you issue a request to show the rating and review dialog and send the related data to the Store.</span></span> <span data-ttu-id="eb60b-119">Diese Methode wurde in Windows10, Version 1607, eingeführt und kann nur in Projekten für die **Windows 10 Anniversary Edition (10.0; Build 14393)** oder einer neueren Version in Visual Studio verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="eb60b-119">This method was introduced in Windows 10, version 1607, and it can only be used in projects that target **Windows 10 Anniversary Edition (10.0; Build 14393)** or a later release in Visual Studio.</span></span> <span data-ttu-id="eb60b-120">Eine allgemeine Übersicht über diese Methode finden Sie unter [Anforderungen an den Store senden](send-requests-to-the-store.md).</span><span class="sxs-lookup"><span data-stu-id="eb60b-120">For a general overview of this method, see [Send requests to the Store](send-requests-to-the-store.md).</span></span>

### <a name="response-data-for-the-rating-and-review-request"></a><span data-ttu-id="eb60b-121">Antwortdaten für die Bewertungs- und Rezensionsanforderung</span><span class="sxs-lookup"><span data-stu-id="eb60b-121">Response data for the rating and review request</span></span>

<span data-ttu-id="eb60b-122">Nach Übermittlung der Anforderung zum Anzeigen eines Bewertungs- und Rezensionsdialogfeldes gibt die [Response](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.Response)-Eigenschaft des [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult)-Rückgabewerts eine Zeichenfolge im JSON-Format zurück, die anzeigt, ob die Anforderung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="eb60b-122">After you submit the request to display the rating and review dialog, the [Response](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.Response) property of the [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult) return value contains a JSON-formatted string that indicates whether the request was successful.</span></span>

<span data-ttu-id="eb60b-123">Das folgende Beispiel veranschaulicht den Rückgabewert für diese Anforderung, nachdem der Kunde erfolgreich eine Bewertung oder Rezension übermittelt hat.</span><span class="sxs-lookup"><span data-stu-id="eb60b-123">The following example demonstrates the return value for this request after the customer successfully submits a rating or review.</span></span>

```json
{ 
  "status": "success", 
  "data": {
    "updated": false
  },
  "errorDetails": "Success"
}
```

<span data-ttu-id="eb60b-124">Das folgende Beispiel veranschaulicht den Rückgabewert für diese Anforderung, nachdem der Kunde gewählt hat, keine Bewertung oder Rezension zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="eb60b-124">The following example demonstrates the return value for this request after the customer chooses not to submit a rating or review.</span></span>

```json
{ 
  "status": "aborted", 
  "errorDetails": "Navigation was unsuccessful"
}
```

<span data-ttu-id="eb60b-125">In der folgenden Tabelle werden die Felder in der Zeichenfolge im JSON-Format erläutert.</span><span class="sxs-lookup"><span data-stu-id="eb60b-125">The following table describes the fields in the JSON-formatted data string.</span></span>

|  <span data-ttu-id="eb60b-126">Feld</span><span class="sxs-lookup"><span data-stu-id="eb60b-126">Field</span></span>  |  <span data-ttu-id="eb60b-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eb60b-127">Description</span></span>  |
|----------------------|---------------|
|  *<span data-ttu-id="eb60b-128">status</span><span class="sxs-lookup"><span data-stu-id="eb60b-128">status</span></span>*                   |  <span data-ttu-id="eb60b-129">Eine Zeichenfolge, die angibt, ob der Kunde eine Bewertung oder Rezension erfolgreich gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="eb60b-129">A string that indicates whether the customer successfully submitted a rating or review.</span></span> <span data-ttu-id="eb60b-130">Die unterstützten Werte sind **success** und **aborted**.</span><span class="sxs-lookup"><span data-stu-id="eb60b-130">The supported values are **success** and **aborted**.</span></span>   |
|  *<span data-ttu-id="eb60b-131">data</span><span class="sxs-lookup"><span data-stu-id="eb60b-131">data</span></span>*                   |  <span data-ttu-id="eb60b-132">Ein Objekt, das nur einen booleschen Wert mit dem Namen *aktualisiert* enthält.</span><span class="sxs-lookup"><span data-stu-id="eb60b-132">An object that contains a single Boolean value named *updated*.</span></span> <span data-ttu-id="eb60b-133">Dieser Wert gibt an, ob der Kunde eine vorhandene Bewertung oder Rezension aktualisiert hat.</span><span class="sxs-lookup"><span data-stu-id="eb60b-133">This value indicates whether the customer updated an existing rating or review.</span></span> <span data-ttu-id="eb60b-134">Das *data*-Objekt ist nur in den Erfolgsantworten enthalten.</span><span class="sxs-lookup"><span data-stu-id="eb60b-134">The *data* object is included in success responses only.</span></span>   |
|  *<span data-ttu-id="eb60b-135">errorDetails</span><span class="sxs-lookup"><span data-stu-id="eb60b-135">errorDetails</span></span>*                   |  <span data-ttu-id="eb60b-136">Eine Zeichenfolge, die Fehlerdetails für die Anforderung enthält.</span><span class="sxs-lookup"><span data-stu-id="eb60b-136">A string that contains the error details for the request.</span></span> |

## <a name="launch-the-rating-and-review-page-for-your-app-in-the-store"></a><span data-ttu-id="eb60b-137">Die Bewertungs- und Rezensionsseite für Ihre App im Store starten</span><span class="sxs-lookup"><span data-stu-id="eb60b-137">Launch the rating and review page for your app in the Store</span></span>

<span data-ttu-id="eb60b-138">Wenn Sie programmgesteuert eine Bewertungs- und Rezensionsseite für Ihre App im Store öffnen möchten, können Sie die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync)-Methode mit dem ```ms-windows-store://review```-URI-Schema verwenden, wie in diesem Codebeispiel gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="eb60b-138">If you want to programmatically open the rating and review page for your app in the Store, you can use the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync) method with the ```ms-windows-store://review``` URI scheme as demonstrated in this code example.</span></span>

```csharp
bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-windows-store://review/?ProductId=9WZDNCRFHVJL"));
```

<span data-ttu-id="eb60b-139">Weitere Informationen finden Sie unter [Die Microsoft Store App starten](../launch-resume/launch-store-app.md).</span><span class="sxs-lookup"><span data-stu-id="eb60b-139">For more information, see [Launch the Microsoft Store app](../launch-resume/launch-store-app.md).</span></span>

## <a name="analyze-your-ratings-and-reviews-data"></a><span data-ttu-id="eb60b-140">Ihre Bewertungs- und Rezensionsdaten analysieren</span><span class="sxs-lookup"><span data-stu-id="eb60b-140">Analyze your ratings and reviews data</span></span>

<span data-ttu-id="eb60b-141">Sie haben mehrere Optionen, um die Bewertungs- und Rezensionsdaten von Ihren Kunden zu analysieren:</span><span class="sxs-lookup"><span data-stu-id="eb60b-141">To analyze the ratings and reviews data from your customers, you have several options:</span></span>
* <span data-ttu-id="eb60b-142">Sie können den [Rezensionsbericht](../publish/reviews-report.md) im Windows Dev Center-Dashboard verwenden, um die Bewertungen und Prüfungen von Ihren Kunden zu sehen.</span><span class="sxs-lookup"><span data-stu-id="eb60b-142">You can use the [Reviews](../publish/reviews-report.md) report in the Windows Dev Center dashboard to see the ratings and reviews from your customers.</span></span> <span data-ttu-id="eb60b-143">Sie können diesen Bericht auch herunterladen, um ihn offline zu sehen.</span><span class="sxs-lookup"><span data-stu-id="eb60b-143">You can also download this report to view it offline.</span></span>
* <span data-ttu-id="eb60b-144">Sie können die [Abrufen von App-Bewertungen](get-app-ratings.md)- und [Abrufen von App-Rezensionen](get-app-reviews.md)-Methoden in der Store-Analyse-API zum programmgesteuerten Abrufen der Bewertungen und Prüfungen von Ihren Kunden im JSON-Format verwenden.</span><span class="sxs-lookup"><span data-stu-id="eb60b-144">You can use the [Get app ratings](get-app-ratings.md) and [Get app reviews](get-app-reviews.md) methods in the Store analytics API to programmatically retrieve the ratings and reviews from your customers in JSON format.</span></span>

## <a name="related-topics"></a><span data-ttu-id="eb60b-145">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="eb60b-145">Related topics</span></span>

* [<span data-ttu-id="eb60b-146">Senden von Anfragen an den Store</span><span class="sxs-lookup"><span data-stu-id="eb60b-146">Send requests to the Store</span></span>](send-requests-to-the-store.md)
* [<span data-ttu-id="eb60b-147">Starten der Microsoft Store-App</span><span class="sxs-lookup"><span data-stu-id="eb60b-147">Launch the Microsoft Store app</span></span>](../launch-resume/launch-store-app.md)
* [<span data-ttu-id="eb60b-148">Rezensionsbericht</span><span class="sxs-lookup"><span data-stu-id="eb60b-148">Reviews report</span></span>](../publish/reviews-report.md)
